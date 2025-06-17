# Vibe Coding Rules

*A surprisingly effective system for working with AI coding agents (and staying sane)*

**TLDR:** 
Develop strict habits while using coding agents. Codify these habits as rules so your agents automatically follow them and don't let you get lazy. End up with your own evolving bible that ensures human/ai best practices. 

## The Core Idea

I know this isn't revolutionary, but it works incredibly well:

- **Auto-attach your default problem-solving meta strategy** (as .md file)  
  Example: *"First confirm you understand this task, and why we are doing it. Then think deeply to plan a good way to approach this problem before attacking it. After doing this check if any other rules apply from /rules."*

- **Include a mapping**: "situation description" → `/rules/rule_path.md`  
  Example: `/useful_rules/complex-problem-solving-meta-strategy.md` → *READ WHEN PROBLEM HAS COMPLEXITY THAT WOULD LIKELY TAKE A SENIOR ENGINEER MORE THAN AN HOUR TO SOLVE*

### Sample Complex Problem Strategy
```
This is a complex problem that may require a complex solution. 

Be critical about whether it is truly the right thing to do. Are we solving the right problem? 

1. Explore alternative goals that would lead to a different problem to solve entirely.
2. Once you have selected the correct problem to solve, explore different solutions to this problem, and think deeply about the tradeoffs (such as which one minimizes complexity whilst maximizing accuracy)
3. Make a plan for the optimal way to approach this solution before attacking it. Visit .md to make sure you are minimizing the tech-debt of your solution.  

Execute.
```

> **Aside:** You may be reading this right now and think that this prompt can be improved, has shitty grammar, isn't optimized, etc. This is true, but in my experience being clear is much more important than premature optimization of prompts. Making a prompt prettier often doesn't offer much juice to be worth it - there's just more to squeeze in other places of your system.

---

## The "Bible" Part: Current Rules That Work

### For AI Agents

1. **I WILL MAKE SURE MY AGENT AFTER WRITING ANY CODE, RUNS THE PIPELINE, AND THE STATE STAYS IN A SYSTEM OF GREEN.** 

2. **I WILL STILL FOLLOW CONTINUOUS IMPROVEMENT OF THE SYSTEM, TESTABLE AND EVOLVEABLE. ANY CHANGE WILL HAVE TEST COVERAGE.**

3. **MY SYSTEM WILL ALWAYS HAVE A SINGLE ATOMIC COMMAND TO PROVE CORRECTNESS OF SYSTEM.** (So that LLM has minimal complexity for agent feedback loop) I SHOULD STRIVE TO ACHIEVE HIGH ACCURACY OF THIS CORRECTNESS, SO THAT I CAN BE RELIANT ON MY TESTS THAT SYSTEM IS PASSING.

4. **MORE IS NOT ALWAYS BETTER, ANY CHANGE SHOULD BE BALANCED WITH THE TECH DEBT OF ADDING MORE COMPLEXITY.**

5. **I WILL ONLY EVOLVE MY SYSTEM, NOT CREATE SIGNIFICANTLY CHANGED COPIES.**

6. **ISOLATE YOUR DAMN CONCERNS AND KEEP YOUR CONCERNS SEPARATED.** AFTER ANY CHANGE MAKE SURE YOU CLEAN UP YOUR ABSTRACTION, SEPARATE CODE INTO FOLDERS, AND HIDE DETAIL BEHIND A CLEAN API SO THAT OUTWARD COMPLEXITY SHOWN IS MINIMIZED. THEN, AFTER DOING THIS ALSO REVIEW THE GENERAL ARCHITECTURE OF THE COLLECTION OF THESE APIS. DOES THE ARCHITECTURE LEVEL MAKE SENSE? ARE THE APIS THE RIGHT BALANCE OF GENERALITY (TO BE USEFUL) BUT SPECIFICITY & MINIMALNESS TO BE CLEAN & MINIMIZE OUTWARDLY SHOWN COMPLEXITY?

7. **I WILL NOT OVERLOAD ONE CHAT HISTORY WITH MORE THAN ONE PROBLEM CONTEXT.** AS SOON AS THIS HAPPENS I WILL WARN THE USER TO COMPRESS MY TRAJECTORY AND START FRESH.

8. **End every prompt with:**  
   *"First confirm you understand this task, why we are doing it, and explore and think deeply to plan a good way to approach this problem before attacking it."*

9. **Please don't create temporary files, even if they are .md explanations of your work. Update permanent documentation instead.**

### For Humans Only
*(Because AI can't automatically follow these... yet!)*

- **I WILL STILL ENSURE MY SYSTEM IS A JOY TO WORK ON**

- **I WILL STILL KEEP COMMITS AND CHAT WINDOWS TO ONE TICKET WORTH EACH.** IF I WANT TO WORK ON MORE THAN ONE COMMIT AT ONCE I WILL:
  - WORK IN PARALLEL ON SEPARATE CLAUDE INSTANCES ON DIFFERENT BRANCHES IF WORKING IN PARALLEL

- **I WILL KEEP MY PROMPTS TO A PROBABILITY OF >50% THAT IT WILL SUCCEED,** SO I CAN BE CONFIDENT AND CHAIN BACKLOG OF PROMPTS IN THE CODE AGENT PIPELINE. IF IT IS LOWER THAN 50% THIS IS A SIGN THE COMPLEXITY IS GETTING TOO LARGE FOR THIS LLM TO HANDLE.

- **ALWAYS REVIEW THE AGENT'S WORK** UNLESS YOU CAN BE ABSOLUTELY CERTAIN THE ABSTRACTION INWARDS ARE WITHIN THE COMPLEXITY RANGE OF WHAT AN LLM CAN EASILY SOLVE.

- **I WILL KEEP MY CONTEXT I INPUT TO THE LLM MINIMIZED TO ONLY WHAT IS ESSENTIAL.** AS MORE AND MORE BECOMES IRRELEVANT, I WILL COMPRESS MY CONTEXT TO RELEVANCY.

- **I WILL CONTINUE TO REMEMBER MY TERMINAL COMMANDS, AND COMPUTER TOOL BASICS.** I can forget the intricacies of my language, that's fine, as long as I spend an equivalent amount of that time learning higher order concepts such as system architecture.

- **Minimize complexity by hiding multiple required steps behind a single atomic action the LLM can run** (e.g. `llm_setup` bash script)

---

## Final Thoughts

This started out as rules I was setting for myself, so I didn't end up with a complete mess of a project state when going a bit crazy with coding agents. A lot of this is just generally good advice for building complex systems.

You'll be amazed how much better results you get if you're somewhat strict in following these rules, and following the meta-process of adding to this rule set every time you frustrate yourself with your agentic-supported failures :(

**Repo link:** https://github.com/manu354/VIBECODE-BIBLE  
*(Though I'd maybe recommend just following the general approach here, and making your own rules - it's probably quite workflow and project dependent)*
