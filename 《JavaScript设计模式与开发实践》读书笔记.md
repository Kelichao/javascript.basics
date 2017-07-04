# 如何科学使用多态

- 多态的最根本好处在于，你不必再向对象询问“你是什么类型”而后根据得到的答
案调用对象的某个行为——你只管调用该行为就是了，其他的一切多态机制都会为你安
排妥当。

> 普通写法

```js
var googleMap = {
    show: function(){
    console.log( '开始渲染谷歌地图' );
    }
};
var baiduMap = {
    show: function(){
    console.log( '开始渲染百度地图' );
    }
};

// 函数以字符串形式的传参形式
// 如果判断条件一旦增多，就会变全是if-else语句
var renderMap = function( type ){
    if ( type === 'google' ){
        googleMap.show();
    }else if ( type === 'baidu' ){
        baiduMap.show();
    }
};

renderMap( 'google' ); // 输出：开始渲染谷歌地图
renderMap( 'baidu' ); // 输出：开始渲染百度地图
```

> 改进写法

```js
// 将render传入的参数换成相应的对象
var renderMap = function( map ){
    if ( map.show instanceof Function ){
        map.show();
    }
};

renderMap( googleMap ); // 输出：开始渲染谷歌地图
renderMap( baiduMap ); // 输出：开始渲染百度地图
```
