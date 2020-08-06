---
title: 示例：只读文件的联机还原（简单恢复模式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restore sequences [SQL Server], online
- online restores [SQL Server], simple recovery model
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: 0c691fc6-9865-46a7-b055-8097424492d6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d84c920a2cb40866ba106b4d30d8e24c4caea611
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694000"
---
# <a name="example-online-restore-of-a-read-only-file-simple-recovery-model"></a><span data-ttu-id="4f9c2-102">示例：只读文件的联机还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="4f9c2-102">Example: Online Restore of a Read-Only File (Simple Recovery Model)</span></span>
  <span data-ttu-id="4f9c2-103">本主题针对采用简单恢复模式并包含只读文件组的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="4f9c2-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the simple recovery model that contain a read-only filegroup.</span></span> <span data-ttu-id="4f9c2-104">在简单恢复模式下，如果某个文件在最后一次变为只读时进行了备份，则可以联机还原该只读文件。</span><span class="sxs-lookup"><span data-stu-id="4f9c2-104">Under the simple recovery model, a read-only file can be restored online if a file backup exists that was taken since the file became read-only for the last time.</span></span>  
  
 <span data-ttu-id="4f9c2-105">在此示例中，名为 `adb` 的数据库包含三个文件组。</span><span class="sxs-lookup"><span data-stu-id="4f9c2-105">In this example, a database named `adb` contains three filegroups.</span></span> <span data-ttu-id="4f9c2-106">文件组 `A` 为读/写文件组，而文件组 `B` 和 `C` 是只读的。</span><span class="sxs-lookup"><span data-stu-id="4f9c2-106">Filegroup `A` is read/write, and filegroups `B` and `C` are read-only.</span></span> <span data-ttu-id="4f9c2-107">最初，所有文件组都处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="4f9c2-107">Initially, all of the filegroups are online.</span></span> <span data-ttu-id="4f9c2-108">现在必须还原文件组 `B`中的只读文件 `b1`。</span><span class="sxs-lookup"><span data-stu-id="4f9c2-108">A read-only file in filegroup `B`, `b1`, has to be restored.</span></span> <span data-ttu-id="4f9c2-109">数据库管理员可以使用在该文件变为只读状态之后获取的备份对其进行还原。</span><span class="sxs-lookup"><span data-stu-id="4f9c2-109">The database administrator can restore it by using a backup that was taken after the file became read-only.</span></span> <span data-ttu-id="4f9c2-110">在还原过程中，文件组 `B` 将处于脱机状态，但是数据库的其余文件组仍处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="4f9c2-110">For the duration of the restore, filegroup `B` will be offline, but the remainder of the database will remain online.</span></span>  
  
## <a name="restore-sequence"></a><span data-ttu-id="4f9c2-111">还原顺序</span><span class="sxs-lookup"><span data-stu-id="4f9c2-111">Restore Sequence</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f9c2-112">联机还原顺序的语法与脱机还原顺序的语法完全相同。</span><span class="sxs-lookup"><span data-stu-id="4f9c2-112">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
 <span data-ttu-id="4f9c2-113">若要还原文件，数据库管理员应使用以下还原顺序：</span><span class="sxs-lookup"><span data-stu-id="4f9c2-113">To restore the file, the database administrator uses the following restore sequence:</span></span>  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup   
WITH RECOVERY  
```  
  
 <span data-ttu-id="4f9c2-114">文件现在处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="4f9c2-114">The file is now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="4f9c2-115">其他示例</span><span class="sxs-lookup"><span data-stu-id="4f9c2-115">Additional Examples</span></span>  
  
-   [<span data-ttu-id="4f9c2-116">示例：数据库的段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="4f9c2-116">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="4f9c2-117">示例：仅对某些文件组进行段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="4f9c2-117">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="4f9c2-118">示例：数据库的段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="4f9c2-118">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="4f9c2-119">示例：仅对某些文件组进行段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="4f9c2-119">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="4f9c2-120">示例：读/写文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="4f9c2-120">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="4f9c2-121">示例：只读文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="4f9c2-121">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="4f9c2-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f9c2-122">See Also</span></span>  
 <span data-ttu-id="4f9c2-123">[联机还原 (SQL Server)](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4f9c2-123">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="4f9c2-124">[段落还原 (SQL Server)](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4f9c2-124">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="4f9c2-125">[文件还原（简单恢复模式）](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="4f9c2-125">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="4f9c2-126">[还原和恢复概述 (SQL Server)](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4f9c2-126">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="4f9c2-127">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4f9c2-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
