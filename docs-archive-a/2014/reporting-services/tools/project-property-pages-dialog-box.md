---
title: “项目属性页”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rpt.rptdesigner.projectpropertypages.general.f1
helpviewer_keywords:
- Project Property Pages dialog box
ms.assetid: 209d9e22-37fc-418f-8739-83adcf447d3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ae5ab7c68c9a95759d27ca2785f99377c98942a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689737"
---
# <a name="project-property-pages-dialog-box"></a><span data-ttu-id="d8705-102">“项目属性页”对话框</span><span class="sxs-lookup"><span data-stu-id="d8705-102">Project Property Pages Dialog Box</span></span>
  <span data-ttu-id="d8705-103">使用项目属性页可以配置报表服务器项目的部署属性。</span><span class="sxs-lookup"><span data-stu-id="d8705-103">Use the project property pages to configure deployment properties for a Report Server project.</span></span> <span data-ttu-id="d8705-104">若要打开此对话框，请从 "**项目**" 菜单中单击 " _\<Report Project Name>_ **属性**"。</span><span class="sxs-lookup"><span data-stu-id="d8705-104">To open this dialog box, from the **Project** menu, click _\<Report Project Name>_**Properties**.</span></span>  
  
 <span data-ttu-id="d8705-105">定义配置属性后，可以从位于工具栏上的“解决方案配置”  下拉列表中选择配置。</span><span class="sxs-lookup"><span data-stu-id="d8705-105">After you define configuration properties, you can select a configuration from the **Solution Configurations** drop-down list on the toolbar.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d8705-106">选项</span><span class="sxs-lookup"><span data-stu-id="d8705-106">Options</span></span>  
 <span data-ttu-id="d8705-107">**配置**</span><span class="sxs-lookup"><span data-stu-id="d8705-107">**Configuration**</span></span>  
 <span data-ttu-id="d8705-108">选择要编辑的配置。</span><span class="sxs-lookup"><span data-stu-id="d8705-108">Select the configuration to edit.</span></span> <span data-ttu-id="d8705-109">最初，可使用以下配置： **Debug**、 **DebugLocal**和 **Release**。</span><span class="sxs-lookup"><span data-stu-id="d8705-109">Initially, the following configurations are available: **Debug**, **DebugLocal**, and **Release**.</span></span> <span data-ttu-id="d8705-110">首先显示活动配置，例如 **Active(Debug)**。</span><span class="sxs-lookup"><span data-stu-id="d8705-110">The active configuration appears first, for example, **Active(Debug)**.</span></span>  
  
 <span data-ttu-id="d8705-111">若要同时查看多个配置的属性，请选择 **“所有配置”** 或 **“多个配置”**。</span><span class="sxs-lookup"><span data-stu-id="d8705-111">To see properties for more than one configuration at the same time, select **All Configurations** or **Multiple Configurations**.</span></span>  
  
 <span data-ttu-id="d8705-112">若要创建其他配置，请单击工具栏上的 **“配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="d8705-112">To create additional configurations, click **Configuration Manager** on the toolbar.</span></span>  
  
 <span data-ttu-id="d8705-113">**Configuration Manager**</span><span class="sxs-lookup"><span data-stu-id="d8705-113">**Configuration Manager**</span></span>  
 <span data-ttu-id="d8705-114">管理整个解决方案的配置或添加其他配置。</span><span class="sxs-lookup"><span data-stu-id="d8705-114">Manage configurations for the entire solution or to add additional configurations.</span></span> <span data-ttu-id="d8705-115">有关详细信息，请参阅 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 文档。</span><span class="sxs-lookup"><span data-stu-id="d8705-115">For more information, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="d8705-116">**OutputPath**</span><span class="sxs-lookup"><span data-stu-id="d8705-116">**OutputPath**</span></span>  
 <span data-ttu-id="d8705-117">键入或粘贴用于存储在报表生成验证、部署和预览过程中使用的报表定义的路径。</span><span class="sxs-lookup"><span data-stu-id="d8705-117">Type or paste the path to store the report definition used in build verification, deployment, and preview of reports.</span></span> <span data-ttu-id="d8705-118">此路径必须与您用于项目的路径不同，并且它是一个相对路径（即项目路径下的一个子文件夹）。</span><span class="sxs-lookup"><span data-stu-id="d8705-118">The path must be different than the path that you use for the project and a relative path that is a child folder under the path of the project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8705-119">可以使用多个配置，以便根据您执行的任务在路径间切换。</span><span class="sxs-lookup"><span data-stu-id="d8705-119">You can use multiple configurations to switch among paths depending on the task you perform.</span></span>  
  
 <span data-ttu-id="d8705-120">**ErrorLevel**</span><span class="sxs-lookup"><span data-stu-id="d8705-120">**ErrorLevel**</span></span>  
 <span data-ttu-id="d8705-121">键入报告为错误的生成问题的严重性。</span><span class="sxs-lookup"><span data-stu-id="d8705-121">Type the severity of the build issues that are reported as errors.</span></span> <span data-ttu-id="d8705-122">严重级别小于或等于 **ErrorLevel** 的值的问题将报告为错误；否则，将问题报告为警告。</span><span class="sxs-lookup"><span data-stu-id="d8705-122">Issues with severity levels less than or equal to the value of **ErrorLevel** are reported as errors; otherwise, the issues are reported as warnings.</span></span> <span data-ttu-id="d8705-123">任何错误都将导致生成任务失败。</span><span class="sxs-lookup"><span data-stu-id="d8705-123">Any error will cause the build task to fail.</span></span> <span data-ttu-id="d8705-124">有效的严重级别为 0 到 4（包括这两者）。</span><span class="sxs-lookup"><span data-stu-id="d8705-124">The valid severity levels are 0 through 4 inclusively.</span></span> <span data-ttu-id="d8705-125">默认值为 2。</span><span class="sxs-lookup"><span data-stu-id="d8705-125">The default value is 2.</span></span>  
  
 <span data-ttu-id="d8705-126">**StartItem**</span><span class="sxs-lookup"><span data-stu-id="d8705-126">**StartItem**</span></span>  
 <span data-ttu-id="d8705-127">选择在项目发布到报表服务器之后将显示在 Web 浏览器中的报表，或选择在本地运行项目时将显示在预览窗口中的报表。</span><span class="sxs-lookup"><span data-stu-id="d8705-127">Select the report that is displayed in the Web browser after the project is published to the report server or in the preview window when the project is run locally.</span></span> <span data-ttu-id="d8705-128">对于生成项目但并不部署项目的配置，以及使用 **Debug** 命令 (**F5**)，启动项是必需的。</span><span class="sxs-lookup"><span data-stu-id="d8705-128">A start item is required for configurations that build but do not deploy the project and for using the **Debug** command (**F5**).</span></span> <span data-ttu-id="d8705-129">对于部署项目的配置，启动项也是必需的。</span><span class="sxs-lookup"><span data-stu-id="d8705-129">It is required for configurations that deploy the project.</span></span>  
  
 <span data-ttu-id="d8705-130">**OverwriteDataSources**</span><span class="sxs-lookup"><span data-stu-id="d8705-130">**OverwriteDataSources**</span></span>  
 <span data-ttu-id="d8705-131">选择 **True** 可在发布报表时使用项目中的数据源覆盖服务器上的数据源。</span><span class="sxs-lookup"><span data-stu-id="d8705-131">Select **True** to overwrite the data source on the server with the data source in the project when the reports are published.</span></span> <span data-ttu-id="d8705-132">选择 **False** 可保留服务器上的现有数据源。</span><span class="sxs-lookup"><span data-stu-id="d8705-132">Select **False** to leave the existing data source on the server.</span></span>  
  
 <span data-ttu-id="d8705-133">**TargetServerVersion**</span><span class="sxs-lookup"><span data-stu-id="d8705-133">**TargetServerVersion**</span></span>  
 <span data-ttu-id="d8705-134">选择 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 版本的， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 或者选择 "**检测版本**" 以自动确定安装在由**TargetServer URL**属性标识的服务器上的版本。</span><span class="sxs-lookup"><span data-stu-id="d8705-134">Select either the [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] or select **Detect Version** to automatically determine the version installed on the server identified by the **TargetServer URL** property.</span></span> <span data-ttu-id="d8705-135">默认值为 **SQL Server 2008 R2**。</span><span class="sxs-lookup"><span data-stu-id="d8705-135">The default value is **SQL Server 2008 R2**.</span></span>  
  
 <span data-ttu-id="d8705-136">**TargetDataSourceFolder**</span><span class="sxs-lookup"><span data-stu-id="d8705-136">**TargetDataSourceFolder**</span></span>  
 <span data-ttu-id="d8705-137">要在其中存储已发布共享数据源的文件夹的名称。</span><span class="sxs-lookup"><span data-stu-id="d8705-137">The name of the folder in which to store the published shared data sources.</span></span> <span data-ttu-id="d8705-138">如果您没有指定文件夹，那么数据源将发布到与报表所在文件夹相同的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d8705-138">If you do not specify a folder, the data source is published to the same folder as the report.</span></span> <span data-ttu-id="d8705-139">如果报表服务器上没有该文件夹，则报表设计器将在发布报表时创建该文件夹。</span><span class="sxs-lookup"><span data-stu-id="d8705-139">If the folder does not exist on the report server, Report Designer creates the folder when the reports are published.</span></span>  
  
 <span data-ttu-id="d8705-140">发布到在本机模式下运行的报表服务器时，指定文件夹层次结构的完整路径（从根文件夹开始）。</span><span class="sxs-lookup"><span data-stu-id="d8705-140">When publishing to a report server running in native mode, specify the full path of the folder hierarchy starting at the root.</span></span> <span data-ttu-id="d8705-141">例如，Folder1/Folder2/Folder3。</span><span class="sxs-lookup"><span data-stu-id="d8705-141">For example, Folder1/Folder2/Folder3.</span></span>  
  
 <span data-ttu-id="d8705-142">发布到在 SharePoint 集成模式下运行的报表服务器时，请使用 SharePoint 库的 URL。</span><span class="sxs-lookup"><span data-stu-id="d8705-142">When publishing to a report server running in SharePoint integrated mode, use a URL to the SharePoint library.</span></span> <span data-ttu-id="d8705-143">例如，http:// *\<servername>/\<site>* /documents/myfolder。</span><span class="sxs-lookup"><span data-stu-id="d8705-143">For example, http://*\<servername>/\<site>*/Documents/MyFolder.</span></span>  
  
 <span data-ttu-id="d8705-144">**TargetReportFolder**</span><span class="sxs-lookup"><span data-stu-id="d8705-144">**TargetReportFolder**</span></span>  
 <span data-ttu-id="d8705-145">要在其中存储已发布报表的文件夹的名称。</span><span class="sxs-lookup"><span data-stu-id="d8705-145">The name of the folder in which to store the published reports.</span></span> <span data-ttu-id="d8705-146">默认情况下，此名称即为报表项目的名称。</span><span class="sxs-lookup"><span data-stu-id="d8705-146">By default, this is the name of the report project.</span></span> <span data-ttu-id="d8705-147">如果报表服务器上没有该文件夹，则报表设计器将在发布报表时创建该文件夹。</span><span class="sxs-lookup"><span data-stu-id="d8705-147">If the folder does not exist on the report server, Report Designer creates the folder when the reports are published.</span></span>  
  
 <span data-ttu-id="d8705-148">发布到在本机模式下运行的报表服务器时，指定文件夹层次结构的完整路径（从根文件夹开始）。</span><span class="sxs-lookup"><span data-stu-id="d8705-148">When publishing to a report server running in native mode, specify the full path of the folder hierarchy starting at the root.</span></span> <span data-ttu-id="d8705-149">如果文件夹位于另一个文件夹内，则包括从根目录开始的到该文件夹的路径，如 Folder1/Folder2/Folder3。</span><span class="sxs-lookup"><span data-stu-id="d8705-149">If a folder is located within another folder, include a path to the folder starting at the root, such as Folder1/Folder2/Folder3.</span></span>  
  
 <span data-ttu-id="d8705-150">发布到在 SharePoint 集成模式下运行的报表服务器时，请使用 SharePoint 库的 URL。</span><span class="sxs-lookup"><span data-stu-id="d8705-150">When publishing to a report server running in SharePoint integrated mode, use a URL to SharePoint library.</span></span> <span data-ttu-id="d8705-151">例如，http:// *\<servername>* / *\<site>* /documents/myfolder。</span><span class="sxs-lookup"><span data-stu-id="d8705-151">For example, http://*\<servername>*/*\<site>*/Documents/MyFolder.</span></span>  
  
 <span data-ttu-id="d8705-152">**TargetServerURL**</span><span class="sxs-lookup"><span data-stu-id="d8705-152">**TargetServerURL**</span></span>  
 <span data-ttu-id="d8705-153">目标报表服务器的 URL。</span><span class="sxs-lookup"><span data-stu-id="d8705-153">The URL of the target report server.</span></span> <span data-ttu-id="d8705-154">在发布报表之前，必须将此属性设置为有效的报表服务器 URL。</span><span class="sxs-lookup"><span data-stu-id="d8705-154">Before you publish a report, you must set this property to a valid report server URL.</span></span>  
  
 <span data-ttu-id="d8705-155">发布到在本机模式下运行的报表服务器时，请使用此报表服务器的虚拟目录 URL。</span><span class="sxs-lookup"><span data-stu-id="d8705-155">When publishing to a report server running in native mode, use the URL of the virtual directory of the report server.</span></span> <span data-ttu-id="d8705-156">例如，http:// \<server> /reportserver。</span><span class="sxs-lookup"><span data-stu-id="d8705-156">For example, http://\<server>/reportserver.</span></span> <span data-ttu-id="d8705-157">这是报表服务器的虚拟目录，而不是报表管理器的虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="d8705-157">This is the virtual directory of the report server, not Report Manager.</span></span> <span data-ttu-id="d8705-158">默认情况下，报表服务器安装在名为“reportserver”的虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="d8705-158">By default, the report server is installed in a virtual directory named "reportserver".</span></span>  
  
 <span data-ttu-id="d8705-159">发布到在 SharePoint 集成模式下运行的报表服务器时，请使用 SharePoint 顶级站点或子站点的 URL。</span><span class="sxs-lookup"><span data-stu-id="d8705-159">When publishing to a report server running in SharePoint integrated mode, use a URL to a SharePoint top-level site or subsite.</span></span> <span data-ttu-id="d8705-160">如果不指定站点，将使用默认顶级站点。</span><span class="sxs-lookup"><span data-stu-id="d8705-160">If you do not specify a site, the default top-level site is used.</span></span> <span data-ttu-id="d8705-161">例如，http:// \<*servername> *、http://<* servername */\<*site>* 或 http:// \<*servername> */\<*site>* / \<*subsite> \*。</span><span class="sxs-lookup"><span data-stu-id="d8705-161">For example, http://\<*servername>*, http://<* servername*/\<*site>* or http://\<*servername>*/\<*site>*/\<*subsite>\*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8705-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8705-162">See Also</span></span>  
 <span data-ttu-id="d8705-163">[发布报表](../publish-reports.md) </span><span class="sxs-lookup"><span data-stu-id="d8705-163">[Publish Reports](../publish-reports.md) </span></span>  
 <span data-ttu-id="d8705-164">[将报表发布到 SharePoint 库](../reports/publish-a-report-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="d8705-164">[Publish a Report to a SharePoint Library](../reports/publish-a-report-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="d8705-165">[设置部署属性 &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="d8705-165">[Set Deployment Properties &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md) </span></span>  
 [<span data-ttu-id="d8705-166">报表设计器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="d8705-166">Report Designer F1 Help</span></span>](report-designer-f1-help.md)  
  
  
