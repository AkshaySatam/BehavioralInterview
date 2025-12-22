# Behavioral Interview

1. Leadership & Mentoring
- Question: "You led a team to build a scalable platform for system issues. How did you manage the team’s progress and ensure technical quality?"
- Situation: At HPE, our microservices needed a centralized, scalable platform to raise and manage system issues.
- Task: I was tasked with leading a team to build this platform using Golang, Kubernetes, and NATS, ensuring it handled issue lifecycles and customer notifications.
- Action: 
* I took ownership of the system and code design, and prioritized the PR merge strategy to keep development fluid. I mentored junior engineers through detailed code reviews and established a testing strategy that included local environment setups for production-like testing.
* For timely delivery, we followed the agile approaches like frequent feedbacks, failing fast. Delivering end to end functionality first. Then adding more features. Every PR however had to have unit tests.
* We introduced feature flags wherever possible
Result: We successfully delivered a scalable deployment with an integrated alerting infrastructure. The platform now manages the full lifecycle of system issues and provides reliable notifications to customers.

- Question: How did you improve things over time ?
- Answer:
* Kubernetes security policies - ingress/egress, runAsNonRoot, readonlyFS, mounting explicit volumes which can be modified, using rolling upgrades, using lighter liveness and readiness checks
* Dockerfile - multi-stage docker builds, explicitly running as a non-root user, using scratch as a runtime base image
* Golang - setting unit testing thresholds 80 %, using mockery framework for generating mocks and unit testing, using wire for dependency injection, using contexts and multi-threading wherever possible
* Helm - adding everything configurable as ENV variables in Helm
* Libraries - putting common code in libraries

- Question: How would you redo issues ?
- Answer:
* Using mountebank for local testing, rather than just mocking data and running unit tests
* I would use a columnar database for historical data
* Using modular documentation to reduce duplication

2. Technical Innovation & Efficiency
Question: "Tell me about a time you used a new technology to solve a persistent problem."
Situation: Technical documentation was becoming difficult to maintain and search efficiently across our evolving microservices.
Task: I wanted to implement a modern solution to generate and query documentation more effectively.
Action: I researched and implemented a tool utilizing Large Language Models (LLM) and Retrieval-Augmented Generation (RAG). This involved creating a pipeline where project data could be retrieved and processed by the LLM to provide accurate, context-aware documentation.
Result: This tool significantly streamlined the documentation process, making it easier for engineers to find specific technical details across the codebase through natural language queries.

Question: "How did you optimize the data synchronization process across multiple microservices?"
Situation: At HPE, data was becoming fragmented across various microservices, leading to consistency issues.
Task: I needed to implement a robust process to synchronize data across these services reliably.
Action: I designed and implemented a synchronization process using shared libraries I developed, specifically the Transaction Outbox pattern and a State Manager. This ensured that data changes were captured and propagated even if service calls failed.
Result: This architecture ensured eventual consistency across the system and reduced manual data reconciliation efforts.

Question: "Tell me about a time you improved the developer experience or 'Inner Sourcing' for your organization."
Situation: Communication and code reuse were bottlenecks for the microservices team at HPE.
Task: I aimed to implement Inner Sourcing to break down silos and allow better knowledge sharing.
Action: I established the Inner Sourcing framework, enabling teams to contribute to each other's codebases. I also implemented common libraries for Consistent Hashing and Sharding so other teams didn't have to reinvent these complex algorithms.
Result: This led to a more collaborative culture and significantly faster development cycles for new services leveraging these shared components.


Action: I developed a custom PDF templating tool and built an accompanying app using Spring Security and Test-Driven Development (TDD). I also wrote SQL Server Stored Procedures to ensure that the data being pulled into these templates was updated atomically and correctly.



Result: The new tool provided a highly configurable alternative to BIRT, allowing the team to perform complex operations on client data and generate reports with higher accuracy and security.

Tips for your Interview:

Emphasize the "Non-Features": Your resume highlights "Non-features" like local setup, inner sourcing, and library creation. In interviews, explain how these "hidden" tasks improved the Developer Experience (DX) and long-term maintainability.




The Toastmasters Edge: Mention your role as VP of Education at Toastmasters to demonstrate that you can bridge the gap between deep technical code (like kernel development) and high-level stakeholder communication.


Leadership & Mentoring
Question: "You led a team of interns to build an onboarding platform. How did you handle that responsibility?"


Situation: At HPE, we needed a scalable platform to onboard new customers efficiently.



Task: I was assigned to lead a team of two interns to build this platform from the ground up.


Action: I took charge of the system design, code design, and feature prioritization while providing a testing strategy for the team. I guided them in developing a CLI and APIs to manage customer data.



Result: We successfully launched the Onboarding Service, which streamlined the entry process for new clients.

Question: "How did you drive adoption of 'Inner Sourcing' across teams?"


Situation: Communication and knowledge sharing across different microservices were fragmented at HPE.



Task: I aimed to implement Inner Sourcing to enable better collaboration and reuse of code.



Action: I implemented the Inner Sourcing process and provided guidance on best practices for inter-service communication and deployment.


Result: This led to better communication and knowledge sharing, as well as the creation of shared libraries like Consistent Hashing and State Managers.


Technical Problem Solving & Efficiency (Continued)
Question: "What were the critical considerations when designing the dual authorization facility?"


Situation: We needed a more secure method for sensitive microservice requests at HPE.



Task: I led a team to build a scalable platform providing dual authorization.



Action: I focused on building the alerting infrastructure and ensuring the system could scale using Golang and Kubernetes. I also integrated Kubernetes security practices and shared libraries to ensure robustness.



Result: We delivered a high-availability authorization system that enhanced the security posture of our microservices.

Reliability & Resilience
Question: "Tell me about a time you used monitoring tools to solve a production-level concern."


Situation: Maintaining high availability for the NATS server infrastructure was critical for inter-microservice communication.



Task: I needed to ensure proactive alerting and data recovery for our messaging layer.


Action: I used Prometheus and Grafana to build an alerting infrastructure and monitoring dashboards for NATS.



Result: This allowed us to manage authorization, data backup, and credentials rotation policies with full visibility into system health.



Question: "How did you handle the security requirements for NATS credentials?"


Situation: Security protocols required that microservice credentials be updated regularly to prevent unauthorized access.



Task: I had to implement a process to rotate NATS credentials without disrupting service.



Action: I developed an automated process using Golang and GitHub Actions to rotate credentials and manage the rotation policy.



Result: This ensured the platform met strict security standards while maintaining continuous availability for all connected microservices.

Adaptability & Learning
Question: "From your OS project, what is the most important lesson you learned about software at its lowest level?"


Situation: During my MS at Stony Brook, I had to develop an operating system from scratch in C and Assembly.




Task: The goal was to implement core kernel functions like memory management and process scheduling.



Action: I wrote the code for interrupt handling, page-fault handling, and a COW (Copy-On-Write) fork.



Result: This gave me a deep understanding of resource management and concurrency, which I now apply when designing high-performance microservices in Golang.


Question: "How did you handle real-time pressure in your DNSMonitor project?"


Situation: We needed to detect Denial-of-Service (DoS) attacks in real-time using Stony Brook University's network data.


Task: I had to process high volumes of DNS data quickly to identify malicious activity.


Action: I utilized Apache Storm, RabbitMQ, and Zookeeper to build a processing pipeline that could handle real-time data streams.


Result: The system successfully detected accesses to malicious websites and frequent website access patterns, providing a layer of security monitoring.

Project Management & Ownership
Question: "How did you balance 'Non-feature' work with product delivery?"


Situation: While delivering microservices at HPE, I realized that developer productivity was hindered by inconsistent local environments.



Task: I needed to ensure that "non-feature" requirements like local setup and automated deployments were prioritized alongside features.



Action: I dedicated time to building a "prod-like" local environment setup and automated platform deployment with functional tests.


Result: This reduced the "it works on my machine" problem and accelerated the development lifecycle for the entire team.
