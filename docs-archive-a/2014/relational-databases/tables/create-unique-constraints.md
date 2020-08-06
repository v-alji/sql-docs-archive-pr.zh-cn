---
title: 创建唯一约束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- UNIQUE constraints [SQL Server], creating
- constraints [SQL Server], creating
- constraints [SQL Server], unique
ms.assetid: a86f9d6f-f242-43be-b65d-b3435b71b62a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 252de63f965f98734a6d62d94bfff9dc5774cab6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692335"
---
# <a name="create-unique-constraints"></a><span data-ttu-id="e4bb8-102">创建唯一约束</span><span class="sxs-lookup"><span data-stu-id="e4bb8-102">Create Unique Constraints</span></span>
  <span data-ttu-id="e4bb8-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中创建唯一约束，以便确保在未参与主键的特定列中不输入重复值。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-103">You can create a unique constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] to ensure no duplicate values are entered in specific columns that do not participate in a primary key.</span></span> <span data-ttu-id="e4bb8-104">创建唯一约束会自动创建相应的唯一索引。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-104">Creating a unique constraint automatically creates a corresponding unique index.</span></span>  
  
 <span data-ttu-id="e4bb8-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="e4bb8-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e4bb8-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="e4bb8-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e4bb8-107">安全性</span><span class="sxs-lookup"><span data-stu-id="e4bb8-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e4bb8-108">**使用以下工具创建唯一约束：**</span><span class="sxs-lookup"><span data-stu-id="e4bb8-108">**To create a unique constraint, using:**</span></span>  
  
     [<span data-ttu-id="e4bb8-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e4bb8-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e4bb8-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e4bb8-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e4bb8-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="e4bb8-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e4bb8-112">Security</span><span class="sxs-lookup"><span data-stu-id="e4bb8-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e4bb8-113">权限</span><span class="sxs-lookup"><span data-stu-id="e4bb8-113">Permissions</span></span>  
 <span data-ttu-id="e4bb8-114">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e4bb8-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e4bb8-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-unique-constraint"></a><span data-ttu-id="e4bb8-116">创建唯一约束</span><span class="sxs-lookup"><span data-stu-id="e4bb8-116">To create a unique constraint</span></span>  
  
1.  <span data-ttu-id="e4bb8-117">在“对象资源管理器”\*\*\*\* 中，右键单击要为其添加唯一约束的表，再单击“设计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-117">In **Object Explorer**, right-click the table to which you want to add a unique constraint, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="e4bb8-118">在 "**表设计器**" 菜单上，单击 "**索引/键**"。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-118">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
3.  <span data-ttu-id="e4bb8-119">在“索引/键”\*\*\*\* 对话框中，单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-119">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="e4bb8-120">在“常规”\*\*\*\* 下的网格中，单击“类型”\*\*\*\*，然后从该属性右侧的下拉列表框中选择“唯一键”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-120">In the grid under **General**, click **Type** and choose **Unique Key** from the drop-down list box to the right of the property.</span></span>  
  
5.  <span data-ttu-id="e4bb8-121">在“文件”菜单上，单击“保存表名称”\*\*\*\*\*\*\*\*__。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-121">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e4bb8-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e4bb8-122">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-unique-constraint"></a><span data-ttu-id="e4bb8-123">创建唯一约束</span><span class="sxs-lookup"><span data-stu-id="e4bb8-123">To create a unique constraint</span></span>  
  
1.  <span data-ttu-id="e4bb8-124">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e4bb8-125">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e4bb8-126">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-126">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e4bb8-127">该示例将创建表 `TransactionHistoryArchive4` ，并且在列 `TransactionID`上创建唯一约束。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-127">The example creates the table `TransactionHistoryArchive4` and creates a unique constraint on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive4  
     (  
       TransactionID int NOT NULL,   
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)   
    );   
    GO  
  
    ```  
  
#### <a name="to-create-a-unique-constraint-on-an-existing-table"></a><span data-ttu-id="e4bb8-128">在现有表中创建唯一约束</span><span class="sxs-lookup"><span data-stu-id="e4bb8-128">To create a unique constraint on an existing table</span></span>  
  
1.  <span data-ttu-id="e4bb8-129">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e4bb8-130">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e4bb8-131">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-131">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e4bb8-132">该示例在表 `PasswordHash` 中的 `PasswordSalt` 和 `Person.Password`列上创建唯一约束。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-132">The example creates a unique constraint on the columns `PasswordHash` and `PasswordSalt` in the table `Person.Password`.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    ALTER TABLE Person.Password   
    ADD CONSTRAINT AK_Password UNIQUE (PasswordHash, PasswordSalt);   
    GO  
  
    ```  
  
#### <a name="to-create-a-unique-constraint-in-an-new-table"></a><span data-ttu-id="e4bb8-133">在新表中创建唯一约束</span><span class="sxs-lookup"><span data-stu-id="e4bb8-133">To create a unique constraint in an new table</span></span>  
  
1.  <span data-ttu-id="e4bb8-134">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e4bb8-135">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e4bb8-136">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e4bb8-137">该示例创建一个表并在 `TransactionID`列上定义唯一约束。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-137">The example creates a table and defines a unique constraint on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive2  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)  
    );  
    GO  
  
    ```  
  
     <span data-ttu-id="e4bb8-138">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)、[CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql) 和 [table_constraint (Transact-SQL)](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e4bb8-138">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql), and [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
