---
title: 创建主键 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- primary keys [SQL Server], creating
ms.assetid: 85c623ca-4656-4d70-a9db-ee4d897cd214
author: stevestein
ms.author: sstein
ms.openlocfilehash: c515ef8f978b41225ff45e87646b0aa7a9706a34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591837"
---
# <a name="create-primary-keys"></a><span data-ttu-id="e1226-102">创建主键</span><span class="sxs-lookup"><span data-stu-id="e1226-102">Create Primary Keys</span></span>
  <span data-ttu-id="e1226-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中定义主键。</span><span class="sxs-lookup"><span data-stu-id="e1226-103">You can define a primary key in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e1226-104">创建主键将自动创建相应的唯一索引、聚集索引或非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="e1226-104">Creating a primary key automatically creates a corresponding unique, clustered or nonclustered index.</span></span>  
  
 <span data-ttu-id="e1226-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="e1226-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e1226-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="e1226-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e1226-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e1226-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e1226-108">安全性</span><span class="sxs-lookup"><span data-stu-id="e1226-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e1226-109">**创建主键，使用：**</span><span class="sxs-lookup"><span data-stu-id="e1226-109">**To create a primary key, using:**</span></span>  
  
     [<span data-ttu-id="e1226-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e1226-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e1226-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e1226-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e1226-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="e1226-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e1226-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e1226-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e1226-114">一个表只能包含一个 PRIMARY KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="e1226-114">A table can contain only one PRIMARY KEY constraint.</span></span>  
  
-   <span data-ttu-id="e1226-115">在 PRIMARY KEY 约束中定义的所有列都必须定义为 NOT NULL。</span><span class="sxs-lookup"><span data-stu-id="e1226-115">All columns defined within a PRIMARY KEY constraint must be defined as NOT NULL.</span></span> <span data-ttu-id="e1226-116">如果没有指定为 Null 性，则加入 PRIMARY KEY 约束的所有列的为 Null 性都将设置为 NOT NULL。</span><span class="sxs-lookup"><span data-stu-id="e1226-116">If nullability is not specified, all columns participating in a PRIMARY KEY constraint have their nullability set to NOT NULL.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e1226-117">Security</span><span class="sxs-lookup"><span data-stu-id="e1226-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e1226-118">权限</span><span class="sxs-lookup"><span data-stu-id="e1226-118">Permissions</span></span>  
 <span data-ttu-id="e1226-119">使用主键创建新表需要在数据库中具有 CREATE TABLE 权限，并对在其中创建表的架构具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="e1226-119">Creating a new table with a primary key requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span>  
  
 <span data-ttu-id="e1226-120">在某一现有表中创建主键需要对该表具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="e1226-120">Creating a primary key in an existing table requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e1226-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e1226-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-primary-key"></a><span data-ttu-id="e1226-122">创建主键</span><span class="sxs-lookup"><span data-stu-id="e1226-122">To create a primary key</span></span>  
  
1.  <span data-ttu-id="e1226-123">在对象资源管理器中，右键单击要向其添加唯一约束的表，然后单击 "**设计**"。</span><span class="sxs-lookup"><span data-stu-id="e1226-123">In Object Explorer, right-click the table to which you want to add a unique constraint, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="e1226-124">在 **“表设计器”** 中，单击要定义为主键的数据库列的行选择器。</span><span class="sxs-lookup"><span data-stu-id="e1226-124">In **Table Designer**, click the row selector for the database column you want to define as the primary key.</span></span> <span data-ttu-id="e1226-125">若要选择多个列，请在单击其他列的行选择器时按住 Ctrl 键。</span><span class="sxs-lookup"><span data-stu-id="e1226-125">If you want to select multiple columns, hold down the CTRL key while you click the row selectors for the other columns.</span></span>  
  
3.  <span data-ttu-id="e1226-126">右键单击该列的行选择器，然后选择“设置主键”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e1226-126">Right-click the row selector for the column and select **Set Primary Key**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="e1226-127">若要重新定义主键，则必须首先删除与现有主键之间的任何关系，然后才能创建新主键。</span><span class="sxs-lookup"><span data-stu-id="e1226-127">If you want to redefine the primary key, any relationships to the existing primary key must be deleted before the new primary key can be created.</span></span> <span data-ttu-id="e1226-128">此时，将显示一条消息警告您：作为该过程的一部分，将自动删除现有关系。</span><span class="sxs-lookup"><span data-stu-id="e1226-128">A message will warn you that existing relationships will be automatically deleted as part of this process.</span></span>  
  
 <span data-ttu-id="e1226-129">主键列由其行选择器中的主键符号标识。</span><span class="sxs-lookup"><span data-stu-id="e1226-129">A primary key column is identified by a primary key symbol in its row selector.</span></span>  
  
 <span data-ttu-id="e1226-130">如果主键由多个列组成，则其中一个列将允许重复值，但是主键中所有列的值的各种组合必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e1226-130">If a primary key consists of more than one column, duplicate values are allowed in one column, but each combination of values from all the columns in the primary key must be unique.</span></span>  
  
 <span data-ttu-id="e1226-131">如果定义复合键，则主键中列的顺序将与表中显示的列顺序相匹配。</span><span class="sxs-lookup"><span data-stu-id="e1226-131">If you define a compound key, the order of columns in the primary key matches the order of columns as shown in the table.</span></span> <span data-ttu-id="e1226-132">不过，您可以在创建主键之后更改列的顺序。</span><span class="sxs-lookup"><span data-stu-id="e1226-132">However, you can change the order of columns after the primary key is created.</span></span> <span data-ttu-id="e1226-133">有关详细信息，请参阅 [修改主键](modify-primary-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="e1226-133">For more information, see [Modify Primary Keys](modify-primary-keys.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e1226-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e1226-134">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-primary-key-in-an-existing-table"></a><span data-ttu-id="e1226-135">在现有表中创建主键</span><span class="sxs-lookup"><span data-stu-id="e1226-135">To create a primary key in an existing table</span></span>  
  
1.  <span data-ttu-id="e1226-136">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="e1226-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e1226-137">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="e1226-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e1226-138">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="e1226-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e1226-139">此示例对列 `TransactionID`创建了一个主键。</span><span class="sxs-lookup"><span data-stu-id="e1226-139">The example creates a primary key on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Production.TransactionHistoryArchive   
    ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID);  
    GO  
  
    ```  
  
#### <a name="to-create-a-primary-key-in-a-new-table"></a><span data-ttu-id="e1226-140">在新表中创建主键</span><span class="sxs-lookup"><span data-stu-id="e1226-140">To create a primary key in a new table</span></span>  
  
1.  <span data-ttu-id="e1226-141">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="e1226-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e1226-142">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="e1226-142">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e1226-143">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="e1226-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e1226-144">此示例将创建一个表并针对 `TransactionID`列定义一个主键。</span><span class="sxs-lookup"><span data-stu-id="e1226-144">The example creates a table and defines a primary key on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive1  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)  
    );  
    GO  
  
    ```  
  
     <span data-ttu-id="e1226-145">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)、[CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql) 和 [table_constraint (Transact-SQL)](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e1226-145">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql), and [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
