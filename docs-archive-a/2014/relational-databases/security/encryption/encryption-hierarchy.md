---
title: 加密层次结构 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], hierarchies
- cryptography [SQL Server], hierarchies
- encryption keys [SQL Server]
- security [SQL Server], encryption
- hierarchies [SQL Server], encryption
ms.assetid: 96c276d5-1bba-4e95-b678-10f059f1fbcf
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: d38bb83c2f6a2487e547c4686be5c65bc012e33e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693684"
---
# <a name="encryption-hierarchy"></a><span data-ttu-id="c063d-102">加密层次结构</span><span class="sxs-lookup"><span data-stu-id="c063d-102">Encryption Hierarchy</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="c063d-103">用分层加密和密钥管理基础结构来加密数据。</span><span class="sxs-lookup"><span data-stu-id="c063d-103">encrypts data with a hierarchical encryption and key management infrastructure.</span></span> <span data-ttu-id="c063d-104">每一层都使用证书、非对称密钥和对称密钥的组合对它下面的一层进行加密。</span><span class="sxs-lookup"><span data-stu-id="c063d-104">Each layer encrypts the layer below it by using a combination of certificates, asymmetric keys, and symmetric keys.</span></span> <span data-ttu-id="c063d-105">非对称密钥和对称密钥可以存储在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之外的可扩展密钥管理 (EKM) 模块中。</span><span class="sxs-lookup"><span data-stu-id="c063d-105">Asymmetric keys and symmetric keys can be stored outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in an Extensible Key Management (EKM) module.</span></span>  
  
 <span data-ttu-id="c063d-106">下图说明了加密层次结构的每一层是如何对它下面的一层进行加密的，并且显示了最常用的加密配置。</span><span class="sxs-lookup"><span data-stu-id="c063d-106">The following illustration shows that each layer of the encryption hierarchy encrypts the layer beneath it, and displays the most common encryption configurations.</span></span> <span data-ttu-id="c063d-107">对层次结构的开始进行的访问通常受密码保护。</span><span class="sxs-lookup"><span data-stu-id="c063d-107">The access to the start of the hierarchy is usually protected by a password.</span></span>  
  
 <span data-ttu-id="c063d-108">![以堆积图形式显示一些加密组合。](../../../database-engine/media/encryption-hierarchy-stack.gif "以堆积图形式显示一些加密组合。")</span><span class="sxs-lookup"><span data-stu-id="c063d-108">![Displays some encryption combinations in a stack.](../../../database-engine/media/encryption-hierarchy-stack.gif "Displays some encryption combinations in a stack.")</span></span>  
  
 <span data-ttu-id="c063d-109">请记住以下概念：</span><span class="sxs-lookup"><span data-stu-id="c063d-109">Keep in mind the following concepts:</span></span>  
  
-   <span data-ttu-id="c063d-110">为了获得最佳性能，使用对称密钥（而不是证书或非对称密钥）加密数据。</span><span class="sxs-lookup"><span data-stu-id="c063d-110">For best performance, encrypt data using symmetric keys instead of certificates or asymmetric keys.</span></span>  
  
-   <span data-ttu-id="c063d-111">数据库主密钥受服务主密钥保护。</span><span class="sxs-lookup"><span data-stu-id="c063d-111">Database master keys are protected by the Service Master Key.</span></span> <span data-ttu-id="c063d-112">服务主密钥由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装程序创建，并且使用 Windows 数据保护 API (DPAPI) 进行加密。</span><span class="sxs-lookup"><span data-stu-id="c063d-112">The Service Master Key is created by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] setup and is encrypted with the Windows Data Protection API (DPAPI).</span></span>  
  
-   <span data-ttu-id="c063d-113">堆叠其他层的其他加密层次结构是可能的。</span><span class="sxs-lookup"><span data-stu-id="c063d-113">Other encryption hierarchies stacking additional layers are possible.</span></span>  
  
-   <span data-ttu-id="c063d-114">可扩展密钥管理 (EKM) 模块将对称密钥或非对称密钥保存在 SQL Server 的外部。</span><span class="sxs-lookup"><span data-stu-id="c063d-114">An Extensible Key Management (EKM) module holds symmetric or asymmetric keys outside of SQL Server.</span></span>  
  
-   <span data-ttu-id="c063d-115">透明数据加密 (TDE) 必须使用称为数据库加密密钥的对称密钥，该密钥受由 master 数据库的数据库主密钥保护的证书保护，或者受存储在 EKM 中的非对称密钥保护。</span><span class="sxs-lookup"><span data-stu-id="c063d-115">Transparent Data Encryption (TDE) must use a symmetric key called the database encryption key which is protected by either a certificate protected by the database master key of the master database, or by an asymmetric key stored in an EKM.</span></span>  
  
-   <span data-ttu-id="c063d-116">服务主密钥和所有数据库主密钥是对称密钥。</span><span class="sxs-lookup"><span data-stu-id="c063d-116">The Service Master Key and all Database Master Keys are symmetric keys.</span></span>  
  
 <span data-ttu-id="c063d-117">下图以另一种方式显示了相同的信息。</span><span class="sxs-lookup"><span data-stu-id="c063d-117">The following illustration shows the same information in an alternative manner.</span></span>  
  
 <span data-ttu-id="c063d-118">![以轮形图形式显示一些加密组合。](../../../database-engine/media/encryption-hierarchy-wheel.gif "以轮形图形式显示一些加密组合。")</span><span class="sxs-lookup"><span data-stu-id="c063d-118">![Displays some encryption combinations in a wheel.](../../../database-engine/media/encryption-hierarchy-wheel.gif "Displays some encryption combinations in a wheel.")</span></span>  
  
 <span data-ttu-id="c063d-119">此图说明了以下其他概念：</span><span class="sxs-lookup"><span data-stu-id="c063d-119">This diagram illustrates the following additional concepts:</span></span>  
  
-   <span data-ttu-id="c063d-120">在此图中，箭头表示常用的加密层次结构。</span><span class="sxs-lookup"><span data-stu-id="c063d-120">In this illustration, arrows indicate common encryption hierarchies.</span></span>  
  
-   <span data-ttu-id="c063d-121">EKM 中的对称密钥和非对称密钥可以保护对存储在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中的对称密钥和非对称密钥进行的访问。</span><span class="sxs-lookup"><span data-stu-id="c063d-121">Symmetric and asymmetric keys in the EKM can protect access to the symmetric and asymmetric keys stored in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c063d-122">与 EKM 有关的虚线表示 EKM 中的密钥可以替换存储在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中的对称密钥和非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="c063d-122">The dotted line associated with EKM indicates that keys in the EKM could replace the symmetric and asymmetric keys stored in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="encryption-mechanisms"></a><span data-ttu-id="c063d-123">加密机制</span><span class="sxs-lookup"><span data-stu-id="c063d-123">Encryption Mechanisms</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="c063d-124">提供了下列加密机制：</span><span class="sxs-lookup"><span data-stu-id="c063d-124">provides the following mechanisms for encryption:</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="c063d-125">函数</span><span class="sxs-lookup"><span data-stu-id="c063d-125">functions</span></span>  
  
-   <span data-ttu-id="c063d-126">非对称密钥</span><span class="sxs-lookup"><span data-stu-id="c063d-126">Asymmetric keys</span></span>  
  
-   <span data-ttu-id="c063d-127">对称密钥</span><span class="sxs-lookup"><span data-stu-id="c063d-127">Symmetric keys</span></span>  
  
-   <span data-ttu-id="c063d-128">证书</span><span class="sxs-lookup"><span data-stu-id="c063d-128">Certificates</span></span>  
  
-   <span data-ttu-id="c063d-129">透明数据加密</span><span class="sxs-lookup"><span data-stu-id="c063d-129">Transparent Data Encryption</span></span>  
  
### <a name="transact-sql-functions"></a><span data-ttu-id="c063d-130">Transact-SQL 函数</span><span class="sxs-lookup"><span data-stu-id="c063d-130">Transact-SQL Functions</span></span>  
 <span data-ttu-id="c063d-131">插入或更新项时可使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 函数对各个项进行加密。</span><span class="sxs-lookup"><span data-stu-id="c063d-131">Individual items can be encrypted as they are inserted or updated using [!INCLUDE[tsql](../../../includes/tsql-md.md)] functions.</span></span> <span data-ttu-id="c063d-132">有关详细信息，请参阅 [ENCRYPTBYPASSPHRASE (Transact SQL)](/sql/t-sql/functions/encryptbypassphrase-transact-sql) 和 [DECRYPTBYPASSPHRASE (Transact SQL)](/sql/t-sql/functions/decryptbypassphrase-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c063d-132">For more information, see [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbypassphrase-transact-sql) and [DECRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/decryptbypassphrase-transact-sql).</span></span>  
  
### <a name="certificates"></a><span data-ttu-id="c063d-133">证书</span><span class="sxs-lookup"><span data-stu-id="c063d-133">Certificates</span></span>  
 <span data-ttu-id="c063d-134">公钥证书（通常只称为证书）是一个数字签名语句，它将公钥的值绑定到拥有对应私钥的人员、设备或服务的标识上。</span><span class="sxs-lookup"><span data-stu-id="c063d-134">A public key certificate, usually just called a certificate, is a digitally-signed statement that binds the value of a public key to the identity of the person, device, or service that holds the corresponding private key.</span></span> <span data-ttu-id="c063d-135">证书是由证书颁发机构 (CA) 颁发和签名的。</span><span class="sxs-lookup"><span data-stu-id="c063d-135">Certificates are issued and signed by a certification authority (CA).</span></span> <span data-ttu-id="c063d-136">从 CA 接收证书的实体是该证书的主体。</span><span class="sxs-lookup"><span data-stu-id="c063d-136">The entity that receives a certificate from a CA is the subject of that certificate.</span></span> <span data-ttu-id="c063d-137">证书中通常包含下列信息。</span><span class="sxs-lookup"><span data-stu-id="c063d-137">Typically, certificates contain the following information.</span></span>  
  
-   <span data-ttu-id="c063d-138">主体的公钥。</span><span class="sxs-lookup"><span data-stu-id="c063d-138">The public key of the subject.</span></span>  
  
-   <span data-ttu-id="c063d-139">主体的标识符信息，如姓名和电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="c063d-139">The identifier information of the subject, such as the name and e-mail address.</span></span>  
  
-   <span data-ttu-id="c063d-140">有效期。</span><span class="sxs-lookup"><span data-stu-id="c063d-140">The validity period.</span></span> <span data-ttu-id="c063d-141">这是指证书被认为有效的时间长度。</span><span class="sxs-lookup"><span data-stu-id="c063d-141">This is the length of time that the certificate is considered valid.</span></span>  
  
     <span data-ttu-id="c063d-142">证书只有在指定的有效期内有效，每个证书都包含一个“有效期始于”  和“有效期至”  日期。</span><span class="sxs-lookup"><span data-stu-id="c063d-142">A certificate is valid only for the period of time specified within it; every certificate contains **Valid From** and **Valid To** dates.</span></span> <span data-ttu-id="c063d-143">这两个日期设置了有效期的界限。</span><span class="sxs-lookup"><span data-stu-id="c063d-143">These dates set the boundaries of the validity period.</span></span> <span data-ttu-id="c063d-144">证书超过有效期后，必须由已过期证书的主体请求一个新证书。</span><span class="sxs-lookup"><span data-stu-id="c063d-144">When the validity period for a certificate has passed, a new certificate must be requested by the subject of the now-expired certificate.</span></span>  
  
-   <span data-ttu-id="c063d-145">颁发者标识符信息。</span><span class="sxs-lookup"><span data-stu-id="c063d-145">Issuer identifier information.</span></span>  
  
-   <span data-ttu-id="c063d-146">颁发者的数字签名。</span><span class="sxs-lookup"><span data-stu-id="c063d-146">The digital signature of the issuer.</span></span>  
  
     <span data-ttu-id="c063d-147">此签名用于证明主体的公钥和标识符信息之间的绑定的有效性。</span><span class="sxs-lookup"><span data-stu-id="c063d-147">This signature attests to the validity of the binding between the public key and the identifier information of the subject.</span></span> <span data-ttu-id="c063d-148">（在对信息进行数字签名的过程中，信息以及发件人拥有的一些秘密信息将被转换成一个称为“签名”的标记。）</span><span class="sxs-lookup"><span data-stu-id="c063d-148">(The process of digitally signing information entails transforming the information, as well as some secret information held by the sender, into a tag called a signature.)</span></span>  
  
 <span data-ttu-id="c063d-149">证书的主要好处是使主机不再需要为每个主体维护一组密码。</span><span class="sxs-lookup"><span data-stu-id="c063d-149">A primary benefit of certificates is that they relieve hosts of the need to maintain a set of passwords for individual subjects.</span></span> <span data-ttu-id="c063d-150">相反，主机只需要与证书颁发者建立信任关系，然后证书颁发者就可以签名无限数量的证书。</span><span class="sxs-lookup"><span data-stu-id="c063d-150">Instead, the host merely establishes trust in a certificate issuer, which may then sign an unlimited number of certificates.</span></span>  
  
 <span data-ttu-id="c063d-151">当主机（如安全 Web 服务器）将某个颁发者指定为受信任的根颁发机构时，主机将隐式信任该颁发者用来建立它所发出的证书绑定的策略。</span><span class="sxs-lookup"><span data-stu-id="c063d-151">When a host, such as a secure Web server, designates an issuer as a trusted root authority, the host implicitly trusts the policies that the issuer has used to establish the bindings of certificates it issues.</span></span> <span data-ttu-id="c063d-152">也就是说，主机将相信该颁发者已经验证了证书主体的标识。</span><span class="sxs-lookup"><span data-stu-id="c063d-152">In effect, the host trusts that the issuer has verified the identity of the certificate subject.</span></span> <span data-ttu-id="c063d-153">主机可以通过将颁发者自签名的证书（其中包含颁发者的公钥）放入主机的受信任根证书颁发机构证书存储区，将此颁发者指定为受信任的根颁发机构。</span><span class="sxs-lookup"><span data-stu-id="c063d-153">A host designates an issuer as a trusted root authority by putting the self-signed certificate of the issuer, which contains the public key of the issuer, into the trusted root certification authority certificate store of the host computer.</span></span> <span data-ttu-id="c063d-154">对于中间证书颁发机构或从属证书颁发机构，只有当它们具有受信任根证书颁发机构的合法路径时才会受到信任。</span><span class="sxs-lookup"><span data-stu-id="c063d-154">Intermediate or subordinate certification authorities are trusted only if they have a valid certification path from a trusted root certification authority.</span></span>  
  
 <span data-ttu-id="c063d-155">颁发者可以在证书到期之前便撤消该证书。</span><span class="sxs-lookup"><span data-stu-id="c063d-155">The issuer can revoke a certificate before it expires.</span></span> <span data-ttu-id="c063d-156">撤消后，将解除公钥与证书中声明的标识之间的绑定。</span><span class="sxs-lookup"><span data-stu-id="c063d-156">Revocation cancels the binding of a public key to an identity that is asserted in the certificate.</span></span> <span data-ttu-id="c063d-157">每个颁发者都维护一个证书撤消列表，此列表可由程序在检查任何给定证书的有效性时使用。</span><span class="sxs-lookup"><span data-stu-id="c063d-157">Each issuer maintains a certificate revocation list that can be used by programs when they are checking the validity of any given certificate.</span></span>  
  
 <span data-ttu-id="c063d-158">由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 创建的自签名证书遵循 X.509 标准并支持 X.509 v1 字段。</span><span class="sxs-lookup"><span data-stu-id="c063d-158">The self-signed certificates created by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] follow the X.509 standard and support the X.509 v1 fields.</span></span>  
  
### <a name="asymmetric-keys"></a><span data-ttu-id="c063d-159">非对称密钥</span><span class="sxs-lookup"><span data-stu-id="c063d-159">Asymmetric Keys</span></span>  
 <span data-ttu-id="c063d-160">非对称密钥由私钥和对应的公钥组成。</span><span class="sxs-lookup"><span data-stu-id="c063d-160">An asymmetric key is made up of a private key and the corresponding public key.</span></span> <span data-ttu-id="c063d-161">每个密钥都可以解密另一个密钥加密的数据。</span><span class="sxs-lookup"><span data-stu-id="c063d-161">Each key can decrypt data encrypted by the other.</span></span> <span data-ttu-id="c063d-162">非对称加密和解密相对来说会消耗大量资源，但它们比对称加密提供了更高的安全级别。</span><span class="sxs-lookup"><span data-stu-id="c063d-162">Asymmetric encryption and decryption are relatively resource-intensive, but they provide a higher level of security than symmetric encryption.</span></span> <span data-ttu-id="c063d-163">非对称密钥可用于加密对称密钥，以便存储在数据库中。</span><span class="sxs-lookup"><span data-stu-id="c063d-163">An asymmetric key can be used to encrypt a symmetric key for storage in a database.</span></span>  
  
### <a name="symmetric-keys"></a><span data-ttu-id="c063d-164">对称密钥</span><span class="sxs-lookup"><span data-stu-id="c063d-164">Symmetric Keys</span></span>  
 <span data-ttu-id="c063d-165">对称密钥是加密和解密都使用的一个密钥。</span><span class="sxs-lookup"><span data-stu-id="c063d-165">A symmetric key is one key that is used for both encryption and decryption.</span></span> <span data-ttu-id="c063d-166">使用对称密钥进行加密和解密非常快，适用于对数据库中敏感数据的日常使用。</span><span class="sxs-lookup"><span data-stu-id="c063d-166">Encryption and decryption by using a symmetric key is fast, and suitable for routine use with sensitive data in the database.</span></span>  
  
### <a name="transparent-data-encryption"></a><span data-ttu-id="c063d-167">透明数据加密</span><span class="sxs-lookup"><span data-stu-id="c063d-167">Transparent Data Encryption</span></span>  
 <span data-ttu-id="c063d-168">透明数据加密 (TDE) 是使用对称密钥进行加密的一种特殊情况。</span><span class="sxs-lookup"><span data-stu-id="c063d-168">Transparent Data Encryption (TDE) is a special case of encryption using a symmetric key.</span></span> <span data-ttu-id="c063d-169">TDE 使用称为数据库加密密钥的对称密钥加密整个数据库。</span><span class="sxs-lookup"><span data-stu-id="c063d-169">TDE encrypts an entire database using that symmetric key called the database encryption key.</span></span> <span data-ttu-id="c063d-170">数据库加密密钥受由数据库主密钥或存储在 EKM 模块中的非对称密钥保护的其他密钥或证书保护。</span><span class="sxs-lookup"><span data-stu-id="c063d-170">The database encryption key is protected by other keys or certificates which are protected either by the database master key or by an asymmetric key stored in an EKM module.</span></span> <span data-ttu-id="c063d-171">有关详细信息，请参阅[透明数据加密 (TDE)](transparent-data-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="c063d-171">For more information, see [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="c063d-172">相关内容</span><span class="sxs-lookup"><span data-stu-id="c063d-172">Related Content</span></span>  
 [<span data-ttu-id="c063d-173">保护 SQL Server</span><span class="sxs-lookup"><span data-stu-id="c063d-173">Securing SQL Server</span></span>](../securing-sql-server.md)  
  
 [<span data-ttu-id="c063d-174">安全函数 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c063d-174">Security Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/security-functions-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="c063d-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c063d-175">See Also</span></span>  
 <span data-ttu-id="c063d-176">[权限层次结构（数据库引擎）](../permissions-hierarchy-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="c063d-176">[Permissions Hierarchy &#40;Database Engine&#41;](../permissions-hierarchy-database-engine.md) </span></span>  
 [<span data-ttu-id="c063d-177">安全对象</span><span class="sxs-lookup"><span data-stu-id="c063d-177">Securables</span></span>](../securables.md)  
  
  
