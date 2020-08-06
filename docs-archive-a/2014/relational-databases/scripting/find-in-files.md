---
title: 在文件中查找
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Find in Files dialog box
ms.assetid: bf92770a-33df-43ef-85ad-5a9223649b98
author: rothja
ms.author: jroth
ms.openlocfilehash: a7bd3051817198fb22e2bf7e96393ddf2023b703
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590721"
---
# <a name="find-in-files"></a><span data-ttu-id="49bba-102">在文件中查找</span><span class="sxs-lookup"><span data-stu-id="49bba-102">Find in Files</span></span>
  <span data-ttu-id="49bba-103">使用“查找和替换”窗口的 **“在文件中查找”** 选项卡，您可以在指定文件集的代码中搜索字符串或表达式。</span><span class="sxs-lookup"><span data-stu-id="49bba-103">The **Find in Files** tab of the Find and Replace window enables you to search the code of a specified set of files for a string or expression.</span></span> <span data-ttu-id="49bba-104">在 **“结果选项”** 中所选的“查找结果”窗口将列出找到的匹配项和执行的操作。</span><span class="sxs-lookup"><span data-stu-id="49bba-104">The matches found and actions taken are listed in the Find Results window selected in **Result Options**.</span></span>  
  
 <span data-ttu-id="49bba-105">您也可使用工具栏按钮和快捷键打开 **“查找和替换”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="49bba-105">Toolbar buttons and shortcut keys are also available to open the **Find and Replace** dialog box.</span></span>  
  
 <span data-ttu-id="49bba-106">以下部分列出了 **“在文件中查找”** 选项卡上可用的控件。</span><span class="sxs-lookup"><span data-stu-id="49bba-106">The sections that follow list controls available on the **Find in Files** tab.</span></span>  
  
## <a name="find-what"></a><span data-ttu-id="49bba-107">查找内容</span><span class="sxs-lookup"><span data-stu-id="49bba-107">Find What</span></span>  
 <span data-ttu-id="49bba-108">使用 **“在文件中查找”** 选项卡上的这些控件，可以指定要匹配的字符串或表达式。</span><span class="sxs-lookup"><span data-stu-id="49bba-108">These controls on the **Find in Files** tab enable you to specify the string or expression that will be matched.</span></span>  
  
 <span data-ttu-id="49bba-109">**查找内容**</span><span class="sxs-lookup"><span data-stu-id="49bba-109">**Find what**</span></span>  
 <span data-ttu-id="49bba-110">键入要搜索的文本。</span><span class="sxs-lookup"><span data-stu-id="49bba-110">Type the text to search for.</span></span> <span data-ttu-id="49bba-111">对话框会尝试使用在打开该对话框前用光标选择的文本、光标附近的文本或以前搜索过的文本，来填充可能的搜索文本。</span><span class="sxs-lookup"><span data-stu-id="49bba-111">The dialog box attempts to fill in a probable search text, using text selected with the cursor before opening the dialog box, or nearby text, or previously searched-for text.</span></span> <span data-ttu-id="49bba-112">通过从此下拉列表中选择字符串，可以重用最近搜索过的 20 个字符串之一。</span><span class="sxs-lookup"><span data-stu-id="49bba-112">You can reuse one of the last 20 search strings by selecting it from this drop-down list.</span></span>  
  
 <span data-ttu-id="49bba-113">**[带有通配符的字符串]**</span><span class="sxs-lookup"><span data-stu-id="49bba-113">**[string with wildcards]**</span></span>  
 <span data-ttu-id="49bba-114">如果要在搜索字符串中使用通配符，如星号 (`*`) 和问号 (`?`)，请选中“查找选项”\*\*\*\* 下的“使用”\*\*\*\* 复选框，然后单击“通配符”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49bba-114">If you want to use wildcards such as asterisks (`*`) and question marks (`?`) in your search string, select the **Use** check box under **Find Options** and then click **Wildcards**.</span></span>  
  
 <span data-ttu-id="49bba-115">**[正则表达式]**</span><span class="sxs-lookup"><span data-stu-id="49bba-115">**[regular expression]**</span></span>  
 <span data-ttu-id="49bba-116">若要设置搜索引擎将搜索字符串解释为正则表达式，请选中“查找选项”\*\*\*\* 下的“使用”\*\*\*\* 复选框，然后单击“正则表达式”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49bba-116">To cause the search engine to interpret your search string as a regular expression, select the **Use** check box under **Find Options** and then click **Regular expressions**.</span></span>  
  
 <span data-ttu-id="49bba-117">**表达式生成器**</span><span class="sxs-lookup"><span data-stu-id="49bba-117">**Expression Builder**</span></span>  
 <span data-ttu-id="49bba-118">如果选中“查找选项”\*\*\*\* 中的“使用”\*\*\*\* 复选框，则“查找内容”\*\*\*\* 框旁边的三角形按钮变为可用状态。</span><span class="sxs-lookup"><span data-stu-id="49bba-118">This triangular button next to the **Find what** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="49bba-119">单击此按钮将显示通配符或正则表达式列表，具体情况取决于所选的 **“使用”** 选项。</span><span class="sxs-lookup"><span data-stu-id="49bba-119">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="49bba-120">从此列表中选择任何项都会将所选项添加到 **“查找内容”** 字符串。</span><span class="sxs-lookup"><span data-stu-id="49bba-120">Choosing any item from this list adds it to the **Find what** string.</span></span>  
  
## <a name="look-in"></a><span data-ttu-id="49bba-121">查找范围</span><span class="sxs-lookup"><span data-stu-id="49bba-121">Look In</span></span>  
 <span data-ttu-id="49bba-122">从“查找范围”\*\*\*\* 下拉列表中选择的选项将确定“在文件中查找”\*\*\*\* 是仅在当前活动文件中搜索，还是在特定文件夹内存储的所有文件中搜索。</span><span class="sxs-lookup"><span data-stu-id="49bba-122">The option chosen from the **Look in** drop-down list determines whether **Find in Files** searches only in currently active files or in all files stored within certain folders.</span></span> <span data-ttu-id="49bba-123">请从列表中选择搜索范围，键入文件夹路径，或单击 **“浏览”** 按钮以显示 **“自定义目录集”** 对话框，然后选择要搜索的文件夹集。</span><span class="sxs-lookup"><span data-stu-id="49bba-123">Select a search scope from the list, type a folder path, or click the **Browse** button to display the **Custom Directory Set Dialog Box** and choose a set of folders to search.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49bba-124"> 如果选择的 **“查找范围”** 选项会对已从源代码管理中签出的文件进行搜索，则将只搜索已下载到本地计算机的文件版本。</span><span class="sxs-lookup"><span data-stu-id="49bba-124">If the **Look in** option selected causes you to search a file that you have checked out from source code control, only the version of that file which has been downloaded to your local computer is searched.</span></span>  
  
 <span data-ttu-id="49bba-125">**查找范围**</span><span class="sxs-lookup"><span data-stu-id="49bba-125">**Look in**</span></span>  
 <span data-ttu-id="49bba-126">从此列表中选择预定义的搜索范围，或使用“自定义目录集”\*\*\*\* 对话框输入你自己的目录集。</span><span class="sxs-lookup"><span data-stu-id="49bba-126">Select a predefined search scope from this list, or use the **Custom Directory Set** dialog box to enter your own set of directories.</span></span>  
  
 <span data-ttu-id="49bba-127">**当前文档**</span><span class="sxs-lookup"><span data-stu-id="49bba-127">**Current Document**</span></span>  
 <span data-ttu-id="49bba-128">当在编辑器中打开了一个文档时，此选项可用。</span><span class="sxs-lookup"><span data-stu-id="49bba-128">This option is available when a document is open in an editor.</span></span> <span data-ttu-id="49bba-129">只在活动文档中搜索在 **“查找内容”** 中指定的字符串。</span><span class="sxs-lookup"><span data-stu-id="49bba-129">It searches only the active document for the string in **Find what**.</span></span>  
  
 <span data-ttu-id="49bba-130">**所有打开的文档**</span><span class="sxs-lookup"><span data-stu-id="49bba-130">**All Open Documents**</span></span>  
 <span data-ttu-id="49bba-131">搜索当前打开以供编辑的所有文件。</span><span class="sxs-lookup"><span data-stu-id="49bba-131">Searches all files currently opened for editing.</span></span>  
  
 <span data-ttu-id="49bba-132">**当前项目**</span><span class="sxs-lookup"><span data-stu-id="49bba-132">**Current Project**</span></span>  
 <span data-ttu-id="49bba-133">搜索活动项目中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="49bba-133">Searches all files in the active project.</span></span>  
  
 <span data-ttu-id="49bba-134">**整个解决方案**</span><span class="sxs-lookup"><span data-stu-id="49bba-134">**Entire Solution**</span></span>  
 <span data-ttu-id="49bba-135">搜索活动解决方案中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="49bba-135">Searches all files in the active solution.</span></span>  
  
 <span data-ttu-id="49bba-136">**包括子文件夹**</span><span class="sxs-lookup"><span data-stu-id="49bba-136">**Include subfolders**</span></span>  
 <span data-ttu-id="49bba-137">指定将搜索在“查找范围”\*\*\*\* 中指定的文件夹的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="49bba-137">Specifies that subfolders of the folder specified in **Look in** will be searched.</span></span> <span data-ttu-id="49bba-138">它需要指定自定义目录集。</span><span class="sxs-lookup"><span data-stu-id="49bba-138">It requires a custom directory set.</span></span>  
  
 <span data-ttu-id="49bba-139">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="49bba-139">**Browse**</span></span>  
 <span data-ttu-id="49bba-140">单击此按钮将显示“自定义目录集”\*\*\*\* 对话框，在其中可以汇编、编辑、保存和选择要输入到“查找范围”\*\*\*\* 框中的命名目录集。</span><span class="sxs-lookup"><span data-stu-id="49bba-140">Click this button to display the **Custom Directory Set** dialog box, where you can assemble, edit, save, and select named sets of directories to enter in the **Look in** box.</span></span>  
  
## <a name="find-options"></a><span data-ttu-id="49bba-141">查找选项</span><span class="sxs-lookup"><span data-stu-id="49bba-141">Find Options</span></span>  
 <span data-ttu-id="49bba-142">您可以展开或折叠 **“查找选项”** 部分。</span><span class="sxs-lookup"><span data-stu-id="49bba-142">You can expand or collapse the **Find Options** section.</span></span> <span data-ttu-id="49bba-143">您可以选中或清除下列选项：</span><span class="sxs-lookup"><span data-stu-id="49bba-143">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="49bba-144">**匹配大小写**</span><span class="sxs-lookup"><span data-stu-id="49bba-144">**Match case**</span></span>  
 <span data-ttu-id="49bba-145">选中此复选框后，“查找结果”窗口将仅显示与“查找内容”\*\*\*\* 中指定的字符串的内容和大小写均匹配的字符串实例。</span><span class="sxs-lookup"><span data-stu-id="49bba-145">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched both by content and by case.</span></span> <span data-ttu-id="49bba-146">例如，在选中 "**匹配大小写**" 复选框的情况下搜索**MyObject**将返回 "MyObject"，而不是 "MYOBJECT" 或 "MyObject"。</span><span class="sxs-lookup"><span data-stu-id="49bba-146">For example, a search for **MyObject** with the **Match case** check box selected will return "MyObject" but not "myobject" or "MYOBJECT."</span></span>  
  
 <span data-ttu-id="49bba-147">**全字匹配**</span><span class="sxs-lookup"><span data-stu-id="49bba-147">**Match whole word**</span></span>  
 <span data-ttu-id="49bba-148">选中此复选框后，“查找结果”窗口将仅显示与“查找内容”\*\*\*\* 中指定的字符串全字匹配的字符串实例。</span><span class="sxs-lookup"><span data-stu-id="49bba-148">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched in complete words.</span></span> <span data-ttu-id="49bba-149">例如，搜索 **MyObject** 将返回“MyObject”，而不会返回“CMyObject”或“MyObjectC”。</span><span class="sxs-lookup"><span data-stu-id="49bba-149">For example, a search for **MyObject** will return "MyObject" but not "CMyObject" or "MyObjectC."</span></span>  
  
 <span data-ttu-id="49bba-150">**使用**</span><span class="sxs-lookup"><span data-stu-id="49bba-150">**Use**</span></span>  
 <span data-ttu-id="49bba-151">指示如何解释“查找内容”\*\*\*\* 或“替换为”\*\*\*\* 文本框中输入的特殊字符。</span><span class="sxs-lookup"><span data-stu-id="49bba-151">Indicates how to interpret special characters entered in the **Find what** or **Replace with** text boxes.</span></span> <span data-ttu-id="49bba-152">选项包括 **“通配符”** 和 **“正则表达式”**。</span><span class="sxs-lookup"><span data-stu-id="49bba-152">The options include **Wildcards** and **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="49bba-153">**正则表达式**</span><span class="sxs-lookup"><span data-stu-id="49bba-153">**Regular Expressions**</span></span>  
 <span data-ttu-id="49bba-154">定义文本匹配模式的特殊表示法。</span><span class="sxs-lookup"><span data-stu-id="49bba-154">Special notations define patterns of text to match.</span></span> <span data-ttu-id="49bba-155">有关列表，请参阅 [使用正则表达式搜索文本](search-text-with-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="49bba-155">For a list, see [Search Text with Regular Expressions](search-text-with-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="49bba-156">**通配符**</span><span class="sxs-lookup"><span data-stu-id="49bba-156">**Wildcards**</span></span>  
 <span data-ttu-id="49bba-157">用于表示一个或多个字符特殊字符，如星号 (`*`) 和问号 (`?`)。</span><span class="sxs-lookup"><span data-stu-id="49bba-157">Special characters such as asterisks (`*`) and question marks (`?`) represent one or more characters.</span></span> <span data-ttu-id="49bba-158">有关列表，请参阅 [使用通配符搜索文本](search-text-with-wildcards.md)。</span><span class="sxs-lookup"><span data-stu-id="49bba-158">For a list, see [Search Text with Wildcards](search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="49bba-159">**查找以下文件类型**</span><span class="sxs-lookup"><span data-stu-id="49bba-159">**Look at these file types**</span></span>  
 <span data-ttu-id="49bba-160">此列表指示要在“查找范围”\*\*\*\* 中指定的目录中搜索的文件的类型。</span><span class="sxs-lookup"><span data-stu-id="49bba-160">This list indicates the types of files to search through in the directories specified in **Look in**.</span></span> <span data-ttu-id="49bba-161">如果此字段保留为空，将搜索 **“查找范围”** 中指定的目录中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="49bba-161">If this field is left blank, all of the files in the directories specified in **Look in** will be searched.</span></span>  
  
```  
*.[ext]; *.[ext] (manual)  
```  
  
 <span data-ttu-id="49bba-162">若要查找特定类型的文件，请输入星号通配符 (`*`) 作为文件名，然后输入句点 (`.`) 和文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="49bba-162">To find files of a particular type, enter an asterisk wildcard (`*`) for the file name, followed by a period (`.`) and the file extension.</span></span> <span data-ttu-id="49bba-163">若要查找多种文件类型，请以分号 (`;`) 分隔输入多个搜索字符串。</span><span class="sxs-lookup"><span data-stu-id="49bba-163">To find more than one file type, enter multiple search strings separated by a semicolon (`;`).</span></span>  
  
```  
*.[ext]; *.[ext] (from list)  
```  
  
 <span data-ttu-id="49bba-164">选择列表中的任意项，以输入将查找特定类型文件的预配置搜索字符串。</span><span class="sxs-lookup"><span data-stu-id="49bba-164">Select any item in the list to enter a preconfigured search string that will find files of particular types.</span></span>  
  
## <a name="result-options"></a><span data-ttu-id="49bba-165">“结果选项”</span><span class="sxs-lookup"><span data-stu-id="49bba-165">Result Options</span></span>  
 <span data-ttu-id="49bba-166">确定单击 **“查找全部”** 后查找结果的位置。</span><span class="sxs-lookup"><span data-stu-id="49bba-166">Determines the location of the results when you click **Find All**.</span></span> <span data-ttu-id="49bba-167">您可以展开或折叠 **“结果选项”** 部分。</span><span class="sxs-lookup"><span data-stu-id="49bba-167">You can expand or collapse the **Result Options** section.</span></span> <span data-ttu-id="49bba-168">您可以选中或清除下列选项：</span><span class="sxs-lookup"><span data-stu-id="49bba-168">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="49bba-169">**“查找结果 1”窗口**</span><span class="sxs-lookup"><span data-stu-id="49bba-169">**Find Results 1 window**</span></span>  
 <span data-ttu-id="49bba-170">如果选中此复选框，则当前搜索的结果将追加到“查找结果 1”窗口内容的末尾。</span><span class="sxs-lookup"><span data-stu-id="49bba-170">When this check box is selected, the results of the current search will be appended to the content of the Find Results 1 window.</span></span> <span data-ttu-id="49bba-171">此窗口将自动打开，以显示搜索结果。</span><span class="sxs-lookup"><span data-stu-id="49bba-171">This window opens automatically to display your search results.</span></span> <span data-ttu-id="49bba-172">若要手动打开此窗口，请在 **“视图”** 菜单上，单击 **“其他窗口”** ，再单击 **“查找结果 1”**。</span><span class="sxs-lookup"><span data-stu-id="49bba-172">To open this window manually, click **Other Windows** on the **View** menu and then click **Find Results 1**.</span></span>  
  
 <span data-ttu-id="49bba-173">**查找结果 2 窗口**</span><span class="sxs-lookup"><span data-stu-id="49bba-173">**Find Results 2 window**</span></span>  
 <span data-ttu-id="49bba-174">如果选中此复选框，则当前搜索的结果将追加到“查找结果 2”窗口内容的末尾。</span><span class="sxs-lookup"><span data-stu-id="49bba-174">When this check box is selected, the results of the current search will be appended to the content of the Find Results 2 window.</span></span> <span data-ttu-id="49bba-175">此窗口将自动打开，以显示搜索结果。</span><span class="sxs-lookup"><span data-stu-id="49bba-175">This window opens automatically to display your search results.</span></span> <span data-ttu-id="49bba-176">若要手动打开此窗口，请在“视图” \*\*\*\* 菜单上，单击“其他窗口” \*\*\*\* ，再单击“查找结果 2” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49bba-176">To open this window manually, click **Other Windows** on the **View** menu and then click **Find Results 2**.</span></span>  
  
 <span data-ttu-id="49bba-177">**只显示文件名**</span><span class="sxs-lookup"><span data-stu-id="49bba-177">**Display file names only**</span></span>  
 <span data-ttu-id="49bba-178">在“查找结果 1”或“查找结果 2”窗口中，对于包含搜索匹配内容的每个文件将显示一项，而不是每个搜索匹配内容均显示一项。</span><span class="sxs-lookup"><span data-stu-id="49bba-178">Displays one entry per file containing a search match rather than one entry per search match in either the Find Results 1 or Find Results 2 window.</span></span> <span data-ttu-id="49bba-179">此选项在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中不可用。</span><span class="sxs-lookup"><span data-stu-id="49bba-179">This option is not available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="49bba-180">**全部替换后保持将已修改的文件打开**</span><span class="sxs-lookup"><span data-stu-id="49bba-180">**Keep modified files open after Replace All**</span></span>  
 <span data-ttu-id="49bba-181">如果选中，则所有替换过的文件都保持打开状态，以便您可以撤消操作或保存更改。</span><span class="sxs-lookup"><span data-stu-id="49bba-181">When selected, leaves open all files in which replacements have been made, so you can undo or save the changes.</span></span> <span data-ttu-id="49bba-182">内存方面的制约可能会限制在替换操作之后可以保持打开的文件数。</span><span class="sxs-lookup"><span data-stu-id="49bba-182">Memory constraints might limit the number of files that can remain open after a replace operation.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="49bba-183">只能对保持打开状态以供编辑的文件使用 **“撤消”** 选项。</span><span class="sxs-lookup"><span data-stu-id="49bba-183">You can use **Undo** only on files that remain open for editing.</span></span> <span data-ttu-id="49bba-184">如果未选择此选项，则尚未打开以供编辑的文件继续处于关闭状态，并且在这些文件中 **“撤消”** 选项不可用。</span><span class="sxs-lookup"><span data-stu-id="49bba-184">If this option is not selected, files that were not already open for editing will remain closed, and no **Undo** option will be available in those files.</span></span>  
  
## <a name="find-and-replace-views"></a><span data-ttu-id="49bba-185">“查找和替换”视图</span><span class="sxs-lookup"><span data-stu-id="49bba-185">Find and Replace Views</span></span>  
 <span data-ttu-id="49bba-186">“查找和替换”窗口顶部的选项卡包含 **“视图”** 菜单。</span><span class="sxs-lookup"><span data-stu-id="49bba-186">The tabs at the top of the Find and Replace window include **View** menus.</span></span> <span data-ttu-id="49bba-187">使用这些菜单，可以选择在活动窗格中显示的不同字段。</span><span class="sxs-lookup"><span data-stu-id="49bba-187">These menus enable you to choose a set of fields to display in the active pane.</span></span> <span data-ttu-id="49bba-188">您可以将“查找和替换”窗口停靠在方便的位置，然后在各个选项卡之间以及各个视图之间进行切换，以执行任意类型的查找或替换操作。</span><span class="sxs-lookup"><span data-stu-id="49bba-188">You can leave the Find and Replace window docked in a convenient location and then change from tab to tab and view to view to perform any type of find or replace operation.</span></span>  
  
 <span data-ttu-id="49bba-189">**切换到快速查找**</span><span class="sxs-lookup"><span data-stu-id="49bba-189">**Switch to Quick Find**</span></span>  
 <span data-ttu-id="49bba-190">使用此工具栏选项卡，将把对话框更改为“快速查找”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="49bba-190">This toolbar tab changes the dialog box to a **Quick Find** dialog box.</span></span>  
  
 <span data-ttu-id="49bba-191">**切换到在文件中查找**</span><span class="sxs-lookup"><span data-stu-id="49bba-191">**Switch to Find in Files**</span></span>  
 <span data-ttu-id="49bba-192">使用此工具栏选项卡，将把对话框更改为“在文件中查找”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="49bba-192">This toolbar tab changes the dialog box to a **Find in Files** dialog box.</span></span>  
  
 <span data-ttu-id="49bba-193">**切换到查找符号**</span><span class="sxs-lookup"><span data-stu-id="49bba-193">**Switch to Find Symbols**</span></span>  
 <span data-ttu-id="49bba-194">使用此工具栏选项卡，将把对话框更改为“在符号中查找”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="49bba-194">This toolbar tab changes the dialog box to a **Find in Symbols** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49bba-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49bba-195">See Also</span></span>  
 [<span data-ttu-id="49bba-196">SQL Server Management Studio 键盘快捷键</span><span class="sxs-lookup"><span data-stu-id="49bba-196">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
