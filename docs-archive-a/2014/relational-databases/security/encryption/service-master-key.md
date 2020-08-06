---
title: 服务主密钥 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server]
- service master key [SQL Server], about service master key
ms.assetid: 85f2095d-2590-4f59-8a29-7e100edd02bb
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: baeeffd49ac89ce85cf64932fbfd4982d7243887
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694418"
---
# <a name="service-master-key"></a><span data-ttu-id="24a5b-102">服务主密钥</span><span class="sxs-lookup"><span data-stu-id="24a5b-102">Service Master Key</span></span>
  <span data-ttu-id="24a5b-103">服务主密钥为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密层次结构的根。</span><span class="sxs-lookup"><span data-stu-id="24a5b-103">The Service Master Key is the root of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption hierarchy.</span></span> <span data-ttu-id="24a5b-104">服务主密钥是首次需要它来加密其他密钥时自动生成的。</span><span class="sxs-lookup"><span data-stu-id="24a5b-104">It is generated automatically the first time it is needed to encrypt another key.</span></span> <span data-ttu-id="24a5b-105">默认情况下，服务主密钥使用 Windows 数据保护 API 和本地计算机密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="24a5b-105">By default, the Service Master Key is encrypted using the Windows data protection API and using the local machine key.</span></span> <span data-ttu-id="24a5b-106">只有创建服务主密钥的 Windows 服务帐户或有权访问服务帐户名称和密码的主体能够打开服务主密钥。</span><span class="sxs-lookup"><span data-stu-id="24a5b-106">The Service Master Key can only be opened by the Windows service account under which it was created or by a principal with access to both the service account name and its password.</span></span>  
  
 <span data-ttu-id="24a5b-107">重新生成或还原服务主密钥涉及解密和重新加密完整的加密层次结构的操作。</span><span class="sxs-lookup"><span data-stu-id="24a5b-107">Regenerating or restoring the Service Master Key involves decrypting and re-encrypting the complete encryption hierarchy.</span></span> <span data-ttu-id="24a5b-108">除非危及到该密钥的安全性，否则应该在需求较低的时间段内安排这种占用大量资源的操作。</span><span class="sxs-lookup"><span data-stu-id="24a5b-108">Unless the key has been compromised, this resource-intensive operation should be scheduled during a period of low demand.</span></span>  
  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] <span data-ttu-id="24a5b-109">使用 AES-256 加密算法来保护服务主密钥 (SMK) 和数据库主密钥 (DMK)。</span><span class="sxs-lookup"><span data-stu-id="24a5b-109">uses the AES encryption algorithm to protect the service master key (SMK) and the database master key (DMK).</span></span> <span data-ttu-id="24a5b-110">AES 是一种比早期版本中使用的 3DES 更新的加密算法。</span><span class="sxs-lookup"><span data-stu-id="24a5b-110">AES is a newer encryption algorithm than 3DES used in earlier versions.</span></span> <span data-ttu-id="24a5b-111">在将 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 实例升级到 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 后，应重新生成 SMK 和 DMK 以便将主密钥升级到 AES。</span><span class="sxs-lookup"><span data-stu-id="24a5b-111">After upgrading an instance of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] the SMK and DMK should be regenerated in order to upgrade the master keys to AES.</span></span> <span data-ttu-id="24a5b-112">有关重新生成 SMK 的详细信息，请参阅 [ALTER SERVICE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/alter-service-master-key-transact-sql) 和 [ALTER MASTER KEY (Transact-SQL)](/sql/t-sql/statements/alter-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="24a5b-112">For more information about regenerating the SMK, see [ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-service-master-key-transact-sql) and [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql).</span></span>  
  
## <a name="best-practice"></a><span data-ttu-id="24a5b-113">最佳做法</span><span class="sxs-lookup"><span data-stu-id="24a5b-113">Best Practice</span></span>  
 <span data-ttu-id="24a5b-114">备份服务主密钥并将备份副本存储在另外一个安全位置。</span><span class="sxs-lookup"><span data-stu-id="24a5b-114">Back up the Service Master Key and store the backed up copy in a secure, off-site location.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="24a5b-115">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="24a5b-115">Related Tasks</span></span>  
 [<span data-ttu-id="24a5b-116">BACKUP SERVICE MASTER KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="24a5b-116">BACKUP SERVICE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-service-master-key-transact-sql)  
  
 [<span data-ttu-id="24a5b-117">RESTORE SERVICE MASTER KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="24a5b-117">RESTORE SERVICE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-service-master-key-transact-sql)  
  
 [<span data-ttu-id="24a5b-118">ALTER SERVICE MASTER KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="24a5b-118">ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-service-master-key-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="24a5b-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24a5b-119">See Also</span></span>  
 [<span data-ttu-id="24a5b-120">加密层次结构</span><span class="sxs-lookup"><span data-stu-id="24a5b-120">Encryption Hierarchy</span></span>](encryption-hierarchy.md)  
  
  
