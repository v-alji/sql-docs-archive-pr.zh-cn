---
title: 删除数据库中的数据文件或日志文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], files
- deleting files
- removing files
- removing data
- data deletions [SQL Server]
- file deletion [SQL Server]
- deleting data
ms.assetid: 0db4018c-ce2c-4ba1-bb29-1e4f3791c925
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6f7bd170e085e9bc94b00446545850e905efaa34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693936"
---
# <a name="delete-data-or-log-files-from-a-database"></a><span data-ttu-id="5840d-102">删除数据库中的数据文件或日志文件</span><span class="sxs-lookup"><span data-stu-id="5840d-102">Delete Data or Log Files from a Database</span></span>
  <span data-ttu-id="5840d-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除数据文件或日志文件。</span><span class="sxs-lookup"><span data-stu-id="5840d-103">This topic describes how to delete data or log files in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5840d-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="5840d-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="5840d-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="5840d-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="5840d-106">文件必须为空后才能删除。</span><span class="sxs-lookup"><span data-stu-id="5840d-106">A file must be empty before it can be deleted.</span></span> <span data-ttu-id="5840d-107">有关详细信息，请参阅 [收缩文件](shrink-a-file.md)。</span><span class="sxs-lookup"><span data-stu-id="5840d-107">For more information, see [Shrink a File](shrink-a-file.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5840d-108">Security</span><span class="sxs-lookup"><span data-stu-id="5840d-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5840d-109">权限</span><span class="sxs-lookup"><span data-stu-id="5840d-109">Permissions</span></span>  
 <span data-ttu-id="5840d-110">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="5840d-110">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5840d-111">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5840d-111">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-data-or-log-files-from-a-database"></a><span data-ttu-id="5840d-112">删除数据库中的数据文件或日志文件</span><span class="sxs-lookup"><span data-stu-id="5840d-112">To delete data or log files from a database</span></span>  
  
1.  <span data-ttu-id="5840d-113">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="5840d-113">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="5840d-114">展开 **“数据库”** ，右键单击要从其中删除文件的数据库，再单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="5840d-114">Expand **Databases**, right-click the database from which to delete the file, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="5840d-115">选择 **“文件”** 页。</span><span class="sxs-lookup"><span data-stu-id="5840d-115">Select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="5840d-116">在 **“数据库文件”** 网格中，选择要删除的文件，然后单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="5840d-116">In the **Database files** grid, select the file to delete and then click **Remove**.</span></span>  
  
5.  <span data-ttu-id="5840d-117">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="5840d-117">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5840d-118">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5840d-118">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-data-or-log-files-from-a-database"></a><span data-ttu-id="5840d-119">删除数据库中的数据文件或日志文件</span><span class="sxs-lookup"><span data-stu-id="5840d-119">To delete data or log files from a database</span></span>  
  
1.  <span data-ttu-id="5840d-120">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5840d-120">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5840d-121">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="5840d-121">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5840d-122">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="5840d-122">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="5840d-123">此示例删除文件 `test1dat4`。</span><span class="sxs-lookup"><span data-stu-id="5840d-123">This example removes the file `test1dat4`.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase4](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase4)]  
  
 <span data-ttu-id="5840d-124">有关更多示例，请参阅 [ALTER DATABASE 文件和文件组选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)。</span><span class="sxs-lookup"><span data-stu-id="5840d-124">For more examples, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5840d-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5840d-125">See Also</span></span>  
 <span data-ttu-id="5840d-126">[收缩数据库](shrink-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="5840d-126">[Shrink a Database](shrink-a-database.md) </span></span>  
 [<span data-ttu-id="5840d-127">向数据库中添加数据文件或日志文件</span><span class="sxs-lookup"><span data-stu-id="5840d-127">Add Data or Log Files to a Database</span></span>](add-data-or-log-files-to-a-database.md)  
  
  
