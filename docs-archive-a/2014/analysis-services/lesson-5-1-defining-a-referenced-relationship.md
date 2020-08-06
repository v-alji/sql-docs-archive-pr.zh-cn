---
title: 定义引用的关系 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4a34ba52-e3b3-4e8a-8e55-73e0cd5a97bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7b14699ad098ba8c0931c00a3cbd30a6a8026771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590971"
---
# <a name="defining-a-referenced-relationship"></a><span data-ttu-id="c4013-102">定义引用关系</span><span class="sxs-lookup"><span data-stu-id="c4013-102">Defining a Referenced Relationship</span></span>
  <span data-ttu-id="c4013-103">在本教程中到目前为止，您定义的每个多维数据集维度都基于一个按主键到外键的关系直接链接到度量值组事实数据表的表。</span><span class="sxs-lookup"><span data-stu-id="c4013-103">Up to this point in the tutorial, each cube dimension that you defined was based on a table that was directly linked to the fact table for a measure group by a primary key to foreign key relationship.</span></span> <span data-ttu-id="c4013-104">在本主题的各任务中，你会将“地域”\*\*\*\* 维度通过一个称为“引用维度”\*\* 的“分销商”\*\*\*\* 维度链接到分销商销售额的事实数据表。</span><span class="sxs-lookup"><span data-stu-id="c4013-104">In the tasks in this topic, you link the **Geography** dimension to the fact table for reseller sales through the **Reseller** dimension, which is called a *reference dimension*.</span></span> <span data-ttu-id="c4013-105">这允许用户按地域定义经销商销售额的维度。</span><span class="sxs-lookup"><span data-stu-id="c4013-105">This enables users to dimension reseller sales by geography.</span></span> <span data-ttu-id="c4013-106">有关详细信息，请参阅 [定义引用的关系和引用的关系属性](multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c4013-106">For more information, see [Define a Referenced Relationship and Referenced Relationship Properties](multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md).</span></span>

## <a name="dimensioning-reseller-sales-by-geography"></a><span data-ttu-id="c4013-107">按地域定义分销商销售维度</span><span class="sxs-lookup"><span data-stu-id="c4013-107">Dimensioning Reseller Sales by Geography</span></span>

1.  <span data-ttu-id="c4013-108">在解决方案资源管理器中，右键单击“多维数据集”\*\*\*\* 文件夹中的“Analysis Services 教程”\*\*\*\*，然后单击“浏览”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c4013-108">In Solution Explorer, right-click **Analysis Services Tutorial** in the **Cubes** folder, and then click **Browse**.</span></span>

2.  <span data-ttu-id="c4013-109">删除“数据”窗格中的所有层次结构，然后验证“分销商销售-销售额”\*\*\*\* 度量值是否出现在“数据”窗格的数据区域中。</span><span class="sxs-lookup"><span data-stu-id="c4013-109">Remove all hierarchies from the data pane, and then verify that the **Reseller Sales-Sales Amount** measure appears in the data area of the data pane.</span></span> <span data-ttu-id="c4013-110">如果未出现该度量值，则请将其添加到“数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="c4013-110">Add it to the data pane if it is not already there.</span></span>

3.  <span data-ttu-id="c4013-111">将“地域”\*\*\*\* 用户定义层次结构从“元数据”窗格中的“地域”\*\*\*\* 维度拖到“数据”窗格的“将行字段拖至此处”\*\*\*\* 区域。</span><span class="sxs-lookup"><span data-stu-id="c4013-111">From the **Geography** dimension in the metadata pane, drag the **Geographies** user-defined hierarchy to the **Drop Row Fields Here** area of the data pane.</span></span>

     <span data-ttu-id="c4013-112">请注意，“分销商销售-销售额”\*\*\*\* 度量值并未按照“区域”\*\*\*\* 层次结构中的“国家/地区-区域”\*\*\*\* 属性成员正确确定维度。</span><span class="sxs-lookup"><span data-stu-id="c4013-112">Notice that the **Reseller Sales-Sales Amount** measure is not correctly dimensioned by the **Country-Region** attribute members in the **Regions** hierarchy.</span></span> <span data-ttu-id="c4013-113">对于每个“国家/地区-区域”\*\*\*\* 属性成员都重复“分销商销售-销售额”\*\*\*\* 的值。</span><span class="sxs-lookup"><span data-stu-id="c4013-113">The value for **Reseller Sales-Sales Amount** repeats for each **Country-Region** attribute member.</span></span>

     <span data-ttu-id="c4013-114">![划分维度的“分销商销售-销售额”度量值](../../2014/tutorials/media/l5-referencedrelationship-1.gif "划分维度的“分销商销售-销售额”度量值")</span><span class="sxs-lookup"><span data-stu-id="c4013-114">![Dimensioned Reseller Sales-Sales Amount measure](../../2014/tutorials/media/l5-referencedrelationship-1.gif "Dimensioned Reseller Sales-Sales Amount measure")</span></span>

4.  <span data-ttu-id="c4013-115">打开 **Adventure Works DW 2012** 数据源视图的数据源视图设计器。</span><span class="sxs-lookup"><span data-stu-id="c4013-115">Open Data Source View Designer for the **Adventure Works DW 2012** data source view.</span></span>

5.  <span data-ttu-id="c4013-116">在“关系图组织程序”\*\*\*\* 窗格中，查看 **Geography** 表和 **ResellerSales** 表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="c4013-116">In the **Diagram Organizer** pane, view the relationship between the **Geography** table and the **ResellerSales** table.</span></span>

     <span data-ttu-id="c4013-117">注意，这些表之间没有直接链接。</span><span class="sxs-lookup"><span data-stu-id="c4013-117">Notice that there is no direct link between these tables.</span></span> <span data-ttu-id="c4013-118">但是，它们之前存在通过“Reseller”\*\*\*\* 表和“SalesTerritory”\*\*\*\* 表进行的间接链接。</span><span class="sxs-lookup"><span data-stu-id="c4013-118">However, there is an indirect link between these tables through either the **Reseller** table or the **SalesTerritory** table.</span></span>

6.  <span data-ttu-id="c4013-119">双击表示 **Geography** 表和 **Reseller** 表之间的关系的箭头。</span><span class="sxs-lookup"><span data-stu-id="c4013-119">Double-click the arrow that represents the relationship between the **Geography** table and the **Reseller** table.</span></span>

     <span data-ttu-id="c4013-120">在“编辑关系”\*\*\*\* 对话框中，注意 **GeographyKey** 列既是 **Geography** 表中的主键，又是 **Reseller** 表中的外键。</span><span class="sxs-lookup"><span data-stu-id="c4013-120">In the **Edit Relationship** dialog box, notice that the **GeographyKey** column is the primary key in the **Geography** table and the foreign key in the **Reseller** table.</span></span>

7.  <span data-ttu-id="c4013-121">单击“取消”\*\*\*\*，切换到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器，然后单击“维度用法”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c4013-121">Click **Cancel**, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Dimension Usage** tab.</span></span>

     <span data-ttu-id="c4013-122">注意，“地域”\*\*\*\* 多维数据集维度当前与“Internet 销售”\*\*\*\* 度量值组或“分销商销售”\*\*\*\* 度量值组都没有关系。</span><span class="sxs-lookup"><span data-stu-id="c4013-122">Notice that the **Geography** cube dimension does not currently have a relationship with either the **Internet Sales** measure group or the **Reseller Sales** measure group.</span></span>

8.  <span data-ttu-id="c4013-123">单击 "**客户**" 维度和 " **Internet 销售**" 度量值组相交处的 "**全名**" 单元中的省略号**按钮 () 。**</span><span class="sxs-lookup"><span data-stu-id="c4013-123">Click the ellipsis button (**...**) in the **Full Name** cell at the intersection of the **Customer** dimension and the **Internet Sales** measure group.</span></span>

     <span data-ttu-id="c4013-124">在“定义关系”\*\*\*\* 对话框中，注意，在 **DimCustomer** 维度表和 **FactInternetSales** 度量值组表之间，根据每个表中的 **CustomerKey** 列定义了“常规”\*\*\*\* 关系。</span><span class="sxs-lookup"><span data-stu-id="c4013-124">In the **Define Relationship** dialog box, notice that a **Regular** relationship is defined between the **DimCustomer** dimension table and the **FactInternetSales** measure group table based on the **CustomerKey** column in each of these tables.</span></span> <span data-ttu-id="c4013-125">到目前为止，您在本教程中定义的所有关系都是常规关系。</span><span class="sxs-lookup"><span data-stu-id="c4013-125">All the relationships that you have defined within this tutorial up to this point have been regular relationships.</span></span>

     <span data-ttu-id="c4013-126">下图显示了“定义关系”\*\*\*\* 对话框，其中常规关系是 **DimCustomer** 维度表和 **FactInternetSales** 度量值组表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="c4013-126">The following image shows the **Define Relationship** dialog box with a regular relationship between the **DimCustomer** dimension table and the **FactInternetSales** measure group table.</span></span>

     <span data-ttu-id="c4013-127">!["定义关系" 对话框](../../2014/tutorials/media/l5-referencedrelationship-4.gif "“定义关系”对话框")</span><span class="sxs-lookup"><span data-stu-id="c4013-127">![Define Relationship dialog box](../../2014/tutorials/media/l5-referencedrelationship-4.gif "Define Relationship dialog box")</span></span>

9. <span data-ttu-id="c4013-128">单击“取消” 。</span><span class="sxs-lookup"><span data-stu-id="c4013-128">Click **Cancel**.</span></span>

10. <span data-ttu-id="c4013-129">单击 "**地域**" 维度和 "**分销商销售**" 度量值组相交处的未命名单元中的省略号**按钮 () 。**</span><span class="sxs-lookup"><span data-stu-id="c4013-129">Click the ellipsis button (**...**) in the unnamed cell at the intersection of the **Geography** dimension and the **Reseller Sales** measure group.</span></span>

     <span data-ttu-id="c4013-130">在“定义关系”\*\*\*\* 对话框中，可查看当前未定义“地域”多维数据集维度和“分销商销售”度量值组之间的关系。</span><span class="sxs-lookup"><span data-stu-id="c4013-130">In the **Define Relationship** dialog box, notice that no relationship is currently defined between the Geography cube dimension and the Reseller Sales measure group.</span></span> <span data-ttu-id="c4013-131">无法定义常规关系，因为“地域”维度的维度表和“分销商销售”度量值组的事实数据表之间没有直接关系。</span><span class="sxs-lookup"><span data-stu-id="c4013-131">You cannot define a regular relationship because there is no direct relationship between the dimension table for the Geography dimension and the fact table for the Reseller Sales measure group.</span></span>

11. <span data-ttu-id="c4013-132">在“选择关系类型”\*\*\*\* 列表中，选择“被引用的”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c4013-132">In the **Select relationship type** list, select **Referenced**.</span></span>

     <span data-ttu-id="c4013-133">你可以通过指定直接连接到度量值组表的维度来定义引用关系，该维度称为“中间维度”\*\*，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 可以使用该维度将引用维度链接到事实数据表。</span><span class="sxs-lookup"><span data-stu-id="c4013-133">You define a referenced relationship by specifying a dimension that is directly connected to the measure group table, called an *intermediate dimension*, that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] can use to link the reference dimension to the fact table.</span></span> <span data-ttu-id="c4013-134">然后指定将引用维度链接到中间维度的属性。</span><span class="sxs-lookup"><span data-stu-id="c4013-134">You then specify the attribute that links the reference dimension to the intermediate dimension.</span></span>

12. <span data-ttu-id="c4013-135">在“中间维度”\*\*\*\* 列表中，选择“分销商”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c4013-135">In the **Intermediate dimension** list, select **Reseller**.</span></span>

     <span data-ttu-id="c4013-136">“地域”维度的基础表通过“分销商”维度的基础表链接到事实数据表。</span><span class="sxs-lookup"><span data-stu-id="c4013-136">The underlying table for the Geography dimension is linked to the fact table through the underlying table for the Reseller dimension.</span></span>

13. <span data-ttu-id="c4013-137">在“引用维度属性”\*\*\*\* 列表中，选择“地域关键字”\*\*\*\*，然后尝试在“中间维度属性”\*\*\*\* 列表中选择“地域关键字”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c4013-137">In the **Reference dimension attribute** list, select **Geography Key**, and then try to select **Geography Key** in the **Intermediate dimension attribute** list.</span></span>

     <span data-ttu-id="c4013-138">注意，“地域关键字”\*\*\*\* 并未出现在“中间维度属性”\*\*\*\* 列表中。</span><span class="sxs-lookup"><span data-stu-id="c4013-138">Notice that **Geography Key** does not appear in the **Intermediate dimension attribute** list.</span></span> <span data-ttu-id="c4013-139">这是因为 **GeographyKey** 列尚未定义为“分销商”\*\*\*\* 维度中的属性。</span><span class="sxs-lookup"><span data-stu-id="c4013-139">This is because the **GeographyKey** column is not defined as an attribute in the **Reseller** dimension.</span></span>

14. <span data-ttu-id="c4013-140">单击“取消” 。</span><span class="sxs-lookup"><span data-stu-id="c4013-140">Click **Cancel**.</span></span>

 <span data-ttu-id="c4013-141">在下一个任务中，您将通过定义基于“分销商”维度中 GeographyKey 列的属性来解决此问题。</span><span class="sxs-lookup"><span data-stu-id="c4013-141">In the next task, you will solve this problem by defining an attribute that is based on the GeographyKey column in the Reseller dimension.</span></span>

## <a name="defining-the-intermediate-dimension-attribute-and-the-referenced-dimension-relationship"></a><span data-ttu-id="c4013-142">定义中间维度属性和引用维度关系</span><span class="sxs-lookup"><span data-stu-id="c4013-142">Defining the Intermediate Dimension Attribute and the Referenced Dimension Relationship</span></span>

1.  <span data-ttu-id="c4013-143">打开“分销商”\*\*\*\* 维度的维度设计器，然后查看“数据源视图”\*\*\*\* 窗格中 **Reseller** 表内的列，再查看“属性”\*\*\*\* 窗格中“分销商”\*\*\*\* 维度内已定义的属性。</span><span class="sxs-lookup"><span data-stu-id="c4013-143">Open Dimension Designer for the **Reseller** dimension, and view the columns in the **Reseller** table in the **Data Source View** pane, and view the defined attributes in the **Reseller** dimension in the **Attributes** pane.</span></span>

     <span data-ttu-id="c4013-144">注意，尽管已将 GeographyKey 定义为 Reseller 表中的一列，但在“分销商”维度中并未基于此列定义任何维度属性。</span><span class="sxs-lookup"><span data-stu-id="c4013-144">Notice that although GeographyKey is defined as a column in the Reseller table, no dimension attribute is defined in the Reseller dimension based on this column.</span></span> <span data-ttu-id="c4013-145">Geography 被定义为“地域”维度中的维度属性，原因在于它是将该维度的基础表链接到事实数据表的键列。</span><span class="sxs-lookup"><span data-stu-id="c4013-145">Geography is defined as a dimension attribute in the Geography dimension because it is the key column that links the underlying table for that dimension to the fact table.</span></span>

2.  <span data-ttu-id="c4013-146">若要将“地域关键字”\*\*\*\* 属性添加到“分销商”\*\*\*\* 维度中，右键单击“数据源视图”\*\*\*\* 中的 **GeographyKey**，然后单击“从列新建属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c4013-146">To add a **Geography Key** attribute to the **Reseller** dimension, right-click **GeographyKey** in the **Data Source View** pane, and then click **New Attribute from Column**.</span></span>

3.  <span data-ttu-id="c4013-147">在“特性”\*\*\*\* 窗格中，选择“地域关键字”\*\*\*\*，然后在“属性”窗口中，将 **AttributeHierarchyOptimizedState** 属性设置为**NotOptimized**，将 **AttributeHierarchyOrdered** 属性设置为 **False**，并将 **AttributeHierarchyVisible** 属性设置为**False**。</span><span class="sxs-lookup"><span data-stu-id="c4013-147">In the **Attributes** pane, select **Geography Key**, and then, in the Properties window, set the **AttributeHierarchyOptimizedState** property to **NotOptimized**, the **AttributeHierarchyOrdered** property to **False**, and the **AttributeHierarchyVisible** property to **False.**</span></span>

     <span data-ttu-id="c4013-148">“分销商”维度中的“地域关键字”属性只能用于将“地域”维度链接到 Reseller Sales 事实数据表。</span><span class="sxs-lookup"><span data-stu-id="c4013-148">The Geography Key attribute in the Reseller dimension will only be used to link the Geography dimension to the Reseller Sales fact table.</span></span> <span data-ttu-id="c4013-149">因为它不能用于浏览，所以不存在将该属性层次结构定义为可见的值。</span><span class="sxs-lookup"><span data-stu-id="c4013-149">Because it will not be used for browsing, there is no value in defining this attribute hierarchy as visible.</span></span> <span data-ttu-id="c4013-150">而且，对该属性层次结构进行排序和优化只能为处理性能带来负面影响。</span><span class="sxs-lookup"><span data-stu-id="c4013-150">Additionally, ordering and optimizing the attribute hierarchy will only negatively affect processing performance.</span></span> <span data-ttu-id="c4013-151">但是，必须启用该属性，使其作为两个维度之间的链接。</span><span class="sxs-lookup"><span data-stu-id="c4013-151">However, the attribute must be enabled to serve as the link between the two dimensions.</span></span>

4.  <span data-ttu-id="c4013-152">切换到 "教程" 多维数据集的多维数据集设计器 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，单击 "**维度用法**" 选项卡，然后单击 "**分销商销售**" 度量值组和 "**地域**" 多维数据集维度相交处的省略号按钮 (") **"。**</span><span class="sxs-lookup"><span data-stu-id="c4013-152">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Dimension Usage** tab, and then click the ellipsis button (**...**) at the intersection of the **Reseller Sales** measure group and the **Geography** cube dimension.</span></span>

5.  <span data-ttu-id="c4013-153">在“选择关系类型”\*\*\*\* 列表中，选择“被引用的”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c4013-153">In the **Select relationship type** list, select **Referenced**.</span></span>

6.  <span data-ttu-id="c4013-154">在“中间维度”\*\*\*\* 列表中，选择“分销商”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c4013-154">In the **Intermediate dimension** list, select **Reseller**.</span></span>

7.  <span data-ttu-id="c4013-155">在“引用维度属性”\*\*\*\* 列表中，选择“地域关键字”\*\*\*\*，然后在“中间维度属性”\*\*\*\* 列表中选择“地域关键字”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c4013-155">In the **Reference dimension attribute** list, select **Geography Key**, and then select **Geography Key** in the **Intermediate dimension attribute** list.</span></span>

     <span data-ttu-id="c4013-156">注意，已选中“具体化”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="c4013-156">Notice that the **Materialize** check box is selected.</span></span> <span data-ttu-id="c4013-157">这是 MOLAP 维度的默认设置。</span><span class="sxs-lookup"><span data-stu-id="c4013-157">This is the default setting for MOLAP dimensions.</span></span> <span data-ttu-id="c4013-158">在处理过程中，具体化维度属性链接可在维度的 MOLAP 结构中具体化或存储事实数据表和每行的引用维度之间的链接值。</span><span class="sxs-lookup"><span data-stu-id="c4013-158">Materializing the dimension attribute link causes the value of the link between the fact table and the reference dimension for each row to be materialized, or stored, in the dimension's MOLAP structure during processing.</span></span> <span data-ttu-id="c4013-159">这样做对处理性能和存储要求的影响不大，但会增强查询性能（有时会很显著）。</span><span class="sxs-lookup"><span data-stu-id="c4013-159">This will have a minor effect on processing performance and storage requirements, but will increase query performance (sometimes significantly).</span></span>

8.  <span data-ttu-id="c4013-160">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="c4013-160">Click **OK**.</span></span>

     <span data-ttu-id="c4013-161">注意，“地域”\*\*\*\* 多维数据集维度现在已链接到“分销商销售”\*\*\*\* 度量值组。</span><span class="sxs-lookup"><span data-stu-id="c4013-161">Notice that the **Geography** cube dimension is now linked to the **Reseller Sales** measure group.</span></span> <span data-ttu-id="c4013-162">该图标指示此关系是引用维度关系。</span><span class="sxs-lookup"><span data-stu-id="c4013-162">The icon indicates that the relationship is a referenced dimension relationship.</span></span>

9. <span data-ttu-id="c4013-163">在“维度用法”\*\*\*\* 选项卡上的“维度”\*\*\*\* 列表中，右键单击“地域”\*\*\*\*，然后单击“重命名”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c4013-163">In the **Dimensions** list on the **Dimension Usage** tab, right-click **Geography**, and then click **Rename**.</span></span>

10. <span data-ttu-id="c4013-164">将此多维数据集维度的名称更改为 `Reseller Geography` 。</span><span class="sxs-lookup"><span data-stu-id="c4013-164">Change the name of this cube dimension to `Reseller Geography`.</span></span>

     <span data-ttu-id="c4013-165">由于该多维数据集维度现在已链接到“分销商销售”\*\*\*\* 度量值组，所以用户可以从显式定义它在多维数据集中的用法中受益，避免可能造成的用户混淆。</span><span class="sxs-lookup"><span data-stu-id="c4013-165">Because this cube dimension is now linked to the **Reseller Sales** measure group, users will benefit from explicitly defining its use in the cube, to avoid possible user confusion.</span></span>

## <a name="successfully-dimensioning-reseller-sales-by-geography"></a><span data-ttu-id="c4013-166">按地域成功定义分销商销售维度</span><span class="sxs-lookup"><span data-stu-id="c4013-166">Successfully Dimensioning Reseller Sales by Geography</span></span>

1.  <span data-ttu-id="c4013-167">在“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c4013-167">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="c4013-168">在部署成功完成后，在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器中单击“浏览器”\*\*\*\* 选项卡，再单击“重新连接”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="c4013-168">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>

3.  <span data-ttu-id="c4013-169">在 "元数据" 窗格中，展开 `Reseller Geography` ，右键单击 "**地域**"，然后单击 "**添加到行区域**"。</span><span class="sxs-lookup"><span data-stu-id="c4013-169">In the metadata pane, expand `Reseller Geography`, right-click **Geographies**, and then click **Add to Row Area**.</span></span>

     <span data-ttu-id="c4013-170">请注意，“分销商销售-销售额”\*\*\*\* 度量值现在已按照“区域”\*\*\*\* 用户定义层次结构中的“国家/地区-区域”\*\*\*\* 属性正确确定了维度，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="c4013-170">Notice that the **Reseller Sales-Sales Amount** measure is now correctly dimensioned by the **Country-Region** attribute of the **Geographies** user-defined hierarchy, as shown in the following image.</span></span>

     <span data-ttu-id="c4013-171">!["定义关系" 对话框](../../2014/tutorials/media/l5-referencedrelationship-5.gif "“定义关系”对话框")</span><span class="sxs-lookup"><span data-stu-id="c4013-171">![Define Relationship dialog box](../../2014/tutorials/media/l5-referencedrelationship-5.gif "Define Relationship dialog box")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="c4013-172">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="c4013-172">Next Task in Lesson</span></span>
 [<span data-ttu-id="c4013-173">定义事实关系</span><span class="sxs-lookup"><span data-stu-id="c4013-173">Defining a Fact Relationship</span></span>](lesson-5-2-defining-a-fact-relationship.md)

## <a name="see-also"></a><span data-ttu-id="c4013-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4013-174">See Also</span></span>
 <span data-ttu-id="c4013-175">[属性关系](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)[定义引用的关系和引用的关系属性](multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)</span><span class="sxs-lookup"><span data-stu-id="c4013-175">[Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) [Define a Referenced Relationship and Referenced Relationship Properties](multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)</span></span>


