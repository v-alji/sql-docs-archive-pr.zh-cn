---
title: 从表中删除列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], deleting
- removing columns
- deleting columns
- dropping columns
ms.assetid: 0d8f6e4f-bc71-4fa3-8615-74249c8e072d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 62f9bca8ee53ae97bb1ac7f37e597b7814a0c370
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587731"
---
# <a name="delete-columns-from-a-table"></a><span data-ttu-id="048fd-102">从表中删除列</span><span class="sxs-lookup"><span data-stu-id="048fd-102">Delete Columns from a Table</span></span>
  <span data-ttu-id="048fd-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除表列。</span><span class="sxs-lookup"><span data-stu-id="048fd-103">This topic describes how to delete table columns in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="048fd-104">删除表中的某一列后，该列及其包含的所有数据都将从数据库中删除。</span><span class="sxs-lookup"><span data-stu-id="048fd-104">When you delete a column from a table, it and all the data it contains are deleted from the database.</span></span> <span data-ttu-id="048fd-105">此操作不可撤消。</span><span class="sxs-lookup"><span data-stu-id="048fd-105">This action cannot be undone.</span></span>  
  
 <span data-ttu-id="048fd-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="048fd-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="048fd-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="048fd-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="048fd-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="048fd-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="048fd-109">安全性</span><span class="sxs-lookup"><span data-stu-id="048fd-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="048fd-110">**使用以下工具从表中删除列：**</span><span class="sxs-lookup"><span data-stu-id="048fd-110">**To delete a column from a table, using:**</span></span>  
  
     [<span data-ttu-id="048fd-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="048fd-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="048fd-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="048fd-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="048fd-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="048fd-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="048fd-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="048fd-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="048fd-115">不能删除具有 CHECK 约束的列。</span><span class="sxs-lookup"><span data-stu-id="048fd-115">You cannot delete a column that has a CHECK constraint.</span></span> <span data-ttu-id="048fd-116">必须首先删除该约束。</span><span class="sxs-lookup"><span data-stu-id="048fd-116">You must first delete the constraint.</span></span>  
  
 <span data-ttu-id="048fd-117">不能删除具有 PRIMARY KEY 或 FOREIGN KEY 约束或者其他依赖关系的列，但在使用表设计器时例外。</span><span class="sxs-lookup"><span data-stu-id="048fd-117">You cannot delete a column that has PRIMARY KEY or FOREIGN KEY constraints or other dependencies except when using the Table Designer.</span></span> <span data-ttu-id="048fd-118">在使用对象资源管理器或 [!INCLUDE[tsql](../../includes/tsql-md.md)]时，必须首先删除该列上的所有依赖关系。</span><span class="sxs-lookup"><span data-stu-id="048fd-118">When using Object Explorer or [!INCLUDE[tsql](../../includes/tsql-md.md)], you must first remove all dependencies on the column.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="048fd-119">Security</span><span class="sxs-lookup"><span data-stu-id="048fd-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="048fd-120">权限</span><span class="sxs-lookup"><span data-stu-id="048fd-120">Permissions</span></span>  
 <span data-ttu-id="048fd-121">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="048fd-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="048fd-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="048fd-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-columns-by-using-object-explorer"></a><span data-ttu-id="048fd-123">通过使用对象资源管理器删除列</span><span class="sxs-lookup"><span data-stu-id="048fd-123">To delete columns by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="048fd-124">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="048fd-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="048fd-125">在“对象资源管理器”\*\*\*\* 中，右键单击要从其中删除列的表，然后选择“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="048fd-125">In **Object Explorer**, right-click the table from which you want to delete columns and choose **Delete**.</span></span>  
  
3.  <span data-ttu-id="048fd-126">在 **“删除对象”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="048fd-126">In **Delete Object** dialog box, click **OK**.</span></span>  
  
 <span data-ttu-id="048fd-127">如果该列包含约束或其他依赖关系，则在 **“删除对象”** 对话框中将显示一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="048fd-127">If the column contains constraints or other dependencies, an error message will display in the **Delete Object** dialog box.</span></span> <span data-ttu-id="048fd-128">通过删除引用的约束解决该错误。</span><span class="sxs-lookup"><span data-stu-id="048fd-128">Resolve the error by deleting the referenced constraints.</span></span>  
  
#### <a name="to-delete-columns-by-using-table-designer"></a><span data-ttu-id="048fd-129">通过使用表设计器删除列</span><span class="sxs-lookup"><span data-stu-id="048fd-129">To delete columns by using Table Designer</span></span>  
  
1.  <span data-ttu-id="048fd-130">在“对象资源管理器”  中，右键单击要从其中删除列的表，然后选择“设计”  。</span><span class="sxs-lookup"><span data-stu-id="048fd-130">In **Object Explorer**, right-click the table from which you want to delete columns and choose **Design**.</span></span>  
  
2.  <span data-ttu-id="048fd-131">右键单击要删除的列，然后从快捷菜单上选择“删除列”  。</span><span class="sxs-lookup"><span data-stu-id="048fd-131">Right-click the column you want to delete and choose **Delete Column** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="048fd-132">如果该列参与了关系（FOREIGN KEY 或 PRIMARY KEY），则将显示一条消息，提示您确认删除所选列及其关系。</span><span class="sxs-lookup"><span data-stu-id="048fd-132">If the column participates in a relationship (FOREIGN KEY or PRIMARY KEY), a message prompts you to confirm the deletion of the selected columns and their relationships.</span></span> <span data-ttu-id="048fd-133">选择“是”  。</span><span class="sxs-lookup"><span data-stu-id="048fd-133">Choose **Yes**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="048fd-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="048fd-134">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-columns"></a><span data-ttu-id="048fd-135">删除列</span><span class="sxs-lookup"><span data-stu-id="048fd-135">To delete columns</span></span>  
  
1.  <span data-ttu-id="048fd-136">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="048fd-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="048fd-137">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="048fd-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="048fd-138">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="048fd-138">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.doc_exb DROP COLUMN column_b ;  
    ```  
  
 <span data-ttu-id="048fd-139">如果该列包含约束或其他依赖关系，将返回一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="048fd-139">If the column contains constraints or other dependencies, an error message will be returned.</span></span> <span data-ttu-id="048fd-140">通过删除引用的约束解决该错误。</span><span class="sxs-lookup"><span data-stu-id="048fd-140">Resolve the error by deleting the referenced constraints.</span></span>  
  
 <span data-ttu-id="048fd-141">有关其他示例，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="048fd-141">For additional examples, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
##  <a name="FollowUp"></a>  
