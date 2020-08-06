---
title: 调用 Web 服务方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Web service [Reporting Services], calls
- calling Web service
- Report Server Web service, SOAP
- XML Web service [Reporting Services], calls
- Report Server Web service, calls
- XML Web service [Reporting Services], SOAP
- SOAP [Reporting Services], calls
ms.assetid: f6f0c6e3-8bb5-4c44-9d19-1872edc72746
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 87f1485b4e3c0ed064e42bb3b411fece96eba8d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688544"
---
# <a name="calling-web-service-methods"></a><span data-ttu-id="13ce8-102">调用 Web 服务方法</span><span class="sxs-lookup"><span data-stu-id="13ce8-102">Calling Web Service Methods</span></span>
  <span data-ttu-id="13ce8-103">使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 代理类调用 Web 服务操作时，可以通过使用该类的方法来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="13ce8-103">When you use a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] proxy class to call Web service operations, you do so by using the methods of that class.</span></span> <span data-ttu-id="13ce8-104">这些方法的响应方式类似于 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 类库中类的任何其他方法。</span><span class="sxs-lookup"><span data-stu-id="13ce8-104">These methods respond like any other method of a class in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library.</span></span> <span data-ttu-id="13ce8-105">所有 Web 服务方法都具有公共访问，并要求您提供适当数量的参数和参数类型。</span><span class="sxs-lookup"><span data-stu-id="13ce8-105">All Web service methods have public access and require you to supply the appropriate number of arguments and argument types.</span></span> <span data-ttu-id="13ce8-106">在项目中创建代理类的实例之后，您可以调用方法以通过报表服务器执行报表操作。</span><span class="sxs-lookup"><span data-stu-id="13ce8-106">After you have created an instance of the proxy class in your project, you can call the methods to perform reporting operations via the report server.</span></span> <span data-ttu-id="13ce8-107">以下 C# 代码说明如何使用 <xref:ReportService2010.ReportingService2010> 代理类的 <xref:ReportService2010.ReportingService2010.ListChildren%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="13ce8-107">The following C# code illustrates the use of the <xref:ReportService2010.ReportingService2010.ListChildren%2A> method of the <xref:ReportService2010.ReportingService2010> proxy class.</span></span> <span data-ttu-id="13ce8-108">此代码用于对返回 <xref:ReportService2010.CatalogItem> 对象数组（此数组包含报表服务器数据库中所有项的列表）的 Web 服务进行递归调用：</span><span class="sxs-lookup"><span data-stu-id="13ce8-108">The code is used to make a recursive call to the Web service that returns an array of <xref:ReportService2010.CatalogItem> objects that contains a list of all items in the report server database:</span></span>  
  
```vb  
Dim rs As New ReportingService2010()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
Dim items As CatalogItem() = rs.ListChildren("/", True)  
```  
  
```csharp  
ReportingService2010 rs = new ReportingService2010();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
CatalogItem[] items = rs.ListChildren("/", true);  
```  
  
## <a name="see-also"></a><span data-ttu-id="13ce8-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13ce8-109">See Also</span></span>  
 <span data-ttu-id="13ce8-110">[使用 Web 服务和 .NET Framework 生成应用程序](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="13ce8-110">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="13ce8-111">[报表服务器 Web 服务](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="13ce8-111">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="13ce8-112">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="13ce8-112">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
