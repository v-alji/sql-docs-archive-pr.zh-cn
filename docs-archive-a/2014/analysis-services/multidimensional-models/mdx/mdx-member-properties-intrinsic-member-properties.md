---
title: MDX)  (内部成员属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- intrinsic member properties [MDX]
ms.assetid: 84e6fe64-9b37-4e79-bedf-ae02e80bfce8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 268203d044734bb4e6a1d2acf6311ee7ef828a53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689055"
---
# <a name="intrinsic-member-properties-mdx"></a><span data-ttu-id="186f5-102">内部成员属性 (MDX)</span><span class="sxs-lookup"><span data-stu-id="186f5-102">Intrinsic Member Properties (MDX)</span></span>
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="186f5-103">公开您可以包含在查询中的维度成员的内部属性，以返回要在自定义应用程序中使用的额外数据或元数据，或帮助进行模型调查或构建。</span><span class="sxs-lookup"><span data-stu-id="186f5-103">exposes intrinsic properties on dimension members that you can include in a query to return additional data or metadata for use in a custom application, or to assist in model investigation or construction.</span></span> <span data-ttu-id="186f5-104">如果您正在使用 SQL Server 客户端工具，可以在 SQL Server Management Studio (SSMS) 中查看内部属性。</span><span class="sxs-lookup"><span data-stu-id="186f5-104">If you are using the SQL Server client tools, you can view intrinsic properties in SQL Server Management Studio (SSMS).</span></span>  
  
 <span data-ttu-id="186f5-105">内部属性包括 `ID`、`KEY`、`KEYx` 和 `NAME`，这些是每个成员在任意级别公开的属性。</span><span class="sxs-lookup"><span data-stu-id="186f5-105">Intrinsic properties include `ID`, `KEY`, `KEYx`, and `NAME`, which are properties exposed by every member, at any level.</span></span> <span data-ttu-id="186f5-106">您还可以返回位置信息，如 `LEVEL_NUMBER` 或 `PARENT_UNIQUE_NAME` 等等。</span><span class="sxs-lookup"><span data-stu-id="186f5-106">You can also return positional information, such as `LEVEL_NUMBER` or `PARENT_UNIQUE_NAME`, among others.</span></span>  
  
 <span data-ttu-id="186f5-107">根据您构造查询的方式和用于执行查询的客户端应用程序，成员属性在结果集中可能是可见的，也可能是不可见的。</span><span class="sxs-lookup"><span data-stu-id="186f5-107">Depending on how you construct the query, and on the client application you are using to execute queries, member properties may or may not be visible in the result set.</span></span> <span data-ttu-id="186f5-108">如果您正在使用 SQL Server Management Studio 测试或运行查询，可以双击结果集中的某个成员以打开“成员属性”对话框，显示每个内部成员属性的值。</span><span class="sxs-lookup"><span data-stu-id="186f5-108">If you are using SQL Server Management Studio to test or run queries, you can double-click a member in the result set to open the Member Properties dialog box, showing the values for each intrinsic member property.</span></span>  
  
 <span data-ttu-id="186f5-109">有关如何使用和查看维度成员属性的说明，请参阅 [在 SSMS 的“MDX 查询”窗口中查看 SSAS 成员属性](https://go.microsoft.com/fwlink/?LinkId=317362)。</span><span class="sxs-lookup"><span data-stu-id="186f5-109">For an introduction to using and viewing dimension member properties, see [Viewing SSAS Member Properties within an MDX Query Window in SSMS](https://go.microsoft.com/fwlink/?LinkId=317362).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="186f5-110">作为与1999年3月 (2.6) 的 OLE DB 规范的 OLAP 部分兼容的提供程序， [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 支持本主题中列出的内部成员属性。</span><span class="sxs-lookup"><span data-stu-id="186f5-110">As a provider that is compliant with the OLAP section of the OLE DB specification dated March 1999 (2.6), [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supports the intrinsic member properties listed in this topic.</span></span>  
>   
>  <span data-ttu-id="186f5-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 以外的提供程序可能支持其他内部成员属性。</span><span class="sxs-lookup"><span data-stu-id="186f5-111">Providers other than [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] may support additional intrinsic member properties.</span></span> <span data-ttu-id="186f5-112">有关其他访问接口支持的内部成员属性的详细信息，请参阅这些访问接口附带的文档。</span><span class="sxs-lookup"><span data-stu-id="186f5-112">For more information about the intrinsic member properties supported by other providers, refer to the documentation that comes with those providers.</span></span>  
  
## <a name="types-of-member-properties"></a><span data-ttu-id="186f5-113">成员属性的类型</span><span class="sxs-lookup"><span data-stu-id="186f5-113">Types of Member Properties</span></span>  
 <span data-ttu-id="186f5-114">支持的内部成员属性 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 有两种类型：</span><span class="sxs-lookup"><span data-stu-id="186f5-114">The intrinsic member properties supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] are of two types:</span></span>  
  
 <span data-ttu-id="186f5-115">上下文相关的成员属性</span><span class="sxs-lookup"><span data-stu-id="186f5-115">Context sensitive member properties</span></span>  
 <span data-ttu-id="186f5-116">这些成员属性必须在特定层次结构或级别的上下文中使用，用于为指定维度或级别的每个成员提供值。</span><span class="sxs-lookup"><span data-stu-id="186f5-116">These member properties must be used in the context of a specific hierarchy or level, and supply values for each member of the specified dimension or level.</span></span>  
  
 <span data-ttu-id="186f5-117">请注意以下示例如何包括 `KEY` 属性的路径：`MEMBER [Measures].[Parent Member Key] AS [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")`。</span><span class="sxs-lookup"><span data-stu-id="186f5-117">Notice how the following example includes the path for the `KEY` property: `MEMBER [Measures].[Parent Member Key] AS [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")`.</span></span>  
  
 <span data-ttu-id="186f5-118">非上下文相关的成员属性</span><span class="sxs-lookup"><span data-stu-id="186f5-118">Non-context sensitive member properties</span></span>  
 <span data-ttu-id="186f5-119">这些成员属性不能在特定维度或级别的上下文中使用，而是为某个轴上的所有成员返回值。</span><span class="sxs-lookup"><span data-stu-id="186f5-119">These member properties cannot be used in the context of a specific dimension or level, and return values for all members on an axis.</span></span>  
  
 <span data-ttu-id="186f5-120">与上下文不相关的属性是独立的，不包括路径信息：</span><span class="sxs-lookup"><span data-stu-id="186f5-120">Context-insensitive properties standalone and do not include path information.</span></span> <span data-ttu-id="186f5-121">请注意在以下示例中没有为 `PARENT_UNIQUE_NAME` 指定任何维度或级别：`DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS`</span><span class="sxs-lookup"><span data-stu-id="186f5-121">Notice how there is no dimension or level specified for `PARENT_UNIQUE_NAME` in the following example: `DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS`</span></span>  
  
 <span data-ttu-id="186f5-122">不论内部成员属性是否是上下文相关的，都应遵循下列使用规则：</span><span class="sxs-lookup"><span data-stu-id="186f5-122">Regardless of whether the intrinsic member property is context sensitive or not, the following usage rules apply:</span></span>  
  
-   <span data-ttu-id="186f5-123">只能指定与投影在轴上的维度成员相关的那些内部成员属性。</span><span class="sxs-lookup"><span data-stu-id="186f5-123">You can specify only those intrinsic member properties that relate to dimension members that are projected on the axis.</span></span>  
  
-   <span data-ttu-id="186f5-124">可以在同一查询中同时包含对上下文相关成员属性和非上下文相关内部成员属性的请求。</span><span class="sxs-lookup"><span data-stu-id="186f5-124">You can mix requests for context sensitive member properties in the same query with non-context sensitive intrinsic member properties.</span></span>  
  
-   <span data-ttu-id="186f5-125">使用 `PROPERTIES` 关键字查询属性。</span><span class="sxs-lookup"><span data-stu-id="186f5-125">You use the `PROPERTIES` keyword to query for the properties.</span></span>  
  
 <span data-ttu-id="186f5-126">以下各节介绍中提供的各种上下文相关和非上下文相关内部成员属性 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ，以及如何将关键字用于每种 `PROPERTIES` 类型的属性。</span><span class="sxs-lookup"><span data-stu-id="186f5-126">The following sections describe both the various context sensitive and non-context sensitive intrinsic member properties available in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], and how to use the `PROPERTIES` keyword with each type of property.</span></span>  
  
## <a name="context-sensitive-member-properties"></a><span data-ttu-id="186f5-127">上下文相关的成员属性</span><span class="sxs-lookup"><span data-stu-id="186f5-127">Context Sensitive Member Properties</span></span>  
 <span data-ttu-id="186f5-128">所有维度成员和级别成员都支持一列上下文相关的内部成员属性。</span><span class="sxs-lookup"><span data-stu-id="186f5-128">All dimension members and level members support a list of intrinsic member properties that are context sensitive.</span></span> <span data-ttu-id="186f5-129">下表列出了这些上下文相关的属性。</span><span class="sxs-lookup"><span data-stu-id="186f5-129">The following table lists these context-sensitive properties.</span></span>  
  
|<span data-ttu-id="186f5-130">属性</span><span class="sxs-lookup"><span data-stu-id="186f5-130">Property</span></span>|<span data-ttu-id="186f5-131">说明</span><span class="sxs-lookup"><span data-stu-id="186f5-131">Description</span></span>|  
|--------------|-----------------|  
|`ID`|<span data-ttu-id="186f5-132">在内部维护的成员 ID。</span><span class="sxs-lookup"><span data-stu-id="186f5-132">The internally maintained ID for the member.</span></span>|  
|`Key`|<span data-ttu-id="186f5-133">以原始数据类型表示的成员键的值。</span><span class="sxs-lookup"><span data-stu-id="186f5-133">The value of the member key in the original data type.</span></span> <span data-ttu-id="186f5-134">MEMBER_KEY 用于向后兼容。</span><span class="sxs-lookup"><span data-stu-id="186f5-134">MEMBER_KEY is for backward-compatibility.</span></span>  <span data-ttu-id="186f5-135">对于非组合键，MEMBER_KEY 具有与 KEY0 相同的值；对于组合键，MEMBER_KEY 属性为 null。</span><span class="sxs-lookup"><span data-stu-id="186f5-135">MEMBER_KEY has the same value as KEY0 for non-composite keys, and MEMBER_KEY property is null for composite keys.</span></span>|  
|`KEYx`|<span data-ttu-id="186f5-136">成员键，其中 x 是成员键的序号，起始值为零。</span><span class="sxs-lookup"><span data-stu-id="186f5-136">The key for the member, where x is the zero-based ordinal of the key.</span></span> <span data-ttu-id="186f5-137">KEY0 适用于组合键和非组合键，但是主要用于组合键。</span><span class="sxs-lookup"><span data-stu-id="186f5-137">KEY0 is available for composite and non-composite keys, but primarily used for composite keys.</span></span><br /><br /> <span data-ttu-id="186f5-138">对于组合键，KEY0、KEY1、KEY2 等共同构成了组合键。</span><span class="sxs-lookup"><span data-stu-id="186f5-138">For composite keys, KEY0, KEY1, KEY2, and so on, collectively form the composite key.</span></span> <span data-ttu-id="186f5-139">您可以在查询中独立使用它们以返回组合键的该部分。</span><span class="sxs-lookup"><span data-stu-id="186f5-139">You can use each one independently in a query to return that portion of the composite key.</span></span> <span data-ttu-id="186f5-140">例如，指定 KEY0 返回组合键的第一部分，指定 KEY1 返回组合键的下一部分等等。</span><span class="sxs-lookup"><span data-stu-id="186f5-140">For example, specifying KEY0 returns the first part of the composite key, specifying KEY1 returns the next part of the composite key, and so on.</span></span><br /><br /> <span data-ttu-id="186f5-141">如果键不是组合键，则 KEY0 与 `Key` 等效。</span><span class="sxs-lookup"><span data-stu-id="186f5-141">If the key is non-composite, then KEY0 is equivalent to `Key`.</span></span><br /><br /> <span data-ttu-id="186f5-142">请注意，`KEYx` 可以在上下文中使用，也可以不带上下文使用。</span><span class="sxs-lookup"><span data-stu-id="186f5-142">Note that `KEYx` can be used in context as well as without context.</span></span> <span data-ttu-id="186f5-143">因此，它显示在两个列表中。</span><span class="sxs-lookup"><span data-stu-id="186f5-143">For this reason, it appears in both lists.</span></span><br /><br /> <span data-ttu-id="186f5-144">有关如何使用此成员属性的示例，请参阅 [简单的 MDX 小组件：Key0、Key1、Key2](https://go.microsoft.com/fwlink/?LinkId=317364)。</span><span class="sxs-lookup"><span data-stu-id="186f5-144">For an example of how to use this member property, see [A Simple MDX Tidbit: Key0, Key1, Key2](https://go.microsoft.com/fwlink/?LinkId=317364).</span></span>|  
|`Name`|<span data-ttu-id="186f5-145">成员名。</span><span class="sxs-lookup"><span data-stu-id="186f5-145">The name of the member.</span></span>|  
  
### <a name="properties-syntax-for-context-sensitive-properties"></a><span data-ttu-id="186f5-146">上下文相关属性的 PROPERTIES 语法</span><span class="sxs-lookup"><span data-stu-id="186f5-146">PROPERTIES Syntax for Context Sensitive Properties</span></span>  
 <span data-ttu-id="186f5-147">在特定维度或级别的上下文中使用这些成员属性，用于为指定维度或级别的每个成员提供值。</span><span class="sxs-lookup"><span data-stu-id="186f5-147">You use these member properties in the context of a specific dimension or level, and supply values for each member of the specified dimension or level.</span></span>  
  
 <span data-ttu-id="186f5-148">对于维度成员属性，在属性名称的前面加上属性适用的维度的名称。</span><span class="sxs-lookup"><span data-stu-id="186f5-148">For dimension member properties, you precede the name of the property with the name of the dimension to which the property applies.</span></span> <span data-ttu-id="186f5-149">下面的示例列出了正确的语法：</span><span class="sxs-lookup"><span data-stu-id="186f5-149">The following example shows the appropriate syntax:</span></span>  
  
 `DIMENSION PROPERTIES Dimension.Property_name`  
  
 <span data-ttu-id="186f5-150">对于级别成员属性，可以在属性名称的前面仅加上级别名称；或者，为了更加明确具体，也可以将维度名称和级别名称都加上。</span><span class="sxs-lookup"><span data-stu-id="186f5-150">For a level member property, you can precede the name of the property with just the level name or, for additional specification, both the dimension and level name.</span></span> <span data-ttu-id="186f5-151">下面的示例列出了正确的语法：</span><span class="sxs-lookup"><span data-stu-id="186f5-151">The following example shows the appropriate syntax:</span></span>  
  
 `DIMENSION PROPERTIES [Dimension.]Level.Property_name`  
  
 <span data-ttu-id="186f5-152">为了说明这一点，假设您希望返回 `[Sales]` 维度中引用的每个成员的所有名称。</span><span class="sxs-lookup"><span data-stu-id="186f5-152">To illustrate, you would like to return all the names of each referenced member in the `[Sales]` dimension.</span></span> <span data-ttu-id="186f5-153">若要返回这些名称，需要在多维表达式 (MDX) 查询中使用以下语句：</span><span class="sxs-lookup"><span data-stu-id="186f5-153">To return these names, you would use the following statement in a Multidimensional Expressions (MDX) query:</span></span>  
  
 `DIMENSION PROPERTIES [Sales].Name`  
  
## <a name="non-context-sensitive-member-properties"></a><span data-ttu-id="186f5-154">非上下文相关的成员属性</span><span class="sxs-lookup"><span data-stu-id="186f5-154">Non-Context Sensitive Member Properties</span></span>  
 <span data-ttu-id="186f5-155">所有成员都支持一列内部成员属性，这些属性不因上下文而改变。</span><span class="sxs-lookup"><span data-stu-id="186f5-155">All members support a list of intrinsic member properties that are the same regardless of context.</span></span> <span data-ttu-id="186f5-156">这些属性提供了一些附加信息，可供应用程序用来改善用户的体验。</span><span class="sxs-lookup"><span data-stu-id="186f5-156">These properties provide additional information that can be used by applications to enhance the user's experience.</span></span>  
  
 <span data-ttu-id="186f5-157">下表列出了支持的非上下文相关的内部属性 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="186f5-157">The following table lists the non-context sensitive intrinsic properties supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="186f5-158">MEMBERS 架构行集中的列支持下表中列出的内部成员属性。</span><span class="sxs-lookup"><span data-stu-id="186f5-158">Columns in the MEMBERS schema rowset support the intrinsic member properties listed in the following table.</span></span> <span data-ttu-id="186f5-159">有关 `MEMBERS` 架构行集的详细信息，请参阅[MDSCHEMA_MEMBERS 行集](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-members-rowset)。</span><span class="sxs-lookup"><span data-stu-id="186f5-159">For more information about the `MEMBERS` schema rowset, see [MDSCHEMA_MEMBERS Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-members-rowset).</span></span>  
  
|<span data-ttu-id="186f5-160">属性</span><span class="sxs-lookup"><span data-stu-id="186f5-160">Property</span></span>|<span data-ttu-id="186f5-161">说明</span><span class="sxs-lookup"><span data-stu-id="186f5-161">Description</span></span>|  
|--------------|-----------------|  
|`CATALOG_NAME`|<span data-ttu-id="186f5-162">此成员所属的多维数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="186f5-162">The name of the cube to which this member belongs.</span></span>|  
|`CHILDREN_CARDINALITY`|<span data-ttu-id="186f5-163">成员具有的子级的个数。</span><span class="sxs-lookup"><span data-stu-id="186f5-163">The number of children that the member has.</span></span> <span data-ttu-id="186f5-164">它可以是一个估计值，所以不应依赖它进行确切计数。</span><span class="sxs-lookup"><span data-stu-id="186f5-164">This can be an estimate, so you should not rely on this to be the exact count.</span></span> <span data-ttu-id="186f5-165">访问接口应尽可能返回最精确的估计值。</span><span class="sxs-lookup"><span data-stu-id="186f5-165">Providers should return the best estimate possible.</span></span>|  
|`CUSTOM_ROLLUP`|<span data-ttu-id="186f5-166">自定义成员表达式。</span><span class="sxs-lookup"><span data-stu-id="186f5-166">The custom member expression.</span></span>|  
|`CUSTOM_ROLLUP_PROPERTIES`|<span data-ttu-id="186f5-167">自定义成员属性。</span><span class="sxs-lookup"><span data-stu-id="186f5-167">The custom member properties.</span></span>|  
|`DESCRIPTION`|<span data-ttu-id="186f5-168">用户可以阅读的成员说明。</span><span class="sxs-lookup"><span data-stu-id="186f5-168">A human-readable description of the member.</span></span>|  
|`DIMENSION_UNIQUE_NAME`|<span data-ttu-id="186f5-169">此成员所属的维度的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="186f5-169">The unique name of the dimension to which this member belongs.</span></span> <span data-ttu-id="186f5-170">对于通过限定生成唯一名称的访问接口，此名称的各组成部分之间用分隔符分隔。</span><span class="sxs-lookup"><span data-stu-id="186f5-170">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`HIERARCHY_UNIQUE_NAME`|<span data-ttu-id="186f5-171">层次结构的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="186f5-171">The unique name of the hierarchy.</span></span> <span data-ttu-id="186f5-172">如果成员属于多个层次结构，则成员所属的每个层次结构都有对应的一行。</span><span class="sxs-lookup"><span data-stu-id="186f5-172">If the member belongs to more than one hierarchy, there is one row for each hierarchy to which the member belongs.</span></span> <span data-ttu-id="186f5-173">对于通过限定生成唯一名称的访问接口，此名称的各组成部分之间用分隔符分隔。</span><span class="sxs-lookup"><span data-stu-id="186f5-173">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`IS_DATAMEMBER`|<span data-ttu-id="186f5-174">一个指示成员是否为数据成员的布尔值。</span><span class="sxs-lookup"><span data-stu-id="186f5-174">A Boolean that indicates whether the member is a data member.</span></span>|  
|`IS_PLACEHOLDERMEMBER`|<span data-ttu-id="186f5-175">用来指明成员是否为占位符的布尔值。</span><span class="sxs-lookup"><span data-stu-id="186f5-175">A Boolean that indicates whether the member is a placeholder.</span></span>|  
|`KEYx`|<span data-ttu-id="186f5-176">成员键，其中 x 是成员键的序号，起始值为零。</span><span class="sxs-lookup"><span data-stu-id="186f5-176">The key for the member, where x is the zero-based ordinal of the key.</span></span> <span data-ttu-id="186f5-177">KEY0 可用于组合键和非组合键。</span><span class="sxs-lookup"><span data-stu-id="186f5-177">KEY0 is available for composite and non-composite keys.</span></span><br /><br /> <span data-ttu-id="186f5-178">如果键不是组合键，则 KEY0 与 `Key` 等效。</span><span class="sxs-lookup"><span data-stu-id="186f5-178">If the key is non-composite, then KEY0 is equivalent to `Key`.</span></span><br /><br /> <span data-ttu-id="186f5-179">对于组合键，KEY0、KEY1、KEY2 等共同构成了组合键。</span><span class="sxs-lookup"><span data-stu-id="186f5-179">For composite keys, KEY0, KEY1, KEY2, and so on, collectively form the composite key.</span></span> <span data-ttu-id="186f5-180">您可以在查询中独立引用它们以返回组合键的该部分。</span><span class="sxs-lookup"><span data-stu-id="186f5-180">You can reference each one independently in a query to return that portion of the composite key.</span></span> <span data-ttu-id="186f5-181">例如，指定 KEY0 返回组合键的第一部分，指定 KEY1 返回组合键的下一部分等等。</span><span class="sxs-lookup"><span data-stu-id="186f5-181">For example, specifying KEY0 returns the first part of the composite key, specifying KEY1 returns the next part of the composite key, and so on.</span></span><br /><br /> <span data-ttu-id="186f5-182">请注意，`KEYx` 可以在上下文中使用，也可以不带上下文使用。</span><span class="sxs-lookup"><span data-stu-id="186f5-182">Note that `KEYx` can be used in context as well as without context.</span></span> <span data-ttu-id="186f5-183">因此，它显示在两个列表中。</span><span class="sxs-lookup"><span data-stu-id="186f5-183">For this reason, it appears in both lists.</span></span><br /><br /> <span data-ttu-id="186f5-184">有关如何使用此成员属性的示例，请参阅 [简单的 MDX 小组件：Key0、Key1、Key2](https://go.microsoft.com/fwlink/?LinkId=317364)。</span><span class="sxs-lookup"><span data-stu-id="186f5-184">For an example of how to use this member property, see [A Simple MDX Tidbit: Key0, Key1, Key2](https://go.microsoft.com/fwlink/?LinkId=317364).</span></span>|  
|<span data-ttu-id="186f5-185">`LCID` x</span><span class="sxs-lookup"><span data-stu-id="186f5-185">`LCID` *x*</span></span>|<span data-ttu-id="186f5-186">区域设置 ID 十六进制值中的成员标题的翻译，其中 *x* 是区域设置 ID 十进制值（例如，LCID1009 表示加拿大英语）。</span><span class="sxs-lookup"><span data-stu-id="186f5-186">The translation of the member caption in the locale ID hexadecimal value, where *x* is the locale ID decimal value (for example, LCID1009 as English-Canada).</span></span> <span data-ttu-id="186f5-187">这仅适用于翻译具有绑定到数据源的标题列的情况。</span><span class="sxs-lookup"><span data-stu-id="186f5-187">This is only available if the translation has the caption column bound to the data source.</span></span>|  
|`LEVEL_NUMBER`|<span data-ttu-id="186f5-188">成员距层次结构的根的距离。</span><span class="sxs-lookup"><span data-stu-id="186f5-188">The distance of the member from the root of the hierarchy.</span></span> <span data-ttu-id="186f5-189">根级别为零。</span><span class="sxs-lookup"><span data-stu-id="186f5-189">The root level is zero.</span></span>|  
|`LEVEL_UNIQUE_NAME`|<span data-ttu-id="186f5-190">成员所属的级别的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="186f5-190">The unique name of the level to which the member belongs.</span></span> <span data-ttu-id="186f5-191">对于通过限定生成唯一名称的访问接口，此名称的各组成部分之间用分隔符分隔。</span><span class="sxs-lookup"><span data-stu-id="186f5-191">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`MEMBER_CAPTION`|<span data-ttu-id="186f5-192">与成员相关的标签或标题。</span><span class="sxs-lookup"><span data-stu-id="186f5-192">A label or caption associated with the member.</span></span> <span data-ttu-id="186f5-193">标题主要用于显示目的。</span><span class="sxs-lookup"><span data-stu-id="186f5-193">The caption is primarily for display purposes.</span></span> <span data-ttu-id="186f5-194">如果不存在标题，查询将返回 `MEMBER_NAME`。</span><span class="sxs-lookup"><span data-stu-id="186f5-194">If a caption does not exist, the query returns `MEMBER_NAME`.</span></span>|  
|`MEMBER_KEY`|<span data-ttu-id="186f5-195">以原始数据类型表示的成员键的值。</span><span class="sxs-lookup"><span data-stu-id="186f5-195">The value of the member key in the original data type.</span></span> <span data-ttu-id="186f5-196">MEMBER_KEY 用于向后兼容。</span><span class="sxs-lookup"><span data-stu-id="186f5-196">MEMBER_KEY is for backward-compatibility.</span></span>  <span data-ttu-id="186f5-197">对于非组合键，MEMBER_KEY 具有与 KEY0 相同的值；对于组合键，MEMBER_KEY 属性为 null。</span><span class="sxs-lookup"><span data-stu-id="186f5-197">MEMBER_KEY has the same value as KEY0 for non-composite keys, and MEMBER_KEY property is null for composite keys.</span></span>|  
|`MEMBER_NAME`|<span data-ttu-id="186f5-198">成员名。</span><span class="sxs-lookup"><span data-stu-id="186f5-198">The name of the member.</span></span>|  
|`MEMBER_TYPE`|<span data-ttu-id="186f5-199">成员的类型。</span><span class="sxs-lookup"><span data-stu-id="186f5-199">The type of the member.</span></span> <span data-ttu-id="186f5-200">此属性可以具有下列值之一：</span><span class="sxs-lookup"><span data-stu-id="186f5-200">This property can have one of the following values:</span></span> <br /><span data-ttu-id="186f5-201">**MDMEMBER_TYPE_REGULAR**</span><span class="sxs-lookup"><span data-stu-id="186f5-201">**MDMEMBER_TYPE_REGULAR**</span></span><br /><span data-ttu-id="186f5-202">**MDMEMBER_TYPE_ALL**</span><span class="sxs-lookup"><span data-stu-id="186f5-202">**MDMEMBER_TYPE_ALL**</span></span><br /><span data-ttu-id="186f5-203">**MDMEMBER_TYPE_FORMULA**</span><span class="sxs-lookup"><span data-stu-id="186f5-203">**MDMEMBER_TYPE_FORMULA**</span></span><br /><span data-ttu-id="186f5-204">**MDMEMBER_TYPE_MEASURE**</span><span class="sxs-lookup"><span data-stu-id="186f5-204">**MDMEMBER_TYPE_MEASURE**</span></span><br /><span data-ttu-id="186f5-205">**MDMEMBER_TYPE_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="186f5-205">**MDMEMBER_TYPE_UNKNOWN**</span></span><br /><br /> <br /><br /> <span data-ttu-id="186f5-206">MDMEMBER_TYPE_FORMULA 优先于 MDMEMBER_TYPE_MEASURE。</span><span class="sxs-lookup"><span data-stu-id="186f5-206">MDMEMBER_TYPE_FORMULA takes precedence over MDMEMBER_TYPE_MEASURE.</span></span> <span data-ttu-id="186f5-207">因此，如果 Measures 维度上有一个公式（计算）成员，则计算成员的 `MEMBER_TYPE` 属性为 MDMEMBER_TYPE_FORMULA。</span><span class="sxs-lookup"><span data-stu-id="186f5-207">Therefore, if there is a formula (calculated) member on the Measures dimension, the `MEMBER_TYPE` property for the calculated member is MDMEMBER_TYPE_FORMULA.</span></span>|  
|`MEMBER_UNIQUE_NAME`|<span data-ttu-id="186f5-208">成员的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="186f5-208">The unique name of the member.</span></span> <span data-ttu-id="186f5-209">对于通过限定生成唯一名称的访问接口，此名称的各组成部分之间用分隔符分隔。</span><span class="sxs-lookup"><span data-stu-id="186f5-209">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`MEMBER_VALUE`|<span data-ttu-id="186f5-210">以原始类型表示的成员的值。</span><span class="sxs-lookup"><span data-stu-id="186f5-210">The value of the member in the original type.</span></span>|  
|`PARENT_COUNT`|<span data-ttu-id="186f5-211">此成员具有的父级的个数。</span><span class="sxs-lookup"><span data-stu-id="186f5-211">The number of parents that this member has.</span></span>|  
|`PARENT_LEVEL`|<span data-ttu-id="186f5-212">成员的父级距层次结构的根级别的距离。</span><span class="sxs-lookup"><span data-stu-id="186f5-212">The distance of the member's parent from the root level of the hierarchy.</span></span> <span data-ttu-id="186f5-213">根级别为零。</span><span class="sxs-lookup"><span data-stu-id="186f5-213">The root level is zero.</span></span>|  
|`PARENT_UNIQUE_NAME`|<span data-ttu-id="186f5-214">成员的父成员的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="186f5-214">The unique name of the member's parent.</span></span> <span data-ttu-id="186f5-215">对于根级别上的任何成员，均返回 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="186f5-215">`NULL` is returned for any members at the root level.</span></span> <span data-ttu-id="186f5-216">对于通过限定生成唯一名称的访问接口，此名称的各组成部分之间用分隔符分隔。</span><span class="sxs-lookup"><span data-stu-id="186f5-216">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`SKIPPED_LEVELS`|<span data-ttu-id="186f5-217">跳过的成员级别数。</span><span class="sxs-lookup"><span data-stu-id="186f5-217">The number of skipped levels for the member.</span></span>|  
|`UNARY_OPERATOR`|<span data-ttu-id="186f5-218">成员的一元运算符。</span><span class="sxs-lookup"><span data-stu-id="186f5-218">The unary operator for the member.</span></span>|  
|`UNIQUE_NAME`|<span data-ttu-id="186f5-219">成员的完全限定名称，它采用以下格式：[dimension].[level].[key6.]</span><span class="sxs-lookup"><span data-stu-id="186f5-219">The fully-qualified name of the member, in this format: [dimension].[level].[key6.]</span></span>|  
  
### <a name="properties-syntax-for-non-context-sensitive-properties"></a><span data-ttu-id="186f5-220">非上下文相关属性的 PROPERTIES 语法</span><span class="sxs-lookup"><span data-stu-id="186f5-220">PROPERTIES Syntax for Non-Context Sensitive Properties</span></span>  
 <span data-ttu-id="186f5-221">使用以下语法指定使用 `PROPERTIES` 关键字的非上下文相关的内部成员属性：</span><span class="sxs-lookup"><span data-stu-id="186f5-221">Use the following syntax to specify an intrinsic, non-context sensitive member property using the `PROPERTIES` keyword:</span></span>  
  
 `DIMENSION PROPERTIES Property`  
  
 <span data-ttu-id="186f5-222">请注意，此语法不允许使用维度或级别来限定属性。</span><span class="sxs-lookup"><span data-stu-id="186f5-222">Notice that this syntax does not allow the property to be qualified by a dimension or level.</span></span> <span data-ttu-id="186f5-223">因为非上下文相关的内部成员属性适用于某条轴上的所有成员，所以不能限定属性。</span><span class="sxs-lookup"><span data-stu-id="186f5-223">The property cannot be qualified because an intrinsic member property that is not context sensitive applies to all members of an axis.</span></span>  
  
 <span data-ttu-id="186f5-224">例如，指定 `DESCRIPTION` 内部成员属性的 MDX 语句具有以下语法：</span><span class="sxs-lookup"><span data-stu-id="186f5-224">For example, an MDX statement that specifies the `DESCRIPTION` intrinsic member property would have the following syntax:</span></span>  
  
 `DIMENSION PROPERTIES DESCRIPTION`  
  
 <span data-ttu-id="186f5-225">此语句返回轴维度中各个成员的说明。</span><span class="sxs-lookup"><span data-stu-id="186f5-225">This statement returns the description of each member in the axis dimension.</span></span> <span data-ttu-id="186f5-226">如果尝试使用维度或级别限定属性，如*维度* `.DESCRIPTION` 或*级别* `.DESCRIPTION` ，则不会验证语句。</span><span class="sxs-lookup"><span data-stu-id="186f5-226">If you tried to qualify the property with a dimension or level, as in *Dimension*`.DESCRIPTION` or *Level*`.DESCRIPTION`, the statement would not validate.</span></span>  
  
### <a name="example"></a><span data-ttu-id="186f5-227">示例</span><span class="sxs-lookup"><span data-stu-id="186f5-227">Example</span></span>  
 <span data-ttu-id="186f5-228">以下示例显示返回内部属性的 MDX 查询。</span><span class="sxs-lookup"><span data-stu-id="186f5-228">The following examples show MDX queries that return intrinsic properties.</span></span>  
  
 <span data-ttu-id="186f5-229">**示例 1：在查询中使用上下文相关的内部属性**</span><span class="sxs-lookup"><span data-stu-id="186f5-229">**Example 1: Use context-sensitive intrinsic properties in query**</span></span>  
  
 <span data-ttu-id="186f5-230">以下示例返回每个产品类别的父 ID、键和名称。</span><span class="sxs-lookup"><span data-stu-id="186f5-230">The following example returns parent ID, key, and name for each product category.</span></span> <span data-ttu-id="186f5-231">请注意属性如何公开为度量值。</span><span class="sxs-lookup"><span data-stu-id="186f5-231">Notice how the properties are exposed as measures.</span></span> <span data-ttu-id="186f5-232">这允许您在运行查询时在单元集中查看属性，而非在 SSMS 的“成员属性”对话框中查看。</span><span class="sxs-lookup"><span data-stu-id="186f5-232">This lets you view the properties in a cellset when you run the query, rather than the Member Properties dialog in SSMS.</span></span> <span data-ttu-id="186f5-233">您可能运行类似的查询以从部署的多维数据集检索成员元数据。</span><span class="sxs-lookup"><span data-stu-id="186f5-233">You might run a query like this to retrieve member metadata from a cube that is already deployed.</span></span>  
  
```  
WITH  
MEMBER [Measures].[Parent Member ID] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("ID")  
MEMBER [Measures].[Parent Member Key] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")  
MEMBER [Measures].[Parent Member Name] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("Name")  
SELECT  
 {[Measures].[Parent Member ID], [Measures].[Parent Member Key], [Measures].[Parent Member Name] } on COLUMNS,   
 [Product].[Product Categories].AllMembers on ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="186f5-234">**示例 2：非上下文相关的内部属性**</span><span class="sxs-lookup"><span data-stu-id="186f5-234">**Example 2: Non-context-sensitive intrinsic properties**</span></span>  
  
 <span data-ttu-id="186f5-235">以下示例是非上下文相关的内部属性的完整列表。</span><span class="sxs-lookup"><span data-stu-id="186f5-235">The following example is the full list of non-context-sensitive intrinsic properties.</span></span> <span data-ttu-id="186f5-236">在 SSMS 中运行查询后，单击各个成员可以在“成员属性”对话框中查看属性。</span><span class="sxs-lookup"><span data-stu-id="186f5-236">After running the query in SSMS, click individual members to view properties in the Member Properties dialog box.</span></span>  
  
```  
SELECT [Measures].[Sales Amount Quota] on COLUMNS,  
[Employee].[Employees].members  
DIMENSION PROPERTIES  
 CATALOG_NAME ,   
 CHILDREN_CARDINALITY ,  
 CUSTOM_ROLLUP ,   
 CUSTOM_ROLLUP_PROPERTIES ,   
 DESCRIPTION ,   
 DIMENSION_UNIQUE_NAME ,   
 HIERARCHY_UNIQUE_NAME ,  
 IS_DATAMEMBER ,   
 IS_PLACEHOLDERMEMBER ,   
 KEY0 ,  
 LCID ,  
 LEVEL_NUMBER ,  
 LEVEL_UNIQUE_NAME ,  
 MEMBER_CAPTION ,   
 MEMBER_KEY ,   
 MEMBER_NAME ,   
 MEMBER_TYPE ,  
 MEMBER_UNIQUE_NAME ,   
 MEMBER_VALUE ,   
 PARENT_COUNT ,   
 PARENT_LEVEL ,   
 PARENT_UNIQUE_NAME ,  
 SKIPPED_LEVELS ,   
 UNARY_OPERATOR ,   
 UNIQUE_NAME    
 ON ROWS  
FROM [Adventure Works]  
WHERE [Employee].[Employee Department].[Department].&[Sales]  
```  
  
 <span data-ttu-id="186f5-237">**示例 3：将成员属性作为结果集中的数据返回**</span><span class="sxs-lookup"><span data-stu-id="186f5-237">**Example 3: Return member properties as data in a result set**</span></span>  
  
 <span data-ttu-id="186f5-238">下面的示例为指定区域设置的 Adventure Works 多维数据集中 Product 维度的产品类别成员返回翻译后的标题。</span><span class="sxs-lookup"><span data-stu-id="186f5-238">The following example returns the translated caption for the product category member in the Product dimension in the Adventure Works cube for specified locales.</span></span>  
  
```  
WITH   
MEMBER Measures.CategoryCaption AS Product.Category.CurrentMember.MEMBER_CAPTION  
MEMBER Measures.SpanishCategoryCaption AS Product.Category.CurrentMember.Properties("LCID3082")  
MEMBER Measures.FrenchCategoryCaption AS Product.Category.CurrentMember.Properties("LCID1036")  
SELECT   
{ Measures.CategoryCaption, Measures.SpanishCategoryCaption, Measures.FrenchCategoryCaption } ON 0  
,[Product].[Category].MEMBERS ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="186f5-239">另请参阅</span><span class="sxs-lookup"><span data-stu-id="186f5-239">See Also</span></span>  
 <span data-ttu-id="186f5-240">[PeriodsToDate &#40;MDX&#41;](/sql/mdx/periodstodate-mdx) </span><span class="sxs-lookup"><span data-stu-id="186f5-240">[PeriodsToDate &#40;MDX&#41;](/sql/mdx/periodstodate-mdx) </span></span>  
 <span data-ttu-id="186f5-241">[子 &#40;MDX&#41;](/sql/mdx/children-mdx) </span><span class="sxs-lookup"><span data-stu-id="186f5-241">[Children &#40;MDX&#41;](/sql/mdx/children-mdx) </span></span>  
 <span data-ttu-id="186f5-242">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span><span class="sxs-lookup"><span data-stu-id="186f5-242">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span></span>  
 <span data-ttu-id="186f5-243">[&#41; &#40;MDX&#41;&#40;集计数](/sql/mdx/count-set-mdx) </span><span class="sxs-lookup"><span data-stu-id="186f5-243">[Count &#40;Set&#41; &#40;MDX&#41;](/sql/mdx/count-set-mdx) </span></span>  
 <span data-ttu-id="186f5-244">[筛选 &#40;MDX&#41;](/sql/mdx/filter-mdx) </span><span class="sxs-lookup"><span data-stu-id="186f5-244">[Filter &#40;MDX&#41;](/sql/mdx/filter-mdx) </span></span>  
 <span data-ttu-id="186f5-245">[AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx) </span><span class="sxs-lookup"><span data-stu-id="186f5-245">[AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx) </span></span>  
 <span data-ttu-id="186f5-246">[DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx) </span><span class="sxs-lookup"><span data-stu-id="186f5-246">[DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx) </span></span>  
 <span data-ttu-id="186f5-247">[MDX&#41;&#40;属性](/sql/mdx/properties-mdx) </span><span class="sxs-lookup"><span data-stu-id="186f5-247">[Properties &#40;MDX&#41;](/sql/mdx/properties-mdx) </span></span>  
 <span data-ttu-id="186f5-248">[PrevMember &#40;MDX&#41;](/sql/mdx/prevmember-mdx) </span><span class="sxs-lookup"><span data-stu-id="186f5-248">[PrevMember &#40;MDX&#41;](/sql/mdx/prevmember-mdx) </span></span>  
 <span data-ttu-id="186f5-249">[&#40;MDX&#41;使用成员属性](mdx-member-properties.md) </span><span class="sxs-lookup"><span data-stu-id="186f5-249">[Using Member Properties &#40;MDX&#41;](mdx-member-properties.md) </span></span>  
 [<span data-ttu-id="186f5-250">MDX 函数引用 (MDX)</span><span class="sxs-lookup"><span data-stu-id="186f5-250">MDX Function Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-function-reference-mdx)  
  
  
