# Timeloop

An implementation of the **Ralph Wiggum coding agent technique** for autonomous AI-driven development.

## What is the Ralph Wiggum Technique?

The Ralph Wiggum technique is an iterative AI development methodology created by [Geoffrey Huntley](https://ghuntley.com/ralph/) in 2025. Named after the relentlessly optimistic character from The Simpsons, it embodies the philosophy of persistent iteration despite setbacks.

At its core, it's elegantly simple: a loop that repeatedly feeds an AI agent a prompt until a completion condition is met. The agent sees its previous work (via git history and modified files), learns from it, and iteratively improves.

### Core Philosophy

- Don't aim for perfect on the first try - let the loop refine the work
- Failures are predictable and informative
- Keep trying until success - the loop handles retry logic automatically
- Success depends on writing good prompts, not just having a good model

## Scripts

### `timeloop`

The main loop script that runs an AI coding agent iteratively until the task is completed.

**Usage:**
```bash
./timeloop "<prompt>" <max_iterations>
```

**Example:**
```bash
./timeloop "Build a REST API with user authentication" 10
```

**How it works:**

1. Takes a prompt and maximum iteration count as arguments
2. Automatically instructs the agent to:
   - Break down large tasks into manageable items in `TODO.md`
   - Work on one phase at a time
   - Write automated tests for every piece of functionality
   - Use timeouts on CLI commands to prevent deadlocks
   - Update `STATUS.md` to `WORKING` or `COMPLETED`
3. After each iteration, checks `STATUS.md` for completion
4. Stops early if `COMPLETED`, otherwise continues until max iterations

### `todo`

A helper script for quickly modifying the `TODO.md` file using natural language.

**Usage:**
```bash
./todo "<request>"
```

**Example:**
```bash
./todo "Add a task to implement error handling"
./todo "Mark the authentication task as complete"
```

Uses markdown checkbox format (`- [ ]` for incomplete, `- [x]` for complete).

## Safety Considerations

- **Always set a reasonable `max_iterations`** to prevent runaway loops
- Run in sandboxed environments when possible
- The agent has full control during execution - review generated code before deploying

## References

- [Original Ralph Wiggum concept by Geoffrey Huntley](https://ghuntley.com/ralph/)
- [VentureBeat: How Ralph Wiggum became the biggest name in AI](https://venturebeat.com/technology/how-ralph-wiggum-went-from-the-simpsons-to-the-biggest-name-in-ai-right-now/)
- [11 Tips For AI Coding With Ralph Wiggum](https://www.aihero.dev/tips-for-ai-coding-with-ralph-wiggum)
