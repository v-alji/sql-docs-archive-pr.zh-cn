---
title: 用 SQL Server 代理计划 SSAS 管理任务 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2d1484b3-51d9-48a0-93d2-0c3e4ed22b87
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2c78fa5fcebc0589ba863163b93ad2d10731b75a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690198"
---
# <a name="schedule-ssas-administrative-tasks-with-sql-server-agent"></a><span data-ttu-id="386fd-102">使用 SQL Server 代理来计划 SSAS 管理任务</span><span class="sxs-lookup"><span data-stu-id="386fd-102">Schedule SSAS Administrative Tasks with SQL Server Agent</span></span>
  <span data-ttu-id="386fd-103">使用 SQL Server 代理服务，你可以根据所需顺序和时间来计划要运行的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理任务。</span><span class="sxs-lookup"><span data-stu-id="386fd-103">Using the SQL Server Agent service, you can schedule [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrative tasks to run in the order and times that you need.</span></span> <span data-ttu-id="386fd-104">通过计划任务，可以自动运行定期或以可预测周期运行的进程。</span><span class="sxs-lookup"><span data-stu-id="386fd-104">Scheduled tasks help you automate processes that run on regular or predictable cycles.</span></span> <span data-ttu-id="386fd-105">您可以计划管理任务（例如多维数据集处理）以在周期长的业务活动期间运行。</span><span class="sxs-lookup"><span data-stu-id="386fd-105">You can schedule administrative tasks, such as cube processing, to run during times of slow business activity.</span></span> <span data-ttu-id="386fd-106">还可以通过在 SQL Server 代理作业中创建作业步骤来确定任务的执行顺序。</span><span class="sxs-lookup"><span data-stu-id="386fd-106">You can also determine the order in which tasks run by creating job steps within a SQL Server Agent job.</span></span> <span data-ttu-id="386fd-107">例如，可以处理多维数据集，然后对该多维数据集进行备份。</span><span class="sxs-lookup"><span data-stu-id="386fd-107">For example, you can process a cube and then perform a backup of the cube.</span></span>  
  
 <span data-ttu-id="386fd-108">使用作业步骤，可以控制执行流。</span><span class="sxs-lookup"><span data-stu-id="386fd-108">Job steps give you control over flow of execution.</span></span> <span data-ttu-id="386fd-109">如果一个作业失败，则可以配置 SQL Server 代理以继续运行剩下的任务或停止执行。</span><span class="sxs-lookup"><span data-stu-id="386fd-109">If one job fails, you can configure SQL Server Agent to continue to run the remaining tasks or to stop execution.</span></span> <span data-ttu-id="386fd-110">也可以配置 SQL Server 代理以发送有关作业执行成功或失败的通知。</span><span class="sxs-lookup"><span data-stu-id="386fd-110">You can also configure SQL Server Agent to send notifications about the success or failure of job execution.</span></span>  
  
 <span data-ttu-id="386fd-111">本主题是一个演练，演示了如何使用 SQL Server 代理通过两种方式运行 XMLA 脚本。</span><span class="sxs-lookup"><span data-stu-id="386fd-111">This topic is a walkthrough that shows two ways of using SQL Server Agent to run XMLA script.</span></span> <span data-ttu-id="386fd-112">第一个示例演示如何计划对单个维度的处理。</span><span class="sxs-lookup"><span data-stu-id="386fd-112">The first example demonstrates how to schedule processing of a single dimension.</span></span> <span data-ttu-id="386fd-113">第二个示例演示如何将处理任务并入按计划运行的单个脚本。</span><span class="sxs-lookup"><span data-stu-id="386fd-113">Example two shows how to combine processing tasks into a single script that runs on a schedule.</span></span> <span data-ttu-id="386fd-114">若要完成此演练，您需要满足下列先决条件。</span><span class="sxs-lookup"><span data-stu-id="386fd-114">To complete this walkthrough, you will need to meet the following prerequisites.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="386fd-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="386fd-115">Prerequisites</span></span>  
 <span data-ttu-id="386fd-116">必须安装 SQL Server 代理服务。</span><span class="sxs-lookup"><span data-stu-id="386fd-116">SQL Server Agent service must be installed.</span></span>  
  
 <span data-ttu-id="386fd-117">默认情况下，作业在服务帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="386fd-117">By default, jobs run under the service account.</span></span> <span data-ttu-id="386fd-118">在中 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ，SQL Server 代理的默认帐户是 NT Service\SQLAgent $ \<instancename> 。</span><span class="sxs-lookup"><span data-stu-id="386fd-118">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the default account for SQL Server Agent is NT Service\SQLAgent$\<instancename>.</span></span> <span data-ttu-id="386fd-119">若要执行备份或处理任务，此帐户必须是 Analysis Services 实例的系统管理员。</span><span class="sxs-lookup"><span data-stu-id="386fd-119">To perform a backup or processing task, this account must be a system administrator on the Analysis Services instance.</span></span> <span data-ttu-id="386fd-120">有关详细信息，请参阅[&#40;Analysis Services&#41;授予服务器管理员权限](grant-server-admin-rights-to-an-analysis-services-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="386fd-120">For more information, see [Grant Server Administrator Permissions &#40;Analysis Services&#41;](grant-server-admin-rights-to-an-analysis-services-instance.md).</span></span>  
  
 <span data-ttu-id="386fd-121">您还应拥有要使用的测试数据库。</span><span class="sxs-lookup"><span data-stu-id="386fd-121">You should also have a test database to work with.</span></span> <span data-ttu-id="386fd-122">可以部署 AdventureWorks 多维示例数据库或 Analysis Services 多维教程中的项目以在本演练中使用。</span><span class="sxs-lookup"><span data-stu-id="386fd-122">You can deploy the AdventureWorks multidimensional sample database or a project from the Analysis Services multidimensional tutorial to use in this walkthrough.</span></span> <span data-ttu-id="386fd-123">有关详细信息，请参阅[安装 Analysis Services 多维建模教程的示例数据和项目](../install-sample-data-and-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="386fd-123">For more information, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](../install-sample-data-and-projects.md).</span></span>  
  
## <a name="example-1-processing-a-dimension-in-a-scheduled-task"></a><span data-ttu-id="386fd-124">示例 1：处理计划任务中的维度</span><span class="sxs-lookup"><span data-stu-id="386fd-124">Example 1: Processing a dimension in a scheduled task</span></span>  
 <span data-ttu-id="386fd-125">此示例演示如何创建和计划处理维度的作业。</span><span class="sxs-lookup"><span data-stu-id="386fd-125">This example demonstrates how to create and schedule a job that processes a dimension.</span></span>  
  
 <span data-ttu-id="386fd-126">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 计划任务是嵌入在 SQL Server 代理作业中的 XMLA 脚本。</span><span class="sxs-lookup"><span data-stu-id="386fd-126">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] scheduled task is an XMLA script that is embedded into a SQL Server Agent job.</span></span> <span data-ttu-id="386fd-127">该作业经过计划，按照所需时间和频率运行。</span><span class="sxs-lookup"><span data-stu-id="386fd-127">This job is scheduled to run at desired times and frequency.</span></span> <span data-ttu-id="386fd-128">由于 SQL Server 代理是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的一部分，因此要同时使用数据库引擎和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 来创建和计划管理任务。</span><span class="sxs-lookup"><span data-stu-id="386fd-128">Because the SQL Server Agent is part of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you work with both the Database Engine and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to create and schedule an administrative task.</span></span>  
  
###  <a name="create-a-script-for-processing-a-dimension-in-a-sql-server-agent-job"></a><a name="bkmk_CreateScript"></a><span data-ttu-id="386fd-129">创建用于处理 SQL Server 代理作业中的维度的脚本</span><span class="sxs-lookup"><span data-stu-id="386fd-129">Create a script for processing a dimension in a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="386fd-130">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="386fd-130">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="386fd-131">打开数据库文件夹并查找维度。</span><span class="sxs-lookup"><span data-stu-id="386fd-131">Open a database folder and find a dimension.</span></span> <span data-ttu-id="386fd-132">右键单击维度，然后选择“处理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="386fd-132">Right-click the dimension and select **Process**.</span></span>  
  
2.  <span data-ttu-id="386fd-133">在 **“处理维度”** 对话框的 **“对象列表”** 下的 **“处理选项”** 列中，验证此列的选项是否为 **“处理全部”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-133">In the **Process Dimension** dialog box, in the **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span> <span data-ttu-id="386fd-134">如果不是，则在“处理选项”\*\*\*\* 下单击选项，然后从下拉列表中选择“处理全部”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="386fd-134">If it is not, under **Process Options**, click the option, and then select **Process Full** from the drop-down list.</span></span>  
  
3.  <span data-ttu-id="386fd-135">单击 **“脚本”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-135">Click **Script**.</span></span>  
  
     <span data-ttu-id="386fd-136">此步骤将打开包含处理维度的 XMLA 脚本的 **“XML 查询”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="386fd-136">This step opens an **XML Query** window that contains the XMLA script that processes the dimension.</span></span>  
  
4.  <span data-ttu-id="386fd-137">在 **“处理维度”** 对话框中，单击 **“取消”** 关闭该对话框。</span><span class="sxs-lookup"><span data-stu-id="386fd-137">In the **Process Dimension** dialog box, click **Cancel** to close the dialog box.</span></span>  
  
5.  <span data-ttu-id="386fd-138">在“XMLA 查询”\*\*\*\* 窗口中，突出显示 XMLA 脚本，右键单击突出显示的脚本，然后选择“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="386fd-138">In the **XMLA Query** window, highlight the XMLA script, right-click the highlighted script, and select **Copy**.</span></span>  
  
     <span data-ttu-id="386fd-139">此步骤会将 XMLA 脚本复制到 Windows 剪贴板中。</span><span class="sxs-lookup"><span data-stu-id="386fd-139">This step copies the XMLA script to the Windows Clipboard.</span></span> <span data-ttu-id="386fd-140">可以将 XMLA 脚本保留在剪贴板中，也可以将其粘贴到记事本或其他文本编辑器中。</span><span class="sxs-lookup"><span data-stu-id="386fd-140">You can leave the XMLA script in the Clipboard or paste it into Notepad or another text editor.</span></span> <span data-ttu-id="386fd-141">以下是 XMLA 脚本的一个示例。</span><span class="sxs-lookup"><span data-stu-id="386fd-141">The following is an example of the XMLA script.</span></span>  
  
    ```  
    <Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
     <Parallel>  
      <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
          <DimensionID>Dim Account</DimensionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
     </Parallel>  
    </Batch>  
    ```  
  
###  <a name="create-and-schedule-the-dimension-processing-job"></a><a name="bkmk_ProcessJob"></a><span data-ttu-id="386fd-142">创建和计划维度处理作业</span><span class="sxs-lookup"><span data-stu-id="386fd-142">Create and schedule the dimension processing job</span></span>  
  
1.  <span data-ttu-id="386fd-143">连接到数据库引擎实例，然后打开对象资源管理器。</span><span class="sxs-lookup"><span data-stu-id="386fd-143">Connect to an instance of the Database Engine and then open Object Explorer.</span></span>  
  
2.  <span data-ttu-id="386fd-144">展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-144">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="386fd-145">右键单击“作业”\*\*\*\*，然后选择“新建作业”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="386fd-145">Right-click **Jobs** and select **New Job**.</span></span>  
  
4.  <span data-ttu-id="386fd-146">在 **“新建作业”** 对话框的 **“名称”** 中，输入作业名称。</span><span class="sxs-lookup"><span data-stu-id="386fd-146">In the **New Job** dialog box, enter a job name in **Name**.</span></span>  
  
5.  <span data-ttu-id="386fd-147">在 **“选择页”** 下，选择 **“步骤”**，然后单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-147">Under **Select a page**, select **Steps**, and then click **New**.</span></span>  
  
6.  <span data-ttu-id="386fd-148">在 **“新建作业步骤”** 对话框的 **“步骤名称”** 中，输入步骤名称。</span><span class="sxs-lookup"><span data-stu-id="386fd-148">In the **New Job Step** dialog box, enter a step name in **Step Name**.</span></span>  
  
7.  <span data-ttu-id="386fd-149">在 "**服务器**" 中，键入默认实例的**localhost** ， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 并为命名实例键入\*\*localhost \\ \*\* \<*instance name*> 。</span><span class="sxs-lookup"><span data-stu-id="386fd-149">In **Server**, type **localhost** for a default instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and **localhost\\**\<*instance name*> for a named instance.</span></span>  
  
     <span data-ttu-id="386fd-150">如果您将从远程计算机运行作业，请使用将运行作业的服务器和实例的名称。</span><span class="sxs-lookup"><span data-stu-id="386fd-150">If you will be running the job from a remote computer, use the server name and instance name where the job will run.</span></span> <span data-ttu-id="386fd-151">对于 \<*server name*> 命名实例，请使用格式> 默认实例和 \<*server name*> \\ < *实例名称*。</span><span class="sxs-lookup"><span data-stu-id="386fd-151">Use the format \<*server name*> for a default instance, and \<*server name*>\\<*instance name*> for a named instance.</span></span>  
  
8.  <span data-ttu-id="386fd-152">在 **“类型”** 中，选择 **“SQL Server Analysis Services 命令”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-152">In **Type**, select **SQL Server Analysis Services Command**.</span></span>  
  
9. <span data-ttu-id="386fd-153">在“命令”\*\*\*\* 中，右键单击并选择“粘贴”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="386fd-153">In **Command**, right-click and select **Paste**.</span></span> <span data-ttu-id="386fd-154">上一步中生成的 XMLA 脚本应显示在命令窗口中。</span><span class="sxs-lookup"><span data-stu-id="386fd-154">The XMLA script that you generated in the previous step should appear in the command window.</span></span>  
  
10. <span data-ttu-id="386fd-155">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="386fd-155">Click **OK**.</span></span>  
  
11. <span data-ttu-id="386fd-156">在 **“选择页”** 下，单击 **“计划”**，然后单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-156">Under **Select a page**, click **Schedules**, and then click **New**.</span></span>  
  
12. <span data-ttu-id="386fd-157">在 **“新建作业计划”** 对话框的 **“名称”** 中，输入计划名称，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-157">In the **New Job Schedule** dialog box, enter a schedule name in **Name**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="386fd-158">此步骤将创建一个于星期日 12:00 AM 启动的计划。</span><span class="sxs-lookup"><span data-stu-id="386fd-158">This step creates a schedule for Sunday at 12:00 AM.</span></span> <span data-ttu-id="386fd-159">下一步将说明如何手动执行作业。</span><span class="sxs-lookup"><span data-stu-id="386fd-159">The next step shows you how to manually execute the job.</span></span> <span data-ttu-id="386fd-160">您还可指定在监视作业时执行作业的计划。</span><span class="sxs-lookup"><span data-stu-id="386fd-160">You can also specify a schedule that executes the job when you are monitoring it.</span></span>  
  
13. <span data-ttu-id="386fd-161">在 **“新建作业”** 对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-161">In the **New Job** dialog box, click **OK**.</span></span>  
  
14. <span data-ttu-id="386fd-162">在“对象资源管理器”\*\*\*\* 中，展开“作业”\*\*\*\*，右键单击创建的作业，然后选择“作业开始步骤”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="386fd-162">In **Object Explorer**, expand **Jobs**, right-click the job you created, and then select **Start Job at Step**.</span></span>  
  
     <span data-ttu-id="386fd-163">由于该作业仅包含一个步骤，因此将立即执行它。</span><span class="sxs-lookup"><span data-stu-id="386fd-163">Because the job has only one step, the job executes immediately.</span></span> <span data-ttu-id="386fd-164">如果作业包含多个步骤，则可选择作业的开始步骤。</span><span class="sxs-lookup"><span data-stu-id="386fd-164">If the job contains more than one step, you can select the step at which the job should start.</span></span>  
  
15. <span data-ttu-id="386fd-165">在作业完成后，请单击 **“关闭”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-165">When the job finishes, click **Close**.</span></span>  
  
## <a name="example-2-batch-processing-a-dimension-and-a-partition-in-a-scheduled-task"></a><span data-ttu-id="386fd-166">示例 2：批处理计划任务中的维度和分区</span><span class="sxs-lookup"><span data-stu-id="386fd-166">Example 2: Batch processing a dimension and a partition in a scheduled task</span></span>  
 <span data-ttu-id="386fd-167">此示例中的过程演示如何创建和计划一个作业，该作业将批处理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库维度并处理依赖于聚合维度的多维数据集分区。</span><span class="sxs-lookup"><span data-stu-id="386fd-167">The procedures in this example demonstrate how to create and schedule a job that batch processes an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database dimension, and at the same time to process a  cube partition that depends on the dimension for aggregation.</span></span> <span data-ttu-id="386fd-168">有关批处理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象的详细信息，请参阅[批处理 (Analysis Services)](../multidimensional-models/batch-processing-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="386fd-168">For more information about batch processing of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Batch Processing &#40;Analysis Services&#41;](../multidimensional-models/batch-processing-analysis-services.md).</span></span>  
  
###  <a name="create-a-script-for-batch-processing-a-dimension-and-partition-in-a-sql-server-agent-job"></a><a name="bkmk_BatchProcess"></a><span data-ttu-id="386fd-169">创建用于批处理 SQL Server 代理作业中的维度和分区的脚本</span><span class="sxs-lookup"><span data-stu-id="386fd-169">Create a script for batch processing a dimension and partition in a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="386fd-170">通过使用相同的数据库，展开“维度”\*\*\*\*，右键单击“客户”\*\*\*\* 维度，然后选择“处理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="386fd-170">Using the same database, expand **Dimensions**, right-click the **Customer** dimension, and select **Process**.</span></span>  
  
2.  <span data-ttu-id="386fd-171">在 **“处理维度”** 对话框的 **“对象列表”** 下的 **“处理选项”** 列中，验证此列的选项是否为 **“处理全部”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-171">In the **Process Dimension** dialog box, in **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span>  
  
3.  <span data-ttu-id="386fd-172">单击 **“脚本”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-172">Click **Script**.</span></span>  
  
     <span data-ttu-id="386fd-173">此步骤将打开包含处理维度的 XMLA 脚本的 **“XML 查询”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="386fd-173">This step opens an **XML Query** window that contains the XMLA script that processes the dimension.</span></span>  
  
4.  <span data-ttu-id="386fd-174">在 **“处理维度”** 对话框中，单击 **“取消”** 关闭该对话框。</span><span class="sxs-lookup"><span data-stu-id="386fd-174">In the **Process Dimension** dialog box, click **Cancel** to close the dialog box.</span></span>  
  
5.  <span data-ttu-id="386fd-175">依次展开“多维数据集”\*\*\*\*、“Adventure Works”\*\*\*\*、“度量值组”\*\*\*\*、“Internet 销售”\*\*\*\* 和“分区”\*\*\*\*，右键单击列表中的最后一个分区，然后选择“处理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="386fd-175">Expand **Cubes**, expand **Adventure Works**, expand **Measure Groups**, expand **Internet Sales**, expand **Partitions**, right-click the last partition in the list, and then select **Process**.</span></span>  
  
6.  <span data-ttu-id="386fd-176">在 **“处理分区”** 对话框的 **“对象列表”** 下的 **“处理选项”** 列中，验证此列的选项是否为 **“处理全部”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-176">In the **Process Partition** dialog box, in the **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span>  
  
7.  <span data-ttu-id="386fd-177">单击 **“脚本”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-177">Click **Script**.</span></span>  
  
     <span data-ttu-id="386fd-178">此步骤将打开另一个包含处理分区的 XMLA 脚本的 **“XML 查询”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="386fd-178">This step opens a second **XML Query** window that contains the XMLA script that processes the partition.</span></span>  
  
8.  <span data-ttu-id="386fd-179">在 **“处理分区”** 对话框中，单击 **“取消”** 关闭该编辑器。</span><span class="sxs-lookup"><span data-stu-id="386fd-179">In the **Process Partition** dialog box, click **Cancel** to close the editor.</span></span>  
  
     <span data-ttu-id="386fd-180">此时，您必须合并这两个脚本，并确保先处理维度。</span><span class="sxs-lookup"><span data-stu-id="386fd-180">At this point you must merge the two scripts, and ensure that the dimension is processed first.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="386fd-181">如果先处理分区，则后续维度处理将导致分区变为未处理状态。</span><span class="sxs-lookup"><span data-stu-id="386fd-181">If the partition is processed first, the subsequent dimension processing causes the partition to become unprocessed.</span></span> <span data-ttu-id="386fd-182">之后，必须再一次处理分区才能使其处于已处理状态。</span><span class="sxs-lookup"><span data-stu-id="386fd-182">The partition would then require a second processing to reach a processed state.</span></span>  
  
9. <span data-ttu-id="386fd-183">在包含处理分区的 XMLA 脚本的“XMLA 查询”\*\*\*\* 窗口中，突出显示 `Batch` 和 `Parallel` 标记中的代码，右键单击突出显示的脚本，然后选择“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="386fd-183">In the **XMLA Query** window that contains the XMLA script that processes the partition, highlight the code inside the `Batch` and `Parallel` tags, right-click the highlighted script, and select **Copy**.</span></span>  
  
    ```  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID> Adventure Works DW Multidimensional</DatabaseID>  
          <CubeID>Adventure Works</CubeID>  
          <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
          <PartitionID> Internet_Sales_2004</PartitionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
    ```  
  
10. <span data-ttu-id="386fd-184">打开包含处理维度的 XMLA 脚本的 **“XMLA 查询”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="386fd-184">Open the **XMLA Query** window that contains the XMLA script that processes the dimension.</span></span> <span data-ttu-id="386fd-185">在 `</Process>` 标记左侧的脚本中右键单击，然后选择“粘贴”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="386fd-185">Right-click within the script to the left of the `</Process>` tag and select **Paste**.</span></span>  
  
     <span data-ttu-id="386fd-186">下面的示例显示了修改后的 XMLA 脚本。</span><span class="sxs-lookup"><span data-stu-id="386fd-186">The following example shows the revised XMLA script.</span></span>  
  
    ```  
    <Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
     <Parallel>  
      <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
          <DimensionID>Dim Customer</DimensionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
      <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
          <CubeID>Adventure Works</CubeID>  
          <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
          <PartitionID>Internet_Sales_2004</PartitionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
     </Parallel>  
    </Batch>  
    ```  
  
11. <span data-ttu-id="386fd-187">突出显示修改后的 XMLA 脚本，右键单击突出显示的脚本，然后选择“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="386fd-187">Highlight the revised XMLA script, right-click the highlighted script, and select **Copy.**</span></span>  
  
12. <span data-ttu-id="386fd-188">此步骤会将 XMLA 脚本复制到 Windows 剪贴板中。</span><span class="sxs-lookup"><span data-stu-id="386fd-188">This step copies the XMLA script to the Windows Clipboard.</span></span> <span data-ttu-id="386fd-189">可以将 XMLA 脚本保留在剪贴板中、将其保存到文件中或将其粘贴到记事本或其他文本编辑器中。</span><span class="sxs-lookup"><span data-stu-id="386fd-189">You can leave the XMLA script in the Clipboard, save it to a file, or paste it into Notepad or another text editor.</span></span>  
  
###  <a name="create-and-schedule-the-batch-processing-job"></a><a name="bkmk_Scheduling"></a><span data-ttu-id="386fd-190">创建和计划批处理作业</span><span class="sxs-lookup"><span data-stu-id="386fd-190">Create and schedule the batch processing job</span></span>  
  
1.  <span data-ttu-id="386fd-191">连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例，然后打开对象资源管理器。</span><span class="sxs-lookup"><span data-stu-id="386fd-191">Connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then open Object Explorer.</span></span>  
  
2.  <span data-ttu-id="386fd-192">展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-192">Expand **SQL Server Agent**.</span></span> <span data-ttu-id="386fd-193">如果该服务尚未运行，请启动该服务。</span><span class="sxs-lookup"><span data-stu-id="386fd-193">Start the service if is not running.</span></span>  
  
3.  <span data-ttu-id="386fd-194">右键单击“作业”\*\*\*\*，然后选择“新建作业”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="386fd-194">Right-click **Jobs** and select **New Job**.</span></span>  
  
4.  <span data-ttu-id="386fd-195">在 **“新建作业”** 对话框的 **“名称”** 中，输入作业名称。</span><span class="sxs-lookup"><span data-stu-id="386fd-195">In the **New Job** dialog box, enter a job name in **Name**.</span></span>  
  
5.  <span data-ttu-id="386fd-196">在 **“步骤”** 中，单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-196">In **Steps**, click **New**.</span></span>  
  
6.  <span data-ttu-id="386fd-197">在 **“新建作业步骤”** 对话框的 **“步骤名称”** 中，输入步骤名称。</span><span class="sxs-lookup"><span data-stu-id="386fd-197">In the **New Job Step** dialog box, enter a step name in **Step Name**.</span></span>  
  
7.  <span data-ttu-id="386fd-198">在 **“类型”** 中，选择 **“SQL Server Analysis Services 命令”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-198">In **Type**, select **SQL Server Analysis Services Command**.</span></span>  
  
8.  <span data-ttu-id="386fd-199">在 **“运行身份”** 中，选择 **“SQL Server 代理服务帐户”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-199">In **Run as**, select the **SQL Server Agent Service Account**.</span></span> <span data-ttu-id="386fd-200">回想“先决条件”部分中所述的内容，此帐户必须对 Analysis Services 具有管理权限。</span><span class="sxs-lookup"><span data-stu-id="386fd-200">Recall from the Prerequisites section that this account must have administrative permissions on Analysis Services.</span></span>  
  
9. <span data-ttu-id="386fd-201">在 **“服务器”** 中，指定 Analysis Services 实例的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="386fd-201">In **Server**, specify the server name of the Analysis Services instance.</span></span>  
  
10. <span data-ttu-id="386fd-202">在“命令”\*\*\*\* 中，右键单击并选择“粘贴”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="386fd-202">In **Command**, right-click and select **Paste**.</span></span>  
  
11. <span data-ttu-id="386fd-203">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="386fd-203">Click **OK**.</span></span>  
  
12. <span data-ttu-id="386fd-204">在 **“计划”** 页上，单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-204">In the **Schedules** page, click **New**.</span></span>  
  
13. <span data-ttu-id="386fd-205">在 **“新建作业计划”** 对话框的 **“名称”** 中，输入计划名称，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-205">In the **New Job Schedule** dialog box, enter a schedule name in **Name**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="386fd-206">此步骤将创建一个于星期日 12:00 AM 启动的计划。</span><span class="sxs-lookup"><span data-stu-id="386fd-206">This step creates a schedule for Sunday at 12:00 AM.</span></span> <span data-ttu-id="386fd-207">下一步将说明如何手动执行作业。</span><span class="sxs-lookup"><span data-stu-id="386fd-207">The next step shows you how to manually execute the job.</span></span> <span data-ttu-id="386fd-208">您还可选择将在监视作业时执行作业的计划。</span><span class="sxs-lookup"><span data-stu-id="386fd-208">You can also select a schedule which will execute the job when you are monitoring it.</span></span>  
  
14. <span data-ttu-id="386fd-209">单击 **“确定”** 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="386fd-209">Click **OK** to close the dialog box.</span></span>  
  
15. <span data-ttu-id="386fd-210">在“对象资源管理器”\*\*\*\* 中，展开“作业”\*\*\*\*，右键单击创建的作业，然后选择“作业开始步骤”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="386fd-210">In **Object Explorer**, expand **Jobs**, right-click the job you created, and select **Start Job at Step**.</span></span>  
  
     <span data-ttu-id="386fd-211">由于该作业仅包含一个步骤，因此将立即执行它。</span><span class="sxs-lookup"><span data-stu-id="386fd-211">Because the job has only one step, the job executes immediately.</span></span> <span data-ttu-id="386fd-212">如果作业包含多个步骤，则可选择作业的开始步骤。</span><span class="sxs-lookup"><span data-stu-id="386fd-212">If the job contains more than one step, you can select the step at which the job should start.</span></span>  
  
16. <span data-ttu-id="386fd-213">在作业完成后，请单击 **“关闭”**。</span><span class="sxs-lookup"><span data-stu-id="386fd-213">When the job finishes, click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="386fd-214">另请参阅</span><span class="sxs-lookup"><span data-stu-id="386fd-214">See Also</span></span>  
 <span data-ttu-id="386fd-215">[处理选项和设置的 &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="386fd-215">[Processing Options and Settings &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md) </span></span>  
 [<span data-ttu-id="386fd-216">在 Analysis Services 中编写管理任务脚本</span><span class="sxs-lookup"><span data-stu-id="386fd-216">Script Administrative Tasks in Analysis Services</span></span>](../script-administrative-tasks-in-analysis-services.md)  
  
  
