---
title: 预测向导 (Excel 数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- forecasting [data mining]
- time series [data mining]
ms.assetid: c5b33f75-42d4-4598-89e7-94815c142ce6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c3fae97bf1c36154d8ae378840014f2fb997afd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579166"
---
# <a name="forecast-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="fe0c0-102">预测向导（Excel 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="fe0c0-102">Forecast Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="fe0c0-103">![“数据挖掘”功能区中的关联向导](media/dmc-forecast.gif "“数据挖掘”功能区中的关联向导")</span><span class="sxs-lookup"><span data-stu-id="fe0c0-103">![Associate wizard in Data Mining ribbon](media/dmc-forecast.gif "Associate wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="fe0c0-104">使用预测向导可以预测时序中的值。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-104">The Forecast wizard helps you predict values in a time series.</span></span> <span data-ttu-id="fe0c0-105">预测向导使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 时序算法，该算法是一个用于预测连续列（例如产品销售）的回归算法。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-105">The Forecast wizard uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm, which is a regression algorithm for use in predicting continuous columns, such as product sales.</span></span>  
  
 <span data-ttu-id="fe0c0-106">每个预测模型都必须包含一个事例序列，即区分序列中不同点的列。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-106">Each forecasting model must contain a case series, which is the column that distinguishes between points in a sequence.</span></span> <span data-ttu-id="fe0c0-107">举例来说，如果您使用历史数据来预测几个月内的销售情况，您会用到一个列，其中包含一系列日期来作为事例序列。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-107">For example, if you are using historical data to forecast sales over a period of several months, you would use a column containing a series of dates as the case series.</span></span>  
  
 <span data-ttu-id="fe0c0-108">您可以从预测模型中创建预测信息，而无需提供新的输入数据。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-108">You can create predictions from a forecasting model without providing new input data.</span></span>  
  
 <span data-ttu-id="fe0c0-109">"**分析**" 功能区中的 "[预测 &#40;表分析工具"&#41;](forecast-table-analysis-tools-for-excel.md)工具可用于创建预测模型，但它的可自定义性更少，并且只能使用 Excel 表中的数据。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-109">The [Forecast &#40;Table Analysis Tools for Excel&#41;](forecast-table-analysis-tools-for-excel.md) tool, in the **Analyze** ribbon, also lets you create forecasting models, but it is less customizable and can only use data in Excel tables.</span></span>  
  
## <a name="using-the-forecast-wizard"></a><span data-ttu-id="fe0c0-110">使用预测向导</span><span class="sxs-lookup"><span data-stu-id="fe0c0-110">Using the Forecast Wizard</span></span>  
  
1.  <span data-ttu-id="fe0c0-111">在 "**数据挖掘**" 功能区中，单击 "**预测**"。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-111">In the **Data Mining** ribbon, click **Forecast**.</span></span>  
  
2.  <span data-ttu-id="fe0c0-112">在 "**选择源数据**" 中，选择要用作输入的 Excel 表、区域或外部数据源。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-112">In the **Select Source Data**, choose the Excel table, range, or external data source to use as inputs.</span></span>  
  
     <span data-ttu-id="fe0c0-113">如果使用外部数据源，您可以定义自定义视图或查询并将其另存为 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据源。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-113">If you use an external data source, you can define custom view or queries and save it as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span>  
  
3.  <span data-ttu-id="fe0c0-114">在 "**预测**" 页上，对于 "**时间戳**"，选择包含唯一数值的列 (这包括可用作事例序列) 日期和时间值。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-114">On the **Forecasting** page, for **Time stamp**, select a column that contains unique numeric value (this includes date and time values) that can be used as the case series.</span></span> <span data-ttu-id="fe0c0-115">必须按此列以升序顺序对数据源进行排序。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-115">The data source must be sorted in ascending order by this column.</span></span>  
  
     <span data-ttu-id="fe0c0-116">如果数据没有此类列，可以使用选项 \<no time stamp> 。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-116">If your data does not have such a column, you can use the option \<no time stamp>.</span></span> <span data-ttu-id="fe0c0-117">此向导将为输入数据添加一个唯一的排序列；因此，您必须确保首先按照您希望的方式对数据进行排序，然后再运行此向导和选择此选项。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-117">The wizard will add a unique order column for the input data; therefore, you must make sure that the data is sorted the way you want before running the wizard and choosing this option.</span></span>  
  
4.  <span data-ttu-id="fe0c0-118">或者，您可以单击 "**参数**" 并自定义挖掘模型的行为。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-118">Optionally, you can click **Parameters** and customize the behavior of the mining model.</span></span>  
  
     <span data-ttu-id="fe0c0-119">预测模型支持以下几种不同的算法：</span><span class="sxs-lookup"><span data-stu-id="fe0c0-119">Forecasting models support several different algorithms:</span></span>  
  
    -   <span data-ttu-id="fe0c0-120">ARIMA</span><span class="sxs-lookup"><span data-stu-id="fe0c0-120">ARIMA</span></span>  
  
    -   <span data-ttu-id="fe0c0-121">ARTXP（一种回归模型）</span><span class="sxs-lookup"><span data-stu-id="fe0c0-121">ARTXP (a type of regression model)</span></span>  
  
    -   <span data-ttu-id="fe0c0-122">组合的 ARTXP 和 ARIMA</span><span class="sxs-lookup"><span data-stu-id="fe0c0-122">ARTXP and ARIMA combined</span></span>  
  
     <span data-ttu-id="fe0c0-123">有关差异的信息，请参阅[Microsoft 时序算法技术参考](data-mining/microsoft-time-series-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-123">For information about the differences, see [Microsoft Time Series Algorithm Technical Reference](data-mining/microsoft-time-series-algorithm-technical-reference.md).</span></span>  
  
     <span data-ttu-id="fe0c0-124">您还可以为模型添加周期提示、指定平滑选项以及自定义回归选项。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-124">You can also add periodicity hints, specify smoothing options, and customize regression options for the model.</span></span>  
  
5.  <span data-ttu-id="fe0c0-125">在 "**完成**" 页上，为数据集和模型提供描述性名称，并设置以下选项来控制使用已完成模型的方式：</span><span class="sxs-lookup"><span data-stu-id="fe0c0-125">On the **Finish** page, provide a descriptive name for your data set and model, and set the following options that control how you work with the finished model:</span></span>  
  
    -   <span data-ttu-id="fe0c0-126">**浏览模型**。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-126">**Browse model**.</span></span> <span data-ttu-id="fe0c0-127">如果选择此选项，向导处理完模型后就会立即打开 "**浏览**" 窗口，以帮助您浏览结果。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-127">When this option is selected, as soon as the wizard finishes processing the model, it opens a **Browse** window to help you explore the results.</span></span> <span data-ttu-id="fe0c0-128">查看器的内容取决于您建立的模型的类型。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-128">The contents of the viewer depend on the type of model you built.</span></span> <span data-ttu-id="fe0c0-129">有关详细信息，请参阅[浏览预测模型](browsing-a-forecasting-model.md)。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-129">For more information, see [Browsing a Forecasting Model](browsing-a-forecasting-model.md).</span></span>  
  
    -   <span data-ttu-id="fe0c0-130">**启用钻取**。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-130">**Enable drillthrough**.</span></span> <span data-ttu-id="fe0c0-131">选择此选项可以查看已完成模型中的基础数据。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-131">Select this option to view the underlying data from the finished model.</span></span> <span data-ttu-id="fe0c0-132">此选项仅在建立决策树模型时可用。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-132">This option is only available if you build a Decision Tree model.</span></span>  
  
    -   <span data-ttu-id="fe0c0-133">**使用临时模型**。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-133">**Use temporary model**.</span></span> <span data-ttu-id="fe0c0-134">如果您选择此选项，模型将不会被保存到服务器。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-134">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="fe0c0-135">在您关闭 Excel 时，临时模型将被删除。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-135">Temporary models are deleted when you close Excel.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="fe0c0-136">要求</span><span class="sxs-lookup"><span data-stu-id="fe0c0-136">Requirements</span></span>  
 <span data-ttu-id="fe0c0-137">您的数据中应至少包括一个可用作时序的列。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-137">Your data should include at least one column that can be used as the time series.</span></span> <span data-ttu-id="fe0c0-138">此列中的值应是唯一的并且是连续的，也就是说，不应有空白。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-138">The values in this column should be unique and continuous - that is, there should be no gaps.</span></span> <span data-ttu-id="fe0c0-139">在运行此向导之前，请按时序列以升序顺序对数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-139">Before running the wizard, sort the data by the time series column in ascending order.</span></span>  
  
 <span data-ttu-id="fe0c0-140">如果您的数据中不包括时间或日期列，可以指定任意数值序列或由向导创建一个数值序列。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-140">If your data does not include a time or date column, you can assign an arbitrary numeric series, or let the wizard create one.</span></span> <span data-ttu-id="fe0c0-141">如果您选择由向导创建序列排序列，请确保在启动向导之前按您所希望的方式对其他列进行了排序。</span><span class="sxs-lookup"><span data-stu-id="fe0c0-141">F you let the wizard create the series order column, make sure the other columns are sorted in the worder you want them before starting the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0c0-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe0c0-142">See Also</span></span>  
 <span data-ttu-id="fe0c0-143">[创建数据挖掘模型](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="fe0c0-143">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 <span data-ttu-id="fe0c0-144">[用于 Excel&#41;的预测 &#40;表分析工具](forecast-table-analysis-tools-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="fe0c0-144">[Forecast &#40;Table Analysis Tools for Excel&#41;](forecast-table-analysis-tools-for-excel.md) </span></span>  
 [<span data-ttu-id="fe0c0-145">浏览预测模型</span><span class="sxs-lookup"><span data-stu-id="fe0c0-145">Browsing a Forecasting Model</span></span>](browsing-a-forecasting-model.md)  
  
  
