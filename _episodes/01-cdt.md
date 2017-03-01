---
title: "C/C++ Development Tools"
teaching: 30
exercises: 0
questions:
- "How can I used CDT to develop C++ applications"
- "What are the main features of CDT that will help me develop C++ programs"
objectives:
- "Learn how to configure CDT."
- "Learn how to create C++ projects."
- "Understand the basic features of Eclipse."
- "Be familiar with terminology."
- "Experiment with the software engineering features of Eclipse and CDT."
keypoints:
- "CDT provides a complete integrated environment for C++ development"
- "Integration with other tools, such as Git version control, are also available"
- "CDT is useful for small, medium or large collaborative projects"
- "CDT automates many aspects of C++ development"
---

CDT is an Eclipse-based development environment for C and C++ programs. It provides a commercial-quality
environment for working on any size development projects. The main features provided by CDT include:

* Syntax highlighting
* Code formatting
* Code completion
* Code analysis
* Type hinting
* Refactoring
* Visual debugging
* Unittest integration
* Code coverage

In addition, because CDT is built using Eclipse, it also has available many of the development tools that
are integrated with the Eclipse environment, such as Git and modeling tools.

### Your First Project

After starting Eclipse and selecting a workspace where your files will be kept (the default one is fine), you are
now ready to create your first project.  Here is a screenshot of the main window of the C/C++ perspective. This is 
for Mac OS X, but it should look similar on Windows and Linux.

<img src="{{ site.github.url }}/fig/01-cdt-main.png"/>

You can ignore most of the icons and menus for now. The first thing to notice is that it is divided into two
parts. On the left is the Project Explorer. This is where your projects, directories, and files will be
visible. On the right is a big empty area that we will be using to edit C++ code soon.

To create a new project, select **File** > **New**. You'll notice there are a number of different project types you
can create. These are:

**Makefile Project with Existing Code**
: This is for creating a project from an existing source distribution. Although it assumes that the project is built
using a Makefile, other types of build systems can also be used.

**C++ Project**
: This is for creating a new C++ project and will include options specific to building C++ programs. It assumes that CDT 
will automatically generate the Makefiles to build the project.

**C Project**
: This is for creating a new C project and will include options specific to building C programs. It assumes that CDT will 
]automatically generate the Makefiles to build the project.

**C/C++ Project**
: This is just another way of choosing either a C++ or C project.

In this case, we're going to choose **C++ Project**. Once you select this option, you will see the C++ Project wizard.
There are many settings that you can change on this wizard, but for now, just give your project a name (e.g. "my_project"). 
You should also choose `Hello World C++ Project` from the `Executable` folder in the **Project type:** box.

<img src="{{ site.github.url }}/fig/01-cdt-new.png" width="50%"/>

When you're done, select the **Finish** button and you should see the project appear in the Project Explorer view.
Clicking on the small triangle to the left of the project will open it. Open the `src` folder and you will see
a file called `my_project.cpp` that was automatically created for you.

<img src="{{ site.github.url }}/fig/01-cdt-first.png">

### Editor Features

If you used the `Hello World C++ Project` template, CDT will have automatically created a file called `my_project.cpp` and
opened the source code editor.

<img src="{{ site.github.url }}/fig/01-cdt-editor.png">

The first editor feature you will notice is syntax highlighting (color coding of keywords and strings). Code folding is achieved by clicking
on the + and - icons on the left side of the editor. Right clicking in the editor window will open a pop-up menu that will allow you
to access a wide range of functions. See the [C/C++ editor](http://help.eclipse.org/neon/topic/org.eclipse.cdt.doc.user/concepts/cdt_c_editor.htm?cp=8_2_5_0) for complete details on how to use the editor.

Other visible features include an outline view on the right hand edge of the editor. This view shows the high level structure of the code.
At the bottom of the main window are three status fields. The first shows permissions for the file being edited (`Writable`, `Read Only`, etc.).
The second shows the edit mode (`Smart Insert` or `Overwrite`) which can be changed by double clicking on the field. The last field
shows the line and character position of the insertion point.

When you modify the code in the editor, an asterisk (`*`) will be displayed next to 
the name of the file in the editor tab. This provides a visual indication that the file has been modified and needs to be saved. 

### Compiling My Program

One of the advantages of using a development environment like CDT is that it can manage how the program is built. When we chose an `Executable`
project type, we told CDT to automatically create Makefiles for the project. Other project types may require us to provide our own Makefiles.

To compile the program, simply make sure the project is selected in the Projet Explorer view, then click on the **Build** button (the hammer icon).
When you do this, you will see a new folder called `Debug` created. Open this folder, and you will see it now contains various Makefiles (and 
files ending in `.mk`, as well as object files, and an executable. The program has now been compiled!

<img src="{{ site.github.url }}/fig/01-cdt-build.png">

### Running My Program

Running the program is easy. Just make sure that the project is selected in the Project Explorer view, and choose
**Run** > **Run**. Your program should immediately run, and the results will be displayed 
in a Console view which popped up below the editor window.

<img src="{{ site.github.url }}/fig/01-cdt-console.png">

### Fixing Bugs

Let's run the same Python program, but this time under the control of a debugger. First, let's tell the debugger that
we want to suspend execution when the `print(fib(10))` statement is about to be executed. To do this, we need to set a 
*breakpoint* at line 13. Just point to the number `13` in the left hand margin and double click. You should now see a 
breakpoint marker on the line.

<img src="{{ site.github.url }}/fig/01-pydev-breakpoint.png">

Now, to start the debugger just choose **Run** > **Debug**. The first time you do this, you will see the dialog
below. This is just to warn you that the perspective is going to switch to the Debug perspective. If you want this
to happen automatically in the future (and I would recommend doing so), check the box next to **Remember my decision** 
and click on **Yes**.

<img src="{{ site.github.url }}/fig/01-pydev-switch.png">

Whoa, everything just changed! Don't worry, this was supposed to happen. You are now in a Python debugger, and rather than
having to launch a separate tool, PyDev has done it all for you. Here's what you should see:

<img src="{{ site.github.url }}/fig/01-pydev-debug.png">

This looks a little complicated, but it is all layed out pretty logically:

1. Across the top is a *toolbar* with a variety of debug commands. Well use some of these in a minute. 
2. Below that is the **Debug** view (top left) which shows the current *call stack*. You can see that the line 
   `<module> [my_module.py:13]` is highlighted, which tells you that the program is currently
   suspended at line 13 of my_module.py (where we put the breakpoint.) This view is important for navigating up and down
   the call stack.
3. To the right is the **Variables** view (top right) which shows all the local and global variables in the program.
4. Behind the Variabls view, but not visible, is the **Breakpoints** view, which lists all the breakpoints you've set.
5. Below the Debug view is the normal editor you're used to using. The editor has a marker in it showing the line
   at which the program is suspended, and this line is also highlighted.
6. To the right of the editor is the **Outline** view, which shows a high level outline of the program.
7. Finally, at the bottom is the **Console** view that we've seen before (there are also some other views we're
   not going to discuss here.
  
Now, in order to work out the bug, we're going to tell the program to execute statements one at a time so we can see
what is going on. We do this by *single stepping* the program. There are three buttons on the toolbar that we can use
to do this:

* <img src="{{ site.github.url }}/fig/01-pydev-step-into.png"> **Step Into** - Single step the program, but when a function
  call is encountered, step *into* the function.
* <img src="{{ site.github.url }}/fig/01-pydev-step-over.png"> **Step Over** - Single step the program, but when a function
  call is encountered, step *over* the function (i.e. execute the function as if it was a builtin function).
* <img src="{{ site.github.url }}/fig/01-pydev-step-return.png"> **Step Return** - Single step the program, but return
  immediately to where the current function was called from. If the current function is the main program, exit the program.
 
So, lets begin by clicking on the <img src="{{ site.github.url }}/fig/01-pydev-step-into.png"> **Step Into** button. When you do this,
you'll notice that the `fib` function appears in the call stack, and we see the current line in the editor move to the first
line of the function. Also, notice that the variables view has changed, and now shows the value of the argument `n` that
was passed into the function.

<img src="{{ site.github.url }}/fig/01-pydev-vars.png">

If we click on <img src="{{ site.github.url }}/fig/01-pydev-step-into.png"> again, we can see which branch of the `if`
statement was taken (the second, since `n` is currently 10.) Keep clicking on 
<img src="{{ site.github.url }}/fig/01-pydev-step-into.png">
and you will see more and more entries for `fib` in the call stack. This is because the `fib` function is *recursive*, 
i.e. it calls itself. We are interested in when `fib` is called with the value 2. Notice that when this happens, the
`fib` function still takes the second branch of the `if` statement.

AHA!

We know that the second element of the Fibonacci sequence is 1, so `fib(2)` should return the value 1. Instead, it will
return the value of `fib(1) + fib(0)` which will evaluate to 2 in our function. Our `if` statement
should actually be `if n <= `**`2`**`:`.

Now that we've finished debugging, we can click on the <img src="{{ site.github.url }}/fig/01-pydev-terminate.png"> 
**Terminate** button to end the debug session. 

### Where To Go From Here?

* [The PyDev homepage](http://pydev.org)
* [The PyDev user manual](http://www.pydev.org/manual.html)
* [A blog that has information on PyDev development](http://pydev.blogspot.com)
* [PyDev bug tracker](https://sw-brainwy.rhcloud.com)
* [PyDev feature requests](https://sw-brainwy.rhcloud.com)
* [Source code](https://github.com/fabioz/Pydev)
* If you have questions, [StackOverflow (with the PyDev tag)](http://stackoverflow.com/questions/tagged/pydev)
 
