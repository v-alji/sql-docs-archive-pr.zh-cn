---
title: 使用 INSERT 和 UPDATE 语句禁用外键约束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
- UPDATE statement [SQL Server], foreign key constraints
- INSERT statement [SQL Server], foreign key constraints
ms.assetid: 029168d7-085e-4b13-9b86-5644b67c6e24
author: stevestein
ms.author: sstein
ms.openlocfilehash: e91328f4f12f2a0a27f397c7bd95390a505f3998
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581155"
---
# <a name="disable-foreign-key-constraints-with-insert-and-update-statements"></a><span data-ttu-id="55dc5-102">使用 INSERT 和 UPDATE 语句禁用外键约束</span><span class="sxs-lookup"><span data-stu-id="55dc5-102">Disable Foreign Key Constraints with INSERT and UPDATE Statements</span></span>
  <span data-ttu-id="55dc5-103">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，您可以通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]，在 INSERT 和 UPDATE 事务期间禁用外键约束。</span><span class="sxs-lookup"><span data-stu-id="55dc5-103">You can disable a foreign key constraint during INSERT and UPDATE transactions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="55dc5-104">如果您知道新数据将与现有约束冲突或者如果约束仅适用于数据库中已有的数据，则可选择此选项。</span><span class="sxs-lookup"><span data-stu-id="55dc5-104">Use this option if you know that new data will violate the existing constraint or if the constraint applies only to the data already in the database.</span></span>  
  
 <span data-ttu-id="55dc5-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="55dc5-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="55dc5-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="55dc5-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="55dc5-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="55dc5-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="55dc5-108">安全性</span><span class="sxs-lookup"><span data-stu-id="55dc5-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="55dc5-109">**对 INSERT 和 UPDATE 语句禁用外键约束，使用：**</span><span class="sxs-lookup"><span data-stu-id="55dc5-109">**To disable a foreign key constraint for INSERT and UPDATE statements, using:**</span></span>  
  
     [<span data-ttu-id="55dc5-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="55dc5-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="55dc5-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="55dc5-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="55dc5-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="55dc5-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="55dc5-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="55dc5-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="55dc5-114">在禁用这些约束后，在将来插入或更新列时，将不会根据约束条件进行验证。</span><span class="sxs-lookup"><span data-stu-id="55dc5-114">After you disable these constraints, future inserts or updates to the column will not be validated against the constraint conditions.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="55dc5-115">Security</span><span class="sxs-lookup"><span data-stu-id="55dc5-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="55dc5-116">权限</span><span class="sxs-lookup"><span data-stu-id="55dc5-116">Permissions</span></span>  
 <span data-ttu-id="55dc5-117">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="55dc5-117">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="55dc5-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="55dc5-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a><span data-ttu-id="55dc5-119">对 INSERT 和 UPDATE 语句禁用外键约束</span><span class="sxs-lookup"><span data-stu-id="55dc5-119">To disable a foreign key constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="55dc5-120">在 **“对象资源管理器”** 中，展开具有约束的表，再展开 **“键”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="55dc5-120">In **Object Explorer**, expand the table with the constraint and then expand the **Keys** folder.</span></span>  
  
2.  <span data-ttu-id="55dc5-121">右键单击该约束，再选择“修改”  。</span><span class="sxs-lookup"><span data-stu-id="55dc5-121">Right-click the constraint and select **Modify**.</span></span>  
  
3.  <span data-ttu-id="55dc5-122">在“表设计器”  下的网格中，单击  “强制外键约束”，然后从下拉菜单中选择  “否”。</span><span class="sxs-lookup"><span data-stu-id="55dc5-122">In the grid under **Table Designer**, click **Enforce Foreign Key Constraint** and select **No** from the drop-down menu.</span></span>  
  
4.  <span data-ttu-id="55dc5-123">单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="55dc5-123">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="55dc5-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="55dc5-124">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a><span data-ttu-id="55dc5-125">对 INSERT 和 UPDATE 语句禁用外键约束</span><span class="sxs-lookup"><span data-stu-id="55dc5-125">To disable a foreign key constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="55dc5-126">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="55dc5-126">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="55dc5-127">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="55dc5-127">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="55dc5-128">将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="55dc5-128">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT FK_PurchaseOrderHeader_Employee_EmployeeID;  
    GO  
    ```  
  
 <span data-ttu-id="55dc5-129">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="55dc5-129">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
