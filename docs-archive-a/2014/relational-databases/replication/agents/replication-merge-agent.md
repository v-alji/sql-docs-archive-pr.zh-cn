---
title: 复制合并代理 | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Merge Agent, executables
- Merge Agent, parameter reference
- agents [SQL Server replication], Merge Agent
- command prompt [SQL Server replication]
ms.assetid: fe1e7f60-b0c8-45e9-a5e8-4fedfa73d7ea
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3b3d74dcc6be62ae8a01d911a8404c7bc32fd651
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578149"
---
# <a name="replication-merge-agent"></a><span data-ttu-id="0c81d-102">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="0c81d-102">Replication Merge Agent</span></span>
  <span data-ttu-id="0c81d-103">复制合并代理是一个将数据库表中保存的初始快照应用于订阅服务器的实用工具可执行文件。</span><span class="sxs-lookup"><span data-stu-id="0c81d-103">The Replication Merge Agent is a utility executable that applies the initial snapshot held in the database tables to the Subscribers.</span></span> <span data-ttu-id="0c81d-104">它还合并自初始快照创建后发布服务器上发生的增量数据更改，并根据配置的规则或通过使用创建的自定义冲突解决程序来协调冲突。</span><span class="sxs-lookup"><span data-stu-id="0c81d-104">It also merges incremental data changes that occurred at the Publisher after the initial snapshot was created, and reconciles conflicts either according to the rules you configure or using a custom resolver you create.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0c81d-105">可以按任意顺序指定参数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-105">Parameters can be specified in any order.</span></span> <span data-ttu-id="0c81d-106">如果未指定可选参数，将使用本地计算机上预定义的注册表设置中的值。</span><span class="sxs-lookup"><span data-stu-id="0c81d-106">When optional parameters are not specified, values from predefined registry settings on the local computer are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c81d-107">语法</span><span class="sxs-lookup"><span data-stu-id="0c81d-107">Syntax</span></span>  
  
```  
  
      replmerg [-?]   
-Publisherserver_name[\instance_name]  
-PublisherDBpublisher_database-Publicationpublication-Subscriberserver_name[\instance_name]  
-SubscriberDBsubscriber_database  
[-AltSnapshotFolderalt_snapshot_folder_path]  
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-DestThreadsnumber_of_destination_threads]  
[-Distributorserver_name[\instance_name]]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-DownloadGenerationsPerBatchdownload_generations_per_batch]  
[-DownloadReadChangesPerBatchdownload_read_changes_per_batch]  
[-DownloadWriteChangesPerBatchdownload_write_changes_per_batch]  
[-DynamicSnapshotLocationdynamic_snapshot_location]  
[-EncryptionLevel [0|1|2]]  
[-ExchangeType [1|2|3]]  
[-FastRowCount [0|1]]  
[-FileTransferType [0|1]]  
[-ForceConvergenceLevel [0|1|2 (Publisher|Subscriber|Both)]]  
[-FtpAddressftp_address]  
[-FtpPasswordftp_password]  
[-FtpPortftp_port]  
[-FtpUserNameftp_user_name]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-Hostnamehost_name]  
[-InteractiveResolution [0|1]]  
[-InternetLogininternet_login]  
[-InternetPasswordinternet_password]  
[-InternetProxyLogininternet_proxy_login]  
[-InternetProxyPasswordinternet_proxy_password]  
[-InternetProxyServerinternet_proxy_server]  
[-InternetSecurityMode [0|1]]  
[-InternetTimeoutinternet_timeout]  
[-InternetURL internet_url]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MakeGenerationIntervalmake_generation_interval_seconds]  
[-MaxBcpThreadsnumber_of_threads]  
[-MaxDownloadChangesnumber_of_download_changes]  
[-MaxUploadChangesnumber_of_upload_changes]  
[-MetadataRetentionCleanup [0|1]]  
[-Output]  
[-OutputVerboseLevel [0|1|2]]  
[-ParallelUploadDownload [0|1]]  
[-PacketSizepacket_size]   
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherLoginpublisher_login]  
[-PublisherPassword publisher_password]  
[-PublisherSecurityMode [0|1]]  
[-QueryTimeOutquery_time_out_seconds]  
[-SrcThreadsnumber_of_source_threads]  
[-StartQueueTimeoutstart_queue_timeout_seconds]  
[-SubscriberConflictClean [0|1]]  
[-SubscriberDatabasePathsubscriber_path]  
[-SubscriberDBAddOption [0|1|2|3]]  
[-SubscriberLoginsubscriber_login]  
[-SubscriberPasswordsubscriber_password   
[-SubscriberSecurityMode [0|1]]  
[-SubscriberType [0|1|2|3|4|5|6|7|8|9]]  
[-SubscriptionType [0|1|2]]  
[-SyncToAlternate [0|1]  
[-UploadGenerationsPerBatchupload_generations_per_batch]  
[-UploadReadChangesPerBatchupload_read_changes_per_batch]  
[-UploadWriteChangesPerBatchupload_write_changes_per_batch]  
[-UseInprocLoader]  
[-Validate [0|1|2|3]]  
[-ValidateIntervalvalidate_interval]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0c81d-108">参数</span><span class="sxs-lookup"><span data-stu-id="0c81d-108">Arguments</span></span>  
 <span data-ttu-id="0c81d-109">**-?**</span><span class="sxs-lookup"><span data-stu-id="0c81d-109">**-?**</span></span>  
 <span data-ttu-id="0c81d-110">输出所有可用的参数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-110">Prints all available parameters.</span></span>  
  
 <span data-ttu-id="0c81d-111">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="0c81d-111">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="0c81d-112">发布服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="0c81d-112">Is the name of the Publisher.</span></span> <span data-ttu-id="0c81d-113">为该服务器上的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认实例指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="0c81d-113">Specify *server_name* for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="0c81d-114">为该服务器上的 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认实例指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="0c81d-114">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="0c81d-115">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="0c81d-115">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="0c81d-116">发布服务器数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="0c81d-116">Is the name of the Publisher database.</span></span>  
  
 <span data-ttu-id="0c81d-117">**-Publication** _publication_</span><span class="sxs-lookup"><span data-stu-id="0c81d-117">**-Publication** _publication_</span></span>  
 <span data-ttu-id="0c81d-118">发布的名称。</span><span class="sxs-lookup"><span data-stu-id="0c81d-118">Is the name of the publication.</span></span> <span data-ttu-id="0c81d-119">只有将发布设置为总是使快照可用于新订阅或重新初始化的订阅时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="0c81d-119">This parameter is only valid if the publication is set to always have a snapshot available for new or reinitialized subscriptions.</span></span>  
  
 <span data-ttu-id="0c81d-120">**-Subscriber** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="0c81d-120">**-Subscriber** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="0c81d-121">订阅服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="0c81d-121">Is the name of the Subscriber.</span></span> <span data-ttu-id="0c81d-122">为该服务器上的 *默认实例指定* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0c81d-122">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="0c81d-123">为该服务器上的 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认实例指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="0c81d-123">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="0c81d-124">**-SubscriberDB** _subscriber_database_</span><span class="sxs-lookup"><span data-stu-id="0c81d-124">**-SubscriberDB** _subscriber_database_</span></span>  
 <span data-ttu-id="0c81d-125">订阅服务器数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="0c81d-125">Is the name of the Subscriber database.</span></span>  
  
 <span data-ttu-id="0c81d-126">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span><span class="sxs-lookup"><span data-stu-id="0c81d-126">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span></span>  
 <span data-ttu-id="0c81d-127">包含订阅的初始快照的文件夹路径。</span><span class="sxs-lookup"><span data-stu-id="0c81d-127">Is the path to the folder that contains the initial snapshot for a subscription.</span></span>  
  
 <span data-ttu-id="0c81d-128">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="0c81d-128">**-Continuous**</span></span>  
 <span data-ttu-id="0c81d-129">指定代理是否尝试连续轮询已复制的事务。</span><span class="sxs-lookup"><span data-stu-id="0c81d-129">Specifies whether the agent attempts to poll replicated transactions continually.</span></span> <span data-ttu-id="0c81d-130">如果指定了该参数，即使没有事务挂起，代理也将在轮询间隔期间轮询来自源的已复制事务。</span><span class="sxs-lookup"><span data-stu-id="0c81d-130">If specified, the agent polls replicated transactions from the source at polling intervals, even if there are no transactions pending.</span></span>  
  
 <span data-ttu-id="0c81d-131">**-DestThreads** _number_of_destination_threads_</span><span class="sxs-lookup"><span data-stu-id="0c81d-131">**-DestThreads** _number_of_destination_threads_</span></span>  
 <span data-ttu-id="0c81d-132">指定合并代理用于在目标上应用更改的目标线程数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-132">Specifies the number of destination threads that the Merge Agent uses to apply changes at the destination.</span></span> <span data-ttu-id="0c81d-133">在上载过程中，目标是发布服务器；在下载过程中，目标是订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="0c81d-133">The destination is the Publisher during upload and the Subscriber during download.</span></span> <span data-ttu-id="0c81d-134">默认值为 4。</span><span class="sxs-lookup"><span data-stu-id="0c81d-134">The default is 4.</span></span>  
  
 <span data-ttu-id="0c81d-135">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="0c81d-135">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="0c81d-136">代理定义文件的路径。</span><span class="sxs-lookup"><span data-stu-id="0c81d-136">Is the path of the agent definition file.</span></span> <span data-ttu-id="0c81d-137">代理定义文件中包含代理的命令提示符参数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-137">An agent definition file contains command prompt arguments for the agent.</span></span> <span data-ttu-id="0c81d-138">文件的内容被当作可执行文件进行分析。</span><span class="sxs-lookup"><span data-stu-id="0c81d-138">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="0c81d-139">使用双引号 (") 指定包含任意字符的参数值。</span><span class="sxs-lookup"><span data-stu-id="0c81d-139">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="0c81d-140">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="0c81d-140">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="0c81d-141">分发服务器名称。</span><span class="sxs-lookup"><span data-stu-id="0c81d-141">Is the Distributor name.</span></span> <span data-ttu-id="0c81d-142">为该服务器上的 *默认实例指定* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0c81d-142">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="0c81d-143">为该服务器上的 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认实例指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="0c81d-143">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="0c81d-144">对于分发服务器（推送）分发，名称默认为本地计算机上 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的默认实例的名称。</span><span class="sxs-lookup"><span data-stu-id="0c81d-144">For Distributor (push) distribution, the name defaults to the name of the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="0c81d-145">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="0c81d-145">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="0c81d-146">分发服务器登录名。</span><span class="sxs-lookup"><span data-stu-id="0c81d-146">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="0c81d-147">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="0c81d-147">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="0c81d-148">分发服务器密码。</span><span class="sxs-lookup"><span data-stu-id="0c81d-148">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="0c81d-149">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-149">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="0c81d-150">指定分发服务器的安全模式。</span><span class="sxs-lookup"><span data-stu-id="0c81d-150">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="0c81d-151">值 **0** 指示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证模式（默认设置），值 **1** 指示 Windows 身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="0c81d-151">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="0c81d-152">**-DownloadGenerationsPerBatch** _download_generations_per_batch_</span><span class="sxs-lookup"><span data-stu-id="0c81d-152">**-DownloadGenerationsPerBatch** _download_generations_per_batch_</span></span>  
 <span data-ttu-id="0c81d-153">将更改从发布服务器下载到订阅服务器时要在单个批次中处理的生成数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-153">Is the number of generations to be processed in a single batch while downloading changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="0c81d-154">生成的定义是每个项目中属于一个逻辑组的更改。</span><span class="sxs-lookup"><span data-stu-id="0c81d-154">A generation is defined as a logical group of changes per article.</span></span> <span data-ttu-id="0c81d-155">可靠的通信链接的默认值为 100。</span><span class="sxs-lookup"><span data-stu-id="0c81d-155">The default for a reliable communication link is 100.</span></span> <span data-ttu-id="0c81d-156">不可靠的通信链接的默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="0c81d-156">The default for an unreliable communication link is 10.</span></span>  
  
 <span data-ttu-id="0c81d-157">**-DownloadReadChangesPerBatch** _download_read_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="0c81d-157">**-DownloadReadChangesPerBatch** _download_read_changes_per_batch_</span></span>  
 <span data-ttu-id="0c81d-158">将发布服务器上的更改下载到订阅服务器时要在单个批次中读取的更改数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-158">Is the number of changes to be read in a single batch while downloading changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="0c81d-159">默认值为 100。</span><span class="sxs-lookup"><span data-stu-id="0c81d-159">The default is 100.</span></span>  
  
 <span data-ttu-id="0c81d-160">**-DownloadWriteChangesPerBatch** _download_write_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="0c81d-160">**-DownloadWriteChangesPerBatch** _download_write_changes_per_batch_</span></span>  
 <span data-ttu-id="0c81d-161">将发布服务器上的更改下载到订阅服务器时要在单个批次中应用的更改数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-161">Is the number of changes to be applied in a single batch while downloading changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="0c81d-162">默认值为 100。</span><span class="sxs-lookup"><span data-stu-id="0c81d-162">The default is 100.</span></span>  
  
 <span data-ttu-id="0c81d-163">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span><span class="sxs-lookup"><span data-stu-id="0c81d-163">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span></span>  
 <span data-ttu-id="0c81d-164">当发布使用参数化行筛选器时所筛选数据快照文件的位置。</span><span class="sxs-lookup"><span data-stu-id="0c81d-164">Is the location of the filtered data snapshot files when the publication uses parameterized row filters.</span></span>  
  
 <span data-ttu-id="0c81d-165">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="0c81d-165">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="0c81d-166">建立连接时合并代理使用的安全套接字层 (SSL) 加密的级别。</span><span class="sxs-lookup"><span data-stu-id="0c81d-166">Is the level of Secure Sockets Layer (SSL) encryption used by the Merge Agent when making connections.</span></span>  
  
|<span data-ttu-id="0c81d-167">EncryptionLevel 值</span><span class="sxs-lookup"><span data-stu-id="0c81d-167">EncryptionLevel value</span></span>|<span data-ttu-id="0c81d-168">说明</span><span class="sxs-lookup"><span data-stu-id="0c81d-168">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="0c81d-169">**0**</span><span class="sxs-lookup"><span data-stu-id="0c81d-169">**0**</span></span>|<span data-ttu-id="0c81d-170">指定不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="0c81d-170">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="0c81d-171">**1**</span><span class="sxs-lookup"><span data-stu-id="0c81d-171">**1**</span></span>|<span data-ttu-id="0c81d-172">指定使用 SSL，但是代理不验证 SSL 服务器证书是否已由可信的颁发者进行签名。</span><span class="sxs-lookup"><span data-stu-id="0c81d-172">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="0c81d-173">**2**</span><span class="sxs-lookup"><span data-stu-id="0c81d-173">**2**</span></span>|<span data-ttu-id="0c81d-174">指定使用 SSL，并验证证书。</span><span class="sxs-lookup"><span data-stu-id="0c81d-174">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="0c81d-175">使用 SQL Server 的完全限定的域名定义有效的 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="0c81d-175">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="0c81d-176">为了在将 -EncryptionLevel 设置为 2 时成功连接代理，请在本地 SQL Server 上创建别名。</span><span class="sxs-lookup"><span data-stu-id="0c81d-176">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="0c81d-177">“Alias Name”参数应为服务器名称，”Server”参数应设置为 SQL Server 的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="0c81d-177">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
  
 <span data-ttu-id="0c81d-178">有关详细信息，请参阅[SQL Server 复制安全性](../security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="0c81d-178">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="0c81d-179">**-ExchangeType** [ **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-179">**-ExchangeType** [ **1**| **2**| **3**]</span></span>  
 > [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="0c81d-180">要限制上载，请改用 `@subscriber_upload_options` 的 `sp_addmergearticle`。</span><span class="sxs-lookup"><span data-stu-id="0c81d-180">To restrict uploading, use the `@subscriber_upload_options` of `sp_addmergearticle` instead.</span></span>  
  
 <span data-ttu-id="0c81d-181">指定同步过程中数据交换的类型，可以是下列值之一：</span><span class="sxs-lookup"><span data-stu-id="0c81d-181">Specifies the type of data exchange during synchronization, which can be one of the following:</span></span>  
  
|<span data-ttu-id="0c81d-182">ExchangeType 值</span><span class="sxs-lookup"><span data-stu-id="0c81d-182">ExchangeType value</span></span>|<span data-ttu-id="0c81d-183">说明</span><span class="sxs-lookup"><span data-stu-id="0c81d-183">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="0c81d-184">**1**</span><span class="sxs-lookup"><span data-stu-id="0c81d-184">**1**</span></span>|<span data-ttu-id="0c81d-185">代理应将订阅服务器上的数据更改上载到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="0c81d-185">Agent should upload data changes from the Subscriber to the Publisher.</span></span>|  
|<span data-ttu-id="0c81d-186">**2**</span><span class="sxs-lookup"><span data-stu-id="0c81d-186">**2**</span></span>|<span data-ttu-id="0c81d-187">代理应将发布服务器上的数据更改下载到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="0c81d-187">Agent should download data changes from the Publisher to the Subscriber.</span></span>|  
|<span data-ttu-id="0c81d-188">**3** （默认值）</span><span class="sxs-lookup"><span data-stu-id="0c81d-188">**3** (default)</span></span>|<span data-ttu-id="0c81d-189">代理应首先将订阅服务器上的数据更改上载到发布服务器，然后将发布服务器上的数据更改下载到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="0c81d-189">Agent should first upload data changes from the Subscriber to the Publisher and then download data changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="0c81d-190">您必须将此选项与 Web 同步一起使用。</span><span class="sxs-lookup"><span data-stu-id="0c81d-190">You must use this option with Web synchronization.</span></span>|  
  
 <span data-ttu-id="0c81d-191">仅下载类型的项目使得您可以控制发布中单个项目的同步行为并可提高性能。</span><span class="sxs-lookup"><span data-stu-id="0c81d-191">Download-only articles enable you to control the synchronization behavior of individual articles in a publication, and they can provide a performance benefit.</span></span> <span data-ttu-id="0c81d-192">有关详细信息，请参阅[使用仅下载项目优化合并复制性能](../merge/optimize-merge-replication-performance-with-download-only-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="0c81d-192">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](../merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
 <span data-ttu-id="0c81d-193">若要使用 `ExchangeType` 将合并复制的上载和下载阶段分隔为单独的会话，则必须先在将 `ExchangeType` 设为 1 的情况下运行合并代理，然后将该值设为 2 再运行一次合并代理。</span><span class="sxs-lookup"><span data-stu-id="0c81d-193">If using `ExchangeType` to separate the upload and download phase of merge replication into separate sessions, you must run the merge agent with `ExchangeType` set to 1 first and then run the merge agent again with the value 2.</span></span> <span data-ttu-id="0c81d-194">不以这两个参数运行合并代理将导致系统删除元数据并需要您重新初始化订阅（不上载）。</span><span class="sxs-lookup"><span data-stu-id="0c81d-194">Failure to run the merge agent with both parameters will cause metadata to be deleted and require you to reinitialize the subscription (without upload).</span></span>  
  
 <span data-ttu-id="0c81d-195">**-FastRowCount** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-195">**-FastRowCount** [**0**|**1**]</span></span>  
 <span data-ttu-id="0c81d-196">指定应为行计数验证使用何种行计数计算类型。</span><span class="sxs-lookup"><span data-stu-id="0c81d-196">Specifies what type of rowcount calculation method should be used for rowcount validation.</span></span> <span data-ttu-id="0c81d-197">值 **1** （默认值）表示快速方法。</span><span class="sxs-lookup"><span data-stu-id="0c81d-197">A value of **1** (default) indicates the fast method.</span></span> <span data-ttu-id="0c81d-198">值 **0** 表示完全行计数方法。</span><span class="sxs-lookup"><span data-stu-id="0c81d-198">A value of **0** indicates the full rowcount method.</span></span>  
  
 <span data-ttu-id="0c81d-199">**-FileTransferType** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-199">**-FileTransferType** [**0**|**1**]</span></span>  
 <span data-ttu-id="0c81d-200">指定文件传输类型。</span><span class="sxs-lookup"><span data-stu-id="0c81d-200">Specifies the file transfer type.</span></span> <span data-ttu-id="0c81d-201"> 值为 **0** ，表示 UNC（通用命名约定），值为 1，表示 FTP（文件传输协议）。</span><span class="sxs-lookup"><span data-stu-id="0c81d-201">A value of **0** indicates UNC (universal naming convention), and a value of **1** indicates FTP (file transfer protocol).</span></span>  
  
 <span data-ttu-id="0c81d-202">**-ForceConvergenceLevel** [**0**|**1**|**2** ( **Publisher**| **Subscriber**| **Both**)]</span><span class="sxs-lookup"><span data-stu-id="0c81d-202">**-ForceConvergenceLevel** [**0**|**1**|**2** ( **Publisher**| **Subscriber**| **Both**)]</span></span>  
 <span data-ttu-id="0c81d-203">指定合并代理应使用的收敛级别，可以为以下值之一：</span><span class="sxs-lookup"><span data-stu-id="0c81d-203">Specifies the level of convergence the Merge Agent should use, and can be one of the following:</span></span>  
  
|<span data-ttu-id="0c81d-204">ForceConvergenceLevel 值</span><span class="sxs-lookup"><span data-stu-id="0c81d-204">ForceConvergenceLevel value</span></span>|<span data-ttu-id="0c81d-205">说明</span><span class="sxs-lookup"><span data-stu-id="0c81d-205">Description</span></span>|  
|---------------------------------|-----------------|  
|<span data-ttu-id="0c81d-206">**0** （默认值）</span><span class="sxs-lookup"><span data-stu-id="0c81d-206">**0** (default)</span></span>|<span data-ttu-id="0c81d-207">默认。</span><span class="sxs-lookup"><span data-stu-id="0c81d-207">Default.</span></span> <span data-ttu-id="0c81d-208">执行不具有附加收敛的标准合并。</span><span class="sxs-lookup"><span data-stu-id="0c81d-208">Perform a standard merge without additional convergence.</span></span>|  
|<span data-ttu-id="0c81d-209">**1**</span><span class="sxs-lookup"><span data-stu-id="0c81d-209">**1**</span></span>|<span data-ttu-id="0c81d-210">强制所有生成进行收敛。</span><span class="sxs-lookup"><span data-stu-id="0c81d-210">Force convergence for all generations.</span></span>|  
|<span data-ttu-id="0c81d-211">**2**</span><span class="sxs-lookup"><span data-stu-id="0c81d-211">**2**</span></span>|<span data-ttu-id="0c81d-212">强制所有生成进行收敛并更正损坏的沿袭。</span><span class="sxs-lookup"><span data-stu-id="0c81d-212">Force convergence for all generations and correct corrupt lineages.</span></span> <span data-ttu-id="0c81d-213">当指定此值时，请指定应更正何处的沿袭：发布服务器、订阅服务器，还是发布服务器和订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="0c81d-213">When specifying this value, specify where lineages should be corrected: the Publisher, the Subscriber, or both the Publisher and the Subscriber.</span></span>|  
  
 <span data-ttu-id="0c81d-214">**-FtpAddress** _ftp_address_</span><span class="sxs-lookup"><span data-stu-id="0c81d-214">**-FtpAddress** _ftp_address_</span></span>  
 <span data-ttu-id="0c81d-215">分发服务器的 FTP 服务网络地址。</span><span class="sxs-lookup"><span data-stu-id="0c81d-215">Is the network address of the FTP service for the Distributor.</span></span> <span data-ttu-id="0c81d-216">如果不指定，则使用 **Distributor** 。</span><span class="sxs-lookup"><span data-stu-id="0c81d-216">When not specified, **Distributor** is used.</span></span>  
  
 <span data-ttu-id="0c81d-217">**-FtpPassword** _ftp_password_</span><span class="sxs-lookup"><span data-stu-id="0c81d-217">**-FtpPassword** _ftp_password_</span></span>  
 <span data-ttu-id="0c81d-218">用于连接到 FTP 服务的用户密码。</span><span class="sxs-lookup"><span data-stu-id="0c81d-218">Is the user password used to connect to the FTP service.</span></span>  
  
 <span data-ttu-id="0c81d-219">**-FtpPort** _ftp_port_</span><span class="sxs-lookup"><span data-stu-id="0c81d-219">**-FtpPort** _ftp_port_</span></span>  
 <span data-ttu-id="0c81d-220">分发服务器 FTP 服务的端口号。</span><span class="sxs-lookup"><span data-stu-id="0c81d-220">Is the port number of the FTP service for the Distributor.</span></span> <span data-ttu-id="0c81d-221">如果不指定，则使用 FTP 服务的默认端口号 (21)。</span><span class="sxs-lookup"><span data-stu-id="0c81d-221">When not specified, the default port number for FTP service (21) is used.</span></span>  
  
 <span data-ttu-id="0c81d-222">**-FtpUserName** _ftp_user_name_</span><span class="sxs-lookup"><span data-stu-id="0c81d-222">**-FtpUserName** _ftp_user_name_</span></span>  
 <span data-ttu-id="0c81d-223">用于连接到 FTP 服务的用户名。</span><span class="sxs-lookup"><span data-stu-id="0c81d-223">Is the user name used to connect to the FTP service.</span></span> <span data-ttu-id="0c81d-224">如果不指定，则使用 anonymous。</span><span class="sxs-lookup"><span data-stu-id="0c81d-224">When not specified, anonymous is used.</span></span>  
  
 <span data-ttu-id="0c81d-225">**-HistoryVerboseLevel** [**1**|**2**|**3**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-225">**-HistoryVerboseLevel** [**1**|**2**|**3**]</span></span>  
 <span data-ttu-id="0c81d-226">指定在合并操作期间记录的历史记录数量。</span><span class="sxs-lookup"><span data-stu-id="0c81d-226">Specifies the amount of history logged during a merge operation.</span></span> <span data-ttu-id="0c81d-227">选择 **1**可将历史日志记录对性能的影响减至最小。</span><span class="sxs-lookup"><span data-stu-id="0c81d-227">You can minimize the effect of history logging on performance by selecting **1**.</span></span>  
  
|<span data-ttu-id="0c81d-228">HistoryVerboseLevel 值</span><span class="sxs-lookup"><span data-stu-id="0c81d-228">HistoryVerboseLevel value</span></span>|<span data-ttu-id="0c81d-229">说明</span><span class="sxs-lookup"><span data-stu-id="0c81d-229">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="0c81d-230">**0**</span><span class="sxs-lookup"><span data-stu-id="0c81d-230">**0**</span></span>|<span data-ttu-id="0c81d-231">记录最终的代理状态消息、最终的会话详细信息和任何错误。</span><span class="sxs-lookup"><span data-stu-id="0c81d-231">Log the final agent status message, final session details, and any errors.</span></span>|  
|<span data-ttu-id="0c81d-232">**1**</span><span class="sxs-lookup"><span data-stu-id="0c81d-232">**1**</span></span>|<span data-ttu-id="0c81d-233">记录每个会话状态的增量会话详细信息，包括完成百分比、最终代理状态消息、最终会话详细信息以及任何错误。</span><span class="sxs-lookup"><span data-stu-id="0c81d-233">Log incremental session details at each session status, including percent complete, in addition to the final agent status message, final session details, and any errors.</span></span>|  
|<span data-ttu-id="0c81d-234">**2**</span><span class="sxs-lookup"><span data-stu-id="0c81d-234">**2**</span></span>|<span data-ttu-id="0c81d-235">默认。</span><span class="sxs-lookup"><span data-stu-id="0c81d-235">Default.</span></span> <span data-ttu-id="0c81d-236">记录每个会话状态的增量会话详细信息和项目级别会话详细信息，包括完成百分比、最终代理状态消息、最终会话详细信息以及任何错误。</span><span class="sxs-lookup"><span data-stu-id="0c81d-236">Log both incremental session details at each session status and article level session details, including percent complete, in addition to the final agent status message, final session details, and any errors.</span></span> <span data-ttu-id="0c81d-237">同时还会记录代理状态消息。</span><span class="sxs-lookup"><span data-stu-id="0c81d-237">Agent status messages are also logged.</span></span>|  
|<span data-ttu-id="0c81d-238">**3**</span><span class="sxs-lookup"><span data-stu-id="0c81d-238">**3**</span></span>|<span data-ttu-id="0c81d-239">除了将更多地记录代理进度消息之外，其他与 **-HistoryVerboseLevel** = **2**时相同。</span><span class="sxs-lookup"><span data-stu-id="0c81d-239">The same as **-HistoryVerboseLevel** = **2**, except that more agent progress messages are logged.</span></span>|  
  
 <span data-ttu-id="0c81d-240">**-Hostname** _host_name_</span><span class="sxs-lookup"><span data-stu-id="0c81d-240">**-Hostname** _host_name_</span></span>  
 <span data-ttu-id="0c81d-241">本地计算机的网络名。</span><span class="sxs-lookup"><span data-stu-id="0c81d-241">Is the network name of the local computer.</span></span> <span data-ttu-id="0c81d-242">默认为本地计算机名称。</span><span class="sxs-lookup"><span data-stu-id="0c81d-242">The default is the local computer name.</span></span>  
  
 <span data-ttu-id="0c81d-243">**-InteractiveResolution** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-243">**-InteractiveResolution** [**0**|**1**]</span></span>  
 <span data-ttu-id="0c81d-244">指定在同步期间发生冲突时是否使用交互式冲突解决方法。</span><span class="sxs-lookup"><span data-stu-id="0c81d-244">Specifies whether interactive conflict resolution is used when a conflict occurs during synchronization.</span></span> <span data-ttu-id="0c81d-245">默认值为 **0**，指示不使用交互式冲突解决方法。</span><span class="sxs-lookup"><span data-stu-id="0c81d-245">The default is **0**, indicating that interactive conflict resolution is not used.</span></span>  
  
 <span data-ttu-id="0c81d-246">**-InternetLogin** _internet_login_</span><span class="sxs-lookup"><span data-stu-id="0c81d-246">**-InternetLogin** _internet_login_</span></span>  
 <span data-ttu-id="0c81d-247">指定连接到需要进行身份验证的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制侦听器 ISAPI DLL 时所使用的登录名。</span><span class="sxs-lookup"><span data-stu-id="0c81d-247">Specifies the login name used when connecting to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL that requires authentication.</span></span>  
  
 <span data-ttu-id="0c81d-248">**-InternetPassword** _internet_password_</span><span class="sxs-lookup"><span data-stu-id="0c81d-248">**-InternetPassword** _internet_password_</span></span>  
 <span data-ttu-id="0c81d-249">指定连接到需要进行身份验证的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制侦听器 ISAPI DLL 时所使用的密码。</span><span class="sxs-lookup"><span data-stu-id="0c81d-249">Specifies the password used when connecting to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL that requires authentication.</span></span>  
  
 <span data-ttu-id="0c81d-250">**-InternetProxyLogin**  *internet_proxy_login*</span><span class="sxs-lookup"><span data-stu-id="0c81d-250">**-InternetProxyLogin**  *internet_proxy_login*</span></span>  
 <span data-ttu-id="0c81d-251">指定连接到需要进行身份验证的代理服务器（在 *internet_proxy_server*中定义）时所使用的登录名。</span><span class="sxs-lookup"><span data-stu-id="0c81d-251">Specifies the login name used when connecting to a proxy server, defined in *internet_proxy_server*, that requires authentication.</span></span>  
  
 <span data-ttu-id="0c81d-252">**-InternetProxyPassword**  *internet_proxy_password*</span><span class="sxs-lookup"><span data-stu-id="0c81d-252">**-InternetProxyPassword**  *internet_proxy_password*</span></span>  
 <span data-ttu-id="0c81d-253">指定连接到需要进行身份验证的代理服务器（在 *internet_proxy_server*中定义）时所使用的密码。</span><span class="sxs-lookup"><span data-stu-id="0c81d-253">Specifies the password used when connecting to a proxy server, defined in *internet_proxy_server*, that requires authentication.</span></span>  
  
 <span data-ttu-id="0c81d-254">**-InternetProxyServer**  *internet_proxy_server*</span><span class="sxs-lookup"><span data-stu-id="0c81d-254">**-InternetProxyServer**  *internet_proxy_server*</span></span>  
 <span data-ttu-id="0c81d-255">指定当访问 *internet_url*中指定的 HTTP 资源时要使用的代理服务器。</span><span class="sxs-lookup"><span data-stu-id="0c81d-255">Specifies the proxy server to use when accessing the HTTP resource specified in *internet_url*.</span></span>  
  
 <span data-ttu-id="0c81d-256">**-InternetSecurityMode** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-256">**-InternetSecurityMode** [**0**|**1**]</span></span>  
 <span data-ttu-id="0c81d-257">指定在 Web 同步期间连接到 Web 服务器时所使用的 IIS 安全模式。</span><span class="sxs-lookup"><span data-stu-id="0c81d-257">Specifies the IIS security mode used when connecting to the Web server during Web synchronization.</span></span> <span data-ttu-id="0c81d-258">值为 **0** ，表示为基本身份验证，值为 **1** ，表示为 Windows 集成身份验证（默认）。</span><span class="sxs-lookup"><span data-stu-id="0c81d-258">A value of **0** indicates Basic Authentication, and a value of **1** indicates Windows Integrated Authentication (default).</span></span>  
  
 <span data-ttu-id="0c81d-259">**-InternetTimeout** _internet_timeout_</span><span class="sxs-lookup"><span data-stu-id="0c81d-259">**-InternetTimeout** _internet_timeout_</span></span>  
 <span data-ttu-id="0c81d-260">与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制侦听器 ISAPI DLL 的连接超时之前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-260">Is the number of seconds before a connection to the to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL times out.</span></span>  
  
 <span data-ttu-id="0c81d-261">**-InternetURL** _internet_url_</span><span class="sxs-lookup"><span data-stu-id="0c81d-261">**-InternetURL** _internet_url_</span></span>  
 <span data-ttu-id="0c81d-262">指定用于连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制侦听器 ISAPI DLL 的 URL。</span><span class="sxs-lookup"><span data-stu-id="0c81d-262">Specifies the URL used to connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL.</span></span> <span data-ttu-id="0c81d-263">必须指定此属性。</span><span class="sxs-lookup"><span data-stu-id="0c81d-263">This property must be specified.</span></span>  
  
 <span data-ttu-id="0c81d-264">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="0c81d-264">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span></span>  
 <span data-ttu-id="0c81d-265">在历史记录线程检查目前是否有连接在等待服务器响应之前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-265">Is the number of seconds before the history thread checks if any of the existing connections is waiting for a response from the server.</span></span> <span data-ttu-id="0c81d-266">在执行长时间运行的批处理时，减小该值可避免检查代理将合并代理标记为可疑。</span><span class="sxs-lookup"><span data-stu-id="0c81d-266">This value can be decreased to avoid having the checkup agent mark the Merge Agent as suspect when executing a long-running batch.</span></span> <span data-ttu-id="0c81d-267">默认值为 **300** 秒。</span><span class="sxs-lookup"><span data-stu-id="0c81d-267">The default is **300** seconds.</span></span>  
  
 <span data-ttu-id="0c81d-268">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="0c81d-268">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="0c81d-269">登录超时前等待的秒数。 默认值为 15 秒。</span><span class="sxs-lookup"><span data-stu-id="0c81d-269">Is the number of seconds before the login times out. The default is **15** seconds.</span></span>  
  
 <span data-ttu-id="0c81d-270">**-MakeGenerationInterval** _make_generation_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="0c81d-270">**-MakeGenerationInterval** _make_generation_interval_seconds_</span></span>  
 <span data-ttu-id="0c81d-271">等待创建生成或更改批的秒数或下载到客户端的秒数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-271">Is the number of seconds to wait between creating generations, or batches of changes, to download to the client.</span></span> <span data-ttu-id="0c81d-272">默认值为 **1** 秒。</span><span class="sxs-lookup"><span data-stu-id="0c81d-272">The default is **1** second.</span></span>  
  
 <span data-ttu-id="0c81d-273">Makegeneration 是准备要下载到订阅服务器的发布服务器更改的进程，这可能是下载期间的性能瓶颈。</span><span class="sxs-lookup"><span data-stu-id="0c81d-273">Makegeneration is the process that prepares Publisher changes to be downloaded to Subscribers, and it can be a performance bottleneck during downloads.</span></span> <span data-ttu-id="0c81d-274">如果 makegeneration 进程已按 **-MakeGenerationInterval**指定的间隔运行，则将为当前同步会话跳过该进程。</span><span class="sxs-lookup"><span data-stu-id="0c81d-274">If the makegeneration process already ran within the interval specified by **-MakeGenerationInterval**, the process is skipped for the current synchronization session.</span></span> <span data-ttu-id="0c81d-275">此操作将有助于同步并发，在订阅服务器不希望下载更改时尤为有用。</span><span class="sxs-lookup"><span data-stu-id="0c81d-275">This can benefit synchronization concurrency and is especially helpful if Subscribers do not expect to download changes.</span></span>  
  
 <span data-ttu-id="0c81d-276">**-MaxBcpThreads** _number_of_threads_</span><span class="sxs-lookup"><span data-stu-id="0c81d-276">**-MaxBcpThreads** _number_of_threads_</span></span>  
 <span data-ttu-id="0c81d-277">指定可以并行执行的大容量复制操作的数量。</span><span class="sxs-lookup"><span data-stu-id="0c81d-277">Specifies the number of bulk copy operations that can be performed in parallel.</span></span> <span data-ttu-id="0c81d-278">同时存在的线程和 ODBC 连接的最大数目为 **MaxBcpThreads** 与在发布数据库的系统表 **sysmergeschemachange** 中列出的大容量复制请求数这二者中的较小者。</span><span class="sxs-lookup"><span data-stu-id="0c81d-278">The maximum number of threads and ODBC connections that exist simultaneously is the lesser of **MaxBcpThreads** or the number of bulk copy requests that appear in the system table **sysmergeschemachange** in the publication database.</span></span> <span data-ttu-id="0c81d-279">**MaxBcpThreads** 的值必须大于 0，并且不存在任何硬编码的上限。</span><span class="sxs-lookup"><span data-stu-id="0c81d-279">**MaxBcpThreads** must have a value greater than 0 and has no hard-coded upper limit.</span></span> <span data-ttu-id="0c81d-280">默认值为 **1**。</span><span class="sxs-lookup"><span data-stu-id="0c81d-280">The default is **1**.</span></span>  
  
 <span data-ttu-id="0c81d-281">**-MaxDownloadChanges** _number_of_download_changes_</span><span class="sxs-lookup"><span data-stu-id="0c81d-281">**-MaxDownloadChanges** _number_of_download_changes_</span></span>  
 <span data-ttu-id="0c81d-282">指定应从发布服务器下载到订阅服务器的已更改行的最大数量。</span><span class="sxs-lookup"><span data-stu-id="0c81d-282">Specifies the maximum number of changed rows that should be downloaded from the Publisher to the Subscriber.</span></span> <span data-ttu-id="0c81d-283">下载的行数可能会由于以下原因大于指定的最大值：处理了所有生成或可能运行了并行的目标线程，这两种情况在第一次传递中均会处理至少 100 个更改。</span><span class="sxs-lookup"><span data-stu-id="0c81d-283">The number of rows downloaded may be higher than the specified maximum because: complete generations are processed; and parallel destination threads may run, each of which processes at least 100 changes in its first pass.</span></span> <span data-ttu-id="0c81d-284">默认情况下将发送所有已准备好下载的更改。</span><span class="sxs-lookup"><span data-stu-id="0c81d-284">By default all changes that are ready to be downloaded are sent.</span></span>  
  
 <span data-ttu-id="0c81d-285">**-MaxUploadChanges** _number_of_upload_changes_</span><span class="sxs-lookup"><span data-stu-id="0c81d-285">**-MaxUploadChanges** _number_of_upload_changes_</span></span>  
 <span data-ttu-id="0c81d-286">指定应从订阅服务器上载到发布服务器的已更改行的最大数量。</span><span class="sxs-lookup"><span data-stu-id="0c81d-286">Specifies the maximum number of changed rows that should be uploaded from the Subscriber to the Publisher.</span></span> <span data-ttu-id="0c81d-287">上载的行数可能会由于以下原因大于指定的最大值：处理了所有生成或可能运行了并行的目标线程，这两种情况在第一次传递中均会处理至少 100 个更改。</span><span class="sxs-lookup"><span data-stu-id="0c81d-287">The number of rows uploaded may be higher than the specified maximum because: complete generations are processed; and parallel destination threads may run, each of which processes at least 100 changes in its first pass.</span></span> <span data-ttu-id="0c81d-288">默认情况下将发送所有已准备好上载的更改。</span><span class="sxs-lookup"><span data-stu-id="0c81d-288">By default all changes that are ready to be uploaded are sent.</span></span>  
  
 <span data-ttu-id="0c81d-289">**-MetadataRetentionCleanup** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-289">**-MetadataRetentionCleanup** [**0**|**1**]</span></span>  
 <span data-ttu-id="0c81d-290">指定是否基于发布的保持期从 [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql)、 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)、 [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql)、 [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)和 [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) 中删除元数据。</span><span class="sxs-lookup"><span data-stu-id="0c81d-290">Specifies if metadata is removed from [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql), and [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) based on the publication retention period.</span></span> <span data-ttu-id="0c81d-291">默认值为 **1**，指示应执行清除操作。</span><span class="sxs-lookup"><span data-stu-id="0c81d-291">The default is **1**, indicating that cleanup should occur.</span></span> <span data-ttu-id="0c81d-292">值为 **0** 指示不应自动执行清除操作。</span><span class="sxs-lookup"><span data-stu-id="0c81d-292">A value of **0** indicates that cleanup should not occur automatically.</span></span>  
  
 <span data-ttu-id="0c81d-293">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="0c81d-293">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="0c81d-294">代理输出文件的路径。</span><span class="sxs-lookup"><span data-stu-id="0c81d-294">Is the path of the agent output file.</span></span> <span data-ttu-id="0c81d-295">如果未提供文件名，则向控制台发送该输出。</span><span class="sxs-lookup"><span data-stu-id="0c81d-295">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="0c81d-296">如果指定的文件名已存在，会将输出追加到该文件。</span><span class="sxs-lookup"><span data-stu-id="0c81d-296">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="0c81d-297">**-OutputVerboseLevel** [**0**|**1**|**2**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-297">**-OutputVerboseLevel** [**0**|**1**|**2**]</span></span>  
 <span data-ttu-id="0c81d-298">指定输出是否应提供详细内容。</span><span class="sxs-lookup"><span data-stu-id="0c81d-298">Specifies whether the output should be verbose.</span></span> <span data-ttu-id="0c81d-299">如果详细级别为 0，则只输出错误消息。</span><span class="sxs-lookup"><span data-stu-id="0c81d-299">If the verbose level is **0**, only error messages are printed.</span></span> <span data-ttu-id="0c81d-300">如果详细级别为 **1**，则输出所有的进度报告消息。</span><span class="sxs-lookup"><span data-stu-id="0c81d-300">If the verbose level is **1**, all of the progress report messages are printed.</span></span> <span data-ttu-id="0c81d-301">如果详细级别为 2（默认），则输出所有错误消息和进度消息，这对调试很有帮助。</span><span class="sxs-lookup"><span data-stu-id="0c81d-301">If the verbose level is **2** (default), all error messages and progress report messages are printed, which is useful for debugging.</span></span>  
  
 <span data-ttu-id="0c81d-302">**-ParallelUploadDownload** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-302">**-ParallelUploadDownload** [**0**|**1**]</span></span>  
 <span data-ttu-id="0c81d-303">指定合并代理是否应并行处理上载到发布服务器和下载到订阅服务器的更改，这对于具有高带宽的大容量环境很有用。</span><span class="sxs-lookup"><span data-stu-id="0c81d-303">Specifies whether the Merge Agent should process in parallel the changes uploaded to the Publisher and those downloaded to the Subscriber, which is useful in high volume environments with high network bandwidth.</span></span> <span data-ttu-id="0c81d-304">如果 **ParallelUploadDownload** 为 **1**，则启用并行处理。</span><span class="sxs-lookup"><span data-stu-id="0c81d-304">If **ParallelUploadDownload** is **1**, then parallel processing is enabled.</span></span>  
  
 <span data-ttu-id="0c81d-305">**-PacketSize**</span><span class="sxs-lookup"><span data-stu-id="0c81d-305">**-PacketSize**</span></span>  
 <span data-ttu-id="0c81d-306">数据包大小（按字节计）。</span><span class="sxs-lookup"><span data-stu-id="0c81d-306">Is the packet size, in bytes.</span></span> <span data-ttu-id="0c81d-307">默认值为 4096（字节）。</span><span class="sxs-lookup"><span data-stu-id="0c81d-307">The default is 4096 (bytes).</span></span>  
  
 <span data-ttu-id="0c81d-308">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="0c81d-308">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="0c81d-309">查询发布服务器或订阅服务器有无数据更改的频率（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="0c81d-309">Is how often, in seconds, the Publisher or Subscriber is queried for data changes.</span></span> <span data-ttu-id="0c81d-310">默认值为 60 秒。</span><span class="sxs-lookup"><span data-stu-id="0c81d-310">The default is 60 seconds.</span></span>  
  
 <span data-ttu-id="0c81d-311">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="0c81d-311">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="0c81d-312">指定用于代理参数的代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="0c81d-312">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="0c81d-313">如果 **ProfileName** 为 NULL，则将禁用代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="0c81d-313">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="0c81d-314">如果未指定 **ProfileName** ，则使用该代理类型的默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="0c81d-314">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="0c81d-315">有关信息，请参阅[复制代理配置文件](replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="0c81d-315">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="0c81d-316">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="0c81d-316">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="0c81d-317">指定参加与发布数据库进行的数据库镜像会话的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移伙伴实例。</span><span class="sxs-lookup"><span data-stu-id="0c81d-317">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="0c81d-318">有关详细信息，请参阅 [数据库镜像和复制 (SQL Server)](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0c81d-318">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="0c81d-319">**-PublisherLogin** _publisher_login_</span><span class="sxs-lookup"><span data-stu-id="0c81d-319">**-PublisherLogin** _publisher_login_</span></span>  
 <span data-ttu-id="0c81d-320">发布服务器登录名。</span><span class="sxs-lookup"><span data-stu-id="0c81d-320">Is the Publisher login name.</span></span> <span data-ttu-id="0c81d-321">如果 **PublisherSecurityMode** 为 **0** （对于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证），则必须指定此参数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-321">If **PublisherSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="0c81d-322">**-PublisherPassword** _publisher_password_</span><span class="sxs-lookup"><span data-stu-id="0c81d-322">**-PublisherPassword** _publisher_password_</span></span>  
 <span data-ttu-id="0c81d-323">发布服务器密码。</span><span class="sxs-lookup"><span data-stu-id="0c81d-323">Is the Publisher password.</span></span> <span data-ttu-id="0c81d-324">如果 **PublisherSecurityMode** 为 **0** （对于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证），则必须指定此参数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-324">If **PublisherSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="0c81d-325">**-PublisherSecurityMode** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-325">**-PublisherSecurityMode** [**0**|**1**]</span></span>  
 <span data-ttu-id="0c81d-326">指定发布服务器的安全模式。</span><span class="sxs-lookup"><span data-stu-id="0c81d-326">Specifies the security mode of the Publisher.</span></span> <span data-ttu-id="0c81d-327">值 **0** 指示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证（默认值），值 **1** 指示 Windows 身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="0c81d-327">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="0c81d-328">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="0c81d-328">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="0c81d-329">查询超时前等待的秒数。默认值为 300 秒。</span><span class="sxs-lookup"><span data-stu-id="0c81d-329">Is the number of seconds before the query times out. The default is 300 seconds.</span></span> <span data-ttu-id="0c81d-330">当此值大于 1800 时，合并代理还将使用 `QueryTimeout` 的值来确定等待生成分区快照的时间。</span><span class="sxs-lookup"><span data-stu-id="0c81d-330">The Merge Agent also uses the value of `QueryTimeout` to determine how long to wait for generation of a partitioned snapshot when this value is greater than 1800.</span></span>  
  
 <span data-ttu-id="0c81d-331">**-SrcThreads** _number_of_source_threads_</span><span class="sxs-lookup"><span data-stu-id="0c81d-331">**-SrcThreads** _number_of_source_threads_</span></span>  
 <span data-ttu-id="0c81d-332">指定合并代理用于枚举来自源的更改的源线程数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-332">Specifies the number of source threads that the Merge Agent uses to enumerate changes from the source.</span></span> <span data-ttu-id="0c81d-333">在上载过程中，源是订阅服务器；在下载过程中，源是发布服务器。</span><span class="sxs-lookup"><span data-stu-id="0c81d-333">The source is the Subscriber during upload and the Publisher during download.</span></span> <span data-ttu-id="0c81d-334">默认值为 **3**。</span><span class="sxs-lookup"><span data-stu-id="0c81d-334">The default is **3**.</span></span>  
  
 <span data-ttu-id="0c81d-335">**-StartQueueTimeout** _start_queue_timeout_seconds_</span><span class="sxs-lookup"><span data-stu-id="0c81d-335">**-StartQueueTimeout** _start_queue_timeout_seconds_</span></span>  
 <span data-ttu-id="0c81d-336">当运行的并发合并进程数达到 sp_addmergepublication 的属性设置的限制时，合并代理等待的最大秒数 **@max_concurrent_merge** 。 **sp_addmergepublication**</span><span class="sxs-lookup"><span data-stu-id="0c81d-336">Is the maximum number of seconds that the Merge Agent waits when the number of concurrent merge processes running is at the limit set by the **@max_concurrent_merge** property of **sp_addmergepublication**.</span></span> <span data-ttu-id="0c81d-337">如果在达到最大秒数之后合并代理仍在等待，则合并代理将退出。</span><span class="sxs-lookup"><span data-stu-id="0c81d-337">If the maximum number of seconds is reached and the Merge Agent is still waiting, it will exit.</span></span> <span data-ttu-id="0c81d-338">值 0 表示代理将无限期地等待，但是可以将其取消。</span><span class="sxs-lookup"><span data-stu-id="0c81d-338">A value of 0 means that the agent waits indefinitely, although it can be cancelled.</span></span>  
  
 <span data-ttu-id="0c81d-339">**-SubscriberDatabasePath** _subscriber_database_path_</span><span class="sxs-lookup"><span data-stu-id="0c81d-339">**-SubscriberDatabasePath** _subscriber_database_path_</span></span>  
 <span data-ttu-id="0c81d-340">如果 **SubscriberType** 为 **2** （允许建立到 Jet 数据库的连接，而无需 ODBC 数据源名称 (DSN)），则为 Jet 数据库（.mdb 文件）的路径。</span><span class="sxs-lookup"><span data-stu-id="0c81d-340">Is the path to the Jet database (.mdb file) if **SubscriberType** is **2** (allows a connection to a Jet database without an ODBC Data Source Name (DSN)).</span></span>  
  
 <span data-ttu-id="0c81d-341">**-SubscriberDBAddOption** [**0**| **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-341">**-SubscriberDBAddOption** [**0**| **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="0c81d-342">指定是否存在现有的订阅服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="0c81d-342">Specifies whether there is an existing Subscriber database.</span></span>  
  
|<span data-ttu-id="0c81d-343">SubscriberDBAddOption 值</span><span class="sxs-lookup"><span data-stu-id="0c81d-343">SubscriberDBAddOption value</span></span>|<span data-ttu-id="0c81d-344">说明</span><span class="sxs-lookup"><span data-stu-id="0c81d-344">Description</span></span>|  
|---------------------------------|-----------------|  
|<span data-ttu-id="0c81d-345">**0**</span><span class="sxs-lookup"><span data-stu-id="0c81d-345">**0**</span></span>|<span data-ttu-id="0c81d-346">使用现有数据库（默认值）。</span><span class="sxs-lookup"><span data-stu-id="0c81d-346">Use the existing database (default).</span></span>|  
|<span data-ttu-id="0c81d-347">**1**</span><span class="sxs-lookup"><span data-stu-id="0c81d-347">**1**</span></span>|<span data-ttu-id="0c81d-348">创建一个新的空订阅服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="0c81d-348">Create a new, empty Subscriber database.</span></span>|  
|<span data-ttu-id="0c81d-349">**2**</span><span class="sxs-lookup"><span data-stu-id="0c81d-349">**2**</span></span>|<span data-ttu-id="0c81d-350">创建一个新的数据库并将其附加到指定文件。</span><span class="sxs-lookup"><span data-stu-id="0c81d-350">Create a new database and attach it to the specified file.</span></span>|  
|<span data-ttu-id="0c81d-351">**3**</span><span class="sxs-lookup"><span data-stu-id="0c81d-351">**3**</span></span>|<span data-ttu-id="0c81d-352">创建一个新数据库，附加该数据库，并启用在文件中可能存在的所有订阅。</span><span class="sxs-lookup"><span data-stu-id="0c81d-352">Create a new database, attach the database, and enable all subscriptions that might exist at the file.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="0c81d-353">如果使用值 **2** 或 **3**，则必须在 **SubscriberDatabasePath** 选项中指定订阅服务器的数据库路径。</span><span class="sxs-lookup"><span data-stu-id="0c81d-353">When you use values **2** and **3**, the database path for the Subscriber must be specified in the **SubscriberDatabasePath** option.</span></span>  
  
 <span data-ttu-id="0c81d-354">**-SubscriberLogin** _subscriber_login_</span><span class="sxs-lookup"><span data-stu-id="0c81d-354">**-SubscriberLogin** _subscriber_login_</span></span>  
 <span data-ttu-id="0c81d-355">订阅服务器登录名。</span><span class="sxs-lookup"><span data-stu-id="0c81d-355">Is the Subscriber login name.</span></span> <span data-ttu-id="0c81d-356">如果 **SubscriberSecurityMode** 为 **0** （对于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证），则必须指定此参数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-356">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="0c81d-357">**-SubscriberPassword** _subscriber_password_</span><span class="sxs-lookup"><span data-stu-id="0c81d-357">**-SubscriberPassword** _subscriber_password_</span></span>  
 <span data-ttu-id="0c81d-358">订阅服务器密码。</span><span class="sxs-lookup"><span data-stu-id="0c81d-358">Is the Subscriber password.</span></span> <span data-ttu-id="0c81d-359">如果 **SubscriberSecurityMode** 为 **0** （对于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证），则必须指定此参数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-359">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="0c81d-360">**-SubscriberSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-360">**-SubscriberSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="0c81d-361">指定订阅服务器的安全模式。</span><span class="sxs-lookup"><span data-stu-id="0c81d-361">Specifies the security mode of the Subscriber.</span></span> <span data-ttu-id="0c81d-362">值 **0** 指示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证（默认值），值 **1** 指示 Windows 身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="0c81d-362">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="0c81d-363">**-SubscriberConflictClean** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-363">**-SubscriberConflictClean** [ **0**| **1**]</span></span>  
 <span data-ttu-id="0c81d-364">如果在同步期间清除了订阅服务器上的冲突表，则值 **1** 指示订阅服务器上的冲突表已清除。</span><span class="sxs-lookup"><span data-stu-id="0c81d-364">Is if conflict tables are cleaned-up at the Subscriber during the synchronization process, where a value of **1** indicates that conflict tables at the Subscriber are cleaned-up.</span></span> <span data-ttu-id="0c81d-365">此参数仅用于对使用分散冲突日志记录的发布的订阅。</span><span class="sxs-lookup"><span data-stu-id="0c81d-365">This parameter is used only for subscriptions to publications with decentralized conflict logging.</span></span>  
  
 <span data-ttu-id="0c81d-366">**-SubscriberType** [ **0**| **1**| **3**| **4**| **5**| **6**| **7**| **8**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-366">**-SubscriberType** [ **0**| **1**| **3**| **4**| **5**| **6**| **7**| **8**]</span></span>  
 <span data-ttu-id="0c81d-367">指定合并代理所使用的订阅服务器连接的类型。</span><span class="sxs-lookup"><span data-stu-id="0c81d-367">Specifies the type of Subscriber connection used by the Merge Agent.</span></span> <span data-ttu-id="0c81d-368">仅支持将此参数设置为默认值 **0** 。</span><span class="sxs-lookup"><span data-stu-id="0c81d-368">Only the default value of **0** is supported for this parameter.</span></span>  
  
 <span data-ttu-id="0c81d-369">**-SubscriptionType**[ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-369">**-SubscriptionType**[ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="0c81d-370">指定分发的订阅类型。</span><span class="sxs-lookup"><span data-stu-id="0c81d-370">Specifies the subscription type for distribution.</span></span> <span data-ttu-id="0c81d-371">值为 **0** ，表示推送订阅（默认值），值为 **1** ，表示请求订阅，值为 **2** ，表示匿名订阅。</span><span class="sxs-lookup"><span data-stu-id="0c81d-371">A value of **0** indicates a push subscription (default), a value of **1** indicates a pull subscription, and a value of **2** indicates an anonymous subscription.</span></span>  
  
 <span data-ttu-id="0c81d-372">**-SyncToAlternate** [ **0|1**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-372">**-SyncToAlternate** [ **0|1**]</span></span>  
 <span data-ttu-id="0c81d-373">指定合并代理是否在订阅服务器和备用发布服务器之间进行同步。</span><span class="sxs-lookup"><span data-stu-id="0c81d-373">Specifies whether the Merge Agent is synchronizing between a Subscriber and an alternate Publisher.</span></span> <span data-ttu-id="0c81d-374">值为 **1** 表示它是备用发布服务器。</span><span class="sxs-lookup"><span data-stu-id="0c81d-374">A value of **1** indicates that it is an alternate Publisher.</span></span> <span data-ttu-id="0c81d-375">默认值为 **0**。</span><span class="sxs-lookup"><span data-stu-id="0c81d-375">The default is **0**.</span></span>  
  
 <span data-ttu-id="0c81d-376">**-UploadGenerationsPerBatch** _upload_generations_per_batch_</span><span class="sxs-lookup"><span data-stu-id="0c81d-376">**-UploadGenerationsPerBatch** _upload_generations_per_batch_</span></span>  
 <span data-ttu-id="0c81d-377">将订阅服务器上的更改上载到发布服务器时要在单个批次处理的生成数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-377">Is the number of generations to be processed in a single batch while uploading changes from the Subscriber to the Publisher.</span></span> <span data-ttu-id="0c81d-378">生成的定义是每个项目中属于一个逻辑组的更改。</span><span class="sxs-lookup"><span data-stu-id="0c81d-378">A generation is defined as a logical group of changes per article.</span></span> <span data-ttu-id="0c81d-379">可靠的通信链接的默认值为 **100**。</span><span class="sxs-lookup"><span data-stu-id="0c81d-379">The default for a reliable communication link is **100**.</span></span> <span data-ttu-id="0c81d-380">不可靠的通信链接的默认值为 **1**。</span><span class="sxs-lookup"><span data-stu-id="0c81d-380">The default for an unreliable communication link is **1**.</span></span>  
  
 <span data-ttu-id="0c81d-381">**-UploadReadChangesPerBatch** _upload_read_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="0c81d-381">**-UploadReadChangesPerBatch** _upload_read_changes_per_batch_</span></span>  
 <span data-ttu-id="0c81d-382">将订阅服务器上的更改上载到发布服务器时要在单个批次中读取的更改数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-382">Is the number of changes to be read in a single batch while uploading changes from the Subscriber to the Publisher.</span></span> <span data-ttu-id="0c81d-383">默认值为 **100**。</span><span class="sxs-lookup"><span data-stu-id="0c81d-383">The default is **100**.</span></span>  
  
 <span data-ttu-id="0c81d-384">**-UploadWriteChangesPerBatch** _upload_write_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="0c81d-384">**-UploadWriteChangesPerBatch** _upload_write_changes_per_batch_</span></span>  
 <span data-ttu-id="0c81d-385">将订阅服务器上的更改上载到发布服务器时要在单个批次中应用的更改数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-385">Is the number of changes to be applied in a single batch while uploading changes from the Subscriber to the Publisher.</span></span> <span data-ttu-id="0c81d-386">默认值为 **100**。</span><span class="sxs-lookup"><span data-stu-id="0c81d-386">The default is **100**.</span></span>  
  
 <span data-ttu-id="0c81d-387">**-UseInprocLoader**</span><span class="sxs-lookup"><span data-stu-id="0c81d-387">**-UseInprocLoader**</span></span>  
 <span data-ttu-id="0c81d-388">通过让合并代理在将快照文件应用于订阅服务器时使用 BULK INSERT 命令，提高初始快照的性能。</span><span class="sxs-lookup"><span data-stu-id="0c81d-388">Improves the performance of the initial snapshot by causing the Merge Agent to use the BULK INSERT command when applying snapshot files to the Subscriber.</span></span> <span data-ttu-id="0c81d-389">不推荐使用此参数，因为它与 XML 数据类型不兼容。</span><span class="sxs-lookup"><span data-stu-id="0c81d-389">This parameter is deprecated because it is not compatible with the XML data type.</span></span> <span data-ttu-id="0c81d-390">如果不复制 XML 数据，则可以使用此参数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-390">If you are not replicating XML data, this parameter can be used.</span></span> <span data-ttu-id="0c81d-391">此参数不能用于字符模式快照。</span><span class="sxs-lookup"><span data-stu-id="0c81d-391">This parameter cannot be used with character mode snapshots.</span></span> <span data-ttu-id="0c81d-392">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 如果使用此参数，订阅服务器上的  服务帐户必须具有快照 .bcp 数据文件所在目录的读取权限。</span><span class="sxs-lookup"><span data-stu-id="0c81d-392">If you use this parameter, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account at the Subscriber must have read permissions on the directory where the snapshot .bcp data files are located.</span></span> <span data-ttu-id="0c81d-393">如果不使用此参数，则代理加载的 ODBC 驱动程序将从文件中读取，从而不使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务帐户的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="0c81d-393">When this parameter is not used, the ODBC driver loaded by the agent reads from the files, so the security context of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account is not used.</span></span>  
  
 <span data-ttu-id="0c81d-394">**-Validate** [**0**|**1**|**2**|**3**]</span><span class="sxs-lookup"><span data-stu-id="0c81d-394">**-Validate** [**0**|**1**|**2**|**3**]</span></span>  
 <span data-ttu-id="0c81d-395">指定是否应在合并会话结束时执行验证，以及如果要执行验证，应执行哪种类型的验证。</span><span class="sxs-lookup"><span data-stu-id="0c81d-395">Specifies whether validation should be done at the end of the merge session, and, if so, what type of validation.</span></span> <span data-ttu-id="0c81d-396">建议值为 **3** 。</span><span class="sxs-lookup"><span data-stu-id="0c81d-396">The value of **3** is the recommended value.</span></span>  
  
|<span data-ttu-id="0c81d-397">Validate 值</span><span class="sxs-lookup"><span data-stu-id="0c81d-397">Validate value</span></span>|<span data-ttu-id="0c81d-398">说明</span><span class="sxs-lookup"><span data-stu-id="0c81d-398">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="0c81d-399">**0** （默认值）</span><span class="sxs-lookup"><span data-stu-id="0c81d-399">**0** (default)</span></span>|<span data-ttu-id="0c81d-400">不执行验证。</span><span class="sxs-lookup"><span data-stu-id="0c81d-400">No validation.</span></span>|  
|<span data-ttu-id="0c81d-401">**1**</span><span class="sxs-lookup"><span data-stu-id="0c81d-401">**1**</span></span>|<span data-ttu-id="0c81d-402">只验证行计数。</span><span class="sxs-lookup"><span data-stu-id="0c81d-402">Rowcount-only validation.</span></span>|  
|<span data-ttu-id="0c81d-403">**2**</span><span class="sxs-lookup"><span data-stu-id="0c81d-403">**2**</span></span>|<span data-ttu-id="0c81d-404">验证行计数和校验和。</span><span class="sxs-lookup"><span data-stu-id="0c81d-404">Rowcount and checksum validation.</span></span>|  
|<span data-ttu-id="0c81d-405">**3**</span><span class="sxs-lookup"><span data-stu-id="0c81d-405">**3**</span></span>|<span data-ttu-id="0c81d-406">验证行计数和二进制校验值。</span><span class="sxs-lookup"><span data-stu-id="0c81d-406">Rowcount and binary checksum validation.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="0c81d-407">如果订阅服务器与发布服务器上的数据类型不同，则使用二进制校验和或校验和进行的验证可能会错误地报告失败。</span><span class="sxs-lookup"><span data-stu-id="0c81d-407">Validation by using binary checksum or checksum can incorrectly report a failure if data types are different at the Subscriber than they are at the Publisher.</span></span> <span data-ttu-id="0c81d-408">有关详细信息，请参阅[验证已复制的数据](../validate-data-at-the-subscriber.md)的“数据验证的注意事项”部分。</span><span class="sxs-lookup"><span data-stu-id="0c81d-408">For more information, see the section "Considerations for Data Validation" in [Validate Replicated Data](../validate-data-at-the-subscriber.md).</span></span>  
  
 <span data-ttu-id="0c81d-409">**-ValidateInterval** _validate_interval_</span><span class="sxs-lookup"><span data-stu-id="0c81d-409">**-ValidateInterval** _validate_interval_</span></span>  
 <span data-ttu-id="0c81d-410">在连续模式下对订阅进行验证的频率（单位为分钟）。</span><span class="sxs-lookup"><span data-stu-id="0c81d-410">Is how often, in minutes, the subscription is validated in continuous mode.</span></span> <span data-ttu-id="0c81d-411">默认值为 **60** 分钟。</span><span class="sxs-lookup"><span data-stu-id="0c81d-411">The default is **60** minutes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c81d-412">备注</span><span class="sxs-lookup"><span data-stu-id="0c81d-412">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0c81d-413">如果您安装的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理是通过本地系统帐户而非域用户帐户（默认值）运行，则该服务只能访问本地计算机。</span><span class="sxs-lookup"><span data-stu-id="0c81d-413">If you have installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a local system account rather than under a domain user account (the default), the service can access only the local computer.</span></span> <span data-ttu-id="0c81d-414">如果以 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理身份运行的合并代理已配置为在登录到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]时使用 Windows 身份验证模式，则合并代理将失败。</span><span class="sxs-lookup"><span data-stu-id="0c81d-414">If the Merge Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Merge Agent fails.</span></span> <span data-ttu-id="0c81d-415">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认设置为  身份验证。</span><span class="sxs-lookup"><span data-stu-id="0c81d-415">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="0c81d-416">若要启动合并代理，请从命令提示符下执行 **replmerg.exe** 。</span><span class="sxs-lookup"><span data-stu-id="0c81d-416">To start the Merge Agent, execute **replmerg.exe** from the command prompt.</span></span> <span data-ttu-id="0c81d-417">有关信息，请参阅 [复制代理可执行文件](../concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="0c81d-417">For information, see [Replication Agent Executables](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
 <span data-ttu-id="0c81d-418">在连续模式下运行时，不删除当前会话的合并代理历史记录。</span><span class="sxs-lookup"><span data-stu-id="0c81d-418">The merge agent history for the current session is not removed while running in continuous mode.</span></span> <span data-ttu-id="0c81d-419">长期运行的代理可能导致合并历史记录表中包含大量条目，这会影响性能。</span><span class="sxs-lookup"><span data-stu-id="0c81d-419">A long running agent can result in a large number of entries in the merge history tables which could impact performance.</span></span> <span data-ttu-id="0c81d-420">要解决此问题，请切换到计划模式，或继续使用连续模式但是创建一个专用作业来定期重新启动合并代理，或降低历史记录级别的详细程度以减少行数从而降低性能影响。</span><span class="sxs-lookup"><span data-stu-id="0c81d-420">To resolve this problem switch to scheduled mode, or continue to use continuous mode but create a dedicated job to periodically restart the merge agent, or reduce the verbosity of the history level to reduce the number of rows and therefor reduce the performance impact.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c81d-421">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0c81d-421">See Also</span></span>  
 [<span data-ttu-id="0c81d-422">复制代理管理</span><span class="sxs-lookup"><span data-stu-id="0c81d-422">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
