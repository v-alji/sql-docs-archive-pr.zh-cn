---
title: 主题服务器实例（配置数据库镜像安全向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.principalsrvr.f1
ms.assetid: 58af27d7-c5dd-4669-be6b-b472bc2c8ef4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2632b5ffd5355065b4b5c1f905b3b6e5c5b6204d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690124"
---
# <a name="principal-server-instance-configure-database-mirroring-security-wizard"></a><span data-ttu-id="27d31-102">主体服务器实例（配置数据库镜像安全向导）</span><span class="sxs-lookup"><span data-stu-id="27d31-102">Principal Server Instance (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="27d31-103">使用此页可以指定有关主体数据库的服务器实例的信息。</span><span class="sxs-lookup"><span data-stu-id="27d31-103">Use this page to specify information about the server instance of the principal database.</span></span> <span data-ttu-id="27d31-104">主体数据库是开始镜像会话的数据库的副本。</span><span class="sxs-lookup"><span data-stu-id="27d31-104">The principal database is the copy of the database that begins the mirroring session.</span></span> <span data-ttu-id="27d31-105">会话开始后，主体数据库是接受用户更改的数据库副本。</span><span class="sxs-lookup"><span data-stu-id="27d31-105">After the session has begun, the principal database is the copy of the database that accepts user changes.</span></span> <span data-ttu-id="27d31-106">（当发生故障转移时，主体和镜像角色交换；因此，初始的主体数据库可能不再是主体数据库。）</span><span class="sxs-lookup"><span data-stu-id="27d31-106">(When a failover occurs, the principal and mirroring roles are swapped; therefore, the initial principal database might not remain the principal database.)</span></span>  
  
 <span data-ttu-id="27d31-107">**使用 SQL Server Management Studio 配置数据库镜像**</span><span class="sxs-lookup"><span data-stu-id="27d31-107">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="27d31-108">使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="27d31-108">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="27d31-109">启动配置数据库镜像安全向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="27d31-109">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="27d31-110">选项</span><span class="sxs-lookup"><span data-stu-id="27d31-110">Options</span></span>  
 <span data-ttu-id="27d31-111">**主体服务器实例**</span><span class="sxs-lookup"><span data-stu-id="27d31-111">**Principal server instance**</span></span>  
 <span data-ttu-id="27d31-112">因为 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的数据库镜像总是从主体服务器配置，所以当前的服务器实例总是为主体服务器实例。</span><span class="sxs-lookup"><span data-stu-id="27d31-112">Because database mirroring in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is always configured from the principal server, the current server instance is always the principal server instance.</span></span>  
  
 <span data-ttu-id="27d31-113">**侦听程序端口**</span><span class="sxs-lookup"><span data-stu-id="27d31-113">**Listener Port**</span></span>  
 <span data-ttu-id="27d31-114">此选项的行为取决于此服务器实例是否存在镜像端点，如下所示：</span><span class="sxs-lookup"><span data-stu-id="27d31-114">The behavior of this option depends on whether the mirroring endpoint exists for this server instance, as follows:</span></span>  
  
-   <span data-ttu-id="27d31-115">如果此服务器实例不存在侦听器端口，则端口号 5022 将显示在 **“端口”** 文本框中。</span><span class="sxs-lookup"><span data-stu-id="27d31-115">If the listener port does not exist for this server instance, port number 5022 is displayed in the **Port** text box.</span></span> <span data-ttu-id="27d31-116">可以使用任何可用的端口号，例如 7022。</span><span class="sxs-lookup"><span data-stu-id="27d31-116">You can use any available port number, such as, 7022.</span></span>  
  
-   <span data-ttu-id="27d31-117">如果镜像端点已经存在，则会显示该端点的端口号。</span><span class="sxs-lookup"><span data-stu-id="27d31-117">When the mirroring endpoint already exists, the port number from the endpoint is displayed.</span></span> <span data-ttu-id="27d31-118">如果需要更改端口，请使用 ALTER ENDPOINT 命令。</span><span class="sxs-lookup"><span data-stu-id="27d31-118">If you need to change the port, use an ALTER ENDPOINT command.</span></span> <span data-ttu-id="27d31-119">有关详细信息，请参阅 [ALTER ENDPOINT (Transact-SQL)](/sql/t-sql/statements/alter-endpoint-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="27d31-119">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27d31-120">端口号是必需的。</span><span class="sxs-lookup"><span data-stu-id="27d31-120">A port number is required.</span></span>  
  
 <span data-ttu-id="27d31-121">**终结点名称**</span><span class="sxs-lookup"><span data-stu-id="27d31-121">**Endpoint name**</span></span>  
 <span data-ttu-id="27d31-122">如果此服务器实例存在镜像端点，则端点名称将显示在此处。</span><span class="sxs-lookup"><span data-stu-id="27d31-122">If the mirroring endpoint exists for this server instance, the endpoint name is displayed here.</span></span> <span data-ttu-id="27d31-123">如果端点不存在，则可以指定端点的名称。</span><span class="sxs-lookup"><span data-stu-id="27d31-123">If the endpoint does not exist, you can specify the name of the endpoint.</span></span>  
  
 <span data-ttu-id="27d31-124">**加密通过此端点发送的数据**</span><span class="sxs-lookup"><span data-stu-id="27d31-124">**Encrypt data sent through this endpoint**</span></span>  
 <span data-ttu-id="27d31-125">默认情况下，将启用加密。</span><span class="sxs-lookup"><span data-stu-id="27d31-125">By default, encryption is enabled.</span></span> <span data-ttu-id="27d31-126">如果启用，则要求（而不仅仅是支持）进行加密，并且所有加密选项都将使用默认值。</span><span class="sxs-lookup"><span data-stu-id="27d31-126">When enabled, encryption is required (not merely supported) and uses the default values for all of the encryption options.</span></span> <span data-ttu-id="27d31-127">有关详细信息，请参阅 [CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql)的信息。</span><span class="sxs-lookup"><span data-stu-id="27d31-127">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
 <span data-ttu-id="27d31-128">若要禁用加密，请清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="27d31-128">To disable encryption, clear the check box.</span></span> <span data-ttu-id="27d31-129">若要重新启用加密，请选中此复选框。</span><span class="sxs-lookup"><span data-stu-id="27d31-129">To re-enable encryption, select the check box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d31-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27d31-130">See Also</span></span>  
 <span data-ttu-id="27d31-131">[数据库镜像终结点 (SQL Server)](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="27d31-131">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="27d31-132">[数据库属性（“镜像”页）](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="27d31-132">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="27d31-133">[为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="27d31-133">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="27d31-134">[启动数据库镜像监视器 (SQL Server Management Studio)](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="27d31-134">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="27d31-135">数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="27d31-135">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
