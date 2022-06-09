# Introduction to the Command Line

<a href="http://creativecommons.org/licenses/by-nc/4.0/" rel="license"><img style="border-width: 0;" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" alt="Creative Commons License" /></a>
This tutorial is licensed under a <a href="http://creativecommons.org/licenses/by-nc/4.0/" rel="license">Creative Commons Attribution-NonCommercial 4.0 International License</a>.

This lab covers a variety of topics related to how computers "work." This lab is designed to help you gain an understanding of how the basic logical and mathematical operations underlying computation are performed mechanically. We will also use a simulation of CPU architecture to learn more about how an instruction is processed along the CPU data path cycle and how values from memory are incorporated into CPU instructions. We are doing this to gain more experience with understanding a computer’s mechanical operations at a higher level of abstraction. Finally, this lab covers reading and writing basic machine language, to help us see the 0s and 1s underneath higher level programming and apply them to basic algorithms.

<table>
 <tr><td>
<img src="https://elearn.southampton.ac.uk/wp-content/blogs.dir/sites/64/2021/04/PanPan.png" alt="Panopto logo" width="50"/></td>
  <td><a href="https://notredame.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=63a3251a-e1d0-4b36-b002-ad3d00cb609c">LAB OVERVIEW PLACEHOLDER</a></td>
  </tr>
  </table>
  
<table>
 <tr><td>
<img src="https://elearn.southampton.ac.uk/wp-content/blogs.dir/sites/64/2021/04/PanPan.png" alt="Panopto logo" width="50"/></td>
<td><a href="https://notredame.hosted.panopto.com/Panopto/Pages/Viewer.aspx?pid=d55a3a86-9e99-4008-9e4f-ae510174ce65">LECTURE/LIVE CODING PLAYLIST PLACEHOLDER</a></td>
  </tr>
  </table>

## Acknowledgements

This lab is based on and adapts content from the following tutorials:
- Ian Milligan and James Baker, "Introduction to the Bash Command Line," The Programming Historian 3 (2014), https://doi.org/10.46430/phen0037.
- Miriam Posner, "[Getting Started With Unix](https://github.com/miriamposner/unix/blob/main/getting_started_with_commandline.md)" tutorial

# Table of Contents

- [Lecture and Live Coding](#lecture-and-live-coding)
- [Lab Notebook Template](#lab-notebook-template)
- [Working at the Command Line](#working-at-the-command-line)
  * [Opening Your Shell](#opening-your-shell)
  * [Terminal Wayfinding](#terminal-wayfinding)
  * [Typing Commands in the Terminal](#typing-commands-in-the-terminal)
  * [Navigating Your File System](#navigating-your-file-system)
    * [`ls`](#ls)
    * [`cd`](#cd)
  * [Additional Resources](#additional-resources)
- [Lab Notebook Questions](#lab-notebook-questions)

# Lecture and Live Coding

Throughout this lab, you will see a Panopto icon at the start of select sections.

This icon indicates there is lecture/live coding asynchronous content that accompanies this section of the lab. 

You can click the link in the figure caption to access these materials (ND users only).

Example:

<table>
 <tr><td>
<img src="https://elearn.southampton.ac.uk/wp-content/blogs.dir/sites/64/2021/04/PanPan.png" alt="Panopto logo" width="50"/></td>
  <td><a href="https://notredame.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=63a3251a-e1d0-4b36-b002-ad3d00cb609c">LAB OVERVIEW PLACEHOLDER</a></td>
  </tr>
  </table>
  
<table>
 <tr><td>
<img src="https://elearn.southampton.ac.uk/wp-content/blogs.dir/sites/64/2021/04/PanPan.png" alt="Panopto logo" width="50"/></td>
<td><a href="https://notredame.hosted.panopto.com/Panopto/Pages/Viewer.aspx?pid=d55a3a86-9e99-4008-9e4f-ae510174ce65">LECTURE LIVE CODING PLACEHOLDER</a></td>
  </tr>
  </table>

# Lab Notebook Template

[Link to lab notebook template](https://docs.google.com/document/d/11zPRqQiJG_UBU3Ja6DB32oKqM_6VGXCGbjGXuzSoHR4/copy) (ND users, Google Doc)
 
# Working at the Command Line

<table>
 <tr><td>
<img src="https://elearn.southampton.ac.uk/wp-content/blogs.dir/sites/64/2021/04/PanPan.png" alt="Panopto logo" width="50"/></td>
<td><a href="https://notredame.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=879d98fd-b758-412a-982b-ad3d00c65d52">Command Line Interface</a></td>
  </tr>
  </table>

 *The Programming Historian* is a multi-language, peer-reviewed online resource with "novice-friendly, peer-reviewed tutorials that help humanists learn a wide range of digital tools, techniques, and workflows to facilitate research and teaching" (["The Programming Historian"](https://programminghistorian.org/))
 
In this lab, we will work through an adapted version of the "[Introduction to the Bash Command Line](https://programminghistorian.org/en/lessons/intro-to-bash)" lesson, to apply the concepts covered in the "Bite Size Command Line" zine.
- Ian Milligan and James Baker, "Introduction to the Bash Command Line," The Programming Historian 3 (2014), https://doi.org/10.46430/phen0037.
 
The text content below is adapted from the *PH* lesson as well as Miriam Posner's "[Getting Started With Unix](https://github.com/miriamposner/unix/blob/main/getting_started_with_commandline.md)" tutorial.

1. The usual way that computer users today interact with their system is through a Graphical-User Interface, or GUI. This means that when you go into a folder, you click on a picture of a file folder; when you run a program, you click on it; and when you browse the web, you use your mouse to interact with various elements on a webpage. Before the rise of GUIs in the late 1980s, however, the primary way to interact with a computer was through a command-line interface [CLI].

2. Command-line interfaces have advantages for computer users who need more precision in their work – such as digital historians. They allow for more detail when running some programs, as you can add modifiers to specify exactly how you want your program to run. Furthermore, they can be easily automated through scripts, which are essentially recipes of text-based commands.

3. There are two main command-line interfaces, or "shells." On OS [Mac] or many Linux installations, the shell is known as `bash`, or the ‘Bourne-again shell.’ For users on Windows-based systems, the command-line interface is by default `MS-DOS-based`, which uses different commands and syntax, but can often achieve similar tasks. This tutorial provides a basic introduction to the `bash` terminal, and Windows users can follow along by installing popular shells such as Cygwin or Git Bash [details and instructions provided below].

<table>
 <tr><td>
<img src="https://www.freeiconspng.com/thumbs/survey-icon/survey-icon-12.png" alt="Clipboard icon" width="50"/></td>
  <td><a href="https://docs.google.com/forms/d/e/1FAIpQLSdq6gyJ26OLOWUVG4c1HVhiXPz3Q0b68Gqv1r0qfQhSR0zW9Q/viewform?usp=sf_link">Operating Systems Lecture Check-In</a></td>
  </tr>
  </table>

### For Windows Users

4. For Mac users (and most Linux installations), you’re in luck — you already have a bash shell installed. 

5. Windows users will need to take one extra step and install Git Bash. 
- Download the most recent ‘Full installer’ at [this page](https://git-for-windows.github.io)
- Instructions for installation are available at [Open Hatch](https://web.archive.org/web/20190114082523/https://openhatch.org/missions/windows-setup/install-git-bash)

## Opening Your Shell

*NOTE: The following screenshots show the Mac OS terminal/shell. Folks with other operating systems should still be able to follow the procedural steps.*

<p align="center"><img align="center" src="https://github.com/kwaldenphd/how-computers-work/blob/main/images/Fig_A1.png?raw=true" alt="Image of Mac Shell icon"></p>
 
6. To launch the terminal...

Mac:
- By default, the shell is located in `Applications -> Utilities -> Terminal`

Windows:
- Run Git Bash from the directory that you installed it in. You will have to run it as an administrator - to do so, right click on the program and select 'Run as Administrator.'

<p align="center"><img align="center" src="https://github.com/kwaldenphd/how-computers-work/blob/main/images/Fig_A.png?raw=true" alt="Image of Mac Shell"></p>
 
7. When the terminal or shell is running, you will see a window that looks similar to the image above.

<p align="center"><img align="center" src="https://github.com/kwaldenphd/how-computers-work/blob/main/images/Fig_B.png?raw=true" alt="Image of Mac terminal settings"></p>
 
8. For Mac users who want to customize the terminal's visual appearance:
- Open the `Settings` menu (in `Preferences`, under `Terminal`)
- Click the `Settings` tab to change the color scheme

9. Windows users can right-click on the application's top bar and select `Properties` to open the `Properties` tab.

## Terminal Wayfinding

<p align="center"><img align="center" src="https://github.com/kwaldenphd/how-computers-work/blob/main/images/Fig_C.jpeg?raw=true" alt="Image of Mac shell"></p>

*NOTE: The following text and images are adapted from UCLA faculty member Miriam Posner's "[Getting Started With Unix](https://github.com/miriamposner/unix/blob/main/getting_started_with_commandline.md)" tutorial*

10. This is a terminal window, also called a `shell`. 

11. The active cursor showing up in the window is a `command prompt`. This is where you will type commands or instructions.

12. First, we can check your username using the `whoami` command.

13. Type `whoami` in the shell and hit the `Enter` or `Return` key.

14. The terminal returns your username.

15. The terminal's command prompt is ready for another command or instruction.

16. Let's try another command- this type, we'll use `echo` to repeat a set of characters in quotation marks.

17. Type `echo 'Hello world!' into the terminal and hit the 'Enter' or 'Return' key.

18. The `echo` command instructs the terminal to repeat whichever characters you include in the quotation marks.

## Typing Commands in the Terminal

19. You may have already noticed you're not able to navigate the terminal using your mouse or cursor.

20. We can navigate the terminal using the keyboard.

21. The `up` and `down` arrow keys let you move back (up) and forward (down) through previously typed commands. 

22. The `left` and `right` arrow keys let you move within characters or symbols for a specific command.

23. Press the `up` arrow once to show the previously-typed `echo` command.

24. Then, use the `left` and `right` arrow keys to navigate to the characters within the quotation marks and replace them with another word or phrase of your choosing.

25. Press `Return` or `Enter` to run the modified command. 

26. A couple other useful navigation tools:
- Press `Control` + `A` to move to the start of a line
- Press `Control` + `E` to move to the end of a line
- Type `clear` into the terminal and press `Return`/`Enter` to clear the screen
- When you're ready to close the terminal window, type `exit` and press `Return`/`Enter`

<p align="center"><img align="center" src="https://github.com/kwaldenphd/how-computers-work/blob/main/images/Fig_D.jpeg?raw=true" alt="Diagram illustrating terminal syntax"></p>

27. A couple notes on terminal syntax:
- `commands` tell the computer to perform an action 
- `options` modify the command and use a hyphen (`-`) symbol
  * Sometimes `options` are called `flags` or `switches`
- `arguments` specify what the command operation will be performed on (i.e. a specific file or directory)

28. Not all commands require arguments or options, but some commands can have one or more of each.

29. You can also chain multiple commands together using the vertical bar `|` symbol. This is often called a `pipe`.

## Navigating Your File System

30. Before we start moving around, let's use the `pwd` (print working directory` command to show your current location.

31. Type `pwd` in the terminal and press `Enter` or `Return`.

32. Your output might look something like this:
```
/Users/kwalden
```

33. This directory information is called a `path` (sometimes called a `file path` when dealing with specific files).
- The backslash `/` at the start of the path stands for your computer's `root`
- Subsequent slashes indicate subfolders or subdirectories

34. So in the `/Users/kwalden` example, the terminal is running in the `kwalden` subfolder which is located in the `Users` folder. The `Users` folder is located at my computer's `root`.

<p align="center"><img align="center" src="https://github.com/kwaldenphd/how-computers-work/blob/main/images/Fig_E.jpeg?raw=true" alt="Diagram illustrating computer directory structure"></p>

35. The inverted tree diagram shown above shows one example of a computer's file system.
- The `root` (top of the tree) is your computer's hard drive.
- The next set of branches are a set of folders (`directories`) that are used by everyone who uses the computer
- The `users` folder includes different specific user profiles
- The folders located under a specific username are associated with that user profile
  * These folders commonly include `Applications`, `Desktop`, `Documents`, `Downloads`, etc.

36. If you have ever used `File Explorer` (Windows) or `Finder` (Mac), you have navigated this tree structure using the graphical user interface (GUI).

37. Now let's think about how we navigate this structure using the command line interface (CLI).

### `ls`

38. Typically by default, your terminal will open in the folder or directory for your user profile.
- But you can check this using the `pwd` (print working directory) command

39. Let's see what other files and subdirectories are located in your current path by using the list command (`ls`).

40. Type `ls` in the terminal and press `Enter`/`Return`.

<p align="center"><img align="center" src="https://github.com/kwaldenphd/how-computers-work/blob/main/images/Fig_F.jpeg?raw=true" alt="Terminal screenshot showing directory contents"></p>

41. Items that are followed by a file extension (e.g. `.docx`, `.txt`, `.xlsx`, etc) are generally individual files. Items that do not have a file extension are typically subfolders or subdirectories.

### `cd`

42. We can move down the tree using the `change directory` command (`cd`).

43. Let's move from your user profile folder to the Desktop.

44. Type `cd Desktop` and press `Enter`/`Return`.
- You can also type `cd Desk` and press the `Tab` key (before `Enter`/`Return`) to autocomplete the command

45. When using the `cd` (change directory) command, we are navigating the computer's file system using `relative paths`. This means the location information we are specifying in the terminal is relative to our current position or location in the file system. 

46. The previous `cd Desktop` command is an example of a relative path.

47. `Absolute paths` always start at the `root` and use backslash `/` symbols to indicate subfolders.
- `/Users/kwalden/Desktop` would be the absolute path version of the previous command
- NOTE: Be sure to replace `kwalden` with your user name

48. We can use the `ls` command again to see the materials located on our Desktop.

49. We can also move back up the file system tree using the `cd` command.

50. Instead of using `cd`  followed by a relative or absolute path, we can use `cd ..` (`cd` followed by a space and two periods) to move up one level in the tree.

51. Type `cd ..` in the terminal and press `Enter`/`Return`. You can test using `pwd` if needed, but you should be back in the specific user profile folder.

## Additional Resources

If you want to further explore command line syntax:
- Software Carpentries, "[The Unix Shell](https://swcarpentry.github.io/shell-novice/)" lesson
- Mary Brent, "[Linux Command Cheat Sheet](https://www.guru99.com/linux-commands-cheat-sheet.html)", *Guru99* (28 May 2022)
- Ian Milligan and James Baker, "Introduction to the Bash Command Line," The Programming Historian 3 (2014), https://doi.org/10.46430/phen0037.
- Miriam Posner, "[Getting Started With Unix](https://github.com/miriamposner/unix/blob/main/getting_started_with_commandline.md)" tutorial

# Lab Notebook Questions

All of the required questions are listed here for you to reference. Be sure to answer each question completely, including an explanation of how you arrived at your answer.
 
[Link to lab notebook template](https://docs.google.com/document/d/11zPRqQiJG_UBU3Ja6DB32oKqM_6VGXCGbjGXuzSoHR4/copy) (ND users, Google Doc)
  
Q1: Going back to our work with navigating the command line, open a Terminal on your laptop or desktop. Describe what you see. 

Q2: When you use the ls -l (lower-case letter l, lower-case letter s, space, dash, lower-case letter l) command, can you decipher the information that is displayed? Watch https://youtu.be/exQNuYxqFpA to help decode the information.

Q3: Take a few moments to reflect on your experience working in the command line. How does your navigation of the computer at the command line compare other ways of navigating a computer’s user interface?
