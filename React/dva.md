## 添加新状态和引入和更改

####1.设置中间件

```javascript
const setListSetup = (props, advanced) => {
  const { dispatch } = props;
  dispatch({
    type: 'management/saveListSetup',
    payload: {
      advanced
    }
  });
};
export { setListSetup };
```

####2.在已经注册过的配置文件里添加 reducers 和 effects 并在 state 里添加需要的状态

```javascript
export default {
  namespace: 'management',
  state: {
    list: [],
    loading: false,
    hasData: true
  },
  reducers: {
    setListSetup(state, action) {
      const { advanced } = action;
      return {
        ...state,
        ...advanced
      };
    }
  },
  effects: {
    *saveListSetup({ payload }, { pat, call }) {
      const { advanced } = payload;
      yield put({
        type: 'setListSetup',
        advanced
      });
    }
  },
  subscriptions: {}
};
```

####3.1 在需要使用状态的组件里 connect 连接

```javascript
export default connect(state => {
  return {
    list: state.management.list,
    loading: state.management.loading,
    hasData: state.management.hasData
  };
})(List); //List为这个组件
```

####3.2 在需要设置状态值的文件里

> 首先引入中间件

```javascript
import { setListSetup } from '../config/listSetup';
```

> 然后便可以更新数据

```javascript
setListSetup(props, {
  loading: false,
  hasData: true
});
```
