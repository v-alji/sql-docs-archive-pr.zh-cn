---
title: 使用对象资源管理器执行按需评估 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: ee6d3b79-18bc-49d3-8a1d-0c0905b990f0
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e32876978ac462af361986d84e11ef3dc0f278e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577151"
---
# <a name="perform-an-on-demand-evaluation-by-using-object-explorer"></a><span data-ttu-id="aea64-102">通过使用对象资源管理器执行按需评估</span><span class="sxs-lookup"><span data-stu-id="aea64-102">Perform an On-Demand Evaluation by Using Object Explorer</span></span>
  <span data-ttu-id="aea64-103">在此任务中，您将使用对象资源管理器为 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 的单个实例上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]执行最佳实践策略的按需评估。</span><span class="sxs-lookup"><span data-stu-id="aea64-103">In this task, you will use Object Explorer to perform an on-demand evaluation of best practices policies for the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] on a single instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aea64-104">您还可以通过已注册的服务器评估单个实例上的策略。</span><span class="sxs-lookup"><span data-stu-id="aea64-104">You can also evaluate policies on a single instance through Registered Servers.</span></span> <span data-ttu-id="aea64-105">有关详细信息，请参阅[使用已注册的服务器执行按需评估](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="aea64-105">For more information, see [Perform an On-Demand Evaluation by Using Registered Servers](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="aea64-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="aea64-106">Prerequisites</span></span>  
 <span data-ttu-id="aea64-107">本课基于 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="aea64-107">This lesson is based on the version of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aea64-108">若要针对正在运行的实例执行最佳实践策略的按需评估 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] ，您必须使用主题使用[已注册的服务器执行按需评估](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)主题中所述的过程。</span><span class="sxs-lookup"><span data-stu-id="aea64-108">To perform an on-demand evaluation of best practices policies against instances that are running [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], you must use the procedure in the topic [Perform an On-Demand Evaluation by Using Registered Servers](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).</span></span>  
  
### <a name="to-perform-an-on-demand-evaluation-by-using-object-explorer"></a><span data-ttu-id="aea64-109">通过使用对象资源管理器执行按需评估</span><span class="sxs-lookup"><span data-stu-id="aea64-109">To perform an on-demand evaluation by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="aea64-110">启动 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]，然后连接到[!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="aea64-110">Start [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], and then connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="aea64-111">在对象资源管理器中，依次展开 "**管理**"、"**策略管理**"，右键单击 "**策略**"，然后单击 "**评估**"。</span><span class="sxs-lookup"><span data-stu-id="aea64-111">In Object Explorer, expand **Management**, expand **Policy Management**, right-click **Policies**, and then click **Evaluate**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aea64-112">默认情况下，本地实例用作策略的源。</span><span class="sxs-lookup"><span data-stu-id="aea64-112">By default, the local instance is used as the source of the policies.</span></span> <span data-ttu-id="aea64-113">如果您以前导入了最佳实践策略，将会列出它们，一起还会列出您已创建的任何其他策略。</span><span class="sxs-lookup"><span data-stu-id="aea64-113">If you have previously imported best practices policies, they will be listed, together with any other policies that you have created.</span></span> <span data-ttu-id="aea64-114">你可以选择任何导入的最佳实践策略，然后单击 "**评估**"。</span><span class="sxs-lookup"><span data-stu-id="aea64-114">You can select any of the imported best practices policies, and then click **Evaluate**.</span></span> <span data-ttu-id="aea64-115">如果您尚未导入最佳实践策略，则继续此过程。</span><span class="sxs-lookup"><span data-stu-id="aea64-115">If you have not imported the best practices policies, continue with this procedure.</span></span>  
  
3.  <span data-ttu-id="aea64-116">在 "**评估策略**" 对话框中，在 "**源**" 框旁，单击省略号 (**...**) "按钮。</span><span class="sxs-lookup"><span data-stu-id="aea64-116">In the **Evaluate Policies** dialog box, next to the **Source** box, click the ellipsis (**...**) button.</span></span>  
  
4.  <span data-ttu-id="aea64-117">在 "**选择源**" 对话框中，可以选择 "**文件**" 或 "**服务器**" 作为要评估的策略文件的源。</span><span class="sxs-lookup"><span data-stu-id="aea64-117">In the **Select Source** dialog box, you can select either **Files** or **Server** as the source of the policy files to evaluate.</span></span> <span data-ttu-id="aea64-118">如果单击 "**服务器**"，则可以对以前导入到本地或远程服务器上基于策略的管理的任何最佳实践策略执行按需评估。</span><span class="sxs-lookup"><span data-stu-id="aea64-118">If you click **Server**, you can perform an on-demand evaluation of any best practices policies that were previously imported into Policy-Based Management on a local or remote server.</span></span> <span data-ttu-id="aea64-119">在本教程中，您将单击 "**文件**"，然后选择您要评估的各个策略文件。</span><span class="sxs-lookup"><span data-stu-id="aea64-119">In this tutorial, you will click **Files**, and then select the individual policy files that you want to evaluate.</span></span> <span data-ttu-id="aea64-120">要实现这一点，请执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="aea64-120">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="aea64-121">单击 "**文件**"。</span><span class="sxs-lookup"><span data-stu-id="aea64-121">Click **Files**.</span></span>  
  
    2.  <span data-ttu-id="aea64-122">在 "**文件**" 旁，单击省略号 (**...**) "按钮。</span><span class="sxs-lookup"><span data-stu-id="aea64-122">Next to **Files**, click the ellipsis (**...**) button.</span></span>  
  
    3.  <span data-ttu-id="aea64-123">在 "**选择策略**" 对话框中，浏览到包含最佳实践策略的以下文件夹：</span><span class="sxs-lookup"><span data-stu-id="aea64-123">In the **Select Policy** dialog box, browse to the following folder, which contains the best practices policies:</span></span>  
  
         <span data-ttu-id="aea64-124">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span><span class="sxs-lookup"><span data-stu-id="aea64-124">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="aea64-125">文件路径可能各不相同，具体取决于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 程序文件的安装位置、运行的操作系统是 32 位还是 64 位以及语言标识符。</span><span class="sxs-lookup"><span data-stu-id="aea64-125">The file path may vary, depending on where you installed the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] program files, whether you are running a 32-bit or 64-bit operating system, and the language identifier.</span></span>  
  
    4.  <span data-ttu-id="aea64-126">选择要评估的一个或多个 .xml 策略文件，然后单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="aea64-126">Select one or more .xml policy files to evaluate, and then click **Open**.</span></span>  
  
         <span data-ttu-id="aea64-127">所选文件的列表将显示在 "**文件**" 框中。</span><span class="sxs-lookup"><span data-stu-id="aea64-127">The list of selected files appears in the **Files** box.</span></span>  
  
    5.  <span data-ttu-id="aea64-128">在 "**选择源**" 对话框中，单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="aea64-128">In the **Select Source** dialog box, click **OK**.</span></span>  
  
    6.  <span data-ttu-id="aea64-129">如果显示 "**加载策略**" 对话框，则单击 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="aea64-129">If the **Loading Policies** dialog box appears, click **Close**.</span></span>  
  
     <span data-ttu-id="aea64-130">选择的策略将在 "**策略选择**" 页上列出。</span><span class="sxs-lookup"><span data-stu-id="aea64-130">The policies that you selected are listed on the **Policy Selection** page.</span></span> <span data-ttu-id="aea64-131">请注意，某一策略旁的警告图标指示该策略包含脚本。</span><span class="sxs-lookup"><span data-stu-id="aea64-131">Be aware that a warning icon next to a policy indicates that the policy contains scripts.</span></span>  
  
5.  <span data-ttu-id="aea64-132">单击 "**评估**" 以评估策略。</span><span class="sxs-lookup"><span data-stu-id="aea64-132">Click **Evaluate** to evaluate the policies.</span></span>  
  
     <span data-ttu-id="aea64-133">在**结果**表中，将列出每个策略的结果。</span><span class="sxs-lookup"><span data-stu-id="aea64-133">In the **Results** table, the results for each policy are listed.</span></span> <span data-ttu-id="aea64-134">红色的“x”图标指示不符合策略。</span><span class="sxs-lookup"><span data-stu-id="aea64-134">A red "x" icon indicates that policy compliance failed.</span></span>  
  
6.  <span data-ttu-id="aea64-135">对于某些策略失败，基于策略的管理使您能够立即对目标强制策略符合。</span><span class="sxs-lookup"><span data-stu-id="aea64-135">For some policy failures, Policy-Based Management enables you to immediately enforce policy compliance on the target.</span></span> <span data-ttu-id="aea64-136">对于此类失败，在失败的策略旁将出现一个复选框。</span><span class="sxs-lookup"><span data-stu-id="aea64-136">For such failures, a check box will appear next to the failed policy.</span></span> <span data-ttu-id="aea64-137">如果选中此复选框，"**应用**" 按钮将变为可用。</span><span class="sxs-lookup"><span data-stu-id="aea64-137">If you select the check box, the **Apply** button becomes available.</span></span> <span data-ttu-id="aea64-138">单击 "**应用**" 时，将在目标实例上自动更新不符合设置。</span><span class="sxs-lookup"><span data-stu-id="aea64-138">When you click **Apply**, the noncompliant setting will be automatically updated on the target instance.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="aea64-139">在自动更新目标实例前，请确保您完全理解该策略设置。</span><span class="sxs-lookup"><span data-stu-id="aea64-139">Make sure that you fully understand the policy setting before automatically updating a target instance.</span></span> <span data-ttu-id="aea64-140">建议你在选中一个或多个复选框后，单击 "**脚本**"，然后选择一个输出位置，以便可以在 [!INCLUDE[tsql](../includes/tsql-md.md)] 应用更改之前查看基础代码。</span><span class="sxs-lookup"><span data-stu-id="aea64-140">We recommend that after you select one or more check boxes, you click **Script**, and choose an output location so that you can review the underlying [!INCLUDE[tsql](../includes/tsql-md.md)] code before you apply the changes.</span></span>  
  
7.  <span data-ttu-id="aea64-141">若要查看某个策略的详细结果，请在 "**结果**" 表中单击该策略。</span><span class="sxs-lookup"><span data-stu-id="aea64-141">To view detailed results for a policy, click the policy in the **Results** table.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="aea64-142">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="aea64-142">Next Task in Lesson</span></span>  
 [<span data-ttu-id="aea64-143">通过使用已注册的服务器执行按需评估</span><span class="sxs-lookup"><span data-stu-id="aea64-143">Perform an On-Demand Evaluation by Using Registered Servers</span></span>](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)  
  
  
