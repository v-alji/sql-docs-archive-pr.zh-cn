---
title: 安装和配置语义搜索 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], installing
- semantic search [SQL Server], configuring
ms.assetid: 2cdd0568-7799-474b-82fb-65d79df3057c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8d95e0bb2adf3bacf7057b881ab2e85afd50feef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690470"
---
# <a name="install-and-configure-semantic-search"></a><span data-ttu-id="dab8c-102">安装和配置语义搜索</span><span class="sxs-lookup"><span data-stu-id="dab8c-102">Install and Configure Semantic Search</span></span>
  <span data-ttu-id="dab8c-103">说明统计语义搜索的必备组件以及如何安装或检查它们。</span><span class="sxs-lookup"><span data-stu-id="dab8c-103">Describes the prerequisites for statistical semantic search and how to install or check them.</span></span>  
  
## <a name="installing-semantic-search"></a><span data-ttu-id="dab8c-104">安装语义搜索</span><span class="sxs-lookup"><span data-stu-id="dab8c-104">Installing Semantic Search</span></span>  
  
###  <a name="how-to-check-whether-semantic-search-is-installed"></a><a name="HowToCheckInstalled"></a><span data-ttu-id="dab8c-105">如何：检查是否安装了语义搜索</span><span class="sxs-lookup"><span data-stu-id="dab8c-105">How To: Check Whether Semantic Search Is Installed</span></span>  
 <span data-ttu-id="dab8c-106">查询 [SERVERPROPERTY (Transact-SQL)](/sql/t-sql/functions/serverproperty-transact-sql) 元数据函数的 **IsFullTextInstalled** 属性。</span><span class="sxs-lookup"><span data-stu-id="dab8c-106">Query the **IsFullTextInstalled** property of the [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) metadata function.</span></span>  
  
 <span data-ttu-id="dab8c-107">返回值 1 表示安装了全文搜索和语义搜索；返回值 0 表示未安装它们。</span><span class="sxs-lookup"><span data-stu-id="dab8c-107">A return value of 1 indicates that Full-Text Search and Semantic Search are installed; a return value of 0 indicates that they are not installed.</span></span>  
  
```sql  
SELECT SERVERPROPERTY('IsFullTextInstalled');  
GO  
```  
  
###  <a name="how-to-install-semantic-search"></a><a name="BasicsSemanticSearch"></a><span data-ttu-id="dab8c-108">如何：安装语义搜索</span><span class="sxs-lookup"><span data-stu-id="dab8c-108">How To: Install Semantic Search</span></span>  
 <span data-ttu-id="dab8c-109">若要安装语义搜索，在安装过程中，请在“要安装的功能”\*\*\*\* 页上选择“全文和语义提取搜索”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dab8c-109">To install Semantic Search, select **Full-Text and Semantic Extractions for Search** on the **Features to Install** page during setup.</span></span>  
  
 <span data-ttu-id="dab8c-110">统计语义搜索依赖于全文搜索。</span><span class="sxs-lookup"><span data-stu-id="dab8c-110">Statistical Semantic Search depends on Full-Text Search.</span></span> <span data-ttu-id="dab8c-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的这两个可选功能是一起安装的。</span><span class="sxs-lookup"><span data-stu-id="dab8c-111">These two optional features of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] are installed together.</span></span>  
  
## <a name="installing-or-removing-the-semantic-language-statistics-database"></a><span data-ttu-id="dab8c-112">安装或删除语义语言统计数据库</span><span class="sxs-lookup"><span data-stu-id="dab8c-112">Installing or Removing the Semantic Language Statistics Database</span></span>  
 <span data-ttu-id="dab8c-113">语义搜索具有一个称为语义语言统计数据库的附加外部依赖项。</span><span class="sxs-lookup"><span data-stu-id="dab8c-113">Semantic Search has an additional external dependency that is called the semantic language statistics database.</span></span> <span data-ttu-id="dab8c-114">此数据库包含语义搜索所需的统计语言模型。</span><span class="sxs-lookup"><span data-stu-id="dab8c-114">This database contains the statistical language models required by semantic search.</span></span> <span data-ttu-id="dab8c-115">单个语义语言统计数据库包含语义索引支持的所有语言的语言模型。</span><span class="sxs-lookup"><span data-stu-id="dab8c-115">A single semantic language statistics database contains the language models for all the languages that are supported for semantic indexing.</span></span>  
  
###  <a name="how-to-check-whether-the-semantic-language-statistics-database-is-installed"></a><a name="HowToCheckDatabase"></a><span data-ttu-id="dab8c-116">如何：检查是否安装了语义语言统计信息数据库</span><span class="sxs-lookup"><span data-stu-id="dab8c-116">How To: Check Whether the Semantic Language Statistics Database Is Installed</span></span>  
 <span data-ttu-id="dab8c-117">查询目录视图 [sys.fulltext_semantic_language_statistics_database (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="dab8c-117">Query the catalog view [sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql).</span></span>  
  
 <span data-ttu-id="dab8c-118">如果为该实例安装并注册了语义语言统计数据库，则查询结果将包含有关该数据库的单行信息。</span><span class="sxs-lookup"><span data-stu-id="dab8c-118">If the semantic language statistics database is installed and registered for the instance, then the query results contain a single row of information about the database.</span></span>  
  
```vb  
SELECT * FROM sys.fulltext_semantic_language_statistics_database;  
GO  
```  
  
###  <a name="how-to-install-attach-and-register-the-semantic-language-statistics-database"></a><a name="HowToInstallModel"></a><span data-ttu-id="dab8c-119">如何：安装、附加和注册语义语言统计信息数据库</span><span class="sxs-lookup"><span data-stu-id="dab8c-119">How To: Install, Attach, and Register the Semantic Language Statistics Database</span></span>  
 <span data-ttu-id="dab8c-120">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装程序不安装语义语言统计数据库。</span><span class="sxs-lookup"><span data-stu-id="dab8c-120">The semantic language statistics database is not installed by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] setup program.</span></span> <span data-ttu-id="dab8c-121">若要将语义语言统计数据库设置为语义索引的必备组件，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="dab8c-121">To set up the Semantic Language Statistics database as a prerequisite for semantic indexing, do the following tasks:</span></span>  
  
 <span data-ttu-id="dab8c-122">**1.安装语义语言统计数据库。**</span><span class="sxs-lookup"><span data-stu-id="dab8c-122">**1. Install the semantic language statistics database.**</span></span>  
 1.  <span data-ttu-id="dab8c-123">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装介质上找到语义语言统计数据库，或者从 Web 上下载它。</span><span class="sxs-lookup"><span data-stu-id="dab8c-123">Locate the semantic language statistics database on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation media or download it from the Web.</span></span>  
  
    -   <span data-ttu-id="dab8c-124">在 **安装介质上找到名为** SemanticLanguageDatabase.msi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的 Windows 安装程序包。</span><span class="sxs-lookup"><span data-stu-id="dab8c-124">Locate the Windows installer package named **SemanticLanguageDatabase.msi** on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation media.</span></span> <span data-ttu-id="dab8c-125">根据目标系统，找到 32 位或 64 位版本的安装程序包。</span><span class="sxs-lookup"><span data-stu-id="dab8c-125">Locate the 32-bit or 64-bit version of the installer package depending on the target system.</span></span> <span data-ttu-id="dab8c-126">包含文件夹的名称标识 32 位或 64 位版本文件；文件名本身对于这两个版本是相同的。</span><span class="sxs-lookup"><span data-stu-id="dab8c-126">The name of the containing folder identifies the 32-bit or 64-bit version of the file; the file name itself is the same for both versions.</span></span>  
  
    -   <span data-ttu-id="dab8c-127">从[Microsoft？？下载安装程序包SQL Server？？2014语义语言统计信息](https://go.microsoft.com/fwlink/?LinkID=296743)页面 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="dab8c-127">Download the installer package from the [Microsoft?? SQL Server?? 2014 Semantic Language Statistics](https://go.microsoft.com/fwlink/?LinkID=296743) page on the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Download Center.</span></span>  
  
2.  <span data-ttu-id="dab8c-128">运行 **SemanticLanguageDatabase.msi** Windows 安装程序包，以提取数据库和日志文件。</span><span class="sxs-lookup"><span data-stu-id="dab8c-128">Run the **SemanticLanguageDatabase.msi** Windows installer package to extract the database and log file.</span></span>  
  
     <span data-ttu-id="dab8c-129">也可以选择更改目标目录。</span><span class="sxs-lookup"><span data-stu-id="dab8c-129">You can optionally change the destination directory.</span></span> <span data-ttu-id="dab8c-130">默认情况下，安装程序将文件提取到32位或 64-位 Program Files 文件夹中名为**Microsoft 语义语言数据库**的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="dab8c-130">By default, the installer extracts the files to a folder named **Microsoft Semantic Language Database** in the 32-bit or 64-bit Program Files folder.</span></span> <span data-ttu-id="dab8c-131">MSI 文件包含压缩的数据库文件和日志文件。</span><span class="sxs-lookup"><span data-stu-id="dab8c-131">The MSI file contains a compressed database file and log file.</span></span>  
  
3.  <span data-ttu-id="dab8c-132">将提取的数据库文件和日志文件移到文件系统中的合适位置。</span><span class="sxs-lookup"><span data-stu-id="dab8c-132">Move the extracted database file and log file to a suitable location in the file system.</span></span>  
  
     <span data-ttu-id="dab8c-133">如果将文件放入默认位置，则不可能为另一个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例提取数据库的另一个副本。</span><span class="sxs-lookup"><span data-stu-id="dab8c-133">If you leave the files in their default location, it will not be possible to extract another copy of the database for another instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dab8c-134">提取语义语言统计数据库时，向文件系统默认位置中的数据库文件和日志文件分配受限权限。</span><span class="sxs-lookup"><span data-stu-id="dab8c-134">When the semantic language statistics database is extracted, restricted permissions are assigned to the database file and log file in the default location in the file system.</span></span> <span data-ttu-id="dab8c-135">因此，如果将文件放入默认位置，您可能没有附加该数据库的权限。</span><span class="sxs-lookup"><span data-stu-id="dab8c-135">As a result, you may not have permission to attach the database if you leave it in the default location.</span></span> <span data-ttu-id="dab8c-136">如果在尝试附加数据库时引发了错误，请删除这些文件，或检查并根据需要修复文件系统权限。</span><span class="sxs-lookup"><span data-stu-id="dab8c-136">If an error is raised when you try to attach the database, move the files, or check and fix file system permissions as appropriate.</span></span>  
  
 <span data-ttu-id="dab8c-137">**2.附加语义语言统计数据库。**</span><span class="sxs-lookup"><span data-stu-id="dab8c-137">**2. Attach the semantic language statistics database.**</span></span>  
 <span data-ttu-id="dab8c-138">使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 或通过 **FOR ATTACH** 语法调用 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) 将数据库附加到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="dab8c-138">Attach the database to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or by calling [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) with the **FOR ATTACH** syntax.</span></span> <span data-ttu-id="dab8c-139">有关详细信息，请参阅[数据库分离和附加 (SQL Server)](../databases/database-detach-and-attach-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="dab8c-139">For more information, see [Database Detach and Attach &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md).</span></span>  
  
 <span data-ttu-id="dab8c-140">默认情况下，该数据库的名称为**semanticsdb**。</span><span class="sxs-lookup"><span data-stu-id="dab8c-140">By default, the name of the database is **semanticsdb**.</span></span> <span data-ttu-id="dab8c-141">也可以选择在附加数据库时为数据库提供其他名称。</span><span class="sxs-lookup"><span data-stu-id="dab8c-141">You can optionally give the database a different name when you attach it.</span></span> <span data-ttu-id="dab8c-142">当使用后续步骤注册数据库时，必须提供此名称。</span><span class="sxs-lookup"><span data-stu-id="dab8c-142">You have to provide this name when you register the database in the subsequent step.</span></span>  
  
```sql  
CREATE DATABASE semanticsdb  
            ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb.mdf' )  
            LOG ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb_log.ldf' )  
            FOR ATTACH;  
GO  
```  
  
 <span data-ttu-id="dab8c-143">此代码示例假定您将数据库从其默认位置移动到新位置。</span><span class="sxs-lookup"><span data-stu-id="dab8c-143">This code sample assumes that you have moved the database from its default location to a new location.</span></span>  
  
 <span data-ttu-id="dab8c-144">**3.注册语义语言统计数据库。**</span><span class="sxs-lookup"><span data-stu-id="dab8c-144">**3. Register the semantic language statistics database.**</span></span>  
 <span data-ttu-id="dab8c-145">调用 [sp_fulltext_semantic_register_language_statistics_db (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql) 存储过程，并提供在附加数据库时向该数据库提供的名称。</span><span class="sxs-lookup"><span data-stu-id="dab8c-145">Call the stored procedure [sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql) and provide the name that you gave to the database when you attached it.</span></span>  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = N'semanticsdb';  
GO  
```  
  
###  <a name="how-to-unregister-detach-and-remove-the-semantic-language-statistics-database"></a><a name="HowToUnregister"></a><span data-ttu-id="dab8c-146">如何取消注册、分离和删除语义语言统计信息数据库</span><span class="sxs-lookup"><span data-stu-id="dab8c-146">How To: Unregister, Detach, and Remove the Semantic Language Statistics Database</span></span>  
 <span data-ttu-id="dab8c-147">**取消注册语义语言统计数据库。**</span><span class="sxs-lookup"><span data-stu-id="dab8c-147">**Unregister the semantic language statistics database.**</span></span>  
 <span data-ttu-id="dab8c-148">调用 [sp_fulltext_semantic_unregister_language_statistics_db (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql) 存储过程。</span><span class="sxs-lookup"><span data-stu-id="dab8c-148">Call the stored procedure [sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql).</span></span> <span data-ttu-id="dab8c-149">由于一个实例仅有一个语义语言统计数据库，因此您不必提供该数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="dab8c-149">You do not have to provide the name of the database since an instance can have only one semantic language statistics database.</span></span>  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
 <span data-ttu-id="dab8c-150">**分离语义语言统计数据库。**</span><span class="sxs-lookup"><span data-stu-id="dab8c-150">**Detach the semantic language statistics database.**</span></span>  
 <span data-ttu-id="dab8c-151">调用 [sp_detach_db (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql) 存储过程并提供该数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="dab8c-151">Call the stored procedure [sp_detach_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql) and provide the name of the database.</span></span>  
  
```sql  
USE master;  
GO  
  
EXEC sp_detach_db @dbname = N'semanticsdb';  
GO  
```  
  
 <span data-ttu-id="dab8c-152">**删除语义语言统计数据库。**</span><span class="sxs-lookup"><span data-stu-id="dab8c-152">**Remove the semantic language statistics database.**</span></span>  
 <span data-ttu-id="dab8c-153">撤消注册并分离该数据库后，您可以删除数据库文件。</span><span class="sxs-lookup"><span data-stu-id="dab8c-153">After unregistering and detaching the database, you can simply delete the database file.</span></span> <span data-ttu-id="dab8c-154">不提供卸载程序，在“控制面板”的 **“程序和功能”** 中没有相应条目。</span><span class="sxs-lookup"><span data-stu-id="dab8c-154">There is no uninstall program and there is no entry in **Programs and Features** in the Control Panel.</span></span>  
  
###  <a name="requirements-and-restrictions-for-installing-and-removing-the-semantic-language-statistics-database"></a><a name="reqinstall"></a><span data-ttu-id="dab8c-155">安装和删除语义语言统计信息数据库的要求和限制</span><span class="sxs-lookup"><span data-stu-id="dab8c-155">Requirements and Restrictions for Installing and Removing the Semantic Language Statistics Database</span></span>  
  
-   <span data-ttu-id="dab8c-156">在一个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例上只能附加和注册一个语义语言统计数据库。</span><span class="sxs-lookup"><span data-stu-id="dab8c-156">You can only attach and register one semantic language statistics database on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="dab8c-157">单个计算机上的每个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例都需要一个单独的语义语言统计数据库的物理副本。</span><span class="sxs-lookup"><span data-stu-id="dab8c-157">Each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on a single computer requires a separate physical copy of the semantic language statistics database.</span></span> <span data-ttu-id="dab8c-158">对每个实例附加一个副本。</span><span class="sxs-lookup"><span data-stu-id="dab8c-158">Attach one copy to each instance.</span></span>  
  
-   <span data-ttu-id="dab8c-159">您不能分离注册的有效语义语言统计数据库，并将其替换为一个任意同名的数据库。</span><span class="sxs-lookup"><span data-stu-id="dab8c-159">You cannot detach a valid and registered semantic language statistics database and replace it with an arbitrary database that has the same name.</span></span> <span data-ttu-id="dab8c-160">这样做将导致当前或未来的索引填充失败。</span><span class="sxs-lookup"><span data-stu-id="dab8c-160">Doing so will cause active or future index populations to fail.</span></span>  
  
-   <span data-ttu-id="dab8c-161">语义语言统计数据库是只读的。</span><span class="sxs-lookup"><span data-stu-id="dab8c-161">The semantic language statistics database is read-only.</span></span> <span data-ttu-id="dab8c-162">您不能自定义此数据库。</span><span class="sxs-lookup"><span data-stu-id="dab8c-162">You cannot customize this database.</span></span> <span data-ttu-id="dab8c-163">如果您以任何方式更改数据库的内容，未来语义索引的结果将是不确定的。</span><span class="sxs-lookup"><span data-stu-id="dab8c-163">If you alter the content of the database in any way, the results for future semantic indexing are indeterministic.</span></span> <span data-ttu-id="dab8c-164">若要恢复此数据的原始状态，您可以删除已更改的数据库，然后下载并附加未更改的数据库新副本。</span><span class="sxs-lookup"><span data-stu-id="dab8c-164">To restore the original state of this data, you can drop the altered database, and download and attach a new and unaltered copy of the database.</span></span>  
  
-   <span data-ttu-id="dab8c-165">可以分离或删除语义语言统计数据库。</span><span class="sxs-lookup"><span data-stu-id="dab8c-165">It is possible to detach or drop the semantic language statistics database.</span></span> <span data-ttu-id="dab8c-166">如果有对数据库具有读取锁定的任何活动索引操作，则分离或删除操作将失败或超时。这与现有行为一致。</span><span class="sxs-lookup"><span data-stu-id="dab8c-166">If there are any active indexing operations that have read locks on the database, then the detach or drop operation will fail or time out. This is consistent with existing behavior.</span></span> <span data-ttu-id="dab8c-167">删除该数据库后，任何语义索引操作都将失败。</span><span class="sxs-lookup"><span data-stu-id="dab8c-167">After the database is removed, semantic indexing operations will fail.</span></span>  
  
## <a name="installing-optional-support-for-newer-document-types"></a><span data-ttu-id="dab8c-168">为较新文档类型安装可选支持</span><span class="sxs-lookup"><span data-stu-id="dab8c-168">Installing Optional Support for Newer Document Types</span></span>  
  
###  <a name="how-to-install-the-latest-filters-for-microsoft-office-and-other-microsoft-document-types"></a><a name="office"></a><span data-ttu-id="dab8c-169">如何：为 Microsoft Office 和其他 Microsoft 文档类型安装最新筛选器</span><span class="sxs-lookup"><span data-stu-id="dab8c-169">How to: Install the Latest Filters for Microsoft Office and other Microsoft Document Types</span></span>  
 <span data-ttu-id="dab8c-170">此版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装最新的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 断字符和词干分析器，但是不为 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office 文档和其他 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 文档类型安装最新的筛选器。</span><span class="sxs-lookup"><span data-stu-id="dab8c-170">This release of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installs the latest [!INCLUDE[msCoName](../../../includes/msconame-md.md)] word breakers and stemmers, but does not install the latest filters for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office documents and other [!INCLUDE[msCoName](../../../includes/msconame-md.md)] document types.</span></span> <span data-ttu-id="dab8c-171">要为使用最新版本的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office 和其他 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 应用程序创建的文档编制索引，必须安装这些筛选器。</span><span class="sxs-lookup"><span data-stu-id="dab8c-171">These filters are required for indexing documents created with recent versions of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office and other [!INCLUDE[msCoName](../../../includes/msconame-md.md)] applications.</span></span> <span data-ttu-id="dab8c-172">若要下载最新的筛选器，请参阅 [Microsoft Office 2010 Filter Packs](https://www.microsoft.com/download/details.aspx?id=17062)。</span><span class="sxs-lookup"><span data-stu-id="dab8c-172">To download the latest filters, see [Microsoft Office 2010 Filter Packs](https://www.microsoft.com/download/details.aspx?id=17062).</span></span>  
  
  
