Central Command Interface: Solution Architecture Overview


Live Deployment: [https://central-command.heynephew.tech/](https://central-command.heynephew.tech/)



Target Architecture Core: Microsoft Azure (AZ-305 Blueprint)


Target Role Alignment: Solutions Engineer / Cloud Infrastructure Architect / Technical Operations


Executive Summary


The Central Command Interface is an interactive, high-fidelity single-page application (SPA) designed to demonstrate complex system integrations and cloud orchestration concepts. It serves as a visual proof-of-concept for a decoupled, high-availability architecture by simulating real-time telemetry, Zero Trust Identity and Access Management (IAM), and FinOps resource allocation. By mapping front-end interactions to simulated enterprise-grade backend behaviors, the project effectively bridges the gap between client-side user experience and global cloud infrastructure routing.


Current Architecture & Stack (The Visual Front-End)


Front-End Layout Engine: Vanilla HTML5 utilizing a rigorous CSS3 Grid and Flexbox architecture. The interface implements Glassmorphism UI patterns, CSS animations (`@keyframes`), and strict structural zoning for high-density data visualization.



Compute & Logic: Vanilla JavaScript (ES6) driving a custom SPA state engine, DOM manipulation, drag-and-drop Kanban functionality, and asynchronous event simulation relying on `setTimeout` constructs to mimic API latency and database processing times.



Data & Integration Layer:** Currently utilizes hardcoded JSON-like state structures and client-side calculations—such as the FinOps resource optimization math and the Starfleet Academy logic assessments—rather than querying external database endpoints.



Telemetry & Pipeline:** Simulated via client-side terminal outputs and static DOM updates. CI/CD log streaming, Azure DevOps webhooks, and routing sequences are represented visually to demonstrate the logic flow of a true transmission sequence.


Anticipated Tech Stack for Production (Enterprise Scale)


To elevate this lightweight UI into a robust, enterprise-grade application suitable for thousands of concurrent sessions, the following Microsoft Azure (AZ-305) components must be integrated:


Compute & Global Content Delivery:


Azure Static Web Apps: To host the vanilla HTML/CSS/JS frontend with global edge distribution and automated GitHub Actions CI/CD integration.


Azure Front Door: Configured for global Layer 7 load balancing, SSL offloading, and intelligent edge caching to ensure the interface renders with sub-millisecond latency worldwide.


Azure Kubernetes Service (AKS) or Azure Functions: For migrating the simulated JavaScript logic (e.g., Fleet Management routing, Kobayashi Maru architectural scenarios) into decoupled, serverless, or containerized microservices.



Data Integration & Performance Caching:


Azure Cosmos DB (MongoDB vCore): To replace the static DOM state, acting as the globally distributed, low-latency data store for Fleet telemetry, logistics data, and RAG/Vector query responses.


Azure Cache for Redis: To cache high-frequency dashboard telemetry (e.g., resource allocation percentages, active threat feeds) to drastically reduce Cosmos DB read unit (RU) consumption and improve TTFB (Time to First Byte).


Identity, Access Management, & Security:


Microsoft Entra ID (formerly Azure AD): To implement a true Zero Trust posture, enforcing authentic OAuth 2.0 token validation, replacing the visually simulated JIT/PIM access and RBAC logic.


Azure Web Application Firewall (WAF): Attached directly to Azure Front Door to protect the SPA from malicious packet floods, SQL injection, and cross-site scripting (XSS) at the network edge.


Observability & Business Continuity:


Azure Application Insights: To capture real user telemetry, track JavaScript execution exceptions, and map frontend interactions to backend service performance.


Azure Log Analytics & Microsoft Sentinel (SIEM/SOAR): To ingest authentic threat data and trigger automated runbooks for incident response, aligning with the SOC perimeter monitoring concepts visualized in the UI.


Common Build & Deployment Issues with Remediation


Issue 1: State Loss on Refresh (Ephemeral Client-Side Data)


The Situation: Currently, dynamic state changes—such as Kanban card placement in the Shipyard, PIM access countdown timers, and FinOps optimization execution—are lost upon a browser refresh because the data relies entirely on the client's volatile memory and DOM state.


Architectural Remediation: Decouple the state management by implementing Azure Cosmos DB synchronized via Azure API Management (APIM). State mutations on the frontend will trigger asynchronous `PUT` requests to the APIM, pushing changes to the database. A subsequent `GET` request on initialization reconstructs the environment precisely as the user left it.


Issue 2: API Gateway Bottlenecks under Polling Load


The Situation: The application simulates high-frequency data feeds (like the Supply Chain IoT telemetry and SOC alerts). In a production scenario, attempting to retrieve this data via standard HTTP polling would quickly exhaust connection pools and trigger HTTP 429 (Too Many Requests) throttling.


Architectural Remediation: Transition from synchronous REST polling to event-driven push notifications utilizing Azure SignalR Service. Backend IoT devices or event hubs stream telemetry to SignalR, which establishes a persistent WebSocket connection to the client, pushing updates to the UI natively without overloading the API gateway.


Issue 3: Hardcoded Security Posture and Client-Side Trust


The Situation: The interface visually depicts advanced Zero Trust concepts, such as Just-In-Time (JIT) role elevation and conditional access blocks based on location, but enforces these boundaries strictly via client-side CSS and JavaScript toggle classes.


Architectural Remediation: Integrate the Microsoft Authentication Library (MSAL) into the frontend code linked to an Entra ID App Registration. True backend microservices will enforce validation by requiring a Bearer token on every request. Simulated PIM elevations will be replaced by actual Microsoft Graph API calls invoking Entra ID Privileged Identity Management capabilities to ensure security is enforced at the identity layer, not the DOM layer.