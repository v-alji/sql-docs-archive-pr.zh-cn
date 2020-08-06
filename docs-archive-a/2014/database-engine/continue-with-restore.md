---
title: 继续还原 |Microsoft Docs
description: 在 SQL Server 中，使用 "继续还原" 对话框指示是否要还原下一个备份集。
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.continuerestore.f1
ms.assetid: 987ac05f-57c0-49a9-9903-9889717aae4f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c7a438ac7b8696d2f57bdf93ff86030cf607e682
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693050"
---
# <a name="continue-with-restore"></a><span data-ttu-id="ddfbb-103">继续还原</span><span class="sxs-lookup"><span data-stu-id="ddfbb-103">Continue with Restore</span></span>
  <span data-ttu-id="ddfbb-104">使用 **“继续还原”** 对话框可指示是否要还原到下一个备份集。</span><span class="sxs-lookup"><span data-stu-id="ddfbb-104">Use the **Continue with Restore** dialog box to indicate whether you want to restore the next backup set.</span></span> <span data-ttu-id="ddfbb-105">若要延迟还原操作（例如，需要更换磁带），请待您做好继续操作的准备后再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="ddfbb-105">To delay the restore operation, for example, to swap tapes, wait until you are ready to proceed before you click **OK**.</span></span>  
  
 <span data-ttu-id="ddfbb-106">单击 **“否”** 将终止还原顺序，但是会将数据库保持在还原状态。</span><span class="sxs-lookup"><span data-stu-id="ddfbb-106">Clicking **No** terminates the restore sequence, leaving the database in the restoring state.</span></span> <span data-ttu-id="ddfbb-107">若要在以后继续执行还原操作，请使用相应的 **“还原数据库”** 或 **“还原事务日志”** 任务。</span><span class="sxs-lookup"><span data-stu-id="ddfbb-107">To continue with the restore later, use either the **Restore Database** or **Restore Transaction Log** task, as appropriate.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ddfbb-108">选项</span><span class="sxs-lookup"><span data-stu-id="ddfbb-108">Options</span></span>  
 <span data-ttu-id="ddfbb-109">**介质集**</span><span class="sxs-lookup"><span data-stu-id="ddfbb-109">**Media set**</span></span>  
 <span data-ttu-id="ddfbb-110">显示下一个介质集名称（如果可用的话）。</span><span class="sxs-lookup"><span data-stu-id="ddfbb-110">Displays the next media set name (if available).</span></span>  
  
 <span data-ttu-id="ddfbb-111">**备份集**</span><span class="sxs-lookup"><span data-stu-id="ddfbb-111">**Backup set**</span></span>  
 <span data-ttu-id="ddfbb-112">显示备份集的名称。</span><span class="sxs-lookup"><span data-stu-id="ddfbb-112">Displays the backup set name.</span></span>  
  
 <span data-ttu-id="ddfbb-113">**备份集说明**</span><span class="sxs-lookup"><span data-stu-id="ddfbb-113">**Backup set description**</span></span>  
 <span data-ttu-id="ddfbb-114">显示备份集的说明。</span><span class="sxs-lookup"><span data-stu-id="ddfbb-114">Displays the backup set description.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddfbb-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ddfbb-115">See Also</span></span>  
 <span data-ttu-id="ddfbb-116">[查看备份磁带或文件的内容 (SQL Server)](../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ddfbb-116">[View the Contents of a Backup Tape or File &#40;SQL Server&#41;](../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md) </span></span>  
 <span data-ttu-id="ddfbb-117">[查看逻辑备份设备的属性和内容 (SQL Server)](../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ddfbb-117">[View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md) </span></span>  
 <span data-ttu-id="ddfbb-118">[还原数据库备份 &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="ddfbb-118">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md) </span></span>  
 [<span data-ttu-id="ddfbb-119">还原事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ddfbb-119">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
  
