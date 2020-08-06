---
title: “项目版本”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isprojectprop.versions.f1
ms.assetid: a48a387c-2e70-45bc-be2e-26e57a9bb2c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 998dd194c2a056121fd6f7a404e75c7080b85aa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691839"
---
# <a name="project-versions-dialog-box"></a><span data-ttu-id="7bc7d-102">“项目版本”对话框</span><span class="sxs-lookup"><span data-stu-id="7bc7d-102">Project Versions Dialog Box</span></span>
  <span data-ttu-id="7bc7d-103">使用 **“项目版本”** 对话框可以查看项目版本和还原以前的版本。</span><span class="sxs-lookup"><span data-stu-id="7bc7d-103">Use the **Project Versions** dialog box to view versions of a project and to restore a previous version.</span></span>  
  
 <span data-ttu-id="7bc7d-104">你还可以在 [catalog.object_versions（SSISDB 数据库）](/sql/integration-services/system-views/catalog-object-versions-ssisdb-database)视图中查看先前版本，以及使用[catalog.restore_project（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database)存储过程还原先前版本。</span><span class="sxs-lookup"><span data-stu-id="7bc7d-104">You can also view previous versions in the [catalog.object_versions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-versions-ssisdb-database) view, and use the [catalog.restore_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database) stored procedure to restore previous versions.</span></span>  
  
 <span data-ttu-id="7bc7d-105">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="7bc7d-105">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="7bc7d-106">打开“项目版本”对话框</span><span class="sxs-lookup"><span data-stu-id="7bc7d-106">Open the Project Versions dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="7bc7d-107">还原项目版本</span><span class="sxs-lookup"><span data-stu-id="7bc7d-107">Restore a Project Version</span></span>](#restore)  
  
##  <a name="open-the-project-versions-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="7bc7d-108">打开“项目版本”对话框</span><span class="sxs-lookup"><span data-stu-id="7bc7d-108">Open the Project Versions dialog box</span></span>  
  
1.  <span data-ttu-id="7bc7d-109">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="7bc7d-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="7bc7d-110">也就是说，连接到承载 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 数据库的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="7bc7d-110">That is, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="7bc7d-111">在对象资源管理器中，展开树以便显示 **“Integration Services 目录”** 节点。</span><span class="sxs-lookup"><span data-stu-id="7bc7d-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="7bc7d-112">展开 **“Integration Services 目录”** 节点以显示 **SSISDB** 节点。</span><span class="sxs-lookup"><span data-stu-id="7bc7d-112">Expand the **Integration Services Catalogs** node to display the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="7bc7d-113">**SSISDB** 节点包含一个或多个文件夹，每个文件夹包含一个或多个项目。</span><span class="sxs-lookup"><span data-stu-id="7bc7d-113">The **SSISDB** node contains one or more folders that each contain one or more projects.</span></span> <span data-ttu-id="7bc7d-114">展开包含您感兴趣的项目的文件夹。</span><span class="sxs-lookup"><span data-stu-id="7bc7d-114">Expand the folder that contains the project you are interested in.</span></span>  
  
5.  <span data-ttu-id="7bc7d-115">右键单击该项目，然后单击“版本”。 </span><span class="sxs-lookup"><span data-stu-id="7bc7d-115">Right-click the project, and then click **Versions**.</span></span>  
  
 <span data-ttu-id="7bc7d-116">在“项目版本”对话框中，“版本”表显示服务器上已部署的项目的版本列表，并显示部署版本的日期和时间、还原版本的日期和时间（如果被还原过）、版本说明以及版本标识符。  </span><span class="sxs-lookup"><span data-stu-id="7bc7d-116">In the **Project Versions** dialog box, the **Versions** table displays the list of versions of the project that have been deployed on the server, with the date and time the version was deployed, the date and time the version was restored (if it was restored), the version description, and a version identifier.</span></span> <span data-ttu-id="7bc7d-117">当前活动版本用表的 **“当前”** 列中的复选标记表示。</span><span class="sxs-lookup"><span data-stu-id="7bc7d-117">The currently active version is indicated with a check mark in the **Current** column of the table.</span></span>  
  
##  <a name="restore-a-project-version"></a><a name="restore"></a> <span data-ttu-id="7bc7d-118">还原项目版本</span><span class="sxs-lookup"><span data-stu-id="7bc7d-118">Restore a Project Version</span></span>  
 <span data-ttu-id="7bc7d-119">若要还原项目的以前版本，请在 **“版本”** 表中选择该版本，然后单击 **“还原到所选版本”** 。</span><span class="sxs-lookup"><span data-stu-id="7bc7d-119">To restore a previous version of a project, select the version in the **Versions** table, and then click **Restore to Selected Version**.</span></span> <span data-ttu-id="7bc7d-120">项目将还原到所选版本，且该版本用 **“版本”** 表的 **“当前”** 列中的复选标记表示。</span><span class="sxs-lookup"><span data-stu-id="7bc7d-120">The project is restored to the selected version and that version is indicated with a check mark in the **Current** column of the **Versions** table.</span></span>  
  
  
