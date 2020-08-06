---
title: 数据挖掘工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tools [Analysis Services]
- mining models [Analysis Services], tools
- data mining [Analysis Services], tools
- data mining [Analysis Services], development
ms.assetid: 003ada6a-0bcd-4f16-8c34-1a9ffc75cd2c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4be2f343f0fb7969f76b63ec1eb1677c1c9e589f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591661"
---
# <a name="data-mining-tools"></a><span data-ttu-id="17a05-102">数据挖掘工具</span><span class="sxs-lookup"><span data-stu-id="17a05-102">Data Mining Tools</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="17a05-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 提供了以下工具，可用于创建数据挖掘解决方案：</span><span class="sxs-lookup"><span data-stu-id="17a05-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides the following tools that you can use to create data mining solutions:</span></span>  
  
-   <span data-ttu-id="17a05-104">利用 **中的** 数据挖掘向导 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ，可以使用关系数据源或多维数据集中的多维数据来轻松创建挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="17a05-104">The **Data Mining Wizard** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] makes it easy to create mining structures and mining models, using either relational data sources or multidimensional data in cubes.</span></span>  
  
     <span data-ttu-id="17a05-105">在该向导中，您可以选择要使用的数据，然后应用特定的数据挖掘技术，如聚类分析、神经网络或时序建模。</span><span class="sxs-lookup"><span data-stu-id="17a05-105">In the wizard, you choose data to use, and then apply specific data mining techniques, such as clustering, neural networks, or time series modeling.</span></span>  
  
-   <span data-ttu-id="17a05-106">\*\*\*\* 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中都提供了模型查看器 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]，可用于在创建挖掘模型后对其进行浏览。</span><span class="sxs-lookup"><span data-stu-id="17a05-106">**Model viewers** are provided in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], for exploring your mining models after they are created.</span></span>  <span data-ttu-id="17a05-107">可以使用为每种算法定制的查看器来浏览模型，或使用模型内容查看器进行更深入的分析。</span><span class="sxs-lookup"><span data-stu-id="17a05-107">You can browse models using viewers tailored to each algorithm, or go deeper into analysis by using the model content viewer.</span></span>  
  
-   <span data-ttu-id="17a05-108">\*\*\*\* 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中都提供了预测查询生成器 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ，可帮助您创建预测查询。</span><span class="sxs-lookup"><span data-stu-id="17a05-108">The **Prediction Query Builder** is provided in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to help you create prediction queries.</span></span> <span data-ttu-id="17a05-109">还可以针对维持数据集或外部数据来测试模型的准确性，或使用交叉验证来评估数据集的质量。</span><span class="sxs-lookup"><span data-stu-id="17a05-109">You can also test the accuracy of models against a holdout data set or external data, or use cross-validation to assess the quality of your data set.</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="17a05-110">是一个接口，可用于管理已部署到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例的现有数据挖掘解决方案。</span><span class="sxs-lookup"><span data-stu-id="17a05-110">is the interface where you manage existing data mining solutions that have been deployed to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="17a05-111">可以重新处理结构和模型以更新其包含的数据。</span><span class="sxs-lookup"><span data-stu-id="17a05-111">You can reprocess structures and models to update the data in them.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="17a05-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]包含一些工具，可用于清除数据、自动执行任务（如创建预测和更新模型）以及创建文本挖掘解决方案。</span><span class="sxs-lookup"><span data-stu-id="17a05-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contains tools that you can use to clean data, to automate tasks such as creating predictions and updating models, and to create text mining solutions.</span></span>  
  
 <span data-ttu-id="17a05-113">下面详细地介绍了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的数据挖掘工具。</span><span class="sxs-lookup"><span data-stu-id="17a05-113">The following sections provide more information about the data mining tools in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="data-mining-wizard"></a><span data-ttu-id="17a05-114">中的</span><span class="sxs-lookup"><span data-stu-id="17a05-114">Data Mining Wizard</span></span>  
 <span data-ttu-id="17a05-115">可使用数据挖掘向导开始创建数据挖掘解决方案。</span><span class="sxs-lookup"><span data-stu-id="17a05-115">Use the Data Mining Wizard to get started creating data mining solutions.</span></span> <span data-ttu-id="17a05-116">该向导简单易用，可指导您完成创建数据挖掘结构和初始相关挖掘模型的过程，其中包括选择算法类型和数据源以及定义用于分析的事例数据等任务。</span><span class="sxs-lookup"><span data-stu-id="17a05-116">The wizard is quick and easy, and guides you through the process of creating a data mining structure and an initial related mining model, and includes the tasks of selecting an algorithm type and a data source, and defining the case data used for analysis.</span></span>  
  
 <span data-ttu-id="17a05-117">**有关详细信息：** [数据挖掘向导（Analysis Services - 数据挖掘）](data-mining-wizard-analysis-services-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="17a05-117">**For More Information:** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-analysis-services-data-mining.md)</span></span>  
  
## <a name="data-mining-designer"></a><span data-ttu-id="17a05-118">Data Mining Designer</span><span class="sxs-lookup"><span data-stu-id="17a05-118">Data Mining Designer</span></span>  
 <span data-ttu-id="17a05-119">在使用数据挖掘向导创建挖掘结构和挖掘模型后，您可以从 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中使用数据挖掘设计器来处理现有模型和结构。</span><span class="sxs-lookup"><span data-stu-id="17a05-119">After you have created a mining structure and mining model by using the Data Mining Wizard, you can use the Data Mining Designer from either [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to work with existing models and structures.</span></span>  
  
 <span data-ttu-id="17a05-120">该设计器包含用于执行以下任务的工具：</span><span class="sxs-lookup"><span data-stu-id="17a05-120">The designer includes tools for these tasks:</span></span>  
  
-   <span data-ttu-id="17a05-121">修改挖掘结构的属性，添加列并创建列别名，更改值的装箱方法或预期分布。</span><span class="sxs-lookup"><span data-stu-id="17a05-121">Modify the properties of mining structures, add columns and create column aliases, change the binning method or expected distribution of values.</span></span>  
  
-   <span data-ttu-id="17a05-122">向现有结构中添加新模型；复制模型，更改模型属性或元数据，或定义挖掘模型的筛选器。</span><span class="sxs-lookup"><span data-stu-id="17a05-122">Add new models to an existing structure; copy models, change model properties or metadata, or define filters on a mining model.</span></span>  
  
-   <span data-ttu-id="17a05-123">浏览模型中的模式和规则；浏览关联或决策树。</span><span class="sxs-lookup"><span data-stu-id="17a05-123">Browse the patterns and rules within the model; explore associations or decision trees.</span></span> <span data-ttu-id="17a05-124">获取有关为</span><span class="sxs-lookup"><span data-stu-id="17a05-124">Get detailed statistics about</span></span>  
  
     <span data-ttu-id="17a05-125">每个不同的模型时间提供的自定义查看器的详细统计信息，以帮助您分析数据和浏览数据挖掘所显示的模式。</span><span class="sxs-lookup"><span data-stu-id="17a05-125">Custom viewers are provided for each different time of model, to help you analyze your data and explore the patterns revealed by data mining.</span></span>  
  
-   <span data-ttu-id="17a05-126">通过创建提升图或分析模型的利润曲线来验证模型。</span><span class="sxs-lookup"><span data-stu-id="17a05-126">Validate models by creating lift charts, or analyzing the profit curve for models.</span></span> <span data-ttu-id="17a05-127">使用分类矩阵比较模型，或使用交叉验证来验证数据集及其模型。</span><span class="sxs-lookup"><span data-stu-id="17a05-127">Compare models using classification matrices, or validate a data set and its models by using cross-validation.</span></span>  
  
-   <span data-ttu-id="17a05-128">创建针对现有挖掘模型的预测和内容查询。</span><span class="sxs-lookup"><span data-stu-id="17a05-128">Create predictions and content queries against existing mining models.</span></span> <span data-ttu-id="17a05-129">生成一次性查询，或设置用于为整个外部数据表生成预测的查询。</span><span class="sxs-lookup"><span data-stu-id="17a05-129">Build one-off queries, or set up queries to generate predictions for entire tables of external data.</span></span>  
  
 <span data-ttu-id="17a05-130">**有关详细信息：** [数据挖掘设计器](data-mining-designer.md)</span><span class="sxs-lookup"><span data-stu-id="17a05-130">**For More Information:** [Data Mining Designer](data-mining-designer.md)</span></span>  
  
## <a name="sql-server-management-studio"></a><span data-ttu-id="17a05-131">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="17a05-131">SQL Server Management Studio</span></span>  
 <span data-ttu-id="17a05-132">在创建挖掘模型并将其部署到服务器之后，您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 来管理承载数据挖掘对象的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="17a05-132">After you create and deploy mining models to a server, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that hosts the data mining objects.</span></span> <span data-ttu-id="17a05-133">也可以继续执行使用模型的任务，如浏览模型、处理新数据和创建预测。</span><span class="sxs-lookup"><span data-stu-id="17a05-133">You can also continue to perform tasks that use the model, such as exploring the models, processing new data, and creating predictions.</span></span>  
  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="17a05-134">还包含查询编辑器，可用于设计和执行数据挖掘扩展插件 (DMX) 查询或用于通过使用 XMLA 来处理数据挖掘对象。</span><span class="sxs-lookup"><span data-stu-id="17a05-134">also contains query editors that you can use to design and execute Data Mining Extensions (DMX) queries, or ot work with data mining objects by using XMLA.</span></span>  
  
## <a name="integration-services-data-mining-tasks-and-transformations"></a><span data-ttu-id="17a05-135">Integration Services 数据挖掘任务和转换</span><span class="sxs-lookup"><span data-stu-id="17a05-135">Integration Services Data Mining Tasks and Transformations</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="17a05-136">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]提供了多个支持数据挖掘的组件。</span><span class="sxs-lookup"><span data-stu-id="17a05-136">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides many components that support data mining.</span></span>  
  
 <span data-ttu-id="17a05-137">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的一些工具旨在帮助自动执行常见数据挖掘任务，包括预测、建模和处理。</span><span class="sxs-lookup"><span data-stu-id="17a05-137">Some tools in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] are designed to help automate common data mining tasks, including prediction, model building, and processing.</span></span> <span data-ttu-id="17a05-138">例如：</span><span class="sxs-lookup"><span data-stu-id="17a05-138">For example:</span></span>  
  
-   <span data-ttu-id="17a05-139">创建一个 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包，每当用新客户更新数据集时，该包会自动更新模型。</span><span class="sxs-lookup"><span data-stu-id="17a05-139">Create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that automatically updates the model every time the dataset is updated with new customers</span></span>  
  
-   <span data-ttu-id="17a05-140">对事例记录进行自定义分段或自定义采样。</span><span class="sxs-lookup"><span data-stu-id="17a05-140">Perform custom segmentation or custom sampling of case records.</span></span>  
  
-   <span data-ttu-id="17a05-141">自动生成通过参数传递的模型。</span><span class="sxs-lookup"><span data-stu-id="17a05-141">Automatically generate models passed on parameters.</span></span>  
  
 <span data-ttu-id="17a05-142">但是，您还可以在包工作流中将数据挖掘用作其他进程的输入。</span><span class="sxs-lookup"><span data-stu-id="17a05-142">However, you can also use data mining in a package workflow, as an input to other processes.</span></span> <span data-ttu-id="17a05-143">例如：</span><span class="sxs-lookup"><span data-stu-id="17a05-143">For example:</span></span>  
  
-   <span data-ttu-id="17a05-144">使用模型所生成的概率值来加权文本挖掘或其他分类任务的分数。</span><span class="sxs-lookup"><span data-stu-id="17a05-144">Use probability values generated by the model to weight scores for text mining or other classification tasks.</span></span>  
  
-   <span data-ttu-id="17a05-145">基于之前的数据自动生成预测，并使用这些值来评估新数据的有效性。</span><span class="sxs-lookup"><span data-stu-id="17a05-145">Automatically generate predictions based on prior data and use those values to assess the validity of new data.</span></span>  
  
-   <span data-ttu-id="17a05-146">使用逻辑回归按风险划分传入客户。</span><span class="sxs-lookup"><span data-stu-id="17a05-146">Using logistic regression to segment incoming customers by risk.</span></span>  
  
 <span data-ttu-id="17a05-147">**有关详细信息：** [数据挖掘解决方案的相关项目](data-mining-solutions.md)</span><span class="sxs-lookup"><span data-stu-id="17a05-147">**For More Information:** [Related Projects for Data Mining Solutions](data-mining-solutions.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a05-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17a05-148">See Also</span></span>  
 <span data-ttu-id="17a05-149">[&#40;DMX&#41; 的数据挖掘扩展插件](/sql/dmx/data-mining-extensions-dmx-reference) </span><span class="sxs-lookup"><span data-stu-id="17a05-149">[Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference) </span></span>  
 <span data-ttu-id="17a05-150">[挖掘模型任务和操作指南](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="17a05-150">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="17a05-151">[挖掘模型查看器任务和操作指南](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="17a05-151">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="17a05-152">数据挖掘解决方案</span><span class="sxs-lookup"><span data-stu-id="17a05-152">Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
  
