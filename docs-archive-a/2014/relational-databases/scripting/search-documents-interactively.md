---
title: 交互式搜索文档
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- interactive searches [SQL Server Management Studio]
- searches [SQL Server Management Studio], interactive
- Query Editor [SQL Server Management Studio], interactive search
ms.assetid: dae65ac5-67af-45c6-a6e0-952fea26d680
author: rothja
ms.author: jroth
ms.openlocfilehash: 5603db77ea4f58d4bb036635a23ec3cfa400a818
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590708"
---
# <a name="search-documents-interactively"></a><span data-ttu-id="16f4b-102">交互式搜索文档</span><span class="sxs-lookup"><span data-stu-id="16f4b-102">Search Documents Interactively</span></span>
  <span data-ttu-id="16f4b-103">使用 **“查找和替换”** 对话框，可以搜索一个或多个打开的文件或窗口，并逐个移动到每个搜索匹配项。</span><span class="sxs-lookup"><span data-stu-id="16f4b-103">Using the **Find and Replace** dialog box, you can search one or more open files or windows and move through the search matches one by one.</span></span> <span data-ttu-id="16f4b-104">该技术允许您在匹配项周围的文本上下文中检查每个单独的搜索匹配项。</span><span class="sxs-lookup"><span data-stu-id="16f4b-104">This technique allows you to review each individual search match in the context of the text around the match.</span></span> <span data-ttu-id="16f4b-105">**“查找和替换”** 对话框还提供了执行大容量查找操作和在报表格式中检查搜索匹配项的选项。</span><span class="sxs-lookup"><span data-stu-id="16f4b-105">You also have the option of performing bulk find operations and reviewing search matches in report format using the **Find and Replace** dialog box.</span></span>  
  
### <a name="to-search-all-open-documents"></a><span data-ttu-id="16f4b-106">搜索所有打开的文档</span><span class="sxs-lookup"><span data-stu-id="16f4b-106">To search all open documents</span></span>  
  
1.  <span data-ttu-id="16f4b-107">打开想要搜索的项。</span><span class="sxs-lookup"><span data-stu-id="16f4b-107">Open the items you wish to search.</span></span>  
  
2.  <span data-ttu-id="16f4b-108">在“编辑”  菜单上，指向“查找和替换”  ，再单击“快速查找”  。</span><span class="sxs-lookup"><span data-stu-id="16f4b-108">On the **Edit** menu, point to **Find and Replace,** and then click **QuickFind**.</span></span>  
  
3.  <span data-ttu-id="16f4b-109">在 **“查找和替换”** 文本框中，输入要搜索的文本。</span><span class="sxs-lookup"><span data-stu-id="16f4b-109">In the **Find and Replace** text box, enter the text to search for.</span></span>  
  
4.  <span data-ttu-id="16f4b-110">在 **“查找范围”** 列表中，选择 **“所有打开的文档”** 。</span><span class="sxs-lookup"><span data-stu-id="16f4b-110">In the **Look in** list, select **All Open Documents**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="16f4b-111">如果选择 **“所有打开的文档”** ，则可能不搜索某些打开的文件。</span><span class="sxs-lookup"><span data-stu-id="16f4b-111">Certain open files might not be searched when **All Open Documents** is selected.</span></span> <span data-ttu-id="16f4b-112">只有当前在文本视图（如代码视图）中打开的文件才会包括在搜索中。</span><span class="sxs-lookup"><span data-stu-id="16f4b-112">Only files currently open in a textual view, such as Code view, are included in searches.</span></span> <span data-ttu-id="16f4b-113">设计器视图中的文件不包括在搜索中。</span><span class="sxs-lookup"><span data-stu-id="16f4b-113">Files in Designer view are not included in searches.</span></span>  
  
5.  <span data-ttu-id="16f4b-114">选择其他搜索选项可以提高搜索准确性。</span><span class="sxs-lookup"><span data-stu-id="16f4b-114">Select additional search options to increase the accuracy of the search.</span></span>  
  
6.  <span data-ttu-id="16f4b-115">单击 **“查找下一个”** 可以启动搜索，连续单击 **“查找下一个”** 直到搜索了最后一个文件。</span><span class="sxs-lookup"><span data-stu-id="16f4b-115">Click **Find Next** to start the search, and continue clicking **Find Next** until the last file has been searched.</span></span>  
  
 <span data-ttu-id="16f4b-116">在搜索通过文档的开始或末尾时，将在状态栏中显示消息。</span><span class="sxs-lookup"><span data-stu-id="16f4b-116">When the search passes the beginning or end of the document, a message is displayed in the status bar.</span></span> <span data-ttu-id="16f4b-117">如果搜索到达搜索的起点，则出现消息框。</span><span class="sxs-lookup"><span data-stu-id="16f4b-117">A message box appears when the search reaches the starting point of the search.</span></span>  
  
#### <a name="to-replace-in-all-active-files-interactively"></a><span data-ttu-id="16f4b-118">在所有活动文件中交互式替换</span><span class="sxs-lookup"><span data-stu-id="16f4b-118">To replace in all active files interactively</span></span>  
  
1.  <span data-ttu-id="16f4b-119">在“编辑”  菜单上，指向“查找和替换”  ，再单击“快速替换”  。</span><span class="sxs-lookup"><span data-stu-id="16f4b-119">On the **Edit** menu, point to **Find and Replace**, and then click **QuickReplace**.</span></span>  
  
2.  <span data-ttu-id="16f4b-120">在 **“查找内容”** 框中，输入要搜索的文本。</span><span class="sxs-lookup"><span data-stu-id="16f4b-120">In the **Find what** box, enter the text to search for.</span></span>  
  
3.  <span data-ttu-id="16f4b-121">在 **“替换为”** 框中，输入用来替换搜索文本的文本。</span><span class="sxs-lookup"><span data-stu-id="16f4b-121">In the **Replace with** box, enter the text to replace the search text.</span></span>  
  
4.  <span data-ttu-id="16f4b-122">在 **“查找范围”** 列表中，选择 **“所有打开的文档”** 。</span><span class="sxs-lookup"><span data-stu-id="16f4b-122">In the **Look in** list, select **All Open Documents**.</span></span>  
  
5.  <span data-ttu-id="16f4b-123">单击 **“替换”** ，并连续单击 **“替换”** ，直到替换了最后一个文件中的最后一个匹配项。</span><span class="sxs-lookup"><span data-stu-id="16f4b-123">Click **Replace**, and continue clicking **Replace** until the last match in the last file has been replaced.</span></span> <span data-ttu-id="16f4b-124">单击 **“查找下一个”** 可以跳过不想替换的匹配项。</span><span class="sxs-lookup"><span data-stu-id="16f4b-124">Click **Find Next** to skip a match you do not want to replace.</span></span>  
  
     <span data-ttu-id="16f4b-125">-或-</span><span class="sxs-lookup"><span data-stu-id="16f4b-125">-or-</span></span>  
  
     <span data-ttu-id="16f4b-126">选择 **“全部替换”** 以替换所有匹配项。</span><span class="sxs-lookup"><span data-stu-id="16f4b-126">Choose **Replace All** to replace all matches.</span></span> <span data-ttu-id="16f4b-127">然后将出现消息框，列出替换的总数。</span><span class="sxs-lookup"><span data-stu-id="16f4b-127">A message box appears, listing the total number of replacements.</span></span>  
  
 <span data-ttu-id="16f4b-128">**“全部替换”** 命令将替换所有搜索匹配项，包括那些已经用 **“查找下一个”** 按钮跳过的匹配项。</span><span class="sxs-lookup"><span data-stu-id="16f4b-128">The **Replace All** command replaces all search matches, including those you have skipped with the **Find Next** button.</span></span> <span data-ttu-id="16f4b-129">若要取消 **“全部替换”** ，请在关闭任何文件之前从 **“编辑”** 菜单中单击 **“撤消”** 。</span><span class="sxs-lookup"><span data-stu-id="16f4b-129">To cancel **Replace All**, click **Undo** from the **Edit** menu before closing any of the files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16f4b-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="16f4b-130">See Also</span></span>  
 <span data-ttu-id="16f4b-131">[增量搜索活动文档](search-an-active-document-incrementally.md) </span><span class="sxs-lookup"><span data-stu-id="16f4b-131">[Search an Active Document Incrementally](search-an-active-document-incrementally.md) </span></span>  
 <span data-ttu-id="16f4b-132">[搜索和替换](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="16f4b-132">[Search and Replace](search-and-replace.md) </span></span>  
 <span data-ttu-id="16f4b-133">[使用结果列表搜索文档](search-documents-using-results-lists.md) </span><span class="sxs-lookup"><span data-stu-id="16f4b-133">[Search Documents Using Results Lists](search-documents-using-results-lists.md) </span></span>  
 <span data-ttu-id="16f4b-134">[使用通配符搜索文本](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="16f4b-134">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="16f4b-135">使用正则表达式搜索文本</span><span class="sxs-lookup"><span data-stu-id="16f4b-135">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
