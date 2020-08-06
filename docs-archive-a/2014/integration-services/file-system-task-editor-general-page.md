---
title: 文件系统任务编辑器 ("常规" 页) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.filesystemtask.general.f1
helpviewer_keywords:
- File System Task Editor
ms.assetid: 51fe6614-3418-4eff-a28d-02ea31cc9aa9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e893f667c2a32fbc667c375dc57647d1aff1b806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693406"
---
# <a name="file-system-task-editor-general-page"></a><span data-ttu-id="e3d0a-102">文件系统任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="e3d0a-102">File System Task Editor (General Page)</span></span>
  <span data-ttu-id="e3d0a-103">可以使用 **“文件系统任务编辑器”** 对话框的 **“常规”** 页，配置任务执行的文件系统操作。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-103">Use the **General** page of the **File System Task Editor** dialog to configure the file system operation that the task performs.</span></span>  
  
 <span data-ttu-id="e3d0a-104">若要了解此任务，请参阅 [File System Task](control-flow/file-system-task.md)。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-104">To learn about this task, see [File System Task](control-flow/file-system-task.md).</span></span>  
  
 <span data-ttu-id="e3d0a-105">必须通过设置 SourceConnection 和 DestinationConnection 属性来指定源和目标连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-105">You must specify a source and destination connection manager by setting the SourceConnection and DestinationConnection properties.</span></span> <span data-ttu-id="e3d0a-106">您可以提供指向任务将其用作源或目标的文件的文件连接管理器的名称，如果文件路径存储在变量中，则可以提供变量的名称。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-106">You can either provide the names of File connection managers that point to the files that the task uses as a source or destination, or if the paths of the files are stored in variables, you can provide the names of the variables.</span></span> <span data-ttu-id="e3d0a-107">若要使用变量来存储文件路径，必须先将源连接的 IsSourcePathVariable 选项和目标连接的 IsDestinationPatheVariable 选项设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-107">To use variables to store the file paths, you must set first set the IsSourcePathVariable option for the source connection and the IsDestinationPatheVariable option for the destination connection to **True**.</span></span> <span data-ttu-id="e3d0a-108">然后，您可以选择使用现有的系统或用户定义变量，也可以创建新变量。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-108">You can then choose the existing system or user-defined variables to use, or you can create new variables.</span></span> <span data-ttu-id="e3d0a-109">在 **“添加变量”** 对话框中，可以配置和指定变量的作用域。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-109">In the **Add Variable** dialog box, you can configure and specify the scope of the variables.</span></span> <span data-ttu-id="e3d0a-110">该作用域必须是文件系统任务或父容器。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-110">The scope must be the File System task or a parent container.</span></span> <span data-ttu-id="e3d0a-111">有关详细信息，请参阅 [Integration Services (SSIS) 变量](integration-services-ssis-variables.md)和[在包中使用变量](../../2014/integration-services/use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-111">For more information see, [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) and [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e3d0a-112">若要覆盖为和属性选择的 `SourceConnection` 变量 `DestinationConnection` ，请为 "**源**" 和 "**目标**" 属性输入表达式。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-112">To override the variables you selected for the `SourceConnection` and `DestinationConnection` properties, enter an expression for the **Source** and **Destination** properties.</span></span> <span data-ttu-id="e3d0a-113">在 **“文件系统任务编辑器”** 的 **“表达式”** 页上输入表达式。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-113">You enter expressions on the **Expressions** page of the **File System Task Editor**.</span></span> <span data-ttu-id="e3d0a-114">例如，若要设置任务作为目标的文件路径，您可能要在某些情况下使用变量 A 并在另一些情况下使用变量 B。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-114">For example, to set the path of the files that the task uses as a destination, you may want to use variable A under certain conditions and use variable B under other conditions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e3d0a-115">文件系统任务对单个文件或目录进行操作。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-115">The File System task operates on a single file or directory.</span></span> <span data-ttu-id="e3d0a-116">因此，该任务不支持使用通配符对多个文件或目录执行同一操作。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-116">Therefore, this task does not support the use of wildcard characters to perform the same operation on multiple files or directories.</span></span> <span data-ttu-id="e3d0a-117">若要使此文件系统任务对多个文件或目录重复执行某个操作，请将此文件系统任务放置于一个 Foreach 循环容器中。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-117">To have the File System task repeat an operation on multiple files or directories, put the File System task in a Foreach Loop container.</span></span> <span data-ttu-id="e3d0a-118">有关详细信息，请参阅 [File System Task](control-flow/file-system-task.md)。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-118">For more information, see [File System Task](control-flow/file-system-task.md).</span></span>  
  
 <span data-ttu-id="e3d0a-119">您可以使用表达式来使用不同的变量</span><span class="sxs-lookup"><span data-stu-id="e3d0a-119">You can use expressions to use different variables for the</span></span>  
  
## <a name="options"></a><span data-ttu-id="e3d0a-120">选项</span><span class="sxs-lookup"><span data-stu-id="e3d0a-120">Options</span></span>  
 <span data-ttu-id="e3d0a-121">**IsDestinationPathVariable**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-121">**IsDestinationPathVariable**</span></span>  
 <span data-ttu-id="e3d0a-122">指示目标路径是否存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-122">Indicate whether the destination path is stored in a variable.</span></span> <span data-ttu-id="e3d0a-123">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-123">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="e3d0a-124">值</span><span class="sxs-lookup"><span data-stu-id="e3d0a-124">Value</span></span>|<span data-ttu-id="e3d0a-125">说明</span><span class="sxs-lookup"><span data-stu-id="e3d0a-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e3d0a-126">**True**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-126">**True**</span></span>|<span data-ttu-id="e3d0a-127">目标路径存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-127">The destination path is stored in a variable.</span></span> <span data-ttu-id="e3d0a-128">选择此值将显示动态选项 **DestinationVariable**。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-128">Selecting this value displays the dynamic option, **DestinationVariable**.</span></span>|  
|<span data-ttu-id="e3d0a-129">**False**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-129">**False**</span></span>|<span data-ttu-id="e3d0a-130">目标路径在文件连接管理器中指定。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-130">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="e3d0a-131">选择此值将显示动态选项 `DestinationConnection` 。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-131">Selecting this value displays the dynamic option, `DestinationConnection`.</span></span>|  
  
 <span data-ttu-id="e3d0a-132">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-132">**OverwriteDestination**</span></span>  
 <span data-ttu-id="e3d0a-133">指定操作是否可以覆盖目标目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-133">Specify whether the operation can overwrite files in the destination directory.</span></span>  
  
 <span data-ttu-id="e3d0a-134">**名称**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-134">**Name**</span></span>  
 <span data-ttu-id="e3d0a-135">为文件系统任务提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-135">Provide a unique name for the File System task.</span></span> <span data-ttu-id="e3d0a-136">此名称用作任务图标中的标签。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-136">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e3d0a-137">任务名称在一个包内必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-137">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="e3d0a-138">**说明**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-138">**Description**</span></span>  
 <span data-ttu-id="e3d0a-139">键入文件系统任务的说明。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-139">Type a description of the File System task.</span></span>  
  
 <span data-ttu-id="e3d0a-140">**操作**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-140">**Operation**</span></span>  
 <span data-ttu-id="e3d0a-141">选择要执行的文件系统操作。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-141">Select the file-system operation to perform.</span></span> <span data-ttu-id="e3d0a-142">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-142">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="e3d0a-143">值</span><span class="sxs-lookup"><span data-stu-id="e3d0a-143">Value</span></span>|<span data-ttu-id="e3d0a-144">说明</span><span class="sxs-lookup"><span data-stu-id="e3d0a-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e3d0a-145">**复制目录**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-145">**Copy directory**</span></span>|<span data-ttu-id="e3d0a-146">复制目录。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-146">Copy a directory.</span></span> <span data-ttu-id="e3d0a-147">选择此值将显示源和目标的动态选项。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-147">Selecting this value displays the dynamic options for a source and destination.</span></span>|  
|<span data-ttu-id="e3d0a-148">**复制文件**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-148">**Copy file**</span></span>|<span data-ttu-id="e3d0a-149">复制文件。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-149">Copy a file.</span></span> <span data-ttu-id="e3d0a-150">选择此值将显示源和目标的动态选项。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-150">Selecting this value displays the dynamic options for a source and destination.</span></span>|  
|<span data-ttu-id="e3d0a-151">**创建目录**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-151">**Create directory**</span></span>|<span data-ttu-id="e3d0a-152">创建目录。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-152">Create a directory.</span></span> <span data-ttu-id="e3d0a-153">选择此值将显示源和目标目录的动态选项。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-153">Selecting this value displays the dynamic options for a source and a destination directory.</span></span>|  
|<span data-ttu-id="e3d0a-154">**删除目录**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-154">**Delete directory**</span></span>|<span data-ttu-id="e3d0a-155">删除目录。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-155">Delete a directory.</span></span> <span data-ttu-id="e3d0a-156">选择此值将显示源的动态选项。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-156">Selecting this value displays the dynamic options for a source.</span></span>|  
|<span data-ttu-id="e3d0a-157">**删除目录内容**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-157">**Delete directory content**</span></span>|<span data-ttu-id="e3d0a-158">删除目录的内容。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-158">Delete the content of a directory.</span></span> <span data-ttu-id="e3d0a-159">选择此值将显示源的动态选项。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-159">Selecting this value displays the dynamic options for a source.</span></span>|  
|<span data-ttu-id="e3d0a-160">**删除文件**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-160">**Delete file**</span></span>|<span data-ttu-id="e3d0a-161">删除文件。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-161">Delete a file.</span></span> <span data-ttu-id="e3d0a-162">选择此值将显示源的动态选项。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-162">Selecting this value displays the dynamic options for a source.</span></span>|  
|<span data-ttu-id="e3d0a-163">**移动目录**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-163">**Move directory**</span></span>|<span data-ttu-id="e3d0a-164">移动目录。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-164">Move a directory.</span></span> <span data-ttu-id="e3d0a-165">选择此值将显示源和目标的动态选项。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-165">Selecting this value displays the dynamic options for a source and destination.</span></span>|  
|<span data-ttu-id="e3d0a-166">**移动文件**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-166">**Move file**</span></span>|<span data-ttu-id="e3d0a-167">移动文件。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-167">Move a file.</span></span> <span data-ttu-id="e3d0a-168">选择此值将显示源和目标的动态选项。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-168">Selecting this value displays the dynamic options for a source and destination.</span></span><br /><br /> <span data-ttu-id="e3d0a-169">注意：移动文件时，在作为目标提供的目录路径中不要包含文件名。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-169">Note: When moving a file, do not include a file name in the directory path that you provide as the destination.</span></span>|  
|<span data-ttu-id="e3d0a-170">**重命名文件**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-170">**Rename file**</span></span>|<span data-ttu-id="e3d0a-171">重命名文件。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-171">Rename a file.</span></span> <span data-ttu-id="e3d0a-172">选择此值将显示源和目标的动态选项。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-172">Selecting this value displays the dynamic options for a source and destination.</span></span><br /><br /> <span data-ttu-id="e3d0a-173">注意：在重命名文件时，请在为目标提供的目录路径中包含新文件名。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-173">Note: When renaming a file, include the new file name in the directory path that you provide for the destination.</span></span>|  
|<span data-ttu-id="e3d0a-174">**设置属性**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-174">**Set attributes**</span></span>|<span data-ttu-id="e3d0a-175">设置文件或目录的属性。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-175">Set the attributes of a file or directory.</span></span> <span data-ttu-id="e3d0a-176">选择此值将显示源和操作的动态选项。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-176">Selecting this value displays the dynamic options for a source and operation.</span></span>|  
  
 `IsSourcePathVariable`  
 <span data-ttu-id="e3d0a-177">指示目标路径是否存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-177">Indicate whether the destination path is stored in a variable.</span></span> <span data-ttu-id="e3d0a-178">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-178">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="e3d0a-179">值</span><span class="sxs-lookup"><span data-stu-id="e3d0a-179">Value</span></span>||  
|-----------|-|  
|<span data-ttu-id="e3d0a-180">**True**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-180">**True**</span></span>|<span data-ttu-id="e3d0a-181">目标路径存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-181">The destination path is stored in a variable.</span></span> <span data-ttu-id="e3d0a-182">选择此值将显示动态选项 **SourceVariable**。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-182">Selecting this value displays the dynamic option, **SourceVariable**.</span></span>|  
|<span data-ttu-id="e3d0a-183">**False**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-183">**False**</span></span>|<span data-ttu-id="e3d0a-184">目标路径在文件连接管理器中指定。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-184">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="e3d0a-185">选择此值将显示动态选项 **DestinationVariable**。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-185">Selecting this value displays the dynamic option, **DestinationVariable**.</span></span>|  
  
## <a name="isdestinationpathvariable-dynamic-options"></a><span data-ttu-id="e3d0a-186">IsDestinationPathVariable 动态选项</span><span class="sxs-lookup"><span data-stu-id="e3d0a-186">IsDestinationPathVariable Dynamic Options</span></span>  
  
### <a name="isdestinationpathvariable--true"></a><span data-ttu-id="e3d0a-187">IsDestinationPathVariable = True</span><span class="sxs-lookup"><span data-stu-id="e3d0a-187">IsDestinationPathVariable = True</span></span>  
 <span data-ttu-id="e3d0a-188">**DestinationVariable**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-188">**DestinationVariable**</span></span>  
 <span data-ttu-id="e3d0a-189">从列表中选择变量名称，或单击“\<**New variable...**>”创建新变量。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-189">Select the variable name in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="e3d0a-190">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="e3d0a-190">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="isdestinationpathvariable--false"></a><span data-ttu-id="e3d0a-191">IsDestinationPathVariable = False</span><span class="sxs-lookup"><span data-stu-id="e3d0a-191">IsDestinationPathVariable = False</span></span>  
 `DestinationConnection`  
 <span data-ttu-id="e3d0a-192">从列表中选择文件连接管理器，或单击“\<**New connection...**>”创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-192">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="e3d0a-193">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="e3d0a-193">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
## <a name="issourcepathvariable-dynamic-options"></a><span data-ttu-id="e3d0a-194">IsSourcePathVariable 动态选项</span><span class="sxs-lookup"><span data-stu-id="e3d0a-194">IsSourcePathVariable Dynamic Options</span></span>  
  
### <a name="issourcepathvariable--true"></a><span data-ttu-id="e3d0a-195">IsSourcePathVariable = True</span><span class="sxs-lookup"><span data-stu-id="e3d0a-195">IsSourcePathVariable = True</span></span>  
 <span data-ttu-id="e3d0a-196">**SourceVariable**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-196">**SourceVariable**</span></span>  
 <span data-ttu-id="e3d0a-197">从列表中选择变量名称，或单击“\<**New variable...**>”创建新变量。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-197">Select the variable name in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="e3d0a-198">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="e3d0a-198">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="issourcepathvariable--false"></a><span data-ttu-id="e3d0a-199">IsSourcePathVariable = False</span><span class="sxs-lookup"><span data-stu-id="e3d0a-199">IsSourcePathVariable = False</span></span>  
 `SourceConnection`  
 <span data-ttu-id="e3d0a-200">从列表中选择文件连接管理器，或单击“\<**New connection...**>”创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-200">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="e3d0a-201">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="e3d0a-201">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
## <a name="operation-dynamic-options"></a><span data-ttu-id="e3d0a-202">Operation 动态选项</span><span class="sxs-lookup"><span data-stu-id="e3d0a-202">Operation Dynamic Options</span></span>  
  
### <a name="operation--set-attributes"></a><span data-ttu-id="e3d0a-203">Operation = 设置属性</span><span class="sxs-lookup"><span data-stu-id="e3d0a-203">Operation = Set Attributes</span></span>  
 <span data-ttu-id="e3d0a-204">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-204">**Hidden**</span></span>  
 <span data-ttu-id="e3d0a-205">指示文件或目录是否可见。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-205">Indicate whether the file or directory is visible.</span></span>  
  
 <span data-ttu-id="e3d0a-206">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-206">**ReadOnly**</span></span>  
 <span data-ttu-id="e3d0a-207">指示文件是否是只读的。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-207">Indicate whether the file is read-only.</span></span>  
  
 <span data-ttu-id="e3d0a-208">**存档**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-208">**Archive**</span></span>  
 <span data-ttu-id="e3d0a-209">指示文件或目录可以用于存档。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-209">Indicate whether the file or directory is ready for archiving.</span></span>  
  
 <span data-ttu-id="e3d0a-210">**系统**</span><span class="sxs-lookup"><span data-stu-id="e3d0a-210">**System**</span></span>  
 <span data-ttu-id="e3d0a-211">指示文件是否是操作系统文件。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-211">Indicate whether the file is an operating system file.</span></span>  
  
### <a name="operation--create-directory"></a><span data-ttu-id="e3d0a-212">Operation = 创建目录</span><span class="sxs-lookup"><span data-stu-id="e3d0a-212">Operation = Create directory</span></span>  
 `UseDirectoryIfExists`  
 <span data-ttu-id="e3d0a-213">指示“创建目录”操作是否使用具有指定名称的现有目录，而不创建新目录。</span><span class="sxs-lookup"><span data-stu-id="e3d0a-213">Indicates whether the **Create directory** operation uses an existing directory with the specified name instead of creating a new directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3d0a-214">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3d0a-214">See Also</span></span>  
 <span data-ttu-id="e3d0a-215">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e3d0a-215">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="e3d0a-216">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="e3d0a-216">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
