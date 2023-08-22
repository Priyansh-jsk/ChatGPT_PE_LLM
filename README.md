# ChatGPT Prompt Engineering for Developers Course- Notes

![2023-08-17 17_52_18-DLAI - Learning Platform Beta](https://github.com/Priyansh-jsk/ChatGPT_PE_LLM/assets/58244081/2ac1e47b-b105-441d-818d-c3455a2ccef9)

The power of Large Language Models(LLM) as a developer tool, that is using API calls to LLMs to quickly build software applications.

**_There are two types of LLMs-_**

_**Base LLM**_

-> Predicts next word, based on text training data.

**Input:** _Once upon a time, there was a unicorn_
**output:** _that lived in a magical forest with all her unicorn friends_

**Input:** _What is the capital of France?_ 
**output:** 
_What is France’s largest city?_  
_What is France’s population?_  
_What is the currency of France?_

_**Instruction Turned LLM**_

Tries to follow instructions: 

-> Start off with a base LLM that’s been trained on a huge amount of text data.
-> Fine-tune on instructions and good attempts at following those instructions.
-> Technique called RLHF (reinforcement learning from human feedback)
-> helpful, honest, harmless.

**Input:** _What is the capital of France?_
**output:** _The captial of France is Paris._


_Load OpenAI Key_

![2023-08-17 18_27_58-DLAI - Learning Platform Beta](https://github.com/Priyansh-jsk/ChatGPT_PE_LLM/assets/58244081/82e356b5-73d2-4d43-9bff-f8f3ccf8d769)


_Model used_

we will use the OpenAI gpt-3.5-turbo model. This helper function will make it easier to use prompts and look at the generated outputs:

![2023-08-17 18_25_10-DLAI - Learning Platform Beta](https://github.com/Priyansh-jsk/ChatGPT_PE_LLM/assets/58244081/514b7825-1e99-4dd2-8594-a621cdee28b5)


**Principles of prompting:**

1. Write clear and specific instructions.
2. Use delimiters like: ```, """, < >, <tag> </tag>, : 
3. Ask for structured output-> HTML, JSON, etc.
4. Check whether conditions are satisfied to do a task.
5. Few examples of the sorts of task prompting completion.
6. Give the model time to think.
7. Specify the steps to output the task, breaking down the solution into neat steps.
8. Make the output in a specified format for better parsing.
9. Instruct the model to find its own solution before rushing to a conclusion.
10. Iterations are important. There is no perfect prompt, but using a process to improve can help refine ideas and prompts.

_**Iterative-prompt-development**_

![2023-08-22 13_43_00-DLAI - Learning Platform Beta](https://github.com/Priyansh-jsk/ChatGPT_PE_LLM/assets/58244081/8c408e0d-430e-4a76-b362-43435dd29828)

**Prompt Guidelines**
- Be clear and specific.
- Analyze why the result does not give the desired output.
- Refine the idea and the prompt.
- Repeat

**Iterative Process**
- Try something.
- Analyze where the result does not give what you want.
- Clarify instructions, and give more time to think.
- Think to Refine prompts with a batch of examples

**_Example:_**
Assume we have a text prompt- Generate a marketing product description from a product fact sheet.
""" 
OVERVIEW
- Part of a beautiful family of mid-century-inspired office furniture, 
including filing cabinets, desks, bookcases, meeting tables, and more.
- Several options of shell color and base finishes.
- Available with plastic back and front upholstery (SWC-100) 
or full upholstery (SWC-110) in 10 fabric and 6 leather options.
- Base finish options are stainless steel, matte black, 
gloss white, or chrome.
- Chair is available with or without armrests.
- Suitable for home or business settings.
- Qualified for contract use.

CONSTRUCTION
- 5-wheel plastic coated aluminum base.
- Pneumatic chair adjust for easy raise/lower action.

DIMENSIONS
- WIDTH 53 CM | 20.87”
- DEPTH 51 CM | 20.08”
- HEIGHT 80 CM | 31.50”
- SEAT HEIGHT 44 CM | 17.32”
- SEAT DEPTH 41 CM | 16.14”

OPTIONS
- Soft or hard-floor caster options.
- Two choices of seat foam densities: 
 medium (1.8 lb/ft3) or high (2.8 lb/ft3)
- Armless or 8-position PU armrests 

MATERIALS
SHELL BASE GLIDER
- Cast Aluminum with modified nylon PA6/PA66 coating.
- Shell thickness: 10 mm.
SEAT
- HD36 foam

COUNTRY OF ORIGIN
- Italy
"""

We have some issues with performing this prompt text data. 

**Issue 1:** The text is too long 
Limit the number of words/sentences/characters.

**Issue 2:** Text focuses on the wrong details
Ask it to focus on the aspects that are relevant to the intended audience.

**Issue 3:** Description needs a table of dimensions
Ask it to extract information and organize it in a table.

Let's see now, How to Load Python libraries to view HTML.

We have the following commands to view HTML.

_from IPython.display import display, HTML_

_display(HTML(response))_

