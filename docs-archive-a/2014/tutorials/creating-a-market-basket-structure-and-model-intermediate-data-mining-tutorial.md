---
title: 创建市场篮结构和模型 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 659b7a4e-f687-44d9-a60a-86490ccbf90f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b276fe5bed1d9df8e8b2e3e2826966b6abfb734e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577173"
---
# <a name="creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="00d63-102">创建市场篮结构和模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="00d63-102">Creating a Market Basket Structure and Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="00d63-103">您已创建了一个数据源视图，现在将使用数据挖掘向导创建一个新的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="00d63-103">Now that you have created a data source view, you will use the Data Mining Wizard to create a new mining structure.</span></span> <span data-ttu-id="00d63-104">在本任务中，将创建基于 [!INCLUDE[msCoName](../includes/msconame-md.md)] 关联算法的挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="00d63-104">In this task, you will create a mining structure and a mining model that is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="00d63-105">如果遇到说明 vAssocSeqLineItems 不能用作嵌套表的错误，请返回本课中的前一个任务，并确保通过从 vAssocSeqLineItems 表（多端）拖到 vAssocSeqOrders 表（一端）来创建多对一联接。</span><span class="sxs-lookup"><span data-stu-id="00d63-105">If you encounter an error stating that vAssocSeqLineItems cannot be used as a nested table, return to the previous task in the lesson, and be sure to create the many-to-one join by dragging from the vAssocSeqLineItems table (the many side) to the vAssocSeqOrders table (the one side).</span></span> <span data-ttu-id="00d63-106">还可以通过右键单击联接线来编辑这两个表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="00d63-106">You can also edit the relationship between the tables by right-clicking the join line.</span></span>  
  
### <a name="to-create-an-association-mining-structure"></a><span data-ttu-id="00d63-107">创建关联挖掘结构</span><span class="sxs-lookup"><span data-stu-id="00d63-107">To create an association mining structure</span></span>  
  
1.  <span data-ttu-id="00d63-108">在的解决方案资源管理器中 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，右键单击 "**挖掘结构**"，然后选择 "**新建挖掘结构**" 以打开数据挖掘向导。</span><span class="sxs-lookup"><span data-stu-id="00d63-108">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure** to open the Data Mining Wizard.</span></span>  
  
2.  <span data-ttu-id="00d63-109">在 **“欢迎使用数据挖掘向导”** 页上，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="00d63-109">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="00d63-110">在 "**选择定义方法**" 页上，验证是否选择了 "**从现有关系数据库或数据仓库**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="00d63-110">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="00d63-111">在 "**创建数据挖掘结构**" 页上，在 "**要使用何种数据挖掘技术？**" 下，从列表中选择 " **Microsoft 关联规则**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="00d63-111">On the **Create the Data Mining Structure** page, under **Which data mining technique do you want to use?**, select **Microsoft Association Rules** from the list, and then click **Next**.</span></span> <span data-ttu-id="00d63-112">此时将显示 "**选择数据源视图**" 页。</span><span class="sxs-lookup"><span data-stu-id="00d63-112">The **Select Data Source View** page appears.</span></span>  
  
5.  <span data-ttu-id="00d63-113">选择 "**可用数据源视图**" 下的**订单**，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="00d63-113">Select **Orders**under **Available data source views**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="00d63-114">在 "**指定表类型**" 页上，在 vAssocSeqLineItems 表的行中选中 "**嵌套**" 复选框，并在嵌套表 vAssocSeqOrders 的行中选中 "**事例**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="00d63-114">On the **Specify Table Types** page, in the row for the vAssocSeqLineItems table, select the **Nested** check box, and in the row for the nested table vAssocSeqOrders, select the **Case** check box.</span></span> <span data-ttu-id="00d63-115">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="00d63-115">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="00d63-116">在 "**指定定型数据**" 页上，清除可能选中的任何框。</span><span class="sxs-lookup"><span data-stu-id="00d63-116">On the **Specify the Training Data** page, clear any boxes that might be checked.</span></span> <span data-ttu-id="00d63-117">通过选中 "OrderNumber" 旁边的 "**键**" 复选框，为事例表 vAssocSeqOrders 设置密钥。</span><span class="sxs-lookup"><span data-stu-id="00d63-117">Set the key for the case table, vAssocSeqOrders, by selecting the **Key** check box next to OrderNumber.</span></span>  
  
     <span data-ttu-id="00d63-118">由于市场篮分析的目的是确定单个交易中包含哪些产品，因此不必使用**CustomerKey**字段。</span><span class="sxs-lookup"><span data-stu-id="00d63-118">Because the purpose of the market basket analysis is to determine which products are included in a single transaction, you do not have to use the **CustomerKey** field.</span></span>  
  
8.  <span data-ttu-id="00d63-119">通过选择 "模型" 旁边的 "**键**" 复选框，设置嵌套表 vAssocSeqLineItems 的键。</span><span class="sxs-lookup"><span data-stu-id="00d63-119">Set the key for the nested table, vAssocSeqLineItems, by selecting the **Key** check box next to Model.</span></span> <span data-ttu-id="00d63-120">执行此操作时，还会自动选择 "**输入**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="00d63-120">The **Input** check box is also automatically selected when you do this.</span></span> <span data-ttu-id="00d63-121">同时选中 "**可预测**" 复选框 `Model` 。</span><span class="sxs-lookup"><span data-stu-id="00d63-121">Select the **Predictable** check box for `Model` as well.</span></span>  
  
     <span data-ttu-id="00d63-122">在市场篮模型中，你不关心购物篮中产品的顺序，因此，不应将**LineNumber**作为嵌套表的键。</span><span class="sxs-lookup"><span data-stu-id="00d63-122">In a market basket model, you do not care about the sequence of products in the shopping basket, and therefore you should not include **LineNumber** as a key for the nested table.</span></span> <span data-ttu-id="00d63-123">只在序列非常重要的模型中使用**LineNumber**作为键。</span><span class="sxs-lookup"><span data-stu-id="00d63-123">You would use **LineNumber** as a key only in a model where the sequence is important.</span></span> <span data-ttu-id="00d63-124">您将在第 4 课中创建使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 顺序分析和聚类分析算法的模型。</span><span class="sxs-lookup"><span data-stu-id="00d63-124">You will create a model that uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm in Lesson 4.</span></span>  
  
9. <span data-ttu-id="00d63-125">选中 IncomeGroup 和 Region 左侧的复选框，但是不进行任何其他选择。</span><span class="sxs-lookup"><span data-stu-id="00d63-125">Select the check box to the left of IncomeGroup and Region,but do not make any other selections.</span></span> <span data-ttu-id="00d63-126">选中最左侧的列会将这些列添加到结构中以供日后参考，但不会用在模型中。</span><span class="sxs-lookup"><span data-stu-id="00d63-126">Checking the leftmost column adds the columns to the structure for later reference, but the columns will not be used in the model.</span></span> <span data-ttu-id="00d63-127">您选择的内容应如下所示：</span><span class="sxs-lookup"><span data-stu-id="00d63-127">Your selections should look like the following:</span></span>  
  
     <span data-ttu-id="00d63-128">![对话框外观如何](../../2014/tutorials/media/tutorial-configassocmodel.gif "对话框外观如何")</span><span class="sxs-lookup"><span data-stu-id="00d63-128">![how dialog box should look](../../2014/tutorials/media/tutorial-configassocmodel.gif "how dialog box should look")</span></span>  
  
10. <span data-ttu-id="00d63-129">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="00d63-129">Click **Next**.</span></span>  
  
11. <span data-ttu-id="00d63-130">在 "**指定列的内容和数据类型"** 页上，查看应如下表所示的选择，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="00d63-130">On the **Specify Columns' Content and Data Type**page, review the selections, which should be as shown in the following table, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="00d63-131">列</span><span class="sxs-lookup"><span data-stu-id="00d63-131">Columns</span></span>|<span data-ttu-id="00d63-132">内容类型</span><span class="sxs-lookup"><span data-stu-id="00d63-132">Content Type</span></span>|<span data-ttu-id="00d63-133">数据类型</span><span class="sxs-lookup"><span data-stu-id="00d63-133">Data Type</span></span>|  
    |-------------|------------------|---------------|  
    |<span data-ttu-id="00d63-134">IncomeGroup</span><span class="sxs-lookup"><span data-stu-id="00d63-134">IncomeGroup</span></span>|<span data-ttu-id="00d63-135">离散</span><span class="sxs-lookup"><span data-stu-id="00d63-135">Discrete</span></span>|<span data-ttu-id="00d63-136">文本</span><span class="sxs-lookup"><span data-stu-id="00d63-136">Text</span></span>|  
    |<span data-ttu-id="00d63-137">订单编号</span><span class="sxs-lookup"><span data-stu-id="00d63-137">Order Number</span></span>|<span data-ttu-id="00d63-138">密钥</span><span class="sxs-lookup"><span data-stu-id="00d63-138">Key</span></span>|<span data-ttu-id="00d63-139">文本</span><span class="sxs-lookup"><span data-stu-id="00d63-139">Text</span></span>|  
    |<span data-ttu-id="00d63-140">区域</span><span class="sxs-lookup"><span data-stu-id="00d63-140">Region</span></span>|<span data-ttu-id="00d63-141">离散</span><span class="sxs-lookup"><span data-stu-id="00d63-141">Discrete</span></span>|<span data-ttu-id="00d63-142">文本</span><span class="sxs-lookup"><span data-stu-id="00d63-142">Text</span></span>|  
    |<span data-ttu-id="00d63-143">vAssocSeqLineItems</span><span class="sxs-lookup"><span data-stu-id="00d63-143">vAssocSeqLineItems</span></span>|||  
    |<span data-ttu-id="00d63-144">模型</span><span class="sxs-lookup"><span data-stu-id="00d63-144">Model</span></span>|<span data-ttu-id="00d63-145">密钥</span><span class="sxs-lookup"><span data-stu-id="00d63-145">Key</span></span>|<span data-ttu-id="00d63-146">文本</span><span class="sxs-lookup"><span data-stu-id="00d63-146">Text</span></span>|  
  
12. <span data-ttu-id="00d63-147">在 "**创建测试集**" 页上，"**测试数据百分比**" 选项的默认值为30%。</span><span class="sxs-lookup"><span data-stu-id="00d63-147">On the **Create testing set** page, the default value for the option **Percentage of data for testing** is 30 percent.</span></span> <span data-ttu-id="00d63-148">将此更改为**0**。</span><span class="sxs-lookup"><span data-stu-id="00d63-148">Change this to **0**.</span></span> <span data-ttu-id="00d63-149">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="00d63-149">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="00d63-150">为测量模型精确度提供不同的图表。</span><span class="sxs-lookup"><span data-stu-id="00d63-150">provides different charts for measuring model accuracy.</span></span> <span data-ttu-id="00d63-151">但是，某些精确度图表类型（如提升图和交叉验证报告）旨在进行分类和估计。</span><span class="sxs-lookup"><span data-stu-id="00d63-151">However, some accuracy chart types, such as the lift chart and cross-validation report, are designed for classification and estimation.</span></span> <span data-ttu-id="00d63-152">关联预测不支持这些方法。</span><span class="sxs-lookup"><span data-stu-id="00d63-152">They are not supported for associative prediction.</span></span>  
  
13. <span data-ttu-id="00d63-153">在 "**完成向导**" 页上的 "**挖掘结构名称**" 中，键入 `Association` 。</span><span class="sxs-lookup"><span data-stu-id="00d63-153">On the **Completing the Wizard** page, in **Mining structure name**, type `Association`.</span></span>  
  
14. <span data-ttu-id="00d63-154">在 "**挖掘模型名称**" 中，键入 `Association` 。</span><span class="sxs-lookup"><span data-stu-id="00d63-154">In **Mining model name**, type `Association`.</span></span>  
  
15. <span data-ttu-id="00d63-155">选择 "**允许钻取**" 选项，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="00d63-155">Select the option **Allow drill through**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="00d63-156">此时将打开数据挖掘设计器，显示 `Association` 您刚创建的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="00d63-156">Data Mining Designer opens to display the `Association` mining structure that you just created.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="00d63-157">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="00d63-157">Next Task in Lesson</span></span>  
 [<span data-ttu-id="00d63-158">&#40;中级数据挖掘教程来修改和处理市场篮模型&#41;</span><span class="sxs-lookup"><span data-stu-id="00d63-158">Modifying and Processing the Market Basket Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="00d63-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00d63-159">See Also</span></span>  
 <span data-ttu-id="00d63-160">[Microsoft 关联算法](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="00d63-160">[Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span></span>  
 [<span data-ttu-id="00d63-161">内容类型（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="00d63-161">Content Types &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/content-types-data-mining.md)  
  
  
