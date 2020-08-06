---
title: MSSQLSERVER_41333 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6ba3cfc9627b4b44c3c9eccc620fb16bb94b861b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689921"
---
# <a name="mssqlserver_41333"></a><span data-ttu-id="4073b-102">MSSQLSERVER_41333</span><span class="sxs-lookup"><span data-stu-id="4073b-102">MSSQLSERVER_41333</span></span>
    
## <a name="details"></a><span data-ttu-id="4073b-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="4073b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4073b-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="4073b-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="4073b-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4073b-105">Event ID</span></span>|<span data-ttu-id="4073b-106">41333</span><span class="sxs-lookup"><span data-stu-id="4073b-106">41333</span></span>|  
|<span data-ttu-id="4073b-107">事件源</span><span class="sxs-lookup"><span data-stu-id="4073b-107">Event Source</span></span>|<span data-ttu-id="4073b-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4073b-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4073b-109">组件</span><span class="sxs-lookup"><span data-stu-id="4073b-109">Component</span></span>|<span data-ttu-id="4073b-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4073b-110">SQLEngine</span></span>|  
|<span data-ttu-id="4073b-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="4073b-111">Symbolic Name</span></span>|<span data-ttu-id="4073b-112">CROSS_CONTAINER_ISOLATION_FAILURE</span><span class="sxs-lookup"><span data-stu-id="4073b-112">CROSS_CONTAINER_ISOLATION_FAILURE</span></span>|  
|<span data-ttu-id="4073b-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="4073b-113">Message Text</span></span>|<span data-ttu-id="4073b-114">以下事务必须能够在快照隔离下访问内存优化表和本机编译的存储过程：RepeatableRead 事务、可串行事务以及访问在 RepeatableRead 或可串行隔离中未进行内存优化的表的事务。</span><span class="sxs-lookup"><span data-stu-id="4073b-114">The following transactions must access memory optimized tables and natively compiled stored procedures under snapshot isolation: RepeatableRead transactions, Serializable transactions, and transactions that access tables that are not memory optimized in RepeatableRead or Serializable isolation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4073b-115">说明</span><span class="sxs-lookup"><span data-stu-id="4073b-115">Explanation</span></span>  
 <span data-ttu-id="4073b-116">对于基于磁盘的事务和 XTP 事务之间的更高隔离级别用户，存在一些限制。</span><span class="sxs-lookup"><span data-stu-id="4073b-116">There are restrictions against the user of the higher isolation levels between disk based transactions and XTP transactions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4073b-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="4073b-117">User Action</span></span>  
 <span data-ttu-id="4073b-118">不要尝试对内存优化表（和本机编译存储过程）以及基于磁盘的表执行高级别隔离操作。</span><span class="sxs-lookup"><span data-stu-id="4073b-118">Don't attempt high level isolation operations on memory-optimized tables (and natively compiled procedures) and disk based tables.</span></span>  
  
 <span data-ttu-id="4073b-119">有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="4073b-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4073b-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4073b-120">See Also</span></span>  
 [<span data-ttu-id="4073b-121">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="4073b-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
