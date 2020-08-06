---
title: 配置 HealthCheckTimeout 属性设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a38cd6e9e4718a2f1c136e5412cde340e92f14c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586269"
---
# <a name="configure-healthchecktimeout-property-settings"></a><span data-ttu-id="a08fa-102">配置 HealthCheckTimeout 属性设置</span><span class="sxs-lookup"><span data-stu-id="a08fa-102">Configure HealthCheckTimeout Property Settings</span></span>
  <span data-ttu-id="a08fa-103">HealthCheckTimeout 设置用于指定在报告 AlwaysOn 故障转移群集实例 (FCI) 为无响应之前，SQL Server 资源 DLL 应等待[sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)存储过程返回的信息的时间长度（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="a08fa-103">The HealthCheckTimeout setting is used to specify the length of time, in milliseconds, that the SQL Server resource DLL should wait for information returned by the [sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) stored procedure before reporting the AlwaysOn Failover Cluster Instance (FCI) as unresponsive.</span></span> <span data-ttu-id="a08fa-104">对超时设置所做的更改会立即生效，不需要重新启动 SQL Server 资源。</span><span class="sxs-lookup"><span data-stu-id="a08fa-104">Changes that are made to the timeout settings are effective immediately and do not require a restart of the SQL Server resource.</span></span>  
  
-   <span data-ttu-id="a08fa-105">**开始之前：** [限制和局限](#Limits)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="a08fa-105">**Before you begin:**  [Limitations and Restrictions](#Limits), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="a08fa-106">**要配置 HeathCheckTimeout 设置，请使用：**  [PowerShell](#PowerShellProcedure)、[故障转移群集管理器](#WSFC)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="a08fa-106">**To Configure the HeathCheckTimeout setting, using:**  [PowerShell](#PowerShellProcedure), [Failover Cluster Manager](#WSFC), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a08fa-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="a08fa-107">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Limits"></a> <span data-ttu-id="a08fa-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a08fa-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="a08fa-109">此属性的默认值为 60,000 毫秒（60 秒）。</span><span class="sxs-lookup"><span data-stu-id="a08fa-109">The default value for this property is 60,000 milliseconds (60 seconds).</span></span> <span data-ttu-id="a08fa-110">最小值为 15,000 毫秒（15 秒）。</span><span class="sxs-lookup"><span data-stu-id="a08fa-110">The minimum value is 15,000 milliseconds (15 seconds).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a08fa-111">Security</span><span class="sxs-lookup"><span data-stu-id="a08fa-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a08fa-112">权限</span><span class="sxs-lookup"><span data-stu-id="a08fa-112">Permissions</span></span>  
 <span data-ttu-id="a08fa-113">需要 ALTER SETTINGS 和 VIEW SERVER STATE 权限。</span><span class="sxs-lookup"><span data-stu-id="a08fa-113">Requires ALTER SETTINGS and VIEW SERVER STATE permissions.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="a08fa-114">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a08fa-114">Using PowerShell</span></span>  
  
### <a name="to-configure-healthchecktimeout-settings"></a><span data-ttu-id="a08fa-115">配置 HealthCheckTimeout 设置</span><span class="sxs-lookup"><span data-stu-id="a08fa-115">To configure HealthCheckTimeout settings</span></span>  
  
1.  <span data-ttu-id="a08fa-116">通过 **“以管理员身份运行”** 启动提升的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a08fa-116">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="a08fa-117">导入 `FailoverClusters` 模块以启用群集 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a08fa-117">Import the `FailoverClusters` module to enable cluster cmdlets.</span></span>  
  
3.  <span data-ttu-id="a08fa-118">使用 `Get-ClusterResource` cmdlet 查找 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 资源，然后使用 `Set-ClusterParameter` cmdlet 为故障转移群集实例设置**HealthCheckTimeout**属性。</span><span class="sxs-lookup"><span data-stu-id="a08fa-118">Use the `Get-ClusterResource` cmdlet to find the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource, then use `Set-ClusterParameter` cmdlet to set the **HealthCheckTimeout** property for the failover cluster instance.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="a08fa-119">每次您打开新的 PowerShell 窗口时，都需要导入 `FailoverClusters` 模块。</span><span class="sxs-lookup"><span data-stu-id="a08fa-119">Every time you open a new PowerShell window, you need to import the `FailoverClusters` module.</span></span>  

 <span data-ttu-id="a08fa-120">下面的示例将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 资源“`SQL Server (INST1)`”上的 HealthCheckTimeout 设置更改为 60000 毫秒。</span><span class="sxs-lookup"><span data-stu-id="a08fa-120">The following example changes the HealthCheckTimeout setting on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource "`SQL Server (INST1)`" to 60000 milliseconds.</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
```  
  
### <a name="related-content-powershell"></a><span data-ttu-id="a08fa-121">相关内容 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="a08fa-121">Related Content (PowerShell)</span></span>  
  
-   <span data-ttu-id="a08fa-122">[群集和高可用性](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) （故障转移群集和网络负载平衡团队博客）</span><span class="sxs-lookup"><span data-stu-id="a08fa-122">[Clustering and High-Availability](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (Failover Clustering and Network Load Balancing Team Blog)</span></span>  
  
-   <span data-ttu-id="a08fa-123">[故障转移群集上的 Windows PowerShell 入门](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a08fa-123">[Getting Started with Windows PowerShell on a Failover Cluster](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="a08fa-124">群集资源命令和等效的 Windows PowerShell cmdlet</span><span class="sxs-lookup"><span data-stu-id="a08fa-124">Cluster resource commands and equivalent Windows PowerShell cmdlets</span></span>](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> <span data-ttu-id="a08fa-125">使用故障转移群集管理器管理单元</span><span class="sxs-lookup"><span data-stu-id="a08fa-125">Using the Failover Cluster Manager Snap-in</span></span>  
 <span data-ttu-id="a08fa-126">**配置 HealthCheckTimeout 设置**</span><span class="sxs-lookup"><span data-stu-id="a08fa-126">**To configure HealthCheckTimeout setting**</span></span>  
  
1.  <span data-ttu-id="a08fa-127">打开故障转移群集管理器管理单元。</span><span class="sxs-lookup"><span data-stu-id="a08fa-127">Open the Failover Cluster Manager snap-in.</span></span>  
  
2.  <span data-ttu-id="a08fa-128">展开 **“服务和应用程序”** ，然后选择 FCI。</span><span class="sxs-lookup"><span data-stu-id="a08fa-128">Expand **Services and Applications** and select the FCI.</span></span>  
  
3.  <span data-ttu-id="a08fa-129">右键单击“其他资源”\*\*\*\* 下的“SQL Server 资源”\*\*\*\*，然后从右键菜单中选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a08fa-129">Right-click the **SQL Server resource** under **Other Resources** and select **Properties** from the right-click menu.</span></span> <span data-ttu-id="a08fa-130">此时将打开 SQL Server 资源 **“属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="a08fa-130">The SQL Server resource **Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="a08fa-131">选择 **“属性”** 选项卡，为 **HealthCheckTimeout** 属性输入所需的值，然后单击 **“确定”** 以应用更改。</span><span class="sxs-lookup"><span data-stu-id="a08fa-131">Select the **Properties** tab, enter the desired value for the **HealthCheckTimeout** property, and then click **OK** to apply the change.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a08fa-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a08fa-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="a08fa-133">使用[ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句，你可以指定 HealthCheckTimeOut 属性值。</span><span class="sxs-lookup"><span data-stu-id="a08fa-133">Using the [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement, you can specify the HealthCheckTimeOut property value.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="a08fa-134">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a08fa-134">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="a08fa-135">下面的示例将 HealthCheckTimeout 选项设置为 15,000 毫秒（15 秒）。</span><span class="sxs-lookup"><span data-stu-id="a08fa-135">The following example sets the HealthCheckTimeout option to 15,000 milliseconds (15 seconds).</span></span>  
  
```sql
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a><span data-ttu-id="a08fa-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a08fa-136">See Also</span></span>  
 [<span data-ttu-id="a08fa-137">Failover Policy for Failover Cluster Instances</span><span class="sxs-lookup"><span data-stu-id="a08fa-137">Failover Policy for Failover Cluster Instances</span></span>](failover-policy-for-failover-cluster-instances.md)  
