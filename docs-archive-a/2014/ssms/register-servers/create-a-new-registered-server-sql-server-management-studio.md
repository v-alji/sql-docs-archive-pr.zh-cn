---
title: 新建已注册的服务器
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.general.sqlce.f1
- sql12.swb.registerserver.general.sqlserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], creating new registered servers
ms.assetid: 716ea070-a3b5-4514-9de2-82ce8a96514b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 43cdb06179531a739f6595dc5ade9eeb79ea65ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576499"
---
# <a name="create-a-new-registered-server-sql-server-management-studio"></a><span data-ttu-id="d6292-102">创建新的已注册的服务器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="d6292-102">Create a New Registered Server (SQL Server Management Studio)</span></span>
  <span data-ttu-id="d6292-103">本主题介绍如何通过在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的已注册服务器组件中注册服务器，以保存经常访问的服务器的连接信息。</span><span class="sxs-lookup"><span data-stu-id="d6292-103">This topic describes how to save the connection information for servers that you access frequently, by registering the server in the Registered Servers component of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="d6292-104">您可以在连接之前注册服务器，也可以在从对象资源管理器中进行连接时注册服务器。</span><span class="sxs-lookup"><span data-stu-id="d6292-104">A server can be registered before connecting, or when connecting from Object Explorer.</span></span> <span data-ttu-id="d6292-105">对象资源管理器中有注册本地计算机上的服务器实例的专用菜单选项。</span><span class="sxs-lookup"><span data-stu-id="d6292-105">There is a special menu option to register the server instances on the local computer.</span></span>  
  
 <span data-ttu-id="d6292-106">共有两种类型的已注册服务器：</span><span class="sxs-lookup"><span data-stu-id="d6292-106">There are two kinds of registered servers:</span></span>  
  
-   <span data-ttu-id="d6292-107">本地服务器组</span><span class="sxs-lookup"><span data-stu-id="d6292-107">Local server groups</span></span>  
  
     <span data-ttu-id="d6292-108">可以使用本地服务器组方便地连接到经常管理的服务器。</span><span class="sxs-lookup"><span data-stu-id="d6292-108">Use local server groups to easily connect to servers that you frequently manage.</span></span> <span data-ttu-id="d6292-109">本地服务器和非本地服务器都是在本地服务器组中注册的。</span><span class="sxs-lookup"><span data-stu-id="d6292-109">Both local and non-local servers are registered into local server groups.</span></span> <span data-ttu-id="d6292-110">对于每个用户来说，本地服务器组是唯一的。</span><span class="sxs-lookup"><span data-stu-id="d6292-110">Local server groups are unique to each user.</span></span> <span data-ttu-id="d6292-111">有关如何共享已注册的服务器信息，请参阅 [导出已注册服务器信息 (SQL Server Management Studio)](export-registered-server-information-sql-server-management-studio.md) 和 [导入已注册的服务器信息 (SQL Server Management Studio)](import-registered-server-information-sql-server-management-studio.md)的已注册服务器组件中注册服务器，以保存经常访问的服务器的连接信息。</span><span class="sxs-lookup"><span data-stu-id="d6292-111">For information about how to share registered server information, see [Export Registered Server Information &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) and [Import Registered Server Information &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6292-112">建议您尽量使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="d6292-112">We recommend that you use Windows Authentication whenever possible.</span></span>  
  
-   <span data-ttu-id="d6292-113">中央管理服务器</span><span class="sxs-lookup"><span data-stu-id="d6292-113">Central Management Servers</span></span>  
  
     <span data-ttu-id="d6292-114">中央管理服务器将服务器注册信息存储在中央管理服务器中，而不是存储在文件系统中。</span><span class="sxs-lookup"><span data-stu-id="d6292-114">Central Management Servers store server registrations in the Central Management Server instead of on the file system.</span></span> <span data-ttu-id="d6292-115">只能使用 Windows 身份验证来注册中央管理服务器和已注册的从属服务器。</span><span class="sxs-lookup"><span data-stu-id="d6292-115">Central Management Servers and subordinate registered servers can be registered only by using Windows Authentication.</span></span> <span data-ttu-id="d6292-116">中央管理服务器注册完毕后，与其关联的已注册服务器将自动显示出来。</span><span class="sxs-lookup"><span data-stu-id="d6292-116">After a Central Management Server has been registered, its associated registered servers will be automatically displayed.</span></span> <span data-ttu-id="d6292-117">有关详细信息，请参阅 [使用中央管理服务器管理多台服务器](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="d6292-117">For more information about Central Management Servers, see [Administer Multiple Servers Using Central Management Servers](../../relational-databases/administer-multiple-servers-using-central-management-servers.md).</span></span> <span data-ttu-id="d6292-118">不能将早于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 指定为中央管理服务器。</span><span class="sxs-lookup"><span data-stu-id="d6292-118">Versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] cannot be designated as a Central Management Server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d6292-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d6292-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-automatically-register-the-local-server-instances"></a><span data-ttu-id="d6292-120">自动注册本地服务器实例</span><span class="sxs-lookup"><span data-stu-id="d6292-120">To automatically register the local server instances</span></span>  
  
-   <span data-ttu-id="d6292-121">在“已注册的服务器”中，右键单击已注册的服务器树中的任意节点，再单击“更新本地服务器注册”  。</span><span class="sxs-lookup"><span data-stu-id="d6292-121">In Registered Servers, right-click any node in the Registered Servers tree, and then click **Update Local Server Registration**.</span></span>  
  
#### <a name="to-create-a-new-registered-server"></a><span data-ttu-id="d6292-122">创建新的已注册的服务器</span><span class="sxs-lookup"><span data-stu-id="d6292-122">To create a new registered server</span></span>  
  
1.  <span data-ttu-id="d6292-123">如果已注册的服务器在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中没有出现，请在 **“视图”** 菜单上，单击 **“已注册的服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="d6292-123">If Registered Servers is not visible in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
     <span data-ttu-id="d6292-124">**服务器类型**</span><span class="sxs-lookup"><span data-stu-id="d6292-124">**Server type**</span></span>  
     <span data-ttu-id="d6292-125">从“已注册的服务器”中注册某服务器时，“服务器类型”  框是只读的，它与“已注册的服务器”窗格中显示的服务器类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="d6292-125">When a server is registered from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers pane.</span></span> <span data-ttu-id="d6292-126">若要注册其他类型的服务器，请在开始注册新服务器之前，在 **“已注册的服务器”** 工具栏上依次单击 **“数据库引擎”** 、 **“分析服务器”** 、 **Reporting Services** 或 **Integration Services** 。</span><span class="sxs-lookup"><span data-stu-id="d6292-126">To register a different type of server, click **Database Engine**, **Analysis Server**, **Reporting Services**, or **Integration Services** on the **Registered Servers** toolbar before starting to register a new server.</span></span>  
  
     <span data-ttu-id="d6292-127">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="d6292-127">**Server name**</span></span>  
     <span data-ttu-id="d6292-128">选择要注册的服务器实例，格式为： *\<servername>* [ \\ *\<instancename>* ]。</span><span class="sxs-lookup"><span data-stu-id="d6292-128">Select the server instance to register in the format: *\<servername>*[\\*\<instancename>*].</span></span>  
  
     <span data-ttu-id="d6292-129">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="d6292-129">**Authentication**</span></span>  
     <span data-ttu-id="d6292-130">在连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例时，可以使用两种身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="d6292-130">Two authentication modes are available when connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="d6292-131">**Windows 身份验证**</span><span class="sxs-lookup"><span data-stu-id="d6292-131">**Windows Authentication**</span></span>  
     <span data-ttu-id="d6292-132">Windows 身份验证模式允许用户通过 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 用户帐户进行连接。</span><span class="sxs-lookup"><span data-stu-id="d6292-132">Windows Authentication mode allows a user to connect through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
     <span data-ttu-id="d6292-133">**SQL Server 身份验证**</span><span class="sxs-lookup"><span data-stu-id="d6292-133">**SQL Server Authentication**</span></span>  
     <span data-ttu-id="d6292-134">当用户使用指定的登录名和密码通过不可信连接进行连接时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将自行进行身份验证，即检查是否已设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录帐户以及指定的密码是否与以前记录的密码相匹配。</span><span class="sxs-lookup"><span data-stu-id="d6292-134">When a user connects with a specified login name and password from a nontrusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking whether a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and whether the specified password matches the one previously recorded.</span></span> <span data-ttu-id="d6292-135">如果未设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录帐户，则身份验证失败，并且用户会收到一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="d6292-135">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)] <span data-ttu-id="d6292-136">有关详细信息，请参阅 [选择身份验证模式](../../relational-databases/security/choose-an-authentication-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="d6292-136">For more information, see [Choose an Authentication Mode](../../relational-databases/security/choose-an-authentication-mode.md).</span></span>  
  
     <span data-ttu-id="d6292-137">**用户名**</span><span class="sxs-lookup"><span data-stu-id="d6292-137">**User name**</span></span>  
     <span data-ttu-id="d6292-138">显示当前连接所使用的用户名。</span><span class="sxs-lookup"><span data-stu-id="d6292-138">Shows the current user name you are connecting with.</span></span> <span data-ttu-id="d6292-139">只有在已选择使用 Windows 身份验证进行连接的情况下，此只读选项才可用。</span><span class="sxs-lookup"><span data-stu-id="d6292-139">This read-only option is only available if you have selected to connect using Windows Authentication.</span></span> <span data-ttu-id="d6292-140">若要更改 **“用户名”** ，请以其他用户身份登录计算机。</span><span class="sxs-lookup"><span data-stu-id="d6292-140">To change **User names**, log in to the computer as a different user.</span></span>  
  
     <span data-ttu-id="d6292-141">**登录**</span><span class="sxs-lookup"><span data-stu-id="d6292-141">**Login**</span></span>  
     <span data-ttu-id="d6292-142">输入连接所用的登录名。</span><span class="sxs-lookup"><span data-stu-id="d6292-142">Enter the login to connect with.</span></span> <span data-ttu-id="d6292-143">只有选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="d6292-143">This option is available only if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="d6292-144">**密码**</span><span class="sxs-lookup"><span data-stu-id="d6292-144">**Password**</span></span>  
     <span data-ttu-id="d6292-145">输入登录名的密码。</span><span class="sxs-lookup"><span data-stu-id="d6292-145">Enter the password for the login.</span></span> <span data-ttu-id="d6292-146">只有在已选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接的情况下，此选项才是可编辑的。</span><span class="sxs-lookup"><span data-stu-id="d6292-146">This option can be edited only if you have selected to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="d6292-147">**记住密码**</span><span class="sxs-lookup"><span data-stu-id="d6292-147">**Remember password**</span></span>  
     <span data-ttu-id="d6292-148">选择此选项，可以让 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对输入的密码进行加密并存储。</span><span class="sxs-lookup"><span data-stu-id="d6292-148">Select to have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] encrypt and store the password you have entered.</span></span> <span data-ttu-id="d6292-149">只有在已选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接的情况下，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="d6292-149">This option is displayed only if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6292-150">如果已经存储了此密码，而现在要放弃存储，请清除此复选框，再单击“保存”  。</span><span class="sxs-lookup"><span data-stu-id="d6292-150">If you have stored the password and want to stop storing it, clear this check box, and then click **Save**.</span></span>  
  
     <span data-ttu-id="d6292-151">**已注册的服务器名称**</span><span class="sxs-lookup"><span data-stu-id="d6292-151">**Registered server name**</span></span>  
     <span data-ttu-id="d6292-152">希望在“已注册的服务器”中显示的名称。</span><span class="sxs-lookup"><span data-stu-id="d6292-152">The name you want to appear in Registered Servers.</span></span> <span data-ttu-id="d6292-153">此名称不必与 **“服务器名称”** 框中的内容匹配。</span><span class="sxs-lookup"><span data-stu-id="d6292-153">This name does not have to match the **Server name** box.</span></span>  
  
     <span data-ttu-id="d6292-154">**已注册的服务器说明**</span><span class="sxs-lookup"><span data-stu-id="d6292-154">**Registered server description**</span></span>  
     <span data-ttu-id="d6292-155">输入服务器的说明（可选）。</span><span class="sxs-lookup"><span data-stu-id="d6292-155">Enter an optional description of the server.</span></span>  
  
     <span data-ttu-id="d6292-156">**Test**</span><span class="sxs-lookup"><span data-stu-id="d6292-156">**Test**</span></span>  
     <span data-ttu-id="d6292-157">单击此项可测试与“服务器名称”  中所选服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="d6292-157">Click to test the connection to the server selected in **Server name**.</span></span>  
  
     <span data-ttu-id="d6292-158">**保存**</span><span class="sxs-lookup"><span data-stu-id="d6292-158">**Save**</span></span>  
     <span data-ttu-id="d6292-159">单击此项可保存已注册服务器的设置。</span><span class="sxs-lookup"><span data-stu-id="d6292-159">Click to save the registered server settings.</span></span>  
  
## <a name="multiserver-queries"></a><span data-ttu-id="d6292-160">多服务器查询</span><span class="sxs-lookup"><span data-stu-id="d6292-160">Multiserver Queries</span></span>  
 <span data-ttu-id="d6292-161">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的查询编辑器窗口可以同时连接到多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例并对其进行查询。</span><span class="sxs-lookup"><span data-stu-id="d6292-161">The Query Editor window in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] can connect to and query multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] at the same time.</span></span> <span data-ttu-id="d6292-162">可以将查询返回的结果合并到单个结果窗格中，也可以在单独结果窗格中返回这些结果。</span><span class="sxs-lookup"><span data-stu-id="d6292-162">The results that are returned by the query can be merged into a single results pane, or they can be returned in separate results panes.</span></span> <span data-ttu-id="d6292-163">查询编辑器可以选择包含一些列（提供生成每个行的服务器名称）以及登录名（用于连接到提供每个行的服务器）。</span><span class="sxs-lookup"><span data-stu-id="d6292-163">As an option, Query Editor can include columns that provide the name of the server that produced each row, and also the login that was used to connect to the server that provided each row.</span></span> <span data-ttu-id="d6292-164">有关如何执行多服务器查询的详细信息，请参阅[同时对多个服务器执行语句 (SQL Server Management Studio)](execute-statements-against-multiple-servers-simultaneously.md)。</span><span class="sxs-lookup"><span data-stu-id="d6292-164">For more information about how to execute multiserver queries, see [Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md).</span></span>  
  
 <span data-ttu-id="d6292-165">若要对本地服务器组中的所有服务器执行查询，请右键单击该服务器组，指向并单击“连接”  ，然后单击“新建查询”  。</span><span class="sxs-lookup"><span data-stu-id="d6292-165">To execute queries against all the servers in a local server group, right-click the server group, point to click **Connect**, and then click **New Query**.</span></span> <span data-ttu-id="d6292-166">在新的查询编辑器窗口中执行查询时，将利用存储的连接信息（包括用户身份验证上下文）对该组中的全部服务器进行查询。</span><span class="sxs-lookup"><span data-stu-id="d6292-166">When queries are executed in the new Query Editor window, they will execute against all servers in the group, using the stored connection information including the user authentication context.</span></span> <span data-ttu-id="d6292-167">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证注册服务器但未保存密码，服务器将无法进行连接。</span><span class="sxs-lookup"><span data-stu-id="d6292-167">Servers registered by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication but not saving the password will fail to connect.</span></span>  
  
 <span data-ttu-id="d6292-168">若要对注册到中央管理服务器的所有服务器执行查询，请展开此中央管理服务器，右键单击服务器组，指向并单击“连接”  ，然后单击“新建查询”  。</span><span class="sxs-lookup"><span data-stu-id="d6292-168">To execute queries against all the servers that are registered with a Central Management Server, expand the Central Management Server, right-click the server group, point to click **Connect**, and then click **New Query**.</span></span> <span data-ttu-id="d6292-169">在新的查询编辑器窗口中执行查询时，将使用存储的连接信息以及用户的 Windows 身份验证上下文对服务器组中的所有服务器执行查询。</span><span class="sxs-lookup"><span data-stu-id="d6292-169">When queries are executed in the new Query Editor window, they will execute against all of the servers in the server group, using the stored connection information and using the Windows Authentication context of the user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6292-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6292-170">See Also</span></span>  
 <span data-ttu-id="d6292-171">[在对象资源管理器中隐藏系统对象](../object/hide-system-objects-in-object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="d6292-171">[Hide System Objects in Object Explorer](../object/hide-system-objects-in-object-explorer.md) </span></span>  
 <span data-ttu-id="d6292-172">[导出已注册服务器信息 (SQL Server Management Studio)](export-registered-server-information-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="d6292-172">[Export Registered Server Information &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="d6292-173">导入已注册的服务器信息 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="d6292-173">Import Registered Server Information &#40;SQL Server Management Studio&#41;</span></span>](import-registered-server-information-sql-server-management-studio.md)  
  
  
