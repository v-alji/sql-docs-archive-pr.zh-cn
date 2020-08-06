---
title: 在 Windows 应用程序中使用 SOAP API | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendered reports [Reporting Services]
- Windows applications [Reporting Services]
- Windows Forms [Reporting Services]
- SOAP [Reporting Services], Windows applications
ms.assetid: e4804792-20cd-4df2-9257-fb958ff447b4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 115ce02da69a8adb2c7a3de4175e528f281eb2b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576550"
---
# <a name="using-the-soap-api-in-a-windows-application"></a><span data-ttu-id="c1c26-102">在 Windows 应用程序中使用 SOAP API</span><span class="sxs-lookup"><span data-stu-id="c1c26-102">Using the SOAP API in a Windows Application</span></span>
  <span data-ttu-id="c1c26-103">可以通过 Reporting Services SOAP API 访问报表服务器的完整功能。</span><span class="sxs-lookup"><span data-stu-id="c1c26-103">You can access the full functionality of the report server through the Reporting Services SOAP API.</span></span> <span data-ttu-id="c1c26-104">SOAP API 是一个 Web 服务，同样可以轻松地访问此服务以向自定义业务应用程序提供企业报表功能。</span><span class="sxs-lookup"><span data-stu-id="c1c26-104">The SOAP API is a Web service and, as such, can be easily accessed to provide enterprise reporting features to your custom business applications.</span></span> <span data-ttu-id="c1c26-105">只需通过编写对此 Web 服务进行调用的代码，即可在 Windows 应用程序中访问此服务。</span><span class="sxs-lookup"><span data-stu-id="c1c26-105">You can access the Web service in a Windows application simply by writing code that makes calls to the service.</span></span> <span data-ttu-id="c1c26-106">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ，你可以生成一个代理类，该类公开 Web 服务的属性和方法，并使你能够使用熟悉的基础结构和工具来构建基于技术构建的业务应用程序 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c1c26-106">Using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can generate a proxy class that exposes the properties and methods of the Web service and enables you to use a familiar infrastructure and tools to build business applications built on [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] technology.</span></span>  
  
## <a name="integrating-report-management-functionality-using-windows-forms"></a><span data-ttu-id="c1c26-107">使用 Windows 窗体集成报表管理功能</span><span class="sxs-lookup"><span data-stu-id="c1c26-107">Integrating Report Management Functionality Using Windows Forms</span></span>  
 <span data-ttu-id="c1c26-108">与 URL 访问不同，SOAP API 公开可用于整个报表服务器的一组完整的管理功能。</span><span class="sxs-lookup"><span data-stu-id="c1c26-108">Unlike URL access, the SOAP API exposes the complete set of management functions that are available through the report server.</span></span> <span data-ttu-id="c1c26-109">这意味着，借助于 SOAP，开发人员可以使用报表管理器的完整管理功能。</span><span class="sxs-lookup"><span data-stu-id="c1c26-109">This means that the entire administrative functionality of Report Manager is available to developers through SOAP.</span></span> <span data-ttu-id="c1c26-110">同样，您可以使用 Windows 窗体开发完整的控制和管理工具。</span><span class="sxs-lookup"><span data-stu-id="c1c26-110">As such, you can develop a complete management and administration tool using Windows Forms.</span></span> <span data-ttu-id="c1c26-111">例如，在 Windows 应用程序中，您可能希望使得用户能够检索报表服务器命名空间的内容。</span><span class="sxs-lookup"><span data-stu-id="c1c26-111">For example, in your Windows application, you might want to enable your users to retrieve the contents of the report server namespace.</span></span> <span data-ttu-id="c1c26-112">为此，您可以使用 Web 服务 <xref:ReportService2010.ReportingService2010.ListChildren%2A> 方法列出报表服务器数据库中的所有项，然后使用 Listview、Treeview 或 Combobox 控件向用户显示这些项。</span><span class="sxs-lookup"><span data-stu-id="c1c26-112">To do this, you could use the Web service <xref:ReportService2010.ReportingService2010.ListChildren%2A> method to list all the items in the report server database and then use a Listview, Treeview, or Combobox control to display those items to your users.</span></span> <span data-ttu-id="c1c26-113">以下 Web 服务代码可用于在用户单击窗体上的某个按钮时，检索用户的“我的报表”文件夹中可用报表的当前列表：</span><span class="sxs-lookup"><span data-stu-id="c1c26-113">The following Web service code might be used to retrieve the current list of available reports in a user's My Reports folder when a user clicks a button on a form:</span></span>  
  
```vb  
' Button click event that retrieves a list of reports from  
' the My Reports folder and displays them in a combo box  
Private Sub listReportsButton_Click(sender As Object, e As System.EventArgs)  
   ' Create a new Web service object and set credentials  
   ' to Windows Authentication  
   Dim rs As New ReportingService2010()  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
   ' Return the list of items in My Reports  
   Dim items As CatalogItem() = rs.ListChildren("/Adventureworks 2008 Sample Reports", False)  
  
   Dim ci As CatalogItem  
   For Each ci In  items  
      ' If the item is a report, add it to   
      ' a combo box  
      If ci.TypeName = "Report" Then  
         catalogComboBox.Items.Add(ci.Name)  
      End If  
   Next ci  
End Sub 'listReportsButton_Click  
```  
  
```csharp  
// Button click event that retrieves a list of reports from  
// the My Reports folder and displays them in a combo box  
private void listReportsButton_Click(object sender, System.EventArgs e)  
{  
   // Create a new Web service object and set credentials  
   // to Windows Authentication  
   ReportingService2010 rs = new ReportingService2010();  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
  
   // Return the list of items in My Reports  
   CatalogItem[] items = rs.ListChildren("/Adventureworks 2008 Sample Reports", false);  
  
   foreach (CatalogItem ci in items)  
   {  
      // If the item is a report, add it to   
      // a combo box  
      if (ci.TypeName == "Report")  
         catalogComboBox.Items.Add(ci.Name);  
   }  
}  
```  
  
 <span data-ttu-id="c1c26-114">从此处，您可以让用户通过 Web 浏览器控件或图像控件，从组合框中选择报表并在窗体上预览此报表。</span><span class="sxs-lookup"><span data-stu-id="c1c26-114">From there, you might enable users to select the report from the Combo box and preview the report on the form either using a Web browser control or an image control.</span></span>  
  
## <a name="enabling-report-viewing-and-navigation-using-windows-forms"></a><span data-ttu-id="c1c26-115">使用 Windows 窗体启用报表查看和导航</span><span class="sxs-lookup"><span data-stu-id="c1c26-115">Enabling Report Viewing and Navigation Using Windows Forms</span></span>  
 <span data-ttu-id="c1c26-116">可以通过两种方法将报表集成到 Windows 窗体应用程序中。</span><span class="sxs-lookup"><span data-stu-id="c1c26-116">There are two methods available for integrating reports into your Windows Forms applications.</span></span>  
  
 <span data-ttu-id="c1c26-117">可以使用 SOAP API 通过 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法将报表呈现为所支持的任何呈现格式。</span><span class="sxs-lookup"><span data-stu-id="c1c26-117">You can use the SOAP API to render reports to any of the supported rendering formats using the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method.</span></span> <span data-ttu-id="c1c26-118">通过 SOAP 启用报表查看和导航也有一些缺点，但这些缺点微不足道：</span><span class="sxs-lookup"><span data-stu-id="c1c26-118">There are slight disadvantages to enabling report viewing and navigation through SOAP:</span></span>  
  
-   <span data-ttu-id="c1c26-119">您无法利用报表工具栏（通过 URL 访问随 HTML 查看器提供）的内置功能。</span><span class="sxs-lookup"><span data-stu-id="c1c26-119">You cannot take advantage of the built-in functionality of the report toolbar that is included with the HTML Viewer through URL access.</span></span>  
  
-   <span data-ttu-id="c1c26-120">如果您呈现到 HTML，则必须使用 <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> 方法将任何图像或资源单独呈现为其他流。</span><span class="sxs-lookup"><span data-stu-id="c1c26-120">If you render to HTML, you must separately render any images or resources as additional streams using the <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> method.</span></span>  
  
-   <span data-ttu-id="c1c26-121">使用 URL 访问呈现报表比使用 SOAP API 在性能方面具有轻微的优势。</span><span class="sxs-lookup"><span data-stu-id="c1c26-121">There is a slight performance advantage to rendering reports using URL access over using the SOAP API.</span></span>  
  
 <span data-ttu-id="c1c26-122">然而，可以使用 SOAP API 的 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法以编程方式呈现报表并将它们保存为不同的输出格式。</span><span class="sxs-lookup"><span data-stu-id="c1c26-122">However, the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method of the SOAP API can be used to render reports and save them to various output formats programmatically.</span></span> <span data-ttu-id="c1c26-123">这是强于 URL 访问的一个优势，它要求用户交互。</span><span class="sxs-lookup"><span data-stu-id="c1c26-123">This is an advantage over URL access, which requires user interaction.</span></span> <span data-ttu-id="c1c26-124">当您使用 SOAP API <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法呈现报表时，您可以呈现为所支持的任何输出格式。</span><span class="sxs-lookup"><span data-stu-id="c1c26-124">When you render a report using the SOAP API <xref:ReportExecution2005.ReportExecutionService.Render%2A> method, you can render to any of the supported output formats.</span></span>  
  
 <span data-ttu-id="c1c26-125">你还可以使用附带的自由分发的 ReportViewer 控件 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c1c26-125">You can also use the freely distributable ReportViewer controls that are included with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)].</span></span> <span data-ttu-id="c1c26-126">通过 ReportViewer 控件，可以轻松地将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能嵌入到自定义应用程序中。</span><span class="sxs-lookup"><span data-stu-id="c1c26-126">The ReportViewer controls make it easy to embed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] functionality into custom applications.</span></span> <span data-ttu-id="c1c26-127">ReportViewer 控件供开发人员使用，以提供预先设计并编写完全的报表，作为应用程序功能集的一部分（例如，网站管理应用程序可能包含显示对公司网站的点击流分析的报表）。</span><span class="sxs-lookup"><span data-stu-id="c1c26-127">The ReportViewer controls are intended for developers who want to provide predesigned, fully authored reports as part of an application feature set (for example, a Web site management application might include reports that show click-stream analysis on company Web sites).</span></span> <span data-ttu-id="c1c26-128">在应用程序中嵌入控件为在应用程序部署中包含 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务器组件提供了简化的替代方法。</span><span class="sxs-lookup"><span data-stu-id="c1c26-128">Embedding the controls in an application provides a streamlined alternative to including the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] server components in your application deployment.</span></span> <span data-ttu-id="c1c26-129">这些控件提供报表功能，但不提供可在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中找到的其他对报表创作、发布或分发和传递的支持。</span><span class="sxs-lookup"><span data-stu-id="c1c26-129">The controls provide report functionality, but without the additional report authoring, publication, or distribution and delivery support that you find in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c1c26-130">ReportViewer 控件有两个版本，一个用于各种 Windows 客户端应用程序，另一个用于 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 应用程序。</span><span class="sxs-lookup"><span data-stu-id="c1c26-130">There are two versions of the ReportViewer controls, one for rich Windows client applications and one for [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications.</span></span> <span data-ttu-id="c1c26-131">这两个控件都支持本地处理模式和远程处理模式。</span><span class="sxs-lookup"><span data-stu-id="c1c26-131">The controls support both local processing and remote processing modes.</span></span> <span data-ttu-id="c1c26-132">在本地处理模式中，应用程序提供报表定义以及数据集报表处理和触发器报表处理。</span><span class="sxs-lookup"><span data-stu-id="c1c26-132">In local processing mode, your application provides the report definition and datasets and triggers report processing.</span></span> <span data-ttu-id="c1c26-133">在远程处理模式中，数据检索和报表处理在报表服务器上进行，而 ReportViewer 控件用于显示和报表导航。</span><span class="sxs-lookup"><span data-stu-id="c1c26-133">In remote processing mode, data retrieval and report processing happen on the report server and the control is used for display and report navigation.</span></span> <span data-ttu-id="c1c26-134">使用此模式可以生成丰富的应用程序，小至桌面应用程序，大到企业级应用程序。</span><span class="sxs-lookup"><span data-stu-id="c1c26-134">This model allows you to build rich applications that can be scaled from desktop to the enterprise.</span></span>  
  
 <span data-ttu-id="c1c26-135">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 联机帮助中有关于 ReportViewer 控件的记载。</span><span class="sxs-lookup"><span data-stu-id="c1c26-135">ReportViewer controls are documented in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] online Help.</span></span> <span data-ttu-id="c1c26-136">有关详细信息，请参阅 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 产品文档。</span><span class="sxs-lookup"><span data-stu-id="c1c26-136">For more information, see the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] product documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c26-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c1c26-137">See Also</span></span>  
 <span data-ttu-id="c1c26-138">[使用 Web 服务和 .NET Framework 生成应用程序](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="c1c26-138">[Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="c1c26-139">[将 Reporting Services 集成到应用程序中](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="c1c26-139">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 [<span data-ttu-id="c1c26-140">在 Web 应用程序中使用 SOAP API</span><span class="sxs-lookup"><span data-stu-id="c1c26-140">Using the SOAP API in a Web Application</span></span>](integrating-reporting-services-using-soap-web-application.md)  
  
  
