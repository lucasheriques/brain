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
## Write clear and specific instructions

You should express  what you want a model to do by providing instructions that are as clear and specific as you can possibly make them. Clear =/= short. In many cases, writing longer prompts provide more clarity and context for the model, which can actually lead to more detailed and relevant outputs.

### Tactic 1: Use delimiters
- Delimiters can be anything like: triple backticks, """, < >, `<tag> </tag>`, `:`

Using delimiters is also helpful to avoid prompt injections. 

Prompt injections happens if the user is allowed to have some input into your prompt. They might give kind of conflicting instructions to the model that might make it follow the user's instructions rather than doing what you want it to do.


1. Give the model time to think
