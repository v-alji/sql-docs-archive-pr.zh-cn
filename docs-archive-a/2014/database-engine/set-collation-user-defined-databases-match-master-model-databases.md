---
title: 将用户定义数据库的排序规则设置为与 master 和 model 数据库的排序规则 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c686446f-dae1-4b05-a3df-837b3422988d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b48696fb56c40062d62f04845715170887f84fda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683042"
---
# <a name="set-the-collation-of-user-defined-databases-to-match-those-of-the-master-and-model-databases"></a><span data-ttu-id="079a5-102">将用户定义的数据库排序规则设置为与 master 和 model 数据库的排序规则一致</span><span class="sxs-lookup"><span data-stu-id="079a5-102">Set the Collation of User-defined Databases to Match Those of the master and model Databases</span></span>
  <span data-ttu-id="079a5-103">此规则检查用户定义的数据库是否是使用与 master 或 model 相同的数据库排序规则进行定义的。</span><span class="sxs-lookup"><span data-stu-id="079a5-103">This rule checks whether user-defined databases are defined by using a database collation that is the same as the collation for master or model.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="079a5-104">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="079a5-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="079a5-105">建议用户定义的数据库排序规则与 master 或 model 的排序规则一致。</span><span class="sxs-lookup"><span data-stu-id="079a5-105">We recommend that the collations of user-defined databases match the collation of master or model.</span></span> <span data-ttu-id="079a5-106">否则，可能会发生使代码无法执行的排序规则冲突。</span><span class="sxs-lookup"><span data-stu-id="079a5-106">Otherwise, collation conflicts can occur that might prevent code from executing.</span></span> <span data-ttu-id="079a5-107">例如，当存储过程将一个表连接到一个临时表时，如果用户定义的数据库排序规则与 model 数据库的排序规则不同，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可能会结束该批处理并返回一个排序规则冲突错误。</span><span class="sxs-lookup"><span data-stu-id="079a5-107">For example, when a stored procedure joins one table to a temporary table, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] might end the batch and return a collation conflict error if the collations of the user-defined database and the model database are different.</span></span> <span data-ttu-id="079a5-108">出现这种情况的原因是临时表是在 tempdb 中创建的，而后者的排序规则基于 model 的排序规则。</span><span class="sxs-lookup"><span data-stu-id="079a5-108">This occurs because temporary tables are created in tempdb, which bases its collation on that of model.</span></span>  
  
 <span data-ttu-id="079a5-109">如果遇到排序规则冲突错误，请考虑下面的解决方案之一：</span><span class="sxs-lookup"><span data-stu-id="079a5-109">If you experience collation conflict errors, consider one of the following solutions:</span></span>  
  
-   <span data-ttu-id="079a5-110">从用户数据库中导出数据，并将该数据导入排序规则与 master 和 model 数据库排序规则相同的新表中。</span><span class="sxs-lookup"><span data-stu-id="079a5-110">Export the data from the user database and import it into new tables that have the same collation as the master and model databases.</span></span>  
  
-   <span data-ttu-id="079a5-111">重新生成系统数据库以使用与用户数据库排序规则一致的排序规则。</span><span class="sxs-lookup"><span data-stu-id="079a5-111">Rebuild the system databases to use a collation that matches the user database collation.</span></span> <span data-ttu-id="079a5-112">有关如何重新生成系统数据库的详细信息，请参阅[重新生成系统数据库](../relational-databases/databases/system-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="079a5-112">For more information about how to rebuild the system databases, see [Rebuild System Databases](../relational-databases/databases/system-databases.md).</span></span>  
  
-   <span data-ttu-id="079a5-113">修改将用户表连接到 tempdb 中的表的任何存储过程，以便使用用户数据库的排序规则在 tempdb 中创建表。</span><span class="sxs-lookup"><span data-stu-id="079a5-113">Modify any stored procedures that join user tables to tables in tempdb to create the tables in tempdb by using the collation of the user database.</span></span> <span data-ttu-id="079a5-114">为此，请在临时表的列定义中添加 `COLLATE database_default` 子句，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="079a5-114">To do this, add the `COLLATE database_default` clause to the column definitions of the temporary table, as shown in the following example:</span></span>  
  
    ```  
    CREATE TABLE #temp1 ( c1 int, c2 varchar(30) COLLATE database_default )  
    ```  
  
## <a name="for-more-information"></a><span data-ttu-id="079a5-115">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="079a5-115">For More Information</span></span>  
 [<span data-ttu-id="079a5-116">设置或更改数据库排序规则</span><span class="sxs-lookup"><span data-stu-id="079a5-116">Set or Change the Database Collation</span></span>](../relational-databases/collations/set-or-change-the-database-collation.md)  
  
 [<span data-ttu-id="079a5-117">设置或更改列排序规则</span><span class="sxs-lookup"><span data-stu-id="079a5-117">Set or Change the Column Collation</span></span>](../relational-databases/collations/set-or-change-the-column-collation.md)  
  
 [<span data-ttu-id="079a5-118">ALTER DATABASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="079a5-118">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [<span data-ttu-id="079a5-119">COLLATE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="079a5-119">COLLATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/collations)  
  
 [<span data-ttu-id="079a5-120">sys.databases (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="079a5-120">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [<span data-ttu-id="079a5-121">Microsoft 知识库文章325335</span><span class="sxs-lookup"><span data-stu-id="079a5-121">Microsoft Knowledge Base article 325335</span></span>](https://go.microsoft.com/fwlink/?linkid=117751)  
  
 [<span data-ttu-id="079a5-122">如何从命令提示符安装 SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="079a5-122">How to: Install SQL Server 2008 from the Command Prompt</span></span>](https://go.microsoft.com/fwlink/?LinkId=81585)  
  
## <a name="see-also"></a><span data-ttu-id="079a5-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="079a5-123">See Also</span></span>  
 [<span data-ttu-id="079a5-124">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="079a5-124">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
