---
title: "Kubernetes RBAC Does Not Authorize MCP Tool Calls"
slug: kubernetes-rbac-does-not-authorize-mcp-tool-calls
date: 2026-10-29 09:40:00 +0000
author: Michael Kantor
categories:
  - Article
tags:
  - Security
  - Platform Engineering
  - AI Agents
---

A platform team can deploy a Model Context Protocol (MCP) server in Kubernetes, give its Pod a dedicated ServiceAccount, and restrict the namespace with NetworkPolicy. Those are useful controls, but they do not answer a basic question: **should this particular caller be allowed to invoke this particular tool with these arguments?**

Kubernetes RBAC can decide whether a workload identity may perform an operation against the Kubernetes API. It does not authenticate an MCP client or understand an MCP tool's arguments. A server can have minimal Kubernetes permissions and still expose a tool that calls an external service with overly broad credentials.

The distinction matters when an internal developer platform offers MCP servers as a reusable "golden path." The platform is responsible for more than keeping the Pod alive. It needs to define where caller authorization, workload permissions, and outbound access are checked.

## Start with the request the platform actually receives

Consider an HTTP MCP server offering two tools: \`find_deployment\` and \`restart_deployment\`. A developer's agent sends a \`tools/call\` request. The server might be behind an Ingress or API gateway and run with its own Kubernetes ServiceAccount.

There are at least two separate authorization decisions:

1. **Caller to tool server:** Is the incoming client permitted to call \`restart_deployment\`, and for which namespace and workload? This needs server-side application policy tied to a verified caller identity. Checking only the tool name is insufficient if a caller can choose a different namespace in the arguments.
2. **Tool server to Kubernetes:** Does the ServiceAccount used by the server have the Kubernetes API permissions needed to perform the requested operation? Kubernetes RBAC applies here, but its subject is the server's workload identity, not automatically the original MCP caller.

A third boundary appears if the tool also calls an external ticketing, cloud, or secrets API. The server must separately limit the downstream credential and request. The identity that authenticated to the MCP server should not silently become an unrestricted credential for another service.

The [MCP authorization specification](https://modelcontextprotocol.io/specification/2026-07-28/basic/authorization) defines optional authorization for HTTP transports. When that mechanism is used, it treats a protected MCP server as an OAuth resource server and specifies discovery and token-handling requirements. It does not replace the application's decision about which tool arguments are acceptable for a given caller. The authorization section also does not apply in the same way to locally launched \`stdio\` servers.

## Do not mistake a ServiceAccount for end-user delegation

Kubernetes [ServiceAccounts](https://kubernetes.io/docs/concepts/security/service-accounts/) give Pods a namespaced identity. Roles and RoleBindings can limit their access to Kubernetes resources. They do not, by themselves, prove which human or agent initiated an MCP request.

Suppose the server uses one ServiceAccount with permission to patch Deployments in three namespaces. If the application does not check the caller's permitted namespace before making the patch, every caller who reaches that tool may be able to exercise the same server-side authority. Kubernetes sees the ServiceAccount, not the original MCP user's intent.

For a shared MCP service, prefer an explicit mapping between verified client identity, permitted tool names, permitted resource selectors, and allowed argument ranges. Put this check in the server or a trusted authorization component that has enough context to inspect the requested operation. Then give the server only the downstream permissions that its supported operations require.

If a Pod has no reason to call the Kubernetes API, consider setting \`automountServiceAccountToken: false\` in its Pod specification. This removes an unnecessary credential mount; it does not authorize or block an MCP tool call.

## Restrict egress, but know what NetworkPolicy can prove

Kubernetes [NetworkPolicy](https://kubernetes.io/docs/concepts/services-networking/network-policies/) controls IP- and port-level traffic when the cluster's networking plugin implements enforcement. By default, a Pod is not isolated for egress, so outbound connections are allowed unless an applicable policy restricts them.

A narrowly selected baseline policy might begin like this:

\`\`\`yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: mcp-deny-egress
  namespace: agent-tools
spec:
  podSelector:
    matchLabels:
      app: mcp-tool-server
  policyTypes:
    - Egress
  egress: []
\`\`\`

This example is a **starting deny rule**, not a deployable allowlist. It isolates egress for matching Pods only when the network plugin enforces NetworkPolicy. Any genuinely required destinations, including DNS, identity discovery, and approved downstream APIs, need narrowly scoped allowances. Test those allowances in your own cluster before rollout.

NetworkPolicy cannot determine whether \`restart_deployment\` was an appropriate action for a particular user. It cannot enforce a semantic distinction between \`read_customer_record\` and \`export_all_customers\` when both calls reach the same HTTPS endpoint. That remains an application authorization problem.

## Test each boundary independently

A useful preproduction review should produce evidence for the failure cases, not just a successful demo. Use synthetic accounts and nonproduction workloads; avoid putting production credentials or customer data in the test.

| Probe | Evidence to collect |
| --- | --- |
| A client without authorization invokes a valid tool name | The MCP service denies the request without executing the downstream operation |
| A permitted client changes the namespace or resource argument | Server-side policy denies the out-of-scope target before making the API call |
| A valid tool request reaches Kubernetes with insufficient ServiceAccount RBAC | Kubernetes denies the operation, and the server reports the failure accurately |
| The MCP Pod attempts to reach a destination outside its egress allowlist | The connection fails **in a cluster with verified NetworkPolicy enforcement** |
| The policy service or required identity check is unavailable | Sensitive operations do not silently fall back to unrestricted execution |

Record the decision's verified principal, tool name, target resource, result, and a correlation identifier. Avoid logging raw secrets or unredacted sensitive tool arguments. For the downstream result, verify the target system's actual state; an HTTP success response alone is not proof that a requested change happened.

A denied Kubernetes API call does not prove the MCP server's caller authorization works. Likewise, a denied MCP call does not prove that the Pod's egress is restricted. Treat these as distinct claims requiring distinct evidence.

## Make this part of the platform contract

A reusable MCP deployment template can require a short, reviewable declaration: who may call which tools; which arguments affect resource scope; what Kubernetes permissions and external credentials the server uses; which network destinations are necessary; and how denied actions and policy outages are handled.

That declaration should be reviewed whenever the tool catalog changes, not just when the Pod image changes. Adding a new tool can expand the actions a previously authorized client is able to request without changing its network endpoint or Kubernetes ServiceAccount.

The platform team's job is to make these boundaries visible and testable. Kubernetes RBAC and NetworkPolicy are valuable parts of the design. Neither should be presented as proof that an MCP tool call is authorized.

### Sources

- [Model Context Protocol, authorization, July 28, 2026 specification](https://modelcontextprotocol.io/specification/2026-07-28/basic/authorization)
- [Kubernetes ServiceAccounts](https://kubernetes.io/docs/concepts/security/service-accounts/)
- [Kubernetes NetworkPolicy](https://kubernetes.io/docs/concepts/services-networking/network-policies/)
- [Kubernetes Pod Security Standards](https://kubernetes.io/docs/concepts/security/pod-security-standards/)

*Author and affiliation disclosure: Michael Kantor is President of HOL, which maintains open-source agent standards and security tooling. This article does not recommend any HOL product. The views here are the author's and do not represent an official position of the Cloud Native Platform Engineering Community or its working groups.*
