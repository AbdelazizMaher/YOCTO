# Poky

**Poky** is a reference distribution of Yocto Project. The word **"reference"** is used to mean **"example"** in this context.

Yocto Project uses Poky to build images `(kernel, system, and application software)`for targeted hardware.

At the technical level it is a combined repository of the components:

-  Bitbake
-  OpenEmbedded Core
-  meta-yocto-bsp
-  Documentation

**Note:** Poky does not contain binary files,it is a working example of how to build your own custom Linux distribution from source.

## Difference between poky and Yocto

Difference between Yocto and Poky is Yocto refers to the organization `( like one would refer to 'canonical', the company behind Ubuntu )`, and Poky refers to the actual bits downloaded` ( analogous to 'Ubuntu' )`

**Poky includes:**

- some OE components(oe-core)
- bitbake
- demo-BSP's
- helper scripts to setup environment
- emulator QEMU to test the image

  
| Poky = Bitbake + Metadata |
| :-----------------------: |

 
### 1- Metadata 

- Metadata refers to the build instructions
- Commands and data used to indicate what versions of software are used
- Where they are obtained from
- Changes or additions to the software itself ( patches ) which are used to fix bugs or customize the software for use in a particular situation

**Metadata is collection of:**

- Configuration files (.conf)
- Recipes (.bb and .bbappend)
- Classes (.bbclass)
- Includes (.inc)

	
### 2- Recipes

A recipe is a set of instructions that is read and processed by the bitbake ( a software component)

**Extension of Recipe: .bb**

A recipe describes:
- where you get source code
- which patches to apply
- Configuration options
- Compile options (library dependencies)
- Install
- License


### 3- Configuration Files

They tell the build system what to build and put into the image to support a particular platform

Files which hold:
- global definition of variables
- user defined variables and
- hardware configuration information

**Extension: .conf**
	
	
### 3- classes

Class files are used to abstract common functionality and share it amongst multiple recipe (.bb) files

- To use a class file, you simply make sure the recipe inherits the class
  
- They are usually placed in classes directory inside the `meta* directory`


```bash
Eg. inherit classname
```

**Extension: .bbclass**

Example of classes
-------------------

`cmake.bbclass` - Handles cmake in recipes

`kernel.bbclass` - Handles building kernels. Contains code to build all kernel trees

`module.bbclass` - Provides support for building out-of-tree Linux Kernel Modules


## 4- Layers

A collection of related recipes **or** Layers are recipe containers (folders)

**Typical naming convention:** meta-<layername>

Poky has the following layers:

`meta`, `meta-poky`, `meta-selftest`, `meta-skeleton`, `meta-yocto-bsp`


Image
-----------

- An image is the top level recipe, it has a description, a license and inherits the core-image class

- It is used alongside the machine definition,where a machine describes the hardware used and its capabilities

**`Image`** is architecture agnostic and defines how the root filesystem is built, with what packages.



Command to check the list of available image recipes
----------------------------------------------------
```bash
ls meta*/recipes*/images/*.bb
```

Packages
-------------

A package is a binary file with name `*.rpm`, `*.deb`, or `*.ipkg`

A single recipe produces many packages. All packages that a recipe generated are listed in the recipe variable




