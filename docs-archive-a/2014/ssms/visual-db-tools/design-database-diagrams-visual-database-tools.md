---
title: 设计数据库关系图 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65536
- vdt.DatabaseDesigner
helpviewer_keywords:
- Database Diagram Designer
- Visual Database Tools [SQL Server], database diagrams
- database diagrams [SQL Server], designing
- diagrams [SQL Server], designing
ms.assetid: 6d2c14e1-3d73-4d10-ae5b-7f2b5d6c4ea8
author: stevestein
ms.author: sstein
ms.openlocfilehash: bb4cbc518b6878ed8fb6e9f7d5d2d00803ab4d62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688416"
---
# <a name="design-database-diagrams-visual-database-tools"></a><span data-ttu-id="73fb7-102">设计数据库关系图 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="73fb7-102">Design Database Diagrams (Visual Database Tools)</span></span>
  <span data-ttu-id="73fb7-103">数据库设计器是一种可视化工具，它允许您对所连接的数据库进行设计和可视化处理。</span><span class="sxs-lookup"><span data-stu-id="73fb7-103">The Database Designer is a visual tool that allows you to design and visualize a database to which you are connected.</span></span> <span data-ttu-id="73fb7-104">设计数据库时，您可以使用数据库设计器创建、编辑或删除表、列、键、索引、关系和约束。</span><span class="sxs-lookup"><span data-stu-id="73fb7-104">When designing a database, you can use Database Designer to create, edit, or delete tables, columns, keys, indexes, relationships, and constraints.</span></span> <span data-ttu-id="73fb7-105">为使数据库可视化，您可创建一个或多个关系图，以显示数据库中的部分或全部表、列、键和关系。</span><span class="sxs-lookup"><span data-stu-id="73fb7-105">To visualize a database, you can create one or more diagrams illustrating some or all of the tables, columns, keys, and relationships in it.</span></span>  
  
 <span data-ttu-id="73fb7-106">![阐释表关系的数据库关系图](../../database-engine/media//dv3w7c1.gif "阐释表关系的数据库关系图")</span><span class="sxs-lookup"><span data-stu-id="73fb7-106">![Database diagram illustrating table relationships](../../database-engine/media//dv3w7c1.gif "Database diagram illustrating table relationships")</span></span>  
  
 <span data-ttu-id="73fb7-107">对于任何数据库，您都可以创建任意数目的数据库关系图；每个数据库表都可以出现在任意数目的关系图中。</span><span class="sxs-lookup"><span data-stu-id="73fb7-107">For any database, you can create as many database diagrams as you like; each database table can appear on any number of diagrams.</span></span> <span data-ttu-id="73fb7-108">这样，便可以创建不同的关系图使数据库的不同部分可视化，或强调设计的不同方面。</span><span class="sxs-lookup"><span data-stu-id="73fb7-108">Thus, you can create different diagrams to visualize different portions of the database, or to accentuate different aspects of the design.</span></span> <span data-ttu-id="73fb7-109">例如，可以创建一个大型关系图来显示所有表和列，并创建一个较小的关系图来显示所有表但不显示列。</span><span class="sxs-lookup"><span data-stu-id="73fb7-109">For example, you can create a large diagram showing all tables and columns, and you can create a smaller diagram showing all tables without showing the columns.</span></span>  
  
 <span data-ttu-id="73fb7-110">所创建的每个数据库关系图都存储在关联数据库中。</span><span class="sxs-lookup"><span data-stu-id="73fb7-110">Each database diagram you create is stored in the associated database.</span></span>  
  
## <a name="tables-and-columns-in-a-database-diagram"></a><span data-ttu-id="73fb7-111">数据库关系图中的表和列</span><span class="sxs-lookup"><span data-stu-id="73fb7-111">Tables and Columns in a Database Diagram</span></span>  
 <span data-ttu-id="73fb7-112">在数据库关系图中，每个表都可以带有三种不同的功能：标题栏、行选择器和一组属性列。</span><span class="sxs-lookup"><span data-stu-id="73fb7-112">Within a database diagram, each table can appear with three distinct features: a title bar, a row selector, and a set of property columns.</span></span>  
  
 <span data-ttu-id="73fb7-113">**标题栏** 标题栏显示表的名称</span><span class="sxs-lookup"><span data-stu-id="73fb7-113">**Title Bar** The title bar shows the name of the table</span></span>  
  
 <span data-ttu-id="73fb7-114">如果修改了某个表，但尚未保存该表，则表名末尾将显示一个星号 (\*)，表示未保存更改。</span><span class="sxs-lookup"><span data-stu-id="73fb7-114">If you have modified a table and have not yet saved it, an asterisk (\*) appears at the end of the table name to indicate unsaved changes.</span></span> <span data-ttu-id="73fb7-115">有关保存修改后的表和关系图的详细信息，请参阅 [使用数据库关系图 (Visual Database Tools)](visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="73fb7-115">For information about saving modified tables and diagrams, see [Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md)</span></span>  
  
 <span data-ttu-id="73fb7-116">**行选择器** 可以通过单击行选择器来选择表中的数据库列。</span><span class="sxs-lookup"><span data-stu-id="73fb7-116">**Row Selector** You can click the row selector to select a database column in the table.</span></span> <span data-ttu-id="73fb7-117">如何该列是表的主键，则行选择器将显示一个键符号。</span><span class="sxs-lookup"><span data-stu-id="73fb7-117">The row selector displays a key symbol if the column is in the table's primary key.</span></span> <span data-ttu-id="73fb7-118">有关主键的信息，请参阅[primary 和 Foreign Key 约束](../../relational-databases/tables/primary-and-foreign-key-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="73fb7-118">For information about primary keys, see [Primary and Foreign Key Constraints](../../relational-databases/tables/primary-and-foreign-key-constraints.md).</span></span>  
  
 <span data-ttu-id="73fb7-119">**属性列** 属性列组仅在表的某些视图中可见。</span><span class="sxs-lookup"><span data-stu-id="73fb7-119">**Property Columns** The set of property columns is visible only in the certain views of your table.</span></span> <span data-ttu-id="73fb7-120">您可以在五个不同视图中的任何一个视图中查看表，以帮助您管理关系图的大小和布局。</span><span class="sxs-lookup"><span data-stu-id="73fb7-120">You can view a table in any of five different views to help you manage the size and layout of your diagram.</span></span>  
  
 <span data-ttu-id="73fb7-121">有关表视图的详细信息，请参阅[自定义关系图中显示的信息量 (Visual Database Tools)](customize-the-amount-of-information-displayed-in-diagrams-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="73fb7-121">For more information about table views, see [Customize the Amount of Information Displayed in Diagrams &#40;Visual Database Tools&#41;](customize-the-amount-of-information-displayed-in-diagrams-visual-database-tools.md).</span></span>  
  
## <a name="relationships-in-a-database-diagram"></a><span data-ttu-id="73fb7-122">数据库关系图中的关系</span><span class="sxs-lookup"><span data-stu-id="73fb7-122">Relationships in a Database Diagram</span></span>  
 <span data-ttu-id="73fb7-123">在数据库关系图中，每个关系都可以带有三种不同的功能：终结点、线型和相关表。</span><span class="sxs-lookup"><span data-stu-id="73fb7-123">Within a database diagram, each relationship can appear with three distinct features: endpoints, a line style, and related tables.</span></span>  
  
 <span data-ttu-id="73fb7-124">**终结点** 线的终结点表示关系是一对一还是一对多关系。</span><span class="sxs-lookup"><span data-stu-id="73fb7-124">**Endpoints** The endpoints of the line indicate whether the relationship is one-to-one or one-to-many.</span></span> <span data-ttu-id="73fb7-125">如果某个关系在一个终结点处有键，在另一个终结点处有无穷符号，则该关系是一对多关系。</span><span class="sxs-lookup"><span data-stu-id="73fb7-125">If a relationship has a key at one endpoint and a figure-eight at the other, it is a one-to-many relationship.</span></span> <span data-ttu-id="73fb7-126">如果某个关系在每个终结点处都有键，则该关系是一对一关系。</span><span class="sxs-lookup"><span data-stu-id="73fb7-126">If a relationship has a key at each endpoint, it is a one-to-one relationship.</span></span>  
  
 <span data-ttu-id="73fb7-127">**线型** 线本身（非其终结点）表示当向外键表添加新数据时，数据库管理系统 (DBMS) 是否强制关系的引用完整性。</span><span class="sxs-lookup"><span data-stu-id="73fb7-127">**Line Style** The line itself (not its endpoints) indicates whether the Database Management System (DBMS) enforces referential integrity for the relationship when new data is added to the foreign-key table.</span></span> <span data-ttu-id="73fb7-128">如果为实线，则在外键表中添加或修改行时，DBMS 将强制关系的引用完整性。</span><span class="sxs-lookup"><span data-stu-id="73fb7-128">If the line appears solid, the DBMS enforces referential integrity for the relationship when rows are added or modified in the foreign-key table.</span></span> <span data-ttu-id="73fb7-129">如果为点线，则在外键表中添加或修改行时，DBMS 不强制关系的引用完整性。</span><span class="sxs-lookup"><span data-stu-id="73fb7-129">If the line appears dotted, the DBMS does not enforce referential integrity for the relationship when rows are added or modified in the foreign-key table.</span></span>  
  
 <span data-ttu-id="73fb7-130">**相关表** 关系线表示两个表之间存在外键关系。</span><span class="sxs-lookup"><span data-stu-id="73fb7-130">**Related Tables** The relationship line indicates that a foreign-key relationship exists between one table and another.</span></span> <span data-ttu-id="73fb7-131">对于一对多关系，外键表是靠近线的无穷符号的那个表。</span><span class="sxs-lookup"><span data-stu-id="73fb7-131">For a one-to-many relationship, the foreign-key table is the table near the line's figure-eight symbol.</span></span> <span data-ttu-id="73fb7-132">如果线的两个终结点连接到同一个表，则该关系是自反关系。</span><span class="sxs-lookup"><span data-stu-id="73fb7-132">If both endpoints of the line attach to the same table, the relationship is a reflexive relationship.</span></span> <span data-ttu-id="73fb7-133">有关详细信息，请参阅[绘制自反关系 (Visual Database Tools)](draw-reflexive-relationships-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="73fb7-133">For more information, see [Draw Reflexive Relationships &#40;Visual Database Tools&#41;](draw-reflexive-relationships-visual-database-tools.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="73fb7-134">本节内容</span><span class="sxs-lookup"><span data-stu-id="73fb7-134">In this Section</span></span>  
 [<span data-ttu-id="73fb7-135">了解数据库关系图所有权 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="73fb7-135">Understand Database Diagram Ownership &#40;Visual Database Tools&#41;</span></span>](understand-database-diagram-ownership-visual-database-tools.md)  
  
 [<span data-ttu-id="73fb7-136">在数据库关系图设计器中导航 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="73fb7-136">Navigate in Database Diagram Designer &#40;Visual Database Tools&#41;</span></span>](navigate-in-database-diagram-designer-visual-database-tools.md)  
  
 [<span data-ttu-id="73fb7-137">设置数据库关系图设计器 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="73fb7-137">Set Up Database Diagram Designer &#40;Visual Database Tools&#41;</span></span>](set-up-database-diagram-designer-visual-database-tools.md)  
  
 [<span data-ttu-id="73fb7-138">从以前的版本升级数据库关系图 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="73fb7-138">Upgrade Database Diagrams from Previous Editions &#40;Visual Database Tools&#41;</span></span>](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)  
  
 [<span data-ttu-id="73fb7-139">打开数据库关系图设计器 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="73fb7-139">Open Database Diagram Designer &#40;Visual Database Tools&#41;</span></span>](open-database-diagram-designer-visual-database-tools.md)  
  
## <a name="see-also"></a><span data-ttu-id="73fb7-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73fb7-140">See Also</span></span>  
 <span data-ttu-id="73fb7-141">[使用数据库关系图 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="73fb7-141">[Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="73fb7-142">[使用 Visual Database Tools &#40;数据库关系图中的表&#41;](work-with-tables-in-database-diagram-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="73fb7-142">[Work with Tables in Database Diagram &#40;Visual Database Tools&#41;](work-with-tables-in-database-diagram-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="73fb7-143">使用关系图布局 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="73fb7-143">Work with Diagram Layout &#40;Visual Database Tools&#41;</span></span>](work-with-diagram-layout-visual-database-tools.md)  
  
  
