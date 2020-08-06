---
title: 选择加密算法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], algorithms
- encryption [SQL Server], algorithms
- security [SQL Server], encryption
- algorithms [SQL Server encryption]
ms.assetid: 8227028c-a9c9-489d-bd27-fbf8242634ae
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 3b2c5292b4a00a3ad81e53fdbc603bb584130613
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693699"
---
# <a name="choose-an-encryption-algorithm"></a><span data-ttu-id="4ee99-102">选择加密算法</span><span class="sxs-lookup"><span data-stu-id="4ee99-102">Choose an Encryption Algorithm</span></span>
  <span data-ttu-id="4ee99-103">加密是希望保护 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例安全的管理员可以采用的多种深度防御方法之一。</span><span class="sxs-lookup"><span data-stu-id="4ee99-103">Encryption is one of several defenses-in-depth that are available to the administrator who wants to secure an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="4ee99-104">加密算法定义了未经授权的用户无法轻松逆转的数据转换。</span><span class="sxs-lookup"><span data-stu-id="4ee99-104">Encryption algorithms define data transformations that cannot be easily reversed by unauthorized users.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="4ee99-105">允许管理员和开发人员从多种算法中进行选择，其中包括 DES、Triple DES、TRIPLE_DES_3KEY、RC2、RC4、128 位 RC4、DESX、128 位 AES、192 位 AES 和 256 位 AES。</span><span class="sxs-lookup"><span data-stu-id="4ee99-105">allows administrators and developers to choose from among several algorithms, including DES, Triple DES, TRIPLE_DES_3KEY, RC2, RC4, 128-bit RC4, DESX, 128-bit AES, 192-bit AES, and 256-bit AES.</span></span>  
  
 <span data-ttu-id="4ee99-106">没有一种算法能够解决所有问题，有关每种算法的优势的说明不属于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 联机丛书的讨论范畴。</span><span class="sxs-lookup"><span data-stu-id="4ee99-106">No single algorithm is ideal for all situations, and guidance on the merits of each is beyond the scope of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="4ee99-107">但是，下列一般原则适应于：</span><span class="sxs-lookup"><span data-stu-id="4ee99-107">However, the following general principles apply:</span></span>  
  
-   <span data-ttu-id="4ee99-108">强加密通常会比较弱的加密占用更多的 CPU 资源。</span><span class="sxs-lookup"><span data-stu-id="4ee99-108">Strong encryption generally consumes more CPU resources than weak encryption.</span></span>  
  
-   <span data-ttu-id="4ee99-109">长密钥通常会比短密钥生成更强的加密。</span><span class="sxs-lookup"><span data-stu-id="4ee99-109">Long keys generally yield stronger encryption than short keys.</span></span>  
  
-   <span data-ttu-id="4ee99-110">非对称加密比使用相同密钥长度的对称加密更弱，但速度相对较慢。</span><span class="sxs-lookup"><span data-stu-id="4ee99-110">Asymmetric encryption is weaker than symmetric encryption using the same key length, but it is relatively slow.</span></span>  
  
-   <span data-ttu-id="4ee99-111">使用长密钥的块密码比流密码更强。</span><span class="sxs-lookup"><span data-stu-id="4ee99-111">Block ciphers with long keys are stronger than stream ciphers.</span></span>  
  
-   <span data-ttu-id="4ee99-112">复杂的长密码比短密码更强。</span><span class="sxs-lookup"><span data-stu-id="4ee99-112">Long, complex passwords are stronger than short passwords.</span></span>  
  
-   <span data-ttu-id="4ee99-113">如果您正在加密大量数据，应使用对称密钥来加密数据，并使用非对称密钥来加密该对称密钥。</span><span class="sxs-lookup"><span data-stu-id="4ee99-113">If you are encrypting lots of data, you should encrypt the data using a symmetric key, and encrypt the symmetric key with an asymmetric key.</span></span>  
  
-   <span data-ttu-id="4ee99-114">不能压缩已加密的数据，但可以加密已压缩的数据。</span><span class="sxs-lookup"><span data-stu-id="4ee99-114">Encrypted data cannot be compressed, but compressed data can be encrypted.</span></span> <span data-ttu-id="4ee99-115">如果使用压缩，应在加密前压缩数据。</span><span class="sxs-lookup"><span data-stu-id="4ee99-115">If you use compression, you should compress data before encrypting it.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4ee99-116">RC4 算法仅用于支持向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="4ee99-116">The RC4 algorithm is only supported for backward compatibility.</span></span> <span data-ttu-id="4ee99-117">仅当数据库兼容级别为 90 或 100 时，才能使用 RC4 或 RC4_128 对新材料进行加密。</span><span class="sxs-lookup"><span data-stu-id="4ee99-117">New material can only be encrypted using RC4 or RC4_128 when the database is in compatibility level 90 or 100.</span></span> <span data-ttu-id="4ee99-118">（建议不要使用。）而是使用一种较新的算法，如 AES 算法之一。</span><span class="sxs-lookup"><span data-stu-id="4ee99-118">(Not recommended.) Use a newer algorithm such as one of the AES algorithms instead.</span></span> <span data-ttu-id="4ee99-119">在 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 和更高版本中，可以在任何兼容级别对使用 RC4 或 RC4_128 加密的材料进行解密。</span><span class="sxs-lookup"><span data-stu-id="4ee99-119">In [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] and higher material encrypted using RC4 or RC4_128 can be decrypted in any compatibility level.</span></span>  
>   
>  <span data-ttu-id="4ee99-120">对不同数据块重复使用相同的 RC4 或 RC4_128 KEY_GUID 将导致产生相同的 RC4 密钥，因为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不自动提供 salt。</span><span class="sxs-lookup"><span data-stu-id="4ee99-120">Repeated use of the same RC4 or RC4_128 KEY_GUID on different blocks of data will result in the same RC4 key because [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not provide a salt automatically.</span></span> <span data-ttu-id="4ee99-121">重复使用相同的 RC4 密钥是已知错误，将导致加密非常不可靠。</span><span class="sxs-lookup"><span data-stu-id="4ee99-121">Using the same RC4 key repeatedly is a well-known error that will result in very weak encryption.</span></span> <span data-ttu-id="4ee99-122">因此，不推荐使用 RC4 和 RC4_128 关键字。</span><span class="sxs-lookup"><span data-stu-id="4ee99-122">Therefore, we have deprecated the RC4 and RC4_128 keywords.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="4ee99-123">有关加密算法和加密技术的详细信息，请参阅 MSDN 的 .NET Framework 开发人员指南中的 [重要安全性概念](https://go.microsoft.com/fwlink/?LinkId=62082) 。</span><span class="sxs-lookup"><span data-stu-id="4ee99-123">For more information about encryption algorithms and encryption technology, see [Key Security Concepts](https://go.microsoft.com/fwlink/?LinkId=62082) in the .NET Framework Developer's Guide on MSDN.</span></span>  
  
 <span data-ttu-id="4ee99-124">**关于 DES 算法的说明：**</span><span class="sxs-lookup"><span data-stu-id="4ee99-124">**Clarification regarding DES algorithms:**</span></span>  
  
-   <span data-ttu-id="4ee99-125">DESX 的命名不正确。</span><span class="sxs-lookup"><span data-stu-id="4ee99-125">DESX was incorrectly named.</span></span> <span data-ttu-id="4ee99-126">使用 ALGORITHM = DESX 创建的对称密钥实际上使用的是具有 192 位密钥的 TRIPLE DES 密码。</span><span class="sxs-lookup"><span data-stu-id="4ee99-126">Symmetric keys created with ALGORITHM = DESX actually use the TRIPLE DES cipher with a 192-bit key.</span></span> <span data-ttu-id="4ee99-127">不提供 DESX 算法。</span><span class="sxs-lookup"><span data-stu-id="4ee99-127">The DESX algorithm is not provided.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
-   <span data-ttu-id="4ee99-128">使用 ALGORITHM = TRIPLE_DES_3KEY 创建的对称密钥使用的是具有 192 位密钥的 TRIPLE DES。</span><span class="sxs-lookup"><span data-stu-id="4ee99-128">Symmetric keys created with ALGORITHM = TRIPLE_DES_3KEY use TRIPLE DES with a 192-bit key.</span></span>  
  
-   <span data-ttu-id="4ee99-129">使用 ALGORITHM = TRIPLE_DES 创建的对称密钥使用的是具有 128 位密钥的 TRIPLE DES。</span><span class="sxs-lookup"><span data-stu-id="4ee99-129">Symmetric keys created with ALGORITHM = TRIPLE_DES use TRIPLE DES with a 128-bit key.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="4ee99-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="4ee99-130">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4ee99-131">使用对称密钥加密。</span><span class="sxs-lookup"><span data-stu-id="4ee99-131">Encrypting using a symmetric key.</span></span>|[<span data-ttu-id="4ee99-132">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4ee99-132">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-symmetric-key-transact-sql)|  
|<span data-ttu-id="4ee99-133">使用非对称密钥加密。</span><span class="sxs-lookup"><span data-stu-id="4ee99-133">Encrypting using an asymmetric key.</span></span>|[<span data-ttu-id="4ee99-134">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4ee99-134">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)|  
|<span data-ttu-id="4ee99-135">使用证书加密。</span><span class="sxs-lookup"><span data-stu-id="4ee99-135">Encrypting using a certificate.</span></span>|[<span data-ttu-id="4ee99-136">CREATE CERTIFICATE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4ee99-136">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)|  
|<span data-ttu-id="4ee99-137">使用透明数据加密对数据库文件进行加密。</span><span class="sxs-lookup"><span data-stu-id="4ee99-137">Encrypting database files using transparent data encryption.</span></span>|[<span data-ttu-id="4ee99-138">透明数据加密 (TDE)</span><span class="sxs-lookup"><span data-stu-id="4ee99-138">Transparent Data Encryption &#40;TDE&#41;</span></span>](transparent-data-encryption.md)|  
|<span data-ttu-id="4ee99-139">如何加密表中的列。</span><span class="sxs-lookup"><span data-stu-id="4ee99-139">How to encrypt one column of a table.</span></span>|[<span data-ttu-id="4ee99-140">加密数据列</span><span class="sxs-lookup"><span data-stu-id="4ee99-140">Encrypt a Column of Data</span></span>](encrypt-a-column-of-data.md)|  
  
## <a name="see-also"></a><span data-ttu-id="4ee99-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ee99-141">See Also</span></span>  
 <span data-ttu-id="4ee99-142">[SQL Server 加密](sql-server-encryption.md) </span><span class="sxs-lookup"><span data-stu-id="4ee99-142">[SQL Server Encryption](sql-server-encryption.md) </span></span>  
 [<span data-ttu-id="4ee99-143">加密层次结构</span><span class="sxs-lookup"><span data-stu-id="4ee99-143">Encryption Hierarchy</span></span>](encryption-hierarchy.md)  
  
  
