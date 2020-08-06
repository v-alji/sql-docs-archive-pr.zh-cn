---
title: 实现安全扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
- forms-based authentication [Reporting Services]
- custom authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: d2327e7c-0d48-49e3-bcd9-3bba4e67a68b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e5cf1fa6ce0e0a02a52e6a27f693c152d1f97152
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587210"
---
# <a name="implementing-a-security-extension"></a><span data-ttu-id="b9f34-102">实现安全扩展插件</span><span class="sxs-lookup"><span data-stu-id="b9f34-102">Implementing a Security Extension</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="b9f34-103">Windows 身份验证是用于在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中保护报表安全性的主要系统。</span><span class="sxs-lookup"><span data-stu-id="b9f34-103">Windows Authentication is the primary system for securing reports in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="b9f34-104">然而，在某些情况下，您可能需要扩展 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 安全系统以适应企业中的自定义安全性。</span><span class="sxs-lookup"><span data-stu-id="b9f34-104">In certain cases, however, you may need to extend the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security system to accommodate custom security in your enterprise.</span></span> <span data-ttu-id="b9f34-105">为此，可以使用 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] API 提供的开发平台。</span><span class="sxs-lookup"><span data-stu-id="b9f34-105">You can do this using the development platform provided by the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] API.</span></span> <span data-ttu-id="b9f34-106">本节概述 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的安全扩展插件。</span><span class="sxs-lookup"><span data-stu-id="b9f34-106">This section will present an overview of security extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b9f34-107">有关实现、部署和删除 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 安全扩展插件的完整详细信息，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="b9f34-107">For complete details about implementing, deploying, and removing a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security extension, please see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9f34-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="b9f34-108">In This Section</span></span>  
 [<span data-ttu-id="b9f34-109">安全扩展插件概述</span><span class="sxs-lookup"><span data-stu-id="b9f34-109">Security Extensions Overview</span></span>](security-extensions-overview.md)  
 <span data-ttu-id="b9f34-110">提供有关 Reporting Services 安全扩展插件的概述。</span><span class="sxs-lookup"><span data-stu-id="b9f34-110">Provides an overview of Reporting Services Security Extensions.</span></span>  
  
 [<span data-ttu-id="b9f34-111">Reporting Services 中的身份验证</span><span class="sxs-lookup"><span data-stu-id="b9f34-111">Authentication in Reporting Services</span></span>](authentication-in-reporting-services.md)  
 <span data-ttu-id="b9f34-112">讨论 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的身份验证。</span><span class="sxs-lookup"><span data-stu-id="b9f34-112">Discusses authentication in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="b9f34-113">Reporting Services 中的授权</span><span class="sxs-lookup"><span data-stu-id="b9f34-113">Authorization in Reporting Services</span></span>](authorization-in-reporting-services.md)  
 <span data-ttu-id="b9f34-114">介绍 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的授权。</span><span class="sxs-lookup"><span data-stu-id="b9f34-114">Covers authorization in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9f34-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b9f34-115">See Also</span></span>  
 <xref:Microsoft.ReportingServices.Interfaces>   
 <span data-ttu-id="b9f34-116">[Reporting Services 扩展插件](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="b9f34-116">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="b9f34-117">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="b9f34-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
