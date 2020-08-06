---
title: SQL Server Profiler-"查找" 对话框 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.find.f1
helpviewer_keywords:
- Find dialog box
ms.assetid: dfaeec04-93d3-4214-9fc1-38b80179b36b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cedf50930c06d211ebcee0c45a249667219f392c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691854"
---
# <a name="sql-server-profiler---find-dialog-box"></a><span data-ttu-id="8cbca-102">SQL Server Profiler -“查找”对话框</span><span class="sxs-lookup"><span data-stu-id="8cbca-102">SQL Server Profiler - Find Dialog Box</span></span>
  <span data-ttu-id="8cbca-103">使用 **“查找”** 对话框可以在跟踪中搜索特定字符或字词。</span><span class="sxs-lookup"><span data-stu-id="8cbca-103">Use the **Find** dialog box to search a trace for specific characters or words.</span></span> <span data-ttu-id="8cbca-104">若要取消正在进行的搜索，请按 Esc。</span><span class="sxs-lookup"><span data-stu-id="8cbca-104">To cancel a search in progress, press ESC.</span></span>  
  
 <span data-ttu-id="8cbca-105">若要在 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]中打开此对话框，请在 **“编辑”** 菜单上，单击 **“查找”**。</span><span class="sxs-lookup"><span data-stu-id="8cbca-105">To open this dialog box in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], on the **Edit** menu, click **Find**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8cbca-106">选项</span><span class="sxs-lookup"><span data-stu-id="8cbca-106">Options</span></span>  
 <span data-ttu-id="8cbca-107">**查找内容**</span><span class="sxs-lookup"><span data-stu-id="8cbca-107">**Find what**</span></span>  
 <span data-ttu-id="8cbca-108">输入要搜索的文本。</span><span class="sxs-lookup"><span data-stu-id="8cbca-108">Enter the text that you want to search for.</span></span> <span data-ttu-id="8cbca-109">该搜索匹配包含指定字符串的任何字符串。</span><span class="sxs-lookup"><span data-stu-id="8cbca-109">The search matches any string containing the specified string.</span></span> <span data-ttu-id="8cbca-110">例如，针对“Completed”的搜索匹配“SQL:BatchCompleted”。</span><span class="sxs-lookup"><span data-stu-id="8cbca-110">For example, searching for "Completed" matches "SQL:BatchCompleted."</span></span> <span data-ttu-id="8cbca-111">不支持通配符（\*、? 等）。</span><span class="sxs-lookup"><span data-stu-id="8cbca-111">Wild card characters (\*, ?, etc.) are not supported.</span></span>  
  
 <span data-ttu-id="8cbca-112">**在列中搜索**</span><span class="sxs-lookup"><span data-stu-id="8cbca-112">**Search in column**</span></span>  
 <span data-ttu-id="8cbca-113">单击要搜索的数据列，或单击 " **\<All columns>** 搜索" 以搜索跟踪中的所有数据列。</span><span class="sxs-lookup"><span data-stu-id="8cbca-113">Click a data column to search, or click **\<All columns>** to search all the data columns in the trace.</span></span>  
  
 <span data-ttu-id="8cbca-114">**匹配大小写**</span><span class="sxs-lookup"><span data-stu-id="8cbca-114">**Match case**</span></span>  
 <span data-ttu-id="8cbca-115">查找与“查找内容”\*\*\*\* 框中的大小写完全匹配的文本。</span><span class="sxs-lookup"><span data-stu-id="8cbca-115">Finds text that has the same case as the **Find what** box.</span></span> <span data-ttu-id="8cbca-116">清除此复选框将在跟踪中不区分文本字符的大小写形式查找匹配项。</span><span class="sxs-lookup"><span data-stu-id="8cbca-116">Clear this check box to find examples in the trace that are in both uppercase and lowercase text characters.</span></span>  
  
 <span data-ttu-id="8cbca-117">**全字匹配**</span><span class="sxs-lookup"><span data-stu-id="8cbca-117">**Match whole word**</span></span>  
 <span data-ttu-id="8cbca-118">将搜索结果限制为完整的字词。</span><span class="sxs-lookup"><span data-stu-id="8cbca-118">Restricts the search to entire words.</span></span> <span data-ttu-id="8cbca-119">清除 **“全字匹配”** 复选框可以搜索单词内的部分字符。</span><span class="sxs-lookup"><span data-stu-id="8cbca-119">Clear the **Match whole word** check box to search for characters within a word.</span></span>  
  
 <span data-ttu-id="8cbca-120">**查找下一个**</span><span class="sxs-lookup"><span data-stu-id="8cbca-120">**Find Next**</span></span>  
 <span data-ttu-id="8cbca-121">查找“查找内容”\*\*\*\* 框中字符的下一个匹配项。</span><span class="sxs-lookup"><span data-stu-id="8cbca-121">Finds the next example of the characters in the **Find what** box.</span></span>  
  
 <span data-ttu-id="8cbca-122">**查找上一个**</span><span class="sxs-lookup"><span data-stu-id="8cbca-122">**Find Previous**</span></span>  
 <span data-ttu-id="8cbca-123">在跟踪中向后搜索，以查找“查找内容”\*\*\*\* 框中字符的上一个匹配项。</span><span class="sxs-lookup"><span data-stu-id="8cbca-123">Searches backwards in the trace, to find the previous example of the characters in the **Find what** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cbca-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8cbca-124">See Also</span></span>  
 <span data-ttu-id="8cbca-125">[在跟踪 &#40;SQL Server Profiler 时查找值或数据列&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="8cbca-125">[Find a Value or Data Column While Tracing &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="8cbca-126">[创建跟踪 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="8cbca-126">[Create a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="8cbca-127">[打开跟踪表 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="8cbca-127">[Open a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="8cbca-128">[打开跟踪文件 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="8cbca-128">[Open a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="8cbca-129">[SQL Server Profiler 模板和权限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="8cbca-129">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="8cbca-130">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="8cbca-130">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
