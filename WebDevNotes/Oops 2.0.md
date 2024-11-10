Procedure programming(functions that operate on data sequentially executed) while oops is about creating obj that contain both data & methods.

helps to keep the C# code DRY "Don't Repeat Yourself"

## Class-
class is a blueprint for creating objects.
class isn't collection of obj

## Object-
obj is small entity in program that represent real physical thing.
obj is instance (Eg) of class.
All obj stored inside heap

## Method-
Method is a function but it will only work in class not outside the class and function used outside of the class.

## Class creating syntax-

accessModifier modifier class ClassName
{
Fields
Methods
Constructor
Properties
Event
Destructor
}

If your have two projects then you can access both projects by adding references option in visual studio.

a **reference variable** is a variable that holds reference to an object rather than the object’s actual data and it is stored in heap.
```To create ReferenceVaraible-
classname referencevariable;
Customer c;
```

## Important points to remember -

- Object is a programmatic representation of a person or thing.
    
- All objects are created based on classes; stored in 'heap'.
    
- For each application execution, a new heap will be created (and only one).
    
- All reference variables (local variables of methods) are stored in stack. For each method call, a new stack will be created.
    
- Method is a collection of statements to perform some operation / calculation.
    
- Class supports two access modifiers: 'internal' and 'public'.
    
- Class supports four modifiers: 'static', 'abstract', 'sealed' and 'partial'.
    
- Objects stores actual data (group of fields) & can access methods of class.
    
- A reference variable stores address of an (only one) object.

## Fields-

Variables that are declared in the class; stored in the objects.

Isolated for each object.

  

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_08-43-41-10e8a8962feaba6c71b64c416cd762c4.png)

1. class Car
2. {
3.   string regNo;
4.   string carModel;
5.   int carYear;
6. }


**Syntax of Field**

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_08-43-41-0f7be9a5523043975d08fa9a3169e91a.png)

  

#### Access Modifiers of Fields

Access Modifier (a.k.a. "Access Specifier" or "Visibility Modifier) specifies the accessibility of fields, where the fields can be accessible; they provide security for the fields.

  

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_08-43-41-d2e16ea7eedfd275d2bf30020c43616f.png)

**Static Fields**

Static fields are store outside the object.

Static fields are common to all objects of a class.



**Class Memory in Heap**

bankName: Bank of Dummyland

  

**Objects in Heap**

object 1:

accountNumber: 1001

accountHolderName: Scott

currentBalance: 5000

  

object 2:

accountNumber: 1002

accountHolderName: Bob

currentBalance: 6000

  

1. class BankAccount
2. {
3.   long accountNumber;
4.   string accountHolderName;
5.   double currentBalance;
6.   static string bankName;
7. }


#### Instance Fields (vs) Static Fields

**Storage:**

**Instance Fields:** Stored in Objects

**Static Fields:** Stored in Class's memory.

  

**Related to:**

**Instance Fields:** Represents data related to objects.

**Static Fields:** Represents common data that belongs to all objects.

  

**Declaration:**

**Instance Fields:** Declared without "static" keyword. Syntax: type fieldName;

**Static Fields:** Declared with "static" keyword. Syntax: static type fieldName;

  

**Accessible with:**

**Instance Fields:** Accessible with object (through reference variable).

**Static Fields:** Accessible with class name only (not with object).

  

**When memory gets allocated:**

**Instance Fields:** Allocated separately for each object, because instance fields are stored "inside" the objects.

**Static Fields:** Allocated only once for the entire program; i.e. when the class is used for the first time while executing the program.


#### Constant Fields

Constant Fields are like static fields, that are common to all objects of the class.

We can't change the value of constant field.

Constant Fields are accessible with class name [not with object].

Constant Fields are not stored in the object; will not be stored anywhere.

Constant Fields will be replaced with its value, while compilation; so it will not be stored anywhere in memory.

Constant Fields must be initialized, in line with declaration (with a literal value only).

Constants can also be declared as 'local constants' (in a method).

AccessModifier   const    type   FieldName = value;


#### Readonly Fields

Readonly Fields are like instance fields, that is stored in every object, individually.

We can't change the value of readonly field.

Readonly Fields are accessible with reference variable [with object].

Readonly Fields must be initialized, either "in-line with declaration" [or] "in the constructor".

AccessModifier    readonly    DataType    FieldName = value;

  

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_08-43-41-e383c15e933ccddaf54b3d4b110962a7.png)

  

**Key Points to Remember**

- Fields are variables that are declared in the class; but stored in objects.
    
- Access modifiers of fields: private, protected, private protected, internal, protected internal, public
    
- Modifiers of fields: static, const, readonly
    
- Instance fields are individual for each object; Static fields are common (one-time) for all objects.
    
- Constants must be initialized along with declaration; Readonly fields must be initialized either 'along with declaration' or in 'instance constructor'.


#### Methods

Method is a function (group of statements), to do some process based on fields.

Methods are parts of the class.

Methods can receive one or more input values as "parameters" and return a value as "return".

  

Eg:

1. class Car
2. {
3.   int calculateEmi( int carPrice, int noOfMonths, int interestRate )
4.   {
5.     //do calculation here
6.     return (emi);
7.   }
8. }

  

**Syntax of Method**

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-16-af55b412743555b9aa654d1803c274da.png)

  

#### Access Modifiers of Methods

Access Modifiers (a.k.a. "Access Specifier" or "Visibility Modifier) of methods, are same as access modifiers of fields.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-16-94409b0b6b0d10de0d0d7f4b915bc82a.png)

  

  

  

#### Encapsulation

Encapsulation is a concept of:

- Bundling the data (fields) and operations (methods) that manipulate the data together.
    
- ides internal implementation details of an object and provide a essential members to interacting with them.
    

  

Benefits:

1. Modularity
    
2. Hiding implementation details
    
3. Data Integrity
    

  

Implemented using:

1. Private fields &
    
2. Public properties or public methods
    

  

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-17-cabec444a4ea599674ec5b186cdf4018.png)

  

  

#### Local Variables and Parameters

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-17-b26449bf467f69570fb83d2cd8685f99.png)

**Parameters:**

The variables that are being received from the "method caller" are called as "parameters".

The parameters are stored in the Stack of the method.

For every method call, a new stack will be created.

  

**Local Variables:**

The variables that are declared inside the method are called as "Local variables". Local variables can be used only within the same method.

Local variables are stored in the same stack, just like parameters.

The stack will be deleted at the end of method execution. So all local variables and parameters will be deleted.

  

  

#### "this" keyword

The "this" keyword refers to "current object", which method has invoked the method.

The "this" keyword is available only within the "instance methods".

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-17-5352bf56c32388003df3d99a2a90c9ef.png)

  

  

#### Instance Methods (vs) Static Methods

**Association:**

**Instance Methods:** Associated with Objects

**Static Methods:** Associated with class.

  

**Manipulates:**

**Instance Methods:** Manipulates instance fields.

**Static Methods:** Manipulates static fields.

  

**Declaration:**

**Instance Methods:** Declared without "static" keyword. Syntax: `returnType methodName( ) { }`

**Static Methods:** Declared with "static" keyword. Syntax: `static returnType methodName( ) {  }`

  

**Accessible with:**

**Instance Methods:** Accessible with object (through reference variable).

**Static Methods:** Accessible with class name only (not with object).

  

**Can access (fields)**

**Instance Methods:**  Can access both instance fields and static fields

**Static Methods:** Can't access instance fields; but can access static fields only.

  

**Can access (methods)**

**Instance Methods:** Can access both instance methods and static methods.

**Static Methods:**  Can't access instance methods; but can access static methods only.

  

**"this" keyword:**

**Instance Methods:** Can use "this" keyword, as there must be "current object" to call instance method.

**Static Methods:** Can't use "this" keyword, as there is NO "current object" while calling instance methods.

  

  

#### Reference Variables as Arguments

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-17-338af2410973a44c74a6fc3bbbe1b733.png)

If you pass "reference variable" as argument, the reference (address) of object will be passed to the method.

The parameter's data type will be the class name.

If you make any changes to object in the method, the same will be affected automatically in the caller method, as you are accessing the same object.

  

  

#### Default Arguments

Default value of the parameter of a method.

If you don’t pass value to the parameter, the default value gets assigned to the parameter.

To void bothering to pass value to the parameter; instead, take some default value into the parameter automatically, if the method caller has not supplied value to the parameter.

1. accessModifier   modifier    returnType  MethodName( parameter1 )
2. {
3.                  Method body here
4. }

  

  

#### Named Arguments

Supply value to the parameter, based on parameter name.

Syntax: `parametername: value`

You can change order of parameters, while passing arguments.

Parameter names are expressive (understandable) at method-calling time.

Calling a method: `MethodName(ParameterName : value, ParameterName : value);`

  

  

#### Method Overloading

Writing multiple methods with same name in the same class, with different parameters.

Caller would have several options, while calling a method.

Difference between parameters of all the methods that have same name, is MUST.

1. MethodName( )
2. MethodName( int )
3. MethodName( string )
4. MethodName( int, string )
5. MethodName( string , int)
6. MethodName( string , string, int)
7. etc.

  

  

#### Parameter Modifiers

Specifies how the parameter receives a value.

- Default [No keyword]
    
- ref
    
- out
    
- in
    
- params
    

  

  

#### Parameter Modifiers (default)

The "Argument" will be assigned into the "Parameter" but not reverse.

  

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-17-1a39b98a3a6a0fb6204bff72d9e457eb.png)

  

  

#### Parameter Modifiers (ref)

The "Argument" will be assigned into the "Parameter" and vice versa.

The Argument must be a variable and must be pre-initialized.

  

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-18-ac7b6418594ee8ff35c69018e6bf8ca6.png)

  

  

#### Parameter Modifiers (out)

The "Argument" will not be assigned into the "Parameter" but only reverse.

The Argument must be a variable; The Argument can be un-initialized.

  

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-18-1f9684f50552c4e0394fdbd61ece9913.png)

  

  

#### 'out' variable declaration

You can declare out variable directly while calling the method with 'out' parameter.

New feature in C# 7.0.

  

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-18-7cc88e86bad33568ee3267a8655445fb.png)

  

  

#### Parameter Modifiers (in)

The "Argument" will be assigned into the "Parameter", but the parameter becomes read-only.

We can't modify the value of parameter in the method; if you try to change, compile-time error will be shown.

New feature of C# 7.2.

  

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-18-95e432dc80d2412d20abb47b4c77675a.png)

  

  

#### ref returns

The reference of return variable will be assigned to receiving variable.

New feature in C# 7.3.

  

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-18-1edd5e8b3eb7bcfd5b624ab110a90852.png)

  

  

#### Parameter Modifiers (params)

All the set of arguments will be at-a-time received as an array into the parameter.

The "params" parameter modifier can be used only for the last parameter of the method; and can be used only once for one method.

  

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-18-686ce508337b9ad11b8becaf99fda424.png)

  

  

#### Local Functions

"Local functions" are functions, to do some small process, which is written inside a method.

Local functions are not part of the class; they can't be called directly through reference variable.

Local functions don't support "access modifiers" and "modifiers".

Local functions support parameters, return.

  

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-18-361a7843c5b09747e3f3412fc69e4ed9.png)

  

  

#### Static Local Functions

"Static Local functions" are functions, same as normal "Local Functions".

Only the difference is, static local functions can't access local variables or parameters of containing method.

This is to avoid accidental access of local variables or parameters of containing method, inside the local function.

  

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-18-df4ffe8e2f6fabb5bfb76cdd6cee8b29.png)

  

  

#### Recursion

A method calls itself.

Useful in mathematic computations, such as finding factorial of a number.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2023-03-19_17-48-18-ab0686deaec3fda7f7af331c9fde5a4d.png)

  

  

**Key Points to Remember**

- Method is a part of class, that contains collection of statements to do some process.
    
- Access modifiers of Methods: private, protected, private protected, internal, protected internal, public.
    
- Modifiers of Methods: static, virtual, abstract, override, new, partial, sealed
    
- For each method call, a new stack will be created; all local variables and parameters of the method will be stored in that stack; will be deleted automatically at the end of method execution.
    
- In instance methods, the 'this' keyword refers to 'current object, based on which the method is called'.
    
- Instance methods can access & manipulate instance fields & static fields; Static methods can access only static fields.
    
- But static method can create an object for the class; then access instance fields through that object.
    
- Using named arguments , you can change order of parameters while calling the method.
    
- Method Overloading is 'writing multiple methods with same name in the same class with different set of parameters'.
    
- The 'ref' parameter is used to receive value into the method and also return some value back to the method caller; The 'out' parameter is only used to return value back to the method caller; but not for receiving value into the method.
