---
title: 传输错误消息任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.f1
helpviewer_keywords:
- Transfer Error Messages task [Integration Services]
ms.assetid: da702289-035a-4d14-bd74-04461fbfee1b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 952acc28a79fef7e7351c97400e05bc7ba5b9243
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576913"
---
# <a name="transfer-error-messages-task"></a><span data-ttu-id="d238d-102">传输错误消息任务</span><span class="sxs-lookup"><span data-stu-id="d238d-102">Transfer Error Messages Task</span></span>
  <span data-ttu-id="d238d-103">传输错误消息任务可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例之间传输一个或多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]用户定义错误消息。</span><span class="sxs-lookup"><span data-stu-id="d238d-103">The Transfer Error Messages task transfers one or more [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user-defined error messages between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d238d-104">用户定义的消息是标识符等于或大于 50000 的消息。</span><span class="sxs-lookup"><span data-stu-id="d238d-104">User-defined messages are messages with an identifier that is equal to or greater than 50000.</span></span> <span data-ttu-id="d238d-105">标识符小于 50000 的消息是系统错误消息，无法使用传输错误消息任务来传输它。</span><span class="sxs-lookup"><span data-stu-id="d238d-105">Messages with an identifier less than 50000 are system error messages, and cannot be transferred by using the Transfer Error Messages task.</span></span>  
  
 <span data-ttu-id="d238d-106">传输错误消息任务可以配置为传输所有错误消息，也可以配置为只传输指定的错误消息。</span><span class="sxs-lookup"><span data-stu-id="d238d-106">The Transfer Error Messages task can be configured to transfer all error messages, or only the specified error messages.</span></span> <span data-ttu-id="d238d-107">用户定义的错误消息可以多种不同的语言提供，该任务可以配置为只传输选定语言的消息。</span><span class="sxs-lookup"><span data-stu-id="d238d-107">User-defined error messages may be available in a number of different languages and the task can be configured to transfer only messages in selected languages.</span></span> <span data-ttu-id="d238d-108">对于使用代码页 1033 的 us_english 版本的消息来说，在可以将该消息的其他语言版本传输到目标服务器之前，此消息必须已存在于该服务器上。</span><span class="sxs-lookup"><span data-stu-id="d238d-108">A us_english version of the message that uses code page 1033 must exist on the destination server before you can transfer other language versions of the message to that server.</span></span>  
  
 <span data-ttu-id="d238d-109">master 数据库中的 sysmessages 表包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的所有错误消息，包括系统错误消息和用户定义的错误消息。</span><span class="sxs-lookup"><span data-stu-id="d238d-109">The sysmessages table in the master database contains all the error messages-both system and user-defined-that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses.</span></span>  
  
 <span data-ttu-id="d238d-110">要传输的用户定义的消息可能已经存在于目标服务器上。</span><span class="sxs-lookup"><span data-stu-id="d238d-110">The user-defined messages to be transferred may already exist on the destination.</span></span> <span data-ttu-id="d238d-111">如果标识符和语言相同，则错误消息会被视为重复的错误消息。</span><span class="sxs-lookup"><span data-stu-id="d238d-111">An error message is defined as a duplicate error message if the identifier and the language are the same.</span></span> <span data-ttu-id="d238d-112">传输错误消息任务可以配置为以下列方式处理现有错误消息：</span><span class="sxs-lookup"><span data-stu-id="d238d-112">The Transfer Error Messages task can be configured to handle existing error messages in the following ways:</span></span>  
  
-   <span data-ttu-id="d238d-113">覆盖现有错误消息。</span><span class="sxs-lookup"><span data-stu-id="d238d-113">Overwrite existing error messages.</span></span>  
  
-   <span data-ttu-id="d238d-114">如果存在重复消息，则该任务失败。</span><span class="sxs-lookup"><span data-stu-id="d238d-114">Fail the task when duplicate messages exist.</span></span>  
  
-   <span data-ttu-id="d238d-115">跳过重复的错误消息。</span><span class="sxs-lookup"><span data-stu-id="d238d-115">Skip duplicate error messages.</span></span>  
  
 <span data-ttu-id="d238d-116">在运行时，传输错误消息任务使用一个或多个 SMO 连接管理器连接到源服务器和目标服务器。</span><span class="sxs-lookup"><span data-stu-id="d238d-116">At run time, the Transfer Error Messages task connects to the source and destination servers by using one or two SMO connection managers.</span></span> <span data-ttu-id="d238d-117">SMO 连接管理器与传输错误消息任务分开进行配置，然后在传输错误消息任务中引用连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d238d-117">The SMO connection manager is configured separately from the Transfer Error Messages task, and then is referenced in the Transfer Error Messages task.</span></span> <span data-ttu-id="d238d-118">SMO 连接管理器指定服务器以及在访问该服务器时要使用的身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="d238d-118">The SMO connection manager specifies the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="d238d-119">有关详细信息，请参阅 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="d238d-119">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="d238d-120">传输错误消息任务支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 源和目标。</span><span class="sxs-lookup"><span data-stu-id="d238d-120">The Transfer Error Messages task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span> <span data-ttu-id="d238d-121">对于使用哪个版本作为源或目标，没有限制。</span><span class="sxs-lookup"><span data-stu-id="d238d-121">There are no restrictions on which version to use as a source or destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="d238d-122">事件</span><span class="sxs-lookup"><span data-stu-id="d238d-122">Events</span></span>  
 <span data-ttu-id="d238d-123">该任务引发一个报告已经传输的错误消息数的信息事件。</span><span class="sxs-lookup"><span data-stu-id="d238d-123">The task raises an information event that reports the number of error messages that have been transferred.</span></span>  
  
 <span data-ttu-id="d238d-124">传输错误消息任务并不报告错误消息传输的进度，它仅报告 0% 和 100 % 完成。</span><span class="sxs-lookup"><span data-stu-id="d238d-124">The Transfer Error Messages task does not report incremental progress of the error message transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="d238d-125">执行值</span><span class="sxs-lookup"><span data-stu-id="d238d-125">Execution Value</span></span>  
 <span data-ttu-id="d238d-126">在该任务的 `ExecutionValue` 属性中定义的执行值返回已传输的错误消息数。</span><span class="sxs-lookup"><span data-stu-id="d238d-126">The execution value, defined in the `ExecutionValue` property of the task, returns the number of error messages that have been transferred.</span></span> <span data-ttu-id="d238d-127">通过将用户定义的变量分配给传输错误消息任务的 `ExecValueVariable` 属性，包中的其他对象就可以访问有关错误消息传输的信息。</span><span class="sxs-lookup"><span data-stu-id="d238d-127">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Error Message task, information about the error message transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="d238d-128">有关详细信息，请参阅 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)和[在包中使用变量](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="d238d-128">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="d238d-129">日志项</span><span class="sxs-lookup"><span data-stu-id="d238d-129">Log Entries</span></span>  
 <span data-ttu-id="d238d-130">传输错误消息任务包括下列自定义日志项：</span><span class="sxs-lookup"><span data-stu-id="d238d-130">The Transfer Error Messages task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="d238d-131">TransferErrorMessagesTaskStartTransferringObjects    此日志项报告传输已经开始。</span><span class="sxs-lookup"><span data-stu-id="d238d-131">TransferErrorMessagesTaskStartTransferringObjects    This log entry reports that the transfer has started.</span></span> <span data-ttu-id="d238d-132">日志项包括开始时间。</span><span class="sxs-lookup"><span data-stu-id="d238d-132">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="d238d-133">TransferErrorMessagesTaskFinishedTransferringObjects   此日志项报告传输已经完成。</span><span class="sxs-lookup"><span data-stu-id="d238d-133">TransferErrorMessagesTaskFinishedTransferringObjects   This log entry reports that the transfer has finished.</span></span> <span data-ttu-id="d238d-134">日志项包括结束时间。</span><span class="sxs-lookup"><span data-stu-id="d238d-134">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="d238d-135">此外，`OnInformation` 事件的日志项报告已传输的错误消息数，`OnWarning event`的日志项是为目标服务器上被覆盖的每个错误消息写入的。</span><span class="sxs-lookup"><span data-stu-id="d238d-135">In addition, a log entry for the `OnInformation` event reports the number of error messages that were transferred, and a log entry for the `OnWarning event` is written for each error message on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="d238d-136">安全和权限</span><span class="sxs-lookup"><span data-stu-id="d238d-136">Security and Permissions</span></span>  
 <span data-ttu-id="d238d-137">若要新建错误消息，运行该包的用户必须是目标服务器上 sysadmin 的成员或 serveradmin 服务器角色。</span><span class="sxs-lookup"><span data-stu-id="d238d-137">To create new error messages, the user that runs the package must be a member of the sysadmin or serveradmin server role on the destination server.</span></span>  
  
## <a name="configuration-of-the-transfer-error-messages-task"></a><span data-ttu-id="d238d-138">配置传输错误消息任务</span><span class="sxs-lookup"><span data-stu-id="d238d-138">Configuration of the Transfer Error Messages Task</span></span>  
 <span data-ttu-id="d238d-139">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="d238d-139">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d238d-140">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="d238d-140">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d238d-141">传输错误消息任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="d238d-141">Transfer Error Messages Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="d238d-142">传输错误消息任务编辑器（“消息”页）</span><span class="sxs-lookup"><span data-stu-id="d238d-142">Transfer Error Messages Task Editor &#40;Messages Page&#41;</span></span>](../transfer-error-messages-task-editor-messages-page.md)  
  
-   [<span data-ttu-id="d238d-143">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="d238d-143">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="d238d-144">有关以编程方式设置这些属性的信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="d238d-144">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferErrorMessagesTask.TransferErrorMessagesTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="d238d-145">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="d238d-145">Related Tasks</span></span>  
 <span data-ttu-id="d238d-146">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="d238d-146">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="d238d-147">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="d238d-147">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="d238d-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d238d-148">See Also</span></span>  
 <span data-ttu-id="d238d-149">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="d238d-149">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="d238d-150">控制流</span><span class="sxs-lookup"><span data-stu-id="d238d-150">Control Flow</span></span>](control-flow.md)  
  
  
