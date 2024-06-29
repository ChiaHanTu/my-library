### DLL Dynamic Linked Library

> A DLL is a file that includes code that can be re-used across different programs.  

### Assembly

> An assembly is a file (DLL or EXE) that contains one or more namespaces and classes.  


### IL Intermediate Language

> between C# code and machine code.  

### CLR Common Language Runtime

> compile IL code into native machine code. The process of compilation of IL code to machine code is called JIT(Just In Time Compilation).


### Overflowing 

> Value is out of bound of the type.

```C#
checked
{
	byte number = 255;
	number = number + 1;
}
```

This situation would throw an exception to prevent overflow.

### Casting

> It means explicit type conversion

```C#
int i = 1;
byte b = (byte)i;
```

### Struct

> w


### Verbatim string

> 1

```c#
string path = @"c:\projects\folder";
```

