---
title: 在 MDX 查询设计器中为 Analysis Services (报表生成器和 SSRS) 定义参数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- parameters [Reporting Services], MDX
- Multidimensional Expressions [Reporting Services]
- Data Mining Prediction [Reporting Services]
- MDX [Reporting Services], defining parameters
- DMX [Reporting Services]
ms.assetid: 4ad1e5bc-f510-4752-b4f6-589e55317a90
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6b2b05fc0122eb25a7a0799f7b47b1b99486a28c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694282"
---
# <a name="define-parameters-in-the-mdx-query-designer-for-analysis-services-report-builder-and-ssrs"></a><span data-ttu-id="72a84-102">在 Analysis Services 的 MDX 查询设计器中定义参数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="72a84-102">Define Parameters in the MDX Query Designer for Analysis Services (Report Builder and SSRS)</span></span>
  <span data-ttu-id="72a84-103">若要参数化 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 数据源的 MDX 查询，则必须向查询添加查询参数。</span><span class="sxs-lookup"><span data-stu-id="72a84-103">To parameterize an MDX query for an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source, you must add a query parameter to the query.</span></span> <span data-ttu-id="72a84-104">在 MDX 查询设计器中，在设计模式和查询模式下都可以通过指定筛选器来添加查询参数。</span><span class="sxs-lookup"><span data-stu-id="72a84-104">In the MDX query designer, you can add a query parameter in both Design mode and Query mode by specifying a filter.</span></span> <span data-ttu-id="72a84-105">使用查询参数定义查询后，Reporting Services 会自动创建报表参数和数据集，以提供有效值的列表。</span><span class="sxs-lookup"><span data-stu-id="72a84-105">After you define the query with a query parameter, Reporting Services automatically creates a report parameter and a dataset to provide the list of valid values.</span></span> <span data-ttu-id="72a84-106">这样用户就可以指定要直接传递给查询的值。</span><span class="sxs-lookup"><span data-stu-id="72a84-106">This enables a user to specify a value that is passed directly to the query.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-define-a-query-parameter-in-mdx-in-design-mode"></a><span data-ttu-id="72a84-107">在设计模式下的 MDX 中定义查询参数</span><span class="sxs-lookup"><span data-stu-id="72a84-107">To define a query parameter in MDX in Design mode</span></span>

1.  <span data-ttu-id="72a84-108">在“报表数据”窗格中，右键单击从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 数据源类型创建的数据集，然后单击“查询”  。</span><span class="sxs-lookup"><span data-stu-id="72a84-108">In the Report Data pane, right-click on a dataset created from a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source type, and then click **Query**.</span></span> <span data-ttu-id="72a84-109">此时将在设计模式下打开 MDX 查询设计器。</span><span class="sxs-lookup"><span data-stu-id="72a84-109">The MDX query designer opens in Design mode.</span></span>

2.  <span data-ttu-id="72a84-110">将维度拖至筛选区域，然后将其放入 **“维度”** 列的第一个单元格中。</span><span class="sxs-lookup"><span data-stu-id="72a84-110">Drag a dimension to the filter area and drop it on the first cell in the **Dimension** column.</span></span>

3.  <span data-ttu-id="72a84-111">在“ **层次结构** ”列中，从下拉列表中选择一个值。</span><span class="sxs-lookup"><span data-stu-id="72a84-111">In the **Hierarchy** column, choose a value from the drop-down list.</span></span>

4.  <span data-ttu-id="72a84-112">在“ **运算符** ”列中，从下拉列表中选择一个运算符。</span><span class="sxs-lookup"><span data-stu-id="72a84-112">In the **Operator** column, choose an operator for the drop-down list.</span></span>

5.  <span data-ttu-id="72a84-113">在“ **筛选表达式** ”列中，从下拉列表中选择单个值，或单击“ **全部** ”成员选择所有值。</span><span class="sxs-lookup"><span data-stu-id="72a84-113">In the **Filter Expression** column, select individual values from the drop-down list, or click the **All** member to choose all values.</span></span>

6.  <span data-ttu-id="72a84-114">在 **“参数”** 列中，选择复选框以创建报表参数。</span><span class="sxs-lookup"><span data-stu-id="72a84-114">In the **Parameters** column, select the check box to create a report parameter.</span></span>

7.  <span data-ttu-id="72a84-115">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="72a84-115">Click **Run**.</span></span>

     <span data-ttu-id="72a84-116">运行查询后，单击工具栏中的 **“设计”** 可以切换到查询模式来查看所创建的 MDX 查询。</span><span class="sxs-lookup"><span data-stu-id="72a84-116">After you run the query, click **Design** on the toolbar to toggle to Query mode to view the MDX query that was created.</span></span> <span data-ttu-id="72a84-117">若要继续使用设计模式开发查询，请不要在查询模式下更改查询文本。</span><span class="sxs-lookup"><span data-stu-id="72a84-117">Do not change the query text in Query mode if you want to continue to use Design mode to develop the query.</span></span> <span data-ttu-id="72a84-118">单击 **“设计”** 可以切换回设计模式。</span><span class="sxs-lookup"><span data-stu-id="72a84-118">Click **Design** to toggle back to Design mode.</span></span>

8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

     <span data-ttu-id="72a84-119">在“报表数据”窗格中，展开“参数”节点以显示自动为筛选器创建的报表参数。</span><span class="sxs-lookup"><span data-stu-id="72a84-119">In the Report Data pane, expand the Parameters node to display the report parameter that was automatically created for the filter.</span></span>

     <span data-ttu-id="72a84-120">若要查看为报表参数提供可用值的数据集，请右键单击“报表数据”窗格中的任意空白区域，然后单击“ **显示隐藏的数据集**”。</span><span class="sxs-lookup"><span data-stu-id="72a84-120">To view the dataset that provides available values for the report parameter, right-click any blank area in the Report Data pane, and then click **Show Hidden Datasets**.</span></span> <span data-ttu-id="72a84-121">此时“报表数据”窗格将显示报表中的所有数据集。</span><span class="sxs-lookup"><span data-stu-id="72a84-121">The Report Data pane displays all datasets in the report.</span></span>

### <a name="to-define-a-query-parameter-in-mdx-in-query-mode"></a><span data-ttu-id="72a84-122">在查询模式下的 MDX 中定义查询参数</span><span class="sxs-lookup"><span data-stu-id="72a84-122">To define a query parameter in MDX in Query mode</span></span>

1.  <span data-ttu-id="72a84-123">在“报表数据”窗格中，右键单击从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 数据源类型创建的数据集，然后单击“查询”  。</span><span class="sxs-lookup"><span data-stu-id="72a84-123">In the Report Data pane, right-click on a dataset created from a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source type, and then click **Query**.</span></span> <span data-ttu-id="72a84-124">此时将在设计模式下打开 MDX 查询设计器。</span><span class="sxs-lookup"><span data-stu-id="72a84-124">The MDX query designer opens in Design mode.</span></span>

2.  <span data-ttu-id="72a84-125">在工具栏上单击 **“设计”** 以切换到查询模式。</span><span class="sxs-lookup"><span data-stu-id="72a84-125">On the toolbar, click **Design** to toggle to Query mode.</span></span>

3.  <span data-ttu-id="72a84-126">在 MDX 查询设计器工具栏上，单击“查询参数”  （![“查询参数”对话框图标](../../analysis-services/media/iconqueryparameter.gif "“查询参数”对话框图标")）。</span><span class="sxs-lookup"><span data-stu-id="72a84-126">On the MDX query designer toolbar, click **Query Parameters** (![Icon for the Query Parameters dialog box](../../analysis-services/media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")).</span></span> <span data-ttu-id="72a84-127">此时将打开“查询参数”对话框。</span><span class="sxs-lookup"><span data-stu-id="72a84-127">The Query Parameters dialog box opens.</span></span>

4.  <span data-ttu-id="72a84-128">在 "**参数**" 列中，单击 **\<Enter Parameter>** ""，然后键入参数的名称。</span><span class="sxs-lookup"><span data-stu-id="72a84-128">In the **Parameter** column, click **\<Enter Parameter>**, and then type the name of a parameter.</span></span>

5.  <span data-ttu-id="72a84-129">在“ **维度** ”列中，从下拉列表中选择一个值。</span><span class="sxs-lookup"><span data-stu-id="72a84-129">In the **Dimension** column, choose a value from the drop-down list.</span></span>

6.  <span data-ttu-id="72a84-130">在“ **层次结构** ”列中，从下拉列表中选择一个值。</span><span class="sxs-lookup"><span data-stu-id="72a84-130">In the **Hierarchy** column, choose a value from the drop-down list.</span></span>

7.  <span data-ttu-id="72a84-131">在 **“多个值”** 列中，选中复选框以创建多值参数。</span><span class="sxs-lookup"><span data-stu-id="72a84-131">In the **Multiple values** column, select the check box to create a multivalue parameter.</span></span>

8.  <span data-ttu-id="72a84-132">在“ **默认值** ”列中，根据步骤 5 中的选择，从下拉列表中选择一个值或多个值。</span><span class="sxs-lookup"><span data-stu-id="72a84-132">In the **Default** column, from the drop-down list, select a single value or multiple values depending on your choice in step 5.</span></span>

9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

10. <span data-ttu-id="72a84-133">在查询设计器工具栏中，单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="72a84-133">On the query designer toolbar, click **Run**.</span></span>

11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

     <span data-ttu-id="72a84-134">在“报表数据”窗格中，展开“参数”节点以显示自动为筛选器创建的报表参数。</span><span class="sxs-lookup"><span data-stu-id="72a84-134">In the Report Data pane, expand the Parameters node to display the report parameter that was automatically created for the filter.</span></span>

     <span data-ttu-id="72a84-135">若要查看为报表参数提供可用值的数据集，请右键单击“报表数据”窗格中的任意空白区域，然后单击“ **显示隐藏的数据集**”。</span><span class="sxs-lookup"><span data-stu-id="72a84-135">To view the dataset that provides available values for the report parameter, right-click any blank area in the Report Data pane, and then click **Show Hidden Datasets**.</span></span> <span data-ttu-id="72a84-136">此时“报表数据”窗格将显示报表中的所有数据集。</span><span class="sxs-lookup"><span data-stu-id="72a84-136">The Report Data pane displays all datasets in the report.</span></span>

## <a name="see-also"></a><span data-ttu-id="72a84-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72a84-137">See Also</span></span>
 <span data-ttu-id="72a84-138">[Mdx &#40;SSRS&#41;Analysis Services 连接类型](analysis-services-connection-type-for-mdx-ssrs.md) [Analysis Services Mdx 查询设计器用户界面](analysis-services-mdx-query-designer-user-interface.md)</span><span class="sxs-lookup"><span data-stu-id="72a84-138">[Analysis Services Connection Type for MDX &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md) [Analysis Services MDX Query Designer User Interface](analysis-services-mdx-query-designer-user-interface.md)</span></span>


