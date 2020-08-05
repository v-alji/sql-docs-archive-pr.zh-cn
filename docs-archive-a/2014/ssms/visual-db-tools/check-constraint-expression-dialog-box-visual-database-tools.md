---
title: “CHECK 约束表达式”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.checkconstraintexpression
ms.assetid: beb6ce43-3913-4d66-8826-8e885335b790
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38268d4e49a9c674c100bc22c0782e3e61477967
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576487"
---
# <a name="check-constraint-expression-dialog-box-visual-database-tools"></a><span data-ttu-id="94cad-102">“CHECK 约束表达式”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="94cad-102">Check Constraint Expression Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="94cad-103">向表或列附加 CHECK 约束时，必须包括 SQL 表达式。</span><span class="sxs-lookup"><span data-stu-id="94cad-103">When you attach a check constraint to a table or column, you must include an SQL expression.</span></span> <span data-ttu-id="94cad-104">在提供的框中键入 CHECK 约束表达式。</span><span class="sxs-lookup"><span data-stu-id="94cad-104">Type the check constraint expression in the box provided.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="94cad-105">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="94cad-105">UI element list</span></span>  
 <span data-ttu-id="94cad-106">表达式</span><span class="sxs-lookup"><span data-stu-id="94cad-106">Expression</span></span>  
 <span data-ttu-id="94cad-107">输入表达式</span><span class="sxs-lookup"><span data-stu-id="94cad-107">Enter the expression</span></span>  
  
 <span data-ttu-id="94cad-108">您可以创建简单的约束表达式，用简单条件检查数据；也可以使用布尔运算符创建复杂表达式，用若干个条件检查数据。</span><span class="sxs-lookup"><span data-stu-id="94cad-108">You can create a simple constraint expression to check data for a simple condition; or you can create a complex expression, using Boolean operators, to check data for several conditions.</span></span> <span data-ttu-id="94cad-109">例如，假设 Authors 表有一个需要 5 位数字字符串的邮政编码列。</span><span class="sxs-lookup"><span data-stu-id="94cad-109">For example, suppose the authors table has a zip column where a 5-digit character string is required.</span></span> <span data-ttu-id="94cad-110">下面的示例约束表达式可保证只允许 5 位的数字：</span><span class="sxs-lookup"><span data-stu-id="94cad-110">This sample constraint expression guarantees that only 5-digit numbers are allowed:</span></span>  
  
```  
zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
```  
  
 <span data-ttu-id="94cad-111">或者，假设 sales 表中包含一个名为 qty 的列，此列的值必须大于 0。</span><span class="sxs-lookup"><span data-stu-id="94cad-111">Or suppose the sales table has a column called qty which requires a value greater than 0.</span></span> <span data-ttu-id="94cad-112">此示例约束可保证只允许使用正值：</span><span class="sxs-lookup"><span data-stu-id="94cad-112">This sample constraint guarantees that only positive values are allowed:</span></span>  
  
```  
qty > 0  
```  
  
 <span data-ttu-id="94cad-113">或假设 Orders 表限制了所有信用卡订单可以接受的信用卡的类型。</span><span class="sxs-lookup"><span data-stu-id="94cad-113">Or suppose the orders table limits the type of credit cards accepted for all credit card orders.</span></span> <span data-ttu-id="94cad-114">下面的示例约束可保证在出现信用卡订单的情况下，只接受 Visa、MasterCard 或 American Express：</span><span class="sxs-lookup"><span data-stu-id="94cad-114">This sample constraint guarantees that if the order is placed on a credit card, then only Visa, MasterCard, or American Express is accepted:</span></span>  
  
```  
NOT (payment_method = 'credit card') OR  
   (card_type IN ('VISA', 'MASTERCARD', 'AMERICAN EXPRESS'))  
```  
  
## <a name="to-define-a-constraint-expression"></a><span data-ttu-id="94cad-115">定义约束表达式</span><span class="sxs-lookup"><span data-stu-id="94cad-115">To define a constraint expression</span></span>  
 <span data-ttu-id="94cad-116">在属性页的“检查约束”选项卡中，使用以下语法在“约束表达式”框中键入表达式：</span><span class="sxs-lookup"><span data-stu-id="94cad-116">In the Check Constraints tab of the property pages, type an expression in the Constraint expression box using the following syntax:</span></span>  
  
 `{constant | column_name | function | (subquery)}`  
  
 `[{operator | AND | OR | NOT}`  
  
 `{constant | column_name | function | (subquery)}...]`  
  
 <span data-ttu-id="94cad-117">SQL 语法由下列参数组成：</span><span class="sxs-lookup"><span data-stu-id="94cad-117">The SQL syntax is made up of the following parameters:</span></span>  
  
|<span data-ttu-id="94cad-118">参数</span><span class="sxs-lookup"><span data-stu-id="94cad-118">Parameter</span></span>|<span data-ttu-id="94cad-119">说明</span><span class="sxs-lookup"><span data-stu-id="94cad-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94cad-120">常量</span><span class="sxs-lookup"><span data-stu-id="94cad-120">constant</span></span>|<span data-ttu-id="94cad-121">一个如数值数据或字符数据之类的文本值。</span><span class="sxs-lookup"><span data-stu-id="94cad-121">A literal value, such as numeric or character data.</span></span> <span data-ttu-id="94cad-122">字符数据必须用单引号 (') 括起来。</span><span class="sxs-lookup"><span data-stu-id="94cad-122">Character data must be enclosed within single quotation marks (').</span></span>|  
|<span data-ttu-id="94cad-123">column_name</span><span class="sxs-lookup"><span data-stu-id="94cad-123">column_name</span></span>|<span data-ttu-id="94cad-124">指定列。</span><span class="sxs-lookup"><span data-stu-id="94cad-124">Specifies a column.</span></span>|  
|<span data-ttu-id="94cad-125">函数</span><span class="sxs-lookup"><span data-stu-id="94cad-125">function</span></span>|<span data-ttu-id="94cad-126">内置函数。</span><span class="sxs-lookup"><span data-stu-id="94cad-126">A built-in function.</span></span>|  
|<span data-ttu-id="94cad-127">运算符后的表达式</span><span class="sxs-lookup"><span data-stu-id="94cad-127">operator</span></span>|<span data-ttu-id="94cad-128">算术运算符、位运算符、比较运算符或字符串运算符。</span><span class="sxs-lookup"><span data-stu-id="94cad-128">Arithmetic, bitwise, comparison, or string operators.</span></span>|  
|<span data-ttu-id="94cad-129">和</span><span class="sxs-lookup"><span data-stu-id="94cad-129">AND</span></span>|<span data-ttu-id="94cad-130">在布尔表达式中使用，用来连接两个表达式。</span><span class="sxs-lookup"><span data-stu-id="94cad-130">Use in Boolean expressions to connect two expressions.</span></span> <span data-ttu-id="94cad-131">当两个表达式都为 True 时返回结果。</span><span class="sxs-lookup"><span data-stu-id="94cad-131">Results are returned when both expressions are true.</span></span><br /><br /> <span data-ttu-id="94cad-132">当在一个语句中同时使用 AND 和 OR 时，首先处理 AND。</span><span class="sxs-lookup"><span data-stu-id="94cad-132">When AND and OR are both used in a statement, AND is processed first.</span></span> <span data-ttu-id="94cad-133">可以使用括号更改执行顺序。</span><span class="sxs-lookup"><span data-stu-id="94cad-133">You can change the order of execution by using parentheses.</span></span>|  
|<span data-ttu-id="94cad-134">或</span><span class="sxs-lookup"><span data-stu-id="94cad-134">OR</span></span>|<span data-ttu-id="94cad-135">在布尔表达式中使用，用来连接两个或多个条件。</span><span class="sxs-lookup"><span data-stu-id="94cad-135">Use in Boolean expressions to connect two or more conditions.</span></span> <span data-ttu-id="94cad-136">当任何一个条件为 True 时返回结果。</span><span class="sxs-lookup"><span data-stu-id="94cad-136">Results are returned when either condition is true.</span></span><br /><br /> <span data-ttu-id="94cad-137">当在一个语句中同时使用 AND 和 OR 时，在计算 AND 之后再计算 OR。</span><span class="sxs-lookup"><span data-stu-id="94cad-137">When AND and OR are both used in a statement, OR is evaluated after AND.</span></span> <span data-ttu-id="94cad-138">可以使用括号更改执行顺序。</span><span class="sxs-lookup"><span data-stu-id="94cad-138">You can change the order of execution by using parentheses.</span></span>|  
|<span data-ttu-id="94cad-139">NOT</span><span class="sxs-lookup"><span data-stu-id="94cad-139">NOT</span></span>|<span data-ttu-id="94cad-140">对任何布尔表达式（可包含如 LIKE、NULL、BETWEEN、IN 和 EXISTS 之类的关键字）求反。</span><span class="sxs-lookup"><span data-stu-id="94cad-140">Negates any Boolean expression (which can include keywords, such as LIKE, NULL, BETWEEN, IN, and EXISTS).</span></span><br /><br /> <span data-ttu-id="94cad-141">当在一个语句中使用多个逻辑运算符时，首先处理 NOT。</span><span class="sxs-lookup"><span data-stu-id="94cad-141">When more than one logical operator is used in a statement, NOT is processed first.</span></span> <span data-ttu-id="94cad-142">可以使用括号更改执行顺序。</span><span class="sxs-lookup"><span data-stu-id="94cad-142">You can change the order of execution by using parentheses.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94cad-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94cad-143">See Also</span></span>  
 <span data-ttu-id="94cad-144">[Unique 约束和 Check 约束](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="94cad-144">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="94cad-145">创建唯一约束</span><span class="sxs-lookup"><span data-stu-id="94cad-145">Create Unique Constraints</span></span>](../../relational-databases/tables/create-unique-constraints.md)  
  
  
