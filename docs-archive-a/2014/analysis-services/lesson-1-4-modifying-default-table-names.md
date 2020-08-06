---
title: 修改默认表名 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ddd97483-a76d-43c1-8b40-fc7cc57fb0c2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 254f797be95f60211983400b019415431d4cf39c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577044"
---
# <a name="modifying-default-table-names"></a><span data-ttu-id="03200-102">修改默认表名</span><span class="sxs-lookup"><span data-stu-id="03200-102">Modifying Default Table Names</span></span>
  <span data-ttu-id="03200-103">可以在数据源视图中更改 **FriendlyName** 属性的值，以使它们更易于受人关注和使用。</span><span class="sxs-lookup"><span data-stu-id="03200-103">You can change the value of the **FriendlyName** property for objects in the data source view to make them easier to notice and use.</span></span>  
  
 <span data-ttu-id="03200-104">在下面的任务中，将从数据源视图中的每个表中删除“**Dim**”和“**Fact**”前缀来更改这些表的友好名称。</span><span class="sxs-lookup"><span data-stu-id="03200-104">In the following task, you will change the friendly name of each table in the data source view by removing the "**Dim**" and "**Fact**" prefixes from these tables.</span></span> <span data-ttu-id="03200-105">这会使将在下一课程中定义的多维数据集和维度对象变得更易于受人关注和使用。</span><span class="sxs-lookup"><span data-stu-id="03200-105">This will make the cube and dimension objects (that you will define in the next lesson) easier to notice and use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03200-106">此外，还可以更改列的友好名称，定义计算列，以及联接数据源视图中的表或视图以使其变得更易于使用。</span><span class="sxs-lookup"><span data-stu-id="03200-106">You can also change the friendly names of columns, define calculated columns, and join tables or views in the data source view to make them easier to use.</span></span>  
  
### <a name="to-modify-the-default-name-of-a-table"></a><span data-ttu-id="03200-107">修改表的默认名称</span><span class="sxs-lookup"><span data-stu-id="03200-107">To modify the default name of a table</span></span>  
  
1.  <span data-ttu-id="03200-108">在“数据源视图设计器”\*\*\*\* 的“表”\*\*\*\* 窗格中右键单击 **FactInternetSales** 表，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03200-108">In the **Tables** pane of **Data Source View Designer**, right-click the **FactInternetSales** table, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="03200-109">如果在 Microsoft Visual Studio 窗口的右侧未显示“属性”窗口，则单击“属性”窗口的标题栏上的“自动隐藏”\*\*\*\* 按钮，以便该窗口保持可见状态。</span><span class="sxs-lookup"><span data-stu-id="03200-109">If the Properties window on the right side of the Microsoft Visual Studio window is not displayed, click the **Auto Hide** button on the title bar of the Properties window so that this window remains visible.</span></span>  
  
     <span data-ttu-id="03200-110">在“属性”窗口保持打开状态时，更容易更改数据源视图中各个表的属性。</span><span class="sxs-lookup"><span data-stu-id="03200-110">It is easier to change the properties for each table in the data source view when the Properties window remains open.</span></span> <span data-ttu-id="03200-111">如果不使用“自动隐藏”\*\*\*\* 按钮使窗口保持打开状态，则在“关系图”\*\*\*\* 窗格中单击其他对象时，该窗口将会关闭。</span><span class="sxs-lookup"><span data-stu-id="03200-111">If you do not pin the window open by using the **Auto Hide** button, the window will close when you click a different object in the **Diagram** pane.</span></span>  
  
3.  <span data-ttu-id="03200-112">将**FactInternetSales**对象的**FriendlyName**属性更改为 *`InternetSales`* 。</span><span class="sxs-lookup"><span data-stu-id="03200-112">Change the **FriendlyName** property for the **FactInternetSales** object to *`InternetSales`*.</span></span>  
  
     <span data-ttu-id="03200-113">如果在 **FriendlyName** 属性单元格外单击，则应用此更改。</span><span class="sxs-lookup"><span data-stu-id="03200-113">When you click away from the cell for the **FriendlyName** property, the change is applied.</span></span> <span data-ttu-id="03200-114">在下一课中，将定义一个基于该事实数据表的度量值组。</span><span class="sxs-lookup"><span data-stu-id="03200-114">In the next lesson, you will define a measure group that is based on this fact table.</span></span> <span data-ttu-id="03200-115">由于您在本课中进行了更改，因此该事实数据表的名称将为 InternetSales，而不是 FactInternetSales。</span><span class="sxs-lookup"><span data-stu-id="03200-115">The name of the fact table will be InternetSales instead of FactInternetSales because of the change you made in this lesson.</span></span>  
  
4.  <span data-ttu-id="03200-116">在“表”\*\*\*\* 窗格中单击 **DimProduct**。</span><span class="sxs-lookup"><span data-stu-id="03200-116">Click **DimProduct** in the **Tables** pane.</span></span> <span data-ttu-id="03200-117">在属性窗口中，将**FriendlyName**属性更改为 *`Product`* 。</span><span class="sxs-lookup"><span data-stu-id="03200-117">In the Properties window, change the **FriendlyName** property to *`Product`*.</span></span>  
  
5.  <span data-ttu-id="03200-118">使用同样的方法更改数据源视图中剩余的各个表的 **FriendlyName** 属性，删除“**Dim**”前缀。</span><span class="sxs-lookup"><span data-stu-id="03200-118">Change the **FriendlyName** property of each remaining table in the data source view in the same way, to remove the "**Dim**" prefix.</span></span>  
  
6.  <span data-ttu-id="03200-119">完成更改后，单击“自动隐藏”\*\*\*\* 按钮，重新隐藏“属性”窗口。</span><span class="sxs-lookup"><span data-stu-id="03200-119">When you have finished, click the **Auto Hide** button to hide the Properties window again.</span></span>  
  
7.  <span data-ttu-id="03200-120">在“文件”\*\*\*\* 菜单上，或者在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的工具栏上，单击“全部保存”\*\*\*\*，以保存截至目前已在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 项目中进行的更改。</span><span class="sxs-lookup"><span data-stu-id="03200-120">On the **File** menu, or on the toolbar of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Save All** to save the changes you have made to this point in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span> <span data-ttu-id="03200-121">您可以根据需要在此处停止教程学习，并在以后继续。</span><span class="sxs-lookup"><span data-stu-id="03200-121">You can stop the tutorial here if you want and resume it later.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="03200-122">下一课</span><span class="sxs-lookup"><span data-stu-id="03200-122">Next Lesson</span></span>  
 [<span data-ttu-id="03200-123">第 2 课：定义和部署多维数据集</span><span class="sxs-lookup"><span data-stu-id="03200-123">Lesson 2: Defining and Deploying a Cube</span></span>](lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="03200-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03200-124">See Also</span></span>  
 <span data-ttu-id="03200-125">[多维模型中的数据源视图](multidimensional-models/data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="03200-125">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="03200-126">在数据源视图中更改属性 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="03200-126">Change Properties in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)  
  
  
