---
title: 定义多维数据集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8aa4ac2d-857f-4048-baa0-0f314e207cf6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 354a05840dd2e091f956454858edd5c75c8c4bdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577024"
---
# <a name="defining-a-cube"></a><span data-ttu-id="7209f-102">定义多维数据集</span><span class="sxs-lookup"><span data-stu-id="7209f-102">Defining a Cube</span></span>
  <span data-ttu-id="7209f-103">多维数据集向导可以帮助您为多维数据集定义度量值组和维度。</span><span class="sxs-lookup"><span data-stu-id="7209f-103">The Cube Wizard helps you define the measure groups and dimensions for a cube.</span></span> <span data-ttu-id="7209f-104">在下面的任务中，将使用维度向导来构建多维数据集。</span><span class="sxs-lookup"><span data-stu-id="7209f-104">In the following task, you will use the Cube Wizard to build a cube.</span></span>  
  
### <a name="to-define-a-cube-and-its-properties"></a><span data-ttu-id="7209f-105">定义多维数据集及其属性</span><span class="sxs-lookup"><span data-stu-id="7209f-105">To define a cube and its properties</span></span>  
  
1.  <span data-ttu-id="7209f-106">在解决方案资源管理器中，右键单击“多维数据集”\*\*\*\*，然后单击“新建多维数据集”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7209f-106">In Solution Explorer, right-click **Cubes**, and then click **New Cube**.</span></span> <span data-ttu-id="7209f-107">多维数据集向导将显示。</span><span class="sxs-lookup"><span data-stu-id="7209f-107">The Cube Wizard appears.</span></span>  
  
2.  <span data-ttu-id="7209f-108">在“欢迎使用多维数据集向导”\*\*\*\* 页上，单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7209f-108">On the **Welcome to the Cube Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="7209f-109">在“选择创建方法”\*\*\*\* 页上，确认已选中“使用现有表”\*\*\*\* 选项，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7209f-109">On the **Select Creation Method** page, verify that the **Use existing tables** option is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="7209f-110">在“选择度量值组表”\*\*\*\* 页上，确认已选中“Adventure Works DW 2012”\*\*\*\* 数据源视图。</span><span class="sxs-lookup"><span data-stu-id="7209f-110">On the **Select Measure Group Tables** page, verify that the **Adventure Works DW 2012** data source view is selected.</span></span>  
  
5.  <span data-ttu-id="7209f-111">单击“建议”\*\*\*\* 允许多维数据集向导建议要用来创建度量值组的表。</span><span class="sxs-lookup"><span data-stu-id="7209f-111">Click **Suggest** to have the cube wizard suggest tables to use to create measure groups.</span></span>  
  
     <span data-ttu-id="7209f-112">该向导会检查这些表并建议将 **InternetSales** 作为度量值组表。</span><span class="sxs-lookup"><span data-stu-id="7209f-112">The wizard examines the tables and suggests **InternetSales** as a measure group table.</span></span> <span data-ttu-id="7209f-113">度量值组表（又称为事实数据表）包含你感兴趣的度量值（如已销售的单位数）。</span><span class="sxs-lookup"><span data-stu-id="7209f-113">Measure group tables, also called fact tables, contain the measures you are interested in, such as the number of units sold.</span></span>  
  
6.  <span data-ttu-id="7209f-114">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="7209f-114">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="7209f-115">在“选择度量值”\*\*\*\* 页上，查看在“Internet 销售”\*\*\*\* 度量值组中选择的度量值，然后清除下列度量值的复选框：</span><span class="sxs-lookup"><span data-stu-id="7209f-115">On the **Select Measures** page, review the selected measures in the **Internet Sales** measure group, and then clear the check boxes for the following measures:</span></span>  
  
    -   <span data-ttu-id="7209f-116">**促销关键字**</span><span class="sxs-lookup"><span data-stu-id="7209f-116">**Promotion Key**</span></span>  
  
    -   <span data-ttu-id="7209f-117">**货币关键字**</span><span class="sxs-lookup"><span data-stu-id="7209f-117">**Currency Key**</span></span>  
  
    -   <span data-ttu-id="7209f-118">**销售区域关键字**</span><span class="sxs-lookup"><span data-stu-id="7209f-118">**Sales Territory Key**</span></span>  
  
    -   <span data-ttu-id="7209f-119">**修订号**</span><span class="sxs-lookup"><span data-stu-id="7209f-119">**Revision Number**</span></span>  
  
     <span data-ttu-id="7209f-120">默认情况下，该向导会选择将事实数据表中未链接到维度的所有数值列作为度量值。</span><span class="sxs-lookup"><span data-stu-id="7209f-120">By default, the wizard selects as measures all numeric columns in the fact table that are not linked to dimensions.</span></span> <span data-ttu-id="7209f-121">但这四列不是实际的度量值。</span><span class="sxs-lookup"><span data-stu-id="7209f-121">However, these four columns are not actual measures.</span></span> <span data-ttu-id="7209f-122">前三列是将事实数据表与未在此多维数据集的初始版本中使用的维度表链接起来的键值。</span><span class="sxs-lookup"><span data-stu-id="7209f-122">The first three are key values that link the fact table with dimension tables that are not used in the initial version of this cube.</span></span>  
  
8.  <span data-ttu-id="7209f-123">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="7209f-123">Click **Next**.</span></span>  
  
9. <span data-ttu-id="7209f-124">在“选择现有维度”\*\*\*\* 页上，确保选择了以前创建的“日期”\*\*\*\* 维度，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7209f-124">On the **Select Existing Dimensions** page, make sure the **Date** dimension that you created earlier is selected, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="7209f-125">在“选择新维度”\*\*\*\* 页上，选择要创建的新维度。</span><span class="sxs-lookup"><span data-stu-id="7209f-125">On the **Select New Dimensions** page, select the new dimensions to be created.</span></span> <span data-ttu-id="7209f-126">为此，请确认已选中“客户”\*\*\*\*、“地域”\*\*\*\* 和“产品”\*\*\*\* 复选框，然后清除“InternetSales”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="7209f-126">To do this, verify that the **Customer**, **Geography**, and **Product** check boxes are selected, and then clear the **InternetSales** check box.</span></span>  
  
11. <span data-ttu-id="7209f-127">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="7209f-127">Click **Next**.</span></span>  
  
12. <span data-ttu-id="7209f-128">在 "**完成向导**" 页上，将多维数据集的名称更改为 `Analysis Services Tutorial` 。</span><span class="sxs-lookup"><span data-stu-id="7209f-128">On the **Completing the Wizard** page, change the name of the cube to `Analysis Services Tutorial`.</span></span> <span data-ttu-id="7209f-129">在“预览”窗格中，可以看到 **InternetSales** 度量值组及其度量值。</span><span class="sxs-lookup"><span data-stu-id="7209f-129">In the Preview pane, you can see the **InternetSales** measure group and its measures.</span></span> <span data-ttu-id="7209f-130">还可以看到“日期”\*\*\*\*、“客户”\*\*\*\* 和“产品”\*\*\*\* 维度。</span><span class="sxs-lookup"><span data-stu-id="7209f-130">You can also see the **Date**, **Customer,** and **Product** dimensions.</span></span>  
  
13. <span data-ttu-id="7209f-131">单击 **“完成”** 以完成向导。</span><span class="sxs-lookup"><span data-stu-id="7209f-131">Click **Finish** to complete the wizard.</span></span>  
  
     <span data-ttu-id="7209f-132">在解决方案资源管理器的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 项目中，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集显示在“多维数据集”\*\*\*\* 文件夹中，而“客户”和“产品”数据库维度则显示在“维度”\*\*\*\* 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="7209f-132">In Solution Explorer, in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube appears in the **Cubes** folder, and the Customer and Product database dimensions appear in the **Dimensions** folder.</span></span> <span data-ttu-id="7209f-133">此外，“多维数据集结构”选项卡在开发环境的中央显示 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="7209f-133">Additionally, in the center of the development environment, the Cube Structure tab displays the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
14. <span data-ttu-id="7209f-134">在“多维数据集结构”选项卡的工具栏上，将“缩放”\*\*\*\* 级别更改为 50 %，以便更轻松地查看多维数据集内的维度和事实数据表。</span><span class="sxs-lookup"><span data-stu-id="7209f-134">On the toolbar of the Cube Structure tab, change the **Zoom** level to 50 percent, so that you can more easily see the dimensions and fact tables in the cube.</span></span> <span data-ttu-id="7209f-135">注意，事实数据表是黄色的，维度表是蓝色的。</span><span class="sxs-lookup"><span data-stu-id="7209f-135">Notice that the fact table is yellow and the dimension tables are blue.</span></span>  
  
15. <span data-ttu-id="7209f-136">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="7209f-136">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="7209f-137">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="7209f-137">Next Task in Lesson</span></span>  
 [<span data-ttu-id="7209f-138">向维度添加属性</span><span class="sxs-lookup"><span data-stu-id="7209f-138">Adding Attributes to Dimensions</span></span>](lesson-2-3-adding-attributes-to-dimensions.md)  
  
## <a name="see-also"></a><span data-ttu-id="7209f-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7209f-139">See Also</span></span>  
 <span data-ttu-id="7209f-140">[多维模型中的多维数据集](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="7209f-140">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="7209f-141">多维模型中的维度</span><span class="sxs-lookup"><span data-stu-id="7209f-141">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
