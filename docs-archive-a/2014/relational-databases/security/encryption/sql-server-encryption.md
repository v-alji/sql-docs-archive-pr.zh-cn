---
title: SQL Server 加密 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], about encryption
- security [SQL Server], encryption
- cryptography [SQL Server], about cryptography
ms.assetid: ead0150e-4943-4ad5-84c8-36f85c7278f4
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 6fc68e6f3280a8e23d6a1bf4f364aadfffd69f85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694413"
---
# <a name="sql-server-encryption"></a><span data-ttu-id="00b29-102">SQL Server 加密</span><span class="sxs-lookup"><span data-stu-id="00b29-102">SQL Server Encryption</span></span>
  <span data-ttu-id="00b29-103">加密是指通过使用密钥或密码对数据进行模糊处理的过程。</span><span class="sxs-lookup"><span data-stu-id="00b29-103">Encryption is the process of obfuscating data by the use of a key or password.</span></span> <span data-ttu-id="00b29-104">这会使数据变得毫无用处，除非使用对应的解密密钥或密码。</span><span class="sxs-lookup"><span data-stu-id="00b29-104">This can make the data useless without the corresponding decryption key or password.</span></span> <span data-ttu-id="00b29-105">加密并不解决访问控制问题。</span><span class="sxs-lookup"><span data-stu-id="00b29-105">Encryption does not solve access control problems.</span></span> <span data-ttu-id="00b29-106">不过，它可以通过限制数据丢失来增强安全性，即使在访问控制失效的情况下。</span><span class="sxs-lookup"><span data-stu-id="00b29-106">However, it enhances security by limiting data loss even if access controls are bypassed.</span></span> <span data-ttu-id="00b29-107">例如，如果数据库主机配置有误且黑客获取了敏感数据，则如果数据已加密，那么被盗信息可能会毫无用处。</span><span class="sxs-lookup"><span data-stu-id="00b29-107">For example, if the database host computer is misconfigured and a hacker obtains sensitive data, that stolen information might be useless if it is encrypted.</span></span>  
  
 <span data-ttu-id="00b29-108">您可以在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中为连接、数据和存储过程使用加密。</span><span class="sxs-lookup"><span data-stu-id="00b29-108">You can use encryption in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for connections, data, and stored procedures.</span></span> <span data-ttu-id="00b29-109">下表包含有关 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中的加密的详细信息。</span><span class="sxs-lookup"><span data-stu-id="00b29-109">The following table contains more information about encryption in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="00b29-110">虽然加密是可帮助确保安全性的有力工具，但它并不适用于所有数据或连接。</span><span class="sxs-lookup"><span data-stu-id="00b29-110">Although encryption is a valuable tool to help ensure security, it should not be considered for all data or connections.</span></span> <span data-ttu-id="00b29-111">在决定是否实现加密时，请考虑用户访问数据的方式。</span><span class="sxs-lookup"><span data-stu-id="00b29-111">When you are deciding whether to implement encryption, consider how users will access data.</span></span> <span data-ttu-id="00b29-112">如果用户通过公共网络访问数据，则可能需要使用数据加密以增强安全性。</span><span class="sxs-lookup"><span data-stu-id="00b29-112">If users access data over a public network, data encryption might be required to increase security.</span></span> <span data-ttu-id="00b29-113">但是，如果所有访问都具有某项安全 Intranet 配置，则可能不需要使用加密。</span><span class="sxs-lookup"><span data-stu-id="00b29-113">However, if all access involves a secure intranet configuration, encryption might not be required.</span></span> <span data-ttu-id="00b29-114">任何时候使用加密时还应包括密码、密钥和证书的维护策略。</span><span class="sxs-lookup"><span data-stu-id="00b29-114">Any use of encryption should also include a maintenance strategy for passwords, keys, and certificates.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00b29-115">本节内容</span><span class="sxs-lookup"><span data-stu-id="00b29-115">In This Section</span></span>  
 [<span data-ttu-id="00b29-116">加密层次结构</span><span class="sxs-lookup"><span data-stu-id="00b29-116">Encryption Hierarchy</span></span>](encryption-hierarchy.md)  
 <span data-ttu-id="00b29-117">提供有关 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中的加密层次结构的信息。</span><span class="sxs-lookup"><span data-stu-id="00b29-117">Information about the encryption hierarchy in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="00b29-118">选择加密算法</span><span class="sxs-lookup"><span data-stu-id="00b29-118">Choose an Encryption Algorithm</span></span>](choose-an-encryption-algorithm.md)  
 <span data-ttu-id="00b29-119">说明如何选择有效的加密算法。</span><span class="sxs-lookup"><span data-stu-id="00b29-119">Information about how to select an effective encrypting algorithm.</span></span>  
  
 [<span data-ttu-id="00b29-120">透明数据加密 (TDE)</span><span class="sxs-lookup"><span data-stu-id="00b29-120">Transparent Data Encryption &#40;TDE&#41;</span></span>](transparent-data-encryption.md)  
 <span data-ttu-id="00b29-121">提供有关如何以透明方式来加密数据的一般信息。</span><span class="sxs-lookup"><span data-stu-id="00b29-121">General information about how to encrypt data transparently.</span></span>  
  
 [<span data-ttu-id="00b29-122">SQL Server 和数据库加密密钥（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="00b29-122">SQL Server and Database Encryption Keys &#40;Database Engine&#41;</span></span>](sql-server-and-database-encryption-keys-database-engine.md)  
 <span data-ttu-id="00b29-123">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，加密密钥包括一组用来保护敏感数据的公钥、私钥和对称密钥。</span><span class="sxs-lookup"><span data-stu-id="00b29-123">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], encryption keys include a combination of public, private, and symmetric keys that are used to protect sensitive data.</span></span> <span data-ttu-id="00b29-124">该部分介绍如何实现和管理加密密钥。</span><span class="sxs-lookup"><span data-stu-id="00b29-124">This section explains how to implement and manage encryption keys.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="00b29-125">相关内容</span><span class="sxs-lookup"><span data-stu-id="00b29-125">Related Content</span></span>  
 [<span data-ttu-id="00b29-126">保护 SQL Server</span><span class="sxs-lookup"><span data-stu-id="00b29-126">Securing SQL Server</span></span>](../securing-sql-server.md)  
 <span data-ttu-id="00b29-127">简要介绍如何帮助确保 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 平台的安全性以及如何处理用户和安全对象。</span><span class="sxs-lookup"><span data-stu-id="00b29-127">Overview of how to help secure the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] platform, and how to work with users and securable objects.</span></span>  
  
 [<span data-ttu-id="00b29-128">加密函数 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="00b29-128">Cryptographic Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/cryptographic-functions-transact-sql)  
 <span data-ttu-id="00b29-129">说明如何实现加密函数。</span><span class="sxs-lookup"><span data-stu-id="00b29-129">Information about how to implement cryptographic functions.</span></span>  
  
 [<span data-ttu-id="00b29-130">ENCRYPTBYPASSPHRASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="00b29-130">ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
 <span data-ttu-id="00b29-131">说明如何使用密码来加密数据。</span><span class="sxs-lookup"><span data-stu-id="00b29-131">Information about how to use a password to encrypt data.</span></span>  
  
 [<span data-ttu-id="00b29-132">ENCRYPTBYKEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="00b29-132">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbykey-transact-sql)  
 <span data-ttu-id="00b29-133">说明如何使用对称密钥来加密数据。</span><span class="sxs-lookup"><span data-stu-id="00b29-133">Information about how to use a symmetric key to encrypt data.</span></span>  
  
 [<span data-ttu-id="00b29-134">ENCRYPTBYASYMKEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="00b29-134">ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
 <span data-ttu-id="00b29-135">说明如何使用非对称密钥来加密数据。</span><span class="sxs-lookup"><span data-stu-id="00b29-135">Information about how to use an asymmetric key to encrypt data.</span></span>  
  
 [<span data-ttu-id="00b29-136">ENCRYPTBYCERT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="00b29-136">ENCRYPTBYCERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbycert-transact-sql)  
 <span data-ttu-id="00b29-137">说明如何使用证书来加密数据。</span><span class="sxs-lookup"><span data-stu-id="00b29-137">Information about how to use a certificate to encrypt data.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="00b29-138">外部资源</span><span class="sxs-lookup"><span data-stu-id="00b29-138">External Resources</span></span>  
 [<span data-ttu-id="00b29-139">SQL Server 2005 安全的10个步骤</span><span class="sxs-lookup"><span data-stu-id="00b29-139">10 Steps to SQL Server 2005 Security</span></span>](https://www.itprotoday.com/sql-server/10-steps-sql-server-2005-security)  
 <span data-ttu-id="00b29-140">包含有关 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安全性的最新信息。</span><span class="sxs-lookup"><span data-stu-id="00b29-140">Current information about [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b29-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00b29-141">See Also</span></span>  
 <span data-ttu-id="00b29-142">[sys.key_encryptions (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-key-encryptions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="00b29-142">[sys.key_encryptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-encryptions-transact-sql) </span></span>  
 <span data-ttu-id="00b29-143">[SQL Server 和数据库加密密钥（数据库引擎）](sql-server-and-database-encryption-keys-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="00b29-143">[SQL Server and Database Encryption Keys &#40;Database Engine&#41;](sql-server-and-database-encryption-keys-database-engine.md) </span></span>  
 [<span data-ttu-id="00b29-144">备份和还原 Reporting Services 加密密钥</span><span class="sxs-lookup"><span data-stu-id="00b29-144">Back Up and Restore Reporting Services Encryption Keys</span></span>](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
  
  
