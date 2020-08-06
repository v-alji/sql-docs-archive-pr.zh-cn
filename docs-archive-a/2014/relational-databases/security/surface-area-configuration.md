---
title: 外围应用配置器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- reducing attackable surface area
- upgrading SQL Server, security
- surface area configuration [SQL Server]
- surface area configuration [SQL Server], about surface area configuration
- attackable surface area [SQL Server]
- installing SQL Server, security
ms.assetid: f741169c-1453-4ad2-830b-bf2be27d712f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ef64fbbeb2b8953ff3816db63572b499d42f012e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688703"
---
# <a name="surface-area-configuration"></a><span data-ttu-id="d8b0b-102">Surface Area Configuration</span><span class="sxs-lookup"><span data-stu-id="d8b0b-102">Surface Area Configuration</span></span>
  <span data-ttu-id="d8b0b-103">在新安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的默认配置中，许多功能并未启用。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-103">In the default configuration of new installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], many features are not enabled.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d8b0b-104">只是有选择地安装和启动关键服务和功能，以最大限度地减少可能受到恶意用户攻击的功能数。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-104">selectively installs and starts only key services and features, to minimize the number of features that can be attacked by a malicious user.</span></span> <span data-ttu-id="d8b0b-105">系统管理员可以在安装时更改这些设置，也可以有选择地启用或禁用运行中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的功能。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-105">A system administrator can change these defaults at installation time and also selectively enable or disable features of a running instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d8b0b-106">此外，如果从其他计算机进行连接，则在配置协议之前某些组件可能不可用。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-106">Additionally, some components may not be available when connecting from other computers until protocols are configured.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8b0b-107">与新安装不同，升级期间不会关闭任何现有服务或功能；但在升级完成后可应用其他外围应用配置器选项。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-107">Unlike new installations, no existing services or features are turned off during an upgrade, but additional surface area configuration options can be applied after the upgrade is completed.</span></span>  
  
## <a name="protocols-connection-and-startup-options"></a><span data-ttu-id="d8b0b-108">协议、连接和启动选项</span><span class="sxs-lookup"><span data-stu-id="d8b0b-108">Protocols, Connection, and Startup Options</span></span>  
 <span data-ttu-id="d8b0b-109">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器可以启动和停止服务，配置启动选项，以及启用协议和其他连接选项。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-109">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to start and stop services, configure the startup options, and enable protocols and other connection options.</span></span>  
  
#### <a name="to-start-sql-server-configuration-manager"></a><span data-ttu-id="d8b0b-110">启动 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="d8b0b-110">To start SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="d8b0b-111">在 **“开始”** 菜单中，依次指向 **“所有程序”** 、 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-111">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
    -   <span data-ttu-id="d8b0b-112">使用 **“SQL Server 服务”** 区域可以启动组件并配置自动启动选项。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-112">Use the **SQL Server Services** area to start components and configure the automatic starting options.</span></span>  
  
    -   <span data-ttu-id="d8b0b-113">使用“SQL Server 网络配置”区域可以启用连接协议和连接选项（如，TCP/IP 固定端口或强制加密）。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-113">Use the **SQL Server Network Configuration** area to enable connection protocols, and connection options such as fixed TCP/IP ports, or forcing encryption.</span></span>  
  
 <span data-ttu-id="d8b0b-114">有关详细信息，请参阅 [SQL Server Configuration Manager](../sql-server-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-114">For more information, see [SQL Server Configuration Manager](../sql-server-configuration-manager.md).</span></span> <span data-ttu-id="d8b0b-115">此外，远程连接还取决于是否对防火墙进行了正确配置。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-115">Remote connectivity can also depend upon the correct configuration of a firewall.</span></span> <span data-ttu-id="d8b0b-116">有关详细信息，请参阅 [配置 Windows 防火墙以允许 SQL Server 访问](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-116">For more information, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
## <a name="enabling-and-disabling-features"></a><span data-ttu-id="d8b0b-117">启用和禁用功能</span><span class="sxs-lookup"><span data-stu-id="d8b0b-117">Enabling and Disabling Features</span></span>  
 <span data-ttu-id="d8b0b-118">可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的方面来配置启用和禁用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-118">Enabling and disabling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features can be configured using facets in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-configure-surface-area-using-facets"></a><span data-ttu-id="d8b0b-119">使用方面配置外围应用</span><span class="sxs-lookup"><span data-stu-id="d8b0b-119">To configure surface area using facets</span></span>  
  
1.  <span data-ttu-id="d8b0b-120">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的组件。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-120">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] connect to a component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="d8b0b-121">在对象资源管理器中，右键单击服务器，然后单击“方面”。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-121">In Object Explorer, right-click the server, and then click **Facets**.</span></span>  
  
3.  <span data-ttu-id="d8b0b-122">在“查看方面”对话框中，展开“方面”列表，然后选择相应的“外围应用配置器”方面（“外围应用配置器”、“Analysis Services 的外围应用配置器”或“Reporting Services 的外围应用配置器”）。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-122">In the **View Facets** dialog box, expand the **Facet** list, and select the appropriate **Surface Area Configuration** facet (**Surface Area Configuration**, **Surface Area Configuration for Analysis Services**, or **Surface Area Configuration for Reporting Services**).</span></span>  
  
4.  <span data-ttu-id="d8b0b-123">在 **“方面属性”** 区域，选择要用于每个属性的值。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-123">In the **Facet properties** area, select the values that you want for each property.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="d8b0b-124">若要定期检查某个方面的配置，请使用基于策略的管理。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-124">To periodically check the configuration of a facet, use Policy-Based Management.</span></span> <span data-ttu-id="d8b0b-125">有关基于策略的管理的详细信息，请参阅 [使用基于策略的管理来管理服务器](../policy-based-management/administer-servers-by-using-policy-based-management.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-125">For more information about Policy-Based Management, see [Administer Servers by Using Policy-Based Management](../policy-based-management/administer-servers-by-using-policy-based-management.md).</span></span>  
  
 <span data-ttu-id="d8b0b-126">也可以使用 `sp_configure` 存储过程来设置[!INCLUDE[ssDE](../../includes/ssde-md.md)]选项。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-126">You can also set [!INCLUDE[ssDE](../../includes/ssde-md.md)] options using the `sp_configure` stored procedure.</span></span> <span data-ttu-id="d8b0b-127">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-127">For more information, see [Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).</span></span>  
  
 <span data-ttu-id="d8b0b-128">若要更改 **的** EnableIntegrated Security [!INCLUDE[ssRS](../../includes/ssrs.md)]属性，请使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的属性设置。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-128">To change the **EnableIntegrated Security** property of [!INCLUDE[ssRS](../../includes/ssrs.md)], use the property settings in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d8b0b-129">若要更改“预定事件和报表传递”  属性和“Web 服务和 HTTP 访问”  属性，请编辑 **RSReportServer.config** 配置文件。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-129">To change the **Schedule events and report delivery** property and the **Web service and HTTP access** property, edit the **RSReportServer.config** configuration file.</span></span>  
  
## <a name="command-prompt-options"></a><span data-ttu-id="d8b0b-130">命令提示符选项</span><span class="sxs-lookup"><span data-stu-id="d8b0b-130">Command-prompt Options</span></span>  
 <span data-ttu-id="d8b0b-131">使用 **Invoke-PolicyEvaluation**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell cmdlet 可以调用外围应用配置器策略。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-131">Use the **Invoke-PolicyEvaluation**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell cmdlet to invoke Surface Area Configuration Policies.</span></span> <span data-ttu-id="d8b0b-132">有关详细信息，请参阅 [使用数据库引擎 cmdlets](../../database-engine/use-the-database-engine-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-132">For more information, see [Use the Database Engine cmdlets](../../database-engine/use-the-database-engine-cmdlets.md).</span></span>  
  
## <a name="soap-and-service-broker-endpoints"></a><span data-ttu-id="d8b0b-133">SOAP 和 Service Broker 端点</span><span class="sxs-lookup"><span data-stu-id="d8b0b-133">SOAP and Service Broker Endpoints</span></span>  
 <span data-ttu-id="d8b0b-134">若要关闭端点，请使用基于策略的管理。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-134">To turn endpoints off, use Policy-Based Management.</span></span> <span data-ttu-id="d8b0b-135">若要创建和更改端点的属性，可使用 [CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql) 和 [ALTER ENDPOINT (Transact-SQL)](/sql/t-sql/statements/alter-endpoint-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d8b0b-135">To create and alter the properties of endpoints, use [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) and [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="d8b0b-136">相关内容</span><span class="sxs-lookup"><span data-stu-id="d8b0b-136">Related Content</span></span>  
 [<span data-ttu-id="d8b0b-137">SQL Server 数据库引擎和 Azure SQL Database 的安全中心</span><span class="sxs-lookup"><span data-stu-id="d8b0b-137">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [<span data-ttu-id="d8b0b-138">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d8b0b-138">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
