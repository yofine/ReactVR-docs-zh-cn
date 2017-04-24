# React VR 概述

React 是由 Facebook 开源的 UI 库，可以轻松创建交互式用户界面。React VR 将其提升到一个新水平，在虚拟现实中创建 UI 和 3D 场景。

在本章节，我们会强调 React VR 的一些主要优点和概念。

### JSX 与 声明式 UIs

使 React 具有吸引力的一个原因在于它将声明式 UI 与代码进行组合并以优雅的方式操纵它们。UI 元素被类似 HTML 的组件标签所描述，例如：`<Greeting name='Joe' />` 标签可能表示了一个 **欢迎** 组件并接收一个 **name** 作为参数，这些标签在 JSX 的辅助下被直接插入 JavaScript。

JSX 是 JavaScript 的语法扩展，它在 React Native packager 中被预处理为 JavaScript ，JSX 允许使用更为优雅的方式来描述 UI 元素。

```
<MyButton color="blue" shadowSize={2}>
  Click Me
</MyButton>
```

上方代码被编译为：

```
React.createElement(
  MyButton,
  {color: 'blue', shadowSize: 2},
  'Click Me'
)
```

推荐使用更加宜读的 JSX 语法，这并不强制。更多请参考 [JSX In Depth](https://facebook.github.io/react/docs/jsx-in-depth.html)。

### React 主要概念

使用 React 需要了解一些专业术语与主要概念，下面快速总结一些重要概念：

* 组件（Components）- **组件** 是 **可复用** 的 UI 元素，它可以于标签中使用，例如：`<Greeting />`。 React Native 提供了内置组件，比如 `Text` 与 `Image`。通过从 `React.Component` 派生一个类来声明其它组件，每个组件都有一个 `render（）` 函数，该函数返回一组完整描述其内容的 **子子组件**。

* 属性（Props）- 组件可以接收参数，比如 `<Greeting name='Rexxar' />` 中的 `name`。这些参数称为属性（props 或 properties），可以通过 `this.props` 变量访问到它们。在上面的例子中， `name` 值可以通过 `{ this.props.name }` 访问到。更多请参考 [Components, Props and State](https://facebook.github.io/react-vr/docs/components-props-and-state.html)。

* 状态（State）- 组件可以通过存储状态进行界面内容显示的控制。当状态值变化时，组件会重新渲染。所有可修改的状态都存储在组件内 **this.state** 对象中，并且只能通过专用的 **setState函数** 进行修改，例如：

```
this.setState({myStateVariableCounter : 10})
```

* 事件（Events）- 组件可以在某些 UI 操作时产生事件，例如： `View` 组件在焦点进入或离开特定区域时产生 `OnEnter` 与 `OnExit` 事件。这些事件可以在组件声明中处理，以便正确处理交互。例如：

```
<View onEnter={() => this.setState({hasFocus: true})}>
```

* 布局（Layout）- React使用 flexbox 算法和布局规则自动定位 2D 平面内的组件，该布局通过计算或指定宽度、高度来规定组件尺寸、控件样式属性（如 alignItems ）。更多请参考 [Layout and Style](https://facebook.github.io/react-vr/docs/layout-and-style.html)。

* 样式（Style）- 样式对象控制组件的外观和布局。它们通常通过样式对象指定，例如：

```
<View style={{width: 100, height: 100, backgroundColor: 'skyblue'}}/>
```

在 `StyleSheet.create` 的帮助下，可以将样式对象于外部声明，而不是直接指定所有组件属性，这种外部样式表简化了组件重用。 虽然 React StyleSheet 对象与 CSS 共享一些属性名称，但它们并不直接相关。

### React 生态系统

虽然最初是为了简化 Web 的开发而开发的，但 React 生态系统已经发展到多个方面：

* [React](https://facebook.github.io/react/)

* [React Native](https://facebook.github.io/react-native/)

* React VR

虽然它在浏览器中运行，但 React VR 更接近 React Native，因为两者支持许多相同的标签，如 `<View>` 和 `<Text>`。 除了 2D 布局，它还引入了 **3D 场景**、**变换** 和 **全景图** 的概念，允许将对象放置在 3D 空间中并于 VR 中渲染。

React VR 使用了 OVRUI 库，它基于 **Three.js** JavaScript 3D 引擎。 Three.js 在浏览器内部运行，并通过 WebGL 渲染场景。 通过 Web VR API 提供的 **VR headsets** 访问接口，可以在 Rift、GearVR 等设备显示。 然而，React VR 并不需要 **VR headsets** 来运行，它也可用于创建在浏览器或手机上运行的交互式 360 体验。


React Native 框架的关键概念也适用于 React VR。 以下是其中一些关键概念，以及进一步详细信息的链接。

#### React Native Packager

在浏览器运行 JavaScript 之前，必须对 JavaScript 代码进行预处理。 此预处理由 React Native Packager 执行， 它类似于 Browserify 和 Webpack，并提供了一个类似 CommonJS 的模块系统、JavaScript 编译（ES6，Flow，JSX）、捆绑和资源加载。

对于 React VR ，我们主要使用两个命令：

* bundle - 将 JavaScript 文件进行处理、转换和合并为一个单一的 JavaScript 静态文件。

* start - 使用 React Native package 作为 Web 服务器并动态打包 JavaScript 文件。

使用 `npm start` 启动 packager ，它与下方命令等价：

```
node node_modules/react-native/local-cli/cli.js start
```

在这种模式下，packager 起到了本地服务器的作用，它将 React 和 JSX 代码转换成浏览器所需要的 JavaScript 代码。你可以通过 `npm start` 命令启动项目并访问 [http://localhost:8081/index.vr.bundle?platform=vr]( http://localhost:8081/index.vr.bundle?platform=vr) 观看效果。

对于静态网站，你需要存储生成的内容。通过 `npm run bundle` 进行文件的打包。

打包后的 `index.vr.bundle` 文件包含了浏览器支持的 JavaScript 代码。

我们在此只讨论使用方式，更多信息请参考 [React Native Packager](https://github.com/facebook/react-native/blob/master/packager/README.md)。

#### 网络

React VR 使用 Fetch API 通过网络获取资源，如果你以前使用过 **XMLHttpRequest** 或其它 API ，你将会很快熟悉 Fetch。

关于结合 Fetch 使用 React Native 的更多信息以及例子，请访问 [Networking](https://facebook.github.io/react-native/docs/network.html) 。

查看 Fetch 所有属性，请访问 [Fetch 请求 文档](https://developer.mozilla.org/en-US/docs/Web/API/Request)。

查看 Fetch API 文档，请访问 [Fetch API 文档](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)。
