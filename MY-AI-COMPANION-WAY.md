# MY WAY OF THE AI COMPANION

This document describes my evolution in AI usage during the last months.

## Stage 0 - Regular search engine (Jan 2025)

- Use as a search engine, search for terms, click on links

- **One line summary:** Better results than regular searches

## Stage 1 - Advanced search engine (Feb 2025)

- Use as a search engine with very detailed questions un natural language
- Specifically ask for "references about the answers"
- I started NOT reading documentation, but letting the AI summarize and answer my requests based on real documentation
- I had the option to check the original if I had any doubts or if got in a loop with the AI


- **Critical driver:** When I need to do something new, I spend a lot of time reading documentation.
- **AI Benefits:** This made switch from searching and reading documentation, to just let the AI explain it to me.
- **One line summary:** AI explains things to me

## Stage 2 - Text generator (Mar 2025)

- Use as a generator for technical texts
- I told it the general lines of a paragraph or section I needed to write, then told it to write it
- Used it as an initial draft of the definitive text
- Mostly copy & paste


- **Critical driver:** I had a deadline for a huge proposal which would take me a lot of time to write, even if we were perfectly capable of executing the job proposed.
- **AI Benefits:** This usage allowed me to focus on the technical design, writing a detailed outline, and then delegate the writing of the proposal text to the AI, based on that outline.
- **One line summary:** AI writes specialized texts for me

## Stage 2 - Initial steps in development (Jun 2025)

- Use as a generator of simple code snippets
- Asked simple things, like: "write me a simple playbook for installing program XXX", or "give me the exact command line to do YYYY"
- Also in copy & paste mode


- **Critical driver:** I needed to develop some new code for deploying applications, or do surgical fixes to existing deployment code.
- **AI Benefits:** This usage allowed me to be much faster in creating those fixes. Code was generated as small snippets that were manually copied, pasted and commited after verification. Craft work.
- **One line summary:** AI writes small code snippets for me

## Stage 3 - Give AI access to code repository (Nov 2025)

- Use as an advanced code generator
- Use a specific Development Environment (VS Code, Cursor, ...), install AI extension (Gemini Code Assist, Claude Code, ...)
- Run the IDE on the code repository with the AI extension enabled
- Use the agent window to interact with the AI and ask it for bigger code blocks
- Even for a general skeleton of an application, giving it some short directions about the general architecture
- I asked it to generate the application in a programming language that I did not know (GO), but tha seemed easy to review (sort of :-) )
- The AI generated a fully working app skeleton in 5 minutes


- **Critical driver:** I needed to develop an application with a tight deadline, and I would prefer it to be in the regular language used in my new company (GO) instead of the one I'm an expert with (Perl)
- **AI Benefits:** This usage allowed me to create an application and start working on it without any previous experience in GO programming. This also enabled me to read GO code completely focused on a present personal need, which is one of the best ways of learning a new language.
- **One line summary:** AI generates a full working application skeleton for me

## Stage 4 - Write prompts instead of interacting with the AI window (Jan 2026)

- "Talking" to the AI was soon shown to be repetitive and tedious, always writing the same things and conditions to ensure the answer were in line with my personal preferences and constraints
- I started writing a planning document at the beginning of the day, with the tasks that I would ask the AI to do in that day. Clearly separated, one section per task, in a Markdown document.
- The tasks started to be quite detailed, but in general language: "I need this function in the application, I need it to follow this architecture, Write code to this and that file, use this configuration style, etc."
- I spent about 1 hour per day doing that. Then I saved the document, went to the AI window and told it "read this document, follow its directions and start working on the tasks described"
- I did this for several days, adding more context, requirements, general directions and refining the general section of the prompt document, and each day, changing only the tasks to be done
- I specifically added a section telling it to add a section to the prompt file with a Task Completion status list with checkboxes that allowed me to check how was the work going on.


- **Critical driver:** I had the application skeleton, but I need to get to speed developing real functionality, and still I had no GO experience. But reading GO code made it easier and easier to review and validate the AI-generated code.
- **AI Benefits:** Enhanced speed and streamlined development of real application functionality
- **One line summary:** AI develops real application functionality for me, giving it detailed requirements

## Stage 4.1 - Fix production problems (Jan 2026)

- I asked for expert help in solving production issues (related to my area of expertise) that were blocking to some team mates and needed urgent solution
- Start with a temporary directory, write some of the problematic files in there
- Start Claude in that directory, describe the problem in detail, even copying and pasting some error and log lines
- Ask it for help to fix the problem
- Give it full access to tools that examine the affected systems and their state: kubectl commands, code review, access to logs, etc.
- _Talk_ to the agent, understand its tests, explanations and conclusions, give it feedback from me, and iterate until the problem is solved
- The agent researched for me and consulted documentation that I _knew_ existed, but that would take me a long time to analyze and use for fixing the problems


- **Critical driver:** Urgent problems with systems that were in my area of expertise, but which are very complex to reason about (e.g. complex Kubernetes deployments, environments where a full team deploys together, and sometimes in a non-coordinated form)
- **AI Benefits:** Agent researched, read documentation, analyzed, did systems tests and proposed solutions on each step, way faster than I can do it.
- **One line summary:** AI did troubleshooting in 3-40 minutes on a couple of problems that would have taken me 1-2 full days of work to solve by myself


## Stage 5 - Start using CLAUDE.md (Feb 2026)

- I continued doing this for several days, and in the process I realized that I was copying and pasting lots of text (requirements, constraints, recommendations) from one day to the next one
- I used the `/init` command in the repository base directory to make Claude read and analyze the whole repository, which by that time had the app skeleton, and some 2 or 3 functions already implemented.
- Claude wrote an initial CLAUDE.md file to the repository with a detailed decription of the application, its architecture, design and existing functions. The details were extremely focused and correct.
- I added to the CLAUDE.md all my constraints, requirements, etc. (in AI parlance these are called the "guardrails") that had to be followed at all times when working on that repo
- I continued to do tasks in my previous style: create daily prompt files with the tasks, but remove all the common things that I already had put in CLAUDE.md
- I started noticing that for each task the LLM context was getting almost full, so I decided to start a new context for each task. The relevant architecture constraints were in CLAUDE.md, and the updated status of each of the tasks was stored in the prompt document, so I lost no information.


- **Critical Driver:** I spent too much time copying and pasting from previous prompts
- **AI Benefits:** I centralized the way to work with the repository in a single document that is always loaded on each Claude session without explicitly telling the AI to do so
- **One line summary:** AI gets really fast developing new functionality with higher level requirements
  
## Stage 6 - Handovers (Mar 2026)

- I had started working day by day in a systematic way: writing a file named `YYYY-MM-DD.md` and storing them in a `.prompts` directory at each repository root (for all repositories I worked on during the day)
- I started seeing that when the context is getting full, the quality of the AI executed work is lower, and a fresh start is needed. For this I started using commands like "write your memories and prepare for handover".
- Soon I added this kind of command as a CLAUDE.md hint in a special section, and so when I felt it was time to recycle the session, I just had to command "handover" and start a new session after it finished writing.
- On the new session I usually start with "read your memories and resume work on task XX"

- **Critical Driver:** as time passes in the same session, output quality gets lower. A new session needs to be started, but saving the relevant parts of the current context
- **AI Benefits:** a fresh context makea AI work again full-tilt
- **One line summary:** AI also gets "tired" and needs to refresh

## Stage 7 - Using skills and Agent Teams (Mar 2026)

- Working linearly (one task after another) started to be a bottleneck and was slowing me down.
- The solution was to use the "Agent Teams" feature: when I need to work on a big functionality, or on different unrelated tasks, I start multiple agents in parallel. THis function is activated with prompts similar to "Using an Agent Team, work on the following tasks"
- Also, for any task, it would be good if the agent that runs the work was somehow specialized in that task. E.g.: when working on a web aplication, have a Backend expert, a Frontend expert and a Database expert. The solution for this is the "Skills" functionality, which is invoked by using prompts like the following one: "For this task, you are an Expert backend developer with lots of experience in design and implementation, knowledge of best practices, with technology XXX".
- The main agent is the "Task Coordinator"which _writes no code_ but instead takes care of managing the other agents and coordinating them: first assess with the System Architect, then do a plan and handover tasks to different specialists...
- I had to be careful with this one: starting several agents in parallel also burns LLM credits much faster.

- **Critical Driver:** having a single worker with generic experience execute tasks is a bottleneck and not the highest quality
- **AI Benefits:** you can have an unlimited number of additional agents running in parallel, with different specialized skills, and coordinating between themselves to do several tasks in parallel
- **One line summary:** use parallel specialized agents for faster and better work

## Stage 8 - Test plans (Apr 2026)

- I found that having the AI design and develop an application based only on requirement prompts was fine for simple applications. But when the complexity level raises, the code generated starts to drift from the requirements and has too much variability.
- The solution: based on the generic high level requirements, ask the AI itself to design a systematic test plan (system requirements) that can help track project progress anc compliance to the high level requirements.
- Prompts like "Using the requirements in documents XXX and YYY, design a detailed test plan for all functionalities" can be used to start the creation of the plan, and can be iterated until a realistic test plan is created.

- **Critical Driver:** I needed to track real progress in the project and the degree of compliance with the high level requirements
- **AI Benefits:** AI can be use for the systemtic work of translating the high level requirements to the low level ones, adequate for regular testing
- **One line summary:** use the AI to create your detailed test plans

## Stage 9 - Code review (Apr 2026)

- Having instructed the AI to create a full test plan from high level requirements, I found myself with a huge test plan (good!). But then when I started to work on fixing non-compliances, I found that the quality of the test plan itself was dismal, and AI had made up more than half of it: fictional functionalities, fake tests that always gave "PASS",... well, the AI had hallucinated a great part of the plan.
- The solution to this is Code Review: as a part of your development process, you instruct the AI to create the new piece of code (a test program, new functionality, whatever), and then ask the AI to launch an independent agent and have it review the output generated by the first agent.
- Prompts similar to tis one: "Develop functionality XXX according to requirements XXX.1, XXX.2, etc. When you are done, launch an independent agent expert in XXX, and make it review the generated code very critically."

- **Critical Driver:** small pieces of code or simple applications are generated easily by AI. But complex ones can be complete hallucinations that need to be controlled and eliminated.
- **AI Benefits:** having different skills and roles, you can have independent assessment of the code generated by one of your agents
- **One line summary:** use the AI to review other AI's code

## Stage 9.1 - Writing new skills (Apr 2026)

- After a few months on the same repo I noticed I was typing the same instructions at the start of every session: how to run the tests, how to prepare a handover, how to bump a version, how to launch an isolated work area for an agent. Those are not knowledge, they are **procedures**
- A "skill" is a procedure written down once, that the AI loads by itself when it recognises the situation. You don't invoke it: you describe your problem, and it shows up
- I did not write my skills from scratch. When you have spent a lot of time working on a single repo, the repo code, the prompt history, the documentation and the accumulated Claude memories already contain them - the work is **extracting** the procedure, not inventing it
- The distinction that took me longest to see, and the one I think almost everybody misses:
  - **Knowledge skills** - "you are an expert Kubernetes engineer", "you are an expert Perl developer". Easy to write, and everyone writes these first
  - **Method skills** - how verification works here, how you brief and review a team of agents, how a handover is written, what evidence is required before saying "it works"
  - **The value is in the second kind.** The model already knows Kubernetes better than my skill ever will. What it cannot possibly know is how *I* work
- Two tiers, and putting something in the wrong one hurts:
  - **Global** skills, valid in every project: debugging methodology, verification discipline, agent orchestration, shell scripting standards
  - **Project** skills: how THIS repo runs its test suite, its release sequence, its investigation playbooks
  - A project skill promoted too early becomes a global rule that is wrong everywhere else; a global lesson left local gets re-learned from zero on the next project
- Skills vs agents - I mixed these up for a while:
  - A **skill** is a procedure loaded into the session you are already in
  - An **agent** is a separate worker, with its own context, its own tools and its own restrictions
  - Rule of thumb: **a role becomes an agent, a procedure becomes a skill**. And they compose - my audit skill dispatches an auditor agent and then an independent reviewer agent on its output
- The mechanical detail nobody warns you about: **the description field is what decides whether the skill fires at all**. It is not a summary for a human reader, it is the trigger. A skill with an excellent body and a vague description simply never runs, and you end up concluding that skills don't work
- When to write one: **the third time** you repeat the same procedure. Any earlier and you are guessing which parts of it are actually stable
- Past a dozen skills I stopped remembering what I had, so I ended up writing a skill whose only job is to list my own skills and agents
- And the trap, which cost me dearly later: **a skill is executed, not merely read**. Stale documentation misleads you; a stale skill quietly does the wrong thing on your behalf, in your name, every time it fires (see Stage 13)

- **Critical Driver:** I was re-typing the same procedures at the start of every session, and getting a slightly different execution of them each time
- **AI Benefits:** my procedures run the same way every time without me having to remember to ask for them, and a new project inherits every one of them that isn't project-specific
- **One line summary:** write down how you work, not what you know

## Stage 10 - Executable guardrails (May 2026)

- By this point I had a long list of rules written in CLAUDE.md: never push to origin, never write to the main branch, never amend a commit, always use `git -C <path>` instead of `cd <path>`
- The agents followed them... most of the time. Every few days one of them didn't. And the ones they broke were, of course, the irreversible ones
- The realization: **a rule written in CLAUDE.md is a recommendation, not a constraint**. The agent reads it, and when the context fills up or the task gets complicated, it can forget it, reinterpret it, or decide that this particular case is an exception
- The solution is "hooks": small scripts that the tool runs BEFORE executing a command, and that can block it. I wrote five of them:
  - `block-push.sh` - blocks `git push` and `gh pr create`
  - `block-main-write.sh` - blocks any git write operation against a checkout sitting on `main`
  - `block-amend.sh` - blocks `git commit --amend` (a failed pre-commit hook means the commit did NOT happen, so an amend would silently rewrite the previous one)
  - `warn-cd-git.sh` - warns, does not block, when someone uses `cd X && git ...`
  - `session-start.sh` - prints a one-line project status when a session starts, so I don't have to ask "where are we"
- The key design decision is what to BLOCK and what to WARN about: block anything irreversible or with effects outside my machine; warn about style. And every block has an escape hatch (an environment variable prefix) so I can authorize it explicitly when I really mean it
- There is a second-order lesson here, and this one hurt: **one of the guards was inert for 11 days and nobody noticed**. `git -C <path> commit` skipped the check entirely - and my own CLAUDE.md convention was to always use `git -C`. My style rule had silently disabled my safety rule. Since then, every hook has its own self-test

- **Critical Driver:** agents occasionally broke my absolute rules, and the rules they broke were precisely the ones I could not afford to have broken
- **AI Benefits:** the critical rules stop depending on the agent's good will and start being enforced by the machine; and the permission prompts I still get are only the ones that actually deserve my attention
- **One line summary:** turn your critical rules from recommendations into constraints - and test the constraints

## Stage 11 - Memory as an institution (May 2026)

- Handovers (Stage 6) solved the "the context is full" problem, but only for the next session. A lesson learned three weeks ago was gone
- So I started saving memory entries systematically: **one fact per file**, with a description, a type, and an index file that lists them all in one line each
- Four types, and keeping them separate is what makes the whole thing usable:
  - **feedback** - a working rule, plus the incident that paid for it. "Never revert a mutation-test edit with `git checkout <file>` - it discards your own uncommitted work too"
  - **project** - state, decisions, standing directives
  - **technique** - a reusable diagnostic method, so the next investigation doesn't reinvent it
  - **reference** - an external fact, verified, with its source
- The entries link to each other, so reading one leads to the related ones
- The most valuable of the four by far is **feedback**. I have around 100 of them in a single project. Each one names the failure that produced it, which is what makes an agent (and me) actually obey it - a rule with a scar attached is followed; an abstract best practice is not
- An important rule: **a memory says what was true when it was written**. Memories that turn out to be wrong get corrected or deleted, not kept "just in case". A wrong memory is worse than no memory, because it is confidently applied
- What this really is: it is not "the AI remembering things". It is the **project** accumulating institutional knowledge that survives the session, the model version, and eventually me

- **Critical Driver:** I was re-learning the same lessons and re-explaining the same constraints every few weeks, and so was the AI
- **AI Benefits:** every session starts with everything the project has ever learned, not with what fits in one context window
- **One line summary:** your project accumulates knowledge, not just code

## Stage 12 - Autonomous overnight runs (Jul 2026)

- Even with an agent team, I still had to be there: dispatching, reviewing, merging, deciding. My presence had become the bottleneck
- So I started writing an explicit **directive** before leaving the session unattended, and letting it run overnight. Not a conversation: a written order
- What a good directive contains:
  1. Numbered rules, unambiguous
  2. An agreed execution order for the work
  3. What to decide alone, without asking me
  4. What to always stop for - the decisions that are mine
  5. What never to do under any circumstance (push to origin, regenerate reference images, anything with effects outside the machine)
- The most useful thing I learned to write is a section naming the **tensions inside my own directive**. In one run, rule 3 said "every new issue found goes into the current milestone" and rule 5 said "keep working until the milestone is empty" - together they are a treadmill that never converges. Writing that down, and saying how to resolve it, is the difference between a directive and a wish
- The output of an autonomous run is not only the work. It is an **audit trail**: what was done, what was decided, on what evidence, and an explicit "blocked on the user" list for the morning
- Results of one such night: 17 issues closed, the main session acting purely as coordinator, all the real work delegated to sub-agents. I reviewed it the next morning in about twenty minutes
- What makes this safe is Stage 10. **Autonomy without executable limits is not delegation, it is gambling** - and this is the point where the guardrails stop being a nicety and become the precondition

- **Critical Driver:** I was the bottleneck; the work could only advance while I was watching it
- **AI Benefits:** the project advances while I sleep, within limits I set in writing, and leaves me an auditable record instead of a surprise
- **One line summary:** delegate a night's work with a written directive, not with a conversation

## Stage 13 - Consolidating knowledge (Aug 2026)

- After a few months of this, my memory directory had grown to around 400 entries and my skills had quietly drifted away from my own rules
- So I wrote a skill whose job is to review the knowledge itself: harvest what was learned, promote the generalizable half to my global configuration, keep the local half local, and **delete what is stale**
- The first real run found **six live defects in my own skills and agents**. Not tidying - actual bugs that had been causing failures for weeks:
  - Skills that piped a test command into `tail`, which throws away the exit status. A failing build was being reported as a success
  - Skills that restated counts ("33 regression cases") that had gone stale months earlier
  - Three reviewer agents that listed `APPROVE-WITH-NITS` as a valid verdict - **they were themselves the cause** of the non-binary review verdicts I had been complaining about for months. I had been blaming the model for following my own written instructions
- The same run retired an entire `.claude/docs/` directory: 597 lines of AI-facing documentation living in a place that nothing ever loaded. Three of the five files were stale or actively wrong
- The rule that came out of that: **knowledge for the AI goes where it gets loaded; knowledge for humans goes in the documentation. A document in between is dead weight, and it rots**
- And the consolidation itself gets an independent review (Stage 9 applies to this too), plus a ledger recording what was distilled and what was rejected, so the next run doesn't re-litigate the same decisions

- **Critical Driver:** my own tooling had silently drifted away from my own rules, and I was diagnosing the symptoms instead of the cause
- **AI Benefits:** the AI audits the instructions I gave it, and finds the contradictions I can no longer see because I wrote them
- **One line summary:** your skills and memories rot too - schedule their review the same way you schedule code review

## Stage 14 - Porting the method to another project (Aug 2026)

- Everything above was learned on a single project: an emulator, written in C++, with a very specific hardware specification as its reference
- The honest question was: how much of this is the method, and how much is just that particular repository tuned over five months?
- So I applied the whole structure to a completely different project: a remote debugger, written in Z80 assembly, a fork of somebody else's code
- What transferred **unchanged**: the hooks, the agent roles (manager who writes no code, independent reviewer, read-only specification oracle), the branch-and-worktree isolation, the merge protocol, the binary review verdict, the memory scheme, the workflow rules
- What had to be rewritten: only the domain-specific parts - which oracle is authoritative, how the tests run, how the build works
- Roughly 90% of the value transferred, and the transfer took about a day
- I also applied a deliberately lighter version to a third project: just a CLAUDE.md, two skills and the daily prompt files, nothing else. **The method scales down**; you don't need the whole apparatus on day one, and installing it before you need it is its own mistake
- This was the point where I understood what I had actually built. It is not an emulator with good tooling. It is a way of working that happens to have been born in an emulator

- **Critical Driver:** I needed to know whether I had learned something reusable, or merely tuned one repository very well
- **AI Benefits:** a new project starts at the maturity level of the last one instead of starting from zero
- **One line summary:** the method is the asset, not the repository it was born in
