# 🦀 Supertraits & `Sized` - Quick Reference Cheat Sheet

---

## 📋 **Part 1: Supertraits**

### **What It Is**
A trait that **must** be implemented before another trait can be implemented.

### **Syntax**
```rust
trait SuperTrait { }
trait SubTrait: SuperTrait { }  // SubTrait REQUIRES SuperTrait
//             ^^^^^^^^^^^ This is the supertrait
```

### **Quick Rules**
| Rule | Explanation |
|------|-------------|
| **Dependency** | Can't implement `SubTrait` without implementing `SuperTrait` |
| **Method Access** | `SubTrait` impls can call `SuperTrait` methods |
| **Multiple** | Use `+` for multiple: `trait T: Super1 + Super2` |
| **Compiler Error** | Missing supertrait = compilation failure |

### **Quick Example**
```rust
trait Connect { fn connect(&self); }
trait Query: Connect { fn query(&self); }  // ← Connect required
//          ^^^^^^^^

struct DB;
impl Connect for DB { fn connect(&self) { } }
impl Query for DB { fn query(&self) { } }  // ✅ Works because Connect is impl'd
```

### **When to Use**
- ✅ Building trait hierarchies (Logger → StructuredLogger → DistributedLogger)
- ✅ Enforcing prerequisites (Query requires Connect)
- ✅ Trait composition (Display + Debug)

---

## 📋 **Part 2: The `Sized` Trait**

### **What It Is**
Marker trait = "This type's size is known at compile time"

### **The Big Rule**
```rust
fn foo<T>(x: T)              // Implicit: T: Sized
fn foo<T: Sized>(x: T)       // Explicit (same as above)
fn foo<T: ?Sized>(x: &T)     // Opt-out: T may be unsized
//       ^^^^^^^ "Maybe Sized"
```

### **Sized vs Unsized Types**

| **Sized Types** ✅ | **Unsized Types (DSTs)** ❌ |
|-------------------|---------------------------|
| `i32`, `bool`, `char` | `str` (without `&`) |
| `String`, `Vec<T>` | `[T]` (without `&`) |
| `&str`, `&[T]` (pointers are sized!) | `dyn Trait` |
| Structs, Enums | - |

### **Key Insight**
```rust
// ❌ Can't do this
let s: str = ???;           // str is unsized

// ✅ Must use indirection
let s: &str = "hello";      // Pointer is sized (16 bytes)
let s: Box<str> = Box::from("hello");  // Box is sized (16 bytes)
```

### **Implicit Sized Bounds**
```rust
// These are IDENTICAL:
struct Foo<T> { x: T }
struct Foo<T: Sized> { x: T }  // Compiler adds this automatically
```

### **When Sized Matters**
| Operation | Requires Sized? |
|-----------|----------------|
| Pass by value: `fn(x: T)` | ✅ YES |
| Return by value: `fn() -> T` | ✅ YES |
| Store in struct: `struct S { x: T }` | ✅ YES |
| Store behind pointer: `struct S { x: &T }` | ❌ NO (use `?Sized`) |
| Store in Box: `struct S { x: Box<T> }` | ❌ NO (use `?Sized`) |

---

## 📋 **Part 3: The Three DSTs (Dynamically Sized Types)**

### **1. `str` - String Slice**
```rust
// ❌ Invalid
let s: str = "hello";

// ✅ Valid
let s: &str = "hello";        // Fat pointer: ptr + len (16 bytes)
let s: Box<str> = Box::from("hello");
```

### **2. `[T]` - Array Slice**
```rust
// ❌ Invalid
let a: [i32] = [1, 2, 3];

// ✅ Valid
let a: &[i32] = &[1, 2, 3];   // Fat pointer: ptr + len (16 bytes)
let a: Box<[i32]> = Box::new([1, 2, 3]);
```

### **3. `dyn Trait` - Trait Object**
```rust
use std::fmt::Display;

// ❌ Invalid
let t: dyn Display = 42;

// ✅ Valid
let t: &dyn Display = &42;    // Fat pointer: ptr + vtable (16 bytes)
let t: Box<dyn Display> = Box::new(42);
```

### **Fat Pointer Breakdown**
```
Regular Pointer (&i32):     [   address   ]  = 8 bytes

Fat Pointer (&str):         [   address   |   length   ]  = 16 bytes

Fat Pointer (&dyn Trait):   [   address   |   vtable   ]  = 16 bytes
```

---

## 📋 **Part 4: The `?Sized` Escape Hatch**

### **What It Means**
`?Sized` = "This type **may or may not** be Sized"

### **The Pattern**
```rust
// Default: Only Sized types
fn foo<T>(x: T) { }
// Equivalent to: fn foo<T: Sized>(x: T)

// Opt-out: Allow Sized AND Unsized types
fn foo<T: ?Sized>(x: &T) { }
//       ^^^^^^^^ May be unsized
//                  ^ MUST use reference/pointer
```

### **Quick Rules**
| With `?Sized` | Without `?Sized` |
|---------------|------------------|
| Can accept `&str` | Only `String`, `&str` (pointer is sized) |
| Can accept `&[T]` | Only `Vec<T>`, `&[T]` |
| Can accept `&dyn Trait` | Only concrete types |
| **Must use `&T` or `Box<T>`** | Can use `T` directly |

### **Common Use Cases**
```rust
// Standard library examples:

// Box can hold unsized types
pub struct Box<T: ?Sized> { /* ... */ }

// Cow can work with str (unsized)
pub enum Cow<'a, B: ?Sized + 'a> where B: ToOwned { /* ... */ }

// Generic over both String and &str
fn process<S: AsRef<str>>(s: S) { }  // Accepts both!
```

---

## 🎯 **Quick Decision Tree**

```
Need to pass/return/store by VALUE?
├─ YES → Type MUST be Sized
│        Use: fn foo<T>(x: T)
│
└─ NO (using &T or Box<T>)
    │
    └─ Want maximum flexibility?
        ├─ YES → Use ?Sized
        │        Use: fn foo<T: ?Sized>(x: &T)
        │
        └─ NO → Keep default Sized bound
                 Use: fn foo<T>(x: &T)
```

---

## 🔥 **Common Patterns Cheat Sheet**

### **Pattern 1: Generic Over String Types**
```rust
// ✅ Accepts String, &str, Cow<str>
fn process<S: AsRef<str>>(text: S) {
    let s: &str = text.as_ref();
    // ...
}
```

### **Pattern 2: Wrapper for Unsized Types**
```rust
// ✅ Can wrap both String and str
struct Container<T: ?Sized> {
    data: Box<T>,  // Must use Box/& for ?Sized
}

let c1: Container<String> = Container { data: Box::new(String::from("hi")) };
let c2: Container<str> = Container { data: Box::from("hi") };
```

### **Pattern 3: Supertrait Hierarchy**
```rust
trait Base { }
trait Middle: Base { }           // Requires Base
trait Advanced: Middle { }       // Requires Middle (and Base)

// Must implement in order: Base → Middle → Advanced
```

### **Pattern 4: Trait Object Collections**
```rust
use std::fmt::Display;

let items: Vec<Box<dyn Display>> = vec![
    Box::new(42),
    Box::new("hello"),
    Box::new(3.14),
];
```

---

## ⚡ **Memory Layout Quick Reference**

```rust
use std::mem::size_of;

size_of::<i32>()           // 4 bytes
size_of::<&i32>()          // 8 bytes (thin pointer)
size_of::<&str>()          // 16 bytes (fat pointer: ptr + len)
size_of::<&[i32]>()        // 16 bytes (fat pointer: ptr + len)
size_of::<&dyn Display>()  // 16 bytes (fat pointer: ptr + vtable)
size_of::<Box<str>>()      // 16 bytes (fat pointer)
size_of::<String>()        // 24 bytes (ptr + len + capacity)
```

---

## ❌ **Common Errors & Fixes**

### **Error 1: Missing Supertrait**
```rust
// ❌ Error
trait A { }
trait B: A { }
struct S;
impl B for S { }  // ERROR: A not implemented

// ✅ Fix
impl A for S { }
impl B for S { }
```

### **Error 2: Passing Unsized by Value**
```rust
// ❌ Error
fn foo<T: ?Sized>(x: T) { }  // ERROR: can't pass unsized by value

// ✅ Fix
fn foo<T: ?Sized>(x: &T) { }
```

### **Error 3: Storing Unsized Directly**
```rust
// ❌ Error
struct S<T: ?Sized> {
    data: T,  // ERROR: can't store unsized directly
}

// ✅ Fix
struct S<T: ?Sized> {
    data: Box<T>,  // or &'a T
}
```

### **Error 4: Type Inference Failure with `.into()`**
```rust
// ❌ Error
let s = "hello".into();  // ERROR: can't infer type

// ✅ Fix
let s: String = "hello".into();
// or
let s = String::from("hello");
```

---

## 🎓 **One-Sentence Summary**

**Supertraits** = "Implement me first before implementing the subtrait"  
**`Sized`** = "I know this type's size at compile time"  
**DSTs** = "These 3 types (`str`, `[T]`, `dyn Trait`) need pointers"  
**`?Sized`** = "Opt-out of Sized requirement for maximum flexibility"

---

## 🔖 **Save This For Later**

```rust
// THE GOLDEN RULES

// Rule 1: All generics are Sized by default
fn foo<T>(x: T) { }  // T: Sized (implicit)

// Rule 2: Use ?Sized when working through indirection
fn foo<T: ?Sized>(x: &T) { }  // Max flexibility

// Rule 3: DSTs always need pointers
let s: &str = "hello";    // ✅
let s: str = "hello";     // ❌

// Rule 4: Supertraits are prerequisites
trait Sub: Super { }      // Must impl Super first

// Rule 5: Fat pointers are 16 bytes (64-bit systems)
size_of::<&str>() == 16   // ptr + len
size_of::<&dyn T>() == 16 // ptr + vtable
```

---
