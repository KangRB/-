##iconfont 旋转
需要将其 dispaly 设置为 block 或 inline-block

##X号 关闭
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
  border-top: 2px solid #D8D8D8;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%) rotate(45deg);
}

.x::after {
  content: '';
  width: inherit;
  border-top: 2px solid #D8D8D8;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%) rotate(-45deg);
}
```