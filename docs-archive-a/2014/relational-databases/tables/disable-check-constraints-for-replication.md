---
title: 对复制禁用 CHECK 约束 | Microsoft Docs
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
ms.assetid: af98fc70-24dd-4bd3-a0a3-f701dfa67b2c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98b6ca7c3525edeffdb47f294db568d3c115b2c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576600"
---
# <a name="disable-check-constraints-for-replication"></a><span data-ttu-id="17c65-102">对复制禁用 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="17c65-102">Disable Check Constraints for Replication</span></span>
  <span data-ttu-id="17c65-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 禁用 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="17c65-103">You can disable check constraints in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="17c65-104">也可以对复制显式禁用检查约束，这在从早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中发布数据时会非常有用。</span><span class="sxs-lookup"><span data-stu-id="17c65-104">You can also explicitly disable check constraints for replication, which can be useful if you are publishing data from a previous version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17c65-105">如果表是使用复制发布的，则对于复制代理执行的操作将自动禁用检查约束。</span><span class="sxs-lookup"><span data-stu-id="17c65-105">If a table is published using replication, check constraints are automatically disabled for operations performed by replication agents.</span></span> <span data-ttu-id="17c65-106">当复制代理在订阅服务器上执行插入、更新或删除操作时，将不检查约束；如果用户执行插入、更新或删除操作，则检查约束。</span><span class="sxs-lookup"><span data-stu-id="17c65-106">When a replication agent performs an insert, update, or delete at a Subscriber, the constraint is not checked; if a user performs an insert, update, or delete, the constraint is checked.</span></span> <span data-ttu-id="17c65-107">由于最初插入、更新或删除数据时已经在发布服务器上检查过约束，所以对于复制代理将禁用该约束。</span><span class="sxs-lookup"><span data-stu-id="17c65-107">The constraint is disabled for the replication agent because the constraint was already checked at the Publisher when the data was originally inserted, updated, or deleted.</span></span> <span data-ttu-id="17c65-108">有关详细信息，请参阅 [指定架构选项](../replication/publish/specify-schema-options.md)。</span><span class="sxs-lookup"><span data-stu-id="17c65-108">For more information, see [Specify Schema Options](../replication/publish/specify-schema-options.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="17c65-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="17c65-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="17c65-110">Security</span><span class="sxs-lookup"><span data-stu-id="17c65-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="17c65-111">权限</span><span class="sxs-lookup"><span data-stu-id="17c65-111">Permissions</span></span>  
 <span data-ttu-id="17c65-112">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="17c65-112">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="17c65-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="17c65-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-replication"></a><span data-ttu-id="17c65-114">对复制禁用 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="17c65-114">To disable a check constraint for replication</span></span>  
  
1.  <span data-ttu-id="17c65-115">在 **“对象资源管理器”** 中，展开具有要修改的 CHECK 约束的表，再展开 **“约束”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="17c65-115">In **Object Explorer**, expand the table with the check constraint you want to modify, and then expand the **Constraints** folder.</span></span>  
  
2.  <span data-ttu-id="17c65-116">右键单击要修改的 CHECK 约束，然后单击 **“修改”** 。</span><span class="sxs-lookup"><span data-stu-id="17c65-116">Right-click the check constraint you wish to modify and then click **Modify**.</span></span>  
  
3.  <span data-ttu-id="17c65-117">在 **“CHECK 约束”** 对话框中的 **“表设计器”** ，对 **“强制用于复制”** 选择 **“否”** 值。</span><span class="sxs-lookup"><span data-stu-id="17c65-117">In the **Check Constraints** dialog box, under **Table Designer**, select a value of **No** for **Enforce For Replication**.</span></span>  
  
4.  <span data-ttu-id="17c65-118">单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="17c65-118">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="17c65-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="17c65-119">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-replication"></a><span data-ttu-id="17c65-120">对复制禁用 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="17c65-120">To disable a check constraint for replication</span></span>  
  
1.  <span data-ttu-id="17c65-121">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="17c65-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="17c65-122">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="17c65-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="17c65-123">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="17c65-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="17c65-124">第一个示例创建包含一个 IDENTITY 列的表和表中的一个 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="17c65-124">The example creates a table with an IDENTITY column and a CHECK constraint on the table.</span></span> <span data-ttu-id="17c65-125">然后，该示例删除该约束，并通过指定 NOT FOR REPLICATION 子句重新创建约束。</span><span class="sxs-lookup"><span data-stu-id="17c65-125">The example then drops the constraint and recreates it specifying the NOT FOR REPLICATION clause.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE dbo.doc_exd (column_a int IDENTITY (1,1)   
    CONSTRAINT exd_check CHECK (column_a > 1))   
  
    ALTER TABLE dbo.doc_exd   
    DROP CONSTRAINT exd_check;   
    GO  
    ALTER TABLE dbo.doc_exd    
    ADD CONSTRAINT exd_check CHECK NOT FOR REPLICATION (column_a > 1);  
    ```  
  
 <span data-ttu-id="17c65-126">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="17c65-126">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>   
## <a name="see-also"></a><span data-ttu-id="17c65-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17c65-127">See Also</span></span>  
 [<span data-ttu-id="17c65-128">指定架构选项</span><span class="sxs-lookup"><span data-stu-id="17c65-128">Specify Schema Options</span></span>](../replication/publish/specify-schema-options.md)  
  
  
