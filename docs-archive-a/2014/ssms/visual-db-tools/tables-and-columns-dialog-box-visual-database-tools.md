---
title: “表和列”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.tablesandcolumns
ms.assetid: 8cf27be1-e66d-4735-a428-9ab4b33af4f5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28e0c52b74413a3a5a4122412c6028b34e974b09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589995"
---
# <a name="tables-and-columns-dialog-box-visual-database-tools"></a><span data-ttu-id="10125-102">“表和列”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="10125-102">Tables and Columns Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="10125-103">使用此对话框可以将一个表中的主键映射到另一个表中的外键。</span><span class="sxs-lookup"><span data-stu-id="10125-103">Use this dialog box to map a primary key in one table to a foreign key in another.</span></span> <span data-ttu-id="10125-104">若要访问此对话框，请在“表设计器”  菜单中，单击“关系”  。</span><span class="sxs-lookup"><span data-stu-id="10125-104">To access this dialog box, from the **Table Designer** menu, click **Relationships**.</span></span> <span data-ttu-id="10125-105">在“外键关系”对话框中，单击“表和列规范”字段，再单击属性右侧的省略号 (…)    。</span><span class="sxs-lookup"><span data-stu-id="10125-105">In the **Foreign Key Relationships** dialog box, click the **Tables and Columns Specification** field, and then click the ellipses **(...)** to the right of the property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10125-106">如果表是为复制发布的，则必须使用 Transact-SQL 语句 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理对象 (SMO) 对架构进行更改。</span><span class="sxs-lookup"><span data-stu-id="10125-106">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="10125-107">使用表设计器或数据库关系图设计器更改架构后，会尝试删除并重新创建表。</span><span class="sxs-lookup"><span data-stu-id="10125-107">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="10125-108">由于您不能删除已发布的对象，因此架构更改将失败。</span><span class="sxs-lookup"><span data-stu-id="10125-108">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="10125-109">选项</span><span class="sxs-lookup"><span data-stu-id="10125-109">Options</span></span>  
 <span data-ttu-id="10125-110">**关系名**</span><span class="sxs-lookup"><span data-stu-id="10125-110">**Relationship name**</span></span>  
 <span data-ttu-id="10125-111">显示关系的名称。</span><span class="sxs-lookup"><span data-stu-id="10125-111">Shows the name of the relationship.</span></span>  
  
 <span data-ttu-id="10125-112">**主键表**</span><span class="sxs-lookup"><span data-stu-id="10125-112">**Primary Key Table**</span></span>  
 <span data-ttu-id="10125-113">列出数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="10125-113">Lists the tables in the database.</span></span> <span data-ttu-id="10125-114">选择将处于关系主键方的表。</span><span class="sxs-lookup"><span data-stu-id="10125-114">Choose the table that will be on the primary-key side of the relationship.</span></span>  
  
 <span data-ttu-id="10125-115">**外键表**</span><span class="sxs-lookup"><span data-stu-id="10125-115">**Foreign Key Table**</span></span>  
 <span data-ttu-id="10125-116">显示处于关系外键方的表。</span><span class="sxs-lookup"><span data-stu-id="10125-116">Shows the table on the foreign key side of the relationship.</span></span> <span data-ttu-id="10125-117">这是表设计器中的当前所选表。</span><span class="sxs-lookup"><span data-stu-id="10125-117">This is the table currently selected in Table Designer.</span></span>  
  
 <span data-ttu-id="10125-118">**主键表下的网格**</span><span class="sxs-lookup"><span data-stu-id="10125-118">**Grid beneath Primary Key Table**</span></span>  
 <span data-ttu-id="10125-119">列出在“主键表”  列表中选定的表列。</span><span class="sxs-lookup"><span data-stu-id="10125-119">List the columns of the table selected in the **Primary Key Table** list.</span></span> <span data-ttu-id="10125-120">输入分配给该表的主键的列。</span><span class="sxs-lookup"><span data-stu-id="10125-120">Enter the columns contributing to that table's primary key.</span></span>  
  
 <span data-ttu-id="10125-121">**外键表下的网格**</span><span class="sxs-lookup"><span data-stu-id="10125-121">**Grid beneath Foreign Key Table**</span></span>  
 <span data-ttu-id="10125-122">列出在“外键表”  列表中选定的表列。</span><span class="sxs-lookup"><span data-stu-id="10125-122">List the columns of the table selected in the **Foreign Key Table** list.</span></span> <span data-ttu-id="10125-123">输入外键表中对应于主键列的外键列。</span><span class="sxs-lookup"><span data-stu-id="10125-123">Enter the foreign-key column of the foreign-key table that corresponds to the primary key column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10125-124">选作外键的列必须与其对应的主键列具有相同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="10125-124">The columns you choose for the foreign key must have the same data type of the primary columns they correspond to.</span></span> <span data-ttu-id="10125-125">每个键中列的数目必须相等。</span><span class="sxs-lookup"><span data-stu-id="10125-125">There must be an equal number of columns in each of the keys.</span></span> <span data-ttu-id="10125-126">例如，如果关系主键方的表的主键由两列组成，您将需要将这两列中的每一列与关系外键方的表中的列匹配。</span><span class="sxs-lookup"><span data-stu-id="10125-126">For example, if the primary key of the table on the primary side of the relationship is made up of two columns, you will need to match each of those columns with a column in the table for the foreign key side of the relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10125-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10125-127">See Also</span></span>  
 [<span data-ttu-id="10125-128">创建外键关系</span><span class="sxs-lookup"><span data-stu-id="10125-128">Create Foreign Key Relationships</span></span>](../../relational-databases/tables/create-foreign-key-relationships.md)  
  
  
