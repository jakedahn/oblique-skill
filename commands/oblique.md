---
description: Draw an oblique strategy card to season your coding session with lateral thinking
allowed-tools: Bash, AskUserQuestion
---

# Oblique Strategy

Inspired by Brian Eno and Peter Schmidt's Oblique Strategies - creative prompts to break through blocks and introduce unexpected directions.

## Workflow

1. Run the script to get 4 random strategies:

```bash
${CLAUDE_PLUGIN_ROOT}/skills/oblique/scripts/pick-strategies.sh -n 4
```

2. Present the strategies to the user via `AskUserQuestion`:
   - header: "Strategy"
   - question: "Which oblique strategy would you like to apply?"
   - Each strategy as an option with a brief interpretation as description
   - multiSelect: false

3. After selection, ask how to apply via another `AskUserQuestion`:
   - header: "Application"
   - question: "How would you like to apply '[selected strategy]'?"
   - Options:
     - "Apply to current task" - Focus this strategy on whatever I'm working on right now
     - "Use as session mindset" - Let this color the entire session's approach
     - "Help me interpret it" - Explain what this might mean in a coding context

4. Based on choice:
   - **Apply to current task**: Reframe current work through the strategy's lens
   - **Use as session mindset**: Acknowledge and reference naturally throughout
   - **Help me interpret it**: Explain the strategy and offer coding interpretations
