---
title: “CHECK 约束”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.checkconstraint
ms.assetid: ad0bbf7f-b0de-406a-bd0a-cb779816b101
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7244984b869a1c68e597984a1cd03e16e53d0306
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576486"
---
# <a name="check-constraint-dialog-box-visual-database-tools"></a><span data-ttu-id="79f0d-102">“CHECK 约束”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="79f0d-102">Check Constraint Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="79f0d-103">如果在表设计器中右键单击表定义网格，再单击“CHECK 约束”  ，则会显示此对话框。</span><span class="sxs-lookup"><span data-stu-id="79f0d-103">This dialog box appears when you right-click a table definition grid in Table Designer and click **Check Constraints**.</span></span> <span data-ttu-id="79f0d-104">此对话框包含附加到数据库中表的非唯一约束的一组属性。</span><span class="sxs-lookup"><span data-stu-id="79f0d-104">The dialog box contains a set of properties for non-unique constraints attached to the tables in your database.</span></span> <span data-ttu-id="79f0d-105">应用于唯一约束的属性则包含在“索引/键”  对话框中。</span><span class="sxs-lookup"><span data-stu-id="79f0d-105">Properties applying to unique constraints appear in the **Indexes/Keys** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="79f0d-106">如果表是为复制发布的，则必须使用 Transact-SQL 语句 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理对象 (SMO) 对架构进行更改。</span><span class="sxs-lookup"><span data-stu-id="79f0d-106">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="79f0d-107">使用表设计器或数据库关系图设计器更改架构后，会尝试删除并重新创建表。</span><span class="sxs-lookup"><span data-stu-id="79f0d-107">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="79f0d-108">由于您不能删除已发布的对象，因此架构更改将失败。</span><span class="sxs-lookup"><span data-stu-id="79f0d-108">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="79f0d-109">选项</span><span class="sxs-lookup"><span data-stu-id="79f0d-109">Options</span></span>  
 <span data-ttu-id="79f0d-110">**选定的 CHECK 约束**</span><span class="sxs-lookup"><span data-stu-id="79f0d-110">**Selected Check Constraints**</span></span>  
 <span data-ttu-id="79f0d-111">列出可用的 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="79f0d-111">Lists available check constraints.</span></span> <span data-ttu-id="79f0d-112">若要查看约束的属性，请在列表中将其选定。</span><span class="sxs-lookup"><span data-stu-id="79f0d-112">To view the properties of a constraint, select it in the list.</span></span>  
  
 <span data-ttu-id="79f0d-113">**添加**</span><span class="sxs-lookup"><span data-stu-id="79f0d-113">**Add**</span></span>  
 <span data-ttu-id="79f0d-114">为选定的数据库表创建一个新约束，并为该约束提供默认名称和其他值。</span><span class="sxs-lookup"><span data-stu-id="79f0d-114">Create a new constraint for the selected database table and provide a default name and other values for the constraint.</span></span> <span data-ttu-id="79f0d-115">只有在为该约束输入表达式之后，该约束才会生效。</span><span class="sxs-lookup"><span data-stu-id="79f0d-115">The constraint will not become valid until an expression is entered for the constraint.</span></span>  
  
 <span data-ttu-id="79f0d-116">**删除**</span><span class="sxs-lookup"><span data-stu-id="79f0d-116">**Delete**</span></span>  
 <span data-ttu-id="79f0d-117">从表中移除选定的约束。</span><span class="sxs-lookup"><span data-stu-id="79f0d-117">Remove the selected constraint from the table.</span></span> <span data-ttu-id="79f0d-118">若要取消添加 CHECK 约束，请使用此按钮来移除约束。</span><span class="sxs-lookup"><span data-stu-id="79f0d-118">To cancel the addition of a check constraint, use this button to remove the constraint.</span></span>  
  
 <span data-ttu-id="79f0d-119">**常规类别**</span><span class="sxs-lookup"><span data-stu-id="79f0d-119">**General Category**</span></span>  
 <span data-ttu-id="79f0d-120">展开此项可显示“表达式”  属性字段。</span><span class="sxs-lookup"><span data-stu-id="79f0d-120">Expand to show the **Expression** property field.</span></span>  
  
 <span data-ttu-id="79f0d-121">**表达式**</span><span class="sxs-lookup"><span data-stu-id="79f0d-121">**Expression**</span></span>  
 <span data-ttu-id="79f0d-122">显示选定的 CHECK 约束的表达式。</span><span class="sxs-lookup"><span data-stu-id="79f0d-122">Displays the expression for the selected check constraint.</span></span> <span data-ttu-id="79f0d-123">对于新约束，必须先输入表达式，然后才能退出此框。</span><span class="sxs-lookup"><span data-stu-id="79f0d-123">For new constraints, you must enter the expression before exiting this box.</span></span> <span data-ttu-id="79f0d-124">您还可以编辑现有的 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="79f0d-124">You can also edit existing check constraints.</span></span> <span data-ttu-id="79f0d-125">有关详细信息，请参阅 [Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="79f0d-125">For more information, see [Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md).</span></span>  
  
 <span data-ttu-id="79f0d-126">**标识类别**</span><span class="sxs-lookup"><span data-stu-id="79f0d-126">**Identity Category**</span></span>  
 <span data-ttu-id="79f0d-127">展开此项可显示“名称”  和“说明”  的属性。</span><span class="sxs-lookup"><span data-stu-id="79f0d-127">Expand to show properties for **Name** and **Description**.</span></span>  
  
 <span data-ttu-id="79f0d-128">**名称**</span><span class="sxs-lookup"><span data-stu-id="79f0d-128">**Name**</span></span>  
 <span data-ttu-id="79f0d-129">显示选定的 CHECK 约束的名称。</span><span class="sxs-lookup"><span data-stu-id="79f0d-129">Shows the name of the selected check constraint.</span></span> <span data-ttu-id="79f0d-130">若要更改此约束的名称，请直接在属性字段键入文本。</span><span class="sxs-lookup"><span data-stu-id="79f0d-130">To change the name of this constraint, type the text directly in the property field.</span></span>  
  
 <span data-ttu-id="79f0d-131">**说明**</span><span class="sxs-lookup"><span data-stu-id="79f0d-131">**Description**</span></span>  
 <span data-ttu-id="79f0d-132">描述此 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="79f0d-132">Describing this check constraint.</span></span> <span data-ttu-id="79f0d-133">既可以在属性字段中键入内容来编辑说明，也可以单击属性字段右侧显示的省略号按钮(…)，然后在“说明属性”对话框中编辑说明   。</span><span class="sxs-lookup"><span data-stu-id="79f0d-133">You can edit the description by typing into the property field or you can click the ellipsis button (**...**) that appears to the right of the property field and edit the description in the **Description Property** dialog box.</span></span>  
  
 <span data-ttu-id="79f0d-134">**表设计器类别**</span><span class="sxs-lookup"><span data-stu-id="79f0d-134">**Table Designer Category**</span></span>  
 <span data-ttu-id="79f0d-135">展开此项可显示“在创建或重新启用时检查现有数据”  、“强制用于 INSERT 和 UPDATE”  和“强制用于复制”  的属性。</span><span class="sxs-lookup"><span data-stu-id="79f0d-135">Expand to show properties for **Check Existing Data on Creation or Re-enabling**, **Enforce For Inserts And Updates**, and **Enforce Replication**.</span></span>  
  
 <span data-ttu-id="79f0d-136">**在创建或重新启用时检查现有数据**</span><span class="sxs-lookup"><span data-stu-id="79f0d-136">**Check Existing Data On Creation or Re-Enabling**</span></span>  
 <span data-ttu-id="79f0d-137">指定是否根据约束验证所有预先存在的数据（创建约束前存在于表中的数据）。</span><span class="sxs-lookup"><span data-stu-id="79f0d-137">Specify whether all pre-existing data (data existing in the table before the constraint is created) is verified against the constraint.</span></span>  
  
 <span data-ttu-id="79f0d-138">**强制用于 INSERT 和 UPDATE**</span><span class="sxs-lookup"><span data-stu-id="79f0d-138">**Enforce For Inserts And Updates**</span></span>  
 <span data-ttu-id="79f0d-139">指定在表中插入或更新数据时是否强制约束。</span><span class="sxs-lookup"><span data-stu-id="79f0d-139">Specify whether the constraint is enforced when data is inserted into or updated in the table.</span></span>  
  
 <span data-ttu-id="79f0d-140">**强制用于复制**</span><span class="sxs-lookup"><span data-stu-id="79f0d-140">**Enforce For Replication**</span></span>  
 <span data-ttu-id="79f0d-141">指示当复制代理对此表执行插入或更新操作时是否强制约束。</span><span class="sxs-lookup"><span data-stu-id="79f0d-141">Indicates whether to enforce the constraint when a replication agent performs an insert or update on this table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f0d-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="79f0d-142">See Also</span></span>  
 <span data-ttu-id="79f0d-143">[Unique 约束和 Check 约束](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="79f0d-143">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="79f0d-144">Visual Database Tools &#40;的 "索引和键" 对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="79f0d-144">Indexes and Keys Dialog Box &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
