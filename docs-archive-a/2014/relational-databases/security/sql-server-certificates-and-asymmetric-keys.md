---
title: SQL Server 证书和非对称密钥 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server], certificates and asymmetric keys
ms.assetid: 8519aa2f-f09c-4c1c-96b5-abc24811e60c
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e8af2d92b31fee4f220b4c950fb6b7bd9c519885
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688708"
---
# <a name="sql-server-certificates-and-asymmetric-keys"></a><span data-ttu-id="a5144-102">SQL Server 证书和非对称密钥</span><span class="sxs-lookup"><span data-stu-id="a5144-102">SQL Server Certificates and Asymmetric Keys</span></span>
  <span data-ttu-id="a5144-103">公钥加密 (PKI) 是一种消息保密方式，在使用这种方式时用户将创建一个“公钥”和一个“私钥”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a5144-103">Public Key Cryptography (PKI) is a form of message secrecy in which a user creates a *public* key and a *private* key.</span></span> <span data-ttu-id="a5144-104">私钥是保密的，而公钥可以分发给其他人。</span><span class="sxs-lookup"><span data-stu-id="a5144-104">The private key is kept secret, whereas the public key can be distributed to others.</span></span> <span data-ttu-id="a5144-105">虽然密钥之间具有数学关系，但要想通过公钥推导出私钥却并不容易。</span><span class="sxs-lookup"><span data-stu-id="a5144-105">Although the keys are mathematically related, the private key cannot be easily derived by using the public key.</span></span> <span data-ttu-id="a5144-106">公钥用于加密数据，私钥用于解密数据。</span><span class="sxs-lookup"><span data-stu-id="a5144-106">The public key is used to encrypt data and the private key is used to decrypt data.</span></span> <span data-ttu-id="a5144-107">使用公钥加密的消息只能使用正确的私钥来解密。</span><span class="sxs-lookup"><span data-stu-id="a5144-107">A message that is encrypted by using the public key can only be decrypted by using the correct private key.</span></span> <span data-ttu-id="a5144-108">\*\* 由于存在两个不同的密钥，因而这些密钥是“非对称的”。</span><span class="sxs-lookup"><span data-stu-id="a5144-108">Since there are two different keys, these keys are *asymmetric*.</span></span>  
  
 <span data-ttu-id="a5144-109">证书和非对称密钥都属于非对称加密的使用方式。</span><span class="sxs-lookup"><span data-stu-id="a5144-109">Certificates and asymmetric keys are both ways to use asymmetric encryption.</span></span> <span data-ttu-id="a5144-110">证书通常用作非对称密钥的容器，因为它们可以包含更多信息，例如过期日期和颁发者。</span><span class="sxs-lookup"><span data-stu-id="a5144-110">Certificates are often used as containers for asymmetric keys because they can contain more information such as expiry dates and issuers.</span></span> <span data-ttu-id="a5144-111">这两种机制的加密算法之间存在差异，但相同密钥长度的加密强度是相同的。</span><span class="sxs-lookup"><span data-stu-id="a5144-111">There is no difference between the two mechanisms for the cryptographic algorithm, and no difference in strength given the same key length.</span></span> <span data-ttu-id="a5144-112">通常，可以使用证书来加密数据库中其他类型的加密密钥，或者为代码模块签名。</span><span class="sxs-lookup"><span data-stu-id="a5144-112">Generally, you use a certificate to encrypt other types of encryption keys in a database, or to sign code modules.</span></span>  
  
 <span data-ttu-id="a5144-113">证书和非对称密钥可以解密其他人加密的数据。</span><span class="sxs-lookup"><span data-stu-id="a5144-113">Certificates and asymmetric keys can decrypt data that the other encrypts.</span></span> <span data-ttu-id="a5144-114">通常，可以使用非对称加密来加密存储在数据库中的对称密钥。</span><span class="sxs-lookup"><span data-stu-id="a5144-114">Generally, you use asymmetric encryption to encrypt a symmetric key for storage in a database.</span></span>  
  
 <span data-ttu-id="a5144-115">公钥不像证书那样具有特定格式，并且不能将其导出到文件中。</span><span class="sxs-lookup"><span data-stu-id="a5144-115">A public key does not have a particular format like a certificate would have, and you cannot export it to a file.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a5144-116">包含多种功能，可用于创建和管理与服务器和数据库一起使用的证书和密钥。</span><span class="sxs-lookup"><span data-stu-id="a5144-116">contains features that enable you to create and manage certificates and keys for use with the server and database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a5144-117">无法用于创建和管理与其他应用程序或操作系统一起使用的证书和密钥。</span><span class="sxs-lookup"><span data-stu-id="a5144-117">cannot be used to create and manage certificates and keys with other applications or in the operating system.</span></span>  
  
## <a name="certificates"></a><span data-ttu-id="a5144-118">证书</span><span class="sxs-lookup"><span data-stu-id="a5144-118">Certificates</span></span>  
 <span data-ttu-id="a5144-119">证书是一个数字签名的安全对象，其中包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的公钥（还可以选择包含私钥）。</span><span class="sxs-lookup"><span data-stu-id="a5144-119">A certificate is a digitally signed security object that contains a public (and optionally a private) key for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a5144-120">您可以使用外部生成的证书，也可以由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 生成证书。</span><span class="sxs-lookup"><span data-stu-id="a5144-120">You can use externally generated certificates or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can generate certificates.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a5144-121">证书符合 IETF X.509v3 证书标准。</span><span class="sxs-lookup"><span data-stu-id="a5144-121">certificates comply with the IETF X.509v3 certificate standard.</span></span>  
  
 <span data-ttu-id="a5144-122">证书非常有用，因为它具有将密钥导出和导入 X.509 证书文件的选项。</span><span class="sxs-lookup"><span data-stu-id="a5144-122">Certificates are useful because of the option of both exporting and importing keys to X.509 certificate files.</span></span> <span data-ttu-id="a5144-123">用于创建证书的语法允许为证书使用创建选项，例如过期日期。</span><span class="sxs-lookup"><span data-stu-id="a5144-123">The syntax for creating certificates allows for creation options for certificates such as an expiry date.</span></span>  
  
### <a name="using-a-certificate-in-sql-server"></a><span data-ttu-id="a5144-124">在 SQL Server 中使用证书</span><span class="sxs-lookup"><span data-stu-id="a5144-124">Using a Certificate in SQL Server</span></span>  
 <span data-ttu-id="a5144-125">证书可用来帮助确保连接的安全性（在数据库镜像中）、为包和其他对象签名或者加密数据或连接。</span><span class="sxs-lookup"><span data-stu-id="a5144-125">Certificates can be used to help secure connections, in database mirroring, to sign packages and other objects, or to encrypt data or connections.</span></span> <span data-ttu-id="a5144-126">下表列出了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中有关证书的其他资源。</span><span class="sxs-lookup"><span data-stu-id="a5144-126">The following table lists additional resources for certificates in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="a5144-127">主题</span><span class="sxs-lookup"><span data-stu-id="a5144-127">Topic</span></span>|<span data-ttu-id="a5144-128">说明</span><span class="sxs-lookup"><span data-stu-id="a5144-128">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a5144-129">CREATE CERTIFICATE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a5144-129">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)|<span data-ttu-id="a5144-130">介绍用于创建证书的命令。</span><span class="sxs-lookup"><span data-stu-id="a5144-130">Explains the command for creating certificates.</span></span>|  
|[<span data-ttu-id="a5144-131">使用数字签名标识包的源</span><span class="sxs-lookup"><span data-stu-id="a5144-131">Identify the Source of Packages with Digital Signatures</span></span>](../../integration-services/security/identify-the-source-of-packages-with-digital-signatures.md)|<span data-ttu-id="a5144-132">显示有关如何使用证书为软件包签名的信息。</span><span class="sxs-lookup"><span data-stu-id="a5144-132">Shows information about how to use certificates to sign software packages.</span></span>|  
|[<span data-ttu-id="a5144-133">使用数据库镜像终结点证书 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a5144-133">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)|<span data-ttu-id="a5144-134">提供有关如何将证书用于数据库镜像的信息。</span><span class="sxs-lookup"><span data-stu-id="a5144-134">Covers information about how to use certificates with Database Mirroring.</span></span>|  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="a5144-135">非对称密钥</span><span class="sxs-lookup"><span data-stu-id="a5144-135">Asymmetric Keys</span></span>  
 <span data-ttu-id="a5144-136">非对称密钥用于确保对称密钥的安全性。</span><span class="sxs-lookup"><span data-stu-id="a5144-136">Asymmetric keys are used for securing symmetric keys.</span></span> <span data-ttu-id="a5144-137">它们还可用于有限数据加密以及对数据库对象进行数字签名。</span><span class="sxs-lookup"><span data-stu-id="a5144-137">They can also be used for limited data encryption and to digitally sign database objects.</span></span> <span data-ttu-id="a5144-138">非对称密钥由私钥和对应的公钥组成。</span><span class="sxs-lookup"><span data-stu-id="a5144-138">An asymmetric key consists of a private key and a corresponding public key.</span></span> <span data-ttu-id="a5144-139">有关非对称密钥的详细信息，请参阅 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)的公钥（还可以选择包含私钥）。</span><span class="sxs-lookup"><span data-stu-id="a5144-139">For more information about asymmetric keys, see [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql).</span></span>  
  
 <span data-ttu-id="a5144-140">可以从强名称密钥文件导入非对称密钥，但不能将其导出。</span><span class="sxs-lookup"><span data-stu-id="a5144-140">Asymmetric keys can be imported from strong name key files, but they cannot be exported.</span></span> <span data-ttu-id="a5144-141">它们也没有过期选项。</span><span class="sxs-lookup"><span data-stu-id="a5144-141">They also do not have expiry options.</span></span> <span data-ttu-id="a5144-142">非对称密钥不能加密连接。</span><span class="sxs-lookup"><span data-stu-id="a5144-142">Asymmetric keys cannot encrypt connections.</span></span>  
  
### <a name="using-an-asymmetric-key-in-sql-server"></a><span data-ttu-id="a5144-143">在 SQL Server 中使用非对称密钥</span><span class="sxs-lookup"><span data-stu-id="a5144-143">Using an Asymmetric Key in SQL Server</span></span>  
 <span data-ttu-id="a5144-144">非对称密钥可用来帮助确保数据的安全性或为纯文本签名。</span><span class="sxs-lookup"><span data-stu-id="a5144-144">Asymmetric keys can be used to help secure data or sign plaintext.</span></span> <span data-ttu-id="a5144-145">下表列出了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中有关非对称密钥的其他资源。</span><span class="sxs-lookup"><span data-stu-id="a5144-145">The following table lists additional resources for asymmetric keys in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="a5144-146">主题</span><span class="sxs-lookup"><span data-stu-id="a5144-146">Topic</span></span>|<span data-ttu-id="a5144-147">说明</span><span class="sxs-lookup"><span data-stu-id="a5144-147">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a5144-148">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a5144-148">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)|<span data-ttu-id="a5144-149">介绍用于创建非对称密钥的命令。</span><span class="sxs-lookup"><span data-stu-id="a5144-149">Explains the command for creating asymmetric keys.</span></span>|  
|[<span data-ttu-id="a5144-150">SIGNBYASYMKEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a5144-150">SIGNBYASYMKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/signbyasymkey-transact-sql)|<span data-ttu-id="a5144-151">显示用于为对象签名的选项。</span><span class="sxs-lookup"><span data-stu-id="a5144-151">Displays the options for signing objects.</span></span>|  
  
## <a name="tools"></a><span data-ttu-id="a5144-152">工具</span><span class="sxs-lookup"><span data-stu-id="a5144-152">Tools</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="a5144-153">提供了用于生成证书和强名称密钥文件的工具和实用工具。</span><span class="sxs-lookup"><span data-stu-id="a5144-153">provides tools and utilities that will generate certificates and strong name key files.</span></span> <span data-ttu-id="a5144-154">与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 语法相比，这些工具在密钥生成过程中提供了更加丰富的灵活选择。</span><span class="sxs-lookup"><span data-stu-id="a5144-154">These tools offer a richer amount of flexibility in the key generation process than the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntax.</span></span> <span data-ttu-id="a5144-155">您可以使用这些工具创建具有更复杂的密钥长度的 RSA 密钥，然后将其导入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a5144-155">You can use these tools to create RSA keys with more complex key lengths and then import them into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a5144-156">下表介绍了在哪里可以找到这些工具。</span><span class="sxs-lookup"><span data-stu-id="a5144-156">The following table explains shows where to find these tools.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5144-157">工具</span><span class="sxs-lookup"><span data-stu-id="a5144-157">Tool</span></span>|<span data-ttu-id="a5144-158">目的</span><span class="sxs-lookup"><span data-stu-id="a5144-158">Purpose</span></span>|  
|<span data-ttu-id="a5144-159">[makecert](https://msdn2.microsoft.com/library/bfsktky3\(VS.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a5144-159">[makecert](https://msdn2.microsoft.com/library/bfsktky3\(VS.80\).aspx)</span></span>|<span data-ttu-id="a5144-160">创建证书。</span><span class="sxs-lookup"><span data-stu-id="a5144-160">Creates certificates.</span></span>|  
|<span data-ttu-id="a5144-161">[sn](https://msdn2.microsoft.com/library/k5b5tt23\(VS.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a5144-161">[sn](https://msdn2.microsoft.com/library/k5b5tt23\(VS.80\).aspx)</span></span>|<span data-ttu-id="a5144-162">创建对称密钥的强名称。</span><span class="sxs-lookup"><span data-stu-id="a5144-162">Creates strong names for symmetric keys.</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="a5144-163">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="a5144-163">Related Tasks</span></span>  
 [<span data-ttu-id="a5144-164">选择加密算法</span><span class="sxs-lookup"><span data-stu-id="a5144-164">Choose an Encryption Algorithm</span></span>](encryption/choose-an-encryption-algorithm.md)  
  
 [<span data-ttu-id="a5144-165">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a5144-165">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-symmetric-key-transact-sql)  
  
 [<span data-ttu-id="a5144-166">CREATE CERTIFICATE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a5144-166">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="a5144-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5144-167">See Also</span></span>  
 <span data-ttu-id="a5144-168">[sys.certificates (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a5144-168">[sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql) </span></span>  
 [<span data-ttu-id="a5144-169">透明数据加密 (TDE)</span><span class="sxs-lookup"><span data-stu-id="a5144-169">Transparent Data Encryption &#40;TDE&#41;</span></span>](encryption/transparent-data-encryption.md)  
  
