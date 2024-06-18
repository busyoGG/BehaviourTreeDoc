# GraphViewExtension 文档

各部分功能说明及使用方式文档

## 文档说明

- 本文档使用[docsify](https://docsify.js.org/#/zh-cn/)构建。
- 项目工程见[BehaviourTree](https://github.com/busyoGG/BehaviourTree)。
- 自定义节点需要继承 `BhBaseNode`。
- 本项目编辑器配合使用[GraphViewExtension](https://github.com/busyoGG/GraphViewExtension)。
- 项目原理说明见 [Untiy-行为树](https://busyo.buzz/article/f9b68df4028f/)。

<!-- * `_sidebar.md` 文件为侧边栏导航配置文件。 -->

<!-- * 如果需要增加侧边栏项目，请在 docs 文件夹下新建 md 文档，并且配置到侧边栏导航文件中。 -->

<!-- * `AfterProgress.js` 为页面处理代码，一些页面的布局处理效果在这里实现。 -->

- `index.html` 中的 `plugins` 的 `function(hook)` 提供自定义插件的修改能力，详情见[开发插件](https://docsify.js.org/#/zh-cn/write-a-plugin)

## 特殊插件使用说明

### tab

<!-- tabs:start -->

#### **English**

Hello!

#### **French**

Bonjour!

#### **Italian**

Ciao!

<!-- tabs:end -->

按照如下格式书写

```markdown
<!-- tabs:start -->

#### **English**

Hello!

#### **French**

Bonjour!

#### **Italian**

Ciao!

<!-- tabs:end -->
```