---
title: Reporting Services 向后兼容性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- SSRS, backward compatibility
- SQL Server Reporting Services, backward compatibility
- backward compatibility [Reporting Services]
ms.assetid: 675b0e0e-cfee-4790-9675-80fc3ea6d30f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7203740ba7f52dfc2cd3793a20fed9fecf5f9468
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691064"
---
# <a name="reporting-services-backward-compatibility"></a><span data-ttu-id="20269-102">Reporting Services 的向后兼容性</span><span class="sxs-lookup"><span data-stu-id="20269-102">Reporting Services Backward Compatibility</span></span>
  <span data-ttu-id="20269-103">本部分介绍各个版本之间的行为变化 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="20269-103">This section describes changes in behavior between versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="20269-104">它包括不再可用或计划在将来的版本中删除的功能。</span><span class="sxs-lookup"><span data-stu-id="20269-104">It covers features that are no longer available or are scheduled to be removed in a future release.</span></span> <span data-ttu-id="20269-105">本节还介绍了对产品所做的根本性更改，已知这些更改会使包含 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能的自定义应用程序不能正常工作。</span><span class="sxs-lookup"><span data-stu-id="20269-105">It also describes fundamental changes to the product that are known to break a custom application that includes [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="20269-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="20269-106">In This Section</span></span>  
  
|<span data-ttu-id="20269-107">主题</span><span class="sxs-lookup"><span data-stu-id="20269-107">Topic</span></span>|<span data-ttu-id="20269-108">说明</span><span class="sxs-lookup"><span data-stu-id="20269-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="20269-109">SQL Server 2014 的 SQL Server Reporting Services 中停止使用的功能</span><span class="sxs-lookup"><span data-stu-id="20269-109">Discontinued Functionality to SQL Server Reporting Services in SQL Server 2014</span></span>](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)|<span data-ttu-id="20269-110">介绍在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的早期版本中存在但在后来的版本中已删除的功能。</span><span class="sxs-lookup"><span data-stu-id="20269-110">Describes features that existed in earlier versions of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] but that have been removed in later versions.</span></span>|  
|[<span data-ttu-id="20269-111">SQL Server 2014 的 SQL Server Reporting Services 中不推荐使用的功能</span><span class="sxs-lookup"><span data-stu-id="20269-111">Deprecated Features in SQL Server Reporting Services in SQL Server 2014</span></span>](deprecated-features-in-sql-server-reporting-services-ssrs.md)|<span data-ttu-id="20269-112">介绍此版本的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中出于向后兼容的目的而存在、但在将来版本的 SQL Server 中将会删除的功能。</span><span class="sxs-lookup"><span data-stu-id="20269-112">Describes features that exist this release of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] for backward compatibility, but which will be removed in a future version of SQL Server.</span></span>|  
|[<span data-ttu-id="20269-113">SQL Server 2014 的 SQL Server Reporting Services 中的重大更改</span><span class="sxs-lookup"><span data-stu-id="20269-113">Breaking Changes in SQL Server Reporting Services in SQL Server 2014</span></span>](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)|<span data-ttu-id="20269-114">介绍升级到 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]时可能遇到的问题。</span><span class="sxs-lookup"><span data-stu-id="20269-114">Describes issues that you might encounter when you upgrade [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="20269-115">SQL Server 2014 中 SQL Server Reporting Services 的行为更改</span><span class="sxs-lookup"><span data-stu-id="20269-115">Behavior Changes to SQL Server Reporting Services  in SQL Server 2014</span></span>](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)|<span data-ttu-id="20269-116">介绍在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]中已更改的功能。</span><span class="sxs-lookup"><span data-stu-id="20269-116">Describes features that have changed in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20269-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20269-117">See Also</span></span>  
 <span data-ttu-id="20269-118">[向后兼容性](../../2014/getting-started/backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="20269-118">[Backward Compatibility](../../2014/getting-started/backward-compatibility.md) </span></span>  
 [<span data-ttu-id="20269-119">Analysis Services 向后兼容性</span><span class="sxs-lookup"><span data-stu-id="20269-119">Analysis Services Backward Compatibility</span></span>](../../2014/analysis-services/analysis-services-backward-compatibility.md)  
  
  
