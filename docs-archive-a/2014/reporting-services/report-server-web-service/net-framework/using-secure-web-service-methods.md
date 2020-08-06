---
title: 使用安全 Web 服务方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e88a164602f9bbe6ad42c3897285a484cac94466
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692685"
---
# <a name="using-secure-web-service-methods"></a><span data-ttu-id="b2cba-102">使用安全 Web 服务方法</span><span class="sxs-lookup"><span data-stu-id="b2cba-102">Using Secure Web Service Methods</span></span>
  <span data-ttu-id="b2cba-103">当您调用某些报表服务器 Web 服务方法时，它们可能要求安全连接。</span><span class="sxs-lookup"><span data-stu-id="b2cba-103">Certain Report Server Web service methods may require a secure connection when you invoke them.</span></span> <span data-ttu-id="b2cba-104">要求安全连接的方法由 RSReportServer.config 文件中的 `SecureConnectionLevel` 设置确定。</span><span class="sxs-lookup"><span data-stu-id="b2cba-104">The methods that require a secure connection are determined by the `SecureConnectionLevel` setting in the RSReportServer.config file.</span></span> <span data-ttu-id="b2cba-105">该设置的值是整数值，大于等于 0 即可。</span><span class="sxs-lookup"><span data-stu-id="b2cba-105">The value of the setting is an integer value with a valid range of 0 and higher.</span></span> <span data-ttu-id="b2cba-106">下表介绍了这些值。</span><span class="sxs-lookup"><span data-stu-id="b2cba-106">The following table describes these values.</span></span>  
  
|<span data-ttu-id="b2cba-107">级别</span><span class="sxs-lookup"><span data-stu-id="b2cba-107">Level</span></span>|<span data-ttu-id="b2cba-108">说明</span><span class="sxs-lookup"><span data-stu-id="b2cba-108">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b2cba-109">**0**</span><span class="sxs-lookup"><span data-stu-id="b2cba-109">**0**</span></span>|<span data-ttu-id="b2cba-110">不安全。</span><span class="sxs-lookup"><span data-stu-id="b2cba-110">Not secure.</span></span> <span data-ttu-id="b2cba-111">对 Reporting Services SOAP API 的调用不要求安全连接。</span><span class="sxs-lookup"><span data-stu-id="b2cba-111">Calls made to the Reporting Services SOAP API do not require a secure connection.</span></span>|  
|<span data-ttu-id="b2cba-112">大于“0” </span><span class="sxs-lookup"><span data-stu-id="b2cba-112">Greater than **0**</span></span>|<span data-ttu-id="b2cba-113">安全。</span><span class="sxs-lookup"><span data-stu-id="b2cba-113">Secure.</span></span> <span data-ttu-id="b2cba-114">对 Reporting Services SOAP API 所进行的所有调用都要求安全连接。</span><span class="sxs-lookup"><span data-stu-id="b2cba-114">All calls made to the Reporting Services SOAP API require a secure connection.</span></span>|  
  
 <span data-ttu-id="b2cba-115">可以使用 Web 服务的 <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> 方法返回根据报表服务器的当前配置要求安全连接的 Web 服务方法列表。</span><span class="sxs-lookup"><span data-stu-id="b2cba-115">You can use the <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> method of the Web service to return a list of Web service methods that require a secure connection according to the current configuration of the report server.</span></span> <span data-ttu-id="b2cba-116">在 SSL 方案中，应评估由 <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> 返回的方法列表，并根据所调用的方法将 Web 服务 URI 的架构名称更改为“https”或“http”。</span><span class="sxs-lookup"><span data-stu-id="b2cba-116">In an SSL scenario, you should evaluate the list of methods that are returned by <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> and change the scheme name of the Web service URI to "https" or "http" depending on the method being called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2cba-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2cba-117">See Also</span></span>  
 <span data-ttu-id="b2cba-118">[使用 Web 服务和 .NET Framework 生成应用程序](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="b2cba-118">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="b2cba-119">报表服务器 Web 服务</span><span class="sxs-lookup"><span data-stu-id="b2cba-119">Report Server Web Service</span></span>](../report-server-web-service.md)  
  
  
