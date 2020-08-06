---
title: 数据源和连接方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- connections [Reporting Services], data sources
- reports [Reporting Services], data
- data sources [Reporting Services], methods
ms.assetid: 50999b52-fc7c-4333-9fb0-d04c37a4c90f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 29dd8dd1c002ab3b7d4594a4e25ec44bdb2cc8ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691594"
---
# <a name="data-sources-and-connection-methods"></a><span data-ttu-id="10a14-102">数据源和连接方法</span><span class="sxs-lookup"><span data-stu-id="10a14-102">Data Sources and Connection Methods</span></span>
  <span data-ttu-id="10a14-103">可以使用以下方法设置和管理数据源连接和凭据。</span><span class="sxs-lookup"><span data-stu-id="10a14-103">You can use these methods to set and manage data source connections and credentials.</span></span>  
  
|<span data-ttu-id="10a14-104">方法</span><span class="sxs-lookup"><span data-stu-id="10a14-104">Method</span></span>|<span data-ttu-id="10a14-105">操作</span><span class="sxs-lookup"><span data-stu-id="10a14-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateDataSource%2A>|<span data-ttu-id="10a14-106">在报表服务器数据库或 SharePoint 库中创建新数据源。</span><span class="sxs-lookup"><span data-stu-id="10a14-106">Creates a new data source in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DisableDataSource%2A>|<span data-ttu-id="10a14-107">禁用已启用的数据源。</span><span class="sxs-lookup"><span data-stu-id="10a14-107">Disables a data source that is enabled.</span></span>|  
|<xref:ReportService2010.ReportingService2010.EnableDataSource%2A>|<span data-ttu-id="10a14-108">启用已禁用的数据源。</span><span class="sxs-lookup"><span data-stu-id="10a14-108">Enables a data source that is disabled.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetDataSourceContents%2A>|<span data-ttu-id="10a14-109">返回数据源的内容。</span><span class="sxs-lookup"><span data-stu-id="10a14-109">Returns the contents of a data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSourcePrompts%2A>|<span data-ttu-id="10a14-110">获取指定项的数据源提示。</span><span class="sxs-lookup"><span data-stu-id="10a14-110">Gets the data source prompts for a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSources%2A>|<span data-ttu-id="10a14-111">返回目录中项的数据源。</span><span class="sxs-lookup"><span data-stu-id="10a14-111">Returns the data sources for an item in the catalog.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListDependentItems%2A>|<span data-ttu-id="10a14-112">返回引用指定目录项的目录项列表。</span><span class="sxs-lookup"><span data-stu-id="10a14-112">Returns a list of catalog items that reference a specified catalog item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSubscriptionsUsingDataSource%2A>|<span data-ttu-id="10a14-113">返回与给定数据源关联的订阅列表。</span><span class="sxs-lookup"><span data-stu-id="10a14-113">Returns a list of subscriptions that are associated with a given data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetDataSourceContents%2A>|<span data-ttu-id="10a14-114">设置与数据源关联的连接属性。</span><span class="sxs-lookup"><span data-stu-id="10a14-114">Sets the connection properties that are associated with a data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetItemDataSources%2A>|<span data-ttu-id="10a14-115">为报表服务器数据库或 SharePoint 库中的项设置数据源。</span><span class="sxs-lookup"><span data-stu-id="10a14-115">Sets the data sources for an item in a report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.TestConnectForDataSourceDefinition%2A>|<span data-ttu-id="10a14-116">测试数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="10a14-116">Tests the connection for a data source.</span></span> <span data-ttu-id="10a14-117">此方法支持数据源的直接测试。</span><span class="sxs-lookup"><span data-stu-id="10a14-117">This method supports the direct testing of the data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.TestConnectForItemDataSource%2A>|<span data-ttu-id="10a14-118">测试数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="10a14-118">Tests the connection for a data source.</span></span> <span data-ttu-id="10a14-119">此方法支持已发布的数据源的测试，这些数据源由报表或模型和共享数据源使用。</span><span class="sxs-lookup"><span data-stu-id="10a14-119">This method supports the testing of published data sources that are used by reports or models and shared data sources.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10a14-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10a14-120">See Also</span></span>  
 <span data-ttu-id="10a14-121">[使用 Web 服务和 .NET Framework 生成应用程序](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="10a14-121">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="10a14-122">[报表服务器 Web 服务](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="10a14-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="10a14-123">[报表服务器 Web 服务方法](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="10a14-123">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="10a14-124">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="10a14-124">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
