---
title: 配置和管理加密密钥（SSRS 配置管理器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- encryption keys [Reporting Services]
- private keys [Reporting Services]
- cryptography [Reporting Services]
- symmetric keys [Reporting Services]
- encryption [Reporting Services]
- public keys [Reporting Services]
ms.assetid: 58e61636-88a2-4338-ae5f-3dd210aee887
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: afe9edff22c67b9b27c1fca88c9413f5a9ed98de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694307"
---
# <a name="configure-and-manage-encryption-keys-ssrs-configuration-manager"></a><span data-ttu-id="0f843-102">配置和管理加密密钥（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="0f843-102">Configure and Manage Encryption Keys (SSRS Configuration Manager)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="0f843-103">使用加密密钥来保护存储在报表服务器数据库中的凭据和连接信息。</span><span class="sxs-lookup"><span data-stu-id="0f843-103">uses encryption keys to secure credentials and connection information that is stored in a report server database.</span></span> <span data-ttu-id="0f843-104">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中，通过一组用于保护敏感数据的公钥、私钥和对称密钥支持加密。</span><span class="sxs-lookup"><span data-stu-id="0f843-104">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], encryption is supported through a combination of public, private, and symmetric keys that are used to protect sensitive data.</span></span> <span data-ttu-id="0f843-105">安装或配置报表服务器时，在报表服务器初始化期间会创建对称密钥，报表服务器使用此对称密钥对存储在报表服务器中的敏感数据进行加密。</span><span class="sxs-lookup"><span data-stu-id="0f843-105">The symmetric key is created during report server initialization when you install or configure the report server, and it is used by the report server to encrypt sensitive data that is stored in the report server.</span></span> <span data-ttu-id="0f843-106">公钥和私钥由操作系统创建，用于保护对称密钥。</span><span class="sxs-lookup"><span data-stu-id="0f843-106">Public and private keys are created by the operating system, and they are used to protect the symmetric key.</span></span> <span data-ttu-id="0f843-107">对于在报表服务器数据库中存储敏感数据的每个报表服务器实例，都要创建一个公钥私钥对。</span><span class="sxs-lookup"><span data-stu-id="0f843-107">A public and private key pair is created for each report server instance that stores sensitive data in a report server database.</span></span>  
  
 <span data-ttu-id="0f843-108">管理加密密钥包括创建对称密钥的备份副本以及了解密钥的还原、删除或更改的时间和方式。</span><span class="sxs-lookup"><span data-stu-id="0f843-108">Managing the encryption keys consists of creating a backup copy of the symmetric key, and knowing when and how to restore, delete, or change the keys.</span></span> <span data-ttu-id="0f843-109">如果迁移报表服务器安装或配置扩展部署，则必须拥有对称密钥的备份副本，以便可以将其应用于新的安装。</span><span class="sxs-lookup"><span data-stu-id="0f843-109">If you migrate a report server installation or configure a scale-out deployment, you must have a backup copy of the symmetric key so that you can apply it to the new installation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0f843-110">定期更改 Reporting Services 加密密钥是确保安全的好办法。</span><span class="sxs-lookup"><span data-stu-id="0f843-110">Periodically changing the Reporting Services encryption key is a security best practice.</span></span> <span data-ttu-id="0f843-111">建议在升级 Reporting Services 主版本后立即更改密钥。</span><span class="sxs-lookup"><span data-stu-id="0f843-111">A recommended time to change the key is immediately following a major version upgrade of Reporting Services.</span></span> <span data-ttu-id="0f843-112">升级后更改密钥将使在升级周期外更改 Reporting Services 加密密钥所导致的额外服务中断降到最低程度。</span><span class="sxs-lookup"><span data-stu-id="0f843-112">Changing the key after an upgrade minimizes additional service interruption caused by changing the Reporting Services encryption key outside of the upgrade cycle.</span></span>  
  
 <span data-ttu-id="0f843-113">若要管理对称密钥，可以使用 Reporting Services 配置工具或 **rskeymgmt** 实用工具。</span><span class="sxs-lookup"><span data-stu-id="0f843-113">To manage symmetric keys, you can use the Reporting Services Configuration tool or the **rskeymgmt** utility.</span></span> <span data-ttu-id="0f843-114">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中包括的工具仅用于管理对称密钥（公钥和私钥由操作系统管理）。</span><span class="sxs-lookup"><span data-stu-id="0f843-114">The tools included in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] are used to manage the symmetric key only (the public and private keys are managed by the operating system).</span></span> <span data-ttu-id="0f843-115">Reporting Services 配置工具和 **rskeymgmt** 实用工具都支持以下任务：</span><span class="sxs-lookup"><span data-stu-id="0f843-115">Both the Reporting Services Configuration tool and the **rskeymgmt** utility support the following tasks:</span></span>  
  
-   <span data-ttu-id="0f843-116">备份对称密钥的副本，以便可以使用该副本来恢复报表服务器安装或作为计划迁移的一部分。</span><span class="sxs-lookup"><span data-stu-id="0f843-116">Back up a copy of the symmetric key so that you can use it to recover a report server installation or as part of a planned migration.</span></span>  
  
-   <span data-ttu-id="0f843-117">将以前保存的对称密钥还原到报表服务器数据库，以允许新的报表服务器实例访问最初不是由其进行加密的现有数据。</span><span class="sxs-lookup"><span data-stu-id="0f843-117">Restore a previously saved symmetric key to a report server database, allowing a new report server instance to access existing data that it did not originally encrypt.</span></span>  
  
-   <span data-ttu-id="0f843-118">在无法再访问加密数据时删除报表服务器数据库中的加密数据，这种情况极少出现。</span><span class="sxs-lookup"><span data-stu-id="0f843-118">Delete the encrypted data in a report server database in the unlikely event that you can no longer access encrypted data.</span></span>  
  
-   <span data-ttu-id="0f843-119">当对称密钥遭到破坏时重新创建对称密钥并重新加密数据，这种情况极少出现。</span><span class="sxs-lookup"><span data-stu-id="0f843-119">Re-create symmetric keys and re-encrypt data in the unlikely event that the symmetric key is compromised.</span></span> <span data-ttu-id="0f843-120">作为安全性方面的最佳做法，您应定期（例如，每隔几个月）重新创建对称密钥，以保护报表服务器数据库，使其能够抵御试图解开密钥的网络攻击。</span><span class="sxs-lookup"><span data-stu-id="0f843-120">As a security best practice, you should recreate the symmetric key periodically (for example, every few months) to protect the report server database from cyber attacks that attempt to decipher the key.</span></span>  
  
-   <span data-ttu-id="0f843-121">在报表服务器扩展部署（多个报表服务器同时共享一个报表服务器数据库以及为该数据库提供可逆加密的对称密钥）中添加或删除报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="0f843-121">Add or remove a report server instance from a report server scale-out deployment where multiple report servers share both a single report server database and the symmetric key that provides reversible encryption for that database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f843-122">本节内容</span><span class="sxs-lookup"><span data-stu-id="0f843-122">In This Section</span></span>  
 [<span data-ttu-id="0f843-123">初始化 Report Server（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="0f843-123">Initialize a Report Server &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-initialize-a-report-server.md)  
 <span data-ttu-id="0f843-124">介绍如何创建加密密钥。</span><span class="sxs-lookup"><span data-stu-id="0f843-124">Explains how encryption keys are created.</span></span>  
  
 [<span data-ttu-id="0f843-125">备份和还原 Reporting Services 加密密钥</span><span class="sxs-lookup"><span data-stu-id="0f843-125">Back Up and Restore Reporting Services Encryption Keys</span></span>](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
 <span data-ttu-id="0f843-126">介绍如何备份加密密钥以及如何还原备份以恢复或迁移报表服务器安装。</span><span class="sxs-lookup"><span data-stu-id="0f843-126">Explains how to back up encryption keys and restore them to recover or migrate a report server installation.</span></span>  
  
 [<span data-ttu-id="0f843-127">存储加密的 Report Server 数据（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="0f843-127">Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-store-encrypted-report-server-data.md)  
 <span data-ttu-id="0f843-128">介绍报表服务器的加密。</span><span class="sxs-lookup"><span data-stu-id="0f843-128">Describes encryption on a report server.</span></span>  
  
 [<span data-ttu-id="0f843-129">删除和重新创建加密密钥（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="0f843-129">Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)  
 <span data-ttu-id="0f843-130">介绍如何用新版本替换对称密钥以及在无法验证对称密钥时如何重新开始。</span><span class="sxs-lookup"><span data-stu-id="0f843-130">Explains how you can replace a symmetric key with a new version, and how to start over if symmetric keys cannot be validated.</span></span>  
  
 [<span data-ttu-id="0f843-131">添加和删除扩展部署的加密密钥（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="0f843-131">Add and Remove Encryption Keys for Scale-Out Deployment &#40;SSRS Configuration Manager&#41;</span></span>](add-and-remove-encryption-keys-for-scale-out-deployment.md)  
 <span data-ttu-id="0f843-132">介绍如何添加和删除加密密钥以控制在扩展部署中包括哪些报表服务器。</span><span class="sxs-lookup"><span data-stu-id="0f843-132">Explains how to add and remove encryption keys to control which report servers are part of a scale-out deployment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f843-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f843-133">See Also</span></span>  
 [<span data-ttu-id="0f843-134">存储加密的 Report Server 数据（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="0f843-134">Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-store-encrypted-report-server-data.md)  
  
  
