---
title: 修改外键关系 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65538
- vdt.ppg.relationships
helpviewer_keywords:
- foreign keys [SQL Server], modifying
- modifying foreign keys
ms.assetid: 0c9ca80d-d79b-44c4-a21e-0fce39c398ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: ba9010b0d634a174dd35391c870d5003aa78efa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578034"
---
# <a name="modify-foreign-key-relationships"></a><span data-ttu-id="b627d-102">修改外键关系</span><span class="sxs-lookup"><span data-stu-id="b627d-102">Modify Foreign Key Relationships</span></span>
  <span data-ttu-id="b627d-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改关系的外键端。</span><span class="sxs-lookup"><span data-stu-id="b627d-103">You can modify the foreign key side of a relationship in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b627d-104">修改表的外键会更改与主键表中的列相关的列。</span><span class="sxs-lookup"><span data-stu-id="b627d-104">Modifying a table's foreign key changes which columns are related to columns in the primary key table.</span></span>  
  
 <span data-ttu-id="b627d-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b627d-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b627d-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b627d-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b627d-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b627d-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b627d-108">安全性</span><span class="sxs-lookup"><span data-stu-id="b627d-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b627d-109">**修改外键，使用：**</span><span class="sxs-lookup"><span data-stu-id="b627d-109">**To modify a foreign key using:**</span></span>  
  
     [<span data-ttu-id="b627d-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b627d-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b627d-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b627d-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b627d-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="b627d-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b627d-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b627d-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="b627d-114">新的外键列必须与和其相关的主键列的数据类型和大小相匹配，但以下情况例外：</span><span class="sxs-lookup"><span data-stu-id="b627d-114">The new foreign key column must match the data type and size of the primary key column to which it relates, with these exceptions:</span></span>  
  
-   <span data-ttu-id="b627d-115">`char` 列或 `sysname` 列可以与 `varchar` 列相关。</span><span class="sxs-lookup"><span data-stu-id="b627d-115">A `char` column or `sysname` column can relate to a `varchar` column.</span></span>  
  
-   <span data-ttu-id="b627d-116">`binary` 列可以与 `varbinary` 列相关。</span><span class="sxs-lookup"><span data-stu-id="b627d-116">A `binary` column can relate to a `varbinary` column.</span></span>  
  
-   <span data-ttu-id="b627d-117">别名数据类型可以与其基类型相关。</span><span class="sxs-lookup"><span data-stu-id="b627d-117">An alias data type can relate to its base type.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b627d-118">Security</span><span class="sxs-lookup"><span data-stu-id="b627d-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b627d-119">权限</span><span class="sxs-lookup"><span data-stu-id="b627d-119">Permissions</span></span>  
 <span data-ttu-id="b627d-120">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="b627d-120">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b627d-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b627d-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-foreign-key"></a><span data-ttu-id="b627d-122">修改外键</span><span class="sxs-lookup"><span data-stu-id="b627d-122">To modify a foreign key</span></span>  
  
1.  <span data-ttu-id="b627d-123">在 **“对象资源管理器”** 中，展开具有外键的表，再展开 **“键”** 。</span><span class="sxs-lookup"><span data-stu-id="b627d-123">In **Object Explorer**, expand the table with the foreign key and then expand **Keys**.</span></span>  
  
2.  <span data-ttu-id="b627d-124">右键单击要修改的外键，然后选择“修改”  。</span><span class="sxs-lookup"><span data-stu-id="b627d-124">Right-click the foreign key to be modified and select **Modify**.</span></span>  
  
3.  <span data-ttu-id="b627d-125">在 **“外键关系”** 对话框中，可以进行以下修改。</span><span class="sxs-lookup"><span data-stu-id="b627d-125">In the **Foreign Key Relationships** dialog box, you can make the following modifications.</span></span>  
  
     <span data-ttu-id="b627d-126">**选定的关系**</span><span class="sxs-lookup"><span data-stu-id="b627d-126">**Selected Relationship**</span></span>  
     <span data-ttu-id="b627d-127">列出现有的关系。</span><span class="sxs-lookup"><span data-stu-id="b627d-127">Lists existing relationships.</span></span> <span data-ttu-id="b627d-128">选择一个关系将在右侧的网格中显示其属性。</span><span class="sxs-lookup"><span data-stu-id="b627d-128">Select a relationship to show its properties in the grid to the right.</span></span> <span data-ttu-id="b627d-129">如果该列表为空，则表示尚未为该表定义关系。</span><span class="sxs-lookup"><span data-stu-id="b627d-129">If the list is empty, no relationships have been defined for the table.</span></span>  
  
     <span data-ttu-id="b627d-130">**添加**</span><span class="sxs-lookup"><span data-stu-id="b627d-130">**Add**</span></span>  
     <span data-ttu-id="b627d-131">创建新关系。</span><span class="sxs-lookup"><span data-stu-id="b627d-131">Create a new relationship.</span></span> <span data-ttu-id="b627d-132">必须先设置 **“表和列规范”** ，之后该关系才会生效。</span><span class="sxs-lookup"><span data-stu-id="b627d-132">The **Tables and Columns Specifications** must be set before the relationship will be valid.</span></span>  
  
     <span data-ttu-id="b627d-133">**删除**</span><span class="sxs-lookup"><span data-stu-id="b627d-133">**Delete**</span></span>  
     <span data-ttu-id="b627d-134">在“选定的关系”  列表中删除所选的关系。</span><span class="sxs-lookup"><span data-stu-id="b627d-134">Delete the relationship selected in the **Selected Relationships** list.</span></span> <span data-ttu-id="b627d-135">若要取消添加关系，请使用此按钮来移除关系。</span><span class="sxs-lookup"><span data-stu-id="b627d-135">To cancel the addition of a relationship, use this button to remove the relationship.</span></span>  
  
     <span data-ttu-id="b627d-136">**常规类别**</span><span class="sxs-lookup"><span data-stu-id="b627d-136">**General Category**</span></span>  
     <span data-ttu-id="b627d-137">展开此项可显示“在创建或重新启用时检查现有数据”  以及“表和列规范”  。</span><span class="sxs-lookup"><span data-stu-id="b627d-137">Expand to show **Check Existing Data on Creation or RE-Enabling** and **Tables and Columns Specifications**.</span></span>  
  
     <span data-ttu-id="b627d-138">**在创建或重新启用时检查现有数据**</span><span class="sxs-lookup"><span data-stu-id="b627d-138">**Check Existing Data on Creation or Re-Enabling**</span></span>  
     <span data-ttu-id="b627d-139">根据约束对创建或重新启用约束前表中的全部已有数据进行验证。</span><span class="sxs-lookup"><span data-stu-id="b627d-139">Verify all existing data in the table before the constraint was created or re-enabled, against the constraint.</span></span>  
  
     <span data-ttu-id="b627d-140">**表和列规范类别**</span><span class="sxs-lookup"><span data-stu-id="b627d-140">**Tables and Columns Specifications Category**</span></span>  
     <span data-ttu-id="b627d-141">展开此项可显示哪些表中的哪些列用作关系中的外键和主键（或唯一键）。</span><span class="sxs-lookup"><span data-stu-id="b627d-141">Expand to show which columns from which tables act as the foreign key and primary (or unique) key in the relationship.</span></span> <span data-ttu-id="b627d-142">若要编辑或定义这些值，请单击属性字段右侧的省略号按钮 (…)  。</span><span class="sxs-lookup"><span data-stu-id="b627d-142">To edit or define these values, click the ellipsis button (**...**) to the right of the property field.</span></span>  
  
     <span data-ttu-id="b627d-143">**外键基表**</span><span class="sxs-lookup"><span data-stu-id="b627d-143">**Foreign Key Base Table**</span></span>  
     <span data-ttu-id="b627d-144">显示哪个表包含用作所选关系中外键的列。</span><span class="sxs-lookup"><span data-stu-id="b627d-144">Shows which table contains the column acting as a foreign key in the selected relationship.</span></span>  
  
     <span data-ttu-id="b627d-145">**外键列**</span><span class="sxs-lookup"><span data-stu-id="b627d-145">**Foreign Key Columns**</span></span>  
     <span data-ttu-id="b627d-146">显示哪个列用作所选关系的外键。</span><span class="sxs-lookup"><span data-stu-id="b627d-146">Shows which column acts as a foreign key in the selected relationship.</span></span>  
  
     <span data-ttu-id="b627d-147">**主/唯一键基表**</span><span class="sxs-lookup"><span data-stu-id="b627d-147">**Primary/Unique Key Base Table**</span></span>  
     <span data-ttu-id="b627d-148">显示哪个表包含用作所选关系中主键（或唯一键）的列。</span><span class="sxs-lookup"><span data-stu-id="b627d-148">Shows which table contains the column acting as a primary (or unique) key in the selected relationship.</span></span>  
  
     <span data-ttu-id="b627d-149">**主/唯一键列**</span><span class="sxs-lookup"><span data-stu-id="b627d-149">**Primary/Unique Key Columns**</span></span>  
     <span data-ttu-id="b627d-150">显示哪个列用作所选关系的主键（或唯一键）。</span><span class="sxs-lookup"><span data-stu-id="b627d-150">Shows which column acts as a primary (or unique) key in the selected relationship.</span></span>  
  
     <span data-ttu-id="b627d-151">**标识类别**</span><span class="sxs-lookup"><span data-stu-id="b627d-151">**Identity Category**</span></span>  
     <span data-ttu-id="b627d-152">展开此项可显示“名称”  和“说明”  的属性字段。</span><span class="sxs-lookup"><span data-stu-id="b627d-152">Expand to show the property fields for **Name** and **Description**.</span></span>  
  
     <span data-ttu-id="b627d-153">**名称**</span><span class="sxs-lookup"><span data-stu-id="b627d-153">**Name**</span></span>  
     <span data-ttu-id="b627d-154">显示关系的名称。</span><span class="sxs-lookup"><span data-stu-id="b627d-154">Shows the name of the relationship.</span></span> <span data-ttu-id="b627d-155">在创建新关系时，将基于 **表设计器**的活动窗口中的表为其指定默认名称。</span><span class="sxs-lookup"><span data-stu-id="b627d-155">When a new relationship is created, it is given a default name based on the table in the active window in **Table Designer**.</span></span> <span data-ttu-id="b627d-156">可随时更改名称。</span><span class="sxs-lookup"><span data-stu-id="b627d-156">You can change the name at any time.</span></span>  
  
     <span data-ttu-id="b627d-157">**说明**</span><span class="sxs-lookup"><span data-stu-id="b627d-157">**Description**</span></span>  
     <span data-ttu-id="b627d-158">描述该关系。</span><span class="sxs-lookup"><span data-stu-id="b627d-158">Describe the relationship.</span></span> <span data-ttu-id="b627d-159">若要编写更详细的说明，请单击“说明”  ，再单击属性字段右侧显示的省略号 **(...)** 。</span><span class="sxs-lookup"><span data-stu-id="b627d-159">To write a more detailed description, click **Description** and then click the ellipsis **(...)** that appears to the right of the property field.</span></span> <span data-ttu-id="b627d-160">这可以提供一个更大的文本编写区域。</span><span class="sxs-lookup"><span data-stu-id="b627d-160">This provides a larger area in which to write text.</span></span>  
  
     <span data-ttu-id="b627d-161">**表设计器类别**</span><span class="sxs-lookup"><span data-stu-id="b627d-161">**Table Designer Category**</span></span>  
     <span data-ttu-id="b627d-162">展开此项可显示“在创建或重新启用时检查现有数据”  和“强制用于复制”  的信息。</span><span class="sxs-lookup"><span data-stu-id="b627d-162">Expand to show information for **Check Existing Data on Creation or Re-Enabling** and **Enforce for Replication**.</span></span>  
  
     <span data-ttu-id="b627d-163">**强制用于复制**</span><span class="sxs-lookup"><span data-stu-id="b627d-163">**Enforce For Replication**</span></span>  
     <span data-ttu-id="b627d-164">指示当复制代理对此表执行插入、更新或删除操作时是否强制约束。</span><span class="sxs-lookup"><span data-stu-id="b627d-164">Indicates whether to enforce the constraint when a replication agent performs an insert, update, or delete on this table.</span></span>  
  
     <span data-ttu-id="b627d-165">**强制外键约束**</span><span class="sxs-lookup"><span data-stu-id="b627d-165">**Enforce Foreign Key Constraint**</span></span>  
     <span data-ttu-id="b627d-166">指示如果对关系中列数据的更改会使外键关系的完整性失效，是否允许进行这样的更改。</span><span class="sxs-lookup"><span data-stu-id="b627d-166">Specify whether changes are allowed to the data of the columns in the relationship if those changes would invalidate the integrity of the foreign key relationship.</span></span> <span data-ttu-id="b627d-167">如果不允许这样的更改，则选择 **“是”** ；如果允许这样的更改，则选择 **“否”** 。</span><span class="sxs-lookup"><span data-stu-id="b627d-167">Choose **Yes** if you do not want to allow such changes, and choose **No** if you do want to allow them.</span></span>  
  
     <span data-ttu-id="b627d-168">**INSERT 和 UPDATE 规范类别**</span><span class="sxs-lookup"><span data-stu-id="b627d-168">**INSERT and UPDATE Specification Category**</span></span>  
     <span data-ttu-id="b627d-169">展开此项可显示关系的“删除规则”  和“更新规则”  的信息。</span><span class="sxs-lookup"><span data-stu-id="b627d-169">Expand to show information for the **Delete Rule** and the **Update Rule** for the relationship.</span></span>  
  
     <span data-ttu-id="b627d-170">**删除规则**</span><span class="sxs-lookup"><span data-stu-id="b627d-170">**Delete Rule**</span></span>  
     <span data-ttu-id="b627d-171">指定当用户尝试删除某一行而该行包含外键关系涉及的数据时将发生的情况。</span><span class="sxs-lookup"><span data-stu-id="b627d-171">Specify what happens if a user tries to delete a row with data that is involved in a foreign key relationship:</span></span>  
  
    -   <span data-ttu-id="b627d-172">**不执行任何操作** 错误消息告知用户不允许进行删除并将回滚 DELETE。</span><span class="sxs-lookup"><span data-stu-id="b627d-172">**No Action** An error message tells the user that the deletion is not allowed and the DELETE is rolled back.</span></span>  
  
    -   <span data-ttu-id="b627d-173">**级联** 删除所有包含外键关系所涉及数据的行。</span><span class="sxs-lookup"><span data-stu-id="b627d-173">**Cascade** Deletes all rows containing data involved in the foreign key relationship.</span></span> <span data-ttu-id="b627d-174">如果该表将包含在使用逻辑记录的合并发布中，则不要指定 CASCADE。</span><span class="sxs-lookup"><span data-stu-id="b627d-174">Do not specify CASCADE if the table will be included in a merge publication that uses logical records.</span></span>  
  
    -   <span data-ttu-id="b627d-175">**设置 Null** 如果表的所有外键列都可接受 Null 值，则将该值设置为 Null。</span><span class="sxs-lookup"><span data-stu-id="b627d-175">**Set Null** Sets the value to null if all foreign key columns for the table can accept null values.</span></span>  
  
    -   <span data-ttu-id="b627d-176">**设置默认值** 如果表的所有外键列均已定义默认值，则将该值设置成为该列定义的默认值。</span><span class="sxs-lookup"><span data-stu-id="b627d-176">**Set Default** Sets the value to the default value defined for the column if all foreign key columns for the table have defaults defined for them.</span></span>  
  
     <span data-ttu-id="b627d-177">**更新规则**</span><span class="sxs-lookup"><span data-stu-id="b627d-177">**Update Rule**</span></span>  
     <span data-ttu-id="b627d-178">指定当用户尝试更新某一行而该行包含外键关系涉及的数据时将发生的情况。</span><span class="sxs-lookup"><span data-stu-id="b627d-178">Specify what occurs if a user tries to update a row with data that is involved in a foreign key relationship:</span></span>  
  
    -   <span data-ttu-id="b627d-179">**不执行任何操作** 错误消息告知用户不允许进行更新并将回滚 UPDATE。</span><span class="sxs-lookup"><span data-stu-id="b627d-179">**No Action** An error message tells the user that the update is not allowed and the UPDATE is rolled back.</span></span>  
  
    -   <span data-ttu-id="b627d-180">**级联** 更新所有包含外键关系所涉及数据的行。</span><span class="sxs-lookup"><span data-stu-id="b627d-180">**Cascade** Updates all rows that contain data involved in the foreign key relationship.</span></span> <span data-ttu-id="b627d-181">如果该表将包含在使用逻辑记录的合并发布中，则不要指定 CASCADE。</span><span class="sxs-lookup"><span data-stu-id="b627d-181">Do not specify CASCADE if the table will be included in a merge publication that uses logical records.</span></span>  
  
    -   <span data-ttu-id="b627d-182">**设置 Null** 如果表的所有外键列都可接受 Null 值，则将该值设置为 Null。</span><span class="sxs-lookup"><span data-stu-id="b627d-182">**Set Null** Sets the value to null if all foreign key columns for the table can accept null values.</span></span>  
  
    -   <span data-ttu-id="b627d-183">**设置默认值** 如果表的所有外键列均已定义默认值，则将值设置成为该列定义的默认值。</span><span class="sxs-lookup"><span data-stu-id="b627d-183">**Set Default** Sets the value to the default value that is defined for the column if all foreign key columns for the table have defaults defined for them.</span></span>  
  
4.  <span data-ttu-id="b627d-184">在“文件”  菜单上，单击“保存”  以保存表名  。</span><span class="sxs-lookup"><span data-stu-id="b627d-184">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b627d-185">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b627d-185">Using Transact-SQL</span></span>  
 <span data-ttu-id="b627d-186">**修改外键**</span><span class="sxs-lookup"><span data-stu-id="b627d-186">**To modify a foreign key**</span></span>  
  
 <span data-ttu-id="b627d-187">若要使用 Transact-SQL 修改 FOREIGN KEY 约束，必须先删除现有的 FOREIGN KEY 约束，然后再用新定义重新创建该约束。</span><span class="sxs-lookup"><span data-stu-id="b627d-187">To modify a FOREIGN KEY constraint by using Transact-SQL, you must first delete the existing FOREIGN KEY constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="b627d-188">有关详细信息，请参阅 [Delete Foreign Key Relationships](delete-foreign-key-relationships.md) 和 [Create Foreign Key Relationships](create-foreign-key-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="b627d-188">For more information, see [Delete Foreign Key Relationships](delete-foreign-key-relationships.md) and [Create Foreign Key Relationships](create-foreign-key-relationships.md).</span></span>  
  
###  <a name="TsqlExample"></a>  
