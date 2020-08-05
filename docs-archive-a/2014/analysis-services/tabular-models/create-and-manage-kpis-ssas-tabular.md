---
title: 创建和管理 Kpi (SSAS 表格) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.kpi.f1
ms.assetid: c96026c2-4394-4c3c-986b-4c95a4421900
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8e9d7ef77939efe407ed6ab0d725a6d788c58b49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580404"
---
# <a name="create-and-manage-kpis-ssas-tabular"></a><span data-ttu-id="561c1-102">创建和管理 KPI（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="561c1-102">Create and Manage KPIs (SSAS Tabular)</span></span>
  <span data-ttu-id="561c1-103">本主题介绍如何在表格模型中创建、编辑或删除 KPI（关键绩效指标）。</span><span class="sxs-lookup"><span data-stu-id="561c1-103">This topic describes how to create, edit, or delete a KPI (Key Performance Indicator) in a tabular model.</span></span> <span data-ttu-id="561c1-104">若要创建 KPI，请选择计算结果为 KPI 的基础值的度量值。</span><span class="sxs-lookup"><span data-stu-id="561c1-104">To create a KPI, you select a measure that evaluates to the KPI's Base value.</span></span> <span data-ttu-id="561c1-105">然后使用“关键绩效指标”对话框选择计算结果为某一目标值的第二个度量值或绝对值。</span><span class="sxs-lookup"><span data-stu-id="561c1-105">You then use the Key Performance Indicator dialog box to select a second measure or an absolute value that evaluates to a target value.</span></span> <span data-ttu-id="561c1-106">之后可以定义状态阈值，这些状态阈值度量基础度量值和目标度量值之间的性能。</span><span class="sxs-lookup"><span data-stu-id="561c1-106">You can then define status thresholds that measure the performance between the Base and Target measures.</span></span>  
  
 <span data-ttu-id="561c1-107">本主题包括以下任务：</span><span class="sxs-lookup"><span data-stu-id="561c1-107">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="561c1-108">创建 KPI</span><span class="sxs-lookup"><span data-stu-id="561c1-108">To create a KPI</span></span>](#bkmk_create_KPI)  
  
-   [<span data-ttu-id="561c1-109">编辑 KPI</span><span class="sxs-lookup"><span data-stu-id="561c1-109">To edit a KPI</span></span>](#bkmk_edit_KPI)  
  
-   [<span data-ttu-id="561c1-110">删除 KPI 和基础度量值</span><span class="sxs-lookup"><span data-stu-id="561c1-110">To delete a KPI and the base measure</span></span>](#bkmk_delete)  
  
-   [<span data-ttu-id="561c1-111">删除 KPI 但保留基础度量值</span><span class="sxs-lookup"><span data-stu-id="561c1-111">To delete a KPI, but keep the base measure</span></span>](#bkmk_delete_KPI)  
  
## <a name="tasks"></a><span data-ttu-id="561c1-112">任务</span><span class="sxs-lookup"><span data-stu-id="561c1-112">Tasks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="561c1-113">在创建 KPI 前，您必须首先创建一个求值的基础度量值。</span><span class="sxs-lookup"><span data-stu-id="561c1-113">Before creating a KPI, you must first create a Base measure that evaluates to value.</span></span> <span data-ttu-id="561c1-114">然后，您将该基础度量值扩展到 KPI。</span><span class="sxs-lookup"><span data-stu-id="561c1-114">You then extend the Base measure to a KPI.</span></span> <span data-ttu-id="561c1-115">另一主题 [创建和管理度量值（SSAS 表格）](measures-ssas-tabular.md)中有描述如何创建度量值。</span><span class="sxs-lookup"><span data-stu-id="561c1-115">How to create measures are described in another topic, [Create and Manage Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md).</span></span> <span data-ttu-id="561c1-116">KPI 也要求目标值。</span><span class="sxs-lookup"><span data-stu-id="561c1-116">A KPI also requires a target value.</span></span> <span data-ttu-id="561c1-117">该值可来自另一个预定义的度量值或绝对值。</span><span class="sxs-lookup"><span data-stu-id="561c1-117">This value can be from another pre-defined measure or an absolute value.</span></span> <span data-ttu-id="561c1-118">一旦您将基础度量值扩展到 KPI 后，可以选择目标值并且在“关键绩效指标”对话框中定义状态阈值。</span><span class="sxs-lookup"><span data-stu-id="561c1-118">Once you have extended a Base measure to a KPI, you can then select the target value and define status thresholds in the Key Performance Indicator dialog box.</span></span>  
  
###  <a name="to-create-a-kpi"></a><a name="bkmk_create_KPI"></a> <span data-ttu-id="561c1-119">创建 KPI</span><span class="sxs-lookup"><span data-stu-id="561c1-119">To create a KPI</span></span>  
  
1.  <span data-ttu-id="561c1-120">在度量值网格中，右键单击将充当基础度量值（值）的度量值，然后单击“创建 KPI”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="561c1-120">In the measure grid, right-click the measure that will serve as the Base measure (value), and then click **Create KPI**.</span></span>  
  
2.  <span data-ttu-id="561c1-121">在 **“关键绩效指标”** 对话框的 **“定义目标值”** 中，选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="561c1-121">In the **Key Performance Indicator** dialog box, in **Define target value**, select from one of the following:</span></span>  
  
     <span data-ttu-id="561c1-122">选择 **“度量值”**，然后从列表框中选择一个目标度量值。</span><span class="sxs-lookup"><span data-stu-id="561c1-122">Select **Measure**, and then select a target measure from the listbox.</span></span>  
  
     <span data-ttu-id="561c1-123">选择 **“绝对值”**，然后键入一个数值。</span><span class="sxs-lookup"><span data-stu-id="561c1-123">Select **Absolute value**, and then type a numerical value.</span></span>  
  
3.  <span data-ttu-id="561c1-124">在 **“定义状态阈值”** 中，单击并滑动阈值下限和上限。</span><span class="sxs-lookup"><span data-stu-id="561c1-124">In **Define status thresholds**, click and slide the low and high threshold values.</span></span>  
  
4.  <span data-ttu-id="561c1-125">在 **“选择图标样式”** 中，单击某一图像类型。</span><span class="sxs-lookup"><span data-stu-id="561c1-125">In **Select icon style**, click an image type.</span></span>  
  
5.  <span data-ttu-id="561c1-126">单击 **“说明”**，然后为“KPI”、“值”、“状态”和“目标”键入说明。</span><span class="sxs-lookup"><span data-stu-id="561c1-126">Click on **Descriptions**, and then type descriptions for KPI, Value, Status, and Target.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="561c1-127">您可以使用“在 Excel 中分析”功能测试您的 KPI。</span><span class="sxs-lookup"><span data-stu-id="561c1-127">You can use the Analyze in Excel feature to test your KPI.</span></span> <span data-ttu-id="561c1-128">有关详细信息，请参阅本主题后面的 [在 Excel 中分析（SSAS 表格）](analyze-in-excel-ssas-tabular.md)中的“角色管理器”对话框定义角色的表格模型作者。</span><span class="sxs-lookup"><span data-stu-id="561c1-128">For more information, see [Analyze in Excel &#40;SSAS Tabular&#41;](analyze-in-excel-ssas-tabular.md).</span></span>  
  
###  <a name="to-edit-a-kpi"></a><a name="bkmk_edit_KPI"></a> <span data-ttu-id="561c1-129">编辑 KPI</span><span class="sxs-lookup"><span data-stu-id="561c1-129">To edit a KPI</span></span>  
  
-   <span data-ttu-id="561c1-130">在度量值网格中，右键单击充当 KPI 的基础度量值（值）的度量值，然后单击“编辑 KPI 设置”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="561c1-130">In the measure grid, right-click the measure that serves as the Base measure (value) of the KPI, and then click **Edit KPI Settings**.</span></span>  
  
###  <a name="to-delete-a-kpi-and-the-base-measure"></a><a name="bkmk_delete"></a> <span data-ttu-id="561c1-131">删除 KPI 和基础度量值</span><span class="sxs-lookup"><span data-stu-id="561c1-131">To delete a KPI and the base measure</span></span>  
  
-   <span data-ttu-id="561c1-132">在度量值网格中，右键单击充当 KPI 的基础度量值（值）的度量值，然后单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="561c1-132">In the measure grid, right-click the measure that serves as the Base measure (value) of the KPI, and then click **Delete**.</span></span>  
  
###  <a name="to-delete-a-kpi-but-keep-the-base-measure"></a><a name="bkmk_delete_KPI"></a><span data-ttu-id="561c1-133">删除 KPI 但保留基础度量值</span><span class="sxs-lookup"><span data-stu-id="561c1-133">To delete a KPI, but keep the base measure</span></span>  
  
-   <span data-ttu-id="561c1-134">在度量值网格中，右键单击充当 KPI 的基础度量值（值）的度量值，然后单击“删除 KPI”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="561c1-134">In the measure grid, right-click the measure that serves as the Base measure (value) of the KPI, and then click **Delete KPI**.</span></span>  
  
## <a name="alt-shortcuts"></a><span data-ttu-id="561c1-135">ALT 快捷键</span><span class="sxs-lookup"><span data-stu-id="561c1-135">ALT Shortcuts</span></span>  
  
|<span data-ttu-id="561c1-136">用户界面部分</span><span class="sxs-lookup"><span data-stu-id="561c1-136">UI section</span></span>|<span data-ttu-id="561c1-137">键命令</span><span class="sxs-lookup"><span data-stu-id="561c1-137">Key command</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="561c1-138">KPI 基础度量值</span><span class="sxs-lookup"><span data-stu-id="561c1-138">KPI base measure</span></span>|<span data-ttu-id="561c1-139">ALT+B</span><span class="sxs-lookup"><span data-stu-id="561c1-139">ALT+B</span></span>|  
|<span data-ttu-id="561c1-140">KPI 状态</span><span class="sxs-lookup"><span data-stu-id="561c1-140">KPI Status</span></span>|<span data-ttu-id="561c1-141">Alt+S</span><span class="sxs-lookup"><span data-stu-id="561c1-141">ALT+S</span></span>|  
|<span data-ttu-id="561c1-142">度量</span><span class="sxs-lookup"><span data-stu-id="561c1-142">Measure</span></span>|<span data-ttu-id="561c1-143">Alt+M</span><span class="sxs-lookup"><span data-stu-id="561c1-143">ALT+M</span></span>|  
|<span data-ttu-id="561c1-144">“绝对值”</span><span class="sxs-lookup"><span data-stu-id="561c1-144">Absolute value</span></span>|<span data-ttu-id="561c1-145">ALT+A</span><span class="sxs-lookup"><span data-stu-id="561c1-145">ALT+A</span></span>|  
|<span data-ttu-id="561c1-146">“定义状态阈值”</span><span class="sxs-lookup"><span data-stu-id="561c1-146">Define status thresholds</span></span>|<span data-ttu-id="561c1-147">ALT+U</span><span class="sxs-lookup"><span data-stu-id="561c1-147">ALT+U</span></span>|  
|<span data-ttu-id="561c1-148">“选择图标样式”</span><span class="sxs-lookup"><span data-stu-id="561c1-148">Select icon style</span></span>|<span data-ttu-id="561c1-149">Alt+I</span><span class="sxs-lookup"><span data-stu-id="561c1-149">ALT+I</span></span>|  
|<span data-ttu-id="561c1-150">趋势</span><span class="sxs-lookup"><span data-stu-id="561c1-150">Trend</span></span>|<span data-ttu-id="561c1-151">ALT+T</span><span class="sxs-lookup"><span data-stu-id="561c1-151">ALT+T</span></span>|  
|<span data-ttu-id="561c1-152">说明</span><span class="sxs-lookup"><span data-stu-id="561c1-152">Descriptions</span></span>|<span data-ttu-id="561c1-153">ALT+D</span><span class="sxs-lookup"><span data-stu-id="561c1-153">ALT+D</span></span>|  
|<span data-ttu-id="561c1-154">趋势</span><span class="sxs-lookup"><span data-stu-id="561c1-154">Trend</span></span>|<span data-ttu-id="561c1-155">ALT+T</span><span class="sxs-lookup"><span data-stu-id="561c1-155">ALT+T</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="561c1-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="561c1-156">See Also</span></span>  
 <span data-ttu-id="561c1-157">[&#40;SSAS 表格&#41;的 Kpi](kpis-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="561c1-157">[KPIs &#40;SSAS Tabular&#41;](kpis-ssas-tabular.md) </span></span>  
 <span data-ttu-id="561c1-158">[&#40;SSAS 表格&#41;度量值](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="561c1-158">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="561c1-159">创建和管理度量值（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="561c1-159">Create and Manage Measures &#40;SSAS Tabular&#41;</span></span>](create-and-manage-measures-ssas-tabular.md)  
  
  
