---
title: 排查 SQL Server 实用工具问题 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f5f47c2a-38ea-40f8-9767-9bc138d14453
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3c139f9f084374aeb711e905ac0c315acc25c6ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691341"
---
# <a name="troubleshoot-the-sql-server-utility"></a><span data-ttu-id="bc4da-102">SQL Server 实用工具故障排除</span><span class="sxs-lookup"><span data-stu-id="bc4da-102">Troubleshoot the SQL Server Utility</span></span>
  <span data-ttu-id="bc4da-103">解决 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实用工具问题可能包括解决向 UCP 注册 SQL Server 实例的失败的操作、排除导致 UCP 上托管实例列表视图中图标灰显的失败的数据收集故障、缓解性能瓶颈或者解决资源运行状况问题。</span><span class="sxs-lookup"><span data-stu-id="bc4da-103">Troubleshooting [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility issues might include resolving a failed operation to enroll an instance of SQL Server with a UCP, troubleshooting failed data collection resulting in gray icons in the managed instance list view on a UCP, mitigating performance bottlenecks, or resolving resource health issues.</span></span> <span data-ttu-id="bc4da-104">有关缓解 UCP 标识的资源运行状况问题的详细信息 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅[SQL Server 资源运行状况的疑难解答 &#40;SQL Server 实用工具&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="bc4da-104">For more information about mitigating resource health issues identified by a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP, see [Troubleshoot SQL Server Resource Health &#40;SQL Server Utility&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md).</span></span>  
  
## <a name="failed-operation-to-enroll-an-instance-of-sql-server-into-a-sql-server-utility"></a><span data-ttu-id="bc4da-105">向 SQL Server 实用工具中注册 SQL Server 实例的失败的操作</span><span class="sxs-lookup"><span data-stu-id="bc4da-105">Failed Operation to Enroll an Instance of SQL Server into a SQL Server Utility</span></span>  
 <span data-ttu-id="bc4da-106">如果您使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证来连接到要注册的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，并且指定属于与 UCP 所在的域不同的其他 Active Directory 域的代理帐户，则实例验证将成功，但注册操作将失败并且具有以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="bc4da-106">If you connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, and you specify a proxy account that belongs to a different Active Directory domain than the domain where the UCP is located, instance validation succeeds, but the enrollment operation fails with the following error message:</span></span>  
  
 <span data-ttu-id="bc4da-107">执行 Transact-SQL 语句或批处理时发生了异常。</span><span class="sxs-lookup"><span data-stu-id="bc4da-107">An exception occurred while executing a Transact-SQL statement or batch.</span></span> <span data-ttu-id="bc4da-108">(Microsoft.SqlServer.ConnectionInfo)</span><span class="sxs-lookup"><span data-stu-id="bc4da-108">(Microsoft.SqlServer.ConnectionInfo)</span></span>  
  
 <span data-ttu-id="bc4da-109">其他信息：无法获取有关 Windows NT 组/用户“\<DomainName\AccountName>”的信息，错误代码 0x5。</span><span class="sxs-lookup"><span data-stu-id="bc4da-109">Additional information:  Could not obtain information about Windows NT group/user '\<DomainName\AccountName>', error code 0x5.</span></span> <span data-ttu-id="bc4da-110">（Microsoft SQL Server，错误：15404）</span><span class="sxs-lookup"><span data-stu-id="bc4da-110">(Microsoft SQL Server, Error: 15404)</span></span>  
  
 <span data-ttu-id="bc4da-111">在以下示例中将发生此问题：</span><span class="sxs-lookup"><span data-stu-id="bc4da-111">This issue occurs in the following example scenario:</span></span>  
  
1.  <span data-ttu-id="bc4da-112">UCP 是“Domain_1”的成员。</span><span class="sxs-lookup"><span data-stu-id="bc4da-112">The UCP is a member of "Domain_1."</span></span>  
  
2.  <span data-ttu-id="bc4da-113">存在单向域信任关系：即，“Domain_1”不为“Domain_2”所信任，但“Domain_2”为“Domain_1”所信任。</span><span class="sxs-lookup"><span data-stu-id="bc4da-113">A one-way domain trust relationship is in place: that is, "Domain_1" is not trusted by "Domain_2" but "Domain_2" is trusted by "Domain_1."</span></span>  
  
3.  <span data-ttu-id="bc4da-114">要注册到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实用工具中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例还是“Domain_1”的成员。</span><span class="sxs-lookup"><span data-stu-id="bc4da-114">The instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll into the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility is also a member of "Domain_1."</span></span>  
  
4.  <span data-ttu-id="bc4da-115">在注册操作过程中， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 使用 "sa" 连接到要注册的实例。</span><span class="sxs-lookup"><span data-stu-id="bc4da-115">During the enroll operation, connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll using "sa".</span></span> <span data-ttu-id="bc4da-116">指定来自“Domain_2”的一个代理帐户。</span><span class="sxs-lookup"><span data-stu-id="bc4da-116">Specify a proxy account from "Domain_2."</span></span>  
  
5.  <span data-ttu-id="bc4da-117">验证成功但注册失败。</span><span class="sxs-lookup"><span data-stu-id="bc4da-117">Validation succeeds but enrollment fails.</span></span>  
  
 <span data-ttu-id="bc4da-118">此问题的解决方法是使用以上示例，使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] "sa" 连接到要注册到实用工具的实例， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 并提供 "Domain_1" 的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="bc4da-118">The workaround for this issue, using the example above, is to connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll into the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility using "sa" and provide a proxy account from "Domain_1."</span></span>  
  
## <a name="failed-wmi-validation"></a><span data-ttu-id="bc4da-119">失败的 WMI 验证</span><span class="sxs-lookup"><span data-stu-id="bc4da-119">Failed WMI Validation</span></span>  
 <span data-ttu-id="bc4da-120">如果在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的实例上未正确配置 WMI，则“创建 UCP”和“注册托管实例”操作将显示一个警告，但不阻塞该操作。</span><span class="sxs-lookup"><span data-stu-id="bc4da-120">If WMI is not properly configured on an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the Create UCP and Enroll Managed Instance operations display a warning, but the operation is not blocked.</span></span> <span data-ttu-id="bc4da-121">此外，如果您更改 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理帐户配置，以便 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理对于必需的 WMI 类没有权限，则 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的受影响的托管实例上的数据收集将无法上载到 UCP。</span><span class="sxs-lookup"><span data-stu-id="bc4da-121">Additionally, if you change the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent account configuration so that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent does not have permission to required WMI classes, data collection on the affected managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fails to upload to the UCP.</span></span> <span data-ttu-id="bc4da-122">这将导致 UCP 中的灰色图标。</span><span class="sxs-lookup"><span data-stu-id="bc4da-122">This results in gray icons in the UCP.</span></span>  
  
 <span data-ttu-id="bc4da-123">失败的数据收集将导致 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的受影响托管实例的 UCP 列表视图中的灰色状态图标。</span><span class="sxs-lookup"><span data-stu-id="bc4da-123">Failed data collection results in gray status icons in the UCP list view for affected managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bc4da-124">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的托管实例上的作业历史记录显示 sysutility_mi_collect_and_upload 在步骤 2（暂存从 PowerShell 脚本收集的数据）上失败。</span><span class="sxs-lookup"><span data-stu-id="bc4da-124">The job history on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shows that sysutility_mi_collect_and_upload fails on step 2 (Stage Data Collected from PowerShell Script).</span></span>  
  
 <span data-ttu-id="bc4da-125">简化的错误消息如下：</span><span class="sxs-lookup"><span data-stu-id="bc4da-125">The simplified error messages are:</span></span>  
  
 <span data-ttu-id="bc4da-126">命令执行已停止，因为 shell 变量 "ErrorActionPreference" 设置为 Stop: 拒绝访问。</span><span class="sxs-lookup"><span data-stu-id="bc4da-126">Command execution stopped because the shell variable "ErrorActionPreference" is set to Stop: Access denied.</span></span>  
  
 <span data-ttu-id="bc4da-127">错误： \<Date-time (MM/DD/YYYY HH:MM:SS)> ：收集 cpu 属性时捕获到异常。</span><span class="sxs-lookup"><span data-stu-id="bc4da-127">ERROR: \<Date-time (MM/DD/YYYY HH:MM:SS)>: Caught exception while collecting cpu properties.</span></span>  <span data-ttu-id="bc4da-128">WMI 查询可能已失败。</span><span class="sxs-lookup"><span data-stu-id="bc4da-128">A WMI query might have failed.</span></span>  <span data-ttu-id="bc4da-129">警告。</span><span class="sxs-lookup"><span data-stu-id="bc4da-129">WARNING.</span></span>  
  
 <span data-ttu-id="bc4da-130">为了解决此问题，请验证以下配置设置：</span><span class="sxs-lookup"><span data-stu-id="bc4da-130">To resolve this issue, verify the following configuration settings:</span></span>  
  
-   <span data-ttu-id="bc4da-131">在 Windows Server 2003 上，SQL Server 代理服务必须是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]托管实例上 Windows 性能监视组的一部分。</span><span class="sxs-lookup"><span data-stu-id="bc4da-131">On Windows Server 2003, the SQL Server Agent service must be part of the Windows Performance Monitoring group on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="bc4da-132">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的托管实例上必须启用和配置 WMI 服务。</span><span class="sxs-lookup"><span data-stu-id="bc4da-132">The WMI service must be enabled and configured on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="bc4da-133">WMI 存储库在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的托管实例上可能损坏。</span><span class="sxs-lookup"><span data-stu-id="bc4da-133">The WMI repository might be corrupt on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="bc4da-134">性能库在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的托管实例上可能缺失或损坏。</span><span class="sxs-lookup"><span data-stu-id="bc4da-134">The performance library might be missing or corrupt on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bc4da-135">为了确认 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的指定实例已正确配置为向 UCP 报告数据，请验证在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的指定实例上以下类可用并且这些类对于 SQL Server 代理服务帐户而言是可访问的：</span><span class="sxs-lookup"><span data-stu-id="bc4da-135">To verify that the specified instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is configured properly to report data to the UCP, verify that the following classes are available on the specified instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and that they are accessible to SQL Server Agent service account:</span></span>  
  
-   <span data-ttu-id="bc4da-136">Win32_MountPoint</span><span class="sxs-lookup"><span data-stu-id="bc4da-136">Win32_MountPoint</span></span>  
  
-   <span data-ttu-id="bc4da-137">Win32_PerfRawData_PerfProc_Process</span><span class="sxs-lookup"><span data-stu-id="bc4da-137">Win32_PerfRawData_PerfProc_Process</span></span>  
  
-   <span data-ttu-id="bc4da-138">Win32_PerfRawData_PerfOS_Processor</span><span class="sxs-lookup"><span data-stu-id="bc4da-138">Win32_PerfRawData_PerfOS_Processor</span></span>  
  
-   <span data-ttu-id="bc4da-139">Win32_Processor</span><span class="sxs-lookup"><span data-stu-id="bc4da-139">Win32_Processor</span></span>  
  
-   <span data-ttu-id="bc4da-140">Win32_Volume</span><span class="sxs-lookup"><span data-stu-id="bc4da-140">Win32_Volume</span></span>  
  
-   <span data-ttu-id="bc4da-141">Win32_LogicalDisk</span><span class="sxs-lookup"><span data-stu-id="bc4da-141">Win32_LogicalDisk</span></span>  
  
 <span data-ttu-id="bc4da-142">您可以对上述每个类使用 Get-WmiObject PowerShell cmdlet 命令，以便验证每个类都是可访问的。</span><span class="sxs-lookup"><span data-stu-id="bc4da-142">You can use the Get-WmiObject PowerShell cmdlet on each of the classes to verify that each class is accessible.</span></span> <span data-ttu-id="bc4da-143">对 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的托管实例运行以下 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="bc4da-143">Run the following cmdlets on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
```  
Get-WmiObject Win32_MountPoint -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_PerfRawData_PerfProc_Process -ErrorAction Stop| Out-Null  
Get-WmiObject Win32_PerfRawData_PerfOS_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Volume -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_LogicalDisk -ErrorAction Stop | Out-Null  
```  
  
 <span data-ttu-id="bc4da-144">有关 WMI 疑难解答的详细信息，请参阅[Wmi 故障排除](https://go.microsoft.com/fwlink/?LinkId=178250)。</span><span class="sxs-lookup"><span data-stu-id="bc4da-144">For more information about troubleshooting WMI, see [Troubleshooting WMI](https://go.microsoft.com/fwlink/?LinkId=178250).</span></span> <span data-ttu-id="bc4da-145">请注意，这些 SQL Server 实用工具操作中的查询在本地运行，因此，DCOM 和远程故障排除内容不适用。</span><span class="sxs-lookup"><span data-stu-id="bc4da-145">Note that queries in these SQL Server Utility operations are running locally, so the DCOM and remote troubleshooting content does not apply.</span></span>  
  
## <a name="failed-data-collection"></a><span data-ttu-id="bc4da-146">失败的数据收集</span><span class="sxs-lookup"><span data-stu-id="bc4da-146">Failed Data Collection</span></span>  
 <span data-ttu-id="bc4da-147">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实用工具数据收集事件失败，请考虑以下可行方法：</span><span class="sxs-lookup"><span data-stu-id="bc4da-147">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility data collection events fail, consider the following possibilities:</span></span>  
  
-   <span data-ttu-id="bc4da-148">不要更改 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的托管实例上“实用工具信息”收集组的任何属性，并且不要手动打开或关闭数据收集，因为数据收集由实用工具代理作业控制。</span><span class="sxs-lookup"><span data-stu-id="bc4da-148">Do not change any properties of the "Utility Information" collection set on a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and do not turn data collection on/off manually, as data collection is controlled by a Utility agent job.</span></span>  
  
-   <span data-ttu-id="bc4da-149">失败的或不支持的 WMI 验证。</span><span class="sxs-lookup"><span data-stu-id="bc4da-149">Failed or unsupported WMI validation.</span></span> <span data-ttu-id="bc4da-150">有关详细信息，请参阅本主题前面的“失败的 WMI 验证”部分。</span><span class="sxs-lookup"><span data-stu-id="bc4da-150">For more information, see the Failed WMI Validation section earlier in this topic.</span></span>  
  
-   <span data-ttu-id="bc4da-151">刷新托管实例列表视图中的数据，因为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实用工具视点中的数据不自动刷新。</span><span class="sxs-lookup"><span data-stu-id="bc4da-151">Refresh data in the managed instance list view, as data in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility viewpoints does not refresh automatically.</span></span> <span data-ttu-id="bc4da-152">若要刷新数据，请右键单击 **“实用工具资源管理器导航”** 窗格中的 **“托管实例”** 节点，然后选择 **“刷新”**；或者在列表视图中右键单击 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例名称，然后选择 **“刷新”**。</span><span class="sxs-lookup"><span data-stu-id="bc4da-152">To refresh data, right-click the **Managed Instances** node in the **Utility Explorer Navigation** pane, then select **Refresh**, or right-click on the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance name in the list view, then select **Refresh**.</span></span> <span data-ttu-id="bc4da-153">请注意，在已向某一 UCP 注册 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的某一实例后，可能需要最长 30 分钟的时间，数据才会首次出现在实用工具资源管理器内容窗格的面板和视点中。</span><span class="sxs-lookup"><span data-stu-id="bc4da-153">Note that after an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has been enrolled with a UCP, it can take up to 30 minutes for data to first appear in the dashboard and viewpoints in the Utility Explorer content pane.</span></span>  
  
-   <span data-ttu-id="bc4da-154">使用 SQL Server 配置管理器验证该 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="bc4da-154">Use SQL Server Configuration Manager to verify that the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   <span data-ttu-id="bc4da-155">如果数据收集或数据上载由于超时问题而失败，则更新 MSDB 数据库中的函数 dbo.fn_sysutility_mi_get_collect_script()。</span><span class="sxs-lookup"><span data-stu-id="bc4da-155">If data collection or data upload fail due to timeout issues, update the function dbo.fn_sysutility_mi_get_collect_script() in the MSDB database.</span></span> <span data-ttu-id="bc4da-156">具体而言，在函数“Invoke-BulkCopyCommand()”中添加行：</span><span class="sxs-lookup"><span data-stu-id="bc4da-156">Specifically, in the function "Invoke-BulkCopyCommand()" add line:</span></span>  
  
    ```
    $bulkCopy.BulkCopyTimeout=180  
    ```  
  
     <span data-ttu-id="bc4da-157">默认超时值为 30 秒。</span><span class="sxs-lookup"><span data-stu-id="bc4da-157">The default timeout value is 30 seconds.</span></span>  
  
-   <span data-ttu-id="bc4da-158">如果该 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例未群集化，则验证 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理服务是否正在运行并且该服务是否设置为在该 UCP 上以及 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的托管实例上自动启动。</span><span class="sxs-lookup"><span data-stu-id="bc4da-158">If the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is not clustered, verify that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service is running and that the service is set to start automatically on the UCP and on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="bc4da-159">验证是否正在使用有效帐户在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的托管实例上运行数据收集。</span><span class="sxs-lookup"><span data-stu-id="bc4da-159">Verify that a valid account is being used to run data collection on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bc4da-160">例如，密码可能已到期。</span><span class="sxs-lookup"><span data-stu-id="bc4da-160">For example, the password may have expired.</span></span> <span data-ttu-id="bc4da-161">如果代理密码已到期，则更新 SSMS 中的密码凭据，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bc4da-161">If the proxy password has expired, update password credentials in SSMS, as follows:</span></span>  
  
    1.  <span data-ttu-id="bc4da-162">在 SSMS 的 **“对象资源管理器”** 中，展开 **“安全性”** 节点，然后展开 **“凭据”** 节点。</span><span class="sxs-lookup"><span data-stu-id="bc4da-162">In SSMS **Object Explorer**, expand the **Security** node, then expand the **Credentials** node.</span></span>  
  
    2.  <span data-ttu-id="bc4da-163">右键单击**UtilityAgentProxyCredential_ \<GUID> \*\* ，然后选择 "**属性\*\*"。</span><span class="sxs-lookup"><span data-stu-id="bc4da-163">Right-click on **UtilityAgentProxyCredential_\<GUID>** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="bc4da-164">在 "凭据属性" 对话框中，根据需要为\*\*UtilityAgentProxyCredential_ \<GUID> \*\*凭据更新凭据。</span><span class="sxs-lookup"><span data-stu-id="bc4da-164">On the Credential Properties dialog, update credentials as necessary for the **UtilityAgentProxyCredential_\<GUID>** credential.</span></span>  
  
    4.  <span data-ttu-id="bc4da-165">单击“确定”确认更改。</span><span class="sxs-lookup"><span data-stu-id="bc4da-165">Click **OK** to confirm the change.</span></span>  
  
-   <span data-ttu-id="bc4da-166">在 UCP 上和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的托管实例上，应启用 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="bc4da-166">TCP/IP should be enabled on the UCP and on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bc4da-167">通过 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置管理器启用 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="bc4da-167">Enable TCP/IP through [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
-   <span data-ttu-id="bc4da-168">UCP 上的 SQL Server Browser 服务必须启动，并且它必须配置为自动启动。</span><span class="sxs-lookup"><span data-stu-id="bc4da-168">The SQL Server Browser service on the UCP should be started and configured to start automatically.</span></span> <span data-ttu-id="bc4da-169">如果您的组织禁止使用 SQL Server Browser 服务，则使用以下步骤可以允许 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的托管实例连接到 UCP：</span><span class="sxs-lookup"><span data-stu-id="bc4da-169">If your organization prevents use of the SQL Server Browser service, use the following steps to allow a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to connect to the UCP:</span></span>  
  
    1.  <span data-ttu-id="bc4da-170">在的托管实例上的 Windows 任务栏上 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，单击 "**开始**"，然后单击 "**运行 ...**"。</span><span class="sxs-lookup"><span data-stu-id="bc4da-170">On the Windows taskbar on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], click **Start**, then click **Run...**.</span></span>  
  
    2.  <span data-ttu-id="bc4da-171">在提供的空间中键入“cliconfg.exe”，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="bc4da-171">Type "cliconfg.exe" in the space provided, then click **OK**.</span></span>  
  
    3.  <span data-ttu-id="bc4da-172">如果提示允许“SQL 客户端配置实用工具 EXE”启动，则单击 **“继续”**。</span><span class="sxs-lookup"><span data-stu-id="bc4da-172">If prompted to allow "SQL Client Configuration Utility EXE" to start, click "**Continue**."</span></span>  
  
    4.  <span data-ttu-id="bc4da-173">在 " **SQL Server 客户端网络实用工具**" 对话框上，选择 "**别名**" 选项卡，然后单击 "**添加 ...**"。</span><span class="sxs-lookup"><span data-stu-id="bc4da-173">On the **SQL Server Client Network Utility** dialog box, select the **Alias** tab, then click **Add...**.</span></span>  
  
    5.  <span data-ttu-id="bc4da-174">在 **“添加网络库配置”** 对话框上：</span><span class="sxs-lookup"><span data-stu-id="bc4da-174">On the **Add Network Library Configuration** dialog box:</span></span>  
  
    6.  <span data-ttu-id="bc4da-175">从网络库的列表中指定 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="bc4da-175">Specify TCP/IP from the list of network libraries.</span></span>  
  
    7.  <span data-ttu-id="bc4da-176">在 **“服务器别名”** 文本框中指定 UCP 的 ComputerName\InstanceName。</span><span class="sxs-lookup"><span data-stu-id="bc4da-176">Specify the ComputerName\InstanceName of the UCP in the **Server Alias** text box.</span></span>  
  
    8.  <span data-ttu-id="bc4da-177">在 **“服务器名称”** 文本框中指定 UCP 的 ComputerName。</span><span class="sxs-lookup"><span data-stu-id="bc4da-177">Specify the ComputerName of the UCP in the **Server Name** text box.</span></span>  
  
    9. <span data-ttu-id="bc4da-178">取消选中 **“动态确定端口”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="bc4da-178">Uncheck the **Dynamically determine port** checkbox.</span></span>  
  
    10. <span data-ttu-id="bc4da-179">在 **“端口号”** 文本框中指定 UCP 正在侦听的端口号。</span><span class="sxs-lookup"><span data-stu-id="bc4da-179">Specify the port number that the UCP is listening on in the **Port number** text box.</span></span>  
  
    11. <span data-ttu-id="bc4da-180">\*\*\*\* 单击“确定”以保存你的更改。</span><span class="sxs-lookup"><span data-stu-id="bc4da-180">Click **OK** to save your changes.</span></span>  
  
    12. <span data-ttu-id="bc4da-181">为连接到未启用 SQL Server Browser 服务的 UCP 的每个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 托管实例重复上述步骤。</span><span class="sxs-lookup"><span data-stu-id="bc4da-181">Repeat these steps for each managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that connects to a UCP where the SQL Server Browser service is not enabled.</span></span>  
  
-   <span data-ttu-id="bc4da-182">请确保 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的托管实例连接到网络。</span><span class="sxs-lookup"><span data-stu-id="bc4da-182">Ensure that managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] are connected to the network.</span></span>  
  
-   <span data-ttu-id="bc4da-183">如果在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的托管实例上存在名称相同但区分大小写设置不同的数据库，则数据库及其视点之间的标识可能不正确，并且导致失败的数据收集。</span><span class="sxs-lookup"><span data-stu-id="bc4da-183">If there are databases with the same name but different case-sensitivity settings on a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the identification between the database and its viewpoints can be incorrect, resulting in failed data collection.</span></span> <span data-ttu-id="bc4da-184">例如，名为“MYDATABASE”的数据库可能显示名为“MyDatabase”的数据库的运行状态。</span><span class="sxs-lookup"><span data-stu-id="bc4da-184">For example, a database named "MYDATABASE" might show health states for a database named "MyDatabase".</span></span> <span data-ttu-id="bc4da-185">在此情况下不产生任何错误。</span><span class="sxs-lookup"><span data-stu-id="bc4da-185">No error is generated in this scenario.</span></span> <span data-ttu-id="bc4da-186">失败的数据收集可能还源自 UCP 中显示的其他对象（例如数据库文件和文件组名称）中的区分大小写设置不匹配。</span><span class="sxs-lookup"><span data-stu-id="bc4da-186">Failed data collection can also result from case-sensitivity mismatches in other objects displayed in the UCP, like database file and file group names.</span></span>  
  
-   <span data-ttu-id="bc4da-187">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的某一托管实例承载在 Windows Server 2003 计算机上，则 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理服务帐户必须属于性能监视器用户安全组或本地管理员组。</span><span class="sxs-lookup"><span data-stu-id="bc4da-187">If a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is hosted on a Windows Server 2003 computer, then the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service account must belong to the Performance Monitor Users security group or the local Administrators group.</span></span> <span data-ttu-id="bc4da-188">否则，数据收集将失败并且具有拒绝访问错误。</span><span class="sxs-lookup"><span data-stu-id="bc4da-188">Otherwise, data collection will fail with an access denied error.</span></span> <span data-ttu-id="bc4da-189">若要将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理服务帐户添加到性能监视器用户安全组中，请使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="bc4da-189">To add a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service account to the Performance Monitor Users security group, use the following steps:</span></span>  
  
    1.  <span data-ttu-id="bc4da-190">依次打开 **“计算机管理”**、 **“本地用户和组”**、 **“组”**。</span><span class="sxs-lookup"><span data-stu-id="bc4da-190">Open **Computer Management**, then **Local Users and Groups**, then **Groups**.</span></span>  
  
    2.  <span data-ttu-id="bc4da-191">右键单击 **“性能监视器用户”** ，然后选择 **“添加到组”**。</span><span class="sxs-lookup"><span data-stu-id="bc4da-191">Right-click **Performance Monitor Users** and select **Add to Group**.</span></span>  
  
    3.  <span data-ttu-id="bc4da-192">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="bc4da-192">Click **Add**.</span></span>  
  
    4.  <span data-ttu-id="bc4da-193">输入 SQL Server 代理服务正基于其运行的帐户，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="bc4da-193">Enter the account that the SQL Server Agent service is running under, then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="bc4da-194">如果在将用户添加到该组之前，该 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例已向 UCP 注册，则重新启动 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理服务。</span><span class="sxs-lookup"><span data-stu-id="bc4da-194">If the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] was already enrolled with the UCP before adding the user to this group, restart the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc4da-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc4da-195">See Also</span></span>  
 <span data-ttu-id="bc4da-196">[SQL Server 实用工具的功能和任务](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="bc4da-196">[SQL Server Utility Features and Tasks](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="bc4da-197">SQL Server 资源运行状况故障排除（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="bc4da-197">Troubleshoot SQL Server Resource Health &#40;SQL Server Utility&#41;</span></span>](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)
