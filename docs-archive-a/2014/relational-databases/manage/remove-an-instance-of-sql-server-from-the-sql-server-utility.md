---
title: 从 SQL Server 实用工具中删除 SQL Server 实例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.utility.remove.f1
ms.assetid: ae1d126a-46d2-47bf-b339-17c743df6491
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c09897fcd3ac6d82308288391cf54176eef49d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591334"
---
# <a name="remove-an-instance-of-sql-server-from-the-sql-server-utility"></a><span data-ttu-id="2507e-102">从 SQL Server 实用工具中删除 SQL Server 实例</span><span class="sxs-lookup"><span data-stu-id="2507e-102">Remove an Instance of SQL Server from the SQL Server Utility</span></span>
  <span data-ttu-id="2507e-103">使用以下步骤从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例。</span><span class="sxs-lookup"><span data-stu-id="2507e-103">Use the following steps to remove a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="2507e-104">此过程从 UCP 列表视图中删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，并且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具数据收集将停止。</span><span class="sxs-lookup"><span data-stu-id="2507e-104">This procedure removes the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the UCP list view and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility data collection stops.</span></span> <span data-ttu-id="2507e-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例不卸载。</span><span class="sxs-lookup"><span data-stu-id="2507e-105">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not uninstalled.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2507e-106">在您使用此过程从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例前，请确保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 SQL Server 代理服务正在要删除的实例上运行。</span><span class="sxs-lookup"><span data-stu-id="2507e-106">Before you use this procedure to remove an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, make sure that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and SQL Server Agent services are running on the instance to remove.</span></span>  
  
1.  <span data-ttu-id="2507e-107">从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的实用工具资源管理器中，单击 **“托管实例”** 。</span><span class="sxs-lookup"><span data-stu-id="2507e-107">From the Utility Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click on **Managed Instances**.</span></span> <span data-ttu-id="2507e-108">观察实用工具资源管理器内容窗格中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例的列表视图。</span><span class="sxs-lookup"><span data-stu-id="2507e-108">Observe the list view of managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the Utility Explorer content pane.</span></span>  
  
2.  <span data-ttu-id="2507e-109">在该列表视图的 **“SQL Server 实例名称”** 列中，选择要从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具删除的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="2507e-109">In the **SQL Server Instance Name** column of the list view, select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to remove from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="2507e-110">右键单击要删除的实例，然后选择“删除托管实例…”。</span><span class="sxs-lookup"><span data-stu-id="2507e-110">Right-click on the instance to remove, and select **Remove Managed Instance...**.</span></span>  
  
3.  <span data-ttu-id="2507e-111">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的管理员权限指定凭据：单击“连接...”，确认“连接到服务器”对话框中的信息，然后单击“连接”。  </span><span class="sxs-lookup"><span data-stu-id="2507e-111">Specify credentials with administrator privileges for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: Click **Connect...**, verify the information in the **Connect to Server** dialog box, then click **Connect**.</span></span> <span data-ttu-id="2507e-112">您将在 **“删除托管实例”** 对话框中看到登录信息。</span><span class="sxs-lookup"><span data-stu-id="2507e-112">You will see the login information on the **Remove Managed Instance** dialog.</span></span>  
  
4.  <span data-ttu-id="2507e-113">若要确认该操作，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="2507e-113">To confirm the operation, click **OK**.</span></span> <span data-ttu-id="2507e-114">若要退出该操作，请单击 **“取消”** 。</span><span class="sxs-lookup"><span data-stu-id="2507e-114">To quit the operation, click **Cancel**.</span></span>  
  
## <a name="manually-remove-a-managed-instance-of-sql-server-from-a-sql-server-utility"></a><span data-ttu-id="2507e-115">手动从 SQL Server 实用工具中删除 SQL Server 的托管实例</span><span class="sxs-lookup"><span data-stu-id="2507e-115">Manually Remove a Managed Instance of SQL Server from a SQL Server Utility</span></span>  
 <span data-ttu-id="2507e-116">此过程从 UCP 列表视图中删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例并且停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具数据收集。</span><span class="sxs-lookup"><span data-stu-id="2507e-116">This procedure removes the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the UCP list view and stops [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility data collection.</span></span> <span data-ttu-id="2507e-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例不卸载。</span><span class="sxs-lookup"><span data-stu-id="2507e-117">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not uninstalled.</span></span>  
  
 <span data-ttu-id="2507e-118">使用 PowerShell 从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例。</span><span class="sxs-lookup"><span data-stu-id="2507e-118">To use PowerShell to remove a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="2507e-119">此脚本执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2507e-119">This script performs the following operations:</span></span>  
  
-   <span data-ttu-id="2507e-120">按服务器实例名称获取 UCP。</span><span class="sxs-lookup"><span data-stu-id="2507e-120">Gets the UCP by server instance name.</span></span>  
  
-   <span data-ttu-id="2507e-121">从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例。</span><span class="sxs-lookup"><span data-stu-id="2507e-121">Removes the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
```powershell
# Get Ucp connection  
$UcpServerInstanceName = "ComputerName\InstanceName";  
$UtilityInstance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $UcpServerInstanceName;  
$UcpConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $UtilityInstance.ConnectionContext.SqlConnectionObject;  
$Utility = [Microsoft.SqlServer.Management.Utility.Utility]::Connect($UcpConnection);  
  
# Now remove the ManagedInstance from the SQL Server Utility  
$ServerInstanceName = "ComputerName\InstanceName";  
$Instance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $ServerInstanceName;  
$InstanceConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $Instance.ConnectionContext.SqlConnectionObject;  
$ManagedInstance = $Utility.ManagedInstances[$ServerInstanceName];  
$ManagedInstance.Remove($InstanceConnection);  
```  
  
<span data-ttu-id="2507e-122">务必 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 严格按照存储在中的实例名称进行引用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2507e-122">It's important to refer to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name exactly as it is stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2507e-123">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的区分大小写的实例上，必须使用与 @@SERVERNAME 返回的完全一致的大小写来指定实例名称。</span><span class="sxs-lookup"><span data-stu-id="2507e-123">On a case-sensitive instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must specify the instance name using the exact casing as returned by @@SERVERNAME.</span></span> 

<span data-ttu-id="2507e-124">若要获取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的托管实例的实例名称，请对该托管实例运行以下查询：</span><span class="sxs-lookup"><span data-stu-id="2507e-124">To get the instance name for the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], run this query on the managed instance:</span></span>  
  
```sql
select @@SERVERNAME AS instance_name  
```  
  
 <span data-ttu-id="2507e-125">此时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例将从 UCP 完全删除。</span><span class="sxs-lookup"><span data-stu-id="2507e-125">At this point, the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is fully removed from the UCP.</span></span> <span data-ttu-id="2507e-126">在您下次刷新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具的数据时，该托管实例将从列表视图中消失。</span><span class="sxs-lookup"><span data-stu-id="2507e-126">It disappears from the list view the next time you refresh data for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="2507e-127">此状态完全等同于用户成功在 SSMS 用户界面中完成删除托管实例操作。</span><span class="sxs-lookup"><span data-stu-id="2507e-127">This state is identical to a user successfully going through the remove managed instance operation in the SSMS user interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2507e-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2507e-128">See Also</span></span>  
 <span data-ttu-id="2507e-129">[使用实用工具资源管理器管理 SQL Server 实用工具](use-utility-explorer-to-manage-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="2507e-129">[Use Utility Explorer to Manage the SQL Server Utility](use-utility-explorer-to-manage-the-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="2507e-130">SQL Server 实用工具故障排除</span><span class="sxs-lookup"><span data-stu-id="2507e-130">Troubleshoot the SQL Server Utility</span></span>](../../database-engine/troubleshoot-the-sql-server-utility.md)  
