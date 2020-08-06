---
title: 消息队列任务编辑器 (发送页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.send.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 565aa079-ac44-4407-8efc-cddab839de30
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3534e1a8b475f22064ef7f2283c2e70eb561294f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694515"
---
# <a name="message-queue-task-editor-send-page"></a><span data-ttu-id="19e35-102">消息队列任务编辑器（“发送”页）</span><span class="sxs-lookup"><span data-stu-id="19e35-102">Message Queue Task Editor (Send Page)</span></span>
  <span data-ttu-id="19e35-103">使用“消息队列任务编辑器”对话框的“发送”页面，能配置消息队列任务以便从 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包发送消息   。</span><span class="sxs-lookup"><span data-stu-id="19e35-103">Use the **Send** page of the **Message Queue Task Editor** dialog box to configure a Message Queue task to send messages from a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span>  
  
 <span data-ttu-id="19e35-104">若要了解此任务，请参阅 [Message Queue Task](control-flow/message-queue-task.md)。</span><span class="sxs-lookup"><span data-stu-id="19e35-104">To learn about this task, see [Message Queue Task](control-flow/message-queue-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="19e35-105">选项</span><span class="sxs-lookup"><span data-stu-id="19e35-105">Options</span></span>  
 <span data-ttu-id="19e35-106">**UseEncryption**</span><span class="sxs-lookup"><span data-stu-id="19e35-106">**UseEncryption**</span></span>  
 <span data-ttu-id="19e35-107">指示是否对消息进行加密。</span><span class="sxs-lookup"><span data-stu-id="19e35-107">Indicate whether to encrypt the message.</span></span> <span data-ttu-id="19e35-108">默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="19e35-108">The default is `False`.</span></span>  
  
 <span data-ttu-id="19e35-109">**EncryptionAlgorithm**</span><span class="sxs-lookup"><span data-stu-id="19e35-109">**EncryptionAlgorithm**</span></span>  
 <span data-ttu-id="19e35-110">如果选择使用加密，请指定要使用的加密算法的名称。</span><span class="sxs-lookup"><span data-stu-id="19e35-110">If you choose to use encryption, specify the name of the encryption algorithm to use.</span></span> <span data-ttu-id="19e35-111">消息队列任务可以使用 RC2 和 RC4 算法。</span><span class="sxs-lookup"><span data-stu-id="19e35-111">The Message Queue task can use the RC2 and RC4 algorithms.</span></span> <span data-ttu-id="19e35-112">默认值为 **RC2**。</span><span class="sxs-lookup"><span data-stu-id="19e35-112">The default is **RC2**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19e35-113">RC4 算法仅用于支持向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="19e35-113">The RC4 algorithm is only supported for backward compatibility.</span></span> <span data-ttu-id="19e35-114">仅当数据库兼容级别为 90 或 100 时，才能使用 RC4 或 RC4_128 对新材料进行加密。</span><span class="sxs-lookup"><span data-stu-id="19e35-114">New material can only be encrypted using RC4 or RC4_128 when the database is in compatibility level 90 or 100.</span></span> <span data-ttu-id="19e35-115">（建议不要使用。）而是使用一种较新的算法，如 AES 算法之一。</span><span class="sxs-lookup"><span data-stu-id="19e35-115">(Not recommended.) Use a newer algorithm such as one of the AES algorithms instead.</span></span> <span data-ttu-id="19e35-116">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的当前版本中，可以通过任何兼容级别对使用 RC4 或 RC4_128 加密的材料进行解密。</span><span class="sxs-lookup"><span data-stu-id="19e35-116">In the current release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], material encrypted using RC4 or RC4_128 can be decrypted in any compatibility level.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="19e35-117">这些算法是消息队列（也称为 MSMQ）技术支持的加密算法。</span><span class="sxs-lookup"><span data-stu-id="19e35-117">These are the encryption algorithms that the Message Queuing (also known as MSMQ) technology supports.</span></span> <span data-ttu-id="19e35-118">与较新的算法相比，这两种加密算法都被视为加密性很弱的算法，但消息队列尚不支持新的算法。</span><span class="sxs-lookup"><span data-stu-id="19e35-118">Both of these encryption algorithms are now considered cryptographically weak compared to newer algorithms, which Message Queuing does not yet support.</span></span> <span data-ttu-id="19e35-119">因此，在使用消息队列任务发送消息时，应考虑您的加密需要。</span><span class="sxs-lookup"><span data-stu-id="19e35-119">Therefore, you should consider your cryptography needs carefully when sending messages using the Message Queue task.</span></span>  
  
 <span data-ttu-id="19e35-120">**MessageType**</span><span class="sxs-lookup"><span data-stu-id="19e35-120">**MessageType**</span></span>  
 <span data-ttu-id="19e35-121">选择消息类型。</span><span class="sxs-lookup"><span data-stu-id="19e35-121">Select the message type.</span></span> <span data-ttu-id="19e35-122">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="19e35-122">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="19e35-123">值</span><span class="sxs-lookup"><span data-stu-id="19e35-123">Value</span></span>|<span data-ttu-id="19e35-124">说明</span><span class="sxs-lookup"><span data-stu-id="19e35-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="19e35-125">**数据文件消息**</span><span class="sxs-lookup"><span data-stu-id="19e35-125">**Data file message**</span></span>|<span data-ttu-id="19e35-126">消息存储在文件中。</span><span class="sxs-lookup"><span data-stu-id="19e35-126">The message is stored in a file.</span></span> <span data-ttu-id="19e35-127">选择该值将显示动态选项 **DataFileMessage**。</span><span class="sxs-lookup"><span data-stu-id="19e35-127">Selecting the value displays the dynamic option, **DataFileMessage**.</span></span>|  
|<span data-ttu-id="19e35-128">**变量消息**</span><span class="sxs-lookup"><span data-stu-id="19e35-128">**Variable message**</span></span>|<span data-ttu-id="19e35-129">消息存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="19e35-129">The message is stored in a variable.</span></span> <span data-ttu-id="19e35-130">选择该值将显示动态选项 **VariableMessage**。</span><span class="sxs-lookup"><span data-stu-id="19e35-130">Selecting the value displays the dynamic option, **VariableMessage**.</span></span>|  
|<span data-ttu-id="19e35-131">**字符串消息**</span><span class="sxs-lookup"><span data-stu-id="19e35-131">**String message**</span></span>|<span data-ttu-id="19e35-132">消息存储在消息队列任务中。</span><span class="sxs-lookup"><span data-stu-id="19e35-132">The message is stored in the Message Queue task.</span></span> <span data-ttu-id="19e35-133">选择该值将显示动态选项 **StringMessage**。</span><span class="sxs-lookup"><span data-stu-id="19e35-133">Selecting the value displays the dynamic option, **StringMessage**.</span></span>|  
  
## <a name="messagetype-dynamic-options"></a><span data-ttu-id="19e35-134">MessageType 动态选项</span><span class="sxs-lookup"><span data-stu-id="19e35-134">MessageType Dynamic Options</span></span>  
  
### <a name="messagetype--data-file-message"></a><span data-ttu-id="19e35-135">MessageType = 数据文件消息</span><span class="sxs-lookup"><span data-stu-id="19e35-135">MessageType = Data file message</span></span>  
 <span data-ttu-id="19e35-136">**DataFileMessage**</span><span class="sxs-lookup"><span data-stu-id="19e35-136">**DataFileMessage**</span></span>  
 <span data-ttu-id="19e35-137">键入数据文件的路径，或单击省略号 (…) 后再定位到相应的文件。</span><span class="sxs-lookup"><span data-stu-id="19e35-137">Type the path of the data file, or click the ellipsis **(...)** and then locate the file.</span></span>  
  
### <a name="messagetype--variable-message"></a><span data-ttu-id="19e35-138">MessageType = 变量消息</span><span class="sxs-lookup"><span data-stu-id="19e35-138">MessageType = Variable message</span></span>  
 <span data-ttu-id="19e35-139">**VariableMessage**</span><span class="sxs-lookup"><span data-stu-id="19e35-139">**VariableMessage**</span></span>  
 <span data-ttu-id="19e35-140">键入变量名称，或单击省略号 (…) 后再选择相应的变量。</span><span class="sxs-lookup"><span data-stu-id="19e35-140">Type the variable names, or click the ellipsis **(...)** and then select the variables.</span></span> <span data-ttu-id="19e35-141">各变量之间用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="19e35-141">Variables are separated by commas.</span></span>  
  
 <span data-ttu-id="19e35-142">**相关主题：** 选择变量</span><span class="sxs-lookup"><span data-stu-id="19e35-142">**Related Topics:** Select Variables</span></span>  
  
### <a name="messagetype--string-message"></a><span data-ttu-id="19e35-143">MessageType = 字符串消息</span><span class="sxs-lookup"><span data-stu-id="19e35-143">MessageType = String message</span></span>  
 <span data-ttu-id="19e35-144">**StringMessage**</span><span class="sxs-lookup"><span data-stu-id="19e35-144">**StringMessage**</span></span>  
 <span data-ttu-id="19e35-145">键入字符串消息，或单击省略号 (…) 后在“输入字符串消息”对话框中键入消息。</span><span class="sxs-lookup"><span data-stu-id="19e35-145">Type the string message, or click the ellipsis **(...)** and then type the message in the **Enter String Message** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e35-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19e35-146">See Also</span></span>  
 <span data-ttu-id="19e35-147">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="19e35-147">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="19e35-148">[消息队列任务编辑器 &#40;常规页&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="19e35-148">[Message Queue Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="19e35-149">[消息队列任务编辑器 &#40;接收页面&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span><span class="sxs-lookup"><span data-stu-id="19e35-149">[Message Queue Task Editor &#40;Receive Page&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span></span>  
 [<span data-ttu-id="19e35-150">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="19e35-150">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
