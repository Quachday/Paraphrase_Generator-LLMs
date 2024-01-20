# Paraphrase_Generator-LLMs
In this project, I utilized GenerativeAI with Large Language Models for the task of paraphrasing English sentences.
I experimented in Google Colab environment.

The project goes through some stages (in GenAI lifecycle) including:
1. Scope: Define the use case - Paraphrasing
2. Select: Choose pretrain model (LLM one - here I chose Flan-T5-base from Hugging face)
3. Adapt and Align model:
- Prompt engineering (zero-shot, one-shot, few-shot): The results were good enough for the task even though I tried several ways to modify the prompts.
Note: You can select other LLMs to test and consider whether or not they suit for your task.
- Fine-Tuning:
We have some choices for this phase: full-training or peft (parameter-efficient fine-tuning - lora) - which consider to update low rank parameters of the original model.
With the power of free-Colab environment, running 1 epochs gets ~15G gpu, leading to out of resources -> Bad inferences.
After that, I tried with PEFT, which requires much, much less compute resourse (~1% compared to the full training) -> The performance improved a lot.
- Evaluation:
Quantitative Evaluation: ROUGE and BLEU are utilized by using lib.
Qualitative Evaluation: Human. 


