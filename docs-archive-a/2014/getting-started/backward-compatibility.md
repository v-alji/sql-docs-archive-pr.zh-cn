---
title: 向后兼容性 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Surface Area Configuration Tool
- command prompt [SQL Server], discontinued parameters
- discontinued functionality [SQL Server]
- compatibility [SQL Server], discontinued features
- SAC tool
- compatibility [Analysis Services]
- compatibility [Integration Services]
- SQL Server, discontinued features
- compatibility [Replication]
- compatibility [SQL Server]
- previous versions [SQL Server], (See also backward compatibility)
- backward compatibility [SQL Server]
- compatibility [Reporting Services]
- earlier versions [SQL Server], (See also backward compatibility)
ms.assetid: 15d9117e-e2fa-4985-99ea-66a117c1e9fd
author: rothja
ms.author: jroth
ms.openlocfilehash: fd8be66efd648f5b6703a76855a549a9bd30f1e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591510"
---
# <a name="backward-compatibility"></a><span data-ttu-id="bf9c1-102">Backward Compatibility</span><span class="sxs-lookup"><span data-stu-id="bf9c1-102">Backward Compatibility</span></span>
  <span data-ttu-id="bf9c1-103">下列各节包含 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 组件的向后兼容信息。</span><span class="sxs-lookup"><span data-stu-id="bf9c1-103">The following sections contain backward compatibility information for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="bf9c1-104">本内容包括有关不推荐使用的功能、废止的功能、重大更改和行为更改的信息。</span><span class="sxs-lookup"><span data-stu-id="bf9c1-104">This content includes information about deprecated features, discontinued features, breaking changes, and behavior changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bf9c1-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="bf9c1-105">In This Section</span></span>  
  
|<span data-ttu-id="bf9c1-106">主题</span><span class="sxs-lookup"><span data-stu-id="bf9c1-106">Topic</span></span>|<span data-ttu-id="bf9c1-107">说明</span><span class="sxs-lookup"><span data-stu-id="bf9c1-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="bf9c1-108">SQL Server 的向后兼容性</span><span class="sxs-lookup"><span data-stu-id="bf9c1-108">SQL Server Backward Compatibility</span></span>](../../2014/getting-started/sql-server-backward-compatibility.md)|<span data-ttu-id="bf9c1-109">包含介绍 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中的更改的一些主题，这些更改可能会要求您更改应用程序。</span><span class="sxs-lookup"><span data-stu-id="bf9c1-109">Contains topics that describe changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your applications.</span></span> <span data-ttu-id="bf9c1-110">本主题范围中包含的功能包括数据可编程性、外围应用配置器工具、安装程序、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服务，以及其他多种功能更改。</span><span class="sxs-lookup"><span data-stu-id="bf9c1-110">Features that are included in this topic area include data programmability, surface area configuration tools, Setup, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services, and other broad functionality changes.</span></span>|  
|[<span data-ttu-id="bf9c1-111">SQL Server 数据库引擎的向后兼容性</span><span class="sxs-lookup"><span data-stu-id="bf9c1-111">SQL Server Database Engine Backward Compatibility</span></span>](../database-engine/sql-server-database-engine-backward-compatibility.md)|<span data-ttu-id="bf9c1-112">包含介绍 [!INCLUDE[ssDE](../includes/ssde-md.md)] 中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 更改的一些主题，这些更改可能会要求您更改应用程序。</span><span class="sxs-lookup"><span data-stu-id="bf9c1-112">Contains topics that describe [!INCLUDE[ssDE](../includes/ssde-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your applications.</span></span>|  
|[<span data-ttu-id="bf9c1-113">Analysis Services 向后兼容性</span><span class="sxs-lookup"><span data-stu-id="bf9c1-113">Analysis Services Backward Compatibility</span></span>](../../2014/analysis-services/analysis-services-backward-compatibility.md)|<span data-ttu-id="bf9c1-114">包含介绍 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 更改的一些主题，这些更改可能会要求您更改应用程序。</span><span class="sxs-lookup"><span data-stu-id="bf9c1-114">Contains topics that describe [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your applications.</span></span>|  
|[<span data-ttu-id="bf9c1-115">Integration Services 的向后兼容性</span><span class="sxs-lookup"><span data-stu-id="bf9c1-115">Integration Services Backward Compatibility</span></span>](../integration-services/integration-services-backward-compatibility.md)|<span data-ttu-id="bf9c1-116">介绍 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 更改，这些更改可能会要求您更改现有 Data Transformation Services 应用程序。</span><span class="sxs-lookup"><span data-stu-id="bf9c1-116">Describes [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your existing Data Transformation Services applications.</span></span>|  
|[<span data-ttu-id="bf9c1-117">Reporting Services 后向兼容性</span><span class="sxs-lookup"><span data-stu-id="bf9c1-117">Reporting Services Backward Compatibility</span></span>](../reporting-services/reporting-services-backward-compatibility.md)|<span data-ttu-id="bf9c1-118">包含介绍 [!INCLUDE[ssRS](../includes/ssrs.md)] 中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 更改的一些主题，这些更改可能会要求您更改现有 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 解决方案。</span><span class="sxs-lookup"><span data-stu-id="bf9c1-118">Contains topics that describe [!INCLUDE[ssRS](../includes/ssrs.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your existing [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] solutions.</span></span>|  
|[<span data-ttu-id="bf9c1-119">向后兼容性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bf9c1-119">Backward Compatibility &#40;Master Data Services&#41;</span></span>](../master-data-services/backward-compatibility-master-data-services.md)|<span data-ttu-id="bf9c1-120">包含介绍 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 更改的一些主题，这些更改可能会要求您更改现有 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 解决方案。</span><span class="sxs-lookup"><span data-stu-id="bf9c1-120">Contains topics that describe [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your existing [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] solutions.</span></span>|  
|[<span data-ttu-id="bf9c1-121">复制的向后兼容性</span><span class="sxs-lookup"><span data-stu-id="bf9c1-121">Replication Backward Compatibility</span></span>](../../2014/relational-databases/replication/replication-backward-compatibility.md)|<span data-ttu-id="bf9c1-122">包含介绍 [!INCLUDE[ssDE](../includes/ssde-md.md)] 中的[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]更改的一些主题，这些更改可能会要求您更改现有复制解决方案。</span><span class="sxs-lookup"><span data-stu-id="bf9c1-122">Contains topics that describe [!INCLUDE[ssDE](../includes/ssde-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to existing Replication solutions.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf9c1-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf9c1-123">See Also</span></span>  
 <span data-ttu-id="bf9c1-124">[安装 SQL Server 2014](../database-engine/install-windows/install-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bf9c1-124">[Install SQL Server 2014](../database-engine/install-windows/install-sql-server.md) </span></span>  
 [<span data-ttu-id="bf9c1-125">升级到 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="bf9c1-125">Upgrade to SQL Server 2014</span></span>](../database-engine/install-windows/upgrade-sql-server.md)  
  
  
