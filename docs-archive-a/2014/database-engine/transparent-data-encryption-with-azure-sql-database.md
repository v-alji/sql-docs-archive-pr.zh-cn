---
title: 借助 Azure SQL 数据库实现透明数据加密 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TDE, SQL Database
- Transparent Data Encryption, SQL Database
- encryption (SQL Database) TDE
ms.assetid: 0bf7e8ff-1416-4923-9c4c-49341e208c62
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6af7c52741b85a2733b93c2b1ed8c03a14dd6343
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586939"
---
# <a name="transparent-data-encryption-with-azure-sql-database"></a><span data-ttu-id="7380b-102">借助 Azure SQL 数据库实现透明数据加密</span><span class="sxs-lookup"><span data-stu-id="7380b-102">Transparent Data Encryption with Azure SQL Database</span></span>
  [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] <span data-ttu-id="7380b-103">透明数据加密（预览）通过执行数据库的实时加密和解密、关联的备份和处于休眠状态的事务日志文件来帮助保护用户免受恶意活动的威胁，而无需更改应用程序。</span><span class="sxs-lookup"><span data-stu-id="7380b-103">transparent data encryption (preview) helps protect against the threat of malicious activity by performing real-time encryption and decryption of the database, associated backups, and transaction log files at rest without requiring changes to the application.</span></span>

 <span data-ttu-id="7380b-104">TDE 使用称为数据库加密密钥的对称密钥来加密整个数据库的存储。</span><span class="sxs-lookup"><span data-stu-id="7380b-104">TDE encrypts the storage of an entire database by using a symmetric key called the database encryption key.</span></span> <span data-ttu-id="7380b-105">在 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 中，数据库加密密钥通过内置的服务器证书进行保护。</span><span class="sxs-lookup"><span data-stu-id="7380b-105">In [!INCLUDE[ssSDS](../includes/sssds-md.md)] the database encryption key is protected by a built-in server certificate.</span></span> <span data-ttu-id="7380b-106">内置服务器证书对每个 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 服务器而言是唯一的。</span><span class="sxs-lookup"><span data-stu-id="7380b-106">The built-in server certificate is unique for each [!INCLUDE[ssSDS](../includes/sssds-md.md)] server.</span></span> <span data-ttu-id="7380b-107">如果数据库是 GeoDR 关系，则将它受每个服务器上不同的密钥保护。</span><span class="sxs-lookup"><span data-stu-id="7380b-107">If a database is in a GeoDR relationship, it is protected by a different key on each server.</span></span> <span data-ttu-id="7380b-108">如果 2 个数据库连接到同一台服务器，则它们共享相同的内置证书。</span><span class="sxs-lookup"><span data-stu-id="7380b-108">If 2 databases are connected to the same server, they share the same built-in certificate.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="7380b-109">至少每隔 90 天自动轮换这些证书。</span><span class="sxs-lookup"><span data-stu-id="7380b-109">automatically rotates these certificates at least every 90 days.</span></span> <span data-ttu-id="7380b-110">有关 TDE 的一般说明，请参阅 [透明数据加密 (TDE)](../relational-databases/security/encryption/transparent-data-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="7380b-110">For a general description of TDE, see [Transparent Data Encryption &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md).</span></span>

 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] <span data-ttu-id="7380b-111">不支持 Azure 密钥保管库与 TDE 的集成。</span><span class="sxs-lookup"><span data-stu-id="7380b-111">does not support Azure Key Vault integration with TDE.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="7380b-112">可以使用密钥保管库的非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="7380b-112">running on an Azure virtual machine can use an asymmetric key from the Key Vault.</span></span> <span data-ttu-id="7380b-113">有关详细信息，请参阅 [Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault](../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md#ExampleA)。</span><span class="sxs-lookup"><span data-stu-id="7380b-113">For more information, see [Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault](../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md#ExampleA).</span></span>

||
|-|
|<span data-ttu-id="7380b-114">**适用**于： [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] [在某些区域](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag))  (预览。</span><span class="sxs-lookup"><span data-stu-id="7380b-114">**Applies to**: [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] ([Preview in some regions](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).</span></span>|

> [!IMPORTANT]
>  <span data-ttu-id="7380b-115">目前这是预览功能。</span><span class="sxs-lookup"><span data-stu-id="7380b-115">This is currently a preview feature.</span></span> <span data-ttu-id="7380b-116">我确认并同意我的数据库中的 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 透明数据加密的实现遵从我的许可证协议（例如企业协议、Microsoft Azure 协议或 Microsoft 在线订阅协议）的预览版条款，以及任何适用的 [Microsoft Azure 预览版的补充使用条款](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)。</span><span class="sxs-lookup"><span data-stu-id="7380b-116">I acknowledge and agree that implementation of [!INCLUDE[ssSDS](../includes/sssds-md.md)] transparent data encryption in my database(s) is subject to the preview terms in my license agreement (e.g. the Enterprise Agreement, Microsoft Azure Agreement, or Microsoft Online Subscription Agreement), as well as any applicable [Supplemental Terms of Use for Microsoft Azure Preview](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).</span></span>

 <span data-ttu-id="7380b-117">即使在 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 的版本系列 V12 现在宣布为处于公开发布状态的部分地理区域中，TDE 的状态预览也适用。</span><span class="sxs-lookup"><span data-stu-id="7380b-117">The preview of status of TDE applies even in the subset of geographic regions where version family V12 of [!INCLUDE[ssSDS](../includes/sssds-md.md)] is announced as now being in general availability status.</span></span> <span data-ttu-id="7380b-118">在 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 宣布将 TDE 从预览提升为 GA 之前， [!INCLUDE[msCoName](../includes/msconame-md.md)] 的 TDE 不适用于生产数据库。</span><span class="sxs-lookup"><span data-stu-id="7380b-118">TDE for [!INCLUDE[ssSDS](../includes/sssds-md.md)] is not intended for use in production databases until [!INCLUDE[msCoName](../includes/msconame-md.md)] announces that TDE is promoted from preview to GA.</span></span> <span data-ttu-id="7380b-119">有关 [!INCLUDE[ssSDS](../includes/sssds-md.md)] V12 的详细信息，请参阅 [Azure SQL Database 中的新增功能](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/)。</span><span class="sxs-lookup"><span data-stu-id="7380b-119">For more information about [!INCLUDE[ssSDS](../includes/sssds-md.md)] V12, see [What's new in Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/).</span></span>

##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7380b-120">权限</span><span class="sxs-lookup"><span data-stu-id="7380b-120">Permissions</span></span>
 <span data-ttu-id="7380b-121">若要通过 Azure 门户利用 REST API 或 PowerShell 注册预览并配置 TDE，则必须作为 Azure 所有者、参与者或 SQL 安全管理员连接。</span><span class="sxs-lookup"><span data-stu-id="7380b-121">To sign up for the preview and to configure TDE through the Azure portal, by using the REST API, or by using PowerShell, you must be connected as the Azure Owner, Contributor, or SQL Security Manager.</span></span>

 <span data-ttu-id="7380b-122">要使用 [!INCLUDE[tsql](../includes/tsql-md.md)] 配置 TDE，则需要具备以下条件：</span><span class="sxs-lookup"><span data-stu-id="7380b-122">To configure TDE by using [!INCLUDE[tsql](../includes/tsql-md.md)] requires the following:</span></span>

-   <span data-ttu-id="7380b-123">必须已经注册 TDE 预览。</span><span class="sxs-lookup"><span data-stu-id="7380b-123">You must be already signed up for the TDE preview.</span></span>

-   <span data-ttu-id="7380b-124">要创建数据库加密密钥，则必须是 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 管理员或主数据库中 **dbmanager** 角色的成员，并且具有数据库的 **CONTROL** 权限。</span><span class="sxs-lookup"><span data-stu-id="7380b-124">To create the database encryption key you must be a [!INCLUDE[ssSDS](../includes/sssds-md.md)] administrator or you must be a member of the **dbmanager** role in the master database and have the **CONTROL** permission on the database.</span></span>

-   <span data-ttu-id="7380b-125">使用 SET 选项执行 ALTER DATABASE 语句仅需要 **dbmanager** 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="7380b-125">To execute the ALTER DATABASE statement with the SET option only requires membership in the **dbmanager** role.</span></span>

##  <a name="sign-up-for-the-preview-of-tde-and-enable-tde-on-a-database"></a><a name="Preview"></a><span data-ttu-id="7380b-126">注册 TDE 预览并在数据库上启用 TDE</span><span class="sxs-lookup"><span data-stu-id="7380b-126">Sign Up for the Preview of TDE and Enable TDE on a Database</span></span>

1.  <span data-ttu-id="7380b-127">访问 Azure 门户 [https://portal.azure.com](https://portal.azure.com) ，并通过 Azure 管理员或参与者帐户登录。</span><span class="sxs-lookup"><span data-stu-id="7380b-127">Visit the Azure Portal at [https://portal.azure.com](https://portal.azure.com) and sign-in with your Azure Administrator or Contributor account.</span></span>

2.  <span data-ttu-id="7380b-128">在左侧标题栏中，单击“浏览”\*\*\*\*，然后单击“SQL 数据库”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7380b-128">On the left banner, click to **BROWSE**, and then click **SQL databases**.</span></span>

3.  <span data-ttu-id="7380b-129">在左窗格中选择“SQL 数据库”后，单击你的用户数据库\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7380b-129">With **SQL databases** selected in the left pane, click your user database.</span></span>

4.  <span data-ttu-id="7380b-130">在数据库边栏选项卡中，单击“所有设置” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7380b-130">In the database blade, click **All settings**.</span></span>

5.  <span data-ttu-id="7380b-131">在“设置” \*\*\*\* 边栏选项卡中，单击“透明数据加密（预览）” \*\*\*\* 部分打开“透明数据加密预览” \*\*\*\* 边栏选项卡。</span><span class="sxs-lookup"><span data-stu-id="7380b-131">In the **Settings** blade, click **Transparent data encryption (preview)** part to open the **Transparent data encryption PREVIEW** blade.</span></span> <span data-ttu-id="7380b-132">如果尚未注册 TDE 预览，则将在完成注册前禁用数据加密设置。</span><span class="sxs-lookup"><span data-stu-id="7380b-132">If you have not already signed up for the TDE preview, the data encryption settings will be disabled until you complete signup.</span></span>

6.  <span data-ttu-id="7380b-133">单击“预览条款” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7380b-133">Click **PREVIEW TERMS**.</span></span>

7.  <span data-ttu-id="7380b-134">阅读预览条款，如果同意条款，请选中 "**透明数据 encryptionPreview 条款**" 复选框，然后单击页面底部附近的 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="7380b-134">Read the terms of the preview, and if you agree to the terms, select the **Transparent Data encryptionPreview terms** check box, and then click **OK** near the bottom of the page.</span></span> <span data-ttu-id="7380b-135">返回 " **Data encryptionPREVIEW** " 边栏选项卡，其中现在应启用 "**数据加密**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="7380b-135">Returning to the **Data encryptionPREVIEW** blade, where the **Data encryption** button should now be enabled.</span></span>

8.  <span data-ttu-id="7380b-136">在“数据加密预览” \*\*\*\* 边栏选项卡中，将“数据加密” \*\*\*\* 按钮移动为“开” \*\*\*\*，然后单击“保存” \*\*\*\* （在页面顶部）以应用设置。</span><span class="sxs-lookup"><span data-stu-id="7380b-136">In the **Data encryption PREVIEW** blade, move the **Data encryption** button to **On**, and then click **Save** (at the top of the page) to apply the setting.</span></span> <span data-ttu-id="7380b-137">“加密状态” \*\*\*\* 将粗略估计透明数据加密的进度。</span><span class="sxs-lookup"><span data-stu-id="7380b-137">The **Encryption status** will approximate the progress of the transparent data encryption.</span></span>

     <span data-ttu-id="7380b-138">![SQLDB_TDE_TermsNewUI](../../2014/database-engine/media/sqldb-tde-termsnewui.png "SQLDB_TDE_TermsNewUI")</span><span class="sxs-lookup"><span data-stu-id="7380b-138">![SQLDB_TDE_TermsNewUI](../../2014/database-engine/media/sqldb-tde-termsnewui.png "SQLDB_TDE_TermsNewUI")</span></span>

     <span data-ttu-id="7380b-139">此外，还可以通过使用查询工具（如 [!INCLUDE[ssSDS](../includes/sssds-md.md)] ）作为具有“查看数据库状态” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]**权限的数据库用户连接到** ，以便监视加密进度。</span><span class="sxs-lookup"><span data-stu-id="7380b-139">You can also monitor the progress of encryption by connecting to [!INCLUDE[ssSDS](../includes/sssds-md.md)] using a query tool such as [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] as a database user with the **VIEW DATABASE STATE** permission.</span></span> <span data-ttu-id="7380b-140">查询 `encryption_state` [sys.databases dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)视图的列。</span><span class="sxs-lookup"><span data-stu-id="7380b-140">Query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) view.</span></span>

##  <a name="enabling-tde-on-sssds-by-using-transact-sql"></a><a name="Encrypt"></a><span data-ttu-id="7380b-141">使用 Transact-sql 在上启用 TDE [!INCLUDE[ssSDS](../includes/sssds-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7380b-141">Enabling TDE on [!INCLUDE[ssSDS](../includes/sssds-md.md)] by Using Transact-SQL</span></span>
 <span data-ttu-id="7380b-142">以下步骤中，假定你已注册预览。</span><span class="sxs-lookup"><span data-stu-id="7380b-142">The following steps, assume you have already signed up for the preview.</span></span>

###  <a name="TsqlProcedure"></a>

1.  <span data-ttu-id="7380b-143">使用管理员或主数据库中 **dbmanager** 角色成员的登录名连接到数据库。</span><span class="sxs-lookup"><span data-stu-id="7380b-143">Connect to the database using a login that is an administrator or a member of the **dbmanager** role in the master database.</span></span>

2.  <span data-ttu-id="7380b-144">执行以下语句以创建数据库加密密钥并对数据库进行加密。</span><span class="sxs-lookup"><span data-stu-id="7380b-144">Execute the following statements to create a database encryption key and encrypt the database.</span></span>

    ```sql
    -- Create the database encryption key that will be used for TDE.
    CREATE DATABASE ENCRYPTION KEY 
    WITH ALGORITHM = AES_256 
    ENCRYPTION BY SERVER CERTIFICATE ##MS_TdeCertificate##;

    -- Enable encryption
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION ON;
    GO
    ```

3.  <span data-ttu-id="7380b-145">若要监视加密的进度 [!INCLUDE[ssSDS](../includes/sssds-md.md)] ，具有**VIEW database STATE**权限的数据库用户可以查询 `encryption_state` [sys.databases dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)视图的列。</span><span class="sxs-lookup"><span data-stu-id="7380b-145">To monitor the progress of encryption on [!INCLUDE[ssSDS](../includes/sssds-md.md)], database users with the **VIEW DATABASE STATE** permission can query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) view.</span></span>

## <a name="enabling-tde-on-sql-database-by-using-powershell"></a><span data-ttu-id="7380b-146">通过使用 PowerShell 在 SQL 数据库上启用 TDE</span><span class="sxs-lookup"><span data-stu-id="7380b-146">Enabling TDE on SQL Database by Using PowerShell</span></span>
 <span data-ttu-id="7380b-147">使用 Azure PowerShell 则可运行以下命令来打开/关闭 TDE。</span><span class="sxs-lookup"><span data-stu-id="7380b-147">Using the Azure PowerShell you can run the following command to turn TDE on/off.</span></span> <span data-ttu-id="7380b-148">运行该命令之前，需要将帐户连接到 PS 窗口中。</span><span class="sxs-lookup"><span data-stu-id="7380b-148">You do have to connect your account to the PS window before running the command.</span></span> <span data-ttu-id="7380b-149">以下步骤中，假定你已注册预览。</span><span class="sxs-lookup"><span data-stu-id="7380b-149">The following steps, assume you have already signed up for the preview.</span></span> <span data-ttu-id="7380b-150">有关 PowerShell 的其他信息，请参阅 [如何安装和配置 Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/)。</span><span class="sxs-lookup"><span data-stu-id="7380b-150">For additional information about PowerShell, see [How to install and configure Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).</span></span>

1.  <span data-ttu-id="7380b-151">要启用 TDE，则返回 TDE 状态并查看加密活动。</span><span class="sxs-lookup"><span data-stu-id="7380b-151">To enable TDE, return the TDE status, and view the encryption activity.</span></span>

    ```powershell
    Switch-AzureMode -Name AzureResourceManager
    Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Enabled"

    Get-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"
    Get-AzureSqlDatabaseTransparentDataEncryptionActivity -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"
    ```

2.  <span data-ttu-id="7380b-152">要禁用 TDE：</span><span class="sxs-lookup"><span data-stu-id="7380b-152">To disable TDE:</span></span>

    ```powershell
    Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Disabled"
    Switch-AzureMode -Name AzureServiceManagement
    ```

##  <a name="decrypting-a-tde-protected-database-on-sssds"></a><a name="Decrypt"></a><span data-ttu-id="7380b-153">解密受 TDE 保护的数据库[!INCLUDE[ssSDS](../includes/sssds-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7380b-153">Decrypting a TDE Protected Database on [!INCLUDE[ssSDS](../includes/sssds-md.md)]</span></span>

#### <a name="to-disable-tde-by-using-the-azure-portal"></a><span data-ttu-id="7380b-154">要通过使用 Azure 门户中禁用 TDE</span><span class="sxs-lookup"><span data-stu-id="7380b-154">To Disable TDE by Using the Azure Portal</span></span>

1.  <span data-ttu-id="7380b-155">访问 Azure 门户 [https://portal.azure.com](https://portal.azure.com) ，并通过 Azure 管理员或参与者帐户登录。</span><span class="sxs-lookup"><span data-stu-id="7380b-155">Visit the Azure Portal at [https://portal.azure.com](https://portal.azure.com) and sign-in with your Azure Administrator or Contributor account.</span></span>

2.  <span data-ttu-id="7380b-156">在左侧标题栏中，单击“浏览”\*\*\*\*，然后单击“SQL 数据库”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7380b-156">On the left banner, click to **BROWSE**, and then click **SQL databases**.</span></span>

3.  <span data-ttu-id="7380b-157">在左窗格中选择“SQL 数据库”后，单击你的用户数据库\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7380b-157">With **SQL databases** selected in the left pane, click your user database.</span></span>

4.  <span data-ttu-id="7380b-158">在数据库边栏选项卡中，单击“所有设置” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7380b-158">In the database blade, click **All settings**.</span></span>

5.  <span data-ttu-id="7380b-159">在“设置” \*\*\*\* 边栏选项卡中，单击“透明数据加密（预览）” \*\*\*\* 部分打开“透明数据加密预览” \*\*\*\* 边栏选项卡。</span><span class="sxs-lookup"><span data-stu-id="7380b-159">In the **Settings** blade, click **Transparent data encryption (preview)** part to open the **Transparent data encryption PREVIEW** blade.</span></span>

6.  <span data-ttu-id="7380b-160">在“透明数据加密预览” \*\*\*\* 边栏选项卡中，将“数据加密” \*\*\*\* 按钮移动为“关” \*\*\*\*，然后单击“保存” \*\*\*\* （在页面顶部）以应用设置。</span><span class="sxs-lookup"><span data-stu-id="7380b-160">In the **Transparent data encryption PREVIEW** blade, move the **Data encryption** button to **Off**, and then click **Save** (at the top of the page) to apply the setting.</span></span> <span data-ttu-id="7380b-161">“加密状态” \*\*\*\* 将粗略估计透明数据解密的进度。</span><span class="sxs-lookup"><span data-stu-id="7380b-161">The **Encryption status** will approximate the progress of the transparent data decryption.</span></span>

     <span data-ttu-id="7380b-162">此外，还可以通过使用查询工具（如 [!INCLUDE[ssSDS](../includes/sssds-md.md)] ）作为具有“查看数据库状态” [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]**权限的数据库用户连接到** ，以便监视解密进度。</span><span class="sxs-lookup"><span data-stu-id="7380b-162">You can also monitor the progress of decryption by connecting to [!INCLUDE[ssSDS](../includes/sssds-md.md)] using a query tool such as [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] as a database user with the **VIEW DATABASE STATE** permission.</span></span> <span data-ttu-id="7380b-163">查询 `encryption_state` [sys.databases dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)视图的列。</span><span class="sxs-lookup"><span data-stu-id="7380b-163">Query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)view.</span></span>

#### <a name="to-disable-tde-by-using-transact-sql"></a><span data-ttu-id="7380b-164">通过使用 Transact-SQL 禁用 TDE</span><span class="sxs-lookup"><span data-stu-id="7380b-164">To Disable TDE by Using Transact-SQL</span></span>

1.  <span data-ttu-id="7380b-165">使用管理员或主数据库中 **dbmanager** 角色成员的登录名连接到数据库。</span><span class="sxs-lookup"><span data-stu-id="7380b-165">Connect to the database using a login that is an administrator or a member of the **dbmanager** role in the master database.</span></span>

2.  <span data-ttu-id="7380b-166">执行以下语句以解密该数据库。</span><span class="sxs-lookup"><span data-stu-id="7380b-166">Execute the following statements to decrypt the database.</span></span>

    ```sql
    -- Enable encryption
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION OFF;
    GO
    ```

3.  <span data-ttu-id="7380b-167">若要监视加密的进度 [!INCLUDE[ssSDS](../includes/sssds-md.md)] ，具有**VIEW database STATE**权限的数据库用户可以查询 `encryption_state` [sys.databases dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)视图的列。</span><span class="sxs-lookup"><span data-stu-id="7380b-167">To monitor the progress of encryption on [!INCLUDE[ssSDS](../includes/sssds-md.md)], database users with the **VIEW DATABASE STATE** permission can query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) view.</span></span>

##  <a name="working-with-tde-protected-databases-on-sssds"></a><a name="Working"></a><span data-ttu-id="7380b-168">使用 TDE 受保护的数据库[!INCLUDE[ssSDS](../includes/sssds-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7380b-168">Working with TDE Protected Databases on [!INCLUDE[ssSDS](../includes/sssds-md.md)]</span></span>
 <span data-ttu-id="7380b-169">不需要为 Azure 中的操作解密数据库。</span><span class="sxs-lookup"><span data-stu-id="7380b-169">You do not need to decrypt databases for operations within Azure.</span></span> <span data-ttu-id="7380b-170">源数据库或主数据库上 TDE 的设置均以透明方式继承在目标系统上。</span><span class="sxs-lookup"><span data-stu-id="7380b-170">The TDE settings on the source database or primary database are transparently inherited on the target.</span></span> <span data-ttu-id="7380b-171">这包括涉及以下内容的操作：</span><span class="sxs-lookup"><span data-stu-id="7380b-171">This includes operations involving:</span></span>

-   <span data-ttu-id="7380b-172">地域恢复</span><span class="sxs-lookup"><span data-stu-id="7380b-172">Geo-Restore</span></span>

-   <span data-ttu-id="7380b-173">自服务时点还原</span><span class="sxs-lookup"><span data-stu-id="7380b-173">Self-Service Point in Time Restore</span></span>

-   <span data-ttu-id="7380b-174">还原已删除数据库</span><span class="sxs-lookup"><span data-stu-id="7380b-174">Restore a Deleted Database</span></span>

-   <span data-ttu-id="7380b-175">活动地域复制</span><span class="sxs-lookup"><span data-stu-id="7380b-175">Active Geo_Replication</span></span>

-   <span data-ttu-id="7380b-176">创建数据库副本</span><span class="sxs-lookup"><span data-stu-id="7380b-176">Creating a Database Copy</span></span>

##  <a name="moving-a-tde-protected-database-on-using-bacpac-files"></a><a name="Moving"></a><span data-ttu-id="7380b-177">使用在上移动 TDE 保护的数据库。Bacpac 文件</span><span class="sxs-lookup"><span data-stu-id="7380b-177">Moving a TDE Protected Database on using .Bacpac Files</span></span>
 <span data-ttu-id="7380b-178">使用 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] 门户或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 导入和导出向导中的导出数据库功能导出 TDE 保护的数据库时，数据库的内容不加密。</span><span class="sxs-lookup"><span data-stu-id="7380b-178">When exporting a TDE protected database using the Export Database function in the [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] Portal or the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard, the content of the database is not encrypted.</span></span> <span data-ttu-id="7380b-179">内容存储在未加密的 .Bacpac 文件中。</span><span class="sxs-lookup"><span data-stu-id="7380b-179">The content is stored in .bacpac files which are not encrypted.</span></span>  <span data-ttu-id="7380b-180">完成新数据库的导入后，请务必适当保护 .Bacpac 文件并启用 TDE。</span><span class="sxs-lookup"><span data-stu-id="7380b-180">Be sure to protect the .bacpac files appropriately and enable TDE once import of the new database is completed.</span></span>

## <a name="related-sql-server-topic"></a><span data-ttu-id="7380b-181">相关的 SQL Server 主题</span><span class="sxs-lookup"><span data-stu-id="7380b-181">Related SQL Server Topic</span></span>
 [<span data-ttu-id="7380b-182">使用 EKM 启用 TDE</span><span class="sxs-lookup"><span data-stu-id="7380b-182">Enable TDE Using EKM</span></span>](../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)

## <a name="see-also"></a><span data-ttu-id="7380b-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7380b-183">See Also</span></span>
 <span data-ttu-id="7380b-184">[透明数据加密 &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md) [Create CREDENTIAL &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [Create 非对称密钥 &#40;TRANSACT-SQL](/sql/t-sql/statements/create-asymmetric-key-transact-sql)&#41;[create DATABASE Encryption Key](/sql/t-sql/statements/create-database-encryption-key-transact-sql) &#40;TRANSACT-SQL&#41;Alter [Database &#40;transact-sql](/sql/t-sql/statements/alter-database-transact-sql)&#41;[alter database SET Options &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)</span><span class="sxs-lookup"><span data-stu-id="7380b-184">[Transparent Data Encryption &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql) [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)</span></span>
