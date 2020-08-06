---
title: 将计划的策略部署到多个实例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: f551b8e8-3668-4ed4-852f-bae826254f4f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 30faf94c2033be43ac035517e58d5a18c0c68ab8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687387"
---
# <a name="deploy-scheduled-policies-to-multiple-instances"></a><span data-ttu-id="fc02d-102">将计划的策略部署到多个实例</span><span class="sxs-lookup"><span data-stu-id="fc02d-102">Deploy Scheduled Policies to Multiple Instances</span></span>
  <span data-ttu-id="fc02d-103">通过使用已注册的服务器，可以从一个集中位置将计划的策略部署到多个托管服务器。</span><span class="sxs-lookup"><span data-stu-id="fc02d-103">By using Registered Servers, you can deploy scheduled policies to managed servers from a central location.</span></span> <span data-ttu-id="fc02d-104">您可以从本地服务器组或中央管理服务器部署计划的策略。</span><span class="sxs-lookup"><span data-stu-id="fc02d-104">You can deploy scheduled policies from either a local server group, or from a Central Management Server.</span></span>  
  
 <span data-ttu-id="fc02d-105">在本任务中，您将执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="fc02d-105">In this task, you will do the following:</span></span>  
  
1.  <span data-ttu-id="fc02d-106">将您在前一个任务中计划的策略导出到某个文件夹。</span><span class="sxs-lookup"><span data-stu-id="fc02d-106">Export the policies that you scheduled in the previous task to a folder.</span></span>  
  
2.  <span data-ttu-id="fc02d-107">将计划的政策部署到通过已注册服务管理的目标实例。</span><span class="sxs-lookup"><span data-stu-id="fc02d-107">Deploy the scheduled policies to target instances that are managed through Registered Servers.</span></span>  
  
 <span data-ttu-id="fc02d-108">您将在完成本课程先前任务的计算机上执行这些任务。</span><span class="sxs-lookup"><span data-stu-id="fc02d-108">You will perform these tasks on the computer where you completed the previous tasks in this lesson.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fc02d-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="fc02d-109">Prerequisites</span></span>  
 <span data-ttu-id="fc02d-110">此任务具有以下必备条件：</span><span class="sxs-lookup"><span data-stu-id="fc02d-110">This task has the following prerequisites:</span></span>  
  
-   <span data-ttu-id="fc02d-111">您必须完成了本课程中的先前任务。</span><span class="sxs-lookup"><span data-stu-id="fc02d-111">You must have completed the previous tasks in this lesson.</span></span>  
  
-   <span data-ttu-id="fc02d-112">您要在其中部署计划策略的实例必须运行于 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 或更高版本上。</span><span class="sxs-lookup"><span data-stu-id="fc02d-112">The instances where you want to deploy the scheduled policies must be running [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] or a later version.</span></span> <span data-ttu-id="fc02d-113">自动过程要求在本地存储策略，但早于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 版本不支持此功能。</span><span class="sxs-lookup"><span data-stu-id="fc02d-113">Automation requires the policies to be stored locally, which is not supported on versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
-   <span data-ttu-id="fc02d-114">要在其中部署计划策略的服务器必须在 "**本地服务器组**" 或 "**中央管理服务器**" 节点的已注册服务器中注册。</span><span class="sxs-lookup"><span data-stu-id="fc02d-114">The servers where you want to deploy the scheduled policies must be registered in Registered Servers in either the **Local Server Groups** or the **Central Management Servers** node.</span></span> <span data-ttu-id="fc02d-115">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="fc02d-115">For more information, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="fc02d-116">创建或编辑服务器组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="fc02d-116">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
    -   <span data-ttu-id="fc02d-117">[&#40;SQL Server Management Studio&#41;注册连接的服务器](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="fc02d-117">[Register a Connected Server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).</span></span>  
  
    -   [<span data-ttu-id="fc02d-118">创建中央管理服务器和服务器组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="fc02d-118">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-export-the-scheduled-policies-as-xml-files"></a><span data-ttu-id="fc02d-119">将计划策略导出为 .xml 文件</span><span class="sxs-lookup"><span data-stu-id="fc02d-119">To export the scheduled policies as .xml files</span></span>  
  
1.  <span data-ttu-id="fc02d-120">在上一个任务中配置了计划策略的服务器上，展开 "**管理**"，再展开 "**策略管理**"，然后单击 "**策略**"。</span><span class="sxs-lookup"><span data-stu-id="fc02d-120">On the server where you configured scheduled policies in the previous task, expand **Management**, expand **Policy Management**, and then click **Policies**.</span></span>  
  
2.  <span data-ttu-id="fc02d-121">在“视图”\*\*\*\* 菜单中，单击“对象资源管理器详细信息”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc02d-121">On the **View** menu, click **Object Explorer Details**.</span></span>  
  
3.  <span data-ttu-id="fc02d-122">在 "**对象资源管理器详细信息**" 窗格中，选择要通过已注册的服务器部署到其他服务器的所有计划的最佳实践策略。</span><span class="sxs-lookup"><span data-stu-id="fc02d-122">In the **Object Explorer Details** pane, select all the scheduled best practices policies that you want to deploy to other servers through Registered Servers.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc02d-123">您可以单击 "**类别**" 标题以按类别对策略进行排序。</span><span class="sxs-lookup"><span data-stu-id="fc02d-123">You can click the **Category** heading to sort the policies by category.</span></span>  
  
4.  <span data-ttu-id="fc02d-124">右键单击所选内容，然后单击 "**导出策略**"。</span><span class="sxs-lookup"><span data-stu-id="fc02d-124">Right-click the selection, and then click **Export Policy**.</span></span>  
  
5.  <span data-ttu-id="fc02d-125">如果已选择要导出的多个策略，请在 "**查找文件夹**" 对话框中选择目标文件夹，或创建新文件夹。</span><span class="sxs-lookup"><span data-stu-id="fc02d-125">If you selected multiple policies to export, in the **Browse For Folder** dialog box, select a destination folder, or create a new folder.</span></span> <span data-ttu-id="fc02d-126">在本课中，请创建一个路径为**c：\ Scheduled_BP_Policies**的新文件夹，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="fc02d-126">For this lesson, create a new folder with the path **C:\Scheduled_BP_Policies**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="fc02d-127">如果仅选择了一个要导出的策略，请在 "**导出策略**" 对话框中创建一个路径为**c：\ Scheduled_BP_Policies**的新文件夹，单击 "**打开**"，然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="fc02d-127">If you only selected one policy to export, in the **Export Policy** dialog box, create a new folder with the path **C:\Scheduled_BP_Policies**, click **Open**, and then click **Save**.</span></span>  
  
     <span data-ttu-id="fc02d-128">将在此文件夹位置中创建 .xml 策略文件。</span><span class="sxs-lookup"><span data-stu-id="fc02d-128">The .xml policy files are created in the folder location.</span></span>  
  
### <a name="to-deploy-the-scheduled-policies-to-servers-that-are-managed-through-registered-servers"></a><span data-ttu-id="fc02d-129">将计划的政策部署到通过已注册服务管理的服务器</span><span class="sxs-lookup"><span data-stu-id="fc02d-129">To deploy the scheduled policies to servers that are managed through Registered Servers</span></span>  
  
1.  <span data-ttu-id="fc02d-130">在“视图”菜单上，单击“已注册的服务器”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fc02d-130">On the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="fc02d-131">展开 "**数据库引擎**"，展开 "**本地服务器组**" 或 "**中央管理服务器**"，右键单击要向其部署策略的节点，然后单击 "**导入策略**"。</span><span class="sxs-lookup"><span data-stu-id="fc02d-131">Expand **Database Engine**, expand either **Local Server Groups** or **Central Management Servers**, right-click the node that you want to deploy the policies to, and then click **Import Policies**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc02d-132">如果右键单击 "**本地服务器组**" 或 "中央管理服务器"，则会将策略部署到所有托管服务器。</span><span class="sxs-lookup"><span data-stu-id="fc02d-132">If you right-click **Local Server Groups** or the Central Management Server itself, the policies will be deployed to all managed servers.</span></span> <span data-ttu-id="fc02d-133">如果右键单击特定的服务器组，则策略将只部署到该组中的服务器。</span><span class="sxs-lookup"><span data-stu-id="fc02d-133">If you right-click a specific server group, the policies will only be deployed to servers in that group.</span></span> <span data-ttu-id="fc02d-134">如果右键单击特定的已注册服务器，则策略将只部署到该服务器。</span><span class="sxs-lookup"><span data-stu-id="fc02d-134">If you right-click a specific registered server, the policies will only be deployed to that server.</span></span>  
  
3.  <span data-ttu-id="fc02d-135">在 "**要导入的文件**" 旁，单击省略号按钮 " (**...** ") 。</span><span class="sxs-lookup"><span data-stu-id="fc02d-135">Next to **Files to import**, click the ellipsis button (**...**).</span></span>  
  
4.  <span data-ttu-id="fc02d-136">在 "**选择策略**" 对话框中，浏览到保存计划策略的文件夹位置。</span><span class="sxs-lookup"><span data-stu-id="fc02d-136">In the **Select Policy** dialog box, browse to the folder location where you saved the scheduled policies.</span></span> <span data-ttu-id="fc02d-137">对于本示例，浏览到位置**c：\ Scheduled_BP_Policies**。</span><span class="sxs-lookup"><span data-stu-id="fc02d-137">For this example, browse to the location **C:\Scheduled_BP_Policies**.</span></span>  
  
5.  <span data-ttu-id="fc02d-138">选择要导入到目标实例的策略，然后单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="fc02d-138">Select the policies that you want to import to the target instances, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="fc02d-139">在 "**导入**" 对话框的 "**策略状态**" 列表中，选择所需的策略状态。</span><span class="sxs-lookup"><span data-stu-id="fc02d-139">In the **Import** dialog box, in the **Policy state** list, select the desired policy state.</span></span> <span data-ttu-id="fc02d-140">您可以选择在导入时保留策略状态、启用或禁用策略。</span><span class="sxs-lookup"><span data-stu-id="fc02d-140">You can choose to preserve the policy state, enable, or disable the policies on import.</span></span> <span data-ttu-id="fc02d-141">请注意，必须启用策略才能根据计划运行它们。</span><span class="sxs-lookup"><span data-stu-id="fc02d-141">Be aware that the policies must be enabled to run on a schedule.</span></span>  
  
7.  <span data-ttu-id="fc02d-142">单击 **"确定"** 以将策略导入到所有目标实例。</span><span class="sxs-lookup"><span data-stu-id="fc02d-142">Click **OK** to import the policies to all the target instances.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc02d-143">如果出现任何错误，则 "**导入**" 对话框不会消失。</span><span class="sxs-lookup"><span data-stu-id="fc02d-143">If there are any errors, the **Import** dialog box does not disappear.</span></span> <span data-ttu-id="fc02d-144">单击 "**日志**" 页可查看消息。</span><span class="sxs-lookup"><span data-stu-id="fc02d-144">Click the **Log** page to review the messages.</span></span> <span data-ttu-id="fc02d-145">单击“取消”\*\*\*\* 以关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="fc02d-145">Click **Cancel** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="fc02d-146">若要查看目标实例中的策略，请连接到实例，打开对象资源管理器，展开 "**管理**"，然后展开 "**策略**"。</span><span class="sxs-lookup"><span data-stu-id="fc02d-146">To view the policies from a target instance, connect to the instance, open Object Explorer, expand **Management**, and then expand **Policies**.</span></span> <span data-ttu-id="fc02d-147">应会在 "**策略**" 节点中看到导入的策略。</span><span class="sxs-lookup"><span data-stu-id="fc02d-147">You should see the imported policies in the **Policies** node.</span></span> <span data-ttu-id="fc02d-148">如果您双击每个策略，则可以查看计划或更改设置。</span><span class="sxs-lookup"><span data-stu-id="fc02d-148">If you double-click each policy, you can view the schedule, or change the settings.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc02d-149">若要在运行计划的策略之后查看评估结果，请打开目标实例上的“策略历史记录”日志。</span><span class="sxs-lookup"><span data-stu-id="fc02d-149">To view the evaluation results after a scheduled policy runs, open the Policy History log on the target instance.</span></span> <span data-ttu-id="fc02d-150">若要打开日志，请右键单击 "**策略管理**"，然后单击 "**查看历史记录**"。</span><span class="sxs-lookup"><span data-stu-id="fc02d-150">To open the log, right-click **Policy Management**, and then click **View History**.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="fc02d-151">摘要</span><span class="sxs-lookup"><span data-stu-id="fc02d-151">Summary</span></span>  
 <span data-ttu-id="fc02d-152">本教程介绍了如何针对 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的一个或多个实例执行最佳实践策略的按需和计划评估。</span><span class="sxs-lookup"><span data-stu-id="fc02d-152">This tutorial has shown you how to perform both on-demand and scheduled evaluations of the best practices policies against one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="next"></a><span data-ttu-id="fc02d-153">下一步</span><span class="sxs-lookup"><span data-stu-id="fc02d-153">Next</span></span>  
 <span data-ttu-id="fc02d-154">现已学完了本教程。</span><span class="sxs-lookup"><span data-stu-id="fc02d-154">This tutorial is finished.</span></span> <span data-ttu-id="fc02d-155">若要返回到开始，请参阅[教程：使用基于策略的管理来评估最佳实践](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md)。</span><span class="sxs-lookup"><span data-stu-id="fc02d-155">To return to the start, see [Tutorial: Evaluating Best Practices by Using Policy-Based Management](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md).</span></span>  
  
 <span data-ttu-id="fc02d-156">若要查看教程的列表 [!INCLUDE[ssDE](../includes/ssde-md.md)] ，请单击[数据库引擎教程](../relational-databases/database-engine-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="fc02d-156">To see a list of [!INCLUDE[ssDE](../includes/ssde-md.md)] tutorials, click [Database Engine Tutorials](../relational-databases/database-engine-tutorials.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc02d-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc02d-157">See Also</span></span>  
 [<span data-ttu-id="fc02d-158">使用基于策略的管理来管理服务器</span><span class="sxs-lookup"><span data-stu-id="fc02d-158">Administer Servers by Using Policy-Based Management</span></span>](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
