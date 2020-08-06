---
title: 使用结果列表搜索文档
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- searches [SQL Server Management Studio], result lists
- result list searches [SQL Server Management Studio]
- searches [SQL Server Management Studio], multiple files
- Query Editor [SQL Server Management Studio], search multiple files
ms.assetid: 275e1b6c-fbd0-4408-af77-35903f90657c
author: rothja
ms.author: jroth
ms.openlocfilehash: 58ff3754bc1667de75426e52b3ddd855e7d1a348
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590703"
---
# <a name="search-documents-using-results-lists"></a><span data-ttu-id="4b8e2-102">使用结果列表搜索文档</span><span class="sxs-lookup"><span data-stu-id="4b8e2-102">Search Documents Using Results Lists</span></span>
  <span data-ttu-id="4b8e2-103">使用 **“查找和替换”** 对话框，可以搜索和替换项目或解决方案中或文件系统文件夹中的所有文件中的文本（即使这些文件未在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中打开）。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-103">Using the **Find and Replace** dialog box, you can search and replace text in all files in a project or solution or in a file system folder, even when they are not open in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="4b8e2-104">使用 **“查找和替换”** 对话框执行的搜索返回的匹配项将显示在“查找结果 1”和“查找结果 2”窗口中。这样，您可以查看包含匹配项的行中的完全匹配文本。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-104">Matches from searches that were performed with the **Find and Replace** dialog box appear in the Find Results 1 and Find Results 2 windows, which allows you to view the exact text from the line containing the match.</span></span>  
  
### <a name="to-search-in-multiple-files"></a><span data-ttu-id="4b8e2-105">在多个文件中搜索</span><span class="sxs-lookup"><span data-stu-id="4b8e2-105">To search in multiple files</span></span>  
  
1.  <span data-ttu-id="4b8e2-106">在 **“编辑”** 菜单上，指向 **“查找和替换”** ，再单击 **“在文件中查找”** 。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-106">On the **Edit** menu, point to **Find and Replace,** and then click **Find in Files**.</span></span>  
  
2.  <span data-ttu-id="4b8e2-107">在 **“查找内容”** 文本框中，输入要搜索的文本。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-107">In the **Find what** text box, enter the text to search for.</span></span>  
  
3.  <span data-ttu-id="4b8e2-108">在 **“查找范围”** 列表中，单击 **“所有打开的文档”** 、 **“当前项目”** 、 **“整个解决方案”** ，或者键入目录路径。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-108">In the **Look in** list, click **All Open Documents**, **Current Project**, **Entire Solution**, or type a directory path.</span></span>  
  
4.  <span data-ttu-id="4b8e2-109">在 **“文件类型”** 列表中，选择一个列出的文件扩展名组，或输入要搜索的文件类型的扩展名（由分号分隔）。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-109">In the **File types** list, select one of the listed sets of file extensions or enter the extensions for the types of files to be searched, separated by semicolons.</span></span> <span data-ttu-id="4b8e2-110">使用 \*.\* 可以搜索在“查找范围”  下拉列表中列出的目录中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-110">Use \*.\* to search all files in the directory listed in the **Look in** drop-down list.</span></span>  
  
5.  <span data-ttu-id="4b8e2-111">选择其余搜索选项以提高搜索的准确性。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-111">Select from the remaining search options to improve the accuracy of the search.</span></span>  
  
6.  <span data-ttu-id="4b8e2-112">单击 **“查找”** 以开始执行搜索。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-112">Click **Find** to begin the search.</span></span>  
  
 <span data-ttu-id="4b8e2-113">在默认情况下，搜索匹配项将显示在“查找结果 1”窗口中。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-113">The matches for the search appear in the Find Results 1 window by default.</span></span> <span data-ttu-id="4b8e2-114">可以通过双击“查找结果 1”窗口中的每个条目浏览搜索匹配项。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-114">You can browse the search matches by double-clicking each entry in the Find Results 1 window.</span></span> <span data-ttu-id="4b8e2-115">若要在新窗口中查看搜索结果，请选择 **“在查找 2 中显示”** 。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-115">To view the search results in a new window, select **Display in Find 2**.</span></span>  
  
#### <a name="to-replace-across-multiple-files-or-folders"></a><span data-ttu-id="4b8e2-116">在多个文件或文件夹中替换</span><span class="sxs-lookup"><span data-stu-id="4b8e2-116">To replace across multiple files or folders</span></span>  
  
1.  <span data-ttu-id="4b8e2-117">在 **“编辑”** 菜单上，指向 **“查找和替换”** ，再单击 **“在文件中替换”** 。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-117">On the **Edit** menu, point to **Find and Replace,** and then click **Replace in Files**.</span></span>  
  
2.  <span data-ttu-id="4b8e2-118">在 **“查找内容”** 文本框中，输入要搜索的文本。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-118">In the **Find what** text box, enter the text to search for.</span></span>  
  
3.  <span data-ttu-id="4b8e2-119">在 **“替换为”** 框中，输入用来替换搜索文本的文本。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-119">In the **Replace with** box, enter the text to replace the search text.</span></span>  
  
4.  <span data-ttu-id="4b8e2-120">在 **“查找范围”** 列表中，单击 **“所有打开的文档”** 、 **“当前项目”** 、 **“整个解决方案”** ，或者键入目录路径。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-120">In the **Look in** list, click **All Open Documents**, **Current Project**, **Entire Solution**, or type a directory path.</span></span>  
  
5.  <span data-ttu-id="4b8e2-121">单击 **“替换”** 以使用 **“替换为”** 框中的文本替换当前的搜索匹配项。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-121">Click **Replace** to replace the current search match with the text in the **Replace with** box.</span></span> <span data-ttu-id="4b8e2-122">可以通过单击 **“查找下一个”** 跳过单个匹配项，或通过单击 **“跳过文件”** 跳过整个文件。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-122">You can skip a single match by clicking **Find Next** or skip an entire file clicking **Skip File**.</span></span>  
  
     <span data-ttu-id="4b8e2-123">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="4b8e2-123">\- or -</span></span>  
  
     <span data-ttu-id="4b8e2-124">选择 **“全部替换”** 以使用 **“替换为”** 框中的文本替换所有匹配项。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-124">Choose **Replace all** to replace all search matches with the text in the **Replace with** box.</span></span> <span data-ttu-id="4b8e2-125">若要在其他时间撤消某些替换，请选择 **“在全部替换后使已修改文件保持打开状态”** 。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-125">Select **Keep modified files open after Replace All** if you want to undo some of the replacements at another time.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b8e2-126">如果选择 **“全部替换”** ，则系统将替换所有搜索匹配项，包括已使用 **“跳过文件”** 或 **“查找下一个”** 跳过的那些搜索匹配项。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-126">**Replace all** replaces all search matches, including those in files you have skipped with **Skip File** or **Find Next**.</span></span> <span data-ttu-id="4b8e2-127">只能针对在替换操作完成后仍保持打开状态的文件中进行的替换使用 **“撤消”** 操作。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-127">You can only use **Undo** for replacements made in files that remain open after the replacement operation.</span></span>  
  
 <span data-ttu-id="4b8e2-128">默认情况下，替换信息将显示在“查找结果 1”窗口中。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-128">Replacement information appears in the Find Results 1 window by default.</span></span> <span data-ttu-id="4b8e2-129">可以通过双击“查找结果 1”窗口中的各个条目来浏览替换项。</span><span class="sxs-lookup"><span data-stu-id="4b8e2-129">You can browse replacements by double-clicking each entry in the Find Results 1 window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b8e2-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b8e2-130">See Also</span></span>  
 <span data-ttu-id="4b8e2-131">[搜索和替换](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="4b8e2-131">[Search and Replace](search-and-replace.md) </span></span>  
 <span data-ttu-id="4b8e2-132">[交互式搜索文档](search-documents-interactively.md) </span><span class="sxs-lookup"><span data-stu-id="4b8e2-132">[Search Documents Interactively](search-documents-interactively.md) </span></span>  
 <span data-ttu-id="4b8e2-133">[使用通配符搜索文本](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="4b8e2-133">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="4b8e2-134">使用正则表达式搜索文本</span><span class="sxs-lookup"><span data-stu-id="4b8e2-134">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
