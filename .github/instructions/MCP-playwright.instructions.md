# MCP Playwright Instructions

## User Testing Context

When the user asks to perform user testing, this means to access and interact with the application through Playwright's browser automation capabilities.

## Overview

The MCP Playwright server provides automated browser testing capabilities through Playwright. Use this server for end-to-end testing, UI automation, and web scraping tasks.

## Core Capabilities

-   **Browser Automation**: Control Chromium, Firefox, and WebKit browsers programmatically.
-   **Cross-Browser Testing**: Run tests across multiple browser engines for compatibility.
-   **Mobile Testing**: Simulate mobile devices and responsive designs.
-   **Screenshot Capture**: Take screenshots and generate visual comparisons.
-   **Network Interception**: Mock API responses and monitor network traffic.
-   **Test Generation**: Auto-generate test scripts from user interactions.

## Best Practices

### Test Structure

-   Organize tests by feature or page rather than by test type.
-   Use page object models to encapsulate page-specific logic and selectors.
-   Group related tests in describe blocks with meaningful descriptions.
-   Use beforeEach/afterEach hooks for common setup and cleanup operations.

### Selector Strategy

-   Prefer `data-testid` attributes over CSS selectors or text content.
-   Use role-based selectors (`getByRole`) for accessibility-focused testing.
-   Avoid brittle selectors that depend on implementation details like class names.
-   Use `getByLabel`, `getByPlaceholder`, or `getByText` for form elements when appropriate.

### Assertions and Waits

-   Use Playwright's built-in assertions with automatic retries (`expect(locator).toBeVisible()`).
-   Avoid hard waits (`page.waitForTimeout()`); use smart waits instead.
-   Wait for specific conditions (`waitForSelector`, `waitForResponse`) rather than arbitrary delays.
-   Use soft assertions (`expect.soft()`) for non-critical checks that shouldn't stop test execution.

### Test Data Management

-   Use test fixtures for consistent test data setup.
-   Store test data in separate files (JSON, CSV) rather than hardcoding in tests.
-   Clean up test data after test execution to avoid side effects.
-   Use unique identifiers for test data to prevent conflicts in parallel execution.

## Configuration

### Browser Settings

-   Configure headless mode for CI/CD environments and headed mode for debugging.
-   Set appropriate viewport sizes for responsive testing.
-   Enable screenshot capture on test failures for debugging.
-   Configure trace collection for detailed test execution analysis.

### Parallel Execution

-   Enable parallel test execution to reduce total test runtime.
-   Use worker-scoped fixtures for data that can be shared across tests in the same worker.
-   Avoid shared state between tests that could cause race conditions.

## Error Handling

-   Use try-catch blocks for operations that might fail due to timing issues.
-   Implement retry logic for flaky network operations or external dependencies.
-   Provide meaningful error messages that help identify the root cause of failures.
-   Use `page.screenshot()` in catch blocks to capture the state when errors occur.

## Performance Considerations

-   Minimize the number of page navigations in tests.
-   Use `page.goto()` with `waitUntil: 'networkidle'` for pages with dynamic content.
-   Consider using `page.route()` to mock external API calls and reduce test execution time.
-   Avoid unnecessary element interactions that don't contribute to test objectives.

## Debugging

-   Use `page.pause()` to stop execution and inspect the page interactively.
-   Enable trace viewer for detailed step-by-step analysis of test execution.
-   Use `console.log()` strategically to track test progress and variable states.
-   Leverage browser developer tools when running in headed mode.