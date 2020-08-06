---
title: 第8课：创建关键绩效指标 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a6c8ac2b-64ba-456f-b418-7bf0afe145d1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3beaab8a34844ecbd633eb5fabbacf37edfede2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689088"
---
# <a name="lesson-8-create-key-performance-indicators"></a><span data-ttu-id="02e86-102">第 8 课：创建关键绩效指标</span><span class="sxs-lookup"><span data-stu-id="02e86-102">Lesson 8: Create Key Performance Indicators</span></span>
  <span data-ttu-id="02e86-103">在本课中，您将创建关键绩效指标 (KPI)。</span><span class="sxs-lookup"><span data-stu-id="02e86-103">In this lesson, you will create Key Performance Indicators (KPIs).</span></span> <span data-ttu-id="02e86-104">KPI 用来衡量由基度量值定义的某个值的绩效（与同样由度量值或绝对值定义的目标值进行对比）。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="02e86-104">KPIs are used to gauge performance of a value, defined by a *Base* measure, against a *Target* value, also defined by a measure or by an absolute value.</span></span> <span data-ttu-id="02e86-105">在报告客户端应用程序中，KPI 可以为业务专业人员提供一种快速简单的方法来了解业务成功摘要情况或查明趋势。</span><span class="sxs-lookup"><span data-stu-id="02e86-105">In reporting client applications, KPIs can provide business professionals a quick and easy way to understand a summary of business success or to identify trends.</span></span> <span data-ttu-id="02e86-106">若要了解详细信息，请参阅 [KPI（SSAS 表格）](tabular-models/kpis-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="02e86-106">To learn more, see [KPIs &#40;SSAS Tabular&#41;](tabular-models/kpis-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="02e86-107">学完本课的估计时间： **15 分钟**</span><span class="sxs-lookup"><span data-stu-id="02e86-107">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="02e86-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="02e86-108">Prerequisites</span></span>  
 <span data-ttu-id="02e86-109">本主题是表格建模教程的一部分，应当按顺序完成。</span><span class="sxs-lookup"><span data-stu-id="02e86-109">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="02e86-110">在执行本课程中的任务之前，须已完成上一课： [第 7 课：创建度量值](lesson-6-create-measures.md)。</span><span class="sxs-lookup"><span data-stu-id="02e86-110">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 7: Create Measures](lesson-6-create-measures.md).</span></span>  
  
## <a name="create-key-performance-indicators"></a><span data-ttu-id="02e86-111">创建关键绩效指标</span><span class="sxs-lookup"><span data-stu-id="02e86-111">Create Key Performance Indicators</span></span>  
  
#### <a name="to-create-an-internet-current-quarter-sales-performance-kpi"></a><span data-ttu-id="02e86-112">创建 Internet Current Quarter Sales Performance KPI</span><span class="sxs-lookup"><span data-stu-id="02e86-112">To create an Internet Current Quarter Sales Performance KPI</span></span>  
  
1.  <span data-ttu-id="02e86-113">在模型设计器中，单击“Internet Sales”\*\*\*\* 表（选项卡）。</span><span class="sxs-lookup"><span data-stu-id="02e86-113">In the model designer, click the **Internet Sales** table (tab).</span></span>  
  
2.  <span data-ttu-id="02e86-114">在度量值网格中，单击某个空单元格。</span><span class="sxs-lookup"><span data-stu-id="02e86-114">In the measure grid, click an empty cell.</span></span>  
  
3.  <span data-ttu-id="02e86-115">在表上方的公式栏中，键入以下公式：</span><span class="sxs-lookup"><span data-stu-id="02e86-115">In the formula bar, above the table, type the following formula:</span></span>  
  
     `Internet Current Quarter Sales Performance :=IFERROR([Internet Current Quarter Sales]/[Internet Previous Quarter Sales Proportion to QTD],BLANK())`  
  
     <span data-ttu-id="02e86-116">在您完成公式的建立后，按 Enter。</span><span class="sxs-lookup"><span data-stu-id="02e86-116">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="02e86-117">此度量值将用作 KPI 的基本度量值。</span><span class="sxs-lookup"><span data-stu-id="02e86-117">This measure will serve as the Base measure for the KPI.</span></span>  
  
4.  <span data-ttu-id="02e86-118">在度量值网格中，右键单击“Internet Current Quarter Sales Performance”\*\*\*\* 度量值，然后单击“创建 KPI”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02e86-118">In the measure grid, right-click the **Internet Current Quarter Sales Performance** measure, and then click **Create KPI**.</span></span>  
  
     <span data-ttu-id="02e86-119">将打开“关键绩效指标”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="02e86-119">The **Key Performance Indicator** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="02e86-120">在“关键绩效指标”\*\*\*\* 对话框的“定义目标值”\*\*\*\* 中，选择“绝对值”\*\*\*\* 选项。</span><span class="sxs-lookup"><span data-stu-id="02e86-120">In the **Key Performance Indicator** dialog box, in **Define Target Value**, select the **Absolute Value** option.</span></span>  
  
6.  <span data-ttu-id="02e86-121">在 "**绝对值**" 字段中，键入 `1.1` ，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="02e86-121">In the **Absolute Value** field, type `1.1`, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="02e86-122">在 "**定义状态阈值**" 中，在左侧 (低) 滑块 "字段中键入 `1` ，然后在右侧 (" 高) "滑块字段中，键入 `1.07` 。</span><span class="sxs-lookup"><span data-stu-id="02e86-122">In **Define Status Thresholds**, in the left (low) slider field, type `1`, and then in the right (high) slider field, type `1.07`.</span></span>  
  
8.  <span data-ttu-id="02e86-123">在“选择图标样式”中，选择菱形（红色）、三角形（黄色）、圆形（绿色）图标类型。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="02e86-123">In **Select Icon Style**, select the diamond (red), triangle (yellow), circle (green) icon type.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="02e86-124">请注意可用图标样式下方的“说明”\*\*\*\* 可扩展字段。</span><span class="sxs-lookup"><span data-stu-id="02e86-124">Notice the **Descriptions** expandable field below the available icon styles.</span></span> <span data-ttu-id="02e86-125">您可以为不同的 KPI 元素键入说明，以使它们在客户端应用程序中更易于识别。</span><span class="sxs-lookup"><span data-stu-id="02e86-125">You can type descriptions for the various KPI elements to make them more identifiable in client applications.</span></span>  
  
9. <span data-ttu-id="02e86-126">单击“确定”以完成 KPI。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="02e86-126">Click **OK** to complete the KPI.</span></span>  
  
     <span data-ttu-id="02e86-127">在度量值网格中，请注意“Internet Current Quarter Sales Performance”\*\*\*\* 度量值旁的图标。</span><span class="sxs-lookup"><span data-stu-id="02e86-127">In the measure grid, notice the icon next to the **Internet Current Quarter Sales Performance** measure.</span></span> <span data-ttu-id="02e86-128">此图标指示此度量值用作某个 KPI 的基值。</span><span class="sxs-lookup"><span data-stu-id="02e86-128">This icon indicates that this measure serves as a Base value for a KPI.</span></span>  
  
#### <a name="to-create-an-internet-current-quarter-margin-performance-kpi"></a><span data-ttu-id="02e86-129">创建 Internet Current Quarter Margin Performance KPI</span><span class="sxs-lookup"><span data-stu-id="02e86-129">To create an Internet Current Quarter Margin Performance KPI</span></span>  
  
1.  <span data-ttu-id="02e86-130">在“Internet Sales”\*\*\*\* 表的度量值网格中，单击一个空单元。</span><span class="sxs-lookup"><span data-stu-id="02e86-130">In the measure grid for the **Internet Sales** table, click an empty cell.</span></span>  
  
2.  <span data-ttu-id="02e86-131">在表上方的公式栏中，键入以下公式：</span><span class="sxs-lookup"><span data-stu-id="02e86-131">In the formula bar, above the table, type the following formula:</span></span>  
  
     `Internet Current Quarter Margin Performance :=IF([Internet Previous Quarter Margin Proportion to QTD]<>0,([Internet Current Quarter Margin]-[Internet Previous Quarter Margin Proportion to QTD])/[Internet Previous Quarter Margin Proportion to QTD],BLANK())`  
  
     <span data-ttu-id="02e86-132">在您完成公式的建立后，按 Enter。</span><span class="sxs-lookup"><span data-stu-id="02e86-132">When you have finished building the formula, press ENTER.</span></span>  
  
3.  <span data-ttu-id="02e86-133">在度量值网格中，右键单击“Internet Current Quarter Margin Performance”\*\*\*\* 度量值，然后单击“创建 KPI”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02e86-133">In the measure grid, right-click the **Internet Current Quarter Margin Performance** measure, and then click **Create KPI**.</span></span>  
  
4.  <span data-ttu-id="02e86-134">在“关键绩效指标”\*\*\*\* 对话框的“定义目标值”\*\*\*\* 中，选择“绝对值”\*\*\*\* 选项。</span><span class="sxs-lookup"><span data-stu-id="02e86-134">In the **Key Performance Indicator** dialog box, in **Define Target Value**, select the **Absolute Value** option.</span></span>  
  
5.  <span data-ttu-id="02e86-135">在 "**绝对值**" 字段中，键入 `1.25` 。</span><span class="sxs-lookup"><span data-stu-id="02e86-135">In the **Absolute Value** field, type `1.25`.</span></span>  
  
6.  <span data-ttu-id="02e86-136">在“定义状态阈值”\*\*\*\* 中，滑动左侧（低）滑块字段，直到此字段显示 **0.8**，然后滑动右侧（高）滑块字段，直到此字段显示 **1.03**。</span><span class="sxs-lookup"><span data-stu-id="02e86-136">In **Define Status Thresholds**, slide the left (low) slider field until the field displays **0.8**, and then slide the right (high) slider field, until the field displays **1.03**.</span></span>  
  
7.  <span data-ttu-id="02e86-137">在“选择图标样式”中，选择菱形（红色）、三角形（黄色）、圆形（绿色）图标类型，并单击“确定”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="02e86-137">In **Select Icon Style**, select the diamond (red), triangle (yellow), circle (green) icon type, and then click **OK**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="02e86-138">下一步</span><span class="sxs-lookup"><span data-stu-id="02e86-138">Next Step</span></span>  
 <span data-ttu-id="02e86-139">若要继续学习本教程，请转到下一课： [第 9 课：创建透视](lesson-8-create-perspectives.md)。</span><span class="sxs-lookup"><span data-stu-id="02e86-139">To continue this tutorial, go to the next lesson: [Lesson 9: Create Perspectives](lesson-8-create-perspectives.md).</span></span>  
  
  
