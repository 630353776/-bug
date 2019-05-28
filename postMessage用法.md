# postMeaage 用法
##### postMessage用来解决跨域，跨窗口消息传递（可用于iframe传值）

###### postMessage(data,origin)方法接受两个参数
* data:要传递的数据，html5规范中提到该参数可以是JavaScript的任意基本类型或可复制的对象，然而并不是所有浏览器都做到了这点儿，部分浏览器只能处理字符串参数，所       以我们在传递参数的时候需要使用JSON.stringify()方法对对象参数序列化，在低版本IE中引用json2.js可以实现类似效果。
* origin：字符串参数，指明目标窗口的源，协议+主机+端口号[+URL]，URL会被忽略，所以可以不写，这个参数是为了安全考虑，postMessage()方法只会将message传递给指        定窗口，当然如果愿意也可以建参数设置为"*"，这样可以传递给任意窗口，如果要指定和当前窗口同源的话设置为"/"。

###### 用法
1、子页面向父页面发送消息
```
var parentData = {type: 'passDataBack', data: passData};
window.parent.postMessage(parentData, '*');
```
 
2、父页面向子页面发送消息
```
var data = {type: 'answerResult', data: jsonData.data};
$(".courseware_h5 iframe")[0].contentWindow.postMessage(data, '*');
```
 
3、接收消息方法
```
window.addEventListener('message', function (e) {
})
```