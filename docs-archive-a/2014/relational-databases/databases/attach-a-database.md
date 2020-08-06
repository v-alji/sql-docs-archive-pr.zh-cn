---
title: 附加数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.attachdatabase.f1
helpviewer_keywords:
- database attaching [SQL Server]
- attaching databases [SQL Server]
ms.assetid: b4efb0ae-cfe6-4d81-a4b4-6e4916885caa
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb11b5c257007872e92d3f0a7eadb3e46b4969cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693954"
---
# <a name="attach-a-database"></a><span data-ttu-id="14d77-102">附加数据库</span><span class="sxs-lookup"><span data-stu-id="14d77-102">Attach a Database</span></span>
  <span data-ttu-id="14d77-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中附加数据库。</span><span class="sxs-lookup"><span data-stu-id="14d77-103">This topic describes how to attach a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="14d77-104">可以使用此功能来复制、移动或升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="14d77-104">You can use this feature to copy, move, or upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="14d77-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="14d77-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="14d77-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="14d77-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="14d77-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="14d77-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="14d77-108">建议</span><span class="sxs-lookup"><span data-stu-id="14d77-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="14d77-109">安全性</span><span class="sxs-lookup"><span data-stu-id="14d77-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="14d77-110">**附加数据库，使用：**</span><span class="sxs-lookup"><span data-stu-id="14d77-110">**To Attach a Database by using:**</span></span>  
  
     [<span data-ttu-id="14d77-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="14d77-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="14d77-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="14d77-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="14d77-113">**跟进：**  [在升级数据库之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="14d77-113">**Follow Up:**  [After Upgrading a Database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="14d77-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="14d77-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="14d77-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="14d77-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="14d77-116">必须首先分离数据库。</span><span class="sxs-lookup"><span data-stu-id="14d77-116">The database must first be detached.</span></span> <span data-ttu-id="14d77-117">尝试附加未分离的数据库将返回错误。</span><span class="sxs-lookup"><span data-stu-id="14d77-117">Attempting to attach a database that has not been detached will return an error.</span></span> <span data-ttu-id="14d77-118">有关详细信息，请参阅 [分离数据库](detach-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="14d77-118">For more information, see [Detach a Database](detach-a-database.md).</span></span>  
  
-   <span data-ttu-id="14d77-119">附加数据库时，所有数据文件（MDF 文件和 LDF 文件）都必须可用。</span><span class="sxs-lookup"><span data-stu-id="14d77-119">When you attach a database, all data files (MDF and LDF files) must be available.</span></span> <span data-ttu-id="14d77-120">如果任何数据文件的路径不同于首次创建数据库或上次附加数据库时的路径，则必须指定文件的当前路径。</span><span class="sxs-lookup"><span data-stu-id="14d77-120">If any data file has a different path from when the database was first created or last attached, you must specify the current path of the file.</span></span>  
  
-   <span data-ttu-id="14d77-121">在附加数据库时，如果 MDF 和 LDF 文件位于不同目录并且其中一条路径包含 \\\\?\GlobalRoot，该操作将失败。</span><span class="sxs-lookup"><span data-stu-id="14d77-121">When you attach a database, if MDF and LDF files are located in different directories and one of the paths includes \\\\?\GlobalRoot, the operation will fail.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="14d77-122">建议</span><span class="sxs-lookup"><span data-stu-id="14d77-122">Recommendations</span></span>  
<span data-ttu-id="14d77-123">建议使用 `ALTER DATABASE` 计划的重定位过程（而不是使用分离和附加操作）移动数据库。</span><span class="sxs-lookup"><span data-stu-id="14d77-123">We recommend that you move databases by using the `ALTER DATABASE` planned relocation procedure, instead of using detach and attach.</span></span> <span data-ttu-id="14d77-124">有关详细信息，请参阅 [Move User Databases](move-user-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="14d77-124">For more information, see [Move User Databases](move-user-databases.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="14d77-125">Security</span><span class="sxs-lookup"><span data-stu-id="14d77-125">Security</span></span>  
<span data-ttu-id="14d77-126">文件访问权限可在很多数据库操作过程中设置，其中包括分离或附加数据库。</span><span class="sxs-lookup"><span data-stu-id="14d77-126">File access permissions are set during a number of database operations, including detaching or attaching a database.</span></span> <span data-ttu-id="14d77-127">有关分离或附加数据库时设置的文件权限的信息，请参阅 [联机丛书中的](https://technet.microsoft.com/library/ms189128.aspx) 保护数据和日志文件 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="14d77-127">For information about file permissions that are set whenever a database is detached and attached, see [Securing Data and Log Files](https://technet.microsoft.com/library/ms189128.aspx) in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Books Online.</span></span>  
  
<span data-ttu-id="14d77-128">建议您不要附加或还原来自未知或不可信源的数据库。</span><span class="sxs-lookup"><span data-stu-id="14d77-128">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="14d77-129">此类数据库可能包含恶意代码，这些代码可能会执行非预期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码，或者通过修改架构或物理数据库结构导致错误。</span><span class="sxs-lookup"><span data-stu-id="14d77-129">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="14d77-130">使用来自未知源或不可信源的数据库前，请在非生产服务器上针对数据库运行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，然后检查数据库中的代码，例如存储过程或其他用户定义代码。</span><span class="sxs-lookup"><span data-stu-id="14d77-130">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span> <span data-ttu-id="14d77-131">有关附加数据库的详细信息以及在附加数据库时对元数据进行的更改的信息，请参阅[数据库分离和附加 (SQL Server)](database-detach-and-attach-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="14d77-131">For more information about attaching databases and information about changes that are made to metadata when you attach a database, see [Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="14d77-132">权限</span><span class="sxs-lookup"><span data-stu-id="14d77-132">Permissions</span></span>  
<span data-ttu-id="14d77-133">需要 `CREATE DATABASE`、`CREATE ANY DATABASE` 或 `ALTER ANY DATABASE` 权限。</span><span class="sxs-lookup"><span data-stu-id="14d77-133">Requires `CREATE DATABASE`, `CREATE ANY DATABASE`, or `ALTER ANY DATABASE` permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="14d77-134">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="14d77-134">Using SQL Server Management Studio</span></span>  
  
### <a name="to-attach-a-database"></a><span data-ttu-id="14d77-135">附加数据库</span><span class="sxs-lookup"><span data-stu-id="14d77-135">To Attach a Database</span></span>  
  
1.  <span data-ttu-id="14d77-136">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 对象资源管理器中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="14d77-136">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="14d77-137">右键单击“数据库”，然后单击“附加”。</span><span class="sxs-lookup"><span data-stu-id="14d77-137">Right-click **Databases** and click **Attach**.</span></span>  
  
3.  <span data-ttu-id="14d77-138">在 **“附加数据库”** 对话框中，若要指定要附加的数据库，请单击 **“添加”** ，然后在 **“定位数据库文件”** 对话框中选择数据库所在的磁盘驱动器并展开目录树，以查找并选择数据库的 .mdf 文件。例如：</span><span class="sxs-lookup"><span data-stu-id="14d77-138">In the **Attach Databases** dialog box, to specify the database to be attached, click **Add**; and in the **Locate Database Files** dialog box, select the disk drive where the database resides and expand the directory tree to find and select the .mdf file of the database; for example:</span></span>  
  
     `C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\AdventureWorks2012_Data.mdf`  
  
    > [!IMPORTANT]  
    > <span data-ttu-id="14d77-139">尝试选择已附加的数据库将生成错误。</span><span class="sxs-lookup"><span data-stu-id="14d77-139">Trying to select a database that is already attached generates an error.</span></span>  
  
     <span data-ttu-id="14d77-140">**“要附加的数据库”**</span><span class="sxs-lookup"><span data-stu-id="14d77-140">**Databases to attach**</span></span>  
     <span data-ttu-id="14d77-141">显示所选数据库的有关信息。</span><span class="sxs-lookup"><span data-stu-id="14d77-141">Displays information about the selected databases.</span></span>  
  
     \<no column header>  
     <span data-ttu-id="14d77-142">显示一个图标，用以指示附加操作的状态。</span><span class="sxs-lookup"><span data-stu-id="14d77-142">Displays an icon indicating the status of the attach operation.</span></span> <span data-ttu-id="14d77-143">下面的 **“状态”** 说明中介绍可能的图标。</span><span class="sxs-lookup"><span data-stu-id="14d77-143">The possible icons are described in the **Status** description, below).</span></span>  
  
     <span data-ttu-id="14d77-144">**MDF 文件位置**</span><span class="sxs-lookup"><span data-stu-id="14d77-144">**MDF File Location**</span></span>  
     <span data-ttu-id="14d77-145">显示选定 MDF 文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="14d77-145">Displays the path and file name of the selected MDF file.</span></span>  
  
     <span data-ttu-id="14d77-146">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="14d77-146">**Database Name**</span></span>  
     <span data-ttu-id="14d77-147">显示数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="14d77-147">Displays the name of the database.</span></span>  
  
     <span data-ttu-id="14d77-148">**附加为**</span><span class="sxs-lookup"><span data-stu-id="14d77-148">**Attach As**</span></span>  
     <span data-ttu-id="14d77-149">根据需要，可以指定要附加数据库的其他名称。</span><span class="sxs-lookup"><span data-stu-id="14d77-149">Optionally, specifies a different name for the database to attach as.</span></span>  
  
     <span data-ttu-id="14d77-150">**所有者**</span><span class="sxs-lookup"><span data-stu-id="14d77-150">**Owner**</span></span>  
     <span data-ttu-id="14d77-151">提供数据库可能所有者的下拉列表，您可以根据需要从其中选择其他所有者。</span><span class="sxs-lookup"><span data-stu-id="14d77-151">Provides a drop-down list of possible database owners from which you can optionally select a different owner.</span></span>  
  
     <span data-ttu-id="14d77-152">**Status**</span><span class="sxs-lookup"><span data-stu-id="14d77-152">**Status**</span></span>  
     <span data-ttu-id="14d77-153">显示下表中相应的数据库状态。</span><span class="sxs-lookup"><span data-stu-id="14d77-153">Displays the status of the database according to the following table.</span></span>  
  
    |<span data-ttu-id="14d77-154">图标</span><span class="sxs-lookup"><span data-stu-id="14d77-154">Icon</span></span>|<span data-ttu-id="14d77-155">状态文本</span><span class="sxs-lookup"><span data-stu-id="14d77-155">Status text</span></span>|<span data-ttu-id="14d77-156">说明</span><span class="sxs-lookup"><span data-stu-id="14d77-156">Description</span></span>|  
    |----------|-----------------|-----------------|  
    |<span data-ttu-id="14d77-157">（无图标）</span><span class="sxs-lookup"><span data-stu-id="14d77-157">(No icon)</span></span>|<span data-ttu-id="14d77-158">（无文本）</span><span class="sxs-lookup"><span data-stu-id="14d77-158">(No text)</span></span>|<span data-ttu-id="14d77-159">此对象的附加操作尚未启动或者可能挂起。</span><span class="sxs-lookup"><span data-stu-id="14d77-159">Attach operation has not been started or may be pending for this object.</span></span> <span data-ttu-id="14d77-160">这是打开该对话框时的默认值。</span><span class="sxs-lookup"><span data-stu-id="14d77-160">This is the default when the dialog is opened.</span></span>|  
    |<span data-ttu-id="14d77-161">绿色的右向三角形</span><span class="sxs-lookup"><span data-stu-id="14d77-161">Green, right-pointing triangle</span></span>|<span data-ttu-id="14d77-162">正在进行</span><span class="sxs-lookup"><span data-stu-id="14d77-162">In progress</span></span>|<span data-ttu-id="14d77-163">已启动附加操作，但是该操作未完成。</span><span class="sxs-lookup"><span data-stu-id="14d77-163">Attach operation has been started but it is not complete.</span></span>|  
    |<span data-ttu-id="14d77-164">绿色的选中标记</span><span class="sxs-lookup"><span data-stu-id="14d77-164">Green check mark</span></span>|<span data-ttu-id="14d77-165">Success</span><span class="sxs-lookup"><span data-stu-id="14d77-165">Success</span></span>|<span data-ttu-id="14d77-166">已成功附加该对象。</span><span class="sxs-lookup"><span data-stu-id="14d77-166">The object has been attached successfully.</span></span>|  
    |<span data-ttu-id="14d77-167">包含白色十字形的红色圆圈</span><span class="sxs-lookup"><span data-stu-id="14d77-167">Red circle containing a white cross</span></span>|<span data-ttu-id="14d77-168">错误</span><span class="sxs-lookup"><span data-stu-id="14d77-168">Error</span></span>|<span data-ttu-id="14d77-169">附加操作遇到错误，未成功完成。</span><span class="sxs-lookup"><span data-stu-id="14d77-169">Attach operation encountered an error and did not complete successfully.</span></span>|  
    |<span data-ttu-id="14d77-170">包含左、右两个黑色象限和上、下两个白色象限的圆圈</span><span class="sxs-lookup"><span data-stu-id="14d77-170">Circle containing two black quadrants (on left and right) and two white quadrants (on top and bottom)</span></span>|<span data-ttu-id="14d77-171">已停止</span><span class="sxs-lookup"><span data-stu-id="14d77-171">Stopped</span></span>|<span data-ttu-id="14d77-172">由于用户停止了附加操作，该操作未成功完成。</span><span class="sxs-lookup"><span data-stu-id="14d77-172">Attach operation was not completed successfully because the user stopped the operation.</span></span>|  
    |<span data-ttu-id="14d77-173">包含一个指向逆时针方向的曲线箭头的圆圈</span><span class="sxs-lookup"><span data-stu-id="14d77-173">Circle containing a curved arrow pointing counter-clockwise</span></span>|<span data-ttu-id="14d77-174">已回滚</span><span class="sxs-lookup"><span data-stu-id="14d77-174">Rolled Back</span></span>|<span data-ttu-id="14d77-175">附加操作已成功，但已对其进行回滚，因为在附加其他对象的过程中出现了错误。</span><span class="sxs-lookup"><span data-stu-id="14d77-175">Attach operation was successful but it has been rolled back due to an error during attachment of another object.</span></span>|  
  
     <span data-ttu-id="14d77-176">**消息**</span><span class="sxs-lookup"><span data-stu-id="14d77-176">**Message**</span></span>  
     <span data-ttu-id="14d77-177">显示空消息或“找不到文件”超链接。</span><span class="sxs-lookup"><span data-stu-id="14d77-177">Displays either a blank message or a "File not found" hyperlink.</span></span>  
  
     <span data-ttu-id="14d77-178">**添加**</span><span class="sxs-lookup"><span data-stu-id="14d77-178">**Add**</span></span>  
     <span data-ttu-id="14d77-179">查找必需的主数据库文件。</span><span class="sxs-lookup"><span data-stu-id="14d77-179">Find the necessary main database files.</span></span> <span data-ttu-id="14d77-180">当用户选择 .mdf 文件时，就会在 **“要附加的数据库”** 网格的相应字段中自动填充合适的信息。</span><span class="sxs-lookup"><span data-stu-id="14d77-180">When the user selects an .mdf file, applicable information is automatically filled in the respective fields of the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="14d77-181">**删除**</span><span class="sxs-lookup"><span data-stu-id="14d77-181">**Remove**</span></span>  
     <span data-ttu-id="14d77-182">从 **“要附加的数据库”** 网格中删除选定文件。</span><span class="sxs-lookup"><span data-stu-id="14d77-182">Removes the selected file from the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="14d77-183">" <database_name> " 数据库详细信息</span><span class="sxs-lookup"><span data-stu-id="14d77-183">**"** *<database_name>* **" database details**</span></span>  
     <span data-ttu-id="14d77-184">显示要附加的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="14d77-184">Displays the names of the files to be attached.</span></span> <span data-ttu-id="14d77-185">若要验证或更改文件的路径名，请单击“浏览”按钮 (…) 。</span><span class="sxs-lookup"><span data-stu-id="14d77-185">To verify or change the pathname of a file, click the **Browse** button (**...**).</span></span>  
  
    > [!NOTE]  
    > <span data-ttu-id="14d77-186">如果文件不存在，则 **“消息”** 列显示“找不到”。</span><span class="sxs-lookup"><span data-stu-id="14d77-186">If a file does not exist, the **Message** column displays "Not found."</span></span> <span data-ttu-id="14d77-187">如果找不到日志文件，则说明它位于其他目录中或者已被删除。</span><span class="sxs-lookup"><span data-stu-id="14d77-187">If a log file is not found, it exists in another directory or has been deleted.</span></span> <span data-ttu-id="14d77-188">您需要更新 **“数据库详细信息”** 网格中该文件的路径使其指向正确的位置，或者从网格中删除该日志文件。</span><span class="sxs-lookup"><span data-stu-id="14d77-188">You need to either update the file path in the **database details** grid to point to the correct location or remove the log file from the grid.</span></span> <span data-ttu-id="14d77-189">如果找不到 .ndf 数据文件，则需要更新网格中该文件的路径使其指向正确的位置。</span><span class="sxs-lookup"><span data-stu-id="14d77-189">If an .ndf data file is not found, you need to update its path in the grid to point to the correct location.</span></span>  
  
     <span data-ttu-id="14d77-190">**原始文件名**</span><span class="sxs-lookup"><span data-stu-id="14d77-190">**Original File Name**</span></span>  
     <span data-ttu-id="14d77-191">显示属于数据库的已附加文件的名称。</span><span class="sxs-lookup"><span data-stu-id="14d77-191">Displays the name of the attached file belonging to the database.</span></span>  
  
     <span data-ttu-id="14d77-192">**文件类型**</span><span class="sxs-lookup"><span data-stu-id="14d77-192">**File Type**</span></span>  
     <span data-ttu-id="14d77-193">指示文件类型，即 **“数据”** 或 **“日志”** 。</span><span class="sxs-lookup"><span data-stu-id="14d77-193">Indicates the type of file, **Data** or **Log**.</span></span>  
  
     <span data-ttu-id="14d77-194">**当前文件路径**</span><span class="sxs-lookup"><span data-stu-id="14d77-194">**Current File Path**</span></span>  
     <span data-ttu-id="14d77-195">显示所选数据库文件的路径。</span><span class="sxs-lookup"><span data-stu-id="14d77-195">Displays the path to the selected database file.</span></span> <span data-ttu-id="14d77-196">可以手动编辑该路径。</span><span class="sxs-lookup"><span data-stu-id="14d77-196">The path can be edited manually.</span></span>  
  
     <span data-ttu-id="14d77-197">**消息**</span><span class="sxs-lookup"><span data-stu-id="14d77-197">**Message**</span></span>  
     <span data-ttu-id="14d77-198">显示空消息或 **“找不到文件”** 超链接。</span><span class="sxs-lookup"><span data-stu-id="14d77-198">Displays either a blank message or a "**File not found**" hyperlink.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="14d77-199">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="14d77-199">Using Transact-SQL</span></span>  
  
### <a name="to-attach-a-database"></a><span data-ttu-id="14d77-200">附加数据库</span><span class="sxs-lookup"><span data-stu-id="14d77-200">To attach a database</span></span>  
  
1.  <span data-ttu-id="14d77-201">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="14d77-201">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="14d77-202">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="14d77-202">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="14d77-203">使用带有 close 的[CREATE DATABASE](/sql/t-sql/statements/create-database-sql-server-transact-sql)语句 `FOR ATTACH` 。</span><span class="sxs-lookup"><span data-stu-id="14d77-203">Use the [CREATE DATABASE](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the `FOR ATTACH` close.</span></span>  
  
     <span data-ttu-id="14d77-204">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="14d77-204">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="14d77-205">此示例附加 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库的文件并将该数据库重命名为 `MyAdventureWorks`。</span><span class="sxs-lookup"><span data-stu-id="14d77-205">This example attaches the files of the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database and renames the database to `MyAdventureWorks`.</span></span>  
  
    ```sql  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks_Data.mdf'),   
        (FILENAME = 'C:\MySQLServer\AdventureWorks_Log.ldf')   
        FOR ATTACH;  
    ```  
  
    > [!NOTE]  
    > <span data-ttu-id="14d77-206">或者，你可以使用 [sp_attach_db](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql) 或 [sp_attach_single_file_db](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql) 存储过程。</span><span class="sxs-lookup"><span data-stu-id="14d77-206">Alternatively, you can use the [sp_attach_db](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql) or [sp_attach_single_file_db](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql) stored procedure.</span></span> <span data-ttu-id="14d77-207">但是，Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的未来版本中将删除这些存储过程。</span><span class="sxs-lookup"><span data-stu-id="14d77-207">However, these procedures will be removed in a future version of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="14d77-208">请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="14d77-208">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span> <span data-ttu-id="14d77-209">建议使用 CREATE DATABASE .。。作为附加。</span><span class="sxs-lookup"><span data-stu-id="14d77-209">We recommend that you use CREATE DATABASE ... FOR ATTACH instead.</span></span>  
  
##  <a name="follow-up-after-upgrading-a-sql-server-database"></a><a name="FollowUp"></a> <span data-ttu-id="14d77-210">跟进：在升级 SQL Server 数据库之后</span><span class="sxs-lookup"><span data-stu-id="14d77-210">Follow Up: After Upgrading a SQL Server Database</span></span>  
 <span data-ttu-id="14d77-211">fter 使用 attach 方法升级数据库后，该数据库将立即变为可用，并自动进行升级。</span><span class="sxs-lookup"><span data-stu-id="14d77-211">fter you upgrade a database by using the attach method, the database becomes available immediately and is automatically upgraded.</span></span> <span data-ttu-id="14d77-212">如果数据库具有全文检索，升级过程将导入、重置或重新生成它们，具体取决于 **全文升级选项** 服务器属性的设置。</span><span class="sxs-lookup"><span data-stu-id="14d77-212">If the database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the **Full-Text Upgrade Option** server property.</span></span> <span data-ttu-id="14d77-213">如果将升级选项设置为“导入”或“重新生成”，在升级过程中将无法使用全文检索。</span><span class="sxs-lookup"><span data-stu-id="14d77-213">If the upgrade option is set to **Import** or **Rebuild**, the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="14d77-214">导入可能需要数小时，而重新生成所需的时间最多时可能十倍于此，具体取决于要编制索引的数据量。</span><span class="sxs-lookup"><span data-stu-id="14d77-214">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="14d77-215">另请注意，当升级选项设置为“导入”时，如果全文目录不可用，将重新生成关联的全文检索。</span><span class="sxs-lookup"><span data-stu-id="14d77-215">Note also that when the upgrade option is set to **Import**, if a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span>  
  
<span data-ttu-id="14d77-216">如果升级前用户数据库的兼容级别为 100 或更高，升级后将保持相应级别。</span><span class="sxs-lookup"><span data-stu-id="14d77-216">If the compatibility level of a user database is 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="14d77-217">如果升级前兼容级别为 90，则在升级后的数据库中，兼容级别将设置为 100，该级别为 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]支持的最低兼容级别。</span><span class="sxs-lookup"><span data-stu-id="14d77-217">If the compatibility level is 90 before upgrade, in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="14d77-218">有关详细信息，请参阅 [ALTER DATABASE 兼容级别 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)。</span><span class="sxs-lookup"><span data-stu-id="14d77-218">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14d77-219">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14d77-219">See Also</span></span>  
 <span data-ttu-id="14d77-220">[CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="14d77-220">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="14d77-221">分离数据库</span><span class="sxs-lookup"><span data-stu-id="14d77-221">Detach a Database</span></span>](detach-a-database.md)  
  
  
