---
title: 删除和重新创建加密密钥（SSRS 配置管理器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- re-creating encryption keys
- encryption keys [Reporting Services]
- deleting encryption keys
- symmetric keys [Reporting Services]
- removing encryption keys
- resetting encryption keys
ms.assetid: 201afe5f-acc9-4a37-b5ec-121dc7df2a61
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8fa5138e4bbb84395bad79a272d2bde31389396b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694305"
---
# <a name="delete-and-re-create-encryption-keys--ssrs-configuration-manager"></a><span data-ttu-id="ec34b-102">删除和重新创建加密密钥（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="ec34b-102">Delete and Re-create Encryption Keys  (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="ec34b-103">删除和重新创建加密密钥不属于加密密钥例行维护活动。</span><span class="sxs-lookup"><span data-stu-id="ec34b-103">Deleting and re-creating encryption keys are activities that fall outside of routine encryption key maintenance.</span></span> <span data-ttu-id="ec34b-104">您可以为了响应对报表服务器的特定威胁来执行这些任务，或者当无法访问报表服务器数据库时作为最后一种解决手段来执行这些任务。</span><span class="sxs-lookup"><span data-stu-id="ec34b-104">You perform these tasks in response to a specific threat to your report server, or as a last resort when you can no longer access a report server database.</span></span>  
  
-   <span data-ttu-id="ec34b-105">当确信现有对称密钥的安全受到威胁时，应重新创建对称密钥。</span><span class="sxs-lookup"><span data-stu-id="ec34b-105">Re-create the symmetric key when you believe the existing symmetric key is compromised.</span></span> <span data-ttu-id="ec34b-106">作为安全性方面的最佳做法，您还可以定期重新创建密钥。</span><span class="sxs-lookup"><span data-stu-id="ec34b-106">You can also re-create the key on a regular basis as a security best practice.</span></span>  
  
-   <span data-ttu-id="ec34b-107">当无法还原对称密钥时，应删除现有加密密钥和不可用的加密内容。</span><span class="sxs-lookup"><span data-stu-id="ec34b-107">Delete existing encryption keys and unusable encrypted content when you cannot restore the symmetric key.</span></span>  
  
## <a name="re-creating-encryption-keys"></a><span data-ttu-id="ec34b-108">重新创建加密密钥</span><span class="sxs-lookup"><span data-stu-id="ec34b-108">Re-creating Encryption Keys</span></span>  
 <span data-ttu-id="ec34b-109">如果确认对称密钥已泄露给未经授权的用户，或者报表服务器遭到攻击，作为一种防范措施，您想要重置对称密钥，那么可以重新创建对称密钥。</span><span class="sxs-lookup"><span data-stu-id="ec34b-109">If you have evidence that the symmetric key is known to unauthorized users, or if your report server has been under attack and you want to reset the symmetric key as a precaution, you can re-create the symmetric key.</span></span> <span data-ttu-id="ec34b-110">当重新创建对称密钥时，将使用新值对所有加密值重新进行加密。</span><span class="sxs-lookup"><span data-stu-id="ec34b-110">When you re-create the symmetric key, all encrypted values will be re-encrypted using the new value.</span></span> <span data-ttu-id="ec34b-111">如果在扩展部署中运行了多个报表服务器，则对称密钥的所有副本都将更新为新值。</span><span class="sxs-lookup"><span data-stu-id="ec34b-111">If you are running multiple report servers in a scale-out deployment, all copies of the symmetric key will be updated to the new value.</span></span> <span data-ttu-id="ec34b-112">报表服务器使用可用的公钥更新部署中每一台服务器的对称密钥。</span><span class="sxs-lookup"><span data-stu-id="ec34b-112">The report server uses the public keys available to it to update the symmetric key for each server in the deployment.</span></span>  
  
 <span data-ttu-id="ec34b-113">只有在报表服务器处于工作状态时，才能重新创建对称密钥。</span><span class="sxs-lookup"><span data-stu-id="ec34b-113">You can only re-create the symmetric key when the report server is in a working state.</span></span> <span data-ttu-id="ec34b-114">重新创建加密密钥以及重新对内容进行加密将会中断服务器的操作。</span><span class="sxs-lookup"><span data-stu-id="ec34b-114">Re-creating the encryption keys and re-encrypting content disrupts server operations.</span></span> <span data-ttu-id="ec34b-115">在进行重新加密时，必须将服务器脱机。</span><span class="sxs-lookup"><span data-stu-id="ec34b-115">You must take the server offline while re-encryption is underway.</span></span> <span data-ttu-id="ec34b-116">在重新加密过程中，不应该向报表服务器发送请求。</span><span class="sxs-lookup"><span data-stu-id="ec34b-116">There should be no requests made to the report server during re-encryption.</span></span>  
  
 <span data-ttu-id="ec34b-117">可以使用 Reporting Services 配置工具或 **rskeymgmt** 实用工具重置对称密钥和加密的数据。</span><span class="sxs-lookup"><span data-stu-id="ec34b-117">You can use the Reporting Services Configuration tool or the **rskeymgmt** utility to reset the symmetric key and encrypted data.</span></span> <span data-ttu-id="ec34b-118">有关如何创建对称密钥的详细信息，请参阅[初始化报表服务器（SSRS 配置管理器）](ssrs-encryption-keys-initialize-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ec34b-118">For more information about how the symmetric key is created, see [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-initialize-a-report-server.md).</span></span>  
  
#### <a name="how-to-re-create-encryption-keys-reporting-services-configuration-tool"></a><span data-ttu-id="ec34b-119">如何重新创建加密密钥（Reporting Services 配置工具）</span><span class="sxs-lookup"><span data-stu-id="ec34b-119">How to re-create encryption keys (Reporting Services Configuration Tool)</span></span>  
  
1.  <span data-ttu-id="ec34b-120">通过修改 rsreportserver.config 文件中的 `IsWebServiceEnabled` 属性禁用报表服务器 Web 服务和 HTTP 访问。</span><span class="sxs-lookup"><span data-stu-id="ec34b-120">Disable the Report Server Web service and HTTP access by modifying the `IsWebServiceEnabled` property in the rsreportserver.config file.</span></span> <span data-ttu-id="ec34b-121">此步骤可暂时停止将身份验证请求发送到报表服务器而不会完全关闭服务器。</span><span class="sxs-lookup"><span data-stu-id="ec34b-121">This step temporarily stops authentication requests from being sent to the report server without completely shutting down the server.</span></span> <span data-ttu-id="ec34b-122">您必须具有最低限度的服务，以便可以重新创建密钥。</span><span class="sxs-lookup"><span data-stu-id="ec34b-122">You must have minimal service so that you can recreate the keys.</span></span>  
  
     <span data-ttu-id="ec34b-123">如果要为报表服务器扩展部署重新创建加密密钥，请对该部署中的所有实例禁用此属性。</span><span class="sxs-lookup"><span data-stu-id="ec34b-123">If you are recreating encryption keys for a report server scale-out deployment, disable this property on all instances in the deployment.</span></span>  
  
    1.  <span data-ttu-id="ec34b-124">打开 Windows 资源管理器，导航到 *drive*:\Program Files\Microsoft SQL Server\\*report_server_instance*\Reporting Services。</span><span class="sxs-lookup"><span data-stu-id="ec34b-124">Open Windows Explorer and navigate to *drive*:\Program Files\Microsoft SQL Server\\*report_server_instance*\Reporting Services.</span></span> <span data-ttu-id="ec34b-125">将 *drive* 替换为你的驱动器号，并将 *report_server_instance* 替换为与要禁用其 Web 服务和 HTTP 访问的报表服务器实例对应的文件夹名称。</span><span class="sxs-lookup"><span data-stu-id="ec34b-125">Replace *drive* with your drive letter and *report_server_instance* with the folder name that corresponds to the report server instance for which you want to disable the Web service and HTTP access.</span></span> <span data-ttu-id="ec34b-126">例如，C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services。</span><span class="sxs-lookup"><span data-stu-id="ec34b-126">For example, C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services.</span></span>  
  
    2.  <span data-ttu-id="ec34b-127">打开 rsreportserver.config 文件。</span><span class="sxs-lookup"><span data-stu-id="ec34b-127">Open the rsreportserver.config file.</span></span>  
  
    3.  <span data-ttu-id="ec34b-128">对于 `IsWebServiceEnabled` 属性，指定为 `False`，然后保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="ec34b-128">For the `IsWebServiceEnabled` property, specify `False`, and then save your changes.</span></span>  
  
2.  <span data-ttu-id="ec34b-129">启动 Reporting Services 配置工具，再连接到要配置的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="ec34b-129">Start the Reporting Services Configuration tool, and then connect to the report server instance you want to configure.</span></span>  
  
3.  <span data-ttu-id="ec34b-130">在“加密密钥”页上，单击 **“更改”**。</span><span class="sxs-lookup"><span data-stu-id="ec34b-130">On the Encryption Keys page, click **Change**.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="ec34b-131">重新启动报表服务器 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="ec34b-131">Restart the Report Server Windows service.</span></span> <span data-ttu-id="ec34b-132">如果要为扩展部署重新创建加密密钥，请在所有实例上重新启动该服务。</span><span class="sxs-lookup"><span data-stu-id="ec34b-132">If you are recreating encryption keys for a scale-out deployment, restart the service on all instances.</span></span>  
  
5.  <span data-ttu-id="ec34b-133">通过修改 rsreportserver.config 文件中的 `IsWebServiceEnabled` 属性，重新启用 Web 服务和 HTTP 访问。</span><span class="sxs-lookup"><span data-stu-id="ec34b-133">Re-enable the Web service and HTTP access by modifying the `IsWebServiceEnabled` property in the rsreportserver.config file.</span></span> <span data-ttu-id="ec34b-134">如果使用的是扩展部署，请对所有实例执行此操作。</span><span class="sxs-lookup"><span data-stu-id="ec34b-134">Do this for all instances if you are working with a scale out deployment.</span></span>  
  
#### <a name="how-to-re-create-encryption-keys-rskeymgmt"></a><span data-ttu-id="ec34b-135">如何重新创建加密密钥 (rskeymgmt)</span><span class="sxs-lookup"><span data-stu-id="ec34b-135">How to re-create encryption keys (rskeymgmt)</span></span>  
  
1.  <span data-ttu-id="ec34b-136">禁用报表服务器 Web 服务和 HTTP 访问。</span><span class="sxs-lookup"><span data-stu-id="ec34b-136">Disable the Report Server Web service and HTTP access.</span></span> <span data-ttu-id="ec34b-137">使用以上过程中的说明停止 Web 服务操作。</span><span class="sxs-lookup"><span data-stu-id="ec34b-137">Use the instructions in the previous procedure to stop Web service operations.</span></span>  
  
2.  <span data-ttu-id="ec34b-138">在承载报表服务器的计算机上本地运行 **rskeymgmt.exe** 。</span><span class="sxs-lookup"><span data-stu-id="ec34b-138">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="ec34b-139">使用 `-s` 参数重置对称密钥。</span><span class="sxs-lookup"><span data-stu-id="ec34b-139">Use the `-s` argument to reset the symmetric key.</span></span> <span data-ttu-id="ec34b-140">不需要其他参数：</span><span class="sxs-lookup"><span data-stu-id="ec34b-140">No other arguments are required:</span></span>  
  
    ```  
    rskeymgmt -s  
    ```  
  
3.  <span data-ttu-id="ec34b-141">重新启动 Windows 服务，并启用 Web 服务操作。</span><span class="sxs-lookup"><span data-stu-id="ec34b-141">Restart the Windows service and enable Web service operations.</span></span>  
  
## <a name="deleting-unusable-encrypted-content"></a><span data-ttu-id="ec34b-142">删除无用的加密内容</span><span class="sxs-lookup"><span data-stu-id="ec34b-142">Deleting Unusable Encrypted Content</span></span>  
 <span data-ttu-id="ec34b-143">如果由于某些原因无法还原加密密钥，报表服务器将永远无法解密和使用由该密钥加密的所有数据。</span><span class="sxs-lookup"><span data-stu-id="ec34b-143">If for some reason you cannot restore the encryption key, the report server will never be able to decrypt and use any data that is encrypted with that key.</span></span> <span data-ttu-id="ec34b-144">若要将报表服务器还原到工作状态，必须删除当前存储在报表服务器数据库中的加密值，然后手动重新指定需要的值。</span><span class="sxs-lookup"><span data-stu-id="ec34b-144">To return the report server to a working state, you must delete the encrypted values that are currently stored in the report server database and then manually re-specify the values you need.</span></span>  
  
 <span data-ttu-id="ec34b-145">删除加密密钥会将所有对称密钥信息从报表服务器数据库中删除，并会删除所有加密内容。</span><span class="sxs-lookup"><span data-stu-id="ec34b-145">Deleting the encryption keys removes all symmetric key information from the report server database and deletes any encrypted content.</span></span> <span data-ttu-id="ec34b-146">所有未加密的数据都将保持不变；只有加密内容被删除。</span><span class="sxs-lookup"><span data-stu-id="ec34b-146">All unencrypted data is left intact; only encrypted content is removed.</span></span> <span data-ttu-id="ec34b-147">删除加密密钥时，报表服务器通过添加新的对称密钥自动对自身进行重新初始化。</span><span class="sxs-lookup"><span data-stu-id="ec34b-147">When you delete the encryption keys, the report server re-initializes itself automatically by adding a new symmetric key.</span></span> <span data-ttu-id="ec34b-148">删除加密内容时，会出现以下情况：</span><span class="sxs-lookup"><span data-stu-id="ec34b-148">The following occurs when you delete encrypted content:</span></span>  
  
-   <span data-ttu-id="ec34b-149">共享数据源中的连接字符串被删除。</span><span class="sxs-lookup"><span data-stu-id="ec34b-149">Connection strings in shared data sources are deleted.</span></span> <span data-ttu-id="ec34b-150">运行报表的用户得到错误消息“ConnectionString 属性尚未初始化”。</span><span class="sxs-lookup"><span data-stu-id="ec34b-150">Users who run reports get the error "The ConnectionString property has not been initialized."</span></span>  
  
-   <span data-ttu-id="ec34b-151">存储的凭据被删除。</span><span class="sxs-lookup"><span data-stu-id="ec34b-151">Stored credentials are deleted.</span></span> <span data-ttu-id="ec34b-152">报表和共享数据源重新配置为使用所提示的凭据。</span><span class="sxs-lookup"><span data-stu-id="ec34b-152">Reports and shared data sources are reconfigured to use prompted credentials.</span></span>  
  
-   <span data-ttu-id="ec34b-153">基于模型（且需要共享数据源配置为使用存储的凭据或不使用凭据）的报表将不会运行。</span><span class="sxs-lookup"><span data-stu-id="ec34b-153">Reports that are based on models (and require shared data sources configured with stored or no credentials) will not run.</span></span>  
  
-   <span data-ttu-id="ec34b-154">订阅被停用。</span><span class="sxs-lookup"><span data-stu-id="ec34b-154">Subscriptions are deactivated.</span></span>  
  
 <span data-ttu-id="ec34b-155">加密内容一旦被删除，便无法恢复。</span><span class="sxs-lookup"><span data-stu-id="ec34b-155">Once you delete encrypted content, you cannot recover it.</span></span> <span data-ttu-id="ec34b-156">必须重新指定连接字符串和存储的凭据，并且必须激活订阅。</span><span class="sxs-lookup"><span data-stu-id="ec34b-156">You must re-specify connection strings and stored credentials, and you must activate subscriptions.</span></span>  
  
 <span data-ttu-id="ec34b-157">可以使用 Reporting Services 配置工具或 **rskeymgmt** 实用工具删除值。</span><span class="sxs-lookup"><span data-stu-id="ec34b-157">You can use the Reporting Services Configuration tool or the **rskeymgmt** utility to remove the values.</span></span>  
  
#### <a name="how-to-delete-encryption-keys-reporting-services-configuration-tool"></a><span data-ttu-id="ec34b-158">如何删除加密密钥（Reporting Services 配置工具）</span><span class="sxs-lookup"><span data-stu-id="ec34b-158">How to delete encryption keys (Reporting Services Configuration Tool)</span></span>  
  
1.  <span data-ttu-id="ec34b-159">启动 Reporting Services 配置工具，再连接到要配置的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="ec34b-159">Start the Reporting Services Configuration tool, and then connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="ec34b-160">单击 **“加密密钥”**，再单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="ec34b-160">Click **Encryption Keys**, and then click **Delete**.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  <span data-ttu-id="ec34b-161">重新启动报表服务器 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="ec34b-161">Restart the Report Server Windows service.</span></span> <span data-ttu-id="ec34b-162">对于扩展部署，应对所有报表服务器实例执行此操作。</span><span class="sxs-lookup"><span data-stu-id="ec34b-162">For a scale-out deployment, do this on all report server instances.</span></span>  
  
#### <a name="how-to-delete-encryption-keys-rskeymmgt"></a><span data-ttu-id="ec34b-163">如何删除加密密钥 (rskeymmgt)</span><span class="sxs-lookup"><span data-stu-id="ec34b-163">How to delete encryption keys (rskeymmgt)</span></span>  
  
1.  <span data-ttu-id="ec34b-164">在承载报表服务器的计算机上本地运行 **rskeymgmt.exe** 。</span><span class="sxs-lookup"><span data-stu-id="ec34b-164">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="ec34b-165">必须使用 **-d** 应用参数。</span><span class="sxs-lookup"><span data-stu-id="ec34b-165">You must use the **-d** apply argument.</span></span> <span data-ttu-id="ec34b-166">下面的示例说明了必须指定的参数：</span><span class="sxs-lookup"><span data-stu-id="ec34b-166">The following example illustrates the argument you must specify:</span></span>  
  
    ```  
    rskeymgmt -d  
    ```  
  
2.  <span data-ttu-id="ec34b-167">重新启动报表服务器 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="ec34b-167">Restart the Report Server Windows service.</span></span> <span data-ttu-id="ec34b-168">对于扩展部署，应对所有报表服务器实例执行此操作。</span><span class="sxs-lookup"><span data-stu-id="ec34b-168">For a scale-out deployment, do this on all report server instances.</span></span>  
  
#### <a name="how-to-re-specify-encrypted-values"></a><span data-ttu-id="ec34b-169">如何重新指定加密值</span><span class="sxs-lookup"><span data-stu-id="ec34b-169">How to re-specify encrypted values</span></span>  
  
1.  <span data-ttu-id="ec34b-170">对于每个共享数据源，必须重新键入连接字符串。</span><span class="sxs-lookup"><span data-stu-id="ec34b-170">For each shared data source, you must retype the connection string.</span></span>  
  
2.  <span data-ttu-id="ec34b-171">对于每个使用存储的凭据的报表和共享数据源，必须重新键入用户名和密码，然后再保存。</span><span class="sxs-lookup"><span data-stu-id="ec34b-171">For each report and shared data source that uses stored credentials, you must retype the user name and password, and then save.</span></span> <span data-ttu-id="ec34b-172">有关详细信息，请参阅 [“联机丛书”中的](../../integration-services/connection-manager/data-sources.md) 指定报表数据源的凭据和连接信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ec34b-172">For more information, see [Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
3.  <span data-ttu-id="ec34b-173">对于每个数据驱动订阅，打开每个订阅，再重新键入订阅数据库的凭据。</span><span class="sxs-lookup"><span data-stu-id="ec34b-173">For each data-driven subscription, open each subscription and retype the credentials to the subscription database.</span></span>  
  
4.  <span data-ttu-id="ec34b-174">对于使用加密数据的订阅（其中包括文件共享传递扩展插件和使用加密的任何第三方传递扩展插件），打开每个订阅，再重新键入凭据。</span><span class="sxs-lookup"><span data-stu-id="ec34b-174">For subscriptions that use encrypted data (this includes the File Share delivery extension and any third-party delivery extension that uses encryption), open each subscription and retype credentials.</span></span> <span data-ttu-id="ec34b-175">使用报表服务器电子邮件传递的订阅不使用加密数据，因而不受密钥更改的影响。</span><span class="sxs-lookup"><span data-stu-id="ec34b-175">Subscriptions that use Report Server e-mail delivery do not use encrypted data and are unaffected by the key change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec34b-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ec34b-176">See Also</span></span>  
 <span data-ttu-id="ec34b-177">[&#40;SSRS Configuration Manager 中配置和管理加密密钥&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="ec34b-177">[Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span></span>  
 [<span data-ttu-id="ec34b-178">存储加密的 Report Server 数据（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="ec34b-178">Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-store-encrypted-report-server-data.md)  
  
  
