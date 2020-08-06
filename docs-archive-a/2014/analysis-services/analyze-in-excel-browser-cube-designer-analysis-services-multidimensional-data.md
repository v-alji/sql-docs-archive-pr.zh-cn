---
title: 在 Excel 中分析 (浏览器选项卡、多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.datapane.f1
- sql12.asvs.ssms.analyzeinexcel.f1
ms.assetid: 890ed457-137e-44ac-9b2c-83344a1b8fc9
author: minewiskan
ms.author: owend
ms.openlocfilehash: b9fa27ae291d40b7f5637e3968438fcaec1de03d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579380"
---
# <a name="analyze-in-excel-browser-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="0444b-102">在 Excel 中分析（“浏览器”选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="0444b-102">Analyze in Excel (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="0444b-103">**“在 Excel 中分析”** 为多维数据集开发人员提供了一种快速检查项目将如何呈现给最终用户的方式。</span><span class="sxs-lookup"><span data-stu-id="0444b-103">**Analyze in Excel** provides the cube developer with a way to quickly review how a project would look to the end user.</span></span> <span data-ttu-id="0444b-104">使用 **“在 Excel 中分析”** 功能可以打开 Microsoft Excel、创建到模型工作区数据库的数据源连接，以及自动将数据透视表添加到工作表。</span><span class="sxs-lookup"><span data-stu-id="0444b-104">The **Analyze in Excel** feature opens Microsoft Excel, creates a data source connection to the workspace database, and automatically adds a PivotTable to the worksheet.</span></span> <span data-ttu-id="0444b-105">此功能将取代 Office Web Control，后者在以前版本的“浏览器”选项卡中提供了一个嵌入的数据透视表。</span><span class="sxs-lookup"><span data-stu-id="0444b-105">This feature replaces the Office Web Control that provided an embedded PivotTable in the Browser tab in previous releases.</span></span>  
  
 <span data-ttu-id="0444b-106">**查看多维数据集数据：**</span><span class="sxs-lookup"><span data-stu-id="0444b-106">**To view cube data:**</span></span>  
  
1.  <span data-ttu-id="0444b-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]的解决方案资源管理器中，双击某一多维数据集以在多维数据集设计器中打开它。</span><span class="sxs-lookup"><span data-stu-id="0444b-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], in Solution Explorer, double-click a cube to open it in Cube Designer.</span></span>  
  
2.  <span data-ttu-id="0444b-108">单击 **“浏览器”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="0444b-108">Click the **Browser** tab.</span></span>  
  
3.  <span data-ttu-id="0444b-109">单击 **“重新连接”** 以便对连接进行验证。</span><span class="sxs-lookup"><span data-stu-id="0444b-109">Click **Reconnect** to validate the connection.</span></span>  
  
4.  <span data-ttu-id="0444b-110">单击菜单栏中的 Excel 图标。</span><span class="sxs-lookup"><span data-stu-id="0444b-110">Click the Excel icon in the menu bar.</span></span>  
  
5.  <span data-ttu-id="0444b-111">在系统提示您启用数据连接时，单击 **“启用”**。</span><span class="sxs-lookup"><span data-stu-id="0444b-111">When asked to enable data connections, click **Enable**.</span></span> <span data-ttu-id="0444b-112">Excel 将使用当前数据连接打开，并且向电子表格中添加一个数据透视表，以便您可以开始浏览数据。</span><span class="sxs-lookup"><span data-stu-id="0444b-112">Excel opens using the current data connection, adding a PivotTable to the worksheet so that you can begin browsing your data.</span></span>  
  
 <span data-ttu-id="0444b-113">您可以通过将度量值从事实表拖到“值”区域，并且将维度属性拖到“行”和“列”区域，以交互方式生成数据透视表。</span><span class="sxs-lookup"><span data-stu-id="0444b-113">You can now build a PivotTable interactively by dragging measures from the fact table to the Values area, and dimension attributes to the Row and Column areas.</span></span> <span data-ttu-id="0444b-114">如果您具有层次结构，则将它们添加到“行”和“列”区域。</span><span class="sxs-lookup"><span data-stu-id="0444b-114">If you have hierarchies, add them to Rows or Column areas.</span></span> <span data-ttu-id="0444b-115">您可以汇总或深化层次结构，以便在不同级别浏览事实数据。</span><span class="sxs-lookup"><span data-stu-id="0444b-115">You can roll up or drill down the hierarchy to browse fact data at different levels.</span></span>  
  
 <span data-ttu-id="0444b-116">在有效用户或角色的上下文以及透视中查看对象和数据。</span><span class="sxs-lookup"><span data-stu-id="0444b-116">Objects and data are viewed within the context of the effective user or role and perspective.</span></span> <span data-ttu-id="0444b-117">在使用 Excel 时，默认情况下，在执行查询时，当前用户的凭据（而非在 **“模拟信息”** 页中指定的凭据）用于连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="0444b-117">When using Excel, the credentials of the current user, not the credentials specified in the **Impersonation Information** page, are used to connect to the data source when a query is executed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0444b-118">为了使用“在 Excel 中分析”功能，Excel 必须与 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]安装在同一台计算机上。</span><span class="sxs-lookup"><span data-stu-id="0444b-118">To use the Analyze in Excel feature, Excel must be installed on the same computer as [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="0444b-119">如果 Excel 安装在不同的计算机上，您可以在另一计算机上使用 Excel 并连接到作为数据源的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="0444b-119">If Excel is not installed on the same computer, you can use Excel on another computer and connect to the cube as a data source.</span></span> <span data-ttu-id="0444b-120">然后可以将数据透视表手动添加到工作表。</span><span class="sxs-lookup"><span data-stu-id="0444b-120">You can then manually add a PivotTable to the worksheet.</span></span> <span data-ttu-id="0444b-121">模型对象（表、列、度量值和 KPI）作为数据透视表字段列表中的字段包含。</span><span class="sxs-lookup"><span data-stu-id="0444b-121">Model objects (tables, columns, measures, and KPIs) are included as fields in the PivotTable field list.</span></span>  
  
 <span data-ttu-id="0444b-122">有关 **“在 Excel 中分析”** 功能的详细信息，请参阅以下资源：</span><span class="sxs-lookup"><span data-stu-id="0444b-122">For more information about the **Analyze in Excel** feature, see these resources:</span></span>  
  
 [<span data-ttu-id="0444b-123">在 Excel 中分析（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="0444b-123">Analyze in Excel &#40;SSAS Tabular&#41;</span></span>](tabular-models/analyze-in-excel-ssas-tabular.md)  
  
 [<span data-ttu-id="0444b-124">在 Excel 中分析表格模型（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="0444b-124">Analyze a Tabular Model in Excel &#40;SSAS Tabular&#41;</span></span>](tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)  
  
 [<span data-ttu-id="0444b-125">浏览多维数据集中的数据和元数据</span><span class="sxs-lookup"><span data-stu-id="0444b-125">Browse data and metadata in Cube</span></span>](multidimensional-models/browse-data-and-metadata-in-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="0444b-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0444b-126">See Also</span></span>  
 <span data-ttu-id="0444b-127">[浏览器 &#40;多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="0444b-127">[Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="0444b-128">[工具栏 &#40;浏览器选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="0444b-128">[Toolbar &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="0444b-129">[元数据 &#40;浏览器选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="0444b-129">[Metadata &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="0444b-130">查询和筛选 &#40;浏览器选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="0444b-130">Query and Filter &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md)  
  
  
