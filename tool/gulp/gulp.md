# gulp

### 介绍
- 概念
    - gulp是一个自动化构建工具，主要用来设定程序自动处理静态资源的工作。简单的说，gulp就是用来打包项目的。
- 安装
    - `npm install gulp-cli -g`
    - `npm install gulp -D`
    - `npx -p touch nodetouch gulpfile.js`
- 初始化
    - `npm init`
### gulp函数
- gulp.src() 找到源文件路径
- gulp.dest() 找到目的文件的路径
- 整理html文件
```javascript
gulp.task("copy-html",function(){
    return gulp.src("index.html")
    .pipe(gulp.dest("dist/"))
})
```
- 静态文件/拷贝文件
```javascript
gulp.task("images",function(){
    return gulp.src("img/**/*.{jpg,png}").pipe(gulp.dest('dist/images"))
})
```
- 拷贝多个文件到一个目录
```javascript
gulp.task("data",function(){
    return gulp.src(["json/*.json","xml/*.xml","!xml/04.xml"])
    .pipe(gulp.dest("dist/data"))
})
```
- 一次性执行多个任务操作
```javascript
gulp.task("build",["copy-html","image","data"],function(){
    console.log("任务操作完毕")
})
```
- 监听，如果监听到文件有改变，会自动去执行对应的任务，更新数据
```javascript
gulp.task("watch",function(){
/*
    第一个参数，是文件监听的路径
    第二个参数，我们要执行的任务
*/
gulp.watch("index.html",["copy-html"]);
gulp.watch(""img/**/*",["images])
gulp.watch(["jason/*.json","xml/*.xml","!xml/04.xml"],["data"])
})
```
- 启动一个服务器（配合插件）
```javascript
const connect = require("gulp-connect")
gulp.task("server",function(){
    connect.server({
        root:"dist",//设置跟目录
        port:8888,
        livereload:true//启动实时刷新功能
    })
})
```
- 同时启动监听和服务 ，default我们可以直接在控制台通过 gulp命令启动
```javascript
gulp.task("default",["watch","server"])
```

### gulp插件
- 使用
    - 下载到本地
        - cnpm install 插件名字 --save -dev
        - cnpm i 插件名字 -D
    - 通过require[]引入文件
    - 查阅插件用法
- 常用插件
    - sass
    - gulp-minify-css 压缩css
        - 开发版本 index.css  上线版本 index.mini.css
    - gulp-rename 重命名插件
        - 保存开发，压缩上线两个版本
    - gulp-concat  合并文件
    - gulp-uglify 压缩js文件
    - gulp-connect 启动服务器  