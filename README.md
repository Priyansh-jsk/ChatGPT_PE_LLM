# ChatGPT Prompt Engineering for Developers Course- Notes

![2023-08-17 17_52_18-DLAI - Learning Platform Beta](https://github.com/Priyansh-jsk/ChatGPT_PE_LLM/assets/58244081/2ac1e47b-b105-441d-818d-c3455a2ccef9)

The power of Large Language Models(LLM) as a developer tool, that uses API calls to LLMs to quickly build software applications. The importance of prompt engineering will continue to grow as time passes, given the increasing significance of AI and chatbots like ChatGPT in the future.

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

- Start off with a base LLM that’s been trained on a huge amount of text data.
- Fine-tune on instructions and good attempts at following those instructions.
- They are trained in RLHF (reinforcement learning from human feedback)
- They've been trained to be helpful, honest, and harmless. (e.g.: They're less likely to output toxic tests vs. base LLMs).

**Input:** _What is the capital of France?_

**output:** _The captial of France is Paris._


_Load OpenAI Key_

![2023-08-24 14_35_48-DLAI - Learning Platform Beta](https://github.com/Priyansh-jsk/ChatGPT_PE_LLM/assets/58244081/2813dd55-e550-4bcd-8bf4-3b001386edbb)

_Model used_

we will use the OpenAI gpt-3.5-turbo model. This helper function will make it easier to use prompts and look at the generated outputs:

![2023-08-17 18_25_10-DLAI - Learning Platform Beta](https://github.com/Priyansh-jsk/ChatGPT_PE_LLM/assets/58244081/514b7825-1e99-4dd2-8594-a621cdee28b5)


**Principles of prompting:**

1. Write clear and specific instructions.
2. Use delimiters like: ```, """, < >, <tag> </tag>, : 
3. Ask for structured output-> HTML, JSON, etc.
4. Check whether conditions are satisfied to do a task.
5. A few examples of the sorts of task prompting completion.
6. Give the model time to think.
7. Specify the steps to output the task, breaking down the solution into neat steps.
8. Make the output in a specified format for better parsing.
9. Instruct the model to find its own solution before rushing to a conclusion.
10. Model Limitations: Hallucinations

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

Iterations are important. There is no perfect prompt, but using a process to improve can help refine ideas and prompts
We have some issues with performing prompt text data. 

**Issue 1:** The text is too long 
Limit the number of words/sentences/characters.

**Issue 2:** Text focuses on the wrong details
Ask it to focus on the aspects that are relevant to the intended audience.

**Issue 3:** Description needs a table of dimensions
Ask it to extract information and organize it in a table.

Let's see now, How to Load Python libraries to view HTML.

**We have the following commands to view HTML.**

_from IPython.display import display, HTML_

_display(HTML(response))_

_**Summarizing**_

There's so much text we see in today's world, But we don't have to read all the things. So, Now one of the most exciting applications We have in the world which is the Large Language Model is to use it to summarize text, in an accurate way.

E.g., summarizing user reviews for brevity, etc.

- In summary, give more details about the intent of the summary viewer to help the response from ChatGPT focus on the relevant details from the original content.
- Extract information that removes other parts from the response, in summary, to focus exactly.
- Looping over a list can help summarize product sites quickly.
- Binary responses (positive or negative) can be used to help with programmatic use.
- Extracting a list of emotions from the writer for a text is also possible.

_Summarize with a word/sentence/character limit_

```
prod_review =
"""
Got this panda plush toy for my daughter's birthday, who loves it and takes it everywhere. It's soft and super cute, and its face has a friendly look. It's a bit small for what I paid though. I think there might be other options that are bigger for the same price. It arrived a day earlier than expected, so I got to play with it myself before I gave it to her.
"""
```

```
prompt = f"""
Your task is to generate a short summary of a product review from an ecommerce site. 

Summarize the review below, delimited by triple backticks, in at most 30 words. 

Review: ```{prod_review}```
"""

response = get_completion(prompt)
print(response)
```

**Output-** This panda plush toy is loved by the reviewer's daughter, but they feel it is a bit small for the price.

_Summarize with a focus on price and value_

```
prompt = f"""
Your task is to generate a short summary of a product review from an ecommerce site to give feedback to the pricing deparmtment, responsible for determining the price of the product.  

Summarize the review below, delimited by triple backticks, in at most 30 words, and focusing on any aspects that are relevant to the price and perceived value. 

Review: ```{prod_review}```
"""

response = get_completion(prompt)
print(response)
```

**Output-** The customer loves the panda plush toy for its softness and cuteness, but feels it is overpriced compared to other options available.

_Try "extract" instead of "summarize"_

```
prompt = f"""
Your task is to extract relevant information from a product review from an ecommerce site to give feedback to the Shipping department. 

From the review below, delimited by triple quotes extract the information relevant to shipping and delivery. Limit to 30 words. 

Review: ```{prod_review}```
"""

response = get_completion(prompt)
print(response)
```

**Output-** The shipping department should take note that the product arrived a day earlier than expected.

_Summarize multiple product reviews_
For example, We have three lengthy product reviews to be grouped into a list initially. The second is to implement a Python for loop to run the prompt on all the reviews.

_**Inferring**_

Inferring allows for the quick building and implementation of natural language processing systems. So, if we want to extract a sentiment, positive or negative, of a piece of text in the traditional M.L workflow, you have to collect the label data set, train a model Somewhere in the cloud, and make inferences that could work pretty well but it wants you to know just a lot of work to go through that process, and also for every task, such sentiment extracting names Versus.

E.g., sentiment classification and topic extraction.

1. Sentiment-> positive / Negative
2. Identify types of emotion 
    -> Identify anger-> In yes or no
3. Extract product and company name from Customer reviews.
4. Doing multiple tasks at once 
5. Inferring topics

To get infer 5 topics

Make a news alert for certain topics

_**Transforming**_

LLM is good at transforming its input to a different format, such as inputting a piece of text in one language and transforming it or translating it to a different language. ChatGPT is trained with sources in many languages. This gives the model the ability to do translations.

E.g., translation, spelling & grammar correction.

-> Tone transformation- The way we write changes depending on who we're writing for. ChatGPT can make different tones.

-> Format Conversion- JSON to HTML (table), transforming formats such as inputting HTML and outputting JSON.

-> Spellcheck / Grammer check- It fixes grammar if there is any wrong grammar in sentences. 

_**Expanding**_

Now, we are going to use a parameter of the LLM called temperature that will allow us to change the kind of variety of the model's response. So you can kind of to think of temperature as the degree of exploration or kind of randomness of the model.

E.g., automatically writing emails.

The two features to submission of your application with two properties:

-> Sentiment – A general feeling from the user on how they feel about an item. Either “positive” or “negative”

-> Review – A message composed by the user expanding on their feelings.

**Temperature-** 
The temperature parameter is used in the generation of text using language models to control the level of randomness and creativity in the generated text. Usually, the lower the temperature, the more likely GPT-3 will choose words with a higher probability of occurrence. A higher temperature leads to a more diverse and creative output.

![2023-08-24 14_11_33-DLAI - Learning Platform Beta](https://github.com/Priyansh-jsk/ChatGPT_PE_LLM/assets/58244081/fedbc707-4d27-412b-a944-5e7f99080e1d)

There are three important things we want to know:

_Temperature:_ Controls randomness, higher values increase diversity.

_Top-p (nucleus):_ The cumulative probability cutoff for token selection. Lower values mean sampling from a smaller, more top-weighted nucleus.

_Top-k:_ Sample from the k most likely next tokens at each step. Lower k focuses on higher probability tokens.

Let's understand in simple terms:

-> High temperature makes results more messy and varied.

-> Lower top-p values reduce diversity and focus on more probable tokens.

-> Lower top-k also concentrates sampling on the highest probability tokens for each step.

_**ChatBot**_

LLM also uses it to build custom chatbots with only a modest amount of effort.

-> ChatGPT the web interface is a way for you to have a conversational interface a conversation via a large language model.

-> We can also build a custom chatbot using LLM.

Note: While you want a chatbot to talk in a friendly way to users, when you need the information for working with, you'd like it to be less creative and more like what you expect. To do that, you can change the "temperature" setting to 0, which makes it act in a consistent and predictable manner.

Below is the sample Chatbot- OrderBot that will take orders at a pizza restaurant.  

![2023-08-24 14_52_41-DLAI - Learning Platform Beta](https://github.com/Priyansh-jsk/ChatGPT_PE_LLM/assets/58244081/2ae2c9a1-cbab-466b-8b45-e4aff7954639)

Here's a JSON summary of your food order:

![2023-08-24 14_53_16-DLAI - Learning Platform Beta](https://github.com/Priyansh-jsk/ChatGPT_PE_LLM/assets/58244081/7e3870aa-19ae-447c-8f97-f5dcc734cf7d)

Source:
ChatGPT Prompt Engineering for Developers course: https://www.deeplearning.ai/short-courses/chatgpt-prompt-engineering-for-developers/
