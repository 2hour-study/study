好的，下面是带有示例的 Git 常用命令及其详细说明：

### 1. Git 配置
- **`git config --global user.name "Your Name"`**
  - 设置全局用户名，用于标识提交者。
  - **示例**: 
    ```bash
    git config --global user.name "Alice"
    ```

- **`git config --global user.email "you@example.com"`**
  - 设置全局用户邮箱，用于标识提交者。
  - **示例**: 
    ```bash
    git config --global user.email "alice@example.com"
    ```

- **`git config --global core.editor "your-editor"`**
  - 设置默认文本编辑器。
  - **示例**: 
    ```bash
    git config --global core.editor "vim"
    ```

### 2. 创建和克隆仓库
- **`git init`**
  - 在当前目录初始化一个新的 Git 仓库。
  - **示例**: 
    ```bash
    mkdir my-project
    cd my-project
    git init
    ```

- **`git clone <repository>`**
  - 克隆远程仓库到本地。
  - **示例**: 
    ```bash
    git clone https://github.com/user/repo.git
    ```

### 3. 文件状态
- **`git status`**
  - 显示当前工作目录和暂存区的状态。
  - **示例**: 
    ```bash
    git status
    ```

- **`git add <file>`**
  - 将指定文件添加到暂存区。
  - **示例**: 
    ```bash
    git add file.txt
    ```

- **`git add .`**
  - 将当前目录下的所有更改的文件添加到暂存区。
  - **示例**: 
    ```bash
    git add .
    ```

- **`git reset <file>`**
  - 从暂存区中移除指定文件，但保留工作目录中的更改。
  - **示例**: 
    ```bash
    git reset file.txt
    ```

### 4. 提交更改
- **`git commit -m "commit message"`**
  - 提交暂存区的更改，并附上提交信息。
  - **示例**: 
    ```bash
    git commit -m "Add new feature"
    ```

- **`git commit -a -m "commit message"`**
  - 自动将所有已跟踪文件的更改提交（不包括新文件）。
  - **示例**: 
    ```bash
    git commit -a -m "Fix bugs"
    ```

### 5. 查看历史
- **`git log`**
  - 查看提交历史。
  - **示例**: 
    ```bash
    git log
    ```

- **`git log --oneline`**
  - 以简洁的格式查看提交历史。
  - **示例**: 
    ```bash
    git log --oneline
    ```

- **`git diff`**
  - 查看未暂存的文件和最后一次提交之间的差异。
  - **示例**: 
    ```bash
    git diff
    ```

- **`git diff --cached`**
  - 查看暂存区与最后一次提交之间的差异。
  - **示例**: 
    ```bash
    git diff --cached
    ```

### 6. 分支管理
- **`git branch`**
  - 列出所有本地分支。
  - **示例**: 
    ```bash
    git branch
    ```

- **`git branch <branch-name>`**
  - 创建一个新分支。
  - **示例**: 
    ```bash
    git branch feature-branch
    ```

- **`git checkout <branch-name>`**
  - 切换到指定分支。
  - **示例**: 
    ```bash
    git checkout feature-branch
    ```

- **`git checkout -b <branch-name>`**
  - 创建并切换到新分支。
  - **示例**: 
    ```bash
    git checkout -b new-feature
    ```

- **`git merge <branch-name>`**
  - 将指定分支合并到当前分支。
  - **示例**: 
    ```bash
    git merge feature-branch
    ```

### 7. 远程操作
- **`git remote -v`**
  - 查看所有远程仓库及其地址。
  - **示例**: 
    ```bash
    git remote -v
    ```

- **`git remote add <name> <url>`**
  - 添加一个新的远程仓库。
  - **示例**: 
    ```bash
    git remote add origin https://github.com/user/repo.git
    ```

- **`git fetch <remote>`**
  - 从远程仓库获取更新，但不自动合并。
  - **示例**: 
    ```bash
    git fetch origin
    ```

- **`git pull <remote> <branch>`**
  - 从远程仓库获取更新并合并到当前分支。
  - **示例**: 
    ```bash
    git pull origin main
    ```

- **`git push <remote> <branch>`**
  - 将本地分支的更改推送到远程仓库。
  - **示例**: 
    ```bash
    git push origin main
    ```

### 8. 标签管理
- **`git tag`**
  - 列出所有标签。
  - **示例**: 
    ```bash
    git tag
    ```

- **`git tag <tag-name>`**
  - 创建一个新标签。
  - **示例**: 
    ```bash
    git tag v1.0
    ```

- **`git push <remote> <tag-name>`**
  - 将标签推送到远程仓库。
  - **示例**: 
    ```bash
    git push origin v1.0
    ```

### 9. 撤销更改
- **`git checkout -- <file>`**
  - 撤销对指定文件的所有未保存更改。
  - **示例**: 
    ```bash
    git checkout -- file.txt
    ```

- **`git reset --hard`**
  - 重置工作目录和暂存区到最后一次提交状态（注意：会丢失未保存的更改）。
  - **示例**: 
    ```bash
    git reset --hard
    ```

### 10. 其他命令
- **`git stash`**
  - 将当前工作目录的更改保存到栈中，以便稍后恢复。
  - **示例**: 
    ```bash
    git stash
    ```

- **`git stash pop`**
  - 恢复最近存储的更改并从栈中删除。
  - **示例**: 
    ```bash
    git stash pop
    ```

- **`git rebase <branch>`**
  - 将当前分支的更改应用到指定分支的最新提交上。
  - **示例**: 
    ```bash
    git rebase main
    ```

- **`git cherry-pick <commit>`**
  - 将指定的提交应用到当前分支。
  - **示例**: 
    ```bash
    git cherry-pick 1a2b3c4
    ```

