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
  
## Stage 6 - Defining skills and using subagents (Mar 2026) (ongoing)

- Define skills files for different types of subagents: the "Task coordinator", the "Kubernetes expert", the "Terraform expert", the "AWS expert", the "Systems Architect", the "Go developer", etc.
- When working on a big functionality, start multiple agents in parallel, with different skills defined previously
- The main agent is the "Task Coordinator"which _writes no code_ but instead takes care of managing the other agents and coordinating them: first assess with the System Architect, then do a plan and handover tasks to different specialists...
- ...
