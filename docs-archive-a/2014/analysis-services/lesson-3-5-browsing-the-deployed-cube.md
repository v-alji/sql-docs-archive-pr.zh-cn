---
title: 浏览部署的多维数据集 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 849c6109-1453-4fe4-a892-c49a982cfadb
author: minewiskan
ms.author: owend
ms.openlocfilehash: b876c8b2876aaf4ad28b0f4ea3fb8bab32cd787b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588129"
---
# <a name="browsing-the-deployed-cube"></a><span data-ttu-id="3db7b-102">浏览已部署的多维数据集</span><span class="sxs-lookup"><span data-stu-id="3db7b-102">Browsing the Deployed Cube</span></span>
  <span data-ttu-id="3db7b-103">在下面的任务中，将浏览 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="3db7b-103">In the following task, you browse the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="3db7b-104">因为我们的分析将比较多个维度的度量值，所以，您将使用 Excel 数据透视表来浏览您的数据。</span><span class="sxs-lookup"><span data-stu-id="3db7b-104">Because our analysis compares measure across multiple dimensions, you will use an Excel PivotTable to browse your data.</span></span> <span data-ttu-id="3db7b-105">使用数据透视表使您可以将客户、日期和产品信息放置于不同的轴上，这样，您可以在查看时看到在特定的时间段、客户人口统计信息和产品系列上 Internet 销售是如何变化的。</span><span class="sxs-lookup"><span data-stu-id="3db7b-105">Using a PivotTable lets you place customer, date, and product information on different axes so that you can see how Internet Sales change when viewed across specific time periods, customer demographics, and product lines.</span></span>  
  
### <a name="to-browse-the-deployed-cube"></a><span data-ttu-id="3db7b-106">浏览部署的多维数据集</span><span class="sxs-lookup"><span data-stu-id="3db7b-106">To browse the deployed cube</span></span>  
  
1.  <span data-ttu-id="3db7b-107">若要切换到中的多维数据集设计器 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] ，请双击解决方案资源管理器**Cubes**的 cube 文件夹中的 " \*\* [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程\*\*" 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="3db7b-107">To switch to Cube Designer in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], double-click the **[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial** cube in the **Cubes** folder of the Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="3db7b-108">打开“浏览器”\*\*\*\* 选项卡，然后单击设计器工具栏上的“重新连接”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="3db7b-108">Open the **Browser** tab, and then click the **Reconnect** button on the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="3db7b-109">单击 Excel 图标，以便使用工作区数据库作为数据源来启动 Excel。</span><span class="sxs-lookup"><span data-stu-id="3db7b-109">Click the Excel icon to launch Excel using the workspace database as the data source.</span></span> <span data-ttu-id="3db7b-110">系统提示启用连接时，单击“启用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3db7b-110">When prompted to enable connections, click **Enable**.</span></span>  
  
4.  <span data-ttu-id="3db7b-111">在数据透视表字段列表中，展开“Internet 销售”\*\*\*\*，然后将“销售额”\*\*\*\* 度量值添加到“值”\*\*\*\* 区域。</span><span class="sxs-lookup"><span data-stu-id="3db7b-111">In the PivotTable Field List, expand **Internet Sales**, and then drag the **Sales Amount** measure to the **Values** area.</span></span>  
  
5.  <span data-ttu-id="3db7b-112">在数据透视表字段列表中，展开“产品”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3db7b-112">In the PivotTable Field List, expand **Product**.</span></span>  
  
6.  <span data-ttu-id="3db7b-113">将“产品型号系列”\*\*\*\* 用户层次结构拖到“列”\*\*\*\* 区域。</span><span class="sxs-lookup"><span data-stu-id="3db7b-113">Drag the **Product Model Lines** user hierarchy to the **Columns** area.</span></span>  
  
7.  <span data-ttu-id="3db7b-114">在数据透视表字段列表中，依次展开“客户”\*\*\*\* 和“位置”\*\*\*\*，然后将“客户所在地域”\*\*\*\* 层次结构从“客户”维度中的“位置”显示文件夹拖到“行”\*\*\*\* 区域。</span><span class="sxs-lookup"><span data-stu-id="3db7b-114">In the PivotTable Field List, expand **Customer**, expand **Location**, and then drag the **Customer Geography** hierarchy from the Location display folder in the Customer dimension to the **Rows** area.</span></span>  
  
8.  <span data-ttu-id="3db7b-115">在数据透视表字段列表中，展开“订单日期”\*\*\*\*，然后将“Order Date.Calendar Date”\*\*\*\* 层次结构拖到“报表筛选器”\*\*\*\* 区域。</span><span class="sxs-lookup"><span data-stu-id="3db7b-115">In the PivotTable Field List, expand **Order Date**, and then drag the **Order Date.Calendar Date** hierarchy to the **Report Filter** area.</span></span>  
  
9. <span data-ttu-id="3db7b-116">在数据窗格中，单击“Order Date.Calendar Date”\*\*\*\* 筛选器右边的箭头，清除“(全部)”\*\*\*\* 级别的复选框，依次展开“2006”\*\*\*\*、“H1 CY 2006”\*\*\*\* 和“Q1 CY 2006”\*\*\*\*，选中“2006 年 2 月”\*\*\*\* 的复选框，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3db7b-116">Click the arrow to the right of the **Order Date.Calendar Date** filter in the data pane, clear the check box for the **(All)** level, expand **2006**, expand **H1 CY 2006**, expand **Q1 CY 2006**, select the check box for **February 2006**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="3db7b-117">此时会按区域和产品系列显示 2006 年 2 月份的 Internet 销售，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="3db7b-117">Internet sales by region and product line for the month of February, 2006 appear as shown in the following image.</span></span>  
  
     <span data-ttu-id="3db7b-118">![按区域和产品系列划分的“Internet 销售”](../../2014/tutorials/media/l3-cube-browser-finish.gif "按区域和产品系列划分的“Internet 销售”")</span><span class="sxs-lookup"><span data-stu-id="3db7b-118">![Internet sales by region and product line](../../2014/tutorials/media/l3-cube-browser-finish.gif "Internet sales by region and product line")</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="3db7b-119">下一课</span><span class="sxs-lookup"><span data-stu-id="3db7b-119">Next Lesson</span></span>  
 [<span data-ttu-id="3db7b-120">第 4 课：定义高级属性和维度属性</span><span class="sxs-lookup"><span data-stu-id="3db7b-120">Lesson 4: Defining Advanced Attribute and Dimension Properties</span></span>](lesson-4-defining-advanced-attribute-and-dimension-properties.md)  
  
  
