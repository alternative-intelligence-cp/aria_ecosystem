# Absolute Imports

**Category**: Modules → Importing  
**Purpose**: Import from fixed, unambiguous paths

---

## Overview

Absolute imports specify the **full path** from the crate root or external crate.

---

## From Crate Root

```aria
// Import from your crate's root
use crate.models.User;
use crate.database.connect;
use crate.utils.validators.validate_email;
```

---

## From Standard Library

```aria
use std.io.File;
use std.collections.HashMap;
use std.http.Client;
```

---

## From External Crates

```aria
use serde.Serialize;
use tokio.runtime.Runtime;
use reqwest.Client;
```

---

## Syntax

```aria
// Standard library
use std.<module>.<item>;

// Your crate
use crate.<module>.<item>;

// External crate
use <crate_name>.<module>.<item>;
```

---

## Examples

### Standard Library

```aria
use std.io.readFile;
use std.io.writeFile;
use std.collections.HashMap;
use std.math.sqrt;

content: string = readFile("data.txt")?;
map: HashMap<string, i32> = HashMap.new();
result: i32 = sqrt(16);
```

### Your Application

```
myapp/
├── main.aria
├── models/
│   └── user.aria
├── database/
│   └── connection.aria
└── utils/
    └── validators.aria
```

```aria
// From anywhere in your app
use crate.models.user.User;
use crate.database.connection.connect;
use crate.utils.validators.validate_email;
```

---

## When to Use Absolute Imports

### ✅ Cross-Module Dependencies

```aria
// services/user_service.aria
use crate.models.User;         // From models/
use crate.database.connect;    // From database/
use crate.utils.hash_password; // From utils/
```

### ✅ Avoid Ambiguity

```aria
// Clear and unambiguous
use crate.http.Client;  // Your HTTP client
use std.http.Client;    // Standard library client
```

### ✅ Refactoring Safety

```aria
// Absolute paths don't break when you move files
use crate.models.User;  // Always works from crate root
```

---

## Absolute vs Relative

```aria
// Absolute - from crate root
use crate.models.User;

// Relative - from current location
use super.models.User;   // Depends on where you are
use self.helpers.format; // Current module
```

---

## Common Patterns

### Standard Library Groups

```aria
use std.io.{File, readFile, writeFile};
use std.collections.{HashMap, HashSet, Vec};
use std.http.{Client, get, post};
```

### Application Modules

```aria
use crate.models.{User, Post, Comment};
use crate.database.{connect, query, execute};
use crate.auth.{login, logout, verify_token};
```

---

## Best Practices

### ✅ DO: Use `crate::` for Internal Modules

```aria
use crate.database.models.User;  // ✅ Clear
```

### ✅ DO: Specify Standard Library

```aria
use std.collections.HashMap;  // ✅ Explicit
```

### ✅ DO: Full Path for Clarity

```aria
use crate.services.user.create_user;  // ✅ Know exactly where it's from
```

### ❌ DON'T: Mix Absolute and Relative Unnecessarily

```aria
// Inconsistent
use crate.models.User;      // Absolute
use super.database.connect; // Relative

// Better - pick one style
use crate.models.User;      // ✅ Absolute
use crate.database.connect; // ✅ Absolute
```

---

## External Dependencies

```aria
// From Cargo.toml or package manager
use serde.{Serialize, Deserialize};
use tokio.runtime.Runtime;
use reqwest.get;
```

---

## Nested Absolute Paths

```aria
use crate.app.features.user.management.create_user;

// Better - flatten if possible
use crate.user.create_user;
```

---

## Related

- [import](import.md) - Importing modules
- [relative_imports](relative_imports.md) - Relative import paths
- [use](use.md) - Use statement

---

**Remember**: Absolute imports are **clear** and **refactor-safe**!
