---
title: 如何：调试自定义程序集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services], debugging
- debugging custom assemblies [Reporting Services]
- troubleshooting [Reporting Services], custom assemblies
ms.assetid: 3a3215b3-548c-4474-81ba-3a98dd3912bf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1b5f9f5a4595d59cce98da4f753422cd07529926
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690406"
---
# <a name="how-to-debug-custom-assemblies"></a><span data-ttu-id="96309-102">如何：调试自定义程序集</span><span class="sxs-lookup"><span data-stu-id="96309-102">How to: Debug Custom Assemblies</span></span>
  <span data-ttu-id="96309-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 提供了一些调试工具，这些工具可帮助您分析您的自定义程序集代码和查找其中的错误。</span><span class="sxs-lookup"><span data-stu-id="96309-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides several debugging tools that can help you analyze your custom assembly code and locate errors in it.</span></span> <span data-ttu-id="96309-104">要使用的最佳工具取决于您试图完成的任务。</span><span class="sxs-lookup"><span data-stu-id="96309-104">The best tool to use will depend on what you are trying to accomplish.</span></span> <span data-ttu-id="96309-105">此示例使用 [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="96309-105">This example uses [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)].</span></span>  
  
 <span data-ttu-id="96309-106">设计、开发和测试 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 自定义程序集的建议方式是创建包含您的测试报表和自定义程序集的解决方案。</span><span class="sxs-lookup"><span data-stu-id="96309-106">The recommended way to design, develop, and test custom assemblies for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is to create a solution that contains both your test reports and your custom assembly.</span></span>  
  
### <a name="to-debug-assemblies-using-a-single-instance-of-visual-studio"></a><span data-ttu-id="96309-107">使用 Visual Studio 的单个实例调试程序集</span><span class="sxs-lookup"><span data-stu-id="96309-107">To debug assemblies using a single instance of Visual Studio</span></span>  
  
1.  <span data-ttu-id="96309-108">使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 创建新的报表项目。</span><span class="sxs-lookup"><span data-stu-id="96309-108">Create a new report project using [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>  
  
     <span data-ttu-id="96309-109">创建报表项目时，[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 还会创建一个用以包含该项目的解决方案。</span><span class="sxs-lookup"><span data-stu-id="96309-109">At the time you create a report project, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] also creates a solution to contain it.</span></span>  
  
2.  <span data-ttu-id="96309-110">将一个新的类库项目添加到现有解决方案。</span><span class="sxs-lookup"><span data-stu-id="96309-110">Add a new Class Library project to the existing solution.</span></span> <span data-ttu-id="96309-111">请确保该报表项目设置为启动项目。</span><span class="sxs-lookup"><span data-stu-id="96309-111">Make sure that the report project is set as the startup project.</span></span> <span data-ttu-id="96309-112">有关如何实现此操作的详细信息，请参阅 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 文档。</span><span class="sxs-lookup"><span data-stu-id="96309-112">For more information about how to accomplish this, see your [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentation.</span></span>  
  
3.  <span data-ttu-id="96309-113">在解决方案资源管理器中，选择解决方案。</span><span class="sxs-lookup"><span data-stu-id="96309-113">In Solution Explorer, select the solution.</span></span>  
  
4.  <span data-ttu-id="96309-114">在“视图”菜单上，单击“属性页” 。</span><span class="sxs-lookup"><span data-stu-id="96309-114">On the **View** menu, click **Property Pages**.</span></span>  
  
     <span data-ttu-id="96309-115">“解决方案属性页”对话框会打开\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-115">The **Solution Property Pages** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="96309-116">在左窗格中，根据需要展开“自定义属性”，然后单击“项目依赖项”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-116">In the left pane, expand **Common Properties** if necessary, and click **Project Dependencies**.</span></span> <span data-ttu-id="96309-117">从“项目”下拉列表中选择相应的报表项目\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-117">Select the report project from the **Project** drop-down list.</span></span> <span data-ttu-id="96309-118">在“依赖于”列表中选择程序集项目\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-118">Select your assembly project in the **Depends On** list.</span></span>  
  
6.  <span data-ttu-id="96309-119">单击“确定”以保存更改，然后关闭“属性页”对话框\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-119">Click **OK** to save the changes, and close the **Property Pages** dialog.</span></span>  
  
7.  <span data-ttu-id="96309-120">在解决方案资源管理器中，选择您的自定义程序集项目。</span><span class="sxs-lookup"><span data-stu-id="96309-120">In Solution Explorer, select your custom assembly project.</span></span>  
  
8.  <span data-ttu-id="96309-121">在“视图”菜单上，单击“属性页” 。</span><span class="sxs-lookup"><span data-stu-id="96309-121">On the **View** menu, click **Property Pages**.</span></span>  
  
     <span data-ttu-id="96309-122">“项目属性页”对话框会打开\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-122">The **Project Property Pages** dialog box opens.</span></span>  
  
9. <span data-ttu-id="96309-123">单击“生成”选项卡（如果处于 C# 项目中）或“编译”选项卡（如果处于 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 项目中）\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-123">Click the **Build** tab if you're in a C# project or the **Compile** tab if you're in a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] project.</span></span>  
  
10. <span data-ttu-id="96309-124">在 "**生成** / **编译**" 页上，输入报表设计器文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="96309-124">On the **Build**/**Compile** page, enter the path to the Report Designer folder.</span></span> <span data-ttu-id="96309-125">默认情况下，在“输出路径”文本框中是 C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-125">By default, this is C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE) in the **Output Path** text box.</span></span> <span data-ttu-id="96309-126">这将在执行您的报表之前将自定义程序集的更新的版本直接生成和部署到报表设计器中。</span><span class="sxs-lookup"><span data-stu-id="96309-126">This builds and deploys an updated version of your custom assembly directly to Report Designer before your report is executed.</span></span>  
  
11. <span data-ttu-id="96309-127">在您设计了报表并开发了自定义程序集后，在自定义程序集代码中设置断点。</span><span class="sxs-lookup"><span data-stu-id="96309-127">Once you have designed your report and developed your custom assembly, set breakpoints in your custom assembly code.</span></span>  
  
12. <span data-ttu-id="96309-128">通过按下 F5 键在 DebugLocal 模式下运行报表\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-128">Run the report under **DebugLocal** mode by pressing the F5 key.</span></span> <span data-ttu-id="96309-129">在报表在弹出式预览窗口中执行时，调试器命中与程序集中的可执行代码相对应的任何断点。</span><span class="sxs-lookup"><span data-stu-id="96309-129">When the report executes in the pop-up preview window, the debugger hits any breakpoints that correspond to executable code in your assembly.</span></span> <span data-ttu-id="96309-130">使用 F11 可以单步执行您的自定义程序集代码。</span><span class="sxs-lookup"><span data-stu-id="96309-130">Use F11 to step through your custom assembly code.</span></span>  
  
### <a name="to-debug-assemblies-using-two-instances-of-visual-studio"></a><span data-ttu-id="96309-131">使用 Visual Studio 的两个实例调试程序集</span><span class="sxs-lookup"><span data-stu-id="96309-131">To debug assemblies using two instances of Visual Studio</span></span>  
  
1.  <span data-ttu-id="96309-132">启动 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 并打开您的自定义程序集项目。</span><span class="sxs-lookup"><span data-stu-id="96309-132">Start [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] and open your custom assembly project.</span></span>  
  
2.  <span data-ttu-id="96309-133">生成项目，并将自定义程序集以及随附的 .pdb 文件部署到报表设计器。</span><span class="sxs-lookup"><span data-stu-id="96309-133">Build the project, and deploy your custom assembly and the accompanying .pdb file to the Report Designer.</span></span> <span data-ttu-id="96309-134">有关部署的详细信息，请参阅[部署自定义程序集](deploying-a-custom-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="96309-134">For more information about deployment, see [Deploying a Custom Assembly](deploying-a-custom-assembly.md).</span></span>  
  
3.  <span data-ttu-id="96309-135">打开使用您的自定义程序集的报表项目，同时在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 的一个单独实例中让自定义程序集代码处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="96309-135">Open up a report project that uses your custom assembly while leaving your custom assembly code open in a separate instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>  
  
4.  <span data-ttu-id="96309-136">导航到 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中包含自定义程序集项目的实例，并在代码中设置一些断点。</span><span class="sxs-lookup"><span data-stu-id="96309-136">Navigate to the instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] that contains your custom assembly project and set some break points in your code.</span></span>  
  
5.  <span data-ttu-id="96309-137">在自定义程序集项目的窗口仍然保持活动状态的同时，在“调试”菜单上单击“附加到进程”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-137">With the custom assembly project still the active window, click **Attach to Process** on the **Debug** menu.</span></span>  
  
     <span data-ttu-id="96309-138">“附加到进程”对话框会打开\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-138">The **Attach to Process** dialog opens.</span></span>  
  
6.  <span data-ttu-id="96309-139">从进程列表中，选择与报表项目对应的 devenv.exe 进程并单击“附加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-139">From the list of processes, select the devenv.exe process that corresponds to your Report Project and click **Attach**.</span></span>  
  
7.  <span data-ttu-id="96309-140">定义将用于您的自定义程序集的报表的表达式并设计报表。</span><span class="sxs-lookup"><span data-stu-id="96309-140">Define the expressions that you will use in your report from your custom assembly and design your report.</span></span>  
  
8.  <span data-ttu-id="96309-141">在完成报表设计后，单击“预览”选项卡\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-141">When you are finished designing your report, click the **Preview** tab.</span></span>  
  
     <span data-ttu-id="96309-142">报表将执行，并且自定义程序集代码应在您预定义的断点处中断。</span><span class="sxs-lookup"><span data-stu-id="96309-142">The report executes, and the custom assembly code should break at your predefined break points.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="96309-143">使用“预览”选项卡并不强制对程序集的代码权限\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-143">Using the **Preview** tab does not enforce code permissions for the assembly.</span></span> <span data-ttu-id="96309-144">对于包括任何代码访问权限错误的完整测试，启动 DebugLocal 配置设置下的报表项目\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96309-144">For a complete test, which includes any code access security errors, start the report project under the **DebugLocal** configuration setting.</span></span>  
  
9. <span data-ttu-id="96309-145">使用 F11 键分步执行代码。</span><span class="sxs-lookup"><span data-stu-id="96309-145">Step through your code using the F11 key.</span></span> <span data-ttu-id="96309-146">有关使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 进行调试的详细信息，请参阅 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 文档。</span><span class="sxs-lookup"><span data-stu-id="96309-146">For more information about debugging using [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], see the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96309-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96309-147">See Also</span></span>  
 [<span data-ttu-id="96309-148">将自定义程序集用于报表</span><span class="sxs-lookup"><span data-stu-id="96309-148">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
