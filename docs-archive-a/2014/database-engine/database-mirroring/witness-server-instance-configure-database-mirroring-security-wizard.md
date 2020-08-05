---
title: 见证服务器实例（配置数据库镜像安全向导） | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.witnsrvr.f1
ms.assetid: b5763663-984a-473b-93a3-6cd3322ad41c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fcea7d39e1bc2c6161b5c6e1edd4852d9fdeb073
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579760"
---
# <a name="witness-server-instance-configure-database-mirroring-security-wizard"></a><span data-ttu-id="bebc4-102">见证服务器实例（配置数据库镜像安全向导）</span><span class="sxs-lookup"><span data-stu-id="bebc4-102">Witness Server Instance (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="bebc4-103">对于作为会话的见证服务器的服务器实例，使用此页可以指定有关该服务器实例的信息。</span><span class="sxs-lookup"><span data-stu-id="bebc4-103">Use this page to specify information about the server instance that is to serve as the witness for the session.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bebc4-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的各版本中均未提供见证服务器实例。</span><span class="sxs-lookup"><span data-stu-id="bebc4-104">A witness server instance is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bebc4-105">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="bebc4-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="bebc4-106">**使用 SQL Server Management Studio 配置数据库镜像**</span><span class="sxs-lookup"><span data-stu-id="bebc4-106">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="bebc4-107">使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="bebc4-107">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="bebc4-108">启动配置数据库镜像安全向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="bebc4-108">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="bebc4-109">选项</span><span class="sxs-lookup"><span data-stu-id="bebc4-109">Options</span></span>  
 <span data-ttu-id="bebc4-110">**见证服务器实例**</span><span class="sxs-lookup"><span data-stu-id="bebc4-110">**Witness server instance**</span></span>  
 <span data-ttu-id="bebc4-111">如果已指定见证服务器实例（在\*\*\*\*“数据库属性”对话框的\*\*\*\*“镜像”页中），则将显示该实例（有关详细信息，请参阅[数据库属性（“镜像”页）](../../relational-databases/databases/database-properties-mirroring-page.md)）。</span><span class="sxs-lookup"><span data-stu-id="bebc4-111">If a witness server instance is already specified (on the **Mirroring** page of the **Database Properties** dialog box), that instance is displayed (for more information, see [Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)).</span></span>  
  
 <span data-ttu-id="bebc4-112">否则，此列表框显示当前服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="bebc4-112">Otherwise, this list box displays the name of the current server.</span></span> <span data-ttu-id="bebc4-113">请注意，见证服务器实例不能与主体或镜像服务器实例相同。</span><span class="sxs-lookup"><span data-stu-id="bebc4-113">Be aware that the witness server instance cannot be the same as the principal or mirror server instances.</span></span>  
  
 <span data-ttu-id="bebc4-114">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="bebc4-114">**Connect**</span></span>  
 <span data-ttu-id="bebc4-115">如果尚未指定见证服务器实例，请单击\*\*\*\*“连接”。</span><span class="sxs-lookup"><span data-stu-id="bebc4-115">If a witness server instance has not been specified, click **Connect**.</span></span> <span data-ttu-id="bebc4-116">这将显示 **“连接到服务器”** 对话框，在其中可以指定服务器实例并建立连接。</span><span class="sxs-lookup"><span data-stu-id="bebc4-116">This displays the **Connect to Server** dialog box in which you can specify the server instance and establish a connection.</span></span>  
  
 <span data-ttu-id="bebc4-117">如果已经指定实例，但向导缺少一个具有足够权限检查端点存在性的连接，请单击 **“连接”**。</span><span class="sxs-lookup"><span data-stu-id="bebc4-117">If the instance has been specified, but the wizard lacks a connection with sufficient permission to check for the existence of the endpoint, click **Connect**.</span></span> <span data-ttu-id="bebc4-118">这将显示“连接到服务器”\*\*\*\* 对话框，其中列出了你预先选择的服务器实例，而且此时你已无法更换该实例。</span><span class="sxs-lookup"><span data-stu-id="bebc4-118">This displays the **Connect to Server** dialog box with the server instance pre-selected and unchangeable.</span></span> <span data-ttu-id="bebc4-119">指定具有足够权限的域帐户，并连接到服务器实例。</span><span class="sxs-lookup"><span data-stu-id="bebc4-119">Specify a domain account with sufficient permission, and connect to the server instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bebc4-120">与服务器实例建立连接时，配置数据库镜像安全向导将使用 **“连接到服务器”** 对话框中提供的凭据。</span><span class="sxs-lookup"><span data-stu-id="bebc4-120">When connecting to the server instance, the Configure Database Mirroring Security Wizard uses the credentials provided in the **Connect to Server** dialog box.</span></span> <span data-ttu-id="bebc4-121">这些凭据与镜像会话的凭据不同，镜像会话使用启动帐户（其中服务器实例作为服务运行）的凭据。</span><span class="sxs-lookup"><span data-stu-id="bebc4-121">These are different from the credentials of a mirroring session, which uses the credentials of the startup account where the server instance is running as a service.</span></span>  
  
 <span data-ttu-id="bebc4-122">**侦听程序端口**</span><span class="sxs-lookup"><span data-stu-id="bebc4-122">**Listener Port**</span></span>  
 <span data-ttu-id="bebc4-123">此选项的行为取决于此服务器实例是否存在镜像端点，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bebc4-123">The behavior of this option depends on whether the mirroring endpoint exists for this server instance, as follows:</span></span>  
  
-   <span data-ttu-id="bebc4-124">如果该服务器实例不存在侦听器端口，则端口号 5022 将显示在 **“端口”** 文本框中。</span><span class="sxs-lookup"><span data-stu-id="bebc4-124">If the listener port does not exist for the server instance, port number 5022 is displayed in the **Port** text box.</span></span> <span data-ttu-id="bebc4-125">可以输入任何可用的端口号，例如 7022。</span><span class="sxs-lookup"><span data-stu-id="bebc4-125">You can enter any available port number, such as, 7022.</span></span>  
  
-   <span data-ttu-id="bebc4-126">如果镜像端点已经存在，则会显示该端点的端口号。</span><span class="sxs-lookup"><span data-stu-id="bebc4-126">When the mirroring endpoint already exists, the port number from the endpoint is displayed.</span></span> <span data-ttu-id="bebc4-127">如果需要更改该端口，请使用 ALTER ENDPOINT 语句。</span><span class="sxs-lookup"><span data-stu-id="bebc4-127">If you need to change that port, use an ALTER ENDPOINT statement.</span></span> <span data-ttu-id="bebc4-128">有关详细信息，请参阅 [ALTER ENDPOINT (Transact-SQL)](/sql/t-sql/statements/alter-endpoint-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bebc4-128">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bebc4-129">端口号是必需的。</span><span class="sxs-lookup"><span data-stu-id="bebc4-129">A port number is required.</span></span>  
  
 <span data-ttu-id="bebc4-130">**终结点名称**</span><span class="sxs-lookup"><span data-stu-id="bebc4-130">**Endpoint name**</span></span>  
 <span data-ttu-id="bebc4-131">如果此服务器实例存在镜像端点，则端点名称将显示在此处。</span><span class="sxs-lookup"><span data-stu-id="bebc4-131">If the mirroring endpoint exists for this server instance, the endpoint name is displayed here.</span></span> <span data-ttu-id="bebc4-132">如果端点不存在，则可以指定端点的名称。</span><span class="sxs-lookup"><span data-stu-id="bebc4-132">If the endpoint does not exist, you can specify the name of the endpoint.</span></span>  
  
 <span data-ttu-id="bebc4-133">**加密通过此端点发送的数据**</span><span class="sxs-lookup"><span data-stu-id="bebc4-133">**Encrypt data sent through this endpoint**</span></span>  
 <span data-ttu-id="bebc4-134">默认情况下，将启用加密。</span><span class="sxs-lookup"><span data-stu-id="bebc4-134">By default, encryption is enabled.</span></span> <span data-ttu-id="bebc4-135">如果启用，则要求（而不仅仅是支持）进行加密，并且所有加密选项都将使用默认值。</span><span class="sxs-lookup"><span data-stu-id="bebc4-135">When enabled, encryption is required (not merely supported) and uses the default values for all of the encryption options.</span></span> <span data-ttu-id="bebc4-136">有关详细信息，请参阅 [CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql)的信息。</span><span class="sxs-lookup"><span data-stu-id="bebc4-136">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
 <span data-ttu-id="bebc4-137">若要禁用加密，请清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="bebc4-137">To disable encryption, clear the check box.</span></span> <span data-ttu-id="bebc4-138">若要重新启用加密，请选中此复选框。</span><span class="sxs-lookup"><span data-stu-id="bebc4-138">To re-enable encryption, select the check box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bebc4-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bebc4-139">See Also</span></span>  
 <span data-ttu-id="bebc4-140">[数据库镜像终结点 (SQL Server)](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bebc4-140">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="bebc4-141">[数据库属性（“镜像”页）](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="bebc4-141">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="bebc4-142">[为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="bebc4-142">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="bebc4-143">[启动数据库镜像监视器 (SQL Server Management Studio)](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="bebc4-143">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="bebc4-144">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bebc4-144">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="bebc4-145">数据库镜像见证服务器</span><span class="sxs-lookup"><span data-stu-id="bebc4-145">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
