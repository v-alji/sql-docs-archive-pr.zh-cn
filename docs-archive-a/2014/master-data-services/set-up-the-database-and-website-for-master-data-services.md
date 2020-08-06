---
title: 为 Master Data Services 设置数据库和网站 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: da797bc6f9838a2baab6cc440cc7d778a7a6e186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591448"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a><span data-ttu-id="09ee8-102">为 Master Data Services 设置数据库和网站</span><span class="sxs-lookup"><span data-stu-id="09ee8-102">Set up the Database and Website for Master Data Services</span></span>
  <span data-ttu-id="09ee8-103">使用 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 为 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) 设置数据库和网站</span><span class="sxs-lookup"><span data-stu-id="09ee8-103">Use the [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] to set up the database and website for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS)</span></span>  
  
 <span data-ttu-id="09ee8-104">若要设置数据和网站，请完成以下任务。</span><span class="sxs-lookup"><span data-stu-id="09ee8-104">To set up the database and website, complete the following tasks.</span></span>  
  
1.  <span data-ttu-id="09ee8-105">使用中的 "**数据库配置**" 页创建数据库 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="09ee8-105">Create a database using the **Database Configuration** page in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span>  
  
     <span data-ttu-id="09ee8-106">有关信息，请参阅[数据库配置页 &#40;Master Data Services 配置管理器&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md)和[创建数据库向导 &#40;Master Data Services 配置管理器&#41;](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="09ee8-106">For information, see [Database Configuration Page &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md) and [Create Database Wizard &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
2.  <span data-ttu-id="09ee8-107">创建新网站，选择默认网站，或者使用中的 " **Web 配置**" 页选择另一个现有网站 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="09ee8-107">Create a new website, select the default website, or select another existing website, using the **Web Configuration** page in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span> <span data-ttu-id="09ee8-108">然后将 MDS 数据库与你选择或创建的 Web 应用程序相关联。</span><span class="sxs-lookup"><span data-stu-id="09ee8-108">Then associate the MDS database with the web application you select or create.</span></span>  
  
     <span data-ttu-id="09ee8-109">有关信息，请参阅[Web 配置页 &#40;Master Data Services 配置管理器&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md)和 "[创建网站" 对话框 &#40;Master Data Services 配置管理器&#41;](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="09ee8-109">For information, see [Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) and [Create Website Dialog Box &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="09ee8-110"> (可选) 使用中的 " **Web 配置**" 页启用与 Data Quality Services 的集成 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="09ee8-110">(Optional) Enable integration with Data Quality Services using the **Web Configuration** page in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span>  
  
     <span data-ttu-id="09ee8-111">有关详细信息，请参阅[Web 配置页 &#40;Master Data Services 配置管理器&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md)和[启用 Data Quality Services 与 Master Data Services 集成](install-windows/enable-data-quality-services-integration-with-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="09ee8-111">For more information, see [Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) and [Enable Data Quality Services Integration with Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).</span></span>  
  
 <span data-ttu-id="09ee8-112">你还可以使用 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 指定与 MDS 数据库相关联的 Web 应用程序和服务的设置。</span><span class="sxs-lookup"><span data-stu-id="09ee8-112">You can also use [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] to specify settings for the web applications and services associated with the MDS database.</span></span> <span data-ttu-id="09ee8-113">例如，你可以指定加载数据的频率或发送验证电子邮件的频率。</span><span class="sxs-lookup"><span data-stu-id="09ee8-113">For example, you can specify how frequently data is loaded or how often validation emails are sent.</span></span> <span data-ttu-id="09ee8-114">有关详细信息，请参阅[系统设置 (Master Data Services)](../../2014/master-data-services/system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="09ee8-114">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ee8-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09ee8-115">See Also</span></span>  
 <span data-ttu-id="09ee8-116">[Master Data Services 数据库](../../2014/master-data-services/master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="09ee8-116">[Master Data Services Database](../../2014/master-data-services/master-data-services-database.md) </span></span>  
 [<span data-ttu-id="09ee8-117">主数据管理器 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="09ee8-117">Master Data Manager Web Application</span></span>](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  
