---
title: 查询和视图设计器如何表示 (Visual Database Tools) 的联接 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL pane [Visual Database Tools]
- joins [SQL Server], Query and View Designer
- Diagram pane [Visual Database Tools]
ms.assetid: 20a99dcb-83bd-4aa6-9139-92e2e5ba4887
author: stevestein
ms.author: sstein
ms.openlocfilehash: 55fdea533436f9fa7c2a902667b3166085c27e99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587677"
---
# <a name="how-the-query-and-view-designer-represents-joins-visual-database-tools"></a><span data-ttu-id="b4af9-102">查询和视图设计器如何表示联接 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b4af9-102">How the Query and View Designer Represents Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="b4af9-103">如果对表进行了联接， [查询和视图设计器](visual-database-tools.md) 将在[“关系图”](diagram-pane-visual-database-tools.md) 窗格中以图形方式表示联接，并在 [SQL 窗格](sql-pane-visual-database-tools.md)中使用 SQL 语法表示联接。</span><span class="sxs-lookup"><span data-stu-id="b4af9-103">If tables are joined, the [Query and View Designer](visual-database-tools.md) represents the join graphically in the [Diagram pane](diagram-pane-visual-database-tools.md) and by using SQL syntax in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
## <a name="diagram-pane"></a><span data-ttu-id="b4af9-104">“关系图”窗格</span><span class="sxs-lookup"><span data-stu-id="b4af9-104">Diagram Pane</span></span>  
 <span data-ttu-id="b4af9-105">在“关系图”窗格中，查询和视图设计器在联接所涉及的数据列之间显示一条联接线。</span><span class="sxs-lookup"><span data-stu-id="b4af9-105">In the Diagram pane the Query and View Designer displays a join line between the data columns involved in the join.</span></span> <span data-ttu-id="b4af9-106">查询和视图设计器为每个联接条件显示一条联接线。</span><span class="sxs-lookup"><span data-stu-id="b4af9-106">The Query and View Designer displays one join line for each join condition.</span></span> <span data-ttu-id="b4af9-107">例如，下图阐释两个联接的表之间的联接线：</span><span class="sxs-lookup"><span data-stu-id="b4af9-107">For example, the following illustration shows a join line between two tables that are joined:</span></span>  
  
 <span data-ttu-id="b4af9-108">![联接线显示两个表之间的关系](../../database-engine/media//dv3wbig.gif "联接线显示两个表之间的关系")</span><span class="sxs-lookup"><span data-stu-id="b4af9-108">![Join line shows relationship between two tables](../../database-engine/media//dv3wbig.gif "Join line shows relationship between two tables")</span></span>  
  
 <span data-ttu-id="b4af9-109">如果用多个联接条件联接表，则查询和视图设计器将显示多条联接线，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="b4af9-109">If tables are joined using more than one join condition, the Query and View Designer displays multiple join lines, as in the following example:</span></span>  
  
 <span data-ttu-id="b4af9-110">![使用多个联接条件联接的表](../../database-engine/media//dv3w9n1.gif "使用多个联接条件联接的表")</span><span class="sxs-lookup"><span data-stu-id="b4af9-110">![Tables joined using more than one join condition](../../database-engine/media//dv3w9n1.gif "Tables joined using more than one join condition")</span></span>  
  
 <span data-ttu-id="b4af9-111">如果没有显示联接的数据列（例如，表示表或表结构对象的矩形已最小化，或者联接涉及表达式），则查询和视图设计器会将联接线放到表示表或表结构对象的矩形的标题栏中。</span><span class="sxs-lookup"><span data-stu-id="b4af9-111">If the joined data columns are not displayed (for example, the rectangle representing the table or table-structured object is minimized or the join involves an expression), the Query and View Designer places the join line at the title bar of the rectangle representing the table or table-structured object.</span></span>  
  
 <span data-ttu-id="b4af9-112">联接线中间的图标形状指示表或表结构对象的联接方式。</span><span class="sxs-lookup"><span data-stu-id="b4af9-112">The shape of the icon in the middle of the join line indicates how the tables or table-structured objects are joined.</span></span> <span data-ttu-id="b4af9-113">如果联接子句使用等号 (=) 以外的运算符，则该运算符将出现在联接线图标中。</span><span class="sxs-lookup"><span data-stu-id="b4af9-113">If the join clause uses an operator other than equal (=), the operator appears in the join line icon.</span></span> <span data-ttu-id="b4af9-114">下表列出了在联接线上显示的图标。</span><span class="sxs-lookup"><span data-stu-id="b4af9-114">The following table lists the icons that appear in the join line.</span></span>  
  
|<span data-ttu-id="b4af9-115">**联接线图标**</span><span class="sxs-lookup"><span data-stu-id="b4af9-115">**Join line icon**</span></span>|<span data-ttu-id="b4af9-116">**说明**</span><span class="sxs-lookup"><span data-stu-id="b4af9-116">**Description**</span></span>|  
|------------------------|---------------------|  
|<span data-ttu-id="b4af9-117">![Visual Database Tools 图标](../../database-engine/media//dv3wbih.gif "Visual Database Tools 图标")</span><span class="sxs-lookup"><span data-stu-id="b4af9-117">![Visual Database Tools icon](../../database-engine/media//dv3wbih.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="b4af9-118">内部联接（用等号创建）。</span><span class="sxs-lookup"><span data-stu-id="b4af9-118">Inner join (created using an equal sign).</span></span>|  
|<span data-ttu-id="b4af9-119">![Visual Database Tools 图标](../../database-engine/media//dv3wbii.gif "Visual Database Tools 图标")</span><span class="sxs-lookup"><span data-stu-id="b4af9-119">![Visual Database Tools icon](../../database-engine/media//dv3wbii.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="b4af9-120">基于“大于”运算符的内部联接。</span><span class="sxs-lookup"><span data-stu-id="b4af9-120">Inner join based on the "greater than" operator.</span></span>|  
|<span data-ttu-id="b4af9-121">![Visual Database Tools 图标](../../database-engine/media//dv3wbij.gif "Visual Database Tools 图标")</span><span class="sxs-lookup"><span data-stu-id="b4af9-121">![Visual Database Tools icon](../../database-engine/media//dv3wbij.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="b4af9-122">外部联接，其中包括左侧表示的表中的所有行，即使它们在相关表中没有匹配行。</span><span class="sxs-lookup"><span data-stu-id="b4af9-122">Outer join in which all rows from the table represented on the left will be included, even if they do not have matches in the related table.</span></span>|  
|<span data-ttu-id="b4af9-123">![Visual Database Tools 图标](../../database-engine/media//dv3wbik.gif "Visual Database Tools 图标")</span><span class="sxs-lookup"><span data-stu-id="b4af9-123">![Visual Database Tools icon](../../database-engine/media//dv3wbik.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="b4af9-124">外部联接，其中包括右侧表示的表中的所有行，即使它们在相关表中没有匹配行。</span><span class="sxs-lookup"><span data-stu-id="b4af9-124">Outer join in which all rows from the table represented on the right will be included, even if they do not have matches in the related table.</span></span>|  
|<span data-ttu-id="b4af9-125">![Visual Database Tools 图标](../../database-engine/media//dv3wbil.gif "Visual Database Tools 图标")</span><span class="sxs-lookup"><span data-stu-id="b4af9-125">![Visual Database Tools icon](../../database-engine/media//dv3wbil.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="b4af9-126">完全外部联接，其中包括两个表中的所有行，即使它们在相关表中没有匹配行。</span><span class="sxs-lookup"><span data-stu-id="b4af9-126">Full outer join in which all rows from both tables will be included, even if they do not have matches in the related table.</span></span>|  
  
 <span data-ttu-id="b4af9-127">联接线末端的符号指示联接类型。</span><span class="sxs-lookup"><span data-stu-id="b4af9-127">The symbols on the ends of the join line indicate the type of join.</span></span> <span data-ttu-id="b4af9-128">下表列出联接类型和在联接线末端显示的图标。</span><span class="sxs-lookup"><span data-stu-id="b4af9-128">The following table lists the types of joins and the icons displayed on the ends of the join line.</span></span>  
  
|<span data-ttu-id="b4af9-129">**联接线末端的图标**</span><span class="sxs-lookup"><span data-stu-id="b4af9-129">**Icon on ends of join line**</span></span>|<span data-ttu-id="b4af9-130">**联接类型**</span><span class="sxs-lookup"><span data-stu-id="b4af9-130">**Type of join**</span></span>|  
|-----------------------------------|----------------------|  
|<span data-ttu-id="b4af9-131">![Visual Database Tools 图标](../../database-engine/media//dv3wbim.gif "Visual Database Tools 图标")</span><span class="sxs-lookup"><span data-stu-id="b4af9-131">![Visual Database Tools icon](../../database-engine/media//dv3wbim.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="b4af9-132">一对一联接。</span><span class="sxs-lookup"><span data-stu-id="b4af9-132">One-to-one join.</span></span>|  
|<span data-ttu-id="b4af9-133">![Visual Database Tools 图标](../../database-engine/media//dv3wbin.gif "Visual Database Tools 图标")</span><span class="sxs-lookup"><span data-stu-id="b4af9-133">![Visual Database Tools icon](../../database-engine/media//dv3wbin.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="b4af9-134">一对多联接。</span><span class="sxs-lookup"><span data-stu-id="b4af9-134">One-to-many join.</span></span>|  
|<span data-ttu-id="b4af9-135">![Visual Database Tools 图标](../../database-engine/media//dv3wbio.gif "Visual Database Tools 图标")</span><span class="sxs-lookup"><span data-stu-id="b4af9-135">![Visual Database Tools icon](../../database-engine/media//dv3wbio.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="b4af9-136">查询和视图设计器无法确定联接类型。</span><span class="sxs-lookup"><span data-stu-id="b4af9-136">Query and View Designer cannot determine the join type.</span></span> <span data-ttu-id="b4af9-137">这种情况最常发生在手动创建联接时。</span><span class="sxs-lookup"><span data-stu-id="b4af9-137">This situation occurs most often when you have created a join manually.</span></span>|  
  
## <a name="sql-pane"></a><span data-ttu-id="b4af9-138">SQL 窗格</span><span class="sxs-lookup"><span data-stu-id="b4af9-138">SQL Pane</span></span>  
 <span data-ttu-id="b4af9-139">在 SQL 语句中，可以采用许多方式表达联接。</span><span class="sxs-lookup"><span data-stu-id="b4af9-139">A join can be expressed in a number of ways in an SQL statement.</span></span> <span data-ttu-id="b4af9-140">确切的语法取决于所使用的数据库以及定义联接的方式。</span><span class="sxs-lookup"><span data-stu-id="b4af9-140">The exact syntax depends on the database you are using and on how you have defined the join.</span></span>  
  
 <span data-ttu-id="b4af9-141">联接表的语法选项包括：</span><span class="sxs-lookup"><span data-stu-id="b4af9-141">Syntax options for joining tables include:</span></span>  
  
-   <span data-ttu-id="b4af9-142">**FROM 子句的 JOIN 限定符**。</span><span class="sxs-lookup"><span data-stu-id="b4af9-142">**JOIN qualifier for the FROM clause**.</span></span>   <span data-ttu-id="b4af9-143">关键字 INNER 和 OUTER 指定联接类型。</span><span class="sxs-lookup"><span data-stu-id="b4af9-143">The keywords INNER and OUTER specify the join type.</span></span> <span data-ttu-id="b4af9-144">此语法是 ANSI 92 SQL 的标准语法。</span><span class="sxs-lookup"><span data-stu-id="b4af9-144">This syntax is standard for ANSI 92 SQL.</span></span>  
  
     <span data-ttu-id="b4af9-145">例如，如果基于每个表中的 `publishers` 列联接 `pub_info` 和 `pub_id` 表，所得到的 SQL 语句可能类似于以下形式：</span><span class="sxs-lookup"><span data-stu-id="b4af9-145">For example, if you join the `publishers` and `pub_info` tables based on the `pub_id` column in each table, the resulting SQL statement might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM publishers INNER JOIN pub_info ON  
       publishers.pub_id = pub_info.pub_id  
    ```  
  
     <span data-ttu-id="b4af9-146">如果创建外部联接，将显示关键字 LEFT OUTER 或 RIGHT OUTER 来代替关键字 INNER。</span><span class="sxs-lookup"><span data-stu-id="b4af9-146">If you create an outer join, the words LEFT OUTER or RIGHT OUTER appear in place of the word INNER.</span></span>  
  
-   <span data-ttu-id="b4af9-147">**WHERE 子句比较两个表中的列**。</span><span class="sxs-lookup"><span data-stu-id="b4af9-147">**WHERE clause compares columns in both tables**.</span></span>   <span data-ttu-id="b4af9-148">如果数据库不支持 JOIN 语法（或用户自己输入该语法），将显示 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="b4af9-148">A WHERE clause appears if the database does not support the JOIN syntax (or if you entered it yourself).</span></span> <span data-ttu-id="b4af9-149">如果联接是在 WHERE 子句中创建的，则两个表名都出现在 FROM 子句中。</span><span class="sxs-lookup"><span data-stu-id="b4af9-149">If the join is created in the WHERE clause, both table names appear in the FROM clause.</span></span>  
  
     <span data-ttu-id="b4af9-150">例如，下面的语句联接 `publishers` 和 `pub_info` 表。</span><span class="sxs-lookup"><span data-stu-id="b4af9-150">For example, the following statement joins the `publishers` and `pub_info` tables.</span></span>  
  
    ```  
    SELECT *  
    FROM publishers, pub_info  
    WHERE publishers.pub_id = pub_info.pub_id  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b4af9-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4af9-151">See Also</span></span>  
 <span data-ttu-id="b4af9-152">[利用联接查询 &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b4af9-152">[Query with Joins &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="b4af9-153">“联接”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b4af9-153">Join Dialog Box &#40;Visual Database Tools&#41;</span></span>](join-dialog-box-visual-database-tools.md)  
  
  
