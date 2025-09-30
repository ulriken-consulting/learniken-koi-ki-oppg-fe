---
applyTo: "**/*.{ts,tsx,js,jsx,d.ts,mts,cts}"
---

# TypeScript Development Guidelines

This document applies to files with the following extensions:
- `.ts` - TypeScript files
- `.tsx` - TypeScript React components
- `.js` - JavaScript files (when using TypeScript in mixed projects)
- `.jsx` - JavaScript React components (when using TypeScript in mixed projects)
- `.d.ts` - TypeScript declaration files
- `.mts` - TypeScript ES modules
- `.cts` - TypeScript CommonJS modules

## Testing

-   Always use vitest for testing.
-   Keep the unit tests in 'tests' folders.

## Type Safety

-   Always define explicit return types for public functions and methods.
-   Use TypeScript's strictest settings in tsconfig.json whenever possible.
-   Prefer interfaces over type aliases for object shapes that will be implemented or extended.
-   Use union types instead of enums when the values themselves are meaningful.
-   Avoid using `any` type; prefer `unknown` when the type is truly not known.
-   Use type guards and type narrowing instead of type assertions (as).
-   Consider readonly modifiers for arrays and properties that shouldn't change.

## Naming Conventions

-   All names should be easily readable and should favor readability and meaning over brevity.
-   All names should have a clear, obvious meaning.

### Files and Folders

-   Use camelCase for folders and non-component file names.
-   Use PascalCase for component files and interface files.

### Components and Types

-   Use PascalCase for components.
-   Use PascalCase for interfaces and type aliases.

### Variables and Functions

-   Use camelCase for function and variable names.
-   Use an underscore prefix (\_camelCase) in the following cases:
    -   Private properties
    -   Temporary or intermediate variables
    -   Variables shadowing another variable name

### Constants and Enums

-   Use camelCase for constants that are initialized at run-time.
-   Use SCREAMING_SNAKE_CASE for constants that are known prior to execution.
-   Use PascalCase for enum names.
-   Use SCREAMING_SNAKE_CASE for enum values.
-   Use camelCase for meaningful names that describe enum values.

## React Patterns

-   Use functional components with hooks instead of class components.
-   Define prop interfaces with the naming pattern `ComponentNameProps`.
-   Use React.FC or React.FunctionComponent only when necessary.
-   Extract complex logic into custom hooks with the naming pattern `useFeatureName`.
-   Use React.memo for performance optimization only when necessary and after measuring.
-   Keep components focused on one responsibility; extract complex UI into smaller components.

## Code Organization

-   Group related files in feature-based folders.
-   Keep components and their tests close together in the file structure.
-   Organize imports in groups: external libraries, internal modules, relative imports.

## Comments

-   Only add comments when they explain "why" something is done, not "what" is being done.
-   Avoid redundant comments that merely restate the code.
-   Use JSDoc comments for public APIs and interfaces to provide intellisense support.
-   Document complex algorithms, business rules, or non-obvious solutions.
-   Keep comments up to date when changing code.
-   Use TODO comments sparingly and include a description of what needs to be done.

## Delegation and Separation of Concerns

-   Follow the single responsibility principle; each module or class should have only one reason to change.
-   Separate business logic from UI components using custom hooks, services, or context providers.
-   Use composition over inheritance for sharing behavior between components.
-   Create dedicated service classes/modules for external API calls and complex business logic.
-   Implement domain-specific abstractions instead of exposing implementation details.
-   Use dependency injection patterns (via props, context, or service locators) to improve testability.
-   Consider using the mediator pattern for complex inter-component communication.
-   Extract reusable business logic into pure functions with explicit inputs and outputs.

## Styling

-   Do not include styles directly in HTML components; use styled components instead.

## Error Handling

-   Use error boundaries for catching and displaying UI errors.
-   Prefer explicit error types over generic Error objects.
-   Handle async errors with try/catch blocks or Promise.catch().
-   Use optional chaining (?.) and nullish coalescing (??) for safer property access.

## Dependencies

-   Do not include new nuget libraries unless explicitly asked to do so.
