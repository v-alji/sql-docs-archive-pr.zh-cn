---
title: 将 RenderedOutputFile 类用于传递扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- RenderedOutputFile class
- data streams [Reporting Services]
- delivery extensions [Reporting Services], data streams
ms.assetid: 8b591801-42d5-49fa-b710-bf7e6917accf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1dcbf250a367326e5cad528384e533a9ac9d945b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591773"
---
# <a name="using-the-renderedoutputfile-class-for-a-delivery-extension"></a><span data-ttu-id="d0ee6-102">将 RenderedOutputFile 类用于传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="d0ee6-102">Using the RenderedOutputFile Class for a Delivery Extension</span></span>
  <span data-ttu-id="d0ee6-103"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 类表示某个数据流以及有关该数据流的关联属性的信息。</span><span class="sxs-lookup"><span data-stu-id="d0ee6-103">The <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> class represents a data stream and information about the data stream's associated properties.</span></span> <span data-ttu-id="d0ee6-104"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 类的 Data 属性用于将呈现的报表或报表资源表示为 Stream 对象。</span><span class="sxs-lookup"><span data-stu-id="d0ee6-104">The **Data** property of the <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> class is used to represent a rendered report or report resource as a **Stream** object.</span></span>  
  
 <span data-ttu-id="d0ee6-105">Report 对象的 <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> 方法返回包含一个或多个 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 对象的数组，这些对象一起构成单个呈现的报表。</span><span class="sxs-lookup"><span data-stu-id="d0ee6-105">The <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> method of the **Report** object returns an array of one or more <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects that together constitute a single rendered report.</span></span> <span data-ttu-id="d0ee6-106">第一个 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 对象为呈现的报表。</span><span class="sxs-lookup"><span data-stu-id="d0ee6-106">The first <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object is the rendered report.</span></span> <span data-ttu-id="d0ee6-107">任何其他 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 对象为必须随报表数据一起传递的资源（例如，HTML 文件和关联的图像）。</span><span class="sxs-lookup"><span data-stu-id="d0ee6-107">Any other <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects are resources that must be delivered along with the report data (for example, an HTML file and associated images).</span></span> <span data-ttu-id="d0ee6-108">属于单一流呈现扩展插件（IMAGE、PDF、MHTML 和 EXCEL）的呈现扩展插件只返回此数组中的一个 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 对象。</span><span class="sxs-lookup"><span data-stu-id="d0ee6-108">Rendering extensions that are single-stream rendering extensions (IMAGE, PDF, MHTML, and EXCEL) return only one <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object in the array.</span></span>  
  
 <span data-ttu-id="d0ee6-109">有关如何使用 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 类的示例，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="d0ee6-109">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ee6-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0ee6-110">See Also</span></span>  
 <span data-ttu-id="d0ee6-111">[实现传递扩展插件](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="d0ee6-111">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="d0ee6-112">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="d0ee6-112">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
