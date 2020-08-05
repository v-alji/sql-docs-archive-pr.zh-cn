---
title: "\"活动操作\" 对话框 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isoperations.executions.f1
- sql12.ssis.ssms.isoperations.general.f1
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 49861de7be207875c554e02d3f3b1b2f941fff64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579018"
---
# <a name="active-operations-dialog-box"></a><span data-ttu-id="5426f-102">“活动操作”对话框</span><span class="sxs-lookup"><span data-stu-id="5426f-102">Active Operations Dialog Box</span></span>
  <span data-ttu-id="5426f-103">使用 **“活动操作”** 对话框可以查看 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器上当前运行的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 操作的状态，例如部署、验证和包执行。</span><span class="sxs-lookup"><span data-stu-id="5426f-103">Use the **Active Operations** dialog box to view the status of currently running [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] operations on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, such as deployment, validation, and package execution.</span></span> <span data-ttu-id="5426f-104">此数据存储在 SSISDB 目录中。</span><span class="sxs-lookup"><span data-stu-id="5426f-104">This data is stored in the SSISDB catalog.</span></span>  
  
 <span data-ttu-id="5426f-105">有关相关 [!INCLUDE[tsql](../includes/tsql-md.md)] 视图的详细信息，请参阅 [catalog.operations（SSISDB 数据库）](/sql/integration-services/system-views/catalog-operations-ssisdb-database)、[catalog.validations（SSISDB 数据库）](/sql/integration-services/system-views/catalog-validations-ssisdb-database)和 [catalog.executions（SSISDB 数据库）](/sql/integration-services/system-views/catalog-executions-ssisdb-database)</span><span class="sxs-lookup"><span data-stu-id="5426f-105">For more information about related [!INCLUDE[tsql](../includes/tsql-md.md)] views, see [catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database), [catalog.validations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-validations-ssisdb-database), and [catalog.executions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database)</span></span>  
  
 <span data-ttu-id="5426f-106">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="5426f-106">**What do you want to do?**</span></span>  
  
1.  [<span data-ttu-id="5426f-107">打开 "活动操作" 对话框</span><span class="sxs-lookup"><span data-stu-id="5426f-107">Open the Active Operations Dialog Box</span></span>](#open_dialog)  
  
2.  [<span data-ttu-id="5426f-108">配置选项</span><span class="sxs-lookup"><span data-stu-id="5426f-108">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-active-operations-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="5426f-109">打开“活动操作”对话框</span><span class="sxs-lookup"><span data-stu-id="5426f-109">Open the Active Operations Dialog Box</span></span>  
  
1.  <span data-ttu-id="5426f-110">打开 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5426f-110">Open [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="5426f-111">连接 Microsoft SQL Server 数据库引擎</span><span class="sxs-lookup"><span data-stu-id="5426f-111">Connect Microsoft SQL Server Database Engine</span></span>  
  
3.  <span data-ttu-id="5426f-112">在对象资源管理器中，展开 **Integration Services** 节点，右键单击 **SSISDB**，然后单击 **“活动操作”** 。</span><span class="sxs-lookup"><span data-stu-id="5426f-112">In Object Explorer, expand the **Integration Services** node, right-click **SSISDB**, and then click **Active Operations**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="5426f-113">配置选项</span><span class="sxs-lookup"><span data-stu-id="5426f-113">Configure the Options</span></span>  
  
### <a name="options"></a><span data-ttu-id="5426f-114">选项</span><span class="sxs-lookup"><span data-stu-id="5426f-114">Options</span></span>  
 <span data-ttu-id="5426f-115">类型</span><span class="sxs-lookup"><span data-stu-id="5426f-115">**Type**</span></span>  
 <span data-ttu-id="5426f-116">指定操作的类型。</span><span class="sxs-lookup"><span data-stu-id="5426f-116">Specifies the type of operation.</span></span> <span data-ttu-id="5426f-117">下面是 "**类型**" 字段的可能值以及 transact-sql 视图的 "operations_type" 列中的相应值 `catalog.operations` 。</span><span class="sxs-lookup"><span data-stu-id="5426f-117">The following are the possible values for the **Type** field and the corresponding values in the operations_type column of the Transact-SQL `catalog.operations` view.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5426f-118">Integration Services 初始化</span><span class="sxs-lookup"><span data-stu-id="5426f-118">Integration Services initialization</span></span>|<span data-ttu-id="5426f-119">1</span><span class="sxs-lookup"><span data-stu-id="5426f-119">1</span></span>|  
|<span data-ttu-id="5426f-120">操作清除（SQL 代理作业）</span><span class="sxs-lookup"><span data-stu-id="5426f-120">Operations cleanup (SQL Agent job)</span></span>|<span data-ttu-id="5426f-121">2</span><span class="sxs-lookup"><span data-stu-id="5426f-121">2</span></span>|  
|<span data-ttu-id="5426f-122">项目版本清除（SQL 代理作业）</span><span class="sxs-lookup"><span data-stu-id="5426f-122">Project versions cleanup (SQL Agent job)</span></span>|<span data-ttu-id="5426f-123">3</span><span class="sxs-lookup"><span data-stu-id="5426f-123">3</span></span>|  
|<span data-ttu-id="5426f-124">部署项目</span><span class="sxs-lookup"><span data-stu-id="5426f-124">Deploy project</span></span>|<span data-ttu-id="5426f-125">101</span><span class="sxs-lookup"><span data-stu-id="5426f-125">101</span></span>|  
|<span data-ttu-id="5426f-126">还原项目</span><span class="sxs-lookup"><span data-stu-id="5426f-126">Restore project</span></span>|<span data-ttu-id="5426f-127">106</span><span class="sxs-lookup"><span data-stu-id="5426f-127">106</span></span>|  
|<span data-ttu-id="5426f-128">创建和启动包执行</span><span class="sxs-lookup"><span data-stu-id="5426f-128">Create and start package execution</span></span>|<span data-ttu-id="5426f-129">200</span><span class="sxs-lookup"><span data-stu-id="5426f-129">200</span></span>|  
|<span data-ttu-id="5426f-130">停止操作（停止验证或执行）</span><span class="sxs-lookup"><span data-stu-id="5426f-130">Stop operation (stopping a validation or execution</span></span>|<span data-ttu-id="5426f-131">202</span><span class="sxs-lookup"><span data-stu-id="5426f-131">202</span></span>|  
|<span data-ttu-id="5426f-132">验证项目</span><span class="sxs-lookup"><span data-stu-id="5426f-132">Validate project</span></span>|<span data-ttu-id="5426f-133">300</span><span class="sxs-lookup"><span data-stu-id="5426f-133">300</span></span>|  
|<span data-ttu-id="5426f-134">验证包</span><span class="sxs-lookup"><span data-stu-id="5426f-134">Validate package</span></span>|<span data-ttu-id="5426f-135">301</span><span class="sxs-lookup"><span data-stu-id="5426f-135">301</span></span>|  
|<span data-ttu-id="5426f-136">配置目录</span><span class="sxs-lookup"><span data-stu-id="5426f-136">Configure catalog</span></span>|<span data-ttu-id="5426f-137">1000</span><span class="sxs-lookup"><span data-stu-id="5426f-137">1000</span></span>|  
  
 <span data-ttu-id="5426f-138">**Stop**</span><span class="sxs-lookup"><span data-stu-id="5426f-138">**Stop**</span></span>  
 <span data-ttu-id="5426f-139">单击以停止当前正在运行的操作。</span><span class="sxs-lookup"><span data-stu-id="5426f-139">Click to stop a currently running operation.</span></span>  
  
  
