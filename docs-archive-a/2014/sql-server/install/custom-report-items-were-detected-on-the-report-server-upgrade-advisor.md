---
title: " (Upgrade Advisor) Report Server 上检测到自定义报表项 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- custom report items, upgrading
ms.assetid: aee32006-65b2-4dfe-9570-d85a249d17b2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: feacf6aa6f233f85a67b43e7b72d3a50913991bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579963"
---
# <a name="custom-report-items-were-detected-on-the-report-server-upgrade-advisor"></a><span data-ttu-id="b6636-102">在报表服务器上检测到自定义报表项（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="b6636-102">Custom report items were detected on the report server (Upgrade Advisor)</span></span>
  <span data-ttu-id="b6636-103">为的早期版本创建的自定义报表项 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 与不兼容 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b6636-103">Custom report items that were created for previous releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] are not compatible with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="b6636-104">可以继续升级，但使用该自定义报表项的报表将不会按预期运行。</span><span class="sxs-lookup"><span data-stu-id="b6636-104">Upgrade can continue, but reports that use the custom report item will not run as expected.</span></span> <span data-ttu-id="b6636-105">升级顾问检测到了自定义报表项。</span><span class="sxs-lookup"><span data-stu-id="b6636-105">Upgrade Advisor detected custom report items.</span></span> <span data-ttu-id="b6636-106">可以继续升级，但您必须在升级完成后，手动将自定义报表项文件移到新的安装文件夹。</span><span class="sxs-lookup"><span data-stu-id="b6636-106">Upgrade can continue, but you must manually move the custom report item files to the new installation folder after upgrade completes.</span></span>  
  
||  
|-|  
|<span data-ttu-id="b6636-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="b6636-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="b6636-108">组件</span><span class="sxs-lookup"><span data-stu-id="b6636-108">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="b6636-109">说明</span><span class="sxs-lookup"><span data-stu-id="b6636-109">Description</span></span>  
 <span data-ttu-id="b6636-110">升级顾问在配置文件中检测到自定义 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 扩展插件设置，这指示安装中包含报表的一个或多个自定义程序集。</span><span class="sxs-lookup"><span data-stu-id="b6636-110">Upgrade Advisor detected custom [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] extension settings in the configuration files, indicating that your installation includes one or more custom assemblies for reports.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="b6636-111">纠正措施</span><span class="sxs-lookup"><span data-stu-id="b6636-111">Corrective Action</span></span>  
 <span data-ttu-id="b6636-112">在升级完成之后，手动将自定义报表项文件移到新的安装文件夹。</span><span class="sxs-lookup"><span data-stu-id="b6636-112">After upgrade completes, manually move the custom report item files to the new installation folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6636-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6636-113">See Also</span></span>  
 [<span data-ttu-id="b6636-114">升级顾问 &#40;Reporting Services 升级问题&#41;</span><span class="sxs-lookup"><span data-stu-id="b6636-114">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
