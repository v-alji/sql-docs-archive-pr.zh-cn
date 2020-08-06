---
title: 创建外键关系 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- relationships [SQL Server], creating
ms.assetid: 867a54b8-5be4-46e6-9702-49ae6dabf67c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ee0de3311eb6abffcdb71ab725d0650fe96b04c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591836"
---
# <a name="create-foreign-key-relationships"></a><span data-ttu-id="5b0c4-102">创建外键关系</span><span class="sxs-lookup"><span data-stu-id="5b0c4-102">Create Foreign Key Relationships</span></span>
  <span data-ttu-id="5b0c4-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建外键关系。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-103">This topic describes how to create foreign key relationships in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5b0c4-104">当希望将一个表的行与另一个表的行相关联时，您可在这两个表之间创建关系。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-104">You create a relationship between two tables when you want to associate rows of one table with rows of another.</span></span>  
  
 <span data-ttu-id="5b0c4-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="5b0c4-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5b0c4-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="5b0c4-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5b0c4-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="5b0c4-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="5b0c4-108">安全性</span><span class="sxs-lookup"><span data-stu-id="5b0c4-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5b0c4-109">**创建外键关系，使用：**</span><span class="sxs-lookup"><span data-stu-id="5b0c4-109">**To Create Foreign Key Relationships by using:**</span></span>  
  
     [<span data-ttu-id="5b0c4-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5b0c4-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5b0c4-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5b0c4-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5b0c4-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="5b0c4-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5b0c4-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="5b0c4-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="5b0c4-114">外键约束并不仅仅可以与另一表的主键约束相链接，它还可以定义为引用另一个表中 UNIQUE 约束的列。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-114">A foreign key constraint does not have to be linked only to a primary key constraint in another table; it can also be defined to reference the columns of a UNIQUE constraint in another table.</span></span>  
  
-   <span data-ttu-id="5b0c4-115">如果在 FOREIGN KEY 约束的列中输入非 NULL 值，则此值必须在被引用列中存在；否则，将返回违反外键约束的错误信息。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-115">When a value other than NULL is entered into the column of a FOREIGN KEY constraint, the value must exist in the referenced column; otherwise, a foreign key violation error message is returned.</span></span> <span data-ttu-id="5b0c4-116">若要确保验证了组合外键约束的所有值，请对所有参与列指定 NOT NULL。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-116">To make sure that all values of a composite foreign key constraint are verified, specify NOT NULL on all the participating columns.</span></span>  
  
-   <span data-ttu-id="5b0c4-117">FOREIGN KEY 约束仅能引用位于同一服务器上的同一数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-117">FOREIGN KEY constraints can reference only tables within the same database on the same server.</span></span> <span data-ttu-id="5b0c4-118">跨数据库的引用完整性必须通过触发器实现。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-118">Cross-database referential integrity must be implemented through triggers.</span></span> <span data-ttu-id="5b0c4-119">有关详细信息，请参阅 [CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-119">For more information, see [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
-   <span data-ttu-id="5b0c4-120">FOREIGN KEY 约束可引用同一表中的其他列。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-120">FOREIGN KEY constraints can reference another column in the same table.</span></span> <span data-ttu-id="5b0c4-121">此行为称为自引用。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-121">This is referred to as a self-reference.</span></span>  
  
-   <span data-ttu-id="5b0c4-122">在列级指定的 FOREIGN KEY 约束只能列出一个引用列。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-122">A FOREIGN KEY constraint specified at the column level can list only one reference column.</span></span> <span data-ttu-id="5b0c4-123">此列的数据类型必须与定义约束的列的数据类型相同。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-123">This column must have the same data type as the column on which the constraint is defined.</span></span>  
  
-   <span data-ttu-id="5b0c4-124">在表级指定的 FOREIGN KEY 约束所具有的引用列数目必须与约束列列表中的列数相同。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-124">A FOREIGN KEY constraint specified at the table level must have the same number of reference columns as the number of columns in the constraint column list.</span></span> <span data-ttu-id="5b0c4-125">每个引用列的数据类型也必须与列表中相应列的数据类型相同。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-125">The data type of each reference column must also be the same as the corresponding column in the column list.</span></span>  
  
-   <span data-ttu-id="5b0c4-126">对于表可包含的引用其他表的 FOREIGN KEY 约束的数目或其他表所拥有的引用特定表的 FOREIGN KEY 约束的数目， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 都没有预定义的限制。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-126">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not have a predefined limit on either the number of FOREIGN KEY constraints a table can contain that reference other tables, or the number of FOREIGN KEY constraints that are owned by other tables that reference a specific table.</span></span> <span data-ttu-id="5b0c4-127">尽管如此，可使用的 FOREIGN KEY 约束的实际数目还是受硬件配置以及数据库和应用程序设计的限制。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-127">Nevertheless, the actual number of FOREIGN KEY constraints that can be used is limited by the hardware configuration and by the design of the database and application.</span></span> <span data-ttu-id="5b0c4-128">建议表中包含的 FOREIGN KEY 约束不要超过 253 个，并且引用该表的 FOREIGN KEY 约束也不要超过 253 个。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-128">We recommend that a table contain no more than 253 FOREIGN KEY constraints, and that it be referenced by no more than 253 FOREIGN KEY constraints.</span></span>  
  
-   <span data-ttu-id="5b0c4-129">对于临时表不强制 FOREIGN KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-129">FOREIGN KEY constraints are not enforced on temporary tables.</span></span>  
  
-   <span data-ttu-id="5b0c4-130">如果在 CLR 用户定义类型的列上定义外键，则该类型的实现必须支持二进制排序。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-130">If a foreign key is defined on a CLR user-defined type column, the implementation of the type must support binary ordering.</span></span> <span data-ttu-id="5b0c4-131">有关详细信息，请参阅 [CLR 用户定义类型](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-131">For more information, see [CLR User-Defined Types](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).</span></span>  
  
-   <span data-ttu-id="5b0c4-132">仅当 FOREIGN KEY 约束引用的主键也定义为类型 `varchar(max)` 时，才能在此约束中使用类型为 `varchar(max)` 的列。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-132">A column of type `varchar(max)` can participate in a FOREIGN KEY constraint only if the primary key it references is also defined as type `varchar(max)`.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5b0c4-133">Security</span><span class="sxs-lookup"><span data-stu-id="5b0c4-133">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5b0c4-134">权限</span><span class="sxs-lookup"><span data-stu-id="5b0c4-134">Permissions</span></span>  
 <span data-ttu-id="5b0c4-135">使用外键创建新表需要在数据库中具有 CREATE TABLE 权限，并对在其中创建表的架构具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-135">Creating a new table with a foreign key requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span>  
  
 <span data-ttu-id="5b0c4-136">在某一现有表中创建外键需要对该表具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-136">Creating a foreign key in an existing table requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5b0c4-137">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5b0c4-137">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-foreign-key-relationship-in-table-designer"></a><span data-ttu-id="5b0c4-138">在表设计器中创建外键关系</span><span class="sxs-lookup"><span data-stu-id="5b0c4-138">To create a foreign key relationship in Table Designer</span></span>  
  
1.  <span data-ttu-id="5b0c4-139">在对象资源管理器中，右键单击将位于关系的外键方的表，再单击“设计”。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-139">In Object Explorer, right-click the table that will be on the foreign-key side of the relationship and click **Design**.</span></span>  
  
     <span data-ttu-id="5b0c4-140">此时，将在表设计器中打开该表。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-140">The table opens in **Table Designer**.</span></span>  
  
2.  <span data-ttu-id="5b0c4-141">在 **表设计器** 菜单上，单击 **“关系”** 。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-141">From the **Table Designer** menu, click **Relationships**.</span></span>  
  
3.  <span data-ttu-id="5b0c4-142">在“外键关系”对话框中，单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-142">In the **Foreign-key Relationships** dialog box, click **Add**.</span></span>  
  
     <span data-ttu-id="5b0c4-143">“选定的关系”列表中将显示关系以及系统提供的名称，格式为 FK_\<*tablename*>_\<*tablename*>，其中 tablename 是外键表的名称。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-143">The relationship appears in the **Selected Relationship** list with a system-provided name in the format FK_\<*tablename*>_\<*tablename*>, where *tablename* is the name of the foreign key table.</span></span>  
  
4.  <span data-ttu-id="5b0c4-144">在 **“选定的关系”** 列表中单击该关系。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-144">Click the relationship in the **Selected Relationship** list.</span></span>  
  
5.  <span data-ttu-id="5b0c4-145">单击右侧网格中的“表和列规范”，再单击该属性右侧的省略号 (…) 。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-145">Click **Tables and Columns Specification** in the grid to the right and click the ellipses (**...**) to the right of the property.</span></span>  
  
6.  <span data-ttu-id="5b0c4-146">在“表和列”对话框中，从“主键”下拉列表中选择要位于关系主键方的表。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-146">In the **Tables and Columns** dialog box, in the **Primary Key** drop-down list, choose the table that will be on the primary-key side of the relationship.</span></span>  
  
7.  <span data-ttu-id="5b0c4-147">在下方的网格中，选择要分配给表的主键的列。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-147">In the grid beneath, choose the columns contributing to the table's primary key.</span></span> <span data-ttu-id="5b0c4-148">在每列左侧的相临网格单元格中，选择外键表的相应外键列。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-148">In the adjacent grid cell to the left of each column, choose the corresponding foreign-key column of the foreign-key table.</span></span>  
  
     <span data-ttu-id="5b0c4-149">**表设计器** 将为此关系提供一个建议名称。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-149">**Table Designer** suggests a name for the relationship.</span></span> <span data-ttu-id="5b0c4-150">若要更改此名称，请编辑 **“关系名”** 文本框的内容。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-150">To change this name, edit the contents of the **Relationship Name** text box.</span></span>  
  
8.  <span data-ttu-id="5b0c4-151">选择 **“确定”** 以创建该关系。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-151">Choose **OK** to create the relationship.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5b0c4-152">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5b0c4-152">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-foreign-key-in-a-new-table"></a><span data-ttu-id="5b0c4-153">在新表中创建外键</span><span class="sxs-lookup"><span data-stu-id="5b0c4-153">To create a foreign key in a new table</span></span>  
  
1.  <span data-ttu-id="5b0c4-154">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-154">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5b0c4-155">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-155">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5b0c4-156">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-156">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="5b0c4-157">此实例创建一个表并定义针对列 `TempID` 的外键约束，该列引用 `SalesReasonID` 表中的列 `Sales.SalesReason` 。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-157">The example creates a table and defines a foreign key constraint on the column `TempID` that references the column `SalesReasonID` in the `Sales.SalesReason` table.</span></span> <span data-ttu-id="5b0c4-158">ON DELETE CASCADE 和 ON UPDATE CASCADE 子句用于确保对 `Sales.SalesReason` 表的更改自动传播到 `Sales.TempSalesReason` 表。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-158">The ON DELETE CASCADE and ON UPDATE CASCADE clauses are used to ensure that changes made to `Sales.SalesReason` table are automatically propagated to the `Sales.TempSalesReason` table.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Sales.TempSalesReason (TempID int NOT NULL, Name nvarchar(50),   
    CONSTRAINT PK_TempSales PRIMARY KEY NONCLUSTERED (TempID),   
    CONSTRAINT FK_TempSales_SalesReason FOREIGN KEY (TempID)   
        REFERENCES Sales.SalesReason (SalesReasonID)   
        ON DELETE CASCADE  
        ON UPDATE CASCADE  
    );GO  
  
    ```  
  
#### <a name="to-create-a-foreign-key-in-an-existing-table"></a><span data-ttu-id="5b0c4-159">在现有表中创建外键</span><span class="sxs-lookup"><span data-stu-id="5b0c4-159">To create a foreign key in an existing table</span></span>  
  
1.  <span data-ttu-id="5b0c4-160">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-160">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5b0c4-161">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-161">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5b0c4-162">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-162">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="5b0c4-163">此示例针对 `TempID` 列创建外键并引用 `SalesReasonID` 表中的 `Sales.SalesReason` 列。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-163">The example creates a foreign key on the column `TempID` and references the column `SalesReasonID` in the `Sales.SalesReason` table.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Sales.TempSalesReason   
    ADD CONSTRAINT FK_TempSales_SalesReason FOREIGN KEY (TempID)   
        REFERENCES Sales.SalesReason (SalesReasonID)   
        ON DELETE CASCADE  
        ON UPDATE CASCADE  
    ;  
    GO  
  
    ```  
  
     <span data-ttu-id="5b0c4-164">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)、[CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql) 和 [table_constraint (Transact-SQL)](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5b0c4-164">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql), and [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).</span></span>  
  
  
