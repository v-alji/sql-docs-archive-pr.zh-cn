---
title: 备份服务主密钥 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], exporting
ms.assetid: f60b917c-6408-48be-b911-f93b05796904
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: b79212040df67c22ae7e34cd380a1a1f1bd10773
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693698"
---
# <a name="back-up-the-service-master-key"></a><span data-ttu-id="d6c92-102">备份服务主密钥</span><span class="sxs-lookup"><span data-stu-id="d6c92-102">Back Up the Service Master Key</span></span>
  <span data-ttu-id="d6c92-103">本主题介绍如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中备份服务主密钥。</span><span class="sxs-lookup"><span data-stu-id="d6c92-103">This topic describes how to back-up the Service Master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d6c92-104">服务主密钥是加密层次结构的根。</span><span class="sxs-lookup"><span data-stu-id="d6c92-104">The service master key is the root of the encryption hierarchy.</span></span> <span data-ttu-id="d6c92-105">应当对服务主密钥进行备份，并将其存储在另外一个安全的位置。</span><span class="sxs-lookup"><span data-stu-id="d6c92-105">It should be backed up and stored in a secure, off-site location.</span></span> <span data-ttu-id="d6c92-106">创建该备份应该是首先在服务器上执行的管理操作之一。</span><span class="sxs-lookup"><span data-stu-id="d6c92-106">Creating this backup should be one of the first administrative actions performed on the server.</span></span>  
  
 <span data-ttu-id="d6c92-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="d6c92-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d6c92-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="d6c92-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d6c92-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="d6c92-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d6c92-110">安全性</span><span class="sxs-lookup"><span data-stu-id="d6c92-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="d6c92-111">备份服务主密钥</span><span class="sxs-lookup"><span data-stu-id="d6c92-111">To back-up the Service Master key</span></span>](#Procedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d6c92-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="d6c92-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d6c92-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="d6c92-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d6c92-114">主密钥必须为打开状态，因此在备份主密钥之前应对其进行解密。</span><span class="sxs-lookup"><span data-stu-id="d6c92-114">The master key must be open and, therefore, decrypted before it is backed up.</span></span> <span data-ttu-id="d6c92-115">如果使用服务主密钥进行加密，则无需显式打开主密钥；不过，如果只使用密码对主密钥进行加密，则必须显式打开它。</span><span class="sxs-lookup"><span data-stu-id="d6c92-115">If it is encrypted with the service master key, the master key does not have to be explicitly opened; however, if the master key is encrypted only with a password, it must be explicitly opened.</span></span>  
  
-   <span data-ttu-id="d6c92-116">我们建议您在创建主密钥之后立即对其进行备份，并存储于另外一个安全的位置中。</span><span class="sxs-lookup"><span data-stu-id="d6c92-116">We recommend that you back up the master key as soon as it is created, and store the backup in a secure, off-site location.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d6c92-117">Security</span><span class="sxs-lookup"><span data-stu-id="d6c92-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d6c92-118">权限</span><span class="sxs-lookup"><span data-stu-id="d6c92-118">Permissions</span></span>  
 <span data-ttu-id="d6c92-119">要求对数据库具有 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="d6c92-119">Requires CONTROL permission on the database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="Procedure"></a> <span data-ttu-id="d6c92-120">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d6c92-120">Using Transact-SQL</span></span>  
  
#### <a name="to-back-up-the-service-master-key"></a><span data-ttu-id="d6c92-121">备份服务主密钥</span><span class="sxs-lookup"><span data-stu-id="d6c92-121">To back-up the Service Master key</span></span>  
  
1.  <span data-ttu-id="d6c92-122">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，连接到包含需要备份的服务主密钥的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="d6c92-122">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance containing the service master key you wish to back up.</span></span>  
  
2.  <span data-ttu-id="d6c92-123">选择要用于在备份介质上加密服务主密钥的密码。</span><span class="sxs-lookup"><span data-stu-id="d6c92-123">Choose a password that will be used to encrypt the service master key on the backup medium.</span></span> <span data-ttu-id="d6c92-124">此密码应通过复杂性检查。</span><span class="sxs-lookup"><span data-stu-id="d6c92-124">This password is subject to complexity checks.</span></span> <span data-ttu-id="d6c92-125">有关详细信息，请参阅 [Password Policy](../password-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="d6c92-125">For more information, see [Password Policy](../password-policy.md).</span></span>  
  
3.  <span data-ttu-id="d6c92-126">获得一个用于存储密钥备份副本的可移动备份介质。</span><span class="sxs-lookup"><span data-stu-id="d6c92-126">Obtain a removable backup medium for storing a copy of the backed-up key.</span></span>  
  
4.  <span data-ttu-id="d6c92-127">确定将在其下创建密钥备份的 NTFS 目录。</span><span class="sxs-lookup"><span data-stu-id="d6c92-127">Identify an NTFS directory in which to create the backup of the key.</span></span> <span data-ttu-id="d6c92-128">这就是在下一步中指定的要创建文件的位置。</span><span class="sxs-lookup"><span data-stu-id="d6c92-128">This is where you will create the file specified in the next step.</span></span> <span data-ttu-id="d6c92-129">应使用高限制级访问控制列表 (ACL) 来保护目录。</span><span class="sxs-lookup"><span data-stu-id="d6c92-129">The directory should be protected with highly restrictive access control lists (ACLs).</span></span>  
  
5.  <span data-ttu-id="d6c92-130">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="d6c92-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
6.  <span data-ttu-id="d6c92-131">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="d6c92-131">On the Standard bar, click **New Query**.</span></span>  
  
7.  <span data-ttu-id="d6c92-132">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="d6c92-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key.  
    -- Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;  
    GO  
    BACKUP SERVICE MASTER KEY TO FILE = 'c:\temp_backups\keys\service_master_ key'   
        ENCRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6c92-133">指向密钥和密钥的密码（如果有）的文件路径不同于以上所指示的路径。</span><span class="sxs-lookup"><span data-stu-id="d6c92-133">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="d6c92-134">确保这两个路径都是针对您的服务器和密钥设置的。</span><span class="sxs-lookup"><span data-stu-id="d6c92-134">Make sure that both are specific to your server and key set-up.</span></span>  
  
8.  <span data-ttu-id="d6c92-135">将文件复制到备份介质上并验证该副本是否完好。</span><span class="sxs-lookup"><span data-stu-id="d6c92-135">Copy the file to the backup medium and verify the copy.</span></span>  
  
9. <span data-ttu-id="d6c92-136">将备份存储在另外一个安全的位置。</span><span class="sxs-lookup"><span data-stu-id="d6c92-136">Store the backup in a secure, off-site location.</span></span>  
  
 <span data-ttu-id="d6c92-137">有关详细信息，请参阅 [OPEN MASTER KEY (Transact-SQL)](/sql/t-sql/statements/open-master-key-transact-sql) 和 [BACKUP MASTER KEY (Transact-SQL)](/sql/t-sql/statements/backup-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d6c92-137">For more information, see [OPEN MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql) and [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).</span></span>  
  
  
