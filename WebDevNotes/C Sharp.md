1. **.NET Framework** is the original implementation of .NET. It supports running websites, services, desktop apps, and more on Windows.
2. **.NET** is a cross-platform implementation for running websites, services, and console apps on Windows, Linux, and macOS. [.NET is open source](https://dotnet.microsoft.com/en-us/platform/open-source) on GitHub. .NET was previously called .NET Core.

## Architecture of .NET Framework

The two major components of .NET Framework are the Common Language Runtime and the .NET Framework Class Library.

- The **Common Language Runtime (CLR)** is the execution engine that handles running applications. It provides services like thread management, garbage collection, type-safety, exception handling, and more.
- The **Class Library** provides a set of APIs and types for common functionality. It provides types for strings, dates, numbers, etc. The Class Library includes APIs for reading and writing files, connecting to databases, drawing, and more.

.NET applications are written in the C#, F#, or Visual Basic programming language. Code is compiled into a language-agnostic Common Intermediate Language (CIL). Compiled code is stored in assemblies—files with a .dll or .exe file extension.

When an app runs, the CLR takes the assembly and uses a just-in-time compiler (JIT) to turn it into machine code that can execute on the specific architecture of the computer it is running on.
![[swimlane-architecture-framework.svg]]
## Namespace-
It acts like a container that can hold classes, interfaces, enums, structs, and other namespaces, allowing you to group related code elements together.
```namespace ProjectA {
 public class MyClass {
  // Class implementation for ProjectA } }
```
### **Primitive Value Types:**

| Data Type | Size     | Description                                                                        |
| --------- | -------- | ---------------------------------------------------------------------------------- |
| `byte`    | 1 byte   | Unsigned 8-bit integer (0 to 255)                                                  |
| `sbyte`   | 1 byte   | Signed 8-bit integer (-128 to 127)                                                 |
| `short`   | 2 bytes  | Signed 16-bit integer (-32,768 to 32,767)                                          |
| `ushort`  | 2 bytes  | Unsigned 16-bit integer (0 to 65,535)                                              |
| `int`     | 4 bytes  | Signed 32-bit integer (-2,147,483,648 to 2,147,483,647)                            |
| `uint`    | 4 bytes  | Unsigned 32-bit integer (0 to 4,294,967,295)                                       |
| `long`    | 8 bytes  | Signed 64-bit integer (-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807)    |
| `ulong`   | 8 bytes  | Unsigned 64-bit integer (0 to 18,446,744,073,709,551,615)                          |
| `float`   | 4 bytes  | 32-bit floating-point number                                                       |
| `double`  | 8 bytes  | 64-bit floating-point number                                                       |
| `decimal` | 16 bytes | 128-bit high-precision floating-point number (suitable for financial calculations) |
| `bool`    | 1 byte   | Boolean value (`true` or `false`)                                                  |
| `char`    | 2 bytes  | A single 16-bit Unicode character                                                  |

## Type Casting-
Types-
1. Implicit-
		 Happens automatically when there is no risk of data loss.
		char > int > long > float > double
		```int num = 10;
double doubleNum = num;  // Implicit casting: int to double

2. Explicit-
		Manual-when there is potential for data loss.
		```
```double doubleNum = 9.78;
int intNum = (int)doubleNum;  // Explicit casting: double to int (fractional part will be truncated)
```

	3.Parsing Strings to Other Types:

The `Parse()` method converts strings to numeric types. If the conversion fails (e.g., the string isn't numeric), it throws an exception. (string must be numeric)
`string str = "123"; int num = int.Parse(str);  // Parse string to int`



