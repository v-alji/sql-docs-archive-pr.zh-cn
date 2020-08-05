---
title: 子报表（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab5bea3a-109e-4c25-92d9-494df7c52dd8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ce30cf575148af11d6485125089beace07fd5429
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577253"
---
# <a name="subreports-report-builder-and-ssrs"></a><span data-ttu-id="edd82-102">子报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="edd82-102">Subreports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="edd82-103">子报表是在主报表的表体中显示其他报表的报表项。</span><span class="sxs-lookup"><span data-stu-id="edd82-103">A subreport is a report item that displays another report inside the body of a main report.</span></span> <span data-ttu-id="edd82-104">从概念上说，报表中的子报表类似于网页中的框架。</span><span class="sxs-lookup"><span data-stu-id="edd82-104">Conceptually, a subreport in a report is similar to a frame in a Web page.</span></span> <span data-ttu-id="edd82-105">子报表用于在报表中嵌入另一个报表。</span><span class="sxs-lookup"><span data-stu-id="edd82-105">It is used to embed a report within a report.</span></span> <span data-ttu-id="edd82-106">任何报表都可以用作子报表。</span><span class="sxs-lookup"><span data-stu-id="edd82-106">Any report can be used as a subreport.</span></span> <span data-ttu-id="edd82-107">显示为子报表的报表存储在报表服务器上，通常与父报表在同一文件夹中。</span><span class="sxs-lookup"><span data-stu-id="edd82-107">The report that is displayed as the subreport is stored on a report server, usually in the same folder as the parent report.</span></span> <span data-ttu-id="edd82-108">您可以设计父报表，以便向子报表传递参数。</span><span class="sxs-lookup"><span data-stu-id="edd82-108">You can design the parent report to pass parameters to the subreport.</span></span> <span data-ttu-id="edd82-109">可以在数据区域中重复子报表，使用参数在子报表的每个实例中筛选数据。</span><span class="sxs-lookup"><span data-stu-id="edd82-109">A subreport can be repeated within data regions, using a parameter to filter data in each instance of the subreport.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="edd82-110">如果在 Tablix 数据区域中使用子报表，将为每一行处理子报表及其参数。</span><span class="sxs-lookup"><span data-stu-id="edd82-110">If you use a subreport in a tablix data region, the subreport and its parameters will be processed for every row.</span></span> <span data-ttu-id="edd82-111">如果存在多行，可考虑采用钻取报表是否更为合适。</span><span class="sxs-lookup"><span data-stu-id="edd82-111">If there are many rows, consider whether a drillthrough report is more appropriate.</span></span>  
  
 <span data-ttu-id="edd82-112">![rs_Subreport](../media/rs-subreport.gif "rs_Subreport")</span><span class="sxs-lookup"><span data-stu-id="edd82-112">![rs_Subreport](../media/rs-subreport.gif "rs_Subreport")</span></span>  
  
 <span data-ttu-id="edd82-113">在此图中，显示在 Sales Order 主报表中的联系人信息实际上来自于 Contacts 子报表。</span><span class="sxs-lookup"><span data-stu-id="edd82-113">In this illustration, the contact information displayed in the main Sales Order report actually comes from a Contacts subreport.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="comparing-subreports-and-nested-data-regions"></a><span data-ttu-id="edd82-114">比较子报表和嵌套数据区域</span><span class="sxs-lookup"><span data-stu-id="edd82-114">Comparing Subreports and Nested Data Regions</span></span>  
 <span data-ttu-id="edd82-115">如果您打算使用子报表来显示单独数据组，请考虑改用数据区域，例如表、矩阵和图表。</span><span class="sxs-lookup"><span data-stu-id="edd82-115">If you're thinking of using subreports to display separate groups of data, consider using data regions, such as tables, matrices, and charts, instead.</span></span> <span data-ttu-id="edd82-116">仅包含数据区域的报表的性能优于包含子报表的报表。</span><span class="sxs-lookup"><span data-stu-id="edd82-116">Reports with data regions only may perform better than reports that include subreports.</span></span>  
  
 <span data-ttu-id="edd82-117">使用数据区域可以在一个数据区域内嵌套来自同一数据源的数据组。</span><span class="sxs-lookup"><span data-stu-id="edd82-117">Use data regions to nest groups of data from the same data source within a single data region.</span></span> <span data-ttu-id="edd82-118">使用子报表可以在一个数据区域内嵌套来自不同数据源的数据组、在多个父报表中重复使用某个子报表，或者在另一个报表中显示独立的报表。</span><span class="sxs-lookup"><span data-stu-id="edd82-118">Use subreports to nest groups of data from different data sources within a single data region, reuse a subreport in multiple parent reports, or display a standalone report inside of another report.</span></span> <span data-ttu-id="edd82-119">例如，通过在另一个报表的表体内放置多个子报表，可以创建“摘要簿”。</span><span class="sxs-lookup"><span data-stu-id="edd82-119">For example, you can create a "briefing book" by placing multiple subreports inside the body of another report.</span></span>  
  
 <span data-ttu-id="edd82-120">数据区域的功能和灵活性与子报表相差无几，但性能更佳。</span><span class="sxs-lookup"><span data-stu-id="edd82-120">Data regions provide much of the same functionality and flexibility as subreports, but with better performance.</span></span> <span data-ttu-id="edd82-121">由于报表服务器将子报表的每个实例作为独立的报表来处理，因此性能可能会受到影响。</span><span class="sxs-lookup"><span data-stu-id="edd82-121">Because the report server processes each instance of a subreport as a separate report, performance can be impacted.</span></span> <span data-ttu-id="edd82-122">有关详细信息，请参阅 [嵌套数据区域（报表生成器和 SSRS）](nested-data-regions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="edd82-122">For more information, see [Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md).</span></span>  
  
## <a name="using-parameters-in-subreports"></a><span data-ttu-id="edd82-123">在子报表中使用参数</span><span class="sxs-lookup"><span data-stu-id="edd82-123">Using Parameters in Subreports</span></span>  
 <span data-ttu-id="edd82-124">若要将参数从父报表传递给子报表，请在用作子报表的报表中定义报表参数。</span><span class="sxs-lookup"><span data-stu-id="edd82-124">To pass parameters from the parent report to the subreport, define a report parameter in the report that you use as the subreport.</span></span> <span data-ttu-id="edd82-125">在父报表中放入子报表时，您可以选择报表参数以及要从父报表传递给子报表中的报表参数的值。</span><span class="sxs-lookup"><span data-stu-id="edd82-125">When you place the subreport in the parent report, you can select the report parameter and a value to pass from the parent report to the report parameter in the subreport.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="edd82-126">从子报表中选择的参数是报表参数，而不是查询参数。</span><span class="sxs-lookup"><span data-stu-id="edd82-126">The parameter that you select from the subreport is a report parameter, not a query parameter.</span></span>  
  
 <span data-ttu-id="edd82-127">可以将子报表放入报表的主体或数据区域中。</span><span class="sxs-lookup"><span data-stu-id="edd82-127">You can place a subreport in the main body of the report, or in a data region.</span></span> <span data-ttu-id="edd82-128">如果将子报表放在数据区域中，则子报表将重复数据区域中的组或行的每个实例。</span><span class="sxs-lookup"><span data-stu-id="edd82-128">If you place a subreport in a data region, the subreport will repeat with each instance of the group or row in the data region.</span></span> <span data-ttu-id="edd82-129">若要将值从组或行传递给子报表，则在子报表值属性中，对于包含要传递给子报表参数的值的字段，请使用字段表达式。</span><span class="sxs-lookup"><span data-stu-id="edd82-129">To pass a value from the group or row to the subreport, in the subreport value property, use a field expression for the field containing the value you want to pass to the subreport parameter.</span></span>  
  
 <span data-ttu-id="edd82-130">有关使用子报表的详细信息，请参阅[添加子报表和参数（报表生成器和 SSRS）](add-a-subreport-and-parameters-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="edd82-130">For more information about working with subreports, see [Add a Subreport and Parameters &#40;Report Builder and SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md).</span></span>  
  
## <a name="specifying-subreport-names-and-locations"></a><span data-ttu-id="edd82-131">指定子报表的名称和位置</span><span class="sxs-lookup"><span data-stu-id="edd82-131">Specifying Subreport Names and Locations</span></span>  
 <span data-ttu-id="edd82-132">您可以设计一个主报表，将子报表的位置指定为同一报表服务器上的不同文件夹。</span><span class="sxs-lookup"><span data-stu-id="edd82-132">You can design a main report to specify a subreport in a different folder on the same report server.</span></span>  
  
 <span data-ttu-id="edd82-133">用于指定子报表的语法取决于报表服务器是处于本机模式还是 SharePoint 集成模式。</span><span class="sxs-lookup"><span data-stu-id="edd82-133">The syntax you use to specify the subreport depends on whether the report server is in native mode or SharePoint integrated mode.</span></span> <span data-ttu-id="edd82-134">有关详细信息，请参阅[指定外部项的路径（报表生成器和 SSRS）](specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="edd82-134">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="edd82-135">在报表生成器中，若要预览主报表中的子报表，这两个报表必须位于相同报表服务器中，否则必须指定子报表的完整路径。</span><span class="sxs-lookup"><span data-stu-id="edd82-135">In Report Builder, to preview a subreport in a main report, both reports must be located in the same report server, or you must specify a full path to the subreport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edd82-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="edd82-136">See Also</span></span>  
 [<span data-ttu-id="edd82-137">钻取、深化、子报表和嵌套数据区域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="edd82-137">Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;</span></span>](drillthrough-drilldown-subreports-and-nested-data-regions.md)  
  
  
