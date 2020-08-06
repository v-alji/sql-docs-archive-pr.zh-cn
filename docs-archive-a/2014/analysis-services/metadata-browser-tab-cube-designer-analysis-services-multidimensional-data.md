---
title: " (浏览器选项卡、多维数据集设计器)  (Analysis Services 多维数据) 的元数据 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.metadatapane.f1
ms.assetid: a1ace545-488d-4645-8330-56408a5e8abd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8093ac8cac8e3cd5a609e97b47ede89912897e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693138"
---
# <a name="metadata-browser-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="65a6a-102">元数据（“浏览器”选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="65a6a-102">Metadata (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="65a6a-103">在多维数据集设计器中，可以使用 **“浏览器”** 选项卡上的 **“元数据”** 窗格浏览多维数据集的结构，以查看相关度量值，以及查看和创建维度。</span><span class="sxs-lookup"><span data-stu-id="65a6a-103">Use the **Metadata** pane on the **Browser** tab in Cube Designer to browse the structure of the cube, to see related measures, and to view and create dimensions.</span></span> <span data-ttu-id="65a6a-104">您可以深化到层次结构中，查看可用度量值和 KPI 的列表，并复制对象的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="65a6a-104">You can drill down into hierarchies, view a list of available measures and KPIs, and copy the fully qualified names of objects.</span></span>  
  
 <span data-ttu-id="65a6a-105">还可以将 **“元数据”** 窗格中的对象和层次结构拖至查询生成区域，以创建新查询或导出数据以便在 Excel 中浏览。</span><span class="sxs-lookup"><span data-stu-id="65a6a-105">You can also drag the objects and hierarchies in the **Metadata** pane to the query building area, to create new queries or export data for browsing in Excel.</span></span>  
  
## <a name="options"></a><span data-ttu-id="65a6a-106">选项</span><span class="sxs-lookup"><span data-stu-id="65a6a-106">Options</span></span>  
 <span data-ttu-id="65a6a-107">Metadata</span><span class="sxs-lookup"><span data-stu-id="65a6a-107">**Metadata**</span></span>  
 <span data-ttu-id="65a6a-108">显示当前视图中可用的元数据。</span><span class="sxs-lookup"><span data-stu-id="65a6a-108">Displays the metadata available in the current view.</span></span> <span data-ttu-id="65a6a-109">可以更改该视图（即当前选定的透视或多维数据集），只需单击多维数据集图标，然后使用“选择多维数据集”\*\*\*\* 对话框选择新的多维数据集或透视。</span><span class="sxs-lookup"><span data-stu-id="65a6a-109">You can change the view (that is, the currently selected perspective or cube) by clicking the cube icon, and then using the **Cube Selection** dialog box to choose a new cube or perspective.</span></span> <span data-ttu-id="65a6a-110">还可以单击 **“度量值组”**，然后从下拉列表中选择新的度量值组，以便筛选在 **“元数据”** 窗格中可用的对象。</span><span class="sxs-lookup"><span data-stu-id="65a6a-110">You can also click **Measure Group**, and select a new measure group from the dropdown list to filter the objects that are available in the **Metadata** pane.</span></span>  
  
 <span data-ttu-id="65a6a-111">将所选项拖到 [!INCLUDE[msCoName](../includes/msconame-md.md)] “报表” **窗格中的** Office 11.0 数据透视表控件的筛选器、数据、行或列区域中，可以显示所选项的数据。</span><span class="sxs-lookup"><span data-stu-id="65a6a-111">Drag selected items to the filter, data, row, or column areas of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 11.0 PivotTable control in the **Report** pane to display the data for the selected item.</span></span>  
  
 <span data-ttu-id="65a6a-112">**函数**</span><span class="sxs-lookup"><span data-stu-id="65a6a-112">**Functions**</span></span>  
 <span data-ttu-id="65a6a-113">显示可用于在“浏览器”\*\*\*\* 中创建查询或数据视图的所有函数、运算符和常量的列表。</span><span class="sxs-lookup"><span data-stu-id="65a6a-113">Displays a list of all functions, operators, and constants that can be used to create queries or data views in the **Browser**.</span></span> <span data-ttu-id="65a6a-114">若要使用某个函数，找到所需的函数，然后将其拖入查询区域。</span><span class="sxs-lookup"><span data-stu-id="65a6a-114">To use a function, locate the one you want, and drag it into the query area.</span></span> <span data-ttu-id="65a6a-115">语法定义将添加到文本中。</span><span class="sxs-lookup"><span data-stu-id="65a6a-115">The syntax definition is added to the text</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="65a6a-116"> 在图形设计视图中工作时， **“函数”** 列表不可用。</span><span class="sxs-lookup"><span data-stu-id="65a6a-116">The **Function** list is not available when you are working in graphical design view.</span></span>  
  
 <span data-ttu-id="65a6a-117">当使用表格模型时，函数列表将包含 MDX 函数和 DAX 函数。</span><span class="sxs-lookup"><span data-stu-id="65a6a-117">When working with a tabular model, the list of functions includes both MDX functions and DAX functions.</span></span> <span data-ttu-id="65a6a-118">否则，该列表仅包含 MDX。</span><span class="sxs-lookup"><span data-stu-id="65a6a-118">Otherwise, the list includes only MDX.</span></span> <span data-ttu-id="65a6a-119">多维模型无法直接使用 DAX 函数，尽管可以在对象定义中包括 DAX 表达式。</span><span class="sxs-lookup"><span data-stu-id="65a6a-119">A multidimensional model cannot use DAX functions directly, although a DAX expression might be included as part of an object definition.</span></span>  
  
 <span data-ttu-id="65a6a-120">提示：包含 DAX 函数的文件夹以全大写字母列出。</span><span class="sxs-lookup"><span data-stu-id="65a6a-120">Tip: The folders that contain DAX functions are listed in all upper-case letters.</span></span> <span data-ttu-id="65a6a-121">所有其他文件夹包含的都是 MDX 函数。</span><span class="sxs-lookup"><span data-stu-id="65a6a-121">All other folders contain MDX functions.</span></span> <span data-ttu-id="65a6a-122">例如，有两个用于统计函数的文件夹： **STATISTICAL** 包含相关的 DAX 函数。</span><span class="sxs-lookup"><span data-stu-id="65a6a-122">For example, there are two folders for statistical functions: **STATISTICAL** contains the related DAX functions.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="65a6a-123">上下文菜单</span><span class="sxs-lookup"><span data-stu-id="65a6a-123">Context Menu</span></span>  
 <span data-ttu-id="65a6a-124">右键单击“元数据”\*\*\*\* 窗格中显示的元素，可以从所显示的上下文菜单中访问以下选项：</span><span class="sxs-lookup"><span data-stu-id="65a6a-124">The following options are available in the context menu displayed by right-clicking an element displayed in the **Metadata** pane:</span></span>  
  
|<span data-ttu-id="65a6a-125">选项</span><span class="sxs-lookup"><span data-stu-id="65a6a-125">Option</span></span>|<span data-ttu-id="65a6a-126">说明</span><span class="sxs-lookup"><span data-stu-id="65a6a-126">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="65a6a-127">**添加到查询**</span><span class="sxs-lookup"><span data-stu-id="65a6a-127">**Add to Query**</span></span>|<span data-ttu-id="65a6a-128">单击此选项可以将选定的对象添加到查询生成区域的下部窗格中。</span><span class="sxs-lookup"><span data-stu-id="65a6a-128">Click to add the selected object to the lower pane of the query building area.</span></span>|  
|<span data-ttu-id="65a6a-129">**添加到筛选器**</span><span class="sxs-lookup"><span data-stu-id="65a6a-129">**Add to Filter**</span></span>|<span data-ttu-id="65a6a-130">单击此选项可以将所选的维度、属性、层次结构或级别添加至 **“浏览器”** 的筛选区域。</span><span class="sxs-lookup"><span data-stu-id="65a6a-130">Click to add the selected dimension, attribute, hierarchy, or level to the filter area of the **Browser**.</span></span><br /><br /> <span data-ttu-id="65a6a-131">注意：只有在选择了维度、属性、层次结构或级别时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="65a6a-131">Note: This option is enabled only if a dimension, attribute, hierarchy, or level is selected.</span></span>|  
|<span data-ttu-id="65a6a-132">**复制**</span><span class="sxs-lookup"><span data-stu-id="65a6a-132">**Copy**</span></span>|<span data-ttu-id="65a6a-133">单击此选项可以将所选项添加到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="65a6a-133">Click to add the selected item to the Clipboard.</span></span><br /><br /> <span data-ttu-id="65a6a-134">注意：此选项复制对象的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="65a6a-134">Note: This option copies the fully qualified name of the object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65a6a-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65a6a-135">See Also</span></span>  
 <span data-ttu-id="65a6a-136">[工具栏 &#40;浏览器选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="65a6a-136">[Toolbar &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="65a6a-137">[在 Excel &#40;浏览器选项卡、多维数据集设计器&#41; &#40;Analysis Services 多维数据中分析&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="65a6a-137">[Analyze in Excel &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="65a6a-138">[查询和筛选 &#40;浏览器选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="65a6a-138">[Query and Filter &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="65a6a-139">浏览器 &#40;多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="65a6a-139">Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browser-cube-designer-analysis-services-multidimensional-data.md)  
  
  
