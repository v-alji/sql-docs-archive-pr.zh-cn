---
title: 配置无人参与的执行帐户（SSRS 配置管理器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- no credentials option [Reporting Services]
- security [Reporting Services], unattended report processing
- unattended report processing [Reporting Services]
- credentials [Reporting Services]
- external data sources [Reporting Services]
- accounts [Reporting Services]
- reports [Reporting Services], processing
ms.assetid: 4e50733e-bd8c-4bf6-8379-98b1531bb9ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 437b28b57bc304d079acea3123983bed389341ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689795"
---
# <a name="configure-the-unattended-execution-account-ssrs-configuration-manager"></a><span data-ttu-id="57f97-102">配置无人参与的执行帐户（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="57f97-102">Configure the Unattended Execution Account (SSRS Configuration Manager)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="57f97-103">提供一个特殊帐户，用于进行无人参与的报表处理和通过网络发送连接请求。</span><span class="sxs-lookup"><span data-stu-id="57f97-103">provides a special account that is used for unattended report processing and for sending connection requests across the network.</span></span> <span data-ttu-id="57f97-104">可以通过下列方式使用该帐户：</span><span class="sxs-lookup"><span data-stu-id="57f97-104">The account is used in the following ways:</span></span>  
  
-   <span data-ttu-id="57f97-105">通过网络为使用数据库身份验证的报表发送连接请求，或连接到不需要或不使用身份验证的外部报表数据源。</span><span class="sxs-lookup"><span data-stu-id="57f97-105">Send connection requests over the network for reports that use database authentication, or connect to external report data sources that do not require or use authentication.</span></span> <span data-ttu-id="57f97-106">有关详细信息，请参阅 SQL Server 联机丛书中的 [为报表数据源指定凭据和连接信息](../../integration-services/connection-manager/data-sources.md) 。</span><span class="sxs-lookup"><span data-stu-id="57f97-106">For more information, see [Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md) in SQL Server Books Online.</span></span>  
  
-   <span data-ttu-id="57f97-107">检索在报表中使用的外部图像文件。</span><span class="sxs-lookup"><span data-stu-id="57f97-107">Retrieve external image files that are used in report.</span></span> <span data-ttu-id="57f97-108">如果您要使用图像文件并且无法通过匿名访问来访问该文件，则可以配置无人参与的报表处理帐户并授予该帐户访问该文件的权限。</span><span class="sxs-lookup"><span data-stu-id="57f97-108">If you want to use an image file and the file cannot be accessed through Anonymous access, you can configure the unattended report processing account and grant the account permission to access the file.</span></span>  
  
 <span data-ttu-id="57f97-109">无人参与的报表处理是指任何由事件（计划驱动事件或数据刷新事件）而不是用户请求触发的报表执行过程。</span><span class="sxs-lookup"><span data-stu-id="57f97-109">Unattended report processing refers to any report execution process that is triggered by an event (either a schedule-driven event or data refresh event) rather than a user request.</span></span> <span data-ttu-id="57f97-110">报表服务器使用无人参与的报表处理帐户来登录承载外部数据源的计算机。</span><span class="sxs-lookup"><span data-stu-id="57f97-110">The report server uses the unattended report processing account to log on to the computer that hosts the external data source.</span></span> <span data-ttu-id="57f97-111">由于报表服务器服务帐户从不用于连接到其他计算机，因此该帐户是必需的。</span><span class="sxs-lookup"><span data-stu-id="57f97-111">This account is necessary because the credentials of the Report Server service account are never used to connect to other computers.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="57f97-112">配置该帐户的过程为可选操作。</span><span class="sxs-lookup"><span data-stu-id="57f97-112">Configuring the account is optional.</span></span> <span data-ttu-id="57f97-113">但是，如果不配置该帐户，用于连接到某些数据源的选项会受到限制，并且可能无法从远程计算机检索图像文件。</span><span class="sxs-lookup"><span data-stu-id="57f97-113">However, if you do not configure it, you will limit your options for connecting to some data sources, and you might not be able to retrieve image files from remote computers.</span></span> <span data-ttu-id="57f97-114">如果配置了该帐户，则必须对其进行不断更新。</span><span class="sxs-lookup"><span data-stu-id="57f97-114">If you do configure the account, you must keep it up to date.</span></span> <span data-ttu-id="57f97-115">具体来说，如果允许密码过期或在 Active Directory 中更改了帐户信息，则在下次处理报表时将遇到以下错误：“登录失败 (rsLogonFailed) 登录失败: 未知的用户名或密码不正确。”</span><span class="sxs-lookup"><span data-stu-id="57f97-115">Specifically, if you allow a password to expire or the account information is changed in Active Directory, you will encounter the following error the next time a report is processed: "Logon failed (rsLogonFailed) Logon failure: unknown user name or bad password."</span></span> <span data-ttu-id="57f97-116">即使您从不检索外部图像也不向外部计算机发送连接请求，正确维护无人参与的报表处理帐户也是必要的。</span><span class="sxs-lookup"><span data-stu-id="57f97-116">Proper maintenance of the unattended report processing account is essential, even if you never retrieve external images or send connection requests to external computers.</span></span> <span data-ttu-id="57f97-117">如果配置了该帐户但后来发现不需要使用它，则可以将其删除以避免日常的帐户维护任务。</span><span class="sxs-lookup"><span data-stu-id="57f97-117">If you configure the account but then find that you are not using it, you can delete it to avoid routine account maintenance tasks.</span></span>  
  
## <a name="how-to-configure-the-account"></a><span data-ttu-id="57f97-118">如何配置帐户</span><span class="sxs-lookup"><span data-stu-id="57f97-118">How to Configure the Account</span></span>  
 <span data-ttu-id="57f97-119">必须使用域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="57f97-119">You must use a domain user account.</span></span> <span data-ttu-id="57f97-120">若要发挥该帐户应有的作用，它应不同于用于运行报表服务器服务的帐户。</span><span class="sxs-lookup"><span data-stu-id="57f97-120">To serve its intended purpose, this account should be different than the one used to run the Report Server service.</span></span> <span data-ttu-id="57f97-121">请确保使用具有如下特征的帐户：对为报表服务器提供数据源和资源的那些计算机只拥有最小权限（具有网络连接权限的只读访问权限就已足够）和有限访问权限。</span><span class="sxs-lookup"><span data-stu-id="57f97-121">Be sure to use an account that has minimum permissions (read-only access with network connection permissions is sufficient) and limited access to just those computers that provide data sources and resources to the report server.</span></span> <span data-ttu-id="57f97-122">有关详细信息，请参阅 [Reporting Services Configuration Manager（本机模式）](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="57f97-122">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 <span data-ttu-id="57f97-123">若要指定帐户，可使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具或 **rsconfig** 实用工具。</span><span class="sxs-lookup"><span data-stu-id="57f97-123">To specify the account, you can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool or the **rsconfig** utility.</span></span> <span data-ttu-id="57f97-124">配置无人参与的执行帐户的最简便方法是运行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具，然后在“执行帐户”页中指定凭据。</span><span class="sxs-lookup"><span data-stu-id="57f97-124">The easiest way to configure the unattended execution account is to run the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and specify credentials in the Execution Account page.</span></span>  
  
1.  <span data-ttu-id="57f97-125">启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具，然后连接到要配置的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="57f97-125">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you want to configure.</span></span> <span data-ttu-id="57f97-126">有关说明，请参阅 [Reporting Services Configuration Manager（本机模式）](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="57f97-126">For instructions, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="57f97-127">在“执行帐户”页上，选择 **“指定执行帐户”** 。</span><span class="sxs-lookup"><span data-stu-id="57f97-127">On the Execution Account page, select **Specify an execution account**.</span></span>  
  
3.  <span data-ttu-id="57f97-128">键入帐户和密码，再次键入密码，然后单击 **“应用”** 。</span><span class="sxs-lookup"><span data-stu-id="57f97-128">Type the account and password, retype the password, and then click **Apply**.</span></span>  
  
### <a name="using-rsconfig-utility"></a><span data-ttu-id="57f97-129">使用 RSCONFIG 实用工具</span><span class="sxs-lookup"><span data-stu-id="57f97-129">Using RSCONFIG Utility</span></span>  
 <span data-ttu-id="57f97-130">设置帐户的另一种方法是使用 **rsconfig** 实用工具。</span><span class="sxs-lookup"><span data-stu-id="57f97-130">Another way to set the account is to use the **rsconfig** utility.</span></span> <span data-ttu-id="57f97-131">若要指定帐户，请使用 **rsconfig** 的 **-e**参数。</span><span class="sxs-lookup"><span data-stu-id="57f97-131">To specify the account, use the **-e** argument of **rsconfig**.</span></span> <span data-ttu-id="57f97-132">为 **rsconfig** 指定 **-e** 参数可强制该实用工具将帐户信息写入到配置文件中。</span><span class="sxs-lookup"><span data-stu-id="57f97-132">Specifying the **-e** argument for **rsconfig** directs the utility to write the account information to the configuration file.</span></span> <span data-ttu-id="57f97-133">您无需指定 RSreportserver.config 的路径。请按照以下步骤来配置该帐户。</span><span class="sxs-lookup"><span data-stu-id="57f97-133">You do not need to specify a path to RSreportserver.config. Follow these steps to configure the account.</span></span>  
  
1.  <span data-ttu-id="57f97-134">创建或选择一个有权访问为报表服务器提供数据或服务的计算机和服务器的域帐户。</span><span class="sxs-lookup"><span data-stu-id="57f97-134">Create or select a domain account that has access to computers and servers that provide data or services to a report server.</span></span> <span data-ttu-id="57f97-135">您应使用权限受到限制（如只读权限）的帐户。</span><span class="sxs-lookup"><span data-stu-id="57f97-135">You should use an account that has reduced permissions (for example, read-only permissions).</span></span>  
  
2.  <span data-ttu-id="57f97-136">打开命令提示符窗口：在 **“开始”** 菜单上，单击 **“运行”** ，键入 **cmd**，再单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="57f97-136">Open a command prompt: On the **Start** menu, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="57f97-137">键入以下命令，为本地报表服务器实例配置该帐户：</span><span class="sxs-lookup"><span data-stu-id="57f97-137">Type the following command to configure the account on a local report server instance:</span></span>  
  
     <span data-ttu-id="57f97-138">**rsconfig-e-u \<domain/username> p\<password>**</span><span class="sxs-lookup"><span data-stu-id="57f97-138">**rsconfig -e -u\<domain/username> -p\<password>**</span></span>  
  
 <span data-ttu-id="57f97-139">**rsconfig -e** 支持其他参数。</span><span class="sxs-lookup"><span data-stu-id="57f97-139">**rsconfig -e** supports additional arguments.</span></span> <span data-ttu-id="57f97-140">若要获取有关语法的详细信息和查看命令示例，请参阅 SQL Server 联机丛书中的 [rsconfig 配置工具 (SSRS)](../tools/rsconfig-utility-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="57f97-140">For more information about syntax and to view command examples, see [rsconfig Utility &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md) in SQL Server Books Online.</span></span>  
  
### <a name="how-account-information-is-stored"></a><span data-ttu-id="57f97-141">帐户信息的存储方式</span><span class="sxs-lookup"><span data-stu-id="57f97-141">How Account Information is Stored</span></span>  
 <span data-ttu-id="57f97-142">设置帐户后，将在本地或远程报表服务器实例上的 RSreportserver.config 文件中以加密值的形式指定以下设置：</span><span class="sxs-lookup"><span data-stu-id="57f97-142">When you set the account, the following settings are specified as encrypted values in the RSreportserver.config file on a local or remote report server instance:</span></span>  
  
```  
<UnattendedExecutionAccount>  
     <UserName></UserName>  
     <Password></Password>  
     <Domain></Domain>  
</UnattendedExecutionAccount>  
```  
  
 <span data-ttu-id="57f97-143">设置值后，将无法通过解密以纯文本的形式查看这些值。</span><span class="sxs-lookup"><span data-stu-id="57f97-143">Once you set the values, you cannot decrypt them to view the values in plain text.</span></span> <span data-ttu-id="57f97-144">如果输错了值或忘记了指定的值，则必须使用 Reporting Services 配置工具或运行 **rsconfig -e** 重新设置。</span><span class="sxs-lookup"><span data-stu-id="57f97-144">If you mistype the values or forget the values you specified, you must use the Reporting Services Configuration tool or run **rsconfig -e** to start over.</span></span>  
  
## <a name="how-to-use-the-unattended-report-processing-account"></a><span data-ttu-id="57f97-145">无人参与的报表处理帐户的使用方法</span><span class="sxs-lookup"><span data-stu-id="57f97-145">How to Use the Unattended Report Processing Account</span></span>  
 <span data-ttu-id="57f97-146">若要检索图像文件，报表服务器将自动使用该帐户，您不需要执行任何具体操作。</span><span class="sxs-lookup"><span data-stu-id="57f97-146">To retrieve image files, the report server uses the account automatically and no specific action is required on your part.</span></span> <span data-ttu-id="57f97-147">若要使用此帐户连接到为报表提供数据的外部数据源，则必须在报表数据源或共享数据源的“数据源属性”页中指定 **“凭据类型”** 选项：</span><span class="sxs-lookup"><span data-stu-id="57f97-147">To use the account to connect to external data sources that provide data to reports, you must specify a **Credential Type** option in the data source properties page of the report data source or shared data source:</span></span>  
  
-   <span data-ttu-id="57f97-148">在报表管理器或 SharePoint 站点中，选择 **“不需要凭据”** 选项。</span><span class="sxs-lookup"><span data-stu-id="57f97-148">In Report Manager or on a SharePoint site, select the **Credentials are not required** option.</span></span>  
  
 <span data-ttu-id="57f97-149">无人参与的报表处理帐户主要用于连接到外部服务器，而不是用作数据库服务器的登录名。</span><span class="sxs-lookup"><span data-stu-id="57f97-149">The unattended report processing account is used primarily to connect to external servers, and not as a login to database servers.</span></span> <span data-ttu-id="57f97-150">如果要使用此帐户凭据登录到数据库，则必须在连接字符串中指定凭据。</span><span class="sxs-lookup"><span data-stu-id="57f97-150">If you want to use the account credentials to log in to a database, you must specify credentials in the connection string.</span></span> <span data-ttu-id="57f97-151">如果数据库服务器支持 Windows 集成安全性，并且用于无人参与报表处理的帐户拥有数据库读取权限，则可以指定 **Integrated Security=SSPI** 。</span><span class="sxs-lookup"><span data-stu-id="57f97-151">You can specify **Integrated Security=SSPI** if the database server supports Windows integrated security and the account used for unattended report processing has permission to read the database.</span></span> <span data-ttu-id="57f97-152">否则，必须在连接字符串中输入用户名和密码，该字符串对拥有数据源连接属性编辑权限的任何用户均显示为明文形式。</span><span class="sxs-lookup"><span data-stu-id="57f97-152">Otherwise, you must enter the user name and password in the connection string, where it appears in clear text to any user who has permission to edit data source connection properties.</span></span>  
  
 <span data-ttu-id="57f97-153">虽然系统不会阻止您使用无人参与的报表处理帐户在建立连接后检索数据，但是不建议这样做。</span><span class="sxs-lookup"><span data-stu-id="57f97-153">Although you are not prevented from using the unattended report processing account to retrieve data after the connection is made, doing so is not recommended.</span></span> <span data-ttu-id="57f97-154">该帐户应该用于非常具体的功能。</span><span class="sxs-lookup"><span data-stu-id="57f97-154">The account is supposed to be used for very specific functions.</span></span> <span data-ttu-id="57f97-155">如果使用该帐户检索数据，则有违本意。</span><span class="sxs-lookup"><span data-stu-id="57f97-155">If you use it to retrieve data, you undermine the purpose for which it is intended.</span></span>  
  
## <a name="how-to-maintain-the-unattended-report-processing-account"></a><span data-ttu-id="57f97-156">无人参与的报表处理帐户的维护方法</span><span class="sxs-lookup"><span data-stu-id="57f97-156">How to Maintain the Unattended Report Processing Account</span></span>  
 <span data-ttu-id="57f97-157">定义此帐户后，必须确保不断更新此帐户和密码。</span><span class="sxs-lookup"><span data-stu-id="57f97-157">Once you define the account, you must ensure that the account and password are kept up to date.</span></span> <span data-ttu-id="57f97-158">可以使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具来更新用于存储此帐户相关信息的配置设置。</span><span class="sxs-lookup"><span data-stu-id="57f97-158">You can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to update the configuration settings that store information about this account.</span></span>  
  
1.  <span data-ttu-id="57f97-159">启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具，然后连接到要配置的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="57f97-159">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="57f97-160">在“执行帐户”页上，确认已选中 **“指定执行帐户”** 。</span><span class="sxs-lookup"><span data-stu-id="57f97-160">On the Execution Account page, verify that **Specify an execution account** is selected.</span></span>  
  
3.  <span data-ttu-id="57f97-161">键入新帐户或密码，再次键入密码，然后单击 **“应用”**。</span><span class="sxs-lookup"><span data-stu-id="57f97-161">Type the new account or password, retype the password, and then click **Apply**.</span></span>  
  
## <a name="how-to-delete-the-unattended-report-processing-account"></a><span data-ttu-id="57f97-162">无人参与的报表处理帐户的删除方法</span><span class="sxs-lookup"><span data-stu-id="57f97-162">How to Delete the Unattended Report Processing Account</span></span>  
 <span data-ttu-id="57f97-163">如果您不需要使用该帐户，则可以将其删除以避免日常的帐户维护任务。</span><span class="sxs-lookup"><span data-stu-id="57f97-163">If you are not using the account, you can delete it to avoid routine account maintenance tasks.</span></span>  
  
1.  <span data-ttu-id="57f97-164">启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具，然后连接到要配置的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="57f97-164">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="57f97-165">在“执行帐户”页上，清除 **“指定执行帐户”**。</span><span class="sxs-lookup"><span data-stu-id="57f97-165">On the Execution Account page, clear **Specify an execution account**.</span></span>  
  
3.  <span data-ttu-id="57f97-166">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="57f97-166">Click **Apply**.</span></span>  
  
 <span data-ttu-id="57f97-167">将从 RSReportServer.config 文件中删除此帐户的信息。</span><span class="sxs-lookup"><span data-stu-id="57f97-167">The account information is removed from the RSReportServer.config file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57f97-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57f97-168">See Also</span></span>  
 [<span data-ttu-id="57f97-169">Reporting Services 配置管理器 &#40;del&#41;</span><span class="sxs-lookup"><span data-stu-id="57f97-169">Reporting Services Configuration Manager &#40;del&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
