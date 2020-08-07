---
title: “性能”事件类别 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Performance event category
- Performance event category [SQL Server]
- event classes [SQL Server], Performance event category
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
author: stevestein
ms.author: sstein
ms.openlocfilehash: b0c076a4132298797313ecbf0874d9d2d4e453cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588512"
---
# <a name="performance-event-category"></a><span data-ttu-id="f74ae-102">Performance 事件类别</span><span class="sxs-lookup"><span data-stu-id="f74ae-102">Performance Event Category</span></span>
  <span data-ttu-id="f74ae-103">使用 **Performance** 事件类别可以监视 **Showplan** 事件类以及在执行 SQL 数据操作语言 (DML) 运算符时生成的事件类。</span><span class="sxs-lookup"><span data-stu-id="f74ae-103">Use the **Performance** event category to monitor **Showplan** event classes and event classes that are produced from the execution of SQL data manipulation language (DML) operators.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f74ae-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="f74ae-104">In This Section</span></span>  
  
|<span data-ttu-id="f74ae-105">主题</span><span class="sxs-lookup"><span data-stu-id="f74ae-105">Topic</span></span>|<span data-ttu-id="f74ae-106">说明</span><span class="sxs-lookup"><span data-stu-id="f74ae-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f74ae-107">Auto Stats 事件类</span><span class="sxs-lookup"><span data-stu-id="f74ae-107">Auto Stats Event Class</span></span>](auto-stats-event-class.md)|<span data-ttu-id="f74ae-108">指示已自动更新索引统计信息和列统计信息。</span><span class="sxs-lookup"><span data-stu-id="f74ae-108">Indicates that an automatic updating of index and column statistics has occurred.</span></span>|  
|[<span data-ttu-id="f74ae-109">Degree of Parallelism (7.0 Insert) 事件类</span><span class="sxs-lookup"><span data-stu-id="f74ae-109">Degree of Parallelism &#40;7.0 Insert&#41; Event Class</span></span>](degree-of-parallelism-7-0-insert-event-class.md)|<span data-ttu-id="f74ae-110">指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已经使用串行或并行计划执行 SELECT、INSERT、UPDATE 或 DELETE 语句。</span><span class="sxs-lookup"><span data-stu-id="f74ae-110">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has executed a SELECT, INSERT, UPDATE, or DELETE statement using either a serial or parallel plan.</span></span> <span data-ttu-id="f74ae-111">此外，还会报告用来执行该操作的 CPU 数。</span><span class="sxs-lookup"><span data-stu-id="f74ae-111">The number of CPUs used to perform the operation is also reported.</span></span>|  
|[<span data-ttu-id="f74ae-112">Performance Statistics 事件类</span><span class="sxs-lookup"><span data-stu-id="f74ae-112">Performance Statistics Event Class</span></span>](performance-statistics-event-class.md)|<span data-ttu-id="f74ae-113">监视正在执行的查询的性能。</span><span class="sxs-lookup"><span data-stu-id="f74ae-113">Monitors performance of the queries that are being executed.</span></span>|  
|[<span data-ttu-id="f74ae-114">Showplan All 事件类</span><span class="sxs-lookup"><span data-stu-id="f74ae-114">Showplan All Event Class</span></span>](showplan-all-event-class.md)|<span data-ttu-id="f74ae-115">标识 SQL 语句中的 **Showplan** 运算符。</span><span class="sxs-lookup"><span data-stu-id="f74ae-115">Identifies **Showplan** operators within a SQL statement.</span></span>|  
|[<span data-ttu-id="f74ae-116">Showplan All for Query Compile 事件类</span><span class="sxs-lookup"><span data-stu-id="f74ae-116">Showplan All for Query Compile Event Class</span></span>](showplan-all-for-query-compile-event-class.md)|<span data-ttu-id="f74ae-117">显示 **Showplan** 运算符的编写时数据。</span><span class="sxs-lookup"><span data-stu-id="f74ae-117">Displays compile time data for **Showplan** operators.</span></span>|  
|[<span data-ttu-id="f74ae-118">Showplan Statistics Profile 事件类</span><span class="sxs-lookup"><span data-stu-id="f74ae-118">Showplan Statistics Profile Event Class</span></span>](showplan-statistics-profile-event-class.md)|<span data-ttu-id="f74ae-119">显示查询的估计开销。</span><span class="sxs-lookup"><span data-stu-id="f74ae-119">Displays the estimated cost of a query.</span></span>|  
|[<span data-ttu-id="f74ae-120">Showplan XML 事件类</span><span class="sxs-lookup"><span data-stu-id="f74ae-120">Showplan XML Event Class</span></span>](showplan-xml-event-class.md)|<span data-ttu-id="f74ae-121">标识 SQL 语句中的 **Showplan** 运算符。</span><span class="sxs-lookup"><span data-stu-id="f74ae-121">Identifies the **Showplan** operators in a SQL statement.</span></span> <span data-ttu-id="f74ae-122">该事件类将每个事件作为定义好的 XML 文档进行存储。</span><span class="sxs-lookup"><span data-stu-id="f74ae-122">The event class stores each event as a well defined XML document.</span></span>|  
|[<span data-ttu-id="f74ae-123">Showplan XML For Query Compile 事件类</span><span class="sxs-lookup"><span data-stu-id="f74ae-123">Showplan XML for Query Compile Event Class</span></span>](showplan-xml-for-query-compile-event-class.md)|<span data-ttu-id="f74ae-124">以 XML 格式显示 **Showplan** 运算符的编写时数据。</span><span class="sxs-lookup"><span data-stu-id="f74ae-124">Displays compile time data for **Showplan** operators in XML format.</span></span>|  
|[<span data-ttu-id="f74ae-125">Showplan XML Statistics Profile 事件类</span><span class="sxs-lookup"><span data-stu-id="f74ae-125">Showplan XML Statistics Profile Event Class</span></span>](showplan-xml-statistics-profile-event-class.md)|<span data-ttu-id="f74ae-126">标识与 SQL 语句关联的 **Showplan** 运算符。</span><span class="sxs-lookup"><span data-stu-id="f74ae-126">Identifies the **Showplan** operators associated with a SQL statement.</span></span> <span data-ttu-id="f74ae-127">将输出一个 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="f74ae-127">The output is an XML document.</span></span>|  
|[<span data-ttu-id="f74ae-128">SQL:FullTextQuery 事件类</span><span class="sxs-lookup"><span data-stu-id="f74ae-128">SQL:FullTextQuery Event Class</span></span>](sql-fulltextquery-event-class.md)|<span data-ttu-id="f74ae-129">指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已执行全文查询。</span><span class="sxs-lookup"><span data-stu-id="f74ae-129">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has executed a full-text query.</span></span>|  
|[<span data-ttu-id="f74ae-130">Plan Guide Successful 事件类</span><span class="sxs-lookup"><span data-stu-id="f74ae-130">Plan Guide Successful Event Class</span></span>](plan-guide-successful-event-class.md)|<span data-ttu-id="f74ae-131">指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已成功为计划指南中包含的查询或批处理生成执行计划。</span><span class="sxs-lookup"><span data-stu-id="f74ae-131">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] successfully produced an execution plan for a query or batch that contained a plan guide.</span></span>|  
|[<span data-ttu-id="f74ae-132">Plan Guide Unsuccessful 事件类</span><span class="sxs-lookup"><span data-stu-id="f74ae-132">Plan Guide Unsuccessful Event Class</span></span>](plan-guide-unsuccessful-event-class.md)|<span data-ttu-id="f74ae-133">指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 无法为计划指南中包含的查询或批处理生成执行计划。</span><span class="sxs-lookup"><span data-stu-id="f74ae-133">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] could not produce an execution plan for a query or batch that contained a plan guide.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f74ae-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f74ae-134">See Also</span></span>  
 [<span data-ttu-id="f74ae-135">扩展事件</span><span class="sxs-lookup"><span data-stu-id="f74ae-135">Extended Events</span></span>](../extended-events/extended-events.md)  
  
  
