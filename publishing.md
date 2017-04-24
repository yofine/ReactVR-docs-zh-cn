# 发布你的项目
### 创建生产环境版本

一旦你创建了引人入胜的 VR 项目，很有可能你会将它于网上分享。 React VR 附带一个脚本，可以将所有内容处理成极少的文件，然后我们将它们上传到 Web 服务器中。

在你的项目根目录下，通过命令行运行以下命令：

```
 npm run bundle
```

这会在 `vr` 目录下创建一个 `build` 目录，其中包含了该项目编译后的文件。`build` 目录下的文件需要上传到 Web 服务器中。

如果使用了其它资源（比如放置于 `static_assets` 目录下的图片），你需要
将 `static_assets` 目录也上传到 Web 服务器中以便 VR 程序正确地引用。现在的目录结构可能如下：

```
Web Server
├─ static_assets
|
├─ index.html
├─ index.bundle.js
└─ client.bundle.js
```
如果你想将 JavaScript 文件托管到其它位置，比如 CDN 中，那么需要在调用 `ReactVR.init()` 时传递 `assetRoot` 路径。例如你的文件托管在 `https://cdn.example.com/vr_assets/` ，那么就需要在调用中传递第三个参数：

```
ReactVR.init(
  'path/to/index.bundle.js',
  document.body,
  { assetRoot: 'https://cdn.example.com/vr_assets/' }  // 第三个参数
);
```

### 与现有网页集成

如果你希望将 VR 体验集成于某网页中，推荐的方式是使用 `<iframe>` 标签。设置 `src` 属性值为你项目的 `index.html` 文件地址，并为 `iframe` 设置合适的大小。
