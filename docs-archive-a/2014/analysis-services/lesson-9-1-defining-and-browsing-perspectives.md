---
title: 定义和浏览透视 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 766004b9-6578-4914-a445-6f44843a5fb0
author: minewiskan
ms.author: owend
ms.openlocfilehash: c9658098180618c2d5d6d6d9e00e7a7e4a6c4231
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690848"
---
# <a name="defining-and-browsing-perspectives"></a><span data-ttu-id="c6720-102">定义和浏览透视</span><span class="sxs-lookup"><span data-stu-id="c6720-102">Defining and Browsing Perspectives</span></span>
  <span data-ttu-id="c6720-103">透视可以出于特定目的简化多维数据集的视图。</span><span class="sxs-lookup"><span data-stu-id="c6720-103">A perspective can simplify the view of a cube for specific purposes.</span></span> <span data-ttu-id="c6720-104">默认情况下，用户可以查看多维数据集内对其具有查看权限的所有元素。</span><span class="sxs-lookup"><span data-stu-id="c6720-104">By default, users can see all of the elements in a cube to which they have permissions.</span></span> <span data-ttu-id="c6720-105">用户查看整个 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多维数据集时所看到的内容是该多维数据集的默认透视。</span><span class="sxs-lookup"><span data-stu-id="c6720-105">What users are viewing when they view an entire [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube is the default perspective for the cube.</span></span> <span data-ttu-id="c6720-106">对于导航视图的用户，尤其对于只需与多维数据集的一小部分交互就能满足其商业智能和报表需求的用户来说，整个多维数据集的视图将是非常复杂的。</span><span class="sxs-lookup"><span data-stu-id="c6720-106">A view of the whole cube can be very complex for users to navigate, especially for users who only need to interact with a small part of the cube to satisfy their business intelligence and reporting requirements.</span></span>  
  
 <span data-ttu-id="c6720-107">若要降低多维数据集明显的复杂性，可以创建多维数据集的可查看子集，这称为“透视”\*\*，透视可以只向用户显示多维数据集内的度量值组、度量值、维度、属性、层次结构、关键绩效指标 (KPI)、操作和计算成员的一部分。</span><span class="sxs-lookup"><span data-stu-id="c6720-107">To reduce the apparent complexity of a cube, you can create viewable subsets of the cube, called *perspectives*, which show users only a part of the measure groups, measures, dimensions, attributes, hierarchies, Key Performance Indicators (KPIs), actions, and calculated members in the cube.</span></span> <span data-ttu-id="c6720-108">在使用针对以前版本的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]编写的客户端应用程序时，这种做法可能特别有用。</span><span class="sxs-lookup"><span data-stu-id="c6720-108">This can be particularly useful for working with client applications that were written for a previous release of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="c6720-109">例如，这些客户端不具有显示文件夹或透视的概念，但对于较早的客户端，透视的显示方式类似于多维数据集。</span><span class="sxs-lookup"><span data-stu-id="c6720-109">These clients have no concept of display folders or perspectives, for example, but a perspective appears to older clients as if it were a cube.</span></span> <span data-ttu-id="c6720-110">有关详细信息，请参阅 [透视](multidimensional-models-olap-logical-cube-objects/perspectives.md)和 [多维模型中的透视](multidimensional-models/perspectives-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="c6720-110">For more information, see [Perspectives](multidimensional-models-olap-logical-cube-objects/perspectives.md), and [Perspectives in Multidimensional Models](multidimensional-models/perspectives-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c6720-111">透视不是安全机制，而是用于提供更好用户体验的工具。</span><span class="sxs-lookup"><span data-stu-id="c6720-111">A perspective is not a security mechanism, but instead is a tool for providing a better user experience.</span></span> <span data-ttu-id="c6720-112">透视的所有安全性都从基础多维数据集继承。</span><span class="sxs-lookup"><span data-stu-id="c6720-112">All security for a perspective is inherited from the underlying cube.</span></span>  
  
 <span data-ttu-id="c6720-113">在此主题的任务中，将定义几个不同透视，然后通过每个新透视来浏览多维数据集。</span><span class="sxs-lookup"><span data-stu-id="c6720-113">In the tasks in this topic, you will define several different perspectives and then browse the cube through each of these new perspectives.</span></span>  
  
## <a name="defining-an-internet-sales-perspective"></a><span data-ttu-id="c6720-114">定义“Internet 销售”透视</span><span class="sxs-lookup"><span data-stu-id="c6720-114">Defining an Internet Sales Perspective</span></span>  
  
1.  <span data-ttu-id="c6720-115">打开 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器，然后单击“透视”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c6720-115">Open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Perspectives** tab.</span></span>  
  
     <span data-ttu-id="c6720-116">所有对象和它们的对象类型都将出现在“透视”\*\*\*\* 窗格中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="c6720-116">All the objects and their object types appear in the **Perspectives** pane, as shown in the following image.</span></span>  
  
     <span data-ttu-id="c6720-117">![多维数据集设计器的“透视”窗格](../../2014/tutorials/media/l9-perspectives-1.gif "多维数据集设计器的“透视”窗格")</span><span class="sxs-lookup"><span data-stu-id="c6720-117">![Perspectives pane of Cube Designer](../../2014/tutorials/media/l9-perspectives-1.gif "Perspectives pane of Cube Designer")</span></span>  
  
2.  <span data-ttu-id="c6720-118">在“透视”\*\*\*\* 选项卡的工具栏上，单击“新建透视”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="c6720-118">On the toolbar of the **Perspectives** tab, click the **New Perspective** button.</span></span>  
  
     <span data-ttu-id="c6720-119">新透视将显示在“透视名称”\*\*\*\* 列中，其默认名称为“透视”\*\*\*\*，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="c6720-119">A new perspective appears in the **Perspective Name** column with a default name of **Perspective**, as shown in the following image.</span></span> <span data-ttu-id="c6720-120">注意，每个对象的复选框均已选中；除非您清除了对象的复选框，否则此透视与此多维数据集的默认透视是相同的。</span><span class="sxs-lookup"><span data-stu-id="c6720-120">Notice that the check box for every object is selected; until you clear the check box for an object, this perspective is identical to the default perspective of this cube.</span></span>  
  
     <span data-ttu-id="c6720-121">![“透视名称”列中的新建透视](../../2014/tutorials/media/l9-perspectives-2.gif "“透视名称”列中的新建透视")</span><span class="sxs-lookup"><span data-stu-id="c6720-121">![New perspective in Perspective Name column](../../2014/tutorials/media/l9-perspectives-2.gif "New perspective in Perspective Name column")</span></span>  
  
3.  <span data-ttu-id="c6720-122">将透视名称更改为 `Internet Sales` 。</span><span class="sxs-lookup"><span data-stu-id="c6720-122">Change the perspective name to `Internet Sales`.</span></span>  
  
4.  <span data-ttu-id="c6720-123">在下一行中，将 DefaultMeasure 设置为“Internet 销售额”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6720-123">On the next row, set the DefaultMeasure to **Internet Sales-Sales Amount**.</span></span>  
  
     <span data-ttu-id="c6720-124">当用户通过使用此透视来浏览多维数据集时，此度量值将是用户所看到的度量值（除非指定了其他度量值）。</span><span class="sxs-lookup"><span data-stu-id="c6720-124">When users browse the cube by using this perspective, this will be the measure that the users see unless they specify some other measure.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c6720-125">还可以在多维数据集的“多维数据集结构”\*\*\*\* 选项卡上的“属性”窗口中，为整个 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集设置默认度量值。</span><span class="sxs-lookup"><span data-stu-id="c6720-125">You can also set the default measure for the whole [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube in the Properties window on the **Cube Structure** tab for the cube.</span></span>  
  
5.  <span data-ttu-id="c6720-126">请清除下列对象的复选框：</span><span class="sxs-lookup"><span data-stu-id="c6720-126">Clear the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="c6720-127">`Reseller Sales`度量值组</span><span class="sxs-lookup"><span data-stu-id="c6720-127">`Reseller Sales` measure group</span></span>  
  
    -   <span data-ttu-id="c6720-128">“销售配额”\*\*\*\* 度量值组</span><span class="sxs-lookup"><span data-stu-id="c6720-128">**Sales Quotas** measure group</span></span>  
  
    -   <span data-ttu-id="c6720-129">“销售配额 1”\*\*\*\* 度量值组</span><span class="sxs-lookup"><span data-stu-id="c6720-129">**Sales Quotas 1** measure group</span></span>  
  
    -   <span data-ttu-id="c6720-130">“分销商”\*\*\*\* 多维数据集维度</span><span class="sxs-lookup"><span data-stu-id="c6720-130">**Reseller** cube dimension</span></span>  
  
    -   <span data-ttu-id="c6720-131">“分销商所在地域”\*\*\*\* 多维数据集维度</span><span class="sxs-lookup"><span data-stu-id="c6720-131">**Reseller Geography** cube dimension</span></span>  
  
    -   <span data-ttu-id="c6720-132">“销售区域”\*\*\*\* 多维数据集维度</span><span class="sxs-lookup"><span data-stu-id="c6720-132">**Sales Territory** cube dimension</span></span>  
  
    -   <span data-ttu-id="c6720-133">“雇员”\*\*\*\* 多维数据集维度</span><span class="sxs-lookup"><span data-stu-id="c6720-133">**Employee** cube dimension</span></span>  
  
    -   <span data-ttu-id="c6720-134">“促销”\*\*\*\* 多维数据集维度</span><span class="sxs-lookup"><span data-stu-id="c6720-134">**Promotion** cube dimension</span></span>  
  
    -   <span data-ttu-id="c6720-135">“分销商收入”\*\*\*\* KPI</span><span class="sxs-lookup"><span data-stu-id="c6720-135">**Reseller Revenue** KPI</span></span>  
  
    -   <span data-ttu-id="c6720-136">“大型分销商”\*\*\*\* 命名集</span><span class="sxs-lookup"><span data-stu-id="c6720-136">**Large Resellers** named set</span></span>  
  
    -   <span data-ttu-id="c6720-137">“总销售额”\*\*\*\* 计算成员</span><span class="sxs-lookup"><span data-stu-id="c6720-137">**Total Sales Amount** calculated member</span></span>  
  
    -   <span data-ttu-id="c6720-138">“总产品成本”\*\*\*\* 计算成员</span><span class="sxs-lookup"><span data-stu-id="c6720-138">**Total Product Cost** calculated member</span></span>  
  
    -   <span data-ttu-id="c6720-139">“分销商 GPM”\*\*\*\* 计算成员</span><span class="sxs-lookup"><span data-stu-id="c6720-139">**Reseller GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="c6720-140">“总 GPM”\*\*\*\* 计算成员</span><span class="sxs-lookup"><span data-stu-id="c6720-140">**Total GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="c6720-141">“所有产品的分销商销售额比率”\*\*\*\* 计算成员</span><span class="sxs-lookup"><span data-stu-id="c6720-141">**Reseller Sales Ratio to All Products** calculated member</span></span>  
  
    -   <span data-ttu-id="c6720-142">“所有产品的总销售额比率”\*\*\*\* 计算成员</span><span class="sxs-lookup"><span data-stu-id="c6720-142">**Total Sales Ratio to All Products** calculated member</span></span>  
  
     <span data-ttu-id="c6720-143">这些对象与“Internet 销售”无关。</span><span class="sxs-lookup"><span data-stu-id="c6720-143">These objects do not relate to Internet sales.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c6720-144">在每个维度中，还可以单独选择希望出现在透视中的用户定义层次结构和属性。</span><span class="sxs-lookup"><span data-stu-id="c6720-144">Within each dimension, you can also individually select the user-defined hierarchies and attributes that you want to appear in a perspective.</span></span>  
  
## <a name="defining-a-reseller-sales-perspective"></a><span data-ttu-id="c6720-145">定义“分销商销售”透视</span><span class="sxs-lookup"><span data-stu-id="c6720-145">Defining a Reseller Sales Perspective</span></span>  
  
1.  <span data-ttu-id="c6720-146">在“透视”\*\*\*\* 选项卡的工具栏上，单击“新建透视”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="c6720-146">On the toolbar of the **Perspectives** tab, click the **New Perspective** button.</span></span>  
  
2.  <span data-ttu-id="c6720-147">将新透视的名称更改为 `Reseller Sales` 。</span><span class="sxs-lookup"><span data-stu-id="c6720-147">Change the name of the new perspective to `Reseller Sales`.</span></span>  
  
3.  <span data-ttu-id="c6720-148">将“分销商销售额”\*\*\*\* 设置为默认度量值。</span><span class="sxs-lookup"><span data-stu-id="c6720-148">Set **Reseller Sales-Sales Amount** as the default measure.</span></span>  
  
     <span data-ttu-id="c6720-149">当用户通过使用此透视来浏览多维数据集时，此度量值将是用户所看到的度量值（除非指定了其他度量值）。</span><span class="sxs-lookup"><span data-stu-id="c6720-149">When users browse the cube by using this perspective, this measure will be the measure that the users will see unless they specify some other measure.</span></span>  
  
4.  <span data-ttu-id="c6720-150">请清除下列对象的复选框：</span><span class="sxs-lookup"><span data-stu-id="c6720-150">Clear the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="c6720-151">`Internet Sales`度量值组</span><span class="sxs-lookup"><span data-stu-id="c6720-151">`Internet Sales` measure group</span></span>  
  
    -   <span data-ttu-id="c6720-152">“Internet 销售原因”\*\*\*\* 度量值组</span><span class="sxs-lookup"><span data-stu-id="c6720-152">**Internet Sales Reason** measure group</span></span>  
  
    -   <span data-ttu-id="c6720-153">“客户”\*\*\*\* 多维数据集维度</span><span class="sxs-lookup"><span data-stu-id="c6720-153">**Customer** cube dimension</span></span>  
  
    -   <span data-ttu-id="c6720-154">“Internet 销售订单详细信息”\*\*\*\* 多维数据集维度</span><span class="sxs-lookup"><span data-stu-id="c6720-154">**Internet Sales Order Details** cube dimension</span></span>  
  
    -   <span data-ttu-id="c6720-155">“销售原因”\*\*\*\* 多维数据集维度</span><span class="sxs-lookup"><span data-stu-id="c6720-155">**Sales Reason** cube dimension</span></span>  
  
    -   <span data-ttu-id="c6720-156">“Internet 销售详细信息钻取操作”\*\*\*\* 钻取操作</span><span class="sxs-lookup"><span data-stu-id="c6720-156">**Internet Sales Details Drillthrough Action** drillthrough action</span></span>  
  
    -   <span data-ttu-id="c6720-157">“总销售额”\*\*\*\* 计算成员</span><span class="sxs-lookup"><span data-stu-id="c6720-157">**Total Sales Amount** calculated member</span></span>  
  
    -   <span data-ttu-id="c6720-158">“总产品成本”\*\*\*\* 计算成员</span><span class="sxs-lookup"><span data-stu-id="c6720-158">**Total Product Cost** calculated member</span></span>  
  
    -   <span data-ttu-id="c6720-159">“Internet GPM”\*\*\*\* 计算成员</span><span class="sxs-lookup"><span data-stu-id="c6720-159">**Internet GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="c6720-160">“总 GPM”\*\*\*\* 计算成员</span><span class="sxs-lookup"><span data-stu-id="c6720-160">**Total GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="c6720-161">“所有产品的 Internet 销售额比率”\*\*\*\* 计算成员</span><span class="sxs-lookup"><span data-stu-id="c6720-161">**Internet Sales Ratio to All Products** calculated member</span></span>  
  
    -   <span data-ttu-id="c6720-162">“所有产品的总销售额比率”\*\*\*\* 计算成员</span><span class="sxs-lookup"><span data-stu-id="c6720-162">**Total Sales Ratio to All Products** calculated member</span></span>  
  
     <span data-ttu-id="c6720-163">这些对象与“分销商销售”无关。</span><span class="sxs-lookup"><span data-stu-id="c6720-163">These objects do not relate to resellers sales.</span></span>  
  
## <a name="defining-a-sales-summary-perspective"></a><span data-ttu-id="c6720-164">定义“销售汇总”透视</span><span class="sxs-lookup"><span data-stu-id="c6720-164">Defining a Sales Summary Perspective</span></span>  
  
1.  <span data-ttu-id="c6720-165">在“透视”\*\*\*\* 选项卡的工具栏上，单击“新建透视”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="c6720-165">On the toolbar of the **Perspectives** tab, click the **New Perspective** button.</span></span>  
  
2.  <span data-ttu-id="c6720-166">将新透视的名称更改为 `Sales Summary` 。</span><span class="sxs-lookup"><span data-stu-id="c6720-166">Change the name of the new perspective to `Sales Summary`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c6720-167">不能将计算度量值指定为默认度量值。</span><span class="sxs-lookup"><span data-stu-id="c6720-167">You cannot specify a calculated measure as the default measure.</span></span>  
  
3.  <span data-ttu-id="c6720-168">请清除下列对象的复选框：</span><span class="sxs-lookup"><span data-stu-id="c6720-168">Clear the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="c6720-169">`Internet Sales`度量值组</span><span class="sxs-lookup"><span data-stu-id="c6720-169">`Internet Sales` measure group</span></span>  
  
    -   <span data-ttu-id="c6720-170">`Reseller Sales`度量值组</span><span class="sxs-lookup"><span data-stu-id="c6720-170">`Reseller Sales` measure group</span></span>  
  
    -   <span data-ttu-id="c6720-171">“Internet 销售原因”\*\*\*\* 度量值组</span><span class="sxs-lookup"><span data-stu-id="c6720-171">**Internet Sales Reason** measure group</span></span>  
  
    -   <span data-ttu-id="c6720-172">“销售配额”\*\*\*\* 度量值组</span><span class="sxs-lookup"><span data-stu-id="c6720-172">**Sales Quotas** measure group</span></span>  
  
    -   <span data-ttu-id="c6720-173">“销售 Quotas1”\*\*\*\* 度量值组</span><span class="sxs-lookup"><span data-stu-id="c6720-173">**Sales Quotas1** measure group</span></span>  
  
    -   <span data-ttu-id="c6720-174">“Internet 销售订单详细信息”\*\*\*\* 多维数据集维度</span><span class="sxs-lookup"><span data-stu-id="c6720-174">**Internet Sales Order Details** cube dimension</span></span>  
  
    -   <span data-ttu-id="c6720-175">“销售原因”\*\*\*\* 多维数据集维度</span><span class="sxs-lookup"><span data-stu-id="c6720-175">**Sales Reason** cube dimension</span></span>  
  
    -   <span data-ttu-id="c6720-176">“Internet 销售详细信息钻取操作”\*\*\*\* 钻取操作</span><span class="sxs-lookup"><span data-stu-id="c6720-176">**Internet Sales Details Drillthrough Action** drillthrough action</span></span>  
  
4.  <span data-ttu-id="c6720-177">选中以下对象的复选框：</span><span class="sxs-lookup"><span data-stu-id="c6720-177">Select the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="c6720-178">“Internet 销售计数”\*\*\*\* 度量值</span><span class="sxs-lookup"><span data-stu-id="c6720-178">**Internet Sales Count** measure</span></span>  
  
    -   <span data-ttu-id="c6720-179">“分销商销售计数”\*\*\*\* 度量值</span><span class="sxs-lookup"><span data-stu-id="c6720-179">**Reseller Sales Count** measure</span></span>  
  
## <a name="browsing-the-cube-through-each-perspective"></a><span data-ttu-id="c6720-180">通过每个透视浏览多维数据集</span><span class="sxs-lookup"><span data-stu-id="c6720-180">Browsing the Cube Through Each Perspective</span></span>  
  
1.  <span data-ttu-id="c6720-181">在“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6720-181">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="c6720-182">成功完成部署后，请切换到“浏览器”\*\*\*\* 选项卡，然后单击“重新连接”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="c6720-182">When deployment has successfully completed, switch to the **Browser** tab, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="c6720-183">启动 Excel。</span><span class="sxs-lookup"><span data-stu-id="c6720-183">Start Excel.</span></span>  
  
4.  <span data-ttu-id="c6720-184">当您在 Excel 中浏览模型时，“在 Excel 中分析”将会提示选择您要使用的透视，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="c6720-184">Analyze in Excel prompts you to choose which perspective to use when browsing the model in Excel, as shown in the following image.</span></span>  
  
     <span data-ttu-id="c6720-185">![“Internet 销售额”透视的对象](../../2014/tutorials/media/l9-perspectives-3.gif "“Internet 销售额”透视的对象")</span><span class="sxs-lookup"><span data-stu-id="c6720-185">![Objects for the Internet Sales perspective](../../2014/tutorials/media/l9-perspectives-3.gif "Objects for the Internet Sales perspective")</span></span>  
  
5.  <span data-ttu-id="c6720-186">或者，您可以从 Windows 的“开始”菜单启动 Excel，定义与本地主机上 Analysis Services 教程数据库的连接，并且在数据连接向导中选择某一透视，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="c6720-186">Alternatively, you can start Excel from the Windows Start menu, define a connection to the Analysis Services Tutorial database on localhost, and choose a perspective in the Data Connection wizard, as shown in the following image.</span></span>  
  
     <span data-ttu-id="c6720-187">![Excel 中的“数据连接”向导](../../2014/tutorials/media/l9-perspectives-3b.gif "Excel 中的“数据连接”向导")</span><span class="sxs-lookup"><span data-stu-id="c6720-187">![Data Connection wizard in Excel](../../2014/tutorials/media/l9-perspectives-3b.gif "Data Connection wizard in Excel")</span></span>  
  
6.  <span data-ttu-id="c6720-188">`Internet Sales`在**透视**列表中选择，然后在 "元数据" 窗格中查看度量值和维度。</span><span class="sxs-lookup"><span data-stu-id="c6720-188">Select `Internet Sales` in the **Perspective** list and then review the measures and dimensions in the metadata pane.</span></span>  
  
     <span data-ttu-id="c6720-189">请注意，只那些为“Internet 销售”透视指定的对象才会出现。</span><span class="sxs-lookup"><span data-stu-id="c6720-189">Notice that only those objects that are specified for the Internet Sales perspective appear.</span></span>  
  
7.  <span data-ttu-id="c6720-190">在元数据窗格中，展开“度量值”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6720-190">In the metadata pane, expand **Measures**.</span></span>  
  
     <span data-ttu-id="c6720-191">请注意，只有 `Internet Sales` 度量值组显示为 "所有产品的**GPM**和**internet 销售比率**" 计算成员。</span><span class="sxs-lookup"><span data-stu-id="c6720-191">Notice that only the `Internet Sales` measure group appears, together with the **Internet GPM** and **Internet Sales Ratio to All Products** calculated members.</span></span>  
  
8.  <span data-ttu-id="c6720-192">在模型中，再次选择 Excel。</span><span class="sxs-lookup"><span data-stu-id="c6720-192">In the model, select Excel again.</span></span> <span data-ttu-id="c6720-193">选择 `Sales Summary`。</span><span class="sxs-lookup"><span data-stu-id="c6720-193">Select `Sales Summary`.</span></span>  
  
     <span data-ttu-id="c6720-194">注意，在每个度量值组中，只出现单个度量值，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="c6720-194">Notice that in each of these measure groups, only a single measure appears, as shown in the following image.</span></span>  
  
     <span data-ttu-id="c6720-195">![“Internet 销售”度量值和“分销商销售”度量值](../../2014/tutorials/media/l9-perspectives-4.gif "“Internet 销售”度量值和“分销商销售”度量值")</span><span class="sxs-lookup"><span data-stu-id="c6720-195">![Internet Sales and Reseller Sales measures](../../2014/tutorials/media/l9-perspectives-4.gif "Internet Sales and Reseller Sales measures")</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c6720-196">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="c6720-196">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c6720-197">定义和浏览翻译</span><span class="sxs-lookup"><span data-stu-id="c6720-197">Defining and Browsing Translations</span></span>](lesson-9-2-defining-and-browsing-translations.md)  
  
## <a name="see-also"></a><span data-ttu-id="c6720-198">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c6720-198">See Also</span></span>  
 <span data-ttu-id="c6720-199">[视角](multidimensional-models-olap-logical-cube-objects/perspectives.md) </span><span class="sxs-lookup"><span data-stu-id="c6720-199">[Perspectives](multidimensional-models-olap-logical-cube-objects/perspectives.md) </span></span>  
 [<span data-ttu-id="c6720-200">多维模型中的透视</span><span class="sxs-lookup"><span data-stu-id="c6720-200">Perspectives in Multidimensional Models</span></span>](multidimensional-models/perspectives-in-multidimensional-models.md)  
  
  
