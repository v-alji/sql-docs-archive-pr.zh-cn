---
title: 创建链接服务器（SQL Server 数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 11/20/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.linkedserver.properties.general.f1
- sql12.swb.linkedserver.properties.security.f1
- sql12.swb.linkedserver.properties.provider.f1
- sql12.swb.linkedserver.properties.options.f1
helpviewer_keywords:
- linked servers [SQL Server], creating
ms.assetid: 3228065d-de8f-4ece-a9b1-e06d3dca9310
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6b28468db1024a9789364e5b6e5c115cba71fa9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688911"
---
# <a name="create-linked-servers-sql-server-database-engine"></a><span data-ttu-id="787e9-102">创建链接服务器（SQL Server 数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="787e9-102">Create Linked Servers (SQL Server Database Engine)</span></span>
  <span data-ttu-id="787e9-103">本主题说明如何通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 创建链接服务器和访问来自其他 [!INCLUDE[tsql](../../includes/tsql-md.md)]的数据。</span><span class="sxs-lookup"><span data-stu-id="787e9-103">This topic shows how to create a linked server and access data from another [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="787e9-104">通过创建链接服务器，您可以使用来自多个数据源的数据。</span><span class="sxs-lookup"><span data-stu-id="787e9-104">By creating a linked server,  you can work with data from multiple sources.</span></span> <span data-ttu-id="787e9-105">该链接服务器不必是其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例，尽管这种情况很常见。</span><span class="sxs-lookup"><span data-stu-id="787e9-105">The linked server does not have to be another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but that is a common scenario.</span></span>  
  
##  <a name="background"></a><a name="Background"></a> <span data-ttu-id="787e9-106">背景</span><span class="sxs-lookup"><span data-stu-id="787e9-106">Background</span></span>  
 <span data-ttu-id="787e9-107">链接服务器让用户可以对 OLE DB 数据源进行分布式异类查询。</span><span class="sxs-lookup"><span data-stu-id="787e9-107">A linked server allows for access to distributed, heterogeneous queries against OLE DB data sources.</span></span> <span data-ttu-id="787e9-108">在创建某一链接服务器后，可对该服务器运行分布式查询，并且查询可以联接来自多个数据源的表。</span><span class="sxs-lookup"><span data-stu-id="787e9-108">After a linked server is created, distributed queries can be run against this server, and queries can join tables from more than one data source.</span></span> <span data-ttu-id="787e9-109">如果链接服务器定义为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例，则可执行远程存储过程。</span><span class="sxs-lookup"><span data-stu-id="787e9-109">If the linked server is defined as an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], remote stored procedures can be executed.</span></span>  
  
 <span data-ttu-id="787e9-110">链接服务器的功能和必需的参数可能会有很大差异。</span><span class="sxs-lookup"><span data-stu-id="787e9-110">The capabilities and required arguments of the linked server can vary significantly.</span></span> <span data-ttu-id="787e9-111">本主题中的示例是典型示例，但并未描述所有选项。</span><span class="sxs-lookup"><span data-stu-id="787e9-111">The examples in this topic provide a typical example but all options are not described.</span></span> <span data-ttu-id="787e9-112">有关详细信息，请参阅 [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)的数据。</span><span class="sxs-lookup"><span data-stu-id="787e9-112">For more information, see [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="787e9-113">Security</span><span class="sxs-lookup"><span data-stu-id="787e9-113">Security</span></span>  
  
### <a name="permissions"></a><span data-ttu-id="787e9-114">权限</span><span class="sxs-lookup"><span data-stu-id="787e9-114">Permissions</span></span>  
 <span data-ttu-id="787e9-115">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句时，需要 `ALTER ANY LINKED SERVER` 对服务器的权限或**setupadmin**固定服务器角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="787e9-115">When using [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, requires `ALTER ANY LINKED SERVER` permission on the server or membership in the **setupadmin** fixed server role.</span></span> <span data-ttu-id="787e9-116">当使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 需要 `CONTROL SERVER` 权限或**sysadmin**固定服务器角色的成员身份时。</span><span class="sxs-lookup"><span data-stu-id="787e9-116">When using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] requires `CONTROL SERVER` permission or membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="how-to-create-a-linked-server"></a><a name="Procedures"></a> <span data-ttu-id="787e9-117">如何创建链接服务器</span><span class="sxs-lookup"><span data-stu-id="787e9-117">How to Create a Linked Server</span></span>  
 <span data-ttu-id="787e9-118">您可以使用以下任意一项：</span><span class="sxs-lookup"><span data-stu-id="787e9-118">You can use any of the following:</span></span>  
  
-   [<span data-ttu-id="787e9-119">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="787e9-119">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="787e9-120">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="787e9-120">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="787e9-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="787e9-121">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-linked-server-to-another-instance-of-sql-server-using-sql-server-management-studio"></a><span data-ttu-id="787e9-122">使用 SQL Server Management Studio 创建与其他 SQL Server 实例的链接服务器</span><span class="sxs-lookup"><span data-stu-id="787e9-122">To create a linked server to another instance of SQL Server Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="787e9-123">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，打开对象资源管理器，展开 **“服务器对象”** ，右键单击 **“链接服务器”** ，然后单击 **“新建链接服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="787e9-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer, expand **Server Objects**, right-click **Linked Servers**, and then click **New Linked Server**.</span></span>  
  
2.  <span data-ttu-id="787e9-124">在 **“常规”** 页上的 **“链接服务器”** 框中，键入您链接到的 **SQL Server** 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="787e9-124">On the **General** page, in the **Linked server** box, type the name of the instance of **SQL Server** that you area linking to.</span></span>  
  
     <span data-ttu-id="787e9-125">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="787e9-125">**SQL Server**</span></span>  
     <span data-ttu-id="787e9-126">将链接服务器标识为 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="787e9-126">Identify the linked server as an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="787e9-127">如果您使用此方法来定义某个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 链接服务器，则在 **“链接服务器”** 中指定的名称必须是该服务器的网络名称。</span><span class="sxs-lookup"><span data-stu-id="787e9-127">If you use this method of defining a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] linked server, the name specified in **Linked server** must be the network name of the server.</span></span> <span data-ttu-id="787e9-128">另外，从该服务器上检索的所有表都来自该链接服务器上为相应登录名所定义的默认数据库。</span><span class="sxs-lookup"><span data-stu-id="787e9-128">Also, any tables retrieved from the server are from the default database defined for the login on the linked server.</span></span>  
  
     <span data-ttu-id="787e9-129">**其他数据源**</span><span class="sxs-lookup"><span data-stu-id="787e9-129">**Other data source**</span></span>  
     <span data-ttu-id="787e9-130">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以外的 OLE DB 服务器类型。</span><span class="sxs-lookup"><span data-stu-id="787e9-130">Specify an OLE DB server type other than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="787e9-131">单击此选项将激活其下面的选项。</span><span class="sxs-lookup"><span data-stu-id="787e9-131">Clicking this option activates the options below it.</span></span>  
  
     <span data-ttu-id="787e9-132">**提供程序**</span><span class="sxs-lookup"><span data-stu-id="787e9-132">**Provider**</span></span>  
     <span data-ttu-id="787e9-133">从列表框中选择 OLE DB 数据源。</span><span class="sxs-lookup"><span data-stu-id="787e9-133">Select an OLE DB data source from the list box.</span></span> <span data-ttu-id="787e9-134">OLE DB 访问接口是使用注册表中给定的 PROGID 注册的。</span><span class="sxs-lookup"><span data-stu-id="787e9-134">The OLE DB provider is registered with the given PROGID in the registry.</span></span>  
  
     <span data-ttu-id="787e9-135">**产品名称**</span><span class="sxs-lookup"><span data-stu-id="787e9-135">**Product name**</span></span>  
     <span data-ttu-id="787e9-136">键入要作为链接服务器添加的 OLE DB 数据源的产品名称。</span><span class="sxs-lookup"><span data-stu-id="787e9-136">Type the product name of the OLE DB data source to add as a linked server.</span></span>  
  
     <span data-ttu-id="787e9-137">**数据源**</span><span class="sxs-lookup"><span data-stu-id="787e9-137">**Data source**</span></span>  
     <span data-ttu-id="787e9-138">根据 OLE DB 访问接口的说明，键入数据源名称。</span><span class="sxs-lookup"><span data-stu-id="787e9-138">Type the name of the data source as interpreted by the OLE DB provider.</span></span> <span data-ttu-id="787e9-139">如果要连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例，请提供实例名称。</span><span class="sxs-lookup"><span data-stu-id="787e9-139">If you are connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], provide the instance name.</span></span>  
  
     <span data-ttu-id="787e9-140">**访问接口字符串**</span><span class="sxs-lookup"><span data-stu-id="787e9-140">**Provider string**</span></span>  
     <span data-ttu-id="787e9-141">键入与数据源相对应的 OLE DB 访问接口的唯一编程标识符 (PROGID)。</span><span class="sxs-lookup"><span data-stu-id="787e9-141">Type the unique programmatic identifier (PROGID) of the OLE DB provider that corresponds to the data source.</span></span> <span data-ttu-id="787e9-142">有关有效访问接口字符串的示例，请参阅 [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)的数据。</span><span class="sxs-lookup"><span data-stu-id="787e9-142">For examples of valid provider strings, see [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>  
  
     <span data-ttu-id="787e9-143">**位置**</span><span class="sxs-lookup"><span data-stu-id="787e9-143">**Location**</span></span>  
     <span data-ttu-id="787e9-144">根据 OLE DB 访问接口的说明，键入数据库的位置。</span><span class="sxs-lookup"><span data-stu-id="787e9-144">Type the location of the database as interpreted by the OLE DB provider.</span></span>  
  
     <span data-ttu-id="787e9-145">**目录**</span><span class="sxs-lookup"><span data-stu-id="787e9-145">**Catalog**</span></span>  
     <span data-ttu-id="787e9-146">键入在连接 OLE DB 访问接口时要使用的目录的名称。</span><span class="sxs-lookup"><span data-stu-id="787e9-146">Type the name of the catalog to use when making a connection to the OLE DB provider.</span></span>  
  
     <span data-ttu-id="787e9-147">若要测试能否连接到链接服务器，请在对象资源管理器中，右键单击链接服务器，然后单击 **“测试连接”** 。</span><span class="sxs-lookup"><span data-stu-id="787e9-147">To test the ability to connect to a linked server, in Object Explorer, right-click the linked server and then click **Test Connection**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="787e9-148">如果该 **SQL Server** 实例是默认实例，则输入承载 **SQL Server**实例的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="787e9-148">If the instance of **SQL Server** is the default instance, enter the name of the computer that hosts the instance of **SQL Server**.</span></span> <span data-ttu-id="787e9-149">如果该 **SQL Server** 是命名实例，则输入计算机名称和实例名称，例如 **Accounting\SQLExpress**。</span><span class="sxs-lookup"><span data-stu-id="787e9-149">If the **SQL Server** is a named instance, enter the name of the computer and the name of the instance, such as **Accounting\SQLExpress**.</span></span>  
  
3.  <span data-ttu-id="787e9-150">在“服务器类型”区域中，选择 SQL Server 以便指示该链接服务器是 SQL Server的另一个实例    。</span><span class="sxs-lookup"><span data-stu-id="787e9-150">In the **Server type** area, select **SQL Server** to indicate that the linked server is another instance of **SQL Server**.</span></span>  
  
4.  <span data-ttu-id="787e9-151">在 **“安全性”** 页上，指定在原始 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接到链接服务器时将使用的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="787e9-151">On the **Security** page, specify the security context that will be used when the original [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to the linked server.</span></span> <span data-ttu-id="787e9-152">在通过使用其域登录名连接用户的域环境中，选择“使用登录名的当前安全上下文建立连接”通常是最佳选择  。</span><span class="sxs-lookup"><span data-stu-id="787e9-152">In a domain environment where users are connecting by using their domain logins, selecting **Be made using the login's current security context** is often the best choice.</span></span> <span data-ttu-id="787e9-153">在用户通过使用 **SQL Server** 登录名连接到原始 **SQL Server** 时，最佳选择通常是选择 **“通过使用此安全上下文”** ，然后提供在链接服务器上进行身份验证时所必需的凭据。</span><span class="sxs-lookup"><span data-stu-id="787e9-153">When users connect to the original **SQL Server** by using a **SQL Server** login, the best choice is often to select **By using this security context**, and then providing the necessary credentials to authenticate at the linked server.</span></span>  
  
     <span data-ttu-id="787e9-154">**本地登录**</span><span class="sxs-lookup"><span data-stu-id="787e9-154">**Local login**</span></span>  
     <span data-ttu-id="787e9-155">指定可连接到链接服务器的本地登录。</span><span class="sxs-lookup"><span data-stu-id="787e9-155">Specify the local login that can connect to the linked server.</span></span> <span data-ttu-id="787e9-156">本地登录可以是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证的登录，也可以是使用 Windows 身份验证的登录。</span><span class="sxs-lookup"><span data-stu-id="787e9-156">The local login can be either a login using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication or a Windows Authentication login.</span></span> <span data-ttu-id="787e9-157">使用此列表可以将连接限定为特定的登录，也可以允许某些登录使用其他登录名进行连接。</span><span class="sxs-lookup"><span data-stu-id="787e9-157">Use this list to restrict the connection to specific logins, or to allow some logins to connect as a different login.</span></span>  
  
     <span data-ttu-id="787e9-158">**Impersonate**</span><span class="sxs-lookup"><span data-stu-id="787e9-158">**Impersonate**</span></span>  
     <span data-ttu-id="787e9-159">将用户名和密码从本地登录传递到链接服务器。</span><span class="sxs-lookup"><span data-stu-id="787e9-159">Pass the username and password from the local login to the linked server.</span></span> <span data-ttu-id="787e9-160">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，具有完全相同的名称和密码的登录必须存在于远程服务器中。</span><span class="sxs-lookup"><span data-stu-id="787e9-160">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, a login with the exact same name and password must exist on the remote server.</span></span> <span data-ttu-id="787e9-161">对于 Windows 登录，登录必须是链接服务器中的有效登录。</span><span class="sxs-lookup"><span data-stu-id="787e9-161">For Windows logins, the login must be a valid login on the linked server.</span></span>  
  
     <span data-ttu-id="787e9-162">若要使用模拟功能，配置必须满足委托的要求。</span><span class="sxs-lookup"><span data-stu-id="787e9-162">To use impersonation, the configuration must meet the requirement for delegation.</span></span>  
  
     <span data-ttu-id="787e9-163">**远程用户**</span><span class="sxs-lookup"><span data-stu-id="787e9-163">**Remote User**</span></span>  
     <span data-ttu-id="787e9-164">使用远程用户映射 **“本地登录”** 中未定义的用户。</span><span class="sxs-lookup"><span data-stu-id="787e9-164">Use the remote user to map users not defined in **Local login**.</span></span> <span data-ttu-id="787e9-165">**“远程用户”** 必须是远程服务器中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证登录。</span><span class="sxs-lookup"><span data-stu-id="787e9-165">The **Remote User** must be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login on the remote server.</span></span>  
  
     <span data-ttu-id="787e9-166">**远程密码**</span><span class="sxs-lookup"><span data-stu-id="787e9-166">**Remote Password**</span></span>  
     <span data-ttu-id="787e9-167">指定远程用户的密码。</span><span class="sxs-lookup"><span data-stu-id="787e9-167">Specify the password of the Remote User.</span></span>  
  
     <span data-ttu-id="787e9-168">**添加**</span><span class="sxs-lookup"><span data-stu-id="787e9-168">**Add**</span></span>  
     <span data-ttu-id="787e9-169">添加新的本地登录。</span><span class="sxs-lookup"><span data-stu-id="787e9-169">Add a new local login.</span></span>  
  
     <span data-ttu-id="787e9-170">**移除**</span><span class="sxs-lookup"><span data-stu-id="787e9-170">**Remove**</span></span>  
     <span data-ttu-id="787e9-171">删除现有的本地登录。</span><span class="sxs-lookup"><span data-stu-id="787e9-171">Remove an existing local login.</span></span>  
  
     <span data-ttu-id="787e9-172">**不建立连接**</span><span class="sxs-lookup"><span data-stu-id="787e9-172">**Not be made**</span></span>  
     <span data-ttu-id="787e9-173">指定不对列表中未定义的登录建立连接。</span><span class="sxs-lookup"><span data-stu-id="787e9-173">Specify that a connection will not be made for logins not defined in the list.</span></span>  
  
     <span data-ttu-id="787e9-174">**不使用安全上下文建立连接**</span><span class="sxs-lookup"><span data-stu-id="787e9-174">**Be made without using a security context**</span></span>  
     <span data-ttu-id="787e9-175">指定对于列表中未定义的登录，不使用安全上下文建立连接。</span><span class="sxs-lookup"><span data-stu-id="787e9-175">Specify that a connection will be made without using a security context for logins not defined in the list.</span></span>  
  
     <span data-ttu-id="787e9-176">**使用登录当前的安全上下文建立连接**</span><span class="sxs-lookup"><span data-stu-id="787e9-176">**Be made using the login's current security context**</span></span>  
     <span data-ttu-id="787e9-177">指定对于列表中未定义的登录，使用登录的当前安全上下文建立连接。</span><span class="sxs-lookup"><span data-stu-id="787e9-177">Specify that a connection will be made using the current security context of the login for logins not defined in the list.</span></span> <span data-ttu-id="787e9-178">如果使用 Windows 身份验证连接到本地服务器，则使用 Windows 凭据连接到远程服务器。</span><span class="sxs-lookup"><span data-stu-id="787e9-178">If connected to the local server using Windows Authentication, your windows credentials will be used to connect to the remote server.</span></span> <span data-ttu-id="787e9-179">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证连接到本地服务器，则在连接到远程服务器时需要使用登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="787e9-179">If connected to the local server using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, login name and password will be used to connect to the remote server.</span></span> <span data-ttu-id="787e9-180">在这种情况下，具有完全相同的名称和密码的登录必须存在于远程服务器中。</span><span class="sxs-lookup"><span data-stu-id="787e9-180">In this case a login with the exact same name and password must exist on the remote server.</span></span>  
  
     <span data-ttu-id="787e9-181">**使用此安全上下文建立连接**</span><span class="sxs-lookup"><span data-stu-id="787e9-181">**Be made using this security context**</span></span>  
     <span data-ttu-id="787e9-182">指定对于列表中未定义的登录，使用 **“远程登录”** 和 **“使用密码”** 框中指定的登录名和密码建立连接。</span><span class="sxs-lookup"><span data-stu-id="787e9-182">Specify that a connection will be made using the login and password specified in the **Remote login** and **With password** boxes for logins not defined in the list.</span></span> <span data-ttu-id="787e9-183">远程登录必须是远程服务器中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证登录。</span><span class="sxs-lookup"><span data-stu-id="787e9-183">The remote login must be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login on the remote server.</span></span>  
  
5.  <span data-ttu-id="787e9-184">或者，若要查看或指定服务器选项，请单击 **“服务器选项”**  页。</span><span class="sxs-lookup"><span data-stu-id="787e9-184">Optionally, to view or specify server options, click the **Server Options**  page.</span></span>  
  
     <span data-ttu-id="787e9-185">**排序规则兼容**</span><span class="sxs-lookup"><span data-stu-id="787e9-185">**Collation Compatible**</span></span>  
     <span data-ttu-id="787e9-186">影响分布式查询在链接服务器上的执行。</span><span class="sxs-lookup"><span data-stu-id="787e9-186">Affects Distributed Query execution against linked servers.</span></span> <span data-ttu-id="787e9-187">如果该选项设置为 true，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 假定链接服务器中的所有字符在字符集和排序规则（或排序顺序）上与本地服务器兼容。</span><span class="sxs-lookup"><span data-stu-id="787e9-187">If this option is set to true, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assumes that all characters in the linked server are compatible with the local server, with regard to character set and collation sequence (or sort order).</span></span> <span data-ttu-id="787e9-188">这使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 得以将字符列上的比较发送给提供程序。</span><span class="sxs-lookup"><span data-stu-id="787e9-188">This enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to send comparisons on character columns to the provider.</span></span> <span data-ttu-id="787e9-189">如果没有设置该选项，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将始终在本地进行字符列上的比较。</span><span class="sxs-lookup"><span data-stu-id="787e9-189">If this option is not set, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] always evaluates comparisons on character columns locally.</span></span>  
  
     <span data-ttu-id="787e9-190">只有在确信链接服务器所对应的数据源与本地服务器有相同的字符集和排序顺序时，才应当设置该选项。</span><span class="sxs-lookup"><span data-stu-id="787e9-190">This option should be set only if it is certain that the data source corresponding to the linked server has the same character set and sort order as the local server.</span></span>  
  
     <span data-ttu-id="787e9-191">**数据访问**</span><span class="sxs-lookup"><span data-stu-id="787e9-191">**Data Access**</span></span>  
     <span data-ttu-id="787e9-192">启用和禁用链接服务器以进行分布式查询访问。</span><span class="sxs-lookup"><span data-stu-id="787e9-192">Enables and disables a linked server for distributed query access.</span></span>  
  
     <span data-ttu-id="787e9-193">**RPC**</span><span class="sxs-lookup"><span data-stu-id="787e9-193">**RPC**</span></span>  
     <span data-ttu-id="787e9-194">从指定的服务器启用 RPC。</span><span class="sxs-lookup"><span data-stu-id="787e9-194">Enables RPC from the specified server.</span></span>  
  
     <span data-ttu-id="787e9-195">**RPC Out**</span><span class="sxs-lookup"><span data-stu-id="787e9-195">**RPC Out**</span></span>  
     <span data-ttu-id="787e9-196">对指定的服务器启用 RPC。</span><span class="sxs-lookup"><span data-stu-id="787e9-196">Enables RPC to the specified server.</span></span>  
  
     <span data-ttu-id="787e9-197">**使用远程排序规则**</span><span class="sxs-lookup"><span data-stu-id="787e9-197">**Use Remote Collation**</span></span>  
     <span data-ttu-id="787e9-198">确定是使用远程列的排序规则还是使用本地服务器的排序规则。</span><span class="sxs-lookup"><span data-stu-id="787e9-198">Determines whether the collation of a remote column or of a local server will be used.</span></span>  
  
     <span data-ttu-id="787e9-199">如果为 True，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据源将使用远程列的排序规则，并且非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据源将使用排序规则名称指定的排序规则。</span><span class="sxs-lookup"><span data-stu-id="787e9-199">If true, the collation of remote columns is used for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data sources, and the collation specified in collation name is used for non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data sources.</span></span>  
  
     <span data-ttu-id="787e9-200">如果为 False，则分布式查询将始终使用本地服务器的默认排序规则，而排序规则名称和远程列的排序规则将被忽略。</span><span class="sxs-lookup"><span data-stu-id="787e9-200">If false, distributed queries will always use the default collation of the local server, while collation name and the collation of remote columns are ignored.</span></span> <span data-ttu-id="787e9-201">默认值为 false。</span><span class="sxs-lookup"><span data-stu-id="787e9-201">The default is false.</span></span>  
  
     <span data-ttu-id="787e9-202">**排序规则名称**</span><span class="sxs-lookup"><span data-stu-id="787e9-202">**Collation Name**</span></span>  
     <span data-ttu-id="787e9-203">如果“使用远程排序规则”为 True，并且数据源不是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据源，则指定远程数据源使用的排序规则名称。</span><span class="sxs-lookup"><span data-stu-id="787e9-203">Specifies the name of the collation used by the remote data source if use remote collation is true and the data source is not a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source.</span></span> <span data-ttu-id="787e9-204">此名称必须是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]支持的排序规则之一。</span><span class="sxs-lookup"><span data-stu-id="787e9-204">The name must be one of the collations supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="787e9-205">如果访问的是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以外的 OLE DB 数据源，但该数据源的排序规则与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的某个排序规则匹配，则使用该选项。</span><span class="sxs-lookup"><span data-stu-id="787e9-205">Use this option when accessing an OLE DB data source other than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but whose collation matches one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collations.</span></span>  
  
     <span data-ttu-id="787e9-206">链接服务器必须支持该服务器中所有列使用的单个排序规则。</span><span class="sxs-lookup"><span data-stu-id="787e9-206">The linked server must support a single collation to be used for all columns in that server.</span></span> <span data-ttu-id="787e9-207">如果链接服务器支持单个数据源内的多个排序规则，或者如果无法确定链接服务器的排序规则是否与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的某个排序规则匹配，则不要设置该选项。</span><span class="sxs-lookup"><span data-stu-id="787e9-207">Do not set this option if the linked server supports multiple collations within a single data source, or if the linked server's collation cannot be determined to match one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collations.</span></span>  
  
     <span data-ttu-id="787e9-208">**连接超时**</span><span class="sxs-lookup"><span data-stu-id="787e9-208">**Connection Timeout**</span></span>  
     <span data-ttu-id="787e9-209">连接到链接服务器时的超时值（秒）。</span><span class="sxs-lookup"><span data-stu-id="787e9-209">Time-out value in seconds for connecting to a linked server.</span></span>  
  
     <span data-ttu-id="787e9-210">如果为 0，则使用 **sp_configure** 默认 [远程登录超时](../../database-engine/configure-windows/configure-the-remote-login-timeout-server-configuration-option.md) 选项值。</span><span class="sxs-lookup"><span data-stu-id="787e9-210">If 0, use the **sp_configure** default [remote login timeout](../../database-engine/configure-windows/configure-the-remote-login-timeout-server-configuration-option.md) option value.</span></span>  
  
     <span data-ttu-id="787e9-211">**查询超时**</span><span class="sxs-lookup"><span data-stu-id="787e9-211">**Query Timeout**</span></span>  
     <span data-ttu-id="787e9-212">链接服务器上执行的查询的超时值（秒）。</span><span class="sxs-lookup"><span data-stu-id="787e9-212">Time-out value in seconds for queries against a linked server.</span></span>  
  
     <span data-ttu-id="787e9-213">如果为 0，则使用 **sp_configure** 默认 [远程查询超时](../../database-engine/configure-windows/configure-the-remote-query-timeout-server-configuration-option.md) 选项值。</span><span class="sxs-lookup"><span data-stu-id="787e9-213">If 0, use the **sp_configure** default [remote query timeout](../../database-engine/configure-windows/configure-the-remote-query-timeout-server-configuration-option.md) option value.</span></span>  
  
     <span data-ttu-id="787e9-214">**启用分布式事务处理的升级**</span><span class="sxs-lookup"><span data-stu-id="787e9-214">**Enable Promotion of Distributed Transactions**</span></span>  
     <span data-ttu-id="787e9-215">使用该选项可通过 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 分布式事务处理协调器 (MS DTC) 事务保护服务器到服务器的操作过程。</span><span class="sxs-lookup"><span data-stu-id="787e9-215">Use this option to protect the actions of a server-to-server procedure through a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) transaction.</span></span> <span data-ttu-id="787e9-216">如果该选项是 TRUE，则调用远程存储过程将启动分布式事务，并用 MS DTC 登记该事务。</span><span class="sxs-lookup"><span data-stu-id="787e9-216">When this option is TRUE, calling a remote stored procedure starts a distributed transaction and enlists the transaction with MS DTC.</span></span> <span data-ttu-id="787e9-217">有关详细信息，请参阅 [sp_serveroption (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)的数据。</span><span class="sxs-lookup"><span data-stu-id="787e9-217">For more information, see [sp_serveroption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql).</span></span>  
  
6.  <span data-ttu-id="787e9-218">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="787e9-218">Click **OK**.</span></span>  
  
##### <a name="to-view-the-provider-options"></a><span data-ttu-id="787e9-219">查看提供程序选项</span><span class="sxs-lookup"><span data-stu-id="787e9-219">To view the provider options</span></span>  
  
-   <span data-ttu-id="787e9-220">若要查看提供程序提供的选项，请单击 **“提供程序选项”** 页。</span><span class="sxs-lookup"><span data-stu-id="787e9-220">To view the options that the provider makes available, click the **Providers Options** page.</span></span>  
  
     <span data-ttu-id="787e9-221">每个访问接口的选项都各不相同。</span><span class="sxs-lookup"><span data-stu-id="787e9-221">All providers do not have the same options available.</span></span> <span data-ttu-id="787e9-222">例如，某些类型的数据提供索引，有些则没有提供。</span><span class="sxs-lookup"><span data-stu-id="787e9-222">For example, some types of data have indexes available and some might not.</span></span> <span data-ttu-id="787e9-223">使用此对话框可以帮助 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 理解访问接口的功能。</span><span class="sxs-lookup"><span data-stu-id="787e9-223">Use this dialog box to help [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] understand the capabilities of the provider.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="787e9-224">安装某些常用的数据访问接口，但在提供数据的产品发生更改时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装的访问接口可能不支持所有最新的功能。</span><span class="sxs-lookup"><span data-stu-id="787e9-224">installs some common data providers, however when the product providing the data changes, the provider installed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not support all the newest features.</span></span> <span data-ttu-id="787e9-225">提供数据的产品功能的有关信息的最佳来源是针对该产品的文档。</span><span class="sxs-lookup"><span data-stu-id="787e9-225">The best source of information about the capabilities of the product providing the data is the documentation for that product.</span></span>  
  
     <span data-ttu-id="787e9-226">**动态参数**</span><span class="sxs-lookup"><span data-stu-id="787e9-226">**Dynamic parameter**</span></span>  
     <span data-ttu-id="787e9-227">表明访问接口允许对参数化查询使用“?”参数标记语法。</span><span class="sxs-lookup"><span data-stu-id="787e9-227">Indicates that the provider allows '?' parameter marker syntax for parameterized queries.</span></span> <span data-ttu-id="787e9-228">仅当该访问接口支持 **ICommandWithParameters** 接口并支持“?”作为参数标记时，才应设置此选项。</span><span class="sxs-lookup"><span data-stu-id="787e9-228">Set this option only if the provider supports the **ICommandWithParameters** interface and supports a '?' as the parameter marker.</span></span> <span data-ttu-id="787e9-229">如果设置了此选项，则允许 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 针对该访问接口执行参数化查询。</span><span class="sxs-lookup"><span data-stu-id="787e9-229">Setting this option allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute parameterized queries against the provider.</span></span> <span data-ttu-id="787e9-230">这种对访问接口执行参数化查询的能力会提高某些查询的性能。</span><span class="sxs-lookup"><span data-stu-id="787e9-230">The ability to execute parameterized queries against the provider can result in better performance for certain queries.</span></span>  
  
     <span data-ttu-id="787e9-231">**嵌套查询**</span><span class="sxs-lookup"><span data-stu-id="787e9-231">**Nested queries**</span></span>  
     <span data-ttu-id="787e9-232">指示访问接口允许在 FROM 子句中使用嵌套的  `SELECT` 语句。</span><span class="sxs-lookup"><span data-stu-id="787e9-232">Indicates that the provider allows nested  `SELECT` statements in the FROM clause.</span></span> <span data-ttu-id="787e9-233">如果设置了此选项，则允许 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将某些查询委托给需要在 FROM 子句中嵌套 SELECT 语句的访问接口。</span><span class="sxs-lookup"><span data-stu-id="787e9-233">Setting this option allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to delegate certain queries to the provider that require nesting SELECT statements in the FROM clause.</span></span>  
  
     <span data-ttu-id="787e9-234">**仅零级**</span><span class="sxs-lookup"><span data-stu-id="787e9-234">**Level zero only**</span></span>  
     <span data-ttu-id="787e9-235">只对访问接口调用 0 级的 OLE DB 接口。</span><span class="sxs-lookup"><span data-stu-id="787e9-235">Only level 0 OLE DB interfaces are invoked against the provider.</span></span>  
  
     <span data-ttu-id="787e9-236">**允许进程内**</span><span class="sxs-lookup"><span data-stu-id="787e9-236">**Allow inprocess**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="787e9-237">允许将访问接口实例化为进程内服务器。</span><span class="sxs-lookup"><span data-stu-id="787e9-237">allows the provider to be instantiated as an in-process server.</span></span> <span data-ttu-id="787e9-238">如果未设置此选项，则默认行为是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程外实例化访问接口。</span><span class="sxs-lookup"><span data-stu-id="787e9-238">When this option is not set, the default behavior is to instantiate the provider outside the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="787e9-239">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程外实例化访问接口，可防止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程在访问接口中出错。</span><span class="sxs-lookup"><span data-stu-id="787e9-239">Instantiating the provider outside the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process protects the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process from errors in the provider.</span></span> <span data-ttu-id="787e9-240">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程外实例化访问接口时，不允许更新或插入长的引用列（`text`、`ntext` 或 `image`）。</span><span class="sxs-lookup"><span data-stu-id="787e9-240">When the provider is instantiated outside the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process, updates or inserts referencing long columns (`text`, `ntext`, or `image`) are not allowed.</span></span>  
  
     <span data-ttu-id="787e9-241">**非事务更新**</span><span class="sxs-lookup"><span data-stu-id="787e9-241">**Non transacted updates**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="787e9-242">允许更新，即使 **ITransactionLocal** 不可用时也是如此。</span><span class="sxs-lookup"><span data-stu-id="787e9-242">allows updates, even if **ITransactionLocal** is not available.</span></span> <span data-ttu-id="787e9-243">如果启用此选项，对访问接口的更新将不可恢复，因为该访问接口不支持事务。</span><span class="sxs-lookup"><span data-stu-id="787e9-243">If this option is enabled, updates against the provider are not recoverable, because the provider does not support transactions.</span></span>  
  
     <span data-ttu-id="787e9-244">**作为访问路径的索引**</span><span class="sxs-lookup"><span data-stu-id="787e9-244">**Index as access path**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="787e9-245">尝试使用访问接口的索引来提取数据。</span><span class="sxs-lookup"><span data-stu-id="787e9-245">attempts to use indexes of the provider to fetch data.</span></span> <span data-ttu-id="787e9-246">默认情况下，索引只能用于元数据而且从不打开。</span><span class="sxs-lookup"><span data-stu-id="787e9-246">By default, indexes are used only for metadata and are never opened</span></span>  
  
     <span data-ttu-id="787e9-247">**禁止即席访问**</span><span class="sxs-lookup"><span data-stu-id="787e9-247">**Disallow ad hoc access**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="787e9-248">不允许通过 OPENROWSET 和 OPENDATASOURCE 函数对 OLE DB 访问接口进行即席访问。</span><span class="sxs-lookup"><span data-stu-id="787e9-248">does not allow ad hoc access through the OPENROWSET and OPENDATASOURCE functions against the OLE DB provider.</span></span> <span data-ttu-id="787e9-249">如果未设置此选项，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 同样不允许进行即席访问。</span><span class="sxs-lookup"><span data-stu-id="787e9-249">When this option is not set, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] also does not allow ad hoc access.</span></span>  
  
     <span data-ttu-id="787e9-250">**支持 "Like" 运算符**</span><span class="sxs-lookup"><span data-stu-id="787e9-250">**Supports 'Like' operator**</span></span>  
     <span data-ttu-id="787e9-251">指示访问接口支持使用 LIKE 关键字的查询。</span><span class="sxs-lookup"><span data-stu-id="787e9-251">Indicates that the provider supports queries using the LIKE key word.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="787e9-252">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="787e9-252">Using Transact-SQL</span></span>  
 <span data-ttu-id="787e9-253">若要通过使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 创建链接服务器，请使用 [sp_addlinkedserver (Transact SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)[CREATE LOGIN (Transact SQL)](/sql/t-sql/statements/create-login-transact-sql) 和 [sp_addlinkedsrvlogin (Transact SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="787e9-253">To create a linked server by using [!INCLUDE[tsql](../../includes/tsql-md.md)], use the [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) and [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql) statements.</span></span>  
  
##### <a name="to-create-a-linked-server-to-another-instance-of-sql-server-using-transact-sql"></a><span data-ttu-id="787e9-254">使用 Transact-SQL 创建与其他 SQL Server 实例的链接服务器</span><span class="sxs-lookup"><span data-stu-id="787e9-254">To create a linked server to another instance of SQL Server using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="787e9-255">在查询编辑器中，输入以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令以便链接到名为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 `SRVR002\ACCTG`实例：</span><span class="sxs-lookup"><span data-stu-id="787e9-255">In Query Editor, enter the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command to link to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] named `SRVR002\ACCTG`:</span></span>  
  
    ```sql  
    USE [master]  
    GO  
    EXEC master.dbo.sp_addlinkedserver   
        @server = N'SRVR002\ACCTG',   
        @srvproduct=N'SQL Server' ;  
    GO  
  
    ```  
  
2.  <span data-ttu-id="787e9-256">执行以下代码，以便将链接服务器配置为使用正在使用链接服务器的登录名的域凭据。</span><span class="sxs-lookup"><span data-stu-id="787e9-256">Execute the following code to configure the linked server to use the domain credentials of the login that is using the linked server.</span></span>  
  
    ```sql  
    EXEC master.dbo.sp_addlinkedsrvlogin   
        @rmtsrvname = N'SRVR002\ACCTG',   
        @locallogin = NULL ,   
        @useself = N'True' ;  
    GO  
  
    ```  
  
##  <a name="follow-up-steps-to-take-after-you-create-a-linked-server"></a><a name="FollowUp"></a><span data-ttu-id="787e9-257">跟进：在创建链接服务器后要执行的步骤</span><span class="sxs-lookup"><span data-stu-id="787e9-257">Follow Up: Steps to take after you create a linked server</span></span>  
  
#### <a name="to-test-the-linked-server"></a><span data-ttu-id="787e9-258">测试链接服务器</span><span class="sxs-lookup"><span data-stu-id="787e9-258">To test the linked server</span></span>  
  
-   <span data-ttu-id="787e9-259">执行下面的代码，测试与链接服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="787e9-259">Execute the following code to test the connection to the linked server.</span></span> <span data-ttu-id="787e9-260">以下示例返回链接服务器上数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="787e9-260">This example the returns the names of the databases on the linked server.</span></span>  
  
    ```sql  
    SELECT name FROM [SRVR002\ACCTG].master.sys.databases ;  
    GO  
  
    ```  
  
#### <a name="writing-a-query-that-joins-tables-from-a-linked-server"></a><span data-ttu-id="787e9-261">编写联接来自某一链接服务器的多个表的查询</span><span class="sxs-lookup"><span data-stu-id="787e9-261">Writing a query that joins tables from a linked server</span></span>  
  
-   <span data-ttu-id="787e9-262">使用由四部分组成的名称引用链接服务器上的对象。</span><span class="sxs-lookup"><span data-stu-id="787e9-262">Use four-part names to refer to an object on a linked server.</span></span> <span data-ttu-id="787e9-263">执行以下代码，以便返回本地服务器上所有登录名的列表及其在链接服务器上的匹配登录名。</span><span class="sxs-lookup"><span data-stu-id="787e9-263">Execute the following code to return a list of all logins on the local server and their matching logins on the linked server.</span></span>  
  
    ```sql  
    SELECT local.name AS LocalLogins, linked.name AS LinkedLogins  
    FROM master.sys.server_principals AS local  
    LEFT JOIN [SRVR002\ACCTG].master.sys.server_principals AS linked  
        ON local.name = linked.name ;  
    GO  
    ```  
  
     <span data-ttu-id="787e9-264">如果为链接服务器登录名返回了 NULL，则意味着该登录名在链接服务器上不存在。</span><span class="sxs-lookup"><span data-stu-id="787e9-264">When NULL is returned for the linked server login it indicates that the login does not exist on the linked server.</span></span> <span data-ttu-id="787e9-265">这些登录名将无法使用链接服务器，除非链接服务器配置为传递不同的安全上下文或者链接服务器接受匿名连接。</span><span class="sxs-lookup"><span data-stu-id="787e9-265">These logins will not be able to use the linked server unless the linked server is configured to pass a different security context or the linked server accepts anonymous connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="787e9-266">另请参阅</span><span class="sxs-lookup"><span data-stu-id="787e9-266">See Also</span></span>  
 <span data-ttu-id="787e9-267">[链接服务器（数据库引擎）](linked-servers-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="787e9-267">[Linked Servers &#40;Database Engine&#41;](linked-servers-database-engine.md) </span></span>  
 <span data-ttu-id="787e9-268">[sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="787e9-268">[sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) </span></span>  
 [<span data-ttu-id="787e9-269">sp_serveroption (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="787e9-269">sp_serveroption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)  
  
  
