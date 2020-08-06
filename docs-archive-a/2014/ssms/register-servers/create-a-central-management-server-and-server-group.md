---
title: 创建中央管理服务器和组
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- configuration server
ms.assetid: da265482-3953-440a-ac23-0ab7e42a55eb
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f53b75966a14dbc6fd6cdc9bea0929ccac7780c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682634"
---
# <a name="create-a-central-management-server-and-server-group-sql-server-management-studio"></a><span data-ttu-id="de09a-102">创建中央管理服务器和服务器组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="de09a-102">Create a Central Management Server and Server Group (SQL Server Management Studio)</span></span>
  <span data-ttu-id="de09a-103">本主题说明如何在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 指定一个 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]实例作为中央管理服务器。</span><span class="sxs-lookup"><span data-stu-id="de09a-103">This topic describes how to designate an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a central management server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="de09a-104">中央管理服务器存储组织到一个或多个中央管理服务器组中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例列表。</span><span class="sxs-lookup"><span data-stu-id="de09a-104">Central management servers store a list of instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is organized into one or more central management server groups.</span></span> <span data-ttu-id="de09a-105">使用中央管理服务器组执行的操作将作用于服务器组中的所有服务器。</span><span class="sxs-lookup"><span data-stu-id="de09a-105">Actions that are taken by using a central management server group act on all servers in the server group.</span></span> <span data-ttu-id="de09a-106">这包括使用对象资源管理器连接到服务器以及在多个服务器上同时执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句和基于策略的管理策略。</span><span class="sxs-lookup"><span data-stu-id="de09a-106">This includes connecting to servers by using Object Explorer and executing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and Policy-Based Management policies on multiple servers at the same time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de09a-107">不能将早于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 指定为中央管理服务器。</span><span class="sxs-lookup"><span data-stu-id="de09a-107">Versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] cannot be designated as a central management server.</span></span>  
  
 <span data-ttu-id="de09a-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="de09a-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="de09a-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="de09a-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="de09a-110">安全性</span><span class="sxs-lookup"><span data-stu-id="de09a-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="de09a-111">**若要创建中央管理服务器和服务器组，请使用：**</span><span class="sxs-lookup"><span data-stu-id="de09a-111">**To create a Central Management Server and Server Group, using:**</span></span>  
  
     [<span data-ttu-id="de09a-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="de09a-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="de09a-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="de09a-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="de09a-114">Security</span><span class="sxs-lookup"><span data-stu-id="de09a-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="de09a-115">权限</span><span class="sxs-lookup"><span data-stu-id="de09a-115">Permissions</span></span>  
 <span data-ttu-id="de09a-116">msdb 数据库中有两个数据库角色可授予对中央管理服务器的访问权限。</span><span class="sxs-lookup"><span data-stu-id="de09a-116">Two database roles in the msdb database grant access to central management servers.</span></span> <span data-ttu-id="de09a-117">只有 ServerGroupAdministratorRole 角色的成员能够管理中央管理服务器。</span><span class="sxs-lookup"><span data-stu-id="de09a-117">Only members of the ServerGroupAdministratorRole role can manage the central management server.</span></span> <span data-ttu-id="de09a-118">若要连接到中央管理服务器，需要具有 ServerGroupReaderRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="de09a-118">Membership in the ServerGroupReaderRole role is required to connect to a central management server.</span></span>  
  
 <span data-ttu-id="de09a-119">由于中央管理服务器维护的连接是在用户的上下文中使用 Windows 身份验证执行的，因此对注册的服务器的有效权限可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="de09a-119">Because the connections that are maintained by a central management server execute in the context of the user, by using Windows Authentication, the effective permissions on the registered servers might vary.</span></span> <span data-ttu-id="de09a-120">例如，用户可能是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A 实例上 sysadmin 固定服务器角色的成员，但仅具有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B 实例的有限权限。</span><span class="sxs-lookup"><span data-stu-id="de09a-120">For example, the user might be a member of the sysadmin fixed server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A, but have limited permissions on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="de09a-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="de09a-121">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="de09a-122">下面的过程说明如何执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="de09a-122">The following procedures describe how to perform the following steps.</span></span>  
  
1.  <span data-ttu-id="de09a-123">创建中央管理服务器。</span><span class="sxs-lookup"><span data-stu-id="de09a-123">Create a central management server.</span></span>  
  
2.  <span data-ttu-id="de09a-124">向中央管理服务器添加一个或多个服务器组，和向服务器组添加一个或多个已注册的服务器。</span><span class="sxs-lookup"><span data-stu-id="de09a-124">Add one or more server groups to the central management server and add one or more registered servers to the server groups.</span></span>  
  
#### <a name="create-a-central-management-server"></a><span data-ttu-id="de09a-125">创建中央管理服务器</span><span class="sxs-lookup"><span data-stu-id="de09a-125">Create a central management server</span></span>  
  
1.  <span data-ttu-id="de09a-126">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的 **“视图”** 菜单上，单击 **“已注册的服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="de09a-126">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="de09a-127">在“已注册的服务器”中，展开“数据库引擎”  ，右键单击“中央管理服务器”  ，然后单击“注册中央管理服务器”  。</span><span class="sxs-lookup"><span data-stu-id="de09a-127">In Registered Servers, expand **Database Engine**, right-click **Central Management Servers**, and then  click **Register Central Management Server**.</span></span>  
  
3.  <span data-ttu-id="de09a-128">在“新建服务器注册”  对话框中，从服务器下拉列表中选择要作为中央管理服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="de09a-128">In the **New Server Registration** dialog box, select the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to become the central management server from the drop-down list of servers.</span></span> <span data-ttu-id="de09a-129">必须为此中央管理服务器使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="de09a-129">You must use Windows Authentication for the central management server.</span></span>  
  
4.  <span data-ttu-id="de09a-130">在 **“已注册的服务器”** 中，输入服务器名称和可选说明。</span><span class="sxs-lookup"><span data-stu-id="de09a-130">In **Registered Server**, enter a server name and optional description.</span></span>  
  
5.  <span data-ttu-id="de09a-131">在 **“连接属性”** 选项卡上，查看或修改网络和连接属性。</span><span class="sxs-lookup"><span data-stu-id="de09a-131">From the **Connection Properties** tab, review or modifiy the network  and connection properties.</span></span> <span data-ttu-id="de09a-132">有关详细信息，请参阅[连接到服务器（“连接属性”页）数据库引擎](../f1-help/connect-to-server-connection-properties-page-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="de09a-132">For more information, see [Connect to Server &#40;Connection Properties Page&#41; Database Engine](../f1-help/connect-to-server-connection-properties-page-database-engine.md)</span></span>  
  
6.  <span data-ttu-id="de09a-133">单击 **“测试”** ，对连接进行测试。</span><span class="sxs-lookup"><span data-stu-id="de09a-133">Click **Test**, to test the connection.</span></span>  
  
7.  <span data-ttu-id="de09a-134">单击“保存”  。</span><span class="sxs-lookup"><span data-stu-id="de09a-134">Click **Save**.</span></span> <span data-ttu-id="de09a-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例将出现在 **“中央管理服务器”** 文件夹下。</span><span class="sxs-lookup"><span data-stu-id="de09a-135">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will appear under the **Central Management Servers** folder.</span></span>  
  
#### <a name="create-a-new-server-group-and-add-servers-to-the-group"></a><span data-ttu-id="de09a-136">创建新服务器组并向该组添加服务器</span><span class="sxs-lookup"><span data-stu-id="de09a-136">Create a new server group and add servers to the group</span></span>  
  
1.  <span data-ttu-id="de09a-137">在 **“已注册的服务器”** 中，展开 **“中央管理服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="de09a-137">From **Registered Servers**, expand **Central Management Servers**.</span></span> <span data-ttu-id="de09a-138">右键单击在上述步骤中添加的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，然后选择“新建服务器组”  。</span><span class="sxs-lookup"><span data-stu-id="de09a-138">Right-click the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] added in the procedure above and select **New Server Group**.</span></span>  
  
2.  <span data-ttu-id="de09a-139">在 **“新建服务器组属性”** 中，输入组名和可选说明。</span><span class="sxs-lookup"><span data-stu-id="de09a-139">In **New Server Group Properties**, enter a group name and optional description.</span></span>  
  
3.  <span data-ttu-id="de09a-140">在“已注册的服务器”  中，右键单击服务器组，然后单击“新建服务器注册”  。</span><span class="sxs-lookup"><span data-stu-id="de09a-140">From **Registered Servers**, right-click the server group and click **New Server Registration**.</span></span>  
  
4.  <span data-ttu-id="de09a-141">在新服务器注册中，选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="de09a-141">From New Server Registration, select an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="de09a-142">有关详细信息，请参阅[创建新的已注册的服务器 (SQL Server Management Studio)](create-a-new-registered-server-sql-server-management-studio.md).</span><span class="sxs-lookup"><span data-stu-id="de09a-142">For more information, see [Create a New Registered Server &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md).</span></span> <span data-ttu-id="de09a-143">根据需要添加更多服务器。</span><span class="sxs-lookup"><span data-stu-id="de09a-143">Add more servers as appropriate.</span></span>  
  
#### <a name="to-execute-queries-against-several-configuration-targets-at-the-same-time"></a><span data-ttu-id="de09a-144">同时对多个配置目标执行查询</span><span class="sxs-lookup"><span data-stu-id="de09a-144">To execute queries against several configuration targets at the same time</span></span>  
  
-   <span data-ttu-id="de09a-145">在创建中央管理服务器、一个或多个服务器组以及一个或多个已注册的服务器后，您可以同时对整个组执行查询。</span><span class="sxs-lookup"><span data-stu-id="de09a-145">After you create a central management server, one or more server groups, and one or more registered servers, you can execute queries against a whole group at the same time.</span></span> <span data-ttu-id="de09a-146">有关如何同时对服务器组中的服务器执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的详细信息，请参阅[同时对多个服务器执行语句 (SQL Server Management Studio)](execute-statements-against-multiple-servers-simultaneously.md)。</span><span class="sxs-lookup"><span data-stu-id="de09a-146">For more information about how to execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements on the servers in a server group at the same time, see [Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de09a-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de09a-147">See Also</span></span>  
 [<span data-ttu-id="de09a-148">使用中央管理服务器管理多台服务器</span><span class="sxs-lookup"><span data-stu-id="de09a-148">Administer Multiple Servers Using Central Management Servers</span></span>](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
