---
title: 授予访问数据库对象的权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 22bd0bb1f01e59ec30f7cf1bbf128c890d3d5d64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590470"
---
# <a name="granting-access-to-a-database-object"></a><span data-ttu-id="e646c-102">授予访问数据库对象的权限</span><span class="sxs-lookup"><span data-stu-id="e646c-102">Granting Access to a Database Object</span></span>
  <span data-ttu-id="e646c-103">作为管理员，可以从 **Products** 表和 **vw_Names** 视图执行 Select，以及执行 **pr_Names** 过程；但是 Mary 不能。</span><span class="sxs-lookup"><span data-stu-id="e646c-103">As an administrator, you can execute the SELECT from the **Products** table and the **vw_Names** view, and execute the **pr_Names** procedure; however, Mary cannot.</span></span> <span data-ttu-id="e646c-104">若要授予 Mary 必要的权限，请使用 GRANT 语句。</span><span class="sxs-lookup"><span data-stu-id="e646c-104">To grant Mary the necessary permissions, use the GRANT statement.</span></span>  
  
### <a name="procedure-title"></a><span data-ttu-id="e646c-105">过程标题</span><span class="sxs-lookup"><span data-stu-id="e646c-105">Procedure Title</span></span>  
  
1.  <span data-ttu-id="e646c-106">执行以下语句将 `Mary` 存储过程的 `EXECUTE` 权限授予 `pr_Names` 。</span><span class="sxs-lookup"><span data-stu-id="e646c-106">Execute the following statement to give `Mary` the `EXECUTE` permission for the `pr_Names` stored procedure.</span></span>  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
 <span data-ttu-id="e646c-107">在这种情况下，Mary 只能通过使用存储过程访问 **Products** 表。</span><span class="sxs-lookup"><span data-stu-id="e646c-107">In this scenario, Mary can only access the **Products** table by using the stored procedure.</span></span> <span data-ttu-id="e646c-108">如果您希望 Mary 能够对视图执行 SELECT 语句，则您还必须执行 `GRANT SELECT ON vw_Names TO Mary`。</span><span class="sxs-lookup"><span data-stu-id="e646c-108">If you want Mary to be able to execute a SELECT statement against the view, then you must also execute `GRANT SELECT ON vw_Names TO Mary`.</span></span> <span data-ttu-id="e646c-109">若要删除对数据库对象的访问权限，请使用 REVOKE 语句。</span><span class="sxs-lookup"><span data-stu-id="e646c-109">To remove access to database objects, use the REVOKE statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e646c-110">如果表、视图和存储过程不是由同一架构拥有，则授予权限将变得更复杂。</span><span class="sxs-lookup"><span data-stu-id="e646c-110">If the table, the view, and the stored procedure are not owned by the same schema, granting permissions becomes more complex.</span></span>  
  
## <a name="about-grant"></a><span data-ttu-id="e646c-111">关于 GRANT</span><span class="sxs-lookup"><span data-stu-id="e646c-111">About GRANT</span></span>  
 <span data-ttu-id="e646c-112">必须具有 EXECUTE 权限才能执行存储过程。</span><span class="sxs-lookup"><span data-stu-id="e646c-112">You must have EXECUTE permission to execute a stored procedure.</span></span> <span data-ttu-id="e646c-113">必须具有 SELECT、INSERT、UPDATE 和 DELETE 权限才能访问和更改数据。</span><span class="sxs-lookup"><span data-stu-id="e646c-113">You must have SELECT, INSERT, UPDATE, and DELETE permissions to access and change data.</span></span> <span data-ttu-id="e646c-114">GRANT 语句还用于其他权限，如创建表的权限。</span><span class="sxs-lookup"><span data-stu-id="e646c-114">The GRANT statement is also used for other permissions, such as permission to create tables.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="e646c-115">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="e646c-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="e646c-116">摘要：配置数据库对象的权限</span><span class="sxs-lookup"><span data-stu-id="e646c-116">Summary: Configuring Permissions on Database Objects</span></span>](lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="e646c-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e646c-117">See Also</span></span>  
 <span data-ttu-id="e646c-118">[GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e646c-118">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 [<span data-ttu-id="e646c-119">REVOKE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e646c-119">REVOKE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/revoke-transact-sql)  
  
  
