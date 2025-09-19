**Phase 2: Prompt Engineering Mastery**

The following are the prompts used per task:

----
**1. Classification/Analysis:**

Categorizing or evaluating complex information from transcript and identifying the disease and its symptoms would be the job of the AI. Giving the ICD code would also be ideal.


----
- CLEAR PROMPT: 

*Prompt:*
You are a medical expert who can identify and evaluate the exact disease and its ICD 10 code through the case study. The given is to help the biller quickly get the disease into the system. Give a 1 sentence answer. Given is the paragraph for it.

"This condition presents with increased thirst, frequent urination, fatigue, blurred vision, and slow-healing wounds. It is caused by the body’s ineffective use of insulin leading to elevated blood glucose levels. Diagnosis includes blood tests such as fasting glucose and HbA1c. Treatment involves lifestyle changes like a balanced diet and regular exercise to control blood sugar, oral medications like metformin, and insulin therapy if needed. Managing complications such as nerve damage, kidney issues, and cardiovascular problems is critical."

*Reasoning:* 
The given prompt ensures that the AI understands it's audience and context. The patient is 30 years old and is definitely not a medical expert like the AI. The AI needs to summarize the information and make it more understandable for the patient. 

*Expected Output:*

Diabetes Mellitus II, ICD 10 is E11

*Failure:*
Failure could occur due to context length as the transcript/ case is a paragraph. If the AI does not have enough medical knowledge or ICD 10 databse knowledge, the AI model will fail

----
- Few-Shot PROMPT:

*Prompt:*
You are a medical expert who can identify and evaluate the exact disease and its ICD 10 code through the case study. The given is to help the biller quickly get the disease into the system. Given is the paragraph for it.

"This condition presents with increased thirst, frequent urination, fatigue, blurred vision, and slow-healing wounds. It is caused by the body’s ineffective use of insulin leading to elevated blood glucose levels. Diagnosis includes blood tests such as fasting glucose and HbA1c. Treatment involves lifestyle changes like a balanced diet and regular exercise to control blood sugar, oral medications like metformin, and insulin therapy if needed. Managing complications such as nerve damage, kidney issues, and cardiovascular problems is critical."

Your response should be as follows:
"[Disease], ICD 10 is [Code]"

Here are a few examples for it:

- Hypertension, ICD 10 is I10.9

- Myocardial Infarction, ICD 10 is I21.9

*Reasoning:* 
The given prompt is based on the CLEAR prompt and gives exactly hwo the structure and output for it should be. 

*Expected Output:*

Diabetes Mellitus II, ICD 10 is E11

*Failure:*
Failure could occur due to context length as the transcript/ case is a paragraph. If the AI does not have enough medical knowledge or ICD 10 databse knowledge, the AI model will fail

----
- Chain-of-Thought PROMPT:
  
*Prompt:*
You are a medical expert who can identify and evaluate the exact disease and its ICD 10 code through the case study. The given is to help the biller quickly get the disease into the system. Give a 1 sentence answer. Given is the paragraph for it.

"This condition presents with increased thirst, frequent urination, fatigue, blurred vision, and slow-healing wounds. It is caused by the body’s ineffective use of insulin leading to elevated blood glucose levels. Diagnosis includes blood tests such as fasting glucose and HbA1c. Treatment involves lifestyle changes like a balanced diet and regular exercise to control blood sugar, oral medications like metformin, and insulin therapy if needed. Managing complications such as nerve damage, kidney issues, and cardiovascular problems is critical."

Your response should be as follows:
"[Disease], ICD 10 is [Code]"

Also give the reasoning for the given conclusion.

*Reasoning:* 
The given prompt is based on the CLEAR prompt and asks the AI model to reason the disease. As the disease is unspecified the given output should be E11 or similair category of E11.x as these are the codes related to the given disease. 

*Expected Output:*

Diabetes Mellitus II, ICD 10 is E11
Reasoning: xxxx

*Failure:*
Failure could occur due to context length as the transcript/ case is a paragraph. If the AI does not have enough medical knowledge or ICD 10 databse knowledge, the AI model will fail


****
**2. Generation/ Creation:**

The model will be assessed based on how well the model summarizes the text based on 2 categories (patient facing and clinician facing).

----
- CLEAR PROMPT: 

*Prompt:*
You are a transcription and medical expert who needs to explain to a 30 year old patient what condition they have alongwith the treatment they would be provided by the medical expert overseeing their case. Ensure you summarize it in 100 words maximum and also assess the patient's health status. Below is the a paragraph regarding it.

"This case involves a progressive respiratory disorder marked by chronic airflow limitation, primarily due to prolonged exposure to noxious inhalants leading to persistent inflammatory responses in the airway. The pathological process includes structural remodeling and alveolar destruction causing impaired alveolar-capillary gas exchange, manifesting clinically as exertional dyspnea, productive cough, and episodic wheezing. Pulmonary function testing confirmed the presence of obstructive ventilatory defect with a post-bronchodilator FEV1/FVC ratio below the diagnostic threshold.

Management encompasses comprehensive measures beginning with cessation of exposure to the inciting agent, combined pharmacotherapy with long-acting bronchodilators including beta2-agonists and muscarinic antagonists to relieve airway obstruction, and the addition of inhaled corticosteroids to attenuate airway inflammation in cases with frequent exacerbations. Adjunctive interventions include structured pulmonary rehabilitation to mitigate deconditioning and improve exercise capacity. For advanced disease, supplemental oxygen therapy is administered to maintain adequate tissue oxygenation, and surgical options may be considered in select cases.

Acute exacerbations are managed aggressively with systemic corticosteroids and targeted antimicrobial therapy if infectious etiology is suspected, as these episodes accelerate functional decline and increase morbidity. Continuous monitoring through serial spirometry and symptom evaluation guides optimization of therapeutic regimens to stabilize disease progression and enhance the patient's quality of life."

*Reasoning:* 
The given prompt ensures that the AI understands it's audience and context. The patient is 30 years old and is definitely not a medical expert like the AI. The AI needs to summarize the information and make it more understandable for the patient. 

*Expected Output:*
You have a lung condition called COPD, which means your airways are narrowed and damaged, making it hard to breathe. This happened mainly due to long-term exposure to harmful substances, like smoke. You may feel shortness of breath, cough often, and have wheezing. Treatment will focus on stopping exposure to these irritants, using inhalers that open your airways and reduce swelling, and doing exercises to improve lung strength. If needed, oxygen therapy may be used. It's important to manage flare-ups quickly with medication. Regular check-ups will help adjust treatment and keep your breathing as good as possible.

*Failure:*
Failure could occur due to context length as the transcript/ case is 3 paragraph long.

----
- Few-Shot PROMPT:

*Prompt:*
You are a transcription and medical expert who needs to explain to a 30 year old patient what condition they have alongwith the treatment they would be provided by the medical expert overseeing their case. Ensure you summarize it in 100 words maximum and also assess the patient's health status. Below is the a paragraph regarding it.

"This case involves a progressive respiratory disorder marked by chronic airflow limitation, primarily due to prolonged exposure to noxious inhalants leading to persistent inflammatory responses in the airway. The pathological process includes structural remodeling and alveolar destruction causing impaired alveolar-capillary gas exchange, manifesting clinically as exertional dyspnea, productive cough, and episodic wheezing. Pulmonary function testing confirmed the presence of obstructive ventilatory defect with a post-bronchodilator FEV1/FVC ratio below the diagnostic threshold.

Management encompasses comprehensive measures beginning with cessation of exposure to the inciting agent, combined pharmacotherapy with long-acting bronchodilators including beta2-agonists and muscarinic antagonists to relieve airway obstruction, and the addition of inhaled corticosteroids to attenuate airway inflammation in cases with frequent exacerbations. Adjunctive interventions include structured pulmonary rehabilitation to mitigate deconditioning and improve exercise capacity. For advanced disease, supplemental oxygen therapy is administered to maintain adequate tissue oxygenation, and surgical options may be considered in select cases.

Acute exacerbations are managed aggressively with systemic corticosteroids and targeted antimicrobial therapy if infectious etiology is suspected, as these episodes accelerate functional decline and increase morbidity. Continuous monitoring through serial spirometry and symptom evaluation guides optimization of therapeutic regimens to stabilize disease progression and enhance the patient's quality of life."

The structure of your response for it should be as follows:

"You have been diagnosed with [disease], due to [cause] and will be treated as follows [treatment/ procedure]."


*Reasoning:* 
The given prompt is based on the previous CLEAR prompt but now has a structured example of how the output. summary should be like. The given prompt ensures that the following format is followed by the LLM.

*Expected Output:*

You have been diagnosed with chronic obstructive pulmonary disease (COPD), due to long-term exposure to harmful inhalants causing damage and narrowing of your airways. Treatment will include stopping exposure to irritants, using inhalers that open your airways and reduce inflammation, and attending pulmonary rehabilitation to improve your breathing and fitness. For frequent flare-ups, corticosteroids and antibiotics may be prescribed. In advanced cases, oxygen therapy might be needed. Your health will be regularly monitored to adjust treatment and maintain lung function, aiming to improve your quality of life and reduce complications.

*Failure:*
Failure could occur if the LLM does not focus on the second half of the prompt giving the structure or it could fail due to context length constraitns.

----
- Chain-of-Thought PROMPT:

*Prompt:*
You are a transcription and medical expert who needs to explain to a 30 year old patient what condition they have alongwith the treatment they would be provided by the medical expert overseeing their case. Ensure you summarize it in 100 words maximum and also assess the patient's health status. Below is the a paragraph regarding it.

"This case involves a progressive respiratory disorder marked by chronic airflow limitation, primarily due to prolonged exposure to noxious inhalants leading to persistent inflammatory responses in the airway. The pathological process includes structural remodeling and alveolar destruction causing impaired alveolar-capillary gas exchange, manifesting clinically as exertional dyspnea, productive cough, and episodic wheezing. Pulmonary function testing confirmed the presence of obstructive ventilatory defect with a post-bronchodilator FEV1/FVC ratio below the diagnostic threshold.

Management encompasses comprehensive measures beginning with cessation of exposure to the inciting agent, combined pharmacotherapy with long-acting bronchodilators including beta2-agonists and muscarinic antagonists to relieve airway obstruction, and the addition of inhaled corticosteroids to attenuate airway inflammation in cases with frequent exacerbations. Adjunctive interventions include structured pulmonary rehabilitation to mitigate deconditioning and improve exercise capacity. For advanced disease, supplemental oxygen therapy is administered to maintain adequate tissue oxygenation, and surgical options may be considered in select cases.

Acute exacerbations are managed aggressively with systemic corticosteroids and targeted antimicrobial therapy if infectious etiology is suspected, as these episodes accelerate functional decline and increase morbidity. Continuous monitoring through serial spirometry and symptom evaluation guides optimization of therapeutic regimens to stabilize disease progression and enhance the patient's quality of life."

Also give your reasoning as to why you structured your summary the way you did.

*Reasoning:* 
The given prompt is based on the CLEAR prompt and now asks for the explanation for the given summary. This will assess how well the model performs the COT process and will be scored based on the Likert Scale for its reasoning and summarization.

*Expected Output:*
Summary of the given case and its reasoning.

"You have been diagnosed with [disease], due to [cause] and will be treated as follows [treatment/ procedure]."
Reasoning: XXXX

*Failure:*
Context length could be a failure and an incomplete answer might be given for the same. 


****

**3. Question-Answering:**

The model will be assessed based on a specific prompt and its accuracy in answering the question. A dataset containing diseases & with the exact verifiable ICD, CPT and HCPCS code to assess the model’s domain knowledge and specificity.ICD-CM Databse is a dataset that would be used for evaluation.

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


**Pilot Testing for each one of the CLEAR prompts was done using the CHATGPT 4o model and link is below:**
https://chatgpt.com/share/68cd6e98-aa0c-8007-b3a2-1b30c7d67493

