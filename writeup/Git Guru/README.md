<p align="center"><a href="https://git.io/typing-svg"><img src="https://readme-typing-svg.herokuapp.com?font=Pixelify+Sans&size=25&pause=1000&color=0CF730&center=true&random=false&width=435&lines=Official+writeup+of+Git+Guru" alt="Typing SVG" /></a></p>


In Git Guru challenge we have been given a zip file named git_guru.zip .


After unzipping it we get a directory named git_guru. If we cd into the directory we can see that's a git repo.

```
cd repo
```
which currently contains a directory named .git, three txt file named iamtheflag.txt, noiamtheflag.txt, README.md

In README.md it says that the flag is broken into multiple parts and have been scattered.

If we use  ``` git log ```  we can see there are 9 commits the master branch if we keep looking in those commits using 

> ```git show <commit-ID>```    # to show the commit details

 we eventually get the 1st part of the flag in the 4th and 5th commit.
```
git show 425bcc8cdf39d1c0096b1f538434ec63be3c7914
```
```
git show e5c4dba20ad103c0b1b20c3dec1f8a51252af7c2
```
Now if we use ```git branch -a``` we see there are 5 brances including master
```
* master
  remotes/origin/dev
  remotes/origin/exploits
  remotes/origin/master
  remotes/origin/research
```


if we keep looking into these too we'll notice there are 12 commits in remotes/origin/research branch, which is higher than the rest of the brances.
If we show the 10th commit we'll get the 2nd part of the flag.
```
git checkout remotes/origin/research # for changing branch
```
You might see some error saying some file might get overwritten by checkout so commit the files first
```
error: Your local changes to the following files would be overwritten by checkout:
        noiamtheflag.txt
Please commit your changes or stash them before you switch branches.
Aborting
```
So just add the files that was shown in the error and do the commit, for example:
```
git add noiamtheflag.txt
```
```
git commit -m "This is message for commit ^-^"
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

> ```git show <tag-name>```   # for showing the tag details
```
git show flag5
```
