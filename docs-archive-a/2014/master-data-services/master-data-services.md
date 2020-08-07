---
title: Master Data Services |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 87d8c588c3893a5aadf950a60681ec60d50309de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587453"
---
# <a name="master-data-services"></a><span data-ttu-id="20c5f-102">Master Data Services</span><span class="sxs-lookup"><span data-stu-id="20c5f-102">Master Data Services</span></span>
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] <span data-ttu-id="20c5f-103">(MDS) 是针对主数据管理的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 解决方案。</span><span class="sxs-lookup"><span data-stu-id="20c5f-103">(MDS) is the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] solution for master data management.</span></span> <span data-ttu-id="20c5f-104">主数据管理 (MDM) 描述组织为发现和定义数据的非事务列表（其目标是编译可维护的主列表）而付出的努力。</span><span class="sxs-lookup"><span data-stu-id="20c5f-104">Master data management (MDM) describes the efforts made by an organization to discover and define non-transactional lists of data, with the goal of compiling maintainable master lists.</span></span> <span data-ttu-id="20c5f-105">一个 MDM 项目通常包括评估和重构内部业务流程以及实现 MDM 技术。</span><span class="sxs-lookup"><span data-stu-id="20c5f-105">An MDM project generally includes an evaluation and restructuring of internal business processes along with the implementation of MDM technology.</span></span> <span data-ttu-id="20c5f-106">成功的 MDM 解决方案的结果是可以进行分析的可靠、集中的数据，从而导致更好的业务决策。</span><span class="sxs-lookup"><span data-stu-id="20c5f-106">The result of a successful MDM solution is reliable, centralized data that can be analyzed, resulting in better business decisions.</span></span>

 <span data-ttu-id="20c5f-107">通过适当的培训，大多数业务用户应能够实现 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 解决方案。</span><span class="sxs-lookup"><span data-stu-id="20c5f-107">With the right training, most business users should be able to implement a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] solution.</span></span> <span data-ttu-id="20c5f-108">此外，您可以使用 MDS 管理任何域；这一管理并非特定于管理客户、产品或帐户的列表。</span><span class="sxs-lookup"><span data-stu-id="20c5f-108">In addition, you can use MDS to manage any domain; it's not specific to managing lists of customers, products, or accounts.</span></span> <span data-ttu-id="20c5f-109">首次安装 MDS 时，它不包含任何域的结构-您可以通过为它们创建模型来定义所需的域。</span><span class="sxs-lookup"><span data-stu-id="20c5f-109">When MDS is first installed, it does not include the structure for any domains-you define the domains you need by creating models for them.</span></span>

 <span data-ttu-id="20c5f-110">其他 Master Data Services 功能包括层次结构、粒度安全性、事务、数据版本控制和业务规则。</span><span class="sxs-lookup"><span data-stu-id="20c5f-110">Other Master Data Services features include hierarchies, granular security, transactions, data versioning, and business rules.</span></span>

 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]<span data-ttu-id="20c5f-111">包括以下组件和工具：</span><span class="sxs-lookup"><span data-stu-id="20c5f-111">includes the following components and tools:</span></span>

-   [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]<span data-ttu-id="20c5f-112">，这个工具可用于创建和配置 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库以及 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="20c5f-112">, a tool you use to create and configure [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] databases and web applications.</span></span>

-   [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]<span data-ttu-id="20c5f-113">，用于执行管理任务的 web 应用程序 (如) 创建模型或业务规则，以及用户访问更新数据的权限。</span><span class="sxs-lookup"><span data-stu-id="20c5f-113">, a web application you use to perform administrative tasks (like creating a model or business rule), and that users access to update data.</span></span>

-   <span data-ttu-id="20c5f-114">MDSModelDeploy.exe，这个工具可用于创建您的模型对象和数据的包，以便您可以将它们部署到其他环境。</span><span class="sxs-lookup"><span data-stu-id="20c5f-114">MDSModelDeploy.exe, a tool you use to create packages of your model objects and data so you can deploy them to other environments.</span></span>

-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] <span data-ttu-id="20c5f-115">Web 服务，开发人员可使用它来扩展或开发针对 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 的自定义解决方案。</span><span class="sxs-lookup"><span data-stu-id="20c5f-115">web service, which developers can use to extend or develop custom solutions for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span>

-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]<span data-ttu-id="20c5f-116">[!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]，用于管理数据以及创建新实体和属性。</span><span class="sxs-lookup"><span data-stu-id="20c5f-116">[!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)], which you use to manage data and create new entities and attributes.</span></span>

 <span data-ttu-id="20c5f-117">有关 MDS 资源的摘要，请参阅[SQL Server Master Data Services 门户](https://go.microsoft.com/fwlink/?LinkID=214272)。</span><span class="sxs-lookup"><span data-stu-id="20c5f-117">For a summary of MDS resources, see the [SQL Server Master Data Services Portal](https://go.microsoft.com/fwlink/?LinkID=214272).</span></span>

|||
|-|-|
|<span data-ttu-id="20c5f-118">**按区域浏览内容**</span><span class="sxs-lookup"><span data-stu-id="20c5f-118">**Browse Content by Area**</span></span><br /> <span data-ttu-id="20c5f-119">![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标") [Master Data Services 概述](master-data-services-overview-mds.md)</span><span class="sxs-lookup"><span data-stu-id="20c5f-119">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Master Data Services Overview](master-data-services-overview-mds.md)</span></span><br /><br /> <span data-ttu-id="20c5f-120">![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标") [Master Data Services 功能和任务](../../2014/master-data-services/master-data-services-features-and-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="20c5f-120">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Master Data Services Features and Tasks](../../2014/master-data-services/master-data-services-features-and-tasks.md)</span></span><br /><br /> <span data-ttu-id="20c5f-121">![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标")[技术参考 (Master Data Services) ](technical-reference-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="20c5f-121">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Technical Reference (Master Data Services)](technical-reference-master-data-services.md)</span></span><br /><br /> <span data-ttu-id="20c5f-122">![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标")[开发人员指南 (Master Data Services) ](develop/master-data-services-developer-documentation.md)</span><span class="sxs-lookup"><span data-stu-id="20c5f-122">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Developer's Guide (Master Data Services)](develop/master-data-services-developer-documentation.md)</span></span>||


