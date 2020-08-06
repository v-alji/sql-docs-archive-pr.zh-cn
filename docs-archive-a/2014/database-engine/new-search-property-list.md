---
title: 新搜索属性列表 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.newsearchpropertylist.f1
ms.assetid: ffca78e9-8608-4b15-bd38-b2d78da4247a
author: rothja
ms.author: jroth
ms.openlocfilehash: 48c9e475b380d5f0c7310e33717f261c38acbbd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590352"
---
# <a name="new-search-property-list"></a><span data-ttu-id="78950-102">新建搜索属性列表</span><span class="sxs-lookup"><span data-stu-id="78950-102">New Search Property List</span></span>
  <span data-ttu-id="78950-103">使用此对话框可以创建搜索属性列表。</span><span class="sxs-lookup"><span data-stu-id="78950-103">Use this dialog box to create a search property list.</span></span>  
  
## <a name="options"></a><span data-ttu-id="78950-104">选项</span><span class="sxs-lookup"><span data-stu-id="78950-104">Options</span></span>  
 <span data-ttu-id="78950-105">**搜索属性列表名称**</span><span class="sxs-lookup"><span data-stu-id="78950-105">**Search property list name**</span></span>  
 <span data-ttu-id="78950-106">输入搜索属性列表的名称。</span><span class="sxs-lookup"><span data-stu-id="78950-106">Enter the name of the search property list.</span></span>  
  
 <span data-ttu-id="78950-107">**所有者**</span><span class="sxs-lookup"><span data-stu-id="78950-107">**Owner**</span></span>  
 <span data-ttu-id="78950-108">指定搜索属性列表的所有者。</span><span class="sxs-lookup"><span data-stu-id="78950-108">Specify the owner of the search property list.</span></span> <span data-ttu-id="78950-109">如果希望将所有权分配给您自己（即分配给当前用户），请将此字段留空。</span><span class="sxs-lookup"><span data-stu-id="78950-109">If you want ownership to be assigned to yourself, that is, to the current user, leave this field empty.</span></span> <span data-ttu-id="78950-110">若要指定另一个用户，请单击浏览按钮。</span><span class="sxs-lookup"><span data-stu-id="78950-110">To specify a different user, click the browse button.</span></span>  
  
### <a name="create-search-property-list-options"></a><span data-ttu-id="78950-111">创建搜索属性列表选项</span><span class="sxs-lookup"><span data-stu-id="78950-111">Create Search Property List Options</span></span>  
 <span data-ttu-id="78950-112">单击下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="78950-112">Click one of the following options:</span></span>  
  
 <span data-ttu-id="78950-113">**创建空的搜索属性列表**</span><span class="sxs-lookup"><span data-stu-id="78950-113">**Create an empty search property list**</span></span>  
 <span data-ttu-id="78950-114">创建一个没有任何属性的搜索属性列表。</span><span class="sxs-lookup"><span data-stu-id="78950-114">Creates a search property list without any properties.</span></span>  
  
 <span data-ttu-id="78950-115">**从现有搜索属性列表创建**</span><span class="sxs-lookup"><span data-stu-id="78950-115">**Create from an existing search property list**</span></span>  
 <span data-ttu-id="78950-116">将现有搜索属性列表复制到到新的属性列表。</span><span class="sxs-lookup"><span data-stu-id="78950-116">Copies the properties of an existing search property list into the new property list.</span></span> <span data-ttu-id="78950-117">搜索属性列表是数据库对象，因此，您必须指定包含要复制的属性列表的数据库。</span><span class="sxs-lookup"><span data-stu-id="78950-117">Search property lists are database objects, so you must specify the database that contains the property list that you want to copy.</span></span>  
  
 <span data-ttu-id="78950-118">**源数据库**</span><span class="sxs-lookup"><span data-stu-id="78950-118">**Source database**</span></span>  
 <span data-ttu-id="78950-119">指定现有搜索属性列表所属的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="78950-119">Specify the name of the database to which the existing search property list belongs.</span></span> <span data-ttu-id="78950-120">默认情况下选择当前数据库。</span><span class="sxs-lookup"><span data-stu-id="78950-120">The current database is selected by default.</span></span> <span data-ttu-id="78950-121">（可选）如果当前连接与该数据库中的用户 ID 相关联，您可以使用列表框来选择其他数据库。</span><span class="sxs-lookup"><span data-stu-id="78950-121">Optionally, you can use the list box to select another database, if your current connection is associated with a user ID in that database.</span></span>  
  
 <span data-ttu-id="78950-122">**源搜索属性列表**</span><span class="sxs-lookup"><span data-stu-id="78950-122">**Source search property list**</span></span>  
 <span data-ttu-id="78950-123">从属于所选数据库的搜索属性列表中选择一个现有搜索属性列表的名称。</span><span class="sxs-lookup"><span data-stu-id="78950-123">Select the name of an existing search property list from those belonging to the selected database.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="78950-124">权限</span><span class="sxs-lookup"><span data-stu-id="78950-124">Permissions</span></span>  
 <span data-ttu-id="78950-125">请参阅[CREATE SEARCH PROPERTY LIST &#40;transact-sql&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="78950-125">See [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql).</span></span>  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a><span data-ttu-id="78950-126">使用 SQL Server Management Studio 管理搜索属性列表</span><span class="sxs-lookup"><span data-stu-id="78950-126">To Use SQL Server Management Studio to Manage Search Property Lists</span></span>  
 <span data-ttu-id="78950-127">有关如何创建、查看、更改或删除搜索属性列表以及如何为属性搜索配置全文索引的信息，请参阅 [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md)。</span><span class="sxs-lookup"><span data-stu-id="78950-127">For information about how to create, view, change, or delete a search property list, and about how to configure a full-text index for property searching, see [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78950-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78950-128">See Also</span></span>  
 <span data-ttu-id="78950-129">[&#40;Transact-sql&#41;创建搜索属性列表](/sql/t-sql/statements/create-search-property-list-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="78950-129">[CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql) </span></span>  
 <span data-ttu-id="78950-130">[用搜索属性列表搜索文档属性](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span><span class="sxs-lookup"><span data-stu-id="78950-130">[Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span></span>  
 [<span data-ttu-id="78950-131">sys.registered_search_property_lists (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="78950-131">sys.registered_search_property_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  
