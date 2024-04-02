# This is Lab Report 1 - Remote Access and FileSystem (Week 1)

For **all 9 examples** below, the absolute path to the working directory is `C:/Users/inclo/Documents/CSE15L/lecture1`.

## `cd`
1. "Share an example of using the command with *no* arguments." <br/>
```
inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
$ cd

inclo@landons-laptop MINGW64 ~
```
I got this output because without any arguments, `cd` goes back to the top of my User directory, at `C:/Users/inclo/`. <br/>
This output is not an error, since the command had the expected output, which was to change the directory. <br/>
<br/>
2. "Share an example of using the command with a path to a *directory* as an argument." <br/>
```
inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
$ cd messages/

inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1/messages (main)
```
I got this output because the relative path passed in as an argument was `./messages`, so `cd` used the given path to change the directory to `C:/Users/inclo/Documents/CSE15L/lecture1/messages`. <br/>
This behavior is not an error, as it successfully navigated to the directory provided by the path. <br/>
<br/>
3. "Share an example of using the command with a path to a *file* as an argument." <br/>
```
inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
$ cd messages/en-us.txt
bash: cd: messages/en-us.txt: Not a directory

inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
```
I got this output because it is impossible to change directory to a text file, as `en-us.txt` does not have any other files inside of it. <br/>
This behavior is an error, as the directory was not changed in the end, remaining in the working directory that had been provided at the start. <br/>

## `ls`
