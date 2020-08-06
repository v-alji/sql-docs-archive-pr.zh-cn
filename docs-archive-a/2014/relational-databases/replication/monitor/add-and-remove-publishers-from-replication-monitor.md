---
title: 从复制监视器中添加和删除发布服务器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, adding and removing Publishers
ms.assetid: fa36c4b4-bfa5-494e-92e3-07a02d7332c3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 16c2876b55541e347e4e638132f36ad33932abb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693758"
---
# <a name="add-and-remove-publishers-from-replication-monitor"></a><span data-ttu-id="7ec1f-102">从复制监视器中添加和删除发布服务器</span><span class="sxs-lookup"><span data-stu-id="7ec1f-102">Add and Remove Publishers from Replication Monitor</span></span>
  <span data-ttu-id="7ec1f-103">如果从中启动复制监视器的服务器是发布服务器，则会自动将其添加到监视器中。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-103">The server from which you launch Replication Monitor is automatically added to the monitor if it is a Publisher.</span></span> <span data-ttu-id="7ec1f-104">其他发布服务器可以通过 **“添加发布服务器”** 对话框来添加。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-104">Additional Publishers can be added through the **Add Publisher** dialog box.</span></span> <span data-ttu-id="7ec1f-105">添加发布服务器后，该服务器便会显示在监视器左窗格中的某个组中。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-105">After adding a Publisher, it is displayed in a group in the left pane of the monitor.</span></span> <span data-ttu-id="7ec1f-106">默认情况下，包括 **“我的发布服务器”** 组，但还可以创建新组来管理一个或多个复制拓扑。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-106">The **My Publishers** group is included by default, but you can create new groups to manage one or more replication topologies.</span></span> <span data-ttu-id="7ec1f-107">有关启动复制监视器的信息，请参阅[启动复制监视器](start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-107">For information about starting Replication Monitor, see [Start the Replication Monitor](start-the-replication-monitor.md).</span></span>  
  
### <a name="to-add-a-sql-server-publisher"></a><span data-ttu-id="7ec1f-108">添加 SQL Server 发布服务器</span><span class="sxs-lookup"><span data-stu-id="7ec1f-108">To add a SQL Server Publisher</span></span>  
  
1.  <span data-ttu-id="7ec1f-109">在左窗格中右键单击 **“复制监视器”** 节点或发布服务器组节点，再单击 **“添加发布服务器”**。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-109">Right-click the **Replication Monitor** node or a Publisher group node in the left pane, and then click **Add Publisher**.</span></span>  
  
2.  <span data-ttu-id="7ec1f-110">在 **“添加发布服务器”** 对话框中单击 **“添加”**，再单击 **“添加 SQL Server 发布服务器”**。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-110">In the **Add Publisher** dialog box, click **Add**, and then click **Add SQL Server Publisher**.</span></span>  
  
3.  <span data-ttu-id="7ec1f-111">在 **“连接到服务器”** 对话框中输入该发布服务器的名称，然后选择身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-111">In the **Connect to Server** dialog box, enter the name of the Publisher, and then select the authentication type.</span></span> <span data-ttu-id="7ec1f-112">如果选择 **“SQL Server 身份验证”**，请输入登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-112">If you select **SQL Server Authentication**, enter a login and password.</span></span> <span data-ttu-id="7ec1f-113">您所指定的凭据由复制监视器进行保存，以便将来连接到此服务器时使用。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-113">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="7ec1f-114">指定的 Windows 帐户或 SQL Server 登录名必须为 **sysadmin** 固定服务器角色的成员或分发数据库中 **replmonitor** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-114">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
4.  <span data-ttu-id="7ec1f-115">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-115">Click **Connect**.</span></span> <span data-ttu-id="7ec1f-116">如果发布服务器使用远程分发服务器，系统将在 **“连接到服务器”** 对话框中提示您连接到分发服务器。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-116">If the Publisher uses a remote Distributor, you will be prompted to connect to the Distributor in the **Connect to Server** dialog box.</span></span> <span data-ttu-id="7ec1f-117">您所指定的凭据由复制监视器进行保存，以便将来连接到此服务器时使用。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-117">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="7ec1f-118">指定的 Windows 帐户或 SQL Server 登录名必须为 **sysadmin** 固定服务器角色的成员或分发数据库中 **replmonitor** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-118">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
5.  <span data-ttu-id="7ec1f-119">发布服务器和分发服务器的名称显示在 **“开始监视下列发布服务器”** 网格中。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-119">The name of the Publisher and Distributor are displayed in the **Start monitoring the following Publisher(s)** grid.</span></span>  
  
6.  <span data-ttu-id="7ec1f-120">若要为发布服务器指定刷新和连接选项，请在该网格中选择发布服务器，并根据需要修改选项。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-120">To specify refresh and connection options for the Publisher, select the Publisher in the grid, and modify options as necessary.</span></span> <span data-ttu-id="7ec1f-121">有关刷新选项的详细信息，请参阅 [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-121">For more information about refresh options, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
7.  <span data-ttu-id="7ec1f-122">选择复制监视器中放置发布服务器的组。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-122">Select the group under which the Publisher should be displayed in Replication Monitor.</span></span> <span data-ttu-id="7ec1f-123">若要创建新组，请单击 **“新建组”** 选项，然后输入组名称；在 **“在以下组中显示此发布服务器”** 列表中选择该组。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-123">To create a new group, click **New Group**, and then enter a group name; select the group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-add-an-oracle-publisher"></a><span data-ttu-id="7ec1f-124">添加 Oracle 发布服务器</span><span class="sxs-lookup"><span data-stu-id="7ec1f-124">To add an Oracle Publisher</span></span>  
  
1.  <span data-ttu-id="7ec1f-125">在左窗格中右键单击 **“复制监视器”** 节点或发布服务器组节点，再单击 **“添加发布服务器”**。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-125">Right-click the **Replication Monitor** node or a Publisher group node in the left pane, and then click **Add Publisher**.</span></span>  
  
2.  <span data-ttu-id="7ec1f-126">在 **“添加发布服务器”** 对话框中，单击 **“添加”**，然后单击 **“添加 Oracle 发布服务器”**。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-126">In the **Add Publisher** dialog box, click **Add**, and then click **Add Oracle Publisher**.</span></span>  
  
3.  <span data-ttu-id="7ec1f-127">在“连接到服务器”对话框中，输入与 Oracle 发布服务器关联的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器的名称，然后选择身份验证类型\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-127">In the **Connect to Server** dialog box, enter the name of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor associated with the Oracle Publisher, and then select the authentication type.</span></span> <span data-ttu-id="7ec1f-128">如果选择 **“SQL Server 身份验证”**，请输入登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-128">If you select **SQL Server Authentication**, enter a login and password.</span></span> <span data-ttu-id="7ec1f-129">您所指定的凭据由复制监视器进行保存，以便将来连接到此服务器时使用。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-129">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="7ec1f-130">指定的 Windows 帐户或 SQL Server 登录名必须为 **sysadmin** 固定服务器角色的成员或分发数据库中 **replmonitor** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-130">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
4.  <span data-ttu-id="7ec1f-131">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-131">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="7ec1f-132">发布服务器和分发服务器的名称显示在 **“开始监视下列发布服务器”** 网格中。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-132">The name of the Publisher and Distributor are displayed in the **Start monitoring the following Publisher(s)** grid.</span></span>  
  
6.  <span data-ttu-id="7ec1f-133">若要为发布服务器指定刷新和连接选项，请在该网格中选择发布服务器，并根据需要修改选项。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-133">To specify refresh and connection options for the Publisher, select the Publisher in the grid, and modify options as necessary.</span></span> <span data-ttu-id="7ec1f-134">有关刷新选项的详细信息，请参阅 [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-134">For more information about refresh options, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
7.  <span data-ttu-id="7ec1f-135">选择复制监视器中放置发布服务器的组。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-135">Select the group under which the Publisher should be displayed in Replication Monitor.</span></span> <span data-ttu-id="7ec1f-136">若要创建新组，请单击 **“新建组”** 选项，然后输入组名称；在 **“在以下组中显示此发布服务器”** 列表中选择该组。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-136">To create a new group, click **New Group**, and then enter a group name; select the group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-add-one-or-more-publishers-that-use-the-same-distributor"></a><span data-ttu-id="7ec1f-137">添加一个或多个使用相同分发服务器的发布服务器</span><span class="sxs-lookup"><span data-stu-id="7ec1f-137">To add one or more Publishers that use the same Distributor</span></span>  
  
1.  <span data-ttu-id="7ec1f-138">在左窗格中右键单击 **“复制监视器”** 节点或发布服务器组节点，再单击 **“添加发布服务器”**。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-138">Right-click the **Replication Monitor** node or a Publisher group node in the left pane, and then click **Add Publisher**.</span></span>  
  
2.  <span data-ttu-id="7ec1f-139">在 **“添加发布服务器”** 对话框中，单击 **“添加”**，然后单击 **“指定分发服务器并添加其发布服务器”**。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-139">In the **Add Publisher** dialog box, click **Add**, and then click **Specify a Distributor and Add Its Publishers**.</span></span>  
  
3.  <span data-ttu-id="7ec1f-140">在 **“连接到服务器”** 对话框中，输入该分发服务器的名称，然后选择身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-140">In the **Connect to Server** dialog box, enter the name of the Distributor, and then select the authentication type.</span></span> <span data-ttu-id="7ec1f-141">如果选择 **“SQL Server 身份验证”**，请输入登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-141">If you select **SQL Server Authentication**, enter a login and password.</span></span> <span data-ttu-id="7ec1f-142">您所指定的凭据由复制监视器进行保存，以便将来连接到此服务器时使用。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-142">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="7ec1f-143">指定的 Windows 帐户或 SQL Server 登录名必须为 **sysadmin** 固定服务器角色的成员或分发数据库中 **replmonitor** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-143">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
4.  <span data-ttu-id="7ec1f-144">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-144">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="7ec1f-145">分发服务器和每个发布服务器的名称显示在 **“开始监视下列发布服务器”** 网格中。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-145">The name of the Distributor and each Publisher are displayed in the **Start monitoring the following Publisher(s)** grid.</span></span> <span data-ttu-id="7ec1f-146">如果一个发布服务器已经添加到复制监视器中，则该网格中不显示其名称。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-146">If a Publisher has already been added to Replication Monitor, it does not appear in the grid.</span></span>  
  
6.  <span data-ttu-id="7ec1f-147">若要为发布服务器指定刷新和连接选项，请在该网格中选择发布服务器，并根据需要修改选项。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-147">To specify refresh and connection options for the Publisher, select the Publisher in the grid, and modify options as necessary.</span></span> <span data-ttu-id="7ec1f-148">有关刷新选项的详细信息，请参阅 [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-148">For more information about refresh options, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
7.  <span data-ttu-id="7ec1f-149">选择复制监视器中放置发布服务器的组。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-149">Select the group under which Publishers should be displayed in Replication Monitor.</span></span> <span data-ttu-id="7ec1f-150">若要创建新组，请单击 **“新建组”** 选项，然后输入组名称；在 **“在以下组中显示此发布服务器”** 列表中选择该组。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-150">To create a new group, click **New Group**, and then enter a group name; select the group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-modify-settings-for-the-publisher-and-publisher-groups"></a><span data-ttu-id="7ec1f-151">修改发布服务器和发布服务器组的设置</span><span class="sxs-lookup"><span data-stu-id="7ec1f-151">To modify settings for the Publisher and Publisher Groups</span></span>  
  
1.  <span data-ttu-id="7ec1f-152">在左窗格中右键单击发布服务器，再单击 **“发布服务器设置”**。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-152">Right-click a Publisher in the left pane, and then click **Publisher Settings**.</span></span>  
  
2.  <span data-ttu-id="7ec1f-153">在 **“发布服务器设置”** 对话框中进行任何更改：</span><span class="sxs-lookup"><span data-stu-id="7ec1f-153">Make any changes in the **Publisher Settings** dialog box:</span></span>  
  
    -   <span data-ttu-id="7ec1f-154">若要更改复制监视器用来连接到服务器的凭据，请单击 **“发布服务器连接”** 或 **“分发服务器连接”**，然后在 **“连接到服务器”** 对话框中输入凭据。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-154">To change the credentials that Replication Monitor uses to connect to a server, click **Publisher Connection** or **Distributor Connection**, and then enter credentials in the **Connect to Server** dialog box.</span></span>  
  
    -   <span data-ttu-id="7ec1f-155">若要将发布服务器从一个组移动到另一个组，请在 **“开始监视下列发布服务器”** 网格中选择发布服务器，然后在 **“在以下组中显示此发布服务器”** 列表中选择新组。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-155">To move a Publisher from one group to another, select the Publisher in the **Start monitoring the following Publisher(s)** grid, and then select the new group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-remove-a-publisher-from-replication-monitor"></a><span data-ttu-id="7ec1f-156">从复制监视器删除发布服务器</span><span class="sxs-lookup"><span data-stu-id="7ec1f-156">To remove a Publisher from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="7ec1f-157">右键单击左窗格中的某发布服务器。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-157">Right-click a Publisher in the left pane.</span></span>  
  
2.  <span data-ttu-id="7ec1f-158">单击“删除”。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-158">Click **Remove**.</span></span>  
  
### <a name="to-add-a-publisher-group-to-replication-monitor"></a><span data-ttu-id="7ec1f-159">向复制监视器添加发布服务器组</span><span class="sxs-lookup"><span data-stu-id="7ec1f-159">To add a Publisher group to Replication Monitor</span></span>  
  
1.  <span data-ttu-id="7ec1f-160">只有在添加发布服务器或修改发布服务器设置时才能创建发布服务器组。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-160">Publisher groups can be created only when adding a Publisher or modifying settings for a Publisher.</span></span> <span data-ttu-id="7ec1f-161">有关详细信息，请参阅有关添加发布服务器的操作过程。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-161">See the how to procedures on adding a Publisher for more information.</span></span>  
  
### <a name="to-remove-a-publisher-group-from-replication-monitor"></a><span data-ttu-id="7ec1f-162">从复制监视器删除发布服务器组</span><span class="sxs-lookup"><span data-stu-id="7ec1f-162">To remove a Publisher group from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="7ec1f-163">从复制监视器将所有发布服务器移动到其他组或删除它们。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-163">Move all Publishers to a different group or remove them from Replication Monitor.</span></span> <span data-ttu-id="7ec1f-164">有关详细信息，请参阅本主题前面的操作过程。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-164">For more information, see previous procedures in this topic.</span></span>  
  
2.  <span data-ttu-id="7ec1f-165">右键单击发布服务器组，再单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="7ec1f-165">Right-click the Publisher group, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec1f-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ec1f-166">See Also</span></span>  
 <span data-ttu-id="7ec1f-167">[“配置分发”](../configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="7ec1f-167">[Configure Distribution](../configure-distribution.md) </span></span>  
 [<span data-ttu-id="7ec1f-168">监视复制</span><span class="sxs-lookup"><span data-stu-id="7ec1f-168">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
