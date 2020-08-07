---
title: Oracle 发布服务器的管理注意事项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], administrative considerations
- administering replication, Oracle publishing
ms.assetid: cfd81fb5-419b-4a1b-97c4-be7c9d4ee289
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3104b507987a4a236d39dd0ae1f8e3c29358c730
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588978"
---
# <a name="administrative-considerations-for-oracle-publishers"></a><span data-ttu-id="4c951-102">Oracle 发布服务器的管理注意事项</span><span class="sxs-lookup"><span data-stu-id="4c951-102">Administrative Considerations for Oracle Publishers</span></span>
  <span data-ttu-id="4c951-103">在配置 Oracle 发布服务器并实施复制更改跟踪机制后，Oracle 数据库系统管理员仍然可以使用标准 Oracle 数据库实用工具并执行典型的系统管理任务。</span><span class="sxs-lookup"><span data-stu-id="4c951-103">After an Oracle Publisher is configured and the replication change tracking mechanisms are in place, administrators of the Oracle database system can still use standard Oracle database utilities and perform typical system administration tasks.</span></span> <span data-ttu-id="4c951-104">但是，应该了解执行某些管理任务对已发布数据的影响。</span><span class="sxs-lookup"><span data-stu-id="4c951-104">However, you should be aware of the effects on the published data of performing certain administrative tasks.</span></span>  
  
 <span data-ttu-id="4c951-105">除了删除或修改为复制发布的列或者任意复制对象，这些注意事项不适用于快照发布。</span><span class="sxs-lookup"><span data-stu-id="4c951-105">With the exception of dropping or modifying a column that is published for replication, or dropping or modifying any replication objects, these considerations do not apply to snapshot publications.</span></span>  
  
## <a name="importing-and-loading-data"></a><span data-ttu-id="4c951-106">导入和加载数据</span><span class="sxs-lookup"><span data-stu-id="4c951-106">Importing and loading data</span></span>  
 <span data-ttu-id="4c951-107">触发器用于 Oracle 中的事务发布的更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="4c951-107">Triggers are used in change tracking for transactional publications on Oracle.</span></span> <span data-ttu-id="4c951-108">对已发布表的更改只有在发生更新、插入或删除时复制触发器激发的情况下才能复制到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="4c951-108">Changes to published tables can be replicated to Subscribers only if the replication triggers fire when an update, insert, or delete occurs.</span></span> <span data-ttu-id="4c951-109">Oracle 导入和 SQL\*Loader 这两个 Oracle 实用工具都有影响触发器的选项，用来决定当用这些实用工具将行插入到复制的表中时是否激发触发器。</span><span class="sxs-lookup"><span data-stu-id="4c951-109">The Oracle utilities Oracle Import and SQL\*Loader both have options that affect whether triggers will fire when rows are inserted into replicated tables with these utilities.</span></span>  
  
### <a name="oracle-import"></a><span data-ttu-id="4c951-110">Oracle 导入</span><span class="sxs-lookup"><span data-stu-id="4c951-110">Oracle Import</span></span>  
 <span data-ttu-id="4c951-111">用 Oracle 导入，可以将 **ignore** 选项设置为“y”或“n”（默认值为“n”）。</span><span class="sxs-lookup"><span data-stu-id="4c951-111">With Oracle Import, you can set the option **ignore** to 'y' or 'n' (the default is 'n').</span></span> <span data-ttu-id="4c951-112">如果将 **ignore** 设置为“n”，表会删除并在导入过程中重新创建。</span><span class="sxs-lookup"><span data-stu-id="4c951-112">If **ignore** is set to 'n', the table is dropped and re-created during import.</span></span> <span data-ttu-id="4c951-113">这会删除复制触发器并禁用复制。</span><span class="sxs-lookup"><span data-stu-id="4c951-113">This removes replication triggers and disables replication.</span></span> <span data-ttu-id="4c951-114">如果将 **ignore** 设置为“y”，导入将尝试将行加载到现有表中，这会激发复制触发器。</span><span class="sxs-lookup"><span data-stu-id="4c951-114">If **ignore** is set to 'y', import will attempt to load the rows into the existing table, which fires the replication triggers.</span></span> <span data-ttu-id="4c951-115">因此，用导入工具向复制的表导入时，确保将 **ignore** 设置为“y”。</span><span class="sxs-lookup"><span data-stu-id="4c951-115">Therefore, ensure **ignore** is set to 'y' when importing into a replicated table with the Import tool.</span></span>  
  
### <a name="sqlloader"></a><span data-ttu-id="4c951-116">SQL\*Loader</span><span class="sxs-lookup"><span data-stu-id="4c951-116">SQL\*Loader</span></span>  
 <span data-ttu-id="4c951-117">使用 SQL\*Loader，可以将选项 **direct** 设置为“true”或“false”（默认值为“false”）。</span><span class="sxs-lookup"><span data-stu-id="4c951-117">With SQL\*Loader, you can set the option **direct** to 'true' or 'false' (the default is 'false').</span></span> <span data-ttu-id="4c951-118">如果将 **direct** 设置为“false”，则用常规 INSERT 语句插入行，这些语句会激发复制触发器。</span><span class="sxs-lookup"><span data-stu-id="4c951-118">If **direct** is set to 'false', rows are inserted using conventional INSERT statements, which fire replication triggers.</span></span> <span data-ttu-id="4c951-119">如果将 **direct** 设置为“true”，则优化加载而不激发触发器。</span><span class="sxs-lookup"><span data-stu-id="4c951-119">If **direct** is set to 'true', the load is optimized, and triggers are not fired.</span></span> <span data-ttu-id="4c951-120">因此，使用 SQL\*Loader 工具向复制的表导入时，请确保将 **direct** 设置为“false”。</span><span class="sxs-lookup"><span data-stu-id="4c951-120">Therefore, ensure **direct** is set to 'false' when loading into a replicated table with the SQL\*Loader tool.</span></span>  
  
## <a name="making-changes-to-published-objects"></a><span data-ttu-id="4c951-121">对已发布的对象进行更改</span><span class="sxs-lookup"><span data-stu-id="4c951-121">Making changes to published objects</span></span>  
 <span data-ttu-id="4c951-122">下列操作没有特别的注意事项：</span><span class="sxs-lookup"><span data-stu-id="4c951-122">The following actions require no special considerations:</span></span>  
  
-   <span data-ttu-id="4c951-123">重新生成对已发布表的索引。</span><span class="sxs-lookup"><span data-stu-id="4c951-123">Rebuilding indexes on published tables.</span></span>  
  
-   <span data-ttu-id="4c951-124">将用户触发器添加到已发布表。</span><span class="sxs-lookup"><span data-stu-id="4c951-124">Adding user triggers to a published table.</span></span>  
  
 <span data-ttu-id="4c951-125">下列操作需要停止已发布表上的所有活动：</span><span class="sxs-lookup"><span data-stu-id="4c951-125">The following action requires you to stop all activity on the published tables:</span></span>  
  
-   <span data-ttu-id="4c951-126">移动已发布表。</span><span class="sxs-lookup"><span data-stu-id="4c951-126">Moving a published table.</span></span>  
  
 <span data-ttu-id="4c951-127">下列操作要求删除发布、执行操作，然后重新创建发布：</span><span class="sxs-lookup"><span data-stu-id="4c951-127">The following actions require you to drop the publication, perform the operation, and then recreate the publication:</span></span>  
  
-   <span data-ttu-id="4c951-128">截断已发布表。</span><span class="sxs-lookup"><span data-stu-id="4c951-128">Truncating a published table.</span></span>  
  
-   <span data-ttu-id="4c951-129">重命名已发布表。</span><span class="sxs-lookup"><span data-stu-id="4c951-129">Renaming a published table.</span></span>  
  
-   <span data-ttu-id="4c951-130">向已发布表添加列。</span><span class="sxs-lookup"><span data-stu-id="4c951-130">Adding a column to a published table.</span></span>  
  
-   <span data-ttu-id="4c951-131">删除或修改为复制发布的列。</span><span class="sxs-lookup"><span data-stu-id="4c951-131">Dropping or modifying a column that is published for replication.</span></span>  
  
-   <span data-ttu-id="4c951-132">执行日志未记录的操作。</span><span class="sxs-lookup"><span data-stu-id="4c951-132">Performing non-logged operations.</span></span>  
  
## <a name="dropping-or-modifying-replication-objects"></a><span data-ttu-id="4c951-133">删除或修改复制对象</span><span class="sxs-lookup"><span data-stu-id="4c951-133">Dropping or modifying replication objects</span></span>  
 <span data-ttu-id="4c951-134">如果删除或修改了任何发布服务器级的跟踪表、触发器、序列或存储过程，必须删除并重新配置发布服务器。</span><span class="sxs-lookup"><span data-stu-id="4c951-134">You must drop and reconfigure the Publisher if you drop or modify any Publisher level tracking tables, triggers, sequences, or stored procedures.</span></span> <span data-ttu-id="4c951-135">有关这些对象的部分列表，请参阅[在 Oracle 发布服务器上创建的对象](objects-created-on-the-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="4c951-135">For a partial list of these objects, see [Objects Created on the Oracle Publisher](objects-created-on-the-oracle-publisher.md).</span></span>  
  
 <span data-ttu-id="4c951-136">有关删除和重新配置发布服务器的信息，请参阅主题 [Troubleshooting Oracle Publishers](troubleshooting-oracle-publishers.md)中的“进行需要重新配置发布服务器的更改”部分。</span><span class="sxs-lookup"><span data-stu-id="4c951-136">For information about dropping and reconfiguring the Publisher, see the section "Changes are made that require reconfiguration of the Publisher" in the topic [Troubleshooting Oracle Publishers](troubleshooting-oracle-publishers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c951-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4c951-137">See Also</span></span>  
 <span data-ttu-id="4c951-138">[配置 Oracle 发布服务器](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="4c951-138">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="4c951-139">[Oracle 发布服务器的设计注意事项和限制](design-considerations-and-limitations-for-oracle-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="4c951-139">[Design Considerations and Limitations for Oracle Publishers](design-considerations-and-limitations-for-oracle-publishers.md) </span></span>  
 [<span data-ttu-id="4c951-140">Oracle 发布概述</span><span class="sxs-lookup"><span data-stu-id="4c951-140">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
