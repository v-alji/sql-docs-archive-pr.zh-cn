---
title: MSSQLSERVER_41399 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e134cbc8b39a3c65d9c515183243f0b4caed434
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580767"
---
# <a name="mssqlserver_41399"></a><span data-ttu-id="6cde8-102">MSSQLSERVER_41399</span><span class="sxs-lookup"><span data-stu-id="6cde8-102">MSSQLSERVER_41399</span></span>
    
## <a name="details"></a><span data-ttu-id="6cde8-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="6cde8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6cde8-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="6cde8-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="6cde8-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="6cde8-105">Event ID</span></span>|<span data-ttu-id="6cde8-106">41399</span><span class="sxs-lookup"><span data-stu-id="6cde8-106">41399</span></span>|  
|<span data-ttu-id="6cde8-107">事件源</span><span class="sxs-lookup"><span data-stu-id="6cde8-107">Event Source</span></span>|<span data-ttu-id="6cde8-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6cde8-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6cde8-109">组件</span><span class="sxs-lookup"><span data-stu-id="6cde8-109">Component</span></span>|<span data-ttu-id="6cde8-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6cde8-110">SQLEngine</span></span>|  
|<span data-ttu-id="6cde8-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="6cde8-111">Symbolic Name</span></span>|<span data-ttu-id="6cde8-112">MAX_SORT_ROW_WIDTH_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="6cde8-112">MAX_SORT_ROW_WIDTH_EXCEEDED</span></span>|  
|<span data-ttu-id="6cde8-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="6cde8-113">Message Text</span></span>|<span data-ttu-id="6cde8-114">排序操作太复杂。</span><span class="sxs-lookup"><span data-stu-id="6cde8-114">The sort operation is too complex.</span></span> <span data-ttu-id="6cde8-115">有关详细信息，请查阅 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="6cde8-115">Consult SQL Server Books Online for more information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6cde8-116">说明</span><span class="sxs-lookup"><span data-stu-id="6cde8-116">Explanation</span></span>  
 <span data-ttu-id="6cde8-117">对联接和聚合操作的结果进行排序会通过增加排序缓冲区中行的大小而增加排序操作的复杂程度。</span><span class="sxs-lookup"><span data-stu-id="6cde8-117">Sorting the result of join and aggregation operations increases the complexity of the sort operation by increasing the size of the row in the sort buffer.</span></span> <span data-ttu-id="6cde8-118">此错误意味着行的大小大于本机编译存储过程中排序运算符支持的最大大小。</span><span class="sxs-lookup"><span data-stu-id="6cde8-118">This error means that the size of the row is larger than the maximum size supported by the sort operator in natively compiled stored procedures.</span></span> <span data-ttu-id="6cde8-119">请注意，排序缓冲区中行的大小只由联接的数目以及聚合函数的数目和类型确定。</span><span class="sxs-lookup"><span data-stu-id="6cde8-119">Note that the size of a row in the sort buffer is determined solely by the number of joins and the number and type of aggregate functions.</span></span> <span data-ttu-id="6cde8-120">基表中行的大小不会影响排序缓冲区中行的大小。</span><span class="sxs-lookup"><span data-stu-id="6cde8-120">The size of the rows in the base tables does not affect the size of the row in the buffer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6cde8-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="6cde8-121">User Action</span></span>  
 <span data-ttu-id="6cde8-122">通过删除联接或聚合函数降低查询的复杂程度。</span><span class="sxs-lookup"><span data-stu-id="6cde8-122">Decrease the complexity of the query by removing joins or aggregate functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cde8-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6cde8-123">See Also</span></span>  
 [<span data-ttu-id="6cde8-124">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="6cde8-124">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
