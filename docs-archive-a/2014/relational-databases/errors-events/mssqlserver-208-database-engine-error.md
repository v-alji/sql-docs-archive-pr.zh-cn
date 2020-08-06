---
title: MSSQLSERVER_208 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 208 (Database Engine error)
ms.assetid: 4b1895f5-3197-4da1-af86-954c93507956
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 97ab3eb220c03c3de0c95251861f3b947890b090
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577724"
---
# <a name="mssqlserver_208"></a><span data-ttu-id="a8003-102">MSSQLSERVER_208</span><span class="sxs-lookup"><span data-stu-id="a8003-102">MSSQLSERVER_208</span></span>
    
## <a name="details"></a><span data-ttu-id="a8003-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="a8003-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a8003-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="a8003-104">Product Name</span></span>|<span data-ttu-id="a8003-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a8003-105">SQL Server</span></span>|  
|<span data-ttu-id="a8003-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="a8003-106">Event ID</span></span>|<span data-ttu-id="a8003-107">208</span><span class="sxs-lookup"><span data-stu-id="a8003-107">208</span></span>|  
|<span data-ttu-id="a8003-108">事件源</span><span class="sxs-lookup"><span data-stu-id="a8003-108">Event Source</span></span>|<span data-ttu-id="a8003-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a8003-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a8003-110">组件</span><span class="sxs-lookup"><span data-stu-id="a8003-110">Component</span></span>|<span data-ttu-id="a8003-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a8003-111">SQLEngine</span></span>|  
|<span data-ttu-id="a8003-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="a8003-112">Symbolic Name</span></span>|<span data-ttu-id="a8003-113">SQ_BADOBJECT</span><span class="sxs-lookup"><span data-stu-id="a8003-113">SQ_BADOBJECT</span></span>|  
|<span data-ttu-id="a8003-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="a8003-114">Message Text</span></span>|<span data-ttu-id="a8003-115">对象名 '%.\*ls' 无效。</span><span class="sxs-lookup"><span data-stu-id="a8003-115">Invalid object name '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a8003-116">说明</span><span class="sxs-lookup"><span data-stu-id="a8003-116">Explanation</span></span>  
 <span data-ttu-id="a8003-117">找不到指定的对象。</span><span class="sxs-lookup"><span data-stu-id="a8003-117">The specified object cannot be found.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="a8003-118">可能的原因</span><span class="sxs-lookup"><span data-stu-id="a8003-118">Possible Causes</span></span>  
 <span data-ttu-id="a8003-119">此错误可能是由以下问题之一导致的：</span><span class="sxs-lookup"><span data-stu-id="a8003-119">This error can be caused by one of the following problems:</span></span>  
  
-   <span data-ttu-id="a8003-120">未正确指定对象。</span><span class="sxs-lookup"><span data-stu-id="a8003-120">The object is not specified correctly.</span></span>  
  
-   <span data-ttu-id="a8003-121">当前的数据库或指定的数据库中不存在该对象。</span><span class="sxs-lookup"><span data-stu-id="a8003-121">The object does not exist in the current database or in the specified database.</span></span>  
  
-   <span data-ttu-id="a8003-122">该对象存在，但无法向用户公开。</span><span class="sxs-lookup"><span data-stu-id="a8003-122">The object exists, but could not be exposed to the user.</span></span> <span data-ttu-id="a8003-123">例如，用户对于该对象可能不具有权限，或者该对象创建于 EXECUTE 语句内部，而用户却从 EXECUTE 语句的作用域外部访问它。</span><span class="sxs-lookup"><span data-stu-id="a8003-123">For example, the user might not have permissions on the object or the object is created within an EXECUTE statement but accessed outside the scope of the EXECUTE statement.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a8003-124">用户操作</span><span class="sxs-lookup"><span data-stu-id="a8003-124">User Action</span></span>  
 <span data-ttu-id="a8003-125">查看以下信息并根据需要更正该语句。</span><span class="sxs-lookup"><span data-stu-id="a8003-125">Verify the following information and correct the statement as appropriate.</span></span>  
  
-   <span data-ttu-id="a8003-126">对象名的拼写是否正确。</span><span class="sxs-lookup"><span data-stu-id="a8003-126">The object name is spelled correctly.</span></span>  
  
-   <span data-ttu-id="a8003-127">当前数据库的上下文是否正确。</span><span class="sxs-lookup"><span data-stu-id="a8003-127">The current database context is correct.</span></span> <span data-ttu-id="a8003-128">如果没有为该对象指定数据库名称，则当前数据库中必须存在该对象。</span><span class="sxs-lookup"><span data-stu-id="a8003-128">If a database name for the object is not specified, the object must exist in the current database.</span></span> <span data-ttu-id="a8003-129">有关设置数据库上下文的详细信息，请参阅 [USE (Transact-SQL)](/sql/t-sql/language-elements/use-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a8003-129">For more information about setting the database context, see [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).</span></span>  
  
-   <span data-ttu-id="a8003-130">系统表中是否存在该对象。</span><span class="sxs-lookup"><span data-stu-id="a8003-130">The object exists in the system tables.</span></span> <span data-ttu-id="a8003-131">若要验证是否存在表或其他架构范围内的对象，请查询 **sys.objects** 目录视图。</span><span class="sxs-lookup"><span data-stu-id="a8003-131">To verify whether a table or other schema-scoped object exists, query the **sys.objects** catalog view.</span></span> <span data-ttu-id="a8003-132">如果系统表中没有此对象，则表明此对象已删除或者用户没有查看此对象元数据的权限。</span><span class="sxs-lookup"><span data-stu-id="a8003-132">If the object is not in the system tables, the object has been deleted, or the user does not have permissions to view the object metadata.</span></span> <span data-ttu-id="a8003-133">有关查看对象元数据的权限的详细信息，请参阅[元数据可见性配置](../security/metadata-visibility-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="a8003-133">For more information about permissions to view object metadata, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
-   <span data-ttu-id="a8003-134">该对象是否包含在用户的默认架构中。</span><span class="sxs-lookup"><span data-stu-id="a8003-134">The object is contained in the default schema of the user.</span></span> <span data-ttu-id="a8003-135">如果不包含在默认架构中，则必须使用两部分格式 *schema_name.object_name* 来指定该对象。</span><span class="sxs-lookup"><span data-stu-id="a8003-135">If it is not, the object must be specified using the two-part format *schema_name.object_name*.</span></span> <span data-ttu-id="a8003-136">请注意，必须始终使用至少由两部分组成的名称来调用标量值函数。</span><span class="sxs-lookup"><span data-stu-id="a8003-136">Note that scalar-valued functions must always be invoked by using at least a two-part name.</span></span>  
  
-   <span data-ttu-id="a8003-137">数据库排序规则区分大小写。</span><span class="sxs-lookup"><span data-stu-id="a8003-137">The case sensitivity of the database collation.</span></span>  
  
     <span data-ttu-id="a8003-138">当数据库使用区分大小写的排序规则时，对象名的大小写必须与数据库中对象的大小写一致。</span><span class="sxs-lookup"><span data-stu-id="a8003-138">When a database uses a case-sensitive collation, the object name must match the case of the object in the database.</span></span> <span data-ttu-id="a8003-139">例如，如果使用区分大小写的排序规则在数据库中将某个对象指定为 **MyTable**，那么，以 **mytable** 或 **Mytable** 形式引用该对象的查询将因对象名不匹配而导致返回错误 208。</span><span class="sxs-lookup"><span data-stu-id="a8003-139">For example, when an object is specified as **MyTable** in a database with a case sensitive collation, queries that refer to the object as **mytable** or **Mytable** will cause error 208 to return because the object names do not match.</span></span>  
  
     <span data-ttu-id="a8003-140">您可以通过运行下面的语句来检验数据库排序规则。</span><span class="sxs-lookup"><span data-stu-id="a8003-140">You can verify the database collation by running the following statement.</span></span>  
  
    ```  
    SELECT collation_name FROM sys.databases WHERE name = 'database_name';  
    ```  
  
     <span data-ttu-id="a8003-141">排序规则名称中的缩写 CS 指示排序规则区分大小写。</span><span class="sxs-lookup"><span data-stu-id="a8003-141">The abbreviation CS in the collation name indicates the collation is case sensitive.</span></span> <span data-ttu-id="a8003-142">例如，Latin1_General_CS_AS 是一个区分大小写和重音符号的排序规则。</span><span class="sxs-lookup"><span data-stu-id="a8003-142">For example, Latin1_General_CS_AS is a case sensitive, accent sensitive collation.</span></span> <span data-ttu-id="a8003-143">CI 指示排序规则不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="a8003-143">CI indicates a case insensitive collation.</span></span>  
  
-   <span data-ttu-id="a8003-144">用户是否有权访问该对象。</span><span class="sxs-lookup"><span data-stu-id="a8003-144">The user has permission to access the object.</span></span> <span data-ttu-id="a8003-145">若要验证用户是否有权访问该对象，请使用 **Has_Perms_By_Name** 系统函数。</span><span class="sxs-lookup"><span data-stu-id="a8003-145">To verify the permissions the user has on the object, use the **Has_Perms_By_Name** system function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8003-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8003-146">See Also</span></span>  
 <span data-ttu-id="a8003-147">[使用 &#40;Transact-sql&#41;](/sql/t-sql/language-elements/use-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a8003-147">[USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql) </span></span>  
 <span data-ttu-id="a8003-148">[元数据可见性配置](../security/metadata-visibility-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="a8003-148">[Metadata Visibility Configuration](../security/metadata-visibility-configuration.md) </span></span>  
 [<span data-ttu-id="a8003-149">HAS_PERMS_BY_NAME (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a8003-149">HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/has-perms-by-name-transact-sql)  
  
  
