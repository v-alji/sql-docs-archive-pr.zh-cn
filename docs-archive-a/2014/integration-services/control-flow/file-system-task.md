---
title: 文件系统任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.filesystemtask.f1
helpviewer_keywords:
- File System task [Integration Services]
ms.assetid: 7dd79a6a-e066-4028-a385-1d40f31056f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3ce3d31ceb720704fb61c33043a4c7319607caff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576941"
---
# <a name="file-system-task"></a><span data-ttu-id="bf3d8-102">文件系统任务</span><span class="sxs-lookup"><span data-stu-id="bf3d8-102">File System Task</span></span>
  <span data-ttu-id="bf3d8-103">文件系统任务对文件系统中的文件和目录执行操作。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-103">The File System task performs operations on files and directories in the file system.</span></span> <span data-ttu-id="bf3d8-104">例如，通过使用文件系统任务，包可以创建、移动或删除目录和文件。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-104">For example, by using the File System task, a package can create, move, or delete directories and files.</span></span> <span data-ttu-id="bf3d8-105">您还可以使用文件系统任务设置文件和目录的属性。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-105">You can also use the File System task to set attributes on files and directories.</span></span> <span data-ttu-id="bf3d8-106">例如，文件系统任务可以让文件隐藏或只读。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-106">For example, the File System task can make files hidden or read-only.</span></span>  
  
 <span data-ttu-id="bf3d8-107">所有文件系统任务操作都使用源，源可以是文件或目录。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-107">All File System task operations use a source, which can be a file or a directory.</span></span> <span data-ttu-id="bf3d8-108">例如，任务复制的文件或删除的目录都是源。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-108">For example, the file that the task copies or the directory it deletes is a source.</span></span> <span data-ttu-id="bf3d8-109">源可以通过使用指向目录或文件的文件连接管理器来指定，也可以通过提供包含源路径的变量的名称来指定。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-109">The source can be specified by using a File connection manager that points to the directory or file or by providing the name of a variable that contains the source path.</span></span> <span data-ttu-id="bf3d8-110">有关详细信息，请参阅[文件连接管理器](../connection-manager/file-connection-manager.md)和 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-110">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="bf3d8-111">复制和移动文件及目录的操作与重命名文件的操作都使用目标和源。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-111">The operations that copy and move file and directories and rename files use a destination and a source.</span></span> <span data-ttu-id="bf3d8-112">目标可以使用文件连接管理器或变量指定。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-112">The destination is specified by using a File connection manager or a variable.</span></span> <span data-ttu-id="bf3d8-113">文件系统任务操作可以配置为允许覆盖目标文件和目录。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-113">File system task operations can be configured to permit overwriting of destination files and directories.</span></span> <span data-ttu-id="bf3d8-114">创建新目录的操作可以配置为使用具有指定名称的现有目录，而不是在目录已经存在时失败。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-114">The operation that creates a new directory can be configured to use an existing directory that has the specified name instead of failing when the directory already exists.</span></span>  
  
## <a name="predefined-file-system-operations"></a><span data-ttu-id="bf3d8-115">预定义的文件系统操作</span><span class="sxs-lookup"><span data-stu-id="bf3d8-115">Predefined File System Operations</span></span>  
 <span data-ttu-id="bf3d8-116">文件系统任务包含一组预定义的操作。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-116">The File System task includes a predefined set of operations.</span></span> <span data-ttu-id="bf3d8-117">下表介绍了这些运算。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-117">The following table describes these operations.</span></span>  
  
|<span data-ttu-id="bf3d8-118">Operation</span><span class="sxs-lookup"><span data-stu-id="bf3d8-118">Operation</span></span>|<span data-ttu-id="bf3d8-119">说明</span><span class="sxs-lookup"><span data-stu-id="bf3d8-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf3d8-120">复制目录</span><span class="sxs-lookup"><span data-stu-id="bf3d8-120">Copy directory</span></span>|<span data-ttu-id="bf3d8-121">将文件夹从一个位置复制到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-121">Copies a folder from one location to another.</span></span>|  
|<span data-ttu-id="bf3d8-122">复制文件</span><span class="sxs-lookup"><span data-stu-id="bf3d8-122">Copy file</span></span>|<span data-ttu-id="bf3d8-123">将文件从一个位置复制到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-123">Copies a file from one location to another.</span></span>|  
|<span data-ttu-id="bf3d8-124">创建目录</span><span class="sxs-lookup"><span data-stu-id="bf3d8-124">Create directory</span></span>|<span data-ttu-id="bf3d8-125">在指定位置创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-125">Creates a folder in a specified location.</span></span>|  
|<span data-ttu-id="bf3d8-126">删除目录</span><span class="sxs-lookup"><span data-stu-id="bf3d8-126">Delete directory</span></span>|<span data-ttu-id="bf3d8-127">删除指定位置的文件夹。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-127">Deletes a folder in a specified location.</span></span>|  
|<span data-ttu-id="bf3d8-128">删除目录内容</span><span class="sxs-lookup"><span data-stu-id="bf3d8-128">Delete directory content</span></span>|<span data-ttu-id="bf3d8-129">删除文件夹中的所有文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-129">Deletes all files and folders in a folder.</span></span>|  
|<span data-ttu-id="bf3d8-130">删除文件</span><span class="sxs-lookup"><span data-stu-id="bf3d8-130">Delete file</span></span>|<span data-ttu-id="bf3d8-131">删除指定位置的文件。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-131">Deletes a file in a specified location.</span></span>|  
|<span data-ttu-id="bf3d8-132">移动目录</span><span class="sxs-lookup"><span data-stu-id="bf3d8-132">Move directory</span></span>|<span data-ttu-id="bf3d8-133">将文件夹从一个位置移动到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-133">Moves a folder from one location to another.</span></span>|  
|<span data-ttu-id="bf3d8-134">移动文件</span><span class="sxs-lookup"><span data-stu-id="bf3d8-134">Move file</span></span>|<span data-ttu-id="bf3d8-135">将文件从一个位置移动到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-135">Moves a file from one location to another.</span></span>|  
|<span data-ttu-id="bf3d8-136">重命名文件</span><span class="sxs-lookup"><span data-stu-id="bf3d8-136">Rename file</span></span>|<span data-ttu-id="bf3d8-137">重命名指定位置的文件。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-137">Renames a file in a specified location.</span></span>|  
|<span data-ttu-id="bf3d8-138">设置属性</span><span class="sxs-lookup"><span data-stu-id="bf3d8-138">Set attributes</span></span>|<span data-ttu-id="bf3d8-139">设置文件和文件夹的属性。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-139">Sets attributes on files and folders.</span></span> <span data-ttu-id="bf3d8-140">属性包括“存档”、“隐藏”、“正常”、“只读”和“系统”。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-140">Attributes include Archive, Hidden, Normal, ReadOnly, and System.</span></span> <span data-ttu-id="bf3d8-141">“正常”指没有属性，它不能与其他属性结合使用。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-141">Normal is the lack of attributes, and it cannot be combined with other attributes.</span></span> <span data-ttu-id="bf3d8-142">所有其他属性都可以组合使用。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-142">All other attributes can be used in combination.</span></span>|  
  
 <span data-ttu-id="bf3d8-143">文件系统任务对单个文件或目录进行操作。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-143">The File System task operates on a single file or directory.</span></span> <span data-ttu-id="bf3d8-144">因此，该任务不支持使用通配符对多个文件执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-144">Therefore, this task does not support the use of wildcard characters to perform the same operation on multiple files.</span></span> <span data-ttu-id="bf3d8-145">若要使此文件系统任务对多个文件或目录重复执行某个操作，请将此文件系统任务放置于一个 Foreach 循环容器中，如下面的步骤所述：</span><span class="sxs-lookup"><span data-stu-id="bf3d8-145">To have the File System task repeat an operation on multiple files or directories, put the File System task in a Foreach Loop container, as described in the following steps:</span></span>  
  
-   <span data-ttu-id="bf3d8-146">**配置 Foreach 循环容器** 在 Foreach 循环编辑器的 **“集合”** 页上，将枚举器设置为 **“Foreach 文件枚举器”** ，然后输入通配符表达式作为 **“文件”** 的枚举器配置。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-146">**Configure the Foreach Loop container** On the **Collection** page of the Foreach Loop Editor, set the enumerator to **Foreach File Enumerator** and enter the wildcard expression as the enumerator configuration for **Files**.</span></span> <span data-ttu-id="bf3d8-147">在 Foreach 循环编辑器的 **“变量映射”** 页上，将要用来传递文件名称的变量按照一次一个的方式映射至文件系统任务。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-147">On the **Variable Mappings** page of the Foreach Loop Editor, map a variable that you want to use to pass the file names one at a time to the File System task.</span></span>  
  
-   <span data-ttu-id="bf3d8-148">**添加和配置文件系统任务** 将文件系统任务添加到 Foreach 循环容器。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-148">**Add and configure a File System task** Add a File System task to the Foreach Loop container.</span></span> <span data-ttu-id="bf3d8-149">在文件系统任务编辑器的 **“常规”** 页上，将 **“SourceVariable”** 或 **“DestinationVariable”** 属性设置为您在 Foreach 循环容器中定义的变量。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-149">On the **General** page of the File System Task Editor, set the **SourceVariable** or **DestinationVariable** property to the variable that you defined in the Foreach Loop container.</span></span>  
  
## <a name="custom-log-entries-available-on-the-file-system-task"></a><span data-ttu-id="bf3d8-150">文件系统任务可用的自定义日志项</span><span class="sxs-lookup"><span data-stu-id="bf3d8-150">Custom Log Entries Available on the File System Task</span></span>  
 <span data-ttu-id="bf3d8-151">下表介绍了文件系统任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-151">The following table describes the custom log entry for the File System task.</span></span> <span data-ttu-id="bf3d8-152">有关详细信息，请参阅 [Integration Services (SSIS) 日志记录](../performance/integration-services-ssis-logging.md)和[日志记录的自定义消息](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-152">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="bf3d8-153">日志项</span><span class="sxs-lookup"><span data-stu-id="bf3d8-153">Log entry</span></span>|<span data-ttu-id="bf3d8-154">说明</span><span class="sxs-lookup"><span data-stu-id="bf3d8-154">Description</span></span>|  
|---------------|-----------------|  
|`FileSystemOperation`|<span data-ttu-id="bf3d8-155">报告任务所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-155">Reports the operation that the task performs.</span></span> <span data-ttu-id="bf3d8-156">在文件系统操作开始时写入日志项，日志项包括有关源和目标的信息。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-156">The log entry is written when the file system operation starts and includes information about the source and destination.</span></span>|  
  
## <a name="configuring-the-file-system-task"></a><span data-ttu-id="bf3d8-157">配置文件系统任务</span><span class="sxs-lookup"><span data-stu-id="bf3d8-157">Configuring the File System Task</span></span>  
 <span data-ttu-id="bf3d8-158">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-158">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="bf3d8-159">有关可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="bf3d8-159">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topics:</span></span>  
  
-   [<span data-ttu-id="bf3d8-160">文件系统任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="bf3d8-160">File System Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="bf3d8-161">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="bf3d8-161">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="bf3d8-162">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="bf3d8-162">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topic:</span></span>  
  
-   [<span data-ttu-id="bf3d8-163">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="bf3d8-163">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
 <span data-ttu-id="bf3d8-164">有关如何以编程方式设置这些属性的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="bf3d8-164">For more information about how to set these properties programmatically, see the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="bf3d8-165">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="bf3d8-165">Related Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="bf3d8-166">包括一个可下载和上载数据文件以及管理服务器上目录的任务。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-166">includes a task that downloads and uploads data files and manages directories on servers.</span></span> <span data-ttu-id="bf3d8-167">有关详细信息，请参阅 [FTP Task](ftp-task.md)。</span><span class="sxs-lookup"><span data-stu-id="bf3d8-167">For more information, see [FTP Task](ftp-task.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf3d8-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf3d8-168">See Also</span></span>  
 <span data-ttu-id="bf3d8-169">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="bf3d8-169">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="bf3d8-170">控制流</span><span class="sxs-lookup"><span data-stu-id="bf3d8-170">Control Flow</span></span>](control-flow.md)  
  
  
