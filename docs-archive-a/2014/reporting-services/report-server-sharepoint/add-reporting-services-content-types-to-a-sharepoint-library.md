---
title: 将报表查看器 Web 部件添加到 SharePoint 集成模式下的网页 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- Web Parts [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
ms.assetid: cac75345-2380-467d-a394-0a2140908a5a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d9b933fad8bc566b3cb0ef04303a85c5f034e620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691596"
---
# <a name="add-the-report-viewer-web-part-to-a-web-page-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="9a571-102">将报表查看器 Web 部件添加到网页（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="9a571-102">Add the Report Viewer Web Part to a Web Page (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="9a571-103">可以使用报表查看器 Web 部件查看在报表服务器（配置为在 SharePoint 集成模式下运行）上运行的报表。</span><span class="sxs-lookup"><span data-stu-id="9a571-103">You can use the Report Viewer Web Part to view reports that run on report server that is configured to run in SharePoint integrated mode.</span></span> <span data-ttu-id="9a571-104">可以使用 Web 部件显示您在报表生成器或报表设计器中创建并上载到库中的报表定义 (.rdl) 文件。</span><span class="sxs-lookup"><span data-stu-id="9a571-104">You can use the Web Part to display report definition (.rdl) files that you created in Report Builder or Report Designer and uploaded to a library.</span></span>  
  
 <span data-ttu-id="9a571-105">如果要在网页中嵌入报表，则可以向该网页添加报表查看器 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="9a571-105">You can add the Report Viewer Web Part to a Web page if you want to embed a report on that page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a571-106">尽管名称相同，但通过 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序安装的报表查看器 Web 部件与 RSWebParts.cab 文件中包含的报表查看器 Web 部件并不相同。</span><span class="sxs-lookup"><span data-stu-id="9a571-106">Although they have identical names, the Report Viewer Web Part that is installed through the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is different from the Report Viewer Web Part that is included in the RSWebParts.cab file.</span></span> <span data-ttu-id="9a571-107">本主题中的说明专门针对通过 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序安装的报表查看器 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="9a571-107">The instructions in this topic are specifically for the Report Viewer Web Part that is installed through the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span>  
  
 <span data-ttu-id="9a571-108">若要向网页中添加 Web 部件，您必须拥有该站点级别的“添加和自定义网页”权限。</span><span class="sxs-lookup"><span data-stu-id="9a571-108">To add a Web Part to a Web page, you must have the Add and Customize Pages permission at the site level.</span></span> <span data-ttu-id="9a571-109">如果使用默认安全设置，此权限将授予拥有“完全控制”级权限的“所有者”  组的成员。</span><span class="sxs-lookup"><span data-stu-id="9a571-109">If you are using default security settings, this permission is granted to members of the **Owners** group who have the Full Control level of permission.</span></span>  
  
### <a name="to-embed-a-report-in-a-web-page"></a><span data-ttu-id="9a571-110">将报表嵌入网页中</span><span class="sxs-lookup"><span data-stu-id="9a571-110">To embed a report in a Web page</span></span>  
  
1.  <span data-ttu-id="9a571-111">打开或创建 Web 部件页或面板。</span><span class="sxs-lookup"><span data-stu-id="9a571-111">Open or create the Web Part page or dashboard.</span></span>  
  
2.  <span data-ttu-id="9a571-112">在 **“站点操作”** 菜单上，单击 **“编辑页面”**。</span><span class="sxs-lookup"><span data-stu-id="9a571-112">On **Site Actions**, click **Edit Page**.</span></span>  
  
3.  <span data-ttu-id="9a571-113">单击 **“添加 Web 部件”**。</span><span class="sxs-lookup"><span data-stu-id="9a571-113">Click **Add a Web Part**.</span></span>  
  
4.  <span data-ttu-id="9a571-114">在 Web 部件类别列表中，选择 **“杂项”** 类别，然后选择 **“SQL Server Reporting Services 报表查看器”**。</span><span class="sxs-lookup"><span data-stu-id="9a571-114">In the list of web part categories, select the **Miscellaneous** category, and then select **SQL Server Reporting Services Report Viewer**.</span></span>  
  
5.  <span data-ttu-id="9a571-115">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="9a571-115">Click **Add**.</span></span> <span data-ttu-id="9a571-116">Web 部件将添加到区域的顶部。</span><span class="sxs-lookup"><span data-stu-id="9a571-116">The Web Part is added at the top of the zone.</span></span> <span data-ttu-id="9a571-117">可以将其拖至区域中的其他位置。</span><span class="sxs-lookup"><span data-stu-id="9a571-117">You can drag it to a different location in the zone.</span></span>  
  
6.  <span data-ttu-id="9a571-118">在查看器中，单击 **“单击此处打开工具窗格”**。</span><span class="sxs-lookup"><span data-stu-id="9a571-118">Within the viewer, click **Click here to open the tool pane**.</span></span>  
  
7.  <span data-ttu-id="9a571-119">通过单击“浏览”(**...**) 按钮，从当前网站集合的任一库中选择报表。</span><span class="sxs-lookup"><span data-stu-id="9a571-119">Select a report from any library in the current site collection by clicking the browse (**...**) button.</span></span> <span data-ttu-id="9a571-120">也可以键入报表 URL。</span><span class="sxs-lookup"><span data-stu-id="9a571-120">You can also type the report URL.</span></span> <span data-ttu-id="9a571-121">若要确定任一报表的 URL，请右键单击报表并选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9a571-121">To determine the URL for any report, right-click the report and select **Properties**.</span></span> <span data-ttu-id="9a571-122">请勿单击报表旁的向下箭头；报表项的“查看属性”页上未指出报表 URL。</span><span class="sxs-lookup"><span data-stu-id="9a571-122">Do not click the down arrow next to the report; the report URL is not indicated in the View Properties page of the item.</span></span> <span data-ttu-id="9a571-123">如果从“属性”\*\*\*\* 对话框复制并粘贴 URL，请用空格替换“%20”URL 编码（例如，“Company%20Sales”应为“Company Sales”）。</span><span class="sxs-lookup"><span data-stu-id="9a571-123">If you copy and paste the URL from the **Properties** dialog box, replace the "%20" URL encoding with a space (for example, "Company%20Sales" should be "Company Sales").</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9a571-124">每个报表查看器 Web 部件都包含一个报表。</span><span class="sxs-lookup"><span data-stu-id="9a571-124">Each Report Viewer Web Part contains a single report.</span></span> <span data-ttu-id="9a571-125">URL 必须是当前 SharePoint 站点或同一 Web 应用程序或场内站点上的报表的完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="9a571-125">The URL must be the fully qualified path to a report that is on the current SharePoint site, or on a site within the same Web application or farm.</span></span> <span data-ttu-id="9a571-126">URL 必须能解析为包含报表的文档库或文档库内的文件夹。</span><span class="sxs-lookup"><span data-stu-id="9a571-126">The URL must resolve to a document library or to a folder within a document library that contains the report.</span></span> <span data-ttu-id="9a571-127">报表 URL 必须包含 .rdl 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="9a571-127">The report URL must include the .rdl file extension.</span></span> <span data-ttu-id="9a571-128">如果报表依赖的是模型或共享数据源文件，则不必在 URL 中指定这些文件。</span><span class="sxs-lookup"><span data-stu-id="9a571-128">If the report depends on a model or shared data source files, you do not need to specify those files in the URL.</span></span> <span data-ttu-id="9a571-129">报表包含对所需文件的引用。</span><span class="sxs-lookup"><span data-stu-id="9a571-129">The report contains references to the files it needs.</span></span>  
  
8.  <span data-ttu-id="9a571-130">在工具窗格打开时，可以通过设置属性来修改默认外观和布局。</span><span class="sxs-lookup"><span data-stu-id="9a571-130">While the tool pane is open, you can set properties to modify the default appearance and layout.</span></span>  
  
9. <span data-ttu-id="9a571-131">在工具窗格的底部，单击 **“应用”** ，然后单击 **“确定”** 关闭窗格。</span><span class="sxs-lookup"><span data-stu-id="9a571-131">Click **Apply** at the bottom of the tool pane, and then click **OK** to close the pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a571-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a571-132">See Also</span></span>  
 <span data-ttu-id="9a571-133">[SharePoint 站点上的报表查看器 Web 部件](../report-viewer-web-part-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="9a571-133">[Report Viewer Web Part on a SharePoint Site](../report-viewer-web-part-on-a-sharepoint-site.md) </span></span>  
 <span data-ttu-id="9a571-134">[自定义报表查看器 Web 部件](../customize-the-report-viewer-web-part.md) </span><span class="sxs-lookup"><span data-stu-id="9a571-134">[Customize the Report Viewer Web Part](../customize-the-report-viewer-web-part.md) </span></span>  
 <span data-ttu-id="9a571-135">[授予对 SharePoint 站点上的报表服务器项的权限](../security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="9a571-135">[Granting Permissions on Report Server Items on a SharePoint Site](../security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="9a571-136">安装或卸载用于 SharePoint 的 Reporting Services 外接程序 &#40;SharePoint 2010 和 SharePoint 2013&#41;</span><span class="sxs-lookup"><span data-stu-id="9a571-136">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](../install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
