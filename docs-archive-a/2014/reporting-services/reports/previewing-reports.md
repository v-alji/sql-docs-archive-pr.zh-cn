---
title: 预览报表
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: fb068937efff71667d7f73c8e7ecd4d9ebfa576b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579479"
---
# <a name="preview-reports-in-sql-server-reporting-services-ssrs"></a><span data-ttu-id="d4116-102">预览 SQL Server Reporting Services (SSRS) 中的报表</span><span class="sxs-lookup"><span data-stu-id="d4116-102">Preview Reports in SQL Server Reporting Services (SSRS)</span></span>

  <span data-ttu-id="d4116-103">在设计报表时，在将报表发布到生产环境中之前可能需要查看该报表。</span><span class="sxs-lookup"><span data-stu-id="d4116-103">When you design a report, you may want to view it before publishing it to a production environment.</span></span> <span data-ttu-id="d4116-104">可使用多种方法查看该报表：在报表设计器中切换到预览模式、使用报表设计器中的预览窗口以及在测试环境中将报表发布到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="d4116-104">You can do this in several ways: by switching to Preview mode in Report Designer, by using the preview window in Report Designer, and by publishing the report to a report server in a test environment.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="d4116-105">在预览报表时，报表数据将缓存到本地计算机上的文件中。</span><span class="sxs-lookup"><span data-stu-id="d4116-105">When you preview a report, the data for the report is cached to a file on the local computer.</span></span> <span data-ttu-id="d4116-106">使用相同的查询、参数和凭据再次预览同一报表时，报表设计器将检索缓存副本，而不是重新运行查询。</span><span class="sxs-lookup"><span data-stu-id="d4116-106">When you preview the same report again using the same query, parameters, and credentials, Report Designer retrieves the cached copy rather than rerunning the query.</span></span> <span data-ttu-id="d4116-107">数据文件 *\<reportname>* 在报表定义文件所在的同一目录中另存为 .rdl。</span><span class="sxs-lookup"><span data-stu-id="d4116-107">The data file is saved as *\<reportname>*.rdl.data in the same directory as the report definition file.</span></span> <span data-ttu-id="d4116-108">关闭报表设计器时，不会删除该文件。</span><span class="sxs-lookup"><span data-stu-id="d4116-108">The file is not deleted when you close Report Designer.</span></span>  
  
## <a name="preview-mode"></a><span data-ttu-id="d4116-109">预览模式</span><span class="sxs-lookup"><span data-stu-id="d4116-109">Preview Mode</span></span>

 <span data-ttu-id="d4116-110">可以通过单击 "**预览**" 在报表设计器中预览报表。</span><span class="sxs-lookup"><span data-stu-id="d4116-110">You can preview a report in Report Designer by clicking **Preview**.</span></span> <span data-ttu-id="d4116-111">这将在本地运行报表，使用的报表处理功能和呈现功能与报表服务器所提供的功能相同。</span><span class="sxs-lookup"><span data-stu-id="d4116-111">This runs the report locally, using the same report processing and rendering functionality that is provided with the report server.</span></span> <span data-ttu-id="d4116-112">所显示的报表是一个交互式的图像；您可以选择参数、单击链接、查看文档结构图以及展开和折叠报表的隐藏区域。</span><span class="sxs-lookup"><span data-stu-id="d4116-112">The report that is displayed is an interactive image; you can select parameters, click links, view the document map, and expand and collapse hidden areas of the report.</span></span> <span data-ttu-id="d4116-113">您还可以使用所安装的任意一种呈现格式将报表导出。</span><span class="sxs-lookup"><span data-stu-id="d4116-113">You can also export the report to any of the installed rendering formats.</span></span>  
  
## <a name="standalone-preview"></a><span data-ttu-id="d4116-114">独立预览</span><span class="sxs-lookup"><span data-stu-id="d4116-114">Standalone Preview</span></span>

 <span data-ttu-id="d4116-115">预览报表的另一种方法是使用调试配置运行报表项目，例如，调试您编写的自定义程序集。</span><span class="sxs-lookup"><span data-stu-id="d4116-115">Another way to preview a report is to run the report project in a debug configuration, for example, to debug custom assemblies that you write.</span></span> <span data-ttu-id="d4116-116">运行项目的方法有以下三种：</span><span class="sxs-lookup"><span data-stu-id="d4116-116">There are three ways to run a project:</span></span>  
  
- <span data-ttu-id="d4116-117">单击 "**调试**" 菜单上的 "**启动**"。</span><span class="sxs-lookup"><span data-stu-id="d4116-117">By clicking **Start** on the **Debug** menu.</span></span>  
  
- <span data-ttu-id="d4116-118">单击 "标准" 工具栏上的 "**开始**" 按钮 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d4116-118">By clicking the **Start** button on the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] standard toolbar.</span></span>  
  
- <span data-ttu-id="d4116-119">按 F5。</span><span class="sxs-lookup"><span data-stu-id="d4116-119">By pressing F5.</span></span>  
  
 <span data-ttu-id="d4116-120">如果使用生成报表但不部署该报表的项目配置，则将在单独的预览窗口中打开在当前配置的 `StartItem` 属性中指定的报表。</span><span class="sxs-lookup"><span data-stu-id="d4116-120">If you use a project configuration that builds the report but does not deploy it, the report that is specified in the `StartItem` property of the current configuration opens in a separate preview window.</span></span> <span data-ttu-id="d4116-121">预览窗口显示报表的方式与预览模式相同，并具有相同功能。</span><span class="sxs-lookup"><span data-stu-id="d4116-121">The preview window displays the report in the same way and has the same functionality as Preview mode.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="d4116-122">在调试报表之前，必须设置开始项。</span><span class="sxs-lookup"><span data-stu-id="d4116-122">Before debugging a report, you must set a start item.</span></span> <span data-ttu-id="d4116-123">若要设置启动项，请在解决方案资源管理器中右键单击报表项目，再单击 "**属性**"，然后在中 `StartItem` ，选择要显示的报表的名称。</span><span class="sxs-lookup"><span data-stu-id="d4116-123">To set a start item, in Solution Explorer, right-click the report project, click **Properties**, and then in `StartItem`, select the name of the report to display.</span></span>  
  
 <span data-ttu-id="d4116-124">若要预览项目开始项之外的特定报表，请选择生成报表但不部署该报表的配置（例如，DebugLocal 配置），右键单击报表，再单击 **“运行”**。</span><span class="sxs-lookup"><span data-stu-id="d4116-124">If you wish to preview a particular report that is not the start item for the project, select a configuration that builds the report but does not deploy it (for example, the DebugLocal configuration), right-click the report, and then click **Run**.</span></span> <span data-ttu-id="d4116-125">必须选择不部署报表的配置；否则，报表将发布到报表服务器，而不是显示在本地预览窗口中。</span><span class="sxs-lookup"><span data-stu-id="d4116-125">You must choose a configuration that does not deploy the report; otherwise, the report will be published to the report server instead of displayed locally in a preview window.</span></span>  
  
## <a name="print-preview"></a><span data-ttu-id="d4116-126">打印预览</span><span class="sxs-lookup"><span data-stu-id="d4116-126">Print Preview</span></span>

 <span data-ttu-id="d4116-127">首次在预览模式下或在预览窗口中查看报表时，报表的视图类似于 HTML 呈现扩展插件所生成的报表。</span><span class="sxs-lookup"><span data-stu-id="d4116-127">When you first view a report on in Preview mode or in the preview window, the view of the report resembles a report produced by the HTML rendering extension.</span></span> <span data-ttu-id="d4116-128">虽然预览并非 HTML 格式，但报表的布局和分页与 HTML 格式的输出结果类似。</span><span class="sxs-lookup"><span data-stu-id="d4116-128">The preview is not HTML, but the layout and pagination of the report is similar to HTML output.</span></span>  
  
 <span data-ttu-id="d4116-129">可通过切换到打印预览模式，查看报表的打印效果。</span><span class="sxs-lookup"><span data-stu-id="d4116-129">You can change the view to represent a printed report by switching to print preview mode.</span></span> <span data-ttu-id="d4116-130">单击预览工具栏上的 **“打印预览”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="d4116-130">Click the **Print Preview** button on the preview toolbar.</span></span> <span data-ttu-id="d4116-131">所显示的报表就如同打印在纸张上一样。</span><span class="sxs-lookup"><span data-stu-id="d4116-131">The report will display as though it were on a physical page.</span></span> <span data-ttu-id="d4116-132">此视图与图像呈现扩展插件和 PDF 呈现扩展插件所生成的输出类似。</span><span class="sxs-lookup"><span data-stu-id="d4116-132">This view resembles the output produced by the Image and PDF rendering extensions.</span></span> <span data-ttu-id="d4116-133">虽然打印预览并非图像或 PDF 文件，但报表的布局和分页与这些格式的输出类似。</span><span class="sxs-lookup"><span data-stu-id="d4116-133">Print preview is not an image or PDF file, but the layout and pagination of the report is similar the output in those formats.</span></span>  
  
## <a name="publish-to-a-test-server"></a><span data-ttu-id="d4116-134">发布到测试服务器</span><span class="sxs-lookup"><span data-stu-id="d4116-134">Publish to a Test Server</span></span>

 <span data-ttu-id="d4116-135">也可以通过将报表发布到测试服务器来对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="d4116-135">You can also test reports by publishing them to a test server.</span></span> <span data-ttu-id="d4116-136">将报表发布到测试服务器与发布到生产服务器是相同的。</span><span class="sxs-lookup"><span data-stu-id="d4116-136">Publishing a report to a test server is the same as publishing to a production server.</span></span> <span data-ttu-id="d4116-137">有关发布报表的信息，请参阅 [将报表发布到报表服务器](publishing-reports-to-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d4116-137">For information about publishing a report, see [Publishing Reports to a Report Server](publishing-reports-to-a-report-server.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d4116-138">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d4116-138">Next steps</span></span>

 - [<span data-ttu-id="d4116-139">打印报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="d4116-139">Print Reports &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/print-reports-report-builder-and-ssrs.md)
 - [<span data-ttu-id="d4116-140">打印报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="d4116-140">Print a Report &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/print-a-report-report-builder-and-ssrs.md)
 - [<span data-ttu-id="d4116-141">发布报表</span><span class="sxs-lookup"><span data-stu-id="d4116-141">Publish Reports</span></span>](../publish-reports.md)
 - [<span data-ttu-id="d4116-142">将自定义程序集用于报表</span><span class="sxs-lookup"><span data-stu-id="d4116-142">Using Custom Assemblies with Reports</span></span>](../custom-assemblies/using-custom-assemblies-with-reports.md)