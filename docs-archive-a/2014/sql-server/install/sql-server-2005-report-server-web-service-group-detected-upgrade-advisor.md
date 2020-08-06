---
title: SQL Server 2005 (升级顾问) 检测到报表服务器 Web 服务组 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 70be2b9c4e7abd55daaa752830a73cbe6e222659
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694235"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a><span data-ttu-id="ee160-102">检测到 SQL Server 2005 报表服务器 Web 服务组（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="ee160-102">SQL Server 2005 Report Server Web Service group detected (Upgrade Advisor)</span></span>
  <span data-ttu-id="ee160-103">升级顾问检测到该 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例与 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 报表服务器 Web 服务组关联。</span><span class="sxs-lookup"><span data-stu-id="ee160-103">Upgrade Advisor detected that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is associated with a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Report Server Web service group.</span></span>  
  
||  
|-|  
|<span data-ttu-id="ee160-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式。</span><span class="sxs-lookup"><span data-stu-id="ee160-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="ee160-105">组件</span><span class="sxs-lookup"><span data-stu-id="ee160-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="ee160-106">说明</span><span class="sxs-lookup"><span data-stu-id="ee160-106">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="ee160-107">不 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]报表服务器 Web 服务组。</span><span class="sxs-lookup"><span data-stu-id="ee160-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not use the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Report Server Web service group.</span></span> <span data-ttu-id="ee160-108">从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 时，将删除此服务组，并且在升级期间不保留此组的自定义访问控制列表 (ACL) 或属于此组的用户。</span><span class="sxs-lookup"><span data-stu-id="ee160-108">When you upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this service group is deleted and custom Access Control Lists (ACLs) for this group or users who belong to the group are not retained during the upgrade.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="ee160-109">纠正措施</span><span class="sxs-lookup"><span data-stu-id="ee160-109">Corrective Action</span></span>  
 <span data-ttu-id="ee160-110">在升级之前，请备份任何自定义 ACL 或属于 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 报表服务器 Web 服务组的用户。</span><span class="sxs-lookup"><span data-stu-id="ee160-110">Before you upgrade, back up any custom ACLs or users who belong to the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Report Server Web service group.</span></span> <span data-ttu-id="ee160-111">为此，你可以在 sp2 和更高版本中使用**Icacls.exe**命令行工具， [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 或在 Sp2 之前的 Windows 操作系统中使用 Cacls.exe 命令行工具 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ee160-111">To do this, you can use the **Icacls.exe** command-line tool in [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 and later or the Cacls.exe command-line tool in Windows operating systems prior to [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2.</span></span> <span data-ttu-id="ee160-112">有关这些工具的语法的详细信息，请参阅 Windows 产品文档。</span><span class="sxs-lookup"><span data-stu-id="ee160-112">For more information about the syntax for these tools, see the Windows product documentation.</span></span> <span data-ttu-id="ee160-113">在安装程序成功完成之后，请对报表服务器实例的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 报表服务器 Windows 组应用自定义 ACL 或用户。</span><span class="sxs-lookup"><span data-stu-id="ee160-113">After setup successfully completes, apply the custom ACLs or users to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Report Server Windows group for your report server instance.</span></span> <span data-ttu-id="ee160-114">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]报表服务器 Windows 组采用 SQLServerReportServerUser $ 的形式 \<*computer_name*> $ \<*instance_name*> 。</span><span class="sxs-lookup"><span data-stu-id="ee160-114">The [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Report Server Windows group takes the form of SQLServerReportServerUser$\<*computer_name*>$\<*instance_name*>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee160-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee160-115">See Also</span></span>  
 [<span data-ttu-id="ee160-116">升级顾问 &#40;Reporting Services 升级问题&#41;</span><span class="sxs-lookup"><span data-stu-id="ee160-116">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
