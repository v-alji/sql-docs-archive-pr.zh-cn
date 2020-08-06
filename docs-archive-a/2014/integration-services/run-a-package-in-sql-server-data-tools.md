---
title: 在 SQL Server Data Tools 中运行包 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 31ca2390ef6bb04b63e4de9978193aed8884da36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687963"
---
# <a name="run-a-package-in-sql-server-data-tools"></a><span data-ttu-id="be064-102">在 SQL Server Data Tools 中运行包</span><span class="sxs-lookup"><span data-stu-id="be064-102">Run a Package in SQL Server Data Tools</span></span>
  <span data-ttu-id="be064-103">在开发、调试和测试包的过程中，通常在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中运行包。</span><span class="sxs-lookup"><span data-stu-id="be064-103">You typically run packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] during the development, debugging, and testing of packages.</span></span> <span data-ttu-id="be064-104">在从 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器运行包时，包始终可以立即运行。</span><span class="sxs-lookup"><span data-stu-id="be064-104">When you run a package from [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the package always runs immediately.</span></span>  
  
 <span data-ttu-id="be064-105">包运行时， [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器在 **“进度”** 选项卡上显示包执行的进度。除了有关包中失败的所有任务或容器的信息外，还可以查看包及其任务和容器的开始时间和完成时间。</span><span class="sxs-lookup"><span data-stu-id="be064-105">While a package is running, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer displays the progress of package execution on the **Progress** tab. You can view the start and finish time of the package and its tasks and containers, in addition to information about any tasks or containers in the package that failed.</span></span> <span data-ttu-id="be064-106">在包完成运行后，运行时信息仍显示在“执行结果”  选项卡上。有关详细信息，请参阅 [Debugging Control Flow](control-flow/control-flow.md)主题中的“进度报告”部分。</span><span class="sxs-lookup"><span data-stu-id="be064-106">After the package finishes running, the run-time information remains available on the **Execution Results** tab. For more information, see the section, "Progress Reporting," in the topic, [Debugging Control Flow](control-flow/control-flow.md).</span></span>  
  
 <span data-ttu-id="be064-107">**设计时部署**。</span><span class="sxs-lookup"><span data-stu-id="be064-107">**Design-time deployment**.</span></span> <span data-ttu-id="be064-108">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中运行包时，包被生成，然后部署到文件夹。</span><span class="sxs-lookup"><span data-stu-id="be064-108">When you run a package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], the package is built and then deployed to a folder.</span></span> <span data-ttu-id="be064-109">在运行包前，可以指定要包将部署到其中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="be064-109">Before you run the package, you can specify the folder to which the package is deployed.</span></span> <span data-ttu-id="be064-110">如果未指定文件夹，默认将使用 **bin** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="be064-110">If you do not specify a folder, the **bin** folder is used by default.</span></span> <span data-ttu-id="be064-111">这种部署称为设计时部署。</span><span class="sxs-lookup"><span data-stu-id="be064-111">This type of deployment is called design-time deployment.</span></span>  
  
### <a name="to-run-a-package-in-sql-server-data-tools"></a><span data-ttu-id="be064-112">在 SQL Server Data Tools 中运行包</span><span class="sxs-lookup"><span data-stu-id="be064-112">To run a package in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="be064-113">在“解决方案资源管理器”中，如果解决方案包含多个项目，则右键单击包含包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目，然后单击“设为启动对象”  以便设置启动项目。</span><span class="sxs-lookup"><span data-stu-id="be064-113">In Solution Explorer, if your solution contains multiple projects, right-click the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package, and then click **Set as StartUp Object** to set the startup project.</span></span>  
  
2.  <span data-ttu-id="be064-114">在“解决方案资源管理器”中，如果项目包含多个包，则右键单击某个包，然后单击“设为启动对象”  以便设置启动包。</span><span class="sxs-lookup"><span data-stu-id="be064-114">In Solution Explorer, if your project contains multiple packages, right-click a package, and then click **Set as StartUp Object** to set the startup package.</span></span>  
  
3.  <span data-ttu-id="be064-115">若要运行包，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="be064-115">To run a package, use one of the following procedures:</span></span>  
  
    -   <span data-ttu-id="be064-116">打开要运行的包，然后单击菜单栏上的 **“启动调试”** ，或按 F5。</span><span class="sxs-lookup"><span data-stu-id="be064-116">Open the package that you want to run and then click **Start Debugging** on the menu bar, or press F5.</span></span> <span data-ttu-id="be064-117">包运行完成后，按 Shift+F5 返回设计模式。</span><span class="sxs-lookup"><span data-stu-id="be064-117">After the package finishes running, press Shift+F5 to return to design mode.</span></span>  
  
    -   <span data-ttu-id="be064-118">在“解决方案资源管理器”中，右键单击包，然后单击“执行包”  。</span><span class="sxs-lookup"><span data-stu-id="be064-118">In Solution Explorer, right-click the package, and then click **Execute Package**.</span></span>  
  
### <a name="to-specify-a-different-folder-for-design-time-deployment"></a><span data-ttu-id="be064-119">为设计时部署指定不同文件夹</span><span class="sxs-lookup"><span data-stu-id="be064-119">To specify a different folder for design-time deployment</span></span>  
  
1.  <span data-ttu-id="be064-120">在“解决方案资源管理器”中，右键单击包含要运行的包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目文件夹，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="be064-120">In Solution Explorer, right-click the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project folder that contains the package you want to run, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="be064-121">在“\<project name>属性页”对话框中，单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="be064-121">In the **\<project name> Property Pages** dialog box, click **Build**.</span></span>  
  
3.  <span data-ttu-id="be064-122">更新 OutputPath 属性中的值以指定要用于设计时部署的文件夹，然后单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="be064-122">Update the value in the OutputPath property to specify the folder you want to use for design-time deployment, and click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be064-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="be064-123">See Also</span></span>  
 <span data-ttu-id="be064-124">[项目和包的执行](packages/run-integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="be064-124">[Execution of Projects and Packages](packages/run-integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="be064-125">Integration Services (SSIS) 包</span><span class="sxs-lookup"><span data-stu-id="be064-125">Integration Services &#40;SSIS&#41; Packages</span></span>](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
