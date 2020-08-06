---
title: 向数据库中添加数据文件或日志文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], files
- adding data files
- adding files
- adding log files
- file additions [SQL Server], steps
- files [SQL Server], adding
- data additions [SQL Server]
ms.assetid: 8ead516a-1334-4f40-84b2-509d0a8ffa45
author: stevestein
ms.author: sstein
ms.openlocfilehash: f72e00f9dab422652237b4b85579c544d0cda9fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693957"
---
# <a name="add-data-or-log-files-to-a-database"></a><span data-ttu-id="b0127-102">向数据库中添加数据文件或日志文件</span><span class="sxs-lookup"><span data-stu-id="b0127-102">Add Data or Log Files to a Database</span></span>
  <span data-ttu-id="b0127-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中向数据库添加数据文件或日志文件。</span><span class="sxs-lookup"><span data-stu-id="b0127-103">This topic describes how to add data or log files to a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b0127-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b0127-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b0127-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b0127-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b0127-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b0127-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b0127-107">安全性</span><span class="sxs-lookup"><span data-stu-id="b0127-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b0127-108">**向数据库中添加数据文件或日志文件，使用：**</span><span class="sxs-lookup"><span data-stu-id="b0127-108">**To add data or log files to a database, using:**</span></span>  
  
     [<span data-ttu-id="b0127-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b0127-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b0127-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b0127-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b0127-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="b0127-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b0127-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b0127-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b0127-113">当 BACKUP 语句正在运行时，不能添加或删除文件。</span><span class="sxs-lookup"><span data-stu-id="b0127-113">You cannot add or remove a file while a BACKUP statement is running.</span></span>  
  
-   <span data-ttu-id="b0127-114">可以为每个数据库指定最多 32,767 个文件和 32,767 个文件组。</span><span class="sxs-lookup"><span data-stu-id="b0127-114">A maximum of 32,767 files and 32,767 filegroups can be specified for each database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b0127-115">Security</span><span class="sxs-lookup"><span data-stu-id="b0127-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b0127-116">权限</span><span class="sxs-lookup"><span data-stu-id="b0127-116">Permissions</span></span>  
 <span data-ttu-id="b0127-117">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="b0127-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b0127-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b0127-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-data-or-log-files-to-a-database"></a><span data-ttu-id="b0127-119">向数据库添加数据文件或日志文件</span><span class="sxs-lookup"><span data-stu-id="b0127-119">To add data or log files to a database</span></span>  
  
1.  <span data-ttu-id="b0127-120">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="b0127-120">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="b0127-121">展开“数据库”，右键单击要从中添加文件的数据库，然后单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="b0127-121">Expand **Databases**, right-click the database from which to add the files, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="b0127-122">在 **“数据库属性”** 对话框中，选择 **“文件”** 页。</span><span class="sxs-lookup"><span data-stu-id="b0127-122">In the **Database Properties** dialog box, select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="b0127-123">若要添加数据或事务日志文件，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="b0127-123">To add a data or transaction log file, click **Add**.</span></span>  
  
5.  <span data-ttu-id="b0127-124">在 **“数据库文件”** 网格中，输入文件的逻辑名称。</span><span class="sxs-lookup"><span data-stu-id="b0127-124">In the **Database files** grid, enter a logical name for the file.</span></span> <span data-ttu-id="b0127-125">该文件名在数据库中必须唯一。</span><span class="sxs-lookup"><span data-stu-id="b0127-125">The file name must be unique within the database.</span></span>  
  
6.  <span data-ttu-id="b0127-126">选择文件类型：数据或日志。</span><span class="sxs-lookup"><span data-stu-id="b0127-126">Select the file type, data or log.</span></span>  
  
7.  <span data-ttu-id="b0127-127">对于数据文件，从列表中选择文件应属于的文件组，或选择 \<new filegroup> 以创建新的文件组。</span><span class="sxs-lookup"><span data-stu-id="b0127-127">For a data file, select the filegroup in which the file should be included from the list, or select **\<new filegroup>** to create a new filegroup.</span></span> <span data-ttu-id="b0127-128">事务日志不能放在文件组中。</span><span class="sxs-lookup"><span data-stu-id="b0127-128">Transaction logs cannot be put in filegroups.</span></span>  
  
8.  <span data-ttu-id="b0127-129">指定文件的初始大小。</span><span class="sxs-lookup"><span data-stu-id="b0127-129">Specify the initial size of the file.</span></span> <span data-ttu-id="b0127-130">根据数据库中您希望的最大数据量，使数据文件尽可能大。</span><span class="sxs-lookup"><span data-stu-id="b0127-130">Make the data file as large as possible, based on the maximum amount of data you expect in the database.</span></span>  
  
9. <span data-ttu-id="b0127-131">若要指定文件的增长方式，请在“自动增长”列中单击 (…) 。</span><span class="sxs-lookup"><span data-stu-id="b0127-131">To specify how the file should grow, click (**...**) in the **Autogrowth** column.</span></span> <span data-ttu-id="b0127-132">从下列选项中进行选择：</span><span class="sxs-lookup"><span data-stu-id="b0127-132">Select from the following options:</span></span>  
  
    1.  <span data-ttu-id="b0127-133">若要允许当前选中的文件根据数据空间量的需求增加而增长，请选中 **“启用自动增长”** 复选框，然后从下列选项中进行选择：</span><span class="sxs-lookup"><span data-stu-id="b0127-133">To allow for the currently selected file to grow as more data space is required, select the **Enable Autogrowth** check box and then select from the following options:</span></span>  
  
    2.  <span data-ttu-id="b0127-134">若要指定文件按固定增量增长，请选择 **“按 MB”** 并指定一个值。</span><span class="sxs-lookup"><span data-stu-id="b0127-134">To specify that the file should grow by fixed increments, select **In Megabytes** and specify a value.</span></span>  
  
    3.  <span data-ttu-id="b0127-135">若要指定文件按当前文件大小的百分比增长，请选择 **“按百分比”** 并指定一个值。</span><span class="sxs-lookup"><span data-stu-id="b0127-135">To specify that the file should grow by a percentage of the current file size, select **In Percent** and specify a value.</span></span>  
  
10. <span data-ttu-id="b0127-136">若要指定最大文件大小限制，请从下列选项中进行选择：</span><span class="sxs-lookup"><span data-stu-id="b0127-136">To specify the maximum file size limit, select from the following options:</span></span>  
  
    1.  <span data-ttu-id="b0127-137">若要指定文件能够增长到的最大大小，请选择“限制文件增长(MB)”并指定一个值。</span><span class="sxs-lookup"><span data-stu-id="b0127-137">To specify the maximum size the file should be able to grow to, select **Restricted File Growth (MB)** and specify a value.</span></span>  
  
    2.  <span data-ttu-id="b0127-138">若要允许文件根据需要增长，请选择 **“不限制文件增长”** 。</span><span class="sxs-lookup"><span data-stu-id="b0127-138">To allow for the file to grow as much as needed, select **Unrestricted File Growth**.</span></span>  
  
    3.  <span data-ttu-id="b0127-139">若要防止文件增长，请清除 **“启用自动增长”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="b0127-139">To prevent the file from growing, clear the **Enable Autogrowth** check box.</span></span> <span data-ttu-id="b0127-140">文件大小不会增长到超过“初始大小(MB)”列中指定的值。</span><span class="sxs-lookup"><span data-stu-id="b0127-140">The size of the file will not grow beyond the value specified in the **Initial Size (MB)** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b0127-141">最大数据库大小由可用磁盘空间量决定，许可限制由正在使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本决定。</span><span class="sxs-lookup"><span data-stu-id="b0127-141">The maximum database size is determined by the amount of disk space available and the licensing limits determined by the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you are using.</span></span>  
  
11. <span data-ttu-id="b0127-142">指定文件位置的路径。</span><span class="sxs-lookup"><span data-stu-id="b0127-142">Specify the path for the file location.</span></span> <span data-ttu-id="b0127-143">指定的路径必须存在才能添加文件。</span><span class="sxs-lookup"><span data-stu-id="b0127-143">The specified path must exist before adding the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b0127-144">默认情况下，数据和事务日志放在相同的驱动器和路径中以适应单磁盘系统，但这对于生产环境可能并非最佳方式。</span><span class="sxs-lookup"><span data-stu-id="b0127-144">By default, the data and transaction logs are put on the same drive and path to accommodate single-disk systems, but may not be optimal for production environments.</span></span> <span data-ttu-id="b0127-145">有关详细信息，请参阅 [数据库文件和文件组](database-files-and-filegroups.md)。</span><span class="sxs-lookup"><span data-stu-id="b0127-145">For more information, see [Database Files and Filegroups](database-files-and-filegroups.md).</span></span>  
  
12. <span data-ttu-id="b0127-146">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="b0127-146">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b0127-147">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b0127-147">Using Transact-SQL</span></span>  
  
#### <a name="to-add-data-or-log-files-to-a-database"></a><span data-ttu-id="b0127-148">向数据库添加数据文件或日志文件</span><span class="sxs-lookup"><span data-stu-id="b0127-148">To add data or log files to a database</span></span>  
  
1.  <span data-ttu-id="b0127-149">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0127-149">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b0127-150">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b0127-150">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b0127-151">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b0127-151">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b0127-152">此实例向数据库添加由两个文件组成的文件组。</span><span class="sxs-lookup"><span data-stu-id="b0127-152">The example adds a filegroup with two files to a database.</span></span> <span data-ttu-id="b0127-153">此示例在 `Test1FG1` 数据库中创建文件组 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ，然后将两个 5MB 的文件添加到该文件组。</span><span class="sxs-lookup"><span data-stu-id="b0127-153">The example creates the filegroup `Test1FG1` in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database and adds two 5-MB files to the filegroup.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase2](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase2)]  
  
 <span data-ttu-id="b0127-154">有关更多示例，请参阅 [ALTER DATABASE 文件和文件组选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)。</span><span class="sxs-lookup"><span data-stu-id="b0127-154">For more examples, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0127-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b0127-155">See Also</span></span>  
 <span data-ttu-id="b0127-156">[Database Files and Filegroups](database-files-and-filegroups.md) </span><span class="sxs-lookup"><span data-stu-id="b0127-156">[Database Files and Filegroups](database-files-and-filegroups.md) </span></span>  
 <span data-ttu-id="b0127-157">[删除数据库中的数据文件或日志文件](delete-data-or-log-files-from-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="b0127-157">[Delete Data or Log Files from a Database](delete-data-or-log-files-from-a-database.md) </span></span>  
 [<span data-ttu-id="b0127-158">增加数据库的大小</span><span class="sxs-lookup"><span data-stu-id="b0127-158">Increase the Size of a Database</span></span>](increase-the-size-of-a-database.md)  
  
  
