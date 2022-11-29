# Language Execution Classification

Every language creator, based on the language's strength and purpose, decides the execution environment for the language. There are couple of factors that affect the classification. Lets get started with the basics.

1. ##### Scripting Language

   ```
   A scripting language usually sits behind some programming language. These do not require explicit compilation step.
   They usually have less access to computer's native abilities, since they run on a subset of the original programming
   language. Example: JavaScript unable to access your file system. Scripting languages are usually slower than
   programming languages.

   Example: Lua, JavaScript, VBScript, Perl

   This line is getting more and more blurry since compilation can be so fast with modern hardware and modern
   compilation techniques. For instance, V8, actually compiles the js code on the fly into machine code. It does not
   matter if the language is scripting, interpreted or compiled, what matters more is how it performs as designed.
   Example: Ruby was originally entirely interpreted, but there are now multiple compilers for it.
   ```
2. ##### Interpreted Language

   ```
   Interpreted code compiles code to machine code at the time of execution.
   Many of an interpreted language’s instructions can be executed directly, without compiling to machine code;
   however, when certain code is required, an interpreter steps in during runtime and translates it on the spot.

   Example: Python
   ```
3. ##### Compiled Language

   ```
   Languages with an explicit compilation step. Such languages convert human-readable code into machine code prior to
   execution. 

   Compiler:
   Program that converts human-readable code into computer-readable instructions
       — a process that only happens once in the lifespan of that code. 
       Initially, it takes a bit longer because the compiler has to rearrange, optimize or “compile” object code first.
       Object code can’t always run on its own; it needs dynamic load libraries and other bits of code
           — code that’s unique to the operating system, which is housed in those libraries.
       Within the compiling process, these libraries are linked to object code in a “linker”

   Linker:
   A part of the compiler that bundles those bits of code together, then it’s good to go.

   Example: C, C++, C#, Erlang, Objective-C, Java, Pascal, Scala, Swift, TypeScript
   ```



