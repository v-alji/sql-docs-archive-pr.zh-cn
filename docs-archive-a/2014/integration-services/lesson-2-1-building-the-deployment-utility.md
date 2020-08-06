---
title: 步骤 1：生成部署实用工具 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1ff4dcff-89b3-4b99-a725-5f7963e98abf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3d32dcbf4bfcf9758dfe58803b75094d1807aa90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586811"
---
# <a name="step-1-building-the-deployment-utility"></a><span data-ttu-id="32a8b-102">步骤 1：生成部署实用工具</span><span class="sxs-lookup"><span data-stu-id="32a8b-102">Step 1: Building the Deployment Utility</span></span>
  <span data-ttu-id="32a8b-103">在此任务中，将为 Deployment Tutorial 项目配置和生成部署实用工具。</span><span class="sxs-lookup"><span data-stu-id="32a8b-103">In this task, you will configure and build a deployment utility for the Deployment Tutorial project.</span></span>  
  
 <span data-ttu-id="32a8b-104">必须先修改 Deployment Tutorial 项目的属性，才能生成部署实用工具。</span><span class="sxs-lookup"><span data-stu-id="32a8b-104">Before you can build the deployment utility, you must modify the properties of the Deployment Tutorial project.</span></span> <span data-ttu-id="32a8b-105">使用“Deployment Tutorial 属性页”对话框配置这些属性。 </span><span class="sxs-lookup"><span data-stu-id="32a8b-105">You will use the **Deployment Tutorial Property Pages** dialog box to configure these properties.</span></span> <span data-ttu-id="32a8b-106">在此对话框中，您必须允许在部署期间更新配置，并指定生成进程将生成部署实用工具。</span><span class="sxs-lookup"><span data-stu-id="32a8b-106">In this dialog box, you must enable the ability to update configurations during deployment and specify that the build process generates a deployment utility.</span></span> <span data-ttu-id="32a8b-107">在设置属性后，将生成项目。</span><span class="sxs-lookup"><span data-stu-id="32a8b-107">After you set the properties, you will build the project.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="32a8b-108">提供了一组窗口，可以使用它们来调试包。</span><span class="sxs-lookup"><span data-stu-id="32a8b-108">provides a set of windows that you can use to debug packages.</span></span> <span data-ttu-id="32a8b-109">您可以查看错误、警告和信息性消息，在运行时跟踪包的状态，或查看生成进程的进度和结果。</span><span class="sxs-lookup"><span data-stu-id="32a8b-109">You can view error, warning, and information messages, track about the status of packages at run time, or view the progress and results of build processes.</span></span> <span data-ttu-id="32a8b-110">在本课中，将使用“输出”窗口查看生成部署实用工具的进度和结果。</span><span class="sxs-lookup"><span data-stu-id="32a8b-110">For this lesson, you will use the Output window to view the progress and results of building the deployment utility.</span></span>  
  
### <a name="to-set-the-deployment-utility-properties"></a><span data-ttu-id="32a8b-111">设置部署实用工具的属性</span><span class="sxs-lookup"><span data-stu-id="32a8b-111">To set the deployment utility properties</span></span>  
  
1.  <span data-ttu-id="32a8b-112">如果 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 尚未打开，请单击“开始”，依次指向“所有程序”和“Microsoft SQL Server”，再单击“Business Intelligence Development Studio”。    </span><span class="sxs-lookup"><span data-stu-id="32a8b-112">If [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **Business Intelligence Development Studio**.</span></span>  
  
2.  <span data-ttu-id="32a8b-113">在“文件”  菜单上，依次单击“打开”  、“项目/解决方案”  、“Deployment Tutorial”  文件夹，然后再次单击“打开”  ，最后双击“Deployment Tutorial.sln”  。</span><span class="sxs-lookup"><span data-stu-id="32a8b-113">On the **File** menu, click **Open**, click **Project/Solution**, click the **Deployment Tutorial** folder and click **Open**, and then double-click **Deployment Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="32a8b-114">在解决方案资源管理器中，右键单击“Deployment Tutorial”，再单击“属性”。 </span><span class="sxs-lookup"><span data-stu-id="32a8b-114">In Solution Explorer, right-click Deployment Tutorial and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="32a8b-115">在“Deployment Tutorial 属性页”  对话框中，展开“配置属性”，再单击“部署实用工具”。</span><span class="sxs-lookup"><span data-stu-id="32a8b-115">In the **Deployment Tutorial Property Pages** dialog box, expand Configuration Properties, and click Deployment Utility.</span></span>  
  
5.  <span data-ttu-id="32a8b-116">在 "**部署教程属性页**" 对话框的右窗格中，验证 `AllowConfigurationChanges` 是否将设置为 `true` ，将设置 `CreateDeploymentUtility` 为 `true` ，并选择性地更新的默认值 `DeploymentOutputPath` 。</span><span class="sxs-lookup"><span data-stu-id="32a8b-116">In the right pane of the **Deployment Tutorial Property Pages** dialog box, verify that `AllowConfigurationChanges` is set to `true`, set `CreateDeploymentUtility` to `true`, and optionally update the default value of `DeploymentOutputPath`.</span></span>  
  
6.  <span data-ttu-id="32a8b-117">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="32a8b-117">Click **OK**.</span></span>  
  
### <a name="to-build-the-deployment-utility"></a><span data-ttu-id="32a8b-118">生成部署实用工具</span><span class="sxs-lookup"><span data-stu-id="32a8b-118">To build the deployment utility</span></span>  
  
1.  <span data-ttu-id="32a8b-119">在解决方案资源管理器中，单击“Deployment Tutorial”  。</span><span class="sxs-lookup"><span data-stu-id="32a8b-119">In Solution Explorer, click **Deployment Tutorial**.</span></span>  
  
2.  <span data-ttu-id="32a8b-120">在“视图”  菜单上，单击“输出”  。</span><span class="sxs-lookup"><span data-stu-id="32a8b-120">On the **View** menu, click **Output**.</span></span> <span data-ttu-id="32a8b-121">默认情况下，“输出”窗口位于 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的左下角。</span><span class="sxs-lookup"><span data-stu-id="32a8b-121">By default, the Output window is located in the bottom left corner of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
3.  <span data-ttu-id="32a8b-122">在“生成”  菜单上，单击“生成 Deployment Tutorial”  。</span><span class="sxs-lookup"><span data-stu-id="32a8b-122">On the **Build** menu, click **Build Deployment Tutorial**.</span></span>  
  
4.  <span data-ttu-id="32a8b-123">在“输出”窗口中，验证以下信息：</span><span class="sxs-lookup"><span data-stu-id="32a8b-123">In the Output window, verify the following information:</span></span>  
  
     <span data-ttu-id="32a8b-124">已启动生成: SQL Integration Services 项目: 增量 ...</span><span class="sxs-lookup"><span data-stu-id="32a8b-124">Build started: SQL Integration Services project: Incremental ...</span></span>  
  
     <span data-ttu-id="32a8b-125">正在创建部署实用工具...</span><span class="sxs-lookup"><span data-stu-id="32a8b-125">Creating deployment utility...</span></span>  
  
     <span data-ttu-id="32a8b-126">已创建部署实用工具。</span><span class="sxs-lookup"><span data-stu-id="32a8b-126">Deployment Utility created.</span></span>  
  
     <span data-ttu-id="32a8b-127">生成完成 -- 0 个错误，0 个警告</span><span class="sxs-lookup"><span data-stu-id="32a8b-127">Build complete -- 0 errors, 0 warnings</span></span>  
  
     <span data-ttu-id="32a8b-128">========== 生成: 0 已成功，0 已失败，1 最新，0 已跳过 ==========</span><span class="sxs-lookup"><span data-stu-id="32a8b-128">========== Build: 0 succeeded, 0 failed, 1 up-to-date, 0 skipped ==========</span></span>  
  
5.  <span data-ttu-id="32a8b-129">在 **“文件”** 菜单中，单击 **“退出”** 。</span><span class="sxs-lookup"><span data-stu-id="32a8b-129">On the **File** menu, click **Exit**.</span></span> <span data-ttu-id="32a8b-130">如果提示保存对 Deployment Tutorial 的各项所做的更改，请单击“是”  。</span><span class="sxs-lookup"><span data-stu-id="32a8b-130">If prompted to save changes to Deployment Tutorial items, click **Yes**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="32a8b-131">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="32a8b-131">Next Task in Lesson</span></span>  
 [<span data-ttu-id="32a8b-132">步骤 2：验证部署捆绑</span><span class="sxs-lookup"><span data-stu-id="32a8b-132">Step 2: Verifying the Deployment Bundle</span></span>](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
<span data-ttu-id="32a8b-133">![Integration Services 图标 (小型) ](media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="32a8b-133">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="32a8b-134">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="32a8b-134">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="32a8b-135">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="32a8b-135">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="32a8b-136">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="32a8b-136">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a8b-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32a8b-137">See Also</span></span>  
 [<span data-ttu-id="32a8b-138">创建部署实用工具</span><span class="sxs-lookup"><span data-stu-id="32a8b-138">Create a Deployment Utility</span></span>](../../2014/integration-services/create-a-deployment-utility.md)  
  
  
