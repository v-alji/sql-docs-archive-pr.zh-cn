---
title: 使用 Reporting Services SOAP 标头 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- SOAP headers [Reporting Services]
- SOAP [Reporting Services], headers
- XML Web service [Reporting Services], SOAP
ms.assetid: 306d2c06-a25a-40f8-8a35-13dd32e8841e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f48be183398d4d441b5781c9f9467178c3011e32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690352"
---
# <a name="using-reporting-services-soap-headers"></a><span data-ttu-id="d4c32-102">使用 Reporting Services SOAP 标头</span><span class="sxs-lookup"><span data-stu-id="d4c32-102">Using Reporting Services SOAP Headers</span></span>
  <span data-ttu-id="d4c32-103">使用 SOAP 与 Web 服务方法的通信遵循标准的格式。</span><span class="sxs-lookup"><span data-stu-id="d4c32-103">Communication with a Web service method using SOAP follows a standard format.</span></span> <span data-ttu-id="d4c32-104">此格式中的部分内容为在 XML 文档中编码的数据。</span><span class="sxs-lookup"><span data-stu-id="d4c32-104">Part of this format is the data that is encoded in an XML document.</span></span> <span data-ttu-id="d4c32-105">XML 文档由根 Envelope 元素组成，而根 Envelope 元素又由必需的 Body 元素和可选的 Header 元素组成\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d4c32-105">The XML document consists of a root **Envelope** element, which in turn consists of a required **Body** element and an optional **Header** element.</span></span> <span data-ttu-id="d4c32-106">Body 元素包含特定于相应消息的数据\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d4c32-106">The **Body** element contains the data specific to the message.</span></span> <span data-ttu-id="d4c32-107">可选的 Header 元素包含与特定消息并不直接相关的其他信息\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d4c32-107">The optional **Header** element can contain additional information not directly related to the particular message.</span></span> <span data-ttu-id="d4c32-108">Header 元素的每一子元素都称为 SOAP 标头\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d4c32-108">Each child element of the **Header** element is called a SOAP header.</span></span>  
  
 <span data-ttu-id="d4c32-109">尽管 SOAP 标头可以包含与相应消息相关的数据，但是一般而言， SOAP 标头包含的是 Web 服务器基础结构所处理的信息。</span><span class="sxs-lookup"><span data-stu-id="d4c32-109">Although the SOAP headers can contain data related to the message, they typically contain information processed by the Web server infrastructure.</span></span>  
  
 <span data-ttu-id="d4c32-110">报表服务器 Web 服务定义几个可在 SOAP 标头中使用的类：<xref:ReportService2005.BatchHeader>、<xref:ReportService2010.ItemNamespaceHeader>、<xref:ReportService2010.ServerInfoHeader>、<xref:ReportService2010.TrustedUserHeader> 和 <xref:ReportExecution2005.ExecutionHeader>。</span><span class="sxs-lookup"><span data-stu-id="d4c32-110">The Report Server Web services define several classes for use in the SOAP header: <xref:ReportService2005.BatchHeader>, <xref:ReportService2010.ItemNamespaceHeader>, <xref:ReportService2010.ServerInfoHeader>, <xref:ReportService2010.TrustedUserHeader>, and <xref:ReportExecution2005.ExecutionHeader>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4c32-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="d4c32-111">In This Section</span></span>  
  
|<span data-ttu-id="d4c32-112">主题</span><span class="sxs-lookup"><span data-stu-id="d4c32-112">Topic</span></span>|<span data-ttu-id="d4c32-113">说明</span><span class="sxs-lookup"><span data-stu-id="d4c32-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d4c32-114">批处理方法</span><span class="sxs-lookup"><span data-stu-id="d4c32-114">Batching Methods</span></span>](batching-methods.md)|<span data-ttu-id="d4c32-115">介绍如何使用 <xref:ReportService2005.BatchHeader> 将多个操作纳入一个事务中进行批处理。</span><span class="sxs-lookup"><span data-stu-id="d4c32-115">Describes how to batch multiple operations into a single transaction using <xref:ReportService2005.BatchHeader>.</span></span>|  
|[<span data-ttu-id="d4c32-116">标识执行状态</span><span class="sxs-lookup"><span data-stu-id="d4c32-116">Identifying Execution State</span></span>](identifying-execution-state.md)|<span data-ttu-id="d4c32-117">介绍如何使用 SessionHeader 管理 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的会话状态\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d4c32-117">Describes how to manage session state in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] using **SessionHeader**.</span></span>|  
|[<span data-ttu-id="d4c32-118">为 GetProperties 方法设置项命名空间</span><span class="sxs-lookup"><span data-stu-id="d4c32-118">Setting the Item Namespace for the GetProperties Method</span></span>](setting-the-item-namespace-for-the-getproperties-method.md)|<span data-ttu-id="d4c32-119">介绍如何通过使用 <xref:ReportService2010.ReportingService2010.GetProperties%2A> 方法和 <xref:ReportService2010.ItemNamespaceHeader> SOAP 标头来根据项的路径或 ID 检索属性。</span><span class="sxs-lookup"><span data-stu-id="d4c32-119">Describes how to retrieve properties based on either the path or the ID of an item by using the <xref:ReportService2010.ReportingService2010.GetProperties%2A> method and the <xref:ReportService2010.ItemNamespaceHeader> SOAP header.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4c32-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4c32-120">See Also</span></span>  
 <span data-ttu-id="d4c32-121">[使用 Web 服务和 .NET Framework 生成应用程序](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="d4c32-121">[Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="d4c32-122">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="d4c32-122">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
