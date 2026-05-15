---
name: writing-playwright-typescript-tests
description: 'Writes, reviews, and structures Playwright + TypeScript test automation following project standards. Use when creating E2E tests, page objects, fixtures, or applying test patterns (AAA, POM, Builder, Factory) to a TypeScript test suite.'
argument-hint: 'A description of the feature, user journey, or component to test'
user-invocable: true
---

# Writing Playwright TypeScript Tests

Use this skill when creating or reviewing Playwright + TypeScript tests, page objects, or test infrastructure for this project.
It applies the full set of project standards — from locator strategy and assertion style to page object design and TypeScript conventions.

## When to Use

Use this skill when the user asks for things like:

- "write a Playwright test for the login flow"
- "write a Playwright test for the Spec writen in the following Gherkin file"
- "create a page object for the checkout page"
- "review this test for flakiness or anti-patterns"
- "set up fixtures for authenticated tests"
- "how should I structure my E2E test files?"

Typical scenarios:

- writing new E2E test specs for a feature or user journey
- creating or refactoring page objects and component objects
- adding fixtures for shared setup/teardown
- applying Builder or Factory patterns to test data
- auditing existing tests against project anti-patterns

## Outcome Standard

A strong result includes:

- tests that follow the Arrange–Act–Assert (AAA) structure
- locators that use user-facing roles and labels (not brittle CSS/XPath)
- page objects exposing intent-level methods with private locators
- no `waitForTimeout()` — only explicit assertions and Playwright auto-wait
- TypeScript with explicit types, no `any`, and proper module hygiene
- files placed in `tests/` with `<feature>.spec.ts` naming

## Instruction Standards

This skill applies four scoped instruction sets. Load the relevant one(s) before writing or reviewing code.

| Scope | File | Applies To |
|---|---|---|
| E2E test rules | [`resources/e2e-playwright.instructions.md`](./resources/e2e-playwright.instructions.md) | `tests/e2e/**/*.spec.ts` |
| Page Object rules | [`resources/page-objects.instructions.md`](./resources/page-objects.instructions.md) | `src/pages/**/*.ts` |
| General Playwright patterns | [`resources/playwright-typescript.instructions.md`](./resources/playwright-typescript.instructions.md) | `**` |
| TypeScript style | [`resources/typescript-style.instructions.md`](./resources/typescript-style.instructions.md) | `{tests,src}/**/*.ts` |

See [`resources/README.md`](./resources/README.md) for the full instruction architecture guide.

## Workflow

### Phase 0: Clarify the scope

- identify what needs to be created: spec file, page object, fixture, or all three
- confirm the file path, feature name, and user journey to cover
- note which instruction sets apply based on what will be written

### Phase 1: Load the relevant instructions

- read the applicable instruction files from `resources/` before writing any code
- apply all rules from those files — they are not optional guidelines
- check the anti-pattern checklists to avoid known failure modes

### Phase 2: Write the code

- structure specs with `test.describe()` → `test()` → `test.step()`
- use role-based locators (`getByRole`, `getByLabel`, `getByTestId`) as the default
- implement page objects with private locators and intent-level methods
- add fixtures for shared login/setup flows
- apply AAA, POM, Builder, or Factory patterns where the instructions recommend them

### Phase 3: Validate against checklists

Before handing off, verify against the quality checklist in [`resources/playwright-typescript.instructions.md`](./resources/playwright-typescript.instructions.md):

- [ ] All locators are accessible, specific, and strict-mode safe
- [ ] No `waitForTimeout()` calls anywhere
- [ ] Assertions follow async web-first style (`await expect(...)`)
- [ ] Tests are isolated (no shared mutable state)
- [ ] TypeScript types are explicit — no `any`
- [ ] Files are named and located correctly

## Resource Map

- [`resources/e2e-playwright.instructions.md`](./resources/e2e-playwright.instructions.md) — E2E test structure, isolation, locator, flake prevention, and reporting rules
- [`resources/page-objects.instructions.md`](./resources/page-objects.instructions.md) — Page object responsibilities, locator rules, naming, and fixture integration
- [`resources/playwright-typescript.instructions.md`](./resources/playwright-typescript.instructions.md) — Patterns (AAA, POM, Builder, Factory, Fixtures, Steps) with TypeScript examples
- [`resources/typescript-style.instructions.md`](./resources/typescript-style.instructions.md) — Types, errors, imports, async, and test assertion style rules
- [`resources/README.md`](./resources/README.md) — Instruction architecture guide (global vs. scoped, how `applyTo` works, best practices)

## Definition of Done

A task using this skill is complete when:

- all written code passes the quality checklist above without exceptions
- page objects expose intent-level methods and keep locators private
- test files are placed in `tests/` with correct naming
- no anti-patterns from any instruction file are present
- TypeScript compiles cleanly with no `any` types in new code
