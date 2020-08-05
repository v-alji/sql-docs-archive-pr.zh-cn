---
title: 使用数据库镜像终结点证书 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- certificates [SQL Server], database mirroring
- authentication [SQL Server], database mirroring
- database mirroring [SQL Server], security
ms.assetid: f7c23cc2-48dc-4b78-b441-89ca29a0bd9e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c159e66e798524c41bf6e653283c299cc8393be5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580872"
---
# <a name="use-certificates-for-a-database-mirroring-endpoint-transact-sql"></a><span data-ttu-id="20339-102">使用数据库镜像端点证书 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="20339-102">Use Certificates for a Database Mirroring Endpoint (Transact-SQL)</span></span>
  <span data-ttu-id="20339-103">若要在给定的服务器实例上启用数据库镜像的证书验证，系统管理员必须配置每个服务器实例，以在出站连接和进站连接中使用证书。</span><span class="sxs-lookup"><span data-stu-id="20339-103">To enable certificate authentication for database mirroring on a given server instance, the system administrator must configure each server instance to use certificates on both outbound and inbound connections.</span></span> <span data-ttu-id="20339-104">必须先配置出站连接。</span><span class="sxs-lookup"><span data-stu-id="20339-104">Outbound connections must be configured first.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20339-105">服务器实例上的所有镜像连接都使用单个数据库镜像端点，必须在创建端点时指定服务器实例的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="20339-105">All mirroring connections on a server instance use a single database mirroring endpoint, and you must specify the authentication method of the server instance when you create the endpoint.</span></span> <span data-ttu-id="20339-106">因此，可以对数据库镜像的每个服务器实例只使用一种验证方式。</span><span class="sxs-lookup"><span data-stu-id="20339-106">Therefore, you can use only one form of authentication per server instance for database mirroring.</span></span>  
  
## <a name="configuring-outbound-connections"></a><span data-ttu-id="20339-107">配置出站连接</span><span class="sxs-lookup"><span data-stu-id="20339-107">Configuring Outbound Connections</span></span>  
 <span data-ttu-id="20339-108">在为数据库镜像配置的每个服务器实例上执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="20339-108">Follow these steps on each server instance that you are configuring for database mirroring:</span></span>  
  
1.  <span data-ttu-id="20339-109">在 **master** 数据库中，创建数据库主密钥。</span><span class="sxs-lookup"><span data-stu-id="20339-109">In the **master** database, create a database master key.</span></span>  
  
2.  <span data-ttu-id="20339-110">在 **master** 数据库中，为服务器实例创建加密证书。</span><span class="sxs-lookup"><span data-stu-id="20339-110">In the **master** database, create an encrypted certificate on the server instance.</span></span>  
  
3.  <span data-ttu-id="20339-111">使用服务器实例的证书为该服务器实例创建端点。</span><span class="sxs-lookup"><span data-stu-id="20339-111">Create an endpoint for the server instance using its certificate.</span></span>  
  
4.  <span data-ttu-id="20339-112">将证书备份到文件，并将其安全地复制到其他系统。</span><span class="sxs-lookup"><span data-stu-id="20339-112">Back up the certificate to a file and securely copy it to the other system or systems.</span></span>  
  
 <span data-ttu-id="20339-113">必须对每一个伙伴和见证服务器（如果存在）完成以上步骤。</span><span class="sxs-lookup"><span data-stu-id="20339-113">You must complete these steps for each partner and the witness, if there is one.</span></span>  
  
 <span data-ttu-id="20339-114">有关详细信息，请参阅 [允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)](database-mirroring-use-certificates-for-outbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="20339-114">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
## <a name="configuring-inbound-connections"></a><span data-ttu-id="20339-115">配置入站连接</span><span class="sxs-lookup"><span data-stu-id="20339-115">Configuring Inbound Connections</span></span>  
 <span data-ttu-id="20339-116">然后，对为数据库镜像配置的每个伙伴执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="20339-116">Next, follow these steps for each partner that you are configuring for database mirroring.</span></span> <span data-ttu-id="20339-117">在 **master** 数据库中：</span><span class="sxs-lookup"><span data-stu-id="20339-117">In the **master** database:</span></span>  
  
1.  <span data-ttu-id="20339-118">为其他系统创建登录名。</span><span class="sxs-lookup"><span data-stu-id="20339-118">Create a login for the other system.</span></span>  
  
2.  <span data-ttu-id="20339-119">创建一个使用该登录名的用户。</span><span class="sxs-lookup"><span data-stu-id="20339-119">Create a user for that login.</span></span>  
  
3.  <span data-ttu-id="20339-120">获取其他服务器实例的镜像端点的证书。</span><span class="sxs-lookup"><span data-stu-id="20339-120">Obtain the certificate for the mirroring endpoint of the other server instance.</span></span>  
  
4.  <span data-ttu-id="20339-121">将该证书与在步骤 2 中创建的用户相关联。</span><span class="sxs-lookup"><span data-stu-id="20339-121">Associate the certificate with the user created in step 2.</span></span>  
  
5.  <span data-ttu-id="20339-122">授予对该镜像端点的登录名的 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="20339-122">Grant CONNECT permission on the login for that mirroring endpoint.</span></span>  
  
 <span data-ttu-id="20339-123">如果存在见证服务器，还必须为见证服务器设置进站连接。</span><span class="sxs-lookup"><span data-stu-id="20339-123">If there is a witness, you must also set up inbound connections for it.</span></span> <span data-ttu-id="20339-124">这需要在两个伙伴上为见证服务器设置登录名、用户和证书，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="20339-124">This requires setting up logins, users, and certificates for the witness on both of the partners, and vice versa.</span></span>  
  
 <span data-ttu-id="20339-125">有关详细信息，请参阅 [允许数据库镜像终结点将证书用于入站连接 (Transact-SQL)](database-mirroring-use-certificates-for-inbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="20339-125">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="20339-126">安全性</span><span class="sxs-lookup"><span data-stu-id="20339-126">Security</span></span>  
 <span data-ttu-id="20339-127">建议您对数据库镜像连接进行加密，除非您能够保证网络的安全。</span><span class="sxs-lookup"><span data-stu-id="20339-127">Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections.</span></span> <span data-ttu-id="20339-128">有关详细信息，请参阅 [数据库镜像终结点 (SQL Server)](the-database-mirroring-endpoint-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="20339-128">For more information, see [The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md).</span></span>  
  
 <span data-ttu-id="20339-129">将证书复制到其他系统时，请使用安全的复制方法。</span><span class="sxs-lookup"><span data-stu-id="20339-129">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="20339-130">必须格外小心地保证所有证书的安全。</span><span class="sxs-lookup"><span data-stu-id="20339-130">Be extremely careful to keep all of your certificates secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20339-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20339-131">See Also</span></span>  
 <span data-ttu-id="20339-132">[创建数据库主密钥](../../relational-databases/security/encryption/create-a-database-master-key.md) </span><span class="sxs-lookup"><span data-stu-id="20339-132">[Create a Database Master Key](../../relational-databases/security/encryption/create-a-database-master-key.md) </span></span>  
 <span data-ttu-id="20339-133">[CREATE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/create-master-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20339-133">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span></span>  
 <span data-ttu-id="20339-134">[用于数据库镜像和 AlwaysOn 可用性组 &#40;SQL Server 的传输安全&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="20339-134">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="20339-135">[SQL Server 数据库引擎和 Azure SQL 数据库的安全中心](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md) </span><span class="sxs-lookup"><span data-stu-id="20339-135">[Security Center for SQL Server Database Engine and Azure SQL Database](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md) </span></span>  
 [<span data-ttu-id="20339-136">数据库镜像终结点 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20339-136">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](the-database-mirroring-endpoint-sql-server.md)  
  
  
