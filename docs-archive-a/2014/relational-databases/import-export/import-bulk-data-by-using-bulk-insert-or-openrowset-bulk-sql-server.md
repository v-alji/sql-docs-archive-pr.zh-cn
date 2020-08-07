---
title: 使用 BULK INSERT 或 OPENROWSET(BULK...) 导入批量数据 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- BULK INSERT statement, importing data from a remote data file
- bulk importing [SQL Server], methods
- bulk exporting [SQL Server], methods
- OPENROWSET function, BULK INSERT
- bulk importing [SQL Server], security
- bulk rowset providers [SQL Server]
- bulk exporting [SQL Server], BULK INSERT statement
- remote data access [SQL Server], bulk importing
- bulk importing [SQL Server], BULK INSERT statement
- Transact-SQL bulk export/import operations
ms.assetid: 18a64236-0285-46ea-8929-6ee9bcc020b9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: be36167020b96dba6d494685d958c38e0e6afbba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589076"
---
# <a name="import-bulk-data-by-using-bulk-insert-or-openrowsetbulk-sql-server"></a><span data-ttu-id="5aac9-102">使用 BULK INSERT 或 OPENROWSET(BULK...) 导入批量数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-102">Import Bulk Data by Using BULK INSERT or OPENROWSET(BULK...) (SQL Server)</span></span>
  <span data-ttu-id="5aac9-103">本主题概述了如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] BULK INSERT 语句和 INSERT...SELECT \* FROM OPENROWSET(BULK...) 语句将数据从某一数据文件大容量导入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中。</span><span class="sxs-lookup"><span data-stu-id="5aac9-103">This topic provides an overview of how to use the [!INCLUDE[tsql](../../includes/tsql-md.md)] BULK INSERT statement and the INSERT...SELECT \* FROM OPENROWSET(BULK...) statement to bulk import data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="5aac9-104">本主题还说明了使用 BULK INSERT 和 OPENROWSET(BULK...) 以及使用这些方法从远程数据源大容量导入数据的安全注意事项。</span><span class="sxs-lookup"><span data-stu-id="5aac9-104">This topic also describes security considerations for using BULK INSERT and OPENROWSET(BULK...), and using these methods to bulk import from a remote data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5aac9-105">在使用 BULK INSERT 或 OPENROWSET(BULK...) 时，请务必了解 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本处理模拟的方式。</span><span class="sxs-lookup"><span data-stu-id="5aac9-105">When you use BULK INSERT or OPENROWSET(BULK...), it is important to understand how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version handles impersonation.</span></span> <span data-ttu-id="5aac9-106">有关详细信息，请参阅本主题后面的“安全注意事项”。</span><span class="sxs-lookup"><span data-stu-id="5aac9-106">For more information, see "Security Considerations," later in this topic.</span></span>  
  
## <a name="bulk-insert-statement"></a><span data-ttu-id="5aac9-107">BULK INSERT 语句</span><span class="sxs-lookup"><span data-stu-id="5aac9-107">BULK INSERT Statement</span></span>  
 <span data-ttu-id="5aac9-108">BULK INSERT 将数据从数据文件加载到表中。</span><span class="sxs-lookup"><span data-stu-id="5aac9-108">BULK INSERT loads data from a data file into a table.</span></span> <span data-ttu-id="5aac9-109">此功能与 **bcp** 命令的 **in** 选项提供的功能相似，但是数据文件将由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程读取。</span><span class="sxs-lookup"><span data-stu-id="5aac9-109">This functionality is similar to that provided by the **in** option of the **bcp** command; however, the data file is read by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="5aac9-110">有关 BULK INSERT 语法的说明，请参阅 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5aac9-110">For a description of the BULK INSERT syntax, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="5aac9-111">示例</span><span class="sxs-lookup"><span data-stu-id="5aac9-111">Examples</span></span>  
 <span data-ttu-id="5aac9-112">有关 BULK INSERT 示例，请参阅：</span><span class="sxs-lookup"><span data-stu-id="5aac9-112">For BULK INSERT examples, see:</span></span>  
  
-   [<span data-ttu-id="5aac9-113">BULK INSERT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5aac9-113">BULK INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
-   [<span data-ttu-id="5aac9-114">批量导入和导出 XML 文档的示例 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-114">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-115">批量导入数据时保留标识值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-115">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-116">在批量导入期间保留 Null 或使用默认值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-116">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-117">指定字段终止符和行终止符 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-117">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-118">使用格式化文件批量导入数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-118">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-119">使用字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-119">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-120">使用本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-120">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-121">使用 Unicode 字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-121">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-122">使用 Unicode 本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-122">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-123">使用格式化文件跳过表列 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-123">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-124">使用格式化文件将表列映射到数据文件字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-124">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="openrowsetbulk-function"></a><span data-ttu-id="5aac9-125">OPENROWSET(BULK…)函数</span><span class="sxs-lookup"><span data-stu-id="5aac9-125">OPENROWSET(BULK...) Function</span></span>  
 <span data-ttu-id="5aac9-126">通过调用 OPENROWSET 函数并指定 BULK 选项，访问 OPENROWSET 大容量行集提供程序。</span><span class="sxs-lookup"><span data-stu-id="5aac9-126">The OPENROWSET bulk rowset provider is accessed by calling the OPENROWSET function and specifying the BULK option.</span></span> <span data-ttu-id="5aac9-127">使用 OPENROWSET(BULK...) 函数可以通过 OLE DB 访问接口连接到远程数据源（如数据文件）以访问远程数据。</span><span class="sxs-lookup"><span data-stu-id="5aac9-127">The OPENROWSET(BULK...) function allows you to access remote data by connecting to a remote data source, such as a data file, through an OLE DB provider.</span></span>  
  
 <span data-ttu-id="5aac9-128">若要大容量导入数据，请从 INSERT 语句中的 SELECT...FROM 子句调用 OPENROWSET(BULK...)。</span><span class="sxs-lookup"><span data-stu-id="5aac9-128">To bulk import data, call OPENROWSET(BULK...) from a SELECT...FROM clause within an INSERT statement.</span></span> <span data-ttu-id="5aac9-129">大容量导入数据的基本语法如下：</span><span class="sxs-lookup"><span data-stu-id="5aac9-129">The basic syntax for bulk importing data is:</span></span>  
  
 <span data-ttu-id="5aac9-130">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="5aac9-130">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
  
 <span data-ttu-id="5aac9-131">在 INSERT 语句中使用时，OPENROWSET(BULK...) 支持表提示。</span><span class="sxs-lookup"><span data-stu-id="5aac9-131">When used in an INSERT statement, OPENROWSET(BULK...) supports table hints.</span></span> <span data-ttu-id="5aac9-132">除了常规表提示（例如 TABLOCK），BULK 子句还可以接受以下专用表提示：IGNORE_CONSTRAINTS（仅忽略 CHECK 约束）、IGNORE_TRIGGERS、KEEPDEFAULTS 和 KEEPIDENTITY。</span><span class="sxs-lookup"><span data-stu-id="5aac9-132">In addition to the regular table hints, such as TABLOCK, the BULK clause can accept the following specialized table hints: IGNORE_CONSTRAINTS (ignores only the CHECK constraints), IGNORE_TRIGGERS, KEEPDEFAULTS, and KEEPIDENTITY.</span></span> <span data-ttu-id="5aac9-133">有关详细信息，请参阅[表提示 (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-table)。</span><span class="sxs-lookup"><span data-stu-id="5aac9-133">For more information, see [Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span></span>  
  
 <span data-ttu-id="5aac9-134">有关 BULK 选项的更多使用信息，请参阅 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5aac9-134">For information about additional uses of the BULK option, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="5aac9-135">示例</span><span class="sxs-lookup"><span data-stu-id="5aac9-135">Examples</span></span>  
 <span data-ttu-id="5aac9-136">有关 INSERT...SELECT \* FROM OPENROWSET(BULK...) 语句的示例，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="5aac9-136">For examples of INSERT...SELECT \* FROM OPENROWSET(BULK...) statements, see the following topics:</span></span>  
  
-   [<span data-ttu-id="5aac9-137">批量导入和导出 XML 文档的示例 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-137">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-138">批量导入数据时保留标识值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-138">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-139">在批量导入期间保留 Null 或使用默认值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-139">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-140">使用格式化文件批量导入数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-140">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-141">使用字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-141">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-142">使用格式化文件跳过表列 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-142">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-143">使用格式化文件跳过数据字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-143">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="5aac9-144">使用格式化文件将表列映射到数据文件字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5aac9-144">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="security-considerations"></a><span data-ttu-id="5aac9-145">安全注意事项</span><span class="sxs-lookup"><span data-stu-id="5aac9-145">Security Considerations</span></span>  
 <span data-ttu-id="5aac9-146">如果用户使用的是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名，则系统将使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程帐户的安全配置文件。</span><span class="sxs-lookup"><span data-stu-id="5aac9-146">If a user uses a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login, the security profile of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process account is used.</span></span> <span data-ttu-id="5aac9-147">使用 SQL Server 身份验证的登录名不能在数据库引擎外部进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="5aac9-147">A login using SQL Server authentication cannot be authenticated outside of the Database Engine.</span></span> <span data-ttu-id="5aac9-148">因此，当 BULK INSERT 命令由使用 SQL Server 身份验证的登录名启动时，使用 SQL Server 进程帐户（SQL Server 数据库引擎服务使用的帐户）的安全上下文建立到数据的连接。</span><span class="sxs-lookup"><span data-stu-id="5aac9-148">Therefore, when a BULK INSERT command is initiated by a login using SQL Server authentication, the connection to the data is made using the security context of the SQL Server process account (the account used by the SQL Server Database Engine service).</span></span> <span data-ttu-id="5aac9-149">要成功读取源数据，您必须授予 SQL Server 数据库引擎使用的帐户访问源数据的权限。</span><span class="sxs-lookup"><span data-stu-id="5aac9-149">To successfully read the source data you must grant the account used by the SQL Server Database Engine, access to the source data.</span></span> <span data-ttu-id="5aac9-150">与此相反，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户使用 Windows 身份验证登录，则该用户只能读取用户帐户可以访问的那些文件，而不考虑 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程的安全配置文件。</span><span class="sxs-lookup"><span data-stu-id="5aac9-150">In contrast, if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user logs on by using Windows Authentication, the user can read only those files that can be accessed by the user account, regardless of the security profile of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span>  
  
 <span data-ttu-id="5aac9-151">例如，假设用户使用 Windows 身份验证登录到某个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="5aac9-151">For example, consider a user who logged in to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span> <span data-ttu-id="5aac9-152">对于能够使用 BULK INSERT 或 OPENROWSET 将数据从数据文件导入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中的用户，用户帐户需要具有数据文件的读取权限。</span><span class="sxs-lookup"><span data-stu-id="5aac9-152">For the user to be able to use BULK INSERT or OPENROWSET to import data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, the user account requires read access to the data file.</span></span> <span data-ttu-id="5aac9-153">有了数据文件的访问权限，即使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程没有访问该文件的权限，用户也可以将数据从文件导入表中。</span><span class="sxs-lookup"><span data-stu-id="5aac9-153">With access to the data file, the user can import data from the file into a table even if the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process does not have permission to access the file.</span></span> <span data-ttu-id="5aac9-154">用户无需将文件访问权限授予 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程。</span><span class="sxs-lookup"><span data-stu-id="5aac9-154">The user does not have to grant file-access permission to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5aac9-155">和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows，使得一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例可以通过转发已经过身份验证的 Windows 用户的凭据来连接到另一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="5aac9-155">and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows can be configured to enable an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to connect to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by forwarding the credentials of an authenticated Windows user.</span></span> <span data-ttu-id="5aac9-156">这种安排称为“模拟”  或“委托” 。</span><span class="sxs-lookup"><span data-stu-id="5aac9-156">This arrangement is known as *impersonation* or *delegation*.</span></span> <span data-ttu-id="5aac9-157">在使用 BULK INSERT 或 OPENROWSET 时，请务必了解 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本是如何处理用户模拟的安全性的。</span><span class="sxs-lookup"><span data-stu-id="5aac9-157">Understanding how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version handle security for user impersonation is important when you use BULK INSERT or OPENROWSET.</span></span> <span data-ttu-id="5aac9-158">用户模拟允许数据文件保存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程或用户所在的计算机以外的另一台计算机上。</span><span class="sxs-lookup"><span data-stu-id="5aac9-158">User impersonation allows the data file to reside on a different computer than either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process or the user.</span></span> <span data-ttu-id="5aac9-159">例如，如果 **Computer_A** 上的用户具有对 **Computer_B**上的数据文件的访问权限，而且凭据委托已设置妥当，则用户可以连接到运行在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Computer_C **上的**实例，访问 **Computer_B**中的数据文件以及将数据从该文件大容量导入到 **Computer_C**中的表中。</span><span class="sxs-lookup"><span data-stu-id="5aac9-159">For example, if a user on **Computer_A** has access to a data file on **Computer_B**, and the delegation of credentials has been set appropriately, the user can connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on **Computer_C**, access the data file on **Computer_B**, and bulk import data from that file into a table on **Computer_C**.</span></span>  
  
## <a name="bulk-importing-from-a-remote-data-file"></a><span data-ttu-id="5aac9-160">从远程数据文件中大容量导入</span><span class="sxs-lookup"><span data-stu-id="5aac9-160">Bulk Importing from a Remote Data File</span></span>  
 <span data-ttu-id="5aac9-161">若要使用 BULK INSERT 或 INSERT...SELECT \* FROM OPENROWSET(BULK...) 从其他计算机中大容量导入数据，必须在两台计算机之间共享数据文件。</span><span class="sxs-lookup"><span data-stu-id="5aac9-161">To use BULK INSERT or INSERT...SELECT \* FROM OPENROWSET(BULK...) to bulk import data from another computer, the data file must be shared between the two computers.</span></span> <span data-ttu-id="5aac9-162">指定共享数据文件时，请使用它的通用命名约定 (UNC) 名称，其一般形式为 **\\\\** _服务器名_ **\\** _共享名_ **\\** _路径_ **\\** _文件名_。</span><span class="sxs-lookup"><span data-stu-id="5aac9-162">To specify a shared data file, use its universal naming convention (UNC) name, which takes the general form, **\\\\**_Servername_**\\**_Sharename_**\\**_Path_**\\**_Filename_.</span></span> <span data-ttu-id="5aac9-163">此外，用来访问该数据文件的帐户必须具有读取远程磁盘上的文件所需的权限。</span><span class="sxs-lookup"><span data-stu-id="5aac9-163">Additionally, the account used to access the data file must have the permissions that are required for reading the file on the remote disk.</span></span>  
  
 <span data-ttu-id="5aac9-164">例如，下面的 `BULK INSERT` 语句会将名为 `SalesOrderDetail` 的数据文件中的数据大容量导入到 `AdventureWorks` 数据库的 `newdata.txt`表。</span><span class="sxs-lookup"><span data-stu-id="5aac9-164">For example, the following `BULK INSERT` statement bulk imports data into the `SalesOrderDetail` table of the `AdventureWorks` database from a data file that is named `newdata.txt`.</span></span> <span data-ttu-id="5aac9-165">此数据文件驻留在系统 `\dailyorders` 的 `salesforce` 网络共享目录下的 `computer2`共享文件夹中。</span><span class="sxs-lookup"><span data-stu-id="5aac9-165">This data file resides in a shared folder named `\dailyorders` on a network share directory named `salesforce` on a system named `computer2`.</span></span>  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM '\\computer2\salesforce\dailyorders\neworders.txt';  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="5aac9-166">此限制不适用于 **bcp** 实用工具，因为客户端独立于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 读取文件。</span><span class="sxs-lookup"><span data-stu-id="5aac9-166">This restriction does not apply to the **bcp** utility because the client reads the file independently of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aac9-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5aac9-167">See Also</span></span>  
 <span data-ttu-id="5aac9-168">[INSERT (Transact-SQL)](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5aac9-168">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="5aac9-169">[SELECT 子句 (Transact-SQL)](/sql/t-sql/queries/select-clause-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5aac9-169">[SELECT Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span></span>  
 <span data-ttu-id="5aac9-170">[批量导入和导出数据 (SQL Server)](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5aac9-170">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="5aac9-171">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5aac9-171">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="5aac9-172">[SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5aac9-172">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 <span data-ttu-id="5aac9-173">[FROM (Transact-SQL)](/sql/t-sql/queries/from-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5aac9-173">[FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) </span></span>  
 <span data-ttu-id="5aac9-174">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="5aac9-174">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 [<span data-ttu-id="5aac9-175">BULK INSERT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5aac9-175">BULK INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
  
