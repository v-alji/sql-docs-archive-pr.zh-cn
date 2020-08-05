---
title: 分类关系图演练 () 的数据挖掘外接程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Visio shapes, cluster
- diagram, cluster
- shapes, data mining
- shapes, cluster
- data mining layout toolbar
ms.assetid: 761bef6a-37d4-4b19-944e-f2aadc75a242
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44ee8cce3cd2498d765c9b69e7f352b49cb0f115
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579882"
---
# <a name="cluster-diagram-walkthrough-data-mining-add-ins"></a><span data-ttu-id="56b6e-102">分类关系图演练（数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="56b6e-102">Cluster Diagram Walkthrough (Data Mining Add-ins)</span></span>
  <span data-ttu-id="56b6e-103">创建了聚类分析模型之后，可以使用 "**分类**" 形状将其导入 Visio，然后继续自定义并增强布局。</span><span class="sxs-lookup"><span data-stu-id="56b6e-103">After you have created a clustering model, you can import it into Visio using the **Cluster** shape and then continue to customize and enhance the layout.</span></span> <span data-ttu-id="56b6e-104">**Visio 数据挖掘形状**包含以下用于处理数据挖掘关系图的自定义控件：</span><span class="sxs-lookup"><span data-stu-id="56b6e-104">The **Data Mining Shapes for Visio** include the following custom controls for working with data mining diagrams:</span></span>  
  
-   <span data-ttu-id="56b6e-105">分类关系图的呈现控件</span><span class="sxs-lookup"><span data-stu-id="56b6e-105">Rendering controls for the cluster diagram</span></span>  
  
     <span data-ttu-id="56b6e-106">这些选项是在将形状拖放到 Visio 工作区中时启动的 "**群集向导**" 的一部分。</span><span class="sxs-lookup"><span data-stu-id="56b6e-106">These options are part of the **Cluster Wizard** that is launched when you drop a shape into the Visio workspace.</span></span>  
  
-   <span data-ttu-id="56b6e-107">**数据挖掘布局**工具栏</span><span class="sxs-lookup"><span data-stu-id="56b6e-107">**Data Mining Layout** toolbar</span></span>  
  
     <span data-ttu-id="56b6e-108">这些选项将添加到 Visio 工作区以便与数据挖掘形状交互。</span><span class="sxs-lookup"><span data-stu-id="56b6e-108">These options are added to the Visio workspace to help you interact with the data mining shape.</span></span> <span data-ttu-id="56b6e-109">根据所用挖掘模型的类型，选项可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="56b6e-109">The options are different depending on which type of data mining model you are using.</span></span>  
  
## <a name="build-a-cluster-diagram"></a><span data-ttu-id="56b6e-110">生成分类关系图</span><span class="sxs-lookup"><span data-stu-id="56b6e-110">Build a Cluster Diagram</span></span>  
 <span data-ttu-id="56b6e-111">本演练演示如何在 Visio 中生成和自定义分类关系图。</span><span class="sxs-lookup"><span data-stu-id="56b6e-111">This walkthrough demonstrates how to build and customize a clustering diagram in Visio.</span></span>  
  
 <span data-ttu-id="56b6e-112">要按照演练内容操作，您应有一个可用分类模型。</span><span class="sxs-lookup"><span data-stu-id="56b6e-112">To follow along, you should have a clustering model already available.</span></span> <span data-ttu-id="56b6e-113">如果没有模型，请使用[群集向导 &#40;Excel 的数据挖掘外接程序 "&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)向导，并使用示例工作簿中的定型数据集创建一个模型，并使用所有默认值。</span><span class="sxs-lookup"><span data-stu-id="56b6e-113">If you do not have a model, use the [Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) wizard and create a model using the Training data set in the sample workbook, using all the defaults.</span></span>  
  
#### <a name="use-the-cluster-visio-shape-wizard"></a><span data-ttu-id="56b6e-114">使用分类 Visio 形状向导</span><span class="sxs-lookup"><span data-stu-id="56b6e-114">Use the Cluster Visio Shape Wizard</span></span>  
  
1.  <span data-ttu-id="56b6e-115">如果在 "**形状**" 列表中看不到 " **Microsoft 数据挖掘形状**"，请单击 "**更多形状**"，选择 "**打开模具**"，然后从默认安装位置打开模板。</span><span class="sxs-lookup"><span data-stu-id="56b6e-115">If you do not see **Microsoft Data Mining Shapes** in the **Shapes** list, click **More Shapes**, select **Open Stencil**, and open the template from the default installation location.</span></span>  
  
     <span data-ttu-id="56b6e-116">\<drive>： \Program files\Microsoft SQL Server 2012 DM 外接程序</span><span class="sxs-lookup"><span data-stu-id="56b6e-116">\<drive>:\Program files\Microsoft SQL Server 2012 DM Add-Ins</span></span>  
  
2.  <span data-ttu-id="56b6e-117">将**群集**形状拖到页面上。</span><span class="sxs-lookup"><span data-stu-id="56b6e-117">Drag the **Cluster** shape onto the page.</span></span>  
  
3.  <span data-ttu-id="56b6e-118">在**群集 Visio 形状向导**的 "欢迎" 页上，单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="56b6e-118">On the welcome page of the **Cluster Visio Shape Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="56b6e-119">在**群集向导**的 "**选择数据源**" 页上，选择一个与 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器的连接，该服务器包含要显示的数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="56b6e-119">On the **Select a Data Source** page of the **Cluster Wizard**, choose a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that contains the data mining models you want to visualize.</span></span>  
  
5.  <span data-ttu-id="56b6e-120">选择适当的挖掘模型，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="56b6e-120">Select an appropriate mining model, and click **Next**.</span></span>  
  
     <span data-ttu-id="56b6e-121">若要确保选择聚类分析模型，请在 "**属性**" 窗格中查看说明。</span><span class="sxs-lookup"><span data-stu-id="56b6e-121">To make sure you choose a clustering model, review the description in the **Properties** pane.</span></span>  
  
6.  <span data-ttu-id="56b6e-122">如果连接成功，则在 "**分类关系图" 选项**的 "选项" 中，确定要包括在 Visio 演示中的分类关系图类型：</span><span class="sxs-lookup"><span data-stu-id="56b6e-122">If the connection is successful, on the page, **Options for cluster diagram**, you decide which type of cluster diagram to include in your Visio presentation:</span></span>  
  
     <span data-ttu-id="56b6e-123">**仅显示分类形状**</span><span class="sxs-lookup"><span data-stu-id="56b6e-123">**Show cluster shapes only**</span></span>  
     <span data-ttu-id="56b6e-124">此选项会创建一个简单的分类关系图，每个分类用一个矩形或您选择的其他形状表示。</span><span class="sxs-lookup"><span data-stu-id="56b6e-124">This option creates a simple cluster diagram, with each cluster represented by a rectangle or other shape you choose</span></span>  
  
     <span data-ttu-id="56b6e-125">**用特征图显示分类**</span><span class="sxs-lookup"><span data-stu-id="56b6e-125">**Show clusters with characteristics chart**</span></span>  
     <span data-ttu-id="56b6e-126">此选项会创建与上面相同的图表，但形状内是描述分类特征的直方图。</span><span class="sxs-lookup"><span data-stu-id="56b6e-126">This option creates the same chart as above, but inside the shapes are histograms that describe the characteristics of the cluster.</span></span>  
  
     <span data-ttu-id="56b6e-127">![Visio 中群集特征图的示例](media/dm13-visio-cluster-samplecharshape.gif "Visio 中群集特征图的示例")</span><span class="sxs-lookup"><span data-stu-id="56b6e-127">![Example of cluster characteristics chart in Visio](media/dm13-visio-cluster-samplecharshape.gif "Example of cluster characteristics chart in Visio")</span></span>  
  
     <span data-ttu-id="56b6e-128">**用对比图显示分类**</span><span class="sxs-lookup"><span data-stu-id="56b6e-128">**Show clusters with discrimination chart**</span></span>  
     <span data-ttu-id="56b6e-129">此选项会创建与分类关系图相同的图表，但它会列出将当前分类与其他分类区分开来的最明显的特征。</span><span class="sxs-lookup"><span data-stu-id="56b6e-129">This option creates the same chart as the cluster diagram, but instead lists the characteristics of the current cluster that most strongly distinguish it from other clusters.</span></span>  
  
     <span data-ttu-id="56b6e-130">在向导生成关系图后，您可以切换到其他图表类型，具体方法是右键单击某一分类并选择一种新的图表类型。</span><span class="sxs-lookup"><span data-stu-id="56b6e-130">You can switch to another chart type after the wizard has built the diagram, by right-clicking a cluster and selecting a new chart type.</span></span> <span data-ttu-id="56b6e-131">现在，选择选项 "**显示具有特征的分类" 图表**。</span><span class="sxs-lookup"><span data-stu-id="56b6e-131">For now, choose the option, **Show clusters with characteristics chart**.</span></span>  
  
7.  <span data-ttu-id="56b6e-132">保留该选项，**图表中的行数**为5。</span><span class="sxs-lookup"><span data-stu-id="56b6e-132">Leave the option, **Number of rows in the chart**, as 5.</span></span>  
  
     <span data-ttu-id="56b6e-133">此选项不会更改模型中的分类数;它只是限制可显示为每个分类的功能的属性数。</span><span class="sxs-lookup"><span data-stu-id="56b6e-133">This option doesn't change the number of clusters in the model; it simply limits the number of attributes that can be displayed as features of each cluster.</span></span>  
  
     <span data-ttu-id="56b6e-134">但是，此选项将作为图表数据的筛选器，因此不能再增加项的数量。</span><span class="sxs-lookup"><span data-stu-id="56b6e-134">However, the option acts as a filter on the chart data, so you can't increase the number of items later.</span></span>  
  
8.  <span data-ttu-id="56b6e-135">单击 **“高级”** 。</span><span class="sxs-lookup"><span data-stu-id="56b6e-135">Click **Advanced**.</span></span>  
  
     <span data-ttu-id="56b6e-136">在 "**群集选项**" 对话框中，您可以自定义在关系图中使用的形状的可视外观。</span><span class="sxs-lookup"><span data-stu-id="56b6e-136">The **Cluster Options** dialog box is where you customize the visual appearance of shapes used in the diagram.</span></span> <span data-ttu-id="56b6e-137">您可以更改图形中使用的颜色和用于分类的形状。</span><span class="sxs-lookup"><span data-stu-id="56b6e-137">You can change the colors used in the graph, and the shape used for clusters.</span></span>  
  
     <span data-ttu-id="56b6e-138">"**明暗度变量**" 控件在 Office 2013 中不起作用。</span><span class="sxs-lookup"><span data-stu-id="56b6e-138">The **Shading Variable** control does not work in Office 2013.</span></span>  
  
     <span data-ttu-id="56b6e-139">![单击“高级”以选择形状颜色](media/dm13-visio-clusteroptions-advanced.gif "单击“高级”以选择形状颜色")</span><span class="sxs-lookup"><span data-stu-id="56b6e-139">![click Advanced to choose shape colors](media/dm13-visio-clusteroptions-advanced.gif "click Advanced to choose shape colors")</span></span>  
  
     <span data-ttu-id="56b6e-140">**提示：** 稍后，可以使用 Visio 主题和形状编辑控件更改某些颜色。</span><span class="sxs-lookup"><span data-stu-id="56b6e-140">**Tip:** Some colors can be altered later by using Visio themes and shape editing controls.</span></span> <span data-ttu-id="56b6e-141">但是，Visio 主题还会覆盖这些颜色选择中的一部分，因此我们建议您从默认颜色开始，逐步应用更改。</span><span class="sxs-lookup"><span data-stu-id="56b6e-141">However, Visio themes will also override some of these color selections, so we recommend starting with the default colors and gradually applying changes.</span></span>  
  
9. <span data-ttu-id="56b6e-142">单击 "**完成**" 以创建关系图。</span><span class="sxs-lookup"><span data-stu-id="56b6e-142">Click **Finish** to create the graph.</span></span>  
  
     <span data-ttu-id="56b6e-143">向导将从数据挖掘模型中检索信息、呈现形状并使用属性和值填充每个分类。</span><span class="sxs-lookup"><span data-stu-id="56b6e-143">The wizard retrieves information from the data mining model, renders the shapes, and populates each cluster with attributes and values.</span></span>  
  
     <span data-ttu-id="56b6e-144">![依赖关系网络](media/dm13-visiodepnet-defaultgraph.gif "依赖关系网络")</span><span class="sxs-lookup"><span data-stu-id="56b6e-144">![a dependency network](media/dm13-visiodepnet-defaultgraph.gif "a dependency network")</span></span>  
  
## <a name="explore-and-modify-the-finished-diagram"></a><span data-ttu-id="56b6e-145">浏览和修改已完成的关系图</span><span class="sxs-lookup"><span data-stu-id="56b6e-145">Explore and Modify the Finished Diagram</span></span>  
 <span data-ttu-id="56b6e-146">完成关系图后，您可以继续使用 Visio 控件自定义外观，如下面示例所示。</span><span class="sxs-lookup"><span data-stu-id="56b6e-146">After the diagram is complete, you can continue to customize the appearance using the Visio controls, as shown in the following example.</span></span>  
  
 <span data-ttu-id="56b6e-147">![使用 Visio 自定义的群集关系图](media/dm13-visio-clustercomplete1.gif "使用 Visio 自定义的群集关系图")</span><span class="sxs-lookup"><span data-stu-id="56b6e-147">![cluster diagram customized using Visio](media/dm13-visio-clustercomplete1.gif "cluster diagram customized using Visio")</span></span>  
  
 <span data-ttu-id="56b6e-148">所有基本分类形状都由向导生成；使用以下工具可以对关系图进行升级和个性化设置：</span><span class="sxs-lookup"><span data-stu-id="56b6e-148">All of the basic cluster shapes are generated by the wizard; use the following tools to update and personalize the diagram:</span></span>  
  
1.  <span data-ttu-id="56b6e-149">拖动 "**群集选项**" 控件中的滑块，筛选出较弱的关系并简化关系图。</span><span class="sxs-lookup"><span data-stu-id="56b6e-149">Drag the slider in the **Cluster Options** control, to filter out weaker relationships and simplify the diagram.</span></span>  
  
2.  <span data-ttu-id="56b6e-150">使用 Visio "**重新布局页面**" 选项试验不同的群集布局。</span><span class="sxs-lookup"><span data-stu-id="56b6e-150">Use the Visio **Re-Layout Page** option to experiment with different cluster layouts.</span></span>  
  
3.  <span data-ttu-id="56b6e-151">使用 "**设计**" 选项卡上的 "**连接器**" 选项可以更改连接线样式，使线条不跨越分类。</span><span class="sxs-lookup"><span data-stu-id="56b6e-151">Use the **Connectors** option on the **Design** tab to change the connector style to keep lines from crossing over clusters.</span></span>  
  
4.  <span data-ttu-id="56b6e-152">单击 "**外接程序**" 功能区，然后显示用于处理数据挖掘关系图的自定义工具栏之一：</span><span class="sxs-lookup"><span data-stu-id="56b6e-152">Click the **Add-Ins** ribbon, and then display one of the custom toolbars used for working with data mining diagrams:</span></span>  
  
     <span data-ttu-id="56b6e-153">**布局**</span><span class="sxs-lookup"><span data-stu-id="56b6e-153">**Layout**</span></span>  
     <span data-ttu-id="56b6e-154">优化分类的排列以适合当前页。</span><span class="sxs-lookup"><span data-stu-id="56b6e-154">Optimizes the arrangement of clusters to fit in the current page.</span></span>  
  
     <span data-ttu-id="56b6e-155">**调整页大小**</span><span class="sxs-lookup"><span data-stu-id="56b6e-155">**Resize Page**</span></span>  
     <span data-ttu-id="56b6e-156">此控件适用于早期 HTML 版本。</span><span class="sxs-lookup"><span data-stu-id="56b6e-156">This control was intended for earlier HTML versions.</span></span> <span data-ttu-id="56b6e-157">请改用 Visio 页面大小调整控件。</span><span class="sxs-lookup"><span data-stu-id="56b6e-157">Use the Visio page resizing controls instead.</span></span>  
  
     <span data-ttu-id="56b6e-158">**说明**</span><span class="sxs-lookup"><span data-stu-id="56b6e-158">**Description**</span></span>  
     <span data-ttu-id="56b6e-159">选择一个分类后，单击此选项可显示有关该分类的详细信息。</span><span class="sxs-lookup"><span data-stu-id="56b6e-159">If a cluster is selected, click this option to display details about the cluster.</span></span>  
  
     <span data-ttu-id="56b6e-160">![单击“说明”以获取有关该群集的详细信息](media/dm13-visio-cluster-description-control.gif "单击“说明”以获取有关该群集的详细信息")</span><span class="sxs-lookup"><span data-stu-id="56b6e-160">![click Description to get details about the cluster](media/dm13-visio-cluster-description-control.gif "click Description to get details about the cluster")</span></span>  
  
     <span data-ttu-id="56b6e-161">**边缘强度**</span><span class="sxs-lookup"><span data-stu-id="56b6e-161">**Edge Strength**</span></span>  
     <span data-ttu-id="56b6e-162">在连接分类的线条上显示置信度得分。</span><span class="sxs-lookup"><span data-stu-id="56b6e-162">Displays confidence scores on the lines connecting clusters.</span></span>  
  
     <span data-ttu-id="56b6e-163">但是，如果您使用任意特殊格式而不是向导默认生成的格式，包括一些背景，这些数字可能不会显示。</span><span class="sxs-lookup"><span data-stu-id="56b6e-163">However, if you apply any special formatting other than the default generated by the wizard, including some backgrounds, these numbers might not be visible.</span></span>  
  
     <span data-ttu-id="56b6e-164">**滑块**</span><span class="sxs-lookup"><span data-stu-id="56b6e-164">**Slider**</span></span>  
     <span data-ttu-id="56b6e-165">筛选分类之间的线条。</span><span class="sxs-lookup"><span data-stu-id="56b6e-165">Filters the lines between clusters.</span></span> <span data-ttu-id="56b6e-166">向上移动滑块会删除最重要关联外的所有关联。</span><span class="sxs-lookup"><span data-stu-id="56b6e-166">Moving the slider up removes all but the most important associations.</span></span>  
  
     <span data-ttu-id="56b6e-167">**明暗度**</span><span class="sxs-lookup"><span data-stu-id="56b6e-167">**Shading**</span></span>  
     <span data-ttu-id="56b6e-168">此控件在 Office 2013 中不能使用。</span><span class="sxs-lookup"><span data-stu-id="56b6e-168">This control does not work in Office 2013.</span></span>  
  
5.  <span data-ttu-id="56b6e-169">使用 Visio "**视图**" 功能区的 "**任务窗格**" 区域中的 "**平移和缩放**" 控件，可以重点关注一组分类并四处移动关系图。</span><span class="sxs-lookup"><span data-stu-id="56b6e-169">Use the **Pan and Zoom** control, in the **Task Pane** area of the Visio **View** ribbon, to focus on a set of clusters and move around the diagram.</span></span>  
  
6.  <span data-ttu-id="56b6e-170">右键单击任意分类可查看分类形状的特定选项：</span><span class="sxs-lookup"><span data-stu-id="56b6e-170">Right-click any cluster to see options specific to the cluster shape:</span></span>  
  
    -   <span data-ttu-id="56b6e-171">更改图表样式。</span><span class="sxs-lookup"><span data-stu-id="56b6e-171">Change the chart style.</span></span>  
  
    -   <span data-ttu-id="56b6e-172">添加分类特征图。</span><span class="sxs-lookup"><span data-stu-id="56b6e-172">Add a cluster characteristics chart.</span></span>  
  
    -   <span data-ttu-id="56b6e-173">添加分类对比图。</span><span class="sxs-lookup"><span data-stu-id="56b6e-173">Add a cluster discrimination chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56b6e-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56b6e-174">See Also</span></span>  
 [<span data-ttu-id="56b6e-175">解决 Visio 数据挖掘关系图 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="56b6e-175">Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;</span></span>](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
