Rebase

It is imperative to understand the rebase, especially the risks behind.

We are using rebase to make history more clean, clear and ordered. This clearly means, we play with history of commits. Not in the very aggresive way, but still, history is kind of corrupted. This is huge risk when a huge team is working on the same repository.

Also rebase may lead to many conflicts.

Ok, it is time to explain the steps.

1 step is similar to previous activity - merge. We have master and branch.
Step2. When we perform the rebase operation, parent commit of the branch (the one from where we created branch) is moved to the HEAD of master, all differences between master and branch are merger and all commits on the branch are "copied/moved" (with all respective changes from master branch).
Step 3. The last thing is to do merge on master branch in order to move HEAD of master to the proper place.
Let's see it in the example.

System prepared second repository in rebase directory, and the state is exactly the same like in the merge repo, but without final merge.

cd ../rebase

git adog

We see that branches are not merged.

Let's switch to the second-branch (in case if we are not there, but we should) and do the rebase with master.

git checkout second-branch

git rebase master

git adog

Right now we can see two things

history looks totally different. Is 'flat' now and shuffled.
HEAD of master is in the wrong position.
If we leave it that way, believe, we generate a chaos, mess, and comments of hatred ;P So, let's switch to master and then move the marker by merge the branch to master.

git checkout master

git merge second-branch

git adog

Now we have HEAD in proper place and the history which, in fact, does not represent the past work order, but is more readable.

Pleace notice, the merge was created in 'fast-forward' mode. It means that no additional commit was created, but the HEAD marker was moved.
