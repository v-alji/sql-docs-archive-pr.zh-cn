---
title: 备份时间线 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.POINTINTIMERESTORE.F1
- sql12.swb.backuptimeline.f1
helpviewer_keywords:
- Backup Timeline
ms.assetid: ae3565f2-ddb2-4469-a992-7531d4f9ebb8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9b075f8c9ec32cfe483c64e34e9f9b4e4b6e80e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591426"
---
# <a name="backup-timeline"></a><span data-ttu-id="b8428-102">备份时间线</span><span class="sxs-lookup"><span data-stu-id="b8428-102">Backup Timeline</span></span>
  <span data-ttu-id="b8428-103">使用“备份时间线”  对话框可以查找和指定备份以便将数据库还原到某个时间点。</span><span class="sxs-lookup"><span data-stu-id="b8428-103">Use the **Backup Timeline** dialog box to locate and specify backups to restore a database to a point-in-time.</span></span> <span data-ttu-id="b8428-104">通过单击“还原数据库（“常规”页）”  窗格上的“时间线”  可以访问“备份时间线”  对话框。</span><span class="sxs-lookup"><span data-stu-id="b8428-104">The **Backup Timeline** dialog box is accessed by clicking **Timeline** on the **Restore Database (General Page)** pane.</span></span> <span data-ttu-id="b8428-105">通过此对话框，您可以查看对数据库执行的还原操作的时间线。</span><span class="sxs-lookup"><span data-stu-id="b8428-105">This dialog box allows you to view a timeline of the restore operations performed on the database.</span></span>  
  
 <span data-ttu-id="b8428-106">数据库恢复顾问确保仅选择需要恢复到该时点的那些备份。</span><span class="sxs-lookup"><span data-stu-id="b8428-106">The Database Recovery Advisor ensures that only backups that are required for restoring to that point in time are selected.</span></span> <span data-ttu-id="b8428-107">这些选定的备份构成了为您的还原操作建议的还原计划。</span><span class="sxs-lookup"><span data-stu-id="b8428-107">These selected backups make up the recommended restore plan for your restore operation.</span></span> <span data-ttu-id="b8428-108">您应仅使用选定的备份。</span><span class="sxs-lookup"><span data-stu-id="b8428-108">You should use only the selected backups.</span></span> <span data-ttu-id="b8428-109">有关数据库恢复顾问的信息，请参阅[还原和恢复概述 (SQL Server)](restore-and-recovery-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b8428-109">For information about the Database Recovery Advisor, see [Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md).</span></span>  
  
## <a name="restore-to"></a><span data-ttu-id="b8428-110">还原到</span><span class="sxs-lookup"><span data-stu-id="b8428-110">Restore to</span></span>  
 <span data-ttu-id="b8428-111">默认情况下，将选择 **“上次所做备份”** 。</span><span class="sxs-lookup"><span data-stu-id="b8428-111">**Last backup taken** is selected by default.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="b8428-112">将选择相应的备份以便还原数据库，并且将数据库还原到该时点的上一备份。</span><span class="sxs-lookup"><span data-stu-id="b8428-112">will select the appropriate backups to restore the database, and will restore the database to the point of the last backup.</span></span> <span data-ttu-id="b8428-113">单击“具体日期和时间”  可以手动设置日期和时间（选择特定的时间点）。</span><span class="sxs-lookup"><span data-stu-id="b8428-113">Click **A specific date and time** to manually set the date and time (selecting a specific point in time).</span></span>  
  
 <span data-ttu-id="b8428-114">**“特定日期和时间”** 允许您停止在所选的特定日期和时间上的还原。</span><span class="sxs-lookup"><span data-stu-id="b8428-114">**Specific date and time** permits you stop the restore at a specific date and time that you select.</span></span> <span data-ttu-id="b8428-115">时间线展现了围绕所选日期和时间的 24 小时中执行的备份操作。</span><span class="sxs-lookup"><span data-stu-id="b8428-115">The timeline shows a representation of the backup operations performed in the 24 hours around the select date and time.</span></span>  
  
 <span data-ttu-id="b8428-116">**Date**</span><span class="sxs-lookup"><span data-stu-id="b8428-116">**Date**</span></span>  
 <span data-ttu-id="b8428-117">输入一个日期或者从下拉列表中选择一个日期。</span><span class="sxs-lookup"><span data-stu-id="b8428-117">Enter or select a date from the drop-down list.</span></span>  
  
 <span data-ttu-id="b8428-118">**时间**</span><span class="sxs-lookup"><span data-stu-id="b8428-118">**Time**</span></span>  
 <span data-ttu-id="b8428-119">输入或选择一个日期以便为还原停止指定特定的时间点。</span><span class="sxs-lookup"><span data-stu-id="b8428-119">Enter or select a date to designate the specific point-in-time for the restore to stop.</span></span>  
  
 <span data-ttu-id="b8428-120">**时间线间隔**</span><span class="sxs-lookup"><span data-stu-id="b8428-120">**Timeline Interval**</span></span>  
 <span data-ttu-id="b8428-121">显示可在时间线上查看的间隔类型的选项。</span><span class="sxs-lookup"><span data-stu-id="b8428-121">Displays the options for the interval types viewable on the timeline.</span></span>  
  
## <a name="timeline-and-legend"></a><span data-ttu-id="b8428-122">时间线和图例</span><span class="sxs-lookup"><span data-stu-id="b8428-122">Timeline and Legend</span></span>  
 <span data-ttu-id="b8428-123">使用时间线之下的滚动条，沿时间线向前和向后移动光标。</span><span class="sxs-lookup"><span data-stu-id="b8428-123">Use the scroll bar beneath the timeline to move the cursor forward and backward along the timeline.</span></span> <span data-ttu-id="b8428-124">单击某一备份以便将滚动条移动到该备份的结尾处。</span><span class="sxs-lookup"><span data-stu-id="b8428-124">Click on a backup to move the scroll bar to the end of that backup.</span></span> <span data-ttu-id="b8428-125">将鼠标指针悬停在标记之上，以便显示提供与所选备份集有关的信息的屏幕提示。</span><span class="sxs-lookup"><span data-stu-id="b8428-125">Hover the mouse over a marker to display a ScreenTip providing information about the selected backup set.</span></span> <span data-ttu-id="b8428-126">备份信息通过以下标记显示在时间线上。</span><span class="sxs-lookup"><span data-stu-id="b8428-126">Backup information is shown on the timeline by the following markers.</span></span>  
  
 <span data-ttu-id="b8428-127">大三角形</span><span class="sxs-lookup"><span data-stu-id="b8428-127">Larger triangle</span></span>  
 <span data-ttu-id="b8428-128">表示对数据库执行的完全备份，同时指示执行每个完整备份的特定时间点。</span><span class="sxs-lookup"><span data-stu-id="b8428-128">Represents the full backups performed on the database, denoting the specific point in time each full backup was performed.</span></span>  
  
 <span data-ttu-id="b8428-129">小三角形</span><span class="sxs-lookup"><span data-stu-id="b8428-129">Smaller triangle</span></span>  
 <span data-ttu-id="b8428-130">表示对数据库执行的差异备份，同时指示执行每个差异备份的特定时间点。</span><span class="sxs-lookup"><span data-stu-id="b8428-130">Represents the differential backups performed on the database, denoting the specific point in time that each differential backup was performed.</span></span>  
  
 <span data-ttu-id="b8428-131">绿色阴影区域</span><span class="sxs-lookup"><span data-stu-id="b8428-131">Green shaded areas</span></span>  
 <span data-ttu-id="b8428-132">表示事务日志备份覆盖范围。</span><span class="sxs-lookup"><span data-stu-id="b8428-132">Represents the transaction log backup coverage.</span></span>  
  
 <span data-ttu-id="b8428-133">红线</span><span class="sxs-lookup"><span data-stu-id="b8428-133">Red line</span></span>  
 <span data-ttu-id="b8428-134">只能沿着可能执行还原的时间线定位。</span><span class="sxs-lookup"><span data-stu-id="b8428-134">Can only be positioned along the timeline where the restore is possible.</span></span> <span data-ttu-id="b8428-135">沿时间线移动红线将调整在 **“日期”** 和 **“时间”** 框中显示的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="b8428-135">Moving the red line along the timeline adjusts the date and time displayed in the **Date** and **Time** boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8428-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b8428-136">See Also</span></span>  
 [<span data-ttu-id="b8428-137">还原数据库（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="b8428-137">Restore Database &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
  
