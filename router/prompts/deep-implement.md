---
description: Deep implementation with review gate — scout → planner → power-worker → reviewer → judge
---
Use the subagent tool with the chain parameter to execute this workflow:

1. First, use the "scout" agent to find all code relevant to: $@
2. Then, use the "planner" agent to create an implementation plan for "$@" (use {previous} placeholder)
3. Then, use the "power-worker" agent to implement the plan from the previous step (use {previous} placeholder)
4. Then, use the "reviewer" agent to hostile-review the implementation (use {previous} placeholder). If the review finds blocking issues, send them back to power-worker for repair (use {previous} placeholder)
5. Finally, use the "judge" agent to give the final PASS/REPAIR/ABORT verdict (use {previous} placeholder)

Execute this as a chain, passing output between steps via {previous}.
