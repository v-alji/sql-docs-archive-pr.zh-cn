---
title: 启用到数据库引擎 (SQL Server 配置管理器) 的加密连接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], encrypted
- SSL [SQL Server]
- Secure Sockets Layer (SSL)
- encryption [SQL Server], connections
- cryptography [SQL Server], connections
- certificates [SQL Server], installing
- requesting encrypted connections
- installing certificates
- security [SQL Server], encryption
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e1653df929e3f8bc67158a0685ce07b8ba65de6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693459"
---
# <a name="enable-encrypted-connections-to-the-database-engine-sql-server-configuration-manager"></a><span data-ttu-id="296fd-102">启用数据库引擎的加密连接（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="296fd-102">Enable Encrypted Connections to the Database Engine (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="296fd-103">本主题介绍如何通过使用 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 配置管理器为 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 指定证书来启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的加密连接。</span><span class="sxs-lookup"><span data-stu-id="296fd-103">This topic describes how to enable encrypted connections for an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] by specifying a certificate for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="296fd-104">服务器计算机必须具有提供的证书，客户端计算机必须设置为信任该证书的根颁发机构。</span><span class="sxs-lookup"><span data-stu-id="296fd-104">The server computer must have a certificate provisioned, and the client machine must be set up to trust the certificate's root authority.</span></span> <span data-ttu-id="296fd-105">提供是指通过将证书导入 Windows 来安装证书的过程。</span><span class="sxs-lookup"><span data-stu-id="296fd-105">Provisioning is the process of installing a certificate by importing it into Windows.</span></span>  
  
 <span data-ttu-id="296fd-106">必须颁发证书才能进行 **服务器身份验证**。</span><span class="sxs-lookup"><span data-stu-id="296fd-106">The certificate must be issued for **Server Authentication**.</span></span> <span data-ttu-id="296fd-107">证书名称必须为计算机的完全限定域名 (FQDN)。</span><span class="sxs-lookup"><span data-stu-id="296fd-107">The name of the certificate must be the fully qualified domain name (FQDN) of the computer.</span></span>  
  
 <span data-ttu-id="296fd-108">用户的证书存储在本地计算机上。</span><span class="sxs-lookup"><span data-stu-id="296fd-108">Certificates are stored locally for the users on the computer.</span></span> <span data-ttu-id="296fd-109">若要安装证书以供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用，必须使用运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务时所用的用户帐户来运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器，除非该服务作为 LocalSystem、NetworkService 或 LocalService 运行（在这种情况下，可以使用管理帐户）。</span><span class="sxs-lookup"><span data-stu-id="296fd-109">To install a certificate for use by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must be running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager under the same user account as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service unless the service is running as LocalSystem, NetworkService, or LocalService, in which case you may use an administrative account.</span></span>  
  
 <span data-ttu-id="296fd-110">客户端必须能够验证服务器所用证书的所有权。</span><span class="sxs-lookup"><span data-stu-id="296fd-110">The client must be able to verify the ownership of the certificate used by the server.</span></span> <span data-ttu-id="296fd-111">如果客户端具有对服务器证书进行签名的证书颁发机构所颁发的公钥证书，则不需要进一步的配置。</span><span class="sxs-lookup"><span data-stu-id="296fd-111">If the client has the public key certificate of the certification authority that signed the server certificate, no further configuration is necessary.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="296fd-112">Windows 包含多个证书颁发机构所颁发的公钥证书。</span><span class="sxs-lookup"><span data-stu-id="296fd-112">Windows includes the public key certificates of many certification authorities.</span></span> <span data-ttu-id="296fd-113">如果服务器证书由公共或私人证书颁发机构进行签名，而客户端没有该机构颁发的公钥证书，则必须安装对服务器证书进行签名的证书颁发机构所颁发的公钥证书。</span><span class="sxs-lookup"><span data-stu-id="296fd-113">If the server certificate was signed by a public or private certification authority for which the client does not have the public key certificate, you must install the public key certificate of the certification authority that signed the server certificate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="296fd-114">若要在故障转移群集中使用加密，必须在故障转移群集的所有节点上安装带有虚拟服务器的完全限定 DNS 名称的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="296fd-114">To use encryption with a failover cluster, you must install the server certificate with the fully qualified DNS name of the virtual server on all nodes in the failover cluster.</span></span> <span data-ttu-id="296fd-115">例如，如果有一个双节点群集，其中节点名为 *\<your company>* test1。com 和 *\<your company>* test2。对于 com，你有一个名为 virtsql 的虚拟服务器，需要为 virtsql 安装一个 *\<your company>* 证书。在两个节点上都有 com。</span><span class="sxs-lookup"><span data-stu-id="296fd-115">For example, if you have a two-node cluster, with nodes named test1.*\<your company>*.com and test2.*\<your company>*.com, and you have a virtual server named virtsql, you need to install a certificate for virtsql.*\<your company>*.com on both nodes.</span></span> <span data-ttu-id="296fd-116">可以将“ForceEncryption”\*\*\*\* 选项的值设置为“是”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="296fd-116">You can set the value of the **ForceEncryption**option to **Yes**.</span></span>  
  
 <span data-ttu-id="296fd-117">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="296fd-117">**In This Topic**</span></span>  
  
-   <span data-ttu-id="296fd-118">**若要允许加密连接：**</span><span class="sxs-lookup"><span data-stu-id="296fd-118">**To enable encrypted connections:**</span></span>  
  
     [<span data-ttu-id="296fd-119">在服务器上设置（安装）证书</span><span class="sxs-lookup"><span data-stu-id="296fd-119">Provision (install) a certificate on the server</span></span>](#Provision)  
  
     [<span data-ttu-id="296fd-120">导出服务器证书</span><span class="sxs-lookup"><span data-stu-id="296fd-120">Export the server certificate</span></span>](#Export)  
  
     [<span data-ttu-id="296fd-121">将服务器配置为接受加密连接</span><span class="sxs-lookup"><span data-stu-id="296fd-121">Configure the server to accept encrypted connections</span></span>](#ConfigureServerConnections)  
  
     [<span data-ttu-id="296fd-122">将客户端配置为请求加密连接</span><span class="sxs-lookup"><span data-stu-id="296fd-122">Configure the client to request encrypted connections</span></span>](#ConfigureClientConnections)  
  
     [<span data-ttu-id="296fd-123">通过 SQL Server Management Studio 加密连接</span><span class="sxs-lookup"><span data-stu-id="296fd-123">Encrypt a connection from SQL Server Management Studio</span></span>](#EncryptConnection)  
  
##  <a name="SSMSProcedure"></a>  
  
###  <a name="to-provision-install-a-certificate-on-the-server"></a><a name="Provision"></a> <span data-ttu-id="296fd-124">在服务器中提供（安装）证书</span><span class="sxs-lookup"><span data-stu-id="296fd-124">To provision (install) a certificate on the server</span></span>  
  
1.  <span data-ttu-id="296fd-125">在 "**开始**" 菜单上，单击 "**运行**"，然后在 "**打开**" 框中键入， `MMC` 然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="296fd-125">On the **Start** menu, click **Run**, and in the **Open** box, type `MMC` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="296fd-126">在 MMC 控制台的“文件”菜单上，单击“添加/删除管理单元”。</span><span class="sxs-lookup"><span data-stu-id="296fd-126">In the MMC console, on the **File** menu, click **Add/Remove Snap-in**.</span></span>  
  
3.  <span data-ttu-id="296fd-127">在“添加/删除管理单元”对话框中，单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="296fd-127">In the **Add/Remove Snap-in** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="296fd-128">在“添加独立管理单元”对话框中，单击“证书”，再单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="296fd-128">In the **Add Standalone Snap-in** dialog box, click **Certificates**, click **Add**.</span></span>  
  
5.  <span data-ttu-id="296fd-129">在“证书管理单元”对话框中，单击“计算机帐户”，再单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="296fd-129">In the **Certificates snap-in** dialog box, click **Computer account**, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="296fd-130">在“添加独立管理单元”对话框中，单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="296fd-130">In the **Add Standalone Snap-in** dialog box, click **Close.**</span></span>  
  
7.  <span data-ttu-id="296fd-131">在“添加/删除管理单元”对话框中，单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="296fd-131">In the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
8.  <span data-ttu-id="296fd-132">在“证书”管理单元中，依次展开“证书”和“个人”，右键单击“证书”，指向“所有任务”，然后单击“导入”。</span><span class="sxs-lookup"><span data-stu-id="296fd-132">In the **Certificates** snap-in, expand **Certificates**, expand **Personal**, and then right-click **Certificates**, point to **All Tasks**, and then click **Import**.</span></span>  
  
9. <span data-ttu-id="296fd-133">完成 **证书导入向导**，将证书添加到计算机中，然后关闭 MMC 控制台。</span><span class="sxs-lookup"><span data-stu-id="296fd-133">Complete the **Certificate Import Wizard**, to add a certificate to the computer, and close the MMC console.</span></span> <span data-ttu-id="296fd-134">有关向计算机添加证书的详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="296fd-134">For more information about adding a certificate to a computer, see your Windows documentation.</span></span>  
  
###  <a name="to-export-the-server-certificate"></a><a name="Export"></a> <span data-ttu-id="296fd-135">导出服务器证书</span><span class="sxs-lookup"><span data-stu-id="296fd-135">To export the server certificate</span></span>  
  
1.  <span data-ttu-id="296fd-136">在“证书”管理单元中的“证书” / “个人”文件夹中找到证书，右键单击“证书”，指向“所有任务”，然后单击“导出”。</span><span class="sxs-lookup"><span data-stu-id="296fd-136">From the **Certificates** snap-in, locate the certificate in the **Certificates** / **Personal** folder, right-click the **Certificate**, point to **All Tasks**, and then click **Export**.</span></span>  
  
2.  <span data-ttu-id="296fd-137">完成 **“证书导出向导”** ，将证书文件存储在方便的位置。</span><span class="sxs-lookup"><span data-stu-id="296fd-137">Complete the **Certificate Export Wizard**, storing the certificate file in a convenient location.</span></span>  
  
###  <a name="to-configure-the-server-to-accept-encrypted-connections"></a><a name="ConfigureServerConnections"></a> <span data-ttu-id="296fd-138">将服务器配置为接受加密连接</span><span class="sxs-lookup"><span data-stu-id="296fd-138">To configure the server to accept encrypted connections</span></span>  
  
1.  <span data-ttu-id="296fd-139">在“SQL Server 配置管理器”中，展开“SQL Server 网络配置”，右键单击“\<server instance> 的协议”，然后选择“属性”。  </span><span class="sxs-lookup"><span data-stu-id="296fd-139">In **SQL Server Configuration Manager**, expand **SQL Server Network Configuration**, right-click **Protocols for** _\<server instance>_, and then select**Properties**.</span></span>  
  
2.  <span data-ttu-id="296fd-140">在 " **Protocols for** _\<instance name>_ **属性**的协议" 对话框中的 "**证书**" 选项卡上，从 "**证书**" 框的下拉菜单中选择所需的证书，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="296fd-140">In the **Protocols for**_\<instance name>_ **Properties** dialog box, on the **Certificate** tab, select the desired certificate from the drop down for the **Certificate** box, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="296fd-141">在 **“标志”** 选项卡的 **“ForceEncryption”** 框中，选择 **“是”** ，然后单击 **“确定”** 关闭该对话框。</span><span class="sxs-lookup"><span data-stu-id="296fd-141">On the **Flags** tab, in the **ForceEncryption** box, select **Yes**, and then click **OK** to close the dialog box.</span></span>  
  
4.  <span data-ttu-id="296fd-142">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="296fd-142">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
###  <a name="to-configure-the-client-to-request-encrypted-connections"></a><a name="ConfigureClientConnections"></a> <span data-ttu-id="296fd-143">将客户端配置为请求加密连接</span><span class="sxs-lookup"><span data-stu-id="296fd-143">To configure the client to request encrypted connections</span></span>  
  
1.  <span data-ttu-id="296fd-144">将原始证书或导出的证书文件复制到客户端计算机。</span><span class="sxs-lookup"><span data-stu-id="296fd-144">Copy either the original certificate or the exported certificate file to the client computer.</span></span>  
  
2.  <span data-ttu-id="296fd-145">在客户端计算机上，使用“证书”管理单元来安装根证书或导出的证书文件。</span><span class="sxs-lookup"><span data-stu-id="296fd-145">On the client computer, use the **Certificates** snap-in to install either the root certificate or the exported certificate file.</span></span>  
  
3.  <span data-ttu-id="296fd-146">在控制台窗格中，右键单击“SQL Server Native Client 配置”\*\*\*\*，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="296fd-146">In the console pane, right-click **SQL Server Native Client Configuration**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="296fd-147">在 **“标志”** 选项卡的 **“强制协议加密”** 框中，单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="296fd-147">On the **Flags** page, in the **Force protocol encryption** box, click **Yes**.</span></span>  
  
###  <a name="to-encrypt-a-connection-from-sql-server-management-studio"></a><a name="EncryptConnection"></a><span data-ttu-id="296fd-148">加密 SQL Server Management Studio 的连接</span><span class="sxs-lookup"><span data-stu-id="296fd-148">To encrypt a connection from SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="296fd-149">在对象资源管理器工具栏上，单击 **“连接”** ，再单击 **“数据库引擎”** 。</span><span class="sxs-lookup"><span data-stu-id="296fd-149">On the Object Explorer toolbar, click **Connect**, and then click **Database Engine**.</span></span>  
  
2.  <span data-ttu-id="296fd-150">在 **“连接到服务器”** 对话框中，填写连接信息，然后单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="296fd-150">In the **Connect to Server** dialog box, complete the connection information, and then click **Options**.</span></span>  
  
3.  <span data-ttu-id="296fd-151">在 **“连接属性”** 选项卡上，单击 **“加密连接”** 。</span><span class="sxs-lookup"><span data-stu-id="296fd-151">On the **Connection Properties** tab, click **Encrypt connection**.</span></span>  
  
  
