---
title: 重命名用户定义函数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: c2695a5c-9cc5-4b18-8771-53027ca9a9af
author: rothja
ms.author: jroth
ms.openlocfilehash: ec923be64cf7819c4018ebda71a472f58b29cf8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591817"
---
# <a name="rename-user-defined-functions"></a><span data-ttu-id="fad18-102">重命名用户定义函数</span><span class="sxs-lookup"><span data-stu-id="fad18-102">Rename User-defined Functions</span></span>
  <span data-ttu-id="fad18-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 重命名 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="fad18-103">You can rename user-defined functions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="fad18-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="fad18-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fad18-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="fad18-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fad18-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="fad18-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fad18-107">安全性</span><span class="sxs-lookup"><span data-stu-id="fad18-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fad18-108">**若要重命名用户定义函数，请使用：**</span><span class="sxs-lookup"><span data-stu-id="fad18-108">**To rename user-defined functions, using:**</span></span>  
  
     [<span data-ttu-id="fad18-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fad18-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fad18-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fad18-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fad18-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="fad18-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fad18-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="fad18-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fad18-113">函数名称必须符合 [标识符](../databases/database-identifiers.md)规则。</span><span class="sxs-lookup"><span data-stu-id="fad18-113">Function names must comply with the rules for [identifiers](../databases/database-identifiers.md).</span></span>  
  
-   <span data-ttu-id="fad18-114">重命名用户定义函数将不会更改 **sys.sql_modules** 目录视图的定义列中相应对象名的名称。</span><span class="sxs-lookup"><span data-stu-id="fad18-114">Renaming a user-defined function will not change the name of the corresponding object name in the definition column of the **sys.sql_modules** catalog view.</span></span> <span data-ttu-id="fad18-115">因此，我们建议不要重命名此对象类型。</span><span class="sxs-lookup"><span data-stu-id="fad18-115">Therefore, we recommend that you do not rename this object type.</span></span> <span data-ttu-id="fad18-116">而是删除存储过程，然后使用新名称重新创建该存储过程。</span><span class="sxs-lookup"><span data-stu-id="fad18-116">Instead, drop and re-create the stored procedure with its new name.</span></span>  
  
-   <span data-ttu-id="fad18-117">在未将对象更新为反映已对用户定义函数所做的更改时，更改用户定义函数的名称或定义可能导致依赖对象失败。</span><span class="sxs-lookup"><span data-stu-id="fad18-117">Changing the name or definition of a user-defined function can cause dependent objects to fail when the objects are not updated to reflect the changes that have been made to the function.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fad18-118">Security</span><span class="sxs-lookup"><span data-stu-id="fad18-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fad18-119">权限</span><span class="sxs-lookup"><span data-stu-id="fad18-119">Permissions</span></span>  
 <span data-ttu-id="fad18-120">若要删除函数，要求对函数所属架构具有 ALTER 权限，或对函数具有 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="fad18-120">To drop the function, requires either ALTER permission on the schema to which the function belongs or CONTROL permission on the function.</span></span> <span data-ttu-id="fad18-121">若要重新创建函数，要求在数据库中具有 CREATE FUNCTION 权限，并对创建函数时所在的架构具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="fad18-121">To re-create the function, requires CREATE FUNCTION permission in the database and ALTER permission on the schema in which the function is being created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fad18-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fad18-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-user-defined-functions"></a><span data-ttu-id="fad18-123">重命名用户定义函数</span><span class="sxs-lookup"><span data-stu-id="fad18-123">To rename user-defined functions</span></span>  
  
1.  <span data-ttu-id="fad18-124">在 **“对象资源管理器”** 中，单击包含您要重命名的函数的数据库旁边的加号，然后</span><span class="sxs-lookup"><span data-stu-id="fad18-124">In **Object Explorer**, click the plus sign next to the database that contains the function you wish to rename and then</span></span>  
  
2.  <span data-ttu-id="fad18-125">单击 **“可编程性”** 文件夹旁的加号。</span><span class="sxs-lookup"><span data-stu-id="fad18-125">Click the plus sign next to the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="fad18-126">单击包含要重命名的函数的文件夹旁边的加号：</span><span class="sxs-lookup"><span data-stu-id="fad18-126">Click the plus sign next to the folder that contains the function you wish to rename:</span></span>  
  
    -   <span data-ttu-id="fad18-127">Table-valued Function</span><span class="sxs-lookup"><span data-stu-id="fad18-127">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="fad18-128">标量值函数</span><span class="sxs-lookup"><span data-stu-id="fad18-128">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="fad18-129">Aggregate 函数</span><span class="sxs-lookup"><span data-stu-id="fad18-129">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="fad18-130">右键单击要重命名的函数，然后选择“重命名”  。</span><span class="sxs-lookup"><span data-stu-id="fad18-130">Right-click the function you wish to rename and select **Rename**.</span></span>  
  
5.  <span data-ttu-id="fad18-131">输入函数的新名称。</span><span class="sxs-lookup"><span data-stu-id="fad18-131">Enter the function's new name.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fad18-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fad18-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="fad18-133">**重命名用户定义函数**</span><span class="sxs-lookup"><span data-stu-id="fad18-133">**To rename user-defined functions**</span></span>  
  
 <span data-ttu-id="fad18-134">无法使用 Transact-SQL 语句执行此任务。</span><span class="sxs-lookup"><span data-stu-id="fad18-134">This task cannot be performed using Transact-SQL statements.</span></span> <span data-ttu-id="fad18-135">若要使用 Transact-SQL 重命名用户定义函数，必须首先删除现有的函数，然后用新名称重新创建函数。</span><span class="sxs-lookup"><span data-stu-id="fad18-135">To rename a user-defined function using Transact-SQL, you must first delete the existing function and then re-create it with the new name.</span></span> <span data-ttu-id="fad18-136">请确保使用了该函数的旧名称的所有代码和应用程序现在都使用该新名称。</span><span class="sxs-lookup"><span data-stu-id="fad18-136">Ensure that all code and applications that used the function's old name now use the new name.</span></span>  
  
 <span data-ttu-id="fad18-137">有关详细信息，请参阅 [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql) 和 [DROP FUNCTION (Transact-SQL)](/sql/t-sql/statements/drop-function-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fad18-137">For more information, see [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) and [DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fad18-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fad18-138">See Also</span></span>  
 <span data-ttu-id="fad18-139">[sys.sql_expression_dependencies (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fad18-139">[sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) </span></span>  
 [<span data-ttu-id="fad18-140">查看用户定义的函数</span><span class="sxs-lookup"><span data-stu-id="fad18-140">View User-defined Functions</span></span>](user-defined-functions.md)  
  
  
