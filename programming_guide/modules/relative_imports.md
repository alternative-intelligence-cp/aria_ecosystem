# Relative Imports

**Category**: Modules → Importing  
**Purpose**: Import from paths relative to current module

---

## Overview

Relative imports use **keywords** to navigate from the current module's location.

---

## Keywords

- `self` - Current module
- `super` - Parent module
- `crate` - Crate root (technically absolute)

---

## `super` - Parent Module

```aria
mod parent {
    pub fn parent_function() { }
    
    mod child {
        use super.parent_function;
        
        pub fn use_parent() {
            parent_function();  // From parent
        }
    }
}
```

---

## Directory Example

```
app/
├── models/
│   └── user.aria
└── services/
    └── user_service.aria
```

```aria
// In services/user_service.aria
use super.models.user.User;  // Go up to 'app', then to 'models'

pub fn create_user() -> User {
    return User.new();
}
```

---

## Multiple `super`

```
app/
├── core/
│   └── types/
│       └── user.aria
└── features/
    └── auth/
        └── login.aria
```

```aria
// In features/auth/login.aria
use super.super.core.types.user.User;  // auth -> features -> app -> core -> types -> user
```

---

## `self` - Current Module

```aria
mod database {
    pub mod connection {
        pub fn connect() { }
    }
    
    pub fn init() {
        use self.connection.connect;
        connect();
    }
}
```

---

## `crate` - Crate Root

```aria
// From anywhere in your crate
use crate.models.User;
use crate.database.connect;
```

While `crate` starts from root, it's useful for navigating to siblings without deep `super` chains.

---

## Common Patterns

### Sibling Modules

```
app/
├── models/
│   └── user.aria
├── services/
│   └── user_service.aria
└── utils/
    └── validators.aria
```

```aria
// In services/user_service.aria

// Relative to sibling
use super.models.user.User;
use super.utils.validators.validate_email;

// Or absolute from crate
use crate.models.user.User;
use crate.utils.validators.validate_email;
```

---

### Parent Items

```aria
mod parent {
    pub const CONFIG: string = "config";
    
    mod child {
        use super.CONFIG;
        
        pub fn use_config() {
            config: string = CONFIG;
        }
    }
}
```

---

## When to Use Relative Imports

### ✅ Accessing Parent Module

```aria
use super.parent_function;  // ✅ Clear relationship
```

### ✅ Nearby Sibling Modules

```aria
// In auth/login.aria
use super.tokens.generate_token;  // auth/tokens/
```

### ❌ Deep Nesting

```aria
use super.super.super.module;  // ❌ Hard to follow

// Better
use crate.module;  // ✅ Clearer
```

---

## Best Practices

### ✅ DO: Use `super` for Parents

```aria
// In child module
use super.parent_constant;  // ✅ Clear parent relationship
```

### ✅ DO: Limit `super` Chains

```aria
use super.sibling;        // ✅ One level
use super.super.module;   // ⚠️ Two levels max

use super.super.super.module;  // ❌ Too many
```

### ✅ DO: Use `crate::` for Distant Modules

```aria
// Instead of many supers
use crate.deeply.nested.module;  // ✅ Clear
```

### ❌ DON'T: Mix Styles Randomly

```aria
// Inconsistent
use super.models.User;          // Relative
use crate.database.connect;     // Absolute

// Pick one approach per file
```

---

## Relative vs Absolute

```aria
// Relative - depends on current location
use super.models.User;

// Absolute - fixed from root
use crate.models.User;
```

**Trade-off**: Relative imports show local relationships but break when moving files. Absolute imports are refactor-safe.

---

## Examples by Structure

### Flat Structure

```
app/
├── auth.aria
├── database.aria
└── models.aria
```

```aria
// In auth.aria
use super.models;      // Sibling module
use super.database;    // Sibling module
```

---

### Nested Structure

```
app/
├── features/
│   ├── auth/
│   │   └── login.aria
│   └── users/
│       └── profile.aria
└── shared/
    └── types.aria
```

```aria
// In features/auth/login.aria

// One super to features/
use super.super.users.profile;

// Or use absolute
use crate.features.users.profile;  // ✅ Clearer
```

---

## Related

- [absolute_imports](absolute_imports.md) - Absolute import paths
- [import](import.md) - Importing modules
- [use](use.md) - Use statement

---

**Remember**: Use `super` for **nearby** modules, `crate` for **distant** ones!
