---
title: 数据挖掘解决方案 |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], about data mining
- data mining [Analysis Services], development
ms.assetid: 84f6548d-ebb0-4e10-9b29-66253fa0a04a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0ab4b5ddcc9958fa36d6c8ecae0e7fd79585b4fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581037"
---
# <a name="data-mining-solutions"></a><span data-ttu-id="94b5d-102">数据挖掘解决方案</span><span class="sxs-lookup"><span data-stu-id="94b5d-102">Data Mining Solutions</span></span>
  <span data-ttu-id="94b5d-103">数据挖掘解决方案是一个包含一个或多个数据挖掘项目的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 解决方案。</span><span class="sxs-lookup"><span data-stu-id="94b5d-103">A data mining solution is an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] solution that contains one or more data mining projects.</span></span>  
  
 <span data-ttu-id="94b5d-104">本节中的主题提供有关如何使用设计和实现集成数据挖掘解决方案的信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="94b5d-104">The topics in this section provide information about how to design and implement an integrated data mining solution by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="94b5d-105">有关数据挖掘设计过程和相关工具的概述，请参阅 [Data Mining Concepts](data-mining-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="94b5d-105">For an overview of the data mining design process and related tools, see [Data Mining Concepts](data-mining-concepts.md).</span></span>  
  
 <span data-ttu-id="94b5d-106">有关对数据挖掘有用的其他项目类型的详细信息，请参阅 [数据挖掘解决方案的相关项目](data-mining-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="94b5d-106">For more information about additional projects types that are useful for data mining, see [Related Projects for Data Mining Solutions](data-mining-solutions.md).</span></span>  
  
 [<span data-ttu-id="94b5d-107">关系与多维解决方案</span><span class="sxs-lookup"><span data-stu-id="94b5d-107">Relational vs. Multidimensional Solutions</span></span>](#bkmk_RelMD)  
  
 [<span data-ttu-id="94b5d-108">部署数据挖掘解决方案</span><span class="sxs-lookup"><span data-stu-id="94b5d-108">Deploying Data Mining Solutions</span></span>](#bkmk_Deploy)  
  
 [<span data-ttu-id="94b5d-109">解决方案演练</span><span class="sxs-lookup"><span data-stu-id="94b5d-109">Solution Walkthroughs</span></span>](#bkmk_Walkthru)  
  
##  <a name="relational-vs-multidimensional-solutions"></a><a name="bkmk_RelMD"></a><span data-ttu-id="94b5d-110">关系与多维解决方案</span><span class="sxs-lookup"><span data-stu-id="94b5d-110">Relational vs. Multidimensional Solutions</span></span>  
 <span data-ttu-id="94b5d-111">数据挖掘解决方案可基于多维数据（即现有多维数据集）或纯关系数据（例如，数据仓库中的表和视图），或者基于文本文件、Excel 工作簿或其他外部数据源。</span><span class="sxs-lookup"><span data-stu-id="94b5d-111">A data mining solution can be based either on multidimensional data-that is, an existing cube-or on purely relational data, such as the tables and views in a data warehouse, or on text files, Excel workbooks, or other external data sources.</span></span>  
  
-   <span data-ttu-id="94b5d-112">可以在现有多维数据库解决方案中创建数据挖掘对象。</span><span class="sxs-lookup"><span data-stu-id="94b5d-112">You can create data mining objects within an existing multidimensional database solution.</span></span>  
  
     <span data-ttu-id="94b5d-113">通常，如果您已创建一个多维数据集，并希望通过将该多维数据集用作数据源来执行数据挖掘，则您需要创建一个与此类似的解决方案。</span><span class="sxs-lookup"><span data-stu-id="94b5d-113">Typically you would create a solution like this if you have already created a cube and want to perform data mining by using the cube as a data source.</span></span> <span data-ttu-id="94b5d-114">当您基于一个多维数据集移动和备份模型时，该多维数据集也将被移动或复制。</span><span class="sxs-lookup"><span data-stu-id="94b5d-114">When you move and backup models based on a cube, the cube must also be moved or copied.</span></span>  
  
-   <span data-ttu-id="94b5d-115">可以创建仅包含数据挖掘对象（包括支持的数据源和数据源视图）的数据挖掘解决方案和仅使用关系数据源的数据挖掘解决方案。</span><span class="sxs-lookup"><span data-stu-id="94b5d-115">You can create a data mining solution that contains only data mining objects, including the supporting data sources and data source views, and that uses relational data source only.</span></span>  
  
     <span data-ttu-id="94b5d-116">这是创建数据挖掘模型的首选方法，因为通常针对关系数据源的处理和查询的速度最快。</span><span class="sxs-lookup"><span data-stu-id="94b5d-116">This is the preferred method for creating data mining models, as processing and querying is generally fastest against relational data sources.</span></span> <span data-ttu-id="94b5d-117">还可以使用 EXPORT 和 IMPORT 命令在服务器间轻松移动和备份模型。</span><span class="sxs-lookup"><span data-stu-id="94b5d-117">You can also easily move and backup models between servers by using the EXPORT and IMPORT commands.</span></span>  
  
##  <a name="deploying-data-mining-solutions"></a><a name="bkmk_Deploy"></a><span data-ttu-id="94b5d-118">部署数据挖掘解决方案</span><span class="sxs-lookup"><span data-stu-id="94b5d-118">Deploying Data Mining Solutions</span></span>  
 <span data-ttu-id="94b5d-119">要将解决方案部署到的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例必须在支持多维对象和数据挖掘对象的模式下运行；即，您不能将数据挖掘对象部署到承载表格模型或 PowerPivot 数据的实例。</span><span class="sxs-lookup"><span data-stu-id="94b5d-119">The instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to which you deploy the solution must be running in a mode that supports multidimensional objects and data mining objects; that is, you cannot deploy data mining objects to an instance that hosts tabular models or PowerPivot data.</span></span>  
  
 <span data-ttu-id="94b5d-120">因此，在 Visual Studio 中创建数据挖掘解决方案时，请务必使用模板 **“Analysis Services 多维和数据挖掘项目”**。</span><span class="sxs-lookup"><span data-stu-id="94b5d-120">Therefore, when you create a data mining solution in Visual Studio, be sure to use the template, **Analysis Services Multidimensional and Data Mining Project**.</span></span>  
  
 <span data-ttu-id="94b5d-121">在部署解决方案时，将在与解决方案文件同名的数据库中的指定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例中创建用于数据挖掘的对象。</span><span class="sxs-lookup"><span data-stu-id="94b5d-121">When you deploy the solution, the objects used for data mining are created in the specified [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, in a database with the same name as the solution file.</span></span>  
  
 <span data-ttu-id="94b5d-122">有关如何同时部署关系解决方案和多维解决方案的详细信息，请参阅 [部署数据挖掘解决方案](deployment-of-data-mining-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="94b5d-122">For more information about how to deploy both relational and multidimensional solutions, see [Deployment of Data Mining Solutions](deployment-of-data-mining-solutions.md).</span></span>  
  
##  <a name="solution-walkthrough"></a><a name="bkmk_Walkthru"></a> <span data-ttu-id="94b5d-123">解决方案演练</span><span class="sxs-lookup"><span data-stu-id="94b5d-123">Solution Walkthrough</span></span>  
 <span data-ttu-id="94b5d-124">概述了如何使用数据挖掘向导创建数据挖掘解决方案。</span><span class="sxs-lookup"><span data-stu-id="94b5d-124">Provides an overview of how to create data mining solutions by using the Data Mining Wizard.</span></span>  
  
 [<span data-ttu-id="94b5d-125">创建关系挖掘结构</span><span class="sxs-lookup"><span data-stu-id="94b5d-125">Create a Relational Mining Structure</span></span>](create-a-relational-mining-structure.md)  
 <span data-ttu-id="94b5d-126">从可组合到数据源视图中的关系数据、文本文件和其他源创建挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="94b5d-126">Create a mining structure from relational data, text files, and other sources that can be combined in a data source view.</span></span>  
  
 [<span data-ttu-id="94b5d-127">创建 OLAP 挖掘结构</span><span class="sxs-lookup"><span data-stu-id="94b5d-127">Create an OLAP Mining Structure</span></span>](create-an-olap-mining-structure.md)  
 <span data-ttu-id="94b5d-128">基于 OLAP 多维数据集中的数据创建挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="94b5d-128">Create a mining structure based on data in an OLAP cube.</span></span> <span data-ttu-id="94b5d-129">可将从 OLAP 数据创建的模型另存为数据挖掘维度，也可将数据和模型集另存为新的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="94b5d-129">Models that you create from OLAP data can be saved as a data mining dimension, or you can save the set of data and your models as a new cube.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94b5d-130">本节内容</span><span class="sxs-lookup"><span data-stu-id="94b5d-130">In This Section</span></span>  
 [<span data-ttu-id="94b5d-131">数据挖掘项目</span><span class="sxs-lookup"><span data-stu-id="94b5d-131">Data Mining Projects</span></span>](data-mining-projects.md)  
  
 [<span data-ttu-id="94b5d-132">处理数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="94b5d-132">Processing Data Mining Objects</span></span>](processing-data-mining-objects.md)  
  
 [<span data-ttu-id="94b5d-133">数据挖掘解决方案的相关项目</span><span class="sxs-lookup"><span data-stu-id="94b5d-133">Related Projects for Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
 [<span data-ttu-id="94b5d-134">部署数据挖掘解决方案</span><span class="sxs-lookup"><span data-stu-id="94b5d-134">Deployment of Data Mining Solutions</span></span>](deployment-of-data-mining-solutions.md)  
  
## <a name="related-tasks-and-topics"></a><span data-ttu-id="94b5d-135">相关任务和主题</span><span class="sxs-lookup"><span data-stu-id="94b5d-135">Related Tasks and Topics</span></span>  
 <span data-ttu-id="94b5d-136">在创建一个基本数据挖掘解决方案（包括数据源和挖掘结构）后，可通过添加新模型、测试并比较模型、创建预测和试用数据子集来基于该解决方案进行生成。</span><span class="sxs-lookup"><span data-stu-id="94b5d-136">After you have created a basic data mining solution, including data sources and a mining structure, you can build on the solution by adding new models, testing and comparing models, creating predictions, and experimenting with subsets of data.</span></span>  
  
 <span data-ttu-id="94b5d-137">有关详细信息，请参阅以下链接：</span><span class="sxs-lookup"><span data-stu-id="94b5d-137">For more information, see the following links:</span></span>  
  
|<span data-ttu-id="94b5d-138">任务</span><span class="sxs-lookup"><span data-stu-id="94b5d-138">Tasks</span></span>|<span data-ttu-id="94b5d-139">主题</span><span class="sxs-lookup"><span data-stu-id="94b5d-139">Topics</span></span>|  
|-----------|------------|  
|<span data-ttu-id="94b5d-140">测试您创建的模型，验证定型数据的质量并创建代表数据挖掘模型的准确性的图表。</span><span class="sxs-lookup"><span data-stu-id="94b5d-140">Test the models you create, validate the quality of your training data, and create charts that represent the accuracy of data mining models.</span></span>|[<span data-ttu-id="94b5d-141">测试和验证（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="94b5d-141">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)|  
|<span data-ttu-id="94b5d-142">通过用数据填充结构及相关模型来定型模型。</span><span class="sxs-lookup"><span data-stu-id="94b5d-142">Train the model by populating the structure and related models with data.</span></span> <span data-ttu-id="94b5d-143">使用新数据更新和扩展模型。</span><span class="sxs-lookup"><span data-stu-id="94b5d-143">Update and extend models with new data.</span></span>|[<span data-ttu-id="94b5d-144">处理数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="94b5d-144">Processing Data Mining Objects</span></span>](processing-data-mining-objects.md)|  
|<span data-ttu-id="94b5d-145">通过对定型数据应用筛选器、选择其他算法或设置高级算法参数来自定义挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="94b5d-145">Customize a mining model by applying filters to the training data, choosing a different algorithm, or setting advanced algorithm parameters.</span></span>|[<span data-ttu-id="94b5d-146">自定义挖掘模型和结构</span><span class="sxs-lookup"><span data-stu-id="94b5d-146">Customize Mining Models and Structure</span></span>](customize-mining-models-and-structure.md)|  
|<span data-ttu-id="94b5d-147">通过对在定型模式下使用的数据应用筛选器来自定义挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="94b5d-147">Customize a mining model by applying filters to the data used in training the mode.</span></span>|[<span data-ttu-id="94b5d-148">向结构中添加挖掘模型（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="94b5d-148">Add Mining Models to a Structure &#40;Analysis Services - Data Mining&#41;</span></span>](add-mining-models-to-a-structure-analysis-services-data-mining.md)|  
|<span data-ttu-id="94b5d-149">更新和管理数据挖掘解决方案。</span><span class="sxs-lookup"><span data-stu-id="94b5d-149">Update and manage data mining solutions.</span></span>|<span data-ttu-id="94b5d-150">链接 TBD</span><span class="sxs-lookup"><span data-stu-id="94b5d-150">Link TBD</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94b5d-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94b5d-151">See Also</span></span>  
 [<span data-ttu-id="94b5d-152">数据挖掘教程 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="94b5d-152">Data Mining Tutorials &#40;Analysis Services&#41;</span></span>](../data-mining-tutorials-analysis-services.md)  
  
  
