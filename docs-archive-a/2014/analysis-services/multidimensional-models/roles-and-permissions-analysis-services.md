---
title: 角色和权限 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], about security
- security [Analysis Services - multidimensional data], about security
ms.assetid: bb885447-868b-4686-853c-8241f63d4370
author: minewiskan
ms.author: owend
ms.openlocfilehash: d6595d931b2c2760e5fd3013ff6bec88f85106d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694609"
---
# <a name="roles-and-permissions-analysis-services"></a><span data-ttu-id="6ec74-102">角色和权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6ec74-102">Roles and Permissions (Analysis Services)</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="6ec74-103">提供基于角色的授权模型，该模型授予对操作、对象和数据的访问权限。</span><span class="sxs-lookup"><span data-stu-id="6ec74-103">provides a role-based authorization model that grants access to operations, objects, and data.</span></span> <span data-ttu-id="6ec74-104">访问 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例或数据库的所有用户都必须在某一角色范畴内执行操作。</span><span class="sxs-lookup"><span data-stu-id="6ec74-104">All users who access an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance or database must do so within the context of a role.</span></span>  
  
 <span data-ttu-id="6ec74-105">作为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 系统管理员，你将负责将成员身份授予 **服务器管理员角色** ，从而提供对服务器上的操作不受限制的访问权限。</span><span class="sxs-lookup"><span data-stu-id="6ec74-105">As an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] system administrator, you are in charge of granting membership to the **server administrator role** that conveys unrestricted access to operations on the server.</span></span> <span data-ttu-id="6ec74-106">此角色具有固定权限，不能自定义。</span><span class="sxs-lookup"><span data-stu-id="6ec74-106">This role has fixed permissions and cannot be customized.</span></span> <span data-ttu-id="6ec74-107">默认情况下，本地 Administrators 组的成员将自动是 Analysis Services 系统管理员。</span><span class="sxs-lookup"><span data-stu-id="6ec74-107">By default, members of the local Administrators group are automatically Analysis Services system administrators.</span></span>  
  
 <span data-ttu-id="6ec74-108">执行查询或处理数据的非管理用户通过 **数据库角色**获得访问权限。</span><span class="sxs-lookup"><span data-stu-id="6ec74-108">Non-administrative users who query or process data are granted access through **database roles**.</span></span> <span data-ttu-id="6ec74-109">系统管理员和数据库管理员都可以创建描述给定数据库内不同访问级别的角色，然后将成员身份分配给要求访问的每个用户。</span><span class="sxs-lookup"><span data-stu-id="6ec74-109">Both system administrators and database administrators can create the roles that describe different levels of access within a given database, and then assign membership to every user who requires access.</span></span> <span data-ttu-id="6ec74-110">每个角色都有一组自定义的权限，用于访问特定数据库内的对象和操作。</span><span class="sxs-lookup"><span data-stu-id="6ec74-110">Each role has a customized set of permissions for accessing objects and operations within a particular database.</span></span> <span data-ttu-id="6ec74-111">您可以在以下级别分配权限：数据库、内部对象（例如多维数据集和维度，但不包括透视）和行。</span><span class="sxs-lookup"><span data-stu-id="6ec74-111">You can assign permissions at these levels: database, interior objects such as cubes and dimensions (but not perspectives), and rows.</span></span>  
  
 <span data-ttu-id="6ec74-112">创建角色和分配成员身份通常将作为单独的操作。</span><span class="sxs-lookup"><span data-stu-id="6ec74-112">It is common practice to create roles and assign membership as separate operations.</span></span> <span data-ttu-id="6ec74-113">通常情况下，模型设计者在设计阶段添加角色。</span><span class="sxs-lookup"><span data-stu-id="6ec74-113">Often, the model designer adds roles during the design phase.</span></span> <span data-ttu-id="6ec74-114">这样，所有角色定义都将反映在定义该模型的项目文件中。</span><span class="sxs-lookup"><span data-stu-id="6ec74-114">This way, all role definitions are reflected in the project files that define the model.</span></span> <span data-ttu-id="6ec74-115">角色成员身份通常在以后在数据库进入生产阶段时实现，并且通常由创建了可被开发、测试和作为独立操作运行的脚本的数据库管理员执行。</span><span class="sxs-lookup"><span data-stu-id="6ec74-115">Role membership is typically rolled out later as the database moves into production, usually by database administrators who create scripts that can be developed, tested, and run as an independent operation.</span></span>  
  
 <span data-ttu-id="6ec74-116">所有授权都基于有效的 Windows 用户标识。</span><span class="sxs-lookup"><span data-stu-id="6ec74-116">All authorization is predicated on a valid Windows user identity.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="6ec74-117">使用专用于验证用户身份的 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="6ec74-117">uses Windows authentication exclusively to authenticate user identities.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="6ec74-118">不提供专有身份验证方法。请参阅[Analysis Services 支持的身份验证方法](../instances/authentication-methodologies-supported-by-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6ec74-118">provides no proprietary authentication method.See [Authentication methodologies supported by Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6ec74-119">在数据库中的所有角色中，对于每个 Windows 用户或组，权限都是可以累加的。</span><span class="sxs-lookup"><span data-stu-id="6ec74-119">Permissions are additive for each Windows user or group, across all roles in the database.</span></span> <span data-ttu-id="6ec74-120">如果某个角色拒绝用户或用户组执行特定任务或查看特定数据的权限，但是另一个角色为该用户或用户组授予相应的执行或查看权限，则该用户或用户组将具有执行任务或查看数据的权限。</span><span class="sxs-lookup"><span data-stu-id="6ec74-120">If one role denies a user or group permission to perform certain tasks or view certain data, but another role grants this permission to that user or group, the user or group will have permission to perform the task or view the data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ec74-121">本节内容</span><span class="sxs-lookup"><span data-stu-id="6ec74-121">In this section</span></span>  
  
-   [<span data-ttu-id="6ec74-122">授予对对象和操作的访问权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6ec74-122">Authorizing access to objects and operations &#40;Analysis Services&#41;</span></span>](authorizing-access-to-objects-and-operations-analysis-services.md)  
  
-   [<span data-ttu-id="6ec74-123">授予数据库权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6ec74-123">Grant database permissions &#40;Analysis Services&#41;</span></span>](grant-database-permissions-analysis-services.md)  
  
-   [<span data-ttu-id="6ec74-124">授予多维数据集或模型权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6ec74-124">Grant cube or model permissions &#40;Analysis Services&#41;</span></span>](grant-cube-or-model-permissions-analysis-services.md)  
  
-   [<span data-ttu-id="6ec74-125">授予处理权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6ec74-125">Grant process permissions &#40;Analysis Services&#41;</span></span>](grant-process-permissions-analysis-services.md)  
  
-   [<span data-ttu-id="6ec74-126">授予对象元数据的读取定义权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6ec74-126">Grant read definition permissions on object metadata &#40;Analysis Services&#41;</span></span>](grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
-   [<span data-ttu-id="6ec74-127">授予数据源对象的权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6ec74-127">Grant permissions on a data source object &#40;Analysis Services&#41;</span></span>](grant-permissions-on-a-data-source-object-analysis-services.md)  
  
-   [<span data-ttu-id="6ec74-128">授予数据挖掘结构和模型的权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6ec74-128">Grant permissions on data mining structures and models &#40;Analysis Services&#41;</span></span>](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)  
  
-   [<span data-ttu-id="6ec74-129">授予维度的权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6ec74-129">Grant permissions on a dimension &#40;Analysis Services&#41;</span></span>](grant-permissions-on-a-dimension-analysis-services.md)  
  
-   [<span data-ttu-id="6ec74-130">授予对维度数据的自定义访问权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6ec74-130">Grant custom access to dimension data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-dimension-data-analysis-services.md)  
  
-   [<span data-ttu-id="6ec74-131">授予单元数据的自定义访问权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6ec74-131">Grant custom access to cell data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-cell-data-analysis-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="6ec74-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ec74-132">See Also</span></span>  
 [<span data-ttu-id="6ec74-133">创建和管理角色（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="6ec74-133">Create and Manage Roles &#40;SSAS Tabular&#41;</span></span>](../tabular-models/roles-ssas-tabular.md)  
  
  
