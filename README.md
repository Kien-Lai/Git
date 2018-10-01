# Git cheetsheet
> # Operation:
![alt text](https://git-scm.com/figures/18333fig0106-tn.png)

### File Status LifeCycle:
![alt text](https://git-scm.com/figures/18333fig0201-tn.png)

### Show difference Staged and Unstaged:
``` git diff ```. (just use for file that isnot committed)
Giả sử bạn sửa và stage tập tin README lại một lần nữa, sau đó là sửa tập benchmarks.rb mà không stage nó. Nếu bạn chạy lệnh status, bạn sẽ lại nhìn thấy tương tự như sau:
```git
$ git status
On branch master
Changes to be committed:
(use "git reset HEAD <file>..." to unstage)
new file:   README
Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
modified:   benchmarks.rb 
```


### Show difference between file staged and file unmodifed"
Show sự thay đổi giữa file đã được git add . và file đó khi chưa modified
```git
git diff --cached
```

### Recover
+ To override last commit use: 
```git
git commit --amend
```

+ To Recovery a file to last commit use:
```git
git checkout "filename"
```
warning: this command cannot be recovery, you will lost all data you modified

+ To unstage a file to last commit use:
```git
git reset HEAD <file>
```
### Git tag
+ List all tag your repository has
```git
git tag
```
+ add new tag
```git
git tag -a v1.0 -m"version 1.0"
```

### Git log
+ Log all commit
```git 
git log
```
+ Log lass commit
```git
git log -1 HEAD
```
> # Branch
+ A commit look like image below:
![alt text](https://git-scm.com/figures/18333fig0301-tn.png) 
+ When you add a commit, commit tree is going to look like this:
![alt text](https://git-scm.com/figures/18333fig0302-tn.png)

+ List all branches 
```git
git branch
```
+ List all branches which havenot merged
```git 
git branch --no-merged
```

+ Delete a branch
```git
git branch -d <branch_name>
```
note: if branch you want to delete isnot an ancestor of your current HEAD, git will warning and if you want to continute, use command : git branch -D <branch_name>

+ Create local branch and tracking with origin branch
```git
git checkout -b <localbranch> origin/<originbranch>
```

+ Tracking local branch with remote branch
```git
git checkout --track origin/<namebranch>
```

+ Delete a remote branch
```git
git push origin :<branch_name>
```

+ Rebase
current commit tree:
![alt text](https://git-scm.com/figures/18333fig0327-tn.png)
if you use merge command, commit tree will be:
![alt text](https://git-scm.com/figures/18333fig0328-tn.png)
Tuy nhiên, còn có một cách khác: bạn có thể sử dụng bản vá của thay đổi được đưa ra ở C3 và áp dụng nó lên trên C4. Trong Git, đây được gọi là rebasing. Bằng cách sử dụng lệnh rebase, bạn có thể sử dụng tất cả các thay đổi được commit ở một nhánh và "chạy lại" (replay) chúng trên một nhánh khác.
Nó thực hiện bằng cách đi tới commit cha chung của hai nhánh (nhánh bạn đang làm việc và nhánh bạn đang muốn rebase), tìm sự khác biệt trong mỗi commit của nhánh mà bạn đang làm việc, lưu lại các thay đổi đó vào một tập tin tạm thời, khôi phục lại nhánh hiện tại về cùng một commit với nhánh bạn đang rebase, và cuối cùng áp dụng lần lượt các thay đổi. Hình 3-29 minh họa toàn bộ quá trình này.
![alt text](https://git-scm.com/figures/18333fig0329-tn.png)
Đến lúc này, bạn có thể quay lại nhánh master và thực hiện fast-forward merge (xem Hình 3-30).
![alt text](https://git-scm.com/figures/18333fig0330-tn.png)    

+ discard all unstaged:
- git checkout -- .
- For a specific file use:
git checkout path/to/file/to/revert
- Another quicker way is:
git stash save --keep-index
Include --include-untracked if you'd want to be thorough about it.

delete a cached file:
git remote --cache :file_name;

git remote set-url origin https://github.com/USERNAME/REPOSITORY.git

