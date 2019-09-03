##排序数组 根据对象中某个键值排序
```javascript
const compare=(id)=>{
  //根据id从小到大排序
  return function(a,b){
      var value1 = a[id];
      var value2 = b[id];
      return value1 - value2;
  }
}
data.sort(compare('id'))
```