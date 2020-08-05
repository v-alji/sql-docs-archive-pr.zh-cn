---
title: KPI 浏览器 (Kpi 选项卡，多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpibrowserpane.f1
ms.assetid: 2f61bde6-e6ec-4511-8645-c272374014ad
author: minewiskan
ms.author: owend
ms.openlocfilehash: 591dfb7c27842e365b78484153dbbde3713b452e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579146"
---
# <a name="kpi-browser-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="84622-102">KPI 浏览器（KPI 选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="84622-102">KPI Browser (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="84622-103">可以使用多维数据集设计器中的“KPI”\*\*\*\* 选项卡上的“KPI 浏览器”\*\*\*\* 窗格查看和测试关键绩效指标 (KPI) 的结果。</span><span class="sxs-lookup"><span data-stu-id="84622-103">Use the **KPI Browser** pane on the **KPIs** tab in Cube Designer to view and test the results of Key Performance Indicators (KPIs).</span></span> <span data-ttu-id="84622-104">在浏览之前，必须先将 kpi 部署到 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="84622-104">KPIs must first be deployed to a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance before browsing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84622-105">此窗格仅显示在浏览器视图中。</span><span class="sxs-lookup"><span data-stu-id="84622-105">This pane is displayed only in browser view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="84622-106">选项</span><span class="sxs-lookup"><span data-stu-id="84622-106">Options</span></span>  
 <span data-ttu-id="84622-107">**子多维数据集网格**</span><span class="sxs-lookup"><span data-stu-id="84622-107">**Subcube grid**</span></span>  
 <span data-ttu-id="84622-108">用于定义子多维数据集和限制在“结果”\*\*\*\* 窗格中显示的 KPI 结果。</span><span class="sxs-lookup"><span data-stu-id="84622-108">Use to define a subcube and restrict the results of the KPIs to be displayed in the **Results** pane.</span></span> <span data-ttu-id="84622-109">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="84622-109">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="84622-110">**维度**</span><span class="sxs-lookup"><span data-stu-id="84622-110">**Dimension**</span></span>  
 <span data-ttu-id="84622-111">选择应用此筛选器的维度。</span><span class="sxs-lookup"><span data-stu-id="84622-111">Select the dimension to which this filter applies.</span></span>  
  
 <span data-ttu-id="84622-112">**层次结构**</span><span class="sxs-lookup"><span data-stu-id="84622-112">**Hierarchy**</span></span>  
 <span data-ttu-id="84622-113">选择应用此筛选器的层次结构。</span><span class="sxs-lookup"><span data-stu-id="84622-113">Select the hierarchy to which this filter applies.</span></span>  
  
 <span data-ttu-id="84622-114">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="84622-114">**Operator**</span></span>  
 <span data-ttu-id="84622-115">选择运算符，以定义“筛选表达式”\*\*\*\* 中的表达式如何应用于所选层次结构。</span><span class="sxs-lookup"><span data-stu-id="84622-115">Select the operator that defines how the expression in **Filter Expression** is applied to the selected hierarchy.</span></span> <span data-ttu-id="84622-116">下表对可用的运算符进行了说明：</span><span class="sxs-lookup"><span data-stu-id="84622-116">The following table describes the available operators.</span></span>  
  
|<span data-ttu-id="84622-117">值</span><span class="sxs-lookup"><span data-stu-id="84622-117">Value</span></span>|<span data-ttu-id="84622-118">说明</span><span class="sxs-lookup"><span data-stu-id="84622-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84622-119">**等于**</span><span class="sxs-lookup"><span data-stu-id="84622-119">**Equal**</span></span>|<span data-ttu-id="84622-120">结果限制为在 **“筛选表达式”** 中定义的集合。</span><span class="sxs-lookup"><span data-stu-id="84622-120">The results are restricted to the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="84622-121">**不等于**</span><span class="sxs-lookup"><span data-stu-id="84622-121">**Not Equal**</span></span>|<span data-ttu-id="84622-122">结果限制为排除在 **“筛选表达式”** 中所定义集合之外的成员。</span><span class="sxs-lookup"><span data-stu-id="84622-122">The results are restricted to the members excluded by the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="84622-123">**在**</span><span class="sxs-lookup"><span data-stu-id="84622-123">**In**</span></span>|<span data-ttu-id="84622-124">结果限制为在 **“筛选表达式”** 中选择的命名集。</span><span class="sxs-lookup"><span data-stu-id="84622-124">The results are restricted to the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="84622-125">**不位于**</span><span class="sxs-lookup"><span data-stu-id="84622-125">**Not In**</span></span>|<span data-ttu-id="84622-126">结果限制为排除在 **“筛选表达式”** 中所选命名集之外的成员。</span><span class="sxs-lookup"><span data-stu-id="84622-126">The results are restricted to the members excluded by the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="84622-127">**包含**</span><span class="sxs-lookup"><span data-stu-id="84622-127">**Contains**</span></span>|<span data-ttu-id="84622-128">结果限制为成员名称包含 **“筛选表达式”** 中的字符串的成员。</span><span class="sxs-lookup"><span data-stu-id="84622-128">The results are restricted to members whose member names contain the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="84622-129">**开头为**</span><span class="sxs-lookup"><span data-stu-id="84622-129">**Begins With**</span></span>|<span data-ttu-id="84622-130">结果限制为成员名称以 **“筛选表达式”** 中的字符串开头的成员。</span><span class="sxs-lookup"><span data-stu-id="84622-130">The results are restricted to members whose member names begin with the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="84622-131">**范围(包括)**</span><span class="sxs-lookup"><span data-stu-id="84622-131">**Range (Inclusive)**</span></span>|<span data-ttu-id="84622-132">结果限制为在 **“筛选表达式”** 中选择的范围。</span><span class="sxs-lookup"><span data-stu-id="84622-132">The results are restricted to the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="84622-133">**范围(不包括)**</span><span class="sxs-lookup"><span data-stu-id="84622-133">**Range (Exclusive)**</span></span>|<span data-ttu-id="84622-134">结果限制为排除在 **“筛选表达式”** 中所选范围之外的成员。</span><span class="sxs-lookup"><span data-stu-id="84622-134">The results are restricted to the members excluded by the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="84622-135">**MDX**</span><span class="sxs-lookup"><span data-stu-id="84622-135">**MDX**</span></span>|<span data-ttu-id="84622-136">结果限制为在“筛选表达式”\*\*\*\* 中设置的多维表达式 (MDX) 表达式。</span><span class="sxs-lookup"><span data-stu-id="84622-136">The results are restricted to the Multidimensional Expressions (MDX) expression set in **Filter Expression**.</span></span>|  
  
 <span data-ttu-id="84622-137">**筛选表达式**</span><span class="sxs-lookup"><span data-stu-id="84622-137">**Filter Expression**</span></span>  
 <span data-ttu-id="84622-138">键入通过“运算符”\*\*\*\* 计算的表达式，该表达式可限制要浏览的 KPI 结果。</span><span class="sxs-lookup"><span data-stu-id="84622-138">Type the expression that is to be evaluated by **Operator**, which restricts the KPI results to be browsed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84622-139">此字段是动态数据输入元素，其外观将根据所选运算符的不同而相应改变，以反映该运算符所需的数据类型。</span><span class="sxs-lookup"><span data-stu-id="84622-139">This field is a dynamic data entry element, changing appearance to reflect the types of data necessary for the selected operator.</span></span>  
  
 <span data-ttu-id="84622-140">**结果网格**</span><span class="sxs-lookup"><span data-stu-id="84622-140">**Results grid**</span></span>  
 <span data-ttu-id="84622-141">基于“筛选器网格”\*\*\*\* 中定义的筛选器，显示 KPI 的计算结果值、目标、状态和走向。</span><span class="sxs-lookup"><span data-stu-id="84622-141">Displays the evaluated value, goal, status, and trend for the KPIs, based on the filter defined in **Filter grid**.</span></span> <span data-ttu-id="84622-142">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="84622-142">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="84622-143">**显示结构**</span><span class="sxs-lookup"><span data-stu-id="84622-143">**Display Structure**</span></span>  
 <span data-ttu-id="84622-144">显示多维数据集包含的 KPI，按照每个 KPI 的“显示文件夹”\*\*\*\* 或“父 KPI”\*\*\*\* 值分层组织。</span><span class="sxs-lookup"><span data-stu-id="84622-144">Displays the KPIs contained by the cube, hierarchically organized according to the **Display folder** or **Parent KPI** values for each KPI.</span></span>  
  
 <span data-ttu-id="84622-145">**值**</span><span class="sxs-lookup"><span data-stu-id="84622-145">**Value**</span></span>  
 <span data-ttu-id="84622-146">显示 KPI 的值。</span><span class="sxs-lookup"><span data-stu-id="84622-146">Displays the value of the KPI.</span></span>  
  
 <span data-ttu-id="84622-147">**目标**</span><span class="sxs-lookup"><span data-stu-id="84622-147">**Goal**</span></span>  
 <span data-ttu-id="84622-148">显示 KPI 的目标值。</span><span class="sxs-lookup"><span data-stu-id="84622-148">Displays the goal value of the KPI.</span></span>  
  
 <span data-ttu-id="84622-149">**Status**</span><span class="sxs-lookup"><span data-stu-id="84622-149">**Status**</span></span>  
 <span data-ttu-id="84622-150">显示 KPI 的状态图形。</span><span class="sxs-lookup"><span data-stu-id="84622-150">Displays the status graphic of the KPI.</span></span>  
  
 <span data-ttu-id="84622-151">**趋势**</span><span class="sxs-lookup"><span data-stu-id="84622-151">**Trend**</span></span>  
 <span data-ttu-id="84622-152">显示 KPI 的走向图形。</span><span class="sxs-lookup"><span data-stu-id="84622-152">Displays the trend graphic of the KPI.</span></span>  
  
 <span data-ttu-id="84622-153">**Weight**</span><span class="sxs-lookup"><span data-stu-id="84622-153">**Weight**</span></span>  
 <span data-ttu-id="84622-154">显示 KPI 的加权系数。</span><span class="sxs-lookup"><span data-stu-id="84622-154">Displays the weight factor of the KPI.</span></span>  
  
 <span data-ttu-id="84622-155">\*\* (说明) \*\*</span><span class="sxs-lookup"><span data-stu-id="84622-155">**(Description)**</span></span>  
 <span data-ttu-id="84622-156">如果为 KPI 提供了说明，则显示信息图标。</span><span class="sxs-lookup"><span data-stu-id="84622-156">Displays an information icon if a description is provided for a KPI.</span></span>  
  
 <span data-ttu-id="84622-157">将鼠标悬停在信息图标上方可以显示包含 KPI 说明的工具提示。</span><span class="sxs-lookup"><span data-stu-id="84622-157">Hover the mouse over the information icon to display a ToolTip containing the description for the KPI.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84622-158">如果在对 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例计算 KPI 时发生错误，此选项将显示与该错误关联的信息。</span><span class="sxs-lookup"><span data-stu-id="84622-158">If an error occurs while calculating a KPI on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, this option displays information associated with the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84622-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84622-159">See Also</span></span>  
 [<span data-ttu-id="84622-160">&#40;多维数据集设计器的 Kpi&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="84622-160">KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  
