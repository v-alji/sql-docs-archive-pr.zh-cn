---
title: MSMQ 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], message queues
- connection managers [Integration Services], MSMQ
- MSMQ connection manager
- message queue connections [Integration Services]
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0c51866eeef281f6587bf281461e4faa2278308d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589836"
---
# <a name="msmq-connection-manager"></a><span data-ttu-id="f727a-102">MSMQ 连接管理器</span><span class="sxs-lookup"><span data-stu-id="f727a-102">MSMQ Connection Manager</span></span>
  <span data-ttu-id="f727a-103">MSMQ 连接管理器使包能够连接到使用“消息队列”（也称为 MSMQ）的消息队列。</span><span class="sxs-lookup"><span data-stu-id="f727a-103">An MSMQ connection manager enables a package to connect to a message queue that uses Message Queuing (also known as MSMQ).</span></span> <span data-ttu-id="f727a-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含的消息队列任务使用 MSMQ 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="f727a-104">The Message Queue task that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses an MSMQ connection manager.</span></span>  
  
 <span data-ttu-id="f727a-105">将 MSMQ 连接管理器添加到包时，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会创建将在运行时解析 MSMQ 连接的连接管理器，同时还会设置该连接管理器的属性，并将该连接管理器添加到包的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="f727a-105">When you add an MSMQ connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an MSMQ connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="f727a-106">该连接管理器的 `ConnectionManagerType` 属性设置为 `MSMQ`。</span><span class="sxs-lookup"><span data-stu-id="f727a-106">The `ConnectionManagerType` property of the connection manager is set to `MSMQ`.</span></span>  
  
 <span data-ttu-id="f727a-107">可以按下列方式来配置 MSMQ 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="f727a-107">You can configure an MSMQ connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="f727a-108">提供一个连接字符串。</span><span class="sxs-lookup"><span data-stu-id="f727a-108">Provide a connection string.</span></span>  
  
-   <span data-ttu-id="f727a-109">提供要连接的消息队列的路径。</span><span class="sxs-lookup"><span data-stu-id="f727a-109">Provide the path of the message queue to connect to.</span></span>  
  
 <span data-ttu-id="f727a-110">路径的格式取决于队列的类型，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="f727a-110">The format of the path depends on the type of queue, as shown in the following table.</span></span>  
  
|<span data-ttu-id="f727a-111">队列类型</span><span class="sxs-lookup"><span data-stu-id="f727a-111">Queue type</span></span>|<span data-ttu-id="f727a-112">示例路径</span><span class="sxs-lookup"><span data-stu-id="f727a-112">Sample path</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="f727a-113">公共</span><span class="sxs-lookup"><span data-stu-id="f727a-113">Public</span></span>|<span data-ttu-id="f727a-114">\<computer name>\\<queue name\></span><span class="sxs-lookup"><span data-stu-id="f727a-114">\<computer name>\\<queue name\></span></span>|  
|<span data-ttu-id="f727a-115">专用</span><span class="sxs-lookup"><span data-stu-id="f727a-115">Private</span></span>|<span data-ttu-id="f727a-116">\<computer name>\Private$\\<queue name\></span><span class="sxs-lookup"><span data-stu-id="f727a-116">\<computer name>\Private$\\<queue name\></span></span>|  
  
 <span data-ttu-id="f727a-117">可以用句点 (.) 代表本地计算机。</span><span class="sxs-lookup"><span data-stu-id="f727a-117">You can use a period (.) to represent the local computer.</span></span>  
  
## <a name="configuration-of-the-msmq-connection-manager"></a><span data-ttu-id="f727a-118">MSMQ 连接管理器的配置</span><span class="sxs-lookup"><span data-stu-id="f727a-118">Configuration of the MSMQ Connection Manager</span></span>  
 <span data-ttu-id="f727a-119">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="f727a-119">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="f727a-120">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请参阅 [MSMQ 连接管理器编辑器](../msmq-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="f727a-120">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [MSMQ Connection Manager Editor](../msmq-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="f727a-121">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="f727a-121">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f727a-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f727a-122">See Also</span></span>  
 <span data-ttu-id="f727a-123">[消息队列任务](../control-flow/message-queue-task.md) </span><span class="sxs-lookup"><span data-stu-id="f727a-123">[Message Queue Task](../control-flow/message-queue-task.md) </span></span>  
 [<span data-ttu-id="f727a-124">Integration Services (SSIS) 连接</span><span class="sxs-lookup"><span data-stu-id="f727a-124">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
