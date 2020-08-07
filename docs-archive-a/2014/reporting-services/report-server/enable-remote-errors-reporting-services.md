---
title: 启用远程错误 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- remote data source [Reporting Services]
- EnableRemoteError server property
ms.assetid: 5f05022b-d557-43e0-b50a-f5e2a1846b83
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d2a7e7e0b38b38bf563dfc2a8cff65c897c5293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588275"
---
# <a name="enable-remote-errors-reporting-services"></a><span data-ttu-id="94ad2-102">启用远程错误 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="94ad2-102">Enable Remote Errors (Reporting Services)</span></span>
  <span data-ttu-id="94ad2-103">可以将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表服务器上的服务器属性设置为返回远程服务器上所发生的错误情形的其他信息。</span><span class="sxs-lookup"><span data-stu-id="94ad2-103">You can set server properties on a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server to return additional information about error conditions that occur on remote servers.</span></span> <span data-ttu-id="94ad2-104">如果错误消息中包含文本“有关此错误的详细信息，请导航到本地服务器上的报表服务器或启用远程错误”，则可以将 `EnableRemoteErrors` 属性设置为访问可帮助您解决问题的其他信息。</span><span class="sxs-lookup"><span data-stu-id="94ad2-104">If an error message contains the text "For more information about this error, navigate to the report server on the local server machine, or enable remote errors", you can set the `EnableRemoteErrors` property to access additional information that can help you troubleshoot the problem.</span></span> <span data-ttu-id="94ad2-105">有关详细信息，请参阅 [联机丛书中的](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) 报表服务器系统属性 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="94ad2-105">For more information, see [Report Server System Properties](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="94ad2-106">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="94ad2-106">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="94ad2-107">为 SharePoint 模式启用远程错误</span><span class="sxs-lookup"><span data-stu-id="94ad2-107">Enable Remote Errors for SharePoint Mode</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="94ad2-108">通过 SQL Server Management Studio 启用远程错误（本机模式）</span><span class="sxs-lookup"><span data-stu-id="94ad2-108">Enable remote errors through SQL Server Management Studio (Native Mode)</span></span>](#bkmk_mgtStudio)  
  
-   [<span data-ttu-id="94ad2-109">通过脚本启用远程错误（本机模式）</span><span class="sxs-lookup"><span data-stu-id="94ad2-109">Enable remote errors through script (Native Mode)</span></span>](#bkmk_script)  
  
-   [<span data-ttu-id="94ad2-110">修改 ConfigurationInfo 表（本机模式）</span><span class="sxs-lookup"><span data-stu-id="94ad2-110">Modifying the ConfigurationInfo table (Native Mode)</span></span>](#bkmk_ConfigurationInfo)  
  
##  <a name="enable-remote-errors-for-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="94ad2-111">为 SharePoint 模式启用远程错误</span><span class="sxs-lookup"><span data-stu-id="94ad2-111">Enable Remote Errors for SharePoint Mode</span></span>  
 <span data-ttu-id="94ad2-112">可以通过两个不同的过程为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式启用远程错误。</span><span class="sxs-lookup"><span data-stu-id="94ad2-112">There are two different procedures for enabling remote errors for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="94ad2-113">对于两个不同的报表服务器体系结构，过程是不同的。</span><span class="sxs-lookup"><span data-stu-id="94ad2-113">The procedure is different for the two different report server architectures.</span></span> <span data-ttu-id="94ad2-114">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 版本中引入的基于较新的 SharePoint 服务的体系结构利用可为每个 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序配置的设置。</span><span class="sxs-lookup"><span data-stu-id="94ad2-114">The newer SharePoint service based architecture that was introduced in the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] release, utilizes a setting that can be configured for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="94ad2-115">较旧的体系结构利用单一站点级别的设置。</span><span class="sxs-lookup"><span data-stu-id="94ad2-115">The older architecture utilizes a single site level setting.</span></span>  
  
#### <a name="enable-remote-errors-for-a-reporting-services-service-application"></a><span data-ttu-id="94ad2-116">为 Reporting Services 服务应用程序启用远程错误</span><span class="sxs-lookup"><span data-stu-id="94ad2-116">Enable Remote errors for a Reporting Services Service Application</span></span>  
  
1.  <span data-ttu-id="94ad2-117">对于随 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或较新版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]一起安装的 SharePoint 模式报表服务器，启用服务应用程序设置 **“启用远程错误”** 。</span><span class="sxs-lookup"><span data-stu-id="94ad2-117">For a SharePoint mode report server installed with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or a newer version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], enable the service application setting **Enable remote errors**.</span></span> <span data-ttu-id="94ad2-118">可为每个 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序配置该设置。</span><span class="sxs-lookup"><span data-stu-id="94ad2-118">The setting can be configured for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
2.  <span data-ttu-id="94ad2-119">在 SharePoint 管理中心的 **“应用程序管理”** 组中，单击 **“管理服务应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="94ad2-119">In SharePoint Central Administration, click **Manage service applications** in the **Application Management** group.</span></span>  
  
3.  <span data-ttu-id="94ad2-120">找到您的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序并单击其名称。</span><span class="sxs-lookup"><span data-stu-id="94ad2-120">Find your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application and click the name of your service application.</span></span>  
  
4.  <span data-ttu-id="94ad2-121">单击 **“系统设置”** 。</span><span class="sxs-lookup"><span data-stu-id="94ad2-121">Click **System Settings**.</span></span>  
  
5.  <span data-ttu-id="94ad2-122">在 **“安全性”** 部分，单击 **“启用远程错误”** 。</span><span class="sxs-lookup"><span data-stu-id="94ad2-122">Click **Enable Remote Errors** in the **Security** section.</span></span>  
  
6.  <span data-ttu-id="94ad2-123">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="94ad2-123">Click **OK**.</span></span>  
  
#### <a name="enable-remote-errors-for-a-sharepoint-site"></a><span data-ttu-id="94ad2-124">为 SharePoint 站点启用远程错误</span><span class="sxs-lookup"><span data-stu-id="94ad2-124">Enable Remote Errors for a SharePoint Site</span></span>  
  
1.  <span data-ttu-id="94ad2-125">对于随 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 之前的 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]版本安装的 SharePoint 模式报表服务器，启用站点设置 **“启用本地模式下的远程错误”** 。</span><span class="sxs-lookup"><span data-stu-id="94ad2-125">For a SharePoint mode report server installed with a version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] prior to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], enable the site setting **Enable remote errors in local mode**.</span></span>  
  
2.  <span data-ttu-id="94ad2-126">在 **“站点操作”** 中，单击您要修改的站点对应的 **“站点设置”** 。</span><span class="sxs-lookup"><span data-stu-id="94ad2-126">In **Site Actions** click **Site Settings** for the site you want to modify.</span></span>  
  
3.  <span data-ttu-id="94ad2-127">在 **“Reporting Services”** 组，单击 **“Reporting Services 站点设置”** 。</span><span class="sxs-lookup"><span data-stu-id="94ad2-127">Click **Reporting Services Site Settings** in the **Reporting Services** group.</span></span>  
  
4.  <span data-ttu-id="94ad2-128">单击 **“启用本地模式下的远程错误”** 。</span><span class="sxs-lookup"><span data-stu-id="94ad2-128">Click **Enable remote errors in local mode**.</span></span>  
  
5.  <span data-ttu-id="94ad2-129">单击 **“确定”**</span><span class="sxs-lookup"><span data-stu-id="94ad2-129">Click **OK**</span></span>  
  
##  <a name="enable-remote-errors-through-sql-server-management-studio-native-mode"></a><a name="bkmk_mgtStudio"></a> <span data-ttu-id="94ad2-130">通过 SQL Server Management Studio 启用远程错误（本机模式）</span><span class="sxs-lookup"><span data-stu-id="94ad2-130">Enable remote errors through SQL Server Management Studio (Native Mode)</span></span>  
  
1.  <span data-ttu-id="94ad2-131">启动 Management Studio 并连接到报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="94ad2-131">Start Management Studio and connect to a report server instance.</span></span> <span data-ttu-id="94ad2-132">有关详细信息，请参阅 [联机丛书中的](../tools/connect-to-a-report-server-in-management-studio.md) 连接到 Management Studio 中的报表服务器 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="94ad2-132">For more information, see [Connect to a Report Server in Management Studio](../tools/connect-to-a-report-server-in-management-studio.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="94ad2-133">右键单击报表服务器节点，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="94ad2-133">Right-click the report server node, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="94ad2-134">单击 **“高级”** 以打开属性页。</span><span class="sxs-lookup"><span data-stu-id="94ad2-134">Click **Advanced** to open the properties page.</span></span> <span data-ttu-id="94ad2-135">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的[服务器属性（“高级”页）- Reporting Services](../tools/server-properties-advanced-page-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="94ad2-135">For more information, see [Server Properties &#40;Advanced Page&#41; - Reporting Services](../tools/server-properties-advanced-page-reporting-services.md)in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
4.  <span data-ttu-id="94ad2-136">在中 `EnableRemoteErrors` ，选择 `True` 。</span><span class="sxs-lookup"><span data-stu-id="94ad2-136">In `EnableRemoteErrors`, select `True`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="enable-remote-errors-through-script-native-mode"></a><a name="bkmk_script"></a> <span data-ttu-id="94ad2-137">通过脚本启用远程错误（本机模式）</span><span class="sxs-lookup"><span data-stu-id="94ad2-137">Enable remote errors through script (Native Mode)</span></span>  
  
1.  <span data-ttu-id="94ad2-138">创建文本文件并将以下脚本复制到该文件中。</span><span class="sxs-lookup"><span data-stu-id="94ad2-138">Create a text file and copy the following script into the file.</span></span>  
  
    ```  
    Public Sub Main()  
      Dim P As New [Property]()  
      P.Name = "EnableRemoteErrors"  
      P.Value = True  
      Dim Properties(0) As [Property]  
      Properties(0) = P  
      Try  
        rs.SetSystemProperties(Properties)  
        Console.WriteLine("Remote errors enabled.")  
      Catch SE As SoapException  
        Console.WriteLine(SE.Detail.OuterXml)  
      End Try  
    End Sub  
    ```  
  
2.  <span data-ttu-id="94ad2-139">将文件另存为 EnableRemoteErrors.rss。</span><span class="sxs-lookup"><span data-stu-id="94ad2-139">Save the file as EnableRemoteErrors.rss.</span></span>  
  
3.  <span data-ttu-id="94ad2-140">单击 **“开始”** ，指向 **“运行”** ，键入 **cmd**，再单击 **“确定”** 打开命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="94ad2-140">Click **Start**, point to **Run**, type **cmd**, and click **OK** to open a command prompt window.</span></span>  
  
4.  <span data-ttu-id="94ad2-141">导航到包含您刚刚创建的 .rss 文件的目录。</span><span class="sxs-lookup"><span data-stu-id="94ad2-141">Navigate to the directory that contains the .rss file you just created.</span></span>  
  
5.  <span data-ttu-id="94ad2-142">键入以下命令行，并将 *servername* 替换为服务器的实际名称：</span><span class="sxs-lookup"><span data-stu-id="94ad2-142">Type the following command line, replacing *servername* with the actual name of your server:</span></span>  
  
    ```  
    rs -i EnableRemoteErrors.rss -s http://servername/ReportServer  
    ```  
  
6.  <span data-ttu-id="94ad2-143">有关详细信息，请参阅 [RS.exe 实用工具 (SSRS)](../tools/rs-exe-utility-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="94ad2-143">For more information, see [RS.exe Utility &#40;SSRS&#41;](../tools/rs-exe-utility-ssrs.md)</span></span>  
  
##  <a name="modifying-the-configurationinfo-table-native-mode"></a><a name="bkmk_ConfigurationInfo"></a> <span data-ttu-id="94ad2-144">修改 ConfigurationInfo 表（本机模式）</span><span class="sxs-lookup"><span data-stu-id="94ad2-144">Modifying the ConfigurationInfo table (Native Mode)</span></span>  
  
1.  > [!NOTE]  
    >  <span data-ttu-id="94ad2-145">您可以编辑 Report Server 数据库中的**ConfigurationInfo**表以设置 `EnableRemoteErrors` 为 `True` ，但如果 Report Server 正在使用中，则应使用 SQL Server Management Studio 或脚本来修改设置。</span><span class="sxs-lookup"><span data-stu-id="94ad2-145">You can edit the **ConfigurationInfo** table in the report server database to set `EnableRemoteErrors` to `True`, but if the report server is actively used, you should use SQL Server Management Studio or script to modify the settings.</span></span> <span data-ttu-id="94ad2-146">如果修改了数据库中的设置，则需要重新启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务，然后更改才会生效。</span><span class="sxs-lookup"><span data-stu-id="94ad2-146">If you modify the setting in the database, you need to restart the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service before the changes take effect.</span></span>  
  
  
