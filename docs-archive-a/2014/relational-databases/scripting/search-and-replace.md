---
title: 搜索和替换
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- match case [SQL Server]
- undo operations
- searches [SQL Server Management Studio]
- replacing text
- quick search and replaces [SQL Server Management Studio]
- Query Editor [SQL Server Management Studio], undo
- Query Editor [SQL Server Management Studio], searching
- regular expressions [SQL Server Management Studio]
- finding text [SQL Server Management Studio]
- text [SQL Server], search and replace operations
- finding [SQL Server Management Studio]
- locating text
- Query Editor [SQL Server Management Studio], replacing text
- Find and Replace dialog box
- wildcard options [SQL Server Management Studio]
- match whole word [SQL Server]
- searches [SQL Server Management Studio], replacing
ms.assetid: 3641c7b3-3e3e-4ddd-af82-c15b50004f94
author: rothja
ms.author: jroth
ms.openlocfilehash: 55422fa7201213477426c7bc25c45ff05acf8945
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578785"
---
# <a name="search-and-replace"></a><span data-ttu-id="f5de0-102">搜索和替换</span><span class="sxs-lookup"><span data-stu-id="f5de0-102">Search and Replace</span></span>
  <span data-ttu-id="f5de0-103">您可以采用几种不同的方法来查找和替换文本。</span><span class="sxs-lookup"><span data-stu-id="f5de0-103">There are several different ways to find and replace text.</span></span> <span data-ttu-id="f5de0-104">在 **“编辑”** 菜单上， **“查找和替换”** 提供了四个选项： **“快速查找”** 、 **“快速替换”** 、 **“在文件中查找”** 或 **“在文件中替换”** 。</span><span class="sxs-lookup"><span data-stu-id="f5de0-104">On the **Edit** menu, **Find and Replace** offers four choices: **Quick Find**, **Quick Replace**, **Find in Files**, or **Replace in Files**.</span></span> <span data-ttu-id="f5de0-105">每个选项均可以打开不同版本的 **“查找和替换”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="f5de0-105">Each of these opens versions of the **Find and Replace** dialog box.</span></span> <span data-ttu-id="f5de0-106">您还可以通过使用渐进式搜索键盘快捷键在没有对话框的情况下进行搜索。</span><span class="sxs-lookup"><span data-stu-id="f5de0-106">You can also search without a dialog box by using incremental search keyboard shortcut keys.</span></span> <span data-ttu-id="f5de0-107">通过这些技术，您可以控制查找和替换的范围，并选择查看搜索匹配项和替换项的方法。</span><span class="sxs-lookup"><span data-stu-id="f5de0-107">These techniques allow you to control the scope of find and replace, and choose the method of reviewing search matches and replacements.</span></span>  
  
 <span data-ttu-id="f5de0-108">搜索和替换文本时应注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="f5de0-108">You should consider the following when you search and replace text:</span></span>  
  
-   <span data-ttu-id="f5de0-109">在 **“查找和替换”** 对话框中设置的选项将影响对文本的搜索。</span><span class="sxs-lookup"><span data-stu-id="f5de0-109">Options set in the **Find and Replace** dialog box affect all the searches.</span></span> <span data-ttu-id="f5de0-110">这些选项包括 **“大小写匹配”** 、 **“全字匹配”** 、 **“向上搜索”** 、 **“搜索隐藏文本”** 、 **“通配符”** 、 **“正则表达式”** 、 **“在所有打开的文档中查找”** 以及 **“在当前项目中查找”** 。</span><span class="sxs-lookup"><span data-stu-id="f5de0-110">These options include **Match case**, **Match whole word**, **Search up**, **Search hidden text**, **Wildcards**, **Regular Expressions**, **Look in All Open Documents**, and **Look in Current Project**.</span></span> <span data-ttu-id="f5de0-111">并非所有版本中的 **“查找和替换”** 对话框均提供了所有选项。</span><span class="sxs-lookup"><span data-stu-id="f5de0-111">All options are not available in all versions of the **Find and Replace** dialog box.</span></span>  
  
-   <span data-ttu-id="f5de0-112">**“撤消”** 只适用于在替换操作完成后仍保持打开状态的文档。</span><span class="sxs-lookup"><span data-stu-id="f5de0-112">**Undo** is available only for documents left open after a replace operation.</span></span>  
  
-   <span data-ttu-id="f5de0-113">对跨多个文件的 **“全部替换”** 操作执行 **“撤消”** 被视为对所有受影响文件执行的单个大容量操作，</span><span class="sxs-lookup"><span data-stu-id="f5de0-113">**Undo** for a **Replace All** operation that spans more than one file is considered a single, bulk action across all the affected files.</span></span> <span data-ttu-id="f5de0-114">在这种情况下，您不能在某些文件中撤消更改，而在其他文件中保留该更改。</span><span class="sxs-lookup"><span data-stu-id="f5de0-114">That is, you cannot undo the change in some files while retaining the change in other files.</span></span>  
  
 <span data-ttu-id="f5de0-115">通常，您无法搜索包含图形视图的项。</span><span class="sxs-lookup"><span data-stu-id="f5de0-115">Generally, you cannot search items with graphical views.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5de0-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5de0-116">See Also</span></span>  
 <span data-ttu-id="f5de0-117">[增量搜索活动文档](search-an-active-document-incrementally.md) </span><span class="sxs-lookup"><span data-stu-id="f5de0-117">[Search an Active Document Incrementally](search-an-active-document-incrementally.md) </span></span>  
 <span data-ttu-id="f5de0-118">[交互式搜索文档](search-documents-interactively.md) </span><span class="sxs-lookup"><span data-stu-id="f5de0-118">[Search Documents Interactively](search-documents-interactively.md) </span></span>  
 <span data-ttu-id="f5de0-119">[使用结果列表搜索文档](search-documents-using-results-lists.md) </span><span class="sxs-lookup"><span data-stu-id="f5de0-119">[Search Documents Using Results Lists](search-documents-using-results-lists.md) </span></span>  
 <span data-ttu-id="f5de0-120">[使用通配符搜索文本](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="f5de0-120">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="f5de0-121">使用正则表达式搜索文本</span><span class="sxs-lookup"><span data-stu-id="f5de0-121">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
