# file-loader
用于上传文件的Vue组件<br>
用此组件包裹你的视图 即可在点击它/拖拽文件时将文件信息存至浏览器<br>
组件接受四个参数 一个事件<br>
<file-loader
    accept='*' 同input的属性 默认'*'
    :mutiple='false' 同input的属性 默认false
    capture='user'同input的属性 默认'user'
    :drag='true' 是否允许拖拽上传 默认true
    @load='fun' 用户选择文件后fun得到filesValue作为参数 filesValue为fileList类型 为用户已经选择的文件
                还具有一个函数属性 toFormData
                toFormData接受一个对象extraData作为参数 返回值为表单
                函数将filesValue的所有文件和extraData的所有key和对应的value依次插入表单
>
</file-loader>