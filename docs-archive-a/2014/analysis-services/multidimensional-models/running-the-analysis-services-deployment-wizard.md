---
title: 运行 Analysis Services 部署向导 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, running
ms.assetid: 3a38d489-4625-4878-bd18-c6f903be33df
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6207e3e7981f52ca158f50515166d237e0524ea7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694610"
---
# <a name="running-the-analysis-services-deployment-wizard"></a><span data-ttu-id="bad1b-102">运行 Analysis Services 部署向导</span><span class="sxs-lookup"><span data-stu-id="bad1b-102">Running the Analysis Services Deployment Wizard</span></span>
  <span data-ttu-id="bad1b-103">使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导部署 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目时，可以通过以下方式运行向导：</span><span class="sxs-lookup"><span data-stu-id="bad1b-103">When you use the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard to deploy a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you can run the wizard in the following ways:</span></span>  
  
-   <span data-ttu-id="bad1b-104">**交互式** 进行交互式运行时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导根据输入文件生成一个 XML 部署脚本，并根据用户的输入进行交互式更改。</span><span class="sxs-lookup"><span data-stu-id="bad1b-104">**Interactively** When run interactively, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard generates an XML deployment script based on the input files, as modified interactively by user input.</span></span> <span data-ttu-id="bad1b-105">此向导将任何用户的更改仅应用于部署脚本。</span><span class="sxs-lookup"><span data-stu-id="bad1b-105">The wizard applies any user modifications only to the deployment script.</span></span> <span data-ttu-id="bad1b-106">向导不会更改输入文件。</span><span class="sxs-lookup"><span data-stu-id="bad1b-106">The wizard does not modify the input files.</span></span> <span data-ttu-id="bad1b-107">有关输入文件的详细信息，请参阅 [了解用于创建部署脚本的输入文件](deployment-script-files-input-used-to-create-deployment-script.md)。</span><span class="sxs-lookup"><span data-stu-id="bad1b-107">For more information about the input files, see [Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md).</span></span>  
  
-   <span data-ttu-id="bad1b-108">**从命令提示符**在命令提示符下运行时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导基于用于运行向导的开关生成 (XMLA) 部署脚本 XML for Analysis。</span><span class="sxs-lookup"><span data-stu-id="bad1b-108">**From the command prompt** When run at the command prompt, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard generates an XML for Analysis (XMLA) deployment script based upon the switches that you use to run the wizard.</span></span> <span data-ttu-id="bad1b-109">该向导可以指导进行下面的任何一项操作：提示用户输入并基于输入更改输入文件；按原样使用输入文件以静默、无人参与模式运行部署；或创建一个以后可能使用的部署脚本。</span><span class="sxs-lookup"><span data-stu-id="bad1b-109">The wizard may any one of the following: prompt you for user input and modify input files based on that input; run a silent, unattended deployment using the input files as is; or create a deployment script that you can use later.</span></span>  
  
## <a name="running-the-analysis-services-deployment-wizard-interactively"></a><span data-ttu-id="bad1b-110">交互式运行 Analysis Services 部署向导</span><span class="sxs-lookup"><span data-stu-id="bad1b-110">Running the Analysis Services Deployment Wizard Interactively</span></span>  
 <span data-ttu-id="bad1b-111">进行交互式运行时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导读取输入文件中的值并向您显示该信息。</span><span class="sxs-lookup"><span data-stu-id="bad1b-111">When you run interactively, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the values from the input files and presents this information to you.</span></span> <span data-ttu-id="bad1b-112">您可以修改这些输入值-例如部署目标、配置设置、部署选项和连接字符串密码，或将其保留原样。</span><span class="sxs-lookup"><span data-stu-id="bad1b-112">You can modify these input values-such as deployment destination, configuration settings, deployment options, and connection string passwords-or leave them as is.</span></span> <span data-ttu-id="bad1b-113">如果更改任何输入值，在生成 XMLA 部署脚本时向导将使用这些更改。</span><span class="sxs-lookup"><span data-stu-id="bad1b-113">If you change any input values, the wizard uses these changes when generating the XMLA deployment script.</span></span> <span data-ttu-id="bad1b-114">但是，向导不会更改输入文件中的任何值。</span><span class="sxs-lookup"><span data-stu-id="bad1b-114">However, the wizard does not make any changes to the values in the input file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bad1b-115">如果使 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导更改输入值，那么可以在命令提示符处运行向导并将向导设置为以应答文件模式运行。</span><span class="sxs-lookup"><span data-stu-id="bad1b-115">If you want to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard modify the input values, run the wizard at the command prompt and set the wizard to run in answer file mode.</span></span>  
  
 <span data-ttu-id="bad1b-116">在检查完输入值并按照需要进行更改后，向导生成 XMLA 部署脚本。</span><span class="sxs-lookup"><span data-stu-id="bad1b-116">After you review the input values and make any wanted changes, the wizard generates the XMLA deployment script.</span></span> <span data-ttu-id="bad1b-117">可以立即在目标服务器上运行该部署脚本或者保存该脚本以备将来使用。</span><span class="sxs-lookup"><span data-stu-id="bad1b-117">You can run this deployment script immediately on the destination server or save the script for later use.</span></span>  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-interactively"></a><span data-ttu-id="bad1b-118">交互式运行 Analysis Services 部署向导</span><span class="sxs-lookup"><span data-stu-id="bad1b-118">To run the Analysis Services Deployment Wizard interactively</span></span>  
  
-   <span data-ttu-id="bad1b-119">单击 **“开始”**，依次指向 **“所有程序”**、 **“Microsoft SQL Server”** 和 **“Analysis Services”**，然后单击 **“部署向导”**。</span><span class="sxs-lookup"><span data-stu-id="bad1b-119">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Analysis Services**, and then click **Deployment Wizard**.</span></span>  
  
     <span data-ttu-id="bad1b-120">- 或 -</span><span class="sxs-lookup"><span data-stu-id="bad1b-120">-or-</span></span>  
  
-   <span data-ttu-id="bad1b-121">在项目的 "**项目**" 文件夹中 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，双击 *\<project name>* .asdatabase 文件。</span><span class="sxs-lookup"><span data-stu-id="bad1b-121">In the **Projects** folder of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, double-click the *\<project name>*.asdatabase file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bad1b-122">如果找不到 *\<project name>* .asdatabase 文件，请尝试使用 "搜索" 并指定 ".asdatabase"。</span><span class="sxs-lookup"><span data-stu-id="bad1b-122">If you cannot find the *\<project name>*.asdatabase file, try using Search and specify \*.asdatabase.</span></span>  
  
## <a name="running-the-analysis-services-deployment-wizard-at-the-command-prompt"></a><span data-ttu-id="bad1b-123">在命令提示符下运行 Analysis Services 部署向导</span><span class="sxs-lookup"><span data-stu-id="bad1b-123">Running the Analysis Services Deployment Wizard at the Command Prompt</span></span>  
 <span data-ttu-id="bad1b-124">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导也可以在命令提示符下运行。</span><span class="sxs-lookup"><span data-stu-id="bad1b-124">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard can also be run at the command prompt.</span></span> <span data-ttu-id="bad1b-125">在命令提示符下运行该向导时，应提供 .asdatabase 文件的完整路径，并使用下列模式之一运行该向导：</span><span class="sxs-lookup"><span data-stu-id="bad1b-125">When you run the wizard at the command prompt, you provide the full path to the .asdatabase file and  run the wizard in one of the following modes:</span></span>  
  
 <span data-ttu-id="bad1b-126">**应答文件模式**</span><span class="sxs-lookup"><span data-stu-id="bad1b-126">**Answer file mode**</span></span>  
 <span data-ttu-id="bad1b-127">使用应答文件模式，在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中生成 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]项目时，向导允许你交互式更改最初生成的输入文件。</span><span class="sxs-lookup"><span data-stu-id="bad1b-127">In answer file mode, the wizard lets you interactively modify the input files that were originally generated when the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project was built in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="bad1b-128">并且该向导在生成 XMLA 部署脚本之前保存更改过的这些输入文件。</span><span class="sxs-lookup"><span data-stu-id="bad1b-128">The wizard saves these modified input files before generating the XMLA deployment script.</span></span> <span data-ttu-id="bad1b-129">这些更改过的输入文件便成为向导下次运行时的新起点。</span><span class="sxs-lookup"><span data-stu-id="bad1b-129">The modified input files become the new starting point the next time that the wizard is run.</span></span>  
  
 <span data-ttu-id="bad1b-130">若要以应答文件模式运行向导，请使用 **/a**开关。</span><span class="sxs-lookup"><span data-stu-id="bad1b-130">To run the wizard in answer file mode, use the **/a** switch.</span></span>  
  
 <span data-ttu-id="bad1b-131">**静默模式**</span><span class="sxs-lookup"><span data-stu-id="bad1b-131">**Silent mode**</span></span>  
 <span data-ttu-id="bad1b-132">使用静默模式，向导基于输入文件中的信息以静默、无人参与的模式运行部署。</span><span class="sxs-lookup"><span data-stu-id="bad1b-132">In silent mode, the wizard runs a silent, unattended deployment based on the information resident in the input files.</span></span>  
  
 <span data-ttu-id="bad1b-133">若要以静默模式运行向导，请使用 **/s**开关。</span><span class="sxs-lookup"><span data-stu-id="bad1b-133">To run the wizard in silent mode, use the **/s** switch.</span></span> <span data-ttu-id="bad1b-134">如果以静默模式运行向导，则消息将输出至控制台或日志文件（如果有）。</span><span class="sxs-lookup"><span data-stu-id="bad1b-134">When you run the wizard in silent mode, messages are output to the console or to a log file if one is provided.</span></span>  
  
 <span data-ttu-id="bad1b-135">**输出模式**</span><span class="sxs-lookup"><span data-stu-id="bad1b-135">**Output mode**</span></span>  
 <span data-ttu-id="bad1b-136">使用输出模式，向导将基于输入文件生成 XMLA 部署脚本供以后执行。</span><span class="sxs-lookup"><span data-stu-id="bad1b-136">In output mode, the wizard generates an XMLA deployment script for later execution based on the input files.</span></span>  
  
 <span data-ttu-id="bad1b-137">若要以输出模式运行向导，请使用 **/o**开关并提供输出文件名。</span><span class="sxs-lookup"><span data-stu-id="bad1b-137">To run the wizard in output mode, use the **/o** switch and provide an output file name.</span></span>  
  
 <span data-ttu-id="bad1b-138">有关此类命令行开关的详细信息，请参阅 [使用部署实用工具部署模型解决方案](deploy-model-solutions-with-the-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="bad1b-138">For more information about these command line switches, see [Deploy Model Solutions with the Deployment Utility](deploy-model-solutions-with-the-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="bad1b-139">下面的过程说明了如何在命令提示符下运行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导。</span><span class="sxs-lookup"><span data-stu-id="bad1b-139">The following procedure describes how to run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt.</span></span>  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-at-the-command-prompt"></a><span data-ttu-id="bad1b-140">在命令提示符下运行 Analysis Services 部署向导</span><span class="sxs-lookup"><span data-stu-id="bad1b-140">To run the Analysis Services Deployment Wizard at the command prompt</span></span>  
  
1.  <span data-ttu-id="bad1b-141">打开命令提示符，导航到 C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE 文件夹。</span><span class="sxs-lookup"><span data-stu-id="bad1b-141">Open a command prompt and navigate to the C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE folder.</span></span>  
  
2.  <span data-ttu-id="bad1b-142">键入 **Microsoft.AnalysisServices.Deployment.exe** ，后跟与要使用的向导运行模式相对应的开关。</span><span class="sxs-lookup"><span data-stu-id="bad1b-142">Type **Microsoft.AnalysisServices.Deployment.exe** followed by the switches that correspond to the mode in which you want to run the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad1b-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bad1b-143">See Also</span></span>  
 <span data-ttu-id="bad1b-144">[了解 Analysis Services 部署脚本](understanding-the-analysis-services-deployment-script.md) </span><span class="sxs-lookup"><span data-stu-id="bad1b-144">[Understanding the Analysis Services Deployment Script](understanding-the-analysis-services-deployment-script.md) </span></span>  
 [<span data-ttu-id="bad1b-145">使用部署向导部署模型解决方案</span><span class="sxs-lookup"><span data-stu-id="bad1b-145">Deploy Model Solutions Using the Deployment Wizard</span></span>](deploy-model-solutions-using-the-deployment-wizard.md)  
  
  
