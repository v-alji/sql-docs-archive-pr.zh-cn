---
title: 在仪表面板中包括指示器和仪表（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4dff9b67-b483-4c51-a822-6dbe706a6840
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b1107745f54cd94abd7507a3e9b5a706ca5402de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692735"
---
# <a name="include-indicators-and-gauges-in-a-gauge-panel-report-builder-and-ssrs"></a><span data-ttu-id="35731-102">在仪表面板中包括指示器和仪表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="35731-102">Include Indicators and Gauges in a Gauge Panel (Report Builder and SSRS)</span></span>
  <span data-ttu-id="35731-103">仪表面板是包含一个或多个仪表和指示器的顶级容器。</span><span class="sxs-lookup"><span data-stu-id="35731-103">The gauge panel is the top-level container that holds one or more gauges and indicators.</span></span> <span data-ttu-id="35731-104">指示器可以嵌入在仪表中或在仪表面板放置于仪表旁。</span><span class="sxs-lookup"><span data-stu-id="35731-104">Indicators can be embedded in gauges or placed next to them in the gauge panel.</span></span>  
  
 <span data-ttu-id="35731-105">如果指示器和仪表在仪表面板中相邻并且显示来自不同字段的数据，则您最好添加标签，以便清楚地表明仪表和指示器提供的数据。</span><span class="sxs-lookup"><span data-stu-id="35731-105">If the indicator and gauge are adjacent in the gauge panel and show data from different fields, you might want to add labels to make it clear what data the gauge and indicator convey.</span></span>  
  
 <span data-ttu-id="35731-106">可以使用表达式设置仪表和指示器选项。</span><span class="sxs-lookup"><span data-stu-id="35731-106">Gauge and indicator options can be set by using expressions.</span></span> <span data-ttu-id="35731-107">有关详细信息，请参阅[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="35731-107">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-indicator-in-a-gauge"></a><span data-ttu-id="35731-108">将指示器嵌入在仪表中</span><span class="sxs-lookup"><span data-stu-id="35731-108">To embed an indicator in a gauge</span></span>  
  
1.  <span data-ttu-id="35731-109">打开一个现有报表，或者创建一个新报表（其中包含具有要显示的数据的表或矩阵）。</span><span class="sxs-lookup"><span data-stu-id="35731-109">Open an existing report or create a new report that contains a table and matrix with the data you want to display.</span></span> <span data-ttu-id="35731-110">有关详细信息，请参阅[表（报表生成器和 SSRS）](tables-report-builder-and-ssrs.md)或[矩阵（报表生成器和 SSRS）](create-a-matrix-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="35731-110">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="35731-111">在您的表或矩阵中插入列。</span><span class="sxs-lookup"><span data-stu-id="35731-111">Insert a column in your table or matrix.</span></span> <span data-ttu-id="35731-112">有关详细信息，请参阅[插入或删除列（报表生成器和 SSRS）](insert-or-delete-a-column-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="35731-112">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="35731-113">在 **“插入”** 选项卡的 **“数据区域”** 组中，单击 **“仪表”**，然后单击新列中的单元。</span><span class="sxs-lookup"><span data-stu-id="35731-113">On the **Insert** tab, in the **Data Regions** group, click **Gauge**, and then, and then click a cell in the new column.</span></span> <span data-ttu-id="35731-114">此时将显示 **“选择仪表类型”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="35731-114">The **Select Gauge Type** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="35731-115">单击 **“径向”**。</span><span class="sxs-lookup"><span data-stu-id="35731-115">Click **Radial**.</span></span> <span data-ttu-id="35731-116">此时将选中第一个径向仪表。</span><span class="sxs-lookup"><span data-stu-id="35731-116">The first radial gauge is selected.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="35731-117">单击仪表。</span><span class="sxs-lookup"><span data-stu-id="35731-117">Click the gauge.</span></span> <span data-ttu-id="35731-118">将打开 **“仪表数据”** 窗格。</span><span class="sxs-lookup"><span data-stu-id="35731-118">The **Gauge Data** pane opens.</span></span>  
  
7.  <span data-ttu-id="35731-119">在“值”区域的“(未指定)”列表框中，单击要将其值显示在仪表中的字段\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35731-119">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display in the gauge.</span></span> <span data-ttu-id="35731-120">或者，从报表数据集拖动要使用的字段。</span><span class="sxs-lookup"><span data-stu-id="35731-120">Alternatively, drag the field to use from the report dataset.</span></span>  
  
8.  <span data-ttu-id="35731-121">右键单击仪表，单击“添加指示器”，然后单击“子级”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35731-121">Right-click the gauge, click **Add Indicator**, and then click **Child**.</span></span> <span data-ttu-id="35731-122">**“选择指示器样式”** 对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="35731-122">The **Select Indicator Style** dialog box opens.</span></span>  
  
9. <span data-ttu-id="35731-123">在 **“选择指示器样式”** 对话框的左窗格中，单击所需的指示器类型，然后单击指示器集。</span><span class="sxs-lookup"><span data-stu-id="35731-123">In the **Select Indicator Style** dialog box, in the left pane, click the indicator type you want, and then click the indicator set.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
11. <span data-ttu-id="35731-124">单击指示器。</span><span class="sxs-lookup"><span data-stu-id="35731-124">Click the indicator.</span></span> <span data-ttu-id="35731-125">将打开 **“仪表数据”** 窗格。</span><span class="sxs-lookup"><span data-stu-id="35731-125">The **Gauge Data** pane opens.</span></span>  
  
12. <span data-ttu-id="35731-126">在“值”区域的“(未指定)”列表框中，单击要将其值显示为指示器的字段\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35731-126">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display as an indicator.</span></span> <span data-ttu-id="35731-127">或者，从报表数据集拖动要使用的字段。</span><span class="sxs-lookup"><span data-stu-id="35731-127">Alternatively, drag the field to use from the report dataset.</span></span>  
  
     <span data-ttu-id="35731-128">该字段可与您在仪表中使用的字段相同或不同。</span><span class="sxs-lookup"><span data-stu-id="35731-128">The field can be the same or a different field from the one you use in the gauge.</span></span>  
  
13. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-show-an-indicator-and-gauge-side-by-side"></a><span data-ttu-id="35731-129">并排显示指示器和仪表</span><span class="sxs-lookup"><span data-stu-id="35731-129">To show an indicator and gauge side by side</span></span>  
  
1.  <span data-ttu-id="35731-130">打开一个现有报表，或者创建一个新报表（其中包含具有要显示的数据的表或矩阵）。</span><span class="sxs-lookup"><span data-stu-id="35731-130">Open an existing report or create a new report that contains a table and matrix with the data you want to display.</span></span> <span data-ttu-id="35731-131">有关详细信息，请参阅[表（报表生成器和 SSRS）](tables-report-builder-and-ssrs.md)或[矩阵（报表生成器和 SSRS）](create-a-matrix-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="35731-131">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="35731-132">在您的表或矩阵中插入列。</span><span class="sxs-lookup"><span data-stu-id="35731-132">Insert a column in your table or matrix.</span></span> <span data-ttu-id="35731-133">有关详细信息，请参阅[插入或删除列（报表生成器和 SSRS）](insert-or-delete-a-column-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="35731-133">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="35731-134">在 **“插入”** 选项卡的 **“数据区域”** 组中，单击 **“仪表”**，然后单击您插入的列中的单元。</span><span class="sxs-lookup"><span data-stu-id="35731-134">On the **Insert** tab, in the **Data Regions** group, click **Gauge**, and then click a cell in the column you inserted.</span></span> <span data-ttu-id="35731-135">将显示 **“选择仪表类型”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="35731-135">The **Select Gauge Type** dialog appears.</span></span>  
  
4.  <span data-ttu-id="35731-136">单击 **“径向”**。</span><span class="sxs-lookup"><span data-stu-id="35731-136">Click **Radial**.</span></span> <span data-ttu-id="35731-137">此时将选中第一个径向仪表。</span><span class="sxs-lookup"><span data-stu-id="35731-137">The first radial gauge is selected.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="35731-138">单击仪表。</span><span class="sxs-lookup"><span data-stu-id="35731-138">Click the gauge.</span></span> <span data-ttu-id="35731-139">将打开 **“仪表数据”** 窗格。</span><span class="sxs-lookup"><span data-stu-id="35731-139">The **Gauge Data** pane opens.</span></span>  
  
7.  <span data-ttu-id="35731-140">在“值”区域的“(未指定)”列表框中，单击要将其值显示在仪表中的字段\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35731-140">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display in the gauge.</span></span> <span data-ttu-id="35731-141">或者，从报表数据集拖动要使用的字段。</span><span class="sxs-lookup"><span data-stu-id="35731-141">Alternatively, drag the field to use from the report dataset.</span></span>  
  
8.  <span data-ttu-id="35731-142">右键单击仪表，单击“添加指示器”，然后单击“相邻”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35731-142">Right-click the gauge, click **Add Indicator**, and then click **Adjacent**.</span></span> <span data-ttu-id="35731-143">**“选择指示器样式”** 对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="35731-143">The **Select Indicator Style** dialog box opens.</span></span>  
  
9. <span data-ttu-id="35731-144">在 **“选择指示器样式”** 对话框的左窗格中，单击所需的指示器类型，然后单击指示器集。</span><span class="sxs-lookup"><span data-stu-id="35731-144">In the **Select Indicator Style** dialog box, in the left pane, click the indicator type you want, and then click the indicator set.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
11. <span data-ttu-id="35731-145">单击指示器。</span><span class="sxs-lookup"><span data-stu-id="35731-145">Click the indicator.</span></span> <span data-ttu-id="35731-146">将打开 **“仪表数据”** 窗格。</span><span class="sxs-lookup"><span data-stu-id="35731-146">The **Gauge Data** pane opens.</span></span>  
  
12. <span data-ttu-id="35731-147">在“值”区域的“(未指定)”列表框中，单击要将其值显示为指示器的字段\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35731-147">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display as an indicator.</span></span> <span data-ttu-id="35731-148">或者，从报表数据集拖动要使用的字段。</span><span class="sxs-lookup"><span data-stu-id="35731-148">Alternatively, drag the field to use from the report dataset.</span></span>  
  
     <span data-ttu-id="35731-149">该字段可与您在仪表中使用的字段相同或不同。</span><span class="sxs-lookup"><span data-stu-id="35731-149">The field can be the same or a different field from the one you use in the gauge.</span></span>  
  
13. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
14. <span data-ttu-id="35731-150">右键单击仪表面板，再单击“添加标签”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35731-150">Right-click the gauge panel and click **Add Label**.</span></span> <span data-ttu-id="35731-151">此时将向仪表面板添加一个标签。</span><span class="sxs-lookup"><span data-stu-id="35731-151">A label is added to the gauge panel.</span></span> <span data-ttu-id="35731-152">再重复一次此操作。</span><span class="sxs-lookup"><span data-stu-id="35731-152">Repeat one more time.</span></span>  
  
     <span data-ttu-id="35731-153">此时仪表面板将具有两个标签。</span><span class="sxs-lookup"><span data-stu-id="35731-153">The gauge panel has two labels.</span></span>  
  
15. <span data-ttu-id="35731-154">将每个标签拖到仪表或指示器旁边的位置。</span><span class="sxs-lookup"><span data-stu-id="35731-154">Drag each label to a location near the gauge or indicator.</span></span>  
  
16. <span data-ttu-id="35731-155">右键单击仪表旁边的标签，单击“标签属性”，然后在“文本”框中键入所需文本\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35731-155">Right-click the label near the gauge, click **Label Properties**,and type the text you want in the **Text** box.</span></span>  
  
17. <span data-ttu-id="35731-156">右键单击指示器旁边的标签，单击“标签属性”，然后在“文本”框中键入所需文本\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35731-156">Right-click the label near the indicator, click **Label Properties**,and type the text you want in the **Text** box.</span></span>  
  
18. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="35731-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35731-157">See Also</span></span>  
 [<span data-ttu-id="35731-158">指示器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="35731-158">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
