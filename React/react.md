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

##antD 日期选择器 限制时间选择范围
```javascript
disabledDate = current => {
  // 限制时间选择范围在活动时间范围内
  return current && current < moment(new Date(this.props.startTime))||current>moment(new Date(this.props.endTime))
}
disabledRangeTime = (_, type) => {
  // 限制时间选择范围在活动时间范围内
  const range = (start, end) => {
    const result = []
    for (let i = start; i < end; i++) {
      result.push(i)
    }
    return result
  }
  if (type === 'start') {
    return {
        disabledHours: () => range(1,moment(this.props.startTime).get('hours')+1),
        disabledMinutes: () => range(1,moment(this.props.startTime).get('miuntes')+1),
        disabledSeconds: () => range(1,moment(this.props.startTime).get('seconds')+1)
      }
    }
    return {
      disabledHours: () => range( moment(this.props.endTime).get('hours')+1,24),
      disabledMinutes: () => range( moment(this.props.endTime).get('minutes')+1,60),
      disabledSeconds: () => range( moment(this.props.endTime).get('seconds')+1,60)
    }
}
```
## antd上传图片 限制格式、大小、尺寸
```javascript
  isSize = (file, height) => {
    return new Promise((resolve, reject) => {
      let _URL = window.URL || window.webkitURL;
      let img = new Image();
      img.onload = function () {
        let valid = img.height < height
        valid ? resolve() : reject()
      };
      img.src = _URL.createObjectURL(file)
    }).then(
      () => {
        return file;
      },
      () => {
        message.error(`${file.name}图片尺寸不符合要求，请修改后重新上传！`)
        return Promise.reject()
      }
    )
  }
  beforeUpload={(file) => {
    const isJPG = file.type === 'image/jpeg';
    const isPNG = file.type === 'image/png';
    const isBMP = file.type === 'image/bmp';
    const isGIF = file.type === 'image/gif';
    const isWEBP = file.type === 'image/webp';
    const isPic = isJPG || isPNG || isBMP || isGIF || isWEBP;
    if (!isPic) {
      message.error('只能上传图片');
      this.setState({ uploadList: { fileList: [] } })
    }
    const isLt500k = file.size / 1024 / 1024 < 0.5;
    const isSize = this.isSize(file, 60)
    if (!isLt500k) {
      message.error('图片大小不能超过500k!');
      this.setState({ uploadList: { fileList: [] } })
    }
    if (!isSize) {
      message.error('高不得小于60px!');
      this.setState({ uploadList: { fileList: [] } })
    }
    if (isPic && isLt500k && isSize) {
      this.setState({ uploadList: {} })
    }
    return isPic && isLt500k && isSize;
  }}
```

## antd 实时监控页面表单验证错误项
getFieldsError('form-item的name')
此方法返回一个包含验证信息的数组

####input禁止输入空格
```javascript
  getValueFromEvent: (event) => {
    return event.target.value.replace(/\s+/g, "")
  },
```