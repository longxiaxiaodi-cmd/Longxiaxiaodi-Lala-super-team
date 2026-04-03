# GitHub 網站上傳流程

## 📋 前置準備

### 1. 確認 Git 配置

```bash
# 查看當前 Git 配置
cd ~/.openclaw/Longxiaxiaodi-Lala-super-team
git config --list

# 確認用戶名和郵箱
git config user.name
git config user.email
```

### 2. 配置 Git 憑證（如果尚未配置）

```bash
# 配置 Git 憑證助手
git config --global credential.helper osxkeychain

# 或者使用 store 模式（不推薦，不安全）
git config --global credential.helper store
```

### 3. 創建 GitHub Personal Access Token

1. 訪問：https://github.com/settings/tokens
2. 點擊「Generate new token (classic)」
3. 選擇 `repo` 權限
4. 點擊「Generate token」
5. 複製 token（只顯示一次）

---

## 🚀 上傳流程（選項 3：只上傳靜態文件）

### 步驟 1：構建 Hugo 網站

```bash
# 進入網站目錄
cd ~/.openclaw/Longxiaxiaodi-Lala-super-team/growth-tracker

# 構建網站
hugo

# 檢查構建結果
ls -la public/
```

### 步驟 2：複製靜態文件到倉庫根目錄

```bash
# 回到倉庫根目錄
cd ~/.openclaw/Longxiaxiaodi-Lala-super-team

# 複製 public/ 目錄的內容到倉庫根目錄
cp -r growth-tracker/public/* .

# 檢查複製結果
ls -la
```

### 步驟 3：提交變更到 Git

```bash
# 查看變更狀態
git status

# 添加所有變更
git add .

# 提交變更
git commit -m "Add static website files (Option 3) - Deploy compiled Hugo site"

# 查看提交歷史
git log --oneline -3
```

### 步驟 4：推送到 GitHub

```bash
# 推送到 GitHub
git push origin main

# 如果遇到身份驗證問題，輸入：
# Username: longxiaxiaodi
# Password: <your-personal-access-token>
```

### 步驟 5：驗證推送結果

```bash
# 查看遠程分支
git branch -a

# 查看推送狀態
git status
```

---

## 🔄 後續更新流程

### 更新網站內容後

```bash
# 1. 修改網站內容
cd ~/.openclaw/Longxiaxiaodi-Lala-super-team/growth-tracker/content/
# 編輯內容文件...

# 2. 構建網站
cd ~/.openclaw/Longxiaxiaodi-Lala-super-team/growth-tracker
hugo

# 3. 複製靜態文件
cd ~/.openclaw/Longxiaxiaodi-Lala-super-team
rm -rf 404.html categories/ craft/ index.html index.xml lala/ lumi/ ori/ page/ pixel/ sage/ scss/ sitemap.xml tags/ ts/
cp -r growth-tracker/public/* .

# 4. 提交變更
git add .
git commit -m "Update website content"

# 5. 推送到 GitHub
git push origin main
```

---

## 🎯 配置 GitHub Pages

### 1. 訪問 GitHub Pages 設置

訪問：https://github.com/longxiaxiaodi-cmd/Longxiaxiaxiaodi-Lala-super-team/settings/pages

### 2. 配置 GitHub Pages

- **Source:** 選擇「Deploy from a branch」
- **Branch:** 選擇「main」
- **Folder:** 選擇「/ (root)」
- 點擊「Save」

### 3. 等待部署完成

- 等待 1-2 分鐘
- 查看部署狀態

### 4. 訪問網站

訪問：https://longxiaxiaodi-cmd.github.io/Longxiaxiaodi-Lala-super-team/

---

## 🔧 常見問題

### 問題 1：Git 推送失敗

**錯誤訊息：**
```
fatal: could not read Username for 'https://github.com': Device not configured
```

**解決方案：**
```bash
# 配置 Git 憑證助手
git config --global credential.helper osxkeychain

# 推送時輸入用戶名和 token
git push origin main
# Username: longxiaxiaodi
# Password: <your-personal-access-token>
```

### 問題 2：Git 推送失敗（SSH）

**錯誤訊息：**
```
fatal: 'github.com/longxiaxiaodi-cmd/Longxiaxiaodi-Lala-super-team.git' does not appear to be a git repository
```

**解決方案：**
```bash
# 檢查遠程 URL
git remote -v

# 如果是 SSH 格式，改為 HTTPS 格式
git remote set-url origin https://github.com/longxiaxiaodi-cmd/Longxiaxiaodi-Lala-super-team.git

# 推送
git push origin main
```

### 問題 3：GitHub Pages 部署失敗

**解決方案：**
1. 檢查 GitHub Pages 設置
2. 確認分支和目錄設置正確
3. 查看部署日誌

---

## 📊 快速參考

### 完整上傳流程（一次性）

```bash
# 1. 構建網站
cd ~/.openclaw/Longxiaxiaodi-Lala-super-team/growth-tracker
hugo

# 2. 複製靜態文件
cd ~/.openclaw/Longxiaxiaodi-Lala-super-team
cp -r growth-tracker/public/* .

# 3. 提交變更
git add .
git commit -m "Add static website files (Option 3) - Deploy compiled Hugo site"

# 4. 推送到 GitHub
git push origin main
```

### 更新網站流程（後續）

```bash
# 1. 構建網站
cd ~/.openclaw/Longxiaxiaodi-Lala-super-team/growth-tracker
hugo

# 2. 複製靜態文件
cd ~/.openclaw/Longxiaxiaodi-Lala-super-team
rm -rf 404.html categories/ craft/ index.html index.xml lala/ lumi/ ori/ page/ pixel/ sage/ scss/ sitemap.xml tags/ ts/
cp -r growth-tracker/public/* .

# 3. 提交變更
git add .
git commit -m "Update website content"

# 4. 推送到 GitHub
git push origin main
```

---

## 🎉 完成

完成後，你可以：
1. 訪問 GitHub：https://github.com/longxiaxiaodi-cmd/Longxiaxiaodi-Lala-super-team
2. 配置 GitHub Pages
3. 訪問網站：https://longxiaxiaodi-cmd.github.io/Longxiaxiaodi-Lala-super-team/

---

_創建時間：2026-04-04 02:50_
_創建者：Lala 👔_
