# smads18's git hand-in

mail: smads18@student.sdu.dk

This can also be read on github: 



## Execise 1

Before the exercise...

After executing `git log --oneline --graph --decorate --all` the output was,

<code>

    * aaf1b44 (HEAD -> master) add the word, and done with 321
    * c09c6c1 add prime directive to 321
    * 8d140bf most relevant!
    * 272dc52 Add more relevancy
    * 497caae Working on 321
    * c24f1ec initial file

</code>

### Task

1. _Squash_ the five relevant commits into one, with the commit message of "close #321"

This was done with the following command,

`git rebase -i HEAD~5`


Then I picked the first commit and squashed the next four. Then changed the commit message to 'close #321'.

2. How does `git log` look now?

<code>

    commit 3f0135a831efaf3f1336801e698c0779fd8b7df4 (HEAD -> master)
    Author: simonmdsn <simonmdsn@gmail.com>
    Date:   Sat Aug 8 18:07:37 2020 +0200

        close #321

    commit c24f1ec4dfffaae9fb983bf644012fba779c1bc3
    Author: simonmdsn <simonmdsn@gmail.com>
    Date:   Sat Aug 8 18:07:37 2020 +0200

        initial file

</code>

After completing the exercise `git log --oneline --graph --decorate --all` output was,

<code>

    * 3f0135a (HEAD -> master) close #321
    * c24f1ec initial file

</code>



## Execise 2

Before the exercise...

After executing `git log --oneline --graph --decorate --all` the output was,

<code>

    * 86e294d (master) Implement second part of feature
    * b32c052 Fix bug
    | * 8115845 (HEAD -> new-feature) Implement first part of feature
    |/
    * daf7238 Initial commit

</code>

### Task

1. Move the faulty commit from the `master` branch to the `new-feature` branch.

The following sequence of commands were executed,

<code>

    git checkout new-feature
    git cherry-pick 86e294d
    git add myapp.txt
    git commit
    git checkout master
    git reset --hard HEAD~1

</code>

2. Copy the bugfix to your feature branch as well

The following command was executed,

<code>

    git cherry-pick b32c052

</code>

3. The commit containing the second part of the feature makes master fail in the CI and you need to take that change out. How would you do that? Answer should provide both the command and the reasoning behind it.

I would use `git rebase -i HEAD~n`, where n is representing the 'Implement second part of feature' commit. This will rebase just before the commit you want to change. It will then 'replay' all other commits into the log.


After completing the exercise `git log --oneline --graph --decorate --all` output was,

<code>

    * 7688c89 (HEAD -> new-feature) Fix bug
    * 119d81a Implement second part of feature
    * 8115845 Implement first part of feature
    | * b32c052 (master) Fix bug
    |/
    * daf7238 Initial commit

</code>



## Execise 3

Before the exercise...

After executing `git log --oneline --graph --decorate --all` the output was,

<code>

    * 9d235a1 (feature) Change greeting to uppercase
    | * 6113184 (HEAD -> master) Add readme
    |/
    * 90b0da5 Add content to greeting.txt
    * 9fad4a2 Add file greeting.txt

</code>

### Task

* Show the commands in order to achieve this position of commits.

The following sequence of commands were executed,

<code>

    git checkout feature
    git rebase master

</code>

* Why does the commit with message "Change greeting to uppercase" change sha, when the others do not?

sha's hash is dependent on its previously commit(s). We changed it's parent with rebase.

After completing the exercise `git log --oneline --graph --decorate --all` output was,

<code>

    * f8ba4f7 (HEAD -> feature) Change greeting to uppercase
    * 6113184 (master) Add readme
    * 90b0da5 Add content to greeting.txt
    * 9fad4a2 Add file greeting.txt

</code>



## Execise 4

Before the exercise...

After executing `git log --oneline --graph --decorate --all` the output was,

<code>

    * 0976988 (HEAD -> master) Add bad content to afile.txt
    * cb2e956 first commit  

</code>

### Task

* In words, describe what you are seeing in the repository. Use the git terminology when applicable.

There are 3 files:
    .gitgnore
    afile.txt
    bfile.txt

The .gitignore file specifies what files should be ignored.
The afile.txt is being tracked and committed at 0976988. It has then AFTER been modified, but the changes has not been commited.  
The bfile.txt is not tracked in this repo. 

Show the list of commands you need to do the following (in the given order).

* remove the work in progress using git.

`git checkout -- afile.txt`

* remove the staged change

`git reset HEAD afile.txt`

* make master go back to the commit before the bad commit

`git reset --soft HEAD~1`

* does git track bfile.txt? Reason your answer.

No. In the .gitignore file it is specified to ignore exactly bfile.txt.

After completing the exercise `git log --oneline --graph --decorate --all` output was,

<code>

    * cb2e956 (HEAD -> master) first commit

</code>



## Execise 5

Before the exercise...

After executing `git log --oneline --graph --decorate --all` the output was,

<code>

    * 1d82904 (HEAD) E
    * 8ec7870 (master) D
    * 95a68af C
    * 5320156 B
    * 1133c07 A

</code>

### Task

* In words, describe what you are seeing in the repository. Use the git terminology when applicable.

We have five commits who have been commited one after the other until commit 'D', where checkout to HEAD~3 has been made and then commit 'E' but then a rebase has been made, which is why HEAD is detached from 1133c07 (first commit).


Show the list of commands you need to do the following (in the given order).

* Move to `master`

`git checkout master`

* Make a branch  called `the-beginning` that is made from the first commit with message `A`

`git branch the-beginning HEAD~4`

* Show how you would find the commit with the message `E` and make a branch called `dangling` on that commit.

`git branch dangling 1d82904`

After completing the exercise `git log --oneline --graph --decorate --all` output was,

<code>

    * 1d82904 (HEAD, dangling) E
    * 8ec7870 (master) D
    * 95a68af C
    * 5320156 B
    * 1133c07 (the-beginning) A

</code>