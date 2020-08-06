---
title: 复制分发代理 | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Distribution Agent, executables
- agents [SQL Server replication], Distribution Agent
- Distribution Agent, parameter reference
- command prompt [SQL Server replication]
ms.assetid: 7b4fd480-9eaf-40dd-9a07-77301e44e2ac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5bd0b61626f4af268f93043114d5945d00a37b5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586621"
---
# <a name="replication-distribution-agent"></a><span data-ttu-id="09a90-102">复制分发代理</span><span class="sxs-lookup"><span data-stu-id="09a90-102">Replication Distribution Agent</span></span>
  <span data-ttu-id="09a90-103">复制分发代理是一个可执行文件，它能将快照（对于快照复制和事务复制）和保存在分发数据库表中的事务（对于事务复制）移动到订阅服务器上的目标表中。</span><span class="sxs-lookup"><span data-stu-id="09a90-103">The Replication Distribution Agent is an executable that moves the snapshot (for snapshot replication and transactional replication) and the transactions held in the distribution database tables (for transactional replication) to the destination tables at the Subscribers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09a90-104">可以按任意顺序指定参数。</span><span class="sxs-lookup"><span data-stu-id="09a90-104">Parameters can be specified in any order.</span></span> <span data-ttu-id="09a90-105">如果未指定可选参数，将使用本地计算机上预定义的注册表设置中的值。</span><span class="sxs-lookup"><span data-stu-id="09a90-105">When optional parameters are not specified, values from predefined registry settings on the local computer are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09a90-106">语法</span><span class="sxs-lookup"><span data-stu-id="09a90-106">Syntax</span></span>  
  
```  
  
      distrib [-?]  
-Publisherserver_name[\instance_name]  
-PublisherDBpublisher_database-Subscriberserver_name[\instance_name]  
-SubscriberDBsubscriber_database   
[-AltSnapshotFolderalt_snapshot_folder_path]   
[-BcpBatchSizebcp_batch_size]  
[-CommitBatchSizecommit_batch_size]  
[-CommitBatchThresholdcommit_batch_threshold]  
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributordistributor]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-ErrorFileerror_path_and_file_name]  
[-ExtendedEventConfigFileconfiguration_path_and_file_name]  
[-FileTransferType [0|1]]  
[-FtpAddressftp_address]  
[-FtpPasswordftp_password]   
[-FtpPortftp_port]  
[-FtpUserNameftp_user_name]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-Hostnamehost_name]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MaxBcpThreads]  
[-MaxDeliveredTransactionsnumber_of_transactions]  
[-MessageIntervalmessage_interval]  
[-OledbStreamThresholdoledb_stream_threshold]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PacketSizepacket_size]  
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]  
[-Publicationpublication]  
[-QueryTimeOutquery_time_out_seconds]  
[-QuotedIdentifierquoted_identifier]  
[-SkipErrorsnative_error_id [:...n]]  
[-SubscriberDatabasePathsubscriber_path]  
[-SubscriberLoginsubscriber_login]  
[-SubscriberPasswordsubscriber_password]  
[-SubscriberSecurityMode [0|1]]  
[-SubscriberType [0|1|3]]  
[-SubscriptionStreams [1|2|...64]]  
[-SubscriptionTableNamesubscription_table]  
[-SubscriptionType [0|1|2]]  
[-TransactionsPerHistory [0|1|...10000]]  
[-UseDTS]  
[-UseInprocLoader]  
[-UseOledbStreaming]  
```  
  
## <a name="arguments"></a><span data-ttu-id="09a90-107">参数</span><span class="sxs-lookup"><span data-stu-id="09a90-107">Arguments</span></span>  
 <span data-ttu-id="09a90-108">**-?**</span><span class="sxs-lookup"><span data-stu-id="09a90-108">**-?**</span></span>  
 <span data-ttu-id="09a90-109">输出所有可用的参数。</span><span class="sxs-lookup"><span data-stu-id="09a90-109">Prints all available parameters.</span></span>  
  
 <span data-ttu-id="09a90-110">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="09a90-110">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="09a90-111">发布服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="09a90-111">Is the name of the Publisher.</span></span> <span data-ttu-id="09a90-112">为该服务器上的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认实例指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="09a90-112">Specify *server_name* for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="09a90-113">为该服务器上的 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认实例指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="09a90-113">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="09a90-114">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="09a90-114">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="09a90-115">发布服务器数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="09a90-115">Is the name of the Publisher database.</span></span>  
  
 <span data-ttu-id="09a90-116">**-Subscriber** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="09a90-116">**-Subscriber** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="09a90-117">订阅服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="09a90-117">Is the name of the Subscriber.</span></span> <span data-ttu-id="09a90-118">为该服务器上的 *默认实例指定* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="09a90-118">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="09a90-119">为该服务器上的 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认实例指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="09a90-119">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="09a90-120">**-SubscriberDB** _subscriber_database_</span><span class="sxs-lookup"><span data-stu-id="09a90-120">**-SubscriberDB** _subscriber_database_</span></span>  
 <span data-ttu-id="09a90-121">订阅服务器数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="09a90-121">Is the name of the Subscriber database.</span></span>  
  
 <span data-ttu-id="09a90-122">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span><span class="sxs-lookup"><span data-stu-id="09a90-122">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span></span>  
 <span data-ttu-id="09a90-123">包含订阅的初始快照的文件夹路径。</span><span class="sxs-lookup"><span data-stu-id="09a90-123">Is the path to the folder that contains the initial snapshot for a subscription.</span></span>  
  
 <span data-ttu-id="09a90-124">**-BcpBatchSize** _bcp_batch_size_</span><span class="sxs-lookup"><span data-stu-id="09a90-124">**-BcpBatchSize** _bcp_batch_size_</span></span>  
 <span data-ttu-id="09a90-125">在一次大容量复制操作中发送的行数。</span><span class="sxs-lookup"><span data-stu-id="09a90-125">Is the number of rows to send in a bulk copy operation.</span></span> <span data-ttu-id="09a90-126">执行 **bcp in** 操作时，批的大小为要作为一个事务发送到服务器的行数，并且也是分发代理记录 bcp 进度消息之前必须发送的行数。</span><span class="sxs-lookup"><span data-stu-id="09a90-126">When performing a **bcp in** operation, the batch size is the number of rows to send to the server as one transaction, and also the number of rows that must be sent before the Distribution Agent logs a **bcp** progress message.</span></span> <span data-ttu-id="09a90-127">当执行 **bcp out** 操作时，将使用固定批大小 **1000** 。</span><span class="sxs-lookup"><span data-stu-id="09a90-127">When performing a **bcp out** operation, a fixed batch size of **1000** is used.</span></span>  
  
 <span data-ttu-id="09a90-128">**-CommitBatchSize** _commit_batch_size_</span><span class="sxs-lookup"><span data-stu-id="09a90-128">**-CommitBatchSize** _commit_batch_size_</span></span>  
 <span data-ttu-id="09a90-129">发出 COMMIT 语句前要发给订阅服务器的事务数。</span><span class="sxs-lookup"><span data-stu-id="09a90-129">Is the number of transactions to be issued to the Subscriber before a COMMIT statement is issued.</span></span> <span data-ttu-id="09a90-130">默认值为 100。</span><span class="sxs-lookup"><span data-stu-id="09a90-130">The default is 100.</span></span>  
  
 <span data-ttu-id="09a90-131">**-CommitBatchThreshold**  _commit_batch_threshold_</span><span class="sxs-lookup"><span data-stu-id="09a90-131">**-CommitBatchThreshold**  _commit_batch_threshold_</span></span>  
 <span data-ttu-id="09a90-132">发出 COMMIT 语句前要发给订阅服务器的复制命令数。</span><span class="sxs-lookup"><span data-stu-id="09a90-132">Is the number of replication commands to be issued to the Subscriber before a COMMIT statement is issued.</span></span> <span data-ttu-id="09a90-133">默认值为 1000。</span><span class="sxs-lookup"><span data-stu-id="09a90-133">The default is 1000.</span></span>  
  
 <span data-ttu-id="09a90-134">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="09a90-134">**-Continuous**</span></span>  
 <span data-ttu-id="09a90-135">指定代理是否尝试连续轮询已复制的事务。</span><span class="sxs-lookup"><span data-stu-id="09a90-135">Specifies whether the agent attempts to poll replicated transactions continually.</span></span> <span data-ttu-id="09a90-136">如果指定了该参数，即使没有事务挂起，代理也将在轮询间隔期间轮询来自源的已复制事务。</span><span class="sxs-lookup"><span data-stu-id="09a90-136">If specified, the agent polls replicated transactions from the source at polling intervals, even if there are no transactions pending.</span></span>  
  
 <span data-ttu-id="09a90-137">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="09a90-137">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="09a90-138">代理定义文件的路径。</span><span class="sxs-lookup"><span data-stu-id="09a90-138">Is the path of the agent definition file.</span></span> <span data-ttu-id="09a90-139">代理定义文件中包含代理的命令提示符参数。</span><span class="sxs-lookup"><span data-stu-id="09a90-139">An agent definition file contains command prompt arguments for the agent.</span></span> <span data-ttu-id="09a90-140">文件的内容被当作可执行文件进行分析。</span><span class="sxs-lookup"><span data-stu-id="09a90-140">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="09a90-141">使用双引号 (") 指定包含任意字符的参数值。</span><span class="sxs-lookup"><span data-stu-id="09a90-141">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="09a90-142">**-Distributor** _distributor_</span><span class="sxs-lookup"><span data-stu-id="09a90-142">**-Distributor** _distributor_</span></span>  
 <span data-ttu-id="09a90-143">分发服务器名称。</span><span class="sxs-lookup"><span data-stu-id="09a90-143">Is the Distributor name.</span></span> <span data-ttu-id="09a90-144">对于分发服务器（推送）分发，该名称默认为本地分发服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="09a90-144">For Distributor (push) distribution, the name defaults to the name of the local Distributor.</span></span>  
  
 <span data-ttu-id="09a90-145">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="09a90-145">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="09a90-146">分发服务器登录名。</span><span class="sxs-lookup"><span data-stu-id="09a90-146">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="09a90-147">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="09a90-147">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="09a90-148">分发服务器密码。</span><span class="sxs-lookup"><span data-stu-id="09a90-148">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="09a90-149">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="09a90-149">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="09a90-150">指定分发服务器的安全模式。</span><span class="sxs-lookup"><span data-stu-id="09a90-150">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="09a90-151">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 值为 0，表示为  身份验证模式，值为 1，表示为 Windows 身份验证模式（默认）。</span><span class="sxs-lookup"><span data-stu-id="09a90-151">A value of 0 indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode, and a value of 1 indicates Windows Authentication Mode (default).</span></span>  
  
 <span data-ttu-id="09a90-152">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="09a90-152">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="09a90-153">分发代理建立连接时使用的安全套接字层 (SSL) 加密级别。</span><span class="sxs-lookup"><span data-stu-id="09a90-153">Is the level of Secure Sockets Layer (SSL) encryption used by the Distribution Agent when making connections.</span></span>  
  
|<span data-ttu-id="09a90-154">EncryptionLevel 值</span><span class="sxs-lookup"><span data-stu-id="09a90-154">EncryptionLevel value</span></span>|<span data-ttu-id="09a90-155">说明</span><span class="sxs-lookup"><span data-stu-id="09a90-155">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="09a90-156">**0**</span><span class="sxs-lookup"><span data-stu-id="09a90-156">**0**</span></span>|<span data-ttu-id="09a90-157">指定不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="09a90-157">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="09a90-158">**1**</span><span class="sxs-lookup"><span data-stu-id="09a90-158">**1**</span></span>|<span data-ttu-id="09a90-159">指定使用 SSL，但是代理不验证 SSL 服务器证书是否已由可信的颁发者进行签名。</span><span class="sxs-lookup"><span data-stu-id="09a90-159">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="09a90-160">**2**</span><span class="sxs-lookup"><span data-stu-id="09a90-160">**2**</span></span>|<span data-ttu-id="09a90-161">指定使用 SSL，并验证证书。</span><span class="sxs-lookup"><span data-stu-id="09a90-161">Specifies that SSL is used, and that the certificate is verified.</span></span>|  
 
 > [!NOTE]  
 >  <span data-ttu-id="09a90-162">使用 SQL Server 的完全限定的域名定义有效的 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="09a90-162">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="09a90-163">为了在将 -EncryptionLevel 设置为 2 时成功连接代理，请在本地 SQL Server 上创建别名。</span><span class="sxs-lookup"><span data-stu-id="09a90-163">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="09a90-164">“Alias Name”参数应为服务器名称，”Server”参数应设置为 SQL Server 的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="09a90-164">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>

 <span data-ttu-id="09a90-165">有关详细信息，请参阅[SQL Server 复制安全性](../security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="09a90-165">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="09a90-166">**-ErrorFile** _error_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="09a90-166">**-ErrorFile** _error_path_and_file_name_</span></span>  
 <span data-ttu-id="09a90-167">分发代理生成的错误文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="09a90-167">Is the path and file name of the error file generated by the Distribution Agent.</span></span> <span data-ttu-id="09a90-168">在订阅服务器上应用复制事务时，在故障发生位置生成此文件；在发布服务器或分发服务器上出现的错误不记录在此文件中。</span><span class="sxs-lookup"><span data-stu-id="09a90-168">This file is generated at any point where failure occurred while applying replication transactions at the Subscriber; errors that occur at the Publisher or Distributor are not logged in this file.</span></span> <span data-ttu-id="09a90-169">此文件包含失败的复制事务和相关的错误消息。</span><span class="sxs-lookup"><span data-stu-id="09a90-169">This file contains the failed replication transactions and associated error messages.</span></span> <span data-ttu-id="09a90-170">如果没有指定，则在分发代理的当前目录中生成此错误文件。</span><span class="sxs-lookup"><span data-stu-id="09a90-170">When not specified, the error file is generated in the current directory of the Distribution Agent.</span></span> <span data-ttu-id="09a90-171">错误文件名为分发代理的名称，扩展名为 .err。</span><span class="sxs-lookup"><span data-stu-id="09a90-171">The error file name is the name of the Distribution Agent with an .err extension.</span></span> <span data-ttu-id="09a90-172">如果指定的文件名已存在，会将错误消息追加到该文件中。</span><span class="sxs-lookup"><span data-stu-id="09a90-172">If the specified file name exists, error messages are appended to the file.</span></span> <span data-ttu-id="09a90-173">此参数最多可包含 256 个 Unicode 字符。</span><span class="sxs-lookup"><span data-stu-id="09a90-173">This parameter can be a maximum of 256 Unicode characters.</span></span>  
  
 <span data-ttu-id="09a90-174">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="09a90-174">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span></span>  
 <span data-ttu-id="09a90-175">为扩展事件 XML 配置文件指定路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="09a90-175">Specifies the path and file name for the extended events XML configuration file.</span></span> <span data-ttu-id="09a90-176">通过该扩展事件 XML 配置文件，您可以配置会话并且启用事件跟踪。</span><span class="sxs-lookup"><span data-stu-id="09a90-176">The extended events configuration file allows you to configure sessions and enable events for tracking.</span></span>  
  
 <span data-ttu-id="09a90-177">**-FileTransferType** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="09a90-177">**-FileTransferType** [ **0**| **1**]</span></span>  
 <span data-ttu-id="09a90-178">指定文件传输类型。</span><span class="sxs-lookup"><span data-stu-id="09a90-178">Specifies the file transfer type.</span></span> <span data-ttu-id="09a90-179">值为 **0** ，表示 UNC（通用命名约定），值为 1，表示 FTP（文件传输协议）。</span><span class="sxs-lookup"><span data-stu-id="09a90-179">A value of **0** indicates UNC (universal naming convention), and a value of **1** indicates FTP (file transfer protocol).</span></span>  
  
 <span data-ttu-id="09a90-180">**-FtpAddress** _ftp_address_</span><span class="sxs-lookup"><span data-stu-id="09a90-180">**-FtpAddress** _ftp_address_</span></span>  
 <span data-ttu-id="09a90-181">分发服务器的 FTP 服务网络地址。</span><span class="sxs-lookup"><span data-stu-id="09a90-181">Is the network address of the FTP service for the Distributor.</span></span> <span data-ttu-id="09a90-182">未指定该参数时，使用 DistributorAddress。</span><span class="sxs-lookup"><span data-stu-id="09a90-182">When not specified, **DistributorAddress** is used.</span></span> <span data-ttu-id="09a90-183">如果未指定 **DistributorAddress** ，将使用 Distributor。</span><span class="sxs-lookup"><span data-stu-id="09a90-183">If **DistributorAddress** is not specified, **Distributor** is used.</span></span>  
  
 <span data-ttu-id="09a90-184">**-FtpPassword** _ftp_password_</span><span class="sxs-lookup"><span data-stu-id="09a90-184">**-FtpPassword** _ftp_password_</span></span>  
 <span data-ttu-id="09a90-185">用于连接到 FTP 服务的用户密码。</span><span class="sxs-lookup"><span data-stu-id="09a90-185">Is the user password used to connect to the FTP service.</span></span>  
  
 <span data-ttu-id="09a90-186">**-FtpPort** _ftp_port_</span><span class="sxs-lookup"><span data-stu-id="09a90-186">**-FtpPort** _ftp_port_</span></span>  
 <span data-ttu-id="09a90-187">分发服务器 FTP 服务的端口号。</span><span class="sxs-lookup"><span data-stu-id="09a90-187">Is the port number of the FTP service for the Distributor.</span></span> <span data-ttu-id="09a90-188">如果不指定，则使用 FTP 服务的默认端口号 (21)。</span><span class="sxs-lookup"><span data-stu-id="09a90-188">When not specified, the default port number for FTP service (21) is used.</span></span>  
  
 <span data-ttu-id="09a90-189">**-FtpUserName**  _ftp_user_name_</span><span class="sxs-lookup"><span data-stu-id="09a90-189">**-FtpUserName**  _ftp_user_name_</span></span>  
 <span data-ttu-id="09a90-190">用于连接到 FTP 服务的用户名。</span><span class="sxs-lookup"><span data-stu-id="09a90-190">Is the user name used to connect to the FTP service.</span></span> <span data-ttu-id="09a90-191"> 如果不指定，则使用 anonymous。</span><span class="sxs-lookup"><span data-stu-id="09a90-191">When not specified, **anonymous** is used.</span></span>  
  
 <span data-ttu-id="09a90-192">**-HistoryVerboseLevel** [ **0** | **1** | **2** | **3** ]</span><span class="sxs-lookup"><span data-stu-id="09a90-192">**-HistoryVerboseLevel** [ **0** | **1** | **2** | **3** ]</span></span>  
 <span data-ttu-id="09a90-193">指定分发操作期间记录的历史信息量。</span><span class="sxs-lookup"><span data-stu-id="09a90-193">Specifies the amount of history logged during a distribution operation.</span></span> <span data-ttu-id="09a90-194">选择 1 可将历史日志记录对性能的影响减小到最低限度。</span><span class="sxs-lookup"><span data-stu-id="09a90-194">You can minimize the performance effect of history logging by selecting **1**.</span></span>  
  
|<span data-ttu-id="09a90-195">HistoryVerboseLevel 值</span><span class="sxs-lookup"><span data-stu-id="09a90-195">HistoryVerboseLevel value</span></span>|<span data-ttu-id="09a90-196">说明</span><span class="sxs-lookup"><span data-stu-id="09a90-196">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="09a90-197">**0**</span><span class="sxs-lookup"><span data-stu-id="09a90-197">**0**</span></span>|<span data-ttu-id="09a90-198">进度消息将写入控制台或输出文件。</span><span class="sxs-lookup"><span data-stu-id="09a90-198">Progress messages are written either to the console or to an output file.</span></span> <span data-ttu-id="09a90-199">不在分发数据库中记录历史记录。</span><span class="sxs-lookup"><span data-stu-id="09a90-199">History records are not logged in the distribution database.</span></span>|  
|<span data-ttu-id="09a90-200">**1**</span><span class="sxs-lookup"><span data-stu-id="09a90-200">**1**</span></span>|<span data-ttu-id="09a90-201">默认。</span><span class="sxs-lookup"><span data-stu-id="09a90-201">Default.</span></span> <span data-ttu-id="09a90-202">总是更新具有相同状态（启动、进行中、成功等）的上一历史记录消息。</span><span class="sxs-lookup"><span data-stu-id="09a90-202">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="09a90-203">如果不存在状态相同的上一记录，将插入新记录。</span><span class="sxs-lookup"><span data-stu-id="09a90-203">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="09a90-204">**2**</span><span class="sxs-lookup"><span data-stu-id="09a90-204">**2**</span></span>|<span data-ttu-id="09a90-205">除非记录为空闲消息或长时间运行的作业消息等信息（此时将更新上一记录），否则插入新的历史记录。</span><span class="sxs-lookup"><span data-stu-id="09a90-205">Insert new history records unless the record is for such things as idle messages or long-running job messages, in which case update the previous records.</span></span>|  
|<span data-ttu-id="09a90-206">**3**</span><span class="sxs-lookup"><span data-stu-id="09a90-206">**3**</span></span>|<span data-ttu-id="09a90-207">始终插入新记录，除非它与空闲消息有关。</span><span class="sxs-lookup"><span data-stu-id="09a90-207">Always insert new records, unless it is for idle messages.</span></span>|  
  
 <span data-ttu-id="09a90-208">**-Hostname** _host_name_</span><span class="sxs-lookup"><span data-stu-id="09a90-208">**-Hostname** _host_name_</span></span>  
 <span data-ttu-id="09a90-209">连接到发布服务器时使用的主机名。</span><span class="sxs-lookup"><span data-stu-id="09a90-209">Is the host name used when connecting to the Publisher.</span></span> <span data-ttu-id="09a90-210">此参数最多可包含 128 个 Unicode 字符。</span><span class="sxs-lookup"><span data-stu-id="09a90-210">This parameter can be a maximum of 128 Unicode characters.</span></span>  
  
 <span data-ttu-id="09a90-211">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="09a90-211">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span></span>  
 <span data-ttu-id="09a90-212">在历史记录线程检查目前是否有连接在等待服务器响应之前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="09a90-212">Is the number of seconds before the history thread checks if any of the existing connections is waiting for a response from the server.</span></span> <span data-ttu-id="09a90-213">在执行长时间运行的批处理时，减小该值可避免检查代理将分发代理标记为可疑。</span><span class="sxs-lookup"><span data-stu-id="09a90-213">This value can be decreased to avoid having the checkup agent mark the Distribution Agent as suspect when executing a long-running batch.</span></span> <span data-ttu-id="09a90-214">默认值为 **300** 秒。</span><span class="sxs-lookup"><span data-stu-id="09a90-214">The default is **300** seconds.</span></span>  
  
 <span data-ttu-id="09a90-215">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="09a90-215">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="09a90-216">登录超时前等待的秒数。 默认值为 15 秒。</span><span class="sxs-lookup"><span data-stu-id="09a90-216">Is the number of seconds before the login times out. The default is **15** seconds.</span></span>  
  
 <span data-ttu-id="09a90-217">**-MaxBcpThreads** _number_of_threads_</span><span class="sxs-lookup"><span data-stu-id="09a90-217">**-MaxBcpThreads** _number_of_threads_</span></span>  
 <span data-ttu-id="09a90-218">指定可以并行执行的大容量复制操作的数量。</span><span class="sxs-lookup"><span data-stu-id="09a90-218">Specifies the number of bulk copy operations that can be performed in parallel.</span></span> <span data-ttu-id="09a90-219">同时存在的线程和 ODBC 连接的最大数量为 **MaxBcpThreads** 或显示在分发数据库中同步事务中的大容量复制请求数中较小的那一个。</span><span class="sxs-lookup"><span data-stu-id="09a90-219">The maximum number of threads and ODBC connections that exist simultaneously is the lesser of **MaxBcpThreads** or the number of bulk copy requests that appear in the synchronization transaction in the distribution database.</span></span> <span data-ttu-id="09a90-220">**MaxBcpThreads** 的值必须大于 **0** ，并且不存在任何硬编码的上限。</span><span class="sxs-lookup"><span data-stu-id="09a90-220">**MaxBcpThreads** must have a value greater than **0** and has no hard-coded upper limit.</span></span> <span data-ttu-id="09a90-221">默认值是处理器数目的 **2**倍，最大值为 8。</span><span class="sxs-lookup"><span data-stu-id="09a90-221">The default is **2** times the number of processors, up to a maximum value of **8**.</span></span> <span data-ttu-id="09a90-222">应用于使用并发快照选项在发布服务器上生成的快照时，不管为 **MaxBcpThreads**指定了什么数值，都将使用一个线程。</span><span class="sxs-lookup"><span data-stu-id="09a90-222">When applying a snapshot that was generated at the Publisher using the concurrent snapshot option, one thread is used, regardless of the number you specify for **MaxBcpThreads**.</span></span>  
  
 <span data-ttu-id="09a90-223">**-MaxDeliveredTransactions** _number_of_transactions_</span><span class="sxs-lookup"><span data-stu-id="09a90-223">**-MaxDeliveredTransactions** _number_of_transactions_</span></span>  
 <span data-ttu-id="09a90-224">一次同步期间应用于订阅服务器的推送事务或请求事务的最大数量。</span><span class="sxs-lookup"><span data-stu-id="09a90-224">Is the maximum number of push or pull transactions applied to Subscribers in one synchronization.</span></span> <span data-ttu-id="09a90-225">值为 0，表示最大值为无穷多个事务。</span><span class="sxs-lookup"><span data-stu-id="09a90-225">A value of **0** indicates that the maximum is an infinite number of transactions.</span></span> <span data-ttu-id="09a90-226">订阅服务器可使用其他值缩短从发布服务器请求的同步的持续时间。</span><span class="sxs-lookup"><span data-stu-id="09a90-226">Other values can be used by Subscribers to shorten the duration of a synchronization being pulled from a Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09a90-227">如果同时指定了 -MaxDeliveredTransactions 和 -Continuous，分发代理将传送指定数目的事务，然后停止（即使指定了 -Continuous）。</span><span class="sxs-lookup"><span data-stu-id="09a90-227">If -MaxDeliveredTransactions and -Continuous are both specified, the Distribution Agent delivers the specified number of transactions and then stops (even though -Continuous is specified).</span></span> <span data-ttu-id="09a90-228">在作业完成后，您必须重新启动分发代理。</span><span class="sxs-lookup"><span data-stu-id="09a90-228">You must restart the Distribution Agent after the job completes.</span></span>  
  
 <span data-ttu-id="09a90-229">**-MessageInterval**  _message_interval_</span><span class="sxs-lookup"><span data-stu-id="09a90-229">**-MessageInterval**  _message_interval_</span></span>  
 <span data-ttu-id="09a90-230">用于历史日志记录的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="09a90-230">Is the time interval used for history logging.</span></span> <span data-ttu-id="09a90-231">当达到以下参数值之一时，将记录一个历史记录事件：</span><span class="sxs-lookup"><span data-stu-id="09a90-231">A history event is logged when one of these parameters is reached:</span></span>  
  
-   <span data-ttu-id="09a90-232">记录上一历史记录事件后，达到 **TransactionsPerHistory** 值。</span><span class="sxs-lookup"><span data-stu-id="09a90-232">The **TransactionsPerHistory** value is reached after the last history event is logged.</span></span>  
  
-   <span data-ttu-id="09a90-233">记录上一历史记录事件后，达到 **MessageInterval** 值。</span><span class="sxs-lookup"><span data-stu-id="09a90-233">The **MessageInterval** value is reached after the last history event is logged.</span></span>  
  
 <span data-ttu-id="09a90-234">如果源上没有可用的已复制事务，代理将向分发服务器报告无事务消息。</span><span class="sxs-lookup"><span data-stu-id="09a90-234">If there is no replicated transaction available at the source, the agent reports a no-transaction message to the Distributor.</span></span> <span data-ttu-id="09a90-235">此选项可指定代理在报告另一条无事务消息前将等待多长时间。</span><span class="sxs-lookup"><span data-stu-id="09a90-235">This option specifies how long the agent waits before reporting another no-transaction message.</span></span> <span data-ttu-id="09a90-236">在上次处理已复制事务后，如果代理在源上没有检测到任何可用的事务，则总是会报告一条无事务消息。</span><span class="sxs-lookup"><span data-stu-id="09a90-236">Agents always report a no-transaction message when they detect that there are no transactions available at the source after previously processing replicated transactions.</span></span> <span data-ttu-id="09a90-237">默认值为 60 秒。</span><span class="sxs-lookup"><span data-stu-id="09a90-237">The default is 60 seconds.</span></span>  
  
 <span data-ttu-id="09a90-238">**-OledbStreamThreshold** _oledb_stream_threshold_</span><span class="sxs-lookup"><span data-stu-id="09a90-238">**-OledbStreamThreshold** _oledb_stream_threshold_</span></span>  
 <span data-ttu-id="09a90-239">指定二进制大型对象数据的最小大小（按字节计），如果超过此大小，数据将作为流进行绑定。</span><span class="sxs-lookup"><span data-stu-id="09a90-239">Specifies the minimum size, in bytes, for binary large object data above which the data will be bound as a stream.</span></span> <span data-ttu-id="09a90-240">必须将 -UseOledbStreaming 指定为使用此参数。</span><span class="sxs-lookup"><span data-stu-id="09a90-240">You must specify **-UseOledbStreaming** to use this parameter.</span></span> <span data-ttu-id="09a90-241">值可以介于 400 个字节到 1048576 个字节之间，默认值为 16384 个字节。</span><span class="sxs-lookup"><span data-stu-id="09a90-241">Values can range from 400 to 1048576 bytes, with a default of 16384 bytes.</span></span>  
  
 <span data-ttu-id="09a90-242">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="09a90-242">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="09a90-243">代理输出文件的路径。</span><span class="sxs-lookup"><span data-stu-id="09a90-243">Is the path of the agent output file.</span></span> <span data-ttu-id="09a90-244">如果未提供文件名，则向控制台发送该输出。</span><span class="sxs-lookup"><span data-stu-id="09a90-244">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="09a90-245">如果指定的文件名已存在，会将输出追加到该文件。</span><span class="sxs-lookup"><span data-stu-id="09a90-245">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="09a90-246">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="09a90-246">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="09a90-247">指定输出是否应提供详细内容。</span><span class="sxs-lookup"><span data-stu-id="09a90-247">Specifies whether the output should be verbose.</span></span> <span data-ttu-id="09a90-248">如果详细级别为 0，则只输出错误消息。</span><span class="sxs-lookup"><span data-stu-id="09a90-248">If the verbose level is **0**, only error messages are printed.</span></span> <span data-ttu-id="09a90-249">如果详细级别为 1，则输出所有进度报告消息。</span><span class="sxs-lookup"><span data-stu-id="09a90-249">If the verbose level is **1**, all the progress report messages are printed.</span></span> <span data-ttu-id="09a90-250">如果详细级别为 2（默认），则输出所有错误消息和进度消息，这对调试很有帮助。</span><span class="sxs-lookup"><span data-stu-id="09a90-250">If the verbose level is **2** (default), all error messages and progress report messages are printed, which is useful for debugging.</span></span>  
  
 <span data-ttu-id="09a90-251">**-PacketSize** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="09a90-251">**-PacketSize** _packet_size_</span></span>  
 <span data-ttu-id="09a90-252">数据包大小（按字节计）。</span><span class="sxs-lookup"><span data-stu-id="09a90-252">Is the packet size, in bytes.</span></span> <span data-ttu-id="09a90-253">默认值为 4096（字节）。</span><span class="sxs-lookup"><span data-stu-id="09a90-253">The default is 4096 (bytes).</span></span>  
  
 <span data-ttu-id="09a90-254">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="09a90-254">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="09a90-255">对分发数据库进行已复制事务查询的频率（以秒计）。</span><span class="sxs-lookup"><span data-stu-id="09a90-255">Is how often, in seconds, the distribution database is queried for replicated transactions.</span></span> <span data-ttu-id="09a90-256">默认值为 5 秒。</span><span class="sxs-lookup"><span data-stu-id="09a90-256">The default is 5 seconds.</span></span>  
  
 <span data-ttu-id="09a90-257">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="09a90-257">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="09a90-258">指定用于代理参数的代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="09a90-258">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="09a90-259">如果 **ProfileName** 为 NULL，则将禁用代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="09a90-259">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="09a90-260">如果未指定 **ProfileName** ，则使用该代理类型的默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="09a90-260">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="09a90-261">有关信息，请参阅[复制代理配置文件](replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="09a90-261">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="09a90-262">**-Publication**  _publication_</span><span class="sxs-lookup"><span data-stu-id="09a90-262">**-Publication**  _publication_</span></span>  
 <span data-ttu-id="09a90-263">发布的名称。</span><span class="sxs-lookup"><span data-stu-id="09a90-263">Is the name of the publication.</span></span> <span data-ttu-id="09a90-264">只有将发布设置为总是使快照可用于新订阅或重新初始化的订阅时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="09a90-264">This parameter is only valid if the publication is set to always have a snapshot available for new or reinitialized subscriptions.</span></span>  
  
 <span data-ttu-id="09a90-265">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="09a90-265">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="09a90-266">查询超时前等待的秒数。默认值为 1800 秒。</span><span class="sxs-lookup"><span data-stu-id="09a90-266">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="09a90-267">**-QuotedIdentifier** _quoted_identifier_</span><span class="sxs-lookup"><span data-stu-id="09a90-267">**-QuotedIdentifier** _quoted_identifier_</span></span>  
 <span data-ttu-id="09a90-268">指定要使用的带引号的标识符字符。</span><span class="sxs-lookup"><span data-stu-id="09a90-268">Specifies the quoted identifier character to use.</span></span> <span data-ttu-id="09a90-269">该值的第一个字符表示分发代理使用的值。</span><span class="sxs-lookup"><span data-stu-id="09a90-269">The first character of the value indicates the value the Distribution Agent uses.</span></span> <span data-ttu-id="09a90-270">如果使用不带有任何值的 **QuotedIdentifier** ，则分发代理使用一个空格。</span><span class="sxs-lookup"><span data-stu-id="09a90-270">If **QuotedIdentifier** is used with no value, the Distribution Agent uses a space.</span></span> <span data-ttu-id="09a90-271">如果未使用 **QuotedIdentifier** ，则分发代理使用订阅服务器支持的任意带引号的标识符。</span><span class="sxs-lookup"><span data-stu-id="09a90-271">If **QuotedIdentifier** is not used, the Distribution Agent uses whatever quoted identifier the Subscriber supports.</span></span>  
  
 <span data-ttu-id="09a90-272">**-SkipErrors** _native_error_id_ [ **:** _...n_]</span><span class="sxs-lookup"><span data-stu-id="09a90-272">**-SkipErrors** _native_error_id_ [**:**_...n_]</span></span>  
 <span data-ttu-id="09a90-273">以冒号分隔的列表，指定此代理要跳过的错误号。</span><span class="sxs-lookup"><span data-stu-id="09a90-273">Is a colon-separated list that specifies the error numbers to be skipped by this agent.</span></span>  
  
 <span data-ttu-id="09a90-274">**-SubscriberDatabasePath** _subscriber_database_path_</span><span class="sxs-lookup"><span data-stu-id="09a90-274">**-SubscriberDatabasePath** _subscriber_database_path_</span></span>  
 <span data-ttu-id="09a90-275">如果 **SubscriberType** 为 **2** （允许建立到 Jet 数据库的连接，而无需 ODBC 数据源名称 (DSN)），则为 Jet 数据库（.mdb 文件）的路径。</span><span class="sxs-lookup"><span data-stu-id="09a90-275">Is the path to the Jet database (.mdb file) if **SubscriberType** is **2** (allows a connection to a Jet database without an ODBC Data Source Name (DSN)).</span></span>  
  
 <span data-ttu-id="09a90-276">**-SubscriberLogin** _subscriber_login_</span><span class="sxs-lookup"><span data-stu-id="09a90-276">**-SubscriberLogin** _subscriber_login_</span></span>  
 <span data-ttu-id="09a90-277">订阅服务器登录名。</span><span class="sxs-lookup"><span data-stu-id="09a90-277">Is the Subscriber login name.</span></span> <span data-ttu-id="09a90-278">如果 **SubscriberSecurityMode** 为 **0** （对于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证），则必须指定此参数。</span><span class="sxs-lookup"><span data-stu-id="09a90-278">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="09a90-279">**-SubscriberPassword** _subscriber_password_</span><span class="sxs-lookup"><span data-stu-id="09a90-279">**-SubscriberPassword** _subscriber_password_</span></span>  
 <span data-ttu-id="09a90-280">订阅服务器密码。</span><span class="sxs-lookup"><span data-stu-id="09a90-280">Is the Subscriber password.</span></span> <span data-ttu-id="09a90-281">如果 **SubscriberSecurityMode** 为 **0** （对于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证），则必须指定此参数。</span><span class="sxs-lookup"><span data-stu-id="09a90-281">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="09a90-282">**-SubscriberSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="09a90-282">**-SubscriberSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="09a90-283">指定订阅服务器的安全模式。</span><span class="sxs-lookup"><span data-stu-id="09a90-283">Specifies the security mode of the Subscriber.</span></span> <span data-ttu-id="09a90-284">值为 0 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，表示为  身份验证，值为 1，表示为 Windows 身份验证模式（默认）。</span><span class="sxs-lookup"><span data-stu-id="09a90-284">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, and a value of **1** indicates Windows Authentication Mode (default).</span></span>  
  
 <span data-ttu-id="09a90-285">**-SubscriberType** [ **0**| **1**| **3**]</span><span class="sxs-lookup"><span data-stu-id="09a90-285">**-SubscriberType** [ **0**| **1**| **3**]</span></span>  
 <span data-ttu-id="09a90-286">指定分发代理使用的订阅服务器连接类型。</span><span class="sxs-lookup"><span data-stu-id="09a90-286">Specifies the type of Subscriber connection used by the Distribution Agent.</span></span>  
  
|<span data-ttu-id="09a90-287">SubscriberType 值</span><span class="sxs-lookup"><span data-stu-id="09a90-287">SubscriberType value</span></span>|<span data-ttu-id="09a90-288">说明</span><span class="sxs-lookup"><span data-stu-id="09a90-288">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="09a90-289">**0**</span><span class="sxs-lookup"><span data-stu-id="09a90-289">**0**</span></span>|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="09a90-290">**1**</span><span class="sxs-lookup"><span data-stu-id="09a90-290">**1**</span></span>|<span data-ttu-id="09a90-291">ODBC 数据源</span><span class="sxs-lookup"><span data-stu-id="09a90-291">ODBC data source</span></span>|  
|<span data-ttu-id="09a90-292">**3**</span><span class="sxs-lookup"><span data-stu-id="09a90-292">**3**</span></span>|<span data-ttu-id="09a90-293">OLE DB 数据源</span><span class="sxs-lookup"><span data-stu-id="09a90-293">OLE DB data source</span></span>|  
  
 <span data-ttu-id="09a90-294">**-SubscriptionStreams** [**0**|**1**|**2**|...**64**]</span><span class="sxs-lookup"><span data-stu-id="09a90-294">**-SubscriptionStreams** [**0**|**1**|**2**|...**64**]</span></span>  
 <span data-ttu-id="09a90-295">每个分发代理允许的连接数，用于将成批更改并行应用于订阅服务器，同时保留在使用单线程时具有的多种事务特征。</span><span class="sxs-lookup"><span data-stu-id="09a90-295">Is the number of connections allowed per Distribution Agent to apply batches of changes in parallel to a Subscriber, while maintaining many of the transactional characteristics present when using a single thread.</span></span> <span data-ttu-id="09a90-296">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 对于  发布服务器，支持介于 1 到 64 之间的值。</span><span class="sxs-lookup"><span data-stu-id="09a90-296">For a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Publisher, a range of values from 1 to 64 is supported.</span></span> <span data-ttu-id="09a90-297">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 只有当发布服务器和分发服务器均在  或更高版本上运行时，才支持此参数。</span><span class="sxs-lookup"><span data-stu-id="09a90-297">This parameter is only supported when the Publisher and Distributor are running on [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later versions.</span></span> <span data-ttu-id="09a90-298">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 对于非  订阅服务器或对等订阅，不支持此参数或者参数必须为 0。</span><span class="sxs-lookup"><span data-stu-id="09a90-298">This parameter is not supported or must be 0 for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers or peer-to-peer subscriptions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09a90-299">如果有一个连接无法执行或提交，则所有连接将中止当前批处理，而且代理将用单独的流重试失败的批处理。</span><span class="sxs-lookup"><span data-stu-id="09a90-299">If one of the connections fails to execute or commit, all connections will abort the current batch, and the agent will use a single stream to retry the failed batches.</span></span> <span data-ttu-id="09a90-300">在重试阶段完成之前，订阅服务器上会存在临时事务不一致。</span><span class="sxs-lookup"><span data-stu-id="09a90-300">Before this retry phase completes, there can be temporary transactional inconsistencies at the Subscriber.</span></span> <span data-ttu-id="09a90-301">失败的批处理成功提交后，订阅服务器将恢复到事务一致状态。</span><span class="sxs-lookup"><span data-stu-id="09a90-301">After the failed batches are successfully committed, the Subscriber is brought back to a state of transactional consistency.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="09a90-302">将 **-SubscriptionStreams**的值指定为 2 或更大的数字时，订阅服务器接收事务的顺序可能与发布服务器提交事务的顺序不同。</span><span class="sxs-lookup"><span data-stu-id="09a90-302">When you specify a value of 2 or greater for **-SubscriptionStreams**, the order in which transactions are received at the Subscriber may differ from the order in which they were made at the Publisher.</span></span> <span data-ttu-id="09a90-303">如果此行为在同步期间导致约束冲突，则应使用 NOT FOR REPLICATION 选项禁止在同步期间强制执行约束。</span><span class="sxs-lookup"><span data-stu-id="09a90-303">If this behavior causes constraint violations during synchronization, you should use the NOT FOR REPLICATION option to disable the enforcement of constraints during synchronization.</span></span> <span data-ttu-id="09a90-304">有关详细信息，请参阅[控制同步期间触发器和约束的行为（复制 Transact-SQL 编程）](../control-behavior-of-triggers-and-constraints-in-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="09a90-304">For more information, see [Control the Behavior of Triggers and Constraints During Synchronization &#40;Replication Transact-SQL Programming&#41;](../control-behavior-of-triggers-and-constraints-in-synchronization.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09a90-305">[!INCLUDE[tsql](../../../includes/tsql-md.md)]订阅流不适用于配置为传递  的项目。</span><span class="sxs-lookup"><span data-stu-id="09a90-305">Subscriptionstreams do not work for articles configured to deliver [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="09a90-306">若要使用订阅流，请改将项目配置为传递存储过程调用。</span><span class="sxs-lookup"><span data-stu-id="09a90-306">To use subscriptionstreams, configure articles to deliver stored procedure calls instead.</span></span>  
  
 <span data-ttu-id="09a90-307">**-SubscriptionTableName** _subscription_table_</span><span class="sxs-lookup"><span data-stu-id="09a90-307">**-SubscriptionTableName** _subscription_table_</span></span>  
 <span data-ttu-id="09a90-308">在给定订阅服务器上生成或使用的订阅表的名称。</span><span class="sxs-lookup"><span data-stu-id="09a90-308">Is the name of the subscription table generated or used at the given Subscriber.</span></span> <span data-ttu-id="09a90-309">如果未指定，将使用 [MSreplication_subscriptions (Transact-SQL)](/sql/relational-databases/system-tables/msreplication-subscriptions-transact-sql) 表。</span><span class="sxs-lookup"><span data-stu-id="09a90-309">When not specified, the [MSreplication_subscriptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msreplication-subscriptions-transact-sql) table is used.</span></span> <span data-ttu-id="09a90-310">可将此选项用于不支持长文件名的数据库管理系统 (DBMS)。</span><span class="sxs-lookup"><span data-stu-id="09a90-310">Use this option for database management systems (DBMS) that do not support long file names.</span></span>  
  
 <span data-ttu-id="09a90-311">**-SubscriptionType** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="09a90-311">**-SubscriptionType** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="09a90-312">指定分发的订阅类型。</span><span class="sxs-lookup"><span data-stu-id="09a90-312">Specifies the subscription type for distribution.</span></span> <span data-ttu-id="09a90-313">值为 **0** ，表示推送订阅，值为 **1** ，表示请求订阅，值为 2，表示匿名订阅。</span><span class="sxs-lookup"><span data-stu-id="09a90-313">A value of **0** indicates a push subscription, a value of **1** indicates a pull subscription, and a value of **2** indicates an anonymous subscription.</span></span>  
  
 <span data-ttu-id="09a90-314">**-TransactionsPerHistory** [ **0**| **1**|...**10000**]</span><span class="sxs-lookup"><span data-stu-id="09a90-314">**-TransactionsPerHistory** [ **0**| **1**|... **10000**]</span></span>  
 <span data-ttu-id="09a90-315">指定历史日志记录的事务间隔。</span><span class="sxs-lookup"><span data-stu-id="09a90-315">Specifies the transaction interval for history logging.</span></span> <span data-ttu-id="09a90-316">如果自历史日志记录上一实例之后的已提交事务数大于此选项，将记录历史记录消息。</span><span class="sxs-lookup"><span data-stu-id="09a90-316">If the number of committed transactions after the last instance of history logging is greater than this option, a history message is logged.</span></span> <span data-ttu-id="09a90-317">默认值为 100。</span><span class="sxs-lookup"><span data-stu-id="09a90-317">The default is 100.</span></span> <span data-ttu-id="09a90-318">值 **0** 表示无限 **TransactionsPerHistory**。</span><span class="sxs-lookup"><span data-stu-id="09a90-318">A value of **0** indicates infinite **TransactionsPerHistory**.</span></span> <span data-ttu-id="09a90-319">请参阅**MessageInterval**参数。</span><span class="sxs-lookup"><span data-stu-id="09a90-319">See the preceding **-MessageInterval**parameter.</span></span>  
  
 <span data-ttu-id="09a90-320">**-UseDTS**</span><span class="sxs-lookup"><span data-stu-id="09a90-320">**-UseDTS**</span></span>  
 <span data-ttu-id="09a90-321">必须指定为允许数据转换的发布的参数。</span><span class="sxs-lookup"><span data-stu-id="09a90-321">Must be specified as a parameter for a publication that allows data transformation.</span></span>  
  
 <span data-ttu-id="09a90-322">**-UseInprocLoader**</span><span class="sxs-lookup"><span data-stu-id="09a90-322">**-UseInprocLoader**</span></span>  
 <span data-ttu-id="09a90-323">通过让分发代理在将快照文件应用于订阅服务器时使用 BULK INSERT 命令，提高初始快照的性能。</span><span class="sxs-lookup"><span data-stu-id="09a90-323">Improves the performance of the initial snapshot by causing the Distribution Agent to use the BULK INSERT command when applying snapshot files to the Subscriber.</span></span> <span data-ttu-id="09a90-324">不推荐使用此参数，因为它与 XML 数据类型不兼容。</span><span class="sxs-lookup"><span data-stu-id="09a90-324">This parameter is deprecated because it is not compatible with the XML data type.</span></span> <span data-ttu-id="09a90-325">如果不复制 XML 数据，则可以使用此参数。</span><span class="sxs-lookup"><span data-stu-id="09a90-325">If you are not replicating XML data, this parameter can be used.</span></span> <span data-ttu-id="09a90-326">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 此参数不可用于字符模式快照或非  订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="09a90-326">This parameter cannot be used with character mode snapshots or non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers.</span></span> <span data-ttu-id="09a90-327">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 如果使用此参数，订阅服务器上的  服务帐户必须具有快照 .bcp 数据文件所在目录的读取权限。</span><span class="sxs-lookup"><span data-stu-id="09a90-327">If you use this parameter, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account at the Subscriber must have read permissions on the directory where the snapshot .bcp data files are located.</span></span> <span data-ttu-id="09a90-328">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 如果不使用此参数，代理（对于非 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器）或代理加载的 ODBC 驱动程序（对于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器）从文件中读取数据，因此不使用  服务帐户的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="09a90-328">When this parameter is not used, the agent (for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers) or the ODBC driver loaded by the agent (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers) reads from the files, so the security context of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account is not used.</span></span>  
  
 <span data-ttu-id="09a90-329">**-UseOledbStreaming**</span><span class="sxs-lookup"><span data-stu-id="09a90-329">**-UseOledbStreaming**</span></span>  
 <span data-ttu-id="09a90-330">指定此参数时，可以将二进制大型对象数据作为流进行绑定。</span><span class="sxs-lookup"><span data-stu-id="09a90-330">When specified, enables the binding of binary large object data as a stream.</span></span> <span data-ttu-id="09a90-331">使用 **-OledbStreamThreshold** 指定大小（按字节计），超过此大小时将使用流。</span><span class="sxs-lookup"><span data-stu-id="09a90-331">Use **-OledbStreamThreshold** to specify the size, in bytes, above which a stream will be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09a90-332">备注</span><span class="sxs-lookup"><span data-stu-id="09a90-332">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="09a90-333">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 如果安装了  代理以在本地系统帐户而非域用户帐户（默认）下运行，则服务只能访问本地计算机。</span><span class="sxs-lookup"><span data-stu-id="09a90-333">If you have installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a local system account rather than under a domain user account (the default), the service can only access the local computer.</span></span> <span data-ttu-id="09a90-334">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 如果将以 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]代理身份运行的分发代理配置为在登录到  实例时使用 Windows 身份验证模式，则分发代理将失败。</span><span class="sxs-lookup"><span data-stu-id="09a90-334">If the Distribution Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Distribution Agent fails.</span></span> <span data-ttu-id="09a90-335">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认设置为  身份验证。</span><span class="sxs-lookup"><span data-stu-id="09a90-335">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="09a90-336">[View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md)有关更改安全帐户的详细信息，请参阅。</span><span class="sxs-lookup"><span data-stu-id="09a90-336">For information on changing security accounts, see [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="09a90-337">若要启动分发代理，请从命令提示符下执行 **distrib.exe** 。</span><span class="sxs-lookup"><span data-stu-id="09a90-337">To start the Distribution Agent, execute **distrib.exe** from the command prompt.</span></span> <span data-ttu-id="09a90-338">有关信息，请参阅[复制代理可执行文件概念](../concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="09a90-338">For information, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="change-history"></a><span data-ttu-id="09a90-339">更改历史记录</span><span class="sxs-lookup"><span data-stu-id="09a90-339">Change History</span></span>  
  
|<span data-ttu-id="09a90-340">更新的内容</span><span class="sxs-lookup"><span data-stu-id="09a90-340">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="09a90-341"> 添加了 -ExtendedEventConfigFile 参数。</span><span class="sxs-lookup"><span data-stu-id="09a90-341">Added the **-ExtendedEventConfigFile** parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09a90-342">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09a90-342">See Also</span></span>  
 [<span data-ttu-id="09a90-343">复制代理管理</span><span class="sxs-lookup"><span data-stu-id="09a90-343">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
