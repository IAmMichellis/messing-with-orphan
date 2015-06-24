# messing with git checkout --orphan

yeaaaaaah that was cool. So, for my future reference, what I wanted:

I had a repo I was trying to setup for a workshop. It was disorganized but useful to me, so I wanted the code, but I wanted to rewrite the code, from scratch, in a very organized way for the attendees.

Solution:

1. git checkout --orphan newMaster:
Creates branch called "newMaster" with no revision history. First commit on this branch will become commit 0.

2. (on newMaster) git rm -rf .:
Nukes everything. Now it's a branch with no history and no files: a clean slate.

3. (Do some stuff and commit to newMaster. This will be commit 0)

4. git push origin newMaster

5. git branch -m master oldMaster: rename master to oldMaster

6. git push origin oldMaster
This is current master, shortly old master. This will be the only reference to it.

7. git branch -m newMaster master
locally rename newMaster to master

8. git push -f origin master
nuke remote master with your newMaster.

And all is well. Obviously this is a collaboration nightmare.
