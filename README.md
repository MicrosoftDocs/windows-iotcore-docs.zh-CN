## <a name="microsoft-open-source-code-of-conduct"></a>Microsoft 开放源代码行为准则

此项目采用了[Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。
有关详细信息，请参阅[代码的行为准则常见问题解答](https://opensource.microsoft.com/codeofconduct/faq/)或联系[ opencode@microsoft.com ](mailto:opencode@microsoft.com)提出任何其他问题或意见。

# <a name="how-to-contribute-to-windows-10-iotcore-documentation"></a>如何参与撰写 Windows 10 IoT 核心版文档

## <a name="legal-notices"></a>法律声明
Microsoft 及任何创作人按照[创作共用署名 4.0 国际公共许可](https://creativecommons.org/licenses/by/4.0/legalcode)授予你此存储中的 Microsoft 文档和其他内容的许可，请参阅[许可证](LICENSE)文件，并按照 [MIT 许可](https://opensource.org/licenses/MIT)授予你存储库中任何代码的许可，请参阅[许可证代码](LICENSE-CODE)文件。

本文档中引用的 Microsoft、Windows、Microsoft Azure 和/或其他 Microsoft 产品和服务是 Microsoft 在美国和/或其他国际/地区的商标或注册商标。
此项目的许可证并未授予你使用任何 Microsoft 名称、徽标或商标的权利。
有关 Microsoft 的常规商标指南，可参看 http://go.microsoft.com/fwlink/?LinkID=254653 。

可在 https://privacy.microsoft.com/en-us/ 查找隐私信息

Microsoft 及任何创作人保留所有其他权利（无论是其各自的版权、专利或商标），无论是通过默示、禁止否认的方式还是以其他方式。

## <a name="contributing"></a>投稿

这是托管在 [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core) 上的 Windows 10 IoT **文档**的存储库。

如果希望看到新的报道或提供反馈，请考虑[**投稿**](/CONTRIBUTING.md)。  可以编辑现有内容、添加新内容，或者直接创建新[问题](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues)。 我们会查看你的建议，并争取将其纳入文档中。

若要编辑内容，只需在要更改的文章中单击“编辑”即可：

![关于如何编辑文档的 Gif](windows-iotcore/media/edit-doc.gif)


也可通过克隆或下载存储库进行更改：

![关于如何克隆或下载存储库的 Gif](windows-iotcore/media/download-repo.gif)

此外还需为拉取请求添加审阅者或审阅，这样我们才能批准它们：

![为拉取请求添加审阅者](windows-iotcore/media/reviewers.gif)

# <a name="conventions"></a>约定
  - 添加某个页面时，必须在 [toc.md](windows-iotcore/TOC.md) 中为它添加一个条目，否则它不会显示。
  - 一个文件夹可以包含多个文件夹或 `readme.md`
  - 文件夹/目录名称用短划线分隔（例如 `f12-tools`）并采用小写。 它们用在 docs.microsoft.com 站点上的 URL 中。 请勿使用下划线或 PascalCase/camelCase。


## <a name="other-text-elements"></a>其他文本元素

这些其他的文本元素有可用的样式设置：

* 未经排序的列表
* 使用常规项目符号
   * 也可将项目符号嵌套起来
   * 项目符号列表应该有不止一个条目。
* 极标准

1. 经过排序的列表
2. 使用常规编号或西式编号。
3. 只有在某个列表真的可以排序时才使用。

_________________________

提供水平规则。 建议谨慎使用，以免造成混乱。
请勿将水平规则与标题标记组合使用；某些已针对视觉层次结构使用线条样式。
另外，请勿将备注（见下）组合到编号列表中， 否则会扰乱编号顺序。

## <a name="displaying-code"></a>显示代码

可以使用内联 `code` Markdown 语法（使用反撇号）。

也可这样显示代码块：

```css
body {
    background: #fff;
}
```

## <a name="tables"></a>表

| 你可以     | 使用标头 | 在表中    |
|-------------|-------------|-------------:|
| 左对齐| 除非使用 #  | 456          |
| 文本值  | 更多文本   | $0.00        |

## <a name="notes"></a>说明

请谨慎使用注释。 注释是旨在突出显示“请勿错过”信息的块。

我们有四个不同版本的目前已进行样式设置的注释：
- 注意
- 警告
- 提示
- 重要提示


对于多行块引用注释，请在每行注释前面使用 >，如以下示例所示。

## <a name="images"></a>映像

图像应该存储在 `media` 文件夹中，使用相对路径进行引用：

`![Note patterns](media/notes.png)`


## <a name="code-of-conduct"></a>行为准则
此项目采用了[Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。 有关详细信息，请参阅[代码的行为准则常见问题解答](https://opensource.microsoft.com/codeofconduct/faq/)或联系[ opencode@microsoft.com ](mailto:opencode@microsoft.com)提出任何其他问题或意见。
