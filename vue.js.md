//单页面安装环境
    创建一个(新建文件夹)

    全局安装 vue-cli
    npm install  vue-cli   //全局安装 vue-cli
    【//如需本地安装(npm install -g vue-cli)】
    npm install -g vue-cli
    vue init webpack [Name如(vue-abc)] //创建一个基于 "webpack" 模板的新项目
    cd vue-abc          //进入vue-abc
    npm install         //安装依赖 node_modules
    npm run dev         ////运行项目
    npm run build       //生成正常HTML文本
    
    项目内如有【node_modules】则不上传，
    在根目录创建【.gitignore】文件，
    再在文件内 写上文件名 【node_modules】 或者 文件名  则不会上传

//使用路由构建单页面

    安装路由：npm install vue-router

//严格按照以下程序操作

    1.在【main.js】中 添加
        var Vue = require('vue');
        var VueRouter = require('vue-router');          //创建路由
        var Hello = require('./components/Hello.vue');  //创建组件Hello
        var One = require('./components/One.vue');      //创建组件One
        var Two = require('./components/Two.vue');      //创建组件Two
        var Three = require('./components/Three.vue');  //创建组件Three
        var AppIndex = require('./App.vue');            //创建组件App
        Vue.use(VueRouter)
        //【 var Foo = Vue.extend({
        //  template: '<p>这是一个连接！</p>'
        // })】
        var App = Vue.extend({})
        var router = new VueRouter()
        router.map({
            '/': {                      连接根目录
                component: AppIndex 
            },
            '/hello': {                 连接hello
                component: Hello
            },
            '/one': {                   连接one
                component: One
            },
            '/two': {                   连接two
                component: Two
            },
            '/three': {                 连接three
                component: Three
            },
            // 【'/': {
            //  component: function (AppIndex) {
            //      require(['./App.vue'], AppIndex)
            //  }
            // },】
        })
        router.start(App, '#app')
        //启动应用.路由器会创建一个App实例，并且挂载到选择符#app匹配的元素上
    2在【components】中创建Hello.vue,One.vue,Two.vue,Three.vue等文本
    3在【index.html】中添加:<app></app
                            <div id="app">
                                <router-view></router-view>
                            </div





//运行错误(1)

    原因：Error: Cannot find module 'express'//这句意思是没有找到 'express'模块
    解决方法：1.rm -rf node-modules  //先删除
              2.npm install  //在安装
              3.npm run dev  //再运行


