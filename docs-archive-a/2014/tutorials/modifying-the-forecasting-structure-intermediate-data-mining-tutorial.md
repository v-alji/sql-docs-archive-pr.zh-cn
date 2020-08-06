---
title: " (中级数据挖掘教程) 修改预测结构 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1a6c138e-643b-4ae6-ad08-93631f149c20
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9acf410fe04c53493e559257832e5e21727bc45b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577154"
---
# <a name="modifying-the-forecasting-structure-intermediate-data-mining-tutorial"></a><span data-ttu-id="d0667-102">修改预测结构（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="d0667-102">Modifying the Forecasting Structure (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="d0667-103">您在上一个任务中创建的挖掘结构包含单个预测模型。</span><span class="sxs-lookup"><span data-stu-id="d0667-103">The mining structure that you created in the previous task contains a single forecasting model.</span></span> <span data-ttu-id="d0667-104">在处理和浏览该模型之前，您必须对其结构稍加更改并修改它的一个属性。</span><span class="sxs-lookup"><span data-stu-id="d0667-104">Before you process and explore the model, you must change its structure slightly and modify one of its properties.</span></span>  
  
## <a name="modifying-the-mining-structure"></a><span data-ttu-id="d0667-105">修改挖掘结构</span><span class="sxs-lookup"><span data-stu-id="d0667-105">Modifying the Mining Structure</span></span>  
 <span data-ttu-id="d0667-106">您可以使用数据挖掘设计器的 "**挖掘结构**" 选项卡来更改挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="d0667-106">You can change the mining structure by using the **Mining Structure** tab of Data Mining Designer.</span></span> <span data-ttu-id="d0667-107">您在使用数据挖掘向导创建该模型时，使用了以下三个列：ReportingDate、ModelRegion 和 Quantity。</span><span class="sxs-lookup"><span data-stu-id="d0667-107">When you created the model with the Data Mining Wizard, you used three columns: ReportingDate, ModelRegion, and Quantity.</span></span> <span data-ttu-id="d0667-108">但是，**预测**表还包含一个 "金额" 列，可以使用它来预测销售额。</span><span class="sxs-lookup"><span data-stu-id="d0667-108">However, the **Forecasting** table also contains an Amount column, which you can use to forecast the amount of sales.</span></span> <span data-ttu-id="d0667-109">通过使用 "**挖掘结构**" 选项卡，您可以从数据源视图将此列添加到挖掘结构中。</span><span class="sxs-lookup"><span data-stu-id="d0667-109">By using the **Mining Structure** tab, you can add this column from the data source view to the mining structure.</span></span>  
  
#### <a name="to-add-the-amount-column-to-the-forecasting-mining-structure"></a><span data-ttu-id="d0667-110">将“金额”列添加到“预测”挖掘结构</span><span class="sxs-lookup"><span data-stu-id="d0667-110">To add the Amount column to the Forecasting mining structure</span></span>  
  
1.  <span data-ttu-id="d0667-111">在数据挖掘设计器的 "**挖掘结构**" 选项卡上，在 "**数据源视图**" 窗格中，选择 "vTimeSeries" 表中的 "金额" 列。</span><span class="sxs-lookup"><span data-stu-id="d0667-111">On the **Mining Structure** tab of Data Mining Designer, in the **Data Source View** pane, select the Amount column in the vTimeSeries table.</span></span>  
  
2.  <span data-ttu-id="d0667-112">将 "数量" 列从 "**数据源视图**" 窗格拖到 "**预测**" 结构的列的列表中。</span><span class="sxs-lookup"><span data-stu-id="d0667-112">Drag the Amount column from the **Data Source View** pane into the list of columns for the **Forecasting** structure.</span></span>  
  
     <span data-ttu-id="d0667-113">"金额" 列现在包含在**预测**挖掘结构中。</span><span class="sxs-lookup"><span data-stu-id="d0667-113">The Amount column is now included in the **Forecasting** mining structure.</span></span>  
  
## <a name="modifying-the-columns-in-the-mining-model"></a><span data-ttu-id="d0667-114">修改挖掘模型中的列</span><span class="sxs-lookup"><span data-stu-id="d0667-114">Modifying the Columns in the Mining Model</span></span>  
 <span data-ttu-id="d0667-115">由于向结构中添加了新列，所以必须定义模型使用该列的方式。</span><span class="sxs-lookup"><span data-stu-id="d0667-115">Because you added a new column to the structure, you must define how the model will use the column.</span></span> <span data-ttu-id="d0667-116">您可以在数据挖掘设计器的 "**挖掘模型**" 选项卡上指定列的使用方式。</span><span class="sxs-lookup"><span data-stu-id="d0667-116">You can specify how the column will be used on the **Mining Models** tab of Data Mining Designer.</span></span>  
  
 <span data-ttu-id="d0667-117">"**挖掘模型**" 选项卡列出了挖掘结构在网格的 "**结构**" 列中包含的列，并列出了该挖掘模型包含的列（在此情况下为**预测**）。</span><span class="sxs-lookup"><span data-stu-id="d0667-117">The **Mining Models** tab lists the columns that the mining structure contains in the **Structure** column of the grid, and lists the columns that the mining model contains in the column that has the name of the model, in this case **Forecasting**.</span></span> <span data-ttu-id="d0667-118">单击列名称以进行修改。</span><span class="sxs-lookup"><span data-stu-id="d0667-118">Click the names of the columns to make modifications.</span></span> <span data-ttu-id="d0667-119">在**预测**挖掘模型中，"金额" 列用作输入列，还用于预测将来的销售额。</span><span class="sxs-lookup"><span data-stu-id="d0667-119">In the **Forecasting** mining model, the Amount column is used as an input column and is also used to forecast future sales.</span></span> <span data-ttu-id="d0667-120">因此，必须设置该列的属性，以便可同时将其用作输入列和可预测列。</span><span class="sxs-lookup"><span data-stu-id="d0667-120">Therefore, you must set the properties of the column so that it can be used as both an input column and a predictable column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0667-121">在 "**挖掘模型**" 选项卡中，您还可以基于同一结构创建新模型，并可以调整每个模型的算法和列属性。</span><span class="sxs-lookup"><span data-stu-id="d0667-121">In the **Mining Models** tab, you can also create new models based on the same structure, and you can adjust the algorithm and column properties for each model.</span></span> <span data-ttu-id="d0667-122">但是，必须先处理模型，然后这些更改才能生效。</span><span class="sxs-lookup"><span data-stu-id="d0667-122">However, you must process the model before these changes take effect.</span></span>  
  
#### <a name="to-define-how-the-amount-column-will-be-used"></a><span data-ttu-id="d0667-123">定义“金额”列的使用方式</span><span class="sxs-lookup"><span data-stu-id="d0667-123">To define how the Amount column will be used</span></span>  
  
1.  <span data-ttu-id="d0667-124">在 "**挖掘模型**" 选项卡上的网格的 "**预测**" 列中，单击 "金额" 行中的单元格。</span><span class="sxs-lookup"><span data-stu-id="d0667-124">In the **Forecasting** column of the grid on the **Mining Models** tab, click the cell in the Amount row.</span></span>  
  
2.  <span data-ttu-id="d0667-125">从列表中选择 "**预测**"。</span><span class="sxs-lookup"><span data-stu-id="d0667-125">Select **Predict** from the list.</span></span>  
  
     <span data-ttu-id="d0667-126">现在，Amount 列既是输入列，又是可预测列。</span><span class="sxs-lookup"><span data-stu-id="d0667-126">The Amount column is now both an input column and a predictable column.</span></span>  
  
 <span data-ttu-id="d0667-127">您还可以通过选择列并打开 "**属性**" 窗口来更改各列的属性。</span><span class="sxs-lookup"><span data-stu-id="d0667-127">You can also change the properties of individual columns by selecting the column and opening the **Properties** window.</span></span> <span data-ttu-id="d0667-128">若要打开 "**属性**" 窗口，请右键单击列名称，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="d0667-128">To open the **Properties** window, right-click the column name, and then select **Properties**.</span></span> <span data-ttu-id="d0667-129">如果在单个模型的列中更改属性，则只能更改该模型的属性。</span><span class="sxs-lookup"><span data-stu-id="d0667-129">If you change a property within the column for an individual model, you can change the properties only for that model.</span></span> <span data-ttu-id="d0667-130">但是，在**结构**列中更改属性时，更改会影响与该结构关联的每个模型。</span><span class="sxs-lookup"><span data-stu-id="d0667-130">However, when you change a property within the **Structure** column, the change affects every model that is associated with the structure.</span></span> <span data-ttu-id="d0667-131">无论何时对模型或结构进行更改，都必须对它们进行重新处理才能查看效果。</span><span class="sxs-lookup"><span data-stu-id="d0667-131">Whenever you make changes to the model or structure, you must reprocess to see the effects.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d0667-132">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="d0667-132">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d0667-133">自定义和处理预测模型 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="d0667-133">Customizing and Processing the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="d0667-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0667-134">See Also</span></span>  
 <span data-ttu-id="d0667-135">[挖掘结构 &#40;Analysis Services 数据挖掘&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="d0667-135">[Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="d0667-136">挖掘模型（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="d0667-136">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
