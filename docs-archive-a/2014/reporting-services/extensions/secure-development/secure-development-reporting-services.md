---
title: 安全开发 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- development security [Reporting Services]
- security [Reporting Services], development
- security [Reporting Services], strategies
ms.assetid: 12161a6c-b93b-4312-9d27-0c922561eb9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7ba284b9013c5da6b03cce06ec72deccb045cfad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591765"
---
# <a name="secure-development-reporting-services"></a><span data-ttu-id="bdc1c-102">安全开发 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="bdc1c-102">Secure Development (Reporting Services)</span></span>
  <span data-ttu-id="bdc1c-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 提供了一个功能强大的安全系统，该系统可以在一个受到严格约束并由管理员定义的安全上下文中运行代码。</span><span class="sxs-lookup"><span data-stu-id="bdc1c-103">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides a robust security system that can run code in tightly constrained, administrator-defined security contexts.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="bdc1c-104">使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 安全系统，该系统也称为“代码访问安全”（或“基于证据的安全”）。</span><span class="sxs-lookup"><span data-stu-id="bdc1c-104">uses the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] security system, known as code access security (or evidence-based security).</span></span> <span data-ttu-id="bdc1c-105">对于代码访问安全性，可以信任用户访问某个资源，但是如果用户执行的代码不受信任，则会拒绝其访问该资源。</span><span class="sxs-lookup"><span data-stu-id="bdc1c-105">Under code access security, a user may be trusted to access a resource, but if the code the user executes is not trusted, access to the resource will be denied.</span></span>  
  
 <span data-ttu-id="bdc1c-106">基于代码而不是基于特定用户的安全性允许表达您为 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 开发的自定义程序集或数据、传递、呈现和安全扩展插件的安全性。</span><span class="sxs-lookup"><span data-stu-id="bdc1c-106">Security based on code, as opposed to specific users, permits security to be expressed for custom assemblies or data, delivery, rendering, and security extensions that you develop for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="bdc1c-107">您的扩展代码可由任何数量的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 用户执行，所有这些用户在开发时都是未知的。</span><span class="sxs-lookup"><span data-stu-id="bdc1c-107">Your extension code may be executed by any number of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] users, all of whom are unknown at development time.</span></span> <span data-ttu-id="bdc1c-108">您开发的自定义程序集或扩展插件需要 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的特定安全策略。</span><span class="sxs-lookup"><span data-stu-id="bdc1c-108">The custom assemblies or extensions that you develop require specific security policies in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="bdc1c-109">这些安全策略在 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中表示为类型。</span><span class="sxs-lookup"><span data-stu-id="bdc1c-109">These security policies are represented as types in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="bdc1c-110">有关代码访问安全性的详细信息，请参阅 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 文档中的“代码访问安全性”。</span><span class="sxs-lookup"><span data-stu-id="bdc1c-110">For a more information about code access security, see "Code Access Security" in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] documentation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bdc1c-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="bdc1c-111">In This Section</span></span>  
 [<span data-ttu-id="bdc1c-112">Reporting Services 中的代码访问安全性</span><span class="sxs-lookup"><span data-stu-id="bdc1c-112">Code Access Security in Reporting Services</span></span>](code-access-security-in-reporting-services.md)  
 <span data-ttu-id="bdc1c-113">介绍针对 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的自定义程序集和扩展插件的代码访问安全性和策略配置。</span><span class="sxs-lookup"><span data-stu-id="bdc1c-113">Introduces code access security and policy configuration for custom assemblies and extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="bdc1c-114">了解安全策略</span><span class="sxs-lookup"><span data-stu-id="bdc1c-114">Understanding Security Policies</span></span>](understanding-security-policies.md)  
 <span data-ttu-id="bdc1c-115">介绍 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的各种程序集类型以及代码访问安全性如何影响代码权限。</span><span class="sxs-lookup"><span data-stu-id="bdc1c-115">Describes the various assembly types in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] and how code access security affects code permissions.</span></span>  
  
 [<span data-ttu-id="bdc1c-116">使用 Reporting Services 安全策略文件</span><span class="sxs-lookup"><span data-stu-id="bdc1c-116">Using Reporting Services Security Policy Files</span></span>](using-reporting-services-security-policy-files.md)  
 <span data-ttu-id="bdc1c-117">介绍不同的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 组件和相应的策略配置文件。</span><span class="sxs-lookup"><span data-stu-id="bdc1c-117">Describes the different [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] components and the corresponding policy configuration files.</span></span>  
  
  
