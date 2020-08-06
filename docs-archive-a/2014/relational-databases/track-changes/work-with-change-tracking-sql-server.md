---
title: 使用更改跟踪 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server], making changes
- change tracking [SQL Server], troubleshooting
- updating data [SQL Server]
- troubleshooting [SQL Server], change tracking
- data changes [SQL Server]
- tracking data changes [SQL Server]
- data [SQL Server], changing
- change tracking [SQL Server], data restore
- change tracking [SQL Server], ensuring consistent results
- change tracking [SQL Server], handling changes
ms.assetid: 5aec22ce-ae6f-4048-8a45-59ed05f04dc5
author: rothja
ms.author: jroth
ms.openlocfilehash: bdb8205a789894caf8c8e2d3c3f491751757bab6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590653"
---
# <a name="work-with-change-tracking-sql-server"></a><span data-ttu-id="fbe38-102">使用更改跟踪 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fbe38-102">Work with Change Tracking (SQL Server)</span></span>
  <span data-ttu-id="fbe38-103">使用更改跟踪的应用程序必须能够获取跟踪的更改，将这些更改应用到其他数据存储区并更新源数据库。</span><span class="sxs-lookup"><span data-stu-id="fbe38-103">Applications that use change tracking must be able to obtain tracked changes, apply these changes to another data store, and update the source database.</span></span> <span data-ttu-id="fbe38-104">本主题介绍了如何执行这些任务，以及在发生故障转移且必须从备份还原数据库时，角色更改跟踪如何进行。</span><span class="sxs-lookup"><span data-stu-id="fbe38-104">This topic describes how to perform these tasks, and also the role change tracking plays when a failover occurs and a database must be restored from a backup.</span></span>  
  
##  <a name="obtain-changes-by-using-change-tracking-functions"></a><a name="Obtain"></a> <span data-ttu-id="fbe38-105">通过使用更改跟踪函数获取更改</span><span class="sxs-lookup"><span data-stu-id="fbe38-105">Obtain Changes by Using Change Tracking Functions</span></span>  
 <span data-ttu-id="fbe38-106">介绍如何使用更改跟踪功能来获取更改以及有关对数据库所做的更改的信息。</span><span class="sxs-lookup"><span data-stu-id="fbe38-106">Describes how to use the change tracking functions to obtain changes and information about the changes that were made to a database.</span></span>  
  
### <a name="about-the-change-tracking-functions"></a><span data-ttu-id="fbe38-107">关于更改跟踪函数</span><span class="sxs-lookup"><span data-stu-id="fbe38-107">About the Change Tracking Functions</span></span>  
 <span data-ttu-id="fbe38-108">应用程序可以使用以下函数来获取在数据库中所做的更改以及有关这些更改的信息：</span><span class="sxs-lookup"><span data-stu-id="fbe38-108">Applications can use the following functions to obtain the changes that are made in a database and information about the changes:</span></span>  
  
 <span data-ttu-id="fbe38-109">CHANGETABLE(CHANGES …) 函数</span><span class="sxs-lookup"><span data-stu-id="fbe38-109">CHANGETABLE(CHANGES ...) function</span></span>  
 <span data-ttu-id="fbe38-110">此行集函数用于查询更改信息。</span><span class="sxs-lookup"><span data-stu-id="fbe38-110">This rowset function is used to query for change information.</span></span> <span data-ttu-id="fbe38-111">该函数查询内部更改跟踪表中存储的数据。</span><span class="sxs-lookup"><span data-stu-id="fbe38-111">The function queries the data stored in the internal change tracking tables.</span></span> <span data-ttu-id="fbe38-112">该函数返回的结果集中包含已更改的行的主键和其他更改信息，例如，操作、更新的列以及行版本。</span><span class="sxs-lookup"><span data-stu-id="fbe38-112">The function returns a results set that contains the primary keys of rows that have changed together with other change information such as the operation, columns updated and version for the row.</span></span>  
  
 <span data-ttu-id="fbe38-113">CHANGETABLE(CHANGES …) 将上次同步版本作为参数。</span><span class="sxs-lookup"><span data-stu-id="fbe38-113">CHANGETABLE(CHANGES ...) takes a last synchronization version as an argument.</span></span> <span data-ttu-id="fbe38-114">上次同步版本使用 `@last_synchronization_version` 变量获得。</span><span class="sxs-lookup"><span data-stu-id="fbe38-114">The last sychronization version is obtained using the `@last_synchronization_version` variable.</span></span> <span data-ttu-id="fbe38-115">上次同步版本的语义如下所示：</span><span class="sxs-lookup"><span data-stu-id="fbe38-115">The semantics of the last synchronization version are as follows:</span></span>  
  
-   <span data-ttu-id="fbe38-116">进行调用的客户端已获取更改，并知道直至上次同步版本（含该版本）所做的所有更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-116">The calling client has obtained changes and knows about all changes up to and including the last synchronization version.</span></span>  
  
-   <span data-ttu-id="fbe38-117">因此，CHANGETABLE(CHANGES …) 返回在上次同步版本之后进行的所有更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-117">CHANGETABLE(CHANGES ...) will therefore return all changes that have occurred after the last synchronization version.</span></span>  
  
     <span data-ttu-id="fbe38-118">下图说明了如何使用 CHANGETABLE(CHANGES …) 获取更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-118">The following illustration shows how CHANGETABLE(CHANGES ...) is used to obtain changes.</span></span>  
  
     <span data-ttu-id="fbe38-119">![变更跟踪查询输出的示例](../../database-engine/media/queryoutput.gif "更改跟踪查询输出的示例")</span><span class="sxs-lookup"><span data-stu-id="fbe38-119">![Example of change tracking query output](../../database-engine/media/queryoutput.gif "Example of change tracking query output")</span></span>  
  
 <span data-ttu-id="fbe38-120">CHANGE_TRACKING_CURRENT_VERSION() 函数</span><span class="sxs-lookup"><span data-stu-id="fbe38-120">CHANGE_TRACKING_CURRENT_VERSION() function</span></span>  
 <span data-ttu-id="fbe38-121">用于获取当前版本，以供下次查询更改时使用。</span><span class="sxs-lookup"><span data-stu-id="fbe38-121">Is used to obtain the current version that will be used the next time when querying changes.</span></span> <span data-ttu-id="fbe38-122">该版本表示上次提交的事务的版本。</span><span class="sxs-lookup"><span data-stu-id="fbe38-122">This version represents the version of the last committed transaction.</span></span>  
  
 <span data-ttu-id="fbe38-123">CHANGE_TRACKING_MIN_VALID_VERSION() 函数</span><span class="sxs-lookup"><span data-stu-id="fbe38-123">CHANGE_TRACKING_MIN_VALID_VERSION()function</span></span>  
 <span data-ttu-id="fbe38-124">用于获取客户端能够具有的并且仍能从 CHANGETABLE() 获取有效结果的最低有效版本。</span><span class="sxs-lookup"><span data-stu-id="fbe38-124">Is used to obtain the minimum valid version that a client can have and still obtain valid results from CHANGETABLE().</span></span> <span data-ttu-id="fbe38-125">客户端应将上次同步版本与此函数返回的值进行对照检查。</span><span class="sxs-lookup"><span data-stu-id="fbe38-125">The client should check the last synchronization version against the value thatis returned by this function.</span></span> <span data-ttu-id="fbe38-126">如果上次同步版本低于此函数返回的版本，客户端将无法从 CHANGETABLE() 获取有效结果，而必须重新进行初始化。</span><span class="sxs-lookup"><span data-stu-id="fbe38-126">If the last synchronization version is less than the version returned by this function, the client will be unable to obtain valid results from CHANGETABLE() and will have to reinitialize.</span></span>  
  
### <a name="obtaining-initial-data"></a><span data-ttu-id="fbe38-127">获取初始数据</span><span class="sxs-lookup"><span data-stu-id="fbe38-127">Obtaining Initial Data</span></span>  
 <span data-ttu-id="fbe38-128">在应用程序第一次获取更改之前，应用程序必须发送查询以获取初始数据和同步版本。</span><span class="sxs-lookup"><span data-stu-id="fbe38-128">Before an application can obtain changes for the first time, the application must send a query to obtain the initial data and the synchronization version.</span></span> <span data-ttu-id="fbe38-129">应用程序必须直接从表中获取相应的数据，然后使用 CHANGE_TRACKING_CURRENT_VERSION() 获取初始版本。</span><span class="sxs-lookup"><span data-stu-id="fbe38-129">The application must obtain the appropriate data directly from the table, and then use CHANGE_TRACKING_CURRENT_VERSION() to obtain the initial version.</span></span> <span data-ttu-id="fbe38-130">第一次获取更改时，会将此版本传递给 CHANGETABLE(CHANGES …)。</span><span class="sxs-lookup"><span data-stu-id="fbe38-130">This version will be passed to CHANGETABLE(CHANGES ...) the first time that changes are obtained.</span></span>  
  
 <span data-ttu-id="fbe38-131">下面的示例说明了如何获取初始同步版本和初始数据集。</span><span class="sxs-lookup"><span data-stu-id="fbe38-131">The following example shows how to obtain the initial synchronization version and the initial data set.</span></span>  
  
```sql  
    -- Obtain the current synchronization version. This will be used next time that changes are obtained.  
    SET @synchronization_version = CHANGE_TRACKING_CURRENT_VERSION();  
  
    -- Obtain initial data set.  
    SELECT  
        P.ProductID, P.Name, P.ListPrice  
    FROM  
        SalesLT.Product AS P  
```  
  
### <a name="using-the-change-tracking-functions-to-obtain-changes"></a><span data-ttu-id="fbe38-132">使用更改跟踪函数获取更改</span><span class="sxs-lookup"><span data-stu-id="fbe38-132">Using the Change Tracking Functions to Obtain Changes</span></span>  
 <span data-ttu-id="fbe38-133">若要获取表中更改的行以及有关这些更改的信息，请使用 CHANGETABLE(CHANGES…)。例如，下面的查询获取 `SalesLT.Product` 表的更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-133">To obtain the changed rows for a table and information about the changes, use CHANGETABLE(CHANGES...). For example, the following query obtains changes for the `SalesLT.Product` table.</span></span>  
  
```sql  
SELECT  
    CT.ProductID, CT.SYS_CHANGE_OPERATION,  
    CT.SYS_CHANGE_COLUMNS, CT.SYS_CHANGE_CONTEXT  
FROM  
    CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
  
```  
  
 <span data-ttu-id="fbe38-134">通常，客户端需要获取行的最新数据，而不仅仅是行的主键。</span><span class="sxs-lookup"><span data-stu-id="fbe38-134">Usually, a client will want to obtain the latest data for a row instead of only the primary keys for the row.</span></span> <span data-ttu-id="fbe38-135">因此，应用程序将来自 CHANGETABLE(CHANGES …) 的结果与用户表中的数据联接在一起。</span><span class="sxs-lookup"><span data-stu-id="fbe38-135">Therefore, an application would join the results from CHANGETABLE(CHANGES ...) with the data in the user table.</span></span> <span data-ttu-id="fbe38-136">例如，下面的查询与 `SalesLT.Product` 表联接在一起以获取 `Name` 和 `ListPrice` 列的值。</span><span class="sxs-lookup"><span data-stu-id="fbe38-136">For example, the following query joins with the `SalesLT.Product` table to obtain the values for the `Name` and `ListPrice` columns.</span></span> <span data-ttu-id="fbe38-137">请注意，本例中使用了 `OUTER JOIN`。</span><span class="sxs-lookup"><span data-stu-id="fbe38-137">Note the use of `OUTER JOIN`.</span></span> <span data-ttu-id="fbe38-138">若要确保返回有关从用户表中删除的那些行的更改信息，则必须使用此运算符。</span><span class="sxs-lookup"><span data-stu-id="fbe38-138">This is required to make sure that the change information is returned for those rows that have been deleted from the user table.</span></span>  
  
```sql  
SELECT  
    CT.ProductID, P.Name, P.ListPrice,  
    CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS,  
    CT.SYS_CHANGE_CONTEXT  
FROM  
    SalesLT.Product AS P  
RIGHT OUTER JOIN  
    CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
ON  
    P.ProductID = CT.ProductID  
```  
  
 <span data-ttu-id="fbe38-139">若要获取在下次更改枚举中使用的版本，请使用 CHANGE_TRACKING_CURRENT_VERSION()，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="fbe38-139">To obtain the version for use in the next change enumeration, use CHANGE_TRACKING_CURRENT_VERSION(), as shown in the following example.</span></span>  
  
```sql  
SET @synchronization_version = CHANGE_TRACKING_CURRENT_VERSION()  
```  
  
 <span data-ttu-id="fbe38-140">当应用程序获取更改时，它必须同时使用 CHANGETABLE(CHANGES…) 和 CHANGE_TRACKING_CURRENT_VERSION()，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="fbe38-140">When an application obtains changes, it must use both CHANGETABLE(CHANGES...) and CHANGE_TRACKING_CURRENT_VERSION(), as shown in the following example.</span></span>  
  
```sql  
-- Obtain the current synchronization version. This will be used the next time CHANGETABLE(CHANGES...) is called.  
SET @synchronization_version = CHANGE_TRACKING_CURRENT_VERSION();  
  
-- Obtain incremental changes by using the synchronization version obtained the last time the data was synchronized.  
SELECT  
    CT.ProductID, P.Name, P.ListPrice,  
    CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS,  
    CT.SYS_CHANGE_CONTEXT  
FROM  
    SalesLT.Product AS P  
RIGHT OUTER JOIN  
    CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
ON  
    P.ProductID = CT.ProductID  
```  
  
### <a name="version-numbers"></a><span data-ttu-id="fbe38-141">版本号</span><span class="sxs-lookup"><span data-stu-id="fbe38-141">Version Numbers</span></span>  
 <span data-ttu-id="fbe38-142">启用了更改跟踪的数据库具有一个版本计数器；在对启用了更改跟踪的表进行更改时，该计数器会随之递增。</span><span class="sxs-lookup"><span data-stu-id="fbe38-142">A database that has change tracking enabled has a version counter that increases as changes are made to change tracked tables.</span></span> <span data-ttu-id="fbe38-143">每个更改的行都有一个关联的版本号。</span><span class="sxs-lookup"><span data-stu-id="fbe38-143">Each changed row has a version number that is associated with it.</span></span> <span data-ttu-id="fbe38-144">将请求发送到应用程序以查询更改时，将调用一个函数以提供版本号。</span><span class="sxs-lookup"><span data-stu-id="fbe38-144">When a request is sent to an application to query for changes, a function is called that supplies a version number.</span></span> <span data-ttu-id="fbe38-145">该函数返回在该版本之后所做的所有更改的相关信息。</span><span class="sxs-lookup"><span data-stu-id="fbe38-145">The function returns information about all the changes that have been made since that version.</span></span> <span data-ttu-id="fbe38-146">从某种意义上讲，更改跟踪版本在概念上与 `rowversion` 数据类型类似。</span><span class="sxs-lookup"><span data-stu-id="fbe38-146">In some ways, change tracking version is similar in concept to the `rowversion` data type.</span></span>  
  
### <a name="validating-the-last-synchronized-version"></a><span data-ttu-id="fbe38-147">验证上次同步版本</span><span class="sxs-lookup"><span data-stu-id="fbe38-147">Validating the Last Synchronized Version</span></span>  
 <span data-ttu-id="fbe38-148">更改的相关信息将保留有限的一段时间。</span><span class="sxs-lookup"><span data-stu-id="fbe38-148">Information about changes is maintained for a limited time.</span></span> <span data-ttu-id="fbe38-149">时间长度是由 CHANGE_RETENTION 参数控制的，可以将该参数指定为 ALTER DATABASE 的一部分。</span><span class="sxs-lookup"><span data-stu-id="fbe38-149">The length of time is controlled by the CHANGE_RETENTION parameter that can be specified as part of the ALTER DATABASE.</span></span>  
  
 <span data-ttu-id="fbe38-150">请注意，为 CHANGE_RETENTION 指定的时间决定了所有应用程序必须每隔多长时间从数据库中请求一次更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-150">Be aware that the time specified for CHANGE_RETENTION determines how frequently all applications must request changes from the database.</span></span> <span data-ttu-id="fbe38-151">如果应用程序使用的 *last_synchronization_version* 值早于表的最低有效同步版本，该应用程序将无法执行有效的更改枚举。</span><span class="sxs-lookup"><span data-stu-id="fbe38-151">If an application has a value for *last_synchronization_version* that is older than the minimum valid synchronization version for a table, that application cannot perform valid change enumeration.</span></span> <span data-ttu-id="fbe38-152">这是因为，可能已清除了某些更改信息。</span><span class="sxs-lookup"><span data-stu-id="fbe38-152">This is because some change information might have been cleaned up.</span></span> <span data-ttu-id="fbe38-153">在应用程序使用 CHANGETABLE(CHANGES …) 获取更改之前，该应用程序必须验证计划传递给 CHANGETABLE(CHANGES …) 的 last_synchronization_version 值  。如果 *last_synchronization_version* 的值无效，则该应用程序必须重新初始化所有数据。</span><span class="sxs-lookup"><span data-stu-id="fbe38-153">Before an application obtains changes by using CHANGETABLE(CHANGES ...), the application must validate the value for *last_synchronization_version* that it plans to pass to CHANGETABLE(CHANGES ...). If the value of *last_synchronization_version* is not valid, that application must reinitialize all the data.</span></span>  
  
 <span data-ttu-id="fbe38-154">下面的示例说明了如何验证每个表的 `last_synchronization_version` 值的有效性。</span><span class="sxs-lookup"><span data-stu-id="fbe38-154">The following example shows how to verify the validity of the value of `last_synchronization_version` for each table.</span></span>  
  
```sql  
-- Check individual table.  
IF (@last_synchronization_version < CHANGE_TRACKING_MIN_VALID_VERSION(  
                                   OBJECT_ID('SalesLT.Product')))  
BEGIN  
  -- Handle invalid version and do not enumerate changes.  
  -- Client must be reinitialized.  
END  
```  
  
 <span data-ttu-id="fbe38-155">正如下面的示例所示，可以对照数据库中的所有表检查 `last_synchronization_version` 值的有效性。</span><span class="sxs-lookup"><span data-stu-id="fbe38-155">As the following example shows, the validity of the value of `last_synchronization_version` can be checked against all tables in the database.</span></span>  
  
```sql  
-- Check all tables with change tracking enabled  
IF EXISTS (  
  SELECT COUNT(*) FROM sys.change_tracking_tables  
  WHERE min_valid_version > @last_synchronization_version )  
BEGIN  
  -- Handle invalid version & do not enumerate changes  
  -- Client must be reinitialized  
END  
```  
  
### <a name="using-column-tracking"></a><span data-ttu-id="fbe38-156">使用列跟踪</span><span class="sxs-lookup"><span data-stu-id="fbe38-156">Using Column Tracking</span></span>  
 <span data-ttu-id="fbe38-157">通过使用列跟踪，应用程序可以仅获取已更改的列数据，而不是获取整个行。</span><span class="sxs-lookup"><span data-stu-id="fbe38-157">Column tracking enables applications to obtain the data for only the columns that have changed instead of the whole row.</span></span> <span data-ttu-id="fbe38-158">例如，请考虑以下情况：某个表包含一个或多个较大但很少更改的列，并且还包含其他经常更改的列。</span><span class="sxs-lookup"><span data-stu-id="fbe38-158">For example, consider the scenario in which a table has one or more columns that are large, but rarely change; and also has other columns that frequently change.</span></span> <span data-ttu-id="fbe38-159">如果未使用列跟踪，应用程序只能确定某一行已更改并且必须同步所有数据（包括大型列数据）。</span><span class="sxs-lookup"><span data-stu-id="fbe38-159">Without column tracking, an application can only determine that a row has changed and would have to synchronize all the data that includes the large column data.</span></span> <span data-ttu-id="fbe38-160">但是，通过使用列跟踪，应用程序可以确定是否更改了大型列数据，并且仅同步已更改的数据。</span><span class="sxs-lookup"><span data-stu-id="fbe38-160">However, by using column tracking, an application can determine whether the large column data changed and only synchronize the data if it has changed.</span></span>  
  
 <span data-ttu-id="fbe38-161">列跟踪信息出现在 CHANGETABLE(CHANGES …) 函数返回的 SYS_CHANGE_COLUMNS 列中。</span><span class="sxs-lookup"><span data-stu-id="fbe38-161">Column tracking information appears in the SYS_CHANGE_COLUMNS column that is returned by the CHANGETABLE(CHANGES ...) function.</span></span>  
  
 <span data-ttu-id="fbe38-162">可以使用列跟踪，以便为未更改的列返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="fbe38-162">Column tracking can be used so that NULL is returned for a column that has not changed.</span></span> <span data-ttu-id="fbe38-163">如果可以将列更改为 NULL，则必须返回一个单独的列以指示是否更改了该列。</span><span class="sxs-lookup"><span data-stu-id="fbe38-163">If the column can be changed to NULL, a separate column must be returned to indicate whether the column changed.</span></span>  
  
 <span data-ttu-id="fbe38-164">在下面的示例中，如果 `CT_ThumbnailPhoto` 列未更改，则为该列返回 `NULL` 。</span><span class="sxs-lookup"><span data-stu-id="fbe38-164">In the following example, the `CT_ThumbnailPhoto` column will be `NULL` if that column did not change.</span></span> <span data-ttu-id="fbe38-165">该列本身也可能为 `NULL` ，因为已将其更改为 `NULL` ；应用程序可以使用 `CT_ThumbNailPhoto_Changed` 列来确定是否更改了该列。</span><span class="sxs-lookup"><span data-stu-id="fbe38-165">This column could also be `NULL` because it was changed to `NULL` - the application can use the `CT_ThumbNailPhoto_Changed` column to determine whether the column changed.</span></span>  
  
```sql  
DECLARE @PhotoColumnId int = COLUMNPROPERTY(  
    OBJECT_ID('SalesLT.Product'),'ThumbNailPhoto', 'ColumnId')  
  
SELECT  
    CT.ProductID, P.Name, P.ListPrice, -- Always obtain values.  
    CASE  
           WHEN CHANGE_TRACKING_IS_COLUMN_IN_MASK(  
                     @PhotoColumnId, CT.SYS_CHANGE_COLUMNS) = 1  
            THEN ThumbNailPhoto  
            ELSE NULL  
      END AS CT_ThumbNailPhoto,  
      CHANGE_TRACKING_IS_COLUMN_IN_MASK(  
                     @PhotoColumnId, CT.SYS_CHANGE_COLUMNS) AS  
                                   CT_ThumbNailPhoto_Changed  
     CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS,  
     CT.SYS_CHANGE_CONTEXT  
FROM  
     SalesLT.Product AS P  
INNER JOIN  
     CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
ON  
     P.ProductID = CT.ProductID AND  
     CT.SYS_CHANGE_OPERATION = 'U'  
```  
  
### <a name="obtaining-consistent-and-correct-results"></a><span data-ttu-id="fbe38-166">获得一致且正确的结果</span><span class="sxs-lookup"><span data-stu-id="fbe38-166">Obtaining Consistent and Correct Results</span></span>  
 <span data-ttu-id="fbe38-167">若要获取更改的表数据，您需要执行多个步骤。</span><span class="sxs-lookup"><span data-stu-id="fbe38-167">Obtaining the changed data for a table requires multiple steps.</span></span> <span data-ttu-id="fbe38-168">请注意，如果没有考虑到并处理某些问题，可能会返回不一致或错误的结果。</span><span class="sxs-lookup"><span data-stu-id="fbe38-168">Be aware that inconsistent or incorrect results could be returned if certain issues are not considered and handled.</span></span>  
  
 <span data-ttu-id="fbe38-169">例如，若要获取对 Sales 和 SalesOrders 表所做的更改，应用程序应执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="fbe38-169">For example, to obtain the changes that were made to a Sales table and SalesOrders table, an application would perform the following steps:</span></span>  
  
1.  <span data-ttu-id="fbe38-170">使用 CHANGE_TRACKING_MIN_VALID_VERSION() 验证上次同步版本。</span><span class="sxs-lookup"><span data-stu-id="fbe38-170">Validate the last synchronized version by using CHANGE_TRACKING_MIN_VALID_VERSION().</span></span>  
  
2.  <span data-ttu-id="fbe38-171">使用 CHANGE_TRACKING_CURRENT_VERSION() 获取可供下次获取更改时使用的版本。</span><span class="sxs-lookup"><span data-stu-id="fbe38-171">Obtain the version that can be used to obtain change the next time by using CHANGE_TRACKING_CURRENT_VERSION().</span></span>  
  
3.  <span data-ttu-id="fbe38-172">使用 CHANGETABLE(CHANGES …) 获取对 Sales 表所做的更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-172">Obtain the changes for the Sales table by using CHANGETABLE(CHANGES ...).</span></span>  
  
4.  <span data-ttu-id="fbe38-173">使用 CHANGETABLE(CHANGES …) 获取对 SalesOrders 表所做的更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-173">Obtain the changes for the SalesOrders table by using CHANGETABLE(CHANGES ...).</span></span>  
  
 <span data-ttu-id="fbe38-174">数据库中运行的两个进程可能会影响上述步骤返回的结果：</span><span class="sxs-lookup"><span data-stu-id="fbe38-174">Two processes are occurring in the database that can affect the results that are returned by the previous steps:</span></span>  
  
-   <span data-ttu-id="fbe38-175">清除进程在后台运行，并删除早于指定保持期的更改跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="fbe38-175">The cleanup process runs in the background and removes change tracking information that is older than the specified retention period.</span></span>  
  
     <span data-ttu-id="fbe38-176">清除进程是一个单独的后台进程，它使用在为数据库配置更改跟踪时指定的保持期。</span><span class="sxs-lookup"><span data-stu-id="fbe38-176">The cleanup process is a separate background process that uses the retention period that is specified when you configure change tracking for the database.</span></span> <span data-ttu-id="fbe38-177">问题是清除进程可能会在验证上次同步版本之后以及调用 CHANGETABLE(CHANGES…) 之前运行。</span><span class="sxs-lookup"><span data-stu-id="fbe38-177">The issue is that the cleanup process can occur in the time between when the last synchronization version was validated and when the call to CHANGETABLE(CHANGES...) is made.</span></span> <span data-ttu-id="fbe38-178">到获取更改时，刚刚还有效的上次同步版本可能不再有效。</span><span class="sxs-lookup"><span data-stu-id="fbe38-178">A last synchronization version that was just valid might no longer be valid by the time the changes are obtained.</span></span> <span data-ttu-id="fbe38-179">因此，可能会返回错误的结果。</span><span class="sxs-lookup"><span data-stu-id="fbe38-179">Therefore, incorrect results might be returned.</span></span>  
  
-   <span data-ttu-id="fbe38-180">正在 Sales 和 SalesOrders 表中执行 DML 操作，如下面的操作：</span><span class="sxs-lookup"><span data-stu-id="fbe38-180">Ongoing DML operations are occurring in the Sales and SalesOrders tables, such as the following operations:</span></span>  
  
    -   <span data-ttu-id="fbe38-181">在使用 CHANGE_TRACKING_CURRENT_VERSION() 获取下次使用的版本后，可能对表进行了更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-181">Changes can be made to the tables after the version for next time has been obtained by using CHANGE_TRACKING_CURRENT_VERSION().</span></span> <span data-ttu-id="fbe38-182">因此，返回的更改可能超过预期数量。</span><span class="sxs-lookup"><span data-stu-id="fbe38-182">Therefore, more changes can be returned than expected.</span></span>  
  
    -   <span data-ttu-id="fbe38-183">可能在从 Sales 表中获取更改的调用以及从 SalesOrders 表中获取更改的调用之间提交了事务。</span><span class="sxs-lookup"><span data-stu-id="fbe38-183">A transaction could commit in the time between the call to obtain changes from the Sales table and the call to obtain changes from the SalesOrders table.</span></span> <span data-ttu-id="fbe38-184">因此，SalesOrder 表的结果可能包含 Sales 表中不存在的外键值。</span><span class="sxs-lookup"><span data-stu-id="fbe38-184">Therefore, the results for the SalesOrder table could have foreign key value that does not exist in the Sales table.</span></span>  
  
 <span data-ttu-id="fbe38-185">若要解决上面列出的难题，建议您使用快照隔离。</span><span class="sxs-lookup"><span data-stu-id="fbe38-185">To overcome the previously listed challenges, we recommend that you use snapshot isolation.</span></span> <span data-ttu-id="fbe38-186">这有助于确保更改信息的一致性，并避免出现与后台清除任务有关的争用情况。</span><span class="sxs-lookup"><span data-stu-id="fbe38-186">This will help to ensure consistency of change information and avoid race conditions that are related to the background cleanup task.</span></span> <span data-ttu-id="fbe38-187">如果没有使用快照事务，在开发使用更改跟踪的应用程序时，可能需要增加很多工作量。</span><span class="sxs-lookup"><span data-stu-id="fbe38-187">If you do not use snapshot transactions, developing an application that uses change tracking could require significantly more effort.</span></span>  
  
#### <a name="using-snapshot-isolation"></a><span data-ttu-id="fbe38-188">使用快照隔离</span><span class="sxs-lookup"><span data-stu-id="fbe38-188">Using Snapshot Isolation</span></span>  
 <span data-ttu-id="fbe38-189">从设计上，更改跟踪可以很好地与快照隔离配合使用。</span><span class="sxs-lookup"><span data-stu-id="fbe38-189">Change tracking has been designed to work well with snapshot isolation.</span></span> <span data-ttu-id="fbe38-190">必须为数据库启用快照隔离。</span><span class="sxs-lookup"><span data-stu-id="fbe38-190">Snapshot isolation must be enabled for the database.</span></span> <span data-ttu-id="fbe38-191">获取更改所需的所有步骤必须包含在快照事务中。</span><span class="sxs-lookup"><span data-stu-id="fbe38-191">All the steps that are required to obtain changes must be included inside a snapshot transaction.</span></span> <span data-ttu-id="fbe38-192">这可确保快照事务中的查询看不见在获取更改时对数据所做的所有更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-192">This will ensure that all changes that are made to data while obtaining changes will not be visible to the queries inside the snapshot transaction.</span></span>  
  
 <span data-ttu-id="fbe38-193">若要获取快照事务中的数据，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="fbe38-193">To obtain data inside a snapshot transaction, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="fbe38-194">将事务隔离级别设置为快照，然后启动一个事务。</span><span class="sxs-lookup"><span data-stu-id="fbe38-194">Set the transaction isolation level to snapshot and start a transaction.</span></span>  
  
2.  <span data-ttu-id="fbe38-195">使用 CHANGE_TRACKING_MIN_VALID_VERSION() 验证上次同步版本。</span><span class="sxs-lookup"><span data-stu-id="fbe38-195">Validate the last synchronization version by using CHANGE_TRACKING_MIN_VALID_VERSION().</span></span>  
  
3.  <span data-ttu-id="fbe38-196">使用 CHANGE_TRACKING_CURRENT_VERSION() 获取下次要使用的版本。</span><span class="sxs-lookup"><span data-stu-id="fbe38-196">Obtain the version to be used the next time by using CHANGE_TRACKING_CURRENT_VERSION().</span></span>  
  
4.  <span data-ttu-id="fbe38-197">使用 CHANGETABLE(CHANGES …) 获取对 Sales 表所做的更改</span><span class="sxs-lookup"><span data-stu-id="fbe38-197">Obtain the changes for the Sales table by using CHANGETABLE(CHANGES ...)</span></span>  
  
5.  <span data-ttu-id="fbe38-198">使用 CHANGETABLE(CHANGES …) 获取对 Salesorders 表所做的更改</span><span class="sxs-lookup"><span data-stu-id="fbe38-198">Obtain the changes for the Salesorders table by using CHANGETABLE(CHANGES ...)</span></span>  
  
6.  <span data-ttu-id="fbe38-199">提交事务。</span><span class="sxs-lookup"><span data-stu-id="fbe38-199">Commit the transaction.</span></span>  
  
 <span data-ttu-id="fbe38-200">由于获取更改所需的所有步骤都是在快照事务中执行的，因此，应注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="fbe38-200">Some points to remember as all steps to obtain changes are inside a snapshot transaction:</span></span>  
  
-   <span data-ttu-id="fbe38-201">如果清除是在验证上次同步版本之后进行的，则来自 CHANGETABLE(CHANGES …) 的结果仍将有效，因为在事务中看不见清除执行的删除操作。</span><span class="sxs-lookup"><span data-stu-id="fbe38-201">If cleanup occurs after the last synchronization version is validated, the results from CHANGETABLE(CHANGES ...) will still be valid as the delete operations performed by cleanup will not be visible inside the transaction.</span></span>  
  
-   <span data-ttu-id="fbe38-202">在获取下次同步版本后对 Sales 或 SalesOrders 表所做的所有更改将不可见，并且 CHANGETABLE(CHANGES …) 调用绝不会返回版本晚于 CHANGE_TRACKING_CURRENT_VERSION() 返回结果的更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-202">Any changes that are made to the Sales table or the SalesOrders table after the next synchronization version is obtained will not be visible, and the calls to CHANGETABLE(CHANGES ...) will never return changes with a version later than that returned by CHANGE_TRACKING_CURRENT_VERSION().</span></span> <span data-ttu-id="fbe38-203">还会保持 Sales 和 SalesOrders 表之间的一致性，因为在 CHANGETABLE(CHANGES …) 调用之间提交的事务将不可见。</span><span class="sxs-lookup"><span data-stu-id="fbe38-203">Consistency between the Sales table and the SalesOrders table will also be maintained, because the transactions that were committed in the time between calls to CHANGETABLE(CHANGES ...) will not be visible.</span></span>  
  
 <span data-ttu-id="fbe38-204">下面的示例说明了如何为数据库启用快照隔离。</span><span class="sxs-lookup"><span data-stu-id="fbe38-204">The following example shows how snapshot isolation is enabled for a database.</span></span>  
  
```sql  
-- The database must be configured to enable snapshot isolation.  
ALTER DATABASE AdventureWorksLT  
    SET ALLOW_SNAPSHOT_ISOLATION ON;  
```  
  
 <span data-ttu-id="fbe38-205">快照事务是按如下方式使用的：</span><span class="sxs-lookup"><span data-stu-id="fbe38-205">A snapshot transaction is used as follows:</span></span>  
  
```sql  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
BEGIN TRAN  
  -- Verify that version of the previous synchronization is valid.  
  -- Obtain the version to use next time.  
  -- Obtain changes.  
COMMIT TRAN  
```  
  
 <span data-ttu-id="fbe38-206">有关快照事务的详细信息，请参阅 [SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fbe38-206">For more information about snapshot transactions, see [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span>  
  
#### <a name="alternatives-to-using-snapshot-isolation"></a><span data-ttu-id="fbe38-207">使用快照隔离的替代方法</span><span class="sxs-lookup"><span data-stu-id="fbe38-207">Alternatives to Using Snapshot Isolation</span></span>  
 <span data-ttu-id="fbe38-208">使用快照隔离有一些替代方法，但它们需要完成更多的工作以确保满足所有应用程序要求。</span><span class="sxs-lookup"><span data-stu-id="fbe38-208">There are alternatives to using snapshot isolation, but they require more work to make sure all application requirements are met.</span></span> <span data-ttu-id="fbe38-209">若要确保 *last_synchronization_version* 有效，并且清除进程在获取更改之前没有删除数据，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="fbe38-209">To make sure the *last_synchronization_version* is valid and data is not removed by the cleanup process before changes are obtained, do the following:</span></span>  
  
1.  <span data-ttu-id="fbe38-210">调用 CHANGETABLE() 后检查 *last_synchronization_version* 。</span><span class="sxs-lookup"><span data-stu-id="fbe38-210">Check *last_synchronization_version* after the calls to CHANGETABLE().</span></span>  
  
2.  <span data-ttu-id="fbe38-211">在使用 CHANGETABLE() 获取更改的每个查询中检查 *last_synchronization_version* 。</span><span class="sxs-lookup"><span data-stu-id="fbe38-211">Check *last_synchronization_version* as part of each query to obtain changes by using CHANGETABLE().</span></span>  
  
 <span data-ttu-id="fbe38-212">在为下次枚举获取同步版本后，可能会发生数据更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-212">Changes can occur after the synchronization version for the next enumeration has been obtained.</span></span> <span data-ttu-id="fbe38-213">可以使用两种方法来处理这种情况。</span><span class="sxs-lookup"><span data-stu-id="fbe38-213">There are two ways to handle this situation.</span></span> <span data-ttu-id="fbe38-214">所使用的选项取决于应用程序及其处理每种方法的副作用的方式：</span><span class="sxs-lookup"><span data-stu-id="fbe38-214">The option that is used depends on the application and how it can handle the side-effects of each approach:</span></span>  
  
-   <span data-ttu-id="fbe38-215">忽略版本高于新同步版本的更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-215">Ignore changes that have a version larger than the new synchronization version.</span></span>  
  
     <span data-ttu-id="fbe38-216">这种方法具有以下副作用：如果创建或更新的行版本早于新同步版本，将跳过新行或更新的行，但以后会对其进行更新。</span><span class="sxs-lookup"><span data-stu-id="fbe38-216">This approach has the side effect that a new or updated row would be skipped if it was created or updated before the new synchronization version, but then updated afterward.</span></span> <span data-ttu-id="fbe38-217">如果有一个新行，并且另一个表中创建的行引用跳过的行，则可能会出现引用完整性问题。</span><span class="sxs-lookup"><span data-stu-id="fbe38-217">If there is a new row, a referential integrity problem might occur if there was a row in another table that was created that referenced the skipped row.</span></span> <span data-ttu-id="fbe38-218">如果更新了某个现有行，将跳过该行，并且下次才会对其进行同步。</span><span class="sxs-lookup"><span data-stu-id="fbe38-218">If there is an updated existing row, the row will be skipped and not synchronized until the next time.</span></span>  
  
-   <span data-ttu-id="fbe38-219">包括所有更改，即便更改的版本高于新同步版本。</span><span class="sxs-lookup"><span data-stu-id="fbe38-219">Include all changes, even those that have a version larger than the new synchronization version.</span></span>  
  
     <span data-ttu-id="fbe38-220">下次进行同步时，将重新获取版本高于新同步版本的行。</span><span class="sxs-lookup"><span data-stu-id="fbe38-220">The rows that have a version larger than the new synchronization version will be obtained again on the next synchronization.</span></span> <span data-ttu-id="fbe38-221">应用程序必须能够预料并处理这种情况。</span><span class="sxs-lookup"><span data-stu-id="fbe38-221">This must be expected and handled by the application.</span></span>  
  
 <span data-ttu-id="fbe38-222">除了上述两个选项外，还可以设计结合这两个选项的方法，具体取决于所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="fbe38-222">In addition to the previous two options, you can devise approach that combines both options, depending on the operation.</span></span> <span data-ttu-id="fbe38-223">例如，您可能希望应用程序最好忽略晚于下次同步版本（在该版本中创建或删除了行）的更改，但不忽略更新。</span><span class="sxs-lookup"><span data-stu-id="fbe38-223">For example, you might want an application for which it is best to ignore changes newer than the next synchronization version in which the row was created or deleted, but updates are not ignored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fbe38-224">若要在使用更改跟踪（或任何自定义跟踪机制）时选择适合应用程序的方法，您需要完成大量的分析工作。</span><span class="sxs-lookup"><span data-stu-id="fbe38-224">Choosing the approach that will work for the application when you are using change tracking (or any custom tracking mechanism), requires significant analysis.</span></span> <span data-ttu-id="fbe38-225">因此，使用快照隔离要简单得多。</span><span class="sxs-lookup"><span data-stu-id="fbe38-225">Therefore, it is much simpler to use snapshot isolation.</span></span>  
  
##  <a name="how-change-tracking-handles-changes-to-a-database"></a><a name="Handles"></a><span data-ttu-id="fbe38-226">更改跟踪如何处理对数据库的更改</span><span class="sxs-lookup"><span data-stu-id="fbe38-226">How Change Tracking Handles Changes to a Database</span></span>  
 <span data-ttu-id="fbe38-227">某些使用更改跟踪的应用程序执行与另一个数据存储区的双向同步。</span><span class="sxs-lookup"><span data-stu-id="fbe38-227">Some applications that use change tracking perform two-way synchronization with another data store.</span></span> <span data-ttu-id="fbe38-228">即，在一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中所做的更改将更新到另一个数据存储区中，而在该数据存储区中所做的更改将更新到该 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中。</span><span class="sxs-lookup"><span data-stu-id="fbe38-228">That is, changes that are made in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database are updated in the other data store, and changes that are made in the other store are updated in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="fbe38-229">当应用程序使用另一个数据存储区中的更改更新本地数据库时，应用程序必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="fbe38-229">When an application updates the local database with changes from another data store, the application must perform the following operations:</span></span>  
  
-   <span data-ttu-id="fbe38-230">检查冲突。</span><span class="sxs-lookup"><span data-stu-id="fbe38-230">Check for conflicts.</span></span>  
  
     <span data-ttu-id="fbe38-231">如果在两个数据存储区中同时更改相同的数据，则会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="fbe38-231">A conflict occurs when the same data is changed at the same time in both data stores.</span></span> <span data-ttu-id="fbe38-232">应用程序必须能够检查冲突，并获取足够的信息以便能够解决冲突。</span><span class="sxs-lookup"><span data-stu-id="fbe38-232">The application must be able to check for a conflict and obtain enough information to enable the conflict to be resolved.</span></span>  
  
-   <span data-ttu-id="fbe38-233">存储应用程序上下文信息。</span><span class="sxs-lookup"><span data-stu-id="fbe38-233">Store application context information.</span></span>  
  
     <span data-ttu-id="fbe38-234">应用程序存储具有更改跟踪信息的数据。</span><span class="sxs-lookup"><span data-stu-id="fbe38-234">The application stores data that has the change tracking information.</span></span> <span data-ttu-id="fbe38-235">如果更改是从本地数据库中获取的，则会将此信息与其他更改跟踪信息放在一起。</span><span class="sxs-lookup"><span data-stu-id="fbe38-235">This information would be available together with other change tracking information when changes were obtained from the local database.</span></span> <span data-ttu-id="fbe38-236">此上下文信息的一个常见示例是作为更改源的数据存储区的标识符。</span><span class="sxs-lookup"><span data-stu-id="fbe38-236">A common example of this contextual information is an identifier for the data store that was the source of the change.</span></span>  
  
 <span data-ttu-id="fbe38-237">若要执行上述操作，同步应用程序可使用下列函数：</span><span class="sxs-lookup"><span data-stu-id="fbe38-237">To perform the previous operations, a synchronization application can use the following functions:</span></span>  
  
-   <span data-ttu-id="fbe38-238">CHANGETABLE(VERSION...)</span><span class="sxs-lookup"><span data-stu-id="fbe38-238">CHANGETABLE(VERSION...)</span></span>  
  
     <span data-ttu-id="fbe38-239">当应用程序进行更改时，它可以使用该函数来检查冲突。</span><span class="sxs-lookup"><span data-stu-id="fbe38-239">When an application is making changes, it can use this function to check for conflicts.</span></span> <span data-ttu-id="fbe38-240">对于启用了更改跟踪的表，该函数可获取该表中指定行的最新更改跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="fbe38-240">The function obtains the latest change tracking information for a specified row in a change tracked table.</span></span> <span data-ttu-id="fbe38-241">更改跟踪信息包括上次更改的行的版本。</span><span class="sxs-lookup"><span data-stu-id="fbe38-241">The change tracking information includes the version of the row that was last changed.</span></span> <span data-ttu-id="fbe38-242">应用程序可以使用此信息来确定自上次应用程序同步后该行是否进行了更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-242">This information enables an application to determine whether the row was changed after the last time that the application was synchronized.</span></span>  
  
-   <span data-ttu-id="fbe38-243">WITH CHANGE_TRACKING_CONTEXT</span><span class="sxs-lookup"><span data-stu-id="fbe38-243">WITH CHANGE_TRACKING_CONTEXT</span></span>  
  
     <span data-ttu-id="fbe38-244">应用程序可以使用此子句来存储上下文数据。</span><span class="sxs-lookup"><span data-stu-id="fbe38-244">An application can use this clause to store context data.</span></span>  
  
### <a name="checking-for-conflicts"></a><span data-ttu-id="fbe38-245">检查冲突</span><span class="sxs-lookup"><span data-stu-id="fbe38-245">Checking for Conflicts</span></span>  
 <span data-ttu-id="fbe38-246">在双向同步方案中，客户端应用程序必须确定在应用程序上次获取更改后某一行是否有更新。</span><span class="sxs-lookup"><span data-stu-id="fbe38-246">In a two-way synchronization scenario, the client application must determine whether a row has not been updated since the application last obtained the changes.</span></span>  
  
 <span data-ttu-id="fbe38-247">下面的示例说明了如何使用 CHANGETABLE(VERSION …) 函数以最有效的方式检查冲突，而不是使用单独的查询。</span><span class="sxs-lookup"><span data-stu-id="fbe38-247">The following example shows how to use the CHANGETABLE(VERSION ...) function to check for conflicts in the most efficient way, without a separate query.</span></span> <span data-ttu-id="fbe38-248">在该示例中， `CHANGETABLE(VERSION ...)` 确定 `SYS_CHANGE_VERSION` 所指定的行的 `@product id`。</span><span class="sxs-lookup"><span data-stu-id="fbe38-248">In the example, `CHANGETABLE(VERSION ...)` determines the `SYS_CHANGE_VERSION` for the row specified by `@product id`.</span></span> <span data-ttu-id="fbe38-249">`CHANGETABLE(CHANGES ...)` 可以获取相同的信息，但效率较低。</span><span class="sxs-lookup"><span data-stu-id="fbe38-249">`CHANGETABLE(CHANGES ...)` can obtain the same information, but that would be less efficient.</span></span> <span data-ttu-id="fbe38-250">如果该行的 `SYS_CHANGE_VERSION` 值大于 `@last_sync_version`值，则说明有冲突。</span><span class="sxs-lookup"><span data-stu-id="fbe38-250">If the value of `SYS_CHANGE_VERSION` for the row is larger than the value of `@last_sync_version`, there is a conflict.</span></span> <span data-ttu-id="fbe38-251">如果有冲突，则不会更新该行。</span><span class="sxs-lookup"><span data-stu-id="fbe38-251">If there is a conflict, the row will not be updated.</span></span> <span data-ttu-id="fbe38-252">`ISNULL()` 检查是必需的，因为该行可能没有可用的更改信息。</span><span class="sxs-lookup"><span data-stu-id="fbe38-252">The `ISNULL()` check is required because there might be no change information available for the row.</span></span> <span data-ttu-id="fbe38-253">如果在启用更改跟踪或清除更改信息后没有更新该行，则不存在任何更改信息。</span><span class="sxs-lookup"><span data-stu-id="fbe38-253">No change information would exist if the row had not been updated since change tracking was enabled or since the change information was cleaned up.</span></span>  
  
```sql  
-- Assumption: @last_sync_version has been validated.  
  
UPDATE  
    SalesLT.Product  
SET  
    ListPrice = @new_listprice  
FROM  
    SalesLT.Product AS P  
WHERE  
    ProductID = @product_id AND  
    @last_sync_version >= ISNULL (  
        SELECT CT.SYS_CHANGE_VERSION  
        FROM CHANGETABLE(VERSION SalesLT.Product,  
                        (ProductID), (P.ProductID)) AS CT),  
        0)  
```  
  
 <span data-ttu-id="fbe38-254">以下代码可以检查更新的行数以及找出有关冲突的更多信息。</span><span class="sxs-lookup"><span data-stu-id="fbe38-254">The following code can check the updated row count and can identify more information about the conflict.</span></span>  
  
```sql  
-- If the change cannot be made, find out more information.  
IF (@@ROWCOUNT = 0)  
BEGIN  
    -- Obtain the complete change information for the row.  
    SELECT  
        CT.SYS_CHANGE_VERSION, CT.SYS_CHANGE_CREATION_VERSION,  
        CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS  
    FROM  
        CHANGETABLE(CHANGES SalesLT.Product, @last_sync_version) AS CT  
    WHERE  
        CT.ProductID = @product_id;  
  
    -- Check CT.SYS_CHANGE_VERSION to verify that it really was a conflict.  
    -- Check CT.SYS_CHANGE_OPERATION to determine the type of conflict:  
    -- update-update or update-delete.  
    -- The row that is specified by @product_id might no longer exist   
    -- if it has been deleted.  
END  
```  
  
### <a name="setting-context-information"></a><span data-ttu-id="fbe38-255">设置上下文信息</span><span class="sxs-lookup"><span data-stu-id="fbe38-255">Setting Context Information</span></span>  
 <span data-ttu-id="fbe38-256">通过使用 WITH CHANGE_TRACKING_CONTEXT 子句，应用程序可以将上下文信息与更改信息存储在一起。</span><span class="sxs-lookup"><span data-stu-id="fbe38-256">By using the WITH CHANGE_TRACKING_CONTEXT clause, an application can store context information together with the change information.</span></span> <span data-ttu-id="fbe38-257">可随后从 CHANGETABLE(CHANGES ...) 返回的 SYS_CHANGE_CONTEXT 列中获取此信息。</span><span class="sxs-lookup"><span data-stu-id="fbe38-257">This information can then be obtained from the SYS_CHANGE_CONTEXT column that is returned by CHANGETABLE(CHANGES ...).</span></span>  
  
 <span data-ttu-id="fbe38-258">上下文信息通常用于确定更改源。</span><span class="sxs-lookup"><span data-stu-id="fbe38-258">Context information is typically used to identify the source of the changes.</span></span> <span data-ttu-id="fbe38-259">如果可以确定更改源，数据存储区在重新同步时可使用该信息来避免获取更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-259">If the source of the change can be identified, that information can be used by a data store to avoid obtaining changes when it synchronizes again.</span></span>  
  
```sql  
  -- Try to update the row and check for a conflict.  
  WITH CHANGE_TRACKING_CONTEXT (@source_id)  
  UPDATE  
     SalesLT.Product  
  SET  
      ListPrice = @new_listprice  
  FROM  
      SalesLT.Product AS P  
  WHERE  
     ProductID = @product_id AND  
     @last_sync_version >= ISNULL (  
         (SELECT CT.SYS_CHANGE_VERSION FROM CHANGETABLE(VERSION SalesLT.Product,  
         (ProductID), (P.ProductID)) AS CT),  
         0)  
```  
  
### <a name="ensuring-consistent-and-correct-results"></a><span data-ttu-id="fbe38-260">确保获得一致且正确的结果</span><span class="sxs-lookup"><span data-stu-id="fbe38-260">Ensuring Consistent and Correct Results</span></span>  
 <span data-ttu-id="fbe38-261">在验证 @last_sync_version 值时，应用程序必须考虑清除过程。</span><span class="sxs-lookup"><span data-stu-id="fbe38-261">An application must consider the cleanup process when it validates the value of @last_sync_version.</span></span> <span data-ttu-id="fbe38-262">这是因为，在调用 CHANGE_TRACKING_MIN_VALID_VERSION() 后但在进行更新之前，可能已将数据删除。</span><span class="sxs-lookup"><span data-stu-id="fbe38-262">This is because data could have been removed after CHANGE_TRACKING_MIN_VALID_VERSION() was called, but before the update was made.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fbe38-263">建议您使用快照隔离，并在快照事务中进行更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-263">We recommend that you use snapshot isolation and make the changes within a snapshot transaction.</span></span>  
  
```sql  
-- Prerequisite is to ensure ALLOW_SNAPSHOT_ISOLATION is ON for the database.  
  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
BEGIN TRAN  
    -- Verify that last_sync_version is valid.  
    IF (@last_sync_version <  
CHANGE_TRACKING_MIN_VALID_VERSION(OBJECT_ID('SalesLT.Product')))  
    BEGIN  
       RAISERROR (N'Last_sync_version too old', 16, -1);  
    END  
    ELSE  
    BEGIN  
        -- Try to update the row.  
        -- Check @@ROWCOUNT and check for a conflict.  
    END  
COMMIT TRAN  
```  
  
> [!NOTE]  
>  <span data-ttu-id="fbe38-264">在快照事务启动之后，在该快照事务中正在更新的行可能已经在另一个事务中进行了更新。</span><span class="sxs-lookup"><span data-stu-id="fbe38-264">There is a possibility that the row being updated within the snapshot transaction could have been updated in another transaction after the snapshot transaction was started.</span></span> <span data-ttu-id="fbe38-265">在这种情况下，会发生快照隔离更新冲突并导致该事务终止。</span><span class="sxs-lookup"><span data-stu-id="fbe38-265">In this case, a snapshot isolation update conflict will occur and lead to the transaction being terminated.</span></span> <span data-ttu-id="fbe38-266">如果发生这种情况，请重试此更新。</span><span class="sxs-lookup"><span data-stu-id="fbe38-266">If this happens, retry the update.</span></span> <span data-ttu-id="fbe38-267">随后，这会导致检测到更改跟踪冲突并且不会更改任何行。</span><span class="sxs-lookup"><span data-stu-id="fbe38-267">This will then lead to a change tracking conflict being detected and no rows being changed.</span></span>  
  
##  <a name="change-tracking-and-data-restore"></a><a name="DataRestore"></a><span data-ttu-id="fbe38-268">更改跟踪和数据还原</span><span class="sxs-lookup"><span data-stu-id="fbe38-268">Change Tracking and Data Restore</span></span>  
 <span data-ttu-id="fbe38-269">对于需要同步的应用程序，必须考虑启用了更改跟踪的数据库恢复到早期版本数据的情况。</span><span class="sxs-lookup"><span data-stu-id="fbe38-269">Applications that require synchronization must consider the case in which a database that has change tracking enabled reverts to an earlier version of the data.</span></span> <span data-ttu-id="fbe38-270">如果发生故障转移到异步数据库镜像的情况，或者如果在使用日志传送时出现故障，则数据库从备份还原之后就会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="fbe38-270">This can occur after a database is restored from a backup, when there is a failover to an asynchronous database mirror, or when there is a failure when using log shipping.</span></span> <span data-ttu-id="fbe38-271">以下情况揭示了这一问题：</span><span class="sxs-lookup"><span data-stu-id="fbe38-271">The following scenario illustrates the issue:</span></span>  
  
1.  <span data-ttu-id="fbe38-272">表 T1 启用了更改跟踪，并且该表的最低有效版本为 50。</span><span class="sxs-lookup"><span data-stu-id="fbe38-272">Table T1 is change tracked, and the minimum valid version for table is 50.</span></span>  
  
2.  <span data-ttu-id="fbe38-273">客户端应用程序在版本 100 处同步数据，并获取有关版本 50 到 100 之间的所有更改的信息。</span><span class="sxs-lookup"><span data-stu-id="fbe38-273">A client application synchronizes data at version 100 and obtains information about all changes between versions 50 and 100.</span></span>  
  
3.  <span data-ttu-id="fbe38-274">在版本 100 之后又对表 T1 进行了其他更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-274">Additional changes are made to table T1 after version 100.</span></span>  
  
4.  <span data-ttu-id="fbe38-275">在版本 120 处出现故障，数据库管理员还原了数据库，但出现了数据丢失。</span><span class="sxs-lookup"><span data-stu-id="fbe38-275">At version 120, there is a failure and the database administrator restores the database with data loss.</span></span> <span data-ttu-id="fbe38-276">在还原操作之后，该表包含直至版本 70 的数据，最低同步版本仍为 50。</span><span class="sxs-lookup"><span data-stu-id="fbe38-276">After the restore operation, the table contains data up through version 70, and the minimum synchronized version is still 50.</span></span>  
  
     <span data-ttu-id="fbe38-277">也就是说，同步数据存储区具有主数据存储区中已不再存在的数据。</span><span class="sxs-lookup"><span data-stu-id="fbe38-277">This means that the synchronized data store has data that no longer exists in the primary data store.</span></span>  
  
5.  <span data-ttu-id="fbe38-278">T1 更新了许多次。</span><span class="sxs-lookup"><span data-stu-id="fbe38-278">T1 is updated many times.</span></span> <span data-ttu-id="fbe38-279">当前版本为 130。</span><span class="sxs-lookup"><span data-stu-id="fbe38-279">This brings the current version to 130.</span></span>  
  
6.  <span data-ttu-id="fbe38-280">客户端应用程序再次进行同步并提供上次同步版本号 100。</span><span class="sxs-lookup"><span data-stu-id="fbe38-280">The client application synchronizes again and supplies a last-synchronized version of 100.</span></span> <span data-ttu-id="fbe38-281">客户端会验证此版本号有效，因为 100 大于 50。</span><span class="sxs-lookup"><span data-stu-id="fbe38-281">The client validates this number successfully because 100 is greater than 50.</span></span>  
  
     <span data-ttu-id="fbe38-282">客户端获取版本 100 到 130 之间的更改。</span><span class="sxs-lookup"><span data-stu-id="fbe38-282">The client obtains changes between version 100 and 130.</span></span> <span data-ttu-id="fbe38-283">此时，客户端并不知道版本 70 到 100 之间的更改已经与以前不同。</span><span class="sxs-lookup"><span data-stu-id="fbe38-283">At this point, the client is not aware that the changes between 70 and 100 are not the same as before.</span></span> <span data-ttu-id="fbe38-284">客户端上的数据与服务器上的数据不同步。</span><span class="sxs-lookup"><span data-stu-id="fbe38-284">The data on the client and server are not synchronized.</span></span>  
  
 <span data-ttu-id="fbe38-285">请注意，如果将数据库恢复到版本 100 之后的某一版本，则同步不会出现问题。</span><span class="sxs-lookup"><span data-stu-id="fbe38-285">Note that if the database was recovered to a point after version 100, there would be no problems with synchronization.</span></span> <span data-ttu-id="fbe38-286">客户端和服务器将在下一个同步间隔内正确同步数据。</span><span class="sxs-lookup"><span data-stu-id="fbe38-286">The client and server would synchronize data correctly during the next synchronization interval.</span></span>  
  
 <span data-ttu-id="fbe38-287">更改跟踪不支持恢复丢失的数据。</span><span class="sxs-lookup"><span data-stu-id="fbe38-287">Change tracking does not provide support for recovering from the loss of data.</span></span> <span data-ttu-id="fbe38-288">但是，有两种选择可用于检测这些类型的同步问题：</span><span class="sxs-lookup"><span data-stu-id="fbe38-288">However, there are two options for detecting these types of synchronization issues:</span></span>  
  
-   <span data-ttu-id="fbe38-289">在服务器上存储数据库版本 ID，每次恢复数据库或丢失数据时都更新此值。</span><span class="sxs-lookup"><span data-stu-id="fbe38-289">Store a database version ID on the server, and update this value whenever a database is recovered or otherwise loses data.</span></span> <span data-ttu-id="fbe38-290">每个客户端应用程序将存储该 ID，并且每个客户端在同步数据时必须验证此 ID。</span><span class="sxs-lookup"><span data-stu-id="fbe38-290">Each client application would store the ID, and each client would have to validate this ID when it synchronizes data.</span></span> <span data-ttu-id="fbe38-291">如果发生数据丢失，则 ID 将不匹配，并且客户端将重新初始化。</span><span class="sxs-lookup"><span data-stu-id="fbe38-291">If data loss occurs, the IDs will not match and the clients would reinitialize.</span></span> <span data-ttu-id="fbe38-292">这种方法有一个缺点，即如果数据丢失未越过上次的同步边界，则客户端可能会进行不必要的重新初始化。</span><span class="sxs-lookup"><span data-stu-id="fbe38-292">One drawback is if the data loss had not crossed the last synchronized boundary, the client might do unnecessary reinitialization.</span></span>  
  
-   <span data-ttu-id="fbe38-293">当客户端查询更改时，会在服务器上为每个客户端记录上次同步的版本号。</span><span class="sxs-lookup"><span data-stu-id="fbe38-293">When a client queries for changes, record the last synchronization version number for each client on the server.</span></span> <span data-ttu-id="fbe38-294">如果数据有问题，则上次同步的版本号将不匹配。</span><span class="sxs-lookup"><span data-stu-id="fbe38-294">If there is a problem with the data, the last synchronized version numbers would not match.</span></span> <span data-ttu-id="fbe38-295">这表明需要进行重新初始化。</span><span class="sxs-lookup"><span data-stu-id="fbe38-295">This indicates that a reinitialization is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbe38-296">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fbe38-296">See Also</span></span>  
 <span data-ttu-id="fbe38-297">[跟踪数据更改 (SQL Server)](../track-changes/track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fbe38-297">[Track Data Changes &#40;SQL Server&#41;](../track-changes/track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="fbe38-298">[关于更改跟踪 (SQL Server)](../track-changes/about-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fbe38-298">[About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="fbe38-299">[管理更改跟踪 &#40;SQL Server&#41;](../track-changes/manage-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fbe38-299">[Manage Change Tracking &#40;SQL Server&#41;](../track-changes/manage-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="fbe38-300">[启用和禁用更改跟踪 &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fbe38-300">[Enable and Disable Change Tracking &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="fbe38-301">[CHANGETABLE &#40;Transact-sql&#41;](/sql/relational-databases/system-functions/changetable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fbe38-301">[CHANGETABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/changetable-transact-sql) </span></span>  
 <span data-ttu-id="fbe38-302">[CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-sql&#41;](/sql/relational-databases/system-functions/change-tracking-min-valid-version-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fbe38-302">[CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/change-tracking-min-valid-version-transact-sql) </span></span>  
 <span data-ttu-id="fbe38-303">[CHANGE_TRACKING_CURRENT_VERSION &#40;Transact-sql&#41;](/sql/relational-databases/system-functions/change-tracking-current-version-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fbe38-303">[CHANGE_TRACKING_CURRENT_VERSION &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/change-tracking-current-version-transact-sql) </span></span>  
 [<span data-ttu-id="fbe38-304">WITH CHANGE_TRACKING_CONTEXT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="fbe38-304">WITH CHANGE_TRACKING_CONTEXT &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/with-change-tracking-context-transact-sql)  
  
  
