# This is Lab Report 1 - Remote Access and FileSystem (Week 1)

For **all 9 examples** below, the absolute path to the working directory is `~/Documents/CSE15L/lecture1`.

## `cd`
1. "Share an example of using the command with *no* arguments." <br/>
```
inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
$ cd

inclo@landons-laptop MINGW64 ~
```
I got this output because without any arguments, `cd` goes back to the top of my User directory, at `~`. <br/>
This output is not an error since the command had the expected output, which was to change the directory. <br/>
<br/>
2. "Share an example of using the command with a path to a *directory* as an argument." <br/>
```
inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
$ cd messages/

inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1/messages (main)
```
I got this output because the relative path passed in as an argument was `./messages`, so `cd` used the given path to change the directory to `~/Documents/CSE15L/lecture1/messages`. <br/>
This behavior is not an error, as it successfully navigated to the directory provided by the path. <br/>
<br/>
3. "Share an example of using the command with a path to a *file* as an argument." <br/>
```
inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
$ cd messages/en-us.txt
bash: cd: messages/en-us.txt: Not a directory

inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
```
I got this output because it is impossible to change the directory to a text file, as `en-us.txt` does not have any other files inside of it. <br/>
This behavior is an error, as the directory was not changed in the end, remaining in the working directory that had been provided at the start. <br/>

## `ls`
1. "Share an example of using the command with *no* arguments." <br/>
```
inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
$ ls
Hello.class  Hello.java  messages/  README

inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
```
Having no arguments meant that running `ls` would simply list the contents of the working directory, as reflected in the output. <br/>
This behavior is not an error. <br/>
<br/>
2. "Share an example of using the command with a path to a *directory* as an argument." <br/>
```
inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
$ ls ../
CSE15L-S24-Lecture02-URLs-Paths-git.pptx.pdf  CSE15L-S24-Lecture03-SSH-URLs-Video.pptx.pdf  lecture1/  wavelet/
```
The command listed the contents of the folder `~/Documents/CSE15L`, as the relative path I gave was to that folder. <br/>
This output is not an error, as it correctly listed all the contents of the given directory. <br/>
<br/>
3. "Share an example of using the command with a path to a *file* as an argument." <br/>
```
inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
$ ls Hello.java
Hello.java
```
I got this output because `Hello.java` is the only file that the command could parse from the relative path I gave it. Technically, it's listing the contents of `~/Documents/CSE15L/lecture1/Hello.java`, which is why it simply restates the filename. <br/>
This output is not an error, since the command produces an output that corresponds with the relative path given to it. <br/>

## `cat`
1. "Share an example of using the command with *no* arguments." <br/>
```
inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
$ cat
```
There was no further output from my terminal after running `cat` with no arguments, since the command requires two filepaths and it was run with none. <br/>
This output is an error because it bricks my terminal and prevents me from running any other commands, requiring me to kill that terminal and make a new one. <br/>
<br/>
2. "Share an example of using the command with a path to a *directory* as an argument." <br/>
```
inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
$ cat ./ ../
cat: ./: Is a directory
cat: ../: Is a directory
```
I ran the command using two paths, just to show that the command supports multiple, but a similar output is generated with just one path to a directory. I got this output because `cat` requires a filepath, rather than a path to a directory. Thus, the command returns an error message. <br/>
This output is an error because it doesn't print the contents of anything, instead returning an error message to notify the user that they are using the command improperly. <br/>
<br/>
3. "Share an example of using the command with a path to a *file* as an argument." <br/>
```
inclo@landons-laptop MINGW64 ~/Documents/CSE15L/lecture1 (main)
$ cat ./Hello.java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);
    System.out.println(content);
  }
}
```
I got this output because I input a command to print the contents of `Hello.java`, which is reflected in the output. <br/>
This output is not erroneous, since it printed every line within the text file. <br/>
