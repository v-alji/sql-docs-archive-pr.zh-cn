---
title: 发送邮件任务编辑器 (Mail Page) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sendmailtask.mail.f1
helpviewer_keywords:
- Send Mail Task Editor
ms.assetid: adb385d5-ef24-4d18-b9ea-b39e00a7075e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 52cab62f3c88ea248b76061664547fd8f1314099
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694041"
---
# <a name="send-mail-task-editor-mail-page"></a><span data-ttu-id="26e60-102">发送邮件任务编辑器（“邮件”页）</span><span class="sxs-lookup"><span data-stu-id="26e60-102">Send Mail Task Editor (Mail Page)</span></span>
  <span data-ttu-id="26e60-103">使用 **“发送邮件任务编辑器”** 对话框中的 **“邮件”** 页，可以指定收件人、邮件类型和邮件的优先级。</span><span class="sxs-lookup"><span data-stu-id="26e60-103">Use the **Mail** page of the **Send Mail Task Editor** dialog box to specify recipients, message type, and priority for a message.</span></span> <span data-ttu-id="26e60-104">您还可以在邮件中附加文件。</span><span class="sxs-lookup"><span data-stu-id="26e60-104">You can also attach files to the message.</span></span> <span data-ttu-id="26e60-105">邮件正文可以是您提供的字符串，也可以是指向包含文本的文件连接，还可以是包含文本的变量的名称。</span><span class="sxs-lookup"><span data-stu-id="26e60-105">The message text can be a string you provide, a file connection to a file that contains the text, or the name of a variable that contains the text.</span></span>  
  
 <span data-ttu-id="26e60-106">若要了解此任务，请参阅 [Send Mail Task](control-flow/send-mail-task.md)。</span><span class="sxs-lookup"><span data-stu-id="26e60-106">To learn about this task, see [Send Mail Task](control-flow/send-mail-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="26e60-107">选项</span><span class="sxs-lookup"><span data-stu-id="26e60-107">Options</span></span>  
 <span data-ttu-id="26e60-108">**SMTPConnection**</span><span class="sxs-lookup"><span data-stu-id="26e60-108">**SMTPConnection**</span></span>  
 <span data-ttu-id="26e60-109">从列表中选择一个 SMTP 连接管理器，或单击“\<New connection...>”创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="26e60-109">Select an SMTP connection manager in the list, or click **\<New connection...>** to create a new connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="26e60-110">SMTP 连接管理器仅支持匿名身份验证和 Windows 身份验证，</span><span class="sxs-lookup"><span data-stu-id="26e60-110">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="26e60-111">而不支持基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="26e60-111">It does not support basic authentication.</span></span>  
  
 <span data-ttu-id="26e60-112">**相关主题：** [SMTP 连接管理器](connection-manager/smtp-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="26e60-112">**Related Topics:** [SMTP Connection Manager](connection-manager/smtp-connection-manager.md)</span></span>  
  
 <span data-ttu-id="26e60-113">**From**</span><span class="sxs-lookup"><span data-stu-id="26e60-113">**From**</span></span>  
 <span data-ttu-id="26e60-114">指定发件人的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="26e60-114">Specify the e-mail address of the sender.</span></span>  
  
 <span data-ttu-id="26e60-115">**收件人**</span><span class="sxs-lookup"><span data-stu-id="26e60-115">**To**</span></span>  
 <span data-ttu-id="26e60-116">提供收件人的电子邮件地址，用分号分隔。</span><span class="sxs-lookup"><span data-stu-id="26e60-116">Provide the e-mail addresses of the recipients, delimited by semicolons.</span></span>  
  
 <span data-ttu-id="26e60-117">**抄送**</span><span class="sxs-lookup"><span data-stu-id="26e60-117">**Cc**</span></span>  
 <span data-ttu-id="26e60-118">指定也可以收到邮件副本的各个人员的电子邮件地址，用分号分隔。</span><span class="sxs-lookup"><span data-stu-id="26e60-118">Specify the e-mail addresses, delimited by semicolons, of individuals who also receive copies of the message.</span></span>  
  
 <span data-ttu-id="26e60-119">**密件抄送**</span><span class="sxs-lookup"><span data-stu-id="26e60-119">**Bcc**</span></span>  
 <span data-ttu-id="26e60-120">指定将收到邮件的隐蔽副本 (Bcc) 的各个人员的电子邮件地址，用分号分隔。</span><span class="sxs-lookup"><span data-stu-id="26e60-120">Specify the e-mail addresses, delimited by semicolons, of individuals who receive blind carbon copies (Bcc) copies of the message.</span></span>  
  
 <span data-ttu-id="26e60-121">**主题**</span><span class="sxs-lookup"><span data-stu-id="26e60-121">**Subject**</span></span>  
 <span data-ttu-id="26e60-122">提供电子邮件的主题。</span><span class="sxs-lookup"><span data-stu-id="26e60-122">Provide a subject for the e-mail message.</span></span>  
  
 <span data-ttu-id="26e60-123">**MessageSourceType**</span><span class="sxs-lookup"><span data-stu-id="26e60-123">**MessageSourceType**</span></span>  
 <span data-ttu-id="26e60-124">选择消息的源类型。</span><span class="sxs-lookup"><span data-stu-id="26e60-124">Select the source type of the message.</span></span> <span data-ttu-id="26e60-125">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="26e60-125">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="26e60-126">值</span><span class="sxs-lookup"><span data-stu-id="26e60-126">Value</span></span>|<span data-ttu-id="26e60-127">说明</span><span class="sxs-lookup"><span data-stu-id="26e60-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="26e60-128">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="26e60-128">**Direct input**</span></span>|<span data-ttu-id="26e60-129">将源设置为邮件正文。</span><span class="sxs-lookup"><span data-stu-id="26e60-129">Set the source to the message text.</span></span> <span data-ttu-id="26e60-130">选择此值将显示动态选项 **MessageSource**。</span><span class="sxs-lookup"><span data-stu-id="26e60-130">Selecting this value displays the dynamic option, **MessageSource**.</span></span>|  
|<span data-ttu-id="26e60-131">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="26e60-131">**File connection**</span></span>|<span data-ttu-id="26e60-132">将源设置为包含邮件正文的文件。</span><span class="sxs-lookup"><span data-stu-id="26e60-132">Set the source to the file that contains the message text.</span></span> <span data-ttu-id="26e60-133">选择此值将显示动态选项 **MessageSource**。</span><span class="sxs-lookup"><span data-stu-id="26e60-133">Selecting this value displays the dynamic option, **MessageSource**.</span></span>|  
|<span data-ttu-id="26e60-134">**变量**</span><span class="sxs-lookup"><span data-stu-id="26e60-134">**Variable**</span></span>|<span data-ttu-id="26e60-135">将源设置为包含消息正文的变量。</span><span class="sxs-lookup"><span data-stu-id="26e60-135">Set the source to a variable that contains the message text.</span></span> <span data-ttu-id="26e60-136">选择此值将显示动态选项 **MessageSource**。</span><span class="sxs-lookup"><span data-stu-id="26e60-136">Selecting this value displays the dynamic option, **MessageSource**.</span></span>|  
  
 <span data-ttu-id="26e60-137">**Priority**</span><span class="sxs-lookup"><span data-stu-id="26e60-137">**Priority**</span></span>  
 <span data-ttu-id="26e60-138">设置邮件的优先级。</span><span class="sxs-lookup"><span data-stu-id="26e60-138">Set the priority of the message.</span></span>  
  
 <span data-ttu-id="26e60-139">**Attachments**</span><span class="sxs-lookup"><span data-stu-id="26e60-139">**Attachments**</span></span>  
 <span data-ttu-id="26e60-140">为电子邮件附件提供文件名，用竖线 (|) 字符分隔。</span><span class="sxs-lookup"><span data-stu-id="26e60-140">Provide the file names of attachments to the e-mail message, delimited by the pipe (|) character.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26e60-141">根据 Internet 标准，每个 To、Cc 和 Bcc 行最多包含 256 个字符。</span><span class="sxs-lookup"><span data-stu-id="26e60-141">The To, Cc, and Bcc lines are limited to 256 characters in accordance with Internet standards.</span></span>  
  
## <a name="messagesourcetype-dynamic-options"></a><span data-ttu-id="26e60-142">MessageSourceType 动态选项</span><span class="sxs-lookup"><span data-stu-id="26e60-142">MessageSourceType Dynamic Options</span></span>  
  
### <a name="messagesourcetype--direct-input"></a><span data-ttu-id="26e60-143">MessageSourceType = 直接输入</span><span class="sxs-lookup"><span data-stu-id="26e60-143">MessageSourceType = Direct Input</span></span>  
 <span data-ttu-id="26e60-144">**MessageSource**</span><span class="sxs-lookup"><span data-stu-id="26e60-144">**MessageSource**</span></span>  
 <span data-ttu-id="26e60-145">键入邮件正文，或单击浏览按钮 (…)，然后在“消息源”对话框中键入邮件内容  。</span><span class="sxs-lookup"><span data-stu-id="26e60-145">Type the message text or click the browse button (...) and then type the message in the **Message source** dialog box.</span></span>  
  
### <a name="messagesourcetype--file-connection"></a><span data-ttu-id="26e60-146">MessageSourceType = 文件连接</span><span class="sxs-lookup"><span data-stu-id="26e60-146">MessageSourceType = File connection</span></span>  
 <span data-ttu-id="26e60-147">**MessageSource**</span><span class="sxs-lookup"><span data-stu-id="26e60-147">**MessageSource**</span></span>  
 <span data-ttu-id="26e60-148">从列表中选择“文件连接管理器，或单击“\<**New connection...**>”创建新”的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="26e60-148">Select a File connection manager in the list or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="26e60-149">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="26e60-149">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="messagesourcetype--variable"></a><span data-ttu-id="26e60-150">MessageSourceType = 变量</span><span class="sxs-lookup"><span data-stu-id="26e60-150">MessageSourceType = Variable</span></span>  
 <span data-ttu-id="26e60-151">**MessageSource**</span><span class="sxs-lookup"><span data-stu-id="26e60-151">**MessageSource**</span></span>  
 <span data-ttu-id="26e60-152">在列表中选择变量，或单击“\<**New variable...**>”创建新变量。</span><span class="sxs-lookup"><span data-stu-id="26e60-152">Select a variable in the list or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="26e60-153">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="26e60-153">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26e60-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26e60-154">See Also</span></span>  
 <span data-ttu-id="26e60-155">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="26e60-155">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="26e60-156">[&#40;常规页发送邮件任务编辑器&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="26e60-156">[Send Mail Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="26e60-157">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="26e60-157">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
