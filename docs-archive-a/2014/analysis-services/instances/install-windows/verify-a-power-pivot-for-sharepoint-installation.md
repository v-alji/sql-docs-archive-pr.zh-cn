---
title: 验证 PowerPivot for SharePoint 安装 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 855bd055-5ad3-493f-9c5b-1f5297b2e6e2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0f45e1aa1d48dd5a50b7ce38dc364089d438f215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588744"
---
# <a name="verify-a-powerpivot-for-sharepoint-installation"></a><span data-ttu-id="61a63-102">验证 PowerPivot for SharePoint 安装</span><span class="sxs-lookup"><span data-stu-id="61a63-102">Verify a PowerPivot for SharePoint Installation</span></span>
  <span data-ttu-id="61a63-103">您在 SharePoint 场中安装的 PowerPivot for SharePoint 实例通过 SharePoint 管理中心进行管理。</span><span class="sxs-lookup"><span data-stu-id="61a63-103">A PowerPivot for SharePoint instance that you install in a SharePoint farm is administered through SharePoint Central Administration.</span></span> <span data-ttu-id="61a63-104">至少，您可以检查管理中心和 SharePoint 网站上的页面以便确认 PowerPivot 服务器组件和功能可用。</span><span class="sxs-lookup"><span data-stu-id="61a63-104">At a minimum, you can check pages in Central Administration and on SharePoint sites to verify that PowerPivot server components and features are available.</span></span> <span data-ttu-id="61a63-105">但是，若要完全验证某一安装，您必须具有可发布到 SharePoint 并从库中访问的 PowerPivot 工作簿。</span><span class="sxs-lookup"><span data-stu-id="61a63-105">However, to fully verify an installation, you must have a PowerPivot workbook that you can publish to SharePoint and access from a library.</span></span> <span data-ttu-id="61a63-106">出于测试目的，您可以发布已包含 PowerPivot 数据的示例工作簿并使用它来确认 SharePoint 集成已正确配置。</span><span class="sxs-lookup"><span data-stu-id="61a63-106">For testing purposes, you can publish a sample workbook that already contains PowerPivot data and use it to confirm that SharePoint integration is correctly configured.</span></span>  
  
##  <a name="verify-central-administration-integration"></a><a name="verifyinstall"></a> <span data-ttu-id="61a63-107">验证管理中心集成</span><span class="sxs-lookup"><span data-stu-id="61a63-107">Verify Central Administration Integration</span></span>  
 <span data-ttu-id="61a63-108">若要验证 PowerPivot 与管理中心的集成，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="61a63-108">To verify PowerPivot integration with Central Administration, do the following:</span></span>  
  
1.  <span data-ttu-id="61a63-109">在 "开始" 菜单上，单击 "**所有程序**"，打开 "Microsoft SharePoint 2010 产品"，然后单击 " **SharePoint 2010 管理中心**"。</span><span class="sxs-lookup"><span data-stu-id="61a63-109">On the Start menu, click **All Programs**, open Microsoft SharePoint 2010 Products, and click **SharePoint 2010 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="61a63-110">输入您的用户名和密码，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="61a63-110">Enter your user name and password, and then click **OK**.</span></span>  
  
     <span data-ttu-id="61a63-111">或者，您可以修改浏览器设置，以便避免每次打开管理中心时都不得不输入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="61a63-111">Optionally, you can modify browser settings to avoid having to enter a user name and password each time you open Central Administration.</span></span> <span data-ttu-id="61a63-112">若要将管理中心作为可信站点添加，请执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="61a63-112">To add Central Administration as a trusted site, do the following.</span></span>  
  
    1.  <span data-ttu-id="61a63-113">在 Internet Explorer 的 "工具" 菜单上，单击 " **Internet 选项**"。</span><span class="sxs-lookup"><span data-stu-id="61a63-113">In Internet Explorer, on the Tools menu, click **Internet options**.</span></span>  
  
    2.  <span data-ttu-id="61a63-114">在“安全”选项卡中，在 **“选择要查看或更改安全设置的区域”** 部分中，单击“受信任的站点”，然后单击“站点”。</span><span class="sxs-lookup"><span data-stu-id="61a63-114">On the Security tab, in the **Select a zone to view or change security settings** section, click Trusted Sites, and then click Sites.</span></span>  
  
    3.  <span data-ttu-id="61a63-115">取消选中“对该区域中的所有站点要求服务器验证(https:)”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="61a63-115">Clear the **Require server verification (https:) for all sites in this zone** checkbox.</span></span>  
  
    4.  <span data-ttu-id="61a63-116">在 **“将该网站添加到区域中”** 中，键入您的网站的 URL，然后单击 **“添加”**。</span><span class="sxs-lookup"><span data-stu-id="61a63-116">In **Add this Web site to the zone**, type the URL to your site, and then click **Add**.</span></span>  
  
    5.  <span data-ttu-id="61a63-117">单击“关闭”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="61a63-117">Click **Close**, and then click **OK**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="61a63-118">SharePoint 安装文档包含有关解决代理服务器错误和禁用 Internet Explorer 安全增强配置的附加说明，以便您可以下载和安装更新。</span><span class="sxs-lookup"><span data-stu-id="61a63-118">SharePoint installation documentation includes additional instructions for working around proxy server errors and for disabling Internet Explorer Enhanced Security Configuration so that you can download and install updates.</span></span> <span data-ttu-id="61a63-119">有关详细信息，请参阅 Microsoft 网站上 **Deploy a single server with SQL Server** （部署单台带有 SQL Server 的服务器）中的 [Perform additional tasks](https://go.microsoft.com/fwlink/?LinkId=177754) “执行附加任务”部分。</span><span class="sxs-lookup"><span data-stu-id="61a63-119">For more information, see the **Perform additional tasks** section in [Deploy a single server with SQL Server](https://go.microsoft.com/fwlink/?LinkId=177754) on the Microsoft web site.</span></span>  
  
3.  <span data-ttu-id="61a63-120">在管理中心的“系统设置”中，单击 **“管理场功能”**。</span><span class="sxs-lookup"><span data-stu-id="61a63-120">In Central Administration, in System Settings, click **Manage farm features**.</span></span>  
  
4.  <span data-ttu-id="61a63-121">确认 **“PowerPivot 集成功能”** 为 **“活动”**。</span><span class="sxs-lookup"><span data-stu-id="61a63-121">Verify that **PowerPivot Integration Feature** is **Active**.</span></span>  
  
5.  <span data-ttu-id="61a63-122">在管理中心的 "系统设置" 中，单击 "**管理服务器上的服务**"。</span><span class="sxs-lookup"><span data-stu-id="61a63-122">In Central Administration, in System Settings, click **Manage services on server**.</span></span>  
  
6.  <span data-ttu-id="61a63-123">验证 **SQL Server Analysis Services** 和 **SQL Server PowerPivot 系统服务** 是否已启动。</span><span class="sxs-lookup"><span data-stu-id="61a63-123">Verify that **SQL Server Analysis Services** and **SQL Server PowerPivot System Service** are started.</span></span>  
  
7.  <span data-ttu-id="61a63-124">在“管理中心”的“应用程序管理”中，单击 **“管理服务应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="61a63-124">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
8.  <span data-ttu-id="61a63-125">单击 "**默认 PowerPivot 服务应用程序**" 以便为此应用程序打开 PowerPivot 管理面板。</span><span class="sxs-lookup"><span data-stu-id="61a63-125">Click **Default PowerPivot Service Application** to open PowerPivot Management Dashboard for this application.</span></span> <span data-ttu-id="61a63-126">第一次使用时，面板要花几分钟的加载时间。</span><span class="sxs-lookup"><span data-stu-id="61a63-126">On first use, the dashboard takes several minutes to load.</span></span>  
  
     <span data-ttu-id="61a63-127">或者，单击 "**默认 PowerPivot 服务应用程序**" 旁边的空白区域以选择该行，然后单击 "**属性**" 以查看此服务应用程序的配置设置。</span><span class="sxs-lookup"><span data-stu-id="61a63-127">Alternatively, click the empty space next to **Default PowerPivot Service Application** to select the row, and click **Properties** to view the configuration settings for this service application.</span></span> <span data-ttu-id="61a63-128">您可以修改配置设置和应用程序属性以更改服务器配置。</span><span class="sxs-lookup"><span data-stu-id="61a63-128">You can modify both configuration settings and application properties to change your server configuration.</span></span> <span data-ttu-id="61a63-129">有关这些设置的详细信息，请参阅[在管理中心中创建和配置 PowerPivot 服务应用程序](../../power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)。</span><span class="sxs-lookup"><span data-stu-id="61a63-129">For more information about these settings, see [Create and Configure a PowerPivot Service Application in Central Administration](../../power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md).</span></span>  
  
## <a name="verify-integration-at-the-site-level"></a><span data-ttu-id="61a63-130">验证网站级别的集成</span><span class="sxs-lookup"><span data-stu-id="61a63-130">Verify Integration at the Site Level</span></span>  
 <span data-ttu-id="61a63-131">若要验证 PowerPivot 与 SharePoint 网站的集成，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="61a63-131">To verify PowerPivot integration with a SharePoint site, do the following:</span></span>  
  
1.  <span data-ttu-id="61a63-132">在浏览器中，打开您创建的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="61a63-132">In a browser, open the Web application you created.</span></span> <span data-ttu-id="61a63-133">如果使用了默认值，则可以 \<your computer name> 在 URL 地址中指定 http://。</span><span class="sxs-lookup"><span data-stu-id="61a63-133">If you used default values, you can specify http://\<your computer name> in the URL address.</span></span>  
  
2.  <span data-ttu-id="61a63-134">验证 PowerPivot 数据访问和处理功能在应用程序中可用。</span><span class="sxs-lookup"><span data-stu-id="61a63-134">Verify that PowerPivot data access and processing features are available in the application.</span></span> <span data-ttu-id="61a63-135">您可以通过验证 PowerPivot 提供的库模板是否存在来验证此可用性：</span><span class="sxs-lookup"><span data-stu-id="61a63-135">You can do this by verifying the presence of PowerPivot-provided library templates:</span></span>  
  
    1.  <span data-ttu-id="61a63-136">在 "网站操作" 上，单击 "**更多选项 ...**"</span><span class="sxs-lookup"><span data-stu-id="61a63-136">On Site Actions, click **More Options..**.</span></span>  
  
    2.  <span data-ttu-id="61a63-137">在 "库" 中，应会看到 "**数据馈送库**" 和 " **PowerPivot 库**"。</span><span class="sxs-lookup"><span data-stu-id="61a63-137">In Libraries, you should see **Data Feed Library** and **PowerPivot Gallery**.</span></span> <span data-ttu-id="61a63-138">这些库模板由 PowerPivot 功能提供，并且在正确集成了该功能的情况下在“库”列表中将可见。</span><span class="sxs-lookup"><span data-stu-id="61a63-138">These library templates are provided by the PowerPivot feature and will be visible in the Libraries list if the feature is integrated correctly.</span></span>  
  
## <a name="verify-data-access-on-the-server"></a><span data-ttu-id="61a63-139">验证服务器上的数据访问。</span><span class="sxs-lookup"><span data-stu-id="61a63-139">Verify Data Access on the Server</span></span>  
 <span data-ttu-id="61a63-140">若要验证服务器上的 PowerPivot 数据访问，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="61a63-140">To verify PowerPivot data access on the server, do the following:</span></span>  
  
1.  <span data-ttu-id="61a63-141">[下载](https://go.microsoft.com/fwlink/?LinkID=219108) Reporting Services 教程附带的“野餐”数据示例。</span><span class="sxs-lookup"><span data-stu-id="61a63-141">[Download](https://go.microsoft.com/fwlink/?LinkID=219108) the Picnic data sample that accompanies a Reporting Services tutorial.</span></span> <span data-ttu-id="61a63-142">您将使用此下载中的示例工作簿来验证 PowerPivot 数据访问。</span><span class="sxs-lookup"><span data-stu-id="61a63-142">You will use the sample workbook in this download to verify PowerPivot data access.</span></span> <span data-ttu-id="61a63-143">解压缩文件。</span><span class="sxs-lookup"><span data-stu-id="61a63-143">Extract the files.</span></span>  
  
2.  <span data-ttu-id="61a63-144">将 Excel 工作簿 (.xlsx) 上载到“共享文档”。</span><span class="sxs-lookup"><span data-stu-id="61a63-144">Upload the Excel workbook (.xlsx) to Shared Documents.</span></span> <span data-ttu-id="61a63-145">该工作簿包含嵌入的 PowerPivot 数据。</span><span class="sxs-lookup"><span data-stu-id="61a63-145">The workbook contains embedded PowerPivot data.</span></span>  
  
3.  <span data-ttu-id="61a63-146">单击该文档以便从库中打开它。</span><span class="sxs-lookup"><span data-stu-id="61a63-146">Click on the document to open it from the library.</span></span>  
  
4.  <span data-ttu-id="61a63-147">在该工作簿顶部单击某个切片器或筛选器。</span><span class="sxs-lookup"><span data-stu-id="61a63-147">Click on a slicer or filter at the top of the workbook.</span></span> <span data-ttu-id="61a63-148">月份、颜色和类型是此工作簿中的切片器。</span><span class="sxs-lookup"><span data-stu-id="61a63-148">Month, color, and type are slicers in this workbook.</span></span> <span data-ttu-id="61a63-149">单击切片器会启动 PowerPivot 查询并证明您的服务器可以正常运行。</span><span class="sxs-lookup"><span data-stu-id="61a63-149">Clicking a slicer starts a PowerPivot query and proves that your server is operational.</span></span> <span data-ttu-id="61a63-150">该服务器将在后台加载 PowerPivot 数据并返回结果。</span><span class="sxs-lookup"><span data-stu-id="61a63-150">The server will load PowerPivot data in the background and return the results.</span></span>  
  
5.  <span data-ttu-id="61a63-151">返回到库。</span><span class="sxs-lookup"><span data-stu-id="61a63-151">Go back to the library.</span></span> <span data-ttu-id="61a63-152">选择该工作簿右侧的向下箭头，然后单击 **“启动 Power View”**。</span><span class="sxs-lookup"><span data-stu-id="61a63-152">Select the down arrow to the right of the workbook, and then click **Launch Power View**.</span></span> <span data-ttu-id="61a63-153">此步骤确认 Reporting Services 中的 [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] 功能可以正常工作。</span><span class="sxs-lookup"><span data-stu-id="61a63-153">This step confirms that the [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] feature in Reporting Services is operational.</span></span> <span data-ttu-id="61a63-154">如果您未安装 Reporting Services，请跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="61a63-154">If you did not install Reporting Services, skip this step.</span></span>  
  
     <span data-ttu-id="61a63-155">在下一步骤中，您将在 Management Studio 中连接到该服务器以确认数据已加载并且缓存。</span><span class="sxs-lookup"><span data-stu-id="61a63-155">In the next step, you will connect to the server in Management Studio to verify the data is loaded and cached.</span></span>  
  
6.  <span data-ttu-id="61a63-156">从“开始”菜单中的 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 程序组启动 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="61a63-156">Start SQL Server Management Studio from the [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] program group in the Start menu.</span></span> <span data-ttu-id="61a63-157">如果未在您的服务器上安装此工具，则可以跳到最后一步以便确认缓存文件是否存在。</span><span class="sxs-lookup"><span data-stu-id="61a63-157">If this tool is not installed on your server, you can skip ahead to the last step to confirm the presence of cached files.</span></span>  
  
7.  <span data-ttu-id="61a63-158">在 "服务器类型" 中选择**Analysis Services**。</span><span class="sxs-lookup"><span data-stu-id="61a63-158">In Server Type, select **Analysis Services**.</span></span>  
  
8.  <span data-ttu-id="61a63-159">在 "服务器名称" 中，输入\*\* \<server-name> \powerpivot\*\*，其中 **\<server-name>** 是安装了 PowerPivot for SharePoint 的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="61a63-159">In Server Name, enter **\<server-name>\powerpivot**, where **\<server-name>** is the name of the computer that has the PowerPivot for SharePoint installation.</span></span>  
  
9. <span data-ttu-id="61a63-160">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="61a63-160">Click **Connect**.</span></span> <span data-ttu-id="61a63-161">这将验证 Analysis Services 服务器是否可用。</span><span class="sxs-lookup"><span data-stu-id="61a63-161">This verifies that the Analysis Services server is available.</span></span>  
  
10. <span data-ttu-id="61a63-162">在对象资源管理器中，可以单击 "**数据库**" 查看加载的 PowerPivot 数据文件的列表。</span><span class="sxs-lookup"><span data-stu-id="61a63-162">In Object Explorer, you can click **Databases** to view the list of PowerPivot data files that are loaded.</span></span>  
  
11. <span data-ttu-id="61a63-163">在计算机文件系统上，检查以下文件夹以便确定文件是否已缓存到磁盘。</span><span class="sxs-lookup"><span data-stu-id="61a63-163">On the computer file system, check the following folder to determine whether files are cached to disk.</span></span> <span data-ttu-id="61a63-164">存在缓存文件将进一步证实您的部署正常工作。</span><span class="sxs-lookup"><span data-stu-id="61a63-164">The presence of cached files is further verification that your deployment is operational.</span></span> <span data-ttu-id="61a63-165">若要查看文件缓存，请参阅 \<drive> ： \Program FILES\MICROSOFT SQL Server\MSAS11。POWERPIVOT\OLAP\Backup\Sandboxes\Default PowerPivot 服务应用程序文件夹。</span><span class="sxs-lookup"><span data-stu-id="61a63-165">To view the file cache, go to the \<drive>:\Program Files\Microsoft SQL Server\MSAS11.POWERPIVOT\OLAP\Backup\Sandboxes\Default PowerPivot Service Application folder.</span></span> <span data-ttu-id="61a63-166">每个缓存数据库均存储在自己的文件夹中，可使用基于 GUID 的命名约定来确保唯一名称。</span><span class="sxs-lookup"><span data-stu-id="61a63-166">Each cached database is stored in its own folder, using a GUID-based naming convention to ensure a unique name.</span></span>  
  
  
