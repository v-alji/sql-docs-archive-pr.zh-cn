---
title: "\"添加表\" 对话框 () 的查询和视图设计器 (Visual Database Tools) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.query.addtable
- vdtsql.chm:65565
ms.assetid: fce7adcc-4cf5-4a52-9203-11c13d1ecf08
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8d7bf30cbdd37927735c36f184208a1ded957763
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579948"
---
# <a name="add-table-dialog-box-query-and-view-designers-visual-database-tools"></a><span data-ttu-id="9c540-102">“添加表”对话框（查询和视图设计器）(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9c540-102">Add Table Dialog Box (Query and View Designers) (Visual Database Tools)</span></span>
  <span data-ttu-id="9c540-103">使用此对话框可以向查询或视图中添加表、视图、用户定义函数或同义词。</span><span class="sxs-lookup"><span data-stu-id="9c540-103">This dialog box lets you add tables, views, user-defined functions, or synonyms to a query or view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c540-104">如果表是为复制发布的，则必须使用 Transact-SQL 语句 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理对象 (SMO) 对架构进行更改。</span><span class="sxs-lookup"><span data-stu-id="9c540-104">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="9c540-105">使用表设计器或数据库关系图设计器更改架构后，会尝试删除并重新创建表。</span><span class="sxs-lookup"><span data-stu-id="9c540-105">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="9c540-106">由于您不能删除已发布的对象，因此架构更改将失败。</span><span class="sxs-lookup"><span data-stu-id="9c540-106">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9c540-107">选项</span><span class="sxs-lookup"><span data-stu-id="9c540-107">Options</span></span>  
 <span data-ttu-id="9c540-108">**表**</span><span class="sxs-lookup"><span data-stu-id="9c540-108">**Tables**</span></span>  
 <span data-ttu-id="9c540-109">列出可以向“关系图”  窗格中添加的表。</span><span class="sxs-lookup"><span data-stu-id="9c540-109">Lists the tables you can add to the **Diagram** pane.</span></span> <span data-ttu-id="9c540-110">若要添加某个表，请选择该表，再单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="9c540-110">To add a table, select it and click **Add**.</span></span> <span data-ttu-id="9c540-111">若要同时添加多个表，请选中这些表，再单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="9c540-111">To add several tables at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="9c540-112">**视图**</span><span class="sxs-lookup"><span data-stu-id="9c540-112">**Views**</span></span>  
 <span data-ttu-id="9c540-113">列出可以向“关系图”  窗格中添加的视图。</span><span class="sxs-lookup"><span data-stu-id="9c540-113">Lists the views you can add to the **Diagram** pane.</span></span> <span data-ttu-id="9c540-114">若要添加某个视图，请选择该视图，再单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="9c540-114">To add a view, select it and click **Add**.</span></span> <span data-ttu-id="9c540-115">若要同时添加多个视图，请选中这些视图，再单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="9c540-115">To add several views at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="9c540-116">**函数**</span><span class="sxs-lookup"><span data-stu-id="9c540-116">**Functions**</span></span>  
 <span data-ttu-id="9c540-117">列出可以向“关系图”  窗格中添加的用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="9c540-117">Lists the user-defined functions you can add to the **Diagram** pane.</span></span> <span data-ttu-id="9c540-118">若要添加某个函数，请选择该函数，再单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="9c540-118">To add a function, select it and click **Add**.</span></span> <span data-ttu-id="9c540-119">若要同时添加多个函数，请选中这些函数，再单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="9c540-119">To add several functions at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="9c540-120">**同义词**</span><span class="sxs-lookup"><span data-stu-id="9c540-120">**Synonyms**</span></span>  
 <span data-ttu-id="9c540-121">列出可以向“关系图”  窗格中添加的同义词。</span><span class="sxs-lookup"><span data-stu-id="9c540-121">Lists the synonyms you can add to the **Diagram** pane.</span></span> <span data-ttu-id="9c540-122">若要添加某个同义词，请选择该同义词，再单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="9c540-122">To add a synonym, select it and click **Add**.</span></span> <span data-ttu-id="9c540-123">若要同时添加多个同义词，请选中这些同义词，再单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="9c540-123">To add several synonyms at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="9c540-124">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="9c540-124">**Refresh**</span></span>  
 <span data-ttu-id="9c540-125">更新该列表以包含自上次检索该列表以来对数据库做出的所有更改。</span><span class="sxs-lookup"><span data-stu-id="9c540-125">Update the list to include any changes made to the database since the list was last retrieved.</span></span>  
  
 <span data-ttu-id="9c540-126">**添加**</span><span class="sxs-lookup"><span data-stu-id="9c540-126">**Add**</span></span>  
 <span data-ttu-id="9c540-127">添加所选的一项或多项。</span><span class="sxs-lookup"><span data-stu-id="9c540-127">Add the selected item or items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c540-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c540-128">See Also</span></span>  
 [<span data-ttu-id="9c540-129">设计查询和视图操作指南主题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9c540-129">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
