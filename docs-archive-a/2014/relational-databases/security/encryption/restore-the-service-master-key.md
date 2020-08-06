---
title: 还原服务主密钥 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], importing
- service master key [SQL Server], restoring
ms.assetid: 14bdbbbe-d384-4692-b670-4243d2466fe1
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 2ad99fc9baa518d50678ddd6e6db1ec554658823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694421"
---
# <a name="restore-the-service-master-key"></a><span data-ttu-id="eacf0-102">还原服务主密钥</span><span class="sxs-lookup"><span data-stu-id="eacf0-102">Restore the Service Master Key</span></span>
  <span data-ttu-id="eacf0-103">本主题介绍如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中还原服务主密钥。</span><span class="sxs-lookup"><span data-stu-id="eacf0-103">This topic describes how to restore the service master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="eacf0-104">您可能永远也不需要还原服务主密钥。</span><span class="sxs-lookup"><span data-stu-id="eacf0-104">It is unlikely that you will ever need to restore the service master key.</span></span> <span data-ttu-id="eacf0-105">但如果进行此操作，应当格外谨慎。</span><span class="sxs-lookup"><span data-stu-id="eacf0-105">If you do, you should proceed with extreme caution.</span></span> <span data-ttu-id="eacf0-106">有关详细信息，请参阅 [Back Up the Service Master Key](service-master-key.md)。</span><span class="sxs-lookup"><span data-stu-id="eacf0-106">For more information, see [Back Up the Service Master Key](service-master-key.md).</span></span>  
  
 <span data-ttu-id="eacf0-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="eacf0-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="eacf0-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="eacf0-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="eacf0-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="eacf0-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="eacf0-110">安全性</span><span class="sxs-lookup"><span data-stu-id="eacf0-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="eacf0-111">使用 Transact-SQL 还原服务主密钥</span><span class="sxs-lookup"><span data-stu-id="eacf0-111">To restore the service master key using Transact-SQL</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eacf0-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="eacf0-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="eacf0-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="eacf0-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="eacf0-114">当还原服务主密钥时， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将对所有已使用当前服务主密钥加密的密钥和机密内容进行解密，然后使用从备份文件中加载的服务主密钥对这些密钥和机密内容进行加密。</span><span class="sxs-lookup"><span data-stu-id="eacf0-114">When the service master key is restored, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] decrypts all the keys and secrets that have been encrypted with the current service master key, and then encrypts them with the service master key loaded from the backup file.</span></span>  
  
-   <span data-ttu-id="eacf0-115">如果有任意一种解密操作失败，则还原操作将会失败。</span><span class="sxs-lookup"><span data-stu-id="eacf0-115">If any one of the decryptions fails, the restore will fail.</span></span> <span data-ttu-id="eacf0-116">您可以使用 FORCE 选项忽略错误，但是该选项会使无法进行解密的数据丢失。</span><span class="sxs-lookup"><span data-stu-id="eacf0-116">You can use the FORCE option to ignore errors, but this option will cause the loss of any data that cannot be decrypted.</span></span>  
  
-   <span data-ttu-id="eacf0-117">重新生成加密层次结构是一种消耗大量资源的操作。</span><span class="sxs-lookup"><span data-stu-id="eacf0-117">Regenerating the encryption hierarchy is a resource-intensive operation.</span></span> <span data-ttu-id="eacf0-118">您应当将该操作安排在资源需求较低的时段进行。</span><span class="sxs-lookup"><span data-stu-id="eacf0-118">You should schedule this during a period of low demand.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="eacf0-119">服务主密钥为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密层次结构的根。</span><span class="sxs-lookup"><span data-stu-id="eacf0-119">The service master key is the root of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption hierarchy.</span></span> <span data-ttu-id="eacf0-120">服务主密钥直接或间接地保护树中的所有其他密钥。</span><span class="sxs-lookup"><span data-stu-id="eacf0-120">The service master key directly or indirectly secures all other keys in the tree.</span></span> <span data-ttu-id="eacf0-121">如果在强制的还原过程中不能对某个相关密钥进行解密，则由该密钥所保护的数据便会丢失。</span><span class="sxs-lookup"><span data-stu-id="eacf0-121">If a dependent key cannot be decrypted during a forced restore, data that is secured by that key will be lost.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eacf0-122">Security</span><span class="sxs-lookup"><span data-stu-id="eacf0-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="eacf0-123">权限</span><span class="sxs-lookup"><span data-stu-id="eacf0-123">Permissions</span></span>  
 <span data-ttu-id="eacf0-124">需要对服务器的 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="eacf0-124">Requires CONTROL SERVER permission on the server.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="SSMSProcedure"></a> <span data-ttu-id="eacf0-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eacf0-125">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-the-service-master-key"></a><span data-ttu-id="eacf0-126">还原服务主密钥</span><span class="sxs-lookup"><span data-stu-id="eacf0-126">To restore the service master key</span></span>  
  
1.  <span data-ttu-id="eacf0-127">从物理备份介质或本地文件系统上的某个目录检索备份的服务主密钥的副本。</span><span class="sxs-lookup"><span data-stu-id="eacf0-127">Retrieve a copy of the backed-up service master key, either from a physical backup medium or a directory on the local file system.</span></span>  
  
2.  <span data-ttu-id="eacf0-128">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="eacf0-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
3.  <span data-ttu-id="eacf0-129">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="eacf0-129">On the Standard bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="eacf0-130">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="eacf0-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Restores the service master key from a backup file.  
    RESTORE SERVICE MASTER KEY   
        FROM FILE = 'c:\temp_backups\keys\service_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="eacf0-131">指向密钥和密钥的密码（如果有）的文件路径不同于以上所指示的路径。</span><span class="sxs-lookup"><span data-stu-id="eacf0-131">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="eacf0-132">请确保这两个路径都是针对您的服务器和密钥设置的。</span><span class="sxs-lookup"><span data-stu-id="eacf0-132">Please make sure that both are specific to your server and key set-up.</span></span>  
  
  
