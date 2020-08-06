---
title: 发布数据源和报表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- publishing data sources [Reporting Services]
- publishing reports [Reporting Services]
- data sources [Reporting Services], managing
ms.assetid: 3a740f8a-1060-4ec3-938b-2305b6887ebd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 941362afde1cfe5dd3d235c9f243fb17875adadc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687439"
---
# <a name="publishing-data-sources-and-reports"></a><span data-ttu-id="8731a-102">发布数据源和报表</span><span class="sxs-lookup"><span data-stu-id="8731a-102">Publishing Data Sources and Reports</span></span>
  <span data-ttu-id="8731a-103">在发布报表之前，您应预览报表以查看其运行时的外观。</span><span class="sxs-lookup"><span data-stu-id="8731a-103">Before publishing your report, you should preview the report to see how it will look when it is run.</span></span> <span data-ttu-id="8731a-104">您可以继续改进设计，直到对结果满意为止。</span><span class="sxs-lookup"><span data-stu-id="8731a-104">You can continue to refine the design until you are satisfied with the results.</span></span>  
  
 <span data-ttu-id="8731a-105">在设计和测试完报表之后，您可能想要与他人共享报表。</span><span class="sxs-lookup"><span data-stu-id="8731a-105">After you design and test your report, you may want to share it with other individuals.</span></span> <span data-ttu-id="8731a-106">若要共享报表，您需要将其发布或“部署” \*\* 到报表服务器或 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="8731a-106">To share your report, you need to publish, or *deploy*, it to a report server or SharePoint site.</span></span> <span data-ttu-id="8731a-107">发布报表后，对报表服务器或 SharePoint 站点拥有权限的个人可运行该报表。</span><span class="sxs-lookup"><span data-stu-id="8731a-107">After it has been published, individuals who have permissions to the report server or the SharePoint site can run your report.</span></span> <span data-ttu-id="8731a-108">另外，对报表服务器拥有管理员权限的人可创建对报表的订阅，以便可以定期更新报表并将其发送至用户。</span><span class="sxs-lookup"><span data-stu-id="8731a-108">In addition, a person with administrator permissions on the report server can create subscriptions to your report so that the report can be updated and sent to users on a regular schedule.</span></span>  
  
 <span data-ttu-id="8731a-109">如果您使用了共享数据源来创建报表，则需要将其发布至与报表相同的位置。</span><span class="sxs-lookup"><span data-stu-id="8731a-109">If you used a shared data source to create your report, you need to publish it to the same location as the report.</span></span> <span data-ttu-id="8731a-110">与报表的管理类似，可在报表服务器上单独管理共享数据源。</span><span class="sxs-lookup"><span data-stu-id="8731a-110">Like reports, shared data sources can be managed separately on the report server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8731a-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="8731a-111">In This Section</span></span>  
 [<span data-ttu-id="8731a-112">预览报表</span><span class="sxs-lookup"><span data-stu-id="8731a-112">Previewing Reports</span></span>](previewing-reports.md)  
 <span data-ttu-id="8731a-113">说明如何在发布报表之前对其进行预览。</span><span class="sxs-lookup"><span data-stu-id="8731a-113">Describes how to preview a report before you publish it.</span></span>  
  
 [<span data-ttu-id="8731a-114">将报表发布到报表服务器</span><span class="sxs-lookup"><span data-stu-id="8731a-114">Publishing Reports to a Report Server</span></span>](publishing-reports-to-a-report-server.md)  
 <span data-ttu-id="8731a-115">说明如何将报表发布到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="8731a-115">Describes how to publish a report to a report server.</span></span>  
  
 [<span data-ttu-id="8731a-116">用于 SharePoint 模式下在报表服务器上已发布的报表项的 URL 示例 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="8731a-116">URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;</span></span>](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)  
 <span data-ttu-id="8731a-117">说明如何将报表发布到 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="8731a-117">Describes how to publish a report to a SharePoint site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8731a-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8731a-118">See Also</span></span>  
 <span data-ttu-id="8731a-119">[Reporting Services 中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="8731a-119">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="8731a-120">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8731a-120">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="8731a-121">[页面布局和呈现 &#40;报表生成器和 SSRS&#41;](../report-design/page-layout-and-rendering-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8731a-121">[Page Layout and Rendering &#40;Report Builder and SSRS&#41;](../report-design/page-layout-and-rendering-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8731a-122">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8731a-122">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="8731a-123">[查找、查看和管理 &#40;报表生成器和 SSRS 的报表 &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8731a-123">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8731a-124">[导出报表 &#40;报表生成器和 SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8731a-124">[Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8731a-125">打印报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="8731a-125">Print Reports &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/print-reports-report-builder-and-ssrs.md)  
  
  
