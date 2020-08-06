---
title: 指定用户定义层次结构中属性之间的属性关系 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 456c2a47-d395-45f9-9efa-89f3fa2ac621
author: minewiskan
ms.author: owend
ms.openlocfilehash: dc2fa03f72039aedd16c82b86ce0dd41b8f59702
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578551"
---
# <a name="specifying-attribute-relationships-between-attributes-in-a-user-defined-hierarchy"></a><span data-ttu-id="4356d-102">指定用户定义层次结构中属性之间的属性关系</span><span class="sxs-lookup"><span data-stu-id="4356d-102">Specifying Attribute Relationships Between Attributes in a User-Defined Hierarchy</span></span>
  <span data-ttu-id="4356d-103">您已了解本教程中的内容，现在可以将属性层次结构组织到用户层次结构内的级别中，以便在多维数据集中为用户提供导航路径。</span><span class="sxs-lookup"><span data-stu-id="4356d-103">As you have already learned in this tutorial, you can organize attribute hierarchies into levels within user hierarchies to provide navigation paths for users in a cube.</span></span> <span data-ttu-id="4356d-104">用户层次结构可以表示自然层次结构（如市/县、州/省/自治区和国家/地区），或者可以只表示导航路径（如雇员姓名、职务和部门名称）。</span><span class="sxs-lookup"><span data-stu-id="4356d-104">A user hierarchy can represent a natural hierarchy, such as city, state, and country, or can just represent a navigation path, such as employee name, title, and department name.</span></span> <span data-ttu-id="4356d-105">对于在层次结构中导航的用户而言，这两类用户层次结构应相同。</span><span class="sxs-lookup"><span data-stu-id="4356d-105">To the user navigating a hierarchy, these two types of user hierarchies are the same.</span></span>  
  
 <span data-ttu-id="4356d-106">使用自然层次结构时，如果定义了组成级别的属性之间的属性关系，则 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 可以使用某个属性的聚合来获取相关属性的结果。</span><span class="sxs-lookup"><span data-stu-id="4356d-106">With a natural hierarchy, if you define attribute relationships between the attributes that make up the levels, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] can use an aggregation from one attribute to obtain the results from a related attribute.</span></span> <span data-ttu-id="4356d-107">如果属性之间没有定义的关系，则 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将根据键属性聚合所有非键属性。</span><span class="sxs-lookup"><span data-stu-id="4356d-107">If there are no defined relationships between attributes, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] will aggregate all non-key attributes from the key attribute.</span></span> <span data-ttu-id="4356d-108">因此，如果基础数据支持，则应定义属性间的属性关系。</span><span class="sxs-lookup"><span data-stu-id="4356d-108">Therefore, if the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="4356d-109">定义属性关系可改进维度、分区和查询处理性能。</span><span class="sxs-lookup"><span data-stu-id="4356d-109">Defining attribute relationships improves dimension, partition, and query processing performance.</span></span> <span data-ttu-id="4356d-110">有关详细信息，请参阅 [定义属性关系](multidimensional-models/attribute-relationships-define.md) 和 [属性关系](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="4356d-110">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
 <span data-ttu-id="4356d-111">在定义属性关系时，可以指定此关系是弹性的还是刚性的。</span><span class="sxs-lookup"><span data-stu-id="4356d-111">When you define attribute relationships, you can specify that the relationship is either flexible or rigid.</span></span> <span data-ttu-id="4356d-112">如果您将关系定义为刚性，则 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 会在更新维度时保留聚合。</span><span class="sxs-lookup"><span data-stu-id="4356d-112">If you define a relationship as rigid, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] retains aggregations when the dimension is updated.</span></span> <span data-ttu-id="4356d-113">如果实际过程更改了定义为刚性的关系，那么除非维度得到完全处理，否则 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将在处理过程中生成错误。</span><span class="sxs-lookup"><span data-stu-id="4356d-113">If a relationship that is defined as rigid actually changes, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] generates an error during processing unless the dimension is fully processed.</span></span> <span data-ttu-id="4356d-114">指定适当的关系和关系属性，可提高查询和处理性能。</span><span class="sxs-lookup"><span data-stu-id="4356d-114">Specifying the appropriate relationships and relationship properties increases query and processing performance.</span></span> <span data-ttu-id="4356d-115">有关详细信息，请参阅[定义属性关系](multidimensional-models/attribute-relationships-define.md)和[用户层次结构属性](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="4356d-115">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md), and [User Hierarchy Properties](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md).</span></span>  
  
 <span data-ttu-id="4356d-116">在本主题的各个任务中，您将为 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 项目的自然用户层次结构中的属性定义属性关系。</span><span class="sxs-lookup"><span data-stu-id="4356d-116">In the tasks in this topic, you define attribute relationships for the attributes in the natural user hierarchies in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span> <span data-ttu-id="4356d-117">这些层次结构包括“客户”维度中的“客户所在地域”层次结构、“销售区域”维度中的“销售区域”层次结构、“产品”维度中的“产品型号系列”层次结构，以及“日期”维度中的“会计日期”和“日历日期”层次结构。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="4356d-117">These include the **Customer Geography** hierarchy in the **Custome**r dimension, the **Sales Territory** hierarchy in the **Sales Territory** dimension, the **Product Model** Lines hierarchy in the **Product** dimension, and the **Fiscal Date** and **Calendar Date** hierarchies in the **Date** dimension.</span></span> <span data-ttu-id="4356d-118">这些用户层次结构全部是自然层次结构。</span><span class="sxs-lookup"><span data-stu-id="4356d-118">These user hierarchies are all natural hierarchies.</span></span>  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-customer-geography-hierarchy"></a><span data-ttu-id="4356d-119">为“客户所在地域”层次结构中的属性定义属性关系</span><span class="sxs-lookup"><span data-stu-id="4356d-119">Defining Attribute Relationships for Attributes in the Customer Geography Hierarchy</span></span>  
  
1.  <span data-ttu-id="4356d-120">切换到“客户”维度的维度设计器，然后单击“维度结构”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="4356d-120">Switch to Dimension Designer for the Customer dimension, and then click the **Dimension Structure** tab.</span></span>  
  
     <span data-ttu-id="4356d-121">在“层次结构”窗格中，请注意“客户所在地域”用户定义层次结构中的级别。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="4356d-121">In the **Hierarchies** pane, notice the levels in the **Customer Geography** user-defined hierarchy.</span></span> <span data-ttu-id="4356d-122">此层次结构当前只是用户的向下钻取路径，因为在级别或属性之间未定义任何关系。</span><span class="sxs-lookup"><span data-stu-id="4356d-122">This hierarchy is currently just a drill-down path for users, as no relationship between levels or attributes have been defined.</span></span>  
  
2.  <span data-ttu-id="4356d-123">单击 **“属性关系”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="4356d-123">Click the **Attribute Relationships** tab.</span></span>  
  
     <span data-ttu-id="4356d-124">请注意用于将 **Geography** 表的非键属性链接到 **Geography** 表的键属性的 4 个属性关系。</span><span class="sxs-lookup"><span data-stu-id="4356d-124">Notice the four attribute relationships that link the non-key attributes from the **Geography** table to the key attribute from the **Geography** table.</span></span> <span data-ttu-id="4356d-125">“地域”属性与“全名”属性相关。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="4356d-125">The **Geography** attribute is related to the **Full Name** attribute.</span></span> <span data-ttu-id="4356d-126">由于“邮政编码”链接到“地域”属性，“地域”属性链接到“全名”属性，所以“邮政编码”属性通过“地域”属性间接链接到“全名”属性\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-126">The **Postal Code** attribute is indirectly linked to the **Full Name** attribute through the **Geography** attribute, because the **Postal Code** is linked to the **Geography** attribute and the **Geography** attribute is linked to the **Full Name** attribute.</span></span> <span data-ttu-id="4356d-127">接下来，我们将更改属性关系，以便它们不使用“地域”属性\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-127">Next, we will change the attribute relationships so that they do not use the **Geography** attribute.</span></span>  
  
3.  <span data-ttu-id="4356d-128">在关系图中，右键单击“全名”\*\*\*\* 属性，然后选择“新建属性关系”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-128">In the diagram, right-click the **Full Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
4.  <span data-ttu-id="4356d-129">在“创建属性关系”对话框中，“源属性”是“全名”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-129">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Full Name**.</span></span> <span data-ttu-id="4356d-130">将“相关属性”设置为“邮政编码”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-130">Set the **Related Attribute** to **Postal Code**.</span></span> <span data-ttu-id="4356d-131">因为各成员之间的关系会随时间变化，所以在“关系类型”列表中，将关系类型设置保留为“柔性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-131">In the **Relationship type** list, leave the relationship type set to **Flexible** because relationships between the members might change over time.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="4356d-132">因为此关系是冗余关系，所以在关系图中会显示警告图标。</span><span class="sxs-lookup"><span data-stu-id="4356d-132">A warning icon appears in the diagram because the relationship is redundant.</span></span> <span data-ttu-id="4356d-133">关系**全名**  ->  **地理位置** ->  **代码**已存在，您刚刚创建了关系**全名**  ->  **邮政编码**。</span><span class="sxs-lookup"><span data-stu-id="4356d-133">The relationship **Full Name** -> **Geography**-> **Postal Code** already existed, and you just created the relationship **Full Name** -> **Postal Code**.</span></span> <span data-ttu-id="4356d-134">此关系**地理位置** ->  **邮政编码**现在是冗余的，因此我们将其删除。</span><span class="sxs-lookup"><span data-stu-id="4356d-134">The relationship **Geography**-> **Postal Code** is now redundant, so we will remove it.</span></span>  
  
6.  <span data-ttu-id="4356d-135">在“属性关系”窗格中，右键单击“地域”-> “邮政编码”，然后单击“删除”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-135">In the **Attribute Relationships** pane, right-click **Geography**-> **Postal Code** and then click **Delete**.</span></span>  
  
7.  <span data-ttu-id="4356d-136">显示“删除对象”对话框时，单击“确定”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-136">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
8.  <span data-ttu-id="4356d-137">在关系图中，右键单击“邮政编码”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-137">In the diagram, right-click the **Postal Code** attribute and then select **New Attribute Relationship**.</span></span>  
  
9. <span data-ttu-id="4356d-138">在“创建属性关系”对话框中，“源属性”是“邮政编码”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-138">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Postal Code**.</span></span> <span data-ttu-id="4356d-139">将“相关属性”设置为“市县”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-139">Set the **Related Attribute** to **City**.</span></span> <span data-ttu-id="4356d-140">在“关系类型”列表中，将关系类型设置保留为“柔性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-140">In the **Relationship type** list, leave the relationship type set to **Flexible**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="4356d-141">关系**地理** ->  **城市**现在是冗余的，因此我们将其删除。</span><span class="sxs-lookup"><span data-stu-id="4356d-141">The relationship **Geography**-> **City** is now redundant so we will delete it.</span></span>  
  
11. <span data-ttu-id="4356d-142">在 "属性关系" 窗格中，右键单击**Geography** ->  **City** ，然后单击 "**删除**"。</span><span class="sxs-lookup"><span data-stu-id="4356d-142">In the Attribute Relationships pane, right-click **Geography**-> **City** and then click **Delete**.</span></span>  
  
12. <span data-ttu-id="4356d-143">显示“删除对象”对话框时，单击“确定”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-143">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
13. <span data-ttu-id="4356d-144">在关系图中，右键单击“市县”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-144">In the diagram, right-click the **City** attribute and then select **New Attribute Relationship**.</span></span>  
  
14. <span data-ttu-id="4356d-145">在“创建属性关系”对话框中，“源属性”是“市县”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-145">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **City**.</span></span> <span data-ttu-id="4356d-146">将“相关属性”设置为“省/市/自治区”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-146">Set the **Related Attribute** to **State-Province**.</span></span> <span data-ttu-id="4356d-147">因为市/县与州/省/自治区之间的关系将不会随着时间推移而更改，所以在“关系类型”列表中将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-147">In the **Relationship type** list, set the relationship type to **Rigid** because the relationship between a city and a state will not change over time.</span></span>  
  
15. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
16. <span data-ttu-id="4356d-148">右键单击“地域”和“省/市/自治区”之间的箭头，然后单击“删除”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-148">Right-click the arrow between **Geography** and **State-Province** and then click **Delete**.</span></span>  
  
17. <span data-ttu-id="4356d-149">显示“删除对象”对话框时，单击“确定”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-149">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
18. <span data-ttu-id="4356d-150">在关系图中，右键单击“省/市/自治区”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-150">In the diagram, right-click the **State-Province** attribute and then select **New Attribute Relationship**.</span></span>  
  
19. <span data-ttu-id="4356d-151">在“创建属性关系”对话框中，“源属性”是“省/市/自治区”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-151">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **State-Province**.</span></span> <span data-ttu-id="4356d-152">将“相关属性”设置为“国家/地区-区域”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-152">Set the **Related Attribute** to **Country-Region**.</span></span> <span data-ttu-id="4356d-153">因为州/省/自治区与国家/地区区域之间的关系将不会随着时间的推移而更改，所以在“关系类型”列表中，将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-153">In the **Relationship type** list, set the relationship type to **Rigid** because the relationship between a state-province and a country-region will not change over time.</span></span>  
  
20. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
21. <span data-ttu-id="4356d-154">在 "属性关系" 窗格中，右键单击 "**地理** ->  **国家/地区**"，然后单击 "**删除**"。</span><span class="sxs-lookup"><span data-stu-id="4356d-154">In the Attribute Relationships pane, right-click **Geography**-> **Country-Region** and then click **Delete**.</span></span>  
  
22. <span data-ttu-id="4356d-155">显示“删除对象”对话框时，单击“确定”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-155">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
23. <span data-ttu-id="4356d-156">单击“维度结构”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="4356d-156">Click the **Dimension Structure** tab.</span></span>  
  
     <span data-ttu-id="4356d-157">请注意，在你删除“地域”和其他属性之间的最后一个属性关系后，“地域”本身也将被删除\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-157">Notice that when you delete the last attribute relationship between **Geography** and other attributes, that **Geography** itself is deleted.</span></span> <span data-ttu-id="4356d-158">这是因为不再使用该属性。</span><span class="sxs-lookup"><span data-stu-id="4356d-158">This is because the attribute is no longer used.</span></span>  
  
24. <span data-ttu-id="4356d-159">在 "文件" 菜单上，单击 "**全部保存**"。</span><span class="sxs-lookup"><span data-stu-id="4356d-159">On the File menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-sales-territory-hierarchy"></a><span data-ttu-id="4356d-160">为“销售区域”层次结构中的属性定义属性关系</span><span class="sxs-lookup"><span data-stu-id="4356d-160">Defining Attribute Relationships for Attributes in the Sales Territory Hierarchy</span></span>  
  
1.  <span data-ttu-id="4356d-161">打开“销售区域”维度的维度设计器，然后单击“属性关系”选项卡\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-161">Open Dimension Designer for the **Sales Territory** dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="4356d-162">在关系图中，右键单击“销售区域所属国家/地区”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-162">In the diagram, right-click the **Sales Territory Country** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="4356d-163">在“创建属性关系”对话框中，“源属性”是“销售区域所属国家/地区”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-163">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Sales Territory Country**.</span></span> <span data-ttu-id="4356d-164">将“相关属性”设置为“销售区域组”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-164">Set the **Related Attribute** to **Sales Territory Group**.</span></span> <span data-ttu-id="4356d-165">在“关系类型”列表中，将关系类型设置保留为“柔性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-165">In the **Relationship type** list, leave the relationship type set to **Flexible**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="4356d-166">“销售区域组”现已链接到“销售区域所属国家”，而“销售区域所属国家”现已链接到“销售区域所属地区”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-166">**Sales Territory Group** is now linked to **Sales Territory Country**, and **Sales Territory Country** is now linked to **Sales Territory Region**.</span></span> <span data-ttu-id="4356d-167">因为一个国家/地区内的区域分组以及国家/地区的分组都可能会随着时间的推移而更改，所以每种关系的 **RelationshipType** 属性都设置为“柔性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-167">The **RelationshipType** property for each of these relationships is set to **Flexible** because the groupings of regions within a country might change over time and because the groupings of countries into groups might change over time.</span></span>  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-product-model-lines-hierarchy"></a><span data-ttu-id="4356d-168">为“产品型号系列”层次结构中的属性定义属性关系</span><span class="sxs-lookup"><span data-stu-id="4356d-168">Defining Attribute Relationships for Attributes in the Product Model Lines Hierarchy</span></span>  
  
1.  <span data-ttu-id="4356d-169">打开“产品”维度的维度设计器，然后单击“属性关系”选项卡\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-169">Open Dimension Designer for the **Product** dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="4356d-170">在关系图中，右键单击“型号名称”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-170">In the diagram, right-click the **Model Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="4356d-171">在“创建属性关系”对话框中，“源属性”是“型号名称”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-171">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Model Name**.</span></span> <span data-ttu-id="4356d-172">将“相关属性”设置为“产品系列”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-172">Set the **Related Attribute** to **Product Line**.</span></span> <span data-ttu-id="4356d-173">在“关系类型”列表中，将关系类型设置保留为“柔性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-173">In the **Relationship type** list, leave the relationship type set to **Flexible**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-fiscal-date-hierarchy"></a><span data-ttu-id="4356d-174">为“会计日期”层次结构中的属性定义属性关系</span><span class="sxs-lookup"><span data-stu-id="4356d-174">Defining Attribute Relationships for Attributes in the Fiscal Date Hierarchy</span></span>  
  
1.  <span data-ttu-id="4356d-175">切换到“日期”维度的维度设计器，然后单击“属性关系”选项卡\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-175">Switch to Dimension Designer for the **Date** dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="4356d-176">在关系图中，右键单击“月份名称”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-176">In the diagram, right-click the **Month Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="4356d-177">在“创建属性关系”对话框中，“源属性”是“月份名称”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-177">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Month Name**.</span></span> <span data-ttu-id="4356d-178">将“相关属性”设置为“会计季度”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-178">Set the **Related Attribute** to **Fiscal Quarter**.</span></span> <span data-ttu-id="4356d-179">在“关系类型”列表中，将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-179">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="4356d-180">在关系图中，右键单击“会计季度”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-180">In the diagram, right-click the **Fiscal Quarter** attribute and then select **New Attribute Relationship**.</span></span>  
  
6.  <span data-ttu-id="4356d-181">在“创建属性关系”对话框中，“源属性”是“会计季度”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-181">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Fiscal Quarter**.</span></span> <span data-ttu-id="4356d-182">将“相关属性”设置为“会计半期”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-182">Set the **Related Attribute** to **Fiscal Semester**.</span></span> <span data-ttu-id="4356d-183">在“关系类型”列表中，将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-183">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="4356d-184">在关系图中，右键单击“会计半期”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-184">In the diagram, right-click the **Fiscal Semester** attribute and then select **New Attribute Relationship**.</span></span>  
  
9. <span data-ttu-id="4356d-185">在“创建属性关系”对话框中，“源属性”是“会计半期”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-185">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Fiscal Semester**.</span></span> <span data-ttu-id="4356d-186">将“相关属性”设置为“会计年度”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-186">Set the **Related Attribute** to **Fiscal Year**.</span></span> <span data-ttu-id="4356d-187">在“关系类型”列表中，将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-187">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-calendar-date-hierarchy"></a><span data-ttu-id="4356d-188">为“日历日期”层次结构中的属性定义属性关系</span><span class="sxs-lookup"><span data-stu-id="4356d-188">Defining Attribute Relationships for Attributes in the Calendar Date Hierarchy</span></span>  
  
1.  <span data-ttu-id="4356d-189">在关系图中，右键单击“月份名称”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-189">In the diagram, right-click the **Month Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
2.  <span data-ttu-id="4356d-190">在“创建属性关系”对话框中，“源属性”是“月份名称”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-190">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Month Name**.</span></span> <span data-ttu-id="4356d-191">将“相关属性”设置为“日历季度”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-191">Set the **Related Attribute** to **Calendar Quarter**.</span></span> <span data-ttu-id="4356d-192">在“关系类型”列表中，将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-192">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="4356d-193">在关系图中，右键单击“日历季度”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-193">In the diagram, right-click the **Calendar Quarter** attribute and then select **New Attribute Relationship**.</span></span>  
  
5.  <span data-ttu-id="4356d-194">在“创建属性关系”对话框中，“源属性”是“日历季度”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-194">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Quarter**.</span></span> <span data-ttu-id="4356d-195">将“相关属性”设置为“日历半期”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-195">Set the **Related Attribute** to **Calendar Semester**.</span></span> <span data-ttu-id="4356d-196">在“关系类型”列表中，将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-196">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="4356d-197">在关系图中，右键单击“日历半期”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-197">In the diagram, right-click the **Calendar Semester** attribute and then select **New Attribute Relationship**.</span></span>  
  
8.  <span data-ttu-id="4356d-198">在“创建属性关系”对话框中，“源属性”是“日历半期”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-198">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Semester**.</span></span> <span data-ttu-id="4356d-199">将“相关属性”设置为“日历年”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-199">Set the **Related Attribute** to **Calendar Year**.</span></span> <span data-ttu-id="4356d-200">在“关系类型”列表中，将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-200">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-geography-hierarchy"></a><span data-ttu-id="4356d-201">为“地域”层次结构中的属性定义属性关系</span><span class="sxs-lookup"><span data-stu-id="4356d-201">Defining Attribute Relationships for Attributes in the Geography Hierarchy</span></span>  
  
1.  <span data-ttu-id="4356d-202">打开“地域”维度的维度设计器，然后单击“属性关系”选项卡\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-202">Open Dimension Designer for the Geography dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="4356d-203">在关系图中，右键单击“邮政编码”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-203">In the diagram, right-click the **Postal Code** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="4356d-204">在“创建属性关系”对话框中，“源属性”是“邮政编码”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-204">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Postal Code**.</span></span> <span data-ttu-id="4356d-205">将“相关属性”设置为“市县”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-205">Set the **Related Attribute** to **City**.</span></span> <span data-ttu-id="4356d-206">在“关系类型”列表中，将关系类型设置为“柔性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-206">In the **Relationship type** list, set the relationship type to **Flexible**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="4356d-207">在关系图中，右键单击“市县”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-207">In the diagram, right-click the **City** attribute and then select **New Attribute Relationship**.</span></span>  
  
6.  <span data-ttu-id="4356d-208">在“创建属性关系”对话框中，“源属性”是“市县”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-208">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **City**.</span></span> <span data-ttu-id="4356d-209">将“相关属性”设置为“省/市/自治区”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-209">Set the **Related Attribute** to **State-Province**.</span></span> <span data-ttu-id="4356d-210">在“关系类型”列表中，将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-210">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="4356d-211">在关系图中，右键单击“省/市/自治区”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-211">In the diagram, right-click the **State-Province** attribute and then select **New Attribute Relationship**.</span></span>  
  
9. <span data-ttu-id="4356d-212">在“创建属性关系”对话框中，“源属性”是“省/市/自治区”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-212">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **State-Province**.</span></span> <span data-ttu-id="4356d-213">将“相关属性”设置为“国家/地区-区域”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-213">Set the **Related Attribute** to **Country-Region**.</span></span> <span data-ttu-id="4356d-214">在“关系类型”列表中，将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-214">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="4356d-215">在关系图中，右键单击“地域关键字”特性，然后选择“属性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-215">In the diagram, right-click the **Geography Key** attribute and then select **Properties**.</span></span>  
  
12. <span data-ttu-id="4356d-216">将 **AttributeHierarchyOptimizedState** 属性设置为 **NotOptimized**，将 **AttributeHierarchyOrdered** 属性设置为 **False**，并将 **AttributeHierarchyVisible** 属性设置为 **False**。</span><span class="sxs-lookup"><span data-stu-id="4356d-216">Set the **AttributeHierarchyOptimizedState** property to **NotOptimized**, set the **AttributeHierarchyOrdered** property to **False**, and set the **AttributeHierarchyVisible** property to **False**.</span></span>  
  
13. <span data-ttu-id="4356d-217">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="4356d-217">On the **File** menu, click **Save All**.</span></span>  
  
14. <span data-ttu-id="4356d-218">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的“生成”菜单上，单击“部署 Analysis Services 教程”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4356d-218">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="4356d-219">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="4356d-219">Next Task in Lesson</span></span>  
 [<span data-ttu-id="4356d-220">定义未知成员和 Null 处理属性</span><span class="sxs-lookup"><span data-stu-id="4356d-220">Defining the Unknown Member and Null Processing Properties</span></span>](lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="4356d-221">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4356d-221">See Also</span></span>  
 <span data-ttu-id="4356d-222">[定义属性关系](multidimensional-models/attribute-relationships-define.md) </span><span class="sxs-lookup"><span data-stu-id="4356d-222">[Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) </span></span>  
 [<span data-ttu-id="4356d-223">用户层次结构属性</span><span class="sxs-lookup"><span data-stu-id="4356d-223">User Hierarchy Properties</span></span>](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)  
  
  
