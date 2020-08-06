---
title: “添加表”对话框（数据库设计器）(Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65555
- vdt.dlgbox.schema.addtable
ms.assetid: 3c0b1b30-795c-4240-91d6-890b8348014a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ae9d3763ef66c0a7580cc516169c2f273f36528
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579949"
---
# <a name="add-table-dialog-box-database-designer-visual-database-tools"></a><span data-ttu-id="7f721-102">“添加表”对话框（数据库设计器）(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7f721-102">Add Table Dialog Box (Database Designer) (Visual Database Tools)</span></span>
  <span data-ttu-id="7f721-103">使用此对话框可以在数据库设计器中添加表。</span><span class="sxs-lookup"><span data-stu-id="7f721-103">Lets you add tables in Database Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f721-104">如果表是为复制发布的，则必须使用 Transact-SQL 语句 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理对象 (SMO) 对架构进行更改。</span><span class="sxs-lookup"><span data-stu-id="7f721-104">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="7f721-105">使用表设计器或数据库关系图设计器更改架构后，会尝试删除并重新创建表。</span><span class="sxs-lookup"><span data-stu-id="7f721-105">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="7f721-106">由于您不能删除已发布的对象，因此架构更改将失败。</span><span class="sxs-lookup"><span data-stu-id="7f721-106">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="7f721-107">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="7f721-107">UI element list</span></span>  
 <span data-ttu-id="7f721-108">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="7f721-108">**Refresh**</span></span>  
 <span data-ttu-id="7f721-109">刷新表的列表以与数据库的当前状态匹配。</span><span class="sxs-lookup"><span data-stu-id="7f721-109">Refreshed the list of tables to match the current state of the database.</span></span>  
  
 <span data-ttu-id="7f721-110">**添加**</span><span class="sxs-lookup"><span data-stu-id="7f721-110">**Add**</span></span>  
 <span data-ttu-id="7f721-111">添加所选的一个或多个表。</span><span class="sxs-lookup"><span data-stu-id="7f721-111">Adds the selected table or tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f721-112">如果希望将多个表添加到关系图中，可以将其全部选定，再单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="7f721-112">If you want to add several tables to the diagram, you can select them all before clicking **Add**.</span></span> <span data-ttu-id="7f721-113">或者，也可以双击要添加的每个表，然后在完成后单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="7f721-113">Alternatively, you can double-click each table you want to add, then click **Close** when you are finished.</span></span>  
  
 <span data-ttu-id="7f721-114">**关闭**</span><span class="sxs-lookup"><span data-stu-id="7f721-114">**Close**</span></span>  
 <span data-ttu-id="7f721-115">关闭对话框而不再添加表。</span><span class="sxs-lookup"><span data-stu-id="7f721-115">Closes the dialog box without adding further tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f721-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f721-116">See Also</span></span>  
 [<span data-ttu-id="7f721-117">向关系图中添加表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7f721-117">Add Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
