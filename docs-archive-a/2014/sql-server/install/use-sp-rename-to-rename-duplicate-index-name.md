---
title: 使用 sp_rename 重命名重复的索引名称 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- table names [SQL Server]
- duplicate table names
- index names [SQL Server]
- sp_rename
- duplicate index names
ms.assetid: ee66c7a5-eb6d-4fcf-970c-ab099d78c8d9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b8ffe3b9befd0c7239d32094e5738e0fb2947c5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694219"
---
# <a name="use-sp_rename-to-rename-duplicate-index-name"></a><span data-ttu-id="94d96-102">使用 sp_rename 重命名重复的索引名称</span><span class="sxs-lookup"><span data-stu-id="94d96-102">Use sp_rename to rename duplicate index name</span></span>
  <span data-ttu-id="94d96-103">升级顾问检测到重复的表或视图索引名称。</span><span class="sxs-lookup"><span data-stu-id="94d96-103">Upgrade Advisor has detected duplicate table or view index names.</span></span> <span data-ttu-id="94d96-104">请先重命名重复的索引以消除重复，然后再升级。</span><span class="sxs-lookup"><span data-stu-id="94d96-104">Rename the indexes to remove duplicates before upgrading.</span></span>  
  
## <a name="component"></a><span data-ttu-id="94d96-105">组件</span><span class="sxs-lookup"><span data-stu-id="94d96-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="94d96-106">纠正措施</span><span class="sxs-lookup"><span data-stu-id="94d96-106">Corrective Action</span></span>  
  
1.  <span data-ttu-id="94d96-107">执行以下查询找出重复的索引。</span><span class="sxs-lookup"><span data-stu-id="94d96-107">Locate the duplicate indexes by executing the following query.</span></span>  
  
    ```  
    SELECT DISTINCT OBJECT_NAME(o.id), name  
    FROM sysindexes as o  
    WHERE EXISTS   
        (SELECT name FROM sysindexes  as i  
          WHERE i.id = o.id  
          AND i.name = o.name and i.indid < o.indid);  
    ```  
  
2.  <span data-ttu-id="94d96-108">使用**sp_rename**更改其中一个索引名称。</span><span class="sxs-lookup"><span data-stu-id="94d96-108">Use **sp_rename** to change one of the index names.</span></span> <span data-ttu-id="94d96-109">由于索引名称相同，因此无法确定哪个索引将被重命名。</span><span class="sxs-lookup"><span data-stu-id="94d96-109">Because the index names are the same, you cannot determine which index will be renamed.</span></span> <span data-ttu-id="94d96-110">可通过此步骤区分索引。</span><span class="sxs-lookup"><span data-stu-id="94d96-110">This step allows you to differentiate the indexes.</span></span>  
  
    ```  
    EXEC sp_rename N'table_name.index_name', N'new_index_name', N'INDEX'  
    ```  
  
3.  <span data-ttu-id="94d96-111">通过执行以下查询来验证哪个索引进行了重命名。</span><span class="sxs-lookup"><span data-stu-id="94d96-111">Verify which index was renamed by executing the following query.</span></span> <span data-ttu-id="94d96-112">此查询返回指定表或视图的所有索引（包括键列名）。</span><span class="sxs-lookup"><span data-stu-id="94d96-112">This query returns all indexes (including key column names) on the specified table or view.</span></span>  
  
    ```  
    SELECT i.name AS IndexName, c.name AS ColumnName, ik.colid, ik.keyno  
    FROM sysindexes i  
    JOIN sysindexkeys ik ON i.id = ik.id and i.indid = ik.indid   
    JOIN syscolumns c ON c.id = ik.id and ik.colid = c.colid  
    WHERE i.id = OBJECT_ID('table_or_view_name')  
    ```  
  
4.  <span data-ttu-id="94d96-113">如有必要，请再次使用**sp_rename**来更正索引名称。</span><span class="sxs-lookup"><span data-stu-id="94d96-113">If necessary, use **sp_rename** again to correct the index names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94d96-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94d96-114">See Also</span></span>  
 <span data-ttu-id="94d96-115">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="94d96-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="94d96-116">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="94d96-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
