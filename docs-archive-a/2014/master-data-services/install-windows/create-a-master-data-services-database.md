---
title: 创建 Master Data Services 数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 8373bb35-f0f9-4c3c-a53c-dfaa2ce567ac
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9ee90ac5d02489da3b411b12389e949ff3136287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578912"
---
# <a name="create-a-master-data-services-database"></a><span data-ttu-id="693ae-102">创建 Master Data Services 数据库</span><span class="sxs-lookup"><span data-stu-id="693ae-102">Create a Master Data Services Database</span></span>
  <span data-ttu-id="693ae-103">在需要新数据库来支持 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web 应用程序和 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 服务时，创建 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="693ae-103">Create a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database when you need a new database to support the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application and [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="693ae-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="693ae-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="693ae-105">有关承载该数据库的计算机的要求信息，请参阅[数据库要求 (Master Data Services)](database-requirements-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="693ae-105">For information about the requirements for the computer that hosts the database, see [Database Requirements &#40;Master Data Services&#41;](database-requirements-master-data-services.md).</span></span>  
  
### <a name="to-create-a-master-data-services-database"></a><span data-ttu-id="693ae-106">创建 Master Data Services 数据库</span><span class="sxs-lookup"><span data-stu-id="693ae-106">To create a Master Data Services database</span></span>  
  
1.  <span data-ttu-id="693ae-107">打开 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="693ae-107">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="693ae-108">在左窗格中单击 **“数据库配置”** 。</span><span class="sxs-lookup"><span data-stu-id="693ae-108">In the left pane, click **Database Configuration**.</span></span>  
  
3.  <span data-ttu-id="693ae-109">在 **“数据库配置”** 页上，单击 **“创建数据库”**。</span><span class="sxs-lookup"><span data-stu-id="693ae-109">On the **Database Configuration** page, click **Create Database**.</span></span>  
  
4.  <span data-ttu-id="693ae-110">完成 **“创建数据库”** 向导来创建和配置数据库。</span><span class="sxs-lookup"><span data-stu-id="693ae-110">Complete the **Create Database** wizard to create and configure the database.</span></span> <span data-ttu-id="693ae-111">有关向导中的用户界面 (UI) 选项的信息，请参阅[创建数据库向导（Master Data Services 配置管理器）](../create-database-wizard-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="693ae-111">For information about the user interface (UI) options in the wizard, see [Create Database Wizard &#40;Master Data Services Configuration Manager&#41;](../create-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="693ae-112">后续步骤</span><span class="sxs-lookup"><span data-stu-id="693ae-112">Next Steps</span></span>  
  
-   <span data-ttu-id="693ae-113">为数据库和 Web 应用程序配置系统设置。</span><span class="sxs-lookup"><span data-stu-id="693ae-113">Configure system settings for the database and web application.</span></span> <span data-ttu-id="693ae-114">有关详细信息，请参阅[系统设置 (Master Data Services)](../system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="693ae-114">For more information, see [System Settings &#40;Master Data Services&#41;](../system-settings-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="693ae-115">创建 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序以与此数据库关联。</span><span class="sxs-lookup"><span data-stu-id="693ae-115">Create a [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application to associate with this database.</span></span> <span data-ttu-id="693ae-116">有关详细信息，请参阅[创建主数据管理器 Web 应用程序 (Master Data Services)](create-a-master-data-manager-web-application-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="693ae-116">For more information, see [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="693ae-117">配置维护计划以备份数据库和事务日志。</span><span class="sxs-lookup"><span data-stu-id="693ae-117">Configure a maintenance plan to back up the database and transaction logs.</span></span> <span data-ttu-id="693ae-118">有关详细信息，请参阅[数据库要求 (Master Data Services)](database-requirements-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="693ae-118">For more information, see [Database Requirements &#40;Master Data Services&#41;](database-requirements-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="693ae-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="693ae-119">See Also</span></span>  
 [<span data-ttu-id="693ae-120">安装 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="693ae-120">Install Master Data Services</span></span>](install-master-data-services.md)  
  
  
