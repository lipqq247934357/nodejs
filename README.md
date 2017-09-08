# nodejs
nodejs
关于nodejs部署几个自己注意的点：
1.session共享使用 的是redis
在使用session-redis之前先使用express-session
然后再安装connect-redis中间件
然后配置如下:
var options = {
    host: "127.0.0.1",
    port: 6379,
    "ttl": 60 * 60 * 24 * 30,   //Session的有效期为30天
}
app.use(session({
    store: new RedisStore(options),
    resave:false,
    saveUninitialized:true,
    secret: 'lipeng',
}));
关于axios的说明：在response对象中获取data属性为返回的数据值
关于快速重启express的说明：使用supervisor
具体：npm install  supervisor global
然后到项目目录下执行：supervisor ./bin/www命令
