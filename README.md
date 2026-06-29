
# Agentic AI Service Desk

An elegantly designed, full-stack AI Help Desk and Service Level Agreement (SLA) operations platform. This application integrates a live **RAG (Retrieval-Augmented Generation) Support Agent** powered by Gemini with a secure **PostgreSQL Ticket Registry** and **Metrics Dashboard**.

---

## 🚀 Key Modules & Capabilities

### 1. AI Desk Agent (RAG + LLM Workflow)
*   **Contextual Diagnostic Search**: Formulates custom search queries against a relational Knowledge Base to locate EAP configurations, VPN parameters, or device lock rules.
*   **Autonomous Ticket Escalation**: If troubleshooting fails or requires physical/security overrides (e.g., hardware jam, locked password, lost MFA device), the agent writes a high/critical-priority case directly to the PostgreSQL database.
*   **Automatic Queue Routing**: Intelligently routes tickets to dedicated queues such as **SecOps**, **SysAdmin**, **NetOps**, **Desktop Support**, or **Facilities** based on issue semantics.

### 2. Technician Queue (PostgreSQL Database)
*   **SLA Incident Management**: Supports manual ticket creation, category categorization, and active status updates (`Open` ➜ `In Progress` ➜ `Resolved`).
*   **SLA Escalation Logs**: Visually maps every operational checkpoint, automated agent decision, assignment change, and team re-allocation.
*   **Developer Comments**: Supports cross-functional engineering collaboration with structured chat threads on active tickets.

### 3. Knowledge Library
*   **Self-Service Repository**: Categorized guidelines for Corporate VPN connections, Google Authenticator setup, Slack licensing, and printer configs.
*   **Interactive Analytics**: Allows users to find articles via fuzzy search, register helpfulness upvotes, and publish new articles.

### 4. Metrics Dashboard
*   **Incident Telemetry**: Built-in data visualization using **Recharts** representing ticket trend lines, priority densities, and resolution rates.
*   **Live Health Checks**: Monitored connections for RAG pipelines, API nodes, and database connection pools.

---

## 🛠️ Tech Stack & Architecture

*   **Frontend Framework**: React 18 with Vite (TypeScript)
*   **Styling**: Tailwind CSS (Utility classes, responsive viewport boundaries, custom transitions)
*   **Animations & Micro-interactions**: Framer Motion
*   **Visualization**: Recharts & D3
*   **Backend Server**: Node.js Express Server
*   **Database**: Google Cloud SQL (PostgreSQL)
*   **ORM Layer**: Drizzle ORM (Fully type-safe schemas, relations, and seeding)
*   **Identity System**: Firebase Auth (SAML-compliant JWT Verification & Google Identity SSO)
*   **AI Orchestrator**: Official `@google/genai` SDK
    *   *Reliability Mechanism*: Implements custom exponential backoff retries and dynamic fallback nodes (`gemini-3.5-flash` ➜ `gemini-3.1-flash-lite` ➜ `gemini-flash-latest`) to bypass transient high-demand API bottlenecks.

---

## ⚙️ Environment Variables Setup

Create a `.env` file in the root directory of your project:

```env
# Google Cloud SQL Connection Parameters
SQL_HOST=127.0.0.1
SQL_USER=your_db_user
SQL_PASSWORD=your_db_password
SQL_DB_NAME=your_db_name

# Administrative Connection (Used for Drizzle Migrations)
SQL_ADMIN_USER=your_admin_user
SQL_ADMIN_PASSWORD=your_admin_password

# Generative AI Key (Gemini API)
GEMINI_API_KEY=your_gemini_api_key

# Node Environment Settings
NODE_ENV=development
PORT=3000
