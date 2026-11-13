# plan-your-plan

A free Claude skill that helps you plan a job one step at a time. You describe a process you run; it writes it as steps, keeps the taste calls with you, sorts every other step into you, plain code, a workflow (a model at one fixed step) or an agent, and puts a stop, a fence and a check around any agent step.

## Install
Copy the `plan-your-plan` folder into `~/.claude/skills/` (for all your projects) or into a project's `.claude/skills/` folder. Then start a chat with Claude.

## Example
You type:

> Plan my plan: at the start of a design project I gather references, look at competitors, read the client interviews, find the themes, make a moodboard and write the insight.

It replies, roughly:

> **Your steps:** 1. File the references. 2. Scan competitors. 3. Summarise the interviews. 4. Find the themes. 5. Build the moodboard. 6. Write the insight. Is this right?
>
> | Step | Taste call? | Rule can be written? | Order known? | Mistake cost & how often | Route | Rails / who checks |
> |---|---|---|---|---|---|---|
> | 1. File the references | No | Yes | n/a | Low; every project | Plain code | None needed: same every time |
> | 2. Scan competitors | No | No | No | Low; once a project | Agent | Stop: max 10 searches. Fence: read-only (reads outside content: tightest fence). Check: you |
> | 3. Summarise the interviews | No | No | Yes | High: client's customers' personal data; every project | Workflow (model at one step) | Tight fence (text you didn't write). Your approval built in. Check: you, against the transcripts |
> | 4. Find the themes | Yes | n/a | n/a | n/a | You (taste call) | Model drafts options from the summaries (same tight fence as step 3); you choose which themes stand |
> | 5. Build the moodboard | Yes | n/a | n/a | n/a | You (taste call) | Model drafts options, if you want them |
> | 6. Write the insight | Yes | n/a | n/a | n/a | You (taste call) | Yours |
>
> **Summary:** three steps stay with you (all taste calls), one is plain code, one is a workflow with your check, and one is an agent with a stop, a fence and your check. Does any route feel wrong to you?

It asks one question at a time when a step is unclear (four at most), and changes the plan when you push back. It plans; it doesn't build, and it doesn't estimate costs. You stay the orchestrator.

## The post
This skill comes from the blog post ["Agent stacks or the old ways for creative flows? A case for both"](https://x.com/elletheengineer), on X at [@elletheengineer](https://x.com/elletheengineer).

## Licence
MIT. Made by Elle the Engineer. More skills: https://github.com/elletheengineer/skills
