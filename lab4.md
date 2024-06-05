# This is Lab Report 4 - Vim (Week 7)

## 4. Log into ieng6
1. ![lab4-Step4](https://github.com/clockuru/cse15l-lab-reports/assets/146829235/471731d8-25e8-429a-8ac3-a4e615e4163d)<br/>
2. `ssh<space>lacannon@ieng6.ucsd.edu<enter>`<br/>
3. I used the `ssh` command in order to enter my user on ieng6 to sign in to. I typed out the full command and pressed `<enter>` because I began this portion with a fresh terminal, meaning that there was no command history for me to save keypresses with.<br/>
## 5. Clone your fork of the repository from your Github account (using the `SSH` URL)
1. ![lab4-Step5](https://github.com/clockuru/cse15l-lab-reports/assets/146829235/9fa89e85-e91b-4dfb-8569-b7627b7a90d5)<br/>
2. `git<space>clone<space><ctrl + v><enter>`<br/>
3. I typed out the majority of the `git clone` command myself, though I copy and pasted the `SSH` URL for my fork with `<ctrl + v>`, as it would be tedious and time-consuming to type it out normally.<br/>
## 6. Run the tests, demonstrating that they fail
1. ![lab4-Step6](https://github.com/clockuru/cse15l-lab-reports/assets/146829235/428830b5-2935-4b01-819a-902b15583b87)<br/>
2. `cd<space>l<tab><enter>` , `bash<space>t<tab><enter>`<br/>
3. For my first set of keypresses, I changed directory into `lab7/` in order to prevent having to type out that directory for the rest of my commands. Additioanlly, I took advantage of `<tab>` by not having any other directories starting with 'L', meaning that I could directly enter the directory with just an 'L' and a `<tab>`. The same applies to the second set of keypresses, where `test.sh` is the only file starting with a 'T'. After typing out the filename, I ran `test.sh` in order to demonstrate that the tests fail.<br/>
## 7. Edit the code to fix the failing test
1. ![lab4-Step7](https://github.com/clockuru/cse15l-lab-reports/assets/146829235/47307231-197c-4443-bd98-204f49ee9f60)<br/>
2. `vim<space><shift + l>.<tab><enter>` , `44<shift + g>/1<enter>r2:wq`<br/>
3. For my first set of keypresses, I used tabs once again in order to save keypresses on typing filenames, getting to `ListExamples.java` with the ones that I used, the file that needs to be corrected. As for my second set of keypresses, I use `44G` in order to skip to line 44, then `/1<enter>` to skip to the '1' in that line. Using `r2` replaces that '1' with a '2', then I quit and write my changes to the file with `:wq`.<br/>
## 8. Run the tests, demonstrating that they now succeed
1. ![lab4-Step8](https://github.com/clockuru/cse15l-lab-reports/assets/146829235/0dc4c9b9-7770-476e-92dc-5c7a30e36539)<br/>
2. `<up><up><enter>`<br/>
3. I inputted `bash test.sh` from my command history by pressing `<up>` twice, then entered it in order to run the tests once more.<br/>
## 9. Commit and push the changes to your Github account (you can pick any commit message!)
1. ![lab4-Step9](https://github.com/clockuru/cse15l-lab-reports/assets/146829235/a7dc2e40-2f9c-483c-823e-3f505d3f80ee)<br/>
2. `git<space>add<space>.<enter>` , `git<space>commit<space>-m<space>"a"<enter>` , `git<space>push<enter>`<br/>
3. I inputted all of the commands to add, commit, and push my changes to my Github account, as I do not think I have any shortcuts to use for this step in terms of typing the commands. The first set of keypresses adds all of the set of changes I'm pushing, with the second set adding a commit message. I simply chose "a" to be my commit message, as it requires just one keypress. Lastly, my third set of keypresses pushes all of the changes I made throughout these steps to my `lab7` repository on Github.<br/>
