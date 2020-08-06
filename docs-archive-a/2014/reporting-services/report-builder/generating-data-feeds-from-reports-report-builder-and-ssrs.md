---
title: 基于报表生成数据馈送（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4e00789f-6967-42e5-b2b4-03181fdb1e2c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c7f999560bf3216ea84c672c733539d2cad44a15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580038"
---
# <a name="generating-data-feeds-from-reports-report-builder-and-ssrs"></a><span data-ttu-id="1a54a-102">基于报表生成数据馈送（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="1a54a-102">Generating Data Feeds from Reports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1a54a-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Atom 呈现扩展插件可生成 Atom 服务文档，该文档列出报表中可用的数据馈送以及来自报表中的数据区域的数据馈送。</span><span class="sxs-lookup"><span data-stu-id="1a54a-103">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Atom rendering extension generates an Atom service document that lists the data feeds available from a report and the data feeds from the data regions in a report.</span></span> <span data-ttu-id="1a54a-104">使用此扩展插件生成与 Atom 兼容的数据馈送，这些馈送是可读的，并可以与使用从报表生成的数据馈送的应用程序进行交换。</span><span class="sxs-lookup"><span data-stu-id="1a54a-104">You use this extension to generate Atom-compliant data feeds that are readable and exchangeable with applications that can consume data feeds generated from reports.</span></span> <span data-ttu-id="1a54a-105">例如，可以使用 Atom 呈现扩展插件生成可在客户端中使用的数据馈送 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1a54a-105">For example, you can use the Atom rendering extension to generated data feeds that you can then use in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] client.</span></span>  
  
 <span data-ttu-id="1a54a-106">Atom 服务文档为报表中的每个数据区域至少列出一个数据馈送。</span><span class="sxs-lookup"><span data-stu-id="1a54a-106">The Atom service document lists at least one data feed for each data region in a report.</span></span> <span data-ttu-id="1a54a-107">根据数据区域的类型以及数据区域显示的数据， [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 可以自数据区域生成多个数据馈送。</span><span class="sxs-lookup"><span data-stu-id="1a54a-107">Depending on the type of data region and the data that the data region displays, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] might generate multiple data feeds from a data region.</span></span> <span data-ttu-id="1a54a-108">例如，矩阵或图表可以提供多个数据馈送。</span><span class="sxs-lookup"><span data-stu-id="1a54a-108">For example, a matrix or chart can provide multiple data feeds.</span></span> <span data-ttu-id="1a54a-109">Atom 呈现扩展插件创建 Atom 服务文档时，将为每个数据馈送创建一个唯一标识符，在 URL 中使用该标识符可以访问数据馈送的内容。</span><span class="sxs-lookup"><span data-stu-id="1a54a-109">When the Atom rendering extension creates the Atom service document, a unique identifier is created for each data feed and you use the identifier in the URL to access the content of the data feed.</span></span>  
  
 <span data-ttu-id="1a54a-110">Atom 呈现扩展插件为数据馈送生成数据的方式类似于逗号分隔值 (CSV) 呈现扩展插件将数据呈现到 CSV 文件的方式。</span><span class="sxs-lookup"><span data-stu-id="1a54a-110">The way that the Atom rendering extension generates data for a data feed is similar to how the Comma-Separated Value (CSV) rendering extension renders data to a CSV file.</span></span> <span data-ttu-id="1a54a-111">类似于 CSV 文件，数据馈送是报表数据的平展表示形式。</span><span class="sxs-lookup"><span data-stu-id="1a54a-111">Like a CSV file, a data feed is a flattened representation of the report data.</span></span> <span data-ttu-id="1a54a-112">例如，表中有一个行组对某组中的销售额进行加总时，会对每个数据行重复加总，并没有单独的行仅包含总和。</span><span class="sxs-lookup"><span data-stu-id="1a54a-112">For example, a table with a row group that sums the sales within a group repeats the sum in every data row and there is no separate row that contains only the sum.</span></span>  
  
 <span data-ttu-id="1a54a-113">可以使用 Report Manager、Report Server 或与 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]集成的 SharePoint 站点来生成 Atom 服务文档和数据馈送。</span><span class="sxs-lookup"><span data-stu-id="1a54a-113">You can generate Atom service documents and data feeds using Report Manager, Report Server, or a SharePoint site that is integrated with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1a54a-114">Atom 应用于一对相关标准。</span><span class="sxs-lookup"><span data-stu-id="1a54a-114">Atom applies to a pair of related standards.</span></span> <span data-ttu-id="1a54a-115">Atom 服务文档符合 RFC 5023 Atom 发布协议规范，数据馈送符合 RFC 4287 Atom 联合格式协议规范。</span><span class="sxs-lookup"><span data-stu-id="1a54a-115">The Atom service document conforms to the RFC 5023 Atom publishing protocol specification and the data feeds conform to the RFC 4287 Atom syndication format protocol specification.</span></span>  
  
 <span data-ttu-id="1a54a-116">以下各节提供有关如何使用 Atom 呈现扩展插件的附加信息：</span><span class="sxs-lookup"><span data-stu-id="1a54a-116">The following sections provide additional information about how to use the Atom rendering extension:</span></span>  
  
 [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="reports-as-data-feeds"></a><a name="ReportDataAsDataFeeds"></a> <span data-ttu-id="1a54a-117">作为数据馈送的报表</span><span class="sxs-lookup"><span data-stu-id="1a54a-117">Reports as Data Feeds</span></span>  
 <span data-ttu-id="1a54a-118">可以将生产报表作为数据馈送导出，或者可以创建主要目的是以数据馈送的形式向应用程序提供数据的报表。</span><span class="sxs-lookup"><span data-stu-id="1a54a-118">You can export a production report as a data feed or you can create a report whose primary purpose is provide data, in the form of data feeds, to applications.</span></span> <span data-ttu-id="1a54a-119">将报表用作数据馈送为您在以下情况下提供了另一种向应用程序提供数据的方式：当数据不易通过客户端数据访问接口访问时，或者您更喜欢隐藏数据源的复杂性以使数据的使用更为简便时。</span><span class="sxs-lookup"><span data-stu-id="1a54a-119">Using reports as a data feed gives you an additional way to provide data to applications when the data is not easy to access through client data providers, or when you prefer to hide the complexity of the data source and make it simpler to use the data.</span></span> <span data-ttu-id="1a54a-120">将报表用作数据馈送的另一个优点是：您可以使用 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 功能（如 Report Manager、安全、计划和报表快照）来管理用来提供数据馈送的报表。</span><span class="sxs-lookup"><span data-stu-id="1a54a-120">Another benefit of using report data as a data feed is that you can use [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] features such as Report Manager, security, scheduling, and report snapshots to manage the reports that provide data feeds.</span></span>  
  
 <span data-ttu-id="1a54a-121">若要充分利用 Atom 呈现扩展插件，您应该理解报表是如何呈现到数据馈送中的。</span><span class="sxs-lookup"><span data-stu-id="1a54a-121">To get the most from the Atom rendering extension, you should understand how the report is rendered into data feeds.</span></span> <span data-ttu-id="1a54a-122">如果使用现有报表，则若能预测这些报表能够生成的数据馈送将很有用；如果编写报表的目的是专门用作数据馈送，则重要的是能够包括数据并优化报表布局以充分利用数据馈送。</span><span class="sxs-lookup"><span data-stu-id="1a54a-122">If you are using existing reports, being able to predict what the data feeds the reports will generate is useful; if you are writing report specifically for use as data feeds, being able to include the data and fine tune the report layout to maximize the usefulness of the data feeds is valuable.</span></span>  
  
 <span data-ttu-id="1a54a-123">有关详细信息，请参阅[从报表生成数据馈送 &#40;报表生成器和 SSRS&#41;](generate-data-feeds-from-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1a54a-123">For more information, see [Generate Data Feeds from a Report &#40;Report Builder and SSRS&#41;](generate-data-feeds-from-a-report-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="atom-service-document-atomsvc-file"></a><a name="AtomServiceDocument"></a> <span data-ttu-id="1a54a-124">Atom 服务文档（.atomsvc 文件）</span><span class="sxs-lookup"><span data-stu-id="1a54a-124">Atom Service Document (.atomsvc file)</span></span>  
 <span data-ttu-id="1a54a-125">Atom 服务文档指定针对一个或多个数据馈送的连接。</span><span class="sxs-lookup"><span data-stu-id="1a54a-125">An Atom service document specifies a connection to one or more data feeds.</span></span> <span data-ttu-id="1a54a-126">该连接至少是指向生成馈送的数据服务的简单 URL。</span><span class="sxs-lookup"><span data-stu-id="1a54a-126">At a minimum, the connection is a simple URL to the data service that produces the feed.</span></span>  
  
 <span data-ttu-id="1a54a-127">使用 Atom 呈现扩展插件呈现报表数据时，Atom 服务文档将列出可用于报表的数据馈送。</span><span class="sxs-lookup"><span data-stu-id="1a54a-127">When you render report data by using the Atom rendering extension, the Atom service document lists the data feeds available for a report.</span></span> <span data-ttu-id="1a54a-128">该文档为报表中的每个数据区域至少列出一个数据馈送。</span><span class="sxs-lookup"><span data-stu-id="1a54a-128">The document lists at least one data feed for each data region in the report.</span></span> <span data-ttu-id="1a54a-129">表和仪表都只生成一个数据馈送；但矩阵、列表和图表可能生成多个数据馈送，具体取决于它们所显示的数据。</span><span class="sxs-lookup"><span data-stu-id="1a54a-129">Tables and gauges generate only one data feed each, but matrices, lists, and charts might generated multiple depending on the data they display.</span></span>  
  
 <span data-ttu-id="1a54a-130">下图显示了使用两个表和一个图表的报表。</span><span class="sxs-lookup"><span data-stu-id="1a54a-130">The following diagram shows a report that uses two tables and a chart.</span></span>  
  
 <span data-ttu-id="1a54a-131">![RS_Atom_TableAndChartDataFeeds](../media/rs-atom-tableandchartdatafeeds.gif "RS_Atom_TableAndChartDataFeeds")</span><span class="sxs-lookup"><span data-stu-id="1a54a-131">![RS_Atom_TableAndChartDataFeeds](../media/rs-atom-tableandchartdatafeeds.gif "RS_Atom_TableAndChartDataFeeds")</span></span>  
  
 <span data-ttu-id="1a54a-132">从此报表生成的 Atom 服务文档包括三个数据馈送：两个表各对应一个数据馈送，图表对应一个数据馈送。</span><span class="sxs-lookup"><span data-stu-id="1a54a-132">The Atom service document generated from this report includes three data feeds, one for each table and one for the chart.</span></span>  
  
 <span data-ttu-id="1a54a-133">矩阵数据区域可能包括多个数据馈送，这取决于该矩阵的结构。</span><span class="sxs-lookup"><span data-stu-id="1a54a-133">The matrix data regions might have more than one data feed, depending on the structure of the matrix.</span></span> <span data-ttu-id="1a54a-134">下图显示的报表使用生成两个数据馈送的矩阵。</span><span class="sxs-lookup"><span data-stu-id="1a54a-134">The following diagram shows a report that uses a matrix that generates two data feeds.</span></span>  
  
 <span data-ttu-id="1a54a-135">![RS_Atom_PeerDynamicColumns](../media/rs-atom-peerdynamiccolumns.gif "RS_Atom_PeerDynamicColumns")</span><span class="sxs-lookup"><span data-stu-id="1a54a-135">![RS_Atom_PeerDynamicColumns](../media/rs-atom-peerdynamiccolumns.gif "RS_Atom_PeerDynamicColumns")</span></span>  
  
 <span data-ttu-id="1a54a-136">从此报表生成的 Atom 服务文档包括两个数据馈送：两个动态对等列（Territory 和 Year）各对应一个数据馈送。</span><span class="sxs-lookup"><span data-stu-id="1a54a-136">The Atom service document generated from this report includes two data feeds, one for each of the dynamic peer columns: Territory and Year.</span></span> <span data-ttu-id="1a54a-137">下图显示了每个数据馈送的内容。</span><span class="sxs-lookup"><span data-stu-id="1a54a-137">The following diagram shows the content of each data feed.</span></span>  
  
 <span data-ttu-id="1a54a-138">![RS_Atom_PeerDynamicDataFeeds](../media/rs-atom-peerdynamicdatafeeds.gif "RS_Atom_PeerDynamicDataFeeds")</span><span class="sxs-lookup"><span data-stu-id="1a54a-138">![RS_Atom_PeerDynamicDataFeeds](../media/rs-atom-peerdynamicdatafeeds.gif "RS_Atom_PeerDynamicDataFeeds")</span></span>  
  

  
##  <a name="data-feeds"></a><a name="DataFeeds"></a><span data-ttu-id="1a54a-139">数据馈送</span><span class="sxs-lookup"><span data-stu-id="1a54a-139">Data Feeds</span></span>  
 <span data-ttu-id="1a54a-140">数据馈送是一个 XML 文件，它具有一致的不随时间变化的表格格式，以及在每次运行报表时都可能不同的可变数据。</span><span class="sxs-lookup"><span data-stu-id="1a54a-140">The data feed is an XML file that has a consistent tabular format that does not change over time and variable data that can be different each time the report is run.</span></span> <span data-ttu-id="1a54a-141">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 生成的数据馈送采用与 ADO.NET Data Services 生成的数据馈送相同的格式。</span><span class="sxs-lookup"><span data-stu-id="1a54a-141">The data feeds generated by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] are in the same format as those generated by  that ADO.NET Data Services.</span></span>  
  
 <span data-ttu-id="1a54a-142">数据馈送包含两部分：标题和数据。</span><span class="sxs-lookup"><span data-stu-id="1a54a-142">A data feed contains two sections: header and data.</span></span> <span data-ttu-id="1a54a-143">Atom 规范中定义了各部分中的元素。</span><span class="sxs-lookup"><span data-stu-id="1a54a-143">The Atom specification defines the elements in each section.</span></span> <span data-ttu-id="1a54a-144">标题包括用于数据馈送的字符编码架构之类的信息。</span><span class="sxs-lookup"><span data-stu-id="1a54a-144">The header includes information such as the character encoding schema to use with the data feeds.</span></span>  
  
### <a name="header-section"></a><span data-ttu-id="1a54a-145">标题部分</span><span class="sxs-lookup"><span data-stu-id="1a54a-145">Header Section</span></span>  
 <span data-ttu-id="1a54a-146">以下 XML 代码显示数据馈送的标题部分。</span><span class="sxs-lookup"><span data-stu-id="1a54a-146">The following XML code shows the header section of a data feed.</span></span>  
  
 `<?xml version="1.0" encoding="utf-8" standalone="yes"?><feed xmlns:d="https://schemas.microsoft.com/ado/2007/08/dataservices" xmlns:m="https://schemas.microsoft.com/ado/2007/08/dataservices/metadata" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<title type="text"></title>`  
  
 `<id>uuid:1795992c-a6f3-40ec-9243-fbfd0b1a5be3;id=166321</id>`  
  
 `<updated>2009-05-08T23:09:58Z</updated>`  
  
### <a name="data-section"></a><span data-ttu-id="1a54a-147">数据部分</span><span class="sxs-lookup"><span data-stu-id="1a54a-147">Data Section</span></span>  
 <span data-ttu-id="1a54a-148">数据馈送的数据部分 `entry` 为 Atom 呈现扩展插件生成的平展行集中的每一行包含一个 <> 元素。</span><span class="sxs-lookup"><span data-stu-id="1a54a-148">The data section of the data feeds contains one <`entry`> element for each row in the flattened rowset generated by the Atom rendering extension.</span></span>  
  
 <span data-ttu-id="1a54a-149">下图显示了使用组和总计的报表。</span><span class="sxs-lookup"><span data-stu-id="1a54a-149">The following diagram shows a report that uses groups and totals.</span></span>  
  
 <span data-ttu-id="1a54a-150">![RS_Atom_ProductSalesSummaryCircledValues](../media/rs-atom-productsalessummarycircledvalues.gif "RS_Atom_ProductSalesSummaryCircledValues")</span><span class="sxs-lookup"><span data-stu-id="1a54a-150">![RS_Atom_ProductSalesSummaryCircledValues](../media/rs-atom-productsalessummarycircledvalues.gif "RS_Atom_ProductSalesSummaryCircledValues")</span></span>  
  
 <span data-ttu-id="1a54a-151">下面的 XML `entry` 在数据馈送中显示了来自该报表的 <> 元素。</span><span class="sxs-lookup"><span data-stu-id="1a54a-151">The following XML shows an <`entry`> element from that report in a data feed.</span></span> <span data-ttu-id="1a54a-152">请注意，<`entry`> 元素包含组的销售和订单的总计以及所有组的销售和订单的总计。</span><span class="sxs-lookup"><span data-stu-id="1a54a-152">Notice that the <`entry`> element includes the totals of the sales and orders for the group and the totals of sales and orders for all the groups.</span></span> <span data-ttu-id="1a54a-153"><`entry`> 元素包含报表中的所有值。</span><span class="sxs-lookup"><span data-stu-id="1a54a-153">The <`entry`> element includes all values on the report.</span></span>  
  
 `<entry><id>uuid:1795992c-a6f3-40ec-9243-fbfd0b1a5be3;id=166322</id><title type="text"></title><updated>2009-05-08T23:09:58Z</updated><author /><content type="application/xml"><m:properties>`  
  
 `<d:ProductCategory_Value>Accessories</d:ProductCategory_Value>`  
  
 `<d:OrderYear_Value m:type="Edm.Int32">2001</d:OrderYear_Value>`  
  
 `<d:SumLineTotal_Value m:type="Edm.Decimal">20235.364608</d:SumLineTotal_Value>`  
  
 `<d:SumOrderQty_Value m:type="Edm.Int32">1003</d:SumOrderQty_Value>`  
  
 `<d:SumLineTotal_Total_2_1 m:type="Edm.Decimal">1272072.883926</d:SumLineTotal_Total_2_1>`  
  
 `<d:SumOrderQty_Total_2_1 m:type="Edm.Double">61932</d:SumOrderQty_Total_2_1>`  
  
 `<d:SumLineTotal_Total_2_2 m:type="Edm.Decimal">109846381.399888</d:SumLineTotal_Total_2_2>`  
  
 `<d:SumOrderQty_Total_2_2 m:type="Edm.Double">274914</d:SumOrderQty_Total_2_2></m:properties></content>`  
  
 `</entry>`  
  
### <a name="working-with-data-feeds"></a><span data-ttu-id="1a54a-154">使用数据馈送</span><span class="sxs-lookup"><span data-stu-id="1a54a-154">Working with Data Feeds</span></span>  
 <span data-ttu-id="1a54a-155">由报表生成的所有数据馈送都包括生成数据馈送的数据区域父级范围内的报表项。</span><span class="sxs-lookup"><span data-stu-id="1a54a-155">All data feeds generated by the report include the report items that are in scope of the parent of the data region that generate the data feeds.</span></span> <span data-ttu-id="1a54a-156">.</span><span class="sxs-lookup"><span data-stu-id="1a54a-156">.</span></span> <span data-ttu-id="1a54a-157">设想有一个报表包含若干表和一个图表。</span><span class="sxs-lookup"><span data-stu-id="1a54a-157">Imagine a report that has several tables and a chart.</span></span> <span data-ttu-id="1a54a-158">报表正文中的文本框提供有关每个数据区域的说明性文本。</span><span class="sxs-lookup"><span data-stu-id="1a54a-158">Text boxes in the report body provides descriptive text of each data region.</span></span> <span data-ttu-id="1a54a-159">该报表生成的每个数据馈送中的每个条目都包括该文本框的值。</span><span class="sxs-lookup"><span data-stu-id="1a54a-159">Every entry in every data feed that the report generates includes the value of the text box.</span></span> <span data-ttu-id="1a54a-160">例如，如果文本为“Chart displays monthly sales averages by sales region”，则所有三个数据馈送都会在每一行中包括此文本。</span><span class="sxs-lookup"><span data-stu-id="1a54a-160">For example, if the text is "Chart displays monthly sales averages by sales region", all three data feeds would include this text on each row.</span></span>  
  
 <span data-ttu-id="1a54a-161">如果报表布局包括分层数据关系，如嵌套数据区域，这些关系将包括在报表数据的平展行集中。</span><span class="sxs-lookup"><span data-stu-id="1a54a-161">If the report layout includes hierarchical data relationships, such as nested data regions, those relationships are included in the flattened rowset of report data.</span></span>  
  
 <span data-ttu-id="1a54a-162">嵌套数据区域的数据行通常较宽，特别是在嵌套表和矩阵包括组和总计的情况下。</span><span class="sxs-lookup"><span data-stu-id="1a54a-162">The data rows for nested data regions are typically wide, especially if the nested tables and matrices include groups and totals.</span></span> <span data-ttu-id="1a54a-163">您可能会发现，将报表导出到数据馈送并且查看数据馈送以确定生成的数据就是所需数据，这会很有帮助。</span><span class="sxs-lookup"><span data-stu-id="1a54a-163">You might find it useful to export the report to a data feed and view the data feed to verify that the data generated is what you expected.</span></span>  
  
 <span data-ttu-id="1a54a-164">当 Atom 呈现扩展插件创建 Atom 服务文档时，将为数据馈送创建一个唯一标识符，在 URL 中使用该标识符可以查看数据馈送的内容。</span><span class="sxs-lookup"><span data-stu-id="1a54a-164">When the Atom rendering extension creates the Atom service document, a unique identifier is created for the data feed and you use the identifier in the URL to view the content of the data feed.</span></span> <span data-ttu-id="1a54a-165">示例 Atom 服务文档（如上所示）包括 URL <http://ServerName/ReportServer?%2fProduct+Sales+Summary&rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=xAx0x1> "。</span><span class="sxs-lookup"><span data-stu-id="1a54a-165">The sample Atom service document, shown above, includes the URL <http://ServerName/ReportServer?%2fProduct+Sales+Summary&rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=xAx0x1>".</span></span> <span data-ttu-id="1a54a-166">该 URL 标识报表 (Product Sales Summary)、Atom 呈现格式 (ATOM) 以及数据馈送的名称 (xAx0x1)。</span><span class="sxs-lookup"><span data-stu-id="1a54a-166">The URL identifies the report (Product Sales Summary), the Atom rendering format (ATOM), and the name of the data feed (xAx0x1).</span></span>  
  
 <span data-ttu-id="1a54a-167">报表项名称默认为报表项的报表定义语言 (RDL) 元素名称，这些名称经常较为直观或容易记忆。</span><span class="sxs-lookup"><span data-stu-id="1a54a-167">Report item names default to the report definition language (RDL) element names of the report items and often they are not intuitive or easy to remember.</span></span> <span data-ttu-id="1a54a-168">例如，放入报表的第一个矩阵的默认名称为 Tablix 1。</span><span class="sxs-lookup"><span data-stu-id="1a54a-168">For example, the default name of the first matrix placed in a report is Tablix 1.</span></span> <span data-ttu-id="1a54a-169">数据馈送使用这些名称。</span><span class="sxs-lookup"><span data-stu-id="1a54a-169">The data feeds use these names.</span></span>  
  
 <span data-ttu-id="1a54a-170">若要令数据馈送易于使用，可以使用数据区域的 DataElementName 属性来提供友好名称。</span><span class="sxs-lookup"><span data-stu-id="1a54a-170">To make the data feed easier to work with, you can use the DataElementName property of the data region to provide friendly names.</span></span> <span data-ttu-id="1a54a-171">如果为 DataElementName 提供了值，则> 将使用 <数据馈送子元素， `d` 而不是使用默认的数据区域名称。</span><span class="sxs-lookup"><span data-stu-id="1a54a-171">If you provide a value for DataElementName the data feed subelement <`d`> will use is it instead of the default data region name.</span></span> <span data-ttu-id="1a54a-172">例如，如果数据区域的默认名称为 Tablix1，DataElementName 设置为 SalesByTerritoryYear，则 `d` 数据馈送中的 <> 将使用 SalesByTerritoryYear。</span><span class="sxs-lookup"><span data-stu-id="1a54a-172">For example, if the default name of a data regions is Tablix1 and DataElementName set SalesByTerritoryYear then the <`d`> in the data feed uses SalesByTerritoryYear.</span></span> <span data-ttu-id="1a54a-173">如果数据区域具有两个数据馈送（类似上述矩阵报表），则数据馈送中使用的名称为 SalesByTerritoryYear _Territory 和 SalesByTerritoryYear _Year。</span><span class="sxs-lookup"><span data-stu-id="1a54a-173">If the data regions has two data feeds like the matrix report described above, the names used in the data feeds are SalesByTerritoryYear _Territory and SalesByTerritoryYear _Year.</span></span>  
  
 <span data-ttu-id="1a54a-174">如果对报表显示的数据和数据馈送中的数据进行比较，则可能发现一些差异。</span><span class="sxs-lookup"><span data-stu-id="1a54a-174">If you compare the data shown on the report and the data in the data feed, you might notice some differences.</span></span> <span data-ttu-id="1a54a-175">报表经常显示格式化的数值和时间/日期数据，但数据馈送包含非格式化的数据。</span><span class="sxs-lookup"><span data-stu-id="1a54a-175">Reports often shows formatted numeric and time/date data whereas the data feed contains unformatted data.</span></span>  
  
 <span data-ttu-id="1a54a-176">数据馈送用 .atom 文件扩展名保存。</span><span class="sxs-lookup"><span data-stu-id="1a54a-176">A data feed is saved with the .atom file name extension.</span></span> <span data-ttu-id="1a54a-177">可以使用文本或 XML 编辑器（如记事本或 XML 编辑器）来查看文件结构和内容。</span><span class="sxs-lookup"><span data-stu-id="1a54a-177">You can use a text or XML editor such as Notepad or XML Editor to view the file structure and content.</span></span>  
  

  
##  <a name="flattening-report-data"></a><a name="FlatteningReportData"></a> <span data-ttu-id="1a54a-178">平展报表数据</span><span class="sxs-lookup"><span data-stu-id="1a54a-178">Flattening Report Data</span></span>  
 <span data-ttu-id="1a54a-179">Atom 呈现器将报表数据提供为 XML 格式的平展行集。</span><span class="sxs-lookup"><span data-stu-id="1a54a-179">The Atom renderer provides report data as flattened rowsets in an XML format.</span></span> <span data-ttu-id="1a54a-180">用于平展数据表的规则与用于 CSV 呈现器的规则相同，只有以下几点例外：</span><span class="sxs-lookup"><span data-stu-id="1a54a-180">The rules for flattening data tables are the same to those of the CSV renderer with a few exceptions:</span></span>  
  
-   <span data-ttu-id="1a54a-181">范围中的项平展到详细信息级别。</span><span class="sxs-lookup"><span data-stu-id="1a54a-181">Items in scope are flattened to the detail level.</span></span> <span data-ttu-id="1a54a-182">不同于 CSV 呈现器，顶级文本框显示在写入数据馈送的每个条目中。</span><span class="sxs-lookup"><span data-stu-id="1a54a-182">Unlike the CSV renderer, the text boxes at the top level appear in each entry written to the data feed.</span></span>  
  
-   <span data-ttu-id="1a54a-183">在输出的每一行上呈现报表参数值。</span><span class="sxs-lookup"><span data-stu-id="1a54a-183">Report parameter values are rendered on each row of the output.</span></span>  
  
 <span data-ttu-id="1a54a-184">分层数据和分组数据必须进行平展才能以与 Atom 兼容的格式表示。</span><span class="sxs-lookup"><span data-stu-id="1a54a-184">Hierarchical and grouped data must be flattened in order to be represented in the Atom-compliant format.</span></span> <span data-ttu-id="1a54a-185">呈现扩展插件可将报表平展为用于表示数据区域中嵌套组的树结构。</span><span class="sxs-lookup"><span data-stu-id="1a54a-185">The rendering extension flattens the report into a tree structure that represents the nested groups within the data region.</span></span> <span data-ttu-id="1a54a-186">要平展报表：</span><span class="sxs-lookup"><span data-stu-id="1a54a-186">To flatten the report:</span></span>  
  
-   <span data-ttu-id="1a54a-187">行层次结构在列层次结构之前进行平展。</span><span class="sxs-lookup"><span data-stu-id="1a54a-187">A row hierarchy is flattened before a column hierarchy.</span></span>  
  
-   <span data-ttu-id="1a54a-188">行层次结构的成员在列层次结构的成员之前呈现到数据馈送。</span><span class="sxs-lookup"><span data-stu-id="1a54a-188">Members of the row hierarchy are rendered to the data feed before members of the column hierarchy.</span></span>  
  
-   <span data-ttu-id="1a54a-189">列按照以下顺序排序：表体中的文本框的顺序为从左到右，从上到下，后面紧跟数据区域，后者顺序为从左到右，从上到下。</span><span class="sxs-lookup"><span data-stu-id="1a54a-189">Columns are ordered as follows: text boxes in body order left-to-right, top-to-bottom followed by data regions ordered left-to-right, top-to-bottom.</span></span>  
  
-   <span data-ttu-id="1a54a-190">在数据区域中，列按照以下顺序排序：角成员、行层次结构成员、列层次结构成员，然后是单元。</span><span class="sxs-lookup"><span data-stu-id="1a54a-190">Within a data region, the columns are ordered as follows: corner members, row hierarchy members, column hierarchy members, and then cells.</span></span>  
  
-   <span data-ttu-id="1a54a-191">对等数据区域是一些共享一个公共数据区域或动态祖先的数据区域或动态组。</span><span class="sxs-lookup"><span data-stu-id="1a54a-191">Peer data regions are data regions or dynamic groups that share a common data region or dynamic ancestor.</span></span> <span data-ttu-id="1a54a-192">对等数据通过平展后的树的分支进行标识。</span><span class="sxs-lookup"><span data-stu-id="1a54a-192">Peer data is identified by branching of the flattened tree.</span></span>  
  
 <span data-ttu-id="1a54a-193">有关详细信息，请参阅 [表、矩阵和列表（报表生成器和 SSRS）](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1a54a-193">For more information, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="atom-rendering-rules"></a><a name="AtomRendering"></a> <span data-ttu-id="1a54a-194">Atom 呈现规则</span><span class="sxs-lookup"><span data-stu-id="1a54a-194">Atom Rendering Rules</span></span>  
 <span data-ttu-id="1a54a-195">Atom 呈现扩展插件在呈现数据馈送时忽略以下信息：</span><span class="sxs-lookup"><span data-stu-id="1a54a-195">The Atom rendering extension ignores the following information when rendering a data feed:</span></span>  
  
-   <span data-ttu-id="1a54a-196">格式设置和布局</span><span class="sxs-lookup"><span data-stu-id="1a54a-196">Formatting and layout</span></span>  
  
-   <span data-ttu-id="1a54a-197">页眉</span><span class="sxs-lookup"><span data-stu-id="1a54a-197">Page header</span></span>  
  
-   <span data-ttu-id="1a54a-198">页脚</span><span class="sxs-lookup"><span data-stu-id="1a54a-198">Page footer</span></span>  
  
-   <span data-ttu-id="1a54a-199">自定义报表项</span><span class="sxs-lookup"><span data-stu-id="1a54a-199">Custom report items</span></span>  
  
-   <span data-ttu-id="1a54a-200">矩形</span><span class="sxs-lookup"><span data-stu-id="1a54a-200">Rectangles</span></span>  
  
-   <span data-ttu-id="1a54a-201">线条</span><span class="sxs-lookup"><span data-stu-id="1a54a-201">Lines</span></span>  
  
-   <span data-ttu-id="1a54a-202">映像</span><span class="sxs-lookup"><span data-stu-id="1a54a-202">Images</span></span>  
  
-   <span data-ttu-id="1a54a-203">自动小计</span><span class="sxs-lookup"><span data-stu-id="1a54a-203">Automatic subtotals</span></span>  
  
 <span data-ttu-id="1a54a-204">对其余的报表项进行排序，先从上到下排，再从左到右排。</span><span class="sxs-lookup"><span data-stu-id="1a54a-204">The remaining report items are sorted, from top to bottom, and then left to right.</span></span> <span data-ttu-id="1a54a-205">之后，每一项将呈现到一列中。</span><span class="sxs-lookup"><span data-stu-id="1a54a-205">Each item is then rendered to a column.</span></span> <span data-ttu-id="1a54a-206">如果报表有嵌套数据项（如列表或表），则会在每一行中重复它的父项。</span><span class="sxs-lookup"><span data-stu-id="1a54a-206">If the report has nested data items like lists or tables, the parent items are repeated on each row.</span></span>  
  
 <span data-ttu-id="1a54a-207">下表说明了呈现报表项时这些报表项的外观：</span><span class="sxs-lookup"><span data-stu-id="1a54a-207">The following table indicates the appearance of report items when rendered:</span></span>  
  
|<span data-ttu-id="1a54a-208">项</span><span class="sxs-lookup"><span data-stu-id="1a54a-208">Item</span></span>|<span data-ttu-id="1a54a-209">呈现行为</span><span class="sxs-lookup"><span data-stu-id="1a54a-209">Rendering behavior</span></span>|  
|----------|------------------------|  
|<span data-ttu-id="1a54a-210">表</span><span class="sxs-lookup"><span data-stu-id="1a54a-210">Table</span></span>|<span data-ttu-id="1a54a-211">呈现方式为扩展该表，在只保留最起码的格式的情况下为每一行和每一列都分别创建行和列。</span><span class="sxs-lookup"><span data-stu-id="1a54a-211">Renders by expanding the table and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="1a54a-212">小计行和小计列没有列标题或行标题。</span><span class="sxs-lookup"><span data-stu-id="1a54a-212">Subtotal rows and columns do not have column or row headings.</span></span> <span data-ttu-id="1a54a-213">不支持钻取报表。</span><span class="sxs-lookup"><span data-stu-id="1a54a-213">Drillthrough reports are not supported.</span></span>|  
|<span data-ttu-id="1a54a-214">Matrix</span><span class="sxs-lookup"><span data-stu-id="1a54a-214">Matrix</span></span>|<span data-ttu-id="1a54a-215">呈现方式为扩展该矩阵，在只保留最起码的格式的情况下为每一行和每一列都分别创建行和列。</span><span class="sxs-lookup"><span data-stu-id="1a54a-215">Renders by expanding the matrix and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="1a54a-216">小计行和小计列没有列标题或行标题。</span><span class="sxs-lookup"><span data-stu-id="1a54a-216">Subtotal rows and columns do not have column or row headings.</span></span>|  
|<span data-ttu-id="1a54a-217">列出</span><span class="sxs-lookup"><span data-stu-id="1a54a-217">List</span></span>|<span data-ttu-id="1a54a-218">为列表中每一明细行或实例呈现一个记录。</span><span class="sxs-lookup"><span data-stu-id="1a54a-218">Renders a record for each detail row or instance in the list.</span></span>|  
|<span data-ttu-id="1a54a-219">子报表</span><span class="sxs-lookup"><span data-stu-id="1a54a-219">Subreport</span></span>|<span data-ttu-id="1a54a-220">对于内容的每个实例，都会重复它的父项。</span><span class="sxs-lookup"><span data-stu-id="1a54a-220">The parent item is repeated for each instance of the contents.</span></span>|  
|<span data-ttu-id="1a54a-221">图表</span><span class="sxs-lookup"><span data-stu-id="1a54a-221">Chart</span></span>|<span data-ttu-id="1a54a-222">为每个图表值呈现具有所有图表标签的记录。</span><span class="sxs-lookup"><span data-stu-id="1a54a-222">Renders a record with all chart labels for each chart value.</span></span> <span data-ttu-id="1a54a-223">来自系列和类别的标签采用平展的层次结构，并包含在图表值的行中。</span><span class="sxs-lookup"><span data-stu-id="1a54a-223">Labels from series and categories in hierarchies are flattened and included in the row for a chart value.</span></span>|  
|<span data-ttu-id="1a54a-224">数据条</span><span class="sxs-lookup"><span data-stu-id="1a54a-224">Data bar</span></span>|<span data-ttu-id="1a54a-225">像图表一样呈现。</span><span class="sxs-lookup"><span data-stu-id="1a54a-225">Renders like a chart.</span></span> <span data-ttu-id="1a54a-226">通常，数据条并不包括层次结构或标签。</span><span class="sxs-lookup"><span data-stu-id="1a54a-226">Typically, a data bar does not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="1a54a-227">迷你图</span><span class="sxs-lookup"><span data-stu-id="1a54a-227">Sparkline</span></span>|<span data-ttu-id="1a54a-228">像图表一样呈现。</span><span class="sxs-lookup"><span data-stu-id="1a54a-228">Renders like a chart.</span></span> <span data-ttu-id="1a54a-229">通常，迷你图并不包括层次结构或标签。</span><span class="sxs-lookup"><span data-stu-id="1a54a-229">Typically, a sparkline does not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="1a54a-230">仪表</span><span class="sxs-lookup"><span data-stu-id="1a54a-230">Gauge</span></span>|<span data-ttu-id="1a54a-231">作为单个记录呈现，具有线性刻度的最小值和最大值、范围的起始和终止值，以及指针的值。</span><span class="sxs-lookup"><span data-stu-id="1a54a-231">Renders as a single record with the minimum and maximum values of the linear scale, start and end values of the range, and the value of the pointer.</span></span>|  
|<span data-ttu-id="1a54a-232">指示器</span><span class="sxs-lookup"><span data-stu-id="1a54a-232">Indicator</span></span>|<span data-ttu-id="1a54a-233">作为单个记录呈现，具有活动状态名称、可用状态以及数据值。</span><span class="sxs-lookup"><span data-stu-id="1a54a-233">Renders as a single record with the active state name, available states, and the data value.</span></span>|  
|<span data-ttu-id="1a54a-234">映射</span><span class="sxs-lookup"><span data-stu-id="1a54a-234">Map</span></span>|<span data-ttu-id="1a54a-235">为每个地图数据区域生成数据馈送。</span><span class="sxs-lookup"><span data-stu-id="1a54a-235">Generates a data feed for each map data region.</span></span> <span data-ttu-id="1a54a-236">如果多个地图层使用相同数据区域，数据馈送将包含所有层的数据。</span><span class="sxs-lookup"><span data-stu-id="1a54a-236">If multiple map layers use the same data region, the data feed includes all of them.</span></span> <span data-ttu-id="1a54a-237">该数据馈送包含一个记录，该记录包含地图层的每个地图成员的标签和值。</span><span class="sxs-lookup"><span data-stu-id="1a54a-237">The data feed includes a record with the labels and values for each map member of the map layer.</span></span>|  
  

  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="1a54a-238">设备信息设置</span><span class="sxs-lookup"><span data-stu-id="1a54a-238">Device Information Settings</span></span>  
 <span data-ttu-id="1a54a-239">您可以更改此呈现器的某些默认设置，包括要使用的编码架构。</span><span class="sxs-lookup"><span data-stu-id="1a54a-239">You can change some default settings for this renderer, including the encoding schema to use.</span></span> <span data-ttu-id="1a54a-240">有关详细信息，请参阅 [ATOM Device Information Settings](../atom-device-information-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="1a54a-240">For more information, see [ATOM Device Information Settings](../atom-device-information-settings.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="1a54a-241">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1a54a-241">See Also</span></span>  
 <span data-ttu-id="1a54a-242">[导出到 CSV 文件 &#40;报表生成器和 SSRS&#41;](exporting-to-a-csv-file-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1a54a-242">[Exporting to a CSV File &#40;Report Builder and SSRS&#41;](exporting-to-a-csv-file-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1a54a-243">导出报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1a54a-243">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](export-reports-report-builder-and-ssrs.md)  
  
  
