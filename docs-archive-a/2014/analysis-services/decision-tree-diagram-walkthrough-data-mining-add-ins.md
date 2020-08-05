---
title: 决策树关系图演练 (数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- shapes, data mining
- diagram, decision tree
- Visio shapes, decision tree
- decision tree [data mining]
ms.assetid: 9566f6a2-c750-4125-ba5e-42c7251a78c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: bbe54db1ab3d00d074917db770a9a731f884f49a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581011"
---
# <a name="decision-tree-diagram-walkthrough--data-mining-add-ins"></a><span data-ttu-id="950bf-102">决策树关系图演练 (数据挖掘外接程序) </span><span class="sxs-lookup"><span data-stu-id="950bf-102">Decision Tree Diagram Walkthrough  (Data Mining Add-ins)</span></span>
  <span data-ttu-id="950bf-103">如果您已创建决策树模型，则可以使用决策树形状或依赖关系网络形状在 Visio 创建自定义关系图。</span><span class="sxs-lookup"><span data-stu-id="950bf-103">If you have created a decision tree model, you can create a customized diagram in Visio by using either the Decision Tree shape or the Dependency Network shape.</span></span> <span data-ttu-id="950bf-104">本主题介绍使用**决策树**形状和这些控件可以执行的自定义：</span><span class="sxs-lookup"><span data-stu-id="950bf-104">This topic describes the customizations you can perform using the **Decision Tree** shape and these controls:</span></span>  
  
-   <span data-ttu-id="950bf-105">决策树关系图的呈现控件</span><span class="sxs-lookup"><span data-stu-id="950bf-105">Rendering controls for the decision tree diagram</span></span>  
  
     <span data-ttu-id="950bf-106">这些选项是在将形状拖放到 Visio 工作区中时启动的**决策树向导**的一部分。</span><span class="sxs-lookup"><span data-stu-id="950bf-106">These options are part of the **Decision Tree Wizard** that is launched when you drop a shape into the Visio workspace.</span></span>  
  
-   <span data-ttu-id="950bf-107">**数据挖掘布局**工具栏</span><span class="sxs-lookup"><span data-stu-id="950bf-107">**Data Mining Layout** toolbar</span></span>  
  
     <span data-ttu-id="950bf-108">这些选项将添加到 Visio 工作区以便与形状交互。</span><span class="sxs-lookup"><span data-stu-id="950bf-108">These options are added to the Visio workspace to help you interact with the shape.</span></span>  
  
## <a name="build-a-decision-tree-diagram"></a><span data-ttu-id="950bf-109">生成决策树关系图</span><span class="sxs-lookup"><span data-stu-id="950bf-109">Build a Decision Tree Diagram</span></span>  
 <span data-ttu-id="950bf-110">您将决策树形状拖到 Visio 页面上，以启动**决策树 Visio 形状向导**并设置关系图选项。</span><span class="sxs-lookup"><span data-stu-id="950bf-110">You drop the Decision Tree shape onto the Visio page to launch the **Decision Tree Visio Shape Wizard** and set diagram options.</span></span>  
  
#### <a name="use-the-decision-tree-wizard"></a><span data-ttu-id="950bf-111">使用决策树向导</span><span class="sxs-lookup"><span data-stu-id="950bf-111">Use the Decision Tree Wizard</span></span>  
  
1.  <span data-ttu-id="950bf-112">如果在 "**形状**" 列表中看不到 " **Microsoft 数据挖掘形状**"，请单击 "**更多形状**"，选择 "**打开模具**"，然后从默认安装位置打开模板。</span><span class="sxs-lookup"><span data-stu-id="950bf-112">If you do not see **Microsoft Data Mining Shapes** in the **Shapes** list, click **More Shapes**, select **Open Stencil**, and open the template from the default installation location.</span></span>  
  
     <span data-ttu-id="950bf-113">\<drive>： \Program 文件 (x85) \Microsoft SQL Server 2012 DM 外接程序</span><span class="sxs-lookup"><span data-stu-id="950bf-113">\<drive>:\Program files (x85)\Microsoft SQL Server 2012 DM Add-Ins</span></span>  
  
2.  <span data-ttu-id="950bf-114">将**决策树**形状拖到页面上。</span><span class="sxs-lookup"><span data-stu-id="950bf-114">Drag the **Decision Tree** shape onto the page.</span></span>  
  
3.  <span data-ttu-id="950bf-115">在**决策树 Visio 形状向导**的 "欢迎" 页上，单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="950bf-115">On the welcome page of the **Decision Tree Visio Shape Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="950bf-116">在**群集向导**的 "**选择数据源**" 页上，选择与 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 要可视化的模型的服务器之间的连接。</span><span class="sxs-lookup"><span data-stu-id="950bf-116">On the **Select a Data Source** page of the **Cluster Wizard**, choose a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that has the model you want to visualize.</span></span>  
  
5.  <span data-ttu-id="950bf-117">选择适当的挖掘模型，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="950bf-117">Select an appropriate mining model, and click **Next**.</span></span>  
  
     <span data-ttu-id="950bf-118">此关系图类型支持使用决策树或线性回归算法创建的模型。</span><span class="sxs-lookup"><span data-stu-id="950bf-118">This diagram type supports models created using the Decision Trees or Linear Regression algorithm.</span></span>  
  
6.  <span data-ttu-id="950bf-119">在 "**选择决策树**" 页上，选择要显示的单个树。</span><span class="sxs-lookup"><span data-stu-id="950bf-119">On the **Select Decision Tree** page, choose an individual tree to display.</span></span>  
  
     <span data-ttu-id="950bf-120">树对导致已建模的特定结果的交互建模;因此，即使模型包含多个结果，一次只能显示一个树。</span><span class="sxs-lookup"><span data-stu-id="950bf-120">A tree models the interactions that lead to a particular outcome you've modeled; therefore, even if your model contains multiple outcomes, you can display only one tree at a time.</span></span>  
  
7.  <span data-ttu-id="950bf-121">在 "**选择决策树**" 对话框中，您还可以设置这些呈现选项：</span><span class="sxs-lookup"><span data-stu-id="950bf-121">In the **Select Decision Tree** dialog box, you can also set these rendering options:</span></span>  
  
     <span data-ttu-id="950bf-122">**最大呈现深度**</span><span class="sxs-lookup"><span data-stu-id="950bf-122">**Maximum Rendering Depth**</span></span>  
     <span data-ttu-id="950bf-123">使用此选项可控制显示的节点数目。</span><span class="sxs-lookup"><span data-stu-id="950bf-123">Use this option to control how many nodes are displayed.</span></span>  
  
     <span data-ttu-id="950bf-124">决策树可能会变得很深，从而产生无法适合该页的关系图。</span><span class="sxs-lookup"><span data-stu-id="950bf-124">A decision tree might go very deep, creating a diagram that does not fit on the page.</span></span> <span data-ttu-id="950bf-125">使用此控件可重点关注最左侧（也更加重要）的节点。</span><span class="sxs-lookup"><span data-stu-id="950bf-125">Use this control to focus on the leftmost nodes, which are more important.</span></span>  
  
     <span data-ttu-id="950bf-126">默认设置是三级节点。</span><span class="sxs-lookup"><span data-stu-id="950bf-126">The default is three levels of nodes.</span></span>  
  
     <span data-ttu-id="950bf-127">**选择值的颜色和显示文本**</span><span class="sxs-lookup"><span data-stu-id="950bf-127">**Select color and display text for values**</span></span>  
     <span data-ttu-id="950bf-128">选择表示每种结果的颜色。</span><span class="sxs-lookup"><span data-stu-id="950bf-128">Choose the color that will represent each one of the outcomes.</span></span> <span data-ttu-id="950bf-129">如果您不指定颜色，则会使用当前视频主题颜色自动生成颜色。</span><span class="sxs-lookup"><span data-stu-id="950bf-129">If you do not specify colors, they are automatically generated using the current video theme colors.</span></span>  
  
8.  <span data-ttu-id="950bf-130">单击 "**高级**"，为决策树关系图中的每个节点自定义以下选项。</span><span class="sxs-lookup"><span data-stu-id="950bf-130">Click **Advanced** to customize the following options for each of the nodes in the decision tree diagram.</span></span>  
  
     <span data-ttu-id="950bf-131">**明暗度变量**和**状态**</span><span class="sxs-lookup"><span data-stu-id="950bf-131">**Shading Variable** and **State**</span></span>  
     <span data-ttu-id="950bf-132">选择要在树关系图中显示的目标结果。</span><span class="sxs-lookup"><span data-stu-id="950bf-132">Choose the target outcome that you want to show in the tree diagram.</span></span>  
  
     <span data-ttu-id="950bf-133">**显示直方图**</span><span class="sxs-lookup"><span data-stu-id="950bf-133">**Show Histogram**</span></span>  
     <span data-ttu-id="950bf-134">向每个节点添加图表以显示定义该节点的规则。</span><span class="sxs-lookup"><span data-stu-id="950bf-134">Adds a chart to each node that shows the rules that define that node.</span></span>  
  
     <span data-ttu-id="950bf-135">**显示标签**</span><span class="sxs-lookup"><span data-stu-id="950bf-135">**Show Label**</span></span>  
     <span data-ttu-id="950bf-136">向直方图添加列名称。</span><span class="sxs-lookup"><span data-stu-id="950bf-136">Adds column names to the histogram.</span></span>  
  
     <span data-ttu-id="950bf-137">**显示概率**</span><span class="sxs-lookup"><span data-stu-id="950bf-137">**Show Probability**</span></span>  
     <span data-ttu-id="950bf-138">显示每个值的概率。</span><span class="sxs-lookup"><span data-stu-id="950bf-138">Displays the probability of each value.</span></span>  
  
     <span data-ttu-id="950bf-139">**显示支持**</span><span class="sxs-lookup"><span data-stu-id="950bf-139">**Show Support**</span></span>  
     <span data-ttu-id="950bf-140">显示对每个值的支持。</span><span class="sxs-lookup"><span data-stu-id="950bf-140">Displays the support for each value.</span></span>  
  
     <span data-ttu-id="950bf-141">**显示页脚**</span><span class="sxs-lookup"><span data-stu-id="950bf-141">**Show Footer**</span></span>  
     <span data-ttu-id="950bf-142">添加用于将所有显示的值相加的页脚。</span><span class="sxs-lookup"><span data-stu-id="950bf-142">Adds a footer that sums all displayed values.</span></span>  
  
     <span data-ttu-id="950bf-143">**显示页眉**</span><span class="sxs-lookup"><span data-stu-id="950bf-143">**Show Header**</span></span>  
     <span data-ttu-id="950bf-144">添加列标题。</span><span class="sxs-lookup"><span data-stu-id="950bf-144">Adds column headings.</span></span>  
  
     <span data-ttu-id="950bf-145">**显示无支持的状态**</span><span class="sxs-lookup"><span data-stu-id="950bf-145">**Show states with zero support**</span></span>  
     <span data-ttu-id="950bf-146">可用来显示缺失的值。</span><span class="sxs-lookup"><span data-stu-id="950bf-146">Lets you display missing values.</span></span>  
  
9. <span data-ttu-id="950bf-147">单击 "**完成**" 以创建关系图。</span><span class="sxs-lookup"><span data-stu-id="950bf-147">Click **Finish** to create the graph.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="950bf-148">在某些环境中，图表中的连接器可能无法在 Office 2013 中呈现。</span><span class="sxs-lookup"><span data-stu-id="950bf-148">In some environments, connectors in the chart might fail to render in Office 2013.</span></span>  
  
## <a name="explore-and-modify-the-finished-diagram"></a><span data-ttu-id="950bf-149">浏览和修改已完成的关系图</span><span class="sxs-lookup"><span data-stu-id="950bf-149">Explore and Modify the Finished Diagram</span></span>  
 <span data-ttu-id="950bf-150">完成**决策树 Visio 形状向导**后，visio 会在页面上创建一个树关系图，以图形方式显示导致预测结果的规则。</span><span class="sxs-lookup"><span data-stu-id="950bf-150">After you have completed the **Decision Tree Visio Shape Wizard**, Visio creates a tree diagram on the page that graphically displays the rules that lead to the predicted outcome.</span></span>  
  
 <span data-ttu-id="950bf-151">您可以使用以下用于决策树关系图的控件继续修改形状。</span><span class="sxs-lookup"><span data-stu-id="950bf-151">You can continue to modify the shape by using the following controls for decision tree diagrams:</span></span>  
  
#### <a name="using-the-decision-tree-option-menus"></a><span data-ttu-id="950bf-152">使用决策树选项菜单</span><span class="sxs-lookup"><span data-stu-id="950bf-152">Using the decision tree option menus</span></span>  
  
1.  <span data-ttu-id="950bf-153">单击 "**外接程序**" 功能区，然后显示用于处理数据挖掘关系图的自定义工具栏之一：</span><span class="sxs-lookup"><span data-stu-id="950bf-153">Click the **Add-Ins** ribbon, and then display one of the custom toolbars used for working with data mining diagrams:</span></span>  
  
     <span data-ttu-id="950bf-154">**布局**</span><span class="sxs-lookup"><span data-stu-id="950bf-154">**Layout**</span></span>  
     <span data-ttu-id="950bf-155">优化树的排列以适合当前页。</span><span class="sxs-lookup"><span data-stu-id="950bf-155">Optimizes the arrangement of the tree to fit the current page.</span></span>  
  
     <span data-ttu-id="950bf-156">**调整页大小**</span><span class="sxs-lookup"><span data-stu-id="950bf-156">**Resize Page**</span></span>  
     <span data-ttu-id="950bf-157">此控件适用于早期 HTML 版本。</span><span class="sxs-lookup"><span data-stu-id="950bf-157">This control was intended for earlier HTML versions.</span></span> <span data-ttu-id="950bf-158">改用 Visio 页面大小调整控件。</span><span class="sxs-lookup"><span data-stu-id="950bf-158">Use the Visio page resizing controls instead,</span></span>  
  
     <span data-ttu-id="950bf-159">**说明**</span><span class="sxs-lookup"><span data-stu-id="950bf-159">**Description**</span></span>  
     <span data-ttu-id="950bf-160">在选择树的一个节点后，单击此选项可显示有关该节点情况的详细信息。</span><span class="sxs-lookup"><span data-stu-id="950bf-160">When a node of the tree is selected, click this option to display details about the cases in the node.</span></span>  
  
2.  <span data-ttu-id="950bf-161">使用 Visio 的 "**设计**" 功能区中的 "**重新布局页面**" 选项来试验不同的树布局。</span><span class="sxs-lookup"><span data-stu-id="950bf-161">Use the **Re-Layout Page** option in the Visio **Design** ribbon to experiment with different tree layouts.</span></span>  
  
3.  <span data-ttu-id="950bf-162">使用 "**设计**" 选项卡上的 "**连接器**" 选项来更改在树中的节点之间使用的连接器。</span><span class="sxs-lookup"><span data-stu-id="950bf-162">Use the **Connectors** option on the **Design** tab to change the connectors used between nodes in the tree.</span></span>  
  
4.  <span data-ttu-id="950bf-163">使用 Visio "**视图**" 功能区的 "**任务窗格**" 区域中的 "**平移和缩放**" 控件，可以重点关注关系图的特定区域。</span><span class="sxs-lookup"><span data-stu-id="950bf-163">Use the **Pan and Zoom** control, in the **Task Pane** area of the Visio **View** ribbon, to focus on a particular area of the diagram.</span></span>  
  
5.  <span data-ttu-id="950bf-164">右键单击树中的任一节点，从与决策树关系图相关的以下快捷菜单选项中选择：</span><span class="sxs-lookup"><span data-stu-id="950bf-164">Right-click any node in the tree, and choose from these shortcut menu options specific to decision tree diagrams:</span></span>  
  
     <span data-ttu-id="950bf-165">**优化页面布局**</span><span class="sxs-lookup"><span data-stu-id="950bf-165">**Improve Page Layout**</span></span>  
     <span data-ttu-id="950bf-166">在页面上平均分布节点，调整页面视图以便可以看到所有节点。</span><span class="sxs-lookup"><span data-stu-id="950bf-166">Distributes the nodes evenly on the page and adjusts the page view to see all nodes.</span></span>  
  
     <span data-ttu-id="950bf-167">**将子级移到新页**</span><span class="sxs-lookup"><span data-stu-id="950bf-167">**Move Children to New Page**</span></span>  
     <span data-ttu-id="950bf-168">将当前所选节点的子级移到新页。</span><span class="sxs-lookup"><span data-stu-id="950bf-168">Moves the children of the currently selected node to a new page.</span></span>  
  
     <span data-ttu-id="950bf-169">**折叠子节点**</span><span class="sxs-lookup"><span data-stu-id="950bf-169">**Collapse Child Nodes**</span></span>  
     <span data-ttu-id="950bf-170">隐藏当前所选节点的子级。</span><span class="sxs-lookup"><span data-stu-id="950bf-170">Hides the children of the currently selected node.</span></span>  
  
     <span data-ttu-id="950bf-171">**展开子节点**</span><span class="sxs-lookup"><span data-stu-id="950bf-171">**Expand Child Nodes**</span></span>  
     <span data-ttu-id="950bf-172">显示当前所选节点的子级。</span><span class="sxs-lookup"><span data-stu-id="950bf-172">Displays the children of the currently selected node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="950bf-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="950bf-173">See Also</span></span>  
 [<span data-ttu-id="950bf-174">解决 Visio 数据挖掘关系图 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="950bf-174">Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;</span></span>](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
