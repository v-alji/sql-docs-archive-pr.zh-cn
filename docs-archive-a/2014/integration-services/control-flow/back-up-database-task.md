---
title: “备份数据库”任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.backupdatabasetask.f1
helpviewer_keywords:
- database backups [Integration Services]
- Back Up Database task [Integration Services]
- backing up databases [Integration Services]
- transaction log backups [Integration Services]
- backing up transaction logs [Integration Services]
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b0980d89cc915121414dd7d3c89be6f4d72eb715
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579698"
---
# <a name="back-up-database-task"></a><span data-ttu-id="e2ee3-102">“备份数据库”任务</span><span class="sxs-lookup"><span data-stu-id="e2ee3-102">Back Up Database Task</span></span>
  <span data-ttu-id="e2ee3-103">“备份数据库”任务可执行不同类型的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库备份。</span><span class="sxs-lookup"><span data-stu-id="e2ee3-103">The Back Up Database task performs different types of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database backups.</span></span> <span data-ttu-id="e2ee3-104">有关详细信息，请参阅 [SQL Server 数据库的备份和还原](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="e2ee3-104">For more information, see [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
 <span data-ttu-id="e2ee3-105">通过使用“备份数据库”任务，包可以备份单个数据库或多个数据库。</span><span class="sxs-lookup"><span data-stu-id="e2ee3-105">By using the Back Up Database task, a package can back up a single database or multiple databases.</span></span> <span data-ttu-id="e2ee3-106">如果此任务仅备份单个数据库，则可以选择备份组件：数据库或者其文件和文件组。</span><span class="sxs-lookup"><span data-stu-id="e2ee3-106">If the task backs up only a single database, you can choose the backup component: the database, or its files and filegroups.</span></span>  
  
## <a name="supported-recover-models-and-backup-types"></a><span data-ttu-id="e2ee3-107">支持的恢复模式和备份类型</span><span class="sxs-lookup"><span data-stu-id="e2ee3-107">Supported Recover Models and Backup Types</span></span>  
 <span data-ttu-id="e2ee3-108">下表列出了“备份数据库”任务支持的恢复模式和备份类型。</span><span class="sxs-lookup"><span data-stu-id="e2ee3-108">The following table lists the recovery models and backup types that the Back Up Database task supports.</span></span>  
  
|<span data-ttu-id="e2ee3-109">恢复模式</span><span class="sxs-lookup"><span data-stu-id="e2ee3-109">Recovery model</span></span>|<span data-ttu-id="e2ee3-110">数据库</span><span class="sxs-lookup"><span data-stu-id="e2ee3-110">Database</span></span>|<span data-ttu-id="e2ee3-111">数据库差异</span><span class="sxs-lookup"><span data-stu-id="e2ee3-111">Database differential</span></span>|<span data-ttu-id="e2ee3-112">事务日志</span><span class="sxs-lookup"><span data-stu-id="e2ee3-112">Transaction log</span></span>|<span data-ttu-id="e2ee3-113">文件或文件差异</span><span class="sxs-lookup"><span data-stu-id="e2ee3-113">File or file differential</span></span>|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|<span data-ttu-id="e2ee3-114">简单</span><span class="sxs-lookup"><span data-stu-id="e2ee3-114">Simple</span></span>|<span data-ttu-id="e2ee3-115">必选</span><span class="sxs-lookup"><span data-stu-id="e2ee3-115">Required</span></span>|<span data-ttu-id="e2ee3-116">可选</span><span class="sxs-lookup"><span data-stu-id="e2ee3-116">Optional</span></span>|<span data-ttu-id="e2ee3-117">不支持</span><span class="sxs-lookup"><span data-stu-id="e2ee3-117">Not supported</span></span>|<span data-ttu-id="e2ee3-118">不支持</span><span class="sxs-lookup"><span data-stu-id="e2ee3-118">Not supported</span></span>|  
|<span data-ttu-id="e2ee3-119">完全</span><span class="sxs-lookup"><span data-stu-id="e2ee3-119">Full</span></span>|<span data-ttu-id="e2ee3-120">必选</span><span class="sxs-lookup"><span data-stu-id="e2ee3-120">Required</span></span>|<span data-ttu-id="e2ee3-121">可选</span><span class="sxs-lookup"><span data-stu-id="e2ee3-121">Optional</span></span>|<span data-ttu-id="e2ee3-122">必选</span><span class="sxs-lookup"><span data-stu-id="e2ee3-122">Required</span></span>|<span data-ttu-id="e2ee3-123">可选</span><span class="sxs-lookup"><span data-stu-id="e2ee3-123">Optional</span></span>|  
|<span data-ttu-id="e2ee3-124">大容量日志</span><span class="sxs-lookup"><span data-stu-id="e2ee3-124">Bulk-logged</span></span>|<span data-ttu-id="e2ee3-125">必选</span><span class="sxs-lookup"><span data-stu-id="e2ee3-125">Required</span></span>|<span data-ttu-id="e2ee3-126">可选</span><span class="sxs-lookup"><span data-stu-id="e2ee3-126">Optional</span></span>|<span data-ttu-id="e2ee3-127">必选</span><span class="sxs-lookup"><span data-stu-id="e2ee3-127">Required</span></span>|<span data-ttu-id="e2ee3-128">可选</span><span class="sxs-lookup"><span data-stu-id="e2ee3-128">Optional</span></span>|  
  
 <span data-ttu-id="e2ee3-129">“备份数据库”任务封装 Transact-SQL BACKUP 语句。</span><span class="sxs-lookup"><span data-stu-id="e2ee3-129">The Back Up Database task encapsulates a Transact-SQL BACKUP statement.</span></span> <span data-ttu-id="e2ee3-130">有关详细信息，请参阅 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e2ee3-130">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
## <a name="configuration-of-the-back-up-database-task"></a><span data-ttu-id="e2ee3-131">“备份数据库”任务的配置</span><span class="sxs-lookup"><span data-stu-id="e2ee3-131">Configuration of the Back Up Database Task</span></span>  
 <span data-ttu-id="e2ee3-132">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器来设置属性。</span><span class="sxs-lookup"><span data-stu-id="e2ee3-132">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="e2ee3-133">此任务位于 **设计器中** “工具箱” **的** “维护计划中的任务” [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="e2ee3-133">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="e2ee3-134">有关可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="e2ee3-134">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="e2ee3-135">“备份数据库”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="e2ee3-135">Back Up Database Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/options-in-the-back-up-database-task-for-maintenance-plan.md)  
  
 <span data-ttu-id="e2ee3-136">有关如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="e2ee3-136">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="e2ee3-137">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="e2ee3-137">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
