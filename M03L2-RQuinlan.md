# Submission Template: Module 3 Lab 2: Service Selection Under Constraints

Name: Ryne Quinlan    Date: 11/4/26   
GIT RQuinlan-SMCws-ai-portfolio:All of my ML projects

**How to use this file.** Work down it in order. Each section matches a step in the lab. Replace every line that starts with a chevron. Leave nothing blank: if a section does not apply, write why.

---

## 1. Your prediction, written first

Step 2 of the lab asks for this before you fill in the table. A wrong guess reasoned honestly earns full marks. A guess edited afterwards to match earns none.

**Which factor will appear most often:** COST

**How many of the eight (0 to 8):** 6

**One sentence on why you picked that factor**

The volume of many of the business requests are very large in the 10s to 100s thousands so I feel that how much it all costs will be a key factor. They will all be very expensive per month. And R4 has a $300 budget.

## 2. Your eight decisions

All eight requests are listed below. The latency, volume, and constraint columns are in m3_service_requests.csv. For each one: the obvious answer, your choice, and the factor. The factor must be one of capability-gap, latency, cost, language, compliance, output-shape, spelled exactly.

### R1. Read handwritten delivery notes photographed by drivers and pull out the recipient name and the signature date

- **Obvious answer:** Rekognition
- **My choice:** Textract
- **Factor:** Output-shape

**Why the obvious answer fails. Quote the constraint column**

 Due to the constraint the value is in the form fields not what the photo shows.

### R2. Transcribe recorded pharmacy consultations and flag every medication mentioned

- **Obvious answer:** Transcribe
- **My choice:** Comprehend
- **Factor:** Compliance

**Why the obvious answer fails. Quote the constraint column**

Comprehend has a medical version which can deal with clinical vocabulary.

### R3. Answer inbound customer phone calls with a voice bot that can book an appointment

- **Obvious answer:** Lex
- **My choice:** Lex
- **Factor:** Latency

**Why the obvious answer fails. Quote the constraint column**

Lex is the only service to make bots.

### R4. Translate a 60,000 word product catalog into six languages every week

- **Obvious answer:** Textract
- **My choice:** Transcribe
- **Factor:** Capability-gap

**Why the obvious answer fails. Quote the constraint column**

Transcribe is the only service that translates. It is also budget friendly for the volume.

### R5. Block uploaded profile photos that contain nudity or graphic violence before they appear on the site

- **Obvious answer:** Comprehend
- **My choice:** Rekognition
- **Factor:** Capability-gap

**Why the obvious answer fails. Quote the constraint column**

The constraint brings up the content and if it is permited, it does not have to do with if it is in the frame.

### R6. Find personally identifiable information in customer chat transcripts where roughly 40 percent of the chats are in Spanish

- **Obvious answer:** Textract
- **My choice:** Transcribe
- **Factor:** Language

**Why the obvious answer fails. Quote the constraint column**

The constraint says the detector has to be told which language it is reading and Transcribe will already intrepret the correct language.

### R7. Show a live human agent a running sentiment read on the chat they are handling so they can escalate

- **Obvious answer:** Textract
- **My choice:** Comprehend
- **Factor:** Latency

**Why the obvious answer fails. Quote the constraint column**

Need the analysis to be in real time. 

### R8. Turn 400 page quarterly compliance filings into a one page brief for the board

- **Obvious answer:** Comprehend
- **My choice:** Lex
- **Factor:** Output-shape

**Why the obvious answer fails. Quote the constraint column**

Needs new prose and not a list of extracted phrases.

## 3. Your chains

Step 3 of the lab. At least two of the eight need more than one service. Name the request, write the chain in order, and say what each stage produces.

### Constrained request 1

- **Request ID:** R6
- **The chain, in order:** Transcribe -> Translate -> Comprehend

### Constrained request 2

- **Request ID:** R2
- **The chain, in order:** Transcribe -> Comprehend Medical

**What each stage of each chain produces, one line per stage**

Request 1: 
A produces: The transcribed text
B produces: The translated text
C produces: The breakdown of the text into entities

Request 2:
A produces: A transcribed text
B produces: The breakdown of the medical vocabulary, each medication labeled

## 4. Your console verification

Step 4 of the lab. One service, run twice. Screenshots go in your submission as separate image files or collected into one PDF.

**Service I ran:** Translation

**Confidence on the easy input:** none shown

**Confidence on the awkward input:** not shown

**The awkward input I built, written out in full**

Hey, my nombre es Ryne how are you today.
I have tres gatos, inu as well.

**What changed between the two results, and whether the service warned me**

Written in a more casual tone, no warnings.

## 5. Your two cost estimates

Step 5 of the lab. The two highest volume requests. Arithmetic line by line, then the source and the date you read it.

### Constrained request 1

- **Request ID:** R5
- **Monthly total:**  2,100,000


### Constrained request 2

- **Request ID:** R7
- **Monthly total:** 9,000,000


**The arithmetic, line by line**

Request 1:

$0.001 For first million
$0.0008 for next 4 million

COST = 0.001(1000000) + 0.0008(1100000)
     = $1,880/month


Request 2:

$0.0001 up to 10M units.

COST = 0.001(9000000)
     = $9,000/month




**Pricing page URL and the date I read it**

https://aws.amazon.com/rekognition/pricing/?nc2=type_a 11/4/26

https://aws.amazon.com/comprehend/pricing/ 11/4/26
**One sentence: is this plausible for that business**

Yes to the content checking of costing 1,880 a month, but the Comprehend cost might be too much at $9k a month.

## 6. Count what actually decided it

Step 2 again, at the end. Count how many times each factor appeared in your finished table, then compare against the prediction you wrote at the top of this file.

**The factor that appeared most often:** Capability-gap and Output-shape

**How many times, out of eight:** Each 2 out of the 8

## 7. Break it on purpose

Paste the exact error text. Not a description of it.

### Break 1: Take the service you verified in Step 4 and send it an empty input, then an input in a language it does not support.

**Exact error or behavior I observed:**

With an empty input I got back nothing, as there was nothing to translate.

When I put in Vulcan(Star Trek), it repeated the same input back to me.
Dif-tor heh smusma = Live long and prosper

**What this tells me about how it works:**

Vulcan is not an actual language which can be translated and you need to input something for it to translate something.

### Break 2: Take one of your chains and remove the middle stage. Describe what the chain now produces.

**Exact error or behavior I observed:**

Constrained request 1

- **Request ID:** R6
- **The chain, in order:** Transcribe -> Translate -> Comprehend
Taking out the translate step.
Some transcriptions will be in spanish. 

**What this tells me about how it works:**

If you take out the translate step then you would miss the %40 of the possible chats that are in spanish.

### Break 3: Recompute one Step 5 estimate at fifty times the volume.

**Exact error or behavior I observed:**

Request 2:

$0.0001 up to 10M units.

COST = 0.001(9000000)
     = $9,000/month

For now 50M units:

From 10M-50M units = $0.00005

COST =  9,000 + (0.00005)*(40,000,000)
     =  $11,000/month



**What this tells me about how it works:**

Take the original $9k a month from the first million then add on 40 million times the price after 10 million which is 40 million. 
Add it all up and get the solution of $11k a month.

## 8. Results - See earlier sections for values

**Your eight row table**

> Posted in step 2

**Your chains, with each stage labeled**

> Posted in step 3

**Your Step 4 results, easy input and awkward input, with confidence scores if shown**

Easy:
Hello, my name is Ryne Quinlan.
I am a student at SMC.

Hola, me llamo Ryne Quinlan.
Soy estudiante en SMC.

Awkward:
Hey, my nombre es Ryne how are you today.
I have tres gatos, inu as well.

Hola, mi nombre es Ryne, ¿cómo estás hoy?
Tengo tres gatos, y Minu también.

**Your two cost estimates with sources and dates**

### Constrained request 1

- **Request ID:** R5
- **Monthly total:**  2,100,000


### Constrained request 2

- **Request ID:** R7
- **Monthly total:** 9,000,000


**The arithmetic, line by line**

Request 1:

$0.001 For first million
$0.0008 for next 4 million

COST = 0.001(1000000) + 0.0008(1100000)
     = $1,880/month

Request 2:

$0.0001 up to 10M units.

COST = 0.001(9000000)
     = $9,000/month

**Pricing page URL and the date I read it**

https://aws.amazon.com/rekognition/pricing/?nc2=type_a 11/4/26

https://aws.amazon.com/comprehend/pricing/ 11/4/26

## 9. Reflection

Your own words. No AI assistance. Graders check these against the rest of your submission.

### 1. Report your Step 2 prediction about which factor would dominate, then count what actually dominated in your finished table. Give both numbers out of eight and say what the gap taught you.

I got two uses for both Capability-gap and Output-shape. It taught me that the cost is not usually the problem and that it is the output or what the service can actually do compared to what is aiming to get done.

### 2. Paste the awkward input you built in Step 4 and both results. Say whether the service told you it was struggling or returned something confidently wrong, and explain why that difference matters for a system you would put in front of customers.

"Hey, my nombre es Ryne how are you today.
I have tres gatos, inu as well."

Translation:

Hola, mi nombre es Ryne, ¿cómo estás hoy?
Tengo tres gatos, y Minu también.

This is the awkward input I used for the translator. It idd struggle with me adding in japanese for dog (inu), as it showed me Minu, which means nothing. One should always be hesitant with translations, you never want to offend cutomers.

## 10. AI use disclosure

Required by the course AI Use Policy.

- **Tool used (write none if you used no AI):** Google Translate

**If you used one: what you asked it, what you kept, and how you checked it**

Asked it if what was translated by AWS Translator was correct by inputting it and checking the output. I just kept the knowedge that it was correct and wrote that the translation was correct in step 4.


## 11. Before you submit

- [ ] Predictions written before running
- [ ] Actual results recorded, including the ones I got wrong
- [ ] Exact error text captured for every break it item
- [ ] Reflection written by me
- [ ] Files uploaded individually, no archive
