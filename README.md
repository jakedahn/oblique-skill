# Oblique Skills

A [Claude Code](https://claude.ai/code) plugin inspired by Brian Eno and Peter Schmidt's [Oblique Strategies](https://en.wikipedia.org/wiki/Oblique_Strategies) - a deck of cards offering creative prompts to break through blocks and introduce unexpected directions.

Use `/oblique-skills:oblique` to draw a strategy card and season your coding session with lateral thinking.

## Installation

```
/plugin marketplace add jakedahn/oblique-skill
/plugin install oblique-skills@jakedahn/oblique-skill
```

## Usage

```
/oblique-skills:oblique
```

This presents you with 4 randomly-selected strategies. Pick one, then choose how to apply it:

- **Apply to current task** - Focus the strategy on whatever you're working on right now
- **Use as session mindset** - Let it color your entire session's approach
- **Help me interpret it** - Get an explanation of what it might mean in a coding context

## Example

```
> /oblique-skills:oblique

Which oblique strategy would you like to apply?
  ○ Honor thy error as a hidden intention
  ○ Emphasise the flaws
  ○ Do nothing for as long as possible
  ○ Use an old idea

> Honor thy error as a hidden intention

How would you like to apply it?
  ○ Apply to current task
  ○ Use as session mindset
  ○ Help me interpret it

> Use as session mindset

"Honor thy error as a hidden intention" is now seasoning this session.

That bug you found might actually be a feature in disguise. Instead of
immediately fixing, let's explore what the error is trying to tell us...
```

## The Strategies

All 113 original Oblique Strategies are included:

> Do we need holes? • Emphasise differences • Honor thy error as a hidden intention • Trust in the you of now • Turn it upside down • Use an old idea • What wouldn't you do? • Faced with a choice, do both • Remove specifics and convert to ambiguities • Repetition is a form of change • *...and 103 more*

## How It Works

```
oblique-skill/
├── .claude-plugin/
│   └── plugin.json
├── commands/
│   └── oblique.md          # /oblique command definition
└── skills/
    └── oblique/
        ├── SKILL.md
        └── scripts/
            └── pick-strategies.sh   # Random selection (POSIX-compatible)
```

The bash script uses a simple POSIX pipeline for cross-platform random selection:

```bash
cat <<'EOF' | awk 'BEGIN{srand()} {print rand(), $0}' | sort -n | head -n 4 | cut -d' ' -f2-
```

Works identically on macOS and Linux.

## Credits

[Oblique Strategies](https://en.wikipedia.org/wiki/Oblique_Strategies) was created by Brian Eno and Peter Schmidt in 1975. The original deck consists of cards with cryptic remarks intended to help artists break creative blocks.

This plugin adapts that concept for vibecoding - introducing lateral thinking prompts to help developers approach problems from unexpected angles.

## License

MIT
