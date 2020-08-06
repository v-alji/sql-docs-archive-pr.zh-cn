---
title: 还原数据库主密钥 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], importing
ms.assetid: 16897cc5-db8f-43bb-a38e-6855c82647cf
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 614ba8bdc494ae7e7e5b3ed7b62390721ef642a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694420"
---
# <a name="restore-a-database-master-key"></a><span data-ttu-id="44484-102">还原数据库主密钥</span><span class="sxs-lookup"><span data-stu-id="44484-102">Restore a Database Master Key</span></span>
  <span data-ttu-id="44484-103">本主题介绍如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中还原数据库主密钥。</span><span class="sxs-lookup"><span data-stu-id="44484-103">This topic describes how to restore the database master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="44484-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="44484-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="44484-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="44484-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="44484-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="44484-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="44484-107">安全性</span><span class="sxs-lookup"><span data-stu-id="44484-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="44484-108">使用 Transact-SQL 还原数据库主密钥</span><span class="sxs-lookup"><span data-stu-id="44484-108">To restore the database master key using Transact-SQL</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="44484-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="44484-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="44484-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="44484-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="44484-111">还原主密钥之后， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 会对使用当前活动的主密钥加密的所有密钥进行解密，然后使用还原后的主密钥对这些密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="44484-111">When the master key is restored, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] decrypts all the keys that are encrypted with the currently active master key, and then encrypts these keys with the restored master key.</span></span> <span data-ttu-id="44484-112">这种大量消耗资源的操作应当安排在资源需求较低的时段执行。</span><span class="sxs-lookup"><span data-stu-id="44484-112">This resource-intensive operation should be scheduled during a period of low demand.</span></span> <span data-ttu-id="44484-113">如果当前的数据库主密钥未打开或无法打开，或者无法对任何使用该主密钥加密的密钥进行解密，则还原操作将失败。</span><span class="sxs-lookup"><span data-stu-id="44484-113">If the current database master key is not open or cannot be opened, or if any of the keys that are encrypted by it cannot be decrypted, the restore operation fails.</span></span>  
  
-   <span data-ttu-id="44484-114">如果有任意一种解密操作失败，则还原操作将会失败。</span><span class="sxs-lookup"><span data-stu-id="44484-114">If any one of the decryptions fails, the restore will fail.</span></span> <span data-ttu-id="44484-115">您可以使用 FORCE 选项忽略错误，但是该选项会使无法进行解密的数据丢失。</span><span class="sxs-lookup"><span data-stu-id="44484-115">You can use the FORCE option to ignore errors, but this option will cause the loss of any data that cannot be decrypted.</span></span>  
  
-   <span data-ttu-id="44484-116">如果主密钥通过服务主密钥进行加密，则还原后的主密钥也通过该服务主密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="44484-116">If the master key was encrypted by the service master key, the restored master key will also be encrypted by the service master key.</span></span>  
  
-   <span data-ttu-id="44484-117">如果当前数据库中没有主密钥，则 RESTORE MASTER KEY 将创建一个主密钥。</span><span class="sxs-lookup"><span data-stu-id="44484-117">If there is no master key in the current database, RESTORE MASTER KEY creates a master key.</span></span> <span data-ttu-id="44484-118">新的主密钥不会自动使用服务主密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="44484-118">The new master key will not be automatically encrypted with the service master key.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="44484-119">Security</span><span class="sxs-lookup"><span data-stu-id="44484-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="44484-120">权限</span><span class="sxs-lookup"><span data-stu-id="44484-120">Permissions</span></span>  
 <span data-ttu-id="44484-121">要求对数据库具有 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="44484-121">Requires CONTROL permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio-with-transact-sql"></a><a name="SSMSProcedure"></a><span data-ttu-id="44484-122">将 SQL Server Management Studio 与 Transact-sql 一起使用</span><span class="sxs-lookup"><span data-stu-id="44484-122">Using SQL Server Management Studio with Transact-SQL</span></span>  
  
#### <a name="to-restore-the-database-master-key"></a><span data-ttu-id="44484-123">还原数据库主密钥</span><span class="sxs-lookup"><span data-stu-id="44484-123">To restore the database master key</span></span>  
  
1.  <span data-ttu-id="44484-124">从物理备份介质或本地文件系统上的某个目录检索备份的数据库主密钥的副本。</span><span class="sxs-lookup"><span data-stu-id="44484-124">Retrieve a copy of the backed-up database master key, either from a physical backup medium or a directory on the local file system.</span></span>  
  
2.  <span data-ttu-id="44484-125">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="44484-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
3.  <span data-ttu-id="44484-126">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="44484-126">On the Standard bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="44484-127">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="44484-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Restores the database master key of the AdventureWorks2012 database.  
    USE AdventureWorks2012;  
    GO  
    RESTORE MASTER KEY   
        FROM FILE = 'c:\backups\keys\AdventureWorks2012_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003#GHkf02597gheij04'   
        ENCRYPTION BY PASSWORD = '259087M#MyjkFkjhywiyedfgGDFD';  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="44484-128">指向密钥和密钥的密码（如果有）的文件路径不同于以上所指示的路径。</span><span class="sxs-lookup"><span data-stu-id="44484-128">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="44484-129">请确保这两个路径都是针对您的服务器和密钥设置的。</span><span class="sxs-lookup"><span data-stu-id="44484-129">Please make sure that both are specific to your server and key set-up.</span></span>  
  
 <span data-ttu-id="44484-130">有关详细信息，请参阅 [RESTORE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/restore-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="44484-130">For more information, see [RESTORE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-master-key-transact-sql)</span></span>  
  
  
