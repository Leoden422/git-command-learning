### 

#### 1. **在远端创建空的 GitHub 仓库**

- 登录 GitHub → New repository → 填写相关信息 → Create repository。

#### 2. **本地操作**

```bash
# 0.进入powershell
	win+R 打开窗口 输入：powershell
# 1. 创建本地目录并初始化仓库
	mkdir my-project && cd my-project#创建新文件并且进入新文件
	git init#初始化仓库，把文件夹变为本地仓库
# 2. 添加文件并提交
	#在文件夹创建文件并且编辑内容保存
# 3.返回powershell执行以下命令
	git add .
	git commit -m "初始化项目"
# 4.如果再次修改
	git add .
	git commit --amend #把这次提交和最后一次提交合并，少一次记录
# 5. 关联远程仓库（替换为你的仓库URL）
	git remote add origin https://github.com/用户名/仓库名.git
# 6. 如果 GitHub 仓库已存在文件（如 README、LICENSE），推送会冲突，需先合并：
     #拉取远程更新并合并（保留双方内容），两个仓库都是初始化允许合并
	git pull origin main --allow-unrelated-histories
# 7. 解决可能的冲突（编辑冲突文件后）
	git add .
	git commit -amend 
# 8. 推送至远程（首次需指定分支）
	#若本地分支是master
	git push -u origin master:main
	# 若本地分支是main
	git push -u origin main
```



### **三、强制覆盖远端（谨慎使用）**

若远端仓库内容不重要，可强制覆盖：

```bash
git push -f -u origin master:main  # 危险！会删除远端不匹配的内容
```

### **四、统一分支名（避免混淆）**

若本地分支是 `master`，而 GitHub 默认是 `main`，建议统一：

```bash
git branch -m master main  # 重命名本地分支
git push -u origin main    # 推送并关联main分支
```

### **五、后续常规操作**

```bash
# 修改文件后
git add .
git commit -m "更新说明"
git push  # 直接推送（已关联远程分支）
```

### **关键注意事项**

1. **避免冲突**：创建 GitHub 仓库时不要初始化，保持为空。

2. 中文文件名

   ：若显示乱码，执行：

   ```bash
   git config --global core.quotepath false
   ```