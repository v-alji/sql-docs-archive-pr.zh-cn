---
title: MSSQLSERVER_1505 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1505 (Database Engine error)
ms.assetid: ef4df75d-0f36-4c8b-b36c-e427f65f91ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 74c152404cf2d3710bbe98b29da7a96d86f58859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688937"
---
# <a name="mssqlserver_1505"></a><span data-ttu-id="6e5f0-102">MSSQLSERVER_1505</span><span class="sxs-lookup"><span data-stu-id="6e5f0-102">MSSQLSERVER_1505</span></span>
    
## <a name="details"></a><span data-ttu-id="6e5f0-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="6e5f0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e5f0-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="6e5f0-104">Product Name</span></span>|<span data-ttu-id="6e5f0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6e5f0-105">SQL Server</span></span>|  
|<span data-ttu-id="6e5f0-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="6e5f0-106">Event ID</span></span>|<span data-ttu-id="6e5f0-107">1505</span><span class="sxs-lookup"><span data-stu-id="6e5f0-107">1505</span></span>|  
|<span data-ttu-id="6e5f0-108">事件源</span><span class="sxs-lookup"><span data-stu-id="6e5f0-108">Event Source</span></span>|<span data-ttu-id="6e5f0-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6e5f0-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6e5f0-110">组件</span><span class="sxs-lookup"><span data-stu-id="6e5f0-110">Component</span></span>|<span data-ttu-id="6e5f0-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6e5f0-111">SQLEngine</span></span>|  
|<span data-ttu-id="6e5f0-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="6e5f0-112">Symbolic Name</span></span>|<span data-ttu-id="6e5f0-113">DUP_KEY</span><span class="sxs-lookup"><span data-stu-id="6e5f0-113">DUP_KEY</span></span>|  
|<span data-ttu-id="6e5f0-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="6e5f0-114">Message Text</span></span>|<span data-ttu-id="6e5f0-115">因为发现对象名称“%.\*ls”和索引名称“%.\*ls”有重复的键，所以 CREATE UNIQUE INDEX 已终止。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-115">CREATE UNIQUE INDEX terminated because a duplicate key was found for object name '%.\*ls' and index name '%.\*ls'.</span></span>  <span data-ttu-id="6e5f0-116">重复的键值为 %ls。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-116">The duplicate key value is %ls.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6e5f0-117">说明</span><span class="sxs-lookup"><span data-stu-id="6e5f0-117">Explanation</span></span>  
 <span data-ttu-id="6e5f0-118">如果表中有多行包含指定的重复值，那么，当您尝试创建唯一索引时，会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-118">This error occurs when you attempt to create a unique index and more than one row in the table contains the specified duplicate value.</span></span> <span data-ttu-id="6e5f0-119">当您创建索引并指定 UNIQUE 关键字时，或者当您创建 UNIQUE 约束时，会创建唯一索引。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-119">A unique index is created when you create an index and specify the UNIQUE keyword, or when you create a UNIQUE constraint.</span></span> <span data-ttu-id="6e5f0-120">对于表内的任何行，索引或约束中所定义的列中都不能有重复值。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-120">The table cannot contain any rows that have duplicate values in the columns defined in the index or constraint.</span></span>  
  
 <span data-ttu-id="6e5f0-121">请考虑以下 **Employee** 表中的数据：</span><span class="sxs-lookup"><span data-stu-id="6e5f0-121">Consider the data in the following **Employee** table:</span></span>  
  
|<span data-ttu-id="6e5f0-122">LastName</span><span class="sxs-lookup"><span data-stu-id="6e5f0-122">LastName</span></span>|<span data-ttu-id="6e5f0-123">FirstName</span><span class="sxs-lookup"><span data-stu-id="6e5f0-123">FirstName</span></span>|<span data-ttu-id="6e5f0-124">JobTitle</span><span class="sxs-lookup"><span data-stu-id="6e5f0-124">JobTitle</span></span>|<span data-ttu-id="6e5f0-125">HireDate</span><span class="sxs-lookup"><span data-stu-id="6e5f0-125">HireDate</span></span>|  
|--------------|---------------|--------------|--------------|  
|<span data-ttu-id="6e5f0-126">Walters</span><span class="sxs-lookup"><span data-stu-id="6e5f0-126">Walters</span></span>|<span data-ttu-id="6e5f0-127">Rob</span><span class="sxs-lookup"><span data-stu-id="6e5f0-127">Rob</span></span>|<span data-ttu-id="6e5f0-128">Senior Tool Designer</span><span class="sxs-lookup"><span data-stu-id="6e5f0-128">Senior Tool Designer</span></span>|<span data-ttu-id="6e5f0-129">2004-11-19</span><span class="sxs-lookup"><span data-stu-id="6e5f0-129">2004-11-19</span></span>|  
|<span data-ttu-id="6e5f0-130">Brown</span><span class="sxs-lookup"><span data-stu-id="6e5f0-130">Brown</span></span>|<span data-ttu-id="6e5f0-131">Kevin</span><span class="sxs-lookup"><span data-stu-id="6e5f0-131">Kevin</span></span>|<span data-ttu-id="6e5f0-132">Marketing Assistant</span><span class="sxs-lookup"><span data-stu-id="6e5f0-132">Marketing Assistant</span></span>|<span data-ttu-id="6e5f0-133">Null</span><span class="sxs-lookup"><span data-stu-id="6e5f0-133">NULL</span></span>|  
|<span data-ttu-id="6e5f0-134">Brown</span><span class="sxs-lookup"><span data-stu-id="6e5f0-134">Brown</span></span>|<span data-ttu-id="6e5f0-135">Jo</span><span class="sxs-lookup"><span data-stu-id="6e5f0-135">Jo</span></span>|<span data-ttu-id="6e5f0-136">Design Engineer</span><span class="sxs-lookup"><span data-stu-id="6e5f0-136">Design Engineer</span></span>|<span data-ttu-id="6e5f0-137">Null</span><span class="sxs-lookup"><span data-stu-id="6e5f0-137">NULL</span></span>|  
|<span data-ttu-id="6e5f0-138">Walters</span><span class="sxs-lookup"><span data-stu-id="6e5f0-138">Walters</span></span>|<span data-ttu-id="6e5f0-139">Rob</span><span class="sxs-lookup"><span data-stu-id="6e5f0-139">Rob</span></span>|<span data-ttu-id="6e5f0-140">Tool Designer</span><span class="sxs-lookup"><span data-stu-id="6e5f0-140">Tool Designer</span></span>|<span data-ttu-id="6e5f0-141">2001-08-09</span><span class="sxs-lookup"><span data-stu-id="6e5f0-141">2001-08-09</span></span>|  
  
 <span data-ttu-id="6e5f0-142">由于行中存在重复值，因此不能针对 **LastName** 列或 **LastName** 列与 **FirstName** 列的组合创建唯一索引。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-142">A unique index can not be created on the column combinations **LastName** or **LastName**, **FirstName** because of duplicate values in the rows.</span></span>  
  
 <span data-ttu-id="6e5f0-143">**HireDate** 列中可能存在不太明显的唯一性冲突。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-143">Less obvious is the potential for a uniqueness violation in the **HireDate** column.</span></span> <span data-ttu-id="6e5f0-144">为了利于创建索引，NULL 值与 NULL 值的比较结果为相等。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-144">For indexing purposes, NULL values compare as equal.</span></span> <span data-ttu-id="6e5f0-145">因此，如果不止一行中的键值为 NULL，则不能创建唯一索引或唯一约束。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-145">Therefore, you cannot create a unique index or constraint if the key values are NULL in more than one row.</span></span> <span data-ttu-id="6e5f0-146">有了上面的数据，不能针对 **HireDate** 列或 **LastName** 列与 **HireDate** 列的组合创建唯一索引。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-146">Given the data above, a unique index cannot be created on the column combinations **HireDate** or **LastName**, **HireDate**.</span></span>  
  
 <span data-ttu-id="6e5f0-147">错误消息 1505 返回第一个违反唯一性约束的行。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-147">Error message 1505 returns the first row that violates the uniqueness constraint.</span></span> <span data-ttu-id="6e5f0-148">该表中可能存在其他重复行。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-148">There may be other duplicate rows in the table.</span></span> <span data-ttu-id="6e5f0-149">若要查找所有的重复行，请查询指定的表，然后使用 GROUP BY 和 HAVING 子句报告重复行。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-149">To find all duplicate rows, query the specified table and use the GROUP BY and HAVING clauses to report the duplicate rows.</span></span> <span data-ttu-id="6e5f0-150">例如，下面的查询返回 **Employee** 表中具有重复名字和姓氏的行：</span><span class="sxs-lookup"><span data-stu-id="6e5f0-150">For example, the following query returns the rows in the **Employee** table that have duplicate first and last names.</span></span>  
  
 <span data-ttu-id="6e5f0-151">从 dbo 中选择 "LastName"、"名字"、"计数" (\*) 。员工组按 LastName，名字 \*)  (> 1;</span><span class="sxs-lookup"><span data-stu-id="6e5f0-151">SELECT LastName, FirstName, count(\*) FROM dbo.Employee GROUP BY LastName, FirstName HAVING count(\*) > 1;</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6e5f0-152">用户操作</span><span class="sxs-lookup"><span data-stu-id="6e5f0-152">User Action</span></span>  
 <span data-ttu-id="6e5f0-153">请考虑以下解决方案。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-153">Consider the following solutions.</span></span>  
  
-   <span data-ttu-id="6e5f0-154">在索引或约束定义中添加或删除列以创建唯一组合。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-154">Add or remove columns in the index or constraint definition to create a unique composite.</span></span> <span data-ttu-id="6e5f0-155">在前面的例子中，向索引或约束定义中添加 **MiddleName** 列可以解决重复问题。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-155">In the previous example, adding a **MiddleName** column to the index or constraint definition might resolve the duplication problem.</span></span>  
  
-   <span data-ttu-id="6e5f0-156">当为唯一索引或唯一约束选择列时，请选择那些定义为 NOT NULL 的列。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-156">Select columns that are defined as NOT NULL when you choose columns for a unique index or constraint.</span></span> <span data-ttu-id="6e5f0-157">这样，当多行的键值包含 NULL 时，就消除了导致唯一性冲突的可能性。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-157">This eliminates the possibility of a uniqueness violation caused when more than one row contains NULL in the key values.</span></span>  
  
-   <span data-ttu-id="6e5f0-158">如果重复值是因数据输入错误而引起的，则可以先手动更正数据，然后创建索引或约束。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-158">If the duplicate values are the result of data entry errors, manually correct the data and then create the index or constraint.</span></span> <span data-ttu-id="6e5f0-159">有关删除表中重复行的信息，请参阅知识库文章 139444：[如何从 SQL Server 中的表中删除重复行](https://support.microsoft.com/kb/139444)。</span><span class="sxs-lookup"><span data-stu-id="6e5f0-159">For information about removing duplicate rows in a table, see Knowledge Base article 139444: [How to remove duplicate rows from a table in SQL Server](https://support.microsoft.com/kb/139444).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5f0-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6e5f0-160">See Also</span></span>  
 <span data-ttu-id="6e5f0-161">[CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6e5f0-161">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="6e5f0-162">[创建唯一索引](../indexes/indexes.md) </span><span class="sxs-lookup"><span data-stu-id="6e5f0-162">[Create Unique Indexes](../indexes/indexes.md) </span></span>  
 [<span data-ttu-id="6e5f0-163">创建唯一约束</span><span class="sxs-lookup"><span data-stu-id="6e5f0-163">Create Unique Constraints</span></span>](../tables/create-unique-constraints.md)  
  
  
