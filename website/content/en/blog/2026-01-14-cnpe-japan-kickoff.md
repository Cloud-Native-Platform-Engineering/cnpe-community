---
title: "Cloud Native Platform Engineering Japan Kickoff in Japan!"
slug: cnpe-japan-kickoff
date: 2026-01-14
author: Ken Komazawa (Red Hat)
categories:
- Article
tags:
- Event
- Platform Engineering
- Community
---

Hello, everyone.
I'm Ken Komazawa, Chief Architect at Red Hat.

Today, I'd like to share details about the Cloud Native Platform Engineering Japan Kickoff held on December 8th.
This marks the **first** event of its kind in Japan organized by the CNCF community focused on platform engineering.

This event is organized by Cloud Native Platform Engineering Japan, a SIG of Cloud Native Community Japan ([CNCJ](https://community.cncf.io/cloud-native-community-japan/)), which is the Japanese chapter of the CNCF.
The group's mission is to "spread awareness about platform engineering from the CNCF's perspective!
Let practitioners gather to share insights, collaborate closely with upstream projects, and connect Japan with the world!"

I am also participating as one of the organizers.
As shown in the slide below, it was announced at the LF Japan Community Days on October 21st.

![Announcement slide at LF Japan Community Days](/images/cnpe-japan-kickoff/announcement.png)

The story for launching this community began with a conversation between Nakamura-san, Head of OSPO at Hitachi and a member of the CNCF Governing Board, and Vincent, APAC CTO at Red Hat.
They discussed how platform engineering activities in Japan and Asia lagged behind those in Europe and the US, concluding that establishing a dedicated community in Japan would be beneficial.
That's how Nakamura-san and I connected.

Coinciding with the launch of the CNCF's platform engineering certification, [CNPA](https://training.linuxfoundation.org/ja/certification/certified-cloud-native-platform-engineering-associate-cnpa/) (Cloud Native Platform Engineering Associate), I approached Nakamura-san with the idea, "Why don't we localize it into Japanese?"
This sparked our communication, and this group came together to volunteer and drive forward such activities.

Hayakawa-san from LINE Yahoo has been involved in the CNCF Platform Engineering Technical Community Group from early on and also had connections to the domestic community in Japan (Platform Engineering Kaigi/Meetup), so he serves as the leader of this group.

Tabata-san from Hitachi is also a Keycloak committer and actively promotes the community in security fields like the CNCF TAG Security and Compliance.
He joined this community, leveraging his operational experience.
(He is also a CNCF Ambassador.)

Furthermore, Matsuda-san from Hitachi is a Kubestronaut (a superhuman holding all Kubernetes certifications) and enthusiastically joined, eager to contribute to this community!
(He is the only Kubestronaut in the Chugoku region of Japan!)

Okabe-san is a university student and a Mercari intern, but he was the driving force behind this project's planning and execution, pushing things forward energetically.
Okabe-san is also a CNCF Ambassador and a leader with a strong presence in the OSS community.

And after this event, we even had Aoyama-san from CyberAgent join us!
With Aoyama-san—who also organizes events like Kubernetes Meetup and Cloud Native Days—participating, our community operations team has become even stronger.

What should I do among such diverse and talented members!?

I serve as an architect at Red Hat.
As an ambassador for Japan, I believe I can take on the role of promoting "[The Open Source Way](https://www.theopensourceway.org/)"—the approach Red Hat has practiced to build a business around open source.
The Open Source Way, a development model that drives developer innovation through open decision-making while enhancing transparency, should be highly compatible with platform engineering—which maximizes developer experience as an internal platform.

While working at Red Hat, this approach to organizational management and mindset can start to feel like second nature.
Yet putting it into practice is extremely challenging, and much of it remains tacit knowledge, largely unknown outside the company.
I hope to use this community to share how Red Hat has developed software and coexisted with the open source community.

That was a long introduction, but I'd like to briefly introduce the event's content.

## Keynote

Vincent delivered the keynote titled "Bridging the Gap".
His message was that platform engineering activities, grounded in both internal and external community initiatives, will shape the future of software development in Japan.
The challenges of IT talent shortages and skill gaps within end-user companies are more severe compared to Europe and the US.
To improve this, companies should advance internal "innersource" activities (activities that openly share knowledge within the company to build collective intelligence).
As one key measure for this, the Internal Developer Platform (IDP) becomes crucial.

![Vincent's keynote](/images/cnpe-japan-kickoff/keynote-1.jpg)
![Vincent's keynote slide](/images/cnpe-japan-kickoff/keynote-2.jpg)

## Platform Engineering from CNCF's Perspective

Next, Hayakawa-san from LINE Yahoo introduced platform engineering from the CNCF's perspective.
CNCF provides resources such as the Platforms Whitepaper, which outlines the role, value, and measurement methods of platform engineering, along with how to establish platform teams; a Maturity Model to review platform outcomes and identify improvement opportunities; and a certification program for platform engineering.
In this way, CNCF is a community that shares the foundational knowledge and theory for practicing platform engineering, supporting the formation of common understanding and best practices within the cloud-native field.

Hayakawa-san serves as the Product Owner for his company's internal platform.
Drawing on his in-house experience, he actively provides feedback to the CNCF and shares insights within the community.
His discussions are highly persuasive, grounded in practical experience with mission-critical infrastructure at his company, including best practices for multi-tenant operations in Kubernetes and infrastructure automation.

![Hayakawa-san's presentation](/images/cnpe-japan-kickoff/hayakawa-1.jpg)
![Hayakawa-san's presentation slide](/images/cnpe-japan-kickoff/hayakawa-2.jpg)

## Avoiding Pitfalls When Adopting Gateway API: Secure-by-Default Design Achieved with Kuadrant and Keycloak

Next, Matsuda-san from Hitachi gave a technical presentation titled "Avoiding Pitfalls When Adopting Gateway API: Secure-by-Default Design Achieved with Kuadrant and Keycloak".
He explained Kubernetes architecture by personifying it as a family structure, making it both easy to understand and enjoyable.

![Matsuda-san's presentation slide](/images/cnpe-japan-kickoff/matsuda-1.jpg)

In increasingly complex platforms, it is crucial that security is built in from the design phase.
How can we clearly communicate to engineers how the Kubernetes ecosystem addresses security challenges?
I believe this is one of the most critical tasks within the domain of platform engineering.

Matsuda-san is a Kubestronaut (the only one in the Chugoku region of Japan).
He provides such clear explanations through his blog and other channels, making him an incredibly valuable and reassuring team member.

![Matsuda-san's presentation](/images/cnpe-japan-kickoff/matsuda-2.jpg)

## The Evolution of Platform Engineering at Mercari

Finally, Rafael, Engineering Manager of the Engineering Enablement group at Mercari, gave a presentation on the evolution of platform engineering at Mercari.

He specifically outlined the challenges and countermeasures in platform engineering efforts from 2018 to the present.
He explained that the platform team needed to become an enabler focused on developer success, not just a tool provider.
To foster an inner-source culture, they shifted to a structure where domain expert teams lead the community, ensuring the platform team itself doesn't become a bottleneck.

Mercari, where Okabe-san works, has achieved a culture distinct from typical Japanese organizations.
This makes it a highly insightful experience for other companies to learn from.

![Rafael's presentation slide](/images/cnpe-japan-kickoff/rafael-1.jpg)
![Rafael's presentation](/images/cnpe-japan-kickoff/rafael-2.jpg)

## Summary

This kickoff meeting covered the content described above.

For Japanese engineers, this kickoff aimed to pose the question: "What kind of impact can platform engineering activities have?"

As part of your company's business activities, platform engineering can serve as a powerful driving force.
Let's not only accumulate this experience internally as inner-source activities, but also share it externally.
Doing so creates a positive feedback loop: it contributes positively to the open-source community (outer-source), which is recognized as enhancing your corporate brand, ultimately benefiting your company.

We ask for your continued cooperation to keep energizing this community!

## Bonus: A Thinking Framework for Platform Engineering

Below is my perspective on the overall landscape of platform engineering.
I see three overlapping problem domains: "Platform as a Product", which treats internal platforms as products; "Platform as Engineering", which views them as an extension of software engineering; and "Platform as Organization & Architecture", which considers them as organizational and architectural challenges.
By framing it this way, I believe we can position platform teams as core functions within corporate strategy and design, enabling the planning of investments.

![Platform engineering overview](/images/cnpe-japan-kickoff/framework.png)

Below is a list of excellent books to guide you.
The three logos at the bottom represent open-source practice communities based on Red Hat's experience.
If you can adapt and implement the ideas and practices they convey to suit your own company, you should be able to build a platform that maximizes your business value.

![Reference books list](/images/cnpe-japan-kickoff/books.png)

Let's all practice platform engineering together!
