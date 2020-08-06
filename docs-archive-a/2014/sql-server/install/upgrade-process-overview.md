---
title: 升级过程概述 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server
- Upgrade Advisor [SQL Server], process description
- SQL Server Upgrade Advisor, process description
- upgrade process [Upgrade Advisor]
ms.assetid: f77ffbab-a195-4124-acce-9c538f7ca9ce
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5da6dc3b3e6d6c7058193801100bf2552bfde7cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694225"
---
# <a name="upgrade-process-overview"></a><span data-ttu-id="15a95-102">升级过程概述</span><span class="sxs-lookup"><span data-stu-id="15a95-102">Upgrade Process Overview</span></span>
  <span data-ttu-id="15a95-103">本主题提供了 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 升级顾问的最佳实践信息并概括介绍了升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的推荐过程。</span><span class="sxs-lookup"><span data-stu-id="15a95-103">This topic provides best practice information for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor and a summary of the recommended process for upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="upgrade-process"></a><span data-ttu-id="15a95-104">升级过程</span><span class="sxs-lookup"><span data-stu-id="15a95-104">Upgrade Process</span></span>  
 <span data-ttu-id="15a95-105">运行 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 的服务器可升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="15a95-105">Servers that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] can be upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="15a95-106">有些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件可以就地升级，其他组件则必须迁移，并且仍然有一些其他组件已被新的组件取代。</span><span class="sxs-lookup"><span data-stu-id="15a95-106">Whereas some [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components can be upgraded in place, others must be migrated, and still others have been superseded by new components.</span></span> <span data-ttu-id="15a95-107">例如，从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 开始，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) 便取代了 Data Transformation Services (DTS)，并且 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中不再支持 DTS。</span><span class="sxs-lookup"><span data-stu-id="15a95-107">For example, starting with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) supersedes Data Transformation Services (DTS), and DTS is no longer supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="15a95-108">当设计升级计划时，您可能需要计划将当前 DTS 包升级为 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="15a95-108">When you formulate your upgrade plan, you might need to plan for updating your current DTS packages to [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages.</span></span>  
  
 <span data-ttu-id="15a95-109">利用升级顾问，可以对当前 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装、组件和相关文件进行评估，以便识别在升级或迁移到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的过程中及其后会导致问题的已知问题。</span><span class="sxs-lookup"><span data-stu-id="15a95-109">Upgrade Advisor enables you to evaluate current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations, components, and related files to identify known issues that will cause problems both during and after you upgrade or migrate to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="15a95-110">其中一些已知问题会阻止 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 升级。</span><span class="sxs-lookup"><span data-stu-id="15a95-110">A few of these known issues block the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] upgrade.</span></span> <span data-ttu-id="15a95-111">在升级顾问的报表中，这些问题被标识为“阻止升级的问题”。</span><span class="sxs-lookup"><span data-stu-id="15a95-111">In the Upgrade Advisor report, these issues are identified as Upgrade Blockers.</span></span> <span data-ttu-id="15a95-112">如果在运行安装程序前未解决阻止升级的问题，[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装程序将退出并建议您运行升级顾问以找出妨碍升级的特定问题。</span><span class="sxs-lookup"><span data-stu-id="15a95-112">If you have not addressed the Upgrade Blockers before you run Setup, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup exits and recommends that you run Upgrade Advisor to identify the specific issues that are blocking the upgrade.</span></span>  
  
 <span data-ttu-id="15a95-113">作为一种最佳做法，在升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之前，我们建议您备份数据和系统设置，并且按照为组织机构定义的操作指南中概括的关键步骤进行操作。</span><span class="sxs-lookup"><span data-stu-id="15a95-113">As a best practice before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you back up your data and system settings, and take strategic steps as outlined in the operational guidelines defined for your organization.</span></span> <span data-ttu-id="15a95-114">使用以下步骤完成升级：</span><span class="sxs-lookup"><span data-stu-id="15a95-114">Use the following steps to complete the upgrade:</span></span>  
  
1.  <span data-ttu-id="15a95-115">阅读 [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="15a95-115">Review [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="15a95-116">备份数据和系统设置。</span><span class="sxs-lookup"><span data-stu-id="15a95-116">Back up data and system settings.</span></span>  
  
3.  <span data-ttu-id="15a95-117">运行升级顾问。</span><span class="sxs-lookup"><span data-stu-id="15a95-117">Run Upgrade Advisor.</span></span>  
  
     <span data-ttu-id="15a95-118">升级顾问不修改计算机中的数据或更改计算机中的设置。</span><span class="sxs-lookup"><span data-stu-id="15a95-118">Upgrade Advisor does not modify your data or change settings on your computer.</span></span>  
  
4.  <span data-ttu-id="15a95-119">查看升级顾问报告中标识的问题。</span><span class="sxs-lookup"><span data-stu-id="15a95-119">Review the issues identified in the Upgrade Advisor report.</span></span>  
  
5.  <span data-ttu-id="15a95-120">解决任何妨碍您升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的问题。</span><span class="sxs-lookup"><span data-stu-id="15a95-120">Resolve any blocking issues that would prevent you from upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
6.  <span data-ttu-id="15a95-121">解决所有其他升级前的问题。</span><span class="sxs-lookup"><span data-stu-id="15a95-121">Resolve any other pre-upgrade issues.</span></span>  
  
7.  <span data-ttu-id="15a95-122">运行升级顾问以确认所有已知问题均以解决。</span><span class="sxs-lookup"><span data-stu-id="15a95-122">Run Upgrade Advisor to verify that all known issues have been addressed.</span></span>  
  
8.  <span data-ttu-id="15a95-123">运行 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装程序。</span><span class="sxs-lookup"><span data-stu-id="15a95-123">Run [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup.</span></span>  
  
9. <span data-ttu-id="15a95-124">解决所有升级后的问题和迁移问题。</span><span class="sxs-lookup"><span data-stu-id="15a95-124">Resolve any post-upgrade and migration issues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a95-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15a95-125">See Also</span></span>  
 <span data-ttu-id="15a95-126">[&#40;用户界面运行升级顾问&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span><span class="sxs-lookup"><span data-stu-id="15a95-126">[Running Upgrade Advisor &#40;User Interface&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span></span>  
 <span data-ttu-id="15a95-127">[使用报表](../../../2014/sql-server/install/using-reports.md) </span><span class="sxs-lookup"><span data-stu-id="15a95-127">[Using Reports](../../../2014/sql-server/install/using-reports.md) </span></span>  
 [<span data-ttu-id="15a95-128">使用升级顾问</span><span class="sxs-lookup"><span data-stu-id="15a95-128">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
