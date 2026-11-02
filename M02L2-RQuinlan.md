# Module 2 Lab 2: Metric Selection Under Cost Pressure

Submission template. 20 points. Fill this document in as you work, then upload it to Canvas with your notebook and a PDF of the full notebook run. Check Canvas for the due date.

## Your Unique Values

**Your name:**

Ryne Quinlan

**Scenario you chose for Step 1 (scenario_id):**

S2 - Enterprise spam filter

**GitHub portfolio repository URL:**

https://github.com/RQuinlan-SMC/aws-ai-portfolio

**Date and time you last ran your notebook top to bottom:**

11/2/26


## Prediction 1: Accuracy Versus Recall

*Write this BEFORE Step 1. Look only at the four counts for your chosen scenario. Will accuracy be higher or lower than recall, and by roughly how much? An honest wrong prediction earns full credit.*

**My prediction and reasoning:**

Accuracy would be higher than recall as there is a larger amount acting as the divisor compared to just the predicted positives(TP and FN). Roughly by .2 is what I predict.


## Step 1: One Scenario by Hand

*No code, and cover the computed columns in the file. Show every division.*

**TP, FP, FN, TN for my scenario:**

TP = 1200
FP = 95
FN = 310
TN = 48000

**Accuracy, with arithmetic:**

Accuracy = (TP + TN) / everything

= .992

**Precision, with arithmetic:**

Precision = TP / (TP + FP)

= 0.92

**Recall, with arithmetic:**

Recall = TP / (TP + FN)

= 0.79

**F1, with arithmetic:**

F1 = 2PR / (P + R)

=  0.81

**Do these match the file's columns within rounding? If not, what was the error?:**

All match except for F1 which I believe is beacuse I just did the math with 2 decimal places when excel most likely did 4.

**Prediction 1 compared with what I found:**

I was correct with accuracy being greater then the recall by about .2.


## Step 2: All Four in Code

*The code lives in your notebook. Record the result here.*

**Do my computed columns match the file for all four scenarios?:**

Yes only some rounding differences

**Any mismatch I found and how I fixed it:**

Only rounding differences no actual issues


## Prediction 2: Accuracy Versus Cost

*Write this BEFORE you run Step 3. Will the scenario with the highest accuracy also have the lowest total error cost?*

**My prediction and reasoning:**

Yes, as if the system is accurate there would be no issues as the correct answer is always able to be given/the wrong issue always flagged.


## Step 3: Total Error Cost

| Scenario | Accuracy | Total error cost $ | Rank by cost (1 = highest) |
|---|---|---|---|
| S1 |.9900 | 500008 | 1 |
| S2 |.9918 | 7520   | 4 |
| S3 |.9930 | 27140  | 3 |
| S4 |.9536 | 343000 | 2 |

**Prediction 2 compared with what the table showed:**

The greater the accuracy does not always mean the lowest total error cost, as S3 has a technical higher accuracy and a larger total error cost compared to S2 which has a slightly lower accuracy of .002 difference.


## Step 4: Metric Call for Each Scenario

*Write all four calls before you open the instructor key column.*

| Scenario | Metric I would optimize | Error type that drove the choice, in two sentences |
|---|---|---|
| S1 | Accuracy | The price for false negative is $250,000 which is a high error to pay. | Compared to the false negative price of $1 one would want to make sure to be as accurate as possible.
| S2 | Precision | Being precise is key when dealing with finding spam. | Looking at the cost of a false positive that $40 can add up the more legit emails are filtered to be spam.
| S3 | Recall | You want to make sure of the defects found which were actual defects. | The cost of both the false negative and false positive can be brutal, so knowing which parts have the defect will help check for both.
| S4 | Accuracy | Want to make sure that everything is good on the patient's side before surgery is considered or happens. | It costs $3,200 for loans not approved slipping through the cracks as the triage is still done. The more accurate the check of the pre-approval will help any extra costs.

**After opening the key: where I disagreed, and why:**

I did not see a key on the document



## Step 5: S4 Threshold Sweep

*Model at least five settings. Each step adds 4 false positives and removes 1 false negative.*

| Step | False positives | False negatives | Total error cost $ |
|---|---|---|---|
| 0 | 130 | 95 | 343000 |
| 1 | 131 | 94 | 340100 |
| 2 | 132 | 93 | 337200 |
| 3 | 133 | 92 | 334300 |
| 4 | 134 | 91 | 331400 |
| 5 | 135 | 90 | 328500 |

**Step with the lowest total cost:**

5th step

**Dollar saving against step 0:**

343000 - 328500 = $14500


## Reflection

*In your own words, no AI assistance. Answer from your own run. Graders check these answers against your notebook outputs.*

**1. Report your Step 3 prediction and what the table actually showed. Quote your own accuracy and total error cost figures for at least two scenarios.:**

I believed the greatest the accuracy the lowest the cost but it was not true as the lowest cost technically had a lower accuracy. Scenario 2 had an accuracy of .9918 and a cost of 7520 which made it the lowest cost, but compared to S3 with an cost of 27140 it had a higher accuracy of .9930. By my prediction S3 should have been the lowest, proving me wrong that the lowest accuracy did not mean the lowest cost.

**2. Scenario S1 has an accuracy of 0.99 in the file. Explain, using the actual counts, why that number is close to meaningless and what you would report to a hospital administrator instead.:**

The number to look at is not the accuracy of 0.99 as this does not give the information wihch action can be taken. Instead look at the total error cost of $500,008. This is what the hospital would pay for possibly errors made for missed screenings. Look to the money as the important variable to base a system off of.

**3. Your S4 threshold sweep found a minimum. State the setting and the dollar saving against the starting point. Then say what would have to be true operationally for that setting to be a bad idea anyway.:**

The minimum was found at step 5 with a total of $328,500. This came from increasing the false positives by 5 and decreasing the false negatives by 5. The amount saved was $14500 compared to the inital step 0. For this to happen operationally there would be more false positive loan pre-aproved triage so more patients told they did not have the pre-aproval and less false negatives of patients not having the aproval and getting the triage done. This scenario is a bad idea as more patients would contact the hospital/insurance company about why they were not pre-aproved even when it is a false positive. The cost may be lower than the original but more people would be effected in a negative way with more triage that needed to be done not done more calls and adminstrative help as patients call about the false positives.


## AI Use Disclosure

*List any AI tool you used, what you used it for, and how you checked what it produced. Write None if you used none. Predictions and reflection answers must be your own work with no AI assistance.*

**Tools used:**



**What I used them for:**



**How I verified the output:**




## Before You Submit

- [ ] I computed one scenario entirely by hand before writing code
- [ ] My reflection quotes my own numbers, not the example numbers
- [ ] Both predictions were written before I ran the matching step
- [ ] I recorded the actual result for both predictions, including any I got wrong
- [ ] Notebook runs top to bottom with every output visible
- [ ] PDF exported after that full run and it matches
- [ ] Work pushed to my GitHub portfolio repository and the URL is above
- [ ] Reflection answers written by me with no AI assistance
- [ ] Files uploaded individually, no archive
