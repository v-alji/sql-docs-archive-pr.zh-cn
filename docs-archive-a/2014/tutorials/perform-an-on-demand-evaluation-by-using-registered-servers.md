---
title: 使用已注册的服务器执行按需评估 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: c14034ef-6e0b-4df5-8072-bfb8d90b3172
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a3a06efaabff7e94e5b560744f0e1c739831042a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577152"
---
# <a name="perform-an-on-demand-evaluation-by-using-registered-servers"></a><span data-ttu-id="86586-102">通过使用已注册的服务器执行按需评估</span><span class="sxs-lookup"><span data-stu-id="86586-102">Perform an On-Demand Evaluation by Using Registered Servers</span></span>

  <span data-ttu-id="86586-103">您可以通过使用已注册的服务器对 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的一个或多个实例执行最佳实践策略的按需评估。</span><span class="sxs-lookup"><span data-stu-id="86586-103">You can perform an on-demand evaluation of best practices policies against one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using Registered Servers.</span></span> <span data-ttu-id="86586-104">您可以使用本地服务器组或中央管理服务器。</span><span class="sxs-lookup"><span data-stu-id="86586-104">You can use either local server groups or a central management server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="86586-105">您可以对运行 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] 或者 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的更高版本的服务器组成员执行最佳实践策略的按需评估。</span><span class="sxs-lookup"><span data-stu-id="86586-105">You can perform an on-demand evaluation of best practices policies against server group members that are running [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] or a later version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="86586-106">但是，如果存在引用在 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] 或 [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)] 中不支持的策略的一些属性，则您可能会接收异常错误。</span><span class="sxs-lookup"><span data-stu-id="86586-106">However, you may receive an exception error if there are some properties that are referred to by a policy that are not supported in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] or [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="86586-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="86586-107">Prerequisites</span></span>  
 <span data-ttu-id="86586-108">要执行此任务，您必须在已注册的服务器中已配置一个或多个服务器注册。</span><span class="sxs-lookup"><span data-stu-id="86586-108">To perform this task, you must have configured one or more server registrations in Registered Servers.</span></span> <span data-ttu-id="86586-109">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="86586-109">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="86586-110">创建或编辑服务器组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="86586-110">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   <span data-ttu-id="86586-111">[&#40;SQL Server Management Studio&#41;注册连接的服务器](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="86586-111">[Register a Connected Server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).</span></span>  
  
-   [<span data-ttu-id="86586-112">创建中央管理服务器和服务器组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="86586-112">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-evaluate-best-practices-policies-against-a-server-group"></a><span data-ttu-id="86586-113">对于服务器组执行最佳实践策略</span><span class="sxs-lookup"><span data-stu-id="86586-113">To evaluate best practices policies against a server group</span></span>  
  
1.  <span data-ttu-id="86586-114">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中的 **“视图”** 菜单上，单击 **“已注册的服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="86586-114">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="86586-115">展开 "**数据库引擎**"，然后展开 "**本地服务器组**" 或 "**中央管理服务器**"，具体取决于你的配置。</span><span class="sxs-lookup"><span data-stu-id="86586-115">Expand **Database Engine**, and then expand either **Local Server Groups**, or **Central Management Servers**, depending on your configuration.</span></span>  
  
3.  <span data-ttu-id="86586-116">执行下列任一操作：</span><span class="sxs-lookup"><span data-stu-id="86586-116">Do either of the following:</span></span>  
  
    -   <span data-ttu-id="86586-117">若要针对本地服务器组或中央管理服务器管理的所有服务器评估策略，请右键单击本地服务器组名称或中央管理服务器名称，然后单击 "**评估策略**"。</span><span class="sxs-lookup"><span data-stu-id="86586-117">To evaluate the policies against all servers that are managed by the local server group or the central management server, right-click the local server group name or the central management server name, and then click **Evaluate Policies**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="86586-118">在通过中央管理服务器评估策略时，不对中央管理服务器本身评估策略。</span><span class="sxs-lookup"><span data-stu-id="86586-118">When you evaluate policies through a central management server, the policies are not evaluated against the central management server itself.</span></span>  
  
    -   <span data-ttu-id="86586-119">若要针对特定服务器或服务器组评估策略，请展开 "**本地服务器组**" 或 "中央管理服务器名称"，右键单击要评估策略的服务器或服务器组，然后单击 "**评估策略**"。</span><span class="sxs-lookup"><span data-stu-id="86586-119">To evaluate the policies against a specific server or server group, expand **Local Server Groups** or the central management server name, right-click the server or server group that you want to evaluate policies against, and then click **Evaluate Policies**.</span></span>  
  
4.  <span data-ttu-id="86586-120">在 "**评估策略**" 对话框中，在 "**源**" 框旁，单击省略号 (**...**) "按钮。</span><span class="sxs-lookup"><span data-stu-id="86586-120">In the **Evaluate Policies** dialog box, next to the **Source** box, click the ellipsis (**...**) button.</span></span>  
  
5.  <span data-ttu-id="86586-121">在 "**选择源**" 对话框中，可以选择 "**文件**" 或 "**服务器**" 作为要评估的策略文件的源。</span><span class="sxs-lookup"><span data-stu-id="86586-121">In the **Select Source** dialog box, you can select either **Files** or **Server** as the source of the policy files to evaluate.</span></span> <span data-ttu-id="86586-122">如果单击 "**服务器**"，则可以对以前导入到本地或远程服务器上基于策略的管理的任何最佳实践策略执行按需评估。</span><span class="sxs-lookup"><span data-stu-id="86586-122">If you click **Server**, you can perform an on-demand evaluation of any best practices policies that were previously imported into Policy-Based Management on a local or remote server.</span></span> <span data-ttu-id="86586-123">在本教程中，您将单击 "**文件**"，然后选择您要评估的各个策略文件。</span><span class="sxs-lookup"><span data-stu-id="86586-123">In this tutorial, you will click **Files**, and then select the individual policy files that you want to evaluate.</span></span> <span data-ttu-id="86586-124">要实现这一点，请执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="86586-124">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="86586-125">单击 "**文件**"。</span><span class="sxs-lookup"><span data-stu-id="86586-125">Click **Files**.</span></span>  
  
    2.  <span data-ttu-id="86586-126">在 "**文件**" 旁，单击省略号 (**...**) "按钮。</span><span class="sxs-lookup"><span data-stu-id="86586-126">Next to **Files**, click the ellipsis (**...**) button.</span></span>  
  
    3.  <span data-ttu-id="86586-127">选择要评估的一个或多个 .xml 策略文件，然后单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="86586-127">Select one or more .xml policy files to evaluate, and then click **Open**.</span></span>  
  
         <span data-ttu-id="86586-128">所选文件的列表将显示在 "**文件**" 框中。</span><span class="sxs-lookup"><span data-stu-id="86586-128">The list of selected files appears in the **Files** box.</span></span>  
  
    4.  <span data-ttu-id="86586-129">在 "**选择源**" 对话框中，单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="86586-129">In the **Select Source** dialog box, click **OK**.</span></span>  
  
    5.  <span data-ttu-id="86586-130">如果显示 "**加载策略**" 对话框，则单击 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="86586-130">If the **Loading Policies** dialog box appears, click **Close**.</span></span>  
  
     <span data-ttu-id="86586-131">选择的策略将在 "**策略选择**" 页上列出。</span><span class="sxs-lookup"><span data-stu-id="86586-131">The policies that you selected are listed on the **Policy Selection** page.</span></span> <span data-ttu-id="86586-132">请注意，某一策略旁的警告图标指示该策略包含脚本。</span><span class="sxs-lookup"><span data-stu-id="86586-132">Be aware that a warning icon next to a policy indicates that the policy contains scripts.</span></span>  
  
6.  <span data-ttu-id="86586-133">单击 "**评估**" 以评估策略。</span><span class="sxs-lookup"><span data-stu-id="86586-133">Click **Evaluate** to evaluate the policies.</span></span>  
  
7.  <span data-ttu-id="86586-134">对于某些策略失败，基于策略的管理使您能够立即对目标强制策略符合。</span><span class="sxs-lookup"><span data-stu-id="86586-134">For some policy failures, Policy-Based Management enables you to immediately enforce policy compliance on the target.</span></span> <span data-ttu-id="86586-135">对于此类失败，在失败的策略旁将出现一个复选框。</span><span class="sxs-lookup"><span data-stu-id="86586-135">For such failures, a check box will appear next to the failed policy.</span></span> <span data-ttu-id="86586-136">如果选中该复选框，或单击具有失败策略的行，则复选框将出现在 "**目标详细信息**" 窗格中的 "目标详细信息" 窗格中。</span><span class="sxs-lookup"><span data-stu-id="86586-136">If you select the check box, or click the row with the failed policy, check boxes appear in the **Target details** pane next to the target instances that failed the evaluation.</span></span> <span data-ttu-id="86586-137">如果选中任何复选框，"**应用**" 按钮将变为可用。</span><span class="sxs-lookup"><span data-stu-id="86586-137">If any of the check boxes are selected, the **Apply** button becomes available.</span></span> <span data-ttu-id="86586-138">单击 "**应用**" 时，不符合性设置将在你选择的目标实例上自动更新。</span><span class="sxs-lookup"><span data-stu-id="86586-138">When you click **Apply**, the noncompliant setting will be automatically updated on the target instances that you selected.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="86586-139">在自动更新目标实例前，请确保您完全理解该策略设置。</span><span class="sxs-lookup"><span data-stu-id="86586-139">Make sure that you fully understand the policy setting before automatically updating a target instance.</span></span> <span data-ttu-id="86586-140">建议你在选中一个或多个复选框后，单击 "**脚本**"，然后选择一个输出位置，以便可以在 [!INCLUDE[tsql](../includes/tsql-md.md)] 应用更改之前查看基础代码。</span><span class="sxs-lookup"><span data-stu-id="86586-140">We recommend that after you select one or more check boxes, you click **Script**, and choose an output location so that you can review the underlying [!INCLUDE[tsql](../includes/tsql-md.md)] code before you apply the changes.</span></span>  
  
8.  <span data-ttu-id="86586-141">若要查看某个策略的详细结果，请在 "**结果**" 表中单击该策略。</span><span class="sxs-lookup"><span data-stu-id="86586-141">To view detailed results for a policy, click the policy in the **Results** table.</span></span> <span data-ttu-id="86586-142">"**目标详细信息**" 表显示每个实例的详细信息。</span><span class="sxs-lookup"><span data-stu-id="86586-142">The **Target details** table shows the details for each instance.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="86586-143">下一课</span><span class="sxs-lookup"><span data-stu-id="86586-143">Next Lesson</span></span>  
 [<span data-ttu-id="86586-144">第 2 课：定期评估最佳做法策略</span><span class="sxs-lookup"><span data-stu-id="86586-144">Lesson 2: Evaluate Best Practices Policies on a Scheduled Basis</span></span>](../../2014/tutorials/lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis.md)  
  
## <a name="see-also"></a><span data-ttu-id="86586-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86586-145">See Also</span></span>  
 <span data-ttu-id="86586-146">[使用基于策略的管理来监视和强制实施最佳实践](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md) </span><span class="sxs-lookup"><span data-stu-id="86586-146">[Monitor and Enforce Best Practices by Using Policy-Based Management](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md) </span></span>  
 [<span data-ttu-id="86586-147">使用中央管理服务器管理多台服务器</span><span class="sxs-lookup"><span data-stu-id="86586-147">Administer Multiple Servers Using Central Management Servers</span></span>](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
