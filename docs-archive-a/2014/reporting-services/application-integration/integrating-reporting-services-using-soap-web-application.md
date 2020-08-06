---
title: 在 Web 应用程序中使用 SOAP API | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], Web applications
- impersonation [Reporting Services]
- user impersonation [Reporting Services]
- report servers [Reporting Services], SOAP
- Web applications [Reporting Services]
ms.assetid: e8ca4455-0dc3-4741-8872-3636114938ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e228f01915df633f50b23bf93e892446863c28ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687551"
---
# <a name="using-the-soap-api-in-a-web-application"></a><span data-ttu-id="474b7-102">在 Web 应用程序中使用 SOAP API</span><span class="sxs-lookup"><span data-stu-id="474b7-102">Using the SOAP API in a Web Application</span></span>
  <span data-ttu-id="474b7-103">可以通过 Reporting Services SOAP API 访问报表服务器的完整功能。</span><span class="sxs-lookup"><span data-stu-id="474b7-103">You can access the full functionality of the report server through the Reporting Services SOAP API.</span></span> <span data-ttu-id="474b7-104">因为它是一个 Web 服务，所以您可以轻松地访问 SOAP API 以向自定义业务应用程序提供企业报表功能。</span><span class="sxs-lookup"><span data-stu-id="474b7-104">Because it's a Web service, the SOAP API can be easily accessed to provide enterprise reporting features to your custom business applications.</span></span> <span data-ttu-id="474b7-105">从 Web 应用程序访问报表服务器 Web 服务的方法与从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 应用程序访问 SOAP API 的方法非常类似。</span><span class="sxs-lookup"><span data-stu-id="474b7-105">You access the Report Server Web service from a Web application in much the same way that you access the SOAP API from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application.</span></span> <span data-ttu-id="474b7-106">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ，你可以生成一个代理类，该类公开报表服务器 Web 服务的属性和方法，并使你能够使用熟悉的基础结构和工具来生成技术的业务应用程序 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="474b7-106">Using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can generate a proxy class that exposes the properties and methods of the Report Server Web service and enables you to use a familiar infrastructure and tools to build business applications on [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] technology.</span></span>  
  
 <span data-ttu-id="474b7-107">从 Web 应用程序访问 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表管理功能与从 Windows 应用程序进行访问一样简单。</span><span class="sxs-lookup"><span data-stu-id="474b7-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report management functionality is just as easily accessed from a Web application as from a Windows application.</span></span> <span data-ttu-id="474b7-108">在 Web 应用程序中，您可以从报表服务器数据库添加和删除项，设置项安全性，修改报表服务器数据库项，管理计划和传递以及等等。</span><span class="sxs-lookup"><span data-stu-id="474b7-108">From a Web application, you can add and remove items from the report server database, set item security, modify report server database items, manage scheduling and delivery, and more.</span></span>  
  
## <a name="enabling-impersonation"></a><span data-ttu-id="474b7-109">启用模拟</span><span class="sxs-lookup"><span data-stu-id="474b7-109">Enabling Impersonation</span></span>  
 <span data-ttu-id="474b7-110">配置 Web 应用程序的第一步是从 Web 服务客户端启用模拟。</span><span class="sxs-lookup"><span data-stu-id="474b7-110">The first step in configuring your Web application is to enable impersonation from the Web service client.</span></span> <span data-ttu-id="474b7-111">在模拟模式中，[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 应用程序可以使用它们实际运行时所用的客户端身份来运行。</span><span class="sxs-lookup"><span data-stu-id="474b7-111">With impersonation, [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications can execute with the identity of the client on whose behalf they are operating.</span></span> [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] <span data-ttu-id="474b7-112">依赖于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) 来对用户身份进行验证，并将已验证的标记传递到 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 应用程序，或者，在无法对用户身份进行验证的情况下，传递未通过身份验证的标记。</span><span class="sxs-lookup"><span data-stu-id="474b7-112">relies on [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) to authenticate the user and either pass an authenticated token to the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] application or, if unable to authenticate the user, pass an unauthenticated token.</span></span> <span data-ttu-id="474b7-113">在任一种情况下，如果启用了模拟，则无论收到哪种标记，[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 应用程序都会进行模拟。</span><span class="sxs-lookup"><span data-stu-id="474b7-113">In either case, the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] application impersonates whichever token is received if impersonation is enabled.</span></span> <span data-ttu-id="474b7-114">您可以对于客户端启用模拟，为此，请按以下所示修改客户端应用程序的 Web.config 文件：</span><span class="sxs-lookup"><span data-stu-id="474b7-114">You can enable impersonation on the client, by modifying the Web.config file of the client application as follows:</span></span>  
  
```  
<!-- Web.config file. -->  
<identity impersonate="true"/>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="474b7-115">默认情况下，模拟处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="474b7-115">Impersonation is disabled by default.</span></span>  
  
 <span data-ttu-id="474b7-116">有关模拟的详细信息 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] ，请参阅 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文档。</span><span class="sxs-lookup"><span data-stu-id="474b7-116">For more information about [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] impersonation, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="managing-the-report-server-using-soap-api"></a><span data-ttu-id="474b7-117">使用 SOAP API 管理报表服务器</span><span class="sxs-lookup"><span data-stu-id="474b7-117">Managing the Report Server using SOAP API</span></span>  
 <span data-ttu-id="474b7-118">还可以使用 Web 应用程序管理报表服务器及其内容。</span><span class="sxs-lookup"><span data-stu-id="474b7-118">You can also use your Web application to manage a report server and its contents.</span></span> <span data-ttu-id="474b7-119">随 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 提供的报表管理器是完全使用 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 和 Reporting Services SOAP API 生成的 Web 应用程序的一个示例。</span><span class="sxs-lookup"><span data-stu-id="474b7-119">Report Manager, included with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], is an example of a Web application that is completely built using [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] and the Reporting Services SOAP API.</span></span> <span data-ttu-id="474b7-120">您可以将报表管理器的报表管理功能添加到自定义 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="474b7-120">You can add the report management functionality of Report Manager to your custom Web applications.</span></span> <span data-ttu-id="474b7-121">例如，您可能希望返回 Report Server 数据库中的可用报表列表，并将它们显示在 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] `Listbox` 控件中供用户选择。</span><span class="sxs-lookup"><span data-stu-id="474b7-121">For example, you might want to return a list of available reports in the report server database and display them in a [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] `Listbox` control for your users to choose from.</span></span> <span data-ttu-id="474b7-122">下面的代码连接到报表服务器数据库并返回报表服务器数据库中的项列表。</span><span class="sxs-lookup"><span data-stu-id="474b7-122">The following code connects to the report server database and returns a list of items in the report server database.</span></span> <span data-ttu-id="474b7-123">然后，将可用报表添加到 Listbox 控件，而该控件显示每个报表的路径。</span><span class="sxs-lookup"><span data-stu-id="474b7-123">The available reports are then added to a Listbox control, which displays the path of each report.</span></span>  
  
```vb  
Private Sub Page_Load(sender As Object, e As System.EventArgs)  
   ' Create a Web service proxy object and set credentials  
   Dim rs As New ReportingService2005()  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
   ' Return a list of catalog items in the report server database  
   Dim items As CatalogItem() = rs.ListChildren("/", True)  
  
   ' For each report, display the path of the report in a Listbox  
   Dim ci As CatalogItem  
   For Each ci In  items  
      If ci.Type = ItemTypeEnum.Report Then  
         catalogListBox.Items.Add(ci.Path)  
      End If  
   Next ci  
End Sub ' Page_Load   
```  
  
```csharp  
private void Page_Load(object sender, System.EventArgs e)  
{  
   // Create a Web service proxy object and set credentials  
   ReportingService2005 rs = new ReportingService2005();  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
  
   // Return a list of catalog items in the report server database  
   CatalogItem[] items = rs.ListChildren("/", true);  
  
   // For each report, display the path of the report in a Listbox  
   foreach(CatalogItem ci in items)  
   {  
      if (ci.Type == ItemTypeEnum.Report)  
         catalogListBox.Items.Add(ci.Path);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="474b7-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="474b7-124">See Also</span></span>  
 <span data-ttu-id="474b7-125">[使用 Web 服务和 .NET Framework 生成应用程序](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="474b7-125">[Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="474b7-126">[将 Reporting Services 集成到应用程序中](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="474b7-126">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="474b7-127">[报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="474b7-127">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="474b7-128">在 Windows 应用程序中使用 SOAP API</span><span class="sxs-lookup"><span data-stu-id="474b7-128">Using the SOAP API in a Windows Application</span></span>](integrating-reporting-services-using-soap-windows-application.md)  
  
  
