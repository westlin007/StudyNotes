#node中req.params,req.query,req.body三者的区别

其中`req.params`,`req.query`是用在get请求当中,`req.body`是用在post请求当中

##1.req.params
所对应的url长这个样子  http://localhost:3000/10
```js
app.get("/:id",function (req,res) {
	res.send(req.params["id"]);
});
```

就是把请求 / 后面的参数当成id，通过req.params就能获取到id，返回页面也就是10

##2.req.query
所对应的url长这个样子http://localhost:3000/?id=10

```js
app.get("/",function (req,res) {
    res.send(req.query["id"]);
});
```

```js
app.get("/",function (req,res) {
    console.log(req.query);     //{id=10}
    console.log(req.query.id);  // 10
});
```

req.query也就是指url问号后面带的数据

##3.req.body
req.body是用在post请求当中的
用法如下
```js
const express = require('express');
const router = express.Router();
router.post('/login',function(req,res,next){
  let name = req.body.name;
  let password = req.body.password;
  console.log(name);
  if(name == 'goudan' && password == '8888'){
    res.send('登录成功')
  }
})
```


从中可以看出get请求和post请求的区别，get接受参数使用req.query,而post接受参数使用req.body
