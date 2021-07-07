## <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="5f9d3-101">Microsoft 开放源代码行为准则</span><span class="sxs-lookup"><span data-stu-id="5f9d3-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="5f9d3-102">此项目采用了 [Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="5f9d3-103">有关详细信息，请参阅[行为准则常见问题](https://opensource.microsoft.com/codeofconduct/faq/)，或如果有任何其他问题或意见，请与 [opencode@microsoft.com](mailto:opencode@microsoft.com) 联系。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

# <a name="how-to-contribute-to-windows-10-iotcore-documentation"></a><span data-ttu-id="5f9d3-104">如何参与撰写 Windows 10 IoT 核心版文档</span><span class="sxs-lookup"><span data-stu-id="5f9d3-104">How to contribute to Windows 10 IoTCore documentation</span></span>

## <a name="legal-notices"></a><span data-ttu-id="5f9d3-105">法律声明</span><span class="sxs-lookup"><span data-stu-id="5f9d3-105">Legal Notices</span></span>
<span data-ttu-id="5f9d3-106">Microsoft 及任何创作人按照[创作共用署名 4.0 国际公共许可](https://creativecommons.org/licenses/by/4.0/legalcode)授予你此存储中的 Microsoft 文档和其他内容的许可，请参阅[许可证](LICENSE)文件，并按照 [MIT 许可](https://opensource.org/licenses/MIT)授予你存储库中任何代码的许可，请参阅[许可证代码](LICENSE-CODE)文件。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-106">Microsoft and any contributors grant you a license to the Microsoft documentation and other content in this repository under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode), see the [LICENSE](LICENSE) file, and grant you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the [LICENSE-CODE](LICENSE-CODE) file.</span></span>

<span data-ttu-id="5f9d3-107">Microsoft、Windows、Microsoft Azure 和/或其他在本文档中引用的 Microsoft 产品和服务可能是 Microsoft 在美国和/或其他国家/地区的商标或注册商标。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-107">Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.</span></span>
<span data-ttu-id="5f9d3-108">该项目的许可证没有授予你使用任何 Microsoft 名称、徽标或商标的权利。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-108">The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.</span></span>
<span data-ttu-id="5f9d3-109">有关 Microsoft 的常规商标指南，可参看 http://go.microsoft.com/fwlink/?LinkID=254653 。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-109">Microsoft's general trademark guidelines can be found at http://go.microsoft.com/fwlink/?LinkID=254653.</span></span>

<span data-ttu-id="5f9d3-110">有关隐私信息，请参阅 https://privacy.microsoft.com/en-us/</span><span class="sxs-lookup"><span data-stu-id="5f9d3-110">Privacy information can be found at https://privacy.microsoft.com/en-us/</span></span>

<span data-ttu-id="5f9d3-111">Microsoft 和任何参与者通过暗示、禁止或其他方式保留其他所有权利，无论是他们各自的版权、专利权利，还是商标权利。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-111">Microsoft and any contributors reserve all others rights, whether under their respective copyrights, patents, or trademarks, whether by implication, estoppel or otherwise.</span></span>

## <a name="contributing"></a><span data-ttu-id="5f9d3-112">供稿</span><span class="sxs-lookup"><span data-stu-id="5f9d3-112">Contributing</span></span>

<span data-ttu-id="5f9d3-113">这是托管在 [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core) 上的 Windows 10 IoT **文档** 的存储库。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-113">This is the repository for Windows 10 IoT **documentation** hosted at [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core).</span></span>

<span data-ttu-id="5f9d3-114">如果希望看到新的报道或提供反馈，请考虑 [**投稿**](/CONTRIBUTING.md)。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-114">If you would like to see new coverage or have feedback, please consider [**contributing**](/CONTRIBUTING.md).</span></span>  <span data-ttu-id="5f9d3-115">可以编辑现有内容、添加新内容，或者直接创建新[问题](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues)。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-115">You can edit the existing content, add new content, or simply create new [issues](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues).</span></span> <span data-ttu-id="5f9d3-116">我们会查看你的建议，并争取将其纳入文档中。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-116">We’ll take a look at your suggestions and will work together to incorporate them into the docs.</span></span>

<span data-ttu-id="5f9d3-117">若要编辑内容，只需在要更改的文章中单击“编辑”即可：</span><span class="sxs-lookup"><span data-stu-id="5f9d3-117">To edit content, just click edit on the article you want to make changes to:</span></span>

![关于如何编辑文档的 Gif](windows-iotcore/media/edit-doc.gif)


<span data-ttu-id="5f9d3-119">也可通过克隆或下载存储库进行更改：</span><span class="sxs-lookup"><span data-stu-id="5f9d3-119">You can also clone or download the repo to make changes:</span></span>

![关于如何克隆或下载存储库的 Gif](windows-iotcore/media/download-repo.gif)

<span data-ttu-id="5f9d3-121">此外还需为拉取请求添加审阅者或审阅，这样我们才能批准它们：</span><span class="sxs-lookup"><span data-stu-id="5f9d3-121">You will also need to add a reviewer or reviews to your pull requests to get them approved:</span></span>

![为拉取请求添加审阅者](windows-iotcore/media/reviewers.gif)

# <a name="conventions"></a><span data-ttu-id="5f9d3-123">约定</span><span class="sxs-lookup"><span data-stu-id="5f9d3-123">Conventions</span></span>
  - <span data-ttu-id="5f9d3-124">添加某个页面时，必须在 [toc.md](windows-iotcore/TOC.md) 中为它添加一个条目，否则它不会显示。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-124">When adding a page, you must add an entry for it in [toc.md](windows-iotcore/TOC.md) for it to appear.</span></span>
  - <span data-ttu-id="5f9d3-125">一个文件夹可以包含多个文件夹或 `readme.md`</span><span class="sxs-lookup"><span data-stu-id="5f9d3-125">A folder can contain more folders or `readme.md`s</span></span>
  - <span data-ttu-id="5f9d3-126">文件夹/目录名称用短划线分隔（例如 `f12-tools`）并采用小写。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-126">Folder/directory names are dash-separated (e.g., `f12-tools`) and lowercase.</span></span> <span data-ttu-id="5f9d3-127">它们用在 docs.microsoft.com 站点上的 URL 中。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-127">They are used in URLs on the docs.microsoft.com site.</span></span> <span data-ttu-id="5f9d3-128">请勿使用下划线或 PascalCase/camelCase。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-128">Don't use underscores or PascalCase/camelCase.</span></span>


## <a name="other-text-elements"></a><span data-ttu-id="5f9d3-129">其他文本元素</span><span class="sxs-lookup"><span data-stu-id="5f9d3-129">Other text elements</span></span>

<span data-ttu-id="5f9d3-130">这些其他的文本元素有可用的样式设置：</span><span class="sxs-lookup"><span data-stu-id="5f9d3-130">These other text elements have styling available:</span></span>

* <span data-ttu-id="5f9d3-131">未经排序的列表</span><span class="sxs-lookup"><span data-stu-id="5f9d3-131">Unordered lists</span></span>
* <span data-ttu-id="5f9d3-132">使用常规项目符号</span><span class="sxs-lookup"><span data-stu-id="5f9d3-132">Have regular bullets</span></span>
   * <span data-ttu-id="5f9d3-133">也可将项目符号嵌套起来</span><span class="sxs-lookup"><span data-stu-id="5f9d3-133">You can also nest bullets</span></span>
   * <span data-ttu-id="5f9d3-134">项目符号列表应该有不止一个条目。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-134">Bullets lists should have more than one entry.</span></span>
* <span data-ttu-id="5f9d3-135">极标准</span><span class="sxs-lookup"><span data-stu-id="5f9d3-135">Pretty standard</span></span>

1. <span data-ttu-id="5f9d3-136">有序列表</span><span class="sxs-lookup"><span data-stu-id="5f9d3-136">Ordered lists</span></span>
2. <span data-ttu-id="5f9d3-137">使用常规编号或西式编号。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-137">Use regular ol' western-style numbering.</span></span>
3. <span data-ttu-id="5f9d3-138">只有在某个列表真的可以排序时才使用。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-138">Should be used only when a list truly has order.</span></span>

_________________________

<span data-ttu-id="5f9d3-139">提供水平规则。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-139">Horizontal rules are available.</span></span> <span data-ttu-id="5f9d3-140">建议谨慎使用，以免造成混乱。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-140">We suggest using them sparingly to reduce clutter.</span></span>
<span data-ttu-id="5f9d3-141">请勿将水平规则与标题标记组合使用；某些已针对视觉层次结构使用线条样式。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-141">Do not combine horizontal rules with heading tags; some already used line styles for visual hierarchy.</span></span>
<span data-ttu-id="5f9d3-142">另外，请勿将备注（见下）组合到编号列表中，</span><span class="sxs-lookup"><span data-stu-id="5f9d3-142">Also, do not combine notes (see below) in the middle of numbered lists.</span></span> <span data-ttu-id="5f9d3-143">否则会扰乱编号顺序。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-143">This messes with the numbering order.</span></span>

## <a name="displaying-code"></a><span data-ttu-id="5f9d3-144">显示代码</span><span class="sxs-lookup"><span data-stu-id="5f9d3-144">Displaying code</span></span>

<span data-ttu-id="5f9d3-145">可以使用内联 `code` Markdown 语法（使用反撇号）。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-145">You can use inline `code` Markdown syntax (with the backticks).</span></span>

<span data-ttu-id="5f9d3-146">也可这样显示代码块：</span><span class="sxs-lookup"><span data-stu-id="5f9d3-146">Or you can display blocks of code like so:</span></span>

```css
body {
    background: #fff;
}
```

## <a name="tables"></a><span data-ttu-id="5f9d3-147">表</span><span class="sxs-lookup"><span data-stu-id="5f9d3-147">Tables</span></span>

| <span data-ttu-id="5f9d3-148">可以</span><span class="sxs-lookup"><span data-stu-id="5f9d3-148">You can</span></span>     | <span data-ttu-id="5f9d3-149">使用标头</span><span class="sxs-lookup"><span data-stu-id="5f9d3-149">use headers</span></span> | <span data-ttu-id="5f9d3-150">在表中</span><span class="sxs-lookup"><span data-stu-id="5f9d3-150">on tables</span></span>    |
|-------------|-------------|-------------:|
| <span data-ttu-id="5f9d3-151">左对齐</span><span class="sxs-lookup"><span data-stu-id="5f9d3-151">Left-aligned</span></span>| <span data-ttu-id="5f9d3-152">除非使用 #</span><span class="sxs-lookup"><span data-stu-id="5f9d3-152">Unless a #</span></span>  | <span data-ttu-id="5f9d3-153">456</span><span class="sxs-lookup"><span data-stu-id="5f9d3-153">456</span></span>          |
| <span data-ttu-id="5f9d3-154">文本值</span><span class="sxs-lookup"><span data-stu-id="5f9d3-154">Text value</span></span>  | <span data-ttu-id="5f9d3-155">更多文本</span><span class="sxs-lookup"><span data-stu-id="5f9d3-155">More text</span></span>   | <span data-ttu-id="5f9d3-156">$0.00</span><span class="sxs-lookup"><span data-stu-id="5f9d3-156">$0.00</span></span>        |

## <a name="notes"></a><span data-ttu-id="5f9d3-157">注释</span><span class="sxs-lookup"><span data-stu-id="5f9d3-157">Notes</span></span>

<span data-ttu-id="5f9d3-158">请谨慎使用注释。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-158">Use notes sparingly.</span></span> <span data-ttu-id="5f9d3-159">注释是旨在突出显示“请勿错过”信息的块。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-159">They are blocks designed to highlight "don't-miss-it" information.</span></span>

<span data-ttu-id="5f9d3-160">我们有四个不同版本的目前已进行样式设置的注释：</span><span class="sxs-lookup"><span data-stu-id="5f9d3-160">We have four different versions of notes currently styled:</span></span>
- <span data-ttu-id="5f9d3-161">注意</span><span class="sxs-lookup"><span data-stu-id="5f9d3-161">NOTE</span></span>
- <span data-ttu-id="5f9d3-162">WARNING</span><span class="sxs-lookup"><span data-stu-id="5f9d3-162">WARNING</span></span>
- <span data-ttu-id="5f9d3-163">提示</span><span class="sxs-lookup"><span data-stu-id="5f9d3-163">TIP</span></span>
- <span data-ttu-id="5f9d3-164">重要事项</span><span class="sxs-lookup"><span data-stu-id="5f9d3-164">IMPORTANT</span></span>


<span data-ttu-id="5f9d3-165">对于多行块引用注释，请在每行注释前面使用 >，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-165">For multi-line blockquote notes, use a > in front of each line of the notes as seen in the example below.</span></span>

## <a name="images"></a><span data-ttu-id="5f9d3-166">映像</span><span class="sxs-lookup"><span data-stu-id="5f9d3-166">Images</span></span>

<span data-ttu-id="5f9d3-167">图像应该存储在 `media` 文件夹中，使用相对路径进行引用：</span><span class="sxs-lookup"><span data-stu-id="5f9d3-167">Images should be stored in a `media` folder and referenced with a relative path:</span></span>

`![Note patterns](media/notes.png)`


## <a name="code-of-conduct"></a><span data-ttu-id="5f9d3-168">行为准则</span><span class="sxs-lookup"><span data-stu-id="5f9d3-168">Code of Conduct</span></span>
<span data-ttu-id="5f9d3-169">此项目采用了 [Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-169">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span> <span data-ttu-id="5f9d3-170">有关详细信息，请参阅[行为准则常见问题](https://opensource.microsoft.com/codeofconduct/faq/)，或如果有任何其他问题或意见，请与 [opencode@microsoft.com](mailto:opencode@microsoft.com) 联系。</span><span class="sxs-lookup"><span data-stu-id="5f9d3-170">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>
