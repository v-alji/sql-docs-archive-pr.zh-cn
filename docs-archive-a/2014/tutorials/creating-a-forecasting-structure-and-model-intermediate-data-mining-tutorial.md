---
title: 创建预测结构和模型 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5f55cbf6-0db4-4cb4-a0f5-e27441873d4f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d77b15a9a8efe9a9c6faec49a2274ee182706992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682474"
---
# <a name="creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="6339b-102">创建预测结构和模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="6339b-102">Creating a Forecasting Structure and Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="6339b-103">现在您将使用数据挖掘向导，基于刚创建的数据源视图创建新的挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="6339b-103">Next, you will use the Data Mining Wizard to create a new mining structure and mining model based on the data source view that you just created.</span></span> <span data-ttu-id="6339b-104">在本任务中，您将指定挖掘模型应使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 时序算法。</span><span class="sxs-lookup"><span data-stu-id="6339b-104">In this task you will specify that the mining model should use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm.</span></span>  
  
### <a name="to-create-a-forecasting-mining-structure"></a><span data-ttu-id="6339b-105">创建预测挖掘结构</span><span class="sxs-lookup"><span data-stu-id="6339b-105">To create a forecasting mining structure</span></span>  
  
1.  <span data-ttu-id="6339b-106">在的解决方案资源管理器中 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，右键单击 "**挖掘结构**"，然后选择 "**新建挖掘结构**"。</span><span class="sxs-lookup"><span data-stu-id="6339b-106">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure**.</span></span>  
  
2.  <span data-ttu-id="6339b-107">在 **“欢迎使用数据挖掘向导”** 页上，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="6339b-107">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="6339b-108">在 "**选择定义方法**" 页上，验证是否选择了 "**从现有关系数据库或数据仓库**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="6339b-108">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="6339b-109">在 "**创建数据挖掘结构**" 页上，在 "**要使用何种数据挖掘技术？**" 下，选择 " **Microsoft 时序**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="6339b-109">On the **Create the Data Mining Structure** page, under **Which data mining technique do you want to use?**, select **Microsoft Time Series**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="6339b-110">在 "**选择数据源视图**" 页上的 "**可用数据源视图**" 下，选择**salesbyregion.dsv**。</span><span class="sxs-lookup"><span data-stu-id="6339b-110">On the **Select Data Source View** page, under **Available data source views**, select **SalesByRegion**.</span></span>  
  
6.  <span data-ttu-id="6339b-111">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="6339b-111">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="6339b-112">在 "**指定表类型**" 页上，确保选中 "vTimeSeries" 表的 "**事例**" 列中的复选框，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="6339b-112">On the **Specify Table Types** page, ensure that the check box in the **Case** column for the vTimeSeries table is selected, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="6339b-113">在 "**指定定型数据**" 页上，选中 ModelRegion 和 ReportingDate 列的**键**列中的复选框。</span><span class="sxs-lookup"><span data-stu-id="6339b-113">On the **Specify the Training Data** page, select the check boxes in the **Key** column for the ModelRegion and ReportingDate columns.</span></span>  
  
     <span data-ttu-id="6339b-114">ReportingDate 默认情况下应处于选中状态，因为您在创建数据源视图时已经将该列指定为逻辑主键。</span><span class="sxs-lookup"><span data-stu-id="6339b-114">ReportingDate should be selected by default, because you specified this column as the logical primary key when you created the data source view.</span></span> <span data-ttu-id="6339b-115">通过将 ModelRegion 添加为第二个键，您将指示此算法为该字段中列出的每个模型和地区组合创建一个单独的时序。</span><span class="sxs-lookup"><span data-stu-id="6339b-115">By adding ModelRegion as a second key, you are telling the algorithm to create a separate time series for each combination of model and region listed in this field.</span></span>  
  
9. <span data-ttu-id="6339b-116">选中 "数量" 列的 "**输入**" 和 "**可预测**" 列中的复选框，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="6339b-116">Select the check boxes in the **Input** and **Predictable** columns for the Quantity, column, and then click **Next**.</span></span>  
  
     <span data-ttu-id="6339b-117">通过选择 "**可预测**"，您可以指示要对此列中的数据创建预测。</span><span class="sxs-lookup"><span data-stu-id="6339b-117">By selecting **Predictable**, you indicate that you want to create forecasts on the data in this column.</span></span> <span data-ttu-id="6339b-118">但是，由于您希望预测基于以前的数据，还必须添加该列作为输入。</span><span class="sxs-lookup"><span data-stu-id="6339b-118">However, because you want to base the forecasts on past data, you must also add the column as an input.</span></span>  
  
10. <span data-ttu-id="6339b-119">在 "**指定列的内容和数据类型**" 页上，查看所选内容。</span><span class="sxs-lookup"><span data-stu-id="6339b-119">On the page **Specify Columns' Content and Data Type**, review the selections.</span></span>  
  
     <span data-ttu-id="6339b-120">将 ModelRegion 列指定为**键**列，并将 ReportingDate 列自动指定为**key Time**列。</span><span class="sxs-lookup"><span data-stu-id="6339b-120">The ModelRegion column is designated as a **Key** column and the ReportingDate column is automatically designated as a **Key Time** column.</span></span> <span data-ttu-id="6339b-121">您只能拥有一种类型的键。</span><span class="sxs-lookup"><span data-stu-id="6339b-121">You can have only one of each type of key.</span></span>  
  
11. <span data-ttu-id="6339b-122">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="6339b-122">Click **Next**.</span></span>  
  
12. <span data-ttu-id="6339b-123">在 "**完成向导**" 页的 "**挖掘结构名称**" 中，键入 `Forecasting` 。</span><span class="sxs-lookup"><span data-stu-id="6339b-123">On the **Completing the Wizard** page, for **Mining structure name**, type `Forecasting`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6339b-124">用来启用钻取的选项对于时序模型不可用。</span><span class="sxs-lookup"><span data-stu-id="6339b-124">The option to enable drillthrough is not available for time series models.</span></span>  
  
13. <span data-ttu-id="6339b-125">在 "**挖掘模型名称**" 中，键入 `Forecasting` ，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="6339b-125">In **Mining model name**, type `Forecasting`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="6339b-126">此时将打开数据挖掘设计器，显示 `Forecasting` 您刚创建的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="6339b-126">Data Mining Designer opens to display the `Forecasting` mining structure that you just created.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6339b-127">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="6339b-127">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6339b-128">&#40;中级数据挖掘教程修改预测结构&#41;</span><span class="sxs-lookup"><span data-stu-id="6339b-128">Modifying the Forecasting Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="6339b-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6339b-129">See Also</span></span>  
 <span data-ttu-id="6339b-130">[数据挖掘设计器](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="6339b-130">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="6339b-131">Microsoft 时序算法</span><span class="sxs-lookup"><span data-stu-id="6339b-131">Microsoft Time Series Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
