---
title: 选项 (查询结果-SQL Server-结果到网格页) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLResultsToGrid
ms.assetid: f88a0f5c-e800-473b-ae23-c3943de5ed63
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f9cec7e544c295420a9ae2a25e96ea9aa82030b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690777"
---
# <a name="options-query-results-sql-server-results-to-grid-page"></a><span data-ttu-id="ac8bc-102">选项 (查询结果-SQL Server-结果到网格页) </span><span class="sxs-lookup"><span data-stu-id="ac8bc-102">Options (Query Results-SQL Server-Results to Grid Page)</span></span>
  <span data-ttu-id="ac8bc-103">使用此页可以指定以网格格式显示查询结果集的选项。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-103">Use this page to specify the options for displaying a query result set in grid format.</span></span> <span data-ttu-id="ac8bc-104">对这些选项所做的更改只应用于新的 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查询。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-104">Changes to these options are applied only to new [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="ac8bc-105">若要更改当前查询的选项，请在 "**查询**" 菜单上单击 "**查询选项**"，或在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查询窗口中右键单击并选择 "**查询选项**"。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-105">To change the options for the current queries, click **Query Options** on the **Query** menu, or right-click in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window and select **Query Options**.</span></span> <span data-ttu-id="ac8bc-106">在 **“查询选项”** 对话框的左窗格中，在 **“结果”** 下，单击 **“网格”**。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-106">In the left pane of the **Query Options** dialog box, under **Results**, click **Grid**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="ac8bc-107">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="ac8bc-107">UI element list</span></span>  
 <span data-ttu-id="ac8bc-108">**在结果集中包括查询**</span><span class="sxs-lookup"><span data-stu-id="ac8bc-108">**Include the query in the result set**</span></span>  
 <span data-ttu-id="ac8bc-109">作为查询输出的一部分返回查询文本。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-109">Returns the text of the query as part of the query output.</span></span>  
  
 <span data-ttu-id="ac8bc-110">**复制或保存结果时包括列标题**</span><span class="sxs-lookup"><span data-stu-id="ac8bc-110">**Include column headers when copying or saving the results**</span></span>  
 <span data-ttu-id="ac8bc-111">在将结果复制到剪贴板或保存到文件时若要包括列标题，请选中此复选框。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-111">Select this check box to include column headers when results are copied to the clipboard, or saved in a file.</span></span> <span data-ttu-id="ac8bc-112">如果希望保存或复制的结果数据只有数据而没有列标题，请清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-112">Clear this check box if you want saved or copied result data to have only the data and not the column headings.</span></span>  
  
 <span data-ttu-id="ac8bc-113">**执行后放弃结果**</span><span class="sxs-lookup"><span data-stu-id="ac8bc-113">**Discard results after execution**</span></span>  
 <span data-ttu-id="ac8bc-114">禁止在查看窗格中显示查询结果。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-114">Prevents query results from being displayed in the reviewing pane.</span></span> <span data-ttu-id="ac8bc-115">结果将在执行查询之后立即放弃。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-115">The results are discarded immediately after execution.</span></span> <span data-ttu-id="ac8bc-116">指定此选项可帮助节省内存。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-116">Specifying this option helps save memory.</span></span>  
  
 <span data-ttu-id="ac8bc-117">**在单独选项卡中显示结果**</span><span class="sxs-lookup"><span data-stu-id="ac8bc-117">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="ac8bc-118">选中此复选框可在新选项卡中显示结果集，而不是在查询文档窗口的底部显示。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-118">Select this check box to display the result set in a new tab, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="ac8bc-119">**执行查询后切换到“结果”选项卡**</span><span class="sxs-lookup"><span data-stu-id="ac8bc-119">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="ac8bc-120">单击此项可在执行查询时，将屏幕焦点自动设置到结果窗格。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-120">Click to automatically set the screen focus to the results pane upon execution of a query.</span></span>  
  
 <span data-ttu-id="ac8bc-121">**检索的最多字符数**</span><span class="sxs-lookup"><span data-stu-id="ac8bc-121">**Maximum Characters Retrieved**</span></span>  
 <span data-ttu-id="ac8bc-122">**非 XML 数据**：</span><span class="sxs-lookup"><span data-stu-id="ac8bc-122">**Non XML data**:</span></span>  
  
 <span data-ttu-id="ac8bc-123">输入一个介于 1 到 65535 之间的数字以指定每个单元中显示的最大字符数。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-123">Enter a number from 1 through 65535 to specify the maximum number of characters that will be displayed in each cell.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac8bc-124">指定大量字符可能会导致结果集中显示的数据截断。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-124">Specifying a large number of characters may cause data in the result set to appear truncated.</span></span> <span data-ttu-id="ac8bc-125">每个单元中显示的最大字符数取决于字号。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-125">The maximum number of characters displayed in each cell is dependent on the font size.</span></span> <span data-ttu-id="ac8bc-126">在返回较大的结果集时，如果此框中的值太大，可能会导致 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 运行时内存不足，从而影响系统性能。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-126">When large result sets are returned, a high value in this box can cause [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to run low on memory and hinder system performance.</span></span>  
  
 <span data-ttu-id="ac8bc-127">**XML 数据**：</span><span class="sxs-lookup"><span data-stu-id="ac8bc-127">**XML data**:</span></span>  
  
 <span data-ttu-id="ac8bc-128">选择**1 MB**、 **2 MB**或**5 mb**。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-128">Select **1 MB**, **2 MB**, or **5 MB**.</span></span> <span data-ttu-id="ac8bc-129">选择 "**无限制**" 将检索所有字符。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-129">Select **Unlimited** to retrieve all characters.</span></span>  
  
 <span data-ttu-id="ac8bc-130">**重置为默认值**</span><span class="sxs-lookup"><span data-stu-id="ac8bc-130">**Reset to Default**</span></span>  
 <span data-ttu-id="ac8bc-131">将此页上的所有值重置为原始默认值。</span><span class="sxs-lookup"><span data-stu-id="ac8bc-131">Resets all values on this page to the original default values.</span></span>  
  
  
