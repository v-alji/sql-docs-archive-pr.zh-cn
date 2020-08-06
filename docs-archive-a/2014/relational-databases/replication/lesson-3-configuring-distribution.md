---
title: 第 3 课：配置分发 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f248984a-0b59-4c2f-a56d-31f8dafe72b5
author: rothja
ms.author: jroth
ms.openlocfilehash: 52b284b6186e599b7afe73bd37ab0a8348ec38da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692846"
---
# <a name="lesson-3-configuring-distribution"></a><span data-ttu-id="def13-102">第 3 课：配置分发</span><span class="sxs-lookup"><span data-stu-id="def13-102">Lesson 3: Configuring Distribution</span></span>
  <span data-ttu-id="def13-103">在本课中，将在发布服务器中配置分发，并设置所需的发布数据库和分发数据库权限。</span><span class="sxs-lookup"><span data-stu-id="def13-103">In this lesson, you will configure distribution at the Publisher and set the required permissions on the publication and distribution databases.</span></span> <span data-ttu-id="def13-104">如果已经配置了分发服务器，则必须在开始本课之前先禁用发布和分发。</span><span class="sxs-lookup"><span data-stu-id="def13-104">If you have already configured the Distributor, you must first disable publishing and distribution before you begin this lesson.</span></span> <span data-ttu-id="def13-105">如果必须保留现有复制拓扑，请不要执行该操作。</span><span class="sxs-lookup"><span data-stu-id="def13-105">Do not do this if you must retain an existing replication topology.</span></span>  
  
 <span data-ttu-id="def13-106">使用远程分发服务器配置发布服务器不属于本教程讨论的范畴。</span><span class="sxs-lookup"><span data-stu-id="def13-106">Configuring a Publisher with a remote Distributor is outside the scope of this tutorial.</span></span>  
  
### <a name="configuring-distribution-at-the-publisher"></a><span data-ttu-id="def13-107">在发布服务器中配置分发</span><span class="sxs-lookup"><span data-stu-id="def13-107">Configuring distribution at the Publisher</span></span>  
  
1.  <span data-ttu-id="def13-108">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="def13-108">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="def13-109">右键单击“复制”\*\*\*\* 文件夹，然后单击“配置分发”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="def13-109">Right-click the **Replication** folder and click **Configure Distribution**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="def13-110">如果连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的是 **localhost** ，而不是实际服务器名称，则系统会向你显示一个警告提示，指出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 无法连接到服务器 **'localhost'**。</span><span class="sxs-lookup"><span data-stu-id="def13-110">If you have connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using **localhost** rather than the actual server name you will be prompted with a warning that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is unable to connect to server **'localhost'**.</span></span> <span data-ttu-id="def13-111">在警告对话框中单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="def13-111">Click **OK** on the warning dialog.</span></span> <span data-ttu-id="def13-112">在“连接到服务器”\*\*\*\* 对话框中，将“服务器名称”\*\*\*\* 从 **localhost** 更改为你的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="def13-112">In the **Connect to Server** dialog change the **Server name** from **localhost** to the name of your server.</span></span> <span data-ttu-id="def13-113">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="def13-113">Click **Connect**.</span></span>  
  
     <span data-ttu-id="def13-114">此时分发配置向导启动。</span><span class="sxs-lookup"><span data-stu-id="def13-114">The Distribution Configuration Wizard launches.</span></span>  
  
3.  <span data-ttu-id="def13-115">在 "**分发服务器**" 页上，选择 **"** _\<ServerName>_ **" 将充当自己的分发服务器;SQL Server 将创建分发数据库和日志**，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="def13-115">On the **Distributor** page, select **'**_\<ServerName>_**' will act as its own Distributor; SQL Server will create a distribution database and log**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="def13-116">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 未运行，则在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]“代理启动”\*\*\*\* 页上，选择“是”\*\*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，将 \*\* 代理服务配置为自动启动。</span><span class="sxs-lookup"><span data-stu-id="def13-116">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not running, on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**Agent Start** page, select **Yes**, configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to start automatically.</span></span> <span data-ttu-id="def13-117">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="def13-117">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="def13-118">**\\\\** \<_Machine_Name> 在 "**快照文件夹**" 文本框中输入 _**\repldata (** ，其中 \<*Machine_Name> \* 是发布服务器的名称，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="def13-118">Enter **\\\\**\<_Machine_Name>_**\repldata** in the **Snapshot folder** text box, where \<*Machine_Name>\* is the name of the Publisher, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="def13-119">接受向导剩余页上的默认值。</span><span class="sxs-lookup"><span data-stu-id="def13-119">Accept the default values on the remaining pages of the wizard.</span></span>  
  
7.  <span data-ttu-id="def13-120">单击“完成”\*\*\*\* 以启用分发。</span><span class="sxs-lookup"><span data-stu-id="def13-120">Click **Finish** to enable distribution.</span></span>  
  
### <a name="setting-database-permissions-at-the-publisher"></a><span data-ttu-id="def13-121">在发布服务器中设置数据库权限</span><span class="sxs-lookup"><span data-stu-id="def13-121">Setting database permissions at the Publisher</span></span>  
  
1.  <span data-ttu-id="def13-122">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，展开 "**安全性**"，右键单击 "**登录名**"，然后选择 "**新建登录名**"。</span><span class="sxs-lookup"><span data-stu-id="def13-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand **Security**, right-click **Logins**, and then select **New Login**.</span></span>  
  
2.  <span data-ttu-id="def13-123">在 "**常规**" 页上，单击 "**搜索**"， \<_Machine_Name> 在 "**输入要选择的对象名称**" 框中输入 _**\ repl_snapshot** ，其中 \<*Machine_Name> \* 是本地发布服务器的名称，单击 "**检查名称**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="def13-123">On the **General** page, click **Search**, enter \<_Machine_Name>_**\repl_snapshot** in the **Enter the object name to select** box, where \<*Machine_Name>\* is the name of the local Publisher server, click **Check Names**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="def13-124">在 "**用户映射**" 页上，在 "**映射到此登录名的用户**" 列表中，选择 "**分发**" 和 " [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库"。</span><span class="sxs-lookup"><span data-stu-id="def13-124">On the **User Mapping** page, in the **Users mapped to this login** list select both the **distribution** and [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] databases.</span></span>  
  
     <span data-ttu-id="def13-125">在 "**数据库角色成员身份**" 列表中，为 `db_owner` 这两个数据库的登录名选择角色。</span><span class="sxs-lookup"><span data-stu-id="def13-125">In the **Database role membership** list select the `db_owner` role for the login for both databases.</span></span>  
  
4.  <span data-ttu-id="def13-126">单击“确定”\*\*\*\* 创建登录名。</span><span class="sxs-lookup"><span data-stu-id="def13-126">Click **OK** to create the login.</span></span>  
  
5.  <span data-ttu-id="def13-127">重复步骤 1 至 4，为本地 repl_logreader 帐户创建登录名。</span><span class="sxs-lookup"><span data-stu-id="def13-127">Repeat steps 1-4 to create a login for the local repl_logreader account.</span></span> <span data-ttu-id="def13-128">此登录名也必须映射到作为 `db_owner` **分发**和**AdventureWorks**数据库中固定数据库角色的成员的用户。</span><span class="sxs-lookup"><span data-stu-id="def13-128">This login must also be mapped to users that are members of the `db_owner` fixed database role in the **distribution** and **AdventureWorks** databases.</span></span>  
  
6.  <span data-ttu-id="def13-129">重复步骤 1 至 4，为本地 repl_distribution 帐户创建登录名。</span><span class="sxs-lookup"><span data-stu-id="def13-129">Repeat steps 1-4 to create a login for the local repl_distribution account.</span></span> <span data-ttu-id="def13-130">此登录名必须映射到属于 `db_owner` **分发**数据库中固定数据库角色的成员的用户。</span><span class="sxs-lookup"><span data-stu-id="def13-130">This login must be mapped to a user that is a member of the `db_owner` fixed database role in the **distribution** database.</span></span>  
  
7.  <span data-ttu-id="def13-131">重复步骤 1 至 4，为本地 repl_merge 帐户创建登录名。</span><span class="sxs-lookup"><span data-stu-id="def13-131">Repeat steps 1-4 to create a login for the local repl_merge account.</span></span> <span data-ttu-id="def13-132">此登录名必须在 **distribution** 数据库和 **AdventureWorks** 数据库中拥有用户映射。</span><span class="sxs-lookup"><span data-stu-id="def13-132">This login must have user mappings in the **distribution** and **AdventureWorks** databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="def13-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="def13-133">See Also</span></span>  
 <span data-ttu-id="def13-134">[“配置分发”](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="def13-134">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="def13-135">复制代理安全模式</span><span class="sxs-lookup"><span data-stu-id="def13-135">Replication Agent Security Model</span></span>](security/replication-agent-security-model.md)  
  
  
