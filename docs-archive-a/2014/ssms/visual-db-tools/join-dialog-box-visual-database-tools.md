---
title: “联接”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.ppg.joinline
- vdtsql.chm:69638
ms.assetid: 0d9516bb-4ad3-4fcf-bb77-93474dea698f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7fbd2b61a080a681b5d15a4b69c466fae76e04e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682592"
---
# <a name="join-dialog-box-visual-database-tools"></a><span data-ttu-id="fa8fb-102">“联接”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="fa8fb-102">Join Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="fa8fb-103">使用此对话框可以指定用于对表进行联接的选项。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-103">Use this dialog box to specify options for joining tables.</span></span> <span data-ttu-id="fa8fb-104">若要访问此对话框，请在“设计”  窗格中选择联接线。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-104">To access this dialog, in the **Design** pane select a join line.</span></span> <span data-ttu-id="fa8fb-105">然后，在“属性”窗口中单击“联接条件和类型”，再单击属性右侧显示的省略号 (…)    。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-105">Then in the **Properties** window click **Join Condition And Type**, and click the ellipses **(...)** that appear to the right of the property.</span></span>  
  
 <span data-ttu-id="fa8fb-106">默认情况下，相关表使用内部联接进行联接，内部联接可基于联接列中包含匹配信息的行创建结果集。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-106">By default, related tables are joined using an inner join that creates a result set based on rows containing matching information in the join columns.</span></span> <span data-ttu-id="fa8fb-107">通过在“联接”  对话框中设置选项，可以指定基于不同运算符的联接，还可以指定外部联接。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-107">By setting options in the **Join** dialog box, you can specify a join based on a different operator, and you can specify an outer join.</span></span>  
  
 <span data-ttu-id="fa8fb-108">有关联接表的详细信息，请参阅[使用联接进行查询 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-108">For more information about joining tables, see [Query with Joins &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fa8fb-109">选项</span><span class="sxs-lookup"><span data-stu-id="fa8fb-109">Options</span></span>  
  
|<span data-ttu-id="fa8fb-110">**术语**</span><span class="sxs-lookup"><span data-stu-id="fa8fb-110">**Term**</span></span>|<span data-ttu-id="fa8fb-111">**定义**</span><span class="sxs-lookup"><span data-stu-id="fa8fb-111">**Definition**</span></span>|  
|--------------|--------------------|  
|<span data-ttu-id="fa8fb-112">**表**</span><span class="sxs-lookup"><span data-stu-id="fa8fb-112">**Table**</span></span>|<span data-ttu-id="fa8fb-113">联接中涉及的表或表值对象的名称。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-113">The names of the tables or table-valued objects involved in the join.</span></span> <span data-ttu-id="fa8fb-114">不能在此处更改表名（此信息仅作为信息显示）。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-114">You cannot change the names of the tables here - this information is displayed for information only.</span></span>|  
|<span data-ttu-id="fa8fb-115">**列**</span><span class="sxs-lookup"><span data-stu-id="fa8fb-115">**Column**</span></span>|<span data-ttu-id="fa8fb-116">用于联接表的列的名称。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-116">The names of the columns used for joining the tables.</span></span> <span data-ttu-id="fa8fb-117">运算符列表中的运算符指定了这些列中数据之间的关系。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-117">The operator in the operator list specifies the relationship between the data in the columns.</span></span> <span data-ttu-id="fa8fb-118">不能在此处更改列名（此信息仅作为信息显示）。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-118">You cannot change the names of the columns here - this information is displayed for information only.</span></span>|  
|<span data-ttu-id="fa8fb-119">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="fa8fb-119">**Operator**</span></span>|<span data-ttu-id="fa8fb-120">指定用于使联接列相关的运算符。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-120">Specify the operator used to relate the join columns.</span></span> <span data-ttu-id="fa8fb-121">若要指定等号 (=) 以外的运算符，请从列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-121">To specify an operator other than equal (=), select it from the list.</span></span> <span data-ttu-id="fa8fb-122">关闭该属性页后，您选择的运算符将显示在联接线的菱形图中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="fa8fb-122">When you close the property page, the operator you selected will appear in the diamond graphic of the join line, as in the following:</span></span><br /><br /> <span data-ttu-id="fa8fb-123">![Visual Database Tools 图标](../../database-engine/media//dv3wbii.gif "Visual Database Tools 图标")</span><span class="sxs-lookup"><span data-stu-id="fa8fb-123">![Visual Database Tools icon](../../database-engine/media//dv3wbii.gif "Visual Database Tools icon")</span></span>|  
|<span data-ttu-id="fa8fb-124">**所有行 \<table1>**</span><span class="sxs-lookup"><span data-stu-id="fa8fb-124">**All rows from \<table1>**</span></span>|<span data-ttu-id="fa8fb-125">指定即使右表中没有相应的匹配行，左表中的所有行也都显示在输出中。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-125">Specify that all the rows from the left table appear in the output, even if there are no corresponding matches in the right table.</span></span> <span data-ttu-id="fa8fb-126">右表中不包含匹配数据的列显示为空。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-126">Columns with no matching data in the right table appear as null.</span></span> <span data-ttu-id="fa8fb-127">选择此选项等效于在 SQL 语句中指定 LEFT OUTER JOIN。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-127">Choosing this option is equivalent to specifying LEFT OUTER JOIN in the SQL statement.</span></span>|  
|<span data-ttu-id="fa8fb-128">**所有行 \<table2>**</span><span class="sxs-lookup"><span data-stu-id="fa8fb-128">**All rows from \<table2>**</span></span>|<span data-ttu-id="fa8fb-129">指定即使左表中没有相应的匹配行，右表中的所有行也都显示在输出中。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-129">Specify that all the rows from the right table appear in the output, even if there are no corresponding matches in the left table.</span></span> <span data-ttu-id="fa8fb-130">左表中不包含匹配数据的列显示为空。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-130">Columns with no matching data in the left table appear as null.</span></span> <span data-ttu-id="fa8fb-131">选择此选项等效于在 SQL 语句中指定 RIGHT OUTER JOIN。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-131">Choosing this option is equivalent to specifying RIGHT OUTER JOIN in the SQL statement.</span></span>|  
  
 <span data-ttu-id="fa8fb-132">同时选择“\<table1> 中的所有行”和“\<table2> 中的所有行”等效于在 SQL 语句中指定 FULL OUTER JOIN。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-132">Selecting both All **rows from \<table1>** and **All rows from \<table2>** is equivalent to specifying FULL OUTER JOIN in the SQL statement.</span></span>  
  
 <span data-ttu-id="fa8fb-133">当选择创建外部联接的选项时，联接线中的菱形图会随之改变，以指示联接是左外部联接、右外部联接还是完全外部联接。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-133">When you select an option to create an outer join, the diamond graphic in the join line changes to indicate that the join is a left outer, right outer, or full outer join.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa8fb-134">文中的“左”和“右”并不一定与表在“关系图”窗格中的位置相对应。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-134">The words "left" and "right" do not necessarily correspond to the position of tables in the Diagram pane.</span></span> <span data-ttu-id="fa8fb-135">“左”指的是其名称显示在 SQL 语句中 JOIN 关键字左侧的表，而“右”指的是其名称显示在 JOIN 关键字右侧的表。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-135">"Left" refers to the table whose name appears to the left of the keyword JOIN in the SQL statement, and "right" refers to the table whose name appears to the right of the JOIN keyword.</span></span> <span data-ttu-id="fa8fb-136">在“关系图”  窗格中移动表时不会更改表原有的“左”或“右”顺序。</span><span class="sxs-lookup"><span data-stu-id="fa8fb-136">If you move tables in the **Diagram** pane, you do not change which table is considered left or right.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa8fb-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa8fb-137">See Also</span></span>  
 <span data-ttu-id="fa8fb-138">[利用联接查询 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="fa8fb-138">[Query with Joins &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="fa8fb-139">设计查询和视图操作指南主题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="fa8fb-139">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
