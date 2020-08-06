---
title: MSSQLSERVER_3961 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3961 (Database Engine error)
ms.assetid: 3bbc6965-6445-400c-940a-2d85b037513f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f55be9288b3c2e559633d0f67709829466fc8815
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590214"
---
# <a name="mssqlserver_3961"></a><span data-ttu-id="6538d-102">MSSQLSERVER_3961</span><span class="sxs-lookup"><span data-stu-id="6538d-102">MSSQLSERVER_3961</span></span>
    
## <a name="details"></a><span data-ttu-id="6538d-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="6538d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6538d-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="6538d-104">Product Name</span></span>|<span data-ttu-id="6538d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6538d-105">SQL Server</span></span>|  
|<span data-ttu-id="6538d-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="6538d-106">Event ID</span></span>|<span data-ttu-id="6538d-107">3961</span><span class="sxs-lookup"><span data-stu-id="6538d-107">3961</span></span>|  
|<span data-ttu-id="6538d-108">事件源</span><span class="sxs-lookup"><span data-stu-id="6538d-108">Event Source</span></span>|<span data-ttu-id="6538d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6538d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6538d-110">组件</span><span class="sxs-lookup"><span data-stu-id="6538d-110">Component</span></span>|<span data-ttu-id="6538d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6538d-111">SQLEngine</span></span>|  
|<span data-ttu-id="6538d-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="6538d-112">Symbolic Name</span></span>|<span data-ttu-id="6538d-113">XACT_METADATA_INVALID</span><span class="sxs-lookup"><span data-stu-id="6538d-113">XACT_METADATA_INVALID</span></span>|  
|<span data-ttu-id="6538d-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="6538d-114">Message Text</span></span>|<span data-ttu-id="6538d-115">数据库 '%.\*ls' 中的快照隔离事务失败，因为自此事务启动后，该语句所访问的对象已由其他并发事务中的 DDL 语句修改。</span><span class="sxs-lookup"><span data-stu-id="6538d-115">Snapshot isolation transaction failed in database '%.\*ls' because the object accessed by the statement has been modified by a DDL statement in another concurrent transaction since the start of this transaction.</span></span>  <span data-ttu-id="6538d-116">禁用它是因为元数据未进行版本控制。</span><span class="sxs-lookup"><span data-stu-id="6538d-116">It is disallowed because the metadata is not versioned.</span></span> <span data-ttu-id="6538d-117">在混合了快照隔离操作的情况下，对元数据进行并发更新可能导致不一致。</span><span class="sxs-lookup"><span data-stu-id="6538d-117">A concurrent update to metadata can lead to inconsistency if mixed with snapshot isolation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6538d-118">说明</span><span class="sxs-lookup"><span data-stu-id="6538d-118">Explanation</span></span>  
 <span data-ttu-id="6538d-119">如果在快照隔离情况下查询元数据，同时有一个并发 DDL 语句在更新元数据，而该元数据在快照隔离情况下被访问，则可能发生此错误。</span><span class="sxs-lookup"><span data-stu-id="6538d-119">This error can occur if you are querying metadata under snapshot isolation and there is a concurrent DDL statement that updates the metadata that is being accessed under snapshot isolation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6538d-120">不支持元数据的版本控制。</span><span class="sxs-lookup"><span data-stu-id="6538d-120">does not support versioning of metadata.</span></span> <span data-ttu-id="6538d-121">因此，对于快照隔离情况下在显式事务中能够执行的具体 DDL 操作会存在限制。</span><span class="sxs-lookup"><span data-stu-id="6538d-121">For this reason, there are restrictions on what DDL operations can be performed within an explicit transaction running under snapshot isolation.</span></span> <span data-ttu-id="6538d-122">根据定义，隐式事务是单个语句，有了该语句就可以强制实施快照隔离的语义，即使在 DDL 语句存在的情况下也是如此。</span><span class="sxs-lookup"><span data-stu-id="6538d-122">An implicit transaction, by definition, is a single statement which makes it possible to enforce the semantics of snapshot isolation even with DDL statements.</span></span> <span data-ttu-id="6538d-123">在快照隔离下，以下 DDL 语句不允许出现在 BEGIN TRANSACTION 语句后：ALTER TABLE、CREATE INDEX、CREATE XML INDEX、ALTER INDEX、DROP INDEX、DBCC REINDEX、ALTER PARTITION FUNCTION、ALTER PARTITION SCHEME 或任何常用语言运行时(CLR) DDL 语句。</span><span class="sxs-lookup"><span data-stu-id="6538d-123">The following DDL statements are not permitted under snapshot isolation after a BEGIN TRANSACTION statement: ALTER TABLE, CREATE INDEX, CREATE XML INDEX, ALTER INDEX, DROP INDEX, DBCC REINDEX, ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME, or any common language runtime (CLR) DDL statement.</span></span> <span data-ttu-id="6538d-124">在隐式事务中使用快照隔离时，允许使用这些语句。</span><span class="sxs-lookup"><span data-stu-id="6538d-124">These statements are permitted when you are using snapshot isolation within implicit transactions.</span></span> <span data-ttu-id="6538d-125">根据定义，隐式事务是单个语句，有了该语句就可以强制实施快照隔离的语义，即使在 DDL 语句存在的情况下也是如此。</span><span class="sxs-lookup"><span data-stu-id="6538d-125">An implicit transaction, by definition, is a single statement which makes it possible to enforce the semantics of snapshot isolation even with DDL statements.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6538d-126">用户操作</span><span class="sxs-lookup"><span data-stu-id="6538d-126">User Action</span></span>  
 <span data-ttu-id="6538d-127">在查询元数据之前将快照隔离级别更改为诸如“已提交读”之类的非快照隔离级别。</span><span class="sxs-lookup"><span data-stu-id="6538d-127">Change the snapshot isolation level to a non-snapshot isolation level such as read committed before querying metadata.</span></span>  
  
  
