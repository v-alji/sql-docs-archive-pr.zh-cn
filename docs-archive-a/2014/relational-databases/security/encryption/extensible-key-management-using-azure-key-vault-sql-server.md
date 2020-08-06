---
title: 使用 Azure Key Vault 的可扩展密钥管理 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- EKM, with key vault
- TDE, EKM and key vault
- Extensible Key Management with key vault
- Key Management with key vault
- Transparent Data Encryption, using EKM and key vault
ms.assetid: 3efdc48a-8064-4ea6-a828-3fbf758ef97c
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 0e4bbc4f0c371c927988e6b91fdbf47307ad9d3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694424"
---
# <a name="extensible-key-management-using-azure-key-vault-sql-server"></a><span data-ttu-id="a178c-102">使用 Azure Key Vault 的可扩展密钥管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a178c-102">Extensible Key Management Using Azure Key Vault (SQL Server)</span></span>
  <span data-ttu-id="a178c-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]连接器 for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Azure Key Vault 允许 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密使用 Azure Key Vault 服务作为[可扩展密钥管理 &#40;EKM&#41;](extensible-key-management-ekm.md)提供程序，以保护其加密密钥。</span><span class="sxs-lookup"><span data-stu-id="a178c-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Azure Key Vault enables [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption to leverage the Azure Key Vault service as an [Extensible Key Management &#40;EKM&#41;](extensible-key-management-ekm.md) provider to protect its encryption keys.</span></span>

 <span data-ttu-id="a178c-104">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="a178c-104">Included in this topic:</span></span>

-   [<span data-ttu-id="a178c-105">使用 EKM</span><span class="sxs-lookup"><span data-stu-id="a178c-105">Uses of EKM</span></span>](#Uses)

-   [<span data-ttu-id="a178c-106">步骤 1：安装用于 SQL Server 的 Key Vault</span><span class="sxs-lookup"><span data-stu-id="a178c-106">Step 1: Setting up the Key Vault for use by SQL Server</span></span>](#Step1)

-   [<span data-ttu-id="a178c-107">步骤 2：安装 SQL Server Connector</span><span class="sxs-lookup"><span data-stu-id="a178c-107">Step 2: Installing the SQL Server Connector</span></span>](#Step2)

-   [<span data-ttu-id="a178c-108">步骤 3：配置 SQL Server，将 EKM 提供程序用于 Key Vault</span><span class="sxs-lookup"><span data-stu-id="a178c-108">Step 3: Configure SQL Server to use an EKM provider for the Key Vault</span></span>](#Step3)

-   [<span data-ttu-id="a178c-109">示例 A：通过使用 Key Vault 的非对称密钥实现透明数据加密</span><span class="sxs-lookup"><span data-stu-id="a178c-109">Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault</span></span>](#ExampleA)

-   [<span data-ttu-id="a178c-110">示例 B：通过使用 Key Vault 的非对称密钥加密备份文件</span><span class="sxs-lookup"><span data-stu-id="a178c-110">Example B: Encrypting Backups by Using an Asymmetric Key from the Key Vault</span></span>](#ExampleB)

-   [<span data-ttu-id="a178c-111">示例 C：通过使用 Key Vault 的非对称密钥实现列级加密</span><span class="sxs-lookup"><span data-stu-id="a178c-111">Example C: Column Level Encryption by Using an Asymmetric Key from the Key Vault</span></span>](#ExampleC)

##  <a name="uses-of-ekm"></a><a name="Uses"></a><span data-ttu-id="a178c-112">使用 EKM</span><span class="sxs-lookup"><span data-stu-id="a178c-112">Uses of EKM</span></span>
 <span data-ttu-id="a178c-113">组织可使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密来保护敏感数据。</span><span class="sxs-lookup"><span data-stu-id="a178c-113">An organization can use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption to protect sensitive data.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="a178c-114">加密包括[透明数据加密 &#40;TDE&#41;](transparent-data-encryption.md)、[列级加密](/sql/t-sql/functions/cryptographic-functions-transact-sql) (CLE) 和[备份加密](../../backup-restore/backup-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="a178c-114">encryption includes [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md), [Column Level Encryption](/sql/t-sql/functions/cryptographic-functions-transact-sql) (CLE), and [Backup Encryption](../../backup-restore/backup-encryption.md).</span></span> <span data-ttu-id="a178c-115">在这几种情况下，均使用对称数据加密密钥对数据进行加密。</span><span class="sxs-lookup"><span data-stu-id="a178c-115">In all of these cases the data is encrypted using a symmetric data encryption key.</span></span> <span data-ttu-id="a178c-116">通过使用存储在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中的密钥层次结构对对称数据加密密钥进行加密而使其获得进一步的保护。</span><span class="sxs-lookup"><span data-stu-id="a178c-116">The symmetric data encryption key is further protected by encrypting it with a hierarchy of keys stored in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a178c-117">或者，借助 EKM 提供程序体系结构， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可通过使用存储在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之外的一个外部加密提供程序中的非对称密钥来保护数据加密密钥。</span><span class="sxs-lookup"><span data-stu-id="a178c-117">Alternatively, the EKM provider architecture enables [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to protect the data encryption keys by using an asymmetric key stored outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in an external cryptographic provider.</span></span> <span data-ttu-id="a178c-118">使用 EKM 提供程序体系结构会额外提供一层安全保护，使组织可分开管理密钥和数据。</span><span class="sxs-lookup"><span data-stu-id="a178c-118">Using EKM provider architecture adds an additional layer of security and allows organizations to separate the management of keys and data.</span></span>

 <span data-ttu-id="a178c-119">借助适用于 Azure Key Vault 的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可以将此可扩展、高性能和高度可用的密钥保管库服务用作 EKM 提供程序以实现加密密钥保护。</span><span class="sxs-lookup"><span data-stu-id="a178c-119">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector for Azure Key Vault lets [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] leverage the scalable, high performance, and highly available key vault service as an EKM provider for encryption key protection.</span></span> <span data-ttu-id="a178c-120">密钥保管库服务可用于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Azure 虚拟机和本地服务器上的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 安装。</span><span class="sxs-lookup"><span data-stu-id="a178c-120">The key vault service can be used with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installations on [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Azure Virtual Machines and for on-premises servers.</span></span> <span data-ttu-id="a178c-121">Key Vault 服务还提供一种选择，即使用受到严格控制和监视的硬件安全模块 (HSM) 来实现对非对称加密密钥的更高级别的保护。</span><span class="sxs-lookup"><span data-stu-id="a178c-121">The key vault service also provides the option to use tightly controlled and monitored Hardware Security Modules (HSMs) for a higher level of protection for asymmetric encryption keys.</span></span> <span data-ttu-id="a178c-122">有关密钥保管库的详细信息，请参阅 [Azure 密钥保管库](https://go.microsoft.com/fwlink/?LinkId=521401)。</span><span class="sxs-lookup"><span data-stu-id="a178c-122">For more information about the key vault, see [Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521401).</span></span>

 <span data-ttu-id="a178c-123">下图总结了使用密钥保管库的 EKM 处理流程。</span><span class="sxs-lookup"><span data-stu-id="a178c-123">The following image summarizes the process flow of EKM using the key vault.</span></span> <span data-ttu-id="a178c-124">图中的处理步骤数与以下的设置步骤数并不一致。</span><span class="sxs-lookup"><span data-stu-id="a178c-124">The process step numbers in the image are not meant to match the setup step numbers that follow the image.</span></span>

 <span data-ttu-id="a178c-125">![使用 Azure Key Vault 的 SQL Server EKM](../../../database-engine/media/ekm-using-azure-key-vault.png "使用 Azure Key Vault 的 SQL Server EKM")</span><span class="sxs-lookup"><span data-stu-id="a178c-125">![SQL Server EKM using the Azure Key Vault](../../../database-engine/media/ekm-using-azure-key-vault.png "SQL Server EKM using the Azure Key Vault")</span></span>

##  <a name="step-1-set-up-the-key-vault-for-use-by-sql-server"></a><a name="Step1"></a><span data-ttu-id="a178c-126">步骤1：设置 Key Vault 以供 SQL Server 使用</span><span class="sxs-lookup"><span data-stu-id="a178c-126">Step 1: Set up the Key Vault for use by SQL Server</span></span>
 <span data-ttu-id="a178c-127">使用以下步骤设置 Key Vault，使其可与 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 一起使用来实现对加密密钥的保护。</span><span class="sxs-lookup"><span data-stu-id="a178c-127">Use the following steps to set up a key vault for use with the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] for encryption key protection.</span></span> <span data-ttu-id="a178c-128">组织可能已使用了某个保管库。</span><span class="sxs-lookup"><span data-stu-id="a178c-128">A vault may already be in use for the organization.</span></span> <span data-ttu-id="a178c-129">如果不存在保管库，则组织中指定管理加密密钥的 Azure 管理员可以创建一个保管库，在保管库中生成一个非对称密钥，然后授权 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用该密钥。</span><span class="sxs-lookup"><span data-stu-id="a178c-129">When a vault does not exist, the Azure Administrator in your organization that is designated to manage encryption keys can create a vault, generate an asymmetric key in the vault, and then authorize [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to use the key.</span></span> <span data-ttu-id="a178c-130">请查看 [Azure Key Vault 入门](https://go.microsoft.com/fwlink/?LinkId=521402)和 PowerShell [Azure Key Vault Cmdlet](https://docs.microsoft.com/powershell/module/azurerm.keyvault) 参考，详细了解 Key Vault 服务的相关内容。</span><span class="sxs-lookup"><span data-stu-id="a178c-130">To familiarize yourself with the key vault service review [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402), and the PowerShell [Azure Key Vault Cmdlets](https://docs.microsoft.com/powershell/module/azurerm.keyvault) reference.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="a178c-131">如果你拥有多个 Azure 订阅，则必须使用包含 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的订阅。</span><span class="sxs-lookup"><span data-stu-id="a178c-131">If you have multiple Azure subscriptions, you must use the subscription that contains [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

1.  <span data-ttu-id="a178c-132">**创建保管库：** 请使用 **Azure 密钥保管库入门** 中的 [创建密钥保管库](https://go.microsoft.com/fwlink/?LinkId=521402)部分中的说明来创建保管库。</span><span class="sxs-lookup"><span data-stu-id="a178c-132">**Create a vault:** Create a vault by using the instructions in the **Create a key vault** section of [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span> <span data-ttu-id="a178c-133">记录保管库的名称。</span><span class="sxs-lookup"><span data-stu-id="a178c-133">Record the name of the vault.</span></span> <span data-ttu-id="a178c-134">本主题将 **ContosoKeyVault** 作为 Key Vault 名称。</span><span class="sxs-lookup"><span data-stu-id="a178c-134">This topic uses **ContosoKeyVault** as the key vault name.</span></span>

2.  <span data-ttu-id="a178c-135">**在保管库中生成非对称密钥：** 密钥保管库中的非对称密钥用于保护 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密密钥。</span><span class="sxs-lookup"><span data-stu-id="a178c-135">**Generate an asymmetric key in the vault:** The asymmetric key in the key vault is used to protect [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption keys.</span></span> <span data-ttu-id="a178c-136">仅非对称密钥的公共部分会离开保管库，其私有部分绝不会由保管库导出。</span><span class="sxs-lookup"><span data-stu-id="a178c-136">Only the public portion of the asymmetric key ever leaves the vault, the private portion is never exported by the vault.</span></span> <span data-ttu-id="a178c-137">使用非对称密钥的所有加密操作都委托给了 Azure Key Vault，并受到 Key Vault 安全性的保护。</span><span class="sxs-lookup"><span data-stu-id="a178c-137">All cryptographic operations using the asymmetric key are delegated to the Azure Key Vault, and are protected by the key vault security.</span></span>

     <span data-ttu-id="a178c-138">你可通过若干方法生成不对称密钥并将其存储在保管库中。</span><span class="sxs-lookup"><span data-stu-id="a178c-138">There are several ways that you can generate an asymmetric key and store it in the vault.</span></span> <span data-ttu-id="a178c-139">你可在外部生成密钥，然后将其作为 .pfx 文件导入保管库。</span><span class="sxs-lookup"><span data-stu-id="a178c-139">You can externally generate a key, and import the key into the vault as a .pfx file.</span></span> <span data-ttu-id="a178c-140">或者使用密钥保管库 API 直接在保管库中创建密钥。</span><span class="sxs-lookup"><span data-stu-id="a178c-140">Or create the key directly in the vault by using the key vault APIs.</span></span>

     <span data-ttu-id="a178c-141">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 连接器要求非对称密钥为 2048 位 RSA，且密钥名称只能使用字符“a-z”、“A-Z”、“0-9”和“-”。</span><span class="sxs-lookup"><span data-stu-id="a178c-141">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector requires the asymmetric keys to be 2048-bit RSA, and the key name can only use the characters "a-z", "A-Z", "0-9", and "-".</span></span> <span data-ttu-id="a178c-142">在本文档中，非对称密钥名称被称为 **ContosoMasterKey**。</span><span class="sxs-lookup"><span data-stu-id="a178c-142">In this document the name of the asymmetric key is referred to as **ContosoMasterKey**.</span></span> <span data-ttu-id="a178c-143">将名称替换为你用于密钥的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="a178c-143">Replace this with the unique name you use for the key.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="a178c-144">强烈建议对生产情况导入非对称密钥，因为这样管理员就可以在密钥托管系统中托管密钥。</span><span class="sxs-lookup"><span data-stu-id="a178c-144">Importing the asymmetric key is highly recommended for production scenarios because it allows the administrator to escrow the key in a key escrow system.</span></span> <span data-ttu-id="a178c-145">如果非对称密钥是在保管库中创建的，则无法托管，因为私有密钥无法离开保管库。</span><span class="sxs-lookup"><span data-stu-id="a178c-145">If the asymmetric key is created in the vault, it cannot be escrowed because the private key can never leave the vault.</span></span> <span data-ttu-id="a178c-146">应托管用于保护关键数据的密钥。</span><span class="sxs-lookup"><span data-stu-id="a178c-146">Keys used to protect critical data should be escrowed.</span></span> <span data-ttu-id="a178c-147">丢失非对称密钥将导致数据永久性不可恢复。</span><span class="sxs-lookup"><span data-stu-id="a178c-147">The loss of an asymmetric key will result in permanently unrecoverable data.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="a178c-148">Key Vault 支持多个版本的具有相同命名的密钥。</span><span class="sxs-lookup"><span data-stu-id="a178c-148">The key vault supports multiple versions of the same named key.</span></span> <span data-ttu-id="a178c-149">不应设置 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 连接器要使用的密钥的版本或对其进行滚动。</span><span class="sxs-lookup"><span data-stu-id="a178c-149">Keys to be used by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector should not be versioned or rolled.</span></span> <span data-ttu-id="a178c-150">如果管理员想要滚动用于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密的密钥，则应在保管库中创建一个具有不同名称的新密钥并用它来加密 DEK。</span><span class="sxs-lookup"><span data-stu-id="a178c-150">If the administrator wants to roll the key used for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption, a new key with a different name should be created in the vault and used to encrypt the DEK.</span></span>

     <span data-ttu-id="a178c-151">若要详细了解如何将密钥导入 key vault 或在 key vault 中创建密钥 (不推荐用于生产环境) ，请参阅[Azure Key Vault 入门](https://go.microsoft.com/fwlink/?LinkId=521402)中的**向 key vault 添加密钥或机密**部分。</span><span class="sxs-lookup"><span data-stu-id="a178c-151">For more information on how to import a key into the key vault or to create a key in the key vault (not recommended for a production environment), see the **Add a key or secret to the key vault** section in [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span>

3.  <span data-ttu-id="a178c-152">**获取 Azure Active Directory 服务主体以用于 SQL Server：** 当组织注册 Microsoft 云服务时，即获取 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="a178c-152">**Get Azure Active Directory Service Principals to use for SQL Server:** When the organization signs up for a Microsoft cloud service, it gets an Azure Active Directory.</span></span> <span data-ttu-id="a178c-153">在 Azure Active Directory 中创建 **服务主体** 以供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 在访问 Key Vault 时使用（向 Azure Active Directory 验证自己的身份）。</span><span class="sxs-lookup"><span data-stu-id="a178c-153">Create **Service Principals** in the Azure Active Directory for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to use (to authenticate itself to Azure Active Directory) while accessing the key vault.</span></span>

    -   <span data-ttu-id="a178c-154">若要在配置 \*\*\*\* 以使用加密时访问保管库， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理员将需要一个服务主体 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a178c-154">One **Service Principal** will be needed by a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] administrator to access the vault while configuring [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to use encryption.</span></span>

    -   <span data-ttu-id="a178c-155">若要访问 \*\*\*\* 加密中使用的展开密钥的保管库， [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 将需要另一个服务主体 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a178c-155">Another **Service Principal** will be needed by the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] to access the vault for unwrapping keys used in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption.</span></span>

     <span data-ttu-id="a178c-156">有关如何注册应用程序和生成服务主体的详细信息，请参阅 **Azure Key Vault 入门** 中的 [向 Azure Active Directory 注册应用程序](https://go.microsoft.com/fwlink/?LinkId=521402)部分。</span><span class="sxs-lookup"><span data-stu-id="a178c-156">For more information about how to register an application and generate a service principal, see the **Register an Application with Azure Active Directory** section in [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span> <span data-ttu-id="a178c-157">注册过程将针对每一个 Azure Active Directory **服务主体** 返回一个 **应用程序 ID**（也称为 **客户端 ID** ）和一个 **身份验证密钥**（也称为 **Secret**）。</span><span class="sxs-lookup"><span data-stu-id="a178c-157">The registration process returns an **Application ID** (also known as a **CLIENT ID**) and a **Authentication Key** (also known as a **Secret**) for each Azure Active Directory **Service Principal**.</span></span> <span data-ttu-id="a178c-158">当在语句中使用时 `CREATE CREDENTIAL` ，必须从**客户端 ID**中删除连字符。</span><span class="sxs-lookup"><span data-stu-id="a178c-158">When used in the `CREATE CREDENTIAL` statement, the hyphen must be removed from the **CLIENT ID**.</span></span> <span data-ttu-id="a178c-159">记录这些密钥，以在下面的脚本中使用：</span><span class="sxs-lookup"><span data-stu-id="a178c-159">Record these for use in the scripts below:</span></span>

    -   <span data-ttu-id="a178c-160">\*\*\*\* 登录的 **服务主体** ： **CLIENTID_服务主体_login** 和 **SECRET_服务主体_login**</span><span class="sxs-lookup"><span data-stu-id="a178c-160">**Service Principal** for a **sysadmin** login: **CLIENTID_sysadmin_login** and **SECRET_sysadmin_login**</span></span>

    -   <span data-ttu-id="a178c-161">用于**的** 服务主体 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]: **CLIENTID_DBEngine** 和 **SECRET_DBEngine**。</span><span class="sxs-lookup"><span data-stu-id="a178c-161">**Service Principal** for the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]: **CLIENTID_DBEngine** and **SECRET_DBEngine**.</span></span>

4.  <span data-ttu-id="a178c-162">**授予服务主体访问密钥保管库的权限：** 和 **和\*\*\*\*服务主体** 均需要密钥保管库中的 **get**, **list**, **wrapKey**,  **unwrapKey** 权限。</span><span class="sxs-lookup"><span data-stu-id="a178c-162">**Grant Permission for the Service Principals to access the Key Vault:** Both the **CLIENTID_sysadmin_login** and **CLIENTID_DBEngineService Principals** require the **get**, **list**, **wrapKey**, and **unwrapKey** permissions in the key vault.</span></span> <span data-ttu-id="a178c-163">如果你打算通过 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 来创建密钥，则还需要授予 Key Vault 中的 **create** 权限。</span><span class="sxs-lookup"><span data-stu-id="a178c-163">If you intend to create keys through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] you also need to grant the **create** permission in key vault.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="a178c-164"> 用户至少必须拥有用于 Key Vault 的 **wrapKey** 和 **unwrapKey** 操作。</span><span class="sxs-lookup"><span data-stu-id="a178c-164">Users must have at least the **wrapKey** and **unwrapKey** operations for the key vault.</span></span>

     <span data-ttu-id="a178c-165">有关授予对保管库的权限的详细内容，请参阅 **Azure Key Vault 入门**[中的授权应用程序使用密钥或机密](https://go.microsoft.com/fwlink/?LinkId=521402)部分。</span><span class="sxs-lookup"><span data-stu-id="a178c-165">For more information about granting permissions to the vault, see the **Authorize the application to use the key or secret** section in [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span>

     <span data-ttu-id="a178c-166">链接至 Azure Key Vault 文档</span><span class="sxs-lookup"><span data-stu-id="a178c-166">Links to Azure Key Vault documentation</span></span>

    -   [<span data-ttu-id="a178c-167">什么是 Azure 密钥保管库？</span><span class="sxs-lookup"><span data-stu-id="a178c-167">What is Azure Key Vault?</span></span>](https://go.microsoft.com/fwlink/?LinkId=521401)

    -   [<span data-ttu-id="a178c-168">Azure Key Vault 入门</span><span class="sxs-lookup"><span data-stu-id="a178c-168">Get Started with Azure Key Vault</span></span>](https://go.microsoft.com/fwlink/?LinkId=521402)

    -   <span data-ttu-id="a178c-169">PowerShell [Azure 密钥保管库 Cmdlet](https://docs.microsoft.com/powershell/module/azurerm.keyvault) 参考</span><span class="sxs-lookup"><span data-stu-id="a178c-169">PowerShell [Azure Key Vault Cmdlets](https://docs.microsoft.com/powershell/module/azurerm.keyvault) reference</span></span>

##  <a name="step-2-install-the-sql-server-connector"></a><a name="Step2"></a><span data-ttu-id="a178c-170">步骤2：安装 SQL Server 连接器</span><span class="sxs-lookup"><span data-stu-id="a178c-170">Step 2: Install the SQL Server Connector</span></span>
 <span data-ttu-id="a178c-171">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 连接器是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 计算机的管理员下载和安装的。</span><span class="sxs-lookup"><span data-stu-id="a178c-171">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector is downloaded and installed by the administrator of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] computer.</span></span> <span data-ttu-id="a178c-172">可在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Microsoft 下载中心 [下载](https://go.microsoft.com/fwlink/p/?LinkId=521700)连接器。</span><span class="sxs-lookup"><span data-stu-id="a178c-172">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector is available as a download from the [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=521700).</span></span>  <span data-ttu-id="a178c-173">搜索 **适用于 Microsoft Azure Key Vault 的 SQL Server Connector**，查看详细内容、系统要求和安装说明，然后选择下载连接器并使用“运行” \*\*\*\* 开始进行安装。</span><span class="sxs-lookup"><span data-stu-id="a178c-173">Search for **SQL Server Connector for Microsoft Azure Key Vault**, review the details, system requirements and install instructions and choose to download the connector and start the installation using **Run**.</span></span> <span data-ttu-id="a178c-174">查看许可证，接受许可证，然后继续。</span><span class="sxs-lookup"><span data-stu-id="a178c-174">Review the license and accept the license and continue.</span></span>

 <span data-ttu-id="a178c-175">默认情况下，连接器安装在**C:\Program Files\SQL Server connector for Microsoft Azure Key Vault**。</span><span class="sxs-lookup"><span data-stu-id="a178c-175">By default the connector is installed at **C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault**.</span></span> <span data-ttu-id="a178c-176">可在设置过程中更改此位置。</span><span class="sxs-lookup"><span data-stu-id="a178c-176">This location can be changed during setup.</span></span> <span data-ttu-id="a178c-177">（若已更改，请调整以下脚本。）</span><span class="sxs-lookup"><span data-stu-id="a178c-177">(If changed, adjust the scripts below.)</span></span>

 <span data-ttu-id="a178c-178">安装完成时，以下内容将安装到计算机：</span><span class="sxs-lookup"><span data-stu-id="a178c-178">On completing the install, the following are installed on the machine:</span></span>

-   <span data-ttu-id="a178c-179">**Microsoft.AzureKeyVaultService.EKM.dll**:这是加密 EKM 提供程序 DLL，需要通过使用 CREATE CRYPTOGRAPHIC PROVIDER 语句与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 一起注册。</span><span class="sxs-lookup"><span data-stu-id="a178c-179">**Microsoft.AzureKeyVaultService.EKM.dll**: This is the cryptographic EKM provider DLL that needs to be registered with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using the CREATE CRYPTOGRAPHIC PROVIDER statement.</span></span>

-   <span data-ttu-id="a178c-180">**Azure Key Vault SQL Server Connector**：这是一个 Windows 服务，使加密 EKM 提供程序可以与 Key Vault 进行通信。</span><span class="sxs-lookup"><span data-stu-id="a178c-180">**Azure Key Vault SQL Server Connector**: This is a Windows service that enables the cryptographic EKM provider to communicate with the key vault.</span></span>

 <span data-ttu-id="a178c-181">借助 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 连接器安装，你还可以选择性地下载用于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密的示例脚本。</span><span class="sxs-lookup"><span data-stu-id="a178c-181">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector installation also allows you to optionally download sample scripts for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption.</span></span>

##  <a name="step-3-configure-sql-server-to-use-an-ekm-provider-for-the-key-vault"></a><a name="Step3"></a><span data-ttu-id="a178c-182">步骤3：将 SQL Server 配置为对 Key Vault 使用 EKM 提供程序</span><span class="sxs-lookup"><span data-stu-id="a178c-182">Step 3: Configure SQL Server to use an EKM provider for the Key Vault</span></span>

###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a178c-183">权限</span><span class="sxs-lookup"><span data-stu-id="a178c-183">Permissions</span></span>
 <span data-ttu-id="a178c-184">若要完成整个流程，需要具备 CONTROL SERVER 权限或 **sysadmin** 固定服务器角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="a178c-184">To complete this entire process requires CONTROL SERVER permission or membership in the **sysadmin** fixed server role.</span></span> <span data-ttu-id="a178c-185">特定操作要求具有以下权限：</span><span class="sxs-lookup"><span data-stu-id="a178c-185">Specific actions require the following permissions:</span></span>

-   <span data-ttu-id="a178c-186">若要创建加密提供程序，需要具备 CONTROL SERVER 权限或 **sysadmin** 固定服务器角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="a178c-186">To create a cryptographic provider, requires CONTROL SERVER permission or membership in the **sysadmin** fixed server role.</span></span>

-   <span data-ttu-id="a178c-187">若要更改配置选项以及运行 RECONFIGURE 语句，您必须具有 ALTER SETTINGS 服务器级别权限。</span><span class="sxs-lookup"><span data-stu-id="a178c-187">To change a configuration option and run the RECONFIGURE statement, you must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="a178c-188">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="a178c-188">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>

-   <span data-ttu-id="a178c-189">若要创建凭据，则需要 ALTER ANY CREDENTIAL 权限。</span><span class="sxs-lookup"><span data-stu-id="a178c-189">To create a credential, requires ALTER ANY CREDENTIAL permission.</span></span>

-   <span data-ttu-id="a178c-190">若要向登录添加凭据，需要 ALTER ANY LOGIN 权限。</span><span class="sxs-lookup"><span data-stu-id="a178c-190">To add a credential to a login, requires ALTER ANY LOGIN permission.</span></span>

-   <span data-ttu-id="a178c-191">若要创建非对称密钥，需要 CREATE ASYMMETRIC KEY 权限。</span><span class="sxs-lookup"><span data-stu-id="a178c-191">To create an asymmetric key, requires CREATE ASYMMETRIC KEY permission.</span></span>

###  <a name="to-configure-sql-server-to-use-a-cryptographic-provider"></a><a name="TsqlProcedure"></a><span data-ttu-id="a178c-192">将 SQL Server 配置为使用加密提供程序</span><span class="sxs-lookup"><span data-stu-id="a178c-192">To configure SQL Server to use a cryptographic provider</span></span>

1.  <span data-ttu-id="a178c-193">配置 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 以使用 EKM，并对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]注册（创建）加密提供程序。</span><span class="sxs-lookup"><span data-stu-id="a178c-193">Configure the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to use EKM, and register (create) the cryptographic provider with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

    ```sql
    -- Enable advanced options.
    USE master;
    GO

    sp_configure 'show advanced options', 1 ;
    GO
    RECONFIGURE ;
    GO
    -- Enable EKM provider
    sp_configure 'EKM provider enabled', 1 ;
    GO
    RECONFIGURE ;
    GO

    -- Create a cryptographic provider, using the SQL Server Connector
    -- which is an EKM provider for the Azure Key Vault. This example uses 
    -- the name AzureKeyVault_EKM_Prov.

    CREATE CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov 
    FROM FILE = 'C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll';
    GO
    ```

2.  <span data-ttu-id="a178c-194">安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 凭据，使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理员可以登录使用 Key Vault，以便安装和管理 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密方案。</span><span class="sxs-lookup"><span data-stu-id="a178c-194">Setup a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] credential for a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] administrator login to use the key vault in order to setup and manage [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption scenarios.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="a178c-195">的**标识**参数 `CREATE CREDENTIAL` 需要密钥保管库名称。</span><span class="sxs-lookup"><span data-stu-id="a178c-195">The **IDENTITY** argument of `CREATE CREDENTIAL` requires the key vault name.</span></span> <span data-ttu-id="a178c-196">的**机密**参数 `CREATE CREDENTIAL` 需要 *\<Client ID>* 不带连字符) 的 (，并 *\<Secret>* 将它们一起传递时不使用空格。</span><span class="sxs-lookup"><span data-stu-id="a178c-196">The **SECRET** argument of `CREATE CREDENTIAL` requires the *\<Client ID>* (without hyphens) and *\<Secret>* to be passed together without a space between them.</span></span>

     <span data-ttu-id="a178c-197">在下面的示例中，**客户端 ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) 去除连字符，并输入为字符串 `EF5C8E094D2A4A769998D93440D8115D` ，并且**机密**由字符串*SECRET_sysadmin_login*表示。</span><span class="sxs-lookup"><span data-stu-id="a178c-197">In the following example, the **Client ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) is stripped of the hyphens and entered as the string `EF5C8E094D2A4A769998D93440D8115D` and the **Secret** is represented by the string *SECRET_sysadmin_login*.</span></span>

    ```sql
    USE master;
    CREATE CREDENTIAL sysadmin_ekm_cred 
        WITH IDENTITY = 'ContosoKeyVault', 
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_sysadmin_login' 
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;

    -- Add the credential to the SQL Server administrators domain login 
    ALTER LOGIN [<domain>/<login>]
    ADD CREDENTIAL sysadmin_ekm_cred;
    ```

     <span data-ttu-id="a178c-198">有关使用参数的变量 `CREATE CREDENTIAL` 和以编程方式从客户端 ID 中删除连字符的示例，请参阅[CREATE CREDENTIAL &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a178c-198">For an example of using variables for the `CREATE CREDENTIAL` arguments and programmatically removing the hyphens from the Client ID, see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).</span></span>

3.  <span data-ttu-id="a178c-199">如果按照上述章节 3 步骤 1 中所述导入了一个非对称密钥，请通过在下例中提供密钥名称来打开密钥。</span><span class="sxs-lookup"><span data-stu-id="a178c-199">If you imported an asymmetric key as described earlier in step 1, section 3, open the key by providing your key name in the following example.</span></span>

    ```sql
    CREATE ASYMMETRIC KEY CONTOSO_KEY 
    FROM PROVIDER [AzureKeyVault_EKM_Prov]
    WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',
    CREATION_DISPOSITION = OPEN_EXISTING;
    ```

     <span data-ttu-id="a178c-200">虽然不建议用于生产（因为无法导出密钥），但还是可以从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]直接在保管库中创建非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="a178c-200">Though not recommended for production (because the key cannot be exported), it is possible to create an asymmetric key directly in the vault from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a178c-201">如果之前未导入密钥，请使用以下脚本在 key vault 中创建一个用于测试的非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="a178c-201">If you did not import a key earlier, then create an asymmetric key in the key vault for testing by using the following script.</span></span> <span data-ttu-id="a178c-202">使用 **sysadmin_ekm_cred** 凭据随附的登录来执行脚本。</span><span class="sxs-lookup"><span data-stu-id="a178c-202">Execute the script, using a login provisioned with the **sysadmin_ekm_cred** credential.</span></span>

    ```sql
    CREATE ASYMMETRIC KEY CONTOSO_KEY 
    FROM PROVIDER [AzureKeyVault_EKM_Prov]
    WITH ALGORITHM = RSA_2048,
    PROVIDER_KEY_NAME = 'ContosoMasterKey';
    ```

> [!TIP]
>  <span data-ttu-id="a178c-203">用户收到错误 **无法从提供程序中导出公钥。提供程序错误代码：2053。**</span><span class="sxs-lookup"><span data-stu-id="a178c-203">Users receiving the error **Cannot export public key from the provider. Provider error code: 2053.**</span></span> <span data-ttu-id="a178c-204">应在密钥保管库中检查它们的 **get**、 **list**、 **wrapKey**、 and **unwrapKey** 权限。</span><span class="sxs-lookup"><span data-stu-id="a178c-204">should check their **get**, **list**, **wrapKey**, and **unwrapKey** permissions in the key vault.</span></span>

 <span data-ttu-id="a178c-205">有关详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="a178c-205">For more information, see the following:</span></span>

-   [<span data-ttu-id="a178c-206">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a178c-206">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)

-   [<span data-ttu-id="a178c-207">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a178c-207">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)

-   [<span data-ttu-id="a178c-208">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a178c-208">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-credential-transact-sql)

-   [<span data-ttu-id="a178c-209">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a178c-209">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)

-   [<span data-ttu-id="a178c-210">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a178c-210">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)

-   [<span data-ttu-id="a178c-211">ALTER LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a178c-211">ALTER LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-login-transact-sql)

## <a name="examples"></a><span data-ttu-id="a178c-212">示例</span><span class="sxs-lookup"><span data-stu-id="a178c-212">Examples</span></span>

###  <a name="example-a-transparent-data-encryption-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleA"></a><span data-ttu-id="a178c-213">示例 A：通过使用 Key Vault 中的非对称密钥透明数据加密</span><span class="sxs-lookup"><span data-stu-id="a178c-213">Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault</span></span>
 <span data-ttu-id="a178c-214">完成以上步骤后，创建一个凭据和一个登录，然后创建一个受 Key Vault 中非对称密钥保护的数据库加密密钥。</span><span class="sxs-lookup"><span data-stu-id="a178c-214">After completing the steps above, create a credential and a login, create a database encryption key protected by the asymmetric key in the key vault.</span></span> <span data-ttu-id="a178c-215">使用数据库加密密钥对带 TDE 的数据库进行加密。</span><span class="sxs-lookup"><span data-stu-id="a178c-215">Use the database encryption key to encrypt a database with TDE.</span></span>

 <span data-ttu-id="a178c-216">若要加密数据库，需要对数据库的 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="a178c-216">To encrypt a database requires CONTROL permission on the database.</span></span>

##### <a name="to-enable-tde-using-ekm-and-the-key-vault"></a><span data-ttu-id="a178c-217">使用 EKM 和 Key Vault 启用 TDE</span><span class="sxs-lookup"><span data-stu-id="a178c-217">To enable TDE using EKM and the Key Vault</span></span>

1.  <span data-ttu-id="a178c-218">创建 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 凭据，以供 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 在数据库加载期间访问 key vault EKM 时使用。</span><span class="sxs-lookup"><span data-stu-id="a178c-218">Create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] credential for the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to use when accessing the key vault EKM during database load.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="a178c-219">的**标识**参数 `CREATE CREDENTIAL` 需要密钥保管库名称。</span><span class="sxs-lookup"><span data-stu-id="a178c-219">The **IDENTITY** argument of `CREATE CREDENTIAL` requires the key vault name.</span></span> <span data-ttu-id="a178c-220">的**机密**参数 `CREATE CREDENTIAL` 需要 *\<Client ID>* 不带连字符) 的 (，并 *\<Secret>* 将它们一起传递时不使用空格。</span><span class="sxs-lookup"><span data-stu-id="a178c-220">The **SECRET** argument of `CREATE CREDENTIAL` requires the *\<Client ID>* (without hyphens) and *\<Secret>* to be passed together without a space between them.</span></span>

     <span data-ttu-id="a178c-221">在下例中， **客户端 ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) 去掉了连字符，并输入为字符串 `EF5C8E094D2A4A769998D93440D8115D` ，而 **Secret** 则表示为字符串 *SECRET_DBEngine*。</span><span class="sxs-lookup"><span data-stu-id="a178c-221">In the following example, the **Client ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) is stripped of the hyphens and entered as the string `EF5C8E094D2A4A769998D93440D8115D` and the **Secret** is represented by the string *SECRET_DBEngine*.</span></span>

    ```sql
    USE master;
    CREATE CREDENTIAL Azure_EKM_TDE_cred 
        WITH IDENTITY = 'ContosoKeyVault', 
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine' 
        FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;
    ```

2.  <span data-ttu-id="a178c-222">创建一个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录以便 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 将其用于 TDE，并对其添加凭据。</span><span class="sxs-lookup"><span data-stu-id="a178c-222">Create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login to be used by the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] for TDE, and add the credential to it.</span></span> <span data-ttu-id="a178c-223">此示例使用存储在 key vault 中的 CONTOSO_KEY 非对称密钥，该密钥是之前如上面的 [章节 3 步骤 3](#Step3) 中所述为主数据库导入或创建的。</span><span class="sxs-lookup"><span data-stu-id="a178c-223">This example uses the CONTOSO_KEY asymmetric key stored in the key vault, which was imported or created earlier for the master database, as described in [Step 3, section 3](#Step3) above.</span></span>

    ```sql
    USE master;
    -- Create a SQL Server login associated with the asymmetric key 
    -- for the Database engine to use when it loads a database 
    -- encrypted by TDE.
    CREATE LOGIN TDE_Login 
    FROM ASYMMETRIC KEY CONTOSO_KEY;
    GO 

    -- Alter the TDE Login to add the credential for use by the 
    -- Database Engine to access the key vault
    ALTER LOGIN TDE_Login 
    ADD CREDENTIAL Azure_EKM_TDE_cred ;
    GO
    ```

3.  <span data-ttu-id="a178c-224">创建将用于 TDE 的数据库加密密钥 (DEK)。</span><span class="sxs-lookup"><span data-stu-id="a178c-224">Create the database encryption key (DEK) that will be used for TDE.</span></span> <span data-ttu-id="a178c-225">可使用任何 SQL Server 支持的算法或密钥长度来创建 DEK。</span><span class="sxs-lookup"><span data-stu-id="a178c-225">The DEK can be created using any SQL Server supported algorithm or key length.</span></span> <span data-ttu-id="a178c-226">DEK 将受到 key vault 中的非对称密钥保护。</span><span class="sxs-lookup"><span data-stu-id="a178c-226">The DEK will be protected by the asymmetric key in the key vault.</span></span>

     <span data-ttu-id="a178c-227">此示例使用存储在 key vault 中的 CONTOSO_KEY 非对称密钥，该密钥是之前如上面的 [章节 3 步骤 3](#Step3) 中所述导入或创建的。</span><span class="sxs-lookup"><span data-stu-id="a178c-227">This example uses the CONTOSO_KEY asymmetric key stored in the key vault, which was imported or created earlier, as described in [Step 3, section 3](#Step3) above.</span></span>

    ```sql
    USE ContosoDatabase;
    GO

    CREATE DATABASE ENCRYPTION KEY 
    WITH ALGORITHM = AES_128 
    ENCRYPTION BY SERVER ASYMMETRIC KEY CONTOSO_KEY;
    GO

    -- Alter the database to enable transparent data encryption.
    ALTER DATABASE ContosoDatabase 
    SET ENCRYPTION ON ;
    GO
    ```

     <span data-ttu-id="a178c-228">有关详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="a178c-228">For more information, see the following:</span></span>

    -   [<span data-ttu-id="a178c-229">CREATE DATABASE ENCRYPTION KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a178c-229">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)

    -   [<span data-ttu-id="a178c-230">ALTER DATABASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a178c-230">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)

###  <a name="example-b-encrypting-backups-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleB"></a><span data-ttu-id="a178c-231">示例 B：使用 Key Vault 中的非对称密钥加密备份</span><span class="sxs-lookup"><span data-stu-id="a178c-231">Example B: Encrypting Backups by Using an Asymmetric Key from the Key Vault</span></span>
 <span data-ttu-id="a178c-232">从 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]开始支持加密备份。</span><span class="sxs-lookup"><span data-stu-id="a178c-232">Encrypted backups are supported starting with [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="a178c-233">以下示例创建并还原了经过数据加密密钥加密的备份文件，其中该加密密钥受到 key vault 中的非加密密钥保护。</span><span class="sxs-lookup"><span data-stu-id="a178c-233">The following example creates and restores a backup encrypted a data encryption key protected by the asymmetric key in the key vault.</span></span>

```sql
USE master;
BACKUP DATABASE [DATABASE_TO_BACKUP]
TO DISK = N'[PATH TO BACKUP FILE]' 
WITH FORMAT, INIT, SKIP, NOREWIND, NOUNLOAD, 
ENCRYPTION(ALGORITHM = AES_256, SERVER ASYMMETRIC KEY = [CONTOSO_KEY]);
GO
```

 <span data-ttu-id="a178c-234">还原代码示例。</span><span class="sxs-lookup"><span data-stu-id="a178c-234">Sample restore code.</span></span>

```sql
RESTORE DATABASE [DATABASE_TO_BACKUP]
FROM DISK = N'[PATH TO BACKUP FILE]' WITH FILE = 1, NOUNLOAD, REPLACE;
GO
```

 <span data-ttu-id="a178c-235">有关备份选项的详细信息，请参阅[backup &#40;transact-sql&#41;](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a178c-235">For more information about backup options, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>

###  <a name="example-c-column-level-encryption-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleC"></a><span data-ttu-id="a178c-236">示例 C：通过使用 Key Vault 中的非对称密钥进行列级加密</span><span class="sxs-lookup"><span data-stu-id="a178c-236">Example C: Column Level Encryption by Using an Asymmetric Key from the Key Vault</span></span>
 <span data-ttu-id="a178c-237">以下示例创建了受 key vault 中非对称密钥保护的对称密钥。</span><span class="sxs-lookup"><span data-stu-id="a178c-237">The following example creates a symmetric key protected by the asymmetric key in the key vault.</span></span> <span data-ttu-id="a178c-238">然后该对称密钥用于对数据库中的数据进行加密。</span><span class="sxs-lookup"><span data-stu-id="a178c-238">Then the symmetric key is used to encrypt data in the database.</span></span>

 <span data-ttu-id="a178c-239">此示例使用存储在 key vault 中的 CONTOSO_KEY 非对称密钥，该密钥是之前如上面的 [章节 3 步骤 3](#Step3) 中所述导入或创建的。</span><span class="sxs-lookup"><span data-stu-id="a178c-239">This example uses the CONTOSO_KEY asymmetric key stored in the key vault, which was imported or created earlier, as described in [Step 3, section 3](#Step3) above.</span></span> <span data-ttu-id="a178c-240">若要在 `ContosoDatabase` 数据库中使用此非对称密钥，必须再次执行 CREATE ASYMMETRIC KEY 语句，为 `ContosoDatabase` 数据库提供对该密钥的引用。</span><span class="sxs-lookup"><span data-stu-id="a178c-240">To use this asymmetric key in the `ContosoDatabase` database, you must execute the CREATE ASYMMETRIC KEY statement again, to provide the `ContosoDatabase` database with a reference to the key.</span></span>

```sql
USE [ContosoDatabase];
GO

-- Create a reference to the key in the key vault
CREATE ASYMMETRIC KEY CONTOSO_KEY 
FROM PROVIDER [AzureKeyVault_EKM_Prov]
WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',
CREATION_DISPOSITION = OPEN_EXISTING;

-- Create the data encryption key.
-- The data encryption key can be created using any SQL Server 
-- supported algorithm or key length.
-- The DEK will be protected by the asymmetric key in the key vault

CREATE SYMMETRIC KEY DATA_ENCRYPTION_KEY
    WITH ALGORITHM=AES_256
    ENCRYPTION BY ASYMMETRIC KEY CONTOSO_KEY;

DECLARE @DATA VARBINARY(MAX);

--Open the symmetric key for use in this session
OPEN SYMMETRIC KEY DATA_ENCRYPTION_KEY 
DECRYPTION BY ASYMMETRIC KEY CONTOSO_KEY;

--Encrypt syntax
SELECT @DATA = ENCRYPTBYKEY(KEY_GUID('DATA_ENCRYPTION_KEY'), CONVERT(VARBINARY,'Plain text data to encrypt'));

-- Decrypt syntax
SELECT CONVERT(VARCHAR, DECRYPTBYKEY(@DATA));

--Close the symmetric key
CLOSE SYMMETRIC KEY DATA_ENCRYPTION_KEY;
```

## <a name="see-also"></a><span data-ttu-id="a178c-241">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a178c-241">See Also</span></span>
 <span data-ttu-id="a178c-242">[创建加密提供程序 &#40;transact-sql&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql) [Create CREDENTIAL &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [Create 非对称密钥 &#40;transact-sql&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) [Create 对称密钥 &#40;transact-sql&#41;](/sql/t-sql/statements/create-symmetric-key-transact-sql) [可扩展密钥管理 &#40;EKM&#41;](extensible-key-management-ekm.md) [使用 ekm](enable-tde-on-sql-server-using-ekm.md) [备份加密](../../backup-restore/backup-encryption.md)[创建加密的备份](../../backup-restore/create-an-encrypted-backup.md)</span><span class="sxs-lookup"><span data-stu-id="a178c-242">[CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-symmetric-key-transact-sql) [Extensible Key Management &#40;EKM&#41;](extensible-key-management-ekm.md) [Enable TDE Using EKM](enable-tde-on-sql-server-using-ekm.md) [Backup Encryption](../../backup-restore/backup-encryption.md) [Create an Encrypted Backup](../../backup-restore/create-an-encrypted-backup.md)</span></span>
