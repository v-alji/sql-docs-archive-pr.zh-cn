---
title: MSSQLSERVER_1418 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1418 (Database Engine error)
ms.assetid: 6e9c7241-0201-44e0-9f8b-b3c4e293f0f6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1fcac03f044aacce5e907824862eb589c97a07d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690630"
---
# <a name="mssqlserver_1418"></a><span data-ttu-id="ab3c1-102">MSSQLSERVER_1418</span><span class="sxs-lookup"><span data-stu-id="ab3c1-102">MSSQLSERVER_1418</span></span>
    
## <a name="details"></a><span data-ttu-id="ab3c1-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="ab3c1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ab3c1-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="ab3c1-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="ab3c1-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="ab3c1-105">Event ID</span></span>|<span data-ttu-id="ab3c1-106">1418</span><span class="sxs-lookup"><span data-stu-id="ab3c1-106">1418</span></span>|  
|<span data-ttu-id="ab3c1-107">事件源</span><span class="sxs-lookup"><span data-stu-id="ab3c1-107">Event Source</span></span>|<span data-ttu-id="ab3c1-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ab3c1-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ab3c1-109">组件</span><span class="sxs-lookup"><span data-stu-id="ab3c1-109">Component</span></span>|<span data-ttu-id="ab3c1-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ab3c1-110">SQLEngine</span></span>|  
|<span data-ttu-id="ab3c1-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="ab3c1-111">Symbolic Name</span></span>|<span data-ttu-id="ab3c1-112">DBM_PARTNERNOTFOUND</span><span class="sxs-lookup"><span data-stu-id="ab3c1-112">DBM_PARTNERNOTFOUND</span></span>|  
|<span data-ttu-id="ab3c1-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="ab3c1-113">Message Text</span></span>|<span data-ttu-id="ab3c1-114">服务器网络地址 "%.\*ls" 无法访问或不存在。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-114">The server network address "%.\*ls" can not be reached or does not exist.</span></span> <span data-ttu-id="ab3c1-115">请检查网络地址名称，并检查本地和远程端点的端口是否正常运行。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-115">Check the network address name and that the ports for the local and remote endpoints are operational.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ab3c1-116">说明</span><span class="sxs-lookup"><span data-stu-id="ab3c1-116">Explanation</span></span>  
 <span data-ttu-id="ab3c1-117">该服务器网络端点未做出响应，这是因为无法到达指定的服务器网络地址或该地址不存在。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-117">The server network endpoint did not respond because the specified server network address cannot be reached or does not exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab3c1-118">默认情况下，[!INCLUDE[msCoName](../../includes/msconame-md.md)] 操作系统会阻止所有端口。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-118">By default, [!INCLUDE[msCoName](../../includes/msconame-md.md)] operating system blocks all ports.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ab3c1-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="ab3c1-119">User Action</span></span>  
 <span data-ttu-id="ab3c1-120">验证网络地址名称并重新发出命令。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-120">Verify the network address name and reissue the command.</span></span>  
  
 <span data-ttu-id="ab3c1-121">伙伴双方可能都需要执行更正操作。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-121">Corrective action might be required on both partners.</span></span> <span data-ttu-id="ab3c1-122">例如，如果在主体服务器实例上尝试运行 SET PARTNER 时引发此消息，则此消息可能表示您只需要在镜像服务器实例上执行更正操作。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-122">For example, if this message is raised when you are trying to run SET PARTNER on the principal server instance, the message might imply that you only have to take corrective action on the mirror server instance.</span></span> <span data-ttu-id="ab3c1-123">但是，伙伴双方可能都需要执行更正操作。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-123">However, corrective actions might be required on both partners.</span></span>  
  
### <a name="additional-corrective-actions"></a><span data-ttu-id="ab3c1-124">其他更正操作</span><span class="sxs-lookup"><span data-stu-id="ab3c1-124">Additional Corrective Actions</span></span>  
  
-   <span data-ttu-id="ab3c1-125">确保镜像数据库已为镜像做好准备。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-125">Make sure that the mirror database is ready for mirroring.</span></span>  
  
-   <span data-ttu-id="ab3c1-126">确保镜像服务器实例的名称和端口都正确。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-126">Make sure that the name and port of the mirror server instance are correct.</span></span>  
  
-   <span data-ttu-id="ab3c1-127">确保目标镜像服务器实例不在防火墙之后。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-127">Make sure that the destination mirror server instance is not behind a firewall.</span></span>  
  
-   <span data-ttu-id="ab3c1-128">确保主体服务器实例不在防火墙之后。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-128">Make sure that the principal server instance is not behind a firewall.</span></span>  
  
-   <span data-ttu-id="ab3c1-129">使用 **sys.database_mirroring_endpoints** 目录视图中的 **state** 或 **state_desc** 列验证伙伴上的端点是否都已启动。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-129">Verify that the endpoints are started on the partners by using the **state** or **state_desc** column the of the **sys.database_mirroring_endpoints** catalog view.</span></span> <span data-ttu-id="ab3c1-130">如果未启动任一端点，则执行 ALTER ENDPOINT 语句将其启动。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-130">If either endpoint is not started, execute an ALTER ENDPOINT statement to start it.</span></span>  
  
-   <span data-ttu-id="ab3c1-131">确保主体服务器实例正在侦听分配给其数据库镜像端点的端口，并且镜像服务器实例正在侦听它自己的端口。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-131">Make sure that the principal server instance is listening on the port assigned to its database mirroring endpoint and that and the mirror server instance is listening on its port.</span></span> <span data-ttu-id="ab3c1-132">有关详细信息，请参阅本主题后面的“验证端口可用性”部分。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-132">For more information, see "Verifying Port Availability," later in this topic.</span></span> <span data-ttu-id="ab3c1-133">如果某个伙伴没有侦听为其分配的端口，则请修改数据库镜像端点以侦听其他端口。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-133">If a partner is not listening on its assigned port, modify the database mirroring endpoint to listen on a different port.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ab3c1-134">错误配置的安全性可引发常规设置错误消息。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-134">Improperly configured security can cause a general setup error message.</span></span> <span data-ttu-id="ab3c1-135">通常，服务器实例只删除错误的连接请求而不做出响应。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-135">Typically, the server instance drops the bad connection request without responding.</span></span> <span data-ttu-id="ab3c1-136">对于调用方，安全配置错误可能由于其他许多原因引起，如镜像数据库处于错误状态或不存在、权限不正确等等。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-136">To the caller, a security-configuration error could appear to have occurred for a variety of other reasons, such as the mirror database in a bad state or does not exist, incorrect permissions, and so on.</span></span>  
  
### <a name="using-the-error-log-file-for-diagnosis"></a><span data-ttu-id="ab3c1-137">使用错误日志文件进行诊断</span><span class="sxs-lookup"><span data-stu-id="ab3c1-137">Using the Error Log File for Diagnosis</span></span>  
 <span data-ttu-id="ab3c1-138">在某些情况下，错误日志文件只能用于进行调查。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-138">In some cases, only error log files are available for investigation.</span></span> <span data-ttu-id="ab3c1-139">在这些情况下，请确定错误日志是否包含数据库镜像端点 TCP 端口的错误消息 26023。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-139">In these cases, determine whether the error log contains error message 26023 for the TCP port of the database mirroring endpoint.</span></span> <span data-ttu-id="ab3c1-140">此错误严重级别为 16，可能指示数据库镜像端点尚未启动。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-140">This error, which is severity 16, might indicate that the database mirroring endpoint is not started.</span></span> <span data-ttu-id="ab3c1-141">即使 **sys.database_mirroring_endpoints** 显示端点状态为已启动，也会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-141">This message can occur even if **sys.database_mirroring_endpoints** shows the endpoint state as started.</span></span>  
  
 <span data-ttu-id="ab3c1-142">解决遇到的所有问题之后，请在主体服务器上重新运行 ALTER DATABASE *database_name* SET PARTNER 语句。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-142">After resolving any issues that you encounter, rerun the ALTER DATABASE *database_name* SET PARTNER statement on the principal server.</span></span>  
  
### <a name="verifying-port-availability"></a><span data-ttu-id="ab3c1-143">验证端口可用性</span><span class="sxs-lookup"><span data-stu-id="ab3c1-143">Verifying Port Availability</span></span>  
 <span data-ttu-id="ab3c1-144">为数据库镜像会话配置网络时，请确保每个服务器实例的数据库镜像端点只由数据库镜像过程使用。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-144">When you are configuring the network for a database mirroring session, make sure the database mirroring endpoint of each server instance is used by only the database mirroring process.</span></span> <span data-ttu-id="ab3c1-145">如果另一个过程正在侦听分配给数据库镜像端点的端口，则其他服务器实例的数据库镜像过程将无法连接到该端点。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-145">If another process is listening on the port assigned to a database mirroring endpoint, the database mirroring processes of the other server instances cannot connect to the endpoint.</span></span>  
  
 <span data-ttu-id="ab3c1-146">若要显示基于 Windows 的服务器正在侦听的所有端口，请使用 **netstat** 命令提示实用工具。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-146">To display all the ports on which a Windows-based server is listening, use the **netstat** command-prompt utility.</span></span> <span data-ttu-id="ab3c1-147">**netstat** 语法取决于 Windows 操作系统的版本。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-147">The syntax for **netstat** depends on the version of the Windows operating system.</span></span> <span data-ttu-id="ab3c1-148">有关详细信息，请参阅操作系统文档。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-148">For more information, see the operating system documentation.</span></span>  
  
#### <a name="windows-server-2003-service-pack-1-sp1"></a><span data-ttu-id="ab3c1-149">Windows Server 2003 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="ab3c1-149">Windows Server 2003 Service Pack 1 (SP1)</span></span>  
 <span data-ttu-id="ab3c1-150">若要列出侦听端口以及打开这些端口的进程，请在 Windows 命令提示符下输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="ab3c1-150">To list listening ports and the processes that have those ports opened, enter the following command at the Windows command prompt:</span></span>  
  
 <span data-ttu-id="ab3c1-151">**netstat -abn**</span><span class="sxs-lookup"><span data-stu-id="ab3c1-151">**netstat -abn**</span></span>  
  
#### <a name="windows-server-2003-pre-sp1"></a><span data-ttu-id="ab3c1-152">Windows Server 2003（SP1 以前的版本）</span><span class="sxs-lookup"><span data-stu-id="ab3c1-152">Windows Server 2003 (pre-SP1)</span></span>  
 <span data-ttu-id="ab3c1-153">若要标识侦听端口以及打开这些端口的进程，请按照以下步骤进行：</span><span class="sxs-lookup"><span data-stu-id="ab3c1-153">To identify the listening ports and the processes that have those ports opened, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ab3c1-154">获取进程 ID</span><span class="sxs-lookup"><span data-stu-id="ab3c1-154">Obtain the process ID.</span></span>  
  
     <span data-ttu-id="ab3c1-155">若要了解 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的进程 ID，请连接到该实例并使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="ab3c1-155">To learn the process ID of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], connect to that instance and use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    SELECT SERVERPROPERTY('ProcessID')   
    ```  
  
     <span data-ttu-id="ab3c1-156">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“SERVERPROPERTY (Transact-SQL)”。</span><span class="sxs-lookup"><span data-stu-id="ab3c1-156">For more information, see "SERVERPROPERTY (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="ab3c1-157">然后，将进程 ID 与以下 **netstat** 命令的输出进行匹配：</span><span class="sxs-lookup"><span data-stu-id="ab3c1-157">Match the process ID with the output of the following **netstat** command:</span></span>  
  
     <span data-ttu-id="ab3c1-158">**netstat -ano**</span><span class="sxs-lookup"><span data-stu-id="ab3c1-158">**netstat -ano**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab3c1-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab3c1-159">See Also</span></span>  
 <span data-ttu-id="ab3c1-160">[ALTER ENDPOINT (Transact-SQL)](/sql/t-sql/statements/alter-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab3c1-160">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="ab3c1-161">[数据库镜像终结点 (SQL Server)](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ab3c1-161">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="ab3c1-162">[为镜像准备镜像数据库 (SQL Server)](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ab3c1-162">[Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="ab3c1-163">[SERVERPROPERTY (Transact-SQL)](/sql/t-sql/functions/serverproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab3c1-163">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span></span>  
 <span data-ttu-id="ab3c1-164">[指定服务器网络地址（数据库镜像）](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="ab3c1-164">[Specify a Server Network Address &#40;Database Mirroring&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md) </span></span>  
 <span data-ttu-id="ab3c1-165">[sys.database_mirroring_endpoints (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab3c1-165">[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) </span></span>  
 [<span data-ttu-id="ab3c1-166">数据库镜像配置故障排除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab3c1-166">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
