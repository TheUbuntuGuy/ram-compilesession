RAM-compilesession
=====================

## What is it?
RAM-compilesession is a management script for creating, initializing, saving, and destroying a ramdisk for the purpose of using it to compile and link an application that uses cmake.

This script can be used for setting up an environment for compiling any application that uses cmake.

## Why would I use it?

Best to use an example.
In my case, I have all my source code on a file server. This means that linking large C/C++ applications is very time consuming. A single code change may take 1 second to compile but 90 seconds to link. Very ineffective use of my time. This script can get that time down dramatically, in my case down to 1 second. Compiling is also sped up, but not nearly as much.

## How does it work?

Linking is a very I/O intensive operation when lots of files are involved. By placing all the object files in a ramdisk, they can be linked at ridiculous speeds. The source files are not moved from their original location on nonvolatile storage, so they can be confidently saved at any time.

## What do I need?

An application to compile that uses cmake, and Linux. That's it.

## How do I use it?

Configure it first. (See below) It's really easy...

When you want to start working, run:

    # ram-compilesession loadsession

This creates a ramdisk and loads any previous build files into it.
If they don't exist, it creates them by running cmake.

Continue to edit code as normal where it resides on disk. No sources exist on the ramdisk, so no risk of losing work.
Compiling and linking will be super fast as they are operating in a ramdisk.

At any time just run:

    # ram-compilesession saveram

This saves the contents of the ramdisk to nonvolatile storage.

When finished working, run:

    # ram-compilesession endsession

This saves the contents of the ramdisk to nonvolatile storage and destroys the ramdisk.

## Configuration

Open the ram-compilesession file and at the top are 7 parameters that can be changed.
They are all explained in the file. Be sure to set these before running anything!

Be sure to make it executable by running:

    # chmod +x ram-compilesession

### Notes

This is definitely not as polished as I would like it to be. More work needs to be done, and more features need to be added. These will come with time.
