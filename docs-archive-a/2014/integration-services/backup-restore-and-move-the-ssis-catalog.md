---
title: 备份、还原和移动 SSIS 目录 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bf806aef-8556-48ab-aed5-e95de9a2204e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9de552ddd54168f516f42d9988302561616fd65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580855"
---
# <a name="backup-restore-and-move-the-ssis-catalog"></a><span data-ttu-id="65b74-102">备份、还原和移动 SSIS 目录</span><span class="sxs-lookup"><span data-stu-id="65b74-102">Backup, Restore, and Move the SSIS Catalog</span></span>
  [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] <span data-ttu-id="65b74-103">包含 SSISDB 数据库。</span><span class="sxs-lookup"><span data-stu-id="65b74-103">includes the SSISDB database.</span></span> <span data-ttu-id="65b74-104">查询 SSISDB 数据库中的视图可以检查 **SSISDB** 目录中存储的对象、设置和操作数据。</span><span class="sxs-lookup"><span data-stu-id="65b74-104">You query views in the SSISDB database to inspect objects, settings, and operational data that are stored in the **SSISDB** catalog.</span></span> <span data-ttu-id="65b74-105">本主题说明如何备份和还原该数据库。</span><span class="sxs-lookup"><span data-stu-id="65b74-105">This topic provides instructions for backing up and restoring the database.</span></span>  
  
 <span data-ttu-id="65b74-106">SSISDB 目录存储部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器的包。</span><span class="sxs-lookup"><span data-stu-id="65b74-106">The **SSISDB** catalog stores the packages that you've deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="65b74-107">有关该目录的详细信息，请参阅 [SSIS 目录](catalog/ssis-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="65b74-107">For more information about the catalog, see [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
##  <a name="to-back-up-the-ssis-database"></a><a name="backup"></a> <span data-ttu-id="65b74-108">备份 SSIS 数据库</span><span class="sxs-lookup"><span data-stu-id="65b74-108">To Back up the SSIS Database</span></span>  
  
1.  <span data-ttu-id="65b74-109">打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 并连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="65b74-109">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="65b74-110">使用 BACKUP MASTER KEY Transact-SQL 语句备份 SSISDB 数据库的主密钥。</span><span class="sxs-lookup"><span data-stu-id="65b74-110">Back up the master key for the SSISDB database, by using the BACKUP MASTER KEY Transact-SQL statement.</span></span> <span data-ttu-id="65b74-111">该密钥存储在您指定的文件中。</span><span class="sxs-lookup"><span data-stu-id="65b74-111">The key is stored in a file that you specify.</span></span> <span data-ttu-id="65b74-112">使用密码加密该文件中的主密钥。</span><span class="sxs-lookup"><span data-stu-id="65b74-112">Use a password to encrypt the master key in the file.</span></span>  
  
     <span data-ttu-id="65b74-113">有关语句的详细信息，请参阅 [BACKUP MASTER KEY (Transact-SQL)](/sql/t-sql/statements/backup-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="65b74-113">For more information about the statement, see [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).</span></span>  
  
     <span data-ttu-id="65b74-114">在下面的示例中，将主密钥导出到 `c:\temp directory\RCTestInstKey` 文件。</span><span class="sxs-lookup"><span data-stu-id="65b74-114">In the following example, the master key is exported to the `c:\temp directory\RCTestInstKey` file.</span></span> <span data-ttu-id="65b74-115">使用 `LS2Setup!` 密码加密主密钥。</span><span class="sxs-lookup"><span data-stu-id="65b74-115">The `LS2Setup!` password is used to encrypt the master key.</span></span>  
  
    ```  
    backup master key to file = 'c:\temp\RCTestInstKey'  
           encryption by password = 'LS2Setup!'  
  
    ```  
  
3.  <span data-ttu-id="65b74-116">在 **中使用** “备份数据库” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]对话框备份 SSISDB 数据库。</span><span class="sxs-lookup"><span data-stu-id="65b74-116">Back up the SSISDB database by using the **Backup Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="65b74-117">有关详细信息，请参阅[操作说明：备份数据库 (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=231812)。</span><span class="sxs-lookup"><span data-stu-id="65b74-117">For more information, see [How to: Back Up a Database (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=231812).</span></span>  
  
4.  <span data-ttu-id="65b74-118">通过执行以下操作，生成 ##MS_SSISServerCleanupJobLogin## 的 CREATE LOGIN 脚本。</span><span class="sxs-lookup"><span data-stu-id="65b74-118">Generate the CREATE LOGIN script for ##MS_SSISServerCleanupJobLogin##, by doing the following.</span></span> <span data-ttu-id="65b74-119">有关详细信息，请参阅 [CREATE LOGIN (Transact-SQL)](/sql/t-sql/statements/create-login-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="65b74-119">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
    1.  <span data-ttu-id="65b74-120">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]的对象资源管理器中，展开 **“安全性”** 节点，然后展开 **“登录名”** 节点。</span><span class="sxs-lookup"><span data-stu-id="65b74-120">In Object Explorer in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the **Security** node and then expand the **Logins** node.</span></span>  
  
    2.  <span data-ttu-id="65b74-121">右键单击 **##MS_SSISServerCleanupJobLogin##** ，然后依次单击“编写登录脚本为” > “CREATE 到” > “新查询编辑器窗口”。  </span><span class="sxs-lookup"><span data-stu-id="65b74-121">Right-click **##MS_SSISServerCleanupJobLogin##**, and then click **Script Login as** > **CREATE To** > **New Query Editor Window**.</span></span>  
  
5.  <span data-ttu-id="65b74-122">如果要将 SSISDB 数据库还原到从未创建 SSISDB 目录的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，请执行以下操作生成 sp_ssis_startup 的 CREATE PROCEDURE 脚本。</span><span class="sxs-lookup"><span data-stu-id="65b74-122">If you will be restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, generate the CREATE PROCEDURE script for sp_ssis_startup, by doing the following.</span></span> <span data-ttu-id="65b74-123">有关详细信息，请参阅 [CREATE PROCEDURE (Transact-SQL)](/sql/t-sql/statements/create-procedure-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="65b74-123">For more information, see [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).</span></span>  
  
    1.  <span data-ttu-id="65b74-124">在对象资源管理器中，展开 "**数据库**" 节点，然后展开 "**系统数据库**" "  >  **主**  >  **可编程性**" "  >  **存储过程**" 节点。</span><span class="sxs-lookup"><span data-stu-id="65b74-124">In Object Explorer, expand the **Databases** node and then expand the **System Databases** > **master** > **Programmability** > **Stored Procedures** node.</span></span>  
  
    2.  <span data-ttu-id="65b74-125">右键单击 **dbo.sp_ssis_startup**，然后依次单击“编写存储过程脚本为” > “CREATE 到” > “新查询编辑器窗口”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="65b74-125">Right click **dbo.sp_ssis_startup**, and then click **Script Stored Procedure as** > **CREATE To** > **New Query Editor Window**.</span></span>  
  
6.  <span data-ttu-id="65b74-126">确认 SQL Server 代理已启动</span><span class="sxs-lookup"><span data-stu-id="65b74-126">Confirm that SQL Server Agent has been started</span></span>  
  
7.  <span data-ttu-id="65b74-127">如果要将 SSISDB 数据库还原到从不创建 SSISDB 目录的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，请执行以下操作生成 SSIS 服务器维护作业的脚本。</span><span class="sxs-lookup"><span data-stu-id="65b74-127">If you will be restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, generate a script for the SSIS Server Maintenance Job by doing the following.</span></span> <span data-ttu-id="65b74-128">创建 SSISDB 目录时自动在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理中创建该脚本。</span><span class="sxs-lookup"><span data-stu-id="65b74-128">The script is created in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent automatically when the SSISDB catalog is created.</span></span> <span data-ttu-id="65b74-129">该作业帮助清除保留期窗口之外的操作日志并删除较旧版本的项目。</span><span class="sxs-lookup"><span data-stu-id="65b74-129">The job helps clean up cleanup operation logs outside the retention window and remove older versions of projects.</span></span>  
  
    1.  <span data-ttu-id="65b74-130">在对象资源管理器中，展开 **“SQL Server 代理”** 节点，然后展开 **“作业”** 节点。</span><span class="sxs-lookup"><span data-stu-id="65b74-130">In Object Explorer, expand the **SQL Server Agent** node and then expand the **Jobs** node.</span></span>  
  
    2.  <span data-ttu-id="65b74-131">右键单击 "SSIS 服务器维护作业"，然后**Script Job as**单击 "  >  **创建到**  >  **新查询编辑器窗口**的脚本作业"。</span><span class="sxs-lookup"><span data-stu-id="65b74-131">Right click SSIS Server Maintenance Job, and then click **Script Job as** > **CREATE To** > **New Query Editor Window**.</span></span>  
  
### <a name="to-restore-the-ssis-database"></a><span data-ttu-id="65b74-132">还原 SSIS 数据库</span><span class="sxs-lookup"><span data-stu-id="65b74-132">To Restore the SSIS Database</span></span>  
  
1.  <span data-ttu-id="65b74-133">如果要将 SSISDB 数据库还原到从不创建 SSISDB 目录的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，请通过运行 sp_configure 存储过程来启用公共语言运行时 (clr)。</span><span class="sxs-lookup"><span data-stu-id="65b74-133">If you are restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, enable common language runtime (clr) by running the sp_configure stored procedure.</span></span> <span data-ttu-id="65b74-134">有关详细信息，请参阅 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 和 [clr enabled 选项](https://go.microsoft.com/fwlink/?LinkId=231855)。</span><span class="sxs-lookup"><span data-stu-id="65b74-134">For more information, see [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) and [clr enabled Option](https://go.microsoft.com/fwlink/?LinkId=231855).</span></span>  
  
    ```  
    use master   
           sp_configure 'clr enabled', 1  
           reconfigure  
  
    ```  
  
2.  <span data-ttu-id="65b74-135">如果要将 SSISDB 数据库还原到从不创建 SSISDB 目录的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，请创建非对称密钥和对应非对称密钥的登录名并将 UNSAFE 权限授予该登录名。</span><span class="sxs-lookup"><span data-stu-id="65b74-135">If you are restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, create the asymmetric key and the login from the asymmetric key, and grant UNSAFE permission to the login.</span></span>  
  
    ```  
    Create Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey  
           FROM Executable File = 'C:\Program Files\Microsoft SQL Server\110\DTS\Binn\Microsoft.SqlServer.IntegrationServices.Server.dll'  
  
    ```  
  
     [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="65b74-136">CLR 存储过程要求将 UNSAFE 权限授予该登录名，因为该登录名需要对受限制资源（如 Microsoft Win32 API）的更高访问权限。</span><span class="sxs-lookup"><span data-stu-id="65b74-136">CLR stored procedures require UNSAFE permissions to be granted to the login because the login requires additional access to restricted resources, such as the Microsoft Win32 API.</span></span> <span data-ttu-id="65b74-137">有关 UNSAFE 代码权限的详细信息，请参阅 [Creating an Assembly](../relational-databases/clr-integration/assemblies/creating-an-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="65b74-137">For more information about the UNSAFE code permission, see [Creating an Assembly](../relational-databases/clr-integration/assemblies/creating-an-assembly.md).</span></span>  
  
    ```  
    Create Login MS_SQLEnableSystemAssemblyLoadingUser  
           FROM Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey   
  
           Grant unsafe Assembly to MS_SQLEnableSystemAssemblyLoadingUser  
  
    ```  
  
3.  <span data-ttu-id="65b74-138">在 **中使用** “还原数据库” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]对话框从备份中还原 SSISDB 数据库。</span><span class="sxs-lookup"><span data-stu-id="65b74-138">Restore the SSISDB database from the backup by using the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="65b74-139">有关详细信息，请参阅以下主题。</span><span class="sxs-lookup"><span data-stu-id="65b74-139">For more information, see the following topics.</span></span>  
  
    -   [<span data-ttu-id="65b74-140">还原数据库（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="65b74-140">Restore Database &#40;General Page&#41;</span></span>](general-page-of-integration-services-designers-options.md)  
  
    -   [<span data-ttu-id="65b74-141">还原数据库（“文件”页）</span><span class="sxs-lookup"><span data-stu-id="65b74-141">Restore Database &#40;Files Page&#41;</span></span>](../relational-databases/backup-restore/restore-database-files-page.md)  
  
    -   [<span data-ttu-id="65b74-142">还原数据库（“选项”页）</span><span class="sxs-lookup"><span data-stu-id="65b74-142">Restore Database &#40;Options Page&#41;</span></span>](../relational-databases/backup-restore/restore-database-options-page.md)  
  
4.  <span data-ttu-id="65b74-143">执行你在 [备份 SSIS 数据库](#backup) 中为 ##MS_SSISServerCleanupJobLogin##、sp_ssis_startup 和 SSIS 服务器维护作业创建的脚本。</span><span class="sxs-lookup"><span data-stu-id="65b74-143">Execute the scripts that you created in the [To Back up the SSIS Database](#backup) for ##MS_SSISServerCleanupJobLogin##, sp_ssis_startup, and SSIS Server Maintenance Job.</span></span> <span data-ttu-id="65b74-144">确认 SQL Server 代理已启动。</span><span class="sxs-lookup"><span data-stu-id="65b74-144">Confirm that SQL Server Agent has been started.</span></span>  
  
5.  <span data-ttu-id="65b74-145">运行以下语句以将 sp_ssis_startup 过程设置为自动执行。</span><span class="sxs-lookup"><span data-stu-id="65b74-145">Run the following statement to set the sp_ssis_startup prodecure for autoexecution.</span></span> <span data-ttu-id="65b74-146">有关详细信息，请参阅 [sp_procoption (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="65b74-146">For more information, see [sp_procoption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql).</span></span>  
  
    ```  
    EXEC sp_procoption N'sp_ssis_startup','startup','on'  
    ```  
  
6.  <span data-ttu-id="65b74-147">通过在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中使用“登录属性”对话框，将 SSISDB 用户 ##MS_SSISServerCleanupJobUser##（SSISDB 数据库）映射到 ##MS_SSISServerCleanupJobLogin##。</span><span class="sxs-lookup"><span data-stu-id="65b74-147">Map the SSISDB user ##MS_SSISServerCleanupJobUser## (SSISDB database) to ##MS_SSISServerCleanupJobLogin##, by using the **Login Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
7.  <span data-ttu-id="65b74-148">使用下列方法之一还原主密钥。</span><span class="sxs-lookup"><span data-stu-id="65b74-148">Restore the master key by using one of the following methods.</span></span> <span data-ttu-id="65b74-149">有关加密的详细信息，请参阅 [Encryption Hierarchy](../relational-databases/security/encryption/encryption-hierarchy.md)。</span><span class="sxs-lookup"><span data-stu-id="65b74-149">For more information about encryption, see [Encryption Hierarchy](../relational-databases/security/encryption/encryption-hierarchy.md).</span></span>  
  
    -   <span data-ttu-id="65b74-150">**方法 1**</span><span class="sxs-lookup"><span data-stu-id="65b74-150">**Method 1**</span></span>  
  
         <span data-ttu-id="65b74-151">如果已备份数据库主密钥且具有用于加密主密钥的密码，则使用此方法。</span><span class="sxs-lookup"><span data-stu-id="65b74-151">Use this method if you've already performed a backup of the database master key, and you have the password used to encrypt the master key.</span></span>  
  
        ```  
               Restore master key from file = 'c:\temp\RCTestInstKey'  
               Decryption by password = 'LS2Setup!' -- 'Password used to encrypt the master key during SSISDB backup'  
               Encryption by password = 'LS3Setup!' -- 'New Password'  
               Force  
  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="65b74-152">确认 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服务帐户有权读取备份密钥文件。</span><span class="sxs-lookup"><span data-stu-id="65b74-152">Confirm that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] service account has permissions to read the backup key file.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="65b74-153">如果服务主密钥尚未加密数据库主密钥，将看到 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中显示的以下警告消息。</span><span class="sxs-lookup"><span data-stu-id="65b74-153">You will see the following warning message displayed in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] if the database master key has not yet been encrypted by the service master key.</span></span> <span data-ttu-id="65b74-154">忽略警告消息。</span><span class="sxs-lookup"><span data-stu-id="65b74-154">Ignore the warning message.</span></span>  
        >   
        >  <span data-ttu-id="65b74-155">**无法解密当前主密钥。此错误已被忽略，因为指定了 FORCE 选项。**</span><span class="sxs-lookup"><span data-stu-id="65b74-155">**The current master key cannot be decrypted. The error was ignored because the FORCE option was specified.**</span></span>  
        >   
        >  <span data-ttu-id="65b74-156">FORCE 参数指定即使当前数据库主密钥未打开，也应继续执行还原过程。</span><span class="sxs-lookup"><span data-stu-id="65b74-156">The FORCE argument specifies that the restore process should continue even if the current database master key is not open.</span></span> <span data-ttu-id="65b74-157">对于 SSISDB 目录，由于在您正在其中还原数据库的实例上未打开数据库主密钥，您将看到此消息。</span><span class="sxs-lookup"><span data-stu-id="65b74-157">For the SSISDB catalog, because the database master key has not been opened on the instance where you are restoring the database, you will see this message.</span></span>  
  
    -   <span data-ttu-id="65b74-158">**方法 2**</span><span class="sxs-lookup"><span data-stu-id="65b74-158">**Method 2**</span></span>  
  
         <span data-ttu-id="65b74-159">如果您具有用于创建 SSISDB 的原始密码，则使用此方法。</span><span class="sxs-lookup"><span data-stu-id="65b74-159">Use this method if you have the original password that was used to create SSISDB.</span></span>  
  
        ```  
        open master key decryption by password = 'LS1Setup!' --'Password used when creating SSISDB'  
               Alter Master Key Add encryption by Service Master Key  
        ```  
  
8.  <span data-ttu-id="65b74-160">通过运行 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog.check_schema_version [，确定 SSISDB 目录架构与](/sql/integration-services/system-stored-procedures/catalog-check-schema-version)二进制文件（ISServerExec 和 SQLCLR 程序集）是否兼容。</span><span class="sxs-lookup"><span data-stu-id="65b74-160">Determine whether the SSISDB catalog schema and the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] binaries (ISServerExec and SQLCLR assembly) are compatible, by running [catalog.check_schema_version](/sql/integration-services/system-stored-procedures/catalog-check-schema-version).</span></span>  
  
9. <span data-ttu-id="65b74-161">若要确认 SSISDB 数据库已成功还原，请针对 SSISDB 目录执行操作，如运行部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器的包。</span><span class="sxs-lookup"><span data-stu-id="65b74-161">To confirm that the SSISDB database has been restored successfully, perform operations against the SSISDB catalog such as running packages that have been deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="65b74-162">有关详细信息，请参阅 [使用 SQL Server Management Studio 在 SSIS 服务器上运行包](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="65b74-162">For more information, see [Run a Package on the SSIS Server Using SQL Server Management Studio](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md).</span></span>  
  
### <a name="to-move-the-ssis-database"></a><span data-ttu-id="65b74-163">移动 SSIS 数据库</span><span class="sxs-lookup"><span data-stu-id="65b74-163">To Move the SSIS Database</span></span>  
  
-   <span data-ttu-id="65b74-164">按移动用户数据库的说明操作。</span><span class="sxs-lookup"><span data-stu-id="65b74-164">Follow the instructions for moving user databases.</span></span> <span data-ttu-id="65b74-165">有关详细信息，请参阅 [Move User Databases](../relational-databases/databases/move-user-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="65b74-165">For more information, see [Move User Databases](../relational-databases/databases/move-user-databases.md).</span></span>  
  
     <span data-ttu-id="65b74-166">确保您备份 SSISDB 数据库的主密钥并保护备份文件。</span><span class="sxs-lookup"><span data-stu-id="65b74-166">Ensure that you back up the master key for the SSISDB database and protect the backup file.</span></span> <span data-ttu-id="65b74-167">有关详细信息，请参阅 [备份 SSIS 数据库](#backup)。</span><span class="sxs-lookup"><span data-stu-id="65b74-167">For more information, see [To Back up the SSIS Database](#backup).</span></span>  
  
     <span data-ttu-id="65b74-168">确保在尚未创建 SSISDB 目录的新 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例中创建 Integration Services (SSIS) 相关对象。</span><span class="sxs-lookup"><span data-stu-id="65b74-168">Ensure that the Integration Services (SSIS) relevant objects are created in the new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog has not yet been created.</span></span>  
  
  
