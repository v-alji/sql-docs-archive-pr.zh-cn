---
title: 属性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- free-form attributes [Master Data Services]
- attributes [Master Data Services], about attributes
- attributes [Master Data Services], file attributes
- file attributes [Master Data Services]
- attributes [Master Data Services], free-form attributes
- attributes [Master Data Services]
ms.assetid: 95ecb75f-c559-41c3-933c-40ae60a4c2fd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5a6fb01b47658f39e14c599ae88aa7ad3d29c69a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589748"
---
# <a name="attributes-master-data-services"></a><span data-ttu-id="1ae17-102">属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1ae17-102">Attributes (Master Data Services)</span></span>
  <span data-ttu-id="1ae17-103">属性是 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 实体中包含的对象。</span><span class="sxs-lookup"><span data-stu-id="1ae17-103">Attributes are objects that are contained in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] entities.</span></span> <span data-ttu-id="1ae17-104">属性值描述实体的成员。</span><span class="sxs-lookup"><span data-stu-id="1ae17-104">Attribute values describe the members of the entity.</span></span> <span data-ttu-id="1ae17-105">属性可用于描述叶成员、合并成员或集合。</span><span class="sxs-lookup"><span data-stu-id="1ae17-105">An attribute can be used to describe a leaf member, a consolidated member, or a collection.</span></span>  
  
## <a name="how-attributes-relate-to-other-model-objects"></a><span data-ttu-id="1ae17-106">属性如何与其他模型对象关联</span><span class="sxs-lookup"><span data-stu-id="1ae17-106">How Attributes Relate to Other Model Objects</span></span>  
 <span data-ttu-id="1ae17-107">您可以将属性视作实体表中的列。</span><span class="sxs-lookup"><span data-stu-id="1ae17-107">You can think of an attribute as a column in an entity table.</span></span> <span data-ttu-id="1ae17-108">属性值是用于描述特定成员的值。</span><span class="sxs-lookup"><span data-stu-id="1ae17-108">An attribute value is the value used to describe a specific member.</span></span>  
  
 <span data-ttu-id="1ae17-109">![表示为表的 Master Data Services 实体](../../2014/master-data-services/media/mds-conc-entity-table.gif "表示为表的 Master Data Services 实体")</span><span class="sxs-lookup"><span data-stu-id="1ae17-109">![Master Data Services Entity Represented as Table](../../2014/master-data-services/media/mds-conc-entity-table.gif "Master Data Services Entity Represented as Table")</span></span>  
  
 <span data-ttu-id="1ae17-110">创建包含很多属性的实体时，可以将属性组织为属性组。</span><span class="sxs-lookup"><span data-stu-id="1ae17-110">When you create an entity that contains many attributes, you can organize the attributes into attribute groups.</span></span> <span data-ttu-id="1ae17-111">有关详细信息，请参阅 [属性组 (Master Data Services)](attribute-groups-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae17-111">For more information, see [Attribute Groups &#40;Master Data Services&#41;](attribute-groups-master-data-services.md).</span></span>  
  
## <a name="required-attributes"></a><span data-ttu-id="1ae17-112">必需的属性</span><span class="sxs-lookup"><span data-stu-id="1ae17-112">Required Attributes</span></span>  
 <span data-ttu-id="1ae17-113">创建实体时，将自动创建 Name 和 Code 属性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-113">When you create an entity, the Name and Code attributes are automatically created.</span></span> <span data-ttu-id="1ae17-114">Code 需要一个值，并且必须在实体中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="1ae17-114">Code requires a value and must be unique within the entity.</span></span> <span data-ttu-id="1ae17-115">不能删除 Name 和 Code 属性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-115">You cannot remove the Name and Code attributes.</span></span>  
  
## <a name="attribute-types"></a><span data-ttu-id="1ae17-116">属性类型</span><span class="sxs-lookup"><span data-stu-id="1ae17-116">Attribute Types</span></span>  
 <span data-ttu-id="1ae17-117">有三种类型的属性：</span><span class="sxs-lookup"><span data-stu-id="1ae17-117">There are three types of attributes:</span></span>  
  
-   <span data-ttu-id="1ae17-118">自由格式的属性，允许针对文本、数字、日期或链接的自由格式的输入。</span><span class="sxs-lookup"><span data-stu-id="1ae17-118">Free-form attributes, which allow free-form input for text, numbers, dates, or links.</span></span>  
  
-   <span data-ttu-id="1ae17-119">基于域的属性，由实体填充。</span><span class="sxs-lookup"><span data-stu-id="1ae17-119">Domain-based attributes, which are populated by entities.</span></span> <span data-ttu-id="1ae17-120">有关详细信息，请参阅 [基于域的属性 (Master Data Services)](../../2014/master-data-services/domain-based-attributes-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae17-120">For more information, see [Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="1ae17-121">文件属性，用于存储文件、文档或图像。</span><span class="sxs-lookup"><span data-stu-id="1ae17-121">File attributes, which are used to store files, documents, or images.</span></span> <span data-ttu-id="1ae17-122">文件属性旨在通过要求文件具有特定的扩展名，帮助确保数据的一致性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-122">File attributes are intended to help with the consistency of your data by requiring files to have a specific extension.</span></span> <span data-ttu-id="1ae17-123">文件属性不一定能够防止恶意用户上载不同类型的文件。</span><span class="sxs-lookup"><span data-stu-id="1ae17-123">File attributes cannot be guaranteed to prevent a malicious user from uploading a file of a different type.</span></span>  
  
### <a name="numeric-free-form-attributes"></a><span data-ttu-id="1ae17-124">数字自由格式属性</span><span class="sxs-lookup"><span data-stu-id="1ae17-124">Numeric Free-Form Attributes</span></span>  
 <span data-ttu-id="1ae17-125">数字自由格式属性值需要特殊处理，因为它们被限制为 **SqlDouble** 值类型。</span><span class="sxs-lookup"><span data-stu-id="1ae17-125">Numeric free-form attributes require special handling, because numeric free-form attribute values are limited to the **SqlDouble** value type.</span></span>  
  
 <span data-ttu-id="1ae17-126">默认情况下， **SqlDouble** 值包含 15 个小数位数的精度，尽管它在内部维护最大 17 位的精度。</span><span class="sxs-lookup"><span data-stu-id="1ae17-126">By default, a **SqlDouble** value contains 15 decimal digits of precision, although a maximum of 17 digits is maintained internally.</span></span> <span data-ttu-id="1ae17-127">浮点数的精度具有以下若干影响：</span><span class="sxs-lookup"><span data-stu-id="1ae17-127">The precision of a floating-point number has several consequences:</span></span>  
  
-   <span data-ttu-id="1ae17-128">对于特定精度，看起来相等的两个浮点数在进行比较时可能不相等，因为其最小有效位不同。</span><span class="sxs-lookup"><span data-stu-id="1ae17-128">Two floating-point numbers that appear equal for a particular precision might not compare equal because their least significant digits are different.</span></span>  
  
-   <span data-ttu-id="1ae17-129">在使用小数时，使用浮点数的算术或比较运算不一定产生相同结果，因为浮点数可能无法精确表示小数。</span><span class="sxs-lookup"><span data-stu-id="1ae17-129">A mathematical or comparison operation that uses a floating-point number might not yield the same result if a decimal number is used because the floating-point number might not exactly approximate the decimal number.</span></span>  
  
-   <span data-ttu-id="1ae17-130">如果包含浮点数，值可能无法“往返转换”。\*\*</span><span class="sxs-lookup"><span data-stu-id="1ae17-130">A value might not *roundtrip* if a floating-point number is involved.</span></span> <span data-ttu-id="1ae17-131">如果某一运算将原始浮点数转换为其他形式，而相反运算将已转换形式转换回浮点数，并且最终生成的浮点数与原始浮点数相等，则值被认为是往返转换。</span><span class="sxs-lookup"><span data-stu-id="1ae17-131">A value is said to roundtrip if an operation converts an original floating-point number to another form, an inverse operation transforms the converted form back to a floating-point number, and the final floating-point number is equal to the original floating-point number.</span></span> <span data-ttu-id="1ae17-132">因为在转换过程中一个或多个最小有效位缺失或更改，所以该往返转换可能失败。</span><span class="sxs-lookup"><span data-stu-id="1ae17-132">The roundtrip might fail because one or more least significant digits are lost or changed in a conversion.</span></span>  
  
## <a name="attribute-examples"></a><span data-ttu-id="1ae17-133">属性示例</span><span class="sxs-lookup"><span data-stu-id="1ae17-133">Attribute Examples</span></span>  
 <span data-ttu-id="1ae17-134">在下面的示例中，实体具有 Name、Code、Subcategory、StandardCost、ListPrice 和 FilePhoto 属性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-134">In the following example, the entity has the attributes: Name, Code, Subcategory, StandardCost, ListPrice, and FilePhoto.</span></span> <span data-ttu-id="1ae17-135">这些属性描述成员。</span><span class="sxs-lookup"><span data-stu-id="1ae17-135">These attributes describe the members.</span></span> <span data-ttu-id="1ae17-136">每个成员由一行属性值表示。</span><span class="sxs-lookup"><span data-stu-id="1ae17-136">Each member is represented by a single row of attribute values.</span></span>  
  
 <span data-ttu-id="1ae17-137">![自行车产品实体表](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "自行车产品实体表")</span><span class="sxs-lookup"><span data-stu-id="1ae17-137">![Bike Product Entity Table](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Bike Product Entity Table")</span></span>  
  
 <span data-ttu-id="1ae17-138">在下面的示例中，Product 实体包含：</span><span class="sxs-lookup"><span data-stu-id="1ae17-138">In the following example, the Product entity contains:</span></span>  
  
-   <span data-ttu-id="1ae17-139">Name、Code、StandardCost 和 ListPrice 的自由格式属性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-139">The free-form attributes of Name, Code, StandardCost and ListPrice.</span></span>  
  
-   <span data-ttu-id="1ae17-140">Subcategory 的基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-140">The domain-based attribute of Subcategory.</span></span>  
  
-   <span data-ttu-id="1ae17-141">FilePhoto 的文件属性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-141">The file attribute of FilePhoto.</span></span>  
  
 <span data-ttu-id="1ae17-142">Subcategory 是用作 Product 的基于域的属性的实体。</span><span class="sxs-lookup"><span data-stu-id="1ae17-142">Subcategory is an entity that is used as a domain-based attribute of Product.</span></span> <span data-ttu-id="1ae17-143">Category 是用作 Subcategory 的基于域的属性的实体。</span><span class="sxs-lookup"><span data-stu-id="1ae17-143">Category is an entity that is used as a domain-based attribute of Subcategory.</span></span> <span data-ttu-id="1ae17-144">与 Product 实体一样，Category 和 Subcategory 实体各自包含默认 Name 和 Code 属性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-144">Like the Product entity, the Category and Subcategory entities each contain the default Name and Code attributes.</span></span>  
  
 <span data-ttu-id="1ae17-145">![产品实体树结构](../../2014/master-data-services/media/mds-conc-entity-ui.gif "产品实体树结构")</span><span class="sxs-lookup"><span data-stu-id="1ae17-145">![Product Entity Tree Structure](../../2014/master-data-services/media/mds-conc-entity-ui.gif "Product Entity Tree Structure")</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1ae17-146">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="1ae17-146">Related Tasks</span></span>  
  
|<span data-ttu-id="1ae17-147">任务说明</span><span class="sxs-lookup"><span data-stu-id="1ae17-147">Task Description</span></span>|<span data-ttu-id="1ae17-148">主题</span><span class="sxs-lookup"><span data-stu-id="1ae17-148">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="1ae17-149">创建新的自由格式的文本属性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-149">Create a new free-form text attribute.</span></span>|[<span data-ttu-id="1ae17-150">创建文本属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1ae17-150">Create a Text Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)|  
|<span data-ttu-id="1ae17-151">创建新的自由格式的数字属性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-151">Create a new free-form numeric attribute.</span></span>|[<span data-ttu-id="1ae17-152">创建数字属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1ae17-152">Create a Numeric Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md)|  
|<span data-ttu-id="1ae17-153">创建新的自由格式的链接属性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-153">Create a new free-form link attribute.</span></span>|[<span data-ttu-id="1ae17-154">创建链接属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1ae17-154">Create a Link Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-link-attribute-master-data-services.md)|  
|<span data-ttu-id="1ae17-155">创建新的文件属性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-155">Create a new file attribute.</span></span>|[<span data-ttu-id="1ae17-156">创建文件属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1ae17-156">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)|  
|<span data-ttu-id="1ae17-157">创建新的基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-157">Create a new domain-based attribute.</span></span>|[<span data-ttu-id="1ae17-158">创建基于域的属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1ae17-158">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|<span data-ttu-id="1ae17-159">更改现有属性的名称。</span><span class="sxs-lookup"><span data-stu-id="1ae17-159">Change the name of an existing attribute.</span></span>|[<span data-ttu-id="1ae17-160">更改属性名称 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ae17-160">Change an Attribute Name &#40;Master Data Services&#41;</span></span>](change-an-attribute-name-and-data-type-master-data-services.md)|  
|<span data-ttu-id="1ae17-161">向更改跟踪组添加现有属性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-161">Add existing attributes to a change tracking group.</span></span>|[<span data-ttu-id="1ae17-162">向更改跟踪组添加属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1ae17-162">Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|<span data-ttu-id="1ae17-163">删除现有属性。</span><span class="sxs-lookup"><span data-stu-id="1ae17-163">Delete an existing attribute.</span></span>|[<span data-ttu-id="1ae17-164">删除属性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ae17-164">Delete an Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-attribute-master-data-services.md)|  
|<span data-ttu-id="1ae17-165">更改属性的顺序。</span><span class="sxs-lookup"><span data-stu-id="1ae17-165">Change the order of attributes.</span></span>|[<span data-ttu-id="1ae17-166">更改属性的顺序</span><span class="sxs-lookup"><span data-stu-id="1ae17-166">Change the Order of Attributes</span></span>](../../2014/master-data-services/change-the-order-of-attributes.md)|  
  
## <a name="related-content"></a><span data-ttu-id="1ae17-167">相关内容</span><span class="sxs-lookup"><span data-stu-id="1ae17-167">Related Content</span></span>  
  
-   [<span data-ttu-id="1ae17-168">基于域的属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1ae17-168">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
-   [<span data-ttu-id="1ae17-169">属性组 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1ae17-169">Attribute Groups &#40;Master Data Services&#41;</span></span>](attribute-groups-master-data-services.md)  
  
-   [<span data-ttu-id="1ae17-170">成员 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ae17-170">Members &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/members-master-data-services.md)  
  
-   [<span data-ttu-id="1ae17-171">叶权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1ae17-171">Leaf Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/leaf-permissions-master-data-services.md)  
  
-   [<span data-ttu-id="1ae17-172">&#40;Master Data Services 的合并权限&#41;</span><span class="sxs-lookup"><span data-stu-id="1ae17-172">Consolidated Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  
