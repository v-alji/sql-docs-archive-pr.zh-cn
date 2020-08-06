---
title: 服务器属性（“安全性”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.security.f1
ms.assetid: b8a131c7-e7bd-4203-bf26-234f1ebfe622
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5f45c0a04a0d7cc627901d8de24175f1d63a99fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591581"
---
# <a name="server-properties-security-page"></a><span data-ttu-id="67054-102">服务器属性（“安全性”页）</span><span class="sxs-lookup"><span data-stu-id="67054-102">Server Properties (Security Page)</span></span>
  <span data-ttu-id="67054-103">使用此页可以查看或修改服务器安全选项。</span><span class="sxs-lookup"><span data-stu-id="67054-103">Use this page to view or modify your server security options.</span></span>  
  
## <a name="server-authentication"></a><span data-ttu-id="67054-104">服务器身份验证</span><span class="sxs-lookup"><span data-stu-id="67054-104">Server Authentication</span></span>  
 <span data-ttu-id="67054-105">**Windows 身份验证模式**</span><span class="sxs-lookup"><span data-stu-id="67054-105">**Windows Authentication mode**</span></span>  
 <span data-ttu-id="67054-106">使用 Windows 身份验证对所尝试的连接进行验证。</span><span class="sxs-lookup"><span data-stu-id="67054-106">Uses Windows Authentication to validate attempted connections.</span></span> <span data-ttu-id="67054-107">更改安全模式时，如果 **sa** 密码为空白，系统就会提示用户输入 **sa** 密码。</span><span class="sxs-lookup"><span data-stu-id="67054-107">If the **sa** password is blank when the security mode is being changed, the user is prompted to enter an **sa** password.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="67054-108">Windows 身份验证比 SQL Server 身份验证更加安全。</span><span class="sxs-lookup"><span data-stu-id="67054-108">Windows Authentication is much more secure than SQL Server Authentication.</span></span> <span data-ttu-id="67054-109">请尽量使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="67054-109">When possible, you should use Windows Authentication.</span></span>  
  
 <span data-ttu-id="67054-110">**SQL Server 和 Windows 身份验证模式**</span><span class="sxs-lookup"><span data-stu-id="67054-110">**SQL Server and Windows Authentication mode**</span></span>  
 <span data-ttu-id="67054-111">使用混合模式的身份验证对所尝试的连接进行验证，以便向后兼容早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="67054-111">Uses mixed mode authentication to verify attempted connections, for backward compatibility with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="67054-112">更改安全模式时，如果 **sa** 密码为空白，系统就会提示用户输入 **sa** 密码。</span><span class="sxs-lookup"><span data-stu-id="67054-112">If the **sa** password is blank when the security mode is being changed, the user is prompted to enter an **sa** password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67054-113">更改安全性配置后需要重新启动服务。</span><span class="sxs-lookup"><span data-stu-id="67054-113">Changing the security configuration requires a restart of the service.</span></span> <span data-ttu-id="67054-114">将服务器身份验证改为 SQL Server 和 Windows 身份验证模式时，不会自动启用 SA 帐户。</span><span class="sxs-lookup"><span data-stu-id="67054-114">When changing the Server Authentication to SQL Server and Windows Authentication mode the SA account is not automatically enabled.</span></span> <span data-ttu-id="67054-115">若要使用 SA 帐户，请执行带有 ENABLE 选项的 [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) 命令。</span><span class="sxs-lookup"><span data-stu-id="67054-115">To use the SA account, execute [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) with the ENABLE option.</span></span>  
  
## <a name="login-auditing"></a><span data-ttu-id="67054-116">登录审核</span><span class="sxs-lookup"><span data-stu-id="67054-116">Login Auditing</span></span>  
 <span data-ttu-id="67054-117">无</span><span class="sxs-lookup"><span data-stu-id="67054-117">**None**</span></span>  
 <span data-ttu-id="67054-118">关闭登录审核。</span><span class="sxs-lookup"><span data-stu-id="67054-118">Turns off login auditing.</span></span>  
  
 <span data-ttu-id="67054-119">**仅限失败的登录**</span><span class="sxs-lookup"><span data-stu-id="67054-119">**Failed logins only**</span></span>  
 <span data-ttu-id="67054-120">仅审核未成功的登录。</span><span class="sxs-lookup"><span data-stu-id="67054-120">Audits unsuccessful logins only.</span></span>  
  
 <span data-ttu-id="67054-121">**仅限成功的登录**</span><span class="sxs-lookup"><span data-stu-id="67054-121">**Successful logins only**</span></span>  
 <span data-ttu-id="67054-122">仅审核成功的登录。</span><span class="sxs-lookup"><span data-stu-id="67054-122">Audits successful logins only.</span></span>  
  
 <span data-ttu-id="67054-123">**成功和失败的登录**</span><span class="sxs-lookup"><span data-stu-id="67054-123">**Both failed and successful logins**</span></span>  
 <span data-ttu-id="67054-124">审核所有登录尝试。</span><span class="sxs-lookup"><span data-stu-id="67054-124">Audits all login attempts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67054-125">更改审核级别后需要重新启动服务。</span><span class="sxs-lookup"><span data-stu-id="67054-125">Changing the audit level requires restarting the service.</span></span>  
  
## <a name="server-proxy-account"></a><span data-ttu-id="67054-126">服务器代理帐户</span><span class="sxs-lookup"><span data-stu-id="67054-126">Server Proxy Account</span></span>  
 <span data-ttu-id="67054-127">**启用服务器代理帐户**</span><span class="sxs-lookup"><span data-stu-id="67054-127">**Enable server proxy account**</span></span>  
 <span data-ttu-id="67054-128">启用供 **xp_cmdshell**使用的帐户。</span><span class="sxs-lookup"><span data-stu-id="67054-128">Enables an account for use by **xp_cmdshell**.</span></span> <span data-ttu-id="67054-129">在执行操作系统命令时，代理帐户可模拟登录、服务器角色和数据库角色。</span><span class="sxs-lookup"><span data-stu-id="67054-129">Proxy accounts allow for the impersonation of logins, server roles, and database roles when an operating system command is being executed.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="67054-130">服务器代理帐户所用的登录帐户应该只具有执行既定工作所需的最低权限。</span><span class="sxs-lookup"><span data-stu-id="67054-130">The login used by the server proxy account should have the least privileges required to perform the intended work.</span></span> <span data-ttu-id="67054-131">代理帐户的权限过大有可能会被恶意用户利用，从而危及系统安全。</span><span class="sxs-lookup"><span data-stu-id="67054-131">Excessive privileges for the proxy account could be used by a malicious user to compromise your system security.</span></span>  
  
 <span data-ttu-id="67054-132">**代理帐户**</span><span class="sxs-lookup"><span data-stu-id="67054-132">**Proxy account**</span></span>  
 <span data-ttu-id="67054-133">指定所使用的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="67054-133">Specify the proxy account used.</span></span>  
  
 <span data-ttu-id="67054-134">**密码**</span><span class="sxs-lookup"><span data-stu-id="67054-134">**Password**</span></span>  
 <span data-ttu-id="67054-135">指定代理帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="67054-135">Specify the password for the proxy account.</span></span>  
  
## <a name="options"></a><span data-ttu-id="67054-136">选项</span><span class="sxs-lookup"><span data-stu-id="67054-136">Options</span></span>  
 <span data-ttu-id="67054-137">**启用 C2 审核跟踪**</span><span class="sxs-lookup"><span data-stu-id="67054-137">**Enable C2 audit tracing**</span></span>  
 <span data-ttu-id="67054-138">审核对语句和对象的所有访问尝试，并记录到文件中，对于默认 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例，该文件位于 \MSSQL\Data 目录中，对于*命名实例，该文件位于 \MSSQL$* instancename [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Data 目录中。</span><span class="sxs-lookup"><span data-stu-id="67054-138">Audits all attempts to access statements and objects and records them to a file in the \MSSQL\Data directory for default instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or the \MSSQL$*instancename*\Data directory for named instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="67054-139">有关详细信息，请参阅 [c2 审核模式服务器配置选项](c2-audit-mode-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="67054-139">For more information, see [c2 audit mode Server Configuration Option](c2-audit-mode-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="67054-140">**跨数据库所有权链接**</span><span class="sxs-lookup"><span data-stu-id="67054-140">**Cross database ownership chaining**</span></span>  
 <span data-ttu-id="67054-141">选中此项将允许数据库成为跨数据库所有权链的源或目标。</span><span class="sxs-lookup"><span data-stu-id="67054-141">Select to allow the database to be the source or target of a cross-database ownership chain.</span></span> <span data-ttu-id="67054-142">有关详细信息，请参阅 [跨数据库所有权链接服务器配置选项](cross-db-ownership-chaining-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="67054-142">For more information, see [cross db ownership chaining Server Configuration Option](cross-db-ownership-chaining-server-configuration-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67054-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67054-143">See Also</span></span>  
 [<span data-ttu-id="67054-144">服务器配置选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="67054-144">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
