---
title: 创建使用 Windows 身份验证的数据库镜像终结点 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- database mirroring [SQL Server], endpoint
- endpoints [SQL Server], database mirroring
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: baf1a4b1-6790-4275-b261-490bca33bdb9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5558bc5684f2eb9053c935543db0c05d6225daf7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579768"
---
# <a name="create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql"></a><span data-ttu-id="7ee11-102">创建使用 Windows 身份验证的数据库镜像端点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7ee11-102">Create a Database Mirroring Endpoint for Windows Authentication (Transact-SQL)</span></span>
  <span data-ttu-id="7ee11-103">本主题介绍如何创建一个数据库镜像端点，该端点通过 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="7ee11-103">This topic describes how to create a database mirroring endpoint that uses Windows Authentication in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7ee11-104">为了支持数据库镜像或 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] ， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的每个实例都需要一个数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="7ee11-104">To support database mirroring or [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires a database mirroring endpoint.</span></span> <span data-ttu-id="7ee11-105">一个服务器实例只能有一个数据库镜像端点，该端点有一个端口。</span><span class="sxs-lookup"><span data-stu-id="7ee11-105">A server instance can have only one database mirroring endpoint, which has a single port.</span></span> <span data-ttu-id="7ee11-106">在创建端点时，数据库镜像端点可以使用本地系统上任何可用的端口。</span><span class="sxs-lookup"><span data-stu-id="7ee11-106">A database mirroring endpoint can use any port that is available on the local system when the endpoint is created.</span></span> <span data-ttu-id="7ee11-107">服务器实例上的所有数据库镜像会话都侦听该端口，并且数据库镜像的所有传入连接都使用该端口。</span><span class="sxs-lookup"><span data-stu-id="7ee11-107">All database mirroring sessions on a server instance listen on that port, and all incoming connections for database mirroring use that port.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7ee11-108">如果数据库镜像端点已存在并处于使用状态，则我们建议您使用此端点。</span><span class="sxs-lookup"><span data-stu-id="7ee11-108">If a database mirroring endpoint exists and is already in use, we recommend that you use that endpoint.</span></span> <span data-ttu-id="7ee11-109">删除正在使用的端点会中断现有会话。</span><span class="sxs-lookup"><span data-stu-id="7ee11-109">Dropping an in-use endpoint disrupts existing sessions.</span></span>  
  
 <span data-ttu-id="7ee11-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="7ee11-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7ee11-111">**开始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="7ee11-111">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="7ee11-112">若要创建数据库镜像端点，请使用：[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="7ee11-112">**To create a database mirroring endpoint, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7ee11-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="7ee11-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7ee11-114">Security</span><span class="sxs-lookup"><span data-stu-id="7ee11-114">Security</span></span>  
 <span data-ttu-id="7ee11-115">服务器实例的身份验证和加密方法由系统管理员建立。</span><span class="sxs-lookup"><span data-stu-id="7ee11-115">The authentication and encryption methods of the server instance are established by the system administrator.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7ee11-116">不推荐使用 RC4 算法。</span><span class="sxs-lookup"><span data-stu-id="7ee11-116">The RC4 algorithm is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="7ee11-117">我们建议使用 AES。</span><span class="sxs-lookup"><span data-stu-id="7ee11-117">We recommend that you use AES.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7ee11-118">权限</span><span class="sxs-lookup"><span data-stu-id="7ee11-118">Permissions</span></span>  
 <span data-ttu-id="7ee11-119">要求具有 CREATE ENDPOINT 权限，或者具有 sysadmin 固定服务器角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="7ee11-119">Requires CREATE ENDPOINT permission, or membership in the sysadmin fixed server role.</span></span> <span data-ttu-id="7ee11-120">有关详细信息，请参阅 [GRANT 终结点权限 (Transact-SQL)](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7ee11-120">For more information, see [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7ee11-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7ee11-121">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-database-mirroring-endpoint-that-uses-windows-authentication"></a><span data-ttu-id="7ee11-122">创建使用 Windows 身份验证的数据库镜像端点</span><span class="sxs-lookup"><span data-stu-id="7ee11-122">To Create a Database Mirroring Endpoint That Uses Windows Authentication</span></span>  
  
1.  <span data-ttu-id="7ee11-123">连接至要为其创建数据库镜像端点的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="7ee11-123">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which you want to create a database mirroring endpoint.</span></span>  
  
2.  <span data-ttu-id="7ee11-124">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="7ee11-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7ee11-125">使用以下语句确定数据库镜像端点是否已经存在：</span><span class="sxs-lookup"><span data-stu-id="7ee11-125">Determine if a database mirroring endpoint already exists by using the following statement:</span></span>  
  
    ```sql
    SELECT name, role_desc, state_desc FROM sys.database_mirroring_endpoints;
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="7ee11-126">如果服务器实例已有数据库镜像端点，则可以将该端点用于在服务器实例上建立的任何其他会话。</span><span class="sxs-lookup"><span data-stu-id="7ee11-126">If a database mirroring endpoint already exists for the server instance, use that endpoint for any other sessions you establish on the server instance.</span></span>  
  
4.  <span data-ttu-id="7ee11-127">若要使用 Transact-SQL 创建使用 Windows 身份验证的端点，请使用 CREATE ENDPOINT 语句。</span><span class="sxs-lookup"><span data-stu-id="7ee11-127">To use Transact-SQL to create an endpoint to use with Windows Authentication, use a CREATE ENDPOINT statement.</span></span> <span data-ttu-id="7ee11-128">该语句采用以下常规形式：</span><span class="sxs-lookup"><span data-stu-id="7ee11-128">The statement takes the following general form:</span></span>  
  
     <span data-ttu-id="7ee11-129">CREATE ENDPOINT \<endpointName></span><span class="sxs-lookup"><span data-stu-id="7ee11-129">CREATE ENDPOINT *\<endpointName>*</span></span>  
  
     <span data-ttu-id="7ee11-130">STATE=STARTED</span><span class="sxs-lookup"><span data-stu-id="7ee11-130">STATE=STARTED</span></span>  
  
     <span data-ttu-id="7ee11-131">AS TCP ( LISTENER_PORT = \<listenerPortList> )</span><span class="sxs-lookup"><span data-stu-id="7ee11-131">AS TCP ( LISTENER_PORT = *\<listenerPortList>* )</span></span>  
  
     <span data-ttu-id="7ee11-132">FOR DATABASE_MIRRORING</span><span class="sxs-lookup"><span data-stu-id="7ee11-132">FOR DATABASE_MIRRORING</span></span>  
  
     <span data-ttu-id="7ee11-133">(</span><span class="sxs-lookup"><span data-stu-id="7ee11-133">(</span></span>  
  
     <span data-ttu-id="7ee11-134">[ AUTHENTICATION = WINDOWS [ \<authorizationMethod> ]</span><span class="sxs-lookup"><span data-stu-id="7ee11-134">[ AUTHENTICATION = **WINDOWS** [ *\<authorizationMethod>* ]</span></span>  
  
     <span data-ttu-id="7ee11-135">]</span><span class="sxs-lookup"><span data-stu-id="7ee11-135">]</span></span>  
  
     <span data-ttu-id="7ee11-136">[ [ **,** ] ENCRYPTION = **REQUIRED**</span><span class="sxs-lookup"><span data-stu-id="7ee11-136">[ [**,**] ENCRYPTION = **REQUIRED**</span></span>  
  
     <span data-ttu-id="7ee11-137">[ ALGORITHM { \<algorithm> } ]</span><span class="sxs-lookup"><span data-stu-id="7ee11-137">[ ALGORITHM { *\<algorithm>* } ]</span></span>  
  
     <span data-ttu-id="7ee11-138">]</span><span class="sxs-lookup"><span data-stu-id="7ee11-138">]</span></span>  
  
     <span data-ttu-id="7ee11-139">[,] ROLE = \<role></span><span class="sxs-lookup"><span data-stu-id="7ee11-139">[**,**] ROLE = *\<role>*</span></span>  
  
     <span data-ttu-id="7ee11-140">)</span><span class="sxs-lookup"><span data-stu-id="7ee11-140">)</span></span>  
  
     <span data-ttu-id="7ee11-141">其中</span><span class="sxs-lookup"><span data-stu-id="7ee11-141">where</span></span>  
  
    -   <span data-ttu-id="7ee11-142">\<endpointName> 是服务器实例的数据库镜像终结点的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="7ee11-142">*\<endpointName>* is a unique name for the database mirroring endpoint of the server instance.</span></span>  
  
    -   <span data-ttu-id="7ee11-143">STARTED 指定端点启动并开始侦听连接。</span><span class="sxs-lookup"><span data-stu-id="7ee11-143">STARTED specifies that the endpoint is to be started and to begin listening for connections.</span></span> <span data-ttu-id="7ee11-144">数据库镜像端点创建后通常处于 STARTED 状态。</span><span class="sxs-lookup"><span data-stu-id="7ee11-144">A database mirroring endpoint typically is created in the STARTED state.</span></span> <span data-ttu-id="7ee11-145">另外，可以启动处于 STOPPED 状态（默认值）或 DISABLED 状态中的会话。</span><span class="sxs-lookup"><span data-stu-id="7ee11-145">Alternatively, you can start a session in a STOPPED state (the default) or DISABLED state.</span></span>  
  
    -   <span data-ttu-id="7ee11-146">\<listenerPortList> 是需要服务器在其上侦听数据库镜像消息的单一端口号 (nnnn) 。</span><span class="sxs-lookup"><span data-stu-id="7ee11-146">*\<listenerPortList>* is a single port number (*nnnn*) on which you want the server to listen for database mirroring messages.</span></span> <span data-ttu-id="7ee11-147">只允许使用 TCP，指定任何其他协议都会导致发生错误。</span><span class="sxs-lookup"><span data-stu-id="7ee11-147">Only TCP is allowed; specifying any other protocol causes an error.</span></span>  
  
         <span data-ttu-id="7ee11-148">每个计算机系统一次只能使用一个端口号。</span><span class="sxs-lookup"><span data-stu-id="7ee11-148">A port number can be used only once per computer system.</span></span> <span data-ttu-id="7ee11-149">在创建端点时，数据库镜像端点可以使用本地系统上任何可用的端口。</span><span class="sxs-lookup"><span data-stu-id="7ee11-149">A database mirroring endpoint can use any port that is available on the local system when the endpoint is created.</span></span> <span data-ttu-id="7ee11-150">若要识别出系统上 TCP 端点当前使用的端口，请使用以下 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="7ee11-150">To identify the ports currently being used by TCP endpoints on the system, use the following Transact-SQL statement:</span></span>  
  
        ```  
        SELECT name, port FROM sys.tcp_endpoints;  
        ```  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="7ee11-151">每个服务器实例需要且只需要一个唯一的侦听器端口。</span><span class="sxs-lookup"><span data-stu-id="7ee11-151">Each server instance requires one and only one unique listener port.</span></span>  
  
    -   <span data-ttu-id="7ee11-152">对于 Windows 身份验证，AUTHENTICATION 选项是可选的，除非您只想让端点使用 NTLM 或 Kerberos 对连接进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="7ee11-152">For Windows Authentication, the AUTHENTICATION option is optional, unless you want the endpoint to use only NTLM or Kerberos to authenticate connections.</span></span> <span data-ttu-id="7ee11-153">\<authorizationMethod> 指定用于对连接进行身份验证的以下某种方法：NTLM、KERBEROS 或 NEGOTIATE。</span><span class="sxs-lookup"><span data-stu-id="7ee11-153">*\<authorizationMethod>* specifies the method used to authenticate connections as one of the following: NTLM, KERBEROS, or NEGOTIATE.</span></span> <span data-ttu-id="7ee11-154">默认方法 NEGOTIATE 会导致端点使用 Windows 协商协议来选择 NTLM 或 Kerberos。</span><span class="sxs-lookup"><span data-stu-id="7ee11-154">The default, NEGOTIATE, causes the endpoint to use the Windows negotiation protocol to choose either NTLM or Kerberos.</span></span> <span data-ttu-id="7ee11-155">根据另一侧端点的身份验证级别的不同，协商协议启用具有或没有身份验证的连接。</span><span class="sxs-lookup"><span data-stu-id="7ee11-155">Negotiation enables connections with or without authentication, depending on the authentication level of the opposite endpoint.</span></span>  
  
    -   <span data-ttu-id="7ee11-156">默认情况下，ENCRYPTION 设置为 REQUIRED。</span><span class="sxs-lookup"><span data-stu-id="7ee11-156">ENCRYPTION is set to REQUIRED by default.</span></span> <span data-ttu-id="7ee11-157">这意味着此端点的所有连接都必须加密。</span><span class="sxs-lookup"><span data-stu-id="7ee11-157">This means that all connections to this endpoint must use encryption.</span></span> <span data-ttu-id="7ee11-158">但您可以禁用加密，或对于端点可以选择禁用加密。</span><span class="sxs-lookup"><span data-stu-id="7ee11-158">However, you can disable encryption or make it optional on an endpoint.</span></span> <span data-ttu-id="7ee11-159">可以选择的选项如下：</span><span class="sxs-lookup"><span data-stu-id="7ee11-159">The alternatives are as follows:</span></span>  
  
        |<span data-ttu-id="7ee11-160">值</span><span class="sxs-lookup"><span data-stu-id="7ee11-160">Value</span></span>|<span data-ttu-id="7ee11-161">定义</span><span class="sxs-lookup"><span data-stu-id="7ee11-161">Definition</span></span>|  
        |-----------|----------------|  
        |<span data-ttu-id="7ee11-162">DISABLED</span><span class="sxs-lookup"><span data-stu-id="7ee11-162">DISABLED</span></span>|<span data-ttu-id="7ee11-163">指定不对通过连接发送的数据加密。</span><span class="sxs-lookup"><span data-stu-id="7ee11-163">Specifies that data sent over a connection is not encrypted.</span></span>|  
        |<span data-ttu-id="7ee11-164">SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="7ee11-164">SUPPORTED</span></span>|<span data-ttu-id="7ee11-165">指定只有在对方端点指定了 SUPPORTED 或者 REQUIRED 时，才加密数据。</span><span class="sxs-lookup"><span data-stu-id="7ee11-165">Specifies that the data is encrypted only if the opposite endpoint specifies either SUPPORTED or REQUIRED.</span></span>|  
        |<span data-ttu-id="7ee11-166">REQUIRED</span><span class="sxs-lookup"><span data-stu-id="7ee11-166">REQUIRED</span></span>|<span data-ttu-id="7ee11-167">指定必须对通过连接发送的数据加密。</span><span class="sxs-lookup"><span data-stu-id="7ee11-167">Specifies that data sent over a connection must be encrypted.</span></span>|  
  
         <span data-ttu-id="7ee11-168">如果端点要求加密，则对于其他端点，必须将 ENCRYPTION 设置为 SUPPORTED 或 REQUIRED。</span><span class="sxs-lookup"><span data-stu-id="7ee11-168">If an endpoint requires encryption, the other endpoint must have ENCRYPTION set to either SUPPORTED or REQUIRED.</span></span>  
  
    -   <span data-ttu-id="7ee11-169">\<algorithm> 提供为终结点指定加密标准的选项。</span><span class="sxs-lookup"><span data-stu-id="7ee11-169">*\<algorithm>* provides the option of specifying the encryption standards for the endpoint.</span></span> <span data-ttu-id="7ee11-170">\<algorithm> 的值可以是以下算法或这些算法的组合之一：RC4、AES、AES RC4 或 RC4 AES。</span><span class="sxs-lookup"><span data-stu-id="7ee11-170">The value of *\<algorithm>* can be one following algorithms or combinations of algorithms: RC4, AES, AES RC4, or RC4 AES.</span></span>  
  
         <span data-ttu-id="7ee11-171">AES RC4 指定此端点协商加密算法，但优先使用 AES 算法。</span><span class="sxs-lookup"><span data-stu-id="7ee11-171">AES RC4 specifies that this endpoint will negotiate for the encryption algorithm, giving preference to the AES algorithm.</span></span> <span data-ttu-id="7ee11-172">RC4 AES 指定此端点协商加密算法，但优先使用 RC4 算法。</span><span class="sxs-lookup"><span data-stu-id="7ee11-172">RC4 AES specifies that this endpoint will negotiate for the encryption algorithm, giving preference to the RC4 algorithm.</span></span> <span data-ttu-id="7ee11-173">如果两个端点都指定了这两种算法，但顺序不同，则接受连接的端点入选。</span><span class="sxs-lookup"><span data-stu-id="7ee11-173">If both endpoints specify both algorithms but in different orders, the endpoint accepting the connection wins.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="7ee11-174">不推荐使用 RC4 算法。</span><span class="sxs-lookup"><span data-stu-id="7ee11-174">The RC4 algorithm is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="7ee11-175">我们建议使用 AES。</span><span class="sxs-lookup"><span data-stu-id="7ee11-175">We recommend that you use AES.</span></span>  
  
    -   <span data-ttu-id="7ee11-176">\<role> 定义服务器可以执行的一个或多个角色。</span><span class="sxs-lookup"><span data-stu-id="7ee11-176">*\<role>* defines the role or roles that the server can perform.</span></span> <span data-ttu-id="7ee11-177">必须指定 ROLE。</span><span class="sxs-lookup"><span data-stu-id="7ee11-177">Specifying ROLE is required.</span></span> <span data-ttu-id="7ee11-178">不过，该端点的角色仅针对数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="7ee11-178">However, the role of the endpoint is relevant only for database mirroring.</span></span> <span data-ttu-id="7ee11-179">对于 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]，该端点的角色将被忽略。</span><span class="sxs-lookup"><span data-stu-id="7ee11-179">For [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], the role of the endpoint is ignored.</span></span>  
  
         <span data-ttu-id="7ee11-180">若要让服务器实例对于一个数据库镜像会话执行一个角色，对于另一个会话执行另一个角色，请指定 ROLE = ALL。</span><span class="sxs-lookup"><span data-stu-id="7ee11-180">To allow a server instance to serve as one role for one database mirroring session and different role for another session, specify ROLE=ALL.</span></span> <span data-ttu-id="7ee11-181">若要让服务器实例限于执行伙伴角色或见证角色，请分别指定 ROLE = PARTNER 或 ROLE = WITNESS。</span><span class="sxs-lookup"><span data-stu-id="7ee11-181">To restrict a server instance to being either a partner or a witness, specify ROLE=PARTNER or ROLE=WITNESS, respectively.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="7ee11-182">有关不同版本的的数据库镜像选项的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[SQL Server 2014 的各个版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="7ee11-182">For more information about Database Mirroring options for different editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
     <span data-ttu-id="7ee11-183">有关 CREATE ENDPOINT 语法的完整说明，请参阅 [CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql)中使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="7ee11-183">For a complete description of the CREATE ENDPOINT syntax, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7ee11-184">若要更改现有的端点，请使用 [ALTER ENDPOINT (Transact-SQL)](/sql/t-sql/statements/alter-endpoint-transact-sql)中使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="7ee11-184">To change an existing endpoint, use [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
###  <a name="example-creating-endpoints-to-support-for-database-mirroring-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="7ee11-185">示例：创建终结点以支持数据库镜像 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7ee11-185">Example: Creating Endpoints to Support for Database Mirroring (Transact-SQL)</span></span>  
 <span data-ttu-id="7ee11-186">下面的示例为三个不同的计算机系统上的默认服务器实例创建数据库镜像端点：</span><span class="sxs-lookup"><span data-stu-id="7ee11-186">The following example creates database mirroring endpoints for the default server instances on three separate computer systems:</span></span>  
  
|<span data-ttu-id="7ee11-187">服务器实例的角色</span><span class="sxs-lookup"><span data-stu-id="7ee11-187">Role of server instance</span></span>|<span data-ttu-id="7ee11-188">主机的名称</span><span class="sxs-lookup"><span data-stu-id="7ee11-188">Name of host computer</span></span>|  
|-----------------------------|---------------------------|  
|<span data-ttu-id="7ee11-189">伙伴（最初在主体角色中）</span><span class="sxs-lookup"><span data-stu-id="7ee11-189">Partner (initially in the principal role)</span></span>|`SQLHOST01\.`|  
|<span data-ttu-id="7ee11-190">伙伴（最初在镜像角色中）</span><span class="sxs-lookup"><span data-stu-id="7ee11-190">Partner (initially in the mirror role)</span></span>|`SQLHOST02\.`|  
|<span data-ttu-id="7ee11-191">见证</span><span class="sxs-lookup"><span data-stu-id="7ee11-191">Witness</span></span>|`SQLHOST03\.`|  
  
 <span data-ttu-id="7ee11-192">在本示例中，尽管任何可用的端口号都可以，但所有三个端点都使用端口号 7022。</span><span class="sxs-lookup"><span data-stu-id="7ee11-192">In this example, all three endpoints use port number 7022, though any available port number would work.</span></span> <span data-ttu-id="7ee11-193">AUTHENTICATION 选项是不必要的，因为端点使用默认类型，即 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="7ee11-193">The AUTHENTICATION option is unnecessary, because the endpoints use the default type, Windows Authentication.</span></span> <span data-ttu-id="7ee11-194">ENCRYPTION 选项也是不必要的，因为端点都打算通过协商来决定连接的身份验证方法，这是 Windows 身份验证的默认行为。</span><span class="sxs-lookup"><span data-stu-id="7ee11-194">The ENCRYPTION option is also unnecessary, because the endpoints are all intended to negotiate the authentication method for a connection, which is the default behavior for Windows Authentication.</span></span> <span data-ttu-id="7ee11-195">而且，所有端点都需要加密，这是默认行为。</span><span class="sxs-lookup"><span data-stu-id="7ee11-195">Also, all of the endpoints require the encryption, which is the default behavior.</span></span>  
  
 <span data-ttu-id="7ee11-196">每个服务器实例都只能作为伙伴或见证服务器，而每个服务器端点都明确指定了角色（ROLE=PARTNER 或 ROLE=WITNESS）。</span><span class="sxs-lookup"><span data-stu-id="7ee11-196">Each server instance is limited to serving as either a partner or a witness, and the endpoint of each server expressly specifies which role (ROLE=PARTNER or ROLE=WITNESS).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7ee11-197">每个服务器实例只能有一个端点。</span><span class="sxs-lookup"><span data-stu-id="7ee11-197">Each server instance can have only one endpoint.</span></span> <span data-ttu-id="7ee11-198">因此，如果您希望某个服务器实例在一些会话中作为伙伴，在另一些会话中作为见证服务器，请指定 ROLE=ALL。</span><span class="sxs-lookup"><span data-stu-id="7ee11-198">Therefore, if you want a server instance to be a partner in some sessions and the witness in others, specify ROLE=ALL.</span></span>  
  
```sql
--Endpoint for initial principal server instance, which  
--is the only server instance running on SQLHOST01.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=PARTNER);  
GO  
--Endpoint for initial mirror server instance, which  
--is the only server instance running on SQLHOST02.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=PARTNER);  
GO  
--Endpoint for witness server instance, which  
--is the only server instance running on SQLHOST03.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=WITNESS);  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="7ee11-199">相关任务</span><span class="sxs-lookup"><span data-stu-id="7ee11-199">Related Tasks</span></span>  

### <a name="to-configure-a-database-mirroring-endpoint"></a><span data-ttu-id="7ee11-200">配置数据库镜像端点</span><span class="sxs-lookup"><span data-stu-id="7ee11-200">To Configure a Database Mirroring Endpoint</span></span>
  
-   [<span data-ttu-id="7ee11-201">为 AlwaysOn 可用性组 &#40;SQL Server PowerShell 创建数据库镜像端点&#41;</span><span class="sxs-lookup"><span data-stu-id="7ee11-201">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](../availability-groups/windows/database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="7ee11-202">使用数据库镜像终结点证书 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7ee11-202">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [<span data-ttu-id="7ee11-203">允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7ee11-203">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [<span data-ttu-id="7ee11-204">允许数据库镜像终结点将证书用于入站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7ee11-204">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="7ee11-205">指定服务器网络地址（数据库镜像）</span><span class="sxs-lookup"><span data-stu-id="7ee11-205">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](specify-a-server-network-address-database-mirroring.md)  
  
-   [<span data-ttu-id="7ee11-206">在添加或修改可用性副本时指定终结点 URL (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7ee11-206">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](../availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="7ee11-207">**查看有关数据库镜像端点的信息**</span><span class="sxs-lookup"><span data-stu-id="7ee11-207">**To View Information About the Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="7ee11-208">sys.database_mirroring_endpoints (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7ee11-208">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="7ee11-209">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ee11-209">See Also</span></span>  
 <span data-ttu-id="7ee11-210">[ALTER ENDPOINT (Transact-SQL)](/sql/t-sql/statements/alter-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7ee11-210">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="7ee11-211">[选择加密算法](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="7ee11-211">[Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span></span>  
 <span data-ttu-id="7ee11-212">[CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7ee11-212">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="7ee11-213">[指定服务器网络地址（数据库镜像）](specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="7ee11-213">[Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md) </span></span>  
 <span data-ttu-id="7ee11-214">[示例：使用 Windows 身份验证设置数据库镜像 (Transact-SQL)](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="7ee11-214">[Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md) </span></span>  
 [<span data-ttu-id="7ee11-215">数据库镜像终结点 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7ee11-215">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](the-database-mirroring-endpoint-sql-server.md)  
