---
title: 将三维效果添加到图表（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab9625d8-6557-4a4d-8123-eefa7c066ff5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4fcd90452e32b760bc446ac5d085ed00520a2f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590072"
---
# <a name="add-3d-effects-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="ceda9-102">将三维效果添加到图表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ceda9-102">Add 3D Effects to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ceda9-103">三维 (3D) 效果可以使图表具有深度并增强视觉效果。</span><span class="sxs-lookup"><span data-stu-id="ceda9-103">Three-dimensional (3D) effects can be used to provide depth and add visual impact to your chart.</span></span> <span data-ttu-id="ceda9-104">例如，若要强调分离型饼图的某个特定切片，可以旋转并更改图表的透视，以便人们可以首先注意到该切片。</span><span class="sxs-lookup"><span data-stu-id="ceda9-104">For example, if you want to emphasize a particular slice of an exploded pie chart, you can rotate and change the perspective of the chart so that people notice that slice first.</span></span> <span data-ttu-id="ceda9-105">将三维效果应用于图表时，将会禁用所有渐变颜色和阴影类型。</span><span class="sxs-lookup"><span data-stu-id="ceda9-105">When 3D effects are applied to your chart, all gradient colors and hatching styles are disabled.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-apply-3d-effects-to-a-range-area-line-scatter-or-polar-chart"></a><span data-ttu-id="ceda9-106">将三维效果应用于范围图、面积图、折线图、散点图或极坐标图</span><span class="sxs-lookup"><span data-stu-id="ceda9-106">To apply 3D effects to a Range, Area, Line, Scatter or Polar chart</span></span>  
  
1.  <span data-ttu-id="ceda9-107">右键单击图表区域的任意位置，然后选择“三维效果”  。</span><span class="sxs-lookup"><span data-stu-id="ceda9-107">Right-click anywhere inside the chart area and select **3D Effects**.</span></span> <span data-ttu-id="ceda9-108">随即显示“图表区属性”对话框。 </span><span class="sxs-lookup"><span data-stu-id="ceda9-108">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="ceda9-109">在 **“三维选项”** 中，选择 **“启用三维”** 选项。</span><span class="sxs-lookup"><span data-stu-id="ceda9-109">In **3D Options**, select the **Enable 3D** option.</span></span>  
  
3.  <span data-ttu-id="ceda9-110">（可选）在“三维选项”  中，可以设置各种与三维角度和场景选项相关的属性。</span><span class="sxs-lookup"><span data-stu-id="ceda9-110">(Optional) In **3D Options**, you can set a variety of properties relating to 3D angles and scene options.</span></span> <span data-ttu-id="ceda9-111">有关这些属性的详细信息，请参阅 [图表中的三维效果、凹凸效果和其他效果（报表生成器和 SSRS）](chart-effects-3d-bevel-and-other-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="ceda9-111">For more information about these properties, see [3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md).</span></span>  
  
4.  <span data-ttu-id="ceda9-112">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="ceda9-112">Click **OK**.</span></span>  
  
### <a name="to-apply-3d-effects-to-a-funnel-chart"></a><span data-ttu-id="ceda9-113">将三维效果应用于漏斗图</span><span class="sxs-lookup"><span data-stu-id="ceda9-113">To apply 3D effects to a Funnel chart</span></span>  
  
1.  <span data-ttu-id="ceda9-114">右键单击图表区域的任意位置，然后选择“三维效果”  。</span><span class="sxs-lookup"><span data-stu-id="ceda9-114">Right-click anywhere inside the chart area and select **3D Effects**.</span></span> <span data-ttu-id="ceda9-115">随即显示“图表区属性”对话框。 </span><span class="sxs-lookup"><span data-stu-id="ceda9-115">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="ceda9-116">在 **“三维选项”** 中，选择 **“启用三维”** 选项。</span><span class="sxs-lookup"><span data-stu-id="ceda9-116">In **3D Options**, select the **Enable 3D** option.</span></span> <span data-ttu-id="ceda9-117">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="ceda9-117">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="ceda9-118">（可选）若要自定义漏斗图视觉外观，可以转到“属性”窗格，更改漏斗图的特定属性。</span><span class="sxs-lookup"><span data-stu-id="ceda9-118">(Optional) To customize the funnel chart visual appearance, you can go to the Properties pane and change properties specific to the funnel chart.</span></span>  
  
    1.  <span data-ttu-id="ceda9-119">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="ceda9-119">Open the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="ceda9-120">在设计图面上，单击漏斗图的任意位置。</span><span class="sxs-lookup"><span data-stu-id="ceda9-120">On the design surface, click anywhere on the funnel.</span></span> <span data-ttu-id="ceda9-121">漏斗图序列的属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="ceda9-121">The properties for the series of the funnel chart are displayed in the Properties pane.</span></span>  
  
    3.  <span data-ttu-id="ceda9-122">在 **“常规”** 部分，展开 **CustomAttributes** 节点。</span><span class="sxs-lookup"><span data-stu-id="ceda9-122">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
    4.  <span data-ttu-id="ceda9-123">在 **Funnel3DDrawingStyle** 属性中，选择以圆形或正方形显示漏斗。</span><span class="sxs-lookup"><span data-stu-id="ceda9-123">For the **Funnel3DDrawingStyle** property, select whether the funnel will be shown with as circular or square.</span></span>  
  
    5.  <span data-ttu-id="ceda9-124">对于 **Funnel3DRotationAngle** 属性，设置介于 -10 和 10 之间的值。</span><span class="sxs-lookup"><span data-stu-id="ceda9-124">For the **Funnel3DRotationAngle** property, set a value between -10 and 10.</span></span> <span data-ttu-id="ceda9-125">该值决定三维漏斗图显示的倾斜度。</span><span class="sxs-lookup"><span data-stu-id="ceda9-125">This will determine the degree of tilt that will be displayed on the 3D funnel chart.</span></span>  
  
### <a name="to-apply-3d-effects-to-a-pie-chart"></a><span data-ttu-id="ceda9-126">将三维效果应用于饼图</span><span class="sxs-lookup"><span data-stu-id="ceda9-126">To apply 3D effects to a Pie chart</span></span>  
  
1.  <span data-ttu-id="ceda9-127">右键单击图表区的任意位置，然后选择“三维效果”。</span><span class="sxs-lookup"><span data-stu-id="ceda9-127">Right-click anywhere inside the chart area and select 3D Effects.</span></span> <span data-ttu-id="ceda9-128">随即显示“图表区属性”对话框。 </span><span class="sxs-lookup"><span data-stu-id="ceda9-128">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="ceda9-129">在 **“三维选项”** 中，选择 **“启用三维”** 选项。</span><span class="sxs-lookup"><span data-stu-id="ceda9-129">In **3D Options**, select the **Enable 3D** option.</span></span> <span data-ttu-id="ceda9-130">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="ceda9-130">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="ceda9-131">（可选）在“旋转”中，键入代表饼图水平旋转的整数值  。</span><span class="sxs-lookup"><span data-stu-id="ceda9-131">(Optional) In **Rotation**, type an integer value that represents the horizontal rotation of the pie chart.</span></span>  
  
4.  <span data-ttu-id="ceda9-132">（可选）在“倾角”中，键入代表饼图垂直倾斜旋转的整数值  。</span><span class="sxs-lookup"><span data-stu-id="ceda9-132">(Optional) In **Inclination**, type an integer value that represents the vertical tilt rotation of the pie chart.</span></span>  
  
5.  <span data-ttu-id="ceda9-133">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="ceda9-133">Click **OK**.</span></span>  
  
### <a name="to-apply-3d-effects-to-a-bar-or-column-chart"></a><span data-ttu-id="ceda9-134">将三维效果应用于条形图或柱形图</span><span class="sxs-lookup"><span data-stu-id="ceda9-134">To apply 3D effects to a Bar or Column chart</span></span>  
  
1.  <span data-ttu-id="ceda9-135">右键单击图表区域的任意位置，然后选择“三维效果”  。</span><span class="sxs-lookup"><span data-stu-id="ceda9-135">Right-click anywhere inside the chart area and select **3D Effects**.</span></span> <span data-ttu-id="ceda9-136">随即显示“图表区属性”对话框。 </span><span class="sxs-lookup"><span data-stu-id="ceda9-136">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="ceda9-137">选择 **“启用三维”** 选项。</span><span class="sxs-lookup"><span data-stu-id="ceda9-137">Select the **Enable 3D** option.</span></span> <span data-ttu-id="ceda9-138">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="ceda9-138">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="ceda9-139">（可选）选择“启用序列聚类分析”选项  。</span><span class="sxs-lookup"><span data-stu-id="ceda9-139">(Optional) Select the **Enable series clustering** option.</span></span> <span data-ttu-id="ceda9-140">如果图表包含多个条形图序列或柱形图序列，此选项会将该序列显示为聚集。</span><span class="sxs-lookup"><span data-stu-id="ceda9-140">If your chart contains multiple bar or column chart series, this option will display the series as clustered.</span></span> <span data-ttu-id="ceda9-141">默认情况下，会并行显示多个条序列或列序列。</span><span class="sxs-lookup"><span data-stu-id="ceda9-141">By default, multiple bar or column series are shown side-by-side.</span></span>  
  
4.  <span data-ttu-id="ceda9-142">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="ceda9-142">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="ceda9-143">（可选）若要将圆柱效果添加到条形图或柱形图，请按以下步骤操作：</span><span class="sxs-lookup"><span data-stu-id="ceda9-143">(Optional) To add cylinder effects to a bar or column chart, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="ceda9-144">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="ceda9-144">Open the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="ceda9-145">在设计图面上，单击序列中的任意条。</span><span class="sxs-lookup"><span data-stu-id="ceda9-145">On the design surface, click any of the bars in the series.</span></span> <span data-ttu-id="ceda9-146">序列的属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="ceda9-146">The properties for the series are displayed in the Properties pane.</span></span>  
  
    3.  <span data-ttu-id="ceda9-147">在 **“常规”** 部分，展开 **CustomAttributes** 节点。</span><span class="sxs-lookup"><span data-stu-id="ceda9-147">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
    4.  <span data-ttu-id="ceda9-148">对于 **DrawingStyle** 属性，指定 **“柱状”** 值。</span><span class="sxs-lookup"><span data-stu-id="ceda9-148">For the **DrawingStyle** property, specify the **Cylinder** value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceda9-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ceda9-149">See Also</span></span>  
 <span data-ttu-id="ceda9-150">[图表中的三维效果、凹凸效果和其他效果（报表生成器和 SSRS）](chart-effects-3d-bevel-and-other-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="ceda9-150">[3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span></span>  
 <span data-ttu-id="ceda9-151">[设置图表格式（报表生成器和 SSRS）](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ceda9-151">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ceda9-152">图表&#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ceda9-152">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
