# Heysam Engineering: The Day One Technical Primer

Welcome to the codebase. At Heysam, we don't just write scripts; we compose scalable systems. Our infrastructure is designed to be lean, containerized, and high-performance. 

This document outlines the technical baseline required to push code here. Read it before you clone your first repository.

## 1. Local Environment: The Docker Mandate
We do not accept "it works on my machine" as an excuse. Our entire local, staging, and production environments are containerized. Whether you are spinning up the front-end for Avval, the subscription engine for Strite, or a PostgreSQL database, it happens inside Docker.

*   **Install:** You must have Docker and Docker Compose installed locally.
*   **Spin Up:** Most repositories can be started by running `docker compose up -d` in the root directory. if a repository doesn't it's a problem fix it or ask for a fix.
*   **The Logs are the Truth:** If something breaks, do not guess. Run `docker logs <container_name>` before you ask for help. 90% of your answers are sitting in the standard output.

## 2. Version Control: Git Standards
We treat our Git history as documentation. If you look at the commit history, it should read like a logical story of how a feature was built or a bug was resolved.

*   **Branching:** Never push directly to `main`. Create an isolated branch for your work. Use standard prefixes: `feat/` for new features, `fix/` for bug fixes, and `refactor/` for structural changes.
*   **Commits:** Commit early and often locally, but squash your commits into logical, working chunks before opening a Pull Request. 
*   **Messages:** Write commit messages that explain *why* a change was made, not just *what* changed. (e.g., "Fix: Resolve Azno logical replication connection timeout" instead of "Fixed database").

## 3. Own the Mechanism (Do Not Code Blind)
AI is a powerful tool, not a senior engineer. Never let a chatbot dictate your architecture or blindly copy-paste generated code into our codebase. 

If an AI writes a fix or a feature, you must be able to explain exactly how and why it works. If you do not fundamentally understand the mechanics of what you are shipping, you cannot maintain it, scale it, or debug it when it breaks—and your role here becomes irrelevant. 

Be relentlessly curious. When an AI implements a solution, dissect the logic. Take notes on the gaps in your knowledge and figure them out before opening a PR. You are the architect; the AI is just the typist.

## 4. The Pull Request (PR) Pipeline
A Pull Request is a request for *review*, not a request for *QA*. You are expected to thoroughly test your own work before asking another engineer to look at it. I will not review a PR unless it meets the following criteria:

*   **It Has a Clear Message:** Your PR description must clearly state exactly what problem it solves and for which user. We do not merge code without context.
*   **It Builds Locally:** You have pulled the latest `main`, merged it into your branch, and the build succeeds with zero compilation errors.
*   **It is Clean:** You have removed all dead commented-out code, unused variables, and random print statements. If you are writing Python, ensure it follows clean Object-Oriented principles, not just functional scripting.
*   **You Handled the Edge Cases:** What happens if the API is slow? What happens if the user leaves a form blank or hits the back button? Loading and error states must be graceful.

## 5. Getting Unstuck (Applying the 30-Minute Rule)
When you inevitably hit a wall—whether it's a Next.js routing error, an Nginx reverse proxy configuration, or a database schema mismatch—execute the 30-Minute Struggle:

1.  **Read the Error:** Actually read the stack trace. 
2.  **Check the Docs:** Go to the official documentation first, not just Stack Overflow.
3.  **Isolate the Variable:** Strip away the complexity. If the API is failing, test it with an empty payload. If the container won't start, check the port bindings.
4.  **Document & Escalate:** If 30 minutes pass, stop. Write down exactly what you tried, what the error is, and bring it to Office Hours.
5.  **Dont Stop** Dont wait for office go for your next problem  to solve.
