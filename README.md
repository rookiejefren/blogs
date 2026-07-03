# Hexo Stellar Blog

这是一个使用 Hexo 和 Stellar 主题初始化的博客项目。

线上地址：

```text
https://blogs.murycarry.site/
```

## 常用命令

```bash
npm install
npm run server
npm run build
```

## 写文章

```bash
npx hexo new post "文章标题"
```

文章会生成在 `source/_posts/`。

## 功能配置

### Stellar 主题

主题配置主要在：

```text
_config.stellar.yml
```

当前已配置：

- 顶部/侧边菜单
- Wiki 文档入口
- 页脚访问统计
- Artalk 留言评论区

### 访问统计

访问人数统计使用不蒜子，脚本通过 `_config.yml` 的 `inject.script` 注入：

```yml
inject:
  script:
    - '<script async src="https://busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>'
```

页脚展示配置在 `_config.stellar.yml` 的 `footer.content`。

### 留言评论

评论系统使用自托管 Artalk，Stellar 配置：

```yml
comments:
  service: artalk
  comment_title: 快来参与讨论吧~
  artalk:
    server: https://blogs.murycarry.site/artalk
    site: 我的博客
```

Artalk 后台入口：

```text
https://blogs.murycarry.site/artalk/
```

管理员登录信息保存在服务器：

```bash
cat /root/artalk-admin.txt
```

## 服务器服务

当前服务器使用 systemd 和 nginx：

```bash
systemctl status blog
systemctl status artalk
systemctl status nginx
```

重启服务：

```bash
systemctl restart blog
systemctl restart artalk
systemctl reload nginx
```

端口关系：

```text
nginx 443 -> 127.0.0.1:4000   # Hexo 博客
nginx /artalk/ -> 127.0.0.1:23366   # Artalk 评论
```

## 连接 GitHub 仓库

```bash
git remote add origin git@github.com:你的用户名/你的仓库名.git
git push -u origin main
```

如果使用 HTTPS：

```bash
git remote add origin https://github.com/你的用户名/你的仓库名.git
git push -u origin main
```
