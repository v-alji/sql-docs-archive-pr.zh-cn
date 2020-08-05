---
title: 发送邮件任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sendmailtask.f1
helpviewer_keywords:
- mail [Integration Services]
- Send Mail task
- e-mail [Integration Services]
- messages [Integration Services]
- sending messages
ms.assetid: fe0b7cbc-fe8e-4fe2-95b4-2953efff5869
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c93723f3c443705acc14226ce07f456da4d5a884
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578993"
---
# <a name="send-mail-task"></a><span data-ttu-id="06914-102">发送邮件任务</span><span class="sxs-lookup"><span data-stu-id="06914-102">Send Mail Task</span></span>
  <span data-ttu-id="06914-103">发送邮件任务可以发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="06914-103">The Send Mail task sends an e-mail message.</span></span> <span data-ttu-id="06914-104">通过使用发送邮件任务，包可以在包工作流中的任务成功或失败时发送邮件，也可为响应运行时包引发的事件而发送邮件。</span><span class="sxs-lookup"><span data-stu-id="06914-104">By using the Send Mail task, a package can send messages if tasks in the package workflow succeed or fail, or send messages in response to an event that the package raises at run time.</span></span> <span data-ttu-id="06914-105">例如，该任务可以通知数据库管理员，告知备份数据库任务是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="06914-105">For example, the task can notify a database administrator about the success or failure of the Backup Database task.</span></span>  
  
 <span data-ttu-id="06914-106">可以采用下列方法配置发送邮件任务：</span><span class="sxs-lookup"><span data-stu-id="06914-106">You can configure the Send Mail task in the following ways:</span></span>  
  
-   <span data-ttu-id="06914-107">提供电子邮件的消息正文。</span><span class="sxs-lookup"><span data-stu-id="06914-107">Provide the message text for the e-mail message.</span></span>  
  
-   <span data-ttu-id="06914-108">提供电子邮件的主题行。</span><span class="sxs-lookup"><span data-stu-id="06914-108">Provide a subject line for the e-mail message.</span></span>  
  
-   <span data-ttu-id="06914-109">设置邮件的优先级别。</span><span class="sxs-lookup"><span data-stu-id="06914-109">Set the priority level of the message.</span></span> <span data-ttu-id="06914-110">该任务支持三种优先级别：正常、低和高。</span><span class="sxs-lookup"><span data-stu-id="06914-110">The task supports three priority levels: normal, low, and high.</span></span>  
  
-   <span data-ttu-id="06914-111">在 To、Cc 和 Bcc 行中指定收件人。</span><span class="sxs-lookup"><span data-stu-id="06914-111">Specify the recipients on the To, Cc, and Bcc lines.</span></span> <span data-ttu-id="06914-112">如果任务指定多个收件人，则收件人之间用分号分隔。</span><span class="sxs-lookup"><span data-stu-id="06914-112">If the task specifies multiple recipients, they are separated by semicolons.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="06914-113">根据 Internet 标准，每个 To、Cc 和 Bcc 行最多包含 256 个字符。</span><span class="sxs-lookup"><span data-stu-id="06914-113">The To, Cc, and Bcc lines are limited to 256 characters each in accordance with Internet standards.</span></span>  
  
-   <span data-ttu-id="06914-114">包含附件。</span><span class="sxs-lookup"><span data-stu-id="06914-114">Include attachments.</span></span> <span data-ttu-id="06914-115">如果任务指定多个附件，则附件之间用管道符 (|) 分隔。</span><span class="sxs-lookup"><span data-stu-id="06914-115">If the task specifies multiple attachments, they are separated by the pipe (|) character.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="06914-116">如果包时运行时找不到附件文件，则将产生错误。</span><span class="sxs-lookup"><span data-stu-id="06914-116">If an attachment file does not exist when the package runs, an error occurs.</span></span>  
  
-   <span data-ttu-id="06914-117">指定要使用的 SMTP 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="06914-117">Specify the SMTP connection manager to use.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="06914-118">SMTP 连接管理器仅支持匿名身份验证和 Windows 身份验证，</span><span class="sxs-lookup"><span data-stu-id="06914-118">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="06914-119">而不支持基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="06914-119">It does not support basic authentication.</span></span>  
  
 <span data-ttu-id="06914-120">消息正文可以是提供的字符串、包含文本的文件连接或包含文本的变量名。</span><span class="sxs-lookup"><span data-stu-id="06914-120">The message text can be a string that you provide, a connection to a file that contains the text, or the name of a variable that contains the text.</span></span> <span data-ttu-id="06914-121">该任务使用文件连接管理器来连接文件。</span><span class="sxs-lookup"><span data-stu-id="06914-121">The task uses a File connection manager to connect to a file.</span></span> <span data-ttu-id="06914-122">有关详细信息，请参阅 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="06914-122">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="06914-123">该任务使用 SMTP 连接管理器与邮件服务器建立连接。</span><span class="sxs-lookup"><span data-stu-id="06914-123">The task uses an SMTP connection manager to connect to a mail server.</span></span> <span data-ttu-id="06914-124">有关详细信息，请参阅 [SMTP Connection Manager](../connection-manager/smtp-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="06914-124">For more information, see [SMTP Connection Manager](../connection-manager/smtp-connection-manager.md).</span></span>  
  
## <a name="custom-logging-messages-available-on-the-send-mail-task"></a><span data-ttu-id="06914-125">发送邮件任务可用的自定义日志记录消息</span><span class="sxs-lookup"><span data-stu-id="06914-125">Custom Logging Messages Available on the Send Mail Task</span></span>  
 <span data-ttu-id="06914-126">下表列出了发送邮件任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="06914-126">The following table lists the custom log entries for the Send Mail task.</span></span> <span data-ttu-id="06914-127">有关详细信息，请参阅 [Integration Services (SSIS) 日志记录](../performance/integration-services-ssis-logging.md)和[日志记录的自定义消息](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="06914-127">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="06914-128">日志项</span><span class="sxs-lookup"><span data-stu-id="06914-128">Log entry</span></span>|<span data-ttu-id="06914-129">说明</span><span class="sxs-lookup"><span data-stu-id="06914-129">Description</span></span>|  
|---------------|-----------------|  
|`SendMailTaskBegin`|<span data-ttu-id="06914-130">指示任务开始发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="06914-130">Indicates that the task began to send an e-mail message.</span></span>|  
|`SendMailTaskEnd`|<span data-ttu-id="06914-131">指示任务已发送完电子邮件。</span><span class="sxs-lookup"><span data-stu-id="06914-131">Indicates that the task finished sending an e-mail message.</span></span>|  
|`SendMailTaskInfo`|<span data-ttu-id="06914-132">提供有关任务的说明性信息。</span><span class="sxs-lookup"><span data-stu-id="06914-132">Provides descriptive information about the task.</span></span>|  
  
## <a name="configuring-the-send-mail-task"></a><span data-ttu-id="06914-133">配置发送邮件任务</span><span class="sxs-lookup"><span data-stu-id="06914-133">Configuring the Send Mail Task</span></span>  
 <span data-ttu-id="06914-134">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="06914-134">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="06914-135">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="06914-135">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="06914-136">发送邮件任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="06914-136">Send Mail Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="06914-137">发送邮件任务编辑器（“邮件”页）</span><span class="sxs-lookup"><span data-stu-id="06914-137">Send Mail Task Editor &#40;Mail Page&#41;</span></span>](../send-mail-task-editor-mail-page.md)  
  
-   [<span data-ttu-id="06914-138">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="06914-138">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="06914-139">有关以编程方式设置这些属性的信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="06914-139">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.SendMailTask.SendMailTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="06914-140">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="06914-140">Related Tasks</span></span>  
 <span data-ttu-id="06914-141">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的信息，单击 [设置任务或容器的属性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="06914-141">For information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="06914-142">相关内容</span><span class="sxs-lookup"><span data-stu-id="06914-142">Related Content</span></span>  
  
-   <span data-ttu-id="06914-143">shareourideas.com 上的技术文章 [如何在 C# 中发送具有传递通知的电子邮件](https://go.microsoft.com/fwlink/?LinkId=237625)（如何在 C# 中发送具有传递通知的电子邮件）</span><span class="sxs-lookup"><span data-stu-id="06914-143">Technical article, [How to send email with delivery notification in C#](https://go.microsoft.com/fwlink/?LinkId=237625), on shareourideas.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06914-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06914-144">See Also</span></span>  
 <span data-ttu-id="06914-145">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="06914-145">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="06914-146">控制流</span><span class="sxs-lookup"><span data-stu-id="06914-146">Control Flow</span></span>](control-flow.md)  
  
  
