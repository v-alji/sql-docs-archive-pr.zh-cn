---
title: FTP 任务编辑器 (文件传输页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.filetransfer.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 37e52220-feb2-474c-ad88-fa1b1059acd4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8094051e93c4165be6ae186bde394f9271d60669
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579640"
---
# <a name="ftp-task-editor-file-transfer-page"></a><span data-ttu-id="e456e-102">FTP 任务编辑器（“文件传输”页）</span><span class="sxs-lookup"><span data-stu-id="e456e-102">FTP Task Editor (File Transfer Page)</span></span>
  <span data-ttu-id="e456e-103">可以使用 **“FTP 任务编辑器”** 对话框的 **“文件传输”** 页配置任务执行的 FTP 操作。</span><span class="sxs-lookup"><span data-stu-id="e456e-103">Use the **File Transfer** page of the **FTP Task Editor** dialog box to configure the FTP operation that the task performs.</span></span>  
  
 <span data-ttu-id="e456e-104">若要了解此任务，请参阅 [FTP 任务](control-flow/ftp-task.md)。</span><span class="sxs-lookup"><span data-stu-id="e456e-104">To learn about this task, see [FTP Task](control-flow/ftp-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e456e-105">选项</span><span class="sxs-lookup"><span data-stu-id="e456e-105">Options</span></span>  
 <span data-ttu-id="e456e-106">**IsRemotePathVariable**</span><span class="sxs-lookup"><span data-stu-id="e456e-106">**IsRemotePathVariable**</span></span>  
 <span data-ttu-id="e456e-107">指示远程路径是否存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="e456e-107">Indicate whether the remote path is stored in a variable.</span></span> <span data-ttu-id="e456e-108">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="e456e-108">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="e456e-109">值</span><span class="sxs-lookup"><span data-stu-id="e456e-109">Value</span></span>|<span data-ttu-id="e456e-110">说明</span><span class="sxs-lookup"><span data-stu-id="e456e-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e456e-111">**True**</span><span class="sxs-lookup"><span data-stu-id="e456e-111">**True**</span></span>|<span data-ttu-id="e456e-112">目标路径存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="e456e-112">The destination path is stored in a variable.</span></span> <span data-ttu-id="e456e-113">选择该值将显示动态选项 **RemoteVariable**。</span><span class="sxs-lookup"><span data-stu-id="e456e-113">Selecting the value displays the dynamic option, **RemoteVariable**.</span></span>|  
|<span data-ttu-id="e456e-114">**False**</span><span class="sxs-lookup"><span data-stu-id="e456e-114">**False**</span></span>|<span data-ttu-id="e456e-115">目标路径在文件连接管理器中指定。</span><span class="sxs-lookup"><span data-stu-id="e456e-115">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="e456e-116">选择该值将显示动态选项 **RemotePath**。</span><span class="sxs-lookup"><span data-stu-id="e456e-116">Selecting the value displays the dynamic option, **RemotePath**.</span></span>|  
  
 <span data-ttu-id="e456e-117">**OverwriteFileAtDestination**</span><span class="sxs-lookup"><span data-stu-id="e456e-117">**OverwriteFileAtDestination**</span></span>  
 <span data-ttu-id="e456e-118">指定是否可以覆盖目标位置中的文件。</span><span class="sxs-lookup"><span data-stu-id="e456e-118">Specify whether a file at the destination can be overwritten.</span></span>  
  
 <span data-ttu-id="e456e-119">**IsLocalPathVariable**</span><span class="sxs-lookup"><span data-stu-id="e456e-119">**IsLocalPathVariable**</span></span>  
 <span data-ttu-id="e456e-120">指示本地路径是否存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="e456e-120">Indicate whether the local path is stored in a variable.</span></span> <span data-ttu-id="e456e-121">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="e456e-121">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="e456e-122">值</span><span class="sxs-lookup"><span data-stu-id="e456e-122">Value</span></span>|<span data-ttu-id="e456e-123">说明</span><span class="sxs-lookup"><span data-stu-id="e456e-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e456e-124">**True**</span><span class="sxs-lookup"><span data-stu-id="e456e-124">**True**</span></span>|<span data-ttu-id="e456e-125">目标路径存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="e456e-125">The destination path is stored in a variable.</span></span> <span data-ttu-id="e456e-126">选择该值将显示动态选项 **LocalVariable**。</span><span class="sxs-lookup"><span data-stu-id="e456e-126">Selecting the value displays the dynamic option, **LocalVariable**.</span></span>|  
|<span data-ttu-id="e456e-127">**False**</span><span class="sxs-lookup"><span data-stu-id="e456e-127">**False**</span></span>|<span data-ttu-id="e456e-128">目标路径在文件连接管理器中指定。</span><span class="sxs-lookup"><span data-stu-id="e456e-128">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="e456e-129">选择该值将显示动态选项 **LocalPath**。</span><span class="sxs-lookup"><span data-stu-id="e456e-129">Selecting the value displays the dynamic option, **LocalPath**.</span></span>|  
  
 <span data-ttu-id="e456e-130">**操作**</span><span class="sxs-lookup"><span data-stu-id="e456e-130">**Operation**</span></span>  
 <span data-ttu-id="e456e-131">选择要执行的 FTP 操作。</span><span class="sxs-lookup"><span data-stu-id="e456e-131">Select the FTP operation to perform.</span></span> <span data-ttu-id="e456e-132">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="e456e-132">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="e456e-133">值</span><span class="sxs-lookup"><span data-stu-id="e456e-133">Value</span></span>|<span data-ttu-id="e456e-134">说明</span><span class="sxs-lookup"><span data-stu-id="e456e-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e456e-135">**发送文件**</span><span class="sxs-lookup"><span data-stu-id="e456e-135">**Send files**</span></span>|<span data-ttu-id="e456e-136">发送文件。</span><span class="sxs-lookup"><span data-stu-id="e456e-136">Send files.</span></span> <span data-ttu-id="e456e-137">选择此值将显示动态选项 **LocalVariable**、 **LocalPathRemoteVariable** 和 **RemotePath**。</span><span class="sxs-lookup"><span data-stu-id="e456e-137">Selecting this value displays the dynamic options, **LocalVariable**, **LocalPathRemoteVariable** and **RemotePath**.</span></span>|  
|<span data-ttu-id="e456e-138">**接收文件**</span><span class="sxs-lookup"><span data-stu-id="e456e-138">**Receive files**</span></span>|<span data-ttu-id="e456e-139">接收文件。</span><span class="sxs-lookup"><span data-stu-id="e456e-139">Receive files.</span></span> <span data-ttu-id="e456e-140">选择此值将显示动态选项 **LocalVariable**、 **LocalPathRemoteVariable** 和 **RemotePath**。</span><span class="sxs-lookup"><span data-stu-id="e456e-140">Selecting this value displays the dynamic options, **LocalVariable**, **LocalPathRemoteVariable** and **RemotePath**.</span></span>|  
|<span data-ttu-id="e456e-141">**创建本地目录**</span><span class="sxs-lookup"><span data-stu-id="e456e-141">**Create local directory**</span></span>|<span data-ttu-id="e456e-142">创建本地目录。</span><span class="sxs-lookup"><span data-stu-id="e456e-142">Create a local directory.</span></span> <span data-ttu-id="e456e-143">选择此值将显示动态选项 **LocalVariable** 和 **LocalPath**。</span><span class="sxs-lookup"><span data-stu-id="e456e-143">Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.</span></span>|  
|<span data-ttu-id="e456e-144">**创建远程目录**</span><span class="sxs-lookup"><span data-stu-id="e456e-144">**Create remote directory**</span></span>|<span data-ttu-id="e456e-145">创建远程目录。</span><span class="sxs-lookup"><span data-stu-id="e456e-145">Create a remote directory.</span></span> <span data-ttu-id="e456e-146">选择此值将显示动态选项 **RemoteVariable** 和 **RemotelPath**。</span><span class="sxs-lookup"><span data-stu-id="e456e-146">Selecting this value displays the dynamic options, **RemoteVariable** and **RemotelPath**.</span></span>|  
|<span data-ttu-id="e456e-147">**删除本地目录**</span><span class="sxs-lookup"><span data-stu-id="e456e-147">**Remove local directory**</span></span>|<span data-ttu-id="e456e-148">删除本地目录。</span><span class="sxs-lookup"><span data-stu-id="e456e-148">Removes a local directory.</span></span> <span data-ttu-id="e456e-149">选择此值将显示动态选项 **LocalVariable** 和 **LocalPath**。</span><span class="sxs-lookup"><span data-stu-id="e456e-149">Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.</span></span>|  
|<span data-ttu-id="e456e-150">**删除远程目录**</span><span class="sxs-lookup"><span data-stu-id="e456e-150">**Remove remote directory**</span></span>|<span data-ttu-id="e456e-151">删除远程目录。</span><span class="sxs-lookup"><span data-stu-id="e456e-151">Remove a remote directory.</span></span> <span data-ttu-id="e456e-152">选择此值将显示动态选项 **RemoteVariable** 和 **RemotePath**。</span><span class="sxs-lookup"><span data-stu-id="e456e-152">Selecting this value displays the dynamic options, **RemoteVariable** and **RemotePath**.</span></span>|  
|<span data-ttu-id="e456e-153">**删除本地文件**</span><span class="sxs-lookup"><span data-stu-id="e456e-153">**Delete local files**</span></span>|<span data-ttu-id="e456e-154">删除本地文件。</span><span class="sxs-lookup"><span data-stu-id="e456e-154">Delete local files.</span></span> <span data-ttu-id="e456e-155">选择此值将显示动态选项 **LocalVariable** 和 **LocalPath**。</span><span class="sxs-lookup"><span data-stu-id="e456e-155">Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.</span></span>|  
|<span data-ttu-id="e456e-156">**删除远程文件**</span><span class="sxs-lookup"><span data-stu-id="e456e-156">**Delete remote files**</span></span>|<span data-ttu-id="e456e-157">删除远程文件。</span><span class="sxs-lookup"><span data-stu-id="e456e-157">Delete remote files.</span></span> <span data-ttu-id="e456e-158">选择此值将显示动态选项 **RemoteVariable** 和 **RemotePath**。</span><span class="sxs-lookup"><span data-stu-id="e456e-158">Selecting this value displays the dynamic options, **RemoteVariable** and **RemotePath**.</span></span>|  
  
 <span data-ttu-id="e456e-159">**IsTransferASCII**</span><span class="sxs-lookup"><span data-stu-id="e456e-159">**IsTransferASCII**</span></span>  
 <span data-ttu-id="e456e-160">指示是否应以 ASCII 模式传输从远程 FTP 服务器传输来的文件和传输到远程 FTP 服务器上的文件。</span><span class="sxs-lookup"><span data-stu-id="e456e-160">Indicate whether files transferred to and from the remote FTP server should be transferred in ASCII mode.</span></span>  
  
## <a name="isremotepathvariable-dynamic-options"></a><span data-ttu-id="e456e-161">IsRemotePathVariable 动态选项</span><span class="sxs-lookup"><span data-stu-id="e456e-161">IsRemotePathVariable Dynamic Options</span></span>  
  
### <a name="isremotepathvariable--true"></a><span data-ttu-id="e456e-162">IsRemotePathVariable = True</span><span class="sxs-lookup"><span data-stu-id="e456e-162">IsRemotePathVariable = True</span></span>  
 <span data-ttu-id="e456e-163">**RemoteVariable**</span><span class="sxs-lookup"><span data-stu-id="e456e-163">**RemoteVariable**</span></span>  
 <span data-ttu-id="e456e-164">选择用户定义的现有变量，或单击“\<**New variable...**>”以创建用户定义变量。</span><span class="sxs-lookup"><span data-stu-id="e456e-164">Select an existing user-defined variable, or click \<**New variable...**> to create a user-defined variable.</span></span>  
  
 <span data-ttu-id="e456e-165">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、添加变量</span><span class="sxs-lookup"><span data-stu-id="e456e-165">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), Add Variable</span></span>  
  
### <a name="isremotepathvariable--false"></a><span data-ttu-id="e456e-166">IsRemotePathVariable = False</span><span class="sxs-lookup"><span data-stu-id="e456e-166">IsRemotePathVariable = False</span></span>  
 <span data-ttu-id="e456e-167">**RemotePath**</span><span class="sxs-lookup"><span data-stu-id="e456e-167">**RemotePath**</span></span>  
 <span data-ttu-id="e456e-168">选择现有 FTP 连接管理器，或单击“\<**New connection...**>”以创建连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e456e-168">Select an existing FTP connection manager, or click \<**New connection...**> to create a connection manager.</span></span>  
  
 <span data-ttu-id="e456e-169">**相关主题：** [FTP 连接管理器](connection-manager/ftp-connection-manager.md)、[FTP 连接管理器编辑器](../../2014/integration-services/ftp-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="e456e-169">**Related Topics:** [FTP Connection Manager](connection-manager/ftp-connection-manager.md), [FTP Connection Manager Editor](../../2014/integration-services/ftp-connection-manager-editor.md)</span></span>  
  
## <a name="islocalpathvariable-dynamic-options"></a><span data-ttu-id="e456e-170">IsLocalPathVariable 动态选项</span><span class="sxs-lookup"><span data-stu-id="e456e-170">IsLocalPathVariable Dynamic Options</span></span>  
  
### <a name="islocalpathvariable--true"></a><span data-ttu-id="e456e-171">IsLocalPathVariable = True</span><span class="sxs-lookup"><span data-stu-id="e456e-171">IsLocalPathVariable = True</span></span>  
 <span data-ttu-id="e456e-172">**LocalVariable**</span><span class="sxs-lookup"><span data-stu-id="e456e-172">**LocalVariable**</span></span>  
 <span data-ttu-id="e456e-173">选择用户定义的现有变量，或单击“\<**New variable...**>”以创建变量。</span><span class="sxs-lookup"><span data-stu-id="e456e-173">Select an existing user-defined variable, or click \<**New variable...**> to create a variable.</span></span>  
  
 <span data-ttu-id="e456e-174">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、添加变量</span><span class="sxs-lookup"><span data-stu-id="e456e-174">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), Add Variable</span></span>  
  
### <a name="islocalpathvariable--false"></a><span data-ttu-id="e456e-175">IsLocalPathVariable = False</span><span class="sxs-lookup"><span data-stu-id="e456e-175">IsLocalPathVariable = False</span></span>  
 <span data-ttu-id="e456e-176">**LocalPath**</span><span class="sxs-lookup"><span data-stu-id="e456e-176">**LocalPath**</span></span>  
 <span data-ttu-id="e456e-177">选择现有“文件连接管理器”，或单击“\<**New connection...**>创建一个连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e456e-177">Select an existing File connection manager, or click \<**New connection...**> to create a connection manager.</span></span>  
  
 <span data-ttu-id="e456e-178">**相关主题**： [Flat File Connection Manager](connection-manager/file-connection-manager.md)、 [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="e456e-178">**Related Topics**: [Flat File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e456e-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e456e-179">See Also</span></span>  
 <span data-ttu-id="e456e-180">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e456e-180">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e456e-181">[FTP 任务编辑器 &#40;常规 "页面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="e456e-181">[FTP Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="e456e-182">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="e456e-182">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
