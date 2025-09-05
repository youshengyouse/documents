---
title: 新建 nextjs 项目
---

## 新建 nextjs 项目

```bash
## 镜像 https://registry.npmjs.org
## 不用科学上网

cd /home/tom/www2026/5_docs && pnpm create fumadocs-app fumadocs-20250721
# 过程如下
┌  Create Fumadocs App
│
◆  Choose a template
│  ● Next.js: Fumadocs MDX (recommended)
│  ○ Next.js: Content Collections
│  ○ React Router: MDX Remote
│  ○ Tanstack Start: MDX Remote
◆  Use `/src` directory?
│  ● Yes / ○ No
◆  Add default ESLint configuration?
│  ● Yes / ○ No
◇  Do you want to install packages automatically? (detected as pnpm)
│  Yes
│
◇  Project Generated
│
└  Done

## 切换到项目目录
cd fumadocs-20250721

## 安装依赖
npm config set registry https://registry.npmmirror.com
pnpm i

## 运行开发服务器
npm run dev | pnpm run dev | yarn dev
```

## 报错

```bash
 ⨯ [next]/internal/font/google/inter_59dee874.module.css:8:9
Module not found: Can't resolve '@vercel/turbopack-next/internal/font/google/font'
   6 |   font-display: swap;
   7 |   src: url(@vercel/turbopack-next/internal/font/google/font?{%22url%22:%22https://fonts.gstatic.com/s/inter/v19/UcC73FwrK3iLTeHuS_nVMrMxCp50SjIa2JL7W0Q5n-wU.woff2%22,%22preload%22:false,%22has_size_adjust%22:true}) format('woff2');
>  8 |   unicode-range: U+0460-052F, U+1C80-1C8A, U+20B4, U+2DE0-2DFF, U+A640-A69F, U+FE2E-FE2F;
     |         ^
   9 | }
  10 | /* cyrillic */
  11 | @font-face {

Import map: Resolved by import map
```

上面因为 google 字体的问题，下一课解决

## package.json

```json
{
  "name": "fumadocs-20250721",
  "version": "0.0.0",
  "private": true,
  "scripts": {
    "build": "next build",
    "dev": "next dev --turbo",
    "start": "next start",
    "postinstall": "fumadocs-mdx"
  },
  "dependencies": {
    "next": "15.4.2",
    "react": "^19.1.0",
    "react-dom": "^19.1.0",
    "fumadocs-ui": "15.6.5",
    "fumadocs-core": "15.6.5",
    "fumadocs-mdx": "11.7.0"
  },
  "devDependencies": {
    "@types/node": "24.0.15",
    "@types/react": "^19.1.8",
    "@types/react-dom": "^19.1.6",
    "typescript": "^5.8.3",
    "@types/mdx": "^2.0.13",
    "@tailwindcss/postcss": "^4.1.11",
    "tailwindcss": "^4.1.11",
    "postcss": "^8.5.6",
    "eslint": "^8",
    "eslint-config-next": "15.4.2"
  }
}
```
