## <a name="microsoft-open-source-code-of-conduct"></a>Microsoft 开放源代码行为准则

此项目已采用[Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。
有关详细信息请参阅[代码的行为准则常见问题解答](https://opensource.microsoft.com/codeofconduct/faq/)或联系[ opencode@microsoft.com ](mailto:opencode@microsoft.com)与任何其他问题或意见。

# <a name="how-to-contribute-to-windows-10-iotcore-documentation"></a>如何参与编辑 Windows 10 IoTCore 文档

## <a name="legal-notices"></a>法律声明
Microsoft 及任何创作人按照[创作共用署名 4.0 国际公共许可](https://creativecommons.org/licenses/by/4.0/legalcode)授予你此存储中的 Microsoft 文档和其他内容的许可，请参阅[许可证](LICENSE)文件，并按照 [MIT 许可](https://opensource.org/licenses/MIT)授予你存储库中任何代码的许可，请参阅[许可证代码](LICENSE-CODE)文件。

本文档中引用的 Microsoft、Windows、Microsoft Azure 和/或其他 Microsoft 产品和服务是 Microsoft 在美国和/或其他国际/地区的商标或注册商标。
此项目的许可证并未授予你使用任何 Microsoft 名称、徽标或商标的权利。
Microsoft 的一般商标准则，请参阅 http://go.microsoft.com/fwlink/?LinkID=254653。

可以在发现的隐私信息 https://privacy.microsoft.com/en-us/

Microsoft 及任何创作人保留所有其他权利（无论是其各自的版权、专利或商标），无论是通过默示、禁止否认的方式还是以其他方式。

## <a name="contributing"></a>参与

这是存储库，适用于 Windows 10 IoT**文档**托管于[ https://docs.microsoft.com/windows/iot-core ](https://docs.microsoft.com/windows/iot-core)。

如果想要了解新的覆盖范围或有任何反馈，请考虑[**参与**](/CONTRIBUTING.md)。  可以编辑现有的内容、 添加新的内容，或只需创建新[问题](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues)。 我们来看看您的建议，并将协同工作来将其合并到文档。

若要编辑内容，只需单击编辑在想要对注册表进行更改的文章：

![有关如何编辑文档的 Gif](windows-iotcore/media/edit-doc.gif)


您还可以克隆或下载存储库进行更改：

![如何克隆或下载存储库上的 Gif](windows-iotcore/media/download-repo.gif)

您还需要将审阅者或评论添加到拉取请求来获取批准它们：

![将审阅者添加到你的拉取请求](windows-iotcore/media/reviewers.gif)

# <a name="conventions"></a>约定
  - 在添加一个页面时，您必须添加一个条目中为其[toc.md](windows-iotcore/TOC.md)它才会显示。
  - 一个文件夹可以包含更多的文件夹或`readme.md`s
  - 文件夹/目录名称是短划线分隔 (例如， `f12-tools`) 和大小写。 Docs.microsoft.com 网站上的 Url 中使用它们。 不要使用下划线或 pascal 命名法/驼峰式大小写。


## <a name="other-text-elements"></a>其他文本元素

这些其他文本元素具有样式设置可用：

* 未排序的列表
* 具有常规项目符号
   * 此外可以嵌套项目符号
   * 项目符号列表应具有多个条目。
* 漂亮的标准

1. 排序的列表
2. 使用正则这可怜的家伙 western 样式编号。
3. 仅当真正有顺序的列表时，才应使用。

_________________________

水平规则可使用。 我们建议尽量少使用它们来减少混乱。
与标题标记，则不要混用水平标尺一些已对可视层次结构使用线条样式。
此外，不要混用中间编号列表的说明 （见下文）。 这都在困扰着编号顺序。

## <a name="displaying-code"></a>显示代码

可以使用内联`code`Markdown 语法 （使用反撇号）。

也可以显示的代码块如下所示：

```css
body {
    background: #fff;
}
```

## <a name="tables"></a>表

| 你可以     | 使用标头 | 上表    |
|-------------|-------------|-------------:|
| 左对齐| 除非 #  | 456          |
| 文本值  | 更多的文本   | $0.00        |

## <a name="notes"></a>说明

尽量少使用说明。 它们是块旨在突出显示"无-未命中的 it"信息。

我们有四个不同版本的当前样式的说明：
- 注意
- 警告
- 提示
- 重要提示


对于多行块引用说明，请使用 > 的说明，如下面的示例中所示的每一行的前面。

## <a name="images"></a>映像

图像应存储在`media`文件夹和相对路径引用：

`![Note patterns](media/notes.png)`


## <a name="code-of-conduct"></a>行为准则
此项目已采用[Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。 有关详细信息请参阅[代码的行为准则常见问题解答](https://opensource.microsoft.com/codeofconduct/faq/)或联系[ opencode@microsoft.com ](mailto:opencode@microsoft.com)与任何其他问题或意见。
