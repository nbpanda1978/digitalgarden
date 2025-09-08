---
{"dg-publish":true,"permalink":"/开发/Gatsby 使用Github Pages搭建个人网站/"}
---

一、在Github上新建一个Repository用于存放Gateby的网站
![6e2cc5b0275436c238989caf00a3b301_MD5.png](/img/user/%E5%BC%80%E5%8F%91/attachments/6e2cc5b0275436c238989caf00a3b301_MD5.png)
二、在本机（开发机）yunchenweb目录下安装gh-pages包
```
npm install gh-pages --save-dev
```
三、修改yuchenweb根目录下 gastby-config.js 和 package.json 文件
3.1 gastby-config.js:
```
module.exports = {
 pathPrefix: `/project-name`, 
 }
```
如果配置成 `/project-name` ，则访问 `https://username.github.io/project-name/`；这里的project-name就是新建的repository的name  yunchenweb
3.2 package.json:
```
"scripts": {
 "deploy": "gatsby build --prefix-paths && gh-pages -d public"
  }
```
在package.json，添加一个scripts 配置，将先将静态文件build 到public 目录，然后再**push** 到github工程的gh-pages 分支。

四、本机git对接github repository
在yuchenweb目录下
```
git init
git remote add origin https://github.com/nbpanda1978/yuchenweb.git
```
![fdfaaac2be5f53bec93c884686652a93_MD5.png](/img/user/%E5%BC%80%E5%8F%91/attachments/fdfaaac2be5f53bec93c884686652a93_MD5.png)

五、发布至Github
在本机（开发机）输入
```
npm run deploy
```
六、配置 GitHub Pages 源分支
必须从 GitHub 中的存储库设置中选择要部署哪个分支，GitHub Pages 才能运行。在 GitHub 上：
1. 导航到您站点的存储库。
2. 在存储库名称下，单击**“设置”**。
3. 在 GitHub Pages 部分中，使用**“Source”**下拉列表选择 `gh-pages`（作为 GitHub Pages 发布源。
4. 保存
七、验证
打开浏览时 输入 `https://username.github.io/project-name/`