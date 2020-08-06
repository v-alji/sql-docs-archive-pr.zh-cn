---
title: 配置分发 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], distribution
- distribution configuration [SQL Server replication]
- remote Distributors [SQL Server replication]
- transactional replication, configuring distribution
- distribution databases [SQL Server replication], sizing
- Distributors [SQL Server replication], configuring
- distribution databases [SQL Server replication], about distribution databases
- distribution databases [SQL Server replication]
- merge replication [SQL Server replication], configuring distribution
ms.assetid: 94d52169-384e-4885-84eb-2304e967d9f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0378fe285ba57e1420b7e6bebf5e2e6fe13d29e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580137"
---
# <a name="configure-distribution"></a><span data-ttu-id="fcd0a-102">配置分发</span><span class="sxs-lookup"><span data-stu-id="fcd0a-102">Configure Distribution</span></span>
  <span data-ttu-id="fcd0a-103">分发服务器是指包含分发数据库的服务器，其中存储所有类型复制的元数据和历史记录数据以及事务复制的事务。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-103">The Distributor is a server that contains the distribution database, which stores metadata and history data for all types of replication and transactions for transactional replication.</span></span> <span data-ttu-id="fcd0a-104">若要建立复制，必须配置分发服务器。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-104">To set up replication, you must configure a Distributor.</span></span> <span data-ttu-id="fcd0a-105">只能为每台发布服务器分配一个分发服务器实例，但是多台发布服务器可共享一台分发服务器。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-105">Each Publisher can be assigned to only a single Distributor instance, but multiple publishers can share a Distributor.</span></span> <span data-ttu-id="fcd0a-106">分发服务器在其所在服务器上使用以下附加资源：</span><span class="sxs-lookup"><span data-stu-id="fcd0a-106">The Distributor uses these additional resources on the server where it is located:</span></span>  
  
-   <span data-ttu-id="fcd0a-107">额外的磁盘空间，如果发布的快照文件存储在分发服务器上（通常如此）。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-107">Additional disk space if the snapshot files for the publication are stored on the Distributor (which they typically are).</span></span>  
  
-   <span data-ttu-id="fcd0a-108">存储分发数据库所需的附加磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-108">Additional disk space to store the distribution database.</span></span>  
  
-   <span data-ttu-id="fcd0a-109">运行于分发服务器上的复制代理执行推送订阅所需的附加处理器资源。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-109">Additional processor usage by replication agents for push subscriptions running on the Distributor.</span></span>  
  
 <span data-ttu-id="fcd0a-110">选作分发服务器的服务器应有足够的磁盘空间和处理器运算能力，以支持该服务器上的复制和任何其他活动。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-110">The server you select as the Distributor should have adequate disk space and processor power to support replication and any other activities on that server.</span></span> <span data-ttu-id="fcd0a-111">配置分发服务器时，需指定下列内容：</span><span class="sxs-lookup"><span data-stu-id="fcd0a-111">When you configure the Distributor, you specify the following:</span></span>  
  
-   <span data-ttu-id="fcd0a-112">快照文件夹，默认情况下供使用此分发服务器的所有发布服务器使用。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-112">A snapshot folder, which is used, by default, for all Publishers that use this Distributor.</span></span> <span data-ttu-id="fcd0a-113">请确保此文件夹已共享并设置了适当的权限。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-113">Ensure that this folder is already shared and has the appropriate permissions set.</span></span> <span data-ttu-id="fcd0a-114">有关详细信息，请参阅[保护快照文件夹](security/secure-the-snapshot-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-114">For more information, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span>  
  
-   <span data-ttu-id="fcd0a-115">分发数据库的名称和文件位置。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-115">A name and file locations for the distribution database.</span></span> <span data-ttu-id="fcd0a-116">分发数据库创建后不能重命名。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-116">The distribution database cannot be renamed after it is created.</span></span> <span data-ttu-id="fcd0a-117">若要对数据库使用其他名称，必须禁用并重新配置分发。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-117">To use a different name for the database, you must disable distribution and reconfigure it.</span></span>  
  
-   <span data-ttu-id="fcd0a-118">获得授权使用分发服务器的发布服务器。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-118">Any Publishers authorized to use the Distributor.</span></span> <span data-ttu-id="fcd0a-119">如果要指定分发服务器而非发布服务器运行实例，还必须指定发布服务器连接到远程分发服务器所用密码。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-119">If you specify Publishers other than the instance on which the Distributor runs, you must also specify a password for the connections the Publishers make to the remote Distributor.</span></span>  
  
 <span data-ttu-id="fcd0a-120">对于事务复制，配置分发后，建议您：</span><span class="sxs-lookup"><span data-stu-id="fcd0a-120">For transactional replication, after you configure distribution, we recommend that you:</span></span>  
  
-   <span data-ttu-id="fcd0a-121">适当调整分发数据库的大小。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-121">Size the distribution database appropriately.</span></span> <span data-ttu-id="fcd0a-122">在系统承受典型负载的情况下对复制进行测试，以确定存储命令需要多少空间。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-122">Test replication with a typical load for your system to determine how much space is required to store commands.</span></span> <span data-ttu-id="fcd0a-123">确保数据库足以存储命令，而无需频繁地自动增大。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-123">Ensure the database is large enough to store commands without having to auto-grow frequently.</span></span> <span data-ttu-id="fcd0a-124">有关更改数据库大小的详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-124">For more information about changing the size of a database, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="fcd0a-125">针对分发数据库设置 **sync with backup** 选项。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-125">Set the **sync with backup** option on the distribution database.</span></span> <span data-ttu-id="fcd0a-126">有关详细信息，请参阅[快照复制和事务复制的备份和还原策略](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)和[为事务复制启用协调备份（复制 Transact-SQL 编程）](administration/enable-coordinated-backups-for-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-126">For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) and [Enable Coordinated Backups for Transactional Replication &#40;Replication Transact-SQL Programming&#41;](administration/enable-coordinated-backups-for-transactional-replication.md).</span></span>  
  
## <a name="local-and-remote-distributors"></a><span data-ttu-id="fcd0a-127">本地分发服务器和远程分发服务器</span><span class="sxs-lookup"><span data-stu-id="fcd0a-127">Local and Remote Distributors</span></span>  
 <span data-ttu-id="fcd0a-128">默认情况下，分发服务器与发布服务器是同一台服务器（本地分发服务器），但也可以是与发布服务器不同的服务器（远程分发服务器）。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-128">By default, the Distributor is the same server as the Publisher (a local Distributor), but it can also be a separate server from the Publisher (a remote Distributor).</span></span> <span data-ttu-id="fcd0a-129">通常，在下列情况下，要选用远程分发服务器：</span><span class="sxs-lookup"><span data-stu-id="fcd0a-129">Typically, you would choose to use a remote Distributor if you want to:</span></span>  
  
-   <span data-ttu-id="fcd0a-130">希望复制对发布服务器的影响降低到最小（例如，如果发布服务器是一台 OLTP 服务器），将处理卸载到另一台计算机上。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-130">Offload processing to another computer if you want minimal impact from replication on the Publisher (for example, if the Publisher is an OLTP server).</span></span>  
  
-   <span data-ttu-id="fcd0a-131">为多台发布服务器配置一台集中的分发服务器。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-131">Configure a centralized Distributor for multiple Publishers.</span></span>  
  
 <span data-ttu-id="fcd0a-132">与合并复制相比，远程分发服务器较常用于事务复制中，原因有二：</span><span class="sxs-lookup"><span data-stu-id="fcd0a-132">Remote Distributors are more common in transactional replication than they are in merge replication for two reasons:</span></span>  
  
-   <span data-ttu-id="fcd0a-133">分发服务器在事务复制中发挥着更大的作用，因为所有复制的事务都要写入分发数据库中并从中读取。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-133">The Distributor plays a larger role in transactional replication because all replicated transactions are written to and read from the distribution database.</span></span>  
  
-   <span data-ttu-id="fcd0a-134">合并复制拓扑通常使用请求订阅，因此代理在每台订阅服务器上运行，而不是所有代理都在分发服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-134">Merge replication topologies typically use pull subscriptions, so agents run at each Subscriber, rather than all running at the Distributor.</span></span> <span data-ttu-id="fcd0a-135">有关详细信息，请参阅[订阅发布](subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-135">For more information, see [Subscribe to Publications](subscribe-to-publications.md).</span></span> <span data-ttu-id="fcd0a-136">在大多数情况下，应为将本地分发服务器用于合并复制。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-136">In most cases, you should use a local Distributor for merge replication.</span></span>  
  
 <span data-ttu-id="fcd0a-137">若要配置发布和分发，请参阅 [Configure Publishing and Distribution](configure-publishing-and-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-137">To configure publishing and distribution, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md).</span></span>  
  
 <span data-ttu-id="fcd0a-138">若要修改发布服务器和分发服务器属性，请参阅 [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="fcd0a-138">To modify Publisher and Distributor properties, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcd0a-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fcd0a-139">See Also</span></span>  
 <span data-ttu-id="fcd0a-140">[发布数据和数据库对象](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="fcd0a-140">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="fcd0a-141">保护分发服务器</span><span class="sxs-lookup"><span data-stu-id="fcd0a-141">Secure the Distributor</span></span>](security/secure-the-distributor.md)  
  
  
