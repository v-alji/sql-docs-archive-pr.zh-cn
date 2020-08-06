---
title: 脚本任务示例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], examples
- examples [Integration Services]
- SSIS Script task, examples
ms.assetid: b0dd77ee-ee11-4cd9-87aa-61dd67f2fe1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 920d2ee5cc2e64db1048d10522d9be644794e55b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689941"
---
# <a name="script-task-examples"></a><span data-ttu-id="7d346-102">脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="7d346-102">Script Task Examples</span></span>
  <span data-ttu-id="7d346-103">脚本任务是一个多用途工具，您可以在包中使用该工具以满足 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 附带的任务无法满足的几乎所有要求。</span><span class="sxs-lookup"><span data-stu-id="7d346-103">The Script task is a multi-purpose tool that you can use in a package to fill almost any requirement that is not met by the tasks included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="7d346-104">本主题列出了用于演示一些可用功能的脚本任务代码示例。</span><span class="sxs-lookup"><span data-stu-id="7d346-104">This topic lists Script task code samples that demonstrate some of the available functionality.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d346-105">如果希望创建可更方便地重用于多个包的任务，请考虑以这些脚本任务示例中的代码为基础，创建自定义任务。</span><span class="sxs-lookup"><span data-stu-id="7d346-105">If you want to create tasks that you can more easily reuse across multiple packages, consider using the code in these Script task samples as the starting point for custom tasks.</span></span> <span data-ttu-id="7d346-106">有关详细信息，请参阅 [开发自定义任务](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="7d346-106">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d346-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="7d346-107">In This Section</span></span>  
  
### <a name="example-topics"></a><span data-ttu-id="7d346-108">示例主题</span><span class="sxs-lookup"><span data-stu-id="7d346-108">Example Topics</span></span>  
 <span data-ttu-id="7d346-109">本节包含一些代码示例，这些示例演示了 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 类的各种用法，您可以将这些类并入 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 脚本任务中。</span><span class="sxs-lookup"><span data-stu-id="7d346-109">This section contains code examples that demonstrate various uses of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes that you can incorporate into an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Script task:</span></span>  
  
 [<span data-ttu-id="7d346-110">使用脚本任务检测空平面文件</span><span class="sxs-lookup"><span data-stu-id="7d346-110">Detecting an Empty Flat File with the Script Task</span></span>](../extending-packages-scripting-task-examples/detecting-an-empty-flat-file-with-the-script-task.md)  
 <span data-ttu-id="7d346-111">检查平面文件以确定该文件是否包含数据行，并将结果保存到变量以用于控制流分支。</span><span class="sxs-lookup"><span data-stu-id="7d346-111">Checks a flat file to determine whether it contains rows of data, and saves the result to a variable for use in control flow branching.</span></span>  
  
 [<span data-ttu-id="7d346-112">使用脚本任务为 ForEach 循环收集列表</span><span class="sxs-lookup"><span data-stu-id="7d346-112">Gathering a List for the ForEach Loop with the Script Task</span></span>](../extending-packages-scripting-task-examples/gathering-a-list-for-the-foreach-loop-with-the-script-task.md)  
 <span data-ttu-id="7d346-113">收集满足用户指定条件的文件的列表，并填充变量以供 Foreach 源变量枚举器将来使用。</span><span class="sxs-lookup"><span data-stu-id="7d346-113">Gathers a list of files that meet user-specified criteria, and populates a variable for later use by the Foreach from Variable Enumerator.</span></span>  
  
 [<span data-ttu-id="7d346-114">使用脚本任务查询 Active Directory</span><span class="sxs-lookup"><span data-stu-id="7d346-114">Querying the Active Directory with the Script Task</span></span>](../extending-packages-scripting-task-examples/querying-the-active-directory-with-the-script-task.md)  
 <span data-ttu-id="7d346-115">使用 System.DirectoryServices 命名空间中的类，基于 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 变量的值从 Active Directory 检索用户信息。</span><span class="sxs-lookup"><span data-stu-id="7d346-115">Retrieves user information from Active Directory based on the value of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable, by using classes in the System.DirectoryServices namespace.</span></span>  
  
 [<span data-ttu-id="7d346-116">使用脚本任务监视性能计数器</span><span class="sxs-lookup"><span data-stu-id="7d346-116">Monitoring Performance Counters with the Script Task</span></span>](../extending-packages-scripting-task-examples/monitoring-performance-counters-with-the-script-task.md)  
 <span data-ttu-id="7d346-117">使用 System.Diagnostics 命名空间中的类，创建可用于跟踪 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的执行进度的自定义性能计数器。</span><span class="sxs-lookup"><span data-stu-id="7d346-117">Creates a custom performance counter that can be used to track the execution progress of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package, by using classes in the System.Diagnostics namespace.</span></span>  
  
 [<span data-ttu-id="7d346-118">使用脚本任务处理图像</span><span class="sxs-lookup"><span data-stu-id="7d346-118">Working with Images with the Script Task</span></span>](../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)  
 <span data-ttu-id="7d346-119">使用 System.Drawing 命名空间中的类，将图像压缩为 JPEG 格式，并根据这些图像创建缩略图。</span><span class="sxs-lookup"><span data-stu-id="7d346-119">Compresses images into the JPEG format and creates thumbnail images from them, by using classes in the System.Drawing namespace.</span></span>  
  
 [<span data-ttu-id="7d346-120">使用脚本任务查找已安装的打印机</span><span class="sxs-lookup"><span data-stu-id="7d346-120">Finding Installed Printers with the Script Task</span></span>](../extending-packages-scripting-task-examples/finding-installed-printers-with-the-script-task.md)  
 <span data-ttu-id="7d346-121">使用 Drawing.Printing 命名空间中的类，查找支持特定纸张大小的已安装打印机。</span><span class="sxs-lookup"><span data-stu-id="7d346-121">Locates installed printers that support a specific paper size, by using classes in the System.Drawing.Printing namespace.</span></span>  
  
 [<span data-ttu-id="7d346-122">使用脚本任务发送 HTML 邮件消息</span><span class="sxs-lookup"><span data-stu-id="7d346-122">Sending an HTML Mail Message with the Script Task</span></span>](../extending-packages-scripting-task-examples/sending-an-html-mail-message-with-the-script-task.md)  
 <span data-ttu-id="7d346-123">以 HTML 格式而不是纯文本格式发送邮件消息。</span><span class="sxs-lookup"><span data-stu-id="7d346-123">Sends a mail message in HTML format instead of plain text format.</span></span>  
  
 [<span data-ttu-id="7d346-124">使用脚本任务处理 Excel 文件</span><span class="sxs-lookup"><span data-stu-id="7d346-124">Working with Excel Files with the Script Task</span></span>](../extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
 <span data-ttu-id="7d346-125">列出了 Excel 文件中的工作表，并检查特定工作表是否存在。</span><span class="sxs-lookup"><span data-stu-id="7d346-125">Lists the worksheets in an Excel file and checks for the existence of a specific worksheet.</span></span>  
  
 [<span data-ttu-id="7d346-126">使用脚本任务向远程私有消息队列发送消息</span><span class="sxs-lookup"><span data-stu-id="7d346-126">Sending to a Remote Private Message Queue with the Script Task</span></span>](../extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md)  
 <span data-ttu-id="7d346-127">向远程私有消息队列发送消息。</span><span class="sxs-lookup"><span data-stu-id="7d346-127">Sends a message to a remote private message queue.</span></span>  
  
### <a name="other-examples"></a><span data-ttu-id="7d346-128">其他示例</span><span class="sxs-lookup"><span data-stu-id="7d346-128">Other Examples</span></span>  
 <span data-ttu-id="7d346-129">下面的主题还包含用于脚本任务的代码示例：</span><span class="sxs-lookup"><span data-stu-id="7d346-129">The following topics also contain code examples for use with the Script task:</span></span>  
  
 [<span data-ttu-id="7d346-130">在脚本任务中使用变量</span><span class="sxs-lookup"><span data-stu-id="7d346-130">Using Variables in the Script Task</span></span>](../extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 <span data-ttu-id="7d346-131">要求用户基于可能超出在另一个变量中指定的限制的包变量值，确认包是否应该继续运行。</span><span class="sxs-lookup"><span data-stu-id="7d346-131">Asks the user for confirmation of whether the package should continue to run, based on the value of a package variable that may exceed the limit specified in another variable.</span></span>  
  
 [<span data-ttu-id="7d346-132">在脚本任务中连接数据源</span><span class="sxs-lookup"><span data-stu-id="7d346-132">Connecting to Data Sources in the Script Task</span></span>](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 <span data-ttu-id="7d346-133">从在包中定义的连接管理器中检索连接或连接信息。</span><span class="sxs-lookup"><span data-stu-id="7d346-133">Retrieves a connection or connection information from connection managers defined in the package.</span></span>  
  
 [<span data-ttu-id="7d346-134">在脚本任务中引发事件</span><span class="sxs-lookup"><span data-stu-id="7d346-134">Raising Events in the Script Task</span></span>](../extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 <span data-ttu-id="7d346-135">基于服务器上的 Internet 连接状态引发错误、警告或信息性消息。</span><span class="sxs-lookup"><span data-stu-id="7d346-135">Raises an error, a warning, or an informational message based on the status of the Internet connection on the server.</span></span>  
  
 [<span data-ttu-id="7d346-136">脚本任务中的日志记录</span><span class="sxs-lookup"><span data-stu-id="7d346-136">Logging in the Script Task</span></span>](../extending-packages-scripting/task/logging-in-the-script-task.md)  
 <span data-ttu-id="7d346-137">向已启用的日志提供程序记录由任务处理的项数。</span><span class="sxs-lookup"><span data-stu-id="7d346-137">Logs the number of items processed by the task to enabled log providers.</span></span>  
  
<span data-ttu-id="7d346-138">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="7d346-138">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="7d346-139">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="7d346-139">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="7d346-140">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="7d346-140">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="7d346-141">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="7d346-141">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
