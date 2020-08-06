---
title: ssbdiagnose 实用工具 (Service Broker) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- Service Broker, runtime reports
- Service Broker, command prompt utilities
- troubleshooting [Service Broker], conversations
- troubleshooting [Service Broker], configurations
- command prompt utilities [Service Broker]
- Service Broker, troubleshooting
- Service Broker, configuration reports
- Service Broker, tools
- troubleshooting [Service Broker], runtime
- conversations [Service Broker], troubleshooting
- troubleshooting [Service Broker], ssbdiagnose utility
- tools [Service Broker], ssbdiagnose
- Service Broker, ssbdiagnose utility
- ssbdiagnose
ms.assetid: 0c1636e8-a3db-438e-be4c-1ea40d1f4877
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8efc581eebd7d8fa7fa265abb54168af78b57ca2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691431"
---
# <a name="ssbdiagnose-utility-service-broker"></a><span data-ttu-id="54eda-102">ssbdiagnose 实用工具 (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="54eda-102">ssbdiagnose Utility (Service Broker)</span></span>
  <span data-ttu-id="54eda-103">**ssbdiagnose** 实用工具可报告 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 会话或 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 服务配置中的问题。</span><span class="sxs-lookup"><span data-stu-id="54eda-103">The **ssbdiagnose** utility reports issues in [!INCLUDE[ssSB](../../includes/sssb-md.md)] conversations or the configuration of [!INCLUDE[ssSB](../../includes/sssb-md.md)] services.</span></span> <span data-ttu-id="54eda-104">可为两个服务或单个服务执行配置检查。</span><span class="sxs-lookup"><span data-stu-id="54eda-104">Configuration checks can be made for either two services or a single service.</span></span> <span data-ttu-id="54eda-105">检查出的问题在命令提示符窗口以人工读取文本的形式报告，或输出为可重定向到文件或其他程序的格式化 XML。</span><span class="sxs-lookup"><span data-stu-id="54eda-105">Issues are reported either in the command prompt window as human-readable text, or as formatted XML that can be redirected to a file or another program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54eda-106">语法</span><span class="sxs-lookup"><span data-stu-id="54eda-106">Syntax</span></span>  
  
```  
  
      ssbdiagnose   
[ [ -XML ]  
    [ -LEVEL { ERROR | WARNING | INFO } ]  
  [-IGNOREerror_id ] [ ...n]  
    [ <baseconnectionoptions> ]  
  { <configurationreport> | <runtimereport> }  
]  
| -?  
  
<configurationreport> ::=  
    CONFIGURATION  
  { [ FROM SERVICEservice_name  
      [ <fromconnectionoptions> ]  
      [ MIRROR <mirrorconnectionoptions> ]  
    ]  
    [ TO SERVICEservice_name[, broker_id ]  
      [ <toconnectionoptions> ]  
      [ MIRROR <mirrorconnectionoptions> ]  
    ]  
  }  
    ON CONTRACTcontract_name  
  [ ENCRYPTION { ON | OFF | ANONYMOUS } ]  
  
<runtime_report> ::=  
    RUNTIME  
    [-SHOWEVENTS ]  
        [ -NEW  
         [ -ID { conversation_handle  
                | conversation_group_id  
                 | conversation_id  
                  }  
        ] [ ...n]  
        ]  
    [ -TIMEOUTtimeout_interval ]  
    [ <runtimeconnectionoptions> ]  
  
<baseconnectionoptions> ::=  
  <connectionoptions>  
  
<fromconnectionoptions> ::=  
  <connectionoptions>  
  
<toconnectionoptions> ::=  
  <connectionoptions>  
  
<mirrorconnectionoptions> ::=  
  <connectionoptions>  
  
<runtimeconnectionoptions> ::=  
  [ CONNECT TO <connectionoptions> ] [ ...n]  
  
<connectionoptions> ::=  
    [ -E | { -Ulogin_id [ -Ppassword ] } ]  
  [ -Sserver_name[\instance_name] ]  
  [ -ddatabase_name ]  
  [ -llogin_timeout ]  
  
```  
  
## <a name="command-line-options"></a><span data-ttu-id="54eda-107">命令行选项</span><span class="sxs-lookup"><span data-stu-id="54eda-107">Command Line Options</span></span>  
 <span data-ttu-id="54eda-108">**-XML**</span><span class="sxs-lookup"><span data-stu-id="54eda-108">**-XML**</span></span>  
 <span data-ttu-id="54eda-109">指定将 **ssbdiagnose** 输出生成为格式化 XML。</span><span class="sxs-lookup"><span data-stu-id="54eda-109">Specifies that the **ssbdiagnose** output be generated as formatted XML.</span></span> <span data-ttu-id="54eda-110">此输出可重定向到一个文件或其他应用程序。</span><span class="sxs-lookup"><span data-stu-id="54eda-110">This can be redirected to a file or to another application.</span></span> <span data-ttu-id="54eda-111">如果未指定 **-XML** ，则 **ssbdiagnose** 输出的格式为人工读取的文本。</span><span class="sxs-lookup"><span data-stu-id="54eda-111">If **-XML** is not specified, the **ssbdiagnose** output is formatted as human-readable text.</span></span>  
  
 <span data-ttu-id="54eda-112">**-LEVEL** { **ERROR** | **WARNING** | **INFO**}</span><span class="sxs-lookup"><span data-stu-id="54eda-112">**-LEVEL** { **ERROR** | **WARNING** | **INFO**}</span></span>  
 <span data-ttu-id="54eda-113">指定要报告的消息的级别。</span><span class="sxs-lookup"><span data-stu-id="54eda-113">Specifies the level of messages to report.</span></span>  
  
 <span data-ttu-id="54eda-114">**ERROR**：仅报告错误消息。</span><span class="sxs-lookup"><span data-stu-id="54eda-114">**ERROR**: report only error messages.</span></span>  
  
 <span data-ttu-id="54eda-115">**WARNING**：报告错误消息和警告消息。</span><span class="sxs-lookup"><span data-stu-id="54eda-115">**WARNING**: report error and warning messages.</span></span>  
  
 <span data-ttu-id="54eda-116">**INFO**：报告错误消息、警告消息和信息性消息。</span><span class="sxs-lookup"><span data-stu-id="54eda-116">**INFO**: report error, warning, and informational messages.</span></span>  
  
 <span data-ttu-id="54eda-117">默认设置为 **WARNING**。</span><span class="sxs-lookup"><span data-stu-id="54eda-117">The default setting is **WARNING**.</span></span>  
  
 <span data-ttu-id="54eda-118">**-IGNORE** *error_id*</span><span class="sxs-lookup"><span data-stu-id="54eda-118">**-IGNORE** *error_id*</span></span>  
 <span data-ttu-id="54eda-119">指定不在报告中包含具有指定 *error_id* 的错误或消息。</span><span class="sxs-lookup"><span data-stu-id="54eda-119">Specifies that errors or messages that have the specified *error_id* not be included in reports.</span></span> <span data-ttu-id="54eda-120">可以多次指定 **-IGNORE** 来禁止显示多个消息 ID。</span><span class="sxs-lookup"><span data-stu-id="54eda-120">You can specify **-IGNORE** multiple times to suppress multiple message IDs.</span></span>  
  
 **\<baseconnectionoptions>**  
 <span data-ttu-id="54eda-121">指定在特定子句中未包含连接选项时 **ssbdiagnose** 所使用的基本连接信息。</span><span class="sxs-lookup"><span data-stu-id="54eda-121">Specifies the base connection information that is used by **ssbdiagnose** when connection options are not included in a specific clause.</span></span> <span data-ttu-id="54eda-122">特定子句中给定的连接信息将覆盖 **baseconnectionoption** 信息。</span><span class="sxs-lookup"><span data-stu-id="54eda-122">The connection information that is given in a specific clause overrides the **baseconnectionoption** information.</span></span> <span data-ttu-id="54eda-123">各参数分别执行此选项。</span><span class="sxs-lookup"><span data-stu-id="54eda-123">This is performed separately for each parameter.</span></span> <span data-ttu-id="54eda-124">例如，如果 **baseconnetionoptions** 中指定了 **-S** 和 **-d**，而 **toconnetionoptions** 中仅指定了 **-d**，则 **ssbdiagnose** 使用 **baseconnetionoptions** 中的 -S 和 **toconnetionoptions**中的 -d。</span><span class="sxs-lookup"><span data-stu-id="54eda-124">For example, if both **-S** and **-d** are specified in **baseconnetionoptions**, and only **-d** is specified in **toconnetionoptions**, **ssbdiagnose** uses -S from **baseconnetionoptions** and -d from **toconnetionoptions**.</span></span>  
  
 <span data-ttu-id="54eda-125">**CONFIGURATION**</span><span class="sxs-lookup"><span data-stu-id="54eda-125">**CONFIGURATION**</span></span>  
 <span data-ttu-id="54eda-126">请求一对 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 服务之间或单个服务的配置错误报告。</span><span class="sxs-lookup"><span data-stu-id="54eda-126">Requests a report of configuration errors between a pair of [!INCLUDE[ssSB](../../includes/sssb-md.md)] services, or for a single service.</span></span>  
  
 <span data-ttu-id="54eda-127">**FROM SERVICE** *service_name*</span><span class="sxs-lookup"><span data-stu-id="54eda-127">**FROM SERVICE** *service_name*</span></span>  
 <span data-ttu-id="54eda-128">指定启动会话的服务。</span><span class="sxs-lookup"><span data-stu-id="54eda-128">Specifies the service that initiates conversations.</span></span>  
  
 **\<fromconnectionoptions>**  
 <span data-ttu-id="54eda-129">指定连接到承载发起方服务的数据库所需的信息。</span><span class="sxs-lookup"><span data-stu-id="54eda-129">Specifies the information that is required to connect to the database that holds the initiator service.</span></span> <span data-ttu-id="54eda-130">如果未指定 **fromconnectionoptions** ，则 **ssbdiagnose** 使用 **baseconnectionoptions** 中的连接信息来连接到发起方数据库。</span><span class="sxs-lookup"><span data-stu-id="54eda-130">If **fromconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions** to connect to the initiator database.</span></span> <span data-ttu-id="54eda-131">如果指定了 **fromconnectionoptions** ，则它必须包括含有发起方服务的数据库。</span><span class="sxs-lookup"><span data-stu-id="54eda-131">If **fromconnectionoptions** is specified it must include the database that contains the initiator service.</span></span> <span data-ttu-id="54eda-132">如果未指定 **fromconnectionoptions** ，则 **baseconnectionoptions** 必须指定发起方数据库。</span><span class="sxs-lookup"><span data-stu-id="54eda-132">If **fromconnectionoptions** is not specified, the **baseconnectionoptions** must specify the initiator database.</span></span>  
  
 <span data-ttu-id="54eda-133">**TO SERVICE** *service_name*[, *broker_id* ]</span><span class="sxs-lookup"><span data-stu-id="54eda-133">**TO SERVICE** *service_name*[, *broker_id* ]</span></span>  
 <span data-ttu-id="54eda-134">指定作为会话目标的服务。</span><span class="sxs-lookup"><span data-stu-id="54eda-134">Specifies the service that is the target for the conversations.</span></span>  
  
 <span data-ttu-id="54eda-135">*service_name*：指定目标服务的名称。</span><span class="sxs-lookup"><span data-stu-id="54eda-135">*service_name*: specifies the name of the target service.</span></span>  
  
 <span data-ttu-id="54eda-136">*broker_id*：指定标识目标数据库的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID。</span><span class="sxs-lookup"><span data-stu-id="54eda-136">*broker_id*: specifies the [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID that identifies the target database.</span></span> <span data-ttu-id="54eda-137">*broker_id* 是一个 GUID。</span><span class="sxs-lookup"><span data-stu-id="54eda-137">*broker_id* is a GUID.</span></span> <span data-ttu-id="54eda-138">可在目标数据库中运行以下查询来查找该 ID：</span><span class="sxs-lookup"><span data-stu-id="54eda-138">You can run the following query in the target database to find it:</span></span>  
  
```  
SELECT service_broker_guid  
FROM sys.databases  
WHERE database_id = DB_ID();  
```  
  
 **\<toconnectionoptions>**  
 <span data-ttu-id="54eda-139">指定连接承载目标服务的数据库所需的信息。</span><span class="sxs-lookup"><span data-stu-id="54eda-139">Specifies the information that is required to connect the database that holds the target service.</span></span> <span data-ttu-id="54eda-140">如果未指定 **toconnectionoptions** ，则 **ssbdiagnose** 使用 **baseconnectionoptions** 中的连接信息来连接到目标数据库。</span><span class="sxs-lookup"><span data-stu-id="54eda-140">If **toconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions** to connect to the target database.</span></span>  
  
 <span data-ttu-id="54eda-141">**MIRROR**</span><span class="sxs-lookup"><span data-stu-id="54eda-141">**MIRROR**</span></span>  
 <span data-ttu-id="54eda-142">指定关联的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 服务驻留在镜像数据库中。</span><span class="sxs-lookup"><span data-stu-id="54eda-142">Specifies that the associated [!INCLUDE[ssSB](../../includes/sssb-md.md)] service is hosted in a mirrored database.</span></span> <span data-ttu-id="54eda-143">**ssbdiagnose** 验证到该服务的路由是否为镜像路由，其中 MIRROR_ADDRESS 已在 CREATE ROUTE 中指定。</span><span class="sxs-lookup"><span data-stu-id="54eda-143">**ssbdiagnose** verifies that the route to the service is a mirrored route, where MIRROR_ADDRESS was specified on CREATE ROUTE.</span></span>  
  
 **\<mirrorconnectionoptions>**  
 <span data-ttu-id="54eda-144">指定连接到镜像数据库所需的信息。</span><span class="sxs-lookup"><span data-stu-id="54eda-144">Specifies the information that is required to connect to the mirror database.</span></span> <span data-ttu-id="54eda-145">如果未指定 **mirrorconnectionoptions** ，则 **ssbdiagnose** 使用 **baseconnectionoptions** 中的连接信息来连接到镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="54eda-145">If **mirrorconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions** to connect to the mirror database.</span></span>  
  
 <span data-ttu-id="54eda-146">**ON CONTRACT** *contract_name*</span><span class="sxs-lookup"><span data-stu-id="54eda-146">**ON CONTRACT** *contract_name*</span></span>  
 <span data-ttu-id="54eda-147">请求 **ssbdiagnose** 仅检查使用指定协定的配置。</span><span class="sxs-lookup"><span data-stu-id="54eda-147">Requests that **ssbdiagnose** only check configurations that use the specified contract.</span></span> <span data-ttu-id="54eda-148">如果未指定 ON CONTRACT，则 **ssbdiagnose** 会将名为 DEFAULT 的协定作为报告对象。</span><span class="sxs-lookup"><span data-stu-id="54eda-148">If ON CONTRACT is not specified, **ssbdiagnose** reports on the contract named DEFAULT.</span></span>  
  
 <span data-ttu-id="54eda-149">**ENCRYPTION** { **ON** | **OFF** | **ANONYMOUS** }</span><span class="sxs-lookup"><span data-stu-id="54eda-149">**ENCRYPTION** { **ON** | **OFF** | **ANONYMOUS** }</span></span>  
 <span data-ttu-id="54eda-150">请求检查是否为对话正确配置了指定的加密级别：</span><span class="sxs-lookup"><span data-stu-id="54eda-150">Requests verification that the dialog is correctly configured for the specified level of encryption:</span></span>  
  
 <span data-ttu-id="54eda-151">**ON**：默认设置。</span><span class="sxs-lookup"><span data-stu-id="54eda-151">**ON**: Default setting.</span></span> <span data-ttu-id="54eda-152">配置了完全对话安全设置。</span><span class="sxs-lookup"><span data-stu-id="54eda-152">Full dialog security is configured.</span></span> <span data-ttu-id="54eda-153">已为对话双方部署了证书，存在远程服务绑定，且针对目标服务的 GRANT SEND 语句指定了发起方用户。</span><span class="sxs-lookup"><span data-stu-id="54eda-153">Certificates have been deployed on both sides of the dialog, a remote service binding is present, and the GRANT SEND statement for the target service specified the initiator user.</span></span>  
  
 <span data-ttu-id="54eda-154">**OFF**：未配置任何对话安全设置。</span><span class="sxs-lookup"><span data-stu-id="54eda-154">**OFF**: No dialog security is configured.</span></span> <span data-ttu-id="54eda-155">未部署证书，没有创建任何远程服务绑定，且针对发起方服务的 GRANT SEND 指定了 **公共** 角色。</span><span class="sxs-lookup"><span data-stu-id="54eda-155">No certificates have been deployed, no remote service binding was created, and the GRANT SEND for the initiator service specified the **public** role.</span></span>  
  
 <span data-ttu-id="54eda-156">**ANONYMOUS**：配置了匿名对话安全设置。</span><span class="sxs-lookup"><span data-stu-id="54eda-156">**ANONYMOUS**: Anonymous dialog security is configured.</span></span> <span data-ttu-id="54eda-157">已部署了一个证书，远程服务绑定指定了匿名子句，且针对目标服务的 GRANT SEND 指定了 **公共** 角色。</span><span class="sxs-lookup"><span data-stu-id="54eda-157">One certificate has been deployed, the remote service binding specified the anonymous clause, and the GRANT SEND for the target service specified the **public** role.</span></span>  
  
 <span data-ttu-id="54eda-158">**RUNTIME**</span><span class="sxs-lookup"><span data-stu-id="54eda-158">**RUNTIME**</span></span>  
 <span data-ttu-id="54eda-159">请求导致 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 会话运行时错误的问题的报告。</span><span class="sxs-lookup"><span data-stu-id="54eda-159">Requests a report of issues that cause runtime errors for a [!INCLUDE[ssSB](../../includes/sssb-md.md)] conversation.</span></span> <span data-ttu-id="54eda-160">如果 **-NEW** 和 **-ID** 都未指定，则 **ssbdiagnose** 将监视连接选项中指定的所有数据库中的所有会话。</span><span class="sxs-lookup"><span data-stu-id="54eda-160">If neither **-NEW** or **-ID** are specified, **ssbdiagnose** monitors all conversations in all databases specified in the connection options.</span></span> <span data-ttu-id="54eda-161">如果指定了 **-NEW** 或 **-ID** ， **ssbdiagnose** 将生成参数中指定的 ID 列表。</span><span class="sxs-lookup"><span data-stu-id="54eda-161">If **-NEW** or **-ID** are specified, **ssbdiagnose** builds a list of the IDs specified in the parameters.</span></span>  
  
 <span data-ttu-id="54eda-162">**ssbdiagnose** 在运行状态下将记录指示运行时错误的所有 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="54eda-162">While **ssbdiagnose** is running, it records all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] events that indicate runtime errors.</span></span> <span data-ttu-id="54eda-163">它会记录指定 ID 所发生的事件以及系统级事件。</span><span class="sxs-lookup"><span data-stu-id="54eda-163">It records the events that occur for the specified IDs, plus system-level events.</span></span> <span data-ttu-id="54eda-164">如果遇到运行时错误， **ssbdiagnose** 会对相关配置运行配置报告。</span><span class="sxs-lookup"><span data-stu-id="54eda-164">If runtime errors are encountered, **ssbdiagnose** runs a configuration report on the associated configuration.</span></span>  
  
 <span data-ttu-id="54eda-165">默认情况下，输出报告中不包含运行时错误，而只包含对配置的分析结果。</span><span class="sxs-lookup"><span data-stu-id="54eda-165">By default, runtime errors are not included in the output report, only the results of the configuration analysis.</span></span> <span data-ttu-id="54eda-166">使用 **-SHOWEVENTS** 可将运行时错误包含在报告中。</span><span class="sxs-lookup"><span data-stu-id="54eda-166">Use **-SHOWEVENTS** to have the runtime errors included in the report.</span></span>  
  
 <span data-ttu-id="54eda-167">**-SHOWEVENTS**</span><span class="sxs-lookup"><span data-stu-id="54eda-167">**-SHOWEVENTS**</span></span>  
 <span data-ttu-id="54eda-168">指定 **ssbdiagnose** 报告 RUNTIME 报告期间出现的 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="54eda-168">Specifies that **ssbdiagnose** report [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] events during a RUNTIME report.</span></span> <span data-ttu-id="54eda-169">仅报告视为错误情况的事件。</span><span class="sxs-lookup"><span data-stu-id="54eda-169">Only events that are considered error conditions are reported.</span></span> <span data-ttu-id="54eda-170">默认情况下， **ssbdiagnose** 只监视错误事件，而不在输出中报告这些事件。</span><span class="sxs-lookup"><span data-stu-id="54eda-170">By default, **ssbdiagnose** only monitors error events; it does not report them in the output.</span></span>  
  
 <span data-ttu-id="54eda-171">**-NEW**</span><span class="sxs-lookup"><span data-stu-id="54eda-171">**-NEW**</span></span>  
 <span data-ttu-id="54eda-172">请求对 **ssbdiagnose** 开始运行后的第一个会话进行运行时监视。</span><span class="sxs-lookup"><span data-stu-id="54eda-172">Requests runtime monitoring of the first conversation that begins after **ssbdiagnose** starts running.</span></span>  
  
 <span data-ttu-id="54eda-173">**-ID**</span><span class="sxs-lookup"><span data-stu-id="54eda-173">**-ID**</span></span>  
 <span data-ttu-id="54eda-174">请求对指定会话元素进行运行时监视。</span><span class="sxs-lookup"><span data-stu-id="54eda-174">Requests runtime monitoring of the specified conversation elements.</span></span> <span data-ttu-id="54eda-175">可以多次指定 **-ID** 。</span><span class="sxs-lookup"><span data-stu-id="54eda-175">You can specify **-ID** multiple times.</span></span>  
  
 <span data-ttu-id="54eda-176">如果指定一个会话句柄，则仅报告与关联的会话端点相关的事件。</span><span class="sxs-lookup"><span data-stu-id="54eda-176">If you specify a conversation handle, only events associated with the associated conversation endpoint are reported.</span></span> <span data-ttu-id="54eda-177">如果指定一个会话 ID，则会报告该会话及其发起方端点和目标端点的所有事件。</span><span class="sxs-lookup"><span data-stu-id="54eda-177">If you specify a conversation ID, all events for that conversation and its initiator and target endpoints are reported.</span></span> <span data-ttu-id="54eda-178">如果指定一个会话组 ID，则会报告该会话组中所有会话和端点的所有事件。</span><span class="sxs-lookup"><span data-stu-id="54eda-178">If a conversation group ID is specified, all events for all conversations and endpoints in the conversation group are reported.</span></span>  
  
 <span data-ttu-id="54eda-179">*conversation_handle*</span><span class="sxs-lookup"><span data-stu-id="54eda-179">*conversation_handle*</span></span>  
 <span data-ttu-id="54eda-180">标识应用程序中某个会话端点的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="54eda-180">A unique identifier that identifies a conversation endpoint in an application.</span></span> <span data-ttu-id="54eda-181">每个会话端点的会话句柄都是唯一的，发起方端点和目标端点具有不同的会话句柄。</span><span class="sxs-lookup"><span data-stu-id="54eda-181">Conversation handles are unique to one endpoint of a conversation, the initiator and target endpoints have separate conversation handles.</span></span>  
  
 <span data-ttu-id="54eda-182">会话句柄由 *@dialog_handle* **BEGIN DIALOG**语句的参数以及 `conversation_handle` **RECEIVE**语句结果集中的列返回到应用程序。</span><span class="sxs-lookup"><span data-stu-id="54eda-182">Conversation handles are returned to applications by the *@dialog_handle* parameter of the **BEGIN DIALOG** statement, and the `conversation_handle` column in the result set of a **RECEIVE** statement.</span></span>  
  
 <span data-ttu-id="54eda-183">会话句柄在 `conversation_handle` **sys. transmission_queue**和 **.sys conversation_endpoints**目录视图的列中进行报告。</span><span class="sxs-lookup"><span data-stu-id="54eda-183">Conversation handles are reported in the `conversation_handle` column of the **sys.transmission_queue** and **sys.conversation_endpoints** catalog views.</span></span>  
  
 <span data-ttu-id="54eda-184">*conversation_group_id*</span><span class="sxs-lookup"><span data-stu-id="54eda-184">*conversation_group_id*</span></span>  
 <span data-ttu-id="54eda-185">标识会话组的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="54eda-185">The unique identifier that identifies a conversation group.</span></span>  
  
 <span data-ttu-id="54eda-186">会话组 Id 由 *@conversation_group_id* **GET 会话组**语句的参数以及 `conversation_group_id` **RECEIVE**语句结果集中的列返回到应用程序。</span><span class="sxs-lookup"><span data-stu-id="54eda-186">Conversation group IDs are returned to applications by the *@conversation_group_id* parameter of the **GET CONVERSATION GROUP** statement and the `conversation_group_id` column in the result set of a **RECEIVE** statement.</span></span>  
  
 <span data-ttu-id="54eda-187">会话组 Id 在 `conversation_group_id` **sys.databases conversation_groups**和**sys.databases conversation_endpoints**目录视图的列中报告。</span><span class="sxs-lookup"><span data-stu-id="54eda-187">Conversation group IDs are reported in the `conversation_group_id` columns of the **sys.conversation_groups** and **sys.conversation_endpoints** catalog views.</span></span>  
  
 <span data-ttu-id="54eda-188">*conversation_id*</span><span class="sxs-lookup"><span data-stu-id="54eda-188">*conversation_id*</span></span>  
 <span data-ttu-id="54eda-189">标识会话的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="54eda-189">The unique identifier that identifies a conversation.</span></span> <span data-ttu-id="54eda-190">会话的发起方端点和目标端点的会话 ID 是相同的。</span><span class="sxs-lookup"><span data-stu-id="54eda-190">Conversation IDs are the same for both the initiator and target endpoints of a conversation.</span></span>  
  
 <span data-ttu-id="54eda-191">在 `conversation_id` **conversation_endpoints sys.databases**目录视图的列中报告会话 id。</span><span class="sxs-lookup"><span data-stu-id="54eda-191">Conversation IDs are reported in the `conversation_id` column of the **sys.conversation_endpoints** catalog view.</span></span>  
  
 <span data-ttu-id="54eda-192">**-TIMEOUT** *timeout_interval*</span><span class="sxs-lookup"><span data-stu-id="54eda-192">**-TIMEOUT** *timeout_interval*</span></span>  
 <span data-ttu-id="54eda-193">指定运行 **RUNTIME** 报告的秒数。</span><span class="sxs-lookup"><span data-stu-id="54eda-193">Specifies the number of seconds for a **RUNTIME** report to run.</span></span> <span data-ttu-id="54eda-194">如果未指定 **-TIMEOUT** ，则运行时报告的运行时间不限。</span><span class="sxs-lookup"><span data-stu-id="54eda-194">If **-TIMEOUT** is not specified the runtime report runs indefinitely.</span></span> <span data-ttu-id="54eda-195">**-TIMEOUT** 仅用于 **RUNTIME** 报告，而不用于 **CONFIGURATION** 报告。</span><span class="sxs-lookup"><span data-stu-id="54eda-195">**-TIMEOUT** is used only on **RUNTIME** reports, not **CONFIGURATION** reports.</span></span> <span data-ttu-id="54eda-196">如果未指定 -TIMEOUT 或要在超时间隔到期之前结束运行时报告，请按 Ctrl + C 退出 ssbdiagnose   **-** 。</span><span class="sxs-lookup"><span data-stu-id="54eda-196">Use ctrl + C to quit **ssbdiagnose** if **-TIMEOUT** was not specified or to end a runtime report before the time**-** out interval expires.</span></span> <span data-ttu-id="54eda-197">*timeout_interval* 必须是介于 1 和 2,147,483,647 之间的数字。</span><span class="sxs-lookup"><span data-stu-id="54eda-197">*timeout_interval* must be a number between 1 and 2,147,483,647.</span></span>  
  
 **\<runtimeconnectionoptions>**  
 <span data-ttu-id="54eda-198">指定数据库的连接信息，该数据库包含与受监视的会话元素关联的服务。</span><span class="sxs-lookup"><span data-stu-id="54eda-198">Specifies the connection information for the databases that contain the services associated with conversation elements being monitored.</span></span> <span data-ttu-id="54eda-199">如果所有服务都位于同一数据库中，则只需指定一个 **CONNECT TO** 子句。</span><span class="sxs-lookup"><span data-stu-id="54eda-199">If all the services are in the same database, you only have to specify one **CONNECT TO** clause.</span></span> <span data-ttu-id="54eda-200">如果各服务位于不同的数据库中，必须为每个数据库提供一个 **CONNECT TO** 子句。</span><span class="sxs-lookup"><span data-stu-id="54eda-200">If the services are in separate databases you must supply a **CONNECT TO** clause for each database.</span></span> <span data-ttu-id="54eda-201">如果未指定 **runtimeconnectionoptions** ，则 **ssbdiagnose** 使用 **baseconnectionoptions**中的连接信息。</span><span class="sxs-lookup"><span data-stu-id="54eda-201">If **runtimeconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions**.</span></span>  
  
 <span data-ttu-id="54eda-202">**-E**</span><span class="sxs-lookup"><span data-stu-id="54eda-202">**-E**</span></span>  
 <span data-ttu-id="54eda-203">将当前 Windows 帐户用作登录 ID 来打开指向 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例的 Windows 身份验证连接。</span><span class="sxs-lookup"><span data-stu-id="54eda-203">Open a Windows Authentication connection to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by using your current Windows account as the login ID.</span></span> <span data-ttu-id="54eda-204">登录名必须是 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="54eda-204">The login must be a member of the **sysadmin** fixed-server role.</span></span>  
  
 <span data-ttu-id="54eda-205">使用 -E 选项将忽略 SQLCMDUSER 和 SQLCMDPASSWORD 环境变量的用户和密码设置。</span><span class="sxs-lookup"><span data-stu-id="54eda-205">The -E option ignores the user and password settings of the SQLCMDUSER and SQLCMDPASSWORD environment variables.</span></span>  
  
 <span data-ttu-id="54eda-206">如果 **-E** 和 **-U** 都未指定，则 **ssbdiagnose** 将使用 SQLCMDUSER 环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="54eda-206">If neither **-E** nor **-U** is specified, **ssbdiagnose** uses the value from the SQLCMDUSER environment variable.</span></span> <span data-ttu-id="54eda-207">如果 SQLCMDUSER 也未设置，则 **ssbdiagnose** 将使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="54eda-207">If SQLCMDUSER is not set either, **ssbdiagnose** uses Windows Authentication.</span></span>  
  
 <span data-ttu-id="54eda-208">如果将 **-E** 选项与 **-U** 选项或 **-P** 选项一起使用，将生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="54eda-208">If the **-E** option is used together with the **-U** option or the **-P** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="54eda-209">**-U** *login_id*</span><span class="sxs-lookup"><span data-stu-id="54eda-209">**-U** *login_id*</span></span>  
 <span data-ttu-id="54eda-210">使用指定的登录 ID 打开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证连接。</span><span class="sxs-lookup"><span data-stu-id="54eda-210">Open a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication connection by using the specified login ID.</span></span> <span data-ttu-id="54eda-211">登录名必须是 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="54eda-211">The login must be a member of the **sysadmin** fixed-server role.</span></span>  
  
 <span data-ttu-id="54eda-212">如果 **-E** 和 **-U** 都未指定，则 **ssbdiagnose** 将使用 SQLCMDUSER 环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="54eda-212">If neither **-E** nor **-U** is specified, **ssbdiagnose** uses the value from the SQLCMDUSER environment variable.</span></span> <span data-ttu-id="54eda-213">如果 SQLCMDUSER 也未设置，则 **ssbdiagnose** 会尝试使用 Windows 身份验证模式，基于运行 **ssbdiagnose**的用户的 Windows 帐户进行连接。</span><span class="sxs-lookup"><span data-stu-id="54eda-213">If SQLCMDUSER is not set either, **ssbdiagnose** tries to connect by using Windows Authentication mode based on the Windows account of the user who is running **ssbdiagnose**.</span></span>  
  
 <span data-ttu-id="54eda-214">如果将 **-U** 选项与 **-E** 选项一起使用，将生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="54eda-214">If the **-U** option is used together with the **-E** option, an error message is generated.</span></span> <span data-ttu-id="54eda-215">如果 -U  选项后跟多个参数，便会生成错误消息并退出程序。</span><span class="sxs-lookup"><span data-stu-id="54eda-215">If the **-U** option is followed by more than one argument, an error message is generated and the program exits.</span></span>  
  
 <span data-ttu-id="54eda-216">**-P** *password*</span><span class="sxs-lookup"><span data-stu-id="54eda-216">**-P** *password*</span></span>  
 <span data-ttu-id="54eda-217">指定 **-U** 登录 ID 的密码。</span><span class="sxs-lookup"><span data-stu-id="54eda-217">Specifies the password for the **-U** login ID.</span></span> <span data-ttu-id="54eda-218">密码是区分大小写的。</span><span class="sxs-lookup"><span data-stu-id="54eda-218">Passwords are case sensitive.</span></span> <span data-ttu-id="54eda-219">如果使用了 **-U** 选项而未使用 **-P** 选项，则 **ssbdiagnose** 将使用 SQLCMDPASSWORD 环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="54eda-219">If the **-U** option is used and the **-P** option is not used, **ssbdiagnose** uses the value from the SQLCMDPASSWORD environment variable.</span></span> <span data-ttu-id="54eda-220">如果 SQLCMDPASSWORD 也未设置，则 **ssbdiagnose** 会提示用户输入密码。</span><span class="sxs-lookup"><span data-stu-id="54eda-220">If SQLCMDPASSWORD is not set either, **ssbdiagnose** prompts the user for a password.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="54eda-221">键入 SET SQLCMDPASSWORD 命令时，任何可以看到您的监视器的人均可看到密码。</span><span class="sxs-lookup"><span data-stu-id="54eda-221">When you type a SET SQLCMDPASSWORD command, your password will be visible to anyone who can see your monitor.</span></span>  
  
 <span data-ttu-id="54eda-222">如果指定了 **-P** 选项而未指定密码，则 **ssbdiagnose** 将使用默认密码 (NULL)。</span><span class="sxs-lookup"><span data-stu-id="54eda-222">If the **-P** option is specified without a password **ssbdiagnose** uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]<span data-ttu-id="54eda-223">有关详细信息，请参阅[强密码](../../relational-databases/security/strong-passwords.md)。</span><span class="sxs-lookup"><span data-stu-id="54eda-223">For more information, see [Strong Passwords](../../relational-databases/security/strong-passwords.md).</span></span>  
  
 <span data-ttu-id="54eda-224">通过向控制台输出密码提示，可以显示密码提示，如下所示： `Password:`</span><span class="sxs-lookup"><span data-stu-id="54eda-224">The password prompt is displayed by printing the password prompt to the console, as follows: `Password:`</span></span>  
  
 <span data-ttu-id="54eda-225">隐藏用户输入。</span><span class="sxs-lookup"><span data-stu-id="54eda-225">User input is hidden.</span></span> <span data-ttu-id="54eda-226">也就是说，将不会显示任何输入的内容，光标保留原位不动。</span><span class="sxs-lookup"><span data-stu-id="54eda-226">This means that nothing is displayed and the cursor stays in position.</span></span>  
  
 <span data-ttu-id="54eda-227">如果将 **-P** 选项与 **-E** 选项一起使用，将生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="54eda-227">If the **-P** option is used with the **-E** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="54eda-228">如果 **-P** 选项后跟多个参数，将生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="54eda-228">If the **-P** option is followed by more than one argument, an error message is generated.</span></span>  
  
 <span data-ttu-id="54eda-229">**-S** *server_name*[\\*instance_name*]</span><span class="sxs-lookup"><span data-stu-id="54eda-229">**-S** *server_name*[\\*instance_name*]</span></span>  
 <span data-ttu-id="54eda-230">指定承载要分析的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服务的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="54eda-230">Specifies the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that holds the [!INCLUDE[ssSB](../../includes/sssb-md.md)] services to be analyzed.</span></span>  
  
 <span data-ttu-id="54eda-231">指定要连接到该服务器上 *默认实例的* server_name [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="54eda-231">Specify *server_name* to connect to the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on that server.</span></span> <span data-ttu-id="54eda-232">指定*server_name ***\\*** instance_name*连接到该服务器上的命名实例 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="54eda-232">Specify *server_name***\\***instance_name* to connect to a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on that server.</span></span> <span data-ttu-id="54eda-233">如果未指定 **-S** ，则 **ssbdiagnose** 将使用 SQLCMDSERVER 环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="54eda-233">If **-S** is not specified, **ssbdiagnose** uses the value of the SQLCMDSERVER environment variable.</span></span> <span data-ttu-id="54eda-234">如果 SQLCMDSERVER 也未设置，则 **ssbdiagnose** 将连接到本地计算机上的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的默认实例。</span><span class="sxs-lookup"><span data-stu-id="54eda-234">If SQLCMDSERVER is not set either, **ssbdiagnose** connects to the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="54eda-235">**-d** *database_name*</span><span class="sxs-lookup"><span data-stu-id="54eda-235">**-d** *database_name*</span></span>  
 <span data-ttu-id="54eda-236">指定承载要分析的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 服务的数据库。</span><span class="sxs-lookup"><span data-stu-id="54eda-236">Specifies the database that holds the [!INCLUDE[ssSB](../../includes/sssb-md.md)] services to be analyzed.</span></span> <span data-ttu-id="54eda-237">如果该数据库不存在，将生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="54eda-237">If the database does not exist, an error message is generated.</span></span> <span data-ttu-id="54eda-238">如果未指定 **-d** ，则默认为登录帐户的默认数据库属性中指定的数据库。</span><span class="sxs-lookup"><span data-stu-id="54eda-238">If **-d** is not specified, the default is the database specified in the default-database property for your login.</span></span>  
  
 <span data-ttu-id="54eda-239">**-l** *login_timeout*</span><span class="sxs-lookup"><span data-stu-id="54eda-239">**-l** *login_timeout*</span></span>  
 <span data-ttu-id="54eda-240">指定尝试连接到服务器时，等待了多少秒后超时。如果未指定 **-l** ，则 **ssbdiagnose** 将使用为 SQLCMDLOGINTIMEOUT 环境变量设置的值。</span><span class="sxs-lookup"><span data-stu-id="54eda-240">Specifies the number of seconds before an attempt to connect to a server times out. If **-l** is not specified, **ssbdiagnose** uses the value set for the SQLCMDLOGINTIMEOUT environment variable.</span></span> <span data-ttu-id="54eda-241">如果 SQLCMDLOGINTIMEOUT 也未设置，则默认的超时值为 30 秒。</span><span class="sxs-lookup"><span data-stu-id="54eda-241">If SQLCMDLOGINTIMEOUT is not set either, the default time-out is thirty seconds.</span></span> <span data-ttu-id="54eda-242">登录超时必须是介于 0 和 65534 之间的数字。</span><span class="sxs-lookup"><span data-stu-id="54eda-242">The login time-out must be a number between 0 and 65534.</span></span> <span data-ttu-id="54eda-243">如果提供的值不是数值或不在此范围内，则 **ssbdiagnose** 将生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="54eda-243">If the value that is supplied is not numeric or does not fall into that range, **ssbdiagnose** generates an error message.</span></span> <span data-ttu-id="54eda-244">该值为 0 时，则允许无限制等待。</span><span class="sxs-lookup"><span data-stu-id="54eda-244">A value of 0 specifies time-out to be infinite.</span></span>  
  
 <span data-ttu-id="54eda-245">**-?**</span><span class="sxs-lookup"><span data-stu-id="54eda-245">**-?**</span></span>  
 <span data-ttu-id="54eda-246">显示命令行帮助。</span><span class="sxs-lookup"><span data-stu-id="54eda-246">Displays command line help.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54eda-247">备注</span><span class="sxs-lookup"><span data-stu-id="54eda-247">Remarks</span></span>  
 <span data-ttu-id="54eda-248">使用 **ssbdiagnose** 可以执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="54eda-248">Use **ssbdiagnose** to do the following:</span></span>  
  
-   <span data-ttu-id="54eda-249">确认在新配置的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 应用程序中没有配置错误。</span><span class="sxs-lookup"><span data-stu-id="54eda-249">Confirm that there are no configuration errors in a newly configured [!INCLUDE[ssSB](../../includes/sssb-md.md)] application.</span></span>  
  
-   <span data-ttu-id="54eda-250">确认在更改现有 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 应用程序的配置后没有配置错误。</span><span class="sxs-lookup"><span data-stu-id="54eda-250">Confirm that there are no configuration errors after changing the configuration of an existing [!INCLUDE[ssSB](../../includes/sssb-md.md)] application.</span></span>  
  
-   <span data-ttu-id="54eda-251">确认在将 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 数据库从 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例分离并重新附加到数据库引擎的新实例后没有配置错误。</span><span class="sxs-lookup"><span data-stu-id="54eda-251">Confirm that there are no configuration errors after a [!INCLUDE[ssSB](../../includes/sssb-md.md)] database is detached and then reattached to a new instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="54eda-252">探查当消息不能在服务间成功传输时是否存在配置错误。</span><span class="sxs-lookup"><span data-stu-id="54eda-252">Research whether there are configuration errors when messages are not successfully transmitted between services.</span></span>  
  
-   <span data-ttu-id="54eda-253">获取一组 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 会话元素中出现的所有错误的报告。</span><span class="sxs-lookup"><span data-stu-id="54eda-253">Get a report of any errors that occur in a set of [!INCLUDE[ssSB](../../includes/sssb-md.md)] conversation elements.</span></span>  
  
## <a name="configuration-reporting"></a><span data-ttu-id="54eda-254">配置报告</span><span class="sxs-lookup"><span data-stu-id="54eda-254">Configuration Reporting</span></span>  
 <span data-ttu-id="54eda-255">若要正确分析会话所使用的配置，请运行所用选项与该会话所用选项相同的 **ssbdiagnose** 配置报告。</span><span class="sxs-lookup"><span data-stu-id="54eda-255">To correctly analyze the configuration used by a conversation, run a **ssbdiagnose** configuration report that uses the same options that are used by the conversation.</span></span> <span data-ttu-id="54eda-256">如果为 **ssbdiagnose** 指定的选项级别低于会话所使用的选项级别， **ssbdiagnose** 可能不报告会话所需的条件。</span><span class="sxs-lookup"><span data-stu-id="54eda-256">If you specify a lower level of options for **ssbdiagnose** than are used by the conversation, **ssbdiagnose** might not report conditions that are required by the conversation.</span></span> <span data-ttu-id="54eda-257">如果为 **ssbdiagnose**指定的选项级别高于会话所使用的选项级别，则可能会报告会话并不需要的项。</span><span class="sxs-lookup"><span data-stu-id="54eda-257">If you specify a higher level of options for **ssbdiagnose**, it might report items that are not required by the conversation.</span></span> <span data-ttu-id="54eda-258">例如，同一数据库中两个服务间的会话可在 ENCPRYPTION OFF 的情况下运行。</span><span class="sxs-lookup"><span data-stu-id="54eda-258">For example, a conversation between two services in the same database can be run with ENCPRYPTION OFF.</span></span> <span data-ttu-id="54eda-259">如果运行 **ssbdiagnose** 来验证这两个服务间的配置，但使用的是默认的 ENCRYPTION ON 设置，则 **ssbdiagnose** 将报告数据库缺少主密钥。</span><span class="sxs-lookup"><span data-stu-id="54eda-259">If you run **ssbdiagnose** to validate the configuration between the two services, but use the default ENCRYPTION ON setting, **ssbdiagnose** reports that the database is missing a master key.</span></span> <span data-ttu-id="54eda-260">而主密钥并不是会话所需的。</span><span class="sxs-lookup"><span data-stu-id="54eda-260">A master key is not required for the conversation.</span></span>  
  
 <span data-ttu-id="54eda-261">**ssbdiagnose** 配置报告每次运行时只能分析一个 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 服务或单对服务。</span><span class="sxs-lookup"><span data-stu-id="54eda-261">The **ssbdiagnose** configuration report analyzes only one [!INCLUDE[ssSB](../../includes/sssb-md.md)] service or a single pair of services every time it is run.</span></span> <span data-ttu-id="54eda-262">若要对多对 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 服务生成报告，请生成一个 .cmd 命令文件，在其中多次调用 **ssbdiagnose** 。</span><span class="sxs-lookup"><span data-stu-id="54eda-262">To report on multiple pairs of [!INCLUDE[ssSB](../../includes/sssb-md.md)] services, build a .cmd command file that calls **ssbdiagnose** multiple times.</span></span>  
  
## <a name="runtime-reporting"></a><span data-ttu-id="54eda-263">运行时报告</span><span class="sxs-lookup"><span data-stu-id="54eda-263">Runtime Reporting</span></span>  
 <span data-ttu-id="54eda-264">指定了 -RUNTIME 时， **ssbdiagnose** 将搜索 **runtimeconnectionoptions** 和 **baseconnectionoptions** 中指定的所有数据库以生成 [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID 的列表。</span><span class="sxs-lookup"><span data-stu-id="54eda-264">When -RUNTIME is specified, **ssbdiagnose** searches all databases specified in **runtimeconnectionoptions** and **baseconnectionoptions** to build a list of [!INCLUDE[ssSB](../../includes/sssb-md.md)] IDs.</span></span> <span data-ttu-id="54eda-265">生成的 ID 的完整列表取决于为 -NEW 和 -ID 指定的内容：</span><span class="sxs-lookup"><span data-stu-id="54eda-265">The full list of IDs built depends on what is specified for -NEW and -ID:</span></span>  
  
-   <span data-ttu-id="54eda-266">如果 **-NEW** 和 **-ID** 都未指定，则该列表将包含连接选项中指定的所有数据库的所有会话。</span><span class="sxs-lookup"><span data-stu-id="54eda-266">If neither **-NEW** or **-ID** are specified, the list includes all conversations for all databases specified in the connection options.</span></span>  
  
-   <span data-ttu-id="54eda-267">如果指定了 **-NEW** ，则 **ssbdiagnose** 将包含 **ssbdiagnose** 运行后开始的第一个会话的元素。</span><span class="sxs-lookup"><span data-stu-id="54eda-267">If **-NEW** is specified, **ssbdiagnose** includes the elements for the first conversation that starts after **ssbdiagnose** is run.</span></span> <span data-ttu-id="54eda-268">这些元素包括会话 ID 以及目标会话端点和发起方会话端点的会话句柄。</span><span class="sxs-lookup"><span data-stu-id="54eda-268">This includes the conversation ID and the conversation handles for both the target and initiator conversation endpoints.</span></span>  
  
-   <span data-ttu-id="54eda-269">如果指定 **-ID** 时提供了会话句柄，则只在列表中包含该句柄。</span><span class="sxs-lookup"><span data-stu-id="54eda-269">If **-ID** is specified with a conversation handle, only that handle is included in the list.</span></span>  
  
-   <span data-ttu-id="54eda-270">如果指定 **-ID** 时提供了会话 ID，则该会话 ID 及其两个会话端点的句柄都会添加到列表中。</span><span class="sxs-lookup"><span data-stu-id="54eda-270">If **-ID** is specified with a conversation ID, the conversation ID and the handles for both of its conversation endpoints are added to the list.</span></span>  
  
-   <span data-ttu-id="54eda-271">如果指定 **-ID** 时提供了会话组 ID，则该组中的所有会话 ID 和会话句柄都会添加到列表中。</span><span class="sxs-lookup"><span data-stu-id="54eda-271">If **-ID** is specified with a conversation group ID, all the conversation IDs and conversation handles in that group are added to the list.</span></span>  
  
 <span data-ttu-id="54eda-272">该列表不包含连接选项未涵盖的数据库中的元素。</span><span class="sxs-lookup"><span data-stu-id="54eda-272">The list does not include elements from databases that are not covered by the connection options.</span></span> <span data-ttu-id="54eda-273">例如，假定你使用 **-ID** 指定会话 ID，但只为发起方数据库提供 **runtimeconnectionoptions** 子句而不为目标数据库提供。</span><span class="sxs-lookup"><span data-stu-id="54eda-273">For example, assume that you use **-ID** to specify a conversation ID, but only provide a **runtimeconnectionoptions** clause for the initiator database and not the target database.</span></span> <span data-ttu-id="54eda-274">**ssbdiagnose** 将不在其 ID 列表中包含目标会话句柄，而只包含会话 ID 和发起方会话句柄。</span><span class="sxs-lookup"><span data-stu-id="54eda-274">**ssbdiagnose** will not include the target conversation handle in its list of IDs, only the conversation ID and the initiator conversation handle.</span></span>  
  
 <span data-ttu-id="54eda-275">**ssbdiagnose** 监视 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] runtimeconnectionoptions **和** baseconnectionoptions **涵盖的数据库中的**事件。</span><span class="sxs-lookup"><span data-stu-id="54eda-275">**ssbdiagnose** monitors the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] events from the databases covered by **runtimeconnectionoptions** and **baseconnectionoptions**.</span></span> <span data-ttu-id="54eda-276">它会搜索指示运行时列表中的一个或多个 [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID 遇到错误的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="54eda-276">It searches for [!INCLUDE[ssSB](../../includes/sssb-md.md)] events that indicate an error was encountered by one or more of the [!INCLUDE[ssSB](../../includes/sssb-md.md)] IDs in the runtime list.</span></span> <span data-ttu-id="54eda-277">**ssbdiagnose** 还会搜索未专门与任何会话组关联的系统级 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 错误事件。</span><span class="sxs-lookup"><span data-stu-id="54eda-277">**ssbdiagnose** also searches for system-level [!INCLUDE[ssSB](../../includes/sssb-md.md)] error events not specifically associated with any conversation group.</span></span>  
  
 <span data-ttu-id="54eda-278">如果 **ssbdiagnose** 找到会话错误，则该实用工具也将通过运行配置报告来尝试报告导致事件的根本原因。</span><span class="sxs-lookup"><span data-stu-id="54eda-278">If **ssbdiagnose** finds conversation errors, the utility will attempt to report on the root cause of the events by also running a configuration report.</span></span> <span data-ttu-id="54eda-279">**ssbdiagnose** 使用数据库中的元数据来尝试确定会话所使用的实例、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID、数据库、服务和协定。</span><span class="sxs-lookup"><span data-stu-id="54eda-279">**ssbdiagnose** uses the metadata in the databases to try to determine the instances, [!INCLUDE[ssSB](../../includes/sssb-md.md)] IDs, databases, services, and contracts used by the conversation.</span></span> <span data-ttu-id="54eda-280">然后它使用所有可用信息运行配置报告。</span><span class="sxs-lookup"><span data-stu-id="54eda-280">It then runs a configuration report using all available information.</span></span>  
  
 <span data-ttu-id="54eda-281">默认情况下， **ssbdiagnose** 不报告错误事件。</span><span class="sxs-lookup"><span data-stu-id="54eda-281">By default, **ssbdiagnose** does not report error events.</span></span> <span data-ttu-id="54eda-282">它只报告配置检查中找到的基础性问题。</span><span class="sxs-lookup"><span data-stu-id="54eda-282">It only reports the underlying issues found during the configuration check.</span></span> <span data-ttu-id="54eda-283">这使报告的信息量减到最少，有助于您将注意力集中在基础配置问题上。</span><span class="sxs-lookup"><span data-stu-id="54eda-283">This minimizes the amount of information reported and helps you focus on the underlying configuration issues.</span></span> <span data-ttu-id="54eda-284">可以指定 **-SHOWEVENTS** 以查看 **ssbdiagnose**遇到的错误事件。</span><span class="sxs-lookup"><span data-stu-id="54eda-284">You can specify **-SHOWEVENTS** to see the error events encountered by **ssbdiagnose**.</span></span>  
  
## <a name="issues-reported-by-ssbdiagnose"></a><span data-ttu-id="54eda-285">ssbdiagnose 报告的问题</span><span class="sxs-lookup"><span data-stu-id="54eda-285">Issues Reported by ssbdiagnose</span></span>  
 <span data-ttu-id="54eda-286">**ssbdiagnose** 报告三类问题。</span><span class="sxs-lookup"><span data-stu-id="54eda-286">**ssbdiagnose** reports three classes of issues.</span></span> <span data-ttu-id="54eda-287">在 XML 输出文件中，每类问题都作为 Issue 元素的一个单独类型来报告。</span><span class="sxs-lookup"><span data-stu-id="54eda-287">In the XML output file, each class of issue is reported as a separate type of the Issue element.</span></span> <span data-ttu-id="54eda-288">**ssbdiagnose** 报告的三类问题如下：</span><span class="sxs-lookup"><span data-stu-id="54eda-288">The three types of issues reported by **ssbdiagnose** are as follows:</span></span>  
  
 <span data-ttu-id="54eda-289">**诊断**</span><span class="sxs-lookup"><span data-stu-id="54eda-289">**Diagnosis**</span></span>  
 <span data-ttu-id="54eda-290">报告配置问题。</span><span class="sxs-lookup"><span data-stu-id="54eda-290">Reports a configuration issue.</span></span> <span data-ttu-id="54eda-291">这包括运行 **CONFIGURATION** 报告时或在 **RUNTIME** 报告的配置阶段中发现的问题。</span><span class="sxs-lookup"><span data-stu-id="54eda-291">This includes issues found either a **CONFIGURATION** report is running, or during the configuration phase of a **RUNTIME** report.</span></span> <span data-ttu-id="54eda-292">**ssbdiagnose** 对每个配置问题只报告一次。</span><span class="sxs-lookup"><span data-stu-id="54eda-292">**ssbdiagnose** reports each configuration issue one time.</span></span>  
  
 <span data-ttu-id="54eda-293">**事件**</span><span class="sxs-lookup"><span data-stu-id="54eda-293">**Event**</span></span>  
 <span data-ttu-id="54eda-294">报告 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 事件，该事件指示 **RUNTIME** 报告期间监视的会话所遇到的问题。</span><span class="sxs-lookup"><span data-stu-id="54eda-294">Reports a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] event that indicates a problem was encountered by a conversation being monitored during a **RUNTIME** report.</span></span> <span data-ttu-id="54eda-295">**ssbdiagnose** 在每次生成事件时都进行报告。</span><span class="sxs-lookup"><span data-stu-id="54eda-295">**ssbdiagnose** reports events every time they are generated.</span></span> <span data-ttu-id="54eda-296">如果多个会话都遇到相同问题，则会多次报告相关事件。</span><span class="sxs-lookup"><span data-stu-id="54eda-296">Events can be reported multiple times if several conversations encounter the problem.</span></span>  
  
 <span data-ttu-id="54eda-297">问题</span><span class="sxs-lookup"><span data-stu-id="54eda-297">**Problem**</span></span>  
 <span data-ttu-id="54eda-298">报告导致 **ssbdiagnose** 无法完成配置分析或无法监视会话的问题。</span><span class="sxs-lookup"><span data-stu-id="54eda-298">Reports an issue that is preventing **ssbdiagnose** from completing a configuration analysis or from monitoring conversations.</span></span>  
  
## <a name="sqlcmd-environment-variables"></a><span data-ttu-id="54eda-299">sqlcmd 环境变量</span><span class="sxs-lookup"><span data-stu-id="54eda-299">sqlcmd Environment Variables</span></span>  
 <span data-ttu-id="54eda-300">**ssbdiagnose** 实用工具支持 **sqlcmd** 实用工具也使用的 SQLCMDSERVER、SQLCMDUSER、SQLCMDPASSWORD 和 SQLCMDLOGINTIMOUT 环境变量。</span><span class="sxs-lookup"><span data-stu-id="54eda-300">The **ssbdiagnose** utility supports the SQLCMDSERVER, SQLCMDUSER, SQLCMDPASSWORD, and SQLCMDLOGINTIMOUT environment variables that are also used by the **sqlcmd** utility.</span></span> <span data-ttu-id="54eda-301">设置环境变量可以使用命令提示 SET 命令，也可以使用通过 **sqlcmd** 运行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本中的 **setvar**命令。</span><span class="sxs-lookup"><span data-stu-id="54eda-301">You can set the environment variables either by using the command prompt SET command, or by using the **setvar** command in [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts that you run by using **sqlcmd**.</span></span> <span data-ttu-id="54eda-302">有关如何在 **sqlcmd** 中使用 **setvar**的详细信息，请参阅 [将 sqlcmd 与脚本变量结合使用](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="54eda-302">For more information about how to use **setvar** in **sqlcmd**, see [Use sqlcmd with Scripting Variables](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="54eda-303">权限</span><span class="sxs-lookup"><span data-stu-id="54eda-303">Permissions</span></span>  
 <span data-ttu-id="54eda-304">在每个 **connectionoptions** 子句中，通过 **-E** 或 **-U** 指定的登录名必须是 **-S** 所指定实例中 **sysadmin**固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="54eda-304">In each **connectionoptions** clause, the login specified with either **-E** or **-U** must be a member of the **sysadmin** fixed-server role in the instance specified in **-S**.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="54eda-305">示例</span><span class="sxs-lookup"><span data-stu-id="54eda-305">Examples</span></span>  
 <span data-ttu-id="54eda-306">本节包含在命令提示符下使用 **ssbdiagnose** 的示例。</span><span class="sxs-lookup"><span data-stu-id="54eda-306">This section contains examples of using **ssbdiagnose** at a command prompt.</span></span>  
  
### <a name="a-checking-the-configuration-of-two-services-in-the-same-database"></a><span data-ttu-id="54eda-307">A.</span><span class="sxs-lookup"><span data-stu-id="54eda-307">A.</span></span> <span data-ttu-id="54eda-308">检查同一数据库中两个服务的配置</span><span class="sxs-lookup"><span data-stu-id="54eda-308">Checking the Configuration of Two Services in the Same Database</span></span>  
 <span data-ttu-id="54eda-309">下例说明当符合以下条件时如何请求配置报告：</span><span class="sxs-lookup"><span data-stu-id="54eda-309">The following example shows how to request a configuration report when the following are true;</span></span>  
  
-   <span data-ttu-id="54eda-310">发起方服务和目标服务在同一个数据库中。</span><span class="sxs-lookup"><span data-stu-id="54eda-310">The initiator and target service are in the same database.</span></span>  
  
-   <span data-ttu-id="54eda-311">该数据库在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的默认实例中。</span><span class="sxs-lookup"><span data-stu-id="54eda-311">The database is in the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="54eda-312">该实例在运行 **ssbdiagnose** 的计算机上。</span><span class="sxs-lookup"><span data-stu-id="54eda-312">The instances is on the same computer on which **ssbdiagnose** is run.</span></span>  
  
 <span data-ttu-id="54eda-313">**ssbdiagnose** 实用工具将报告使用 DEFAULT 协定的配置，因为没有指定 ON CONTRACT。</span><span class="sxs-lookup"><span data-stu-id="54eda-313">The **ssbdiagnose** utility reports the configuration that uses the DEFAULT contract because ON CONTRACT is not specified.</span></span>  
  
```  
ssbdiagnose -E -d MyDatabase CONFIGURATION FROM SERVICE /test/initiator TO SERVICE /test/target  
```  
  
### <a name="b-checking-the-configuration-of-two-services-on-separate-computers-that-use-one-login"></a><span data-ttu-id="54eda-314">B.</span><span class="sxs-lookup"><span data-stu-id="54eda-314">B.</span></span> <span data-ttu-id="54eda-315">检查在不同计算机上使用一个登录名的两个服务的配置</span><span class="sxs-lookup"><span data-stu-id="54eda-315">Checking the Configuration of Two Services on Separate Computers That Use One Login</span></span>  
 <span data-ttu-id="54eda-316">下例说明在以下情况下如何请求配置报告：发起方服务和目标服务在不同计算机上，但可使用相同的 Windows 身份验证登录名进行访问。</span><span class="sxs-lookup"><span data-stu-id="54eda-316">The following example shows how to request a configuration report when the initiator and target service are on separate computers, but can be accessed by using the same Windows Authentication login.</span></span>  
  
```  
ssbdiagnose -E CONFIGURATION FROM SERVICE /text/initiator -S InitiatorComputer -d InitiatorDatabase TO SERVICE /test/target -S TargetComputer -d TargetDatabase ON CONTRACT TestContract  
```  
  
### <a name="c-checking-the-configuration-of-two-services-on-separate-computers-that-use-separate-logins"></a><span data-ttu-id="54eda-317">C.</span><span class="sxs-lookup"><span data-stu-id="54eda-317">C.</span></span> <span data-ttu-id="54eda-318">检查在不同计算机上使用不同登录名的两个服务的配置</span><span class="sxs-lookup"><span data-stu-id="54eda-318">Checking the Configuration of Two Services on Separate Computers That Use Separate Logins</span></span>  
 <span data-ttu-id="54eda-319">下例说明在以下情况下如何请求配置报告：发起方服务和目标服务在不同计算机上，且每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例需要不同的 [!INCLUDE[ssDE](../../includes/ssde-md.md)]身份验证登录名。</span><span class="sxs-lookup"><span data-stu-id="54eda-319">The following example shows how to request a configuration report when the initiator and target service are on separate computers, and separate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication logins are required for each instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
```  
ssbdiagnose CONFIGURATION FROM SERVICE /text/initiator   
-S InitiatorComputer -U InitiatorLogin -p !wEx23Dvb   
-d InitiatorDatabase TO SERVICE /test/target -S TargetComputer   
-U TargetLogin -p ER!49jiy -d TargetDatabase ON CONTRACT TestContract  
```  
  
### <a name="d-checking-mirrored-service-configurations-on-separate-computers-with-anonymous-encryption"></a><span data-ttu-id="54eda-320">D.</span><span class="sxs-lookup"><span data-stu-id="54eda-320">D.</span></span> <span data-ttu-id="54eda-321">检查不同计算机上包括匿名加密情况在内的镜像服务配置</span><span class="sxs-lookup"><span data-stu-id="54eda-321">Checking Mirrored Service Configurations on Separate Computers With Anonymous Encryption</span></span>  
 <span data-ttu-id="54eda-322">下例说明在以下情况下如何请求配置报告：发起方服务和目标服务在不同计算机上，且发起方镜像到命名实例。</span><span class="sxs-lookup"><span data-stu-id="54eda-322">The following example shows how to request a configuration report when the initiator and target service are on separate computers and the initiator is mirrored to a named instance.</span></span> <span data-ttu-id="54eda-323">该报告还检查服务是否配置为使用匿名加密。</span><span class="sxs-lookup"><span data-stu-id="54eda-323">The report also verifies that the services are configured to use anonymous encryption.</span></span>  
  
```  
ssbdiagnose -E CONFIGURATION FROM SERVICE /text/initiator   
-S InitiatorComputer -d InitiatorDatabase MIRROR   
-S MirrorComputer/MirrorInstance TO SERVICE /test/target   
-S TargetComputer -d TargetDatabase ON CONTRACT TestContract ENCRYPTION ANONYMOUS  
```  
  
### <a name="e-checking-the-configuration-of-two-contracts"></a><span data-ttu-id="54eda-324">E.</span><span class="sxs-lookup"><span data-stu-id="54eda-324">E.</span></span> <span data-ttu-id="54eda-325">检查两个约定的配置</span><span class="sxs-lookup"><span data-stu-id="54eda-325">Checking the Configuration of Two Contracts</span></span>  
 <span data-ttu-id="54eda-326">下例说明当符合以下条件时如何生成请求配置报告的命令文件：</span><span class="sxs-lookup"><span data-stu-id="54eda-326">The following example shows how to build a command file that requests configuration reports when the following are true:</span></span>  
  
-   <span data-ttu-id="54eda-327">发起方服务和目标服务在同一个数据库中。</span><span class="sxs-lookup"><span data-stu-id="54eda-327">The initiator and target service are in the same database.</span></span>  
  
-   <span data-ttu-id="54eda-328">该数据库在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的默认实例中。</span><span class="sxs-lookup"><span data-stu-id="54eda-328">The database is in the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="54eda-329">该实例在运行 **ssbdiagnose** 的计算机上。</span><span class="sxs-lookup"><span data-stu-id="54eda-329">The instance is on the same computer on which **ssbdiagnose** is run.</span></span>  
  
 <span data-ttu-id="54eda-330">**ssbdiagnose** 每次运行时都将报告相同服务间不同协定的配置。</span><span class="sxs-lookup"><span data-stu-id="54eda-330">Each time **ssbdiagnose** is run it reports the configuration for a different contract between the same services.</span></span>  
  
```  
ssbdiagnose -E -d MyDatabase CONFIGURATION FROM SERVICE   
/test/initiator TO SERVICE /test/target ON CONTRACT PayRaiseContract  
ssbdiagnose -E -d MyDatabase CONFIGURATION FROM SERVICE /test/initiator   
TO SERVICE /test/target ON CONTRACT PromotionContract  
```  
  
### <a name="f-monitor-the-status-of-a-specific-conversation-on-the-local-computer-with-a-time-out"></a><span data-ttu-id="54eda-331">F.</span><span class="sxs-lookup"><span data-stu-id="54eda-331">F.</span></span> <span data-ttu-id="54eda-332">监视本地计算机上特定会话的状态，并设置超时</span><span class="sxs-lookup"><span data-stu-id="54eda-332">Monitor the status of a specific conversation on the local computer with a time out</span></span>  
 <span data-ttu-id="54eda-333">下例说明如何监视特定会话，其中发起方服务和目标服务在同一数据库中，该数据库在运行 **ssbdiagnose**的计算机的默认实例中。</span><span class="sxs-lookup"><span data-stu-id="54eda-333">The following example shows how to monitor a specific conversation where the initiator and target services are in the same database in the default instance of the same computer that is running **ssbdiagnose**.</span></span> <span data-ttu-id="54eda-334">超时间隔设置为 20 秒。</span><span class="sxs-lookup"><span data-stu-id="54eda-334">The time-out interval is set to 20 seconds.</span></span>  
  
```  
ssbdiagnose -E -d TestDatabase RUNTIME -ID D68D77A9-B1CF-41BF-A5CE-279ABCAB140D -TIMEOUT 20  
```  
  
### <a name="g-monitor-the-status-of-a-conversation-that-spans-two-computers"></a><span data-ttu-id="54eda-335">G.</span><span class="sxs-lookup"><span data-stu-id="54eda-335">G.</span></span> <span data-ttu-id="54eda-336">监视跨越两台计算机的会话的状态</span><span class="sxs-lookup"><span data-stu-id="54eda-336">Monitor the status of a conversation that spans two computers</span></span>  
 <span data-ttu-id="54eda-337">下例说明如何监视特定会话，其中发起方服务和目标服务在不同计算机上。</span><span class="sxs-lookup"><span data-stu-id="54eda-337">The following example shows how to monitor a specific conversation where the initiator and target services are on separate computers.</span></span>  
  
```  
ssbdiagnose RUNTIME -ID D68D77A9-B1CF-41BF-A5CE-279ABCAB140D   
-TIMEOUT 10 CONNECT TO -E -S InitiatorComputer/InitiatorInstance   
-d InitiatorDatabase CONNECT TO -E -S TargetComputer/TargetInstance   
-d TargetDatabase  
```  
  
### <a name="h-monitor-the-status-of-a-conversation-in-two-databases-in-the-same-instance"></a><span data-ttu-id="54eda-338">H.</span><span class="sxs-lookup"><span data-stu-id="54eda-338">H.</span></span> <span data-ttu-id="54eda-339">监视同一实例的两个数据库中的会话的状态</span><span class="sxs-lookup"><span data-stu-id="54eda-339">Monitor the status of a conversation in two databases in the same instance</span></span>  
 <span data-ttu-id="54eda-340">下例说明如何监视特定会话，其中发起方服务和目标服务在同一 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的不同数据库中。</span><span class="sxs-lookup"><span data-stu-id="54eda-340">The following example shows how to monitor a specific conversation where the initiator and target services are in separate databases in the same instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="54eda-341">该示例使用 **baseconnectionoptions** 来指定实例和登录信息，使用两个 CONNECT TO 子句来指定数据库。</span><span class="sxs-lookup"><span data-stu-id="54eda-341">The example uses the **baseconnectionoptions** to specify the instance and login information, and two CONNECT TO clauses to specify the databases.</span></span> <span data-ttu-id="54eda-342">指定了 -SHOWEVENTS，因此所有运行时事件都包含在报告输出中。</span><span class="sxs-lookup"><span data-stu-id="54eda-342">-SHOWEVENTS is specified so that all runtime events are included in the report output.</span></span>  
  
```  
ssbdiagnose -E -S TestComputer/DevTestInstance RUNTIME -SHOWEVENTS   
-ID 5094d4a7-e38c-4c37-da37-1d58b1cb8455 -TIMEOUT 10 CONNECT TO   
-d InitiatorDatabase CONNECT TO -d TargetDatabase  
```  
  
### <a name="i-monitor-the-status-of-two-conversations-between-two-databases"></a><span data-ttu-id="54eda-343">I.</span><span class="sxs-lookup"><span data-stu-id="54eda-343">I.</span></span> <span data-ttu-id="54eda-344">监视两个数据库间的两个会话的状态</span><span class="sxs-lookup"><span data-stu-id="54eda-344">Monitor the status of two conversations between two databases</span></span>  
 <span data-ttu-id="54eda-345">下例说明如何监视两个会话，其中发起方服务和目标服务在同一 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的不同数据库中。</span><span class="sxs-lookup"><span data-stu-id="54eda-345">The following example shows how to monitor two conversations where the initiator and target services are in separate databases in the same instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="54eda-346">该示例使用 **baseconnectionoptions** 来指定实例和登录信息，使用两个 CONNECT TO 子句来指定数据库。</span><span class="sxs-lookup"><span data-stu-id="54eda-346">The example uses the **baseconnectionoptions** to specify the instance and login information, and two CONNECT TO clauses to specify the databases.</span></span>  
  
```  
ssbdiagnose -E -S TestComputer/DevTestInstance RUNTIME   
-ID 5094d4a7-e38c-4c37-da37-1d58b1cb8455   
-ID 9b293be9-226b-4e22-e169-1d2c2c15be86 -TIMEOUT 10 CONNECT TO   
-d InitiatorDatabase CONNECT TO -d TargetDatabase  
```  
  
### <a name="j-monitor-the-status-of-all-conversations-between-two-databases"></a><span data-ttu-id="54eda-347">J.</span><span class="sxs-lookup"><span data-stu-id="54eda-347">J.</span></span> <span data-ttu-id="54eda-348">监视两个数据库间的所有会话的状态</span><span class="sxs-lookup"><span data-stu-id="54eda-348">Monitor the status of all conversations between two databases</span></span>  
 <span data-ttu-id="54eda-349">下例说明如何监视同一 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例中两个数据库间的所有会话。</span><span class="sxs-lookup"><span data-stu-id="54eda-349">The following example shows how to monitor all the conversation between two databases in the same instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="54eda-350">该示例使用 **baseconnectionoptions** 来指定实例和登录信息，使用两个 CONNECT TO 子句来指定数据库。</span><span class="sxs-lookup"><span data-stu-id="54eda-350">The example uses the **baseconnectionoptions** to specify the instance and login information, and two CONNECT TO clauses to specify the databases.</span></span>  
  
```  
ssbdiagnose -E -S TestComputer/DevTestInstance RUNTIME   
-TIMEOUT 10 CONNECT TO -d InitiatorDatabase CONNECT TO   
-d TargetDatabase  
```  
  
### <a name="k-ignore-specific-errors"></a><span data-ttu-id="54eda-351">K.</span><span class="sxs-lookup"><span data-stu-id="54eda-351">K.</span></span> <span data-ttu-id="54eda-352">忽略特定错误</span><span class="sxs-lookup"><span data-stu-id="54eda-352">Ignore Specific Errors</span></span>  
 <span data-ttu-id="54eda-353">下例说明如何忽略测试系统中当前激活配置方式中存在的已知错误（303 和 304）。</span><span class="sxs-lookup"><span data-stu-id="54eda-353">The following example shows how to ignore known errors (303 and 304) in how activation is currently configured in a test system.</span></span>  
  
```  
ssbdiagnose -IGNORE 303 -IGNORE 304 -E -d TestDatabase   
CONFIGURATION FROM SERVICE /test/initiator TO SERVICE /test/target   
ON CONTRACT TextContract  
```  
  
### <a name="l-redirecting-ssbdiagnose-xml-output"></a><span data-ttu-id="54eda-354">L.</span><span class="sxs-lookup"><span data-stu-id="54eda-354">L.</span></span> <span data-ttu-id="54eda-355">重定向 ssbdiagnose XML 输出</span><span class="sxs-lookup"><span data-stu-id="54eda-355">Redirecting ssbdiagnose XML Output</span></span>  
 <span data-ttu-id="54eda-356">下例说明如何请求 **ssbdiagnose** 将其输出生成为重定向到一个文件的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="54eda-356">The following example shows how to request that **ssbdiagnose** generate its output as an XML file that is redirected to a file.</span></span> <span data-ttu-id="54eda-357">然后应用程序可打开 TestDiag.xml 文件以分析或报告 **ssbdiagnose** XML 文件。</span><span class="sxs-lookup"><span data-stu-id="54eda-357">The TestDiag.xml file can then be opened by an application to analyze or report **ssbdiagnose** XML files.</span></span> <span data-ttu-id="54eda-358">或者，您还可以在常规 XML 编辑器（如 XML Notepad）中查看该 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="54eda-358">Or, you can view it from a general XML editor such as XML Notepad.</span></span>  
  
```  
ssbdiagnose -XML -E -d MyDatabase CONFIGURATION FROM SERVICE   
/test/initiator TO SERVICE /test/target > c:\MyDiagnostics\TestDiag.xml  
```  
  
### <a name="m-using-an-environment-variable"></a><span data-ttu-id="54eda-359">M.</span><span class="sxs-lookup"><span data-stu-id="54eda-359">M.</span></span> <span data-ttu-id="54eda-360">使用环境变量</span><span class="sxs-lookup"><span data-stu-id="54eda-360">Using an Environment Variable</span></span>  
 <span data-ttu-id="54eda-361">以下示例首先设置 SQLCMDSERVER 环境变量使其包含服务器名称，然后运行未指定 **-S** 的 **ssbdiagnose**。</span><span class="sxs-lookup"><span data-stu-id="54eda-361">The following example first sets the SQLCMDSERVER environment variable to hold the server name, and then runs **ssbdiagnose** without specifying **-S**.</span></span>  
  
```  
SET SQLCMDSERVER=MyComputer  
ssbdiagnose -XML -E -d MyDatabase CONFIGURATION FROM SERVICE   
/test/initiator TO SERVICE /test/target  
```  
  
## <a name="see-also"></a><span data-ttu-id="54eda-362">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54eda-362">See Also</span></span>  
 <span data-ttu-id="54eda-363">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span><span class="sxs-lookup"><span data-stu-id="54eda-363">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span></span>  
 <span data-ttu-id="54eda-364">[BEGIN DIALOG CONVERSATION (Transact-SQL)](/sql/t-sql/statements/begin-dialog-conversation-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54eda-364">[BEGIN DIALOG CONVERSATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/begin-dialog-conversation-transact-sql) </span></span>  
 <span data-ttu-id="54eda-365">[CREATE BROKER PRIORITY (Transact-SQL)](/sql/t-sql/statements/create-broker-priority-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54eda-365">[CREATE BROKER PRIORITY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-broker-priority-transact-sql) </span></span>  
 <span data-ttu-id="54eda-366">[CREATE CERTIFICATE (Transact-SQL)](/sql/t-sql/statements/create-certificate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54eda-366">[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql) </span></span>  
 <span data-ttu-id="54eda-367">[CREATE CONTRACT (Transact-SQL)](/sql/t-sql/statements/create-contract-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54eda-367">[CREATE CONTRACT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-contract-transact-sql) </span></span>  
 <span data-ttu-id="54eda-368">[CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54eda-368">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="54eda-369">[CREATE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/create-master-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54eda-369">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span></span>  
 <span data-ttu-id="54eda-370">[CREATE MESSAGE TYPE (Transact-SQL)](/sql/t-sql/statements/create-message-type-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54eda-370">[CREATE MESSAGE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-message-type-transact-sql) </span></span>  
 <span data-ttu-id="54eda-371">[CREATE QUEUE (Transact SQL)](/sql/t-sql/statements/create-queue-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54eda-371">[CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) </span></span>  
 <span data-ttu-id="54eda-372">[CREATE REMOTE SERVICE BINDING (Transact-SQL)](/sql/t-sql/statements/create-remote-service-binding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54eda-372">[CREATE REMOTE SERVICE BINDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-remote-service-binding-transact-sql) </span></span>  
 <span data-ttu-id="54eda-373">[CREATE ROUTE (Transact SQL)](/sql/t-sql/statements/create-route-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54eda-373">[CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql) </span></span>  
 <span data-ttu-id="54eda-374">[CREATE SERVICE (Transact SQL)](/sql/t-sql/statements/create-service-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54eda-374">[CREATE SERVICE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-service-transact-sql) </span></span>  
 <span data-ttu-id="54eda-375">[RECEIVE (Transact-SQL)](/sql/t-sql/statements/receive-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54eda-375">[RECEIVE &#40;Transact-SQL&#41;](/sql/t-sql/statements/receive-transact-sql) </span></span>  
 <span data-ttu-id="54eda-376">[sys.transmission_queue (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-transmission-queue-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54eda-376">[sys.transmission_queue &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-transmission-queue-transact-sql) </span></span>  
 <span data-ttu-id="54eda-377">[sys.conversation_endpoints (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54eda-377">[sys.conversation_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql) </span></span>  
 [<span data-ttu-id="54eda-378">sys.conversation_groups (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="54eda-378">sys.conversation_groups &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-conversation-groups-transact-sql)  
  
  
