---
title: MSSQLSERVER_137 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 137 (Database Engine error)
ms.assetid: 47fb4212-2165-4fec-bc41-6d548465d7be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e0142cd53006609e9274972e4f5964132f5982c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589664"
---
# <a name="mssqlserver_137"></a><span data-ttu-id="cff32-102">MSSQLSERVER_137</span><span class="sxs-lookup"><span data-stu-id="cff32-102">MSSQLSERVER_137</span></span>
    
## <a name="details"></a><span data-ttu-id="cff32-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="cff32-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cff32-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="cff32-104">Product Name</span></span>|<span data-ttu-id="cff32-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cff32-105">SQL Server</span></span>|  
|<span data-ttu-id="cff32-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="cff32-106">Event ID</span></span>|<span data-ttu-id="cff32-107">137</span><span class="sxs-lookup"><span data-stu-id="cff32-107">137</span></span>|  
|<span data-ttu-id="cff32-108">事件源</span><span class="sxs-lookup"><span data-stu-id="cff32-108">Event Source</span></span>|<span data-ttu-id="cff32-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cff32-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cff32-110">组件</span><span class="sxs-lookup"><span data-stu-id="cff32-110">Component</span></span>|<span data-ttu-id="cff32-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cff32-111">SQLEngine</span></span>|  
|<span data-ttu-id="cff32-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="cff32-112">Symbolic Name</span></span>|<span data-ttu-id="cff32-113">P_SCALAR_VAR_NOTFOUND</span><span class="sxs-lookup"><span data-stu-id="cff32-113">P_SCALAR_VAR_NOTFOUND</span></span>|  
|<span data-ttu-id="cff32-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="cff32-114">Message Text</span></span>|<span data-ttu-id="cff32-115">必须声明标量变量 "%.\*ls"。</span><span class="sxs-lookup"><span data-stu-id="cff32-115">Must declare the scalar variable "%.\*ls".</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cff32-116">说明</span><span class="sxs-lookup"><span data-stu-id="cff32-116">Explanation</span></span>  
 <span data-ttu-id="cff32-117">如果未首先声明某个变量就在 SQL 脚本中使用它，则会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="cff32-117">This error occurs when a variable is used in a SQL script without first declaring the variable.</span></span> <span data-ttu-id="cff32-118">下面的示例对 SET 和 SELECT 语句都返回错误137，因为未 **@mycol** 声明。</span><span class="sxs-lookup"><span data-stu-id="cff32-118">The following example returns error 137 for both the SET and SELECT statements because **@mycol** is not declared.</span></span>  
  
 <span data-ttu-id="cff32-119">SET @mycol = 'ContactName';</span><span class="sxs-lookup"><span data-stu-id="cff32-119">SET @mycol = 'ContactName';</span></span>  
  
 <span data-ttu-id="cff32-120">SELECT @mycol;</span><span class="sxs-lookup"><span data-stu-id="cff32-120">SELECT @mycol;</span></span>  
  
 <span data-ttu-id="cff32-121">之所以发生此错误，一个更为复杂的原因就是使用在 EXECUTE 语句外部声明的变量。</span><span class="sxs-lookup"><span data-stu-id="cff32-121">One of the more complicated causes of this error includes the use of a variable that is declared outside the EXECUTE statement.</span></span> <span data-ttu-id="cff32-122">例如， **@mycol** select 语句中指定的变量是 select 语句的局部变量，因此它位于 EXECUTE 语句外部。</span><span class="sxs-lookup"><span data-stu-id="cff32-122">For example, the variable **@mycol** specified in the SELECT statement is local to the SELECT statement; thus it is outside the EXECUTE statement.</span></span>  
  
 <span data-ttu-id="cff32-123">USE AdventureWorks2012;</span><span class="sxs-lookup"><span data-stu-id="cff32-123">USE AdventureWorks2012;</span></span>  
  
 <span data-ttu-id="cff32-124">GO</span><span class="sxs-lookup"><span data-stu-id="cff32-124">GO</span></span>  
  
 <span data-ttu-id="cff32-125">DECLARE @mycol nvarchar(20);</span><span class="sxs-lookup"><span data-stu-id="cff32-125">DECLARE @mycol nvarchar(20);</span></span>  
  
 <span data-ttu-id="cff32-126">SET @mycol = 'Name';</span><span class="sxs-lookup"><span data-stu-id="cff32-126">SET @mycol = 'Name';</span></span>  
  
 <span data-ttu-id="cff32-127">EXECUTE ('SELECT @mycol FROM Production.Product;');</span><span class="sxs-lookup"><span data-stu-id="cff32-127">EXECUTE ('SELECT @mycol FROM Production.Product;');</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cff32-128">用户操作</span><span class="sxs-lookup"><span data-stu-id="cff32-128">User Action</span></span>  
 <span data-ttu-id="cff32-129">确认先声明 SQL 脚本中所使用的任何变量，然后再将其用在脚本中的其他位置。</span><span class="sxs-lookup"><span data-stu-id="cff32-129">Verify that any variables used in a SQL script are declared before being used elsewhere in the script.</span></span>  
  
 <span data-ttu-id="cff32-130">重新编写该脚本，以便不在 EXECUTE 语句中引用在其外部声明的变量。</span><span class="sxs-lookup"><span data-stu-id="cff32-130">Rewrite the script so that it does not reference variables in the EXECUTE statement that are declared outside of it.</span></span> <span data-ttu-id="cff32-131">例如：</span><span class="sxs-lookup"><span data-stu-id="cff32-131">For example:</span></span>  
  
 <span data-ttu-id="cff32-132">USE AdventureWorks2012;</span><span class="sxs-lookup"><span data-stu-id="cff32-132">USE AdventureWorks2012;</span></span>  
  
 <span data-ttu-id="cff32-133">GO</span><span class="sxs-lookup"><span data-stu-id="cff32-133">GO</span></span>  
  
 <span data-ttu-id="cff32-134">DECLARE @mycol nvarchar(20);</span><span class="sxs-lookup"><span data-stu-id="cff32-134">DECLARE @mycol nvarchar(20) ;</span></span>  
  
 <span data-ttu-id="cff32-135">SET @mycol = 'Name';</span><span class="sxs-lookup"><span data-stu-id="cff32-135">SET @mycol = 'Name';</span></span>  
  
 <span data-ttu-id="cff32-136">EXECUTE ('SELECT ' + @mycol + ' FROM Production.Product';) ;</span><span class="sxs-lookup"><span data-stu-id="cff32-136">EXECUTE ('SELECT ' + @mycol + ' FROM Production.Product';) ;</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff32-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cff32-137">See Also</span></span>  
 <span data-ttu-id="cff32-138">[EXECUTE (Transact-SQL)](/sql/t-sql/language-elements/execute-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cff32-138">[EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql) </span></span>  
 <span data-ttu-id="cff32-139">[SET 语句 (Transact-SQL)](/sql/t-sql/statements/set-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cff32-139">[SET Statements &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql) </span></span>  
 [<span data-ttu-id="cff32-140">DECLARE @local_variable (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cff32-140">DECLARE @local_variable &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/declare-local-variable-transact-sql)  
  
  
