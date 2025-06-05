### **一、基础环境配置**

| 命令                                     | 作用           | 示例                                                  |
| ---------------------------------------- | -------------- | ----------------------------------------------------- |
| `git --version`                          | 查看 Git 版本  | `git --version` → `git version 2.39.2`                |
| `git config --global user.name "用户名"` | 设置全局用户名 | `git config --global user.name "Doubao"`              |
| `git config --global user.email "邮箱"`  | 设置全局邮箱   | `git config --global user.email "doubao@example.com"` |
| `git config --list`                      | 查看配置信息   | `git config --list`                                   |

### **二、仓库操作**

| 命令              | 作用               | 流程                                                   |
| ----------------- | ------------------ | ------------------------------------------------------ |
| `git clone <url>` | 克隆远程仓库到本地 | `git clone https://github.com/xxx/repo.git`            |
| `git init`        | 初始化本地仓库     | `git init my-project` → 在当前目录创建`my-project`仓库 |

### **三、文件操作**

| 命令                            | 作用                            | 备注                      |
| ------------------------------- | ------------------------------- | ------------------------- |
| `git status`                    | 查看文件状态（工作区 / 暂存区） | 日常必用！                |
| `git add <文件名>`              | 将文件从工作区添加到暂存区      | `git add README.md`       |
| `git add .`                     | 添加所有改动文件                | 包含新增文件和修改的文件  |
| `git restore <文件名>`          | 丢弃工作区的修改                | `git restore src/main.py` |
| `git restore --staged <文件名>` | 将文件从暂存区退回工作区        | 取消`git add`的效果       |
| `git rm <文件名>`               | 删除文件并提交到暂存区          | `git rm old_file.txt`     |
| `git mv <原文件名> <新文件名>`  | 重命名文件并提交到暂存区        | `git mv a.txt b.txt`      |

### **四、提交操作**

| 命令                    | 作用                             | 最佳实践                            |
| ----------------------- | -------------------------------- | ----------------------------------- |
| `git commit -m "描述"`  | 提交暂存区的内容到本地仓库       | `git commit -m "修复登录bug"`       |
| `git commit -am "描述"` | 直接提交工作区中**已跟踪**的文件 | 省略`git add`步骤，但不处理新增文件 |
| `git commit --amend`    | 修改上一次提交的信息或内容       | 用于修正最近一次提交的错误          |

### **五、分支操作**

| 命令                       | 作用                        | 流程示例                            |
| -------------------------- | --------------------------- | ----------------------------------- |
| `git branch`               | 查看本地分支                | `git branch` → 显示当前所有本地分支 |
| `git branch -a`            | 查看所有分支（本地 + 远程） | 红色为远程分支，绿色为本地分支      |
| `git branch <分支名>`      | 创建新分支                  | `git branch feature/login`          |
| `git checkout <分支名>`    | 切换分支                    | `git checkout feature/login`        |
| `git checkout -b <分支名>` | 创建并切换到新分支          | `git checkout -b feature/login`     |
| `git branch -d <分支名>`   | 删除已合并的分支            | `git branch -d feature/login`       |
| `git branch -D <分支名>`   | 强制删除未合并的分支        | 谨慎使用！会丢失未合并的修改        |
| git checkout -b 分支名     | 创建并切换切换到新分支      |                                     |

### **六、同步远程仓库**

| 命令                                | 作用                         | 注意事项                                |
| ----------------------------------- | ---------------------------- | --------------------------------------- |
| `git pull`                          | 拉取远程分支并合并到当前分支 | 可能产生合并提交                        |
| `git pull --rebase`                 | 拉取远程分支并变基到当前分支 | 保持提交历史线性（推荐）                |
| `git push`                          | 推送本地分支到远程           | `git push origin main`                  |
| `git push -u origin <分支名>`       | 首次推送并关联远程分支       | `-u`参数相当于`--set-upstream`          |
| `git push origin --delete <分支名>` | 删除远程分支                 | `git push origin --delete feature/test` |

### **七、合并与变基**

| 命令                         | 作用                       | 场景                                           |
| ---------------------------- | -------------------------- | ---------------------------------------------- |
| `git merge <分支名>`         | 合并指定分支到当前分支     | `git checkout main` → `git merge feature`      |
| `git merge --no-ff <分支名>` | 非快速合并（保留分支历史） | 强制生成合并提交节点                           |
| `git rebase <分支名>`        | 将当前分支变基到指定分支   | `git rebase main` → 将当前分支 "接到"main 末尾 |
| `git rebase -i <分支名>`     | 交互式变基（修改提交历史） | 可合并、删除、修改提交                         |

### **八、撤销与回滚**

| 命令                        | 作用                               | 示例                                         |
| --------------------------- | ---------------------------------- | -------------------------------------------- |
| `git reset --hard <commit>` | 彻底回退到指定提交（丢失后续修改） | `git reset --hard HEAD~1` → 回退到上一个提交 |
| `git revert <commit>`       | 通过创建新提交撤销指定提交         | `git revert HEAD` → 撤销最近一次提交         |
| `git stash`                 | 暂存当前工作区的修改               | `git stash` → 保存修改到栈                   |
| `git stash list`            | 查看暂存记录                       | `git stash list` → 显示所有 stash            |
| `git stash pop`             | 恢复最近一次暂存并删除记录         | `git stash pop` → 恢复并清理                 |
| `git stash apply`           | 恢复暂存但不删除记录               | `git stash apply stash@{0}`                  |

### **九、标签操作**

| 命令                                | 作用               | 备注                              |
| ----------------------------------- | ------------------ | --------------------------------- |
| `git tag <标签名>`                  | 创建轻量标签       | `git tag v1.0.0`                  |
| `git tag -a <标签名> -m "描述"`     | 创建带注释的标签   | `git tag -a v1.0.0 -m "正式发布"` |
| `git tag`                           | 查看所有标签       | `git tag` → 列出所有标签          |
| `git push origin <标签名>`          | 推送标签到远程     | `git push origin v1.0.0`          |
| `git push origin --tags`            | 推送所有标签到远程 | `git push origin --tags`          |
| `git tag -d <标签名>`               | 删除本地标签       | `git tag -d v1.0.0`               |
| `git push origin --delete <标签名>` | 删除远程标签       | `git push origin --delete v1.0.0` |

### **十、查询与比较**

| 命令                       | 作用                       | 示例                                                  |
| -------------------------- | -------------------------- | ----------------------------------------------------- |
| `git log`                  | 查看提交历史               | `git log` → 显示所有提交记录                          |
| `git log --oneline`        | 简洁模式查看历史           | `git log --oneline` → 单行显示每个提交                |
| `git diff`                 | 查看工作区与暂存区的差异   | `git diff` → 显示未`add`的修改                        |
| `git diff --staged`        | 查看暂存区与最新提交的差异 | `git diff --staged` → 显示已`add`但未`commit`的修改   |
| `git diff <分支1> <分支2>` | 比较两个分支的差异         | `git diff main feature` → 显示 main 和 feature 的差异 |

### **十一、高级技巧**

| 命令                       | 作用                       | 示例                                                    |
| -------------------------- | -------------------------- | ------------------------------------------------------- |
| `git cherry-pick <commit>` | 选择特定提交应用到当前分支 | `git cherry-pick abc123` → 将提交`abc123`应用到当前分支 |
| `git bisect`               | 二分查找定位问题提交       | `git bisect start` → 开始查找                           |
| `git blame <文件名>`       | 查看文件每行的最后修改者   | `git blame README.md` → 显示每行的作者和提交信息        |

### **Git 工作流程图**

```plaintext
远程仓库 (origin/main)
   ↑    ↓
   push pull
   ↑    ↓
本地仓库 (main)
   ↑    ↓
  commit add
   ↑    ↓
暂存区 (staging)
   ↑    ↓
  add  restore --staged
   ↑    ↓
工作区 (working directory)
```

### **最佳实践建议**

1. **日常开发流程**：
   `git pull --rebase` → 开发 → `git add` → `git commit` → `git push`
2. **分支管理**：
   - 主分支（`main`/`master`）：仅用于发布稳定版本
   - 开发分支（`develop`）：集成所有功能
   - 功能分支（`feature/*`）：开发新功能
   - 修复分支（`fix/*`）：紧急修复 bug
3. **提交规范**：
   使用有意义的提交信息，例如：
   `git commit -m "feat: 添加用户登录功能"`
   `git commit -m "fix: 修复购物车计算错误"`
4. **避免冲突**：
   频繁`git pull --rebase`保持本地分支最新，减少合并冲突。
5. **慎用强制操作**：
   `git reset --hard`、`git push -f`等命令可能丢失数据，操作前务必确认。

掌握这些命令，你将能够应对 90% 以上的日常开发场景。Git 的核心是 "提交 - 分支 - 合并" 的工作流，建议通过实际项目反复练习，形成肌肉记忆！