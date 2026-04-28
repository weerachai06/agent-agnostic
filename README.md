# agent-agnostic

A model-agnostic instruction set for [opencode](https://opencode.ai) sessions.  
The rules defined here apply to every AI agent regardless of the underlying model.

## Setup: apply as global instructions in opencode

opencode reads agent rules from `AGENTS.md`. To apply these rules globally across
**all** your projects, copy (or symlink) `AGENTS.md` to opencode's global config directory:

```bash
# Create the config directory if it doesn't exist
mkdir -p ~/.config/opencode

# Option A – copy the file
cp AGENTS.md ~/.config/opencode/AGENTS.md

# Option B – symlink so updates are picked up automatically
ln -sf "$(pwd)/AGENTS.md" ~/.config/opencode/AGENTS.md
```

After this, every opencode session will load the rules automatically.

### Project-level override

To apply the rules to a single project only, copy `AGENTS.md` to that project's root:

```bash
cp AGENTS.md /path/to/your/project/AGENTS.md
```

## Rules

See [`AGENTS.md`](./AGENTS.md) for the full instruction set.

## Language-specific prompts

### TypeScript

[`typescript/AGENTS.md`](./typescript/AGENTS.md) extends the base rules with TypeScript-specific
conventions, tooling, and workflow guidance.

Apply it to a TypeScript project:

```bash
# Copy to your project root
cp typescript/AGENTS.md /path/to/your/ts-project/AGENTS.md

# Or symlink so updates are picked up automatically
ln -sf "$(pwd)/typescript/AGENTS.md" /path/to/your/ts-project/AGENTS.md
```

The file covers:
- Strict-mode TypeScript conventions (`strict`, no `any`, explicit return types)
- Tooling baseline (`tsc --noEmit`, ESLint, Prettier, Vitest/Jest)
- Coding conventions (imports, enums, error handling, async, generics, file naming)
- Testing conventions and project structure reference
- Definition of Done and output format
