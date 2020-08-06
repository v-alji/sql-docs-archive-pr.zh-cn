---
title: 执行用户定义函数 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- invoking user-defined functions
- user-defined functions [SQL Server], executing
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
author: rothja
ms.author: jroth
ms.openlocfilehash: 4446f3b3a132488fdac6e859f30abaca40a193d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591820"
---
# <a name="execute-user-defined-functions"></a><span data-ttu-id="7e3ad-102">执行用户定义函数</span><span class="sxs-lookup"><span data-stu-id="7e3ad-102">Execute User-defined Functions</span></span>
  <span data-ttu-id="7e3ad-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 执行 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="7e3ad-103">You can execute a user defined function in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="7e3ad-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="7e3ad-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7e3ad-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="7e3ad-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7e3ad-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="7e3ad-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7e3ad-107">安全性</span><span class="sxs-lookup"><span data-stu-id="7e3ad-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7e3ad-108">**若要执行用户定义函数，请使用：**</span><span class="sxs-lookup"><span data-stu-id="7e3ad-108">**To execute a user-defined function, using:**</span></span>  
  
     [<span data-ttu-id="7e3ad-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7e3ad-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7e3ad-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="7e3ad-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7e3ad-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="7e3ad-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="7e3ad-112">在 Transact-SQL 中，可通过使用 *value* 或使用 @*parameter_name*=*value*来提供参数。</span><span class="sxs-lookup"><span data-stu-id="7e3ad-112">In Transact-SQL, parameters can be supplied either by using *value* or by using @*parameter_name*=*value.*</span></span> <span data-ttu-id="7e3ad-113">来提供参数。参数不是事务的一部分；因此，如果在以后回退的事务中更改了参数，则此参数的值不会恢复为以前的值。</span><span class="sxs-lookup"><span data-stu-id="7e3ad-113">A parameter is not part of a transaction; therefore, if a parameter is changed in a transaction that is later rolled back, the value of the parameter does not revert to its previous value.</span></span> <span data-ttu-id="7e3ad-114">返回给调用方的值总是模块返回时的值。</span><span class="sxs-lookup"><span data-stu-id="7e3ad-114">The value returned to the caller is always the value at the time the module returns.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7e3ad-115">Security</span><span class="sxs-lookup"><span data-stu-id="7e3ad-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7e3ad-116">权限</span><span class="sxs-lookup"><span data-stu-id="7e3ad-116">Permissions</span></span>  
 <span data-ttu-id="7e3ad-117">运行 EXECUTE 语句无需权限。</span><span class="sxs-lookup"><span data-stu-id="7e3ad-117">Permissions are not required to run the EXECUTE statement.</span></span> <span data-ttu-id="7e3ad-118">但是，需要对 EXECUTE 字符串内引用的安全对象具有权限。</span><span class="sxs-lookup"><span data-stu-id="7e3ad-118">However, permissions are required on the securables that are referenced within the EXECUTE string.</span></span> <span data-ttu-id="7e3ad-119">例如，如果字符串包含 INSERT 语句，则 EXECUTE 语句的调用方对目标表必须具有 INSERT 权限。</span><span class="sxs-lookup"><span data-stu-id="7e3ad-119">For example, if the string contains an INSERT statement, the caller of the EXECUTE statement must have INSERT permission on the target table.</span></span> <span data-ttu-id="7e3ad-120">在遇到 EXECUTE 语句时，即使 EXECUTE 语句包含于模块内，也将检查权限。</span><span class="sxs-lookup"><span data-stu-id="7e3ad-120">Permissions are checked at the time EXECUTE statement is encountered, even if the EXECUTE statement is included within a module.</span></span> <span data-ttu-id="7e3ad-121">有关详细信息，请参阅[EXECUTE &#40;transact-sql&#41;](/sql/t-sql/language-elements/execute-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="7e3ad-121">For more information, see [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7e3ad-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7e3ad-122">Using Transact-SQL</span></span>  
  
#### <a name="to-execute-a-user-defined-function"></a><span data-ttu-id="7e3ad-123">执行用户定义函数</span><span class="sxs-lookup"><span data-stu-id="7e3ad-123">To execute a user-defined function</span></span>  
  
1.  <span data-ttu-id="7e3ad-124">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="7e3ad-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7e3ad-125">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="7e3ad-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7e3ad-126">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="7e3ad-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Declares a variable and sets it to zero.  
    -- This variable is used to return the results of the function.  
    DECLARE @ret nvarchar(15)= NULL;   
  
    -- Executes the dbo.ufnGetSalesOrderStatusText function.  
    --The function requires a value for one parameter, @Status.   
    EXEC @ret = dbo.ufnGetSalesOrderStatusText @Status= 5;   
    --Returns the result in the message tab.  
    PRINT @ret;  
    ```  
  
 <span data-ttu-id="7e3ad-127">有关详细信息，请参阅 [EXECUTE (Transact-SQL)](/sql/t-sql/language-elements/execute-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7e3ad-127">For more information, see [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).</span></span>  
  
  
