##React 动态设置 state

> 需要在设置的 state 值外加[ ]

栗子：

```javascript
data.map((v, k) => {
  this.setState({
    [v.name]: v.data
  });
});
```

##子组件监听 props 变化

```javascript
componentDidUpdate(prevProps){
  if(prevProps.item.width!==this.state.width){
    this.setState({
      width:prevProps.item.width,
    })
  }
}

```
