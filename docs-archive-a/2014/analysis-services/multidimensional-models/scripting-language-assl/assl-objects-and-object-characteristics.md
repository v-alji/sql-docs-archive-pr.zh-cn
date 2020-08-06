---
title: ASSL 对象和对象特征 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- reference exceptions [Analysis Services Scripting Language]
- ASSL, objects
- inheritance [Analysis Services Scripting Language]
- localized names [Analysis Services Scripting Language]
- objects [Analysis Services Scripting Language]
- names [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
- expansion [Analysis Services Scripting Language]
ms.assetid: 6e5c28b5-c0bc-4ccd-82e5-e174bbb71386
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76d57bb421a7f486983476a6549a5121ce88ee9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588722"
---
# <a name="assl-objects-and-object-characteristics"></a><span data-ttu-id="a74ec-102">ASSL 对象和对象特征</span><span class="sxs-lookup"><span data-stu-id="a74ec-102">ASSL Objects and Object Characteristics</span></span>
  <span data-ttu-id="a74ec-103">Analysis Services 脚本语言 (ASSL) 中的对象遵循关于对象组、继承、命名、扩展和处理的特定准则。</span><span class="sxs-lookup"><span data-stu-id="a74ec-103">Objects in Analysis Services Scripting Language (ASSL) follow specific guidelines in regards to object groups, inheritance, naming, expansion, and processing.</span></span>  
  
## <a name="object-groups"></a><span data-ttu-id="a74ec-104">对象组</span><span class="sxs-lookup"><span data-stu-id="a74ec-104">Object Groups</span></span>  
 <span data-ttu-id="a74ec-105">所有 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 对象均具有 XML 表示形式。</span><span class="sxs-lookup"><span data-stu-id="a74ec-105">All [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objects have an XML representation.</span></span> <span data-ttu-id="a74ec-106">这些对象分为以下两组：</span><span class="sxs-lookup"><span data-stu-id="a74ec-106">The objects are divided into two groups:</span></span>  
  
 <span data-ttu-id="a74ec-107">**主要对象**</span><span class="sxs-lookup"><span data-stu-id="a74ec-107">**Major objects**</span></span>  
 <span data-ttu-id="a74ec-108">可以单独创建、更改和删除主要对象。</span><span class="sxs-lookup"><span data-stu-id="a74ec-108">Major objects can be independently created, altered, and deleted.</span></span> <span data-ttu-id="a74ec-109">主要对象包括：</span><span class="sxs-lookup"><span data-stu-id="a74ec-109">Major objects include:</span></span>  
  
-   <span data-ttu-id="a74ec-110">服务器</span><span class="sxs-lookup"><span data-stu-id="a74ec-110">Servers</span></span>  
  
-   <span data-ttu-id="a74ec-111">数据库</span><span class="sxs-lookup"><span data-stu-id="a74ec-111">Databases</span></span>  
  
-   <span data-ttu-id="a74ec-112">维度</span><span class="sxs-lookup"><span data-stu-id="a74ec-112">Dimensions</span></span>  
  
-   <span data-ttu-id="a74ec-113">多维数据集</span><span class="sxs-lookup"><span data-stu-id="a74ec-113">Cubes</span></span>  
  
-   <span data-ttu-id="a74ec-114">度量值组</span><span class="sxs-lookup"><span data-stu-id="a74ec-114">Measure groups</span></span>  
  
-   <span data-ttu-id="a74ec-115">分区</span><span class="sxs-lookup"><span data-stu-id="a74ec-115">Partitions</span></span>  
  
-   <span data-ttu-id="a74ec-116">透视</span><span class="sxs-lookup"><span data-stu-id="a74ec-116">Perspectives</span></span>  
  
-   <span data-ttu-id="a74ec-117">挖掘模型</span><span class="sxs-lookup"><span data-stu-id="a74ec-117">Mining models</span></span>  
  
-   <span data-ttu-id="a74ec-118">角色</span><span class="sxs-lookup"><span data-stu-id="a74ec-118">Roles</span></span>  
  
-   <span data-ttu-id="a74ec-119">与服务器或数据库关联的命令</span><span class="sxs-lookup"><span data-stu-id="a74ec-119">Commands associated with a server or database</span></span>  
  
-   <span data-ttu-id="a74ec-120">数据源</span><span class="sxs-lookup"><span data-stu-id="a74ec-120">Data sources</span></span>  
  
 <span data-ttu-id="a74ec-121">主要对象具有以下可跟踪其历史记录和状态的属性。</span><span class="sxs-lookup"><span data-stu-id="a74ec-121">Major objects have the following properties to track their history and status.</span></span>  
  
-   `CreatedTimestamp`  
  
-   `LastSchemaUpdate`  
  
-   <span data-ttu-id="a74ec-122">`LastProcessed`（视具体情况而定）</span><span class="sxs-lookup"><span data-stu-id="a74ec-122">`LastProcessed` (where appropriate)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a74ec-123">作为主要对象的对象分类将影响 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例处理该对象的方式和以对象定义语言处理该对象的方式。</span><span class="sxs-lookup"><span data-stu-id="a74ec-123">The classification of an object as a major object affects how an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] treats that object and how that object is handled in the object definition language.</span></span> <span data-ttu-id="a74ec-124">但是，此分类不保证 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 管理和开发工具允许这些对象的独立创建、修改或删除。</span><span class="sxs-lookup"><span data-stu-id="a74ec-124">However, this classification does not guarantee that [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] management and development tools will allow the independent creation, modification, or deletion of these objects.</span></span>  
  
 <span data-ttu-id="a74ec-125">**次要对象**</span><span class="sxs-lookup"><span data-stu-id="a74ec-125">**Minor objects**</span></span>  
 <span data-ttu-id="a74ec-126">次要对象只能作为创建、更改或删除父级主要对象操作的组成部分进行创建、修改或删除。</span><span class="sxs-lookup"><span data-stu-id="a74ec-126">Minor objects can only be created, altered, or deleted as part of creating, altering, or deleting the parent major object.</span></span> <span data-ttu-id="a74ec-127">次要对象包括：</span><span class="sxs-lookup"><span data-stu-id="a74ec-127">Minor objects include:</span></span>  
  
-   <span data-ttu-id="a74ec-128">层次结构和级别</span><span class="sxs-lookup"><span data-stu-id="a74ec-128">Hierarchies and levels</span></span>  
  
-   <span data-ttu-id="a74ec-129">属性</span><span class="sxs-lookup"><span data-stu-id="a74ec-129">Attributes</span></span>  
  
-   <span data-ttu-id="a74ec-130">度量值</span><span class="sxs-lookup"><span data-stu-id="a74ec-130">Measures</span></span>  
  
-   <span data-ttu-id="a74ec-131">挖掘模型列</span><span class="sxs-lookup"><span data-stu-id="a74ec-131">Mining model columns</span></span>  
  
-   <span data-ttu-id="a74ec-132">与多维数据集关联的命令</span><span class="sxs-lookup"><span data-stu-id="a74ec-132">Commands associated with a cube</span></span>  
  
-   <span data-ttu-id="a74ec-133">聚合</span><span class="sxs-lookup"><span data-stu-id="a74ec-133">Aggregations</span></span>  
  
## <a name="object-expansion"></a><span data-ttu-id="a74ec-134">对象扩展</span><span class="sxs-lookup"><span data-stu-id="a74ec-134">Object Expansion</span></span>  
 <span data-ttu-id="a74ec-135">`ObjectExpansion` 限制可用于控制服务器返回的 ASSL XML 扩展的程度。</span><span class="sxs-lookup"><span data-stu-id="a74ec-135">The `ObjectExpansion` restriction can be used to control the degree of expansion of ASSL XML returned by the server.</span></span> <span data-ttu-id="a74ec-136">此限制具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="a74ec-136">This restriction has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="a74ec-137">枚举值</span><span class="sxs-lookup"><span data-stu-id="a74ec-137">Enumeration value</span></span>|<span data-ttu-id="a74ec-138">允许用于\<Alter></span><span class="sxs-lookup"><span data-stu-id="a74ec-138">Allowed for \<Alter></span></span>|<span data-ttu-id="a74ec-139">说明</span><span class="sxs-lookup"><span data-stu-id="a74ec-139">Description</span></span>|  
|-----------------------|---------------------------|-----------------|  
|<span data-ttu-id="a74ec-140">*ReferenceOnly*</span><span class="sxs-lookup"><span data-stu-id="a74ec-140">*ReferenceOnly*</span></span>|<span data-ttu-id="a74ec-141">否</span><span class="sxs-lookup"><span data-stu-id="a74ec-141">no</span></span>|<span data-ttu-id="a74ec-142">只返回请求对象以及以递归方式包含的所有主要对象的名称、ID 和时间戳。</span><span class="sxs-lookup"><span data-stu-id="a74ec-142">Returns only the name, ID, and timestamp for the requested object and for all contained major objects recursively.</span></span>|  
|<span data-ttu-id="a74ec-143">*ObjectProperties*</span><span class="sxs-lookup"><span data-stu-id="a74ec-143">*ObjectProperties*</span></span>|<span data-ttu-id="a74ec-144">是</span><span class="sxs-lookup"><span data-stu-id="a74ec-144">yes</span></span>|<span data-ttu-id="a74ec-145">展开请求的对象和次要包含对象，但不返回主要包含对象。</span><span class="sxs-lookup"><span data-stu-id="a74ec-145">Expands the requested object and minor contained objects, but does not return major contained objects.</span></span>|  
|<span data-ttu-id="a74ec-146">*ExpandObject*</span><span class="sxs-lookup"><span data-stu-id="a74ec-146">*ExpandObject*</span></span>|<span data-ttu-id="a74ec-147">否</span><span class="sxs-lookup"><span data-stu-id="a74ec-147">no</span></span>|<span data-ttu-id="a74ec-148">与*ObjectProperties*相同，但还返回包含的主要对象的名称、ID 和时间戳。</span><span class="sxs-lookup"><span data-stu-id="a74ec-148">Same as *ObjectProperties*, but also returns the name, ID, and timestamp for contained major objects.</span></span>|  
|<span data-ttu-id="a74ec-149">*Updateoptions.expandfull*</span><span class="sxs-lookup"><span data-stu-id="a74ec-149">*ExpandFull*</span></span>|<span data-ttu-id="a74ec-150">是</span><span class="sxs-lookup"><span data-stu-id="a74ec-150">yes</span></span>|<span data-ttu-id="a74ec-151">完全展开请求的对象以及所有以递归方式包含的对象。</span><span class="sxs-lookup"><span data-stu-id="a74ec-151">Fully expands the requested object and all contained objects recursively.</span></span>|  
  
 <span data-ttu-id="a74ec-152">此 ASSL 参考部分介绍了*updateoptions.expandfull*的表示形式。</span><span class="sxs-lookup"><span data-stu-id="a74ec-152">This ASSL reference section describes the *ExpandFull* representation.</span></span> <span data-ttu-id="a74ec-153">所有其他 `ObjectExpansion` 级别都派生自此级别。</span><span class="sxs-lookup"><span data-stu-id="a74ec-153">All other `ObjectExpansion` levels are derived from this level.</span></span>  
  
## <a name="object-processing"></a><span data-ttu-id="a74ec-154">对象处理</span><span class="sxs-lookup"><span data-stu-id="a74ec-154">Object Processing</span></span>  
 <span data-ttu-id="a74ec-155">ASSL 包含只读元素或属性（例如 `LastProcessed`），这些元素或属性可从 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例读取，但在向该实例提交命令脚本时将被忽略。</span><span class="sxs-lookup"><span data-stu-id="a74ec-155">ASSL includes read-only elements or properties (for example, `LastProcessed`) that can be read from the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance, but which are omitted when command scripts are submitted to the instance.</span></span> [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="a74ec-156">忽略只读元素的已修改值，并且不发出警告或错误。</span><span class="sxs-lookup"><span data-stu-id="a74ec-156">ignores modified values for read-only elements without warning or error.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="a74ec-157">还会忽略不适当或不相关的属性，并且不会引发验证错误。</span><span class="sxs-lookup"><span data-stu-id="a74ec-157">also ignores inappropriate or irrelevant properties without raising validation errors.</span></span> <span data-ttu-id="a74ec-158">例如，X 元素只应在 Y 元素有特定值时才存在。</span><span class="sxs-lookup"><span data-stu-id="a74ec-158">For example, the X element should only be present when the Y element has a particular value.</span></span> <span data-ttu-id="a74ec-159">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例忽略 X 元素，而不会根据 Y 元素的值验证该元素。</span><span class="sxs-lookup"><span data-stu-id="a74ec-159">The [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance ignores the X element instead of validating that element against the value of the Y element.</span></span>  
  
  
