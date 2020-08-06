---
title: 第 6 课：添加分组和总计 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e3d61228-2aa4-42cc-955e-602dbf3406a7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b98798005a984edf00aff469d4c1b09aa2e34d98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590570"
---
# <a name="lesson-6-adding-grouping-and-totals-reporting-services"></a><span data-ttu-id="91d24-102">第 6 课：添加分组和总计 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="91d24-102">Lesson 6: Adding Grouping and Totals (Reporting Services)</span></span>
  <span data-ttu-id="91d24-103">向报表中添加分组和总计以便组织和汇总数据。</span><span class="sxs-lookup"><span data-stu-id="91d24-103">Add grouping and totals to your report to organize and summarize your data.</span></span>  
  
 <span data-ttu-id="91d24-104">有关向报表添加运行总计的信息，请参阅：[将总计添加到 Reporting Services (SSRS) 报表](https://www.tutorialgateway.org/add-total-and-subtotal-to-ssrs-report/)中。</span><span class="sxs-lookup"><span data-stu-id="91d24-104">For information about adding running totals to reports, see: [Adding totals to Reporting Services (SSRS) reports](https://www.tutorialgateway.org/add-total-and-subtotal-to-ssrs-report/).</span></span>  
  
 <span data-ttu-id="91d24-105">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="91d24-105">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="91d24-106">对报表中的数据进行分组</span><span class="sxs-lookup"><span data-stu-id="91d24-106">To group data in a report</span></span>](#bkmk_groupdata)  
  
-   [<span data-ttu-id="91d24-107">向报表添加总计</span><span class="sxs-lookup"><span data-stu-id="91d24-107">To add totals to a report</span></span>](#bkmk_addtotals)  
  
-   [<span data-ttu-id="91d24-108">向报表添加每日总计</span><span class="sxs-lookup"><span data-stu-id="91d24-108">To add a daily total to a report</span></span>](#bkmk_adddailytotal)  
  
-   [<span data-ttu-id="91d24-109">向报表添加总计</span><span class="sxs-lookup"><span data-stu-id="91d24-109">To add a grand total to a report</span></span>](#bkmk_addgrandtotal)  
  
-   [<span data-ttu-id="91d24-110">若要将报表发布到报表服务器 (可选) </span><span class="sxs-lookup"><span data-stu-id="91d24-110">To Publish the Report to the Report Server (Optional)</span></span>](#bkmk_publishreport)  
  
##  <a name="to-group-data-in-a-report"></a><a name="bkmk_groupdata"></a><span data-ttu-id="91d24-111">对报表中的数据进行分组</span><span class="sxs-lookup"><span data-stu-id="91d24-111">To group data in a report</span></span>  
  
1.  <span data-ttu-id="91d24-112">单击 **“设计”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="91d24-112">Click the **Design** tab.</span></span>  
  
2.  <span data-ttu-id="91d24-113">如果看不到 "**行组**" 窗格，请右键单击设计图面，然后单击 "**查看**"，然后单击 "**分组**"。</span><span class="sxs-lookup"><span data-stu-id="91d24-113">If you do not see the **Row Groups** pane , right-click the design surface and click **view** and then click **Grouping**.</span></span>  
  
3.  <span data-ttu-id="91d24-114">从“报表数据”\*\*\*\* 窗格将 `Date` 字段拖到“行组”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="91d24-114">From the **Report Data** pane, drag the `Date` field to the **Row Groups** pane.</span></span> <span data-ttu-id="91d24-115">并将其放置到名为 **(Details)** 的行上面。</span><span class="sxs-lookup"><span data-stu-id="91d24-115">Place it above the row called **(Details)**.</span></span>  
  
     <span data-ttu-id="91d24-116">请注意，行控点中现在有一个方括号，用于显示组。</span><span class="sxs-lookup"><span data-stu-id="91d24-116">Note that the row handle now has a bracket in it, to show a group.</span></span> <span data-ttu-id="91d24-117">表现在在垂直点线的两侧各有一个 Date 列。</span><span class="sxs-lookup"><span data-stu-id="91d24-117">The table now also has two Date columns -- one on either side of a vertical dotted line.</span></span>  
  
     ![](../../2014/tutorials/media/rs-basictablegroups1design.gif "rs_BasicTableGroups1Design")  
  
4.  <span data-ttu-id="91d24-118">从“报表数据”\*\*\*\* 窗格将 `Order` 字段拖到“行组”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="91d24-118">From the **Report Data** pane, drag the `Order` field to the **Row Groups** pane.</span></span> <span data-ttu-id="91d24-119">并将其放置到 Date 下面和 **(Details)** 上面。</span><span class="sxs-lookup"><span data-stu-id="91d24-119">Place it below Date and above **(Details)**.</span></span>  
  
     <span data-ttu-id="91d24-120">请注意，行控点中现在有两个方括号，用于显示两个组。</span><span class="sxs-lookup"><span data-stu-id="91d24-120">Note that the row handle now has two brackets in it, to show two groups.</span></span> <span data-ttu-id="91d24-121">该表现在也有两 `Order` 列。</span><span class="sxs-lookup"><span data-stu-id="91d24-121">The table now has two `Order` columns, too.</span></span>  
  
5.  <span data-ttu-id="91d24-122">删除两根线条 右侧 的原始 Date 和 **Order** 列。</span><span class="sxs-lookup"><span data-stu-id="91d24-122">Delete the original Date and Order columns to the **right** of the double line.</span></span> <span data-ttu-id="91d24-123">这将删除该单个记录值，以便仅显示组值。</span><span class="sxs-lookup"><span data-stu-id="91d24-123">This removes this individual record values so that only the group value is displayed.</span></span> <span data-ttu-id="91d24-124">选择并右键单击两个列的列句柄，然后单击“删除列”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="91d24-124">Select the column handles for the two columns, right-click and click **Delete Columns**.</span></span>  
  
     <span data-ttu-id="91d24-125">![选择要删除的列](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "选择要删除的列")</span><span class="sxs-lookup"><span data-stu-id="91d24-125">![Select columns to delete](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "Select columns to delete")</span></span>  
  
     <span data-ttu-id="91d24-126">您可以重新设置列标题和日期的格式。</span><span class="sxs-lookup"><span data-stu-id="91d24-126">You can format the column headers and date again.</span></span>  
  
6.  <span data-ttu-id="91d24-127">切换到 **“预览”** 选项卡以预览报表。</span><span class="sxs-lookup"><span data-stu-id="91d24-127">Switch to the **Preview** tab to preview the report.</span></span> <span data-ttu-id="91d24-128">其外观应与下图类似：</span><span class="sxs-lookup"><span data-stu-id="91d24-128">It should look similar to the following illustration:</span></span>  
  
     <span data-ttu-id="91d24-129">![先按日期后按订单分组的表](../../2014/tutorials/media/rs-basictablegroupspreview.gif "先按日期后按订单分组的表")</span><span class="sxs-lookup"><span data-stu-id="91d24-129">![Table grouped by date and then order](../../2014/tutorials/media/rs-basictablegroupspreview.gif "Table grouped by date and then order")</span></span>  
  
##  <a name="to-add-totals-to-a-report"></a><a name="bkmk_addtotals"></a><span data-ttu-id="91d24-130">向报表添加总计</span><span class="sxs-lookup"><span data-stu-id="91d24-130">To add totals to a report</span></span>  
  
1.  <span data-ttu-id="91d24-131">切换到“设计”视图。</span><span class="sxs-lookup"><span data-stu-id="91d24-131">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="91d24-132">右键单击包含 `[LineTotal]` 字段的数据区域单元，并单击“添加总计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="91d24-132">Right-click the data region cell that contains the field `[LineTotal]`, and click **Add Total**.</span></span>  
  
     <span data-ttu-id="91d24-133">这将添加一个带有每个订单的美元总金额的行。</span><span class="sxs-lookup"><span data-stu-id="91d24-133">This adds a row with a sum of the dollar amount for each order.</span></span>  
  
3.  <span data-ttu-id="91d24-134">右键单击包含 `[Qty]` 字段的单元，并单击“添加总计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="91d24-134">Right-click the cell that contains the field `[Qty]`, and click **Add Total**.</span></span>  
  
     <span data-ttu-id="91d24-135">这将向总计行添加每个订单的总数量。</span><span class="sxs-lookup"><span data-stu-id="91d24-135">This adds a sum of the quantity for each order to the totals row.</span></span>  
  
4.  <span data-ttu-id="91d24-136">在 `Sum[Qty]`左侧的空单元中，键入标签“**Order Total**”。</span><span class="sxs-lookup"><span data-stu-id="91d24-136">In the empty cell to the left of `Sum[Qty]`, type the label "**Order Total"**.</span></span>  
  
5.  <span data-ttu-id="91d24-137">可以向总计行添加背景色。</span><span class="sxs-lookup"><span data-stu-id="91d24-137">You can add a background color to the totals row.</span></span> <span data-ttu-id="91d24-138">选择两个累加求和单元和标签单元。</span><span class="sxs-lookup"><span data-stu-id="91d24-138">Select the two sum cells and the label cell.</span></span>  
  
6.  <span data-ttu-id="91d24-139">在 **“格式”** 菜单上，依次单击 **“背景色”**、 **“浅灰色”** 和 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="91d24-139">On the **Format** menu, click **Background Color**, click **Light Gray**, and click **OK**.</span></span>  
  
     <span data-ttu-id="91d24-140">![设计视图：带有订单总计的基本表](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "设计视图：带有订单总计的基本表")</span><span class="sxs-lookup"><span data-stu-id="91d24-140">![Design view: Basic table with order total](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "Design view: Basic table with order total")</span></span>  
  
##  <a name="to-add-a-daily-total-to-a-report"></a><a name="bkmk_adddailytotal"></a><span data-ttu-id="91d24-141">向报表添加每日总计</span><span class="sxs-lookup"><span data-stu-id="91d24-141">To add a daily total to a report</span></span>  
  
1.  <span data-ttu-id="91d24-142">右键单击 Order 单元，指向“添加总计”\*\*\*\*，并单击“晚于”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="91d24-142">Right-click the Order cell, point to **Add Total**, and click **After**.</span></span>  
  
     <span data-ttu-id="91d24-143">这会添加一个新行，其中包含每天的数量和美元量的总和，以及 Order 列中的标签 "**Total**"。</span><span class="sxs-lookup"><span data-stu-id="91d24-143">This adds a new row containing sums of the quantity and dollar amount for each day, and the label "**Total**" in the Order column.</span></span>  
  
2.  <span data-ttu-id="91d24-144">在相同单元中，在 **Total** 单词之前键入 **Daily** 单词，使其显示为 **Daily Total**。</span><span class="sxs-lookup"><span data-stu-id="91d24-144">Type the word **Daily** before the word **Total** in the same cell, so it reads **Daily Total**.</span></span>  
  
3.  <span data-ttu-id="91d24-145">选定 **Daily Total** 单元、两个 **Sum** 单元及其之间的空单元。</span><span class="sxs-lookup"><span data-stu-id="91d24-145">Select the **Daily Total** cell, the two **Sum** cells and the empty cell between them.</span></span>  
  
4.  <span data-ttu-id="91d24-146">在 **“格式”** 菜单上，依次单击 **“背景色”**、 **“橙色”** 和 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="91d24-146">On the **Format** menu, click **Background Color**, click **Orange**, and click **OK**.</span></span>  
  
     ![](../../2014/tutorials/media/rs-basictablesumdaytotaldesign.gif "rs_BasicTableSumDayTotalDesign")  
  
##  <a name="to-add-a-grand-total-to-a-report"></a><a name="bkmk_addgrandtotal"></a><span data-ttu-id="91d24-147">向报表添加总计</span><span class="sxs-lookup"><span data-stu-id="91d24-147">To add a grand total to a report</span></span>  
  
1.  <span data-ttu-id="91d24-148">右键单击“Date”单元，指向“添加总计”\*\*\*\*，并单击“晚于”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="91d24-148">Right-click the Date cell, point to **Add Total**, and click **After**.</span></span>  
  
     <span data-ttu-id="91d24-149">这将添加一个新行，其中包含整个报表的数量和美元金额的总和，以及列中的**总**标签 `Date` 。</span><span class="sxs-lookup"><span data-stu-id="91d24-149">This adds a new row containing sums of the quantity and dollar amount for the entire report, and the **Total** label in the `Date` column.</span></span>  
  
2.  <span data-ttu-id="91d24-150">在相同单元中，在 **Total** 单词之前键入 **Grand** 单词，使其显示为 **Grand Total**。</span><span class="sxs-lookup"><span data-stu-id="91d24-150">Type the word **Grand** before the word **Total** in the same cell, so it reads **Grand Total**.</span></span>  
  
3.  <span data-ttu-id="91d24-151">选定 **Grand Total** 单元、两个 **Sum** 单元及其之间的空单元。</span><span class="sxs-lookup"><span data-stu-id="91d24-151">Select the **Grand Total** cell, the two **Sum** cells and the empty cells between them.</span></span>  
  
4.  <span data-ttu-id="91d24-152">在 **“格式”** 菜单上，依次单击 **“背景色”**、 **“浅蓝色”** 和 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="91d24-152">On the **Format** menu, click **Background Color**, click **Light Blue**, and click **OK**.</span></span>  
  
     <span data-ttu-id="91d24-153">![设计视图：基本表中的总计](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "设计视图：基本表中的总计")</span><span class="sxs-lookup"><span data-stu-id="91d24-153">![Design view: Grand total in basic table](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "Design view: Grand total in basic table")</span></span>  
  
5.  <span data-ttu-id="91d24-154">单击“预览”。</span><span class="sxs-lookup"><span data-stu-id="91d24-154">Click Preview.</span></span>  
  
     <span data-ttu-id="91d24-155">最后一页的外观应与下图相似：</span><span class="sxs-lookup"><span data-stu-id="91d24-155">The last page should look something like this:</span></span>  
  
     <span data-ttu-id="91d24-156">![预览：带有总计的基本表](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "预览：带有总计的基本表")</span><span class="sxs-lookup"><span data-stu-id="91d24-156">![Preview: Basic table with grand total](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "Preview: Basic table with grand total")</span></span>  
  
##  <a name="to-publish-the-report-to-the-report-server-optional"></a><a name="bkmk_publishreport"></a><span data-ttu-id="91d24-157">若要将报表发布到报表服务器 (可选) </span><span class="sxs-lookup"><span data-stu-id="91d24-157">To Publish the Report to the Report Server (Optional)</span></span>  
  
1.  <span data-ttu-id="91d24-158">一个可选步骤是将已完成的报表发送到本机模式报表服务器上，以便您可以从报表管理器查看该报表。</span><span class="sxs-lookup"><span data-stu-id="91d24-158">An optional step is to publish the completed report to the native mode report server so you can view the report from Report Manager.</span></span>  
  
2.  <span data-ttu-id="91d24-159">在工具栏上，单击 **“项目”** ，然后单击 **“教程属性...”**。</span><span class="sxs-lookup"><span data-stu-id="91d24-159">On the toolbar click **Project** and then click **tutorial Properties...**</span></span>  
  
3.  <span data-ttu-id="91d24-160">在**TargetServerURL**中，键入 Report Server 名称的名称，例如**http:// \<servername> /reportserver**</span><span class="sxs-lookup"><span data-stu-id="91d24-160">In the **TargetServerURL** type the name of the name of your report server, for example **http://\<servername>/reportserver**</span></span>  
  
4.  <span data-ttu-id="91d24-161">单击 **“确定”**</span><span class="sxs-lookup"><span data-stu-id="91d24-161">Click **OK**</span></span>  
  
5.  <span data-ttu-id="91d24-162">在工具栏上，单击 **“生成”** ，然后单击 **“部署教程”**。</span><span class="sxs-lookup"><span data-stu-id="91d24-162">On the toolbar click **Build** and then click **Deploy tutorial**.</span></span>  
  
     <span data-ttu-id="91d24-163">如果您在输出窗口中看到如下消息，则指示成功部署。</span><span class="sxs-lookup"><span data-stu-id="91d24-163">If you see a message similar to the following in the output window, it indicates a successful deployment.</span></span>  
  
    > <span data-ttu-id="91d24-164">------ Build started: Project: tutorial, Configuration: Debug ------Skipping 'Sales Orders.rdl'.</span><span class="sxs-lookup"><span data-stu-id="91d24-164">------ Build started: Project: tutorial, Configuration: Debug ------Skipping 'Sales Orders.rdl'.</span></span> <span data-ttu-id="91d24-165">项是最新的。生成完成--0 个错误，------部署开始时出现0个警告：项目：教程，配置： Debug------部署到 http:// \<server name> /reportserverDeploying 报表 "/Tutorial/Sales 订单"。部署完成-0 个错误，0个警告 = = = = = = = = = = 生成：成功或最新，0失败，0已跳过 = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =</span><span class="sxs-lookup"><span data-stu-id="91d24-165">Item is up to date.Build complete -- 0 errors, 0 warnings------ Deploy started: Project: tutorial, Configuration: Debug ------Deploying to http://\<server name>/reportserverDeploying report '/tutorial/Sales Orders'.Deploy complete -- 0 errors, 0 warnings========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==================== Deploy: 1 succeeded, 0 failed, 0 skipped ==========</span></span>  
  
     <span data-ttu-id="91d24-166">如果您看到如下错误消息，则确认您对报表服务器的权限并且已使用管理员权限启动了 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="91d24-166">If you see an error message similar to the following, verify you have permissions on the report server and you have started [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] with administrator privileges.</span></span>  
  
    > <span data-ttu-id="91d24-167">"为用户 ' XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX<的权限 \\ \> 不足，无法执行此操作"</span><span class="sxs-lookup"><span data-stu-id="91d24-167">"The permissions granted to user 'XXXXXXXX\\<your user name\>' are insufficient for performing this operation"</span></span>  
  
6.  <span data-ttu-id="91d24-168">以管理员权限启动报表管理器，例如，右键单击 Internet Explorer 图标，然后单击 "以**管理员身份运行**"。</span><span class="sxs-lookup"><span data-stu-id="91d24-168">Start Report Manager with administrator privileges, for example, right-click the icon for Internet Explorer and click **Run as administrator**.</span></span>  
  
     <span data-ttu-id="91d24-169">浏览至报表管理器 URL，例如： `http://<server name>/reports`。</span><span class="sxs-lookup"><span data-stu-id="91d24-169">Browse to the Report Manager URL, for example: `http://<server name>/reports`.</span></span>  
  
7.  <span data-ttu-id="91d24-170">浏览到包含该报表的文件夹，并单击报表 `Sales Orders` 的名称以在浏览器中查看呈现的报表。</span><span class="sxs-lookup"><span data-stu-id="91d24-170">Browse to the folder that contains the report and click the name of the report `Sales Orders` to view the rendered report in the browser.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="91d24-171">后续步骤</span><span class="sxs-lookup"><span data-stu-id="91d24-171">Next Steps</span></span>  
 <span data-ttu-id="91d24-172">这样，您就成功完成了对“创建基本表报表”教程的学习。</span><span class="sxs-lookup"><span data-stu-id="91d24-172">You have successfully completed the Creating a Basic Table Report tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d24-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91d24-173">See Also</span></span>  
 [<span data-ttu-id="91d24-174">对数据进行筛选、分组和排序（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="91d24-174">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
