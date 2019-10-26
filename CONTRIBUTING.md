# <a name="contributing-to-the-windows-10-iot-documentation"></a>参与撰写 Windows 10 IoT 文档

感谢你对我们的文档的关注。 我们非常感谢你的反馈、编辑、添加和改进文档的帮助。此页介绍了用于参与的基本步骤和指导原则。

## <a name="sign-a-cla"></a>签署 CLA

如果你希望贡献不止数行的内容，但你不是 Microsoft 员工，则需[签署 Microsoft 投稿许可协议 (CLA)](https://cla.microsoft.com/)。 

## <a name="proposing-a-change"></a>建议一项更改

若要建议更改文档，请按以下步骤操作：

1. 如果你是在查看 Docs.microsoft.com 页面，请单击页面右上角的“编辑”按钮。  我们会将你重定向到 [GitHub 存储库](https://github.com/MicrosoftDocs/windows-iotcore-docs)中的相应 Markdown 源文件。  如果已经在 GitHub 存储库中，则可直接导航到要更改的源文件。
2. 如果还没有 GitHub 帐户，请单击右上角的“注册”，创建一个新帐户。
3. 在要更改的 GitHub 页中，单击铅笔图标。 
4. 修改文件，使用预览选项卡来确保所做的更改看起来是合适的。
5. 完成后，提交所做的更改并打开一个拉取请求。

当你创建拉取请求之后，Windows 10 IoT 团队的成员会进行审查。 如果你的请求被接受，则更新会发布到 [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core)。

## <a name="making-more-substantial-changes"></a>进行更重大的更改

若要对现有文章进行重大更改、添加或更改图像或是进行新文章投稿，建议将存储库的分支放置到 GitHub 帐户中，方法是：单击 [GitHub 存储库](https://github.com/MicrosoftDocs/windows-iotcore-docs)右上角的“分支”按钮，然后创建本地克隆（单击绿色的“克隆或下载”按钮，将内容复制到剪贴板中，然后在命令行中输入 `git clone <paste your repo clone link>`）。

我们还要求你在进行新文章投稿时，询问自己以下问题：
* 我是否已提供一个（仅一个）# 级标题（等同于 HTML 中的 H1）？ 
* 我新文章的标题中的动词时态（如果适用）是否采用现在时且与其他文档一致？
* 我的语法是否全都正确？
* 我是否已将文章（如果是进行新文章投稿）添加到适当的类别并更新了 TOC.md？
* 我是否已正确设置 URL 的格式，使之[看起来像这样](https://github.com/MicrosoftDocs/windows-iotcore-docs/blob/master/CONTRIBUTING.md)而不是这样： https://github.com/MicrosoftDocs/windows-iotcore-docs/blob/master/CONTRIBUTING.md ？
* 你是否已安排至少两个人对你的新文章进行评审？
* 联系 Terry Warwick，twarwick@microsoft.com

如果我们接受了你的新文章，建议你：
* 将文章与你的团队共享！ 不要隐藏你的成就 - 让你的同事知道。
* 单击评论框下的“关注”按钮，关注文章的评论。 这样就可以即时了解文章获得的评论。

有关详细信息，请参阅 [Fork a Repo](https://help.github.com/articles/fork-a-repo/)（创建存储库分支）。 请注意，我们不会合并活动分支上的任何 PR。 请务必将 PR 提交到主分支。

如果不熟悉 Git 的使用，请尝试观看 [Lynda.com 的 Git 基础知识培训](https://www.lynda.com/Git-tutorials/Git-Essential-Training/100222-2.html)。

## <a name="authoring-your-contribution"></a>创作稿件

创建存储库的分支并将存储库克隆到本地计算机以后，即可使用所选文本编辑器进行创作。  当然，我们会建议你使用 [Visual Studio Code](https://code.visualstudio.com/)，这是 Microsoft 提供的免费轻型开源编辑器。 若要获取有关 markdown 创作的帮助，请查看此[markdown 对每个人都非常有趣！海报](windows-iotcore/media/DocsMarkdownPoster.pdf)，其中包含需要了解的所有基本知识。 你甚至可以将它打印出来挂在墙上，提醒你投稿。 

## <a name="submitting-your-contribution-and-filing-a-pull-request-pr"></a>提交稿件和拉取请求 (PR)

准备将更改添加到远程存储库暂存以待发表后，请在命令行中输入以下步骤：
- `git status`：此命令将显示已更改的文件，以便可以确认是否要进行这些更改。 
- `git add -A`：此命令通知 git 添加所有更改。 如果只希望添加对某个具体文件的更改，可以改为输入 `git add <file.md>` 命令，其中的“file.md”表示包含更改内容的文件的名称。
- `git commit -m “Fixed a few typos”`：此命令通知 git 提交你在上一步中添加的更改，以及描述你所做的更改的短消息。
- `git push origin <yourbranchname>`：此命令将所做的更改推送到你在 GitHub 上分叉的远程存储库（"源"）到你指定的分支。 由于你已创建存储库的分支并将其放置到你自己的 GitHub 帐户中，因此你可以在“开发”分支中完成自己的工作。 

如果对所做的更改满意并准备提交 PR，请执行以下操作：
- 转到 IoT 存储库的分支： https://github.com/your-github-alias/windows-iotcore-docs 。
- 单击“新建拉取请求”按钮。 （"基本分叉：" 将作为 "MicrosoftDocs/iotcore-文档" 列出，"head 分叉：" 应显示你的存储库和你进行更改的分支的分叉。）你还可以在此处查看你的更改。 
- 单击绿色的“创建拉取请求”按钮。 此时系统会要求你为拉取请求提供标题和说明，然后再次单击“创建拉取请求”按钮。

当你将稿件推送到远程存储库以后，*Open Publishing Build Service* 会向你发送一封电子邮件，告知你投稿是否成功，并提供指向错误警告（例如链接失效）的链接。单击这些链接即可查看暂存在站点上的内容。

查看 [Windows 10 IoT Docs 暂存站点](https://review.docs.microsoft.com/en-us/windows/iot-core/)上的稿件并决定实时发布所做的更改以后，你必须提交拉取请求 (PR)。

当你提交 PR 之后，Windows 10 IoT Docs 团队的成员会进行审查。 如果我们接受了该 PR，你就可以在[暂存站点](https://review.docs.microsoft.com/en-us/windows/iot-core)上查看所做的更改。 这些更新最终会实时发布到 [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core)。

## <a name="working-with-branches"></a>使用分支

[Windows 10 IoT 文档 GitHub 存储库](https://github.com/MicrosoftDocs/windows-iotcore-docs)利用了两个主要的父分支：[开发](https://github.com/MicrosoftDocs/windows-iotcore-docs/tree/develop)、可以在[过渡站点](https://review.docs.microsoft.com/en-us/windows/iot-core)上查看此内容[，并在实时](https://github.com/MicrosoftDocs/windows-iotcore-docs/tree/live)[站点](https://docs.microsoft.com/windows/iot-core)上查看内容。 

投稿时，请将拉取请求 (PR) 提交到**开发**分支。 此分支可以在暂存站点上查看，应该只包含即将实时发布的稿件。

## <a name="using-issues-to-provide-feedback-on-iot-documentation"></a>以问题形式提供 IoT 文档反馈

若要提供反馈而不是直接修改实际文档页面，请[创建一个问题](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues)。

请务必包含主题标题和页面的 URL。

## <a name="additional-resources"></a>其他资源
- [Getting started with writing and formatting on GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)（GitHub 写作和格式设置入门）

## <a name="additional-resources-for-microsoft-employees"></a>Microsoft 员工的其他资源
- [关联 GitHub 帐户和 MS 别名](https://review.docs.microsoft.com/en-us/windows-authoring-guide/github-account#2-connect-your-github-account-and-ms-alias-on-the-microsoft-open-source-portal)
- [编写 Markdown 的资源](https://review.docs.microsoft.com/en-us/windows-authoring-guide/writing-guidance/writing-markdown)
