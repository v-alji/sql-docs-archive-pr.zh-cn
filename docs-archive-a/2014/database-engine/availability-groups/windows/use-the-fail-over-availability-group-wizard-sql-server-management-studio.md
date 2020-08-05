---
title: 使用故障转移可用性组向导 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.failoverwizard.progress.f1
- sql12.swb.failoverwizard.f1
- sql12.swb.failoverwizard.selectnewprimary.f1
- sql12.swb.failoverwizard.confirmdataloss.f1
- sql12.swb.failoverwizard.connecttoreplicas.f1
helpviewer_keywords:
- failover [SQL Server], failover
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], configuring
ms.assetid: 4a602584-63e4-4322-aafc-5d715b82b834
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bd059712aae9c23ebbda107370ad112d7917cd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580376"
---
# <a name="use-the-fail-over-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="8f3d0-102">使用故障转移可用性组向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="8f3d0-102">Use the Fail Over Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="8f3d0-103">本主题介绍如何在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 PowerShell 来对 AlwaysOn 可用性组执行计划的手动故障转移或强制的手动故障转移（强制故障转移）。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-103">This topic describes how to perform a planned manual failover or forced manual failover (forced failover) on an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="8f3d0-104">可用性组在可用性副本级别进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-104">An availability group fails over at the level of an availability replica.</span></span> <span data-ttu-id="8f3d0-105">如果故障转移到一个处于 SYNCHRONIZED 状态的辅助副本，则向导将执行计划的手动故障转移（不会造成数据丢失）。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-105">If you fail over to a secondary replica in the SYNCHRONIZED state, the wizard performs a planned manual failover (without data loss).</span></span> <span data-ttu-id="8f3d0-106">如果故障转移到一个处于 UNSYNCHRONIZED 或 NOT SYNCHRONIZING 状态的次要副本，则向导将执行强制的手动故障转移（这也称为“强制故障转移”，可能造成数据丢失）。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-106">If you fail over to a secondary replica in the UNSYNCHRONIZED or NOT SYNCHRONIZING state, the wizard performs a forced manual failover-also known as a *forced failover* (with possible data loss).</span></span> <span data-ttu-id="8f3d0-107">这两种形式的手动故障转移均会将您所连接的辅助副本转换为主角色。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-107">Both forms of manual failover transition the secondary replica to which you are connected to the primary role.</span></span> <span data-ttu-id="8f3d0-108">计划的手动故障转移当前会将先前的主副本转换为辅助角色。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-108">A planned manual failover currently transitions the former primary replica to the secondary role.</span></span> <span data-ttu-id="8f3d0-109">在强制故障转移之后，一旦先前的主副本联机，它就会转换为辅助角色。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-109">After a forced failover, when the former primary replica comes online, it transitions to the secondary role.</span></span>  
  


  
-   <span data-ttu-id="8f3d0-110">**[!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]页**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-110">**[!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)] pages:**</span></span>  
  
     <span data-ttu-id="8f3d0-111">[“选择新主要副本”页](#SelectNewPrimaryReplica) （将在本主题的后面介绍）</span><span class="sxs-lookup"><span data-stu-id="8f3d0-111">[Select New Primary Replica page](#SelectNewPrimaryReplica) (later in this topic)</span></span>  
  
     <span data-ttu-id="8f3d0-112">[“连接到副本”页](#ConnectToReplica) （将在本主题的后面介绍）</span><span class="sxs-lookup"><span data-stu-id="8f3d0-112">[Connect to Replica page](#ConnectToReplica) (later in this topic)</span></span>  
  
     <span data-ttu-id="8f3d0-113">“确认可能丢失数据”页[](#ConfirmPotentialDataLoss) （将在本主题的后面介绍）</span><span class="sxs-lookup"><span data-stu-id="8f3d0-113">[Confirm Potential Data Loss page](#ConfirmPotentialDataLoss) (later in this topic)</span></span>  
  
     [<span data-ttu-id="8f3d0-114">&#40;AlwaysOn 可用性组向导的 "摘要" 页&#41;</span><span class="sxs-lookup"><span data-stu-id="8f3d0-114">Summary Page &#40;AlwaysOn Availability Group Wizards&#41;</span></span>](summary-page-always-on-availability-group-wizards.md)  
  
     [<span data-ttu-id="8f3d0-115">AlwaysOn 可用性组向导&#41;的进度页 &#40;</span><span class="sxs-lookup"><span data-stu-id="8f3d0-115">Progress Page &#40;AlwaysOn Availability Group Wizards&#41;</span></span>](progress-page-always-on-availability-group-wizards.md)  
  
     [<span data-ttu-id="8f3d0-116">&#40;AlwaysOn 可用性组向导&#41;的结果页</span><span class="sxs-lookup"><span data-stu-id="8f3d0-116">Results Page &#40;AlwaysOn Availability Group Wizards&#41;</span></span>](results-page-always-on-availability-group-wizards.md)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8f3d0-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="8f3d0-117">Before You Begin</span></span>  
 <span data-ttu-id="8f3d0-118">在你首次执行计划的手动故障转移之前，请参阅 [执行可用性组的计划手动故障转移 (SQL Server)](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)或 PowerShell 来对 AlwaysOn 可用性组执行计划的手动故障转移或强制的手动故障转移（强制故障转移）。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-118">Before your first planned manual failover, see the "Before You Begin" section in [Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="8f3d0-119">在首次强制故障转移之前，请参阅“开始之前”和“跟进：强制故障转移之后的重要任务”部分，位于[执行可用性组的强制手动故障转移 &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) 中。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-119">Before your first forced failover, see the "Before You Begin" and "Follow Up: Essential Tasks After a Forced Failover" sections in [Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8f3d0-120">限制和局限</span><span class="sxs-lookup"><span data-stu-id="8f3d0-120">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="8f3d0-121">故障转移命令将在目标辅助副本接受它之后立即返回。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-121">A failover command returns as soon as the target secondary replica has accepted the command.</span></span> <span data-ttu-id="8f3d0-122">但是，在可用性组完成故障转移之后，数据库恢复操作将以异步方式执行。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-122">However, database recovery occurs asynchronously after the availability group has finished failing over.</span></span>  
  
-   <span data-ttu-id="8f3d0-123">故障转移时，不维护可用性组中数据库间的跨数据库一致性。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-123">Cross-database consistency across databases within the availability group is not maintained on failover.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8f3d0-124">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 不支持跨数据库事务和分布式事务。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-124">Cross-database transactions and distributed transactions are not supported by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="8f3d0-125">有关详细信息，请参阅[数据库镜像或 AlwaysOn 可用性组不支持跨数据库事务 (SQL Server)](transactions-always-on-availability-and-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-125">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
###  <a name="prerequisites-for-using-the-failover-availability-group-wizard"></a><a name="Prerequisites"></a> <span data-ttu-id="8f3d0-126">使用“故障转移可用性组向导”的先决条件</span><span class="sxs-lookup"><span data-stu-id="8f3d0-126">Prerequisites for Using the Failover Availability Group Wizard</span></span>  
  
-   <span data-ttu-id="8f3d0-127">必须连接到承载当前可用的可用性副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-127">You must be connected to the server instance that hosts an availability replica that is currently available.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8f3d0-128">Security</span><span class="sxs-lookup"><span data-stu-id="8f3d0-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8f3d0-129">权限</span><span class="sxs-lookup"><span data-stu-id="8f3d0-129">Permissions</span></span>  
 <span data-ttu-id="8f3d0-130">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-130">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8f3d0-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8f3d0-131">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="8f3d0-132">**使用“故障转移可用性组向导”**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-132">**To Use the Failover Availability Group Wizard**</span></span>  
  
1.  <span data-ttu-id="8f3d0-133">在对象资源管理器中，连接到承载需要进行故障转移的可用性组的辅助副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-133">In Object Explorer, connect to the server instance that hosts a secondary replica of the availability group that needs to be failed over, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="8f3d0-134">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-134">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="8f3d0-135">若要启动故障转移可用性组向导，请右键单击你要进行故障转移的可用性组，然后选择“故障转移”。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-135">To launch the Failover Availability Group Wizard, right-click the availability group that you are going to fail over, and select **Failover**.</span></span>  
  
4.  <span data-ttu-id="8f3d0-136">**“简介”** 页面所显示的信息取决于是否有任何辅助副本可用于计划的故障转移。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-136">The information presented by the **Introduction** page depends on whether any secondary replica is eligible for a planned failover.</span></span> <span data-ttu-id="8f3d0-137">如果此页面显示“**执行此可用性组的计划故障转移**”，则您可在不造成数据丢失的情况下对可用性组进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-137">If this page says, "**Perform a planned failover for this availability group**", you can failover the availability group without data loss.</span></span>  
  
5.  <span data-ttu-id="8f3d0-138">在“选择新主要副本”页上，在你选择将成为新的主要副本的次要副本（即故障转移目标）之前，你可查看当前主要副本和 WSFC 仲裁的状态。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-138">On the **Select New Primary Replica** page, you can view the status of the current primary replica and of the WSFC quorum, before you choose the secondary replica that will become the new primary replica (the *failover target*).</span></span> <span data-ttu-id="8f3d0-139">对于计划的手动故障转移，确保选择其 **“故障转移就绪”** 值为“**无数据丢失**”的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-139">For a planned manual failover, be sure to select a secondary replica whose **Failover Readiness** value is "**No data loss**".</span></span> <span data-ttu-id="8f3d0-140">对于强制故障转移，对于所有可能的故障转移目标，此值将为 "\*\*数据丢失，警告 (***#***) \*\*"，其中 *#* 指示给定辅助副本存在的警告数。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-140">For a forced failover, for all the possible failover targets, this value will be "**Data loss, Warnings(***#***)**", where *#* indicates the number of warnings that exist for a given secondary replica.</span></span> <span data-ttu-id="8f3d0-141">若要查看给定故障转移目标的警告，请单击其“故障转移就绪”值。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-141">To view the warnings for a given failover target, click its "Failover Readiness" value.</span></span>  
  
     <span data-ttu-id="8f3d0-142">有关详细信息，请参阅本主题后面的 [“选择新主副本”页](#SelectNewPrimaryReplica)。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-142">For more information, see [Select New Primary Replica page](#SelectNewPrimaryReplica), later in this topic.</span></span>  
  
6.  <span data-ttu-id="8f3d0-143">在 **“连接到副本”** 页上，连接到故障转移目标。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-143">On the **Connect to Replica** page,  connect to the failover target.</span></span> <span data-ttu-id="8f3d0-144">有关详细信息，请参阅本主题后面的 [“连接到副本”页](#ConnectToReplica)。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-144">For more information, see [Connect to Replica page](#ConnectToReplica), later in this topic.</span></span>  
  
7.  <span data-ttu-id="8f3d0-145">如果您正在执行强制故障转移，则向导将显示 **“确认可能丢失数据”** 页。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-145">If you are performing a forced failover, the wizard displays the **Confirm Potential Data Loss** page.</span></span> <span data-ttu-id="8f3d0-146">若要继续执行故障转移，则必须选择 **“单击此处以确认故障转移可能丢失数据”** 。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-146">To proceed with the failover, you must select **Click here to confirm failover with potential data loss**.</span></span> <span data-ttu-id="8f3d0-147">有关详细信息，请参阅本主题后面的[“确认可能丢失数据”页](#ConfirmPotentialDataLoss)。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-147">For more information, see .[Confirm Potential Data Loss page](#ConfirmPotentialDataLoss), later in this topic.</span></span>  
  
8.  <span data-ttu-id="8f3d0-148">在 **“摘要”** 页上，查看故障转移到选定的辅助副本的含义。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-148">On the **Summary** page, review the implications of failing over to the selected secondary replica.</span></span>  
  
     <span data-ttu-id="8f3d0-149">如果您满意所做的选择，可以选择单击 **“脚本”** 以创建向导将执行的步骤的脚本。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-149">If you are satisfied with your selections, optionally click **Script** to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="8f3d0-150">然后，若要将可用性组故障转移到选定的辅助副本，请单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-150">Then, to failover the availability group to the selected secondary replica, click **Finish**.</span></span>  
  
9. <span data-ttu-id="8f3d0-151">**“进度”** 页将显示对可用性组进行故障转移的进度。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-151">The **Progress** page displays the progress of failing over the availability group.</span></span>  
  
10. <span data-ttu-id="8f3d0-152">当故障转移操作完成之后， **“结果”** 页将显示结果。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-152">When the failover operation finishes, the **Results** page displays the result.</span></span> <span data-ttu-id="8f3d0-153">完成向导后，单击 **“关闭”** 以退出安装向导。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-153">When the wizard completes, click **Close** to exit.</span></span>  
  
     <span data-ttu-id="8f3d0-154">有关详细信息，请参阅[“结果”页（AlwaysOn 可用性组向导）](results-page-always-on-availability-group-wizards.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-154">For more information, see [Results Page &#40;AlwaysOn Availability Group Wizards&#41;](results-page-always-on-availability-group-wizards.md).</span></span>  
  
11. <span data-ttu-id="8f3d0-155">强制故障转移后，请参阅“跟进：强制故障转移之后”部分，位于[执行可用性组的强制手动故障转移 &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) 中。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-155">After a forced failover, see the "Follow Up: After a Forced Failover" section in the [Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
## <a name="help-for-pages-that-are-exclusive-to-this-wizard"></a><span data-ttu-id="8f3d0-156">有关此向导独有的页面的帮助</span><span class="sxs-lookup"><span data-stu-id="8f3d0-156">Help for Pages that are Exclusive to This Wizard</span></span>  
 <span data-ttu-id="8f3d0-157">本节介绍 [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]独有的页面。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-157">This section describes the pages that are unique to the [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)].</span></span>  
  
 
  
 <span data-ttu-id="8f3d0-158">此向导的其他页面与一个或多个其他 AlwaysOn 可用性组向导共享帮助，并且在不同的 F1 帮助主题中进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-158">The other pages of this wizard share help with one or more of the other AlwaysOn Availability Groups wizards and are documented in separate F1 help topics.</span></span>  
  
###  <a name="select-new-primary-replica-page"></a><a name="SelectNewPrimaryReplica"></a> <span data-ttu-id="8f3d0-159">Select New Primary Replica Page</span><span class="sxs-lookup"><span data-stu-id="8f3d0-159">Select New Primary Replica Page</span></span>  
 <span data-ttu-id="8f3d0-160">本节介绍 **“选择新主副本”** 页的选项。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-160">This section describes the options of the **Select New Primary Replica** page.</span></span> <span data-ttu-id="8f3d0-161">可使用此页选择可用性组将要故障转移到的辅助副本（即“故障转移目标”）。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-161">Use this page to select the secondary replica (failover target) to which the availability group will fail over.</span></span> <span data-ttu-id="8f3d0-162">此副本将成为新的主副本。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-162">This replica will become the new primary replica.</span></span>  
  
#### <a name="page-options"></a><span data-ttu-id="8f3d0-163">页选项</span><span class="sxs-lookup"><span data-stu-id="8f3d0-163">Page Options</span></span>  
 <span data-ttu-id="8f3d0-164">**当前主副本**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-164">**Current Primary Replica**</span></span>  
 <span data-ttu-id="8f3d0-165">显示当前主副本的名称（如果它处于联机状态的话）。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-165">Displays the name of the current primary replica, if it is online.</span></span>  
  
 <span data-ttu-id="8f3d0-166">**主副本状态**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-166">**Primary Replica Status**</span></span>  
 <span data-ttu-id="8f3d0-167">显示当前主副本的状态（如果它处于联机状态的话）。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-167">Displays the status of the current primary replica, if it is online.</span></span>  
  
 <span data-ttu-id="8f3d0-168">**仲裁状态**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-168">**Quorum Status**</span></span>  
 <span data-ttu-id="8f3d0-169">显示可用性副本的以下 WSFC 仲裁状态之一：</span><span class="sxs-lookup"><span data-stu-id="8f3d0-169">Displays the WSFC quorum status for the availability replica, one of:</span></span>  
  
|<span data-ttu-id="8f3d0-170">值</span><span class="sxs-lookup"><span data-stu-id="8f3d0-170">Value</span></span>|<span data-ttu-id="8f3d0-171">说明</span><span class="sxs-lookup"><span data-stu-id="8f3d0-171">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f3d0-172">**标准仲裁**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-172">**Normal quorum**</span></span>|<span data-ttu-id="8f3d0-173">群集已开始标准仲裁。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-173">The cluster has started with normal quorum.</span></span>|  
|<span data-ttu-id="8f3d0-174">**强制仲裁 (Forced quorum)**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-174">**Forced quorum**</span></span>|<span data-ttu-id="8f3d0-175">群集已开始强制仲裁。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-175">The cluster has started with forced quorum.</span></span>|  
|<span data-ttu-id="8f3d0-176">**未知仲裁**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-176">**Unknown quorum**</span></span>|<span data-ttu-id="8f3d0-177">群集仲裁状态不可用。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-177">The cluster quorum status is unavailable.</span></span>|  
|<span data-ttu-id="8f3d0-178">**不适用**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-178">**Not applicable**</span></span>|<span data-ttu-id="8f3d0-179">承载可用性副本的节点不包含任何仲裁。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-179">The node that hosts the availability replica has no quorum.</span></span>|  
  
 <span data-ttu-id="8f3d0-180">有关详细信息，请参阅 [WSFC 仲裁模式和投票配置 (SQL Server)](../../../sql-server/failover-clusters/windows/wsfc-quorum-modes-and-voting-configuration-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-180">For more information, see [WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-quorum-modes-and-voting-configuration-sql-server.md).</span></span>  
  
 <span data-ttu-id="8f3d0-181">**选择新主副本**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-181">**Choose a new primary replica**</span></span>  
 <span data-ttu-id="8f3d0-182">可使用此网格选择一个将成为新的主副本的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-182">Use this grid to select a secondary replica to become the new primary replica.</span></span> <span data-ttu-id="8f3d0-183">此网格中的列如下所示：</span><span class="sxs-lookup"><span data-stu-id="8f3d0-183">The columns in this grid are as follows:</span></span>  
  
 <span data-ttu-id="8f3d0-184">**服务器实例**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-184">**Server Instance**</span></span>  
 <span data-ttu-id="8f3d0-185">显示承载辅助副本的服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-185">Displays the name of a server instance that hosts a secondary replica.</span></span>  
  
 <span data-ttu-id="8f3d0-186">**可用性模式**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-186">**Availability Mode**</span></span>  
 <span data-ttu-id="8f3d0-187">显示服务器实例的以下可用性模式之一：</span><span class="sxs-lookup"><span data-stu-id="8f3d0-187">Displays the availability mode of the server instance, one of:</span></span>  
  
|<span data-ttu-id="8f3d0-188">值</span><span class="sxs-lookup"><span data-stu-id="8f3d0-188">Value</span></span>|<span data-ttu-id="8f3d0-189">说明</span><span class="sxs-lookup"><span data-stu-id="8f3d0-189">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f3d0-190">**同步提交**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-190">**Synchronous commit**</span></span>|<span data-ttu-id="8f3d0-191">在同步提交模式下，在提交事务之前，同步提交主副本要等待同步提交辅助副本确认它已完成硬化日志。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-191">Under synchronous-commit mode, before committing transactions, a synchronous-commit primary replica waits for a synchronous-commit secondary replica to acknowledge that it has finished hardening the log.</span></span> <span data-ttu-id="8f3d0-192">同步提交模式可确保在给定的辅助数据库与主数据库同步时，充分保护已提交的事务。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-192">Synchronous-commit mode ensures that once a given secondary database is synchronized with the primary database, committed transactions are fully protected.</span></span>|  
|<span data-ttu-id="8f3d0-193">**异步提交**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-193">**Asynchronous commit**</span></span>|<span data-ttu-id="8f3d0-194">在异步提交模式下，主副本无需等待确认异步提交辅助副本已硬化日志，便可提交事务。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-194">Under asynchronous-commit mode, the primary replica commits transactions without waiting for acknowledgement that an asynchronous-commit secondary replica has hardened the log.</span></span> <span data-ttu-id="8f3d0-195">异步提交模式可最大限度地减少辅助数据库上的事务滞后时间，但允许它们滞后于主数据库，因此可能会导致某些数据丢失。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-195">Asynchronous-commit mode minimizes transaction latency on the secondary databases but allows them to lag behind the primary databases, making some data loss possible.</span></span>|  
  
 <span data-ttu-id="8f3d0-196">有关详细信息，请参阅[可用性模式 (AlwaysOn 可用性组) ](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-196">For more information, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="8f3d0-197">**故障转移模式**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-197">**Failover Mode**</span></span>  
 <span data-ttu-id="8f3d0-198">显示服务器实例的以下故障转移模式之一：</span><span class="sxs-lookup"><span data-stu-id="8f3d0-198">Displays the failover mode of the server instance, one of:</span></span>  
  
|<span data-ttu-id="8f3d0-199">值</span><span class="sxs-lookup"><span data-stu-id="8f3d0-199">Value</span></span>|<span data-ttu-id="8f3d0-200">说明</span><span class="sxs-lookup"><span data-stu-id="8f3d0-200">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f3d0-201">**自动**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-201">**Automatic**</span></span>|<span data-ttu-id="8f3d0-202">只要辅助副本与主副本进行同步，配置为进行自动故障转移的辅助副本也会支持计划的手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-202">A secondary replica that is configured for automatic failover also supports planned manual failover whenever the secondary replica is synchronized with the primary replica.</span></span>|  
|<span data-ttu-id="8f3d0-203">**手动**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-203">**Manual**</span></span>|<span data-ttu-id="8f3d0-204">存在两种类型的手动故障转移：计划的（不会造成数据丢失）和强制的（可能造成数据丢失）。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-204">Two types of manual failover exist: planned (without data loss) and forced (with possible data loss).</span></span> <span data-ttu-id="8f3d0-205">对于给定的辅助副本，仅支持这两种类型中的一种，具体取决于可用性模式，而对于同步提交模式，则取决于辅助副本的同步状态。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-205">For a given secondary replica, only one of these is supported, depending on the availability mode and, for synchronous-commit mode, the synchronization state of the secondary replica.</span></span> <span data-ttu-id="8f3d0-206">若要确定给定的辅助副本当前所支持的手动故障转移的形式，请参阅此网格的 **“故障转移就绪”** 列。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-206">To determine which form of manual failover is currently supported by a given secondary replica, see the **Failover Readiness** column of this grid.</span></span>|  
  
 <span data-ttu-id="8f3d0-207">有关详细信息，请参阅[故障转移和故障转移模式（AlwaysOn 可用性组）](failover-and-failover-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-207">For more information, see [Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="8f3d0-208">**“故障转移就绪”**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-208">**Failover Readiness**</span></span>  
 <span data-ttu-id="8f3d0-209">显示辅助副本的以下故障转移就绪情况之一：</span><span class="sxs-lookup"><span data-stu-id="8f3d0-209">Displays failover readiness of the secondary replica, one of:</span></span>  
  
|<span data-ttu-id="8f3d0-210">值</span><span class="sxs-lookup"><span data-stu-id="8f3d0-210">Value</span></span>|<span data-ttu-id="8f3d0-211">说明</span><span class="sxs-lookup"><span data-stu-id="8f3d0-211">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f3d0-212">**无数据丢失**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-212">**No data loss**</span></span>|<span data-ttu-id="8f3d0-213">此辅助副本当前支持计划的故障转移。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-213">This secondary replica currently supports planned failover.</span></span> <span data-ttu-id="8f3d0-214">只有当同步提交模式的辅助副本当前与主副本进行同步时，才会出现此值。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-214">This value occurs only when a synchronous-commit mode secondary replica is currently synchronized with the primary replica.</span></span>|  
|<span data-ttu-id="8f3d0-215">**数据丢失，警告(** *#* **)**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-215">**Data loss, Warnings(** *#* **)**</span></span>|<span data-ttu-id="8f3d0-216">此辅助副本当前支持强制故障转移（可能造成数据丢失）。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-216">This secondary replica currently supports forced failover (with possible data loss).</span></span> <span data-ttu-id="8f3d0-217">只要辅助副本不与主副本进行同步，就会出现此值。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-217">This value occurs whenever the secondary replica is not synchronized with the primary replica.</span></span> <span data-ttu-id="8f3d0-218">有关可能的数据丢失的信息，请单击数据丢失警告链接。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-218">Click the data-loss warnings link for information about the possible data loss.</span></span>|  
  
 <span data-ttu-id="8f3d0-219">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-219">**Refresh**</span></span>  
 <span data-ttu-id="8f3d0-220">单击此按钮可更新网格。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-220">Click to update the grid.</span></span>  
  
 <span data-ttu-id="8f3d0-221">**取消**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-221">**Cancel**</span></span>  
 <span data-ttu-id="8f3d0-222">单击此选项可取消向导操作。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-222">Click to cancel the wizard.</span></span> <span data-ttu-id="8f3d0-223">在 **“选择新主副本”** 页上，取消此向导将会导致其退出而不执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-223">On the **Select New Primary Replica** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  
###  <a name="confirm-potential-data-loss-page"></a><a name="ConfirmPotentialDataLoss"></a> <span data-ttu-id="8f3d0-224">Confirm Potential Data Loss Page</span><span class="sxs-lookup"><span data-stu-id="8f3d0-224">Confirm Potential Data Loss Page</span></span>  
 <span data-ttu-id="8f3d0-225">本节介绍 **“确认可能丢失数据”** 页（只有在执行强制故障转移时才会显示）的选项。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-225">This section describes the options of the **Confirm Potential Data Loss** page, which is displayed only if you are performing a forced failover.</span></span> <span data-ttu-id="8f3d0-226">本主题仅供 [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-226">This topic is used only by the [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)].</span></span> <span data-ttu-id="8f3d0-227">可使用此页指示您是否愿意为强制对可用性组进行故障转移而承担可能造成数据丢失的风险。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-227">Use this page to indicate whether you are willing to risk possible data loss in order to force the availability group to fail over.</span></span>  
  
#### <a name="confirm-potential-data-loss-options"></a><span data-ttu-id="8f3d0-228">“确认可能丢失数据”选项</span><span class="sxs-lookup"><span data-stu-id="8f3d0-228">Confirm Potential Data Loss Options</span></span>  
 <span data-ttu-id="8f3d0-229">如果选定的辅助副本未与主副本进行同步，则向导将显示警告，指出故障转移到此辅助副本可能造成一个或多个数据库上的数据丢失。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-229">If the selected secondary replica is not synchronized with the primary replica, the wizard displays a warning that failing over to this secondary replica could cause data loss on one or more databases.</span></span>  
  
 <span data-ttu-id="8f3d0-230">**单击此处以确认故障转移可能丢失数据。**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-230">**Click here to confirm failover with potential data loss.**</span></span>  
 <span data-ttu-id="8f3d0-231">如果您愿意为了使此可用性组中的数据库对用户可用而承担数据丢失的风险，则单击此复选框。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-231">If you are willing to risk data loss in order to make the databases in this availability group available to users, click this checkbox.</span></span> <span data-ttu-id="8f3d0-232">如果您不愿意承担数据丢失的风险，则可单击 **“上一步”** 返回到 **“选择新主副本”** 页，或单击 **“取消”** 以退出向导，而不对可用性组进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-232">If you are not willing to risk data loss, you can either click **Previous** to return to the **Select New Primary Replica** page, or click **Cancel** to exit the wizard without failing over the availability group.</span></span>  
  
 <span data-ttu-id="8f3d0-233">**取消**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-233">**Cancel**</span></span>  
 <span data-ttu-id="8f3d0-234">单击此选项可取消向导操作。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-234">Click to cancel the wizard.</span></span> <span data-ttu-id="8f3d0-235">在 **“确认可能丢失数据”** 页上，取消此向导将导致其退出而不执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-235">On the **Confirm Potential Data Loss** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  
###  <a name="connect-to-replica-page"></a><a name="ConnectToReplica"></a> <span data-ttu-id="8f3d0-236">Connect to Replica Page</span><span class="sxs-lookup"><span data-stu-id="8f3d0-236">Connect to Replica Page</span></span>  
 <span data-ttu-id="8f3d0-237">本节介绍 **的** “连接到副本” [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]页的选项。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-237">This section describes the options of the **Connect to Replica** page of the [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)].</span></span> <span data-ttu-id="8f3d0-238">只有当您尚未连接到目标辅助副本时才会显示此页。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-238">This page is displayed only if you are not connected to the target secondary replica.</span></span> <span data-ttu-id="8f3d0-239">可使用此页连接到您已选择作为新的主副本的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-239">Use this page to connect to the secondary replica that you have selected as the new primary replica.</span></span>  
  
#### <a name="page-options"></a><span data-ttu-id="8f3d0-240">页选项</span><span class="sxs-lookup"><span data-stu-id="8f3d0-240">Page Options</span></span>  
 <span data-ttu-id="8f3d0-241">**网格列：**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-241">**Grid columns:**</span></span>  
 <span data-ttu-id="8f3d0-242">**服务器实例**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-242">**Server Instance**</span></span>  
 <span data-ttu-id="8f3d0-243">显示将承载可用性副本的服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-243">Displays the name of the server instance that will host the availability replica.</span></span>  
  
 <span data-ttu-id="8f3d0-244">**连接为**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-244">**Connected As**</span></span>  
 <span data-ttu-id="8f3d0-245">显示在建立了连接后连接到服务器实例的帐户。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-245">Displays the account that is connected to the server instance, once the connection has been established.</span></span> <span data-ttu-id="8f3d0-246">如果对于给定的服务器实例此列显示“**未连接**”，则您将需要单击 **“连接”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-246">If this column displays "**Not Connected**" for a given server instance, you will need to click the **Connect** button.</span></span>  
  
 <span data-ttu-id="8f3d0-247">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-247">**Connect**</span></span>  
 <span data-ttu-id="8f3d0-248">如果此服务器实例正基于与您将需要连接到的其他服务器实例不同的帐户运行，则单击此选项。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-248">Click if this server instance is running under a different account than other server instances to which you need to connect.</span></span>  
  
 <span data-ttu-id="8f3d0-249">**取消**</span><span class="sxs-lookup"><span data-stu-id="8f3d0-249">**Cancel**</span></span>  
 <span data-ttu-id="8f3d0-250">单击此选项可取消向导操作。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-250">Click to cancel the wizard.</span></span> <span data-ttu-id="8f3d0-251">在 **“连接到副本”** 页上，取消此向导将导致其退出而不执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="8f3d0-251">On the **Connect to Replica** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f3d0-252">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f3d0-252">See Also</span></span>  
 <span data-ttu-id="8f3d0-253">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8f3d0-253">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="8f3d0-254">[可用性模式 (AlwaysOn 可用性组) ](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="8f3d0-254">[Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="8f3d0-255">[故障转移和故障转移模式 &#40;AlwaysOn 可用性组&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="8f3d0-255">[Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="8f3d0-256">[执行可用性组的计划手动故障转移 (SQL Server)](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8f3d0-256">[Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="8f3d0-257">[执行可用性组的强制手动故障转移 (SQL Server)](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8f3d0-257">[Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) </span></span>  
 [<span data-ttu-id="8f3d0-258">通过强制仲裁进行 WSFC 灾难恢复 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8f3d0-258">WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;</span></span>](../../../sql-server/failover-clusters/windows/wsfc-disaster-recovery-through-forced-quorum-sql-server.md)  
  
  
