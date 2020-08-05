---
title: 创建顺序分析和聚类分析挖掘模型结构 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9339227-6c2e-4c4b-8be2-8c1960bc4a8d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 37d0a1738a758a9d8c4fd6b80310037937a9803f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580486"
---
# <a name="creating-a-sequence-clustering-mining-model-structure-intermediate-data-mining-tutorial"></a><span data-ttu-id="51b9f-102">创建顺序分析和聚类分析挖掘模型结构（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="51b9f-102">Creating a Sequence Clustering Mining Model Structure (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="51b9f-103">要创建顺序分析和聚类分析挖掘模型，第一步是使用数据挖掘向导创建基于 [!INCLUDE[msCoName](../includes/msconame-md.md)] 顺序分析和聚类分析算法的新挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="51b9f-103">The first step in creating a sequence clustering mining model is to use the Data Mining Wizard to create a new mining structure and a mining model based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span>  
  
 <span data-ttu-id="51b9f-104">您将使用与市场篮分析相同的数据源视图，但需要添加一个包含 `sequence` 标识符的列。</span><span class="sxs-lookup"><span data-stu-id="51b9f-104">You will use the same data source view that you used for the market basket analysis, but you will add a column that contains the `sequence` identifier.</span></span> <span data-ttu-id="51b9f-105">在这种情况下，顺序表示客户将项添加到购物篮中的顺序。</span><span class="sxs-lookup"><span data-stu-id="51b9f-105">In this scenario, the sequence means the order in which the customer added items to the shopping basket.</span></span>  
  
 <span data-ttu-id="51b9f-106">还要添加一些列，在其中某一模型中使用，用于按照人口统计信息对客户进行分组。</span><span class="sxs-lookup"><span data-stu-id="51b9f-106">You will also add some columns that are used in one of the models to group customers by demographics.</span></span>  
  
### <a name="to-create-a-sequence-clustering-structure-and-model"></a><span data-ttu-id="51b9f-107">创建顺序分析和聚类分析结构和模型</span><span class="sxs-lookup"><span data-stu-id="51b9f-107">To create a sequence clustering structure and model</span></span>  
  
1.  <span data-ttu-id="51b9f-108">在的解决方案资源管理器中 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，右键单击 "**挖掘结构**"，然后选择 "**新建挖掘结构**"。</span><span class="sxs-lookup"><span data-stu-id="51b9f-108">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure**.</span></span>  
  
2.  <span data-ttu-id="51b9f-109">在 **“欢迎使用数据挖掘向导”** 页上，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="51b9f-109">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="51b9f-110">在 "**选择定义方法**" 页上，验证是否选择了 "**从现有关系数据库或数据仓库**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="51b9f-110">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="51b9f-111">在 "**创建数据挖掘结构**" 页上，验证是否选择了 "**创建具有挖掘模型的挖掘结构**" 选项。</span><span class="sxs-lookup"><span data-stu-id="51b9f-111">On the **Create the Data Mining Structure** page, verify that the option **Create mining structure with a mining model** is selected.</span></span> <span data-ttu-id="51b9f-112">接下来，单击选项的下拉列表 "**要使用何种数据挖掘技术？**"，然后选择 " **Microsoft 顺序分析**"。</span><span class="sxs-lookup"><span data-stu-id="51b9f-112">Next, click the dropdown list for the option, **Which data mining technique do you want to use?**, and select **Microsoft Sequence Clustering**.</span></span> <span data-ttu-id="51b9f-113">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="51b9f-113">Click **Next**.</span></span>  
  
     <span data-ttu-id="51b9f-114">此时将显示 "**选择数据源视图**" 页。</span><span class="sxs-lookup"><span data-stu-id="51b9f-114">The **Select Data Source View** page appears.</span></span> <span data-ttu-id="51b9f-115">在 "**可用数据源视图**" 下，选择 `Orders` 。</span><span class="sxs-lookup"><span data-stu-id="51b9f-115">Under **Available data source views**, select `Orders`.</span></span>  
  
     <span data-ttu-id="51b9f-116">“订单”也是用于市场篮方案的同一数据源视图。</span><span class="sxs-lookup"><span data-stu-id="51b9f-116">Orders is the same data source view that you used for the market basket scenario.</span></span> <span data-ttu-id="51b9f-117">如果尚未创建此数据源视图，请参阅[添加具有嵌套表的数据源视图 &#40;中级数据挖掘教程&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="51b9f-117">If you have not created this data source view, see [Adding a Data Source View with Nested Tables &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md).</span></span>  
  
5.  <span data-ttu-id="51b9f-118">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="51b9f-118">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="51b9f-119">在 "**指定表类型**" 页上，选中**vAssocSeqOrders**表旁边的 "**事例**" 复选框，然后选中 " **vAssocSeqLineItems** " 表旁边的 "**嵌套**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="51b9f-119">On the **Specify Table Types** page, select the **Case** check box next to the **vAssocSeqOrders** table, and select the **Nested** check box next to the **vAssocSeqLineItems** table.</span></span> <span data-ttu-id="51b9f-120">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="51b9f-120">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="51b9f-121">如果在选择**事例**或**嵌套**复选框时出现错误，则可能是数据源视图中的联接不正确。</span><span class="sxs-lookup"><span data-stu-id="51b9f-121">If an error occurs when you select the **Case** or **Nested** check boxes, it may be that the join in the data source view is not correct.</span></span> <span data-ttu-id="51b9f-122">嵌套表**vAssocSeqLineItems**必须通过多对一联接连接到事例表， **vAssocSeqOrders** 。</span><span class="sxs-lookup"><span data-stu-id="51b9f-122">The nested table, **vAssocSeqLineItems**, must be connected to the case table, **vAssocSeqOrders,** by a many-to-one join.</span></span> <span data-ttu-id="51b9f-123">可以通过右键单击联接行并反转联接的方向来编辑关系。</span><span class="sxs-lookup"><span data-stu-id="51b9f-123">You can edit the relationship by right-clicking on the join line and then reversing the direction of the join.</span></span> <span data-ttu-id="51b9f-124">有关详细信息，请参阅 "[创建或编辑关系" 对话框 &#40;Analysis Services 多维数据&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="51b9f-124">For more information, see [Create or Edit Relationship Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
7.  <span data-ttu-id="51b9f-125">在 "**指定定型数据**" 页上，通过选中复选框来选择要在模型中使用的列，如下所示：</span><span class="sxs-lookup"><span data-stu-id="51b9f-125">On the **Specify the Training Data** page, choose the columns for use in the model by selecting a check box as follows:</span></span>  
  
    -   <span data-ttu-id="51b9f-126">**IncomeGroup**选中 "**输入**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="51b9f-126">**IncomeGroup** Select the **Input** check box.</span></span>  
  
         <span data-ttu-id="51b9f-127">此列包含关于客户的重要相关信息，这些信息可以用于聚类分析。</span><span class="sxs-lookup"><span data-stu-id="51b9f-127">This column contains interesting information about the customers that you can use for clustering.</span></span> <span data-ttu-id="51b9f-128">您将在第一个模型中使用这些信息，然后在第二个模型中将其忽略。</span><span class="sxs-lookup"><span data-stu-id="51b9f-128">You will use it in the first model and then ignore it in the second model.</span></span>  
  
    -   <span data-ttu-id="51b9f-129">**OrderNumber**选中该 `Key` 复选框。</span><span class="sxs-lookup"><span data-stu-id="51b9f-129">**OrderNumber** Select the `Key` check box.</span></span>  
  
         <span data-ttu-id="51b9f-130">此字段将用作事例表的标识符，也就是 `Key`。</span><span class="sxs-lookup"><span data-stu-id="51b9f-130">This field will be used as the identifier for the case table, or `Key`.</span></span> <span data-ttu-id="51b9f-131">一般来说，在任何时候都不应使用事例表的键字段作为输入，因为该键包含的唯一值对聚类分析无用。</span><span class="sxs-lookup"><span data-stu-id="51b9f-131">In general, you should never use the key field of the case table as an input, because the key contains unique values that are not useful for clustering.</span></span>  
  
    -   <span data-ttu-id="51b9f-132">**区域**选中 "**输入**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="51b9f-132">**Region** Select the **Input** check box.</span></span>  
  
         <span data-ttu-id="51b9f-133">此列包含关于客户的重要相关信息，这些信息可以用于聚类分析。</span><span class="sxs-lookup"><span data-stu-id="51b9f-133">This column contains interesting information about the customers that you can use for clustering.</span></span> <span data-ttu-id="51b9f-134">您将在第一个模型中使用这些信息，然后在第二个模型中将其忽略。</span><span class="sxs-lookup"><span data-stu-id="51b9f-134">You will use it in the first model and then ignore it in the second model.</span></span>  
  
    -   <span data-ttu-id="51b9f-135">**LineNumber**选中 `Key` 和**输入**复选框。</span><span class="sxs-lookup"><span data-stu-id="51b9f-135">**LineNumber** Select the `Key` and **Input** check boxes.</span></span>  
  
         <span data-ttu-id="51b9f-136">**LineNumber**字段将用作嵌套表的标识符，或 `Sequence Key` 。</span><span class="sxs-lookup"><span data-stu-id="51b9f-136">The **LineNumber** field will be used as the identifier for the nested table, or `Sequence Key`.</span></span> <span data-ttu-id="51b9f-137">必须始终将嵌套表的键用于输入。</span><span class="sxs-lookup"><span data-stu-id="51b9f-137">The key for a nested table must always be used for input.</span></span>  
  
    -   <span data-ttu-id="51b9f-138">**模型**选中 "**输入**" 和 "**可预测**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="51b9f-138">**Model** Select the **Input** and **Predictable** check boxes.</span></span>  
  
     <span data-ttu-id="51b9f-139">确认所做选择正确无误，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="51b9f-139">Verify that the selections are correct, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="51b9f-140">在 "**指定列的内容和数据类型"** 页上，验证网格中是否包含下表中显示的列、内容类型和数据类型，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="51b9f-140">On the **Specify Columns' Content and Data Type** page, verify that the grid contains the columns, content types, and data types shown in the following table, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="51b9f-141">表/列</span><span class="sxs-lookup"><span data-stu-id="51b9f-141">Tables/Columns</span></span>|<span data-ttu-id="51b9f-142">内容类型</span><span class="sxs-lookup"><span data-stu-id="51b9f-142">Content Type</span></span>|<span data-ttu-id="51b9f-143">数据类型</span><span class="sxs-lookup"><span data-stu-id="51b9f-143">Data Type</span></span>|  
    |---------------------|------------------|---------------|  
    |<span data-ttu-id="51b9f-144">IncomeGroup</span><span class="sxs-lookup"><span data-stu-id="51b9f-144">IncomeGroup</span></span>|<span data-ttu-id="51b9f-145">离散</span><span class="sxs-lookup"><span data-stu-id="51b9f-145">Discrete</span></span>|<span data-ttu-id="51b9f-146">文本</span><span class="sxs-lookup"><span data-stu-id="51b9f-146">Text</span></span>|  
    |<span data-ttu-id="51b9f-147">OrderNumber</span><span class="sxs-lookup"><span data-stu-id="51b9f-147">OrderNumber</span></span>|<span data-ttu-id="51b9f-148">密钥</span><span class="sxs-lookup"><span data-stu-id="51b9f-148">Key</span></span>|<span data-ttu-id="51b9f-149">文本</span><span class="sxs-lookup"><span data-stu-id="51b9f-149">Text</span></span>|  
    |<span data-ttu-id="51b9f-150">区域</span><span class="sxs-lookup"><span data-stu-id="51b9f-150">Region</span></span>|<span data-ttu-id="51b9f-151">离散</span><span class="sxs-lookup"><span data-stu-id="51b9f-151">Discrete</span></span>|<span data-ttu-id="51b9f-152">文本</span><span class="sxs-lookup"><span data-stu-id="51b9f-152">Text</span></span>|  
    |<span data-ttu-id="51b9f-153">vAssocSeqLineItems</span><span class="sxs-lookup"><span data-stu-id="51b9f-153">vAssocSeqLineItems</span></span>|||  
    |<span data-ttu-id="51b9f-154">Line Number</span><span class="sxs-lookup"><span data-stu-id="51b9f-154">Line Number</span></span>|<span data-ttu-id="51b9f-155">键序列</span><span class="sxs-lookup"><span data-stu-id="51b9f-155">Key Sequence</span></span>|<span data-ttu-id="51b9f-156">Long</span><span class="sxs-lookup"><span data-stu-id="51b9f-156">Long</span></span>|  
    |<span data-ttu-id="51b9f-157">模型</span><span class="sxs-lookup"><span data-stu-id="51b9f-157">Model</span></span>|<span data-ttu-id="51b9f-158">离散</span><span class="sxs-lookup"><span data-stu-id="51b9f-158">Discrete</span></span>|<span data-ttu-id="51b9f-159">文本</span><span class="sxs-lookup"><span data-stu-id="51b9f-159">Text</span></span>|  
  
9. <span data-ttu-id="51b9f-160">在 "**创建测试集**" 页上，将**测试的数据百分比**更改为20，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="51b9f-160">On the **Create Testing Set** page, change the **Percentage of data for testing** to 20, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="51b9f-161">在 "**完成向导**" 页的 "**挖掘结构名称**" 中，键入 `Sequence Clustering with Region` 。</span><span class="sxs-lookup"><span data-stu-id="51b9f-161">On the **Completing the Wizard** page, for the **Mining structure name**, type `Sequence Clustering with Region`.</span></span>  
  
11. <span data-ttu-id="51b9f-162">对于 "**挖掘模型名称**"，请键入 `Sequence Clustering with Region` 。</span><span class="sxs-lookup"><span data-stu-id="51b9f-162">For the **Mining model name**, type `Sequence Clustering with Region`.</span></span>  
  
12. <span data-ttu-id="51b9f-163">选中 "**允许钻取**" 框，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="51b9f-163">Check the **Allow drill through** box, and then click **Finish**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="51b9f-164">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="51b9f-164">Next Task in Lesson</span></span>  
 [<span data-ttu-id="51b9f-165">处理顺序分析和聚类分析模型</span><span class="sxs-lookup"><span data-stu-id="51b9f-165">Processing the Sequence Clustering Model</span></span>](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="51b9f-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="51b9f-166">See Also</span></span>  
 <span data-ttu-id="51b9f-167">[数据挖掘设计器](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="51b9f-167">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="51b9f-168">Microsoft 顺序分析和聚类分析算法</span><span class="sxs-lookup"><span data-stu-id="51b9f-168">Microsoft Sequence Clustering Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)  
  
  
