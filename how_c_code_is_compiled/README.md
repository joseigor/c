# c

If you use C as programing language in your work/personal projects for sure you are  in touch any of the compilers that translate your .h/.c files to your target machine code.

Large projects with multiple dependencies and source files generally use a build system like make, meson, cmake and other to help in the compilation of a project. What all these build system have in common is that in the end they still need to use a pre-defined compiler to generated a executable or library.

The goal of this article will not be about build systems, if you like to learn more about then you can look at the following links:

1. 
2.
3.

The goal of this article is to dissect what are the steps embedded during the compilation of a simple source. If you understand the steps of compilation of a simple main.c file, it will help you to understand and configure any build system for a large project.

For this writing the GNU Compiler Collection (GCC) will be used. The GNU Compiler Collection (GCC) is an optimizing compiler produced by the GNU Project supporting various programming languages, hardware architectures and operating systems.

Also the development environment used to run all gcc commands is based in a Linux distribution, you are free to choose your own distribution. I like Ubuntu, it is just a tool.

To compile something, first we need something to compile right, so instead of playing with words lets write the giant main.c: 



So how can we compile the main.c above and generate a executable form it using gcc? Well it is simple as inserting the following command in your terminal and pressing ENTER.

The outcome of this command is a file called a.out which is a executable version of you main.c that you can run typing the following in your terminal:



Easy-peasy right, with one line of command we have compiled the source file and an executable was generated. This simplicity to compile main.c could make us think that a compiler is only one giant program that take a source file as input and spill out a executable file. But it is not completely true, a compiler usually consists of a dozen of smaller programmers working in cooperation invoked by a control program called a "compiler driver".

When comes to GCC, the one line command above is in fact putting together at least 4  programs (cpp, gcc, as and ld) to work in cooperation to compile main.c to the executable a.out.

To proof that behind the scenes is using the 4 programs mention above, for instance, cpp, gcc, as and ld, lets first understand what are the steps involved in the GCC compilation process.


## GCC Compilation Process

As shown in the diagram above the 4 steps of the GCC compilation process are:

1. Pre-processing: The C preprocessor, often known as cpp, is a macro processor that is used automatically by the C compiler to transform your program before compilation. It is called a macro processor because it allows you to define macros, which are brief abbreviations for longer constructs.
2. Compilation:
3. Assemble:
4. Linking:

Now lets compile main.c by explicitly following each one of the steps above.

1. Pre-processing
> cpp hello.c > hello.i
2. Compilation:
> gcc -S hello.i
3. Assembly:
> as -o hello.o hello.s
4. Linker:
> ld -o hello.exe hello.o ...libraries...


You see the detailed compilation process by enabling -v (verbose) option. For example:





> No matter how big the knowledge is, it's useless if not shared.
