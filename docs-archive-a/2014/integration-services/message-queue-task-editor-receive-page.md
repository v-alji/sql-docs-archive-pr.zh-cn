---
title: 消息队列任务编辑器 (接收页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.receive.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 7028756d-1dcc-480c-bbcd-e9654f0772a0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f45aa579d37d1fdd3a3124eea972014ce839fdc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694516"
---
# <a name="message-queue-task-editor-receive-page"></a><span data-ttu-id="c0d7d-102">消息队列任务编辑器（“接收”页）</span><span class="sxs-lookup"><span data-stu-id="c0d7d-102">Message Queue Task Editor (Receive Page)</span></span>
  <span data-ttu-id="c0d7d-103">可以使用“消息队列任务编辑器”对话框的“接收”页，配置消息队列任务以接收 [!INCLUDE[msCoName](../includes/msconame-md.md)] 消息队列 (MSMQ) 消息   。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-103">Use the **Receive** page of the **Message Queue Task Editor** dialog box to configure a Message Queue task to receive [!INCLUDE[msCoName](../includes/msconame-md.md)] Message Queuing (MSMQ) messages.</span></span>  
  
 <span data-ttu-id="c0d7d-104">若要了解此任务，请参阅 [Message Queue Task](control-flow/message-queue-task.md)。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-104">To learn about this task, see [Message Queue Task](control-flow/message-queue-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c0d7d-105">选项</span><span class="sxs-lookup"><span data-stu-id="c0d7d-105">Options</span></span>  
 <span data-ttu-id="c0d7d-106">**RemoveFromMessageQueue**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-106">**RemoveFromMessageQueue**</span></span>  
 <span data-ttu-id="c0d7d-107">指示在接收后是否从队列中删除消息。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-107">Indicate whether to remove the message from the queue after it is received.</span></span> <span data-ttu-id="c0d7d-108">默认情况下，此值设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-108">By default, this value is set to `False`.</span></span>  
  
 <span data-ttu-id="c0d7d-109">**ErrorIfMessageTimeOut**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-109">**ErrorIfMessageTimeOut**</span></span>  
 <span data-ttu-id="c0d7d-110">指示当消息超时时任务是否失败，并显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-110">Indicate whether the task fails when the message times out, displaying an error message.</span></span> <span data-ttu-id="c0d7d-111">默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-111">The default is `False`.</span></span>  
  
 <span data-ttu-id="c0d7d-112">**TimeoutAfter**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-112">**TimeoutAfter**</span></span>  
 <span data-ttu-id="c0d7d-113">如果选择任务失败时显示错误消息，则请指定显示超时消息之前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-113">If you choose to display an error message on task failure, specify the number of seconds to wait before displaying the time-out message.</span></span>  
  
 <span data-ttu-id="c0d7d-114">**MessageType**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-114">**MessageType**</span></span>  
 <span data-ttu-id="c0d7d-115">选择消息类型。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-115">Select the message type.</span></span> <span data-ttu-id="c0d7d-116">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-116">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="c0d7d-117">值</span><span class="sxs-lookup"><span data-stu-id="c0d7d-117">Value</span></span>|<span data-ttu-id="c0d7d-118">说明</span><span class="sxs-lookup"><span data-stu-id="c0d7d-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c0d7d-119">**数据文件消息**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-119">**Data file message**</span></span>|<span data-ttu-id="c0d7d-120">消息存储在文件中。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-120">The message is stored in a file.</span></span> <span data-ttu-id="c0d7d-121">选择该值将显示动态选项 **DataFileMessage**。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-121">Selecting the value displays the dynamic option, **DataFileMessage**.</span></span>|  
|<span data-ttu-id="c0d7d-122">**变量消息**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-122">**Variable message**</span></span>|<span data-ttu-id="c0d7d-123">消息存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-123">The message is stored in a variable.</span></span> <span data-ttu-id="c0d7d-124">选择该值将显示动态选项 **VariableMessage**。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-124">Selecting the value displays the dynamic option, **VariableMessage**.</span></span>|  
|<span data-ttu-id="c0d7d-125">**字符串消息**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-125">**String message**</span></span>|<span data-ttu-id="c0d7d-126">消息存储在消息队列任务中。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-126">The message is stored in the Message Queue task.</span></span> <span data-ttu-id="c0d7d-127">选择该值将显示动态选项 **StringMessage**。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-127">Selecting the value displays the dynamic option, **StringMessage**.</span></span>|  
|<span data-ttu-id="c0d7d-128">**变量的字符串消息**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-128">**String message to variable**</span></span>|<span data-ttu-id="c0d7d-129">消息</span><span class="sxs-lookup"><span data-stu-id="c0d7d-129">The message</span></span><br /><br /> <span data-ttu-id="c0d7d-130">选择该值将显示动态选项 **StringMessage**。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-130">Selecting the value displays the dynamic option, **StringMessage**.</span></span>|  
  
## <a name="messagetype-dynamic-options"></a><span data-ttu-id="c0d7d-131">MessageType 动态选项</span><span class="sxs-lookup"><span data-stu-id="c0d7d-131">MessageType Dynamic Options</span></span>  
  
### <a name="messagetype--data-file-message"></a><span data-ttu-id="c0d7d-132">MessageType = 数据文件消息</span><span class="sxs-lookup"><span data-stu-id="c0d7d-132">MessageType = Data file message</span></span>  
 <span data-ttu-id="c0d7d-133">**SaveFileAs**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-133">**SaveFileAs**</span></span>  
 <span data-ttu-id="c0d7d-134">键入要使用的文件的路径，或单击省略号按钮 (…) 后再定位到该文件。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-134">Type the path of the file to use, or click the ellipsis button **(...)** and then locate the file.</span></span>  
  
 <span data-ttu-id="c0d7d-135">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-135">**Overwrite**</span></span>  
 <span data-ttu-id="c0d7d-136">指示在保存数据文件消息的内容时是否覆盖现有文件中的数据。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-136">Indicate whether to overwrite the data in an existing file when saving the contents of a data file message.</span></span> <span data-ttu-id="c0d7d-137">默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-137">The default is `False`.</span></span>  
  
 <span data-ttu-id="c0d7d-138">**筛选器**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-138">**Filter**</span></span>  
 <span data-ttu-id="c0d7d-139">指定是否对消息应用筛选器。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-139">Specify whether to apply a filter to the message.</span></span> <span data-ttu-id="c0d7d-140">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-140">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="c0d7d-141">值</span><span class="sxs-lookup"><span data-stu-id="c0d7d-141">Value</span></span>|<span data-ttu-id="c0d7d-142">说明</span><span class="sxs-lookup"><span data-stu-id="c0d7d-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c0d7d-143">**无筛选器**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-143">**No filter**</span></span>|<span data-ttu-id="c0d7d-144">该任务不筛选消息。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-144">The task does not filter messages.</span></span> <span data-ttu-id="c0d7d-145">选择该值将显示动态选项 **IdentifierReadOnly**。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-145">Selecting the value displays the dynamic option, **IdentifierReadOnly**.</span></span>|  
|<span data-ttu-id="c0d7d-146">**来源包**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-146">**From package**</span></span>|<span data-ttu-id="c0d7d-147">该消息仅接收来自指定包的消息。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-147">The message receives only messages from the specified package.</span></span> <span data-ttu-id="c0d7d-148">选择该值将显示动态选项 **Identifier**。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-148">Selecting the value displays the dynamic option, **Identifier**.</span></span>|  
  
### <a name="filter-dynamic-options"></a><span data-ttu-id="c0d7d-149">Filter 动态选项</span><span class="sxs-lookup"><span data-stu-id="c0d7d-149">Filter Dynamic Options</span></span>  
  
#### <a name="filter--no-filter"></a><span data-ttu-id="c0d7d-150">Filter = 无筛选器</span><span class="sxs-lookup"><span data-stu-id="c0d7d-150">Filter = No filter</span></span>  
 <span data-ttu-id="c0d7d-151">**IdentifierReadOnly**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-151">**IdentifierReadOnly**</span></span>  
 <span data-ttu-id="c0d7d-152">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-152">This option is read-only.</span></span> <span data-ttu-id="c0d7d-153">如果以前设置了 Filter 属性，此选项可能为空或包含包的 GUID。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-153">It may be blank or contain the GUID of a package when the Filter property was previously set.</span></span>  
  
#### <a name="filter--from-package"></a><span data-ttu-id="c0d7d-154">Filter = 来源包</span><span class="sxs-lookup"><span data-stu-id="c0d7d-154">Filter = From package</span></span>  
 <span data-ttu-id="c0d7d-155">**标识符**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-155">**Identifier**</span></span>  
 <span data-ttu-id="c0d7d-156">如果选择应用筛选器，请键入可以从中接收消息的包的唯一标识符，或者单击省略号按钮 (…)，再指定包。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-156">If you choose to apply a filter, type the unique identifier of the package from which messages can be received, or click the ellipsis button **(...)** and then specify the package.</span></span>  
  
 <span data-ttu-id="c0d7d-157">**相关主题：** [选择包](control-flow/select-a-package.md)</span><span class="sxs-lookup"><span data-stu-id="c0d7d-157">**Related Topics:** [Select a Package](control-flow/select-a-package.md)</span></span>  
  
### <a name="messagetype--variable-message"></a><span data-ttu-id="c0d7d-158">MessageType = 变量消息</span><span class="sxs-lookup"><span data-stu-id="c0d7d-158">MessageType = Variable message</span></span>  
 <span data-ttu-id="c0d7d-159">**筛选器**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-159">**Filter**</span></span>  
 <span data-ttu-id="c0d7d-160">指定是否将筛选器应用到消息。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-160">Specify whether to apply a filter to messages.</span></span> <span data-ttu-id="c0d7d-161">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-161">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="c0d7d-162">值</span><span class="sxs-lookup"><span data-stu-id="c0d7d-162">Value</span></span>|<span data-ttu-id="c0d7d-163">说明</span><span class="sxs-lookup"><span data-stu-id="c0d7d-163">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c0d7d-164">**无筛选器**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-164">**No filter**</span></span>|<span data-ttu-id="c0d7d-165">该任务不筛选消息。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-165">The task does not filter messages.</span></span> <span data-ttu-id="c0d7d-166">选择该值将显示动态选项 **IdentifierReadOnly**。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-166">Selecting the value displays the dynamic option, **IdentifierReadOnly**.</span></span>|  
|<span data-ttu-id="c0d7d-167">**来源包**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-167">**From package**</span></span>|<span data-ttu-id="c0d7d-168">该消息仅接收来自指定包的消息。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-168">The message receives only messages from the specified package.</span></span> <span data-ttu-id="c0d7d-169">选择该值将显示动态选项 **Identifier**。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-169">Selecting the value displays the dynamic option, **Identifier**.</span></span>|  
  
 <span data-ttu-id="c0d7d-170">**变量**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-170">**Variable**</span></span>  
 <span data-ttu-id="c0d7d-171">键入变量名称，或单击“\<**New variable...**>”，然后配置新的变量。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-171">Type the variable name, or click \<**New variable...**> and then configure a new variable.</span></span>  
  
 <span data-ttu-id="c0d7d-172">**相关主题：** [添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="c0d7d-172">**Related Topics:** [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="filter-dynamic-options"></a><span data-ttu-id="c0d7d-173">Filter 动态选项</span><span class="sxs-lookup"><span data-stu-id="c0d7d-173">Filter Dynamic Options</span></span>  
  
#### <a name="filter--no-filter"></a><span data-ttu-id="c0d7d-174">Filter = 无筛选器</span><span class="sxs-lookup"><span data-stu-id="c0d7d-174">Filter = No filter</span></span>  
 <span data-ttu-id="c0d7d-175">**IdentifierReadOnly**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-175">**IdentifierReadOnly**</span></span>  
 <span data-ttu-id="c0d7d-176">此选项为空白。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-176">This option is blank.</span></span>  
  
#### <a name="filter--from-package"></a><span data-ttu-id="c0d7d-177">Filter = 来源包</span><span class="sxs-lookup"><span data-stu-id="c0d7d-177">Filter = From package</span></span>  
 <span data-ttu-id="c0d7d-178">**标识符**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-178">**Identifier**</span></span>  
 <span data-ttu-id="c0d7d-179">如果选择应用筛选器，请键入可以从中接收消息的包的唯一标识符，或者单击省略号按钮 (…)，再指定包。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-179">If you choose to apply a filter, type the unique identifier of the package from which messages can be received, or click the ellipsis button **(...)** and then specify the package.</span></span>  
  
 <span data-ttu-id="c0d7d-180">**相关主题：** [选择包](control-flow/select-a-package.md)</span><span class="sxs-lookup"><span data-stu-id="c0d7d-180">**Related Topics:** [Select a Package](control-flow/select-a-package.md)</span></span>  
  
### <a name="messagetype--string-message"></a><span data-ttu-id="c0d7d-181">MessageType = 字符串消息</span><span class="sxs-lookup"><span data-stu-id="c0d7d-181">MessageType = String message</span></span>  
 <span data-ttu-id="c0d7d-182">**比较**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-182">**Compare**</span></span>  
 <span data-ttu-id="c0d7d-183">指定是否将筛选器应用到消息。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-183">Specify whether to apply a filter to messages.</span></span> <span data-ttu-id="c0d7d-184">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-184">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="c0d7d-185">值</span><span class="sxs-lookup"><span data-stu-id="c0d7d-185">Value</span></span>|<span data-ttu-id="c0d7d-186">说明</span><span class="sxs-lookup"><span data-stu-id="c0d7d-186">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c0d7d-187">无</span><span class="sxs-lookup"><span data-stu-id="c0d7d-187">**None**</span></span>|<span data-ttu-id="c0d7d-188">不对消息进行比较。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-188">Messages are not compared.</span></span>|  
|<span data-ttu-id="c0d7d-189">**完全匹配**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-189">**Exact match**</span></span>|<span data-ttu-id="c0d7d-190">消息必须与 **CompareString** 选项中的字符串完全匹配。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-190">Messages must match exactly the string in the **CompareString** option.</span></span>|  
|<span data-ttu-id="c0d7d-191">**忽略大小写**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-191">**Ignore case**</span></span>|<span data-ttu-id="c0d7d-192">消息必须与 **CompareString** 选项中的字符串匹配，但在比较时不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-192">Message must match the string in the **CompareString** option, but the comparison is not case sensitive.</span></span>|  
|<span data-ttu-id="c0d7d-193">**包含**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-193">**Containing**</span></span>|<span data-ttu-id="c0d7d-194">消息必须包含 **CompareString** 选项中的字符串。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-194">Message must contain the string in the **CompareString** option.</span></span>|  
  
 <span data-ttu-id="c0d7d-195">**CompareString**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-195">**CompareString**</span></span>  
 <span data-ttu-id="c0d7d-196">除非将 **Compare** 选项设置为“无”  ，否则请提供与消息进行比较的字符串。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-196">Unless the **Compare** option is set to **None**, provide the string to which the message is compared.</span></span>  
  
### <a name="messagetype--string-message-to-variable"></a><span data-ttu-id="c0d7d-197">MessageType = 变量的字符串消息</span><span class="sxs-lookup"><span data-stu-id="c0d7d-197">MessageType = String message to variable</span></span>  
 <span data-ttu-id="c0d7d-198">**比较**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-198">**Compare**</span></span>  
 <span data-ttu-id="c0d7d-199">指定是否将筛选器应用到消息。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-199">Specify whether to apply a filter to messages.</span></span> <span data-ttu-id="c0d7d-200">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-200">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="c0d7d-201">值</span><span class="sxs-lookup"><span data-stu-id="c0d7d-201">Value</span></span>|<span data-ttu-id="c0d7d-202">说明</span><span class="sxs-lookup"><span data-stu-id="c0d7d-202">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c0d7d-203">无</span><span class="sxs-lookup"><span data-stu-id="c0d7d-203">**None**</span></span>|<span data-ttu-id="c0d7d-204">不对消息进行比较。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-204">Messages are not compared.</span></span>|  
|<span data-ttu-id="c0d7d-205">**完全匹配**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-205">**Exact match**</span></span>|<span data-ttu-id="c0d7d-206">消息必须与 **CompareString** 选项中的字符串完全匹配。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-206">The message must match exactly the string in the **CompareString** option.</span></span>|  
|<span data-ttu-id="c0d7d-207">**忽略大小写**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-207">**Ignore case**</span></span>|<span data-ttu-id="c0d7d-208">消息必须与 **CompareString** 选项中的字符串匹配，但在比较时不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-208">The message must match the string in the **CompareString** option but the comparison is not case sensitive.</span></span>|  
|<span data-ttu-id="c0d7d-209">**包含**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-209">**Containing**</span></span>|<span data-ttu-id="c0d7d-210">消息必须包含 **CompareString** 选项中的字符串。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-210">The message must contain the string in the **CompareString** option.</span></span>|  
  
 <span data-ttu-id="c0d7d-211">**CompareString**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-211">**CompareString**</span></span>  
 <span data-ttu-id="c0d7d-212">除非将 **Compare** 选项设置为“无”  ，否则请提供与消息进行比较的字符串。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-212">Unless the **Compare** option is set to **None**, provide the string to which the message is compared.</span></span>  
  
 <span data-ttu-id="c0d7d-213">**变量**</span><span class="sxs-lookup"><span data-stu-id="c0d7d-213">**Variable**</span></span>  
 <span data-ttu-id="c0d7d-214">键入要保存接收到的消息的变量名，或单击“\<**New variable...**>”，然后配置新的变量。</span><span class="sxs-lookup"><span data-stu-id="c0d7d-214">Type the name of the variable to hold the received message, or click \<**New variable...**> and then configure a new variable.</span></span>  
  
 <span data-ttu-id="c0d7d-215">**相关主题：** [添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="c0d7d-215">**Related Topics:** [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0d7d-216">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0d7d-216">See Also</span></span>  
 <span data-ttu-id="c0d7d-217">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c0d7d-217">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="c0d7d-218">[消息队列任务编辑器 &#40;常规页&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="c0d7d-218">[Message Queue Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="c0d7d-219">[消息队列任务编辑器 &#40;发送页面&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span><span class="sxs-lookup"><span data-stu-id="c0d7d-219">[Message Queue Task Editor &#40;Send Page&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span></span>  
 <span data-ttu-id="c0d7d-220">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="c0d7d-220">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="c0d7d-221">消息队列任务</span><span class="sxs-lookup"><span data-stu-id="c0d7d-221">Message Queue Task</span></span>](control-flow/message-queue-task.md)  
  
  
