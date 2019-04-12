## <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="d20f2-101">Microsoft 开放源代码行为准则</span><span class="sxs-lookup"><span data-stu-id="d20f2-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="d20f2-102">此项目已采用[Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="d20f2-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="d20f2-103">有关详细信息请参阅[代码的行为准则常见问题解答](https://opensource.microsoft.com/codeofconduct/faq/)或联系[ opencode@microsoft.com ](mailto:opencode@microsoft.com)与任何其他问题或意见。</span><span class="sxs-lookup"><span data-stu-id="d20f2-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

# <a name="how-to-contribute-to-windows-10-iotcore-documentation"></a><span data-ttu-id="d20f2-104">如何参与编辑 Windows 10 IoTCore 文档</span><span class="sxs-lookup"><span data-stu-id="d20f2-104">How to contribute to Windows 10 IoTCore documentation</span></span>

## <a name="legal-notices"></a><span data-ttu-id="d20f2-105">法律声明</span><span class="sxs-lookup"><span data-stu-id="d20f2-105">Legal Notices</span></span>
<span data-ttu-id="d20f2-106">Microsoft 及任何创作人按照[创作共用署名 4.0 国际公共许可](https://creativecommons.org/licenses/by/4.0/legalcode)授予你此存储中的 Microsoft 文档和其他内容的许可，请参阅[许可证](LICENSE)文件，并按照 [MIT 许可](https://opensource.org/licenses/MIT)授予你存储库中任何代码的许可，请参阅[许可证代码](LICENSE-CODE)文件。</span><span class="sxs-lookup"><span data-stu-id="d20f2-106">Microsoft and any contributors grant you a license to the Microsoft documentation and other content in this repository under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode), see the [LICENSE](LICENSE) file, and grant you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the [LICENSE-CODE](LICENSE-CODE) file.</span></span>

<span data-ttu-id="d20f2-107">本文档中引用的 Microsoft、Windows、Microsoft Azure 和/或其他 Microsoft 产品和服务是 Microsoft 在美国和/或其他国际/地区的商标或注册商标。</span><span class="sxs-lookup"><span data-stu-id="d20f2-107">Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.</span></span>
<span data-ttu-id="d20f2-108">此项目的许可证并未授予你使用任何 Microsoft 名称、徽标或商标的权利。</span><span class="sxs-lookup"><span data-stu-id="d20f2-108">The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.</span></span>
<span data-ttu-id="d20f2-109">Microsoft 的一般商标准则，请参阅 http://go.microsoft.com/fwlink/?LinkID=254653。</span><span class="sxs-lookup"><span data-stu-id="d20f2-109">Microsoft's general trademark guidelines can be found at http://go.microsoft.com/fwlink/?LinkID=254653.</span></span>

<span data-ttu-id="d20f2-110">可以在发现的隐私信息 https://privacy.microsoft.com/en-us/</span><span class="sxs-lookup"><span data-stu-id="d20f2-110">Privacy information can be found at https://privacy.microsoft.com/en-us/</span></span>

<span data-ttu-id="d20f2-111">Microsoft 及任何创作人保留所有其他权利（无论是其各自的版权、专利或商标），无论是通过默示、禁止否认的方式还是以其他方式。</span><span class="sxs-lookup"><span data-stu-id="d20f2-111">Microsoft and any contributors reserve all others rights, whether under their respective copyrights, patents, or trademarks, whether by implication, estoppel or otherwise.</span></span>

## <a name="contributing"></a><span data-ttu-id="d20f2-112">参与</span><span class="sxs-lookup"><span data-stu-id="d20f2-112">Contributing</span></span>

<span data-ttu-id="d20f2-113">这是存储库，适用于 Windows 10 IoT**文档**托管于[ https://docs.microsoft.com/windows/iot-core ](https://docs.microsoft.com/windows/iot-core)。</span><span class="sxs-lookup"><span data-stu-id="d20f2-113">This is the repository for Windows 10 IoT **documentation** hosted at [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core).</span></span>

<span data-ttu-id="d20f2-114">如果想要了解新的覆盖范围或有任何反馈，请考虑[**参与**](/CONTRIBUTING.md)。</span><span class="sxs-lookup"><span data-stu-id="d20f2-114">If you would like to see new coverage or have feedback, please consider [**contributing**](/CONTRIBUTING.md).</span></span>  <span data-ttu-id="d20f2-115">可以编辑现有的内容、 添加新的内容，或只需创建新[问题](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues)。</span><span class="sxs-lookup"><span data-stu-id="d20f2-115">You can edit the existing content, add new content, or simply create new [issues](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues).</span></span> <span data-ttu-id="d20f2-116">我们来看看您的建议，并将协同工作来将其合并到文档。</span><span class="sxs-lookup"><span data-stu-id="d20f2-116">We’ll take a look at your suggestions and will work together to incorporate them into the docs.</span></span>

<span data-ttu-id="d20f2-117">若要编辑内容，只需单击编辑在想要对注册表进行更改的文章：</span><span class="sxs-lookup"><span data-stu-id="d20f2-117">To edit content, just click edit on the article you want to make changes to:</span></span>

![有关如何编辑文档的 Gif](windows-iotcore/media/edit-doc.gif)


<span data-ttu-id="d20f2-119">您还可以克隆或下载存储库进行更改：</span><span class="sxs-lookup"><span data-stu-id="d20f2-119">You can also clone or download the repo to make changes:</span></span>

![如何克隆或下载存储库上的 Gif](windows-iotcore/media/download-repo.gif)

<span data-ttu-id="d20f2-121">您还需要将审阅者或评论添加到拉取请求来获取批准它们：</span><span class="sxs-lookup"><span data-stu-id="d20f2-121">You will also need to add a reviewer or reviews to your pull requests to get them approved:</span></span>

![将审阅者添加到你的拉取请求](windows-iotcore/media/reviewers.gif)

# <a name="conventions"></a><span data-ttu-id="d20f2-123">约定</span><span class="sxs-lookup"><span data-stu-id="d20f2-123">Conventions</span></span>
  - <span data-ttu-id="d20f2-124">在添加一个页面时，您必须添加一个条目中为其[toc.md](windows-iotcore/TOC.md)它才会显示。</span><span class="sxs-lookup"><span data-stu-id="d20f2-124">When adding a page, you must add an entry for it in [toc.md](windows-iotcore/TOC.md) for it to appear.</span></span>
  - <span data-ttu-id="d20f2-125">一个文件夹可以包含更多的文件夹或`readme.md`s</span><span class="sxs-lookup"><span data-stu-id="d20f2-125">A folder can contain more folders or `readme.md`s</span></span>
  - <span data-ttu-id="d20f2-126">文件夹/目录名称是短划线分隔 (例如， `f12-tools`) 和大小写。</span><span class="sxs-lookup"><span data-stu-id="d20f2-126">Folder/directory names are dash-separated (e.g., `f12-tools`) and lowercase.</span></span> <span data-ttu-id="d20f2-127">Docs.microsoft.com 网站上的 Url 中使用它们。</span><span class="sxs-lookup"><span data-stu-id="d20f2-127">They are used in URLs on the docs.microsoft.com site.</span></span> <span data-ttu-id="d20f2-128">不要使用下划线或 pascal 命名法/驼峰式大小写。</span><span class="sxs-lookup"><span data-stu-id="d20f2-128">Don't use underscores or PascalCase/camelCase.</span></span>


## <a name="other-text-elements"></a><span data-ttu-id="d20f2-129">其他文本元素</span><span class="sxs-lookup"><span data-stu-id="d20f2-129">Other text elements</span></span>

<span data-ttu-id="d20f2-130">这些其他文本元素具有样式设置可用：</span><span class="sxs-lookup"><span data-stu-id="d20f2-130">These other text elements have styling available:</span></span>

* <span data-ttu-id="d20f2-131">未排序的列表</span><span class="sxs-lookup"><span data-stu-id="d20f2-131">Unordered lists</span></span>
* <span data-ttu-id="d20f2-132">具有常规项目符号</span><span class="sxs-lookup"><span data-stu-id="d20f2-132">Have regular bullets</span></span>
   * <span data-ttu-id="d20f2-133">此外可以嵌套项目符号</span><span class="sxs-lookup"><span data-stu-id="d20f2-133">You can also nest bullets</span></span>
   * <span data-ttu-id="d20f2-134">项目符号列表应具有多个条目。</span><span class="sxs-lookup"><span data-stu-id="d20f2-134">Bullets lists should have more than one entry.</span></span>
* <span data-ttu-id="d20f2-135">漂亮的标准</span><span class="sxs-lookup"><span data-stu-id="d20f2-135">Pretty standard</span></span>

1. <span data-ttu-id="d20f2-136">排序的列表</span><span class="sxs-lookup"><span data-stu-id="d20f2-136">Ordered lists</span></span>
2. <span data-ttu-id="d20f2-137">使用正则这可怜的家伙 western 样式编号。</span><span class="sxs-lookup"><span data-stu-id="d20f2-137">Use regular ol' western-style numbering.</span></span>
3. <span data-ttu-id="d20f2-138">仅当真正有顺序的列表时，才应使用。</span><span class="sxs-lookup"><span data-stu-id="d20f2-138">Should be used only when a list truly has order.</span></span>

_________________________

<span data-ttu-id="d20f2-139">水平规则可使用。</span><span class="sxs-lookup"><span data-stu-id="d20f2-139">Horizontal rules are available.</span></span> <span data-ttu-id="d20f2-140">我们建议尽量少使用它们来减少混乱。</span><span class="sxs-lookup"><span data-stu-id="d20f2-140">We suggest using them sparingly to reduce clutter.</span></span>
<span data-ttu-id="d20f2-141">与标题标记，则不要混用水平标尺一些已对可视层次结构使用线条样式。</span><span class="sxs-lookup"><span data-stu-id="d20f2-141">Do not combine horizontal rules with heading tags; some already used line styles for visual hierarchy.</span></span>
<span data-ttu-id="d20f2-142">此外，不要混用中间编号列表的说明 （见下文）。</span><span class="sxs-lookup"><span data-stu-id="d20f2-142">Also, do not combine notes (see below) in the middle of numbered lists.</span></span> <span data-ttu-id="d20f2-143">这都在困扰着编号顺序。</span><span class="sxs-lookup"><span data-stu-id="d20f2-143">This messes with the numbering order.</span></span>

## <a name="displaying-code"></a><span data-ttu-id="d20f2-144">显示代码</span><span class="sxs-lookup"><span data-stu-id="d20f2-144">Displaying code</span></span>

<span data-ttu-id="d20f2-145">可以使用内联`code`Markdown 语法 （使用反撇号）。</span><span class="sxs-lookup"><span data-stu-id="d20f2-145">You can use inline `code` Markdown syntax (with the backticks).</span></span>

<span data-ttu-id="d20f2-146">也可以显示的代码块如下所示：</span><span class="sxs-lookup"><span data-stu-id="d20f2-146">Or you can display blocks of code like so:</span></span>

```css
body {
    background: #fff;
}
```

## <a name="tables"></a><span data-ttu-id="d20f2-147">表</span><span class="sxs-lookup"><span data-stu-id="d20f2-147">Tables</span></span>

| <span data-ttu-id="d20f2-148">你可以</span><span class="sxs-lookup"><span data-stu-id="d20f2-148">You can</span></span>     | <span data-ttu-id="d20f2-149">使用标头</span><span class="sxs-lookup"><span data-stu-id="d20f2-149">use headers</span></span> | <span data-ttu-id="d20f2-150">上表</span><span class="sxs-lookup"><span data-stu-id="d20f2-150">on tables</span></span>    |
|-------------|-------------|-------------:|
| <span data-ttu-id="d20f2-151">左对齐</span><span class="sxs-lookup"><span data-stu-id="d20f2-151">Left-aligned</span></span>| <span data-ttu-id="d20f2-152">除非 #</span><span class="sxs-lookup"><span data-stu-id="d20f2-152">Unless a #</span></span>  | <span data-ttu-id="d20f2-153">456</span><span class="sxs-lookup"><span data-stu-id="d20f2-153">456</span></span>          |
| <span data-ttu-id="d20f2-154">文本值</span><span class="sxs-lookup"><span data-stu-id="d20f2-154">Text value</span></span>  | <span data-ttu-id="d20f2-155">更多的文本</span><span class="sxs-lookup"><span data-stu-id="d20f2-155">More text</span></span>   | <span data-ttu-id="d20f2-156">$0.00</span><span class="sxs-lookup"><span data-stu-id="d20f2-156">$0.00</span></span>        |

## <a name="notes"></a><span data-ttu-id="d20f2-157">说明</span><span class="sxs-lookup"><span data-stu-id="d20f2-157">Notes</span></span>

<span data-ttu-id="d20f2-158">尽量少使用说明。</span><span class="sxs-lookup"><span data-stu-id="d20f2-158">Use notes sparingly.</span></span> <span data-ttu-id="d20f2-159">它们是块旨在突出显示"无-未命中的 it"信息。</span><span class="sxs-lookup"><span data-stu-id="d20f2-159">They are blocks designed to highlight "don't-miss-it" information.</span></span>

<span data-ttu-id="d20f2-160">我们有四个不同版本的当前样式的说明：</span><span class="sxs-lookup"><span data-stu-id="d20f2-160">We have four different versions of notes currently styled:</span></span>
- <span data-ttu-id="d20f2-161">注意</span><span class="sxs-lookup"><span data-stu-id="d20f2-161">NOTE</span></span>
- <span data-ttu-id="d20f2-162">警告</span><span class="sxs-lookup"><span data-stu-id="d20f2-162">WARNING</span></span>
- <span data-ttu-id="d20f2-163">提示</span><span class="sxs-lookup"><span data-stu-id="d20f2-163">TIP</span></span>
- <span data-ttu-id="d20f2-164">重要提示</span><span class="sxs-lookup"><span data-stu-id="d20f2-164">IMPORTANT</span></span>


<span data-ttu-id="d20f2-165">对于多行块引用说明，请使用 > 的说明，如下面的示例中所示的每一行的前面。</span><span class="sxs-lookup"><span data-stu-id="d20f2-165">For multi-line blockquote notes, use a > in front of each line of the notes as seen in the example below.</span></span>

## <a name="images"></a><span data-ttu-id="d20f2-166">映像</span><span class="sxs-lookup"><span data-stu-id="d20f2-166">Images</span></span>

<span data-ttu-id="d20f2-167">图像应存储在`media`文件夹和相对路径引用：</span><span class="sxs-lookup"><span data-stu-id="d20f2-167">Images should be stored in a `media` folder and referenced with a relative path:</span></span>

`![Note patterns](media/notes.png)`


## <a name="code-of-conduct"></a><span data-ttu-id="d20f2-168">行为准则</span><span class="sxs-lookup"><span data-stu-id="d20f2-168">Code of Conduct</span></span>
<span data-ttu-id="d20f2-169">此项目已采用[Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="d20f2-169">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span> <span data-ttu-id="d20f2-170">有关详细信息请参阅[代码的行为准则常见问题解答](https://opensource.microsoft.com/codeofconduct/faq/)或联系[ opencode@microsoft.com ](mailto:opencode@microsoft.com)与任何其他问题或意见。</span><span class="sxs-lookup"><span data-stu-id="d20f2-170">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>
