# 🚀 GITFLOW + PULL REQUEST PRACTICE (FULL TEAM WORKFLOW)

---

# 🎯 MỤC TIÊU

Sau bài này, bạn sẽ:
- Hiểu Git + GitHub trong thực tế
- Làm việc nhóm bằng Gitflow
- Sử dụng Pull Request (PR) đúng chuẩn công ty
- Biết review, approve, merge
- Xử lý các tình huống: conflict, pull, update PR

---

# 🧠 BỐI CẢNH DỰ ÁN

Team bạn đang xây dựng:

👉 **Web App: Mini Task Manager**

Chức năng:
- Login
- Tạo task
- Hoàn thành task

---

# 👥 TEAM (4 NGƯỜI)

| Người | Vai trò |
|------|--------|
| Dev A | Login |
| Dev B | Task |
| Dev C | Complete Task |
| Dev D | Reviewer + QA |

---

# ⚙️ PHẦN 0 – SETUP (LEADER LÀM)

## 1. Tạo project

```bash
mkdir task-app
cd task-app
git init
```
## 2. Tạo file
```
echo "# Task App" > README.md
echo "console.log('App start');" > app.js
```
## 3. Commit đầu
```
git add .
git commit -m "init project"
```
## 4. Tạo branch chuẩn
```
git branch -M main
git checkout -b develop
```
## 5. Push lên GitHub
```
git remote add origin <repo_url>
git push -u origin main
git push -u origin develop
```
👉 Leader add team vào repo

# 👇 PHẦN 1 – MỌI NGƯỜI CLONE
```
git clone <repo_url>
cd task-app
git checkout develop
```
# 🚀 PHẦN 2 – FEATURE + PULL REQUEST
## 👨‍💻 DEV A – LOGIN
## 1. Tạo branch
```
git checkout develop
git pull origin develop
git checkout -b feature/login
```
## 2. Code
```
echo "function login() { return 'login ok'; }" >> app.js
```
## 3. Commit
```
git add app.js
git commit -m "feat: add login"
```
## 4. Push
```
git push origin feature/login
```
## 5. TẠO PULL REQUEST

👉 Lên GitHub:

Compare & Pull Request

Base: develop

Compare: feature/login

Title: feat: add login

Description: add login feature

## 6. REVIEW (DEV D)

## Dev D:

Comment: "ok" hoặc yêu cầu sửa

## 7. APPROVE + MERGE

Approve

Merge Pull Request

## 8. UPDATE LOCAL
```
git checkout develop
git pull origin develop
```
## 👨‍💻 DEV B – TASK
```
git checkout develop
git pull origin develop
git checkout -b feature/task
```
```
echo "function createTask() { return 'task created'; }" >> app.js
```
```
git add app.js
git commit -m "feat: add task"
git push origin feature/task
```
👉 Tạo PR → Review → Merge giống Dev A

## 👨‍💻 DEV C – COMPLETE TASK
```
git checkout develop
git pull origin develop
git checkout -b feature/complete-task
```
```
echo "function completeTask() { return 'done'; }" >> app.js
```
```
git add app.js
git commit -m "feat: complete task"
git push origin feature/complete-task
```
👉 Tạo PR → Review → Merge

# 🐞 PHẦN 3 – BUGFIX
Tình huống:

Login bị lỗi
```
git checkout develop
git pull origin develop
git checkout -b bugfix/login-error
```
👉 sửa code
```
git add app.js
git commit -m "fix: login error"
git push origin bugfix/login-error
```
👉 Tạo PR → Review → Merge vào develop

# 📦 PHẦN 4 – RELEASE
```
git checkout develop
git pull origin develop
git checkout -b release/v1.0.0
echo "version 1.0.0" >> README.md
```
```
git add README.md
git commit -m "chore: release v1.0.0"
git push origin release/v1.0.0
```
👉 Tạo PR:

base: main

compare: release/v1.0.0

👉 Merge vào main

👉 Sau đó:
```
git checkout develop
git merge release/v1.0.0
git push origin develop
```
# 🚨 PHẦN 5 – HOTFIX
Tình huống:

Production lỗi
```
git checkout main
git pull origin main
git checkout -b hotfix/v1.0.1
```
👉 sửa lỗi
```
git add .
git commit -m "hotfix: critical fix"
git push origin hotfix/v1.0.1
```
👉 Tạo PR:

base: main

👉 Merge xong:
```
git checkout develop
git merge hotfix/v1.0.1
git push origin develop
```
# ⚠️ TÌNH HUỐNG THỰC TẾ (QUAN TRỌNG)
## 🔁 1. Bị reject khi push
```
git pull origin develop
```
## 💥 2. Conflict

Git báo:
```
<<<<<<< HEAD
code của bạn
=======
code người khác
>>>>>>> branch
```
👉 sửa → sau đó:
```
git add .
git commit -m "resolve conflict"
```
## 🔄 3. Update PR khi bị yêu cầu sửa
# sửa code
```
git add .
git commit -m "fix: update after review"
git push origin feature/xxx
```
👉 PR tự update

## ❌ 4. Lỡ commit sai branch
```
git cherry-pick <commit_id>
```
## 🔙 5. Undo commit
```
git reset --soft HEAD~1
```
## 🔍 6. Xem lịch sử
```
git log --oneline --graph --all
```
