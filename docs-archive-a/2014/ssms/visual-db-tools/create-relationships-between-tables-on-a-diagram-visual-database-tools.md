---
title: 在 (Visual Database Tools) 的关系图上创建表之间的关系 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- diagrams [SQL Server], designing
ms.assetid: 28e9630c-dff4-46cc-bb0e-fe77998b6ac2
author: stevestein
ms.author: sstein
ms.openlocfilehash: d7d627a37f84dcb66b2129bb9c7dbc5890ccd46c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693177"
---
# <a name="create-relationships-between-tables-on-a-diagram-visual-database-tools"></a><span data-ttu-id="b14af-102">在关系图中创建表间的关系（可视化数据库工具）</span><span class="sxs-lookup"><span data-stu-id="b14af-102">Create Relationships Between Tables on a Diagram (Visual Database Tools)</span></span>
  <span data-ttu-id="b14af-103">您可以在关系图设计器中通过在各个表之间拖动列来创建不同表的列之间的关系。</span><span class="sxs-lookup"><span data-stu-id="b14af-103">You can create relationships between columns in different tables in the Diagram Designer by dragging columns between tables.</span></span>  
  
### <a name="to-create-a-relationship-graphically"></a><span data-ttu-id="b14af-104">以图形方式创建关系</span><span class="sxs-lookup"><span data-stu-id="b14af-104">To create a relationship graphically</span></span>  
  
1.  <span data-ttu-id="b14af-105">在数据库设计器中，单击想要将其与另一个表中的列建立关系的一个或多个数据库列的行选择器。</span><span class="sxs-lookup"><span data-stu-id="b14af-105">In Database Designer, click the row selector for one or more database columns that you want to relate to a column in another table.</span></span>  
  
2.  <span data-ttu-id="b14af-106">将所选列拖动到相关的表中。</span><span class="sxs-lookup"><span data-stu-id="b14af-106">Drag the selected column(s) to the related table.</span></span>  
  
3.  <span data-ttu-id="b14af-107">显示两个对话框：“外键关系”  对话框和前景中显示的“表和列”  对话框。</span><span class="sxs-lookup"><span data-stu-id="b14af-107">Two dialog boxes appear: **Foreign Key Relationship** and **Tables and Columns**, with the latter appearing in the foreground.</span></span>  
  
4.  <span data-ttu-id="b14af-108">**关系名称**具有系统提供的名称，格式为 FK_*localtable*_*foreigntable*。</span><span class="sxs-lookup"><span data-stu-id="b14af-108">**Relationship name** has a system-provided name in the format FK_*localtable*_*foreigntable*.</span></span> <span data-ttu-id="b14af-109">您可以更改此值。</span><span class="sxs-lookup"><span data-stu-id="b14af-109">You may change this value.</span></span>  
  
5.  <span data-ttu-id="b14af-110">验证“主键表”  是否指定了正确的表。</span><span class="sxs-lookup"><span data-stu-id="b14af-110">Verify that **Primary key table** specifies the correct table.</span></span>  
  
6.  <span data-ttu-id="b14af-111">网格列出了本地列及与其匹配的外部列。</span><span class="sxs-lookup"><span data-stu-id="b14af-111">The grid lists the local columns and their matching foreign columns.</span></span> <span data-ttu-id="b14af-112">您可以添加或删除表列或者更改映射。</span><span class="sxs-lookup"><span data-stu-id="b14af-112">You can add or remove table columns or change mappings.</span></span>  
  
7.  <span data-ttu-id="b14af-113">选择“确定”。 </span><span class="sxs-lookup"><span data-stu-id="b14af-113">Choose **OK**.</span></span>  
  
     <span data-ttu-id="b14af-114">此时将出现“外键关系”  对话框。</span><span class="sxs-lookup"><span data-stu-id="b14af-114">The **Foreign Key Relationship** dialog box appears.</span></span> <span data-ttu-id="b14af-115">“选定的关系”  中显示了已创建的关系。</span><span class="sxs-lookup"><span data-stu-id="b14af-115">**Selected Relationship** shows the relationship you have created.</span></span>  
  
8.  <span data-ttu-id="b14af-116">在网格中更改关系的属性。</span><span class="sxs-lookup"><span data-stu-id="b14af-116">Change properties for the relationship in the grid.</span></span>  
  
9. <span data-ttu-id="b14af-117">选择 **“确定”** 以创建该关系。</span><span class="sxs-lookup"><span data-stu-id="b14af-117">Choose **OK** to create the relationship.</span></span>  
  
     <span data-ttu-id="b14af-118">数据库设计器将显示所选列之间的关系。</span><span class="sxs-lookup"><span data-stu-id="b14af-118">Database Designer shows a relationship between the columns you chose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b14af-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b14af-119">See Also</span></span>  
 <span data-ttu-id="b14af-120">[Visual Database Tools &#40;"表和列" 对话框&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b14af-120">[Tables and Columns Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="b14af-121">[Unique 约束和 Check 约束](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="b14af-121">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="b14af-122">使用数据库关系图中的表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b14af-122">Work with Tables in Database Diagram &#40;Visual Database Tools&#41;</span></span>](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
