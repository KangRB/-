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
