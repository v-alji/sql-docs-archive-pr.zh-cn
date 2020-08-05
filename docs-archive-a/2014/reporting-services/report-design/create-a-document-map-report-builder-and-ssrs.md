---
title: 创建文档结构图（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c200a97b-67f2-499f-8374-3ed1ebe3f33c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a9dad0f8e6ee1d9b9ada44fda0eec5908f27cfcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580634"
---
# <a name="create-a-document-map-report-builder-and-ssrs"></a><span data-ttu-id="3510e-102">创建文档结构图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="3510e-102">Create a Document Map (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3510e-103">文档结构图提供了一组指向所呈现报表中的报表项的导航链接。</span><span class="sxs-lookup"><span data-stu-id="3510e-103">A document map provides a set of navigational links to report items in a rendered report.</span></span> <span data-ttu-id="3510e-104">当您查看包含文档结构图的报表时，将在报表旁显示一个单独的侧窗格。</span><span class="sxs-lookup"><span data-stu-id="3510e-104">When you view a report that includes a document map, a separate side pane appears next to the report.</span></span> <span data-ttu-id="3510e-105">用户通过单击文档结构图中的链接，可跳至显示报表项的报表页。</span><span class="sxs-lookup"><span data-stu-id="3510e-105">A user can click links in the document map to jump to the report page that displays that item.</span></span> <span data-ttu-id="3510e-106">报表的各区域和组将按一定层次结构的链接形式排列。</span><span class="sxs-lookup"><span data-stu-id="3510e-106">Report sections and groups are arranged in a hierarchy of links.</span></span> <span data-ttu-id="3510e-107">单击文档结构图中的项会刷新报表，并显示与文档结构图中所单击项对应的报表区域。</span><span class="sxs-lookup"><span data-stu-id="3510e-107">Clicking items in the document map refreshes the report and displays the area of the report that corresponds to the item in the document map.</span></span>  
  
 <span data-ttu-id="3510e-108">若要向文档结构图添加链接，则需要将报表项的 `DocumentMapLabel` 属性设置为您所创建的文本，或者设置为计算结果为您要在文档结构图中显示的文本的表达式。</span><span class="sxs-lookup"><span data-stu-id="3510e-108">To add links to the document map, you set the `DocumentMapLabel` property of the report item to text that you create or to an expression that evaluates to the text that you want display in the document map.</span></span> <span data-ttu-id="3510e-109">还可以向文档结构图添加表或矩阵组的唯一值。</span><span class="sxs-lookup"><span data-stu-id="3510e-109">You can also add the unique values for a table or matrix group to the document map.</span></span> <span data-ttu-id="3510e-110">例如，对于基于颜色的组，每个唯一颜色都是指向显示该颜色组实例的报表页的一个链接。</span><span class="sxs-lookup"><span data-stu-id="3510e-110">For example, for a group based on color, each unique color is a link to the report page that displays the group instance for that color.</span></span>  
  
 <span data-ttu-id="3510e-111">您还可以创建指向报表的 URL 来覆盖文档结构图，这样在运行报表时可以不显示文档结构图，然后通过单击报表查看器工具栏中的 **“显示/隐藏文档结构图”** 按钮，可切换到显示文档结构图。</span><span class="sxs-lookup"><span data-stu-id="3510e-111">You can also create a URL to a report that overrides the display of the document map, so that you can run the report without displaying the document map, and then click the **Show/Hide Document Map** button on the report viewer toolbar to toggle the display.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="document-maps-and-rendering-extensions"></a><a name="DocMapRenderExtensions"></a> <span data-ttu-id="3510e-112">文档结构图和呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="3510e-112">Document Maps and Rendering Extensions</span></span>  
 <span data-ttu-id="3510e-113">文档结构图专门用于 HTML 呈现扩展插件（如预览和报表查看器）。</span><span class="sxs-lookup"><span data-stu-id="3510e-113">The document map is intended for use in the HTML rendering extension-for example, in Preview and the Report Viewer.</span></span> <span data-ttu-id="3510e-114">其他呈现扩展插件具有不同的呈现文档结构图的方式：</span><span class="sxs-lookup"><span data-stu-id="3510e-114">Other rendering extensions have different ways of articulating a document map:</span></span>  
  
-   <span data-ttu-id="3510e-115">PDF 将文档结构图呈现为“书签”窗格。</span><span class="sxs-lookup"><span data-stu-id="3510e-115">PDF renders a document map as the Bookmarks pane.</span></span>  
  
-   <span data-ttu-id="3510e-116">Excel 将文档结构图呈现为包含链接层次结构的命名工作表。</span><span class="sxs-lookup"><span data-stu-id="3510e-116">Excel renders a document map as a named worksheet that includes a hierarchy of links.</span></span> <span data-ttu-id="3510e-117">各报表区域在不同的工作表中呈现，这些工作表与文档结构图处于同一工作簿中。</span><span class="sxs-lookup"><span data-stu-id="3510e-117">Report sections are rendered in separate worksheets that are included with the document map in the same workbook.</span></span>  
  
-   <span data-ttu-id="3510e-118">Word 中包含作为目录的文档结构图。</span><span class="sxs-lookup"><span data-stu-id="3510e-118">Word includes a document map as the table of contents.</span></span>  
  
-   <span data-ttu-id="3510e-119">Atom、TIFF、XML 和 CSV 将忽略文档结构图。</span><span class="sxs-lookup"><span data-stu-id="3510e-119">Atom, TIFF, XML, and CSV ignore document maps.</span></span>  
  
 <span data-ttu-id="3510e-120">有关详细信息，请参阅[不同报表呈现扩展插件的交互功能（报表生成器和 SSRS）](../report-builder/interactive-functionality-different-report-rendering-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="3510e-120">For more information, see [Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md).</span></span>  
  
##  <a name="AddRptItemToMap"></a>   
#### <a name="to-add-a-report-item-to-a-document-map"></a><span data-ttu-id="3510e-121">向文档结构图添加报表项</span><span class="sxs-lookup"><span data-stu-id="3510e-121">To add a report item to a document map</span></span>  
  
1.  <span data-ttu-id="3510e-122">在“设计”视图中，选择要添加到文档结构图中的报表项，如表、矩阵或仪表。</span><span class="sxs-lookup"><span data-stu-id="3510e-122">In Design view, select the report item such as a table, matrix, or gauge that you want to add to the document map.</span></span> <span data-ttu-id="3510e-123">报表项属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="3510e-123">The report item properties appear in the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3510e-124">若要选择 Tablix 数据区域，请在任意单元内单击以显示行控点和列控点，然后单击角控点。</span><span class="sxs-lookup"><span data-stu-id="3510e-124">To select a tablix data region, click in any cell to display the row and column handles, and then click the corner handle.</span></span>  
  
2.  <span data-ttu-id="3510e-125">在 "属性" 窗格中，在属性中键入要在文档结构图中显示的文本 `DocumentMapLabel` ，或输入计算结果为标签的表达式。</span><span class="sxs-lookup"><span data-stu-id="3510e-125">In the Properties pane, type the text that you want to appear in the document map in the `DocumentMapLabel` property, or enter an expression that evaluates to a label.</span></span> <span data-ttu-id="3510e-126">例如，键入 **Sales Chart**。</span><span class="sxs-lookup"><span data-stu-id="3510e-126">For example, type **Sales Chart**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3510e-127">如果看不到“属性”窗格，请在 **“视图”** 选项卡的 **“显示/隐藏”** 组中选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="3510e-127">If you do not see the Properties pane, on the **View** tab, in the **Show/Hide** group, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="3510e-128">对要在文档结构图中显示的每个报表项重复步骤 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="3510e-128">Repeat steps 1 and 2 for every report item that you want to appear in the document map.</span></span>  
  
4.  <span data-ttu-id="3510e-129">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="3510e-129">Click **Run**.</span></span> <span data-ttu-id="3510e-130">将运行报表，并且文档结构图会显示您创建的标签。</span><span class="sxs-lookup"><span data-stu-id="3510e-130">The report runs and the document map displays the labels you created.</span></span> <span data-ttu-id="3510e-131">单击任一链接，可跳至显示该报表项的报表页。</span><span class="sxs-lookup"><span data-stu-id="3510e-131">Click any link to jump to the report page with that item.</span></span>  
  
 
  
##  <a name="AddUniqueValuesToMap"></a>   
#### <a name="to-add-unique-group-values-to-a-document-map"></a><span data-ttu-id="3510e-132">向文档结构图添加唯一组值</span><span class="sxs-lookup"><span data-stu-id="3510e-132">To add unique group values to a document map</span></span>  
  
1.  <span data-ttu-id="3510e-133">在“设计”视图中，选择包含要在文档结构图中显示的组的表、矩阵或列表。</span><span class="sxs-lookup"><span data-stu-id="3510e-133">In Design view, select the table, matrix, or list that contains the group that you want to display in the document map.</span></span> <span data-ttu-id="3510e-134">“分组”窗格随即显示行组和列组。</span><span class="sxs-lookup"><span data-stu-id="3510e-134">The Grouping pane displays the row and column groups.</span></span>  
  
2.  <span data-ttu-id="3510e-135">在“行组”窗格中，右键单击相应的组，然后单击 **“编辑组”** 。</span><span class="sxs-lookup"><span data-stu-id="3510e-135">In the Row Groups pane, right-click the group, and then click **Edit Group**.</span></span> <span data-ttu-id="3510e-136">将打开 **“Tablix 组属性”** 对话框的 **“常规”** 页。</span><span class="sxs-lookup"><span data-stu-id="3510e-136">The **General** page of the **Tablix Group Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="3510e-137">单击“高级”。 </span><span class="sxs-lookup"><span data-stu-id="3510e-137">Click **Advanced**.</span></span>  
  
4.  <span data-ttu-id="3510e-138">在 **“文档结构图”** 列表框中，键入或选择与组表达式匹配的表达式。</span><span class="sxs-lookup"><span data-stu-id="3510e-138">In the **Document map** list box, type or select an expression that matches the group expression.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="3510e-139">对要在文档结构图中显示的每个组重复步骤 1-4。</span><span class="sxs-lookup"><span data-stu-id="3510e-139">Repeat steps 1-4 for every group that you want to appear in the document map.</span></span>  
  
7.  <span data-ttu-id="3510e-140">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="3510e-140">Click **Run**.</span></span> <span data-ttu-id="3510e-141">将运行报表，并且文档结构图会显示组值。</span><span class="sxs-lookup"><span data-stu-id="3510e-141">The report runs and the document map displays the group values.</span></span> <span data-ttu-id="3510e-142">单击任一链接，可跳至显示该报表项的报表页。</span><span class="sxs-lookup"><span data-stu-id="3510e-142">Click any link to jump to the report page with that item.</span></span>  
  
 
  
##  <a name="HideMapWhenViewRpt"></a>   
#### <a name="to-hide-the-document-map-when-you-view-a-report"></a><span data-ttu-id="3510e-143">查看报表时隐藏文档结构图</span><span class="sxs-lookup"><span data-stu-id="3510e-143">To hide the document map when you view a report</span></span>  
  
1.  <span data-ttu-id="3510e-144">在报表管理器中，浏览到包含文档结构图的报表。</span><span class="sxs-lookup"><span data-stu-id="3510e-144">In Report Manager, browse to the report that has the document map.</span></span>  
  
     <span data-ttu-id="3510e-145">例如，对于 [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 示例报表，下面的 URL 指定名为 Product Catalog 的报表。</span><span class="sxs-lookup"><span data-stu-id="3510e-145">For example, for the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] sample reports, the following URL specifies the report named Product Catalog.</span></span>  
  
    ```  
    http://localhost/Reports/Pages/Report.aspx?ItemPath=%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog  
    ```  
  
2.  <span data-ttu-id="3510e-146">复制服务器中的报表路径。</span><span class="sxs-lookup"><span data-stu-id="3510e-146">Copy the report path on the server.</span></span> <span data-ttu-id="3510e-147">在该示例中，报表路径为 `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`。</span><span class="sxs-lookup"><span data-stu-id="3510e-147">In the example, the report path is `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`.</span></span>  
  
3.  <span data-ttu-id="3510e-148">使用以下三个组件创建一个新 URL：</span><span class="sxs-lookup"><span data-stu-id="3510e-148">Create a new URL with the following three components:</span></span>  
  
    -   <span data-ttu-id="3510e-149">报表服务器中的报表查看器： `http://localhost/ReportServer/Pages/ReportViewer.aspx?`</span><span class="sxs-lookup"><span data-stu-id="3510e-149">The report viewer on the report server: `http://localhost/ReportServer/Pages/ReportViewer.aspx?`</span></span>  
  
    -   <span data-ttu-id="3510e-150">步骤 1 中复制的报表的名称，例如： `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`</span><span class="sxs-lookup"><span data-stu-id="3510e-150">The name of the report you copied in step 1, for example: `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`</span></span>  
  
    -   <span data-ttu-id="3510e-151">指定隐藏文档结构图的设备信息参数： `&rs%3aCommand=Render&rc%3aFormat=HTML4.0&rc%3aDocMap=False`</span><span class="sxs-lookup"><span data-stu-id="3510e-151">The device information parameters that specify hiding the document map: `&rs%3aCommand=Render&rc%3aFormat=HTML4.0&rc%3aDocMap=False`</span></span>  
  
     <span data-ttu-id="3510e-152">下面的 URL 由此三个组件以其所列顺序追加而成。</span><span class="sxs-lookup"><span data-stu-id="3510e-152">The following URL consists of these three components appended in the order they are listed.</span></span>  
  
    ```  
    http://localhost/ReportServer/Pages/ReportViewer.aspx?  
    %2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog  
    &rs%3aCommand=Render&rc%3aFormat=HTML4.0&rc%3aDocMap=False  
    ```  
  
     <span data-ttu-id="3510e-153">若要使用此 URL，请复制此 URL，并删除所有换行符。</span><span class="sxs-lookup"><span data-stu-id="3510e-153">To use this URL, copy it and remove all line breaks.</span></span>  
  
4.  <span data-ttu-id="3510e-154">将此 URL 粘贴到报表管理器中，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="3510e-154">Paste the URL in Report Manager, and then press ENTER.</span></span> <span data-ttu-id="3510e-155">将运行报表，并隐藏文档结构图。</span><span class="sxs-lookup"><span data-stu-id="3510e-155">The report runs, and the document map is hidden.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3510e-156"> 有关下载示例报表的详细信息，请参阅 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][报表生成器和报表设计器示例报表](https://go.microsoft.com/fwlink/?LinkId=198283)。</span><span class="sxs-lookup"><span data-stu-id="3510e-156">For more information about downloading sample reports, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
>   
>  <span data-ttu-id="3510e-157">有关详细信息，请参阅 SQL Server 联机丛书中 [Reporting Services 文档](https://go.microsoft.com/fwlink/?linkid=121312) 中的“URL 访问”。</span><span class="sxs-lookup"><span data-stu-id="3510e-157">For more information, see "URL Access" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="3510e-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3510e-158">See Also</span></span>  
 [<span data-ttu-id="3510e-159">在报表管理器中查找和查看报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="3510e-159">Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)  
  
  
