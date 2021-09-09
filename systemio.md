# File Manipulation / System IO

## File and Stream I/O

File and stream Input/Output refers to using storage mediums that aren't typically utilized for programming. One example is reading or writing to a text document.

### Files and directories

The `System.IO` namespace can be used to interact with files and directories.

Commonly used file and directory classes are:
- File: provides static methods for creating, copying deleting, moving and opening files, and helps create a FileStream object.
- FileInfo - provides instance methods for creating, copying, deleting, moving and opening files, and helps create a FileStream object.
- Directory - provides static methods for creating, moving, and enumerating through directories and subdirectories.
- Path - provides methods and properties for processing directory strings in a cross-platform manner.

Give yourself a much larger margin for error when it comes to exception handling with System.IO

### Streams

The `Stream` class is abstract, and supports the reading and writing of bytes. All classes that represent streams inherit from the stream class. The function of these classes is to provide a common view of data sources and repositories, and to filter out irrelevant information. These sound like DTO's.

Streams have three fundamental operations:
- Reading
- Writing
- Seeking

Depending on the source of the data, a stream may not support all three of those operations.

Commonly used stream classes include:
- `FileStream`: for reading and writing to a file.
- `IsolatedStorageFileStream`: for reading and writing to a file in isolated storage. (?)
- `MemoryStream`: for reading and writing to memory as the backing store.
- `BufferedStream`: for improving performance of read and write operations
- `NetworkStream`: for reading and writing over network sockets. (?)
- `PipeStream`: for reading and writing over anonymous and named pipes. (?)
- `CryptoStream`: for linking data streams to cryptographic transformations. (?)

(?) means I have no idea what the stream type is, but they sound interesting.

### Readers and Writers

`System.IO` provides types for reading encoded characters from streams and writing them to streams, since streams are typically designed to handle bytes.

Commonly used reader and writer classes are:
- `BinaryReader` and `BinaryWriter`: for reading and writing primitive data types as binary values.
- `StreamReader` and `StreamWriter`: for reading and writing characters by using an encoding value to convert the characters to and from bytes.
- `StringReader` and `StringWriter`: for reading and writing characters to and from strings.
- `TextReader` and `TextWriter`: serve as the abstract base classes for other readers and writers that read and write characters and strings, but not binary data.

### Asynchronous I/O operations

Reading or writing lots of data is hard, so do it async. The async methods contain async in their names, provided examples are `CopyToAsync`, `FlushAsync`, `ReadAsync`, and `WriteAsync`.

### Compression

Make things smaller. Decompression restores compressed things to a useable format. This is not dissimilar to stringifying and parsing. `System.IO.Compression` has the related methods to this process.

Commonly used compression/decompression classes are:
- `ZipArchive`: for creating and retrieving entries in the zip archive.
- `ZipArchiveEntry`: for representing a compressed file.
- `ZipFile`: for creating, extracting and opening a compressed package.
- `ZipFileExtensions`: for creating and extracting entires in a compressed package.
- `DeflateStream`: For compressing and decompressing streams using the Deflate algorithm
- `GZipStream`: for compressing and decompressing streams in gzip data format.

### Isolated storage

(I didn't expect this to be here.) Isolated storage is a mechanism that provides isolation and safety by defining stanadrized ways of associating code with saved data. This sounds exactly like a VM, though not necessarily as extreme. Isolated storage is not available for windows 8 apps, which use application data classes in the `Windows.Storage` namespace.

Commonly used isolated storage classes are:
- `IsolatedStorage`: provides the base class for isolated storage implementations.
- `IsolatedStorageFile`: provides an isolated storage area that contains files and directories.
- `IsolatedStorageFilseStream`: Exposes a file within isolated storage.

### I/O operations in Windows Store apps

This section pertains primarily to windows 8 store apps, and with windows 11 coming out in a few months I'm not taking notes.

### I/O and security

Classes in the `System.IO` namespace require you to follow operating system security requirements like ACLs, or access control lists, to to control access to files and directories, in addition to any FileIOPermission requirements.

Security polices prevent Internet and intranet apps from accessing a user's files, devs should instead use isolated storage for .NET apps.

## How to: Write text to a file

Common classes and methods used to write text to a file are:
- `StreamWriter`: contrains methods to write to a file synchronously (`Write` and `WriteLine`) or asynchronously (`WriteAsync` and `WriteLineAsync`).
- `File`: provides static methods to write text to a file, such as `WriteAllLines` and `WriteAllText`, or to append text to a file, such as `AppendAllLines`, `AppendAllText`, and `AppendText`.
- `Path`: is for strings that have a file or directory path information. It contains the `Combine` method and, in .Net Core 2.1 and later, the `Join` and `TryJoin` methodsm which allow concatenation of strings to build a file or directory path.

The rest of the page is all examples of how to do so, which I would rather refer to the documentation than my notes for.

## Read and write to a newly created data file

This page is almost exlusively an example that again, I would rather refer to than my own notes.

[<==Back](README.md)