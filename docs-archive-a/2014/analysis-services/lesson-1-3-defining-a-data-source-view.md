---
title: 定义数据源视图 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: af00938a-5a06-4fae-b2fc-f3fb0ca3cea5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d59c5fbe5fd4a07596745447567a72499ddabd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577045"
---
# <a name="defining-a-data-source-view"></a><span data-ttu-id="5686f-102">定义数据源视图</span><span class="sxs-lookup"><span data-stu-id="5686f-102">Defining a Data Source View</span></span>
  <span data-ttu-id="5686f-103">定义了将在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目中使用的数据源后，下一步通常是定义项目的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="5686f-103">After you define the data sources that you will use in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, the next step is generally to define a data source view for the project.</span></span> <span data-ttu-id="5686f-104">数据源视图是元数据的单个统一视图，这些元数据来自数据源在项目中定义的指定表和视图。</span><span class="sxs-lookup"><span data-stu-id="5686f-104">A data source view is a single, unified view of the metadata from the specified tables and views that the data source defines in the project.</span></span> <span data-ttu-id="5686f-105">通过在数据源视图中存储元数据，可以在开发过程中使用元数据，而无需打开与任何基础数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="5686f-105">Storing the metadata in the data source view enables you to work with the metadata during development without an open connection to any underlying data source.</span></span> <span data-ttu-id="5686f-106">有关详细信息，请参阅 [多维模型中的数据源视图](multidimensional-models/data-source-views-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="5686f-106">For more information, see [Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md).</span></span>  
  
 <span data-ttu-id="5686f-107">在以下任务中，定义一个数据源视图，其中包括来自 **AdventureWorksDW2012** 数据源的五个表。</span><span class="sxs-lookup"><span data-stu-id="5686f-107">In the following task, you define a data source view that includes five tables from the **AdventureWorksDW2012** data source.</span></span>  
  
### <a name="to-define-a-new-data-source-view"></a><span data-ttu-id="5686f-108">定义一个新的数据源视图</span><span class="sxs-lookup"><span data-stu-id="5686f-108">To define a new data source view</span></span>  
  
1.  <span data-ttu-id="5686f-109">在解决方案资源管理器中（在 Microsoft Visual Studio 窗口的右侧），右键单击“数据源视图”\*\*\*\*，然后单击“新建数据源视图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5686f-109">In Solution Explorer (on the right of the Microsoft Visual Studio window), right-click **Data Source Views**, and then click **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="5686f-110">在“欢迎使用数据源视图向导”  页上，单击“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="5686f-110">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span> <span data-ttu-id="5686f-111">此时将显示“选择数据源”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="5686f-111">The **Select a Data Source** page appears.</span></span>  
  
3.  <span data-ttu-id="5686f-112">已选中“关系数据源”\*\*\*\* 下的 **Adventure Works DW 2012** 数据源。</span><span class="sxs-lookup"><span data-stu-id="5686f-112">Under **Relational data sources**, the **Adventure Works DW 2012** data source is selected.</span></span> <span data-ttu-id="5686f-113">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="5686f-113">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5686f-114">若要创建一个基于多个数据源的数据源视图，必须先定义一个基于单一数据源的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="5686f-114">To create a data source view that is based on multiple data sources, first define a data source view that is based on a single data source.</span></span> <span data-ttu-id="5686f-115">此数据源将被称为主数据源。</span><span class="sxs-lookup"><span data-stu-id="5686f-115">This data source is then called the primary data source.</span></span> <span data-ttu-id="5686f-116">随后，可以添加来自辅助数据源的表和视图。</span><span class="sxs-lookup"><span data-stu-id="5686f-116">You can then add tables and views from a secondary data source.</span></span> <span data-ttu-id="5686f-117">在基于多个数据源中的相关表设计包含属性的维度时，可能需要将 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据源定义为主数据源，以使用其分布式查询引擎功能。</span><span class="sxs-lookup"><span data-stu-id="5686f-117">When designing dimensions that contain attributes based on related tables in multiple data sources, you might need to define a [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data source as the primary data source to use its distributed query engine capabilities.</span></span>  
  
4.  <span data-ttu-id="5686f-118">在“选择表和视图”\*\*\*\* 页上，可以从选定的数据源提供的对象列表中选择表和视图。</span><span class="sxs-lookup"><span data-stu-id="5686f-118">On the **Select Tables and Views** page, select tables and views from the list of objects that are available from the selected data source.</span></span> <span data-ttu-id="5686f-119">可以筛选此列表，以帮助您选择表和视图。</span><span class="sxs-lookup"><span data-stu-id="5686f-119">You can filter this list to help you select tables and views.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5686f-120">单击右上角中的最大化按钮，以便窗口占据整个屏幕。</span><span class="sxs-lookup"><span data-stu-id="5686f-120">Click the maximize button in the upper-right corner so that the window covers the full screen.</span></span> <span data-ttu-id="5686f-121">这将更便于查看可用对象的完整列表。</span><span class="sxs-lookup"><span data-stu-id="5686f-121">This makes it easier to see the complete list of available objects.</span></span>  
  
     <span data-ttu-id="5686f-122">在“可用对象”\*\*\*\* 列表中，选择下列对象。</span><span class="sxs-lookup"><span data-stu-id="5686f-122">In the **Available objects** list, select the following objects.</span></span> <span data-ttu-id="5686f-123">在按住 Ctrl 键的同时单击各个表可以选择多个表：</span><span class="sxs-lookup"><span data-stu-id="5686f-123">You can select multiple tables by clicking each while holding down the CTRL key:</span></span>  
  
    -   <span data-ttu-id="5686f-124">**DimCustomer (dbo)**</span><span class="sxs-lookup"><span data-stu-id="5686f-124">**DimCustomer (dbo)**</span></span>  
  
    -   <span data-ttu-id="5686f-125">**DimDate (dbo)**</span><span class="sxs-lookup"><span data-stu-id="5686f-125">**DimDate (dbo)**</span></span>  
  
    -   <span data-ttu-id="5686f-126">**DimGeography (dbo)**</span><span class="sxs-lookup"><span data-stu-id="5686f-126">**DimGeography (dbo)**</span></span>  
  
    -   <span data-ttu-id="5686f-127">**DimProduct (dbo)**</span><span class="sxs-lookup"><span data-stu-id="5686f-127">**DimProduct (dbo)**</span></span>  
  
    -   <span data-ttu-id="5686f-128">**FactInternetSales (dbo)**</span><span class="sxs-lookup"><span data-stu-id="5686f-128">**FactInternetSales (dbo)**</span></span>  
  
5.  <span data-ttu-id="5686f-129">单击此 **>** 选项可将所选表添加到 "**包含的对象**" 列表。</span><span class="sxs-lookup"><span data-stu-id="5686f-129">Click **>** to add the selected tables to the **Included objects** list.</span></span>  
  
6.  <span data-ttu-id="5686f-130">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="5686f-130">Click **Next.**</span></span>  
  
7.  <span data-ttu-id="5686f-131">在“名称”字段中，确保显示 **Adventure Works DW 2012**，然后单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5686f-131">In the Name field, make sure **Adventure Works DW 2012** displays, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="5686f-132">此时，**Adventure Works DW 2012** 数据源视图将显示在解决方案资源管理器的“数据源视图”\*\*\*\* 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="5686f-132">The **Adventure Works DW 2012** data source view appears in the **Data Source Views** folder in Solution Explorer.</span></span> <span data-ttu-id="5686f-133">数据源视图的内容还将显示在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的数据源视图设计器中。</span><span class="sxs-lookup"><span data-stu-id="5686f-133">The content of the data source view is also displayed in Data Source View Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="5686f-134">此设计器包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="5686f-134">This designer contains the following elements:</span></span>  
  
    -   <span data-ttu-id="5686f-135">“关系图”\*\*\*\* 窗格，其中将以图形方式显示各个表及其相互关系。</span><span class="sxs-lookup"><span data-stu-id="5686f-135">A **Diagram** pane in which the tables and their relationships are represented graphically.</span></span>  
  
    -   <span data-ttu-id="5686f-136">“表”\*\*\*\* 窗格，其中将以树的形式显示各个表及其架构元素。</span><span class="sxs-lookup"><span data-stu-id="5686f-136">A **Tables** pane in which the tables and their schema elements are displayed in a tree view.</span></span>  
  
    -   <span data-ttu-id="5686f-137">“关系图组织程序”\*\*\*\* 窗格，可在其中创建子关系图，用于查看数据源视图的子集。</span><span class="sxs-lookup"><span data-stu-id="5686f-137">A **Diagram Organizer** pane in which you can create subdiagrams so that you can view subsets of the data source view.</span></span>  
  
    -   <span data-ttu-id="5686f-138">一个特定于数据源视图设计器的工具栏。</span><span class="sxs-lookup"><span data-stu-id="5686f-138">A toolbar that is specific to Data Source View Designer.</span></span>  
  
8.  <span data-ttu-id="5686f-139">若要最大化 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 开发环境，请单击“最大化”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="5686f-139">To maximize the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] development environment, click the **Maximize** button.</span></span>  
  
9. <span data-ttu-id="5686f-140">若要在“关系图”\*\*\*\* 窗格中以 50% 的缩放比例查看表，请单击“数据源视图设计器”工具栏上的“缩放”\*\*\*\* 图标。</span><span class="sxs-lookup"><span data-stu-id="5686f-140">To view the tables in the **Diagram** pane at 50 percent, click the **Zoom** icon on the Data Source View Designer toolbar.</span></span> <span data-ttu-id="5686f-141">这将隐藏每个表的列详细信息。</span><span class="sxs-lookup"><span data-stu-id="5686f-141">This will hide the column details of each table.</span></span>  
  
10. <span data-ttu-id="5686f-142">若要隐藏解决方案资源管理器，请单击“自动隐藏”\*\*\*\* 按钮，该按钮是标题栏上的图钉图标。</span><span class="sxs-lookup"><span data-stu-id="5686f-142">To hide Solution Explorer, click the **Auto Hide** button, which is the pushpin icon on the title bar.</span></span> <span data-ttu-id="5686f-143">若要再次查看解决方案资源管理器，请将指针放在位于开发环境右侧的解决方案资源管理器选项卡上。</span><span class="sxs-lookup"><span data-stu-id="5686f-143">To view Solution Explorer again, position your pointer over the Solution Explorer tab along the right side of the development environment.</span></span> <span data-ttu-id="5686f-144">若要取消隐藏解决方案资源管理器，请再次单击“自动隐藏”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="5686f-144">To unhide Solution Explorer, click the **Auto Hide** button again.</span></span>  
  
11. <span data-ttu-id="5686f-145">如果“属性”窗口在默认情况下没有隐藏，请单击该窗口和“解决方案资源管理器”窗口的标题栏上的“自动隐藏”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5686f-145">If the windows are not hidden by default, click **Auto Hide** on the title bar of the Properties and Solution Explorer windows.</span></span>  
  
     <span data-ttu-id="5686f-146">现在，即可在“关系图”\*\*\*\* 窗格中查看所有表及其相互关系了。</span><span class="sxs-lookup"><span data-stu-id="5686f-146">You can now view all the tables and their relationships in the **Diagram** pane.</span></span> <span data-ttu-id="5686f-147">注意，在 FactInternetSales 表和 DimDate 表之间存在三种关系。</span><span class="sxs-lookup"><span data-stu-id="5686f-147">Notice that there are three relationships between the FactInternetSales table and the DimDate table.</span></span> <span data-ttu-id="5686f-148">每个销售都具有三个与其关联的日期：订单日期、到期日期和发货日期。</span><span class="sxs-lookup"><span data-stu-id="5686f-148">Each sale has three dates associated with the sale: an order date, a due date, and a ship date.</span></span> <span data-ttu-id="5686f-149">若要查看某种关系的详细信息，可双击“关系图”\*\*\*\* 窗格中的关系箭头。</span><span class="sxs-lookup"><span data-stu-id="5686f-149">To view the details of any relationship, double-click the relationship arrow in the **Diagram** pane.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="5686f-150">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="5686f-150">Next Task in Lesson</span></span>  
 [<span data-ttu-id="5686f-151">修改默认表名</span><span class="sxs-lookup"><span data-stu-id="5686f-151">Modifying Default Table Names</span></span>](lesson-1-4-modifying-default-table-names.md)  
  
## <a name="see-also"></a><span data-ttu-id="5686f-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5686f-152">See Also</span></span>  
 [<span data-ttu-id="5686f-153">多维模型中的数据源视图</span><span class="sxs-lookup"><span data-stu-id="5686f-153">Data Source Views in Multidimensional Models</span></span>](multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
