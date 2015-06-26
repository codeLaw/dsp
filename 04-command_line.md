# Learn command line

Please follow and complete the free online [Command Line Crash Course
tutorial](http://cli.learncodethehardway.org/book/). This is a great,
quick tutorial. Each "chapter" focuses on a command. Type the commands
you see in the _Do This_ section, and read the _You Learned This_
section. Move on to the next chapter. You should be able to go through
these in a couple of hours.


---

Make a cheat sheet for yourself: a list of commands and what they do, focused on things that are new, interesting, or otherwise worth remembering.

REPLACE THIS TEXT WITH YOUR RESPONSE

---


---

What does `ls` do? What do `ls -a`, `ls -l`, and `ls -lh` do? What combinations of those flags are meaningful?

>'ls' lists the contents of a given directory.  'ls -a' lists all of the contents of a given directory inalcuding those files that start with a '.'.  'ls -l' lists the contents in long format (including permissions, user, file size, data, time, file name)

---


---

What does `xargs` do? Give an example of how to use it.

>'xargs' is often used with 'find' and 'grep' to obtain file information from standard input.  For example:

>find . -name "*.py" | xargs grep "Pandas"

>This command searches for all files with the '.py' extension and then searches these files for the keyword "Pandas."

---
