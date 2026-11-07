# explain-it-back-machine-learning

A free Claude skill that checks your understanding of how machine learning works. You explain it in your own words; it tells you what you got right, names what's missing, and asks one question per gap until you've got all four steps: Loss, Direction, Move, Repeat.

## Install
Copy the `explain-it-back-machine-learning` folder into `~/.claude/skills/` (for all your projects) or into a project's `.claude/skills/` folder. Then start a chat with Claude.

## Example
You type:

> Explain it back: a model learns by looking at lots of data and getting it right eventually.

It replies, roughly:

> **What you got right:** the model learns from data, and it gets better over time.
>
> **What's missing:**
> - How it knows how wrong it is
> - How it decides what to change
>
> **Questions:**
> 1. Before a model can improve, what does it need to measure about its guess?
> 2. Once it knows how wrong it is, how does it know which way to change?

You answer, and it loops until your explanation covers everything.

## The post
This skill comes from the blog post ["How AI learns: by being wrong, a little less each time"](https://x.com/elletheengineer/status/2118427631053918217), on X at [@elletheengineer](https://x.com/elletheengineer)

## Licence
MIT. Made by Elle the Engineer. More skills: https://github.com/elletheengineer/skills
