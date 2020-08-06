---
title: MSSQLSERVER_41396 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41396 (Database Engine error)
ms.assetid: 4ff04042-8367-46f3-8a16-c94682d6eedb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2386c805b61631c9b843753d74ba6616e7344223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689384"
---
# <a name="mssqlserver_41396"></a><span data-ttu-id="2468f-102">MSSQLSERVER_41396</span><span class="sxs-lookup"><span data-stu-id="2468f-102">MSSQLSERVER_41396</span></span>
    
## <a name="details"></a><span data-ttu-id="2468f-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="2468f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2468f-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="2468f-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="2468f-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="2468f-105">Event ID</span></span>|<span data-ttu-id="2468f-106">41396</span><span class="sxs-lookup"><span data-stu-id="2468f-106">41396</span></span>|  
|<span data-ttu-id="2468f-107">事件源</span><span class="sxs-lookup"><span data-stu-id="2468f-107">Event Source</span></span>|<span data-ttu-id="2468f-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2468f-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2468f-109">组件</span><span class="sxs-lookup"><span data-stu-id="2468f-109">Component</span></span>|<span data-ttu-id="2468f-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2468f-110">SQLEngine</span></span>|  
|<span data-ttu-id="2468f-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="2468f-111">Symbolic Name</span></span>|<span data-ttu-id="2468f-112">MAX_SORT_ROWS_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="2468f-112">MAX_SORT_ROWS_EXCEEDED</span></span>|  
|<span data-ttu-id="2468f-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="2468f-113">Message Text</span></span>|<span data-ttu-id="2468f-114">该排序操作超出了缓冲区限制。</span><span class="sxs-lookup"><span data-stu-id="2468f-114">The sort operation exceeded the buffer limit.</span></span> <span data-ttu-id="2468f-115">存储过程执行已中止。</span><span class="sxs-lookup"><span data-stu-id="2468f-115">The stored procedure execution was aborted.</span></span> <span data-ttu-id="2468f-116">有关详细信息，请查阅 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="2468f-116">Consult SQL Server Books Online for more information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2468f-117">说明</span><span class="sxs-lookup"><span data-stu-id="2468f-117">Explanation</span></span>  
 <span data-ttu-id="2468f-118">本机编译的存储过程在内存中执行排序操作。</span><span class="sxs-lookup"><span data-stu-id="2468f-118">Natively compiled stored procedures perform sort operations in memory.</span></span> <span data-ttu-id="2468f-119">对排序缓冲区的大小存在限制。</span><span class="sxs-lookup"><span data-stu-id="2468f-119">There is a limit on the size of the sort buffer.</span></span> <span data-ttu-id="2468f-120">此错误意味着该排序缓冲区的大小超过了此限制。</span><span class="sxs-lookup"><span data-stu-id="2468f-120">This error means that the size of the sort buffer exceeds this limit.</span></span> <span data-ttu-id="2468f-121">排序操作和存储过程执行已中止。</span><span class="sxs-lookup"><span data-stu-id="2468f-121">The sort operation and the stored procedure execution aborted.</span></span>  
  
 <span data-ttu-id="2468f-122">排序缓冲区中每一行或条目的大小由已排序的行数以及查询中联接的数目和聚合函数的数目和类型确定。</span><span class="sxs-lookup"><span data-stu-id="2468f-122">The size of each row or entry in the sort buffer is determined by the number of rows sorted as well as the number of joins and the number and type of aggregate functions in the query.</span></span> <span data-ttu-id="2468f-123">通过简化查询，可以减小每一行的大小，从而在排序缓冲区中容纳更多的行。</span><span class="sxs-lookup"><span data-stu-id="2468f-123">By simplifying the query, you can reduce the size of each row thereby fitting more rows in the sort buffer.</span></span> <span data-ttu-id="2468f-124">基表中行的大小不会影响排序缓冲区中每一行或条目的大小。</span><span class="sxs-lookup"><span data-stu-id="2468f-124">The size of the rows in the base tables does not affect the size of each row or entry in the sort buffer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2468f-125">用户操作</span><span class="sxs-lookup"><span data-stu-id="2468f-125">User Action</span></span>  
 <span data-ttu-id="2468f-126">选择更少的行，或者通过删除联接或聚合函数降低查询的复杂程度。</span><span class="sxs-lookup"><span data-stu-id="2468f-126">Select fewer rows or decrease the complexity of the query by removing joins or aggregate functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2468f-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2468f-127">See Also</span></span>  
 [<span data-ttu-id="2468f-128">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="2468f-128">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
