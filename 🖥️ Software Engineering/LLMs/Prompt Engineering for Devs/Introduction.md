There are two types of Large Language Models (LLMs)

## Base LLM
Predicts next word, based on text training data

```md
Prompt: Once upon a
```



## Instruction Tuned LLM

think of giving instructions to another person

when a LLM doesn't work, sometimes it's because those instructions were not clear enough

# Guidelines

some principles and tactits to apply when working with LLMs:
## Principle 1: Write clear and specific instructions

You should express  what you want a model to do by providing instructions that are as clear and specific as you can possibly make them. Clear =/= short. In many cases, writing longer prompts provide more clarity and context for the model, which can actually lead to more detailed and relevant outputs.

### Tactic 1: Use delimiters
- Delimiters can be anything like: triple backticks, """, < >, `<tag> </tag>`, `:`

Using delimiters is also helpful to avoid prompt injections. 

Prompt injections happens if the user is allowed to have some input into your prompt. They might give kind of conflicting instructions to the model that might make it follow the user's instructions rather than doing what you want it to do.


### Tactic 2: Ask for a structured output
JSON, HTML, etc.

```python
prompt = f"""
Generate a list of three made-up book titles along \ 
with their authors and genres. 
Provide them in JSON format with the following keys: 
book_id, title, author, genre.
"""
```

#### Tactic 3: Ask the model to check whether conditions are satisfied

```python
text_1 = f"""
Making a cup of tea is easy! First, you need to get some \ 
water boiling. While that's happening, \ 
grab a cup and put a tea bag in it. Once the water is \ 
hot enough, just pour it over the tea bag. \ 
Let it sit for a bit so the tea can steep. After a \ 
few minutes, take out the tea bag. If you \ 
like, you can add some sugar or milk to taste. \ 
And that's it! You've got yourself a delicious \ 
cup of tea to enjoy.
"""
prompt = f"""
You will be provided with text delimited by triple quotes. 
If it contains a sequence of instructions, \ 
re-write those instructions in the following format:

Step 1 - ...
Step 2 - …
…
Step N - …

If the text does not contain a sequence of instructions, \ 
then simply write \"No steps provided.\"

\"\"\"{text_1}\"\"\"
"""
response = get_completion(prompt)
print("Completion for Text 1:")
print(response)
```

Completion for Text 1:
Step 1 - Get some water boiling.
Step 2 - Grab a cup and put a tea bag in it.
Step 3 - Once the water is hot enough, pour it over the tea bag.
Step 4 - Let it sit for a bit so the tea can steep.
Step 5 - After a few minutes, take out the tea bag.
Step 6 - Add some sugar or milk to taste.
Step 7 - Enjoy your delicious cup of tea!

```python
text_2 = f"""
The sun is shining brightly today, and the birds are \
singing. It's a beautiful day to go for a \ 
walk in the park. The flowers are blooming, and the \ 
trees are swaying gently in the breeze. People \ 
are out and about, enjoying the lovely weather. \ 
Some are having picnics, while others are playing \ 
games or simply relaxing on the grass. It's a \ 
perfect day to spend time outdoors and appreciate the \ 
beauty of nature.
"""
prompt = f"""
You will be provided with text delimited by triple quotes. 
If it contains a sequence of instructions, \ 
re-write those instructions in the following format:

Step 1 - ...
Step 2 - …
…
Step N - …

If the text does not contain a sequence of instructions, \ 
then simply write \"No steps provided.\"

\"\"\"{text_2}\"\"\"
"""
response = get_completion(prompt)
print("Completion for Text 2:")
print(response)
```

Completion for Text 2:
No steps provided.

#### Tactic 4: "Few-shot" prompting

```python
prompt = f"""
Your task is to answer in a consistent style.

<child>: Teach me about patience.

<grandparent>: The river that carves the deepest \ 
valley flows from a modest spring; the \ 
grandest symphony originates from a single note; \ 
the most intricate tapestry begins with a solitary thread.

<child>: Teach me about resilience.
"""
response = get_completion(prompt)
print(response)
```
Grandparent: Resilience is like a tree that bends with the wind but never breaks. It is the ability to bounce back from adversity and keep moving forward, even when things get tough. Just like a tree that grows stronger with each storm it weathers, resilience is a quality that can be developed and strengthened over time.

## Principle 2: Give the model time to “think” 

if a modal is making reasoning errors by rushing to an incorrect conclusion, you should try reframing the query to request a chain or a series of relevant reasoning before the model provides its final answer. 

Another way to think about this is that if you give a model a task that's too complex for it to do in a short amount of time or in a small number of words, it may make up a guess which is likely to be incorrect. And you know, this would happen for a person too. If you ask someone to complete a complex math question without time to work out the answer first, the would also likely to make a mistake.

So, in these situations, you can instruct the modal to think longer about a problem, which means it's spending more computational effort on the task.  

#### Tactic 1: Specify the steps required to complete a task





1. Give the model time to think
