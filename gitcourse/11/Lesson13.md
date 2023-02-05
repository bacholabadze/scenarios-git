Better approach
If you work on huge amount of changes, the good practice is to merge the master to your branch before merge to master.

It doesn't help to solve conflicts, but conflict will be on your branch, not master. What is definitelly more confortable for everyone.

Ok, we need to go to the new repo

cd ~/merge3

Ok, we are on the branch, let's do the merge.

git branch

git merge master --no-edit

Yes, we have conflict, but master is still clean.

sed -i '8d' testfile-02 && sed -i '6d' testfile-02 && sed -i '3d' testfile-02 && cat testfile-02

Worth noticing, the center of the conflict (=======) lies in different place than in the example in conflicts lesson.

Now, like last time, we need to stage and commit file.

git status

git add testfile-02

git commit -a -m "merge master to newbranch"

git adog

Ok, we fixed problems, and we are ready to merge our changes on master.

git checkout master

git merge newbranch --no-edit

git adog

So, we completed our merge.

git branch -d newbranch && git branch
