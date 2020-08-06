---
title: 查找和替换
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Find and Replace dialog box
ms.assetid: 09297893-d80b-4c88-86b4-52bfb639e521
author: rothja
ms.author: jroth
ms.openlocfilehash: 9735c2c7271382e3b25ce2b50299153f16882ef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590722"
---
# <a name="find-and-replace"></a><span data-ttu-id="2d99d-102">查找和替换</span><span class="sxs-lookup"><span data-stu-id="2d99d-102">Find and Replace</span></span>
  <span data-ttu-id="2d99d-103">使用 **“查找和替换”** 对话框可以在文件中查找特定文本，并且可以选择是否替换文本。</span><span class="sxs-lookup"><span data-stu-id="2d99d-103">Use the **Find and Replace** dialog box to locate text within a file and optionally replace it.</span></span> <span data-ttu-id="2d99d-104">根据 **“查找和替换”** 对话框打开方式的不同，将显示不同版本的对话框，其中的选项会稍有差异。</span><span class="sxs-lookup"><span data-stu-id="2d99d-104">Versions of the **Find and Replace** dialog box with slightly different options can appear, depending on how the dialog box was opened.</span></span> <span data-ttu-id="2d99d-105">在 **“编辑”** 菜单上，指向 **“查找和替换”** ，再单击 **“快速查找”** ，可打开包含查找选项的对话框，但其中不包含替换选项。</span><span class="sxs-lookup"><span data-stu-id="2d99d-105">On the **Edit** menu, point to **Find and Replace**, and then click **Quick Find** to open the dialog box with find options, but without replace options.</span></span> <span data-ttu-id="2d99d-106">在 **“编辑”** 菜单上，指向 **“查找和替换”** ，再单击 **“快速替换”** ，可打开包含查找选项和替换选项的对话框。</span><span class="sxs-lookup"><span data-stu-id="2d99d-106">On the **Edit** menu, point to **Find and Replace**, and then click **Quick Replace** to open the dialog box with both find options and replace options.</span></span>  
  
 <span data-ttu-id="2d99d-107">您也可使用工具栏按钮和快捷键打开 **“查找和替换”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="2d99d-107">Toolbar buttons and shortcut keys are also available to open the **Find and Replace** dialog box.</span></span>  
  
## <a name="find-what"></a><span data-ttu-id="2d99d-108">查找内容</span><span class="sxs-lookup"><span data-stu-id="2d99d-108">Find What</span></span>  
 <span data-ttu-id="2d99d-109">使用这些控件可以指定要匹配的字符串或表达式。</span><span class="sxs-lookup"><span data-stu-id="2d99d-109">These controls enable you to specify the string or expression that will be matched.</span></span>  
  
 <span data-ttu-id="2d99d-110">**查找内容**</span><span class="sxs-lookup"><span data-stu-id="2d99d-110">**Find what**</span></span>  
 <span data-ttu-id="2d99d-111">键入要搜索的文本。</span><span class="sxs-lookup"><span data-stu-id="2d99d-111">Type the text to search for.</span></span> <span data-ttu-id="2d99d-112">对话框会尝试使用在打开该对话框前用光标选择的文本、光标附近的文本或以前搜索过的文本，来填充可能的搜索文本。</span><span class="sxs-lookup"><span data-stu-id="2d99d-112">The dialog box attempts to fill in a probable search text, using text selected with the cursor before opening the dialog box, or nearby text, or previously searched-for text.</span></span> <span data-ttu-id="2d99d-113">通过从此下拉列表中选择字符串，可以重用最近搜索过的 20 个字符串之一。</span><span class="sxs-lookup"><span data-stu-id="2d99d-113">You can reuse one of the last 20 search strings by selecting it from this drop-down list.</span></span>  
  
 <span data-ttu-id="2d99d-114">**[带有通配符的字符串]**</span><span class="sxs-lookup"><span data-stu-id="2d99d-114">**[string with wildcards]**</span></span>  
 <span data-ttu-id="2d99d-115">如果要在搜索字符串中使用通配符，如星号 (`*`) 和问号 (`?`)，请选中“查找选项”下的“使用”复选框，然后单击“通配符”。</span><span class="sxs-lookup"><span data-stu-id="2d99d-115">If you want to use wildcards such as asterisks (`*`) and question marks (`?`) in your search string, select the **Use** check box under **Find Options** and then click **Wildcards**.</span></span>  
  
 <span data-ttu-id="2d99d-116">**[正则表达式]**</span><span class="sxs-lookup"><span data-stu-id="2d99d-116">**[regular expression]**</span></span>  
 <span data-ttu-id="2d99d-117">若要设置搜索引擎将搜索字符串解释为正则表达式，请选中“查找选项”下的“使用”复选框，然后单击“正则表达式”。</span><span class="sxs-lookup"><span data-stu-id="2d99d-117">To cause the search engine to interpret your search string as a regular expression, select the **Use** check box under **Find Options** and then click **Regular expressions**.</span></span>  
  
 <span data-ttu-id="2d99d-118">**表达式生成器**</span><span class="sxs-lookup"><span data-stu-id="2d99d-118">**Expression Builder**</span></span>  
 <span data-ttu-id="2d99d-119">如果选中“查找选项”中的“使用”复选框，则“查找内容”框旁边的三角形按钮变为可用状态。</span><span class="sxs-lookup"><span data-stu-id="2d99d-119">This triangular button next to the **Find what** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="2d99d-120">单击此按钮将显示通配符或正则表达式列表，具体情况取决于所选的 **“使用”** 选项。</span><span class="sxs-lookup"><span data-stu-id="2d99d-120">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="2d99d-121">从此列表中任选一项，即可将其添加到 **“查找内容”** 框中指定的字符串。</span><span class="sxs-lookup"><span data-stu-id="2d99d-121">Choosing any item from this list adds it to the string specified in the **Find what** box.</span></span>  
  
## <a name="replace-with"></a><span data-ttu-id="2d99d-122">替换为</span><span class="sxs-lookup"><span data-stu-id="2d99d-122">Replace With</span></span>  
 <span data-ttu-id="2d99d-123">使用这些控件，可以指定将插入到匹配字符串或表达式位置的内容。</span><span class="sxs-lookup"><span data-stu-id="2d99d-123">These controls enable you to specify what will be inserted in the place of the matched string or expression.</span></span>  
  
 <span data-ttu-id="2d99d-124">**Replace with**</span><span class="sxs-lookup"><span data-stu-id="2d99d-124">**Replace with**</span></span>  
 <span data-ttu-id="2d99d-125">若要使用其他字符串替换“查找内容”  中指定字符串的实例，请在此字段中输入替换字符串。</span><span class="sxs-lookup"><span data-stu-id="2d99d-125">To replace instances of the string specified in **Find what** with another string, enter the replacement string in this field.</span></span> <span data-ttu-id="2d99d-126">若要删除 **“查找内容”** 框中指定文本的实例，请将此字段保留为空白。</span><span class="sxs-lookup"><span data-stu-id="2d99d-126">To delete instances of the text specified in **Find what**, leave this field blank.</span></span> <span data-ttu-id="2d99d-127">选择下拉列表，以显示最近输入的 20 个项。</span><span class="sxs-lookup"><span data-stu-id="2d99d-127">Select the drop-down list to display the last 20 items entered.</span></span> <span data-ttu-id="2d99d-128">若要使 **“替换为”** 框中指定的字符串包含正则表达式，请单击 **“使用”** 复选框，然后单击 **“正则表达式”** 。</span><span class="sxs-lookup"><span data-stu-id="2d99d-128">To include regular expressions in the string specified in the **Replace with** box, click the **Use** check box and then click **Regular Expressions**.</span></span> <span data-ttu-id="2d99d-129">只有在通过单击 **“快速替换”** 打开此对话框时，才会显示此框。</span><span class="sxs-lookup"><span data-stu-id="2d99d-129">This box only appears if this dialog box was opened by clicked **Quick Replace**.</span></span>  
  
 <span data-ttu-id="2d99d-130">**Replace with**</span><span class="sxs-lookup"><span data-stu-id="2d99d-130">**Replace with**</span></span>  
 <span data-ttu-id="2d99d-131">若要使用其他字符串替换“查找内容”  框中指定字符串的实例，请在此字段中输入替换字符串。</span><span class="sxs-lookup"><span data-stu-id="2d99d-131">To replace instances of the string specified in the **Find what** box with another string, enter the replacement string in this field.</span></span> <span data-ttu-id="2d99d-132">若要删除 **“查找内容”** 框中指定字符串的实例，请将此字段保留为空白。</span><span class="sxs-lookup"><span data-stu-id="2d99d-132">To delete instances of the string specified in the **Find what** box, leave this field blank.</span></span> <span data-ttu-id="2d99d-133">选择下拉列表，以显示最近输入的 20 个项。</span><span class="sxs-lookup"><span data-stu-id="2d99d-133">Select the drop-down list to display the last 20 items entered.</span></span> <span data-ttu-id="2d99d-134">若要使 **“替换为”** 框中指定的字符串包含正则表达式，请单击 **“使用”** 复选框，然后单击 **“正则表达式”** 。</span><span class="sxs-lookup"><span data-stu-id="2d99d-134">To include regular expressions in the string specified in the **Replace with** box, click the **Use** check box and then click **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="2d99d-135">**表达式生成器**</span><span class="sxs-lookup"><span data-stu-id="2d99d-135">**Expression Builder**</span></span>  
 <span data-ttu-id="2d99d-136">如果选中“查找选项”中的“使用”复选框，则“替换为”框旁边的三角形按钮变为可用状态。</span><span class="sxs-lookup"><span data-stu-id="2d99d-136">This triangular button next to the **Replace with** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="2d99d-137">单击此按钮将显示通配符或正则表达式列表，具体情况取决于所选的 **“使用”** 选项。</span><span class="sxs-lookup"><span data-stu-id="2d99d-137">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="2d99d-138">单击此列表中的任意项，即可将其添加到 **“替换为”** 框中指定的字符串。</span><span class="sxs-lookup"><span data-stu-id="2d99d-138">Clicking any item in this list adds it to the string specified in the **Replace with** box.</span></span>  
  
 <span data-ttu-id="2d99d-139">**替换**</span><span class="sxs-lookup"><span data-stu-id="2d99d-139">**Replace**</span></span>  
 <span data-ttu-id="2d99d-140">单击此按钮可使用“替换为” 框中指定的字符串替换“查找内容”框中指定字符串的当前实例，并在“查找范围”框中指定的范围内查找下一个实例。</span><span class="sxs-lookup"><span data-stu-id="2d99d-140">Click this button to replace the current instance of the string specified in the **Find what** box with the string specified in the **Replace with** box, and find the next instance within the scope specified in **Look in**.</span></span>  
  
 <span data-ttu-id="2d99d-141">**全部替换**</span><span class="sxs-lookup"><span data-stu-id="2d99d-141">**Replace all**</span></span>  
 <span data-ttu-id="2d99d-142">单击此按钮可在“查找范围” 框指定范围内的所有文件中，使用“替换为”框中指定的字符串替换“查找内容”框中指定字符串的所有实例。</span><span class="sxs-lookup"><span data-stu-id="2d99d-142">Click this button to replace all instances of the string specified in the **Find what** box with the string specified in the **Replace with** box, in all files within the scope specified in the **Look in** box.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2d99d-143">请确保将“查找范围”  设置为仅包含要修改的文件。</span><span class="sxs-lookup"><span data-stu-id="2d99d-143">Make sure that **Look in** is set to include only those files that you want to modify.</span></span>  
  
 <span data-ttu-id="2d99d-144">此时，将显示一条提醒，其中包含一个 **“保持将已修改的文件打开”** 选项。</span><span class="sxs-lookup"><span data-stu-id="2d99d-144">A reminder is displayed that includes a **Keep modified files open** option.</span></span> <span data-ttu-id="2d99d-145">若要保留 **“撤消”** 选项，您必须选择此选项。</span><span class="sxs-lookup"><span data-stu-id="2d99d-145">To retain the **Undo** option, you must select this option.</span></span> <span data-ttu-id="2d99d-146">**“撤消”** 只在修改后仍保持打开状态以进行编辑的文件中可用。</span><span class="sxs-lookup"><span data-stu-id="2d99d-146">**Undo** is only available in files that remain open for editing after they are modified.</span></span>  
  
 <span data-ttu-id="2d99d-147">**跳过文件**</span><span class="sxs-lookup"><span data-stu-id="2d99d-147">**Skip File**</span></span>  
 <span data-ttu-id="2d99d-148">如果为“查找范围”  指定的值包含多个文件，则此选项可用。</span><span class="sxs-lookup"><span data-stu-id="2d99d-148">Becomes available when the value specified for **Look in** includes multiple files.</span></span> <span data-ttu-id="2d99d-149">如果不希望搜索或修改当前文件，请单击此按钮。</span><span class="sxs-lookup"><span data-stu-id="2d99d-149">Click this button if you do not want to search or modify the current file.</span></span> <span data-ttu-id="2d99d-150">此时，将继续在 **“查找范围”** 列表中的下一个文件内进行搜索。</span><span class="sxs-lookup"><span data-stu-id="2d99d-150">The search will continue in the next file on the list in **Look in**.</span></span>  
  
## <a name="look-in"></a><span data-ttu-id="2d99d-151">查找范围</span><span class="sxs-lookup"><span data-stu-id="2d99d-151">Look In</span></span>  
 <span data-ttu-id="2d99d-152">**Look in**</span><span class="sxs-lookup"><span data-stu-id="2d99d-152">**Look in**</span></span>  
 <span data-ttu-id="2d99d-153">选择“查找内容”  框中指定文本的查找位置。</span><span class="sxs-lookup"><span data-stu-id="2d99d-153">Select the location to look for the text specified in **Find what**.</span></span> <span data-ttu-id="2d99d-154">相应的选项有 **“当前文档”** ，用于搜索在打开该对话框时焦点所在的文档窗口，还有 **“所有打开的文档”** ，用于搜索 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]当前打开的所有文档窗口。</span><span class="sxs-lookup"><span data-stu-id="2d99d-154">Options are **Current Document**, which searches the document window that had focus when the dialog box was opened, and **All Open Documents**, which searches all document windows that are currently open in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="find-options"></a><span data-ttu-id="2d99d-155">查找选项</span><span class="sxs-lookup"><span data-stu-id="2d99d-155">Find Options</span></span>  
 <span data-ttu-id="2d99d-156">您可以展开或折叠 **“查找选项”** 部分。</span><span class="sxs-lookup"><span data-stu-id="2d99d-156">You can expand or collapse the **Find Options** section.</span></span> <span data-ttu-id="2d99d-157">您可以选中或清除下列选项：</span><span class="sxs-lookup"><span data-stu-id="2d99d-157">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="2d99d-158">**匹配大小写**</span><span class="sxs-lookup"><span data-stu-id="2d99d-158">**Match case**</span></span>  
 <span data-ttu-id="2d99d-159">选中此复选框后，“查找结果”窗口将仅显示与“查找内容”  中指定的字符串的内容和大小写均匹配的字符串实例。</span><span class="sxs-lookup"><span data-stu-id="2d99d-159">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched both by content and by case.</span></span> <span data-ttu-id="2d99d-160">例如，在选中 **“匹配大小写”** 复选框的情况下搜索 **MyObject** 将返回“MyObject”，但不能返回“myobject”或“MYOBJECT”。</span><span class="sxs-lookup"><span data-stu-id="2d99d-160">For example, a search for "**MyObject**" with the **Match case** check box selected will return "MyObject" but not "myobject" or "MYOBJECT."</span></span>  
  
 <span data-ttu-id="2d99d-161">**全字匹配**</span><span class="sxs-lookup"><span data-stu-id="2d99d-161">**Match whole word**</span></span>  
 <span data-ttu-id="2d99d-162">选中此复选框后，“查找结果”窗口将仅显示与“查找内容”  框中指定的字符串全字匹配的字符串实例。</span><span class="sxs-lookup"><span data-stu-id="2d99d-162">When selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched in complete words.</span></span> <span data-ttu-id="2d99d-163">例如，搜索 **MyObject** 将返回“MyObject”，而不会返回“CMyObject”或“MyObjectC”。</span><span class="sxs-lookup"><span data-stu-id="2d99d-163">For example, a search for **MyObject** will return "MyObject" but not "CMyObject" or "MyObjectC."</span></span>  
  
 <span data-ttu-id="2d99d-164">**向上搜索**</span><span class="sxs-lookup"><span data-stu-id="2d99d-164">**Search up**</span></span>  
 <span data-ttu-id="2d99d-165">从光标所在的位置向文档开头搜索。</span><span class="sxs-lookup"><span data-stu-id="2d99d-165">Search from the cursor location towards the beginning of the document.</span></span>  
  
 <span data-ttu-id="2d99d-166">**搜索隐藏文本**</span><span class="sxs-lookup"><span data-stu-id="2d99d-166">**Search hidden text**</span></span>  
 <span data-ttu-id="2d99d-167">查找隐藏和折叠的文本实例。</span><span class="sxs-lookup"><span data-stu-id="2d99d-167">Locate instances of the text that are concealed and collapsed text.</span></span>  
  
 <span data-ttu-id="2d99d-168">**使用**</span><span class="sxs-lookup"><span data-stu-id="2d99d-168">**Use**</span></span>  
 <span data-ttu-id="2d99d-169">指示如何解释“查找内容”  或“替换为”  文本框中输入的特殊字符。</span><span class="sxs-lookup"><span data-stu-id="2d99d-169">Indicates how to interpret special characters entered in the **Find what** or **Replace with** text boxes.</span></span> <span data-ttu-id="2d99d-170">选项包括 **“通配符”** 和 **“正则表达式”** 。</span><span class="sxs-lookup"><span data-stu-id="2d99d-170">The options include **Wildcards** and **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="2d99d-171">**“正则表达式”**</span><span class="sxs-lookup"><span data-stu-id="2d99d-171">**Regular Expressions**</span></span>  
 <span data-ttu-id="2d99d-172">定义文本匹配模式的特殊表示法。</span><span class="sxs-lookup"><span data-stu-id="2d99d-172">Special notations define patterns of text to match.</span></span> <span data-ttu-id="2d99d-173">有关列表，请参阅 [使用正则表达式搜索文本](search-text-with-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="2d99d-173">For a list, see [Search Text with Regular Expressions](search-text-with-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="2d99d-174">**通配符**</span><span class="sxs-lookup"><span data-stu-id="2d99d-174">**Wildcards**</span></span>  
 <span data-ttu-id="2d99d-175">用于表示一个或多个字符特殊字符，如星号 (`*`) 和问号 (`?`)。</span><span class="sxs-lookup"><span data-stu-id="2d99d-175">Special characters such as asterisks (`*`) and question marks (`?`) represent one or more characters.</span></span> <span data-ttu-id="2d99d-176">有关列表，请参阅 [使用通配符搜索文本](search-text-with-wildcards.md)。</span><span class="sxs-lookup"><span data-stu-id="2d99d-176">For a list, see [Search Text with Wildcards](search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="2d99d-177">**查找下一个**</span><span class="sxs-lookup"><span data-stu-id="2d99d-177">**Find Next**</span></span>  
 <span data-ttu-id="2d99d-178">开始搜索“查找内容”  框中的文本。</span><span class="sxs-lookup"><span data-stu-id="2d99d-178">Begins searching for the text in the **Find what** box.</span></span>  
  
 <span data-ttu-id="2d99d-179">**替换**</span><span class="sxs-lookup"><span data-stu-id="2d99d-179">**Replace**</span></span>  
 <span data-ttu-id="2d99d-180">单击此按钮可使用“替换为” 框中指定的字符串替换“查找内容”框中指定字符串的当前实例，并在“查找范围”框中指定的范围内查找下一个实例。</span><span class="sxs-lookup"><span data-stu-id="2d99d-180">Click this button to replace the current instance of the string specified in **Find what** with the string specified in **Replace with**, and find the next instance within the scope specified in **Look in**.</span></span>  
  
 <span data-ttu-id="2d99d-181">**Replace All**</span><span class="sxs-lookup"><span data-stu-id="2d99d-181">**Replace All**</span></span>  
 <span data-ttu-id="2d99d-182">单击此按钮可在“查找范围” 框指定范围内的所有文件中，使用“替换为”框中指定的字符串替换“查找内容”框中指定字符串的所有实例。</span><span class="sxs-lookup"><span data-stu-id="2d99d-182">Choose this button to replace all instances of the string specified in **Find what** with the string specified in **Replace with**, in all files within the scope specified in **Look in**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2d99d-183">请确保将“查找范围”  设置为仅包含要修改的文件。</span><span class="sxs-lookup"><span data-stu-id="2d99d-183">Make sure that **Look in** is set to include only those files that you want to modify.</span></span>  
  
## <a name="find-and-replace-views"></a><span data-ttu-id="2d99d-184">“查找和替换”视图</span><span class="sxs-lookup"><span data-stu-id="2d99d-184">Find and Replace Views</span></span>  
 <span data-ttu-id="2d99d-185">“查找和替换”窗口顶部的选项卡包含 **“视图”** 菜单。</span><span class="sxs-lookup"><span data-stu-id="2d99d-185">The tabs at the top of the Find and Replace window include **View** menus.</span></span> <span data-ttu-id="2d99d-186">使用这些菜单，可以选择在活动窗格中显示的不同字段。</span><span class="sxs-lookup"><span data-stu-id="2d99d-186">These menus enable you to choose a set of fields to display in the active pane.</span></span> <span data-ttu-id="2d99d-187">您可以将“查找和替换”  窗口停靠在方便的位置，然后在各个选项卡之间以及各个视图之间进行切换，以执行任意类型的查找或替换操作。</span><span class="sxs-lookup"><span data-stu-id="2d99d-187">You can leave the **Find and Replace** window docked in a convenient location, and then change from tab to tab and view to view to perform any type of find or replace operation.</span></span>  
  
 <span data-ttu-id="2d99d-188">**“快速查找”**</span><span class="sxs-lookup"><span data-stu-id="2d99d-188">**Quick Find**</span></span>  
 <span data-ttu-id="2d99d-189">使用此工具栏选项卡，将把对话框更改为“快速查找”  对话框。</span><span class="sxs-lookup"><span data-stu-id="2d99d-189">This toolbar tab changes the dialog box to a **Quick Find** dialog box.</span></span>  
  
 <span data-ttu-id="2d99d-190">**在文件中查找**</span><span class="sxs-lookup"><span data-stu-id="2d99d-190">**Find in Files**</span></span>  
 <span data-ttu-id="2d99d-191">使用此工具栏选项卡，将把对话框更改为“在文件中查找”  对话框。</span><span class="sxs-lookup"><span data-stu-id="2d99d-191">This toolbar tab changes the dialog box to a **Find in Files** dialog box.</span></span>  
  
 <span data-ttu-id="2d99d-192">**“快速替换”**</span><span class="sxs-lookup"><span data-stu-id="2d99d-192">**Quick Replace**</span></span>  
 <span data-ttu-id="2d99d-193">使用此工具栏选项卡，将把对话框更改为“快速替换”  对话框</span><span class="sxs-lookup"><span data-stu-id="2d99d-193">This toolbar tab changes the dialog box to a **Quick Replace** dialog box</span></span>  
  
 <span data-ttu-id="2d99d-194">**在文件中替换**</span><span class="sxs-lookup"><span data-stu-id="2d99d-194">**Replace in Files**</span></span>  
 <span data-ttu-id="2d99d-195">使用此工具栏选项卡，将把对话框更改为“在文件中替换”  对话框</span><span class="sxs-lookup"><span data-stu-id="2d99d-195">This toolbar tab changes the dialog box to a **Replace in Files** dialog box</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d99d-196">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d99d-196">See Also</span></span>  
 [<span data-ttu-id="2d99d-197">SQL Server Management Studio 键盘快捷键</span><span class="sxs-lookup"><span data-stu-id="2d99d-197">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
