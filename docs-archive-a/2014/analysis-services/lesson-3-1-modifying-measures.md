---
title: 修改度量值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7bd48810-15ce-45ff-862b-372d08606995
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd352cbca1d21f5842e075d9cb8e5e766aa369b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589334"
---
# <a name="modifying-measures"></a><span data-ttu-id="6a701-102">修改度量值</span><span class="sxs-lookup"><span data-stu-id="6a701-102">Modifying Measures</span></span>
  <span data-ttu-id="6a701-103">可以使用“FormatString”\*\*\*\* 属性定义控制如何向用户显示度量值的格式设置。</span><span class="sxs-lookup"><span data-stu-id="6a701-103">You can use the **FormatString** property to define formatting settings that control how measures are displayed to users.</span></span> <span data-ttu-id="6a701-104">在此任务中，您将为 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集中的货币和百分比度量值指定格式设置属性。</span><span class="sxs-lookup"><span data-stu-id="6a701-104">In this task, you specify formatting properties for the currency and percentage measures in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
### <a name="to-modify-the-measures-of-the-cube"></a><span data-ttu-id="6a701-105">修改多维数据集的度量值</span><span class="sxs-lookup"><span data-stu-id="6a701-105">To modify the measures of the cube</span></span>  
  
1.  <span data-ttu-id="6a701-106">切换到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器的“多维数据集结构”\*\*\*\* 选项卡，然后在“度量值”\*\*\*\* 窗格中展开“Internet Sales”\*\*\*\* 度量值组，右键单击“订单数量”\*\*\*\*，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6a701-106">Switch to the **Cube Structure** tab of Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, expand the **Internet Sales** measure group in the **Measures** pane, right-click **Order Quantity**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6a701-107">在“属性”窗口中，单击“自动隐藏”\*\*\*\* 图钉图标使“属性”窗口保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="6a701-107">In the Properties window, click the **Auto Hide** pushpin icon to pin the Properties window open.</span></span>  
  
     <span data-ttu-id="6a701-108">当“属性”窗口处于打开状态时，同时更改多维数据集中多个项的属性将更加容易。</span><span class="sxs-lookup"><span data-stu-id="6a701-108">It is easier to change properties for several items in the cube when the Properties window remains open.</span></span>  
  
3.  <span data-ttu-id="6a701-109">在“属性”窗口中单击“FormatString”\*\*\*\* 列表，然后键入 **#,#**。</span><span class="sxs-lookup"><span data-stu-id="6a701-109">In the Properties window, click the **FormatString** list, and then type **#,#**.</span></span>  
  
4.  <span data-ttu-id="6a701-110">在“多维数据集结构”\*\*\*\* 选项卡的工具栏上，单击左侧的“显示度量值网格”\*\*\*\* 图标。</span><span class="sxs-lookup"><span data-stu-id="6a701-110">On the toolbar of the **Cube Structure** tab, click the **Show Measures Grid** icon on the left.</span></span>  
  
     <span data-ttu-id="6a701-111">通过网格视图，您可以同时选择多个度量值。</span><span class="sxs-lookup"><span data-stu-id="6a701-111">The grid view lets you select multiple measures at the same time.</span></span>  
  
5.  <span data-ttu-id="6a701-112">选择下列度量值之一：</span><span class="sxs-lookup"><span data-stu-id="6a701-112">Select the following measures.</span></span> <span data-ttu-id="6a701-113">可以通过在按住 Ctrl 键的同时单击各个度量值的方式来选择多个度量值：</span><span class="sxs-lookup"><span data-stu-id="6a701-113">You can select multiple measures by clicking each while holding down the CTRL key:</span></span>  
  
    -   <span data-ttu-id="6a701-114">**Unit Price**</span><span class="sxs-lookup"><span data-stu-id="6a701-114">**Unit Price**</span></span>  
  
    -   <span data-ttu-id="6a701-115">**Extended Amount**</span><span class="sxs-lookup"><span data-stu-id="6a701-115">**Extended Amount**</span></span>  
  
    -   <span data-ttu-id="6a701-116">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="6a701-116">**Discount Amount**</span></span>  
  
    -   <span data-ttu-id="6a701-117">**Product Standard Cost**</span><span class="sxs-lookup"><span data-stu-id="6a701-117">**Product Standard Cost**</span></span>  
  
    -   <span data-ttu-id="6a701-118">**Total Product Cost**</span><span class="sxs-lookup"><span data-stu-id="6a701-118">**Total Product Cost**</span></span>  
  
    -   <span data-ttu-id="6a701-119">**Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="6a701-119">**Sales Amount**</span></span>  
  
    -   <span data-ttu-id="6a701-120">**税额**</span><span class="sxs-lookup"><span data-stu-id="6a701-120">**Tax Amt**</span></span>  
  
    -   <span data-ttu-id="6a701-121">**Freight**</span><span class="sxs-lookup"><span data-stu-id="6a701-121">**Freight**</span></span>  
  
6.  <span data-ttu-id="6a701-122">在“属性”窗口的“FormatString”\*\*\*\* 列表中，选择“Currency”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6a701-122">In the Properties window, in the **FormatString** list, select **Currency**.</span></span>  
  
7.  <span data-ttu-id="6a701-123">在“属性”窗口顶部（标题栏正下方）的下拉列表中，选择“Unit Price Discount Pct”\*\*\*\* 度量值，然后在“FormatString”\*\*\*\* 列表中选择“Percent”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6a701-123">In the drop-down list at the top of the Properties window (right below the title bar), select the measure **Unit Price Discount Pct**, and then select **Percent** in the **FormatString** list.</span></span>  
  
8.  <span data-ttu-id="6a701-124">在属性窗口中，将 "**单价折扣 Pct** " 度量值的 "**名称**" 属性更改为 `Unit Price Discount Percentage` 。</span><span class="sxs-lookup"><span data-stu-id="6a701-124">In the Properties window, change the **Name** property for the **Unit Price Discount Pct** measure to `Unit Price Discount Percentage`.</span></span>  
  
9. <span data-ttu-id="6a701-125">在 "**度量值**" 窗格中，单击 "**税金 Amt** "，然后将此度量值的名称更改为 `Tax Amount` 。</span><span class="sxs-lookup"><span data-stu-id="6a701-125">In the **Measures** pane, click **Tax Amt** and change the name of this measure to `Tax Amount`.</span></span>  
  
10. <span data-ttu-id="6a701-126">在“属性”窗口中，单击“自动隐藏”\*\*\*\* 图标隐藏“属性”窗口，然后在“多维数据集结构”\*\*\*\* 选项卡的工具栏上单击“显示度量值树”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6a701-126">In the Properties window, click the **Auto Hide** icon to hide the Properties window, and then click **Show Measures Tree** on the toolbar of the **Cube Structure** tab.</span></span>  
  
11. <span data-ttu-id="6a701-127">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="6a701-127">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6a701-128">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="6a701-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6a701-129">修改“客户”维度</span><span class="sxs-lookup"><span data-stu-id="6a701-129">Modifying the Customer Dimension</span></span>](lesson-3-2-modifying-the-customer-dimension.md)  
  
## <a name="see-also"></a><span data-ttu-id="6a701-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a701-130">See Also</span></span>  
 <span data-ttu-id="6a701-131">[定义数据库维度](multidimensional-models/define-database-dimensions.md) </span><span class="sxs-lookup"><span data-stu-id="6a701-131">[Define Database Dimensions](multidimensional-models/define-database-dimensions.md) </span></span>  
 [<span data-ttu-id="6a701-132">配置度量值属性</span><span class="sxs-lookup"><span data-stu-id="6a701-132">Configure Measure Properties</span></span>](multidimensional-models/configure-measure-properties.md)  
  
  
