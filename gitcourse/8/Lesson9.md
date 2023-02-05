Conflict!
We will create a conflict in unusual but not uncommon way. In the background the system did some work, commits, etc. Now our goal is to go back two commits with revert. Unfortunately, our last two commits are about the same file.

Let's go to our repo cd test

How the history looks now?

git log --oneline

And for the curiosity, what is in testfile-02 ?

cat testfile-02

Let's try to do revert.

clear && git revert --no-edit HEAD~1

Ouch...

CONFLICT (content): Merge conflict in testfile-02
error: could not revert XXXXXXX... my new feature
Let's see what we have in file

cat testfile-02

Thank you git. You were supposed to destroy mess in the universe, not create one!

But wait... Let's look closely what happened.

How the revert works? It removes changes from selected commit, not from all changes!. Now things should be more clear, right?

change1 commit
change2 commit
revert to change1
That means, we have change2 unattended!

<<<<<<< HEAD
This is my important change
=======
>>>>>>> parent of XXXX... my new feature
Here is our conflict.

<<<<<< - this is what we have in current branch

====== = center of our conflict

>>>>>> - this wants to be merged / added. In our case this part is empty (as it should be).

How to solve it? The simplest will be... talk with developers who did the changes which we are reverting, first. Find common solution. And then use vim and make appropriate changes.

Normally you should use vim , and remove lines from 2 to 5 . But here we do:

sed -i '2,5d' testfile-02

We removed mentioned lines. Now the file looks like we want.

cat testfile-02

Please notice, this example is extremely simple :)

The last thing to do is to add and commit the file again. Please look carefully on comments after

clear && git status

Ok, let's do the work.

git add testfile-02

git status

clear && git commit testfile-02 -m "fixed conflict"

git status
