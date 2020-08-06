---
title: 删除主键 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing primary keys
- deleting primary keys
- primary keys [SQL Server], deleting
ms.assetid: c472e465-7bdd-4d74-8fc9-e47fca007ccb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 44fa1271143f813364bfd2109f8147f1d04294a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591828"
---
# <a name="delete-primary-keys"></a><span data-ttu-id="9b03e-102">删除主键</span><span class="sxs-lookup"><span data-stu-id="9b03e-102">Delete Primary Keys</span></span>
  <span data-ttu-id="9b03e-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除主键。</span><span class="sxs-lookup"><span data-stu-id="9b03e-103">You can delete (drop) a primary key in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="9b03e-104">在删除主键时，也将删除相应的索引。</span><span class="sxs-lookup"><span data-stu-id="9b03e-104">When the primary key is deleted, the corresponding index is deleted.</span></span>  
  
 <span data-ttu-id="9b03e-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="9b03e-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9b03e-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="9b03e-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9b03e-107">安全性</span><span class="sxs-lookup"><span data-stu-id="9b03e-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9b03e-108">**使用以下工具删除主键：**</span><span class="sxs-lookup"><span data-stu-id="9b03e-108">**To delete a primary key using:**</span></span>  
  
     [<span data-ttu-id="9b03e-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9b03e-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9b03e-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9b03e-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9b03e-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="9b03e-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9b03e-112">Security</span><span class="sxs-lookup"><span data-stu-id="9b03e-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9b03e-113">权限</span><span class="sxs-lookup"><span data-stu-id="9b03e-113">Permissions</span></span>  
 <span data-ttu-id="9b03e-114">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="9b03e-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9b03e-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9b03e-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-primary-key-constraint-using-object-explorer"></a><span data-ttu-id="9b03e-116">使用对象资源管理器删除主键约束</span><span class="sxs-lookup"><span data-stu-id="9b03e-116">To delete a primary key constraint using Object Explorer</span></span>  
  
1.  <span data-ttu-id="9b03e-117">在对象资源管理器中，展开包含主键的表，再展开 **“键”** 。</span><span class="sxs-lookup"><span data-stu-id="9b03e-117">In Object Explorer, expand the table that contains the primary key and then expand **Keys**.</span></span>  
  
2.  <span data-ttu-id="9b03e-118">右键单击该键，然后选择“删除”  。</span><span class="sxs-lookup"><span data-stu-id="9b03e-118">Right-click the key and select **Delete**.</span></span>  
  
3.  <span data-ttu-id="9b03e-119">在 **“删除对象”** 对话框中，确认指定了正确的键，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="9b03e-119">In the **Delete Object** dialog box, verify the correct key is specified and click **OK**.</span></span>  
  
#### <a name="to-delete-a-primary-key-constraint-using-table-designer"></a><span data-ttu-id="9b03e-120">使用表设计器删除主键约束</span><span class="sxs-lookup"><span data-stu-id="9b03e-120">To delete a primary key constraint using Table Designer</span></span>  
  
1.  <span data-ttu-id="9b03e-121">在对象资源管理器中，右键单击具有主键的表，再单击“设计”  。</span><span class="sxs-lookup"><span data-stu-id="9b03e-121">In Object Explorer, right-click the table with the primary key, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="9b03e-122">在表网格中右键单击包含主键的行，再选择“删除主键”  以将该设置从启用切换到禁用。</span><span class="sxs-lookup"><span data-stu-id="9b03e-122">In the table grid, right-click the row with the primary key and choose **Remove Primary Key** to toggle the setting from on to off.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9b03e-123">若要撤消此操作，请关闭该表而不保存更改。</span><span class="sxs-lookup"><span data-stu-id="9b03e-123">To undo this action, close the table without saving the changes.</span></span> <span data-ttu-id="9b03e-124">若要撤消删除主键操作，就无法避免丢失对表做出的所有其他更改。</span><span class="sxs-lookup"><span data-stu-id="9b03e-124">Deleting a primary key cannot be undone without losing all other changes made to the table.</span></span>  
  
3.  <span data-ttu-id="9b03e-125">在“文件”  菜单上，单击“保存”  以保存表名  。</span><span class="sxs-lookup"><span data-stu-id="9b03e-125">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9b03e-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9b03e-126">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-primary-key-constraint"></a><span data-ttu-id="9b03e-127">删除主键约束</span><span class="sxs-lookup"><span data-stu-id="9b03e-127">To delete a primary key constraint</span></span>  
  
1.  <span data-ttu-id="9b03e-128">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="9b03e-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9b03e-129">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="9b03e-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9b03e-130">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="9b03e-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="9b03e-131">该示例首先标识主键约束的名称，然后删除该约束。</span><span class="sxs-lookup"><span data-stu-id="9b03e-131">The example first identifies the name of the primary key constraint and then deletes the constraint.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Return the name of primary key.  
    SELECT name  
    FROM sys.key_constraints  
    WHERE type = 'PK' AND OBJECT_NAME(parent_object_id) = N'TransactionHistoryArchive';  
    GO  
    -- Delete the primary key constraint.  
    ALTER TABLE Production.TransactionHistoryArchive  
    DROP CONSTRAINT PK_TransactionHistoryArchive_TransactionID;   
    GO  
    ```  
  
 <span data-ttu-id="9b03e-132">有关详细信息，请参阅 [ALTER TABLE (Transact SQL) ](/sql/t-sql/statements/alter-table-transact-sql) 和 [sys.key_constraints (Transact SQL)](/sql/relational-databases/system-catalog-views/sys-key-constraints-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="9b03e-132">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) and [sys.key_constraints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-constraints-transact-sql)</span></span>  
  
###  <a name="TsqlExample"></a>  
