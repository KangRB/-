##iconfont 旋转
需要将其 dispaly 设置为 block 或 inline-block

##X 号 关闭

```css
.x {
  position: relative;
  width: 20px;
  height: 20px;
  display: inline-block;
  cursor: pointer;
}

.x::before {
  content: '';
  width: inherit;
  border-top: 2px solid #d8d8d8;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%) rotate(45deg);
}

.x::after {
  content: '';
  width: inherit;
  border-top: 2px solid #d8d8d8;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%) rotate(-45deg);
}
```

## 一行文本超出省略/多行省略

```css
.text-hide {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
.two-line {
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  /* autoprefixer: off */
  -webkit-box-orient: vertical;
  /* autoprefixer: on */
}
```
