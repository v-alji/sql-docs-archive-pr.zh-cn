---
title: 将 Master Data Services 数据库与 Web 应用程序关联 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ccb25672-f71d-4135-b548-f50eb45d8fa5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 01afde6aea5065a51cb9e7ae5dc4151e9f1e9fc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687952"
---
# <a name="associate-a-master-data-services-database-and-web-application"></a><span data-ttu-id="8f587-102">将 Master Data Services 数据库与 Web 应用程序关联</span><span class="sxs-lookup"><span data-stu-id="8f587-102">Associate a Master Data Services Database and Web Application</span></span>
  <span data-ttu-id="8f587-103">将您的 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序与 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库关联以指定要用于 Web 操作的数据库。</span><span class="sxs-lookup"><span data-stu-id="8f587-103">Associate your [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application with a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database to specify the database to use for web operations.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8f587-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="8f587-104">Prerequisites</span></span>  
  
-   [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] <span data-ttu-id="8f587-105">必须安装在本地计算机上。</span><span class="sxs-lookup"><span data-stu-id="8f587-105">must be installed on the local computer.</span></span> <span data-ttu-id="8f587-106">有关详细信息，请参阅 [安装 Master Data Services](install-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8f587-106">For more information, see [Install Master Data Services](install-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="8f587-107">本地 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序必须存在。</span><span class="sxs-lookup"><span data-stu-id="8f587-107">A local [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application must exist.</span></span> <span data-ttu-id="8f587-108">有关详细信息，请参阅[创建主数据管理器 Web 应用程序 (Master Data Services)](create-a-master-data-manager-web-application-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8f587-108">For more information, see [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="8f587-109">本地或远程 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库必须存在。</span><span class="sxs-lookup"><span data-stu-id="8f587-109">Either a local or remote [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database must exist.</span></span> <span data-ttu-id="8f587-110">有关详细信息，请参阅 [创建 Master Data Services 数据库](create-a-master-data-services-database.md)。</span><span class="sxs-lookup"><span data-stu-id="8f587-110">For more information, see [Create a Master Data Services Database](create-a-master-data-services-database.md).</span></span>  
  
### <a name="to-associate-a-master-data-services-database-and-web-application"></a><span data-ttu-id="8f587-111">将 Master Data Services 数据库与 Web 应用程序关联</span><span class="sxs-lookup"><span data-stu-id="8f587-111">To associate a Master Data Services database and web application</span></span>  
  
1.  <span data-ttu-id="8f587-112">打开 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8f587-112">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="8f587-113">在左窗格中单击 **“Web 配置”** 。</span><span class="sxs-lookup"><span data-stu-id="8f587-113">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="8f587-114">在 **“Web 配置”** 页的 **“Web 应用程序”** 下，从 **“网站”** 列表中选择包含 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序的网站。</span><span class="sxs-lookup"><span data-stu-id="8f587-114">On the **Web Configuration** page, under **Web application**, from the **Website** list, select the website that contains your [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
4.  <span data-ttu-id="8f587-115">在 **“Web 应用程序”** 框中，选择承载 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="8f587-115">In the **Web application** box, select the web application that hosts [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>  
  
5.  <span data-ttu-id="8f587-116">在 **“将应用程序与数据库相关联”** 下，单击 **“选择”**。</span><span class="sxs-lookup"><span data-stu-id="8f587-116">Under **Associate Application with Database**, click **Select**.</span></span> <span data-ttu-id="8f587-117">将打开 **“连接到数据库”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="8f587-117">The **Connect to Database** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="8f587-118">指定承载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 实例的连接信息，然后单击 **“连接”**。</span><span class="sxs-lookup"><span data-stu-id="8f587-118">Specify connection information for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database, and click **Connect**.</span></span>  
  
7.  <span data-ttu-id="8f587-119">从 **“Master Data Services 数据库”** 列表选择要与 Web 应用程序关联的数据库，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="8f587-119">From the **Master Data Services database** list, select the database you want to associate the web application with and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="8f587-120">在 **“将应用程序与数据库相关联”** 下，验证实例和数据库信息是正确的，然后单击 **“应用”**。</span><span class="sxs-lookup"><span data-stu-id="8f587-120">Under **Associate Application with Database**, verify that the instance and database information are correct, and then click **Apply**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8f587-121">后续步骤</span><span class="sxs-lookup"><span data-stu-id="8f587-121">Next Steps</span></span>  
  
-   <span data-ttu-id="8f587-122">在创建 Web 应用程序时，将自动启用对 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web 服务的编程访问。</span><span class="sxs-lookup"><span data-stu-id="8f587-122">Programmatic access to [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web services is automatically enabled when the web application is created.</span></span> <span data-ttu-id="8f587-123">为使开发人员访问服务元数据以便轻松地为编程访问生成代理类，启用元数据发布。</span><span class="sxs-lookup"><span data-stu-id="8f587-123">To let developers access the service metadata to easily generate proxy classes for programmatic access, enable metadata publishing.</span></span> <span data-ttu-id="8f587-124">有关详细信息，请参阅[创建主数据管理器 Web 服务代理类](../develop/create-master-data-manager-web-service-proxy-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="8f587-124">For more information, see [Create Master Data Manager Web Service Proxy Classes](../develop/create-master-data-manager-web-service-proxy-classes.md).</span></span>  
  
-   <span data-ttu-id="8f587-125">将用户和组添加到 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8f587-125">Add users and groups to [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="8f587-126">如果没有向任何用户或组授予访问 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]的权限，您必须使用 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 系统管理员凭据打开 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8f587-126">If no users or groups have been granted access to [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], you must open [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] using the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] system administrator credentials.</span></span> <span data-ttu-id="8f587-127">有关详细信息，请参阅[管理员 (Master Data Services)](../administrators-master-data-services.md) 和[用户和组 (Master Data Services)](../users-and-groups-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8f587-127">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md) and [Users and Groups &#40;Master Data Services&#41;](../users-and-groups-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f587-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f587-128">See Also</span></span>  
 <span data-ttu-id="8f587-129">[安装 Master Data Services](install-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8f587-129">[Install Master Data Services](install-master-data-services.md) </span></span>  
 [<span data-ttu-id="8f587-130">“Web 配置”页（Master Data Services 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="8f587-130">Web Configuration Page &#40;Master Data Services Configuration Manager&#41;</span></span>](../web-configuration-page-master-data-services-configuration-manager.md)  
  
  
