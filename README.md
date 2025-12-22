# Aria Ecosystem Architecture

**Purpose**: System overview documentation showing how all Aria components connect, their interfaces, dependencies, and data flows.

**Status**: Documentation in progress (started Dec 22, 2025)

---

## Document Index

### Core Architecture
- [ECOSYSTEM_OVERVIEW.md](ECOSYSTEM_OVERVIEW.md) - High-level system diagram and component relationships
- [COMPONENT_TREE.md](COMPONENT_TREE.md) - Hierarchical breakdown of all components
- [INTERFACES.md](INTERFACES.md) - Interface definitions between components
- [DATA_FLOW.md](DATA_FLOW.md) - How data moves through the system

### Component Details
- [ARIA_COMPILER.md](components/ARIA_COMPILER.md) - Aria language compiler architecture
- [ARIA_SHELL.md](components/ARIA_SHELL.md) - AriaSH shell implementation
- [ARIA_BUILD.md](components/ARIA_BUILD.md) - AriaBuild build system
- [ARIAX.md](components/ARIAX.md) - AriaX package/dependency manager
- [NIKOLA.md](components/NIKOLA.md) - Nikola consciousness substrate
- [RUNTIME.md](components/RUNTIME.md) - Aria runtime library

### Technical Specifications
- ✅ [TYPE_SYSTEM.md](specs/TYPE_SYSTEM.md) - Complete type theory (primitives, TBB, Result<T>, Wild, generics, inference, ownership)
- ✅ [IO_TOPOLOGY.md](specs/IO_TOPOLOGY.md) - 6-stream design rationale, FD allocation, platform differences, process spawning
- ✅ [ERROR_HANDLING.md](specs/ERROR_HANDLING.md) - Result<T> monad patterns, TBB overflow (ERR sentinel), compiler enforcement
- ✅ [MEMORY_MODEL.md](specs/MEMORY_MODEL.md) - 5 allocators (Arena/Pool/Slab/Wild/GC), comparison matrix, usage patterns, performance
- ✅ [ASYNC_MODEL.md](specs/ASYNC_MODEL.md) - M:N threading, Future/Promise, work-stealing scheduler, 6-stream integration, error handling
- ✅ [FFI_DESIGN.md](specs/FFI_DESIGN.md) - C interop patterns, type marshalling, memory safety across FFI, Nikola C wrapper design

### Integration Guides
- ✅ [COMPILER_RUNTIME.md](integration/COMPILER_RUNTIME.md) - Linking process, builtin lowering, ABI specs, type mapping, DWARF
- ✅ [SHELL_RUNTIME.md](integration/SHELL_RUNTIME.md) - 6-stream spawning (fork/exec/dup2), pipe topology, drain workers, job control
- ✅ [BUILD_COMPILER.md](integration/BUILD_COMPILER.md) - ABC config, compiler invocation, dependency resolution, incremental builds, parallel execution
- ✅ [LSP_COMPILER.md](integration/LSP_COMPILER.md) - Shared frontend (libaria_frontend.a), symbol tables, incremental parsing, diagnostics
- ✅ [DAP_COMPILER.md](integration/DAP_COMPILER.md) - DWARF debug info generation, source line mapping, type formatters (Result<T>/TBB/streams)
- ✅ [NIKOLA_ARIA.md](integration/NIKOLA_ARIA.md) - Consciousness substrate FFI bindings, C wrapper, 6-stream wave data, use cases

---

## Quick Reference

### Active Components
- **Aria Compiler** (ariac) - v0.1.0-dev - `/home/randy/._____RANDY_____/REPOS/aria`
- **Aria Shell** (aria_shell) - Pre-alpha - `/home/randy/._____RANDY_____/REPOS/aria_shell`
- **Aria Build** (ariab) - Unknown - `/home/randy/._____RANDY_____/REPOS/aria_build` (location TBD)
- **AriaX** (ariax) - Pre-alpha - `/home/randy/._____RANDY_____/REPOS/ariax`
- **Nikola** - v0.0.4 (9D-TWI) - `/home/randy/._____RANDY_____/REPOS/nikola`

### Shared Infrastructure
- **Aria Runtime** - libaria_runtime.a - Part of compiler repo
- **Wild Memory** - Arena/pool/slab allocators - Shared across all components
- **TBB System** - Twisted Balanced Binary arithmetic - Shared type system
- **6-Stream I/O** - stdin/stdout/stderr + stddbg/stddati/stddato - Shared I/O model

---

## Navigation

Start with [ECOSYSTEM_OVERVIEW.md](ECOSYSTEM_OVERVIEW.md) for the big picture, then drill down into specific components or integration guides as needed.
