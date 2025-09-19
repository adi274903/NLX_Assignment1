**Phase 2: Prompt Engineering Mastery**

The following are the prompts used per task:


**1. Classification/Analysis:**

Categorizing or evaluating complex information from transcript and correctly giving the ICD, CPT and HCPCS code for the same.

----
- CLEAR PROMPT: 

*Prompt:*
You are a medical coding expert and have access to the ICD9, CPT and HCPCS Database. Ensure that you give the exact code for the given diseases mentioned below. 
Also give the HCPCS or CPT code for the given diseases treatment. Ensure it is in a structured format such that Disease is followed by its icd code and treatment with it's CPT/HCPCS code.

- Hypertension

- Diabetes mellitus, type II 

- Acute myocardial infarction (heart attack)

- Asthma

*Reasoning:* 
The given prompt is based on ensuring that the AI only refers to ICD9, CPT and HCPCS code base and does not get confused with other datasets it might be trained on. The context here is that it is a medical coding expert, length here is just a few words, explicitly the diseases are mentioned, audience here is the billing agent and role is to ensure accurate retrieval of the codes.

*Expected Output:*

XXXX
Hypertension, unspecified: (401.9)
CPT: 99212–99215 

Diabetes mellitus, type II or unspecified: (250.00)
CPT: 99212–99215

Acute myocardial infarction (heart attack) :(410.90)
CPT: 99221–99223 

Asthma, unspecified: (493.90)
CPT: 99212–99215

*Failure:*
There could be potential for failure as no examples are given for the AI model to give the exact output. I would consider it giving any of the CPT codes i nthe given range as a success for the given prompt. It could still go to the ICD 10 databse which would be problematic.


----
- Few-Shot PROMPT:

*Prompt:*

You are a medical coding expert and have access to the ICD9, CPT and HCPCS Database. Ensure that you give the exact code for the given diseases mentioned below. 
Also give the HCPCS or CPT code for the given diseases treatment. Ensure it is in a structured format such that Disease is followed by its icd code and treatment with it's CPT/HCPCS code. Example for it is shown below

- Hypertension : ICD9 401.9
  
  CPT: 99201, 99202
  
- Diabetes mellitus, type II: 250.00
  
  CPT: 99212, 99213

- Acute myocardial infarction (heart attack)
  
  CPT: 99221, 99222

Do the same for the given disease now :

Asthma

*Reasoning:* 

The given prompt is based on the CLEAR prompt with few shot learning approach. We can see that there are 3 examples for the given prompt so that the AI can replicate and give adequate response.

*Expected Output:*

XXXX
Asthma, unspecified (493.90):

CPT: 99212, 99213

*Failure:*
The prompt could result in problems as CPT code might be a range and not just 2 numbers. The prompt might also fail if AI does refer to a different databse, which it should not due to the provided examples.


----
- Chain-of-Thought PROMPT:

*Prompt:*

You are a medical coding expert and have access to the ICD9, CPT and HCPCS Database. Ensure that you give the exact code for the given diseases mentioned below. 
Also give the HCPCS or CPT code for the given diseases treatment. Ensure it is in a structured format such that Disease is followed by its icd code and treatment with it's CPT/HCPCS code. Example for it is shown below

- Hypertension : ICD9 401.9
  CPT: 99201, 99202
  Reasoning: The following is unspecified hypertension so ICD 401.9. CPT codes associated with the highest probability and in ascending order is 99201 and 99202 based on the management part.

Also give the reasoning as to why you chose the given ICD and CPT codes for the below diseases.

- Diabetes mellitus, type II
- Acute myocardial infarction
- Asthma

*Expected Output:*

Diabetes mellitus, type II or unspecified (250.00):
CPT: 99212–99215
Reasoning: XXXX

Acute myocardial infarction (heart attack) (410.90):
CPT: 99221–99223 
Reasoning: XXXX

Asthma, unspecified (493.90):
CPT: 99212–99215
Reasoning: XXXX

*Reasoning:* 
The given prompt is based on the Few shot, CLEAR and reasoning. The given is for reasonign through the databse, finding appropriate codes and giving output based on the given codes. An example was given so that the AI could structure the response and give response in the format.

*Failure:*
AI could always refer to other CPT codes not associated with the given disease or not in the given range as CPT codes are different based on outpatient, inpatient, etc. 




****
**2. Generation/ Creation:**

The model will be assessed based on how well the model summarizes the text based on 2 categories (patient facing and clinician facing).

----
- CLEAR PROMPT: 

*Prompt:*


*Reasoning:* 
The given prompt is based

----
- Few-Shot PROMPT:

*Prompt:*


*Reasoning:* 
The given prompt is based

- Chain-of-Thought PROMPT:

*Prompt:*


*Reasoning:* 
The given prompt is based



****

**3. Question-Answering:**

The model will be assessed based on a specific prompt and its accuracy in answering the question. A dataset containing 3Q & A with the exact verifiable prognosis/ treatment/ procedure would be made to assess the model’s domain knowledge and specificity. MedQA is a dataset that would be used for evaluation.

----

- CLEAR PROMPT: 

*Prompt:*


*Reasoning:* 
The given prompt is based

----

- Few-Shot PROMPT:

*Prompt:*


*Reasoning:* 
The given prompt is based

----

- Chain-of-Thought PROMPT:

*Prompt:*


*Reasoning:* 
The given prompt is based



