PRD v0 — Zomato AI Food Assistant
Author: Ashik K Shetty
Date: 25 March 2026
Status: Draft

## 1. PROBLEM STATEMENT
Zomato users — especially new and occasional users — feel overwhelmed by too many choices on the home page and miss relevant offers, leading to decision fatigue and abandoned orders.

## 2. TARGET USERS
-Abhay, 25, SDE, Bengaluru — daily Zomato 
 user frustrated by endless scrolling and 
 missing discounts. Wants quick recommendations 
 and auto-applied coupons.
-Arun, 40, Professor, Bengaluru — occasional 
 user overwhelmed by cluttered UI. Orders for 
 family of 4 on Sundays. Needs simple guidance 
 and voice/text assistance.

## 3. JOBS TO BE DONE
From Abhay:
When I come home after a long shift, I want 3-4 great recommendations based on my budget, so I can order quickly before I get hangry.
When I'm ready to checkout, I want to be sure I'm getting the best deal, so I don't feel like I'm wasting money by missing a coupon.
From Arun:
When I want to order an afternoon meal or late-night dessert for my family, I want the app to just recommend the best options, so I can order peacefully without getting confused by the tech.
When I am ready to pay, I want discounts to be applied automatically, so I can save money without having to hunt for promo codes.

## 4. AI FIT DECISION
a) It automates the tedious work—like finding budget-friendly food, booking tables, and applying discounts—while acting as a helpful assistant whenever the user asks a question via text or voice.
b) I think it needs to be a mix of both. The AI should automate the heavy lifting: recommending food based on my budget, automatically applying the best discounts, and booking a table just from a quick voice or text command. However, for the final steps, the AI should only augment (or assist) the user. When it comes to checking the cart, making last-minute swaps to the food or restaurant, and actually paying the bill, the human needs to stay in 100% control.
c) It should NEVER automatically pay the bill or guess anything related to health and allergies. For example, if someone asks, "Does this dish have peanuts?", the AI shouldn't just guess; it needs to tell the user to confirm directly with the restaurant.
d) If the AI messes up payments, the user could get overcharged and lose money. Even worse, if the AI guesses incorrectly about a food allergy, it could literally lead to a life-or-death situation for the user.

## 5. SUCCESS METRICS
*North Star Metric- Order conversion rate via AI assistant — target X% (note: to be defined post pilot data) increase within 60 days of launch.
*3 Supporting Metrics- a) X% (note: to be defined post pilot data) of voice/text queries result in a completed recommendation. b) Auto apply coupon feature success rate 90%. c) 90% user satisfaction after AI recommends food and the user orders.
*One Guardrail Metric: the numbers I don't want to rise are- a) self-payment and self-booking without user permission for now it’s 0% if it rises it would be a huge problem. b) AI irrelevant suggestion rate should stay below 5% post-launch.

## 6. OUTPUT SPECIFICATION
*Output Format Keep it simple: Text or Voice + Swipeable Cards. Text (For users like Abhay): A quick reply like "Found 3 top dishes for you," immediately followed by the UI cards. Voice (For users like Arun): A short audio heads-up like, "Here are three options for you." The AI should never read out the whole menu—that’s just annoying. Give them the audio confirmation, but keep the actual control visual. The visual layout: Horizontal, swipeable UI cards.
*Output Content (What's on the card) The cards need to be super clean and not cluttered. Every card must have: The basics: Dish pic, Dish Name, and Restaurant details. The money part: Old price crossed out, final price crystal clear, and the exact promo code highlighted in green, so they know it worked (e.g., "₹180 — ₹40 saved with WELCOME50"). Don't make the user do the math. Action: A straightforward, 1-click "Add to Cart" button.
*Output Constraints (The strict rules) Stop decision fatigue: Show exactly 3 recommendations to start. "Show more" logic: If they hit the "Show more" button, the AI gives a max of 2 extra options. That's it. Money guardrail: Zero automatic payments. The AI never pays without the user going through the standard Zomato checkout. Health/Allergies: No guessing. If someone asks about allergens, the AI must drop this exact disclaimer: "Please check directly with the restaurant regarding specific allergy information before ordering."

## 7. EVALUATION RUBRIC
1.What makes a good recommendation? 
when a user asks the assistant "I wanna eat tiramisu under 300 or 400 " it must show 3 Ui cards with tiramisu pic and hotel name with best ratings and applied discounts, shows estimated delivery time if it does this perfectly it has done a good recommendation
2.What makes a bad recommendation? 
when a user asks the assistant "I wanna eat paneer butter masala" and if it suggests butter chicken masala, show pic of fried rice that's a bad recommendation or suggest hotels with bad reviews that's a bad recommendation
3.Who evaluates it? 
*it's completely evaluated by humans 1st by the Zomato team before releasing 
* after releasing to users when the ai assistant suggested all the recommendations from ai   we can integrate a small msg to rate the experience or give feedback for any improvements whether the user bought any food or not

## 8. RISK LOG
-Fake discounts: applying fake discounts and confusing users. As users have complete control over their payments, if it's fake,users might lose trust 
*How likely is it - low 
*How bad is it if it happens - high  
*What's your mitigation plan- show the true price, if there's discounts apply it or else don't. People are very fond of money if we play with that emotion, we might lose users

-Accent issue: If anybody uses voice chat and talk in their accent it might be sometimes difficult for ai to understand and it will recommend wrong items
*How likely is it- Low 
*How bad is it if it happens- Medium 
*What's your mitigation plan- If Ai couldn't get it properly it should ask two times to spell it properly if not ask them to type the food name people who know to type will type but others should seek external help. If we can advance Ai to understand every accents, then it would be very helpful but it's kinda advanced tech let's see in the future so we can implement it

-Regional Language Issue: if Ai just knows to talk or reply in English I guess it would be difficult for people who doesn't know to type or speak in English ,leading to communication problem 
*How likely is it- Low 
*How bad is it if it happens- Medium 
*What's your mitigation plan- who knows English might talk or type but who doesn't know it will be very difficult so we should make Ai to understand every local language of India and other countries where Zomato is available and they don't speak English. I guess as sarvam ai is growing rapidly we can implement it in future for now seeking external help is the only choice

-Server low or buffering: loading of Ui cards takes long time to show people who are hungry or in urgent need lose hope in app, get hangry- make something by themselves, eat outside or sleep hungry  
*How likely is it- Low 
*How bad is it if it happens- medium to high 
*What's your mitigation plan- when its rare we can't help sometimes server slows down or if there's network issue, but we can always invest in best servers or if can't at least we can inform users like "Problem in server today in Zomato" so the user is kinda mentally prepared 

-The health hazard: without knowledge and with full confidence tells it's safe to eat or confidently tells the user a dish is safe when it may not be, no disclaimer given this leads to life and death situation for a person 
*How likely is it- Low to medium  
*How bad is it if it happens- very high 
*What's your mitigation plan- for everyone their life is dear, so there should be no mistake happening. If the user asks anything related to allergy or something related to health in any condition the ai must not give any answer how much the user might ask to tell. It should just give a clear disclaimer "Can't answer health or allergic related issues, Please ask the respected hotel/cafe to clear the doubt, Be safe than sorry!"

-AI recommending the same restaurants repeatedly: favoring paid/sponsored listings shouldn't be a blockage for a user to eat good food from amazing hotel with best reviews and rating 
*How likely is it - Medium 
*How bad is it if it happens- High 
*What's your mitigation plan- customizing the ai to promote any sponsored hotel/item whenever the user asks it should display UI cards based on taste,hygiene,rating & reviews

## 9. GUARDRAILS
1.
* The Rule: No guessing on health issues and allergies 
*The Why: As for everyone their life is dear, we can't play or take risks in such matters. If anything bad happens the user might be facing life and death situation, and our company will be in big trouble 
*The Fallback: when a user forces to let an AI answer, the AI will not break under any circumstance and tell the user it's safe or some vague answer it will again and again give disclaimers. Even though doesn’t stop after 3 disclaimer we will stop them the action immediately not let them order until and unless they ask the hotel/cafe about the dish 
2.
*The Rule: Auto payment
 *The Why: Because people are fond of their own hard earned money and if the ai mistakenly  pays less or more or let the security system weak and make it easy for the hackers to hack and steal our entire amount it wont be good it will be an trust and legal issue
 *The Fallback: The ai mustn't even ask for auto payment option we wont implement such kind of option itself in the 1st place so user cant push past it
3.
*The Rule: Fake discounts
*The Why: when a user ask something and the ai shows the user Ui cards with actual price if discounts really available it will scratch the real price and show the discounted price but even though there's no discount it shouldn't show fake cut down of price because payment is done by humans at last so they'll get to know it will lead to trust issue
*The Fallback: show exact amount if discounts available apply it or else nope no problem as it is automatic by our side users cant use fake coupons 
4.
*The Rule: It shouldn't sponsored listing bias
*The Why: just because its sponsored it shouldn't come first it should always suggest the food and hotel which has amazing taste,good ratings and reviews this leads to trust gaining from users if the ai keeps the sponsored ones first and we are kind of cheating users for money and that's not humanity i know making money is important but not like this if we are honest in our work automatically we earn money from the trust we built
 *The Fallback: as it is ai automated user cant push past it 
5. 
*The Rule: data privacy
*The Why: data privacy is a major important thing for users as the user give their name,location,number and mainly what they're allergic to these are very private stuff so if it's gone to wrong hands we will facing trust and legal issues
 *The Fallback: users can't push past it in this matter its us and ai who must know sharing data is wrong. after user agreeing all terms & conditions we can pop a new message like we use your personal data for better ai usage if u dont want it u can toggle it on and off whenever u want

## 10. MVP SCOPE
1. What's IN the MVP - 
*Text and voice chat with AI based on the request it gives recommendations
*Hard-coded refusal logic for any allergy, ingredient, or health-related inquiries, forcing the user to contact the restaurant directly.
*Applying real discounts, no faking
*Recommending food based on ratings and reviews
*Data privacy
*Even though almost everything is automated payments and cancellation or change of choice done by humans 
*Showing only 3 recommended UI cards not more than that if need more options there will be button called "Show more" it will show max 2 options
*Feedback prompt after every AI interaction
2.What's OUT of the MVP- 
*Auto-payment — not in scope, payment remains fully in user control.
*Understanding all regional language 
*Accent handling 
*Reserving table & dine-in reservations
3.Why this scope- 
Trust and safety are the main motives. If we gain trust and care about the safety of our users, we will truly succeed. This protects us from financial and legal issues. Let the MVP run for a while after getting feedback we will get to know what to improve, what to add or delete.

## 11. LAUNCH PLAN
1.Launch Phases — 
*After creating an AI assistant MVP, first we will give that MVP to the testing team andgo through rigorous testing to check if it's working properly—whether the server crashes, gives proper text and voice messages back, recommends exactly 3 UI cards, applies discounts automatically, etc. 
*We then move to an internal dogfooding phase with Zomato employees to gather honest and direct feedback. This includes both tech and non-tech teams, ensuring usability and functionality are validated across different user perspectives.
 *After testing by our team and internal employees, we improve what's necessary and launch the MVP.
 *After internal feedback is incorporated, do a small internal beta with maybe 1000–5000 Zomato Gold users in one city first (Bengaluru or Mumbai) before going national. City-level testing before full rollout.
2.Success Signal — 
*After city-level testing, we go national. Initially, this MVP will be provided only to users with a Zomato Gold subscription. We will collect feedback after every interaction to understand user satisfaction and system performance at scale. Based on this, we will improve and later release it to all Zomato users. 
*The gate to move from the Bengaluru/Mumbai beta to a national rollout is: Order conversion rate via AI assistant reaches X% among Zomato Gold beta users in Bengaluru before expanding nationally.
3.Rollback Plan — 
*With rigorous testing and honest internal feedback, the failure rate is expected to be low. However, if any issues occur, a feature flag kill switch will be used to instantly disable the AI assistant via a toggle. Users will see a message like "Improving for you for a smoother experience,We'll be back soon." Meanwhile, engineering will investigate and resolve the issue within 24 hours before re-enabling the feature.




