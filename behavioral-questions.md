# Behavioral Interview

## Leadership & Mentoring
### You led a team to build a scalable platform for system issues. How did you manage the team’s progress and ensure technical quality?
- At HPE, our microservices needed a centralized, scalable platform to raise and manage system issues.
- I was tasked with leading a team to build this platform using Golang, Kubernetes, and NATS, ensuring it handled issue lifecycles and customer notifications.
- I took ownership of the system and code design, and prioritized the PR merge strategy to keep development fluid. I mentored junior engineers through detailed code reviews and established a testing strategy that included local environment setups for production-like testing.
- For timely delivery, we followed the agile approaches like frequent feedbacks, failing fast. Delivering end to end functionality first. Then adding more features. Every PR however had to have unit tests.
- We introduced feature flags wherever possible
- Thus, we successfully delivered a scalable deployment with an integrated alerting infrastructure. The platform now manages the full lifecycle of system issues and provides reliable notifications to customers.

### How did you improve things over time ?
- Kubernetes security policies - ingress/egress, runAsNonRoot, readonlyFS, mounting explicit volumes which can be modified, using rolling upgrades, using lighter liveness and readiness checks
- Dockerfile: multi-stage docker builds, explicitly running as a non-root user, using scratch as a runtime base image
- Golang: setting unit testing thresholds 80 %, using mockery framework for generating mocks and unit testing, using wire for dependency injection, using contexts and multi-threading wherever possible, using circuit-breakers for synchronous calls
- Helm: adding everything configurable as ENV variables in Helm
- Libraries: putting common code in libraries

### How would you redo issues ?
- Using mountebank for local testing, rather than just mocking data and running unit tests
- I would use a columnar database for historical data
- Using modular documentation to reduce duplication

## Technical Innovation & Efficiency
### "Tell me about a time you used a new technology to solve a persistent problem."
- Technical documentation was becoming difficult to maintain and search efficiently across our evolving microservices. I wanted to implement a modern solution to generate and query documentation more effectively.
- I researched and implemented a tool utilizing Large Language Models (LLM) and Retrieval-Augmented Generation (RAG). This involved creating a pipeline where project data could be retrieved and processed by the LLM to provide accurate, context-aware documentation.
- This tool significantly streamlined the documentation process, making it easier for engineers to find specific technical details across the codebase through natural language queries.

### "How did you optimize the data synchronization process across multiple microservices?"
- At HPE, data was becoming fragmented across various microservices, leading to consistency issues.
- I needed to implement a robust process to synchronize data across these services reliably.
- I designed and implemented a synchronization process, documented this process and presented it in the org-wide demos
- This architecture ensured eventual consistency across the system and reduced manual data reconciliation efforts.

### "Tell me about a time you improved the developer experience or 'Inner Sourcing' for your organization."
Situation: Communication and code reuse were bottlenecks for the microservices team at HPE.
- I aimed to implement Inner Sourcing to break down silos and allow better knowledge sharing.
- I extensively documented the code, both in it the code using comments and outside in github docs, enabling teams to contribute to each other's codebases. I also implemented common libraries for Consistent Hashing, Sharding, State Management, Transaction Outbox so other teams didn't have to reinvent these algorithms.
- This led to a more collaborative culture and significantly faster development cycles for new services leveraging these shared components.

### "You led a team of interns to build an onboarding platform. How did you handle that responsibility?"
- At HPE, we needed a scalable platform to onboard new customers efficiently. I was assigned to lead a team of two interns to build this platform from the ground up.
- I took charge of the system design, code design, and feature prioritization while providing a testing strategy for the team. I guided them in developing a CLI and APIs to manage customer data.
- We successfully launched the Onboarding Service, which streamlined the entry process for new clients.


## Technical Problem Solving & Efficiency (Continued)
### "What were the critical considerations when designing the dual authorization facility?"

## Reliability & Resilience
### "Tell me about a time you used monitoring tools to solve a production-level concern."
- Maintaining high availability for the NATS server infrastructure was critical for inter-microservice communication.
- I needed to ensure proactive alerting and data recovery for our messaging layer.
- I used Prometheus and Grafana to build an alerting infrastructure and monitoring dashboards for NATS.
- This allowed us to manage authorization, data backup, and credentials rotation policies with full visibility into system health.

### "How did you handle the security requirements for NATS credentials?"
- Security protocols required that microservice credentials be updated regularly to prevent unauthorized access.
- I had to implement a process to rotate NATS credentials without disrupting service.
- I developed an automated process using Golang, GitHub Actions and Kubernetes/Helm to rotate credentials and manage the rotation policy.
- This ensured the platform met strict security standards while maintaining continuous availability for all connected microservices.

## Adaptability & Learning
### "From your OS project, what is the most important lesson you learned about software at its lowest level?"
- During my MS at Stony Brook, I had to develop an operating system from scratch in C and Assembly.
- The goal was to implement core kernel functions like memory management and process scheduling.
- I wrote the code for interrupt handling, page-fault handling, and a COW (Copy-On-Write) fork.
- This gave me a deep understanding of resource management and concurrency, which I now apply when designing high-performance microservices in Golang.

### "How did you handle real-time pressure in your DNSMonitor project?"
- We needed to detect Denial-of-Service (DoS) attacks in real-time using Stony Brook University's network data.
- I had to process high volumes of DNS data quickly to identify malicious activity.
- I utilized Apache Storm, RabbitMQ, and Zookeeper to build a processing pipeline that could handle real-time data streams.
- The system successfully detected accesses to malicious websites and frequent website access patterns, providing a layer of security monitoring.

## Project Management & Ownership
### "How did you balance 'Non-feature' work with product delivery?"
- While delivering microservices at HPE, I realized that developer productivity was hindered by inconsistent local environments.
- I needed to ensure that "non-feature" requirements like local setup and automated deployments were prioritized alongside features.
- I dedicated time to building a "prod-like" local environment setup and automated platform deployment with functional tests.
- This reduced the "it works on my machine" problem and accelerated the development lifecycle for the entire team.
