---
title: " (中级数据挖掘教程) 创建解决方案和数据源 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0488b231-1045-4169-aabb-c1005d86ca30
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 48009fae653c4c1a231380e8d286363168ae28d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579444"
---
# <a name="creating-a-solution-and-data-source-intermediate-data-mining-tutorial"></a><span data-ttu-id="71a04-102">创建解决方案和数据源（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="71a04-102">Creating a Solution and Data Source (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="71a04-103">若要使用数据挖掘，必须首先在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中使用 **“Analysis Services 多维和数据挖掘项目”** 模板创建一个项目。</span><span class="sxs-lookup"><span data-stu-id="71a04-103">To work with data mining, you must first create a project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] using the template, **Analysis Services Multidimensional and Data Mining Project**.</span></span> <span data-ttu-id="71a04-104">打开该模板时，它将在设计器中加载您进行数据挖掘时可能需要的所有架构：数据源、挖掘结构和挖掘模型，甚至多维数据集（如果您的挖掘结构使用多维数据）。</span><span class="sxs-lookup"><span data-stu-id="71a04-104">When you open the template, it loads into the designer all the schemas that you might need for data mining: data sources, mining structures and mining models, and even cubes if your mining structure uses multidimensional data.</span></span>  
  
 <span data-ttu-id="71a04-105">创建项目时，在部署解决方案之前，解决方案将存储为本地文件。</span><span class="sxs-lookup"><span data-stu-id="71a04-105">When you create the project, your solution is stored as a local file until the solution is deployed.</span></span> <span data-ttu-id="71a04-106">部署解决方案时， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 会查找在项目属性中指定的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器，并使用与项目相同的名称创建新的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="71a04-106">When you deploy the solution, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] looks for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server specified in the project properties, and creates a new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database with the same name as the project.</span></span> <span data-ttu-id="71a04-107">默认情况下， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 使用新项目的“localhost” \*\*\*\* 实例。</span><span class="sxs-lookup"><span data-stu-id="71a04-107">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses the **localhost** instance for new projects.</span></span> <span data-ttu-id="71a04-108">如果您使用的是命名实例，或者您如果为默认实例指定了其他名称，则必须将项目的部署数据库属性更改为要创建数据挖掘对象的位置。</span><span class="sxs-lookup"><span data-stu-id="71a04-108">If you are using a named instance, or if you specified a different name for the default instance, you must change the deployment database property of the project to the location where you want to create your data mining objects.</span></span>  
  
 <span data-ttu-id="71a04-109">有关项目的详细信息 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，请参阅[创建 Analysis Services 项目 &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt)。</span><span class="sxs-lookup"><span data-stu-id="71a04-109">For more information about [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projects, see [Create an Analysis Services Project &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt).</span></span>  
  
### <a name="to-create-a-new-analysis-services-project-for-this-tutorial"></a><span data-ttu-id="71a04-110">为本教程创建新的 Analysis Services 项目</span><span class="sxs-lookup"><span data-stu-id="71a04-110">To create a new Analysis Services project for this tutorial</span></span>  
  
1.  <span data-ttu-id="71a04-111">打开 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="71a04-111">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="71a04-112">在 **“文件”** 菜单上，指向 **“新建”** ，然后单击 **“项目”** 。</span><span class="sxs-lookup"><span data-stu-id="71a04-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="71a04-113">从 **“已安装的模板”** 窗格中选择 **“Analysis Services 多维和数据挖掘项目”** 。</span><span class="sxs-lookup"><span data-stu-id="71a04-113">Select **Analysis Services Multidimensional and Data Mining Project** from the **Installed Templates** pane.</span></span>  
  
4.  <span data-ttu-id="71a04-114">在“名称” \*\*\*\* 框中，将新项目命名为 **DM Intermediate**。</span><span class="sxs-lookup"><span data-stu-id="71a04-114">In the **Name** box, name the new project **DM Intermediate**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored-optional"></a><span data-ttu-id="71a04-115">更改存储数据挖掘对象的实例（可选）</span><span class="sxs-lookup"><span data-stu-id="71a04-115">To change the instance where data mining objects are stored (optional)</span></span>  
  
1.  <span data-ttu-id="71a04-116">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，单击 **“项目”** 菜单中的 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="71a04-116">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="71a04-117">在“属性页” \*\*\*\* 窗格的左侧，单击“部署” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="71a04-117">In the left side of the **Property Pages** pane, click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="71a04-118">验证 **“服务器”** 名称是否为 **localhost**。</span><span class="sxs-lookup"><span data-stu-id="71a04-118">Verify that the **Server** name is **localhost**.</span></span> <span data-ttu-id="71a04-119">如果使用的是其他实例，请键入该实例的名称。</span><span class="sxs-lookup"><span data-stu-id="71a04-119">If you are using a different instance, type the name of the instance.</span></span> <span data-ttu-id="71a04-120">如果使用的是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的命名实例，请键入计算机名称和实例名称。</span><span class="sxs-lookup"><span data-stu-id="71a04-120">If you are using a named instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], type the machine name and then the instance name.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-deployment-properties-for-a-project-optional"></a><span data-ttu-id="71a04-121">更改项目的部署属性（可选）</span><span class="sxs-lookup"><span data-stu-id="71a04-121">To change the deployment properties for a project (optional)</span></span>  
  
1.  <span data-ttu-id="71a04-122">在解决方案资源管理器中，右键单击该项目，然后选择 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="71a04-122">In Solution Explorer, right-click the project, and then select **Properties**.</span></span>  
  
     <span data-ttu-id="71a04-123">- 或 -</span><span class="sxs-lookup"><span data-stu-id="71a04-123">-- or --</span></span>  
  
     <span data-ttu-id="71a04-124">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，选择 **“项目”** 菜单中的 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="71a04-124">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Project** menu, select **Properties**.</span></span>  
  
2.  <span data-ttu-id="71a04-125">在“属性页” \*\*\*\* 窗格的左侧，单击“部署” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="71a04-125">In the left side of the **Property Pages** pane, click **Deployment**.</span></span>  
  
     <span data-ttu-id="71a04-126">在 **“选项”** 窗格中选择 **“部署模式”**，将选项设置为 **“全部部署”** 以覆盖对象，或者设置为 **“仅部署更改”** 以更新对象或添加对象。</span><span class="sxs-lookup"><span data-stu-id="71a04-126">In the **Options** pane, select **Deployment Mode**, and set the options to **Deploy All** to overwrite, or to **Deploy Changes Only** to update objects or add objects.</span></span>  
  
## <a name="creating-a-data-source"></a><span data-ttu-id="71a04-127">创建数据源</span><span class="sxs-lookup"><span data-stu-id="71a04-127">Creating a Data Source</span></span>  
 <span data-ttu-id="71a04-128">在数据挖掘基础教程中，您创建了一个用于存储 *数据库连接信息的“数据源”*[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="71a04-128">In the Basic Data Mining Tutorial, you created a *data source* that stores connection information for the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span> <span data-ttu-id="71a04-129">在本解决方案中按照相同的步骤创建 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 数据源。</span><span class="sxs-lookup"><span data-stu-id="71a04-129">Follow the same steps to create the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source in this solution.</span></span>  
  
#### <a name="to-create-a-data-source"></a><span data-ttu-id="71a04-130">创建数据源</span><span class="sxs-lookup"><span data-stu-id="71a04-130">To create a data source</span></span>  
  
-   [<span data-ttu-id="71a04-131">创建数据源 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="71a04-131">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
 <span data-ttu-id="71a04-132">一个数据源可以支持多个数据源视图，每个数据源视图可以有多个表。</span><span class="sxs-lookup"><span data-stu-id="71a04-132">A single data source can support multiple data source views, and each data source view can have multiple tables.</span></span> <span data-ttu-id="71a04-133">但是，由于数据源和数据源视图 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 与您创建的数据挖掘模型一起部署到您的数据库中，因此，最好只在每个数据源视图中包括每个数据挖掘模型或模型组所需的表。</span><span class="sxs-lookup"><span data-stu-id="71a04-133">However, because the data source and data source view are deployed to your [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database together with the data mining models that you create, as a best practice you should include in each data source view only those tables that are required for each data mining model or group of models.</span></span>  
  
 <span data-ttu-id="71a04-134">在下一课中，您将添加数据源视图以便支持每个新方案。</span><span class="sxs-lookup"><span data-stu-id="71a04-134">In the following lessons, you will add data source views to support each of the new scenarios.</span></span> <span data-ttu-id="71a04-135">只有市场篮以及顺序分析和聚类分析课程使用相同的数据源视图；别的每个方案使用不同的数据源视图，因此各课程彼此是独立的，可以单独完成。</span><span class="sxs-lookup"><span data-stu-id="71a04-135">Only the market basket and sequence clustering lessons use the same data source view; otherwise, each scenario uses a different data source view, so the lessons are independent of each other and can be completed separately.</span></span>  
  
|<span data-ttu-id="71a04-136">方案</span><span class="sxs-lookup"><span data-stu-id="71a04-136">Scenario</span></span>|<span data-ttu-id="71a04-137">包括在数据源视图中的数据</span><span class="sxs-lookup"><span data-stu-id="71a04-137">Data included in the data source view</span></span>|  
|--------------|-------------------------------------------|  
|[<span data-ttu-id="71a04-138">第2课： &#40;中级数据挖掘教程构建预测方案&#41;</span><span class="sxs-lookup"><span data-stu-id="71a04-138">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)|<span data-ttu-id="71a04-139">不同区域的自行车型号的每月销售报表，收集为单一视图形式。</span><span class="sxs-lookup"><span data-stu-id="71a04-139">Monthly sales reports for bicycle models in different regions, collected as a single view.</span></span>|  
|[<span data-ttu-id="71a04-140">第 3 课：生成市场篮方案（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="71a04-140">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)|<span data-ttu-id="71a04-141">一个包含客户订单列表的表，和一个显示每个客户的单独购买情况的嵌套表。</span><span class="sxs-lookup"><span data-stu-id="71a04-141">A table containing a list of customer orders, and a nested table showing the individual purchases for each customer.</span></span>|  
|[<span data-ttu-id="71a04-142">第4课：生成顺序分析和聚类分析方案 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="71a04-142">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)|<span data-ttu-id="71a04-143">用于市场篮分析的相同数据，添加了显示产品购买订单的标识符。</span><span class="sxs-lookup"><span data-stu-id="71a04-143">The same data that is used for the market basket analysis, with the addition of an identifier that shows the order in which items were purchased.</span></span>|  
|[<span data-ttu-id="71a04-144">第 5 课：生成神经网络模型和逻辑回归模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="71a04-144">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)|<span data-ttu-id="71a04-145">包含来自呼叫中心的一些初步性能跟踪数据的单一表。</span><span class="sxs-lookup"><span data-stu-id="71a04-145">A single table containing some preliminary performance tracking data from a call center.</span></span>|  
  
## <a name="next-lesson"></a><span data-ttu-id="71a04-146">下一课</span><span class="sxs-lookup"><span data-stu-id="71a04-146">Next Lesson</span></span>  
 [<span data-ttu-id="71a04-147">第2课： &#40;中级数据挖掘教程构建预测方案&#41;</span><span class="sxs-lookup"><span data-stu-id="71a04-147">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="71a04-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71a04-148">See Also</span></span>  
 <span data-ttu-id="71a04-149">[数据挖掘项目](../../2014/analysis-services/data-mining/data-mining-projects.md) </span><span class="sxs-lookup"><span data-stu-id="71a04-149">[Data Mining Projects](../../2014/analysis-services/data-mining/data-mining-projects.md) </span></span>  
 [<span data-ttu-id="71a04-150">多维模型中的数据源视图</span><span class="sxs-lookup"><span data-stu-id="71a04-150">Data Source Views in Multidimensional Models</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
