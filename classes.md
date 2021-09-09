# Classes & Memory Management

## Introduction to classes

### Reference Types

A type that is defined as a class is a reference type. At run time when you declare a variable of a referece type, the variable is null until you've created an instance of it.

When an object is created, memory is allocated to the managed heap for that specific instance, and the variable holds only a reference to the location of the instance. Types on the managed heap require overhead when allocated, or reclaimed by the CLR. Garbage collection by the CLR is super cool and very efficient.

### Declaring Classes

You make a class similarly to how you instantiate any other variable, by declaring the type (in this instance class) and then a variable name, that will refer to the type of the class. They are then followed by a code block, where a user will list all the properties and methods included in said class.

### Creating objects

Classes and objects are different. Think of a class as a mold, and an object as a result of using that mold. Objects are made by first declaring the type, by listing the class name, then by declaring the name of your new object. Lastly we say that our object is equal to a new invoking of the class. Alternatively to the last step, we can set our new object equal to an existing object, assuming they're compatible.

### Class inheritance

Classes fully support inheritance, which is a fundamental characteristic of object-oriented programming.

You inherit by extending a class. To do this, you put a colon after the class declaration, followed by the class you want to inherit from.

When a class declares a base class (the one after the colon), it inherits all members of the base class with the exception of constructors.

In C# a class can only inherit from one base class. However, a base class may also inherit from another, seperate base class.

A user can mark a class as abstract, and inherit from that. Abstract classes cannot be instantiated on their own, properties and methods declared in an abstract class must be implemented in extending classes.

## Constructors

### Parameterless cosntructors

When you don't provide a constructor for your class C# will create one by default that instantiates the object and sets variables to the default values. If there are none assigned, the values will be null.

### Constructor syntax

A constructor is a method whose name is the same as that of its type. Its signature includes the method name, and its parameter list.

### Static constructors

Static constructors are the same as other constructors, except they have no parameters, and therefore make a generic object of the type.

## Properties

A property is a member that provides a mechanism to read, write, or computer the value of a field. They can be used as public data members, but are actually special methods called accessors. 

### Properties overview

- Properties enable a class to expose a public way of getting and setting values, while hiding implementation or verification code.
- A get property accessor is used to return the property value, and a set property acessor is used to assign a new value. In C# 9 and later, an init property accessor is used to assign a new value only during object construction. The accessors can have different access levels. For more information look into Restricting Accessor Accessibility.
- The value keyword is used to define the value being assigned by the `set` or `init` accessor.
- Properties can be read-write (having both a `get` and a `set` accessor), read-only (having a `get` but no `set`) or write-only (having `set` but no `get`). Write-only properties are rare, and are most commonly used to restrict access to sensitive data.
- Simple properties that require no custom accessor code can be implemented either as expression body definitions or as auto-implemented properties.

### Properties with backing fields

A basic pattern for implementing a property involves using a private backing field for setting and retrieving the property value. The `get` accessor returns the value of the private field, and the `set` accessor performs some date validation before assigning a value to the private field.

### Expression body definitions

Property accessors are typically single-line statements. This whole block just talks about how you can make methods to a class that access properties.

### Auto-implemented properties

This section is just saying you can use `get` and `set` without any additional logic. This seems more like a starting point than an ending point.

## Fundamentals of garbage collection

In the Common Language Runtime (CLR), the Garbage Collector (GC) is an automatic memory manager, managing the allocation and release of memory for an application. This means devs working with managed code don't have to write code to perform memory management tasks. This can eliminate common problems, such as forgettign to free an object and causing a memory leak or attempting to access an object that's already been freed.

### Benefits

- Frees devs from having to manually release memory.
- Allocates objects on the managed heap efficiently.
- Reclaims objjects that are no longer being used, clears their memory, and keeps the memory available for future allocations. Managed objects automatically get clean content to start with, so their constructors don't have to initialize every data field.
- Provides memory safety by making sure that an object cannot use for itself the memory allocated for another object.

### Fundamentals of memory

Important CLR memory concepts are as follows:
- Each process has its own, seperate virtual address space. All processes on the same computer share the same phsyical memory and the page file, if there is one.
- By default, on 32-bit computers, each process has a 2-gb user-mode virtual address space.
- As an application developer, you work only with virtual address space and never manipulate physical memory directly. The garbage collector allocates and frees virtual memory for you on the managed heap. If you're writing native code, you use Windows functions to work with the virtual address space. These functions allocate and free virtual memoery for you on native heaps.
- Virtual memory can be in three states:
  - Free: The block of memory has no references to it and is available for allocation.
  - Reserved: The block of memoery is available for your use and cannot be used for any other allocation request. However, you cannot store data to this memory block until it is committed.
  - Committed: The block of memoery is assigned to physical storage.
- Virtual address space can get fragmented. This means that there are free blocks, also known as holes, in the address space. When a virtual memory allocation is requested, the virtual memoery manager has to find a single free block that is large enough to satisfy that allocation request. Even if you ahve 2 GB of free space, an allocation that requires 2 GB will be unsuccessful unless all of that free space is in a single address block.
- You can run out of memory if there isn't enough virtual address space to reserve or physical space to commit. The page file is used even if phsyical memory pressure (thsi is, demand for phsyical memory) is low. The first time that physical memory pressure is high, the operating system must make room in phsyical memory to store data, and it backs up some of the data that is in phsyical memory to the page file. That data is not paged until it's needed, so it's possible to encounter paging in situations where the physical memory pressure is low.

### Memory allocation

When you initialize a new process, the runtime throws it on the managed heap. The managed heap keeps a pointer to the address where the next object in the heap will be allocated. Initially, this pointer is for the base address of the managed heap. All reference types are allocated on the managed heap. When an app creates its first reference type, memory is allocated for the type at the base address of the managed heap. The next time the app makes an object, the garbage collector allocates memory for it in the address space immediately following the first object. As long as address space is available, the garbage collector continues to allocate space for new objects.

It's faster to allocate memory from the managed heap than an unmanaged location. The runtime allcoates memory by referencing, so it's almost as fast as allocating memory from the stack. Since new objects are allocated consecutively, and therefore contiguously, an app can access the objects quickly.

### Memory release

The garbage collector's optimizing engine determines the best time to perform collection based on the allocations being made. When it does so, it releases memory for objects that are no longer in use by the application. It does this by examining the apps roots, these include static fields, local variables on a thread's stack, CPU registers, GC handles, and the finalized queue. Each root either refers to an object on the managed heap, or is set to null. If an object is not accessable from the roots, it's collected, and freed. While it does this, the garbage collector compacts all memory that IS in use, so that there is more free memory to be assigned to.

### Conditions for Garbage Collection

Garbage collection occurs when these conditions are met:
- The system has low physical memory. This is detected by either the low memory notification from the OS, or low memory as indicated by the host.
- The memory that's used by allocated objects on the managed heap surpasses an acceptable threshold. This threshold is continuously adjusted as the process runs.
-  The `GC.Collect` method is called. In almost all cases, you don't hae to call this method, because the garbage collector runs continuously. This method is primarily used for unique situations and testing.

### The managed heap

There's a managed heap for each managed process, each thread of the process allocates memory for objects on the same heap.

The garbage collector also reserves the memory for an app with the `VirtualAlloc` function, and reserves one segment of memory at a time for managed apps. The garbage collector also reserves and releases segments back to the operating system when they're cleared with the `VirtualFree` function.

The frequency and duration of garbage collections is the result of the volume of allocations and amount of survivded memory on the managed heap.

The heap CAN BE considered the accumulation of two heaps, the large object heap, and the small object heap. Large objects are 85k bytes and larger, typically arrays. It's rare for an instance object to be extremely large. (?)

### Generations

The GC algorithm is based on several things:
- It's faster to compact the memory for a portion of the managed heap than for the entire managed heap.
- Newer objects have shorter lifetimes and older objects have longer lifetimes.
- Newer objects tend to be related to each other and accessed by the application around the same time.

Garbage collection primarily is called for the reclamation of short-lived objects. To optimize this, the managed heap is divided into three generations, so it can handle long-lived and short-lived objects seperately. Everything starts in one generation, and as it survives garbage collections is promoted to older generations. This allows the garbage collector to promote things out of the initial generation, and free the entire remainder at once, instead of picking and choosing.

The next few sections seem further in depth than I need to go, so I'm skipping to another relevant one.

### What happens during garbage collection

Garbage collection has the following phases:
- A marking phase, that finds and creates a list of all live objects.
- A relocating phase that updates the references to the objects that will be compacted.
- A compacting phase that reclaims the space occupied by the dead objects and compacts the surviving objects. The compacting phase move objects that have survived a garbage collection toward the older end of the segment. Moving between segments in a single generation only occurs in the final generation, because before then objects would be moved to a later generation. The large object heap is generally not compacted, unless hard coded in. The two exceptions are when a hard limit is set, specifying either a memory limit on a container, or by the `GCHeapHardLimit` or `GCHeapHardLimitPercent` runtime configuration options.

The garbage collector uses the following information to determien whether objects are live:
- Stack roots, we talked about this.
- Garbage collection handles. Handles that point to managed objets and that can be allocated by user code or by the CLR.
- Static data. Static objects in application domains that could be referencing other objects. Each application domain keeps track of its static objects.w

Before a garbage collection starts, all managed threads are suspended except for the thread that triggered the garbage collection.

### Unmanaged resources

When you create an object that encapsulates an unmanaged resource, it's a good idea to provide the necessary code to remove it with a `Dispose` method.

[<==Back](README.md)