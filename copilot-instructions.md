You are assisting in the development of a Portfolio Command Center that reads structured portfolio JSON files from the /portfolio_registry/ directory and generates a unified HTML/CSS/JS dashboard.

Your responsibilities:

1. DATA INGESTION LAYER
When asked to load data:

Read all JSON files inside /portfolio_registry/

Validate each file against the schema:

portfolio_id

portfolio_name

core_philosophy

final_allocation

role_of_components

expected_behavior

rebalancing_policy

behavioral_commitment

intentional_overlap

Normalize allocations into a consistent internal structure

Merge all portfolios into a single masterData object

Example internal structure:

js
const masterData = {
  portfolios: [...],
  globalIntentionalOverlap: ["SCHD","VXUS","SGOV","VTI","XLV"]
};
2. DASHBOARD GENERATION
When generating the dashboard:

Produce a single HTML file with:

Inline CSS (dark theme)

Inline JavaScript

Responsive layout

No external libraries except Google Fonts

The dashboard must include:

Header

Executive Summary

Portfolio‑by‑Portfolio Cards

Overlap & Redundancy Map

Risk & Volatility Layer

Actionability Layer

Consolidated Allocation View

Signals & Indicators

Narrative Summary

Appendix

3. VISUAL STYLE REQUIREMENTS
Use a modern dark theme:

Background: #0d1117

Card: #161b22

Text: #e6edf3

Accent: #58a6ff

Borders: #30363d

Rounded corners

Soft shadows

Smooth hover animations

Use Inter, Roboto, or SF Pro.

Charts must be built using vanilla JavaScript + <canvas>, no libraries.

4. OVERLAP LOGIC
When analyzing overlap:

Treat these tickers as intentional:

SCHD

VXUS

SGOV

VTI

XLV

Do not flag them as redundancy.

All other cross‑portfolio duplicates should be highlighted as:

Hidden concentration

Redundancy

Review candidates

5. CODE STYLE RULES
Copilot must:

Use modular functions

Use descriptive variable names

Avoid monolithic files

Keep HTML readable

Keep JS organized into sections

Keep CSS clean and minimal

Add comments for your wife/daughter to understand

6. FILE STRUCTURE
Copilot should maintain:

Code
/portfolio_registry/        ← JSON files (source of truth)
/dashboard/                 ← HTML/CSS/JS output
/scripts/                   ← JS modules (optional)
/styles/                    ← CSS (optional)
/.vscode/copilot-instructions.md
7. BEHAVIORAL RULES
Copilot must:

Never rewrite the JSON files unless explicitly asked

Never infer portfolio philosophy — always read from JSON

Never introduce new tickers without instruction

Always preserve your tone: calm, simple, family‑friendly

8. PRIMARY COMMANDS
Copilot should respond to these commands:

“Generate dashboard”
→ Build the full HTML/CSS/JS dashboard using all JSON files.

“Update dashboard layout”
→ Modify only the visual structure.

“Add new portfolio”
→ Validate JSON → integrate into masterData → update dashboard.

“Explain this code”
→ Provide calm, simple explanations.

“Refactor this module”
→ Improve clarity, modularity, and maintainability.

9. OUTPUT REQUIREMENTS
When generating the dashboard:

Output a single HTML file

Contain all CSS and JS inline

No external dependencies

No frameworks

No build tools

10. TONE & INTENT
Copilot must always:

Keep things simple

Avoid complexity

Protect behavioral discipline

Prioritize clarity

Build for your wife and daughter

Make the system future‑proof