---
title: 执行进程任务编辑器 (进程页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executeprocesstask.process.f1
helpviewer_keywords:
- Execute Process Task Editor
ms.assetid: 0fc22406-e79b-47a4-a7e4-108d4ce6202f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ce8629be2c07ae4caac4586b266936a908e71499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682361"
---
# <a name="execute-process-task-editor-process-page"></a><span data-ttu-id="9af82-102">执行进程任务编辑器（“进程”页）</span><span class="sxs-lookup"><span data-stu-id="9af82-102">Execute Process Task Editor (Process Page)</span></span>
  <span data-ttu-id="9af82-103">可以使用 **“执行进程任务编辑器”** 对话框的 **“进程”** 页配置执行进程的选项。</span><span class="sxs-lookup"><span data-stu-id="9af82-103">Use the **Process** page of the **Execute Process Task Editor** dialog box to configure the options that execute the process.</span></span> <span data-ttu-id="9af82-104">这些选项包括要运行的可执行文件、该可执行文件的位置、命令提示符参数以及提供输入及捕获输出的变量。</span><span class="sxs-lookup"><span data-stu-id="9af82-104">These options include the executable to run, its location, command prompt arguments, and the variables that provide input and capture output.</span></span>  
  
 <span data-ttu-id="9af82-105">若要了解此任务，请参阅 [Execute Process Task](control-flow/execute-process-task.md)。</span><span class="sxs-lookup"><span data-stu-id="9af82-105">To learn about this task, see [Execute Process Task](control-flow/execute-process-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9af82-106">选项</span><span class="sxs-lookup"><span data-stu-id="9af82-106">Options</span></span>  
 <span data-ttu-id="9af82-107">**RequireFullFileName**</span><span class="sxs-lookup"><span data-stu-id="9af82-107">**RequireFullFileName**</span></span>  
 <span data-ttu-id="9af82-108">指示在指定位置未找到可执行文件时该任务是否应失败。</span><span class="sxs-lookup"><span data-stu-id="9af82-108">Indicate whether the task should fail if the executable is not found at the specified location.</span></span>  
  
 <span data-ttu-id="9af82-109">**可执行文件**</span><span class="sxs-lookup"><span data-stu-id="9af82-109">**Executable**</span></span>  
 <span data-ttu-id="9af82-110">键入要运行的可执行文件的名称。</span><span class="sxs-lookup"><span data-stu-id="9af82-110">Type the name of the executable to run.</span></span>  
  
 <span data-ttu-id="9af82-111">**参数**</span><span class="sxs-lookup"><span data-stu-id="9af82-111">**Arguments**</span></span>  
 <span data-ttu-id="9af82-112">提供命令提示符参数。</span><span class="sxs-lookup"><span data-stu-id="9af82-112">Provide command prompt arguments.</span></span>  
  
 <span data-ttu-id="9af82-113">**WorkingDirectory**</span><span class="sxs-lookup"><span data-stu-id="9af82-113">**WorkingDirectory**</span></span>  
 <span data-ttu-id="9af82-114">键入包含可执行文件的文件夹的路径，或单击浏览 (…) 按钮定位到该文件夹  。</span><span class="sxs-lookup"><span data-stu-id="9af82-114">Type the path of the folder that contains the executable, or click the browse button **(...)** and locate the folder.</span></span>  
  
 <span data-ttu-id="9af82-115">**StandardInputVariable**</span><span class="sxs-lookup"><span data-stu-id="9af82-115">**StandardInputVariable**</span></span>  
 <span data-ttu-id="9af82-116">选择为进程提供输入的变量，或单击 \<**New variable...**> 创建新的变量：</span><span class="sxs-lookup"><span data-stu-id="9af82-116">Select a variable to provide the input to the process, or click \<**New variable...**> to create a new variable:</span></span>  
  
 <span data-ttu-id="9af82-117">**相关主题：**  [添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="9af82-117">**Related Topics:**  [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="9af82-118">**StandardOutputVariable**</span><span class="sxs-lookup"><span data-stu-id="9af82-118">**StandardOutputVariable**</span></span>  
 <span data-ttu-id="9af82-119">选择捕获进程输出的变量，或单击 \<**New variable...**> 创建新的变量。</span><span class="sxs-lookup"><span data-stu-id="9af82-119">Select a variable to capture the output of the process, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="9af82-120">**StandardErrorVariable**</span><span class="sxs-lookup"><span data-stu-id="9af82-120">**StandardErrorVariable**</span></span>  
 <span data-ttu-id="9af82-121">选择捕获处理器的错误输出的变量，或单击 \<**New variable...**> 创建新的变量。</span><span class="sxs-lookup"><span data-stu-id="9af82-121">Select a variable to capture the error output of the processor, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="9af82-122">**FailTaskIfReturnCodeIsNotSuccessValue**</span><span class="sxs-lookup"><span data-stu-id="9af82-122">**FailTaskIfReturnCodeIsNotSuccessValue**</span></span>  
 <span data-ttu-id="9af82-123">指示在进程退出代码与 **SuccessValue**中指定的值不同时任务是否失败。</span><span class="sxs-lookup"><span data-stu-id="9af82-123">Indicate whether the task fails if the process exit code is different from the value specified in **SuccessValue**.</span></span>  
  
 <span data-ttu-id="9af82-124">**SuccessValue**</span><span class="sxs-lookup"><span data-stu-id="9af82-124">**SuccessValue**</span></span>  
 <span data-ttu-id="9af82-125">指定可执行文件返回的用来指示进程成功的值。</span><span class="sxs-lookup"><span data-stu-id="9af82-125">Specify the value returned by the executable to indicate success.</span></span> <span data-ttu-id="9af82-126">默认情况下，此值设置为 **0**。</span><span class="sxs-lookup"><span data-stu-id="9af82-126">By default this value is set to **0**.</span></span>  
  
 <span data-ttu-id="9af82-127">**TimeOut**</span><span class="sxs-lookup"><span data-stu-id="9af82-127">**TimeOut**</span></span>  
 <span data-ttu-id="9af82-128">指定进程可以运行的秒数。</span><span class="sxs-lookup"><span data-stu-id="9af82-128">Specify the number of seconds that the process can run.</span></span> <span data-ttu-id="9af82-129">如果值为 **0** ，则表示不使用超时值，进程一直运行到处理完毕或出错为止。</span><span class="sxs-lookup"><span data-stu-id="9af82-129">A value of **0** indicates that no time-out value is used, and the process runs until it is completed or until an error occurs.</span></span>  
  
 <span data-ttu-id="9af82-130">**TerminateProcessAfterTimeOut**</span><span class="sxs-lookup"><span data-stu-id="9af82-130">**TerminateProcessAfterTimeOut**</span></span>  
 <span data-ttu-id="9af82-131">指示在 **TimeOut** 选项指定的超时期限过后是否强制结束进程。</span><span class="sxs-lookup"><span data-stu-id="9af82-131">Indicate whether the process is forced to end after the time-out period specified by the **TimeOut** option.</span></span> <span data-ttu-id="9af82-132">只有在 **TimeOut** 不为 **0**时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="9af82-132">This option is available only if **TimeOut** is not **0**.</span></span>  
  
 <span data-ttu-id="9af82-133">**WindowStyle**</span><span class="sxs-lookup"><span data-stu-id="9af82-133">**WindowStyle**</span></span>  
 <span data-ttu-id="9af82-134">指定用于运行进程的窗口样式。</span><span class="sxs-lookup"><span data-stu-id="9af82-134">Specify the window style in which to run the process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9af82-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9af82-135">See Also</span></span>  
 <span data-ttu-id="9af82-136">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9af82-136">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="9af82-137">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="9af82-137">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
