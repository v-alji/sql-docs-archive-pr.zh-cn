---
title: 创建 CHECK 约束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table constraints [SQL Server]
- attaching check constraints
- columns [SQL Server], constraints
- constraints [SQL Server], check
- CHECK constraints, attaching
ms.assetid: b8756304-9454-4d39-996a-64516831b7df
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7795ee6eca85a22bdd4e84c90ce49a9449ddff28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591840"
---
# <a name="create-check-constraints"></a><span data-ttu-id="99f1b-102">创建 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="99f1b-102">Create Check Constraints</span></span>
  <span data-ttu-id="99f1b-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在表中创建 CHECK 约束以便指定在 [!INCLUDE[tsql](../../includes/tsql-md.md)]的一列或多列中可接受的数据值。</span><span class="sxs-lookup"><span data-stu-id="99f1b-103">You can create a check constraint in a table to specify the data values that are acceptable in one or more columns in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="99f1b-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="99f1b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="99f1b-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="99f1b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="99f1b-106">安全性</span><span class="sxs-lookup"><span data-stu-id="99f1b-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="99f1b-107">**使用以下工具创建新的 CHECK 约束：**</span><span class="sxs-lookup"><span data-stu-id="99f1b-107">**To create a new check constraint using:**</span></span>  
  
     [<span data-ttu-id="99f1b-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="99f1b-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="99f1b-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="99f1b-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="99f1b-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="99f1b-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="99f1b-111">Security</span><span class="sxs-lookup"><span data-stu-id="99f1b-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="99f1b-112">权限</span><span class="sxs-lookup"><span data-stu-id="99f1b-112">Permissions</span></span>  
 <span data-ttu-id="99f1b-113">需要具有表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="99f1b-113">Requires ALTER permissions on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="99f1b-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="99f1b-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-new-check-constraint"></a><span data-ttu-id="99f1b-115">创建新的 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="99f1b-115">To create a new check constraint</span></span>  
  
1.  <span data-ttu-id="99f1b-116">在  “对象资源管理器”中，展开要为其添加 CHECK 约束的表，右键单击  “约束”，然后单击  “新建约束”。</span><span class="sxs-lookup"><span data-stu-id="99f1b-116">In **Object Explorer**, expand the table to which you want to add a check constraint, right-click **Constraints** and click **New Constraint**.</span></span>  
  
2.  <span data-ttu-id="99f1b-117">在“CHECK 约束”对话框中，单击“表达式”字段，然后单击省略号 (…)    。</span><span class="sxs-lookup"><span data-stu-id="99f1b-117">In the **Check Constraints** dialog box, click in the **Expression** field and then click the ellipses **(...)**.</span></span>  
  
3.  <span data-ttu-id="99f1b-118">在 **“CHECK 约束表达式”** 对话框中，键入 CHECK 约束的 SQL 表达式。</span><span class="sxs-lookup"><span data-stu-id="99f1b-118">In the **Check Constraint Expression** dialog box, type the SQL expressions for the check constraint.</span></span> <span data-ttu-id="99f1b-119">例如，若要将 `SellEndDate` 表的 `Product` 列中的条目限制为大于等于 `SellStartDate` 列中的日期的值，或者为 NULL 值，则键入：</span><span class="sxs-lookup"><span data-stu-id="99f1b-119">For example, to limit the entries in the `SellEndDate` column of the `Product` table to a value that is either greater than or equal to the date in the `SellStartDate` column or is a NULL value, type:</span></span>  
  
    ```  
    SellEndDate >= SellStartDate OR SellEndDate IS NULL  
    ```  
  
     <span data-ttu-id="99f1b-120">或者，如果要求 `zip` 列中的项为 5 位数，请键入：</span><span class="sxs-lookup"><span data-stu-id="99f1b-120">Or, to require entries in the `zip` column to be 5 digits, type:</span></span>  
  
    ```  
    zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="99f1b-121">确保将任何非数字约束值包含在单引号 (') 中。</span><span class="sxs-lookup"><span data-stu-id="99f1b-121">Make sure to enclose any non-numeric constraint values in single quotation marks (').</span></span>  
  
4.  <span data-ttu-id="99f1b-122">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="99f1b-122">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="99f1b-123">在  “标识”类别中，您可以更改 CHECK 约束的名称并且为该约束添加说明（扩展属性）。</span><span class="sxs-lookup"><span data-stu-id="99f1b-123">In the **Identity** category, you can change the name of the check constraint and add a description (extended property) for the constraint.</span></span>  
  
6.  <span data-ttu-id="99f1b-124">在 **“表设计器”** 类别中，您可以设置何时强制约束。</span><span class="sxs-lookup"><span data-stu-id="99f1b-124">In the **Table Designer** category, you can set when the constraint is enforced.</span></span>  
  
    |<span data-ttu-id="99f1b-125">**发件人：**</span><span class="sxs-lookup"><span data-stu-id="99f1b-125">**To:**</span></span>|<span data-ttu-id="99f1b-126">**在以下字段中选择“是”：**</span><span class="sxs-lookup"><span data-stu-id="99f1b-126">**Select Yes in the Following Fields:**</span></span>|  
    |-------------|---------------------------------------------|  
    |<span data-ttu-id="99f1b-127">对在创建约束前存在的数据测试约束</span><span class="sxs-lookup"><span data-stu-id="99f1b-127">Test the constraint on data that existed before you created the constraint</span></span>|<span data-ttu-id="99f1b-128">**在创建或启用时检查现有数据**</span><span class="sxs-lookup"><span data-stu-id="99f1b-128">**Check Existing Data On Creation Or Enabling**</span></span>|  
    |<span data-ttu-id="99f1b-129">在此表上发生复制操作时强制约束</span><span class="sxs-lookup"><span data-stu-id="99f1b-129">Enforce the constraint whenever a replication operation occurs on this table</span></span>|<span data-ttu-id="99f1b-130">**强制用于复制**</span><span class="sxs-lookup"><span data-stu-id="99f1b-130">**Enforce For Replication**</span></span>|  
    |<span data-ttu-id="99f1b-131">在此表中插入或更新行时强制约束</span><span class="sxs-lookup"><span data-stu-id="99f1b-131">Enforce the constraint whenever a row of this table is inserted or updated</span></span>|<span data-ttu-id="99f1b-132">**强制用于 INSERT 和 UPDATE**</span><span class="sxs-lookup"><span data-stu-id="99f1b-132">**Enforce For INSERTs And UPDATEs**</span></span>|  
  
7.  <span data-ttu-id="99f1b-133">单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="99f1b-133">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="99f1b-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="99f1b-134">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-new-check-constraint"></a><span data-ttu-id="99f1b-135">创建新的 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="99f1b-135">To create a new check constraint</span></span>  
  
1.  <span data-ttu-id="99f1b-136">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="99f1b-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="99f1b-137">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="99f1b-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="99f1b-138">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="99f1b-138">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER TABLE dbo.DocExc   
       ADD ColumnD int NULL   
       CONSTRAINT CHK_ColumnD_DocExc   
       CHECK (ColumnD > 10 AND ColumnD < 50);  
    GO  
    -- Adding values that will pass the check constraint  
    INSERT INTO dbo.DocExc (ColumnD) VALUES (49);  
    GO  
    -- Adding values that will fail the check constraint  
    INSERT INTO dbo.DocExc (ColumnD) VALUES (55);  
    GO  
  
    ```  
  
 <span data-ttu-id="99f1b-139">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="99f1b-139">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
