---
title: 查看 SQL Server 实例的数据库列表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- current databases
- databases currently on server [SQL Server]
- database list [SQL Server]
- viewing database list
- displaying database list
- databases [SQL Server], viewing
- servers [SQL Server], databases listed on
- listing databases
ms.assetid: 7ee7a789-db36-4be9-8a0e-0362a1e152dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 47283fa9065a0b9d6238dab804094d9a65d17897
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693374"
---
# <a name="view-a-list-of-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="a6371-102">查看 SQL Server 实例的数据库列表</span><span class="sxs-lookup"><span data-stu-id="a6371-102">View a List of Databases on an Instance of SQL Server</span></span>
  <span data-ttu-id="a6371-103">本主题说明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查看 [!INCLUDE[tsql](../../includes/tsql-md.md)]实例上的数据库列表。</span><span class="sxs-lookup"><span data-stu-id="a6371-103">This topic describes how to view a list of databases on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a6371-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="a6371-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a6371-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="a6371-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a6371-106">安全性</span><span class="sxs-lookup"><span data-stu-id="a6371-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a6371-107">**查看 SQL Server 实例的数据库列表，使用：**</span><span class="sxs-lookup"><span data-stu-id="a6371-107">**To view a list of databases on an instance of SQL Server, using:**</span></span>  
  
     [<span data-ttu-id="a6371-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a6371-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a6371-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a6371-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a6371-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="a6371-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a6371-111">Security</span><span class="sxs-lookup"><span data-stu-id="a6371-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a6371-112">权限</span><span class="sxs-lookup"><span data-stu-id="a6371-112">Permissions</span></span>  
 <span data-ttu-id="a6371-113">如果 **sys.databases** 的调用方并非数据库的所有者，并且数据库不是 **master** 或 **tempdb**，则查看对应行所需的最小权限为 ALTER ANY DATABASE 或 VIEW ANY DATABASE 服务器级权限，或者为 **master** 数据库中的 CREATE DATABASE 权限。</span><span class="sxs-lookup"><span data-stu-id="a6371-113">If the caller of **sys.databases** is not the owner of the database and the database is not **master** or **tempdb**, the minimum permissions required to see the corresponding row are ALTER ANY DATABASE or VIEW ANY DATABASE server-level permission, or CREATE DATABASE permission in the **master** database.</span></span> <span data-ttu-id="a6371-114">始终可以在 **sys.databases**中查看调用方连接的数据库。</span><span class="sxs-lookup"><span data-stu-id="a6371-114">The database to which the caller is connected can always be viewed in **sys.databases**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a6371-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a6371-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-a-list-of-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="a6371-116">查看 SQL Server 实例的数据库列表</span><span class="sxs-lookup"><span data-stu-id="a6371-116">To view a list of databases on an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="a6371-117">在 **对象资源管理器**中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="a6371-117">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a6371-118">若要查看实例上的所有数据库的列表，请展开 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="a6371-118">To see a list of all databases on the instance, expand **Databases**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a6371-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a6371-119">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-list-of-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="a6371-120">查看 SQL Server 实例的数据库列表</span><span class="sxs-lookup"><span data-stu-id="a6371-120">To view a list of databases on an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="a6371-121">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a6371-121">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a6371-122">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a6371-122">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a6371-123">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="a6371-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a6371-124">此示例返回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上的数据库列表。</span><span class="sxs-lookup"><span data-stu-id="a6371-124">This example returns a list of databases on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a6371-125">该列表包含数据库名称、数据库 ID 和创建数据库的日期。</span><span class="sxs-lookup"><span data-stu-id="a6371-125">The list includes the names of the databases, their database IDs, and the dates when the databases were created.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT name, database_id, create_date  
FROM sys.databases ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6371-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6371-126">See Also</span></span>  
 <span data-ttu-id="a6371-127">[数据库和文件目录视图 (Transact-SQL)](/sql/relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a6371-127">[Databases and Files Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql) </span></span>  
 [<span data-ttu-id="a6371-128">sys.databases (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a6371-128">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
