# `import` Statement

**Category**: Modules → Importing  
**Syntax**: `import <module_path>;`  
**Purpose**: Bring external modules into scope

---

## Overview

`import` loads a module and makes it available in the current scope.

---

## Basic Import

```aria
// Import module
import std.io;

// Use module
file: File = std.io.openFile("data.txt")?;
```

---

## Import Types

### Single Module

```aria
import math;

result: i32 = math.add(5, 3);
```

### Nested Module

```aria
import std.collections.HashMap;

map: HashMap<string, i32> = HashMap.new();
```

### Multiple Modules

```aria
import std.io;
import std.http;
import std.json;
```

---

## Import vs Use

```aria
// import - brings module into scope
import std.math;
result: i32 = math.sqrt(16);  // Use module prefix

// use - brings items into scope
use std.math.sqrt;
result: i32 = sqrt(16);  // No prefix needed
```

---

## Absolute Imports

From crate root or external crate:

```aria
import std.io;              // Standard library
import myapp.database;      // Your crate
import external_crate.module;  // External dependency
```

---

## Relative Imports

From current module location:

```aria
// In module 'app.services'
import super.models;       // app.models
import super.super.utils;  // parent.utils
import self.helpers;       // app.services.helpers
```

---

## Import Paths

### Simple Path

```aria
import auth;
import database;
```

### Dotted Path

```aria
import app.database.models;
import std.collections.HashMap;
```

### With Wildcards

```aria
import std.math.*;  // Import all public items

sqrt(16);    // Direct use
abs(-5);     // Direct use
```

---

## Common Patterns

### Standard Library

```aria
import std.io;
import std.http;
import std.json;
import std.collections;
```

### Your Modules

```aria
import models.User;
import database.connect;
import utils.validators;
```

### Third-Party

```aria
import http_client;
import json_parser;
import crypto.sha256;
```

---

## Module Resolution

```
myapp/
├── main.aria
├── models/
│   ├── mod.aria
│   └── user.aria
└── services/
    └── user_service.aria
```

```aria
// In main.aria
import models;           // Loads models/mod.aria
import models.user;      // Loads models/user.aria
import services.user_service;  // Loads services/user_service.aria
```

---

## Best Practices

### ✅ DO: Group Related Imports

```aria
// Standard library
import std.io;
import std.http;

// Third-party
import serde;
import tokio;

// Your modules
import models;
import database;
import utils;
```

### ✅ DO: Use Specific Imports

```aria
import std.collections.HashMap;  // ✅ Specific

// Not
import std.collections;          // Less specific
```

### ❌ DON'T: Wildcard Import Everything

```aria
import std.*;          // ❌ Unclear what's being used
import database.*;     // ❌ Name conflicts possible
```

---

## Import Aliases

```aria
import very.long.module.name as short;

result: i32 = short.function();
```

---

## Conditional Imports

```aria
#[cfg(os = "linux")]
import linux_specific;

#[cfg(os = "windows")]
import windows_specific;
```

---

## Related

- [use](use.md) - Bringing items into scope
- [mod](mod.md) - Module declaration
- [absolute_imports](absolute_imports.md) - Absolute import paths
- [relative_imports](relative_imports.md) - Relative import paths

---

**Remember**: `import` brings **modules**, `use` brings **items**!
