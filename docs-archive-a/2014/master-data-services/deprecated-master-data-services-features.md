---
title: SQL Server 2014 中不推荐使用的 Master Data Services 功能 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d8506bda-66dd-45a4-bfc9-3a10fa665acc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce532e9f407ec475f7e59c0d79659265a9e0bf3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682914"
---
# <a name="deprecated-master-data-services-features-in-sql-server-2014"></a><span data-ttu-id="1400c-102">SQL Server 2014 中不推荐使用的 Master Data Services 功能</span><span class="sxs-lookup"><span data-stu-id="1400c-102">Deprecated Master Data Services Features in SQL Server 2014</span></span>
  <span data-ttu-id="1400c-103">本主题介绍 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中仍然可用但不推荐使用的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="1400c-103">This topic describes the deprecated [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] features that are still available in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="1400c-104">按照计划， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]未来版本将不再具有这些功能。</span><span class="sxs-lookup"><span data-stu-id="1400c-104">These features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1400c-105">在新的应用程序中不应使用这些不推荐使用的功能。</span><span class="sxs-lookup"><span data-stu-id="1400c-105">Deprecated features should not be used in new applications.</span></span>  
  
## <a name="staging-process"></a><span data-ttu-id="1400c-106">临时过程</span><span class="sxs-lookup"><span data-stu-id="1400c-106">Staging Process</span></span>  
 <span data-ttu-id="1400c-107"> 中使用的临时过程在 Web 应用程序将不再可用，但是仍可在  中使用。</span><span class="sxs-lookup"><span data-stu-id="1400c-107">The staging process that was used in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] is no longer available in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application; however it is still available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="1400c-108">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 临时过程的临时错误将不再显示在 UI 中。</span><span class="sxs-lookup"><span data-stu-id="1400c-108">Staging errors from the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] staging process are no longer displayed in the UI.</span></span> <span data-ttu-id="1400c-109">在临时过程中填充的错误代码在临时表中仍然可用，可在此处找到： [https://msdn.microsoft.com/library/ff487022.aspx](https://msdn.microsoft.com/library/ff487022.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="1400c-109">Error codes that are populated during the staging process are still available in the staging tables, and can be found here: [https://msdn.microsoft.com/library/ff487022.aspx](https://msdn.microsoft.com/library/ff487022.aspx).</span></span>  
  
 <span data-ttu-id="1400c-110">临时表（tblStgMember、tblStgMemberAttribute 和 tblStgRelationship）在数据库中仍然可用。</span><span class="sxs-lookup"><span data-stu-id="1400c-110">The staging tables (tblStgMember, tblStgMemberAttribute, and tblStgRelationship) are still available in the database.</span></span> <span data-ttu-id="1400c-111">用于启动临时过程的存储过程 (mdm.udpStagingSweep) 在数据库中仍然可用。</span><span class="sxs-lookup"><span data-stu-id="1400c-111">The stored procedure used to initiate the staging process (mdm.udpStagingSweep) is still available in the database.</span></span>  
  
 <span data-ttu-id="1400c-112">调用临时过程的 Web 服务方法仍然可用。</span><span class="sxs-lookup"><span data-stu-id="1400c-112">The web service methods that call the staging process are still available.</span></span>  
  
 <span data-ttu-id="1400c-113">在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]中设置的临时间隔适用于 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 和 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 中的临时过程。</span><span class="sxs-lookup"><span data-stu-id="1400c-113">The staging interval set in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] applies to the staging process in both [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] and [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="1400c-114">已在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 中实现性能更高的新临时过程。</span><span class="sxs-lookup"><span data-stu-id="1400c-114">A new, higher performance staging process has been implemented in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="1400c-115">有关详细信息，请参阅[数据导入 (Master Data Services)](overview-importing-data-from-tables-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1400c-115">For more information, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
## <a name="metadata"></a><span data-ttu-id="1400c-116">元数据</span><span class="sxs-lookup"><span data-stu-id="1400c-116">Metadata</span></span>  
 <span data-ttu-id="1400c-117">尽管元数据模型仍显示在[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序中，但不应使用该模型。</span><span class="sxs-lookup"><span data-stu-id="1400c-117">Though the Metadata model is still displayed in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, it should not be used.</span></span> <span data-ttu-id="1400c-118">未来的版本会将其删除。</span><span class="sxs-lookup"><span data-stu-id="1400c-118">It will be removed in a future release.</span></span> <span data-ttu-id="1400c-119">用户也不能再查看 "**资源管理器**" 功能区域中的元数据，也不能再创建元数据模型的版本。</span><span class="sxs-lookup"><span data-stu-id="1400c-119">Users can also no longer view metadata in the **Explorer** functional area, and you can no longer create versions of the Metadata model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1400c-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1400c-120">See Also</span></span>  
 [<span data-ttu-id="1400c-121">SQL Server 2014 中不再支持的 Master Data Services 功能</span><span class="sxs-lookup"><span data-stu-id="1400c-121">Discontinued Master Data Services Features in SQL Server 2014</span></span>](discontinued-master-data-services-features.md)  
  
  
