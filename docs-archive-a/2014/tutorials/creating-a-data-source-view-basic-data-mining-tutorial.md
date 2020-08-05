---
title: 创建数据源视图 (基本数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c1e68a88-0f82-415d-becc-78d180d4f845
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4582845c905ef95601cbff2c810633f0cc901e3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580480"
---
# <a name="creating-a-data-source-view-basic-data-mining-tutorial"></a><span data-ttu-id="3d1a4-102">创建数据源视图（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="3d1a4-102">Creating a Data Source View (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="3d1a4-103">数据源视图是在某个数据源的基础上生成的，并且定义可在您的挖掘结构中使用的数据的子集。</span><span class="sxs-lookup"><span data-stu-id="3d1a4-103">A data source view is built on a data source and defines a subset of the data, which you can then use in your mining structures.</span></span> <span data-ttu-id="3d1a4-104">您还可以使用数据源视图来添加列、创建计算列和聚合以及添加命名视图。</span><span class="sxs-lookup"><span data-stu-id="3d1a4-104">You can also use the data source view to add columns, create calculated columns and aggregates, and add named views.</span></span> <span data-ttu-id="3d1a4-105">通过数据源视图，可以选择与项目相关的数据，建立表之间的关系，以及修改数据的结构，而不必修改原始的数据源。</span><span class="sxs-lookup"><span data-stu-id="3d1a4-105">By using data source views, you can select the data that relates to your project, establish relationships between tables, and modify the structure of the data, without modifying the original data source.</span></span> <span data-ttu-id="3d1a4-106">有关详细信息，请参阅 [多维模型中的数据源视图](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)。</span><span class="sxs-lookup"><span data-stu-id="3d1a4-106">For more information, see [Data Source Views in Multidimensional Models](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models).</span></span>  
  
### <a name="to-create-a-data-source-view"></a><span data-ttu-id="3d1a4-107">创建数据源视图</span><span class="sxs-lookup"><span data-stu-id="3d1a4-107">To create a data source view</span></span>  
  
1.  <span data-ttu-id="3d1a4-108">在**解决方案资源管理器**中，右键单击 "**数据源视图**"，然后选择 "**新建数据源视图**"。</span><span class="sxs-lookup"><span data-stu-id="3d1a4-108">In **Solution Explorer**, right-click **Data Source Views**, and select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="3d1a4-109">在“欢迎使用数据源视图向导”  页上，单击“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="3d1a4-109">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="3d1a4-110">在 "**选择数据源**" 页的 "**关系数据源**" 下，选择在上一个任务中创建的艾德公司 DW 2012 数据源。</span><span class="sxs-lookup"><span data-stu-id="3d1a4-110">On the **Select a Data Source** page, under **Relational data sources**, select the Adventure Works DW 2012 data source that you created in the last task.</span></span> <span data-ttu-id="3d1a4-111">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3d1a4-111">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3d1a4-112">如果要创建数据源，请右键单击 "**数据源**"，然后单击 "**新建数据源**" 以启动 "数据源向导"。</span><span class="sxs-lookup"><span data-stu-id="3d1a4-112">If you want to create a data source, right-click **Data Sources** and then click **New Data Source** to start the Data Source Wizard.</span></span>  
  
4.  <span data-ttu-id="3d1a4-113">在 "**选择表和视图**" 页上，选择下列对象，然后单击右箭头将它们包含在新的数据源视图中：</span><span class="sxs-lookup"><span data-stu-id="3d1a4-113">On the **Select Tables and Views** page, select the following objects, and then click the right arrow to include them in the new data source view:</span></span>  
  
    -   <span data-ttu-id="3d1a4-114">\*\*ProspectiveBuyer (dbo) \*\* -预期自行车购买者的表</span><span class="sxs-lookup"><span data-stu-id="3d1a4-114">**ProspectiveBuyer (dbo)** - table of prospective bike buyers</span></span>  
  
    -   <span data-ttu-id="3d1a4-115">\*\*vTargetMail (dbo) \*\*查看有关过去自行车购买者的历史数据</span><span class="sxs-lookup"><span data-stu-id="3d1a4-115">**vTargetMail (dbo)** - view of historical data about past bike buyers</span></span>  
  
5.  <span data-ttu-id="3d1a4-116">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3d1a4-116">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="3d1a4-117">在 "**完成向导**" 页上，默认情况下将数据源视图命名为 "艾德作品 DW 2012"。</span><span class="sxs-lookup"><span data-stu-id="3d1a4-117">On the **Completing the Wizard** page, by default the data source view is named Adventure Works DW 2012.</span></span> <span data-ttu-id="3d1a4-118">将名称更改为 `Targeted Mailing` ，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="3d1a4-118">Change the name to `Targeted Mailing`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="3d1a4-119">新数据源视图将在 "目标" " **dsv [设计]** " 选项卡中打开。</span><span class="sxs-lookup"><span data-stu-id="3d1a4-119">The new data source view opens in the **Targeted Mailing.dsv [Design]** tab.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="3d1a4-120">课程中的前一个任务</span><span class="sxs-lookup"><span data-stu-id="3d1a4-120">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="3d1a4-121">创建数据源 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="3d1a4-121">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="3d1a4-122">下一课</span><span class="sxs-lookup"><span data-stu-id="3d1a4-122">Next Lesson</span></span>  
 [<span data-ttu-id="3d1a4-123">第2课： &#40;基本数据挖掘教程生成目标邮件结构&#41;</span><span class="sxs-lookup"><span data-stu-id="3d1a4-123">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="3d1a4-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3d1a4-124">See Also</span></span>  
 [<span data-ttu-id="3d1a4-125">定义数据源视图 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="3d1a4-125">Defining a Data Source View &#40;Analysis Services&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/defining-a-data-source-view-analysis-services)  
  
  
