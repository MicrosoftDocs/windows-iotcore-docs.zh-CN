# <a name="contributing-to-the-windows-10-iot-documentation"></a>参与 Windows 10 IoT 文档

感谢您对我们的文档的关注。 我们非常感谢你的反馈，编辑、 新增功能和改进我们的文档的帮助。此页介绍的基本步骤和做出贡献的指导原则。

## <a name="sign-a-cla"></a>签订 CLA

如果你要参与多个几行，并且你不是 Microsoft 员工，需要[签署 Microsoft 贡献许可协议 (CLA)](https://cla.microsoft.com/)。 

## <a name="proposing-a-change"></a>建议进行更改

建议对文档进行更改，请执行以下步骤：

1. 如果您正在查看 Docs.microsoft.com 页上，单击**编辑**中的页面右上角的按钮。  您将重定向到对应的 Markdown 源文件中[GitHub 存储库](https://github.com/MicrosoftDocs/windows-iotcore-docs)。  如果已在 GitHub 存储库中，您可以只需导航到想要更改的源文件。
2. 如果还没有 GitHub 帐户，请单击**注册**右上角权限，并创建新的帐户。
3. 从你想要更改的 GitHub 页上，单击铅笔图标。 
4. 修改文件，并使用预览选项卡来确保所做的更改显示良好。
5. 完成后，提交所做的更改并打开一个拉取请求。

创建拉取请求后，将检查 Windows 10 IoT 团队的成员。 如果接受你的请求，则将更新发布到[ https://docs.microsoft.com/windows/iot-core ](https://docs.microsoft.com/windows/iot-core)。

## <a name="making-more-substantial-changes"></a>进行更重大更改

若要对现有文章进行重大更改、 添加或更改图像，或参与新的项目，我们建议在存储库分叉到 GitHub 帐户 (单击右上角的"分叉"按钮[GitHub 存储库](https://github.com/MicrosoftDocs/windows-iotcore-docs)，，然后创建本地克隆 (单击绿色的"克隆或下载"按钮，复制到剪贴板，然后在你的命令行中输入`git clone <paste your repo clone link>`)。

我们还要求的补充新文章，问问自己以下问题之前...
* 已包含一个，并且只有一个 # 级别标题 （相当于以 html 格式的 H1）？ 
* 是 （如果适用） 谓词时态我现在时中并与其他文档一致的新文章的标题中？
* 所有我语法是否正确？
* 具有我添加我的文章-如果补充新文章-到相应的类别以及更新 TOC.md？
* 我具有正确格式的 Url[如下所示](https://github.com/MicrosoftDocs/windows-iotcore-docs/blob/master/CONTRIBUTING.md)而不是这样： https://github.com/MicrosoftDocs/windows-iotcore-docs/blob/master/CONTRIBUTING.md
* 您是否有至少两个审阅者评审新项目？
* 联系过 Sara (saclayt) 或 Namrata (namkedia) 如果您不确定的任何内容？

新文章 does 获取接受，我们的建议如下：
* 与团队共享文章 ！ 不能隐藏所有人-让你知道的对等方。
* 通过在注释框下单击"关注"按钮，按照您的文章的注释。 这样一来，您将保持更新您的文章可能会收到的注释。

有关详细信息，请参阅[存储库分叉](https://help.github.com/articles/fork-a-repo/)。 请注意，我们不会合并活动分支上的任何 Pr。 请确保您要提交到主分支的拉取请求。

如果您不熟悉使用 Git，请尝试[Lynda.com Git Essentials 培训](https://www.lynda.com/Git-tutorials/Git-Essential-Training/100222-2.html)。

## <a name="authoring-your-contribution"></a>创作您的发布内容

分叉并存储库克隆到本地计算机后，您可以开始创作与所选的文本编辑器。  我们，当然，建议[Visual Studio Code](https://code.visualstudio.com/)，来自 Microsoft 的轻量的免费开放源代码编辑器。 有关 markdown 创作帮助，请查看此[Markdown 的每个人都很有趣 ！海报](windows-iotcore/media/DocsMarkdownPoster.pdf)所有需要了解的基础知识。 甚至可以打印和贴在墙上挂起提醒您参与。 

## <a name="submitting-your-contribution-and-filing-a-pull-request-pr"></a>提交您的发布内容并提交拉取请求 (PR)

若要将所做的更改添加到远程存储库，以便它们将分阶段实现发布准备就绪后，在命令行中输入以下步骤：
- `git status`：此命令将显示哪些文件已更改，以便你可以确认自己想要进行这些更改。 
- `git add -A`：此命令指示 git 进行添加所有所做的更改。 如果您希望仅添加到一个特定的文件所做的更改，而是输入以下命令： `git add <file.md>`，其中"file.md"表示名称包含所做的更改的文件。
- `git commit -m “Fixed a few typos”`：此命令指示 git 提交更改添加在上一步骤中，以及描述你所做的更改的简短消息。
- `git push origin <yourbranchname>`：此命令将所做的更改推送到你指定的分支到分叉 GitHub ("origin") 的远程存储库。 因为您已分叉到 GitHub 帐户的存储库，你也可以完成工作**开发**分支。 

如果要满意所做的更改并准备好提交 PR:
- 转到的 IoT 存储库分叉： https://github.com/your-github-alias/windows-iotcore-docs。
- 单击"新建拉取请求"按钮。 ("基分支:"将被列为"MicrosoftDocs/windows iotcore 的文档"，"头分支:"应显示在存储库和分支所做更改的分支。)还可以查看所做更改。 
- 单击绿色的"创建拉取请求"按钮。 然后将需要为你的拉取请求，标题和说明，然后单击"创建拉取请求"按钮一次。

之后将您的发布内容推送到远程存储库，你将发送的电子邮件*打开发布的生成服务*通知您的发布内容是否已成功生成，并链接到任何错误警告，例如断开的链接，请单击若要查看在站点上暂存内容的链接。

一旦您在检查了您的发布内容[Windows 10 IoT Docs 暂存站点](https://review.docs.microsoft.com/en-us/windows/iot-core/)并且可以确信，你想要实时发布所做的更改，你必须提交拉取请求 (PR)。

PR 提交后，将检查 Windows 10 IoT 文档团队的成员。 它接受后，你将能够查看所做的更改上[过渡站点](https://review.docs.microsoft.com/en-us/windows/iot-core)。 这些更新将最终发布实时到[ https://docs.microsoft.com/windows/iot-core ](https://docs.microsoft.com/windows/iot-core)。

## <a name="working-with-branches"></a>如何使用分支

[Windows 10 IoT Docs GitHub 存储库](https://github.com/MicrosoftDocs/windows-iotcore-docs)利用两个主要的父分支：[开发](https://github.com/MicrosoftDocs/windows-iotcore-docs/tree/develop)，可以在查看此内容[过渡站点](https://review.docs.microsoft.com/en-us/windows/iot-core)，和[Live](https://github.com/MicrosoftDocs/windows-iotcore-docs/tree/live)，内容显示在[实时站点](https://docs.microsoft.com/windows/iot-core)。 

发布内容时，请提交拉取请求 (PR) 到**开发**分支。 此分支可以在过渡网站上查看，并且应仅包含已准备好进行实时发布的发布内容。

## <a name="using-issues-to-provide-feedback-on-iot-documentation"></a>使用问题来提供有关 IoT 文档的反馈

若要提供反馈而不是直接修改的实际文档页面[创建一个问题](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues)。

请务必包含主题标题和页面的 URL。

## <a name="additional-resources"></a>其他资源
- [编写和 GitHub 上格式设置入门](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)

## <a name="additional-resources-for-microsoft-employees"></a>对于 Microsoft 员工的其他资源
- [连接你的 GitHub 帐户和 MS 别名](https://review.docs.microsoft.com/en-us/windows-authoring-guide/github-account#2-connect-your-github-account-and-ms-alias-on-the-microsoft-open-source-portal)
- [用于编写 Markdown 资源](https://review.docs.microsoft.com/en-us/windows-authoring-guide/writing-guidance/writing-markdown)
