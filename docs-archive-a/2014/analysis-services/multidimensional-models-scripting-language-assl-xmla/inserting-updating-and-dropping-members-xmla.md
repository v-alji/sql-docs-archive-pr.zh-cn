---
title: " (XMLA) 插入、更新和删除成员 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- inserting dimension members
- XML for Analysis, members
- removing dimension members
- dropping dimension members
- write-enabled dimensions [Analysis Services]
- XMLA, members
- deleting dimension members
- dimensions [Analysis Services], XML for Analysis
ms.assetid: bba922b5-8b88-4051-9506-ff055248182a
author: minewiskan
ms.author: owend
ms.openlocfilehash: aef124abc8398f1b314a391291b52340a90689ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589927"
---
# <a name="inserting-updating-and-dropping-members-xmla"></a><span data-ttu-id="5615b-102">插入、更新和删除成员 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="5615b-102">Inserting, Updating, and Dropping Members (XMLA)</span></span>
  <span data-ttu-id="5615b-103">您可以使用 XML for Analysis (XMLA) 中的 "[插入](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla)"、"[更新](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)" 和["删除" 命令，](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla)分别在启用写功能的维度中插入、更新或删除成员。</span><span class="sxs-lookup"><span data-stu-id="5615b-103">You can use the [Insert](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla), [Update](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla), and [Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) commands in XML for Analysis (XMLA) to respectively insert, update, or delete members from a write-enabled dimension.</span></span> <span data-ttu-id="5615b-104">有关启用了写功能的维度的详细信息，请参阅[启用写功能的维度](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="5615b-104">For more information about write-enabled dimensions, see [Write-Enabled Dimensions](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).</span></span>  
  
## <a name="inserting-new-members"></a><span data-ttu-id="5615b-105">插入新成员</span><span class="sxs-lookup"><span data-stu-id="5615b-105">Inserting New Members</span></span>  
 <span data-ttu-id="5615b-106">`Insert` 命令可将新成员插入启用写操作的维度的指定特性中。</span><span class="sxs-lookup"><span data-stu-id="5615b-106">The `Insert` command inserts new members into specified attributes in a write-enabled dimension.</span></span>  
  
 <span data-ttu-id="5615b-107">构造 `Insert` 命令之前，应提供要插入的新成员的以下信息：</span><span class="sxs-lookup"><span data-stu-id="5615b-107">Before constructing the `Insert` command, you should have the following information available for the new members to be inserted:</span></span>  
  
-   <span data-ttu-id="5615b-108">要在其中插入新成员的维度。</span><span class="sxs-lookup"><span data-stu-id="5615b-108">The dimension in which to insert the new members.</span></span>  
  
-   <span data-ttu-id="5615b-109">要在其中插入新成员的维度特性。</span><span class="sxs-lookup"><span data-stu-id="5615b-109">The dimension attribute in which to insert the new members.</span></span>  
  
-   <span data-ttu-id="5615b-110">新成员的名称，包括该名称的所有适用翻译。</span><span class="sxs-lookup"><span data-stu-id="5615b-110">The names of the new members, including any applicable translations for the name.</span></span>  
  
-   <span data-ttu-id="5615b-111">新成员的键。</span><span class="sxs-lookup"><span data-stu-id="5615b-111">The keys of the new members.</span></span> <span data-ttu-id="5615b-112">如果某特性使用一个组合键，则该键可能需要多个值。</span><span class="sxs-lookup"><span data-stu-id="5615b-112">If an attribute uses a composite key, the key may require multiple values.</span></span>  
  
-   <span data-ttu-id="5615b-113">不作为该维度内的其他特性实现的所有适用特性属性的值。</span><span class="sxs-lookup"><span data-stu-id="5615b-113">Values for any applicable attribute properties that are not implemented as other attributes within the dimension.</span></span> <span data-ttu-id="5615b-114">此类特性属性包括一元运算符、翻译、自定义汇总、自定义汇总属性以及已跳过的级别。</span><span class="sxs-lookup"><span data-stu-id="5615b-114">Such attribute properties include unary operations, translations, custom rollups, custom rollup properties, and skipped levels.</span></span>  
  
 <span data-ttu-id="5615b-115">`Insert` 命令仅具有两个属性：</span><span class="sxs-lookup"><span data-stu-id="5615b-115">The `Insert` command takes only two properties:</span></span>  
  
-   <span data-ttu-id="5615b-116">[对象](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)属性，它包含要在其中插入成员的维度的对象引用。</span><span class="sxs-lookup"><span data-stu-id="5615b-116">The [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property, which contains an object reference for the dimension in which the members are to be inserted.</span></span> <span data-ttu-id="5615b-117">该对象引用包含维度的数据库标识符、多维数据集标识符和维度标识符。</span><span class="sxs-lookup"><span data-stu-id="5615b-117">The object reference contains the database identifier, cube identifier, and dimension identifier for the dimension.</span></span>  
  
-   <span data-ttu-id="5615b-118">[Attributes](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attributes-element-xmla)属性，其中包含一个或多个[Attribute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attribute-element-xmla)元素，用于标识要在其中插入成员的属性。</span><span class="sxs-lookup"><span data-stu-id="5615b-118">The [Attributes](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attributes-element-xmla) property, which contains one or more [Attribute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attribute-element-xmla) elements to identify the attributes in which members are to be inserted.</span></span> <span data-ttu-id="5615b-119">每个 `Attribute` 元素都标识一个特性，并为要添加到已标识特性的单个成员提供名称、值、翻译、一元运算符、自定义汇总、自定义汇总属性以及已跳过的级别。</span><span class="sxs-lookup"><span data-stu-id="5615b-119">Each `Attribute` element identifies an attribute and provides the name, value, translations, unary operator, custom rollup, custom rollup properties, and skipped levels for a single member to be added to the identified attribute.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5615b-120">必须包括 `Attribute` 元素的所有属性。</span><span class="sxs-lookup"><span data-stu-id="5615b-120">All properties for the `Attribute` element must be included.</span></span> <span data-ttu-id="5615b-121">否则，可能会出错。</span><span class="sxs-lookup"><span data-stu-id="5615b-121">Otherwise, an error may occur.</span></span>  
  
## <a name="updating-existing-members"></a><span data-ttu-id="5615b-122">更新现有成员</span><span class="sxs-lookup"><span data-stu-id="5615b-122">Updating Existing Members</span></span>  
 <span data-ttu-id="5615b-123">`Update` 命令可在已启用写操作的维度中根据指定特性中现有成员与其他特性中其他成员的关系更新现有成员。</span><span class="sxs-lookup"><span data-stu-id="5615b-123">The `Update` command updates existing members in specified attributes, based on relationships with other members in other attributes, in a write-enabled dimension.</span></span> <span data-ttu-id="5615b-124">`Update` 命令可将成员移到维度所包含层次结构中的其他级别，并可用于重新组织父特性所定义的父子层次结构。</span><span class="sxs-lookup"><span data-stu-id="5615b-124">The `Update` command can move members to other levels in hierarchies contained by the dimension, and can be used to restructure parent-child hierarchies defined by parent attributes.</span></span>  
  
 <span data-ttu-id="5615b-125">构造 `Update` 命令之前，应提供要更新的成员的以下信息：</span><span class="sxs-lookup"><span data-stu-id="5615b-125">Before constructing the `Update` command, you should have the following information available for the members to be updated:</span></span>  
  
-   <span data-ttu-id="5615b-126">要在其中更新现有成员的维度。</span><span class="sxs-lookup"><span data-stu-id="5615b-126">The dimension in which to update existing members.</span></span>  
  
-   <span data-ttu-id="5615b-127">要在其中更新现有成员的维度特性。</span><span class="sxs-lookup"><span data-stu-id="5615b-127">The dimension attributes in which to update existing members.</span></span>  
  
-   <span data-ttu-id="5615b-128">现有成员的键。</span><span class="sxs-lookup"><span data-stu-id="5615b-128">The keys of the existing members.</span></span> <span data-ttu-id="5615b-129">如果某特性使用一个组合键，则该键可能需要多个值。</span><span class="sxs-lookup"><span data-stu-id="5615b-129">If an attribute uses a composite key, the key may require multiple values.</span></span>  
  
-   <span data-ttu-id="5615b-130">不作为该维度内的其他特性实现的所有适用特性属性的值。</span><span class="sxs-lookup"><span data-stu-id="5615b-130">Values for any applicable attribute properties that are not implemented as other attributes within the dimension.</span></span> <span data-ttu-id="5615b-131">此类特性属性包括一元运算符、翻译、自定义汇总、自定义汇总属性以及已跳过的级别。</span><span class="sxs-lookup"><span data-stu-id="5615b-131">Such attribute properties include unary operations, translations, custom rollups, custom rollup properties, and skipped levels.</span></span>  
  
 <span data-ttu-id="5615b-132">`Update` 命令仅具有三个必需属性：</span><span class="sxs-lookup"><span data-stu-id="5615b-132">The `Update` command takes only three required properties:</span></span>  
  
-   <span data-ttu-id="5615b-133">`Object` 属性，它包含对要在其中更新成员的维度的对象引用。</span><span class="sxs-lookup"><span data-stu-id="5615b-133">The `Object` property, which contains an object reference for the dimension in which the members are to be updated.</span></span> <span data-ttu-id="5615b-134">该对象引用包含维度的数据库标识符、多维数据集标识符和维度标识符。</span><span class="sxs-lookup"><span data-stu-id="5615b-134">The object reference contains the database identifier, cube identifier, and dimension identifier for the dimension.</span></span>  
  
-   <span data-ttu-id="5615b-135">`Attributes` 属性，它包含用于标识要在其中更新成员的特性的一个或多个 `Attribute` 元素。</span><span class="sxs-lookup"><span data-stu-id="5615b-135">The `Attributes` property, which contains one or more `Attribute` elements to identify the attributes in which members are to be updated.</span></span> <span data-ttu-id="5615b-136">`Attribute` 元素可标识一个特性，并为已标识特性中更新的单个成员提供名称、值、翻译、一元运算符、自定义汇总、自定义汇总属性以及已跳过的级别。</span><span class="sxs-lookup"><span data-stu-id="5615b-136">The `Attribute` element identifies an attribute and provides the name, value, translations, unary operator, custom rollup, custom rollup properties, and skipped levels for a single member updated for the identified attribute.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5615b-137">必须包括 `Attribute` 元素的所有属性。</span><span class="sxs-lookup"><span data-stu-id="5615b-137">All properties for the `Attribute` element must be included.</span></span> <span data-ttu-id="5615b-138">否则，可能会出错。</span><span class="sxs-lookup"><span data-stu-id="5615b-138">Otherwise, an error may occur.</span></span>  
  
-   <span data-ttu-id="5615b-139">[Where](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/where-element-xmla)属性，其中包含一个或多个 `Attribute` 约束要在其中更新成员的属性的元素。</span><span class="sxs-lookup"><span data-stu-id="5615b-139">The [Where](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/where-element-xmla) property, which contains one or more `Attribute` elements that constrain the attributes in which members are to be updated.</span></span> <span data-ttu-id="5615b-140">`Where`属性对于将 `Update` 命令限定为成员的特定实例是至关重要的。</span><span class="sxs-lookup"><span data-stu-id="5615b-140">The `Where` property is crucial to limiting an `Update` command to specific instances of a member.</span></span> <span data-ttu-id="5615b-141">如果 `Where` 未指定属性，则将更新给定成员的所有实例。</span><span class="sxs-lookup"><span data-stu-id="5615b-141">If the `Where` property is not specified, all instances of a given member are updated.</span></span> <span data-ttu-id="5615b-142">例如，有三个客户，您希望将他们的市县名称从 Redmond 更改为 Bellevue。</span><span class="sxs-lookup"><span data-stu-id="5615b-142">For example, there are three customers for whom you want to change the city name from Redmond to Bellevue.</span></span> <span data-ttu-id="5615b-143">若要更改市县名称，您必须提供 `Where` 属性，该属性将标识 Customer 特性的三个成员中应更改其 City 特性的成员。</span><span class="sxs-lookup"><span data-stu-id="5615b-143">To change the city name, you must provide a `Where` property that identifies the three members in the Customer attribute for which the members in the City attribute should be changed.</span></span> <span data-ttu-id="5615b-144">如果您不提供此 `Where` 属性，则运行 `Update` 命令后，其市县名称当前为 Redmond 的每个客户的市县名称都将更改为 Bellevue。</span><span class="sxs-lookup"><span data-stu-id="5615b-144">If you do not provide this `Where` property, every customer whose city name is currently Redmond would have the city name of Bellevue after the `Update` command runs.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5615b-145">除了新成员以外，`Update` 命令只能更新 `Where` 子句中未包括的特性的特性键值。</span><span class="sxs-lookup"><span data-stu-id="5615b-145">With the exception of new members, the `Update` command can only update attribute key values for attributes not included in the `Where` clause.</span></span> <span data-ttu-id="5615b-146">例如，更新客户时不能更新市县名称；否则，会更改所有客户的市县名称。</span><span class="sxs-lookup"><span data-stu-id="5615b-146">For example, the city name cannot be updated when a customer is updated; otherwise, the city name is changed for all customers.</span></span>  
  
### <a name="updating-members-in-parent-attributes"></a><span data-ttu-id="5615b-147">更新父特性中的成员</span><span class="sxs-lookup"><span data-stu-id="5615b-147">Updating Members in Parent Attributes</span></span>  
 <span data-ttu-id="5615b-148">若要支持父属性，请在命令中提供 `Update` 可选的[MoveWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/movewithdescendants-element-xmla)MovewithDescedants 属性。</span><span class="sxs-lookup"><span data-stu-id="5615b-148">To support parent attributes, the `Update` command the optional [MoveWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/movewithdescendants-element-xmla)MovewithDescedants properties.</span></span> <span data-ttu-id="5615b-149">如果将 `MoveWithDescendants` 属性设置为 True，则表示当父成员的标识符发生更改时，该父成员的后代也应与该父成员一起移动。</span><span class="sxs-lookup"><span data-stu-id="5615b-149">Setting the `MoveWithDescendants` property to true indicates that the descendants of the parent member should also be moved with the parent member when the identifier of that parent member changes.</span></span> <span data-ttu-id="5615b-150">如果将此值设置为 False，则移动某父成员将导致该父成员的直接后代提升到该父成员先前所处的级别。</span><span class="sxs-lookup"><span data-stu-id="5615b-150">If this value is set to false, moving a parent member causes the immediate descendants of that parent member to be promoted to the level in which the parent member formerly resided.</span></span>  
  
 <span data-ttu-id="5615b-151">更新父特性中的成员时，`Update` 命令无法更新其他特性中的成员。</span><span class="sxs-lookup"><span data-stu-id="5615b-151">When updating members in a parent attribute, the `Update` command cannot update members in other attributes.</span></span>  
  
## <a name="dropping-existing-members"></a><span data-ttu-id="5615b-152">删除现有成员</span><span class="sxs-lookup"><span data-stu-id="5615b-152">Dropping Existing Members</span></span>  
 <span data-ttu-id="5615b-153">构造 `Drop` 命令之前，应该提供要删除的成员的以下信息：</span><span class="sxs-lookup"><span data-stu-id="5615b-153">Before constructing the `Drop` command, you should have the following information available for the members to be dropped:</span></span>  
  
-   <span data-ttu-id="5615b-154">要在其中删除现有成员的维度。</span><span class="sxs-lookup"><span data-stu-id="5615b-154">The dimension in which to drop existing members.</span></span>  
  
-   <span data-ttu-id="5615b-155">要在其中删除现有成员的维度特性。</span><span class="sxs-lookup"><span data-stu-id="5615b-155">The dimension attributes in which to drop existing members.</span></span>  
  
-   <span data-ttu-id="5615b-156">要删除的现有成员的键。</span><span class="sxs-lookup"><span data-stu-id="5615b-156">The keys of the existing members to be dropped.</span></span> <span data-ttu-id="5615b-157">如果某特性使用一个组合键，则该键可能需要多个值。</span><span class="sxs-lookup"><span data-stu-id="5615b-157">If an attribute uses a composite key, the key may require multiple values.</span></span>  
  
 <span data-ttu-id="5615b-158">`Drop` 命令仅具有两个必需属性：</span><span class="sxs-lookup"><span data-stu-id="5615b-158">The `Drop` command takes only two required properties:</span></span>  
  
-   <span data-ttu-id="5615b-159">`Object` 属性，它包含对要在其中删除成员的维度的对象引用。</span><span class="sxs-lookup"><span data-stu-id="5615b-159">The `Object` property, which contains an object reference for the dimension in which the members are to be dropped.</span></span> <span data-ttu-id="5615b-160">该对象引用包含维度的数据库标识符、多维数据集标识符和维度标识符。</span><span class="sxs-lookup"><span data-stu-id="5615b-160">The object reference contains the database identifier, cube identifier, and dimension identifier for the dimension.</span></span>  
  
-   <span data-ttu-id="5615b-161">`Where` 属性，它包含用于约束要在其中删除成员的特性的一个或多个 `Attribute` 元素。</span><span class="sxs-lookup"><span data-stu-id="5615b-161">The `Where` property, which contains one or more `Attribute` elements to constrain the attributes in which members are to be deleted.</span></span> <span data-ttu-id="5615b-162">`Where` 属性对于将 `Drop` 命令限制于某成员的特定实例来说至关重要。</span><span class="sxs-lookup"><span data-stu-id="5615b-162">The `Where` property is crucial to limiting a `Drop` command to specific instances of a member.</span></span> <span data-ttu-id="5615b-163">如果不指定 `Where` 命令，则将删除给定成员的所有实例。</span><span class="sxs-lookup"><span data-stu-id="5615b-163">If the `Where` command is not specified, all instances of a given member are dropped.</span></span> <span data-ttu-id="5615b-164">例如，您希望从 Redmond 中删除三个客户。</span><span class="sxs-lookup"><span data-stu-id="5615b-164">For example, there are three customers that you want to drop from Redmond.</span></span> <span data-ttu-id="5615b-165">若要删除这三个客户，您必须提供 `Where` 属性，该属性将标识 Customer 特性中要删除的三个成员，以及要在其中删除三个客户的 City 特性的 Redmond 成员。</span><span class="sxs-lookup"><span data-stu-id="5615b-165">To drop these customers, you must provide a `Where` property that identifies the three members in the Customer attribute to be removed and the Redmond member of the City attribute from which the three customers are to be removed.</span></span> <span data-ttu-id="5615b-166">如果 `Where` 属性仅指定 City 特性的 Redmond 成员，则 `Drop` 命令将删除与 Redmond 关联的每个客户。</span><span class="sxs-lookup"><span data-stu-id="5615b-166">If the `Where` property only specifies the Redmond member of the City attribute, every customer associated with Redmond would be dropped by the `Drop` command.</span></span> <span data-ttu-id="5615b-167">如果 `Where` 属性仅指定 Customer 特性中的三个成员，则 `Drop` 命令会将这三个客户全部删除。</span><span class="sxs-lookup"><span data-stu-id="5615b-167">If the `Where` property only specifies the three members in the Customer attribute, the three customers would be deleted entirely by the `Drop` command.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5615b-168">`Attribute` 命令中包含的 `Drop` 元素必须仅包含 `AttributeName` 和 `Keys` 属性。</span><span class="sxs-lookup"><span data-stu-id="5615b-168">The `Attribute` elements included in a `Drop` command must contain only the `AttributeName` and `Keys` properties.</span></span> <span data-ttu-id="5615b-169">否则，可能会出错。</span><span class="sxs-lookup"><span data-stu-id="5615b-169">Otherwise, an error may occur.</span></span>  
  
### <a name="dropping-members-in-parent-attributes"></a><span data-ttu-id="5615b-170">删除父特性中的成员</span><span class="sxs-lookup"><span data-stu-id="5615b-170">Dropping Members in Parent Attributes</span></span>  
 <span data-ttu-id="5615b-171">设置[DeleteWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/deletewithdescendants-element-xmla)属性指示还应使用父成员删除父成员的后代。</span><span class="sxs-lookup"><span data-stu-id="5615b-171">Setting the [DeleteWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/deletewithdescendants-element-xmla) property indicates that the descendants of a parent member should also be deleted with the parent member.</span></span> <span data-ttu-id="5615b-172">如果将此值设置为 False，则父成员的直接后代将提升到该父成员先前所处的级别。</span><span class="sxs-lookup"><span data-stu-id="5615b-172">If this value is set to false, the immediate descendants of the parent member are instead promoted to the level in which the parent member formerly resided.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5615b-173">用户只需删除父成员的权限，即可删除父成员及其后代。</span><span class="sxs-lookup"><span data-stu-id="5615b-173">A user needs only to have delete permissions for the parent member to delete both the parent member and its descendants.</span></span> <span data-ttu-id="5615b-174">用户无需删除后代的权限。</span><span class="sxs-lookup"><span data-stu-id="5615b-174">A user does not need delete permissions on the descendants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5615b-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5615b-175">See Also</span></span>  
 <span data-ttu-id="5615b-176">[Drop 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="5615b-176">[Drop Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) </span></span>  
 <span data-ttu-id="5615b-177">[&#40;XMLA&#41;插入元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="5615b-177">[Insert Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla) </span></span>  
 <span data-ttu-id="5615b-178">[&#40;XMLA&#41;更新元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="5615b-178">[Update Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla) </span></span>  
 <span data-ttu-id="5615b-179">[&#40;XMLA 定义和标识对象&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects) </span><span class="sxs-lookup"><span data-stu-id="5615b-179">[Defining and Identifying Objects &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects) </span></span>  
 [<span data-ttu-id="5615b-180">在 Analysis Services 中使用 XMLA 开发</span><span class="sxs-lookup"><span data-stu-id="5615b-180">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
