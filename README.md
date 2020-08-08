# Git exercises

To make each assignment, run the `setup.sh` file and examine the git repository in the `exercise` folder.

## Hand in requirements

To hand in, Zip the entire folder of all exercises.

In the root of the hand-in folder, make a file next to README.md called HANDIN.txt.

You need to provide the git commands you need to solve the task, as well as a copy of the following command *BEFORE you start AND AFTER you are done solving* the exercise from each repository:

`git log --oneline --graph --decorate --all`

If you are not able to solve the task, provide a description of how you thought you would solve the task, and where you encountered problems.

## 1

The git commit history looks like a developers internal "I gotta save this" work. Not suited for public.
All work belongs to a task called "#321"

### Task

1. _Squash_ the five relevant commits into one, with the commit message of "close #321"
1. How does `git log` look now?

## 2

You develop a new feature on the branch `new-feature`. You have already
implemented the first part of a feature, when you are notified of a critical
bug that has to be fixed right away on the `master` branch.

After the bug fix, you continue to work on the new feature. After you committed the second part of the feature, you realize that you have done your commit on the `master` branch instead of the feature branch.

### Task

1. Move the faulty commit from the `master` branch to the `new-feature` branch.
1. Copy the bugfix to your feature branch as well
1. The commit containing the second part of the feature makes master fail in the CI and you need to take that change out. How would you do that? Answer should provide both the command and the reasoning behind it.

## 3

You have developed a new feature, and want the latest changes from master into your branch:

```bash
* 1f37b43 (HEAD -> master) Add readme
| * a824913 (feature) Change greeting to uppercase
|/ 
* b84f28f Add content to greeting.txt
* efb74a6 Add file greeting.txt
```

Instead of just merging the commit, you like a straight line of commits like the example below

```bash
* 47558e0 (HEAD -> feature) Change greeting to uppercase
* 1f37b43 (master) Add readme
* b84f28f Add content to greeting.txt
* efb74a6 Add file greeting.txt
```

### Task

* Show the commands in order to achieve this position of commits.
* Why does the commit with message "Change greeting to uppercase" change sha, when the others do not?

## 4

Look at the git graph and status of the created repository to find out the state.

### Task

* In words, describe what you are seeing in the repository. Use the git terminology when applicable.

Show the list of commands you need to do the following (in the given order).

* remove the work in progress using git.
* remove the staged change
* make master go back to the commit before the bad commit
* does git track bfile.txt? Reason your answer.

## 5

### Task

* In words, describe what you are seeing in the repository. Use the git terminology when applicable.

Show the list of commands you need to do the following (in the given order).

* Move to `master`
* Make a branch  called `the-beginning` that is made from the first commit with message `A`
* Show how you would find the commit with the message `E` and make a branch called `dangling` on that commit.
