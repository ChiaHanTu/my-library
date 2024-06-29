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

### Structures (struct)

> Primitive types. Used for simple type.

- Values types.
- Allocated on stack.
- Memory allocation done automatically.
- Immediately removed when out of scope.
- Primitive types(bool, int, char, float), Custom Structure.


### Classes 

> non-primitive types. Mostly used.

- Need to allocate memory.
- Memory allocated on heap.
- Garbage collected by CLR.
- String, Array, Custom classes.

### Verbatim text "@"

> 1. won't convert backslash or hexadecimal.
> 2. To use C# keyword as identifier.
> 3. Solving Attribute naming conflict.

```c#
string path = @"c:\projects\folder";
// equals "c:\\projects\\folder";

string s2 = @"He said, ""This is the last \u0063hance\x0021""";
// equals "He said, ""This is the last \u0063hance\x0021"
```

```c#
string[] @for = { "John", "James", "Joan", "Jamie" };
for (int ctr = 0; ctr < @for.Length; ctr++)
{
	Console.WriteLine($"Here is your gift, {@for[ctr]}!");
}
// The example displays the following output:
// Here is your gift, John!
// Here is your gift, James!
// Here is your gift, Joan!
// Here is your gift, Jamie!
```

```c#
[Info("A simple executable.")]
// Generates compiler error CS1614. Ambiguous Info and InfoAttribute.
// Prepend '@' to select 'Info' ([@Info("A simple executable.")]). Specify the full name 'InfoAttribute' to select it.
public class Example
{ 
	[InfoAttribute("The entry point.")]
	public static void Main()
	{
	}
}
```


### Format String

```c#
int i = 1234;
string s = i.ToString(); // "1234"
string t = i.Tostring("C"); // "$1,234.00"
string y = i.Tostring("C0"); // "$1,234"
```

#### Format Specifier
1. C - Currency 123456 (C) -> $123,456
2. D - Decimal 1234 (D6) -> 001234
3. E - Exponential 1052.0329112756 (E) -> 1.052033E + 003
4. F - Fixed Point 1234.567 (F1) -> 1234.5
5. X - Hexadecimal 255 (X) -> FF

### StringBuilder

- Not for search.
- Quickly create string.

### Procedural Programming

> A programming paradigm based on procedure calls. Break down code into a number of 