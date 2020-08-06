---
title: 使用 (SQL Server Management Studio) 的事务发布的备份启用初始化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f5e22614c8c4f5250db3966e747b686091512774
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578099"
---
# <a name="enable-initialization-with-a-backup-for-transactional-publications-sql-server-management-studio"></a><span data-ttu-id="16a8e-102">使用备份来初始化事务发布 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="16a8e-102">Enable Initialization with a Backup for Transactional Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="16a8e-103">若要使用备份初始化对事务发布的订阅，请启用发布以允许使用备份进行初始化，然后指定创建订阅时的备份信息：</span><span class="sxs-lookup"><span data-stu-id="16a8e-103">To initialize a subscription to a transactional publication from a backup, enable the publication to allow initialization from a backup, and then specify backup information when creating the subscription:</span></span>  
  
-   <span data-ttu-id="16a8e-104">在“发布属性 - \<Publication>”对话框的“订阅选项”页中启用发布。 </span><span class="sxs-lookup"><span data-stu-id="16a8e-104">Enable the publication on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="16a8e-105">有关访问此对话框的详细信息，请参阅 [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="16a8e-105">For more information about accessing this dialog box, see [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).</span></span>  
  
-   <span data-ttu-id="16a8e-106">使用存储过程 [sp_addsubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) 指定备份信息。</span><span class="sxs-lookup"><span data-stu-id="16a8e-106">Specify backup information with the stored procedure [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="16a8e-107">有关 **sp_addsubscription** 所需的参数的详细信息，请参阅[使用备份初始化事务订阅（复制 Transact-SQL 编程）](initialize-a-transactional-subscription-from-a-backup.md)。</span><span class="sxs-lookup"><span data-stu-id="16a8e-107">For more information about the parameters required by **sp_addsubscription**, see [Initialize a Transactional Subscription from a Backup &#40;Replication Transact-SQL Programming&#41;](initialize-a-transactional-subscription-from-a-backup.md).</span></span>  
  
### <a name="to-enable-initialization-with-a-backup"></a><span data-ttu-id="16a8e-108">启用使用备份来初始化</span><span class="sxs-lookup"><span data-stu-id="16a8e-108">To enable initialization with a backup</span></span>  
  
1.  <span data-ttu-id="16a8e-109">在“发布属性 - \<Publication>”对话框的“订阅选项”页上，为“允许从备份文件初始化”选项选择“True”值。   </span><span class="sxs-lookup"><span data-stu-id="16a8e-109">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select a value of **True** for the **Allow initialization from backup files** option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16a8e-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="16a8e-110">See Also</span></span>  
 [<span data-ttu-id="16a8e-111">初始化事务订阅（不使用快照）</span><span class="sxs-lookup"><span data-stu-id="16a8e-111">Initialize a Transactional Subscription Without a Snapshot</span></span>](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
