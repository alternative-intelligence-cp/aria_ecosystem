# Aria Programming Guide

**Status**: Structure Created (Content Pending)  
**Total Topics**: 302 individual guides  
**Last Updated**: December 22, 2025

---

## Overview

This comprehensive programming guide covers every feature of the Aria programming language. Each topic has its own dedicated file for detailed documentation.

**Current Phase**: File structure complete. Content will be added incrementally as topics are needed or during development breaks.

---

## Guide Structure

### 📦 Types (74 files)
Comprehensive coverage of Aria's type system:
- **Primitive Integers**: int1, int2, int4, int8, int16, int32, int64, int128, int256, int512
- **Unsigned Integers**: uint8, uint16, uint32, uint64, uint128, uint256, uint512
- **TBB (Twisted Balanced Binary)**: tbb8, tbb16, tbb32, tbb64, ERR sentinels, sticky errors
- **Floating Point**: flt32, flt64, flt128, flt256, flt512
- **Vectors**: vec2, vec3, vec9
- **Dynamic/Object**: dyn, obj
- **Structured**: struct declarations, fields, generics, pointers
- **Collections**: string, array (declarations and operations)
- **Result/Function**: result type, error handling, function types
- **Balanced Numbers**: trit, tryte, nit, nyte (ternary and nonary systems)
- **Advanced**: tensor, matrix, void (FFI only), pointers
- **Special Values**: NIL, NULL, ERR, comparisons

### 🧠 Memory Model (18 files)
Memory management and safety:
- **Allocation Strategies**: wild, gc, stack, wildx
- **RAII**: defer keyword
- **Safety Operators**: pinning (#), borrowing ($), immutable/mutable borrows
- **Pointer Operations**: @ operator, address-of, pointer syntax
- **Allocator Functions**: aria.alloc, aria.free, aria.gc_alloc, specialized allocators

### 🔄 Control Flow (21 files)
All control structures:
- **Conditionals**: if/else syntax
- **Loops**: while, for, loop (bidirectional), till (positive/negative step)
- **Advanced**: when/then/end, pick (pattern matching), fall (fallthrough)
- **Flow Control**: break, continue, return, pass, fail
- **Special**: $ iteration variable, dollar_variable syntax

### ⚙️ Operators (59 files)
Complete operator reference:
- **Assignment**: =, +=, -=, *=, /=, %=
- **Arithmetic**: +, -, *, /, %, ++, --
- **Comparison**: ==, !=, <, >, <=, >=, <=> (spaceship)
- **Logical**: &&, ||, !
- **Bitwise**: &, |, ^, ~, <<, >>
- **Special**: @ (address), # (pin), $ (iteration/borrow), ?. (safe nav), ?? (null coalesce)
- **Advanced**: ? (unwrap), |> <| (pipeline), .. ... (range), is (ternary), -> (pointer member)
- **Annotations**: : (type), . (member access), & (interpolation)
- **Template**: ` (backtick), string interpolation

### 📋 Functions (24 files)
Function system and advanced features:
- **Declarations**: func keyword, syntax, parameters, return types
- **Anonymous**: lambda syntax, closures, capture semantics
- **Higher-Order**: functions as arguments, immediate execution
- **Result Handling**: pass, fail keywords
- **Async**: async/await functions
- **Generics**: generic functions/structs, monomorphization, type inference, * prefix

### 📚 Modules (18 files)
Module system and FFI:
- **Import/Export**: use (import), mod (define), pub (visibility)
- **Paths**: relative, absolute, wildcard, selective imports
- **Advanced**: module aliases, nested modules
- **Conditional**: cfg, platform-specific compilation
- **FFI**: extern blocks, C interop, C pointers, libc integration

### 💾 I/O System (15 files)
6-stream topology (Hex-Stream):
- **Overview**: Six-stream architecture, separation of concerns
- **Standard Streams**: stdin, stdout, stderr (text)
- **Extended Streams**: stddbg (debug), stddati (data in), stddato (data out)
- **Stream Types**: text I/O, binary I/O, debug I/O
- **Architecture**: data plane vs control plane separation

### 📖 Standard Library (23 files)
Built-in functionality:
- **I/O**: print, readFile, writeFile, readJSON, readCSV, openFile, streams
- **Process Management**: spawn, fork, exec, createPipe, wait
- **HTTP**: httpGet, HTTP client
- **Collections**: filter, transform, reduce, sort, reverse, unique
- **Math**: math operations, Math.round
- **System**: getMemoryUsage, getActiveConnections, diagnostics
- **Logging**: createLogger, structured logging, log levels

### 🚀 Advanced Features (26 files)
Language advanced capabilities:
- **Compile-Time**: const, comptime, compile-time computation
- **Concurrency**: async/await, coroutines, threading, atomics
- **Metaprogramming**: NASM-style macros, context stack
- **Patterns**: pattern matching, destructuring
- **Error Handling**: error propagation, Result<T> patterns
- **Syntax**: whitespace-insensitive, brace-delimited, semicolons, comments
- **Internals**: tokens, lexer, parser, AST
- **Best Practices**: code examples, idioms, common patterns

---

## Quick Reference

### File Organization

```
programming_guide/
├── types/               (74 files)  - Type system
├── memory_model/        (18 files)  - Memory management
├── control_flow/        (21 files)  - Control structures
├── operators/           (59 files)  - All operators
├── functions/           (24 files)  - Function system
├── modules/             (18 files)  - Module system & FFI
├── io_system/           (15 files)  - 6-stream I/O
├── standard_library/    (23 files)  - Built-in functions
├── advanced_features/   (26 files)  - Advanced topics
└── README.md           (this file)  - Master index
```

### Usage

Each `.md` file corresponds to a specific language feature and will contain:
- **Syntax**: Exact syntax with examples
- **Semantics**: What it does and how it works
- **Usage**: Common patterns and best practices
- **Gotchas**: Common mistakes and edge cases
- **Related**: Links to related topics
- **Examples**: Code snippets demonstrating usage

---

## Navigation Tips

1. **By Category**: Browse folders for related topics
2. **By Feature**: Use file names (self-documenting)
3. **Full-Text Search**: All files follow consistent naming
4. **Cross-References**: Files link to related topics

---

## Development Status

- ✅ **Structure**: Complete (302 files created)
- 📝 **Content**: Pending (to be filled incrementally)
- 🔗 **Cross-Links**: Pending (after content)
- 📚 **Examples**: Pending (after content)

**Strategy**: Fill content file-by-file as needed during:
- Development breaks
- Feature implementation
- Testing and validation
- Documentation sessions

---

## Related Documentation

- [Aria Specifications](../../aria/docs/info/aria_specs.txt) - Language specification
- [Ecosystem Overview](../ECOSYSTEM_OVERVIEW.md) - System architecture
- [Type System](../specs/TYPE_SYSTEM.md) - Type theory details
- [FFI Design](../specs/FFI_DESIGN.md) - C interop patterns

---

**Status**: Ready for incremental content population  
**Repository**: https://github.com/alternative-intelligence-cp/aria_ecosystem  
**License**: AGPL-3.0
