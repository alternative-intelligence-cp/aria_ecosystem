# Wildcard Imports

**Category**: Modules → Importing  
**Syntax**: `use <module>::*;`  
**Purpose**: Import all public items from a module

---

## Overview

Wildcard (`*`) imports bring **all public items** from a module into scope.

---

## Basic Wildcard

```aria
use std.math.*;

// All public items available
result1: i32 = sqrt(16);
result2: i32 = abs(-5);
result3: i32 = pow(2, 10);
```

---

## Syntax

```aria
use <module_path>.*;
```

---

## Examples

### Standard Library

```aria
use std.io.*;

// All I/O functions available
file: File = openFile("data.txt")?;
content: string = readFile("data.txt")?;
writeFile("output.txt", content)?;
```

### Your Modules

```aria
use models.*;

user: User = User.new();
post: Post = Post.new();
comment: Comment = Comment.new();
```

---

## When to Use

### ✅ Preludes

```aria
// Common pattern in libraries
use std.prelude.*;  // Standard prelude
use mylib.prelude.*;  // Library prelude
```

### ✅ Test Modules

```aria
#[cfg(test)]
mod tests {
    use super.*;  // Import all from parent for testing
    
    #[test]
    fn test_function() {
        result: i32 = function_to_test();
        assert(result == 42);
    }
}
```

### ✅ Small, Well-Known Modules

```aria
use std.math.*;  // Math module is small and well-known
```

---

## Dangers

### ❌ Name Conflicts

```aria
use module_a.*;  // Has function 'process'
use module_b.*;  // Also has function 'process'

process();  // ❌ Error: Which process?
```

### ❌ Unclear Origin

```aria
use std.io.*;
use std.http.*;
use database.*;

result: Response = get("url");  // ❌ Where is 'get' from?
```

### ❌ Namespace Pollution

```aria
use huge_module.*;  // ❌ Imports 100+ items you don't need
```

---

## Best Practices

### ✅ DO: Use for Preludes

```aria
use std.prelude.*;  // ✅ Designed for wildcard import
```

### ✅ DO: Use in Tests

```aria
#[cfg(test)]
mod tests {
    use super.*;  // ✅ Import parent items for testing
}
```

### ❌ DON'T: Wildcard Import Multiple Modules

```aria
use module_a.*;  // ❌ Potential conflicts
use module_b.*;  // ❌ Potential conflicts
```

### ❌ DON'T: Wildcard Large Modules

```aria
use std.*;  // ❌ Way too much!
use database.*;  // ❌ Unclear what's being used
```

---

## Selective vs Wildcard

```aria
// Selective - explicit and clear
use std.math.{sqrt, abs, pow};  // ✅ Know exactly what's imported

// Wildcard - implicit
use std.math.*;  // ❌ Unclear what's being used
```

---

## Conflict Resolution

```aria
// Conflicting names
use module_a.*;
use module_b.*;

// Resolve with full path
result1: i32 = module_a.process();
result2: i32 = module_b.process();

// Or use selective imports instead
use module_a.process as process_a;
use module_b.process as process_b;
```

---

## Wildcard with Alias

```aria
// Not typically done, but possible
use std.collections.* as coll;  // Usually not needed
```

---

## Common Patterns

### Prelude Pattern

```aria
// In lib.aria
pub mod prelude {
    pub use crate.CommonType;
    pub use crate.common_function;
    pub use crate.COMMON_CONSTANT;
}

// Users do:
use mylib.prelude.*;
```

### Test Pattern

```aria
mod my_module {
    pub fn function() -> i32 { 42 }
    fn helper() -> i32 { 10 }
}

#[cfg(test)]
mod tests {
    use super.*;  // Import all from my_module
    
    #[test]
    fn test_function() {
        assert(function() == 42);
        // helper() not available (private)
    }
}
```

---

## Re-exporting with Wildcard

```aria
// In lib.aria
mod internal {
    pub fn func_a() { }
    pub fn func_b() { }
}

// Re-export everything from internal
pub use internal.*;

// Users can now:
// import mylib;
// mylib.func_a();
// mylib.func_b();
```

---

## Recommendations

### Prefer Selective Imports

```aria
// Better - explicit
use std.io.{readFile, writeFile};  // ✅ Clear

// Avoid - implicit
use std.io.*;  // ❌ Unclear
```

### Exception: Preludes

```aria
use std.prelude.*;  // ✅ Acceptable - designed for this
```

---

## Related

- [selective_imports](selective_imports.md) - Selective importing
- [use](use.md) - Use statement
- [import](import.md) - Importing modules

---

**Remember**: Wildcard imports are **convenient** but **dangerous** - use sparingly!
