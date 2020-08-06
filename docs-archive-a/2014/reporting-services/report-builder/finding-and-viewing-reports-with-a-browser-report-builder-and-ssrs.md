---
title: 使用浏览器查找和查看报表（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: edf4843a-2a0a-486f-be25-14a3c1c6bc72
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b864188fc5152a11ad66ac9cd986891b88849a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692761"
---
# <a name="finding-and-viewing-reports-with-a-browser-report-builder-and-ssrs"></a><span data-ttu-id="1a8d4-102">使用浏览器查找和查看报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="1a8d4-102">Finding and Viewing Reports with a Browser (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1a8d4-103">通过与报表服务器直接连接，您可以使用支持的任何 Web 浏览器查看报表。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-103">You can use any supported Web browser to view a report through a direct connection to a report server.</span></span> <span data-ttu-id="1a8d4-104">每个报表在报表服务器上都有一个 URL 地址。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-104">Every report has a URL address on a report server.</span></span> <span data-ttu-id="1a8d4-105">无需使用 Web 应用程序，输入报表的 Web 地址即可在浏览器窗口中打开相应报表。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-105">You can enter the Web address of a report to open it in a browser window independently of a Web application.</span></span> <span data-ttu-id="1a8d4-106">相应的报表会以 HTML 格式打开，并且包含报表工具栏，这样在此报表中您就可以在各页间导航或按数据值进行搜索。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-106">The report opens in HTML format and includes the report toolbar so that you can navigate pages or search on data values within the report.</span></span> <span data-ttu-id="1a8d4-107">您可以在 URL 中设置参数以隐藏报表工具栏或选择报表的输出格式。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-107">You can set parameters on the URL to hide the toolbar or select the output format of the report.</span></span>  
  
 <span data-ttu-id="1a8d4-108">这种通过报表的 Web 地址打开报表的方法适合查看报表，但不适合管理报表。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-108">Opening a report through its Web address is suitable for viewing a report, but not managing a report.</span></span> <span data-ttu-id="1a8d4-109">通过这种方法，无法访问项的属性页或订阅定义页。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-109">You cannot access an item's property pages or subscription definition pages.</span></span> <span data-ttu-id="1a8d4-110">必须使用报表管理器或 SharePoint 站点来完成这些任务。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-110">You must use Report Manager or a SharePoint site for those tasks.</span></span>  
  
 <span data-ttu-id="1a8d4-111">如果不知道某一报表的 Web 地址，则可以打开相应报表服务器的 Web 地址，然后浏览报表服务器文件夹层次结构以选择要查看的报表。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-111">If you do not know the Web address of a report, you can open the Web address of the report server and then browse the report server folder hierarchy to select the report you want to view.</span></span> <span data-ttu-id="1a8d4-112">下图显示了在浏览器窗口中显示的文件夹层次结构。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-112">The following diagram illustrates a folder hierarchy as it appears in a browser window.</span></span>  
  
 <span data-ttu-id="1a8d4-113">![浏览器中的文件夹](../media/rs-browserfolder.GIF "浏览器中的文件夹")</span><span class="sxs-lookup"><span data-stu-id="1a8d4-113">![Folders in a browser](../media/rs-browserfolder.GIF "Folders in a browser")</span></span>  
<span data-ttu-id="1a8d4-114">浏览器中的文件夹</span><span class="sxs-lookup"><span data-stu-id="1a8d4-114">Folders in a browser</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a8d4-115">如果是通过手持设备访问报表，则必须使用浏览器打开报表。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-115">If you are accessing a report from a handheld device, you must use a browser to open a report.</span></span> <span data-ttu-id="1a8d4-116">报表管理器界面的大小不适于在手持设备上显示。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-116">Report Manager is not scaled for handheld devices.</span></span>  
  
 <span data-ttu-id="1a8d4-117">有关可以使用的浏览器类型的详细信息，请参阅 SQL Server 联机丛书中 [Reporting Services 文档](https://go.microsoft.com/fwlink/?linkid=121312) 中的“Reporting Services 支持的浏览器类型”。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-117">For more information about types of browsers that you can use, see "Browser Types Supported by Reporting Services" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="navigating-report-server-folders-in-a-web-browser"></a><span data-ttu-id="1a8d4-118">在 Web 浏览器中定位报表服务器文件夹</span><span class="sxs-lookup"><span data-stu-id="1a8d4-118">Navigating Report Server Folders in a Web Browser</span></span>  
 <span data-ttu-id="1a8d4-119">您可以使用 Web 浏览器定位报表服务器文件夹并运行报表。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-119">You can use a Web browser to navigate report server folders and run reports.</span></span> <span data-ttu-id="1a8d4-120">报表和项在文件夹层次结构中以链接的形式显示。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-120">Reports and items are displayed as links in the folder hierarchy.</span></span> <span data-ttu-id="1a8d4-121">您可以单击链接打开报表、资源或文件夹，或者查看共享数据源的内容。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-121">You can click links to open a report, resource, or folder, or view the contents of a shared data source.</span></span> <span data-ttu-id="1a8d4-122">如果不知道报表的 URL，则可以浏览文件夹层次结构。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-122">Navigating the folder hierarchy is useful if you do not know the URL of a report.</span></span> <span data-ttu-id="1a8d4-123">您可以指定报表服务器的 Web 地址，以在文件夹层次结构的根节点处打开浏览器连接，然后单击文件夹链接以在此层次结构中导航。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-123">You can specify the report server Web address to open a browser connection at the root node of the folder hierarchy, and then click folder links to navigate through the hierarchy.</span></span>  
  
 <span data-ttu-id="1a8d4-124">在访问报表服务器虚拟目录时，您只能查看文件夹、报表以及您可以访问的上载项。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-124">When you access a report server virtual directory, you see only the folders, reports, and uploaded items to which you have access.</span></span> <span data-ttu-id="1a8d4-125">该用户界面只显示文件夹层次结构和基本信息，如创建日期或修改日期、文件大小以及各项的项类型：</span><span class="sxs-lookup"><span data-stu-id="1a8d4-125">The user interface shows only the folder hierarchy and basic information, such as creation or modification date, file size, and item type for individual items:</span></span>  
  
-   <span data-ttu-id="1a8d4-126">不带任何其他指示符的链接指向的是报表或模型。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-126">A link with no other indicator is a report or a model.</span></span>  
  
-   <span data-ttu-id="1a8d4-127">标记 \<ds> 表示共享数据源。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-127">The tag \<ds> indicates a shared data source.</span></span>  
  
-   <span data-ttu-id="1a8d4-128">标记 \<dir> 指示文件夹项。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-128">The tag \<dir> indicates a folder item.</span></span>  
  
-   <span data-ttu-id="1a8d4-129">一种文件扩展名表示一种资源。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-129">A file name extension indicates a resource.</span></span> <span data-ttu-id="1a8d4-130">文件扩展名用于标识资源的 MIME 类型。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-130">The file name extension identifies the MIME type of the resource.</span></span> <span data-ttu-id="1a8d4-131">例如，.jpg 表示 JPEG 格式的图像。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-131">For example, .jpg indicates an image in JPEG format.</span></span>  
  
## <a name="typing-the-url-address-of-a-report"></a><span data-ttu-id="1a8d4-132">键入报表的 URL 地址</span><span class="sxs-lookup"><span data-stu-id="1a8d4-132">Typing the URL Address of a Report</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="1a8d4-133">支持通过 URL 访问报表服务器上的特定项。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-133">supports URL access to specific items on a report server.</span></span> <span data-ttu-id="1a8d4-134">相应的 URL 必须包含报表的完全限定路径以及用来呈现报表的命令。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-134">The URL must include a fully qualified path to the report and commands to render the report.</span></span> <span data-ttu-id="1a8d4-135">如果相应报表包含参数，您还必须指定打开此报表所需的所有值。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-135">If the report includes parameters, you must also specify any values that are required to open the report.</span></span> <span data-ttu-id="1a8d4-136">如果您键入的报表 URL 在路径、参数值或呈现扩展插件中包含空格，则必须在该 URL 中加入 URL 编码字符才能获得预期的结果。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-136">If you are typing a URL for a report that includes spaces in the path, parameter values, or a rendering extension, you must incorporate URL encoded characters into the URL to get the results you expect.</span></span> <span data-ttu-id="1a8d4-137">下例是一个在路径名称、参数和呈现扩展插件中包含空格编码的报表 URL：</span><span class="sxs-lookup"><span data-stu-id="1a8d4-137">The following example illustrates a report URL that includes encoding for spaces in the path name, parameters, and a rendering extension:</span></span>  
  
 `http://<Webservername>/reportserver?/<reportfolder>/employee+sales+summary&ReportYear=2004&ReportMonth=06&EmpID=24&rs:Command=Render&rs:Format=HTML4.0`  
  
 <span data-ttu-id="1a8d4-138">在 Internet Explorer 中对 URL 的最大长度限制为 2,083 个字符。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-138">The maximum limit for a URL in Internet Explorer is 2,083 characters.</span></span> <span data-ttu-id="1a8d4-139">有关详细信息，请参阅 [Internet Explorer 中的最大 URL 长度](https://support.microsoft.com/kb/208427)。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-139">For more information, see [Maximum URL length in Internet Explorer](https://support.microsoft.com/kb/208427).</span></span>  
  
 <span data-ttu-id="1a8d4-140">有关通过 URL 访问报表的详细信息，包括有关 URL 构造方式的信息，请参阅 SQL Server 联机丛书中 [Reporting Services 文档](https://go.microsoft.com/fwlink/?linkid=121312) 中的“URL 访问”。</span><span class="sxs-lookup"><span data-stu-id="1a8d4-140">For more information about how to access a report through a URL, including information on how a URL is constructed, see "URL Access" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a8d4-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1a8d4-141">See Also</span></span>  
 [<span data-ttu-id="1a8d4-142">在报表管理器中查找和查看报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="1a8d4-142">Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;</span></span>](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)  
  
  
