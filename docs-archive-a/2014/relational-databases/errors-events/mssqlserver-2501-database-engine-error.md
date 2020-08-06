---
title: MSSQLSERVER_2501 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2501 (Database Engine error)
ms.assetid: 895aafe3-a4e7-4ed8-acc5-93be76ef3664
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 200997dcfe7bf8a5933b9fce492daabd5baffd04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690623"
---
# <a name="mssqlserver_2501"></a><span data-ttu-id="1b33a-102">MSSQLSERVER_2501</span><span class="sxs-lookup"><span data-stu-id="1b33a-102">MSSQLSERVER_2501</span></span>
    
## <a name="details"></a><span data-ttu-id="1b33a-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="1b33a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1b33a-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="1b33a-104">Product Name</span></span>|<span data-ttu-id="1b33a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1b33a-105">SQL Server</span></span>|  
|<span data-ttu-id="1b33a-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="1b33a-106">Event ID</span></span>|<span data-ttu-id="1b33a-107">2501</span><span class="sxs-lookup"><span data-stu-id="1b33a-107">2501</span></span>|  
|<span data-ttu-id="1b33a-108">事件源</span><span class="sxs-lookup"><span data-stu-id="1b33a-108">Event Source</span></span>|<span data-ttu-id="1b33a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1b33a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1b33a-110">组件</span><span class="sxs-lookup"><span data-stu-id="1b33a-110">Component</span></span>|<span data-ttu-id="1b33a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1b33a-111">SQLEngine</span></span>|  
|<span data-ttu-id="1b33a-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="1b33a-112">Symbolic Name</span></span>|<span data-ttu-id="1b33a-113">DBCC_NO_SUCH_TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1b33a-113">DBCC_NO_SUCH_TABLE_NAME</span></span>|  
|<span data-ttu-id="1b33a-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="1b33a-114">Message Text</span></span>|<span data-ttu-id="1b33a-115">找不到名为 'NAME' 的表或对象。</span><span class="sxs-lookup"><span data-stu-id="1b33a-115">Cannot find a table or object with the name 'NAME'.</span></span> <span data-ttu-id="1b33a-116">请检查系统目录。</span><span class="sxs-lookup"><span data-stu-id="1b33a-116">Check the system catalog.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1b33a-117">说明</span><span class="sxs-lookup"><span data-stu-id="1b33a-117">Explanation</span></span>  
 <span data-ttu-id="1b33a-118">找不到指定的对象。</span><span class="sxs-lookup"><span data-stu-id="1b33a-118">The specified object cannot be found.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="1b33a-119">可能的原因</span><span class="sxs-lookup"><span data-stu-id="1b33a-119">Possible Causes</span></span>  
 <span data-ttu-id="1b33a-120">此错误可能是由以下问题之一导致的：</span><span class="sxs-lookup"><span data-stu-id="1b33a-120">This error can be caused by one of the following problems:</span></span>  
  
-   <span data-ttu-id="1b33a-121">未正确指定对象。</span><span class="sxs-lookup"><span data-stu-id="1b33a-121">The object is not specified correctly.</span></span>  
  
-   <span data-ttu-id="1b33a-122">对象不存在，或在语句使用此对象之前就已删除。</span><span class="sxs-lookup"><span data-stu-id="1b33a-122">The object does not exist, or the object was dropped before a statement tried to use it.</span></span>  
  
-   <span data-ttu-id="1b33a-123">对象可能存在，但无法向用户显示。</span><span class="sxs-lookup"><span data-stu-id="1b33a-123">The object might exist, but could not be exposed to the user.</span></span> <span data-ttu-id="1b33a-124">例如，用户可能对此对象没有权限，或者此对象为用户看不到的内部表。</span><span class="sxs-lookup"><span data-stu-id="1b33a-124">For example, the user might not have permissions on the object, or the object is an internal table that could not be seen by a user.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1b33a-125">用户操作</span><span class="sxs-lookup"><span data-stu-id="1b33a-125">User Action</span></span>  
  
-   <span data-ttu-id="1b33a-126">验证当前数据库上下文是否正确。</span><span class="sxs-lookup"><span data-stu-id="1b33a-126">Verify the current database context is correct.</span></span> <span data-ttu-id="1b33a-127">有关详细信息，请参阅 [USE (Transact-SQL)](/sql/t-sql/language-elements/use-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1b33a-127">For more information, see [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).</span></span>  
  
-   <span data-ttu-id="1b33a-128">验证表或对象名拼写是否正确。</span><span class="sxs-lookup"><span data-stu-id="1b33a-128">Verify that the table or object name is spelled correctly.</span></span>  
  
-   <span data-ttu-id="1b33a-129">验证包含此对象的架构名称。</span><span class="sxs-lookup"><span data-stu-id="1b33a-129">Verify the schema name that contains the object.</span></span> <span data-ttu-id="1b33a-130">如果此对象属于默认 (**dbo**) 架构以外的架构，则必须使用两部分构成方式 *schema_name.object_name* 来指定表名或对象名。</span><span class="sxs-lookup"><span data-stu-id="1b33a-130">If the object belongs to a schema other than the default (**dbo**) schema, you must specify the table or object name by using the two-part format *schema_name.object_name*.</span></span>  
  
-   <span data-ttu-id="1b33a-131">验证此对象是否存在于系统表中。</span><span class="sxs-lookup"><span data-stu-id="1b33a-131">Verify that the object exists in the system tables.</span></span> <span data-ttu-id="1b33a-132">若要验证是否存在表或其他架构范围内的对象，请查询 [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="1b33a-132">To verify whether a table or other schema-scoped object exists, query the [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) catalog view.</span></span> <span data-ttu-id="1b33a-133">如果系统表中没有此对象，则表明此对象已删除或者用户没有查看此对象元数据的权限。</span><span class="sxs-lookup"><span data-stu-id="1b33a-133">If the object is not in the system tables, the object has been deleted, or the user does not have permissions to view the object metadata.</span></span> <span data-ttu-id="1b33a-134">有关如何查看对象元数据的详细信息，请参阅[元数据可见性配置](../security/metadata-visibility-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="1b33a-134">For more information about how to view object metadata, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b33a-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b33a-135">See Also</span></span>  
 [<span data-ttu-id="1b33a-136">目录视图 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1b33a-136">Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)  
  
  
