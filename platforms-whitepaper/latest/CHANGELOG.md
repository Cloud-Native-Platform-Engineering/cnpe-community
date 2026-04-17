# Platforms Whitepaper Changelog

## [v1.1]

### Summary

This release represents a significant revision of the CNCF Platforms White Paper, refining the narrative framing, restructuring key sections, and updating content to reflect the current state of platform engineering practice.

---

### Introduction

- Reframed the opening to position platform engineering as an optimization for enterprises that experienced DevOps autonomy but need to manage the resulting costs, security risks, and inefficiencies.
- Clarified the primary value proposition: codifying what is unique to a business but common across internal teams to create an internal economy of scale.
- Simplified language around cloud-native values delivered by platforms.

### Why Platforms?

- Reframed the DevOps narrative: autonomy brought process improvements but also shifted operational responsibility onto product teams, increasing cognitive load and risk from sprawling implementations.
- Added explicit callout of the duplication of operations across teams as a source of increased risk and unclear ownership.
- Tightened language throughout; removed redundant phrasing.

### What Is a Platform?

- Simplified the definition: "A cloud-native computing platform is an integrated collection of capabilities defined and presented to meet the needs of its users."
- Added emphasis on the platform providing a **consistent, opinionated** user experience.
- Noted that platforms **decouple underlying implementations from provided capabilities**, introducing vendor flexibility while maintaining a consistent interface for users.
- Clarified the distinction between cloud-like environments externalising architecture vs. simply managing independent resources.
- Updated quote formatting for Atlassian and Martin Fowler/Evan Bottcher citations.

### Platform Maturity

- Replaced the previous use-case progression list (5 numbered items) with a new **four-stage maturity model**:
  1. **Provisional** - Built out of necessity, erratic adoption, ad hoc operations.
  2. **Operationalized** - Dedicated team, reactive delivery, centrally tracked operations.
  3. **Scalable** - Treated as a product, investment based on customer value, intrinsic pull adoption.
  4. **Optimizing** - Enabled ecosystem, participatory adoption, specialists empowered to extend capabilities.
- Removed the `pageinfo` callout box; replaced with a direct link to the Platform Engineering Maturity Model.

### Attributes of Platforms

- **User experience**: Added **AI agents** as a supported interface type alongside GUIs, APIs, CLIs, IDEs, and portals.
- **Self-service**: Clarified that capabilities should be available on-demand without waiting for a manual review or approval.
- **Secure by default**: Renamed to **"Secure and compliant by default"**; expanded description to note that security, governance, and compliance requirements should be baked into the platform to reduce user cognitive burden while ensuring consistent enforcement.

### Attributes of Platform Teams

- Updated the list of platform team responsibilities to include **AI agents** alongside portals, APIs, documentation, templates, and CLI tools.
- Minor formatting cleanup (em dash usage, golden paths terminology).

### Challenges with Platforms

- Restructured from a brief bullet list into three explicitly named challenge sections with expanded guidance:
  1. **The platform is disconnected from the actual needs and wants of developers** - Emphasises product management partnership and the danger of top-down mandates.
  2. **Too much effort is spent on low-value solutions that are overfitted to early-adopters** - Advises maintaining a bird's-eye roadmap view while cherishing early adopters as champions.
  3. **Low investment from leadership due to lack of clear impact** - Advises demonstrating direct impact on value stream teams and positioning the platform team as a strategic partner.
- Added a forward reference to the metrics section for addressing the leadership investment challenge.

### Enabling Platform Teams

- Reformatted the three-item enabling list from multi-line bullet blocks to single-line bullets for readability. Content unchanged.

### How to Measure the Success of Platforms

- Minor formatting fix: collapsed a wrapped sentence in the metrics category intro paragraph.

### Capability Catalog Table

- Converted the HTML `<table>` to a Markdown table for improved readability and maintainability.
- **Identity and secret services**: Added **Keycloak** as an example project.
- **Web portals**: Removed "project templates" from the description (now covered under Golden path templates).
- Minor description cleanups across rows.

### Asset / Infrastructure Changes

- Fixed PDF link in the front matter: updated from `v1/assets/` path to `latest/assets/` path.
- Fixed image path for `platform_components.png`: updated from `assets/` to `../assets/` to resolve relative path correctly.
- The `v1.1/` subdirectory and its assets (PDF, diagrams, cover image) were created and then removed within this branch; the canonical content lives in `latest/`.
