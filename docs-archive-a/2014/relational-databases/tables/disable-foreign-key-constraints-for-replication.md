---
title: 对复制禁用外键约束 | Microsoft Docs
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
ms.assetid: 4211f2fd-d16a-4081-995c-43f1f0827f0b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4ee7f2fb7b0a27870a09a9d99b723b7faf739aeb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581159"
---
# <a name="disable-foreign-key-constraints-for-replication"></a><span data-ttu-id="3e587-102">对复制禁用外键约束</span><span class="sxs-lookup"><span data-stu-id="3e587-102">Disable Foreign Key Constraints for Replication</span></span>
  <span data-ttu-id="3e587-103">可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中对复制禁用外键约束。</span><span class="sxs-lookup"><span data-stu-id="3e587-103">You can disable foreign key constraints for replication in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="3e587-104">如果正在从以前版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]发布数据，这很有用。</span><span class="sxs-lookup"><span data-stu-id="3e587-104">This can be useful if you are publishing data from a previous version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3e587-105">如果表是使用复制发布的，则对于复制代理执行的操作将自动禁用外键约束。</span><span class="sxs-lookup"><span data-stu-id="3e587-105">If a table is published using replication, foreign key constraints are automatically disabled for operations performed by replication agents.</span></span> <span data-ttu-id="3e587-106">当复制代理在订阅服务器上执行插入、更新或删除操作时，将不检查约束；如果用户执行插入、更新或删除操作，则检查约束。</span><span class="sxs-lookup"><span data-stu-id="3e587-106">When a replication agent performs an insert, update, or delete at a Subscriber, the constraint is not checked; if a user performs an insert, update, or delete, the constraint is checked.</span></span> <span data-ttu-id="3e587-107">由于最初插入、更新或删除数据时已经在发布服务器上检查过约束，所以对于复制代理将禁用该约束。</span><span class="sxs-lookup"><span data-stu-id="3e587-107">The constraint is disabled for the replication agent because the constraint was already checked at the Publisher when the data was originally inserted, updated, or deleted.</span></span>  
  
 <span data-ttu-id="3e587-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="3e587-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3e587-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="3e587-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3e587-110">安全性</span><span class="sxs-lookup"><span data-stu-id="3e587-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3e587-111">**对复制禁用外键约束，使用：**</span><span class="sxs-lookup"><span data-stu-id="3e587-111">**To disable a foreign key constraint for replication, using:**</span></span>  
  
     [<span data-ttu-id="3e587-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3e587-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3e587-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3e587-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3e587-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="3e587-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3e587-115">Security</span><span class="sxs-lookup"><span data-stu-id="3e587-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3e587-116">权限</span><span class="sxs-lookup"><span data-stu-id="3e587-116">Permissions</span></span>  
 <span data-ttu-id="3e587-117">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="3e587-117">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3e587-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3e587-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a><span data-ttu-id="3e587-119">对复制禁用外键约束</span><span class="sxs-lookup"><span data-stu-id="3e587-119">To disable a foreign key constraint for replication</span></span>  
  
1.  <span data-ttu-id="3e587-120">在 **“对象资源管理器”** 中，展开具有要修改的外键约束的表，再展开 **“键”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="3e587-120">In **Object Explorer**, expand the table with the foreign key constraint you want to modify, and then expand the **Keys** folder.</span></span>  
  
2.  <span data-ttu-id="3e587-121">右键单击外键约束，再单击“修改”  。</span><span class="sxs-lookup"><span data-stu-id="3e587-121">Right-click the foreign key constraint and then click **Modify**.</span></span>  
  
3.  <span data-ttu-id="3e587-122">在 **“外键关系”** 对话框，针对 **“强制用于复制”** 选择 **“否”** 值。</span><span class="sxs-lookup"><span data-stu-id="3e587-122">In the **Foreign Key Relationships** dialog box, select a value of **No** for **Enforce For Replication**.</span></span>  
  
4.  <span data-ttu-id="3e587-123">单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="3e587-123">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3e587-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3e587-124">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a><span data-ttu-id="3e587-125">对复制禁用外键约束</span><span class="sxs-lookup"><span data-stu-id="3e587-125">To disable a foreign key constraint for replication</span></span>  
  
1.  <span data-ttu-id="3e587-126">若要在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中执行此任务，请删除外键约束。</span><span class="sxs-lookup"><span data-stu-id="3e587-126">To perform this task in [!INCLUDE[tsql](../../includes/tsql-md.md)], drop the foreign key constraint.</span></span> <span data-ttu-id="3e587-127">然后添加一个新外键约束，并指定 NOT FOR REPLICATION 选项。</span><span class="sxs-lookup"><span data-stu-id="3e587-127">Then add a new foreign key constraint and specify the NOT FOR REPLICATION option.</span></span>  
  
 <span data-ttu-id="3e587-128">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3e587-128">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
