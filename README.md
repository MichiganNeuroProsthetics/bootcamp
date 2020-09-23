In this tutorial, you will learn the essentials of Git and the command line interface. These tools will allow for you to confidently develop work in a group setting and take advantage of all of Git's features. Specifically, Git allows multiple users to develop something at once without overlapping, overwriting, or unintentionally sabotaging others' work.

# Command Line Interface and Git Basics
If you're taking EECS 280 right now or have already taken it, you can skip this part, assuming you have bash. Otherwise, follow [this command line interface guide](https://eecs280staff.github.io/p1-stats/setup.html#command-line-tools) to learn how to use shells to use Git in the most effective manner possible. Simply put, version control using the command line interface and cloning is to using GitHub.com manually as copy-pasting using Ctrl+C and Ctrl+V is to using the mouse alone. Sure, using a mouse for copy-pasting once or twice isn't too cumbersome, but when you're constantly executing the task, it becomes rather tedious. Additionally, it's extremely easy to learn! Note that if you're using Windows, make sure to follow the WSL tutorial. You can skip the "Starter Files" section and instead follow [this tutorial](https://tutorial.djangogirls.org/en/intro_to_command_line/) for the basic command line interface; note that if you're using WSL (such as the Ubuntu shell), you will want to follow the macOS and Linux sections. Additionally, you'll want to follow this quick [Git handbook page](https://guides.github.com/introduction/git-handbook/) for more information on how to use Git itself.

# Branching with Git
Next, we will be modifying this repository.

First, clone the "bootcamp" repo if you haven't already. You'll likely want to navigate to where you wish to store it first.
```
cd directory_name
git clone https://github.com/MichiganNeuroProsthetics/bootcamp.git
```
You can also use SSH, which makes life significantly easier.
```
git@github.com:MichiganNeuroProsthetics/bootcamp.git
```
Then, go into your clone with `cd bootcamp`. Then, make a new branch with `git checkout -b yourUsername`. The option `-b` denotes that you are making a new branch called "[yourUsername]" and switching over to it.
Branching is a core aspect of Git and allows for committing and pushing to test code while not interfering with the stable build, found on the main branch, or others' builds. Here's a quick [guide on how it works](https://www.atlassian.com/git/tutorials/using-branches) and here's a [more substantive explanation](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging).

Now, create a file called "LOG" or open it if it already exists with `vim LOG` and write a sentence on something you're looking forward to in Michigan Neuroprosthetics at the end of the file. `vim` is a text editor, and can be shortened to `vi` in the command line. Instead of using `touch LOGG`, `vim` automatically creates the file since it does not exist. Once in the editor, you must press "i" for insert mode. Once you're done typing, press "esc," then ":wq" to write and quit (`w` for write and `q` for quit). This will return you to the command line.

Next, add, commit, and push your changes to your branch (yourUsername). Try not to make a habit of `git add *` because you can easily add unintended files to the project and complicate pushing.
```
git add LOG
git commit -m "This is a commit message"
git push origin yourUsername
```

Now, run `git log` and copy the log (see [Quick Tips](https://github.com/MichiganNeuroProsthetics/bootcamp#quick-tips) for information about copying). Then, edit "LOG" by pulling it up with `vi LOG` and following the same steps as before to modify the file. Append your copied Git log at the end of the file and exit. Add, commit, and push as earlier with any commit message you'd like.

Now, we will switch back to the main branch using either `git checkout master` or simply `git checkout`. Enter `git merge yourUsername` to merge the branch "yourUsername" with whatever branch you currently are on. Here, this will be the master branch. You will be unable to do so if new changes have come in since you have last pulled, so you must instead resolve the merge conflict. If you cloned the repository in the first session, you will experience such an issue. This is intentional and will give you practice in resolving them. 

First, use `git pull` to synchronize your remote with the head i.e. make sure you have the latest version. Now, you may try `git merge yourUsername` again. Merge conflcits can take a few forms, and theyre not uncommon in development, but they also doesn't have to be annoying if you know what you're doing. You may either have to go in the file and fix the changes yourself, or you may be presented with a dialog window. If you experience the latter, you may simply exit with "Ctrl+X" since there is no necessary message or otherwise edits to be made. For more information about merge conflicts, visit [this page](https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts). After resolving the conflict (don't delete others' messages!), enter `git commit` with any message you'd like. For merges outside of branching, you will need to push (`git push origin master`).

# Quick Tips
You can use `Ctrl+C` at any point in bash to cease an action, such as entering a password, pushing, or downloading if things aren't going well.
For WSL, this means that instead of using Ctrl+C to copy from the shell, you must use Ctrl+Insert or Ctrl+Shift+C for copying and Shift+Insert, Ctrl+Shift+V, or right-click for pasting.
