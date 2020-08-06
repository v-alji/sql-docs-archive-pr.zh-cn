---
title: 设置加密的镜像数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- database master key [SQL Server], database mirroring
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 7329a575-be29-46e0-abc6-1344db37920c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a5148411792f1ea881bba59e599252284575bbdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690097"
---
# <a name="set-up-an-encrypted-mirror-database"></a><span data-ttu-id="5f651-102">设置加密的镜像数据库</span><span class="sxs-lookup"><span data-stu-id="5f651-102">Set Up an Encrypted Mirror Database</span></span>

<span data-ttu-id="5f651-103">若要对镜像数据库的数据库主密钥启用自动解密，必须提供用于加密该镜像服务器实例的主密钥的口令。</span><span class="sxs-lookup"><span data-stu-id="5f651-103">To enable automatic decryption of the database master key of a mirror database, you must provide the password used to encrypt the master key to the mirror server instance.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="5f651-104">和更高版本包括传输密码的机制。</span><span class="sxs-lookup"><span data-stu-id="5f651-104">and later versions include mechanisms to transfer the password.</span></span> <span data-ttu-id="5f651-105">在开始数据库镜像之前，请使用 **sp_control_dbmasterkey_password** 为数据库主密钥创建一个凭据。</span><span class="sxs-lookup"><span data-stu-id="5f651-105">Use **sp_control_dbmasterkey_password** to create a credential for the database master key before you start database mirroring.</span></span> <span data-ttu-id="5f651-106">必须为要镜像的每个数据库重复此过程。</span><span class="sxs-lookup"><span data-stu-id="5f651-106">You must repeat this process for every database that will be mirrored.</span></span> <span data-ttu-id="5f651-107">有关详细信息，请参阅 [sp_control_dbmasterkey_password (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5f651-107">For more information, see [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql).</span></span>
  
> [!CAUTION]  
>  <span data-ttu-id="5f651-108">对于 **sa** 和其他特权级别高的服务器主体无法访问的数据库，不要启用其故障转移解密功能。</span><span class="sxs-lookup"><span data-stu-id="5f651-108">Do not enable failover decryption of a database that must remain inaccessible to **sa** and other highly privileged server principals.</span></span> <span data-ttu-id="5f651-109">可以对数据库进行配置，以便服务主密钥无法对其密钥层次结构进行解密。</span><span class="sxs-lookup"><span data-stu-id="5f651-109">You can configure a database so that its key hierarchy cannot be decrypted by the service master key.</span></span> <span data-ttu-id="5f651-110">对于包含 **sa** 或其他高特权服务器主体不应访问的信息的数据库来说，此选项是一项深层防御措施。</span><span class="sxs-lookup"><span data-stu-id="5f651-110">This option is supported as a defense-in-depth for databases that contain information that should not be accessible to **sa** or other highly privileged server principals.</span></span> <span data-ttu-id="5f651-111">为此类数据库启用故障转移解密将解除此深层防御措施，使 **sa** 和其他高特权服务器主体能够解密该数据库。</span><span class="sxs-lookup"><span data-stu-id="5f651-111">Enabling failover decryption of such a database removes this defense-in-depth, enabling **sa** and other highly privileged server principals to decrypt the database.</span></span>  


<!-- Note: We cannot append '?view=sql-server-2016' to these, even tho in theory we might want to. -->

## <a name="see-also"></a><span data-ttu-id="5f651-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f651-112">See Also</span></span>

[<span data-ttu-id="5f651-113">sp_control_dbmasterkey_password (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5f651-113">sp_control_dbmasterkey_password &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql)

[<span data-ttu-id="5f651-114">CREATE MASTER KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5f651-114">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)

[<span data-ttu-id="5f651-115">ALTER MASTER KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5f651-115">ALTER MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-master-key-transact-sql)

[<span data-ttu-id="5f651-116">加密层次结构</span><span class="sxs-lookup"><span data-stu-id="5f651-116">Encryption Hierarchy</span></span>](../../relational-databases/security/encryption/encryption-hierarchy.md)

[<span data-ttu-id="5f651-117">设置数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5f651-117">Setting Up Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)

