---
title: 在 SharePoint 集成模式下将筛选器或文档 Web 部件 (Reporting Services 连接) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Filter Web Part [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
- Documents Web Part [Reporting Services]
ms.assetid: 6a303135-c0ef-44cd-a423-1cea8df3dcf3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5ea7b9f9aba128052ae6ac7f05ef40517eb50e6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579529"
---
# <a name="connect-filter-or-documents-web-part-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="02a82-102">连接筛选器或文档 Web 部件（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="02a82-102">Connect Filter or Documents Web Part (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="02a82-103">如果在使用 SharePoint 产品，可以创建一个包含筛选器 Web 部件或文档 Web 部件和报表查看器 Web 部件的面板或 Web 部件页。</span><span class="sxs-lookup"><span data-stu-id="02a82-103">If you are using a SharePoint product, you can create a dashboard or Web Part Page that includes a Filter Web Part or Documents Web part and a Report Viewer Web Part.</span></span> <span data-ttu-id="02a82-104">支持的版本为 [!INCLUDE[SPF2010](../includes/spf2010-md.md)] 或 [!INCLUDE[SPS2010](../includes/sps2010-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="02a82-104">Supported versions are [!INCLUDE[SPF2010](../includes/spf2010-md.md)] or [!INCLUDE[SPS2010](../includes/sps2010-md.md)].</span></span> <span data-ttu-id="02a82-105">还支持 [!INCLUDE[winSPServ3](../includes/winspserv3-md.md)] 或 [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007。</span><span class="sxs-lookup"><span data-stu-id="02a82-105">Also supported are [!INCLUDE[winSPServ3](../includes/winspserv3-md.md)] or [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007.</span></span> <span data-ttu-id="02a82-106">通过连接筛选器 Web 部件，在筛选器 Web 部件中选择筛选器值的用户可以将值发送至同一页中的参数化报表。</span><span class="sxs-lookup"><span data-stu-id="02a82-106">By connecting a Filter Web Part, users who select filter values in a Filter Web Part can send the value to a parameterized report on the same page.</span></span> <span data-ttu-id="02a82-107">通过连接文档 Web 部件，在文档库中单击报表的用户可以在相邻的报表查看器 Web 部件中查看报表。</span><span class="sxs-lookup"><span data-stu-id="02a82-107">By connecting a Documents Web Part, users who click on reports in the Documents library can view the report in an adjacent Report Viewer Web Part.</span></span>  
  
 <span data-ttu-id="02a82-108">筛选器 Web 部件可用于向报表中的一个或多个参数发送值。</span><span class="sxs-lookup"><span data-stu-id="02a82-108">The Filter Web Part is used to send values to one or more parameters on a report.</span></span> <span data-ttu-id="02a82-109">若要使用筛选器 Web 部件，报表必须具有为其定义的参数并且参数与 Web 部件发送的值、数据类型及格式兼容。</span><span class="sxs-lookup"><span data-stu-id="02a82-109">To use a Filter Web Part, the report must have parameters defined for it that are compatible with the values, data type, and format sent by the Web Part.</span></span>  
  
 <span data-ttu-id="02a82-110">文档 Web 部件与主文件夹站点的文档库相关联。</span><span class="sxs-lookup"><span data-stu-id="02a82-110">The Documents Web Part is associated with the Documents library of the Home site.</span></span> <span data-ttu-id="02a82-111">若要从文档库查看、添加或删除项，请单击 **“查看所有站点内容”**。</span><span class="sxs-lookup"><span data-stu-id="02a82-111">To view, add, or remove items from the Documents library, click **View All Site Content**.</span></span> <span data-ttu-id="02a82-112">在“库”中，单击 **“文档”**。</span><span class="sxs-lookup"><span data-stu-id="02a82-112">In Libraries, click **Documents**.</span></span> <span data-ttu-id="02a82-113">可以使用 **“新建”**、 **“上载”** 和 **“操作”** 菜单来管理文档库中的项。</span><span class="sxs-lookup"><span data-stu-id="02a82-113">You can use the **New**, **Upload**, and **Actions** menu to manage the items in the Documents library.</span></span>  
  
### <a name="to-connect-a-filter-web-part"></a><span data-ttu-id="02a82-114">连接筛选器 Web 部件</span><span class="sxs-lookup"><span data-stu-id="02a82-114">To connect a Filter Web Part</span></span>  
  
1.  <span data-ttu-id="02a82-115">打开或创建 Web 部件页或面板。</span><span class="sxs-lookup"><span data-stu-id="02a82-115">Open or create the Web Part page or dashboard.</span></span>  
  
2.  <span data-ttu-id="02a82-116">在 **“站点操作”** 菜单上，单击 **“编辑页面”**。</span><span class="sxs-lookup"><span data-stu-id="02a82-116">On the **Site Actions** menu, click **Edit Page**.</span></span>  
  
3.  <span data-ttu-id="02a82-117">单击 **“添加 Web 部件”**。</span><span class="sxs-lookup"><span data-stu-id="02a82-117">Click **Add a Web Part**.</span></span>  
  
4.  <span data-ttu-id="02a82-118">在 "**所有 Web 部件**的"**杂项**"类别中，选择**SQL Server Reporting Services 报表查看器**"。</span><span class="sxs-lookup"><span data-stu-id="02a82-118">In **All Web Parts**, in the **Miscellaneous** category, select **SQL Server Reporting Services Report Viewer**.</span></span>  
  
5.  <span data-ttu-id="02a82-119">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="02a82-119">Click **Add**.</span></span> <span data-ttu-id="02a82-120">Web 部件将添加到区域的顶部。</span><span class="sxs-lookup"><span data-stu-id="02a82-120">The Web Part is added at the top of the zone.</span></span>  
  
6.  <span data-ttu-id="02a82-121">在同一 Web 部件页或面板中的另一区域上，单击 **“添加 Web 部件”**。</span><span class="sxs-lookup"><span data-stu-id="02a82-121">On another zone in the same Web Part page or dashboard, click **Add a Web Part**.</span></span>  
  
7.  <span data-ttu-id="02a82-122">在 **“所有 Web 部件”** 的 **“筛选器”** 部分，选择一个 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="02a82-122">In **All Web Parts**, in the **Filters** section, select a Web Part.</span></span>  
  
8.  <span data-ttu-id="02a82-123">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="02a82-123">Click **Add**.</span></span> <span data-ttu-id="02a82-124">Web 部件将添加到区域的顶部。</span><span class="sxs-lookup"><span data-stu-id="02a82-124">The Web Part is added at the top of the zone.</span></span>  
  
9. <span data-ttu-id="02a82-125">在包含 web 部件的区域中，单击 web 部件的 "**编辑**" 菜单，依次指向 "**连接**"、"**将筛选器值发送到**"，然后选择 "**报表查看器**  -  *报表名称*"。</span><span class="sxs-lookup"><span data-stu-id="02a82-125">In the zone that contains the Web Part, click the Web Part **edit** menu, point to **Connections**, point to **Send Filter Values To**, and then select **Report Viewer** - *report name*.</span></span>  
  
10. <span data-ttu-id="02a82-126">签入更改并保存此页。</span><span class="sxs-lookup"><span data-stu-id="02a82-126">Check in your changes and save the page.</span></span>  
  
### <a name="to-connect-a-documents-web-part"></a><span data-ttu-id="02a82-127">连接文档 Web 部件</span><span class="sxs-lookup"><span data-stu-id="02a82-127">To connect a Documents Web Part</span></span>  
  
1.  <span data-ttu-id="02a82-128">打开或创建 Web 部件页或面板。</span><span class="sxs-lookup"><span data-stu-id="02a82-128">Open or create the Web Part page or dashboard.</span></span>  
  
2.  <span data-ttu-id="02a82-129">在 **“站点操作”** 菜单上，单击 **“编辑页面”**。</span><span class="sxs-lookup"><span data-stu-id="02a82-129">On the **Site Actions** menu, click **Edit Page**.</span></span>  
  
3.  <span data-ttu-id="02a82-130">单击 **“添加 Web 部件”**。</span><span class="sxs-lookup"><span data-stu-id="02a82-130">Click **Add a Web Part**.</span></span>  
  
4.  <span data-ttu-id="02a82-131">在 **“所有 Web 部件”** 的 **“列表和库”** 部分中，选择 **“文档”**。</span><span class="sxs-lookup"><span data-stu-id="02a82-131">In **All Web Parts**, in the **Lists and Library** section, select **Documents.**</span></span>  
  
5.  <span data-ttu-id="02a82-132">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="02a82-132">Click **Add**.</span></span> <span data-ttu-id="02a82-133">Web 部件将添加到区域的顶部。</span><span class="sxs-lookup"><span data-stu-id="02a82-133">The Web Part is added at the top of the zone.</span></span>  
  
6.  <span data-ttu-id="02a82-134">在工具窗格的底部，单击 **“应用”** ，然后单击 **“确定”** 关闭窗格。</span><span class="sxs-lookup"><span data-stu-id="02a82-134">Click **Apply** at the bottom of the tool pane, and then click **OK** to close the pane.</span></span>  
  
7.  <span data-ttu-id="02a82-135">在同一 Web 部件页或面板中的另一区域上，单击 **“添加 Web 部件”**。</span><span class="sxs-lookup"><span data-stu-id="02a82-135">On another zone in the same Web Part page or dashboard, click **Add a Web Part**.</span></span>  
  
8.  <span data-ttu-id="02a82-136">在 **“所有 Web 部件”** 的 **“杂项”** 类别中，选择 **“SQL Server Reporting Services 报表查看器”.**</span><span class="sxs-lookup"><span data-stu-id="02a82-136">In **All Web Parts**, in the **Miscellaneous** category, select **SQL Server Reporting Services Report Viewer.**</span></span>  
  
9. <span data-ttu-id="02a82-137">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="02a82-137">Click **Add**.</span></span> <span data-ttu-id="02a82-138">Web 部件将添加到区域的顶部。</span><span class="sxs-lookup"><span data-stu-id="02a82-138">The Web Part is added at the top of the zone.</span></span>  
  
10. <span data-ttu-id="02a82-139">在包含 Web 部件的区域中，单击 Web 部件的 **“编辑”** 菜单，依次指向 **“连接”**、 **“获取报表定义于”**，然后选择 **“文档”**。</span><span class="sxs-lookup"><span data-stu-id="02a82-139">In the zone that contains the Web Part, click the Web Part **edit** menu, point to **Connections**, point to **Get report definitions from**, and then select **Documents**.</span></span>  
  
11. <span data-ttu-id="02a82-140">签入更改并保存此页。</span><span class="sxs-lookup"><span data-stu-id="02a82-140">Check in your changes and save the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02a82-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02a82-141">See Also</span></span>  
 <span data-ttu-id="02a82-142">[将报表查看器 Web 部件添加到 Reporting Services SharePoint 集成模式下的网页 &#40;&#41;](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="02a82-142">[Add the Report Viewer Web Part to a Web Page &#40;Reporting Services in SharePoint Integrated Mode&#41;](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="02a82-143">[SharePoint 站点上的报表查看器 Web 部件](../../2014/reporting-services/report-viewer-web-part-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="02a82-143">[Report Viewer Web Part on a SharePoint Site](../../2014/reporting-services/report-viewer-web-part-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="02a82-144">自定义报表查看器 Web 部件</span><span class="sxs-lookup"><span data-stu-id="02a82-144">Customize the Report Viewer Web Part</span></span>](../../2014/reporting-services/customize-the-report-viewer-web-part.md)  
  
  
