---
title: “清除维护”任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.maintenancecleanuptask.f1
helpviewer_keywords:
- deleting files
- removing files
- Maintenance Cleanup task
ms.assetid: 73ad3cd6-9a6d-44cf-905f-c56aa658bf42
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4d39dd775402adadbe51eaadc530f4feb288ab9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580811"
---
# <a name="maintenance-cleanup-task"></a><span data-ttu-id="30f6b-102">“清除维护”任务</span><span class="sxs-lookup"><span data-stu-id="30f6b-102">Maintenance Cleanup Task</span></span>
  <span data-ttu-id="30f6b-103">“清除维护”任务将删除与维护计划相关的文件，包括维护计划所创建的数据库备份文件和报表。</span><span class="sxs-lookup"><span data-stu-id="30f6b-103">The Maintenance Cleanup task removes files related to maintenance plans, including database backup files and reports created by maintenance plans.</span></span> <span data-ttu-id="30f6b-104">有关详细信息，请参阅 [维护计划](../../relational-databases/maintenance-plans/maintenance-plans.md) 和 [SQL Server 数据库的备份和还原](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="30f6b-104">For more information, see [Maintenance Plans](../../relational-databases/maintenance-plans/maintenance-plans.md) and [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
 <span data-ttu-id="30f6b-105">通过使用“清除维护”任务，包可以删除在指定服务器上的备份文件或维护计划报表。</span><span class="sxs-lookup"><span data-stu-id="30f6b-105">By using the Maintenance Cleanup task, a package can remove the backup files or maintenance plan reports on the specified server.</span></span> <span data-ttu-id="30f6b-106">“清除维护”任务包括的一个选项可以删除特定文件或删除文件夹中的一组文件。</span><span class="sxs-lookup"><span data-stu-id="30f6b-106">The Maintenance Cleanup task includes an option to remove a specific file or remove a group of files in a folder.</span></span> <span data-ttu-id="30f6b-107">可以指定要删除的文件的扩展名（可选）。</span><span class="sxs-lookup"><span data-stu-id="30f6b-107">Optionally you can specify the extension of the files to delete.</span></span>  
  
 <span data-ttu-id="30f6b-108">当您配置清除维护任务以删除备份文件时，默认的文件扩展名为 BAK。</span><span class="sxs-lookup"><span data-stu-id="30f6b-108">When you configure the Maintenance Cleanup task to remove backup files, the default file name extension is BAK.</span></span> <span data-ttu-id="30f6b-109">对于报表文件，默认文件扩展名为 TXT。</span><span class="sxs-lookup"><span data-stu-id="30f6b-109">For report files, the default file name extension is TXT.</span></span> <span data-ttu-id="30f6b-110">您可以根据需要更新扩展名，唯一的限制是扩展名的长度必须少于 256 个字符。</span><span class="sxs-lookup"><span data-stu-id="30f6b-110">You can update the extensions to suit your needs; the only limitation is that extensions must be less than 256 characters long.</span></span>  
  
 <span data-ttu-id="30f6b-111">通常，需要删除不再需要的旧文件，并且可以将“清除维护”任务配置为删除已达到指定时限的文件。</span><span class="sxs-lookup"><span data-stu-id="30f6b-111">Typically, you want to remove old files that are no longer needed, and the Maintenance Cleanup task can be configured to delete files that have reached a specified age.</span></span> <span data-ttu-id="30f6b-112">例如，可以将任务配置为删除时限超过四周的文件。</span><span class="sxs-lookup"><span data-stu-id="30f6b-112">For example, the task can be configured to delete files that are older than four weeks.</span></span> <span data-ttu-id="30f6b-113">可以使用日、周、月或年来指定要删除的文件的时限。</span><span class="sxs-lookup"><span data-stu-id="30f6b-113">You can specify the age of files to delete by using days, weeks, months, or years.</span></span> <span data-ttu-id="30f6b-114">如果不指定要删除的文件的最小时限，则删除所有指定类型的文件。</span><span class="sxs-lookup"><span data-stu-id="30f6b-114">If you do not specify the minimum age of files to delete, all files of the specified type are deleted.</span></span>  
  
 <span data-ttu-id="30f6b-115">与更早版本的“清除维护”任务相比，该任务的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本不自动删除指定目录的子目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="30f6b-115">In contrast to earlier versions of the Maintenance Cleanup task, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version of the task does not automatically delete files in the subdirectories of the specified directory.</span></span> <span data-ttu-id="30f6b-116">此约束减少了可能利用“清除维护”任务的功能来恶意删除文件的任何攻击的可攻击面。</span><span class="sxs-lookup"><span data-stu-id="30f6b-116">This constraint reduces the surface area of any attack that could exploit the functionality of the Maintenance Cleanup task to delete files maliciously.</span></span> <span data-ttu-id="30f6b-117">若要删除一级子文件夹，必须通过选中“清除维护任务”对话框的“包括一级子文件夹”选项来显式选择执行此操作   。</span><span class="sxs-lookup"><span data-stu-id="30f6b-117">To delete the first-level subfolders, you must explicitly elect to do this by checking the **Include first-level subfolders** option in the **Maintenance Cleanup Task** dialog box.</span></span>  
  
## <a name="configuration-of-the-maintenance-cleanup-task"></a><span data-ttu-id="30f6b-118">“维护清除”任务的配置</span><span class="sxs-lookup"><span data-stu-id="30f6b-118">Configuration of the Maintenance Cleanup Task</span></span>  
 <span data-ttu-id="30f6b-119">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器来设置属性。</span><span class="sxs-lookup"><span data-stu-id="30f6b-119">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="30f6b-120">此任务位于 **设计器中** “工具箱” **的** “维护计划中的任务” [!INCLUDE[ssIS](../../includes/ssis-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="30f6b-120">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="30f6b-121">有关可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="30f6b-121">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="30f6b-122">“清除维护”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="30f6b-122">Maintenance Cleanup Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/maintenance-cleanup-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="30f6b-123">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="30f6b-123">Related Tasks</span></span>  
 <span data-ttu-id="30f6b-124">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的信息，请参阅 [设置任务或容器的属性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="30f6b-124">For details about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30f6b-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30f6b-125">See Also</span></span>  
 <span data-ttu-id="30f6b-126">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="30f6b-126">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="30f6b-127">控制流</span><span class="sxs-lookup"><span data-stu-id="30f6b-127">Control Flow</span></span>](control-flow.md)  
  
  
