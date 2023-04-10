# FZU-flying-book
[欢迎来到福州大学飞跃手册！](https://fzu-fly.online)


## 提交方法：

git clone git@github.com:MIECer/FZU-flying-book.git 到本地

修改 ./docs 文件夹中的相关的.md 文件

### 下面分为两个过程

备份文件过程
<pre>
git add .
git commit -m"comment" # comment = comment
git push origin main
<pre/>

部署过程
<pre>
mkdocs gh-deploy --force
<pre/>

