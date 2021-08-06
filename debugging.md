## Debugging

### try/catch block for exceptions

One try can have any number of catches. The CLR catches exceptions not handled by catch blocks, and how it handles them can change based on your CLR config.

### Statement Keywords

1. Selection statements: if, else, switch, case
2. Iteration statements: do, for, foreach, while
3. Jump statements: break, continue, default, goto, return, yield
4. Exception Handling Statements: throw, try-catch, try-finally, try-catch-finally
5. Checked and Unchecked: checked, unchecked
6. Fixed Statement: fixed
7. Lock Statement: lock

### try Statements and Exceptions
Try blocks can be followed by catch blocks or finally blocks. Finally executes after trys or catches preceding it, and executes its containing code. You can use a catch block to either compensate for the error, or rethrow the exception Rethrowing the exception is for logging the problem, or throw a new, higher-level exception type. A finally block is a finisher for your try statements, the CLR always tries to run them. It is better to prevent the code from entering a try block than it is to catch errors you're aware of with it.

#### The Catch Clause

A catch clause catches exceptions, these must be a System.Exception or a subclass of them. Catching System.Exception catches all possible errors, which is useful when your program could recover, you want to rethrow the exception, or when your error handler is the last resort before terminating the program. It's better to catch specific exception types. Only one catch block executes for a given exception, if you want to catch a broader exception, it should be after more specific ones, so you can catch something more specifically. An exception can be caught without specifying a variable, if you don't need its properties. You can also omit variable and type, and the catch block will catch all exceptions. You can also add when clauses, to only catch exceptions under more specific circumstances. This can help catch the same exception type multiple times.

#### The finally Block

A finally block with always execute, and is typically used for cleanup code. They will execute after a catch block finishes, after control leaves the try block because of a jump statement, or after the try block ends. The only time you won't reach a finally block is when you get stuck in an infinite loop, or when the process ends abruptly. It's common practice to close things in finally blocks using Dispose.

#### The using statement

Many classes encapsulate unmanaged resources, like file handles, graphics handles, or database connections. These classes implement `System.IDisposable`, this defnites a single parameterless method named `Dispose` to clean up the resources you call it on. The using statement provides syntax for calling `Dispose` on an `IDisposable` object within a finally block.

#### Throwing Exceptions

Exceptions can be thrown either by the runtime or in user code. Using the throw keyword in a catch block logs the error. 

The three most important properties of an exception are these:
- StackTrace, A stringrepresenting all the methods that are called from the origin of the exception to the catch block.
- Message, it's a string.
- InnerException, The inner thing that caused the other thing.

## Therac-25

Therac-25 was the bad kind of neat because people were killed or maimed by software bugs that previously hadn't been a problem because of hardware interlocks int he previous iterations of Therac. These accidents happened primarily due to poor software design, mainly in that it was designed in such a way that it was impossible to test well.

## Ariane 5

Things that worked good somewhere aren't necessarily going to work so good elsewhere. Also if you're going to reuse software between two similar yet different rockets maybe go over it with a fine toothed comb.

[<==Back](README.md)