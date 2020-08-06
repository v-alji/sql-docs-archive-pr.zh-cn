---
title: MSSQLSERVER_18456 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18456 (Database Engine error)
ms.assetid: c417631d-be1f-42e0-8844-9f92c77e11f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f5addb6bfb9d056d9f1796749ae629d4150102a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689409"
---
# <a name="mssqlserver_18456"></a><span data-ttu-id="b913a-102">MSSQLSERVER_18456</span><span class="sxs-lookup"><span data-stu-id="b913a-102">MSSQLSERVER_18456</span></span>
    
## <a name="details"></a><span data-ttu-id="b913a-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="b913a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b913a-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b913a-104">Product Name</span></span>|<span data-ttu-id="b913a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b913a-105">SQL Server</span></span>|  
|<span data-ttu-id="b913a-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b913a-106">Event ID</span></span>|<span data-ttu-id="b913a-107">18456</span><span class="sxs-lookup"><span data-stu-id="b913a-107">18456</span></span>|  
|<span data-ttu-id="b913a-108">事件源</span><span class="sxs-lookup"><span data-stu-id="b913a-108">Event Source</span></span>|<span data-ttu-id="b913a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b913a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b913a-110">组件</span><span class="sxs-lookup"><span data-stu-id="b913a-110">Component</span></span>|<span data-ttu-id="b913a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b913a-111">SQLEngine</span></span>|  
|<span data-ttu-id="b913a-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="b913a-112">Symbolic Name</span></span>|<span data-ttu-id="b913a-113">LOGON_FAILED</span><span class="sxs-lookup"><span data-stu-id="b913a-113">LOGON_FAILED</span></span>|  
|<span data-ttu-id="b913a-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="b913a-114">Message Text</span></span>|<span data-ttu-id="b913a-115">用户 '%.\*ls'.%.\*ls 登录失败</span><span class="sxs-lookup"><span data-stu-id="b913a-115">Login failed for user '%.\*ls'.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b913a-116">说明</span><span class="sxs-lookup"><span data-stu-id="b913a-116">Explanation</span></span>  
 <span data-ttu-id="b913a-117">因密码或用户名错误而使身份验证失败并导致连接尝试被拒时，类似以下内容的消息将返回到客户端：“用户‘<user_name>’登录失败。</span><span class="sxs-lookup"><span data-stu-id="b913a-117">When a connection attempt is rejected because of an authentication failure that involves a bad password or user name, a message similar to the following is returned to the client:  "Login failed for user '<user_name>'.</span></span> <span data-ttu-id="b913a-118">（Microsoft SQL Server，错误：18456）”。</span><span class="sxs-lookup"><span data-stu-id="b913a-118">(Microsoft SQL Server, Error: 18456)".</span></span>  
  
 <span data-ttu-id="b913a-119">返回到客户端的其他信息有：</span><span class="sxs-lookup"><span data-stu-id="b913a-119">Additional information returned to the client includes the following:</span></span>  
  
 <span data-ttu-id="b913a-120">“用户‘<user_name>’登录失败。</span><span class="sxs-lookup"><span data-stu-id="b913a-120">"Login failed for user '<user_name>'.</span></span> <span data-ttu-id="b913a-121">（.Net SqlClient 数据访问接口）”</span><span class="sxs-lookup"><span data-stu-id="b913a-121">(.Net SqlClient Data Provider)"</span></span>  
  
 -----------------------------\-  
  
 <span data-ttu-id="b913a-122">“服务器名称：<computer_name>”</span><span class="sxs-lookup"><span data-stu-id="b913a-122">"Server Name: <computer_name>"</span></span>  
  
 <span data-ttu-id="b913a-123">“错误编号：18456”</span><span class="sxs-lookup"><span data-stu-id="b913a-123">"Error Number: 18456"</span></span>  
  
 <span data-ttu-id="b913a-124">“严重级别：14”</span><span class="sxs-lookup"><span data-stu-id="b913a-124">"Severity: 14"</span></span>  
  
 <span data-ttu-id="b913a-125">“状态：1”</span><span class="sxs-lookup"><span data-stu-id="b913a-125">"State: 1"</span></span>  
  
 <span data-ttu-id="b913a-126">“行号：65536”</span><span class="sxs-lookup"><span data-stu-id="b913a-126">"Line Number: 65536"</span></span>  
  
 <span data-ttu-id="b913a-127">也可能返回以下消息：</span><span class="sxs-lookup"><span data-stu-id="b913a-127">The following message might also be returned:</span></span>  
  
 <span data-ttu-id="b913a-128">“消息 18456、级别 14、状态 1、服务器 <computer_name>、行 1”</span><span class="sxs-lookup"><span data-stu-id="b913a-128">"Msg 18456, Level 14, State 1, Server <computer_name>, Line 1"</span></span>  
  
 <span data-ttu-id="b913a-129">“用户‘<user_name>’登录失败。”</span><span class="sxs-lookup"><span data-stu-id="b913a-129">"Login failed for user '<user_name>'."</span></span>  
  
## <a name="additional-error-information"></a><span data-ttu-id="b913a-130">其他错误信息</span><span class="sxs-lookup"><span data-stu-id="b913a-130">Additional Error Information</span></span>  
 <span data-ttu-id="b913a-131">为了增强安全性，返回到客户端的错误消息有意隐藏身份验证错误的本质。</span><span class="sxs-lookup"><span data-stu-id="b913a-131">To increase security, the error message that is returned to the client deliberately hides the nature of the authentication error.</span></span> <span data-ttu-id="b913a-132">但是，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志中，对应的错误包含映射到身份验证失败条件的错误状态。</span><span class="sxs-lookup"><span data-stu-id="b913a-132">However, in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, a corresponding error contains an error state that maps to an authentication failure condition.</span></span> <span data-ttu-id="b913a-133">将错误状态与以下列表进行比较以确定登录失败的原因。</span><span class="sxs-lookup"><span data-stu-id="b913a-133">Compare the error state to the following list to determine the reason for the login failure.</span></span>  
  
|<span data-ttu-id="b913a-134">状态</span><span class="sxs-lookup"><span data-stu-id="b913a-134">State</span></span>|<span data-ttu-id="b913a-135">说明</span><span class="sxs-lookup"><span data-stu-id="b913a-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b913a-136">1</span><span class="sxs-lookup"><span data-stu-id="b913a-136">1</span></span>|<span data-ttu-id="b913a-137">无法获得错误信息。</span><span class="sxs-lookup"><span data-stu-id="b913a-137">Error information is not available.</span></span> <span data-ttu-id="b913a-138">此状态通常意味着您不拥有接收错误详细信息的权限。</span><span class="sxs-lookup"><span data-stu-id="b913a-138">This state usually means you do not have permission to receive the error details.</span></span> <span data-ttu-id="b913a-139">请联系 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理员以获得详细信息。</span><span class="sxs-lookup"><span data-stu-id="b913a-139">Contact your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrator for more information.</span></span>|  
|<span data-ttu-id="b913a-140">2</span><span class="sxs-lookup"><span data-stu-id="b913a-140">2</span></span>|<span data-ttu-id="b913a-141">用户 ID 无效。</span><span class="sxs-lookup"><span data-stu-id="b913a-141">User ID is not valid.</span></span>|  
|<span data-ttu-id="b913a-142">5</span><span class="sxs-lookup"><span data-stu-id="b913a-142">5</span></span>|<span data-ttu-id="b913a-143">用户 ID 无效。</span><span class="sxs-lookup"><span data-stu-id="b913a-143">User ID is not valid.</span></span>|  
|<span data-ttu-id="b913a-144">6</span><span class="sxs-lookup"><span data-stu-id="b913a-144">6</span></span>|<span data-ttu-id="b913a-145">尝试同时使用 SQL Server 身份验证与 Windows 登录名。</span><span class="sxs-lookup"><span data-stu-id="b913a-145">An attempt was made to use a Windows login name with SQL Server Authentication.</span></span>|  
|<span data-ttu-id="b913a-146">7</span><span class="sxs-lookup"><span data-stu-id="b913a-146">7</span></span>|<span data-ttu-id="b913a-147">登录已禁用，密码不正确。</span><span class="sxs-lookup"><span data-stu-id="b913a-147">Login is disabled, and the password is incorrect.</span></span>|  
|<span data-ttu-id="b913a-148">8</span><span class="sxs-lookup"><span data-stu-id="b913a-148">8</span></span>|<span data-ttu-id="b913a-149">密码不正确。</span><span class="sxs-lookup"><span data-stu-id="b913a-149">The password is incorrect.</span></span>|  
|<span data-ttu-id="b913a-150">9</span><span class="sxs-lookup"><span data-stu-id="b913a-150">9</span></span>|<span data-ttu-id="b913a-151">密码无效。</span><span class="sxs-lookup"><span data-stu-id="b913a-151">Password is not valid.</span></span>|  
|<span data-ttu-id="b913a-152">11</span><span class="sxs-lookup"><span data-stu-id="b913a-152">11</span></span>|<span data-ttu-id="b913a-153">登录有效，但服务器访问失败。</span><span class="sxs-lookup"><span data-stu-id="b913a-153">Login is valid, but server access failed.</span></span> <span data-ttu-id="b913a-154">导致此错误的一个可能原因是：Windows 用户作为本地管理员组的成员有权访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，但 Windows 没有提供管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="b913a-154">One possible cause of this error is when the Windows user has access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a member of the local administrators group, but Windows is not providing administrator credentials.</span></span> <span data-ttu-id="b913a-155">若要连接，请使用“以管理员身份运行”选项启动连接程序，然后将 Windows 用户作为特定的登录名添加到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b913a-155">To connect, start the connecting program using the **Run as administrator** option, and then add the Windows user to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a specific login.</span></span>|  
|<span data-ttu-id="b913a-156">12</span><span class="sxs-lookup"><span data-stu-id="b913a-156">12</span></span>|<span data-ttu-id="b913a-157">登录是有效的登录，但服务器访问失败。</span><span class="sxs-lookup"><span data-stu-id="b913a-157">Login is valid login, but server access failed.</span></span>|  
|<span data-ttu-id="b913a-158">18</span><span class="sxs-lookup"><span data-stu-id="b913a-158">18</span></span>|<span data-ttu-id="b913a-159">必须更改密码。</span><span class="sxs-lookup"><span data-stu-id="b913a-159">Password must be changed.</span></span>|  
  
 <span data-ttu-id="b913a-160">存在其他错误状态，并表示一个意外的内部处理错误。</span><span class="sxs-lookup"><span data-stu-id="b913a-160">Other error states exist and signify an unexpected internal processing error.</span></span>  
  
 <span data-ttu-id="b913a-161">**其他不常见的可能原因**</span><span class="sxs-lookup"><span data-stu-id="b913a-161">**An additional unusual possible cause**</span></span>  
  
 <span data-ttu-id="b913a-162">在以下情况下可能会返回错误原因 **“尝试使用 SQL Server 身份验证登录失败。服务器配置为仅使用 Windows 身份验证。**</span><span class="sxs-lookup"><span data-stu-id="b913a-162">The error reason **An attempt to login using SQL authentication failed. Server is configured for Windows authentication only.**</span></span> <span data-ttu-id="b913a-163">可能会在下列情况下返回。</span><span class="sxs-lookup"><span data-stu-id="b913a-163">can be returned in the following situations.</span></span>  
  
-   <span data-ttu-id="b913a-164">当服务器配置为混合模式身份验证并且某个 ODBC 连接使用 TCP 协议，且该连接未显式指定该连接应使用某一可信连接时。</span><span class="sxs-lookup"><span data-stu-id="b913a-164">When the server is configured for mixed mode authentication, and an ODBC connection uses the TCP protocol, and the connection does not explicitly specify that the connection should use a trusted connection.</span></span>  
  
-   <span data-ttu-id="b913a-165">当服务器配置为混合模式身份验证并且某个 ODBC 连接使用命名管道，且客户端用来打开命名管道的凭据用于自动模拟该用户并且该连接未显式指定该连接应使用某一可信连接时。</span><span class="sxs-lookup"><span data-stu-id="b913a-165">When the server is configured for mixed mode authentication, and an ODBC connection uses named pipes, and the credentials the client used to open the named pipe are used to automatically impersonate the user, and the connection does not explicitly specify that the connection should use a trusted connection.</span></span>  
  
 <span data-ttu-id="b913a-166">若要解决此问题，应在连接字符串中包含 `TRUSTED_CONNECTION = TRUE`。</span><span class="sxs-lookup"><span data-stu-id="b913a-166">To resolve this issue, include `TRUSTED_CONNECTION = TRUE` in the connection string.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b913a-167">示例</span><span class="sxs-lookup"><span data-stu-id="b913a-167">Examples</span></span>  
 <span data-ttu-id="b913a-168">在此示例中，身份验证错误状态为 8。</span><span class="sxs-lookup"><span data-stu-id="b913a-168">In this example, the authentication error state is 8.</span></span> <span data-ttu-id="b913a-169">这表示密码不正确。</span><span class="sxs-lookup"><span data-stu-id="b913a-169">This indicates that the password is incorrect.</span></span>  
  
|<span data-ttu-id="b913a-170">Date</span><span class="sxs-lookup"><span data-stu-id="b913a-170">Date</span></span>|<span data-ttu-id="b913a-171">源</span><span class="sxs-lookup"><span data-stu-id="b913a-171">Source</span></span>|<span data-ttu-id="b913a-172">消息</span><span class="sxs-lookup"><span data-stu-id="b913a-172">Message</span></span>|  
|----------|------------|-------------|  
|<span data-ttu-id="b913a-173">2007-12-05 20:12:56.34</span><span class="sxs-lookup"><span data-stu-id="b913a-173">2007-12-05 20:12:56.34</span></span>|<span data-ttu-id="b913a-174">登录</span><span class="sxs-lookup"><span data-stu-id="b913a-174">Logon</span></span>|<span data-ttu-id="b913a-175">错误：18456，严重级别：14，状态：8.</span><span class="sxs-lookup"><span data-stu-id="b913a-175">Error: 18456, Severity: 14, State: 8.</span></span>|  
|<span data-ttu-id="b913a-176">2007-12-05 20:12:56.34</span><span class="sxs-lookup"><span data-stu-id="b913a-176">2007-12-05 20:12:56.34</span></span>|<span data-ttu-id="b913a-177">登录</span><span class="sxs-lookup"><span data-stu-id="b913a-177">Logon</span></span>|<span data-ttu-id="b913a-178">用户‘<user_name>’登录失败。</span><span class="sxs-lookup"><span data-stu-id="b913a-178">Login failed for user '<user_name>'.</span></span> <span data-ttu-id="b913a-179">[客户端: \<ip address>]</span><span class="sxs-lookup"><span data-stu-id="b913a-179">[CLIENT: \<ip address>]</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="b913a-180">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是使用 Windows 身份验证模式安装的，并随后更改为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 身份验证模式，则最初会禁用 **sa** 登录名。</span><span class="sxs-lookup"><span data-stu-id="b913a-180">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed using Windows Authentication mode and is later changed to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Authentication mode, the **sa** login is initially disabled.</span></span> <span data-ttu-id="b913a-181">这将导致状态 7 错误：“用户‘sa’登录失败。”若要启用 **sa** 登录名，请参阅[更改服务器身份验证模式](../../database-engine/configure-windows/change-server-authentication-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="b913a-181">This causes the state 7 error: "Login failed for user 'sa'." To enable the **sa** login, see [Change Server Authentication Mode](../../database-engine/configure-windows/change-server-authentication-mode.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b913a-182">用户操作</span><span class="sxs-lookup"><span data-stu-id="b913a-182">User Action</span></span>  
 <span data-ttu-id="b913a-183">如果您尝试使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接，请验证是否将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为使用混合身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="b913a-183">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured in Mixed Authentication Mode.</span></span>  
  
 <span data-ttu-id="b913a-184">如果尝试使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接，请验证 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名是否存在以及拼写是否正确。</span><span class="sxs-lookup"><span data-stu-id="b913a-184">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login exists and that you have spelled it properly.</span></span>  
  
 <span data-ttu-id="b913a-185">如果尝试使用 Windows 身份验证进行连接，请验证您是否正确地登录到相应的域。</span><span class="sxs-lookup"><span data-stu-id="b913a-185">If you are trying to connect using Windows Authentication, verify that you are properly logged into the correct domain.</span></span>  
  
 <span data-ttu-id="b913a-186">如果错误指示状态 1，请与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理员联系。</span><span class="sxs-lookup"><span data-stu-id="b913a-186">If your error indicates state 1, contact your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrator.</span></span>  
  
 <span data-ttu-id="b913a-187">如果您尝试使用您的管理员凭据进行连接，则通过使用“以管理员身份运行”选项启动您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="b913a-187">If you are trying to connect using your administrator credentials, start you application by using the **Run as Administrator** option.</span></span> <span data-ttu-id="b913a-188">在连接后，将您的 Windows 用户作为单独的登录名添加。</span><span class="sxs-lookup"><span data-stu-id="b913a-188">When connected, add your Windows user as an individual login.</span></span>  
  
 <span data-ttu-id="b913a-189">如果[!INCLUDE[ssDE](../../includes/ssde-md.md)]支持包含的数据库，请确认在迁移到包含的数据库用户后未删除登录名。</span><span class="sxs-lookup"><span data-stu-id="b913a-189">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] supports contained databases, confirm that the login was not deleted after migration to a contained database user.</span></span>  
  
 <span data-ttu-id="b913a-190">在本地连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例时，在 **NT AUTHORITY\NETWORK SERVICE** 下运行的服务的连接必须使用计算机完全限定域名进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b913a-190">When connecting locally to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], connections from services running under **NT AUTHORITY\NETWORK SERVICE** must authenticate using the computers fully qualified domain name.</span></span> <span data-ttu-id="b913a-191">有关详细信息，请参阅本主题中的[如何在 ASP.NET 中使用网络服务帐户来访问资源](https://msdn.microsoft.com/library/ff647402.aspx)</span><span class="sxs-lookup"><span data-stu-id="b913a-191">For more information, see [How To: Use the Network Service Account to Access Resources in ASP.NET](https://msdn.microsoft.com/library/ff647402.aspx)</span></span>  
  
  
