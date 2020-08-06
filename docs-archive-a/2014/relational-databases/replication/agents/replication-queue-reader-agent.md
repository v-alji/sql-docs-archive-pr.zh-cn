---
title: 复制队列读取器代理 | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], Queue Reader Agent
- command prompt [SQL Server replication]
- Queue Reader Agent, parameter reference
- Queue Reader Agent, executables
ms.assetid: 8e227793-11f6-47c6-99dc-ffc282f5d4bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 854c425db3fbaa346dab5eb2c41bd58cf03f65c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578148"
---
# <a name="replication-queue-reader-agent"></a><span data-ttu-id="cd50a-102">复制队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="cd50a-102">Replication Queue Reader Agent</span></span>
  <span data-ttu-id="cd50a-103">复制队列读取器代理是一个可执行文件，该文件读取存储在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 队列或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 消息队列中的消息，然后将这些消息应用于发布服务器。</span><span class="sxs-lookup"><span data-stu-id="cd50a-103">The Replication Queue Reader Agent is an executable that reads messages stored in a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] queue or a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Message Queue and then applies those messages to the Publisher.</span></span> <span data-ttu-id="cd50a-104">队列读取器代理与允许排队更新的快照发布和事务发布一起使用。</span><span class="sxs-lookup"><span data-stu-id="cd50a-104">Queue Reader Agent is used with snapshot and transactional publications that allow queued updating.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd50a-105">可以按任意顺序指定参数。</span><span class="sxs-lookup"><span data-stu-id="cd50a-105">Parameters can be specified in any order.</span></span> <span data-ttu-id="cd50a-106">如果没有指定可选参数，会使用基于默认代理配置文件的预定义值。</span><span class="sxs-lookup"><span data-stu-id="cd50a-106">When optional parameters are not specified, predefined values based on the default agent profile are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd50a-107">语法</span><span class="sxs-lookup"><span data-stu-id="cd50a-107">Syntax</span></span>  
  
```  
  
      qrdrsvc [-?]  
[-Continuous]  
[-DefinitionFiledefinition_file]  
[-Distributorserver_name[\instance_name]]  
[-DistributionDBdistribution_database]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-LoginTimeOutlogin_time_out_seconds]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PollingIntervalpolling_interval]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-ProfileNameagent_profile_name]  
[-QueryTimeOutquery_time_out_seconds]  
[-ResolverState [1|2|3]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="cd50a-108">参数</span><span class="sxs-lookup"><span data-stu-id="cd50a-108">Arguments</span></span>  
 <span data-ttu-id="cd50a-109">**-?**</span><span class="sxs-lookup"><span data-stu-id="cd50a-109">**-?**</span></span>  
 <span data-ttu-id="cd50a-110">显示用法信息。</span><span class="sxs-lookup"><span data-stu-id="cd50a-110">Displays usage information.</span></span>  
  
 <span data-ttu-id="cd50a-111">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="cd50a-111">**-Continuous**</span></span>  
 <span data-ttu-id="cd50a-112">指定代理是否尝试连续处理排队的事务。</span><span class="sxs-lookup"><span data-stu-id="cd50a-112">Specifies whether the agent attempts to process queued transactions continuously.</span></span> <span data-ttu-id="cd50a-113">如果指定此参数，即使任何订阅方都没有挂起的排队事务，代理仍然会连续执行。</span><span class="sxs-lookup"><span data-stu-id="cd50a-113">If specified, the agent continues execution even if there are no queued transactions pending from any of the subscribers.</span></span>  
  
 <span data-ttu-id="cd50a-114">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="cd50a-114">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="cd50a-115">代理定义文件的路径。</span><span class="sxs-lookup"><span data-stu-id="cd50a-115">Is the path of the agent definition file.</span></span> <span data-ttu-id="cd50a-116">代理定义文件中包含代理的命令提示符参数。</span><span class="sxs-lookup"><span data-stu-id="cd50a-116">An agent definition file contains command-line arguments for the agent.</span></span> <span data-ttu-id="cd50a-117">文件的内容被当作可执行文件进行分析。</span><span class="sxs-lookup"><span data-stu-id="cd50a-117">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="cd50a-118">使用双引号 (") 指定包含任意字符的参数值。</span><span class="sxs-lookup"><span data-stu-id="cd50a-118">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="cd50a-119">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="cd50a-119">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="cd50a-120">分发服务器名称。</span><span class="sxs-lookup"><span data-stu-id="cd50a-120">Is the Distributor name.</span></span> <span data-ttu-id="cd50a-121">为该服务器上的 *默认实例指定* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cd50a-121">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="cd50a-122">为该服务器上的 *server_name*\\*instance_name* instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cd50a-122">Specify *server_name*\\*instance_name* for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="cd50a-123">如果未指定，则名称默认为本地计算机上 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的默认实例的名称。</span><span class="sxs-lookup"><span data-stu-id="cd50a-123">If not specified, the name defaults to the name of the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="cd50a-124">**-DistributionDB** _distribution_database_</span><span class="sxs-lookup"><span data-stu-id="cd50a-124">**-DistributionDB** _distribution_database_</span></span>  
 <span data-ttu-id="cd50a-125">分发数据库。</span><span class="sxs-lookup"><span data-stu-id="cd50a-125">Is the distribution database.</span></span>  
  
 <span data-ttu-id="cd50a-126">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="cd50a-126">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="cd50a-127">分发服务器登录名。</span><span class="sxs-lookup"><span data-stu-id="cd50a-127">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="cd50a-128">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="cd50a-128">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="cd50a-129">分发服务器密码。</span><span class="sxs-lookup"><span data-stu-id="cd50a-129">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="cd50a-130">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="cd50a-130">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="cd50a-131">指定分发服务器的安全模式。</span><span class="sxs-lookup"><span data-stu-id="cd50a-131">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="cd50a-132">值 **0** 指示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证模式（默认设置），值 **1** 指示 Windows 身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="cd50a-132">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="cd50a-133">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="cd50a-133">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="cd50a-134">队列读取器代理建立连接时使用的安全套接字层 (SSL) 加密级别。</span><span class="sxs-lookup"><span data-stu-id="cd50a-134">Is the level of Secure Sockets Layer (SSL) encryption used by the Queue Reader Agent when making connections.</span></span>  
  
|<span data-ttu-id="cd50a-135">EncryptionLevel 值</span><span class="sxs-lookup"><span data-stu-id="cd50a-135">EncryptionLevel value</span></span>|<span data-ttu-id="cd50a-136">说明</span><span class="sxs-lookup"><span data-stu-id="cd50a-136">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="cd50a-137">**0**</span><span class="sxs-lookup"><span data-stu-id="cd50a-137">**0**</span></span>|<span data-ttu-id="cd50a-138">指定不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="cd50a-138">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="cd50a-139">**1**</span><span class="sxs-lookup"><span data-stu-id="cd50a-139">**1**</span></span>|<span data-ttu-id="cd50a-140">指定使用 SSL，但是代理不验证 SSL 服务器证书是否已由可信的颁发者进行签名。</span><span class="sxs-lookup"><span data-stu-id="cd50a-140">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="cd50a-141">**2**</span><span class="sxs-lookup"><span data-stu-id="cd50a-141">**2**</span></span>|<span data-ttu-id="cd50a-142">指定使用 SSL，并验证证书。</span><span class="sxs-lookup"><span data-stu-id="cd50a-142">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="cd50a-143">使用 SQL Server 的完全限定的域名定义有效的 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="cd50a-143">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="cd50a-144">为了在将 -EncryptionLevel 设置为 2 时成功连接代理，请在本地 SQL Server 上创建别名。</span><span class="sxs-lookup"><span data-stu-id="cd50a-144">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="cd50a-145">“Alias Name”参数应为服务器名称，”Server”参数应设置为 SQL Server 的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="cd50a-145">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
  
 <span data-ttu-id="cd50a-146">有关详细信息，请参阅[SQL Server 复制安全性](../security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="cd50a-146">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="cd50a-147">**-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="cd50a-147">**-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="cd50a-148">指定队列读取器运行期间记录的历史记录数量。</span><span class="sxs-lookup"><span data-stu-id="cd50a-148">Specifies the amount of history logged during a queue reader operation.</span></span> <span data-ttu-id="cd50a-149">选择 **1**可将历史日志记录对性能的影响减至最小。</span><span class="sxs-lookup"><span data-stu-id="cd50a-149">You can minimize the effect of history logging on performance by selecting **1**.</span></span>  
  
|<span data-ttu-id="cd50a-150">HistoryVerboseLevel 值</span><span class="sxs-lookup"><span data-stu-id="cd50a-150">HistoryVerboseLevel value</span></span>|<span data-ttu-id="cd50a-151">说明</span><span class="sxs-lookup"><span data-stu-id="cd50a-151">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="cd50a-152">**0**</span><span class="sxs-lookup"><span data-stu-id="cd50a-152">**0**</span></span>|<span data-ttu-id="cd50a-153">不记录历史记录（不推荐）。</span><span class="sxs-lookup"><span data-stu-id="cd50a-153">No history logging (not recommended).</span></span>|  
|<span data-ttu-id="cd50a-154">**1**</span><span class="sxs-lookup"><span data-stu-id="cd50a-154">**1**</span></span>|<span data-ttu-id="cd50a-155">默认。</span><span class="sxs-lookup"><span data-stu-id="cd50a-155">Default.</span></span> <span data-ttu-id="cd50a-156">总是更新具有相同状态（启动、进行中、成功等）的上一历史记录消息。</span><span class="sxs-lookup"><span data-stu-id="cd50a-156">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="cd50a-157">如果不存在状态相同的上一记录，将插入新记录。</span><span class="sxs-lookup"><span data-stu-id="cd50a-157">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="cd50a-158">**2**</span><span class="sxs-lookup"><span data-stu-id="cd50a-158">**2**</span></span>|<span data-ttu-id="cd50a-159">插入新的历史记录，包括空闲消息或长时间运行作业的消息。</span><span class="sxs-lookup"><span data-stu-id="cd50a-159">Insert new history records, including idle messages or long-running job messages.</span></span>|  
|<span data-ttu-id="cd50a-160">**3**</span><span class="sxs-lookup"><span data-stu-id="cd50a-160">**3**</span></span>|<span data-ttu-id="cd50a-161">插入包括了可能对排除故障有用的其他详细信息的新历史记录。</span><span class="sxs-lookup"><span data-stu-id="cd50a-161">Insert new history records that include additional details that may be useful for troubleshooting.</span></span>|  
  
 <span data-ttu-id="cd50a-162">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="cd50a-162">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="cd50a-163">登录超时前等待的秒数。默认值为 15 秒。</span><span class="sxs-lookup"><span data-stu-id="cd50a-163">Is the number of seconds before the login times out. The default is 15 seconds.</span></span>  
  
 <span data-ttu-id="cd50a-164">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="cd50a-164">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="cd50a-165">代理输出文件的路径。</span><span class="sxs-lookup"><span data-stu-id="cd50a-165">Is the path of the agent output file.</span></span> <span data-ttu-id="cd50a-166">如果未提供文件名，则向控制台发送该输出。</span><span class="sxs-lookup"><span data-stu-id="cd50a-166">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="cd50a-167">如果指定的文件名已存在，会将输出追加到该文件。</span><span class="sxs-lookup"><span data-stu-id="cd50a-167">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="cd50a-168">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="cd50a-168">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="cd50a-169">指定输出是否应提供详细内容。</span><span class="sxs-lookup"><span data-stu-id="cd50a-169">Specifies whether the output should be verbose.</span></span> <span data-ttu-id="cd50a-170">如果详细级别为 0，则只输出错误消息。</span><span class="sxs-lookup"><span data-stu-id="cd50a-170">If the verbose level is **0**, only error messages are printed.</span></span> <span data-ttu-id="cd50a-171">如果详细级别为 1，则输出所有进度报告消息。</span><span class="sxs-lookup"><span data-stu-id="cd50a-171">If the verbose level is **1**, all the progress report messages are printed.</span></span> <span data-ttu-id="cd50a-172">如果详细级别为 2（默认），则输出所有错误消息和进度消息，这对调试很有帮助。</span><span class="sxs-lookup"><span data-stu-id="cd50a-172">If the verbose level is **2** (default), all error messages and progress report messages are printed, which is useful for debugging.</span></span>  
  
 <span data-ttu-id="cd50a-173">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="cd50a-173">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="cd50a-174">仅与使用基于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的队列的更新订阅有关。</span><span class="sxs-lookup"><span data-stu-id="cd50a-174">Is relevant only for updating subscriptions that use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] based queues.</span></span> <span data-ttu-id="cd50a-175">指定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 队列接受对挂起的排队事务的轮询的频率（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="cd50a-175">Specifies how often, in seconds, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] queue is polled for pending queued transactions.</span></span> <span data-ttu-id="cd50a-176">该值可介于 0 和 240 秒之间。</span><span class="sxs-lookup"><span data-stu-id="cd50a-176">The value can be between 0 and 240 seconds.</span></span> <span data-ttu-id="cd50a-177">默认值为 5 秒。</span><span class="sxs-lookup"><span data-stu-id="cd50a-177">The default is 5 seconds.</span></span>  
  
 <span data-ttu-id="cd50a-178">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="cd50a-178">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="cd50a-179">指定参加与发布数据库进行的数据库镜像会话的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移伙伴实例。</span><span class="sxs-lookup"><span data-stu-id="cd50a-179">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="cd50a-180">有关详细信息，请参阅 [数据库镜像和复制 (SQL Server)](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="cd50a-180">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="cd50a-181">**-ProfileName** _agent_profile_name_</span><span class="sxs-lookup"><span data-stu-id="cd50a-181">**-ProfileName** _agent_profile_name_</span></span>  
 <span data-ttu-id="cd50a-182">用于向代理提供一组默认值的代理配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="cd50a-182">Is the name of an agent profile used to supply a set of default values to the agent.</span></span> <span data-ttu-id="cd50a-183">有关信息，请参阅[复制代理配置文件](replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="cd50a-183">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="cd50a-184">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="cd50a-184">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="cd50a-185">查询超时前等待的秒数。默认值为 1800 秒。</span><span class="sxs-lookup"><span data-stu-id="cd50a-185">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="cd50a-186">**-ResolverState** [ **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="cd50a-186">**-ResolverState** [ **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="cd50a-187">指定解决排队更新冲突的方式。</span><span class="sxs-lookup"><span data-stu-id="cd50a-187">Specifies how queued updating conflicts are resolved.</span></span> <span data-ttu-id="cd50a-188">值为 **1** ，表示发布服务器赢得冲突且当前发生冲突的排队事务将在发布服务器和发起更新的订阅服务器上回滚，后续排队事务的处理过程将继续进行。</span><span class="sxs-lookup"><span data-stu-id="cd50a-188">A value of **1** indicates the Publisher wins the conflict, and the current conflicting queued transaction will be rolled back on the Publisher and the originating updating Subscriber; the processing of subsequent queued transactions will continue.</span></span> <span data-ttu-id="cd50a-189">值为 **2** 表示订阅服务器赢得冲突且排队事务将覆盖发布服务器上的值。</span><span class="sxs-lookup"><span data-stu-id="cd50a-189">A value of **2** indicates the Subscriber wins the conflict, and the queued transaction will override the values on the Publisher.</span></span> <span data-ttu-id="cd50a-190">值为 **3** 表示任何冲突都将导致订阅服务器重新初始化；发布服务器赢得冲突，后续排队事务的处理过程将终止且订阅将重新初始化。</span><span class="sxs-lookup"><span data-stu-id="cd50a-190">A value of **3** indicates that any conflict will result in Subscriber re-initialization; the Publisher wins the conflict, processing of subsequent queued transactions will be terminated, and the subscription will be reinitialized.</span></span> <span data-ttu-id="cd50a-191">事务发布的默认设置为 **1** ，快照发布的默认设置为 **3** 。</span><span class="sxs-lookup"><span data-stu-id="cd50a-191">The default setting is **1** for transactional publications and **3** for snapshot publications.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd50a-192">备注</span><span class="sxs-lookup"><span data-stu-id="cd50a-192">Remarks</span></span>  
 <span data-ttu-id="cd50a-193">若要启动队列读取器代理，请从命令提示符下执行 **qrdrsvc.exe** 。</span><span class="sxs-lookup"><span data-stu-id="cd50a-193">To start the Queue Reader Agent, execute **qrdrsvc.exe** from the command prompt.</span></span> <span data-ttu-id="cd50a-194">有关信息，请参阅 [复制代理可执行文件](../concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="cd50a-194">For information, see [Replication Agent Executables](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd50a-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd50a-195">See Also</span></span>  
 [<span data-ttu-id="cd50a-196">复制代理管理</span><span class="sxs-lookup"><span data-stu-id="cd50a-196">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
