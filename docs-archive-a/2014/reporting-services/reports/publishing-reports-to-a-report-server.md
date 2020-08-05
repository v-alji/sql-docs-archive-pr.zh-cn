---
title: 将报表发布到报表服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- production environments [Reporting Services]
- report projects [Reporting Services]
- Debug configuration [Reporting Services]
- report publishing [Reporting Services]
- publishing reports [Reporting Services]
- report properties [Reporting Services]
- Report Designer [Reporting Services], deploying reports
- Production configuration [Reporting Services]
- publishing reports [Reporting Services], production environments
- DebugLocal configuration [Reporting Services]
- deploying [Reporting Services], reports
- Report Designer [Reporting Services], publishing reports
ms.assetid: bd7aa5e0-61ce-43fd-8f74-5d1aeed078bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 644db7cc0d6647c160836596e6c87d524a94a4aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580574"
---
# <a name="publishing-reports-to-a-report-server"></a><span data-ttu-id="8aa8e-102">将报表发布到报表服务器</span><span class="sxs-lookup"><span data-stu-id="8aa8e-102">Publishing Reports to a Report Server</span></span>
  <span data-ttu-id="8aa8e-103">设计和测试报表或报表集之后，可以使用中的内置部署功能 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 将报表发布到 Report Server。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-103">After you have designed and tested a report or set of reports, you can use the built-in deployment features in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to publish the reports to a report server.</span></span> <span data-ttu-id="8aa8e-104">您可以发布单个报表或报表服务器项目。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-104">You can publish individual reports or a Report Server project.</span></span> <span data-ttu-id="8aa8e-105">发布报表服务器项目是发布多个报表的最简单方式。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-105">Publishing a Report Server project is the easiest way to publish multiple reports.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="8aa8e-106">使用术语 "*部署*"，而不是 "*发布*"。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-106">uses the term *deploy*, instead ofthe term *publish*.</span></span> <span data-ttu-id="8aa8e-107">这两个术语可以互换。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-107">The two terms are interchangeable.</span></span>  
  
 <span data-ttu-id="8aa8e-108">发布报表之前，您必须具有相应的权限。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-108">Before you can publish a report, you must have permission to do so.</span></span> <span data-ttu-id="8aa8e-109">权限是通过基于角色的安全性确定的，而安全性由报表服务器管理员定义。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-109">Permission is determined through role-based security that is defined by your report server administrator.</span></span> <span data-ttu-id="8aa8e-110">发布操作通常由“发布者”角色授予。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-110">Publishing operations are typically granted through the Publisher role.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="8aa8e-111">为管理报表发布提供项目配置。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-111">provides project configurations for managing report publication.</span></span> <span data-ttu-id="8aa8e-112">此配置指定报表服务器的位置、在报表服务器上安装的 SQL Server Reporting Services 的版本、发布到报表服务器的数据源是否被覆盖等等。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-112">The configuration specifies the location of the report server, the version of SQL Server Reporting Services installed on the report server, whether the data sources published to the report server are overwritten and so forth.</span></span> <span data-ttu-id="8aa8e-113">除了使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 提供的配置之外，还可以创建其他配置。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-113">In addition to using the configurations that [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] provides, you can create additional configurations.</span></span>  
  
## <a name="project-configurations"></a><span data-ttu-id="8aa8e-114">项目配置</span><span class="sxs-lookup"><span data-stu-id="8aa8e-114">Project Configurations</span></span>  
 <span data-ttu-id="8aa8e-115">报表将在发布之前生成，以确保只将有效的报表定义发布到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-115">Reports are built before they are published to ensure that only valid report definitions are published to the report server.</span></span> <span data-ttu-id="8aa8e-116">项目配置包括用于生成报表的属性（如临时存储所生成的报表的文件夹）以及如何处理生成问题。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-116">Project configurations include properties for building reports, such as the folder in which to temporarily store the built reports, and how to handle build issues.</span></span> <span data-ttu-id="8aa8e-117">配置还具有用于指定报表服务器的位置和版本以及报表服务器上的文件夹的属性。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-117">The configurations also have properties that you use to specify the location and version of the report server, the folders on the report server.</span></span>  
  
 <span data-ttu-id="8aa8e-118">默认情况下， [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 提供三种配置：DebugLocal、Debug 和 Release。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-118">By default, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] provides three project configurations: DebugLocal, Debug, and Release.</span></span> <span data-ttu-id="8aa8e-119">默认配置为 DebugLocal。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-119">The default configuration is DebugLocal.</span></span> <span data-ttu-id="8aa8e-120">通常，使用 DebugLocal 配置可以在本地预览窗口中查看报表，使用 Debug 配置可以将报表发布到测试服务器，使用 Release 配置可以将报表发布到生产服务器。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-120">You typically use the DebugLocal configuration to view reports in a local preview window, the Debug configuration to publish reports to a test server, and the Release configuration to publish reports to a production server.</span></span> <span data-ttu-id="8aa8e-121">标准工具栏上的解决方案配置下拉列表中显示了活动的配置。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-121">The solution configurations drop-down list on the Standard toolbar shows the active configuration.</span></span> <span data-ttu-id="8aa8e-122">若要使用其他配置，请从列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-122">To use a different configuration, select it from the list.</span></span>  
  
 <span data-ttu-id="8aa8e-123">报告环境中可能安装了多个报表服务器和不同版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-123">Your reporting environment might have multiple report servers and different versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installed.</span></span> <span data-ttu-id="8aa8e-124">您可以创建多个配置，然后根据部署方案选择不同的配置。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-124">You can create multiple configurations and then use a different one depending the deployment scenario.</span></span> <span data-ttu-id="8aa8e-125">有关详细信息，请参阅[SQL Server Data Tools &#40;SSRS&#41;中的部署和版本支持](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)，并[&#40;Reporting Services&#41;设置部署属性](../tools/set-deployment-properties-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-125">For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md) and [Set Deployment Properties &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md).</span></span>  
  
## <a name="publishing-reports"></a><span data-ttu-id="8aa8e-126">发布报表</span><span class="sxs-lookup"><span data-stu-id="8aa8e-126">Publishing Reports</span></span>  
 <span data-ttu-id="8aa8e-127">您可以发布单个报表，也可以发布包含多个报表的报表服务器项目。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-127">You can publish a single report or a Report Server project that contains multiple reports.</span></span> <span data-ttu-id="8aa8e-128">有关发布报表的说明，请参阅[发布报表](../publish-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-128">For instructions about publishing reports, see [Publish Reports](../publish-reports.md).</span></span>  
  
### <a name="publishing-a-single-report"></a><span data-ttu-id="8aa8e-129">发布单个报表</span><span class="sxs-lookup"><span data-stu-id="8aa8e-129">Publishing a Single Report</span></span>  
 <span data-ttu-id="8aa8e-130">如果不希望发布项目中的所有报表，可以选择只发布单个报表。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-130">If you do not want to publish all reports in a project, you can chose to publish only a single report.</span></span> <span data-ttu-id="8aa8e-131">为此，请选择一种部署报表的配置（例如，“发布”配置），然后右键单击相应的报表，再单击“部署”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-131">To do this, select a configuration that deploys the report (for example, the Release configuration), right-click the report, and then click **Deploy**.</span></span>  
  
 <span data-ttu-id="8aa8e-132">如果报表使用共享数据源，您还需要部署共享数据源，否则，部署的报表将不会运行。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-132">If a report uses a shared data source, you need to also deploy the shared data source or the deployed report will not run.</span></span> <span data-ttu-id="8aa8e-133">右键单击该共享数据源，再单击“部署”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-133">Right-click the shared data source and then click **Deploy**.</span></span>  
  
 <span data-ttu-id="8aa8e-134">必须指定报表服务器的目标服务器 URL，并且可能需要更改将报表和共享数据源部署到的默认文件夹。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-134">The target server URL of the report server must be specified and you might want to change the default folders to which reports and shared data sources deploy.</span></span>  
  
### <a name="publishing-multiple-reports"></a><span data-ttu-id="8aa8e-135">发布多个报表</span><span class="sxs-lookup"><span data-stu-id="8aa8e-135">Publishing Multiple Reports</span></span>  
 <span data-ttu-id="8aa8e-136">当您发布报表服务器项目时，将会发布该项目中的所有报表。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-136">When you publish a Report Server project, you publish all reports in that project.</span></span> <span data-ttu-id="8aa8e-137">将使用相同的项目配置部署所有报表：部署到同一个报表服务器、该服务器上的同一个文件夹等等。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-137">All reports are deployed using the same project configuration: to the same report server, the same folder on the server, and so on.</span></span> <span data-ttu-id="8aa8e-138">若要将报表发布到不同服务器，请逐个发布这些报表，或者只包含报表服务器项目中您要发布的报表。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-138">To publish reports to different servers, either publish them one by one or include only reports you want to in the Report Server project.</span></span> <span data-ttu-id="8aa8e-139">一个解决方案可以包含多个报表服务器项目，而使用多个项目可能会使管理报表部署的过程变得更为简单，因为您可以使用不同的配置来部署不同的项目。</span><span class="sxs-lookup"><span data-stu-id="8aa8e-139">A solution can include multiple Report Server projects, and using multiple project might make it easier to manage the deployment of reports because you can use a different configuration to deploy different projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aa8e-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8aa8e-140">See Also</span></span>  
 <span data-ttu-id="8aa8e-141">["项目属性页" 对话框](../tools/project-property-pages-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="8aa8e-141">[Project Property Pages Dialog Box](../tools/project-property-pages-dialog-box.md) </span></span>  
 <span data-ttu-id="8aa8e-142">[报表服务器内容管理（SSRS 本机模式）](../report-server/report-server-content-management-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="8aa8e-142">[Report Server Content Management &#40;SSRS Native Mode&#41;](../report-server/report-server-content-management-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="8aa8e-143">升级报表</span><span class="sxs-lookup"><span data-stu-id="8aa8e-143">Upgrade Reports</span></span>](../install-windows/upgrade-reports.md)  
  
  
