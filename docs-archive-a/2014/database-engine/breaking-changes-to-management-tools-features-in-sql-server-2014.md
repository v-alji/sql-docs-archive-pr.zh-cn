---
title: SQL Server 2014 中管理工具功能的重大更改 |Microsoft Docs
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 3ff3fad8-b569-4516-bd58-5a3efeb537e2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0487b6ab0958e0b83d4e8e34be507b5b3211ac87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588078"
---
# <a name="breaking-changes-to-management-tools-features-in-sql-server-2014"></a><span data-ttu-id="cf733-102">SQL Server 2014 中管理工具功能的重大更改</span><span class="sxs-lookup"><span data-stu-id="cf733-102">Breaking Changes to Management Tools Features in SQL Server 2014</span></span>
  <span data-ttu-id="cf733-103">本主题介绍管理工具功能的重大更改。</span><span class="sxs-lookup"><span data-stu-id="cf733-103">This topic describes breaking changes to management tools features.</span></span> <span data-ttu-id="cf733-104">这些更改可能导致基于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的早期版本的应用程序、脚本或功能无法继续使用。</span><span class="sxs-lookup"><span data-stu-id="cf733-104">These changes might break applications, scripts, or functionalities that are based on earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cf733-105">在进行升级时可能会遇到这些问题。</span><span class="sxs-lookup"><span data-stu-id="cf733-105">You might encounter these issues when you upgrade.</span></span> <span data-ttu-id="cf733-106">有关详细信息，请参阅 [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="cf733-106">For more information, see [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).</span></span>  
  
## <a name="breaking-changes-in-sssql14"></a><span data-ttu-id="cf733-107">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 中的重大更改。</span><span class="sxs-lookup"><span data-stu-id="cf733-107">Breaking Changes in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span></span>  
 <span data-ttu-id="cf733-108">将很快提供相关信息。</span><span class="sxs-lookup"><span data-stu-id="cf733-108">Information to come later.</span></span>  
  
## <a name="breaking-changes-in-sssql11"></a><span data-ttu-id="cf733-109">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 中的重大更改。</span><span class="sxs-lookup"><span data-stu-id="cf733-109">Breaking Changes in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span></span>  
  
### <a name="you-cannot-use-sssql11-management-tools-to-create-a-utility-control-point-on-a-sskilimanjaro-instance-of-sql-server"></a><span data-ttu-id="cf733-110">不能使用 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 管理工具在 SQL Server 的 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 实例上创建实用工具控制点</span><span class="sxs-lookup"><span data-stu-id="cf733-110">You cannot use [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Management Tools to create a utility control point on a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] instance of SQL Server</span></span>  
 <span data-ttu-id="cf733-111">若要在 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]实例上创建实用工具控制点，请使用 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 管理工具。</span><span class="sxs-lookup"><span data-stu-id="cf733-111">To create a utility control point on an instance of [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], use [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Management Tools.</span></span>  
  
### <a name="smo-has-been-reversioned-in-sssql11"></a><span data-ttu-id="cf733-112">在 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 中复原了 SMO</span><span class="sxs-lookup"><span data-stu-id="cf733-112">SMO has been reversioned in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span></span>  
 <span data-ttu-id="cf733-113">使用 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 或早期版本的 SMO 开发的代码可能需要稍做更改才能针对 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 生成。</span><span class="sxs-lookup"><span data-stu-id="cf733-113">Code developed with SMO from [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] or earlier versions might not build against [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] without minor modifications.</span></span> <span data-ttu-id="cf733-114">有关详细信息，请参阅 [Backward Compatibility in SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md)。</span><span class="sxs-lookup"><span data-stu-id="cf733-114">For more information, see [Backward Compatibility in SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md).</span></span>  

## <a name="breaking-changes-in-sql-server-2005"></a><a name="previous-versions"></a><span data-ttu-id="cf733-115">SQL Server 2005 中的重大更改</span><span class="sxs-lookup"><span data-stu-id="cf733-115">Breaking Changes in SQL Server 2005</span></span>  

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a><span data-ttu-id="cf733-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf733-116">See Also</span></span>  
 [<span data-ttu-id="cf733-117">向后兼容性</span><span class="sxs-lookup"><span data-stu-id="cf733-117">Backward Compatibility</span></span>](../../2014/getting-started/backward-compatibility.md)  
 [<span data-ttu-id="cf733-118">有关 SQL Server 2014 中管理工具功能的重大更改的详细信息</span><span class="sxs-lookup"><span data-stu-id="cf733-118">More about Breaking Changes to Management Tools Features in SQL Server 2014</span></span>](breaking-changes-to-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)  
  
  
