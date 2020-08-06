---
title: 备份数据库主密钥 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], exporting
ms.assetid: 7ad9a0a0-6e4f-4f7b-8801-8c1b9d49c4d8
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 9a66d28fea8289719d3efb2351409e0f14379ec9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693701"
---
# <a name="back-up-a-database-master-key"></a><span data-ttu-id="cdd3c-102">备份数据库主密钥</span><span class="sxs-lookup"><span data-stu-id="cdd3c-102">Back Up a Database Master Key</span></span>
  <span data-ttu-id="cdd3c-103">本主题介绍如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中备份数据库主密钥。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-103">This topic describes how to back up a database master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cdd3c-104">数据库主密钥用于加密数据库里面的其他密钥和证书。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-104">The database master key is used to encrypt other keys and certificates inside a database.</span></span> <span data-ttu-id="cdd3c-105">如果主密钥被删除或损坏，则 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可能无法解密数据库里面的其他密钥，并且使用这些密钥加密的数据就如同丢失一样。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-105">If it is deleted or corrupted, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] may be unable to decrypt those keys, and the data encrypted using them will be effectively lost.</span></span> <span data-ttu-id="cdd3c-106">出于这个原因，您应备份数据库主密钥，并将备份存储在另外一个安全的位置。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-106">For this reason, you should back up the database master key and store the backup in a secure off-site location.</span></span>  
  
 <span data-ttu-id="cdd3c-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="cdd3c-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cdd3c-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="cdd3c-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cdd3c-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="cdd3c-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="cdd3c-110">安全性</span><span class="sxs-lookup"><span data-stu-id="cdd3c-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="cdd3c-111">使用 Transact-SQL 备份数据库主密钥</span><span class="sxs-lookup"><span data-stu-id="cdd3c-111">To back up a database master key using Transact-SQL</span></span>](#Procedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cdd3c-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="cdd3c-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="cdd3c-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="cdd3c-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="cdd3c-114">主密钥必须为打开状态，因此在备份主密钥之前应对其进行解密。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-114">The master key must be open and, therefore, decrypted before it is backed up.</span></span> <span data-ttu-id="cdd3c-115">如果主密钥使用服务主密钥进行加密，则不必显式打开。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-115">If it is encrypted with the service master key, the master key does not have to be explicitly opened.</span></span> <span data-ttu-id="cdd3c-116">但如果主密钥仅使用密码进行加密，则必须显式打开。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-116">But if the master key is encrypted only with a password, it must be explicitly opened.</span></span>  
  
-   <span data-ttu-id="cdd3c-117">我们建议您在创建主密钥之后立即对其进行备份，并存储于另外一个安全的位置中。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-117">We recommend that you back up the master key as soon as it is created, and store the backup in a secure, off-site location.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cdd3c-118">Security</span><span class="sxs-lookup"><span data-stu-id="cdd3c-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cdd3c-119">权限</span><span class="sxs-lookup"><span data-stu-id="cdd3c-119">Permissions</span></span>  
 <span data-ttu-id="cdd3c-120">要求对数据库具有 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-120">Requires CONTROL permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio-with-transact-sql"></a><a name="Procedure"></a><span data-ttu-id="cdd3c-121">将 SQL Server Management Studio 与 Transact-sql 一起使用</span><span class="sxs-lookup"><span data-stu-id="cdd3c-121">Using SQL Server Management Studio with Transact-SQL</span></span>  
  
#### <a name="to-back-up-the-database-master-key"></a><span data-ttu-id="cdd3c-122">备份数据库主密钥</span><span class="sxs-lookup"><span data-stu-id="cdd3c-122">To back-up the database master key</span></span>  
  
1.  <span data-ttu-id="cdd3c-123">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，连接到包含需要备份的数据库主密钥的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-123">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance containing the database master key you wish to back up.</span></span>  
  
2.  <span data-ttu-id="cdd3c-124">选择将用于在备份介质上加密数据库主密钥的密码。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-124">Choose a password that will be used to encrypt the database master key on the backup medium.</span></span> <span data-ttu-id="cdd3c-125">此密码应通过复杂性检查。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-125">This password is subject to complexity checks.</span></span>  
  
3.  <span data-ttu-id="cdd3c-126">获得一个用于存储密钥备份副本的可移动备份介质。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-126">Obtain a removable backup medium for storing a copy of the backed-up key.</span></span>  
  
4.  <span data-ttu-id="cdd3c-127">确定将在其下创建密钥备份的 NTFS 目录。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-127">Identify an NTFS directory in which to create the backup of the key.</span></span> <span data-ttu-id="cdd3c-128">这就是在下一步中指定的要创建文件的位置。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-128">This is where you will create the file specified in the next step.</span></span> <span data-ttu-id="cdd3c-129">应使用高限制级访问控制列表 (ACL) 来保护目录。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-129">The directory should be protected with highly restrictive access control lists (ACLs).</span></span>  
  
5.  <span data-ttu-id="cdd3c-130">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
6.  <span data-ttu-id="cdd3c-131">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-131">On the Standard bar, click **New Query**.</span></span>  
  
7.  <span data-ttu-id="cdd3c-132">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key. Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;   
    GO  
    OPEN MASTER KEY DECRYPTION BY PASSWORD = 'sfj5300osdVdgwdfkli7';   
  
    BACKUP MASTER KEY TO FILE = 'c:\temp\exportedmasterkey'   
        ENCRYPTION BY PASSWORD = 'sd092735kjn$&adsg';   
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="cdd3c-133">指向密钥和密钥的密码（如果有）的文件路径不同于以上所指示的路径。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-133">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="cdd3c-134">请确保这两个路径都是针对您的服务器和密钥设置的。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-134">Please make sure that both are specific to your server and key set-up.</span></span>  
  
8.  <span data-ttu-id="cdd3c-135">将文件复制到备份介质上并验证该副本是否完好。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-135">Copy the file to the backup medium and verify the copy.</span></span>  
  
9. <span data-ttu-id="cdd3c-136">将备份存储在另外一个安全的位置。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-136">Store the backup in a secure, off-site location.</span></span>  
  
 <span data-ttu-id="cdd3c-137">有关详细信息，请参阅 [OPEN MASTER KEY (Transact-SQL)](/sql/t-sql/statements/open-master-key-transact-sql) 和 [BACKUP MASTER KEY (Transact-SQL)](/sql/t-sql/statements/backup-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cdd3c-137">For more information, see [OPEN MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql) and [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).</span></span>  
  
  
