---
title: 创建和编辑 Oracle CDC 服务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- createSrv
ms.assetid: 10cd612e-d8f1-4af2-97d3-a0c22e1e2326
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3325e272285895e813f01d50a1c312e75472919b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580332"
---
# <a name="create-and-edit-an-oracle-cdc-service"></a><span data-ttu-id="22bf8-102">创建和编辑 Oracle CDC 服务</span><span class="sxs-lookup"><span data-stu-id="22bf8-102">Create and Edit an Oracle CDC Service</span></span>
  <span data-ttu-id="22bf8-103">您从 CDC 服务配置控制台创建和编辑新的 Oracle CDC Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="22bf8-103">You create and edit a new Oracle CDC Windows Service from the CDC Service Configuration Console.</span></span>  
  
 <span data-ttu-id="22bf8-104">若要创建新的 Oracle CDC Windows 服务，请从左侧窗格中选择 **“本地 CDC 服务”** ，然后从 **“操作”** 窗格中单击 **“新建服务”** 。</span><span class="sxs-lookup"><span data-stu-id="22bf8-104">To create a new Oracle CDC Windows service, select **Local CDC Services** from the left pane, then click **New Service** from the **Actions** pane.</span></span> <span data-ttu-id="22bf8-105">还可以右键单击“本地 CDC 服务”  ，然后选择“新建服务”  。</span><span class="sxs-lookup"><span data-stu-id="22bf8-105">You can also right-click **Local CDC Services** and select **New Service**.</span></span> <span data-ttu-id="22bf8-106">“新 Oracle CDC Windows 服务”对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="22bf8-106">The New Oracle CDC Windows Service dialog box opens.</span></span>  
  
 <span data-ttu-id="22bf8-107">**OR**</span><span class="sxs-lookup"><span data-stu-id="22bf8-107">**OR**</span></span>  
  
 <span data-ttu-id="22bf8-108">若要编辑 CDC 服务属性，请选择要编辑其属性的服务，然后从 **“操作”** 窗格中单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="22bf8-108">To edit the CDC service properties, select the service that you want to edit the properties for and click **Properties** from the **Actions** pane.</span></span> <span data-ttu-id="22bf8-109">还可以右键单击要使用的服务，然后选择“属性”。 </span><span class="sxs-lookup"><span data-stu-id="22bf8-109">You can also right-click the service you are working with and select **Properties**.</span></span> <span data-ttu-id="22bf8-110">此时将打开“CDC 服务属性”对话框。</span><span class="sxs-lookup"><span data-stu-id="22bf8-110">The CDC Service Properties dialog box opens.</span></span>  
  
 <span data-ttu-id="22bf8-111">在“新 Oracle CDC Windows 服务”对话框或“CDC 服务属性”对话框中输入以下信息。</span><span class="sxs-lookup"><span data-stu-id="22bf8-111">Enter the following information in the New Oracle CDC Windows Service dialog box or the CDC Service Properties dialog box.</span></span>  
  
 <span data-ttu-id="22bf8-112">服务名称</span><span class="sxs-lookup"><span data-stu-id="22bf8-112">Service Name</span></span>  
 <span data-ttu-id="22bf8-113">键入新的 Oracle CDC Windows 服务的名称。</span><span class="sxs-lookup"><span data-stu-id="22bf8-113">Type the name of the new Oracle CDC Windows Service.</span></span> <span data-ttu-id="22bf8-114">如果可能，不应使用长名称。</span><span class="sxs-lookup"><span data-stu-id="22bf8-114">You should not use long names, if possible.</span></span> <span data-ttu-id="22bf8-115">在服务名称中不能使用字符 / 和 \。</span><span class="sxs-lookup"><span data-stu-id="22bf8-115">The characters / and \ cannot be used in the service name.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="22bf8-116">在编辑服务时，此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="22bf8-116">This option is not available when editing the service.</span></span> <span data-ttu-id="22bf8-117">不能更改已存在的 Windows 服务的名称。</span><span class="sxs-lookup"><span data-stu-id="22bf8-117">You cannot change the name of a Windows service that already exists.</span></span>  
  
 <span data-ttu-id="22bf8-118">**说明**</span><span class="sxs-lookup"><span data-stu-id="22bf8-118">**Description**</span></span>  
 <span data-ttu-id="22bf8-119">键入有助于标识该服务的说明。</span><span class="sxs-lookup"><span data-stu-id="22bf8-119">Type a description of the service to help identify it.</span></span>  
  
 <span data-ttu-id="22bf8-120">**服务帐户**</span><span class="sxs-lookup"><span data-stu-id="22bf8-120">**Service Account**</span></span>  
 <span data-ttu-id="22bf8-121">选择下列选项之一以便确定运行服务所基于的帐户：</span><span class="sxs-lookup"><span data-stu-id="22bf8-121">Select one of the following to determine under which account to run the service:</span></span>  
  
-   <span data-ttu-id="22bf8-122">**Local System 帐户**</span><span class="sxs-lookup"><span data-stu-id="22bf8-122">**Local System Account**</span></span>  
  
     <span data-ttu-id="22bf8-123">该帐户不是建议的帐户，因为对服务提供了过多的权限。</span><span class="sxs-lookup"><span data-stu-id="22bf8-123">This is not recommended because it gives too many permissions to the service.</span></span>  
  
-   <span data-ttu-id="22bf8-124">**本帐户**</span><span class="sxs-lookup"><span data-stu-id="22bf8-124">**This Account**</span></span>  
  
     <span data-ttu-id="22bf8-125">在 Windows Vista 或 Windows Server 2008 中，默认服务帐户是 NETWORK SERVICE 帐户。</span><span class="sxs-lookup"><span data-stu-id="22bf8-125">On Windows Vista or Windows Server 2008, the default service account is the NETWORK SERVICE account.</span></span>  
  
     <span data-ttu-id="22bf8-126">在 Windows 7、Windows Server 2008 R2 和更高版本中，默认服务帐户是 NT Service\\<service-name>。</span><span class="sxs-lookup"><span data-stu-id="22bf8-126">On Windows 7, Windows Server 2008 R2 and later, the default service account is NT Service\\<service-name>.</span></span>  
  
     <span data-ttu-id="22bf8-127">通过使用这些帐户，您可以在不使用密码的情况下工作，因为对于这些帐户不需要密码。</span><span class="sxs-lookup"><span data-stu-id="22bf8-127">Using these accounts lets you work without using passwords because a password is not necessary for these accounts.</span></span> <span data-ttu-id="22bf8-128">此外，这些帐户仅提供运行 Oracle CDC 服务所需的必要权限。</span><span class="sxs-lookup"><span data-stu-id="22bf8-128">In addition these accounts provide only the necessary permissions required for the Oracle CDC Service to run.</span></span>  
  
     <span data-ttu-id="22bf8-129">可以将本地或域 Windows 帐户用于该服务帐户。</span><span class="sxs-lookup"><span data-stu-id="22bf8-129">You can use a local or domain Windows account for the service account.</span></span> <span data-ttu-id="22bf8-130">在此情况下，必须为该帐户输入 **“密码”** 。</span><span class="sxs-lookup"><span data-stu-id="22bf8-130">In this case, you must enter the **Password** for that account.</span></span> <span data-ttu-id="22bf8-131">该帐户可以用于本地主机或域帐户。</span><span class="sxs-lookup"><span data-stu-id="22bf8-131">This account can be for the local host or a domain account.</span></span> <span data-ttu-id="22bf8-132">请确保在 Windows 控制面板中使用本地服务更改帐户时更新密码。</span><span class="sxs-lookup"><span data-stu-id="22bf8-132">Be sure to update the password when it is changed using Local Services in the Windows Control Panel.</span></span>  
  
 <span data-ttu-id="22bf8-133">**服务器名称**：选择要连接到的目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例（例如 \\\\<computer_name>\\<instance_name>  ）。</span><span class="sxs-lookup"><span data-stu-id="22bf8-133">**Server name**: Select the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to connect to (for example, **\\\\<computer_name>\\<instance_name>**).</span></span> <span data-ttu-id="22bf8-134">默认情况下，显示上次连接到的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="22bf8-134">The server instance last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="22bf8-135">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="22bf8-135">**Authentication**</span></span>  
 <span data-ttu-id="22bf8-136">选择以下方案之一：</span><span class="sxs-lookup"><span data-stu-id="22bf8-136">Select one of the following:</span></span>  
  
-   <span data-ttu-id="22bf8-137">**Windows 身份验证**：如果选择此选项，Oracle CDC 服务将使用服务帐户标识连接到目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="22bf8-137">**Windows Authentication**: If you select this option, the Oracle CDC service connects to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using the service account identity.</span></span> <span data-ttu-id="22bf8-138">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例正在不同的计算机上运行，则必须将 Windows 身份验证用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="22bf8-138">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is running on a different computer, Windows Authentication must be used with domain accounts.</span></span>  
  
-   <span data-ttu-id="22bf8-139">**SQL Server 身份验证**：如果选择此选项，则必须为你要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名键入“用户名”  和“密码”  。</span><span class="sxs-lookup"><span data-stu-id="22bf8-139">**SQL Server Authentication**: If you select this option, you must type the **User Name** and **Password** for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login you want to use.</span></span> <span data-ttu-id="22bf8-140">Oracle CDC 服务在连接到目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时使用这些凭据。</span><span class="sxs-lookup"><span data-stu-id="22bf8-140">The Oracle CDC service uses these credentials when connecting to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="22bf8-141">Oracle CDC 服务使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名仅需是公共固定服务器角色的成员，无需其他权限。</span><span class="sxs-lookup"><span data-stu-id="22bf8-141">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used by the Oracle CDC Service only needs to be a member of the public fixed-server role, no other privileges are needed.</span></span> <span data-ttu-id="22bf8-142">在添加了新的 Oracle CDC 实例后，该登录名将获取对关联的 **CDC 数据库的** db_owner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 访问权限。</span><span class="sxs-lookup"><span data-stu-id="22bf8-142">Once new Oracle CDC Instances are added, that login will gain **db_owner** access to the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC databases.</span></span>  
  
 <span data-ttu-id="22bf8-143">若要创建 Oracle CDC Windows 服务定义，程序需要对关联的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中的 MSXDBCDC 数据库具有更新访问权限。</span><span class="sxs-lookup"><span data-stu-id="22bf8-143">To create the Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="22bf8-144">在单击 **“确定”** 后，将出现一个对话框，提示用户输入具有对 MSXDBCDC 数据库的更新访问权限的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="22bf8-144">When you click **OK**, a dialog box prompts the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with an update access to the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="22bf8-145">有关必须在“连接到 SQL Server”对话框中键入的数据的信息，请参阅 [Connection to SQL Server](connection-to-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="22bf8-145">For information about the data you must type into the Connect to SQL Server dialog box, see [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
 <span data-ttu-id="22bf8-146">**选项**</span><span class="sxs-lookup"><span data-stu-id="22bf8-146">**Options**</span></span>  
 <span data-ttu-id="22bf8-147">单击箭头可以查看要配置的可用选项。</span><span class="sxs-lookup"><span data-stu-id="22bf8-147">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="22bf8-148">您可以选择保留这些选项不变，使用其默认值。</span><span class="sxs-lookup"><span data-stu-id="22bf8-148">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="22bf8-149">可用选项是：</span><span class="sxs-lookup"><span data-stu-id="22bf8-149">The available options are:</span></span>  
  
-   <span data-ttu-id="22bf8-150">**连接超时值**：键入一个时间（秒钟），未超过该时间，Oracle CDC 服务将等待与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的连接，超过该时间后即超时。默认值为 **15**。</span><span class="sxs-lookup"><span data-stu-id="22bf8-150">**Connection Timeout**: Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
-   <span data-ttu-id="22bf8-151">**执行超时值**：键入一个时间（秒钟），未超过该时间，Oracle CDC Windows 服务将等待命令执行，超过该时间后即超时。默认值为 **30**。</span><span class="sxs-lookup"><span data-stu-id="22bf8-151">**Execution Timeout**: Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
-   <span data-ttu-id="22bf8-152">**加密连接**：选择“加密连接”  将使用加密连接进行 Oracle CDC 服务和目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例之间的通信。</span><span class="sxs-lookup"><span data-stu-id="22bf8-152">**Encrypt Connection**: Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.</span></span>  
  
-   <span data-ttu-id="22bf8-153">**高级**：根据需要键入任何其他连接属性。</span><span class="sxs-lookup"><span data-stu-id="22bf8-153">**Advanced**: Type any additional connection properties, if necessary.</span></span>  
  
 <span data-ttu-id="22bf8-154">**主密码**</span><span class="sxs-lookup"><span data-stu-id="22bf8-154">**Master Password**</span></span>  
 <span data-ttu-id="22bf8-155">输入 Oracle CDC Windows 服务用来保护 Oracle 日志挖掘凭据的密码。</span><span class="sxs-lookup"><span data-stu-id="22bf8-155">Enter a password to be used by the Oracle CDC Windows Service to protect the Oracle log-mining credentials.</span></span>  
  
 <span data-ttu-id="22bf8-156">在高可用性配置中，如果在群集中的其他节点上配置了相同服务的其他实例，则也必须使用相同的主密码。</span><span class="sxs-lookup"><span data-stu-id="22bf8-156">The same master password must also be used when other instances of the same service are configured on other nodes on a cluster in high-availability configuration.</span></span> <span data-ttu-id="22bf8-157">如果您丢失或修改了该主密码，则必须使用 CDC 设计器控制台重新输入在 Oracle CDC 实例数据库中存储的所有日志挖掘密码。</span><span class="sxs-lookup"><span data-stu-id="22bf8-157">If you lose or modify the master password, all log mining passwords stored in Oracle CDC Instance databases must be re-entered using the CDC Designer console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22bf8-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22bf8-158">See Also</span></span>  
 [<span data-ttu-id="22bf8-159">如何创建和编辑 CDC 服务</span><span class="sxs-lookup"><span data-stu-id="22bf8-159">How to Create and Edit a CDC Service</span></span>](how-to-create-and-edit-a-cdc-service.md)  
  
  
