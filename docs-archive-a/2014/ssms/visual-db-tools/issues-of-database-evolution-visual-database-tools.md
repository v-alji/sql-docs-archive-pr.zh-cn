---
title: 数据库演化问题 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], multuser database changes
- database evolution [SQL Server]
ms.assetid: 1ed6ae10-d212-4ec2-8569-1b94ab1cba6d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 80daa694cd015a83657368902b07da254e6196ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693166"
---
# <a name="issues-of-database-evolution-visual-database-tools"></a><span data-ttu-id="2fc25-102">数据库演化问题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="2fc25-102">Issues of Database Evolution (Visual Database Tools)</span></span>
  <span data-ttu-id="2fc25-103">如果更改已部署的数据库的结构，则必须特别留意更改应与现有的数据和数据库结构兼容。</span><span class="sxs-lookup"><span data-stu-id="2fc25-103">If you change the structure of a deployed database, you must take special care that your alteration is compatible with the existing data and database structure.</span></span> <span data-ttu-id="2fc25-104">当进行以下修改时，可能需要采取特殊步骤：</span><span class="sxs-lookup"><span data-stu-id="2fc25-104">You might need to take special steps when you make the following modifications:</span></span>  
  
-   <span data-ttu-id="2fc25-105">**添加约束** 在添加约束时，数据库可能已经包含不满足该约束的数据。</span><span class="sxs-lookup"><span data-stu-id="2fc25-105">**Adding a Constraint** If you add a constraint, the database might already contain data that does not satisfy it.</span></span> <span data-ttu-id="2fc25-106">当尝试保存新约束时，[“保存后通知”对话框 (Visual Database Tools)](visual-database-tools.md) 将通知你数据库服务器无法创建该约束。</span><span class="sxs-lookup"><span data-stu-id="2fc25-106">When you try to save the new constraint, the [Post-Save Notifications Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md) informs you that the database server could not create the constraint.</span></span> <span data-ttu-id="2fc25-107">若要强制数据库接受新约束，可以清除“在创建时检查现有数据”  复选框。</span><span class="sxs-lookup"><span data-stu-id="2fc25-107">To force the database to accept the new constraint, you can clear the **Check existing data on creation** check box.</span></span>  
  
-   <span data-ttu-id="2fc25-108">**添加关系** 在添加关系时，数据库可能已经包含在主键表中没有相应行的外键表中的行。</span><span class="sxs-lookup"><span data-stu-id="2fc25-108">**Adding a Relationship** If you add a relationship, the database might already contain rows of the foreign-key table that do not have corresponding rows in the primary-key table.</span></span> <span data-ttu-id="2fc25-109">即现有数据可能不满足引用完整性。</span><span class="sxs-lookup"><span data-stu-id="2fc25-109">That is, the existing data might not satisfy referential integrity.</span></span> <span data-ttu-id="2fc25-110">尝试保存新关系时，[“保存后通知”对话框 (Visual Database Tools)](visual-database-tools.md) 将通知你数据库服务器无法保存修改过的外键表。</span><span class="sxs-lookup"><span data-stu-id="2fc25-110">When you try to save the new relationship, the[Post-Save Notifications Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md) informs you that the database server could not save the revised foreign-key table.</span></span> <span data-ttu-id="2fc25-111">若要强制数据库接受修改，可以清除“在创建时检查现有数据”  复选框。</span><span class="sxs-lookup"><span data-stu-id="2fc25-111">To force the database to accept the modification, you can clear the **Check existing data on creation** check box.</span></span>  
  
-   <span data-ttu-id="2fc25-112">**修改分配给索引视图的表** 如果修改分配给 Microsoft SQL Server 索引视图的表，该视图的索引将丢失。</span><span class="sxs-lookup"><span data-stu-id="2fc25-112">**Modifying a Table Contributing to an Indexed View** If you modify a table that contributes to a Microsoft SQL Server indexed view, the indexes on the view will be lost.</span></span> <span data-ttu-id="2fc25-113">有关重新创建索引的信息，请参阅 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="2fc25-113">See the SQL Server Books Online for information on recreating indexes.</span></span>  
  
-   <span data-ttu-id="2fc25-114">**删除对象** 在删除某个对象（例如列、表或视图）时，应首先确保数据库中没有其他对象引用该对象。</span><span class="sxs-lookup"><span data-stu-id="2fc25-114">**Deleting an Object** If you delete an object, such as a column, table, or view, check first to be sure that the object is not referenced by another object in the database.</span></span>  
  
 <span data-ttu-id="2fc25-115">无论如何更改数据库设计，都应保留更改的历史记录。</span><span class="sxs-lookup"><span data-stu-id="2fc25-115">No matter how you alter the database design, you should retain a history of the alterations.</span></span> <span data-ttu-id="2fc25-116">可以通过保留对成品数据库进行的所有修改的 SQL 脚本来保留所做更改。</span><span class="sxs-lookup"><span data-stu-id="2fc25-116">One approach is to retain SQL scripts for all modifications that you ever make to your production database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fc25-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2fc25-117">See Also</span></span>  
 <span data-ttu-id="2fc25-118">[Unique 约束和 Check 约束](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="2fc25-118">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="2fc25-119">多用户环境 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="2fc25-119">Multiuser Environments &#40;Visual Database Tools&#41;</span></span>](multiuser-environments-visual-database-tools.md)  
  
  
