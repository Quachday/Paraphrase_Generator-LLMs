# Paraphrase_Generator-LLMs
In this project, I utilized GenerativeAI with Large Language Models for the task of paraphrasing English sentences.
I experimented in Google Colab environment, using Flan-T5-base as original model and dataset :sharad/chatgpt-paraphrases-simple from hugging face.


![image](https://github.com/Quachday/Paraphrase_Generator-LLMs/blob/main/Images/lifecycle.png)


The project goes through some stages (in GenAI lifecycle) including:
1. Scope: Define the use case - Paraphrasing
2. Select: Choose pretrain model (LLM one - here I chose Flan-T5-base from Hugging face)
3. Adapt and Align model:
- Prompt engineering (zero-shot, one-shot, few-shot): The results were good enough for the task after I tried several ways to modify the prompts.
Note: You can select other LLMs to test and consider whether or not they suit for your task.
![image](https://github.com/Quachday/Paraphrase_Generator-LLMs/blob/main/Images/prompt0.PNG)



As you can see, the model tends to answer the question.


![image](https://github.com/Quachday/Paraphrase_Generator-LLMs/blob/main/Images/prompt1.PNG)


With one-shot, by giving an example, the results are better (the completion just changed the main verb of the sentences) - still not completely paraphrased but acceptable to keep going.
- Fine-Tuning:
We have some choices for this phase: full-training or peft (parameter-efficient fine-tuning - lora) - which consider to update low rank parameters of the original model.
With the power of free-Colab environment, running 1 epochs gets ~15G gpu, leading to out of resources -> Bad inferences.

![image](https://github.com/Quachday/Paraphrase_Generator-LLMs/blob/main/Images/full_train.PNG)

After that, I tried with PEFT, which requires much, much less compute resourse (~1% compared to the full training) -> The performance improved a lot.

![image](https://github.com/Quachday/Paraphrase_Generator-LLMs/blob/main/Images/peft.png)

- Evaluation:
Quantitative Evaluation: ROUGE and (BLEU) are utilized by using lib.

![image](https://github.com/Quachday/Paraphrase_Generator-LLMs/blob/main/Images/Evaluation.PNG)

Qualitative Evaluation: Human. 


