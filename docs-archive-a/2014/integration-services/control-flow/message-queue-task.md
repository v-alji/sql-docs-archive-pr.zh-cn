---
title: 消息队列任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.messagequeuetask.f1
helpviewer_keywords:
- Message Queue task [Integration Services]
- receiving messages
- messages [Integration Services]
- sending messages
ms.assetid: ae1d8fad-6649-4e93-b589-14a32d07da33
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c9af2ac69fbee07fdc58faf4b63cddc08317e8ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693426"
---
# <a name="message-queue-task"></a><span data-ttu-id="0eb14-102">Message Queue Task</span><span class="sxs-lookup"><span data-stu-id="0eb14-102">Message Queue Task</span></span>
  <span data-ttu-id="0eb14-103">通过消息队列任务，可以使用消息队列（也称为 MSMQ）在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包之间发送和接收消息，或将消息发送到由自定义应用程序处理的应用程序队列。</span><span class="sxs-lookup"><span data-stu-id="0eb14-103">The Message Queue task allows you to use Message Queuing (also known as MSMQ) to send and receive messages between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, or to send messages to an application queue that is processed by a custom application.</span></span> <span data-ttu-id="0eb14-104">这些消息可以采用简单文本格式、文件格式或变量及其值的格式。</span><span class="sxs-lookup"><span data-stu-id="0eb14-104">These messages can take the form of simple text, files, or variables and their values.</span></span>  
  
 <span data-ttu-id="0eb14-105">用消息队列任务可以协调整个企业的运作。</span><span class="sxs-lookup"><span data-stu-id="0eb14-105">By using the Message Queue task, you can coordinate operations throughout your enterprise.</span></span> <span data-ttu-id="0eb14-106">如果目标不可用或繁忙，可以将消息排队供以后发送；例如，该任务可以将要发给销售代表的离线便携式计算机的消息排队，当他们连接到网络时就会收到消息。</span><span class="sxs-lookup"><span data-stu-id="0eb14-106">Messages can be queued and delivered later if the destination is unavailable or busy; for example, the task can queue messages for the offline laptop computer of sales representatives, who receive their messages when they connect to the network.</span></span> <span data-ttu-id="0eb14-107">可以将消息队列任务用于下列目的：</span><span class="sxs-lookup"><span data-stu-id="0eb14-107">You can use the Message Queue task for the following purposes:</span></span>  
  
-   <span data-ttu-id="0eb14-108">将任务推迟到其他包签入时执行。</span><span class="sxs-lookup"><span data-stu-id="0eb14-108">Delaying task execution until other packages check in.</span></span> <span data-ttu-id="0eb14-109">例如，消息队列任务在各个零售站点夜间维护完成之后向公司计算机发送消息。</span><span class="sxs-lookup"><span data-stu-id="0eb14-109">For example, after nightly maintenance at each of your retail sites, a Message Queue task sends a message to your corporate computer.</span></span> <span data-ttu-id="0eb14-110">在公司计算机上运行的包含有消息队列任务，每个任务等待来自特定零售站点的消息。</span><span class="sxs-lookup"><span data-stu-id="0eb14-110">A package running on the corporate computer contains Message Queue tasks, each waiting for a message from a particular retail site.</span></span> <span data-ttu-id="0eb14-111">当来自站点的消息到达时，任务便从该站点上载数据。</span><span class="sxs-lookup"><span data-stu-id="0eb14-111">When a message from a site arrives, a task uploads data from that site.</span></span> <span data-ttu-id="0eb14-112">所有站点都签入完毕之后，包才计算汇总和。</span><span class="sxs-lookup"><span data-stu-id="0eb14-112">After all the sites have checked in, the package computes summary totals.</span></span>  
  
-   <span data-ttu-id="0eb14-113">将数据文件发送到负责处理这些文件的计算机中。</span><span class="sxs-lookup"><span data-stu-id="0eb14-113">Sending data files to the computer that processes them.</span></span> <span data-ttu-id="0eb14-114">例如，可以用数据文件消息把餐馆收银机的输出发送到公司的工资系统，在此处提取出有关各服务员小费的数据。</span><span class="sxs-lookup"><span data-stu-id="0eb14-114">For example, the output from a restaurant cash register can be sent in a data file message to the corporate payroll system, where data about each waiter's tips is extracted.</span></span>  
  
-   <span data-ttu-id="0eb14-115">在整个企业分发文件。</span><span class="sxs-lookup"><span data-stu-id="0eb14-115">Distributing files throughout your enterprise.</span></span> <span data-ttu-id="0eb14-116">例如，包可以使用消息队列任务将包文件发送给另一台计算机。</span><span class="sxs-lookup"><span data-stu-id="0eb14-116">For example, a package can use a Message Queue task to send a package file to another computer.</span></span> <span data-ttu-id="0eb14-117">然后，在目标计算机上运行的包可以使用消息队列任务在本地检索并保存该包。</span><span class="sxs-lookup"><span data-stu-id="0eb14-117">A package running on the destination computer then uses a Message Queue task to retrieve and save the package locally.</span></span>  
  
 <span data-ttu-id="0eb14-118">发送或接收消息时，“消息队列”任务使用以下四种消息类型之一：数据文件、字符串、变量的字符串消息或变量。</span><span class="sxs-lookup"><span data-stu-id="0eb14-118">When sending or receiving messages, the Message Queue task uses one of four message types: data file, string, string message to variable, or variable.</span></span> <span data-ttu-id="0eb14-119">仅在接收消息时才能使用针对变量消息类型的字符串消息。</span><span class="sxs-lookup"><span data-stu-id="0eb14-119">The string message to variable message type can be used only when receiving messages.</span></span>  
  
 <span data-ttu-id="0eb14-120">任务使用 MSMQ 连接管理器连接到消息队列。</span><span class="sxs-lookup"><span data-stu-id="0eb14-120">The task uses an MSMQ connection manager to connect to a message queue.</span></span> <span data-ttu-id="0eb14-121">有关详细信息，请参阅 [MSMQ 连接管理器](../connection-manager/msmq-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="0eb14-121">For more information, see [MSMQ Connection Manager](../connection-manager/msmq-connection-manager.md).</span></span> <span data-ttu-id="0eb14-122">有关消息队列的详细信息，请参阅 [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022)。</span><span class="sxs-lookup"><span data-stu-id="0eb14-122">For more information about Message Queuing, see the [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022).</span></span>  
  
 <span data-ttu-id="0eb14-123">消息队列任务要求安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="0eb14-123">The Message Queue task requires that the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service be installed.</span></span> <span data-ttu-id="0eb14-124">如果在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导的 **“要安装的组件”** 页或 **“功能选择”** 页上选择安装某些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件，将同时安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件的部分子集。</span><span class="sxs-lookup"><span data-stu-id="0eb14-124">Some [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components that you may select for installation on the **Components to Install** page or the **Feature Selection** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard install a partial subset of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components.</span></span> <span data-ttu-id="0eb14-125">这些组件对特定任务是有用的，但 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 功能将受到限制。</span><span class="sxs-lookup"><span data-stu-id="0eb14-125">These components are useful for specific tasks, but the functionality of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] will be limited.</span></span> <span data-ttu-id="0eb14-126">例如， [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 选项会安装设计包所需的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件，但不安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务，因此消息队列任务不起作用。</span><span class="sxs-lookup"><span data-stu-id="0eb14-126">For example, the [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] option installs the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components required to design a package, but the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is not installed, and therefore the Message Queue task is not functional.</span></span> <span data-ttu-id="0eb14-127">为了确保完整安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]，必须在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] “要安装的组件” **页上选择** 。</span><span class="sxs-lookup"><span data-stu-id="0eb14-127">To ensure a complete installation of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you must select [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] on the **Components to Install** page.</span></span> <span data-ttu-id="0eb14-128">有关安装和运行“消息队列”任务的详细信息，请参阅 [安装 Integration Services](../install-windows/install-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0eb14-128">For more information about installing and running the Message Queue task, see [Install Integration Services](../install-windows/install-integration-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0eb14-129">如果将计算机的操作系统配置为 FIPS 模式并且任务使用加密，则“消息队列”任务将无法遵守联邦信息处理标准 (FIPS) 140-2。</span><span class="sxs-lookup"><span data-stu-id="0eb14-129">The Message Queue task fails to comply with Federal Information Processing Standard (FIPS) 140-2 when the computer's operating system is configured in FIPS mode and the task uses encryption.</span></span> <span data-ttu-id="0eb14-130">如果“消息队列”任务不使用加密，则该任务可以成功运行。</span><span class="sxs-lookup"><span data-stu-id="0eb14-130">If the Message Queue task does not use encryption, the task can run successfully.</span></span>  
  
## <a name="message-types"></a><span data-ttu-id="0eb14-131">消息类型</span><span class="sxs-lookup"><span data-stu-id="0eb14-131">Message Types</span></span>  
 <span data-ttu-id="0eb14-132">可以按下列方式配置消息队列任务提供的消息类型：</span><span class="sxs-lookup"><span data-stu-id="0eb14-132">You can configure the message types that the Message Queue task provides in the following ways:</span></span>  
  
-   <span data-ttu-id="0eb14-133">`Data file` 消息指定文件包含消息。</span><span class="sxs-lookup"><span data-stu-id="0eb14-133">`Data file` message specifies that a file contains the message.</span></span> <span data-ttu-id="0eb14-134">在接收消息时，可以将任务配置为保存文件、覆盖现有文件以及指定该任务可从中接收消息的包。</span><span class="sxs-lookup"><span data-stu-id="0eb14-134">When receiving messages, you can configure the task to save the file, overwrite an existing file, and specify the package from which the task can receive messages.</span></span>  
  
-   <span data-ttu-id="0eb14-135">`String` 消息将消息指定为字符串。</span><span class="sxs-lookup"><span data-stu-id="0eb14-135">`String` message specifies the message as a string.</span></span> <span data-ttu-id="0eb14-136">在接收消息时，可以将任务配置为比较接收到的字符串和用户定义字符串，并根据对比结果执行操作。</span><span class="sxs-lookup"><span data-stu-id="0eb14-136">When receiving messages, you can configure the task to compare the received string with a user-defined string and take action depending on the comparison.</span></span> <span data-ttu-id="0eb14-137">字符串比较可以是完全匹配、区分大小写或不区分大小写，或者使用子字符串。</span><span class="sxs-lookup"><span data-stu-id="0eb14-137">String comparison can be exact, case-sensitive or case-insensitive, or use a substring.</span></span>  
  
-   <span data-ttu-id="0eb14-138">`String message to variable` 将源消息指定为发送到目标变量的字符串。</span><span class="sxs-lookup"><span data-stu-id="0eb14-138">`String message to variable` specifies the source message as a string that is sent to a destination variable.</span></span> <span data-ttu-id="0eb14-139">可以将任务配置为使用完全匹配、不区分大小写或子字符串的比较方式来比较接收到的字符串和用户定义字符串。</span><span class="sxs-lookup"><span data-stu-id="0eb14-139">You can configure the task to compare the received string with a user-defined string using an exact, case-insensitive, or substring comparison.</span></span> <span data-ttu-id="0eb14-140">这种消息类型只能在任务接收消息时使用。</span><span class="sxs-lookup"><span data-stu-id="0eb14-140">This message type is available only when the task is receiving messages.</span></span>  
  
-   <span data-ttu-id="0eb14-141">`Variable` 指定消息包含一个或多个变量。</span><span class="sxs-lookup"><span data-stu-id="0eb14-141">`Variable` specifies that the message contains one or more variables.</span></span> <span data-ttu-id="0eb14-142">可以将任务配置为指定消息中所包含变量的名称。</span><span class="sxs-lookup"><span data-stu-id="0eb14-142">You can configure the task to specify the names of the variables included in the message.</span></span> <span data-ttu-id="0eb14-143">在接收消息时，可以将任务配置为指定任务从中接收消息的包和作为消息目标的变量。</span><span class="sxs-lookup"><span data-stu-id="0eb14-143">When receiving messages, you can configure the task to specify both the package from which it can receive messages and the variable that is the destination of the message.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="0eb14-144">发送消息</span><span class="sxs-lookup"><span data-stu-id="0eb14-144">Sending Messages</span></span>  
 <span data-ttu-id="0eb14-145">配置消息队列任务以发送消息时，可以使用消息队列技术当前支持的加密算法（RC2 和 RC4）之一来加密消息。</span><span class="sxs-lookup"><span data-stu-id="0eb14-145">When configuring the Message Queue task to send messages, you can use one of the encryption algorithms that are currently supported by the Message Queuing technology, RC2 and RC4, to encrypt the message.</span></span> <span data-ttu-id="0eb14-146">与较新的算法相比，这两种加密算法都被视为加密性很弱的算法，但消息队列技术尚不支持较新的算法。</span><span class="sxs-lookup"><span data-stu-id="0eb14-146">Both of these encryption algorithms are now considered cryptographically weak compared to newer algorithms, which Message Queuing technology do not yet support.</span></span> <span data-ttu-id="0eb14-147">因此，在使用消息队列任务发送消息时，应考虑您的加密需要。</span><span class="sxs-lookup"><span data-stu-id="0eb14-147">Therefore, you should consider your cryptography needs carefully when sending messages using the Message Queue task.</span></span>  
  
## <a name="receiving-messages"></a><span data-ttu-id="0eb14-148">接收消息</span><span class="sxs-lookup"><span data-stu-id="0eb14-148">Receiving Messages</span></span>  
 <span data-ttu-id="0eb14-149">在接收消息时，可以按下列方式配置消息队列任务：</span><span class="sxs-lookup"><span data-stu-id="0eb14-149">When receiving messages, the Message Queue task can be configured in the following ways:</span></span>  
  
-   <span data-ttu-id="0eb14-150">跳过消息，或从队列中删除消息。</span><span class="sxs-lookup"><span data-stu-id="0eb14-150">Bypassing the message, or removing the message from the queue.</span></span>  
  
-   <span data-ttu-id="0eb14-151">指定超时。</span><span class="sxs-lookup"><span data-stu-id="0eb14-151">Specifying a time-out.</span></span>  
  
-   <span data-ttu-id="0eb14-152">如果出现超时便失败。</span><span class="sxs-lookup"><span data-stu-id="0eb14-152">Failing if a time-out occurs.</span></span>  
  
-   <span data-ttu-id="0eb14-153">如果消息存储在 `Data file` 中，则覆盖现有文件。</span><span class="sxs-lookup"><span data-stu-id="0eb14-153">Overwriting an existing file, if the message is stored in a `Data file`.</span></span>  
  
-   <span data-ttu-id="0eb14-154">如果消息使用 `Data file message` 类型，则将消息文件另存为其他文件名。</span><span class="sxs-lookup"><span data-stu-id="0eb14-154">Saving the message file to a different file name, if the message uses the `Data file message` type.</span></span>  
  
## <a name="custom-logging-messages-available-on-the-message-queue-task"></a><span data-ttu-id="0eb14-155">消息队列任务可用的自定义日志记录消息</span><span class="sxs-lookup"><span data-stu-id="0eb14-155">Custom Logging Messages Available on the Message Queue Task</span></span>  
 <span data-ttu-id="0eb14-156">下表列出了消息队列任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="0eb14-156">The following table lists the custom log entries for the Message Queue task.</span></span> <span data-ttu-id="0eb14-157">有关详细信息，请参阅 [Integration Services (SSIS) 日志记录](../performance/integration-services-ssis-logging.md)和[日志记录的自定义消息](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="0eb14-157">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="0eb14-158">日志项</span><span class="sxs-lookup"><span data-stu-id="0eb14-158">Log entry</span></span>|<span data-ttu-id="0eb14-159">说明</span><span class="sxs-lookup"><span data-stu-id="0eb14-159">Description</span></span>|  
|---------------|-----------------|  
|`MSMQAfterOpen`|<span data-ttu-id="0eb14-160">指示任务已完成打开消息队列的操作。</span><span class="sxs-lookup"><span data-stu-id="0eb14-160">Indicates that the task finished opening the message queue.</span></span>|  
|`MSMQBeforeOpen`|<span data-ttu-id="0eb14-161">指示任务开始打开消息队列。</span><span class="sxs-lookup"><span data-stu-id="0eb14-161">Indicates that the task began to open the message queue.</span></span>|  
|`MSMQBeginReceive`|<span data-ttu-id="0eb14-162">指示任务开始接收消息。</span><span class="sxs-lookup"><span data-stu-id="0eb14-162">Indicates that the task began to receive a message.</span></span>|  
|`MSMQBeginSend`|<span data-ttu-id="0eb14-163">指示任务开始发送消息。</span><span class="sxs-lookup"><span data-stu-id="0eb14-163">Indicates that the task began to send a message.</span></span>|  
|`MSMQEndReceive`|<span data-ttu-id="0eb14-164">指示任务完成接收消息。</span><span class="sxs-lookup"><span data-stu-id="0eb14-164">Indicates that the task finished receiving a message.</span></span>|  
|`MSMQEndSend`|<span data-ttu-id="0eb14-165">指示任务已完成了发送消息的操作。</span><span class="sxs-lookup"><span data-stu-id="0eb14-165">Indicates that the task finished sending a message.</span></span>|  
|`MSMQTaskInfo`|<span data-ttu-id="0eb14-166">提供有关任务的说明性信息。</span><span class="sxs-lookup"><span data-stu-id="0eb14-166">Provides descriptive information about the task.</span></span>|  
|`MSMQTaskTimeOut`|<span data-ttu-id="0eb14-167">指示任务已超时。</span><span class="sxs-lookup"><span data-stu-id="0eb14-167">Indicates that the task timed out.</span></span>|  
  
## <a name="configuration-of-the-message-queue-task"></a><span data-ttu-id="0eb14-168">消息队列任务的配置</span><span class="sxs-lookup"><span data-stu-id="0eb14-168">Configuration of the Message Queue Task</span></span>  
 <span data-ttu-id="0eb14-169">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="0eb14-169">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span> <span data-ttu-id="0eb14-170">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="0eb14-170">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="0eb14-171">消息队列任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="0eb14-171">Message Queue Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="0eb14-172">消息队列任务编辑器（“接收”页）</span><span class="sxs-lookup"><span data-stu-id="0eb14-172">Message Queue Task Editor &#40;Receive Page&#41;</span></span>](../message-queue-task-editor-receive-page.md)  
  
-   [<span data-ttu-id="0eb14-173">消息队列任务编辑器（“发送”页）</span><span class="sxs-lookup"><span data-stu-id="0eb14-173">Message Queue Task Editor &#40;Send Page&#41;</span></span>](../message-queue-task-editor-send-page.md)  
  
-   [<span data-ttu-id="0eb14-174">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="0eb14-174">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="0eb14-175">有关以编程方式设置这些属性的信息，请参阅开发人员指南中针对 **Microsoft.SqlServer.Dts.Tasks.MessageQueueTask.MessageQueueTask** 类的文档。</span><span class="sxs-lookup"><span data-stu-id="0eb14-175">For information about programmatically setting these properties, see the documentation for the **Microsoft.SqlServer.Dts.Tasks.MessageQueueTask.MessageQueueTask** class in the Developer Guide.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0eb14-176">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0eb14-176">Related Tasks</span></span>  
 <span data-ttu-id="0eb14-177">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请参阅 [设置任务或容器的属性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="0eb14-177">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb14-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0eb14-178">See Also</span></span>  
 <span data-ttu-id="0eb14-179">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="0eb14-179">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="0eb14-180">控制流</span><span class="sxs-lookup"><span data-stu-id="0eb14-180">Control Flow</span></span>](control-flow.md)  
  
  
