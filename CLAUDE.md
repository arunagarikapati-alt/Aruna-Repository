# Aruna-Repository — AI Agent Guide

## Project Overview

Aruna-Repository is a **Playwright E2E testing project** for browser automation and cross-browser testing. This is a fresh TypeScript-based test suite that currently uses example tests visiting the Playwright documentation site.

### Technology Stack
- **Playwright** (`@playwright/test`) - E2E testing framework
- **TypeScript** - Type-safe test code
- **Node.js** - Runtime environment

## Essential Commands

```bash
# Install dependencies (if needed)
npm install

# Run all tests
npx playwright test

# Run tests in UI mode (interactive)
npx playwright test --ui

# Run tests in debug mode
npx playwright test --debug

# Run tests for a specific browser
npx playwright test --project=chromium

# View HTML test report
npx playwright show-report
```

## Project Structure

```
tests/
  example.spec.ts          # Example tests (visiting playwright.dev)
playwright.config.ts       # Test configuration (browsers: chromium, firefox, webkit)
package.json              # Dependencies: @playwright/test, @types/node
```

## Key Conventions

### Test Files
- Test files use `.spec.ts` extension (in the `tests/` directory)
- Use Playwright's `test()` and `expect()` functions
- Import from `@playwright/test`

### Browser Coverage
Tests run against three browsers by default:
- Chromium (default)
- Firefox
- WebKit (Safari)

Mobile and other browsers are commented out in config but can be enabled.

### Configuration
- `playwright.config.ts` is the single source of truth for test setup
- CI detection via `process.env.CI` — adjust retries/workers automatically
- HTML reporter generates reports in `playwright-report/` (gitignored)
- Traces collected on first retry for debugging

## Suggested Next Steps

1. **Add npm scripts** in `package.json` for common commands (test, test:ui, test:debug)
2. **Configure baseURL** in `playwright.config.ts` if testing a local app
3. **Add .gitignore** entries for test artifacts (reports, traces)
4. **Replace example tests** with actual test cases for your application

## Typical Workflow

1. Write test files in `tests/` with `.spec.ts` extension
2. Use Playwright locators: `page.getByRole()`, `page.getByLabel()`, `page.locator()`
3. Assert with `expect()` — e.g., `expect(page).toHaveTitle()`
4. Run tests: `npx playwright test` or use `--ui` for interactive debugging
5. Check results in generated HTML report

## Links

- [Playwright Documentation](https://playwright.dev)
- [Test Configuration Reference](https://playwright.dev/docs/test-configuration)
- [Best Practices](https://playwright.dev/docs/best-practices)
