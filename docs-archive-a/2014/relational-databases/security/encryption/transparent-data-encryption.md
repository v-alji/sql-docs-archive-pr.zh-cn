---
title: 透明数据加密 (TDE) | Microsoft Docs
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption
- database encryption key, about
- TDE
- database encryption key
- TDE, about
- Transparent Data Encryption, about
- encryption [SQL Server], transparent data encryption
ms.assetid: c75d0d4b-4008-4e71-9a9d-cee2a566bd3b
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: a8118f0781d7c9e3d839c029c6bdaf8b01e074b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587308"
---
# <a name="transparent-data-encryption-tde"></a><span data-ttu-id="08072-102">透明数据加密 (TDE)</span><span class="sxs-lookup"><span data-stu-id="08072-102">Transparent Data Encryption (TDE)</span></span>
  <span data-ttu-id="08072-103">*透明数据加密* (TDE) 加密 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] 数据文件，称为加密空闲数据。</span><span class="sxs-lookup"><span data-stu-id="08072-103">*Transparent Data Encryption* (TDE) encrypts [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] data files, known as encrypting data at rest.</span></span> <span data-ttu-id="08072-104">可以采取多种预防措施来帮助保护数据库，例如，设计安全系统、加密机密资产，以及围绕数据库服务器构建防火墙。</span><span class="sxs-lookup"><span data-stu-id="08072-104">You can take several precautions to help secure the database such as designing a secure system, encrypting confidential assets, and building a firewall around the database servers.</span></span> <span data-ttu-id="08072-105">但是，如果物理媒体（如驱动器或备份磁带）失窃，恶意方可能会还原或附加数据库并浏览数据。</span><span class="sxs-lookup"><span data-stu-id="08072-105">However, in a scenario where the physical media (such as drives or backup tapes) are stolen, a malicious party can just restore or attach the database and browse the data.</span></span> <span data-ttu-id="08072-106">一种解决方案是加密数据库中的敏感数据，并通过证书保护用于加密数据的密钥。</span><span class="sxs-lookup"><span data-stu-id="08072-106">One solution is to encrypt the sensitive data in the database and protect the keys that are used to encrypt the data with a certificate.</span></span> <span data-ttu-id="08072-107">这可以防止任何没有密钥的人使用这些数据，但这种保护必须事先计划。</span><span class="sxs-lookup"><span data-stu-id="08072-107">This prevents anyone without the keys from using the data, but this kind of protection must be planned in advance.</span></span>

 <span data-ttu-id="08072-108">TDE 针对数据和日志文件执行实时 I/O 加密和解密。</span><span class="sxs-lookup"><span data-stu-id="08072-108">TDE performs real-time I/O encryption and decryption of the data and log files.</span></span> <span data-ttu-id="08072-109">加密使用数据库加密密钥 (DEK)，它存储在数据库引导记录中，可在恢复时使用。</span><span class="sxs-lookup"><span data-stu-id="08072-109">The encryption uses a database encryption key (DEK), which is stored in the database boot record for availability during recovery.</span></span> <span data-ttu-id="08072-110">DEK 是使用存储在服务器的 master 数据库中的证书保护的对称密钥，或者是由 EKM 模块保护的非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="08072-110">The DEK is a symmetric key secured by using a certificate stored in the master database of the server or an asymmetric key protected by an EKM module.</span></span> <span data-ttu-id="08072-111">TDE 保护“处于休眠状态”的数据，即数据和日志文件。</span><span class="sxs-lookup"><span data-stu-id="08072-111">TDE protects data "at rest", meaning the data and log files.</span></span> <span data-ttu-id="08072-112">它提供了遵从许多法律、法规和各个行业建立的准则的能力。</span><span class="sxs-lookup"><span data-stu-id="08072-112">It provides the ability to comply with many laws, regulations, and guidelines established in various industries.</span></span> <span data-ttu-id="08072-113">软件开发人员籍此可以使用 AES 和 3DES 加密算法来加密数据，且无需更改现有的应用程序。</span><span class="sxs-lookup"><span data-stu-id="08072-113">This enables software developers to encrypt data by using AES and 3DES encryption algorithms without changing existing applications.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="08072-114">TDE 不提供跨通信信道加密。</span><span class="sxs-lookup"><span data-stu-id="08072-114">TDE does not provide encryption across communication channels.</span></span> <span data-ttu-id="08072-115">有关如何跨通信信道加密数据，请参阅[启用数据库引擎的加密连接（SQL Server 配置管理器）](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="08072-115">For more information about how to encrypt data across communication channels, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>
> 
>  <span data-ttu-id="08072-116">**相关主题：**</span><span class="sxs-lookup"><span data-stu-id="08072-116">**Related topics:**</span></span>
> 
>  -   [<span data-ttu-id="08072-117">借助 Azure SQL 数据库实现透明数据加密</span><span class="sxs-lookup"><span data-stu-id="08072-117">Transparent Data Encryption with Azure SQL Database</span></span>](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)
> -   [<span data-ttu-id="08072-118">将受 TDE 保护的数据库移到其他 SQL Server</span><span class="sxs-lookup"><span data-stu-id="08072-118">Move a TDE Protected Database to Another SQL Server</span></span>](move-a-tde-protected-database-to-another-sql-server.md)
> -   [<span data-ttu-id="08072-119">使用 EKM 启用 TDE</span><span class="sxs-lookup"><span data-stu-id="08072-119">Enable TDE Using EKM</span></span>](enable-tde-on-sql-server-using-ekm.md)

## <a name="about-tde"></a><span data-ttu-id="08072-120">关于 TDE</span><span class="sxs-lookup"><span data-stu-id="08072-120">About TDE</span></span>
 <span data-ttu-id="08072-121">数据库文件加密在页面级执行。</span><span class="sxs-lookup"><span data-stu-id="08072-121">Encryption of the database file is performed at the page level.</span></span> <span data-ttu-id="08072-122">已加密数据库中的页在写入磁盘之前会进行加密，在读入内存时会进行解密。</span><span class="sxs-lookup"><span data-stu-id="08072-122">The pages in an encrypted database are encrypted before they are written to disk and decrypted when read into memory.</span></span> <span data-ttu-id="08072-123">TDE 不会增加已加密数据库的大小。</span><span class="sxs-lookup"><span data-stu-id="08072-123">TDE does not increase the size of the encrypted database.</span></span>

 <span data-ttu-id="08072-124">**适用于的信息[!INCLUDE[ssSDS](../../../includes/sssds-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="08072-124">**Information applicable to [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]**</span></span>

 <span data-ttu-id="08072-125">当将 TDE 与 [!INCLUDE[sqldbesa](../../../includes/sqldbesa-md.md)] V12（[在某些区域是预览版](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)）一起使用时， [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]将为你自动创建存储在 master 数据库中的服务器级别的证书。</span><span class="sxs-lookup"><span data-stu-id="08072-125">When using TDE with [!INCLUDE[sqldbesa](../../../includes/sqldbesa-md.md)] V12  ([Preview in some regions](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)) the server-level certificate stored in the master database is automatically created for you by [!INCLUDE[ssSDS](../../../includes/sssds-md.md)].</span></span> <span data-ttu-id="08072-126">若要移动 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] 上的 TDE 数据库，必须解密该数据库、移动该数据库，然后在目标 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]上重新启用 TDE。</span><span class="sxs-lookup"><span data-stu-id="08072-126">To move a TDE database on [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] you must decrypt the database, move the database, and then re-enable TDE on the destination [!INCLUDE[ssSDS](../../../includes/sssds-md.md)].</span></span> <span data-ttu-id="08072-127">有关 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]上 TDE 的分步说明，请参阅 [Transparent Data Encryption with Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)。</span><span class="sxs-lookup"><span data-stu-id="08072-127">For step-by-step instructions for TDE on [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], see [Transparent Data Encryption with Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md).</span></span>

 <span data-ttu-id="08072-128">即使在 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] 的版本系列 V12 现在宣布为处于公开发布状态的部分地理区域中，TDE 的状态预览也适用。</span><span class="sxs-lookup"><span data-stu-id="08072-128">The preview of status of TDE applies even in the subset of geographic regions where version family V12 of [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] is announced as now being in general availability status.</span></span> <span data-ttu-id="08072-129">在 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] 宣布将 TDE 从预览提升为 GA 之前， [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 的 TDE 不适用于生产数据库。</span><span class="sxs-lookup"><span data-stu-id="08072-129">TDE for [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] is not intended for use in production databases until [!INCLUDE[msCoName](../../../includes/msconame-md.md)] announces that TDE is promoted from preview to GA.</span></span> <span data-ttu-id="08072-130">有关 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] V12 的详细信息，请参阅 [Azure SQL Database 中的新增功能](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/)。</span><span class="sxs-lookup"><span data-stu-id="08072-130">For more information about [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] V12, see [What's new in Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/).</span></span>

 <span data-ttu-id="08072-131">**适用于的信息[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="08072-131">**Information applicable to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**</span></span>

 <span data-ttu-id="08072-132">对数据库实施保护措施后，可以通过使用正确的证书还原此数据库。</span><span class="sxs-lookup"><span data-stu-id="08072-132">After it is secured, the database can be restored by using the correct certificate.</span></span> <span data-ttu-id="08072-133">有关证书的详细信息，请参阅 [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="08072-133">For more information about certificates, see [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).</span></span>

 <span data-ttu-id="08072-134">启用 TDE 时，应该立即备份证书和与证书相关联的私钥。</span><span class="sxs-lookup"><span data-stu-id="08072-134">When enabling TDE, you should immediately back up the certificate and the private key associated with the certificate.</span></span> <span data-ttu-id="08072-135">如果证书变为不可用，或者如果必须在另一台服务器上还原或附加数据库，则必须同时具有证书和私钥的备份，否则将无法打开该数据库。</span><span class="sxs-lookup"><span data-stu-id="08072-135">If the certificate ever becomes unavailable or if you must restore or attach the database on another server, you must have backups of both the certificate and the private key or you will not be able to open the database.</span></span> <span data-ttu-id="08072-136">即使不再对数据库启用 TDE，也应该保留加密证书。</span><span class="sxs-lookup"><span data-stu-id="08072-136">The encrypting certificate should be retained even if TDE is no longer enabled on the database.</span></span> <span data-ttu-id="08072-137">即使数据库未加密，事务日志的某些部分仍可能保持受到保护，但在执行数据库的完整备份前，对于某些操作可能需要证书。</span><span class="sxs-lookup"><span data-stu-id="08072-137">Even though the database is not encrypted, parts of the transaction log may still remain protected, and the certificate may be needed for some operations until the full backup of the database is performed.</span></span> <span data-ttu-id="08072-138">超过过期日期的证书仍可以用于通过 TDE 加密和解密数据。</span><span class="sxs-lookup"><span data-stu-id="08072-138">A certificate that has exceeded its expiration date can still be used to encrypt and decrypt data with TDE.</span></span>

 <span data-ttu-id="08072-139">**加密层次结构**</span><span class="sxs-lookup"><span data-stu-id="08072-139">**Encryption Hierarchy**</span></span>

 <span data-ttu-id="08072-140">下图显示了 TDE 加密体系结构。</span><span class="sxs-lookup"><span data-stu-id="08072-140">The following illustration shows the architecture of TDE encryption.</span></span> <span data-ttu-id="08072-141">仅数据库级项目（在 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]上使用 TDE 时，用户可配置数据库加密密钥和 ALTER DATABASE 部分。</span><span class="sxs-lookup"><span data-stu-id="08072-141">Only the database level items (the database encryption key and ALTER DATABASE portions are user-configurable when using TDE on [!INCLUDE[ssSDS](../../../includes/sssds-md.md)].</span></span>

 <span data-ttu-id="08072-142">![显示主题中介绍的层次结构。](../../../database-engine/media/tde-architecture.gif "显示主题中介绍的层次结构。")</span><span class="sxs-lookup"><span data-stu-id="08072-142">![Displays the hierarchy described in the topic.](../../../database-engine/media/tde-architecture.gif "Displays the hierarchy described in the topic.")</span></span>

## <a name="using-transparent-data-encryption"></a><span data-ttu-id="08072-143">使用透明数据加密</span><span class="sxs-lookup"><span data-stu-id="08072-143">Using Transparent Data Encryption</span></span>
 <span data-ttu-id="08072-144">若要使用 TDE，请按以下步骤操作。</span><span class="sxs-lookup"><span data-stu-id="08072-144">To use TDE, follow these steps.</span></span>

||
|-|
|<span data-ttu-id="08072-145">**适用于**： [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="08072-145">**Applies to**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>|

-   <span data-ttu-id="08072-146">创建主密钥</span><span class="sxs-lookup"><span data-stu-id="08072-146">Create a master key</span></span>

-   <span data-ttu-id="08072-147">创建或获取由主密钥保护的证书</span><span class="sxs-lookup"><span data-stu-id="08072-147">Create or obtain a certificate protected by the master key</span></span>

-   <span data-ttu-id="08072-148">创建数据库加密密钥并通过此证书保护该密钥</span><span class="sxs-lookup"><span data-stu-id="08072-148">Create a database encryption key and protect it by the certificate</span></span>

-   <span data-ttu-id="08072-149">将数据库设置为使用加密</span><span class="sxs-lookup"><span data-stu-id="08072-149">Set the database to use encryption</span></span>

 <span data-ttu-id="08072-150">下面的示例演示如何使用安装在名为 `AdventureWorks2012` 的服务器上的证书加密和解密 `MyServerCert`数据库。</span><span class="sxs-lookup"><span data-stu-id="08072-150">The following example illustrates encrypting and decrypting the `AdventureWorks2012` database using a certificate installed on the server named `MyServerCert`.</span></span>

```
USE master;
GO
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';
go
CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My DEK Certificate';
go
USE AdventureWorks2012;
GO
CREATE DATABASE ENCRYPTION KEY
WITH ALGORITHM = AES_128
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;
GO
ALTER DATABASE AdventureWorks2012
SET ENCRYPTION ON;
GO
```

 <span data-ttu-id="08072-151">加密和解密操作由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]安排在后台线程中执行。</span><span class="sxs-lookup"><span data-stu-id="08072-151">The encryption and decryption operations are scheduled on background threads by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="08072-152">您可以使用本主题后面部分显示的列表中的目录视图和动态管理视图查看这些操作的状态。</span><span class="sxs-lookup"><span data-stu-id="08072-152">You can view the status of these operations using the catalog views and dynamic management views in the list that appears later in this topic.</span></span>

> [!CAUTION]
>  <span data-ttu-id="08072-153">启用了 TDE 的数据库的备份文件也使用数据库加密密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="08072-153">Backup files of databases that have TDE enabled are also encrypted by using the database encryption key.</span></span> <span data-ttu-id="08072-154">因此，当您还原这些备份时，用于保护数据库加密密钥的证书必须可用。</span><span class="sxs-lookup"><span data-stu-id="08072-154">As a result, when you restore these backups, the certificate protecting the database encryption key must be available.</span></span> <span data-ttu-id="08072-155">也就是说，除了备份数据库之外，您还要确保自己保留了服务器证书的备份以防数据丢失。</span><span class="sxs-lookup"><span data-stu-id="08072-155">This means that in addition to backing up the database, you have to make sure that you maintain backups of the server certificates to prevent data loss.</span></span> <span data-ttu-id="08072-156">如果证书不再可用，将会导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="08072-156">Data loss will result if the certificate is no longer available.</span></span> <span data-ttu-id="08072-157">有关详细信息，请参阅 [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="08072-157">For more information, see [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).</span></span>

## <a name="commands-and-functions"></a><span data-ttu-id="08072-158">命令和函数</span><span class="sxs-lookup"><span data-stu-id="08072-158">Commands and Functions</span></span>
 <span data-ttu-id="08072-159">TDE 证书必须使用数据库主密钥加密才能被下列语句接受。</span><span class="sxs-lookup"><span data-stu-id="08072-159">The TDE certificates must be encrypted by the database master key to be accepted by the following statements.</span></span> <span data-ttu-id="08072-160">如果它们仅用密码加密，这些语句将拒绝将它们视为加密程序。</span><span class="sxs-lookup"><span data-stu-id="08072-160">If they are encrypted by password only, the statements will reject them as encryptors.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="08072-161">在 TDE 使用证书之后将证书改为用密码保护将会导致数据库在重新启动后无法访问。</span><span class="sxs-lookup"><span data-stu-id="08072-161">Altering the certificates to be password-protected after they are used by TDE will cause the database to become inaccessible after a restart.</span></span>

 <span data-ttu-id="08072-162">下表提供了 TDE 命令和函数的链接和说明。</span><span class="sxs-lookup"><span data-stu-id="08072-162">The following table provides links and explanations of TDE commands and functions.</span></span>

|<span data-ttu-id="08072-163">命令或函数</span><span class="sxs-lookup"><span data-stu-id="08072-163">Command or function</span></span>|<span data-ttu-id="08072-164">目的</span><span class="sxs-lookup"><span data-stu-id="08072-164">Purpose</span></span>|
|-------------------------|-------------|
|[<span data-ttu-id="08072-165">CREATE DATABASE ENCRYPTION KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="08072-165">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)|<span data-ttu-id="08072-166">创建一个用于加密数据库的密钥。</span><span class="sxs-lookup"><span data-stu-id="08072-166">Creates a key that is used to encrypt a database.</span></span>|
|[<span data-ttu-id="08072-167">ALTER DATABASE ENCRYPTION KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="08072-167">ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-encryption-key-transact-sql)|<span data-ttu-id="08072-168">更改用于加密数据库的密钥。</span><span class="sxs-lookup"><span data-stu-id="08072-168">Changes the key that is used to encrypt a database.</span></span>|
|[<span data-ttu-id="08072-169">DROP DATABASE ENCRYPTION KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="08072-169">DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-database-transact-sql)|<span data-ttu-id="08072-170">删除用于加密数据库的密钥。</span><span class="sxs-lookup"><span data-stu-id="08072-170">Removes the key that was used to encrypt a database.</span></span>|
|[<span data-ttu-id="08072-171">ALTER DATABASE SET 选项 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="08072-171">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)|<span data-ttu-id="08072-172">介绍用来启用 TDE 的 `ALTER DATABASE` 选项。</span><span class="sxs-lookup"><span data-stu-id="08072-172">Explains the `ALTER DATABASE` option that is used to enable TDE.</span></span>|

## <a name="catalog-views-and-dynamic-management-views"></a><span data-ttu-id="08072-173">目录视图和动态管理视图</span><span class="sxs-lookup"><span data-stu-id="08072-173">Catalog Views and Dynamic Management Views</span></span>
 <span data-ttu-id="08072-174">下表显示了 TDE 目录视图和动态管理视图。</span><span class="sxs-lookup"><span data-stu-id="08072-174">The following table shows TDE catalog views and dynamic management views.</span></span>

|<span data-ttu-id="08072-175">目录视图或动态管理视图</span><span class="sxs-lookup"><span data-stu-id="08072-175">Catalog view or dynamic management view</span></span>|<span data-ttu-id="08072-176">目的</span><span class="sxs-lookup"><span data-stu-id="08072-176">Purpose</span></span>|
|---------------------------------------------|-------------|
|[<span data-ttu-id="08072-177">sys.databases (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="08072-177">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)|<span data-ttu-id="08072-178">显示数据库信息的目录视图。</span><span class="sxs-lookup"><span data-stu-id="08072-178">Catalog view that displays database information.</span></span>|
|[<span data-ttu-id="08072-179">sys.certificates (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="08072-179">sys.certificates &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)|<span data-ttu-id="08072-180">显示数据库中的证书的目录视图。</span><span class="sxs-lookup"><span data-stu-id="08072-180">Catalog view that shows the certificates in a database.</span></span>|
|[<span data-ttu-id="08072-181">sys.dm_database_encryption_keys (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="08072-181">sys.dm_database_encryption_keys &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)|<span data-ttu-id="08072-182">提供有关数据库中使用的加密密钥的信息以及数据库加密状态的动态管理视图。</span><span class="sxs-lookup"><span data-stu-id="08072-182">Dynamic management view that provides information about the encryption keys used in a database, and the state of encryption of a database.</span></span>|

## <a name="permissions"></a><span data-ttu-id="08072-183">权限</span><span class="sxs-lookup"><span data-stu-id="08072-183">Permissions</span></span>
 <span data-ttu-id="08072-184">如上表中所述，TDE 的每项功能和每个命令都有各自的权限要求。</span><span class="sxs-lookup"><span data-stu-id="08072-184">Each TDE feature and command has individual permission requirements, described in the tables shown earlier.</span></span>

 <span data-ttu-id="08072-185">查看 TDE 所涉及的元数据要求拥有对证书的 VIEW DEFINITION 权限。</span><span class="sxs-lookup"><span data-stu-id="08072-185">Viewing the metadata involved with TDE requires the VIEW DEFINITION permission on the certificate.</span></span>

## <a name="considerations"></a><span data-ttu-id="08072-186">注意事项</span><span class="sxs-lookup"><span data-stu-id="08072-186">Considerations</span></span>
 <span data-ttu-id="08072-187">当进行数据库加密操作的重新加密扫描时，将禁用对数据库的维护操作。</span><span class="sxs-lookup"><span data-stu-id="08072-187">While a re-encryption scan for a database encryption operation is in progress, maintenance operations to the database are disabled.</span></span> <span data-ttu-id="08072-188">您可以使用数据库的单用户模式设置来执行维护操作。</span><span class="sxs-lookup"><span data-stu-id="08072-188">You can use the single user mode setting for the database to perform the maintenance operation.</span></span> <span data-ttu-id="08072-189">有关详细信息，请参阅 [将数据库设置为单用户模式](../../databases/set-a-database-to-single-user-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="08072-189">For more information, see [Set a Database to Single-user Mode](../../databases/set-a-database-to-single-user-mode.md).</span></span>

 <span data-ttu-id="08072-190">可以使用 sys.dm_database_encryption_keys 动态管理视图来确定数据库加密状态。</span><span class="sxs-lookup"><span data-stu-id="08072-190">You can find the state of the database encryption using the sys.dm_database_encryption_keys dynamic management view.</span></span> <span data-ttu-id="08072-191">有关详细信息，请参阅本主题前面的“目录视图和动态管理视图”部分。</span><span class="sxs-lookup"><span data-stu-id="08072-191">For more information, see the "Catalog Views and Dynamic Management Views"section earlier in this topic).</span></span>

 <span data-ttu-id="08072-192">在 TDE 过程中，数据库中的所有文件和文件组都进行加密。</span><span class="sxs-lookup"><span data-stu-id="08072-192">In TDE, all files and filegroups in the database are encrypted.</span></span> <span data-ttu-id="08072-193">如果将数据库中的任何文件组标记为 READ ONLY，数据库加密操作将会失败。</span><span class="sxs-lookup"><span data-stu-id="08072-193">If any filegroups in a database are marked READ ONLY, the database encryption operation will fail.</span></span>

 <span data-ttu-id="08072-194">如果某个数据库正在用于数据库镜像或日志传送，则两个数据库都将进行加密。</span><span class="sxs-lookup"><span data-stu-id="08072-194">If a database is being used in database mirroring or log shipping, both databases will be encrypted.</span></span> <span data-ttu-id="08072-195">日志事务将以加密形式在它们之间发送。</span><span class="sxs-lookup"><span data-stu-id="08072-195">The log transactions will be encrypted when sent between them.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="08072-196">当数据库设置为加密时，将加密所有新的全文索引。</span><span class="sxs-lookup"><span data-stu-id="08072-196">Any new full-text indexes will be encrypted when a database is set for encryption.</span></span> <span data-ttu-id="08072-197">以前创建的全文索引将在升级期间导入，在将数据加载到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]后，将对这些索引进行 TDE。</span><span class="sxs-lookup"><span data-stu-id="08072-197">Previously-created full-text indexes will be imported during upgrade and they will be in TDE after the data is loaded into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="08072-198">对列启用全文索引可导致在全文索引扫描期间将该列数据以纯文本方式写入磁盘。</span><span class="sxs-lookup"><span data-stu-id="08072-198">Enabling a full-text index on a column can cause that column's data to be written in plain text onto the disk during a full-text indexing scan.</span></span> <span data-ttu-id="08072-199">建议不要对已加密的敏感数据创建全文索引。</span><span class="sxs-lookup"><span data-stu-id="08072-199">We recommend that you do not create a full-text index on sensitive encrypted data.</span></span>

 <span data-ttu-id="08072-200">与未加密数据相比，同样的加密数据的压缩率要小得多。</span><span class="sxs-lookup"><span data-stu-id="08072-200">Encrypted data compresses significantly less than equivalent unencrypted data.</span></span> <span data-ttu-id="08072-201">如果使用 TDE 对数据库进行加密，备份压缩将无法显著压缩备份存储。</span><span class="sxs-lookup"><span data-stu-id="08072-201">If TDE is used to encrypt a database, backup compression will not be able to significantly compress the backup storage.</span></span> <span data-ttu-id="08072-202">因此，不建议将 TDE 与备份压缩一起使用。</span><span class="sxs-lookup"><span data-stu-id="08072-202">Therefore, using TDE and backup compression together is not recommended.</span></span>

### <a name="restrictions"></a><span data-ttu-id="08072-203">限制</span><span class="sxs-lookup"><span data-stu-id="08072-203">Restrictions</span></span>
 <span data-ttu-id="08072-204">在初始数据库加密、密钥更改或数据库解密期间，不允许执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="08072-204">The following operations are not allowed during initial database encryption, key change, or database decryption:</span></span>

-   <span data-ttu-id="08072-205">从数据库中的文件组中删除文件</span><span class="sxs-lookup"><span data-stu-id="08072-205">Dropping a file from a filegroup in the database</span></span>

-   <span data-ttu-id="08072-206">删除数据库</span><span class="sxs-lookup"><span data-stu-id="08072-206">Dropping the database</span></span>

-   <span data-ttu-id="08072-207">使数据库脱机</span><span class="sxs-lookup"><span data-stu-id="08072-207">Taking the database offline</span></span>

-   <span data-ttu-id="08072-208">分离数据库</span><span class="sxs-lookup"><span data-stu-id="08072-208">Detaching a database</span></span>

-   <span data-ttu-id="08072-209">将数据库或文件组转换为 READ ONLY 状态</span><span class="sxs-lookup"><span data-stu-id="08072-209">Transitioning a database or filegroup into a READ ONLY state</span></span>

 <span data-ttu-id="08072-210">在执行 CREATE DATABASE ENCRYPTION KEY、ALTER DATABASE ENCRYPTION KEY、DROP DATABASE ENCRYPTION KEY 或 ALTER DATABASE...SET ENCRYPTION 语句期间，不允许执行下列操作。</span><span class="sxs-lookup"><span data-stu-id="08072-210">The following operations are not allowed during the CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY, or ALTER DATABASE...SET ENCRYPTION statements.</span></span>

-   <span data-ttu-id="08072-211">从数据库中的文件组中删除文件。</span><span class="sxs-lookup"><span data-stu-id="08072-211">Dropping a file from a filegroup in the database.</span></span>

-   <span data-ttu-id="08072-212">删除数据库。</span><span class="sxs-lookup"><span data-stu-id="08072-212">Dropping the database.</span></span>

-   <span data-ttu-id="08072-213">使数据库脱机。</span><span class="sxs-lookup"><span data-stu-id="08072-213">Taking the database offline.</span></span>

-   <span data-ttu-id="08072-214">分离数据库。</span><span class="sxs-lookup"><span data-stu-id="08072-214">Detaching a database.</span></span>

-   <span data-ttu-id="08072-215">将数据库或文件组转换为 READ ONLY 状态。</span><span class="sxs-lookup"><span data-stu-id="08072-215">Transitioning a database or filegroup into a READ ONLY state.</span></span>

-   <span data-ttu-id="08072-216">使用 ALTER DATABASE 命令。</span><span class="sxs-lookup"><span data-stu-id="08072-216">Using an ALTER DATABASE command.</span></span>

-   <span data-ttu-id="08072-217">启动数据库或数据库文件备份。</span><span class="sxs-lookup"><span data-stu-id="08072-217">Starting a database or database file backup.</span></span>

-   <span data-ttu-id="08072-218">启动数据库或数据库文件还原。</span><span class="sxs-lookup"><span data-stu-id="08072-218">Starting a database or database file restore.</span></span>

-   <span data-ttu-id="08072-219">创建快照。</span><span class="sxs-lookup"><span data-stu-id="08072-219">Creating a snapshot.</span></span>

 <span data-ttu-id="08072-220">下列操作或条件将阻止执行 CREATE DATABASE ENCRYPTION KEY、ALTER DATABASE ENCRYPTION KEY、DROP DATABASE ENCRYPTION KEY 或 ALTER DATABASE...SET ENCRYPTION 语句。</span><span class="sxs-lookup"><span data-stu-id="08072-220">The following operations or conditions will prevent the CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY, or ALTER DATABASE...SET ENCRYPTION statements.</span></span>

-   <span data-ttu-id="08072-221">数据库为只读或包含任何只读文件组。</span><span class="sxs-lookup"><span data-stu-id="08072-221">The database is read-only or has any read-only file groups.</span></span>

-   <span data-ttu-id="08072-222">正在执行 ALTER DATABASE 命令。</span><span class="sxs-lookup"><span data-stu-id="08072-222">An ALTER DATABASE command is executing.</span></span>

-   <span data-ttu-id="08072-223">正在进行任何数据备份。</span><span class="sxs-lookup"><span data-stu-id="08072-223">Any data backup is running.</span></span>

-   <span data-ttu-id="08072-224">数据处于脱机或还原状态。</span><span class="sxs-lookup"><span data-stu-id="08072-224">The database is in an offline or restore condition.</span></span>

-   <span data-ttu-id="08072-225">正在创建快照。</span><span class="sxs-lookup"><span data-stu-id="08072-225">A snapshot is in progress.</span></span>

-   <span data-ttu-id="08072-226">数据库维护任务。</span><span class="sxs-lookup"><span data-stu-id="08072-226">Database maintenance tasks.</span></span>

 <span data-ttu-id="08072-227">当创建数据库文件时，如果启用了 TDE，则即时文件初始化功能不可用。</span><span class="sxs-lookup"><span data-stu-id="08072-227">When creating database files, instant file initialization is not available when TDE is enabled.</span></span>

 <span data-ttu-id="08072-228">要使用非对称密钥对数据库加密密钥进行加密，非对称密钥必须驻留在可扩展密钥管理提供程序上。</span><span class="sxs-lookup"><span data-stu-id="08072-228">In order to encrypt the database encryption key with an asymmetric key, the asymmetric key must reside on an extensible key management provider.</span></span>

### <a name="transparent-data-encryption-and-transaction-logs"></a><span data-ttu-id="08072-229">透明数据加密与事务日志</span><span class="sxs-lookup"><span data-stu-id="08072-229">Transparent Data Encryption and Transaction Logs</span></span>
 <span data-ttu-id="08072-230">允许数据库使用 TDE 具有将虚拟事务日志的剩余部分“清零”以强制加密下一个虚拟事务日志的效果。</span><span class="sxs-lookup"><span data-stu-id="08072-230">Enabling a database to use TDE has the effect of "zeroing out" the remaining part of the virtual transaction log to force the next virtual transaction log.</span></span> <span data-ttu-id="08072-231">这可以保证在数据库设置为加密后事务日志中不会留有明文。</span><span class="sxs-lookup"><span data-stu-id="08072-231">This guarantees that no clear text is left in the transaction logs after the database is set for encryption.</span></span> <span data-ttu-id="08072-232">可通过查看 `encryption_state` 视图中的 `sys.dm_database_encryption_keys` 列来确定日志文件加密状态，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="08072-232">You can find the status of the log file encryption by viewing the `encryption_state` column in the `sys.dm_database_encryption_keys` view, as in this example:</span></span>

```
USE AdventureWorks2012;
GO
/* The value 3 represents an encrypted state 
   on the database and transaction logs. */
SELECT *
FROM sys.dm_database_encryption_keys
WHERE encryption_state = 3;
GO
```

 <span data-ttu-id="08072-233">有关 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 日志文件体系结构的详细信息，请参阅[事务日志 (SQL Server)](../../logs/the-transaction-log-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="08072-233">For more information about the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] log file architecture, see [The Transaction Log &#40;SQL Server&#41;](../../logs/the-transaction-log-sql-server.md).</span></span>

 <span data-ttu-id="08072-234">所有在数据库加密密钥更改前写入事务日志的数据都将使用之前的数据库加密密钥加密。</span><span class="sxs-lookup"><span data-stu-id="08072-234">All data written to the transaction log before a change in the database encryption key will be encrypted by using the previous database encryption key.</span></span>

 <span data-ttu-id="08072-235">在数据库加密密钥修改过两次后，必须执行日志备份才能再次对数据库加密密钥进行修改。</span><span class="sxs-lookup"><span data-stu-id="08072-235">After a database encryption key has been modified twice, a log backup must be performed before the database encryption key can be modified again.</span></span>

### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a><span data-ttu-id="08072-236">透明数据加密与 tempdb 系统数据库</span><span class="sxs-lookup"><span data-stu-id="08072-236">Transparent Data Encryption and the tempdb System Database</span></span>
 <span data-ttu-id="08072-237">如果 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例中的任何其他数据库是使用 TDE 加密的，则会加密 tempdb 系统数据库。</span><span class="sxs-lookup"><span data-stu-id="08072-237">The tempdb system database will be encrypted if any other database on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is encrypted by using TDE.</span></span> <span data-ttu-id="08072-238">这可能会对同一个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例上的未加密数据库产生性能影响。</span><span class="sxs-lookup"><span data-stu-id="08072-238">This might have a performance effect for unencrypted databases on the same instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="08072-239">有关 tempdb 系统数据库的详细信息，请参阅 tempdb 数据库。</span><span class="sxs-lookup"><span data-stu-id="08072-239">For more information about the tempdb system database, see [tempdb Database](../../databases/tempdb-database.md).</span></span>

### <a name="transparent-data-encryption-and-replication"></a><span data-ttu-id="08072-240">透明数据加密和复制</span><span class="sxs-lookup"><span data-stu-id="08072-240">Transparent Data Encryption and Replication</span></span>
 <span data-ttu-id="08072-241">复制不会以加密形式从启用了 TDE 的数据库中自动复制数据。</span><span class="sxs-lookup"><span data-stu-id="08072-241">Replication does not automatically replicate data from a TDE-enabled database in an encrypted form.</span></span> <span data-ttu-id="08072-242">如果您想保护分发和订阅服务器数据库，则必须单独启用 TDE。</span><span class="sxs-lookup"><span data-stu-id="08072-242">You must separately enable TDE if you want to protect the distribution and subscriber databases.</span></span> <span data-ttu-id="08072-243">快照复制以及用于事务和合并复制的初始数据分发，都能够在未加密的中间文件（例如 bcp 文件）中存储数据。</span><span class="sxs-lookup"><span data-stu-id="08072-243">Snapshot replication, as well as the initial distribution of data for transactional and merge replication, can store data in unencrypted intermediate files; for example, the bcp files.</span></span>  <span data-ttu-id="08072-244">在事务或合并复制期间，可以启用加密来保护通信信道。</span><span class="sxs-lookup"><span data-stu-id="08072-244">During transactional or merge replication, encryption can be enabled to protect the communication channel.</span></span> <span data-ttu-id="08072-245">有关详细信息，请参阅[启用数据库引擎的加密连接（SQL Server 配置管理器）](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="08072-245">For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>

### <a name="transparent-data-encryption-and-filestream-data"></a><span data-ttu-id="08072-246">透明数据加密和 FILESTREAM 数据</span><span class="sxs-lookup"><span data-stu-id="08072-246">Transparent Data Encryption and FILESTREAM DATA</span></span>
 <span data-ttu-id="08072-247">即使启用了 TDE，也不会加密 FILESTREAM 数据。</span><span class="sxs-lookup"><span data-stu-id="08072-247">FILESTREAM data is not encrypted even when TDE is enabled.</span></span>

### <a name="transparent-data-encryption-and-buffer-pool-extension"></a><span data-ttu-id="08072-248">透明数据加密和缓冲池扩展</span><span class="sxs-lookup"><span data-stu-id="08072-248">Transparent Data Encryption and Buffer Pool Extension</span></span>
 <span data-ttu-id="08072-249">在使用 TDE 加密数据库时不对与缓冲池扩展 (BPE) 相关的文件进行加密。</span><span class="sxs-lookup"><span data-stu-id="08072-249">Files related to buffer pool extension (BPE) are not encrypted when database is encrypted using TDE.</span></span> <span data-ttu-id="08072-250">必须对与 BPE 相关的文件使用文件系统级别的加密工具，如 Bitlocker 或 EFS。</span><span class="sxs-lookup"><span data-stu-id="08072-250">You must use file system level encryption tools like Bitlocker or EFS for BPE related files.</span></span>

## <a name="transparent-data-encryption-and-in-memory-oltp"></a><span data-ttu-id="08072-251">透明数据加密和内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="08072-251">Transparent Data Encryption and In-Memory OLTP</span></span>
 <span data-ttu-id="08072-252">可在拥有内存中 OLTP 对象的数据库上启用 TDE。</span><span class="sxs-lookup"><span data-stu-id="08072-252">TDE can be enabled on a database that has In-Memory OLTP objects.</span></span> <span data-ttu-id="08072-253">如果启用 TDE，则内存中 OLTP 日志记录会被加密。</span><span class="sxs-lookup"><span data-stu-id="08072-253">In-Memory OLTP log records are encrypted if TDE is enabled.</span></span> <span data-ttu-id="08072-254">如果启用了 TDE，则不对 MEMORY_OPTIMIZED_DATA 文件组中的数据进行加密。</span><span class="sxs-lookup"><span data-stu-id="08072-254">Data in a MEMORY_OPTIMIZED_DATA filegroup is not encrypted if TDE is enabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="08072-255">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08072-255">See Also</span></span>
 <span data-ttu-id="08072-256">[将受 TDE 保护的数据库移到另一个 SQL Server](move-a-tde-protected-database-to-another-sql-server.md) [使用 EKM 透明数据加密启用 TDE](enable-tde-on-sql-server-using-ekm.md) [和 azure sql 数据库](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md) [SQL Server 加密](sql-server-encryption.md) [SQL Server 和数据库加密密钥 &#40;](sql-server-and-database-encryption-keys-database-engine.md)数据库引擎&#41;[和 Azure SQL 数据库](../security-center-for-sql-server-database-engine-and-azure-sql-database.md) [FILESTREAM SQL Server](../../blob/filestream-sql-server.md)数据库引擎 &#40;SQL Server</span><span class="sxs-lookup"><span data-stu-id="08072-256">[Move a TDE Protected Database to Another SQL Server](move-a-tde-protected-database-to-another-sql-server.md) [Enable TDE Using EKM](enable-tde-on-sql-server-using-ekm.md) [Transparent Data Encryption with Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md) [SQL Server Encryption](sql-server-encryption.md) [SQL Server and Database Encryption Keys &#40;Database Engine&#41;](sql-server-and-database-encryption-keys-database-engine.md) [Security Center for SQL Server Database Engine and Azure SQL Database](../security-center-for-sql-server-database-engine-and-azure-sql-database.md) [FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md)</span></span>


