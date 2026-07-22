# Repository agent guidance

## Repository role

This is a completed GitHub Skills exercise for workflow artifacts. The Octomatch React/Vite app supplies build, unit-test, coverage, Playwright, and deployment artifacts. The product code lives in `src/`, browser tests in `e2e/`, completed workflows in `.github/workflows/`, and course-controller material in `.github/steps/`.

Preserve completed exercise history. Do not reset numbered workflows or course steps unless the task explicitly replays the exercise.

## Development and verification

```bash
npm ci
npm run lint
npm test
npm run test:coverage
npm run build
npm run test:e2e
```

Playwright requires its browser/runtime dependencies. If they are unavailable, record that limitation and still run lint, unit tests, and build.

## Application rules

- Keep component behavior and tests together; update card/data tests when game rules change.
- Preserve accessible interaction, deterministic matching behavior, and responsive layout.
- Do not commit `node_modules`, local Playwright output, coverage directories, or build artifacts unless a course step explicitly requires a checked-in fixture.

## Workflow artifact rules

- Keep artifact names, producer/consumer jobs, retention, and deployment environment expectations aligned.
- Do not expose secrets through uploaded logs, reports, traces, screenshots, or artifacts.
- Keep production deployment dependent on the intended tested build artifact rather than rebuilding different source.
- Pin or deliberately version third-party actions and retain least-privilege permissions.
- Avoid casual edits to `.github/steps/` and numbered course workflows during app changes.

## External action boundary

Workflow dispatches, environment approvals, artifact publication, and production deployment change GitHub or hosted state. Do not trigger them as routine local verification. Review the target environment and workflow inputs before any authorized run.
