---
title: Master Data Services 数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], about the database
- database [Master Data Services]
ms.assetid: 5f590cc1-6ec2-4b8c-a598-03de0f6051a0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7e4bae180dfb7c9051d5445a689c44978ef73bfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587872"
---
# <a name="master-data-services-database"></a><span data-ttu-id="d9823-102">Master Data Services 数据库</span><span class="sxs-lookup"><span data-stu-id="d9823-102">Master Data Services Database</span></span>
  <span data-ttu-id="d9823-103">该数据库包含 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 系统的所有信息。</span><span class="sxs-lookup"><span data-stu-id="d9823-103">The database contains all of the information for the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system.</span></span> <span data-ttu-id="d9823-104">它是 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 部署的关键。</span><span class="sxs-lookup"><span data-stu-id="d9823-104">It is central to a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] deployment.</span></span> <span data-ttu-id="d9823-105">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库：</span><span class="sxs-lookup"><span data-stu-id="d9823-105">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database:</span></span>  
  
-   <span data-ttu-id="d9823-106">存储 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 系统所需的设置、数据库对象和数据。</span><span class="sxs-lookup"><span data-stu-id="d9823-106">Stores the settings, database objects, and data required by the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system.</span></span>  
  
-   <span data-ttu-id="d9823-107">包含用于处理源系统的数据的临时表。</span><span class="sxs-lookup"><span data-stu-id="d9823-107">Contains staging tables that are used to process data from source systems.</span></span>  
  
-   <span data-ttu-id="d9823-108">提供架构和数据库对象来存储源系统的主数据。</span><span class="sxs-lookup"><span data-stu-id="d9823-108">Provides a schema and database objects to store master data from source systems.</span></span>  
  
-   <span data-ttu-id="d9823-109">支持版本控制功能，包括业务规则验证和电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="d9823-109">Supports versioning functionality, including business rule validation and e-mail notifications.</span></span>  
  
-   <span data-ttu-id="d9823-110">为需要从数据库中检索数据的订阅系统提供视图。</span><span class="sxs-lookup"><span data-stu-id="d9823-110">Provides views for subscribing systems that need to retrieve data from the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d9823-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="d9823-111">In This Section</span></span>  
  
-   [<span data-ttu-id="d9823-112">叶成员临时表 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d9823-112">Leaf Member Staging Table &#40;Master Data Services&#41;</span></span>](leaf-member-staging-table-master-data-services.md)  
  
-   [<span data-ttu-id="d9823-113">合并成员临时表 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d9823-113">Consolidated Member Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md)  
  
-   [<span data-ttu-id="d9823-114">关系临时表 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d9823-114">Relationship Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/relationship-staging-table-master-data-services.md)  
  
-   [<span data-ttu-id="d9823-115">临时过程错误 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d9823-115">Staging Process Errors &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/staging-process-errors-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="d9823-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9823-116">See Also</span></span>  
 <span data-ttu-id="d9823-117">[创建 Master Data Services 数据库](install-windows/create-a-master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="d9823-117">[Create a Master Data Services Database](install-windows/create-a-master-data-services-database.md) </span></span>  
 <span data-ttu-id="d9823-118">[数据库对象安全 &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d9823-118">[Database Object Security &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md) </span></span>  
 [<span data-ttu-id="d9823-119">数据库登录名、用户和角色 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d9823-119">Database Logins, Users, and Roles &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/database-logins-users-and-roles-master-data-services.md)  
  
  
