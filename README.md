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
Go into your clone with `cd bootcamp`. Then, edit the file "LOG" with `vim LOG` and write a sentence on something you're looking forward to in Michigan Neuroprosthetics at the end of the file. `vim` is a text editor, and can be shortened to `vi` in the command line. Instead of using `touch LOG`, `vim` automatically creates the file since it does not exist. Once in the editor, you must press "i" for insert mode. Once you're done typing, press "esc," then ":wq" to write and quit (`w` for write and `q` for quit). This will return you to the command line.
Add the file to your stage with `git add LOG`, essentially selecting what files you want to be officially updated. After this, "commit" the change. Committing is the equivalent to pressing "Ctrl+S" for a local file, and it can be done so with `git commit LOG -m "[commit message]"`, filling in the commit message with a brief but insightful message on what you changed. Make sure to always be specific in your commit messages because reverting code happens incredibly often, so having a quick message on what was changed, what works, and what is experimental is critical. Fore more information, see [here](https://chris.beams.io/posts/git-commit/). Changes will not be seen until you "push" to a branch; however, we will NOT be pushing until later.

Make a new branch with `git checkout -b yourFavoriteFood_yourFirstName` (e.g. `git checkout -b watermelon_maxton`). The option `-b` denotes that you are making a new branch called "[yourFavoriteFood]" and switching over to it.
Branching is a core aspect of Git and allows for committing and pushing to test code while not interfering with the stable build, found on the main branch, or others' builds. Here's a quick [guide on how it works](https://www.atlassian.com/git/tutorials/using-branches) and here's a [more substantive explanation](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging).

As before, enter into the file with `vi LOG` and this time write the answer to the following question: If you could have cubic meter of anything, what would it be? Next, add and commit your changes to your branch (yourFavoriteFood_yourFirstName). Try not to make a habit of `git add *` because you can easily add unintended files, such as IDE files, to the project and complicate pushing.

Now, we will switch back to the main branch using either `git checkout master` or simply `git checkout`. Make one more change to the LOG, adding your favorite comic book onomatopoeia e.g. BAM! FTHAP! SKLORSH! Notice that your edit made to the other branch does not appear here, only your first edit. Try `git merge yourFavoriteFood_yourFirstName` to merge said branch with your current branch, "master." You will receive at least one error in doing so, asking you to pull before pushing and to potentially commit your changes. Use, use `git pull` to synchronize your remote with the head i.e. make sure you have the latest version. If you have not added and committed, this will come as a reminder for you to do so. If there are additional pushes since you last pulled, you will need to add, commit, pull then merge before you can push. Enter `git merge yourFavoriteFood_yourFirstName` again after committing changes to attempt to merge again. You will be unable to do so since you made additional changes to LOG on the main branch as well as your other branch.

Merge conflcits can take a few forms, and theyre not uncommon in development, but they also doesn't have to be annoying if you know what you're doing. You may either have to go in the file and fix the changes yourself, or you may be presented with a dialog window. If you experience the latter, you may simply exit with "Ctrl+X" since there is no necessary message or otherwise edits to be made. For more information about merge conflicts, visit [this page](https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts). In all likelihood, you will need to enter into LOG again with `vi LOG` and decide which edit you would like to go with if not a combination of the two. It will look something like this
```
<<<<<<< HEAD
Minecraft command block
THUD!
=======
I'm looking forward to working with other universities and setting up additional assembly locations!
>>>>>>> yourFavoriteFood_yourFirstName
```
In most IDEs or editors, you can click which one you want to accept. Otherwise, you will have to manually remove the undesired one along with the angle bracket and equals lines.

After resolving the conflict (don't delete others' messages!), try `git push -u origin master` with any message you'd like. If you are not added to the repository, you will likely receive errors in pushing. You will need to generate a pull request otherwise, and [more information can be found here](https://docs.github.com/en/desktop/contributing-and-collaborating-using-github-desktop/creating-an-issue-or-pull-request).

After your pull request has been approved, run `git log` and copy the log (see [Quick Tips](https://github.com/MichiganNeuroProsthetics/bootcamp#quick-tips) for information about copying). Then, edit "LOG" by pulling it up with `vi LOG` and following the same steps as before to modify the file. Append your copied Git log at the end of the file and exit. Add, commit, and push as earlier with any commit message you'd like.

# Quick Tips
You can use `Ctrl+C` at any point in bash to cease an action, such as entering a password, pushing, or downloading if things aren't going well.
For WSL, this means that instead of using Ctrl+C to copy from the shell, you must use Ctrl+Insert or Ctrl+Shift+C for copying and Shift+Insert, Ctrl+Shift+V, or right-click for pasting.

# Additional Notes
If you own a repository or are an editor, you would usually push changes as follows.
```
git add fileName1.ino fileName2.txt fileName3.* filename4.csv
git commit -m "This is a commit message"
git push -u origin branchName
```
