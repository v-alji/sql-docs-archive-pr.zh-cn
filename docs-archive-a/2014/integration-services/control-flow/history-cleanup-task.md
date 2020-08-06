---
title: “清除历史记录”任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.historycleanuptask.f1
helpviewer_keywords:
- history tables [SQL Server]
- History Cleanup task [Integration Services]
ms.assetid: 5defc5b9-dfd3-4859-a7fe-ac8c2b5480f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 84bc697b7fb18269fc581cea51e111aebc82c15e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576926"
---
# <a name="history-cleanup-task"></a><span data-ttu-id="cd9bc-102">“清除历史记录”任务</span><span class="sxs-lookup"><span data-stu-id="cd9bc-102">History Cleanup Task</span></span>
  <span data-ttu-id="cd9bc-103">“清除历史记录”任务删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb 数据库中下列历史记录表中的条目：</span><span class="sxs-lookup"><span data-stu-id="cd9bc-103">The History Cleanup task deletes entries in the following history tables in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb database.</span></span>  
  
-   <span data-ttu-id="cd9bc-104">backupfile</span><span class="sxs-lookup"><span data-stu-id="cd9bc-104">backupfile</span></span>  
  
-   <span data-ttu-id="cd9bc-105">backupfilegroup</span><span class="sxs-lookup"><span data-stu-id="cd9bc-105">backupfilegroup</span></span>  
  
-   <span data-ttu-id="cd9bc-106">backupmediafamily</span><span class="sxs-lookup"><span data-stu-id="cd9bc-106">backupmediafamily</span></span>  
  
-   <span data-ttu-id="cd9bc-107">backupmediaset</span><span class="sxs-lookup"><span data-stu-id="cd9bc-107">backupmediaset</span></span>  
  
-   <span data-ttu-id="cd9bc-108">backupset</span><span class="sxs-lookup"><span data-stu-id="cd9bc-108">backupset</span></span>  
  
-   <span data-ttu-id="cd9bc-109">restorefile</span><span class="sxs-lookup"><span data-stu-id="cd9bc-109">restorefile</span></span>  
  
-   <span data-ttu-id="cd9bc-110">restorefilegroup</span><span class="sxs-lookup"><span data-stu-id="cd9bc-110">restorefilegroup</span></span>  
  
-   <span data-ttu-id="cd9bc-111">restorehistory</span><span class="sxs-lookup"><span data-stu-id="cd9bc-111">restorehistory</span></span>  
  
 <span data-ttu-id="cd9bc-112">通过使用“清除历史记录”任务，包可以删除与备份和还原活动、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业和数据库维护计划相关的历史数据。</span><span class="sxs-lookup"><span data-stu-id="cd9bc-112">By using the History Cleanup task, a package can delete historical data related to backup and restore activities, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, and database maintenance plans.</span></span>  
  
 <span data-ttu-id="cd9bc-113">此任务封装 sp_delete_backuphistory 系统存储过程并将指定日期作为参数传递给该过程。</span><span class="sxs-lookup"><span data-stu-id="cd9bc-113">This task encapsulates the sp_delete_backuphistory system stored procedure and passes the specified date to the procedure as an argument.</span></span> <span data-ttu-id="cd9bc-114">有关详细信息，请参阅 [sp_delete_backuphistory (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cd9bc-114">For more information, see [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).</span></span>  
  
## <a name="configuration-of-the-history-cleanup-task"></a><span data-ttu-id="cd9bc-115">“清除历史记录”任务的配置</span><span class="sxs-lookup"><span data-stu-id="cd9bc-115">Configuration of the History Cleanup Task</span></span>  
 <span data-ttu-id="cd9bc-116">此任务包含的一个属性用于指定要保留在历史记录表中的数据的最早日期。</span><span class="sxs-lookup"><span data-stu-id="cd9bc-116">The task includes a property for specifying the oldest date of data retained in the history tables.</span></span> <span data-ttu-id="cd9bc-117">您可以用从当天算起的天数、周数、月数或年数来指示日期，此任务可自动将该间隔转换为一个日期。</span><span class="sxs-lookup"><span data-stu-id="cd9bc-117">You can indicate the date by number of days, weeks, months, or years from the current day, and the task automatically translates the interval to a date.</span></span>  
  
 <span data-ttu-id="cd9bc-118">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器来设置属性。</span><span class="sxs-lookup"><span data-stu-id="cd9bc-118">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="cd9bc-119">此任务位于 **设计器中** “工具箱” **的** “维护计划中的任务” [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="cd9bc-119">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="cd9bc-120">有关可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="cd9bc-120">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="cd9bc-121">“清除历史记录”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="cd9bc-121">History Cleanup Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/history-cleanup-task-maintenance-plan.md)  
  
 <span data-ttu-id="cd9bc-122">有关如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="cd9bc-122">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="cd9bc-123">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="cd9bc-123">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="cd9bc-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd9bc-124">See Also</span></span>  
 <span data-ttu-id="cd9bc-125">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="cd9bc-125">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="cd9bc-126">控制流</span><span class="sxs-lookup"><span data-stu-id="cd9bc-126">Control Flow</span></span>](control-flow.md)  
  
  
