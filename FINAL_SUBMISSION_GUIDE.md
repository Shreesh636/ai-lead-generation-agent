# Final Submission & College Demonstration Guide
## Assignment 07: AI Lead Generation Agent — Complete Qualification & Outreach System

This guide provides step-by-step instructions for demonstrating and submitting your project for **The AI School: Assignment 07**.

---

## 1. Quick Demonstration Walkthrough (For Viva / Faculty Evaluation)

### Part A: Instant Automated Workflow-Logic Verification (Offline) (30 Seconds)
To demonstrate to your professors that the entire workflow structure, scoring rubric, and branching logic operate deterministically before opening n8n:
1. Open a terminal inside the project directory:
   ```bash
   cd "AI_Lead_Generation_Agent_Final"
   ```
2. Run the automated Node.js workflow-logic verification engine:
   ```bash
   node scripts/execute_n8n_workflow.js
   ```
3. Or run the Python verification suite:
   ```bash
   python scripts/run_test_suite.py
   ```
4. **What to point out to the evaluator**:
   - Point out that **all 7 scenarios passed in automated workflow verification** (Enterprise Qualified, Student Poor Fit, Missing Data Handling, High Buying Intent, Unresponsive Follow-ups, Interested Sales Handoff, and Human Approval Enforcement).
   - Point out that **8 persistent records were simulated and updated in the n8n Data Table (`Lead_Records`)**.
   - Show how Elena Rostova (Test 3) preserves `"Unknown"` without the AI hallucinating false phone numbers or revenue.
   - Show how Alex Turner (Test 2) is automatically scored `0/100` and archived.
   - Show how Rachel Green (Test 6) produces a full `HANDOFF-xxxxxx` dossier with an SLA under 2 hours.
    - Show how Test 7 enforces Human Approval: unattended leads genuinely pause in `Pending_Approval` awaiting human decision, approved leads proceed to outreach, and rejected leads route to `Reject -> Stop Outreach` with status `Outreach_Rejected_By_Human`.

---

### Part B: Live Inside-Canvas n8n Workflow Demonstration (2 Minutes)
*(To be triggered directly inside your n8n UI canvas during viva/presentation)*
1. Launch your local or cloud n8n instance (`n8n start` or open `http://localhost:5678`).
2. Go to **Workflows** → Click **`...`** (top right) → **Import from File**.
3. Select `workflow/AI_Lead_Generation_Agent.json`.
4. Click **Execute Workflow** (or test on the `Manual Trigger (Run Demo)` node).
5. **What to demonstrate live on screen**:
   - **Data Normalization Node**: Click to show how raw inputs are standardized into 13 fields and emails are validated via regex.
   - **Loop Over Items Node**: Point out `batchSize: 1`, explaining that each lead is isolated to prevent token bleed and allow discrete conditional branching.
   - **AI Qualification & Scoring Agent**: Show the Groq Llama 3.3 70B prompt and the resulting structured JSON score (0–100) and rationale.
   - **Human Approval Gateway (Wait for Form Decision)**: Show how execution genuinely halts (WAITING status) and generates a review form. Demonstrate submitting Approve to release to outreach, or Reject to route to `Reject -> Stop Outreach`.
   - **Follow-up Cadence**: Show the `Day +3` and `Day +7` automated touchpoints that transition unresponsive leads to `Marked_Cold_Nurture`.
   - **Sales Handoff Dossier**: Show the generated `HANDOFF-xxxxxx` JSON object containing the complete lead profile, score, and next steps for the account executive.

---

### Part C: Presentation Walkthrough (3 Minutes)
1. Open `presentation/AI_Lead_Generation_Agent_Presentation.pptx`.
2. Present the 12 slides:
   - Slide 1: Title & Overview
   - Slide 2: Inbound Sales Bottleneck (Problem)
   - Slide 3: Project Objectives
   - Slide 4: 4-Stage Workflow Architecture
   - Slide 5: Technology Stack (n8n + Groq + Python)
   - Slide 6: Data Hygiene & 13 Standard Fields
   - Slide 7: 0–100 Scoring Rubric (5 Weighted Factors)
   - Slide 8: Grounded Personalization & Guardrails
   - Slide 9: Human Approval Gateway & Safe Send Mode
   - Slide 10: Response Tracking & Multi-Tier Follow-ups
   - Slide 11: Sales Handoff Dossier & Empirical Test Results
   - Slide 12: Conclusion & Future Roadmap
3. Every slide has comprehensive speaker notes embedded for quick reference during your viva!

---

## 2. Deliverables Inventory

| Path | Purpose |
| :--- | :--- |
| `workflow/AI_Lead_Generation_Agent.json` | Complete, importable n8n workflow JSON |
| `data/sample_leads.csv` | 8 sample leads covering all edge cases (CSV format) |
| `data/sample_leads.json` | 8 sample leads in JSON format |
| `scripts/run_test_suite.py` | Python test runner verifying 6/6 test cases |
| `scripts/generate_presentation.py` | PPTX generator script using `python-pptx` |
| `presentation/AI_Lead_Generation_Agent_Presentation.pptx` | 12-slide executive presentation |
| `documentation/PROJECT_REPORT.md` | Full 24-section college academic project report |
| `documentation/ANALYSIS_QUESTIONS.md` | Complete answers to the 5 official assignment questions |
| `documentation/ARCHITECTURE.md` | Deep architecture guide with Mermaid flowcharts & data dictionary |
| `documentation/AI_PROMPT_LIBRARY.md` | System prompts, schemas, and anti-hallucination guardrails |
| `documentation/TEST_CASES.md` | Verification logs and test scenario details |
| `documentation/VIVA_QUESTIONS.md` | 25 curated viva questions with sharp model answers |
| `SUBMISSION_CHECKLIST.md` | Official requirements checklist |
| `README.md` | Master project repository documentation |
| `LICENSE` | MIT Open Source License |

---

## 3. GitHub Repository Publishing Commands

To push this repository to your personal GitHub account:

```bash
cd "C:\Users\Shreesh\Desktop\AI Lead Generation Agent\AI_Lead_Generation_Agent_Final"
git init
git add .
git commit -m "feat: complete AI Lead Generation Agent (Assignment 07)"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/ai-lead-generation-agent.git
git push -u origin main
```
