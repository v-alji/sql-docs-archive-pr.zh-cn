---
title: 数据库引擎配置-帐户预配 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 834b26bc-49de-4033-88d5-6aa7b1609720
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7885bdda72668ac96e90b0900772a4f56575d5fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577242"
---
# <a name="database-engine-configuration---account-provisioning"></a><span data-ttu-id="b64cc-102">数据库引擎配置 - 帐户设置</span><span class="sxs-lookup"><span data-stu-id="b64cc-102">Database Engine Configuration - Account Provisioning</span></span>
  <span data-ttu-id="b64cc-103">使用此页可以设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全模式，并添加 Windows 用户或组作为 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的管理员。</span><span class="sxs-lookup"><span data-stu-id="b64cc-103">Use this page to set the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security mode, and to add Windows users or groups as administrators of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
## <a name="considerations-for-running-sscurrent"></a><span data-ttu-id="b64cc-104">有关运行 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的注意事项</span><span class="sxs-lookup"><span data-stu-id="b64cc-104">Considerations for Running [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]</span></span>  
 <span data-ttu-id="b64cc-105">在以前版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，将 **BUILTIN\Administrators** 组设置为 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中的登录名，本地 Administrators 组的成员可以使用其管理员凭据登录。</span><span class="sxs-lookup"><span data-stu-id="b64cc-105">On previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the **BUILTIN\Administrators** group was provisioned as a login in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and members of the local Administrators group could login using their Administrator credentials.</span></span> <span data-ttu-id="b64cc-106">使用提升的权限并不是最佳做法。</span><span class="sxs-lookup"><span data-stu-id="b64cc-106">Using elevated permissions is not a best practice.</span></span> <span data-ttu-id="b64cc-107">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，未将 **BUILTIN\Administrators** 组设置为登录名。</span><span class="sxs-lookup"><span data-stu-id="b64cc-107">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] the **BUILTIN\Administrators** group is not provisioned as a login.</span></span> <span data-ttu-id="b64cc-108">因此，您应为每个管理用户创建一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名，并在安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]新实例的过程中将该登录名添加到 sysadmin 固定服务器角色中。</span><span class="sxs-lookup"><span data-stu-id="b64cc-108">As a result, you should create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login for each administrative user, and add that login to the sysadmin fixed server role during installation of a new instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b64cc-109">对于用来运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业的 Windows 帐户，您也应该执行这些操作。</span><span class="sxs-lookup"><span data-stu-id="b64cc-109">You should also do this for Windows accounts that are used to run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent jobs.</span></span> <span data-ttu-id="b64cc-110">这些作业包括复制代理作业。</span><span class="sxs-lookup"><span data-stu-id="b64cc-110">These include replication agent jobs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b64cc-111">选项</span><span class="sxs-lookup"><span data-stu-id="b64cc-111">Options</span></span>  
 <span data-ttu-id="b64cc-112">**安全模式** - 选择“Windows 身份验证”或“混合模式身份验证”用于安装。</span><span class="sxs-lookup"><span data-stu-id="b64cc-112">**Security Mode** - Select Windows Authentication or Mixed Mode Authentication for your installation.</span></span>  
  
 <span data-ttu-id="b64cc-113">**Windows 主体设置** - 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的早期版本中，Windows Builtin\Administrator 本地组放入了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin 服务器角色中，有效授予了 Windows 管理员对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的访问权限。</span><span class="sxs-lookup"><span data-stu-id="b64cc-113">**Windows Principal Provisioning** - In previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the Windows Builtin\Administrator local group was placed into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin server role, effectively granting Windows administrators access to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b64cc-114">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的 sysadmin 服务器角色中未设置 Builtin\Administrator 组，</span><span class="sxs-lookup"><span data-stu-id="b64cc-114">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the Builtin\Administrator group is not provisioned in the sysadmin server role.</span></span> <span data-ttu-id="b64cc-115">而是改为由您在安装过程中为新安装显式设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理员。</span><span class="sxs-lookup"><span data-stu-id="b64cc-115">Instead, you should explicitly provision [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrators for new installations during Setup.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b64cc-116">您在安装过程中必须为新安装显式设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理员。</span><span class="sxs-lookup"><span data-stu-id="b64cc-116">You must explicitly provision [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrators for new installations during Setup.</span></span> <span data-ttu-id="b64cc-117">直到您完成此步骤之后，安装程序才允许您继续操作。</span><span class="sxs-lookup"><span data-stu-id="b64cc-117">Setup will not allow you to continue until you complete this step.</span></span>  
  
 <span data-ttu-id="b64cc-118">**指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理员** - 必须为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例至少指定一个 Windows 主体。</span><span class="sxs-lookup"><span data-stu-id="b64cc-118">**Specify [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Administrators** - You must specify at least one Windows principal for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b64cc-119">若要添加用以运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序的帐户，请单击 **“当前用户”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="b64cc-119">To add the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup is running, click the **Current User** button.</span></span> <span data-ttu-id="b64cc-120">若要向系统管理员列表中添加帐户或从中删除帐户，请单击 **“添加”** 或 **“删除”** ，然后编辑将拥有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的管理员特权的用户、组或计算机的列表。</span><span class="sxs-lookup"><span data-stu-id="b64cc-120">To add or remove accounts from the list of system administrators, click **Add** or **Remove**, and then edit the list of users, groups, or computers that will have administrator privileges for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b64cc-121">完成列表的编辑后，单击 **“确定”**，然后在配置对话框中验证管理员列表。</span><span class="sxs-lookup"><span data-stu-id="b64cc-121">When you are finished editing the list, click **OK**, then verify the list of administrators in the configuration dialog.</span></span> <span data-ttu-id="b64cc-122">完成此列表后，请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="b64cc-122">When the list is complete, click **Next**.</span></span>  
  
 <span data-ttu-id="b64cc-123">如果选择“混合模式身份验证”，则必须为内置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统管理员 (SA) 帐户提供登录凭据。</span><span class="sxs-lookup"><span data-stu-id="b64cc-123">If you select Mixed Mode Authentication, you must provide logon credentials for the builtin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator (SA) account.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
 <span data-ttu-id="b64cc-124">**Windows 身份验证模式**</span><span class="sxs-lookup"><span data-stu-id="b64cc-124">**Windows Authentication Mode**</span></span>  
 <span data-ttu-id="b64cc-125">当用户通过 Windows 用户帐户连接时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用操作系统中的 Windows 主体标记验证帐户名和密码。</span><span class="sxs-lookup"><span data-stu-id="b64cc-125">When a user connects through a Windows user account, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] validates the account name and password using the Windows principal token in the operating system.</span></span> <span data-ttu-id="b64cc-126">此为默认身份验证模式，比混合模式更为安全。</span><span class="sxs-lookup"><span data-stu-id="b64cc-126">This is the default authentication mode, and is much more secure than Mixed Mode.</span></span> <span data-ttu-id="b64cc-127">Windows 身份验证利用 Kerberos 安全协议，通过强密码的复杂性验证提供密码策略强制，提供帐户锁定支持，并且支持密码过期。</span><span class="sxs-lookup"><span data-stu-id="b64cc-127">Windows Authentication utilizes Kerberos security protocol, provides password policy enforcement in terms of complexity validation for strong passwords, provides support for account lockout, and supports password expiration.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]<span data-ttu-id="b64cc-128">切勿设置空密码或弱 sa 密码。</span><span class="sxs-lookup"><span data-stu-id="b64cc-128">Never set a blank or weak sa password.</span></span>  
  
 <span data-ttu-id="b64cc-129">\*\*混合模式 (Windows 身份验证或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证) \*\*</span><span class="sxs-lookup"><span data-stu-id="b64cc-129">**Mixed Mode (Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication)**</span></span>  
 <span data-ttu-id="b64cc-130">允许用户使用 Windows 身份验证或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接。</span><span class="sxs-lookup"><span data-stu-id="b64cc-130">Allows users to connect by using Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="b64cc-131">通过 Windows 用户帐户进行连接的用户可以使用经过 Windows 验证的信任连接。</span><span class="sxs-lookup"><span data-stu-id="b64cc-131">Users who connect through a Windows user account can use trusted connections that are validated by Windows.</span></span>  
  
 <span data-ttu-id="b64cc-132">如果必须选择“混合模式身份验证”并且要求使用 SQL 登录名以适应早期应用程序，则必须为所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户设置强密码。</span><span class="sxs-lookup"><span data-stu-id="b64cc-132">If you must choose Mixed Mode Authentication and you have a requirement for using SQL logins to accommodate legacy applications, you must set strong passwords for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accounts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b64cc-133">提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证只是为了向后兼容。</span><span class="sxs-lookup"><span data-stu-id="b64cc-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is provided for backward compatibility only.</span></span> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 <span data-ttu-id="b64cc-134">**输入密码**</span><span class="sxs-lookup"><span data-stu-id="b64cc-134">**Enter Password**</span></span>  
 <span data-ttu-id="b64cc-135">输入并确认系统管理员 (sa) 登录名。</span><span class="sxs-lookup"><span data-stu-id="b64cc-135">Enter and confirm the system administrator (sa) login.</span></span> <span data-ttu-id="b64cc-136">密码是抵御入侵者的第一道防线，因此设置强密码对于系统安全是绝对必要的。</span><span class="sxs-lookup"><span data-stu-id="b64cc-136">Passwords are the first line of defense against intruders, so setting strong passwords is essential to the security of your system.</span></span> <span data-ttu-id="b64cc-137">切勿设置空密码或弱 sa 密码。</span><span class="sxs-lookup"><span data-stu-id="b64cc-137">Never set a blank or weak sa password.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b64cc-138">密码可包含 1 到 128 个字符，包括字母、符号和数字的任意组合。</span><span class="sxs-lookup"><span data-stu-id="b64cc-138">passwords can contain from 1 to 128 characters, including any combination of letters, symbols, and numbers.</span></span> <span data-ttu-id="b64cc-139">如果选择“混合模式身份验证”，则必须输入强 sa 密码才能进入安装向导的下一页。</span><span class="sxs-lookup"><span data-stu-id="b64cc-139">If you choose Mixed Mode authentication, you must enter a strong sa password before you can continue to the next page of the Installation Wizard.</span></span>  
  
 <span data-ttu-id="b64cc-140">**强密码指南**</span><span class="sxs-lookup"><span data-stu-id="b64cc-140">**Strong Password Guidelines**</span></span>  
 <span data-ttu-id="b64cc-141">强密码不易被人猜出，也不能轻易地使用计算机程序进行黑客攻击。</span><span class="sxs-lookup"><span data-stu-id="b64cc-141">Strong passwords are not readily guessed by a person, and are not easily hacked using a computer program.</span></span> <span data-ttu-id="b64cc-142">强密码不能使用禁止的条件或字词，这些条件或字词包括：</span><span class="sxs-lookup"><span data-stu-id="b64cc-142">Strong passwords cannot use prohibited conditions or terms, including:</span></span>  
  
-   <span data-ttu-id="b64cc-143">空条件或 NULL 条件</span><span class="sxs-lookup"><span data-stu-id="b64cc-143">A blank or NULL condition</span></span>  
  
-   <span data-ttu-id="b64cc-144">“Password”</span><span class="sxs-lookup"><span data-stu-id="b64cc-144">"Password"</span></span>  
  
-   <span data-ttu-id="b64cc-145">“Admin”</span><span class="sxs-lookup"><span data-stu-id="b64cc-145">"Admin"</span></span>  
  
-   <span data-ttu-id="b64cc-146">“Administrator”</span><span class="sxs-lookup"><span data-stu-id="b64cc-146">"Administrator"</span></span>  
  
-   <span data-ttu-id="b64cc-147">“sa”</span><span class="sxs-lookup"><span data-stu-id="b64cc-147">"sa"</span></span>  
  
-   <span data-ttu-id="b64cc-148">“sysadmin”</span><span class="sxs-lookup"><span data-stu-id="b64cc-148">"sysadmin"</span></span>  
  
 <span data-ttu-id="b64cc-149">强密码不能是与安装计算机相关联的以下术语：</span><span class="sxs-lookup"><span data-stu-id="b64cc-149">A strong password cannot be the following terms associated with the installation computer:</span></span>  
  
-   <span data-ttu-id="b64cc-150">当前登录到计算机的用户的名称。</span><span class="sxs-lookup"><span data-stu-id="b64cc-150">The name of the user currently logged onto the machine.</span></span>  
  
-   <span data-ttu-id="b64cc-151">计算机名称。</span><span class="sxs-lookup"><span data-stu-id="b64cc-151">The computer name.</span></span>  
  
 <span data-ttu-id="b64cc-152">强密码的长度必须多于 8 个字符，并且强密码至少要满足下列四个条件中的三个：</span><span class="sxs-lookup"><span data-stu-id="b64cc-152">A strong password must be more than 8 characters in length and satisfy at least three of the following four criteria:</span></span>  
  
-   <span data-ttu-id="b64cc-153">它必须包含大写字母。</span><span class="sxs-lookup"><span data-stu-id="b64cc-153">It must contain uppercase letters.</span></span>  
  
-   <span data-ttu-id="b64cc-154">它必须包含小写字母。</span><span class="sxs-lookup"><span data-stu-id="b64cc-154">It must contain lowercase letters.</span></span>  
  
-   <span data-ttu-id="b64cc-155">必须包含数字。</span><span class="sxs-lookup"><span data-stu-id="b64cc-155">It must contain numbers.</span></span>  
  
-   <span data-ttu-id="b64cc-156">必须包含非字母数字字符；例如 #、% 或 ^。</span><span class="sxs-lookup"><span data-stu-id="b64cc-156">It must contain non-alphanumeric characters; for example, #, %, or ^.</span></span>  
  
 <span data-ttu-id="b64cc-157">此页上输入的密码必须符合强密码策略要求。</span><span class="sxs-lookup"><span data-stu-id="b64cc-157">Passwords entered on this page must meet strong password policy requirements.</span></span> <span data-ttu-id="b64cc-158">如果存在任何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证的自动化过程，请确保该密码符合强密码策略要求。</span><span class="sxs-lookup"><span data-stu-id="b64cc-158">If you have any automation that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, ensure that the password meets strong password policy requirements.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="b64cc-159">相关内容</span><span class="sxs-lookup"><span data-stu-id="b64cc-159">Related Content</span></span>  
 <span data-ttu-id="b64cc-160">有关选择 Windows 身份验证和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证的详细信息，请参阅 **联机丛书中的“选择身份验证模式”**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 主题。</span><span class="sxs-lookup"><span data-stu-id="b64cc-160">For more information about choosing Windows Authentication vs. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, see the topic **Choose an Authentication Mode** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="b64cc-161">有关选择帐户以运行 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的详细信息，请参阅 **联机丛书中的“配置 Windows 服务帐户和权限”**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 主题。</span><span class="sxs-lookup"><span data-stu-id="b64cc-161">For more information about choosing an account to run the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], see the topic **Configure Windows Service Accounts and Permissions** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b64cc-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b64cc-162">See Also</span></span>  
 [<span data-ttu-id="b64cc-163">配置 Windows 服务帐户和权限</span><span class="sxs-lookup"><span data-stu-id="b64cc-163">Configure Windows Service Accounts and Permissions</span></span>](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
  
  
