##排序数组 根据对象中某个键值排序

```javascript
const compare = id => {
  //根据id从小到大排序
  return function(a, b) {
    var value1 = a[id];
    var value2 = b[id];
    return value1 - value2;
  };
};
data.sort(compare('id'));
```

##取两个数组的交集/并集

```javascript
const arr1 = [1，2]；
const arr2 = [1, 2, 3];
const arr3 = arr2.filter(function(v) {
  return arr1.indexOf(v) !== -1; // 利用filter方法来遍历是否有相同的元素
});//先取交集 [1，2]
const result = arr2.concat(arr3).filter(function(v) {
  return arr2.indexOf(v) === -1 || arr3.indexOf(v) === -1;
});//后取并集 [3]
```
