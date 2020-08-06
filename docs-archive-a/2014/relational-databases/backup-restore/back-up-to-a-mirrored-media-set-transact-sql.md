---
title: 备份到镜像媒体集 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 255a3c190139c029f5211dcab9780b6d07d975a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587435"
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a><span data-ttu-id="4f2bf-102">备份镜像媒体集 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4f2bf-102">Back Up to a Mirrored Media Set (Transact-SQL)</span></span>
  <span data-ttu-id="4f2bf-103">本主题介绍 [!INCLUDE[tsql](../../includes/tsql-md.md)] 在备份数据库时如何使用[BACKUP](/sql/t-sql/statements/backup-transact-sql)语句指定镜像介质集 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4f2bf-103">This topic describes how to use the [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) statement to specify a mirrored media set when backing up a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="4f2bf-104">在 BACKUP 语句中的 TO 子句中指定第一个镜像。</span><span class="sxs-lookup"><span data-stu-id="4f2bf-104">In your BACKUP statement, specify the first mirror in the TO clause.</span></span> <span data-ttu-id="4f2bf-105">然后，在它自己的 MIRROR TO 子句中指定每个镜像。</span><span class="sxs-lookup"><span data-stu-id="4f2bf-105">Then, specify each mirror in its own MIRROR TO clause.</span></span> <span data-ttu-id="4f2bf-106">TO 和 MIRROR TO 子句必须指定相同数量和类型的备份设备。</span><span class="sxs-lookup"><span data-stu-id="4f2bf-106">The TO and MIRROR TO clauses must specify the same number and type of backup devices.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f2bf-107">示例</span><span class="sxs-lookup"><span data-stu-id="4f2bf-107">Example</span></span>  
 <span data-ttu-id="4f2bf-108">下例创建上一图中所述的镜像介质集并将 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库同时备份到两个镜像。</span><span class="sxs-lookup"><span data-stu-id="4f2bf-108">The following example creates the mirrored media set illustrated in the previous illustration and backs up the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to both mirrors.</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
    FORMAT,  
    MEDIANAME = 'AdventureWorks2012Set1';  
GO  
```  
  
## <a name="related-tasks"></a><span data-ttu-id="4f2bf-109">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="4f2bf-109">Related Tasks</span></span>  
 <span data-ttu-id="4f2bf-110">**从镜像备份还原**</span><span class="sxs-lookup"><span data-stu-id="4f2bf-110">**To restore from a mirrored backup**</span></span>  
  
-   [<span data-ttu-id="4f2bf-111">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4f2bf-111">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="4f2bf-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f2bf-112">See Also</span></span>  
 <span data-ttu-id="4f2bf-113">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4f2bf-113">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="4f2bf-114">镜像备份媒体集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4f2bf-114">Mirrored Backup Media Sets &#40;SQL Server&#41;</span></span>](mirrored-backup-media-sets-sql-server.md)  
  
  
