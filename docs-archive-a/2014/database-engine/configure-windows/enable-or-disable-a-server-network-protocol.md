---
title: 启用或禁用服务器网络协议 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- network protocols [SQL Server], disabling
- remote connections [SQL Server], enabling using Configuration Manager
- protocols [SQL Server], enabling using Configuration Manager
- protocols [SQL Server], disabling using Configuration Manager
- disabling network protocols, Configuration Manager
- network protocols [SQL Server], enabling
- enabling network protocols, Configuration Manager
- surface area configuration [SQL Server], connection protocols
- connections [SQL Server], enabling remote using Configuration Manager
ms.assetid: ec5ccb69-61c9-4576-8843-014b976fd46e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 737edae84ff284ed726ade69cb48e574b830611e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689582"
---
# <a name="enable-or-disable-a-server-network-protocol"></a><span data-ttu-id="280da-102">启用或禁用服务器网络协议</span><span class="sxs-lookup"><span data-stu-id="280da-102">Enable or Disable a Server Network Protocol</span></span>
  <span data-ttu-id="280da-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所有网络协议都是由  安装程序安装的，可以启用也可以禁用这些网络协议。</span><span class="sxs-lookup"><span data-stu-id="280da-103">All network protocols are installed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, but may or may not be enabled.</span></span> <span data-ttu-id="280da-104">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 本主题介绍如何通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器或 PowerShell，在  中启用或禁用服务器网络协议。</span><span class="sxs-lookup"><span data-stu-id="280da-104">This topic describes how to enable or disable a server network protocol in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager or PowerShell.</span></span> <span data-ttu-id="280da-105">必须停止并重新启动 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，更改才能生效。</span><span class="sxs-lookup"><span data-stu-id="280da-105">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be stopped and restarted for the change to take effect.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="280da-106">在安装 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 过程中，为 BUILTIN\Users 组添加一个登录名。</span><span class="sxs-lookup"><span data-stu-id="280da-106">During setup of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] a login is added for the BUILTIN\Users group.</span></span> <span data-ttu-id="280da-107">这可以使计算机的所有通过身份验证的用户作为 public 角色成员访问 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="280da-107">This allows all authenticated users of the computer to access the instance of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] as a member of the public role.</span></span> <span data-ttu-id="280da-108">可以安全地删除 BUILTIN\Users 登录名，以限制 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 对具有单独登录名或为使用此登录名的其他 Windows 组成员的计算机用户的访问。</span><span class="sxs-lookup"><span data-stu-id="280da-108">The BUILTIN\Users login can be safely removed to restrict [!INCLUDE[ssDE](../../includes/ssde-md.md)] access to computer users who have individual logins or are members of other Windows groups with logins.</span></span>  
  
> [!WARNING]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="280da-109">的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 数据提供程序支持 TLS 1.0 和 SSL 3.0。</span><span class="sxs-lookup"><span data-stu-id="280da-109">and [!INCLUDE[msCoName](../../includes/msconame-md.md)] data providers for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support TLS 1.0 and SSL 3.0.</span></span> <span data-ttu-id="280da-110">如果通过在操作系统 SChannel 层中进行更改来强制使用不同的协议（例如 TLS 1.1 或 TLS 1.2），你可能无法连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="280da-110">If you enforce a different protocol (such as TLS 1.1 or TLS 1.2) by making changes in the operating system SChannel layer, your connections to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might fail.</span></span>  
  
 <span data-ttu-id="280da-111">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="280da-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="280da-112">**使用以下工具启用或禁用服务器网络协议：**</span><span class="sxs-lookup"><span data-stu-id="280da-112">**To enable or disable a server network protocol using:**</span></span>  
  
     [<span data-ttu-id="280da-113">SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="280da-113">SQL Server Configuration Manager</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="280da-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="280da-114">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="280da-115">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="280da-115">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-enable-a-server-network-protocol"></a><span data-ttu-id="280da-116">启用服务器网络协议</span><span class="sxs-lookup"><span data-stu-id="280da-116">To enable a server network protocol</span></span>  
  
1.  <span data-ttu-id="280da-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 配置管理器的控制台窗格中，展开“SQL Server 网络配置”。</span><span class="sxs-lookup"><span data-stu-id="280da-117">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the console pane, expand **SQL Server  Network Configuration**.</span></span>  
  
2.  <span data-ttu-id="280da-118">在控制台窗格中，单击“\<instance name> 的协议”。</span><span class="sxs-lookup"><span data-stu-id="280da-118">In the console pane, click **Protocols for** *\<instance name>*.</span></span>  
  
3.  <span data-ttu-id="280da-119">在细节窗格中，右键单击要更改的协议，再单击“启用”  或“禁用” 。</span><span class="sxs-lookup"><span data-stu-id="280da-119">In the details pane, right-click the protocol you want to change, and then click **Enable** or **Disable**.</span></span>  
  
4.  <span data-ttu-id="280da-120">在控制台窗格中，单击“SQL Server 服务”。</span><span class="sxs-lookup"><span data-stu-id="280da-120">In the console pane, click **SQL Server Services**.</span></span>  
  
5.  <span data-ttu-id="280da-121">在详细信息窗格中，右键单击 " **SQL Server (" ***\<instance name>***) **"，然后单击"**重新启动**"以停止并重新启动该 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="280da-121">In the details pane, right-click **SQL Server (***\<instance name>***)**, and then click **Restart**, to stop and restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
##  <a name="using-sql-server-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="280da-122">使用 SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="280da-122">Using SQL Server PowerShell</span></span>  
  
#### <a name="to-enable-a-server-network-protocol-using-powershell"></a><span data-ttu-id="280da-123">使用 PowerShell 启用服务器网络协议</span><span class="sxs-lookup"><span data-stu-id="280da-123">To Enable a Server Network Protocol Using PowerShell</span></span>  
  
1.  <span data-ttu-id="280da-124">使用管理员权限打开一个命令提示符。</span><span class="sxs-lookup"><span data-stu-id="280da-124">Using administrator permissions open a command prompt.</span></span>  
  
2.  <span data-ttu-id="280da-125">可以从任务栏启动 Windows PowerShell 2.0，也可以通过依次单击“开始”、“所有程序”、“附件”、“Windows PowerShell”、“Windows PowerShell”来启动。</span><span class="sxs-lookup"><span data-stu-id="280da-125">Start Windows PowerShell 2.0 from the taskbar, or click Start, then All Programs, then Accessories, then Windows PowerShell, then Windows PowerShell.</span></span>  
  
3.  <span data-ttu-id="280da-126">通过输入导入**sqlps**模块`Import-Module "sqlps"`</span><span class="sxs-lookup"><span data-stu-id="280da-126">Import the **sqlps** module by entering `Import-Module "sqlps"`</span></span>  
  
4.  <span data-ttu-id="280da-127">执行以下语句以启用 TCP 和 Named Pipes 协议。</span><span class="sxs-lookup"><span data-stu-id="280da-127">Execute the following statements to enable both the TCP and named pipes protocols.</span></span> <span data-ttu-id="280da-128">`<computer_name>` 将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]替换为运行  的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="280da-128">Replace `<computer_name>` with the name of the computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="280da-129">`MSSQLSERVER` 如果您在配置命名实例，请将  替换为该实例的名称。</span><span class="sxs-lookup"><span data-stu-id="280da-129">If you are configuring a named instance, replace `MSSQLSERVER` with the instance name.</span></span>  
  
     <span data-ttu-id="280da-130">`IsEnabled` 若要禁用协议，请将 `$false`属性设置为 。</span><span class="sxs-lookup"><span data-stu-id="280da-130">To disable protocols, set the `IsEnabled` properties to `$false`.</span></span>  
  
    ```powershell
    $smo = 'Microsoft.SqlServer.Management.Smo.'  
    $wmi = new-object ($smo + 'Wmi.ManagedComputer').  
  
    # List the object properties, including the instance names.  
    $Wmi  
  
    # Enable the TCP protocol on the default instance.  
    $uri = "ManagedComputer[@Name='<computer_name>']/ ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
    $Tcp = $wmi.GetSmoObject($uri)  
    $Tcp.IsEnabled = $true  
    $Tcp.Alter()  
    $Tcp  
  
    # Enable the named pipes protocol for the default instance.  
    $uri = "ManagedComputer[@Name='<computer_name>']/ ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Np']"  
    $Np = $wmi.GetSmoObject($uri)  
    $Np.IsEnabled = $true  
    $Np.Alter()  
    $Np  
    ```  
  
#### <a name="to-configure-the-protocols-for-the-local-computer"></a><span data-ttu-id="280da-131">为本地计算机配置协议</span><span class="sxs-lookup"><span data-stu-id="280da-131">To configure the protocols for the local computer</span></span>  
  
-   <span data-ttu-id="280da-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 当脚本在本地运行并配置本地计算机时， PowerShell 可以通过动态确定本地计算机的名称使脚本更为灵活。</span><span class="sxs-lookup"><span data-stu-id="280da-132">When the script is run locally and configures the local computer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell can make the script more flexible by dynamically determining the local computer name.</span></span> <span data-ttu-id="280da-133">`$uri` 若要检索本地计算机的名称，请将设置  变量的行替换为以下行。</span><span class="sxs-lookup"><span data-stu-id="280da-133">To retrieve the local computer name, replace the line setting the `$uri` variable with the following line.</span></span>  
  
    ```powershell
    $uri = "ManagedComputer[@Name='" + (Get-Item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
    ```  
  
#### <a name="to-restart-the-database-engine-by-using-sql-server-powershell"></a><span data-ttu-id="280da-134">使用 SQL Server PowerShell 重新启动数据库引擎</span><span class="sxs-lookup"><span data-stu-id="280da-134">To restart the Database Engine by using SQL Server PowerShell</span></span>  
  
-   <span data-ttu-id="280da-135">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 启用或禁用了协议后，必须停止并重新启动才能使更改生效。</span><span class="sxs-lookup"><span data-stu-id="280da-135">After you enable or disable protocols, you must stop and restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for the change to take effect.</span></span> <span data-ttu-id="280da-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 执行以下语句，通过使用  PowerShell 来停止和启动默认实例。</span><span class="sxs-lookup"><span data-stu-id="280da-136">Execute the following statements to stop and start the default instance by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell.</span></span> <span data-ttu-id="280da-137">`'MSSQLSERVER'` 若要停止和启动命名实例，请将 `'MSSQL$<instance_name>'`替换为 。</span><span class="sxs-lookup"><span data-stu-id="280da-137">To stop and start a named instance replace `'MSSQLSERVER'` with `'MSSQL$<instance_name>'`.</span></span>  
  
    ```powershell
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\<computer_name>  
    $Wmi = (Get-Item .).ManagedComputer  
    # Get a reference to the default instance of the Database Engine.  
    $DfltInstance = $Wmi.Services['MSSQLSERVER']  
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Start the service again.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache and display the state of the service.  
    $DfltInstance.Refresh(); $DfltInstance  
    ```  
