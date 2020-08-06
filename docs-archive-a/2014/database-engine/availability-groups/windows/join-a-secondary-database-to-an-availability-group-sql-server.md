---
title: 将辅助数据库联接到可用性组 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.joindbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: fd7efe79-c1f9-497d-bfe7-b2a2b2321cf5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0d79325bcde33d13688003de079a42a9601cc41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585967"
---
# <a name="join-a-secondary-database-to-an-availability-group-sql-server"></a><span data-ttu-id="b2407-102">将辅助数据库联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b2407-102">Join a Secondary Database to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="b2407-103">本主题说明如何通过在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell 来将辅助数据库联接到 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="b2407-103">This topic explains how to join a secondary database to an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b2407-104">在您为辅助副本准备了辅助数据库后，需要尽快将该数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="b2407-104">After you prepare a secondary database for a secondary replica, you need to join the database to the availability group as soon as possible.</span></span> <span data-ttu-id="b2407-105">这将启动从相应的主数据库到辅助数据库的数据移动。</span><span class="sxs-lookup"><span data-stu-id="b2407-105">This will start data movement from the corresponding primary database to the secondary database.</span></span>  
  
-   <span data-ttu-id="b2407-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b2407-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b2407-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="b2407-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="b2407-108">安全性</span><span class="sxs-lookup"><span data-stu-id="b2407-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b2407-109">**若要准备辅助数据库，请使用：**</span><span class="sxs-lookup"><span data-stu-id="b2407-109">**To prepare a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="b2407-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b2407-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b2407-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b2407-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="b2407-112">PowerShell</span><span class="sxs-lookup"><span data-stu-id="b2407-112">PowerShell</span></span>](#PowerShellProcedure)  
  
> [!NOTE]  
>  <span data-ttu-id="b2407-113">有关辅助数据库加入组后会发生的情况的信息，请参阅[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b2407-113">For information about what happens after a secondary database joins the group, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b2407-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="b2407-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="b2407-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="b2407-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="b2407-116">您必须连接到承载辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b2407-116">You must be connected to the server instance that hosts the secondary replica.</span></span>  
  
-   <span data-ttu-id="b2407-117">该辅助副本必须已联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="b2407-117">The secondary replica must already be joined to the availability group.</span></span> <span data-ttu-id="b2407-118">有关详细信息，请参阅 [将辅助副本联接到可用性组 (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="b2407-118">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
-   <span data-ttu-id="b2407-119">辅助数据库必须已在最近进行了准备。</span><span class="sxs-lookup"><span data-stu-id="b2407-119">The secondary database must have been prepared recently.</span></span> <span data-ttu-id="b2407-120">有关详细信息，请参阅 [为可用性组手动准备辅助数据库 (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="b2407-120">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b2407-121">Security</span><span class="sxs-lookup"><span data-stu-id="b2407-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b2407-122">权限</span><span class="sxs-lookup"><span data-stu-id="b2407-122">Permissions</span></span>  
 <span data-ttu-id="b2407-123">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="b2407-123">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b2407-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b2407-124">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="b2407-125">**将辅助数据库联接到可用性组**</span><span class="sxs-lookup"><span data-stu-id="b2407-125">**To join a secondary database to an availability group**</span></span>  
  
1.  <span data-ttu-id="b2407-126">在对象资源管理器中，连接到承载辅助副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="b2407-126">In Object Explorer, connect to the server instance that hosts the secondary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="b2407-127">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="b2407-127">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="b2407-128">展开您要更改的可用性组，然后展开 **“可用性数据库”** 节点。</span><span class="sxs-lookup"><span data-stu-id="b2407-128">Expand the availability group that you want to change, and expand the **Availability Databases** node.</span></span>  
  
4.  <span data-ttu-id="b2407-129">右键单击数据库，然后单击\*\*\*\*“联接到可用性组”。</span><span class="sxs-lookup"><span data-stu-id="b2407-129">Right-click the database, and click **Join to Availability Group**.</span></span>  
  
5.  <span data-ttu-id="b2407-130">这将打开 **“将数据库联接到可用性组”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="b2407-130">This opens the **Join Databases to Availability Group** dialog box.</span></span> <span data-ttu-id="b2407-131">验证在标题栏上显示的可用性组名称以及在网格中显示的数据库名称，然后单击 **“确定”** 或单击 **“取消”**。</span><span class="sxs-lookup"><span data-stu-id="b2407-131">Verify the availability group name, which is displayed on the title bar, and database name or names displayed in the grid, and click **OK**, or click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b2407-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b2407-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="b2407-133">**将辅助数据库联接到可用性组**</span><span class="sxs-lookup"><span data-stu-id="b2407-133">**To join a secondary database to an availability group**</span></span>  
  
1.  <span data-ttu-id="b2407-134">连接到承载辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b2407-134">Connect to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="b2407-135">使用 [ALTER DATABASE 语句的 SET HADR 子句](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) ，如下所述：</span><span class="sxs-lookup"><span data-stu-id="b2407-135">Use the [SET HADR clause of the ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) statement, as follows:</span></span>  
  
     <span data-ttu-id="b2407-136">ALTER DATABASE *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span><span class="sxs-lookup"><span data-stu-id="b2407-136">ALTER DATABASE *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span></span>  
  
     <span data-ttu-id="b2407-137">其中 *database_name* 是要联接的数据库名， *group_name* 是可用性组名。</span><span class="sxs-lookup"><span data-stu-id="b2407-137">where *database_name* is the name of a database to be joined and *group_name* is the name of the availability group.</span></span>  
  
     <span data-ttu-id="b2407-138">下面的示例将辅助数据库 `Db1` 联接到 `MyAG` 可用性组的本地辅助副本。</span><span class="sxs-lookup"><span data-stu-id="b2407-138">The following example joins the secondary database, `Db1`, to the local secondary replica of the `MyAG` availability group.</span></span>  
  
    ```sql
    ALTER DATABASE Db1 SET HADR AVAILABILITY GROUP = MyAG;  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="b2407-139">若要查看此用于上下文的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句，请参阅[创建可用性组 (Transact-SQL)](create-an-availability-group-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="b2407-139">To see this [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement used in context, see [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="b2407-140">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b2407-140">Using PowerShell</span></span>  
 <span data-ttu-id="b2407-141">**将辅助数据库联接到可用性组**</span><span class="sxs-lookup"><span data-stu-id="b2407-141">**To join a secondary database to an availability group**</span></span>  
  
1.  <span data-ttu-id="b2407-142">切换目录 (`cd`) 到承载辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b2407-142">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="b2407-143">使用 `Add-SqlAvailabilityDatabase` cmdlet 将一个或多个辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="b2407-143">Use the `Add-SqlAvailabilityDatabase` cmdlet to join one or more secondary databases to the availability group.</span></span>  
  
     <span data-ttu-id="b2407-144">例如，以下命令将辅助数据库 `Db1`联接到一个承载辅助副本的服务器实例上的可用性组 `MyAG` 。</span><span class="sxs-lookup"><span data-stu-id="b2407-144">For example, the following command joins a secondary database, `Db1`, to the availability group `MyAG` on one of the server instances that hosts a secondary replica.</span></span>  
  
    ```powershell
    Add-SqlAvailabilityDatabase -Path SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAG -Database "Db1"  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="b2407-145">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b2407-145">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="b2407-146">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="b2407-146">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="b2407-147">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="b2407-147">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="b2407-148">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="b2407-148">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b2407-149">相关任务</span><span class="sxs-lookup"><span data-stu-id="b2407-149">Related Tasks</span></span>  
  
-   [<span data-ttu-id="b2407-150">将辅助副本联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b2407-150">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="b2407-151">为可用性组手动准备辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b2407-151">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="b2407-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2407-152">See Also</span></span>  
 <span data-ttu-id="b2407-153">[ALTER AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/alter-availability-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b2407-153">[ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) </span></span>  
 <span data-ttu-id="b2407-154">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b2407-154">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="b2407-155">&#41;删除 AlwaysOn 可用性组配置 &#40;SQL Server 的疑难解答</span><span class="sxs-lookup"><span data-stu-id="b2407-155">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
