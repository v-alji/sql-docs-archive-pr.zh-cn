---
title: 在简单恢复模式下还原数据库备份 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- database restores [SQL Server], full backups
- backing up databases [SQL Server], full backups
- database backups [SQL Server], full backups
- restoring databases [SQL Server], full backups
ms.assetid: a928fa36-e285-476f-9a7b-6840a8bb7283
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e264dd380c3dff40dacc4eb576d34af5195dec01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688954"
---
# <a name="restore-a-database-backup-under-the-simple-recovery-model-transact-sql"></a><span data-ttu-id="27ea7-102">在简单恢复模式下还原数据库备份 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="27ea7-102">Restore a Database Backup Under the Simple Recovery Model (Transact-SQL)</span></span>
  <span data-ttu-id="27ea7-103">本主题说明如何还原完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="27ea7-103">This topic explains how to restore a full database backup.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="27ea7-104">还原完整数据库备份的系统管理员必须是当前使用要还原的数据库的唯一人员。</span><span class="sxs-lookup"><span data-stu-id="27ea7-104">The system administrator restoring the full database backup must be the only person currently using the database to be restored.</span></span>  
  
## <a name="prerequisites-and-recommendations"></a><span data-ttu-id="27ea7-105">先决条件和建议</span><span class="sxs-lookup"><span data-stu-id="27ea7-105">Prerequisites and Recommendations</span></span>  
  
-   <span data-ttu-id="27ea7-106">若要还原已加密的数据库，您必须有权访问用于对数据库进行加密的证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="27ea7-106">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="27ea7-107">如果没有证书或非对称密钥，数据库将无法还原。</span><span class="sxs-lookup"><span data-stu-id="27ea7-107">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="27ea7-108">因此，只要需要该备份，就必须保留用于对数据库加密密钥进行加密的证书。</span><span class="sxs-lookup"><span data-stu-id="27ea7-108">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="27ea7-109">有关详细信息，请参阅 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="27ea7-109">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
-   <span data-ttu-id="27ea7-110">出于安全性考虑，我们建议您不要从未知或不信任的源附加或还原数据库。</span><span class="sxs-lookup"><span data-stu-id="27ea7-110">For security purposes, we recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="27ea7-111">此类数据库可能包含恶意代码，这些代码可能会执行非预期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码，或者通过修改架构或物理数据库结构导致错误。</span><span class="sxs-lookup"><span data-stu-id="27ea7-111">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="27ea7-112">使用来自未知源或不可信源的数据库前，请在非生产服务器上针对数据库运行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，然后检查数据库中的代码，例如存储过程或其他用户定义代码。</span><span class="sxs-lookup"><span data-stu-id="27ea7-112">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
## <a name="database-compatibility-level-after-upgrade"></a><span data-ttu-id="27ea7-113">升级后的数据库兼容级别</span><span class="sxs-lookup"><span data-stu-id="27ea7-113">Database Compatibility Level After Upgrade</span></span>  
 <span data-ttu-id="27ea7-114">升级后， **tempdb**、 **model**、 **msdb** 和 **Resource** 数据库的兼容级别将设置为 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="27ea7-114">The compatibility levels of the **tempdb**, **model**, **msdb** and **Resource** databases are set to the compatibility level of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] after upgrade.</span></span> <span data-ttu-id="27ea7-115">**master** 系统数据库保留它在升级之前的兼容级别，除非该级别小于 100。</span><span class="sxs-lookup"><span data-stu-id="27ea7-115">The **master** system database retains the compatibility level it had before upgrade, unless that level was less than 100.</span></span> <span data-ttu-id="27ea7-116">如果 **master** 的兼容级别在升级前小于 100，升级后兼容级别将设置为 100。</span><span class="sxs-lookup"><span data-stu-id="27ea7-116">If the compatibility level of **master** was less than 100 before upgrade, it is set to 100 after upgrade.</span></span>  
  
 <span data-ttu-id="27ea7-117">如果升级前用户数据库的兼容级别为 100 或更高，升级后将保持相应级别。</span><span class="sxs-lookup"><span data-stu-id="27ea7-117">If the compatibility level of a user database was 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="27ea7-118">如果升级前兼容级别为 90，则在升级后的数据库中，兼容级别将设置为 100，该级别为 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]支持的最低兼容级别。</span><span class="sxs-lookup"><span data-stu-id="27ea7-118">If the compatibility level was 90 before upgrade, in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27ea7-119">新的用户数据库将继承 **model** 数据库的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="27ea7-119">New user databases will inherit the compatibility level of the **model** database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="27ea7-120">过程</span><span class="sxs-lookup"><span data-stu-id="27ea7-120">Procedures</span></span>  
  
#### <a name="to-restore-a-full-database-backup"></a><span data-ttu-id="27ea7-121">还原完整数据库备份</span><span class="sxs-lookup"><span data-stu-id="27ea7-121">To restore a full database backup</span></span>  
  
1.  <span data-ttu-id="27ea7-122">执行 RESTORE DATABASE 语句可以还原完整数据库备份，同时指定：</span><span class="sxs-lookup"><span data-stu-id="27ea7-122">Execute the RESTORE DATABASE statement to restore the full database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="27ea7-123">要还原的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="27ea7-123">The name of the database to restore.</span></span>  
  
    -   <span data-ttu-id="27ea7-124">从中还原完整数据库备份的备份设备。</span><span class="sxs-lookup"><span data-stu-id="27ea7-124">The backup device from where the full database backup is restored.</span></span>  
  
    -   <span data-ttu-id="27ea7-125">NORECOVERY 子句，前提是在还原完整数据库备份之后，还要应用事务日志备份或差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="27ea7-125">The NORECOVERY clause if you have a transaction log or differential database backup to apply after restoring the full database backup.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="27ea7-126">若要还原已加密的数据库，您必须有权访问用于对数据库进行加密的证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="27ea7-126">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="27ea7-127">如果没有证书或非对称密钥，数据库将无法还原。</span><span class="sxs-lookup"><span data-stu-id="27ea7-127">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="27ea7-128">因此，只要需要该备份，就必须保留用于对数据库加密密钥进行加密的证书。</span><span class="sxs-lookup"><span data-stu-id="27ea7-128">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="27ea7-129">有关详细信息，请参阅 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="27ea7-129">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
2.  <span data-ttu-id="27ea7-130">可以选择指定：</span><span class="sxs-lookup"><span data-stu-id="27ea7-130">Optionally, specify:</span></span>  
  
    -   <span data-ttu-id="27ea7-131">FILE 子句，以此标识备份设备上要还原的备份集。</span><span class="sxs-lookup"><span data-stu-id="27ea7-131">The FILE clause to identify the backup set on the backup device to restore.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27ea7-132">如果将早期版本的数据库还原到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]，将自动升级该数据库。</span><span class="sxs-lookup"><span data-stu-id="27ea7-132">If you restore an earlier version database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database is automatically upgraded.</span></span> <span data-ttu-id="27ea7-133">通常，该数据库将立即可用。</span><span class="sxs-lookup"><span data-stu-id="27ea7-133">Typically, the database becomes available immediately.</span></span> <span data-ttu-id="27ea7-134">但是，如果 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 数据库具有全文检索，则升级过程将导入、重置或重新生成它们，具体取决于  **upgrade_option** 服务器属性的设置。</span><span class="sxs-lookup"><span data-stu-id="27ea7-134">However, if a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the  **upgrade_option** server property.</span></span> <span data-ttu-id="27ea7-135">如果将升级选项设置为“导入”(**upgrade_option** = 2) 或“重新生成”(**upgrade_option** = 0)，在升级过程中将无法使用全文检索。</span><span class="sxs-lookup"><span data-stu-id="27ea7-135">If the upgrade option is set to import (**upgrade_option** = 2) or rebuild (**upgrade_option** = 0), the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="27ea7-136">导入可能需要数小时，而重新生成所需的时间最多时可能十倍于此，具体取决于要编制索引的数据量。</span><span class="sxs-lookup"><span data-stu-id="27ea7-136">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="27ea7-137">另请注意，如果将升级选项设置为“导入”，并且全文目录不可用，则会重新生成关联的全文索引。</span><span class="sxs-lookup"><span data-stu-id="27ea7-137">Note also that when the upgrade option is set to import, the associated full-text indexes are rebuilt if a full-text catalog is not available.</span></span> <span data-ttu-id="27ea7-138">若要更改 **upgrade_option** 服务器属性的设置，请使用 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="27ea7-138">To change the setting of the **upgrade_option** server property, use [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27ea7-139">示例</span><span class="sxs-lookup"><span data-stu-id="27ea7-139">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="27ea7-140">说明</span><span class="sxs-lookup"><span data-stu-id="27ea7-140">Description</span></span>  
 <span data-ttu-id="27ea7-141">以下示例从磁带中还原 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 的完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="27ea7-141">This example restores the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] full database backup from tape.</span></span>  
  
### <a name="example"></a><span data-ttu-id="27ea7-142">示例</span><span class="sxs-lookup"><span data-stu-id="27ea7-142">Example</span></span>  
  
```  
USE master;  
GO  
RESTORE DATABASE AdventureWorks2012  
   FROM TAPE = '\\.\Tape0';  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="27ea7-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27ea7-143">See Also</span></span>  
 <span data-ttu-id="27ea7-144">[完整数据库还原（完整恢复模式）](complete-database-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="27ea7-144">[Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="27ea7-145">[完整数据库还原（简单恢复模式）](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="27ea7-145">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="27ea7-146">[完整数据库备份 (SQL Server)](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="27ea7-146">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="27ea7-147">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="27ea7-147">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="27ea7-148">[备份历史记录和标头信息 (SQL Server)](backup-history-and-header-information-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="27ea7-148">[Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) </span></span>  
 [<span data-ttu-id="27ea7-149">重新生成系统数据库</span><span class="sxs-lookup"><span data-stu-id="27ea7-149">Rebuild System Databases</span></span>](../databases/system-databases.md)  
  
  
