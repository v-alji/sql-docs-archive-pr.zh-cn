---
title: " (升级顾问) ，未配置报表服务器数据库 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: b964300c-b220-4244-9fa6-c0c6a57760f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 072e689da3f43222396f071e607214a2ec494749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577235"
---
# <a name="report-server-database-is-not-configured-upgrade-advisor"></a><span data-ttu-id="81d91-102">未配置报表服务器数据库（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="81d91-102">Report server database is not configured (Upgrade Advisor)</span></span>
  <span data-ttu-id="81d91-103">升级因报表服务器配置不完整而受阻。</span><span class="sxs-lookup"><span data-stu-id="81d91-103">Upgrade is blocked due to an incomplete report server configuration.</span></span> <span data-ttu-id="81d91-104">未配置报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="81d91-104">The report server database is not configured.</span></span>  
  
||  
|-|  
|<span data-ttu-id="81d91-105">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="81d91-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="81d91-106">组件</span><span class="sxs-lookup"><span data-stu-id="81d91-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="81d91-107">说明</span><span class="sxs-lookup"><span data-stu-id="81d91-107">Description</span></span>  
 <span data-ttu-id="81d91-108">安装程序只能升级完全配置的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="81d91-108">Setup can only upgrade a fully configured report server instance.</span></span> <span data-ttu-id="81d91-109">若要继续，必须配置 Report Server 数据库，或使用 Microsoft Windows **"控制面板**" 从安装中删除 Report Server 功能 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="81d91-109">To continue, you must either configure the report server database, or use Microsoft Windows **Control Panel** to remove the report server feature from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="81d91-110">删除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 后，便可升级其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件。</span><span class="sxs-lookup"><span data-stu-id="81d91-110">After you remove [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can upgrade other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="81d91-111">纠正措施</span><span class="sxs-lookup"><span data-stu-id="81d91-111">Corrective Action</span></span>  
 <span data-ttu-id="81d91-112">如果尚未配置报表服务器数据库，报表服务器将无法运行，应在升级前将其删除。</span><span class="sxs-lookup"><span data-stu-id="81d91-112">If you did not configure the report server database, the report server is not operational and should be removed prior to upgrade.</span></span>  
  
 <span data-ttu-id="81d91-113">有关卸载的其他信息 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，请参阅[卸载 Reporting Services 2012](https://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\))。</span><span class="sxs-lookup"><span data-stu-id="81d91-113">For additional information on uninstalling [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , see [Uninstall Reporting Services 2012](https://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\)).</span></span> <span data-ttu-id="81d91-114">此主题说明如何卸载特定版本，它涉及的步骤与以前版本所用的步骤相似。</span><span class="sxs-lookup"><span data-stu-id="81d91-114">the topic describes how to uninstall a specific version and the procedures are similar for previous versions as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d91-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="81d91-115">See Also</span></span>  
 [<span data-ttu-id="81d91-116">升级顾问 &#40;Reporting Services 升级问题&#41;</span><span class="sxs-lookup"><span data-stu-id="81d91-116">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
