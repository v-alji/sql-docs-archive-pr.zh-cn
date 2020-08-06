---
title: 授予对维度 (Analysis Services) 的权限 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.dimensions.f1
helpviewer_keywords:
- dimensions [Analysis Services], security
- read/write permissions
- user access rights [Analysis Services], dimensions
- permissions [Analysis Services], dimensions
ms.assetid: be5b2746-0336-4b12-827e-131462bdf605
author: minewiskan
ms.author: owend
ms.openlocfilehash: 735a272cd01e29877c466cc228d1ec340484f995
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682408"
---
# <a name="grant-permissions-on-a-dimension-analysis-services"></a><span data-ttu-id="7b625-102">授予维度的权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="7b625-102">Grant permissions on a dimension (Analysis Services)</span></span>
  <span data-ttu-id="7b625-103">维度安全用于设置维度对象（而非其数据）的权限。</span><span class="sxs-lookup"><span data-stu-id="7b625-103">Dimension security is used to set permissions on a dimension object, not its data.</span></span> <span data-ttu-id="7b625-104">通常，允许或拒绝访问处理操作是在设置维度权限时的主要目标。</span><span class="sxs-lookup"><span data-stu-id="7b625-104">Typically, allowing or denying access to processing operations is the main objective when setting permissions on a dimension.</span></span>  
  
 <span data-ttu-id="7b625-105">但是，也许你的目标不是控制处理操作，而是控制维度的数据访问或其包含的属性和层次结构。</span><span class="sxs-lookup"><span data-stu-id="7b625-105">But perhaps your objective is not to control processing operations, but rather data access to a dimension, or the attributes and hierarchies it contains.</span></span> <span data-ttu-id="7b625-106">例如，具有不同地区销售部门的公司可能想要部门外人员不得接触销售绩效信息。</span><span class="sxs-lookup"><span data-stu-id="7b625-106">For example, a company with regional sales divisions might want to make sales performance information off limits to those outside the division.</span></span> <span data-ttu-id="7b625-107">为了允许或拒绝不同组成人员访问某部分的维度数据，可以对属性和维度成员设置权限。</span><span class="sxs-lookup"><span data-stu-id="7b625-107">To allow or deny access to portions of dimension data for different constituents, you can set permissions on dimension attributes and dimension members.</span></span> <span data-ttu-id="7b625-108">请注意，你无法拒绝对单个维度对象本身的访问，仅可拒绝对其数据的访问。</span><span class="sxs-lookup"><span data-stu-id="7b625-108">Notice that you cannot deny access to an individual dimension object itself, only to its data.</span></span> <span data-ttu-id="7b625-109">如果近期目标是允许或拒绝访问维度中的成员（包括对单个属性结构层次的访问权限），请参阅 [授予对维度数据的自定义访问权限 (Analysis Services)](grant-custom-access-to-dimension-data-analysis-services.md) 了解更多信息。</span><span class="sxs-lookup"><span data-stu-id="7b625-109">If your immediate goal is to allow or deny access to members in a dimension, including access rights to individual attribute hierarchies, see [Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) for more information.</span></span>  
  
 <span data-ttu-id="7b625-110">本主题的剩余部分包含对维度对象本身设置的权限，其中包括：</span><span class="sxs-lookup"><span data-stu-id="7b625-110">The remainder of this topic covers permissions that you can set on the dimension object itself, including:</span></span>  
  
-   <span data-ttu-id="7b625-111">读取或读/写权限（只可从读取或读/写选择；指定“无”不是选项）。</span><span class="sxs-lookup"><span data-stu-id="7b625-111">Read or Read/Write permissions (you can only choose from Read or Read/Write; specifying "none" is not an option).</span></span> <span data-ttu-id="7b625-112">如上所述，如果目标是限制对维度数据的访问权限，请参阅 [授予对维度数据的自定义访问权限 (Analysis Services)](grant-custom-access-to-dimension-data-analysis-services.md) 了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="7b625-112">As noted, if your goal is to restrict access to dimension data, see [Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) for details.</span></span>  
  
-   <span data-ttu-id="7b625-113">处理权限（当方案要求需要对单独的对象设置自定义权限的处理策略时，执行此项）</span><span class="sxs-lookup"><span data-stu-id="7b625-113">Processing permissions (do this when scenarios require a processing strategy that calls for custom permissions on individual objects)</span></span>  
  
-   <span data-ttu-id="7b625-114">读取定义权限（通常要支持工具中的交互式处理或对模型提供可见性时将会执行此项。</span><span class="sxs-lookup"><span data-stu-id="7b625-114">Read definition permissions (typically you would do this to support interactive processing in a tool, or to provide visibility into a model.</span></span> <span data-ttu-id="7b625-115">读取定义可以让你在没有维度数据的访问权限或无法修改其定义时看见维度的结构。）</span><span class="sxs-lookup"><span data-stu-id="7b625-115">Read definition lets you see the structure of a dimension, without permission to its data or the ability to modify its definition).</span></span>  
  
 <span data-ttu-id="7b625-116">在为维度定义角色时，可用维度根据对象是否为（位于数据库内部但在多维数据集外部的）独立数据库维度还是为多维数据集维度而变化。</span><span class="sxs-lookup"><span data-stu-id="7b625-116">When defining roles for a dimension, available permissions vary depending on whether the object is a standalone database dimension ─internal to the database but external to a cube─ or a cube dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b625-117">默认情况下，数据库维度的权限由多维数据集维度继承。</span><span class="sxs-lookup"><span data-stu-id="7b625-117">By default, permissions on a database dimension are inherited by a cube dimension.</span></span> <span data-ttu-id="7b625-118">例如，如果启用“客户”数据库维度上的“读/写”权限，则“客户”多维数据集继承当前角色上下文的“读/写”权限\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b625-118">For example, if you enable **Read/Write** on a Customer database dimension, the Customer cube dimension inherits **Read/Write** in the context of the current role.</span></span> <span data-ttu-id="7b625-119">如果要覆盖权限设置，则可以清除继承的权限。</span><span class="sxs-lookup"><span data-stu-id="7b625-119">You can clear inherited permissions if you want to override a permission setting.</span></span>  
  
## <a name="set-permissions-on-a-database-dimension"></a><span data-ttu-id="7b625-120">设置数据库维度权限</span><span class="sxs-lookup"><span data-stu-id="7b625-120">Set permissions on a database dimension</span></span>  
 <span data-ttu-id="7b625-121">数据库维度是数据库内的独立对象，允许在相同模型内重复使用维度。</span><span class="sxs-lookup"><span data-stu-id="7b625-121">Database dimensions are standalone objects within a database, allowing for dimension reuse within the same model.</span></span> <span data-ttu-id="7b625-122">请考虑在模型中多次使用的“日期”数据库维度，如 Order Date、Ship Date 和 Due Date 多维数据集维度。</span><span class="sxs-lookup"><span data-stu-id="7b625-122">Consider a DATE database dimension that is used multiple times in a model, as Order Date, Ship Date, and Due Date cube dimensions.</span></span> <span data-ttu-id="7b625-123">因为多维数据集维度和数据库维度为数据库中的同等对象，所以可以独立设置每个对象的处理权限。</span><span class="sxs-lookup"><span data-stu-id="7b625-123">Because cubes and database dimensions are peer objects in a database, you can set processing permissions independently on each object.</span></span>  
  
1.  <span data-ttu-id="7b625-124">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，连接到实例 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，在对象资源管理器中展开相应数据库的 "**角色**"，然后单击 "数据库角色" (或 "创建新的数据库角色) "。</span><span class="sxs-lookup"><span data-stu-id="7b625-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand **Roles** for the appropriate database in Object Explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="7b625-125">在“维度” \*\*\*\* 窗格中，维度集应该设置为“所有数据库维度” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b625-125">In the **Dimensions** pane, the dimension set should be set to **All database dimensions**.</span></span>  
  
     <span data-ttu-id="7b625-126">默认情况下，权限设置为“读取” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b625-126">By default, permissions are set to **Read**.</span></span>  
  
     <span data-ttu-id="7b625-127">尽管“读/写”\*\*\*\* 权限可用，但我们推荐不要使用此权限。</span><span class="sxs-lookup"><span data-stu-id="7b625-127">Although **Read/Write** is available, we recommend that you do not use this permission.</span></span> <span data-ttu-id="7b625-128">“读/写”\*\*\*\* 用于维度写回情形下，而这已不推荐使用。</span><span class="sxs-lookup"><span data-stu-id="7b625-128">**Read/Write** is used for dimension writeback scenarios, which have been deprecated.</span></span> <span data-ttu-id="7b625-129">请参阅[SQL Server 2014 中不推荐使用的 Analysis Services 功能](../deprecated-analysis-services-features-in-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="7b625-129">See [Deprecated Analysis Services Features in SQL Server 2014](../deprecated-analysis-services-features-in-sql-server-2014.md).</span></span>  
  
     <span data-ttu-id="7b625-130">此外，还可以对单独的维度对象设置“读取定义” \*\*\*\* 和“处理” \*\*\*\* 权限，前提是这些权限还未在数据库级别进行设置。</span><span class="sxs-lookup"><span data-stu-id="7b625-130">Optionally, you can set **Read Definition** and **Process** permissions on individual dimension objects, as long as those permissions are not already set at the database level.</span></span> <span data-ttu-id="7b625-131">请参阅[授予处理权限 (Analysis Services)](grant-process-permissions-analysis-services.md) 和[授予对象元数据的读取定义权限 (Analysis Services)](grant-read-definition-permissions-on-object-metadata-analysis-services.md) 获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="7b625-131">See [Grant process permissions &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md) and [Grant read definition permissions on object metadata &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md) for details.</span></span>  
  
## <a name="set-permissions-on-a-cube-dimension"></a><span data-ttu-id="7b625-132">设置多维数据集维度权限</span><span class="sxs-lookup"><span data-stu-id="7b625-132">Set permissions on a cube dimension</span></span>  
 <span data-ttu-id="7b625-133">多维数据集维度是已添加到多维数据集的数据库维度。</span><span class="sxs-lookup"><span data-stu-id="7b625-133">Cube dimensions are database dimensions that have been added to a cube.</span></span> <span data-ttu-id="7b625-134">因此，其在结构上依赖于关联的度量值组。</span><span class="sxs-lookup"><span data-stu-id="7b625-134">As such, they are structurally dependent on associated measure groups.</span></span> <span data-ttu-id="7b625-135">虽然可以在授权方面自动处理这些对象，但将多维数据集和多维数据集维度作为一个整体才有意义。</span><span class="sxs-lookup"><span data-stu-id="7b625-135">Although you can process these objects atomically, in terms of authorization, it makes sense to treat the cube and cube dimensions as a single entity.</span></span>  
  
1.  <span data-ttu-id="7b625-136">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，连接到实例 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，在对象资源管理器中展开相应数据库的 "**角色**"，然后单击 "数据库角色" (或 "创建新的数据库角色) "。</span><span class="sxs-lookup"><span data-stu-id="7b625-136">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand **Roles** for the appropriate database in Object Explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="7b625-137">在 "**维度**" 窗格中，将维度集更改为 " \<cube-name> **多维数据集维度**"。</span><span class="sxs-lookup"><span data-stu-id="7b625-137">In the **Dimensions** pane, change the dimension set to \<cube-name> **cube dimensions**.</span></span>  
  
     <span data-ttu-id="7b625-138">默认情况下，权限继承自相应的数据库维度。</span><span class="sxs-lookup"><span data-stu-id="7b625-138">By default, permissions are inherited from a corresponding database dimension.</span></span> <span data-ttu-id="7b625-139">清除“继承”复选框，将权限从“读取”更改为“读/写”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b625-139">Clear the **Inherit** check box to alter permissions from **Read** to **Read/Write**.</span></span> <span data-ttu-id="7b625-140">在使用“读/写”权限之前\*\*\*\*，请务必阅读上一节中的备注。</span><span class="sxs-lookup"><span data-stu-id="7b625-140">Before using **Read/Write**, be sure to read the note in the previous section.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7b625-141">如果使用分析管理对象 (AMO) 配置数据库角色权限，那么，任何对多维数据集的 DimensionPermission 属性中多维数据集维度的引用都将切断对数据库的 DimensionPermission 属性的权限继承。</span><span class="sxs-lookup"><span data-stu-id="7b625-141">If you configure database role permissions by using Analysis Management Objects (AMO), any reference to a cube dimension in a cube's DimensionPermission attribute severs the permission inheritance from the database's DimensionPermission attribute.</span></span> <span data-ttu-id="7b625-142">有关 AMO 的详细信息，请参阅[使用分析管理对象 (AMO) 进行开发](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)。</span><span class="sxs-lookup"><span data-stu-id="7b625-142">For more information about AMO, see [Developing with Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b625-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7b625-143">See Also</span></span>  
 <span data-ttu-id="7b625-144">[角色和权限 &#40;Analysis Services&#41;](roles-and-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="7b625-144">[Roles and Permissions &#40;Analysis Services&#41;](roles-and-permissions-analysis-services.md) </span></span>  
 <span data-ttu-id="7b625-145">[&#40;Analysis Services 授予多维数据集或模型权限&#41;](grant-cube-or-model-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="7b625-145">[Grant cube or model permissions &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md) </span></span>  
 <span data-ttu-id="7b625-146">[授予对数据挖掘结构和模型的权限 &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="7b625-146">[Grant permissions on data mining structures and models &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md) </span></span>  
 <span data-ttu-id="7b625-147">[授予对维度数据的自定义访问 &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="7b625-147">[Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) </span></span>  
 [<span data-ttu-id="7b625-148">授予单元数据的自定义访问权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="7b625-148">Grant custom access to cell data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-cell-data-analysis-services.md)  
  
  
