---
title: KPI 窗体编辑器 (Kpi 选项卡，多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpidefinitionpane.f1
ms.assetid: 45c6453a-bbe2-4ca5-836e-c7ef11cfcb65
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c88d6fcec60634f37ddad8b6d0f5cb2124fa1cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579143"
---
# <a name="kpi-form-editor-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="1ce27-102">KPI 窗体编辑器（KPI 选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="1ce27-102">KPI Form Editor (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="1ce27-103">可以使用多维数据集设计器中的“KPI”选项卡上的“KPI 窗体编辑器”窗格，创建或修改所选的关键绩效指标 (KPI)。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1ce27-103">Use the **KPI Form Editor** pane on the **KPIs** tab in Cube Designer to create or modify the selected Key Performance Indicator (KPI).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ce27-104">此窗格仅显示在窗体视图中。</span><span class="sxs-lookup"><span data-stu-id="1ce27-104">This pane is displayed only in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1ce27-105">选项</span><span class="sxs-lookup"><span data-stu-id="1ce27-105">Options</span></span>  
 <span data-ttu-id="1ce27-106">**名称**</span><span class="sxs-lookup"><span data-stu-id="1ce27-106">**Name**</span></span>  
 <span data-ttu-id="1ce27-107">键入 KPI 的名称。</span><span class="sxs-lookup"><span data-stu-id="1ce27-107">Type the name of the KPI.</span></span>  
  
 <span data-ttu-id="1ce27-108">**关联的度量值组**</span><span class="sxs-lookup"><span data-stu-id="1ce27-108">**Associated measure group**</span></span>  
 <span data-ttu-id="1ce27-109">选择与 KPI 关联的度量值组。</span><span class="sxs-lookup"><span data-stu-id="1ce27-109">Select the measure group associated with the KPI.</span></span> <span data-ttu-id="1ce27-110">客户端应用程序可以使用此信息来确定当用户浏览此 KPI 时哪些维度可用。</span><span class="sxs-lookup"><span data-stu-id="1ce27-110">The client application can use this information to determine which dimensions are available when the user browses this KPI.</span></span>  
  
 <span data-ttu-id="1ce27-111">**值表达式**</span><span class="sxs-lookup"><span data-stu-id="1ce27-111">**Value Expression**</span></span>  
 <span data-ttu-id="1ce27-112">展开此项可以查看或编辑 KPI 值的多维表达式 (MDX) 表达式。</span><span class="sxs-lookup"><span data-stu-id="1ce27-112">Expand to view or edit the Multidimensional Expressions (MDX) expression for the value of the KPI.</span></span>  
  
 <span data-ttu-id="1ce27-113">键入返回 KPI 的值的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="1ce27-113">Type the MDX expression that returns the value of the KPI.</span></span>  
  
 <span data-ttu-id="1ce27-114">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="1ce27-114">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="1ce27-115">**目标表达式**</span><span class="sxs-lookup"><span data-stu-id="1ce27-115">**Goal Expression**</span></span>  
 <span data-ttu-id="1ce27-116">展开此项可以查看或编辑 KPI 的目标值的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="1ce27-116">Expand to view or edit the MDX expression for the goal value of the KPI.</span></span>  
  
 <span data-ttu-id="1ce27-117">键入当 KPI 运行时返回 KPI 的目标值的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="1ce27-117">Type the MDX expression that returns the goal value of the KPI when the KPI is run.</span></span>  
  
 <span data-ttu-id="1ce27-118">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="1ce27-118">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="1ce27-119">**Status**</span><span class="sxs-lookup"><span data-stu-id="1ce27-119">**Status**</span></span>  
 <span data-ttu-id="1ce27-120">展开此项可以查看“状态图形”和“状态表达式”选项。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1ce27-120">Expand to view the **Status graphic** and **Status expression** options.</span></span>  
  
 <span data-ttu-id="1ce27-121">**状态图形**</span><span class="sxs-lookup"><span data-stu-id="1ce27-121">**Status graphic**</span></span>  
 <span data-ttu-id="1ce27-122">选择客户端应用程序用来以图形形式显示状态值的图形。</span><span class="sxs-lookup"><span data-stu-id="1ce27-122">Select the graphic to be used by the client application to represent the status value in graphical form.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ce27-123">客户端应用程序可以支持所选的图形，或将其替换为适当的替代项。</span><span class="sxs-lookup"><span data-stu-id="1ce27-123">The client application can support the selected graphic or replace it with an appropriate alternative.</span></span>  
  
 <span data-ttu-id="1ce27-124">**状态表达式**</span><span class="sxs-lookup"><span data-stu-id="1ce27-124">**Status expression**</span></span>  
 <span data-ttu-id="1ce27-125">键入当 KPI 运行时返回 KPI 的状态值的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="1ce27-125">Type the MDX expression that returns the status value of the KPI when the KPI is run.</span></span>  
  
 <span data-ttu-id="1ce27-126">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="1ce27-126">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="1ce27-127">建议此表达式返回介于-1 和1之间的十进制数字。</span><span class="sxs-lookup"><span data-stu-id="1ce27-127">It is recommended that this expression returns a decimal number between -1 and 1.</span></span> <span data-ttu-id="1ce27-128">数字越小表示情况越差，数字越大表示情况越好。</span><span class="sxs-lookup"><span data-stu-id="1ce27-128">A lower number represents a negative situation, while a higher number represents a positive situation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ce27-129">小于1和更高1的值是可行的，但可能无法由第三方客户端应用程序正确解释。</span><span class="sxs-lookup"><span data-stu-id="1ce27-129">Values below -1 and above 1 are possible but may not be interpreted correctly by third-party client applications.</span></span>  
  
 <span data-ttu-id="1ce27-130">**趋势**</span><span class="sxs-lookup"><span data-stu-id="1ce27-130">**Trend**</span></span>  
 <span data-ttu-id="1ce27-131">展开此项可以查看“走向图”和“走向表达式”\*\*\*\*\*\*\*\* 选项。</span><span class="sxs-lookup"><span data-stu-id="1ce27-131">Expand to view the **Trend graphic** and **Trend expression** options.</span></span>  
  
 <span data-ttu-id="1ce27-132">**走向图**</span><span class="sxs-lookup"><span data-stu-id="1ce27-132">**Trend graphic**</span></span>  
 <span data-ttu-id="1ce27-133">选择客户端应用程序用来以图形形式显示走向值的图形。</span><span class="sxs-lookup"><span data-stu-id="1ce27-133">Select the graphic to be used by the client application to represent the trend value in graphical form.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ce27-134">客户端应用程序可以支持所选的图形，或将其替换为适当的替代项。</span><span class="sxs-lookup"><span data-stu-id="1ce27-134">The client application can support the selected graphic or replace it with an appropriate alternative.</span></span>  
  
 <span data-ttu-id="1ce27-135">**走向表达式**</span><span class="sxs-lookup"><span data-stu-id="1ce27-135">**Trend expression**</span></span>  
 <span data-ttu-id="1ce27-136">键入返回 KPI 的走向值的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="1ce27-136">Type the MDX expression that returns the trend value of the KPI.</span></span>  
  
 <span data-ttu-id="1ce27-137">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="1ce27-137">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="1ce27-138">走向表达式可以基于在给定的业务上下文中有意义的任何基于时间的条件。</span><span class="sxs-lookup"><span data-stu-id="1ce27-138">The trend expression can be based on any time-based criteria that makes sense in a given business context.</span></span> <span data-ttu-id="1ce27-139">建议此表达式返回介于-1 和1之间的十进制数字。</span><span class="sxs-lookup"><span data-stu-id="1ce27-139">It is recommended that this expression returns a decimal number between -1 and 1.</span></span> <span data-ttu-id="1ce27-140">较小的数字表示随着时间的推移情况会越来越差，较大的数字表示随着时间的推移情况会越来越好。</span><span class="sxs-lookup"><span data-stu-id="1ce27-140">A lower number represents a negative trend over time; a higher number represents a positive trend over time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ce27-141">小于1和更高1的值是可行的，但可能无法由第三方客户端应用程序正确解释。</span><span class="sxs-lookup"><span data-stu-id="1ce27-141">Values below -1 and above 1 are possible but may not be interpreted correctly by third-party client applications.</span></span>  
  
 <span data-ttu-id="1ce27-142">**其他属性**</span><span class="sxs-lookup"><span data-stu-id="1ce27-142">**Additional Properties**</span></span>  
 <span data-ttu-id="1ce27-143">展开此项可以查看“显示文件夹”、“父级 KPI”、“当前时间成员”、“权重”和“说明”选项。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1ce27-143">Expand to view the **Display folder**, **Parent KPI**, **Current time member**, **Weight**, and **Description** options.</span></span>  
  
 <span data-ttu-id="1ce27-144">**显示文件夹**</span><span class="sxs-lookup"><span data-stu-id="1ce27-144">**Display folder**</span></span>  
 <span data-ttu-id="1ce27-145">键入客户端应用程序在显示时所使用的 KPI 分类。</span><span class="sxs-lookup"><span data-stu-id="1ce27-145">Type the categorization of the KPI for use by the client application for display purposes.</span></span>  
  
 <span data-ttu-id="1ce27-146">在显示文件夹中使用反斜杠 (\\) 分隔文件夹名称，并使用分号 (;) 分隔多个显示文件夹。</span><span class="sxs-lookup"><span data-stu-id="1ce27-146">Use a backward slash (\\) to separate folder names in a display folder and a semicolon (;) to separate multiple display folders.</span></span> <span data-ttu-id="1ce27-147">例如，键入 `Category\Goal\Scientific;Category\Goal\Metric`。</span><span class="sxs-lookup"><span data-stu-id="1ce27-147">For example, type `Category\Goal\Scientific;Category\Goal\Metric`.</span></span>  
  
 <span data-ttu-id="1ce27-148">**父级 KPI**</span><span class="sxs-lookup"><span data-stu-id="1ce27-148">**Parent KPI**</span></span>  
 <span data-ttu-id="1ce27-149">选择一个现有 KPI，将在其下对 KPI 进行分类以供客户端应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="1ce27-149">Select an existing KPI under which to categorize the KPI for use by the client application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ce27-150">如果将此选项设置为现有 KPI，则忽略“显示文件夹”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ce27-150">If this option is set to an existing KPI, **Display folder** is ignored.</span></span>  
  
 <span data-ttu-id="1ce27-151">**当前时间成员**</span><span class="sxs-lookup"><span data-stu-id="1ce27-151">**Current time member**</span></span>  
 <span data-ttu-id="1ce27-152">键入返回用于标识 KPI 临时上下文的成员的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="1ce27-152">Type the MDX expression that returns the member that identifies the temporal context of the KPI.</span></span>  
  
 <span data-ttu-id="1ce27-153">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="1ce27-153">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1ce27-154">MDX 表达式必须在与“关联的度量值组”中指定的度量值组关联的时间维度内返回唯一的成员名称。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1ce27-154">The MDX expression must return the unique name of a member within a time dimension associated with the measure group specified in **Associated measure group**.</span></span>  
  
 <span data-ttu-id="1ce27-155">**Weight**</span><span class="sxs-lookup"><span data-stu-id="1ce27-155">**Weight**</span></span>  
 <span data-ttu-id="1ce27-156">展开此项可以查看或编辑 KPI 加权系数的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="1ce27-156">Expand to view or edit the MDX expression for the weighting factor of the KPI.</span></span>  
  
 <span data-ttu-id="1ce27-157">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="1ce27-157">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="1ce27-158">**说明**</span><span class="sxs-lookup"><span data-stu-id="1ce27-158">**Description**</span></span>  
 <span data-ttu-id="1ce27-159">键入 KPI 的说明（可选）。</span><span class="sxs-lookup"><span data-stu-id="1ce27-159">Type the optional description of the KPI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce27-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ce27-160">See Also</span></span>  
 [<span data-ttu-id="1ce27-161">&#40;多维数据集设计器的 Kpi&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="1ce27-161">KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  
