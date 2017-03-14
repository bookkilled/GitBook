# 忘掉jQuery，使用JavaScript原生API
（供wap端）以下是jQuery和JavaScript实现相同操作的等价代码
## 选择元素
```bash
//jQuery
var ele = $(".ele");

//javascript
var ele = document.querySelectAll('.ele');

//函数法
var $ = function(ele){
    return document.querySelectAll(ele);
}

var ele = $('.ele'); //调用
```
## 创建元素
```bash
//jquery
var newEle = $('<div>xxx</div>');

//javascript
var newEle = document.createElement('<div>xxx</div>');
```
## 添加事件监听
```bash
//jQuery
$('.ele').on('click',function(){

});

//javascript
[].forEach.call(document.querySelectAll('.ele'),function(ele){
    ele.addEventListener('click',function(){
    },false);
})
```
## 设置/获取属性
```bash
//jQuery
$('.ele').attr('key','value');
$('.ele').attr('key');

//javascript
document.querySelector('.ele').setAttribute('key','value');
document.querySelector('.ele').getAttribute('key');
```
## 添加/移除/切换类
```bash
//jQuery
$('.ele').addClass('class');
$('.ele').removeClass('class');
$('.ele').toggleClass('class');

//javascript
document.querySelector('.ele').classList.add('class');
document.querySelector('.ele').classList.remove('class');
document.querySelector('.ele').classList.toggle('class');
```
## 附加内容（Append）
```bash
//jquery
$('.ele').append('<div>xxx</div>');

//javascript
document.querySelector('.ele').appendChild(document.createElement('<div>xxx</div>'));
```
## 克隆元素
```bash
//jQuery
var cloneEle = $('.ele').clone();

//javascript
var cloneEle = document.querySelector('.ele').cloneNode(true);
```
## 移除元素
```bash
//jQuery
$('.ele').remove();

//javascript
remove('.ele');

function remove(ele){
    var toRemove = document.querySelector(ele);
    toRemove.parentNode.removeChile(toRemove);
}
```
## 获取父元素
```bash
//jQuery
$('.ele').parent();

//javascript
document.querySelector('.ele').parentNode;
```
## 上一个/下一个元素
```bash
//jQuery
$('.ele').prev();
$('.ele').next();

//javascript
document.querySelector('.ele').previousElementsibling;
document.querySelector('.ele').nextElementSibling;
```
## XHR或AJAX
```bash
//jQuery
$.get('url',function(data){

})
$.post('url',{data: data},function(){

})
$.ajax({name:value, name:value, ... })

//javascript
//get
var xhr = new XMLHttpRequest();

xhr.open('GET',url);
xhr.onreadystatechange = function(data){

}
xhr.send();

//post
var xhr = new XMLHttpRequest();

xhr.open('POST',url);
xhr.onreadystatechange = function(data){

}
xhr.send({data: data});

// ajax
// 使用reqwest完成异步请求 https://github.com/ded/reqwest
reqwest({
    method: 'GET',
    url: this.HOST_URL + '/fmall/Yeah/sendGift',
    type: 'jsonp',
    data: {
        mobile: '13122557296',
        sid: xid,
        seccode: 'xyyq',
        channel: 1
    },
    success: function (res) {
        console.log(res);
    }
})
.then(function(res){ // then 传两个参数fuc 第一个success 第二个fail
  console.log('then:-----------');
  console.log(res);
},function(err){})
.always(function(res){
  console.log('always:------------');
})
.fail(function (err, msg) {
  console.log(msg);
});
```
