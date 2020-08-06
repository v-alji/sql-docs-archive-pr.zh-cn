---
title: 关于更改跟踪 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data changes [SQL Server]
- tracking data changes [SQL Server]
- change tracking [SQL Server], about change tracking
- change tracking [SQL Server]
- data [SQL Server], changing
ms.assetid: 5e0ef05a-8317-4c98-be20-b19d4cd78f12
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e8a817421aeca7906d31e4a70c25a12b6af7c0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588392"
---
# <a name="about-change-tracking-sql-server"></a><span data-ttu-id="1d5c1-102">关于更改跟踪 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1d5c1-102">About Change Tracking (SQL Server)</span></span>
  <span data-ttu-id="1d5c1-103">更改跟踪是一种轻量型解决方案，它为应用程序提供了一种有效的更改跟踪机制。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-103">Change tracking is a lightweight solution that provides an efficient change tracking mechanism for applications.</span></span> <span data-ttu-id="1d5c1-104">通常，若要使应用程序能够查询对数据库中的数据所做的更改和访问与这些更改相关的信息，应用程序开发人员必须实现自定义更改跟踪机制。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-104">Typically, to enable applications to query for changes to data in a database and access information that is related to the changes, application developers had to implement custom change tracking mechanisms.</span></span> <span data-ttu-id="1d5c1-105">创建这些机制通常涉及到许多工作，并经常涉及使用触发器、 `timestamp` 列、用于存储跟踪信息的新表和自定义清理过程的组合。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-105">Creating these mechanisms usually involved a lot of work and frequently involved using a combination of triggers, `timestamp` columns, new tables to store tracking information, and custom cleanup processes.</span></span>  
  
 <span data-ttu-id="1d5c1-106">不同类型的应用程序对其所需的有关更改的信息量有不同的要求。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-106">Different types of applications have different requirements for how much information they need about the changes.</span></span> <span data-ttu-id="1d5c1-107">应用程序可以使用更改跟踪来回答以下有关对用户表所做更改的问题：</span><span class="sxs-lookup"><span data-stu-id="1d5c1-107">Applications can use change tracking to answer the following questions about the changes that have been made to a user table:</span></span>  
  
-   <span data-ttu-id="1d5c1-108">用户表中有哪些行发生了更改？</span><span class="sxs-lookup"><span data-stu-id="1d5c1-108">What rows have changed for a user table?</span></span>  
  
    -   <span data-ttu-id="1d5c1-109">所需的只是行已更改的事实，而不是行更改的次数或任何中间更改的值。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-109">Only the fact that a row has changed is required, not how many times the row has changed or the values of any intermediate changes.</span></span>  
  
    -   <span data-ttu-id="1d5c1-110">可以从所跟踪的表中直接获取最新的数据。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-110">The latest data can be obtained directly from the table that is being tracked.</span></span>  
  
-   <span data-ttu-id="1d5c1-111">某行是否已更改？</span><span class="sxs-lookup"><span data-stu-id="1d5c1-111">Has a row changed?</span></span>  
  
    -   <span data-ttu-id="1d5c1-112">当在同一事务中进行更改时，必须提供并记录行已更改的事实以及有关这一更改的信息。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-112">The fact that a row has changed and information about the change must be available and recorded at the time that the change was made in the same transaction.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d5c1-113">如果应用程序需要有关所有所做更改的信息以及所更改数据的中间值，则可能适合使用变更数据捕获，而不适合使用更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-113">If an application requires information about all the changes that were made and the intermediate values of the changed data, using change data capture, instead of change tracking, might be appropriate.</span></span> <span data-ttu-id="1d5c1-114">有关详细信息，请参阅[关于变更数据捕获 (SQL Server)](../track-changes/about-change-data-capture-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-114">For more information, see [About Change Data Capture &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md).</span></span>  
  
## <a name="one-way-and-two-way-synchronization-applications"></a><span data-ttu-id="1d5c1-115">单向和双向同步应用程序</span><span class="sxs-lookup"><span data-stu-id="1d5c1-115">One-Way and Two-Way Synchronization Applications</span></span>  
 <span data-ttu-id="1d5c1-116">需要将数据与 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例同步的应用程序必须能够查询更改。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-116">Applications that have to synchronize data with an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] must be able to query for changes.</span></span> <span data-ttu-id="1d5c1-117">更改跟踪可用作单向和双向同步应用程序的基础。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-117">Change tracking can be used as a foundation for both one-way and two-way synchronization applications.</span></span>  
  
### <a name="one-way-synchronization-applications"></a><span data-ttu-id="1d5c1-118">单向同步应用程序</span><span class="sxs-lookup"><span data-stu-id="1d5c1-118">One-Way Synchronization Applications</span></span>  
 <span data-ttu-id="1d5c1-119">可以生成使用更改跟踪的单向同步应用程序，如客户端或中间层缓存应用程序。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-119">One-way synchronization applications, such as a client or mid-tier caching application, can be built that use change tracking.</span></span> <span data-ttu-id="1d5c1-120">如下图所示，缓存应用程序要求在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中存储数据并在其他数据存储区中缓存数据。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-120">As shown in the following illustration, a caching application requires data to be stored in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and to be cached in other data stores.</span></span> <span data-ttu-id="1d5c1-121">应用程序必须能够使用对数据库表所做的任何更改来使缓存保持最新。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-121">The application must be able to keep the cache up-to-date with any changes that have been made to the database tables.</span></span> <span data-ttu-id="1d5c1-122">没有要传回到的 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的更改。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-122">There are no changes to pass back to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="1d5c1-123">![显示单向同步应用程序](../../database-engine/media/one-waysync.gif "显示单向同步应用程序")</span><span class="sxs-lookup"><span data-stu-id="1d5c1-123">![Shows one-way synchronization applications](../../database-engine/media/one-waysync.gif "Shows one-way synchronization applications")</span></span>  
  
### <a name="two-way-synchronization-applications"></a><span data-ttu-id="1d5c1-124">双向同步应用程序</span><span class="sxs-lookup"><span data-stu-id="1d5c1-124">Two-Way Synchronization Applications</span></span>  
 <span data-ttu-id="1d5c1-125">也可以生成使用更改跟踪的双向同步应用程序。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-125">Two-way synchronization applications can also be built that use change tracking.</span></span> <span data-ttu-id="1d5c1-126">在此方案中， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例中的数据与一个或多个数据存储区同步。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-126">In this scenario, the data in an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is synchronized with one or more data stores.</span></span> <span data-ttu-id="1d5c1-127">可以更新这些存储区中的数据，并且这些更改必须再同步到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-127">The data in those stores can be updated and the changes must be synchronized back to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="1d5c1-128">![显示双向同步应用程序](../../database-engine/media/two-waysync.gif "显示双向同步应用程序")</span><span class="sxs-lookup"><span data-stu-id="1d5c1-128">![Shows two-way synchronization applications](../../database-engine/media/two-waysync.gif "Shows two-way synchronization applications")</span></span>  
  
 <span data-ttu-id="1d5c1-129">偶尔连接的应用程序就是双向同步应用程序的一个很好的示例。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-129">A good example of two-way synchronization application is an occasionally connected application.</span></span> <span data-ttu-id="1d5c1-130">在这种类型的应用程序中，客户端应用程序查询并更新本地存储区。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-130">In this type of application, a client application queries and updates a local store.</span></span> <span data-ttu-id="1d5c1-131">当客户端与服务器之间存在连接时，应用程序会与服务器同步，并更改两个方向的数据流。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-131">When a connection is available between a client and server, the application will synchronize with a server, and changed data flows in both directions.</span></span>  
  
 <span data-ttu-id="1d5c1-132">双向同步应用程序必须能够检测冲突。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-132">The two-way synchronization applications must be able to detect conflicts.</span></span> <span data-ttu-id="1d5c1-133">如果在两次同步之间的时间两个数据存储区中的相同数据发生了更改，则会出现冲突。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-133">A conflict would occur if the same data was changed in both data stores in the time between synchronizations.</span></span> <span data-ttu-id="1d5c1-134">有了检测冲突的功能，应用程序可以确保不会丢失这些更改。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-134">With the ability to detect conflicts, an application can make sure that changes are not lost.</span></span>  
  
## <a name="how-change-tracking-works"></a><span data-ttu-id="1d5c1-135">更改跟踪的工作方式</span><span class="sxs-lookup"><span data-stu-id="1d5c1-135">How Change Tracking Works</span></span>  
 <span data-ttu-id="1d5c1-136">若要配置更改跟踪，可以使用 DDL 语句或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-136">To configure change tracking, you can use DDL statements or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="1d5c1-137">有关详细信息，请参阅 [启用和禁用更改跟踪 (SQL Server)](../track-changes/enable-and-disable-change-tracking-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-137">For more information, see [Enable and Disable Change Tracking &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md).</span></span> <span data-ttu-id="1d5c1-138">若要跟踪更改，必须首先对数据库启用更改跟踪，然后对该数据库内要跟踪的表启用更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-138">To track changes, change tracking must first be enabled for the database and then enabled for the tables that you want to track within that database.</span></span> <span data-ttu-id="1d5c1-139">表定义无需任何更改，也不会创建任何触发器。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-139">The table definition does not have to be changed in any way, and no triggers are created.</span></span>  
  
 <span data-ttu-id="1d5c1-140">为表配置了更改跟踪后，任何影响该表中的行的 DML 语句都将导致针对每个有所修改的行的更改跟踪信息被记录下来。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-140">After change tracking is configured for a table, any DML statement that affects rows in the table will cause change tracking information for each modified row to be recorded.</span></span> <span data-ttu-id="1d5c1-141">若要查询已更改的行并获取有关这些更改的信息，可以使用 [更改跟踪功能](/sql/relational-databases/system-functions/change-tracking-functions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-141">To query for the rows that have changed and to obtain information about the changes, you can use [change tracking functions](/sql/relational-databases/system-functions/change-tracking-functions-transact-sql).</span></span>  
  
 <span data-ttu-id="1d5c1-142">主键列值是来自所跟踪的并记录更改信息的表中的唯一信息。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-142">The values of the primary key column is only information from the tracked table that is recorded with the change information.</span></span> <span data-ttu-id="1d5c1-143">这些值用于标识发生更改的行。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-143">These values identify the rows that have been changed.</span></span> <span data-ttu-id="1d5c1-144">要获取这些行的最新数据，应用程序可以使用主键列值联接源表和所跟踪的表。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-144">To obtain the latest data for those rows, an application can use the primary key column values to join the source table with the tracked table.</span></span>  
  
 <span data-ttu-id="1d5c1-145">使用更改跟踪也可以获取与每个行所做更改相关的信息。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-145">Information about the change that was made to each row can also be obtained by using change tracking.</span></span> <span data-ttu-id="1d5c1-146">例如，导致更改（插入、更新或删除）的 DML 操作的类型或作为更新操作的一部分而更改的列。</span><span class="sxs-lookup"><span data-stu-id="1d5c1-146">For example, the type of DML operation that caused the change (insert, update, or delete) or the columns that were changed as part of an update operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d5c1-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d5c1-147">See Also</span></span>  
 <span data-ttu-id="1d5c1-148">[启用和禁用更改跟踪 &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1d5c1-148">[Enable and Disable Change Tracking &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="1d5c1-149">[使用更改跟踪 &#40;SQL Server&#41;](../track-changes/work-with-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1d5c1-149">[Work with Change Tracking &#40;SQL Server&#41;](../track-changes/work-with-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="1d5c1-150">[管理更改跟踪 &#40;SQL Server&#41;](../track-changes/manage-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1d5c1-150">[Manage Change Tracking &#40;SQL Server&#41;](../track-changes/manage-change-tracking-sql-server.md) </span></span>  
 [<span data-ttu-id="1d5c1-151">跟踪数据更改 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1d5c1-151">Track Data Changes &#40;SQL Server&#41;</span></span>](../track-changes/track-data-changes-sql-server.md)  
  
  
