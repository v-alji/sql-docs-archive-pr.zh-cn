---
title: SharePoint 集成中的报表查看器 Web 部件可编程性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
ms.assetid: 714017b7-1bd6-4950-a3c6-d0df8450a877
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 494ebc3e6668e4d95480019e522caf46b83a6c4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691070"
---
# <a name="report-viewer-web-part-programmability-in-sharepoint-integration"></a><span data-ttu-id="064d2-102">SharePoint 集成中的报表查看器 Web 部件可编程性</span><span class="sxs-lookup"><span data-stu-id="064d2-102">Report Viewer Web Part Programmability in SharePoint Integration</span></span>
  <span data-ttu-id="064d2-103">报表查看器 Web 部件是一个 `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart` 服务器控件，其中包含一组公共应用程序编程接口 (API)，使开发人员能够创建自定义 SharePoint 应用程序。</span><span class="sxs-lookup"><span data-stu-id="064d2-103">The Report Viewer Web Part is a `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart` server control, which contains a set of public application programming interfaces (API) that enables developers to create custom SharePoint applications.</span></span> <span data-ttu-id="064d2-104">您可以创建自定义 Web 部件，以使用 Web 部件连接向报表查看器 Web 部件提供报表路径和参数。</span><span class="sxs-lookup"><span data-stu-id="064d2-104">You can create custom Web Parts that supply report path and parameters to Report Viewer Web Part using Web Part connections.</span></span> <span data-ttu-id="064d2-105">还可以在自定义 SharePoint Web 部件页中嵌入 Web 部件，并使用该公共 API 对其进行自定义。</span><span class="sxs-lookup"><span data-stu-id="064d2-105">You can also embed the Web Part in a custom SharePoint Web Part page and customize it using the public API.</span></span>  
  
## <a name="connecting-to-report-viewer-web-part-with-custom-web-parts"></a><span data-ttu-id="064d2-106">使用自定义 Web 部件连接到报表查看器 Web 部件</span><span class="sxs-lookup"><span data-stu-id="064d2-106">Connecting to Report Viewer Web Part with Custom Web Parts</span></span>  
 <span data-ttu-id="064d2-107">报表查看器 Web 部件是实现 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> 或 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` 的 SharePoint Web 部件的连接使用者。</span><span class="sxs-lookup"><span data-stu-id="064d2-107">The Report Viewer Web Part is a connection consumer to SharePoint Web Parts that implement <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> or `T:Microsoft.SharePoint.WebPartPages.IFilterValues`.</span></span> <span data-ttu-id="064d2-108">将某个 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web 部件（如“文档”Web 部件）放在与报表查看器 Web 部件所在的同一 Web 部件页上时，它可以向报表查看器 Web 部件提供报表路径  。</span><span class="sxs-lookup"><span data-stu-id="064d2-108">An <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part, such as the **Documents** Web Part can supply a report path to a Report Viewer Web Part when placed on the same Web Part page as the Report Viewer Web Part.</span></span> <span data-ttu-id="064d2-109">同样， `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web 部件（如 "**文本筛选**器" 或 "**选择筛选器**"）在与报表查看器 web 部件放置在同一个 web 部件页上时，可以向报表查看器 web 部件提供报表参数。</span><span class="sxs-lookup"><span data-stu-id="064d2-109">Likewise, an `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part, such as the **Text Filter** or the **Choice Filter**, can supply a report parameter to a Report Viewer Web Part when placed on the same Web Part page as the Report Viewer Web Part.</span></span>  
  
### <a name="implementing-a-report-path-provider-with-iwebpartrow"></a><span data-ttu-id="064d2-110">使用 IWebPartRow 实现报表路径访问接口</span><span class="sxs-lookup"><span data-stu-id="064d2-110">Implementing a Report Path Provider with IWebPartRow</span></span>  
 <span data-ttu-id="064d2-111">若要通过 Web 部件连接向报表查看器 Web 部件提供报表路径，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="064d2-111">To supply a report path to the Report Viewer Web Part through Web Part connections, do the following:</span></span>  
  
1.  <span data-ttu-id="064d2-112">创建一个实现 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> 接口的 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="064d2-112">Create a Web Part that implements the <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> interface.</span></span>  
  
2.  <span data-ttu-id="064d2-113">将 Web 部件添加到与报表查看器 Web 部件所在的相同 Web 部件页。</span><span class="sxs-lookup"><span data-stu-id="064d2-113">Add the Web Part to the same Web Part page as the Report Viewer Web Part.</span></span>  
  
3.  <span data-ttu-id="064d2-114">在基于 Web 的 Web 部件设计用户界面中将 Web 部件连接到报表查看器 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="064d2-114">Connect your Web Part to the Report Viewer Web Part in the Web-based Web Part design user interface.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="064d2-115">一次只能将一个 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web 部件连接到报表查看器 Web 部件，并且不能同时将一个 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web 部件和一个 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web 部件连接到报表查看器 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="064d2-115">You can only connect one <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part to the Report Viewer Web Part at a time, and you cannot connect both an <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part and an `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part to the Report Viewer Web Part at the same time.</span></span>  
  
 <span data-ttu-id="064d2-116">若要使您的 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web 部件可以正确地使用 `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`，必须在 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A> 方法中完成下列操作：</span><span class="sxs-lookup"><span data-stu-id="064d2-116">For your <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part to work properly with the `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`, you must do the following in the <xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A> method:</span></span>  
  
-   <span data-ttu-id="064d2-117">使用 <xref:System.Data.DataRowView> 对象作为输入参数调用回调方法。</span><span class="sxs-lookup"><span data-stu-id="064d2-117">Invoke the callback method with a <xref:System.Data.DataRowView> object as the input parameter.</span></span>  
  
-   <span data-ttu-id="064d2-118">确保 <xref:System.Data.DataRowView> 对象包含一个名为“DocUrl”的列，该列包含报表路径。</span><span class="sxs-lookup"><span data-stu-id="064d2-118">Make sure that the <xref:System.Data.DataRowView> object contains a column called "DocUrl" that contains the report path.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="064d2-119">[!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2010 的外接程序中的报表查看器 Web 部件还支持使用“FileRef”列来接收报表路径。</span><span class="sxs-lookup"><span data-stu-id="064d2-119">The Report Viewer Web Part in the add-in for [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2010 also supports receiving the report path using the "FileRef" column.</span></span>  
  
### <a name="implementing-a-report-parameter-provider-with-ifiltervalues"></a><span data-ttu-id="064d2-120">使用 IfilterValues 实现报表参数访问接口</span><span class="sxs-lookup"><span data-stu-id="064d2-120">Implementing a Report Parameter Provider with IFilterValues</span></span>  
 <span data-ttu-id="064d2-121">一个实现 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` 的 Web 部件可以向报表查看器 Web 部件提供一个参数值。</span><span class="sxs-lookup"><span data-stu-id="064d2-121">A Web Part that implements `T:Microsoft.SharePoint.WebPartPages.IFilterValues` can provide one parameter value to the Report Viewer Web Part.</span></span> <span data-ttu-id="064d2-122">发送到报表查看器 Web 部件的参数值可能会受到与在报表定义中指定的报表参数相同的限制，如数据类型、有效值等。</span><span class="sxs-lookup"><span data-stu-id="064d2-122">The parameter value sent to the Report Viewer Web Part is subject to the same restrictions placed on the report parameter as specified in the report definition, such as data type, valid values, and so on</span></span>  
  
 <span data-ttu-id="064d2-123">若要向报表查看器 Web 部件提供报表参数，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="064d2-123">To supply a report parameter to the Report Viewer Web Part, do the following:</span></span>  
  
1.  <span data-ttu-id="064d2-124">创建一个实现 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` 接口的 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="064d2-124">Create a Web Part that implements the `T:Microsoft.SharePoint.WebPartPages.IFilterValues` interface.</span></span>  
  
2.  <span data-ttu-id="064d2-125">将此 Web 部件添加到与 `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart` 所在的相同页。</span><span class="sxs-lookup"><span data-stu-id="064d2-125">Add the Web Part to the same page as the `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`.</span></span>  
  
3.  <span data-ttu-id="064d2-126">在基于 Web 的 Web 部件设计用户界面中，将您的 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web 部件连接到报表查看器 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="064d2-126">Connect your `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part to the Report Viewer Web Part in the Web-based Web Part design user interface.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="064d2-127">可以同时将多个 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web 部件连接到报表查看器 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="064d2-127">You can connect multiple `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Parts to the Report Viewer Web Part at a time.</span></span> <span data-ttu-id="064d2-128">但是，不能同时将 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web 部件和 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web 部件连接到报表查看器 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="064d2-128">However, you cannot connect both an <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part and an `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part to the Report Viewer Web Part at the same time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="064d2-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="064d2-129">See Also</span></span>  
 <span data-ttu-id="064d2-130">[IFilterValues 接口](https://msdn.microsoft.com/library/office/microsoft.sharepoint.webpartpages.ifiltervalues\(v=office.15\).aspx)</span><span class="sxs-lookup"><span data-stu-id="064d2-130">[IFilterValues interface](https://msdn.microsoft.com/library/office/microsoft.sharepoint.webpartpages.ifiltervalues\(v=office.15\).aspx)</span></span>  
  
  
