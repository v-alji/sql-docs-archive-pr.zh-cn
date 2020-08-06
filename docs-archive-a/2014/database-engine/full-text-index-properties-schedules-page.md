---
title: 全文索引属性 (计划页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.schedule.f1
ms.assetid: a828e284-097e-4854-8c49-931934eb73bf
author: rothja
ms.author: jroth
ms.openlocfilehash: f49fb37295f0b3eb2f1a2dd04d44ab86236f109a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591537"
---
# <a name="full-text-index-properties-schedules-page"></a><span data-ttu-id="51868-102">全文索引属性（“计划”页）</span><span class="sxs-lookup"><span data-stu-id="51868-102">Full-Text Index Properties (Schedules Page)</span></span>
  <span data-ttu-id="51868-103">使用此页可以查看和创建运行 SQL Server 代理作业的计划，该作业用于启动对全文索引基表的更新的增量填充。</span><span class="sxs-lookup"><span data-stu-id="51868-103">Use this page to view and create schedules for running a SQL Server Agent job that starts an incremental population of updates to the base table of the full-text index.</span></span> <span data-ttu-id="51868-104">如果基表或视图不包含 `timestamp` 数据类型的列，则执行完全填充。</span><span class="sxs-lookup"><span data-stu-id="51868-104">If the base table or view does not contain a column of the `timestamp` data type, a full population is performed.</span></span>  
  
 <span data-ttu-id="51868-105">**查看或更改全文索引的属性**</span><span class="sxs-lookup"><span data-stu-id="51868-105">**To view or change the properties of a full-text index**</span></span>  
  
-   [<span data-ttu-id="51868-106">管理全文索引</span><span class="sxs-lookup"><span data-stu-id="51868-106">Manage Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="51868-107">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="51868-107">UI element list</span></span>  
 <span data-ttu-id="51868-108">**计划**</span><span class="sxs-lookup"><span data-stu-id="51868-108">**Schedules**</span></span>  
 <span data-ttu-id="51868-109">列出全文索引的基表上的每个计划增量填充（如果有）。</span><span class="sxs-lookup"><span data-stu-id="51868-109">Lists each scheduled incremental population, if any, on the base table for the full-text index.</span></span>  
  
 <span data-ttu-id="51868-110">**名称**</span><span class="sxs-lookup"><span data-stu-id="51868-110">**Name**</span></span>  
 <span data-ttu-id="51868-111">显示每个计划填充的名称。</span><span class="sxs-lookup"><span data-stu-id="51868-111">Displays the name of the each scheduled population.</span></span>  
  
 <span data-ttu-id="51868-112">**填充类型**</span><span class="sxs-lookup"><span data-stu-id="51868-112">**Population Type**</span></span>  
 <span data-ttu-id="51868-113">显示每个计划填充的类型。</span><span class="sxs-lookup"><span data-stu-id="51868-113">Displays the type of each scheduled population.</span></span>  
  
 <span data-ttu-id="51868-114">**已启用**</span><span class="sxs-lookup"><span data-stu-id="51868-114">**Enabled**</span></span>  
 <span data-ttu-id="51868-115">指示当前是启用还是禁用计划填充。</span><span class="sxs-lookup"><span data-stu-id="51868-115">Indicates whether the scheduled population is currently enabled or disabled.</span></span>  
  
 <span data-ttu-id="51868-116">**说明**</span><span class="sxs-lookup"><span data-stu-id="51868-116">**Description**</span></span>  
 <span data-ttu-id="51868-117">显示创建计划时指定的说明。</span><span class="sxs-lookup"><span data-stu-id="51868-117">Displays the description that was specified when the schedule was created.</span></span>  
  
 <span data-ttu-id="51868-118">**新建**</span><span class="sxs-lookup"><span data-stu-id="51868-118">**New**</span></span>  
 <span data-ttu-id="51868-119">单击此选项可以为填充全文索引创建新计划。</span><span class="sxs-lookup"><span data-stu-id="51868-119">Click to create a new schedule for populating the full-text index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51868-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="51868-120">See Also</span></span>  
 <span data-ttu-id="51868-121">[使用全文索引向导](../relational-databases/search/use-the-full-text-indexing-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="51868-121">[Use the Full-Text Indexing Wizard](../relational-databases/search/use-the-full-text-indexing-wizard.md) </span></span>  
 [<span data-ttu-id="51868-122">填充全文索引</span><span class="sxs-lookup"><span data-stu-id="51868-122">Populate Full-Text Indexes</span></span>](../relational-databases/search/populate-full-text-indexes.md)  
  
  
