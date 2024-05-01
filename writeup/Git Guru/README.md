In Git Guru challenge we have been given a zip file named git_guru.zip .


After unzipping it we get a directory named repo. If we cd into the directory we can see that's a git repo.

```
cd repo
```
which currently contains a directory named .git, three txt file named iamtheflag.txt, noiamtheflag.txt, README.md

In README.md it says that the flag is broken into multiple parts and have been scattered.

If we use  ``` git log ```  we can see there are 9 commits the the master branch if we keep looking in those commits using 
```
git show <commit-ID>
```
 we eventually get the 1st part of the flag in the 4th and 5th commit.

Now if we use ```git branch -a``` we see there are 5 brances including master
```
* master
  remotes/origin/dev
  remotes/origin/exploits
  remotes/origin/master
  remotes/origin/research
```


if we keep looking into these too we'll notice there are 12 commits in remotes/origin/research, which is higher than the rest of the brances.
If we show the 10th commit we'll get the 2nd part of the flag.
```
git checkout remotes/origin/research # for canging branch

git show <commit-ID> # to show the commit details
```
The 3rd and last part of the flag is in a tag

if we use ```git tag``` we see that there are 9 tags
```
flag1
flag2
flag3
flag4
flag5
flag6
flag7
flag8
flag9
```

if we keep looking into these too we'll eventually get the last part in the flag5 tag
```
git show <tag-name> # for showing the tag details
