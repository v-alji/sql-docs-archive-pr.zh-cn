---
title: 映射多对多关系 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- relationships [SQL Server], many-to-many
- junction tables [SQL Server]
- many-to-many relationships [SQL Server]
- mapping many-to-many relationships [SQL Server]
- database diagrams [SQL Server], relationships
ms.assetid: 2977cf92-98b5-48b2-b0fd-8fbc7040f2b4
author: stevestein
ms.author: sstein
ms.openlocfilehash: cbcbdbdf8d8371baa2a817e43b831535723be7ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590498"
---
# <a name="map-many-to-many-relationships-visual-database-tools"></a><span data-ttu-id="e3abc-102">映射多对多关系 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e3abc-102">Map Many-to-Many Relationships (Visual Database Tools)</span></span>
  <span data-ttu-id="e3abc-103">使用多对多关系，您可以将一个表中的每一行与另一个表中的多行相关，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="e3abc-103">Many-to-many relationships let you relate each row in one table to many rows in another table, and vice versa.</span></span> <span data-ttu-id="e3abc-104">例如，可以在 `authors` 表与 `titles` 表之间创建多对多关系，以将每位作者与其所有书籍相匹配并将每本书与其所有作者相匹配。</span><span class="sxs-lookup"><span data-stu-id="e3abc-104">For example, you could create a many-to-many relationship between the `authors` table and the `titles` table to match each author to all of his or her books and to match each book to all of its authors.</span></span> <span data-ttu-id="e3abc-105">从上述任何一个表创建一对多关系都会错误地表示每本书只能有一位作者或者每位作者只能编写一本书。</span><span class="sxs-lookup"><span data-stu-id="e3abc-105">Creating a one-to-many relationship from either table would incorrectly indicate that every book can have only one author, or that every author can write only one book.</span></span>  
  
 <span data-ttu-id="e3abc-106">表与表之间的多对多关系通过联接表存储在数据库中。</span><span class="sxs-lookup"><span data-stu-id="e3abc-106">Many-to-many relationships between tables are accommodated in databases by means of junction tables.</span></span> <span data-ttu-id="e3abc-107">联接表包含要相关的两个表的主键列。</span><span class="sxs-lookup"><span data-stu-id="e3abc-107">A junction table contains the primary key columns of the two tables you want to relate.</span></span> <span data-ttu-id="e3abc-108">然后，分别创建从每个表的主键列到联接表中的匹配列之间的关系。</span><span class="sxs-lookup"><span data-stu-id="e3abc-108">You then create a relationship from the primary key columns of each of those two tables to the matching columns in the junction table.</span></span> <span data-ttu-id="e3abc-109">在 pubs 数据库中， `titleauthor` 表为联接表。</span><span class="sxs-lookup"><span data-stu-id="e3abc-109">In the pubs database, the `titleauthor` table is a junction table.</span></span>  
  
### <a name="to-create-a-many-to-many-relationship-between-tables"></a><span data-ttu-id="e3abc-110">在表与表之间创建多对多关系</span><span class="sxs-lookup"><span data-stu-id="e3abc-110">To create a many-to-many relationship between tables</span></span>  
  
1.  <span data-ttu-id="e3abc-111">在数据库关系图中，添加要在它们之间创建多对多关系的表。</span><span class="sxs-lookup"><span data-stu-id="e3abc-111">In your database diagram, add the tables that you want to create a many-to-many relationship between.</span></span>  
  
2.  <span data-ttu-id="e3abc-112">右键单击关系图，然后从快捷菜单中选择“新建表”  创建第三个表。</span><span class="sxs-lookup"><span data-stu-id="e3abc-112">Create a third table by right-clicking the diagram and choosing **New Table** from the shortcut menu.</span></span> <span data-ttu-id="e3abc-113">该表将成为联接表。</span><span class="sxs-lookup"><span data-stu-id="e3abc-113">This will become the junction table.</span></span>  
  
3.  <span data-ttu-id="e3abc-114">在“选择名称”  对话框中，更改系统分配的表名。</span><span class="sxs-lookup"><span data-stu-id="e3abc-114">In the **Choose Name** dialog box, change the system-assigned table name.</span></span> <span data-ttu-id="e3abc-115">例如，`titles` 表和 `authors` 表之间的联接表现在命名为 `titleauthors`。</span><span class="sxs-lookup"><span data-stu-id="e3abc-115">For example, the junction table between the `titles` table and the `authors` table is now named `titleauthors`.</span></span>  
  
4.  <span data-ttu-id="e3abc-116">将其他两个表中的主键列复制到联接表中。</span><span class="sxs-lookup"><span data-stu-id="e3abc-116">Copy the primary key columns from each of the other two tables to the junction table.</span></span> <span data-ttu-id="e3abc-117">与任何其他表一样，您可以向此表中添加其他列。</span><span class="sxs-lookup"><span data-stu-id="e3abc-117">You can add other columns to this table, just as you can to any other table.</span></span>  
  
5.  <span data-ttu-id="e3abc-118">在联接表中，将主键设置为包含其他两个表中的所有主键列。</span><span class="sxs-lookup"><span data-stu-id="e3abc-118">In the junction table, set the primary key to include all the primary key columns from the other two tables.</span></span> <span data-ttu-id="e3abc-119">有关详细信息，请参阅[Create Primary Keys](../../relational-databases/tables/create-primary-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="e3abc-119">For details, see [Create Primary Keys](../../relational-databases/tables/create-primary-keys.md).</span></span>  
  
6.  <span data-ttu-id="e3abc-120">分别定义每个主表与联接表之间的一对多关系。</span><span class="sxs-lookup"><span data-stu-id="e3abc-120">Define a one-to-many relationship between each of the two primary tables and the junction table.</span></span> <span data-ttu-id="e3abc-121">联接表应位于您所创建的这两个关系的“多”方。</span><span class="sxs-lookup"><span data-stu-id="e3abc-121">The junction table should be at the "many" side of both of the relationships you create.</span></span> <span data-ttu-id="e3abc-122">有关详细信息，请参阅[创建外键关系](../../relational-databases/tables/create-foreign-key-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="e3abc-122">For details, see [Create Foreign Key Relationships](../../relational-databases/tables/create-foreign-key-relationships.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e3abc-123">在数据库关系图中创建联接表并不会将数据从相关表插入联接表中。</span><span class="sxs-lookup"><span data-stu-id="e3abc-123">The creation of a junction table in a database diagram does not insert data from the related tables into the junction table.</span></span> <span data-ttu-id="e3abc-124">有关将数据插入表的信息，请参阅[创建插入结果查询 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e3abc-124">For information about inserting data into a table, see [Create Insert Results Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3abc-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3abc-125">See Also</span></span>  
 [<span data-ttu-id="e3abc-126">使用数据库关系图 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e3abc-126">Work with Database Diagrams &#40;Visual Database Tools&#41;</span></span>](work-with-database-diagrams-visual-database-tools.md)  
  
  
