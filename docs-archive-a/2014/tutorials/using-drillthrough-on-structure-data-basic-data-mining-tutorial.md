---
title: 对结构数据使用钻取 (基本数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a693979c-0564-4d6d-b35d-cbbc8f350469
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 49a1ced27150676def541548f47a90a3f847c8ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577114"
---
# <a name="using-drillthrough-on-structure-data-basic-data-mining-tutorial"></a><span data-ttu-id="c1eb1-102">对结构数据使用钻取（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="c1eb1-102">Using Drillthrough on Structure Data (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="c1eb1-103">作为其广告营销活动的一部分， [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 将发送给潜在客户的34-40 年龄人口部分。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-103">As part of their advertising campaign, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] is sending a mailer to potential customers in the 34-40 age demographic.</span></span> <span data-ttu-id="c1eb1-104">市场部已决定还要向五年多以前从 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 购买自行车的客户发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-104">The marketing department has decided that they would also like to send the mailer to the customers who purchased bikes from [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] more than five years ago.</span></span> <span data-ttu-id="c1eb1-105">在本课中，您将标识拥有旧自行车的客户并检索其联系信息。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-105">In this lesson you will identify customers with older bikes and retrieve their contact information.</span></span> <span data-ttu-id="c1eb1-106">模型中不包括此信息，但结构中包括此信息。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-106">This information is not included in the model, but is included in the structure.</span></span> <span data-ttu-id="c1eb1-107">若要检索联系信息，您需要首先确保已对结构启用了钻取，然后使用钻取来显示目标客户的姓名和地址。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-107">To retrieve the contact information you will first ensure that drillthrough is enabled for the structure and then you will use drillthrough to reveal the names and addresses of the targeted customers.</span></span>  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a><span data-ttu-id="c1eb1-108">对挖掘模型启用钻取</span><span class="sxs-lookup"><span data-stu-id="c1eb1-108">To enable drillthrough on a mining model</span></span>  
  
1.  <span data-ttu-id="c1eb1-109">在的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 数据挖掘设计器的 "**挖掘模型**" 选项卡上，右键单击**TM_Decision_Tree**模型，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-109">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Mining Models** tab of Data Mining Designer, right-click the **TM_Decision_Tree** model, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="c1eb1-110">在“属性”窗口中，单击 **AllowDrillthrough**，再选择 **True**。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-110">In the Properties windows, click **AllowDrillthrough**, and select **True**.</span></span>  
  
3.  <span data-ttu-id="c1eb1-111">在“挖掘模型”选项卡中，右键单击所需的模型，再选择“处理模型”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-111">In the Mining Models tab, right-click the model, and select **Process Model**.</span></span>  
  
 <span data-ttu-id="c1eb1-112">有关详细信息，请参阅[钻取查询 &#40;数据挖掘&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="c1eb1-112">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)</span></span>  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a><span data-ttu-id="c1eb1-113">查看挖掘模型的钻取数据</span><span class="sxs-lookup"><span data-stu-id="c1eb1-113">To view drillthrough data from a mining model</span></span>  
  
1.  <span data-ttu-id="c1eb1-114">在数据挖掘设计器中，单击 **“挖掘模型查看器”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-114">In Data Mining Designer, click the **Mining Model Viewer** tab.</span></span>  
  
2.  <span data-ttu-id="c1eb1-115">从 "**挖掘模型**" 列表中选择**TM_Decision_Tree**模型。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-115">Select the **TM_Decision_Tree** model from the **Mining Model** list.</span></span>  
  
3.  <span data-ttu-id="c1eb1-116">将 "**背景**" 值更改为 `1` 。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-116">Change the **Background** value to `1`.</span></span> <span data-ttu-id="c1eb1-117">这样做之后，您将只显示与购买了自行车的客户相关的模型部分。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-117">By doing this, you show only the part of the model that is related to customer who bought bikes.</span></span>  
  
4.  <span data-ttu-id="c1eb1-118">从 **“查看器”** 列表中，选择“Microsoft 树查看器”。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-118">Select the Microsoft Tree viewer from the **Viewer** list.</span></span> <span data-ttu-id="c1eb1-119">这将强制使用新的筛选条件刷新查看器。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-119">This will force the viewer to refresh with the new filter conditions.</span></span> <span data-ttu-id="c1eb1-120">然后，找到**Age >= 34 41 <，** 并右键单击该节点。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-120">Then, locate the **Age >=34 and <41** node and right-click the node.</span></span>  
  
5.  <span data-ttu-id="c1eb1-121">选择 **“钻取”**，然后选择 **“模型和结构列”** 以打开 **“钻取”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-121">Select **Drill Through**, and then select **Model and Structure Columns** to open the **Drill Through** window.</span></span>  
  
6.  <span data-ttu-id="c1eb1-122">滚动到 **Structure.Date First Purchase** 列以查看旧自行车的购买日期。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-122">Scroll to the **Structure.Date First Purchase** column to view the purchase dates for the older bikes.</span></span>  
  
7.  <span data-ttu-id="c1eb1-123">若要将数据复制到剪贴板，请右键单击表中的任何行，并选择“全部复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-123">To copy the data to the Clipboard, right-click any row in the table, and select **Copy All**.</span></span>  
  
 <span data-ttu-id="c1eb1-124">恭喜您！您已经完成了数据挖掘基础教程。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-124">Congratulations, you have completed the basic data mining tutorial.</span></span> <span data-ttu-id="c1eb1-125">既然您已经熟练掌握了数据挖掘工具，我们建议您同时完成数据挖掘中级教程，中级教程将演示如何创建用于预测、市场篮分析以及顺序分析和聚类分析的模型。</span><span class="sxs-lookup"><span data-stu-id="c1eb1-125">Now that you are comfortable using the data mining tools, we recommend that you also complete the intermediate data mining tutorial, which demonstrates how to create models for forecasting, market basket analysis, and sequence clustering.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="c1eb1-126">课程中的前一个任务</span><span class="sxs-lookup"><span data-stu-id="c1eb1-126">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="c1eb1-127">创建预测（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="c1eb1-127">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="c1eb1-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c1eb1-128">See Also</span></span>  
 [<span data-ttu-id="c1eb1-129">使用预测查询生成器创建预测查询</span><span class="sxs-lookup"><span data-stu-id="c1eb1-129">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
