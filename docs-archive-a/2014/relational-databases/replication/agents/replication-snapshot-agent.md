---
title: 复制快照代理 | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, executables
- agents [SQL Server replication], Snapshot Agent
- command prompt [SQL Server replication]
- Snapshot Agent, parameter reference
ms.assetid: 2028ba45-4436-47ed-bf79-7c957766ea04
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a26aca7b33a7355500350572ea5e8ed21bddeacb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578144"
---
# <a name="replication-snapshot-agent"></a><span data-ttu-id="e6ab1-102">复制快照代理</span><span class="sxs-lookup"><span data-stu-id="e6ab1-102">Replication Snapshot Agent</span></span>
  <span data-ttu-id="e6ab1-103">复制快照代理是一个可执行文件，用于准备快照文件（其中包含已发布表和数据库对象的架构及数据），然后将这些文件存储在快照文件夹中，并在分发数据库中记录同步作业。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-103">The Replication Snapshot Agent is an executable file that prepares snapshot files containing schema and data of published tables and database objects, stores the files in the snapshot folder, and records synchronization jobs in the distribution database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6ab1-104">可以按任意顺序指定参数。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-104">Parameters can be specified in any order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6ab1-105">语法</span><span class="sxs-lookup"><span data-stu-id="e6ab1-105">Syntax</span></span>  
  
```  
  
      snapshot [ -?]   
-Publisherserver_name[\instance_name]   
-Publication publication_name   
[-70Subscribers]   
[-BcpBatchSizebcp_batch_size]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributorserver_name[\instance_name]]  
[-DistributorDeadlockPriority [-1|0|1] ]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1] ]  
[-DynamicFilterHostNamedynamic_filter_host_name]  
[-DynamicFilterLogindynamic_filter_login]  
[-DynamicSnapshotLocationdynamic_snapshot_location]   
[-EncryptionLevel [0|1|2]]  
[-FieldDelimiterfield_delimiter]  
[-HistoryVerboseLevel [0|1|2|3] ]  
[-HRBcpBlocksnumber_of_blocks ]  
[-HRBcpBlockSizeblock_size ]  
[-HRBcpDynamicBlocks ]  
[-KeepAliveMessageIntervalkeep_alive_interval]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MaxBcpThreadsnumber_of_threads ]  
[-MaxNetworkOptimization [0|1]]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2] ]  
[-PacketSizepacket_size]
[-PrefetchTables [0|1] ]  
[-ProfileNameprofile_name]  
[-PublisherDBpublisher_database]  
[-PublisherDeadlockPriority [-1|0|1] ]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherLoginpublisher_login]  
[-PublisherPasswordpublisher_password]   
[-PublisherSecurityMode [0|1] ]  
[-QueryTimeOutquery_time_out_seconds]  
[-ReplicationType [1|2] ]  
[-RowDelimiterrow_delimiter]  
[-StartQueueTimeoutstart_queue_timeout_seconds]  
[-UsePerArticleContentsViewuse_per_article_contents_view]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e6ab1-106">参数</span><span class="sxs-lookup"><span data-stu-id="e6ab1-106">Arguments</span></span>  
 <span data-ttu-id="e6ab1-107">**-?**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-107">**-?**</span></span>  
 <span data-ttu-id="e6ab1-108">输出所有可用的参数。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-108">Prints all available parameters.</span></span>  
  
 <span data-ttu-id="e6ab1-109">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="e6ab1-109">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="e6ab1-110">发布服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-110">Is the name of the Publisher.</span></span> <span data-ttu-id="e6ab1-111">为该服务器上的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认实例指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-111">Specify server_name for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="e6ab1-112">为该服务器上的 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认实例指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-112">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="e6ab1-113">**-Publication** _publication_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-113">**-Publication** _publication_</span></span>  
 <span data-ttu-id="e6ab1-114">发布的名称。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-114">Is the name of the publication.</span></span> <span data-ttu-id="e6ab1-115">只有将发布设置为总是使快照可用于新订阅或重新初始化的订阅时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-115">This parameter is only valid if the publication is set to always have a snapshot available for new or reinitialized subscriptions.</span></span>  
  
 <span data-ttu-id="e6ab1-116">**-70Subscribers**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-116">**-70Subscribers**</span></span>  
 <span data-ttu-id="e6ab1-117">如果有任何订阅服务器在运行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 版，则必须使用此参数。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-117">Must be used if any Subscribers are running [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] version 7.0.</span></span>  
  
 <span data-ttu-id="e6ab1-118">**-BcpBatchSize** _bcp_\_ *batch*\_ *size*</span><span class="sxs-lookup"><span data-stu-id="e6ab1-118">**-BcpBatchSize** _bcp_\_ *batch*\_ *size*</span></span>  
 <span data-ttu-id="e6ab1-119">在一次大容量复制操作中发送的行数。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-119">Is the number of rows to send in a bulk copy operation.</span></span> <span data-ttu-id="e6ab1-120"> 执行 **bcp in** 操作时，批的大小为要作为一个事务发送到服务器的行数，并且也是分发代理记录 bcp 进度消息之前必须发送的行数。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-120">When performing a **bcp in** operation, the batch size is the number of rows to send to the server as one transaction, and also the number of rows that must be sent before the Distribution Agent logs a **bcp** progress message.</span></span> <span data-ttu-id="e6ab1-121">当执行 **bcp out** 操作时，将使用固定批大小 1000。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-121">When performing a **bcp out** operation, a fixed batch size of 1000 is used.</span></span> <span data-ttu-id="e6ab1-122">值为 0 表示不记录任何消息。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-122">A value of 0 indicates no message logging.</span></span>  
  
 <span data-ttu-id="e6ab1-123">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-123">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="e6ab1-124">代理定义文件的路径。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-124">Is the path of the agent definition file.</span></span> <span data-ttu-id="e6ab1-125">代理定义文件中包含该代理的命令行参数。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-125">An agent definition file contains command line arguments for the agent.</span></span> <span data-ttu-id="e6ab1-126">文件的内容被当作可执行文件进行分析。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-126">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="e6ab1-127">使用双引号 (") 指定包含任意字符的参数值。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-127">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="e6ab1-128">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="e6ab1-128">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="e6ab1-129">分发服务器名称。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-129">Is the Distributor name.</span></span> <span data-ttu-id="e6ab1-130">为该服务器上的 *默认实例指定* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-130">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="e6ab1-131">为该服务器上的 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认实例指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-131">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="e6ab1-132">**-DistributorDeadlockPriority** [ **-1**|**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="e6ab1-132">**-DistributorDeadlockPriority** [**-1**|**0**|**1**]</span></span>  
 <span data-ttu-id="e6ab1-133">死锁发生时快照代理连接到分发服务器的优先级。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-133">Is the priority of the Snapshot Agent connection to the Distributor when a deadlock occurs.</span></span> <span data-ttu-id="e6ab1-134">指定此参数是为了解决快照生成期间在快照代理和用户应用程序之间发生的死锁问题。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-134">This parameter is specified to resolve deadlocks that may occur between the Snapshot Agent and user applications during snapshot generation.</span></span>  
  
|<span data-ttu-id="e6ab1-135">DistributorDeadlockPriority 值</span><span class="sxs-lookup"><span data-stu-id="e6ab1-135">DistributorDeadlockPriority value</span></span>|<span data-ttu-id="e6ab1-136">说明</span><span class="sxs-lookup"><span data-stu-id="e6ab1-136">Description</span></span>|  
|---------------------------------------|-----------------|  
|<span data-ttu-id="e6ab1-137">**-1**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-137">**-1**</span></span>|<span data-ttu-id="e6ab1-138">在分发服务器上发生死锁时，应用程序而非快照代理优先。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-138">Applications other than the Snapshot Agent have priority when a deadlock occurs at the Distributor.</span></span>|  
|<span data-ttu-id="e6ab1-139">**0** （默认值）</span><span class="sxs-lookup"><span data-stu-id="e6ab1-139">**0** (Default)</span></span>|<span data-ttu-id="e6ab1-140">未分配优先级。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-140">Priority is not assigned.</span></span>|  
|<span data-ttu-id="e6ab1-141">**1**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-141">**1**</span></span>|<span data-ttu-id="e6ab1-142">在分发服务器上发生死锁时，快照代理优先。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-142">Snapshot Agent has priority when a deadlock occurs at the Distributor.</span></span>|  
  
 <span data-ttu-id="e6ab1-143">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-143">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="e6ab1-144">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证连接到分发服务器时所用的登录名。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-144">Is the login used when connecting to the Distributor using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="e6ab1-145">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-145">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="e6ab1-146">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证连接到分发服务器时使用的密码。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-146">Is the password used when connecting to the Distributor using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="e6ab1-147">.</span><span class="sxs-lookup"><span data-stu-id="e6ab1-147">.</span></span>  
  
 <span data-ttu-id="e6ab1-148">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="e6ab1-148">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="e6ab1-149">指定分发服务器的安全模式。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-149">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="e6ab1-150">值 **0** 指示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证模式（默认设置），值 **1** 指示 Windows 身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-150">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="e6ab1-151">**-DynamicFilterHostName** _dynamic_filter_host_name_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-151">**-DynamicFilterHostName** _dynamic_filter_host_name_</span></span>  
 <span data-ttu-id="e6ab1-152">在创建动态快照时，用来为筛选中的 [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) 设置值。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-152">Is used to set a value for [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) in filtering when a dynamic snapshot is created.</span></span> <span data-ttu-id="e6ab1-153">例如，如果为项目指定了子集筛选器子句 `rep_id = HOST_NAME()` ，并且在调用合并代理之前将 **DynamicFilterHostName** 属性设置为“FBJones”，则只会复制 **rep_id** 列中具有“FBJones”的行。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-153">For example, if the subset filter clause `rep_id = HOST_NAME()` is specified for an article, and you set the **DynamicFilterHostName** property to "FBJones" before calling the Merge Agent, only rows having "FBJones" in the **rep_id** column will be replicated.</span></span>  
  
 <span data-ttu-id="e6ab1-154">**-DynamicFilterLogin** _dynamic_filter_login_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-154">**-DynamicFilterLogin** _dynamic_filter_login_</span></span>  
 <span data-ttu-id="e6ab1-155">在创建动态快照时，用来为筛选中的 [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) 设置值。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-155">Is used to set a value for [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql)in filtering when a dynamic snapshot is created.</span></span> <span data-ttu-id="e6ab1-156">例如，如果为项目指定了子集筛选器子句 `user_id = SUSER_SNAME()` ，并且在调用 **SQLSnapshot** 对象的 **Run** 方法之前将 **DynamicFilterLogin** 属性设置为“rsmith”，则只将 **user_id** 列中具有“rsmith”的行包括在快照中。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-156">For example, if the subset filter clause `user_id = SUSER_SNAME()` is specified for an article, and you set the **DynamicFilterLogin** property to "rsmith" before calling the **Run** method of the **SQLSnapshot** object, only rows having "rsmith" in the **user_id** column will be included in the snapshot.</span></span>  
  
 <span data-ttu-id="e6ab1-157">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-157">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span></span>  
 <span data-ttu-id="e6ab1-158">应生成动态快照的位置。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-158">Is the location where the dynamic snapshot should be generated.</span></span>  
  
 <span data-ttu-id="e6ab1-159">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="e6ab1-159">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="e6ab1-160">建立连接时快照代理使用的安全套接字层 (SSL) 加密的等级。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-160">Is the level of Secure Sockets Layer (SSL) encryption used by the Snapshot Agent when making connections.</span></span>  
  
|<span data-ttu-id="e6ab1-161">EncryptionLevel 值</span><span class="sxs-lookup"><span data-stu-id="e6ab1-161">EncryptionLevel value</span></span>|<span data-ttu-id="e6ab1-162">说明</span><span class="sxs-lookup"><span data-stu-id="e6ab1-162">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="e6ab1-163">**0**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-163">**0**</span></span>|<span data-ttu-id="e6ab1-164">指定不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-164">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="e6ab1-165">**1**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-165">**1**</span></span>|<span data-ttu-id="e6ab1-166">指定使用 SSL，但是代理不验证 SSL 服务器证书是否已由可信的颁发者进行签名。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-166">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="e6ab1-167">**2**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-167">**2**</span></span>|<span data-ttu-id="e6ab1-168">指定使用 SSL，并验证证书。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-168">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="e6ab1-169">使用 SQL Server 的完全限定的域名定义有效的 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-169">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="e6ab1-170">为了在将 -EncryptionLevel 设置为 2 时成功连接代理，请在本地 SQL Server 上创建别名。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-170">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="e6ab1-171">“Alias Name”参数应为服务器名称，”Server”参数应设置为 SQL Server 的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-171">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
  
 <span data-ttu-id="e6ab1-172">有关详细信息，请参阅[SQL Server 复制安全性](../security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-172">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="e6ab1-173">**-FieldDelimiter** _field_delimiter_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-173">**-FieldDelimiter** _field_delimiter_</span></span>  
 <span data-ttu-id="e6ab1-174">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 大容量复制数据文件中用于标记字段末尾的字符或字符序列。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-174">Is the character or character sequence that marks the end of a field in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bulk-copy data file.</span></span> <span data-ttu-id="e6ab1-175">默认值为 \n\<x$3>\n。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-175">The default is \n\<x$3>\n.</span></span>  
  
 <span data-ttu-id="e6ab1-176">**-HistoryVerboseLevel** [ **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="e6ab1-176">**-HistoryVerboseLevel** [ **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="e6ab1-177">指定在快照操作过程中记录的历史记录大小。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-177">Specifies the amount of history logged during a snapshot operation.</span></span> <span data-ttu-id="e6ab1-178">选择 **1**可将历史日志记录对性能的影响减至最小。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-178">You can minimize the effect of history logging on performance by selecting **1**.</span></span>  
  
|<span data-ttu-id="e6ab1-179">HistoryVerboseLevel 值</span><span class="sxs-lookup"><span data-stu-id="e6ab1-179">HistoryVerboseLevel value</span></span>|<span data-ttu-id="e6ab1-180">说明</span><span class="sxs-lookup"><span data-stu-id="e6ab1-180">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="e6ab1-181">**0**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-181">**0**</span></span>|<span data-ttu-id="e6ab1-182">进度消息将写入控制台或输出文件。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-182">Progress messages are written either to the console or to an output file.</span></span> <span data-ttu-id="e6ab1-183">不在分发数据库中记录历史记录。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-183">History records are not logged in the distribution database.</span></span>|  
|<span data-ttu-id="e6ab1-184">**1**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-184">**1**</span></span>|<span data-ttu-id="e6ab1-185">总是更新具有相同状态（启动、进行中、成功等）的上一历史记录消息。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-185">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="e6ab1-186">如果不存在状态相同的上一记录，将插入新记录。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-186">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="e6ab1-187">**2** （默认值）</span><span class="sxs-lookup"><span data-stu-id="e6ab1-187">**2** (default)</span></span>|<span data-ttu-id="e6ab1-188">除非记录为空闲消息或长时间运行的作业消息等信息（此时将更新上一记录），否则插入新的历史记录。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-188">Insert new history records unless the record is for such things as idle messages or long-running job messages, in which case update the previous records.</span></span>|  
|<span data-ttu-id="e6ab1-189">**3**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-189">**3**</span></span>|<span data-ttu-id="e6ab1-190">始终插入新记录，除非它与空闲消息有关。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-190">Always insert new records, unless it is for idle messages.</span></span>|  
  
 <span data-ttu-id="e6ab1-191">**-HRBcpBlocks** _number_of_blocks_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-191">**-HRBcpBlocks** _number_of_blocks_</span></span>  
 <span data-ttu-id="e6ab1-192">在编写器线程和读取器线程之间排队的 **bcp** 数据块的数量。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-192">Is the number of **bcp** data blocks that are queued between the writer and reader threads.</span></span> <span data-ttu-id="e6ab1-193">默认值为 50。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-193">The default value is 50.</span></span> <span data-ttu-id="e6ab1-194">**HRBcpBlocks** 仅用于 Oracle 发布。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-194">**HRBcpBlocks** is only used with Oracle publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6ab1-195">此参数用于通过 Oracle 发布服务器优化 **bcp** 的性能。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-195">This parameter is used for performance tuning of **bcp** performance from an Oracle Publisher.</span></span>  
  
 <span data-ttu-id="e6ab1-196">-**HRBcpBlockSize**_block_size_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-196">-**HRBcpBlockSize**_block_size_</span></span>  
 <span data-ttu-id="e6ab1-197">每个 **bcp** 数据块的大小（以 KB 为单位）。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-197">Is the size, in kilobytes (KB), of each **bcp** data block.</span></span> <span data-ttu-id="e6ab1-198">默认值为 64 KB。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-198">The default value is 64 KB.</span></span> <span data-ttu-id="e6ab1-199">**HRBcpBlocks** 仅用于 Oracle 发布。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-199">**HRBcpBlocks** is only used with Oracle publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6ab1-200">此参数用于通过 Oracle 发布服务器优化 **bcp** 的性能。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-200">This parameter is used for performance tuning of **bcp** performance from an Oracle Publisher.</span></span>  
  
 <span data-ttu-id="e6ab1-201">**-HRBcpDynamicBlocks**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-201">**-HRBcpDynamicBlocks**</span></span>  
 <span data-ttu-id="e6ab1-202">每个 **bcp** 数据块的大小是否可以动态增长。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-202">Is whether or not the size of each **bcp** data block can grow dynamically.</span></span> <span data-ttu-id="e6ab1-203">**HRBcpBlocks** 仅用于 Oracle 发布。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-203">**HRBcpBlocks** is only used with Oracle publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6ab1-204">此参数用于通过 Oracle 发布服务器优化 **bcp** 的性能。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-204">This parameter is used for performance tuning of **bcp** performance from an Oracle Publisher.</span></span>  
  
 <span data-ttu-id="e6ab1-205">**-KeepAliveMessageInterval** _keep_alive_interval_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-205">**-KeepAliveMessageInterval** _keep_alive_interval_</span></span>  
 <span data-ttu-id="e6ab1-206">快照代理在向 [MSsnapshot_history](/sql/relational-databases/system-tables/mssnapshot-history-transact-sql) 表中记录“waiting for backend message”之前等待的时间（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-206">Is the amount of time, in seconds, that the Snapshot Agent waits before logging "waiting for backend message" to the [MSsnapshot_history](/sql/relational-databases/system-tables/mssnapshot-history-transact-sql) table.</span></span> <span data-ttu-id="e6ab1-207">默认值为 300 秒。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-207">The default value is 300 seconds.</span></span>  
  
 <span data-ttu-id="e6ab1-208">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-208">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="e6ab1-209">登录超时前等待的秒数。 默认值为 15 秒。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-209">Is the number of seconds before the login times out. The default is **15** seconds.</span></span>  
  
 <span data-ttu-id="e6ab1-210">**-MaxBcpThreads** _number_of_threads_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-210">**-MaxBcpThreads** _number_of_threads_</span></span>  
 <span data-ttu-id="e6ab1-211">指定可以并行执行的大容量复制操作的数量。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-211">Specifies the number of bulk copy operations that can be performed in parallel.</span></span> <span data-ttu-id="e6ab1-212">同时存在的线程和 ODBC 连接的最大数量为 **MaxBcpThreads** 或显示在分发数据库中同步事务中的大容量复制请求数中较小的那一个。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-212">The maximum number of threads and ODBC connections that exist simultaneously is the lesser of **MaxBcpThreads** or the number of bulk copy requests that appear in the synchronization transaction in the distribution database.</span></span> <span data-ttu-id="e6ab1-213">**MaxBcpThreads** 的值必须大于 **0** ，并且不存在任何硬编码的上限。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-213">**MaxBcpThreads** must have a value greater than **0** and has no hard-coded upper limit.</span></span> <span data-ttu-id="e6ab1-214">默认值为 **1**。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-214">The default is **1**.</span></span>  
  
 <span data-ttu-id="e6ab1-215">\- **MaxNetworkOptimization** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="e6ab1-215">\- **MaxNetworkOptimization** [ **0**| **1**]</span></span>  
 <span data-ttu-id="e6ab1-216">是否将无关删除操作发送到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-216">Is if irrelevant deletes are sent to the Subscriber.</span></span> <span data-ttu-id="e6ab1-217">无关删除操作是针对不属于订阅服务器分区的行发送到订阅服务器的 DELETE 命令。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-217">Irrelevant deletes are DELETE commands that are sent to Subscribers for rows that do not belong to the Subscriber's partition.</span></span> <span data-ttu-id="e6ab1-218">无关删除操作不会影响数据的完整性或收敛，但它们会导致不必要的网络通信。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-218">Irrelevant deletes do not affect data integrity or convergence, but they can result in unnecessary network traffic.</span></span> <span data-ttu-id="e6ab1-219">**MaxNetworkOptimization** 的默认值是 **0**。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-219">The default value of **MaxNetworkOptimization** is **0**.</span></span> <span data-ttu-id="e6ab1-220">将 **MaxNetworkOptimization** 设置为 **1** 可将不相关的删除操作发生的机会减至最小，从而减少网络通信，并最大程度地优化网络。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-220">Setting **MaxNetworkOptimization** to **1** minimizing the chances of irrelevant deletes thereby reducing network traffic and maximizing network optimization.</span></span> <span data-ttu-id="e6ab1-221">如果存在多个级别的联接筛选器和复杂子集筛选器，则将此参数设置为 **1** 还会增加元数据的存储并导致发布服务器性能下降。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-221">Setting this parameter to **1** can also increase the storage of metadata and cause performance to degrade at the Publisher if multiple levels of join filters and complex subset filters are present.</span></span> <span data-ttu-id="e6ab1-222">您应仔细评估您的复制拓扑，仅当无关删除操作导致的网络通信高到无法接受时才应将 **MaxNetworkOptimization** 设置为 **1** 。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-222">You should carefully assess your replication topology and set **MaxNetworkOptimization** to **1** only if network traffic from irrelevant deletes is unacceptably high.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6ab1-223">仅当合并发布的同步优化选项设置为**true**时，才会将此参数设置为**1** ，这 (**@keep_partition_changes** [sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)) 的参数。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-223">Setting this parameter to **1** is useful only when the synchronization optimization option of the merge publication is set to **true** (the **@keep_partition_changes** parameter of [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)).</span></span>  
  
 <span data-ttu-id="e6ab1-224">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-224">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="e6ab1-225">代理输出文件的路径。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-225">Is the path of the agent output file.</span></span> <span data-ttu-id="e6ab1-226">如果未提供文件名，则向控制台发送该输出。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-226">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="e6ab1-227">如果指定的文件名已存在，会将输出追加到该文件。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-227">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="e6ab1-228">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="e6ab1-228">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="e6ab1-229">指定输出是否应提供详细内容。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-229">Specifies whether the output should be verbose.</span></span>  
  
|<span data-ttu-id="e6ab1-230">OutputVerboseLevel 值</span><span class="sxs-lookup"><span data-stu-id="e6ab1-230">OutputVerboseLevel value</span></span>|<span data-ttu-id="e6ab1-231">说明</span><span class="sxs-lookup"><span data-stu-id="e6ab1-231">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="e6ab1-232">**0**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-232">**0**</span></span>|<span data-ttu-id="e6ab1-233">仅输出错误消息。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-233">Only error messages are printed.</span></span>|  
|<span data-ttu-id="e6ab1-234">**1** （默认值）</span><span class="sxs-lookup"><span data-stu-id="e6ab1-234">**1** (default)</span></span>|<span data-ttu-id="e6ab1-235">输出所有进度报告消息（默认值）。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-235">All the progress report messages are printed (default).</span></span>|  
|<span data-ttu-id="e6ab1-236">**2**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-236">**2**</span></span>|<span data-ttu-id="e6ab1-237">输出所有错误消息和进度报告消息，这对于调试很有用。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-237">All error messages and progress report messages are printed, which is useful for debugging.</span></span>|  

 <span data-ttu-id="e6ab1-238">**-PrefetchTables** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="e6ab1-238">**-PrefetchTables** [ **0**| **1**]</span></span>  
 <span data-ttu-id="e6ab1-239">可选参数，指定是否预提取并缓存表对象。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-239">Optional parameter that specifies if the table objects will be prefetched and cached.</span></span>  <span data-ttu-id="e6ab1-240">默认行为是，根据内部计算结果，使用 SMO 组件来预提取特定表属性。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-240">The default behavior is to prefetch certain table properties using SMO component based on an internal calculation.</span></span>  <span data-ttu-id="e6ab1-241">如果 SMO 预提取操作的耗时相当长，你会发现此参数非常有用。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-241">This parameter can be helpful in scenarios where SMO prefetch operation takes considerable longer to run.</span></span> <span data-ttu-id="e6ab1-242">如果你不使用此参数，此决定是在运行时做出，依据为以项目形式添加到发布中的表所占的百分比。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-242">If this parameter is not used, this decision is made at runtime based on the percentage of tables that are added as articles to the publication.</span></span>  
  
|<span data-ttu-id="e6ab1-243">OutputVerboseLevel 值</span><span class="sxs-lookup"><span data-stu-id="e6ab1-243">OutputVerboseLevel value</span></span>|<span data-ttu-id="e6ab1-244">说明</span><span class="sxs-lookup"><span data-stu-id="e6ab1-244">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="e6ab1-245">**0**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-245">**0**</span></span>|<span data-ttu-id="e6ab1-246">禁止调用 SMO 组件的预提取方法。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-246">Call to Prefetch method of SMO component is disabled.</span></span>|  
|<span data-ttu-id="e6ab1-247">**1**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-247">**1**</span></span>|<span data-ttu-id="e6ab1-248">快照代理会调用预提取方法，以使用 SMO 缓存一些表属性</span><span class="sxs-lookup"><span data-stu-id="e6ab1-248">Snapshot Agent will call Prefetch method to cache some table properties using SMO</span></span>|  
  
 <span data-ttu-id="e6ab1-249">**-PacketSize** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-249">**-PacketSize** _packet_size_</span></span>  
 <span data-ttu-id="e6ab1-250">快照代理连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]时使用的数据包大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-250">Is the packet size (in bytes) used by the Snapshot Agent when connecting to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e6ab1-251">默认值为 8192 字节。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-251">The default value is 8192 bytes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6ab1-252">除非您确信能够提高性能，否则不要更改数据包的大小。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-252">Do not change the packet size unless you are certain that it will improve performance.</span></span> <span data-ttu-id="e6ab1-253">对于大多数应用程序而言，默认数据包大小为最佳数值。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-253">For most applications, the default packet size is best.</span></span>  
  
 <span data-ttu-id="e6ab1-254">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-254">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="e6ab1-255">指定用于代理参数的代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-255">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="e6ab1-256">如果 **ProfileName** 为 NULL，则将禁用代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-256">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="e6ab1-257">如果未指定 **ProfileName** ，则使用该代理类型的默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-257">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="e6ab1-258">有关信息，请参阅[复制代理配置文件](replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-258">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="e6ab1-259">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-259">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="e6ab1-260">发布数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-260">Is the name of the publication database.</span></span> <span data-ttu-id="e6ab1-261">Oracle 发布服务器不支持该参数。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-261">*This parameter is not supported for Oracle Publishers*.</span></span>  
  
 <span data-ttu-id="e6ab1-262">**-PublisherDeadlockPriority** [ **-1**|**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="e6ab1-262">**-PublisherDeadlockPriority** [**-1**|**0**|**1**]</span></span>  
 <span data-ttu-id="e6ab1-263">死锁发生时快照代理连接到发布服务器的优先级。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-263">Is the priority of the Snapshot Agent connection to the Publisher when a deadlock occurs.</span></span> <span data-ttu-id="e6ab1-264">指定此参数是为了解决快照生成期间在快照代理和用户应用程序之间发生的死锁问题。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-264">This parameter is specified to resolve deadlocks that may occur between the Snapshot Agent and user applications during snapshot generation.</span></span>  
  
|<span data-ttu-id="e6ab1-265">PublisherDeadlockPriority 值</span><span class="sxs-lookup"><span data-stu-id="e6ab1-265">PublisherDeadlockPriority value</span></span>|<span data-ttu-id="e6ab1-266">说明</span><span class="sxs-lookup"><span data-stu-id="e6ab1-266">Description</span></span>|  
|-------------------------------------|-----------------|  
|<span data-ttu-id="e6ab1-267">**-1**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-267">**-1**</span></span>|<span data-ttu-id="e6ab1-268">在发布服务器上发生死锁时，应用程序而非快照代理优先。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-268">Applications other than the Snapshot Agent have priority when a deadlock occurs at the Publisher.</span></span>|  
|<span data-ttu-id="e6ab1-269">**0** （默认值）</span><span class="sxs-lookup"><span data-stu-id="e6ab1-269">**0** (Default)</span></span>|<span data-ttu-id="e6ab1-270">未分配优先级。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-270">Priority is not assigned.</span></span>|  
|<span data-ttu-id="e6ab1-271">**1**</span><span class="sxs-lookup"><span data-stu-id="e6ab1-271">**1**</span></span>|<span data-ttu-id="e6ab1-272">在发布服务器上发生死锁时，快照代理优先。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-272">Snapshot Agent has priority when a deadlock occurs at the Publisher.</span></span>|  
  
 <span data-ttu-id="e6ab1-273">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="e6ab1-273">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="e6ab1-274">指定参加与发布数据库进行的数据库镜像会话的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移伙伴实例。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-274">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="e6ab1-275">有关详细信息，请参阅 [数据库镜像和复制 (SQL Server)](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-275">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="e6ab1-276">**-PublisherLogin** _publisher_login_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-276">**-PublisherLogin** _publisher_login_</span></span>  
 <span data-ttu-id="e6ab1-277">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证连接到发布服务器时所用的登录名。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-277">Is the login used when connecting to the Publisher using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="e6ab1-278">**-PublisherPassword** _publisher_password_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-278">**-PublisherPassword** _publisher_password_</span></span>  
 <span data-ttu-id="e6ab1-279">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证连接到发布服务器时使用的密码。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-279">Is the password used when connecting to the Publisher using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="e6ab1-280">.</span><span class="sxs-lookup"><span data-stu-id="e6ab1-280">.</span></span>  
  
 <span data-ttu-id="e6ab1-281">**-PublisherSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="e6ab1-281">**-PublisherSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="e6ab1-282">指定发布服务器的安全模式。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-282">Specifies the security mode of the Publisher.</span></span> <span data-ttu-id="e6ab1-283">值 **0** 指示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证（默认值），值 **1** 指示 Windows 身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-283">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="e6ab1-284">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-284">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="e6ab1-285">查询超时前等待的秒数。默认值为 1800 秒。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-285">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="e6ab1-286">**-ReplicationType** [ **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="e6ab1-286">**-ReplicationType** [ **1**| **2**]</span></span>  
 <span data-ttu-id="e6ab1-287">指定复制的类型。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-287">Specifies the type of replication.</span></span> <span data-ttu-id="e6ab1-288">值 **1** 指示事务复制，值 **2** 指示合并复制。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-288">A value of **1** indicates transactional replication, and a value of **2** indicates merge replication.</span></span>  
  
 <span data-ttu-id="e6ab1-289">**-RowDelimiter** _row_delimiter_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-289">**-RowDelimiter** _row_delimiter_</span></span>  
 <span data-ttu-id="e6ab1-290">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 大容量复制数据文件中用于标记行尾的字符或字符序列。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-290">Is the character or character sequence that marks the end of a row in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bulk-copy data file.</span></span> <span data-ttu-id="e6ab1-291">默认值为 \n\<,@g>\n。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-291">The default is \n\<,@g>\n.</span></span>  
  
 <span data-ttu-id="e6ab1-292">**-StartQueueTimeout** _start_queue_timeout_seconds_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-292">**-StartQueueTimeout** _start_queue_timeout_seconds_</span></span>  
 <span data-ttu-id="e6ab1-293">当运行的并发动态快照进程数达到 **@max_concurrent_dynamic_snapshots** [&#40;transact-sql&#41;的 sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)属性设置的限制时，快照代理等待的最大秒数。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-293">Is the maximum number of seconds that the Snapshot Agent waits when the number of concurrent dynamic snapshot processes running is at the limit set by the **@max_concurrent_dynamic_snapshots** property of [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="e6ab1-294">如果在经过最大秒数之后快照代理仍在等待，快照代理将退出。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-294">If the maximum number of seconds is reached and the Snapshot Agent is still waiting, it will exit.</span></span> <span data-ttu-id="e6ab1-295">值 0 表示代理将无限期地等待，尽管可以将其取消。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-295">A value of 0 means that the agent waits indefinitely, although it can be canceled.</span></span>  
  
 <span data-ttu-id="e6ab1-296">\- **UsePerArticleContentsView** _use_per_article_contents_view_</span><span class="sxs-lookup"><span data-stu-id="e6ab1-296">\- **UsePerArticleContentsView** _use_per_article_contents_view_</span></span>  
 <span data-ttu-id="e6ab1-297">已不推荐使用此参数，支持它是为了能够向后兼容。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-297">This parameter has been deprecated and is supported for backward-compatibility only.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6ab1-298">备注</span><span class="sxs-lookup"><span data-stu-id="e6ab1-298">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e6ab1-299">如果您安装的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理是通过本地系统帐户而非域用户帐户（默认值）运行，则该服务仅可访问本地计算机。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-299">If you have installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a Local System account rather than under a Domain User account (the default), the service can access only the local computer.</span></span> <span data-ttu-id="e6ab1-300">如果将在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理下运行的快照代理配置为登录 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]时使用 Windows 身份验证模式，则快照代理将失败。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-300">If the Snapshot Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Snapshot Agent fails.</span></span> <span data-ttu-id="e6ab1-301">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认设置为  身份验证。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-301">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="e6ab1-302">若要启动快照代理，请从命令提示符处执行 **snapshot.exe** 。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-302">To start the Snapshot Agent, execute **snapshot.exe** from the command prompt.</span></span> <span data-ttu-id="e6ab1-303">有关信息，请参阅 [复制代理可执行文件](../concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="e6ab1-303">For information, see [Replication Agent Executables](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6ab1-304">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6ab1-304">See Also</span></span>  
 [<span data-ttu-id="e6ab1-305">复制代理管理</span><span class="sxs-lookup"><span data-stu-id="e6ab1-305">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
