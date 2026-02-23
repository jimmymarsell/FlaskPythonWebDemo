# GitHub 代码推送完整指南

## 目录
1. [准备工作](#准备工作)
2. [首次推送（新项目）](#首次推送新项目)
3. [后续更新推送](#后续更新推送)
4. [常见问题](#常见问题)
5. [快捷命令速查表](#快捷命令速查表)

---

## 准备工作

### 1. 安装 Git
- 下载地址：https://git-scm.com/downloads
- 安装后验证：打开终端输入 `git --version`

### 2. 配置 Git 用户信息（只需配置一次）
```bash
git config --global user.name "你的GitHub用户名"
git config --global user.email "你的GitHub邮箱"
```

### 3. 在 GitHub 上创建仓库
1. 登录 GitHub
2. 点击右上角 "+" → "New repository"
3. 填写仓库名称，选择 Public/Private
4. **不要**勾选 "Initialize this repository with a README"（如果本地已有代码）
5. 点击 "Create repository"

---

## 首次推送（新项目）

### 完整步骤

#### 步骤 1：进入项目目录
```bash
cd 你的项目路径
```

#### 步骤 2：初始化 Git 仓库
```bash
git init
```

#### 步骤 3：关联远程仓库
```bash
git remote add origin https://github.com/你的用户名/仓库名.git
```

#### 步骤 4：创建 .gitignore 文件（重要！）
在项目根目录创建 `.gitignore` 文件，内容示例：
```
# 编译生成的文件
*.exe
*.out
*.o
*.obj

# IDE 配置文件
.vscode/
.idea/

# 临时文件
*.tmp
*.temp
```

#### 步骤 5：添加文件到暂存区
```bash
git add .
```
（`.` 表示添加所有文件，也可以指定文件名 `git add 文件名`）

#### 步骤 6：提交文件
```bash
git commit -m "Initial commit"
```
（`-m` 后面是提交说明，用英文或中文都可以）

#### 步骤 7：重命名分支为 main
```bash
git branch -M main
```

#### 步骤 8：推送到 GitHub
```bash
git push -u origin main
```

---

## 后续更新推送

当你修改了代码后，用以下步骤推送：

### 快捷方式（3步）
```bash
git add .
git commit -m "更新说明"
git push
```

### 详细步骤

#### 1. 查看修改状态
```bash
git status
```

#### 2. 添加修改的文件
```bash
git add .
```

#### 3. 提交
```bash
git commit -m "描述你的修改"
```
提交说明示例：
- "添加了快速排序算法"
- "修复了链表删除的bug"
- "更新了README文档"

#### 4. 推送到 GitHub
```bash
git push
```

---

## 常用命令详解

### git status
查看当前仓库状态，哪些文件修改了、哪些待提交

### git add
- `git add .` - 添加所有文件
- `git add 文件名` - 添加指定文件
- `git add *.c` - 添加所有 .c 文件

### git commit
- `git commit -m "说明"` - 提交并添加说明
- `git commit` - 提交（会打开编辑器写说明）

### git push
- `git push` - 推送到远程仓库
- `git push -u origin main` - 首次推送，设置上游分支

### git pull
拉取远程仓库的更新（如果别人修改了代码）
```bash
git pull
```

### git log
查看提交历史
```bash
git log
```

---

## 常见问题

### Q1: 提示 "fatal: not a git repository"
**A:** 还没初始化 git 仓库，先执行 `git init`

### Q2: 提示 "remote origin already exists"
**A:** 远程仓库已关联，可以先删除再添加：
```bash
git remote remove origin
git remote add origin https://github.com/用户名/仓库名.git
```

### Q3: 推送时需要输入密码
**A:** 建议使用 Personal Access Token：
1. GitHub → Settings → Developer settings → Personal access tokens
2. 生成新 token，勾选 repo 权限
3. 推送时用 token 代替密码

### Q4: 提示 "error: failed to push some refs"
**A:** 远程仓库有本地没有的内容，先拉取：
```bash
git pull --rebase origin main
git push
```

---

## 完整示例：从零开始推送

假设你有一个新项目 `MyProject`，要推送到 GitHub：

```bash
# 1. 进入项目目录
cd E:\MyProject

# 2. 初始化 git
git init

# 3. 关联远程仓库（换成你自己的地址）
git remote add origin https://github.com/jimmymarsell/MyProject.git

# 4. 创建 .gitignore（手动创建文件）

# 5. 添加所有文件
git add .

# 6. 提交
git commit -m "Initial commit"

# 7. 重命名分支
git branch -M main

# 8. 推送
git push -u origin main
```

---

## 后续更新示例

```bash
# 修改了一些代码...

# 1. 查看状态
git status

# 2. 添加修改
git add .

# 3. 提交
git commit -m "添加了新功能"

# 4. 推送
git push
```

---

## 记忆口诀

**首次推送 8 步：**
1. 进目录
2. 初始化 (init)
3. 加远程 (remote add)
4. 建忽略 (.gitignore)
5. 加文件 (add)
6. 提交 (commit)
7. 改分支 (branch -M main)
8. 推送 (push -u origin main)

**后续更新 3 步：**
1. add
2. commit
3. push
