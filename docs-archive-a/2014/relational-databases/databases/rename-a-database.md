---
title: 重命名数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], renaming
- renaming databases
ms.assetid: 44c69d35-abcb-4da3-9370-5e0bc9a28496
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd25a78e3d3b9be2e7191ce6ed3d6bdcbb0f9606
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581289"
---
# <a name="rename-a-database"></a><span data-ttu-id="0a1ce-102">重命名数据库</span><span class="sxs-lookup"><span data-stu-id="0a1ce-102">Rename a Database</span></span>
  <span data-ttu-id="0a1ce-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中重命名用户定义的数据库。</span><span class="sxs-lookup"><span data-stu-id="0a1ce-103">This topic describes how to rename a user-defined database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0a1ce-104">数据库名称可以包含任何符合标识符规则的字符。</span><span class="sxs-lookup"><span data-stu-id="0a1ce-104">The name of the database can include any characters that follow the rules for identifiers.</span></span>  
  
 <span data-ttu-id="0a1ce-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="0a1ce-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0a1ce-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="0a1ce-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0a1ce-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0a1ce-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0a1ce-108">安全性</span><span class="sxs-lookup"><span data-stu-id="0a1ce-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0a1ce-109">**重命名数据库，使用：**</span><span class="sxs-lookup"><span data-stu-id="0a1ce-109">**To rename a database, using:**</span></span>  
  
     [<span data-ttu-id="0a1ce-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0a1ce-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0a1ce-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0a1ce-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="0a1ce-112">**跟进：** [在重命名数据库之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="0a1ce-112">**Follow Up:**  [After renaming a database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0a1ce-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="0a1ce-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0a1ce-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0a1ce-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0a1ce-115">无法重命名系统数据库。</span><span class="sxs-lookup"><span data-stu-id="0a1ce-115">System databases cannot be renamed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0a1ce-116">Security</span><span class="sxs-lookup"><span data-stu-id="0a1ce-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0a1ce-117">权限</span><span class="sxs-lookup"><span data-stu-id="0a1ce-117">Permissions</span></span>  
 <span data-ttu-id="0a1ce-118">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="0a1ce-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0a1ce-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0a1ce-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-database"></a><span data-ttu-id="0a1ce-120">重命名数据库</span><span class="sxs-lookup"><span data-stu-id="0a1ce-120">To rename a database</span></span>  
  
1.  <span data-ttu-id="0a1ce-121">在 **对象资源管理器**中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="0a1ce-121">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="0a1ce-122">确保没有任何用户正在使用数据库，然后 [将数据库设置为单用户模式](set-a-database-to-single-user-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="0a1ce-122">Make sure that no one is using the database, and then [set the database to single-user mode](set-a-database-to-single-user-mode.md).</span></span>  
  
3.  <span data-ttu-id="0a1ce-123">展开“数据库”\*\*\*\*，右键单击要重命名的数据库，然后单击“重命名”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0a1ce-123">Expand **Databases**, right-click the database to rename, and then click **Rename**.</span></span>  
  
4.  <span data-ttu-id="0a1ce-124">输入新的数据库名称，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="0a1ce-124">Enter the new database name, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0a1ce-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0a1ce-125">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-database"></a><span data-ttu-id="0a1ce-126">重命名数据库</span><span class="sxs-lookup"><span data-stu-id="0a1ce-126">To rename a database</span></span>  
  
1.  <span data-ttu-id="0a1ce-127">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0a1ce-127">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0a1ce-128">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="0a1ce-128">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0a1ce-129">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="0a1ce-129">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="0a1ce-130">此示例将 `AdventureWorks2012` 数据库的名称更改为 `Northwind`。</span><span class="sxs-lookup"><span data-stu-id="0a1ce-130">This example changes the name of the `AdventureWorks2012` database to `Northwind`.</span></span>  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
Modify Name = Northwind ;  
GO  
```  
  
###  <a name="TsqlExample"></a>   
##  <a name="follow-up-after-renaming-a-database"></a><a name="FollowUp"></a> <span data-ttu-id="0a1ce-131">跟进：在重命名数据库之后</span><span class="sxs-lookup"><span data-stu-id="0a1ce-131">Follow Up: After renaming a database</span></span>  
 <span data-ttu-id="0a1ce-132">在重命名任何数据库后，备份 **master** 数据库。</span><span class="sxs-lookup"><span data-stu-id="0a1ce-132">Back up the **master** database after you rename any database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a1ce-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a1ce-133">See Also</span></span>  
 <span data-ttu-id="0a1ce-134">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a1ce-134">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="0a1ce-135">数据库标识符</span><span class="sxs-lookup"><span data-stu-id="0a1ce-135">Database Identifiers</span></span>](database-identifiers.md)  
  
  
