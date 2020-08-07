---
title: "\"操作属性\" 对话框 (报表生成器和 SSRS) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.action.f1
- "10413"
- "10504"
- sql12.rtp.rptdesigner.calculatedseriesproperties.action.f1
- sql12.rtp.rptdesigner.pictureproperties.action.f1
- sql12.rtp.rptdesigner.actionproperties.f1
- sql12.rtp.rptdesigner.charttitleproperties.action.f1
- "10133"
- "10052"
- "10147"
- sql12.rtp.rptdesigner.chartproperties.action.f1
- "10122"
- sql12.rtp.rptdesigner.serieslabelproperties.action.f1
- sql12.rtp.rptdesigner.textboxproperties.action.f1
- "10162"
- "10168"
- sql12.rtp.rptdesigner.textproperties.action.f1
- sql12.rtp.rptdesigner.placeholderproperties.action.f1
- "10250"
- "10129"
- "10244"
- sql12.rtp.rptdesigner.seriesproperties.action.f1
ms.assetid: 2c5d915b-4f97-42cf-b8f1-49ca3ff3d0f9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77b51af0763010676b95fcedb433ab963fc7fcdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588360"
---
# <a name="action-properties-dialog-box-report-builder-and-ssrs"></a><span data-ttu-id="f5510-102">“操作属性”对话框（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f5510-102">Action Properties Dialog Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f5510-103">使用 **“操作”** 对话框可以为支持链接的图表、仪表和地图元素启用超链接选项。</span><span class="sxs-lookup"><span data-stu-id="f5510-103">The **Action** dialog box can be used to enable hyperlink options for a chart, gauge, and map elements that support links.</span></span> <span data-ttu-id="f5510-104">定义一项操作，以便用户单击报表并链接到 URL、同一报表服务器或与报表服务器集成的 SharePoint 站点上的其他报表，或链接到同一报表中的其他位置。</span><span class="sxs-lookup"><span data-stu-id="f5510-104">Define an action so that a user can click on the report and link to a URL, to a different report on the same report server or on a SharePoint site that is integrated with a report server, or to a different location in the same report.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f5510-105">选项</span><span class="sxs-lookup"><span data-stu-id="f5510-105">Options</span></span>  
 <span data-ttu-id="f5510-106">**启用为操作**</span><span class="sxs-lookup"><span data-stu-id="f5510-106">**Enable as an action**</span></span>  
 <span data-ttu-id="f5510-107">选择一个选项，指示在用户单击该项时将执行的操作。</span><span class="sxs-lookup"><span data-stu-id="f5510-107">Select an option to indicate the action to perform when the user clicks the item.</span></span>  
  
 <span data-ttu-id="f5510-108">**无**</span><span class="sxs-lookup"><span data-stu-id="f5510-108">**None**</span></span>  
 <span data-ttu-id="f5510-109">选择此选项可指示该项没有任何操作。</span><span class="sxs-lookup"><span data-stu-id="f5510-109">Choose this option to indicate that the item has no action.</span></span>  
  
 <span data-ttu-id="f5510-110">**转到报表**</span><span class="sxs-lookup"><span data-stu-id="f5510-110">**Go to report**</span></span>  
 <span data-ttu-id="f5510-111">选择此选项可以创建指向位于报表服务器上的钻取报表的链接。</span><span class="sxs-lookup"><span data-stu-id="f5510-111">Choose this option to create a link to a drillthrough report that is located on a report server.</span></span> <span data-ttu-id="f5510-112">选择 **“转到报表”** 时，页面上将显示以下其他选项。</span><span class="sxs-lookup"><span data-stu-id="f5510-112">The following additional options appear when you select **Go to report**.</span></span>  
  
 <span data-ttu-id="f5510-113">**指定报表**</span><span class="sxs-lookup"><span data-stu-id="f5510-113">**Specify a report**</span></span>  
 <span data-ttu-id="f5510-114">键入或选择要用作钻取报表的报表的名称。</span><span class="sxs-lookup"><span data-stu-id="f5510-114">Type or select the name of the report that you want to use as a drillthrough report.</span></span> <span data-ttu-id="f5510-115">钻取报表必须与此报表位于同一报表服务器上。</span><span class="sxs-lookup"><span data-stu-id="f5510-115">Drillthrough reports must be on the same report server as this report.</span></span>  
  
 <span data-ttu-id="f5510-116">对于发布到配置为本机模式的报表服务器的报表，请使用不带文件扩展名的完整路径或相对路径。</span><span class="sxs-lookup"><span data-stu-id="f5510-116">For a report published to a report server configured for native mode, use a full or relative path without the file name extension.</span></span> <span data-ttu-id="f5510-117">如果该报表与当前报表位于同一文件夹中，则只需使用该报表的名称即可。</span><span class="sxs-lookup"><span data-stu-id="f5510-117">If the report is in the same folder as the current report, use the name of the report only.</span></span> <span data-ttu-id="f5510-118">如果报表位于同一报表服务器上的其他文件夹中，则使用相对路径或完整路径。</span><span class="sxs-lookup"><span data-stu-id="f5510-118">If the report is in a different folder on the same report server, use a relative path or a full path.</span></span> <span data-ttu-id="f5510-119">相对路径从当前文件夹开始并且在文件夹层次结构中上移，例如 ../Folder2/Report1。</span><span class="sxs-lookup"><span data-stu-id="f5510-119">A relative path starts from the current folder and moves up the folder hierarchy, for example, ../Folder2/Report1.</span></span> <span data-ttu-id="f5510-120">完整路径从 /（即主文件夹）开始。</span><span class="sxs-lookup"><span data-stu-id="f5510-120">A full path starts from /, the Home folder.</span></span> <span data-ttu-id="f5510-121">例如，/Reports/Report1。</span><span class="sxs-lookup"><span data-stu-id="f5510-121">For example, /Reports/Report1.</span></span>  
  
 <span data-ttu-id="f5510-122">对于发布到配置为 SharePoint 集成模式的报表服务器的报表，请使用带有文件扩展名 (.rdl) 的完全限定 URL。</span><span class="sxs-lookup"><span data-stu-id="f5510-122">For a report published to a report server configured in SharePoint integrated mode, use a fully qualified URL including the file name extension (.rdl).</span></span> <span data-ttu-id="f5510-123">例如，http:// *\<SharePointservername>/\<site>* /documents/report1.rdl。</span><span class="sxs-lookup"><span data-stu-id="f5510-123">For example, http://*\<SharePointservername>/\<site>*/Documents/Report1.rdl.</span></span> <span data-ttu-id="f5510-124">不支持相对路径。</span><span class="sxs-lookup"><span data-stu-id="f5510-124">Relative paths are not supported.</span></span>  
  
 <span data-ttu-id="f5510-125">有关详细信息，请参阅 msdn.microsoft.com 上[报表生成器文档](https://go.microsoft.com/fwlink/?LinkId=154494)中的[指定外部项的路径（报表生成器和 SSRS）](report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f5510-125">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md) in the [Report Builder documentation](https://go.microsoft.com/fwlink/?LinkId=154494) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="f5510-126">**使用这些参数运行报表**</span><span class="sxs-lookup"><span data-stu-id="f5510-126">**Use these parameters to run the report**</span></span>  
 <span data-ttu-id="f5510-127">添加要传递给钻取报表的参数列表。</span><span class="sxs-lookup"><span data-stu-id="f5510-127">Add a list of parameters to pass to the drillthrough report.</span></span> <span data-ttu-id="f5510-128">参数名称必须与为目标报表定义的参数相匹配。</span><span class="sxs-lookup"><span data-stu-id="f5510-128">The parameter names must match the parameters defined for the target report.</span></span> <span data-ttu-id="f5510-129">使用 **“添加”** 和 **“删除”** 按钮可添加和删除参数，使用向上键和向下键可对参数列表进行排序。</span><span class="sxs-lookup"><span data-stu-id="f5510-129">Use the **Add** and **Delete** buttons to add and remove parameters and use the up and down arrows to order the list of parameters.</span></span>  
  
 <span data-ttu-id="f5510-130">**添加**</span><span class="sxs-lookup"><span data-stu-id="f5510-130">**Add**</span></span>  
 <span data-ttu-id="f5510-131">添加要传递给钻取报表的新参数。</span><span class="sxs-lookup"><span data-stu-id="f5510-131">Add a new parameter to pass to the drillthrough report.</span></span>  
  
 <span data-ttu-id="f5510-132">**删除**</span><span class="sxs-lookup"><span data-stu-id="f5510-132">**Delete**</span></span>  
 <span data-ttu-id="f5510-133">删除钻取报表的参数。</span><span class="sxs-lookup"><span data-stu-id="f5510-133">Delete a parameter for the drillthrough report.</span></span>  
  
 <span data-ttu-id="f5510-134">**向上键**</span><span class="sxs-lookup"><span data-stu-id="f5510-134">**Up arrow**</span></span>  
 <span data-ttu-id="f5510-135">在列表中向上移动参数。</span><span class="sxs-lookup"><span data-stu-id="f5510-135">Move the parameter up in the list.</span></span>  
  
 <span data-ttu-id="f5510-136">**向下键**</span><span class="sxs-lookup"><span data-stu-id="f5510-136">**Down arrow**</span></span>  
 <span data-ttu-id="f5510-137">在列表中向下移动参数。</span><span class="sxs-lookup"><span data-stu-id="f5510-137">Move the parameter down in the list.</span></span>  
  
 <span data-ttu-id="f5510-138">**名称**</span><span class="sxs-lookup"><span data-stu-id="f5510-138">**Name**</span></span>  
 <span data-ttu-id="f5510-139">键入表示钻取报表中所定义参数的名称的文本。</span><span class="sxs-lookup"><span data-stu-id="f5510-139">Type text that is the name of a parameter defined in the drillthrough report.</span></span>  
  
 <span data-ttu-id="f5510-140">**值**</span><span class="sxs-lookup"><span data-stu-id="f5510-140">**Value**</span></span>  
 <span data-ttu-id="f5510-141">键入或选择要传递给钻取报表中的命名参数的值。</span><span class="sxs-lookup"><span data-stu-id="f5510-141">Type or select a value to pass for the named parameter in the drillthrough report.</span></span> <span data-ttu-id="f5510-142">单击“表达式”\*\*\*\* (*fx*) 按钮可编辑表达式。</span><span class="sxs-lookup"><span data-stu-id="f5510-142">Click the **Expression** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="f5510-143">**省略**</span><span class="sxs-lookup"><span data-stu-id="f5510-143">**Omit**</span></span>  
 <span data-ttu-id="f5510-144">选择此选项可阻止参数运行。</span><span class="sxs-lookup"><span data-stu-id="f5510-144">Select to prevent the parameter from running.</span></span> <span data-ttu-id="f5510-145">默认情况下，此复选框已清除，处于不活动状态。</span><span class="sxs-lookup"><span data-stu-id="f5510-145">By default, this check box is cleared and not active.</span></span> <span data-ttu-id="f5510-146">若要选中该复选框，请单击“表达式”\*\*\*\*(fx\*\*) 按钮，再键入 **True** 或创建表达式。</span><span class="sxs-lookup"><span data-stu-id="f5510-146">To select the check box, click the **Expression** (*fx*) button and either type **True** or create an expression.</span></span> <span data-ttu-id="f5510-147">单击 "**表达式**" 对话框中的 **"确定"** 后，将选中该复选框。</span><span class="sxs-lookup"><span data-stu-id="f5510-147">The check box is selected when you click **OK** in the **Expression** dialog box.</span></span>  
  
 <span data-ttu-id="f5510-148">**转到书签**</span><span class="sxs-lookup"><span data-stu-id="f5510-148">**Go to bookmark**</span></span>  
 <span data-ttu-id="f5510-149">选择此选项可以定义指向当前报表内书签的链接。</span><span class="sxs-lookup"><span data-stu-id="f5510-149">Choose this option to define a link to a bookmark in the current report.</span></span> <span data-ttu-id="f5510-150">选择 **“转到书签”** 时，页面上将显示以下其他选项。</span><span class="sxs-lookup"><span data-stu-id="f5510-150">The following additional option appears when you select **Go to bookmark**.</span></span>  
  
 <span data-ttu-id="f5510-151">**选择书签**</span><span class="sxs-lookup"><span data-stu-id="f5510-151">**Select bookmark**</span></span>  
 <span data-ttu-id="f5510-152">键入或选择用户单击该链接时，将跳至的报表书签 ID。</span><span class="sxs-lookup"><span data-stu-id="f5510-152">Type or select the bookmark ID for the report to jump to when the user clicks the link.</span></span> <span data-ttu-id="f5510-153">单击“表达式”(fx\*\*\*\*) 按钮，更改表达式。</span><span class="sxs-lookup"><span data-stu-id="f5510-153">Click the Expression (**fx**) button to change the expression.</span></span> <span data-ttu-id="f5510-154">书签 ID 可以是静态 ID，也可以是计算结果为书签 ID 的表达式。</span><span class="sxs-lookup"><span data-stu-id="f5510-154">The bookmark ID can be either a static ID or an expression that evaluates to a bookmark ID.</span></span> <span data-ttu-id="f5510-155">表达式中可以包括含有书签 ID 的字段。</span><span class="sxs-lookup"><span data-stu-id="f5510-155">The expression can include a field that contains a bookmark ID.</span></span>  
  
 <span data-ttu-id="f5510-156">若要链接到书签，首先必须设置报表项的“书签”属性。</span><span class="sxs-lookup"><span data-stu-id="f5510-156">To link to a bookmark, you must first set the Bookmark property of a report item.</span></span> <span data-ttu-id="f5510-157">若要设置“书签”属性，请选择一个报表项并在“属性”窗格中键入书签 ID 的值或表达式；例如，SalesChart 或 5TopSales。</span><span class="sxs-lookup"><span data-stu-id="f5510-157">To set the Bookmark property, select a report item, and in the Properties pane, type a value or expression for the bookmark ID; for example, SalesChart or 5TopSales.</span></span>  
  
 <span data-ttu-id="f5510-158">**转到 URL**</span><span class="sxs-lookup"><span data-stu-id="f5510-158">**Go to URL**</span></span>  
 <span data-ttu-id="f5510-159">选择此选项可以定义指向网页的链接。</span><span class="sxs-lookup"><span data-stu-id="f5510-159">Choose this option to define a link to a Web page.</span></span> <span data-ttu-id="f5510-160">键入或选择网页的 URL 或计算结果为网页的 URL 的表达式。</span><span class="sxs-lookup"><span data-stu-id="f5510-160">Type or select the URL of a Web page or an expression that evaluates to the URL of a Web page.</span></span> <span data-ttu-id="f5510-161">单击“表达式”\*\*\*\*(fx\*\*) 按钮，更改表达式。</span><span class="sxs-lookup"><span data-stu-id="f5510-161">Click the **Expression** (*fx*) button to change the expression.</span></span> <span data-ttu-id="f5510-162">此表达式可以有一个包含 URL 的字段。</span><span class="sxs-lookup"><span data-stu-id="f5510-162">This expression can include a field that contains a URL.</span></span> <span data-ttu-id="f5510-163">选择 **“转到 URL”** 时，页面上将显示以下其他选项。</span><span class="sxs-lookup"><span data-stu-id="f5510-163">The following additional option appears when you select **Go to URL**.</span></span>  
  
 <span data-ttu-id="f5510-164">**选择 URL**</span><span class="sxs-lookup"><span data-stu-id="f5510-164">**Select URL**</span></span>  
 <span data-ttu-id="f5510-165">键入或输入相应项的 URL。</span><span class="sxs-lookup"><span data-stu-id="f5510-165">Type or enter the URL of the item.</span></span> <span data-ttu-id="f5510-166">对于发布到配置为本机模式的报表服务器的项，请使用完整路径或相对路径。</span><span class="sxs-lookup"><span data-stu-id="f5510-166">For an item published to a report server configured for native mode, use a full or relative path.</span></span> <span data-ttu-id="f5510-167">例如，http:// *\<servername>* /images/image1.jpg。</span><span class="sxs-lookup"><span data-stu-id="f5510-167">For example, http://*\<servername>*/images/image1.jpg.</span></span> <span data-ttu-id="f5510-168">对于发布到在 SharePoint 集成模式下配置的 Report Server 的项，请使用完全限定的 URL (例如 http:// *\<SharePointservername>/\<site>* /Documents/images/image1.jpg) 。</span><span class="sxs-lookup"><span data-stu-id="f5510-168">For an item published to a report server configured in SharePoint integrated mode, use a fully qualified URL (for example, http://*\<SharePointservername>/\<site>*/Documents/images/image1.jpg).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5510-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5510-169">See Also</span></span>  
 <span data-ttu-id="f5510-170">[图表 &#40;报表生成器和 SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f5510-170">[Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f5510-171">[报表生成器对话框、窗格和向导的帮助](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="f5510-171">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="f5510-172">[报表参数 &#40;报表生成器和报表设计器&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="f5510-172">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="f5510-173">[添加子报表和参数 &#40;报表生成器和 SSRS&#41;](report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f5510-173">[Add a Subreport and Parameters &#40;Report Builder and SSRS&#41;](report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f5510-174">交互式排序、文档结构图和链接（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f5510-174">Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;</span></span>](report-design/interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)  
  
  
