---
title: 选择身份验证模式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.ins.instwizard.authenticationmode.f1
helpviewer_keywords:
- sa account
- authentication modes
- trusted connection
- SQL Server Installation Wizard, Authentication Mode page
- choose authentication mode
- authentication [SQL Server], choosing a mode
- Windows authentication [SQL Server]
- mixed mode authentication
- mixed authentication mode
- SQL authentication mode
ms.assetid: ff7a6a48-3d38-4209-aa0f-7d6c0a8c64ef
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 973d1ef75512f44c5dd7bbff844b72525554082e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690454"
---
# <a name="choose-an-authentication-mode"></a><span data-ttu-id="60039-102">选择身份验证模式</span><span class="sxs-lookup"><span data-stu-id="60039-102">Choose an Authentication Mode</span></span>
  <span data-ttu-id="60039-103">在安装过程中，必须为 [!INCLUDE[ssDE](../../includes/ssde-md.md)]选择身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="60039-103">During setup, you must select an authentication mode for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="60039-104">下面是两种可能的模式：Windows 身份验证模式和混合模式。</span><span class="sxs-lookup"><span data-stu-id="60039-104">There are two possible modes: Windows Authentication mode and mixed mode.</span></span> <span data-ttu-id="60039-105">Windows 身份验证模式会启用 Windows 身份验证并禁用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="60039-105">Windows Authentication mode enables Windows Authentication and disables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="60039-106">混合模式会同时启用 Windows 身份验证和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="60039-106">Mixed mode enables both Windows Authentication and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="60039-107">Windows 身份验证始终可用，并且无法禁用。</span><span class="sxs-lookup"><span data-stu-id="60039-107">Windows Authentication is always available and cannot be disabled.</span></span>  
  
## <a name="configuring-the-authentication-mode"></a><span data-ttu-id="60039-108">配置身份验证模式</span><span class="sxs-lookup"><span data-stu-id="60039-108">Configuring the Authentication Mode</span></span>  
 <span data-ttu-id="60039-109">如果在安装过程中选择混合模式身份验证，则必须为名为 sa 的内置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统管理员帐户提供一个强密码并确认该密码。</span><span class="sxs-lookup"><span data-stu-id="60039-109">If you select Mixed Mode Authentication during setup, you must provide and then confirm a strong password for the built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named sa.</span></span> <span data-ttu-id="60039-110">sa 帐户通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接。</span><span class="sxs-lookup"><span data-stu-id="60039-110">The sa account connects by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="60039-111">如果在安装过程中选择 Windows 身份验证，则安装程序会为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证创建 sa 帐户，但会禁用该帐户。</span><span class="sxs-lookup"><span data-stu-id="60039-111">If you select Windows Authentication during setup, Setup creates the sa account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication but it is disabled.</span></span> <span data-ttu-id="60039-112">如果稍后更改为混合模式身份验证并要使用 sa 帐户，则必须启用该帐户。</span><span class="sxs-lookup"><span data-stu-id="60039-112">If you later change to Mixed Mode Authentication and you want to use the sa account, you must enable the account.</span></span> <span data-ttu-id="60039-113">您可以将任何 Windows 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户配置为系统管理员。</span><span class="sxs-lookup"><span data-stu-id="60039-113">Any Windows or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account can be configured as a system administrator.</span></span> <span data-ttu-id="60039-114">由于 sa 帐户广为人知且经常成为恶意用户的攻击目标，因此除非应用程序需要使用 sa 帐户，否则请勿启用该帐户。</span><span class="sxs-lookup"><span data-stu-id="60039-114">Because the sa account is well known and often targeted by malicious users, do not enable the sa account unless your application requires it.</span></span> <span data-ttu-id="60039-115">切勿为 sa 帐户设置空密码或弱密码。</span><span class="sxs-lookup"><span data-stu-id="60039-115">Never set a blank or weak password for the sa account.</span></span> <span data-ttu-id="60039-116">若要从 Windows 身份验证模式更改为混合模式身份验证并使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，请参阅 [更改服务器身份验证模式](../../database-engine/configure-windows/change-server-authentication-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="60039-116">To change from Windows Authentication mode to Mixed Mode Authentication and use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, see [Change Server Authentication Mode](../../database-engine/configure-windows/change-server-authentication-mode.md).</span></span>  
  
## <a name="connecting-through-windows-authentication"></a><span data-ttu-id="60039-117">通过 Windows 身份验证进行连接</span><span class="sxs-lookup"><span data-stu-id="60039-117">Connecting Through Windows Authentication</span></span>  
 <span data-ttu-id="60039-118">当用户通过 Windows 用户帐户连接时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用操作系统中的 Windows 主体标记验证帐户名和密码。</span><span class="sxs-lookup"><span data-stu-id="60039-118">When a user connects through a Windows user account, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] validates the account name and password using the Windows principal token in the operating system.</span></span> <span data-ttu-id="60039-119">也就是说，用户身份由 Windows 进行确认。</span><span class="sxs-lookup"><span data-stu-id="60039-119">This means that the user identity is confirmed by Windows.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="60039-120">不要求提供密码，也不执行身份验证。</span><span class="sxs-lookup"><span data-stu-id="60039-120">does not ask for the password, and does not perform the identity validation.</span></span> <span data-ttu-id="60039-121">Windows 身份验证是默认身份验证模式，并且比 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证更为安全。</span><span class="sxs-lookup"><span data-stu-id="60039-121">Windows Authentication is the default authentication mode, and is much more secure than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="60039-122">Windows 身份验证使用 Kerberos 安全协议，提供有关强密码复杂性验证的密码策略强制，还提供帐户锁定支持，并且支持密码过期。</span><span class="sxs-lookup"><span data-stu-id="60039-122">Windows Authentication uses Kerberos security protocol, provides password policy enforcement with regard to complexity validation for strong passwords, provides support for account lockout, and supports password expiration.</span></span> <span data-ttu-id="60039-123">通过 Windows 身份验证创建的连接有时也称为可信连接，这是因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 信任由 Windows 提供的凭据。</span><span class="sxs-lookup"><span data-stu-id="60039-123">A connection made using Windows Authentication is sometimes called a trusted connection, because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trusts the credentials provided by Windows.</span></span>  
  
 <span data-ttu-id="60039-124">通过使用 Windows 身份验证，可以在域级别创建 Windows 组，并且可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中为整个组创建登录名。</span><span class="sxs-lookup"><span data-stu-id="60039-124">By using Windows Authentication, Windows groups can be created at the domain level, and a login can be created on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the entire group.</span></span> <span data-ttu-id="60039-125">在域级别管理访问可以简化帐户管理。</span><span class="sxs-lookup"><span data-stu-id="60039-125">Managing access from at the domain level can simplify account administration.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="connecting-through-sql-server-authentication"></a><span data-ttu-id="60039-126">通过 SQL Server 身份验证进行连接</span><span class="sxs-lookup"><span data-stu-id="60039-126">Connecting Through SQL Server Authentication</span></span>  
 <span data-ttu-id="60039-127">当使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证时，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中创建的登录名并不基于 Windows 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="60039-127">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, logins are created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are not based on Windows user accounts.</span></span> <span data-ttu-id="60039-128">用户名和密码均通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 创建并存储在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="60039-128">Both the user name and the password are created by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="60039-129">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接的用户每次连接时都必须提供其凭据（登录名和密码）。</span><span class="sxs-lookup"><span data-stu-id="60039-129">Users connecting using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication must provide their credentials (login and password) every time that they connect.</span></span> <span data-ttu-id="60039-130">当使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证时，必须为所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户设置强密码。</span><span class="sxs-lookup"><span data-stu-id="60039-130">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must set strong passwords for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accounts.</span></span> <span data-ttu-id="60039-131">有关强密码的指南，请参阅 [Strong Passwords](strong-passwords.md)。</span><span class="sxs-lookup"><span data-stu-id="60039-131">For strong password guidelines, see [Strong Passwords](strong-passwords.md).</span></span>  
  
 <span data-ttu-id="60039-132">可供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名选择使用的密码策略有三种。</span><span class="sxs-lookup"><span data-stu-id="60039-132">Three optional password policies are available for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
-   <span data-ttu-id="60039-133">用户在下次登录时必须更改密码</span><span class="sxs-lookup"><span data-stu-id="60039-133">User must change password at next login</span></span>  
  
     <span data-ttu-id="60039-134">要求用户在下次连接时更改密码。</span><span class="sxs-lookup"><span data-stu-id="60039-134">Requires the user to change the password the next time that the user connects.</span></span> <span data-ttu-id="60039-135">更改密码的功能由 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]提供。</span><span class="sxs-lookup"><span data-stu-id="60039-135">The ability to change the password is provided by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="60039-136">如果使用该选项，则第三方软件开发人员应提供此功能。</span><span class="sxs-lookup"><span data-stu-id="60039-136">Third-party software developers should provide this feature if this option is used.</span></span>  
  
-   <span data-ttu-id="60039-137">强制密码过期</span><span class="sxs-lookup"><span data-stu-id="60039-137">Enforce password expiration</span></span>  
  
     <span data-ttu-id="60039-138">对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名强制实施计算机的密码最长使用期限策略。</span><span class="sxs-lookup"><span data-stu-id="60039-138">The maximum password age policy of the computer is enforced for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
-   <span data-ttu-id="60039-139">强制实施密码策略</span><span class="sxs-lookup"><span data-stu-id="60039-139">Enforce password policy</span></span>  
  
     <span data-ttu-id="60039-140">对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名强制实施计算机的 Windows 密码策略。</span><span class="sxs-lookup"><span data-stu-id="60039-140">The Windows password policies of the computer are enforced for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="60039-141">这包括密码长度和密码复杂性。</span><span class="sxs-lookup"><span data-stu-id="60039-141">This includes password length and complexity.</span></span> <span data-ttu-id="60039-142">此功能需要通过 `NetValidatePasswordPolicy` API 实现，该 API 只在 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 和更高版本中提供。</span><span class="sxs-lookup"><span data-stu-id="60039-142">This functionality depends on the `NetValidatePasswordPolicy` API, which is only available in [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] and later versions.</span></span>  
  
#### <a name="to-determine-the-password-policies-of-the-local-computer"></a><span data-ttu-id="60039-143">确定本地计算机的密码策略</span><span class="sxs-lookup"><span data-stu-id="60039-143">To determine the password policies of the local computer</span></span>  
  
1.  <span data-ttu-id="60039-144">在 **“开始”** 菜单上，单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="60039-144">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="60039-145">在 "**运行**" 对话框中，键入 `secpol.msc` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="60039-145">In the **Run** dialog box, type `secpol.msc`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="60039-146">在 **“本地安全设置”** 应用程序中，依次展开 **“安全设置”** 、 **“帐户策略”** ，然后单击 **“密码策略”** 。</span><span class="sxs-lookup"><span data-stu-id="60039-146">In the **Local Security Settings** application, expand **Security Settings**, expand **Account Policies**, and then click **Password Policy**.</span></span>  
  
     <span data-ttu-id="60039-147">密码策略将如结果窗格中所示。</span><span class="sxs-lookup"><span data-stu-id="60039-147">The password policies are described in the results pane.</span></span>  
  
### <a name="disadvantages-of-sql-server-authentication"></a><span data-ttu-id="60039-148">SQL Server 身份验证的缺点</span><span class="sxs-lookup"><span data-stu-id="60039-148">Disadvantages of SQL Server Authentication</span></span>  
  
-   <span data-ttu-id="60039-149">如果用户是具有 Windows 登录名和密码的 Windows 域用户，则还必须提供另一个用于连接的 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) 登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="60039-149">If a user is a Windows domain user who has a login and password for Windows, he must still provide another ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) login and password to connect.</span></span> <span data-ttu-id="60039-150">记住多个登录名和密码对于许多用户而言都较为困难。</span><span class="sxs-lookup"><span data-stu-id="60039-150">Keeping track of multiple names and passwords is difficult for many users.</span></span> <span data-ttu-id="60039-151">每次连接到数据库时都必须提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 凭据也十分烦人。</span><span class="sxs-lookup"><span data-stu-id="60039-151">Having to provide [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credentials every time that one connects to the database can be annoying.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="60039-152">身份验证无法使用 Kerberos 安全协议。</span><span class="sxs-lookup"><span data-stu-id="60039-152">Authentication cannot use Kerberos security protocol.</span></span>  
  
-   <span data-ttu-id="60039-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名不能使用 Windows 提供的其他密码策略。</span><span class="sxs-lookup"><span data-stu-id="60039-153">Windows offers additional password policies that are not available for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
-   <span data-ttu-id="60039-154">必须在连接时通过网络传递已加密的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证登录密码。</span><span class="sxs-lookup"><span data-stu-id="60039-154">The encrypted [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login password, must be passed over the network at the time of the connection.</span></span> <span data-ttu-id="60039-155">一些自动连接的应用程序将密码存储在客户端。</span><span class="sxs-lookup"><span data-stu-id="60039-155">Some applications that connect automatically will store the password at the client.</span></span> <span data-ttu-id="60039-156">这可能产生其他攻击点。</span><span class="sxs-lookup"><span data-stu-id="60039-156">These are additional attack points.</span></span>  
  
### <a name="advantages-of-sql-server-authentication"></a><span data-ttu-id="60039-157">SQL Server 身份验证的优点</span><span class="sxs-lookup"><span data-stu-id="60039-157">Advantages of SQL Server Authentication</span></span>  
  
-   <span data-ttu-id="60039-158">允许 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持那些需要进行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证的旧版应用程序和由第三方提供的应用程序。</span><span class="sxs-lookup"><span data-stu-id="60039-158">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to support older applications and applications provided by third parties that require [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
-   <span data-ttu-id="60039-159">允许 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持具有混合操作系统的环境，在这种环境中并不是所有用户均由 Windows 域进行验证。</span><span class="sxs-lookup"><span data-stu-id="60039-159">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to support environments with mixed operating systems, where all users are not authenticated by a Windows domain.</span></span>  
  
-   <span data-ttu-id="60039-160">可让用户从未知或不受信任的域进行连接。</span><span class="sxs-lookup"><span data-stu-id="60039-160">Allows users to connect from unknown or untrusted domains.</span></span> <span data-ttu-id="60039-161">例如，既定客户使用指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名进行连接以接收其订单状态的应用程序。</span><span class="sxs-lookup"><span data-stu-id="60039-161">For instance, an application where established customers connect with assigned [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins to receive the status of their orders.</span></span>  
  
-   <span data-ttu-id="60039-162">允许 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持基于 Web 的应用程序，在这些应用程序中用户可创建自己的标识。</span><span class="sxs-lookup"><span data-stu-id="60039-162">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to support Web-based applications where users create their own identities.</span></span>  
  
-   <span data-ttu-id="60039-163">允许软件开发人员通过使用基于已知的预设 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名的复杂权限层次结构来分发应用程序。</span><span class="sxs-lookup"><span data-stu-id="60039-163">Allows software developers to distribute their applications by using a complex permission hierarchy based on known, preset [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="60039-164">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证不会限制安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机上的本地管理员权限。</span><span class="sxs-lookup"><span data-stu-id="60039-164">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication does not limit the permissions of local administrators on the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60039-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60039-165">See Also</span></span>  
 [<span data-ttu-id="60039-166">安装 SQL Server 的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="60039-166">Security Considerations for a SQL Server Installation</span></span>](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
