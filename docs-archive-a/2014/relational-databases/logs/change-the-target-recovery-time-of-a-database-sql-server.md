---
title: 更改数据库的目标恢复时间 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: e466419a-d8a4-48f7-8d97-13a903ad6b15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c4331d2ade2819d172189a0de9daddecf3d9f6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580740"
---
# <a name="change-the-target-recovery-time-of-a-database-sql-server"></a><span data-ttu-id="4ea71-102">更改数据库的目标恢复时间 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4ea71-102">Change the Target Recovery Time of a Database (SQL Server)</span></span>
  <span data-ttu-id="4ea71-103">本主题介绍如何通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中设置和更改 [!INCLUDE[tsql](../../includes/tsql-md.md)]数据库的目标恢复时间。</span><span class="sxs-lookup"><span data-stu-id="4ea71-103">This topic describes how to set the change the target recovery time of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4ea71-104">默认情况下，目标恢复时间为 0，数据库使用“自动检查点” \*\* （由 **recovery interval** 服务器选项控制）。</span><span class="sxs-lookup"><span data-stu-id="4ea71-104">By default, the target recovery time is 0, and the database uses *automatic checkpoints* (which are controlled by the **recovery interval** server option).</span></span> <span data-ttu-id="4ea71-105">如果将目标恢复时间设置为大于 0，数据库将使用“间接检查点” \*\* 并为此数据库建立恢复时间上限。</span><span class="sxs-lookup"><span data-stu-id="4ea71-105">Setting the target recovery time to greater than 0 causes the database to use the *indirect-checkpoints* and establishes an upper-bound on recovery time for this database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4ea71-106">如果长时间运行的事务导致过多 UNDO 时间，则可能超过给定数据库的目标恢复时间设置为该数据库指定的上限。</span><span class="sxs-lookup"><span data-stu-id="4ea71-106">The upper-bound that is specified for a given database by its target recovery time setting could be exceeded if a long-running transaction causes excessive UNDO times.</span></span>  
  
-   <span data-ttu-id="4ea71-107">**开始之前：** [限制和局限](#Restrictions)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="4ea71-107">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="4ea71-108">**要更改目标恢复时间，请使用：** [SQL Server Management Studio](#SSMSProcedure) 或 [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="4ea71-108">**To change the target recovery time, using:**  [SQL Server Management Studio](#SSMSProcedure) or [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4ea71-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="4ea71-109">Before You Begin</span></span>  
  
###  <a name="Restrictions"></a>  
  
> [!CAUTION]  
>  <span data-ttu-id="4ea71-110">为间接检查点配置的数据库上的联机事务工作负荷可能导致性能下降。</span><span class="sxs-lookup"><span data-stu-id="4ea71-110">An online transactional workload on a database that is configured for indirect checkpoints could experience performance degradation.</span></span> <span data-ttu-id="4ea71-111">间接检查点确保损坏页的数量低于特定阙值，以便在目标恢复时间内完成数据库恢复。</span><span class="sxs-lookup"><span data-stu-id="4ea71-111">Indirect checkpoints make sure that the number of dirty pages are below a certain threshold so that the database recovery completes within the target recovery time.</span></span> <span data-ttu-id="4ea71-112">与利用损坏页数量的间接检查点相反，恢复间隔配置选项使用事务数量来确定恢复时间。</span><span class="sxs-lookup"><span data-stu-id="4ea71-112">The recovery interval configuration option uses the number of transactions to determine the recovery time as opposed to indirect checkpoints which makes use of number of dirty pages.</span></span> <span data-ttu-id="4ea71-113">当在接收大量 DML 操作的数据库上启用了间接检查点时，后台写入线程可以开始积极刷新磁盘的脏缓冲区，以确保执行恢复所需的时间在数据库所设目标恢复时间范围内。</span><span class="sxs-lookup"><span data-stu-id="4ea71-113">When indirect checkpoints are enabled on a database receiving a large number of DML operations, the background writer can start aggressively flushing dirty buffers to disk to ensure that the time required to perform recovery is within the target recovery time set of the database.</span></span> <span data-ttu-id="4ea71-114">这可能造成某些系统上出现额外的 I/O 活动，如果磁盘子系统在 I/O 阙值之上或附近运行，则这会导致性能瓶颈。</span><span class="sxs-lookup"><span data-stu-id="4ea71-114">This can cause additional I/O activity on certain systems which can contribute to a performance bottleneck if the disk subsystem is operating above or nearing the I/O threshold.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4ea71-115">Security</span><span class="sxs-lookup"><span data-stu-id="4ea71-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4ea71-116">权限</span><span class="sxs-lookup"><span data-stu-id="4ea71-116">Permissions</span></span>  
 <span data-ttu-id="4ea71-117">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="4ea71-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4ea71-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4ea71-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="4ea71-119">**更改目标恢复时间**</span><span class="sxs-lookup"><span data-stu-id="4ea71-119">**To change the target recovery time**</span></span>  
  
1.  <span data-ttu-id="4ea71-120">在 **“对象资源管理器”** 中，连接到某个 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例，再展开该实例。</span><span class="sxs-lookup"><span data-stu-id="4ea71-120">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and expand that instance.</span></span>  
  
2.  <span data-ttu-id="4ea71-121">右键单击要更改的数据库，然后单击 **“属性”** 命令。</span><span class="sxs-lookup"><span data-stu-id="4ea71-121">Right-click the database you want to change, and click the **Properties** command.</span></span>  
  
3.  <span data-ttu-id="4ea71-122">在 **“数据库属性”** 对话框中，单击 **“选项”** 页。</span><span class="sxs-lookup"><span data-stu-id="4ea71-122">In the **Database Properties** dialog box, click the **Options** page.</span></span>  
  
4.  <span data-ttu-id="4ea71-123">在 **“恢复”** 面板的 **“目标恢复时间(秒)”** 字段中，指定要作为此数据库恢复时间上限的秒数。</span><span class="sxs-lookup"><span data-stu-id="4ea71-123">In the **Recovery** panel, in the **Target Recovery Time (Seconds)** field, specify the number of seconds that you want as the upper-bound on the recovery time for this database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4ea71-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4ea71-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="4ea71-125">**更改目标恢复时间**</span><span class="sxs-lookup"><span data-stu-id="4ea71-125">**To change the target recovery time**</span></span>  
  
1.  <span data-ttu-id="4ea71-126">连接到数据库所在的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="4ea71-126">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the database resides.</span></span>  
  
2.  <span data-ttu-id="4ea71-127">按如下所示使用以下 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)语句：</span><span class="sxs-lookup"><span data-stu-id="4ea71-127">Use the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)statement, as follows:</span></span>  
  
     <span data-ttu-id="4ea71-128">TARGET_RECOVERY_TIME **=** _target_recovery_time_ { SECONDS | MINUTES }</span><span class="sxs-lookup"><span data-stu-id="4ea71-128">TARGET_RECOVERY_TIME **=**_target_recovery_time_ { SECONDS | MINUTES }</span></span>  
  
     <span data-ttu-id="4ea71-129">*target_recovery_time*</span><span class="sxs-lookup"><span data-stu-id="4ea71-129">*target_recovery_time*</span></span>  
     <span data-ttu-id="4ea71-130">大于 0（默认值）时，指定在发生崩溃的情况下指定数据库的恢复时间上限。</span><span class="sxs-lookup"><span data-stu-id="4ea71-130">When greater than 0 (the default), specifies the upper-bound on the recovery time for the specified database in the event of a crash.</span></span>  
  
     <span data-ttu-id="4ea71-131">SECONDS</span><span class="sxs-lookup"><span data-stu-id="4ea71-131">SECONDS</span></span>  
     <span data-ttu-id="4ea71-132">指示 *target_recovery_time* 表示为秒数。</span><span class="sxs-lookup"><span data-stu-id="4ea71-132">Indicates that *target_recovery_time* is expressed as the number of seconds.</span></span>  
  
     <span data-ttu-id="4ea71-133">MINUTES</span><span class="sxs-lookup"><span data-stu-id="4ea71-133">MINUTES</span></span>  
     <span data-ttu-id="4ea71-134">指示 *target_recovery_time* 表示为分钟数。</span><span class="sxs-lookup"><span data-stu-id="4ea71-134">Indicates that *target_recovery_time* is expressed as the number of minutes.</span></span>  
  
     <span data-ttu-id="4ea71-135">以下示例将 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库的目标恢复时间设置为 `60` 秒。</span><span class="sxs-lookup"><span data-stu-id="4ea71-135">The following example sets the target recovery time of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to `60` seconds.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET TARGET_RECOVERY_TIME = 60 SECONDS;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4ea71-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ea71-136">See Also</span></span>  
 <span data-ttu-id="4ea71-137">[数据库检查点 (SQL Server)](database-checkpoints-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4ea71-137">[Database Checkpoints &#40;SQL Server&#41;](database-checkpoints-sql-server.md) </span></span>  
 [<span data-ttu-id="4ea71-138">ALTER DATABASE SET 选项 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4ea71-138">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
