---
title: MSSQL_ENG002601 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG002601 error
ms.assetid: 657c3ae6-9e4b-4c60-becc-4caf7435c1dc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2e8340fef83749fd6d041af42566b10ed3542c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693254"
---
# <a name="mssql_eng002601"></a><span data-ttu-id="7ca5e-102">MSSQL_ENG002601</span><span class="sxs-lookup"><span data-stu-id="7ca5e-102">MSSQL_ENG002601</span></span>
    
## <a name="message-details"></a><span data-ttu-id="7ca5e-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="7ca5e-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ca5e-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="7ca5e-104">Product Name</span></span>|<span data-ttu-id="7ca5e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7ca5e-105">SQL Server</span></span>|  
|<span data-ttu-id="7ca5e-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="7ca5e-106">Event ID</span></span>|<span data-ttu-id="7ca5e-107">2601</span><span class="sxs-lookup"><span data-stu-id="7ca5e-107">2601</span></span>|  
|<span data-ttu-id="7ca5e-108">事件源</span><span class="sxs-lookup"><span data-stu-id="7ca5e-108">Event Source</span></span>|<span data-ttu-id="7ca5e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7ca5e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7ca5e-110">组件</span><span class="sxs-lookup"><span data-stu-id="7ca5e-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="7ca5e-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="7ca5e-111">Symbolic Name</span></span>|<span data-ttu-id="7ca5e-112">空值</span><span class="sxs-lookup"><span data-stu-id="7ca5e-112">N/A</span></span>|  
|<span data-ttu-id="7ca5e-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="7ca5e-113">Message Text</span></span>|<span data-ttu-id="7ca5e-114">不能在具有唯一索引 '%.\*ls' 的对象 '%.\*ls' 中插入重复键的行。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-114">Cannot insert duplicate key row in object '%.\*ls' with unique index '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7ca5e-115">说明</span><span class="sxs-lookup"><span data-stu-id="7ca5e-115">Explanation</span></span>  
 <span data-ttu-id="7ca5e-116">这是可能引发的一般错误，不管是否复制数据库，都会引发该错误。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-116">This is a general error that can be raised regardless of whether a database is replicated.</span></span> <span data-ttu-id="7ca5e-117">在已复制的数据库中，通常会引发该错误，因为尚未跨拓扑对主键进行适当的管理。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-117">In replicated databases, the error is typically raised because primary keys have not been managed appropriately across the topology.</span></span> <span data-ttu-id="7ca5e-118">在分布式环境中，确保没有将同一值插入到多个节点上的主键列或任何其他唯一列，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-118">In a distributed environment it is essential to ensure that the same value is not inserted into a primary key column or any other unique column at more than one node.</span></span> <span data-ttu-id="7ca5e-119">可能的原因包括：</span><span class="sxs-lookup"><span data-stu-id="7ca5e-119">Possible causes include the following:</span></span>  
  
-   <span data-ttu-id="7ca5e-120">在多个节点上对行进行了插入和更新。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-120">Inserts and updates to a row are occurring at more than one node.</span></span> <span data-ttu-id="7ca5e-121">合并复制和事务性复制的可更新订阅都提供了冲突检测和解决，但是最好还是只在一个节点上插入或更新给定行。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-121">Merge replication and updatable subscriptions for transactional replication both provide conflict detection and resolution, but it is still preferable to insert or update a given row at only one node.</span></span> <span data-ttu-id="7ca5e-122">对等事务性复制没有提供冲突检测和解决，它要求对插入和更新进行分区。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-122">Peer-to-peer transactional does not provide conflict detection and resolution; it requires that inserts and updates be partitioned.</span></span>  
  
-   <span data-ttu-id="7ca5e-123">在应该为只读的订阅服务器上插入了行。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-123">A row was inserted at a Subscriber that should be read-only.</span></span> <span data-ttu-id="7ca5e-124">应该将快照发布的订阅服务器视为只读，就像事务发布的订阅服务器一样，除非使用了可更新的订阅或对等事务性复制。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-124">Subscribers to snapshot publications should be treated as read-only, as should Subscribers to transactional publications unless updatable subscriptions or peer-to-peer transactional replication is used.</span></span>  
  
-   <span data-ttu-id="7ca5e-125">使用了具有标识列的表，但是没有对该列进行适当的管理。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-125">A table with an identity column is being used, but the column is not managed appropriately.</span></span>  
  
-   <span data-ttu-id="7ca5e-126">在合并复制过程中，插入系统表 **MSmerge_contents**时也可发生该错误；所引起的错误类似于：不能在具有唯一索引“ucl1SycContents”的对象“MSmerge_contents”中插入重复键的行。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-126">In merge replication, this error can also occur during an insert into the system table **MSmerge_contents**; the error raised is similar to: Cannot insert duplicate key row in object 'MSmerge_contents' with unique index 'ucl1SycContents.'</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7ca5e-127">用户操作</span><span class="sxs-lookup"><span data-stu-id="7ca5e-127">User Action</span></span>  
 <span data-ttu-id="7ca5e-128">所需操作取决于引发错误的原因：</span><span class="sxs-lookup"><span data-stu-id="7ca5e-128">The action required depends on the reason the error was raised:</span></span>  
  
-   <span data-ttu-id="7ca5e-129">在多个节点上对行进行了插入和更新。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-129">Inserts and updates to a row are occurring at more than one node.</span></span>  
  
     <span data-ttu-id="7ca5e-130">不管使用哪种复制类型，我们都建议您尽可能地对插入和更新进行分区，因为这样可以减少检测和解决冲突所需的处理操作。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-130">Regardless of the type of replication used, we recommend that you partition inserts and updates whenever possible, because this reduces the processing required for conflict detection and resolution.</span></span> <span data-ttu-id="7ca5e-131">对于对等事务性复制，需要对插入和更新进行分区。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-131">For peer-to-peer transactional replication, partitioning inserts and updates is required.</span></span> <span data-ttu-id="7ca5e-132">有关详细信息，请参阅 [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-132">For more information, see [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="7ca5e-133">在应该为只读的订阅服务器上插入了行。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-133">A row was inserted at a Subscriber that should be read-only.</span></span>  
  
     <span data-ttu-id="7ca5e-134">除非使用合并复制、具有可更新订阅的事务性复制或对等事务性复制，否则不要在订阅服务器上插入或更新行。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-134">Do not insert or update rows at the Subscriber unless you are using merge replication, transactional replication with updatable subscriptions, or peer-to-peer transactional replication.</span></span>  
  
-   <span data-ttu-id="7ca5e-135">使用了具有标识列的表，但是没有对该列进行适当的管理。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-135">A table with an identity column is being used, but the column is not managed appropriately.</span></span>  
  
     <span data-ttu-id="7ca5e-136">对于合并复制和具有可更新订阅的事务性复制，标识列应该由复制自动管理。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-136">For merge replication and transactional replication with updatable subscriptions, identity columns should be managed automatically by replication.</span></span> <span data-ttu-id="7ca5e-137">对于对等事务性复制，必须手动进行管理。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-137">For peer-to-peer transactional replication, they must be managed manually.</span></span> <span data-ttu-id="7ca5e-138">有关详细信息，请参阅[复制标识列](publish/replicate-identity-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-138">For more information, see [Replicate Identity Columns](publish/replicate-identity-columns.md).</span></span>  
  
-   <span data-ttu-id="7ca5e-139">此错误在系统表 **MSmerge_contents**中进行插入时发生。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-139">The error occurs during an insert into the system table **MSmerge_contents**.</span></span>  
  
     <span data-ttu-id="7ca5e-140">发生此错误的原因是联接筛选器属性 **join_unique_key**的值不正确。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-140">This error can occur because of an incorrect value for the join filter property **join_unique_key**.</span></span> <span data-ttu-id="7ca5e-141">仅当父表中的联接列唯一时，才应将此属性设置为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-141">This property should be set to TRUE only if the joined column in the parent table is unique.</span></span> <span data-ttu-id="7ca5e-142">如果此属性设置为 TRUE，而该列不唯一，则引发此错误。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-142">If the property is set to TRUE, but the column is not unique, this error is raised.</span></span> <span data-ttu-id="7ca5e-143">有关设置此属性的详细信息，请参阅 [定义和修改合并项目间的联接筛选器](publish/define-and-modify-a-join-filter-between-merge-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="7ca5e-143">For more information on setting this property, see [Define and Modify a Join Filter Between Merge Articles](publish/define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca5e-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ca5e-144">See Also</span></span>  
 [<span data-ttu-id="7ca5e-145">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="7ca5e-145">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
