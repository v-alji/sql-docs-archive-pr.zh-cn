---
title: 虚拟目录具有 (升级顾问) 的不支持的身份验证方法 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 216eca6f-9a66-42e1-aa54-dcf99cec9f7d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 67b1c027b8ed020f65fdea7c093f6d5454f02c5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586105"
---
# <a name="virtual-directory-has-unsupported-authentication-method-upgrade-advisor"></a><span data-ttu-id="b183e-102">虚拟目录包含不支持的身份验证方法（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="b183e-102">Virtual directory has unsupported authentication method (Upgrade Advisor)</span></span>
  <span data-ttu-id="b183e-103">升级顾问检测到报表管理器或报表服务器虚拟目录上存在不支持的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="b183e-103">Upgrade Advisor detected an unsupported authentication method on the Report Manager or report server virtual directory.</span></span> <span data-ttu-id="b183e-104">升级不支持的身份验证方法包括匿名、摘要式和 .NET Passport 身份验证。</span><span class="sxs-lookup"><span data-stu-id="b183e-104">Authentication methods that are not supported by upgrade include Anonymous, Digest, and .NET Passport.</span></span>  
  
||  
|-|  
|<span data-ttu-id="b183e-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式。</span><span class="sxs-lookup"><span data-stu-id="b183e-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="b183e-106">组件</span><span class="sxs-lookup"><span data-stu-id="b183e-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="b183e-107">说明</span><span class="sxs-lookup"><span data-stu-id="b183e-107">Description</span></span>  
 <span data-ttu-id="b183e-108">安装程序不能升级使用以下身份验证方法之一的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 系统</span><span class="sxs-lookup"><span data-stu-id="b183e-108">Setup cannot upgrade a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation that uses one of the following authentication methods</span></span>  
  
-   <span data-ttu-id="b183e-109">匿名</span><span class="sxs-lookup"><span data-stu-id="b183e-109">Anonymous</span></span>  
  
-   <span data-ttu-id="b183e-110">摘要</span><span class="sxs-lookup"><span data-stu-id="b183e-110">Digest</span></span>  
  
-   <span data-ttu-id="b183e-111">.NET Passport</span><span class="sxs-lookup"><span data-stu-id="b183e-111">.NET Passport</span></span>  
  
 <span data-ttu-id="b183e-112">若要继续，可以修改在 Internet Information Services (IIS) 中为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 虚拟目录指定的身份验证方法，也可以迁移您的安装。</span><span class="sxs-lookup"><span data-stu-id="b183e-112">To continue, you can either modify the Authentication method that is specified for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] virtual directories in Internet Information Services (IIS), or you can migrate your installation.</span></span> <span data-ttu-id="b183e-113">有关迁移安装的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="b183e-113">For more information about migrating your installation, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="b183e-114">纠正措施</span><span class="sxs-lookup"><span data-stu-id="b183e-114">Corrective Action</span></span>  
 <span data-ttu-id="b183e-115">若要继续升级，请在 IIS 中修改 ReportServer 和 Reports 虚拟目录的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="b183e-115">To continue with upgrade, modify the Authentication method in IIS for the ReportServer and Reports virtual directories.</span></span> <span data-ttu-id="b183e-116">有关在 IIS 中修改身份验证方法的详细信息，请参阅 IIS 文档。</span><span class="sxs-lookup"><span data-stu-id="b183e-116">For more information about modifying Authentication methods in IIS, see the IIS documentation.</span></span> <span data-ttu-id="b183e-117">在修改 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 虚拟目录的身份验证方法之后，请重新运行升级顾问以确认没有其他升级问题。</span><span class="sxs-lookup"><span data-stu-id="b183e-117">After you modify the Authentication method for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] virtual directories, re-run Upgrade Advisor to confirm that there are no other upgrade issues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b183e-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b183e-118">See Also</span></span>  
 [<span data-ttu-id="b183e-119">升级顾问 &#40;Reporting Services 升级问题&#41;</span><span class="sxs-lookup"><span data-stu-id="b183e-119">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
