## Git 和 GitHub 工作流程

项目远程仓库名 `testProject/testRepo`，主分支为 `main`，GitHub 用户名为 `ChunzhengLab`。

### 1. Fork 仓库

1. 登录 GitHub，访问 `testProject/testRepo` 仓库页面。
2. 点击右上角的 "Fork" 按钮。
3. 在弹出的窗口中选择将仓库 fork 到 `ChunzhengLab` 账户。

### 2. 克隆仓库到本地

```bash
git clone https://github.com/ChunzhengLab/testRepo.git
cd testRepo
```

### 3. 设置上游仓库

```bash
git remote add upstream https://github.com/testProject/testRepo.git
```

### 4. 创建新分支

使用 `git switch` 创建并切换到新分支：

```bash
git switch -c my-feature
```

### 5. 进行开发和提交更改

```bash
# 编辑文件，进行开发
git add .
git commit -m "Add new feature"
```

### 6. 推送到 GitHub

```bash
git push origin my-feature
```

### 7. 创建 Pull Request (PR)

1. 访问 `ChunzhengLab/testRepo` 仓库页面。
2. 点击 "Compare & pull request" 按钮。
3. 确认 PR 的目标分支为 `testProject/testRepo` 的 `main` 分支。
4. 添加标题和描述，然后点击 "Create pull request" 按钮。

### 8. PR 被 Squash 合并后

当管理员选择“Squash and merge”选项合并 PR 时，所有的提交会被压缩成一个提交记录。这可能会导致 `my-feature` 分支的提交记录与原始仓库的主分支不同步。为了解决这个问题并继续开发，可以使用 `git rebase`。

### 9. 使用 `git rebase` 保持分支同步和整洁

#### 1. 确保主分支是最新的

首先，确保 `main` 分支包含最新的上游更改：

```bash
git switch main
git fetch upstream
git pull upstream main
git push origin main
```

#### 2. 切换到功能分支并开始 rebase

切换回功能分支并进行 rebase：

```bash
git switch my-feature
git rebase main
```

在 `rebase` 过程中，如果有冲突，Git 会停止要求解决冲突。解决冲突后，使用 `git add` 标记冲突已解决，然后继续 rebase：

```bash
# 解决冲突
git add <冲突文件>

# 继续 rebase
git rebase --continue
```

如果想要取消 rebase，可以执行

```bash
git rebase --abort
```

#### 3. 强制推送更新到远程仓库

因为 rebase 重写了提交历史，需要强制推送更新到远程仓库：

```bash
git push -f origin my-feature
```

### 10. 继续开发和提交新更改

完成 rebase 后，可以继续在 `my-feature` 分支上开发，并将更改推送到远程仓库：

```bash
# 开发新功能
git add .
git commit -m "Continue development on new feature"
git push origin my-feature
```

### 小结

通过以上步骤，可以在继续开发时保持该分支与主分支同步，并且拥有一个干净的提交历史。以下是完整的工作流示例：

1. **同步主分支**：
    ```bash
    git switch main
    git fetch upstream
    git pull upstream main
    git push origin main
    ```

2. **重新基于主分支**：
    ```bash
    git switch my-feature
    git rebase main
    ```

3. **解决冲突（如有）**：
    ```bash
    # 解决冲突后
    git add <冲突文件>
    git rebase --continue
    ```

4. **强制推送**：
    ```bash
    git push -f origin my-feature
    ```

## Git常用命令

### 基本操作

1. **初始化 Git 仓库**
   ```bash
   git init
   ```
   在当前目录中初始化一个新的 Git 仓库。

2. **克隆远程仓库**
   ```bash
   git clone <repository_url>
   ```
   克隆远程仓库到本地。

3. **查看仓库状态**
   ```bash
   git status
   ```
   显示工作目录和暂存区的状态。

4. **添加文件到暂存区**
   ```bash
   git add <file_or_directory>
   ```
   将文件或目录添加到暂存区。

5. **提交更改**
   ```bash
   git commit -m "commit message"
   ```
   提交暂存区的更改并添加提交信息。

6. **查看提交历史**
   ```bash
   git log
   ```
   查看仓库的提交历史记录。

### 分支操作

1. **查看分支**
   ```bash
   git branch
   ```
   列出所有本地分支。

2. **创建新分支**
   ```bash
   git branch <branch_name>
   ```
   创建一个新的分支。

3. **切换分支**
   ```bash
   git switch <branch_name>
   ```
   切换到指定的分支。

4. **创建并切换到新分支**
   ```bash
   git switch -c <branch_name>
   ```
   创建一个新的分支并切换到该分支。

5. **合并分支**
   ```bash
   git merge <branch_name>
   ```
   将指定分支合并到当前分支。

6. **删除分支**
   ```bash
   git branch -d <branch_name>
   ```
   删除本地分支。

### 远程仓库操作

1. **添加远程仓库**
   ```bash
   git remote add <remote_name> <repository_url>
   ```
   添加一个新的远程仓库。

2. **查看远程仓库**
   ```bash
   git remote -v
   ```
   查看所有远程仓库及其 URL。

3. **推送到远程仓库**
   ```bash
   git push <remote_name> <branch_name>
   ```
   将本地分支推送到远程仓库。

4. **拉取远程仓库的更改**
   ```bash
   git pull <remote_name> <branch_name>
   ```
   从远程仓库拉取并合并指定分支的更改。

5. **从远程仓库获取更新**
   ```bash
   git fetch <remote_name>
   ```
   从远程仓库获取更新但不合并。

### 变基操作

1. **变基当前分支**
   ```bash
   git rebase <branch_name>
   ```
   将当前分支变基到指定分支。

2. **继续变基**
   ```bash
   git rebase --continue
   ```
   解决冲突后继续变基。

3. **中止变基**
   ```bash
   git rebase --abort
   ```
   中止变基操作并恢复到变基前的状态。

### 暂存和恢复

1. **暂存当前更改**
   ```bash
   git stash
   ```
   暂存当前工作目录的更改。

2. **恢复暂存的更改**
   ```bash
   git stash apply
   ```
   恢复最近一次暂存的更改。

3. **查看暂存列表**
   ```bash
   git stash list
   ```
   查看所有暂存的更改。

### 其他常用命令

1. **显示文件差异**
   ```bash
   git diff
   ```
   显示工作目录和暂存区之间的差异。

2. **显示暂存区与最近一次提交之间的差异**
   ```bash
   git diff --cached
   ```
   显示暂存区和上一次提交之间的差异。

3. **查看文件的提交历史**
   ```bash
   git log -- <file_name>
   ```
   查看指定文件的提交历史。

4. **重置暂存区和工作目录**
   ```bash
   git reset --hard <commit_hash>
   ```
   重置当前分支的 HEAD 到指定提交，并重置暂存区和工作目录，使其与该提交匹配。

## `git reflog` 的使用

`git reflog` 是一个非常强大的工具，用于记录对分支的引用（`ref`）所做的所有更改。每当对仓库进行操作，如提交、合并、重置等，`git reflog` 都会记录这些操作的历史。它对于恢复误操作（如错误的 reset 或 merge）非常有用。

### `git reflog` 的常用命令和用法

#### 1. 查看 reflog

```bash
git reflog
```
列出所有的引用日志，显示最近的操作历史。每一行都包括一个操作的哈希值、操作时间、操作人、操作类型和简短的操作描述。

示例输出：
```
abc1234 HEAD@{0}: commit: Add new feature
def5678 HEAD@{1}: rebase finished: returning to refs/heads/main
ghi9101 HEAD@{2}: checkout: moving from my-feature to main
```

#### 2. 使用 reflog 恢复到之前的状态

假设误操作重置了分支，可以使用 reflog 找到之前的提交并恢复：

```bash
git reset --hard HEAD@{2}
```
这将把当前分支重置到 reflog 列表中编号为 2 的操作对应的提交状态。

#### 3. 查看特定引用的 reflog

可以查看特定分支的引用日志，例如查看 `main` 分支的 reflog：

```bash
git reflog show main
```
这会显示 `main` 分支的操作历史。

#### 4. 使用 reflog 恢复已删除的分支

如果误删除了一个分支，可以通过 reflog 找到该分支的最后一个提交并恢复：

```bash
# 查看 HEAD 的引用日志，找到被删除分支的最后一个提交
git reflog

# 恢复已删除分支
git branch <deleted-branch-name> <commit-hash>
```

#### 5. 查看某个引用的具体操作历史

```bash
git reflog show HEAD@{1}
```
查看特定引用的详细操作历史，例如 HEAD@{1}。

### 常见场景示例

#### 恢复误删除的提交

假设误使用 `git reset --hard` 删除了几个提交，可以通过 `git reflog` 找到并恢复它们：

1. **查看 reflog 以找到被删除的提交：**

   ```bash
   git reflog
   ```

   输出示例：
   ```
   abc1234 HEAD@{0}: reset: moving to abc1234
   def5678 HEAD@{1}: commit: Add new feature
   ghi9101 HEAD@{2}: commit: Fix bug
   ```

2. **恢复到被删除的提交：**

   假设想恢复到 `ghi9101` 提交：
   ```bash
   git reset --hard ghi9101
   ```

#### 找回被删除的分支

假设误删除了一个名为 `my-feature` 的分支：

1. **查看 reflog 以找到该分支的最后一个提交：**

   ```bash
   git reflog
   ```

   找到 `my-feature` 分支的最后一个提交的哈希值。

2. **重新创建该分支：**

   ```bash
   git branch my-feature <commit-hash>
   ```


## 在 Git 中只暂存（stash）部分文件的修改

1.	将你想保留的文件的修改添加到暂存区：

```bash
git add path/to/file_you_want_to_keep
```


2.	使用 --keep-index 参数进行暂存：

```bash
git stash push --keep-index
```

注意使用`--keep-index`
这会暂存未暂存的文件修改（即未使用 git add 的文件），并保留已暂存的文件修改在工作区。

