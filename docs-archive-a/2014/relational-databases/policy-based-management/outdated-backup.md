---
title: 过时的备份 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 307a4ad0-675a-4f97-9a3c-cedd61bdfae5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c6a944b08b15d591a9bbce47a0c0c6a8de3eb54a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588471"
---
# <a name="outdated-backup"></a><span data-ttu-id="24d88-102">过时的备份</span><span class="sxs-lookup"><span data-stu-id="24d88-102">Outdated Backup</span></span>
  <span data-ttu-id="24d88-103">此规则检查数据库是否有最新备份。</span><span class="sxs-lookup"><span data-stu-id="24d88-103">This rule checks that a database has recent backups.</span></span> <span data-ttu-id="24d88-104">计划定期备份对于防止数据库因多种不同故障而造成数据丢失很重要。</span><span class="sxs-lookup"><span data-stu-id="24d88-104">Scheduling regular backups is important for protecting your databases against data loss from many different failures.</span></span> <span data-ttu-id="24d88-105">用于备份数据的合适频率取决于数据库的恢复模式、有关可能数据丢失的业务需求以及数据库的更新频率。</span><span class="sxs-lookup"><span data-stu-id="24d88-105">The appropriate frequency for backing up data depends on the recovery model of the database, on business requirements about potential data loss, and on how frequently the database is updated.</span></span> <span data-ttu-id="24d88-106">在频繁更新的数据库中，两次备份之间丢失工作的风险增加得相当快。</span><span class="sxs-lookup"><span data-stu-id="24d88-106">In a frequently updated database, the work-loss exposure increases fairly quickly between backups.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="24d88-107">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="24d88-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="24d88-108">建议您经常执行备份，以防止数据库丢失数据。</span><span class="sxs-lookup"><span data-stu-id="24d88-108">We recommend that you perform backups frequently enough to protect databases against data loss.</span></span>  
  
 <span data-ttu-id="24d88-109">简单恢复模式和完整恢复模式都需要数据备份。</span><span class="sxs-lookup"><span data-stu-id="24d88-109">The simple recovery model and full recovery model both require data backups.</span></span> <span data-ttu-id="24d88-110">对于任意一种恢复模式，您都可以使用差异备份来补充完整备份，以便有效地降低数据丢失的风险。</span><span class="sxs-lookup"><span data-stu-id="24d88-110">For either recovery model, you can supplement your full backups with differential backups to efficiently reduce the risk of data loss.</span></span>  
  
 <span data-ttu-id="24d88-111">对于使用完整恢复模式的数据库，建议您经常进行日志备份。</span><span class="sxs-lookup"><span data-stu-id="24d88-111">For a database that uses the full recovery model, we recommend that you take frequent log backups.</span></span> <span data-ttu-id="24d88-112">对于包含非常重要数据的生产数据库，通常每隔 1 到 15 分钟进行一次日志备份。</span><span class="sxs-lookup"><span data-stu-id="24d88-112">For a production database that contains very important data, log backups would typically be taken every one to fifteen minutes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="24d88-113">计划备份的推荐方法是数据库维护计划。</span><span class="sxs-lookup"><span data-stu-id="24d88-113">The recommended method for scheduling backups is a database maintenance plan.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="24d88-114">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="24d88-114">For More Information</span></span>  
 [<span data-ttu-id="24d88-115">备份和还原系统数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="24d88-115">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [<span data-ttu-id="24d88-116">恢复模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="24d88-116">Recovery Models &#40;SQL Server&#41;</span></span>](../backup-restore/recovery-models-sql-server.md)  
  
 [<span data-ttu-id="24d88-117">创建差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="24d88-117">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](../backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 [<span data-ttu-id="24d88-118">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="24d88-118">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
 [<span data-ttu-id="24d88-119">维护计划</span><span class="sxs-lookup"><span data-stu-id="24d88-119">Maintenance Plans</span></span>](../maintenance-plans/maintenance-plans.md)  
  
 [<span data-ttu-id="24d88-120">事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="24d88-120">Transaction Log Backups &#40;SQL Server&#41;</span></span>](../backup-restore/transaction-log-backups-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="24d88-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24d88-121">See Also</span></span>  
 [<span data-ttu-id="24d88-122">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="24d88-122">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
