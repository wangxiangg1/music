# 🎵 温暖简约音乐播放器 - 部署指南

## 文件说明
- `index.html` - 主文件（Web服务器默认入口）
- `main.html` - 同样的内容备份

---

## 方案一：GitHub Pages（最简单，推荐）

### 步骤：
1. 登录 [GitHub](https://github.com)
2. 点击右上角 "+" → "New repository"
3. 仓库名称填写：`music-player`（或你喜欢的名字）
4. 选择 "Public"
5. 点击 "Create repository"
6. 在仓库页面，点击 "uploading an existing file"
7. 把 `index.html` 拖进去，点击 "Commit changes"
8. 进入 Settings → Pages
9. Source 选择 "main" 分支，点击 Save
10. 等待1分钟，访问：`https://你的用户名.github.io/music-player/`

**优点**：免费、简单、HTTPS
**缺点**：国内访问可能较慢

---

## 方案二：Cloudflare Pages（推荐，全球加速）

### 步骤：
1. 注册 [Cloudflare](https://dash.cloudflare.com/sign-up)
2. 进入 "Workers & Pages"
3. 点击 "Create application" → "Pages" → "Upload assets"
4. 项目名称填写：`music-player`
5. 把 `index.html` 文件拖进去
6. 点击 "Deploy site"
7. 部署完成后获得链接：`https://music-player.pages.dev`

**优点**：全球CDN加速、免费、自动HTTPS、国内访问快
**缺点**：无

---

## 方案三：Vercel（快速）

### 步骤：
1. 访问 [Vercel](https://vercel.com)
2. 用 GitHub 账号登录
3. 先按方案一上传到 GitHub
4. 在 Vercel 点击 "Import Project"
5. 选择你的 GitHub 仓库
6. 点击 Deploy
7. 获得链接：`https://music-player.vercel.app`

**优点**：速度快、自动部署
**缺点**：需要先上传 GitHub

---

## 方案四：VPS 部署（Caddy，最简）

如果你有自己的 VPS：

### 1. 安装 Caddy
```bash
# Ubuntu/Debian
sudo apt install -y caddy

# CentOS/RHEL
sudo yum install -y caddy
```

### 2. 上传文件
```bash
# 创建目录
sudo mkdir -p /var/www/music

# 上传 index.html 到 /var/www/music/
# 可以用 SCP：
scp index.html user@your-vps:/var/www/music/
```

### 3. 配置 Caddy
```bash
# 编辑 Caddyfile
sudo nano /etc/caddy/Caddyfile
```

写入：
```
your-domain.com {
    root * /var/www/music
    file_server
}

# 或者用IP+端口：
:8080 {
    root * /var/www/music
    file_server
}
```

### 4. 启动
```bash
sudo systemctl restart caddy
```

访问 `http://your-vps-ip:8080` 或 `https://your-domain.com`

---

## 方案五：Netlify Drop（零配置，拖拽部署）

**最快方式！**

1. 打开 [Netlify Drop](https://app.netlify.com/drop)
2. 直接把 `index.html` 文件拖进页面
3. 完成！获得链接

---

## 🎯 推荐

| 你的情况 | 推荐方案 |
|---------|---------|
| 第一次部署网站 | Netlify Drop（30秒完成）|
| 想要国内访问快 | Cloudflare Pages |
| 已有 GitHub 账号 | GitHub Pages |
| 已有 VPS | Caddy |

---

## 多端使用

部署后，在任何设备（手机、平板、电脑）的浏览器中打开你的网址即可使用！

建议将网址添加到手机主屏幕，获得类似 App 的体验：
- **iOS**: Safari → 分享 → 添加到主屏幕
- **Android**: Chrome → 菜单 → 添加到主屏幕
