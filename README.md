# carp-handle

A foundational generational handle library for the [Carp language](https://github.com/carp-lang/Carp).

This module provides a type-safe way to reference resources in a pool or array without using raw pointers.

## Features

- **Generational Safety**: Detect if a handle is stale because the underlying resource was deleted or replaced.
- **Generic Type-Tagging**: Handles are tagged with the type they reference to prevent mixing handles of different pools.
- **Zero Overhead**: Minimal memory footprint (typically two integers).
- **Foundation Grade**: Designed for use in high-performance engines and ECS architectures.

## Design Philosophy

The Handle module solves the "Dangling Pointer" problem in a systems environment:

1. **Uniqueness**: A handle is a combination of an `index` and a `generation`.
2. **Detection**: When a resource is replaced, its generation is incremented. Old handles will fail a generation check.
3. **Ergonomics**: Provides standard comparison and string conversion logic.

## Installation

Add this to your project by loading `handle.carp`.

```clojure
(load "path/to/carp-handle/handle.carp")
(use Handle)
```

## Usage

```clojure
(use Handle)

(deftype Entity [])

(let [h (Handle.init 10un 1un)]
  (do
    (IO.println &(str (Handle.index &h)))      ; 10
    (IO.println &(str (Handle.generation &h))) ; 1
    (IO.println &(str (Handle.not-null? &h)))  ; true
    ))
```

## Running Tests

```bash
carp -x test/handle_test.carp
```

## License

MIT
