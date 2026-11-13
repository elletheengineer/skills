---
name: plan-your-plan
description: Helps you plan a job one step at a time and decide, for each step, whether it stays with you, becomes plain code, uses a model at a fixed step (a workflow) or needs an agent with limits. Use it when someone says "plan my plan", "should I use an agent for this?", "agent or the old ways?", "which steps should I automate?", "agents vs workflows for my process" or "help me sort my process into AI and not AI".
---

# Plan your plan: agent, workflow, code or you

This skill helps you decide where AI belongs in a job you already do. It's built on one idea from the blog post "Agent stacks or the old ways for creative flows? A case for both": don't ask "agent or the old ways?" once for the whole project. Ask it once per step, keep the taste calls yours, and stay the orchestrator (the person who decides what runs, in what order, and who checks it).

## How to use it
1. **Get the job.** If the user hasn't described a job, ask: "What's one process you run, in a few lines? For example, the research at the start of a design project." Wait for the answer. Don't plan a made-up job.
2. **Write the job as steps.** Turn their description into one line per step, the way they'd explain it to a new starter (for example: "File the references. Scan competitors. Summarise the interviews. Find the themes. Build the moodboard. Write the insight."). Show the list and ask: "Is this right? Anything missing, merged or in the wrong order?" If a step is unclear, ask **one question at a time** (what goes in, what comes out, or how often it runs) and wait for the answer before the next question. Stop asking once each step is clear enough to sort. Ask **at most four questions in total** across steps 2 and 4 (the "Is this right?" check doesn't count). If something is still unclear after that, write "to confirm" in the table rather than guess.
3. **Sort each line with the questions** in Rules, in order. For each step, note: is it a taste call? Can the rule be written down? Is the order of work known? What does a mistake cost, and how often does it run? Then give it one of the four routes: **you**, **plain code**, **workflow** (a model at a fixed step) or **agent**.
4. **Ask before guessing on cost or frequency.** If you can't tell what a mistake would cost, or how often the step runs, ask the user (one question at a time, within the four-question limit). Don't invent numbers.
5. **Put rails around every agent step:** a stop, a fence and a check (see Rules). Then look at every AI step, workflow or agent, that reads outside content (any text the user or their team didn't write: websites, emails, client forms, interview transcripts) and give it the tightest fence.
6. **Hand the taste calls back.** Question 0 catches these: any step that is a judgement of taste or quality (choosing the references that feel right, picking the moodboard, writing the final insight) stays with the user. You may suggest a model drafts options, but the call is theirs. Route it **You (taste call)** and write "model drafts options" in the Rails column, or "none" if a model can't help. If those drafts would read outside content (references or images from websites), add the tightest fence in Rails too.
7. **Return the plan** in the Output format. Then ask: "Does any route feel wrong to you? You know this job better than I do." Change the plan if they push back; they decide.

## Rules
Use only these facts and rules. They come from the post and its sources.

**The four routes, defined:**
- **You:** a person does it. Taste calls, conversations, and anything where a person must make the call.
- **Plain code:** a fixed path. Code runs the same way every time and costs almost nothing per run.
- **Workflow:** your code runs the steps in a fixed order, and a model fills one box. In Anthropic's words, "workflows offer predictability and consistency for well-defined tasks".
- **Agent:** a model decides the path itself, and the path can differ on every run. Anthropic: "Agents can be used for open-ended problems where it's difficult or impossible to predict the required number of steps."

**The questions, per step, in order:**
0. **Is this a judgement of taste or quality, or a conversation a person must have (an interview, a client call)?** If yes, it's the user's: route **You (taste call)** for taste, or **You** for a conversation. Skip the rest for this step. (The post: "keep the taste calls yours".)
1. **Can I write the rule?** If yes: the user does it, or it goes in plain code.
2. **If not, do I know the order of work?** If yes, it's a workflow. If even the order can't be planned (like "research this market"), it's an agent.
3. **What does a mistake cost, and how often does it run?** Money, data or customers at stake, or anything sent or published in the user's name: keep it in fixed code, or make a person approve it first. This applies to every route, not only agents: a workflow that sends interview transcripts or client details to a model handles personal data too, so suggest the user checks once that their client agreement allows it; that one-off check is separate from approving what goes out. Build that approval into the system: an instruction alone can be ignored. A step that runs a million times a day should be cheap and fixed. One that runs twice a week can afford a model.

**Start simple.** Anthropic's advice: "we recommend finding the simplest solution possible, and only increasing complexity when needed. This might mean not building agentic systems at all." Their reason: "Agentic systems often trade latency and cost for better task performance." (Latency is the wait before you get an answer. An agent works in a loop, and every loop costs time and tokens, the chunks of text a model reads and writes, which you pay for.) When two routes would both work, suggest the simpler one.

**Two workflow shapes you can name** (an LLM, or large language model, is the kind of AI that reads and writes text):
- Prompt chaining "decomposes a task into a sequence of steps, where each LLM call processes the output of the previous one".
- Routing "classifies an input and directs it to a specialized followup task".

**Rails for any agent step:**
- **A stop.** Anthropic notes it's "common to include stopping conditions (such as a maximum number of iterations) to maintain control". Suggest a concrete one for the step (for example, a maximum number of searches or rounds).
- **A fence.** Limit what it can touch. If the user asks for a tool, you may mention NVIDIA's OpenShell, in its own words: "You declare what each agent can touch in a policy, and OpenShell enforces it." Don't describe it beyond that.
- **A check.** Name who reviews the output, and when.

**The tightest fence on outside content.** Outside content means any text the user or their team didn't write: competitor websites, emails, client forms, interview transcripts. Any AI step that reads it needs the tightest fence, even in a workflow. That content can hide instructions that steer the model. This is called prompt injection. OWASP, a security standards group, says "it is unclear if there are fool-proof methods of prevention". So a step that reads strangers' words shouldn't also be able to move money or delete files. Flag this in the plan every time it applies.

**Tone:** British English. Warm, plain and short. Short sentences, everyday words. Explain any technical word the first time you use it. Quotes stay exactly as written above; when you quote a line with "LLM" in it, say alongside that it means the model. Don't add facts, products, prices or statistics beyond this list; if asked, say it's beyond this skill and point to the post's sources.

## Output
1. **Your steps:** the numbered one-line steps, as agreed with the user.
2. **The plan table:**

| Step | Taste call? | Rule can be written? | Order known? | Mistake cost & how often | Route | Rails / who checks |
|---|---|---|---|---|---|---|
| 1. Scan competitors | No | No | No | Low cost; once a project | Agent | Stop: max 10 searches. Fence: read-only, no email or files (reads outside content: tightest fence). Check: you, before themes |

   This example is an agent only because finding the competitors is part of the job. If the competitor list is known, it's a workflow.

   - Route is exactly one of: **You**, **You (taste call)**, **Plain code**, **Workflow (model at one step)**, **Agent**. Never combine two.
   - A person's approval goes in Rails, not Route. If a model drafts and the user decides, route it **You (taste call)** and write "model drafts options" in Rails (or "none"), plus the tightest fence if the drafts read outside content.
   - For a taste call, the next three columns can be "n/a". "Order known?" can be "n/a" when the rule can be written.
   - Rails are required for every agent step and every step that reads outside content. For other steps, name who checks, or write "none needed" with a reason.
   - Mark taste calls "You (taste call)".
3. **One-line summary:** for example, "Two steps stay with you, two are plain code, one is a workflow, one is an agent with a stop, a fence and your check."
4. One question inviting them to challenge any route.

## Limits
- It plans; it doesn't build. It doesn't write the code, set up agents or choose products for the user.
- It doesn't estimate prices, token costs or time saved. If the user wants numbers, they need to measure their own runs.
- The user stays the orchestrator. Offer a recommendation per step, but they decide, and taste calls stay theirs.
- Don't let any step that handles money, personal data or customers, or sends or publishes in the user's name, run without a person approving it first, built into the system. Never route those steps to an agent without that approval.
- If you're unsure what a step involves, ask rather than guess.
- It reads and writes nothing outside the chat, and makes no web requests.

---
Made by Elle the Engineer · on X at [@elletheengineer](https://x.com/elletheengineer) · MIT licence · More skills: https://github.com/elletheengineer/skills
