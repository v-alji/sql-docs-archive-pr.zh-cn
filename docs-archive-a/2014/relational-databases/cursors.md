---
title: 游标 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- results [SQL Server], cursors
- Transact-SQL cursors, about cursors
- cursors [SQL Server]
- data access [SQL Server], cursors
- result sets [SQL Server], cursors
- requesting cursors
- cursors [SQL Server], about cursors
ms.assetid: e668b40c-bd4d-4415-850d-20fc4872ee72
author: rothja
ms.author: jroth
ms.openlocfilehash: 055482a8cf64527f58ed983b449121a99960f566
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591382"
---
# <a name="cursors"></a><span data-ttu-id="1dd7e-102">游标</span><span class="sxs-lookup"><span data-stu-id="1dd7e-102">Cursors</span></span>
  <span data-ttu-id="1dd7e-103">关系数据库中的操作会对整个行集起作用。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-103">Operations in a relational database act on a complete set of rows.</span></span> <span data-ttu-id="1dd7e-104">例如，由 SELECT 语句返回的行集包括满足该语句的 WHERE 子句中条件的所有行。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-104">For example, the set of rows returned by a SELECT statement consists of all the rows that satisfy the conditions in the WHERE clause of the statement.</span></span> <span data-ttu-id="1dd7e-105">这种由语句返回的完整行集称为结果集。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-105">This complete set of rows returned by the statement is known as the result set.</span></span> <span data-ttu-id="1dd7e-106">应用程序，特别是交互式联机应用程序，并不总能将整个结果集作为一个单元来有效地处理。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-106">Applications, especially interactive online applications, cannot always work effectively with the entire result set as a unit.</span></span> <span data-ttu-id="1dd7e-107">这些应用程序需要一种机制以便每次处理一行或一部分行。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-107">These applications need a mechanism to work with one row or a small block of rows at a time.</span></span> <span data-ttu-id="1dd7e-108">游标就是提供这种机制的对结果集的一种扩展。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-108">Cursors are an extension to result sets that provide that mechanism.</span></span>  
  
 <span data-ttu-id="1dd7e-109">游标通过以下方式来扩展结果处理：</span><span class="sxs-lookup"><span data-stu-id="1dd7e-109">Cursors extend result processing by:</span></span>  
  
-   <span data-ttu-id="1dd7e-110">允许定位在结果集的特定行。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-110">Allowing positioning at specific rows of the result set.</span></span>  
  
-   <span data-ttu-id="1dd7e-111">从结果集的当前位置检索一行或一部分行。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-111">Retrieving one row or block of rows from the current position in the result set.</span></span>  
  
-   <span data-ttu-id="1dd7e-112">支持对结果集中当前位置的行进行数据修改。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-112">Supporting data modifications to the rows at the current position in the result set.</span></span>  
  
-   <span data-ttu-id="1dd7e-113">为由其他用户对显示在结果集中的数据库数据所做的更改提供不同级别的可见性支持。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-113">Supporting different levels of visibility to changes made by other users to the database data that is presented in the result set.</span></span>  
  
-   <span data-ttu-id="1dd7e-114">提供脚本、存储过程和触发器中用于访问结果集中的数据的 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-114">Providing [!INCLUDE[tsql](../includes/tsql-md.md)] statements in scripts, stored procedures, and triggers access to the data in a result set.</span></span>  
  
## <a name="concepts"></a><span data-ttu-id="1dd7e-115">概念</span><span class="sxs-lookup"><span data-stu-id="1dd7e-115">Concepts</span></span>  
 <span data-ttu-id="1dd7e-116">游标实现</span><span class="sxs-lookup"><span data-stu-id="1dd7e-116">Cursor Implementations</span></span>  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="1dd7e-117">支持三种游标实现。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-117">supports three cursor implementations.</span></span>  
  
 <span data-ttu-id="1dd7e-118">Transact-SQL 游标</span><span class="sxs-lookup"><span data-stu-id="1dd7e-118">Transact-SQL cursors</span></span>  
 <span data-ttu-id="1dd7e-119">基于 DECLARE CURSOR 语法，主要用于 [!INCLUDE[tsql](../includes/tsql-md.md)] 脚本、存储过程和触发器中。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-119">Are based on the DECLARE CURSOR syntax and are used mainly in [!INCLUDE[tsql](../includes/tsql-md.md)] scripts, stored procedures, and triggers.</span></span> [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="1dd7e-120">游标在服务器上实现，由从客户端发送到服务器的 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句管理。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-120">cursors are implemented on the server and are managed by [!INCLUDE[tsql](../includes/tsql-md.md)] statements sent from the client to the server.</span></span> <span data-ttu-id="1dd7e-121">它们还可能包含在批处理、存储过程或触发器中。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-121">They may also be contained in batches, stored procedures, or triggers.</span></span>  
  
 <span data-ttu-id="1dd7e-122">应用程序编程接口 (API) 服务器游标</span><span class="sxs-lookup"><span data-stu-id="1dd7e-122">Application programming interface (API) server cursors</span></span>  
 <span data-ttu-id="1dd7e-123">支持 OLE DB 和 ODBC 中的 API 游标函数。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-123">Support the API cursor functions in OLE DB and ODBC.</span></span> <span data-ttu-id="1dd7e-124">API 服务器游标在服务器上实现。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-124">API server cursors are implemented on the server.</span></span> <span data-ttu-id="1dd7e-125">每次客户端应用程序调用 API 游标函数时， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口或 ODBC 驱动程序会把请求传输到服务器，以便对 API 服务器游标进行操作。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-125">Each time a client application calls an API cursor function, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client OLE DB provider or ODBC driver transmits the request to the server for action against the API server cursor.</span></span>  
  
 <span data-ttu-id="1dd7e-126">客户端游标</span><span class="sxs-lookup"><span data-stu-id="1dd7e-126">Client cursors</span></span>  
 <span data-ttu-id="1dd7e-127">由 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序和实现 ADO API 的 DLL 在内部实现。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-127">Are implemented internally by the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client ODBC driver and by the DLL that implements the ADO API.</span></span> <span data-ttu-id="1dd7e-128">客户端游标通过在客户端高速缓存所有结果集行来实现。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-128">Client cursors are implemented by caching all the result set rows on the client.</span></span> <span data-ttu-id="1dd7e-129">每次客户端应用程序调用 API 游标函数时， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序或 ADO DLL 会对客户端上高速缓存的结果集行执行游标操作。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-129">Each time a client application calls an API cursor function, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client ODBC driver or the ADO DLL performs the cursor operation on the result set rows cached on the client.</span></span>  
  
 <span data-ttu-id="1dd7e-130">游标类型</span><span class="sxs-lookup"><span data-stu-id="1dd7e-130">Type of Cursors</span></span>  
 <span data-ttu-id="1dd7e-131">只进</span><span class="sxs-lookup"><span data-stu-id="1dd7e-131">Forward-only</span></span>  
 <span data-ttu-id="1dd7e-132">只进游标不支持滚动，它只支持游标从头到尾顺序提取。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-132">A forward-only cursor does not support scrolling; it supports only fetching the rows serially from the start to the end of the cursor.</span></span> <span data-ttu-id="1dd7e-133">行只在从数据库中提取出来后才能检索。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-133">The rows are not retrieved from the database until they are fetched.</span></span> <span data-ttu-id="1dd7e-134">对所有由当前用户发出或由其他用户提交、并影响结果集中的行的 INSERT、UPDATE 和 DELETE 语句，其效果在这些行从游标中提取时是可见的。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-134">The effects of all INSERT, UPDATE, and DELETE statements made by the current user or committed by other users that affect rows in the result set are visible as the rows are fetched from the cursor.</span></span>  
  
 <span data-ttu-id="1dd7e-135">由于游标无法向后滚动，则在提取行后对数据库中的行进行的大多数更改通过游标均不可见。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-135">Because the cursor cannot be scrolled backward, most changes made to rows in the database after the row was fetched are not visible through the cursor.</span></span> <span data-ttu-id="1dd7e-136">当值用于确定所修改的结果集（例如更新聚集索引涵盖的列）中行的位置时，修改后的值通过游标可见。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-136">In cases where a value used to determine the location of the row within the result set is modified, such as updating a column covered by a clustered index, the modified value is visible through the cursor.</span></span>  
  
 <span data-ttu-id="1dd7e-137">尽管数据库 API 游标模型将只进游标视为一种游标类型，但是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 不这样。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-137">Although the database API cursor models consider a forward-only cursor to be a distinct type of cursor, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="1dd7e-138">将只进和滚动视为可应用于静态游标、键集驱动游标和动态游标的选项。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-138">considers both forward-only and scroll as options that can be applied to static, keyset-driven, and dynamic cursors.</span></span> [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="1dd7e-139">游标支持只进静态游标、键集驱动游标和动态游标。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-139">cursors support forward-only static, keyset-driven, and dynamic cursors.</span></span> <span data-ttu-id="1dd7e-140">数据库 API 游标模型则假定静态游标、键集驱动游标和动态游标都是可滚动的。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-140">The database API cursor models assume that static, keyset-driven, and dynamic cursors are always scrollable.</span></span> <span data-ttu-id="1dd7e-141">当数据库 API 游标属性设置为只进时， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将此游标作为只进动态游标实现。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-141">When a database API cursor attribute or property is set to forward-only, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] implements this as a forward-only dynamic cursor.</span></span>  
  
 <span data-ttu-id="1dd7e-142">静态</span><span class="sxs-lookup"><span data-stu-id="1dd7e-142">Static</span></span>  
 <span data-ttu-id="1dd7e-143">静态游标的完整结果集是打开游标时在 **tempdb** 中生成的。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-143">The complete result set of a static cursor is built in **tempdb** when the cursor is opened.</span></span> <span data-ttu-id="1dd7e-144">静态游标总是按照打开游标时的原样显示结果集。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-144">A static cursor always displays the result set as it was when the cursor was opened.</span></span> <span data-ttu-id="1dd7e-145">静态游标在滚动期间很少或根本检测不到变化，但消耗的资源相对很少。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-145">Static cursors detect few or no changes, but consume relatively few resources while scrolling.</span></span>  
  
 <span data-ttu-id="1dd7e-146">游标不反映在数据库中所做的任何影响结果集成员身份的更改，也不反映对组成结果集的行的列值所做的更改。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-146">The cursor does not reflect any changes made in the database that affect either the membership of the result set or changes to the values in the columns of the rows that make up the result set.</span></span> <span data-ttu-id="1dd7e-147">静态游标不会显示打开游标以后在数据库中新插入的行，即使这些行符合游标 SELECT 语句的搜索条件。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-147">A static cursor does not display new rows inserted in the database after the cursor was opened, even if they match the search conditions of the cursor SELECT statement.</span></span> <span data-ttu-id="1dd7e-148">如果组成结果集的行被其他用户更新，则新的数据值不会显示在静态游标中。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-148">If rows making up the result set are updated by other users, the new data values are not displayed in the static cursor.</span></span> <span data-ttu-id="1dd7e-149">静态游标会显示打开游标以后从数据库中删除的行。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-149">The static cursor displays rows deleted from the database after the cursor was opened.</span></span> <span data-ttu-id="1dd7e-150">静态游标中不反映 UPDATE、INSERT 或者 DELETE 操作（除非关闭游标然后重新打开），甚至不反映使用打开游标的同一连接所做的修改。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-150">No UPDATE, INSERT, or DELETE operations are reflected in a static cursor (unless the cursor is closed and reopened), not even modifications made using the same connection that opened the cursor.</span></span>  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="1dd7e-151">静态游标始终是只读的。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-151">static cursors are always read-only.</span></span>  
  
 <span data-ttu-id="1dd7e-152">由于静态游标的结果集存储在 **tempdb**的工作表中，因此结果集中的行大小不能超过 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 表的最大行大小。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-152">Because the result set of a static cursor is stored in a work table in **tempdb**, the size of the rows in the result set cannot exceed the maximum row size for a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="1dd7e-153">称静态游标为不敏感游标。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-153">uses the term insensitive for static cursors.</span></span> <span data-ttu-id="1dd7e-154">一些数据库 API 将这类游标识别为快照游标。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-154">Some database APIs identify them as snapshot cursors.</span></span>  
  
 <span data-ttu-id="1dd7e-155">Keyset</span><span class="sxs-lookup"><span data-stu-id="1dd7e-155">Keyset</span></span>  
 <span data-ttu-id="1dd7e-156">打开由键集驱动的游标时，该游标中各行的成员身份和顺序是固定的。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-156">The membership and order of rows in a keyset-driven cursor are fixed when the cursor is opened.</span></span> <span data-ttu-id="1dd7e-157">由键集驱动的游标由一组唯一标识符（键）控制，这组键称为键集。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-157">Keyset-driven cursors are controlled by a set of unique identifiers, keys, known as the keyset.</span></span> <span data-ttu-id="1dd7e-158">键是根据以唯一方式标识结果集中各行的一组列生成的。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-158">The keys are built from a set of columns that uniquely identify the rows in the result set.</span></span> <span data-ttu-id="1dd7e-159">键集是打开游标时来自符合 SELECT 语句要求的所有行中的一组键值。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-159">The keyset is the set of the key values from all the rows that qualified for the SELECT statement at the time the cursor was opened.</span></span> <span data-ttu-id="1dd7e-160">由键集驱动的游标对应的键集是打开该游标时在 **tempdb** 中生成的。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-160">The keyset for a keyset-driven cursor is built in **tempdb** when the cursor is opened.</span></span>  
  
 <span data-ttu-id="1dd7e-161">动态</span><span class="sxs-lookup"><span data-stu-id="1dd7e-161">Dynamic</span></span>  
 <span data-ttu-id="1dd7e-162">动态游标与静态游标相对。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-162">Dynamic cursors are the opposite of static cursors.</span></span> <span data-ttu-id="1dd7e-163">当滚动游标时，动态游标反映结果集中所做的所有更改。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-163">Dynamic cursors reflect all changes made to the rows in their result set when scrolling through the cursor.</span></span> <span data-ttu-id="1dd7e-164">结果集中的行数据值、顺序和成员在每次提取时都会改变。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-164">The data values, order, and membership of the rows in the result set can change on each fetch.</span></span> <span data-ttu-id="1dd7e-165">所有用户做的全部 UPDATE、INSERT 和 DELETE 语句均通过游标可见。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-165">All UPDATE, INSERT, and DELETE statements made by all users are visible through the cursor.</span></span> <span data-ttu-id="1dd7e-166">如果使用 API 函数（如 **SQLSetPos** ）或 [!INCLUDE[tsql](../includes/tsql-md.md)] WHERE CURRENT OF 子句通过游标进行更新，它们将立即可见。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-166">Updates are visible immediately if they are made through the cursor using either an API function such as **SQLSetPos** or the [!INCLUDE[tsql](../includes/tsql-md.md)] WHERE CURRENT OF clause.</span></span> <span data-ttu-id="1dd7e-167">在游标外部所做的更新直到提交时才可见，除非将游标的事务隔离级别设为未提交读。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-167">Updates made outside the cursor are not visible until they are committed, unless the cursor transaction isolation level is set to read uncommitted.</span></span> <span data-ttu-id="1dd7e-168">动态游标计划从不使用空间索引。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-168">Dynamic cursor plans never use spatial indexes.</span></span>  
  
## <a name="requesting-a-cursor"></a><span data-ttu-id="1dd7e-169">请求游标</span><span class="sxs-lookup"><span data-stu-id="1dd7e-169">Requesting a Cursor</span></span>  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="1dd7e-170">支持两种请求游标的方法：</span><span class="sxs-lookup"><span data-stu-id="1dd7e-170">supports two methods for requesting a cursor:</span></span>  
  
-   [!INCLUDE[tsql](../includes/tsql-md.md)]  
  
     <span data-ttu-id="1dd7e-171">[!INCLUDE[tsql](../includes/tsql-md.md)] 语言支持在 ISO 游标语法之后制定的用于使用游标的语法。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-171">The [!INCLUDE[tsql](../includes/tsql-md.md)] language supports a syntax for using cursors modeled after the ISO cursor syntax.</span></span>  
  
-   <span data-ttu-id="1dd7e-172">数据库应用程序编程接口（API）游标函数</span><span class="sxs-lookup"><span data-stu-id="1dd7e-172">Database application programming interface (API) cursor functions</span></span>  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="1dd7e-173">支持以下数据库 API 的游标功能：</span><span class="sxs-lookup"><span data-stu-id="1dd7e-173">supports the cursor functionality of these database APIs:</span></span>  
  
    -   <span data-ttu-id="1dd7e-174">ADO（[!INCLUDE[msCoName](../includes/msconame-md.md)] ActiveX 数据对象）</span><span class="sxs-lookup"><span data-stu-id="1dd7e-174">ADO ([!INCLUDE[msCoName](../includes/msconame-md.md)] ActiveX Data Object)</span></span>  
  
    -   <span data-ttu-id="1dd7e-175">OLE DB</span><span class="sxs-lookup"><span data-stu-id="1dd7e-175">OLE DB</span></span>  
  
    -   <span data-ttu-id="1dd7e-176">ODBC（开放式数据库连接）</span><span class="sxs-lookup"><span data-stu-id="1dd7e-176">ODBC (Open Database Connectivity)</span></span>  
  
 <span data-ttu-id="1dd7e-177">应用程序不能混合使用这两种请求游标的方法。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-177">An application should never mix these two methods of requesting a cursor.</span></span> <span data-ttu-id="1dd7e-178">已经使用 API 指定游标行为的应用程序不能再执行 [!INCLUDE[tsql](../includes/tsql-md.md)] DECLARE CURSOR 语句请求一个 [!INCLUDE[tsql](../includes/tsql-md.md)] 游标。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-178">An application that has used the API to specify cursor behaviors should not then execute a [!INCLUDE[tsql](../includes/tsql-md.md)] DECLARE CURSOR statement to also request a [!INCLUDE[tsql](../includes/tsql-md.md)] cursor.</span></span> <span data-ttu-id="1dd7e-179">应用程序只有在将所有的 API 游标特性设置回默认值后，才可以执行 DECLARE CURSOR。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-179">An application should only execute DECLARE CURSOR if it has set all the API cursor attributes back to their defaults.</span></span>  
  
 <span data-ttu-id="1dd7e-180">如果既未请求 [!INCLUDE[tsql](../includes/tsql-md.md)] 游标也未请求 API 游标，则默认情况下 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将向应用程序返回一个完整的结果集，这个结果集称为默认结果集。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-180">If neither a [!INCLUDE[tsql](../includes/tsql-md.md)] nor API cursor has been requested, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] defaults to returning a complete result set, known as a default result set, to the application.</span></span>  
  
## <a name="cursor-process"></a><span data-ttu-id="1dd7e-181">游标进程</span><span class="sxs-lookup"><span data-stu-id="1dd7e-181">Cursor Process</span></span>  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="1dd7e-182">游标和 API 游标有不同的语法，但下列一般进程适用于所有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 游标：</span><span class="sxs-lookup"><span data-stu-id="1dd7e-182">cursors and API cursors have different syntax, but the following general process is used with all [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cursors:</span></span>  
  
1.  <span data-ttu-id="1dd7e-183">将游标与 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句的结果集相关联，并且定义该游标的特性，例如是否能够更新游标中的行。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-183">Associate a cursor with the result set of a [!INCLUDE[tsql](../includes/tsql-md.md)] statement, and define characteristics of the cursor, such as whether the rows in the cursor can be updated.</span></span>  
  
2.  <span data-ttu-id="1dd7e-184">执行 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句以填充游标。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-184">Execute the [!INCLUDE[tsql](../includes/tsql-md.md)] statement to populate the cursor.</span></span>  
  
3.  <span data-ttu-id="1dd7e-185">从游标中检索您想要查看的行。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-185">Retrieve the rows in the cursor you want to see.</span></span> <span data-ttu-id="1dd7e-186">从游标中检索一行或一部分行的操作称为提取。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-186">The operation to retrieve one row or one block of rows from a cursor is called a fetch.</span></span> <span data-ttu-id="1dd7e-187">执行一系列提取操作以便向前或向后检索行的操作称为滚动。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-187">Performing a series of fetches to retrieve rows in either a forward or backward direction is called scrolling.</span></span>  
  
4.  <span data-ttu-id="1dd7e-188">根据需要，对游标中当前位置的行执行修改操作（更新或删除）。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-188">Optionally, perform modification operations (update or delete) on the row at the current position in the cursor.</span></span>  
  
5.  <span data-ttu-id="1dd7e-189">关闭游标。</span><span class="sxs-lookup"><span data-stu-id="1dd7e-189">Close the cursor.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="1dd7e-190">相关内容</span><span class="sxs-lookup"><span data-stu-id="1dd7e-190">Related Content</span></span>  
 <span data-ttu-id="1dd7e-191">[游标行为](native-client-odbc-cursors/cursor-behaviors.md) [如何实现游标](native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)</span><span class="sxs-lookup"><span data-stu-id="1dd7e-191">[Cursor Behaviors](native-client-odbc-cursors/cursor-behaviors.md) [How Cursors Are Implemented](native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd7e-192">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1dd7e-192">See Also</span></span>  
 <span data-ttu-id="1dd7e-193">[&#40;Transact-sql 声明游标&#41;](/sql/t-sql/language-elements/declare-cursor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1dd7e-193">[DECLARE CURSOR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-cursor-transact-sql) </span></span>  
 <span data-ttu-id="1dd7e-194">[游标 (Transact-SQL)](/sql/t-sql/language-elements/cursors-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1dd7e-194">[Cursors &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/cursors-transact-sql) </span></span>  
 <span data-ttu-id="1dd7e-195">[Cursor 函数 &#40;Transact-sql&#41;](/sql/t-sql/functions/cursor-functions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1dd7e-195">[Cursor Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/cursor-functions-transact-sql) </span></span>  
 [<span data-ttu-id="1dd7e-196">游标存储过程 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1dd7e-196">Cursor Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/cursor-stored-procedures-transact-sql)  
  
  
