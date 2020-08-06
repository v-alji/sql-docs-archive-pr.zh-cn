---
title: 添加或删除指示器（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a8b1aac1-53ef-47a4-afc0-8fa866c6c480
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 186ed4f5b6cf7cb239dc7c33a11089c11bccae14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691095"
---
# <a name="add-or-delete-an-indicator-report-builder-and-ssrs"></a><span data-ttu-id="d9e83-102">添加或删除指示器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="d9e83-102">Add or Delete an Indicator (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d9e83-103">指示器是以直观的形式提供单个数据值的状态的最小化仪表。</span><span class="sxs-lookup"><span data-stu-id="d9e83-103">Indicators are minimal gauges that convey the state of a single data value at a glance.</span></span> <span data-ttu-id="d9e83-104">有关它们的详细信息，请参阅 [指示器（报表生成器和 SSRS）](indicators-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e83-104">For more information about them, see [Indicators &#40;Report Builder and SSRS&#41;](indicators-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="d9e83-105">指示器通常放在表或矩阵的单元中，但您也可以通过其自身、与仪表并排或嵌入到仪表中来使用指示器。</span><span class="sxs-lookup"><span data-stu-id="d9e83-105">Indicators are commonly placed in cells in a table or matrix, but you can also use indicators by themselves, side-by-side with gauges, or embedded in gauges.</span></span>  
  
 <span data-ttu-id="d9e83-106">当您首次添加指示器时，指示器配置为默认使用百分比作为度量单位。</span><span class="sxs-lookup"><span data-stu-id="d9e83-106">When you first add an indicator, it is by default configured to use percentages as measurement units.</span></span> <span data-ttu-id="d9e83-107">百分比范围均匀分布在指示器集的各成员之间，并且由指示器表示的值的作用域为该指示器的父级（如表或矩阵）。</span><span class="sxs-lookup"><span data-stu-id="d9e83-107">The percentage ranges are evenly distributed across members of the indicator set, and the scope of values shown by the indicator is the parent of the indicator such as a table or matrix.</span></span>  
  
 <span data-ttu-id="d9e83-108">您可以更新指示器的值和状态。</span><span class="sxs-lookup"><span data-stu-id="d9e83-108">You can update the values and states of indicators.</span></span> <span data-ttu-id="d9e83-109">有关详情，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="d9e83-109">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="d9e83-110">更改指示器图标和指示器集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="d9e83-110">Change Indicator Icons and Indicator Sets &#40;Report Builder and SSRS&#41;</span></span>](change-indicator-icons-and-indicator-sets-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="d9e83-111">设置和配置度量单位（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="d9e83-111">Set and Configure Measurement Units &#40;Report Builder and SSRS&#41;</span></span>](set-and-configure-measurement-units-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="d9e83-112">设置同步作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="d9e83-112">Set Synchronization Scope &#40;Report Builder and SSRS&#41;</span></span>](set-synchronization-scope-report-builder-and-ssrs.md)  
  
 <span data-ttu-id="d9e83-113">因为指示器位于仪表面板内，所以，当您要使用 **“指示器属性”** 对话框或 **“属性”** 窗格配置指示器时，您需要选择指示器，而不是选择面板。</span><span class="sxs-lookup"><span data-stu-id="d9e83-113">Because an indicator is positioned inside the gauge panel, you need to select the indicator instead of the panel when you want to configure the indicator by using the **Indicators Properties** dialog box or the **Properties** pane.</span></span> <span data-ttu-id="d9e83-114">下图显示了指示器仪表面板中的一个选定指示器。</span><span class="sxs-lookup"><span data-stu-id="d9e83-114">The following picture shows a selected indicator in its gauge panel.</span></span>  
  
 <span data-ttu-id="d9e83-115">![rs_GaugePanelWithIndicator](../media/rs-gaugepanelwithindicator.gif "rs_GaugePanelWithIndicator")</span><span class="sxs-lookup"><span data-stu-id="d9e83-115">![rs_GaugePanelWithIndicator](../media/rs-gaugepanelwithindicator.gif "rs_GaugePanelWithIndicator")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d9e83-116">根据数据值的列宽和长度，表或矩阵单元中的文本可以换行并在多行上显示文本。</span><span class="sxs-lookup"><span data-stu-id="d9e83-116">Depending on column width and the length of data values, the text in table or matrix cells might wrap and display text on multiple lines.</span></span> <span data-ttu-id="d9e83-117">在发生此情况时，指示器图标可能会拉长和更改形状。</span><span class="sxs-lookup"><span data-stu-id="d9e83-117">When this occurs, the indicator icon might be stretched and change shape.</span></span> <span data-ttu-id="d9e83-118">这可能会降低指示器图标的可读性。</span><span class="sxs-lookup"><span data-stu-id="d9e83-118">This can make the indicator icon less readable.</span></span> <span data-ttu-id="d9e83-119">将指示器放置于矩形内可以确保其图标永远不会拉长。</span><span class="sxs-lookup"><span data-stu-id="d9e83-119">Place the indicator inside a rectangle to ensure that the icon is never stretched.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-indicator-to-a-table-or-matrix"></a><span data-ttu-id="d9e83-120">向表或矩阵添加指示器</span><span class="sxs-lookup"><span data-stu-id="d9e83-120">To add an indicator to a table or matrix</span></span>  
  
1.  <span data-ttu-id="d9e83-121">打开一个现有报表，或者创建一个新报表（其中包含具有要显示的数据的表或矩阵）。</span><span class="sxs-lookup"><span data-stu-id="d9e83-121">Open an existing report or create a new report that contains a table and matrix with the data you want to display.</span></span> <span data-ttu-id="d9e83-122">有关详细信息，请参阅[表（报表生成器和 SSRS）](tables-report-builder-and-ssrs.md)或[矩阵（报表生成器和 SSRS）](create-a-matrix-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e83-122">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="d9e83-123">在您的表或矩阵中插入列。</span><span class="sxs-lookup"><span data-stu-id="d9e83-123">Insert a column in your table or matrix.</span></span> <span data-ttu-id="d9e83-124">有关详细信息，请参阅[插入或删除列（报表生成器和 SSRS）](insert-or-delete-a-column-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e83-124">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="d9e83-125">或者，在 **“插入”** 选项卡上，单击 **“矩形”** ，然后单击新列中的单元。</span><span class="sxs-lookup"><span data-stu-id="d9e83-125">Optionally, on the **Insert** tab, click **Rectangle**, and then click a cell in the new column.</span></span>  
  
4.  <span data-ttu-id="d9e83-126">在 **“插入”** 选项卡上，单击 **“指示器”** ，然后单击新列中的单元。</span><span class="sxs-lookup"><span data-stu-id="d9e83-126">On the **Insert** tab, click **Indicator**, and then click a cell in the new column.</span></span>  
  
     <span data-ttu-id="d9e83-127">如果您向矩形添加了某一单元，则单击该单元。</span><span class="sxs-lookup"><span data-stu-id="d9e83-127">If you added a rectangle to a cell, click that cell.</span></span>  
  
5.  <span data-ttu-id="d9e83-128">在 **“选择指示器样式”** 对话框的左窗格中，单击所需的指示器类型，然后单击指示器集。</span><span class="sxs-lookup"><span data-stu-id="d9e83-128">In the **Select Indicator Style** dialog box, in the left pane, click the indicator type you want, and then click the indicator set.</span></span>  
  
6.  <span data-ttu-id="d9e83-129">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="d9e83-129">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="d9e83-130">单击指示器。</span><span class="sxs-lookup"><span data-stu-id="d9e83-130">Click the indicator.</span></span> <span data-ttu-id="d9e83-131">将打开 **“仪表数据”** 窗格。</span><span class="sxs-lookup"><span data-stu-id="d9e83-131">The **Gauge Data** pane opens.</span></span>  
  
8.  <span data-ttu-id="d9e83-132">在“值”  区域的“(未指定)”  下拉列表中，单击要将其值显示为指示器的字段。</span><span class="sxs-lookup"><span data-stu-id="d9e83-132">In the **Values** area, in the **(Unspecified)** drop-down list, click the field whose values you want to display as an indicator.</span></span>  
  
     <span data-ttu-id="d9e83-133">此指示器配置为使用默认值。</span><span class="sxs-lookup"><span data-stu-id="d9e83-133">The indicator is configured to use default values.</span></span> <span data-ttu-id="d9e83-134">默认情况下，指示器配置为使用百分比作为度量单位，并且百分比范围均匀分布在指示器的各成员之间，指示器提供的值使用最近组的作用域。</span><span class="sxs-lookup"><span data-stu-id="d9e83-134">By default, indicators are configured use percentages as measurement units and the percentage ranges are evenly distributed across the members of the indicator and the value that the indicator conveys uses the scope of the nearest group.</span></span>  
  
### <a name="to-delete-an-indicator-to-a-table-or-matrix"></a><span data-ttu-id="d9e83-135">从表或矩阵删除指示器</span><span class="sxs-lookup"><span data-stu-id="d9e83-135">To delete an indicator to a table or matrix</span></span>  
  
1.  <span data-ttu-id="d9e83-136">右键单击要删除的指示器，然后单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="d9e83-136">Right-click the indicator to delete and click **Delete**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d9e83-137">指示器可能位于包含其他指示器或仪表的仪表面板内。</span><span class="sxs-lookup"><span data-stu-id="d9e83-137">An indicator might be positioned inside a gauge panel that contains other indicators or gauges.</span></span> <span data-ttu-id="d9e83-138">如果仪表面板包含多个项，请确保单击该指示器以删除它，而不要删除仪表面板。</span><span class="sxs-lookup"><span data-stu-id="d9e83-138">If the gauge panels contain multiple items, be sure to click the indicator to delete it, not the gauge panel.</span></span> <span data-ttu-id="d9e83-139">如果单击并删除了仪表面板，则将删除该仪表面板以及其中的所有项。</span><span class="sxs-lookup"><span data-stu-id="d9e83-139">If you click and then delete the gauge panel, the gauge panels and all the items in it are deleted.</span></span>  
  
2.  <span data-ttu-id="d9e83-140">单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="d9e83-140">Click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e83-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9e83-141">See Also</span></span>  
 [<span data-ttu-id="d9e83-142">指示器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="d9e83-142">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
