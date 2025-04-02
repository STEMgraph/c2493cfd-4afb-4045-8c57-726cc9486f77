<!---
{
  "depends_on": ["https://github.com/STEMgraph/718193ef-11a1-408d-af23-4b10c24d490d", "https://github.com/STEMgraph/99787eda-617a-4a68-b9a4-d60ec5c5c303"],
  "author": "Stephan Bökelmann",
  "first_used": "2025-04-02",
  "keywords": ["Linking", "Fortran", "Assembly", "C"]
}
--->
<blockquote>
  <strong>⚠️ Warning:</strong> This is under construction!
</blockquote>

# Cross-language Linking: Fortran, C, and Assembly

## 1) Introduction
Linking object files from different languages is a great way to understand name mangling, ABI compatibility, and calling conventions. In this exercise, you'll receive three files: one written in Fortran, one in C, and one in Assembly. Your goal is to successfully link them into one executable.

### 1.1) Further Readings and Other Sources
- [Linking and Libraries (by Ulrich Drepper)](https://www.akkadia.org/drepper/dsohowto.pdf)
- [Calling Fortran from C](https://gcc.gnu.org/wiki/GFortranCallingC)
- [System V ABI](https://refspecs.linuxfoundation.org/elf/x86_64-SysV-psABI.pdf)

## 2) Tasks
1. **Explore Each File**: Inspect the provided files `foo.f90`, `bar.c`, and `baz.s`. Understand what each function does.
2. **Compile Separately**: Use `gfortran -c foo.f90`, `gcc -c bar.c`, and `as -o baz.o baz.s`.
3. **Inspect Symbols**: Use `nm` on each object file. Do you see matching symbol names? Are some mangled?
4. **Fix Compatibility**: Adjust symbol names and use `extern "C"` in C or `bind(C)` in Fortran as needed.
5. **Link Together**: Link with `gfortran -o fullprog foo.o bar.o baz.o` and test the output.

## 3) Questions
1. What naming conventions are used in Fortran for symbols?
2. How can you make symbols compatible across languages?
3. What linker errors occurred, and how did you resolve them?
4. What role does the linker play in symbol resolution?
5. How can calling conventions affect multi-language programs?

## 4) Advice
Focus on matching symbol names exactly — sometimes the problem is as simple as a trailing underscore or name mangling. Use `nm` and `objdump` heavily when debugging linker issues. Check calling conventions (especially argument order and register use) if runtime behavior is incorrect.