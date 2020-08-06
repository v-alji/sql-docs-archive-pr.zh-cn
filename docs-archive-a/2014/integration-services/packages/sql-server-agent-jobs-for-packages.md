---
title: 包的 SQL Server 代理作业 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- jobs [Integration Services]
- automatic package execution
- scheduling packages [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: ecf7a5f9-b8a7-47f1-9ac0-bac07cb89e31
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eb9c1cf39ab5120958c33dfeff24588d59f71307
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586783"
---
# <a name="sql-server-agent-jobs-for-packages"></a><span data-ttu-id="ce1fc-102">包的 SQL Server 代理作业</span><span class="sxs-lookup"><span data-stu-id="ce1fc-102">SQL Server Agent Jobs for Packages</span></span>
  <span data-ttu-id="ce1fc-103">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理可以自动化和计划 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的执行。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-103">You can automate and schedule the execution of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="ce1fc-104">您可以计划部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器的包，以及存储在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包存储区和文件系统中的包。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-104">You can schedule packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, and are stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
## <a name="sections-in-this-topic"></a><span data-ttu-id="ce1fc-105">本主题的内容</span><span class="sxs-lookup"><span data-stu-id="ce1fc-105">Sections in This Topic</span></span>  
 <span data-ttu-id="ce1fc-106">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="ce1fc-106">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="ce1fc-107">在 SQL Server 代理中计划作业</span><span class="sxs-lookup"><span data-stu-id="ce1fc-107">Scheduling jobs in SQL Server Agent</span></span>](#jobs)  
  
-   [<span data-ttu-id="ce1fc-108">计划 Integration Services 包</span><span class="sxs-lookup"><span data-stu-id="ce1fc-108">Scheduling Integration Services packages</span></span>](#packages)  
  
-   [<span data-ttu-id="ce1fc-109">对计划的包进行故障排除</span><span class="sxs-lookup"><span data-stu-id="ce1fc-109">Troubleshooting scheduled packages</span></span>](#trouble)  
  
##  <a name="scheduling-jobs-in-sql-server-agent"></a><a name="jobs"></a> <span data-ttu-id="ce1fc-110">Scheduling Jobs in SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="ce1fc-110">Scheduling Jobs in SQL Server Agent</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ce1fc-111">代理是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装的服务，使您能够通过运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业自动执行任务和计划任务的执行。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-111">Agent is the service installed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that lets you automate and schedule tasks by running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> <span data-ttu-id="ce1fc-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务必须处于运行状态，作业才能自动运行。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service must be running before jobs can run automatically.</span></span> <span data-ttu-id="ce1fc-113">有关详细信息，请参阅 [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-113">For more information, see [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md).</span></span>  
  
 <span data-ttu-id="ce1fc-114">在您连接到 **的实例时，** “SQL Server 代理” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 节点将出现在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的对象资源管理器中。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-114">The **SQL Server Agent** node appears in Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] when you connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="ce1fc-115">若要自动执行某一重复发生的任务，您可以通过使用 **“新建作业”** 对话框创建某个作业。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-115">To automate a recurring task, you create a job by using the **New Job** dialog box.</span></span> <span data-ttu-id="ce1fc-116">有关详细信息，请参阅 [执行作业](../../ssms/agent/implement-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-116">For more information, see [Implement Jobs](../../ssms/agent/implement-jobs.md).</span></span>  
  
 <span data-ttu-id="ce1fc-117">创建该作业后，必须至少添加一个步骤。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-117">After you create the job, you must add at least one step.</span></span> <span data-ttu-id="ce1fc-118">一个作业可以包括多个步骤，并且每个步骤可以执行不同的任务。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-118">A job can include multiple steps, and each step can perform a different task.</span></span> <span data-ttu-id="ce1fc-119">有关详细信息，请参阅 [Manage Job Steps](../../ssms/agent/manage-job-steps.md)。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-119">For more information, see [Manage Job Steps](../../ssms/agent/manage-job-steps.md).</span></span>  
  
 <span data-ttu-id="ce1fc-120">在创建作业和作业步骤后，可以创建一个运行作业的计划。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-120">After you create the job and the job steps, you can create a schedule for running the job.</span></span> <span data-ttu-id="ce1fc-121">不过，您还可以创建手动运行的无人参与的作业。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-121">However you can also create an unscheduled job that you run manually.</span></span> <span data-ttu-id="ce1fc-122">有关详细信息，请参阅 [创建计划并将计划附加到作业](../../ssms/agent/create-and-attach-schedules-to-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-122">For more information, see [Create and Attach Schedules to Jobs](../../ssms/agent/create-and-attach-schedules-to-jobs.md).</span></span>  
  
 <span data-ttu-id="ce1fc-123">可以通过设置通知选项来增强作业，如指定在作业完成时向某个操作员发送电子邮件或添加警报。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-123">You can enhance the job by setting notification options, such as specifying an operator to send an e-mail message to when the job finishes, or adding alerts.</span></span> <span data-ttu-id="ce1fc-124">有关详细信息，请参阅 [“警报”](../../ssms/agent/alerts.md)。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-124">For more information, see [Alerts](../../ssms/agent/alerts.md).</span></span>  
  
##  <a name="scheduling-integration-services-packages"></a><a name="packages"></a> <span data-ttu-id="ce1fc-125">Scheduling Integration Services Packages</span><span class="sxs-lookup"><span data-stu-id="ce1fc-125">Scheduling Integration Services Packages</span></span>  
 <span data-ttu-id="ce1fc-126">在您创建一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业以便计划 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包后，必须至少添加一个步骤，并将该步骤的类型设置为 **“SQL Server Integration Services 包”** 。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-126">When you create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job to schedule [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you must add at least one step and set the type of the step to **SQL Server Integration Services Package**.</span></span> <span data-ttu-id="ce1fc-127">一个作业可以包括多个步骤，并且每个步骤可以运行不同的包。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-127">A job can include multiple steps, and each step can run a different package.</span></span>  
  
 <span data-ttu-id="ce1fc-128">从作业步骤中运行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包类似于使用 **dtexec** (dtexec.exe) 和 **DTExecUI** (dtexecui.exe) 实用工具运行包。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-128">Running an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package from a job step is like running a package by using the **dtexec** (dtexec.exe) and **DTExecUI** (dtexecui.exe) utilities.</span></span> <span data-ttu-id="ce1fc-129">可以在“新建作业步骤”对话框中设置运行时选项，而不是使用命令行选项或“执行包实用工具”对话框来设置包的运行时选项。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-129">Instead of setting the run-time options for a package by using command-line options or the **Execute Package Utility** dialog box, you set the run-time options in the **New Job Step** dialog box.</span></span> <span data-ttu-id="ce1fc-130">有关运行包的选项的详细信息，请参阅 [dtexec Utility](dtexec-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-130">For more information about the options for running a package, see [dtexec Utility](dtexec-utility.md).</span></span>  
  
 <span data-ttu-id="ce1fc-131">有关详细信息，请参阅 [使用 SQL Server 代理计划包](../schedule-a-package-by-using-sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-131">For more information, see [Schedule a Package by using SQL Server Agent](../schedule-a-package-by-using-sql-server-agent.md).</span></span>  
  
 <span data-ttu-id="ce1fc-132">有关演示如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理来运行包的视频，请观看 MSDN 库中的视频主页[操作说明：使用 SQL Server 代理自动执行包（SQL Server 视频）](https://go.microsoft.com/fwlink/?LinkId=141771)。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-132">For a video that demonstrates how to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run a package, see the video home page, [How to: Automate Package Execution by Using the SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141771), in the MSDN Library.</span></span>  
  
##  <a name="troubleshooting"></a><a name="trouble"></a> <span data-ttu-id="ce1fc-133">故障排除</span><span class="sxs-lookup"><span data-stu-id="ce1fc-133">Troubleshooting</span></span>  
 <span data-ttu-id="ce1fc-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业步骤可能无法启动某个包，即便该包可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中以及从命令行成功运行。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-134">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step may fail to start a package even though the package runs successfully in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and from the command line.</span></span> <span data-ttu-id="ce1fc-135">该问题有一些常见的原因和一些推荐的解决方法。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-135">There are some common reasons for this issue and several recommended solutions.</span></span> <span data-ttu-id="ce1fc-136">有关详细信息，请参阅以下资源。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-136">For more information, see the following resources.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="ce1fc-137">知识库文章： [当从 SQL Server 代理作业步骤调用 SSIS 包时 SSIS 包不运行](https://support.microsoft.com/kb/918760)</span><span class="sxs-lookup"><span data-stu-id="ce1fc-137">Knowledge Base article, [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760)</span></span>  
  
-   <span data-ttu-id="ce1fc-138">MSDN 库中的视频[排除故障：使用 SQL Server 代理执行包（SQL Server 视频）](https://go.microsoft.com/fwlink/?LinkId=141772)。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-138">Video, [Troubleshooting: Package Execution Using SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141772), in the MSDN Library.</span></span>  
  
 <span data-ttu-id="ce1fc-139">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业步骤启动某个包后，该包可能无法执行，或者包可能成功运行但出现意外结果。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-139">After a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step starts a package, the package execution may fail or the package may run successfully but with unexpected results.</span></span> <span data-ttu-id="ce1fc-140">可以使用下列工具来解决这些问题。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-140">You can use the following tools to troubleshoot these issues.</span></span>  
  
-   <span data-ttu-id="ce1fc-141">对于存储在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] MSDB 数据库、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包存储区或本地计算机上的文件夹中的包，可以使用 **“日志文件查看器”** 以及在包执行期间生成的任何日志和调试转储文件。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-141">For packages that are stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] MSDB database, the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, or in a folder on your local machine, you can use the **Log File Viewer** as well as any logs and debug dump files that were generated during the execution of the package.</span></span>  
  
     <span data-ttu-id="ce1fc-142">**若要使用日志文件查看器，请执行下列操作。**</span><span class="sxs-lookup"><span data-stu-id="ce1fc-142">**To use the Log File Viewer, do the following.**</span></span>  
  
    1.  <span data-ttu-id="ce1fc-143">右键单击对象资源管理器中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业，然后单击“查看历史记录”。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-143">Right-click the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in Object Explorer and then click **View History**.</span></span>  
  
    2.  <span data-ttu-id="ce1fc-144">在 **“日志文件摘要”** 框中，找到 **“消息”** 列中标有 **“作业失败”** 消息的作业执行。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-144">Locate the job execution in the **Log file summary** box with the **job failed** message in the **Message** column.</span></span>  
  
    3.  <span data-ttu-id="ce1fc-145">展开该作业节点，然后单击作业步骤查看 **“日志文件摘要”** 框下方区域中的消息的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-145">Expand the job node, and click the job step to view the details of the message in the area below the **Log file summary** box.</span></span>  
  
-   <span data-ttu-id="ce1fc-146">对于存储在 SSISDB 数据库中的包，也可以使用 **“日志文件查看器”** 以及在包执行期间生成的任何日志和调试转储文件。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-146">For packages that are stored in the SSISDB database, you can also use the **Log File Viewer** as well as any logs and debug dump files that were generated during the execution of the package.</span></span> <span data-ttu-id="ce1fc-147">此外，还可以使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器的报告。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-147">In addition, you can use the reports for the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="ce1fc-148">**若要查找报告中与作业执行关联的包执行的信息，请执行以下操作。**</span><span class="sxs-lookup"><span data-stu-id="ce1fc-148">**To find information in the reports for the package execution associated with a job execution, do the following.**</span></span>  
  
    1.  <span data-ttu-id="ce1fc-149">按照如上步骤查看作业步骤消息的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-149">Follow the steps above to view the details of the message for the job step.</span></span>  
  
    2.  <span data-ttu-id="ce1fc-150">找到消息中列出的执行 ID。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-150">Locate the Execution ID listed in the message.</span></span>  
  
    3.  <span data-ttu-id="ce1fc-151">在对象资源管理器中，展开“Integration Services 目录”节点。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-151">Expand the Integration Services Catalog node in Object Explorer.</span></span>  
  
    4.  <span data-ttu-id="ce1fc-152">右键单击 SSISDB，依次指向“报表”和“标准报表”，然后单击“所有执行”。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-152">Right-click SSISDB, point to Reports, then Standard Reports, and then click All Executions.</span></span>  
  
    5.  <span data-ttu-id="ce1fc-153">在 **“所有执行”** 报告的 **ID** 列中，找到该执行 ID。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-153">In the **All Executions** report, locate the Execution ID in the **ID** column.</span></span> <span data-ttu-id="ce1fc-154">单击 **“概述”** 、 **“所有消息”** 或 **“执行性能”** ，查看有关此包执行的信息。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-154">Click **Overview**, **All Messages**, or **Execution Performance** to view information about this package execution.</span></span>  
  
         <span data-ttu-id="ce1fc-155">有关“概述”、“所有消息”和“执行性能”报告的详细信息，请参阅 [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-155">For more information about the Overview, All Messages, and Execution Performance reports, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="ce1fc-156">外部资源</span><span class="sxs-lookup"><span data-stu-id="ce1fc-156">External Resources</span></span>  
  
-   <span data-ttu-id="ce1fc-157">[网站上的知识库文章：](https://support.microsoft.com/kb/918760)当从 SQL Server 代理作业步骤调用 SSIS 包时 SSIS 包不运行 [!INCLUDE[msCoName](../../includes/msconame-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce1fc-157">Knowledge Base article, [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760), on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Web site</span></span>  
  
-   <span data-ttu-id="ce1fc-158">MSDN 库中的视频[排除故障：使用 SQL Server 代理执行包（SQL Server 视频）](https://go.microsoft.com/fwlink/?LinkId=141772)</span><span class="sxs-lookup"><span data-stu-id="ce1fc-158">Video, [Troubleshooting: Package Execution Using SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141772), in the MSDN Library</span></span>  
  
-   <span data-ttu-id="ce1fc-159">MSDN 库中的视频[操作说明：使用 SQL Server 代理自动执行包（SQL Server 视频）](https://go.microsoft.com/fwlink/?LinkId=141771)</span><span class="sxs-lookup"><span data-stu-id="ce1fc-159">Video, [How to: Automate Package Execution by Using the SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141771), in the MSDN Library</span></span>  
  
-   <span data-ttu-id="ce1fc-160">mssqltips.com 上的技术文章 [Checking SQL Server Agent jobs using Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=165675)（使用 Windows PowerShell 检查 SQL Server 代理作业）</span><span class="sxs-lookup"><span data-stu-id="ce1fc-160">Technical article, [Checking SQL Server Agent jobs using Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=165675), on mssqltips.com</span></span>  
  
-   <span data-ttu-id="ce1fc-161">mssqltips.com 上的技术文章 [Auto alert for SQL Agent jobs when they are enabled or disabled](https://go.microsoft.com/fwlink/?LinkId=165676)（在 SQL 代理作业启用或禁用时针对它们的自动警报）</span><span class="sxs-lookup"><span data-stu-id="ce1fc-161">Technical article, [Auto alert for SQL Agent jobs when they are enabled or disabled](https://go.microsoft.com/fwlink/?LinkId=165676), on mssqltips.com</span></span>  
  
-   <span data-ttu-id="ce1fc-162">mssqltips.com 上的博客文章 [配置 SQL 代理作业以便写入 Windows 事件日志](https://go.microsoft.com/fwlink/?LinkId=220745)。</span><span class="sxs-lookup"><span data-stu-id="ce1fc-162">Blog entry, [Configuring SQL Agent Jobs to Write to Windows Event Log](https://go.microsoft.com/fwlink/?LinkId=220745), on mssqltips.com.</span></span>  
  
  
