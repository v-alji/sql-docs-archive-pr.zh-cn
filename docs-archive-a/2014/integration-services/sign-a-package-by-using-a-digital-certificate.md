---
title: 使用数字证书对包进行签名 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- digital signatures [Integration Services]
- signing packages [Integration Services]
- signatures [Integration Services]
ms.assetid: 182b115e-0fe2-4717-8dff-183f9eb6e397
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6bd0f73d609623f882e474c96a01cd3bc0274b6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694017"
---
# <a name="sign-a-package-by-using-a-digital-certificate"></a><span data-ttu-id="d9e1f-102">使用数字证书对包签名</span><span class="sxs-lookup"><span data-stu-id="d9e1f-102">Sign a Package by Using a Digital Certificate</span></span>
  <span data-ttu-id="d9e1f-103">本主题介绍如何使用数字证书对 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包进行签名。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-103">This topic describes how to sign an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package with a digital certificate.</span></span> <span data-ttu-id="d9e1f-104">可以使用数字签名以及其他设置来防止加载和运行无效的包。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-104">You can use a digital signature, together with other settings, to prevent a package that is not valid from loading and running.</span></span>  
  
 <span data-ttu-id="d9e1f-105">必须先执行下列任务才能对 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包进行签名：</span><span class="sxs-lookup"><span data-stu-id="d9e1f-105">Before you can sign an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, you must do the following tasks:</span></span>  
  
-   <span data-ttu-id="d9e1f-106">创建或获取私钥以便与证书关联，并将此私钥存储在本地计算机上。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-106">Create or obtain a private key to associate with the certificate, and store this private key on the local computer.</span></span>  
  
-   <span data-ttu-id="d9e1f-107">以代码签名为目的从可信证书颁发机构获取证书。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-107">Obtain a certificate for the purpose of code signing from a trusted certification authority.</span></span> <span data-ttu-id="d9e1f-108">可以使用下列方法之一来获取或创建证书：</span><span class="sxs-lookup"><span data-stu-id="d9e1f-108">You can use one of the following methods to obtain or create a certificate:</span></span>  
  
    -   <span data-ttu-id="d9e1f-109">从颁发证书的公共商业证书颁发机构获取证书。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-109">Obtain a certificate from a public, commercial certification authority that issues certificates.</span></span>  
  
    -   <span data-ttu-id="d9e1f-110">从允许组织在内部颁发证书的证书服务器获取证书。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-110">Obtain a certificate from a certificate server, that enables an organization to internally issue certificates.</span></span> <span data-ttu-id="d9e1f-111">必须将用于对证书进行签名的根证书添加到 **“受信任的根证书颁发机构”** 存储区中。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-111">You have to add the root certificate that is used to sign the certificate to the **Trusted Root Certification Authorities** store.</span></span> <span data-ttu-id="d9e1f-112">若要添加根证书，可以使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 管理控制台 (MMC) 的证书管理单元。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-112">To add the root certificate, you can use the Certificates snap-in for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console (MMC).</span></span> <span data-ttu-id="d9e1f-113">有关详细信息，请参阅 MSDN 库中的主题“[Certificate Services](https://go.microsoft.com/fwlink/?LinkId=100755)（证书服务）”。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-113">For more information, see the topic, "[Certificate Services](https://go.microsoft.com/fwlink/?LinkId=100755)," in the MSDN library.</span></span>  
  
    -   <span data-ttu-id="d9e1f-114">创建自己的证书（仅用于测试目的）。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-114">Create your own certificate for testing purposes only.</span></span> <span data-ttu-id="d9e1f-115">证书创建工具 (Makecert.exe) 会生成仅用于测试目的的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-115">The Certificate Creation Tool (Makecert.exe) generates X.509 certificates for testing purposes.</span></span> <span data-ttu-id="d9e1f-116">有关详细信息，请参阅 MSDN Library 中的主题“[证书创建工具 (Makecert.exe)](https://go.microsoft.com/fwlink/?LinkId=100756)”。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-116">For more information, see the topic, "[Certificate Creation Tool (Makecert.exe)](https://go.microsoft.com/fwlink/?LinkId=100756)," in the MSDN Library.</span></span>  
  
     <span data-ttu-id="d9e1f-117">有关证书的详细信息，请参阅证书管理单元的联机帮助。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-117">For more information about certificates, see the online Help for the Certificates snap-in.</span></span> <span data-ttu-id="d9e1f-118">有关如何对数字资产进行签名的详细信息，请参阅 MSDN 库中的主题“[Signing and Checking Code with Authenticode](https://go.microsoft.com/fwlink/?LinkId=78100)（使用 Authenticode 签名和检查代码）”。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-118">For more information about how to sign digital assets, see the topic, "[Signing and Checking Code with Authenticode](https://go.microsoft.com/fwlink/?LinkId=78100)," in the MSDN Library.</span></span>  
  
-   <span data-ttu-id="d9e1f-119">确保已为代码签名启用证书。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-119">Make sure that the certificate has been enabled for code signing.</span></span> <span data-ttu-id="d9e1f-120">若要确定证书是否是为代码签名而启用的，请在“证书”管理单元中检查证书的属性。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-120">To determine whether a certificate is enabled for code signing, review the properties of the certificate in the Certificates snap-in.</span></span>  
  
-   <span data-ttu-id="d9e1f-121">将证书存储在个人存储区中。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-121">Store the certificate in the Personal store.</span></span>  
  
 <span data-ttu-id="d9e1f-122">完成上述任务后，即可使用下列过程对包进行签名。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-122">After you have completed the previous tasks, you can use the following procedure to sign a package.</span></span>  
  
### <a name="to-sign-a-package"></a><span data-ttu-id="d9e1f-123">签署包</span><span class="sxs-lookup"><span data-stu-id="d9e1f-123">To sign a package</span></span>  
  
1.  <span data-ttu-id="d9e1f-124">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开要签名的包所在的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-124">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to be signed.</span></span>  
  
2.  <span data-ttu-id="d9e1f-125">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-125">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="d9e1f-126">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器的 **“SSIS”** 菜单上，单击 **“数字签名”**。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-126">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, on the **SSIS** menu, click **Digital Signing**.</span></span>  
  
4.  <span data-ttu-id="d9e1f-127">在 **“数字签名”** 对话框中，单击 **“签名”**。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-127">In the **Digital Signing** dialog box, click **Sign**.</span></span>  
  
5.  <span data-ttu-id="d9e1f-128">在 **“选择证书”** 对话框中，选择一个证书。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-128">In the **Select a Certificate** dialog box, select a certificate.</span></span>  
  
6.  <span data-ttu-id="d9e1f-129">也可单击“查看证书”\*\*\*\* 来查看证书信息。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-129">(Optional) Click **View Certificat**e to view certificate information.</span></span>  
  
7.  <span data-ttu-id="d9e1f-130">单击 **“确定”** 关闭 **“选项证书”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-130">Click **OK** to close the **Select a Certificate** dialog box.</span></span>  
  
8.  <span data-ttu-id="d9e1f-131">单击 **“确定”** 关闭 **“数字签名”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-131">Click **OK** to close the **Digital Signing** dialog box.</span></span>  
  
9. <span data-ttu-id="d9e1f-132">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-132">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
     <span data-ttu-id="d9e1f-133">虽然已对包进行了签名，您现在必须配置 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ，以便在加载该包之前检查或验证数字签名。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-133">Although the package has been signed, you must now configure [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] to check or verify the digital signature before loading the package.</span></span> <span data-ttu-id="d9e1f-134">有关详细信息，请参阅 [使用数字签名标识包的源](security/identify-the-source-of-packages-with-digital-signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e1f-134">For more information, see [Identify the Source of Packages with Digital Signatures](security/identify-the-source-of-packages-with-digital-signatures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e1f-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9e1f-135">See Also</span></span>  
 [<span data-ttu-id="d9e1f-136">安全性概述 (Integration Services)</span><span class="sxs-lookup"><span data-stu-id="d9e1f-136">Security Overview &#40;Integration Services&#41;</span></span>](security/security-overview-integration-services.md)  
  
  
