---
title: " (SSRS 本机模式) 的执行帐户 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.executionaccount.F1
ms.assetid: 440b5a09-5fd4-4c3a-b510-f3c33cbf1c82
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 10e158eb38b9d1f94257f48339bb63bae2d3b61b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588886"
---
# <a name="execution-account-ssrs-native-mode"></a><span data-ttu-id="a90ad-102">执行帐户（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="a90ad-102">Execution Account (SSRS Native Mode)</span></span>
  <span data-ttu-id="a90ad-103">使用此页可以配置用于无人参与处理的帐户。</span><span class="sxs-lookup"><span data-stu-id="a90ad-103">Use this page to configure an account to use for unattended processing.</span></span> <span data-ttu-id="a90ad-104">只有在其他凭据源不可用的以下特殊情况时，才使用此帐户：</span><span class="sxs-lookup"><span data-stu-id="a90ad-104">This account is used under special circumstances when other sources of credentials are not available:</span></span>  
  
-   <span data-ttu-id="a90ad-105">当报表服务器连接到不需要凭据的数据源时。</span><span class="sxs-lookup"><span data-stu-id="a90ad-105">When the report server connects to a data source that does not require credentials.</span></span> <span data-ttu-id="a90ad-106">可能不需要凭据的数据源示例包括 XML 文档和一些客户端数据库应用程序。</span><span class="sxs-lookup"><span data-stu-id="a90ad-106">Examples of data sources that might not require credentials include XML documents and some client-side database applications.</span></span>  
  
-   <span data-ttu-id="a90ad-107">当报表服务器连接到其他服务器以检索报表中所引用的外部图像文件或其他资源时。</span><span class="sxs-lookup"><span data-stu-id="a90ad-107">When the report server connects to another server to retrieve external image files or other resources that are referenced in a report.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="a90ad-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式。</span><span class="sxs-lookup"><span data-stu-id="a90ad-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="a90ad-109">设置此帐户是可选的，但如果不设置此帐户，则将限制您使用外部图像以及与一些数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="a90ad-109">Setting this account is optional, but not setting it limits your use of external images and connections to some data sources.</span></span> <span data-ttu-id="a90ad-110">在检索外部图像文件时，报表服务器将检查是否可以建立匿名连接。</span><span class="sxs-lookup"><span data-stu-id="a90ad-110">When retrieving external image files, the report server checks to see if an anonymous connection can be made.</span></span> <span data-ttu-id="a90ad-111">如果连接受密码保护，报表服务器将使用无人参与的报表处理帐户来连接到远程服务器。</span><span class="sxs-lookup"><span data-stu-id="a90ad-111">If the connection is password protected, the report server uses the unattended report processing account to connect to the remote server.</span></span> <span data-ttu-id="a90ad-112">在为报表检索数据时，报表服务器或者模拟当前用户、提示用户提供凭据或使用存储的凭据，或者（如果数据源连接指定 **“无”** 作为凭证类型）使用无人参与的处理帐户。</span><span class="sxs-lookup"><span data-stu-id="a90ad-112">When retrieving data for a report, the report server either impersonates the current user, prompts the user to provide credentials, uses stored credentials, or uses the unattended processing account if the data source connection specifies **None** as the credential type.</span></span> <span data-ttu-id="a90ad-113">在连接到其他计算机时，报表服务器不允许对其服务帐户凭据进行委托或模拟，因此，如果不能使用其他凭据，报表服务器就必须使用无人参与的处理帐户。</span><span class="sxs-lookup"><span data-stu-id="a90ad-113">The report server does not allow its service account credentials to be delegated or impersonated when connecting to other computers, so it must use the unattended processing account if no other credentials are available.</span></span>  
  
 <span data-ttu-id="a90ad-114">您指定的帐户不能是用于运行服务帐户的帐户。</span><span class="sxs-lookup"><span data-stu-id="a90ad-114">The account you specify should be different from the one used to run the service account.</span></span> <span data-ttu-id="a90ad-115">如果配置了该帐户，它将作为加密值存储在 RSReportServer.config 文件中。</span><span class="sxs-lookup"><span data-stu-id="a90ad-115">If you configure this account, it is stored in the RSReportServer.config file as an encrypted value.</span></span> <span data-ttu-id="a90ad-116">如果将在扩展部署中运行该报表服务器，则必须在每个报表服务器上以相同的方式配置此帐户。</span><span class="sxs-lookup"><span data-stu-id="a90ad-116">If you are running the report server in a scale-out deployment, you must configure this account the same way on each report server.</span></span>  
  
 <span data-ttu-id="a90ad-117">您可以使用任何一个 Windows 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="a90ad-117">You can use any Windows user account.</span></span> <span data-ttu-id="a90ad-118">为获得最佳结果，请选择拥有读取权限和网络登录权限的帐户，以支持与其他计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="a90ad-118">For best results, choose an account that has read permissions and network logon permissions to support connections to other computers.</span></span> <span data-ttu-id="a90ad-119">对于您希望在报表中使用的任何外部图像或数据文件，它必须拥有对这些文件的读取权限。</span><span class="sxs-lookup"><span data-stu-id="a90ad-119">It must have read permissions on any external image or data file that you want to use in a report.</span></span> <span data-ttu-id="a90ad-120">切勿指定本地帐户，除非所有报表数据源和外部图像均存储在报表服务器计算机中。</span><span class="sxs-lookup"><span data-stu-id="a90ad-120">Do not specify a local account unless all report data sources and external images are stored on the report server computer.</span></span> <span data-ttu-id="a90ad-121">只可将该帐户用于无人参与报表处理。</span><span class="sxs-lookup"><span data-stu-id="a90ad-121">Use the account only for unattended report processing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a90ad-122">如果使用的是带高级服务的 [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)]，则仅当在报表中引用外部图像并且访问该图像文件需要相应权限时才需要配置此帐户。</span><span class="sxs-lookup"><span data-stu-id="a90ad-122">If you are using [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] with Advanced Services, you only need to configure this account if you are referencing external images in a report and permission is required to access the image file.</span></span> <span data-ttu-id="a90ad-123">SQL Server Express 不支持到远程服务器的数据源连接。</span><span class="sxs-lookup"><span data-stu-id="a90ad-123">SQL Server Express does not support a data source connection to a remote server.</span></span> <span data-ttu-id="a90ad-124">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]各版本支持的功能列表，请参阅 [SQL Server 2012 各个版本支持的功能](https://go.microsoft.com/fwlink/?linkid=232473)。</span><span class="sxs-lookup"><span data-stu-id="a90ad-124">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
 <span data-ttu-id="a90ad-125">若要打开此页，请启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器，并在导航窗格中选择 **“执行帐户”** 。</span><span class="sxs-lookup"><span data-stu-id="a90ad-125">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and select **Execution Account** in the navigation pane.</span></span> <span data-ttu-id="a90ad-126">有关详细信息，请参阅 [Reporting Services Configuration Manager（本机模式）](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="a90ad-126">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a90ad-127">选项</span><span class="sxs-lookup"><span data-stu-id="a90ad-127">Options</span></span>  
 <span data-ttu-id="a90ad-128">**指定执行帐户**</span><span class="sxs-lookup"><span data-stu-id="a90ad-128">**Specify an execution account**</span></span>  
 <span data-ttu-id="a90ad-129">选择此选项可指定一个帐户。</span><span class="sxs-lookup"><span data-stu-id="a90ad-129">Select to specify an account.</span></span>  
  
 <span data-ttu-id="a90ad-130">**帐户**</span><span class="sxs-lookup"><span data-stu-id="a90ad-130">**Account**</span></span>  
 <span data-ttu-id="a90ad-131">输入一个 Windows 域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="a90ad-131">Enter a Windows domain user account.</span></span> <span data-ttu-id="a90ad-132">使用以下格式： \* \<domain> \\<用户帐户 \> \*。</span><span class="sxs-lookup"><span data-stu-id="a90ad-132">Use this format: *\<domain>\\<user account\>*.</span></span>  
  
 <span data-ttu-id="a90ad-133">**密码**</span><span class="sxs-lookup"><span data-stu-id="a90ad-133">**Password**</span></span>  
 <span data-ttu-id="a90ad-134">键入密码。</span><span class="sxs-lookup"><span data-stu-id="a90ad-134">Type the password.</span></span>  
  
 <span data-ttu-id="a90ad-135">**确认密码**</span><span class="sxs-lookup"><span data-stu-id="a90ad-135">**Confirm password**</span></span>  
 <span data-ttu-id="a90ad-136">重新键入密码。</span><span class="sxs-lookup"><span data-stu-id="a90ad-136">Retype the password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a90ad-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a90ad-137">See Also</span></span>  
 <span data-ttu-id="a90ad-138">[Reporting Services 配置管理器的 F1 帮助主题 &#40;SSRS 本机模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="a90ad-138">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="a90ad-139">[存储加密的 Report Server 数据（SSRS 配置管理器）](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span><span class="sxs-lookup"><span data-stu-id="a90ad-139">[Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span></span>  
 [<span data-ttu-id="a90ad-140">配置无人参与的执行帐户（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="a90ad-140">Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
  
  
