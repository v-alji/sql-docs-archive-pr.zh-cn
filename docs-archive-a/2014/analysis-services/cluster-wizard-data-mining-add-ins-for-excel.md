---
title: 群集向导 (Excel 数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clustering [data mining]
ms.assetid: 85b25625-a7ab-4960-9f9c-df22e8ecae37
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90500ae627bcafd1ca5ce17114dac9df9939691d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579880"
---
# <a name="cluster-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="6d6c0-102">聚类分析向导（Excel 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="6d6c0-102">Cluster Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="6d6c0-103">![“数据挖掘”功能区中的聚类分析向导](media/dmc-cluster.gif "“数据挖掘”功能区中的聚类分析向导")</span><span class="sxs-lookup"><span data-stu-id="6d6c0-103">![Cluster wizard in Data Mining ribbon](media/dmc-cluster.gif "Cluster wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="6d6c0-104">聚类分析向导可帮助您建立模型，检测共享类似特征的行并对这些行进行分组，以最大限度地增加这些组之间的距离。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-104">The Cluster wizard helps you build a model that detects rows that share similar characteristics and groups them to maximize the distance between groups.</span></span> <span data-ttu-id="6d6c0-105">此向导对于查找各种类型数据中的模式非常有用。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-105">This wizard is useful for finding patterns in all kinds of data.</span></span>  
  
 <span data-ttu-id="6d6c0-106">聚类分析向导使用 Microsoft 聚类分析算法，可以进行广泛的自定义。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-106">The Cluster wizard uses the Microsoft Clustering algorithm and can be extensively customized.</span></span> <span data-ttu-id="6d6c0-107">该向导可用于现有的数据，包括 Excel 表、Excel 区域或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 查询。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-107">It works on existing data from an Excel table, an Excel range, or an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] query.</span></span> <span data-ttu-id="6d6c0-108">与 Excel 表分析工具中提供的 "[检测类别](detect-categories-table-analysis-tools-for-excel.md)" 工具相似，它也提供了类似功能。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-108">Similar functionality is provided by the [Detect Categories](detect-categories-table-analysis-tools-for-excel.md) tool, provided in the Table Analysis Tools for Excel.</span></span> <span data-ttu-id="6d6c0-109">不过，检测类别工具无法自定义，必须使用 Excel 表中的数据。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-109">However, the Detect Categories tool cannot be customized and must use data in Excel tables.</span></span>  
  
## <a name="using-the-cluster-wizard"></a><span data-ttu-id="6d6c0-110">使用聚类分析向导</span><span class="sxs-lookup"><span data-stu-id="6d6c0-110">Using the Cluster Wizard</span></span>  
  
1.  <span data-ttu-id="6d6c0-111">在 "数据挖掘" 功能区中，单击 "**群集**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-111">In the Data Mining ribbon, click **Cluster**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="6d6c0-112">在 "**选择源数据**" 页中，选择 Excel 表或区域。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-112">In the **Select Source Data** page, select an Excel table or range.</span></span> <span data-ttu-id="6d6c0-113">也可以指定外部数据源。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-113">Or specify and external data source.</span></span>  
  
     <span data-ttu-id="6d6c0-114">如果使用外部数据源，您可以创建自定义视图或粘贴上自定义查询文本并将数据集另存为 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据源。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-114">If you use an external data source, you can create custom views or paste in custom query text, and save the data set as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span>  
  
3.  <span data-ttu-id="6d6c0-115">在 "**聚类分析**" 页上，您可以自定义模型的生成方式。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-115">On the **Clustering** page, you can customize the way the model is built.</span></span>  
  
    -   <span data-ttu-id="6d6c0-116">对于**段数**，可以让向导创建固定数量的类别，或者让它自动检测最佳的分组数。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-116">For **Number of segments**, you can tell the wizard to create a fixed number of categories, or let it automatically detect the optimum number of groupings.</span></span>  
  
    -   <span data-ttu-id="6d6c0-117">查看 "**输入列**" 列表中的列的列表，然后取消选择在创建模式中不起作用的任何列。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-117">Review the list of columns in the **Input columns** list, and deselect any columns that are not useful in creating patterns.</span></span> <span data-ttu-id="6d6c0-118">应排除的列包括 ID 编号、客户名称等。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-118">Columns you should exclude include ID numbers, customer names, and so on.</span></span>  
  
4.  <span data-ttu-id="6d6c0-119">（可选）单击 "**参数**" 更改算法参数，并自定义聚类分析模型的行为。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-119">Optionally, click **Parameters** to change the algorithm parameters and customize the behavior of the clustering model.</span></span>  
  
5.  <span data-ttu-id="6d6c0-120">在 "将**数据拆分为定型集和测试集**" 页中，指定要保留多少数据用于测试。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-120">In the **Split data into training and testing sets** page, specify how much data to hold out for testing.</span></span> <span data-ttu-id="6d6c0-121">剩余的数据始终用于定型模型。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-121">The remainder is always used for training the model.</span></span>  
  
     <span data-ttu-id="6d6c0-122">默认设置为 30% 的测试数据和 70% 的定型数据。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-122">The default setting is 30% testing data and 70% training data.</span></span>  
  
6.  <span data-ttu-id="6d6c0-123">在 "**完成**" 页上，为数据集和模型提供描述性名称，并设置以下选项来控制使用已完成模型的方式：</span><span class="sxs-lookup"><span data-stu-id="6d6c0-123">On the **Finish** page, provide a descriptive name for your data set and model, and set the following options that control how you work with the finished model:</span></span>  
  
    -   <span data-ttu-id="6d6c0-124">**浏览模型**。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-124">**Browse model**.</span></span> <span data-ttu-id="6d6c0-125">如果选择此选项，向导处理完模型后就会立即打开 "**浏览**" 窗口，以帮助您浏览结果。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-125">When this option is selected, as soon as the wizard finishes processing the model, it opens a **Browse** window to help you explore the results.</span></span> <span data-ttu-id="6d6c0-126">查看器的内容取决于您建立的模型的类型。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-126">The contents of the viewer depend on the type of model you built.</span></span> <span data-ttu-id="6d6c0-127">有关详细信息，请参阅[浏览聚类分析模型](browsing-a-clustering-model.md)。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-127">For more information, see [Browsing a Clustering Model](browsing-a-clustering-model.md).</span></span>  
  
    -   <span data-ttu-id="6d6c0-128">**启用钻取**。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-128">**Enable drillthrough**.</span></span> <span data-ttu-id="6d6c0-129">选择此选项可以查看已完成模型中的基础数据。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-129">Select this option to view the underlying data from the finished model.</span></span> <span data-ttu-id="6d6c0-130">此选项仅在建立决策树模型时可用。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-130">This option is only available if you build a Decision Tree model.</span></span>  
  
    -   <span data-ttu-id="6d6c0-131">**使用临时模型**。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-131">**Use temporary model**.</span></span> <span data-ttu-id="6d6c0-132">如果您选择此选项，模型将不会被保存到服务器。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-132">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="6d6c0-133">在您关闭 Excel 时，临时模型将被删除。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-133">Temporary models are deleted when you close Excel.</span></span>  
  
## <a name="more-about-clustering-models"></a><span data-ttu-id="6d6c0-134">有关聚类分析模型的详细信息</span><span class="sxs-lookup"><span data-stu-id="6d6c0-134">More about Clustering Models</span></span>  
 <span data-ttu-id="6d6c0-135">通过单击 "**高级**" 并使用 "**算法参数**" 对话框，可以更改此向导使用的聚类分析算法。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-135">You can change the clustering algorithm used by this wizard by clicking **Advanced** and using the **Algorithm Parameters** dialog box.</span></span>  
  
 <span data-ttu-id="6d6c0-136">Microsoft 聚类分析算法提供以下聚类分析方法：</span><span class="sxs-lookup"><span data-stu-id="6d6c0-136">The Microsoft Clustering algorithm provides these clustering methods:</span></span>  
  
-   <span data-ttu-id="6d6c0-137">K-means - 可缩放或不可缩放。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-137">K-means -  scalable or non-scaling.</span></span>  
  
-   <span data-ttu-id="6d6c0-138">期望最大化 (EM) - 可缩放或不可缩放。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-138">Expectation Maximization (EM) - scalable or non-scaling.</span></span>  
  
 <span data-ttu-id="6d6c0-139">您还可以使用 CLUSTER_SEED 参数来控制起始值，确保使用相同数据集的重复模型具有相同的结果。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-139">You can also use the CLUSTER_SEED parameter to control the starting value and ensure that repeated models using the same data set have the same results.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="6d6c0-140">要求</span><span class="sxs-lookup"><span data-stu-id="6d6c0-140">Requirements</span></span>  
 <span data-ttu-id="6d6c0-141">若要使用聚类分析向导，您必须连接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-141">To use the Cluster wizard, you must be connected to a [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="6d6c0-142">有关详细信息，请参阅[连接到源数据 &#40;Excel 数据挖掘客户端&#41;](connect-to-source-data-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="6d6c0-142">For more information, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d6c0-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6d6c0-143">See Also</span></span>  
 <span data-ttu-id="6d6c0-144">[创建数据挖掘模型](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="6d6c0-144">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="6d6c0-145">检测类别 &#40;Excel&#41;的表分析工具</span><span class="sxs-lookup"><span data-stu-id="6d6c0-145">Detect Categories &#40;Table Analysis Tools for Excel&#41;</span></span>](detect-categories-table-analysis-tools-for-excel.md)  
  
  
