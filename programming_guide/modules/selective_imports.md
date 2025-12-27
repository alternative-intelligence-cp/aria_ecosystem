# Selective Imports

**Category**: Modules → Importing  
**Purpose**: Import only specific items you need

---

## Overview

Selective imports bring **specific items** into scope instead of entire modules.

---

## Basic Selective Import

```aria
// Instead of importing entire module
import std.math;
result: i32 = math.sqrt(16);

// Import specific function
use std.math.sqrt;
result: i32 = sqrt(16);
```

---

## Single Item

```aria
use std.io.readFile;

content: string = readFile("data.txt")?;
```

---

## Multiple Items

```aria
use std.io.readFile;
use std.io.writeFile;
use std.io.deleteFile;

content: string = readFile("input.txt")?;
writeFile("output.txt", content)?;
deleteFile("temp.txt")?;
```

---

## Grouped Selection

```aria
use std.io.{readFile, writeFile, deleteFile};

content: string = readFile("input.txt")?;
writeFile("output.txt", content)?;
deleteFile("temp.txt")?;
```

---

## Nested Selection

```aria
use std.collections.{
    HashMap.{new as new_map, Entry},
    HashSet.{new as new_set}
};

map: HashMap<string, i32> = new_map();
set: HashSet<string> = new_set();
```

---

## Common Patterns

### Functions

```aria
use std.math.{sqrt, abs, pow, floor, ceil};

a: i32 = sqrt(16);
b: i32 = abs(-5);
c: i32 = pow(2, 10);
d: i32 = floor(3.7);
e: i32 = ceil(3.2);
```

### Types

```aria
use std.collections.{HashMap, HashSet, Vec};

map: HashMap<string, i32> = HashMap.new();
set: HashSet<string> = HashSet.new();
vec: Vec<i32> = Vec.new();
```

### Mixed

```aria
use std.http.{
    Client,      // Type
    get,         // Function
    post,        // Function
    StatusCode   // Enum
};
```

---

## Benefits

### ✅ Clarity

```aria
use std.io.{readFile, writeFile};

// Clear what functions are from std.io
content: string = readFile("data.txt")?;
writeFile("output.txt", content)?;
```

### ✅ Avoids Namespace Pollution

```aria
// Only import what you need
use std.math.{sqrt, abs};  // ✅

// Not everything
use std.math.*;  // ❌ Imports everything
```

### ✅ Prevents Conflicts

```aria
// Both modules have 'Client'
use http_lib.Client as HttpClient;
use database_lib.Client as DbClient;

http: HttpClient = HttpClient.new();
db: DbClient = DbClient.new();
```

---

## Best Practices

### ✅ DO: Import Specific Items

```aria
use std.collections.{HashMap, HashSet};  // ✅ Explicit
```

### ✅ DO: Group Related Items

```aria
use std.io.{
    File,
    readFile,
    writeFile,
    openFile
};
```

### ✅ DO: Use Aliases When Needed

```aria
use std.collections.HashMap as Map;
use std.collections.HashSet as Set;

map: Map<string, i32> = Map.new();
set: Set<string> = Set.new();
```

### ❌ DON'T: Over-select

```aria
// Too granular
use std.io.File.open.options.read;  // ❌

// Better
use std.io.File;
file: File = File.open("data.txt")?;
```

---

## Selective vs Wildcard

```aria
// Selective - explicit
use std.math.{sqrt, abs, pow};  // ✅ Know what's used

// Wildcard - implicit
use std.math.*;  // ❌ Unclear what's used
```

---

## With Re-exports

```aria
// In lib.aria
mod internal {
    pub fn important_function() { }
    pub fn helper_function() { }
}

// Selectively re-export
pub use internal.important_function;  // ✅ Expose only what's needed
```

---

## Common Selections

### I/O Operations

```aria
use std.io.{
    File,
    readFile,
    writeFile,
    openFile,
    deleteFile
};
```

### Collections

```aria
use std.collections.{
    HashMap,
    HashSet,
    Vec,
    LinkedList
};
```

### HTTP

```aria
use std.http.{
    Client,
    get,
    post,
    StatusCode,
    Headers
};
```

---

## Related

- [use](use.md) - Use statement overview
- [wildcard_imports](wildcard_imports.md) - Wildcard imports
- [use_syntax](use_syntax.md) - Use syntax details

---

**Remember**: Be **selective** - import only what you need!
