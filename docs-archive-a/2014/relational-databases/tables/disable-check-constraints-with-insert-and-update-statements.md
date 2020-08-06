---
title: 对 INSERT 和 UPDATE 语句禁用 CHECK 约束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- CHECK constraints, disabling
- constraints [SQL Server], disabling
- disabling constraints
- constraints [SQL Server], check
ms.assetid: c7287ad1-50d2-4e80-bc0c-b5570f7e5f69
author: stevestein
ms.author: sstein
ms.openlocfilehash: 780a2c1bfd9f21c71367ad61f200ec19ab44a608
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586566"
---
# <a name="disable-check-constraints-with-insert-and-update-statements"></a><span data-ttu-id="ad714-102">对 INSERT 和 UPDATE 语句禁用 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="ad714-102">Disable Check Constraints with INSERT and UPDATE Statements</span></span>
  <span data-ttu-id="ad714-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中禁用针对 INSERT 和 UPDATE 事务的 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="ad714-103">You can disable a check constraint for INSERT and UPDATE transactions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ad714-104">在禁用该 CHECK 约束后，在将来插入或更新列时，将不会根据约束条件进行验证。</span><span class="sxs-lookup"><span data-stu-id="ad714-104">After you disable the check constraints, future inserts or updates to the column will not be validated against the constraint conditions.</span></span> <span data-ttu-id="ad714-105">如果您知道新数据将与现有约束冲突或者如果约束仅适用于数据库中已有的数据，则可选择此选项。</span><span class="sxs-lookup"><span data-stu-id="ad714-105">Use this option if you know that new data will violate the existing constraint or if the constraint applies only to the data already in the database.</span></span>  
  
 <span data-ttu-id="ad714-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ad714-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ad714-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ad714-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ad714-108">安全性</span><span class="sxs-lookup"><span data-stu-id="ad714-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ad714-109">**使用以下工具为 INSERT 和 UPDATE 语句禁用 CHECK 约束：**</span><span class="sxs-lookup"><span data-stu-id="ad714-109">**To disable a check constraint for INSERT and UPDATE statements, using:**</span></span>  
  
     [<span data-ttu-id="ad714-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ad714-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ad714-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ad714-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ad714-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="ad714-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ad714-113">Security</span><span class="sxs-lookup"><span data-stu-id="ad714-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ad714-114">权限</span><span class="sxs-lookup"><span data-stu-id="ad714-114">Permissions</span></span>  
 <span data-ttu-id="ad714-115">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="ad714-115">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ad714-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ad714-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-insert-and-update-statements"></a><span data-ttu-id="ad714-117">为 INSERT 和 UPDATE 语句禁用 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="ad714-117">To disable a check constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="ad714-118">在 **“对象资源管理器”** 中，展开具有约束的表，再展开 **“约束”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ad714-118">In **Object Explorer**, expand the table with the constraint and then expand the **Constraints** folder.</span></span>  
  
2.  <span data-ttu-id="ad714-119">右键单击该约束，再选择“修改”  。</span><span class="sxs-lookup"><span data-stu-id="ad714-119">Right-click the constraint and select **Modify**.</span></span>  
  
3.  <span data-ttu-id="ad714-120">在 **“表设计器”** 下的网格中，单击 **“强制用于 INSERT 和 UPDATE”** ，然后从下拉菜单中选择 **“否”** 。</span><span class="sxs-lookup"><span data-stu-id="ad714-120">In the grid under **Table Designer**, click **Enforce For INSERTs And UPDATEs** and select **No** from the drop-down menu.</span></span>  
  
4.  <span data-ttu-id="ad714-121">单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="ad714-121">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ad714-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ad714-122">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-insert-and-update-statements"></a><span data-ttu-id="ad714-123">为 INSERT 和 UPDATE 语句禁用 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="ad714-123">To disable a check constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="ad714-124">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="ad714-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ad714-125">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ad714-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ad714-126">将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="ad714-126">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT CK_PurchaseOrderHeader_Freight;   
    GO  
    ```  
  
 <span data-ttu-id="ad714-127">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ad714-127">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
