---
title: 远程处理 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d58bcb3c-0b3f-4ab0-81eb-4fdcc86153af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4e0d6ade25f5a321e49c748692a961abc369efad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588105"
---
# <a name="remote-processing-analysis-services"></a><span data-ttu-id="b5c4e-102">远程处理 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="b5c4e-102">Remote Processing (Analysis Services)</span></span>
  <span data-ttu-id="b5c4e-103">可在远程 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例上运行计划处理或无人参与的处理，其中在一台计算机上发出处理请求，而在同一网络上的另一台计算机上执行该请求。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-103">You can run scheduled or unattended processing on a remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, where the processing request originates from one computer but executes on another computer on the same network.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b5c4e-104">必备条件</span><span class="sxs-lookup"><span data-stu-id="b5c4e-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="b5c4e-105">如果在每台计算机上运行的 SQL Server 版本不同，则客户端库必须与处理模型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例版本一致。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-105">If you are running different versions of SQL Server on each computer, the client libraries must match the version of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that is processing the model.</span></span> <span data-ttu-id="b5c4e-106">例如，如果在 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] 实例上进行处理，则发起请求的计算机必须具有与 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]对应的客户端库。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-106">For example, if processing is on a [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] instance, then the computer from which the request originates must have the client library corresponding to [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].</span></span> <span data-ttu-id="b5c4e-107">请参阅 [用于 Analysis Services 连接的数据访问接口](../instances/data-providers-used-for-analysis-services-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-107">See [Data providers used for Analysis Services connections](../instances/data-providers-used-for-analysis-services-connections.md).</span></span>  
  
-   <span data-ttu-id="b5c4e-108">在远程服务器上，必须启用 **“允许远程连接到此计算机”** ，然后必须列出发出处理请求的帐户作为允许的用户。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-108">On the remote server, **Allow remote connections to this computer** must be enabled, and the account issuing the processing request must be listed as an allowed user.</span></span>  
  
-   <span data-ttu-id="b5c4e-109">必须配置 Windows 防火墙规则以允许进入 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的入站连接。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-109">Windows firewall rules must be configured to allow inbound connections to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="b5c4e-110">确认可使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 连接到远程 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-110">Verify you can connect to the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="b5c4e-111">请参阅 [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-111">See [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
-   <span data-ttu-id="b5c4e-112">先解决任何现有的本地处理错误，然后再尝试进行远程处理。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-112">Resolve any existing local processing errors before attempting remote processing.</span></span> <span data-ttu-id="b5c4e-113">确认在处理请求位于本地时，可成功地从外部关系数据源检索数据。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-113">Verify that when the processing request is local, data can be successfully retrieved from the external relational data source.</span></span> <span data-ttu-id="b5c4e-114">有关指定用于检索数据的凭据的说明，请参阅[设置模拟选项（SSAS-多维）](set-impersonation-options-ssas-multidimensional.md)。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-114">See [Set Impersonation Options &#40;SSAS - Multidimensional&#41;](set-impersonation-options-ssas-multidimensional.md) for instructions on specifying credentials used to retrieve data.</span></span>  
  
## <a name="on-demand-remote-processing"></a><span data-ttu-id="b5c4e-115">按需远程处理</span><span class="sxs-lookup"><span data-stu-id="b5c4e-115">On-demand remote processing</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="b5c4e-116">接受从具有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理员权限的用户或应用程序帐户发出的处理请求。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-116">accepts processing requests from user or application accounts that have [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrator permissions.</span></span> <span data-ttu-id="b5c4e-117">如果您是管理员，请确认您可连接到远程实例并可通过远程连接手动处理数据库。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-117">If you are an administrator, verify that you can connect to the remote instance and process the database manually over the remote connection.</span></span>  
  
1.  <span data-ttu-id="b5c4e-118">在将用于安排处理的计算机上，启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 并连接到远程 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-118">On the computer that will be used to schedule processing, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
2.  <span data-ttu-id="b5c4e-119">右键单击数据库，选择“处理”，指向“脚本”，然后选择“将操作脚本保存到‘新建查询’窗口”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="b5c4e-119">Right-click the database, select **Process**, point to **Script** and choose **Script Action to New Query Window**.</span></span> <span data-ttu-id="b5c4e-120">随后将在查询窗口中显示用于调用处理的命令。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-120">Commands used to invoke processing will appear in the query window.</span></span>  
  
3.  <span data-ttu-id="b5c4e-121">单击“确认” \*\*\*\* 以开始处理。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-121">Click **OK** to begin processing.</span></span>  
  
     <span data-ttu-id="b5c4e-122">成功完成此任务后，将提供一个 XMLA 查询，可将其嵌入计划作业中。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-122">Successful completion of this task provides an XMLA query that you can embed in a scheduled job.</span></span> <span data-ttu-id="b5c4e-123">它还确认没有连接问题。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-123">It also confirms there are no connection problems.</span></span>  
  
## <a name="schedule-remote-processing-using-sql-server-agent-service"></a><span data-ttu-id="b5c4e-124">使用 SQL Server 代理服务安排远程处理</span><span class="sxs-lookup"><span data-stu-id="b5c4e-124">Schedule remote processing using SQL Server Agent Service</span></span>  
 <span data-ttu-id="b5c4e-125">默认情况下，SQL Server 代理服务在虚拟帐户下运行，其中使用计算机帐户进行网络连接。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-125">By default, SQL Server Agent service runs under a virtual account, with network connections made using the machine account.</span></span> <span data-ttu-id="b5c4e-126">若要避免必须向计算机帐户授予对远程 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的管理权限，应更改 SQL Server 代理服务帐户，使其以最低权限的域用户帐户身份运行。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-126">To avoid having to give a machine account administrative rights on the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, you should change the SQL Server Agent service account to run as a least-privilege domain user account.</span></span>  
  
 <span data-ttu-id="b5c4e-127">请务必授予所有必要的权限，包括向帐户 **sysadmin** 授予对提供服务的数据库引擎实例的权限。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-127">Be sure to grant all of the necessary permissions, including giving the account **sysadmin** rights on the Database Engine instance providing the service.</span></span>  
  
 <span data-ttu-id="b5c4e-128">使用以下链接设置权限：</span><span class="sxs-lookup"><span data-stu-id="b5c4e-128">Use the following links to set permissions:</span></span>  
  
-   [<span data-ttu-id="b5c4e-129">配置 SQL Server 代理</span><span class="sxs-lookup"><span data-stu-id="b5c4e-129">Configure SQL Server Agent</span></span>](../../ssms/agent/configure-sql-server-agent.md)  
  
-   <span data-ttu-id="b5c4e-130">如果不可能授予[SQL Server Agent Components](../../ssms/agent/sql-server-agent.md#Components) 权限，则 **SQL Server Agent Components** 建议另外的固定服务器角色。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-130">[SQL Server Agent Components](../../ssms/agent/sql-server-agent.md#Components) suggests alternative fixed server roles if granting **sysadmin** permissions is not possible.</span></span>  
  
 <span data-ttu-id="b5c4e-131">在配置帐户权限后，请继续进行以下这些步骤。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-131">After account permissions are configured, continue with these steps.</span></span>  
  
#### <a name="grant-the-sql-server-agent-account-administrator-permission-on-ssas"></a><span data-ttu-id="b5c4e-132">向 SQL Server 代理帐户授予对 SSAS 的管理员权限</span><span class="sxs-lookup"><span data-stu-id="b5c4e-132">Grant the SQL Server Agent account administrator permission on SSAS</span></span>  
  
1.  <span data-ttu-id="b5c4e-133">使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]连接到远程 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-133">Using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], connect to the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
2.  <span data-ttu-id="b5c4e-134">右键单击服务器名称，单击“属性”，然后单击“安全”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="b5c4e-134">Right-click the server name, click P**roperties**, and then click **Security**.</span></span>  
  
3.  <span data-ttu-id="b5c4e-135">单击“添加” \*\*\*\* 以添加 SQL Server 代理帐户。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-135">Click **Add** to add the SQL Server Agent account.</span></span>  
  
#### <a name="create-the-job"></a><span data-ttu-id="b5c4e-136">创建作业</span><span class="sxs-lookup"><span data-stu-id="b5c4e-136">Create the Job</span></span>  
  
1.  <span data-ttu-id="b5c4e-137">在 Management Studio 中，连接到本地数据库引擎实例。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-137">In Management Studio, connect to the local Database Engine instance.</span></span> <span data-ttu-id="b5c4e-138">SQL Server 代理是对象资源管理器中的最后一项。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-138">SQL Server Agent is the last item in Object Explorer.</span></span> <span data-ttu-id="b5c4e-139">必要时，请启动该服务。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-139">If necessary, start the service.</span></span>  
  
2.  <span data-ttu-id="b5c4e-140">右键单击“作业”，单击“新建作业”，然后输入名称。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="b5c4e-140">Right-click **Job**s, click **New Job** and then enter a name.</span></span>  
  
3.  <span data-ttu-id="b5c4e-141">在“步骤”中，单击“新建” \*\*\*\* ，然后输入名称。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-141">In Steps, click **New** and then enter a name.</span></span>  
  
4.  <span data-ttu-id="b5c4e-142">在“类型”中，选择“SQL Server Analysis Services 命令” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-142">In Type, choose **SQL Server Analysis Services Command**.</span></span>  
  
5.  <span data-ttu-id="b5c4e-143">在“服务器”中，输入远程 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-143">In Server, enter the name of the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
6.  <span data-ttu-id="b5c4e-144">在“命令”中，粘贴用于处理数据库的 XMLA 命令。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-144">In Command, paste the XMLA command for processing the database.</span></span> <span data-ttu-id="b5c4e-145">这是在按需远程处理的验证步骤中生成的 XMLA 脚本。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-145">This is the XMLA script that you generated in the verification step for on-demand remote processing.</span></span> <span data-ttu-id="b5c4e-146">单击 **“确定”** 保存作业。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-146">Click **OK** to save the job.</span></span>  
  
#### <a name="start-sql-server-profiler"></a><span data-ttu-id="b5c4e-147">启动 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="b5c4e-147">Start SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="b5c4e-148">在远程计算机上，启动 SQL Server Profiler。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-148">On the remote computer, start SQL Server Profiler.</span></span> <span data-ttu-id="b5c4e-149">连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例，然后单击“运行” \*\*\*\* 以使用默认事件启动跟踪。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-149">Connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, and click **Run** to start the trace using the default events.</span></span>  
  
     <span data-ttu-id="b5c4e-150">您将使用 SQL Server Profiler 监视所发生的处理事件。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-150">You will use SQL Server Profiler to monitor the processing events as they occur.</span></span>  
  
2.  <span data-ttu-id="b5c4e-151">或者，可设置跟踪属性，将跟踪内容发送到数据库内的文件或表中。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-151">Optionally, you can set trace properties to send the trace to a file or table in a database.</span></span>  
  
#### <a name="run-the-job"></a><span data-ttu-id="b5c4e-152">运行作业</span><span class="sxs-lookup"><span data-stu-id="b5c4e-152">Run the job</span></span>  
  
1.  <span data-ttu-id="b5c4e-153">在用于运行作业的计算机上，确认作业可执行基本操作。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-153">On the computer used to run the job, verify that the job can perform the basic operation.</span></span> <span data-ttu-id="b5c4e-154">在“对象资源管理器”中的“SQL Server 代理”下，展开“作业”，右键单击刚刚创建的作业，然后单击“作业开始步骤”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="b5c4e-154">In Object Explorer, under SQL Server Agent, expand **Jobs**, right-click the job you just created, and click **Start Job at Step**.</span></span> <span data-ttu-id="b5c4e-155">随后立即启动该作业。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-155">The job starts immediately.</span></span> <span data-ttu-id="b5c4e-156">可在 SQL Server Profiler 中监视进度。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-156">You can monitor progress in SQL Server Profiler.</span></span>  
  
2.  <span data-ttu-id="b5c4e-157">最后一步，修改该作业，使其按您定义的计划运行，并添加管理作业所需的任何警报或通知。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-157">As a final step, modify the job to run on a schedule that you define, adding any alerts or notifications necessary to administer the job.</span></span> <span data-ttu-id="b5c4e-158">可能还要细化处理脚本，或在作业中创建多个步骤以独立处理各个对象。</span><span class="sxs-lookup"><span data-stu-id="b5c4e-158">You might also want to refine the processing script, or create multiple steps in the job to process objects independently.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c4e-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5c4e-159">See Also</span></span>  
 <span data-ttu-id="b5c4e-160">[SQL Server 代理组件](../../ssms/agent/sql-server-agent.md#Components) </span><span class="sxs-lookup"><span data-stu-id="b5c4e-160">[SQL Server Agent Components](../../ssms/agent/sql-server-agent.md#Components) </span></span>  
 <span data-ttu-id="b5c4e-161">[用 SQL Server 代理计划 SSAS 管理任务](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md) </span><span class="sxs-lookup"><span data-stu-id="b5c4e-161">[Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md) </span></span>  
 <span data-ttu-id="b5c4e-162">[批处理 &#40;Analysis Services&#41;](batch-processing-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="b5c4e-162">[Batch Processing &#40;Analysis Services&#41;](batch-processing-analysis-services.md) </span></span>  
 <span data-ttu-id="b5c4e-163">[多维模型对象处理](processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="b5c4e-163">[Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md) </span></span>  
 [<span data-ttu-id="b5c4e-164">处理对象 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="b5c4e-164">Processing Objects &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)  
  
  
