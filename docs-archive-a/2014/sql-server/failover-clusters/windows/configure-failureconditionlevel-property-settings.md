---
title: 配置 FailureConditionLevel 属性设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 513dd179-9a46-46da-9fdd-7632cf6d0816
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8924b864d7cc8be078b370e3182713114f54ff6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586271"
---
# <a name="configure-failureconditionlevel-property-settings"></a><span data-ttu-id="71238-102">配置 FailureConditionLevel 属性设置</span><span class="sxs-lookup"><span data-stu-id="71238-102">Configure FailureConditionLevel Property Settings</span></span>
  <span data-ttu-id="71238-103">使用 FailureConditionLevel 属性可以设置 AlwaysOn 故障转移群集实例 (FCI) 进行故障转移或重新启动的条件。</span><span class="sxs-lookup"><span data-stu-id="71238-103">Use the FailureConditionLevel property to set the conditions for the AlwaysOn Failover Cluster Instance (FCI) to fail over or restart.</span></span> <span data-ttu-id="71238-104">对此属性的更改会立即应用，而无需重新启动 Windows Server 故障转移群集 (WSFC) 服务或 FCI 资源。</span><span class="sxs-lookup"><span data-stu-id="71238-104">Changes to this property are applied immediately without requiring a restart of the Windows Server Failover Cluster (WSFC) service or the FCI resource.</span></span>  
  
-   <span data-ttu-id="71238-105">**开始之前：** [FailureConditionLevel 属性设置](#Restrictions)，[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="71238-105">**Before you begin:**  [FailureConditionLevel Property Settings](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="71238-106">**若要配置 FailureConditionLevel 属性设置，请使用** [PowerShell](#PowerShellProcedure)、[故障转移群集管理器](#WSFC)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="71238-106">**To configure the FailureConditionLevel property settings using,** [PowerShell](#PowerShellProcedure), [Failover Cluster Manager](#WSFC), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="71238-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="71238-107">Before You Begin</span></span>  
  
###  <a name="failureconditionlevel-property-settings"></a><a name="Restrictions"></a> <span data-ttu-id="71238-108">FailureConditionLevel 属性设置</span><span class="sxs-lookup"><span data-stu-id="71238-108">FailureConditionLevel Property Settings</span></span>  
 <span data-ttu-id="71238-109">针对递增的级别设置故障条件。</span><span class="sxs-lookup"><span data-stu-id="71238-109">The failure conditions are set on an increasing scale.</span></span> <span data-ttu-id="71238-110">对于级别 1-5，每个级别除了自己的条件外，还包括之前级别的所有条件。</span><span class="sxs-lookup"><span data-stu-id="71238-110">For levels 1-5, each level includes all the conditions from the previous levels in addition to its own conditions.</span></span> <span data-ttu-id="71238-111">这意味着，每个级别越大，故障转移或重新启动的几率不断加大。</span><span class="sxs-lookup"><span data-stu-id="71238-111">This means that with each level, there is an increased probability of a failover or restart.</span></span>  <span data-ttu-id="71238-112">有关详细信息，请参阅 [Failover Policy for Failover Cluster Instances](failover-policy-for-failover-cluster-instances.md) 主题的“确定故障”一节。</span><span class="sxs-lookup"><span data-stu-id="71238-112">For more information, see the "Determining Failures" section of the [Failover Policy for Failover Cluster Instances](failover-policy-for-failover-cluster-instances.md) topic.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="71238-113">Security</span><span class="sxs-lookup"><span data-stu-id="71238-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="71238-114">权限</span><span class="sxs-lookup"><span data-stu-id="71238-114">Permissions</span></span>  
 <span data-ttu-id="71238-115">需要 ALTER SETTINGS 和 VIEW SERVER STATE 权限。</span><span class="sxs-lookup"><span data-stu-id="71238-115">Requires ALTER SETTINGS and VIEW SERVER STATE permissions.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="71238-116">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="71238-116">Using PowerShell</span></span>  
  
### <a name="to-configure-failureconditionlevel-settings"></a><span data-ttu-id="71238-117">配置 FailureConditionLevel 设置</span><span class="sxs-lookup"><span data-stu-id="71238-117">To configure FailureConditionLevel settings</span></span>  
  
1.  <span data-ttu-id="71238-118">通过 **“以管理员身份运行”** 启动提升的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="71238-118">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="71238-119">导入 `FailoverClusters` 模块以启用群集 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="71238-119">Import the `FailoverClusters` module to enable cluster cmdlets.</span></span>  
  
3.  <span data-ttu-id="71238-120">使用 `Get-ClusterResource` cmdlet 查找 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 资源，然后使用 `Set-ClusterParameter` Cmdlet 为故障转移群集实例设置**FailureConditionLevel**属性。</span><span class="sxs-lookup"><span data-stu-id="71238-120">Use the `Get-ClusterResource` cmdlet to find the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource, then use `Set-ClusterParameter` cmdlet to set the **FailureConditionLevel** property for a Failover Cluster Instance.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="71238-121">每次您打开新的 PowerShell 窗口时，都需要导入 `FailoverClusters` 模块。</span><span class="sxs-lookup"><span data-stu-id="71238-121">Every time you open a new PowerShell window, you need to import the `FailoverClusters` module.</span></span>  

 <span data-ttu-id="71238-122">下面的示例将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 资源“`SQL Server (INST1)`”上的 FailureConditionLevel 设置更改为在出现严重服务器错误时执行故障转移或重新启动。</span><span class="sxs-lookup"><span data-stu-id="71238-122">The following example changes the FailureConditionLevel setting on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource "`SQL Server (INST1)`" to fail over or restart on critical server errors.</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter FailureConditionLevel 3
```  
  
### <a name="related-content-powershell"></a><span data-ttu-id="71238-123">相关内容 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="71238-123">Related Content (PowerShell)</span></span>  
  
-   <span data-ttu-id="71238-124">[群集和高可用性](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) （故障转移群集和网络负载平衡团队博客）</span><span class="sxs-lookup"><span data-stu-id="71238-124">[Clustering and High-Availability](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (Failover Clustering and Network Load Balancing Team Blog)</span></span>  
  
-   <span data-ttu-id="71238-125">[故障转移群集上的 Windows PowerShell 入门](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="71238-125">[Getting Started with Windows PowerShell on a Failover Cluster](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="71238-126">群集资源命令和等效的 Windows PowerShell cmdlet</span><span class="sxs-lookup"><span data-stu-id="71238-126">Cluster resource commands and equivalent Windows PowerShell cmdlets</span></span>](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> <span data-ttu-id="71238-127">使用故障转移群集管理器管理单元</span><span class="sxs-lookup"><span data-stu-id="71238-127">Using the Failover Cluster Manager Snap-in</span></span>  

### <a name="to-configure-failureconditionlevel-property-settings"></a><span data-ttu-id="71238-128">配置 FailureConditionLevel 属性设置</span><span class="sxs-lookup"><span data-stu-id="71238-128">To configure FailureConditionLevel property settings</span></span>
  
1.  <span data-ttu-id="71238-129">打开故障转移群集管理器管理单元。</span><span class="sxs-lookup"><span data-stu-id="71238-129">Open the Failover Cluster Manager snap-in.</span></span>  
  
2.  <span data-ttu-id="71238-130">展开 **“服务和应用程序”** ，然后选择 FCI。</span><span class="sxs-lookup"><span data-stu-id="71238-130">Expand the **Services and Applications** and select the FCI.</span></span>  
  
3.  <span data-ttu-id="71238-131">右键单击“其他资源”下的“SQL Server 资源”，然后从菜单中选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="71238-131">Right-click the **SQL Server resource** under **Other Resources**, and then select **Properties** from the menu.</span></span> <span data-ttu-id="71238-132">此时将打开 SQL Server 资源 **“属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="71238-132">The SQL Server resource **Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="71238-133">选择 **“属性”** 选项卡，为 **FaliureConditionLevel** 属性输入所需的值，然后单击 **“确定”** 以应用更改。</span><span class="sxs-lookup"><span data-stu-id="71238-133">Select the **Properties** tab, enter the desired value for the **FaliureConditionLevel** property, and then click **OK** to apply the change.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="71238-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="71238-134">Using Transact-SQL</span></span>  

### <a name="to-configure-failureconditionlevel-property-settings"></a><span data-ttu-id="71238-135">配置 FailureConditionLevel 属性设置</span><span class="sxs-lookup"><span data-stu-id="71238-135">To configure FailureConditionLevel property settings</span></span>
  
 <span data-ttu-id="71238-136">使用 [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句，可指定 FailureConditionLevel 属性值。</span><span class="sxs-lookup"><span data-stu-id="71238-136">Using the [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement, you can specify the FailureConditionLevel property value.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="71238-137">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="71238-137">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="71238-138">以下示例将 FailureConditionLevel 属性设置为 0，表示对于任何故障条件将不自动触发故障转移或重新启动。</span><span class="sxs-lookup"><span data-stu-id="71238-138">The following example sets the FailureConditionLevel property to 0, indicating that failover or restart will not be triggered automatically on any failure conditions.</span></span>  
  
```sql
ALTER SERVER CONFIGURATION SET FAILOVER CLUSTER PROPERTY FailureConditionLevel = 0;  
```  
  
## <a name="see-also"></a><span data-ttu-id="71238-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71238-139">See Also</span></span>  
 <span data-ttu-id="71238-140">[sp_server_diagnostics (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71238-140">[sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) </span></span>  
 [<span data-ttu-id="71238-141">Failover Policy for Failover Cluster Instances</span><span class="sxs-lookup"><span data-stu-id="71238-141">Failover Policy for Failover Cluster Instances</span></span>](failover-policy-for-failover-cluster-instances.md)  
