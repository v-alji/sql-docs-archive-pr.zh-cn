---
title: 增加数据库的大小 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], size
- increasing database size
- database size [SQL Server], increasing
- size [SQL Server], databases
ms.assetid: 14f4206d-3afa-4ba9-9849-23e81d63306d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 71dcb00b3f5525f7059fc54911baed929f763008
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693932"
---
# <a name="increase-the-size-of-a-database"></a><span data-ttu-id="baace-102">增加数据库的大小</span><span class="sxs-lookup"><span data-stu-id="baace-102">Increase the Size of a Database</span></span>
  <span data-ttu-id="baace-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中增加数据库的大小。</span><span class="sxs-lookup"><span data-stu-id="baace-103">This topic describes how to increase the size of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="baace-104">通过增加现有数据或日志文件的大小或向数据库添加新文件，可以扩展数据库。</span><span class="sxs-lookup"><span data-stu-id="baace-104">The database is expanded by either increasing the size of an existing data or log file or by adding a new file to the database.</span></span>  
  
 <span data-ttu-id="baace-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="baace-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="baace-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="baace-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="baace-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="baace-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="baace-108">安全性</span><span class="sxs-lookup"><span data-stu-id="baace-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="baace-109">**增加数据库的大小，使用：**</span><span class="sxs-lookup"><span data-stu-id="baace-109">**To increase the size of a database, using:**</span></span>  
  
     [<span data-ttu-id="baace-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="baace-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="baace-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="baace-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="baace-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="baace-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="baace-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="baace-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="baace-114">当 BACKUP 语句正在运行时，不能添加或删除文件。</span><span class="sxs-lookup"><span data-stu-id="baace-114">You cannot add or remove a file while a BACKUP statement is running.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="baace-115">Security</span><span class="sxs-lookup"><span data-stu-id="baace-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="baace-116">权限</span><span class="sxs-lookup"><span data-stu-id="baace-116">Permissions</span></span>  
 <span data-ttu-id="baace-117">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="baace-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="baace-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="baace-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-increase-the-size-of-a-database"></a><span data-ttu-id="baace-119">增加数据库的大小</span><span class="sxs-lookup"><span data-stu-id="baace-119">To increase the size of a database</span></span>  
  
1.  <span data-ttu-id="baace-120">在 **对象资源管理器**中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="baace-120">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="baace-121">展开  “数据库”，右键单击要扩展的数据库，再单击  “属性”。</span><span class="sxs-lookup"><span data-stu-id="baace-121">Expand **Databases**, right-click the database to increase, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="baace-122">在 **“数据库属性”** 中，选择 **“文件”** 页。</span><span class="sxs-lookup"><span data-stu-id="baace-122">In **Database Properties**, select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="baace-123">若要增加现有文件的大小，请增加文件的  “初始大小 (MB)”列中的值。</span><span class="sxs-lookup"><span data-stu-id="baace-123">To increase the size of an existing file, increase the value in the **Initial Size (MB)** column for the file.</span></span> <span data-ttu-id="baace-124">数据库的大小必须至少增加 1 MB。</span><span class="sxs-lookup"><span data-stu-id="baace-124">You must increase the size of the database by at least 1 megabyte.</span></span>  
  
5.  <span data-ttu-id="baace-125">若要通过添加新文件增加数据库大小，请单击 **“添加”** ，然后输入新文件的值。</span><span class="sxs-lookup"><span data-stu-id="baace-125">To increase the size of the database by adding a new file, click **Add** and then enter the values for the new file.</span></span> <span data-ttu-id="baace-126">有关详细信息，请参阅 [向数据库中添加数据文件或日志文件](add-data-or-log-files-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="baace-126">For more information, see [Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md).</span></span>  
  
6.  <span data-ttu-id="baace-127">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="baace-127">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="baace-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="baace-128">Using Transact-SQL</span></span>  
  
#### <a name="to-increase-the-size-of-a-database"></a><span data-ttu-id="baace-129">增加数据库的大小</span><span class="sxs-lookup"><span data-stu-id="baace-129">To increase the size of a database</span></span>  
  
1.  <span data-ttu-id="baace-130">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="baace-130">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="baace-131">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="baace-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="baace-132">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="baace-132">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="baace-133">此示例可增加文件 `test1dat3`的大小。</span><span class="sxs-lookup"><span data-stu-id="baace-133">This example increases the size of the file `test1dat3`.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase5](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase5)]  
  
 <span data-ttu-id="baace-134">有关更多示例，请参阅 [ALTER DATABASE 文件和文件组选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)。</span><span class="sxs-lookup"><span data-stu-id="baace-134">For more examples, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baace-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="baace-135">See Also</span></span>  
 <span data-ttu-id="baace-136">[向数据库中添加数据文件或日志文件](add-data-or-log-files-to-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="baace-136">[Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md) </span></span>  
 [<span data-ttu-id="baace-137">收缩数据库</span><span class="sxs-lookup"><span data-stu-id="baace-137">Shrink a Database</span></span>](shrink-a-database.md)  
  
  
