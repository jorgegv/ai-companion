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

## Stage 9 - Writing new skills (Apr 2026) (Ongoing...)

- When you have spent a lot of tiime working on a single repo, it makes sense to create a new skill which is specialized to work on that repo
- All the repo code, prompt history, documentation and Claude memories can be used to create an extremely focused skill that can be invoked by default when working on the repo
- ...
