# 整体配置

## 基础结构

初始化表格时，可以设置一个对象配置串`options`来自定义配置Luckysheet表格。

如下是一个简洁的配置案例：

```js
// 配置项
const options = {
    container: 'luckysheet', // 设定DOM容器的id
    title: 'Luckysheet Demo', // 设定表格名称
    lang: 'zh' // 设定表格语言

    // 更多其他设置...
}

// 初始化表格
luckysheet.create(options)
```

这里的`options`配置项会作用于整个表格，特别的，单个sheet的配置则需要在`options.data`数组中，分别设置对应更详细的参数，参考[工作表配置](/zh/guide/sheet.html)

## 配置项

以下为所有支持的设置参数

- [container](#container)
- [title](#title)
- [lang](#lang)
- [gridKey](#gridKey)
- [loadUrl](#loadUrl)
- [loadSheetUrl](#loadSheetUrl)
- [allowUpdate](#allowUpdate)
- [updateUrl](#updateUrl)
- [updateImageUrl](#updateImageUrl)
- [data](#data)
- [plugins](#plugins)
- [column](#column)
- [row](#row)
- [autoFormatw](#autoFormatw)
- [accuracy](#accuracy)
- [allowCopy](#allowCopy)
- [showtoolbar](#showtoolbar)
- [showtoolbarConfig](#showtoolbarConfig)
- [showinfobar](#showinfobar)
- [showsheetbar](#showsheetbar)
- [showsheetbarConfig](#showsheetbarConfig)
- [showstatisticBar](#showstatisticBar)
- [showstatisticBarConfig](#showstatisticBarConfig)
- [allowEdit](#allowEdit)
- [enableAddRow](#enableAddRow)
- [enableAddCol](#enableAddCol)
- [userInfo](#userInfo)
- [userMenuItem](#userMenuItem)
- [myFolderUrl](#myFolderUrl)
- [devicePixelRatio](#devicePixelRatio)
- [functionButton](#functionButton)
- [showConfigWindowResize](#showConfigWindowResize)
- [enablePage](#enablePage)
- [fullscreenmode](#fullscreenmode)
- [beforeCreateDom](#beforeCreateDom)
- [fireMousedown](#fireMousedown)
- [forceCalculation](#forceCalculation)
- [rightClickConfig](#rightClickConfig)

### container
- 类型：String
- 默认值："luckysheet"
- 作用：容器的ID
  
------------
### title
- 类型：String
- 默认值："Luckysheet Demo"
- 作用：表格的名称

------------
### lang
- 类型：String
- 默认值："en"
- 作用：国际化设置，允许设置表格的语言，支持中文("zh")和英文("en")

------------
### gridKey
- 类型：String
- 默认值：""
- 作用：表格唯一标识符

------------
### loadUrl
- 类型：String
- 默认值：""
- 作用：配置`loadUrl`的地址，Luckysheet会通过ajax请求整个表格数据，默认载入status为1的sheet数据中的所有`celldata`，其余的sheet载入除`celldata`字段外的所有字段。但是考虑到一些公式、图表及数据透视表会引用其他sheet的数据，所以前台会加一个判断，如果该当前sheet引用了其他sheet的数据则把引用到的sheet的数据一并补全。

------------
### loadSheetUrl
- 类型：String
- 默认值：""
- 作用：配置`loadSheetUrl`的地址，参数为`gridKey`（表格主键） 和 `index`（sheet主键合集，格式为`[1,2,3]`），返回的数据为sheet的`celldata`字段数据集合

------------
### allowUpdate
- 类型：Boolean
- 默认值：false
- 作用：是否允许操作表格后的后台更新，与`updateUrl`配合使用

------------
### updateUrl
- 类型：String
- 默认值：""
- 作用：操作表格后的后台更新地址，在`allowUpdate`为`true`时才会有效

------------
### updateImageUrl
- 类型：String
- 默认值：""
- 作用：缩略图的更新地址

------------
### data
- 类型：Array
- 默认值：[{ "name": "Sheet1", color: "", "status": "1", "order": "0", "data": [], "config": {}, "index":0 }, { "name": "Sheet2", color: "", "status": "0", "order": "1", "data": [], "config": {}, "index":1  }, { "name": "Sheet3", color: "", "status": "0", "order": "2", "data": [], "config": {}, "index":2  }]
- 作用：当未配置`loadUrl`和`loadSheetUrl`的时候，需要手动配置传入整个客户端所有sheet数据`[shee1, sheet2, sheet3]`，详细参数设置参见[工作表配置](/zh/guide/sheet.html)

------------
### plugins
- 类型：Array
- 默认值：[]
- 作用：配置插件，支持图表："chart"

------------
### column
- 类型：Number
- 默认值：60
- 作用：空表格默认的列数量

------------
### row
- 类型：Number
- 默认值：84
- 作用：空表格默认的行数据量

------------
### autoFormatw
- 类型：Boolean
- 默认值：false
- 作用：自动格式化超过4位数的数字为‘亿万格式’，例：true or "true" or "TRUE"

------------
### accuracy
- 类型：Number
- 默认值：undefined
- 作用：设置精度，小数点后的位数。传参数为数字或数字字符串，例： "0" 或 0

------------
### allowCopy
- 类型：Boolean
- 默认值：true
- 作用：是否允许拷贝

------------
### showtoolbar
- 类型：Boolean
- 默认值：true
- 作用：是否第二列显示工具栏

------------
#### showtoolbarConfig
- 类型：Object
- 默认值：{}
- 作用：自定义配置工具栏
- 格式：
    ```json
    {
        undoRedo: false, //撤销重做
        paintFormat: false, //格式刷
        currencyFormat: false, //货币格式
        percentageFormat: false, //百分比格式
        numberDecrease: false, // '减少小数位数'
        numberIncrease: false, // '增加小数位数
        moreFormats: false, // '更多格式'
        font: false, // '字体'
        fontSize: false, // '字号大小'
        bold: false, // '粗体 (Ctrl+B)'
        italic: false, // '斜体 (Ctrl+I)'
        strikethrough: false, // '删除线 (Alt+Shift+5)'
        textColor: false, // '文本颜色'
        fillColor: false, // '单元格颜色'
        border: false, // '边框'
        mergeCell: false, // '合并单元格'
        horizontalAlignMode: false, // '水平对齐方式'
        verticalAlignMode: false, // '垂直对齐方式'
        textWrapMode: false, // '换行方式'
        textRotateMode: false, // '文本旋转方式'
        frozenMode: false, // '冻结方式'
        sort: false, // '排序'
        filter: false, // '筛选'
        findAndReplace: false, // '查找替换'
        function: false, // '公式'
        conditionalFormat: false, // '条件格式'
        postil:  false, //'批注'
        pivotTable: false,  //'数据透视表'
        chart: false, // '图表'（图标隐藏，但是如果配置了chart插件，右击仍然可以新建图表）
        screenshot: false, // '截图'
        splitColumn: false, // '分列'        
    }
    ```

------------
### showinfobar
- 类型：Boolean
- 默认值：true
- 作用：是否显示顶部名称栏

------------
### showsheetbar
- 类型：Boolean
- 默认值：true
- 作用：是否显示底部表格名称区域

------------
### showsheetbarConfig
- 类型：Object
- 默认值：{}
- 作用：自定义配置底部表格名称区域
- 格式：
    ```json
    {
        add: false, //新增sheet  
        menu: false, //sheet管理菜单
        sheet: false //sheet页显示
    }
    ```

------------
### showstatisticBar
- 类型：Boolean
- 默认值：true
- 作用：是否显示底部计数栏

------------
### showstatisticBarConfig
- 类型：Object
- 默认值：{}
- 作用：自定义配置底部计数栏
- 格式：
    ```json
    {
        count: false, // 计数栏
        zoom: false // 缩放
    }

------------
### allowEdit
- 类型：Boolean
- 默认值：true
- 作用：是否允许前台编辑

------------
### enableAddRow
- 类型：Boolean
- 默认值：true
- 作用：允许增加行

------------
### enableAddCol
- 类型：Boolean
- 默认值：true
- 作用：允许增加列

------------
### userInfo
- 类型：String
- 默认值：`'<i style="font-size:16px;color:#ff6a00;" class="fa fa-taxi" aria-hidden="true"></i> rabbit'`
- 作用：右上角的用户信息展示样式

------------
### userMenuItem
- 类型：Array
- 默认值：`[{url:"www.baidu.com", "icon":'<i class="fa fa-folder" aria-hidden="true"></i>', "name":"我的表格"}, {url:"www.baidu.com", "icon":'<i class="fa fa-sign-out" aria-hidden="true"></i>', "name":"退出登陆"}]`
- 作用：点击右上角的用户信息弹出的菜单

------------
### myFolderUrl
- 类型：String
- 默认值："www.baidu.com"
- 作用：左上角<返回按钮的链接

------------
### devicePixelRatio
- 类型：Number
- 默认值：window.devicePixelRatio
- 作用：设备比例，比例越大表格分辨率越高

------------
### functionButton
- 类型：String
- 默认值：""
- 作用：右上角功能按钮，例如`'<button id="" class="btn btn-primary" style="padding:3px 6px;font-size: 12px;margin-right: 10px;">下载</button>    <button id="" class="btn btn-primary btn-danger" style="    padding:3px 6px;    font-size: 12px;    margin-right: 10px;">分享</button>    <button id="luckysheet-share-btn-title" class="btn btn-primary btn-danger" style="    padding:3px 6px;    font-size: 12px;    margin-right: 10px;">秀数据</button>'`

------------
### showConfigWindowResize
- 类型：Boolean
- 默认值：true
- 作用：图表或数据透视表的配置会在右侧弹出，设置弹出后表格是否会自动缩进

------------
### enablePage
- 类型：Boolean
- 默认值：false
- 作用：允许加载下一页

------------
### fullscreenmode
- 类型：Boolean
- 默认值：true
- 作用：是否全屏模式。非全屏模式下，标记框不会强制选中

------------
### beforeCreateDom
- 类型：Function
- 默认值：null
- 作用：表格创建之前自定义方法

------------
### fireMousedown
- 类型：Function
- 默认值：null
- 作用：单元格数据下钻自定义方法

------------
### forceCalculation
- 类型：Boolean
- 默认值：false
- 作用：强制刷新公式。

    默认情况下，为提高加载性能，表格初始化的时候，含有公式的单元格会默认直接取得`v`和`m`作为数据结果，而不做实时计算。
    
    如果公式关联到的单元格数据已经变化，或者公式所在的单元格数据结果改变了，则会导致关联单元格应该计算得出的结果和实际显示结果不一致，这是就需要开启公式刷新，保证数据实时计算的准确性。
    
    ⚠️提醒，公式较多时会有性能问题，慎用！

------------
### rightClickConfig
- 类型：Object
- 默认值：{}
- 作用：自定义配置右击菜单
- 格式：
    ```json
    {
        copy:false, // '复制'
        copyAs:false, // '复制为'
        paste:false, // '粘贴',
        insert:false, // '插入',
        delete:false, // '删除',
        hide:false, // '隐藏',
        deleteCell:false, // '删除单元格',
        clear:false, // '清除内容',
        matrix:false, // '矩阵操作选区',
        sort:false, // '排序选区',
        filter:false, //'筛选选区',
        chart:false, // '图表生成',
    }

## 钩子函数

钩子函数应用于二次开发时，会在各个常用鼠标或者键盘操作时植入钩子，调用开发者传入的函数，起到扩展Luckysheet功能的作用。

钩子函数统一配置在`options.hook`下，可以分别针对单元格、sheet页、表格创建配置hook

### cellHover
- 类型：Function
- 默认值：null
- 作用：鼠标移过单元格时(hover)触发
- 参数：
	- {Number} [r]: 单元格所在行数
	- {Number} [c]: 单元格所在列数
	- {Object} [v]: 单元格对象

------------

### cellClickBefore
- 类型：Function
- 默认值：null
- 作用：点击单元格前触发，即在点击单元格的时候，最先触发这个方法

------------

### cellClickAfter
- 类型：Function
- 默认值：null
- 作用：点击单元格后触发，即在点击单元格的时候，最后触发这个方法

------------

### sheetClickBefore
- 类型：Function
- 默认值：null
- 作用：点击sheet页前触发

------------

### sheetClickAfter
- 类型：Function
- 默认值：null
- 作用：点击sheet页后触发

------------

### sheetClickAfter
- 类型：Function
- 默认值：null
- 作用：点击sheet页后触发

------------
