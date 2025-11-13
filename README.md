# n8n-client-onboarding-automation
AI-driven client onboarding workflow using n8n, OpenAI agents, and structured JSON output.

# Client Onboarding Automation (n8n + OpenAI Agents)

This repository contains a complete **AI-driven Client Onboarding automation** built in **n8n**.  
It demonstrates how to orchestrate complex decision workflows using:

- n8n AI Agent nodes  
- Structured Output Parsers  
- Conditional branching  
- Simulated KYC & Credit Score checks  
- Final automated decision reports  

This project is designed both as a learning exercise and as a starting point for real onboarding flows in FinTech environments.

---

## Overview

The workflow simulates a full onboarding journey:

1. Receive client data via **Webhook**
2. Apply business rules using **AI Planner Agent**
3. Dynamically decide which verification checks to run:
   - KYC  
   - Credit Score  
4. Execute verifications or fallbacks  
5. Merge all results  
6. Produce a structured final decision using **AI Final Agent**

The automation outputs a JSON record containing:
- the final onboarding decision,
- risk assessment,
- reasons,
- tools used,
- and the client identifier for traceability.


---

##  Workflow Files

| File | Description |
|------|-------------|
| `automation_testing_Client_Onboarding_Agent.json` | The n8n workflow export (import this into your n8n instance). |
| `/screenshots/` | All workflow screenshots (nodes, agents, parsers, logic). |
| `REPORT.md` (optional) | Full project report explaining the entire logic. |

---

##  Features

###  AI Planning with Clear Business Rules
The first AI agent:
- reads client input  
- applies nationality rules  
- evaluates student exceptions  
- checks for missing identity fields  
- determines which tools must be executed next  

It returns a structured JSON with:
```json
{
  "provisional_action": "approve | reject | manual_review_senior | manual_review_board",
  "reason": "",
  "callTools": []
}
