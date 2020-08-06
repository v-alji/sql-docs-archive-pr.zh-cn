---
title: ) XMLA (取消命令 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- connections [XML for Analysis]
- associated connections [XML for Analysis]
- XML for Analysis, canceling
- associated sessions [XML for Analysis]
- canceling connections
- canceling commands
- canceling sessions
- SPID
- XMLA, canceling
- server process IDs [XML for Analysis]
- sessions [XML for Analysis]
ms.assetid: b59f8197-c33d-4e65-9022-848ccba540f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 003c70362c38ae1838b4679abf6485fa031a9143
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687303"
---
# <a name="canceling-commands-xmla"></a><span data-ttu-id="c3117-102">取消命令 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="c3117-102">Canceling Commands (XMLA)</span></span>
  <span data-ttu-id="c3117-103">根据发出命令的用户的管理权限，XML for Analysis (XMLA 中的 "[取消](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)" 命令) 可以取消对会话、会话、连接、服务器进程或关联会话或连接的命令。</span><span class="sxs-lookup"><span data-stu-id="c3117-103">Depending on the administrative permissions of the user issuing the command, the [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) command in XML for Analysis (XMLA) can cancel a command on a session, a session, a connection, a server process, or an associated session or connection.</span></span>  
  
## <a name="canceling-commands"></a><span data-ttu-id="c3117-104">取消命令</span><span class="sxs-lookup"><span data-stu-id="c3117-104">Canceling Commands</span></span>  
 <span data-ttu-id="c3117-105">用户可以通过发送不带任何指定属性的 `Cancel` 命令，取消当前显式会话上下文中当前正在执行的命令。</span><span class="sxs-lookup"><span data-stu-id="c3117-105">A user can cancel the currently executing command within the context of the current explicit session by sending a `Cancel` command with no specified properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3117-106">用户不能取消隐式会话中正在运行的命令。</span><span class="sxs-lookup"><span data-stu-id="c3117-106">A command running in an implicit session cannot be canceled by a user.</span></span>  
  
### <a name="canceling-batch-commands"></a><span data-ttu-id="c3117-107">取消 Batch 命令</span><span class="sxs-lookup"><span data-stu-id="c3117-107">Canceling Batch Commands</span></span>  
 <span data-ttu-id="c3117-108">如果用户取消了一个 `Batch` 命令，则会取消该 `Batch` 命令中尚未执行的所有其余命令。</span><span class="sxs-lookup"><span data-stu-id="c3117-108">If a user cancels a `Batch` command, then all remaining commands not yet executed within the `Batch` command are canceled.</span></span> <span data-ttu-id="c3117-109">如果 `Batch` 命令是事务性的，则会回滚在 `Cancel` 命令运行前已执行的所有命令。</span><span class="sxs-lookup"><span data-stu-id="c3117-109">If the `Batch` command was transactional, any commands that were executed before the `Cancel` command runs are rolled back.</span></span>  
  
## <a name="canceling-sessions"></a><span data-ttu-id="c3117-110">取消会话</span><span class="sxs-lookup"><span data-stu-id="c3117-110">Canceling Sessions</span></span>  
 <span data-ttu-id="c3117-111">通过在命令的[SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla)属性中指定显式会话的会话标识符 `Cancel` ，数据库管理员或服务器管理员可以取消会话，包括当前正在执行的命令。</span><span class="sxs-lookup"><span data-stu-id="c3117-111">By specifying a session identifier for an explicit session in the [SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) property of the `Cancel` command, a database administrator or server administrator can cancel a session, including the currently executing command.</span></span> <span data-ttu-id="c3117-112">数据库管理员只能取消其拥有管理权限的数据库的会话。</span><span class="sxs-lookup"><span data-stu-id="c3117-112">A database administrator can only cancel sessions for databases on which he or she has administrative permissions.</span></span>  
  
 <span data-ttu-id="c3117-113">数据库管理员可以通过检索 DISCOVER_SESSIONS 架构行集来检索指定数据库的活动会话。</span><span class="sxs-lookup"><span data-stu-id="c3117-113">A database administrator can retrieve the active sessions for a specified database by retrieving the DISCOVER_SESSIONS schema rowset.</span></span> <span data-ttu-id="c3117-114">为了检索 DISCOVER_SESSIONS 架构行集，数据库管理员使用 XMLA `Discover` 方法，并为该方法的[限制](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla)属性中的 "SESSION_CURRENT_DATABASE 限制" 列指定相应的数据库标识符 `Discover` 。</span><span class="sxs-lookup"><span data-stu-id="c3117-114">To retrieve the DISCOVER_SESSIONS schema rowset, the database administrator uses the XMLA `Discover` method and specifies the appropriate database identifier for the SESSION_CURRENT_DATABASE restriction column in the [Restrictions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla) property of the `Discover` method.</span></span>  
  
## <a name="canceling-connections"></a><span data-ttu-id="c3117-115">取消连接</span><span class="sxs-lookup"><span data-stu-id="c3117-115">Canceling Connections</span></span>  
 <span data-ttu-id="c3117-116">通过在命令的[ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla)属性中指定连接标识符 `Cancel` ，服务器管理员可以取消与给定连接关联的所有会话，包括所有正在运行的命令，并取消连接。</span><span class="sxs-lookup"><span data-stu-id="c3117-116">By specifying a connection identifier in the [ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla) property of the `Cancel` command, a server administrator can cancel all of the sessions associated with a given connection, including all running commands, and cancel the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3117-117">如果实例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 无法找到和取消与连接关联的会话（例如，当数据抽取在提供 HTTP 连接的同时打开多个会话时），则实例将无法取消该连接。</span><span class="sxs-lookup"><span data-stu-id="c3117-117">If the instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cannot locate and cancel the sessions associated with a connection, such as when the data pump opens multiple sessions while providing HTTP connectivity, the instance cannot cancel the connection.</span></span> <span data-ttu-id="c3117-118">如果在执行 `Cancel` 命令时遇到了这种情况，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="c3117-118">If this case is encountered during the execution of a `Cancel` command, an error occurs.</span></span>  
  
 <span data-ttu-id="c3117-119">服务器管理员可以检索 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的活动连接，方法是使用 XMLA `Discover` 方法检索 DISCOVER_CONNECTIONS 架构行集。</span><span class="sxs-lookup"><span data-stu-id="c3117-119">A server administrator can retrieve the active connections for an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance by retrieving the DISCOVER_CONNECTIONS schema rowset using the XMLA `Discover` method.</span></span>  
  
## <a name="canceling-server-processes"></a><span data-ttu-id="c3117-120">取消服务器进程</span><span class="sxs-lookup"><span data-stu-id="c3117-120">Canceling Server Processes</span></span>  
 <span data-ttu-id="c3117-121">通过在命令的[spid](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla)属性中指定服务器进程标识符 (spid) `Cancel` ，服务器管理员可以取消与给定 SPID 关联的命令。</span><span class="sxs-lookup"><span data-stu-id="c3117-121">By specifying a server process identifier (SPID) in the [SPID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) property of the `Cancel` command, a server administrator can cancel the commands associated with a given SPID.</span></span>  
  
## <a name="canceling-associated-sessions-and-connections"></a><span data-ttu-id="c3117-122">取消关联的会话和连接</span><span class="sxs-lookup"><span data-stu-id="c3117-122">Canceling Associated Sessions and Connections</span></span>  
 <span data-ttu-id="c3117-123">可以将[CancelAssociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla)属性设置为 true，以便取消与命令中指定的连接、会话或 SPID 关联的连接、会话和命令 `Cancel` 。</span><span class="sxs-lookup"><span data-stu-id="c3117-123">You can set the [CancelAssociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla) property to true to cancel the connections, sessions, and commands associated with the connection, session, or SPID specified in the `Cancel` command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3117-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3117-124">See Also</span></span>  
 <span data-ttu-id="c3117-125">[XMLA&#41;&#40;发现方法](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) </span><span class="sxs-lookup"><span data-stu-id="c3117-125">[Discover Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) </span></span>  
 [<span data-ttu-id="c3117-126">在 Analysis Services 中使用 XMLA 开发</span><span class="sxs-lookup"><span data-stu-id="c3117-126">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
