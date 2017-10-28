---
layout: notes
---


# Object 对象
## 修饰符
public--都可访问(公有)
private--类内可访问（私有)
protected--包内和子类可访问（保护）
不写(default)--包内可访问 （默认）
public > protected > default > private

## 面向对象特征   
### 封装
### 继承  Inherence 
extends 
### 多态 polymorphism
覆盖: 子类重新定义父类的虚函数的做法。
重载: 允许存在多个同名函数，而这些函数的参数表不同

# Process Thread 进程 线程
1. 一个Process 多个Thread
2. 一个Process 有共享内存
3. Thread 需要排队 使用部分 共享内存 
  1. Semaphore 信号量：容纳Thread数量
  2. Mutual exclusion (Mutex）只允许一个Thread

4. NodeJS 代码 单Process单Thread 

5. 异步非阻塞: 点餐 - 买水 - 点餐叫号(回调)


# MVC模式 – Model, View, Controller
<img src="zPhoto/MVC mode.png" height="300px" />
三者相互独立
Model
Ex：改变Model（数据库从MySQL移植到Oracle）

# Firebase - JS
```
<script src="https://www.gstatic.com/firebasejs/4.1.1/firebase.js"></script>
<script>
  // Initialize Firebase
  // TODO: Replace with your project's customized code snippet
  var config = {
    apiKey: "<API_KEY>",
    authDomain: "<PROJECT_ID>.firebaseapp.com",
    databaseURL: "https://<DATABASE_NAME>.firebaseio.com",
    storageBucket: "<BUCKET>.appspot.com",
    messagingSenderId: "<SENDER_ID>",
  };
  firebase.initializeApp(config);
</script>
```
## app






## auth
### firebase.auth().onAuthStateChanged
firebase.auth().onAuthStateChanged(function(user) {
  if (user) {
    // User is signed in.
  }
});




### firebase.auth().currentUser


### firebase.auth.GoogleAuthProvider();

## database 
###Reference 
###### 定位 specific location 
```
firebase.database().ref()
firebase.database().ref("users")
```

### DataSnapshot
read data 读取数据
on() 
once()
val()
##### child()
```
var ref = firebase.database().ref("users");
ref.once("value")
  .then(function(snapshot) {
   
    var user = snapshot.val(); 

    console.log(  user   );
    for( let prop in user) {
      console.log( prop + "=" + user[prop].email  ); 
    } 

  });
```
hasChild
numChildren() children的数量


### OnDisconnect
write data 写入修改

#####  set: 写入修改数据
```
var ref = firebase.database().ref("posts/-KuDAtI1ae8SbptMmRwK/author");
ref.onDisconnect().set("I disconnected!");
```
##### update 改变部分数据 
```
// Ex: 上线，下线 
var ref = firebase.database().ref("users/ada");
ref.update({
      status: "I'm online."
});
ref.onDisconnect().update({
   status: "I'm offline."
});
```
### goOnline()
```
firebase.database().goOnline();
```
###  goOffline()
```
firebase.database().goOnline();
```





## messaging 




## Storage


# Webpack
### Initial  全局安装
npm install -g webpack

### 安装到你的项目目录
npm install --save-dev webpack

### 创建文件 package.json 
npm init 

启动时自动运行命令 webpack

```
   "scripts": {
      "start": "webpack"
   },
```   
 创建文件 webpack.config.js 
 
```
module.exports = {
  entry:  __dirname + "/app/main.js",//已多次提及的唯一入口文件
  output: {
    path: __dirname + "/public",//打包后的文件存放的地方
    filename: "bundle.js"//打包后输出文件的文件名
  }
}
```
## Devtool – Source Map 
### source-map	
在一个单独的文件中产生一个完整且功能完全的文件。这个文件具有最好的source map，但是它会减慢打包速度；
### cheap-module-source-map
在一个单独的文件中生成一个不带列映射的map，不带列映射提高了打包速度，但是也使得浏览器开发者工具只能对应到具体的行，不能对应到具体的列（符号），会对调试造成不便；
###  eval-source-map	//中小型较常用
使用eval打包源文件模块，在同一个文件中生成干净的完整的source map。这个选项可以在不影响构建速度的前提下生成完整的sourcemap，但是对打包后输出的JS文件的执行具有性能和安全的隐患。在开发阶段这是一个非常好的选项，在生产阶段则一定不要启用这个选项；
### cheap-module-eval-source-map	
这是在打包文件时最快的生成source map的方法，生成的Source Map 会和打包后的JavaScript文件同行显示，没有列映射，和eval-source-map选项具有相似的缺点；
配置文件webpack.config.js
devtool: 'eval-source-map'

## Devserver 选项
### contentBase	
默认webpack-dev-server会为根文件夹提供本地服务器，如果想为另外一个目录下的文件提供本地服务器，应该在这里设置其所在目录（本例设置到“public"目录）
### port	
设置默认监听端口，如果省略，默认为”8080“
### inline	
设置为true，当源文件改变时会自动刷新页面
### historyApiFallback	
在开发单页应用时非常有用，它依赖于HTML5 history API，如果设置为true，所有的跳转将指向index.html

作者：zhangwang
链接：http://www.jianshu.com/p/42e11515c10f
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。


```
devServer: {
    contentBase: "./public",//本地服务器所加载的页面所在的目录
    historyApiFallback: true,  //不跳转
    inline: true  //实时刷新
}
``` 
## Loaders
打包过程中处理源文件(JSX，Scss，Less..)
webpack.config.js


1. test：一个用以匹配loaders所处理文件的拓展名的正则表达式（必须）
2. loader：loader的名称（必须）
3. include/exclude:手动添加必须处理的文件（文件夹）或屏蔽不需要处理的文件（文件夹）（可选）；
4. query：为loaders提供额外的设置选项（可选）

```
module.exports = {
    ...
    module: {
        rules: [
            {
                test: /(\.jsx|\.js)$/,
                use: {
                    loader: "babel-loader"
                },
                exclude: /node_modules/
            },
            {
                test: /\.css$/,
                use: [
                    {
                        loader: "style-loader"
                    }, {
                        loader: "css-loader",
                        options: {
                            modules: true
                        }
                    }, {
                        loader: "postcss-loader"
                    }
                ]
            }
        ]
    }
}
```

## Plugin 
### HtmlWebpackPlugin
npm install --save-dev html-webpack-plugin

### Hot Module Replacement
npm install --save-dev babel-plugin-react-transform react-transform-hmr













