---
title: 依赖关系网络关系图演练 () 的数据挖掘外接程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Visio shapes, dependency network
- shapes, data mining
- shapes, network
- dependencies
- diagram, dependency network
- data mining layout toolbar
- dependency network
ms.assetid: aac732a8-5262-4649-b7d7-3ccf6f9cfa8b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07f97dac7ffb0211f0ff1e1b58c2e0792d026174
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590427"
---
# <a name="dependency-network-diagram-walkthrough-data-mining-add-ins"></a><span data-ttu-id="8e3e0-102">依赖关系网络关系图演练（数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="8e3e0-102">Dependency Network Diagram Walkthrough (Data Mining Add-ins)</span></span>
  <span data-ttu-id="8e3e0-103">几种不同的数据挖掘模型将网络图用作探索数据中各种关系的方法。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-103">Several different types of data mining models use a network graph as a way of exploring relationships in the data.</span></span> <span data-ttu-id="8e3e0-104">您可以使用 "**依赖关系网络**" 形状将这些模型导入 Visio，然后继续自定义并增强布局。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-104">You can import these models into Visio using the **Dependency Network** shape and then continue to customize and enhance the layout.</span></span> <span data-ttu-id="8e3e0-105">**Visio 数据挖掘形状**包含以下用于处理依赖关系网络关系图的自定义控件：</span><span class="sxs-lookup"><span data-stu-id="8e3e0-105">The **Data Mining Shapes for Visio** include the following custom controls for working with dependency network diagrams:</span></span>  
  
-   <span data-ttu-id="8e3e0-106">网络图的呈现控件</span><span class="sxs-lookup"><span data-stu-id="8e3e0-106">Rendering controls for the network graph</span></span>  
  
     <span data-ttu-id="8e3e0-107">这些选项包括在将形状置于 Visio 工作区中时启动的向导中。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-107">These options are part of the wizard that is launched when you drop a shape into the Visio workspace.</span></span>  
  
-   <span data-ttu-id="8e3e0-108">**数据挖掘布局**工具栏</span><span class="sxs-lookup"><span data-stu-id="8e3e0-108">**Data Mining Layout** toolbar</span></span>  
  
     <span data-ttu-id="8e3e0-109">这些选项将添加到 Visio 工作区以便与依赖关系网络图交互。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-109">These options are added to the Visio workspace to help you interact with the dependency network graph.</span></span>  
  
## <a name="build-a-dependency-network-graph"></a><span data-ttu-id="8e3e0-110">生成依赖关系网络图</span><span class="sxs-lookup"><span data-stu-id="8e3e0-110">Build a Dependency Network Graph</span></span>  
 <span data-ttu-id="8e3e0-111">您将形状拖放到 Visio 页面上，启动 "**依赖关系网络 Visio 形状向导**" 并设置关系图选项。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-111">You drop a shape onto the Visio page to launch the **Dependency Net Visio Shape Wizard** and set diagram options.</span></span>  
  
#### <a name="use-the-dependency-net-visio-shape-wizard"></a><span data-ttu-id="8e3e0-112">使用依赖关系网络 Visio 形状向导</span><span class="sxs-lookup"><span data-stu-id="8e3e0-112">Use the Dependency Net Visio Shape Wizard</span></span>  
  
1.  <span data-ttu-id="8e3e0-113">如果在 "**形状**" 列表中看不到 " **Microsoft 数据挖掘形状**"，请单击 "**更多形状**"，选择 "**打开模具**"，然后从默认安装位置打开模板。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-113">If you do not see **Microsoft Data Mining Shapes** in the **Shapes** list, click **More Shapes**, select **Open Stencil**, and open the template from the default installation location.</span></span>  
  
     <span data-ttu-id="8e3e0-114">\<drive>： \Program 文件 (x85) \Microsoft SQL Server 2012 DM 外接程序</span><span class="sxs-lookup"><span data-stu-id="8e3e0-114">\<drive>:\Program files (x85)\Microsoft SQL Server 2012 DM Add-Ins</span></span>  
  
2.  <span data-ttu-id="8e3e0-115">将 "**依赖关系网络**" 形状拖到页面上以启动向导。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-115">Drag the **Dependency Network** shape onto the page to start the wizard.</span></span> <span data-ttu-id="8e3e0-116">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-116">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="8e3e0-117">在 "**依赖关系网络 Visio 形状向导**" 的 "欢迎" 页上，单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-117">On the welcome page of the **Dependency Network Visio Shape Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="8e3e0-118">在 "**依赖关系网络 Visio 形状向导**" 的 "**选择数据源**" 页上，选择与 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 要可视化的模型的服务器之间的连接。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-118">On the **Select a Data Source** page of the **Dependency Network Visio Shape Wizard**, choose a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that has the model you want to visualize.</span></span>  
  
5.  <span data-ttu-id="8e3e0-119">选择适当的挖掘模型，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-119">Select an appropriate mining model, and click **Next**.</span></span>  
  
     <span data-ttu-id="8e3e0-120">若要选择适当的模型，可以在 "**属性**" 窗格中查看名称、说明、列和数据类型。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-120">To select an appropriate model, you can review the name, description, columns, and type of data in the **Properties** pane.</span></span>  
  
     <span data-ttu-id="8e3e0-121">此形状支持通过使用以下算法创建的模型：</span><span class="sxs-lookup"><span data-stu-id="8e3e0-121">This shape supports models created by using these algorithms:</span></span>  
  
    -   <span data-ttu-id="8e3e0-122">Naïve Bayes</span><span class="sxs-lookup"><span data-stu-id="8e3e0-122">Naïve Bayes</span></span>  
  
    -   <span data-ttu-id="8e3e0-123">决策树</span><span class="sxs-lookup"><span data-stu-id="8e3e0-123">Decision Trees</span></span>  
  
    -   <span data-ttu-id="8e3e0-124">关联规则</span><span class="sxs-lookup"><span data-stu-id="8e3e0-124">Association Rules</span></span>  
  
6.  <span data-ttu-id="8e3e0-125">在页上，**选择要呈现的节点**，自定义关系图的大小，并根据需要进行筛选，以便只包含某些节点。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-125">On the page, **Select Nodes to Render**, customize the size of the graph, and optionally filter to only include certain nodes.</span></span>  
  
     <span data-ttu-id="8e3e0-126">对于大型数据集，依赖关系图可能会变得很大，并且包含许多相关对象，这些对象表示为*节点*。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-126">With a large dataset, a dependency graph can become huge, and contain many related objects, represented as *nodes*.</span></span> <span data-ttu-id="8e3e0-127">通过使用此对话框，可以创建仅包含相关节点的自定义网络图。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-127">By using this dialog box, you can create a custom network graph that includes only the nodes of interest.</span></span>  
  
     <span data-ttu-id="8e3e0-128">[艺术占位符]</span><span class="sxs-lookup"><span data-stu-id="8e3e0-128">[art placeholder]</span></span>  
  
     <span data-ttu-id="8e3e0-129">**要提取的节点数**</span><span class="sxs-lookup"><span data-stu-id="8e3e0-129">**Number of nodes to fetch**</span></span>  
     <span data-ttu-id="8e3e0-130">如果该模型包含的节点数少于指定的节点数，则此设置无效。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-130">If the model contains fewer than the specified number of nodes, this setting has no effect.</span></span> <span data-ttu-id="8e3e0-131">如果该模型包含的节点数多于指定的节点数，则仅显示最强节点。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-131">If the model contains more nodes than the specified number, only the strongest nodes are displayed.</span></span>  
  
     <span data-ttu-id="8e3e0-132">**名称包含**</span><span class="sxs-lookup"><span data-stu-id="8e3e0-132">**Name contains**</span></span>  
     <span data-ttu-id="8e3e0-133">将此框留空然后单击绿色箭头，可检索该模型中的所有节点。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-133">Leave this box blank and click the green arrow to retrieve all nodes in the model.</span></span>  
  
     <span data-ttu-id="8e3e0-134">或者，键入一个字符串并单击绿色箭头，仅返回包含指定字符串的节点。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-134">Or, type a string and click the green arrow to return only those nodes that contain the specified string.</span></span>  
  
     <span data-ttu-id="8e3e0-135">可使用示例数据创建的大多数模型都不是很大，因此对于本示例，请将节点数增加到 10，然后单击绿色箭头以运行查询并获取所有节点的列表。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-135">Most of the models that you can create with the sample data are not big, so for this example, increase the number of nodes to 10, and then click the green arrow to run a query and get the list of all nodes.</span></span>  
  
7.  <span data-ttu-id="8e3e0-136">单击 "**高级**" 设置图形的明暗度和形状选项。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-136">Click **Advanced** to set shading and shape options for the graph.</span></span>  
  
8.  <span data-ttu-id="8e3e0-137">单击 "**关闭**" 以退出 "**高级**选项" 对话框，然后单击 "**完成**" 以创建关系图。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-137">Click **Close** to exit the **Advanced** options dialog box, and then click **Finish** to create the graph.</span></span>  
  
## <a name="explore-and-modify-the-finished-diagram"></a><span data-ttu-id="8e3e0-138">浏览和修改已完成的关系图</span><span class="sxs-lookup"><span data-stu-id="8e3e0-138">Explore and Modify the Finished Diagram</span></span>  
 <span data-ttu-id="8e3e0-139">在 Visio 创建网络依赖关系图之后，可使用 Visio 中的功能继续修改和增强图形。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-139">After Visio has created the network dependency graph, you can continue to modify and enhance the graph by using the features in Visio.</span></span>  
  
 <span data-ttu-id="8e3e0-140">下图显示依赖关系网络图的默认布局。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-140">The following graphic shows the default layout of a dependency network graph.</span></span>  
  
 <span data-ttu-id="8e3e0-141">[艺术占位符]</span><span class="sxs-lookup"><span data-stu-id="8e3e0-141">[art placeholder]</span></span>  
  
1.  <span data-ttu-id="8e3e0-142">使用 Visio "**视图**" 功能区的 "**任务窗格**" 区域中的 "**平移和缩放**" 控件，可以重点关注关系图的某个部分并四处移动关系图。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-142">Use the **Pan and Zoom** control, in the **Task Pane** area of the Visio **View** ribbon, to focus on a section of the graph and move around the diagram.</span></span>  
  
2.  <span data-ttu-id="8e3e0-143">使用 Visio "**重新布局页面**" 选项提供的不同图形布局进行试验。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-143">Experiment with different graph layouts provided by the Visio **Re-Layout Page** option.</span></span>  
  
3.  <span data-ttu-id="8e3e0-144">单击 "**外接程序**" 功能区，然后显示用于处理数据挖掘关系图的自定义工具栏之一：</span><span class="sxs-lookup"><span data-stu-id="8e3e0-144">Click the **Add-Ins** ribbon, and then display one of the custom toolbars used for working with data mining diagrams:</span></span>  
  
     <span data-ttu-id="8e3e0-145">**布局**</span><span class="sxs-lookup"><span data-stu-id="8e3e0-145">**Layout**</span></span>  
     <span data-ttu-id="8e3e0-146">优化页面上节点的布局，更改视图，以便所有节点都可见。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-146">Optimizes the layout of nodes on the page, and changes the view so that all nodes are visible.</span></span>  
  
     <span data-ttu-id="8e3e0-147">**调整页大小**</span><span class="sxs-lookup"><span data-stu-id="8e3e0-147">**Resize Page**</span></span>  
     <span data-ttu-id="8e3e0-148">更改页面的大小，以便所有节点都可见。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-148">Changes the size of the page so that all nodes are visible.</span></span>  
  
     <span data-ttu-id="8e3e0-149">**边缘强度**</span><span class="sxs-lookup"><span data-stu-id="8e3e0-149">**Edge Strength**</span></span>  
     <span data-ttu-id="8e3e0-150">切换整个图形的边缘强度的显示。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-150">Toggles display of edge strength for the entire graph.</span></span> <span data-ttu-id="8e3e0-151">边缘是节点间的连接。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-151">An edge is a connection between nodes.</span></span> <span data-ttu-id="8e3e0-152">您可以使用滑块控件筛选掉弱连接。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-152">You can use the slider control to filter out connections that are not strong.</span></span>  
  
     <span data-ttu-id="8e3e0-153">**滑块**</span><span class="sxs-lookup"><span data-stu-id="8e3e0-153">**Slider**</span></span>  
     <span data-ttu-id="8e3e0-154">**滑块**可帮助控制依赖关系网络关系图中显示的关系的强度。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-154">The **Slider** helps you control the strength of the relationships that are displayed in the dependency network diagram.</span></span>  
  
     <span data-ttu-id="8e3e0-155">该图形中的每个节点都代表一个状态。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-155">Each node in the graph represents a state.</span></span> <span data-ttu-id="8e3e0-156">箭头代表两个状态之间的转换以及与该转换相关联的概率。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-156">An arrow represents a transition between two states and the probability that is associated with the transition.</span></span> <span data-ttu-id="8e3e0-157">若要减少该图形中的节点数量，可向上移动滑动条。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-157">To reduce the number of nodes in the graph, move the slider bar up.</span></span>  
  
     <span data-ttu-id="8e3e0-158">若要增加该图形中的节点数量，可向下移动滑动条。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-158">To increase the number of nodes in the graph, move the slider bar down.</span></span>  
  
     <span data-ttu-id="8e3e0-159">**添加项**</span><span class="sxs-lookup"><span data-stu-id="8e3e0-159">**Add Items**</span></span>  
     <span data-ttu-id="8e3e0-160">打开 "**选择要呈现的节点**" 对话框，以便您可以选择要添加到关系图中的新节点。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-160">Opens the **Select Nodes to Render** dialog box so that you can select new nodes to add to the graph.</span></span>  
  
4.  <span data-ttu-id="8e3e0-161">您可根据需要使图形变得简单或详细并添加批注，同时保持与模型的连接。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-161">You can make the graphs as simple or elaborate as you like, and add annotations, while staying connected to the model.</span></span>  
  
     <span data-ttu-id="8e3e0-162">[图形占位符]</span><span class="sxs-lookup"><span data-stu-id="8e3e0-162">[ art placeholder]</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="8e3e0-163">在 Office 2013 中，无法突出显示早期版本外接程序中提供的依赖节点和其他快捷菜单选项。</span><span class="sxs-lookup"><span data-stu-id="8e3e0-163">Highlighting of dependent nodes and other shortcut menu options that were available in previous versions of the Add-Ins do not work in Office 2013.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e3e0-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8e3e0-164">See Also</span></span>  
 [<span data-ttu-id="8e3e0-165">解决 Visio 数据挖掘关系图 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="8e3e0-165">Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;</span></span>](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
