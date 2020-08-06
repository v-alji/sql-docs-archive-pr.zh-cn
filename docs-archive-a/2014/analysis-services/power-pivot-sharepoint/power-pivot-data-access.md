---
title: PowerPivot 数据访问 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 83dc82da-91fb-4e47-91a8-0e0db67339b8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8faeec7b2e12871467b93f136360e9a68a0e5acb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589895"
---
# <a name="powerpivot-data-access"></a><span data-ttu-id="0e54f-102">PowerPivot 数据访问</span><span class="sxs-lookup"><span data-stu-id="0e54f-102">PowerPivot Data Access</span></span>
  <span data-ttu-id="0e54f-103">本主题介绍从发布到 SharePoint 库的 PowerPivot 工作簿检索数据的方法。</span><span class="sxs-lookup"><span data-stu-id="0e54f-103">This topic describes the ways in which data is retrieved from a PowerPivot workbook that is published to a SharePoint library.</span></span>  
  
 <span data-ttu-id="0e54f-104">PowerPivot 数据存储于 Excel 工作簿中。</span><span class="sxs-lookup"><span data-stu-id="0e54f-104">PowerPivot data is stored inside an Excel workbook.</span></span> <span data-ttu-id="0e54f-105">连接字符串是指向 SharePoint 站点上的工作簿的 URL。</span><span class="sxs-lookup"><span data-stu-id="0e54f-105">The connection string is a URL to a workbook on a SharePoint site.</span></span>  
  
 <span data-ttu-id="0e54f-106">PowerPivot 数据最常由包含它的工作簿用作数据透视表和数据透视图背后蕴含的数据。</span><span class="sxs-lookup"><span data-stu-id="0e54f-106">PowerPivot data is most often used by the workbook that contains it, as the data behind PivotTables and PivotCharts.</span></span> <span data-ttu-id="0e54f-107">此外，PowerPivot 数据也可以用作外部数据源，其中，工作簿、面板或报表连接到 SharePoint 中的单独 Excel (.xlsx) 文件并且检索数据以供以后使用。</span><span class="sxs-lookup"><span data-stu-id="0e54f-107">Alternatively, PowerPivot data can also be used as an external data source, where a workbook, dashboard, or report connects to a separate Excel (.xlsx) file in SharePoint and retrieves the data for subsequent use.</span></span> <span data-ttu-id="0e54f-108">通常使用 PowerPivot 数据的客户端工具是 Excel、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、其他 Reporting Services 报表和 PerformancePoint。</span><span class="sxs-lookup"><span data-stu-id="0e54f-108">Client tools that typically use PowerPivot data are Excel, [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], other Reporting Services reports, and PerformancePoint.</span></span>  
  
 <span data-ttu-id="0e54f-109">在桌面上，PowerPivot 外接程序使用 AMO 和 ADOMD.NET 来创建、处理和查询客户端工作区中的 PowerPivot 数据。</span><span class="sxs-lookup"><span data-stu-id="0e54f-109">On the desktop, the PowerPivot add-in uses AMO and ADOMD.NET to create, process, and query the PowerPivot data in the client workspace.</span></span>  
  
 <span data-ttu-id="0e54f-110">在 SharePoint 场上，Excel Services 使用本地 MSOLAP OLE DB 访问接口来连接到 PowerPivot 数据。</span><span class="sxs-lookup"><span data-stu-id="0e54f-110">On a SharePoint farm, Excel Services uses the local MSOLAP OLE DB provider to connect to PowerPivot data.</span></span> <span data-ttu-id="0e54f-111">该访问接口向场中的 PowerPivot for SharePoint 服务器发出连接请求。</span><span class="sxs-lookup"><span data-stu-id="0e54f-111">The provider sends the connection request to a PowerPivot for SharePoint server in the farm.</span></span> <span data-ttu-id="0e54f-112">该服务器将加载数据，运行查询，并且返回结果集。</span><span class="sxs-lookup"><span data-stu-id="0e54f-112">That server loads the data, runs the query, and returns the result set.</span></span>  
  
##  <a name="querying-powerpivot-data-in-sharepoint"></a><a name="queryproc"></a><span data-ttu-id="0e54f-113">查询 SharePoint 中的 PowerPivot 数据</span><span class="sxs-lookup"><span data-stu-id="0e54f-113">Querying PowerPivot Data in SharePoint</span></span>  
 <span data-ttu-id="0e54f-114">在查看 SharePoint 库中的 PowerPivot 工作簿时，分别由场内的 Analysis Services 服务器实例来检测、提取和处理该工作簿内的 PowerPivot 数据，同时由 Excel Services 来呈现表示层。</span><span class="sxs-lookup"><span data-stu-id="0e54f-114">When you view a PowerPivot workbook from a SharePoint library, the PowerPivot data that is inside the workbook is detected, extracted, and processed separately on Analysis Services server instances within the farm, while Excel Services renders the presentation layer.</span></span> <span data-ttu-id="0e54f-115">在带有 PowerPivot 外接程序的浏览器窗口或 Excel 2010 桌面应用程序中，您可以查看经过完全处理的工作簿。</span><span class="sxs-lookup"><span data-stu-id="0e54f-115">You can view the fully-processed workbook in a browser window or in an Excel 2010 desktop application that has the PowerPivot add-in.</span></span>  
  
 <span data-ttu-id="0e54f-116">下图说明了场对查询处理请求的处理流程。</span><span class="sxs-lookup"><span data-stu-id="0e54f-116">The following diagram shows how a request for query processing moves through the farm.</span></span> <span data-ttu-id="0e54f-117">由于 PowerPivot 数据是 Excel 2010 工作簿的一部分，因此当用户打开 SharePoint 库中的一个 Excel 工作簿并与包含 PowerPivot 数据的数据透视表或数据透视图进行交互时，就会产生查询处理请求。</span><span class="sxs-lookup"><span data-stu-id="0e54f-117">Because PowerPivot data is part of an Excel 2010 workbook, a request for query processing occurs when a user opens an Excel workbook from a SharePoint library and interacts with a PivotTable or PivotChart that contains PowerPivot data.</span></span>  
  
 <span data-ttu-id="0e54f-118">![GMNI_DataProcReq](../media/gmni-dataprocreq.gif "GMNI_DataProcReq")</span><span class="sxs-lookup"><span data-stu-id="0e54f-118">![GMNI_DataProcReq](../media/gmni-dataprocreq.gif "GMNI_DataProcReq")</span></span>  
  
 <span data-ttu-id="0e54f-119">Excel Services 和 PowerPivot for SharePoint 组件处理同一个工作簿 (.xlsx) 文件的不同部分。</span><span class="sxs-lookup"><span data-stu-id="0e54f-119">Excel Services and PowerPivot for SharePoint components process different parts of the same workbook (.xlsx) file.</span></span> <span data-ttu-id="0e54f-120">Excel Services 检测 PowerPivot 数据，并向场中的 PowerPivot 服务器发出处理请求。</span><span class="sxs-lookup"><span data-stu-id="0e54f-120">Excel Services detects PowerPivot data and requests processing from a PowerPivot server in the farm.</span></span> <span data-ttu-id="0e54f-121">PowerPivot 服务器将该请求分配给 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]实例，该实例从内容库中的工作簿内提取数据并加载数据。</span><span class="sxs-lookup"><span data-stu-id="0e54f-121">The PowerPivot server allocates the request to an [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance, which extracts the data from the workbook in the content library and loads the data.</span></span> <span data-ttu-id="0e54f-122">存储在内存中的数据合并回呈现的工作簿中，并传递回 Excel Web Access，以便在浏览器窗口中显示。</span><span class="sxs-lookup"><span data-stu-id="0e54f-122">Data that is stored in memory is merged back into the rendered workbook, and passed back to Excel Web Access for presentation in a browser window.</span></span>  
  
 <span data-ttu-id="0e54f-123">并不是 PowerPivot 工作簿中的所有数据都由 PowerPivot for SharePoint 处理。</span><span class="sxs-lookup"><span data-stu-id="0e54f-123">Not all data in a PowerPivot workbook is handled by PowerPivot for SharePoint.</span></span> <span data-ttu-id="0e54f-124">Excel Services 处理工作表中的表格和单元格数据。</span><span class="sxs-lookup"><span data-stu-id="0e54f-124">Excel Services processes tables and cell data in a worksheet.</span></span> <span data-ttu-id="0e54f-125">只有与 PowerPivot 数据对应的数据透视表、数据透视图和切片器才由 PowerPivot for SharePoint 处理。</span><span class="sxs-lookup"><span data-stu-id="0e54f-125">Only PivotTables, PivotCharts, and Slicers that go against PowerPivot data are handled by the PowerPivot for SharePoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e54f-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e54f-126">See Also</span></span>  
 <span data-ttu-id="0e54f-127">[连接到 Analysis Services](../instances/connect-to-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="0e54f-127">[Connect to Analysis Services](../instances/connect-to-analysis-services.md) </span></span>  
 [<span data-ttu-id="0e54f-128">表格模型数据访问</span><span class="sxs-lookup"><span data-stu-id="0e54f-128">Tabular Model Data Access</span></span>](../tabular-models/tabular-model-data-access.md)  
  
  
