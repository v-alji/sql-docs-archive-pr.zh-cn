---
title: 需要已更新备份的常用操作 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server replication], actions requiring a backup
- restoring [SQL Server replication], actions requiring a backup
- backups [SQL Server replication], actions requiring a backup
ms.assetid: a5975bf4-183e-42e3-b7d1-ad02f89d2e1d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3eb10bdca8ee188f7b322a46665c38129d57052b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687756"
---
# <a name="common-actions-requiring-an-updated-backup"></a><span data-ttu-id="f8e78-102">需要已更新备份的常用操作</span><span class="sxs-lookup"><span data-stu-id="f8e78-102">Common Actions Requiring an Updated Backup</span></span>
  <span data-ttu-id="f8e78-103">如果执行定期日志备份，则在日志备份中应捕获所有与复制相关的更改。</span><span class="sxs-lookup"><span data-stu-id="f8e78-103">If you perform regular log backups, any replication-related changes should be captured in the log backups.</span></span> <span data-ttu-id="f8e78-104">如果不执行日志备份，就要在修改复制架构或拓扑之后，对发布、分发、订阅、 **msdb**数据库和 **master** 数据库执行备份。</span><span class="sxs-lookup"><span data-stu-id="f8e78-104">If you don't perform log backups, perform a backup of the publication, distribution, subscription, **msdb**, and **master** databases after making modifications to your replication schema or topology.</span></span>  
  
## <a name="publication-database"></a><span data-ttu-id="f8e78-105">发布数据库</span><span class="sxs-lookup"><span data-stu-id="f8e78-105">Publication Database</span></span>  
 <span data-ttu-id="f8e78-106">在执行下列操作后备份发布数据库：</span><span class="sxs-lookup"><span data-stu-id="f8e78-106">Backup the publication database after:</span></span>  
  
-   <span data-ttu-id="f8e78-107">创建新发布。</span><span class="sxs-lookup"><span data-stu-id="f8e78-107">Creating new publications.</span></span>  
  
-   <span data-ttu-id="f8e78-108">更改包括筛选在内的任何发布属性。</span><span class="sxs-lookup"><span data-stu-id="f8e78-108">Changing any publication property, including filtering.</span></span>  
  
-   <span data-ttu-id="f8e78-109">向现有发布中添加项目。</span><span class="sxs-lookup"><span data-stu-id="f8e78-109">Adding articles to an existing publication.</span></span>  
  
-   <span data-ttu-id="f8e78-110">在发布范围内重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="f8e78-110">Performing a publication-wide reinitialization of subscriptions.</span></span>  
  
-   <span data-ttu-id="f8e78-111">对已发布的表进行架构更改。</span><span class="sxs-lookup"><span data-stu-id="f8e78-111">Making a schema change on a published table.</span></span>  
  
-   <span data-ttu-id="f8e78-112">使用 [sp_addscriptexec (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql) 按需执行脚本。</span><span class="sxs-lookup"><span data-stu-id="f8e78-112">Performing on-demand script execution with [sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql).</span></span>  
  
-   <span data-ttu-id="f8e78-113">更改任何项目属性。</span><span class="sxs-lookup"><span data-stu-id="f8e78-113">Changing any article property.</span></span>  
  
-   <span data-ttu-id="f8e78-114">删除任何发布。</span><span class="sxs-lookup"><span data-stu-id="f8e78-114">Dropping any publications.</span></span>  
  
-   <span data-ttu-id="f8e78-115">删除任何项目。</span><span class="sxs-lookup"><span data-stu-id="f8e78-115">Dropping any articles.</span></span>  
  
-   <span data-ttu-id="f8e78-116">禁用复制。</span><span class="sxs-lookup"><span data-stu-id="f8e78-116">Disabling replication.</span></span>  
  
## <a name="distribution-database"></a><span data-ttu-id="f8e78-117">分发数据库</span><span class="sxs-lookup"><span data-stu-id="f8e78-117">Distribution Database</span></span>  
 <span data-ttu-id="f8e78-118">在执行下列操作后备份分发数据库：</span><span class="sxs-lookup"><span data-stu-id="f8e78-118">Backup the distribution database after:</span></span>  
  
-   <span data-ttu-id="f8e78-119">创建或修改复制代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="f8e78-119">Creating or modifying replication agent profiles.</span></span>  
  
-   <span data-ttu-id="f8e78-120">修改复制代理配置文件参数。</span><span class="sxs-lookup"><span data-stu-id="f8e78-120">Modifying replication agent profile parameters.</span></span>  
  
-   <span data-ttu-id="f8e78-121">更改任何推送订阅的复制代理属性（包括计划）。</span><span class="sxs-lookup"><span data-stu-id="f8e78-121">Changing the replication agent properties (including schedules) for any push subscriptions.</span></span>  
  
-   <span data-ttu-id="f8e78-122">自动标识范围管理功能指定了新标识范围。</span><span class="sxs-lookup"><span data-stu-id="f8e78-122">A new range of identities is assigned by the automatic identity range management feature.</span></span>  
  
## <a name="subscription-database"></a><span data-ttu-id="f8e78-123">订阅数据库</span><span class="sxs-lookup"><span data-stu-id="f8e78-123">Subscription Database</span></span>  
 <span data-ttu-id="f8e78-124">在执行下列操作后备份订阅数据库：</span><span class="sxs-lookup"><span data-stu-id="f8e78-124">Backup the subscription database after:</span></span>  
  
-   <span data-ttu-id="f8e78-125">更改任何订阅属性。</span><span class="sxs-lookup"><span data-stu-id="f8e78-125">Changing any subscription property.</span></span>  
  
-   <span data-ttu-id="f8e78-126">在发布服务器上更改合并订阅的优先级。</span><span class="sxs-lookup"><span data-stu-id="f8e78-126">Changing the priority for a merge subscription at the Publisher.</span></span>  
  
-   <span data-ttu-id="f8e78-127">删除任何订阅。</span><span class="sxs-lookup"><span data-stu-id="f8e78-127">Dropping any subscriptions.</span></span>  
  
-   <span data-ttu-id="f8e78-128">禁用复制。</span><span class="sxs-lookup"><span data-stu-id="f8e78-128">Disabling replication.</span></span>  
  
## <a name="msdb-database"></a><span data-ttu-id="f8e78-129">msdb 数据库</span><span class="sxs-lookup"><span data-stu-id="f8e78-129">msdb Database</span></span>  
 <span data-ttu-id="f8e78-130">在执行下列操作后，在相应节点备份 **msdb** 系统数据库：</span><span class="sxs-lookup"><span data-stu-id="f8e78-130">Backup the **msdb** system database at the appropriate node after:</span></span>  
  
-   <span data-ttu-id="f8e78-131">启用或禁用复制。</span><span class="sxs-lookup"><span data-stu-id="f8e78-131">Enabling or disabling replication.</span></span>  
  
-   <span data-ttu-id="f8e78-132">添加或删除分发数据库（在分发服务器上）。</span><span class="sxs-lookup"><span data-stu-id="f8e78-132">Adding or dropping a distribution database (at the Distributor).</span></span>  
  
-   <span data-ttu-id="f8e78-133">启用或禁用发布数据库（在发布服务器上）。</span><span class="sxs-lookup"><span data-stu-id="f8e78-133">Enabling or disabling a database for publishing (at the Publisher).</span></span>  
  
-   <span data-ttu-id="f8e78-134">创建或修改复制代理配置文件（在分发服务器上）。</span><span class="sxs-lookup"><span data-stu-id="f8e78-134">Creating or modifying replication agent profiles (at the Distributor).</span></span>  
  
-   <span data-ttu-id="f8e78-135">修改任何复制代理配置文件参数（在分发服务器上）。</span><span class="sxs-lookup"><span data-stu-id="f8e78-135">Modifying any replication agent profile parameters (at the Distributor).</span></span>  
  
-   <span data-ttu-id="f8e78-136">更改任何推送订阅的复制代理程序属性（包括计划）（在分发服务器上）。</span><span class="sxs-lookup"><span data-stu-id="f8e78-136">Changing the replication agent properties (including schedules) for any push subscriptions (at the Distributor).</span></span>  
  
-   <span data-ttu-id="f8e78-137">更改任何请求订阅的复制代理程序属性（包括计划）（在订阅服务器上）。</span><span class="sxs-lookup"><span data-stu-id="f8e78-137">Changing the replication agent properties (including schedules) for any pull subscriptions (at the Subscriber).</span></span>  
  
-   <span data-ttu-id="f8e78-138">创建与使用可转换订阅的事务发布相关联的 DTS 包（在分发服务器和订阅服务器上）。</span><span class="sxs-lookup"><span data-stu-id="f8e78-138">Creating a DTS package associated with a transactional publication that uses transformable subscriptions (at the Distributor and Subscriber).</span></span>  
  
-   <span data-ttu-id="f8e78-139">添加或删除可转换订阅（在分发服务器和订阅服务器上）。</span><span class="sxs-lookup"><span data-stu-id="f8e78-139">Adding or dropping a transformable subscription (at the Distributor and Subscriber).</span></span>  
  
## <a name="master-database"></a><span data-ttu-id="f8e78-140">master 数据库</span><span class="sxs-lookup"><span data-stu-id="f8e78-140">master Database</span></span>  
 <span data-ttu-id="f8e78-141">在执行下列操作后，在相应节点备份 **master** 系统数据库：</span><span class="sxs-lookup"><span data-stu-id="f8e78-141">Backup the **master** system database at the appropriate node after:</span></span>  
  
-   <span data-ttu-id="f8e78-142">启用或禁用复制。</span><span class="sxs-lookup"><span data-stu-id="f8e78-142">Enabling or disabling replication.</span></span>  
  
-   <span data-ttu-id="f8e78-143">添加或删除分发数据库（在分发服务器上）。</span><span class="sxs-lookup"><span data-stu-id="f8e78-143">Adding or dropping a distribution database (at the Distributor).</span></span>  
  
-   <span data-ttu-id="f8e78-144">启用或禁用发布数据库（在发布服务器上）。</span><span class="sxs-lookup"><span data-stu-id="f8e78-144">Enabling or disabling a database for publishing (at the Publisher).</span></span>  
  
-   <span data-ttu-id="f8e78-145">在任何数据库中添加第一个发布或删除最后一个发布（在发布服务器上）。</span><span class="sxs-lookup"><span data-stu-id="f8e78-145">Adding the first or dropping the last publication in any database (at the Publisher).</span></span>  
  
-   <span data-ttu-id="f8e78-146">在任何数据库中添加第一个订阅或删除最后一个订阅（在订阅服务器上）。</span><span class="sxs-lookup"><span data-stu-id="f8e78-146">Adding the first or dropping the last subscription in any database (at the Subscriber).</span></span>  
  
-   <span data-ttu-id="f8e78-147">在分发发布服务器上启用或禁用发布服务器（在发布服务器和分发服务器上）。</span><span class="sxs-lookup"><span data-stu-id="f8e78-147">Enabling or disabling a Publisher at a Distribution Publisher (at the Publisher and Distributor).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8e78-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8e78-148">See Also</span></span>  
 <span data-ttu-id="f8e78-149">[SQL Server 数据库的备份和还原](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="f8e78-149">[Back Up and Restore of SQL Server Databases](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="f8e78-150">备份和还原复制的数据库</span><span class="sxs-lookup"><span data-stu-id="f8e78-150">Back Up and Restore Replicated Databases</span></span>](back-up-and-restore-replicated-databases.md)  
  
  
