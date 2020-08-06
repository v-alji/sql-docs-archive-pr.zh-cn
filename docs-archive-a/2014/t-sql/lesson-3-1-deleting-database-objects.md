---
title: 删除数据库对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- deleting database objects
ms.assetid: dbb94fdf-c85b-477b-8e84-f830d259bade
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 6bd69935dbfac020c4c75bb391e7932009fd4197
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577991"
---
# <a name="deleting-database-objects"></a><span data-ttu-id="40fb2-102">删除数据库对象</span><span class="sxs-lookup"><span data-stu-id="40fb2-102">Deleting Database Objects</span></span>
  <span data-ttu-id="40fb2-103">若要删除在本教程中创建的所有对象，您只需删除数据库即可。</span><span class="sxs-lookup"><span data-stu-id="40fb2-103">To remove all traces of this tutorial, you could just delete the database.</span></span> <span data-ttu-id="40fb2-104">但是，在本主题中，您将完成下列步骤执行与教程中每项操作相反的操作。</span><span class="sxs-lookup"><span data-stu-id="40fb2-104">However, in this topic, you will go through the steps to reverse every action you took doing the tutorial.</span></span>  
  
### <a name="removing-permissions-and-objects"></a><span data-ttu-id="40fb2-105">删除权限和对象</span><span class="sxs-lookup"><span data-stu-id="40fb2-105">Removing permissions and objects</span></span>  
  
1.  <span data-ttu-id="40fb2-106">在删除对象之前，请确保使用正确的数据库：</span><span class="sxs-lookup"><span data-stu-id="40fb2-106">Before you delete objects, make sure you are in the correct database:</span></span>  
  
    ```  
    USE TestData;  
    GO  
    ```  
  
2.  <span data-ttu-id="40fb2-107">使用 `REVOKE` 语句删除 `Mary` 对存储过程的执行权限：</span><span class="sxs-lookup"><span data-stu-id="40fb2-107">Use the `REVOKE` statement to remove execute permission for `Mary` on the stored procedure:</span></span>  
  
    ```  
    REVOKE EXECUTE ON pr_Names FROM Mary;  
    GO  
  
    ```  
  
3.  <span data-ttu-id="40fb2-108">使用 `DROP` 语句删除 `Mary` 对 `TestData` 数据库的访问权限：</span><span class="sxs-lookup"><span data-stu-id="40fb2-108">Use the `DROP` statement to remove permission for `Mary` to access the `TestData` database:</span></span>  
  
    ```  
    DROP USER Mary;  
    GO  
  
    ```  
  
4.  <span data-ttu-id="40fb2-109">使用 `DROP` 语句删除 `Mary` 对此 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]实例的访问权限。</span><span class="sxs-lookup"><span data-stu-id="40fb2-109">Use the `DROP` statement to remove permission for `Mary` to access this instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]:</span></span>  
  
    ```  
    DROP LOGIN [<computer_name>\Mary];  
    GO  
  
    ```  
  
5.  <span data-ttu-id="40fb2-110">使用 `DROP` 语句删除存储过程 `pr_Names`：</span><span class="sxs-lookup"><span data-stu-id="40fb2-110">Use the `DROP` statement to remove the store procedure `pr_Names`:</span></span>  
  
    ```  
    DROP PROC pr_Names;  
    GO  
  
    ```  
  
6.  <span data-ttu-id="40fb2-111">使用 `DROP` 语句删除视图 `vw_Names`：</span><span class="sxs-lookup"><span data-stu-id="40fb2-111">Use the `DROP` statement to remove the view `vw_Names`:</span></span>  
  
    ```  
    DROP View vw_Names;  
    GO  
  
    ```  
  
7.  <span data-ttu-id="40fb2-112">使用 `DELETE` 语句删除 `Products` 表中的所有行：</span><span class="sxs-lookup"><span data-stu-id="40fb2-112">Use the `DELETE` statement to remove all rows from the `Products` table:</span></span>  
  
    ```  
    DELETE FROM Products;  
    GO  
  
    ```  
  
8.  <span data-ttu-id="40fb2-113">使用 `DROP` 语句删除 `Products` 表：</span><span class="sxs-lookup"><span data-stu-id="40fb2-113">Use the `DROP` statement to remove the `Products` table:</span></span>  
  
    ```  
    DROP Table Products;  
    GO  
  
    ```  
  
9. <span data-ttu-id="40fb2-114">正使用 `TestData` 数据库时，无法删除该数据库；因此，请首先将上下文切换到其他数据库，再使用 `DROP` 语句删除 `TestData` 数据库：</span><span class="sxs-lookup"><span data-stu-id="40fb2-114">You cannot remove the `TestData` database while you are in the database; therefore, first switch context to another database, and then use the `DROP` statement to remove the `TestData` database:</span></span>  
  
    ```  
    USE MASTER;  
    GO  
    DROP DATABASE TestData;  
    GO  
  
    ```  
  
 <span data-ttu-id="40fb2-115">“编写 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句”教程到此结束。</span><span class="sxs-lookup"><span data-stu-id="40fb2-115">This concludes the Writing [!INCLUDE[tsql](../includes/tsql-md.md)] Statements tutorial.</span></span> <span data-ttu-id="40fb2-116">请记住，本教程只是简要概述，它并未介绍所用语句的所有选项。</span><span class="sxs-lookup"><span data-stu-id="40fb2-116">Remember, this tutorial is a brief overview and it does not describe all the options to the statements that are used.</span></span> <span data-ttu-id="40fb2-117">设计和创建有效的数据库结构以及配置对数据的安全访问，需要比本教程中显示的数据库更复杂的数据库。</span><span class="sxs-lookup"><span data-stu-id="40fb2-117">Designing and creating an efficient database structure and configuring secure access to the data requires a more complex database than that shown in this tutorial.</span></span>  
  
## <a name="return-to-sql-server-tools-portal"></a><span data-ttu-id="40fb2-118">返回到 SQL Server 工具入门</span><span class="sxs-lookup"><span data-stu-id="40fb2-118">Return to SQL Server Tools Portal</span></span>  
 [<span data-ttu-id="40fb2-119">教程：编写 Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="40fb2-119">Tutorial: Writing Transact-SQL Statements</span></span>](tutorial-writing-transact-sql-statements.md)  
  
## <a name="see-also"></a><span data-ttu-id="40fb2-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40fb2-120">See Also</span></span>  
 <span data-ttu-id="40fb2-121">[REVOKE (Transact-SQL)](/sql/t-sql/statements/revoke-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40fb2-121">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span></span>  
 <span data-ttu-id="40fb2-122">[DROP USER (Transact-SQL)](/sql/t-sql/statements/drop-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40fb2-122">[DROP USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-user-transact-sql) </span></span>  
 <span data-ttu-id="40fb2-123">[DROP LOGIN &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40fb2-123">[DROP LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-login-transact-sql) </span></span>  
 <span data-ttu-id="40fb2-124">[DROP PROCEDURE &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40fb2-124">[DROP PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span></span>  
 <span data-ttu-id="40fb2-125">[DROP VIEW (Transact-SQL)](/sql/t-sql/statements/drop-view-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40fb2-125">[DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql) </span></span>  
 <span data-ttu-id="40fb2-126">[DELETE (Transact-SQL)](/sql/t-sql/statements/delete-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40fb2-126">[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) </span></span>  
 <span data-ttu-id="40fb2-127">[DROP TABLE (Transact-SQL)](/sql/t-sql/statements/drop-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40fb2-127">[DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) </span></span>  
 [<span data-ttu-id="40fb2-128">DROP DATABASE (Transact SQL)</span><span class="sxs-lookup"><span data-stu-id="40fb2-128">DROP DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-database-audit-specification-transact-sql)  
  
  
