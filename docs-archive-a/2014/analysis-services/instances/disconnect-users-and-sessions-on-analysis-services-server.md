---
title: 断开 Analysis Services Server 上的用户和会话 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ending user activity [Analysis Services]
- connections [Analysis Services]
- sessions [Analysis Services]
ms.assetid: 3b0145a2-f21d-4dd0-a09e-83afeb2ff4a9
author: minewiskan
ms.author: owend
ms.openlocfilehash: bac20b663b0a65902c70e7a3c3bfe3f27b7bf061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689108"
---
# <a name="disconnect-users-and-sessions-on-analysis-services-server"></a><span data-ttu-id="e2891-102">断开 Analysis Services 服务器上用户和会话的连接</span><span class="sxs-lookup"><span data-stu-id="e2891-102">Disconnect Users and Sessions on Analysis Services Server</span></span>
  <span data-ttu-id="e2891-103">作为工作负荷管理的一部分， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理员可能需要结束用户活动。</span><span class="sxs-lookup"><span data-stu-id="e2891-103">An administrator of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] may want to end user activity as part of workload management.</span></span> <span data-ttu-id="e2891-104">可以通过取消会话和连接来完成这一任务。</span><span class="sxs-lookup"><span data-stu-id="e2891-104">You do this by canceling sessions and connections.</span></span> <span data-ttu-id="e2891-105">会话可以在运行查询时隐式自动形成，也可以在创建会话时由管理员显式命名。</span><span class="sxs-lookup"><span data-stu-id="e2891-105">Sessions can be formed automatically when a query is run (implicit), or named at the time of creation by the administrator (explicit).</span></span> <span data-ttu-id="e2891-106">连接是开放的管道，可以通过连接运行查询。</span><span class="sxs-lookup"><span data-stu-id="e2891-106">Connections are open conduits over which queries can be run.</span></span> <span data-ttu-id="e2891-107">会话和连接均可在处于活动状态时结束。</span><span class="sxs-lookup"><span data-stu-id="e2891-107">Both sessions and connections can be ended while they are active.</span></span> <span data-ttu-id="e2891-108">例如，如果会话处理时间过长，或者对正在执行的命令是否被正确写入产生了怀疑，管理员可能要结束对会话的处理。</span><span class="sxs-lookup"><span data-stu-id="e2891-108">For example, an administrator may want to end processing for a session if the processing is taking too long or if some doubt has arisen as to whether the command being executed was written correctly.</span></span>  
  
## <a name="ending-sessions-and-connections"></a><span data-ttu-id="e2891-109">结束会话和连接</span><span class="sxs-lookup"><span data-stu-id="e2891-109">Ending Sessions and Connections</span></span>  
 <span data-ttu-id="e2891-110">若要管理会话和连接，您可以使用动态管理视图 (DMV) 和 XMLA：</span><span class="sxs-lookup"><span data-stu-id="e2891-110">To manage sessions and connections, you can use Dynamic Management Views (DMVs) and XMLA:</span></span>  
  
1.  <span data-ttu-id="e2891-111">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到 Analysis Services 实例。</span><span class="sxs-lookup"><span data-stu-id="e2891-111">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an Analysis Services instance.</span></span>  
  
2.  <span data-ttu-id="e2891-112">将以下任一个 DMV 查询粘贴到 MDX 查询窗口中，以获取当前正在执行的所有会话、连接和命令的列表：</span><span class="sxs-lookup"><span data-stu-id="e2891-112">Paste any one of the following DMV queries in an MDX query window to get a list of all sessions, connections, and commands that are currently executing:</span></span>  
  
     `Select * from $System.Discover_Sessions`  
  
     `Select * from $System.Discover_Connections`  
  
     `Select * from $System.Discover_Commands`  
  
3.  <span data-ttu-id="e2891-113">按 F5 执行该查询。</span><span class="sxs-lookup"><span data-stu-id="e2891-113">Press F5 to execute the query.</span></span>  
  
     <span data-ttu-id="e2891-114">DMV 查询以易于读取和复制的表格结果集返回会话和连接信息。</span><span class="sxs-lookup"><span data-stu-id="e2891-114">The DMV query returns session and connection information in a tabular result set that is easier read and copy from.</span></span>  
  
 <span data-ttu-id="e2891-115">保持查询窗口处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="e2891-115">Keep the query window open.</span></span> <span data-ttu-id="e2891-116">在下一步骤中，你将希望返回至本页以复制你要断开连接的会话的 SPID。</span><span class="sxs-lookup"><span data-stu-id="e2891-116">In the next step, you will want to return to this page to copy the SPIDs of the session you want to disconnect.</span></span>  
  
 <span data-ttu-id="e2891-117">若要结束会话，请打开另一个 XMLA 查询窗口。</span><span class="sxs-lookup"><span data-stu-id="e2891-117">To end a session, open a second XMLA query window.</span></span>  
  
1.  <span data-ttu-id="e2891-118">将以下语法粘贴到 MDX 查询窗口中，用从上一步中复制的有效值替换 ConnectionID、SessionID 或 SPID 占位符。</span><span class="sxs-lookup"><span data-stu-id="e2891-118">Paste the following syntax into an MDX query window, replacing the ConnectionID, SessionID, or SPID placeholder with a valid value copied from the previous step.</span></span>  
  
    ```  
    <Cancel xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  
       <ConnectionID>111</ConnectionID>  
       <SessionID>222</SessionID>  
       <SPID>333</SPID>  
  
    <CancelAssociated>1</CancelAssociated>  
    </Cancel>  
  
    ```  
  
2.  <span data-ttu-id="e2891-119">按 F5 执行取消命令。</span><span class="sxs-lookup"><span data-stu-id="e2891-119">Press F5 to execute the cancel command.</span></span>  
  
 <span data-ttu-id="e2891-120">结束连接将取消所有会话和 SPID，从而结束主机会话。</span><span class="sxs-lookup"><span data-stu-id="e2891-120">Ending a connection cancels all sessions and SPIDs, closing the host session.</span></span>  
  
 <span data-ttu-id="e2891-121">结束会话将停止会话中运行的所有命令 (SPID)。</span><span class="sxs-lookup"><span data-stu-id="e2891-121">Ending a session stops all commands (SPIDs) that are running as part of that session.</span></span>  
  
 <span data-ttu-id="e2891-122">结束 SPID 将取消特殊命令。</span><span class="sxs-lookup"><span data-stu-id="e2891-122">Ending a SPID cancels a particular commend.</span></span>  
  
 <span data-ttu-id="e2891-123">如果 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 无法跟踪与连接关联的所有会话和 SPID（例如当 HTTP 方案中打开了多个会话时），则不会关闭连接，这种情况十分少见。</span><span class="sxs-lookup"><span data-stu-id="e2891-123">In rare cases, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will not close a connection if it cannot track all the sessions and SPIDs associated with the connection (for example, when multiple sessions are open in an HTTP scenario).</span></span>  
  
 <span data-ttu-id="e2891-124">有关本主题中引用的 XMLA 的详细信息，请参阅[执行方法 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) 和[取消元素 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)。</span><span class="sxs-lookup"><span data-stu-id="e2891-124">For more information about the XMLA referenced in this topic, see [Execute Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) and [Cancel Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2891-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2891-125">See Also</span></span>  
 <span data-ttu-id="e2891-126">[&#40;XMLA&#41;管理连接和会话](../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md) </span><span class="sxs-lookup"><span data-stu-id="e2891-126">[Managing Connections and Sessions &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md) </span></span>  
 <span data-ttu-id="e2891-127">[&#40;XMLA&#41;的 BeginSession 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/beginsession-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="e2891-127">[BeginSession Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/beginsession-element-xmla) </span></span>  
 <span data-ttu-id="e2891-128">[&#40;XMLA&#41;的 EndSession 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/endsession-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="e2891-128">[EndSession Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/endsession-element-xmla) </span></span>  
 [<span data-ttu-id="e2891-129">Session 元素 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="e2891-129">Session Element &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/session-element-xmla)  
  
  
