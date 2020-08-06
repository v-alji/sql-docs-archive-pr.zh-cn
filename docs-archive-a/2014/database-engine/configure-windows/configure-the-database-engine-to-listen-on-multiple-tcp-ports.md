---
title: 将数据库引擎配置为侦听多个 TCP 端口 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- ports [SQL Server], multiple
- TDS
- listen on multiple ports
- endpoints [SQL Server], TDS
- adding ports
- tabular data stream
- multiple ports
ms.assetid: 8e955033-06ef-403f-b813-3d8241b62f1f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab803bcaa5ab6b6187c1a994abef02f81ae105c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578434"
---
# <a name="configure-the-database-engine-to-listen-on-multiple-tcp-ports"></a><span data-ttu-id="48781-102">将数据库引擎配置为侦听多个 TCP 端口</span><span class="sxs-lookup"><span data-stu-id="48781-102">Configure the Database Engine to Listen on Multiple TCP Ports</span></span>
  <span data-ttu-id="48781-103">本主题说明如何使用 SQL Server 配置管理器在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中将 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 配置为侦听多个 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="48781-103">This topic describes how to configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on multiple TCP ports in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="48781-104">为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]启用 TCP/IP 后， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将侦听连接点上是否有传入的连接（由 IP 地址和 TCP 端口号组成）。下列过程将创建一个表格格式数据流 (TDS) 端点，以便 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 侦听其他 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="48781-104">When TCP/IP is enabled for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssDE](../../includes/ssde-md.md)] will listen for incoming connections on a connection point consisting of an IP address and TCP port number.The following procedures create a tabular data stream (TDS) endpoint, so that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will listen on an additional TCP port.</span></span>  
  
 <span data-ttu-id="48781-105">创建第二个 TDS 端点的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="48781-105">Possible reasons to create a second TDS endpoint include:</span></span>  
  
-   <span data-ttu-id="48781-106">通过将防火墙配置为限制访问特定子网上的本地客户机的默认端点，提高安全性。</span><span class="sxs-lookup"><span data-stu-id="48781-106">Increase security by configuring the firewall to restrict access to the default endpoint to local client computers on a specific subnet.</span></span> <span data-ttu-id="48781-107">通过创建防火墙对 Internet 公开的新端点并限制服务器支持组对此端点的连接权限，维护支持组对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 Internet 访问。</span><span class="sxs-lookup"><span data-stu-id="48781-107">Maintain Internet access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for your support team by creating a new endpoint that the firewall exposes to the Internet, and restricting connection rights to this endpoint to your server support team.</span></span>  
  
-   <span data-ttu-id="48781-108">使用非一致内存访问 (NUMA) 时，将连接与特定处理器关联。</span><span class="sxs-lookup"><span data-stu-id="48781-108">Affinitizing connections to specific processors when using Non-Uniform Memory Access (NUMA).</span></span>  
  
 <span data-ttu-id="48781-109">配置 TDS 端点的步骤如下，但可以不按顺序进行：</span><span class="sxs-lookup"><span data-stu-id="48781-109">Configuring a TDS endpoint consists of the following steps, which can be done in any order:</span></span>  
  
-   <span data-ttu-id="48781-110">为 TCP 端口创建 TDS 端点，恢复对默认端点的访问权限（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="48781-110">Create the TDS endpoint for the TCP port, and restore access to the default endpoint if appropriate.</span></span>  
  
-   <span data-ttu-id="48781-111">对所需的服务器主体授予对端点的访问权限。</span><span class="sxs-lookup"><span data-stu-id="48781-111">Grant access to the endpoint to the desired server principals.</span></span>  
  
-   <span data-ttu-id="48781-112">指定所选 IP 地址的 TCP 端口号。</span><span class="sxs-lookup"><span data-stu-id="48781-112">Specify the TCP port number for the selected IP address.</span></span>  
  
 <span data-ttu-id="48781-113">有关默认 Windows 防火墙设置的详细信息以及有关影响数据库引擎、Analysis Services、Reporting Services 和 Integration Services 的 TCP 端口的说明，请参阅 [配置 Windows 防火墙以允许 SQL Server 访问](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="48781-113">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the Database Engine, Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-create-a-tds-endpoint"></a><span data-ttu-id="48781-114">创建 TDS 端点</span><span class="sxs-lookup"><span data-stu-id="48781-114">To create a TDS endpoint</span></span>  
  
-   <span data-ttu-id="48781-115">发出以下语句，为服务器上所有可用的 TCP 地址的端口 1500 创建名为 **CustomConnection** 的端点。</span><span class="sxs-lookup"><span data-stu-id="48781-115">Issue the following statement to create an endpoint named **CustomConnection** for port 1500 for all available TCP addresses on the server.</span></span>  
  
    ```  
    USE master;  
    GO  
    CREATE ENDPOINT [CustomConnection]  
    STATE = STARTED  
    AS TCP  
       (LISTENER_PORT = 1500, LISTENER_IP =ALL)  
    FOR TSQL() ;  
    GO  
    ```  
  
 <span data-ttu-id="48781-116">创建新的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 端点时，将撤消默认 TDS 端点的 **public** 连接权限。</span><span class="sxs-lookup"><span data-stu-id="48781-116">When you create a new [!INCLUDE[tsql](../../includes/tsql-md.md)] endpoint, connect permissions for **public** are revoked for the default TDS endpoint.</span></span> <span data-ttu-id="48781-117">如果默认端点需要访问 **public** 组，请使用 `GRANT CONNECT ON ENDPOINT::[TSQL Default TCP] to [public];` 语句重新应用此权限。</span><span class="sxs-lookup"><span data-stu-id="48781-117">If access to the **public** group is needed for the default endpoint, reapply this permission by using the `GRANT CONNECT ON ENDPOINT::[TSQL Default TCP] to [public];` statement.</span></span>  
  
#### <a name="to-grant-access-to-the-endpoint"></a><span data-ttu-id="48781-118">授予对端点的访问权限</span><span class="sxs-lookup"><span data-stu-id="48781-118">To grant access to the endpoint</span></span>  
  
-   <span data-ttu-id="48781-119">发出以下语句，对 corp 域中的 SQLSupport 组授予对 **CustomConnection** 端点的访问权限。</span><span class="sxs-lookup"><span data-stu-id="48781-119">Issue the following statement to grant access to the **CustomConnection** endpoint to the SQLSupport group in the corp domain.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[CustomConnection] to [corp\SQLSupport] ;  
    GO  
    ```  
  
#### <a name="to-configure-the-sql-server-database-engine-to-listen-on-an-additional-tcp-port"></a><span data-ttu-id="48781-120">将 SQL Server 数据库引擎配置为侦听其他 TCP 端口</span><span class="sxs-lookup"><span data-stu-id="48781-120">To configure the SQL Server Database Engine to listen on an additional TCP port</span></span>  
  
1.  <span data-ttu-id="48781-121">在 SQL Server 配置管理器中，展开“SQL Server 网络配置”，然后单击 _<instance_name>_ 的“协议”。</span><span class="sxs-lookup"><span data-stu-id="48781-121">In SQL Server Configuration Manager, expand **SQL Server Network Configuration**, and then click **Protocols for**_<instance_name>_.</span></span>  
  
2.  <span data-ttu-id="48781-122">展开 _<instance_name>_ 的“协议”，然后单击“TCP/IP”。</span><span class="sxs-lookup"><span data-stu-id="48781-122">Expand **Protocols for**_<instance_name>_, and then click **TCP/IP**.</span></span>  
  
3.  <span data-ttu-id="48781-123">在右窗格中，右键单击要启用的每个禁用的 IP 地址，再单击“启用”。</span><span class="sxs-lookup"><span data-stu-id="48781-123">In the right pane, right-click each disabled IP address that you want to enable, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="48781-124">右键单击“IPAll”，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="48781-124">Right-click **IPAll**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="48781-125">在 **“TCP 端口”** 框中，键入要 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 侦听的端口（用逗号分隔）。</span><span class="sxs-lookup"><span data-stu-id="48781-125">In the **TCP Port** box, type the ports that you want the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on, separated by commas.</span></span> <span data-ttu-id="48781-126">在本示例中，如果列出了默认端口1433，请键入，然后 `,1500` `1433,1500` 单击 **"确定**"。</span><span class="sxs-lookup"><span data-stu-id="48781-126">In our example, if the default port 1433 is listed, type `,1500` so the box reads `1433,1500`, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="48781-127">如果不想对所有 IP 地址启用端口，则在属性框中只为所需地址配置其他端口。</span><span class="sxs-lookup"><span data-stu-id="48781-127">If you are not enabling the port on all IP addresses, configure the additional port in the property box for only for the desired address.</span></span> <span data-ttu-id="48781-128">然后，在控制台窗格中，右键单击“TCP/IP”，单击“属性”，然后在“全部侦听”框中选择“否”。</span><span class="sxs-lookup"><span data-stu-id="48781-128">Then, in the console pane, right-click **TCP/IP**, click **Properties**, and in the **Listen All** box, select **No**.</span></span>  
  
6.  <span data-ttu-id="48781-129">在左窗格中，单击 **“SQL Server 服务”** 。</span><span class="sxs-lookup"><span data-stu-id="48781-129">In the left pane, click **SQL Server Services**.</span></span>  
  
7.  <span data-ttu-id="48781-130">在右侧窗格中，右键单击“SQL Server  _<instance_name>_ ”，然后单击“重新启动”。</span><span class="sxs-lookup"><span data-stu-id="48781-130">In the right pane, right-click **SQL Server**_<instance_name>_, and then click **Restart**.</span></span>  
  
     <span data-ttu-id="48781-131">[!INCLUDE[ssDE](../../includes/ssde-md.md)]重新启动后，错误日志将列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 要侦听的端口。</span><span class="sxs-lookup"><span data-stu-id="48781-131">When the [!INCLUDE[ssDE](../../includes/ssde-md.md)] restarts, the Error log will list the ports on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is listening.</span></span>  
  
#### <a name="to-connect-to-the-new-endpoint"></a><span data-ttu-id="48781-132">连接到新端点</span><span class="sxs-lookup"><span data-stu-id="48781-132">To connect to the new endpoint</span></span>  
  
-   <span data-ttu-id="48781-133">发出以下语句，以使用可信连接并假定用户为 [corp\SQLSupport] 组的成员，连接到名为 ACCT 的服务器上的 SQL Server 默认实例的 **CustomConnection** 端点。</span><span class="sxs-lookup"><span data-stu-id="48781-133">Issue the following statement to connect to the **CustomConnection** endpoint of the default instance of SQL Server on the server named ACCT, using a trusted connection, and assuming the user is a member of the [corp\SQLSupport] group.</span></span>  
  
    ```  
    sqlcmd -SACCT,1500  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="48781-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48781-134">See Also</span></span>  
 <span data-ttu-id="48781-135">[CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="48781-135">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="48781-136">[DROP ENDPOINT (Transact SQL)](/sql/t-sql/statements/drop-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="48781-136">[DROP ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="48781-137">[GRANT 终结点权限 (Transact-SQL)](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="48781-137">[GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span></span>  
 [<span data-ttu-id="48781-138">将 TCP IP 端口映射到 NUMA 节点 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="48781-138">Map TCP IP Ports to NUMA Nodes &#40;SQL Server&#41;</span></span>](map-tcp-ip-ports-to-numa-nodes-sql-server.md)  
  
  
