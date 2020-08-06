---
title: " (Upgrade Advisor) Report Server 网站上的客户端证书 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 5ecce26b-99df-4109-8e51-d150d369dff7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 563a64e695ef552a712a5678f56d38fdfbff619f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586206"
---
# <a name="client-certificates-on-the-report-server-web-site-upgrade-advisor"></a><span data-ttu-id="d155d-102">报表服务器网站上的客户端证书（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="d155d-102">Client certificates on the report server web site (Upgrade Advisor)</span></span>
  <span data-ttu-id="d155d-103">升级顾问已检测到承载报表服务器或报表管理器虚拟目录的 IIS 网站存在一个或多个客户端证书。</span><span class="sxs-lookup"><span data-stu-id="d155d-103">Upgrade Advisor detected one or more client certificates on the IIS Web site that hosts the report server or Report Manager virtual directories.</span></span>  
  
||  
|-|  
|<span data-ttu-id="d155d-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式。</span><span class="sxs-lookup"><span data-stu-id="d155d-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="d155d-105">组件</span><span class="sxs-lookup"><span data-stu-id="d155d-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="d155d-106">说明</span><span class="sxs-lookup"><span data-stu-id="d155d-106">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="d155d-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]不支持使用客户端证书对用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d155d-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not support the use of client certificates to authenticate users.</span></span> <span data-ttu-id="d155d-108">可以继续升级，但升级后的报表服务器将不使用客户端证书。</span><span class="sxs-lookup"><span data-stu-id="d155d-108">Upgrade can continue, but client certificates will not be used by the upgraded report server.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="d155d-109">纠正措施</span><span class="sxs-lookup"><span data-stu-id="d155d-109">Corrective Action</span></span>  
 <span data-ttu-id="d155d-110">必须使用单独的解决方案（如 ISA Server）以确保满足任何客户端证书身份验证要求。</span><span class="sxs-lookup"><span data-stu-id="d155d-110">You will have to use a separate solution such as ISA Server to ensure any client certificate authentication requirements are addressed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d155d-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d155d-111">See Also</span></span>  
 [<span data-ttu-id="d155d-112">升级顾问 &#40;Reporting Services 升级问题&#41;</span><span class="sxs-lookup"><span data-stu-id="d155d-112">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
