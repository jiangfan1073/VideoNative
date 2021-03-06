## 总览
控件的属性表格的类型定义

+ Property：属性，可以写在 style 里面，也可以用 class 引用 vnss 脚本里的样式表
+ Method：JS 侧可调用的方法
+ EventHandle：事件回调给 JS 侧的方法


## 通用事件

+ 代码示例：

```js
/**commonEvent.js**/
Page ({
    onTextTap: function (params) {
        var clickStr = "文本被点击";
        console.log(clickStr);
    },
    onLaunch: function () {
        console.log('页面加载完成')
    },
    onPageResult: function (params) {
        console.log('从前一个页面返回， 参数为：' + JSON.stringify(params));
    }
});
```

```html
<!--commonEvent.vnml-->
<view class="container">
    <text width="100%" height="auto" bindTap="onTextTap">可点击文本</text>
</view>
```

事件 Key | 事件类型 | 适用范围 | 参数 Key | 参数类型
--- | --- | --- | --- | ---
bindTap | 点击 | 所有控件 | |
onPageResult(Object params) | 从前一个页面返回 | 页面 | 拉起的页面传递过来的参数 | Object
onLaunch(Object params) | 当前页面启动 | 页面 | 上个页面传递过来的参数 | Object/String
onStart() | 当前页面进入前台 | 页面 |  | 
onStop() | 当前页面进入后台 | 页面 |  | 
onDestroy() | 当前页面即将销毁 | 页面 |  | 
onOrientationChange(int orientation) |  当前页面方向改变 | 页面 | 选项的角度如：0,-90,90 | Integer
 

## 通用属性

+ 代码示例如下：
```html
<!--commonAttribute.vnml-->
<view id="mainContainer">
    <view width="100%" height="75rpx" margin="5rpx" background-color="#FFFFFFFF">
      <text width="75rpx" height="75px" padding="3rpx">
         通用属性
      </text>
    </view>
</view>
```

通用属性名 | 类型 | 默认值 | 说明
--- | --- | --- | --- 
class | String | none | 引用 vnss 中的样式类；多个样式可用空格分割
id | String | none | 主要用于做 CSS 匹配
width | [rpx percent auto] | auto |
height | [rpx percent auto] | auto |
aspect-ratio | Float | | 宽高比
background-stretch-param | [rpx 组合] | | 1.25rpx 15rpx (将对图片(15,25)坐标点进行拉伸) 2.25rpx 10rpx 22rpx 15rpx (将对图片的纵坐标25位置到35位置进行拉伸，并对横坐标22位置到37位置进行拉伸)
background-color | color | #FFFFFFFF | 取值格式为#RGBA，如果同时设置了background，background的优先级更高
background | String | "" | 1.不拉伸的图片如:../image/btn_bg
alpha | Float | 1 | 0:透明 到 1:不透明
padding | [rpx percent 组合] | 0rpx | 参见 CSS 标准写法
padding-left | [rpx percent] | | 共存时覆盖 padding 的值
padding-right | [rpx percent] | | 共存时覆盖 padding 的值
padding-top | [rpx percent] | | 共存时覆盖 padding 的值
padding-bottom | [rpx percent] | | 共存时覆盖 padding 的值
margin | [rpx percent 组合] | 0rpx | 参见 CSS 标准写法
margin-left | [rpx percent] | | 共存时覆盖 margin 的值
margin-right | [rpx percent] | | 共存时覆盖 margin 的值
margin-top | [rpx percent] | | 共存时覆盖 margin 的值
margin-bottom | [rpx percent] | |共存时覆盖 margin 的值
border-width | rpx | 0rpx | 暂不支持
border-style | Enum | none | 暂不支持
border-color | color | #000000FF | 暂不支持
border-radius | rpx | 0rpx |暂不支持
max-height | [rpx percent] | |
max-width | [rpx percent] | |
min-height | [rpx percent] | |
min-width | [rpx percent] | |
hidden | Boolean | false | 是否隐藏
enable | Boolean | true | 是否启用，为 false 时不接收点击事件

## view

+ 代码示例如下：
```html
<!--view.vnml-->
<view width="100%" height="85.4rpx" align-items="center"  justify-content="space-between" flex-direction="row">
    <image height="60rpx" width="95rpx" src="{{iconUrl}}" />
    <text height="100%" width="95rpx" font-size="30rpx"></text>
</view>
```

类型 | 属性/事件/方法名 | 参数类型 | 参数默认值 | 说明
--- | --- | --- | --- | ---
Property | align-content | Enum | stretch |
Property | align-items | Enum | stretch | 
Property | flex-direction | Enum | row | 弹性布局的方向
Property | flex-wrap | Enum | nowarp | 行属性
Property | justify-content | Enum | flex-start |

关于 FlexboxLayout 的详细属性定义，请参见: [CSSFlexibleBoxLayout](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout)

## flex 子视图

+ 代码示例如下：
```html
<!--subView.vnml-->
<view width="100%" height="auto" flex-direction="row" align-items="center">
    <image width="200rpx" aspect-ratio="1.7" src="{{url}}" position-type="absolute" />
    <text height="auto" width="auto" flex-grow="1" font-size="30rpx">{{firstLine}}</text>
</view>
```

类型 | 属性/事件/方法名 | 参数类型 | 参数默认值 | 说明
--- | --- | --- | --- | ---
Property | align-self | Enum | auto |
Property | flex-basis | [Enum Float] | auto | 初始大小
Property | flex-grow | Float | 0 | 拉伸因子
Property | flex-shrink | Float | 1 | 收缩规则
Property | position-type | Enum | relative | relative/absolute

## text和button

+ 代码示例如下：
```html
<!--text.vnml-->
<view width="100%" height="auto" flex-direction="row">
    <text height="auto" width="auto" font-size="30rpx" color="#000000FF" font-style="bold" text-align="center">精彩瞬间</text>
</view>
```

类型 | 属性/事件/方法名 | 参数类型 | 参数默认值 | 说明
--- | --- | --- | --- | ---
Property | font-size | rpx | 手机系统默认 | 文本 size
Property | font-style | Enum | normal | normal/bold/italic/bold_italic
Property | color | color | #000000FF | 取值格式为#RGBA
Property | text-align | Enum(可组合) | left/top | left/top/right/bottom/center/center_horizontal/center_vertical
Property | ellipsize | Enum | none | none;start;middle;end
Property | max-line | Integer | 0 | 0代表不限行数

## image

+ 代码示例如下：
```html
<!--image.vnml-->
<image width="100%" aspect-ratio="1.78" src="{{imageUrl}}" shape="round-corner" corner-radius="30rpx" mode="center-crop"/>
```


类型 | 属性/事件/方法名 | 参数类型 | 参数默认值 | 说明
--- | --- | --- | --- | ---
Property | src | String | | 图片资源地址
Property | mode | Enum | fit-xy | focus-crop/center-crop/center-inside/center/fit-end/fit-center/fit-start/fit-xy
Property | foucs-point-x | Float(0~1) | 0.5 | 重心裁剪功能，仅在 mode 为 focus-crop 时生效
Property | foucs-point-y | Float(0~1) | 0.5 | 重心裁剪功能，仅在 mode 为 focus-crop 时生效
Property | shape | Enum | normal | normal/circle/round-corner
Property | corner-radius | rpx | 12rpx | 圆角半径，仅在 shape 为 round-corner 时生效

其中 mode 的有效值为

模式 | 值 | 说明
--- | --- | ---
缩放 | fit-xy |不保持纵横比缩放图片，使图片的宽高完全拉伸至填满 image 元素
缩放 | fit-start | 保持纵横比缩放图片，使图片的长边能完全显示出来。</br>也就是说，可以完整地将图片显示出来，居上或居左显示。小图会放大，大图会缩小
缩放 | fit-center | 同 fit-start，不过居中显示
缩放 | fit-end | 同 fit-start，不过居右或居左显示
缩放 | center | 不缩放图片，只显示图片的中间区域
缩放 | center-inside | 保持纵横比缩放图片，保证图片的长边能完全居中 显示出来。小图不放大，大图会缩小
裁剪 | center-crop | 保持纵横比缩放图片，只保证图片的短边能完全显示出来。</br>也就是说，图片通常只在水平或垂直方向是完整的，另一个方向将会发生截取
裁剪 | focus-crop | 重心裁剪，具体裁剪位置由 focus-point-x 和 focus-point-y 决定

## checkbox

+ 代码示例如下：
```html
<!--checkbox.vnml-->
<checkbox width="92rpx" aspect-ratio="1" checked="{{selected}}" checked-src="{{check}}" unchecked-src="{{uncheck}}" bindchange="onCheckChange"/>
```

```json
/** checkbox.json **/
{
    "check": "http://connorlu.vip:3000/img/checkbox_y.png",
    "uncheck": "http://connorlu.vip:3000/img/checkbox_n.png",
    "selected": true,
    "position": 10
}
```

```js
/**checkbox.js**/
Page ({
    onCheckChange: function () {
        console.log("checkbox 发生状态切换");
    }
});
```

类型 | 属性/事件/方法名 | 参数类型 | 参数默认值 | 说明
--- | --- | --- | --- | ---
Property | checked | 胡子语句 | | 必填项，绑定 data 里的一个布尔值
Property | checked-src | String | | 选中时图片 url
Property | uncheck-src | String | | 未选中时图片 url
EventHandle | bindChange | function() | | checkbox 状态切换

## input

+ 代码示例如下：
```html
<!--input.vnml-->
<input id="eventText" placeholder="响应事件" max-line="10" confirm-type="done" margin="10rpx" padding="5rpx" width="100%"
            height="auto" font-size="30rpx" bindInput="onInput" bindFocus="onFocus" bindBlur="onBlur" bindConfirm="onConfirm"
            keep-focus="true">{{editdata}}
</input>
```

```json
/** input.json **/
{
  "focusState": "未获取焦点",
  "textCount": 0,
  "confirmCount": 0,
  "editdata": ""
}
```

```js
/**input.js**/
var eventinput;

page({
  onLaunch: function () {
    eventinput = VNDom.findElementByID('eventText');
  },
  onInput: function (params) {
    var text = params.event.value;
    VNData.update('textCount', text.length);

    var orginText = origininput.getValue();
    if (orginText.length > 0) {
      var replaceText = replaceinput.getValue();
      text = text.replaceAll(orginText, replaceText);
      return text;
    }
  },
  onFocus: function (params) {
    VNData.update('focusState', '获取焦点');
  },
  onBlur: function (params) {
    VNData.update('focusState', '未获取焦点');
  },
  onConfirm: function (params) {
    confirmCount = VNData.query('confirmCount');
    confirmCount += 1;
    VNData.update('confirmCount', confirmCount);
  },
  onLeftClick: function (params) {
    var cursor = eventinput.getCursorStart();
    eventinput.setCursorStart(cursor - 1);
  },
  onRightClick: function (params) {
    var cursor = eventinput.getCursorStart();
    eventinput.setCursorStart(cursor + 1);
  },
  onThreeClick: function (params) {
    eventinput.setCursorRange(0, 3);
  },
  onAllClick: function (params) {
    var cursorLength = eventinput.getValue().length;
    eventinput.setCursorRange(0, cursorLength);
  }

});
```

类型 | 属性/事件/方法名 | 参数类型 | 参数默认值 | 说明
--- | --- | --- | --- | ---
Property | font-size | rpx | 手机系统默认 | 文本 size
Property | font-style | Enum | normal | normal/bold/italic/bold_italic
Property | color | color | #000000FF | 取值格式为#RGBA
Property | text-align | Enum(可组合) | left/top | left/top/right/bottom/center/center_horizontal/center_vertical
Property | ellipsize | Enum | none | none;start;middle;end
Property | max-line | Integer | 0 | 0代表不限行数
Property | input-type | Enum | text | text(文字)/number(整数)/digit(小数)
Property | confirm-type | Enum | done | send(发送)/search(搜索)/next(下一个)/go(去)/done(完成)
Property | password | Boolean | false | 是否为密码输入
Property | placeholder | String | "" | 当没有文字输入时的提示文案
Property | placeholder-color | color | #888888FF | 取值格式为#RGBA
Property | keep-focus | Boolean | false | 当点击非本input输入的区域时是否保持焦点
Method | int getCursorStart() |  |  | 当前输入框的光标开始位置
Method | int getCursorEnd() |  |  | 当前输入框的光标结束位置
Method | String getValue() |  |  | 当前输入框的文本
Method | Boolean hasFocus() |  |  | 当前输入框是否获取了焦点
Method | void setCursorRange(int start, int end) |  |  | 设置当前输入框光标起始和结束位置
Method | void setCursorStart(int start) |  |  | 设置当前输入框光标起始位置
Method | void setFocus(boolean focus) |  |  | 设置当前输入框的焦点属性

## list
+ `<list>` 组件是提供垂直列表功能的核心组件。非常适合用于长列表的展示
+ 使用方法:
    
    + `<list>` 标签内有 `vn:for` 属性，使用胡子语法，以 for 循环的方式遍历 `<data>` 标签内的 一个数组
    + 默认情况下，数组的当前项下标变量名为 index，可以通过 `vn:for-index` 属性修改该变量名，同样的 `vn:for-item` 可以修改指定数组当前元素的变量名，和 for 语句定义是一样的
    + 在 `<list>` 标签内使用一组 `<cell>` 标签填充，一个 `<cell>` 代表着一种 ViewType
    + 每个 `<cell>` 都定义了一个子页面布局
    + `<list>` 标签内有 `vn:cell-key` 属性，定义数组元素里标示 ViewType 的字段，默认为 cellType
    + 每个 `<cell>` 标签内应都有 `vn:cell-key` 属性值作为 Key，相应的数组元素里也有同样的 KEY-VALUE
    + `<cell>` 内的页面布局通过胡子语法，访问数组 item 里的属性作为数据填充
    + `<list>` 标签可使用 `<header>` 子标签作为拉下刷新的头部显示的视图，这个标签不能使用当前的 item 访问数据

+ 代码示例如下：
```html
<!--list.vnml-->
<list direction="column" width="100%" height="100%" vn:for="{{listData}}" vn:cell-key="cellType" bindItemTap="onItemClick">
    <cell cellType="text">
        <view>
            <text>{{index}}: {{item.text}}</text>
        </view>
    </cell>
    <cell cellType="image">
        <view flex-direction="row" justify-content="space-between">
            <image width="45%" aspect-ratio="1.5" src="{{item.url}}"/>
            <image width="45%" aspect-ratio="1.5" src="{{item.url}}"/>
        </view>
    </cell>
</list>
```

```json
/** list.json **/
{
  "listData": [
    {
      "cellType": "text",
      "text": "this is first text"
    },
    {
      "cellType": "image",
      "url": "http://puui.qpic.cn/tv/0/11536175_680382/0"
    },
    {
      "cellType": "text",
      "text": "this is second text"
    },
    {
      "cellType": "image",
      "url": "http://puui.qpic.cn/tv/0/11522707_330185/0"
    }
  ]
}
```

```js
/**list.js**/
page({
    onItemClick: function(jsonObject) {
        var position = jsonObject.event.position;
        var path = 'listData[' + position + '].cellType'; 
        var curType = this.VNData.query(path);
        console.log("被点击Item的type为：" + curType);
    }
});
```

类型 | 属性/事件/方法名 | 参数类型 | 参数默认值 | 说明
--- | --- | --- | --- | ---
Property | vn:for | 胡子语句 | | 数据源，必填项
Property | vn:for-index | String | index |
Property | vn:for-item | String | item |
Property | vn:cell-key | String | cellType |
Property | direction | Enum | column | column/row
EventHandle | bindItemTap | function(Integer position) | | 列表 Item 点击，参数为 position
EventHandle | bindHeaderRefreshing | function() | | 列表发生了下拉刷新
EventHandle | bindFooterRefreshing | function() | | 列表发生了上拉加载
EventHandle | bindScroll | function(Float deltaX, Float deltaY) | | 列表滚动，deltaX;deltaY（正数为下滑，负数为上滑）
EventHandle | bindScrollState | function(Integer newState) | | 列表滚动状态切换，newState，0:空闲;1:拖拽;2:滑动;
Method | void scrollToPosition(int position) |  |  | list滚动到指定的位置
Method | void smoothScrollToPosition(int position) |  |  | 有动画的滚动到指定的位置
Method | void setFooterRefreshingEnabled(boolean enable) |  |  | 是否允许上拉加载更多
Method | void setHeaderRefreshingEnabled(boolean enable) |  |  | 是否允许下拉刷新
Method | void setRefreshing(boolean enable) |  |  | 下拉刷新是否开始(如果已经开始下拉刷新可以靠这个值结束下拉刷新，若果没有下拉刷新也可以通过代码触发，前提是setHeaderRefreshingEnabled(true))

## header

```html
<!--listHeader.vnml-->
<list class="mainList" vn:for="{{listData}}" vn:cell-key="cellType" bindHeaderRefreshing="onHeaderRefreshing" bindFooterRefreshing="onFooterRefreshing" >
    <header class="listHeader" bindHeaderStateChange="onHeaderStateChange">
        <text id="header_title" class="headerTitle">下拉刷新</text>
        <text id="header_subtitle" class="headerSubtitle"></text>
        <image id="header_img" class="headerImg" hidden="true" src="http://connorlu.vip:3000/img/header-loading.gif"></image>
    </header>

    <cell cellType="text">
        <view>
            <text>{{index}}: {{item.text}}</text>
        </view>
    </cell>
    <cell cellType="image">
        <view flex-direction="row" justify-content="space-between">
            <image width="45%" aspect-ratio="1.5" src="{{item.url}}"/>
            <image width="45%" aspect-ratio="1.5" src="{{item.url}}"/>
        </view>
    </cell>

</list>
```

```json
/** listHeader.json **/
{
  "listData": [
    {
      "cellType": "text",
      "text": "this is first text"
    },
    {
      "cellType": "image",
      "url": "http://puui.qpic.cn/tv/0/11536175_680382/0"
    },
    {
      "cellType": "text",
      "text": "this is second text"
    },
    {
      "cellType": "image",
      "url": "http://puui.qpic.cn/tv/0/11522707_330185/0"
    }
  ]
}
```

```js
/**listHeader.js**/
page({     
    onHeaderRefreshing: function (param) {
        console.log('onHeaderRefresh');
        this.reloadData();
    },
    onFooterRefreshing: function (param) {
        console.log('onFooterRefresh');
        this.loadNextPage(param);
    },
    onHeaderStateChange: function (event) {
        headerChildren = event.target.getChildrenElement();
        switch (event.event.state) {
        case 0:
            headerChildren[0].setProperty("content", "还原");
            break;
        case 1:
            headerChildren[0].setProperty("content", "拖拽中");
            break;
        case 2:
            headerChildren[0].setProperty("content", "松手");
            break;
        case 3:
            headerChildren[0].setProperty("hidden", true);
            headerChildren[1].setProperty("hidden", true);
            headerChildren[2].setProperty("hidden", false);
            break;
        case 4:
            headerChildren[0].setProperty("content", "刷新完成");
            headerChildren[0].setProperty("hidden", false);
            headerChildren[1].setProperty("hidden", false);
            headerChildren[2].setProperty("hidden", true);
            break;
        }
    }
    });
```

header 主要用于实现下拉刷新，目前只能作为 list 的子控件

类型 | 属性/事件/方法名 | 参数类型 | 参数默认值 | 说明
--- | --- | --- | --- | ---
EventHandle | bindHeaderStateChange | function(Integer state, Boolean isAutomatic, Float maxOffset) | 当下拉刷新状态发生变化时<br> state 0:空闲;1:拖拽;2:松开;3:刷新中;4:刷新完成; <br> isAutomatic 是否为自动触发 <br> maxOffset 达到下拉刷新的偏移量 
EventHandle | bindHeaderMove | function(Boolean hasRefreshed, Boolean isAutomatic, Float offset) | 当下拉刷新视图发生移动时 <br> hasRefreshed 是否已经触发刷新 <br> isAutomatic 是否为自动触发 <br> offset 当前下拉的偏移

## scroll-view

+ 代码示例如下：
```html
<!--scroll.vnml-->
<scroll-view id="scroll" direction="row" width="100%" height="100%"  flex-direction="column" bindScroll="onScroll">
    <view vn:for="{{itemList}}" bindTap="getOffset">
        <image width="50rpx" aspect-ratio="1" src="{{item.iconUrl}}"  />
        <text width="auto" height="auto" flex-grow="1">{{item.title}}</text>
    </view>
</scroll-view>
```

```js
/**scroll.js**/
page({
    printLog: function (log) {
        console.log(log);
    },
    onScroll: function (params) {
        var deltaY = params.event.deltaY;
        this.printLog("滑动速度:" + deltaY + "rpx");
    },
    getOffset: function (params) {
        scrollView = this.VNDom.findElementByID("scroll");
        var offset = scrollView.getOffset();
        this.printLog("当前位移为：" + offset);
    }
});
```

类型 | 属性/事件/方法名 | 参数类型 | 参数默认值 | 说明
--- | --- | --- | --- | ---
Property | direction | Enum | column | column/row
EventHandle | bindScroll | function(Float deltaX,Float deltaY) | | 滚动时触发，deltaX，deltaY，单位为px
Method | scrollTo(Float delta, Boolean animation) | | 0, false | 滚动到指定位置，单位为rpx；参数 animation 指定是否带动画效果
Method | Float getOffset() | | | 获取当前的偏移，单位为rpx



## view-pager

```html
<!--viewPager.vnml-->
<view id="mainContainer">

    <list id="chennelTitleList" class="pageHeader" vn:for="{{pageData}}" vn:cell-key="channelType" style="direction:row;" binditemtap="onChannelItemClick" >
        <cell channelType="channel">
            <text color="{{pageIndex == index ? '#FF0000FF' : '#000000FF'}}">{{item.channelName}}</text>
        </cell>
    </list>

    <view-pager id="mainPager" class="page" vn:for="{{pageData}}" bindPageChange="onPageChange">
        <cell cellType="text">
            <text>{{item.channelName}}</text>
        </cell>
    </view-pager>

</view>
```

```json
/** viewPager.json **/
  {
    "pageIndex":0,
    "pageData": [{
      "cellType": "text",
      "channelType": "channel",
      "channelName":"精选"
    }, {
      "cellType": "text",
      "channelType": "channel",
      "channelName":"电视剧"
    },{
      "cellType": "text",
      "channelType": "channel",
      "channelName":"综艺"
    }, {
      "cellType": "list",
      "channelType": "channel",
      "channelName":"少儿"
    }]
  }
```

```js
/**viewPager.js**/
page({     
    onChannelItemClick: function (params){
        console.log(JSON.stringify(params));
        pager = this.VNDom.findElementByID('mainPager');
        pager.setPageIndex(params.event.position);
    },
    onPageChange: function (param) {
        var cellData = this.VNData.query('pageData[' + param.event.pageIndex + ']');
        this.VNData.update('pageIndex', param.event.pageIndex);

        channelList = this.VNDom.findElementByID('chennelTitleList');
        channelList.smoothScrollToPosition(param.event.pageIndex);
    }
    });
```

类型 | 属性/事件/方法名 | 参数类型 | 参数默认值 | 说明
--- | --- | --- | --- | ---
Property | vn:for | 胡子语句 | | 数据源，必填项
Property | vn:for-index | String | index | 数组下标
Property | vn:for-item | String | item | 数组项
Property | vn:cell-key | String | cellType | 数组项类型
Property | page-gap | rpx | 0rpx | 分页间距
EventHandle | bindScroll | function(Float delta, Float offset, Float offsetPercent, Integer scrollState, Integer pageIndex) | | 滚动时触发， delta, offset, offsetPercent, scrollState, pageIndex
EventHandle | bindScrollStateChange | function(int scrollState) | | 0:空闲;1:拖拽;2:滑动
EventHandle | bindPageChange | function(int pageIndex) | | 滑动停止时指向的分页，pageIndex
Method | void setPageIndex(Integer index) | Integer | | 设置当前的分页编号
Method | Integer getPageIndex() | Integer | | 获取当前的分页编号