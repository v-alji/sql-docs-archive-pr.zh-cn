---
title: SQL Server) 的 AlwaysOn 可用性组 (加密的数据库 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption, AlwaysOn Availability Groups
- TDE, AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 09eb6ebc-3051-4fff-86a5-93524507b1fc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 91e717a896634a7df5a96253c51207831f142cff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578441"
---
# <a name="encrypted-databases-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="e2bac-102">加密的数据库与 AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e2bac-102">Encrypted Databases with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="e2bac-103">本主题包含有关在 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中将当前加密或最近解密的数据库与 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]一起使用的信息。</span><span class="sxs-lookup"><span data-stu-id="e2bac-103">This topic contains information about the using currently encrypted or recently decrypted databases with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="e2bac-104">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="e2bac-104">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="e2bac-105">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e2bac-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="e2bac-106">相关任务</span><span class="sxs-lookup"><span data-stu-id="e2bac-106">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e2bac-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e2bac-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e2bac-108">如果数据库进行了加密或者数据库甚至包含数据库加密密钥 (DEK)，则您无法使用 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 或 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 将该数据库添加到某一可用性组。</span><span class="sxs-lookup"><span data-stu-id="e2bac-108">If a database is encrypted or even contains a Database Encryption Key (DEK), you cannot use the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] to add the database to an availability group.</span></span> <span data-ttu-id="e2bac-109">即使已对加密的数据库进行了解密，其日志备份也可能包含加密的数据。</span><span class="sxs-lookup"><span data-stu-id="e2bac-109">Even if an encrypted database has been decrypted, its log backups might contain encrypted data.</span></span> <span data-ttu-id="e2bac-110">在此情况下，在该数据库上完整的初始数据同步可能会失败。</span><span class="sxs-lookup"><span data-stu-id="e2bac-110">In this case, full initial data synchronization could fail on the database.</span></span> <span data-ttu-id="e2bac-111">其原因在于，还原日志操作可能要求数据库加密密钥 (DEK) 使用的证书，但该证书可能不可用。</span><span class="sxs-lookup"><span data-stu-id="e2bac-111">This is because the restore log operation might require the certificate that was used by the database encryption keys (DEKs), and that certificate might be unavailable.</span></span>  
  
     <span data-ttu-id="e2bac-112">为使解密的数据库可添加到某一可用性组，请使用向导：</span><span class="sxs-lookup"><span data-stu-id="e2bac-112">To make a decrypted database eligible to add to an availability group using the wizard:</span></span>  
  
    1.  <span data-ttu-id="e2bac-113">创建主数据库的日志备份。</span><span class="sxs-lookup"><span data-stu-id="e2bac-113">Create a log backup of the primary database.</span></span>  
  
    2.  <span data-ttu-id="e2bac-114">创建主数据库的完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="e2bac-114">Create a full database backup of the primary database.</span></span>  
  
    3.  <span data-ttu-id="e2bac-115">在承载辅助副本的服务器实例上，还原数据库备份。</span><span class="sxs-lookup"><span data-stu-id="e2bac-115">Restore the database backup on the server instance that hosts the secondary replica.</span></span>  
  
    4.  <span data-ttu-id="e2bac-116">从主数据库创建新的日志备份。</span><span class="sxs-lookup"><span data-stu-id="e2bac-116">Create a new log backup from primary database.</span></span>  
  
    5.  <span data-ttu-id="e2bac-117">在辅助数据库上还原此日志备份。</span><span class="sxs-lookup"><span data-stu-id="e2bac-117">Restore this log backup on the secondary database.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e2bac-118">相关任务</span><span class="sxs-lookup"><span data-stu-id="e2bac-118">Related Tasks</span></span>  
  
-   [<span data-ttu-id="e2bac-119">为可用性组手动准备辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e2bac-119">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="e2bac-120">使用可用性组向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e2bac-120">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="e2bac-121">使用“将数据库添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e2bac-121">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="e2bac-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2bac-122">See Also</span></span>  
 <span data-ttu-id="e2bac-123">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e2bac-123">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="e2bac-124">透明数据加密 (TDE)</span><span class="sxs-lookup"><span data-stu-id="e2bac-124">Transparent Data Encryption &#40;TDE&#41;</span></span>](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
  
