---
title: SQL Server 2014 中 SQL Server Reporting Services 的行为更改 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- rows [Reporting Services], heights
- leading blanks
- installing Reporting Services, behavior changes with release
- cryptography [Reporting Services]
- Setup [Reporting Services], behavior changes with release
- DefaultValueQueryBased property
- encryption [Reporting Services]
- decryption [Reporting Services]
- blank characters [SQL Server]
- initializing installations [Reporting Services]
- behavior changes [Reporting Services]
ms.assetid: 2a767f0f-84f2-4099-8784-1e37790f858e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 966447192c492a907f0b506ae21befd513b2fcfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579533"
---
# <a name="behavior-changes-to-sql-server-reporting-services--in-sql-server-2014"></a><span data-ttu-id="01765-102">SQL Server 2014 中 SQL Server Reporting Services 的行为更改</span><span class="sxs-lookup"><span data-stu-id="01765-102">Behavior Changes to SQL Server Reporting Services  in SQL Server 2014</span></span>
  <span data-ttu-id="01765-103">本主题介绍 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]中的行为更改。</span><span class="sxs-lookup"><span data-stu-id="01765-103">This topic describes behavior changes in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="01765-104">与早期版本的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 相比， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中的功能的工作或交互方式会受到行为更改的影响。</span><span class="sxs-lookup"><span data-stu-id="01765-104">Behavior changes affect how features work or interact in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] as compared to previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="01765-105">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="01765-105">In this topic:</span></span>  
  
-   [<span data-ttu-id="01765-106">SQL Server 2014 Reporting Services 行为更改</span><span class="sxs-lookup"><span data-stu-id="01765-106">SQL Server 2014 Reporting Services Behavior Changes</span></span>](#bkmk_sql14)  
  
-   [<span data-ttu-id="01765-107">SQL Server 2012 Reporting Services 行为更改</span><span class="sxs-lookup"><span data-stu-id="01765-107">SQL Server 2012 Reporting Services Behavior Changes</span></span>](#bkmk_rc0)  
  
-   [<span data-ttu-id="01765-108">SQL Server 2008 R2 Reporting Services 行为更改</span><span class="sxs-lookup"><span data-stu-id="01765-108">SQL Server 2008 R2 Reporting Services Behavior Changes</span></span>](#bkmk_kj)  
  
##  <a name="sssql14-reporting-services-behavior-changes"></a><a name="bkmk_sql14"></a><span data-ttu-id="01765-109">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]Reporting Services 行为更改</span><span class="sxs-lookup"><span data-stu-id="01765-109">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services Behavior Changes</span></span>  
 <span data-ttu-id="01765-110">在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中没有 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]行为上的更改。</span><span class="sxs-lookup"><span data-stu-id="01765-110">There are no [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] behavior changes in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
##  <a name="sssql11-reporting-services-behavior-changes"></a><a name="bkmk_rc0"></a><span data-ttu-id="01765-111">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]Reporting Services 行为更改</span><span class="sxs-lookup"><span data-stu-id="01765-111">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services Behavior Changes</span></span>  
 <span data-ttu-id="01765-112">本节介绍 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 模式的行为更改。</span><span class="sxs-lookup"><span data-stu-id="01765-112">This section describes behavior changes to [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>  
  
### <a name="view-items-permission-will-not-download-shared-datasets-sharepoint-mode"></a><span data-ttu-id="01765-113">“查看项”权限将不会下载共享数据集（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="01765-113">View Items permission will not download Shared Datasets (SharePoint Mode)</span></span>  
 <span data-ttu-id="01765-114">**新行为：** 具有 "查看项" SharePoint 权限的用户无法再下载 Reporting Services 共享数据集的内容。</span><span class="sxs-lookup"><span data-stu-id="01765-114">**New Behavior:** Users with the SharePoint permission of "View Items" can no longer download the contents of Reporting Services shared datasets.</span></span> <span data-ttu-id="01765-115">此行为更改现在与针对报表、数据源和模型的 "查看项" 权限一致。</span><span class="sxs-lookup"><span data-stu-id="01765-115">This behavior change is now consistent with the "View Items" permissions for reports, data sources, and models.</span></span> <span data-ttu-id="01765-116">具有 "查看项" 权限的用户可以查看和执行报表、数据源和模型，但无法下载其内容。</span><span class="sxs-lookup"><span data-stu-id="01765-116">Users with "View Items" permission can view and execute reports, data sources, and models but they cannot download their content.</span></span>  
  
 <span data-ttu-id="01765-117">**以前的行为：** 具有 "查看项" SharePoint 权限的用户可以下载 Reporting Services 共享数据集的内容。</span><span class="sxs-lookup"><span data-stu-id="01765-117">**Previous Behavior:** Users with the "View Items" SharePoint permission could download the contents of Reporting Services shared datasets.</span></span>  
  
 <span data-ttu-id="01765-118">有关 SharePoint 权限级别的详细信息，请参阅 [用户权限和权限级别](https://technet.microsoft.com/library/cc721640.aspx)。</span><span class="sxs-lookup"><span data-stu-id="01765-118">For more information on SharePoint permission levels, see [User permissions and permission levels](https://technet.microsoft.com/library/cc721640.aspx)</span></span>  
  
### <a name="report-server-trace-logs-are-in-a-new-location-for-sharepoint-mode-sharepoint-mode"></a><span data-ttu-id="01765-119">报表服务器跟踪日志位于 SharePoint 模式的新位置（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="01765-119">Report Server trace logs are in a new location for SharePoint mode (SharePoint Mode)</span></span>  
 <span data-ttu-id="01765-120">**新行为：** 对于在 SharePoint 模式下安装的 Report Server，Report Server 跟踪日志将位于%Programfiles%\Common Files\Microsoft Shared\Web Server Extensions\14\Web Services\reportserver\logfiles 下。</span><span class="sxs-lookup"><span data-stu-id="01765-120">**New behavior:** For a report server installed in SharePoint mode, the report server trace logs will be under %Programfiles%\Common Files\Microsoft Shared\Web Server Extensions\14\Web Services\ReportServer\LogFiles.</span></span>  
  
 <span data-ttu-id="01765-121">**以前的行为：** 报表服务器跟踪日志位于如下路径下：%Programfilesdir%\Microsoft SQL Server \\<RS_instance> \Reporting Services\LogFiles</span><span class="sxs-lookup"><span data-stu-id="01765-121">**Previous Behavior:** Report Server trace logs were found under a path similar to the following:  %Programfilesdir%\Microsoft SQL Server\\<RS_instance>\Reporting Services\LogFiles</span></span>  
  
### <a name="getserverconfiginfo-soap-api-is-no-longer-supported-sharepoint-mode"></a><span data-ttu-id="01765-122">GetServerConfigInfo SOAP API 不再受支持（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="01765-122">GetServerConfigInfo SOAP API is no longer supported (SharePoint Mode)</span></span>  
 <span data-ttu-id="01765-123">**新行为**：使用 PowerShell Cmdlet "get-sprsserviceapplicationservers"</span><span class="sxs-lookup"><span data-stu-id="01765-123">**New behavior**: Use PowerShell cmdlet "Get-SPRSServiceApplicationServers"</span></span>  
  
 <span data-ttu-id="01765-124">**以前的行为：** 客户可以开发 SOAP 客户端代码以便直接与 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 终结点进行通信，并 ( # A1 调用 GetReportServerConfigInfo。</span><span class="sxs-lookup"><span data-stu-id="01765-124">**Previous Behavior:** Customers could develop SOAP client code to communicate directly with the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] end point, and call GetReportServerConfigInfo().</span></span>  
  
### <a name="report-server-configuration-and-management-tools"></a><span data-ttu-id="01765-125">报表服务器配置和管理工具</span><span class="sxs-lookup"><span data-stu-id="01765-125">Report Server Configuration and Management Tools</span></span>  
  
#### <a name="configuration-manager-is-not-used-for-sharepoint-mode"></a><span data-ttu-id="01765-126">配置管理器不用于 SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="01765-126">Configuration Manager is not used for SharePoint Mode</span></span>  
 <span data-ttu-id="01765-127">**新行为：**[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Configuration Manager 不再支持 SharePoint 模式报表服务器。</span><span class="sxs-lookup"><span data-stu-id="01765-127">**New behavior:** The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager no longer supports SharePoint Mode report servers.</span></span> <span data-ttu-id="01765-128">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 模式的配置现在可以通过使用 SharePoint 管理中心来完成，因此 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 配置管理器不再支持 SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="01765-128">Configuration of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode can now be completed by using SharePoint Central administration and therefore [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager no longer supports SharePoint mode.</span></span> <span data-ttu-id="01765-129">配置管理器现在仅用于本机模式报表服务器。</span><span class="sxs-lookup"><span data-stu-id="01765-129">Configuration Manager is now only used for Native mode report servers.</span></span>  
  
#### <a name="you-cannot-change-the-server-from-one-mode-to-another"></a><span data-ttu-id="01765-130">无法将服务器从一种模式更改为另一种模式</span><span class="sxs-lookup"><span data-stu-id="01765-130">You cannot change the server from one mode to another</span></span>  
 <span data-ttu-id="01765-131">**新行为：** 无法更改服务器模式。</span><span class="sxs-lookup"><span data-stu-id="01765-131">**New behavior:** You cannot change server modes.</span></span> <span data-ttu-id="01765-132">如果您以本机模式安装了报表服务器，则无法将其更改或重新配置为 SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="01765-132">If you install a report server as Native mode you cannot change or re-configure it to be SharePoint mode.</span></span> <span data-ttu-id="01765-133">如果在 SharePoint 模式中进行安装，则可以将报表服务器更改为本机模式。</span><span class="sxs-lookup"><span data-stu-id="01765-133">If you install in SharePoint mode, you can change the report server to native mode.</span></span>  
  
 <span data-ttu-id="01765-134">**先前行为：** 客户在 SharePoint 模式中安装 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表服务器。</span><span class="sxs-lookup"><span data-stu-id="01765-134">**Previous Behavior:** Customer installs a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server in SharePoint mode.</span></span> <span data-ttu-id="01765-135">如果客户想要将报表服务器切换为本机模式，可以打开 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 配置管理器，通过创建新的本机模式数据库或连接到现有的本机模式数据库，来切换为本机模式。</span><span class="sxs-lookup"><span data-stu-id="01765-135">If the customer wants to switch the report server to Native mode, they could open the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] configuration manager to switch to Native mode by either creating a new or connecting to an existing Native mode database.</span></span> <span data-ttu-id="01765-136">客户还可以使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 配置管理器从 SharePoint 模式切换为本机模式。</span><span class="sxs-lookup"><span data-stu-id="01765-136">The customer could also use [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager to switch from SharePoint mode to Native mode.</span></span>  
  
##  <a name="sql-server-2008-r2-reporting-services-behavior-changes"></a><a name="bkmk_kj"></a><span data-ttu-id="01765-137">SQL Server 2008 R2 Reporting Services 行为更改</span><span class="sxs-lookup"><span data-stu-id="01765-137">SQL Server 2008 R2 Reporting Services Behavior Changes</span></span>  
 <span data-ttu-id="01765-138">本节介绍中的行为更改 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="01765-138">This section describes behavior changes in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="01765-139">因为 SQL Server 2008 R2 是 SQL Server 2008 的次版本升级，所以，我们建议您也查看 SQL Server 2008 部分的内容。</span><span class="sxs-lookup"><span data-stu-id="01765-139">Because SQL Server 2008 R2 is a minor version upgrade of SQL Server 2008, we recommend that you also review the content in the SQL Server 2008 section.</span></span>  
  
### <a name="secureconnectionlevel-property-in-the-reporting-services-wmi-provider-library"></a><span data-ttu-id="01765-140">Reporting Services WMI 提供程序库中的 SecureConnectionLevel 属性</span><span class="sxs-lookup"><span data-stu-id="01765-140">SecureConnectionLevel Property in the Reporting Services WMI Provider Library</span></span>  
 <span data-ttu-id="01765-141">在的 WMI 提供程序库中 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ， **SecureConnectionLevel**属性允许、、、的值， `0` `1` `2` `3` `0` 它指示安全套接字层 (ssl) 对于任何 web 服务方法均不需要 ssl， `3` 指示所有 web 服务方法均需要 ssl，并 `1` `2` 指示需要 ssl 的 web 服务方法的子集。</span><span class="sxs-lookup"><span data-stu-id="01765-141">In the WMI provider library for [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], the **SecureConnectionLevel** property allows values of `0`,`1`,`2`,`3`, with `0` indicating that Secure Socket Layer (SSL) is not required for any of the Web service methods, `3` indicating that SSL is required for all the Web service methods, and `1` and `2` indicate subsets of Web service methods that require SSL.</span></span> <span data-ttu-id="01765-142">在中 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ，这些值将只有两个可能的含义：</span><span class="sxs-lookup"><span data-stu-id="01765-142">In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], these values will have only two possible meanings:</span></span>  
  
-   <span data-ttu-id="01765-143">`0` 指示对于任何 Web 服务方法均不需要 SSL。</span><span class="sxs-lookup"><span data-stu-id="01765-143">`0` indicates SSL is not required for any of the Web service methods.</span></span>  
  
-   <span data-ttu-id="01765-144">正整数指示对于所有 Web 服务方法均需要 SSL。</span><span class="sxs-lookup"><span data-stu-id="01765-144">A positive integer indicates SSL is required for all the Web service methods.</span></span>  
  
 <span data-ttu-id="01765-145">此更改将影响报表服务器响应 Web 服务调用的方式。</span><span class="sxs-lookup"><span data-stu-id="01765-145">This change affects how the report server responds to Web service calls.</span></span> <span data-ttu-id="01765-146">例如， <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> 如果**SecureConnectionLevel**设置为0，并且中的所有方法均 <xref:ReportService2005.ReportingService2005> 设置为**SecureConnectionLevel** `1` 、或，则返回 nothing `2` `3` 。</span><span class="sxs-lookup"><span data-stu-id="01765-146">For example, <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> now returns nothing if **SecureConnectionLevel** is set to 0 and all the methods in <xref:ReportService2005.ReportingService2005> if **SecureConnectionLevel** is set to `1`, `2`, or `3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01765-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="01765-147">See Also</span></span>  
 <span data-ttu-id="01765-148">[新增功能 &#40;Reporting Services&#41;](what-s-new-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="01765-148">[What's New &#40;Reporting Services&#41;](what-s-new-reporting-services.md) </span></span>  
 <span data-ttu-id="01765-149">[SQL Server 2014 的 SQL Server Reporting Services 中的不推荐使用的功能](deprecated-features-in-sql-server-reporting-services-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="01765-149">[Deprecated Features in SQL Server Reporting Services in SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md) </span></span>  
 <span data-ttu-id="01765-150">[SQL Server 2014 中的 SQL Server Reporting Services 已停止使用的功能](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="01765-150">[Discontinued Functionality to SQL Server Reporting Services in SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md) </span></span>  
 [<span data-ttu-id="01765-151">SQL Server 2014 的 SQL Server Reporting Services 中的重大更改</span><span class="sxs-lookup"><span data-stu-id="01765-151">Breaking Changes in SQL Server Reporting Services in SQL Server 2014</span></span>](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)  
  
  
