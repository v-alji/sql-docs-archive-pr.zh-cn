---
title: 查询选项 (网格页) 的结果 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.grid.f1
ms.assetid: 764bf435-3aab-4c62-b4e0-64fe020a5a95
author: rothja
ms.author: jroth
ms.openlocfilehash: bf300dd5071128b0259230ae788a27595bd8d29e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589862"
---
# <a name="query-options-results-grid-page"></a><span data-ttu-id="5d5c2-102">“查询选项”中的“结果”（“网格”页）</span><span class="sxs-lookup"><span data-stu-id="5d5c2-102">Query Options Results (Grid Page)</span></span>
  <span data-ttu-id="5d5c2-103">使用此页可以指定以网格格式显示查询结果集的选项。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-103">Use this page to specify the options for displaying a query result set in grid format.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5d5c2-104">选项</span><span class="sxs-lookup"><span data-stu-id="5d5c2-104">Options</span></span>  
 <span data-ttu-id="5d5c2-105">**在结果集中包括查询**</span><span class="sxs-lookup"><span data-stu-id="5d5c2-105">**Include the query in the result set**</span></span>  
 <span data-ttu-id="5d5c2-106">将查询文本作为结果集的一部分返回。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-106">Returns the text of the query as part of the result set.</span></span>  
  
 <span data-ttu-id="5d5c2-107">**复制或保存结果时包括列标题**</span><span class="sxs-lookup"><span data-stu-id="5d5c2-107">**Include column headers when copying or saving the results**</span></span>  
 <span data-ttu-id="5d5c2-108">将结果复制到剪贴板或保存到文件时，包括列标题。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-108">Include column headers (titles) when results are copied to the clipboard, or saved in a file.</span></span> <span data-ttu-id="5d5c2-109">如果希望保存或复制的结果数据只有数据而没有列标题，请清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-109">Clear this check box if you do not want saved or copied result data to have only the data, and not the column headings.</span></span>  
  
 <span data-ttu-id="5d5c2-110">**执行后放弃结果**</span><span class="sxs-lookup"><span data-stu-id="5d5c2-110">**Discard results after execution**</span></span>  
 <span data-ttu-id="5d5c2-111">当屏幕显示接收到查询结果之后，通过放弃查询结果来释放内存。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-111">Free memory by discarding the query results after the screen display has received them.</span></span>  
  
 <span data-ttu-id="5d5c2-112">**在单独选项卡中显示结果**</span><span class="sxs-lookup"><span data-stu-id="5d5c2-112">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="5d5c2-113">在新文档窗口中显示结果集，而不是在查询文档窗口的底部显示。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-113">Display the result set in a new document window, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="5d5c2-114">**执行查询后切换到“结果”选项卡**</span><span class="sxs-lookup"><span data-stu-id="5d5c2-114">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="5d5c2-115">自动将屏幕焦点设置到结果集。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-115">Automatically set the screen focus to the result set.</span></span>  
  
 <span data-ttu-id="5d5c2-116">**检索的最多字符数**</span><span class="sxs-lookup"><span data-stu-id="5d5c2-116">**Maximum Characters Retrieved**</span></span>  
 <span data-ttu-id="5d5c2-117">**非 XML 数据**：</span><span class="sxs-lookup"><span data-stu-id="5d5c2-117">**Non XML data**:</span></span>  
  
 <span data-ttu-id="5d5c2-118">输入一个介于 1 到 65535 之间的数字以指定每个单元中显示的最大字符数。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-118">Enter a number from 1 through 65535 to specify the maximum number of characters that will be displayed in each cell.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d5c2-119">指定大量字符可能会导致结果集中显示的数据截断。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-119">Specifying a large number of characters may cause data in the result set to appear truncated.</span></span> <span data-ttu-id="5d5c2-120">每个单元中显示的最大字符数取决于字号。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-120">The maximum number of characters displayed in each cell is dependent on the font size.</span></span> <span data-ttu-id="5d5c2-121">在返回较大的结果集时，如果此框中的值太大，可能会导致 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 运行时内存不足，从而影响系统性能。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-121">When large result sets are returned, a high value in this box can cause [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to run low on memory and hinder system performance.</span></span>  
  
 <span data-ttu-id="5d5c2-122">**XML 数据**：</span><span class="sxs-lookup"><span data-stu-id="5d5c2-122">**XML data**:</span></span>  
  
 <span data-ttu-id="5d5c2-123">选择**1 MB**、 **2 MB**或**5 mb**。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-123">Select **1 MB**, **2 MB**, or **5 MB**.</span></span> <span data-ttu-id="5d5c2-124">选择 "**无限制**" 将检索所有字符。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-124">Select **Unlimited** to retrieve all characters.</span></span>  
  
 <span data-ttu-id="5d5c2-125">**重置为默认值**</span><span class="sxs-lookup"><span data-stu-id="5d5c2-125">**Reset to Default**</span></span>  
 <span data-ttu-id="5d5c2-126">将此页上的所有值重置为原始默认值。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-126">Resets all values on this page to the original default values.</span></span>  
  
  
