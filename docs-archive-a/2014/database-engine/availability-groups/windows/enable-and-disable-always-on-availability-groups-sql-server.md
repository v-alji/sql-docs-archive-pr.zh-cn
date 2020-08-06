---
title: 启用和禁用 AlwaysOn 可用性组 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], disabling
- Availability Groups [SQL Server], enabling
ms.assetid: 7c326958-5ae9-4761-9c57-905972276a8f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 585f1d86d328b7c5027241310108d102b56ca327
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578446"
---
# <a name="enable-and-disable-alwayson-availability-groups-sql-server"></a><span data-ttu-id="86ae7-102">启用和禁用 AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="86ae7-102">Enable and Disable AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="86ae7-103">启用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 是服务器实例使用可用性组的先决条件。</span><span class="sxs-lookup"><span data-stu-id="86ae7-103">Enabling [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] is a prerequisite for a server instance to use availability groups.</span></span> <span data-ttu-id="86ae7-104">在创建和配置任何可用性组之前，必须在将承载一个或多个可用性组的可用性副本的每个 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 实例上启用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="86ae7-104">Before you can create and configure any availability group, the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature must have been enabled on the each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that will host an availability replica for one or more availability groups.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="86ae7-105">如果您删除后重新创建了 WSFC 群集，则必须在其原始 WSFC 群集上承载可用性副本的每个 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 实例上都禁用然后重新启用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="86ae7-105">If you delete and re-create a WSFC cluster, you must disable and re-enable the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature on each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosted an availability replica on the original WSFC cluster.</span></span>  
  
-   <span data-ttu-id="86ae7-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="86ae7-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="86ae7-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="86ae7-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="86ae7-108">安全性</span><span class="sxs-lookup"><span data-stu-id="86ae7-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="86ae7-109">**如何：**</span><span class="sxs-lookup"><span data-stu-id="86ae7-109">**How To:**</span></span>  
  
    -   [<span data-ttu-id="86ae7-110">确定是否已启用 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="86ae7-110">Determine Whether AlwaysOn Availability Groups is Enabled</span></span>](#IsEnabled)  
  
    -   [<span data-ttu-id="86ae7-111">启用 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="86ae7-111">Enable AlwaysOn Availability Groups</span></span>](#EnableAOAG)  
  
    -   [<span data-ttu-id="86ae7-112">禁用 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="86ae7-112">Disable AlwaysOn Availability Groups</span></span>](#DisableAOAG)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="86ae7-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="86ae7-113">Before You Begin</span></span>  
  
###  <a name="prerequisites-for-enabling-alwayson-availability-groups"></a><a name="Prerequisites"></a><span data-ttu-id="86ae7-114">启用 AlwaysOn 可用性组的先决条件</span><span class="sxs-lookup"><span data-stu-id="86ae7-114">Prerequisites for Enabling AlwaysOn Availability Groups</span></span>  
  
-   <span data-ttu-id="86ae7-115">该服务器实例必须驻留在 Windows Server 故障转移群集 (WSFC) 节点上。</span><span class="sxs-lookup"><span data-stu-id="86ae7-115">The server instance must reside on a Windows Server Failover Clustering (WSFC) node.</span></span>  
  
-   <span data-ttu-id="86ae7-116">该服务器实例必须正在运行支持 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]的 SQL Server 版本。</span><span class="sxs-lookup"><span data-stu-id="86ae7-116">The server instance must be running an edition of SQL Server that supports [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="86ae7-117">有关详细信息，请参阅 [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="86ae7-117">For more information, see [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="86ae7-118">一次仅为一个服务器实例启用 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="86ae7-118">Enable AlwaysOn Availability Groups on only one server instance at a time.</span></span> <span data-ttu-id="86ae7-119">在启用 AlwaysOn 可用性组之后，一直等待直到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务已重新启动，然后才继续在另一个服务器实例上操作。</span><span class="sxs-lookup"><span data-stu-id="86ae7-119">After enabling AlwaysOn Availability Groups, wait until the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service has restarted before you proceed to another server instance.</span></span>  
  
 <span data-ttu-id="86ae7-120">有关创建和配置可用性组的其他先决条件的信息，请参阅[AlwaysOn 可用性组 &#40;SQL Server&#41;的先决条件、限制和建议](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="86ae7-120">For information about additional prerequisites for creating and configuring availability groups, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="86ae7-121">Security</span><span class="sxs-lookup"><span data-stu-id="86ae7-121">Security</span></span>  
 <span data-ttu-id="86ae7-122">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例上启用 AlwaysOn 可用性组时，服务器实例具有对 WSFC 群集的完全控制权限。</span><span class="sxs-lookup"><span data-stu-id="86ae7-122">While AlwaysOn Availability Groups is enabled on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the server instance has full control on the WSFC cluster.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="86ae7-123">权限</span><span class="sxs-lookup"><span data-stu-id="86ae7-123">Permissions</span></span>  
 <span data-ttu-id="86ae7-124">要求本地计算机上 **Administrator** 组中的成员身份以及对 WSFC 群集的完全控制。</span><span class="sxs-lookup"><span data-stu-id="86ae7-124">Requires membership in the **Administrator** group on the local computer and full control on the WSFC cluster.</span></span> <span data-ttu-id="86ae7-125">使用 PowerShell 启用 AlwaysOn 时，使用 **“以管理员身份运行”** 选项打开命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="86ae7-125">When enabling AlwaysOn by using PowerShell, open the Command Prompt window using the **Run as administrator** option.</span></span>  
  
 <span data-ttu-id="86ae7-126">要求 Active Directory 创建对象和管理对象权限。</span><span class="sxs-lookup"><span data-stu-id="86ae7-126">Requires Active Directory Create Objects and Manage Objects permissions.</span></span>  
  
##  <a name="determine-whether-alwayson-availability-groups-is-enabled"></a><a name="IsEnabled"></a><span data-ttu-id="86ae7-127">确定是否已启用 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="86ae7-127">Determine Whether AlwaysOn Availability Groups is Enabled</span></span>  
  
-   [<span data-ttu-id="86ae7-128">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="86ae7-128">SQL Server Management Studio</span></span>](#SSMS1Procedure)  
  
-   [<span data-ttu-id="86ae7-129">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="86ae7-129">Transact-SQL</span></span>](#Tsql1Procedure)  
  
-   [<span data-ttu-id="86ae7-130">PowerShell</span><span class="sxs-lookup"><span data-stu-id="86ae7-130">PowerShell</span></span>](#PowerShell1Procedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMS1Procedure"></a> <span data-ttu-id="86ae7-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="86ae7-131">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="86ae7-132">**确定是否已启用 AlwaysOn 可用性组**</span><span class="sxs-lookup"><span data-stu-id="86ae7-132">**To determine whether AlwaysOn Availability Groups is enabled**</span></span>  
  
1.  <span data-ttu-id="86ae7-133">在“对象资源管理器”中，右键单击服务器实例，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="86ae7-133">In Object Explorer, right-click the server instance, and  click **Properties**.</span></span>  
  
2.  <span data-ttu-id="86ae7-134">在 **“服务器属性”** 对话框中，单击 **“常规”** 页。</span><span class="sxs-lookup"><span data-stu-id="86ae7-134">In the **Server Properties** dialog box, click the **General** page.</span></span> <span data-ttu-id="86ae7-135">**“启用 HADR”** 属性显示以下值之一：</span><span class="sxs-lookup"><span data-stu-id="86ae7-135">The **Is HADR Enabled** property displays one of the following values:</span></span>  
  
    -   <span data-ttu-id="86ae7-136">**True**（如果启用 AlwaysOn 可用性组）</span><span class="sxs-lookup"><span data-stu-id="86ae7-136">**True**, if AlwaysOn Availability Groups is enabled</span></span>  
  
    -   <span data-ttu-id="86ae7-137">**False**（如果禁用 AlwaysOn 可用性组）。</span><span class="sxs-lookup"><span data-stu-id="86ae7-137">**False**, if AlwaysOn Availability Groups is disabled.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="Tsql1Procedure"></a> <span data-ttu-id="86ae7-138">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="86ae7-138">Using Transact-SQL</span></span>  
 <span data-ttu-id="86ae7-139">**确定是否已启用 AlwaysOn 可用性组**</span><span class="sxs-lookup"><span data-stu-id="86ae7-139">**To determine whether AlwaysOn Availability Groups is enabled**</span></span>  
  
1.  <span data-ttu-id="86ae7-140">使用以下 [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) 语句：</span><span class="sxs-lookup"><span data-stu-id="86ae7-140">Use the following [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) statement:</span></span>  
  
    ```sql
    SELECT SERVERPROPERTY ('IsHadrEnabled');  
    ```  
  
     <span data-ttu-id="86ae7-141">`IsHadrEnabled` 服务器属性的设置指示是否为 AlwaysOn 可用性组启用了 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例，如下所示：</span><span class="sxs-lookup"><span data-stu-id="86ae7-141">The setting of the `IsHadrEnabled` server property indicates whether an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is enabled for AlwaysOn Availability Groups, as follows:</span></span>  
  
    -   <span data-ttu-id="86ae7-142">如果 `IsHadrEnabled` = 1，则启用 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="86ae7-142">If `IsHadrEnabled` = 1, AlwaysOn Availability Groups is enabled.</span></span>  
  
    -   <span data-ttu-id="86ae7-143">如果 `IsHadrEnabled` = 0，则禁用 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="86ae7-143">If `IsHadrEnabled` = 0, AlwaysOn Availability Groups is disabled.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="86ae7-144">有关服务器属性的详细信息 `IsHadrEnabled` ，请参阅[SERVERPROPERTY &#40;transact-sql&#41;](/sql/t-sql/functions/serverproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="86ae7-144">For more information about the `IsHadrEnabled` server property, see [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql).</span></span>  
  
###  <a name="using-powershell"></a><a name="PowerShell1Procedure"></a> <span data-ttu-id="86ae7-145">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="86ae7-145">Using PowerShell</span></span>  
 <span data-ttu-id="86ae7-146">**确定是否已启用 AlwaysOn 可用性组**</span><span class="sxs-lookup"><span data-stu-id="86ae7-146">**To determine whether AlwaysOn Availability Groups is enabled**</span></span>  
  
1.  <span data-ttu-id="86ae7-147">将默认 (`cd`) 设置为服务器实例 (例如， `\SQL\NODE1\DEFAULT` 要在其上确定是否启用了) 。 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86ae7-147">Set default (`cd`) to the server instance (e.g. `\SQL\NODE1\DEFAULT`) on which you want to determine whether [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] is enabled.</span></span>  
  
2.  <span data-ttu-id="86ae7-148">输入以下 PowerShell `Get-Item` 命令：</span><span class="sxs-lookup"><span data-stu-id="86ae7-148">Enter the following PowerShell `Get-Item` command:</span></span>  
  
    ```powershell
    Get-Item . | Select IsHadrEnabled  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="86ae7-149">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="86ae7-149">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="86ae7-150">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="86ae7-150">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="86ae7-151">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="86ae7-151">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="86ae7-152">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="86ae7-152">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="enable-alwayson-availability-groups"></a><a name="EnableAOAG"></a> <span data-ttu-id="86ae7-153">启用 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="86ae7-153">Enable AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="86ae7-154">**启用 AlwaysOn，使用：**</span><span class="sxs-lookup"><span data-stu-id="86ae7-154">**To enable AlwaysOn, using:**</span></span>  
  
-   [<span data-ttu-id="86ae7-155">SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="86ae7-155">SQL Server Configuration Manager</span></span>](#SQLCM2Procedure)  
  
-   [<span data-ttu-id="86ae7-156">PowerShell</span><span class="sxs-lookup"><span data-stu-id="86ae7-156">PowerShell</span></span>](#PScmd2Procedure)  
  
###  <a name="using-sql-server-configuration-manager"></a><a name="SQLCM2Procedure"></a> <span data-ttu-id="86ae7-157">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="86ae7-157">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="86ae7-158">**启用 AlwaysOn 可用性组**</span><span class="sxs-lookup"><span data-stu-id="86ae7-158">**To enable AlwaysOn Availability Groups**</span></span>  
  
1.  <span data-ttu-id="86ae7-159">连接到承载要启用 AlwaysOn 可用性组的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的 Windows Server 故障转移群集 (WSFC) 节点。</span><span class="sxs-lookup"><span data-stu-id="86ae7-159">Connect to the Windows Server Failover Clustering (WSFC) node that hosts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance where you want to enable AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="86ae7-160">在“开始”  菜单上，依次指向“所有程序” 、 [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]、“配置工具” ，然后单击“SQL Server 配置管理器” 。</span><span class="sxs-lookup"><span data-stu-id="86ae7-160">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and  click **SQL Server Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="86ae7-161">在**SQL Server 配置管理器**中，单击 " **SQL Server 服务**"，右键单击 "SQL Server (\*\* < *`instance name`*>) **"，其中 **<*`instance name`*>** 是要为其启用 AlwaysOn 可用性组的本地服务器实例的名称，然后单击 "**属性"。\*\*</span><span class="sxs-lookup"><span data-stu-id="86ae7-161">In **SQL Server Configuration Manager**, click **SQL Server Services**, right-click SQL Server (**<*`instance name`*>)**, where **<*`instance name`*>** is the name of a local server instance for which you want to enable AlwaysOn Availability Groups, and click **Properties.**</span></span>  
  
4.  <span data-ttu-id="86ae7-162">选择 **“AlwaysOn 高可用性”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="86ae7-162">Select the **AlwaysOn High Availability** tab.</span></span>  
  
5.  <span data-ttu-id="86ae7-163">验证 **Windows 故障转移群集名称**字段包含本地故障转移群集的名称。</span><span class="sxs-lookup"><span data-stu-id="86ae7-163">Verify that **Windows failover cluster name** field contains the name of the local failover cluster.</span></span> <span data-ttu-id="86ae7-164">如果此字段为空，则此服务器实例当前不支持 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="86ae7-164">If this field is blank, this server instance currently does not support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="86ae7-165">原因包括本地计算机不是群集节点、WSFC 群集已关闭或此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 不支持 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="86ae7-165">Either the local computer is not a cluster node, the WSFC cluster has been shut down, or this edition of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] that does not support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span>  
  
6.  <span data-ttu-id="86ae7-166">选中 "**启用 AlwaysOn 可用性组**" 复选框，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="86ae7-166">Select the **Enable AlwaysOn Availability Groups** check box, and click **OK**.</span></span>  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="86ae7-167">配置管理器保存您的更改。</span><span class="sxs-lookup"><span data-stu-id="86ae7-167">Configuration Manager saves your change.</span></span> <span data-ttu-id="86ae7-168">然后，必须手动重新启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="86ae7-168">Then, you must manually restart the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="86ae7-169">这使您可以选择最适合您的业务要求的重新启动时间。</span><span class="sxs-lookup"><span data-stu-id="86ae7-169">This enables you to choose a restart time that is best for your business requirements.</span></span> <span data-ttu-id="86ae7-170">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务重新启动时，将启用 AlwaysOn 且 `IsHadrEnabled` 服务器属性将设置为 1。</span><span class="sxs-lookup"><span data-stu-id="86ae7-170">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service restarts, AlwaysOn will be enabled, and the `IsHadrEnabled` server property will be set to 1.</span></span>  
  
###  <a name="using-sql-server-powershell"></a><a name="PScmd2Procedure"></a> <span data-ttu-id="86ae7-171">使用 SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="86ae7-171">Using SQL Server PowerShell</span></span>  
 <span data-ttu-id="86ae7-172">**启用 AlwaysOn**</span><span class="sxs-lookup"><span data-stu-id="86ae7-172">**To enable AlwaysOn**</span></span>  
  
1.  <span data-ttu-id="86ae7-173">将目录切换 (`cd`) 到您要启用 AlwaysOn 可用性组的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="86ae7-173">Change directory (`cd`) to a server instance that you want to enable for AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="86ae7-174">使用 `Enable-SqlAlwaysOn` cmdlet 启用 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="86ae7-174">Use the `Enable-SqlAlwaysOn` cmdlet to enable AlwaysOn Availability Groups.</span></span>  
  
     <span data-ttu-id="86ae7-175">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="86ae7-175">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="86ae7-176">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="86ae7-176">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="86ae7-177">有关如何控制 cmdlet 是否重新启动服务的信息 `Enable-SqlAlwaysOn` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，请参阅本主题后面的[Cmdlet 何时重新启动 SQL Server 服务？](#WhenCmdletRestartsSQL)。</span><span class="sxs-lookup"><span data-stu-id="86ae7-177">For information about how to control whether the `Enable-SqlAlwaysOn` cmdlet restarts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service, see [When Does a Cmdlet Restart the SQL Server Service?](#WhenCmdletRestartsSQL), later in this topic.</span></span>  
  
 <span data-ttu-id="86ae7-178">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="86ae7-178">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="86ae7-179">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="86ae7-179">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
####  <a name="example-enable-sqlalwayson"></a><a name="ExmplEnable-SqlHadrServic"></a> <span data-ttu-id="86ae7-180">示例：Enable-SqlAlwaysOn</span><span class="sxs-lookup"><span data-stu-id="86ae7-180">Example: Enable-SqlAlwaysOn</span></span>  
 <span data-ttu-id="86ae7-181">以下 PowerShell 命令在 SQL Server 实例上启用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] （*计算机*\\*实例*）。</span><span class="sxs-lookup"><span data-stu-id="86ae7-181">The following PowerShell command enables [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] on an instance of SQL Server (*Computer*\\*Instance*).</span></span>  
  
```powershell
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
```  
  
##  <a name="disable-alwayson-availability-groups"></a><a name="DisableAOAG"></a><span data-ttu-id="86ae7-182">禁用 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="86ae7-182">Disable AlwaysOn Availability Groups</span></span>  
  
-   <span data-ttu-id="86ae7-183">**禁用 AlwaysOn 之前：**</span><span class="sxs-lookup"><span data-stu-id="86ae7-183">**Before you disable AlwaysOn:**</span></span>  
  
     [<span data-ttu-id="86ae7-184">建议</span><span class="sxs-lookup"><span data-stu-id="86ae7-184">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="86ae7-185">**禁用 AlwaysOn，使用：**</span><span class="sxs-lookup"><span data-stu-id="86ae7-185">**To disable AlwaysOn, using:**</span></span>  
  
    -   [<span data-ttu-id="86ae7-186">SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="86ae7-186">SQL Server Configuration Manager</span></span>](#SQLCM3Procedure)  
  
    -   [<span data-ttu-id="86ae7-187">PowerShell</span><span class="sxs-lookup"><span data-stu-id="86ae7-187">PowerShell</span></span>](#PScmd3Procedure)  
  
-   <span data-ttu-id="86ae7-188">**跟进：**  [在禁用 AlwaysOn 之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="86ae7-188">**Follow Up:**  [After Disabling AlwaysOn](#FollowUp)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="86ae7-189">一次只能在一个服务器实例上禁用 AlwaysOn。</span><span class="sxs-lookup"><span data-stu-id="86ae7-189">Disable AlwaysOn on only one server instance at a time.</span></span> <span data-ttu-id="86ae7-190">在禁用 AlwaysOn 可用性组之后，一直等待直到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务已重新启动，然后才继续在另一个服务器实例上操作。</span><span class="sxs-lookup"><span data-stu-id="86ae7-190">After disabling AlwaysOn Availability Groups, wait until the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service has restarted before you proceed to another server instance.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="86ae7-191">建议</span><span class="sxs-lookup"><span data-stu-id="86ae7-191">Recommendations</span></span>  
 <span data-ttu-id="86ae7-192">在服务器实例上禁用 AlwaysOn 之前，我们建议您执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="86ae7-192">Before you disable AlwaysOn on a server instance, we recommend that you do the following:</span></span>  
  
1.  <span data-ttu-id="86ae7-193">如果该服务器实例当前正在承载您要保留的可用性组的主副本，我们建议您尽可能手动将该可用性组故障转移到一个同步的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="86ae7-193">If the server instance is currently hosting the primary replica of an availability group that you want to keep, we recommend that you manually fail over the availability group to a synchronized secondary replica, if possible.</span></span> <span data-ttu-id="86ae7-194">有关详细信息，请参阅[执行可用性组的计划手动故障转移 (SQL Server)](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="86ae7-194">For more information, see [Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="86ae7-195">删除所有本地辅助副本。</span><span class="sxs-lookup"><span data-stu-id="86ae7-195">Remove all local secondary replicas.</span></span> <span data-ttu-id="86ae7-196">有关详细信息，请参阅[从可用性组中删除次要副本 (SQL Server)](remove-a-secondary-replica-from-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="86ae7-196">For more information, see [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="using-sql-server-configuration-manager"></a><a name="SQLCM3Procedure"></a> <span data-ttu-id="86ae7-197">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="86ae7-197">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="86ae7-198">**禁用 AlwaysOn**</span><span class="sxs-lookup"><span data-stu-id="86ae7-198">**To disable AlwaysOn**</span></span>  
  
1.  <span data-ttu-id="86ae7-199">连接到承载要禁用 AlwaysOn 可用性组的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的 Windows Server 故障转移群集 (WSFC) 节点。</span><span class="sxs-lookup"><span data-stu-id="86ae7-199">Connect to the Windows Server Failover Clustering (WSFC) node that hosts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance where you want to disable AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="86ae7-200">在 **“开始”** 菜单中，依次指向 **“所有程序”** 、 [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]、 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="86ae7-200">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and click **SQL Server Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="86ae7-201">在**SQL Server 配置管理器**中，单击 " **SQL Server 服务**"，右键单击 "SQL Server (\*\* < *`instance name`*>) **"，其中 **<*`instance name`*>** 是要禁用 AlwaysOn 可用性组的本地服务器实例的名称，然后单击 "**属性\*\*"。</span><span class="sxs-lookup"><span data-stu-id="86ae7-201">In **SQL Server Configuration Manager**, click **SQL Server Services**, right-click SQL Server (**<*`instance name`*>)**, where **<*`instance name`*>** is the name of a local server instance for which you want to disable AlwaysOn Availability Groups, and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="86ae7-202">在“AlwaysOn 高可用性”\*\*\*\* 选项卡上，取消选中“启用 AlwaysOn 可用性组” \*\*\*\* 复选框，然后单击“确定” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="86ae7-202">On the**AlwaysOn High Availability**tab, deselect the **Enable AlwaysOn Availability Groups** check box, and click **OK**.</span></span>  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="86ae7-203">配置管理器保存您的更改并重新启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="86ae7-203">Configuration Manager saves your change and restarts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="86ae7-204">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务重新启动时，将禁用 AlwaysOn 且 `IsHadrEnabled` 服务器属性将设置为 0 以指示禁用 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="86ae7-204">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service restarts, AlwaysOn will be disabled, and the `IsHadrEnabled` server property will be set to 0, to indicate that AlwaysOn Availability Groups is disabled.</span></span>  
  
5.  <span data-ttu-id="86ae7-205">我们建议您查看本主题后面的 [跟进：在禁用 AlwaysOn 之后](#FollowUp)中的信息。</span><span class="sxs-lookup"><span data-stu-id="86ae7-205">We recommend that you read the information in [Follow Up: After Disabling AlwaysOn](#FollowUp), later in this topic.</span></span>  
  
###  <a name="using-sql-server-powershell"></a><a name="PScmd3Procedure"></a> <span data-ttu-id="86ae7-206">使用 SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="86ae7-206">Using SQL Server PowerShell</span></span>  
 <span data-ttu-id="86ae7-207">**禁用 AlwaysOn**</span><span class="sxs-lookup"><span data-stu-id="86ae7-207">**To disable AlwaysOn**</span></span>  
  
1.  <span data-ttu-id="86ae7-208">将目录 (`cd`) 更改为要为其为为 AlwaysOn 可用性组的当前启用的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="86ae7-208">Change directory (`cd`) to a currently-enabled server instance that you want to disenable for AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="86ae7-209">使用 `Disable-SqlAlwaysOn` cmdlet 启用 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="86ae7-209">Use the `Disable-SqlAlwaysOn` cmdlet to enable AlwaysOn Availability Groups.</span></span>  
  
     <span data-ttu-id="86ae7-210">例如，以下命令禁用实例上的 AlwaysOn 可用性组 SQL Server (*计算机* \\ *实例*) 。</span><span class="sxs-lookup"><span data-stu-id="86ae7-210">For example, the following command disables AlwaysOn Availability Groups on an instance of SQL Server (*Computer*\\*Instance*).</span></span>  <span data-ttu-id="86ae7-211">此命令需要重新启动实例，并将提示您确认此重新启动。</span><span class="sxs-lookup"><span data-stu-id="86ae7-211">This command requires restarting the instance, and you will be prompted to confirm this restart.</span></span>  
  
    ```powershell
    Disable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="86ae7-212">有关如何控制 cmdlet 是否重新启动服务的信息 `Disable-SqlAlwaysOn` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，请参阅本主题后面的[Cmdlet 何时重新启动 SQL Server 服务？](#WhenCmdletRestartsSQL)。</span><span class="sxs-lookup"><span data-stu-id="86ae7-212">For information about how to control whether the `Disable-SqlAlwaysOn` cmdlet restarts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service, see [When Does a Cmdlet Restart the SQL Server Service?](#WhenCmdletRestartsSQL), later in this topic.</span></span>  
  
     <span data-ttu-id="86ae7-213">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="86ae7-213">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="86ae7-214">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="86ae7-214">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="86ae7-215">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="86ae7-215">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="86ae7-216">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="86ae7-216">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="follow-up-after-disabling-alwayson"></a><a name="FollowUp"></a><span data-ttu-id="86ae7-217">跟进：在禁用 AlwaysOn 之后</span><span class="sxs-lookup"><span data-stu-id="86ae7-217">Follow Up: After Disabling AlwaysOn</span></span>  
 <span data-ttu-id="86ae7-218">禁用 AlwaysOn 可用性组后，必须重新启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="86ae7-218">After you disable AlwaysOn Availability Groups, the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] must be restarted.</span></span> <span data-ttu-id="86ae7-219">SQL 配置管理器将自动重新启动该服务器实例。</span><span class="sxs-lookup"><span data-stu-id="86ae7-219">SQL Configuration Manager restarts the server instance automatically.</span></span> <span data-ttu-id="86ae7-220">但是，如果您使用了 `Disable-SqlAlwaysOn`cmdlet，将需要手动重新启动该服务器实例。</span><span class="sxs-lookup"><span data-stu-id="86ae7-220">However, if you used the `Disable-SqlAlwaysOn` cmdlet, you will need to restart the server instance manually.</span></span> <span data-ttu-id="86ae7-221">有关详细信息，请参阅 [sqlservr Application](../../../tools/sqlservr-application.md)。</span><span class="sxs-lookup"><span data-stu-id="86ae7-221">For more information, see [sqlservr Application](../../../tools/sqlservr-application.md).</span></span>  
  
 <span data-ttu-id="86ae7-222">在重新启动的服务器实例上：</span><span class="sxs-lookup"><span data-stu-id="86ae7-222">On the restarted server instance:</span></span>  
  
-   <span data-ttu-id="86ae7-223">可用性数据库在 SQL Server 启动时不启动，因此无法访问它们。</span><span class="sxs-lookup"><span data-stu-id="86ae7-223">Availability databases do not start up at SQL Server startup, making them inaccessible.</span></span>  
  
-   <span data-ttu-id="86ae7-224">唯一支持的 AlwaysOn [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句是 [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="86ae7-224">The only supported AlwaysOn [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement is [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql).</span></span> <span data-ttu-id="86ae7-225">不支持 CREATE AVAILABILITY GROUP、ALTER AVAILABILITY GROUP 和 ALTER DATABASE 的 SET HADR 选项。</span><span class="sxs-lookup"><span data-stu-id="86ae7-225">CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP, and the SET HADR options of ALTER DATABASE are not supported.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="86ae7-226">元数据和 WSFC 中的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 配置数据不受禁用 AlwaysOn 可用性组的影响。</span><span class="sxs-lookup"><span data-stu-id="86ae7-226">metadata and [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] configuration data in WSFC are unaffected by disabling AlwaysOn Availability Groups.</span></span>  
  
 <span data-ttu-id="86ae7-227">如果您在为承载一个或多个可用性组的辅助副本的每个服务器实例上都永久禁用了 AlwaysOn 可用性组，则我们建议您完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="86ae7-227">If you permanently disable AlwaysOn Availability Groups on every server instance that hosts an availability replica for one or more availability groups, we recommend that you complete the following steps:</span></span>  
  
1.  <span data-ttu-id="86ae7-228">如果您在禁用 AlwaysOn 前未删除本地可用性组副本，则删除服务器实例正为其承载可用性组副本的每个可用性组。</span><span class="sxs-lookup"><span data-stu-id="86ae7-228">If you did not remove the local availability replicas before disabling AlwaysOn, delete (drop) each availability group for which the server instance is hosting an availability replica.</span></span> <span data-ttu-id="86ae7-229">有关删除可用性组的信息，请参阅[删除可用性组 (SQL Server)](remove-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="86ae7-229">For information about deleting an availability group, see [Remove an Availability Group &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="86ae7-230">若要删除留在原地的元数据，请删除服务器实例上作为原始 WSFC 群集一部分的受影响的可用性组。</span><span class="sxs-lookup"><span data-stu-id="86ae7-230">To remove the metadata left behind, delete (drop) each affected availability group on a server instance that is part of the original WSFC cluster.</span></span>  
  
3.  <span data-ttu-id="86ae7-231">所有连接仍可以访问任何主数据库，但是主数据库和辅助数据库之间的数据同步将停止。</span><span class="sxs-lookup"><span data-stu-id="86ae7-231">Any primary databases continue to be accessible to all connections but the data synchronization between the primary and secondary databases stops.</span></span>  
  
4.  <span data-ttu-id="86ae7-232">辅助数据库将进入 RESTORING 状态。</span><span class="sxs-lookup"><span data-stu-id="86ae7-232">The secondary databases enter the RESTORING state.</span></span> <span data-ttu-id="86ae7-233">您可以删除这些数据库，或者可通过使用 RESTORE WITH RECOVERY 还原它们。</span><span class="sxs-lookup"><span data-stu-id="86ae7-233">You can delete them, or you can restore them by using RESTORE WITH RECOVERY.</span></span> <span data-ttu-id="86ae7-234">但是，还原的数据库不再参与可用性组数据同步。</span><span class="sxs-lookup"><span data-stu-id="86ae7-234">However, restored databases are no longer participating in availability-group data synchronization.</span></span>  
  
##  <a name="when-does-a-cmdlet-restart-the-sql-server-service"></a><a name="WhenCmdletRestartsSQL"></a> <span data-ttu-id="86ae7-235">Cmdlet 何时重新启动 SQL Server 服务？</span><span class="sxs-lookup"><span data-stu-id="86ae7-235">When Does a Cmdlet Restart the SQL Server Service?</span></span>  
 <span data-ttu-id="86ae7-236">在当前正在运行的服务器实例上，使用 `Enable-SqlAlwaysOn` 或 `Disable-SqlAlwaysOn` 更改当前 AlwaysOn 设置可能导致 SQL Server 服务重新启动。</span><span class="sxs-lookup"><span data-stu-id="86ae7-236">On a server instance that is currently running, using `Enable-SqlAlwaysOn` or `Disable-SqlAlwaysOn` to change the current AlwaysOn setting could cause the SQL Server service to restart.</span></span> <span data-ttu-id="86ae7-237">重新启动行为取决于以下条件：</span><span class="sxs-lookup"><span data-stu-id="86ae7-237">The restart behavior on depends on the following conditions:</span></span>  
  
|<span data-ttu-id="86ae7-238">指定了 -NoServiceRestart 参数</span><span class="sxs-lookup"><span data-stu-id="86ae7-238">-NoServiceRestart parameter specified</span></span>|<span data-ttu-id="86ae7-239">指定了 -Force 参数</span><span class="sxs-lookup"><span data-stu-id="86ae7-239">-Force parameter specified</span></span>|<span data-ttu-id="86ae7-240">重新启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务？</span><span class="sxs-lookup"><span data-stu-id="86ae7-240">Is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service restarted?</span></span>|  
|--------------------------------------------|---------------------------------|---------------------------------------------------------|  
|<span data-ttu-id="86ae7-241">否</span><span class="sxs-lookup"><span data-stu-id="86ae7-241">No</span></span>|<span data-ttu-id="86ae7-242">否</span><span class="sxs-lookup"><span data-stu-id="86ae7-242">No</span></span>|<span data-ttu-id="86ae7-243">默认情况。</span><span class="sxs-lookup"><span data-stu-id="86ae7-243">By default.</span></span> <span data-ttu-id="86ae7-244">但是 cmdlet 提示您以下信息：</span><span class="sxs-lookup"><span data-stu-id="86ae7-244">But the cmdlet prompts you as follows:</span></span><br /><br /> <span data-ttu-id="86ae7-245">**若要完成此操作，必须重新启动服务器实例“<instance_name>”的 SQL Server 服务。是否继续？**</span><span class="sxs-lookup"><span data-stu-id="86ae7-245">**To complete this action, we must restart the SQL Server service for server instance '<instance_name>'. Do you want to continue?**</span></span><br /><br /> <span data-ttu-id="86ae7-246">**[Y] 是 [N] 否 [S] 挂起 [?] 帮助（默认值为“Y”）：**</span><span class="sxs-lookup"><span data-stu-id="86ae7-246">**[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):**</span></span><br /><br /> <span data-ttu-id="86ae7-247">如果指定 **N** 或 **S**，则不重新启动该服务。</span><span class="sxs-lookup"><span data-stu-id="86ae7-247">If you specify **N** or **S**, the service is not restarted.</span></span>|  
|<span data-ttu-id="86ae7-248">否</span><span class="sxs-lookup"><span data-stu-id="86ae7-248">No</span></span>|<span data-ttu-id="86ae7-249">是</span><span class="sxs-lookup"><span data-stu-id="86ae7-249">Yes</span></span>|<span data-ttu-id="86ae7-250">重新启动服务。</span><span class="sxs-lookup"><span data-stu-id="86ae7-250">Service is restarted.</span></span>|  
|<span data-ttu-id="86ae7-251">是</span><span class="sxs-lookup"><span data-stu-id="86ae7-251">Yes</span></span>|<span data-ttu-id="86ae7-252">否</span><span class="sxs-lookup"><span data-stu-id="86ae7-252">No</span></span>|<span data-ttu-id="86ae7-253">不重新启动服务。</span><span class="sxs-lookup"><span data-stu-id="86ae7-253">Service is not restarted.</span></span>|  
|<span data-ttu-id="86ae7-254">是</span><span class="sxs-lookup"><span data-stu-id="86ae7-254">Yes</span></span>|<span data-ttu-id="86ae7-255">是</span><span class="sxs-lookup"><span data-stu-id="86ae7-255">Yes</span></span>|<span data-ttu-id="86ae7-256">不重新启动服务。</span><span class="sxs-lookup"><span data-stu-id="86ae7-256">Service is not restarted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86ae7-257">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86ae7-257">See Also</span></span>  
 <span data-ttu-id="86ae7-258">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="86ae7-258">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="86ae7-259">SERVERPROPERTY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="86ae7-259">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)  
