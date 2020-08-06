---
title: 将服务器配置为侦听特定 TCP 端口 (SQL Server 配置管理器) |Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- fixed port
- static ports
- ports [SQL Server], assigning numbers
- assigning port numbers
- dynamic ports [SQL Server]
- TCP/IP [SQL Server], port numbers
ms.assetid: 2276a5ed-ae3f-4855-96d8-f5bf01890640
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4feb740910c65580e8ea3170d03481e6cb628860
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577845"
---
# <a name="configure-a-server-to-listen-on-a-specific-tcp-port-sql-server-configuration-manager"></a><span data-ttu-id="30e20-102">配置服务器以侦听特定 TCP 端口（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="30e20-102">Configure a Server to Listen on a Specific TCP Port (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="30e20-103">本主题说明如何使用 SQL Server 配置管理器配置 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例以便侦听特定的固定端口。</span><span class="sxs-lookup"><span data-stu-id="30e20-103">This topic describes how to configure an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] to listen on a specific fixed port by using the SQL Server Configuration Manager.</span></span> <span data-ttu-id="30e20-104">如果启用， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的默认实例将侦听 TCP 端口 1433。</span><span class="sxs-lookup"><span data-stu-id="30e20-104">If enabled, the default instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] listens on TCP port 1433.</span></span> <span data-ttu-id="30e20-105">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 和 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 的命名实例配置为使用动态端口。</span><span class="sxs-lookup"><span data-stu-id="30e20-105">Named instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssEW](../../includes/ssew-md.md)] are configured for dynamic ports.</span></span> <span data-ttu-id="30e20-106">这意味着启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务时，它们将选择可用的端口。</span><span class="sxs-lookup"><span data-stu-id="30e20-106">This means they select an available port when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service is started.</span></span> <span data-ttu-id="30e20-107">在通过防火墙连接到命名实例时，请配置 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 以侦听特定端口，以便能够在防火墙中打开相应的端口。</span><span class="sxs-lookup"><span data-stu-id="30e20-107">When you are connecting to a named instance through a firewall, configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on a specific port, so that the appropriate port can be opened in the firewall.</span></span>  
  
 <span data-ttu-id="30e20-108">有关默认 Windows 防火墙设置的详细信息以及有关影响数据库引擎、Analysis Services、Reporting Services 和 Integration Services 的 TCP 端口的说明，请参阅 [配置 Windows 防火墙以允许 SQL Server 访问](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="30e20-108">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the Database Engine, Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="30e20-109">选择端口号时，请查看 [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers) 以了解分配给特定应用程序的端口号列表。</span><span class="sxs-lookup"><span data-stu-id="30e20-109">When selecting a port number, consult [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers) for a list of port numbers that are assigned to specific applications.</span></span> <span data-ttu-id="30e20-110">选择一个未分配的端口号。</span><span class="sxs-lookup"><span data-stu-id="30e20-110">Select an unassigned port number.</span></span> <span data-ttu-id="30e20-111">更多详细信息，请参阅 [TCP/IP 的默认动态端口范围在 Windows Vista 和 Windows Server 2008 中已更改](https://support.microsoft.com/kb/929851)。</span><span class="sxs-lookup"><span data-stu-id="30e20-111">For more information, see [The default dynamic port range for TCP/IP has changed in Windows Vista and in Windows Server 2008](https://support.microsoft.com/kb/929851).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="30e20-112">重新启动时，数据库引擎开始侦听新端口。</span><span class="sxs-lookup"><span data-stu-id="30e20-112">The Database Engine begins listening on a new port when restarted.</span></span> <span data-ttu-id="30e20-113">但是， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务监视注册表并在配置更改时报告新端口号，即使数据库引擎可能未使用该端口。</span><span class="sxs-lookup"><span data-stu-id="30e20-113">However the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service monitors the registry and reports the new port number as soon as the configuration is changed, even though the Database Engine might not be using it.</span></span> <span data-ttu-id="30e20-114">重新启动数据库引擎可确保一致性并避免连接失败。</span><span class="sxs-lookup"><span data-stu-id="30e20-114">Restart the Database Engine to ensure consistency and avoid connection failures.</span></span>  
  
 <span data-ttu-id="30e20-115">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="30e20-115">**In This Topic**</span></span>  
  
-   <span data-ttu-id="30e20-116">**若要配置服务器以侦听特定 TCP 端口，请使用：**</span><span class="sxs-lookup"><span data-stu-id="30e20-116">**To configure a server to listen on a specific TCP port, using:**</span></span>  
  
     [<span data-ttu-id="30e20-117">SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="30e20-117">SQL Server Configuration Manager</span></span>](#SSMSProcedure)  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="30e20-118">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="30e20-118">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-assign-a-tcpip-port-number-to-the-sql-server-database-engine"></a><span data-ttu-id="30e20-119">为 SQL Server 数据库引擎分配 TCP/IP 端口号</span><span class="sxs-lookup"><span data-stu-id="30e20-119">To assign a TCP/IP port number to the SQL Server Database Engine</span></span>  
  
1.  <span data-ttu-id="30e20-120">在 SQL Server 配置管理器的控制台窗格中，展开“SQL Server 网络配置”，展开“\<instance name> 的协议”，然后双击“TCP/IP”。</span><span class="sxs-lookup"><span data-stu-id="30e20-120">In SQL Server Configuration Manager, in the console pane, expand **SQL Server Network Configuration**, expand **Protocols for \<instance name>**, and then double-click **TCP/IP**.</span></span>  
  
2.  <span data-ttu-id="30e20-121">在“TCP/IP 属性”对话框的“IP 地址”选项卡上，将显示若干个 IP 地址，格式为：**IP1**、**IP2**...，一直到 **IPAll**。</span><span class="sxs-lookup"><span data-stu-id="30e20-121">In the **TCP/IP Properties** dialog box, on the **IP Addresses** tab, several IP addresses appear in the format **IP1**, **IP2**, up to **IPAll**.</span></span> <span data-ttu-id="30e20-122">这些 IP 地址中有一个是环回适配器的 IP 地址 (127.0.0.1)。</span><span class="sxs-lookup"><span data-stu-id="30e20-122">One of these is for the IP address of the loopback adapter, 127.0.0.1.</span></span> <span data-ttu-id="30e20-123">其他 IP 地址是计算机上的各个 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="30e20-123">Additional IP addresses appear for each IP Address on the computer.</span></span> <span data-ttu-id="30e20-124">右键单击每个地址，再单击\*\*\*\*“属性”，标识要配置的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="30e20-124">Right-click each address, and then click **Properties** to identify the IP address that you want to configure.</span></span>  
  
3.  <span data-ttu-id="30e20-125">如果 **“TCP 动态端口”** 对话框中包含 **0**，则表示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 正在侦听动态端口，请删除 0。</span><span class="sxs-lookup"><span data-stu-id="30e20-125">If the **TCP Dynamic Ports** dialog box contains **0**, indicating the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is listening on dynamic ports, delete the 0.</span></span>  
  
4.  <span data-ttu-id="30e20-126">在“IP_n_ 属性”区域框的“TCP 端口”框中，键入希望此 IP 地址侦听的端口号，然后单击“确定”   。</span><span class="sxs-lookup"><span data-stu-id="30e20-126">In the **IP**_n_ **Properties** area box, in the **TCP Port** box, type the port number you want this IP address to listen on, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="30e20-127">在控制台窗格中，单击“SQL Server 服务”。</span><span class="sxs-lookup"><span data-stu-id="30e20-127">In the console pane, click **SQL Server Services**.</span></span>  
  
6.  <span data-ttu-id="30e20-128">在详细信息窗格中，右键单击“SQL Server(\<instance name>)”，然后单击“重新启动”以停止并重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  。</span><span class="sxs-lookup"><span data-stu-id="30e20-128">In the details pane, right-click **SQL Server (**\<instance name>**)** and then click **Restart**, to stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="30e20-129">在配置完 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以侦听特定端口后，可以通过下列三种方式使用客户端应用程序连接到特定端口：</span><span class="sxs-lookup"><span data-stu-id="30e20-129">After you have configured [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on a specific port, there are three ways to connect to a specific port with a client application:</span></span>  
  
-   <span data-ttu-id="30e20-130">运行服务器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务以按名称连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="30e20-130">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service on the server to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance by name.</span></span>  
  
-   <span data-ttu-id="30e20-131">在客户端上创建一个别名，指定端口号。</span><span class="sxs-lookup"><span data-stu-id="30e20-131">Create an alias on the client, specifying the port number.</span></span>  
  
-   <span data-ttu-id="30e20-132">对客户端进行编程，以便使用自定义连接字符串进行连接。</span><span class="sxs-lookup"><span data-stu-id="30e20-132">Program the client to connect using a custom connection string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30e20-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30e20-133">See Also</span></span>  
 [<span data-ttu-id="30e20-134">创建或删除供客户端使用的服务器别名（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="30e20-134">Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;</span></span>](create-or-delete-a-server-alias-for-use-by-a-client.md)  
  
  
