**1. PROBLEM STATEMENT**
Zomato users — especially new and occasional users — feel overwhelmed by too many choices on the home page and miss relevant offers, leading to decision fatigue and abandoned orders.

**2. TARGET USERS**
Abhay, 25, SDE, Bengaluru — daily Zomato user frustrated by endless scrolling and missing discounts. Wants quick recommendations and auto-applied coupons.

Arun, 40, Professor, Bengaluru — occasional user overwhelmed by cluttered UI. Orders for family of 4 on Sundays. Needs simple guidance and voice/text assistance.

**3. JOBS TO BE DONE**
From Abhay:
- When I come home after a long shift, I want 3-4 great recommendations based on my budget, so I can order quickly before I get hangry.
- When I'm ready to check out, I want to be sure I'm getting the best deal, so I don't feel like I'm wasting money by missing a coupon.

From Arun:
- When I want to order an afternoon meal or late-night dessert for my family, I want the app to just recommend the best options, so I can order peacefully without getting confused by the tech.
- When I am ready to pay, I want discounts to be applied automatically, so I can save money without having to hunt for promo codes.

**4. AI FIT DECISION**
1. The feature automates high-friction tasks such as identifying budget-aligned food options, booking tables, and applying eligible discounts. It also serves as an on-demand assistant for user queries via text and voice.
2. The system follows a **hybrid model** (automation + user control):
    - AI handles recommendation generation, discount application, and booking initiation.
    - The user retains full control over final actions, including cart review, item modifications, and payment execution.
3. The system must not infer or assume health or allergy-related information.
    - If queried (e.g., allergen presence), the AI must redirect users to confirm directly with the restaurant.
4. Failure scenarios carry high business risk:
    - Payment errors → financial loss and reduced trust.
    - Incorrect health-related responses → critical user safety liability.

**5. SUCCESS METRICS**
North Star Metric- Order conversion rate via AI assistant — target X% (note: to be defined post pilot data) increase within 60 days of launch.
3 Supporting Metrics-
a) X% (note: to be defined post pilot data) of voice/text queries result in a completed recommendation.
b) Auto apply coupon feature success rate 90%.
c) 90% user satisfaction after AI recommends food and the user orders.

One Guardrail Metric: the numbers I don't want to rise are-
a) self-payment and self-booking without user permission for now it’s 0% if it rises it would be a huge problem.
b) AI irrelevant suggestion rate should stay below 5% post-launch.

**6. OUTPUT SPECIFICATION**
1. Output Format
* Primary Interface: Text or Voice + Swipeable UI Cards
* Text Response: Short confirmation (e.g., “Found 3 top dishes for you”), followed by UI cards.
* Voice Response: Brief summary (e.g., “Here are three options for you”). Avoid verbose narration.
* UI Layout: Horizontal, swipeable cards.

2. Output Content (Card Structure)
Each card must include:
* Core Details: Dish image, dish name, restaurant details
* Pricing Transparency:
- Original price (strikethrough)
- Final price (clearly displayed)
- Applied promo code with savings (e.g., “₹180 — ₹40 saved with WELCOME50”)
* Primary Action: One-click “Add to Cart” CTA

3. Output Constraints
* Decision Control: Display exactly 3 recommendations initially
* Expansion Logic: “Show more” returns a maximum of 2 additional options
* Payment Control: No automatic payments; all transactions follow standard checkout
* Health Disclaimer (Mandatory):
“Please check directly with the restaurant regarding specific allergy information before ordering.”

**7. EVALUATION RUBRIC**
1.What makes a good recommendation?
Example query:*"I want tiramisu under ₹300–400"*
Expected Outcome:
* 3 UI cards displayed
* Accurate dish match
* Correct restaurant details
* Ratings, discounts, and delivery time included
If all criteria are met → Valid recommendation

2.What makes a bad recommendation?
Example query:*"I want paneer butter masala"*
Failure Conditions:
* Incorrect dish substitution (e.g., butter chicken)
* Mismatched visuals (e.g., fried rice image)
* Low-quality or poorly rated restaurants
Any of the above → Invalid recommendation

3.Who evaluates it?
* Pre-launch (QA/Internal Testing): Evaluated by internal teams (e.g., Zomato QA, product, and ops) before release
* Post-launch (User Feedback): In-product feedback mechanism prompts users to rate and share experience after recommendations, regardless of purchase completion

**8. RISK LOG**
1. Fake Discounts
* Likelihood: Low
* Impact: High (loss of trust, reduced retention)
* Mitigation:
- Trigger: Discount displayed
- Action: Validate against actual pricing engine
- Fallback: Show only verified prices; no discount display if unavailable

2. Accent Recognition Failure
* Likelihood: Low
* Impact: Medium (incorrect recommendations, friction)
* Mitigation:
- Trigger: Low confidence in voice input
- Action: Prompt user to repeat (max 2 attempts)
- Fallback: Request text input

3. Regional Language Limitation
* Likelihood: Low
* Impact**:** Medium (accessibility barrier)
* Mitigation:
- Trigger: Unsupported language detected
- Action: Default to supported language
- Fallback: User relies on external assistance (future scope: multilingual expansion)

4. Latency / Server Issues
* Likelihood: Low
* Impact: Medium–High (drop-offs, poor UX)
* Mitigation:
- **Trigger:** High response latency
- Action: Show loading indicators and status messaging
- Fallback: Inform users of temporary service degradation

5. Health & Allergy Misinterpretation
* Likelihood: Low–Medium
* Impact: Very High (user safety, legal risk)
* Mitigation:
- Trigger: Health/allergy-related query
- Action: Do not answer; provide mandatory disclaimer
- Fallback: Block progression after repeated prompts without user acknowledgment

6. Repetitive or Biased Recommendations
* Likelihood: Medium
* Impact**:** High (reduced trust, perceived bias)
* Mitigation:
- Trigger: Repeated exposure to same listings
- Action: Diversify recommendations based on ratings, reviews, and relevance
- Fallback: Override sponsored prioritization in ranking logic

**9. GUARDRAILS**
1. Health & Allergy Safety
* Rule: No inference or response on health/allergy queries
* Rationale: Prevents critical user safety risks and legal exposure
* Fallback (Trigger → Action → Fallback):
- Trigger: Health-related query
- Action: Provide disclaimer only
- Fallback: After 3 repeated prompts, restrict progression until user confirms with restaurant

2. Payment Control
* Rule: No automatic payments
* Rationale: Ensures financial transparency and prevents unauthorized transactions
* Fallback:
- Trigger: Attempt to automate payment
- Action: Block action
- Fallback: Enforce standard checkout flow

3.Pricing Integrity
* Rule: No display of unverified discounts
* Rationale: Maintains trust and pricing transparency
* Fallback:
- Trigger: Discount unavailable/invalid
- Action: Show actual price only
- Fallback: Disable coupon manipulation

4.Sponsored Listing Neutrality
* Rule: No bias toward sponsored content in core recommendations
* Rationale: Preserves recommendation quality and user trust
* Fallback:
- Trigger: Ranking influenced by sponsorship
- Action: Re-rank based on quality signals (ratings, reviews, relevance)
- Fallback: System-level enforcement (non-overridable)

5.Data Privacy
* Rule: Protect all user data
* Rationale: Prevents legal risk and maintains user trust
* Fallback:
- Trigger: Data usage scenario
- Action: Adhere to privacy policies and consent framework
- Fallback: Provide user control (opt-in/opt-out for data usage)

**10. MVP SCOPE**
1. What’s IN the MVP
- Text and voice chat with AI that provides recommendations based on user requests.
- Hard-coded refusal logic for any allergy, ingredient, or health-related inquiries, forcing users to contact the restaurant directly.
- Applying real discounts only—no fake discounts.
- Recommending food based on ratings and reviews.
- Ensuring data privacy.
- Although most processes are automated, payments, cancellations, and changes are handled by users.
- Showing only three recommended UI cards. If more options are needed, a “Show More” button will display up to two additional options.
- Feedback prompt after every AI interaction.

2. What’s OUT of the MVP
- Auto-payment — not in scope; payment remains fully under user control.
- Understanding all regional languages.
- Accent handling.
- Table reservations and dine-in bookings.

3. Why this scope
- Trust and safety are the primary focus. By prioritizing user safety and building trust, we can achieve long-term success. This approach also protects us from potential financial and legal issues. Once the MVP is live and gathers feedback, we can identify what needs improvement, what to add, and what to remove.

**11. LAUNCH PLAN**
1. Launch Phases
- After creating the AI assistant MVP, we will first provide it to the testing team and conduct rigorous testing to ensure it works properly checking for server stability, accurate text and voice responses, correct recommendation of exactly three UI cards, proper application of discounts, and overall system reliability.
- We will then move to an internal dogfooding phase with Zomato employees to gather honest and direct feedback. This will include both technical and non-technical teams to validate usability and functionality from different perspectives.
- After internal testing, we will implement necessary improvements and prepare the MVP for launch.
- Following this, we will conduct a small beta with approximately 1,000–5,000 Zomato Gold users in a single city (such as Bengaluru or Mumbai) before expanding nationwide. This ensures city-level validation before a full rollout.

2. Success Signal
- After successful city-level testing, we will proceed to a national rollout. Initially, the MVP will be available only to Zomato Gold users. Feedback will be collected after every interaction to evaluate user satisfaction and system performance at scale. Based on these insights, improvements will be made before releasing the feature to all users.
- The key metric for moving from the Bengaluru/Mumbai beta to a national rollout is: the order conversion rate via the AI assistant reaching a defined threshold (X%) among Zomato Gold beta users.

3. Rollback Plan
- With rigorous testing and internal feedback, the failure rate is expected to be low. However, if any issues arise, a feature-flag-based kill switch will be used to instantly disable the AI assistant.
- Users will see a message such as: *“Improving for you for a smoother experience. We’ll be back soon.”*
- Meanwhile, the engineering team will investigate and resolve the issue within 24 hours before re-enabling the feature.