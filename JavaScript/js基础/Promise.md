#Promise

---

##异步编程
- fs文件操作
- 数据库操作
- 网络请求AJAX 
- 定时器

##Promise使用

###util.promisify()
将一个方法进行promise风格转化

###Promise的状态

实例对象中的一个属性`PromiseState`
* pending: 未决定的
* resolved / fulfilled: 成功
* rejected: 失败

###### 状态修改
* resolve(fulfilled状态)
* reject(rejected状态)
* throw(rejected状态)


###Promise对象的值
实例对象中的另一个属性`PromiseResult`
，保存着对象（成功 / 失败）的结果
* resolve
* reject 


###Promise.all(promiseArr)
输入是多个Promise对象组成的数组。

返回一个新的Promise。只有所有的输入Promise都resolve才返回成功

只要一个Promise的状态是resolve就返回失败。并且失败的结果值是第一个失败Promise返回的结果值。

###Promise.race(promiseArr)
输入是多个Promise对象组成的数组。

返回一个新的Promise。第一个完成的Promise的结果状态是最终的结果状态。


###Promise串联多个操作任务
Promise的`then()`返回一个新的Promise对象，
可以使用`then()`的链式调用。

`then()`返回的Promise对象的状态由回调函数的返回值决定。

返回普通值算`fulfilled`

异常穿透：在链式`then()`最后加`catch()`捕捉异常即可。

######中断promise链
返回一个`pending`状态的promise对象。
```javascript
return new Promise(() => {});
```

###实例


封装AJAX
```javascript
function sendAJAX(url) {
    return new Promise((resolve, reject) => {
        const xhr  = new XMLHttpRequest();
        xhr.open("GET", url);
        xhr.send();

        xhr.onreadystatechange = function() {
            if(xhr.readyState === 4) {
                if (xhr.status >= 200 && xhr.status < 300) {
                    resolve(xhr.response);
                } else {
                    reject(xhr.status);
                }
            }
        }
    });
}
```


