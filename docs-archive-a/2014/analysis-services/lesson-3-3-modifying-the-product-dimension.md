---
title: 修改 "产品" 维度 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8e3ffecd-7f40-41a8-8735-bc9858a310cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 04c0a778a73371dada92c9ff207a17366a2fbc7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588133"
---
# <a name="modifying-the-product-dimension"></a><span data-ttu-id="377af-102">修改“产品”维度</span><span class="sxs-lookup"><span data-stu-id="377af-102">Modifying the Product Dimension</span></span>
  <span data-ttu-id="377af-103">在本主题下的任务中，将使用命名计算为产品系列提供更具说明性的名称，在“产品”维度中定义一个层次结构，并为该层次结构指定“(全部)”成员名称。</span><span class="sxs-lookup"><span data-stu-id="377af-103">In the tasks in this topic, you use a named calculation to provide more descriptive names for the product lines, define a hierarchy in the Product dimension, and specify the (All) member name for the hierarchy.</span></span> <span data-ttu-id="377af-104">还可以按显示文件夹组合各个属性。</span><span class="sxs-lookup"><span data-stu-id="377af-104">You also group attributes into display folders.</span></span>  
  
## <a name="adding-a-named-calculation"></a><span data-ttu-id="377af-105">添加命名计算</span><span class="sxs-lookup"><span data-stu-id="377af-105">Adding a Named Calculation</span></span>  
 <span data-ttu-id="377af-106">您可以向数据源视图内的表中添加命名计算。</span><span class="sxs-lookup"><span data-stu-id="377af-106">You can add a named calculation to a table in a data source view.</span></span> <span data-ttu-id="377af-107">在下面的任务中，将创建一个用来显示产品系列完整名称的命名计算。</span><span class="sxs-lookup"><span data-stu-id="377af-107">In the following task, you create a named calculation that displays the full product line name.</span></span>  
  
#### <a name="to-add-a-named-calculation"></a><span data-ttu-id="377af-108">添加命名计算</span><span class="sxs-lookup"><span data-stu-id="377af-108">To add a named calculation</span></span>  
  
1.  <span data-ttu-id="377af-109">若要打开“Adventure Works DW 2012”\*\*\*\* 数据源视图，请在解决方案资源管理器中的“数据源视图”\*\*\*\* 文件夹中双击“Adventure Works DW 2012”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="377af-109">To open the **Adventure Works DW 2012** data source view, double-click **Adventure Works DW 2012** in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="377af-110">在关系图窗格的底部，右键单击“Product”\*\*\*\* 表标题，然后单击“新建命名计算”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="377af-110">In the bottom of the diagram pane, right-click the **Product** table header, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="377af-111">在 "**创建命名计算**" 对话框中，在 `ProductLineName` "**列名称**" 框中键入。</span><span class="sxs-lookup"><span data-stu-id="377af-111">In the **Create Named Calculation** dialog box, type `ProductLineName` in the **Column name** box.</span></span>  
  
4.  <span data-ttu-id="377af-112">在“表达式”\*\*\*\* 框中，键入或复制并粘贴下面的 **CASE** 语句：</span><span class="sxs-lookup"><span data-stu-id="377af-112">In the **Expression** box, type or copy and paste the following **CASE** statement:</span></span>  
  
    ```  
    CASE ProductLine  
       WHEN 'M' THEN 'Mountain'  
       WHEN 'R' THEN 'Road'  
       WHEN 'S' THEN 'Accessory'  
       WHEN 'T' THEN 'Touring'  
       ELSE 'Components'  
    END  
    ```  
  
     <span data-ttu-id="377af-113">此 **CASE** 语句可以为多维数据集内的每个产品系列创建用户友好的名称。</span><span class="sxs-lookup"><span data-stu-id="377af-113">This **CASE** statement creates user-friendly names for each product line in the cube.</span></span>  
  
5.  <span data-ttu-id="377af-114">单击 **"确定"** 以创建 `ProductLineName` 命名计算。</span><span class="sxs-lookup"><span data-stu-id="377af-114">Click **OK** to create the `ProductLineName` named calculation.</span></span> <span data-ttu-id="377af-115">您可能需要等待。</span><span class="sxs-lookup"><span data-stu-id="377af-115">You might need to wait.</span></span>  
  
6.  <span data-ttu-id="377af-116">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="377af-116">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="modifying-the-namecolumn-property-of-an-attribute"></a><span data-ttu-id="377af-117">修改某个特性的 NameColumn 属性</span><span class="sxs-lookup"><span data-stu-id="377af-117">Modifying the NameColumn Property of an Attribute</span></span>  
  
#### <a name="to-modify-the-namecolumn-property-value-of-an-attribute"></a><span data-ttu-id="377af-118">修改某个特性的 NameColumn 属性值</span><span class="sxs-lookup"><span data-stu-id="377af-118">To modify the NameColumn property value of an attribute</span></span>  
  
1.  <span data-ttu-id="377af-119">切换到“产品”维度的维度设计器。</span><span class="sxs-lookup"><span data-stu-id="377af-119">Switch to Dimension Designer for the Product dimension.</span></span> <span data-ttu-id="377af-120">为此，请双击解决方案资源管理器的“维度”\*\*\*\* 节点的“产品”\*\*\*\* 维度。</span><span class="sxs-lookup"><span data-stu-id="377af-120">To do this, double-click the **Product** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="377af-121">在“维度结构”\*\*\*\* 选项卡的“属性”\*\*\*\* 窗格中，选择“产品系列”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="377af-121">In the **Attributes** pane of the **Dimension Structure** tab, select **Product Line**.</span></span>  
  
3.  <span data-ttu-id="377af-122">在屏幕右侧的 "属性窗口中，单击窗口底部的**NameColumn**属性字段，然后单击" 浏览 (**...** ") 按钮以打开"**名称列**"对话框。</span><span class="sxs-lookup"><span data-stu-id="377af-122">In the Properties window on the right side of the screen, click the **NameColumn** property field at the bottom of the window, and then click the browse (**...**) button to open the **Name Column** dialog box.</span></span> <span data-ttu-id="377af-123">（可能需要单击屏幕右侧的“属性”\*\*\*\* 选项卡以打开“属性”窗口。）</span><span class="sxs-lookup"><span data-stu-id="377af-123">(You might need to click the **Properties** tab on the right side of the screen to open the Properties window.</span></span>  
  
4.  <span data-ttu-id="377af-124">选择 " `ProductLineName` **源列**" 列表底部，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="377af-124">Select `ProductLineName` at the bottom of the **Source column** list, and then click **OK**.</span></span>  
  
     <span data-ttu-id="377af-125">“NameColumn”字段现包含 **Product.ProductLineName (WChar)** 文本。</span><span class="sxs-lookup"><span data-stu-id="377af-125">The NameColumn field now contains the text, **Product.ProductLineName (WChar)**.</span></span> <span data-ttu-id="377af-126">“产品系列”\*\*\*\* 属性层次结构的成员现将显示产品系列的完整名称，而不会显示缩写形式的产品系列名称。</span><span class="sxs-lookup"><span data-stu-id="377af-126">The members of the **Product Line** attribute hierarchy now display the full name of the product line instead of an abbreviated product line name.</span></span>  
  
5.  <span data-ttu-id="377af-127">在“维度结构”\*\*\*\* 选项卡的“属性”\*\*\*\* 窗格中，选择“产品密钥”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="377af-127">In the **Attributes** pane of the **Dimension Structure** tab, select **Product Key**.</span></span>  
  
6.  <span data-ttu-id="377af-128">在属性窗口中，单击 " **NameColumn** " 属性字段，然后单击省略号 "浏览 (**...**) " 按钮以打开 "**名称列**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="377af-128">In the Properties window, click the **NameColumn** property field, and then click the ellipsis browse (**...**) button to open the **Name Column** dialog box.</span></span>  
  
7.  <span data-ttu-id="377af-129">选择“源列”\*\*\*\* 列表中的“EnglishProductName”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="377af-129">Select **EnglishProductName** in the **Source column** list, and then click **OK**.</span></span>  
  
     <span data-ttu-id="377af-130">“NameColumn”字段现包含 **Product.EnglishProductName (WChar)** 文本。</span><span class="sxs-lookup"><span data-stu-id="377af-130">The NameColumn field now contains the text, **Product.EnglishProductName (WChar)**.</span></span>  
  
8.  <span data-ttu-id="377af-131">在属性窗口中，向上滚动，单击 "**名称**" 属性字段，然后键入 `Product Name` 。</span><span class="sxs-lookup"><span data-stu-id="377af-131">In the Properties window, scroll up, click the **Name** property field, and then type `Product Name`.</span></span>  
  
## <a name="creating-a-hierarchy"></a><span data-ttu-id="377af-132">创建层次结构</span><span class="sxs-lookup"><span data-stu-id="377af-132">Creating a Hierarchy</span></span>  
  
#### <a name="to-create-a-hierarchy"></a><span data-ttu-id="377af-133">创建层次结构</span><span class="sxs-lookup"><span data-stu-id="377af-133">To create a hierarchy</span></span>  
  
1.  <span data-ttu-id="377af-134">将“产品系列”\*\*\*\* 属性从“属性”\*\*\*\* 窗格拖到“层次结构”\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="377af-134">Drag the **Product Line** attribute from the **Attributes** pane into the **Hierarchies** pane.</span></span>  
  
2.  <span data-ttu-id="377af-135">将“产品系列”\*\*\*\* 级别下方的“型号名称”\*\*\*\* 属性从“属性”\*\*\*\* 窗格拖到“层次结构”\*\*\*\* 窗格的“\<new level>”\*\*\*\* 单元中。</span><span class="sxs-lookup"><span data-stu-id="377af-135">Drag the **Model Name** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Product Line** level.</span></span>  
  
3.  <span data-ttu-id="377af-136">将 `Product Name` 属性从 "**属性**" 窗格拖到 " **\<new level>** **层次结构**" 窗格中的 "**模型名称**" 级别下的单元。</span><span class="sxs-lookup"><span data-stu-id="377af-136">Drag the `Product Name` attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Model Name** level.</span></span> <span data-ttu-id="377af-137">（您已在先前的章节中将 Product Key 重命名为 Product Name。）</span><span class="sxs-lookup"><span data-stu-id="377af-137">(You renamed Product Key to Product Name in the previous section.)</span></span>  
  
4.  <span data-ttu-id="377af-138">在 "**维度结构**" 选项卡的 "**层次**结构" 窗格中，右键单击 "**层次**结构" 层次结构的标题栏，单击 "**重命名**"，然后键入 `Product Model Lines` 。</span><span class="sxs-lookup"><span data-stu-id="377af-138">In the **Hierarchies** pane of the **Dimension Structure** tab, right-click the title bar of the **Hierarchy** hierarchy, click **Rename**, and then type `Product Model Lines`.</span></span>  
  
     <span data-ttu-id="377af-139">层次结构的名称现在为 `Product Model Lines` 。</span><span class="sxs-lookup"><span data-stu-id="377af-139">The name of the hierarchy is now `Product Model Lines`.</span></span>  
  
5.  <span data-ttu-id="377af-140">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="377af-140">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="specifying-folder-names-and-all-member-names"></a><span data-ttu-id="377af-141">指定文件夹名称与“全部”级别成员名称</span><span class="sxs-lookup"><span data-stu-id="377af-141">Specifying Folder Names and All Member Names</span></span>  
  
#### <a name="to-specify-the-folder-and-member-names"></a><span data-ttu-id="377af-142">指定文件夹名称和成员名称</span><span class="sxs-lookup"><span data-stu-id="377af-142">To specify the folder and member names</span></span>  
  
1.  <span data-ttu-id="377af-143">在“属性”\*\*\*\* 窗格中，按住 Ctrl 键的同时单击下列各个属性，将它们选中：</span><span class="sxs-lookup"><span data-stu-id="377af-143">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="377af-144">**类**</span><span class="sxs-lookup"><span data-stu-id="377af-144">**Class**</span></span>  
  
    -   <span data-ttu-id="377af-145">**颜色**</span><span class="sxs-lookup"><span data-stu-id="377af-145">**Color**</span></span>  
  
    -   <span data-ttu-id="377af-146">**生产天数**</span><span class="sxs-lookup"><span data-stu-id="377af-146">**Days To Manufacture**</span></span>  
  
    -   <span data-ttu-id="377af-147">**Reorder Point**</span><span class="sxs-lookup"><span data-stu-id="377af-147">**Reorder Point**</span></span>  
  
    -   <span data-ttu-id="377af-148">**Safety Stock Level**</span><span class="sxs-lookup"><span data-stu-id="377af-148">**Safety Stock Level**</span></span>  
  
    -   <span data-ttu-id="377af-149">**大小**</span><span class="sxs-lookup"><span data-stu-id="377af-149">**Size**</span></span>  
  
    -   <span data-ttu-id="377af-150">**Size Range**</span><span class="sxs-lookup"><span data-stu-id="377af-150">**Size Range**</span></span>  
  
    -   <span data-ttu-id="377af-151">**样式**</span><span class="sxs-lookup"><span data-stu-id="377af-151">**Style**</span></span>  
  
    -   <span data-ttu-id="377af-152">**Weight**</span><span class="sxs-lookup"><span data-stu-id="377af-152">**Weight**</span></span>  
  
2.  <span data-ttu-id="377af-153">在属性窗口的**AttributeHierarchyDisplayFolder**属性字段中，键入 `Stocking` 。</span><span class="sxs-lookup"><span data-stu-id="377af-153">In the **AttributeHierarchyDisplayFolder** property field in the Properties window, type `Stocking`.</span></span>  
  
     <span data-ttu-id="377af-154">此时即将这些属性分组放到单独的显示文件夹中。</span><span class="sxs-lookup"><span data-stu-id="377af-154">You have now grouped these attributes into a single display folder.</span></span>  
  
3.  <span data-ttu-id="377af-155">在“属性”\*\*\*\* 窗格中，选择以下属性：</span><span class="sxs-lookup"><span data-stu-id="377af-155">In the **Attributes** pane, select the following attributes:</span></span>  
  
    -   <span data-ttu-id="377af-156">**经销价格**</span><span class="sxs-lookup"><span data-stu-id="377af-156">**Dealer Price**</span></span>  
  
    -   <span data-ttu-id="377af-157">**标价**</span><span class="sxs-lookup"><span data-stu-id="377af-157">**List Price**</span></span>  
  
    -   <span data-ttu-id="377af-158">**标准成本**</span><span class="sxs-lookup"><span data-stu-id="377af-158">**Standard Cost**</span></span>  
  
4.  <span data-ttu-id="377af-159">在属性窗口的 " **AttributeHierarchyDisplayFolder** " 属性单元中，键入 `Financial` 。</span><span class="sxs-lookup"><span data-stu-id="377af-159">In the **AttributeHierarchyDisplayFolder** property cell in the Properties window, type `Financial`.</span></span>  
  
     <span data-ttu-id="377af-160">此时即将这些属性分组放到第二个显示文件夹中。</span><span class="sxs-lookup"><span data-stu-id="377af-160">You have now grouped these attributes into a second display folder.</span></span>  
  
5.  <span data-ttu-id="377af-161">在“属性”\*\*\*\* 窗格中，选择以下属性：</span><span class="sxs-lookup"><span data-stu-id="377af-161">In the **Attributes** pane, select the following attributes:</span></span>  
  
    -   <span data-ttu-id="377af-162">**结束日期**</span><span class="sxs-lookup"><span data-stu-id="377af-162">**End Date**</span></span>  
  
    -   <span data-ttu-id="377af-163">**开始日期**</span><span class="sxs-lookup"><span data-stu-id="377af-163">**Start Date**</span></span>  
  
    -   <span data-ttu-id="377af-164">**Status**</span><span class="sxs-lookup"><span data-stu-id="377af-164">**Status**</span></span>  
  
6.  <span data-ttu-id="377af-165">在属性窗口的 " **AttributeHierarchyDisplayFolder** " 属性单元中，键入 `History` 。</span><span class="sxs-lookup"><span data-stu-id="377af-165">In the **AttributeHierarchyDisplayFolder** property cell in the Properties window, type `History`.</span></span>  
  
     <span data-ttu-id="377af-166">此时即将这些属性分组放到第三个显示文件夹中。</span><span class="sxs-lookup"><span data-stu-id="377af-166">You have now grouped these attributes into a third display folder.</span></span>  
  
7.  <span data-ttu-id="377af-167">`Product Model Lines`在 "**层次结构**" 窗格中选择层次结构，然后将属性窗口中的**AllMemberName**属性更改为 `All Products` 。</span><span class="sxs-lookup"><span data-stu-id="377af-167">Select the `Product Model Lines` hierarchy in the **Hierarchies** pane, and then change the **AllMemberName** property in the Properties window to `All Products`.</span></span>  
  
8.  <span data-ttu-id="377af-168">单击 "**层次结构**" 窗格的打开区域，然后将属性窗口顶部的 " **AttributeAllMemberName** " 属性更改为 `All Products` 。</span><span class="sxs-lookup"><span data-stu-id="377af-168">Click an open area of the **Hierarchies** pane, and then change the **AttributeAllMemberName** property at the top of the Properties window to `All Products`.</span></span>  
  
     <span data-ttu-id="377af-169">单击空白区域，即可修改“产品”维度自身的属性。</span><span class="sxs-lookup"><span data-stu-id="377af-169">Clicking an open area lets you modify properties of the Product dimension itself.</span></span> <span data-ttu-id="377af-170">还可以单击“属性”\*\*\*\* 窗格中位于属性列表顶部的“产品”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="377af-170">You could also click **Product** at the top of the attributes list in the **Attributes** pane.</span></span>  
  
9. <span data-ttu-id="377af-171">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="377af-171">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships"></a><span data-ttu-id="377af-172">定义属性关系</span><span class="sxs-lookup"><span data-stu-id="377af-172">Defining Attribute Relationships</span></span>  
 <span data-ttu-id="377af-173">如果基础数据支持，则应定义属性间的属性关系。</span><span class="sxs-lookup"><span data-stu-id="377af-173">If the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="377af-174">定义属性关系可加快维度、分区和查询处理的速度。</span><span class="sxs-lookup"><span data-stu-id="377af-174">Defining attribute relationships speeds up dimension, partition, and query processing.</span></span> <span data-ttu-id="377af-175">有关详细信息，请参阅 [定义属性关系](multidimensional-models/attribute-relationships-define.md) 和 [属性关系](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="377af-175">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
#### <a name="to-define-attribute-relationships"></a><span data-ttu-id="377af-176">定义属性关系</span><span class="sxs-lookup"><span data-stu-id="377af-176">To define attribute relationships</span></span>  
  
1.  <span data-ttu-id="377af-177">在“产品”维度的“维度设计器”\*\*\*\* 中，单击“属性关系”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="377af-177">In the **Dimension Designer** for the Product dimension, click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="377af-178">在关系图中，右键单击“模型名称”\*\*\*\* 属性，然后单击“新建属性关系”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="377af-178">In the diagram, right-click the **Model Name** attribute, and then click **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="377af-179">在“创建属性关系”对话框中，“源属性”是“型号名称”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="377af-179">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Model Name**.</span></span> <span data-ttu-id="377af-180">将“相关属性”设置为“产品系列”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="377af-180">Set the **Related Attribute** to **Product Line**.</span></span>  
  
     <span data-ttu-id="377af-181">因为各成员之间的关系会随时间变化，所以在“关系类型”列表中，将关系类型设置保留为“柔性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="377af-181">In the **Relationship type** list, leave the relationship type set to **Flexible** because relationships between the members might change over time.</span></span> <span data-ttu-id="377af-182">例如，产品型号可能会最终移动到另一个产品系列中。</span><span class="sxs-lookup"><span data-stu-id="377af-182">For example, a product model might eventually be moved to a different product line.</span></span>  
  
4.  <span data-ttu-id="377af-183">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="377af-183">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="377af-184">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="377af-184">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="reviewing-product-dimension-changes"></a><span data-ttu-id="377af-185">检查“产品”维度更改</span><span class="sxs-lookup"><span data-stu-id="377af-185">Reviewing Product Dimension Changes</span></span>  
  
#### <a name="to-review-the-product-dimension-changes"></a><span data-ttu-id="377af-186">检查“产品”维度更改</span><span class="sxs-lookup"><span data-stu-id="377af-186">To review the Product dimension changes</span></span>  
  
1.  <span data-ttu-id="377af-187">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的“生成”菜单上，单击“部署 Analysis Services 教程”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="377af-187">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="377af-188">在收到“部署成功完成”\*\*\*\* 消息后，单击“产品”\*\*\*\* 维度的“维度设计器”\*\*\*\* 的“浏览器”\*\*\*\* 选项卡，然后单击设计器工具栏上的“重新连接”按钮。</span><span class="sxs-lookup"><span data-stu-id="377af-188">After you have received the **Deployment Completed Successfully** message, click the **Browser** tab of **Dimension Designer** for the **Product** dimension, and then click the Reconnect button on the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="377af-189">验证 `Product Model Lines` 是否在 "**层次结构**" 列表中选中，然后展开 `All Products` 。</span><span class="sxs-lookup"><span data-stu-id="377af-189">Verify that `Product Model Lines` is selected in the **Hierarchy** list, and then expand `All Products`.</span></span>  
  
     <span data-ttu-id="377af-190">请注意，"**全部**" 成员的名称显示为 `All Products` 。</span><span class="sxs-lookup"><span data-stu-id="377af-190">Notice that the name of the **All** member appears as `All Products`.</span></span> <span data-ttu-id="377af-191">这是因为您已将层次结构的**AllMemberName**属性更改为 `All Products` 前面的课程。</span><span class="sxs-lookup"><span data-stu-id="377af-191">This is because you changed the **AllMemberName** property for the hierarchy to `All Products` earlier in the lesson.</span></span> <span data-ttu-id="377af-192">另请注意，“产品系列”\*\*\*\* 级别的成员现在具有用户友好名称，而不是单字母缩写形式。</span><span class="sxs-lookup"><span data-stu-id="377af-192">Also, the members of the **Product Line** level now have user-friendly names, instead of single-letter abbreviations.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="377af-193">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="377af-193">Next Task in Lesson</span></span>  
 [<span data-ttu-id="377af-194">修改“日期”维度</span><span class="sxs-lookup"><span data-stu-id="377af-194">Modifying the Date Dimension</span></span>](lesson-3-4-modifying-the-date-dimension.md)  
  
## <a name="see-also"></a><span data-ttu-id="377af-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="377af-195">See Also</span></span>  
 <span data-ttu-id="377af-196">[在数据源视图中定义命名计算 &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="377af-196">[Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md) </span></span>  
 <span data-ttu-id="377af-197">[创建用户定义的层次结构](multidimensional-models/user-defined-hierarchies-create.md) </span><span class="sxs-lookup"><span data-stu-id="377af-197">[Create User-Defined Hierarchies](multidimensional-models/user-defined-hierarchies-create.md) </span></span>  
 [<span data-ttu-id="377af-198">配置属性层次结构的“(全部)”级别</span><span class="sxs-lookup"><span data-stu-id="377af-198">Configure the &#40;All&#41; Level for Attribute Hierarchies</span></span>](multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
