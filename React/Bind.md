## React 使用ES6+语法时 事件绑定疑惑

第一种  
```javascript

_handleClick(e) {
    console.log(this);
}
render() {
    return (
        <div>
            <h1 onClick={this._handleClick.bind(this)}>点击</h1>
        </div>
    );
}
```

第二种  
```javascript
constructor(props) {
    super(props);
    this._handleClick = this._handleClick.bind(this)
}
_handleClick(e) {
    console.log(this);
}
render() {
    return (
        <div>
            <h1 onClick={this._handleClick}>点击</h1>
        </div>
    );
}
```

第三种 
```javascript
_handleClick = (e) => {
    // 使用箭头函数(arrow function)
    console.log(this);
}
render() {
    return (
        <div>
            <h1 onClick={this._handleClick}>点击</h1>
        </div>
    );
}
```
注释: 箭头函数需要在 编译的时候, 配置 支持 箭头函数参考文章   
http://babeljs.io/blog/2015/06/07/react-on-es6-plus/  
http://babeljs.io/blog/2015/10/31/setting-up-babel-6/  

第四种  
```javascript
_handleClick() {
    console.log(this);
}
render() {
    return (
        <div>
            <h1 onClick={::this._handleClick}>点击</h1>
        </div>
    );
}
```

第五种  
```javascript
import { autobind } from 'core-decorators'

@autobind
export default class Buy extends React.Component {

}
```