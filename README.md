## 分支说明

hexo 分支存放项目文件

master 分支存放站点文件

##  如何更新

### 新建文章

`hexo new [layout] title`

### 部署

```bash
hexo clean --config source/_data/next.yml && hexo g --config source/_data/next.yml
hexo d
```



## 在新主机上的环境配置步骤


1. `git clone git@github.com:FloatingShuYin/FloatingShuYin.GitHub.git`
2. `cd /FloatingShuYin.GitHub.git`
3. `npm install -g hexo-cli`
4. `npm install `



## 依赖的插件

1. `npm install hexo-deployer-git`
