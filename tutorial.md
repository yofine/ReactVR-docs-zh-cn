# Hello World
我们的第一个 VR 项目只包含了一个 `hello` 字样，你可以在它的源文件 `index.vr.js` 中看到，这个文件是 React VR 项目的入口文件。

```
import React from 'react';
import { AppRegistry, asset, Pano, Text, View } from 'react-vr';

class WelcomeToVR extends React.Component {
  render() {
    // 在加载的 360 全景图像上展示 “hello” 字样
    // “hello” 字样大小为80公分，距你3米远
    return (
      <View>
        <Pano source={asset('chess-world.jpg')} />
        <Text
          style={{
            backgroundColor: '#777879',
            fontSize: 0.8,
            layoutOrigin: [0.5, 0.5],
            paddingLeft: 0.2,
            paddingRight: 0.2,
            textAlign: 'center',
            textAlignVertical: 'center',
            transform: [{translate: [0, 0, -3]}],
          }}>
          hello
        </Text>
      </View>
    );
  }
};

AppRegistry.registerComponent('WelcomeToVR', () => WelcomeToVR);
```
React 应用由众多组件构成（关于“组件”可参考 [官方文档](https://facebook.github.io/react/docs/components-and-props.html)），以上代码声明、注册了顶层组件：**WelcomeToVR**，并定义如何渲染它。

我们的代码由引入依赖（import）开始，接着，它定义了 `WelcomeToVR` 组件，以及如何渲染；由 `AppRegistry` 结束，结束部分在整个项目中只需使用一次。

你可能注意到了，`return` 部分的内容并不完全是 JavaScript 。类似于 `<View>` 、 `<Pano>` 、 `<Text>` 这类标签属于 JSX 语法，它允许你自定义UI，这部分我们稍后会讲到。

我们来回顾下上方代码结构，它返回（`<return>`）了一个 `<View>` 组件，`<View>` 组件包含了两个子组件： `<Pano>` 和 `<Text>` ：
  * `Pano` 创建一个盒子来渲染一张 360 照片，这部分用来渲染你所看到的画面。

  * `Text` 在 3D 空间中渲染文字，这个特定的文本标签 `<Text>` 已经被设计成将一个大字放在你所看到的画面的中间。我们将在其它地方更详细地介绍风格属性（`style`）。

  * `View` 组件被用作容器，它用来包裹其它组件。上方代码中 `<Pano>` 与 `<Text>` 便被 `<View>` 包裹。

每一个 React 组件在渲染时只返回一个根元素，所以我们的 `WelcomeToVR` 组件中的两个子组件需要使用 `<View>` 标签包裹。

为了更好地理解上方代码的作用，你可以尝试修改代码。在 [开始](/getting-started) 中，我们创建了一个 `WelcomeToVR` 项目。嵌套于 `<Text>` 的开始与结束标签中的部分是用来被渲染成文字字符串的，现在我们将其中的 **hello** 换作 **welcome** ，使用 `npm` 启动服务后可以看到更新后的内容。

# JSX 与 ES6 - 这是怎么回事？

现代 Web 开发主要依赖于解析和预处理 JavaScript 的工具，例如将多个 JavaScript 文件打包在一起或实现新的语言功能。这正是 React CLI 所做的，将代码转码以实现 JSX 语法和 ES6 语法。

* JSX 使用类 XML 标记来扩展 JavaScript ，允许你以类似 HTML 的方式将文档组织为一组嵌套的组件。 JSX 使得编写 React 应用更加容易，你可以在 [React in Depth](https://facebook.github.io/react/docs/jsx-in-depth.html) 中深入了解它。如果你希望在React中使用严格的JavaScript语法，那也可以参考 [React Without JSX](https://facebook.github.io/react/docs/react-without-jsx.html) 。

* ES6 即 ES2015，是 JavaScript 语法的升级，目前（截止到 2017-04-22）并没有被所有浏览器支持，所以我们需要在使用它之前进行转码。可以访问 [ECMAScript 6 入门](http://es6.ruanyifeng.com/) 来学习 ES6 语法。

上方代码中类似

```
<Text style={{ fontSize: 0.8, ...}}>
  hello
</Text>
```
便使用了 JSX 语法，它最终会被转为 JavaScript 语法，访问 [React VR Overview](https://facebook.github.io/react-vr/docs/react-vroverview.html) 来了解更多。

### AppRegistry

我们的 `WelcomeToVR` 示例中将 `WelcomeToVR` 定义成组件并使用 `AppRegistry` 进行注册，以便告知 React `WelcomeToVR`组件是整个项目的根组件。你不必过多考虑 `AppRegistry` ，因为它在整个项目中只出现一次。

当你 build 一个 React VR 应用，你可能会编写很多新组件，你在屏幕中看到的任何内容都来自于某些组件的渲染。一个组件可以十分简单，唯一需要的便是 `render` 函数，它将返回一些 JSX 以供渲染。
