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


## Unified Modeling Language (UML)

>A UML diagram is a way to visualize systems and software using Unified Modeling Language (UML).

![[Pasted image 20240706144250.png]]

## Inheritance vs Composition

-  Inheritance is higher coupling, composition is loosely coupled.

### Access Modifier

- Protected: Accessible only from the class and its derived classes.
- Internal: Accessible only from the same assembly.
- Protected Internal: Accessible only from the same assembly or any derived classes.

### Constructor & Inheritance

```c#
namespace Constructors
{
	public class Car : Vehicle
	{
		public Car(string registration)
			:base(registration)
		{
			Console.WriteLine("Car is being initialized.");
		}
	}

	public class Vehicle(string registration)
	{
		Console.WriteLine("Vehicle is being initialized.);
	}
}
// This way, it can construct Vehicle first with the parameter registration, then construct Car with the parameter registration.
```

### Upcasting & Downcasting

```c#
public class Shape
{

}
public class Circle : Shape
{

}
```

#### Upcasting: Conversion from a derived class to a base class.

```c#
Circle circle = new Circle();
Shape shape = circle;
```

#### Downcasting: Conversion from a base class to a derived class.

```c#
Circle circle = new Circle();
Shape shape = circle;

Circle anotherCircle = (Circle)shape;
```