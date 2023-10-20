# file-loader
用于上传文件的Vue组件<br>
用此组件包裹你的视图 即可在点击它/拖拽文件时将文件信息存至浏览器<br>
组件接受四个参数:<br>
accept 同input的属性 默认'*'<br>
mutiple 同input的属性 默认false<br>
capture 同input的属性 默认'user'<br>
drag 是否允许拖拽上传 默认true<br>
拥有一个事件:<br>
load 用户选择文件后 以filesValue为参数触发事件 filesValue为fileList类型 为用户已经选择的文件<br>
    还具有一个函数属性 toFormData<br>
    toFormData接受一个对象extraData作为参数 返回值为表单<br>
    函数将filesValue的所有文件和extraData的所有key和对应的value依次插入表<br>
```html
<file-loader
    accept=''
    :mutiple='false'
    capture='user'
    :drag='true'
    @load='fun' 
    >
</file-loader>
```