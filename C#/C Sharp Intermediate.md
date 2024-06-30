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

> No needs for creating new array for parameters. Just define "params" in front of the params signature.

```c#
public class Calculator
{
	public int Add(params int[] numbers){}
}

var result = calculators.Add(new int[]{1, 2, 3, 4});
var result = calculators.Add(1, 2, 3, 4);
```

### Ref Modifier (Code Smell)

> Turn a value type variance into reference type, and so it can be changed as parameter.

```c#
public class Weirdo
{
	public void DoAWeirdThing(ref int a)
	{
		a += 2;
	}
}

var a = 1;
weirdo.DoAWeirdThing(ref a); // a = 3
```

### Out Modifier (Code Smell)

```c#
public class MyClass
{
	public void MyMethod(out int result)
	{
		result = 1;
	}
}

int a;
myClass.MyMethod(out a);
```

### Dictionary

```c#
public class HttpCookie
{
	private readonly Dictionary<string, string> _dictionary;
	public DateTime Expiry { get; set; }

	public HttpCookie()
	{
		_dictionary = new Dictionary<string, string>();
	}
	
	public string this[string key]
	{
		get { return _dictionary[key]; }
		set { _dictionary[key] = value; }
	} 
}
```

