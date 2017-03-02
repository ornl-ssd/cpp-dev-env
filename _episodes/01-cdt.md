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

<img src="{{ site.github.url }}/fig/01-cdt-new.png" width="50%"/>

There are many settings that you can change on this wizard, but for now, just give your project a name (e.g. "my_project"). 
You should also choose `Hello World C++ Project` from the `Executable` folder in the **Project type:** box. Finally, select
a toolchain compatible with your system (`MinGW GCC` for Windows, `MacOSX GCC` for Mac OS X, or `GCC` for Linux.) 

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
to access a wide range of functions. See the [C/C++ editor documentation](http://help.eclipse.org/neon/topic/org.eclipse.cdt.doc.user/concepts/cdt_c_editor.htm?cp=8_2_5_0) for complete details on how to use the editor.

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

### Making Changes

Let's add some code to the program so it does something more useful. First, let's create a new file called `func.cpp` by selecting
**File** > **New** > **Source File**. This will open the *New Source File* wizard. 

<img src="{{ site.github.url }}/fig/01-cdt-new2.png" width="30%">

All you need to do is enter the name of the file in the `Source file:` field and click on **Finish**. The new file will automatically
open an editor window. If you left the default C++ source template setting the same, then the file will have a comment at the beginning.

Now enter the following code (or copy and paste if you already have it) below the comment.

~~~
// A function to increment its argument
int func(int a) {
	return a+1;
}
~~~
{: .code}

Save this file using **File** > **Save**, then select the `my_project.cpp` tab. Add an external declaration and call to `func()` as follows:

~~~
#include <iostream>
using namespace std;

extern int func(int);

int main() {
	cout << "!!!Hello World!!!" << endl; // prints !!!Hello World!!!
	int a = func(2);
	cout << "func is " << a << endl;
	return 0;
}
~~~
{: .code}

Compile the program again by clicking on the **Build** button (the hammer icon). Notice that you didn't need to make any changes
to the Makefiles, CDT did this for you!

Finally, run the program again to check the output reflects the changes you made.

### Fixing Bugs

Now, lets run the program, but this time under the control of a debugger. To start the debugger just choose **Run** > **Debug**. 
The first time you do this, you will see the dialog below. This is just to warn you that the perspective is going to switch to the Debug perspective. If you want this
to happen automatically in the future (and I would recommend doing so), check the box next to **Remember my decision** 
and click on **Yes**.

<img src="{{ site.github.url }}/fig/01-cdt-switch.png">

Whoa, everything just changed! Don't worry, this was supposed to happen. You are now in a C++ debugger, and rather than
having to launch a separate tool, CDT has done it all for you. Here's what you should see:

<img src="{{ site.github.url }}/fig/01-cdt-debug.png" width="75%">

By default, the debugger will suspend the program at the first executable statement. This is line 14 in `my_project.cpp`.

This looks a little complicated, but it is all layed out pretty logically:

1. Across the top is a *toolbar* with a variety of debug commands. Well use some of these in a minute. 
2. Below that is the **Debug** view (top left) which shows the current *call stack*. You can see that the line 
   `main() at my_project.cpp:14 0x100000f2d` is highlighted, which tells you that the program is currently
   suspended at line 14 of my_project.cpp. This view is important for navigating up and down
   the call stack.
3. To the right is the **Variables** view (top right) which shows all the local and global variables in the program (currently
   `res` has the value 0.)
4. Behind the Variabls view, but not visible, is the **Breakpoints** view, which lists all the breakpoints you've set.
5. Below the Debug view is the normal editor you're used to using. The editor has a marker in it showing the line
   at which the program is suspended, and this line is also highlighted.
6. To the right of the editor is the **Outline** view, which shows a high level outline of the program.
7. Finally, at the bottom is the **Console** view that we've seen before (there are also some other views we're
   not going to discuss here.
  
Now, we're going to tell the program to execute statements one at a time so we can see
what is going on. We do this by *single stepping* the program. There are three buttons on the toolbar that we can use
to do this:

* <img src="{{ site.github.url }}/fig/01-cdt-step-into.png"> **Step Into** - Single step the program, but when a function
  call is encountered, step *into* the function.
* <img src="{{ site.github.url }}/fig/01-cdt-step-over.png"> **Step Over** - Single step the program, but when a function
  call is encountered, step *over* the function (i.e. execute the function as if it was a builtin function).
* <img src="{{ site.github.url }}/fig/01-cdt-step-return.png"> **Step Return** - Single step the program, but return
  immediately to where the current function was called from. Note that this is greyed out as we are at the top level
  of the program and so there is nowhere to return to.
 
So, lets begin by clicking on the <img src="{{ site.github.url }}/fig/01-cdt-step-over.png"> **Step Over** button. When you do this,
you'll notice that the current line moves to line 15. Since line 14 has just been executed, you should see the result printed in the console.

<img src="{{ site.github.url }}/fig/01-cdt-debug2.png" width="75%">

Now we want to step *into* funtion `func`, so lets click on the <img src="{{ site.github.url }}/fig/01-cdt-step-into.png"> **Step Into** button.
This will switch the editor to the `func.cpp` file and show that the current line is now line 9 in this file. The `func` function also appears in 
the call stack, Notice that the variables view has changed, and now shows the value of the argument `a` that
was passed into the function.

<img src="{{ site.github.url }}/fig/01-cdt-debug3.png" width="75%">

Now if we click on the <img src="{{ site.github.url }}/fig/01-cdt-step-return.png"> **Step Return** button, we will be taken back to the
main program. Notice that the variables view shows the result from the function as well as the current value of `res` in the variables view.
Press <img src="{{ site.github.url }}/fig/01-cdt-step-over.png"> **Step Over** a one more time and observe what happens.

<img src="{{ site.github.url }}/fig/01-cdt-debug4.png" width="75%">

Now that we've finished debugging, we can click on the <img src="{{ site.github.url }}/fig/01-cdt-terminate.png"> 
**Terminate** button to end the debug session. 

> ## Breakpoints
>
> Suppose we have a good idea where we want to start looking for bugs rather than stepping through the whole program. The way to do this is
> by setting a *breakpoint*. To do this, just point to the line number in the left hand margin of the file you wish to suspend execution of 
> the program (e.g. line 9 in `func.cpp`) and double click. You should now see a  breakpoint marker appear next to the number.
> 
> <img src="{{ site.github.url }}/fig/01-cdt-breakpoint.png">
>
> Once you start the debug session, you can then click on the <img src="{{ site.github.url }}/fig/01-cdt-resumer.png"> **Resume** button, and 
> the program will execute until the breakpoint is encountered. Try this by setting a breakpoint at line 9 of `func.cpp` and see what happens.
{: .challenge}

### Where To Go From Here?

* [The PyDev homepage](http://pydev.org)
* [The PyDev user manual](http://www.pydev.org/manual.html)
* [A blog that has information on PyDev development](http://pydev.blogspot.com)
* [PyDev bug tracker](https://sw-brainwy.rhcloud.com)
* [PyDev feature requests](https://sw-brainwy.rhcloud.com)
* [Source code](https://github.com/fabioz/Pydev)
* If you have questions, [StackOverflow (with the PyDev tag)](http://stackoverflow.com/questions/tagged/pydev)
 
