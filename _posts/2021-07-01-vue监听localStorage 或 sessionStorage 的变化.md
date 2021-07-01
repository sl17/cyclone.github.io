---
published: false
---
## vue监听localStorage 或 sessionStorage 的变化

#### 在maim.js里面
给 Vue.protorype 注册一个全局方法，然后创建一个 StorageEvent 方法，当我在执行sessionStorage.setItem(k, val) 的时候，初始化事件并派发事件。
```
/*
 * @param { number } type 1 localStorage 2 sessionStorage
 * @param { string } key 键
 * @param { string } data 要存储的数据
*/ 
Vue.prototype.$addStorageEvent = function (type, key, data) {
    if (type === 1) {
        // 创建一个StorageEvent事件
        var newStorageEvent = document.createEvent('StorageEvent');
        const storage = {
            setItem: function (k, val) {
                localStorage.setItem(k, val);
                // 初始化创建的事件
                newStorageEvent.initStorageEvent('setItem', false, false, k, null, val, null, null);
                // 派发对象
                window.dispatchEvent(newStorageEvent);
            }
        }
        return storage.setItem(key, data);
    } else {
        // 创建一个StorageEvent事件
        var newStorageEvent = document.createEvent('StorageEvent');
        const storage = {
            setItem: function (k, val) {
                sessionStorage.setItem(k, val);
                // 初始化创建的事件
                newStorageEvent.initStorageEvent('setItem', false, false, k, null, val, null, null);
                // 派发对象
                window.dispatchEvent(newStorageEvent);
            }
        }
        return storage.setItem(key, data);
    }
}
```

#### 在获取token的组件里
```
created() {
  window.addEventListener("setItem", (e) => {
    console.log(e)
    this.token = e && e.newValue;
  });
},
```
#### 在设置token的组件里
```
methods:{
   setToken(){
      this.$addStorageEvent(1, "token", '');
   }
},
or
created() {
	this.$addStorageEvent(1, "token", '');
},
```

