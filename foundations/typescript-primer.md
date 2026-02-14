# TypeScript Notes: Unions and Literals

## Union Types (`|`)
*   **Definition:** A type formed from two or more other types, representing values that may be *any one* of those types.
*   **Syntax:** `TypeA | TypeB` (e.g., `string | undefined`).
*   **Properties:** You can only access properties that exist on **all** types in the union. To access specific properties, you must narrow the type first.

## Narrowing
*   **Definition:** The process of refining a broader type (like a Union) into a more specific type based on runtime checks.
*   **Assignment Narrowing:** If you assign a specific value to a variable, TypeScript narrows its type.
    *   *Example:* Assigning `"Grace Hopper"` to a `string | number` variable narrows it to `string`.
*   **Conditional Checks:** Using `if (variable === "value")` allows TypeScript to infer the specific type inside the block.
*   **`typeof` Checks:** `if (typeof variable === "string")` works as a type guard.
*   **Truthiness Narrowing:** `if (variable)` excludes `null`, `undefined`, `false`, `0`, and `""` from the possible types.

## Literal Types
*   **Definition:** A type that represents a specific primitive value (e.g., `"Hypatia"` instead of just `string`).
*   **Inference:**
    *   `const` variables are inferred as their **literal type** (because they can't change).
    *   `let` variables are inferred as their **primitive type** (e.g., `string`).
*   **Assignability:** You cannot assign a general `string` to a variable typed as a specific literal (e.g., `let name: "Ada" = "Ada"; name = "Byron"; // Error`).

## Strict Null Checking
*   **The "Billion Dollar Mistake":** Computing history is full of errors caused by unexpected `null` references.
*   **`strictNullChecks`:** A compiler option (recommended). When enabled, variables cannot be `null` or `undefined` unless explicitly included in their type Union (e.g., `string | null`).
*   **Without it:** `string` implicitly includes `null` and `undefined`, which is unsafe.

## Type Aliases
*   **Syntax:** `type MyAlias = ...;` (PascalCase convention).
*   **Use Case:** Assigning a name to complex or repeated Union types.
    *   *Example:* `type RawData = boolean | number | string | null | undefined;`
*   **Runtime:** Executed purely in the type system and erased from the JavaScript output.
