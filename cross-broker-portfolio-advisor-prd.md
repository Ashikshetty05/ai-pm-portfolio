### **1. Problem Statement**
Evolving retail investors increasingly hold assets across multiple brokerages—such as Groww and Zerodha Kite—as they outgrow the limitations of a single platform. However, these walled ecosystems prevent access to a unified, real-time view of their wealth. Users are forced to rely on tedious Excel spreadsheets or clunky third-party tools just to understand their overall financial position.

This fragmentation creates a critical bottleneck, stripping investors of holistic visibility and making it nearly impossible to execute coherent, cross-asset strategies or rebalance portfolios effectively. Breaking down these silos is essential to provide users with the unified, real-time analytics they need to manage their wealth strategically.

### **2. Target Users**
Persona 1: The “Groww-First” Millennial Scaler
- Name: Rohan
- Age: 26
- Occupation: Software Engineer
- City: Bengaluru
- Specific Frustration:
Started his investing journey with mutual funds on Groww due to its simple UI but recently opened a Zerodha account to buy direct equities and ETFs. He dislikes spending Sunday mornings manually updating a Google Sheet just to calculate his overall debt-to-equity ratio across both platforms.

Persona 2: The “Zerodha-First” Active Optimizer
- Name: Priya
- Age: 32
- Occupation: Marketing Manager
- City: Mumbai
- Specific Frustration:
Uses Zerodha Kite extensively for direct stock trading, while her long-term SIPs and family investments are on Groww. She struggles to track whether her direct stock purchases are causing overexposure to specific sectors (e.g., banking) when combined with her mutual fund holdings.

### 3. Jobs To Be Done (JTBD)
For Rohan (Groww-First):
- When I review my monthly finances, I want to see my total net worth and asset allocation across all brokerages in one unified dashboard, so I can understand my financial standing without manual data entry.
- When I decide how to allocate my monthly savings, I want to instantly see my combined debt-to-equity ratio across platforms, so I can maintain my target risk profile without using spreadsheets.

For Priya (Zerodha-First):
- When I analyze portfolio risk, I want to see my combined exposure to sectors and underlying stocks across both direct equities and mutual funds, so I can avoid over-concentration and hedge effectively.
- When I plan my annual tax strategy, I want a consolidated report of realized gains and losses across all platforms, so I can optimize tax harvesting efficiently.

### 4. AI Fit Decision
Where AI Creates Value
- AI enables deep portfolio analysis by interpreting mutual fund holdings and cross-referencing them with direct equities to identify hidden overlaps. For example, it can highlight that Priya holds 15% in HDFC Bank directly while her mutual funds add another 8% exposure.
- It supports natural language queries, allowing users to ask questions like: "*What is my total exposure to the EV sector across all accounts?”* or "*How much dividend income did I earn last quarter?”*
- AI can generate proactive rebalancing suggestions by detecting portfolio drift (e.g., equity allocation rising from 70% to 80%) and providing step-by-step guidance to restore balance.

Where the Human Stays in Control
- **Data Linking:** Users must explicitly authenticate and grant consent via the Account Aggregator framework. AI cannot bypass security protocols.
- **Trade Execution:** The AI never executes trades automatically. It only provides insights and recommendations; users must manually review and execute decisions.
- **Goal Setting:** Users define their financial goals and risk appetite. The AI operates strictly within these boundaries.

### 5. Success Metrics
North Star Metric
- Weekly Active Consolidated Users (WACU):
The number of unique users who access the unified dashboard or interact with cross-brokerage AI insights at least once per week. Why: Indicates whether users rely on the platform as their primary financial overview instead of reverting to spreadsheets.

Supporting Metrics
- Account Link Success Rate:
Percentage of users who successfully connect external brokerages via the Account Aggregator framework. Why: Measures onboarding friction; without account linking, core value cannot be delivered.
- AI Insight Adoption Rate:
Percentage of users engaging with AI features (e.g., natural language queries or sector overlap alerts). Why: Validates whether the AI meaningfully solves real user problems.
- Rebalancing Action Rate:
Percentage of AI-generated suggestions (rebalancing or tax harvesting) that users act on within 30 days. Why: Measures trust and actionability of AI insights.

Guardrail Metrics
- Consent Revocation / Unlink Rate:
Percentage of users who revoke account access or unlink brokerages.Why: Indicates trust issues, privacy concerns, or lack of perceived value.
- Data Inaccuracy / Hallucination Rate:
Number of user-reported errors in portfolio data, calculations, or asset classification.Why: In fintech, even a single incorrect insight can severely damage user trust—accuracy must be absolute.

### 6. Output Specification
1. Output Format
The AI delivers insights through a multi-layered UI approach, adapting to the user’s intent—from passive monitoring to active querying:
- Persistent Dashboard Widgets:
Designed for foundational, at-a-glance metrics (e.g., Rohan’s debt-to-equity ratio). These are highly visual, using donut charts, bar graphs, and clear typography.
- Contextual Insight Cards (“Nudges”):
Proactive, bite-sized cards that appear dynamically on the home screen when the AI detects anomalies (e.g., Priya’s sector overlap). These are dismissible and interactive.
- Conversational Chat Interface:
A dedicated “Ask AI” search bar and chat modal for natural language queries, returning structured text, inline tables, or micro-charts based on the query.

2. Output Content
a) The Unified Dashboard
- Hero Section:
Displays total consolidated net worth (in large text) along with day-over-day percentage change.
- Visualizations:
Includes a unified asset allocation chart (Equity vs. Debt vs. Gold) and a combined “Top 5 Holdings” list, aggregating data from Zerodha Kite and Groww.

b) AI Insight Card (e.g., “Overlap Alert”)
- Header: “⚠️ High Sector Concentration Detected”
- Body: “Your exposure to the Banking sector is currently 32% (Target: 20%).”
- Visual Breakdown:
“Direct Equities (Zerodha): 18% | Mutual Funds (Groww): 14%.”
- Call to Action (CTA): “Review Portfolio Drift.”

c) Rebalancing Suggestion Flow
- Current vs. Target State:
A clear side-by-side comparison of the portfolio’s current allocation versus the target allocation.
- Step-by-Step Action Plan:
A generated checklist (e.g.,
“Step 1: Sell ₹50,000 of XYZ Mutual Fund on Groww.
Step 2: Buy ₹50,000 of ABC ETF on Zerodha”).
- Execution:
Distinct “Approve & Route” buttons that deep-link users to the respective broker’s execution screens.

3. Output Constraints (Strict Guardrails)
- Deterministic Math Only:
The LLM is strictly prohibited from performing financial calculations to avoid hallucinations. It must only retrieve and present results computed by a deterministic backend system.
- No Predictive Financial Advice:
The AI must not predict market movements or recommend assets for alpha generation.
    - ❌ Not allowed: “HDFC is undervalued; you should buy more.”
    - ✅ Allowed: “Buying ₹10,000 of Gold ETFs will restore your target 10% allocation.”
- Tone and Urgency Restrictions:
The output must remain calm, objective, and neutral. It must avoid FOMO-driven language, exaggerated urgency, or emotionally manipulative cues (e.g., “URGENT: Your portfolio is crashing! Sell now!”).
- Explicit Source Attribution:
Every metric or visualization must clearly indicate its data sources (e.g., icons or tooltips showing Groww and Zerodha) to ensure transparency and trust.

### 7. Evaluation Rubric
1. What makes a good AI output? (The Standard of Excellence)
A good output acts as a precise, objective, and transparent analytical tool.
For example, if Rohan asks, *“What’s my current debt-to-equity ratio across both platforms?”*, a high-quality response does not perform the calculation itself. Instead, it retrieves the deterministic result from the backend and presents it clearly:
“Your current debt-to-equity ratio is 30:70.”
It then provides a visual breakdown with explicit source attribution:
“Equity: ₹5L (Zerodha) + ₹2L (Groww) | Debt: ₹3L (Groww).”
Finally, it neutrally highlights deviation from the user’s target (e.g., 20:80) and offers a calm, low-pressure call to action:
“Review options to restore your 20:80 target.”
The output is factual, traceable, and leaves the final decision entirely to the user.

2. What makes a bad AI output? (The Failure States)
A bad output breaks trust through hallucination, panic-inducing tone, or unauthorized financial advice.
For example, if Priya asks, *“Should I sell my HDFC shares because of my sector overlap?”*, a problematic AI response would be:
“Yes, your Banking exposure is dangerously high at 45%! The sector is underperforming right now, so you should urgently sell your HDFC direct equity on Zerodha to protect your portfolio.”
This fails on multiple fronts:
- It hallucinates incorrect data (actual exposure is 32%).
- It uses alarming, FOMO-driven language (“dangerously high,” “urgently”).
- It predicts market movements (“underperforming right now”).
- It provides specific, actionable investment advice on a single stock.

In wealth management, such outputs represent a serious compliance and trust failure.

3. Who evaluates it and when? (The Safety Net)
Because poor outputs can lead to real financial consequences, the evaluation process must be far more rigorous than in a typical consumer application.
Before Launch (Internal Validation)
The AI undergoes intensive red teaming. This is conducted not only by QA engineers but also by a specialized internal compliance and domain expert team. They actively attempt to:
- Trigger the AI into providing unauthorized or illegal financial advice.
- Induce recommendations for speculative assets (e.g., penny stocks).
- Break deterministic math guardrails.

The feature is not released until hallucination and advice-generation rates fall below strict, predefined thresholds set by the compliance team, after which launch clearance is granted.

After Launch (User-Driven Feedback)
We rely on low-friction, high-signal feedback mechanisms:
- Every AI insight card and chat response includes a simple thumbs up / thumbs down option.
- A dedicated and highly visible “Report Data Mismatch” button is present next to every consolidated metric.
If a user flags an issue—such as incorrect calculations or overlapping data—the associated prompt and backend logs are immediately escalated to the engineering team for root-cause analysis, bypassing the standard support queue.

### 8. Risk Log
Risk 1: AI hallucinating financial data
- How likely is it: Medium (LLMs are inherently prone to hallucination if not tightly constrained).
- How bad is it if it happens: Critical
- Mitigation Plan:
Enforce strict architectural separation—the LLM is completely restricted from performing mathematical calculations. It only formats and presents numbers generated by a deterministic backend. Additionally, implement a “Report Data Mismatch” feature for immediate user flagging and rapid engineering escalation.

Risk 2: Account Aggregator (AA) flow failing
- How likely is it: Medium (The AA ecosystem in India is growing rapidly but still experiences occasional downtime and friction).
- How bad is it if it happens: High (It breaks the core “single source of truth” value proposition).
- Mitigation Plan:
Design a graceful degradation UI. If the AA sync fails, clearly display the last successfully synced data with a timestamp (e.g., “Zerodha data last updated 4 hours ago”). As a fallback, allow users to manually upload their NSDL/CDSL CAS (Consolidated Account Statement).

Risk 3: Data security breach
- How likely is it: Low (Assuming industry-standard security protocols are implemented).
- How bad is it if it happens: Critical (Leads to loss of user trust, legal liabilities, and potential business failure).
- Mitigation Plan:
Implement end-to-end encryption for all portfolio data. Follow strict data minimization practices—never store brokerage login credentials; instead, use secure OAuth tokens or temporary AA consent artifacts. Conduct regular third-party penetration testing and independent security audits before major releases.

Risk 4: Regulatory risk — SEBI compliance
- How likely is it: Low (Given strong guardrails in design).
- How bad is it if it happens: Critical (May result in heavy penalties or regulatory shutdown).
- Mitigation Plan:
Hardcode constraints that prevent the AI from recommending specific stocks or predicting market movements. Include clear UI disclaimers such as:*“This tool provides portfolio analytics, not financial advice.”*
Ensure the internal compliance team signs off after rigorous red teaming before launch.

Risk 5: Broker API dependency and ecosystem lock-out
- How likely is it: High (Platforms like Groww and Zerodha prefer retaining users within their ecosystems).
- How bad is it if it happens: High (Loss of connectivity renders the product unusable for affected users).
- Mitigation Plan:
Avoid reliance on unofficial or reverse-engineered APIs. Use the RBI-backed Account Aggregator framework, which provides a regulated pathway for data access. For execution deep links, maintain alignment with broker partnerships and terms of service.

Risk 6: User over-reliance on AI (“Blind Follow” effect)
- How likely is it: High (Users tend to prefer automation to reduce cognitive effort).
- How bad is it if it happens: High (Can lead to regulatory scrutiny and reputational damage if users blame the platform for losses).
- Mitigation Plan:
Introduce intentional friction in the UX. Before allowing users to click “Approve & Route”, require them to review an Impact Summary explaining the rationale behind the recommendation. Auto-execution of trades must never be allowed.

Risk 7: Data freshness and sync latency (Stale Data)
- How likely is it: High (Sync delays are common, especially during peak market hours).
- How bad is it if it happens: High (Users may make incorrect financial decisions based on outdated data).
- Mitigation Plan:
Prominently display “Last Synced at [Time]” across the dashboard. If a user attempts to act on stale data (e.g., older than 15 minutes during market hours), trigger an automatic refresh. If the refresh fails, show a strong warning message such as:*“⚠️ Warning: Your portfolio data is 6 hours old. Verify live prices before executing.”*

### 9. Guardrails
1. No Autonomous Trade Execution
- The Rule:
The system will never autonomously execute a buy, sell, or modify order under any circumstances.
- The Why:
This prevents unauthorized or unintended financial losses caused by system errors or AI misinterpretation, ensuring the user remains fully in control of their capital.
- The Fallback:
If a user types, *“Sell all my HDFC shares,”* the AI responds:*“I cannot execute trades. I have prepared an action plan for you. Click below to review and manually execute this trade on Zerodha.”*

2. No Specific Investment Advice
- The Rule:
The AI will never recommend buying, selling, or holding a specific asset (e.g., stocks or mutual funds) to predict market movements or generate returns.
- The Why:
Providing specific stock recommendations without proper licensing violates strict regulatory guidelines (e.g., SEBI) and exposes the platform to serious legal and compliance risks.
- The Fallback:
If a user asks, *“Which EV stock should I buy right now?”* the AI responds:*“I cannot provide investment advice or predict market performance. However, I can analyze your current portfolio’s exposure to the EV sector or help you rebalance based on your predefined goals.”*

3. No Financial Math by the LLM
- The Rule:
The LLM must never calculate portfolio values, returns, percentages, or financial ratios.
- The Why:
LLMs are non-deterministic and prone to mathematical errors. Even a single incorrect calculation related to a user’s finances can severely damage trust.
- The Fallback:
When a user asks, *“What is my combined debt-to-equity ratio?”*, the LLM routes the query to a deterministic backend engine, retrieves the exact value (e.g., 30:70), and only formats the response conversationally.

4. No Action on Stale Data
- The Rule:
The system will not allow users to approve or execute rebalancing actions based on portfolio data older than 15 minutes during active market hours.
- The Why:
Acting on outdated data can lead to incorrect allocations and financial losses.
- The Fallback:
If a user attempts to act on stale data, the UI disables execution options and displays a blocking message:*“⚠️ Warning: Your Groww data is 3 hours old. Please trigger a manual sync to view updated recommendations.”*

5. Data Consent and Privacy
- The Rule:
The platform will never access, scrape, store, or share brokerage data without explicit, verifiable user consent via the RBI-backed Account Aggregator (AA) framework.
- The Why:
Bypassing official consent mechanisms violates user privacy, breaks data protection laws, and risks being blacklisted by brokerage platforms.
- The Fallback:
If a user asks the AI to analyze an unlinked account, the AI responds:*“I cannot view your Zerodha portfolio because it has not been linked. Please initiate the secure Account Aggregator flow to grant temporary access.”*

### 10. MVP Scope
1. What’s IN the MVP (The Core Experience)
These features represent the absolute minimum required to solve the “walled garden” problem for users like Rohan and Priya, enabling them to safely view and manage their fragmented wealth:
- Targeted Account Aggregation:
Support exclusively for linking Groww and Zerodha Kite via the RBI-backed Account Aggregator framework.
- The Unified Dashboard:
A read-only interface displaying consolidated net worth, combined asset allocation (Equity/Debt/Gold), and a unified “Top 5 Holdings” list.
- Proactive Insight Cards (“The Nudges”):
Automated detection and UI alerts for hidden sector or stock concentration overlaps across both platforms.
- Conversational AI Querying:
The “Ask AI” chat interface for natural language queries strictly related to the user’s linked portfolio.
- Guided Rebalancing:
Step-by-step rebalancing suggestions with clear “Approve & Route” deep links to broker execution screens.
- Trust & Safety Mechanics:
Explicit data source attribution (logos), visible “Last Synced” timestamps, manual refresh triggers, and a strict “stale data blocker” to prevent actions on outdated information.

2. What’s OUT of the MVP (Deferred to V2+)
These features are valuable but introduce unnecessary complexity or dilute the core focus of the initial release:
- Additional Broker Integration (Upstox, Angel One, etc.)*Why deferred:* Integrating two platforms via the Account Aggregator framework will already expose significant edge cases, latency issues, and data-mapping challenges. The experience must be perfected with the top platforms before scaling further.
- Non-Brokerage Asset Tracking (EPF, real estate, bank balances)*Why deferred:* The core problem focuses on active investment fragmentation (equities vs. mutual funds), not general net-worth tracking. Including illiquid or non-tradable assets dilutes the impact of the rebalancing engine.
- Tax-Loss Harvesting Insights*Why deferred:* Accurate tax insights require complex historical transaction data (FIFO rules, holding periods), not just current portfolio snapshots. Trust in basic calculations must be established first.
- Native Mobile Apps (iOS/Android)*Why deferred:* The initial launch will be a Responsive Web App (RWA), enabling faster iteration on complex visualizations and quicker bug fixes without app store delays.
- Automated Trade Execution*Why deferred:* This is not deferred—it is permanently out of scope. As defined in the guardrails, the AI will never execute trades autonomously.

3. Why this scope? (The Guiding Principle)
The guiding principle for this MVP is “Holistic Visibility over Comprehensive Wealth Management.”
We define holistic visibility through our North Star metric: Weekly Active Consolidated Users (WACU). If a feature does not directly encourage users to check this dashboard instead of opening their Excel sheet each week, it does not belong in the MVP.
Every feature included directly contributes to creating a unified, habit-forming view or enabling safe action based on that view. Everything excluded represents potential feature creep that would delay time-to-market or increase regulatory and technical risks before validating core demand.
We are building a highly intelligent flashlight to illuminate walled gardens—not a self-driving wealth manager.

### 11. Launch Plan
1. Launch Phases
Our rollout strategy prioritizes safety, compliance, and deterministic accuracy over speed to market.
Phase 1: Internal Red Teaming & Compliance Sign-off (Zero Users)
- Purpose:
Stress-test the AI guardrails. The compliance and domain expert teams will actively attempt to prompt-inject the AI into providing unauthorized financial advice or breaking deterministic math rules.
- Action:
No clearance, no launch. The feature remains locked until hallucination and advice-generation rates fall below compliance-mandated thresholds.

Phase 2: Internal Dogfooding (Company-Wide)
- Purpose:
Test the system infrastructure (“plumbing”). Internal team members will link their real Groww and Zerodha accounts.
- Action:
Identify failures in the Account Aggregator (AA) flow, detect data staleness during active market hours, and validate that the UI clearly separates the “Brain” (insights) from the “Hands” (manual execution).

Phase 3: Closed Beta with Power Users (Max 200 Users)
- Purpose:
Gather high-quality qualitative feedback. We will invite approximately 200 users similar to Rohan and Priya—multi-broker investors who rely heavily on Excel tracking.
- Action:
Observe how users interact with AI insights. Do they trust the data? Are they using “Approve & Route”? Conduct 1:1 interviews with ~10% of participants.

Phase 4: Expanded Beta (Up to 5,000 Users)
- Purpose:
Conduct quantitative stress testing at scale.
- Action:
Monitor key metrics such as Account Link Success Rate, Weekly Active Consolidated Users (WACU), and the Data Inaccuracy/Hallucination rate. Validate system performance under high-volume sync conditions.

Phase 5: Public Launch (General Availability)
- Purpose:
Release the feature to the entire user base.

2. Success Signals (The Expansion Gates)
Progression between phases is based on strict, measurable criteria:
Gate 1 (Phase 3 → Phase 4):
- Zero Compliance Breaches:
No instances of the AI providing specific stock advice or generating incorrect financial calculations.
- AA Link Success Rate:
Greater than 75% of beta users successfully link both brokerages on their first attempt.

Gate 2 (Phase 4 → Public Launch):
- WACU Retention:
More than 40% of expanded beta users access the dashboard or interact with AI insights at least once per week, indicating replacement of manual tracking methods.
- Data Inaccuracy Rate:
Less than 0.1% of users report data mismatches.

3. Rollback Plan
If a critical issue arises in production (e.g., data sync failure, hallucinated values, or guardrail breach), the following steps are executed:
- The Kill Switch:
The entire “Unified Wealth” module and AI interface are controlled via a server-side feature flag. Engineering can disable the feature instantly for all users without requiring a deployment or app update.
- User Experience During Rollback:
The dashboard gracefully degrades instead of failing. Users see a message such as:*“The Consolidated Wealth Dashboard is undergoing maintenance to improve sync performance. Your funds and brokerage accounts remain safe and unaffected.”*
- Engineering SLA:
Any reported data mismatch or AI hallucination triggers a P0 incident. The on-call engineering and data science teams must acknowledge the issue within 15 minutes. If the root cause cannot be identified within one hour, the feature flag is immediately disabled.