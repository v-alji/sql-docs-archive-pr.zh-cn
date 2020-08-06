---
title: SQL Server Management Studio 中的 Reporting Services (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], how-to topics
ms.assetid: 60685458-9108-47bf-820a-5e7db454d408
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3f4083d8b288c8816925723f4cfaef4342dd0298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691576"
---
# <a name="reporting-services-in-sql-server-management-studio-ssrs"></a><span data-ttu-id="3dbde-102">SQL Server Management Studio 中的 Reporting Services (SSRS)</span><span class="sxs-lookup"><span data-stu-id="3dbde-102">Reporting Services in SQL Server Management Studio (SSRS)</span></span>
  <span data-ttu-id="3dbde-103">报表服务器管理员可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="3dbde-103">Report server administrators can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to:</span></span>  
  
-   <span data-ttu-id="3dbde-104">启用功能、设置服务器默认设置和管理正在运行的作业。</span><span class="sxs-lookup"><span data-stu-id="3dbde-104">Enable features, set server defaults, and manage running jobs.</span></span>  
  
-   <span data-ttu-id="3dbde-105">查看和创建自定义报表。</span><span class="sxs-lookup"><span data-stu-id="3dbde-105">View and create custom reports.</span></span> <span data-ttu-id="3dbde-106">在对象资源管理器中，很多节点都显示一组随 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]一起安装的标准报表。</span><span class="sxs-lookup"><span data-stu-id="3dbde-106">In Object Explorer, many nodes display a set of standard reports that are installed with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="3dbde-107">您必须具有管理员权限。</span><span class="sxs-lookup"><span data-stu-id="3dbde-107">You must have administrator permissions.</span></span> <span data-ttu-id="3dbde-108">自定义报表的架构必须匹配已安装报表的架构。</span><span class="sxs-lookup"><span data-stu-id="3dbde-108">The schema of a custom report must match the schema of the installed reports.</span></span> <span data-ttu-id="3dbde-109">有关详细信息，请参阅 [Management Studio 中的自定义报表](../../ssms/object/custom-reports-in-management-studio.md)和[查找报表定义架构版本 (SSRS)](../reports/find-the-report-definition-schema-version-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3dbde-109">For more information, see [Custom Reports in Management Studio](../../ssms/object/custom-reports-in-management-studio.md) and [Find the Report Definition Schema Version &#40;SSRS&#41;](../reports/find-the-report-definition-schema-version-ssrs.md).</span></span>  
  
 <span data-ttu-id="3dbde-110">报告作者可以使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="3dbde-110">Report authors can use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to:</span></span>  
  
-   <span data-ttu-id="3dbde-111">从地图报表的查询结果集展现空间数据。</span><span class="sxs-lookup"><span data-stu-id="3dbde-111">Visualize spatial data from a query result set for a map report.</span></span> <span data-ttu-id="3dbde-112">在运行查询后，在结果集窗格中使用 **“空间结果”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="3dbde-112">After you run the query, use the **Spatial results** tab in the result set pane.</span></span> <span data-ttu-id="3dbde-113">有关详细信息，请参阅 [View Spatial Data in Object Explorer](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="3dbde-113">For more information, see [View Spatial Data in Object Explorer](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md).</span></span>  
  
 <span data-ttu-id="3dbde-114">本节包含对如何使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]执行各种报表任务的分步说明。</span><span class="sxs-lookup"><span data-stu-id="3dbde-114">This section contains step-by-step instructions for performing various reporting tasks using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="3dbde-115">也可以使用报表管理器来创建和管理共享计划。</span><span class="sxs-lookup"><span data-stu-id="3dbde-115">Creating and managing shared schedules can also be performed using Report Manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3dbde-116">本节内容</span><span class="sxs-lookup"><span data-stu-id="3dbde-116">In This Section</span></span>  
  
-   [<span data-ttu-id="3dbde-117">在 Management Studio 中连接到报表服务器</span><span class="sxs-lookup"><span data-stu-id="3dbde-117">Connect to a Report Server in Management Studio</span></span>](connect-to-a-report-server-in-management-studio.md)  
  
-   [<span data-ttu-id="3dbde-118">设置报表服务器属性 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3dbde-118">Set Report Server Properties &#40;Management Studio&#41;</span></span>](set-report-server-properties-management-studio.md)  
  
-   [<span data-ttu-id="3dbde-119">创建、删除或修改角色 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3dbde-119">Create, Delete, or Modify a Role &#40;Management Studio&#41;</span></span>](../security/role-definitions-create-delete-or-modify.md)  
  
-   [<span data-ttu-id="3dbde-120">删除项 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3dbde-120">Delete an Item &#40;Management Studio&#41;</span></span>](delete-an-item-management-studio.md)  
  
-   [<span data-ttu-id="3dbde-121">取消报表服务器作业 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3dbde-121">Cancel Report Server Jobs &#40;Management Studio&#41;</span></span>](cancel-report-server-jobs-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="3dbde-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3dbde-122">See Also</span></span>  
 <span data-ttu-id="3dbde-123">[Management Studio F1 帮助中的报表服务器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="3dbde-123">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="3dbde-124">SQL Server Management Studio 简介</span><span class="sxs-lookup"><span data-stu-id="3dbde-124">Introducing SQL Server Management Studio</span></span>](../../ssms/sql-server-management-studio-ssms.md)  
  
  
