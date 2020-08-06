---
title: 将 Report 类用于传递扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], report information
- Report class
ms.assetid: 1145ac63-eafd-452a-82af-16f85b1676dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3f750c2383253636db255cbe9f1ce0ee676a9d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591770"
---
# <a name="using-the-report-class-for-a-delivery-extension"></a><span data-ttu-id="606ba-102">将 Report 类用于传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="606ba-102">Using the Report Class for a Delivery Extension</span></span>
  <span data-ttu-id="606ba-103"><xref:Microsoft.ReportingServices.Interfaces.Report> 类表示报表服务器数据库中的报表。</span><span class="sxs-lookup"><span data-stu-id="606ba-103">The <xref:Microsoft.ReportingServices.Interfaces.Report> class represents a report in the report server database.</span></span> <span data-ttu-id="606ba-104">任何订阅都与某一特定报表相关联。</span><span class="sxs-lookup"><span data-stu-id="606ba-104">Any subscription is associated with a specific report.</span></span> <span data-ttu-id="606ba-105">该报表包含在通知中。</span><span class="sxs-lookup"><span data-stu-id="606ba-105">The report is contained in the notification.</span></span> <span data-ttu-id="606ba-106">您的传递扩展插件可以使用作为该通知的一部分的 <xref:Microsoft.ReportingServices.Interfaces.Report> 对象来呈现报表。</span><span class="sxs-lookup"><span data-stu-id="606ba-106">Your delivery extension can use the <xref:Microsoft.ReportingServices.Interfaces.Report> object that is part of the notification to render the report.</span></span> <span data-ttu-id="606ba-107"><xref:Microsoft.ReportingServices.Interfaces.Report> 对象还包含特定于报表的属性，例如指向报表服务器上的报表的 URL 和报表名称。</span><span class="sxs-lookup"><span data-stu-id="606ba-107">The <xref:Microsoft.ReportingServices.Interfaces.Report> object also contains report-specific properties, such as the URL to the report on the report server and the name of the report.</span></span> <span data-ttu-id="606ba-108">这些属性全都可以用作您的传递提供程序的一部分。</span><span class="sxs-lookup"><span data-stu-id="606ba-108">These properties can all be used as part of your delivery provider.</span></span>  
  
 <span data-ttu-id="606ba-109"><xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> 类的 <xref:Microsoft.ReportingServices.Interfaces.Report> 方法可用于呈现一个报表。</span><span class="sxs-lookup"><span data-stu-id="606ba-109">The <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> method of the <xref:Microsoft.ReportingServices.Interfaces.Report> class can be used to render a report.</span></span> <span data-ttu-id="606ba-110"><xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> 方法返回包含一个或多个 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 对象的数组，这些对象一起构成单个所呈现报表。</span><span class="sxs-lookup"><span data-stu-id="606ba-110">The <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> method returns an array of one or more <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects that together comprise a single rendered report.</span></span> <span data-ttu-id="606ba-111">第一个 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 对象为呈现的报表。</span><span class="sxs-lookup"><span data-stu-id="606ba-111">The first <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object is the rendered report.</span></span> <span data-ttu-id="606ba-112">任何其他 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 对象为必须随报表数据一起传递的资源（例如，HTML 文件和关联的图像）。</span><span class="sxs-lookup"><span data-stu-id="606ba-112">Any other <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects are resources that must be delivered along with the report data (for example, an HTML file and associated images).</span></span> <span data-ttu-id="606ba-113">属于单一流呈现扩展插件（IMAGE、PDF、MHTML 和 Excel）的呈现扩展插件只返回此数组中的一个 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 对象。</span><span class="sxs-lookup"><span data-stu-id="606ba-113">Rendering extensions that are single-stream rendering extensions (IMAGE, PDF, MHTML, and Excel) return only one <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object in the array.</span></span>  
  
 <span data-ttu-id="606ba-114">包含报表流的 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 对象可作为传递的一部分。</span><span class="sxs-lookup"><span data-stu-id="606ba-114">The <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object, which contains the report stream, can be included as part of a delivery.</span></span>  
  
 <span data-ttu-id="606ba-115">有关如何使用 <xref:Microsoft.ReportingServices.Interfaces.Report> 类的示例，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）</span><span class="sxs-lookup"><span data-stu-id="606ba-115">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.Report> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="606ba-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="606ba-116">See Also</span></span>  
 <span data-ttu-id="606ba-117">[实现传递扩展插件](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="606ba-117">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 <span data-ttu-id="606ba-118">[Reporting Services 扩展插件库](../reporting-services-extension-library.md) </span><span class="sxs-lookup"><span data-stu-id="606ba-118">[Reporting Services Extension Library](../reporting-services-extension-library.md) </span></span>  
 [<span data-ttu-id="606ba-119">将 RenderedOutputFile 类用于传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="606ba-119">Using the RenderedOutputFile Class for a Delivery Extension</span></span>](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
  
  
