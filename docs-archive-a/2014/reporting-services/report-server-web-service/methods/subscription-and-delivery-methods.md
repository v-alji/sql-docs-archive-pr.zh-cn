---
title: 订阅和传递方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- reports [Reporting Services], delivering
- delivery [Reporting Services]
- methods [Reporting Services], subscription and delivery
- subscriptions [Reporting Services], about subscriptions
ms.assetid: a8637501-1817-4ccc-b07d-dd9ed5608805
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6ae92a6abd5c25b9ab1236a2b5b11429d210cba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688539"
---
# <a name="subscription-and-delivery-methods"></a><span data-ttu-id="08e6d-102">订阅和传递方法</span><span class="sxs-lookup"><span data-stu-id="08e6d-102">Subscription and Delivery Methods</span></span>
  <span data-ttu-id="08e6d-103">可以使用这些方法来创建和管理目录项的订阅和传递。</span><span class="sxs-lookup"><span data-stu-id="08e6d-103">You can use these methods to create and manage subscriptions and delivery of catalog items.</span></span>  
  
|<span data-ttu-id="08e6d-104">方法</span><span class="sxs-lookup"><span data-stu-id="08e6d-104">Method</span></span>|<span data-ttu-id="08e6d-105">操作</span><span class="sxs-lookup"><span data-stu-id="08e6d-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>|<span data-ttu-id="08e6d-106">为指定的项创建数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="08e6d-106">Creates a data-driven subscription for a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetDataDrivenSubscriptionProperties%2A>|<span data-ttu-id="08e6d-107">返回数据驱动订阅的属性。</span><span class="sxs-lookup"><span data-stu-id="08e6d-107">Returns the properties for a data-driven subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateSubscription%2A>|<span data-ttu-id="08e6d-108">创建报表服务器数据库或 SharePoint 库中指定项的订阅。</span><span class="sxs-lookup"><span data-stu-id="08e6d-108">Creates a subscription for the specified item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteSubscription%2A>|<span data-ttu-id="08e6d-109">从报表服务器数据库删除订阅。</span><span class="sxs-lookup"><span data-stu-id="08e6d-109">Deletes a subscription from the report server database.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSubscriptionProperties%2A>|<span data-ttu-id="08e6d-110">返回订阅的属性。</span><span class="sxs-lookup"><span data-stu-id="08e6d-110">Returns the properties of a subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListMySubscriptions%2A>|<span data-ttu-id="08e6d-111">检索报表服务器或 SharePoint 网站的当前用户为给定目录项创建的订阅列表。</span><span class="sxs-lookup"><span data-stu-id="08e6d-111">Retrieves a list of subscriptions that have been created by the current user of the report server or SharePoint site for the given catalog item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSubscriptions%2A>|<span data-ttu-id="08e6d-112">检索为给定项创建的订阅列表。</span><span class="sxs-lookup"><span data-stu-id="08e6d-112">Retrieves a list of subscriptions that have been created for a given item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.PrepareQuery%2A>|<span data-ttu-id="08e6d-113">返回一个数据集，其中包含由数据驱动订阅的传递查询检索的字段。</span><span class="sxs-lookup"><span data-stu-id="08e6d-113">Returns a data set containing the fields retrieved by the delivery query for a data-driven subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A>|<span data-ttu-id="08e6d-114">设置数据驱动订阅的属性的值。</span><span class="sxs-lookup"><span data-stu-id="08e6d-114">Sets the values of properties of a data-driven subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A>|<span data-ttu-id="08e6d-115">设置订阅的属性的值。</span><span class="sxs-lookup"><span data-stu-id="08e6d-115">Sets the values of properties of a subscription.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08e6d-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08e6d-116">See Also</span></span>  
 <span data-ttu-id="08e6d-117">[使用 Web 服务和 .NET Framework 生成应用程序](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="08e6d-117">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="08e6d-118">[报表服务器 Web 服务](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="08e6d-118">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="08e6d-119">[报表服务器 Web 服务方法](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="08e6d-119">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="08e6d-120">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="08e6d-120">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
