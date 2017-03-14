## componentDidMount:  
在组件第一次render之后调用，这时组件对应的DOM节点已被加入到浏览器。在这个方法里可以去实现一些初始化逻辑。

## componentWillUnmount:  
在DOM节点移除之后被调用，这里可以做一些相关的清理工作。

## shouldComponentUpdate:  
这是一个和性能非常相关的方法，在每一次render方法之前被调用。它提供了一个机会让你决定是否要对组件进行实际的render。例如：
```bash
shouldComponentUpdate(nextProps, nextState) {
  return nextProps.id !== this.props.id;
}
```

[推荐阅读地址：https://segmentfault.com/a/1190000004490882](https://segmentfault.com/a/1190000004490882)

## Demo 案例
```bash
import React from 'react';
import { Link } from 'react-router';

export class AboutView extends React.Component {
  constructor(props){
    super(props);
    this.state = {
      name : ''
    }
  }
  handelclick(){
    this.setState({
      name : '展示效果'
    });
  }
  componentWillMount(){
    console.group('componentWillMount');
    console.log('服务器端和客户端都只调用一次，在初始化渲染执行之前立刻调用。如果在这个方法内调用 setState，render() 将会感知到更新后的 state，将会执行仅一次，尽管 state 改变了。');
    console.groupEnd();
  }
  componentDidMount(){
    console.group('componentDidMount');
    console.log('在初始化渲染执行之后立刻调用一次，仅客户端有效（服务器端不会调用）。在生命周期中的这个时间点，组件拥有一个 DOM 展现，你可以通过 this.getDOMNode() 来获取相应 DOM 节点.\n如果想和其它 JavaScript 框架集成，使用 setTimeout 或者 setInterval 来设置定时器，或者发送 AJAX 请求，可以在该方法中执行这些操作。');
    console.groupEnd();
  }
  componentWillReceiveProps(){
    console.group('componentWillReceiveProps');
    console.log('在组件接收到新的 props 的时候调用。在初始化渲染的时候，该方法不会调用。\n用此函数可以作为 react 在 prop 传入之后， render() 渲染之前更新 state 的机会。老的 props 可以通过 this.props 获取到。在该函数中调用 this.setState() 将不会引起第二次渲染。');
    console.groupEnd();
  }
  shouldComponentUpdate(){
    return true;
    console.group('shouldComponentUpdate');
    console.log('在接收到新的 props 或者 state，将要渲染之前调用。该方法在初始化渲染的时候不会调用，在使用 forceUpdate 方法的时候也不会。\n如果确定新的 props 和 state 不会导致组件更新，则此处应该 返回 false。如果 shouldComponentUpdate 返回 false，则 render() 将不会执行，直到下一次 state 改变。（另外，componentWillUpdate 和 componentDidUpdate 也不会被调用。）\n默认情况下，shouldComponentUpdate 总会返回 true，在 state 改变的时候避免细微的 bug，但是如果总是小心地把 state 当做不可变的，在 render() 中只从 props 和 state 读取值，此时你可以覆盖 shouldComponentUpdate 方法，实现新老 props 和 state 的比对逻辑。\n如果性能是个瓶颈，尤其是有几十个甚至上百个组件的时候，使用 shouldComponentUpdate 可以提升应用的性能。');
    console.groupEnd();
  }
  componentWillUpdate(){
    console.group('componentWillUpdate');
    console.log('在接收到新的 props 或者 state 之前立刻调用。在初始化渲染的时候该方法不会被调用。\n使用该方法做一些更新之前的准备工作。你不能在刚方法中使用 this.setState()。如果需要更新 state 来响应某个 prop 的改变，请使用 componentWillReceiveProps。');
    console.groupEnd();
  }
  componentDidUpdate(){
    console.group('componentDidUpdate');
    console.log('在组件的更新已经同步到 DOM 中之后立刻被调用。该方法不会在初始化渲染的时候调用。\n使用该方法可以在组件更新之后操作 DOM 元素。');
    console.groupEnd();
  }
  componentWillUnmount(){
    console.group('componentWillUnmount');
    console.log('在组件从 DOM 中移除的时候立刻被调用。\n在该方法中执行任何必要的清理，比如无效的定时器，或者清除在 componentDidMount 中创建的 DOM 元素。');
    console.groupEnd();
  }

  render () {
    console.log(this.state.name);
    return (
      <div className="mt44 page">
        <h1 className="page-tit" onClick={this.handelclick.bind(this)}>AboutView</h1>
      </div>
    );
  }
}

export default AboutView;
```
