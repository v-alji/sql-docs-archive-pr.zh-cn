---
title: 第10课：创建层次结构 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4d0982a05c37c28167e44e3f9f082ea5113b59bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689661"
---
# <a name="lesson-10-create-hierarchies"></a><span data-ttu-id="6a869-102">第 10 课：创建层次结构</span><span class="sxs-lookup"><span data-stu-id="6a869-102">Lesson 10: Create Hierarchies</span></span>
  <span data-ttu-id="6a869-103">在本课中，您将创建层次结构。</span><span class="sxs-lookup"><span data-stu-id="6a869-103">In this lesson, you will create hierarchies.</span></span> <span data-ttu-id="6a869-104">层次结构是按级别排列的列的分组；例如，地理层次结构可能具有针对国家/地区、省/市/自治区、县和市的子级别。</span><span class="sxs-lookup"><span data-stu-id="6a869-104">Hierarchies are groups of columns arranged in levels; for example, a Geography hierarchy might have sub-levels for Country, State, County, and City.</span></span> <span data-ttu-id="6a869-105">层次结构在报告客户端应用程序字段列表中可以与其他列分开显示，这使得客户端用户更容易在其中导航以及将其包括在报表中。</span><span class="sxs-lookup"><span data-stu-id="6a869-105">Hierarchies can appear separate from other columns in a reporting client application field list, making them easier for client users to navigate and include in a report.</span></span> <span data-ttu-id="6a869-106">若要了解详细信息，请参阅[层次结构（SSAS 表格）](tabular-models/hierarchies-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="6a869-106">To learn more, see [Hierarchies &#40;SSAS Tabular&#41;](tabular-models/hierarchies-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="6a869-107">若要创建层次结构，可使用“关系图视图”\*\* 中的模型设计器。</span><span class="sxs-lookup"><span data-stu-id="6a869-107">To create hierarchies, you will use the model designer in *Diagram View*.</span></span> <span data-ttu-id="6a869-108">在数据视图的模型设计器中不支持创建和管理层次结构。</span><span class="sxs-lookup"><span data-stu-id="6a869-108">Creating and managing hierarchies is not supported in the model designer in Data View.</span></span>  
  
 <span data-ttu-id="6a869-109">本课预计完成时间：**20 分钟**</span><span class="sxs-lookup"><span data-stu-id="6a869-109">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6a869-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="6a869-110">Prerequisites</span></span>  
 <span data-ttu-id="6a869-111">本主题是表格建模教程的一部分，应当按顺序完成。</span><span class="sxs-lookup"><span data-stu-id="6a869-111">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="6a869-112">在执行本课程中的任务之前，应该已完成上一课： [第 9 课：创建透视](lesson-8-create-perspectives.md)。</span><span class="sxs-lookup"><span data-stu-id="6a869-112">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 9: Create Perspectives](lesson-8-create-perspectives.md).</span></span>  
  
## <a name="create-hierarchies"></a><span data-ttu-id="6a869-113">创建层次结构</span><span class="sxs-lookup"><span data-stu-id="6a869-113">Create Hierarchies</span></span>  
  
#### <a name="to-create-a-category-hierarchy-in-the-product-table"></a><span data-ttu-id="6a869-114">在 Product 表中创建类别层次结构</span><span class="sxs-lookup"><span data-stu-id="6a869-114">To create a Category hierarchy in the Product table</span></span>  
  
1.  <span data-ttu-id="6a869-115">在模型设计器中，单击 `Model` 菜单，指向 "**模型视图**"，然后单击 "**关系图视图**"。</span><span class="sxs-lookup"><span data-stu-id="6a869-115">In the model designer, click on the `Model` menu, then point to **Model View**, and then click **Diagram View**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="6a869-116">使用位于模型设计器右上角的 Minimap 控件可更改您在关系图视图中查看对象的方式。</span><span class="sxs-lookup"><span data-stu-id="6a869-116">Use the Minimap controls at the top-right of the model designer to change how you can view objects in Diagram View.</span></span> <span data-ttu-id="6a869-117">如果您在关系图视图中重新定位对象，则当您保存项目时，将保留该视图。</span><span class="sxs-lookup"><span data-stu-id="6a869-117">If you reposition objects in Diagram View, that view will be retained when you save the project.</span></span>  
  
2.  <span data-ttu-id="6a869-118">在模型设计器中，右键单击 `Product` 表，然后单击 "**创建层次结构**"。</span><span class="sxs-lookup"><span data-stu-id="6a869-118">In the model designer, right-click the `Product` table, and then click **Create Hierarchy**.</span></span> <span data-ttu-id="6a869-119">一个新的层次结构将出现在表窗口的底部。</span><span class="sxs-lookup"><span data-stu-id="6a869-119">A new hierarchy appears at the bottom of the table window.</span></span>  
  
3.  <span data-ttu-id="6a869-120">在层次结构名称中，通过键入重命名该层次结构， `Category` 然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="6a869-120">In the hierarchy name, rename the hierarchy by typing `Category`, and then press ENTER.</span></span>  
  
4.  <span data-ttu-id="6a869-121">在 `Product` 表中，单击 " **Product Category Name** " 列，然后将其拖到 `Category` 层次结构中，然后在该名称的顶部释放 `Category` 。</span><span class="sxs-lookup"><span data-stu-id="6a869-121">In the `Product` table, click the **Product Category Name** column, then drag it to the `Category` hierarchy, and then release on top of the `Category` name.</span></span>  
  
5.  <span data-ttu-id="6a869-122">在 `Category` 层次结构中，右键单击 "**产品类别名称**" 列，然后单击 "**重命名**"，然后键入 `Category` 。</span><span class="sxs-lookup"><span data-stu-id="6a869-122">In the `Category` hierarchy, right-click the **Product Category Name** column, then click **Rename**, and then type `Category`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6a869-123">重命名层次结构中的某个列不会重命名表中的该列。</span><span class="sxs-lookup"><span data-stu-id="6a869-123">Renaming a column in a hierarchy does not rename that column in the table.</span></span> <span data-ttu-id="6a869-124">层次结构中的列只是表中该列的表示形式。</span><span class="sxs-lookup"><span data-stu-id="6a869-124">A column in a hierarchy is just a representation of the column in the table.</span></span>  
  
6.  <span data-ttu-id="6a869-125">在 `Product` 表中，右键单击 "**产品子类别名称**" 列，然后在上下文菜单中指向 "**添加到层次结构**"，然后单击 "添加" `Category` 。</span><span class="sxs-lookup"><span data-stu-id="6a869-125">In the `Product` table, right-click the **Product Subcategory Name** column, then in the context menu, point to **Add to Hierarchy**, and then click `Category`.</span></span>  
  
7.  <span data-ttu-id="6a869-126">将**产品子类别名称**重命名为 `Subcategory` 。</span><span class="sxs-lookup"><span data-stu-id="6a869-126">Rename **Product Subcategory Name** to `Subcategory`.</span></span>  
  
8.  <span data-ttu-id="6a869-127">通过使用 "单击并拖动" 或使用上下文菜单中的 "**添加到层次结构**" 命令，将 "**型号名称**" 和 "**产品名称**" 列 (按顺序添加) 并将它们放置在 "**产品子类别名称**" 列下。</span><span class="sxs-lookup"><span data-stu-id="6a869-127">By using click and drag, or by using the **Add to Hierarchy** command in the context menu, add the **Model Name** and **Product Name** columns (in order) and place them beneath the **Product Subcategory Name** column.</span></span> <span data-ttu-id="6a869-128">分别重命名这些列 `Model` 和 `Product` 。</span><span class="sxs-lookup"><span data-stu-id="6a869-128">Rename these columns `Model` and `Product`, respectively.</span></span>  
  
#### <a name="to-create-hierarchies-in-the-date-table"></a><span data-ttu-id="6a869-129">在 Date 表中创建层次结构</span><span class="sxs-lookup"><span data-stu-id="6a869-129">To create hierarchies in the Date table</span></span>  
  
1.  <span data-ttu-id="6a869-130">在模型设计器中，右键单击“Date”\*\*\*\* 表，然后单击“创建层次结构”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6a869-130">In the model designer, right-click the **Date** table, and then click **Create Hierarchy**.</span></span>  
  
2.  <span data-ttu-id="6a869-131">将该层次结构重命名为 **Calendar**。</span><span class="sxs-lookup"><span data-stu-id="6a869-131">Rename the hierarchy to **Calendar**.</span></span>  
  
3.  <span data-ttu-id="6a869-132">按顺序添加下面各列，然后重命名它们：</span><span class="sxs-lookup"><span data-stu-id="6a869-132">Add the following columns, in-order, and then rename them:</span></span>  
  
    |<span data-ttu-id="6a869-133">列</span><span class="sxs-lookup"><span data-stu-id="6a869-133">Column</span></span>|<span data-ttu-id="6a869-134">重命名为：</span><span class="sxs-lookup"><span data-stu-id="6a869-134">Rename to:</span></span>|  
    |------------|----------------|  
    |<span data-ttu-id="6a869-135">Calendar Year</span><span class="sxs-lookup"><span data-stu-id="6a869-135">Calendar Year</span></span>|<span data-ttu-id="6a869-136">年龄</span><span class="sxs-lookup"><span data-stu-id="6a869-136">Year</span></span>|  
    |<span data-ttu-id="6a869-137">Calendar Semester</span><span class="sxs-lookup"><span data-stu-id="6a869-137">Calendar Semester</span></span>|<span data-ttu-id="6a869-138">Semester</span><span class="sxs-lookup"><span data-stu-id="6a869-138">Semester</span></span>|  
    |<span data-ttu-id="6a869-139">Calendar Quarter</span><span class="sxs-lookup"><span data-stu-id="6a869-139">Calendar Quarter</span></span>|<span data-ttu-id="6a869-140">Quarter</span><span class="sxs-lookup"><span data-stu-id="6a869-140">Quarter</span></span>|  
    |<span data-ttu-id="6a869-141">Month Calendar</span><span class="sxs-lookup"><span data-stu-id="6a869-141">Month Calendar</span></span>|<span data-ttu-id="6a869-142">月份</span><span class="sxs-lookup"><span data-stu-id="6a869-142">Month</span></span>|  
    |<span data-ttu-id="6a869-143">Day Of Month</span><span class="sxs-lookup"><span data-stu-id="6a869-143">Day Of Month</span></span>|<span data-ttu-id="6a869-144">天</span><span class="sxs-lookup"><span data-stu-id="6a869-144">Day</span></span>|  
  
4.  <span data-ttu-id="6a869-145">在“Date”\*\*\*\* 表中，重复上述步骤，创建“Fiscal”\*\*\*\* 层次结构，包括以下各列：</span><span class="sxs-lookup"><span data-stu-id="6a869-145">In the **Date** table, repeat the above steps, creating a **Fiscal** hierarchy, including the following columns:</span></span>  
  
    |<span data-ttu-id="6a869-146">列</span><span class="sxs-lookup"><span data-stu-id="6a869-146">Column</span></span>|<span data-ttu-id="6a869-147">重命名为：</span><span class="sxs-lookup"><span data-stu-id="6a869-147">Rename to:</span></span>|  
    |------------|----------------|  
    |<span data-ttu-id="6a869-148">Fiscal Year</span><span class="sxs-lookup"><span data-stu-id="6a869-148">Fiscal Year</span></span>|<span data-ttu-id="6a869-149">年龄</span><span class="sxs-lookup"><span data-stu-id="6a869-149">Year</span></span>|  
    |<span data-ttu-id="6a869-150">Fiscal Semester</span><span class="sxs-lookup"><span data-stu-id="6a869-150">Fiscal Semester</span></span>|<span data-ttu-id="6a869-151">Semester</span><span class="sxs-lookup"><span data-stu-id="6a869-151">Semester</span></span>|  
    |<span data-ttu-id="6a869-152">Fiscal Quarter</span><span class="sxs-lookup"><span data-stu-id="6a869-152">Fiscal Quarter</span></span>|<span data-ttu-id="6a869-153">Quarter</span><span class="sxs-lookup"><span data-stu-id="6a869-153">Quarter</span></span>|  
    |<span data-ttu-id="6a869-154">Month Calendar</span><span class="sxs-lookup"><span data-stu-id="6a869-154">Month Calendar</span></span>|<span data-ttu-id="6a869-155">月份</span><span class="sxs-lookup"><span data-stu-id="6a869-155">Month</span></span>|  
    |<span data-ttu-id="6a869-156">Day Of Month</span><span class="sxs-lookup"><span data-stu-id="6a869-156">Day Of Month</span></span>|<span data-ttu-id="6a869-157">天</span><span class="sxs-lookup"><span data-stu-id="6a869-157">Day</span></span>|  
  
5.  <span data-ttu-id="6a869-158">最后，在“Date”\*\*\*\* 表中，重复上述步骤，创建“Production Calendar”\*\*\*\* 层次结构，包括以下各列：</span><span class="sxs-lookup"><span data-stu-id="6a869-158">Finally, in the **Date** table, repeat the above steps, creating a **Production Calendar** hierarchy, including the following columns:</span></span>  
  
    |<span data-ttu-id="6a869-159">列</span><span class="sxs-lookup"><span data-stu-id="6a869-159">Column</span></span>|<span data-ttu-id="6a869-160">重命名为：</span><span class="sxs-lookup"><span data-stu-id="6a869-160">Rename to:</span></span>|  
    |------------|----------------|  
    |<span data-ttu-id="6a869-161">Calendar Year</span><span class="sxs-lookup"><span data-stu-id="6a869-161">Calendar Year</span></span>|<span data-ttu-id="6a869-162">年龄</span><span class="sxs-lookup"><span data-stu-id="6a869-162">Year</span></span>|  
    |<span data-ttu-id="6a869-163">Week Number Of Year</span><span class="sxs-lookup"><span data-stu-id="6a869-163">Week Number Of Year</span></span>|<span data-ttu-id="6a869-164">周</span><span class="sxs-lookup"><span data-stu-id="6a869-164">Week</span></span>|  
    |<span data-ttu-id="6a869-165">Day Of Week</span><span class="sxs-lookup"><span data-stu-id="6a869-165">Day Of Week</span></span>|<span data-ttu-id="6a869-166">天</span><span class="sxs-lookup"><span data-stu-id="6a869-166">Day</span></span>|  
  
## <a name="next-steps"></a><span data-ttu-id="6a869-167">后续步骤</span><span class="sxs-lookup"><span data-stu-id="6a869-167">Next Steps</span></span>  
 <span data-ttu-id="6a869-168">若要继续学习本教程，请转到下一课： [第 11 课：创建分区](lesson-10-create-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="6a869-168">To continue this tutorial, go to the next lesson: [Lesson 11: Create Partitions](lesson-10-create-partitions.md).</span></span>  
  
  
