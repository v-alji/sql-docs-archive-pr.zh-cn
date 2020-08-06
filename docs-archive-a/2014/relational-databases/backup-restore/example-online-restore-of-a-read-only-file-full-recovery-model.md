---
title: 示例：联机还原只读文件（完整恢复模式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- online restores [SQL Server], full recovery model
- restore sequences [SQL Server], online
ms.assetid: 7ea2d2af-086f-48dc-9636-38dc194c7090
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f493c88d64e6ed22e44f33f1442ae581daa8ed4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694001"
---
# <a name="example-online-restore-of-a-read-only-file-full-recovery-model"></a><span data-ttu-id="ed3d3-102">示例：只读文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="ed3d3-102">Example: Online Restore of a Read-Only File (Full Recovery Model)</span></span>
  <span data-ttu-id="ed3d3-103">本主题与完整恢复模式下包含多个文件或文件组的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库相关。</span><span class="sxs-lookup"><span data-stu-id="ed3d3-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the full recovery model that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="ed3d3-104">在此示例中，名为 `adb`的数据库（使用完整恢复模式）包含三个文件组。</span><span class="sxs-lookup"><span data-stu-id="ed3d3-104">In this example, a database named `adb`, which uses the full recovery model, contains three filegroups.</span></span> <span data-ttu-id="ed3d3-105">文件组 `A` 为读/写文件组，文件组 `B` 和文件组 `C` 为只读文件组。</span><span class="sxs-lookup"><span data-stu-id="ed3d3-105">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="ed3d3-106">最初，所有文件组都处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="ed3d3-106">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="ed3d3-107">现在必须还原数据库 `b1`中文件组 `B` 的只读文件 `adb` 。</span><span class="sxs-lookup"><span data-stu-id="ed3d3-107">A read-only file, `b1`, in filegroup `B` of database `adb` has to be restored.</span></span> <span data-ttu-id="ed3d3-108">由于在文件变为只读后进行过备份，因此不需要使用日志备份。</span><span class="sxs-lookup"><span data-stu-id="ed3d3-108">A backup was taken since the file became read-only; therefore, log backups are not required.</span></span> <span data-ttu-id="ed3d3-109">在还原过程中文件组 `B` 处于脱机状态，而数据库的其余部分保持联机状态。</span><span class="sxs-lookup"><span data-stu-id="ed3d3-109">Filegroup `B` is offline for the duration of the restore, but the remainder of the database remains online.</span></span>  
  
## <a name="restore-sequence"></a><span data-ttu-id="ed3d3-110">还原顺序</span><span class="sxs-lookup"><span data-stu-id="ed3d3-110">Restore Sequence</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ed3d3-111">联机还原顺序的语法与脱机还原顺序的语法完全相同。</span><span class="sxs-lookup"><span data-stu-id="ed3d3-111">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
 <span data-ttu-id="ed3d3-112">若要还原文件，数据库管理员应使用以下还原顺序：</span><span class="sxs-lookup"><span data-stu-id="ed3d3-112">To restore the file, the database administrator uses the following restore sequence:</span></span>  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup  
WITH RECOVERY   
```  
  
 <span data-ttu-id="ed3d3-113">文件组 B 现在处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="ed3d3-113">Filegroup B is now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="ed3d3-114">其他示例</span><span class="sxs-lookup"><span data-stu-id="ed3d3-114">Additional Examples</span></span>  
  
-   [<span data-ttu-id="ed3d3-115">示例：数据库的段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="ed3d3-115">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="ed3d3-116">示例：仅对某些文件组进行段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="ed3d3-116">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="ed3d3-117">示例：只读文件的联机还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="ed3d3-117">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="ed3d3-118">示例：数据库的段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="ed3d3-118">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="ed3d3-119">示例：仅对某些文件组进行段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="ed3d3-119">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="ed3d3-120">示例：读/写文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="ed3d3-120">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="ed3d3-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed3d3-121">See Also</span></span>  
 <span data-ttu-id="ed3d3-122">[联机还原 (SQL Server)](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ed3d3-122">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="ed3d3-123">[还原和恢复概述 (SQL Server)](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ed3d3-123">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="ed3d3-124">[文件还原（完整恢复模式）](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="ed3d3-124">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="ed3d3-125">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ed3d3-125">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
