---
title: 市场篮 DMX 教程 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DMX [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- statements [DMX], tutorials
- Data Mining Extensions [Analysis Services], tutorials
- market basket analysis [Analysis Services]
- tutorials [Data Mining]
- tutorials [DMX]
ms.assetid: 6e262a1d-c89e-4033-8368-46cf25168ef5
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fe12f1c4ca1c0946572c61e89f4f4edb8ba9a762
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691383"
---
# <a name="market-basket-dmx-tutorial"></a><span data-ttu-id="f4179-102">市场篮 DMX 教程</span><span class="sxs-lookup"><span data-stu-id="f4179-102">Market Basket DMX Tutorial</span></span>
  <span data-ttu-id="f4179-103">在本教程中，您将学习如何使用数据挖掘扩展插件 (DMX) 查询语言来创建、定型和浏览挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="f4179-103">In this tutorial, you will learn how to create, train, and explore mining models by using the Data Mining Extensions (DMX) query language.</span></span> <span data-ttu-id="f4179-104">然后，您将使用这些挖掘模型创建预测，说明可能同时购买的产品。</span><span class="sxs-lookup"><span data-stu-id="f4179-104">You will then use these mining models to create predictions that describe which products tend to be purchased at the same time.</span></span>  
  
 <span data-ttu-id="f4179-105">将使用 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 示例数据库中所包含的数据创建挖掘模型，该数据库用于存储虚构公司 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 的数据。</span><span class="sxs-lookup"><span data-stu-id="f4179-105">The mining models will be created from the data contained in the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database, which stores data for the fictitious company [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)].</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="f4179-106">是一家大型跨国制造公司。</span><span class="sxs-lookup"><span data-stu-id="f4179-106">is a large, multinational manufacturing company.</span></span> <span data-ttu-id="f4179-107">公司生产金属和复合材料的自行车，产品远销北美、欧洲和亚洲市场。</span><span class="sxs-lookup"><span data-stu-id="f4179-107">The company manufactures and sells metal and composite bicycles to North American, European, and Asian commercial markets.</span></span> <span data-ttu-id="f4179-108">公司总部设在华盛顿州的伯瑟尔市，拥有 290 名雇员，而且拥有多个活跃在世界各地的地区性销售团队。</span><span class="sxs-lookup"><span data-stu-id="f4179-108">Its base operation is located in Bothell, Washington, with 290 employees, and it has several regional sales teams are located throughout their international market base.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="f4179-109">教程方案</span><span class="sxs-lookup"><span data-stu-id="f4179-109">Tutorial Scenario</span></span>  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="f4179-110">决定创建使用数据挖掘功能的自定义应用程序来预测其客户想要同时购买的产品类型。</span><span class="sxs-lookup"><span data-stu-id="f4179-110">has decided to create a custom application that employs data mining functionality to predict what types of products their customers tend to purchase at the same time.</span></span> <span data-ttu-id="f4179-111">该自定义应用程序的目的是能够指定一组产品，并预测另外还有哪些产品将与指定的产品一同购买。</span><span class="sxs-lookup"><span data-stu-id="f4179-111">The goal for the custom application is to be able to specify a set of products, and predict what additional products will be purchased with the specified products.</span></span> <span data-ttu-id="f4179-112">然后，[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 将使用此信息在其网站中添加“建议”功能，并更好地组织向客户提供信息的方式。</span><span class="sxs-lookup"><span data-stu-id="f4179-112">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] will then use this information to add a "suggest" feature to their website, and also to better organize the way that they present information to their customers.</span></span>  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="f4179-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 提供了多个可用于完成此任务的工具：</span><span class="sxs-lookup"><span data-stu-id="f4179-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides several tools that can be used to accomplish this task:</span></span>  
  
-   <span data-ttu-id="f4179-114">DMX 查询语言</span><span class="sxs-lookup"><span data-stu-id="f4179-114">The DMX query language</span></span>  
  
-   <span data-ttu-id="f4179-115">[Microsoft 关联算法](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)</span><span class="sxs-lookup"><span data-stu-id="f4179-115">The [Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)</span></span>  
  
-   <span data-ttu-id="f4179-116"> 中的查询编辑器</span><span class="sxs-lookup"><span data-stu-id="f4179-116">Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]</span></span>  
  
 <span data-ttu-id="f4179-117">数据挖掘扩展插件 (DMX) 是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 提供的一种查询语言，可以使用它来创建和处理挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="f4179-117">Data Mining Extensions (DMX) is a query language provided by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you can use to create and work with mining models.</span></span> <span data-ttu-id="f4179-118">[!INCLUDE[msCoName](../includes/msconame-md.md)]关联算法创建的模型可以预测可能一起购买的产品。</span><span class="sxs-lookup"><span data-stu-id="f4179-118">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm creates models that can predict the products that are likely to be purchased together.</span></span>  
  
 <span data-ttu-id="f4179-119">本教程的目的是提供将在自定义应用程序中使用的 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="f4179-119">The goal of this tutorial is to provide the DMX queries that will be used in the custom application.</span></span>  
  
 <span data-ttu-id="f4179-120">**有关详细信息：** [数据挖掘解决方案](../../2014/analysis-services/data-mining/data-mining-solutions.md)</span><span class="sxs-lookup"><span data-stu-id="f4179-120">**For more information:** [Data Mining Solutions](../../2014/analysis-services/data-mining/data-mining-solutions.md)</span></span>  
  
## <a name="mining-structure-and-mining-models"></a><span data-ttu-id="f4179-121">挖掘结构和挖掘模型</span><span class="sxs-lookup"><span data-stu-id="f4179-121">Mining Structure and Mining Models</span></span>  
 <span data-ttu-id="f4179-122">开始创建 DMX 语句之前，了解 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用来创建挖掘模型的主要对象十分重要。</span><span class="sxs-lookup"><span data-stu-id="f4179-122">Before you begin to create DMX statements, it is important to understand the main objects that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to create mining models.</span></span> <span data-ttu-id="f4179-123">*挖掘结构*是一种数据结构，用于定义从中生成挖掘模型的数据域。</span><span class="sxs-lookup"><span data-stu-id="f4179-123">The *mining structure* is a data structure that defines the data domain from which mining models are built.</span></span> <span data-ttu-id="f4179-124">单个挖掘结构可包含多个共享同一个域的*挖掘模型*。</span><span class="sxs-lookup"><span data-stu-id="f4179-124">A single mining structure can contain multiple *mining models* that share the same domain.</span></span> <span data-ttu-id="f4179-125">挖掘模型可向挖掘结构所代表的数据应用挖掘模型算法。</span><span class="sxs-lookup"><span data-stu-id="f4179-125">A mining model applies a mining model algorithm to the data, which is represented by a mining structure.</span></span>  
  
 <span data-ttu-id="f4179-126">挖掘结构的构造块是挖掘结构列，这些列对数据源所包含的数据进行说明。</span><span class="sxs-lookup"><span data-stu-id="f4179-126">The building blocks of the mining structure are the mining structure columns, which describe the data that the data source contains.</span></span> <span data-ttu-id="f4179-127">这些列包含诸如数据类型、内容类型以及数据分发方式等信息。</span><span class="sxs-lookup"><span data-stu-id="f4179-127">These columns contain information such as data type, content type, and how the data is distributed.</span></span>  
  
 <span data-ttu-id="f4179-128">挖掘模型必须包含挖掘结构中所述的键列，以及其余列的子集。</span><span class="sxs-lookup"><span data-stu-id="f4179-128">Mining models must contain the key column described in the mining structure, as well as a subset of the remaining columns.</span></span> <span data-ttu-id="f4179-129">挖掘模型定义每个列的用法以及用于创建挖掘模型的算法。</span><span class="sxs-lookup"><span data-stu-id="f4179-129">The mining model defines the usage for each column and defines the algorithm that is used to create the mining model.</span></span> <span data-ttu-id="f4179-130">例如，在 DMX 中，您可以将一列指定为键列或 PREDICT 列。</span><span class="sxs-lookup"><span data-stu-id="f4179-130">For example, in DMX you can specify that a column is a Key column or a PREDICT column.</span></span> <span data-ttu-id="f4179-131">如果有一列未指定，则会将该列假定为一个输入列。</span><span class="sxs-lookup"><span data-stu-id="f4179-131">If a column is left unspecified, it is assumed to be an input column.</span></span>  
  
 <span data-ttu-id="f4179-132">在 DMX 中，有两种创建挖掘模型的方式。</span><span class="sxs-lookup"><span data-stu-id="f4179-132">In DMX, there are two ways to create mining models.</span></span> <span data-ttu-id="f4179-133">您可以使用 `CREATE MINING MODEL` 语句同时创建挖掘结构以及关联的挖掘模型，也可以首先使用 `CREATE MINING STRUCTURE` 语句创建挖掘结构，然后使用 `ALTER STRUCTURE` 语句向结构中添加挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="f4179-133">You can either create the mining structure and associated mining model together by using the `CREATE MINING MODEL` statement, or you can first create a mining structure by using the `CREATE MINING STRUCTURE` statement, and then add a mining model to the structure by using the `ALTER STRUCTURE` statement.</span></span> <span data-ttu-id="f4179-134">下面将介绍这几种方法。</span><span class="sxs-lookup"><span data-stu-id="f4179-134">These methods are described below.</span></span>  
  
 `CREATE MINING MODEL`  
 <span data-ttu-id="f4179-135">使用此语句可以创建挖掘结构以及关联的同名挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="f4179-135">Use this statement to create a mining structure and associated mining model together using the same name.</span></span> <span data-ttu-id="f4179-136">挖掘模型名称后追加有“Structure”，以便与挖掘结构区分开。</span><span class="sxs-lookup"><span data-stu-id="f4179-136">The mining model name is appended with "Structure" to differentiate it from the mining structure.</span></span>  
  
 <span data-ttu-id="f4179-137">如果要创建包含单一挖掘模型的挖掘结构，则此语句将非常有用。</span><span class="sxs-lookup"><span data-stu-id="f4179-137">This statement is useful if you are creating a mining structure that will contain a single mining model.</span></span>  
  
 <span data-ttu-id="f4179-138">有关详细信息，请参阅 [CREATE MINING MODEL (DMX)](/sql/dmx/create-mining-model-dmx)。</span><span class="sxs-lookup"><span data-stu-id="f4179-138">For more information, see [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).</span></span>  
  
 <span data-ttu-id="f4179-139">CREATE MINING STRUCTURE</span><span class="sxs-lookup"><span data-stu-id="f4179-139">CREATE MINING STRUCTURE</span></span>  
 <span data-ttu-id="f4179-140">使用此语句可创建不带任何模型的新挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="f4179-140">Use this statement to create a new mining structure without any models.</span></span>  
  
 <span data-ttu-id="f4179-141">在使用 CREATE MINING STRUCTURE 时，还可以创建一个维持数据集，使用该数据集可测试任何基于相同挖掘结构的模型。</span><span class="sxs-lookup"><span data-stu-id="f4179-141">When you use CREATE MINING STRUCTURE, you can also create a holdout data set that can be used for testing any models that are based on the same mining structure.</span></span>  
  
 <span data-ttu-id="f4179-142">有关详细信息，请参阅 [CREATE MINING STRUCTURE (DMX)](/sql/dmx/create-mining-structure-dmx)。</span><span class="sxs-lookup"><span data-stu-id="f4179-142">For more information, see [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx).</span></span>  
  
 `ALTER MINING STRUCTURE`  
 <span data-ttu-id="f4179-143">使用此语句可以向服务器中已存在的挖掘结构中添加挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="f4179-143">Use this statement to add a mining model to a mining structure that already exists on the server.</span></span>  
  
 <span data-ttu-id="f4179-144">由于各种原因，您可能需要在单一挖掘结构中添加多个挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="f4179-144">There are several reasons that you would want to add more than one mining model in a single mining structure.</span></span> <span data-ttu-id="f4179-145">例如，可以使用不同的算法创建多个挖掘模型以判断哪种方法效果最佳。</span><span class="sxs-lookup"><span data-stu-id="f4179-145">For example, you might create several mining models using different algorithms to see which one works best.</span></span> <span data-ttu-id="f4179-146">也可以创建使用相同算法的多个挖掘模型，但将每个挖掘模型中的某个参数设置为不同的值来寻找最佳参数设置。</span><span class="sxs-lookup"><span data-stu-id="f4179-146">Alternatively, you might create several mining models using the same algorithm, but with a parameter set differently for each mining model to find the best setting for that parameter.</span></span>  
  
 <span data-ttu-id="f4179-147">有关详细信息，请参阅[ALTER 挖掘 STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)。</span><span class="sxs-lookup"><span data-stu-id="f4179-147">For more information, see [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016).</span></span>  
  
 <span data-ttu-id="f4179-148">因为您将创建包含多个挖掘模型的挖掘结构，因此使用本教程中的第二种方法。</span><span class="sxs-lookup"><span data-stu-id="f4179-148">Because you will create a mining structure that contains several mining models, you will use the second method in this tutorial.</span></span>  
  
 <span data-ttu-id="f4179-149">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="f4179-149">**For More Information**</span></span>  
  
 <span data-ttu-id="f4179-150">[数据挖掘扩展插件 &#40;dmx&#41; 参考](/sql/dmx/data-mining-extensions-dmx-reference)，[了解 dmx Select 语句](/sql/dmx/understanding-the-dmx-select-statement)，[使用 dmx 预测查询的结构和用法](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)</span><span class="sxs-lookup"><span data-stu-id="f4179-150">[Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference), [Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement), [Structure and Usage of DMX Prediction Queries](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="f4179-151">学习内容</span><span class="sxs-lookup"><span data-stu-id="f4179-151">What You Will Learn</span></span>  
 <span data-ttu-id="f4179-152">本教程分为以下几课：</span><span class="sxs-lookup"><span data-stu-id="f4179-152">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="f4179-153">第 1 课：创建市场篮挖掘模型</span><span class="sxs-lookup"><span data-stu-id="f4179-153">Lesson 1: Creating the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)  
 <span data-ttu-id="f4179-154">在本课中，您将学习如何使用 `CREATE` 语句创建挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="f4179-154">In this lesson, you will learn how to use the `CREATE` statement to create mining structures.</span></span>  
  
 [<span data-ttu-id="f4179-155">第 2 课：向市场篮挖掘结构中添加挖掘模型</span><span class="sxs-lookup"><span data-stu-id="f4179-155">Lesson 2: Adding Mining Models to the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
 <span data-ttu-id="f4179-156">在本课中，您将学习如何使用 `ALTER` 语句向挖掘结构中添加挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="f4179-156">In this lesson, you will learn how to use the `ALTER` statement to add mining models to a mining structure.</span></span>  
  
 [<span data-ttu-id="f4179-157">第 3 课：处理市场篮挖掘结构</span><span class="sxs-lookup"><span data-stu-id="f4179-157">Lesson 3: Processing the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-3-processing-the-market-basket-mining-structure.md)  
 <span data-ttu-id="f4179-158">在本课中，您将学习如何使用 `INSERT INTO` 语句处理挖掘结构及其关联的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="f4179-158">In this lesson, you will learn how to use the `INSERT INTO` statement to process mining structures and their associated mining models.</span></span>  
  
 [<span data-ttu-id="f4179-159">第 4 课：执行市场篮预测</span><span class="sxs-lookup"><span data-stu-id="f4179-159">Lesson 4: Executing Market Basket Predictions</span></span>](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
 <span data-ttu-id="f4179-160">在本课中，您将学习如何使用 `PREDICTION JOIN` 语句根据挖掘模型创建预测。</span><span class="sxs-lookup"><span data-stu-id="f4179-160">In this lesson, you will learn how to use the `PREDICTION JOIN` statement to create predictions against mining models.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4179-161">要求</span><span class="sxs-lookup"><span data-stu-id="f4179-161">Requirements</span></span>  
 <span data-ttu-id="f4179-162">执行本教程前，请确保安装了下列各项：</span><span class="sxs-lookup"><span data-stu-id="f4179-162">Before doing this tutorial, make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="f4179-163">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4179-163">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="f4179-164">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4179-164">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="f4179-165"> 数据库</span><span class="sxs-lookup"><span data-stu-id="f4179-165">The [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database</span></span>  
  
 <span data-ttu-id="f4179-166">为了增强安全性，默认情况下将不安装该示例数据库。</span><span class="sxs-lookup"><span data-stu-id="f4179-166">By default, the sample databases are not installed, to enhance security.</span></span> <span data-ttu-id="f4179-167">若要安装的正式示例数据库 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅 [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) Microsoft SQL Server 产品示例 "部分中的" Microsoft SQL Server 示例和社区项目 "主页。</span><span class="sxs-lookup"><span data-stu-id="f4179-167">To install the official sample databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], go to [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) or on the Microsoft SQL Server Samples and Community Projects home page in the section Microsoft SQL Server Product Samples.</span></span> <span data-ttu-id="f4179-168">单击 "**数据库**"，再单击 "**发布**" 选项卡，然后选择所需的数据库。</span><span class="sxs-lookup"><span data-stu-id="f4179-168">Click **Databases**, then click the **Releases** tab and select the databases that you want.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4179-169">查看教程时，建议您将 "**下一个主题**" 和 "**上一个主题**" 按钮添加到文档查看器工具栏。</span><span class="sxs-lookup"><span data-stu-id="f4179-169">When you review tutorials, we recommend that you add **Next topic** and **Previous topic** buttons to the document viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4179-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4179-170">See Also</span></span>  
 <span data-ttu-id="f4179-171">[自行车购买者 DMX 教程](../../2014/tutorials/bike-buyer-dmx-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="f4179-171">[Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md) </span></span>  
 <span data-ttu-id="f4179-172">[数据挖掘基础教程](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="f4179-172">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="f4179-173">第 3 课：生成市场篮方案（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="f4179-173">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
  
