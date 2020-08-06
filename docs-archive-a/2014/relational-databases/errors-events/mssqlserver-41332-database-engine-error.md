---
title: MSSQLSERVER_41332 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41332 (Database Engine error)
ms.assetid: d3403c3e-d178-4006-b6c9-c18609562db5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 72a87838673f07f7a40596517ab54533d944e15e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588574"
---
# <a name="mssqlserver_41332"></a><span data-ttu-id="fdddb-102">MSSQLSERVER_41332</span><span class="sxs-lookup"><span data-stu-id="fdddb-102">MSSQLSERVER_41332</span></span>
    
## <a name="details"></a><span data-ttu-id="fdddb-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="fdddb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fdddb-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="fdddb-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="fdddb-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="fdddb-105">Event ID</span></span>|<span data-ttu-id="fdddb-106">41332</span><span class="sxs-lookup"><span data-stu-id="fdddb-106">41332</span></span>|  
|<span data-ttu-id="fdddb-107">事件源</span><span class="sxs-lookup"><span data-stu-id="fdddb-107">Event Source</span></span>|<span data-ttu-id="fdddb-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="fdddb-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="fdddb-109">组件</span><span class="sxs-lookup"><span data-stu-id="fdddb-109">Component</span></span>|<span data-ttu-id="fdddb-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="fdddb-110">SQLEngine</span></span>|  
|<span data-ttu-id="fdddb-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="fdddb-111">Symbolic Name</span></span>|<span data-ttu-id="fdddb-112">SQL_SNAPSHOT_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="fdddb-112">SQL_SNAPSHOT_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="fdddb-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="fdddb-113">Message Text</span></span>|<span data-ttu-id="fdddb-114">当会话 TRANSACTION ISOLATION LEVEL 设置为 SNAPSHOT 时，无法访问或创建内存优化表和本机编译的存储过程。</span><span class="sxs-lookup"><span data-stu-id="fdddb-114">Memory optimized tables and natively compiled stored procedures cannot be accessed or created when the session TRANSACTION ISOLATION LEVEL is set to SNAPSHOT.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fdddb-115">说明</span><span class="sxs-lookup"><span data-stu-id="fdddb-115">Explanation</span></span>  
 <span data-ttu-id="fdddb-116">事务在快照隔离级别启动，然后尝试使用不兼容的功能。</span><span class="sxs-lookup"><span data-stu-id="fdddb-116">The transaction was started in snapshot isolation level and then attempted to use an incompatible feature.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fdddb-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="fdddb-117">User Action</span></span>  
 <span data-ttu-id="fdddb-118">使用不同的隔离级别启动事务。</span><span class="sxs-lookup"><span data-stu-id="fdddb-118">Start the transaction with a different isolation level.</span></span> <span data-ttu-id="fdddb-119">有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="fdddb-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdddb-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fdddb-120">See Also</span></span>  
 [<span data-ttu-id="fdddb-121">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="fdddb-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
