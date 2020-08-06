---
title: MSSQLSERVER_41359 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7cf45a117dcda0827672c6072c603a1fc0866a33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590206"
---
# <a name="mssqlserver_41359"></a><span data-ttu-id="37736-102">MSSQLSERVER_41359</span><span class="sxs-lookup"><span data-stu-id="37736-102">MSSQLSERVER_41359</span></span>
    
## <a name="details"></a><span data-ttu-id="37736-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="37736-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="37736-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="37736-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="37736-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="37736-105">Event ID</span></span>|<span data-ttu-id="37736-106">41359</span><span class="sxs-lookup"><span data-stu-id="37736-106">41359</span></span>|  
|<span data-ttu-id="37736-107">事件源</span><span class="sxs-lookup"><span data-stu-id="37736-107">Event Source</span></span>|<span data-ttu-id="37736-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="37736-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="37736-109">组件</span><span class="sxs-lookup"><span data-stu-id="37736-109">Component</span></span>|<span data-ttu-id="37736-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="37736-110">SQLEngine</span></span>|  
|<span data-ttu-id="37736-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="37736-111">Symbolic Name</span></span>|<span data-ttu-id="37736-112">SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="37736-112">SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="37736-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="37736-113">Message Text</span></span>|<span data-ttu-id="37736-114">当数据库选项 READ_COMMITTED_SNAPSHOT 设置为 ON 时，使用 COMMITTED 隔离级别访问内存优化表的查询不能访问基于磁盘的表。</span><span class="sxs-lookup"><span data-stu-id="37736-114">A query that accesses memory optimized tables using the READ COMMITTED isolation level, cannot access disk based tables when the database option READ_COMMITTED_SNAPSHOT is set to ON.</span></span> <span data-ttu-id="37736-115">使用表提示（例如 WITH (SNAPSHOT)）为内存优化表提供一种支持的隔离级别。</span><span class="sxs-lookup"><span data-stu-id="37736-115">Provide a supported isolation level for the memory optimized table using a table hint, such as WITH (SNAPSHOT).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="37736-116">说明</span><span class="sxs-lookup"><span data-stu-id="37736-116">Explanation</span></span>  
 <span data-ttu-id="37736-117">READ_COMMITTED_SNAPSHOT=ON 的数据库不支持同时访问内存优化表和基于磁盘的表的事务。</span><span class="sxs-lookup"><span data-stu-id="37736-117">The database with READ_COMMITTED_SNAPSHOT=ON does not support the transactions that access both memory-optimized tables and disk based tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="37736-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="37736-118">User Action</span></span>  
 <span data-ttu-id="37736-119">将 READ_COMMITTED_SNAPSHOT 设置为 OFF，或使用表级提示（例如 WITH (SNAPSHOT)）为内存优化表提供一个支持的隔离级别。</span><span class="sxs-lookup"><span data-stu-id="37736-119">Set READ_COMMITTED_SNAPSHOT to OFF or supply a supported isolation level for the memory-optimized table using a table-level hint, such as WITH (SNAPSHOT).</span></span> <span data-ttu-id="37736-120">有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="37736-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37736-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="37736-121">See Also</span></span>  
 [<span data-ttu-id="37736-122">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="37736-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
