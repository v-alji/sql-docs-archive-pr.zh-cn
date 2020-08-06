---
title: 查看脱机日志文件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer, viewing offline logs
- offline log files
ms.assetid: 9223e474-f224-4907-a4f2-081e11db58f5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2afc1992b54c78f69bfae1fc152b41c20bcd4ea1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589065"
---
# <a name="view-offline-log-files"></a><span data-ttu-id="2355f-102">查看脱机日志文件</span><span class="sxs-lookup"><span data-stu-id="2355f-102">View Offline Log Files</span></span>
  <span data-ttu-id="2355f-103">从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]开始，您可以在目标实例处于脱机状态或无法启动时，从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的本地或远程实例查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日志文件。</span><span class="sxs-lookup"><span data-stu-id="2355f-103">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], you can view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files from a local or remote instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when the target instance is offline or cannot start.</span></span>  
  
 <span data-ttu-id="2355f-104">您可以从注册的服务器访问脱机日志文件，或者以编程方式通过 WMI 和 WQL（WMI 查询语言）查询访问这些文件。</span><span class="sxs-lookup"><span data-stu-id="2355f-104">You can access the offline log files from Registered Servers, or programmatically through WMI and WQL (WMI Query Language) queries.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2355f-105">您还可以使用这些方法连接到联机实例，但是因为某种原因，您无法通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接进行连接。</span><span class="sxs-lookup"><span data-stu-id="2355f-105">You can also use these methods to connect to an instance that is online, but for some reason, you cannot connect through a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="2355f-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="2355f-106">Before you Begin</span></span>  
 <span data-ttu-id="2355f-107">若要连接到脱机日志文件， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例必须安装在您用于查看脱机日志文件的计算机上，以及您查看的日志文件所在的计算机上。</span><span class="sxs-lookup"><span data-stu-id="2355f-107">To connect to offline log files, an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be installed on the computer that you are using to view the offline log files, and on the computer where the log files that you want to view are located.</span></span> <span data-ttu-id="2355f-108">如果两台计算机上都安装有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，则您可以在任意一台计算机上查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的脱机文件，以及运行早期版本 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的脱机文件。</span><span class="sxs-lookup"><span data-stu-id="2355f-108">If an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on both computers, you can view offline files for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and for instances that are running earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on either computer.</span></span>  
  
 <span data-ttu-id="2355f-109">如果正在使用已注册的服务器，您想要连接到的实例必须在 **“本地服务器组”** 或 **“中央管理服务器”** 下注册。</span><span class="sxs-lookup"><span data-stu-id="2355f-109">If you are using Registered Servers, the instance that you want to connect to must be registered under **Local Server Groups** or under **Central Management Servers**.</span></span> <span data-ttu-id="2355f-110">实例可以单独进行注册，也可以注册为服务器组的成员。有关如何将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例添加到已注册的服务器的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="2355f-110">(The instance can be registered on its own or be a member of a server group.) For more information about how to add an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to Registered Servers, see the following topics:</span></span>  
  
-   [<span data-ttu-id="2355f-111">创建或编辑服务器组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="2355f-111">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="2355f-112">注册连接的服务器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="2355f-112">Register a Connected Server &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="2355f-113">创建中央管理服务器和服务器组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="2355f-113">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
 <span data-ttu-id="2355f-114">有关如何以编程方式通过 WMI 和 WQL 查询查看脱机日志文件的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="2355f-114">For more information about how to view offline log files programmatically through WMI and WQL queries, see the following topics:</span></span>  
  
-   <span data-ttu-id="2355f-115">[SqlErrorLogEvent 类](../wmi-provider-configuration-classes/sqlerrorlogevent-class.md) （本主题显示如何检索指定日志文件中记录的事件的值。）</span><span class="sxs-lookup"><span data-stu-id="2355f-115">[SqlErrorLogEvent Class](../wmi-provider-configuration-classes/sqlerrorlogevent-class.md) (This topic shows how to retrieve values for logged events in a specified log file.)</span></span>  
  
-   <span data-ttu-id="2355f-116">[SqlErrorLogFile 类](../wmi-provider-configuration-classes/sqlerrorlogfile-class.md) （本主题显示如何检索有关指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]日志文件的信息。）</span><span class="sxs-lookup"><span data-stu-id="2355f-116">[SqlErrorLogFile Class](../wmi-provider-configuration-classes/sqlerrorlogfile-class.md) (This topic shows how to retrieve information about all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files on a specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2355f-117">权限</span><span class="sxs-lookup"><span data-stu-id="2355f-117">Permissions</span></span>  
 <span data-ttu-id="2355f-118">若要连接到脱机日志文件，您必须在本地和远程计算机上同时具有以下权限：</span><span class="sxs-lookup"><span data-stu-id="2355f-118">To connect to an offline log file, you must have the following permissions on both the local and remote computers:</span></span>  
  
-   <span data-ttu-id="2355f-119">针对 **Root\Microsoft\SqlServer\ComputerManagement12** WMI 命名空间的读取访问权限。</span><span class="sxs-lookup"><span data-stu-id="2355f-119">Read access to the **Root\Microsoft\SqlServer\ComputerManagement12** WMI namespace.</span></span> <span data-ttu-id="2355f-120">默认情况下，每个人都可以通过“启用帐户”权限获得读取权限。</span><span class="sxs-lookup"><span data-stu-id="2355f-120">By default, everyone has read access through the Enable Account permission.</span></span> <span data-ttu-id="2355f-121">有关详细信息，请参阅本节后面的“验证 WMI 权限”过程。</span><span class="sxs-lookup"><span data-stu-id="2355f-121">For more information, see the "To verify WMI permissions" procedure later in this section.</span></span>  
  
-   <span data-ttu-id="2355f-122">对包含错误日志文件的文件夹的读取权限。</span><span class="sxs-lookup"><span data-stu-id="2355f-122">Read permission to the folder that contains the error log files.</span></span> <span data-ttu-id="2355f-123">默认情况下，错误日志文件位于下面的路径中（其中 \<*Drive>\* 表示安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的驱动器，\<*InstanceName*> 是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称）：</span><span class="sxs-lookup"><span data-stu-id="2355f-123">By default the error log files are located in the following path (where \<*Drive>\* represents the drive where you installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and \<*InstanceName*> is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):</span></span>  
  
     <span data-ttu-id="2355f-124">**\<Drive>： \Program Files\Microsoft SQL Server\MSSQL12. \<InstanceName>\MSSQL\Log**</span><span class="sxs-lookup"><span data-stu-id="2355f-124">**\<Drive>:\Program Files\Microsoft SQL Server\MSSQL12.\<InstanceName>\MSSQL\Log**</span></span>  
  
 <span data-ttu-id="2355f-125">若要验证 WMI 命名空间安全设置，您可以使用 WMI 控制管理单元。</span><span class="sxs-lookup"><span data-stu-id="2355f-125">To verify WMI namespace security settings, you can use the WMI Control snap-in.</span></span>  
  
#### <a name="to-verify-wmi-permissions"></a><span data-ttu-id="2355f-126">验证 WMI 权限</span><span class="sxs-lookup"><span data-stu-id="2355f-126">To verify WMI permissions</span></span>  
  
1.  <span data-ttu-id="2355f-127">打开 WMI 控制管理单元。</span><span class="sxs-lookup"><span data-stu-id="2355f-127">Open the WMI Control snap-in.</span></span> <span data-ttu-id="2355f-128">为此，请根据所用操作系统执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="2355f-128">To do this, do either of the following, depending on the operating system:</span></span>  
  
    -   <span data-ttu-id="2355f-129">单击 "**开始**"， `wmimgmt.msc` 在 "**开始搜索**" 框中键入，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="2355f-129">Click **Start**, type `wmimgmt.msc` in the **Start Search** box, and then press ENTER.</span></span>  
  
    -   <span data-ttu-id="2355f-130">依次单击 "**开始**"、"**运行**"，键入 `wmimgmt.msc` ，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="2355f-130">Click **Start**, click **Run**, type `wmimgmt.msc`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="2355f-131">默认情况下，WMI 控制管理单元管理本地计算机。</span><span class="sxs-lookup"><span data-stu-id="2355f-131">By default, the WMI Control snap-in manages the local computer.</span></span>  
  
     <span data-ttu-id="2355f-132">如果您想要连接到远程计算机，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="2355f-132">If you want to connect to a remote computer, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="2355f-133">右键单击“WMI 控制(本地)” ，然后单击“连接到另一台计算机” 。</span><span class="sxs-lookup"><span data-stu-id="2355f-133">Right-click **WMI Control (Local)**, and then click **Connect to another computer**.</span></span>  
  
    2.  <span data-ttu-id="2355f-134">在 **“更改被管理的计算机”** 对话框中，单击 **“另一台计算机”** 。</span><span class="sxs-lookup"><span data-stu-id="2355f-134">In the **Change managed computer** dialog box, click **Another computer**.</span></span>  
  
    3.  <span data-ttu-id="2355f-135">输入远程计算机名称，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="2355f-135">Enter the remote computer name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="2355f-136">右键单击 " **Wmi 控制" (本地) **或**WMI control (***RemoteComputerName***) **，然后单击 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="2355f-136">Right-click **WMI Control (Local)** or **WMI Control (***RemoteComputerName***)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="2355f-137">在 **“WMI 控制属性”** 对话框中，单击 **“安全”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="2355f-137">In the **WMI Control Properties** dialog box, click the **Security** tab.</span></span>  
  
5.  <span data-ttu-id="2355f-138">在命名空间树中，找到并单击以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="2355f-138">In the namespace tree, locate and then click the following namespace:</span></span>  
  
     <span data-ttu-id="2355f-139">**Root\Microsoft\SqlServer\ComputerManagement10**</span><span class="sxs-lookup"><span data-stu-id="2355f-139">**Root\Microsoft\SqlServer\ComputerManagement10**</span></span>  
  
6.  <span data-ttu-id="2355f-140">单击 **“安全性”** 。</span><span class="sxs-lookup"><span data-stu-id="2355f-140">Click **Security**.</span></span>  
  
7.  <span data-ttu-id="2355f-141">确保要使用的帐户具有 **“启用帐户”** 权限。</span><span class="sxs-lookup"><span data-stu-id="2355f-141">Make sure that the account that will be used has the **Enable Account** permission.</span></span> <span data-ttu-id="2355f-142">此权限允许对 WMI 对象具有读取权限。</span><span class="sxs-lookup"><span data-stu-id="2355f-142">This permission allows Read access to WMI objects.</span></span>  
  
### <a name="view-log-files"></a><span data-ttu-id="2355f-143">查看日志文件</span><span class="sxs-lookup"><span data-stu-id="2355f-143">View Log Files</span></span>  
 <span data-ttu-id="2355f-144">下面的过程显示如何通过已注册的服务器查看脱机日志文件。</span><span class="sxs-lookup"><span data-stu-id="2355f-144">The following procedure shows how to view offline log files through Registered Servers.</span></span> <span data-ttu-id="2355f-145">该过程假设存在以下条件：</span><span class="sxs-lookup"><span data-stu-id="2355f-145">The procedure assumes the following:</span></span>  
  
 <span data-ttu-id="2355f-146">您要连接到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例已在注册的服务器中注册。</span><span class="sxs-lookup"><span data-stu-id="2355f-146">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to connect to is already registered in Registered Servers.</span></span>  
  
##### <a name="to-view-log-files-for-instances-that-are-offline"></a><span data-ttu-id="2355f-147">查看脱机实例的日志文件</span><span class="sxs-lookup"><span data-stu-id="2355f-147">To view log files for instances that are offline</span></span>  
  
1.  <span data-ttu-id="2355f-148">如果您要查看本地实例的脱机日志文件，请确保使用提升的权限启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2355f-148">If you want to view offline log files on a local instance, make sure that you start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] with elevated permissions.</span></span> <span data-ttu-id="2355f-149">若要这样做，请在启动 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 时，右键单击“SQL Server Management Studio”，然后单击“以管理员身份运行” 。</span><span class="sxs-lookup"><span data-stu-id="2355f-149">To do this, when you start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click **SQL Server Management Studio**, and then click **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="2355f-150">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的 **“视图”** 菜单上，单击 **“已注册的服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="2355f-150">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
3.  <span data-ttu-id="2355f-151">在控制台树中，找到您想要在其上查看脱机文件的实例。</span><span class="sxs-lookup"><span data-stu-id="2355f-151">In the console tree, locate the instance on which you want to view the offline files.</span></span>  
  
4.  <span data-ttu-id="2355f-152">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="2355f-152">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="2355f-153">如果实例位于“本地服务器组”下，则展开“本地服务器组”，展开服务器组（如果实例是组的成员），右键单击该实例，然后单击“查看 SQL Server 日志”  。</span><span class="sxs-lookup"><span data-stu-id="2355f-153">If the instance is under **Local Server Groups**, expand **Local Server Groups**, expand the server group (if the instance is a member of a group), right-click the instance, and then click **View SQL Server Log**.</span></span>  
  
    -   <span data-ttu-id="2355f-154">如果实例是中央管理服务器本身，则展开“中央管理服务器”，右键单击该实例，指向“中央管理服务器操作”，然后单击“查看 SQL Server 日志”  。</span><span class="sxs-lookup"><span data-stu-id="2355f-154">If the instance is the Central Management Server itself, expand **Central Management Servers**, right-click the instance, point to **Central Management Server Actions**, and then click **View SQL Server Log**.</span></span>  
  
    -   <span data-ttu-id="2355f-155">如果实例位于“中央管理服务器”下，则展开“中央管理服务器”，展开中央管理服务器，右键单击该实例（或展开服务器组并右键单击该实例），然后单击“查看 SQL Server 日志”  。</span><span class="sxs-lookup"><span data-stu-id="2355f-155">If the instance is under **Central Management Servers**, expand **Central Management Servers**, expand the Central Management Server, right-click the instance (or expand a server group and right-click the instance), and then click **View SQL Server Log**.</span></span>  
  
5.  <span data-ttu-id="2355f-156">如果您要连接到本地实例，则使用当前用户凭据建立连接。</span><span class="sxs-lookup"><span data-stu-id="2355f-156">If you are connecting to a local instance, the connection is made using the current user credentials.</span></span>  
  
     <span data-ttu-id="2355f-157">如果你要连接到远程实例，请在“日志文件查看器 - 连接为”  对话框中，执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="2355f-157">If you are connecting to a remote instance, in the **Log File Viewer - Connect As** dialog box, do either of the following:</span></span>  
  
    -   <span data-ttu-id="2355f-158">若要以当前用户身份进行连接，请确保清除 **“以其他用户身份连接”** 复选框，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="2355f-158">To connect as the current user, make sure that the **Connect as another user** check box is cleared, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="2355f-159">若要以其他用户身份连接，请选中 **“以其他用户身份连接”** 复选框，然后单击 **“设置用户”** 。</span><span class="sxs-lookup"><span data-stu-id="2355f-159">To connect as another user, select the **Connect as another user** check box, and then click **Set User**.</span></span> <span data-ttu-id="2355f-160">出现提示后，输入用户凭据（以 *domain_name*\\*user_name* 格式输入用户名称），单击“确定”，然后再次单击“确定”以进行连接 。</span><span class="sxs-lookup"><span data-stu-id="2355f-160">When you are prompted, enter the user credentials (with the user name in the format *domain_name*\\*user_name*), click **OK**, and then click **OK** again to connect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2355f-161">如果日志文件加载时间过长，你可以单击日志文件查看器工具栏上的“停止”  。</span><span class="sxs-lookup"><span data-stu-id="2355f-161">If the log files take too long to load, you can click **Stop** on the Log File Viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2355f-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2355f-162">See Also</span></span>  
 [<span data-ttu-id="2355f-163">日志文件查看器</span><span class="sxs-lookup"><span data-stu-id="2355f-163">Log File Viewer</span></span>](log-file-viewer.md)  
  
  
