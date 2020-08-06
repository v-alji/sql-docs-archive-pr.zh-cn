---
title: 发布报表 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], publishing
- publishing reports [Reporting Services]
ms.assetid: ef5a514e-e818-4041-a8b0-15835f9a046b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb54308a6b15260d4c336950f231d0ee40836430
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577359"
---
# <a name="publish-reports"></a><span data-ttu-id="9637d-102">发布报表</span><span class="sxs-lookup"><span data-stu-id="9637d-102">Publish Reports</span></span>
  <span data-ttu-id="9637d-103">从[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，你可以通过部署报表服务器项目将项目中的所有报表和共享数据源发布到报表服务器，也可以发布单个报表。</span><span class="sxs-lookup"><span data-stu-id="9637d-103">From[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can publish either all the reports and shared data sources in a Report Server project to a report server by deploying the project, or you can publish a single report.</span></span> <span data-ttu-id="9637d-104">在可以发布报表之前，必须指定目标报表服务器的 URL。</span><span class="sxs-lookup"><span data-stu-id="9637d-104">Before you can publish a report you must specify the URL of the target report server.</span></span> <span data-ttu-id="9637d-105">有关详细信息，请参阅[设置部署属性 (Reporting Services)](tools/set-deployment-properties-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9637d-105">For more information, see [Set Deployment Properties &#40;Reporting Services&#41;](tools/set-deployment-properties-reporting-services.md).</span></span>  
  
 <span data-ttu-id="9637d-106">可以使用 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 版本的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 打开、修改、预览、保存和发布 [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] 和 [!INCLUDE[ssRSversion10](../includes/ssrsversion10-md.md)] 报表。</span><span class="sxs-lookup"><span data-stu-id="9637d-106">You can use the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] version of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to open, modify, preview, save, and publish both [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] and [!INCLUDE[ssRSversion10](../includes/ssrsversion10-md.md)] reports.</span></span> <span data-ttu-id="9637d-107">有关详细信息，请参阅 [SQL Server Data Tools 中的部署和版本支持 (SSRS)](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)中。</span><span class="sxs-lookup"><span data-stu-id="9637d-107">For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).</span></span>  
  
### <a name="to-publish-all-reports-in-a-project"></a><span data-ttu-id="9637d-108">发布项目中的所有报表</span><span class="sxs-lookup"><span data-stu-id="9637d-108">To publish all reports in a project</span></span>  
  
-   <span data-ttu-id="9637d-109">在 "**生成**" 菜单上，单击 "\*\*部署 \<report project name> \*\*"。</span><span class="sxs-lookup"><span data-stu-id="9637d-109">On the **Build** menu, click **Deploy \<report project name>**.</span></span> <span data-ttu-id="9637d-110">或者，在解决方案资源管理器中，右键单击报表项目，然后单击“部署”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9637d-110">Alternatively, in Solution Explorer, right-click the report project and then click **Deploy**.</span></span> <span data-ttu-id="9637d-111">可以在“输出”窗口中查看发布过程的状态。</span><span class="sxs-lookup"><span data-stu-id="9637d-111">You can view the status of the publishing process in the Output window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9637d-112">当您部署报表服务器项目时，也会部署报表服务器中的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="9637d-112">When you deploy a Report Server project, the shared data sources in the report project are also deployed.</span></span>  
  
### <a name="to-publish-a-single-report"></a><span data-ttu-id="9637d-113">发布单个报表</span><span class="sxs-lookup"><span data-stu-id="9637d-113">To publish a single report</span></span>  
  
-   <span data-ttu-id="9637d-114">在解决方案资源管理器中，右键单击报表，然后单击 **“部署”**。</span><span class="sxs-lookup"><span data-stu-id="9637d-114">In Solution Explorer, right-click the report and then click **Deploy**.</span></span> <span data-ttu-id="9637d-115">可以在“输出”窗口中查看发布过程的状态。</span><span class="sxs-lookup"><span data-stu-id="9637d-115">You can view the status of the publishing process in the Output window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9637d-116">当您发布报表时，还必须部署报表使用的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="9637d-116">When you publish a report, you must also deploy the shared data sources that the report uses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9637d-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9637d-117">See Also</span></span>  
 <span data-ttu-id="9637d-118">[发布数据源和报表](reports/publishing-data-sources-and-reports.md) </span><span class="sxs-lookup"><span data-stu-id="9637d-118">[Publishing Data Sources and Reports](reports/publishing-data-sources-and-reports.md) </span></span>  
 <span data-ttu-id="9637d-119">[预览报表](reports/previewing-reports.md) </span><span class="sxs-lookup"><span data-stu-id="9637d-119">[Previewing Reports](reports/previewing-reports.md) </span></span>  
 <span data-ttu-id="9637d-120">[将报表发布到报表服务器](reports/publishing-reports-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="9637d-120">[Publishing Reports to a Report Server](reports/publishing-reports-to-a-report-server.md) </span></span>  
 <span data-ttu-id="9637d-121">[查找、查看和管理 &#40;报表生成器和 SSRS 的报表 &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9637d-121">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9637d-122">导出报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9637d-122">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
