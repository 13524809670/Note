//安装命令
    
    npm install gulp   全局安装
    npm install -g gulp  本地下载
    npm install gulp-util   gulp利用
    npm install gulp-autoprefixer  浏览器兼容自动处理
    npm install gulp-stylus --save-dev  styl书写格式
    npm install gulp-rename   生成css
    npm init    生成 json

    npm install gulp-minify-css   压缩 css 文件
    npm install gulp-uglify   压缩 js 文件
    npm instal gulp-imagemin  压缩images
    npm install -g cnpm   快速下载 
        npm=cnpm    可快速下载



//压缩 css  js  images 不常用

    var minifyCSS = require('gulp-minify-css');
    var uglify = require("gulp-uglify");
    var imagemin = require('gulp-imagemin');



// 兼容  侦听  改变  常用

    var gulp = require('gulp');
    var stylus = require('gulp-stylus');
    var gutil = require('gulp-util');
    var rename = require("gulp-rename");



// 浏览器兼容自动处理

    var autoprefixer = require('gulp-autoprefixer');
    var browserslist = ['Android 2.3', 'Android >= 4', 'Chrome >= 20', 'Firefox >= 24', 'Explorer >= 8', 'iOS >= 6', 'Opera >= 12', 'Safari >= 6'];



// 在命令行使用 gulp 或 gulp watch 启动此任务

    gulp.task('default',  ['watch']);



// 侦听文件改变执行任务
// 在命令行使用 gulp styl 启动此任务

    gulp.task('watch', function () {
        gulp.watch('./styl/**/*', ['styl']);
    });
    gulp.task('styl',function(){
        gulp.src('./styl/*.styl')
            .pipe(stylus({
                compress:true
                
            }).on('error',gutil.log))
            .pipe(autoprefixer({
                browsers: browserslist,
                cascade: false
            }))
            .pipe(rename({
                suffix: ".min",
                extname: ".css"
            }))
            .pipe(gulp.dest('./min/'));
    })



// 压缩 css 文件
// 在命令行使用 gulp css 启动此任务

    gulp.task('css', function () {
    // 1. 找到文件
    gulp.src('css/index.css')
    // 2. 压缩文件
        .pipe(minifyCSS())
    // 3. 另存为压缩文件
        .pipe(gulp.dest('min/css'))
    })
    // 修改后在命令行使用 gulp auto 启动此任务
    gulp.task('auto', function () {
        // 监听文件修改，当文件被修改则执行 css 任务
        gulp.watch('min/*.css', ['css'])
    });
    // 使用 gulp.task('default') 定义默认任务
    // 在命令行使用 gulp 启动 css 任务和 auto 任务
    gulp.task('default', ['css', 'auto'])



//压缩 js 文件
// 在命令行使用 gulp script 启动此任务

    gulp.task('script', function() {
        // 1.找到文件
        gulp.src('js/*.js')
        // 2. 压缩文件
            .pipe(uglify())
        // 3. 另存为压缩文件
            .pipe(gulp.dest('em.js/js'))
    })



// 压缩图片任务
// 在命令行输入 gulp images 启动此任务

    gulp.task('images', function () {
        // 1. 找到图片
        gulp.src('images/*.*')
        // 2. 压缩图片
            .pipe(imagemin({
                progressive: true
            }))
        // 3. 另存图片
            .pipe(gulp.dest('img/images'))
    });
    // 在命令行使用 gulp auto 启动此任务
    gulp.task('auto', function () {
        // 监听文件修改，当文件被修改则执行 images 任务
        gulp.watch('images/*.*)', ['images'])
    });
    // 使用 gulp.task('default') 定义默认任务
    // 在命令行使用 gulp 启动 images 任务和 auto 任务
    gulp.task('default', ['images', 'auto'])