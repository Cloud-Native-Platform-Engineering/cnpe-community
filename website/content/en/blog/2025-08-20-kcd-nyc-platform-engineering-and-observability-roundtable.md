---
title: "From Chaos to Clarity: Navigating Observability in the Platform Engineering Era (and a Dash of AI)"
slug: kcd-nyc-platform-engineering-and-observability-roundtable
date: 2025-08-20 12:00:00 +0000
author: Graziano Casto
categories:
- Article
tags:
- Community Contributions
---

> There was a great energy at KCD New York this year, and for Graziano Casto, a personal highlight was leading a roundtable on observability. It was a fascinating discussion that really got him thinking about the challenges we're all facing in the platform engineering space. Here is Graziano's recap of the key problems and promising ideas that came up.

## Introduction

It was an absolute pleasure recently to moderate a roundtable at [KCD New York](https://community.cncf.io/events/details/cncf-kcd-new-york-presents-kcd-new-york-2025/), diving deep into the fascinating (and let's be honest, sometimes frustrating) world where **Platform Engineering meets Observability**. As my first time moderating a roundtable, I was genuinely thrilled by the energy and candid participation from everyone in the room. A huge thank you to all the participants: [Michel Murabito](https://www.linkedin.com/in/mich-murabito/), [Colin Lacy](https://www.linkedin.com/in/colinjlacy/), [Tiara Sykes](https://www.linkedin.com/in/tiara-sykes/), [Andrew Espira](https://www.linkedin.com/in/andrew-espira/), [Mariia Rudenko](https://www.linkedin.com/in/mariia-r-748931163/), [Aderianna Williams](https://www.linkedin.com/in/at-williams/), [Marino Wijay](https://www.linkedin.com/in/mwijay/), and [Maria Ashby](https://www.linkedin.com/in/maria-ashby/) whose insights made this discussion truly invaluable. We had an incredibly insightful exchange, and I walked away with some serious food for thought.

<img src="../assets/kcd-nyc-pe-roundtable.jpeg" width=400px />

We kicked off by acknowledging a universal truth in today's cloud-native landscape: managing a full observability stack often feels like trying to hit a moving target. The more we aim to observe, the more inherent complexity seems to creep in. We continuously pile on tools, data, and dashboards--be it metrics, traces, logs, or profiling – and suddenly, we're swimming in a sea of cognitive load, entropy, and quite often, plain old confusion. So, instead of me listing the common headaches, I threw it open to the room: "When you think about managing a full observability stack, across logs, metrics, traces, and so on, what are your biggest pain points? If you had to name the biggest challenge your team is facing with observability right now, what would it be?"

The responses flowed freely, revealing a shared understanding that while observability promises clarity, its real-world implementation often introduces its own unique set of challenges. And, quite organically, our conversation drifted into the exciting (and slightly unsettling) realm of Generative AI, specifically discussing how Large Language Models (LLMs) can be synergistically integrated within platforms to serve as enablers in resolving some of these very challenges.

## The Observability Headaches: Where Do We Feel the Pinch?

One of the loudest points of contention was the persistent struggle to correlate telemetry data with the actual services generating them, and the broader challenge of **telemetry data correlation**. It's like having all the pieces of a complex puzzle but no clear idea how they fit together. You might spot a spike in CPU utilization – a metric – but then you're left guessing which microservice is the culprit. Then begins the detective work: diving into logs to pinpoint an error, and finally tracing requests to understand the flow. The fundamental problem is that these critical data points often reside in disparate systems, use inconsistent identifiers, and demand a significant amount of manual effort and intuition to connect the dots. This fragmentation makes it incredibly difficult to quickly identify the root cause of a problem when seconds count.

Adding to this complexity is the sheer volume of alerts and the difficulty in correlating them with the actual underlying problem. We've all experienced it: a dozen alerts fire simultaneously, each pointing to a symptom, yet none clearly indicating the core issue. This leads to what's known as **alert fatigue**, resulting in missed critical incidents, wasted time triaging false positives, and ultimately, a palpable loss of trust in the alerting system itself. The challenge isn't merely about receiving notifications; it's about receiving meaningful alerts that directly pinpoint the underlying problem, not just its outward manifestations.

Furthermore, a significant unspoken burden that often comes with observability is the **cost** of both creating and maintaining the entire observability stack. From licensing fees for proprietary tools to the infrastructure costs of storing massive volumes of telemetry data and the operational overhead of managing these complex systems, the financial outlay can be substantial. This constant investment of resources, both human and monetary, can become a major pain point, often weighing heavily on budget decisions and resource allocation.

Then there's the pervasive issue of **making insights accessible** and visualizing them in a way that provides the right insight to the right person. Raw telemetry data, in its unadulterated form, is overwhelming. Different roles within an organization – SREs, developers, product managers – need distinct views and varying levels of detail. A developer might require granular trace data, while a product manager needs high-level business metrics. The constant battle involves creating and maintaining these tailored dashboards and ensuring everyone knows where to find what they need. This often leads to information silos and missed opportunities for proactive improvement.

A recurring theme throughout our discussion was the persistent problem of **siloed teams** and the resulting **lack of standardization**. When different teams adopt disparate observability tools, inconsistent naming conventions, or even varied logging formats, it inevitably creates a fragmented and chaotic landscape. This makes it incredibly challenging to gain a holistic view of the system, collaborate effectively during incidents, and leverage best practices across the entire organization. It’s a classic case of "everyone doing their own thing", leading to pervasive inefficiencies and increased complexity.

Finally, a crucial point that resonated deeply was the importance of **developer education**. Observability isn't merely about deploying tools; it's about cultivating a specific mindset. Developers need to grasp why observability is vital, how to effectively instrument their code, how to interpret telemetry data, and critically, how to leverage observability tools to troubleshoot their applications. This knowledge gap can lead to poorly instrumented services, ignored alerts, and a general underutilization of the powerful observability stacks organizations invest heavily in.

## Internal Developer Platforms: The Unified Solution

So, with these common headaches laid out, how do we begin to alleviate them? This is precisely where the concept of an **Internal Developer Platform (IDP)** steps in as a truly powerful solution, providing a cohesive answer to many of these challenges.

An IDP, at its core, inherently solves the problem of standardization. By providing clear standards and abstractions through "golden paths" for building and deploying applications, it ensures consistency across the organization. However, it's crucial that these **golden paths** don't become "golden cages". A well-designed IDP empowers developers with the necessary autonomy to cover edge cases, allowing them to step outside the perimeter of the provided golden paths when needed for specific requirements. This balance is vital for both consistency and innovation.

Moving beyond standardization, IDPs also play a crucial role in addressing the challenges faced by siloed teams that might be working on different components of the same system and often lack a shared performance baseline. During our discussion, we introduced the concept of leveraging generative models within these platforms. Specifically, the role of Generative AI, particularly **Large Language Models (LLMs)**, in the observability space emerged as a truly futuristic and exciting prospect. The idea is that LLMs can help close the gap between users and telemetry data. Imagine being able to ask natural language questions like, "Why is our checkout service slow right now?" and have an LLM sift through mountains of metrics, logs, and traces to provide a concise, actionable answer. Or, "What were the top 3 errors in our authentication service last night?" and get a summary, perhaps even with links to relevant log lines. These models can also be instrumental in enabling teams to define and compare their telemetry data against customized thresholds, ensuring that the entire system is monitored according to a collectively defined baseline, fostering a shared understanding of system health.

From here, we delved into how these models further enhance the transparency and clarity of insights. LLMs, integrated within the IDP, can analyze vast amounts of telemetry data and provide various stakeholders with personalized insights and alerts. This capability opens the door to entirely new interfaces beyond the traditional dashboards, making complex operational data more accessible and actionable for different roles. Unfortunately, we didn't have the opportunity to delve deeper into the intricate topic of telemetry data correlation during the roundtable, but I have written an article that explores this topic further, which you can find [here](https://www.linkedin.com/pulse/9-serving-observability-first-dish-graziano-casto-05rhf).

## The Open Question: Balancing Trust and Cost with Benefits in the LLM Era

However, as with any powerful new technology, the discussion around LLMs quickly led to a critical open question for the community:

**How do we effectively balance the significant benefits that LLMs bring – such as improved automation and deeper insights – against the inherent costs? These costs include not only the economic investment required for these models but also the crucial aspect of trust, both in the accuracy of the results and in entrusting our sensitive data to an LLM, particularly when utilized as a service.**

This is a conversation that needs to continue. As we push the boundaries of what's possible with AI in operations, we must collectively figure out how to build systems that are not only efficient and intelligent but also fundamentally secure, trustworthy, and cost-effective.

## Wrapping Up

My first moderating experience at KCD New York was an absolute blast, and the insights from the roundtable on Platform Engineering and Observability were truly invaluable. It's clear that while observability brings its own set of complexities, Internal Developer Platforms offer a robust framework for overcoming these challenges by promoting standardization, providing contextualized insights, and empowering developers. And looking ahead, the potential of LLMs to revolutionize how we interact with our telemetry data is incredibly exciting, even if it comes with some important questions we need to answer as a community.

What are your thoughts on these challenges and solutions? And how do you see the role of LLMs evolving in the observability space, especially concerning the trust and cost trade-offs? Let's keep the conversation going!
