# ts-utility-plugins/ddzy

一些有用的插件库集合

## 一、说明

> 插件库包括 `canvas特效`插件, `业务`插件、`工具组件`等等...

部分插件已投入使用:

- [canvas-colorful-bubble](https://blog.yyge.top/)
- [canvas-jumping-characters](https://blog.yyge.top/)

**TODO**: 后续会考虑放置到`GitHub-pages`展示

## 二、用法

> **PS**: 重构代码中, 暂未实现对`npm引入`的支持

详细用法, 参考[这里](https://github.com/ddzy/ts-utility-plugins#usage)

## 三、目录

- [x] Canvas
  - [x] [canvas-stars-line](#四canvas-stars-line)
  - [x] [canvas-colorful-bubble](#五canvas-colorful-bubble)
  - [x] [canvas-jumping-characters](#六canvas-jumping-characters)
- [x] Business
  - [x] [business-carousel](#七business-carousel)
  - [x] [business-tab](#八business-tab)
- [x] Utility
  - [ ] [utility-dom](#九utility-dom)

## 四、canvas-stars-line

> 非常nice的`星空连线`特效插件

### 4.1 基本用法

```ts
new StarsLine({
  container: '#app',
});
```

### 4.2 可配置项

```ts
export interface IStaticStarsLineBallRadiusParams {
  min: number,
  max: number,
};
```

| Key          | Type                             | Require | Description      |
| ------------ | -------------------------------- | ------- | ---------------- |
| container    | string                           | true    | 挂载的canvas节点 |
| cvsWidth     | number                           | false   | 画布宽           |
| cvsHeight    | number                           | false   | 画布高           |
| cvsBgColor   | string                           | false   | 画布背景颜色     |
| ballNum      | number                           | false   | 星空点数量       |
| ballRadius   | IStaticStarsLineBallRadiusParams | false   | 星的半径         |
| allowMouse   | boolean                          | false   | 是否允许鼠标交互 |
| lineColor    | string                           | false   | 连线颜色         |
| lineWidth    | number                           | false   | 连线宽度         |
| ballSpeed    | number                           | false   | 星空点移动速度   |
| ballColor    | string                           | false   | 星空点颜色       |
| isResize     | boolean                          | false   | 是否跟随窗口大小 |
| safeDistance | number                           | false   | 连线安全距离     |

### 4.3 注意事项

鼠标交互(`allowMouse`)暂未实现.

## 五、canvas-colorful-bubble

> 构建的canvas气泡插件, 可用作个人博客背景(本人已用上👌, [点这里](https://blog.yyge.top/)查看).

### 5.1 基本用法

```ts
new ColorfulBubble({
  container:
});
```

### 5.2 可配置项

```ts
interface IStaticColorfulBubbleScaleRangeParams {
  min: number,
  max: number,
};
```

| Key               | Type                                  | Require | Description      |
| ----------------- | ------------------------------------- | ------- | ---------------- |
| container         | string                                | false   | 挂载的canvas节点 |
| cvsWidth          | number                                | false   | 画布的初始宽     |
| cvsHeight         | number                                | false   | 画布的初始高     |
| cvsBgColor        | string                                | false   | 画布背景色       |
| bubbleNum         | number                                | false   | 生成的气泡数量   |
| bubbleScaleRange  | IStaticColorfulBubbleScaleRangeParams | false   | 气泡半径大小     |
| bubbleExpandRange | number                                | false   | 气泡最大伸缩距离 |
| bubbleOpacity     | number                                | false   | 气泡初始透明度   |
| bubbleSpeed       | number                                | false   | 气泡运动步长     |
| bubbleColorArr    | string[]                              | false   | 气泡颜色         |
| allowMouse        | boolean                               | false   | 是否允许鼠标交互 |

### 5.3 注意事项

> **Q**: 关于`container`配置项?

***A***: 默认为可选, 但是不填的话会抛出`自定义的异常`, 所以最好还是提供一个挂载节点👌.

> **Q**: 是否会添加`opacity`变化功能?

***A***: 有时间再搞.

## 六、canvas-jumping-characters

> 点击产生文字,并逐渐消失, 可用作个人博客背景.

### 6.1 基本用法

```ts
new JumpingCharacters({
  container: '#app',
});
```

### 6.2 可配置项

| Key            | Type     | Require | Description                  |
| -------------- | -------- | ------- | ---------------------------- |
| container      | string   | true    | 挂载的canvas节点             |
| cvsWidth       | number   | false   | 画布的初始宽                 |
| cvsHeight      | number   | false   | 画布的初始高                 |
| cvsBgColor     | string   | false   | 画布背景色                   |
| text           | string[] | false   | 产生的文字                   |
| textColor      | string[] | false   | 文字颜色                     |
| textSize       | number   | false   | 文字大小                     |
| safeDistance   | number   | false   | 安全距离(文字移动多远后消失) |
| initialOpacity | number   | false   | 初始透明度                   |
| speed          | number   | false   | 移动速率                     |

### 6.3 注意事项

待补充...

## 七、business-carousel

> 封装的```轮播```插件, 用法及其简单, 页面只需```一个div```元素, 不用撰写烦人的DOM, 插件会自动生成DOMTree

### 7.1 基本用法

```ts
new Carousel({});
```

### 7.2 可配置项

```ts
interface IDataSource {
  text: string,
  img: {
    url: string,
    target: string,
  },
}
```

| Key          | Type          | Require | Description          |
| ------------ | ------------- | ------- | -------------------- |
| dataSource   | IDataSource[] | false   | 基本数据             |
| afterChange  | () => void    | false   | 切换后回调           |
| beforeChange | () => void    | false   | 切换前回调           |
| autoPlay     | boolean       | false   | 是否自动切换         |
| showDots     | boolean       | false   | 是否显示导航点       |
| showArrows   | boolean       | false   | 是否显示箭头         |
| easing       | string        | false   | 动画效果             |
| effect       | Fade          | false   | 切换效果             |
| delayTime    | number        | false   | 自动滚动延迟时间     |
| duringTime   | number        | false   | 过渡时间             |
| isHoverPause | boolean       | false   | 鼠标放置是否停止轮播 |

### 7.3 注意事项

> 目前只支持 Fade & Scroll 两种状态轮播图, **默认使用`scroll`**

```ts
new Carousel({
  effect: 'scroll' | 'fade',
});
```

## 八、business-tab

> tabs标签页插件, 只需传入 渲染的数据 和 渲染区间就可

### 8.1 基本用法

> **PS**: 默认会挂载于`body`上, 采用默认数据.

```ts
new Tab({});
```

### 8.2 可用接口

> **PS**: 如下列出了一系列配置项接口.

```ts
export interface ITabConfigProps {
  container?: string;
  dataSource?: ITabDataSource[];
  type?: ITabTypeEffect;
  mouse?: ITabMouseEffect;
  defaultActiveKey?: number;
  tabBarGap?: number;
  tabBarStyle?: ITabBarStyle;
  tabBarLineStyle?: ITabBarLineStyle;
  animated?: boolean;
  onChange?: (activeKey: number | string) => void;
  onTabClick?: () => void;
}
export interface ITabDataSource {
  tabPaneTitle: {
    icon?: string,
    text?: string,
  },
  tabPaneContent: {
    text?: string,
  },
};
export interface ITabBarStyle {
  'background-color'?: string;
  color?: string;
  'font-size'?: number;
  'font-family'?: string;
  backgroundColorActive?: string;
  colorActive?: string;
}
export interface ITabBarLineStyle {
  'background-color'?: string;
  height?: number;
}
export type ITabTypeEffect = 'line' | 'card';
export type ITabMouseEffect = 'mouseenter' | 'click';
```

### 8.3 可配置项

> **PS**: 下述表格中为所有的可配置项

| Key              | Value             | Require | Description       |
| ---------------- | ----------------- | ------- | ----------------- |
| container        | HTMLElement       | false   | 挂载容器          |
| dataSource       | IDataSource       | false   | 源数据            |
| type             | line(card)        | false   | 页签类型          |
| mouse            | mouseenter(click) | false   | 切换属性          |
| defaultActiveKey | number            | false   | 初始化选中面板key |
| tabBarGap        | number            | false   | tabsBar之间的间隙 |
| tabBarStyle      | ITabBarStyle      | false   | tabBar样式对象    |
| tabBarLineStyle  | ITabBarLineStyle  | false   | 线条样式          |
| animated         | boolean           | false   | 是否开启动画      |
| onTabClick       | ()=>void          | false   | tab被点击的回调   |
| onChange         | (activeKey)=>void | false   | 切换面板的回调    |

## 九、utility

一系列工具函数, [项目目录](https://github.com/ddzy/ts-utility-plugins/tree/master/src/ddzy/utility).

### 9.1 工具详解

内容过多, 已迁移至[此处](./utility/README.md)展示.

## 十、其它

持续更新中...

**Enjoy!**