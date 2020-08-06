---
title: MSMQ 连接管理器编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msmqconnectionmanager.f1
helpviewer_keywords:
- MSMQ Connection Manager Editor
ms.assetid: ef842cb4-82da-4550-85fe-9bedbc1e77c7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 41d4231ce121d596c8d818485eccf5ddf6127470
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578302"
---
# <a name="msmq-connection-manager-editor"></a><span data-ttu-id="be570-102">MSMQ 连接管理器编辑器</span><span class="sxs-lookup"><span data-stu-id="be570-102">MSMQ Connection Manager Editor</span></span>
  <span data-ttu-id="be570-103">可以使用“MSMQ 连接管理器”对话框指定“消息队列”（也称为 MSMQ）消息队列的路径。</span><span class="sxs-lookup"><span data-stu-id="be570-103">Use the **MSMQ Connection Manager** dialog box to specify the path to a Message Queuing (also known as MSMQ) message queue.</span></span>  
  
 <span data-ttu-id="be570-104">若要了解有关 MSMQ 连接管理器的详细信息，请参阅 [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="be570-104">To learn more about the MSMQ connection manager, see [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be570-105">MSMQ 连接管理器支持本地公共队列、本地专用队列和远程公共队列。</span><span class="sxs-lookup"><span data-stu-id="be570-105">The MSMQ connection manager supports local public and private queues and remote public queues.</span></span> <span data-ttu-id="be570-106">它不支持远程专用队列。</span><span class="sxs-lookup"><span data-stu-id="be570-106">It does not support remote private queues.</span></span> <span data-ttu-id="be570-107">有关使用脚本任务的解决方法，请参阅 [向远程私有消息队列使用脚本任务发送](control-flow/script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="be570-107">For a workaround that uses the Script Task, see [Sending to a Remote Private Message Queue with the Script Task](control-flow/script-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="be570-108">选项</span><span class="sxs-lookup"><span data-stu-id="be570-108">Options</span></span>  
 <span data-ttu-id="be570-109">**名称**</span><span class="sxs-lookup"><span data-stu-id="be570-109">**Name**</span></span>  
 <span data-ttu-id="be570-110">为工作流中的 MSMQ 连接管理器提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="be570-110">Provide a unique name for the MSMQ connection manager in the workflow.</span></span> <span data-ttu-id="be570-111">所提供的名称将在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中显示。</span><span class="sxs-lookup"><span data-stu-id="be570-111">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="be570-112">**说明**</span><span class="sxs-lookup"><span data-stu-id="be570-112">**Description**</span></span>  
 <span data-ttu-id="be570-113">描述连接管理器。</span><span class="sxs-lookup"><span data-stu-id="be570-113">Describe the connection manager.</span></span> <span data-ttu-id="be570-114">最好按照连接管理器的用途对其进行说明，使包的说明一目了然，且更便于维护。</span><span class="sxs-lookup"><span data-stu-id="be570-114">As a best practice, describe the connection manager in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="be570-115">**路径**</span><span class="sxs-lookup"><span data-stu-id="be570-115">**Path**</span></span>  
 <span data-ttu-id="be570-116">键入消息队列的完整路径。</span><span class="sxs-lookup"><span data-stu-id="be570-116">Type the complete path of the message queue.</span></span> <span data-ttu-id="be570-117">路径的格式取决于队列的类型。</span><span class="sxs-lookup"><span data-stu-id="be570-117">The format of the path depends on the type of queue.</span></span>  
  
|<span data-ttu-id="be570-118">队列类型</span><span class="sxs-lookup"><span data-stu-id="be570-118">Queue type</span></span>|<span data-ttu-id="be570-119">示例路径</span><span class="sxs-lookup"><span data-stu-id="be570-119">Sample path</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="be570-120">公共</span><span class="sxs-lookup"><span data-stu-id="be570-120">Public</span></span>|<span data-ttu-id="be570-121">\<computer name>\\<queue name\></span><span class="sxs-lookup"><span data-stu-id="be570-121">\<computer name>\\<queue name\></span></span>|  
|<span data-ttu-id="be570-122">专用</span><span class="sxs-lookup"><span data-stu-id="be570-122">Private</span></span>|<span data-ttu-id="be570-123">\<computer name>\Private$\\<queue name\></span><span class="sxs-lookup"><span data-stu-id="be570-123">\<computer name>\Private$\\<queue name\></span></span>|  
  
 <span data-ttu-id="be570-124">可以用“.”代表本地计算机。</span><span class="sxs-lookup"><span data-stu-id="be570-124">You can use "." to represent the local computer.</span></span>  
  
 <span data-ttu-id="be570-125">**Test**</span><span class="sxs-lookup"><span data-stu-id="be570-125">**Test**</span></span>  
 <span data-ttu-id="be570-126">在配置 MSMQ 连接管理器之后，单击“测试”确定该连接是否可用。</span><span class="sxs-lookup"><span data-stu-id="be570-126">After configuring the MSMQ connection manager, confirm that the connection is viable by clicking **Test**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be570-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="be570-127">See Also</span></span>  
 [<span data-ttu-id="be570-128">Integration Services 错误和消息引用</span><span class="sxs-lookup"><span data-stu-id="be570-128">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
