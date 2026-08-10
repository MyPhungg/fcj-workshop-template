---
title: "AWS FCAJ Agent Forge - Deepdive Day 2"
date: 2026-08-04
weight: 3
chapter: false
pre: "<b> 4.3. </b>"
---

### Report on “AWS FCAJ Agent Forge - Deepdive Day 2”

### Event Objectives

The **AWS First Cloud AI Journey – Agent Forge Deep Dive 2026** event focused on **Personalization, Evaluation & Optimization**, with the main content centered around **Advanced Amazon Bedrock AgentCore**.

The event helped participants:

- Learn about career development directions for Cloud and AI engineers.
- Gain a better understanding of AI Agent architecture and its components.
- Learn how to use Memory to build Agents with memory and personalization capabilities.
- Explore Observability capabilities for monitoring Agent activities.
- Learn about AgentCore Evaluations to assess Agent quality and effectiveness.
- Explore components such as Registry, Harness, Tools, Payments, Optimization, and Policy.
- Gain hands-on experience building and configuring AI Agents through the **Vibe Coding** approach.

In particular, the hands-on session was guided in detail by **Anh Pham – Cloud Consultant, G-AsiaPacific Vietnam**, helping participants move from theoretical understanding to directly building and experimenting with Agents.

---

### Speakers

- **Nghia Tran** – Agentic SA
- **Anh Pham** – Cloud Consultant, G-AsiaPacific Vietnam

The presentations of the two speakers complemented each other. **Nghia Tran** focused on career development, AI system design thinking, and important AgentCore concepts. Following this, **Anh Pham** focused on the hands-on section, guiding participants step by step in building and experimenting with AI Agents using Vibe Coding.

---

### Key Topics

### 1. Career Development Insights from Mr.Hieu

#### Depth and Breadth in Career Development

One of the notable topics in **Hieu's** presentation was the concept of **depth** and **breadth** in the career development of a technology engineer.

According to the speaker, an engineer does not necessarily have to choose completely between specializing deeply in one field and having knowledge across multiple fields. Instead, career development can be approached progressively through different stages.

- In the early stage, engineers can focus on building **deep expertise** in a particular field.
- They can then expand their knowledge by learning how to deploy applications in **Production** environments.
- Once they have a strong technical foundation, engineers can develop greater **breadth**, such as knowledge of Networking, Security, Cost Optimization, or domain-specific knowledge.

This approach helped me realize that a Cloud or AI engineer not only needs to know how to program or use a specific service, but also needs to understand how different components work together to form a complete system.

#### Necessary and Sufficient Conditions for Engineers

The speaker also discussed the difference between **necessary conditions** and **sufficient conditions** for an engineer.

**Necessary conditions** can be supported by AWS certifications. Certifications help engineers build foundational knowledge and demonstrate their ability to work with Cloud technologies.

However, **sufficient conditions** are not limited to certifications but also involve the ability to deploy an application into a real-world environment.

An engineer needs to be able to:

- Design systems.
- Deploy applications to Production environments.
- Optimize costs.
- Ensure security.
- Set up monitoring systems.
- Monitor and troubleshoot issues.
- Ensure system operation and scalability.

This helped me understand more clearly that an application running successfully does not necessarily mean that the system is ready for Production.

#### Soft Skills and Ownership Mindset

In addition to technical skills, the speaker emphasized the importance of **soft skills** for technology engineers.

An engineer needs to be able to:

- Communicate effectively with people without a technical background.
- Work and communicate in a business environment.
- Proactively investigate and solve problems.
- Participate in technology communities.
- Share and exchange knowledge with others.

In particular, the speaker emphasized the **Ownership Mindset** – a proactive attitude and sense of responsibility toward one's work.

Instead of simply completing assigned tasks, engineers should proactively investigate the root causes of problems, propose solutions, and follow up on the results until the issue is resolved.

This is a lesson that I believe can be directly applied to my learning process and teamwork in software projects.

#### Safe and Responsible Use of AI

As AI becomes increasingly common, the speaker also discussed the importance of **Responsible AI**.

Using AI should not focus only on generating results more quickly but should also take into consideration:

- Information accuracy.
- Safety.
- Data security.
- Privacy.
- Risks associated with relying on AI-generated results.
- Human responsibility for reviewing and using the results.

Through this topic, I realized that AI should be viewed as a tool to support humans rather than completely replacing human thinking and verification.

#### AI Opportunities and Market in Vietnam

The speaker also shared insights into the rapid development of the AI market in Vietnam.

AI is creating many opportunities in areas such as:

- Logistics.
- EdTech.
- Healthcare.
- Developer Tools.
- Finance.
- Enterprise applications.

In addition to self-learning, the speaker encouraged young engineers to participate in technology communities such as **FCAJ** and **Hackathons** to gain hands-on experience, learn from experienced professionals, and turn knowledge into real-world products.

---

### 2. Understanding Memory in AI Agents

#### Basic Agents and Agents with Memory

One of the important topics of the program was the difference between a **basic Agent** and an **Agent with Memory**.

A basic Agent typically processes each request based on the current information or the conversation history available within the provided context.

In contrast, an Agent with Memory can retain important information from previous sessions and reuse this information when the user returns.

For example, a shopping assistant Agent may remember:

- Brands the user is usually interested in.
- Preferred colors.
- Product sizes.
- User preferences.
- Choices made during previous interactions.

As a result, the Agent can provide a more personalized interaction experience.

#### Challenges of Building Memory from Scratch

When building a Memory system from scratch, developers need to address many challenges:

- Designing the storage system.
- Synchronizing data.
- Extracting important information from conversations.
- Retrieving relevant information.
- Managing the context window.
- Controlling token usage.
- Optimizing costs.
- Ensuring scalability.
- Managing and operating the system.

Therefore, building the entire Memory mechanism from scratch can significantly increase system complexity.

#### Amazon Bedrock AgentCore Memory

**Amazon Bedrock AgentCore Memory** provides mechanisms to support information storage and retrieval for Agents, reducing the amount of infrastructure that developers need to build themselves.

The Memory architecture introduced in the event consists of several main components.

#### Short-Term Memory – STM

**STM (Short-Term Memory)** stores information for a short period of time, such as:

- Raw chat messages.
- Events that occur during a session.
- The context of the current conversation.

#### Memory Extraction Module

This component is responsible for extracting important information from conversation data.

Instead of storing the entire conversation for future use, the system can identify information that has long-term value.

For example:

- The user frequently chooses a particular brand.
- The user prefers a specific color.
- The user frequently uses a particular product size.

#### Long-Term Memory – LTM

**LTM (Long-Term Memory)** stores extracted information so that the Agent can use it in future interactions.

This information can be represented as vectors, allowing the Agent to search for and retrieve relevant information when the user returns after a long period of time.

Through this section, I gained a clearer understanding that Memory is not simply about storing the entire conversation history. It also involves the process of **extracting, storing, and retrieving information that is valuable to the Agent**.

---

### 3. AgentCore Observability

Another important topic introduced during the event was **AgentCore Observability**.

For an AI Agent, knowing only the final answer is not enough. During operation, developers need to understand which steps the Agent performed, which tools it used, and what the processing status was.

AgentCore provides mechanisms for monitoring Agent activities through:

- Logs.
- Traces.
- Tool invocation.
- Processing status.
- Steps performed by the Agent while completing a task.

This approach has several similarities to using **Amazon CloudWatch** to monitor traditional AWS systems.

Observability is particularly important when deploying AI Agents into Production.

For example, if an Agent produces an inaccurate result, the Observability system can help developers investigate:

1. How the Agent received the input.
2. Which Tool the Agent selected.
3. Whether the Tool returned accurate data.
4. Whether an error occurred during processing.
5. How the final output was generated.

This makes debugging and improving the Agent easier.

---

### 4. Evaluating Agent Quality with AgentCore Evaluations

An AI Agent needs to be evaluated regularly to determine the quality of its performance.

**AgentCore Evaluations** supports measuring and evaluating Agent effectiveness based on predefined criteria.

One of the methods introduced was **LLM-as-a-Judge**, in which another language model can act as a "judge" to evaluate the Agent's output.

Evaluation criteria may include:

- Accuracy.
- Relevance to the requirements.
- Answer quality.
- Compliance with rules.
- Ability to complete tasks.

This allows the Agent development process to follow a continuous loop:

**Measure → Identify Problems → Improve → Re-evaluate**

Instead of relying solely on the developer's subjective assessment, Agent quality can be evaluated based on more specific criteria.

---

### 5. Main Components of AgentCore

The presentation introduced various components that support the development and operation of AI Agents.

Key functions include:

- **Memory:** manages the Agent's information and long-term context.
- **Observability:** monitors and tracks Agent activities.
- **Evaluations:** evaluates Agent quality.
- **Tools:** allows the Agent to interact with external tools and systems.
- **Session Management:** manages working sessions.
- **Runtime Execution:** provides an execution environment for the Agent.

In addition, the program introduced components such as:

- Registry.
- Harness.
- Payments.
- Optimization.
- Policy.

Through this, I realized that a complete AI Agent system is not simply an LLM model. It also requires multiple supporting components to operate reliably and securely.

### Basic Components for Setting Up an Agent

Building an Agent can focus on three main components:

#### LLM Model

Selecting a suitable foundation model based on requirements for:

- Processing capability.
- Response speed.
- Cost.
- Intended use.

#### System Prompt

The System Prompt defines:

- The Agent's role.
- Tasks.
- Response behavior.
- Rules.
- Limitations that the Agent must follow.

#### Tools & Skills

Tools & Skills provide the Agent with the ability to perform tasks beyond text generation.

Examples include:

- Calling APIs.
- Querying data.
- Performing actions on systems.
- Using external tools.

---

### 6. Hands-on Lab

#### Hands-on Guidance from Anh Pham

After the theoretical presentations, the program moved to the **Hands-on Lab**, directly guided by **Anh Pham – Cloud Consultant, G-AsiaPacific Vietnam**.

This was the part of the program that I valued highly because the content did not stop at introducing concepts. Instead, the speaker provided **very detailed step-by-step practical guidance**.

The hands-on session used the **Vibe Coding** approach, in which AI is used as an assistant throughout the development process.

Instead of having to write all the source code from scratch, developers can describe requirements in natural language and use AI to assist with:

- Creating the initial structure.
- Generating source code.
- Explaining code.
- Detecting errors.
- Fixing errors.
- Adjusting functionality.
- Experimenting with different implementation approaches.

Through the hands-on session, I realized that Vibe Coding can significantly shorten the time from forming an idea to creating a working Prototype.

#### Building an Agent

The speaker guided participants step by step through the process of building an AI Agent.

The hands-on session helped participants better understand the relationship between:

**LLM Model → System Prompt → Tools & Skills → Agent Runtime**

Instead of simply watching a prepared Demo, participants could follow the process of building and configuring the Agent.

This made the concepts presented in the theoretical section more visual and easier to understand.

#### Adding Memory to the Agent

One of the practical activities involved adding **Memory** to the Agent.

This allowed participants to observe the differences between:

- An Agent that only processes the current request.
- An Agent that can remember user information.
- An Agent that can reuse remembered information in subsequent interactions.

This hands-on activity helped me better understand the meaning of STM, Memory Extraction, and LTM presented in the theoretical section.

#### Practicing Agent Observability

The speaker then guided participants through exploring **Agent Observability**.

Instead of only looking at the final answer, participants could observe how the Agent processed a request.

This provided a clearer understanding of:

- Which steps the Agent performed.
- Which Tools the Agent called.
- The processing status.
- Which information could be used for debugging.

This helped me realize that Observability is a very important component when deploying AI Agents into Production environments.

#### Practicing AgentCore Evaluations

The next section was an experience with **AgentCore Evaluations**.

Participants learned how to evaluate Agent quality instead of simply checking results through manual observation.

This is important because AI is inherently variable. An Agent may produce good results in some cases but cannot be guaranteed to operate accurately in every situation.

Building an Evaluation mechanism provides a clearer foundation for continuously improving the Agent.

#### Exploring AgentCore Harness

The hands-on session also introduced and guided participants in exploring **AgentCore Harness**.

Through the direct guidance, participants gained a clearer understanding of how supporting Agent components can be combined during the development of a complete system.

What I appreciated most about the Hands-on session was that **Anh Pham provided very detailed guidance and closely followed the practical process**, from starting to build the Agent, configuring its components, using Vibe Coding, to checking the results.

This was especially useful for people who were new to AgentCore because they could listen to explanations while following each step instead of only receiving theoretical knowledge.

---

### Key Takeaways

#### Career Development Mindset

- Understand the balance between **depth and breadth** in an engineer's career development.
- Realize that certifications are only a foundation, while the ability to deploy and operate real-world systems is more important.
- Understand the importance of Production, Security, Cost Optimization, and Observability.
- Gain greater awareness of the **Ownership Mindset** and the importance of being proactive at work.
- Understand that communication skills and the ability to work with non-technical people are also important.

#### AI Agents

- Gain a better understanding of AI Agent architecture.
- Understand the difference between an Agent with Memory and a basic Agent.
- Understand how STM and LTM support memory capabilities.
- Learn about the role of Memory Extraction in extracting important information.
- Understand the role of Tools and Skills in expanding an Agent's capabilities.
- Recognize the importance of Session Management and Runtime Execution.

#### Observability and Evaluation

- Understand that AI Agents need to be monitored similarly to traditional software systems.
- Learn the role of Logs and Traces in debugging Agents.
- Understand how Observability helps track Tool Invocation and Agent operating status.
- Understand the concept of **LLM-as-a-Judge** for evaluating outputs.
- Recognize that Agent evaluation needs to be performed continuously throughout the development process.

#### Vibe Coding

The hands-on session gave me additional experience with **Vibe Coding** and how AI can be used as an assistant during software development.

I realized that Vibe Coding can:

- Accelerate the Prototype creation process.
- Support faster code development.
- Assist with debugging.
- Help experiment with multiple ideas in a short period of time.
- Reduce the time spent on repetitive programming tasks.

However, programmers still need to understand the fundamentals in order to verify, evaluate, and take responsibility for AI-generated results.

---

### Application to Work

The knowledge gained from the event can be applied to future Cloud and AI projects.

#### For Software Development

- Use AI to support the programming process.
- Leverage Vibe Coding to quickly build Prototypes.
- Use AI to assist with debugging and error analysis.
- Review code and results generated by AI before using them.

#### For Cloud Systems

- Consider Production operational requirements from the system design stage.
- Design systems with Logging and Observability.
- Pay attention to Security.
- Optimize Cloud usage costs.
- Design systems with scalability in mind.

#### For AI Agents

In future projects, I can apply:

- **Memory** to personalize Agents.
- **Tools** to allow Agents to interact with external systems.
- **Observability** to monitor Agent activities.
- **Evaluations** to measure Agent quality.
- **Policy** to control Agent behavior.
- **Vibe Coding** to accelerate Prototype development.

---

### Event Experience

Participating in the **AWS First Cloud AI Journey – Agent Forge Deep Dive 2026** event gave me a clearer understanding of current AI Agent development trends and how to build an Agent system in a practical way.

#### Learning from Experts

The presentation by **Nghia Tran** gave me additional perspectives on the career development of engineers in the AI era.

The topics of **depth, breadth, Production, Responsible AI, and Ownership Mindset** helped me understand that engineers need to develop both technical expertise and soft skills.

#### Understanding Amazon Bedrock AgentCore

Through the theoretical sessions, I gained a better understanding of the components required to build a complete AI Agent.

In particular, I gained additional knowledge about:

- Memory.
- Observability.
- Evaluations.
- Tools.
- Session Management.
- Runtime Execution.
- Harness.
- Policy.
- Optimization.

#### Hands-on Experience

The hands-on session guided by **Anh Pham** was the part I found most useful.

The speaker not only introduced the features but also **provided very detailed step-by-step guidance**, allowing participants to follow along and practice at the same time.

Using **Vibe Coding** during the hands-on session also helped me better understand how AI can become a programming assistant, supporting everything from building the initial structure and writing code to fixing errors and testing functionalities.

In particular, directly experiencing Memory, Observability, Evaluations, and Harness helped me better understand the relationship between these components within a practical Agent system.

---

### Lessons Learned

Through the event, I gained several important lessons:

- AI technology is developing very rapidly, so the ability to learn and adapt is an important factor for software engineers.
- An engineer not only needs to know how to build applications but also needs to understand how to deploy applications into Production environments.
- AWS certifications provide a good foundation but need to be combined with practical experience.
- An AI Agent is not simply an LLM combined with a Prompt; it requires multiple supporting components such as Memory, Tools, Runtime, Observability, and Evaluation.
- Memory allows an Agent to personalize the user experience.
- Observability and Evaluation are important components when deploying Agents in real-world environments.
- Vibe Coding can accelerate development but does not eliminate the role of the programmer.
- AI needs to be used responsibly, especially when working with data and real-world systems.
- Participating in communities and technology competitions is an effective way to transform theoretical knowledge into practical experience.

---

### Conclusion

The **AWS First Cloud AI Journey – Agent Forge Deep Dive 2026** event helped me broaden my knowledge of **Agentic AI and Amazon Bedrock AgentCore**, especially important aspects of building AI Agents in a practical manner, such as **Memory, Observability, and Evaluation**.

While the theoretical sessions helped me understand **what components an Agent needs and why they are important**, the Hands-on session guided by **Anh Pham** helped me better understand **how to start building and testing an Agent in practice**.

I was particularly impressed by the speaker's detailed hands-on guidance using **Vibe Coding**. Combining AI with programming can shorten the time required to build Prototypes while enabling learners to quickly experiment with new ideas.

Through this event, I gained a clearer understanding that building an AI Agent is not simply about selecting a powerful AI model. It is a process that combines **AI, Cloud Computing, Software Engineering, Security, Observability, and Production-oriented operational thinking**.

These are valuable areas of knowledge for my learning journey and future development in **Cloud Computing, AI, and Software Engineering**.

---

### Some Photos from the Event

**Insert photos of the event banner and images taken during the Hands-on Lab here.**

![AWS First Cloud AI Journey – Agent Forge Deep Dive 2026](../../images/agent-forge.png)
