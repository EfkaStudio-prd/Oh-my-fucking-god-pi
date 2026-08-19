---
description: Review-only workflow — engineer work reviewed by hostile reviewer
---
Use the subagent tool with the chain parameter to execute this workflow:

1. First, use the "reviewer" agent to hostile-review the changes described in: $@
2. If REPAIR is needed, use the "engineer" agent to fix the findings (use {previous} placeholder)
3. Finally, use the "judge" agent for the final verdict (use {previous} placeholder)

Execute this as a chain, passing output between steps via {previous}.
