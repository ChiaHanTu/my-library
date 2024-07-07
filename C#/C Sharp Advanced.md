
### Generics 

```c#
namespace Generics
{
	public class Utilities
	{
		public int Max(int a, int b)
		{
			return a > b ? a : b;
		}

		public T Max<T> (T a, T b) where T : IComparable
		{
			return a.CompareTo(b) > 0 ? a : b;
		}
	}
}

default(T) // return the default value of generic type. ex. T = int, return 0.
```

```c#
namespace Generics
{
	public class Utilities<T> where T : IComparable, new()
	{
		public T Max (T a, T b) 
		{
			return a.CompareTo(b) > 0 ? a : b;
		}

		public void DoSomething(T value)
		{
			var obj = new T(); // by adding new() at Utilities class reference.
		}
	}
}
```

### Delegate 

> An object that know how to call a method (or a group of methods).
> A reference to a function.

- For designing extensible and flexible applications (eg. frameworks).

```c#
namespace Delegates
{
	class Program
	{
		static void Main(string[] args)
		{
			var p
		}
	}
}
```