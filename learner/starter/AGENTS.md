# AGENTS.md

## Project overview

This is a deliberately small Python teaching project for a Codex instructions lab. Its business behavior is a tiny shop checkout: `calculate_total(items)` sums each item's price multiplied by its quantity. The primary users are learners and reviewers practicing project inspection, instruction writing, and safe, testable code changes. Keep the sample simple and preserve its stated public contract.

## Technology stack

- Python; standard library only.
- `unittest` for automated tests.
- No web frontend, backend service, database, ORM, or external runtime dependency is present. Do not invent one for a task.

## Repository structure

- `src/checkout.py`: checkout calculation and other small checkout-domain helpers.
- `tests/test_checkout.py`: visible unit tests and behavior contract.
- `sample_orders.json`: synthetic sample data for inspection.
- `README.md`: setup and lab workflow.
- `task_card.md`: scoped exercises and explicit requirements.
- `comparison_worksheet.md`: learner's comparison notes; leave it alone unless asked to complete it.

## Architecture and data flow

This is a standalone module, not a client/server application. Callers pass a sequence of item mappings to functions in `src/checkout.py`; the calculation reads `price` and `quantity` and returns a float. There are no API interactions, persistence, or integrations. Keep calculation logic in the module and presentation/formatting helpers separate from calculation when requested.

## Development setup

No installation or package setup is needed. Run commands from `learner/starter/`:

```sh
python3 -m unittest discover -s tests -v
```

Use `python` instead of `python3` where that is the available interpreter. Do not add a dependency or introduce environment configuration without a task requirement.

## Coding standards

- Follow the surrounding Python style: four-space indentation, `snake_case` functions and variables, and concise docstrings for public helpers.
- Keep changes small and readable; prefer the standard library and existing module structure.
- Preserve existing public behavior unless the task explicitly changes it. In particular, `calculate_total(items)` must continue to work and return a float.
- Avoid unrelated refactors, schema changes, broad exception handling, and speculative abstractions.
- Add or update type annotations only when they fit the affected code and clarify the requested contract; do not reformat unrelated code.

## Frontend guidelines

There is no frontend, routing, UI state, or styling system in this project. Do not add one for checkout tasks.

## Backend guidelines

There is no server or API layer. Keep domain behavior in `src/checkout.py`; validate new function arguments at the function boundary when the requested contract requires it, and raise clear, appropriately specific exceptions. Keep error behavior narrow and predictable.

## Database guidelines

There is no database, ORM, persistence layer, or migration system. Do not add persistence unless explicitly requested.

## Security guidelines

The project has no authentication, authorization, secrets, or network input. Do not introduce credentials or secrets. For new input handling, validate only what the feature contract requires and do not silently accept invalid values.

## Testing and validation

- Add focused `unittest` cases for changed behavior, including boundary and invalid inputs when applicable.
- Run `python3 -m unittest discover -s tests -v` from this directory after code changes (or the equivalent `python` command if needed).
- Do not claim checks passed unless they were run; report any unavailable interpreter or failed check.
- There is no configured linter, type checker, or build pipeline. Do not add one without a task requirement.

## AI agent instructions

1. Read this file, `README.md`, the relevant task card, implementation, and tests before changing code.
2. Treat task-card requirements and the existing public contract as authoritative. If a requested task is ambiguous, make the smallest reasonable change consistent with the stated contract.
3. Implement only the requested behavior and its focused tests. Keep formatting separate from arithmetic when adding presentation helpers.
4. Run the documented test command after implementation and inspect the final diff for accidental or unrelated edits.
5. In the final report, summarize the behavior changed, files touched, validation command and outcome, and any limitation or unrun check.

## Restrictions

- Do not modify files outside `learner/starter/` for a task scoped to this starter project.
- Do not edit `comparison_worksheet.md` or `task_card.md` unless the user explicitly asks; they are lab materials and define the exercise.
- Do not add dependencies, change the item schema, or add a frontend, server, database, or external integration unless explicitly requested.
- Do not overwrite learner work or make broad repository changes as part of a focused checkout task.

## Definition of done

A task is complete when the requested behavior is implemented within scope, the existing public contract is preserved except where explicitly changed, focused tests cover the requested behavior, the documented test suite has been run with its result reported, and the final diff contains no unrelated changes.
