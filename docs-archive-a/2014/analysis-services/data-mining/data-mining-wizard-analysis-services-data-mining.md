---
title: 数据挖掘向导 (Analysis Services 数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], data mining
- OLAP [Analysis Services], mining models
- Data Mining Wizard
- relational mining models [Analysis Services]
ms.assetid: d5fea90f-5f38-4639-8851-7707f6606a12
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30c1800e24a1d655dc87aff10dcfb214bcd69bf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591660"
---
# <a name="data-mining-wizard-analysis-services---data-mining"></a><span data-ttu-id="a783b-102">数据挖掘向导（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a783b-102">Data Mining Wizard (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="a783b-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 每次向数据挖掘项目中添加新的挖掘结构时，都会启动中的数据挖掘向导。</span><span class="sxs-lookup"><span data-stu-id="a783b-103">The Data Mining Wizard in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] starts every time that you add a new mining structure to a data mining project.</span></span> <span data-ttu-id="a783b-104">该向导可帮助您选择数据源并设置可定义要用于分析的数据的数据源视图，然后帮助您创建初始模型。</span><span class="sxs-lookup"><span data-stu-id="a783b-104">The wizard helps you choose a data source and set up a data source view that defines the data to be used for analysis, and then helps you create an initial model.</span></span>  
  
 <span data-ttu-id="a783b-105">在该向导的最后阶段，您可以选择将数据划分为定型集和测试集，并启用钻取等功能。</span><span class="sxs-lookup"><span data-stu-id="a783b-105">In the final phase of the wizard, you can optionally divide your data into training and testing sets, and enable features such as drillthrough.</span></span>  
  
## <a name="what-to-know-before-you-start"></a><span data-ttu-id="a783b-106">开始之前要了解的内容</span><span class="sxs-lookup"><span data-stu-id="a783b-106">What to Know Before You Start</span></span>  
 <span data-ttu-id="a783b-107">启动向导之前需要了解以下内容。</span><span class="sxs-lookup"><span data-stu-id="a783b-107">Here are the things you need to know before you start the wizard.</span></span>  
  
-   <span data-ttu-id="a783b-108">是从关系数据库还是根据 OLAP 数据库中的现有多维数据集生成数据挖掘结构和模型？</span><span class="sxs-lookup"><span data-stu-id="a783b-108">Will you build the data mining structure and models from a relational database or from an existing cube in an OLAP database?</span></span>  
  
-   <span data-ttu-id="a783b-109">哪些列包含唯一标识事例记录的键？</span><span class="sxs-lookup"><span data-stu-id="a783b-109">Which columns contain the keys that uniquely identify a case record?</span></span>  
  
-   <span data-ttu-id="a783b-110">您要将哪些列或属性用于预测？</span><span class="sxs-lookup"><span data-stu-id="a783b-110">Which columns or attributes do you want to use for prediction?</span></span> <span data-ttu-id="a783b-111">哪些列或属性适合用作分析的输入？</span><span class="sxs-lookup"><span data-stu-id="a783b-111">Which columns or attributes are good to use as input for analysis?</span></span>  
  
-   <span data-ttu-id="a783b-112">应使用哪种算法？</span><span class="sxs-lookup"><span data-stu-id="a783b-112">Which algorithm should you use?</span></span> <span data-ttu-id="a783b-113">中提供的算法都 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 具有不同的特征并产生不同的结果。</span><span class="sxs-lookup"><span data-stu-id="a783b-113">The algorithms provided in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] all have different characteristics and produce different results.</span></span> <span data-ttu-id="a783b-114">幸运的是，您并不是只能对每个数据集使用一个模型，您可以通过添加不同的模型来进行任意尝试。</span><span class="sxs-lookup"><span data-stu-id="a783b-114">Fortunately you are not limited to one model for each set of data, so feel free to experiment by adding different models.</span></span>  
  
-   <span data-ttu-id="a783b-115">您是否需要能针对统一数据集来测试模型？</span><span class="sxs-lookup"><span data-stu-id="a783b-115">Do you need to be able to test your models on a unified data set?</span></span> <span data-ttu-id="a783b-116">如果需要，请考虑使用为测试保留一些数据的选项。</span><span class="sxs-lookup"><span data-stu-id="a783b-116">If so, consider using the option to set some data aside for testing.</span></span> <span data-ttu-id="a783b-117">您可以选择一个百分比，并根据需要用指定行数设置其上限。</span><span class="sxs-lookup"><span data-stu-id="a783b-117">You can choose a percentage, and cap that by a specified number of rows if desired.</span></span>  
  
##  <a name="starting-the-data-mining-wizard"></a><a name="BKMK_Using_DM_Wizard"></a> <span data-ttu-id="a783b-118">启动数据挖掘向导</span><span class="sxs-lookup"><span data-stu-id="a783b-118">Starting the Data Mining Wizard</span></span>  
 <span data-ttu-id="a783b-119">若要使用数据挖掘向导，则必须已在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中打开至少包含一个数据挖掘或 OLAP 项目的解决方案。</span><span class="sxs-lookup"><span data-stu-id="a783b-119">To use the Data Mining Wizard, you must have opened a solution in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] that contains at least one data mining or OLAP project.</span></span>  
  
-   <span data-ttu-id="a783b-120">如果你的解决方案已做好数据挖掘准备，则只需在解决方案资源管理器中右键单击“挖掘结构”\*\*\*\* 节点并选择“新建挖掘结构”\*\*\*\* 即可启动该向导。</span><span class="sxs-lookup"><span data-stu-id="a783b-120">If your solution is ready for data mining, you can simply right-click the **Mining Structures** node in Solution Explorer and select **New Mining Structure** to start the wizard.</span></span>  
  
-   <span data-ttu-id="a783b-121">如果解决方案中未包含任何现有项目，则可添加新的数据挖掘项目。</span><span class="sxs-lookup"><span data-stu-id="a783b-121">If your solution does not contain any existing projects, you can add a new data mining project.</span></span> <span data-ttu-id="a783b-122">从“文件”\*\*\*\* 菜单，选择“新建”\*\*\*\*，然后选择“项目”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a783b-122">From the **File** menu, select **New**, and then select **Project**.</span></span> <span data-ttu-id="a783b-123">确保选择模板 **“Analysis Services 多维和数据挖掘项目”**。</span><span class="sxs-lookup"><span data-stu-id="a783b-123">Be sure to choose the template, **Analysis Services Multidimensional and Data Mining Project**.</span></span>  
  
-   <span data-ttu-id="a783b-124">您还可以使用 Analysis Services 导入向导从现有数据挖掘解决方案获取元数据。</span><span class="sxs-lookup"><span data-stu-id="a783b-124">You can also use the Analysis Services Import Wizard to obtain metadata from an existing data mining solution.</span></span> <span data-ttu-id="a783b-125">但是，您不能选择单个对象进行导入；将导入整个数据库，包括任何多维数据集、数据源视图等。另请注意，通过导入创建的新解决方案将自动配置为使用本地默认数据库。</span><span class="sxs-lookup"><span data-stu-id="a783b-125">However, you cannot select the individual objects to import; the entire database is imported, including any cubes, data source views, etc. Also note that the new solution that is created via import is automatically configured to use the local default database.</span></span> <span data-ttu-id="a783b-126">您可能需要先将此更改为其他实例，然后才能处理或浏览对象，如果要从早期版本的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]导入，则可能需要更新对访问接口的引用。</span><span class="sxs-lookup"><span data-stu-id="a783b-126">You might need to change this to another instance before you can process or browse the objects, and if you are importing from a previous version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you might need to update references to providers.</span></span>  
  
 <span data-ttu-id="a783b-127">接下来，您将创建挖掘结构和一个关联的数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="a783b-127">Next, you will create the mining structure and one associated data mining model.</span></span> <span data-ttu-id="a783b-128">您也可以只创建挖掘结构并在稍后添加模型，但先创建测试模型通常最为轻松。</span><span class="sxs-lookup"><span data-stu-id="a783b-128">You can also create just the mining structure and add models later, but it is generally easiest to create a test model first.</span></span>  
  
###  <a name="relational-vs-olap-mining-models"></a><a name="BKMK_Relational"></a> <span data-ttu-id="a783b-129">关系与OLAP 挖掘模型</span><span class="sxs-lookup"><span data-stu-id="a783b-129">Relational vs. OLAP Mining Models</span></span>  
 <span data-ttu-id="a783b-130">为您提供的下一个重要选项可让您确定是使用关系数据源还是使模型基于多维 (OLAP) 数据。</span><span class="sxs-lookup"><span data-stu-id="a783b-130">The next important option that you have is whether to use a relational data source, or to base your model on multidimensional (OLAP) data.</span></span>  
  
 <span data-ttu-id="a783b-131">此时，数据挖掘向导分为两个路径，具体取决于您的数据源是关系数据源还是位于多维数据集中。</span><span class="sxs-lookup"><span data-stu-id="a783b-131">The Data Mining Wizard branches into two paths at this point, depending on whether your data source is relational or in a cube.</span></span> <span data-ttu-id="a783b-132">除数据选择进程之外的其他所有内容都是相同的算法选择、添加维持数据集的能力等，但选择多维数据集数据比使用关系数据稍微复杂一些。</span><span class="sxs-lookup"><span data-stu-id="a783b-132">Everything else except the data selection process is the same-the choice of algorithm, the ability to add a holdout data set, etc.-but selecting cube data is a bit more complex than using relational data.</span></span> <span data-ttu-id="a783b-133">（如果您基于多维数据集创建模型，则在最后还会获得一些其他选项。）</span><span class="sxs-lookup"><span data-stu-id="a783b-133">(You also get some additional options at the end if you create a model based on a cube.)</span></span>  
  
 <span data-ttu-id="a783b-134">有关每个选项的演练的详细说明，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="a783b-134">See the following topics for a walkthrough of each option in more detail:</span></span>  
  
 [<span data-ttu-id="a783b-135">创建关系挖掘结构</span><span class="sxs-lookup"><span data-stu-id="a783b-135">Create a Relational Mining Structure</span></span>](create-a-relational-mining-structure.md)  
 <span data-ttu-id="a783b-136">引导您完成在生成关系数据挖掘模型时做出的决定。</span><span class="sxs-lookup"><span data-stu-id="a783b-136">Walks you through the decisions you make when building a relational data mining model.</span></span>  
  
 [<span data-ttu-id="a783b-137">创建 OLAP 挖掘结构</span><span class="sxs-lookup"><span data-stu-id="a783b-137">Create an OLAP Mining Structure</span></span>](create-an-olap-mining-structure.md)  
 <span data-ttu-id="a783b-138">介绍从 OLAP 多维数据集中选择数据时要做出的其他选择。</span><span class="sxs-lookup"><span data-stu-id="a783b-138">Describes the additional options and selections to make when choosing data from an OLAP cube.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a783b-139">无需拥有多维数据集或 OLAP 数据库即可进行数据挖掘。</span><span class="sxs-lookup"><span data-stu-id="a783b-139">You do not need to have a cube or an OLAP database to do data mining.</span></span> <span data-ttu-id="a783b-140">除非数据已存储在多维数据集中，或者要挖掘 OLAP 维度或 OLAP 聚合或计算的结果，否则，我们建议您将关系表或数据源用于数据挖掘。</span><span class="sxs-lookup"><span data-stu-id="a783b-140">Unless your data is already stored in a cube, or you want to mine OLAP dimensions or the results of OLAP aggregations or calculations, we recommend that you use a relational table or data source for data mining.</span></span>  
  
### <a name="choosing-an-algorithm"></a><span data-ttu-id="a783b-141">选择算法</span><span class="sxs-lookup"><span data-stu-id="a783b-141">Choosing an Algorithm</span></span>  
 <span data-ttu-id="a783b-142">接下来，您必须决定处理数据时要使用的算法。</span><span class="sxs-lookup"><span data-stu-id="a783b-142">Next, you must decide on which algorithm to use in processing your data.</span></span> <span data-ttu-id="a783b-143">此决定可能很难做出。</span><span class="sxs-lookup"><span data-stu-id="a783b-143">This decision can be difficult to make.</span></span> <span data-ttu-id="a783b-144">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中提供的每种算法都有不同的功能并会产生不同的结果，因此，在确定最适合您的数据和业务问题的模型之前，您可以试用多种不同的模型。</span><span class="sxs-lookup"><span data-stu-id="a783b-144">Each algorithm provided in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] has different features and produces different results, so you can experiment and try several different models before determining which is most appropriate for your data and your business problem.</span></span> <span data-ttu-id="a783b-145">请参阅以下主题以查看每种算法最适合的任务的说明：</span><span class="sxs-lookup"><span data-stu-id="a783b-145">See the following topic for an explanation of the tasks to which each algorithm is best suited:</span></span>  
  
 [<span data-ttu-id="a783b-146">数据挖掘算法（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a783b-146">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)  
  
 <span data-ttu-id="a783b-147">同样，可以使用不同的算法创建多个模型，也可以更改算法的参数来创建不同的模型。</span><span class="sxs-lookup"><span data-stu-id="a783b-147">Again, you can create multiple models using different algorithms, or change parameters for the algorithms to create different models.</span></span> <span data-ttu-id="a783b-148">您不应局限于所选的算法，最好的方法是对同一数据创建几个不同的模型。</span><span class="sxs-lookup"><span data-stu-id="a783b-148">You are not locked into your choice of algorithm, and it is good practice to create several different models on the same data.</span></span>  
  
### <a name="define-the-data-used-for-modeling"></a><span data-ttu-id="a783b-149">定义用于建模的数据</span><span class="sxs-lookup"><span data-stu-id="a783b-149">Define the Data Used for Modeling</span></span>  
 <span data-ttu-id="a783b-150">除了从源选择数据之外，还必须指定数据源视图中包含 *事例数据*的表。</span><span class="sxs-lookup"><span data-stu-id="a783b-150">In addition to choosing the data from a source, you must specify which of the table in the data source view contains the *case data*.</span></span> <span data-ttu-id="a783b-151">事例表将用于为数据挖掘模型定型，因此应包含要分析的实体，例如客户及其人口统计信息。</span><span class="sxs-lookup"><span data-stu-id="a783b-151">The case table will be used to train the data mining model, and as such should contain the entities that you want to analyze: for example, customers and their demographic information.</span></span> <span data-ttu-id="a783b-152">每个事例都必须唯一，且必须能被 *事例键*识别。</span><span class="sxs-lookup"><span data-stu-id="a783b-152">Each case must be unique, and must be identifiable by a *case key*.</span></span>  
  
 <span data-ttu-id="a783b-153">除了指定事例表之外，您还可以将 *嵌套表* 包含在数据中。</span><span class="sxs-lookup"><span data-stu-id="a783b-153">In addition to specifying the case table, you can include *nested tables* in your data.</span></span> <span data-ttu-id="a783b-154">嵌套表通常包含有关事例表中实体的附加信息，如客户执行的交易或与实体具有多对一关系的属性。</span><span class="sxs-lookup"><span data-stu-id="a783b-154">A nested table usually contains additional information about the entities in the case table, such as transactions conducted by the customer, or attributes that have a many-to-one relationship with the entity.</span></span> <span data-ttu-id="a783b-155">例如，与 **Customers** 事例表联接的嵌套表可能包括每个客户所购买产品的列表。</span><span class="sxs-lookup"><span data-stu-id="a783b-155">For example, a nested table joined to the **Customers** case table might include a list of products purchased by each customer.</span></span> <span data-ttu-id="a783b-156">在用于分析网站流量的模型中，嵌套表可能包含用户访问过的页面的顺序。</span><span class="sxs-lookup"><span data-stu-id="a783b-156">In a model that analyzes traffic to a Web site, the nested table might include the sequences of pages that the user visited.</span></span> <span data-ttu-id="a783b-157">有关详细信息，请参阅[嵌套表（Analysis Services - 数据挖掘）](nested-tables-analysis-services-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="a783b-157">For more information, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](nested-tables-analysis-services-data-mining.md)</span></span>  
  
### <a name="additional-features"></a><span data-ttu-id="a783b-158">其他功能</span><span class="sxs-lookup"><span data-stu-id="a783b-158">Additional Features</span></span>  
 <span data-ttu-id="a783b-159">为了帮助您选择正确的数据和正确配置数据源，数据挖掘向导还提供了以下功能：</span><span class="sxs-lookup"><span data-stu-id="a783b-159">To assist you in choosing the right data, and configuring the data sources correctly, the Data Mining Wizard provides these additional features:</span></span>  
  
-   <span data-ttu-id="a783b-160">**自动检测数据类型**：该向导将检查列值的唯一性和分布情况，然后提供建议的最佳数据类型和数据使用类型。</span><span class="sxs-lookup"><span data-stu-id="a783b-160">**Auto -detection of data types**: The wizard will examine the uniqueness and distribution of column values and then recommend the best data type, and suggest a usage type for the data.</span></span> <span data-ttu-id="a783b-161">您可以从列表中选择值来覆盖这些建议。</span><span class="sxs-lookup"><span data-stu-id="a783b-161">You can override these suggestions by selecting values from a list.</span></span>  
  
-   <span data-ttu-id="a783b-162">**变量建议**：您可以单击对话框并启动用于计算模型中包含的各个列之间的关联的分析器，并确定在当前给定模型配置的情况下，是否有任何列可能成为结果属性的预测器。</span><span class="sxs-lookup"><span data-stu-id="a783b-162">**Suggestions for variables**: You can click on a dialog box and start an analyzer that calculates correlations across the columns included in the model, and determines whether any columns are likely predictors of the outcome attribute, given the configuration of the model so far.</span></span> <span data-ttu-id="a783b-163">您可以通过键入其他值来覆盖这些建议。</span><span class="sxs-lookup"><span data-stu-id="a783b-163">You can override these suggestions by typing different values.</span></span>  
  
-   <span data-ttu-id="a783b-164">**功能选择**：大多数算法都将自动检测作为良好的预测器的列并优先使用这些列。</span><span class="sxs-lookup"><span data-stu-id="a783b-164">**Feature selection**: Most algorithms will automatically detect columns that are good predictors and use those preferentially.</span></span> <span data-ttu-id="a783b-165">在包含的值过多的列中，将应用 *功能选择* 来减少数据的基数并增大找到有用模式的机会。</span><span class="sxs-lookup"><span data-stu-id="a783b-165">In columns that contain too many values, *feature selection* will be applied, to reduce the cardinality of the data and improve the chances for finding a meaningful pattern.</span></span> <span data-ttu-id="a783b-166">您可以使用模型参数来影响功能选择行为。</span><span class="sxs-lookup"><span data-stu-id="a783b-166">You can affect feature selection behavior by using model parameters.</span></span>  
  
-   <span data-ttu-id="a783b-167">**自动多维数据集切片**：如果挖掘模型基于 OLAP 数据源，则会自动提供使用多维数据集属性对模型进行切片的功能。</span><span class="sxs-lookup"><span data-stu-id="a783b-167">**Automatic cube slicing**: If your mining model is based on an OLAP data source, the ability to slice the model by using cube attributes is automatically provided.</span></span> <span data-ttu-id="a783b-168">这对于创建基于多维数据集数据子集的模型很适用。</span><span class="sxs-lookup"><span data-stu-id="a783b-168">This is handy for crating models based on subsets of cube data.</span></span>  
  
### <a name="completing-the-wizard"></a><span data-ttu-id="a783b-169">完成向导</span><span class="sxs-lookup"><span data-stu-id="a783b-169">Completing the Wizard</span></span>  
 <span data-ttu-id="a783b-170">向导中的最后一步是对挖掘结构和关联的挖掘模型进行命名。</span><span class="sxs-lookup"><span data-stu-id="a783b-170">The last step in the wizard is to name the mining structure and the associated mining model.</span></span> <span data-ttu-id="a783b-171">根据创建的模型类型，您还具有以下重要选项：</span><span class="sxs-lookup"><span data-stu-id="a783b-171">Depending on the type of model you created, you might also have the following important options:</span></span>  
  
-   <span data-ttu-id="a783b-172">如果选择 **“允许钻取”**，则会在模型中启用 *钻取* 。</span><span class="sxs-lookup"><span data-stu-id="a783b-172">If you select **Allow drill through**, the ability to *drill through* is enabled in the model.</span></span> <span data-ttu-id="a783b-173">利用钻取，具有相应权限的用户可以浏览用于生成模型的源数据。</span><span class="sxs-lookup"><span data-stu-id="a783b-173">With drillthrough, users who have the appropriate permissions can explore the source data that is used to build the model.</span></span>  
  
-   <span data-ttu-id="a783b-174">如果要生成 OLAP 模型，您可以选择 **“创建新数据挖掘多维数据集”** 或 **“创建数据挖掘维度”** 选项。</span><span class="sxs-lookup"><span data-stu-id="a783b-174">If you are building an OLAP model, you can select the options, **Create a new data mining cube**, **or Create a data mining dimension**.</span></span> <span data-ttu-id="a783b-175">可利用这两个选项更轻松地浏览已完成的模型并钻取到基础数据。</span><span class="sxs-lookup"><span data-stu-id="a783b-175">Both these options make it easier to browse the completed model and drill through to the underlying data.</span></span>  
  
 <span data-ttu-id="a783b-176">完成数据挖掘向导后，使用数据挖掘设计器来修改挖掘结构和模型、查看模型的准确性、查看结构和模型的特征或者使用模型进行预测。</span><span class="sxs-lookup"><span data-stu-id="a783b-176">After you complete the Data Mining Wizard, you use Data Mining Designer to modify the mining structure and models, to view the accuracy of the model, view characteristics of the structure and models, or make predictions by using the models.</span></span>  
  
 [<span data-ttu-id="a783b-177">返回页首</span><span class="sxs-lookup"><span data-stu-id="a783b-177">Back to Top</span></span>](#BKMK_Using_DM_Wizard)  
  
## <a name="related-content"></a><span data-ttu-id="a783b-178">相关内容</span><span class="sxs-lookup"><span data-stu-id="a783b-178">Related Content</span></span>  
 <span data-ttu-id="a783b-179">若要了解有关在创建数据挖掘模型时需做出的决策的详细信息，请参阅以下链接：</span><span class="sxs-lookup"><span data-stu-id="a783b-179">To learn more about the decisions you need to make when creating a data mining model, see the following links:</span></span>  
  
 [<span data-ttu-id="a783b-180">数据挖掘算法（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a783b-180">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="a783b-181">内容类型（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a783b-181">Content Types &#40;Data Mining&#41;</span></span>](content-types-data-mining.md)  
  
 [<span data-ttu-id="a783b-182">数据类型（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a783b-182">Data Types &#40;Data Mining&#41;</span></span>](data-types-data-mining.md)  
  
 [<span data-ttu-id="a783b-183">功能选择（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a783b-183">Feature Selection &#40;Data Mining&#41;</span></span>](feature-selection-data-mining.md)  
  
 [<span data-ttu-id="a783b-184">缺失值（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a783b-184">Missing Values &#40;Analysis Services - Data Mining&#41;</span></span>](missing-values-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="a783b-185">对挖掘模型的钻取功能</span><span class="sxs-lookup"><span data-stu-id="a783b-185">Drillthrough on Mining Models</span></span>](drillthrough-on-mining-models.md)  
  
## <a name="see-also"></a><span data-ttu-id="a783b-186">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a783b-186">See Also</span></span>  
 <span data-ttu-id="a783b-187">[数据挖掘工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="a783b-187">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="a783b-188">数据挖掘解决方案</span><span class="sxs-lookup"><span data-stu-id="a783b-188">Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
  
