---
title: 删除唯一约束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing constraints
- UNIQUE constraints [SQL Server], deleting
- constraints [SQL Server], deleting
- deleting constraints
- constraints [SQL Server], unique
ms.assetid: 71e563fc-f5d7-4c2e-a42f-f0695a831f32
author: stevestein
ms.author: sstein
ms.openlocfilehash: f2fe2264aed4eb2f292a6bd1e4e565cebe2a833f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588399"
---
# <a name="delete-unique-constraints"></a><span data-ttu-id="20ac9-102">删除唯一约束</span><span class="sxs-lookup"><span data-stu-id="20ac9-102">Delete Unique Constraints</span></span>
  <span data-ttu-id="20ac9-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 删除 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的唯一约束。</span><span class="sxs-lookup"><span data-stu-id="20ac9-103">You can delete a unique constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="20ac9-104">删除唯一约束将删除对在约束表达式所包含的列或列组合中输入的值的唯一性要求，并且会删除相应的唯一索引。</span><span class="sxs-lookup"><span data-stu-id="20ac9-104">Deleting a unique constraint removes the requirement for uniqueness for values entered in the column or combination of columns included in the constraint expression and deletes the corresponding unique index.</span></span>  
  
 <span data-ttu-id="20ac9-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="20ac9-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="20ac9-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="20ac9-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="20ac9-107">安全性</span><span class="sxs-lookup"><span data-stu-id="20ac9-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="20ac9-108">**若要删除唯一约束，请使用：**</span><span class="sxs-lookup"><span data-stu-id="20ac9-108">**To delete a unique constraint, using:**</span></span>  
  
     [<span data-ttu-id="20ac9-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="20ac9-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="20ac9-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="20ac9-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="20ac9-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="20ac9-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="20ac9-112">Security</span><span class="sxs-lookup"><span data-stu-id="20ac9-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="20ac9-113">权限</span><span class="sxs-lookup"><span data-stu-id="20ac9-113">Permissions</span></span>  
 <span data-ttu-id="20ac9-114">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="20ac9-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="20ac9-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="20ac9-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-unique-constraint-using-object-explorer"></a><span data-ttu-id="20ac9-116">使用对象资源管理器删除唯一约束</span><span class="sxs-lookup"><span data-stu-id="20ac9-116">To delete a unique constraint using Object Explorer</span></span>  
  
1.  <span data-ttu-id="20ac9-117">在对象资源管理器中，展开包含唯一约束的表，再展开 **“约束”** 。</span><span class="sxs-lookup"><span data-stu-id="20ac9-117">In Object Explorer, expand the table that contains the unique constraint and then expand **Constraints**.</span></span>  
  
2.  <span data-ttu-id="20ac9-118">右键单击该键，然后选择“删除”  。</span><span class="sxs-lookup"><span data-stu-id="20ac9-118">Right-click the key and select **Delete**.</span></span>  
  
3.  <span data-ttu-id="20ac9-119">在 **“删除对象”** 对话框中，确认指定了正确的键，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="20ac9-119">In the **Delete Object** dialog box, verify the correct key is specified and click **OK**.</span></span>  
  
#### <a name="to-delete-a-unique-constraint-using-table-designer"></a><span data-ttu-id="20ac9-120">使用表设计器删除唯一约束</span><span class="sxs-lookup"><span data-stu-id="20ac9-120">To delete a unique constraint using Table Designer</span></span>  
  
1.  <span data-ttu-id="20ac9-121">在“对象资源管理器”  中，右键单击具有唯一约束的表，然后单击“设计”  。</span><span class="sxs-lookup"><span data-stu-id="20ac9-121">In **Object Explorer**, right-click the table with the unique constraint, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="20ac9-122">在“表设计器”  菜单上，单击“索引/键”  。</span><span class="sxs-lookup"><span data-stu-id="20ac9-122">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
3.  <span data-ttu-id="20ac9-123">在“索引/键”  对话框中，从“选定的主键/唯一键和索引”  列表中选择唯一键。</span><span class="sxs-lookup"><span data-stu-id="20ac9-123">In the **Indexes/Keys** dialog box, select the unique key in the **Selected Primary/Unique Key and Index** list.</span></span>  
  
4.  <span data-ttu-id="20ac9-124">单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="20ac9-124">Click **Delete**.</span></span>  
  
5.  <span data-ttu-id="20ac9-125">在“文件”菜单上，单击“保存表名称”    。</span><span class="sxs-lookup"><span data-stu-id="20ac9-125">On the **File** menu, click **Save** _table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="20ac9-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="20ac9-126">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-unique-constraint"></a><span data-ttu-id="20ac9-127">删除唯一约束</span><span class="sxs-lookup"><span data-stu-id="20ac9-127">To delete a unique constraint</span></span>  
  
1.  <span data-ttu-id="20ac9-128">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="20ac9-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="20ac9-129">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="20ac9-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="20ac9-130">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="20ac9-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Return the name of unique constraint.  
    SELECT name  
    FROM sys.objects  
    WHERE type = 'UQ' AND OBJECT_NAME(parent_object_id) = N' DocExc';  
    GO  
    -- Delete the unique constraint.  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT UNQ_ColumnB_DocExc;  
    GO  
    ```  
  
 <span data-ttu-id="20ac9-131">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql) 和 [sys.objects (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="20ac9-131">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) and [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
