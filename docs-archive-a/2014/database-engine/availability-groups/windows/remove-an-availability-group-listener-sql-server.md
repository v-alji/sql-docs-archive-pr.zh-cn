---
title: 删除可用性组侦听程序 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removeaglistener.default.f1
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
ms.assetid: fd9bba9a-d29f-4c23-8ecd-aaa049ed5f1b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 057b9c137cb4d8bbbdd03be61df600f7e59b264c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579798"
---
# <a name="remove-an-availability-group-listener-sql-server"></a><span data-ttu-id="6e971-102">删除可用性组侦听器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6e971-102">Remove an Availability Group Listener (SQL Server)</span></span>
  <span data-ttu-id="6e971-103">本主题说明如何通过在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell 从 AlwaysOn 可用性组中删除可用性组侦听器。</span><span class="sxs-lookup"><span data-stu-id="6e971-103">This topic describes how to remove an availability group listener from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="6e971-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="6e971-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6e971-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="6e971-105">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="6e971-106">建议</span><span class="sxs-lookup"><span data-stu-id="6e971-106">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="6e971-107">安全性</span><span class="sxs-lookup"><span data-stu-id="6e971-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6e971-108">**删除侦听器，使用：**</span><span class="sxs-lookup"><span data-stu-id="6e971-108">**To remove a listener, using:**</span></span>  
  
     [<span data-ttu-id="6e971-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6e971-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6e971-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6e971-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="6e971-111">PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e971-111">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6e971-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="6e971-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="6e971-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="6e971-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="6e971-114">您必须连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="6e971-114">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="6e971-115">建议</span><span class="sxs-lookup"><span data-stu-id="6e971-115">Recommendations</span></span>  
 <span data-ttu-id="6e971-116">在删除可用性组侦听器之前，我们建议您确保没有任何应用程序在使用它。</span><span class="sxs-lookup"><span data-stu-id="6e971-116">Before you delete an availability group listener, we recommend that you ensure that no applications are using it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6e971-117">Security</span><span class="sxs-lookup"><span data-stu-id="6e971-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6e971-118">权限</span><span class="sxs-lookup"><span data-stu-id="6e971-118">Permissions</span></span>  
 <span data-ttu-id="6e971-119">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="6e971-119">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6e971-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6e971-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="6e971-121">**删除可用性组侦听器**</span><span class="sxs-lookup"><span data-stu-id="6e971-121">**To remove an availability group listener**</span></span>  
  
1.  <span data-ttu-id="6e971-122">在对象资源管理器中，连接到承载主副本的服务器实例，然后单击服务器名称以便展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="6e971-122">In Object Explorer, connect to the server instance that hosts the primary replica, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="6e971-123">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="6e971-123">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="6e971-124">展开可用性组节点，然后展开 **“可用性组侦听器”** 节点。</span><span class="sxs-lookup"><span data-stu-id="6e971-124">Expand the node of the availability group, and expand the **Availability Groups Listeners** node.</span></span>  
  
4.  <span data-ttu-id="6e971-125">右键单击要删除的侦听器，然后选择 **“删除”** 命令。</span><span class="sxs-lookup"><span data-stu-id="6e971-125">Right-click the listener to be removed, and select the **Delete** command.</span></span>  
  
5.  <span data-ttu-id="6e971-126">这将打开 **“从可用性组中删除侦听器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="6e971-126">This opens the **Remove Listener from Availability Group** dialog box.</span></span> <span data-ttu-id="6e971-127">有关详细信息，请参阅本主题后面的 [从可用性组中删除侦听器](#AgListenerPropertiesDialog)。</span><span class="sxs-lookup"><span data-stu-id="6e971-127">For more information, see [Remove Listener from Availability Group](#AgListenerPropertiesDialog), later in this topic.</span></span>  
  
###  <a name="remove-listener-from-availability-group-dialog-box"></a><a name="AgListenerPropertiesDialog"></a><span data-ttu-id="6e971-128">"从可用性组中删除侦听器" (对话框) </span><span class="sxs-lookup"><span data-stu-id="6e971-128">Remove Listener from Availability Group (Dialog Box)</span></span>  
 <span data-ttu-id="6e971-129">**名称**</span><span class="sxs-lookup"><span data-stu-id="6e971-129">**Name**</span></span>  
 <span data-ttu-id="6e971-130">要删除的侦听器的名称。</span><span class="sxs-lookup"><span data-stu-id="6e971-130">The name of the listener to be removed.</span></span>  
  
 <span data-ttu-id="6e971-131">**结果**</span><span class="sxs-lookup"><span data-stu-id="6e971-131">**Result**</span></span>  
 <span data-ttu-id="6e971-132">将显示一个链接，提示 **“成功”** 或 **“错误”**，可单击该链接查看详细信息。</span><span class="sxs-lookup"><span data-stu-id="6e971-132">Displays a link, either **Success** or **Error**, which you can click for more information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6e971-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6e971-133">Using Transact-SQL</span></span>  
 <span data-ttu-id="6e971-134">**删除可用性组侦听器**</span><span class="sxs-lookup"><span data-stu-id="6e971-134">**To remove an availability group listener**</span></span>  
  
1.  <span data-ttu-id="6e971-135">连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="6e971-135">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="6e971-136">按如下所示使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 语句：</span><span class="sxs-lookup"><span data-stu-id="6e971-136">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="6e971-137">更改可用性组*group_name*删除侦听器 **" *`dns_name`* "**</span><span class="sxs-lookup"><span data-stu-id="6e971-137">ALTER AVAILABILITY GROUP *group_name* REMOVE LISTENER **'*`dns_name`*'**</span></span>  
  
     <span data-ttu-id="6e971-138">其中， *group_name* 是可用性组的名称， *dns_name* 是可用性组侦听器的 DNS 名称。</span><span class="sxs-lookup"><span data-stu-id="6e971-138">where *group_name* is the name of the availability group and *dns_name* is the DNS name of the availability group listener.</span></span>  
  
     <span data-ttu-id="6e971-139">下面的示例将删除 `AccountsAG` 可用性组的侦听器。</span><span class="sxs-lookup"><span data-stu-id="6e971-139">The following example deletes the listener of the `AccountsAG` availability group.</span></span> <span data-ttu-id="6e971-140">DNS 名称为 AccountsAG_Listener。</span><span class="sxs-lookup"><span data-stu-id="6e971-140">The DNS name is AccountsAG_Listener.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP AccountsAG REMOVE LISTENER 'AccountsAG_Listener';  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="6e971-141">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e971-141">Using PowerShell</span></span>  
 <span data-ttu-id="6e971-142">**删除可用性组侦听器**</span><span class="sxs-lookup"><span data-stu-id="6e971-142">**To remove an availability group listener**</span></span>  
  
1.  <span data-ttu-id="6e971-143">将默认的 (`cd`) 设置为承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="6e971-143">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="6e971-144">使用内置的 `Remove-Item` cmdlet 来删除侦听器。</span><span class="sxs-lookup"><span data-stu-id="6e971-144">Use the built in `Remove-Item` cmdlet to remove a listener.</span></span> <span data-ttu-id="6e971-145">例如，以下命令从名为 `MyListener` 的可用性组中删除名为 `MyAg`的侦听器。</span><span class="sxs-lookup"><span data-stu-id="6e971-145">For example, the following command removes a listener named `MyListener` from an availability group named `MyAg`.</span></span>  
  
    ```powershell
    Remove-Item SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="6e971-146">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6e971-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="6e971-147">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="6e971-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="6e971-148">相关任务</span><span class="sxs-lookup"><span data-stu-id="6e971-148">Related Tasks</span></span>  
  
-   [<span data-ttu-id="6e971-149">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6e971-149">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="6e971-150">查看可用性组侦听程序属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6e971-150">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="6e971-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6e971-151">See Also</span></span>  
 <span data-ttu-id="6e971-152">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6e971-152">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="6e971-153">可用性组侦听程序、客户端连接和应用程序故障转移 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6e971-153">Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;</span></span>](../../listeners-client-connectivity-application-failover.md)  
