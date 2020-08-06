---
title: 增量搜索活动文档
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- searches [SQL Server Management Studio], incremental
- Query Editor [SQL Server Management Studio], incremental search
- incremental searches [SQL Server Management Studio]
ms.assetid: 490bb36c-dd43-4219-9e2a-ff27046b9395
author: rothja
ms.author: jroth
ms.openlocfilehash: aefc2f0b7abff5992a8f4f7817e564ef1b72009d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578788"
---
# <a name="search-an-active-document-incrementally"></a><span data-ttu-id="cedaf-102">增量搜索活动文档</span><span class="sxs-lookup"><span data-stu-id="cedaf-102">Search an Active Document Incrementally</span></span>
  <span data-ttu-id="cedaf-103">您可以通过输入文字来对单个文档或窗口执行渐进式搜索。</span><span class="sxs-lookup"><span data-stu-id="cedaf-103">You can search a single document or window incrementally by entering text.</span></span> <span data-ttu-id="cedaf-104">搜索操作会突出显示与在文档或窗口的渐进式搜索过程中输入的字符相匹配的第一个字符集。</span><span class="sxs-lookup"><span data-stu-id="cedaf-104">The search operation highlights the first set of characters that matches the characters entered during the incremental search in the document or window.</span></span> <span data-ttu-id="cedaf-105">渐进式搜索会自动搜索文档或窗口内的所有文字，但隐藏文字除外。</span><span class="sxs-lookup"><span data-stu-id="cedaf-105">Incremental search automatically searches all of the text within a document or window except for text that has been hidden.</span></span>  
  
 <span data-ttu-id="cedaf-106">对于 **“大小写匹配”** 选项，渐进式搜索将使用上一次搜索的条件。</span><span class="sxs-lookup"><span data-stu-id="cedaf-106">For the **Match case** option, incremental search uses the criteria from your previous search.</span></span> <span data-ttu-id="cedaf-107">例如，如果使用“在文件中查找”  对话框跨多个文件执行搜索，并选择“大小写匹配”  ，然后执行渐进式搜索，则此搜索将区分大小写。</span><span class="sxs-lookup"><span data-stu-id="cedaf-107">For example, if you searched across multiple files using the **Find in Files** dialog box and select **Match Case**, and you next search incrementally, the search will be case-sensitive.</span></span>  
  
### <a name="to-search-incrementally"></a><span data-ttu-id="cedaf-108">执行渐进式搜索</span><span class="sxs-lookup"><span data-stu-id="cedaf-108">To search incrementally</span></span>  
  
1.  <span data-ttu-id="cedaf-109">打开您要搜索的文件或窗口。</span><span class="sxs-lookup"><span data-stu-id="cedaf-109">Open the file or window to you want to search.</span></span>  
  
2.  <span data-ttu-id="cedaf-110">在 **“编辑”** 菜单中，指向 **“高级”** ，然后单击 **“渐进式搜索”** 。</span><span class="sxs-lookup"><span data-stu-id="cedaf-110">On the **Edit** menu, point to **Advanced**, and then click **Incremental Search**.</span></span>  
  
     <span data-ttu-id="cedaf-111">光标图标会变为带箭头的望远镜，指示搜索方向，并且状态栏显示“渐进式搜索”。</span><span class="sxs-lookup"><span data-stu-id="cedaf-111">The cursor icon changes to a binocular with an arrow, indicating the search direction, and the status bar displays "Incremental Search."</span></span>  
  
3.  <span data-ttu-id="cedaf-112">开始键入文本字符串。</span><span class="sxs-lookup"><span data-stu-id="cedaf-112">Begin typing the text string.</span></span>  
  
     <span data-ttu-id="cedaf-113">当编辑器突出显示此文本的第一个匹配项时，状态栏会显示您正在输入的文本。</span><span class="sxs-lookup"><span data-stu-id="cedaf-113">The status bar displays the text you are entering while the editor highlights the first occurrence that matches the text.</span></span> <span data-ttu-id="cedaf-114">编辑器会随着您的继续键入而移动到下一个匹配项并使其突出显示。</span><span class="sxs-lookup"><span data-stu-id="cedaf-114">As you continue typing, the editor moves to the next match and highlights it.</span></span> <span data-ttu-id="cedaf-115">如果没有匹配项，状态栏会显示以下信息。</span><span class="sxs-lookup"><span data-stu-id="cedaf-115">If no matches are available, the status bar displays the following.</span></span>  
  
    ```  
    Incremental Search: <text> (not found)  
    ```  
  
 <span data-ttu-id="cedaf-116">渐进式搜索从文档中的当前位置向下自左至右执行。</span><span class="sxs-lookup"><span data-stu-id="cedaf-116">Incremental searches are performed from the current location in the document downwards from left to right.</span></span> <span data-ttu-id="cedaf-117">可以使用键盘快捷键完成渐进式搜索。</span><span class="sxs-lookup"><span data-stu-id="cedaf-117">Incremental searches can be done using keyboard shortcut keys.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cedaf-118">有关键盘快捷键的完整列表，请参阅 [SQL Server Management Studio 键盘快捷键](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="cedaf-118">For a complete list of keyboard shortcut keys, see [SQL Server Management Studio Keyboard Shortcuts](../../ssms/sql-server-management-studio-keyboard-shortcuts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cedaf-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cedaf-119">See Also</span></span>  
 <span data-ttu-id="cedaf-120">[搜索和替换](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="cedaf-120">[Search and Replace](search-and-replace.md) </span></span>  
 <span data-ttu-id="cedaf-121">[交互式搜索文档](search-documents-interactively.md) </span><span class="sxs-lookup"><span data-stu-id="cedaf-121">[Search Documents Interactively](search-documents-interactively.md) </span></span>  
 <span data-ttu-id="cedaf-122">[使用结果列表搜索文档](search-documents-using-results-lists.md) </span><span class="sxs-lookup"><span data-stu-id="cedaf-122">[Search Documents Using Results Lists](search-documents-using-results-lists.md) </span></span>  
 <span data-ttu-id="cedaf-123">[使用通配符搜索文本](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="cedaf-123">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="cedaf-124">使用正则表达式搜索文本</span><span class="sxs-lookup"><span data-stu-id="cedaf-124">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
