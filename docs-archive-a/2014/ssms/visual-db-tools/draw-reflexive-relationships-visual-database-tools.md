---
title: 绘制自反关系 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- drawing reflexive relationships
- reflexive relationships
- database diagrams [SQL Server], relationships
ms.assetid: e218363f-faec-46d5-9904-a537fbcc994d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e5056b1a5d0d884edbc4fc818fe8c7ef5cc8ad4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588194"
---
# <a name="draw-reflexive-relationships-visual-database-tools"></a><span data-ttu-id="e085e-102">绘制自反关系 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e085e-102">Draw Reflexive Relationships (Visual Database Tools)</span></span>
  <span data-ttu-id="e085e-103">您可以创建自反关系，将一个表中的一列或多列与同一表中的另一列或多列相链接。</span><span class="sxs-lookup"><span data-stu-id="e085e-103">You create a reflexive relationship to link a column or columns in a table with another column or columns in the same table.</span></span> <span data-ttu-id="e085e-104">例如，假设 `employee` 表包含 `emp_id` 列和 `mgr_id` 列。</span><span class="sxs-lookup"><span data-stu-id="e085e-104">For example, suppose the `employee` table has an `emp_id` column and a `mgr_id` column.</span></span> <span data-ttu-id="e085e-105">因为每个主管也是雇员，所以可以通过绘制该表与其自身的关系线将这两列相关。</span><span class="sxs-lookup"><span data-stu-id="e085e-105">Because each manager is also an employee, you relate these two columns by drawing a relationship line from the table to itself.</span></span> <span data-ttu-id="e085e-106">此关系确保添加到表中的每个主管 ID 与一个现有雇员 ID 匹配。</span><span class="sxs-lookup"><span data-stu-id="e085e-106">This relationship ensures each manager ID that is added to the table matches an existing employee ID.</span></span>  
  
 <span data-ttu-id="e085e-107">在创建关系之前，必须首先为表定义主键或唯一约束。</span><span class="sxs-lookup"><span data-stu-id="e085e-107">Before you create a relationship, you must first define a primary key or unique constraint for your table.</span></span> <span data-ttu-id="e085e-108">然后需要将主键列与匹配列相关。</span><span class="sxs-lookup"><span data-stu-id="e085e-108">You then relate the primary key column to a matching column.</span></span> <span data-ttu-id="e085e-109">一旦创建关系，匹配列即成为表的外键。</span><span class="sxs-lookup"><span data-stu-id="e085e-109">Once you create the relationship, the matching column becomes a foreign key of the table.</span></span>  
  
### <a name="to-draw-a-reflexive-relationship"></a><span data-ttu-id="e085e-110">绘制自反关系</span><span class="sxs-lookup"><span data-stu-id="e085e-110">To draw a reflexive relationship</span></span>  
  
1.  <span data-ttu-id="e085e-111">在数据库关系图中，单击要与另一列相关联的数据库列的行选择器，并将指针拖出表外，直至有一个线条显示为止。</span><span class="sxs-lookup"><span data-stu-id="e085e-111">In your database diagram, click the row selector for the database column that you want to relate to another column and drag the pointer outside the table until a line appears.</span></span>  
  
2.  <span data-ttu-id="e085e-112">将该线条拖回所选的表。</span><span class="sxs-lookup"><span data-stu-id="e085e-112">Drag the line back to the selected table.</span></span>  
  
3.  <span data-ttu-id="e085e-113">释放鼠标按钮。</span><span class="sxs-lookup"><span data-stu-id="e085e-113">Release the mouse button.</span></span> <span data-ttu-id="e085e-114">此时，将显示“表和列”  对话框。</span><span class="sxs-lookup"><span data-stu-id="e085e-114">The **Tables and Columns** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="e085e-115">选择外键列以及要与之建立关系的主键表和列。</span><span class="sxs-lookup"><span data-stu-id="e085e-115">Select the foreign key column and the primary key table and column with which you want form a relationship.</span></span>  
  
5.  <span data-ttu-id="e085e-116">选择“确定”  两次以创建关系。</span><span class="sxs-lookup"><span data-stu-id="e085e-116">Choose **OK** twice to create the relationship.</span></span>  
  
 <span data-ttu-id="e085e-117">如果对表运行查询，则可使用自反关系创建自联接。</span><span class="sxs-lookup"><span data-stu-id="e085e-117">When you run queries against a table, you can use a reflexive relationship to create a self-join.</span></span> <span data-ttu-id="e085e-118">有关使用联接查询表的信息，请参阅 [使用联接进行查询 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e085e-118">For information about querying tables with joins, see [Query with Joins &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e085e-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e085e-119">See Also</span></span>  
 [<span data-ttu-id="e085e-120">使用联接进行查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e085e-120">Query with Joins &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
