# ChatGPT Prompt Engineering for Developers Course- Notes

![2023-08-17 17_52_18-DLAI - Learning Platform Beta](https://github.com/Priyansh-jsk/ChatGPT_PE_LLM/assets/58244081/2ac1e47b-b105-441d-818d-c3455a2ccef9)

The power of Large Language Models(LLM) as a developer tool, that is using API calls to LLMs to quickly build software applications.

**_There are two types of LLMs-_**

_**Base LLM**_

-> Predicts next word, based on text training data.

**input:** _Once upon a time, there was a unicorn_
**output:** _that lived in a magical forest with all her unicorn friends_

**input:** _What is the capital of France?_ 
**output:** 
_What is France’s largest city?_  
_What is France’s population?_  
_What is the currency of France?_

_**Instruction Turned LLM**_

Tries to follow instructions: 

-> start off with a base LLMs that’s been trained on a huge amount of text data.
-> Fine-tune on instructions and good attempts at following those instructions.
-> Technique called RLHF (reinforcement learning from human feedback)
-> helpful, honest, harmless.

**input:** _What is the capital of France?_
**output:** _The captial of France is Paris._


_Load OpenAI Key_

![2023-08-17 18_27_58-DLAI - Learning Platform Beta](https://github.com/Priyansh-jsk/ChatGPT_PE_LLM/assets/58244081/82e356b5-73d2-4d43-9bff-f8f3ccf8d769)


_Model used_

we will use OpenAI gpt-3.5-turbo model. This helper function will make it easier to use prompts and look at the generated outputs:

![2023-08-17 18_25_10-DLAI - Learning Platform Beta](https://github.com/Priyansh-jsk/ChatGPT_PE_LLM/assets/58244081/514b7825-1e99-4dd2-8594-a621cdee28b5)


**Principles of prompting:**

1. Write clear and specific instructions.
2. Use delimiters like: ```, """, < >, <tag> </tag>, : 
3. Ask for structured output-> HTML, JSON etc.
4. Check wheather conditions are satisfied to do a task.
5. Few examples of the sorts of task prompting completion.
6. Give the model time to think.
7. Specify the steps to output the task in, breaking down the solution into neat steps.
8. Make the output in a specified format for better parsing.
9. Instruct the model to find its own solution before rushing to a conclusion.
10. Iterations are important. There is no perfect prompt, but using a process to improve can help refine ideas and prompts.
