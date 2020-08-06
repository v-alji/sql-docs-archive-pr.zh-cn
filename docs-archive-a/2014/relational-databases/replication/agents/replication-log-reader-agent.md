---
title: 复制日志读取器代理 | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Log Reader Agent, executables
- Log Reader Agent, parameter reference
- agents [SQL Server replication], Log Reader Agent
- command prompt [SQL Server replication]
ms.assetid: 5487b645-d99b-454c-8bd2-aff470709a0e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 120c7418d8b16fe6d083961affcf0b8a9c9f6c65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586619"
---
# <a name="replication-log-reader-agent"></a><span data-ttu-id="99087-102">复制日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="99087-102">Replication Log Reader Agent</span></span>
  <span data-ttu-id="99087-103">复制日志读取器代理是一个可执行文件，用于监视为事务复制配置的每个数据库的事务日志，以及将标记为进行复制的事务从事务日志复制到分发数据库中。</span><span class="sxs-lookup"><span data-stu-id="99087-103">The Replication Log Reader Agent is an executable that monitors the transaction log of each database configured for transactional replication and copies the transactions marked for replication from the transaction log into the distribution database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="99087-104">可以按任意顺序指定参数。</span><span class="sxs-lookup"><span data-stu-id="99087-104">Parameters can be specified in any order.</span></span> <span data-ttu-id="99087-105">如果没有指定可选参数，会使用基于默认代理配置文件的预定义值。</span><span class="sxs-lookup"><span data-stu-id="99087-105">When optional parameters are not specified, predefined values based on the default agent profile are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99087-106">语法</span><span class="sxs-lookup"><span data-stu-id="99087-106">Syntax</span></span>  
  
```  
  
      logread [-?]   
-Publisherserver_name[\instance_name]   
-PublisherDBpublisher_database   
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributorserver_name[\instance_name]]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-ExtendedEventConfigFileconfiguration_path_and_file_name]  
[-HistoryVerboseLevel [0|1|2]]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-LogScanThresholdscan_threshold]  
[-MaxCmdsInTrannumber_of_commands]  
[-MessageIntervalmessage_interval]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2|3|4]]  
[-PacketSizepacket_size]  
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]   
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherSecurityMode [0|1]]  
[-PublisherLoginpublisher_login]  
[-PublisherPasswordpublisher_password]   
[-QueryTimeOutquery_time_out_seconds]  
[-ReadBatchSizenumber_of_transactions]   
[-ReadBatchThresholdread_batch_threshold]  
[-RecoverFromDataErrors]  
```  
  
## <a name="arguments"></a><span data-ttu-id="99087-107">参数</span><span class="sxs-lookup"><span data-stu-id="99087-107">Arguments</span></span>  
 <span data-ttu-id="99087-108">**-?**</span><span class="sxs-lookup"><span data-stu-id="99087-108">**-?**</span></span>  
 <span data-ttu-id="99087-109">显示用法信息。</span><span class="sxs-lookup"><span data-stu-id="99087-109">Displays usage information.</span></span>  
  
 <span data-ttu-id="99087-110">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="99087-110">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="99087-111">发布服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="99087-111">Is the name of the Publisher.</span></span> <span data-ttu-id="99087-112">为该服务器上的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认实例指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="99087-112">Specify *server_name* for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="99087-113">为该服务器上的 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认实例指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="99087-113">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="99087-114">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="99087-114">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="99087-115">发布服务器数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="99087-115">Is the name of the Publisher database.</span></span>  
  
 <span data-ttu-id="99087-116">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="99087-116">**-Continuous**</span></span>  
 <span data-ttu-id="99087-117">指定代理是否尝试持续轮询所复制的事务。</span><span class="sxs-lookup"><span data-stu-id="99087-117">Specifies whether the agent tries to poll replicated transactions continually.</span></span> <span data-ttu-id="99087-118">如果指定了该参数，即使没有事务挂起，代理轮询也将在轮询间隔期间轮询来自源的已复制事务。</span><span class="sxs-lookup"><span data-stu-id="99087-118">If specified, the agent polls replicated transactions from the source at polling intervals even if there are no transactions pending.</span></span>  
  
 <span data-ttu-id="99087-119">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="99087-119">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="99087-120">代理定义文件的路径。</span><span class="sxs-lookup"><span data-stu-id="99087-120">Is the path of the agent definition file.</span></span> <span data-ttu-id="99087-121">代理定义文件中包含代理的命令提示符参数。</span><span class="sxs-lookup"><span data-stu-id="99087-121">An agent definition file contains command-line arguments for the agent.</span></span> <span data-ttu-id="99087-122">文件的内容被当作可执行文件进行分析。</span><span class="sxs-lookup"><span data-stu-id="99087-122">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="99087-123">使用双引号 (") 指定包含任意字符的参数值。</span><span class="sxs-lookup"><span data-stu-id="99087-123">Use double quotation marks (") to specify argument values that contain arbitrary characters.</span></span>  
  
 <span data-ttu-id="99087-124">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="99087-124">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="99087-125">分发服务器名称。</span><span class="sxs-lookup"><span data-stu-id="99087-125">Is the Distributor name.</span></span> <span data-ttu-id="99087-126">为该服务器上的 *默认实例指定* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="99087-126">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="99087-127">为该服务器上的 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认实例指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="99087-127">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="99087-128">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="99087-128">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="99087-129">分发服务器登录名。</span><span class="sxs-lookup"><span data-stu-id="99087-129">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="99087-130">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="99087-130">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="99087-131">分发服务器密码。</span><span class="sxs-lookup"><span data-stu-id="99087-131">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="99087-132">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="99087-132">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="99087-133">指定分发服务器的安全模式。</span><span class="sxs-lookup"><span data-stu-id="99087-133">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="99087-134">值为 **0** ，表示为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证模式（默认值），值为 **1** ，表示为 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="99087-134">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="99087-135">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="99087-135">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="99087-136">日志读取器代理建立连接时使用的安全套接字层 (SSL) 加密级别。</span><span class="sxs-lookup"><span data-stu-id="99087-136">Is the level of Secure Sockets Layer (SSL) encryption that is used by the Log Reader Agent when making connections.</span></span>  
  
|<span data-ttu-id="99087-137">EncryptionLevel 值</span><span class="sxs-lookup"><span data-stu-id="99087-137">EncryptionLevel value</span></span>|<span data-ttu-id="99087-138">说明</span><span class="sxs-lookup"><span data-stu-id="99087-138">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="99087-139">**0**</span><span class="sxs-lookup"><span data-stu-id="99087-139">**0**</span></span>|<span data-ttu-id="99087-140">指定不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="99087-140">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="99087-141">**1**</span><span class="sxs-lookup"><span data-stu-id="99087-141">**1**</span></span>|<span data-ttu-id="99087-142">指定使用 SSL，但是代理不验证 SSL 服务器证书是否已由可信的颁发者进行签名。</span><span class="sxs-lookup"><span data-stu-id="99087-142">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="99087-143">**2**</span><span class="sxs-lookup"><span data-stu-id="99087-143">**2**</span></span>|<span data-ttu-id="99087-144">指定使用 SSL，并验证证书。</span><span class="sxs-lookup"><span data-stu-id="99087-144">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="99087-145">使用 SQL Server 的完全限定的域名定义有效的 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="99087-145">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="99087-146">为了在将 -EncryptionLevel 设置为 2 时成功连接代理，请在本地 SQL Server 上创建别名。</span><span class="sxs-lookup"><span data-stu-id="99087-146">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="99087-147">“Alias Name”参数应为服务器名称，”Server”参数应设置为 SQL Server 的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="99087-147">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
 
 <span data-ttu-id="99087-148">有关详细信息，请参阅[SQL Server 复制安全性](../security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="99087-148">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="99087-149">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="99087-149">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span></span>  
 <span data-ttu-id="99087-150">为扩展事件 XML 配置文件指定路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="99087-150">Specifies the path and file name for the extended events XML configuration file.</span></span> <span data-ttu-id="99087-151">通过该扩展事件 XML 配置文件，您可以配置会话并且启用事件跟踪。</span><span class="sxs-lookup"><span data-stu-id="99087-151">The extended events configuration file allows you to configure sessions and enable events for tracking.</span></span>  
  
 <span data-ttu-id="99087-152">**-HistoryVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="99087-152">**-HistoryVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="99087-153">指定在日志读取器运行期间记录的历史记录数量。</span><span class="sxs-lookup"><span data-stu-id="99087-153">Specifies the amount of history logged during a log reader operation.</span></span> <span data-ttu-id="99087-154">选择 1 可将历史日志记录对性能的影响减小到最低限度。</span><span class="sxs-lookup"><span data-stu-id="99087-154">You can minimize the performance effect of history logging by selecting **1**.</span></span>  
  
|<span data-ttu-id="99087-155">HistoryVerboseLevel 值</span><span class="sxs-lookup"><span data-stu-id="99087-155">HistoryVerboseLevel value</span></span>|<span data-ttu-id="99087-156">说明</span><span class="sxs-lookup"><span data-stu-id="99087-156">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="99087-157">**0**</span><span class="sxs-lookup"><span data-stu-id="99087-157">**0**</span></span>||  
|<span data-ttu-id="99087-158">**1**</span><span class="sxs-lookup"><span data-stu-id="99087-158">**1**</span></span>|<span data-ttu-id="99087-159">默认。</span><span class="sxs-lookup"><span data-stu-id="99087-159">Default.</span></span> <span data-ttu-id="99087-160">总是更新具有相同状态（启动、进行中、成功等）的上一历史记录消息。</span><span class="sxs-lookup"><span data-stu-id="99087-160">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="99087-161">如果不存在状态相同的上一记录，将插入新记录。</span><span class="sxs-lookup"><span data-stu-id="99087-161">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="99087-162">**2**</span><span class="sxs-lookup"><span data-stu-id="99087-162">**2**</span></span>|<span data-ttu-id="99087-163">除非记录为空闲消息或长时间运行的作业消息等信息（此时将更新上一记录），否则插入新的历史记录。</span><span class="sxs-lookup"><span data-stu-id="99087-163">Insert new history records unless the record is for such things as idle messages or long-running job messages, in which case update the previous records.</span></span>|  
  
 <span data-ttu-id="99087-164">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="99087-164">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span></span>  
 <span data-ttu-id="99087-165">在历史记录线程检查目前是否有连接在等待服务器响应之前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="99087-165">Is the number of seconds before the history thread checks if any of the existing connections is waiting for a response from the server.</span></span> <span data-ttu-id="99087-166">在执行长时间运行的批处理时，减小该值可避免检查代理将日志读取器代理标记为可疑。</span><span class="sxs-lookup"><span data-stu-id="99087-166">This value can be decreased to avoid having the checkup agent mark the Log Reader Agent as suspect when executing a long-running batch.</span></span> <span data-ttu-id="99087-167">默认值为 300 秒。</span><span class="sxs-lookup"><span data-stu-id="99087-167">The default is 300 seconds.</span></span>  
  
 <span data-ttu-id="99087-168">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="99087-168">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="99087-169">登录超时前等待的秒数。默认值为 15 秒。</span><span class="sxs-lookup"><span data-stu-id="99087-169">Is the number of seconds before the login times out. The default is 15 seconds.</span></span>  
  
 <span data-ttu-id="99087-170">**-LogScanThreshold** _scan_threshold_</span><span class="sxs-lookup"><span data-stu-id="99087-170">**-LogScanThreshold** _scan_threshold_</span></span>  
 <span data-ttu-id="99087-171">仅限内部使用。</span><span class="sxs-lookup"><span data-stu-id="99087-171">Internal use only.</span></span>  
  
 <span data-ttu-id="99087-172">**-MaxCmdsInTran** _number_of_commands_</span><span class="sxs-lookup"><span data-stu-id="99087-172">**-MaxCmdsInTran** _number_of_commands_</span></span>  
 <span data-ttu-id="99087-173">指定在日志读取器将命令写入到分发数据库时可分组到一个事务中的语句的最大数目。</span><span class="sxs-lookup"><span data-stu-id="99087-173">Specifies the maximum number of statements grouped into a transaction as the Log Reader writes commands to the distribution database.</span></span> <span data-ttu-id="99087-174">如果使用此参数，在发布服务器上的大事务（包含许多命令）应用于订阅服务器时，日志读取器代理和分发代理可将这些大事务拆分为若干个较小的事务。</span><span class="sxs-lookup"><span data-stu-id="99087-174">Using this parameter allows the Log Reader Agent and Distribution Agent to divide large transactions (consisting of many commands) at the Publisher into several smaller transactions when applied at the Subscriber.</span></span> <span data-ttu-id="99087-175">指定此参数可以减少分发服务器的争用问题并缩短发布服务器与订阅服务器之间的滞后时间。</span><span class="sxs-lookup"><span data-stu-id="99087-175">Specifying this parameter can reduce contention at the Distributor and reduce latency between the Publisher and Subscriber.</span></span> <span data-ttu-id="99087-176">由于初始事务是以较小的单元应用的，订阅服务器可以在初始事务结束之前访问一个较大的逻辑发布服务器事务的行，因而会破坏事务的原子性。</span><span class="sxs-lookup"><span data-stu-id="99087-176">Because the original transaction is applied in smaller units, the Subscriber can access rows of a large logical Publisher transaction prior to the end of the original transaction, breaking strict transactional atomicity.</span></span> <span data-ttu-id="99087-177">默认值为 0 ，这将保持发布服务器的事务边界。</span><span class="sxs-lookup"><span data-stu-id="99087-177">The default is **0**, which preserves the transaction boundaries of the Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="99087-178">对于非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 发布，会忽略此参数。</span><span class="sxs-lookup"><span data-stu-id="99087-178">This parameter is ignored for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] publications.</span></span> <span data-ttu-id="99087-179">有关详细信息，请参阅 [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md)的“配置事务集作业”部分。</span><span class="sxs-lookup"><span data-stu-id="99087-179">For more information, see the section "Configuring the Transaction Set Job" in [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md).</span></span>  
  
 <span data-ttu-id="99087-180">**-MessageInterval** _message_interval_</span><span class="sxs-lookup"><span data-stu-id="99087-180">**-MessageInterval** _message_interval_</span></span>  
 <span data-ttu-id="99087-181">用于历史日志记录的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="99087-181">Is the time interval used for history logging.</span></span> <span data-ttu-id="99087-182">记录完上一个历史事件后，如达到 **MessageInterval** 值，会开始记录新的历史事件。</span><span class="sxs-lookup"><span data-stu-id="99087-182">A history event is logged when the **MessageInterval** value is reached after the last history event is logged.</span></span>  
  
 <span data-ttu-id="99087-183">如果源上没有可用的已复制事务，代理将向分发服务器报告无事务消息。</span><span class="sxs-lookup"><span data-stu-id="99087-183">If there is no replicated transaction available at the source, the agent reports a no-transaction message to the Distributor.</span></span> <span data-ttu-id="99087-184">此选项可指定代理在报告另一条无事务消息前将等待多长时间。</span><span class="sxs-lookup"><span data-stu-id="99087-184">This option specifies how long the agent waits before reporting another no-transaction message.</span></span> <span data-ttu-id="99087-185">在上次处理已复制事务后，如果代理在源上没有检测到任何可用的事务，则总是会报告一条无事务消息。</span><span class="sxs-lookup"><span data-stu-id="99087-185">Agents always report a no-transaction message when they detect that there are no transactions available at the source after previously processing replicated transactions.</span></span> <span data-ttu-id="99087-186">默认值为 60 秒。</span><span class="sxs-lookup"><span data-stu-id="99087-186">The default is 60 seconds.</span></span>  
  
 <span data-ttu-id="99087-187">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="99087-187">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="99087-188">代理输出文件的路径。</span><span class="sxs-lookup"><span data-stu-id="99087-188">Is the path of the agent output file.</span></span> <span data-ttu-id="99087-189">如果未提供文件名，则向控制台发送该输出。</span><span class="sxs-lookup"><span data-stu-id="99087-189">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="99087-190">如果指定的文件名已存在，会将输出追加到该文件。</span><span class="sxs-lookup"><span data-stu-id="99087-190">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="99087-191">**-OutputVerboseLevel** [ **0**| **1**| **2** | **3** | **4** ]</span><span class="sxs-lookup"><span data-stu-id="99087-191">**-OutputVerboseLevel** [ **0**| **1**| **2** | **3** | **4** ]</span></span>  
 <span data-ttu-id="99087-192">指定输出是否应提供详细内容。</span><span class="sxs-lookup"><span data-stu-id="99087-192">Specifies whether the output should be verbose.</span></span>  
  
|<span data-ttu-id="99087-193">值</span><span class="sxs-lookup"><span data-stu-id="99087-193">Value</span></span>|<span data-ttu-id="99087-194">说明</span><span class="sxs-lookup"><span data-stu-id="99087-194">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="99087-195">**0**</span><span class="sxs-lookup"><span data-stu-id="99087-195">**0**</span></span>|<span data-ttu-id="99087-196">仅输出错误消息。</span><span class="sxs-lookup"><span data-stu-id="99087-196">Only error messages are printed.</span></span>|  
|<span data-ttu-id="99087-197">**1**</span><span class="sxs-lookup"><span data-stu-id="99087-197">**1**</span></span>|<span data-ttu-id="99087-198">输出所有代理进度报告消息。</span><span class="sxs-lookup"><span data-stu-id="99087-198">All agent progress report messages are printed.</span></span>|  
|<span data-ttu-id="99087-199">**2** （默认值）</span><span class="sxs-lookup"><span data-stu-id="99087-199">**2** (default)</span></span>|<span data-ttu-id="99087-200">输出所有错误消息和代理进度报告消息。</span><span class="sxs-lookup"><span data-stu-id="99087-200">All error messages and agent progress report messages are printed.</span></span>|  
|<span data-ttu-id="99087-201">**3**</span><span class="sxs-lookup"><span data-stu-id="99087-201">**3**</span></span>|<span data-ttu-id="99087-202">输出每个复制的命令的前 100 个字节。</span><span class="sxs-lookup"><span data-stu-id="99087-202">The first 100 bytes of each replicated command are printed.</span></span>|  
|<span data-ttu-id="99087-203">**4**</span><span class="sxs-lookup"><span data-stu-id="99087-203">**4**</span></span>|<span data-ttu-id="99087-204">输出所有复制的命令。</span><span class="sxs-lookup"><span data-stu-id="99087-204">All replicated commands are printed.</span></span>|  
  
 <span data-ttu-id="99087-205">进行调试时，值 2-4 颇为有用。</span><span class="sxs-lookup"><span data-stu-id="99087-205">Values 2-4 are useful when debugging.</span></span>  
  
 <span data-ttu-id="99087-206">**-PacketSize** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="99087-206">**-PacketSize** _packet_size_</span></span>  
 <span data-ttu-id="99087-207">数据包大小（按字节计）。</span><span class="sxs-lookup"><span data-stu-id="99087-207">Is the packet size, in bytes.</span></span> <span data-ttu-id="99087-208">默认值为 4096（字节）。</span><span class="sxs-lookup"><span data-stu-id="99087-208">The default is 4096 (bytes).</span></span>  
  
 <span data-ttu-id="99087-209">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="99087-209">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="99087-210">对日志进行已复制事务查询的频率（以秒计）。</span><span class="sxs-lookup"><span data-stu-id="99087-210">Is how often, in seconds, the log is queried for replicated transactions.</span></span> <span data-ttu-id="99087-211">默认值为 5 秒。</span><span class="sxs-lookup"><span data-stu-id="99087-211">The default is 5 seconds.</span></span>  
  
 <span data-ttu-id="99087-212">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="99087-212">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="99087-213">指定用于代理参数的代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="99087-213">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="99087-214">如果 **ProfileName** 为 NULL，则将禁用代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="99087-214">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="99087-215">如果未指定 **ProfileName** ，则使用该代理类型的默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="99087-215">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="99087-216">有关信息，请参阅[复制代理配置文件](replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="99087-216">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="99087-217">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="99087-217">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="99087-218">指定参加与发布数据库进行的数据库镜像会话的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移伙伴实例。</span><span class="sxs-lookup"><span data-stu-id="99087-218">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="99087-219">有关详细信息，请参阅 [数据库镜像和复制 (SQL Server)](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="99087-219">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="99087-220">**-PublisherSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="99087-220">**-PublisherSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="99087-221">指定发布服务器的安全模式。</span><span class="sxs-lookup"><span data-stu-id="99087-221">Specifies the security mode of the Publisher.</span></span> <span data-ttu-id="99087-222">值 **0** 指示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证（默认值），值 **1** 指示 Windows 身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="99087-222">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="99087-223">**-PublisherLogin** _publisher_login_</span><span class="sxs-lookup"><span data-stu-id="99087-223">**-PublisherLogin** _publisher_login_</span></span>  
 <span data-ttu-id="99087-224">发布服务器登录名。</span><span class="sxs-lookup"><span data-stu-id="99087-224">Is the Publisher login name.</span></span>  
  
 <span data-ttu-id="99087-225">**-PublisherPassword** _publisher_password_</span><span class="sxs-lookup"><span data-stu-id="99087-225">**-PublisherPassword** _publisher_password_</span></span>  
 <span data-ttu-id="99087-226">发布服务器密码。</span><span class="sxs-lookup"><span data-stu-id="99087-226">Is the Publisher password.</span></span>  
  
 <span data-ttu-id="99087-227">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="99087-227">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="99087-228">查询超时前等待的秒数。默认值为 1800 秒。</span><span class="sxs-lookup"><span data-stu-id="99087-228">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="99087-229">**-ReadBatchSize** _number_of_transactions_</span><span class="sxs-lookup"><span data-stu-id="99087-229">**-ReadBatchSize** _number_of_transactions_</span></span>  
 <span data-ttu-id="99087-230">每个处理周期从发布数据库的事务日志中读取的最大事务数目，默认值为 500。</span><span class="sxs-lookup"><span data-stu-id="99087-230">Is the maximum number of transactions read out of the transaction log of the publishing database per processing cycle, with a default of 500.</span></span> <span data-ttu-id="99087-231">代理不断读取批次中的事务，直到从该日志中读取所有事务为止。</span><span class="sxs-lookup"><span data-stu-id="99087-231">The agent will continue to read transactions in batches until all transactions are read from the log.</span></span> <span data-ttu-id="99087-232">Oracle 发布服务器不支持该参数。</span><span class="sxs-lookup"><span data-stu-id="99087-232">This parameter is not supported for Oracle Publishers.</span></span>  
  
 <span data-ttu-id="99087-233">**-ReadBatchThreshold** _number_of_commands_</span><span class="sxs-lookup"><span data-stu-id="99087-233">**-ReadBatchThreshold** _number_of_commands_</span></span>  
 <span data-ttu-id="99087-234">在复制命令由分发代理发送给订阅服务器之前，从事务日志读取的复制命令的数目。</span><span class="sxs-lookup"><span data-stu-id="99087-234">Is the number of replication commands to be read from the transaction log before being issued to the Subscriber by the Distribution Agent.</span></span> <span data-ttu-id="99087-235">默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="99087-235">The default is 0.</span></span> <span data-ttu-id="99087-236">如果未指定此参数，日志读取器代理会一直读取完此日志，或者读取到 **-ReadBatchSize** 中指定的数字（事务数）为止。</span><span class="sxs-lookup"><span data-stu-id="99087-236">If this parameter is not specified, the Log Reader Agent will read to the end of the log or to the number specified in **-ReadBatchSize** (number of transactions).</span></span>  
  
 <span data-ttu-id="99087-237">**-RecoverFromDataErrors**</span><span class="sxs-lookup"><span data-stu-id="99087-237">**-RecoverFromDataErrors**</span></span>  
 <span data-ttu-id="99087-238">指定日志读取器代理在从非 SQL Server 发布服务器发布的列数据中遇到错误时应继续运行。</span><span class="sxs-lookup"><span data-stu-id="99087-238">Specifies that the Log Reader Agent continue to run when it encounters errors in column data published from a non-SQL Server Publisher.</span></span> <span data-ttu-id="99087-239">默认情况下，这类错误可导致日志读取器代理失败。</span><span class="sxs-lookup"><span data-stu-id="99087-239">By default, such errors cause the Log Reader Agent to fail.</span></span> <span data-ttu-id="99087-240">在使用 **-RecoverFromDataErrors**后，出错的列数据将复制为 NULL 或者适当的非 Null 值，并在 [MSlogreader_history](/sql/relational-databases/system-tables/mslogreader-history-transact-sql) 表中记录警告消息。</span><span class="sxs-lookup"><span data-stu-id="99087-240">When you use **-RecoverFromDataErrors**, erroneous column data is replicated either as NULL or an appropriate nonnull value, and warning messages are logged to the [MSlogreader_history](/sql/relational-databases/system-tables/mslogreader-history-transact-sql) table.</span></span> <span data-ttu-id="99087-241">仅 Oracle 发布服务器支持此参数。</span><span class="sxs-lookup"><span data-stu-id="99087-241">This parameter is only supported for Oracle Publishers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99087-242">备注</span><span class="sxs-lookup"><span data-stu-id="99087-242">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="99087-243">如果您安装的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理是通过本地系统帐户而不是域用户帐户（默认值）运行，则该服务仅可访问本地计算机。</span><span class="sxs-lookup"><span data-stu-id="99087-243">If you installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a local system account instead of under a domain user account (the default), the service can access only the local computer.</span></span> <span data-ttu-id="99087-244">如果以 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理身份运行的日志读取器代理已配置为在登录到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]时使用 Windows 身份验证模式，则日志读取器代理将失败。</span><span class="sxs-lookup"><span data-stu-id="99087-244">If the Log Reader Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Log Reader Agent fails.</span></span> <span data-ttu-id="99087-245">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认设置为  身份验证。</span><span class="sxs-lookup"><span data-stu-id="99087-245">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="99087-246">有关更改安全帐户的信息，请参阅 [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="99087-246">For information about changing security accounts, see [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="99087-247">若要启动日志读取器代理，请从命令提示符下执行 **logread.exe** 。</span><span class="sxs-lookup"><span data-stu-id="99087-247">To start the Log Reader Agent, execute **logread.exe** from the command prompt.</span></span> <span data-ttu-id="99087-248">有关信息，请参阅[复制代理可执行文件概念](../concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="99087-248">For information, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="change-history"></a><span data-ttu-id="99087-249">更改历史记录</span><span class="sxs-lookup"><span data-stu-id="99087-249">Change History</span></span>  
  
|<span data-ttu-id="99087-250">更新的内容</span><span class="sxs-lookup"><span data-stu-id="99087-250">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="99087-251"> 添加了 -ExtendedEventConfigFile 参数。</span><span class="sxs-lookup"><span data-stu-id="99087-251">Added the **-ExtendedEventConfigFile** parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99087-252">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99087-252">See Also</span></span>  
 [<span data-ttu-id="99087-253">复制代理管理</span><span class="sxs-lookup"><span data-stu-id="99087-253">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
