---
title: 报表、报表部件和报表定义（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report definitions
- reports
ms.assetid: 2d746550-f8cc-4e97-8a06-d0f03cffc18d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0926de326d0b5859e895d69da4dd2ad7863ccd2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590048"
---
# <a name="reports-report-parts-and-report-definitions-report-builder-and-ssrs"></a><span data-ttu-id="93365-102">报表、报表部件和报表定义（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="93365-102">Reports, Report Parts, and Report Definitions (Report Builder and SSRS)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="93365-103">使用各种术语来描述不同状态的报表，包括初始定义、发布的报表以及显示给用户的所查看报表。</span><span class="sxs-lookup"><span data-stu-id="93365-103">uses a variety of terms to describe a report in different states, including the initial definition, the published report, and the viewed report as it appears to the user.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-definition-rdl-files"></a><span data-ttu-id="93365-104">报表定义 (.rdl) 文件</span><span class="sxs-lookup"><span data-stu-id="93365-104">Report Definition (.rdl) Files</span></span>  
 <span data-ttu-id="93365-105">报表定义是一种在报表生成器或报表设计器中创建的文件。</span><span class="sxs-lookup"><span data-stu-id="93365-105">A report definition is a file that you create in Report Builder or Report Designer.</span></span> <span data-ttu-id="93365-106">对于数据源连接、用来检索数据的查询、表达式、参数、图像、文本框、表以及可能包含在报表中的任何其他设计时元素，它都提供了完整的说明。</span><span class="sxs-lookup"><span data-stu-id="93365-106">It provides a complete description of data source connections, queries used to retrieve data, expressions, parameters, images, text boxes, tables, and any other design-time elements that you might include in a report.</span></span> <span data-ttu-id="93365-107">尽管报表定义可以很复杂，但是也可以在最低条件下只指定一个查询以及其他报表内容、报表属性和报表布局。</span><span class="sxs-lookup"><span data-stu-id="93365-107">Although report definitions can be complex, at a minimum they specify a query and other report content, report properties, and a report layout.</span></span>  
  
 <span data-ttu-id="93365-108">在运行时，报表定义作为已处理的报表呈现。</span><span class="sxs-lookup"><span data-stu-id="93365-108">Report definitions are rendered at run time as a processed report.</span></span> <span data-ttu-id="93365-109">此时，将从数据源检索数据并根据报表定义中的说明设置数据格式。</span><span class="sxs-lookup"><span data-stu-id="93365-109">At that time, the data is retrieved from the data source and formatted according to the instructions in the report definition.</span></span> <span data-ttu-id="93365-110">可以从计算机直接运行报表定义并将其保存到本地，也可以将报表定义发布到报表服务器，以便其他人也可以运行报表定义。</span><span class="sxs-lookup"><span data-stu-id="93365-110">A report definition can be run directly from your computer and saved locally, or it can be published to a report server for others to run as well.</span></span>  
  
 <span data-ttu-id="93365-111">报表定义以 XML 格式编写，该格式应符合一种称为报表定义语言 (RDL) 的 XML 语法。</span><span class="sxs-lookup"><span data-stu-id="93365-111">Report definitions are written in XML that conforms to an XML grammar called Report Definition Language (RDL).</span></span> <span data-ttu-id="93365-112">RDL 描述了 XML 元素，包括报表会采用的所有可能变体。</span><span class="sxs-lookup"><span data-stu-id="93365-112">RDL describes the XML elements, encompassing all possible variations that a report can assume.</span></span>  
  
## <a name="client-report-definition-rdlc-files"></a><span data-ttu-id="93365-113">客户端报表定义 (.rdlc) 文件</span><span class="sxs-lookup"><span data-stu-id="93365-113">Client Report Definition (.rdlc) Files</span></span>  
 <span data-ttu-id="93365-114">Visual Studio 报表设计器产生客户端报表定义 (.rdlc) 文件以供与 ReportViewer 控件结合使用。</span><span class="sxs-lookup"><span data-stu-id="93365-114">The Visual Studio Report Designer produces client report definition (.rdlc) files for use with the ReportViewer control.</span></span> <span data-ttu-id="93365-115">.rdlc 文件可以转换为 .rdl 文件以供与 Reporting Services 报表设计器结合使用。</span><span class="sxs-lookup"><span data-stu-id="93365-115">The .rdlc files can be converted to .rdl files for use with Reporting Services Report Designer.</span></span>  
  
## <a name="report-part-rsc-files"></a><span data-ttu-id="93365-116">报表部件 (.rsc) 文件</span><span class="sxs-lookup"><span data-stu-id="93365-116">Report Part (.rsc) Files</span></span>  
 <span data-ttu-id="93365-117">报表部件定义是报表定义文件的 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="93365-117">A report part definition is an XML fragment of a report definition file.</span></span> <span data-ttu-id="93365-118">您可以通过创建报表定义，然后选择报表中要单独发布为报表部件的报表项，从而创建报表部件。</span><span class="sxs-lookup"><span data-stu-id="93365-118">You create report parts by creating a report definition, and then selecting report items in the report to publish separately as report parts.</span></span> <span data-ttu-id="93365-119">报表部件包括数据区域、矩形及其包含项以及图像。</span><span class="sxs-lookup"><span data-stu-id="93365-119">Report parts include data regions, rectangles and their contained items, and images.</span></span> <span data-ttu-id="93365-120">您可以保存报表部件及其相关数据集和共享数据源参考，这样它就可以在其他报表中重新使用。</span><span class="sxs-lookup"><span data-stu-id="93365-120">You can save a report part with its dependent datasets and shared data source references so it can be reused in other reports.</span></span>  
  
 [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
## <a name="published-reports"></a><span data-ttu-id="93365-121">发布的报表</span><span class="sxs-lookup"><span data-stu-id="93365-121">Published Reports</span></span>  
 <span data-ttu-id="93365-122">创建 .rdl 文件后，可以将其保存到本地，也可以将其保存到报表服务器上的个人文件夹（如“我的报表”文件夹）。</span><span class="sxs-lookup"><span data-stu-id="93365-122">After you create an .rdl file, you can save it locally, or save it to a personal folder (such as the My Reports folder) on the report server.</span></span> <span data-ttu-id="93365-123">当报表准备就绪可供他人查看时，您可以通过从报表生成器中将其保存到报表服务器上的公共文件夹，通过报表管理器上载它，或者从报表设计器中部署报表项目解决方案，从而发布此报表。</span><span class="sxs-lookup"><span data-stu-id="93365-123">When the report is ready for others to see, you publish it by saving it from Report Builder to a public folder on the report server, uploading it through Report Manager, or deploying a report project solution from Report Designer.</span></span> <span data-ttu-id="93365-124">发布的报表存储在报表服务器数据库中，并在报表服务器或 SharePoint 站点上进行管理。</span><span class="sxs-lookup"><span data-stu-id="93365-124">A published report is an item that is stored in a report server database and managed on a report server or SharePoint site.</span></span>  
  
 <span data-ttu-id="93365-125">发布的报表是通过角色分配进行保护的，这种角色分配使用的是基于 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 角色的安全模式。</span><span class="sxs-lookup"><span data-stu-id="93365-125">A published report is secured through role assignments using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] role-based security model.</span></span> <span data-ttu-id="93365-126">通过 URL、SharePoint Web 部件或报表管理器，即可访问发布的报表，您也可以导航到发布的报表并在报表生成器中打开这些报表。</span><span class="sxs-lookup"><span data-stu-id="93365-126">Published reports are accessed through URLs, SharePoint Web parts, or Report Manager, or you can navigate to and open them in Report Builder.</span></span>  
  
### <a name="report-snapshots"></a><span data-ttu-id="93365-127">报表快照</span><span class="sxs-lookup"><span data-stu-id="93365-127">Report Snapshots</span></span>  
 <span data-ttu-id="93365-128">报表也可以作为包含自报表最初运行时起的布局信息和数据的快照进行发布。</span><span class="sxs-lookup"><span data-stu-id="93365-128">A report can also be published as a snapshot that contains both layout information and data as of the time the report was initially run.</span></span> <span data-ttu-id="93365-129">报表快照不以特定的呈现格式进行保存。</span><span class="sxs-lookup"><span data-stu-id="93365-129">Report snapshots are not saved in a particular rendering format.</span></span> <span data-ttu-id="93365-130">相反，将以用户或应用程序发出请求时的最终查看格式（如 HTML）来呈现报表快照。</span><span class="sxs-lookup"><span data-stu-id="93365-130">Instead, report snapshots are rendered in a final viewing format (such as HTML) only when a user or an application requests it.</span></span> <span data-ttu-id="93365-131">有关详细信息，请参阅[在报表管理器中查找和查看报表（报表生成器和 SSRS）](../report-builder/finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="93365-131">For more information, see [Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;](../report-builder/finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md).</span></span>  
  
## <a name="rendered-reports"></a><span data-ttu-id="93365-132">呈现的报表</span><span class="sxs-lookup"><span data-stu-id="93365-132">Rendered Reports</span></span>  
 <span data-ttu-id="93365-133">呈现的报表是经过完全处理的报表，其中包含格式适于查看（例如 HTML）的数据和布局信息。</span><span class="sxs-lookup"><span data-stu-id="93365-133">A rendered report is a fully processed report that contains both data and layout information in a format suitable for viewing (such as HTML).</span></span> <span data-ttu-id="93365-134">只有在报表以输出格式呈现之后，才能查看报表。</span><span class="sxs-lookup"><span data-stu-id="93365-134">Until a report is rendered into an output format, it cannot be viewed.</span></span> <span data-ttu-id="93365-135">您可以通过执行以下操作之一来呈现报表：</span><span class="sxs-lookup"><span data-stu-id="93365-135">You can render a report by doing one of the following:</span></span>  
  
-   <span data-ttu-id="93365-136">在报表生成器或报表设计器中创建或打开报表并运行该报表。</span><span class="sxs-lookup"><span data-stu-id="93365-136">Create or open a report in Report Builder or Report Designer and run it.</span></span>  
  
-   <span data-ttu-id="93365-137">在报表管理器中查找某个报表并运行该报表。</span><span class="sxs-lookup"><span data-stu-id="93365-137">Find and run a report in Report Manager.</span></span>  
  
-   <span data-ttu-id="93365-138">在与 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表服务器集成的 SharePoint 站点上查找并运行报表。</span><span class="sxs-lookup"><span data-stu-id="93365-138">Find and run a report on a SharePoint site that is integrated with a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server.</span></span>  
  
-   <span data-ttu-id="93365-139">订阅报表，这样报表将以您指定的输出格式传递到电子邮件收件箱或文件共享位置。</span><span class="sxs-lookup"><span data-stu-id="93365-139">Subscribe to a report, which is delivered to an e-mail inbox or a file share in an output format that you specify.</span></span>  
  
 <span data-ttu-id="93365-140">订阅报表，这样报表将以您指定的输出格式传递到电子邮件收件箱或文件共享位置。报表的默认呈现格式为 HTML 4.0。</span><span class="sxs-lookup"><span data-stu-id="93365-140">Subscribe to a report, which is delivered to an e-mail inbox or a file share in an output format that you specify.The default rendering format for a report is HTML 4.0.</span></span> <span data-ttu-id="93365-141">除了 HTML 之外，报表还可以用多种输出格式呈现，其中包括 Excel、Word、XML、PDF、TIFF 和 CSV。</span><span class="sxs-lookup"><span data-stu-id="93365-141">In addition to HTML, reports can be rendered in a variety of output formats, including Excel, Word, XML, PDF, TIFF, and CSV.</span></span> <span data-ttu-id="93365-142">与发布的报表一样，无法编辑呈现的报表，也不能将其保存回报表服务器。</span><span class="sxs-lookup"><span data-stu-id="93365-142">As with published reports, rendered reports cannot be edited or saved back to a report server.</span></span> <span data-ttu-id="93365-143">有关详细信息，请参阅[导出报表 &#40;报表生成器和 SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="93365-143">For more information, see [Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93365-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93365-144">See Also</span></span>  
 <span data-ttu-id="93365-145">[报表创作概念 &#40;报表生成器和 SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="93365-145">[Report Authoring Concepts &#40;Report Builder and SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="93365-146">[SQL Server 2014 中的报表生成器](../report-builder/report-builder-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="93365-146">[Report Builder in SQL Server 2014](../report-builder/report-builder-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="93365-147">[安装、卸载和报表生成器支持](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="93365-147">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 <span data-ttu-id="93365-148">[查找、查看和管理 &#40;报表生成器和 SSRS 的报表 &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="93365-148">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="93365-149">导出报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="93365-149">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
