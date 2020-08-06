---
title: FTP 任务 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.f1
helpviewer_keywords:
- FTP task [Integration Services]
ms.assetid: 41c3f2c4-ee04-460a-9822-bb9ae4036c2e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 63ec58c1bff9894d0aa73112686c4b1fe9421b98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576934"
---
# <a name="ftp-task"></a><span data-ttu-id="456ea-102">FTP 任务</span><span class="sxs-lookup"><span data-stu-id="456ea-102">FTP Task</span></span>
  <span data-ttu-id="456ea-103">FTP 任务可以下载和上载数据文件，并管理服务器上的目录。</span><span class="sxs-lookup"><span data-stu-id="456ea-103">The FTP task downloads and uploads data files and manages directories on servers.</span></span> <span data-ttu-id="456ea-104">例如，在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包工作流中，包可以从远程服务器或 Internet 位置下载数据文件。</span><span class="sxs-lookup"><span data-stu-id="456ea-104">For example, a package can download data files from a remote server or an Internet location as part of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package workflow.</span></span> <span data-ttu-id="456ea-105">可以将 FTP 任务用于下列用途：</span><span class="sxs-lookup"><span data-stu-id="456ea-105">You can use the FTP task for the following purposes:</span></span>  
  
-   <span data-ttu-id="456ea-106">在移动数据之前或之后，将目录和数据文件从一个目录复制到另一个目录，并对数据应用转换。</span><span class="sxs-lookup"><span data-stu-id="456ea-106">Copying directories and data files from one directory to another, before or after moving data, and applying transformations to the data.</span></span>  
  
-   <span data-ttu-id="456ea-107">登录到源 FTP 位置并将文件或包复制到目标目录。</span><span class="sxs-lookup"><span data-stu-id="456ea-107">Logging in to a source FTP location and copying files or packages to a destination directory.</span></span>  
  
-   <span data-ttu-id="456ea-108">从 FTP 位置下载文件并在将数据加载到数据库之前对列数据应用转换。</span><span class="sxs-lookup"><span data-stu-id="456ea-108">Downloading files from an FTP location and applying transformations to column data before loading the data into a database.</span></span>  
  
 <span data-ttu-id="456ea-109">在运行时，FTP 任务通过使用 FTP 连接管理器连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="456ea-109">At run time, the FTP task connects to a server by using an FTP connection manager.</span></span> <span data-ttu-id="456ea-110">FTP 连接管理器与 FTP 任务分开配置，然后在 FTP 任务中引用连接管理器。</span><span class="sxs-lookup"><span data-stu-id="456ea-110">The FTP connection manager is configured separately from the FTP task, and then is referenced in the FTP task.</span></span> <span data-ttu-id="456ea-111">FTP 连接管理器包括服务器设置、用于访问 FTP 服务器的凭据，以及连接到服务器的超时值和重试次数之类的选项。</span><span class="sxs-lookup"><span data-stu-id="456ea-111">The FTP connection manager includes the server settings, the credentials for accessing the FTP server, and options such as the time-out and the number of retries for connecting to the server.</span></span> <span data-ttu-id="456ea-112">有关详细信息，请参阅 [FTP 连接管理器](../connection-manager/ftp-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="456ea-112">For more information, see [FTP Connection Manager](../connection-manager/ftp-connection-manager.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="456ea-113">FTP 连接管理器仅支持匿名身份验证和基本身份验证，</span><span class="sxs-lookup"><span data-stu-id="456ea-113">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="456ea-114">而不支持 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="456ea-114">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="456ea-115">访问本地文件或本地目录时，FTP 任务使用文件连接管理器或存储在变量中的路径信息。</span><span class="sxs-lookup"><span data-stu-id="456ea-115">When accessing a local file or a local directory, the FTP task uses a File connection manager or path information stored in a variable.</span></span> <span data-ttu-id="456ea-116">与此相反，访问远程文件或远程目录时，FTP 任务使用远程服务器上的直接指定路径（在 FTP 连接管理器中指定）或存储在变量中的路径信息。</span><span class="sxs-lookup"><span data-stu-id="456ea-116">In contrast, when accessing a remote file or a remote directory, the FTP task uses a directly specified path on the remote server, as specified in the FTP connection manager, or path information stored in a variable.</span></span> <span data-ttu-id="456ea-117">有关详细信息，请参阅[文件连接管理器](../connection-manager/file-connection-manager.md)和 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="456ea-117">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="456ea-118">这意味着 FTP 任务可以接收多个文件和删除多个远程文件；但如果使用连接管理器，则该任务只能发送一个文件和删除一个本地文件，因为文件连接管理器只能访问一个文件。</span><span class="sxs-lookup"><span data-stu-id="456ea-118">This means that the FTP task can receive multiple files and delete multiple remote files; but the task can send only one file and delete only one local file if it uses a connection manager, because a File connection manager can access only one file.</span></span> <span data-ttu-id="456ea-119">若要访问多个本地文件，FTP 任务必须使用变量来提供路径信息。</span><span class="sxs-lookup"><span data-stu-id="456ea-119">To access multiple local files, the FTP task must use a variable to provide the path information.</span></span> <span data-ttu-id="456ea-120">例如，包含“C:\Test\\*.txt”的变量所提供的路径可以支持删除或发送 Test 目录中所有以 .txt 为扩展名的文件。</span><span class="sxs-lookup"><span data-stu-id="456ea-120">For example, a variable that contains "C:\Test\\*.txt" provides a path that supports deleting or sending all the files that have a .txt extension in the Test directory.</span></span>  
  
 <span data-ttu-id="456ea-121">若要发送多个文件和访问多个本地文件及目录，还可以通过在 Foreach 循环中包含 FTP 任务来多次执行 FTP 任务。</span><span class="sxs-lookup"><span data-stu-id="456ea-121">To send multiple files and access multiple local files and directories, you can also execute the FTP task multiple times by including the task in a Foreach Loop.</span></span> <span data-ttu-id="456ea-122">Foreach 循环可以使用 For Each 文件枚举器对目录中的文件进行枚举。</span><span class="sxs-lookup"><span data-stu-id="456ea-122">The Foreach Loop can enumerate across files in a directory using the For Each File enumerator.</span></span> <span data-ttu-id="456ea-123">有关详细信息，请参阅 [Foreach 循环容器](foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="456ea-123">For more information, see [Foreach Loop Container](foreach-loop-container.md).</span></span>  
  
 <span data-ttu-id="456ea-124">FTP 任务支持在路径中使用通配符 *?*</span><span class="sxs-lookup"><span data-stu-id="456ea-124">The FTP task supports the *?*</span></span> <span data-ttu-id="456ea-125">和 *\** 。</span><span class="sxs-lookup"><span data-stu-id="456ea-125">and *\** wildcard characters in paths.</span></span> <span data-ttu-id="456ea-126">这使得任务可以访问多个文件。</span><span class="sxs-lookup"><span data-stu-id="456ea-126">This lets the task access multiple files.</span></span> <span data-ttu-id="456ea-127">但是，只能在路径中指定文件名的部分使用通配符。</span><span class="sxs-lookup"><span data-stu-id="456ea-127">However, you can use wildcard characters only in the part of the path that specifies the file name.</span></span> <span data-ttu-id="456ea-128">例如，C:\MyDirectory\\*.txt 是有效路径，而 C:\\\*\MyText.txt 则不是。</span><span class="sxs-lookup"><span data-stu-id="456ea-128">For example, C:\MyDirectory\\*.txt is a valid path, but C:\\\*\MyText.txt is not.</span></span>  
  
 <span data-ttu-id="456ea-129">FTP 操作可以配置为在操作失败时停止文件系统任务，或以 ASCII 模式传输文件。</span><span class="sxs-lookup"><span data-stu-id="456ea-129">The FTP operations can be configured to stop the File System task when the operation fails, or to transfer files in ASCII mode.</span></span> <span data-ttu-id="456ea-130">发送和接收文件副本的操作可以配置为覆盖目标文件和目录。</span><span class="sxs-lookup"><span data-stu-id="456ea-130">The operations that send and receive files copy can be configured to overwrite destination files and directories.</span></span>  
  
## <a name="predefined-ftp-operations"></a><span data-ttu-id="456ea-131">预定义的 FTP 操作</span><span class="sxs-lookup"><span data-stu-id="456ea-131">Predefined FTP Operations</span></span>  
 <span data-ttu-id="456ea-132">FTP 任务包含一组预定义的操作。</span><span class="sxs-lookup"><span data-stu-id="456ea-132">The FTP task includes a predefined set of operations.</span></span> <span data-ttu-id="456ea-133">下表介绍了这些运算。</span><span class="sxs-lookup"><span data-stu-id="456ea-133">The following table describes these operations.</span></span>  
  
|<span data-ttu-id="456ea-134">Operation</span><span class="sxs-lookup"><span data-stu-id="456ea-134">Operation</span></span>|<span data-ttu-id="456ea-135">说明</span><span class="sxs-lookup"><span data-stu-id="456ea-135">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="456ea-136">发送文件</span><span class="sxs-lookup"><span data-stu-id="456ea-136">Send files</span></span>|<span data-ttu-id="456ea-137">将文件从本地计算机发送到 FTP 服务器。</span><span class="sxs-lookup"><span data-stu-id="456ea-137">Sends a file from the local computer to the FTP server.</span></span>|  
|<span data-ttu-id="456ea-138">接收文件</span><span class="sxs-lookup"><span data-stu-id="456ea-138">Receive files</span></span>|<span data-ttu-id="456ea-139">将文件从 FTP 服务器保存到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="456ea-139">Saves a file from the FTP server to the local computer.</span></span>|  
|<span data-ttu-id="456ea-140">创建本地目录</span><span class="sxs-lookup"><span data-stu-id="456ea-140">Create local directory</span></span>|<span data-ttu-id="456ea-141">在本地计算机上创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="456ea-141">Creates a folder on the local computer.</span></span>|  
|<span data-ttu-id="456ea-142">创建远程目录</span><span class="sxs-lookup"><span data-stu-id="456ea-142">Create remote directory</span></span>|<span data-ttu-id="456ea-143">在 FTP 服务器上创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="456ea-143">Creates a folder on the FTP server.</span></span>|  
|<span data-ttu-id="456ea-144">删除本地目录</span><span class="sxs-lookup"><span data-stu-id="456ea-144">Remove local directory</span></span>|<span data-ttu-id="456ea-145">删除本地计算机上的文件夹。</span><span class="sxs-lookup"><span data-stu-id="456ea-145">Deletes a folder on the local computer.</span></span>|  
|<span data-ttu-id="456ea-146">删除远程目录</span><span class="sxs-lookup"><span data-stu-id="456ea-146">Remove remote directory</span></span>|<span data-ttu-id="456ea-147">删除 FTP 服务器上的文件夹。</span><span class="sxs-lookup"><span data-stu-id="456ea-147">Deletes a folder on the FTP server.</span></span>|  
|<span data-ttu-id="456ea-148">删除本地文件</span><span class="sxs-lookup"><span data-stu-id="456ea-148">Delete local files</span></span>|<span data-ttu-id="456ea-149">删除本地计算机上的文件。</span><span class="sxs-lookup"><span data-stu-id="456ea-149">Deletes a file on the local computer.</span></span>|  
|<span data-ttu-id="456ea-150">删除远程文件</span><span class="sxs-lookup"><span data-stu-id="456ea-150">Delete remote files</span></span>|<span data-ttu-id="456ea-151">删除 FTP 服务器上的文件。</span><span class="sxs-lookup"><span data-stu-id="456ea-151">Deletes a file on the FTP server.</span></span>|  
  
## <a name="custom-log-entries-available-on-the-ftp-task"></a><span data-ttu-id="456ea-152">FTP 任务可用的自定义日志项</span><span class="sxs-lookup"><span data-stu-id="456ea-152">Custom Log Entries Available on the FTP Task</span></span>  
 <span data-ttu-id="456ea-153">下表列出了 FTP 任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="456ea-153">The following table lists the custom log entries for the FTP task.</span></span> <span data-ttu-id="456ea-154">有关详细信息，请参阅 [Integration Services (SSIS) 日志记录](../performance/integration-services-ssis-logging.md)和[日志记录的自定义消息](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="456ea-154">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="456ea-155">日志项</span><span class="sxs-lookup"><span data-stu-id="456ea-155">Log entry</span></span>|<span data-ttu-id="456ea-156">说明</span><span class="sxs-lookup"><span data-stu-id="456ea-156">Description</span></span>|  
|---------------|-----------------|  
|`FTPConnectingToServer`|<span data-ttu-id="456ea-157">指示任务已启动与 FTP 服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="456ea-157">Indicates that the task initiated a connection to the FTP server.</span></span>|  
|`FTPOperation`|<span data-ttu-id="456ea-158">报告任务所执行的 FTP 操作的开始及其类型。</span><span class="sxs-lookup"><span data-stu-id="456ea-158">Reports the beginning of and the type of FTP operation that the task performs.</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="456ea-159">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="456ea-159">Related Tasks</span></span>  
 <span data-ttu-id="456ea-160">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="456ea-160">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="456ea-161">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的信息，请参阅 [设置任务或容器的属性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="456ea-161">For information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
 <span data-ttu-id="456ea-162">有关如何以编程方式设置这些属性的详细信息，请参阅 <xref:Microsoft.SqlServer.Dts.Tasks.FtpTask.FtpTask>。</span><span class="sxs-lookup"><span data-stu-id="456ea-162">For more information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Tasks.FtpTask.FtpTask>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="456ea-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="456ea-163">See Also</span></span>  
 <span data-ttu-id="456ea-164">[FTP 任务编辑器 &#40;常规 "页面&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="456ea-164">[FTP Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="456ea-165">[FTP 任务编辑器 &#40;文件传输页面&#41;](../ftp-task-editor-file-transfer-page.md) </span><span class="sxs-lookup"><span data-stu-id="456ea-165">[FTP Task Editor &#40;File Transfer Page&#41;](../ftp-task-editor-file-transfer-page.md) </span></span>  
 <span data-ttu-id="456ea-166">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="456ea-166">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="456ea-167">控制流</span><span class="sxs-lookup"><span data-stu-id="456ea-167">Control Flow</span></span>](control-flow.md)  
  
  
