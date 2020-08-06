---
title: 可扩展的密钥管理 (EKM) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Key Management
- Extensible Key Management
- EKM, described
ms.assetid: 9bfaf500-2d1e-4c02-b041-b8761a9e695b
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 4fc9b002b57f8118494709f8fe27a8b19ce28d8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689823"
---
# <a name="extensible-key-management-ekm"></a><span data-ttu-id="ddcf9-102">可扩展的密钥管理 (EKM)</span><span class="sxs-lookup"><span data-stu-id="ddcf9-102">Extensible Key Management (EKM)</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="ddcf9-103">提供数据加密功能以及*可扩展的密钥管理* (EKM)，同时使用“Microsoft 加密 API”(MSCAPI) 提供程序进行加密和生成密钥。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-103">provides data encryption capabilities together with *Extensible Key Management* (EKM), using the *Microsoft Cryptographic API* (MSCAPI) provider for encryption and key generation.</span></span> <span data-ttu-id="ddcf9-104">在临时密钥容器中可创建用于数据和密钥加密的加密密钥，并且必须先将它们从访问接口中导出，然后才能存储在数据库中。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-104">Encryption keys for data and key encryption are created in transient key containers, and they must be exported from a provider before they are stored in the database.</span></span> <span data-ttu-id="ddcf9-105">这种方法使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]能够对密钥进行管理，其中包括加密密钥层次结构和密钥备份。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-105">This approach enables key management that includes an encryption key hierarchy and key backup, to be handled by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="ddcf9-106">随着法规遵从性和数据隐私问题方面的需求不断增长，组织正利用加密方法来提供“深度防御”解决方案。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-106">With the growing demand for regulatory compliance and concern for data privacy, organizations are taking advantage of encryption as a way to provide a "defense in depth" solution.</span></span> <span data-ttu-id="ddcf9-107">如果仅使用数据库加密管理工具，则这种方法通常是不切实际的。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-107">This approach is often impractical using only database encryption management tools.</span></span> <span data-ttu-id="ddcf9-108">硬件供应商通过使用“硬件安全模块”(HSM) 来提供能解决企业密钥管理的产品。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-108">Hardware vendors provide products that address enterprise key management by using *Hardware Security Modules* (HSM).</span></span> <span data-ttu-id="ddcf9-109">HSM 设备在硬件或软件模块上存储加密密钥。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-109">HSM devices store encryption keys on hardware or software modules.</span></span> <span data-ttu-id="ddcf9-110">由于加密密钥与加密数据分开存储，因此这是一种更安全的解决方案。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-110">This is a more secure solution because the encryption keys do not reside with encryption data.</span></span>  
  
 <span data-ttu-id="ddcf9-111">许多供应商提供 HSM 来解决密钥管理和加密加速问题。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-111">A number of vendors offer HSM for both key management and encryption acceleration.</span></span> <span data-ttu-id="ddcf9-112">HSM 设备对服务器进程使用硬件接口作为应用程序与 HSM 之间的媒介。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-112">HSM devices use hardware interfaces with a server process as an intermediary between an application and an HSM.</span></span> <span data-ttu-id="ddcf9-113">供应商还在他们的模块（可能是硬件或软件）上实施 MSCAPI 访问接口。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-113">Vendors also implement MSCAPI providers over their modules, which might be hardware or software.</span></span> <span data-ttu-id="ddcf9-114">MSCAPI 通常只提供由 HSM 提供的功能子集。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-114">MSCAPI often offers only a subset of the functionality that is offered by an HSM.</span></span> <span data-ttu-id="ddcf9-115">供应商也可以针对 HSM、密钥配置和密钥访问提供管理软件。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-115">Vendors can also provide management software for HSM, key configuration, and key access.</span></span>  
  
 <span data-ttu-id="ddcf9-116">HSM 的实现随供应商的不同而有所不同，将其用于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 需要一个公共接口。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-116">HSM implementations vary from vendor to vendor, and to use them with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] requires a common interface.</span></span> <span data-ttu-id="ddcf9-117">尽管 MSCAPI 提供此接口，但它仅支持 HSM 功能的子集。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-117">Although the MSCAPI provides this interface, it supports only a subset of the HSM features.</span></span> <span data-ttu-id="ddcf9-118">另外它还存在其他限制，例如无法在本机保留对称密钥，以及缺少面向会话的支持。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-118">It also has other limitations, such as the inability to natively persist symmetric keys, and a lack of session-oriented support.</span></span>  
  
 <span data-ttu-id="ddcf9-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可扩展的密钥管理能够使第三方 EKM/HSM 供应商在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中注册他们的模块。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-119">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Extensible Key Management enables third-party EKM/HSM vendors to register their modules in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ddcf9-120">注册后， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用户可以使用存储在 EKM 模块上的加密密钥。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-120">When registered, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] users can use the encryption keys stored on EKM modules.</span></span> <span data-ttu-id="ddcf9-121">这样， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 便可访问这些模块支持的高级加密功能（例如批量加密和解密）以及密钥管理功能（例如密钥老化和密钥旋转）。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-121">This enables [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to access the advanced encryption features these modules support such as bulk encryption and decryption, and key management functions such as key aging and key rotation.</span></span>  
  
 <span data-ttu-id="ddcf9-122">当在 Azure VM 中运行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 时， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可以使用存储在 [Azure 密钥保管库](https://go.microsoft.com/fwlink/?LinkId=521401)中的密钥。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-122">When running [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in an Azure VM, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can use keys stored in the [Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521401).</span></span> <span data-ttu-id="ddcf9-123">有关详细信息，请参阅 [使用 Azure Key Vault 的可扩展密钥管理 (SQL Server)](extensible-key-management-using-azure-key-vault-sql-server.md)能够对密钥进行管理，其中包括加密密钥层次结构和密钥备份。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-123">For more information, see [Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md).</span></span>  
  
## <a name="ekm-configuration"></a><span data-ttu-id="ddcf9-124">EKM 配置</span><span class="sxs-lookup"><span data-stu-id="ddcf9-124">EKM Configuration</span></span>  
 <span data-ttu-id="ddcf9-125">[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的所有版本中都未提供可扩展密钥管理。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-125">Extensible Key Management is not available in every edition of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ddcf9-126">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-126">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="ddcf9-127">默认情况下，可扩展的密钥管理是关闭的。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-127">By default, Extensible Key Management is off.</span></span> <span data-ttu-id="ddcf9-128">若要启用此功能，请使用包含以下选项和值的 sp_configure 命令，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="ddcf9-128">To enable this feature, use the sp_configure command that has the following option and value, as in the following example:</span></span>  
  
```  
sp_configure 'show advanced', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'EKM provider enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ddcf9-129">如果在不支持 EKM 的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本中使用此选项的 sp_configure 命令，将会收到一条错误。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-129">If you use the sp_configure command for this option on editions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that do not support EKM, you will receive an error.</span></span>  
  
 <span data-ttu-id="ddcf9-130">若要禁用该功能，请将此值设置为 **0**。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-130">To disable the feature, set the value to **0**.</span></span> <span data-ttu-id="ddcf9-131">有关如何设置服务器选项的详细信息，请参阅 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-131">For more information about how to set server options, see [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>  
  
## <a name="how-to-use-ekm"></a><span data-ttu-id="ddcf9-132">如何使用 EKM</span><span class="sxs-lookup"><span data-stu-id="ddcf9-132">How to Use EKM</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="ddcf9-133">可扩展的密钥管理能够使保护数据库文件的加密密钥存储在即用型设备中，例如智能卡、USB 设备或 EKM/HSM 模块。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-133">Extensible Key Management enables the encryption keys that protect the database files to be stored in an off-box device such as a smartcard, USB device, or EKM/HSM module.</span></span> <span data-ttu-id="ddcf9-134">这样还能针对数据库管理员（除 sysadmin 组中的成员）来保护数据。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-134">This also enables data protection from database administrators (except members of the sysadmin group).</span></span> <span data-ttu-id="ddcf9-135">可以通过使用只能由数据库用户通过外部 EKM/HSM 模块访问的加密密钥来实现数据加密。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-135">Data can be encrypted by using encryption keys that only the database user has access to on the external EKM/HSM module.</span></span>  
  
 <span data-ttu-id="ddcf9-136">可扩展的密钥管理还提供下列优点：</span><span class="sxs-lookup"><span data-stu-id="ddcf9-136">Extensible Key Management also provides the following benefits:</span></span>  
  
-   <span data-ttu-id="ddcf9-137">其他授权检查（启用责任分离）。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-137">Additional authorization check (enabling separation of duties).</span></span>  
  
-   <span data-ttu-id="ddcf9-138">更高性能的基于硬件的加密/解密。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-138">Higher performance for hardware-based encryption/decryption.</span></span>  
  
-   <span data-ttu-id="ddcf9-139">外部加密密钥生成。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-139">External encryption key generation.</span></span>  
  
-   <span data-ttu-id="ddcf9-140">外部加密密钥存储（物理分离数据和密钥）。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-140">External encryption key storage (physical separation of data and keys).</span></span>  
  
-   <span data-ttu-id="ddcf9-141">加密密钥检索。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-141">Encryption key retrieval.</span></span>  
  
-   <span data-ttu-id="ddcf9-142">外部加密密钥保留（启用加密密钥旋转）。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-142">External encryption key retention (enables encryption key rotation).</span></span>  
  
-   <span data-ttu-id="ddcf9-143">更易于加密密钥恢复。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-143">Easier encryption key recovery.</span></span>  
  
-   <span data-ttu-id="ddcf9-144">可管理的加密密钥分发。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-144">Manageable encryption key distribution.</span></span>  
  
-   <span data-ttu-id="ddcf9-145">安全的加密密钥处置。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-145">Secure encryption key disposal.</span></span>  
  
 <span data-ttu-id="ddcf9-146">您可以对用户名和密码的组合或由 EKM 驱动程序定义的其他方法使用可扩展的密钥管理。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-146">You can use Extensible Key Management for a username and password combination or other methods defined by the EKM driver.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="ddcf9-147">若要进行故障排除， [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 技术支持可能需要 EKM 访问接口的加密密钥。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-147">For troubleshooting, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] technical support might require the encryption key from the EKM provider.</span></span> <span data-ttu-id="ddcf9-148">您可能还需要访问供应商工具或进程，以帮助解决问题。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-148">You might also need to access vendor tools or processes to help resolve an issue.</span></span>  
  
### <a name="authentication-with-an-ekm-device"></a><span data-ttu-id="ddcf9-149">使用 EKM 设备进行身份验证</span><span class="sxs-lookup"><span data-stu-id="ddcf9-149">Authentication with an EKM Device</span></span>  
 <span data-ttu-id="ddcf9-150">EKM 模块可以支持多种类型的身份验证。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-150">An EKM module can support more than one type of authentication.</span></span> <span data-ttu-id="ddcf9-151">每个访问接口只向 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]公开一种身份验证类型，也就是说，如果模块支持“基本”或“其他”身份验证类型，则接口将公开这两种类型中的一种，而不会同时公开这两种类型。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-151">Each provider exposes only one type of authentication to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], that is if the module supports Basic or Other authentication types, it exposes one or the other, but not both.</span></span>  
  
#### <a name="ekm-device-specific-basic-authentication-using-usernamepassword"></a><span data-ttu-id="ddcf9-152">使用用户名/密码的 EKM 设备特定的基本身份验证</span><span class="sxs-lookup"><span data-stu-id="ddcf9-152">EKM Device-Specific Basic Authentication Using username/password</span></span>  
 <span data-ttu-id="ddcf9-153">对于那些支持使用用户名/密码对的基本身份验证的 EKM 模块，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 提供使用凭据的透明身份验证。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-153">For those EKM modules that support Basic authentication using a *username/password* pair, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provides transparent authentication using credentials.</span></span> <span data-ttu-id="ddcf9-154">有关凭据的详细信息，请参阅[凭据（数据库引擎）](../authentication-access/credentials-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-154">For more information about credentials, see [Credentials &#40;Database Engine&#41;](../authentication-access/credentials-database-engine.md).</span></span>  
  
 <span data-ttu-id="ddcf9-155">可以为 EKM 访问接口创建凭据并将其映射到登录名（Windows 帐户和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 帐户），以便根据每个登录名访问 EKM 模块。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-155">A credential can be created for an EKM provider and mapped to a login (both Windows and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] accounts) to access an EKM module on per-login basis.</span></span> <span data-ttu-id="ddcf9-156">凭据的 *Identify* 字段包含用户名； *secret* 字段包含连接到 EKM 模块的密码。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-156">The *Identify* field of the credential contains the username; the *secret* field contains a password to connect to an EKM module.</span></span>  
  
 <span data-ttu-id="ddcf9-157">如果 EKM 访问接口没有任何登录映射的凭据，则使用映射到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-157">If there is no login mapped credential for the EKM provider, the credential mapped to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account is used.</span></span>  
  
 <span data-ttu-id="ddcf9-158">一个登录帐户可以映射多个凭据，只要它们用于不同的 EKM 访问接口即可。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-158">A login can have multiple credentials mapped to it, as long as they are used for distinctive EKM providers.</span></span> <span data-ttu-id="ddcf9-159">每个 EKM 访问接口的每个登录名只能存在一个映射的凭据。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-159">There must be only one mapped credential per EKM provider per login.</span></span> <span data-ttu-id="ddcf9-160">相同的凭据可以映射到其他登录名。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-160">The same credential can be mapped to other logins.</span></span>  
  
#### <a name="other-types-of-ekm-device-specific-authentication"></a><span data-ttu-id="ddcf9-161">其他类型的 EKM 设备特定的身份验证</span><span class="sxs-lookup"><span data-stu-id="ddcf9-161">Other Types of EKM Device-Specific Authentication</span></span>  
 <span data-ttu-id="ddcf9-162">对于身份验证不是采用 Windows 或用户/密码组合的 EKM 模块，必须单独从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 执行身份验证。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-162">For EKM modules that have authentication other than Windows or *user/password* combinations, authentication must be performed independently from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="encryption-and-decryption-by-an-ekm-device"></a><span data-ttu-id="ddcf9-163">通过 EKM 设备的加密和解密</span><span class="sxs-lookup"><span data-stu-id="ddcf9-163">Encryption and Decryption by an EKM Device</span></span>  
 <span data-ttu-id="ddcf9-164">下述功能和特性可用于通过对称和非对称密钥来加密和解密数据：</span><span class="sxs-lookup"><span data-stu-id="ddcf9-164">You can use the following functions and features to encrypt and decrypt data by using symmetric and asymmetric keys:</span></span>  
  
|<span data-ttu-id="ddcf9-165">功能</span><span class="sxs-lookup"><span data-stu-id="ddcf9-165">Function or feature</span></span>|<span data-ttu-id="ddcf9-166">参考</span><span class="sxs-lookup"><span data-stu-id="ddcf9-166">Reference</span></span>|  
|-------------------------|---------------|  
|<span data-ttu-id="ddcf9-167">对称密钥加密</span><span class="sxs-lookup"><span data-stu-id="ddcf9-167">Symmetric key encryption</span></span>|[<span data-ttu-id="ddcf9-168">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ddcf9-168">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-symmetric-key-transact-sql)|  
|<span data-ttu-id="ddcf9-169">非对称密钥加密</span><span class="sxs-lookup"><span data-stu-id="ddcf9-169">Asymmetric Key encryption</span></span>|[<span data-ttu-id="ddcf9-170">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ddcf9-170">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)|  
|<span data-ttu-id="ddcf9-171">EncryptByKey(key_guid, 'cleartext', ...)</span><span class="sxs-lookup"><span data-stu-id="ddcf9-171">EncryptByKey(key_guid, 'cleartext', ...)</span></span>|[<span data-ttu-id="ddcf9-172">ENCRYPTBYKEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ddcf9-172">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbykey-transact-sql)|  
|<span data-ttu-id="ddcf9-173">DecryptByKey(ciphertext, ...)</span><span class="sxs-lookup"><span data-stu-id="ddcf9-173">DecryptByKey(ciphertext, ...)</span></span>|[<span data-ttu-id="ddcf9-174">DECRYPTBYKEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ddcf9-174">DECRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/decryptbykey-transact-sql)|  
|<span data-ttu-id="ddcf9-175">EncryptByAsmKey(key_guid, 'cleartext')</span><span class="sxs-lookup"><span data-stu-id="ddcf9-175">EncryptByAsmKey(key_guid, 'cleartext')</span></span>|[<span data-ttu-id="ddcf9-176">ENCRYPTBYASYMKEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ddcf9-176">ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbyasymkey-transact-sql)|  
|<span data-ttu-id="ddcf9-177">DecryptByAsmKey(ciphertext)</span><span class="sxs-lookup"><span data-stu-id="ddcf9-177">DecryptByAsmKey(ciphertext)</span></span>|[<span data-ttu-id="ddcf9-178">DECRYPTBYASYMKEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ddcf9-178">DECRYPTBYASYMKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/decryptbyasymkey-transact-sql)|  
  
#### <a name="database-keys-encryption-by-ekm-keys"></a><span data-ttu-id="ddcf9-179">通过 EKM 密钥的数据库密钥加密</span><span class="sxs-lookup"><span data-stu-id="ddcf9-179">Database Keys Encryption by EKM Keys</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="ddcf9-180">可以使用 EKM 密钥加密数据库中的其他密钥。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-180">can use EKM keys to encrypt other keys in a database.</span></span> <span data-ttu-id="ddcf9-181">您可以在 EKM 设备上同时创建和使用对称密钥和非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-181">You can create and use both symmetric and asymmetric keys on an EKM device.</span></span> <span data-ttu-id="ddcf9-182">您可以使用 EKM 非对称密钥来加密本机（非 EKM）对称密钥。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-182">You can encrypt native (non-EKM) symmetric keys with EKM asymmetric keys.</span></span>  
  
 <span data-ttu-id="ddcf9-183">下面的示例将创建一个数据库对称密钥并使用 EKM 模块上的密钥对其进行加密。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-183">The following example creates a database symmetric key and encrypts it using a key on an EKM module.</span></span>  
  
```  
CREATE SYMMETRIC KEY Key1  
WITH ALGORITHM = AES_256  
ENCRYPTION BY EKM_AKey1;  
GO  
--Open database key  
OPEN SYMMETRIC KEY Key1  
DECRYPTION BY EKM_AKey1  
```  
  
 <span data-ttu-id="ddcf9-184">有关 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中数据库和服务器密钥的详细信息，请参阅 [SQL Server 和数据库加密密钥（数据库引擎）](sql-server-and-database-encryption-keys-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-184">For more information about Database and Server Keys in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [SQL Server and Database Encryption Keys &#40;Database Engine&#41;](sql-server-and-database-encryption-keys-database-engine.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ddcf9-185">您不能使用一个 EKM 密钥来加密另一个 EKM 密钥。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-185">You cannot encrypt one EKM key with another EKM key.</span></span>  
>   
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="ddcf9-186">不支持对具有从 EKM 提供程序生成的非对称密钥的模块签名。</span><span class="sxs-lookup"><span data-stu-id="ddcf9-186">does not support signing modules with asymmetric keys generated from EKM provider.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ddcf9-187">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ddcf9-187">Related Tasks</span></span>  
 [<span data-ttu-id="ddcf9-188">EKM provider enabled 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="ddcf9-188">EKM provider enabled Server Configuration Option</span></span>](../../../database-engine/configure-windows/ekm-provider-enabled-server-configuration-option.md)  
  
 [<span data-ttu-id="ddcf9-189">使用 EKM 启用 TDE</span><span class="sxs-lookup"><span data-stu-id="ddcf9-189">Enable TDE Using EKM</span></span>](enable-tde-on-sql-server-using-ekm.md)  
  
 [<span data-ttu-id="ddcf9-190">使用 Azure 密钥保管库的可扩展密钥管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ddcf9-190">Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;</span></span>](extensible-key-management-using-azure-key-vault-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="ddcf9-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ddcf9-191">See Also</span></span>  
 <span data-ttu-id="ddcf9-192">[CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-192">[CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-193">[DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL)](/sql/t-sql/statements/drop-cryptographic-provider-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-193">[DROP CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-cryptographic-provider-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-194">[ALTER CRYPTOGRAPHIC PROVIDER (Transact-SQL)](/sql/t-sql/statements/alter-cryptographic-provider-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-194">[ALTER CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-cryptographic-provider-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-195">[sys.cryptographic_providers (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-cryptographic-providers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-195">[sys.cryptographic_providers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-cryptographic-providers-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-196">[sys.dm_cryptographic_provider_sessions (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-sessions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-196">[sys.dm_cryptographic_provider_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-sessions-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-197">[sys.dm_cryptographic_provider_properties (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-properties-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-197">[sys.dm_cryptographic_provider_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-properties-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-198">[sys.dm_cryptographic_provider_algorithms (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-algorithms-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-198">[sys.dm_cryptographic_provider_algorithms &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-algorithms-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-199">[sys.dm_cryptographic_provider_keys (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-keys-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-199">[sys.dm_cryptographic_provider_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-keys-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-200">[sys.credentials (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-200">[sys.credentials &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-201">[CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-201">[CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-202">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-202">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-203">[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-203">[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-204">[ALTER ASYMMETRIC KEY (Transact-SQL)](/sql/t-sql/statements/alter-asymmetric-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-204">[ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-asymmetric-key-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-205">[DROP ASYMMETRIC KEY (Transact-SQL)](/sql/t-sql/statements/drop-asymmetric-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-205">[DROP ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-asymmetric-key-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-206">[CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-symmetric-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-206">[CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-symmetric-key-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-207">[ALTER SYMMETRIC KEY (Transact-SQL)](/sql/t-sql/statements/alter-symmetric-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-207">[ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-symmetric-key-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-208">[DROP SYMMETRIC KEY (Transact-SQL)](/sql/t-sql/statements/drop-symmetric-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-208">[DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-symmetric-key-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-209">[OPEN SYMMETRIC KEY (Transact-SQL)](/sql/t-sql/statements/open-symmetric-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-209">[OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-symmetric-key-transact-sql) </span></span>  
 <span data-ttu-id="ddcf9-210">[备份和还原 Reporting Services 加密密钥](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-210">[Back Up and Restore Reporting Services Encryption Keys](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span></span>  
 <span data-ttu-id="ddcf9-211">[删除和重新创建加密密钥（SSRS 配置管理器）](../../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-211">[Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](../../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span></span>  
 <span data-ttu-id="ddcf9-212">[添加和删除扩展部署的加密密钥（SSRS 配置管理器）](../../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-212">[Add and Remove Encryption Keys for Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md) </span></span>  
 <span data-ttu-id="ddcf9-213">[备份服务主密钥](service-master-key.md) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-213">[Back Up the Service Master Key](service-master-key.md) </span></span>  
 <span data-ttu-id="ddcf9-214">[还原服务主密钥](restore-the-service-master-key.md) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-214">[Restore the Service Master Key](restore-the-service-master-key.md) </span></span>  
 <span data-ttu-id="ddcf9-215">[创建数据库主密钥](create-a-database-master-key.md) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-215">[Create a Database Master Key](create-a-database-master-key.md) </span></span>  
 <span data-ttu-id="ddcf9-216">[备份数据库主密钥](back-up-a-database-master-key.md) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-216">[Back Up a Database Master Key](back-up-a-database-master-key.md) </span></span>  
 <span data-ttu-id="ddcf9-217">[还原数据库主密钥](restore-a-database-master-key.md) </span><span class="sxs-lookup"><span data-stu-id="ddcf9-217">[Restore a Database Master Key](restore-a-database-master-key.md) </span></span>  
 [<span data-ttu-id="ddcf9-218">在两个服务器上创建相同的对称密钥</span><span class="sxs-lookup"><span data-stu-id="ddcf9-218">Create Identical Symmetric Keys on Two Servers</span></span>](create-identical-symmetric-keys-on-two-servers.md)  
  
  
