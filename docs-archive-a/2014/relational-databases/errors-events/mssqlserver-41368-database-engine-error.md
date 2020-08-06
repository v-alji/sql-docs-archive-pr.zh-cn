---
title: MSSQLSERVER_41368 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 10e187223a3f35b4b21ede6965e3c9efea2e30c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689388"
---
# <a name="mssqlserver_41368"></a><span data-ttu-id="b7f1e-102">MSSQLSERVER_41368</span><span class="sxs-lookup"><span data-stu-id="b7f1e-102">MSSQLSERVER_41368</span></span>
    
## <a name="details"></a><span data-ttu-id="b7f1e-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="b7f1e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b7f1e-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b7f1e-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="b7f1e-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b7f1e-105">Event ID</span></span>|<span data-ttu-id="b7f1e-106">41368</span><span class="sxs-lookup"><span data-stu-id="b7f1e-106">41368</span></span>|  
|<span data-ttu-id="b7f1e-107">事件源</span><span class="sxs-lookup"><span data-stu-id="b7f1e-107">Event Source</span></span>|<span data-ttu-id="b7f1e-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b7f1e-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b7f1e-109">组件</span><span class="sxs-lookup"><span data-stu-id="b7f1e-109">Component</span></span>|<span data-ttu-id="b7f1e-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b7f1e-110">SQLEngine</span></span>|  
|<span data-ttu-id="b7f1e-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="b7f1e-111">Symbolic Name</span></span>|<span data-ttu-id="b7f1e-112">SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="b7f1e-112">SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="b7f1e-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="b7f1e-113">Message Text</span></span>|<span data-ttu-id="b7f1e-114">只支持对自动提交事务使用 READ COMMITTED 隔离级别访问内存优化表。</span><span class="sxs-lookup"><span data-stu-id="b7f1e-114">Accessing memory optimized tables using the READ COMMITTED isolation level is supported only for autocommit transactions.</span></span> <span data-ttu-id="b7f1e-115">显式或隐式事务不支持此隔离级别。</span><span class="sxs-lookup"><span data-stu-id="b7f1e-115">It is not supported for explicit or implicit transactions.</span></span> <span data-ttu-id="b7f1e-116">使用表提示（例如 WITH (SNAPSHOT)）为内存优化表提供一种支持的隔离级别。</span><span class="sxs-lookup"><span data-stu-id="b7f1e-116">Provide a supported isolation level for the memory optimized table using a table hint, such as WITH (SNAPSHOT).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b7f1e-117">说明</span><span class="sxs-lookup"><span data-stu-id="b7f1e-117">Explanation</span></span>  
 <span data-ttu-id="b7f1e-118">只支持对自动提交事务使用 READ COMMITTED 隔离级别访问内存优化表。</span><span class="sxs-lookup"><span data-stu-id="b7f1e-118">Accessing memory-optimized tables using the READ COMMITTED isolation level is supported only for autocommit transactions.</span></span> <span data-ttu-id="b7f1e-119">有关详细信息，请参阅 [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="b7f1e-119">For more information, see [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md).</span></span>  
  
 <span data-ttu-id="b7f1e-120">当从使用 BEGIN TRANSACTION 启动的显式事务或从隐式事务访问内存优化表时，如果将 IMPLICIT_TRANSACTIONS 设置为 ON，则不支持 READ COMMITTED 隔离级别。</span><span class="sxs-lookup"><span data-stu-id="b7f1e-120">When accessing a memory-optimized table from an explicit transaction that was started with BEGIN TRANSACTION, or from an implicit transaction, if IMPLICIT_TRANSACTIONS is set to ON, the READ COMMITTED isolation level is not supported.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b7f1e-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="b7f1e-121">User Action</span></span>  
 <span data-ttu-id="b7f1e-122">从显式或隐式 READ COMMITTED 事务访问内存优化表时，使用 SNAPSHOT 来访问该表。</span><span class="sxs-lookup"><span data-stu-id="b7f1e-122">When accessing a memory-optimized table from an explicit or implicit READ COMMITTED transaction, use SNAPSHOT to access the table.</span></span> <span data-ttu-id="b7f1e-123">这可以通过将表提示与 (SNAPSHOT) 结合使用来实现 (有关详细信息，请参阅使用[内存优化表的事务隔离级别的准则](../in-memory-oltp/memory-optimized-tables.md)) 或将数据库选项 MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT 设置为 ON (的详细信息，请参阅[ALTER database SET Options &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)) 。</span><span class="sxs-lookup"><span data-stu-id="b7f1e-123">This can be achieved by using the table hint WITH (SNAPSHOT) (for more information, see [Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md)) or by setting the database option MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT to ON (for more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7f1e-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7f1e-124">See Also</span></span>  
 [<span data-ttu-id="b7f1e-125">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="b7f1e-125">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
