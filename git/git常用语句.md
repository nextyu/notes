# git常用语句

```bash
mdkir notes

cd notes

git init

-- 针对notes这个文件夹设置name和email

git config user.name "nextyu"

git config user.email "imzaobai@gmail.com"

touch README.md

git add .

git commit -m 'first commit'

-- 关联远程分支

git remote add origin git@github.com:nextyu/notes.git

git push -u origin master



-- 修改 内容

git add .

git commit -m 'message'

git push origin master
```