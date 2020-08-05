---
title: 选择准确性图表类型和设置图表选项 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services]
- mining models [Analysis Services], validating
- classification accuracy [data mining]
- accuracy testing [data mining]
ms.assetid: bd24dd4a-624f-478a-9c94-b1361e857680
author: minewiskan
ms.author: owend
ms.openlocfilehash: 33c2b5e8a1e228a86328ef6df1b636742d3614ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581046"
---
# <a name="choose-an-accuracy-chart-type-and-set-chart-options"></a><span data-ttu-id="26213-102">选择准确性图表类型和设置图表选项</span><span class="sxs-lookup"><span data-stu-id="26213-102">Choose an Accuracy Chart Type and Set Chart Options</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="26213-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]提供多种方法来确定挖掘模型的有效性。</span><span class="sxs-lookup"><span data-stu-id="26213-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides multiple methods for determining the validity of your mining models.</span></span> <span data-ttu-id="26213-104">您可以为每个模型或结构创建的准确性图表的类型取决于以下因素：</span><span class="sxs-lookup"><span data-stu-id="26213-104">The type of accuracy chart that you can create for each model or structure depends on these factors:</span></span>  
  
-   <span data-ttu-id="26213-105">用于创建模型的算法的类型</span><span class="sxs-lookup"><span data-stu-id="26213-105">The type of algorithm that was used to create the model</span></span>  
  
-   <span data-ttu-id="26213-106">可预测属性的数据类型</span><span class="sxs-lookup"><span data-stu-id="26213-106">The data type of the predictable attribute</span></span>  
  
-   <span data-ttu-id="26213-107">要进行度量的可预测属性的数量</span><span class="sxs-lookup"><span data-stu-id="26213-107">The number of predictable attributes to measure</span></span>  
  
 <span data-ttu-id="26213-108">本主题概述了不同的准确性图表。</span><span class="sxs-lookup"><span data-stu-id="26213-108">This topic provides an overview of the different accuracy charts.</span></span>  
  
 <span data-ttu-id="26213-109">**注意** 图表及其定义都不会保存。</span><span class="sxs-lookup"><span data-stu-id="26213-109">**Note** Charts and their definitions are not saved.</span></span> <span data-ttu-id="26213-110">如果您关闭包含图表的窗口，则必须重新创建该图表。</span><span class="sxs-lookup"><span data-stu-id="26213-110">If you close the window that contains a chart, you must create the chart again.</span></span>  
  
## <a name="accuracy-chart-types"></a><span data-ttu-id="26213-111">准确性图表类型</span><span class="sxs-lookup"><span data-stu-id="26213-111">Accuracy Chart Types</span></span>  
 <span data-ttu-id="26213-112">根据选择的图表类型，您可以进一步配置选项、浏览图表，或者将图表复制到剪贴板，以及在 Excel 中处理数据。</span><span class="sxs-lookup"><span data-stu-id="26213-112">Depending on the chart type that you choose, you have the ability to further configure options, to browse the chart, or copy the chart to the Clipboard and work with the data in Excel.</span></span>  
  
#### <a name="lift-chart"></a><span data-ttu-id="26213-113">提升图</span><span class="sxs-lookup"><span data-stu-id="26213-113">Lift chart</span></span>  
 <span data-ttu-id="26213-114">配置模型和测试数据的选项后，单击 **“提升图”** 选项卡可查看结果。</span><span class="sxs-lookup"><span data-stu-id="26213-114">After you have configured the options for the models and the testing data, click the **Lift Chart** tab to view the results.</span></span> <span data-ttu-id="26213-115">也可以将图表复制到剪贴板，或者在挖掘图例中查看各条趋势线或数据点的详细信息。</span><span class="sxs-lookup"><span data-stu-id="26213-115">You can also copy the chart to the Clipboard, or view details of individual trend lines or data points in the Mining Legend.</span></span>  
  
#### <a name="profit-chart"></a><span data-ttu-id="26213-116">利润图</span><span class="sxs-lookup"><span data-stu-id="26213-116">Profit Chart</span></span>  
 <span data-ttu-id="26213-117">配置模型和测试数据的选项后，单击 **“提升图”** 选项卡，从 **“图表类型”** 列表中选择 **“利润图”** 可设置利润图选项，然后单击 **“确定”** 可查看结果。</span><span class="sxs-lookup"><span data-stu-id="26213-117">After you have configured the options for the models and the testing data, click the **Lift Chart** tab, select **Profit Chart** from the **Chart Type** list to set profit chart options, and then click **OK** to view the results.</span></span>  
  
 <span data-ttu-id="26213-118">您可以根据需要多次使用 **“利润图设置”** 对话框来尝试不同的成本选项以及重新显示图表。</span><span class="sxs-lookup"><span data-stu-id="26213-118">You can use the **Profit Chart Settings** dialog box as many times as you want to try different cost options and redisplay the chart.</span></span> <span data-ttu-id="26213-119">对于每个模型，挖掘图例会包含有关估计利润的详细信息。</span><span class="sxs-lookup"><span data-stu-id="26213-119">The Mining Legend contains detailed information about the estimated profit for each model.</span></span> <span data-ttu-id="26213-120">也可以将挖掘图例的图表和内容复制到剪贴板，然后在 Excel 中进行处理。</span><span class="sxs-lookup"><span data-stu-id="26213-120">You can also copy the chart and the contents of the Mining Legend to the Clipboard to work with it in Excel.</span></span>  
  
#### <a name="scatter-plot"></a><span data-ttu-id="26213-121">散点图</span><span class="sxs-lookup"><span data-stu-id="26213-121">Scatter Plot</span></span>  
 <span data-ttu-id="26213-122">如果已选择适当类型的模型，则单击 **“提升图”** 选项卡时，图表类型会自动设置为 **“散点图”** 并显示一个散点图。</span><span class="sxs-lookup"><span data-stu-id="26213-122">If you have selected the appropriate type of model, when you click the **Lift Chart** tab, the chart type is automatically set to **Scatter Plot** and a scatter plot is displayed.</span></span> <span data-ttu-id="26213-123">不能进一步进行配置。</span><span class="sxs-lookup"><span data-stu-id="26213-123">No further configuration is possible.</span></span> <span data-ttu-id="26213-124">也可以将图表复制到剪贴板，然后将该图表作为图形粘贴到 Excel 或其他应用程序。</span><span class="sxs-lookup"><span data-stu-id="26213-124">You can also copy the chart to the Clipboard and paste the chart as a graphic into Excel or another application.</span></span>  
  
#### <a name="classification-matrix"></a><span data-ttu-id="26213-125">分类矩阵</span><span class="sxs-lookup"><span data-stu-id="26213-125">Classification Matrix</span></span>  
 <span data-ttu-id="26213-126">对于分类矩阵，使用 **“输入选择”** 选项卡选择模型和测试数据，然后单击 **“分类矩阵”** 选项卡可查看结果。</span><span class="sxs-lookup"><span data-stu-id="26213-126">For a classification matrix, use the **Input Selection** tab to choose the models and the testing data, and then click the **Classification Matrix** tab to view the results.</span></span>  
  
 <span data-ttu-id="26213-127">分类矩阵的内容对于所有模型类型都是相同的，并且无法进行配置。</span><span class="sxs-lookup"><span data-stu-id="26213-127">The contents of a classification matrix are the same for all model types, and cannot be configured.</span></span> <span data-ttu-id="26213-128">可以将图表中的数据复制到剪贴板，然后在 Excel 中进行处理。</span><span class="sxs-lookup"><span data-stu-id="26213-128">You can copy the data in the chart to the Clipboard and then work with it in Excel.</span></span>  
  
#### <a name="cross-validation-report"></a><span data-ttu-id="26213-129">交叉验证报表</span><span class="sxs-lookup"><span data-stu-id="26213-129">Cross-Validation Report</span></span>  
 <span data-ttu-id="26213-130">对于交叉验证报表，在解决方案资源管理器中选择挖掘结构或挖掘模型后，单击“交叉验证”选项卡，配置所有相关选项，然后单击“获取结果”生成报表\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="26213-130">For a cross-validation report, after you have selected a mining structure or mining model in Solution Explorer, click the **Cross Validation** tab, configure all relevant options, and then click **Get Results** to generate the report.</span></span> <span data-ttu-id="26213-131">不能进一步进行配置。</span><span class="sxs-lookup"><span data-stu-id="26213-131">No further configuration is possible.</span></span>  
  
 <span data-ttu-id="26213-132">对于所有模型类型，交叉验证报表的格式均相同，并且无法进行配置。</span><span class="sxs-lookup"><span data-stu-id="26213-132">The format of the cross-validation report is the same for all model types, and cannot be configured.</span></span> <span data-ttu-id="26213-133">但报表的内容会有所不同，具体取决于要分析的模型的类型和可预测属性的数据类型。</span><span class="sxs-lookup"><span data-stu-id="26213-133">However, the content of the report differs depending on the type of model that you are analyzing, and the data type of the predictable attribute.</span></span> <span data-ttu-id="26213-134">也可以将报表的结果复制到剪贴板，然后在 Excel 中处理该数据。</span><span class="sxs-lookup"><span data-stu-id="26213-134">You can also copy the results of the report to the Clipboard and work with the data in Excel.</span></span>  
  
  
