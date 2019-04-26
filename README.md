##CLI Parser


### 1. INTRODUCTION
----------------------------

Many embedded system require a command-line interface (CLI). CLI commands are useful for debugging and testing. This library provides a simply yet feature-rich CLI infrastructure.

The goal of CLI parser is to centralize the complexity of CLI features such that developers do not need to spend a lot of time coding in order to get the convenience of a modern, Cisco-like CLI.

### 2. OVERVIEW
CLI parser simplifies command creation by introducing a .cli file syntax. Users create their commands by writing .cli file. A python script (provided by CLI parser) converts these .cli files into a list of C structures forming a parse tree. The parse tree is then used by CLI parser to provide CLI in run-time.

Users are responsible for providing the following:

    .cli files - These files define CLI commands and are compiled by mk_parser.py into a parse tree used by libparser.

    Action functions - They are callback functions when a CLI command is accepted by CLI parser.

    I/O functions - Prototypes of these functions are listed in cparser_io.h. These functions connect CLI parser to the system I/O. For Linux/UNIX, these functions are provided. For other platforms, you will have to provide your own.

CLI parser provides the following features:

    Command completion
    Command recall
    Context sensitive help
    Automatic help generation

The rest of the document are divided into the following sections:

    CLI Files - Describe the syntax of CLI files.
    Action Functions - Describe how to write action functions.
    Building Your Application - Describe how to build an application using CLI parser.
    Porting - Describe how to port CLI parser to non-UNIX platforms.

### 3. INSTALLATION
To install CLI parser, obtain a .tar.gz file for CLI Parser. Unzip/untar it into a directory of UNIX machine. Go to the top-level directory of CLI Parser and issue: make -s unix. This will create a build/unix directory which contains a library in lib/libcparser.a and some test and demo programs in bin/. (The -s flag is only used to suppress the actual issued command.) On FreeBSD, use gmake instead of make. This is needed because I use some gmake specific feature that is not supported by FreeBSD's make.
4. LICENSING
I have no intention of making a dime out of this work. I am more interested in having some tool that I like available to me regardless of whatever job I take in the future. If you like what you see, feel free to use. I delibrately use a modified BSD license because I don't want people to worry about opening their own source and other legal issue. If you make millions using this, more power to you! Regardless, if you have any kind of feedbacks, drop me a note. 
