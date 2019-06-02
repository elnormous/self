# C++ `self` keyword

`self` is proposed keyword used to refer the current object in C++ (the same as *this). `self` makes more sense for the language because of the following reasons

1. You can not assign to `self`. `this` has a special rule that makes it a prvalue, but `self` does not need any exceptions because references are not assignable.
1. `this` is a special pointer that must point to a valid object however other pointers are not required to do so. References must point to a valid object so `self` is more suited for this purpose than `this`.
1. `return self` instead of `return *this` from assignment operators looks cleaner.
1. Using raw pointers in C++ is usually discouraged (references are preferred). `this` could encrouage programmers to use pointers instead of references.
1. It is easier to teach new programmers how to use references instead of pointers.

`this` points to current object while `self` references it. `self` should not break the C code that is being compiled with a C++ compiler (e.g. Visual Studio). Lots of C projects use `self` as name for a variable that points to the current object so `self` should not be a reserved keyword (just like `override` or `final`).

# History of `this`

Bjarne Stroustrup created "C with classes" in 1979. It was a superset of C and had a `this` pointer in it. "C with classes" did not have references. When "C with classes" evolved to C++ in 1983 references were added to the language but it was decided to leave `this` as a pointer for backwards compatibility. Stroustrup himself has said that the only reason why `this` is not a reference is because it was introduced when C++ had no references (http://www.stroustrup.com/bs_faq2.html#this).

# Usage

Add `#include "self"` or `#define self (*this)` to the top of your source files or pass `-include self` to gcc/clang or `/FI self` to Visual C++ compiler.

# Examples

```cpp
class Foo
{
    Foo& operator=(const Foo& other)
    {
        // do the assignment
        return self;
    }
};
```

# Proposal for the C++ standard

TODO
