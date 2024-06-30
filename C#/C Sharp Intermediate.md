### Singleton

> Should have only one instance of the concept in the memory.

### Object initializers

> Default constructer will be called, and fields will be initialized.

```c#
var person = new Person()
				{
					FirstName = "Mosh";
					LastName = "Hamedani";
				}
```

### Signature of a method

- Name 
- Number and Type of parameters.

```c#
public class Point
{
	public void Move(int x, int y) {}
}
```

### Params Modifier

```c#
public class Calculator
{
	public int Add(params int[] numbers){}
}

var result = calculators.Add(new int[]{1, 2, 3, 4});
var result = calculators
```