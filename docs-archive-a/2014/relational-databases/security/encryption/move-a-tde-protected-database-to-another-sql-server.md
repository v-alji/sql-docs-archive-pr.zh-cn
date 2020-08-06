---
title: 将受 TDE 保护的数据库移到其他 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption, moving
- TDE, moving a database
ms.assetid: fb420903-df54-4016-bab6-49e6dfbdedc7
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 3b03b4d9ecf31e9953fd3e22cec5c51bbacc0c25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694422"
---
# <a name="move-a-tde-protected-database-to-another-sql-server"></a><span data-ttu-id="5d036-102">将受 TDE 保护的数据库移到其他 SQL Server</span><span class="sxs-lookup"><span data-stu-id="5d036-102">Move a TDE Protected Database to Another SQL Server</span></span>
  <span data-ttu-id="5d036-103">本主题介绍如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 通过透明数据加密 (TDE) 来保护数据库，然后再将数据库移动到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的其他实例。</span><span class="sxs-lookup"><span data-stu-id="5d036-103">This topic describes how to protect a database by using transparent data encryption (TDE), and then move the database to another instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5d036-104">TDE 针对数据和日志文件执行实时 I/O 加密和解密。</span><span class="sxs-lookup"><span data-stu-id="5d036-104">TDE performs real-time I/O encryption and decryption of the data and log files.</span></span> <span data-ttu-id="5d036-105">加密使用数据库加密密钥 (DEK)，它存储在数据库引导记录中，可在恢复时使用。</span><span class="sxs-lookup"><span data-stu-id="5d036-105">The encryption uses a database encryption key (DEK), which is stored in the database boot record for availability during recovery.</span></span> <span data-ttu-id="5d036-106">DEK 是使用存储在服务器的 `master` 数据库中的证书保护的对称密钥，或者是由 EKM 模块保护的非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="5d036-106">The DEK is a symmetric key secured by using a certificate stored in the `master` database of the server or an asymmetric key protected by an EKM module.</span></span>  
  
 <span data-ttu-id="5d036-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="5d036-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5d036-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="5d036-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5d036-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="5d036-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="5d036-110">安全性</span><span class="sxs-lookup"><span data-stu-id="5d036-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5d036-111">**若要创建由透明数据加密保护的数据库，可使用：**</span><span class="sxs-lookup"><span data-stu-id="5d036-111">**To create a database protected by transparent data encryption, using:**</span></span>  
  
     [<span data-ttu-id="5d036-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5d036-112">SQL Server Management Studio</span></span>](#SSMSCreate)  
  
     [<span data-ttu-id="5d036-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5d036-113">Transact-SQL</span></span>](#TsqlCreate)  
  
-   <span data-ttu-id="5d036-114">**若要移动数据库，可使用：**</span><span class="sxs-lookup"><span data-stu-id="5d036-114">**To move a database, using:**</span></span>  
  
     [<span data-ttu-id="5d036-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5d036-115">SQL Server Management Studio</span></span>](#SSMSMove)  
  
     [<span data-ttu-id="5d036-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5d036-116">Transact-SQL</span></span>](#TsqlMove)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5d036-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="5d036-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5d036-118">限制和局限</span><span class="sxs-lookup"><span data-stu-id="5d036-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="5d036-119">在移动 TDE 保护的数据库时，您还必须移动用于打开 DEK 的证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="5d036-119">When moving a TDE protected database, you must also move the certificate or asymmetric key that is used to open the DEK.</span></span> <span data-ttu-id="5d036-120">证书或非对称密钥必须安装在 `master` 目标服务器的数据库中，以便 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可以访问数据库文件。</span><span class="sxs-lookup"><span data-stu-id="5d036-120">The certificate or asymmetric key must be installed in the `master` database of the destination server, so that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can access the database files.</span></span> <span data-ttu-id="5d036-121">有关详细信息，请参阅[透明数据加密 (TDE)](transparent-data-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="5d036-121">For more information, see [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md).</span></span>  
  
-   <span data-ttu-id="5d036-122">您必须保留证书文件和私钥文件的备份，以便还原证书。</span><span class="sxs-lookup"><span data-stu-id="5d036-122">You must retain copies of both the certificate file and the private key file in order to recover the certificate.</span></span> <span data-ttu-id="5d036-123">用于私钥的密码不必与数据库主密钥密码相同。</span><span class="sxs-lookup"><span data-stu-id="5d036-123">The password for the private key does not have to be the same as the database master key password.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="5d036-124">将此处创建的文件存储在**C:\Program FILES\MICROSOFT SQL Server\MSSQL12. 中。** 默认情况下，MSSQLSERVER\MSSQL\DATA。</span><span class="sxs-lookup"><span data-stu-id="5d036-124">stores the files created here in **C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA** by default.</span></span> <span data-ttu-id="5d036-125">您的文件名和位置可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="5d036-125">Your file names and locations might be different.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5d036-126">Security</span><span class="sxs-lookup"><span data-stu-id="5d036-126">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5d036-127">权限</span><span class="sxs-lookup"><span data-stu-id="5d036-127">Permissions</span></span>  
  
-   <span data-ttu-id="5d036-128">需要对 `CONTROL DATABASE` 数据库拥有权限 `master` 才能创建数据库主密钥。</span><span class="sxs-lookup"><span data-stu-id="5d036-128">Requires `CONTROL DATABASE` permission on the `master` database to create the database master key.</span></span>  
  
-   <span data-ttu-id="5d036-129">要求对 `CREATE CERTIFICATE` 数据库具有权限， `master` 以创建保护 DEK 的证书。</span><span class="sxs-lookup"><span data-stu-id="5d036-129">Requires `CREATE CERTIFICATE` permission on the `master` database to create the certificate that protects the DEK.</span></span>  
  
-   <span data-ttu-id="5d036-130">需要拥有已加密数据库的 `CONTROL DATABASE` 权限和用于加密数据库加密密钥的证书或非对称密钥的 `VIEW DEFINITION` 权限。</span><span class="sxs-lookup"><span data-stu-id="5d036-130">Requires `CONTROL DATABASE` permission on the encrypted database and `VIEW DEFINITION` permission on the certificate or asymmetric key that is used to encrypt the database encryption key.</span></span>  
  
##  <a name="to-create-a-database-protected-by-transparent-data-encryption"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5d036-131">创建由透明数据加密保护的数据库</span><span class="sxs-lookup"><span data-stu-id="5d036-131">To create a database protected by transparent data encryption</span></span>  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSCreate"></a> <span data-ttu-id="5d036-132">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5d036-132">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="5d036-133">在数据库中创建数据库主密钥和证书 `master` 。</span><span class="sxs-lookup"><span data-stu-id="5d036-133">Create a database master key and certificate in the `master` database.</span></span> <span data-ttu-id="5d036-134">有关详细信息，请参阅下面的 **使用 Transact-SQL** 。</span><span class="sxs-lookup"><span data-stu-id="5d036-134">For more information, see **Using Transact-SQL** below.</span></span>  
  
2.  <span data-ttu-id="5d036-135">在数据库中创建服务器证书的备份 `master` 。</span><span class="sxs-lookup"><span data-stu-id="5d036-135">Create a backup of the server certificate in the `master` database.</span></span> <span data-ttu-id="5d036-136">有关详细信息，请参阅下面的 **使用 Transact-SQL** 。</span><span class="sxs-lookup"><span data-stu-id="5d036-136">For more information, see **Using Transact-SQL** below.</span></span>  
  
3.  <span data-ttu-id="5d036-137">在对象资源管理器中，右键单击 **“数据库”** 文件夹，并选择 **“新建数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="5d036-137">In Object Explorer, right-click the **Databases** folder and select **New Database**.</span></span>  
  
4.  <span data-ttu-id="5d036-138">在 **“新建数据库”** 对话框的 **“数据库名称”** 框中，输入新数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="5d036-138">In the **New Database** dialog box, in the **Database name** box, enter the name of the new database.</span></span>  
  
5.  <span data-ttu-id="5d036-139">在 **“所有者”** 框中，输入新数据库的所有者的名称。</span><span class="sxs-lookup"><span data-stu-id="5d036-139">In the **Owner** box, enter the name of the new database's owner.</span></span> <span data-ttu-id="5d036-140">或者，单击省略号 (…) 以打开“选择数据库所有者”对话框 。</span><span class="sxs-lookup"><span data-stu-id="5d036-140">Alternately, click the ellipsis **(...)** to open the **Select Database Owner** dialog box.</span></span> <span data-ttu-id="5d036-141">有关创建新的数据库的详细信息，请参阅 [Create a Database](../../databases/create-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="5d036-141">For more information on creating a new database, see [Create a Database](../../databases/create-a-database.md).</span></span>  
  
6.  <span data-ttu-id="5d036-142">在对象资源管理器中，右键单击加号以展开 **“数据库”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="5d036-142">In Object Explorer, click the plus sign to expand the **Databases** folder.</span></span>  
  
7.  <span data-ttu-id="5d036-143">右键单击您所创建的数据库，指向 **“任务”** ，然后选择 **“管理数据库加密”** 。</span><span class="sxs-lookup"><span data-stu-id="5d036-143">Right-click the database you created, point to **Tasks**, and select **Manage Database Encryption**.</span></span>  
  
     <span data-ttu-id="5d036-144">**“管理数据库加密”** 对话框中提供了以下选项。</span><span class="sxs-lookup"><span data-stu-id="5d036-144">The following options are available on the **Manage Database Encryption** dialog box.</span></span>  
  
     <span data-ttu-id="5d036-145">**加密算法**</span><span class="sxs-lookup"><span data-stu-id="5d036-145">**Encryption Algorithm**</span></span>  
     <span data-ttu-id="5d036-146">显示或设置要用于数据库加密的算法。</span><span class="sxs-lookup"><span data-stu-id="5d036-146">Displays or sets the algorithm to use for database encryption.</span></span> <span data-ttu-id="5d036-147">`AES128` 为默认算法。</span><span class="sxs-lookup"><span data-stu-id="5d036-147">`AES128` is the default algorithm.</span></span> <span data-ttu-id="5d036-148">此字段不能为空。</span><span class="sxs-lookup"><span data-stu-id="5d036-148">This field cannot be blank.</span></span> <span data-ttu-id="5d036-149">有关加密算法的详细信息，请参阅 [Choose an Encryption Algorithm](choose-an-encryption-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="5d036-149">For more information on encryption algorithms, see [Choose an Encryption Algorithm](choose-an-encryption-algorithm.md).</span></span>  
  
     <span data-ttu-id="5d036-150">**使用服务器证书**</span><span class="sxs-lookup"><span data-stu-id="5d036-150">**Use server certificate**</span></span>  
     <span data-ttu-id="5d036-151">将加密设置为由证书提供保护。</span><span class="sxs-lookup"><span data-stu-id="5d036-151">Sets the encryption to be secured by a certificate.</span></span> <span data-ttu-id="5d036-152">从列表中选择一个。</span><span class="sxs-lookup"><span data-stu-id="5d036-152">Select one from the list.</span></span> <span data-ttu-id="5d036-153">如果没有服务器证书的 `VIEW DEFINITION` 权限，此列表将为空。</span><span class="sxs-lookup"><span data-stu-id="5d036-153">If you do not have the `VIEW DEFINITION` permission on server certificates, this list will be empty.</span></span> <span data-ttu-id="5d036-154">如果选择使用证书进行加密，则此值不能为空。</span><span class="sxs-lookup"><span data-stu-id="5d036-154">If a certificate method of encryption is selected, this value cannot be empty.</span></span> <span data-ttu-id="5d036-155">有关证书的详细信息，请参阅 [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="5d036-155">For more information about certificates, see [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
     <span data-ttu-id="5d036-156">**使用服务器非对称密钥**</span><span class="sxs-lookup"><span data-stu-id="5d036-156">**Use server asymmetric key**</span></span>  
     <span data-ttu-id="5d036-157">将加密设置为由非对称密钥提供保护。</span><span class="sxs-lookup"><span data-stu-id="5d036-157">Sets the encryption to be secured by an asymmetric key.</span></span> <span data-ttu-id="5d036-158">仅显示可用的非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="5d036-158">Only available asymmetric keys are displayed.</span></span> <span data-ttu-id="5d036-159">只有受 EKM 模块保护的非对称密钥才可以使用 TDE 对数据库进行加密。</span><span class="sxs-lookup"><span data-stu-id="5d036-159">Only an asymmetric key protected by an EKM module can encrypt a database using TDE.</span></span>  
  
     <span data-ttu-id="5d036-160">**将数据库加密设置为 ON**</span><span class="sxs-lookup"><span data-stu-id="5d036-160">**Set Database Encryption On**</span></span>  
     <span data-ttu-id="5d036-161">将数据库更改为打开（选中）或关闭（取消选中）TDE。</span><span class="sxs-lookup"><span data-stu-id="5d036-161">Alters the database to turn on (checked) or turn off (unchecked) TDE.</span></span>  
  
8.  <span data-ttu-id="5d036-162">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="5d036-162">When finished, click **OK**.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlCreate"></a> <span data-ttu-id="5d036-163">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5d036-163">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="5d036-164">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="5d036-164">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5d036-165">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="5d036-165">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5d036-166">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="5d036-166">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Create a database master key and a certificate in the master database.  
    USE master ;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1';  
    GO  
    CREATE CERTIFICATE TestSQLServerCert   
    WITH SUBJECT = 'Certificate to protect TDE key'  
    GO  
    -- Create a backup of the server certificate in the master database.  
    -- The following code stores the backup of the certificate and the private key file in the default data location for this instance of SQL Server   
    -- (C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA).  
  
    BACKUP CERTIFICATE TestSQLServerCert   
    TO FILE = 'TestSQLServerCert'  
    WITH PRIVATE KEY   
    (  
        FILE = 'SQLPrivateKeyFile',  
        ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1'  
    );  
    GO  
    -- Create a database to be protected by TDE.  
    CREATE DATABASE CustRecords ;  
    GO  
    -- Switch to the new database.  
    -- Create a database encryption key, that is protected by the server certificate in the master database.   
    -- Alter the new database to encrypt the database using TDE.  
    USE CustRecords;  
    GO  
    CREATE DATABASE ENCRYPTION KEY  
    WITH ALGORITHM = AES_128  
    ENCRYPTION BY SERVER CERTIFICATE TestSQLServerCert;  
    GO  
    ALTER DATABASE CustRecords  
    SET ENCRYPTION ON;  
    GO  
    ```  
  
 <span data-ttu-id="5d036-167">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="5d036-167">For more information, see:</span></span>  
  
-   [<span data-ttu-id="5d036-168">CREATE MASTER KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5d036-168">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [<span data-ttu-id="5d036-169">CREATE CERTIFICATE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5d036-169">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [<span data-ttu-id="5d036-170">BACKUP CERTIFICATE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5d036-170">BACKUP CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-certificate-transact-sql)  
  
-   [<span data-ttu-id="5d036-171">CREATE DATABASE (SQL Server Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5d036-171">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [<span data-ttu-id="5d036-172">CREATE DATABASE ENCRYPTION KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5d036-172">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)  
  
-   [<span data-ttu-id="5d036-173">ALTER DATABASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5d036-173">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
##  <a name="to-move-a-database"></a><a name="TsqlProcedure"></a><span data-ttu-id="5d036-174">移动数据库</span><span class="sxs-lookup"><span data-stu-id="5d036-174">To move a database</span></span>  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSMove"></a> <span data-ttu-id="5d036-175">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5d036-175">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="5d036-176">在对象资源管理器中，右键单击在前面已进行加密的数据库，指向“任务”，然后选择“分离…” 。</span><span class="sxs-lookup"><span data-stu-id="5d036-176">In Object Explorer, right-click the database you encrypted above, point to **Tasks** and select **Detach...**.</span></span>  
  
     <span data-ttu-id="5d036-177">在 **“分离数据库”** 对话框中提供了以下选项。</span><span class="sxs-lookup"><span data-stu-id="5d036-177">The following options are available in the **Detach Database** dialog box.</span></span>  
  
     <span data-ttu-id="5d036-178">**要分离的数据库**</span><span class="sxs-lookup"><span data-stu-id="5d036-178">**Databases to detach**</span></span>  
     <span data-ttu-id="5d036-179">列出要分离的数据库。</span><span class="sxs-lookup"><span data-stu-id="5d036-179">Lists the databases to detach.</span></span>  
  
     <span data-ttu-id="5d036-180">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="5d036-180">**Database Name**</span></span>  
     <span data-ttu-id="5d036-181">显示要分离的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="5d036-181">Displays the name of the database to be detached.</span></span>  
  
     <span data-ttu-id="5d036-182">**删除连接**</span><span class="sxs-lookup"><span data-stu-id="5d036-182">**Drop Connections**</span></span>  
     <span data-ttu-id="5d036-183">断开与指定数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="5d036-183">Disconnect connections to the specified database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5d036-184">不能分离连接为活动状态的数据库。</span><span class="sxs-lookup"><span data-stu-id="5d036-184">You cannot detach a database with active connections.</span></span>  
  
     <span data-ttu-id="5d036-185">**更新统计信息**</span><span class="sxs-lookup"><span data-stu-id="5d036-185">**Update Statistics**</span></span>  
     <span data-ttu-id="5d036-186">默认情况下，分离操作将在分离数据库时保留过期的优化统计信息；若要更新现有的优化统计信息，请单击此复选框。</span><span class="sxs-lookup"><span data-stu-id="5d036-186">By default, the detach operation retains any out-of-date optimization statistics when detaching the database; to update the existing optimization statistics, click this check box.</span></span>  
  
     <span data-ttu-id="5d036-187">**保留全文目录**</span><span class="sxs-lookup"><span data-stu-id="5d036-187">**Keep Full-Text Catalogs**</span></span>  
     <span data-ttu-id="5d036-188">默认情况下，分离操作保留所有与数据库关联的全文目录。</span><span class="sxs-lookup"><span data-stu-id="5d036-188">By default, the detach operation keeps any full-text catalogs that are associated with the database.</span></span> <span data-ttu-id="5d036-189">若要删除全文目录，请清除 **“保留全文目录”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="5d036-189">To remove them, clear the **Keep Full-Text Catalogs** check box.</span></span> <span data-ttu-id="5d036-190">只有从 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]升级数据库时，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="5d036-190">This option appears only when you are upgrading a database from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span>  
  
     <span data-ttu-id="5d036-191">**Status**</span><span class="sxs-lookup"><span data-stu-id="5d036-191">**Status**</span></span>  
     <span data-ttu-id="5d036-192">显示以下状态之一：“就绪”或“未就绪” 。</span><span class="sxs-lookup"><span data-stu-id="5d036-192">Displays one of the following states: **Ready** or **Not ready**.</span></span>  
  
     <span data-ttu-id="5d036-193">**消息**</span><span class="sxs-lookup"><span data-stu-id="5d036-193">**Message**</span></span>  
     <span data-ttu-id="5d036-194">**“消息”** 列可显示关于数据库的如下信息：</span><span class="sxs-lookup"><span data-stu-id="5d036-194">The **Message** column may display information about the database, as follows:</span></span>  
  
    -   <span data-ttu-id="5d036-195">当数据库进行了复制操作，则 **“状态”** 为 **“未就绪”** ， **“消息”** 列将显示 **“已复制数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="5d036-195">When a database is involved with replication, the **Status** is **Not ready** and the **Message** column displays **Database replicated**.</span></span>  
  
    -   <span data-ttu-id="5d036-196">如果数据库有一个或多个活动连接，则“状态”为“未就绪”，“消息”列显示“<number_of_active_connections> 个活动连接”，例如  ：“1 个活动连接”。</span><span class="sxs-lookup"><span data-stu-id="5d036-196">When a database has one or more active connections, the **Status** is **Not ready** and the **Message** column displays _<number_of_active_connections>_**Active connection(s)** - for example: **1 Active connection(s)**.</span></span> <span data-ttu-id="5d036-197">在分离数据库之前，需要通过选择 **“删除连接”** 断开所有活动连接。</span><span class="sxs-lookup"><span data-stu-id="5d036-197">Before you can detach the database, you need to disconnect any active connections by selecting **Drop Connections**.</span></span>  
  
     <span data-ttu-id="5d036-198">若要获取有关消息的详细信息，请单击相应的超链接文本打开活动监视器。</span><span class="sxs-lookup"><span data-stu-id="5d036-198">To obtain more information about a message, click the hyperlinked text to open Activity Monitor.</span></span>  
  
2.  <span data-ttu-id="5d036-199">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="5d036-199">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="5d036-200">使用 Window 资源管理器，将数据库文件从源服务器移动到或复制到目标服务器上的相同位置。</span><span class="sxs-lookup"><span data-stu-id="5d036-200">Using Windows Explorer, move or copy the database files from the source server to the same location on the destination server.</span></span>  
  
4.  <span data-ttu-id="5d036-201">使用 Window 资源管理器，将服务器证书和私钥文件的备份从源服务器移动到或复制到目标服务器上的相同位置。</span><span class="sxs-lookup"><span data-stu-id="5d036-201">Using Windows Explorer, move or copy the backup of the server certificate and the private key file from the source server to the same location on the destination server.</span></span>  
  
5.  <span data-ttu-id="5d036-202">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的目标实例上创建数据库主密钥。</span><span class="sxs-lookup"><span data-stu-id="5d036-202">Create a database master key on the destination instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5d036-203">有关详细信息，请参阅下面的 **使用 Transact-SQL** 。</span><span class="sxs-lookup"><span data-stu-id="5d036-203">For more information, see **Using Transact-SQL** below.</span></span>  
  
6.  <span data-ttu-id="5d036-204">通过使用原始服务器证书备份文件重新创建服务器证书。</span><span class="sxs-lookup"><span data-stu-id="5d036-204">Recreate the server certificate by using the original server certificate backup file.</span></span> <span data-ttu-id="5d036-205">有关详细信息，请参阅下面的 **使用 Transact-SQL** 。</span><span class="sxs-lookup"><span data-stu-id="5d036-205">For more information, see **Using Transact-SQL** below.</span></span>  
  
7.  <span data-ttu-id="5d036-206">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 的对象资源管理器中，右键单击“数据库”文件夹，然后选择“分离…” 。</span><span class="sxs-lookup"><span data-stu-id="5d036-206">In Object Explorer in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], right-click the **Databases** folder and select **Attach...**.</span></span>  
  
8.  <span data-ttu-id="5d036-207">在 **“附加数据库”** 对话框中的 **“要附加的数据库”** 下，单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="5d036-207">In the **Attach Databases** dialog box, under **Databases to attach**, click **Add**.</span></span>  
  
9. <span data-ttu-id="5d036-208">在 "**定位数据库文件-**_server_name_ " 对话框中，选择要附加到新服务器的数据库文件，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="5d036-208">In the **Locate Database Files -**_server_name_ dialog box, select the database file to attach to the new server and click **OK**.</span></span>  
  
     <span data-ttu-id="5d036-209">在 **“附加数据库”** 对话框中提供了以下选项。</span><span class="sxs-lookup"><span data-stu-id="5d036-209">The following options are available in the **Attach Databases** dialog box.</span></span>  
  
     <span data-ttu-id="5d036-210">**“要附加的数据库”**</span><span class="sxs-lookup"><span data-stu-id="5d036-210">**Databases to attach**</span></span>  
     <span data-ttu-id="5d036-211">显示所选数据库的有关信息。</span><span class="sxs-lookup"><span data-stu-id="5d036-211">Displays information about the selected databases.</span></span>  
  
     \<no column header>  
     <span data-ttu-id="5d036-212">显示一个图标，用以指示附加操作的状态。</span><span class="sxs-lookup"><span data-stu-id="5d036-212">Displays an icon indicating the status of the attach operation.</span></span> <span data-ttu-id="5d036-213">下面的 **“状态”** 说明中介绍可能的图标。</span><span class="sxs-lookup"><span data-stu-id="5d036-213">The possible icons are described in the **Status** description, below).</span></span>  
  
     <span data-ttu-id="5d036-214">**MDF 文件位置**</span><span class="sxs-lookup"><span data-stu-id="5d036-214">**MDF File Location**</span></span>  
     <span data-ttu-id="5d036-215">显示选定 MDF 文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="5d036-215">Displays the path and file name of the selected MDF file.</span></span>  
  
     <span data-ttu-id="5d036-216">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="5d036-216">**Database Name**</span></span>  
     <span data-ttu-id="5d036-217">显示数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="5d036-217">Displays the name of the database.</span></span>  
  
     <span data-ttu-id="5d036-218">**附加为**</span><span class="sxs-lookup"><span data-stu-id="5d036-218">**Attach As**</span></span>  
     <span data-ttu-id="5d036-219">根据需要，可以指定要附加数据库的其他名称。</span><span class="sxs-lookup"><span data-stu-id="5d036-219">Optionally, specifies a different name for the database to attach as.</span></span>  
  
     <span data-ttu-id="5d036-220">**所有者**</span><span class="sxs-lookup"><span data-stu-id="5d036-220">**Owner**</span></span>  
     <span data-ttu-id="5d036-221">提供数据库可能所有者的下拉列表，您可以根据需要从其中选择其他所有者。</span><span class="sxs-lookup"><span data-stu-id="5d036-221">Provides a drop-down list of possible database owners from which you can optionally select a different owner.</span></span>  
  
     <span data-ttu-id="5d036-222">**Status**</span><span class="sxs-lookup"><span data-stu-id="5d036-222">**Status**</span></span>  
     <span data-ttu-id="5d036-223">显示下表中相应的数据库状态。</span><span class="sxs-lookup"><span data-stu-id="5d036-223">Displays the status of the database according to the following table.</span></span>  
  
    |<span data-ttu-id="5d036-224">图标</span><span class="sxs-lookup"><span data-stu-id="5d036-224">Icon</span></span>|<span data-ttu-id="5d036-225">状态文本</span><span class="sxs-lookup"><span data-stu-id="5d036-225">Status text</span></span>|<span data-ttu-id="5d036-226">说明</span><span class="sxs-lookup"><span data-stu-id="5d036-226">Description</span></span>|  
    |----------|-----------------|-----------------|  
    |<span data-ttu-id="5d036-227">（无图标）</span><span class="sxs-lookup"><span data-stu-id="5d036-227">(No icon)</span></span>|<span data-ttu-id="5d036-228">（无文本）</span><span class="sxs-lookup"><span data-stu-id="5d036-228">(No text)</span></span>|<span data-ttu-id="5d036-229">此对象的附加操作尚未启动或者可能挂起。</span><span class="sxs-lookup"><span data-stu-id="5d036-229">Attach operation has not been started or may be pending for this object.</span></span> <span data-ttu-id="5d036-230">这是打开该对话框时的默认值。</span><span class="sxs-lookup"><span data-stu-id="5d036-230">This is the default when the dialog is opened.</span></span>|  
    |<span data-ttu-id="5d036-231">绿色的右向三角形</span><span class="sxs-lookup"><span data-stu-id="5d036-231">Green, right-pointing triangle</span></span>|<span data-ttu-id="5d036-232">正在进行</span><span class="sxs-lookup"><span data-stu-id="5d036-232">In progress</span></span>|<span data-ttu-id="5d036-233">已启动附加操作，但是该操作未完成。</span><span class="sxs-lookup"><span data-stu-id="5d036-233">Attach operation has been started but it is not complete.</span></span>|  
    |<span data-ttu-id="5d036-234">绿色的选中标记</span><span class="sxs-lookup"><span data-stu-id="5d036-234">Green check mark</span></span>|<span data-ttu-id="5d036-235">Success</span><span class="sxs-lookup"><span data-stu-id="5d036-235">Success</span></span>|<span data-ttu-id="5d036-236">已成功附加该对象。</span><span class="sxs-lookup"><span data-stu-id="5d036-236">The object has been attached successfully.</span></span>|  
    |<span data-ttu-id="5d036-237">包含白色十字形的红色圆圈</span><span class="sxs-lookup"><span data-stu-id="5d036-237">Red circle containing a white cross</span></span>|<span data-ttu-id="5d036-238">错误</span><span class="sxs-lookup"><span data-stu-id="5d036-238">Error</span></span>|<span data-ttu-id="5d036-239">附加操作遇到错误，未成功完成。</span><span class="sxs-lookup"><span data-stu-id="5d036-239">Attach operation encountered an error and did not complete successfully.</span></span>|  
    |<span data-ttu-id="5d036-240">包含左、右两个黑色象限和上、下两个白色象限的圆圈</span><span class="sxs-lookup"><span data-stu-id="5d036-240">Circle containing two black quadrants (on left and right) and two white quadrants (on top and bottom)</span></span>|<span data-ttu-id="5d036-241">已停止</span><span class="sxs-lookup"><span data-stu-id="5d036-241">Stopped</span></span>|<span data-ttu-id="5d036-242">由于用户停止了附加操作，该操作未成功完成。</span><span class="sxs-lookup"><span data-stu-id="5d036-242">Attach operation was not completed successfully because the user stopped the operation.</span></span>|  
    |<span data-ttu-id="5d036-243">包含一个指向逆时针方向的曲线箭头的圆圈</span><span class="sxs-lookup"><span data-stu-id="5d036-243">Circle containing a curved arrow pointing counter-clockwise</span></span>|<span data-ttu-id="5d036-244">已回滚</span><span class="sxs-lookup"><span data-stu-id="5d036-244">Rolled Back</span></span>|<span data-ttu-id="5d036-245">附加操作已成功，但已对其进行回滚，因为在附加其他对象的过程中出现了错误。</span><span class="sxs-lookup"><span data-stu-id="5d036-245">Attach operation was successful but it has been rolled back due to an error during attachment of another object.</span></span>|  
  
     <span data-ttu-id="5d036-246">**消息**</span><span class="sxs-lookup"><span data-stu-id="5d036-246">**Message**</span></span>  
     <span data-ttu-id="5d036-247">显示空消息或“找不到文件”超链接。</span><span class="sxs-lookup"><span data-stu-id="5d036-247">Displays either a blank message or a "File not found" hyperlink.</span></span>  
  
     <span data-ttu-id="5d036-248">**添加**</span><span class="sxs-lookup"><span data-stu-id="5d036-248">**Add**</span></span>  
     <span data-ttu-id="5d036-249">查找必需的主数据库文件。</span><span class="sxs-lookup"><span data-stu-id="5d036-249">Find the necessary main database files.</span></span> <span data-ttu-id="5d036-250">当用户选择 .mdf 文件时，就会在 **“要附加的数据库”** 网格的相应字段中自动填充合适的信息。</span><span class="sxs-lookup"><span data-stu-id="5d036-250">When the user selects an .mdf file, applicable information is automatically filled in the respective fields of the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="5d036-251">**删除**</span><span class="sxs-lookup"><span data-stu-id="5d036-251">**Remove**</span></span>  
     <span data-ttu-id="5d036-252">从 **“要附加的数据库”** 网格中删除选定文件。</span><span class="sxs-lookup"><span data-stu-id="5d036-252">Removes the selected file from the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="5d036-253">" <database_name> " 数据库详细信息</span><span class="sxs-lookup"><span data-stu-id="5d036-253">**"** _<database_name>_ **" database details**</span></span>  
     <span data-ttu-id="5d036-254">显示要附加的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="5d036-254">Displays the names of the files to be attached.</span></span> <span data-ttu-id="5d036-255">若要验证或更改文件的路径名，请单击“浏览”按钮 (…) 。</span><span class="sxs-lookup"><span data-stu-id="5d036-255">To verify or change the pathname of a file, click the **Browse** button (**...**).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5d036-256">如果文件不存在，则 **“消息”** 列显示“找不到”。</span><span class="sxs-lookup"><span data-stu-id="5d036-256">If a file does not exist, the **Message** column displays "Not found."</span></span> <span data-ttu-id="5d036-257">如果找不到日志文件，则说明它位于其他目录中或者已被删除。</span><span class="sxs-lookup"><span data-stu-id="5d036-257">If a log file is not found, it exists in another directory or has been deleted.</span></span> <span data-ttu-id="5d036-258">您需要更新 **“数据库详细信息”** 网格中该文件的路径使其指向正确的位置，或者从网格中删除该日志文件。</span><span class="sxs-lookup"><span data-stu-id="5d036-258">You need to either update the file path in the **database details** grid to point to the correct location or remove the log file from the grid.</span></span> <span data-ttu-id="5d036-259">如果找不到 .ndf 数据文件，则需要更新网格中该文件的路径使其指向正确的位置。</span><span class="sxs-lookup"><span data-stu-id="5d036-259">If an .ndf data file is not found, you need to update its path in the grid to point to the correct location.</span></span>  
  
     <span data-ttu-id="5d036-260">**原始文件名**</span><span class="sxs-lookup"><span data-stu-id="5d036-260">**Original File Name**</span></span>  
     <span data-ttu-id="5d036-261">显示属于数据库的已附加文件的名称。</span><span class="sxs-lookup"><span data-stu-id="5d036-261">Displays the name of the attached file belonging to the database.</span></span>  
  
     <span data-ttu-id="5d036-262">**文件类型**</span><span class="sxs-lookup"><span data-stu-id="5d036-262">**File Type**</span></span>  
     <span data-ttu-id="5d036-263">指示文件类型，即 **“数据”** 或 **“日志”** 。</span><span class="sxs-lookup"><span data-stu-id="5d036-263">Indicates the type of file, **Data** or **Log**.</span></span>  
  
     <span data-ttu-id="5d036-264">**当前文件路径**</span><span class="sxs-lookup"><span data-stu-id="5d036-264">**Current File Path**</span></span>  
     <span data-ttu-id="5d036-265">显示所选数据库文件的路径。</span><span class="sxs-lookup"><span data-stu-id="5d036-265">Displays the path to the selected database file.</span></span> <span data-ttu-id="5d036-266">可以手动编辑该路径。</span><span class="sxs-lookup"><span data-stu-id="5d036-266">The path can be edited manually.</span></span>  
  
     <span data-ttu-id="5d036-267">**消息**</span><span class="sxs-lookup"><span data-stu-id="5d036-267">**Message**</span></span>  
     <span data-ttu-id="5d036-268">显示空消息或 **“找不到文件”** 超链接。</span><span class="sxs-lookup"><span data-stu-id="5d036-268">Displays either a blank message or a "**File not found**" hyperlink.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlMove"></a> <span data-ttu-id="5d036-269">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5d036-269">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="5d036-270">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="5d036-270">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5d036-271">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="5d036-271">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5d036-272">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="5d036-272">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Detach the TDE protected database from the source server.   
    USE master ;  
    GO  
    EXEC master.dbo.sp_detach_db @dbname = N'CustRecords';  
    GO  
    -- Move or copy the database files from the source server to the same location on the destination server.   
    -- Move or copy the backup of the server certificate and the private key file from the source server to the same location on the destination server.   
    -- Create a database master key on the destination instance of SQL Server.   
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1';  
    GO  
    -- Recreate the server certificate by using the original server certificate backup file.   
    -- The password must be the same as the password that was used when the backup was created.  
  
    CREATE CERTIFICATE TestSQLServerCert   
    FROM FILE = 'TestSQLServerCert'  
    WITH PRIVATE KEY   
    (  
        FILE = 'SQLPrivateKeyFile',  
        DECRYPTION BY PASSWORD = '*rt@40(FL&dasl1'  
    );  
    GO  
    -- Attach the database that is being moved.   
    -- The path of the database files must be the location where you have stored the database files.  
    CREATE DATABASE [CustRecords] ON   
    ( FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\CustRecords.mdf' ),  
    ( FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\CustRecords_log.LDF' )  
    FOR ATTACH ;  
    GO  
    ```  
  
 <span data-ttu-id="5d036-273">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="5d036-273">For more information, see:</span></span>  
  
-   [<span data-ttu-id="5d036-274">sp_detach_db (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5d036-274">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
-   [<span data-ttu-id="5d036-275">CREATE MASTER KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5d036-275">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [<span data-ttu-id="5d036-276">CREATE CERTIFICATE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5d036-276">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [<span data-ttu-id="5d036-277">CREATE DATABASE (SQL Server Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5d036-277">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="5d036-278">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d036-278">See Also</span></span>  
 [<span data-ttu-id="5d036-279">数据库分离和附加 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5d036-279">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../../databases/database-detach-and-attach-sql-server.md)  
  
  
