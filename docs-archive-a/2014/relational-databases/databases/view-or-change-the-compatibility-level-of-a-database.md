---
title: 查看或更改数据库的兼容级别 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- compatibility levels [SQL Server], viewing
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], changing
ms.assetid: 579867ec-57cb-4cb8-af35-9688c1e9e15d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35cf7af50eba333440c42a1bac428df1fff156b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693378"
---
# <a name="view-or-change-the-compatibility-level-of-a-database"></a><span data-ttu-id="ff5f4-102">查看或更改数据库的兼容级别</span><span class="sxs-lookup"><span data-stu-id="ff5f4-102">View or Change the Compatibility Level of a Database</span></span>
  <span data-ttu-id="ff5f4-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中查看或更改数据库的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-103">This topic describes how to view or change the compatibility level of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ff5f4-104">在更改数据库的兼容级别之前，应先了解此更改对应用程序的影响。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-104">Before you change the compatibility level of a database, you should understand the impact of the change on your applications.</span></span> <span data-ttu-id="ff5f4-105">有关详细信息，请参阅 [ALTER DATABASE 兼容级别 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-105">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
 <span data-ttu-id="ff5f4-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ff5f4-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ff5f4-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ff5f4-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ff5f4-108">安全性</span><span class="sxs-lookup"><span data-stu-id="ff5f4-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ff5f4-109">**查看或更改数据库的兼容级别，使用：**</span><span class="sxs-lookup"><span data-stu-id="ff5f4-109">**To view or change the compatibility level of a database, using:**</span></span>  
  
     [<span data-ttu-id="ff5f4-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ff5f4-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ff5f4-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ff5f4-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ff5f4-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="ff5f4-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ff5f4-113">Security</span><span class="sxs-lookup"><span data-stu-id="ff5f4-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ff5f4-114">权限</span><span class="sxs-lookup"><span data-stu-id="ff5f4-114">Permissions</span></span>  
 <span data-ttu-id="ff5f4-115">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-115">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ff5f4-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ff5f4-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-compatibility-level-of-a-database"></a><span data-ttu-id="ff5f4-117">查看或更改数据库的兼容级别</span><span class="sxs-lookup"><span data-stu-id="ff5f4-117">To view or change the compatibility level of a database</span></span>  
  
1.  <span data-ttu-id="ff5f4-118">连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的相应实例之后，在对象资源管理器中，单击服务器名称。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-118">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name.</span></span>  
  
2.  <span data-ttu-id="ff5f4-119">展开 **“数据库”** ，然后根据数据库的不同，选择用户数据库，或展开 **“系统数据库”** ，再选择系统数据库。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-119">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="ff5f4-120">右键单击数据库，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-120">Right-click the database, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="ff5f4-121">**“数据库属性”** 对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-121">The **Database Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="ff5f4-122">在 **“选择页”** 窗格中，单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-122">In the **Select a page** pane, click **Options**.</span></span>  
  
     <span data-ttu-id="ff5f4-123">当前兼容级别显示在 **“兼容级别”** 列表框中。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-123">The current compatibility level is displayed in the **Compatibility level** list box.</span></span>  
  
5.  <span data-ttu-id="ff5f4-124">若要更改兼容级别，请从列表中选择其他选项。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-124">To change the compatibility level, select a different option from the list.</span></span> <span data-ttu-id="ff5f4-125">可用选项包括 **SQL Server 2008 (100)**、 **SQL Server 2012 (110)** 或 **SQL Server 2014 (120)**。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-125">The choices are **SQL Server 2008 (100)**, **SQL Server 2012 (110)**, or **SQL Server 2014 (120)**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ff5f4-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ff5f4-126">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-compatibility-level-of-a-database"></a><span data-ttu-id="ff5f4-127">查看数据库的兼容级别</span><span class="sxs-lookup"><span data-stu-id="ff5f4-127">To view the compatibility level of a database</span></span>  
  
1.  <span data-ttu-id="ff5f4-128">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ff5f4-129">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ff5f4-130">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ff5f4-131">此示例将返回 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-131">This example returns the compatibility level of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-compatibility-level-of-a-database"></a><span data-ttu-id="ff5f4-132">更改数据库的兼容级别</span><span class="sxs-lookup"><span data-stu-id="ff5f4-132">To change the compatibility level of a database</span></span>  
  
1.  <span data-ttu-id="ff5f4-133">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-133">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ff5f4-134">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-134">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ff5f4-135">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-135">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ff5f4-136">此示例更改的兼容级别 [!INCLUDE[ssSampleDBobject](../../includes/sssql14-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ff5f4-136">This example changes the compatibility level of the [!INCLUDE[ssSampleDBobject](../../includes/sssql14-md.md)].</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET COMPATIBILITY_LEVEL = 120;  
GO  
```  
  
  
