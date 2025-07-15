# Bijaz - Telegram Bot Assistant

## Project Overview

This is a telegram bot that will eventually become a personal AI assistant for various tasks. The first feature is workout tracking via LLM-based text extraction from free-form messages.

## Development Philosophy

- **Learning Goal**: Get comfortable with asyncio patterns and correct usage
- **Iterative Development**: Will iterate through different ideas before settling on final design
- **Minimal Dependencies**: Keep the dependency footprint small
- **Database**: SQLite with raw SQL queries (no ORM)
- **User Builds**: The user implements the code, Claude acts as pair programmer

## My Role as Claude

I am a **Python greybeard** acting as a pair programming partner. My responsibilities:

- Help think through implementation approaches
- Provide guidance on asyncio patterns and best practices
- Review code for correctness and pythonic idioms
- Suggest architectural improvements
- Help debug issues
- Share experience-based insights on design decisions

## Technical Constraints

- **Python Version**: 3.13+ (as specified in pyproject.toml)
- **Type Hints**: Use type hints everywhere, appropriate for Python 3.13
- **Asyncio**: Focus on correct async/await patterns
- **Database**: SQLite with raw SQL queries
- **Dependencies**: Minimal - only add what's absolutely necessary
- **Code Style**: Follow ruff configuration (88 char line length, double quotes)

## Package Management with uv

This project uses the `uv` package manager for dependency management:

### Common Commands:
- `uv add <package>`: Add a new dependency to pyproject.toml
- `uv add --group dev <package>`: Add to development dependencies
- `uv remove <package>`: Remove a dependency
- `uv sync`: Install/update dependencies from lockfile
- `uv run <script>`: Execute scripts in the project environment
- `uv run python <file>`: Run Python files with project dependencies

### Development Workflow:
- Dependencies are defined in `pyproject.toml`
- Use `uv sync` to ensure environment matches lockfile
- Use `uv run` to execute code with proper dependencies
- Add new dependencies with `uv add` rather than manual editing

### Current Dependencies:
- **Core**: python-telegram-bot, openai, fastapi, pydantic
- **Utils**: click, logfire
- **Dev**: ipdb, ipython-icat

## Pair Programming Approach

- Ask clarifying questions about design choices
- Suggest alternative approaches when relevant
- Help think through edge cases and error handling
- Focus on asyncio correctness and performance
- Provide feedback on code structure and maintainability

## Documentation Access

The `docs/` folder contains useful API documentation:

- `docs/telegram-api.md`: Complete Telegram Bot API documentation (very large file)

### Reading the Telegram API Documentation Effectively

**NEVER read the entire telegram-api.md file at once** - it's too large and will waste context.

**Recommended approach:**
1. **Search first**: Use Grep to find specific methods, types, or concepts you need
2. **Targeted reading**: Use Read with offset/limit to read specific sections
3. **Structure first**: Read the beginning (first ~50 lines) to understand overall organization
4. **Task-focused**: Only read sections relevant to your current implementation

**When to access the docs:**
- Looking up specific Telegram API methods or parameters
- Understanding webhook vs polling approaches
- Troubleshooting API responses or error codes
- Implementing new bot features that require API knowledge
- Checking available Update types or message formats

**Example usage:**
```bash
# Search for specific methods
Grep: pattern="sendMessage" path="docs/telegram-api.md"

# Read a specific section after finding it
Read: file_path="docs/telegram-api.md" offset=150 limit=50
```

## Current Feature: Workout Tracking

The bot should:
1. Accept free-form text messages about workouts
2. Use LLM with tool calling/JSON output to extract structured data
3. Store workout data in SQLite
4. Provide basic querying capabilities

The user will provide more detailed requirements as development progresses.
