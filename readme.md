# Classes for Beginners

```csharp
public class Phone {

}
```

Each class can have:
- constructors
- finalizer / destructor
- properties
- fields
- methods

## Constructor/-s

Method that is used to setup newly created object, one that is executed when
user calls `new Phone`.

```csharp
public class Phone {

  // Constructor
  public Phone() {
    // This will be executed on new
  }
}
```

Class can have more than one constructor. This is an example:

```csharp
public class Phone {

  // Constructor 1
  public Phone() {
    // This will be executed on new Phone()
  }

  // Constructor 2
  public Phone(string type) {
    // This will be executed on new Phone("iPhone")
  }
}
```

## Finalizer / Destructor

Destructors are very rarely used. They are used if there is something that needs
to be done when object is to be destructed (opposite from created). There can be only one.

```csharp
public class Phone {

  // Constructor
  public Phone() {
    // This will be executed on new Phone()
  }
  public ~Phone() {
    // This will be executed on destructing
  }
}
```

## Fields

Fields are "variables" attached to classes. They store values or referrences in memory and are written like this:

```csharp
public class Phone {

  // Constructor
  public Phone() {
    // This will be executed on new Phone()
  }

  // Field name
  public string Name;
}
```

If no costructor is specified, a default one is assumed by the code.

## Properties

### Default

Properties are elements on classes that are providing an ability for user to
set and get some value. Property can have only getter or setter or most commonly both of them.µÂ

Most common is to use default getters and setters:

```csharp
public class Phone {

  // Constructor
  public Phone() {
    // This will be executed on new Phone()
  }

  // Property Name
  public string Name { get; set; }
}
```

Default getters and setters are just a short and cleaner way to write full code
which would be this:

```csharp
public class Phone {

  // Constructor
  public Phone() {
    // This will be executed on new Phone()
  }

  // Property Name
  public string Name {
    get {
      return _name;
    }
    set {
      _name = value;
    }
  }

  // Field name
  private string _name;
}
```

This means that by declaring a default property, we technically just define a
"gateway" to a field where we write and retrieve some value or referrence.

### Customized

Sometimes we need to change that default behavior. This is an example:

```csharp
public class Phone {

  // Constructor
  public Phone() {
    // This will be executed on new Phone()
  }

  // Property Name
  public string Name {
    get {
      return FirstName + " " + LastName;
    }
    set {
      // Let's split entry to two strings
      var parts = value.Split(" ");

      // Let's assume that first part is a FirstName and second a LastName
      FirstName = parts[0];
      LastName = parts[1];
    }
  }

  // Field LastName
  public string LastName;

  // Field FirstName
  public string FirstName;
}
```

You can see in this example that property `Name` does not have its field but it
is storing its value to two different fields.

## Methods

Methods are "functions" or parts of code that are executed when
called. This is an example:

```csharp
public class Phone {

  // Method
  public void AddNumbers(int a, int b) {
    return a+b;
  }
}
```

Methods can be "overloaded" which means that there can be multiple
methods with the same name but different arguments. Which one will
be executed will be determined by called arguments.

```csharp
public class Phone {

  // Method 1
  public int AddNumbers(int a, int b) {
    return a + b;
  }

  // Method 2
  public int AddNumbers(string a, string b) {
    // First lets parse strings into integers
    var intA = Int32.Parse(a);
    var intB = Int32.Parse(b);

    return intA + intB;
  }
}
```

If all what some method needs to do something or return some value
is provided through arguments, method can be decorated as static.

This is both examples:

```csharp
public class Phone {

  // Method 1 can be static
  public static int AddNumbers(int a, int b) {
    return a + b;
  }

  // Method 2 cannot be static
  public int AddNumbersWithBase(int a, int b) {
    return a + b + _baseNumber;
  }

  // Field _baseNumber
  private int _baseNumber = 4;
}
```

