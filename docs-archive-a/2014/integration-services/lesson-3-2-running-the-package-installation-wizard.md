---
title: 步骤 2：运行包安装向导 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f91fbb89-4626-4c47-b96d-56052dc45861
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9492f9ecc843ef475a3c5d32cde2952e0ff498fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682955"
---
# <a name="step-2-running-the-package-installation-wizard"></a><span data-ttu-id="84551-102">步骤 2：运行包安装向导</span><span class="sxs-lookup"><span data-stu-id="84551-102">Step 2: Running the Package Installation Wizard</span></span>
  <span data-ttu-id="84551-103">在此任务中，将运行包安装向导，将包从 Deployment Tutorial 项目部署到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="84551-103">In this task, you will run the Package Installation Wizard to deploy the packages from the Deployment Tutorial project to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="84551-104">只能将包安装在 msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库的 sysssispackages 表中，而部署捆绑包括的支持文件将被部署到文件系统。</span><span class="sxs-lookup"><span data-stu-id="84551-104">Only packages can be installed in the sysssispackages table in the msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, the supporting files that the deployment bundle includes will be deployed to the file system.</span></span>  
  
 <span data-ttu-id="84551-105">包安装向导将引导您完成安装和配置包的步骤。</span><span class="sxs-lookup"><span data-stu-id="84551-105">The Package Installation Wizard will guide you through the steps to install and configure the packages.</span></span> <span data-ttu-id="84551-106">将包安装到目标计算机（向其复制部署捆绑的计算机）上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="84551-106">You will install the packages to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the destination computer (the computer to which you copied the deployment bundle.</span></span> <span data-ttu-id="84551-107">您还将创建文件夹 C:\DeploymentTutorialInstall，向导将在该文件夹中安装非包文件。</span><span class="sxs-lookup"><span data-stu-id="84551-107">You will also create a folder, C:\DeploymentTutorialInstall, in which the wizard will install the non-package files.</span></span>  
  
 <span data-ttu-id="84551-108">在前面的课程中，已经修改教程中的包，以便使用配置。</span><span class="sxs-lookup"><span data-stu-id="84551-108">In an earlier lesson, you modified the packages in the tutorial to use configurations.</span></span> <span data-ttu-id="84551-109">使用包安装向导，您将编辑这些配置，使得包能够在安装到的环境中成功运行。</span><span class="sxs-lookup"><span data-stu-id="84551-109">Using the Package Installation Wizard, you will edit these configurations to enable packages to run successfully in the installed-to environment.</span></span>  
  
### <a name="to-install-the-packages"></a><span data-ttu-id="84551-110">安装包</span><span class="sxs-lookup"><span data-stu-id="84551-110">To install the packages</span></span>  
  
1.  <span data-ttu-id="84551-111">在目标计算机上，找到部署捆绑。</span><span class="sxs-lookup"><span data-stu-id="84551-111">On the destination computer, locate the deployment bundle.</span></span>  
  
     <span data-ttu-id="84551-112">如果将默认值 bin\Deployment 用作部署实用工具的位置，则部署捆绑是 Deployment Tutorial 项目中的 Deployment 文件夹。</span><span class="sxs-lookup"><span data-stu-id="84551-112">If you used the default value-bin\Deployment-as the location of the deployment utility, the deployment bundle is the Deployment folder in the Deployment Tutorial project.</span></span>  
  
2.  <span data-ttu-id="84551-113">在 Deployment 文件夹中，双击清单文件 Deployment Tutorial.SSISDeploymentManifest。</span><span class="sxs-lookup"><span data-stu-id="84551-113">In the Deployment folder, double-click the manifest file, Deployment Tutorial.SSISDeploymentManifest.</span></span>  
  
3.  <span data-ttu-id="84551-114">在包安装向导的“欢迎”页中，单击“下一步”  。</span><span class="sxs-lookup"><span data-stu-id="84551-114">On the Welcome page of the Package Installation Wizard, click **Next**.</span></span>  
  
4.  <span data-ttu-id="84551-115">在“部署 SSIS 包”页上，选择“SQL Server 部署”  选项，选中“安装后验证包”  复选框，再单击“下一步”  。</span><span class="sxs-lookup"><span data-stu-id="84551-115">On the Deploy SSIS Packages page, select the **SQL Server deployment** option, select the **Validate packages after installation** check box, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="84551-116">在“指定目标 SQL Server”页上，在“服务器名称”框中指定 **(local)** 。</span><span class="sxs-lookup"><span data-stu-id="84551-116">On the Specify Target SQL Server page, specify **(local**), in the **Server name** box.</span></span>  
  
6.  <span data-ttu-id="84551-117">如果 SQL Server 的实例支持 Windows 身份验证，请选择“使用 Windows 身份验证”  ；否则，选择“使用 SQL Server 身份验证”  ，并提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="84551-117">If the instance of SQL Server supports Windows Authentication, select **Use Windows Authentication**; otherwise, select **Use SQL Server Authentication** and provide a user name and a password.</span></span>  
  
7.  <span data-ttu-id="84551-118">验证是否清除了“依靠服务器存储进行加密”  复选框。</span><span class="sxs-lookup"><span data-stu-id="84551-118">Verify that the **Rely on server storage for encryption** check box is cleared.</span></span>  
  
8.  <span data-ttu-id="84551-119">单击“下一步” </span><span class="sxs-lookup"><span data-stu-id="84551-119">Click **Next.**</span></span>  
  
9. <span data-ttu-id="84551-120">在“选择安装文件夹”页上，单击“浏览”  。</span><span class="sxs-lookup"><span data-stu-id="84551-120">On the Select Installation Folder page, click **Browse.**</span></span>  
  
10. <span data-ttu-id="84551-121">在“浏览文件夹”  对话框中，展开“我的电脑”  ，再单击“本地磁盘 (C:)”  。</span><span class="sxs-lookup"><span data-stu-id="84551-121">In the **Browse For Folder** dialog box, expand **My Computer** and then click **Local Disk (C:)**.</span></span>  
  
11. <span data-ttu-id="84551-122">单击“新建文件夹”  ，并将新文件夹的默认名称“新建文件夹”  替换为 **DeploymentTutorialInstall**。</span><span class="sxs-lookup"><span data-stu-id="84551-122">Click **Make New Folder** and replace the default name of the new folder, **New Folder**, with **DeploymentTutorialInstall**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="84551-123">在配置所使用的环境变量的值中，将引用此名称。</span><span class="sxs-lookup"><span data-stu-id="84551-123">This name is referenced in the value of the environment variables that configurations use.</span></span> <span data-ttu-id="84551-124">文件夹的名称与引用必须匹配，否则包无法运行。</span><span class="sxs-lookup"><span data-stu-id="84551-124">The name of the folder and the reference must match or the package cannot run.</span></span>  
  
12. <span data-ttu-id="84551-125">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="84551-125">Click **OK**.</span></span>  
  
13. <span data-ttu-id="84551-126">在“选择安装文件夹”页上，验证“文件夹”框中是否包含 **C:\DeploymentTutorialInstall**，再单击“下一步”  。</span><span class="sxs-lookup"><span data-stu-id="84551-126">On the Select Installation Folder page, verify that the Folder box contains **C:\DeploymentTutorialInstall** and then click **Next**.</span></span>  
  
14. <span data-ttu-id="84551-127">在“确认安装”页上，单击“下一步”  。</span><span class="sxs-lookup"><span data-stu-id="84551-127">On the Confirm Installation page, click **Next**.</span></span>  
  
     <span data-ttu-id="84551-128">向导将安装包。</span><span class="sxs-lookup"><span data-stu-id="84551-128">The wizard installs the packages.</span></span> <span data-ttu-id="84551-129">完成安装后，将打开“配置包”页。</span><span class="sxs-lookup"><span data-stu-id="84551-129">After installation is completed, the Configure Packages page opens.</span></span>  
  
15. <span data-ttu-id="84551-130">在“配置包”页上，验证“配置文件”  框是否列出了 datatransferconfig.dtsconfig 和 loadxmldataconfig.dtsconfig。</span><span class="sxs-lookup"><span data-stu-id="84551-130">On the Configure Packages page, verify that the **Configuration file** box lists datatransferconfig.dtsconfig and loadxmldataconfig.dtsconfig.</span></span>  
  
16. <span data-ttu-id="84551-131">在“配置文件”列表中，单击 **datatransferconfig.dtsconfig**，展开“配置”框的“路径”列中的“属性”，再用下列值更新“值”列：</span><span class="sxs-lookup"><span data-stu-id="84551-131">In the **Configuration file** list, click **datatransferconfig.dtsconfig**, expand Property in the **Path** column of the **Configurations** box, and update the **Value** column with the following values:</span></span>  
  
    |<span data-ttu-id="84551-132">properties</span><span class="sxs-lookup"><span data-stu-id="84551-132">Property</span></span>|<span data-ttu-id="84551-133">值</span><span class="sxs-lookup"><span data-stu-id="84551-133">Value</span></span>|<span data-ttu-id="84551-134">更新后的值</span><span class="sxs-lookup"><span data-stu-id="84551-134">Updated Value</span></span>|  
    |--------------|-----------|-------------------|  
    |<span data-ttu-id="84551-135">\Package.Connections[Deployment Tutorial Log].Properties[ConnectionString]</span><span class="sxs-lookup"><span data-stu-id="84551-135">\Package.Connections[Deployment Tutorial Log].Properties[ConnectionString]</span></span>|<span data-ttu-id="84551-136">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages\Deployment Tutorial Log</span><span class="sxs-lookup"><span data-stu-id="84551-136">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages\Deployment Tutorial Log</span></span>|<span data-ttu-id="84551-137">C:\DeploymentTutorialInstall\Deployment Tutorial Log</span><span class="sxs-lookup"><span data-stu-id="84551-137">C:\DeploymentTutorialInstall\Deployment Tutorial Log</span></span>|  
    |<span data-ttu-id="84551-138">\Package.Connections[NewCustomers].Properties[ConnectionString]</span><span class="sxs-lookup"><span data-stu-id="84551-138">\Package.Connections[NewCustomers].Properties[ConnectionString]</span></span>|<span data-ttu-id="84551-139">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="84551-139">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\NewCustomers.txt</span></span>|<span data-ttu-id="84551-140">C:\DeploymentTutorialInstall\NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="84551-140">C:\DeploymentTutorialInstall\NewCustomers.txt</span></span>|  
  
17. <span data-ttu-id="84551-141">在“配置文件”列表中，单击 loadxmldataconfig.dtsconfig，展开“配置”框的“路径”列中的“属性”，再用下列值更新“值”列：</span><span class="sxs-lookup"><span data-stu-id="84551-141">In the **Configuration file** list, click loadxmldataconfig.dtsconfig, expand Property in the **Path** column of the **Configurations** box, and update the **Value** column with the following values:</span></span>  
  
    |<span data-ttu-id="84551-142">properties</span><span class="sxs-lookup"><span data-stu-id="84551-142">Property</span></span>|<span data-ttu-id="84551-143">值</span><span class="sxs-lookup"><span data-stu-id="84551-143">Value</span></span>|<span data-ttu-id="84551-144">更新后的值</span><span class="sxs-lookup"><span data-stu-id="84551-144">Updated Value</span></span>|  
    |--------------|-----------|-------------------|  
    |<span data-ttu-id="84551-145">\Package.LoadXMLData.Properties[[XML Source].[XMLData]]</span><span class="sxs-lookup"><span data-stu-id="84551-145">\Package.LoadXMLData.Properties[[XML Source].[XMLData]]</span></span>|<span data-ttu-id="84551-146">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xml</span><span class="sxs-lookup"><span data-stu-id="84551-146">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xml</span></span>|<span data-ttu-id="84551-147">C:\DeploymentTutorialInstall\orders.xml</span><span class="sxs-lookup"><span data-stu-id="84551-147">C:\DeploymentTutorialInstall\orders.xml</span></span>|  
    |<span data-ttu-id="84551-148">\Package.LoadXMLData.Properties[[XML Source].[XMLSchemaDefinition]]</span><span class="sxs-lookup"><span data-stu-id="84551-148">\Package.LoadXMLData.Properties[[XML Source].[XMLSchemaDefinition]]</span></span>|<span data-ttu-id="84551-149">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xsd</span><span class="sxs-lookup"><span data-stu-id="84551-149">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xsd</span></span>|<span data-ttu-id="84551-150">C:\DeploymentTutorialInstall\orders.xsd</span><span class="sxs-lookup"><span data-stu-id="84551-150">C:\DeploymentTutorialInstall\orders.xsd</span></span>|  
  
18. <span data-ttu-id="84551-151">在“包验证”页上，查看所安装的每个包的验证结果，再单击“下一步”  。</span><span class="sxs-lookup"><span data-stu-id="84551-151">On the Package Validation page, view the validation results of each package installed and then click **Next**.</span></span>  
  
     <span data-ttu-id="84551-152">由于目标计算机上环境变量的值与开发计算机上环境变量的值不同，因此会在“包验证”页上出现多个警告。</span><span class="sxs-lookup"><span data-stu-id="84551-152">Because the values of the environment variables on the destination computer differ from the values of the environment variables on the development computer, several warnings appear on the Package Validation page.</span></span> <span data-ttu-id="84551-153">您可能会看到下列四个警告：</span><span class="sxs-lookup"><span data-stu-id="84551-153">You should expect four warnings:</span></span>  
  
    -   <span data-ttu-id="84551-154">配置文件 "C:\DeploymentTutorial\DataTransferConfig.dtsConfig" 无效。</span><span class="sxs-lookup"><span data-stu-id="84551-154">The configuration file: "C:\DeploymentTutorial\DataTransferConfig.dtsConfig" is not valid.</span></span> <span data-ttu-id="84551-155">请检查此配置文件名。</span><span class="sxs-lookup"><span data-stu-id="84551-155">Check the configuration file name.</span></span>  
  
    -   <span data-ttu-id="84551-156">包中至少有一个配置条目无法加载。</span><span class="sxs-lookup"><span data-stu-id="84551-156">Failed to load at least one of the configuration entries in the package.</span></span> <span data-ttu-id="84551-157">请检查配置条目和以前的警告，查看配置失败的有关说明。</span><span class="sxs-lookup"><span data-stu-id="84551-157">Check configuration entries and previous warnings to see description of which configuration failed.</span></span>  
  
    -   <span data-ttu-id="84551-158">配置文件 "C:\DeploymentTutorial\LoadXMLDataConfig.dtsConfig" 无效。</span><span class="sxs-lookup"><span data-stu-id="84551-158">The configuration file: "C:\DeploymentTutorial\LoadXMLDataConfig.dtsConfig is not valid.</span></span> <span data-ttu-id="84551-159">请检查此配置文件名。</span><span class="sxs-lookup"><span data-stu-id="84551-159">Check the configuration file name.</span></span>  
  
    -   <span data-ttu-id="84551-160">包中至少有一个配置条目无法加载。</span><span class="sxs-lookup"><span data-stu-id="84551-160">Failed to load at least one of the configuration entries in the package.</span></span> <span data-ttu-id="84551-161">请检查配置条目和以前的警告，查看配置失败的有关说明。</span><span class="sxs-lookup"><span data-stu-id="84551-161">Check configuration entries and previous warnings to see description of which configuration failed.</span></span>  
  
     <span data-ttu-id="84551-162">这些警告不影响包的安装。</span><span class="sxs-lookup"><span data-stu-id="84551-162">These warnings do not affect package installation.</span></span>  
  
     <span data-ttu-id="84551-163">如果在“部署 SSIS 包”页上未选择“安装后验证包”  选项，则不会打开“包验证”页，而且向导不显示有关验证的安装后信息。</span><span class="sxs-lookup"><span data-stu-id="84551-163">If you did not select the **Validate packages after installation** option on the Deploy SSIS Packages page, the Package Validation pages does not open and the wizard does not display post-installation information about validation.</span></span>  
  
19. <span data-ttu-id="84551-164">在“完成包安装向导”页上，阅读安装摘要，再单击“完成”  。</span><span class="sxs-lookup"><span data-stu-id="84551-164">On the Finish the Package Installation Wizard page, read the installation summary and then click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="84551-165">此时，创建一个临时日志文件，供在包验证时使用。</span><span class="sxs-lookup"><span data-stu-id="84551-165">A temporary log file is created to use in the package validation.</span></span> <span data-ttu-id="84551-166">运行包时不使用此文件。</span><span class="sxs-lookup"><span data-stu-id="84551-166">This file is not used when the package runs.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="84551-167">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="84551-167">Next Task in Lesson</span></span>  
 [<span data-ttu-id="84551-168">步骤 3：测试已部署的包</span><span class="sxs-lookup"><span data-stu-id="84551-168">Step 3: Testing the Deployed Packages</span></span>](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
<span data-ttu-id="84551-169">![Integration Services 图标 (小型) ](media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="84551-169">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="84551-170">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="84551-170">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="84551-171">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="84551-171">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="84551-172">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="84551-172">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84551-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84551-173">See Also</span></span>  
 <span data-ttu-id="84551-174">[Integration Services 服务 &#40;SSIS 服务&#41;](service/integration-services-service-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="84551-174">[Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md) </span></span>  
 [<span data-ttu-id="84551-175">管理 Integration Services 服务</span><span class="sxs-lookup"><span data-stu-id="84551-175">Manage the Integration Services Service</span></span>](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  
