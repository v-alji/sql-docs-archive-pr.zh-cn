---
title: 浏览多维数据集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3819946e-d3fa-4c1d-afe3-599c938b1b2e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7cbf35866bb0a1f65074a7e106ecf556e98aa30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577012"
---
# <a name="browsing-the-cube"></a><span data-ttu-id="c3ddb-102">浏览多维数据集</span><span class="sxs-lookup"><span data-stu-id="c3ddb-102">Browsing the Cube</span></span>
  <span data-ttu-id="c3ddb-103">在部署多维数据集后，可以在多维数据集设计器的“浏览器”\*\*\*\* 选项卡中查看多维数据集数据，以及在维度设计器的“浏览器”\*\*\*\* 选项卡中查看维度数据。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-103">After you deploy a cube, the cube data is viewable on the **Browser** tab in Cube Designer, and the dimension data is viewable on the **Browser** tab in Dimension Designer.</span></span> <span data-ttu-id="c3ddb-104">浏览多维数据集和维度数据是以增量方式检查您的工作的方式。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-104">Browsing cube and dimension data is way to check your work incrementally.</span></span> <span data-ttu-id="c3ddb-105">您可以在处理对象后，验证对属性、关系和其他对象的细微更改是否具有期望的效果。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-105">You can verify that small changes to properties, relationships, and other objects have the desired effect once the object is processed.</span></span> <span data-ttu-id="c3ddb-106">在使用“浏览器”选项卡来查看多维数据集和维度数据时，该选项卡将基于您正在浏览的对象提供不同的功能。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-106">While the Browser tab is used to view both cube and dimension data, the tab provides different capabilities based on the object you are browsing.</span></span>  
  
 <span data-ttu-id="c3ddb-107">对于维度，“浏览器”选项卡提供一个方法来查看成员或导航层次结构，可一直向下到叶节点。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-107">For dimensions, the Browser tab provides a way to view members or navigate a hierarchy all the way down to the leaf node.</span></span> <span data-ttu-id="c3ddb-108">您可以通过不同语言浏览维度数据，假定您已将翻译添加到您的模型中。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-108">You can browse dimension data in different languages, assuming you have added the translations to your model.</span></span>  
  
 <span data-ttu-id="c3ddb-109">对于多维数据集，“浏览器”选项卡提供了两种用于浏览数据的方法。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-109">For cubes, the Browser tab provides two approaches for exploring data.</span></span> <span data-ttu-id="c3ddb-110">您可以使用内置 MDX 查询设计器生成从多维数据库返回平展行集的查询。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-110">You can use the built-in MDX Query Designer to build queries that return a flattened rowset from a multidimensional database.</span></span> <span data-ttu-id="c3ddb-111">或者，您可以使用 Excel 快捷方式。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-111">Alternatively, you can use an Excel shortcut.</span></span> <span data-ttu-id="c3ddb-112">当您从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]内启动 Excel 时，Excel 将打开，并且在工作表中已有数据透视表以及与模型工作区数据库的预定义连接。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-112">When you start Excel from within [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], Excel opens with a PivotTable already in the worksheet and a predefined connection to the model workspace database.</span></span>  
  
 <span data-ttu-id="c3ddb-113">Excel 通常会提供更好的浏览体验，因为您可以交互方式浏览多维数据集数据，并且使用水平轴和垂直轴来分析数据中的关系。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-113">Excel generally offers a better browsing experience because you can explore cube data interactively, using horizontal and vertical axes to analyze the relationships in your data.</span></span> <span data-ttu-id="c3ddb-114">相比之下，MDX 查询设计器局限于单个轴。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-114">In contrast, the MDX Query Designer is limited to a single axis.</span></span> <span data-ttu-id="c3ddb-115">此外，因为行集将被平展，所以，您无法获得 Excel 数据透视表提供的深入分析。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-115">Moreover, because the rowset is flattened, you do not get the drilldown that an Excel PivotTable provides.</span></span> <span data-ttu-id="c3ddb-116">随着您向多维数据集添加更多的维度和层次结构（在以后的课程中将会这样做），对于浏览数据而言，Excel 将是首选解决方案。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-116">As you add more dimensions and hierarchies to your cube, which you will do in subsequent lessons, Excel will be the preferred solution for browsing data.</span></span>  
  
### <a name="to-browse-the-deployed-cube"></a><span data-ttu-id="c3ddb-117">浏览部署的多维数据集</span><span class="sxs-lookup"><span data-stu-id="c3ddb-117">To browse the deployed cube</span></span>  
  
1.  <span data-ttu-id="c3ddb-118">切换到 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的“产品”维度的“维度设计器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-118">Switch to **Dimension Designer** for the Product dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="c3ddb-119">为此，请双击解决方案资源管理器的“维度”\*\*\*\* 节点的“产品”\*\*\*\* 维度。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-119">To do this, double-click the **Product** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="c3ddb-120">单击 "**浏览器**" 选项卡以显示属性层次结构的 "**所有**" 成员 `Product Key` 。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-120">Click the **Browser** tab to display the **All** member of the `Product Key` attribute hierarchy.</span></span> <span data-ttu-id="c3ddb-121">在第 3 课中，你将定义“产品”维度的用户层次结构，利用此结构可浏览该维度。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-121">In lesson three, you will define a user hierarchy for the Product dimension that will let you browse the dimension.</span></span>  
  
3.  <span data-ttu-id="c3ddb-122">切换到 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的“多维数据集设计器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-122">Switch to **Cube Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="c3ddb-123">为此，请双击解决方案资源管理器的 "**多维数据集**" 节点中的**Analysis Services 教程**多维数据集。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-123">To do this, double-click the **Analysis Services Tutorial** cube in the **Cubes** node of Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="c3ddb-124">选择“浏览器”\*\*\*\* 选项卡，然后在设计器的工具栏上单击“重新连接”\*\*\*\* 图标。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-124">Select the **Browser** tab, and then click the **Reconnect** icon on the toolbar of the designer.</span></span>  
  
     <span data-ttu-id="c3ddb-125">该设计器的左窗格会显示 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集中的对象。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-125">The left pane of the designer shows the objects in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="c3ddb-126">在“浏览器”\*\*\*\* 选项卡的右侧有两个窗格：上部窗格是“筛选器”\*\*\*\* 窗格，下部是“数据”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-126">On the right side of the **Browser** tab, there are two panes: the upper pane is the **Filter** pane, and the lower pane is the **Data** pane.</span></span> <span data-ttu-id="c3ddb-127">在接下来的课程中，您将使用多维数据集浏览器进行分析。</span><span class="sxs-lookup"><span data-stu-id="c3ddb-127">In an upcoming lesson, you will use the cube browser to do analysis.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="c3ddb-128">下一课</span><span class="sxs-lookup"><span data-stu-id="c3ddb-128">Next Lesson</span></span>  
 [<span data-ttu-id="c3ddb-129">第 3 课：修改度量值、属性和层次结构</span><span class="sxs-lookup"><span data-stu-id="c3ddb-129">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>](lesson-3-modifying-measures-attributes-and-hierarchies.md)  
  
## <a name="see-also"></a><span data-ttu-id="c3ddb-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3ddb-130">See Also</span></span>  
 [<span data-ttu-id="c3ddb-131">MDX 查询编辑器（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="c3ddb-131">MDX Query Editor &#40;Analysis Services - Multidimensional Data&#41;</span></span>](mdx-query-editor-analysis-services-multidimensional-data.md)  
  
  
