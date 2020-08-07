---
title: 在系统管理员被锁定时连接到 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- sa account
- connecting when locked out [SQL Server]
- locked out [SQL Server]
ms.assetid: c0c0082e-b867-480f-a54b-79f2a94ceb67
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 47b9659943e51a2d31a2354740660aebd652745c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588023"
---
# <a name="connect-to-sql-server-when-system-administrators-are-locked-out"></a><span data-ttu-id="09ecf-102">在系统管理员被锁定时连接到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="09ecf-102">Connect to SQL Server When System Administrators Are Locked Out</span></span>
  <span data-ttu-id="09ecf-103">本主题介绍如何以系统管理员身份重新获得对 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的访问权限。</span><span class="sxs-lookup"><span data-stu-id="09ecf-103">This topic describes how you can regain access to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] as a system administrator.</span></span> <span data-ttu-id="09ecf-104">系统管理员可能会由于下列原因之一失去对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的访问权限：</span><span class="sxs-lookup"><span data-stu-id="09ecf-104">A system administrator can lose access to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because of one of the following reasons:</span></span>  
  
-   <span data-ttu-id="09ecf-105">作为 sysadmin 固定服务器角色成员的所有登录名都已经被误删除。</span><span class="sxs-lookup"><span data-stu-id="09ecf-105">All logins that are members of the sysadmin fixed server role have been removed by mistake.</span></span>  
  
-   <span data-ttu-id="09ecf-106">作为 sysadmin 固定服务器角色成员的所有 Windows 组都已经被误删除。</span><span class="sxs-lookup"><span data-stu-id="09ecf-106">All Windows Groups that are members of the sysadmin fixed server role have been removed by mistake.</span></span>  
  
-   <span data-ttu-id="09ecf-107">作为 sysadmin 固定服务器角色成员的登录名用于已经离开公司或者无法找到的个人。</span><span class="sxs-lookup"><span data-stu-id="09ecf-107">The logins that are members of the sysadmin fixed server role are for individuals who have left the company or who are not available.</span></span>  
  
-   <span data-ttu-id="09ecf-108">sa 帐户被禁用或者没有人知道密码。</span><span class="sxs-lookup"><span data-stu-id="09ecf-108">The sa account is disabled or no one knows the password.</span></span>  
  
 <span data-ttu-id="09ecf-109">可以让您重新获得访问权限的一种方法是重新安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并将所有数据库附加到新实例。</span><span class="sxs-lookup"><span data-stu-id="09ecf-109">One way in which you can regain access is to reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and attach all the databases to the new instance.</span></span> <span data-ttu-id="09ecf-110">这种解决方案很耗时，并且若要恢复登录名，可能还需要从备份中还原 master 数据库。</span><span class="sxs-lookup"><span data-stu-id="09ecf-110">This solution is time-consuming; and, to recover the logins, it might require restoring the master database from a backup.</span></span> <span data-ttu-id="09ecf-111">如果 master 数据库的备份较旧，则它可能未包含所有信息。</span><span class="sxs-lookup"><span data-stu-id="09ecf-111">If the backup of the master database is older, it might not have all the information.</span></span> <span data-ttu-id="09ecf-112">如果 master 数据库的备份较新，则它可能与前一个实例具有同样的登录名；因此管理员仍将被锁定。</span><span class="sxs-lookup"><span data-stu-id="09ecf-112">If the backup of the master database is more recent, it might have the same logins as the previous instance; therefore, administrators will still be locked out.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="09ecf-113">解决方法</span><span class="sxs-lookup"><span data-stu-id="09ecf-113">Resolution</span></span>  
 <span data-ttu-id="09ecf-114">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -m **或** -f **选项在单用户模式下启动** 的实例。</span><span class="sxs-lookup"><span data-stu-id="09ecf-114">Start the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode by using either the **-m** or **-f** options.</span></span> <span data-ttu-id="09ecf-115">计算机的本地 Administrators 组的任何成员都可以随后作为 sysadmin 固定服务器角色的成员连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="09ecf-115">Any member of the computer's local Administrators group can then connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a member of the sysadmin fixed server role.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09ecf-116">在单用户模式下启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时，请首先停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务。</span><span class="sxs-lookup"><span data-stu-id="09ecf-116">When you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, first stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span> <span data-ttu-id="09ecf-117">否则， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理可能会首先连接，并阻止您作为第二个用户连接。</span><span class="sxs-lookup"><span data-stu-id="09ecf-117">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent might connect first and prevent you from connecting as a second user.</span></span>  
  
 <span data-ttu-id="09ecf-118">当你将 **-m**选项与**sqlcmd**或结合使用时 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，你可以限制与指定客户端应用程序的连接。</span><span class="sxs-lookup"><span data-stu-id="09ecf-118">When you use the **-m** option with **sqlcmd** or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can limit the connections to a specified client application.</span></span> <span data-ttu-id="09ecf-119">例如， **-m "sqlcmd"** 将连接限制为单个连接，并且该连接必须将自身标识为**sqlcmd**客户端程序。</span><span class="sxs-lookup"><span data-stu-id="09ecf-119">For example, **-m"sqlcmd"** limits connections to a single connection and that connection must identify itself as the **sqlcmd** client program.</span></span> <span data-ttu-id="09ecf-120">当您正在单用户模式下启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并且未知的客户端应用程序正在占用这个唯一的可用连接时，使用此选项。</span><span class="sxs-lookup"><span data-stu-id="09ecf-120">Use this option when you are starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode and an unknown client application is taking the only available connection.</span></span> <span data-ttu-id="09ecf-121">若要通过 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的查询编辑器进行连接，请使用 **-m"Microsoft SQL Server Management Studio - Query"** 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-121">To connect through the Query Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], use **-m"Microsoft SQL Server Management Studio - Query"**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="09ecf-122">不要将此选项作为安全功能使用。</span><span class="sxs-lookup"><span data-stu-id="09ecf-122">Do not use this option as a security feature.</span></span> <span data-ttu-id="09ecf-123">客户端应用程序提供客户端应用程序名称，并且提供假名称来作为连接字符串的一部分。</span><span class="sxs-lookup"><span data-stu-id="09ecf-123">The client application provides the client application name, and can provide a false name as part of the connection string.</span></span>  
  
 <span data-ttu-id="09ecf-124">有关如何在单用户模式下启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的分步说明，请参阅 [配置服务器启动选项（SQL Server 配置管理器）](scm-services-configure-server-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="09ecf-124">For step-by-step instructions about how to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](scm-services-configure-server-startup-options.md).</span></span>  
  
## <a name="step-by-step-instructions"></a><span data-ttu-id="09ecf-125">分步说明</span><span class="sxs-lookup"><span data-stu-id="09ecf-125">Step-By-Step Instructions</span></span>  
 <span data-ttu-id="09ecf-126">下面的说明介绍了如何连接到 Windows 8 或更高版本上运行的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-126">The following instructions describe the process for connecting to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] running on Windows 8 or higher.</span></span> <span data-ttu-id="09ecf-127">对于早期的 SQL Server 或 Windows 版本略有调整。</span><span class="sxs-lookup"><span data-stu-id="09ecf-127">Slight adjustments for earlier versions of SQL Server or Windows are provided.</span></span> <span data-ttu-id="09ecf-128">在作为本地管理员组的成员登录到 Windows 时必须按这些说明操作，假定在计算机上安装了 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-128">These instructions must be performed while logged in to Windows as a member of the local administrators group, and they assume that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is installed on the computer.</span></span>  
  
1.  <span data-ttu-id="09ecf-129">从“开始”页启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="09ecf-129">From the Start page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="09ecf-130">在“视图” \*\*\*\* 菜单上，选择“已注册的服务器” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="09ecf-130">On the **View** menu, select **Registered Servers**.</span></span> <span data-ttu-id="09ecf-131">（如果尚未注册你的服务器，请右键单击“本地服务器组”，指向“任务”，然后单击“注册本地服务器”。\*\*\*\*\*\*\*\*\*\*\*\*）</span><span class="sxs-lookup"><span data-stu-id="09ecf-131">(If your server is not already registered, right-click **Local Server Groups**, point to **Tasks**, and then click **Register Local Servers**.)</span></span>  
  
2.  <span data-ttu-id="09ecf-132">在“已注册的服务器”区域中，右键单击你的服务器，然后单击“SQL Server 配置管理器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="09ecf-132">In the Registered Servers area, right-click your server, and then click **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="09ecf-133">这应要求以管理员身份运行的权限，然后打开配置管理器程序。</span><span class="sxs-lookup"><span data-stu-id="09ecf-133">This should ask for permission to run as administrator, and then open the Configuration Manager program.</span></span>  
  
3.  <span data-ttu-id="09ecf-134">关闭 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="09ecf-134">Close [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
4.  <span data-ttu-id="09ecf-135">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器的左窗格中，选择“SQL Server 服务” 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-135">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the left pane, select **SQL Server Services**.</span></span> <span data-ttu-id="09ecf-136">在右窗格中，查找 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="09ecf-136">In the right-pane, find your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="09ecf-137">（[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的默认实例包括在计算机名称后的 **(MSSQLSERVER)** 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-137">(The default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] includes **(MSSQLSERVER)** after the computer name.</span></span> <span data-ttu-id="09ecf-138">命名实例显示为大写，名称与在“已注册的服务器”中的名称相同。）右键单击 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，然后单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="09ecf-138">Named instances appear in upper case with the same name that they have in Registered Servers.) Right-click the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="09ecf-139">在 "**启动参数**" 选项卡上的 "**指定启动参数**" 框中，键入， `-m` 然后单击 `Add` 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-139">On the **Startup Parameters** tab, in the **Specify a startup parameter** box, type `-m` and then click `Add`.</span></span> <span data-ttu-id="09ecf-140">（这是短划线后跟小写字母 m。）</span><span class="sxs-lookup"><span data-stu-id="09ecf-140">(That's a dash then lower case letter m.)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="09ecf-141">对于某些早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，没有“启动参数”  选项卡。在这种情况下，在“高级”选项卡上，双击“启动参数” 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-141">For some earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] there is no **Startup Parameters** tab. In that case, on the **Advanced** tab, double-click **Startup Parameters**.</span></span> <span data-ttu-id="09ecf-142">参数在非常小的窗口中打开。</span><span class="sxs-lookup"><span data-stu-id="09ecf-142">The parameters open up in a very small window.</span></span> <span data-ttu-id="09ecf-143">请注意不要更改任何现有参数。</span><span class="sxs-lookup"><span data-stu-id="09ecf-143">Be careful not to change any of the existing parameters.</span></span> <span data-ttu-id="09ecf-144">在最后，添加新参数 `;-m`，然后单击 `OK`。</span><span class="sxs-lookup"><span data-stu-id="09ecf-144">At the very end, add a new parameter `;-m` and then click `OK`.</span></span> <span data-ttu-id="09ecf-145">（这是一个分号，后跟短划线和小写字母 m。）</span><span class="sxs-lookup"><span data-stu-id="09ecf-145">(That's a semi-colon then a dash then lower case letter m.)</span></span>  
  
6.  <span data-ttu-id="09ecf-146">单击 `OK` ，然后在要重新启动的消息之后，右键单击您的服务器名称，然后单击 "**重新启动**"。</span><span class="sxs-lookup"><span data-stu-id="09ecf-146">Click `OK`, and after the message to restart, right-click your server name, and then click **Restart**.</span></span>  
  
7.  <span data-ttu-id="09ecf-147">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重启之后，你的服务器将处于单用户模式。</span><span class="sxs-lookup"><span data-stu-id="09ecf-147">After [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has restarted your server will be in single-user mode.</span></span> <span data-ttu-id="09ecf-148">请确保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理未在运行。</span><span class="sxs-lookup"><span data-stu-id="09ecf-148">Make sure that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is not running.</span></span> <span data-ttu-id="09ecf-149">如果启动，它将占用您唯一的连接。</span><span class="sxs-lookup"><span data-stu-id="09ecf-149">If started, it will take your only connection.</span></span>  
  
8.  <span data-ttu-id="09ecf-150">在 Windows 8 启动屏幕上，右键单击 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的图标。</span><span class="sxs-lookup"><span data-stu-id="09ecf-150">On the Windows 8 start screen, right-click the icon for [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="09ecf-151">在屏幕的底部，选择““以管理员身份运行” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="09ecf-151">At the bottom of the screen, select **Run as administrator**.</span></span> <span data-ttu-id="09ecf-152">（这会将您的管理员凭据传递到 SSMS。）</span><span class="sxs-lookup"><span data-stu-id="09ecf-152">(This will pass your administrator credentials to SSMS.)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="09ecf-153">对于 Windows 的早期版本，“以管理员身份运行”选项显示为子菜单。</span><span class="sxs-lookup"><span data-stu-id="09ecf-153">For earlier versions of Windows, the **Run as administrator** option appears as a sub-menu.</span></span>  
  
     <span data-ttu-id="09ecf-154">在某些配置中，SSMS 将尝试进行多个连接。</span><span class="sxs-lookup"><span data-stu-id="09ecf-154">In some configurations, SSMS will attempt to make several connections.</span></span> <span data-ttu-id="09ecf-155">多个连接将失败，因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 处于单用户模式。</span><span class="sxs-lookup"><span data-stu-id="09ecf-155">Multiple connections will fail because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is in single-user mode.</span></span> <span data-ttu-id="09ecf-156">可以选择执行以下操作之一。</span><span class="sxs-lookup"><span data-stu-id="09ecf-156">You can select one of the following actions to perform.</span></span> <span data-ttu-id="09ecf-157">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="09ecf-157">Do one of the following.</span></span>  
  
    1.  <span data-ttu-id="09ecf-158">使用 Windows 身份验证（包括您的管理员凭据）与对象资源管理器连接。</span><span class="sxs-lookup"><span data-stu-id="09ecf-158">Connect with Object Explorer using Windows Authentication (which includes your Administrator credentials).</span></span> <span data-ttu-id="09ecf-159">依次展开“安全性”和“登录名”，然后双击你自己的登录名 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-159">Expand **Security**, expand **Logins**, and double-click your own login.</span></span> <span data-ttu-id="09ecf-160">在 "**服务器角色**" 页上，选择 `sysadmin` ，然后单击 `OK` 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-160">On the **Server Roles** page, select `sysadmin`, and then click `OK`.</span></span>  
  
    2.  <span data-ttu-id="09ecf-161">使用 Windows 身份验证（包括您的管理员凭据）与“查询窗口”连接，而非与对象资源管理器连接。</span><span class="sxs-lookup"><span data-stu-id="09ecf-161">Instead of connecting with Object Explorer, connect with a Query Window using Windows Authentication (which includes your Administrator credentials).</span></span> <span data-ttu-id="09ecf-162"> (如果未连接到对象资源管理器，则只能通过这种方式进行连接。 ) 执行代码（如下所示）来添加作为 `sysadmin` 固定服务器角色成员的新 Windows 身份验证登录名。</span><span class="sxs-lookup"><span data-stu-id="09ecf-162">(You can only connect this way if you did not connect with Object Explorer.) Execute code such as the following to add a new Windows Authentication login that is a member of the `sysadmin` fixed server role.</span></span> <span data-ttu-id="09ecf-163">以下示例添加名为 `CONTOSO\PatK`的域用户。</span><span class="sxs-lookup"><span data-stu-id="09ecf-163">The following example adds a domain user named `CONTOSO\PatK`.</span></span>  
  
        ```  
        CREATE LOGIN [CONTOSO\PatK] FROM WINDOWS;  
        ALTER SERVER ROLE sysadmin ADD MEMBER [CONTOSO\PatK];  
        ```  
  
    3.  <span data-ttu-id="09ecf-164">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在混合身份验证模式下运行，请使用 Windows 身份验证（包括您的管理员凭据）与“查询窗口”连接。</span><span class="sxs-lookup"><span data-stu-id="09ecf-164">If your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running in mixed authentication mode, connect with a Query Window using Windows Authentication (which includes your Administrator credentials).</span></span> <span data-ttu-id="09ecf-165">执行以下代码，以创建作为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定服务器角色成员的新身份验证登录名 `sysadmin` 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-165">Execute code such as the following to create a new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login that is a member of the `sysadmin` fixed server role.</span></span>  
  
        ```  
        CREATE LOGIN TempLogin WITH PASSWORD = '************';  
        ALTER SERVER ROLE sysadmin ADD MEMBER TempLogin;  
        ```  
  
        > [!WARNING]  
        >  <span data-ttu-id="09ecf-166">使用强密码替换 \*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="09ecf-166">Replace \*\*\*\*\*\*\*\*\*\*\*\* with a strong password.</span></span>  
  
    4.  <span data-ttu-id="09ecf-167">如果你正在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 混合身份验证模式下运行，并且你希望重置该帐户的密码 `sa` ，请使用 Windows 身份验证 (，其中包括你的管理员凭据) 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-167">If your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running in mixed authentication mode and you want to reset the password of the `sa` account, connect with a Query Window using Windows Authentication (which includes your Administrator credentials).</span></span> <span data-ttu-id="09ecf-168">`sa`用以下语法更改帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="09ecf-168">Change the password of the `sa` account with the following syntax.</span></span>  
  
        ```  
        ALTER LOGIN sa WITH PASSWORD = '************';  
        ```  
  
        > [!WARNING]  
        >  <span data-ttu-id="09ecf-169">使用强密码替换 \*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="09ecf-169">Replace \*\*\*\*\*\*\*\*\*\*\*\* with a strong password.</span></span>  
  
9. <span data-ttu-id="09ecf-170">以下步骤现在将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 改回多用户模式。</span><span class="sxs-lookup"><span data-stu-id="09ecf-170">The following steps now change [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] back to multi-user mode.</span></span> <span data-ttu-id="09ecf-171">关闭 SSMS。</span><span class="sxs-lookup"><span data-stu-id="09ecf-171">Close SSMS.</span></span>  
  
10. <span data-ttu-id="09ecf-172">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器的左窗格中，选择“SQL Server 服务” 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-172">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the left pane, select **SQL Server Services**.</span></span> <span data-ttu-id="09ecf-173">在右侧窗格中，右键单击 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，然后单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="09ecf-173">In the right-pane, right-click the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then click **Properties**.</span></span>  
  
11. <span data-ttu-id="09ecf-174">在 "**启动参数**" 选项卡上的 "**现有参数**" 框中，选择， `-m` 然后单击 `Remove` 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-174">On the **Startup Parameters** tab, in the **Existing parameters** box, select `-m` and then click `Remove`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="09ecf-175">对于某些早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，没有“启动参数”  选项卡。在这种情况下，在“高级”选项卡上，双击“启动参数” 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-175">For some earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] there is no **Startup Parameters** tab. In that case, on the **Advanced** tab, double-click **Startup Parameters**.</span></span> <span data-ttu-id="09ecf-176">参数在非常小的窗口中打开。</span><span class="sxs-lookup"><span data-stu-id="09ecf-176">The parameters open up in a very small window.</span></span> <span data-ttu-id="09ecf-177">删除 `;-m` 之前添加的，然后单击 "删除" `OK` 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-177">Remove the `;-m` which you added earlier, and then click `OK`.</span></span>  
  
12. <span data-ttu-id="09ecf-178">右键单击你的服务器名称，然后单击“重启”。</span><span class="sxs-lookup"><span data-stu-id="09ecf-178">Right-click your server name, and then click **Restart**.</span></span>  
  
 <span data-ttu-id="09ecf-179">现在，你应该能够使用现在为固定服务器角色的成员的某个帐户进行连接 `sysadmin` 。</span><span class="sxs-lookup"><span data-stu-id="09ecf-179">Now you should be able to connect normally with one of the accounts which is now a member of the `sysadmin` fixed server role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ecf-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09ecf-180">See Also</span></span>  
 <span data-ttu-id="09ecf-181">[在单用户模式下启动 SQL Server](start-sql-server-in-single-user-mode.md) </span><span class="sxs-lookup"><span data-stu-id="09ecf-181">[Start SQL Server in Single-User Mode](start-sql-server-in-single-user-mode.md) </span></span>  
 [<span data-ttu-id="09ecf-182">数据库引擎服务启动选项</span><span class="sxs-lookup"><span data-stu-id="09ecf-182">Database Engine Service Startup Options</span></span>](database-engine-service-startup-options.md)  
  
  
