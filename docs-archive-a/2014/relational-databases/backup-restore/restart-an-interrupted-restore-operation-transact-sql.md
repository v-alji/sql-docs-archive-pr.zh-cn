---
title: 重新启动中断的还原操作 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- interrupted restore operation
- restoring databases [SQL Server], restarting interrupted operation
- resetting options changed after backup
- database restores [SQL Server], restarting interrupted operation
- restarting interrupted restore operation
- restoring interrupted operation [SQL Server]
ms.assetid: 6413a07d-fd90-448d-8f29-12c5a1972618
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a6fa09ce66865d61c8f3a86feedc04eaf8deec2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682896"
---
# <a name="restart-an-interrupted-restore-operation-transact-sql"></a><span data-ttu-id="7ca8e-102">重新启动中断的还原操作 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7ca8e-102">Restart an Interrupted Restore Operation (Transact-SQL)</span></span>
  <span data-ttu-id="7ca8e-103">本主题说明如何重新启动中断的还原操作。</span><span class="sxs-lookup"><span data-stu-id="7ca8e-103">This topic explains how to restart an interrupted restore operation.</span></span>  
  
### <a name="to-restart-an-interrupted-restore-operation"></a><span data-ttu-id="7ca8e-104">重新启动中断的还原操作</span><span class="sxs-lookup"><span data-stu-id="7ca8e-104">To restart an interrupted restore operation</span></span>  
  
1.  <span data-ttu-id="7ca8e-105">再次执行中断的 RESTORE 语句，同时指定：</span><span class="sxs-lookup"><span data-stu-id="7ca8e-105">Execute the interrupted RESTORE statement again, specifying:</span></span>  
  
    -   <span data-ttu-id="7ca8e-106">原 RESTORE 语句中使用的相同子句。</span><span class="sxs-lookup"><span data-stu-id="7ca8e-106">The same clauses used in the original RESTORE statement.</span></span>  
  
    -   <span data-ttu-id="7ca8e-107">RESTART 子句。</span><span class="sxs-lookup"><span data-stu-id="7ca8e-107">The RESTART clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ca8e-108">示例</span><span class="sxs-lookup"><span data-stu-id="7ca8e-108">Example</span></span>  
 <span data-ttu-id="7ca8e-109">以下示例将重新启动中断的还原操作。</span><span class="sxs-lookup"><span data-stu-id="7ca8e-109">This example restarts an interrupted restore operation.</span></span>  
  
```sql  
-- Restore a full database backup of the AdventureWorks database.  
RESTORE DATABASE AdventureWorks  
   FROM DISK = 'C:\AdventureWorks.bck'  
GO  
-- The restore operation halted prematurely.  
-- Repeat the original RESTORE statement specifying WITH RESTART.  
RESTORE DATABASE AdventureWorks   
   FROM DISK = 'C:\AdventureWorks.bck'  
   WITH RESTART  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ca8e-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ca8e-110">See Also</span></span>  
 <span data-ttu-id="7ca8e-111">[完整数据库还原（完整恢复模式）](complete-database-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="7ca8e-111">[Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="7ca8e-112">[完整数据库还原（简单恢复模式）](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="7ca8e-112">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="7ca8e-113">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7ca8e-113">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
