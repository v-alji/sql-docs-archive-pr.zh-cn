---
title: 配置 IIS 以实现 Web 同步 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- IIS server configuration [SQL Server replication]
- websync.log
- Web synchronization, IIS servers
ms.assetid: d651186e-c9ca-4864-a444-2cd6943b8e35
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 523c4fc30151acd3ee4df21f2fdaa2187e702870
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580139"
---
# <a name="configure-iis-for-web-synchronization"></a><span data-ttu-id="e5394-102">配置 IIS 以实现 Web 同步</span><span class="sxs-lookup"><span data-stu-id="e5394-102">Configure IIS for Web Synchronization</span></span>
  <span data-ttu-id="e5394-103">本主题中的过程是为合并复制配置 Web 同步的第二个步骤。</span><span class="sxs-lookup"><span data-stu-id="e5394-103">The procedures in this topic make up the second step in configuring Web synchronization for merge replication.</span></span> <span data-ttu-id="e5394-104">应在为 Web 同步启用发布后执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="e5394-104">You perform this step after you enable a publication for Web synchronization.</span></span> <span data-ttu-id="e5394-105">有关配置过程的概述，请参阅 [“配置 Web 同步”](configure-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="e5394-105">For an overview of the configuration process, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span> <span data-ttu-id="e5394-106">完成本主题中的过程后，请继续执行第三个步骤“配置订阅以使用 Web 同步”。</span><span class="sxs-lookup"><span data-stu-id="e5394-106">After you complete the procedures in this topic, continue to the third step, configuring a subscription to use Web synchronization.</span></span> <span data-ttu-id="e5394-107">下列主题中将介绍第三个步骤：</span><span class="sxs-lookup"><span data-stu-id="e5394-107">This third step is described in the following topics:</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="e5394-108">：[如何配置订阅以使用 Web 同步 \(SQL Server Management Studio\)](https://msdn.microsoft.com/library/ms345214.aspx)</span><span class="sxs-lookup"><span data-stu-id="e5394-108">: [How to: Configure a Subscription to Use Web Synchronization \(SQL Server Management Studio\)](https://msdn.microsoft.com/library/ms345214.aspx)</span></span>  
  
-   <span data-ttu-id="e5394-109">复制 [!INCLUDE[tsql](../../includes/tsql-md.md)] 编程： [如何配置订阅以使用 Web 同步（复制 Transact-SQL 编程）](https://msdn.microsoft.com/library/ms345206.aspx)</span><span class="sxs-lookup"><span data-stu-id="e5394-109">Replication [!INCLUDE[tsql](../../includes/tsql-md.md)] programming: [How to: Configure a Subscription to Use Web Synchronization (Replication Transact-SQL Programming)](https://msdn.microsoft.com/library/ms345206.aspx)</span></span>  
  
-   <span data-ttu-id="e5394-110">RMO： [如何配置订阅以使用 Web 同步（RMO 编程）](https://msdn.microsoft.com/library/ms345207.aspx)</span><span class="sxs-lookup"><span data-stu-id="e5394-110">RMO: [How to: Configure a Subscription to Use Web Synchronization (RMO Programming)](https://msdn.microsoft.com/library/ms345207.aspx)</span></span>  
  
 <span data-ttu-id="e5394-111">Web 同步使用运行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) 的计算机，使请求订阅与合并发布同步。</span><span class="sxs-lookup"><span data-stu-id="e5394-111">Web synchronization uses a computer that is running [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) to synchronize pull subscriptions to merge publications.</span></span> <span data-ttu-id="e5394-112">支持 IIS 5.0、6.0 和 7.0 版。</span><span class="sxs-lookup"><span data-stu-id="e5394-112">IIS version 5.0, IIS version 6.0, and IIS version 7.0 are supported.</span></span> <span data-ttu-id="e5394-113">IIS 版本 7.0 不支持配置 Web 同步向导。</span><span class="sxs-lookup"><span data-stu-id="e5394-113">The Configure Web Synchronization Wizard is not supported on IIS version 7.0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e5394-114">请确保您的应用程序仅使用 [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] 或更高版本，并且 IIS 服务器上没有安装 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 的较早版本。</span><span class="sxs-lookup"><span data-stu-id="e5394-114">Make sure that your application uses only [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] or later versions, and that earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] are not installed on the IIS server.</span></span> <span data-ttu-id="e5394-115">较早版本的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 可能导致错误。</span><span class="sxs-lookup"><span data-stu-id="e5394-115">Earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] can cause errors.</span></span> <span data-ttu-id="e5394-116">这些错误包括以下内容：“Web 同步期间出现的消息的格式无效。</span><span class="sxs-lookup"><span data-stu-id="e5394-116">These include the following: "The format of a message during Web synchronization was invalid.</span></span> <span data-ttu-id="e5394-117">请确保在 Web 服务器上正确配置了复制组件”。</span><span class="sxs-lookup"><span data-stu-id="e5394-117">Ensure that replication components are properly configured at the Web server".</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="e5394-118">不要同时使用 WebSync 和备用快照文件夹位置。</span><span class="sxs-lookup"><span data-stu-id="e5394-118">Do not use both WebSync and alternate snapshot folder locations at the same time.</span></span>  
  
 <span data-ttu-id="e5394-119">若要使用 Web 同步，必须通过完成以下步骤来配置 IIS。</span><span class="sxs-lookup"><span data-stu-id="e5394-119">To use Web synchronization, you must configure IIS by completing the following steps.</span></span> <span data-ttu-id="e5394-120">本主题对每个步骤都进行了详细说明。</span><span class="sxs-lookup"><span data-stu-id="e5394-120">Each step is described in detail in this topic.</span></span>  
  
1.  <span data-ttu-id="e5394-121">配置安全套接字层 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="e5394-121">Configure Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="e5394-122">IIS 和所有订阅服务器之间的通信需要 SSL。</span><span class="sxs-lookup"><span data-stu-id="e5394-122">SSL is required for communication between IIS and all Subscribers.</span></span>  
  
2.  <span data-ttu-id="e5394-123">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用安装向导在运行 IIS 的计算机上安装连接组件 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e5394-123">Install [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connectivity components on the computer that is running IIS by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span> <span data-ttu-id="e5394-124">如果计划使用步骤 3 中提及的配置 Web 同步向导，那么还必须在运行 IIS 的计算机中安装 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e5394-124">If you plan to use the Configure Web Synchronization Wizard that is mentioned in step 3, you must also install [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] on the computer that is running IIS.</span></span>  
  
3.  <span data-ttu-id="e5394-125">为 Web 同步配置正在运行 IIS 的计算机。</span><span class="sxs-lookup"><span data-stu-id="e5394-125">Configure the computer that is running IIS for Web synchronization.</span></span> <span data-ttu-id="e5394-126">可以手动配置计算机，也可以使用配置 Web 同步向导。</span><span class="sxs-lookup"><span data-stu-id="e5394-126">You can configure the computer manually or use the Configure Web Synchronization Wizard.</span></span> <span data-ttu-id="e5394-127">建议您使用该向导。</span><span class="sxs-lookup"><span data-stu-id="e5394-127">We recommend that you use the wizard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5394-128">如果运行 IIS 的计算机运行的是 64 位版本的 Windows，则必须运行以下命令以确保该服务器为运行 Internet Server API (ISAPI) 应用程序进行了正确的配置。</span><span class="sxs-lookup"><span data-stu-id="e5394-128">If the computer that is running IIS is running on a 64-bit version of Windows, you must run following command to make sure that the server is properly configured to run Internet Server API (ISAPI) applications.</span></span> <span data-ttu-id="e5394-129">有关详细信息，请参阅 IIS 文档。</span><span class="sxs-lookup"><span data-stu-id="e5394-129">For more information, see the IIS documentation.</span></span>  
  
    ```  
    cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 1  
    ```  
  
4.  <span data-ttu-id="e5394-130">为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制侦听器设置相应权限。</span><span class="sxs-lookup"><span data-stu-id="e5394-130">Set the appropriate permissions for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener.</span></span>  
  
5.  <span data-ttu-id="e5394-131">在诊断模式下运行 Web 同步，以便测试与正在运行 IIS 的计算机的连接，并确保已正确安装 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="e5394-131">Run Web synchronization in diagnostic mode to test the connection to the computer that is running IIS and to make sure that the SSL certificate is properly installed.</span></span>  
  
## <a name="configuring-secure-sockets-layer"></a><span data-ttu-id="e5394-132">配置安全套接字层</span><span class="sxs-lookup"><span data-stu-id="e5394-132">Configuring Secure Sockets Layer</span></span>  
 <span data-ttu-id="e5394-133">若要配置 SSL，请指定一个供正在运行 IIS 的计算机使用的证书。</span><span class="sxs-lookup"><span data-stu-id="e5394-133">To configure SSL, specify a certificate for the computer that is running IIS to use.</span></span> <span data-ttu-id="e5394-134">用于合并复制的 Web 同步支持使用服务器证书，但不支持使用客户端证书。</span><span class="sxs-lookup"><span data-stu-id="e5394-134">Web synchronization for merge replication supports using server certificates but not client certificates.</span></span> <span data-ttu-id="e5394-135">若要为部署配置 IIS，就必须首先从证书颁发机构 (CA) 获取证书。</span><span class="sxs-lookup"><span data-stu-id="e5394-135">To configure IIS for deployment, you must first obtain a certificate from a certification authority (CA).</span></span> <span data-ttu-id="e5394-136">证书颁发机构是一个实体，负责确保属于用户、计算机或其他证书颁发机构的公共加密密钥的真实性并为其担保。</span><span class="sxs-lookup"><span data-stu-id="e5394-136">A certificate authority is an entity that is responsible for establishing and vouching for the authenticity of public encryption keys that belong to users, computers, or other certification authorities.</span></span> <span data-ttu-id="e5394-137">有关证书的详细信息，请参阅 IIS 文档。</span><span class="sxs-lookup"><span data-stu-id="e5394-137">For more information about certificates, see the IIS documentation.</span></span> <span data-ttu-id="e5394-138">安装证书后，必须使该证书与 Web 同步所用的网站相关联。</span><span class="sxs-lookup"><span data-stu-id="e5394-138">After you install the certificate, you must associate the certificate with the Web site that is used by Web synchronization.</span></span>  
  
#### <a name="to-specify-a-certificate-for-deployment"></a><span data-ttu-id="e5394-139">为部署指定证书</span><span class="sxs-lookup"><span data-stu-id="e5394-139">To specify a certificate for deployment</span></span>  
  
1.  <span data-ttu-id="e5394-140">以管理员身份登录到正在运行 IIS 的计算机。</span><span class="sxs-lookup"><span data-stu-id="e5394-140">Log on to the computer that is running IIS as an administrator.</span></span>  
  
2.  <span data-ttu-id="e5394-141">启动 **“Internet Information Services(IIS)管理器”**：</span><span class="sxs-lookup"><span data-stu-id="e5394-141">Start **Internet Information Services (IIS) Manager**:</span></span>  
  
    1.  <span data-ttu-id="e5394-142">单击 **“启动”** ，再单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-142">Click **Start**, and then click **Run**.</span></span>  
  
    2.  <span data-ttu-id="e5394-143">在 "**打开**" 框中键入 `inetmgr` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="e5394-143">In the **Open** box, type `inetmgr`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e5394-144">运行 IIS 证书向导：</span><span class="sxs-lookup"><span data-stu-id="e5394-144">Run the IIS Certificate Wizard:</span></span>  
  
    1.  <span data-ttu-id="e5394-145">在 **“Internet 信息服务(IIS)管理器”** 中，展开 **“本地计算机”** 节点，然后展开 **“Web 站点”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e5394-145">In **Internet Information Services (IIS) Manager**, expand the **local computer** node, and then expand the **Web Sites** folder.</span></span>  
  
    2.  <span data-ttu-id="e5394-146">右键单击 **“默认的 Web 站点”**，然后单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-146">Right-click **Default Web Site**, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="e5394-147">在 **“默认的 Web 站点属性”** 对话框中的 **“目录安全性”** 选项卡上，单击 **“服务器证书”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-147">In the **Default Web Site Properties** dialog box, on the **Directory Security** tab, click **Server Certificate**.</span></span>  
  
    4.  <span data-ttu-id="e5394-148">完成 Web 服务器证书向导。</span><span class="sxs-lookup"><span data-stu-id="e5394-148">Complete the Web Server Certificate Wizard.</span></span>  
  
4.  <span data-ttu-id="e5394-149">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="e5394-149">Click **OK**.</span></span>  
  
 <span data-ttu-id="e5394-150">如果无法从 CA 获得服务器证书，则可指定进行测试所需的证书。</span><span class="sxs-lookup"><span data-stu-id="e5394-150">If you cannot obtain a server certificate from a CA, you can specify a certificate for testing.</span></span> <span data-ttu-id="e5394-151">若要为测试配置 IIS 6.0，请使用 SelfSSL 实用工具安装证书。</span><span class="sxs-lookup"><span data-stu-id="e5394-151">To configure IIS 6.0 for testing, install a certificate by using the SelfSSL utility.</span></span> <span data-ttu-id="e5394-152">可从 IIS 6.0 资源工具包中获得该实用工具。</span><span class="sxs-lookup"><span data-stu-id="e5394-152">This utility is available in the IIS 6.0 Resource Kit.</span></span> <span data-ttu-id="e5394-153">您可以从 [Microsoft 下载中心](https://www.microsoft.com/download/details.aspx?id=5135)下载这些工具。</span><span class="sxs-lookup"><span data-stu-id="e5394-153">You can download the tools from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=5135).</span></span> <span data-ttu-id="e5394-154">对于 IIS 5.0，请转到 [Microsoft 帮助和支持](https://go.microsoft.com/fwlink/?LinkId=46229)。</span><span class="sxs-lookup"><span data-stu-id="e5394-154">For IIS 5.0, go to [Microsoft Help and Support](https://go.microsoft.com/fwlink/?LinkId=46229).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5394-155">证书必须与网站相关联，该网站才能使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="e5394-155">A certificate must be associated with a Web site before that Web site can use SSL.</span></span> <span data-ttu-id="e5394-156">SelfSSL 自动使证书与默认网站相关联。</span><span class="sxs-lookup"><span data-stu-id="e5394-156">SelfSSL automatically associates the certificate with the default Web site.</span></span> <span data-ttu-id="e5394-157">如果已有证书或以后从 CA 安装证书，则必须明确地使该证书与 Web 同步所使用的网站相关联。</span><span class="sxs-lookup"><span data-stu-id="e5394-157">If you already have a certificate or later install a certificate from a CA, you must explicitly associate that certificate with the Web site that is used by Web synchronization.</span></span> <span data-ttu-id="e5394-158">确保只有一个与用于同步订阅的网站相关联的证书。</span><span class="sxs-lookup"><span data-stu-id="e5394-158">Make sure there is only one certificate associated with the Web site that is used to synchronize subscriptions.</span></span> <span data-ttu-id="e5394-159">如果存在多个证书，订阅服务器将使用第一个可用网站。</span><span class="sxs-lookup"><span data-stu-id="e5394-159">If there are multiple certificates, the Subscriber will use the first available Web site.</span></span>  
  
#### <a name="to-specify-a-certificate-for-testing-in-iis-60"></a><span data-ttu-id="e5394-160">指定在 IIS 6.0 中进行测试所需的证书</span><span class="sxs-lookup"><span data-stu-id="e5394-160">To specify a certificate for testing in IIS 6.0</span></span>  
  
1.  <span data-ttu-id="e5394-161">以管理员身份登录到正在运行 IIS 的计算机。</span><span class="sxs-lookup"><span data-stu-id="e5394-161">Log on to the computer that is running IIS as an administrator.</span></span>  
  
2.  <span data-ttu-id="e5394-162">下载并安装 SelfSSL。</span><span class="sxs-lookup"><span data-stu-id="e5394-162">Download and install SelfSSL.</span></span> <span data-ttu-id="e5394-163">默认情况下，应用程序安装到 \<*drive*> ： \Program Files\IIS resources\selfssl。</span><span class="sxs-lookup"><span data-stu-id="e5394-163">By default, the application is installed to \<*drive*>:\Program Files\IIS Resources\SelfSSL.</span></span> <span data-ttu-id="e5394-164">应用程序和文档快捷方式复制到 \<*drive*> ： \Documents 和 Settings\All Settings\all users\start Menu\Programs\IIS resources\selfssl。</span><span class="sxs-lookup"><span data-stu-id="e5394-164">Application and documentation shortcuts are copied to \<*drive*>:\Documents and Settings\All Users\Start Menu\Programs\IIS Resources\SelfSSL.</span></span>  
  
3.  <span data-ttu-id="e5394-165">运行 SelfSSL：</span><span class="sxs-lookup"><span data-stu-id="e5394-165">Run SelfSSL:</span></span>  
  
    -   <span data-ttu-id="e5394-166">若要用各参数的默认值运行 SelfSSL，请找到应用程序的安装目录，然后双击 SelfSSL.exe。</span><span class="sxs-lookup"><span data-stu-id="e5394-166">To run SelfSSL with default values for all parameters, locate the installation directory for the application, and then double-click SelfSSL.exe.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="e5394-167">默认情况下，SelfSSL 安装的证书有效期为七天。</span><span class="sxs-lookup"><span data-stu-id="e5394-167">By default, the certificate that is installed by SelfSSL is valid for seven days.</span></span>  
  
    -   <span data-ttu-id="e5394-168">若要指定一个或多个参数的值，请单击 **“开始”**，然后单击 **“运行”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-168">To specify values for one or more parameters: click **Start**, and then click **Run**.</span></span> <span data-ttu-id="e5394-169">在 "**打开**" 框中，输入 `cmd` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="e5394-169">In the **Open** box, enter `cmd`, and then click **OK**.</span></span> <span data-ttu-id="e5394-170">找到 SelfSSL 安装目录，键入 `SelfSSL`，然后指定一个或多个参数的值。</span><span class="sxs-lookup"><span data-stu-id="e5394-170">Locate the SelfSSL installation directory, type `SelfSSL`, and then specify values for one or more parameters.</span></span> <span data-ttu-id="e5394-171">若要获得参数列表，请键入 `SelfSSL -?`。</span><span class="sxs-lookup"><span data-stu-id="e5394-171">For a list of parameters, type `SelfSSL -?`.</span></span>  
  
## <a name="installing-connectivity-components-and-sql-server-management-studio"></a><span data-ttu-id="e5394-172">安装连接组件和 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e5394-172">Installing Connectivity Components and SQL Server Management Studio</span></span>  
  
#### <a name="to-install-sql-server-connectivity-components-and-sql-server-management-studio"></a><span data-ttu-id="e5394-173">安装 SQL Server 连接组件和 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e5394-173">To install SQL Server connectivity components and SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="e5394-174">以管理员身份登录到正在运行 IIS 的计算机。</span><span class="sxs-lookup"><span data-stu-id="e5394-174">Log on as an administrator to the computer that is running IIS.</span></span>  
  
2.  <span data-ttu-id="e5394-175">从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 安装磁盘中启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导。</span><span class="sxs-lookup"><span data-stu-id="e5394-175">From the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] installation disk, start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span> <span data-ttu-id="e5394-176">有关使用此向导的详细信息，请参阅安装[向导中的安装 SQL Server 2014 &#40;安装&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="e5394-176">For more information about using this wizard, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
3.  <span data-ttu-id="e5394-177">在 **“功能选择”** 页中，选择 **“客户端工具连接”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-177">On the **Feature Selection** page, select **Client Tools Connectivity**.</span></span>  
  
4.  <span data-ttu-id="e5394-178">如果计划使用配置 Web 同步向导，请选择 **“管理工具 – 基本”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-178">If you plan to use the Configure Web Synchronization Wizard, select **Management Tools - Basic**.</span></span>  
  
5.  <span data-ttu-id="e5394-179">完成该向导，然后重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="e5394-179">Complete the wizard, and then restart the computer.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5394-180">可以安装其他组件，但 Web 同步仅需要连接组件。</span><span class="sxs-lookup"><span data-stu-id="e5394-180">You can install additional components, but only the connectivity components are required for Web synchronization.</span></span>  
  
## <a name="configuring-the-computer-that-is-running-iis-by-using-the-configure-web-synchronization-wizard"></a><span data-ttu-id="e5394-181">使用配置 Web 同步向导配置正在运行 IIS 的计算机</span><span class="sxs-lookup"><span data-stu-id="e5394-181">Configuring the Computer That Is Running IIS by Using the Configure Web Synchronization Wizard</span></span>  
 <span data-ttu-id="e5394-182">使用配置 Web 同步向导或以手动方式配置 IIS 服务器。</span><span class="sxs-lookup"><span data-stu-id="e5394-182">Configure the IIS server by using the Configure Web Synchronization Wizard or manually.</span></span> <span data-ttu-id="e5394-183">我们建议您使用向导，但同时在下一部分中提供手动配置的步骤。</span><span class="sxs-lookup"><span data-stu-id="e5394-183">We recommend using the wizard, but we also provide steps for manual configuration in the next section.</span></span> <span data-ttu-id="e5394-184">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 随附的 Web 同步向导仅适用于在运行 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]的发布服务器上或在已经升级到 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]的发布服务器上创建的发布。</span><span class="sxs-lookup"><span data-stu-id="e5394-184">The Web Synchronization Wizard that is available with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] can be used only for publications that were created on a Publisher that is running [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], or a Publisher that was upgraded to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span> <span data-ttu-id="e5394-185">而不适用于 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]上的发布。</span><span class="sxs-lookup"><span data-stu-id="e5394-185">The wizard cannot be used for publications on [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="e5394-186">该向导适用于 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本和 [!INCLUDE[ssEWnoversion](../../includes/ssewnoversion-md.md)] 3.0 及更高版本上的订阅。</span><span class="sxs-lookup"><span data-stu-id="e5394-186">The wizard can be used with subscriptions on [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions, and [!INCLUDE[ssEWnoversion](../../includes/ssewnoversion-md.md)] 3.0 and later versions.</span></span>  
  
 <span data-ttu-id="e5394-187">该配置有以下特征：</span><span class="sxs-lookup"><span data-stu-id="e5394-187">The configuration has the following characteristics:</span></span>  
  
-   <span data-ttu-id="e5394-188">使用 IIS 中的默认网站。</span><span class="sxs-lookup"><span data-stu-id="e5394-188">Uses the default Web site in IIS.</span></span> <span data-ttu-id="e5394-189">但也可以使用其他网站。</span><span class="sxs-lookup"><span data-stu-id="e5394-189">However, you can use another Web site.</span></span> <span data-ttu-id="e5394-190">有关如何创建网站的详细信息，请参阅 IIS 文档。</span><span class="sxs-lookup"><span data-stu-id="e5394-190">For more information about how to create Web sites, see the IIS documentation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5394-191">通过指定的网站可访问 Web 同步使用的组件。</span><span class="sxs-lookup"><span data-stu-id="e5394-191">The Web site that you specify provides access to the components that are used by Web synchronization.</span></span> <span data-ttu-id="e5394-192">它不会提供对其他数据或网页的访问，除非将其如此配置。</span><span class="sxs-lookup"><span data-stu-id="e5394-192">The Web site does not provide access to other data or Web pages unless you configure the site to do so.</span></span>  
  
-   <span data-ttu-id="e5394-193">创建虚拟目录及其关联的别名。</span><span class="sxs-lookup"><span data-stu-id="e5394-193">Creates a virtual directory and its associated alias.</span></span> <span data-ttu-id="e5394-194">访问 Web 同步组件时使用该别名。</span><span class="sxs-lookup"><span data-stu-id="e5394-194">The alias is used when accessing the Web synchronization components.</span></span> <span data-ttu-id="e5394-195">例如，如果 IIS 地址是 `https://*server.domain.com*`，而你指定了别名“websync1”，那么访问 replisapi.dll 组件的地址就是 `https://*server.domain.com*/websync1/replisapi.dll`。</span><span class="sxs-lookup"><span data-stu-id="e5394-195">For example, if the IIS address is `https://*server.domain.com*` and you specify an alias of 'websync1', the address to access the replisapi.dll component is `https://*server.domain.com*/websync1/replisapi.dll`.</span></span>  
  
-   <span data-ttu-id="e5394-196">使用基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="e5394-196">Uses Basic Authentication.</span></span> <span data-ttu-id="e5394-197">建议使用基本身份验证，因为它不需要 Kerberos 委托就可以在单独的计算机上运行 IIS 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发布服务器/分发服务器（建议配置）。</span><span class="sxs-lookup"><span data-stu-id="e5394-197">We recommend using Basic Authentication because Basic Authentication enables you to run IIS and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher/Distributor on separate computers (the recommended configuration) without requiring Kerberos delegation.</span></span> <span data-ttu-id="e5394-198">将 SSL 与基本身份验证一起使用可以确保登录名、密码和所有数据都在传输中加密。</span><span class="sxs-lookup"><span data-stu-id="e5394-198">Using SSL with Basic Authentication makes sure that logins, passwords, and all data are encrypted in transit.</span></span> <span data-ttu-id="e5394-199">无论使用何种身份验证类型，都需要 (SSL ) 。有关 Web 同步的最佳实践的详细信息，请参阅[配置 Web 同步](configure-web-synchronization.md)中的 "web 同步的最佳安全方案" 一节。</span><span class="sxs-lookup"><span data-stu-id="e5394-199">(SSL is required, regardless of the type of authentication that is used.) For more information about best practices for Web synchronization, see the section "Security Best Practices for Web Synchronization" in [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
#### <a name="to-configure-the-computer-that-is-running-iis-by-using-the-configure-web-synchronization-wizard"></a><span data-ttu-id="e5394-200">使用配置 Web 同步向导配置正在运行 IIS 的计算机</span><span class="sxs-lookup"><span data-stu-id="e5394-200">To configure the computer that is running IIS by using the Configure Web Synchronization Wizard</span></span>  
  
1.  <span data-ttu-id="e5394-201">在正在运行 IIS 的计算机上，启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e5394-201">On the computer that is running IIS, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="e5394-202">连接至发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="e5394-202">Connect to the Publisher, and then expand the server node.</span></span>  
  
3.  <span data-ttu-id="e5394-203">展开 **“本地发布”** 文件夹，右键单击发布，然后单击 **“配置 Web 同步”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-203">Expand the **Local Publications** folder, right-click the publication, and then click **Configure Web Synchronization**.</span></span>  
  
4.  <span data-ttu-id="e5394-204">在配置 Web 同步向导中的 **“订阅服务器类型”** 页中，选择 **SQL Server**。</span><span class="sxs-lookup"><span data-stu-id="e5394-204">In the Configure Web Synchronization Wizard, on the **Subscriber Type** page, select **SQL Server**.</span></span>  
  
5.  <span data-ttu-id="e5394-205">在 **“Web 服务器”** 页中：</span><span class="sxs-lookup"><span data-stu-id="e5394-205">On the **Web Server** page:</span></span>  
  
    1.  <span data-ttu-id="e5394-206">选择将同步订阅的 IIS 实例。</span><span class="sxs-lookup"><span data-stu-id="e5394-206">Select the instance of IIS that will synchronize subscriptions.</span></span>  
  
    2.  <span data-ttu-id="e5394-207">选择 **“创建新的虚拟目录”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-207">Select **Create a new virtual directory**.</span></span>  
  
    3.  <span data-ttu-id="e5394-208">在该页的底部窗格中，展开 IIS 实例，展开 **“网站”**，然后单击 **“默认网站”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-208">In the lower pane of the page, expand the instance of IIS, expand **Web Sites**, and then click **Default Web Site**.</span></span>  
  
6.  <span data-ttu-id="e5394-209">在 **“虚拟目录信息”** 页中：</span><span class="sxs-lookup"><span data-stu-id="e5394-209">On the **Virtual Directory Information** page:</span></span>  
  
    1.  <span data-ttu-id="e5394-210">在 **“别名”** 框中输入虚拟目录别名。</span><span class="sxs-lookup"><span data-stu-id="e5394-210">In the **Alias** box, enter an alias for the virtual directory.</span></span>  
  
    2.  <span data-ttu-id="e5394-211">在 **“路径”** 框中输入虚拟目录的路径。</span><span class="sxs-lookup"><span data-stu-id="e5394-211">In the **Path** box, enter a path of the virtual directory.</span></span> <span data-ttu-id="e5394-212">例如，如果在 `websync1` "**别名**" 框中输入，则在 `C:\Inetpub\wwwroot\websync1` "**路径**" 框中输入。</span><span class="sxs-lookup"><span data-stu-id="e5394-212">For example, if you entered `websync1` in the **Alias** box, enter `C:\Inetpub\wwwroot\websync1` in the **Path** box.</span></span> <span data-ttu-id="e5394-213">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e5394-213">Click **Next**.</span></span>  
  
    3.  <span data-ttu-id="e5394-214">在两个对话框中，单击 **“是”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-214">On both dialog boxes, click **Yes**.</span></span> <span data-ttu-id="e5394-215">这指定您要创建一个新文件夹并复制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Internet Server API (ISAPI) DLL。</span><span class="sxs-lookup"><span data-stu-id="e5394-215">This specifies that you want to create a new folder and that you want to copy the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Internet Server API (ISAPI) DLL.</span></span> <span data-ttu-id="e5394-216">.</span><span class="sxs-lookup"><span data-stu-id="e5394-216">.</span></span>  
  
7.  <span data-ttu-id="e5394-217">在 **“经过身份验证的访问”** 页中：</span><span class="sxs-lookup"><span data-stu-id="e5394-217">On the **Authenticated Access** page:</span></span>  
  
    1.  <span data-ttu-id="e5394-218">确保已清除 **“集成 Windows 身份验证”** 和 **“Windows 域服务器的摘要式身份验证”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-218">Make sure that **Integrated Windows authentication** and **Digest authentication for Windows domain servers** are cleared.</span></span>  
  
    2.  <span data-ttu-id="e5394-219">选择 **“基本身份验证”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-219">Select **Basic Authentication**.</span></span>  
  
    3.  <span data-ttu-id="e5394-220">在 **“默认域”** 和 **“领域”** 框中，输入正在运行 IIS 的计算机的域。</span><span class="sxs-lookup"><span data-stu-id="e5394-220">In the **Default Domain** and **Realm** boxes, enter the domain of the computer that is running IIS.</span></span>  
  
8.  <span data-ttu-id="e5394-221">在 **“目录访问”** 页中：</span><span class="sxs-lookup"><span data-stu-id="e5394-221">On the **Directory Access** page:</span></span>  
  
    1.  <span data-ttu-id="e5394-222">单击 **“添加”**，然后在 **“选择用户或组”** 对话框中添加订阅服务器在与 IIS 建立连接时将要使用的帐户。</span><span class="sxs-lookup"><span data-stu-id="e5394-222">Click **Add**, and then in the **Select Users or Groups** dialog box, add the accounts under which Subscribers will make connections to IIS.</span></span> <span data-ttu-id="e5394-223">你将在新建订阅向导的“Web 服务器信息”页中指定这些帐户或作为 [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)*@internet_login* 参数的值指定它们。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e5394-223">These are the accounts that you will specify on the **Web Server Information** page of the New Subscription Wizard or as the value for the [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)*@internet_login* parameter.</span></span>  
  
9. <span data-ttu-id="e5394-224">在 **“快照共享访问”** 页中，输入快照共享。</span><span class="sxs-lookup"><span data-stu-id="e5394-224">On the **Snapshot Share Access** page, enter the snapshot share.</span></span> <span data-ttu-id="e5394-225">在这个共享上设置相应权限，以使订阅服务器能够访问快照文件。</span><span class="sxs-lookup"><span data-stu-id="e5394-225">The appropriate permissions are set on this share so that Subscribers can access the snapshot files.</span></span> <span data-ttu-id="e5394-226">有关此共享的权限的详细信息，请参阅[保护快照文件](security/secure-the-snapshot-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="e5394-226">For more information about permissions for the share, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span>  
  
10. <span data-ttu-id="e5394-227">在 **“完成向导”** 页中，单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-227">On the **Completing the Wizard** page, click **Finish**.</span></span>  
  
     <span data-ttu-id="e5394-228">如果出现故障，例如尝试配置正在运行 IIS 的远程计算机时出现网络错误，就会回滚所有完成的操作并取消所有剩余操作。</span><span class="sxs-lookup"><span data-stu-id="e5394-228">If a failure occurs, such as a network error while trying to configure a remote computer that is running IIS, all completed actions are rolled back and all remaining actions are canceled.</span></span> <span data-ttu-id="e5394-229">如果无法回滚某项已完成的操作，则向导末页中的状态会显示 **“成功”** ，而已完成的操作会保持提交状态。</span><span class="sxs-lookup"><span data-stu-id="e5394-229">If a completed action cannot be rolled back, the status in the final page of the wizard displays **Success** and the completed actions remain committed.</span></span>  
  
11. <span data-ttu-id="e5394-230">如果运行 IIS 的计算机是在 64 位版本的 Windows 上运行，则必须将 replisapi.dll 复制到相应目录：</span><span class="sxs-lookup"><span data-stu-id="e5394-230">If the computer that is running IIS is running on a 64-bit version of Windows, replisapi.dll must be copied to the appropriate directory:</span></span>  
  
    1.  <span data-ttu-id="e5394-231">单击 **“启动”** ，再单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-231">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="e5394-232">在 "**打开**" 框中，输入 `iisreset` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="e5394-232">In the **Open** box, enter `iisreset`, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="e5394-233">IIS 停止并重新启动后，将 replisapi.dll 从 [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM\replisapi 复制到步骤 6b 中指定的目录。</span><span class="sxs-lookup"><span data-stu-id="e5394-233">After IIS stops and restarts, copy replisapi.dll from [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM\replisapi to the directory that is specified in step 6b.</span></span>  
  
    3.  <span data-ttu-id="e5394-234">单击 **“启动”** ，再单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-234">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="e5394-235">在 "**打开**" 框中，输入 `cmd` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="e5394-235">In the **Open** box, enter `cmd`, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="e5394-236">在步骤 6b 指定的目录中，执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="e5394-236">In the directory that you specified in step 6b, execute the following command:</span></span>  
  
         `regsvr32 replisapi.dll`  
  
## <a name="manually-configuring-the-computer-that-is-running-iis"></a><span data-ttu-id="e5394-237">手动配置正在运行 IIS 的计算机</span><span class="sxs-lookup"><span data-stu-id="e5394-237">Manually Configuring the Computer That Is Running IIS</span></span>  
 <span data-ttu-id="e5394-238">若要手动配置正在运行 IIS 的计算机，必须安装和配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制侦听器，然后为将连接到 IIS 的订阅服务器配置授权。</span><span class="sxs-lookup"><span data-stu-id="e5394-238">To configure the computer that is running IIS manually, you must install and configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener, and then configure authorization for Subscribers that will connect to IIS.</span></span>  
  
#### <a name="to-install-and-configure-the-sql-server-replication-listener"></a><span data-ttu-id="e5394-239">安装和配置 SQL Server 复制侦听器</span><span class="sxs-lookup"><span data-stu-id="e5394-239">To install and configure the SQL Server Replication Listener</span></span>  
  
1.  <span data-ttu-id="e5394-240">在正在运行 IIS 的计算机上创建一个文件目录，用来存放 replisapi.dll。</span><span class="sxs-lookup"><span data-stu-id="e5394-240">Create a file directory on the computer that is running IIS to contain replisapi.dll.</span></span> <span data-ttu-id="e5394-241">可在任意位置创建该目录，但建议将该目录创建在 \<*drive*>:\Inetpub 目录下。</span><span class="sxs-lookup"><span data-stu-id="e5394-241">You can create the directory wherever you want, but we recommend that you create the directory under the \<*drive*>:\Inetpub directory.</span></span> <span data-ttu-id="e5394-242">例如，可以创建目录 \<*drive*>:\Inetpub\SQLReplication\\。</span><span class="sxs-lookup"><span data-stu-id="e5394-242">For example, create the directory \<*drive*>:\Inetpub\SQLReplication\\.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e5394-243">极力建议在 NTFS 文件系统分区中（而不是 FAT 文件系统中）创建此目录。</span><span class="sxs-lookup"><span data-stu-id="e5394-243">We strongly recommend that you create this directory on an NTFS file system partition instead of a FAT file system.</span></span> <span data-ttu-id="e5394-244">使用 NTFS 文件系统时，可以用 NTFS 文件系统权限来精确控制可以访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制的用户。</span><span class="sxs-lookup"><span data-stu-id="e5394-244">When you use the NTFS file system, you can use NTFS file system permissions to control precisely the users that can access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span>  
  
2.  <span data-ttu-id="e5394-245">将 replisapi.dll 从目录 [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ 复制到在步骤 1 中创建的文件目录。</span><span class="sxs-lookup"><span data-stu-id="e5394-245">Copy replisapi.dll from the directory [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ to the file directory that you created in step 1.</span></span>  
  
3.  <span data-ttu-id="e5394-246">注册 replisapi.dll：</span><span class="sxs-lookup"><span data-stu-id="e5394-246">Register replisapi.dll:</span></span>  
  
    1.  <span data-ttu-id="e5394-247">单击 **“启动”** ，再单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-247">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="e5394-248">在 "**打开**" 框中，输入 `cmd` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="e5394-248">In the **Open** box, enter `cmd`, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="e5394-249">在步骤 1 创建的目录中，执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="e5394-249">In the directory that you created in step 1, execute the following command:</span></span>  
  
         `regsvr32 replisapi.dll`  
  
4.  <span data-ttu-id="e5394-250">创建一个用于复制的新网站，或使用现有网站。</span><span class="sxs-lookup"><span data-stu-id="e5394-250">Create a new Web site for replication, or use an existing site.</span></span> <span data-ttu-id="e5394-251">复制组件将在同步过程中访问该网站。</span><span class="sxs-lookup"><span data-stu-id="e5394-251">The Web site will be accessed by replication components during synchronization.</span></span> <span data-ttu-id="e5394-252">有关如何创建网站的详细信息，请参阅 IIS 文档。</span><span class="sxs-lookup"><span data-stu-id="e5394-252">For more information about how to create Web sites, see the IIS documentation.</span></span>  
  
5.  <span data-ttu-id="e5394-253">在 IIS 上创建一个虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="e5394-253">Create a virtual directory in IIS.</span></span> <span data-ttu-id="e5394-254">虚拟目录应在步骤 4 所创建的网站下创建，并将其映射到步骤 1 中创建的目录。</span><span class="sxs-lookup"><span data-stu-id="e5394-254">The virtual directory should be created under the Web site that was created in step 4, and should be mapped to the directory that was created in step 1.</span></span> <span data-ttu-id="e5394-255">有关如何创建虚拟目录的详细信息，请参阅 IIS 文档。</span><span class="sxs-lookup"><span data-stu-id="e5394-255">For more information about how to create virtual directories, see the IIS documentation.</span></span> <span data-ttu-id="e5394-256">建议尽量限制为该目录分配权限。</span><span class="sxs-lookup"><span data-stu-id="e5394-256">We recommend that you be as restrictive as possible when you assign permissions to this directory.</span></span> <span data-ttu-id="e5394-257">必须选择 **“读取”** 和 **“执行”** 权限，但可以清除 **“运行脚本”**、 **“写入”** 和 **“浏览”** 权限。</span><span class="sxs-lookup"><span data-stu-id="e5394-257">You must select **Read** and **Execute** permissions, but you can clear **Run scripts**, **Write**, and **Browse** permissions.</span></span>  
  
6.  <span data-ttu-id="e5394-258">配置 IIS 以允许执行 replisapi.dll。</span><span class="sxs-lookup"><span data-stu-id="e5394-258">Configure IIS to enable replisapi.dll to execute.</span></span> <span data-ttu-id="e5394-259">步骤 4 中分配的权限对 IIS 的早期版本足够了，但 IIS 6.0 版要求启用 Internet Server API (ISAPI) 扩展。</span><span class="sxs-lookup"><span data-stu-id="e5394-259">The permissions that are assigned in step 4 are sufficient for earlier versions of IIS; however, IIS version 6.0 requires Internet Server API (ISAPI) extensions to be enabled.</span></span> <span data-ttu-id="e5394-260">有关详细信息，请参阅 IIS 6.0 文档中的“配置 ISAPI 扩展”和“启用和禁用动态目录”。</span><span class="sxs-lookup"><span data-stu-id="e5394-260">For more information, see "Configuring ISAPI Extensions" and "Enabling and Disabling Dynamic Content" in the IIS 6.0 documentation.</span></span>  
  
#### <a name="to-configure-iis-authentication"></a><span data-ttu-id="e5394-261">配置 IIS 身份验证</span><span class="sxs-lookup"><span data-stu-id="e5394-261">To configure IIS authentication</span></span>  
  
-   <span data-ttu-id="e5394-262">当订阅方连接到 IIS 时，IIS 必须对其进行身份验证，订阅方才能访问资源和过程。</span><span class="sxs-lookup"><span data-stu-id="e5394-262">When Subscribers connect to IIS, IIS must authenticate the Subscribers before they can access resources and processes.</span></span> <span data-ttu-id="e5394-263">IIS 提供了三种类型的身份验证：匿名、基本和集成。</span><span class="sxs-lookup"><span data-stu-id="e5394-263">IIS offers three types of authentication: Anonymous, Basic, and Integrated.</span></span> <span data-ttu-id="e5394-264">身份验证可以应用于整个网站或您创建的虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="e5394-264">Authentication can be applied to the whole Web site or to the virtual directory that you created.</span></span>  
  
     <span data-ttu-id="e5394-265">建议您使用带有 SSL 的基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="e5394-265">We recommend that you use Basic Authentication with SSL.</span></span> <span data-ttu-id="e5394-266">无论使用何种类型的身份验证，都需要 SSL。</span><span class="sxs-lookup"><span data-stu-id="e5394-266">SSL is required, regardless of the type of authentication that is used.</span></span> <span data-ttu-id="e5394-267">有关如何配置身份验证的详细信息，请参阅 IIS 文档。</span><span class="sxs-lookup"><span data-stu-id="e5394-267">For more information about how to configure authentication, see the IIS documentation.</span></span>  
  
## <a name="setting-permissions-for-the-sql-server-replication-listener"></a><span data-ttu-id="e5394-268">设置 SQL Server 复制侦听器的权限</span><span class="sxs-lookup"><span data-stu-id="e5394-268">Setting Permissions for the SQL Server Replication Listener</span></span>  
 <span data-ttu-id="e5394-269">订阅服务器连接到正在运行 IIS 的计算机时，将使用您在配置 IIS 时指定的身份验证类型对订阅服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="e5394-269">When a Subscriber connects to the computer that is running IIS, the Subscriber is authenticated by using the type of authentication that was specified when you configured IIS.</span></span> <span data-ttu-id="e5394-270">IIS 对订阅服务器进行身份验证后，IIS 将检查订阅服务器是否有权调用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制。</span><span class="sxs-lookup"><span data-stu-id="e5394-270">After IIS authenticates the Subscriber, IIS checks whether the Subscriber is authorized to invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="e5394-271">通过设置 replisapi.dll 权限可以控制能够调用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制的用户。</span><span class="sxs-lookup"><span data-stu-id="e5394-271">You control the users that can invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication by setting permissions for replisapi.dll.</span></span> <span data-ttu-id="e5394-272">适当的权限配置对于防止在未经授权的情况下访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制而言很有必要。</span><span class="sxs-lookup"><span data-stu-id="e5394-272">Properly configuring permissions is necessary to prevent unauthorized access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span>  
  
 <span data-ttu-id="e5394-273">若要配置运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制侦听器的帐户的最低权限，请完成以下过程。</span><span class="sxs-lookup"><span data-stu-id="e5394-273">To configure the minimum permissions for the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener runs, complete the following procedure.</span></span> <span data-ttu-id="e5394-274">此过程中的步骤适用于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 运行 IIS 6.0。</span><span class="sxs-lookup"><span data-stu-id="e5394-274">The steps in the procedure apply to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] running IIS 6.0.</span></span>  
  
 <span data-ttu-id="e5394-275">除了要执行下列步骤之外，请确保所需的登录名存在于发布访问列表 (PAL) 中。</span><span class="sxs-lookup"><span data-stu-id="e5394-275">In addition to performing the following steps, make sure that the required logins are in the publication access list (PAL).</span></span> <span data-ttu-id="e5394-276">有关 PAL 的详细信息，请参阅[保护发布服务器](security/secure-the-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="e5394-276">For more information about the PAL, see [Secure the Publisher](security/secure-the-publisher.md).</span></span>  
  
#### <a name="to-configure-the-account-and-permissions"></a><span data-ttu-id="e5394-277">配置帐户和权限</span><span class="sxs-lookup"><span data-stu-id="e5394-277">To configure the account and permissions</span></span>  
  
1.  <span data-ttu-id="e5394-278">在运行 IIS 的计算机上创建一个本地帐户：</span><span class="sxs-lookup"><span data-stu-id="e5394-278">Create a local account on the computer that is running IIS:</span></span>  
  
    1.  <span data-ttu-id="e5394-279">右键单击“我的电脑”\*\*\*\*，然后单击“管理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e5394-279">Right-click **My Computer**, and then click **Manage**.</span></span>  
  
    2.  <span data-ttu-id="e5394-280">在 **“计算机管理”** 中，展开 **“本地用户和组”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-280">In **Computer Management**, expand **Local Users and Groups**.</span></span>  
  
    3.  <span data-ttu-id="e5394-281">右键单击 **“用户”** ，然后单击 **“新建用户”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-281">Right-click **Users**, and then click **New User**.</span></span>  
  
    4.  <span data-ttu-id="e5394-282">输入用户名和强密码。</span><span class="sxs-lookup"><span data-stu-id="e5394-282">Enter a user name and a strong password.</span></span>  
  
    5.  <span data-ttu-id="e5394-283">单击 **“创建”** ，然后单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-283">Click **Create**, and then click **Close**.</span></span>  
  
2.  <span data-ttu-id="e5394-284">将帐户添加到 IIS_WPG 组：</span><span class="sxs-lookup"><span data-stu-id="e5394-284">Add the account to the IIS_WPG group:</span></span>  
  
    1.  <span data-ttu-id="e5394-285">在 **“计算机管理”** 中，展开 **“本地用户和组”**，然后单击 **“组”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-285">In **Computer Management**, expand **Local Users and Groups**, and then click **Groups**.</span></span>  
  
    2.  <span data-ttu-id="e5394-286">右键单击 **IIS_WPG**，然后单击 **“添加到组”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-286">Right-click **IIS_WPG**, and then click **Add to Group**.</span></span>  
  
    3.  <span data-ttu-id="e5394-287">在 **“IIS_WPG 属性”** 对话框中，单击 **“添加”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-287">In the **IIS_WPG Properties** dialog box, click **Add**.</span></span>  
  
    4.  <span data-ttu-id="e5394-288">在 **“选择用户、计算机或组”** 对话框中，添加在步骤 1 中创建的帐户。</span><span class="sxs-lookup"><span data-stu-id="e5394-288">In the **Select Users, Computers, or Groups** dialog box, add the account created in step 1.</span></span>  
  
    5.  <span data-ttu-id="e5394-289">确保 **“从此位置”** 字段中为本地计算机（而不是域）的名称。</span><span class="sxs-lookup"><span data-stu-id="e5394-289">Make sure that the name in the **From this location** field is the name of the local computer instead of a domain.</span></span> <span data-ttu-id="e5394-290">如果不是本地计算机的名称，请单击 **“位置”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-290">If the name is not a local computer, click **Locations**.</span></span> <span data-ttu-id="e5394-291">在 **“位置”** 对话框中，选择本地计算机，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-291">In the **Locations** dialog box, elect the local computer, and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="e5394-292">在 **“选择用户”** 对话框和 **“IIS_WPG 属性”** 对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-292">In the **Select Users** dialog box and the **IIS_WPG Properties** dialog box, click **OK**.</span></span>  
  
3.  <span data-ttu-id="e5394-293">将包含 replisapi.dll 的文件夹的最低权限授予帐户：</span><span class="sxs-lookup"><span data-stu-id="e5394-293">Grant the minimum permissions on the folder that contains replisapi.dll to the account :</span></span>  
  
    1.  <span data-ttu-id="e5394-294">找到为 replisapi.dll 创建的文件夹，右键单击该文件夹，再单击 **“共享和安全”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-294">Locate the folder that you created for replisapi.dll, right-click the folder, and then click **Sharing and Security**.</span></span>  
  
    2.  <span data-ttu-id="e5394-295">在“安全”\*\*\*\* 选项卡上，单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e5394-295">On the **Security** tab, click **Add**.</span></span>  
  
    3.  <span data-ttu-id="e5394-296">在 **“选择用户、计算机或组”** 对话框中，添加在步骤 1 中创建的帐户。</span><span class="sxs-lookup"><span data-stu-id="e5394-296">In the **Select Users, Computers, or Groups** dialog box, add the account that you created in step 1.</span></span>  
  
    4.  <span data-ttu-id="e5394-297">确保 **“从此位置”** 字段中为本地计算机（而不是域）的名称。</span><span class="sxs-lookup"><span data-stu-id="e5394-297">Make sure that the name in the **From this location** field is the name of the local computer instead of a domain.</span></span> <span data-ttu-id="e5394-298">如果不是本地计算机的名称，请单击 **“位置”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-298">If the name is not a local computer, click **Locations**.</span></span> <span data-ttu-id="e5394-299">在 **“位置”** 对话框中，选择本地计算机，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-299">In the **Locations** dialog box, select the local computer, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="e5394-300">请确保只向该帐户授予“读取”、“读取和执行”和“列出文件夹内容”权限。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e5394-300">Make sure that the account is granted only **Read**, **Read & Execute**, and **List Folder Contents** permissions.</span></span>  
  
    6.  <span data-ttu-id="e5394-301">选择所有不需要访问该目录的用户或组，然后单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-301">Select any users or groups that do not require access to the directory, and then click **Remove**.</span></span>  
  
    7.  <span data-ttu-id="e5394-302">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="e5394-302">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="e5394-303">在 **“Internet 信息服务(IIS)管理器”** 中创建应用程序池：</span><span class="sxs-lookup"><span data-stu-id="e5394-303">Create an application pool in **Internet Information Services (IIS) Manager**:</span></span>  
  
    1.  <span data-ttu-id="e5394-304">单击 **“启动”** ，再单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-304">Click **Start**, and then click **Run**.</span></span>  
  
    2.  <span data-ttu-id="e5394-305">在 "**打开**" 框中键入 `inetmgr` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="e5394-305">In the **Open** box, type `inetmgr`, and then click **OK**.</span></span>  
  
    3.  <span data-ttu-id="e5394-306">在 **“Internet 信息服务(IIS)管理器”** 中，展开 **“本地计算机”** 节点。</span><span class="sxs-lookup"><span data-stu-id="e5394-306">In **Internet Information Services (IIS) Manager**, expand the **local computer** node.</span></span>  
  
    4.  <span data-ttu-id="e5394-307">右键单击 **“应用程序池”**，指向 **“新建”** ，然后单击 **“应用程序池”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-307">Right-click **Application Pools**, point to **New** and then click **Application Pool**.</span></span>  
  
    5.  <span data-ttu-id="e5394-308">在 **“应用程序池 ID”** 字段中，输入池的名称，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-308">Enter a name for the pool in the **Application pool ID** field, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="e5394-309">将帐户与应用程序池关联：</span><span class="sxs-lookup"><span data-stu-id="e5394-309">Associate the account with the application pool:</span></span>  
  
    1.  <span data-ttu-id="e5394-310">在 **“Internet 信息服务(IIS)管理器”** 中，展开 **“本地计算机”** 节点，然后展开 **“应用程序池”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-310">In **Internet Information Services (IIS) Manager**, expand the **local computer** node, and then expand **Application Pools**.</span></span>  
  
    2.  <span data-ttu-id="e5394-311">右键单击所创建的应用程序池，然后单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-311">Right-click the application pool that you created, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="e5394-312">在 " \*\* \<ApplicationPoolName> 属性**" 对话框的 "**标识**" 选项卡上，单击 "**可配置\*\*"。</span><span class="sxs-lookup"><span data-stu-id="e5394-312">In the **\<ApplicationPoolName> Properties** dialog box, on the **Identity** tab, click **Configurable**.</span></span>  
  
    4.  <span data-ttu-id="e5394-313">在 **“用户名”** 和 **“密码”** 字段中，输入在步骤 1 中创建的帐户和密码。</span><span class="sxs-lookup"><span data-stu-id="e5394-313">In the **User name** and **password** fields, enter the account and password that were created in step 1.</span></span>  
  
    5.  <span data-ttu-id="e5394-314">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="e5394-314">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="e5394-315">将应用程序池与用于 Web 同步的虚拟目录关联：</span><span class="sxs-lookup"><span data-stu-id="e5394-315">Associate the application pool with the virtual directory that is used for Web synchronization:</span></span>  
  
    1.  <span data-ttu-id="e5394-316">在 **“Internet 信息服务(IIS)管理器”** 中，展开 **“本地计算机”** 节点，再展开 **“网站”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-316">In **Internet Information Services (IIS) Manager**, expand the **local computer** node, and then expand **Web Sites**.</span></span>  
  
    2.  <span data-ttu-id="e5394-317">展开当前用于 Web 同步的网站，右键单击为 Web 同步所创建的虚拟目录，然后单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-317">Expand the Web site that you are using for Web synchronization, right-click the virtual directory that you created for Web synchronization, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="e5394-318">在 " \*\* \<VirtualDirectoryName> 属性**" 对话框的 "**虚拟目录**" 选项卡上的 "**应用程序池\*\*" 下拉列表中，选择在步骤5中创建的应用程序池。</span><span class="sxs-lookup"><span data-stu-id="e5394-318">On the **Virtual Directory** tab of the **\<VirtualDirectoryName> Properties** dialog box, from the **Application pool** drop-down list, select the application pool that was created in step 5.</span></span>  
  
    4.  <span data-ttu-id="e5394-319">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="e5394-319">Click **OK**.</span></span>  
  
## <a name="testing-the-connection-to-replisapidll"></a><span data-ttu-id="e5394-320">测试到 replisapi.dll 的连接</span><span class="sxs-lookup"><span data-stu-id="e5394-320">Testing the Connection to replisapi.dll</span></span>  
 <span data-ttu-id="e5394-321">在诊断模式下运行 Web 同步，以便测试与正在运行 IIS 的计算机的连接，并确保已正确安装安全套接字层 (SSL) 证书。</span><span class="sxs-lookup"><span data-stu-id="e5394-321">Run Web synchronization in diagnostic mode to test the connection to the computer that is running IIS and to make sure that the Secure Sockets Layer (SSL) certificate is properly installed.</span></span> <span data-ttu-id="e5394-322">若要在诊断模式下运行 Web 同步，您必须是运行 IIS 的计算机中的管理员。</span><span class="sxs-lookup"><span data-stu-id="e5394-322">To run Web synchronization in diagnostic mode, you must be an administrator on the computer running IIS.</span></span>  
  
#### <a name="to-test-the-connection-to-replisapidll"></a><span data-ttu-id="e5394-323">测试到 replisapi.dll 的连接</span><span class="sxs-lookup"><span data-stu-id="e5394-323">To test the connection to replisapi.dll</span></span>  
  
1.  <span data-ttu-id="e5394-324">确保订阅服务器中的局域网 (LAN) 设置正确：</span><span class="sxs-lookup"><span data-stu-id="e5394-324">Make sure that local area network (LAN) settings at the Subscriber are correct:</span></span>  
  
    1.  <span data-ttu-id="e5394-325">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 中的 **“工具”** 菜单中，单击 **“Internet 选项”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-325">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, on the **Tools** menu, click **Internet Options**.</span></span>  
  
    2.  <span data-ttu-id="e5394-326">在 **“连接”** 选项卡上，单击 **“局域网设置”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-326">On the **Connections** tab, click **LAN Settings**.</span></span>  
  
    3.  <span data-ttu-id="e5394-327">如果 LAN 中未使用代理服务器，请清除 **“自动检测设置”** 和 **“为 LAN 使用代理服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-327">If a proxy server is not used on the LAN, clear **Automatically Detect Settings** and **Use a proxy server for your LAN**.</span></span>  
  
    4.  <span data-ttu-id="e5394-328">如果使用了代理服务器，请选择 **“为 LAN 使用代理服务器”** 和 **“对于本地地址不使用代理服务器”**。</span><span class="sxs-lookup"><span data-stu-id="e5394-328">If a proxy server is used, select **Use a proxy server for your LAN** and **Bypass proxy server for local addresses**.</span></span>  
  
    5.  <span data-ttu-id="e5394-329">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="e5394-329">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="e5394-330">在订阅服务器上的 Internet Explorer 中，用向 replisapi.dll 的地址追加 `?diag` 的方法以诊断模式连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="e5394-330">At the Subscriber, in Internet Explorer, connect to the server in diagnostic mode by appending `?diag` to the address for the replisapi.dll.</span></span> <span data-ttu-id="e5394-331">例如：`https://server.domain.com/directory/replisapi.dll?diag`。</span><span class="sxs-lookup"><span data-stu-id="e5394-331">For example: `https://server.domain.com/directory/replisapi.dll?diag`.</span></span>  
  
3.  <span data-ttu-id="e5394-332">如果 Windows 操作系统不能识别您为 IIS 指定的证书，则会显示 **“安全警报”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="e5394-332">If the certificate that you specified for IIS is not recognized by the Windows operating system, the **Security Alert** dialog box appears.</span></span> <span data-ttu-id="e5394-333">如果该证书是测试证书或是由 Windows 不能识别的证书颁发机构 (CA) 颁发的证书，便会显示该警报。</span><span class="sxs-lookup"><span data-stu-id="e5394-333">This alert might occur because the certificate is a test certificate or the certificate was issued by a certification authority (CA) that Windows does not recognize.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5394-334">如果未出现此对话框，请确保您所访问的服务器的证书已作为可信证书添加到订阅服务器的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="e5394-334">If this dialog box does not appear, make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="e5394-335">有关导出证书的详细信息，请参阅 IIS 文档。</span><span class="sxs-lookup"><span data-stu-id="e5394-335">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
    1.  <span data-ttu-id="e5394-336">在 **“安全警报”** 对话框中，单击 **“查看证书”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-336">In the **Security Alert** dialog box, click **View Certificate**.</span></span>  
  
    2.  <span data-ttu-id="e5394-337">在 **“证书”** 对话框的 **“常规”** 选项卡上，单击 **“安装证书”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-337">In the **Certificate** dialog box, on the **General** tab, click **Install Certificate**.</span></span>  
  
    3.  <span data-ttu-id="e5394-338">完成证书导入向导，接受默认值。</span><span class="sxs-lookup"><span data-stu-id="e5394-338">Complete the Certificate Import Wizard, accepting the defaults.</span></span>  
  
    4.  <span data-ttu-id="e5394-339">在 **“安全警告”** 对话框中，单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-339">In the **Security Warning** dialog box, click **Yes**.</span></span>  
  
    5.  <span data-ttu-id="e5394-340">在“证书导入向导”确认对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-340">In the Certificate Import Wizard confirmation dialog box, click **OK**.</span></span>  
  
    6.  <span data-ttu-id="e5394-341">关闭 **“证书”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="e5394-341">Close the **Certificate** dialog box.</span></span>  
  
    7.  <span data-ttu-id="e5394-342">在 **“安全警报”** 对话框中，单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="e5394-342">In the **Security Alert** dialog box, click **Yes**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5394-343">为用户安装证书。</span><span class="sxs-lookup"><span data-stu-id="e5394-343">Certificates are installed for users.</span></span> <span data-ttu-id="e5394-344">必须为要与 IIS 同步的每个用户执行该过程。</span><span class="sxs-lookup"><span data-stu-id="e5394-344">This process must be performed for each user that will synchronize with IIS.</span></span>  
  
4.  <span data-ttu-id="e5394-345">在“连接到 \<ServerName>”对话框框中，指定合并代理将用于连接到 IIS 的登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="e5394-345">In the **Connect to \<ServerName>** dialog box, specify the login and password that the Merge Agent will use to connect to IIS.</span></span> <span data-ttu-id="e5394-346">在新建订阅向导中也要指定这些凭据。</span><span class="sxs-lookup"><span data-stu-id="e5394-346">These credentials will also be specified in the New Subscription Wizard.</span></span>  
  
5.  <span data-ttu-id="e5394-347">在名为 **“SQL Websync 诊断信息”** 的 Internet Explorer 窗口中，验证该页中每个 **“状态”** 列的值是否都为 **SUCCESS**。</span><span class="sxs-lookup"><span data-stu-id="e5394-347">In the Internet Explorer window called **SQL Websync diagnostic information**, verify that the value in each **Status** column on the page is **SUCCESS**.</span></span>  
  
6.  <span data-ttu-id="e5394-348">确保证书已正确安装到订阅服务器中：</span><span class="sxs-lookup"><span data-stu-id="e5394-348">Make sure that the certificate is installed correctly on the Subscriber:</span></span>  
  
    1.  <span data-ttu-id="e5394-349">关闭并重新打开 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="e5394-349">Close and then reopen Internet Explorer.</span></span>  
  
    2.  <span data-ttu-id="e5394-350">以诊断模式连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="e5394-350">Connect to the server in diagnostic mode.</span></span> <span data-ttu-id="e5394-351">如果证书安装正确，就不会显示 **“安全警报”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="e5394-351">If the certificate is installed properly, the **Security Alert** dialog box will not appear.</span></span> <span data-ttu-id="e5394-352">如果显示了该对话框，那么合并代理试图连接到正在运行 IIS 的计算机时就会失败。</span><span class="sxs-lookup"><span data-stu-id="e5394-352">If the dialog box appears, the Merge Agent will fail when it tries to connect to the computer that is running IIS.</span></span> <span data-ttu-id="e5394-353">必须确保您所访问的服务器的证书已作为可信证书添加到订阅服务器的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="e5394-353">You must make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="e5394-354">有关导出证书的详细信息，请参阅 IIS 文档。</span><span class="sxs-lookup"><span data-stu-id="e5394-354">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5394-355">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5394-355">See Also</span></span>  
 [<span data-ttu-id="e5394-356">配置 Web 同步</span><span class="sxs-lookup"><span data-stu-id="e5394-356">Configure Web Synchronization</span></span>](configure-web-synchronization.md)  
  
  
