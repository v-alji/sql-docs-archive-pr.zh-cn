---
title: 搜索属性列表编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.searchpropertylisteditor.f1
ms.assetid: 0f3ced6e-0dfd-49fc-b175-82378c3d668e
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c68ec986e2c6f4f53dfec7f188ba2a120532ae4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580863"
---
# <a name="search-property-list-editor"></a><span data-ttu-id="99c3a-102">搜索属性列表编辑器</span><span class="sxs-lookup"><span data-stu-id="99c3a-102">Search Property List Editor</span></span>
  <span data-ttu-id="99c3a-103">使用此对话框可以在搜索属性列表中添加或删除搜索属性。</span><span class="sxs-lookup"><span data-stu-id="99c3a-103">Use this dialog box to add or delete search properties in a search property list.</span></span>  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a><span data-ttu-id="99c3a-104">使用 SQL Server Management Studio 管理搜索属性列表</span><span class="sxs-lookup"><span data-stu-id="99c3a-104">To Use SQL Server Management Studio to Manage Search Property Lists</span></span>  
 <span data-ttu-id="99c3a-105">有关如何创建、查看或删除搜索属性列表以及如何为属性搜索配置全文索引的信息，请参阅[使用搜索属性列表搜索文档属性](../relational-databases/search/search-document-properties-with-search-property-lists.md)。</span><span class="sxs-lookup"><span data-stu-id="99c3a-105">For information about how to create, view, or delete a search property list, and about how to configure a full-text index for property searching, see [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="99c3a-106">选项</span><span class="sxs-lookup"><span data-stu-id="99c3a-106">Options</span></span>  
 <span data-ttu-id="99c3a-107">**属性名称**</span><span class="sxs-lookup"><span data-stu-id="99c3a-107">**Property Name**</span></span>  
 <span data-ttu-id="99c3a-108">指定要用来标识全文查询中的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="99c3a-108">Specify the name to be used to identify the property in full-text queries.</span></span> <span data-ttu-id="99c3a-109">属性名称可以包含内部空格。</span><span class="sxs-lookup"><span data-stu-id="99c3a-109">A property name can contain internal spaces.</span></span> <span data-ttu-id="99c3a-110">**“属性名称”** 的最大长度为 256 个字符。</span><span class="sxs-lookup"><span data-stu-id="99c3a-110">The maximum length of **Property Name** is 256 characters.</span></span> <span data-ttu-id="99c3a-111">此名称可以是“作者”或“家庭地址”等此类用户友好名称，也可以是 Windows 的属性规范名称，如 `System.Author` 或 `System.Contact.HomeAddress`。</span><span class="sxs-lookup"><span data-stu-id="99c3a-111">This name can be a user-friendly name, such as "Author" or "Home Address", or it can be the Windows canonical name of the property, such as `System.Author` or `System.Contact.HomeAddress`.</span></span> <span data-ttu-id="99c3a-112">**“属性名称”** 必须唯一标识属性集中的属性。</span><span class="sxs-lookup"><span data-stu-id="99c3a-112">**Property Name** must uniquely identify the property within the property set.</span></span>  
  
 <span data-ttu-id="99c3a-113">开发人员使用属性名称来标识 [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 谓词中的属性。</span><span class="sxs-lookup"><span data-stu-id="99c3a-113">Developers use the property name to identify the property in the [CONTAINS](/sql/t-sql/queries/contains-transact-sql) predicate.</span></span> <span data-ttu-id="99c3a-114">因此，当添加属性时，务必指定一个在含义上表示该属性的值。</span><span class="sxs-lookup"><span data-stu-id="99c3a-114">Therefore, when adding a property it is important to specify a value that meaningfully represents the property.</span></span>  
  
 <span data-ttu-id="99c3a-115">**属性集 GUID**</span><span class="sxs-lookup"><span data-stu-id="99c3a-115">**Property Set GUID**</span></span>  
 <span data-ttu-id="99c3a-116">指定属性所属的属性集的标识符。</span><span class="sxs-lookup"><span data-stu-id="99c3a-116">Specify the identifier of the property set to which the property belongs.</span></span> <span data-ttu-id="99c3a-117">这是全局唯一标识符 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="99c3a-117">This is a globally unique identifier (GUID).</span></span> <span data-ttu-id="99c3a-118">属性集是一组在逻辑上相关的属性。</span><span class="sxs-lookup"><span data-stu-id="99c3a-118">A property set is a group of logically related properties.</span></span> <span data-ttu-id="99c3a-119">有关获取此值的信息，请参阅本主题后面的“备注”。</span><span class="sxs-lookup"><span data-stu-id="99c3a-119">For information about obtaining this value, see "Remarks," later in this topic.</span></span>  
  
 <span data-ttu-id="99c3a-120">**属性 Int ID**</span><span class="sxs-lookup"><span data-stu-id="99c3a-120">**Property Int ID**</span></span>  
 <span data-ttu-id="99c3a-121">指定属性的属性整型标识符。</span><span class="sxs-lookup"><span data-stu-id="99c3a-121">Specify the property integer identifier of the property.</span></span> <span data-ttu-id="99c3a-122">这一预先分配的值是一个正整数，它在属性集中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="99c3a-122">This pre-assigned value is a positive integer that is unique within the property set.</span></span> <span data-ttu-id="99c3a-123">有关获取此值的信息，请参阅本主题后面的“备注”。</span><span class="sxs-lookup"><span data-stu-id="99c3a-123">For information about obtaining this value, see "Remarks," later in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="99c3a-124">全文搜索不支持使用字符串标识符的文档属性。</span><span class="sxs-lookup"><span data-stu-id="99c3a-124">Document properties that use string identifiers are not supported by full-text search.</span></span>  
  
 <span data-ttu-id="99c3a-125">**属性说明**</span><span class="sxs-lookup"><span data-stu-id="99c3a-125">**Property Description**</span></span>  
 <span data-ttu-id="99c3a-126">指定属性的说明（可选）。</span><span class="sxs-lookup"><span data-stu-id="99c3a-126">Optionally, specify a description of the property.</span></span> <span data-ttu-id="99c3a-127">这是一个最多 512 个字符的字符串。</span><span class="sxs-lookup"><span data-stu-id="99c3a-127">This is a string of up to 512 characters.</span></span> <span data-ttu-id="99c3a-128">例如，说明可能包含有关属性的属性集的信息，或者包含有关从名称上不能直接看出其含义的属性的信息。</span><span class="sxs-lookup"><span data-stu-id="99c3a-128">For example, a description could contain information about the property set of the property or information about a property that is not evident from its name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99c3a-129">备注</span><span class="sxs-lookup"><span data-stu-id="99c3a-129">Remarks</span></span>  
 <span data-ttu-id="99c3a-130">若要向搜索属性列表添加搜索属性，必须为此属性所属的属性集指定全局唯一标识符 (GUID)，并指定此属性的属性整型标识符。</span><span class="sxs-lookup"><span data-stu-id="99c3a-130">To add a search property to a search property list, you must specify the globally unique identifier (GUID) of the property set to which the property belongs and the property integer identifier of the property.</span></span> <span data-ttu-id="99c3a-131">这些标识符的给定组合在给定的搜索属性列表中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="99c3a-131">A given combination of these must be unique in a given search property list.</span></span> <span data-ttu-id="99c3a-132">如果试图添加一个现有组合，则此操作将失败并且会发出错误。</span><span class="sxs-lookup"><span data-stu-id="99c3a-132">If you try to add an existing combination, the operation fails and issues an error.</span></span> <span data-ttu-id="99c3a-133">这意味着，您只能为给定属性配置一个名称。</span><span class="sxs-lookup"><span data-stu-id="99c3a-133">This means that you can configure only one name for a given property.</span></span>  
  
 <span data-ttu-id="99c3a-134">属性说明是可选的。</span><span class="sxs-lookup"><span data-stu-id="99c3a-134">The property description is optional.</span></span>  
  
 <span data-ttu-id="99c3a-135">**配置搜索属性列表以进行全文索引**</span><span class="sxs-lookup"><span data-stu-id="99c3a-135">**To configure a search property list for a full-text index**</span></span>  
  
-   [<span data-ttu-id="99c3a-136">使用搜索属性列表搜索文档属性</span><span class="sxs-lookup"><span data-stu-id="99c3a-136">Search Document Properties with Search Property Lists</span></span>](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
## <a name="permissions"></a><span data-ttu-id="99c3a-137">权限</span><span class="sxs-lookup"><span data-stu-id="99c3a-137">Permissions</span></span>  
 <span data-ttu-id="99c3a-138">请参阅[ALTER SEARCH PROPERTY LIST &#40;transact-sql&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="99c3a-138">See [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c3a-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99c3a-139">See Also</span></span>  
 <span data-ttu-id="99c3a-140">[&#40;Transact-sql&#41;更改搜索属性列表](/sql/t-sql/statements/alter-search-property-list-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="99c3a-140">[ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) </span></span>  
 <span data-ttu-id="99c3a-141">[用搜索属性列表搜索文档属性](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span><span class="sxs-lookup"><span data-stu-id="99c3a-141">[Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span></span>  
 [<span data-ttu-id="99c3a-142">sys.registered_search_property_lists (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="99c3a-142">sys.registered_search_property_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  
