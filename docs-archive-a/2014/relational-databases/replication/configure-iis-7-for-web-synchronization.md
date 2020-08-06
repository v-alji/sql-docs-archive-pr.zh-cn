---
title: 配置 IIS 7 以实现 Web 同步 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- IIS 7 server configuration [SQL Server replication]
- Web synchronization, IIS 7 servers
ms.assetid: c201fe2c-0a76-44e5-a233-05e14cd224a6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 65b5aa1ea0d314a9675b1c1b90b688d2990e6d24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591873"
---
# <a name="configure-iis-7-for-web-synchronization"></a><span data-ttu-id="1f3ea-102">配置 IIS 7 以实现 Web 同步</span><span class="sxs-lookup"><span data-stu-id="1f3ea-102">Configure IIS 7 for Web Synchronization</span></span>
  <span data-ttu-id="1f3ea-103">本主题针对如何将 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) 版本 7 及更高版本用于合并复制的 Web 同步，介绍手动配置 IIS 的完整过程。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-103">The procedures in this topic will guide you through the process of manually configuring [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) version 7 and higher for use with Web synchronization for merge replication.</span></span> 
  
 <span data-ttu-id="1f3ea-104">配置 IIS 7 是启用 Web 同步所需的三个步骤中的第一步。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-104">Configuring IIS 7 is the first of three steps needed to enable Web synchronization.</span></span>  
  
 <span data-ttu-id="1f3ea-105">有关整个配置过程的概述，请参阅[配置 Web 同步](configure-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-105">For an overview of the entire configuration process, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1f3ea-106">请确保您的应用程序仅使用 [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] 或更高版本，并且 IIS 服务器上没有安装 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 的较早版本。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-106">Make sure that your application uses only [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] or later versions, and that earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] are not installed on the IIS server.</span></span> <span data-ttu-id="1f3ea-107">较早版本的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 可能导致错误，例如：“Web 同步期间消息的格式无效。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-107">Earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] can cause errors, such as: "The format of a message during Web synchronization was invalid.</span></span> <span data-ttu-id="1f3ea-108">请确保在 Web 服务器上正确配置了复制组件。”。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-108">Ensure that replication components are properly configured at the Web server."</span></span>  
  
 <span data-ttu-id="1f3ea-109">若要使用 Web 同步，必须通过完成以下步骤来配置 IIS 7。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-109">To use Web synchronization, you must configure IIS 7 by completing the following steps.</span></span> <span data-ttu-id="1f3ea-110">本主题对每个步骤都进行了详细说明。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-110">Each step is described in detail in this topic.</span></span>  
  
1.  <span data-ttu-id="1f3ea-111">在运行 IIS 的计算机上安装和配置 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制侦听器。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-111">Install and configure the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener on the computer that is running IIS.</span></span>  
  
2.  <span data-ttu-id="1f3ea-112">配置安全套接字层 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-112">Configure Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="1f3ea-113">IIS 和所有订阅服务器之间的通信需要 SSL。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-113">SSL is required for communication between IIS and all subscribers.</span></span>  
  
3.  <span data-ttu-id="1f3ea-114">配置 IIS 身份验证。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-114">Configure IIS authentication.</span></span>  
  
4.  <span data-ttu-id="1f3ea-115">为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制侦听器配置帐户并设置权限。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-115">Configure an account and set permissions for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener.</span></span>  
  
## <a name="installing-the-sql-server-replication-listener"></a><span data-ttu-id="1f3ea-116">安装 SQL Server 复制侦听器</span><span class="sxs-lookup"><span data-stu-id="1f3ea-116">Installing the SQL Server Replication Listener</span></span>  

<span data-ttu-id="1f3ea-117">从版本 5.0 开始，IIS 中支持 Web 同步。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-117">Web synchronization is supported on IIS, beginning with version 5.0.</span></span> <span data-ttu-id="1f3ea-118">IIS 版本 5 和 6 的“配置 Web 同步向导”不可与 IIS 版本 7.0 和更高版本一起使用。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-118">The Configure Web Synchronization Wizard of IIS version 5 and 6, is not available with IIS version 7.0 and higher.</span></span> <span data-ttu-id="1f3ea-119">**从 SQL Server 2012 开始，要使用 IIS 服务器上的 Web 同步组件，应当随复制安装 SQL Server。这可以是免费的 SQL Server Express 版本。**</span><span class="sxs-lookup"><span data-stu-id="1f3ea-119">**Beginning with SQL Server 2012, to use the web sync component on IIS server, you should install SQL Server with replication. This can be the free SQL Server Express edition.**</span></span>
  
#### <a name="to-install-and-configure-the-sql-server-replication-listener"></a><span data-ttu-id="1f3ea-120">安装和配置 SQL Server 复制侦听器</span><span class="sxs-lookup"><span data-stu-id="1f3ea-120">To install and configure the SQL Server Replication Listener</span></span>  
  
1. <span data-ttu-id="1f3ea-121">在 IIS 计算机上安装 SQL Server 复制。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-121">Install SQL Server replication on the IIS computer.</span></span>

2.  <span data-ttu-id="1f3ea-122">在正在运行 IIS 的计算机上为 replisapi.dll 创建一个新的文件目录。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-122">Create a new file directory for replisapi.dll on the computer that is running IIS.</span></span> <span data-ttu-id="1f3ea-123">可在任意位置创建该目录，但建议将该目录创建在 \<*drive*>:\Inetpub 目录下。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-123">You can create the directory wherever you want, but we recommend that you create the directory under the \<*drive*>:\Inetpub directory.</span></span> <span data-ttu-id="1f3ea-124">例如，可以创建目录 \<*drive*>:\Inetpub\SQLReplication\\。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-124">For example, create the directory \<*drive*>:\Inetpub\SQLReplication\\.</span></span>  
  
3.  <span data-ttu-id="1f3ea-125">将 replisapi.dll 从目录 [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ 复制到在步骤 1 中创建的文件目录。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-125">Copy replisapi.dll from the directory [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ to the file directory that you created in step 1.</span></span>  
  
4.  <span data-ttu-id="1f3ea-126">注册 replisapi.dll：</span><span class="sxs-lookup"><span data-stu-id="1f3ea-126">Register replisapi.dll:</span></span>  
  
    1.  <span data-ttu-id="1f3ea-127">单击 **“启动”** ，再单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-127">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="1f3ea-128">在 "**打开**" 框中，输入 `cmd` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-128">In the **Open** box, enter `cmd`, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="1f3ea-129">在步骤 1 所创建的目录中，执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="1f3ea-129">In the directory created in step 1, execute the following command:</span></span>  
  
         `regsvr32 replisapi.dll`  
  
5.  <span data-ttu-id="1f3ea-130">创建一个用于复制的新网站或使用现有网站。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-130">Create a new Web site for replication or use an existing site.</span></span> <span data-ttu-id="1f3ea-131">复制组件将在同步过程中访问此网站。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-131">This Web site will be accessed by replication components during synchronization.</span></span> <span data-ttu-id="1f3ea-132">本主题中的过程将假定使用“默认网站”。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-132">Procedures in this topic will assume the Default Web Site.</span></span> <span data-ttu-id="1f3ea-133">有关如何创建网站的详细信息，请参阅 IIS 文档。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-133">For more information about how to create Web sites, see the IIS documentation</span></span>  
  
6.  <span data-ttu-id="1f3ea-134">在 IIS 上创建一个虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-134">Create a virtual directory in IIS.</span></span> <span data-ttu-id="1f3ea-135">应在步骤 4 所创建的网站下创建虚拟目录，并将其映射到步骤 1 中创建的目录。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-135">The virtual directory should be created under the Web site that you created in step 4 and map it to the directory created in step 1.</span></span> <span data-ttu-id="1f3ea-136">建议尽量限制为此目录分配权限。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-136">Be as restrictive as possible when you assign permissions to this directory.</span></span> <span data-ttu-id="1f3ea-137">您必须至少选择 **“读取”** 权限和 **“执行”** 权限。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-137">You must select at least **Read** and **Execute** permissions.</span></span>  
  
    1.  <span data-ttu-id="1f3ea-138">在 **“Internet 信息服务(IIS)管理器”** 的 **“连接”** 窗格中，右键单击 **“默认网站”** ，然后选择 **“添加虚拟目录”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-138">In **Internet Information Services (IIS) Manager**, in the **Connections** pane, right-click **Default Web Site**, and then select **Add Virtual Directory**.</span></span>  
  
    2.  <span data-ttu-id="1f3ea-139">对于 "**别名**"，请输入 `SQLReplication` 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-139">For **Alias**, enter `SQLReplication`.</span></span>  
  
    3.  <span data-ttu-id="1f3ea-140">对于“物理路径”，输入 \<drive>:\Inetpub\SQLReplication\\，然后单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="1f3ea-140">For **Physical Path**, enter **\<drive>:\Inetpub\SQLReplication\\**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="1f3ea-141">配置 IIS 以允许执行 replisapi.dll。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-141">Configure IIS to enable replisapi.dll to execute.</span></span>  
  
    1.  <span data-ttu-id="1f3ea-142">在 **“Internet 信息服务(IIS)管理器”** 中，单击 **“默认网站”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-142">In **Internet Information Services (IIS) Manager**, click **Default Web Site**.</span></span>  
  
    2.  <span data-ttu-id="1f3ea-143">在中央窗格中，单击 **“处理程序映射”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-143">In the center pane, click **Handler Mappings**.</span></span>  
  
    3.  <span data-ttu-id="1f3ea-144">在 **“操作”** 窗格中，单击 **“添加模块映射”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-144">In the **Actions** pane, click **Add Module Mapping**.</span></span>  
  
    4.  <span data-ttu-id="1f3ea-145">对于 "**请求**路径"，请输入 `replisapi.dll` 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-145">For **Request** Path, enter `replisapi.dll`.</span></span>  
  
    5.  <span data-ttu-id="1f3ea-146">从 **“模块”** 下拉列表中，选择 **“IsapiModule”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-146">From the **Module** drop-down list, select **IsapiModule**.</span></span>  
  
    6.  <span data-ttu-id="1f3ea-147">对于“可执行文件”，输入 \<drive>:\Inetpub\SQLReplication\replisapi.dll。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-147">For **Executable**, enter **\<drive>:\Inetpub\SQLReplication\replisapi.dll**.</span></span>  
  
    7.  <span data-ttu-id="1f3ea-148">对于“名称”，请输入 `Replisapi`。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-148">For **Name**, enter `Replisapi`.</span></span>  
  
    8.  <span data-ttu-id="1f3ea-149">依次单击 **“请求限制”** 按钮、 **“访问”** 选项卡和 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-149">Click the **Request Restrictions** button, click the **Access** tab, and then click **Execute**.</span></span>  
  
    9. <span data-ttu-id="1f3ea-150">单击 **“确定”** 关闭 **“请求限制”** 对话框，然后再次单击 **“确定”** 关闭 **“添加模块映射”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-150">Click **OK** to close the **Request Restrictions** dialog box, and then click **OK** again to close the **Add Module Mapping** dialog box.</span></span> <span data-ttu-id="1f3ea-151">在系统提示您允许使用 ISAPI 扩展插件后，单击 **“是”** 以添加该扩展插件。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-151">When you are prompted to allow the ISAPI extension, click **Yes** to add the extension.</span></span>  
  
    10. <span data-ttu-id="1f3ea-152">检查 Replisapi.dll 是否列在 **“已启用”** 处理程序映射下。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-152">Verify that Replisapi.dll is listed under the **Enabled** handler mappings.</span></span> <span data-ttu-id="1f3ea-153">如果它列在 **“已禁用”** 列表中，请右键单击 Replisapi 条目，然后单击 **“编辑功能权限”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-153">If it is in the **Disabled** list, right-click the Replisapi entry and then click **Edit Feature Permissions**.</span></span> <span data-ttu-id="1f3ea-154">选中 **“执行”** 框，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-154">Check the **Execute** box, and then click **OK**.</span></span>  
  
## <a name="configuring-iis-authentication"></a><span data-ttu-id="1f3ea-155">配置 IIS 身份验证</span><span class="sxs-lookup"><span data-stu-id="1f3ea-155">Configuring IIS Authentication</span></span>  
 <span data-ttu-id="1f3ea-156">当订阅服务器计算机连接到 IIS 时，订阅服务器必须经过 IIS 的身份验证才能访问资源和过程。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-156">When subscriber computers connect to IIS, IIS must authenticate the subscribers before they can access resources and processes.</span></span> <span data-ttu-id="1f3ea-157">身份验证可以应用于整个网站或您创建的虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-157">Authentication can be applied to the whole Web site or to the virtual directory that you created.</span></span>  
  
 <span data-ttu-id="1f3ea-158">建议您使用带有 SSL 的基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-158">We recommend that you use Basic Authentication with SSL.</span></span> <span data-ttu-id="1f3ea-159">无论使用何种类型的身份验证，都需要 SSL。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-159">SSL is required, regardless of the type of authentication that is used.</span></span>  
  
 <span data-ttu-id="1f3ea-160">建议您使用带有 SSL 的基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-160">We recommend that you use Basic Authentication with SSL.</span></span> <span data-ttu-id="1f3ea-161">无论使用何种类型的身份验证，都需要 SSL。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-161">SSL is required, regardless of the type of authentication that is used.</span></span>  
  
#### <a name="to-configure-iis-authentication"></a><span data-ttu-id="1f3ea-162">配置 IIS 身份验证</span><span class="sxs-lookup"><span data-stu-id="1f3ea-162">To Configure IIS Authentication</span></span>  
  
1.  <span data-ttu-id="1f3ea-163">在 **“Internet 信息服务(IIS)管理器”** 中，单击 **“默认网站”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-163">In **Internet Information Services (IIS) Manager**, click **Default Web Site**.</span></span>  
  
2.  <span data-ttu-id="1f3ea-164">在中间窗格中，双击 **“身份验证”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-164">In the middle pane, double-click **Authentication**.</span></span>  
  
3.  <span data-ttu-id="1f3ea-165">右键单击“匿名身份验证”，然后选择“禁用”。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-165">Right-click Anonymous Authentication, and then choose Disable.</span></span>  
  
4.  <span data-ttu-id="1f3ea-166">右键单击“基本身份验证”，然后选择“启用”。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-166">Right-click Basic Authentication, and then choose Enable.</span></span>  
  
## <a name="configuring-secure-sockets-layer"></a><span data-ttu-id="1f3ea-167">配置安全套接字层</span><span class="sxs-lookup"><span data-stu-id="1f3ea-167">Configuring Secure Sockets Layer</span></span>  
 <span data-ttu-id="1f3ea-168">若要配置 SSL，请指定一个供正在运行 IIS 的计算机使用的证书。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-168">To configure SSL, specify a certificate to be used by the computer running IIS.</span></span> <span data-ttu-id="1f3ea-169">用于合并复制的 Web 同步支持使用服务器证书，但不支持使用客户端证书。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-169">Web synchronization for merge replication supports using server certificates, but not client certificates.</span></span> <span data-ttu-id="1f3ea-170">若要为部署配置 IIS，就必须首先从证书颁发机构 (CA) 获取证书。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-170">To configure IIS for deployment, you must first obtain a certificate from a certification authority (CA).</span></span> <span data-ttu-id="1f3ea-171">有关证书的详细信息，请参阅 IIS 文档。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-171">For more information about certificates, see the IIS documentation.</span></span>  
  
 <span data-ttu-id="1f3ea-172">安装证书后，必须使该证书与 Web 同步所用的网站相关联。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-172">After you install the certificate, you must associate the certificate with the Web site that is used by Web synchronization.</span></span> <span data-ttu-id="1f3ea-173">出于开发和测试目的，可以指定自签名证书。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-173">For development and testing, you can specify a self-signed certificate.</span></span> <span data-ttu-id="1f3ea-174">IIS 7 可以为您创建证书并在计算机上注册该证书。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-174">IIS 7 can create a certificate for you and register it on your computer.</span></span>  
  
 <span data-ttu-id="1f3ea-175">为生产环境进行部署与在此给出的过程之间的差异在于：在生产和产前测试环境中，您需要使用由 CA 颁发的证书而不是自签名证书。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-175">The difference between deploying for production and the procedures given here is that in production and pre-production testing, you would use a certificate issued by a CA instead of a self-signed certificate.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1f3ea-176">不建议对生产环境中的安装使用自签名证书，</span><span class="sxs-lookup"><span data-stu-id="1f3ea-176">A self-signed certificate is not recommended for a production installation.</span></span> <span data-ttu-id="1f3ea-177">因为自签名证书不安全。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-177">Self-signed certificates are not secure.</span></span> <span data-ttu-id="1f3ea-178">仅将自签名证书用于开发和测试目的。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-178">Use self-signed certificates for development and testing only.</span></span>  
  
 <span data-ttu-id="1f3ea-179">若要配置 SSL，您需要执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="1f3ea-179">To configure SSL, you will perform the following steps:</span></span>  
  
1.  <span data-ttu-id="1f3ea-180">配置网站要求 SSL 并忽略客户端证书。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-180">Configure the Web site to require SSL and ignore client certificates.</span></span>  
  
2.  <span data-ttu-id="1f3ea-181">从 CA 获得证书或创建自签名证书。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-181">Obtain a certificate from a CA or create a self-signed certificate.</span></span>  
  
3.  <span data-ttu-id="1f3ea-182">将证书绑定到复制网站。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-182">Bind the certificate to the replication Web site.</span></span>  
  
#### <a name="to-require-ssl-security-for-a-web-site"></a><span data-ttu-id="1f3ea-183">要求对网站设置 SSL 安全性</span><span class="sxs-lookup"><span data-stu-id="1f3ea-183">To require SSL security for a Web site</span></span>  
  
1.  <span data-ttu-id="1f3ea-184">在 **“Internet 信息服务(IIS)管理器”** 中，展开本地服务器节点，然后单击 **“默认网站”** （或是不同于默认网站的 Web 同步站点）。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-184">In **Internet Information Services (IIS) Manager**, expand the local server node, and then click the **Default Web Site** (or your Web synchronization site if it is different from the default Web site).</span></span>  
  
2.  <span data-ttu-id="1f3ea-185">在中间窗格中，双击 **“SSL 设置”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-185">In the middle pane, double-click **SSL Settings**.</span></span>  
  
3.  <span data-ttu-id="1f3ea-186">选中 **“要求 SSL”** 选项。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-186">Check the **Require SSL** option.</span></span> <span data-ttu-id="1f3ea-187">在 **“客户端证书”** 下，确保已选中 **“忽略”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-187">Under **Client certificates**, verify that the **Ignore** button is selected.</span></span>  
  
#### <a name="to-create-a-self-signed-certificate-for-testing"></a><span data-ttu-id="1f3ea-188">创建用于测试的自签名证书</span><span class="sxs-lookup"><span data-stu-id="1f3ea-188">To create a self-signed certificate for testing</span></span>  
  
1.  <span data-ttu-id="1f3ea-189">在 **“Internet 信息服务(IIS)管理器”** 中，单击本地服务器节点，然后在中央窗格中双击 **“服务器证书”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-189">In **Internet Information Services (IIS) Manager**, click the local server node, and then in the center pane, double-click on **Server Certificates**.</span></span>  
  
2.  <span data-ttu-id="1f3ea-190">在 **“操作”** 窗格中，单击 **“创建自签名证书”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-190">In the **Actions** pane, click **Create Self-Signed Certificate**.</span></span>  
  
3.  <span data-ttu-id="1f3ea-191">在 **“创建自签名证书”** 对话框中，输入证书名称，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-191">In the **Create Self-Signed Certificate** dialog box, enter a name for the certificate, and then click **OK**.</span></span>  
  
###### <a name="to-bind-a-certificate-to-a-web-site"></a><span data-ttu-id="1f3ea-192">将证书绑定到网站</span><span class="sxs-lookup"><span data-stu-id="1f3ea-192">To bind a certificate to a Web site</span></span>  
  
1.  <span data-ttu-id="1f3ea-193">在 **“连接”** 窗格中，单击 **“默认网站”** （或是不同于默认网站的 Web 同步站点）。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-193">In the **Connections** pane, click the **Default Web Site** (or your Web synchronization site, if it is different from the default Web site).</span></span>  
  
2.  <span data-ttu-id="1f3ea-194">在 **“操作”** 窗格中，依次单击 **“绑定”** 和 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-194">In the **Actions** pane, click **Bindings**, and then click **Add**.</span></span> <span data-ttu-id="1f3ea-195">**“添加网站绑定”** 对话框将出现。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-195">The **Add Site Binding** dialog box will appear.</span></span>  
  
3.  <span data-ttu-id="1f3ea-196">从 **“类型”** 下拉列表中，选择 **“https”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-196">From the **Type** drop-down list, select **https**.</span></span> <span data-ttu-id="1f3ea-197">保留 **“IP 地址”** 和 **“端口”** 的默认设置。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-197">Leave the default settings for **IP address** and **Port**.</span></span>  
  
4.  <span data-ttu-id="1f3ea-198">从 **“SSL 证书”** 下拉列表中，选择在“创建用于测试的自签名证书”中创建的证书，单击 **“确定”** ，然后单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-198">From the **SSL certificate** drop-down list, select the certificate created in "To create a self-signed certificate for testing," click **OK**, and then click **Close**.</span></span>  
  
###### <a name="to-test-the-certificate"></a><span data-ttu-id="1f3ea-199">测试证书</span><span class="sxs-lookup"><span data-stu-id="1f3ea-199">To test the certificate</span></span>  
  
1.  <span data-ttu-id="1f3ea-200">在 **在ternet 在formation Services (IIS) Manager**中，单击 **“默认网站”.**</span><span class="sxs-lookup"><span data-stu-id="1f3ea-200">In **Internet Information Services (IIS) Manager**, click **Default Web Site.**</span></span>  
  
2.  <span data-ttu-id="1f3ea-201">从“操作”窗格中，单击“浏览 \*:443(https)”。 </span><span class="sxs-lookup"><span data-stu-id="1f3ea-201">From the **Actions** pane, click **Browse \*:443(https)**.</span></span>  
  
3.  <span data-ttu-id="1f3ea-202">Internet Explorer 随即打开并显示一条消息“此网站的安全证书有问题。”。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-202">Internet Explorer will open and display a message that "There is a problem with this website's security certificate."</span></span> <span data-ttu-id="1f3ea-203">此警告向您表明关联的证书不是由认可的 CA 颁发的，因此可能不值得信任。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-203">This warning tells you that the associated certificate was not issued by a recognized CA and might not be trustworthy.</span></span> <span data-ttu-id="1f3ea-204">这个警告在意料之中，只需单击 **“继续浏览此网站(不推荐)”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-204">This is an expected warning, so click **Continue to this website (not recommended)**.</span></span>  
  
4.  <span data-ttu-id="1f3ea-205">如果系统提示您 **“连接至 localhost”** ，请输入用户名和密码继续操作。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-205">If you are prompted to **Connect to localhost**, enter a user name and password to proceed.</span></span> <span data-ttu-id="1f3ea-206">此时应能看到该网站的默认页面。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-206">You should see the default page for the Web site.</span></span>  
  
## <a name="setting-permissions-for-the-sql-server-replication-listener"></a><span data-ttu-id="1f3ea-207">设置 SQL Server 复制侦听器的权限</span><span class="sxs-lookup"><span data-stu-id="1f3ea-207">Setting Permissions for the SQL Server Replication Listener</span></span>  
 <span data-ttu-id="1f3ea-208">订阅服务器计算机连接到正在运行 IIS 的计算机时，将使用您在配置 IIS 时指定的身份验证类型对该订阅服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-208">When a subscriber computer connects to the computer running IIS, the subscriber is authenticated by using the type of authentication specified when you configured IIS.</span></span> <span data-ttu-id="1f3ea-209">IIS 对订阅服务器进行身份验证后，IIS 将检查该订阅服务器是否有权调用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-209">After IIS authenticates the subscriber, IIS checks whether the subscriber is authorized to invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="1f3ea-210">通过设置 replisapi.dll 权限可以控制能够调用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制的用户。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-210">You control the users that can invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication by setting permissions for replisapi.dll.</span></span> <span data-ttu-id="1f3ea-211">适当的权限配置对于防止在未经授权的情况下访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制而言很有必要。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-211">Properly configuring permissions is necessary to prevent unauthorized access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span>  
  
 <span data-ttu-id="1f3ea-212">若要配置运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制侦听器的帐户的最低权限，请完成以下过程。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-212">To configure the minimum permissions for the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener runs, complete the following procedure.</span></span> <span data-ttu-id="1f3ea-213">以下过程中的步骤适用于运行 IIS 7.0 的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Server 2008。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-213">The steps in the following procedure apply to [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Server 2008 running IIS 7.0.</span></span>  
  
 <span data-ttu-id="1f3ea-214">除了要执行下列步骤之外，请确保所需的登录名存在于发布访问列表 (PAL) 中。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-214">In addition to performing the following steps, make sure that the required logins are in the publication access list (PAL).</span></span> <span data-ttu-id="1f3ea-215">有关 PAL 的详细信息，请参阅[保护发布服务器](security/secure-the-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-215">For more information about the PAL, see [Secure the Publisher](security/secure-the-publisher.md).</span></span>  
  
 <span data-ttu-id="1f3ea-216">**重要提示** 本节中创建的帐户就是要在同步期间连接到发布服务器和分发服务器的帐户。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-216">**Important** The account created in this section is the account that will connect to the Publisher and Distributor during synchronization.</span></span> <span data-ttu-id="1f3ea-217">此帐户必须作为 SQL 登录帐户添加到分发服务器和发布服务器上。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-217">This account must be added as a SQL Login account on the distribution and publication server.</span></span>  
  
 <span data-ttu-id="1f3ea-218">用于 SQL Server 复制侦听器的帐户必须具有“合并代理安全性”主题中的“连接发布服务器或分发服务器”一节所述的权限。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-218">The account used for the SQL Server Replication Listener must have permissions as described in the Merge Agent Security topic, in the "Connect to the Publisher or Distributor" section.</span></span>  
  
 <span data-ttu-id="1f3ea-219">总之，该帐户必须：</span><span class="sxs-lookup"><span data-stu-id="1f3ea-219">In summary, the account must:</span></span>  
  
-   <span data-ttu-id="1f3ea-220">是发布访问列表 (PAL) 的成员。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-220">Be a member of the Publication Access List (PAL).</span></span>  
  
-   <span data-ttu-id="1f3ea-221">映射到与发布数据库中的某个用户关联的登录名。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-221">Be mapped to a login associated with a user in the publication database.</span></span>  
  
-   <span data-ttu-id="1f3ea-222">映射到与分发数据库中的某个用户关联的登录名。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-222">Be mapped to a login associated with a user in the distribution database.</span></span>  
  
-   <span data-ttu-id="1f3ea-223">对快照共享具有读取权限。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-223">Have Read permissions on the snapshot share.</span></span>  
  
#### <a name="to-configure-the-account-and-permissions"></a><span data-ttu-id="1f3ea-224">配置帐户和权限</span><span class="sxs-lookup"><span data-stu-id="1f3ea-224">To configure the account and permissions</span></span>  
  
1.  <span data-ttu-id="1f3ea-225">在运行 IIS 的计算机上创建一个本地帐户：</span><span class="sxs-lookup"><span data-stu-id="1f3ea-225">Create a local account on the computer running IIS:</span></span>  
  
    1.  <span data-ttu-id="1f3ea-226">打开 **“服务器管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-226">Open **Server Manager**.</span></span> <span data-ttu-id="1f3ea-227">从“开始”菜单，右键单击 **“计算机”** ，然后单击 **“管理”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-227">From the Start menu, right-click **Computer**, and then click **Manage**.</span></span>  
  
    2.  <span data-ttu-id="1f3ea-228">在 **“服务器管理器”** 中，展开 **“配置”** ，然后展开 **“本地用户和组”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-228">In **Server Manager**, expand **Configuration**, and then expand **Local Users and Groups**.</span></span>  
  
    3.  <span data-ttu-id="1f3ea-229">右键单击 **“用户”** ，然后单击 **“新建用户”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-229">Right-click **Users**, and then click **New User**.</span></span>  
  
    4.  <span data-ttu-id="1f3ea-230">输入用户名和强密码。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-230">Enter a user name and a strong password.</span></span> <span data-ttu-id="1f3ea-231">清除 **“用户在下次登录时必须更改密码”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-231">Clear **User must change password at next logon**.</span></span>  
  
    5.  <span data-ttu-id="1f3ea-232">单击 **“创建”** ，然后单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-232">Click **Create**, and then click **Close**.</span></span>  
  
2.  <span data-ttu-id="1f3ea-233">将帐户添加到 IIS_IUSRS 组：</span><span class="sxs-lookup"><span data-stu-id="1f3ea-233">Add the account to the IIS_IUSRS group:</span></span>  
  
    1.  <span data-ttu-id="1f3ea-234">在 **“服务器管理器”** 中，依次展开 **“配置”** 和 **“本地用户和组”** ，然后单击 **“组”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-234">In **Server Manager**, expand **Configuration**, expand **Local Users and Groups**, and then click **Groups**.</span></span>  
  
    2.  <span data-ttu-id="1f3ea-235">右键单击 **“IIS_IUSRS”** ，然后单击 **“添加到组”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-235">Right-click **IIS_IUSRS**, and then click **Add to Group**.</span></span>  
  
    3.  <span data-ttu-id="1f3ea-236">在 **“IIS_IUSRS 属性”** 对话框中，单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-236">In the **IIS_IUSRS Properties** dialog box, click **Add**.</span></span>  
  
    4.  <span data-ttu-id="1f3ea-237">在 **“选择用户、计算机或组”** 对话框中，添加在步骤 1 中创建的帐户。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-237">In the **Select Users, Computers, or Groups** dialog box, add the account created in step 1.</span></span>  
  
    5.  <span data-ttu-id="1f3ea-238">确保 **“从此位置”** 显示的是本地计算机（而不是域）的名称。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-238">Verify that **From this location** displays the name of the local computer (not a domain).</span></span> <span data-ttu-id="1f3ea-239">如果此字段不显示本地计算机名称，请单击 **“位置”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-239">If this field does not display the local computer name, click **Locations**.</span></span> <span data-ttu-id="1f3ea-240">在 **“位置”** 对话框中，选择本地计算机，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-240">In the **Locations** dialog box, select the local computer, and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="1f3ea-241">在“选择用户”  对话框和“IIS_IUSRS 属性”  对话框中，单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-241">In the **Select Users** dialog box and the **IIS_IUSRS Properties** dialog box, click**OK**.</span></span>  
  
3.  <span data-ttu-id="1f3ea-242">对包含 replisapi.dll 的文件夹授予最低帐户权限：</span><span class="sxs-lookup"><span data-stu-id="1f3ea-242">Grant minimum account permissions on the folder that contains replisapi.dll:</span></span>  
  
    1.  <span data-ttu-id="1f3ea-243">在 Windows Explorer 中，右键单击为 replisapi.dll 创建的文件夹，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-243">In Windows Explorer, right-click the folder that you created for replisapi.dll, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="1f3ea-244">在 **“安全性”** 选项卡上，单击 **“编辑”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-244">On the **Security** tab, click **Edit**.</span></span>  
  
    3.  <span data-ttu-id="1f3ea-245">在“\<foldername> 的权限”对话框中，单击“添加”以添加在步骤 1 中创建的帐户。 </span><span class="sxs-lookup"><span data-stu-id="1f3ea-245">In the **Permissions for \<foldername>** dialog box, click **Add** to add the account that you created in step 1.</span></span>  
  
    4.  <span data-ttu-id="1f3ea-246">确保 **“从此位置”** 显示的是本地计算机（而不是域）的名称。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-246">Verify that **From this location** displays the name of the local computer (not a domain).</span></span> <span data-ttu-id="1f3ea-247">如果此字段不显示本地计算机名称，请单击 **“位置”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-247">If this field does not display the local computer name, click **Locations**.</span></span> <span data-ttu-id="1f3ea-248">在 **“位置”** 对话框中，选择本地计算机，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-248">In the **Locations** dialog box, select the local computer, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="1f3ea-249">验证是否仅向该帐户授予了“读取”、“读取和执行”和“列出文件夹内容”权限。  </span><span class="sxs-lookup"><span data-stu-id="1f3ea-249">Verify that the account is granted only **Read**, **Read & Execute**, and **List Folder Contents** permissions.</span></span>  
  
    6.  <span data-ttu-id="1f3ea-250">选择所有不需要访问该目录的用户或组，然后依次单击 **“删除”** 和 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-250">Select any users or groups that do not require access to the directory, click **Remove**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="1f3ea-251">在 **“Internet 信息服务(IIS)管理器”** 中创建应用程序池：</span><span class="sxs-lookup"><span data-stu-id="1f3ea-251">Create an application pool in **Internet Information Services (IIS) Manager**:</span></span>  
  
    1.  <span data-ttu-id="1f3ea-252">在 **“Internet 信息服务(IIS)管理器”** 中的 **“连接”** 窗格中，展开本地服务器节点。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-252">In **Internet Information Services (IIS) Manager**, in the **Connections** pane, expand the local server node.</span></span>  
  
    2.  <span data-ttu-id="1f3ea-253">右键单击 **“应用程序池”** ，然后单击 **“添加应用程序池”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-253">Right-click **Application Pools**, and then click **Add Application Pool**.</span></span>  
  
    3.  <span data-ttu-id="1f3ea-254">输入应用程序池的名称，保留其余字段中的默认值，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-254">Enter a name for the application pool, leave the default values for the remaining fields, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1f3ea-255">如果您预计并发同步客户端超过两个，则最好创建 Web 园。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-255">If you anticipate having more than two concurrent synchronization clients, you might want to create a web garden.</span></span> <span data-ttu-id="1f3ea-256">有关详细信息，请参阅[配置 Web 同步](configure-web-synchronization.md)中的“创建 Web 园”。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-256">For more information, see "Creating a Web Garden" in [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
5.  <span data-ttu-id="1f3ea-257">将帐户与应用程序池关联：</span><span class="sxs-lookup"><span data-stu-id="1f3ea-257">Associate the account with the application pool:</span></span>  
  
    1.  <span data-ttu-id="1f3ea-258">在 **“Internet 信息服务(IIS)管理器”** 中，展开本地服务器节点，然后单击 **“应用程序池”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-258">In **Internet Information Services (IIS) Manager**, expand the local server node, and then click on **Application Pools**.</span></span>  
  
    2.  <span data-ttu-id="1f3ea-259">右键单击所创建的应用程序池，然后单击 **“设置应用程序池默认设置”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-259">Right-click the application pool that you created, and then click **Set Application Pool Defaults**.</span></span>  
  
    3.  <span data-ttu-id="1f3ea-260">在 **“应用程序池默认设置”** 对话框中，向下滚动到 **“处理模型”** 部分，然后单击 **“标识”** 字段。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-260">In the **Application Pool Defaults** dialog box, scroll down to the **Process Model** section, and then click the **Identity** field.</span></span>  
  
    4.  <span data-ttu-id="1f3ea-261">单击 **“标识”** 行右侧的省略号按钮。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-261">Click the ellipsis button on the right side of the **Identity** row.</span></span>  
  
    5.  <span data-ttu-id="1f3ea-262">单击 **“自定义帐户”** 单选按钮，然后单击 **“设置”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-262">Click the **Custom Account** radio button, and then click **Set**.</span></span>  
  
    6.  <span data-ttu-id="1f3ea-263">在 **“用户名”** 和 **“密码”** 字段中，输入在步骤 1 中创建的帐户和密码，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-263">In the **User name** and **Password** fields, enter the account and password that were created in step 1, and then click **OK**.</span></span>  
  
    7.  <span data-ttu-id="1f3ea-264">单击“确定”  关闭“应用程序池标识”  对话框，然后再次单击  “确定”关闭 “应用程序池默认设置”对话框。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-264">Click **OK** to close the **Application Pool Identity** dialog box, and then click **OK** again to close the **Application Pool Defaults**dialog box.</span></span>  
  
6.  <span data-ttu-id="1f3ea-265">将应用程序池与复制网站关联：</span><span class="sxs-lookup"><span data-stu-id="1f3ea-265">Associate the application pool with the replication Web site:</span></span>  
  
    1.  <span data-ttu-id="1f3ea-266">在 **“Internet 信息服务(IIS)管理器”** 中，展开本地服务器节点，然后单击 **“默认网站”** （或是不同于默认网站的 Web 同步站点）。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-266">In **Internet Information Services (IIS) Manager**, expand the local server node, and then click on the **Default Web Site** (or your Web synchronization site if it is different from the default Web site).</span></span>  
  
    2.  <span data-ttu-id="1f3ea-267">在 **“操作”** 窗格中的 **“管理网站”** 下，单击 **“高级设置”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-267">In the **Actions** pane, under **Manage Web Site**, click **Advanced Settings**.</span></span>  
  
    3.  <span data-ttu-id="1f3ea-268">在 **“高级设置”** 对话框中，单击 **“应用程序池”** 右侧的省略号按钮。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-268">In the **Advanced Settings** dialog box, click on the ellipsis button to the right of **Application Pool**.</span></span>  
  
    4.  <span data-ttu-id="1f3ea-269">从 **“应用程序池”** 下拉列表中，选择您在步骤 4 中创建的应用程序池，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-269">From the **Application pool** drop-down list, select the application pool you created in step 4, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="1f3ea-270">再次单击 **“确定”** ，关闭“高级设置”。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-270">Click **OK** again to close Advanced Settings.</span></span>  
  
## <a name="testing-the-connection-to-replisapidll"></a><span data-ttu-id="1f3ea-271">测试到 replisapi.dll 的连接</span><span class="sxs-lookup"><span data-stu-id="1f3ea-271">Testing the Connection to replisapi.dll</span></span>  
 <span data-ttu-id="1f3ea-272">在诊断模式下运行 Web 同步，以便测试与正在运行 IIS 的计算机的连接，并确保已正确安装安全套接字层 (SSL) 证书。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-272">Run Web synchronization in diagnostic mode to test the connection to the computer running IIS and to make sure that the Secure Sockets Layer (SSL) certificate is properly installed.</span></span> <span data-ttu-id="1f3ea-273">若要在诊断模式下运行 Web 同步，您必须是运行 IIS 的计算机中的管理员。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-273">To run Web synchronization in diagnostic mode, you must be an administrator on the computer running IIS.</span></span>  
  
#### <a name="to-test-the-connection-to-replisapidll"></a><span data-ttu-id="1f3ea-274">测试到 replisapi.dll 的连接</span><span class="sxs-lookup"><span data-stu-id="1f3ea-274">To test the connection to replisapi.dll</span></span>  
  
1.  <span data-ttu-id="1f3ea-275">确保订阅服务器中的局域网 (LAN) 设置正确：</span><span class="sxs-lookup"><span data-stu-id="1f3ea-275">Make sure that local area network (LAN) settings at the Subscriber are correct:</span></span>  
  
    1.  <span data-ttu-id="1f3ea-276">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 中的 **“工具”** 菜单中，单击 **“Internet 选项”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-276">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, on the **Tools** menu, click **Internet Options**.</span></span>  
  
    2.  <span data-ttu-id="1f3ea-277">在 **“连接”** 选项卡上，单击 **“局域网设置”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-277">On the **Connections** tab, click **LAN Settings**.</span></span>  
  
    3.  <span data-ttu-id="1f3ea-278">如果 LAN 中未使用代理服务器，请清除 **“自动检测设置”** 和 **“为 LAN 使用代理服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-278">If a proxy server is not used on the LAN, clear **Automatically Detect Settings** and **Use a proxy server for your LAN**.</span></span>  
  
    4.  <span data-ttu-id="1f3ea-279">如果使用了代理服务器，请单击 **“为 LAN 使用代理服务器”** 和 **“对于本地地址不使用代理服务器”** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-279">If a proxy server is used, click **Use a proxy server for your LAN** and **Bypass proxy server for local addresses**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="1f3ea-280">在订阅服务器上的 Internet Explorer 中，用向 replisapi.dll 的地址追加 `?diag` 的方法以诊断模式连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-280">At the Subscriber, in Internet Explorer, connect to the server in diagnostic mode by appending `?diag` to the address for the replisapi.dll.</span></span> <span data-ttu-id="1f3ea-281">例如：`https://server.domain.com/directory/replisapi.dll?diag`。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-281">For example: `https://server.domain.com/directory/replisapi.dll?diag`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1f3ea-282">在上例中， **server.domain.com** 应原样替换为在 IIS 管理器的 **“服务器证书”** 部分中列出的 **“颁发给”** 名称。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-282">In the example above, **server.domain.com** should be replaced with the exact **Issued To** name listed under the **Server Certificates** section in IIS Manager.</span></span>  
  
3.  <span data-ttu-id="1f3ea-283">如果 Windows 操作系统不能识别您为 IIS 指定的证书，则会显示 **“安全警报”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-283">If the certificate that you specified for IIS is not recognized by the Windows operating system, the **Security Alert** dialog box appears.</span></span> <span data-ttu-id="1f3ea-284">如果该证书是测试证书或是由 Windows 不能识别的证书颁发机构 (CA) 颁发的证书，便会显示该警报。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-284">This alert might occur because the certificate is a test certificate or the certificate was issued by a certification authority (CA) that Windows does not recognize.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1f3ea-285">如果未出现此对话框，请确保您所访问的服务器的证书已作为可信证书添加到订阅服务器的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-285">If this dialog box does not appear, make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="1f3ea-286">有关导出证书的详细信息，请参阅 IIS 文档。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-286">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
    1.  <span data-ttu-id="1f3ea-287">在 **“安全警报”** 对话框中，单击 **“查看证书”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-287">In the **Security Alert** dialog box, click **View Certificate**.</span></span>  
  
    2.  <span data-ttu-id="1f3ea-288">在 **“证书”** 对话框的 **“常规”** 选项卡上，单击 **“安装证书”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-288">In the **Certificate** dialog box, on the **General** tab, click **Install Certificate**.</span></span>  
  
    3.  <span data-ttu-id="1f3ea-289">完成证书导入向导，接受默认值。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-289">Complete the Certificate Import Wizard, accepting the defaults.</span></span>  
  
    4.  <span data-ttu-id="1f3ea-290">在 **“安全警告”** 对话框中，单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-290">In the **Security Warning** dialog box, click **Yes**.</span></span>  
  
    5.  <span data-ttu-id="1f3ea-291">在“证书导入向导”确认对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-291">In the Certificate Import Wizard confirmation dialog box, click **OK**.</span></span>  
  
    6.  <span data-ttu-id="1f3ea-292">关闭 **“证书”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-292">Close the **Certificate** dialog box.</span></span>  
  
    7.  <span data-ttu-id="1f3ea-293">在 **“安全警报”** 对话框中，单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-293">In the **Security Alert** dialog box, click **Yes**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1f3ea-294">为用户安装证书。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-294">Certificates are installed for users.</span></span> <span data-ttu-id="1f3ea-295">必须为要与 IIS 同步的每个用户执行该过程。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-295">This process must be performed for each user that will synchronize with IIS.</span></span>  
  
4.  <span data-ttu-id="1f3ea-296">在“连接到 \<ServerName>”对话框框中，指定合并代理将用于连接到 IIS 的登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-296">In the **Connect to \<ServerName>** dialog box, specify the login and password that the Merge Agent will use to connect to IIS.</span></span> <span data-ttu-id="1f3ea-297">在新建订阅向导中也要指定这些凭据。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-297">These credentials will also be specified in the New Subscription Wizard.</span></span>  
  
5.  <span data-ttu-id="1f3ea-298">在名为 **“SQL Websync 诊断信息”** 的 Internet Explorer 窗口中，验证该页中每个 **“状态”** 列的值是否都为 **SUCCESS**。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-298">In the Internet Explorer window called **SQL Websync diagnostic information**, verify that the value in each **Status** column on the page is **SUCCESS**.</span></span>  
  
6.  <span data-ttu-id="1f3ea-299">确保证书已正确安装到订阅服务器中：</span><span class="sxs-lookup"><span data-stu-id="1f3ea-299">Make sure that the certificate is installed correctly on the Subscriber:</span></span>  
  
    1.  <span data-ttu-id="1f3ea-300">关闭并重新打开 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-300">Close and then reopen Internet Explorer.</span></span>  
  
    2.  <span data-ttu-id="1f3ea-301">以诊断模式连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-301">Connect to the server in diagnostic mode.</span></span> <span data-ttu-id="1f3ea-302">如果证书安装正确，就不会显示 **“安全警报”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-302">If the certificate is installed properly, the **Security Alert** dialog box will not appear.</span></span> <span data-ttu-id="1f3ea-303">如果显示了该对话框，那么合并代理试图连接到正在运行 IIS 的计算机时就会失败。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-303">If the dialog box appears, the Merge Agent will fail when it tries to connect to the computer that is running IIS.</span></span> <span data-ttu-id="1f3ea-304">必须确保您所访问的服务器的证书已作为可信证书添加到订阅服务器的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-304">You must make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="1f3ea-305">有关导出证书的详细信息，请参阅 IIS 文档。</span><span class="sxs-lookup"><span data-stu-id="1f3ea-305">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f3ea-306">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f3ea-306">See Also</span></span>  
 <span data-ttu-id="1f3ea-307">[合并复制的 Web 同步](web-synchronization-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="1f3ea-307">[Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md) </span></span>  
 [<span data-ttu-id="1f3ea-308">配置 Web 同步</span><span class="sxs-lookup"><span data-stu-id="1f3ea-308">Configure Web Synchronization</span></span>](configure-web-synchronization.md)  
  
  
