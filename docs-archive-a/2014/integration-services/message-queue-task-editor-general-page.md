---
title: 消息队列任务编辑器 (常规页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.general.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 09368b18-37a5-4321-a173-7cfe5d42d2a2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dcec75f3a4dd85efb7c97226c592d6b1e1bb26ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591476"
---
# <a name="message-queue-task-editor-general-page"></a><span data-ttu-id="1e4eb-102">消息队列任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="1e4eb-102">Message Queue Task Editor (General Page)</span></span>
  <span data-ttu-id="1e4eb-103">可以使用 **“消息队列任务编辑器”** 对话框的 **“常规”** 页，对消息队列任务进行命名和说明，指定消息格式，以及指示任务是发送还是接收消息。</span><span class="sxs-lookup"><span data-stu-id="1e4eb-103">Use the **General page** of the **Message Queue Task Editor** dialog box to name and describe the Message Queue task, to specify the message format, and to indicate whether the task sends or receives messages.</span></span>  
  
 <span data-ttu-id="1e4eb-104">若要了解此任务，请参阅 [Message Queue Task](control-flow/message-queue-task.md)。</span><span class="sxs-lookup"><span data-stu-id="1e4eb-104">To learn about this task, see [Message Queue Task](control-flow/message-queue-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1e4eb-105">选项</span><span class="sxs-lookup"><span data-stu-id="1e4eb-105">Options</span></span>  
 <span data-ttu-id="1e4eb-106">**名称**</span><span class="sxs-lookup"><span data-stu-id="1e4eb-106">**Name**</span></span>  
 <span data-ttu-id="1e4eb-107">为消息队列任务提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="1e4eb-107">Provide a unique name for the Message Queue task.</span></span> <span data-ttu-id="1e4eb-108">此名称用作任务图标中的标签。</span><span class="sxs-lookup"><span data-stu-id="1e4eb-108">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e4eb-109">任务名称在一个包内必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="1e4eb-109">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="1e4eb-110">**说明**</span><span class="sxs-lookup"><span data-stu-id="1e4eb-110">**Description**</span></span>  
 <span data-ttu-id="1e4eb-111">键入对消息队列任务的说明。</span><span class="sxs-lookup"><span data-stu-id="1e4eb-111">Type a description of the Message Queue task.</span></span>  
  
 <span data-ttu-id="1e4eb-112">**Use2000Format**</span><span class="sxs-lookup"><span data-stu-id="1e4eb-112">**Use2000Format**</span></span>  
 <span data-ttu-id="1e4eb-113">指示是否使用消息队列（也称为 MSMQ）的 2000 格式。</span><span class="sxs-lookup"><span data-stu-id="1e4eb-113">Indicate whether to use the 2000 format of Message Queuing (also known as MSMQ).</span></span> <span data-ttu-id="1e4eb-114">默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="1e4eb-114">The default is `False`.</span></span>  
  
 <span data-ttu-id="1e4eb-115">**MSMQConnection**</span><span class="sxs-lookup"><span data-stu-id="1e4eb-115">**MSMQConnection**</span></span>  
 <span data-ttu-id="1e4eb-116">选择现有 MSMQ 连接管理器，或单击“\<**New connection...**>”以创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="1e4eb-116">Select an existing MSMQ connection manager or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="1e4eb-117">**相关主题**：[MSMQ 连接管理器](connection-manager/msmq-connection-manager.md)、[MSMQ 连接管理器编辑器](../../2014/integration-services/msmq-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1e4eb-117">**Related Topics**: [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md), [MSMQ Connection Manager Editor](../../2014/integration-services/msmq-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="1e4eb-118">**消息**</span><span class="sxs-lookup"><span data-stu-id="1e4eb-118">**Message**</span></span>  
 <span data-ttu-id="1e4eb-119">指定消息队列任务是发送消息还是接收消息。</span><span class="sxs-lookup"><span data-stu-id="1e4eb-119">Specify whether the Message Queue task sends or receive messages.</span></span> <span data-ttu-id="1e4eb-120">如果选择了 **“发送消息”** ，则该对话框的左窗格将列出“发送”页；如果选择了 **“接收消息”** ，则将列出“接收”页。</span><span class="sxs-lookup"><span data-stu-id="1e4eb-120">If you select **Send message**, the Send page is listed in the left pane of the dialog box; if you select **Receive message**, the Receive page is listed.</span></span> <span data-ttu-id="1e4eb-121">默认情况下，此值设置为 **“发送消息”** 。</span><span class="sxs-lookup"><span data-stu-id="1e4eb-121">By default, this value is set to **Send message**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e4eb-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e4eb-122">See Also</span></span>  
 <span data-ttu-id="1e4eb-123">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1e4eb-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="1e4eb-124">[消息队列任务编辑器 &#40;接收页面&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span><span class="sxs-lookup"><span data-stu-id="1e4eb-124">[Message Queue Task Editor &#40;Receive Page&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span></span>  
 <span data-ttu-id="1e4eb-125">[消息队列任务编辑器 &#40;发送页面&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span><span class="sxs-lookup"><span data-stu-id="1e4eb-125">[Message Queue Task Editor &#40;Send Page&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span></span>  
 [<span data-ttu-id="1e4eb-126">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="1e4eb-126">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
