---
title: 向关系图中添加表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting tables
- adding tables
ms.assetid: 5440fdf7-ac04-4325-9f32-181f4cd402e5
author: stevestein
ms.author: sstein
ms.openlocfilehash: fe5c1274ac390f4834bd8ac1088258061fc0406d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587134"
---
# <a name="add-tables-to-diagrams-visual-database-tools"></a><span data-ttu-id="7c985-102">向关系图中添加表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7c985-102">Add Tables to Diagrams (Visual Database Tools)</span></span>
  <span data-ttu-id="7c985-103">可以将表添加到数据库关系图中，以编辑其结构或使其与关系图中的其他表相关。</span><span class="sxs-lookup"><span data-stu-id="7c985-103">You can add a table to your database diagram to edit its structure or relate it to other tables in your diagram.</span></span> <span data-ttu-id="7c985-104">可以向关系图中添加现有的数据库表，或者插入尚未在数据库中定义的新表。</span><span class="sxs-lookup"><span data-stu-id="7c985-104">You can either add existing database tables to a diagram or insert a new table that has not yet been defined in the database.</span></span>  
  
### <a name="to-insert-a-new-table-into-a-diagram"></a><span data-ttu-id="7c985-105">向关系图中插入新表</span><span class="sxs-lookup"><span data-stu-id="7c985-105">To insert a new table into a diagram</span></span>  
  
1.  <span data-ttu-id="7c985-106">确保已连接到要在其中创建表的数据库。</span><span class="sxs-lookup"><span data-stu-id="7c985-106">Make sure you are connected to the database in which you want to create the table.</span></span>  
  
     <span data-ttu-id="7c985-107">若要在当前关系图中创建表，请单击工具栏上的“新建表”  按钮。</span><span class="sxs-lookup"><span data-stu-id="7c985-107">To create a table in your current diagram, click the **New Table** button on the toolbar.</span></span>  
  
     <span data-ttu-id="7c985-108">-或-</span><span class="sxs-lookup"><span data-stu-id="7c985-108">-or-</span></span>  
  
     <span data-ttu-id="7c985-109">在关系图中右键单击，然后选择“新建表”  。</span><span class="sxs-lookup"><span data-stu-id="7c985-109">Right-click in the diagram and select **New Table**.</span></span>  
  
2.  <span data-ttu-id="7c985-110">在“选择名称”  对话框中修改或接受系统分配的表名，然后选择“确定”  。</span><span class="sxs-lookup"><span data-stu-id="7c985-110">Modify or accept the system-assigned table name, in the **Choose Name** dialog box, and then choose **OK**.</span></span>  
  
     <span data-ttu-id="7c985-111">此时，将在关系图中以标准视图显示一个新表。</span><span class="sxs-lookup"><span data-stu-id="7c985-111">A new table appears in the diagram in Standard view.</span></span>  
  
3.  <span data-ttu-id="7c985-112">在新表的第一个单元格中，键入列名。</span><span class="sxs-lookup"><span data-stu-id="7c985-112">In the first cell of the new table, type a column name.</span></span> <span data-ttu-id="7c985-113">然后按 Tab 键移动到下一个单元格。</span><span class="sxs-lookup"><span data-stu-id="7c985-113">Then press the TAB key to move to the next cell.</span></span>  
  
4.  <span data-ttu-id="7c985-114">在“数据类型”  下，选择列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="7c985-114">Under **Data Type**, select a data type for the column.</span></span> <span data-ttu-id="7c985-115">每个列都必须具有名称和数据类型。</span><span class="sxs-lookup"><span data-stu-id="7c985-115">Each column must have a name and data type.</span></span>  
  
     <span data-ttu-id="7c985-116">您可以在表设计器中设置列的其他属性。</span><span class="sxs-lookup"><span data-stu-id="7c985-116">You can set the column's other properties in Table Designer.</span></span>  
  
5.  <span data-ttu-id="7c985-117">对于要添加到表中的每一列重复第 3 和第 4 步。</span><span class="sxs-lookup"><span data-stu-id="7c985-117">Repeat steps 3 and 4 for each column you want to add to the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7c985-118">在保存数据库关系图时，新表将添加到数据库中。</span><span class="sxs-lookup"><span data-stu-id="7c985-118">When you save your database diagram, the new table will be added to your database.</span></span>  
  
### <a name="to-add-an-existing-table-to-a-diagram"></a><span data-ttu-id="7c985-119">向关系图中添加现有的表</span><span class="sxs-lookup"><span data-stu-id="7c985-119">To add an existing table to a diagram</span></span>  
  
1.  <span data-ttu-id="7c985-120">确保已连接到要编辑其表的数据库。</span><span class="sxs-lookup"><span data-stu-id="7c985-120">Make sure you are connected to the database whose tables you want to edit.</span></span>  
  
2.  <span data-ttu-id="7c985-121">在“表”  文件夹中选择表。</span><span class="sxs-lookup"><span data-stu-id="7c985-121">Select a table in the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="7c985-122">将该表拖动到数据库关系图中。</span><span class="sxs-lookup"><span data-stu-id="7c985-122">Drag the table into your database diagram.</span></span>  
  
4.  <span data-ttu-id="7c985-123">释放鼠标按钮。</span><span class="sxs-lookup"><span data-stu-id="7c985-123">Release the mouse button.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7c985-124">如果选定的表与关系图中的其他表之间存在关系，则自动绘制关系线。</span><span class="sxs-lookup"><span data-stu-id="7c985-124">If relationships exist between the selected table and other tables in your diagram, relationship lines are automatically drawn.</span></span>  
  
### <a name="to-add-related-tables-to-a-diagram"></a><span data-ttu-id="7c985-125">向关系图中添加相关表</span><span class="sxs-lookup"><span data-stu-id="7c985-125">To add related tables to a diagram</span></span>  
  
1.  <span data-ttu-id="7c985-126">在数据库关系图中，选择一个或多个具有外键约束的表。</span><span class="sxs-lookup"><span data-stu-id="7c985-126">Select one or more tables with foreign key constraints in the database diagram.</span></span>  
  
2.  <span data-ttu-id="7c985-127">右键单击任何选定的表，再选择“添加相关表”  。</span><span class="sxs-lookup"><span data-stu-id="7c985-127">Right-click any of the selected tables and choose **Add Related Tables**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7c985-128">选定表的外键约束所引用的表以及引用具有外键约束的选定表的表都将添加到关系图中。</span><span class="sxs-lookup"><span data-stu-id="7c985-128">Both those tables referenced by a foreign key constraint from the selected table(s) and those referencing the selected table(s) with a foreign key constraint are added to the diagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c985-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7c985-129">See Also</span></span>  
 <span data-ttu-id="7c985-130">[使用数据库关系图 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="7c985-130">[Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="7c985-131">使用数据库关系图中的表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7c985-131">Work with Tables in Database Diagram &#40;Visual Database Tools&#41;</span></span>](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
