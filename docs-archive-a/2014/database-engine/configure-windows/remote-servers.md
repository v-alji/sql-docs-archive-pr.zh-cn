---
title: 远程服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- server management [SQL Server], remote servers
- remote servers [SQL Server], configuring
- remote servers [SQL Server]
- servers [SQL Server], remote
- remote access option
ms.assetid: abf0fa24-f199-4273-9a1a-e8787ac9bee1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1d42fc2ed6acd4e46e383c0a56afcc8a8b27d3aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586969"
---
# <a name="remote-servers"></a><span data-ttu-id="5eaa5-102">远程服务器</span><span class="sxs-lookup"><span data-stu-id="5eaa5-102">Remote Servers</span></span>
  <span data-ttu-id="5eaa5-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中支持远程服务器只是为了向后兼容。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-103">Remote servers are supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for backward compatibility only.</span></span> <span data-ttu-id="5eaa5-104">新应用程序应该改用链接服务器。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-104">New applications should use linked servers instead.</span></span> <span data-ttu-id="5eaa5-105">有关详细信息，请参阅 [链接服务器（数据库引擎）](../../relational-databases/linked-servers/linked-servers-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-105">For more information, see [Linked Servers &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md).</span></span>  
  
 <span data-ttu-id="5eaa5-106">远程服务器配置使客户端能够连接到一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，以便在没有建立单独的连接的情况下在其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上执行存储过程。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-106">A remote server configuration allows for a client connected to one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute a stored procedure on another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without establishing a separate connection.</span></span> <span data-ttu-id="5eaa5-107">此时，客户端所连接的服务器接受客户端的请求，并代表客户端将该请求发送到远程服务器。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-107">Instead, the server to which the client is connected accepts the client request and sends the request to the remote server on behalf of the client.</span></span> <span data-ttu-id="5eaa5-108">远程服务器处理请求，并将所有结果返回到原始的服务器。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-108">The remote server processes the request and returns any results to the original server.</span></span> <span data-ttu-id="5eaa5-109">服务器再将那些结果传递给客户端。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-109">This server in turn passes those results to the client.</span></span> <span data-ttu-id="5eaa5-110">当设置远程服务器配置时，还应考虑如何建立安全性。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-110">When you set up a remote server configuration, you should also consider how to establish security.</span></span>  
  
 <span data-ttu-id="5eaa5-111">如果要设置服务器配置以在另一台服务器上执行存储过程，但是没有现有的远程服务器配置，请使用链接服务器而不要使用远程服务器。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-111">If you want to set up a server configuration to execute stored procedures on another server and do not have existing remote server configurations, use linked servers instead of remote servers.</span></span> <span data-ttu-id="5eaa5-112">您可以对链接服务器执行存储过程和分布式查询；但对远程服务器只能执行存储过程。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-112">Both stored procedures and distributed queries are allowed against linked servers; however, only stored procedures are allowed against remote servers.</span></span>  
  
## <a name="remote-server-details"></a><span data-ttu-id="5eaa5-113">远程服务器详细信息</span><span class="sxs-lookup"><span data-stu-id="5eaa5-113">Remote Server Details</span></span>  
 <span data-ttu-id="5eaa5-114">远程服务器是成对设置的。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-114">Remote servers are set up in pairs.</span></span> <span data-ttu-id="5eaa5-115">若要设置一对远程服务器，请将这两台服务器配置为彼此将对方识别为远程服务器。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-115">To set up a pair of remote servers, configure both servers to recognize each other as remote servers.</span></span>  
  
 <span data-ttu-id="5eaa5-116">大多数情况下，不需要为远程服务器设置配置选项。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-116">Most of the time, you should not have to set configuration options for remote servers.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5eaa5-117">组将在本地计算机和远程计算机上设置默认值以允许远程服务器连接。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-117">Set sets the defaults on both the local and remote computers to allow for remote server connections.</span></span>  
  
 <span data-ttu-id="5eaa5-118">为了能够进行远程访问，必须在本地和远程计算机上将 **remote access** 配置选项设置为 1。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-118">For remote server access to work, the **remote access** configuration option must be set to 1 on both the local and remote computers.</span></span> <span data-ttu-id="5eaa5-119">（这是默认设置。）  **remote access** 控制远程服务器的登录。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-119">(This is the default setting.)  **remote access** controls logins from remote servers.</span></span> <span data-ttu-id="5eaa5-120">可以通过使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] sp_configure 存储过程或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 来重置此配置选项。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-120">You can reset this configuration option by using either the [!INCLUDE[tsql](../../includes/tsql-md.md)] **sp_configure** stored procedure or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="5eaa5-121">若要在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中设置选项，请在 **“服务器属性连接”** 页上，使用 **“允许远程连接到此服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-121">To set the option in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **Server Properties Connections** page, use **Allow remote connections to this server**.</span></span> <span data-ttu-id="5eaa5-122">若要访问“服务器属性连接”页，请在对象资源管理器中右键单击服务器名称，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-122">To reach the **Server Properties Connections** page, in Object Explorer, right-click the server name, and then click **Properties**.</span></span> <span data-ttu-id="5eaa5-123">在 **“服务器属性”** 页上，单击 **“连接”** 页。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-123">On the **Server Properties** page, click the **Connections** page.</span></span>  
  
 <span data-ttu-id="5eaa5-124">在本地服务器中，您可以禁用远程服务器配置，以防止远程服务器中的用户对与其配对的本地服务器进行访问。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-124">From the local server, you can disable a remote server configuration to prevent access to that local server by users on the remote server with which it is paired.</span></span>  
  
## <a name="security-for-remote-servers"></a><span data-ttu-id="5eaa5-125">远程服务器的安全性</span><span class="sxs-lookup"><span data-stu-id="5eaa5-125">Security for Remote Servers</span></span>  
 <span data-ttu-id="5eaa5-126">若要为远程服务器启用远程过程调用 (RPC)，必须在远程服务器中设置登录映射，并尽可能在运行有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的本地服务器中设置登录映射。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-126">To enable remote procedure calls (RPC) against a remote server, you must set up login mappings on the remote server and possibly on the local server that is running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5eaa5-127">默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中禁用 RPC。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-127">RPC is disabled by default in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5eaa5-128">此配置通过减少服务器的可攻击外围应用来增强其安全性。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-128">This configuration enhances the security of your server by reducing its attackable surface area.</span></span> <span data-ttu-id="5eaa5-129">使用 RPC 前必须启用此功能。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-129">Before using RPC you must enable this feature.</span></span> <span data-ttu-id="5eaa5-130">有关详细信息，请参阅 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-130">For more information see [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>  
  
### <a name="setting-up-the-remote-server"></a><span data-ttu-id="5eaa5-131">设置远程服务器</span><span class="sxs-lookup"><span data-stu-id="5eaa5-131">Setting Up the Remote Server</span></span>  
 <span data-ttu-id="5eaa5-132">必须在远程服务器上设置远程登录映射。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-132">Remote login mappings must be set up on the remote server.</span></span> <span data-ttu-id="5eaa5-133">使用这些映射，远程服务器可将某个特定服务器为建立 RPC 连接而传入的登录帐户映射到本地登录帐户。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-133">Using these mappings, the remote server maps the incoming login for an RPC connection from a specified server to a local login.</span></span> <span data-ttu-id="5eaa5-134">可以使用 **sp_addremotelogin** 存储过程在远程服务器上设置远程登录映射。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-134">Remote login mappings can be set up by using the **sp_addremotelogin** stored procedure on the remote server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5eaa5-135">**中不支持** sp_remoteoption  **的** trusted [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]选项。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-135">The **trusted** option of  **sp_remoteoption** is not supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="setting-up-the-local-server"></a><span data-ttu-id="5eaa5-136">设置本地服务器</span><span class="sxs-lookup"><span data-stu-id="5eaa5-136">Setting Up the Local Server</span></span>  
 <span data-ttu-id="5eaa5-137">对于经过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证的本地登录帐户，不必在本地服务器上设置登录映射。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-137">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated local logins, you do not have to set up a login mapping on the local server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5eaa5-138">使用本地登录名和密码连接到远程服务器。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-138">uses the local login and password to connect to the remote server.</span></span> <span data-ttu-id="5eaa5-139">对于经过 Windows 身份验证的登录帐户，可以在定义 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例与远程服务器建立 RPC 连接时使用的登录名和密码的本地服务器上设置本地登录映射。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-139">For Windows authenticated logins, set up a local login mapping on a local server that defines what login and password are used by an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when it makes an RPC connection to a remote server.</span></span>  
  
 <span data-ttu-id="5eaa5-140">对于 Windows 身份验证创建的登录帐户，必须使用 **sp_addlinkedservlogin** 存储过程创建到登录名和密码的映射。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-140">For logins created by Windows Authentication, you must create a mapping to a login name and password by using the **sp_addlinkedservlogin** stored procedure.</span></span> <span data-ttu-id="5eaa5-141">此登录名和密码必须与远程服务器预期的传入登录名和密码（由 **sp_addremotelogin**所创建）相匹配。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-141">This login name and password must match the incoming login and password expected by the remote server, as created by **sp_addremotelogin**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5eaa5-142">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-142">When possible, use Windows Authentication.</span></span>  
  
### <a name="remote-server-security-example"></a><span data-ttu-id="5eaa5-143">远程服务器安全性示例</span><span class="sxs-lookup"><span data-stu-id="5eaa5-143">Remote Server Security Example</span></span>  
 <span data-ttu-id="5eaa5-144">以下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装为例： **serverSend** 和 **serverReceive**。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-144">Consider these [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations: **serverSend** and **serverReceive**.</span></span> <span data-ttu-id="5eaa5-145">配置 **serverReceive** 以将传入登录名从 **serverSend**（称为 **Sales_Mary**）映射到 **serverReceive**（称为 **Alice**）中的经过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证的登录名。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-145">**serverReceive** is configured to map an incoming login from **serverSend**, called **Sales_Mary**, to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated login in **serverReceive**, called **Alice**.</span></span> <span data-ttu-id="5eaa5-146">将另一个传入帐户从 **serverSend**（称为 **Joe**）映射到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serverReceive  _（称为_ Joe **）中的经过**身份验证的登录帐户。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-146">Another incoming login from **serverSend**, called **Joe**, is mapped to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated login in **serverReceive**_,_ called **Joe**.</span></span>  
  
 <span data-ttu-id="5eaa5-147">下面的 Transact-SQL 代码示例将 `serverSend` 配置为对 `serverReceive` 执行 RPC。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-147">The following Transact-SQL code example configures `serverSend` to perform RPCs against `serverReceive`.</span></span>  
  
```  
--Create remote server entry for RPCs   
--from serverSend in serverReceive.  
EXEC sp_addserver 'serverSend';  
GO  
  
--Create remote login mapping for login 'Sales_Mary' from serverSend  
--to Alice.  
EXEC sp_addremotelogin 'serverSend', 'Alice', 'Sales_Mary';  
GO  
--Create remote login mapping for login Joe from serverReceive   
--to same login.  
--Assumes same password for Joe in both servers.  
EXEC sp_addremotelogin 'serverSend', 'Joe', 'Joe';  
GO  
```  
  
 <span data-ttu-id="5eaa5-148">在 `serverSend`上创建本地登录映射，以便将经过 Windows 身份验证的登录帐户 `Sales\Mary` 映射到登录帐户 `Sales_Mary`。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-148">On `serverSend`, a local login mapping is created for a Windows authenticated login `Sales\Mary` to a login `Sales_Mary`.</span></span> <span data-ttu-id="5eaa5-149">`Joe`不需要本地映射，因为默认设置使用相同的登录名和密码，并且 `serverReceive` 中有 `Joe`的映射。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-149">No local mapping is required for `Joe`, because the default is to use the same login name and password, and `serverReceive` has a mapping for `Joe`.</span></span>  
  
```  
--Create a remote server entry for RPCs from serverReceive.  
EXEC sp_addserver 'serverReceive';  
GO  
--Create a local login mapping for the Windows authenticated login.  
--Sales\Mary to Sales_Mary. The password should match the  
--password for the login Sales_Mary in serverReceive.  
EXEC sp_addlinkedsrvlogin 'serverReceive', false, 'Sales\Mary',  
   'Sales_Mary', '430[fj%dk';  
GO  
```  
  
## <a name="viewing-local-or-remote-server-properties"></a><span data-ttu-id="5eaa5-150">查看本地或远程服务器属性</span><span class="sxs-lookup"><span data-stu-id="5eaa5-150">Viewing Local or Remote Server Properties</span></span>  
 <span data-ttu-id="5eaa5-151">可以使用 **xp_msver** 扩展存储过程来查看本地或远程服务器属性。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-151">You can use the **xp_msver** extended stored procedure to review server attributes for local or remote servers.</span></span> <span data-ttu-id="5eaa5-152">这些属性包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的版本号、计算机中的处理器类型和数目以及操作系统的版本。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-152">These attributes include the version number of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the type and number of processors in the computer, and the version of the operating system.</span></span> <span data-ttu-id="5eaa5-153">从本地服务器可以查看远程服务器的数据库、文件、登录和工具。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-153">From the local server, you can view databases, files, logins, and tools for a remote server.</span></span> <span data-ttu-id="5eaa5-154">有关详细信息，请参阅 [xp_msver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/xp-msver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5eaa5-154">For more information, see [xp_msver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/xp-msver-transact-sql).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="5eaa5-155">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="5eaa5-155">Related Tasks</span></span>  
 [<span data-ttu-id="5eaa5-156">链接服务器（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="5eaa5-156">Linked Servers &#40;Database Engine&#41;</span></span>](../../relational-databases/linked-servers/linked-servers-database-engine.md)  
  
## <a name="related-content"></a><span data-ttu-id="5eaa5-157">相关内容</span><span class="sxs-lookup"><span data-stu-id="5eaa5-157">Related Content</span></span>  
 [<span data-ttu-id="5eaa5-158">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5eaa5-158">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
 [<span data-ttu-id="5eaa5-159">配置远程访问服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="5eaa5-159">Configure the remote access Server Configuration Option</span></span>](configure-the-remote-access-server-configuration-option.md)  
  
 [<span data-ttu-id="5eaa5-160">RECONFIGURE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5eaa5-160">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
