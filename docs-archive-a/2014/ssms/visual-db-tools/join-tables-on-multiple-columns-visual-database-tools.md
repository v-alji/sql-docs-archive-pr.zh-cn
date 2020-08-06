---
title: 在多个列上联接表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiple column joins
- joins [SQL Server], multiple columns
ms.assetid: 56a158bc-a42a-4b78-baad-4721d2d22cd3
author: stevestein
ms.author: sstein
ms.openlocfilehash: dda52fe27b2034242c8cbf458dd010240c792146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587121"
---
# <a name="join-tables-on-multiple-columns-visual-database-tools"></a><span data-ttu-id="5bf90-102">在多个列上联接表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5bf90-102">Join Tables on Multiple Columns (Visual Database Tools)</span></span>
  <span data-ttu-id="5bf90-103">您可以使用多个列来联接表。</span><span class="sxs-lookup"><span data-stu-id="5bf90-103">You can join tables with multiple columns.</span></span> <span data-ttu-id="5bf90-104">即可以创建这样的一个查询，仅当来自两个表中的行都满足多个条件时才与该查询匹配。</span><span class="sxs-lookup"><span data-stu-id="5bf90-104">That is, you can create a query that matches rows from the two tables only if they satisfy multiple conditions.</span></span> <span data-ttu-id="5bf90-105">如果数据库包含的关系将一个表中的多个外键列与另一个表中的多列主键匹配，则可使用此关系创建多列联接。</span><span class="sxs-lookup"><span data-stu-id="5bf90-105">If the database contains a relationship matching multiple foreign-key columns in one table to a multicolumn primary key in the other table, you can use this relationship to create a multicolumn join.</span></span> <span data-ttu-id="5bf90-106">有关详细信息，请参阅[自动联接表 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5bf90-106">For details, see [Join Tables Automatically &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="5bf90-107">即使数据库不包含多列外键关系，也可手动创建多列联接。</span><span class="sxs-lookup"><span data-stu-id="5bf90-107">Even if the database contains no multi-column foreign-key relationship, you can create the join manually.</span></span>  
  
### <a name="to-manually-create-a-multicolumn-join"></a><span data-ttu-id="5bf90-108">手动创建多列联接</span><span class="sxs-lookup"><span data-stu-id="5bf90-108">To manually create a multicolumn join</span></span>  
  
1.  <span data-ttu-id="5bf90-109">将要联接的表添加到 [“关系图”窗格](diagram-pane-visual-database-tools.md) 中。</span><span class="sxs-lookup"><span data-stu-id="5bf90-109">Add to the [Diagram pane](diagram-pane-visual-database-tools.md) the tables you want to join.</span></span>  
  
2.  <span data-ttu-id="5bf90-110">拖动第一个表窗口中的第一个联接列的名称，并将其放到第二个表窗口的相关列上。</span><span class="sxs-lookup"><span data-stu-id="5bf90-110">Drag the name of the first join column in the first table window and drop it onto the related column in the second table window.</span></span> <span data-ttu-id="5bf90-111">不能基于 text、ntext 或 image 列建立联接。</span><span class="sxs-lookup"><span data-stu-id="5bf90-111">You cannot base a join on text, ntext, or image columns.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5bf90-112">通常，联接列必须具有相同（或兼容）的数据类型。</span><span class="sxs-lookup"><span data-stu-id="5bf90-112">In general, the join columns must be of the same (or compatible) data types.</span></span> <span data-ttu-id="5bf90-113">例如，如果第一个表中的联接列是日期，则必须将其与第二个表中的日期列相关。</span><span class="sxs-lookup"><span data-stu-id="5bf90-113">For example, if the join column in the first table is a date, you must relate it to a date column in the second table.</span></span> <span data-ttu-id="5bf90-114">另一方面，如果第一个联接列是整数，则相关联接列也必须是整数数据类型，但它的大小可以不同。</span><span class="sxs-lookup"><span data-stu-id="5bf90-114">On the other hand, if the first join column is an integer, the related join column must also be of an integer data type, but it can be a different size.</span></span> <span data-ttu-id="5bf90-115">但是，在某些情况下，隐式数据类型转换可以成功地联接看起来不兼容的列。</span><span class="sxs-lookup"><span data-stu-id="5bf90-115">However, there may be cases where implicit data type conversions can join seemingly incompatible columns will work.</span></span>  
    >   
    >  <span data-ttu-id="5bf90-116">[查询和视图设计器](query-and-view-designer-tools-visual-database-tools.md) 不检查要用来创建联接的列的数据类型，但当执行查询时，如果数据类型不兼容，数据库将显示错误。</span><span class="sxs-lookup"><span data-stu-id="5bf90-116">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) will not check the data types of the columns you use to create a join, but when you execute the query, the database will display an error if the data types are not compatible.</span></span>  
  
3.  <span data-ttu-id="5bf90-117">拖动第一个表窗口中的第二个联接列的名称，并将其放到第二个表窗口中的相关列上。</span><span class="sxs-lookup"><span data-stu-id="5bf90-117">Drag the name of the second join column in the first table window and drop it onto the related column in the second table window.</span></span>  
  
4.  <span data-ttu-id="5bf90-118">对于两个表中的其他每个联接列对，重复第 3 步。</span><span class="sxs-lookup"><span data-stu-id="5bf90-118">Repeat step 3 for each additional pair of join columns in the two tables.</span></span>  
  
5.  <span data-ttu-id="5bf90-119">运行查询。</span><span class="sxs-lookup"><span data-stu-id="5bf90-119">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf90-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5bf90-120">See Also</span></span>  
 [<span data-ttu-id="5bf90-121">使用联接进行查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5bf90-121">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
