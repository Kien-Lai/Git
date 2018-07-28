# Git cheetsheet
### Operation:
![alt text](https://git-scm.com/figures/18333fig0106-tn.png)

### File Status LifeCycle:
![alt text](https://git-scm.com/figures/18333fig0201-tn.png)

### Show difference Staged and Unstaged:
``` git diff ```.
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