---
title: 备份文件必须位于独立于数据库文件的设备上 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7039bebb-1f25-4cf3-81f1-393dfb78da12
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d5eff9cb3139e1e1043f99ba63d11160b1010c27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690144"
---
# <a name="backup-files-must-be-on-separate-devices-from-the-database-files"></a><span data-ttu-id="5c39b-102">备份文件必须位于与数据库文件分开的设备上</span><span class="sxs-lookup"><span data-stu-id="5c39b-102">Backup Files Must Be on Separate Devices from the Database Files</span></span>
  <span data-ttu-id="5c39b-103">此规则检查数据库文件是否位于与备份文件分开的设备上。</span><span class="sxs-lookup"><span data-stu-id="5c39b-103">This rule checks whether database files are on devices separate from the backup files.</span></span> <span data-ttu-id="5c39b-104">如果数据库文件和备份文件位于同一台设备上并且该设备出现故障，数据库和备份都将不可用。</span><span class="sxs-lookup"><span data-stu-id="5c39b-104">If database files and backup files are on the same device and the device fails, the database and backups will be unavailable.</span></span> <span data-ttu-id="5c39b-105">此外，将数据库和备份文件放到不同的设备上还可以优化使用数据库和写入备份时的 I/O 性能。</span><span class="sxs-lookup"><span data-stu-id="5c39b-105">Also, putting the database and backup files on the separate devices optimizes the I/O performance for both the production use of the database and the writing of backups.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="5c39b-106">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="5c39b-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="5c39b-107">强烈建议您将数据库和备份放到不同的备份设备上。</span><span class="sxs-lookup"><span data-stu-id="5c39b-107">We strongly recommend that you put the database and backups on separate backup devices.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5c39b-108">此策略无法通过装入点检测分开的物理设备。</span><span class="sxs-lookup"><span data-stu-id="5c39b-108">This policy cannot detect separate physical devices through mount points.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="5c39b-109">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="5c39b-109">For More Information</span></span>  
 [<span data-ttu-id="5c39b-110">备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5c39b-110">Backup Devices &#40;SQL Server&#41;</span></span>](../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
 [<span data-ttu-id="5c39b-111">SQL Server 数据库的备份和还原</span><span class="sxs-lookup"><span data-stu-id="5c39b-111">Back Up and Restore of SQL Server Databases</span></span>](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
## <a name="see-also"></a><span data-ttu-id="5c39b-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5c39b-112">See Also</span></span>  
 [<span data-ttu-id="5c39b-113">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="5c39b-113">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
