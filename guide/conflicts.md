# 声明插件冲突

::: tip
此特性需要 5.0.0 版本或以上。
:::

有时候，您可能希望您的插件不与其它某些插件一起运行。例如，Blessing Skin 官方插件里的「你好，多莉」插件不能与「一言」插件同时运行，因为这两个插件都在页面上同一个位置显示各自的东西。

因此 Blessing Skin 提供一个途径来让您指明不能与哪些插件同时运行。

通过 `package.json` 文件内 `enchants` 字段下的 `conflicts` 字段，您可以声明您的插件不能与哪些插件同时运行。

例如：

```json
{
  "enchants": {
    "conflicts": {
      "a": "*",
      "b": "^3.0.0"
    }
  }
}
```

如上，`conflicts` 是一个键值对结构。其中键是其它插件的 `name`，值是表明与该插件的哪些版本有冲突，这里可以使用语义化版本。

按照上面的例子，当前插件不能与任何版本的 `a` 插件同时运行；而不能与 `3.x` 版本的 `b` 插件同时运行。换句话说，这将允许与 `3.x` 以外的其它版本（如 `2.x` 或 `4.x`）的 `b` 插件同时运行。
