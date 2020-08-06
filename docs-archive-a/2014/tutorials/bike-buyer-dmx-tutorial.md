---
title: 自行车购买者 DMX 教程 |Microsoft Docs
ms.custom: ''
ms.date: 10/19/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DMX [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- statements [DMX], tutorials
- Data Mining Extensions [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 4b634cc1-86dc-42ec-9804-a19292fe8448
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3cf9a0c9e6059330c0b8edbd8228f617ba093564
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691403"
---
# <a name="bike-buyer-dmx-tutorial"></a><span data-ttu-id="e7b13-102">自行车购买者 DMX 教程</span><span class="sxs-lookup"><span data-stu-id="e7b13-102">Bike Buyer DMX Tutorial</span></span>
  <span data-ttu-id="e7b13-103">在本教程中，您将学习如何使用数据挖掘扩展插件 (DMX) 查询语言来创建、定型和浏览挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e7b13-103">In this tutorial, you will learn how create, train, and explore mining models by using the Data Mining Extensions (DMX) query language.</span></span> <span data-ttu-id="e7b13-104">然后，您将使用这些挖掘模型创建预测，确定客户是否将购买自行车。</span><span class="sxs-lookup"><span data-stu-id="e7b13-104">You will then use these mining models to create predictions that determine whether a customer will purchase a bicycle.</span></span>  
  
 <span data-ttu-id="e7b13-105">将使用 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 示例数据库中所包含的数据创建挖掘模型，该数据库用于存储虚构公司 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 的数据。</span><span class="sxs-lookup"><span data-stu-id="e7b13-105">The mining models will be created from the data contained in the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database, which stores data for the fictitious company [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)].</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="e7b13-106">是一家大型跨国制造公司。</span><span class="sxs-lookup"><span data-stu-id="e7b13-106">is a large, multinational manufacturing company.</span></span> <span data-ttu-id="e7b13-107">公司生产金属和复合材料的自行车，产品远销北美、欧洲和亚洲市场。</span><span class="sxs-lookup"><span data-stu-id="e7b13-107">The company manufactures and sells metal and composite bicycles to North American, European, and Asian commercial markets.</span></span> <span data-ttu-id="e7b13-108">公司总部设在华盛顿州的伯瑟尔市，拥有 290 名雇员，而且拥有多个活跃在世界各地的地区性销售团队。</span><span class="sxs-lookup"><span data-stu-id="e7b13-108">Its base operation is located in Bothell, Washington, with 290 employees, and it has several regional sales teams located throughout their international market base.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="e7b13-109">教程方案</span><span class="sxs-lookup"><span data-stu-id="e7b13-109">Tutorial Scenario</span></span>  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="e7b13-110">已决定通过创建使用数据挖掘功能的自定义应用程序来扩展其数据分析。</span><span class="sxs-lookup"><span data-stu-id="e7b13-110">has decided to extend their data analysis by creating a custom application that uses data mining functionality.</span></span> <span data-ttu-id="e7b13-111">自定义应用程序的目的是能够：</span><span class="sxs-lookup"><span data-stu-id="e7b13-111">Their goal for the custom application is to be able to:</span></span>  
  
-   <span data-ttu-id="e7b13-112">输入潜在客户的特定特征并预测这些客户是否将购买自行车。</span><span class="sxs-lookup"><span data-stu-id="e7b13-112">Take as input specific characteristics about a potential customer and predict whether they will buy a bicycle.</span></span>  
  
-   <span data-ttu-id="e7b13-113">输入潜在客户的列表及其特征，并预测哪些客户将购买自行车。</span><span class="sxs-lookup"><span data-stu-id="e7b13-113">Take as input a list of potential customers, as well as characteristics about the customers, and predict which ones will buy a bicycle.</span></span>  
  
 <span data-ttu-id="e7b13-114">在第一种情况下，客户数据由客户注册页提供；在第二种情况下，潜在客户的列表由 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 市场部提供。</span><span class="sxs-lookup"><span data-stu-id="e7b13-114">In the first case, customer data is provided by a customer registration page, and in the second case, a list of potential customers is provided by the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] marketing department.</span></span>  
  
 <span data-ttu-id="e7b13-115">此外，市场部还请求了将现有客户根据各种特征（例如，他们的居住地、孩子个数以及上下班路程）分组到不同类别中。</span><span class="sxs-lookup"><span data-stu-id="e7b13-115">In addition, the marketing department has asked for the ability to group existing customers into categories based on characteristics such as where they live, the number of children they have, and their commute distance.</span></span> <span data-ttu-id="e7b13-116">他们要查看这些群集是否可用于帮助确定特定的客户类型。</span><span class="sxs-lookup"><span data-stu-id="e7b13-116">They want to see whether these clusters can be used to help target specific kinds of customers.</span></span> <span data-ttu-id="e7b13-117">这将需要另外的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e7b13-117">This will require an additional mining model.</span></span>  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="e7b13-118">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 提供了多个可用于完成这些任务的工具：</span><span class="sxs-lookup"><span data-stu-id="e7b13-118">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides several tools that can be used to accomplish these tasks:</span></span>  
  
-   <span data-ttu-id="e7b13-119">DMX 查询语言</span><span class="sxs-lookup"><span data-stu-id="e7b13-119">The DMX query language</span></span>  
  
-   <span data-ttu-id="e7b13-120">[Microsoft 决策树算法](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)和[Microsoft 聚类分析算法](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)</span><span class="sxs-lookup"><span data-stu-id="e7b13-120">The [Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md) and the [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)</span></span>  
  
-   <span data-ttu-id="e7b13-121"> 中的查询编辑器</span><span class="sxs-lookup"><span data-stu-id="e7b13-121">Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]</span></span>  
  
 <span data-ttu-id="e7b13-122">数据挖掘扩展插件 (DMX) 是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 提供的一种查询语言，可以使用它来创建和处理挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e7b13-122">Data Mining Extensions (DMX) is a query language provided by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you can use to create and work with mining models.</span></span> <span data-ttu-id="e7b13-123">[!INCLUDE[msCoName](../includes/msconame-md.md)] 决策树算法创建的模型可用于预测某人是否将购买自行车。</span><span class="sxs-lookup"><span data-stu-id="e7b13-123">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm creates models that can be used to predict whether someone will purchase a bicycle.</span></span> <span data-ttu-id="e7b13-124">生成的模型可以将单个客户或客户表作为一个输入。</span><span class="sxs-lookup"><span data-stu-id="e7b13-124">The resulting model can take an individual customer or a table of customers as an input.</span></span> <span data-ttu-id="e7b13-125">[!INCLUDE[msCoName](../includes/msconame-md.md)] 聚类分析算法可以根据共享特征创建客户分组。</span><span class="sxs-lookup"><span data-stu-id="e7b13-125">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm can create groupings of customers based on shared characteristics.</span></span> <span data-ttu-id="e7b13-126">本教程的目的是提供将在自定义应用程序中使用的 DMX 脚本。</span><span class="sxs-lookup"><span data-stu-id="e7b13-126">The goal of this tutorial is to provide the DMX scripts that will be used in the custom application.</span></span>  
  
 <span data-ttu-id="e7b13-127">**有关详细信息：** [数据挖掘解决方案](../../2014/analysis-services/data-mining/data-mining-solutions.md)</span><span class="sxs-lookup"><span data-stu-id="e7b13-127">**For more information:** [Data Mining Solutions](../../2014/analysis-services/data-mining/data-mining-solutions.md)</span></span>  
  
## <a name="mining-structure-and-mining-models"></a><span data-ttu-id="e7b13-128">挖掘结构和挖掘模型</span><span class="sxs-lookup"><span data-stu-id="e7b13-128">Mining Structure and Mining Models</span></span>  
 <span data-ttu-id="e7b13-129">开始创建 DMX 语句之前，了解 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用来创建挖掘模型的主要对象十分重要。</span><span class="sxs-lookup"><span data-stu-id="e7b13-129">Before you begin to create DMX statements, it is important to understand the main objects that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to create mining models.</span></span> <span data-ttu-id="e7b13-130">挖掘结构是一种数据结构，它定义生成挖掘模型的数据域。</span><span class="sxs-lookup"><span data-stu-id="e7b13-130">The mining structure is a data structure that defines the data domain from which mining models are built.</span></span> <span data-ttu-id="e7b13-131">单个挖掘结构可以包含多个共享相同域的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e7b13-131">A single mining structure can contain multiple mining models that share the same domain.</span></span> <span data-ttu-id="e7b13-132">挖掘模型可向挖掘结构所代表的数据应用挖掘模型算法。</span><span class="sxs-lookup"><span data-stu-id="e7b13-132">A mining model applies a mining model algorithm to the data, which is represented by a mining structure.</span></span>  
  
 <span data-ttu-id="e7b13-133">挖掘结构的构造块是挖掘结构列，这些列对数据源所包含的数据进行说明。</span><span class="sxs-lookup"><span data-stu-id="e7b13-133">The building blocks of the mining structure are the mining structure columns, which describe the data that the data source contains.</span></span> <span data-ttu-id="e7b13-134">这些列包含诸如数据类型、内容类型以及数据分发方式等信息。</span><span class="sxs-lookup"><span data-stu-id="e7b13-134">These columns contain information such as data type, content type, and how the data is distributed.</span></span>  
  
 <span data-ttu-id="e7b13-135">挖掘模型必须包含挖掘结构中所述的键列，以及其余列的子集。</span><span class="sxs-lookup"><span data-stu-id="e7b13-135">Mining models must contain the key column described in the mining structure, as well as a subset of the remaining columns.</span></span> <span data-ttu-id="e7b13-136">挖掘模型定义每个列的用法以及用于创建挖掘模型的算法。</span><span class="sxs-lookup"><span data-stu-id="e7b13-136">The mining model defines the usage for each column and defines the algorithm that is used to create the mining model.</span></span> <span data-ttu-id="e7b13-137">例如，在 DMX 中，您可以将一列指定为键列或 PREDICT 列。</span><span class="sxs-lookup"><span data-stu-id="e7b13-137">For example, in DMX you can specify that a column is a Key column or a PREDICT column.</span></span> <span data-ttu-id="e7b13-138">如果有一列未指定，则会将该列假定为一个输入列。</span><span class="sxs-lookup"><span data-stu-id="e7b13-138">If a column is left unspecified, it is assumed to be an input column.</span></span>  
  
 <span data-ttu-id="e7b13-139">在 DMX 中，有两种创建挖掘模型的方式。</span><span class="sxs-lookup"><span data-stu-id="e7b13-139">In DMX, there are two ways to create mining models.</span></span> <span data-ttu-id="e7b13-140">您可以使用 CREATE MINING MODEL 语句同时创建挖掘结构以及关联的挖掘模型，也可以首先使用 CREATE MINING STRUCTURE 语句创建挖掘结构，然后使用 ALTER STRUCTURE 语句向结构中添加挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e7b13-140">You can either create the mining structure and associated mining model together by using the CREATE MINING MODEL statement, or you can first create a mining structure by using the CREATE MINING STRUCTURE statement, and then add a mining model to the structure by using the ALTER STRUCTURE statement.</span></span> <span data-ttu-id="e7b13-141">下表对这些方法进行了说明。</span><span class="sxs-lookup"><span data-stu-id="e7b13-141">These methods are described in the following table.</span></span>  
  
 <span data-ttu-id="e7b13-142">CREATE MINING MODEL</span><span class="sxs-lookup"><span data-stu-id="e7b13-142">CREATE MINING MODEL</span></span>  
 <span data-ttu-id="e7b13-143">使用此语句可以创建挖掘结构以及关联的同名挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e7b13-143">Use this statement to create a mining structure and associated mining model together using the same name.</span></span> <span data-ttu-id="e7b13-144">挖掘模型名称后追加有“Structure”，以便与挖掘结构区分开。</span><span class="sxs-lookup"><span data-stu-id="e7b13-144">The mining model name is appended with "Structure" to differentiate it from the mining structure.</span></span> <span data-ttu-id="e7b13-145">如果要创建包含单一挖掘模型的挖掘结构，则此语句将非常有用。</span><span class="sxs-lookup"><span data-stu-id="e7b13-145">This statement is useful if you are creating a mining structure that will contain a single mining model.</span></span>  
  
 <span data-ttu-id="e7b13-146">有关详细信息，请参阅 [CREATE MINING MODEL (DMX)](/sql/dmx/create-mining-model-dmx)。</span><span class="sxs-lookup"><span data-stu-id="e7b13-146">For more information, see [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).</span></span>  
  
 <span data-ttu-id="e7b13-147">ALTER MINING STRUCTURE</span><span class="sxs-lookup"><span data-stu-id="e7b13-147">ALTER MINING STRUCTURE</span></span>  
 <span data-ttu-id="e7b13-148">使用此语句可以向服务器中已存在的挖掘结构中添加挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e7b13-148">Use this statement to add a mining model to a mining structure that already exists on the server.</span></span> <span data-ttu-id="e7b13-149">如果要创建包含多个不同挖掘模型的挖掘结构，则此语句将非常有用。</span><span class="sxs-lookup"><span data-stu-id="e7b13-149">This statement is useful if you want to create a mining structure that contains several different mining models.</span></span> <span data-ttu-id="e7b13-150">由于各种原因，您可能需要在单一挖掘结构中添加多个挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e7b13-150">There are several reasons that you would want to add more than one mining model in a single mining structure.</span></span> <span data-ttu-id="e7b13-151">例如，可以创建使用不同算法的多个挖掘模型来判断哪种算法效果最佳。</span><span class="sxs-lookup"><span data-stu-id="e7b13-151">For example, you might create several mining models that use different algorithms to see which algorithm works best.</span></span> <span data-ttu-id="e7b13-152">可以创建使用相同算法的多个挖掘模型，但通过将每一个挖掘模型中的一个参数设置为不同的值来查找最佳参数设置。</span><span class="sxs-lookup"><span data-stu-id="e7b13-152">You might create several mining models that use the same algorithm, but with a parameter set differently for each mining model to find the best setting for the parameter.</span></span>  
  
 <span data-ttu-id="e7b13-153">有关详细信息，请参阅[ALTER 挖掘 STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)。</span><span class="sxs-lookup"><span data-stu-id="e7b13-153">For more information, see [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016).</span></span>  
  
 <span data-ttu-id="e7b13-154">因为您将创建包含多个挖掘模型的挖掘结构，因此使用本教程中的第二种方法。</span><span class="sxs-lookup"><span data-stu-id="e7b13-154">Because you will create a mining structure that contains several mining models, you will use the second method in this tutorial.</span></span>  
  
 <span data-ttu-id="e7b13-155">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="e7b13-155">**For More Information**</span></span>  
  
 <span data-ttu-id="e7b13-156">[数据挖掘扩展插件 &#40;dmx&#41; 参考](/sql/dmx/data-mining-extensions-dmx-reference)，[了解 dmx Select 语句](/sql/dmx/understanding-the-dmx-select-statement)，[使用 dmx 预测查询的结构和用法](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)</span><span class="sxs-lookup"><span data-stu-id="e7b13-156">[Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference), [Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement), [Structure and Usage of DMX Prediction Queries](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="e7b13-157">学习内容</span><span class="sxs-lookup"><span data-stu-id="e7b13-157">What You Will Learn</span></span>  
 <span data-ttu-id="e7b13-158">本教程分为以下几课：</span><span class="sxs-lookup"><span data-stu-id="e7b13-158">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="e7b13-159">第 1 课：创建自行车购买者挖掘结构</span><span class="sxs-lookup"><span data-stu-id="e7b13-159">Lesson 1: Creating the Bike Buyer Mining Structure</span></span>](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)  
 <span data-ttu-id="e7b13-160">在本课中，您将学习如何使用 `CREATE` 语句创建挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="e7b13-160">In this lesson, you will learn how to use the `CREATE` statement to create mining structures.</span></span>  
  
 [<span data-ttu-id="e7b13-161">第 2 课：向自行车购买者挖掘结构添加挖掘模型</span><span class="sxs-lookup"><span data-stu-id="e7b13-161">Lesson 2: Adding Mining Models to the Bike Buyer Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
 <span data-ttu-id="e7b13-162">在本课中，您将学习如何使用 `ALTER` 语句向挖掘结构中添加挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e7b13-162">In this lesson, you will learn how to use the `ALTER` statement to add mining models to a mining structure.</span></span>  
  
 [<span data-ttu-id="e7b13-163">第 3 课：处理自行车购买者挖掘结构</span><span class="sxs-lookup"><span data-stu-id="e7b13-163">Lesson 3: Processing the Bike Buyer Mining Structure</span></span>](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
 <span data-ttu-id="e7b13-164">在本课中，您将学习如何使用 `INSERT INTO` 语句处理挖掘结构及其关联的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e7b13-164">In this lesson you will learn how to use the `INSERT INTO` statement to process mining structures and their associated mining models.</span></span>  
  
 [<span data-ttu-id="e7b13-165">第 4 课：浏览自行车购买者挖掘模型</span><span class="sxs-lookup"><span data-stu-id="e7b13-165">Lesson 4: Browsing the Bike Buyer Mining Models</span></span>](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
 <span data-ttu-id="e7b13-166">在本课中，您将学习如何使用 `SELECT` 语句浏览挖掘模型的内容。</span><span class="sxs-lookup"><span data-stu-id="e7b13-166">In this lesson, you will learn how to use the `SELECT` statement to explore the content of the mining models.</span></span>  
  
 [<span data-ttu-id="e7b13-167">第 5 课：执行预测查询</span><span class="sxs-lookup"><span data-stu-id="e7b13-167">Lesson 5: Executing Prediction Queries</span></span>](../../2014/tutorials/lesson-5-executing-prediction-queries.md)  
 <span data-ttu-id="e7b13-168">在本课中，您将学习如何使用 `PREDICTION JOIN` 语句根据挖掘模型创建预测。</span><span class="sxs-lookup"><span data-stu-id="e7b13-168">In this lesson, you will learn how to use the `PREDICTION JOIN` statement to create predictions against mining models.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7b13-169">要求</span><span class="sxs-lookup"><span data-stu-id="e7b13-169">Requirements</span></span>  
 <span data-ttu-id="e7b13-170">执行本教程前，请确保安装了下列各项：</span><span class="sxs-lookup"><span data-stu-id="e7b13-170">Before doing this tutorial, make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="e7b13-171">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7b13-171">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="e7b13-172">[!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)]、 [!INCLUDE[ssASversion10](../includes/ssasversion10-md.md)] 、 [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] 或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7b13-172">[!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)], [!INCLUDE[ssASversion10](../includes/ssasversion10-md.md)], [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="e7b13-173">[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="e7b13-173">The [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span> <span data-ttu-id="e7b13-174">为了增强安全性，默认情况下将不安装该示例数据库。</span><span class="sxs-lookup"><span data-stu-id="e7b13-174">By default, the sample databases are not installed, to enhance security.</span></span> <span data-ttu-id="e7b13-175">若要安装的正式示例数据库 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请访问[Microsoft SQL 示例数据库](https://go.microsoft.com/fwlink/?LinkId=88417)页，并选择要安装的数据库。</span><span class="sxs-lookup"><span data-stu-id="e7b13-175">To install official sample databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], visit the [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) page and select the databases that you want to install..</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7b13-176">查看教程时，建议您将 "**下一个主题**" 和 "**上一个主题**" 按钮添加到文档查看器工具栏。</span><span class="sxs-lookup"><span data-stu-id="e7b13-176">When you review tutorials, we recommend that you add **Next topic** and **Previous topic** buttons to the document viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b13-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7b13-177">See Also</span></span>  
 <span data-ttu-id="e7b13-178">[市场篮 DMX 教程](../../2014/tutorials/market-basket-dmx-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="e7b13-178">[Market Basket DMX Tutorial](../../2014/tutorials/market-basket-dmx-tutorial.md) </span></span>  
 [<span data-ttu-id="e7b13-179">数据挖掘基础教程</span><span class="sxs-lookup"><span data-stu-id="e7b13-179">Basic Data Mining Tutorial</span></span>](../../2014/tutorials/basic-data-mining-tutorial.md)  
  
  
