# vue-boilerplate

项目名称：药牛牛
合作单位：重庆肿瘤医院

[接口文档](https://www.showdoc.cc/712418420869106?page_id=4043773539371723)

[蓝湖地址](https://lanhuapp.com/web/#/item/project/board?pid=026b7169-0255-437f-a95b-53da02ddce7c)

[项目地址](http://123.207.231.244:3000/projects/cqch_ynn-website)

## 部署

服务器：47.107.142.42
项目地址：/usr/local/www/Drug-Web

域名：

- http://cqprecision.cn/
- http://www.cqprecision.cn/

```sh
# 根目录下

scp -r ./dist/* root@47.107.142.42:/usr/local/www/Drug-Web
```

需 nginx 配置域名并转发`/Apis`开头的请求到后台

## Project setup

```
yarn install
```

### Compiles and hot-reloads for development

```
yarn run serve
```

### Compiles and minifies for production

```
yarn run build
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

yarn build
