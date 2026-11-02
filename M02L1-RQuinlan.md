# Module 2 Lab 1: Frame a Business Problem as a Machine Learning Problem

Submission template. 20 points. This lab has no notebook and no code. Fill this document in as you work, then upload it to Canvas. Check Canvas for the due date.

## Your Unique Values

**Your name:**

Ryne Quinlan

**Organization you chose in Step 1:**

American Girl

**GitHub portfolio repository URL:**

https://github.com/RQuinlan-SMC?tab=repositories

**Date you started this lab:**

11/1/26


## Step 1: Your Business Request

*Two sentences: what the organization is, and what it is asking for. Do not use the dental clinic example.*

**Organization and request:**

The organization is American Girl doll store. Losing sales from not accepting online discounts in-store.


## Prediction 1: Threshold

*Write this BEFORE Step 3. Is the right cutoff for your problem closer to 0.05, 0.5, or 0.9? An honest wrong prediction earns full credit. Do not edit it afterward.*

**My predicted threshold:**

.85

**One sentence of reasoning:**

The more we accept online discounts the more sales we make for the store.


## Step 2: ML Problem

*Fill in every line with something specific. No line may read depends or varies. This is a written form, not code.*

**Type (classification, regression, clustering, ranking, or none):**

binary classification (yes or no to discount)

**Input (one ____):**

one question if we accept the online sale in-store

**Features (at least five):**

Manager on duty says yes to discount, having the item available in-store, discount good enough for customer to bring up, customer previously been given online discount in-store, discount not too big

**Output:**

probability of saying yes to a question of accepting online discount

**Decision (if ____ then ____):**

if p > threshold then how much more is the customer willing to buy along with online discounted item(s)


## Step 3: Threshold From Money

*Show the arithmetic. If a figure is an estimate, label it as an estimate.*

**Cost of acting unnecessarily (false positive) $:**

$50 

**Cost of missing a real case (false negative) $:**

$250 estimate of a possible amount a customer might not pay if discount is denied, leaving the store and buying online only.

**Which figures are estimates, and how you estimated them:**

both FP and FN are estimates. FP estimate of a possible amount a discount might give. Most discounts are 15 to a max of 75% off of an item or set of items. FN estimate of a possible amount a customer might not pay if discount is denied, leaving the store and buying online only. Not allowing the discount leads a customer with a decent full cart to leave and pay only online. With the price of dolls at American Girl running at 135 not counting tax and other acessories $250 seems like a likely average cart.

**Arithmetic: p > FP cost / FN cost:**

p > 50/250

**Computed threshold:**

p > .2

**Prediction 1 compared with the computed threshold:**

I was horribly off as I predicted .85. This prediction is .65 over my actual of .2. I very much over thought my numbers to get such a difference. I was not thinking correctly of what threshold truly meant as I was thinking it had ties to how many times we allow discounts compared to the division of the FP/FN.


## Step 4: The Metric

**Metric I would optimize:**

Precision

**Defense in two sentences, tied to which error costs more:**

Needing precision of allowing the online sales is key to success. Making sure the whole of the leadership understand to allow discounts can help make less and less $250 transations leave the store.


## Step 5: Data and Its Weakest Point

**Labeled history required, roughly how much, and where it comes from:**

The percentage set on the discounts online and how it might reflect in-store. Seeing how many sales go live each weekend (roughly 1 or 2 a weekend) which comes from the higher ups in the company which work with the online store.

**The single weakest point in that data:**

How great a discount might be and how it effects the inventory of the store as a whole. Do we have enough to sell to all who want the discount and have enough to sell more of after the sale.


## Prediction 2: The Deciding Property

*Write this BEFORE Step 6. Which single property will decide the foundation model question: input modality, volume, latency, determinism, or explainability?*

**My predicted deciding property:**

determinism


## Step 6: Why or Why Not a Foundation Model

**My conclusion (WHY or WHY NOT a foundation model):**

Not a foundation model

**The one property that decided it:**

latency

**Prediction 2 compared with what actually decided it:**

Being able to quickly make decisions and mostly looking at the economic number side of each transaction either saved or lost.


## Reflection

*In your own words, no AI assistance. Answer from your own numbers. An answer that could have been written without doing the lab earns no credit.*

**1. Report your Step 2 threshold prediction and your Step 3 computed threshold. If they differed, explain what your instinct was tracking that the money was not, or the reverse.:**

I overly and wrongly predicted a much higher threshold not truly understanding what was being asked till I conducted the computed threshold. Seeing the computed and thinking of how it was calcuated made a lot more sense. I was thinking of a much greater possible discount as (200/250) would have made a closer threshold to my prediction.  

**2. State the weakest point in your data and explain concretely how a model trained on it could look successful in testing and still fail in production.:**

My weakest point was how a great discount could hurt the inventory of the store and damage overall sales. A successful model would be able to look at an inventory numbers and upcoming sales and calculate which discounts should be applied and which should not be. This could also fail if there is aslip and an overally high discount gets through and hurts the store's daily/weekend business.

**3. Someone senior tells you the threshold should be 0.5 because that is standard. Write the two sentence reply you would actually send, using your own numbers.:**

Looking at the actual numbers of an estimated possible discount and the average cart $50 and $250 shows a threshold at (0.2). The standard may be (.5) but in this case that would mean the discount would be $125. This discount would be too high and would hurt overall sales and not be in a sweet point to have both a great number of sales and use of online discounts. 


## AI Use Disclosure

*List any AI tool you used, what you used it for, and how you checked what it produced. Write None if you used none. Predictions and reflection answers must be your own work with no AI assistance.*

**Tools used:**



**What I used them for:**



**How I verified the output:**




## Before You Submit

- [ ] My threshold came from arithmetic, not from 0.5
- [ ] My data risk names something specific about how the label is produced
- [ ] Both predictions were written before I did the matching step
- [ ] I recorded the actual result for both predictions, including any I got wrong
- [ ] This template is pushed to my GitHub portfolio repository and the URL is above
- [ ] Reflection answers written by me with no AI assistance
- [ ] Files uploaded individually, no archive
