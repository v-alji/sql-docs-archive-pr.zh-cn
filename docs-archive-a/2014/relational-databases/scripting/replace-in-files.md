---
title: 在文件中替换
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Replace in Files dialog box
ms.assetid: 51191c0a-e022-41d6-8473-5cb3c6596862
author: rothja
ms.author: jroth
ms.openlocfilehash: ad7f23cfc8ec083d5cf2d7dcadefd3a8c27176e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578789"
---
# <a name="replace-in-files"></a><span data-ttu-id="2d8fe-102">在文件中替换</span><span class="sxs-lookup"><span data-stu-id="2d8fe-102">Replace in Files</span></span>
  <span data-ttu-id="2d8fe-103">使用“查找和替换”窗口的 **“在文件中替换”** 选项卡可以在指定文件集的代码中搜索某个字符串或表达式，并且可以更改找到的部分匹配或全部匹配项。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-103">The **Replace in Files** tab of the Find and Replace window enables you to search the code of a specified set of files for a string or expression and change some or all of the matches found.</span></span> <span data-ttu-id="2d8fe-104">在 **“结果选项”** 中所选的“查找结果”窗口将列出找到的匹配项和执行的操作。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-104">The matches found and actions taken are listed in the Find Results window selected in **Result Options**.</span></span>  
  
 <span data-ttu-id="2d8fe-105">您也可使用工具栏按钮和快捷键打开 **“查找和替换”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-105">Toolbar buttons and shortcut keys are also available to open the **Find and Replace** dialog box.</span></span>  
  
## <a name="find-what"></a><span data-ttu-id="2d8fe-106">查找内容</span><span class="sxs-lookup"><span data-stu-id="2d8fe-106">Find What</span></span>  
 <span data-ttu-id="2d8fe-107">使用 **“在文件中替换”** 选项卡上的这些控件，可以指定要匹配的字符串或表达式。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-107">These controls on the **Replace in Files** tab enable you to specify the string or expression that will be matched.</span></span>  
  
 <span data-ttu-id="2d8fe-108">**查找内容**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-108">**Find what**</span></span>  
 <span data-ttu-id="2d8fe-109">键入要搜索的文本。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-109">Type the text to search for.</span></span> <span data-ttu-id="2d8fe-110">对话框会尝试使用在打开该对话框前用光标选择的文本、光标附近的文本或以前搜索过的文本，来填充可能的搜索文本。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-110">The dialog box attempts to fill in a probable search text, using text selected with the cursor before opening the dialog box, or nearby text, or previously searched-for text.</span></span> <span data-ttu-id="2d8fe-111">通过从此下拉列表中选择字符串，可以重用最近搜索过的 20 个字符串之一。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-111">You can reuse one of the last 20 search strings by selecting it from this drop-down list.</span></span>  
  
 <span data-ttu-id="2d8fe-112">**[带有通配符的字符串]**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-112">**[string with wildcards]**</span></span>  
 <span data-ttu-id="2d8fe-113">如果要在搜索字符串中使用通配符，如星号 (`*`) 和问号 (`?`)，请选中“查找选项”下的“使用”复选框，然后单击“通配符”。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-113">If you want to use wildcards such as asterisks (`*`) and question marks (`?`) in your search string, select the **Use** check box under **Find Options** and then click **Wildcards**.</span></span>  
  
 <span data-ttu-id="2d8fe-114">**[正则表达式]**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-114">**[regular expression]**</span></span>  
 <span data-ttu-id="2d8fe-115">若要设置搜索引擎将搜索字符串解释为正则表达式，请选中“查找选项”下的“使用”复选框，然后单击“正则表达式”。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-115">To cause the search engine to interpret your search string as a regular expression, select the **Use** check box under **Find Options** and then click **Regular expressions**.</span></span>  
  
 <span data-ttu-id="2d8fe-116">**表达式生成器**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-116">**Expression Builder**</span></span>  
 <span data-ttu-id="2d8fe-117">如果选中“查找选项”中的“使用”复选框，则“查找内容”框旁边的三角形按钮变为可用状态。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-117">This triangular button next to the **Find what** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="2d8fe-118">单击此按钮将显示通配符或正则表达式列表，具体情况取决于所选的 **“使用”** 选项。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-118">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="2d8fe-119">从此列表中任选一项，即可将其添加到 **“查找内容”** 框中指定的字符串。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-119">Choosing any item from this list adds it to the string specified in the **Find what** box.</span></span>  
  
## <a name="replace-with"></a><span data-ttu-id="2d8fe-120">替换为</span><span class="sxs-lookup"><span data-stu-id="2d8fe-120">Replace With</span></span>  
 <span data-ttu-id="2d8fe-121">使用这些控件，可以指定将插入到匹配字符串或表达式位置的内容。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-121">These controls enable you to specify what will be inserted in the place of the matched string or expression.</span></span>  
  
 <span data-ttu-id="2d8fe-122">**Replace with**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-122">**Replace with**</span></span>  
 <span data-ttu-id="2d8fe-123">若要使用其他字符串替换“查找内容”  中指定字符串的实例，请在此字段中输入替换字符串。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-123">To replace instances of the string specified in **Find what** with another string, enter the replacement string in this field.</span></span> <span data-ttu-id="2d8fe-124">若要删除在 **“查找内容”** 中指定的字符串实例，请将此框保留为空。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-124">To delete instances of the string specified in **Find what**, leave this box blank.</span></span> <span data-ttu-id="2d8fe-125">选择下拉列表，以显示最近输入的 20 个项。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-125">Select the drop-down list to display the last 20 items entered.</span></span> <span data-ttu-id="2d8fe-126">若要在 **“替换为”** 框中指定的字符串中包括正则表达式，请单击 **“使用”** 复选框，再单击 **“正则表达式”** 选项。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-126">To include regular expressions in the string specified in the **Replace with** box, click the **Use** check box and then click the **Regular Expressions** option.</span></span>  
  
 <span data-ttu-id="2d8fe-127">**表达式生成器**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-127">**Expression Builder**</span></span>  
 <span data-ttu-id="2d8fe-128">如果选中“查找选项”中的“使用”复选框，则“替换为”框旁边的三角形按钮变为可用状态。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-128">This triangular button next to the **Replace with** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="2d8fe-129">单击此按钮将显示通配符或正则表达式列表，具体情况取决于所选的 **“使用”** 选项。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-129">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="2d8fe-130">单击此列表中的任意项，即可将其添加到 **“替换为”** 框中指定的字符串。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-130">Clicking any item in this list adds it to the string specified in the **Replace with** box.</span></span>  
  
 <span data-ttu-id="2d8fe-131">**替换**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-131">**Replace**</span></span>  
 <span data-ttu-id="2d8fe-132">单击此按钮用“替换为”框中指定的字符串替换在“查找内容”中指定的字符串的当前实例，然后在“查找范围”中指定的范围内查找下一个实例。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-132">Click this button to replace the current instance of the string specified in **Find what** with the string specified in the **Replace with** box, and find the next instance within the scope specified in **Look in**.</span></span>  
  
 <span data-ttu-id="2d8fe-133">**全部替换**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-133">**Replace all**</span></span>  
 <span data-ttu-id="2d8fe-134">单击此按钮可在“查找范围”中指定的范围内的所有文件中，使用“替换为”框中指定的字符串替换“查找内容”中指定的字符串的所有实例。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-134">Click this button to replace all instances of the string specified in **Find what** with the string specified in the **Replace with** box, in all files within the scope specified in **Look in**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2d8fe-135">请确保将“查找范围”  设置为仅包含要修改的文件。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-135">Make sure that **Look in** is set to include only those files that you want to modify.</span></span>  
  
 <span data-ttu-id="2d8fe-136">此时，将显示一条提醒，其中包含一个 **“保持将已修改的文件打开”** 选项。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-136">A reminder is displayed that includes a **Keep modified files open** option.</span></span> <span data-ttu-id="2d8fe-137">若要保留 **“撤消”** 选项，您必须选择此选项。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-137">To retain the **Undo** option, you must select this option.</span></span> <span data-ttu-id="2d8fe-138">**“撤消”** 只在修改后仍保持打开状态以进行编辑的文件中可用。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-138">**Undo** is only available in files that remain open for editing after they are modified.</span></span>  
  
 <span data-ttu-id="2d8fe-139">**跳过文件**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-139">**Skip File**</span></span>  
 <span data-ttu-id="2d8fe-140">当“查找范围”  包括多个文件时此按钮可用。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-140">Becomes available when **Look in** includes multiple files.</span></span> <span data-ttu-id="2d8fe-141">如果不希望搜索或修改当前文件，请单击此按钮。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-141">Click this button if you do not want to search or modify the current file.</span></span> <span data-ttu-id="2d8fe-142">此时，将继续在 **“查找范围”** 列表中的下一个文件内进行搜索。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-142">The search will continue in the next file on the list in **Look in**.</span></span>  
  
## <a name="look-in"></a><span data-ttu-id="2d8fe-143">查找范围</span><span class="sxs-lookup"><span data-stu-id="2d8fe-143">Look In</span></span>  
 <span data-ttu-id="2d8fe-144">从“查找范围”  下拉列表中选择的选项，将确定“在文件中替换”  是只搜索当前活动的文件还是搜索存储在特定文件夹内的所有文件。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-144">The option chosen from the **Look in** drop-down list determines whether **Replace in Files** searches only in currently active files or searches all files stored within certain folders.</span></span> <span data-ttu-id="2d8fe-145">请从列表中选择搜索范围，键入文件夹路径，或单击 **“浏览”** 按钮以显示 **“自定义目录集”** 对话框，然后选择要搜索的文件夹集。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-145">Select a search scope from the list, type a folder path, or click the **Browse** button to display the **Custom Directory Set** dialog box and choose a set of folders to search.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d8fe-146">如果选择的“查找范围”  选项会对已从源代码管理中签出的文件进行搜索，则将只搜索已下载到本地计算机的文件版本。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-146">If the **Look in** option selected causes you to search a file that you have checked out from source code control, only the version of that file which has been downloaded to your local computer is searched.</span></span>  
  
 <span data-ttu-id="2d8fe-147">**Look in**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-147">**Look in**</span></span>  
 <span data-ttu-id="2d8fe-148">从此列表中选择预定义的搜索范围，或使用“自定义目录集”  对话框输入你自己的目录集。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-148">Select a predefined search scope from this list, or use the **Custom Directory Set** dialog box to enter your own set of directories.</span></span>  
  
 <span data-ttu-id="2d8fe-149">**当前文档**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-149">**Current Document**</span></span>  
 <span data-ttu-id="2d8fe-150">当在编辑器中打开了一个文档时，此选项可用。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-150">This option is available when a document is open in an editor.</span></span> <span data-ttu-id="2d8fe-151">只在活动文档中搜索在 **“查找内容”** 中指定的字符串。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-151">Searches only the active document for the string specified in **Find what**.</span></span>  
  
 <span data-ttu-id="2d8fe-152">**所有打开的文档**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-152">**All Open Documents**</span></span>  
 <span data-ttu-id="2d8fe-153">搜索当前打开以供编辑的所有文件。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-153">Searches all files currently opened for editing.</span></span>  
  
 <span data-ttu-id="2d8fe-154">**当前项目**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-154">**Current Project**</span></span>  
 <span data-ttu-id="2d8fe-155">搜索活动项目中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-155">Searches all files in the active project.</span></span>  
  
 <span data-ttu-id="2d8fe-156">**整个解决方案**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-156">**Entire Solution**</span></span>  
 <span data-ttu-id="2d8fe-157">搜索活动解决方案中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-157">Searches all files in the active solution.</span></span>  
  
 <span data-ttu-id="2d8fe-158">**包括子文件夹**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-158">**Include subfolders**</span></span>  
 <span data-ttu-id="2d8fe-159">指定将搜索在“查找范围”  中指定的文件夹的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-159">Specifies that subfolders of the folder specified in **Look in** will be searched.</span></span> <span data-ttu-id="2d8fe-160">它需要指定自定义目录集。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-160">It requires a custom directory set.</span></span>  
  
 <span data-ttu-id="2d8fe-161">**浏览(...)**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-161">**Browse (...)**</span></span>  
 <span data-ttu-id="2d8fe-162">单击此按钮将显示“选择搜索文件夹”  对话框，在其中可以汇集、编辑、保存和选择要输入到“查找范围”  框中的命名目录集。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-162">Click this button to display the **Choose Search Folders** dialog box, where you can assemble, edit, save, and select named sets of directories to enter in the **Look in** box.</span></span>  
  
## <a name="find-options"></a><span data-ttu-id="2d8fe-163">查找选项</span><span class="sxs-lookup"><span data-stu-id="2d8fe-163">Find Options</span></span>  
 <span data-ttu-id="2d8fe-164">您可以展开或折叠 **“查找选项”** 部分。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-164">You can expand or collapse the **Find Options** section.</span></span> <span data-ttu-id="2d8fe-165">您可以选中或清除下列选项：</span><span class="sxs-lookup"><span data-stu-id="2d8fe-165">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="2d8fe-166">**匹配大小写**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-166">**Match case**</span></span>  
 <span data-ttu-id="2d8fe-167">选中此复选框后，“查找结果”窗口将仅显示与“查找内容”  中指定的字符串的内容和大小写均匹配的字符串实例。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-167">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched both by content and by case.</span></span> <span data-ttu-id="2d8fe-168">例如，在选中 **“匹配大小写”** 复选框的情况下搜索 **MyObject** 将返回“MyObject”，但不会返回“myobject”或“MYOBJECT”。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-168">For example, a search for **MyObject** with the **Match case** check box selected will return "MyObject" but not "myobject" or "MYOBJECT".</span></span>  
  
 <span data-ttu-id="2d8fe-169">**全字匹配**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-169">**Match whole word**</span></span>  
 <span data-ttu-id="2d8fe-170">选中此复选框后，“查找结果”窗口将仅显示与“查找内容”  中指定的字符串全字匹配的字符串实例。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-170">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched in complete words.</span></span> <span data-ttu-id="2d8fe-171">例如，搜索 **MyObject** 将返回“MyObject”，而不会返回“CMyObject”或“MyObjectC”。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-171">For example, a search for **MyObject** will return "MyObject" but not "CMyObject" or "MyObjectC."</span></span>  
  
 <span data-ttu-id="2d8fe-172">**使用**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-172">**Use**</span></span>  
 <span data-ttu-id="2d8fe-173">指示如何解释“查找内容”  或“替换为”  文本框中输入的特殊字符。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-173">Indicates how to interpret special characters entered in the **Find what** or **Replace with** text boxes.</span></span> <span data-ttu-id="2d8fe-174">选项包括 **“通配符”** 和 **“正则表达式”** 。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-174">The options include **Wildcards** and **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="2d8fe-175">**“正则表达式”**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-175">**Regular Expressions**</span></span>  
 <span data-ttu-id="2d8fe-176">定义文本匹配模式的特殊表示法。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-176">Special notations define patterns of text to match.</span></span> <span data-ttu-id="2d8fe-177">有关列表，请参阅 [使用正则表达式搜索文本](search-text-with-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-177">For a list, see [Search Text with Regular Expressions](search-text-with-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="2d8fe-178">**通配符**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-178">**Wildcards**</span></span>  
 <span data-ttu-id="2d8fe-179">用于表示一个或多个字符特殊字符，如星号 (`*`) 和问号 (`?`)。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-179">Special characters such as asterisks (`*`) and question marks (`?`) represent one or more characters.</span></span> <span data-ttu-id="2d8fe-180">有关列表，请参阅 [使用通配符搜索文本](search-text-with-wildcards.md)。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-180">For a list, see [Search Text with Wildcards](search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="2d8fe-181">**查找以下文件类型**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-181">**Look at these file types**</span></span>  
 <span data-ttu-id="2d8fe-182">此列表指示要在“查找范围”  中指定的目录中搜索的文件的类型。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-182">This list indicates the types of files to search through in the directories specified in **Look in**.</span></span> <span data-ttu-id="2d8fe-183">如果此框保留为空，将搜索在 **“查找范围”** 中指定的目录中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-183">If this box is left blank, all of the files in the directories specified in **Look in** will be searched.</span></span>  
  
```  
*.[ext]; *.[ext] (manual)  
```  
  
 <span data-ttu-id="2d8fe-184">若要查找特定类型的文件，请输入星号通配符 (`*`) 作为文件名，然后输入句点 (`.`) 和文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-184">To find files of a particular type, enter an asterisk wildcard (`*`) for the file name, followed by a period (`.`) and the file extension.</span></span> <span data-ttu-id="2d8fe-185">若要查找多种文件类型，请以分号 (`;`) 分隔输入多个搜索字符串。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-185">To find more than one file type, enter multiple search strings separated by a semicolon (`;`).</span></span>  
  
```  
*.[ext]; *.[ext] (from list)  
```  
  
 <span data-ttu-id="2d8fe-186">选择列表中的任意项，以输入将查找特定类型文件的预配置搜索字符串。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-186">Select any item in the list to enter a preconfigured search string that will find files of particular types.</span></span>  
  
## <a name="result-options"></a><span data-ttu-id="2d8fe-187">“结果选项”</span><span class="sxs-lookup"><span data-stu-id="2d8fe-187">Result Options</span></span>  
 <span data-ttu-id="2d8fe-188">您可以展开或折叠 **“结果选项”** 部分。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-188">You can expand or collapse the **Result Options** section.</span></span> <span data-ttu-id="2d8fe-189">您可以选中或清除下列选项：</span><span class="sxs-lookup"><span data-stu-id="2d8fe-189">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="2d8fe-190">**“查找结果 1”窗口**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-190">**Find Results 1 window**</span></span>  
 <span data-ttu-id="2d8fe-191">如果选中此复选框，则当前搜索的结果将追加到“查找结果 1”窗口内容的末尾。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-191">When this check box is selected, the results of the current search will be appended to the content of the Find Results 1 window.</span></span> <span data-ttu-id="2d8fe-192">此窗口将自动打开，以显示搜索结果。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-192">This window opens automatically to display your search results.</span></span> <span data-ttu-id="2d8fe-193">若要手动打开此窗口，请在 **“视图”** 菜单上，单击 **“其他窗口”** ，再单击 **“查找结果 1”** 。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-193">To open this window manually, click **Other Windows** on the **View** menu and then click **Find Results 1**.</span></span>  
  
 <span data-ttu-id="2d8fe-194">**查找结果 2 窗口**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-194">**Find Results 2 window**</span></span>  
 <span data-ttu-id="2d8fe-195">如果选中此复选框，则当前搜索的结果将追加到“查找结果 2”窗口内容的末尾。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-195">When this check box is selected selected, the results of the current search will be appended to the content of the Find Results 2 window.</span></span> <span data-ttu-id="2d8fe-196">此窗口将自动打开，以显示搜索结果。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-196">This window opens automatically to display your search results.</span></span> <span data-ttu-id="2d8fe-197">若要手动打开此窗口，请在“视图”  菜单上，单击“其他窗口”  ，再单击“查找结果 2”  。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-197">To open this window manually, click **Other Windows** on the **View** menu and then click **Find Results 2**.</span></span>  
  
 <span data-ttu-id="2d8fe-198">**只显示文件名**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-198">**Display file names only**</span></span>  
 <span data-ttu-id="2d8fe-199">在“查找结果 1”或“查找结果 2”窗口中，对于包含搜索匹配内容的每个文件将显示一项，而不是每个搜索匹配内容均显示一项。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-199">Displays one entry per file containing a search match rather than one entry per search match in either the Find Results 1 or Find Results 2 window.</span></span> <span data-ttu-id="2d8fe-200">此选项在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中不可用。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-200">This option is not available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="2d8fe-201">**全部替换后保持将已修改的文件打开**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-201">**Keep modified files open after Replace All**</span></span>  
 <span data-ttu-id="2d8fe-202">如果选中，则所有替换过的文件都保持打开状态，以便您可以撤消操作或保存更改。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-202">When selected, leaves open all files in which replacements have been made, so you can undo or save the changes.</span></span> <span data-ttu-id="2d8fe-203">内存方面的制约可能会限制在替换操作之后可以保持打开的文件数。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-203">Memory constraints might limit the number of files that can remain open after a replace operation.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2d8fe-204">只能对保持打开状态以供编辑的文件使用 **“撤消”** 选项。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-204">You can use **Undo** only on files that remain open for editing.</span></span> <span data-ttu-id="2d8fe-205">如果未选择此选项，则尚未打开以供编辑的文件继续处于关闭状态，并且在这些文件中 **“撤消”** 选项不可用。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-205">If this option is not selected, files that were not already open for editing will remain closed, and no **Undo** option will be available in those files.</span></span>  
  
## <a name="find-and-replace-views"></a><span data-ttu-id="2d8fe-206">“查找和替换”视图</span><span class="sxs-lookup"><span data-stu-id="2d8fe-206">Find and Replace Views</span></span>  
 <span data-ttu-id="2d8fe-207">“查找和替换”窗口顶部的选项卡包含“视图”  菜单。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-207">The tabs at the top of the Findand Replace window include **View** menus.</span></span> <span data-ttu-id="2d8fe-208">使用这些菜单，可以选择在活动窗格中显示的不同字段。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-208">These menus enable you to choose a set of fields to display in the active pane.</span></span> <span data-ttu-id="2d8fe-209">您可以将“查找和替换”窗口停靠在方便的位置，然后在各个选项卡之间以及各个视图之间进行切换，以执行任意类型的查找或替换操作。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-209">You can leave the Find and Replace window docked in a convenient location, and then change from tab to tab and view to view to perform any type of find or replace operation.</span></span>  
  
 <span data-ttu-id="2d8fe-210">**切换到快速查找**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-210">**Switch to Quick Find**</span></span>  
 <span data-ttu-id="2d8fe-211">使用此工具栏选项卡，将把对话框更改为“快速查找”  对话框。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-211">This toolbar tab changes the dialog box to a **Quick Find** dialog box.</span></span>  
  
 <span data-ttu-id="2d8fe-212">**切换到在文件中查找**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-212">**Switch to Find in Files**</span></span>  
 <span data-ttu-id="2d8fe-213">使用此工具栏选项卡，将把对话框更改为“在文件中查找”  对话框。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-213">This toolbar tab changes the dialog box to a **Find in Files** dialog box.</span></span>  
  
 <span data-ttu-id="2d8fe-214">**切换到查找符号**</span><span class="sxs-lookup"><span data-stu-id="2d8fe-214">**Switch to Find Symbols**</span></span>  
 <span data-ttu-id="2d8fe-215">使用此工具栏选项卡，将把对话框更改为“在符号中查找”  对话框。</span><span class="sxs-lookup"><span data-stu-id="2d8fe-215">This toolbar tab changes the dialog box to a **Find in Symbols** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d8fe-216">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d8fe-216">See Also</span></span>  
 [<span data-ttu-id="2d8fe-217">SQL Server Management Studio 键盘快捷键</span><span class="sxs-lookup"><span data-stu-id="2d8fe-217">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
