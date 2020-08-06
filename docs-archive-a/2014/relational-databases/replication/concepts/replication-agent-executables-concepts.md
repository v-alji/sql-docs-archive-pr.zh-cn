---
title: 复制代理可执行文件概念 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- programming interfaces [SQL Server replication]
- programming [SQL Server replication], agents
- replication [SQL Server], agents and profiles
- agents [SQL Server replication], executables
- command prompt [SQL Server replication]
ms.assetid: cba476df-d4ea-44c9-bb86-81488971e328
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 73f9fe0d1a98fa1afc813cd113dcced685b4f98a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693765"
---
# <a name="replication-agent-executables-concepts"></a><span data-ttu-id="f7b3e-102">复制代理可执行文件概念</span><span class="sxs-lookup"><span data-stu-id="f7b3e-102">Replication Agent Executables Concepts</span></span>
  <span data-ttu-id="f7b3e-103">可以使用下列方法以编程方式控制复制代理：</span><span class="sxs-lookup"><span data-stu-id="f7b3e-103">Replication agents can be controlled programmatically in the following ways:</span></span>  
  
-   <span data-ttu-id="f7b3e-104">使用 <xref:Microsoft.SqlServer.Replication> 命名空间中的托管代理编程接口。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-104">Using the managed agent programming interfaces in the <xref:Microsoft.SqlServer.Replication> Namespace.</span></span>  
  
-   <span data-ttu-id="f7b3e-105">在命令提示符下使用提供的一组参数来调用代理可执行文件。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-105">Invoking agent executable files from the command prompt with a supplied set of parameters.</span></span>  
  
 <span data-ttu-id="f7b3e-106">如果直接从命令提示符调用复制代理，则可以从批处理文件中的命令行脚本，以编程方式访问代理。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-106">Directly invoking replication agents from the command prompt enables agents to be programmatically accessed from command-line scripting in batch files.</span></span> <span data-ttu-id="f7b3e-107">从命令提示符调用代理时，代理在调用代理或启动批处理文件的用户的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 安全帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-107">When an agent is invoked from the command prompt, it runs under the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows security account of the user that invoked the agent or started the batch file.</span></span>  
  
 <span data-ttu-id="f7b3e-108">可使用可执行文件运行下列复制代理的实例。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-108">Instances of the following replication agents can be run using executable files.</span></span>  
  
-   [<span data-ttu-id="f7b3e-109">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="f7b3e-109">Replication Distribution Agent</span></span>](../agents/replication-distribution-agent.md)  
  
-   [<span data-ttu-id="f7b3e-110">复制日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="f7b3e-110">Replication Log Reader Agent</span></span>](../agents/replication-log-reader-agent.md)  
  
-   [<span data-ttu-id="f7b3e-111">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="f7b3e-111">Replication Merge Agent</span></span>](../agents/replication-merge-agent.md)  
  
-   [<span data-ttu-id="f7b3e-112">复制队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="f7b3e-112">Replication Queue Reader Agent</span></span>](../agents/replication-queue-reader-agent.md)  
  
-   [<span data-ttu-id="f7b3e-113">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="f7b3e-113">Replication Snapshot Agent</span></span>](../agents/replication-snapshot-agent.md)  
  
 <span data-ttu-id="f7b3e-114">调用复制代理时，您可以使用性能配置文件，以自动向代理可执行文件传递一组已定义的参数。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-114">When invoking replication agents, you can use performance profiles to automatically pass a defined set of parameters to the agent executable.</span></span> <span data-ttu-id="f7b3e-115">有关详细信息，请参阅 [Replication Agent Profiles](../agents/replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-115">For more information, see [Replication Agent Profiles](../agents/replication-agent-profiles.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f7b3e-116">示例</span><span class="sxs-lookup"><span data-stu-id="f7b3e-116">Examples</span></span>  
 <span data-ttu-id="f7b3e-117">下面的示例说明如何从命令提示符调用复制代理。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-117">The following examples show how to invoke replication agents from the command prompt.</span></span> <span data-ttu-id="f7b3e-118">复制代理也可以使用复制管理对象 (RMO) 来调用。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-118">Replication agents can also be invoked using Replication Management Objects (RMO).</span></span> <span data-ttu-id="f7b3e-119">有关详细信息，请参阅[同步订阅（复制）](../synchronize-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-119">For more information, see [Synchronize Subscriptions &#40;Replication&#41;](../synchronize-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7b3e-120">为便于阅读，这些示例中添加了换行符。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-120">Line breaks in these examples were added to improve readability.</span></span> <span data-ttu-id="f7b3e-121">但在批处理文件中，命令必须位于一行中。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-121">In a batch file, commands must be made in a single line.</span></span>  
  
### <a name="running-the-snapshot-agent"></a><span data-ttu-id="f7b3e-122">运行快照代理</span><span class="sxs-lookup"><span data-stu-id="f7b3e-122">Running the Snapshot Agent</span></span>  
 <span data-ttu-id="f7b3e-123">此示例批处理文件从命令提示符调用快照代理，以生成 **AdvWorksSalesOrdersMerge** 发布的快照。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-123">This example batch file invokes the Snapshot Agent from the command prompt to generate a snapshot for the **AdvWorksSalesOrdersMerge** publication.</span></span>  
  
```  
REM -- Declare variables  
SET Publisher=%InstanceName%;  
SET PublicationDB=AdventureWorks2012;   
SET Publication=AdvWorksSalesOrdersMerge;   
  
REM --Start the Snapshot Agent to generate the snapshot for AdvWorksSalesOrdersMerge.  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %Publication%   
-Publisher %Publisher% -Distributor %Publisher% -PublisherDB %PublicationDB%   
-ReplicationType 2 -OutputVerboseLevel 1 -DistributorSecurityMode 1 ;  
  
```  
  
### <a name="running-the-distribution-agent"></a><span data-ttu-id="f7b3e-124">运行分发代理</span><span class="sxs-lookup"><span data-stu-id="f7b3e-124">Running the Distribution Agent</span></span>  
 <span data-ttu-id="f7b3e-125">此示例批处理文件从命令提示符调用分发代理，从而不断地从 **AdvWorksProductTran** 发布向推送订阅服务器复制更改。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-125">This example batch file invokes the Distribution Agent from the command prompt to continuously replicate changes from the **AdvWorksProductTran** publication to a push subscriber.</span></span>  
  
```  
REM -- Declare the variables.  
SET Publisher=%instancename%;  
SET Subscriber=%instancename%;  
SET PublicationDB=AdventureWorks2012;  
SET SubscriptionDB=AdventureWorks2012Replica;   
SET Publication=AdvWorksProductsTran;  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4 ;  
  
```  
  
### <a name="running-the-merge-agent"></a><span data-ttu-id="f7b3e-126">运行合并代理</span><span class="sxs-lookup"><span data-stu-id="f7b3e-126">Running the Merge Agent</span></span>  
 <span data-ttu-id="f7b3e-127">此示例批处理文件从命令提示符调用合并代理，以将请求订阅与 **AdvWorksSalesOrdersMerge** 发布同步。</span><span class="sxs-lookup"><span data-stu-id="f7b3e-127">This example batch file invokes the Merge Agent from the command prompt to synchronize a pull subscription to the **AdvWorksSalesOrdersMerge** publication.</span></span>  
  
```  
REM -- Declare the variables.  
SET Publisher=%instancename%;  
SET Subscriber=%instancename%;  
SET PublicationDB=AdventureWorks2012;  
SET SubscriptionDB=AdventureWorks2012Replica;   
SET Publication=AdvWorksSalesOrdersMerge;  
  
REM --Start the Merge Agent with concurrent upload and download processes.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE" -Publication %Publication%    
-Publisher %Publisher%  -Subscriber  %Subscriber%  -Distributor %Publisher%    
-PublisherDB %PublicationDB%  -SubscriberDB %SubscriptionDB% -PublisherSecurityMode 1    
-OutputVerboseLevel 2  -SubscriberSecurityMode 1  -SubscriptionType 1 -DistributorSecurityMode 1    
-Validate 3  -ParallelUploadDownload 1 ;  
  
```  
  
  
