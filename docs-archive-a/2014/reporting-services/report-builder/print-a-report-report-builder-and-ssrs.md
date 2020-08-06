---
title: 打印报表（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b96936c9-c387-41a9-8c19-6eb325769ffd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe029019cdf9739153256db399cfa1426d3ba632
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580024"
---
# <a name="print-a-report-report-builder-and-ssrs"></a><span data-ttu-id="c7d9f-102">打印报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c7d9f-102">Print a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c7d9f-103">在将报表保存到报表服务器之后，可以通过浏览器、报表管理器或用于查看导出报表的任意应用程序查看和打印报表。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-103">After you save a report to a report server, you can view and print the report from a browser, Report Manager, or any application that you use to view an exported report.</span></span> <span data-ttu-id="c7d9f-104">在保存报表之前，可以在预览报表时打印它。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-104">Before saving a report, you can print it when you preview it.</span></span>  
  
 <span data-ttu-id="c7d9f-105">打印报表时，可以指定所用纸张的大小。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-105">When you print a report, you can specify the size of the paper to use.</span></span> <span data-ttu-id="c7d9f-106">纸张的大小决定了报表的页数以及适合每一页的报表数据。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-106">The size of the paper determines the number of pages in a report and which report data fits on each page.</span></span> <span data-ttu-id="c7d9f-107">纸张的大小仅影响通过硬分页呈现器（PDF、Image 和 Print）呈现的报表。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-107">Paper size affects only reports that are rendered with hard page-break renders: PDF, Image, and Print.</span></span> <span data-ttu-id="c7d9f-108">设置纸张大小不影响其他呈现器。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-108">Setting the paper size has no effect on other renderers.</span></span> <span data-ttu-id="c7d9f-109">有关详细信息，请参阅[呈现行为（报表生成器和 SSRS）](../report-design/rendering-behaviors-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-109">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="c7d9f-110">在报表生成器的“报表查看器”工具栏或报表设计器的“预览”中，可以将报表导出到硬分页呈现器或单击“打印”按钮来打印报表的副本。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-110">From the report viewer toolbar in Report Manager or in preview in Report Builder, you can export a report to a hard page-break renderer or click the Print button to print a copy of the report.</span></span> <span data-ttu-id="c7d9f-111">您可能需要设置纸张大小或其他页面设置属性。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-111">You might need to set the paper size or other page setup properties.</span></span> <span data-ttu-id="c7d9f-112">使用 **“报表属性”** 对话框可以更改页面设置属性，包括纸张大小。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-112">Use the **Report Properties** dialog box to change page setup properties, including paper size.</span></span>  
  
 <span data-ttu-id="c7d9f-113">可以在以下两个不同位置指定打印页边距：在设计模式下和在运行模式下。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-113">You can specify print page margins in two different locations: in design mode and in run mode.</span></span>  
  
-   <span data-ttu-id="c7d9f-114">**设计模式。**</span><span class="sxs-lookup"><span data-stu-id="c7d9f-114">**Design mode.**</span></span> <span data-ttu-id="c7d9f-115">如果设计模式下设置页边距，则保存报表时，这些设置会保存在报表定义中。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-115">When you set page margins in design mode, these settings are saved in the report definition when you save the report.</span></span>  
  
-   <span data-ttu-id="c7d9f-116">**运行模式。**</span><span class="sxs-lookup"><span data-stu-id="c7d9f-116">**Run mode.**</span></span> <span data-ttu-id="c7d9f-117">如果在运行模式下设置页边距，则此信息不会保存在报表定义中。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-117">When you set page margins in run mode, this information is not saved in the report definition.</span></span> <span data-ttu-id="c7d9f-118">下一次打印报表时，将从报表定义中获取设置，除非再次指定打印边距。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-118">The next time you print the report, you will get the settings from the report definition, unless you indicate your print margins again.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7d9f-119">在设计模式或运行模式下不会显示打印边距。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-119">Print margins are not displayed in design or run modes.</span></span> <span data-ttu-id="c7d9f-120">报表的设计图面区域和打印区域之间没有任何关系。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-120">There is no relationship between the design surface area and the print area of your report.</span></span> <span data-ttu-id="c7d9f-121">若要在运行模式下查看打印边距，请在功能区的 **“运行”** 选项卡上单击“打印布局”。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-121">To see print margins, in run mode, click Print Layout on the **Run** tab on the Ribbon.</span></span>  
  
 <span data-ttu-id="c7d9f-122">有关报表分页的详细信息，请参阅 [Reporting Services 中的分页（报表生成器和 SSRS）](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-122">For more information about report paging, see [Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-print-a-report-in-report-builder"></a><span data-ttu-id="c7d9f-123">在报表生成器中打印报表</span><span class="sxs-lookup"><span data-stu-id="c7d9f-123">To print a report in Report Builder</span></span>  
  
1.  <span data-ttu-id="c7d9f-124">打开报表。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-124">Open a report.</span></span>  
  
2.  <span data-ttu-id="c7d9f-125">在 "主页" 选项卡上，单击 "**运行**"。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-125">On the Home tab, click **Run**.</span></span>  
  
3.  <span data-ttu-id="c7d9f-126">（可选）单击“打印布局”以查看报表打印时的显示形式\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-126">(optional) Click **Print Layout** to see how the report will look when it is printed.</span></span>  
  
4.  <span data-ttu-id="c7d9f-127">（可选）单击“页面设置”以设置纸张、方向和边距\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-127">(optional) Click **Page Setup** to set paper, orientation, and margins.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7d9f-128">以上各项的默认值均源自在“设计”视图中设置的报表属性。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-128">The default values for these come from the report properties, which are set in Design view.</span></span> <span data-ttu-id="c7d9f-129">此处您在 **“页面设置”** 对话框中所设置的值仅适用于此次会话。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-129">The values you set here in the **Page Setup** dialog box are for this session only.</span></span> <span data-ttu-id="c7d9f-130">当关闭此报表并将其重新打开时，它将再次恢复默认值。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-130">When you close this report and reopen it, it will have the default values again.</span></span>  
  
5.  <span data-ttu-id="c7d9f-131">单击 **“打印”**。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-131">Click **Print**.</span></span>  
  
6.  <span data-ttu-id="c7d9f-132">在 **“打印”** 对话框中，选择打印机并指定其他打印选项。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-132">In the **Print** dialog box, select a printer and specify other printing options.</span></span>  
  
### <a name="to-print-a-report-from-a-web-browser-application"></a><span data-ttu-id="c7d9f-133">从 Web 浏览器应用程序打印报表</span><span class="sxs-lookup"><span data-stu-id="c7d9f-133">To print a report from a Web browser application</span></span>  
  
1.  <span data-ttu-id="c7d9f-134">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-134">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="c7d9f-135">在报表管理器中，导航到要打印的报表。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-135">In Report Manager, navigate to the report that you want to print.</span></span> <span data-ttu-id="c7d9f-136">打开该报表。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-136">Open the report.</span></span>  
  
3.  <span data-ttu-id="c7d9f-137">在报表顶部的工具栏上，单击 **“打印”** 。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-137">On the toolbar at the top of the report, click **Print**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7d9f-138">首次打印 HTML 报表时，报表服务器会提示您安装用于打印的 ActiveX 控件。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-138">The first time you print an HTML report, the report server prompts you to install an ActiveX control used for printing.</span></span> <span data-ttu-id="c7d9f-139">必须安装并配置该控件才能进行打印。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-139">You must install and configure the control to print.</span></span>  
  
4.  <span data-ttu-id="c7d9f-140">在 **“打印”** 对话框中，选择打印机，再单击 **“打印”** 。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-140">In the **Print** dialog box, select a printer, and then click **Prin**t.</span></span>  
  
### <a name="to-print-a-report-from-other-applications"></a><span data-ttu-id="c7d9f-141">从其他应用程序打印报表</span><span class="sxs-lookup"><span data-stu-id="c7d9f-141">To print a report from other applications</span></span>  
  
1.  <span data-ttu-id="c7d9f-142">在报表管理器中，导航到要打印的报表。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-142">In Report Manager, navigate to the report that you want to print.</span></span> <span data-ttu-id="c7d9f-143">打开该报表。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-143">Open the report.</span></span>  
  
2.  <span data-ttu-id="c7d9f-144">在报表顶部的工具栏上，选择呈现格式，再单击 **“导出”** 。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-144">On the toolbar at the top of the report, select a rendering format, and then click **Export**.</span></span> <span data-ttu-id="c7d9f-145">报表在与该呈现格式相对应的查看器应用程序中打开。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-145">The report opens in a viewer application that corresponds to the rendering format.</span></span>  
  
     <span data-ttu-id="c7d9f-146">例如，如果选择 PDF，则报表在 Adobe Acrobat Reader 中打开。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-146">For example, if you select PDF, the report opens in Adobe Acrobat Reader.</span></span>  
  
3.  <span data-ttu-id="c7d9f-147">在该程序的 **“文件”** 菜单上，单击 **“打印”** 。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-147">On the **File** menu in that program, click **Print**.</span></span>  
  
### <a name="to-change-paper-size"></a><span data-ttu-id="c7d9f-148">更改纸张大小</span><span class="sxs-lookup"><span data-stu-id="c7d9f-148">To change paper size</span></span>  
  
1.  <span data-ttu-id="c7d9f-149">右键单击表体外部区域，然后单击“报表属性”  。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-149">Right-click outside of the report body and click **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="c7d9f-150">在 **“页面设置”** 中，从 **“纸张大小”** 列表选择一个值。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-150">In **Page Setup**, select a value from the **Paper Size** list.</span></span> <span data-ttu-id="c7d9f-151">每一选项都会填充 **“宽度”** 和 **“高度”** 属性。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-151">Each option populates the **Width** and **Height** properties.</span></span> <span data-ttu-id="c7d9f-152">您也可以通过在 **“宽度”** 和 **“高度”** 框中键入数值，来指定自定义大小。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-152">You can also specify a custom size by typing numeric values in the **Width** and **Height** boxes.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7d9f-153">大小值的默认单位由用户的区域设置决定。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-153">Size values have a default unit based on the user's locale settings.</span></span> <span data-ttu-id="c7d9f-154">若要指定其他单位，请在提供的数字值后面键入一个物理单位指示符，例如 cm、mm、pt 或 pc。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-154">To designate a different unit, type a physical unit designator such as cm, mm, pt, or pc after the numeric value.</span></span>  
  
### <a name="to-set-page-margins-in-design-mode"></a><span data-ttu-id="c7d9f-155">在设计模式下设置页边距</span><span class="sxs-lookup"><span data-stu-id="c7d9f-155">To set page margins in design mode</span></span>  
  
-   <span data-ttu-id="c7d9f-156">右键单击设计图面周围的蓝色区域，单击“报表属性”，然后单击“页面设置”   页。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-156">Right-click the blue area around the design surface, click **Report Properties**, and then click the **Page Setup** page.</span></span>  
  
### <a name="to-set-page-margins-in-run-mode"></a><span data-ttu-id="c7d9f-157">在运行模式下设置页边距</span><span class="sxs-lookup"><span data-stu-id="c7d9f-157">To set page margins in run mode</span></span>  
  
-   <span data-ttu-id="c7d9f-158">在 **“运行”** 选项卡上单击 **“页面设置”** 。</span><span class="sxs-lookup"><span data-stu-id="c7d9f-158">Click **Page Setup** on the **Run** tab.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d9f-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7d9f-159">See Also</span></span>  
 <span data-ttu-id="c7d9f-160">[打印报表（报表生成器和 SSRS）](print-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c7d9f-160">[Print Reports &#40;Report Builder and SSRS&#41;](print-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c7d9f-161">[导出报表 &#40;报表生成器和 SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c7d9f-161">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c7d9f-162">[“报表属性”对话框，页面设置（报表生成器）](../report-properties-dialog-box-page-setup-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="c7d9f-162">[Report Properties Dialog Box, Page Setup &#40;Report Builder&#41;](../report-properties-dialog-box-page-setup-report-builder.md) </span></span>  
 [<span data-ttu-id="c7d9f-163">报表设计视图（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="c7d9f-163">Report Design View &#40;Report Builder&#41;</span></span>](report-design-view-report-builder.md)  
  
  
