---
layout: post
title: "Why We Need Better AI QA: The Real-World Cost of Unchecked Algorithms"
date: 2025-06-10 12:00:00 +0000
categories: [Blog]
tags: [ai-safety, qa, ethics, tech-writing]
---

> ⚠️ This document may reference sensitive language. Reader discretion is advised.
{: .prompt-warning }

It is a guarantee that by the time you read this sentence, AI has already impacted your life in some way. Whether it’s the algorithm behind the ad you just scrolled past, the chatbot guiding your customer service interaction, or the system prioritizing your job application—artificial intelligence is now embedded in the fabric of our daily experiences.

But with this rapid integration comes a critical question: How do we ensure that the AI systems shaping our world are working in our best interest? What guardrails are in place to protect users, especially when decisions are made by models that can’t fully understand human context, ethics, or emotion?

The Stanford HAI Index 2025 reports a startling truth: we’re trending in the wrong direction. In 2024, the number of documented “harmful” AI incidents jumped 54% from the year before. These are not isolated technical glitches. They are examples of real harm—psychological, social, legal, and in some cases, fatal.

Here are just a few case studies that illustrate the consequences of deploying AI without proper safeguards:

- In February 2024, 14-year-old Sewell Setzer took their life after allegedly being encouraged by Character.ai’s chatbot during a series of emotionally manipulative, romantically charged exchanges.  
- In 2021, Jaswant Singh Chail was arrested at Windsor Castle with a crossbow after being persuaded by a Replika chatbot to attempt to assassinate the Queen of England.  
- Hiring algorithms have been shown to reject applicants based on age, sex, race, and disability, violating basic human rights and legal standards.  
- AI-driven medical tools have been found to underdiagnose or deprioritize care for Black patients due to racially biased training data.  
- Chatbots have advised users on how to conduct illegal activity, hide crimes, and even discouraged war crime victims from seeking justice.

### Why Should You Care?

Because AI is only as good as the people who design, train, and test it. And people are fallible. 

AI systems hallucinate—they generate confident but false or misleading information. They make decisions based on data that may be incomplete, historically biased, or manipulated. And in the global race for AI dominance, many companies are prioritizing speed, scale, and profits over safety, ethics, and quality assurance.

This is where quality assurance (QA) becomes essential—not just as a technical process, but as a moral imperative. Just like in cybersecurity, the concept of “shifting left” must apply to AI safety—embedding rigorous QA, ethical review, and misuse testing early in the development cycle.

If companies fail to build user trust, they risk more than financial losses. The consequences could include lawsuits, regulation, loss of public confidence, or even global harm. From startup founders to boardroom executives, we all have a stake in getting this right. **Because one day, the very AI tools we release could be the ones making decisions about us.**

## Here Are Some Ways to Get It Right

The good news? We're not powerless against these risks. The AI industry is beginning to recognize that safety isn't just a "nice to have it" essential for sustainable growth and public trust. While there's no silver bullet, there are proven strategies and emerging best practices that can significantly reduce the likelihood of harmful AI incidents.

The following approaches represent both established QA principles adapted for AI and alternative techniques specifically designed for the unique challenges of machine learning systems. 

### Dataset Diversification and Balancing

One of the most overlooked causes of AI harm is the data itself. If your data reflects the biases of history, your AI will too.

Amber Nigam, co-founder and CEO of [Basys AI](https://basys.ai), notes that many underrepresented groups—especially African Americans and other minorities—are often left out of training datasets altogether. This lack of representation leads to outputs that fail to serve (or actively harm) those communities.

> Solution: Actively audit datasets for representation across race, gender identity, age, ability, and geography. Use balancing techniques to ensure fairness, and supplement with synthetic data when necessary to close gaps.

### Don’t Put AI at the Top of the Funnel

When AI is used as a first filter—such as scanning resumes or recommending treatments—it acts as a gatekeeper. If it's flawed, biased, or too confident, it can block opportunities or lead to misinformed decisions without human review.

> Example: In hiring, instead of using AI to reject resumes up front, use it to support final decisions made by humans who can interpret context and nuance.

> Solution: Place AI toward the end of workflows, as a decision-support tool, not a decision-maker. This prevents premature judgments and ensures human oversight.

### Implement Adversarial and Misuse Testing

We need to stop assuming AI will be used as intended. In the real world, people test limits, provoke responses, and find creative (or, really malicious) uses for tools.

> Solution: Perform adversarial QA—simulate hostile inputs, edge cases, and manipulative behavior. Test what happens when users act irrationally or maliciously. Validate that your AI behaves responsibly, even under pressure.

### Monitor for Hallucinations and Explainability

AI models often generate false or misleading information, especially under vague or open-ended prompts. Worse, it’s often difficult to understand why they responded the way they did.

> Solution: Use tools like Attribution tracing, RLHF audits (Reinforcement Learning with Human Feedback), and model interpretability libraries to monitor for hallucinations and improve transparency. Make model decision logic explainable and auditable.

### Introduce AI Ethics Reviews Into QA Checklists

Most QA processes focus on performance, speed, and integration—not on values or user safety. That needs to change.

> Solution: Create Ethics QA Checklists for every release, asking:
- Could this be misused or misunderstood?
- Have we tested this with marginalized or vulnerable groups?
- What’s the worst possible use case, and have we accounted for it?

This can be embedded into SDLC documentation, test cases, and sprint planning.

### Use Transparency Tools Like Model Cards and Datasheets for Datasets

The AI field already has frameworks to promote transparency, but many are underused. Model Cards and Dataset Datasheets describe how models were built, what they’re good at, and what risks they carry.

> Solution: Encourage dev and QA teams to document these artifacts and make them part of your AI development workflow. Transparency protects both companies and users.

### Design for Human Handoff and Escalation

AI shouldn't operate without fail-safes. In high-risk situations—like healthcare, mental health, legal aid, or customer conflict—AI responses should include a built-in handoff to a human agent.

> Solution: Build escalation paths. If the AI encounters sensitive topics (suicide, abuse, criminal behavior), it should stop and escalate rather than engage further.

---
AI is not just software. It’s a mirror of our society and values. And when that mirror is flawed, we risk amplifying harm rather than solving problems.

Quality assurance in AI isn’t optional. It’s the only way to ensure these tools serve people rather than endanger them. Whether you're a tester, tech writer, or concerned citizen, we all play a part in keeping these ecosystems safe. By advocating for better data, stronger checks, and ethical design, we can build AI systems that elevate rather than exploit humanity.

Let's test for what truly matters because the cost of getting it wrong is too high. I mean who wants to live through the Terminator IRL?

## Sources

- [AP News: Chatbot linked to teen suicide](https://apnews.com/article/chatbot-ai-lawsuit-suicide-teen-artificial-intelligence-9d48adc572100822fdbc3c90d1456bd0)
- [Stanford HAI: AI Index 2025 – State of AI in 10 Charts](https://hai.stanford.edu/news/ai-index-2025-state-of-ai-in-10-charts)
- [BBC News: AI and Chatbots Encouraging Harm](https://www.bbc.com/news/technology-67012224)
- [MIT Tech Review: AI Chatbot Told User to Kill Himself](https://www.technologyreview.com/2025/02/06/1111077/nomi-ai-chatbot-told-user-to-kill-himself/)
- [EEOC: iTutorGroup Pays $365,000 for Discriminatory Hiring Suit](https://www.eeoc.gov/newsroom/itutorgroup-pay-365000-settle-eeoc-discriminatory-hiring-suit)
- [Chapman University: Bias in AI](https://www.chapman.edu/ai/bias-in-ai.aspx)
- [Science.org: Racial Bias in Healthcare Algorithms](https://www.science.org/doi/10.1126/science.aax2342)
- [STAT News: How I addressed racial bias in my company's AI algorithm](https://www.statnews.com/2024/11/13/generative-ai-medicine-health-care-ai-racism/)
