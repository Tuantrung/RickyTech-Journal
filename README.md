# 🚀 Hướng dẫn tạo Tech Blog cá nhân với GitHub Pages + Hugo + Decap CMS

## 🧱 Yêu cầu:

- Miễn phí hosting (GitHub Pages)
- Miễn phí domain (GitHub subdomain)
- CMS mạnh mẽ (Decap CMS)
- Sử dụng Hugo - static site generator nhanh, nhẹ

---

## 📦 Bước 1: Cài đặt công cụ

### 1. Cài Git:
```bash
sudo apt install git

### 2. Cài Hugo:
```bash
sudo apt install hugo

## 📁 Bước 2: Tạo project Hugo
```bash
hugo new site my-tech-blog
cd my-tech-blog

## 🎨 Bước 3: Thêm theme PaperMod
```bash
git init
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
echo 'theme = "PaperMod"' >> config.toml

## ✍️ Bước 4: Tạo bài viết đầu tiên
```bash
hugo new posts/hello-world.md

Chỉnh sửa content/posts/hello-world.md, đổi nội dung và bỏ dòng draft: true.
## 🌍 Bước 5: Xem thử blog trên máy local
```bash
hugo server -D

Truy cập http://localhost:1313 để xem blog.
## 🔧 Bước 6: Tích hợp CMS (Decap CMS)
### 1. Tạo thư mục CMS:
```bash
mkdir -p static/admin

### 2. Tạo file static/admin/index.html
```bash
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>Content Manager</title>
    <script src="https://unpkg.com/netlify-cms@^2.0.0/dist/netlify-cms.js"></script>
  </head>
  <body>
  </body>
</html>

### 3. Tạo file static/admin/config.yml
```bash
backend:
  name: github
  repo: your-username/my-tech-blog
  branch: main

media_folder: "static/images/uploads"
public_folder: "/images/uploads"

collections:
  - name: "posts"
    label: "Posts"
    folder: "content/posts"
    create: true
    slug: "{{slug}}"
    fields:
      - { label: "Title", name: "title", widget: "string" }
      - { label: "Body", name: "body", widget: "markdown" }

## 🚀 Bước 7: Đẩy lên GitHub và deploy
#### 1. Tạo repo trên GitHub
#### 2. Thêm remote và đẩy code:
```bash
git remote add origin https://github.com/your-username/my-tech-blog.git
git branch -M main
git push -u origin main

## 📦 Bước 8: Build site và deploy GitHub Pages
Build site:
```bash
hugo

Kết quả build nằm trong thư mục /public.

Bạn có thể:

    Tạo branch gh-pages và push nội dung public vào đó.

    Hoặc dùng GitHub Actions để tự động build & deploy (khuyến nghị).

## ✅ Bước 9: Truy cập blog & CMS

    Blog: https://your-username.github.io

    CMS: https://your-username.github.io/admin/

🔄 Tùy chọn: Dùng GitHub Actions để tự động deploy

    Bạn có thể thêm file .github/workflows/gh-pages.yml để tự động build khi push lên main.

Nếu bạn muốn, hãy yêu cầu mình tạo sẵn file workflow đó.
