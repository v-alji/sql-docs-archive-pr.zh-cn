---
title: 包安装向导 UI 参考 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.deploymentwizard.confirminstallation.f1
- sql12.dts.deploymentwizard.deploydtspackages.f1
- sql12.dts.deploymentwizard.selectinstfolder.f1
- sql12.dts.deploymentwizard.specifytargetsqlserver.f1
- sql12.dts.deploymentwizard.welcome.f1
- sql12.dts.deploymentwizard.finish.f1
- sql12.dts.deploymentwizard.configurepackages.f1
- sql12.dts.deploymentwizard.packagevalidation.f1
helpviewer_keywords:
- Package Installer Wizard
ms.assetid: 6fca44d9-5001-4644-bcf3-c2d10a674b97
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c15b423c66891e799f7f8dcd27682036dce6d8de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688003"
---
# <a name="package-installation-wizard-ui-reference"></a><span data-ttu-id="0b0ae-102">包安装向导 UI 参考</span><span class="sxs-lookup"><span data-stu-id="0b0ae-102">Package Installation Wizard UI Reference</span></span>
  <span data-ttu-id="0b0ae-103">可以使用 **“包安装向导”** 部署 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目（包括包、所包含的杂项文件以及所有包的依赖关系）。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-103">Use the **Package Installation Wizard** to deploy a [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, including the packages and miscellaneous files it contains and any package dependencies.</span></span>  
  
 <span data-ttu-id="0b0ae-104">在部署包之前，可以先创建配置，然后再将其与包一起进行部署。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-104">Before you deploy packages, you can create configurations and then deploy them with the packages.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="0b0ae-105">在运行时使用配置来动态更新包和包对象的属性。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-105">uses configurations to dynamically update properties of packages and package objects at run time.</span></span> <span data-ttu-id="0b0ae-106">例如，通过提供将值映射到包含连接字符串的属性的配置，可在运行时动态设置 OLE DB 连接的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-106">For example, the connection string of an OLE DB connection can be set dynamically at run time by providing a configuration that maps a value to the property that contains the connection string.</span></span>  
  
 <span data-ttu-id="0b0ae-107">只有在生成 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目并创建部署实用工具后，方可运行包安装向导。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-107">You cannot run the Package Installation Wizard until you build an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project and create a deployment utility.</span></span> <span data-ttu-id="0b0ae-108">有关详细信息，请参阅 [Deploy Packages by Using the Deployment Utility](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-108">For more information, see [Deploy Packages by Using the Deployment Utility](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="0b0ae-109">以下部分介绍了该向导中的各页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-109">The following sections describe pages of the wizard.</span></span>  
  
## <a name="welcome-to-the-package-installation-wizard-page"></a><span data-ttu-id="0b0ae-110">“欢迎使用包安装向导”页</span><span class="sxs-lookup"><span data-stu-id="0b0ae-110">Welcome to the Package Installation Wizard Page</span></span>  
 <span data-ttu-id="0b0ae-111">可以使用 **“包安装向导** ”部署为其生成包部署实用工具的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-111">Use the **Package Installation Wizard** to deploy an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project for which you built a package deployment utility.</span></span>  
  
 <span data-ttu-id="0b0ae-112">**不再显示此起始页**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-112">**Do not show this starting page again**</span></span>  
 <span data-ttu-id="0b0ae-113">选择此选项可以在下次运行向导时跳过起始页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-113">Select to skip the starting page when you run the wizard again.</span></span>  
  
 <span data-ttu-id="0b0ae-114">**Next**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-114">**Next**</span></span>  
 <span data-ttu-id="0b0ae-115">转到向导的下一页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-115">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="0b0ae-116">**“完成”**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-116">**Finish**</span></span>  
 <span data-ttu-id="0b0ae-117">跳到“完成包安装向导”页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-117">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="0b0ae-118">如果返回到向导前面的页修改所选项，并指定了所有必需的选项，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-118">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="configure-packages-page"></a><span data-ttu-id="0b0ae-119">“配置包”页</span><span class="sxs-lookup"><span data-stu-id="0b0ae-119">Configure Packages Page</span></span>  
 <span data-ttu-id="0b0ae-120">可以使用 **“配置包”** 页编辑包配置。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-120">Use the **Configure Packages** page to edit package configurations.</span></span>  
  
### <a name="options"></a><span data-ttu-id="0b0ae-121">选项</span><span class="sxs-lookup"><span data-stu-id="0b0ae-121">Options</span></span>  
 <span data-ttu-id="0b0ae-122">**配置文件**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-122">**Configuration file**</span></span>  
 <span data-ttu-id="0b0ae-123">通过从列表中选择文件，可以编辑配置文件的内容。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-123">Edit the contents of a configuration file by selecting the file from the list.</span></span>  
  
 <span data-ttu-id="0b0ae-124">**相关主题：** [创建包配置](../../2014/integration-services/create-package-configurations.md)</span><span class="sxs-lookup"><span data-stu-id="0b0ae-124">**Related Topics:** [Create Package Configurations](../../2014/integration-services/create-package-configurations.md)</span></span>  
  
 <span data-ttu-id="0b0ae-125">**路径**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-125">**Path**</span></span>  
 <span data-ttu-id="0b0ae-126">查看要配置的属性的路径。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-126">View the path of the property to be configured.</span></span>  
  
 <span data-ttu-id="0b0ae-127">类型</span><span class="sxs-lookup"><span data-stu-id="0b0ae-127">**Type**</span></span>  
 <span data-ttu-id="0b0ae-128">查看属性的数据类型。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-128">View the data type of the property.</span></span>  
  
 <span data-ttu-id="0b0ae-129">**值**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-129">**Value**</span></span>  
 <span data-ttu-id="0b0ae-130">指定配置的值。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-130">Specify the value of the configuration.</span></span>  
  
 <span data-ttu-id="0b0ae-131">**Next**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-131">**Next**</span></span>  
 <span data-ttu-id="0b0ae-132">转到向导的下一页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-132">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="0b0ae-133">**“完成”**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-133">**Finish**</span></span>  
 <span data-ttu-id="0b0ae-134">跳到“完成包安装向导”页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-134">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="0b0ae-135">如果返回到向导前面的页修改所选项，并指定了所有必需的选项，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-135">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="confirm-installation-page"></a><span data-ttu-id="0b0ae-136">“确认安装”页</span><span class="sxs-lookup"><span data-stu-id="0b0ae-136">Confirm Installation Page</span></span>  
 <span data-ttu-id="0b0ae-137">可以使用 **“确认安装”** 页开始安装包，查看状态以及查看向导用于从指定项目中安装文件的信息。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-137">Use the **Confirm Installation** page to start the installation of packages, to view the status, and to view the information that the wizard will use to install files from the specified project.</span></span>  
  
 <span data-ttu-id="0b0ae-138">**Next**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-138">**Next**</span></span>  
 <span data-ttu-id="0b0ae-139">安装包及其相关文件，并在完成安装后转到下一个向导页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-139">Install the packages and their dependencies and go to the next wizard page when installation is completed.</span></span>  
  
 <span data-ttu-id="0b0ae-140">**Status**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-140">**Status**</span></span>  
 <span data-ttu-id="0b0ae-141">显示包的安装进度。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-141">Shows the progress of the package installation.</span></span>  
  
 <span data-ttu-id="0b0ae-142">**“完成”**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-142">**Finish**</span></span>  
 <span data-ttu-id="0b0ae-143">转到“完成包安装向导”页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-143">Go to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="0b0ae-144">如果返回到向导前面的页修改所选项，并指定了所有必需的选项，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-144">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all the required options.</span></span>  
  
## <a name="deploy-ssis-packages-page"></a><span data-ttu-id="0b0ae-145">“部署 SSIS 包”页</span><span class="sxs-lookup"><span data-stu-id="0b0ae-145">Deploy SSIS Packages Page</span></span>  
 <span data-ttu-id="0b0ae-146">可以使用 **“部署 SSIS 包”** 页指定 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包及其依赖关系的安装位置。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-146">Use the **Deploy SSIS Packages** page to specify where to install [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages and their dependencies.</span></span>  
  
### <a name="options"></a><span data-ttu-id="0b0ae-147">选项</span><span class="sxs-lookup"><span data-stu-id="0b0ae-147">Options</span></span>  
 <span data-ttu-id="0b0ae-148">**部署到文件系统**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-148">**File system deployment**</span></span>  
 <span data-ttu-id="0b0ae-149">将包及其依赖关系部署到文件系统内指定的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-149">Deploy packages and dependencies in a specified folder in the file system.</span></span>  
  
 <span data-ttu-id="0b0ae-150">**部署到 SQL Server**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-150">**SQL Server deployment**</span></span>  
 <span data-ttu-id="0b0ae-151">将包及其依赖关系部署到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例中。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-151">Deploy packages and dependencies in an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0b0ae-152">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在服务器之间共享包，请使用此选项。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-152">Use this option if [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shares packages between servers.</span></span> <span data-ttu-id="0b0ae-153">将所有包依赖关系安装在文件系统内指定的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-153">Any package dependencies are installed in the specified folder in the file system.</span></span>  
  
 <span data-ttu-id="0b0ae-154">**安装后验证包**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-154">**Validate packages after installation**</span></span>  
 <span data-ttu-id="0b0ae-155">指示安装后是否验证包。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-155">Indicate whether to validate packages after installation.</span></span>  
  
 <span data-ttu-id="0b0ae-156">**Next**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-156">**Next**</span></span>  
 <span data-ttu-id="0b0ae-157">转到向导的下一页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-157">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="0b0ae-158">**“完成”**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-158">**Finish**</span></span>  
 <span data-ttu-id="0b0ae-159">跳到“完成包安装向导”页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-159">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="0b0ae-160">如果返回到向导前面的页修改所选项，并指定了所有必需的选项，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-160">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="packages-validation-page"></a><span data-ttu-id="0b0ae-161">“包验证”页</span><span class="sxs-lookup"><span data-stu-id="0b0ae-161">Packages Validation Page</span></span>  
 <span data-ttu-id="0b0ae-162">可以使用 **“包验证”** 页查看包验证的进度和结果。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-162">Use the **Packages Validation** page to view the progress and results of the package validation.</span></span>  
  
 <span data-ttu-id="0b0ae-163">**Next**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-163">**Next**</span></span>  
 <span data-ttu-id="0b0ae-164">转到向导的下一页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-164">Go to the next page in the wizard.</span></span>  
  
## <a name="select-installation-folder-page"></a><span data-ttu-id="0b0ae-165">“选择安装文件夹”页</span><span class="sxs-lookup"><span data-stu-id="0b0ae-165">Select Installation Folder Page</span></span>  
 <span data-ttu-id="0b0ae-166">可以使用 **“选择安装文件夹”** 页，指定在文件系统中安装包及其依赖关系的文件夹。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-166">Use the **Select Installation Folder** page to specify the file system folder in which to install the packages and their dependencies.</span></span>  
  
### <a name="options"></a><span data-ttu-id="0b0ae-167">选项</span><span class="sxs-lookup"><span data-stu-id="0b0ae-167">Options</span></span>  
 <span data-ttu-id="0b0ae-168">**文件夹**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-168">**Folder**</span></span>  
 <span data-ttu-id="0b0ae-169">指定包及其依赖关系要复制到的路径和文件夹。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-169">Specify the path and folder in which to copy the package and its dependencies.</span></span>  
  
 <span data-ttu-id="0b0ae-170">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-170">**Browse**</span></span>  
 <span data-ttu-id="0b0ae-171">使用“查找文件夹”  对话框找到目标文件夹。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-171">Browse to the target folder by using the **Browse For Folder** dialog box.</span></span>  
  
 <span data-ttu-id="0b0ae-172">**Next**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-172">**Next**</span></span>  
 <span data-ttu-id="0b0ae-173">转到向导的下一页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-173">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="0b0ae-174">**“完成”**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-174">**Finish**</span></span>  
 <span data-ttu-id="0b0ae-175">跳到“完成包安装向导”页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-175">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="0b0ae-176">如果已经复查完前面向导页中的选项，并指定了所有必需的选项，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-176">Use this option if you have backtracked through the wizard pages to revise your choices and if have specified all of the required options.</span></span>  
  
## <a name="specify-target-sql-server-page"></a><span data-ttu-id="0b0ae-177">“指定目标 SQL Server”页</span><span class="sxs-lookup"><span data-stu-id="0b0ae-177">Specify Target SQL Server Page</span></span>  
 <span data-ttu-id="0b0ae-178">可以使用 **“指定目标 SQL Server”** 页，指定将包部署到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例的选项。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-178">Use the **Specify Target SQL Server** page to specify options for deploying the package to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="options"></a><span data-ttu-id="0b0ae-179">选项</span><span class="sxs-lookup"><span data-stu-id="0b0ae-179">Options</span></span>  
 <span data-ttu-id="0b0ae-180">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-180">**Server name**</span></span>  
 <span data-ttu-id="0b0ae-181">指定要部署包的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-181">Specify the name of the server to deploy the packages to.</span></span>  
  
 <span data-ttu-id="0b0ae-182">**Use Windows Authentication**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-182">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="0b0ae-183">指定是否使用 Windows 身份验证来登录到服务器。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-183">Specify whether to use Windows Authentication to log on to the server.</span></span> <span data-ttu-id="0b0ae-184">为了实现更好的安全性，建议使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-184">Windows Authentication is recommended for better security.</span></span>  
  
 <span data-ttu-id="0b0ae-185">**Use SQL Server Authentication**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-185">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="0b0ae-186">指定包是否应使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证来登录到服务器。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-186">Specify whether the package should use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to log on to the server.</span></span> <span data-ttu-id="0b0ae-187">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，则必须提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-187">If you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="0b0ae-188">**用户名**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-188">**User name**</span></span>  
 <span data-ttu-id="0b0ae-189">指定用户名。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-189">Specify a user name.</span></span>  
  
 <span data-ttu-id="0b0ae-190">**密码**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-190">**Password**</span></span>  
 <span data-ttu-id="0b0ae-191">指定密码。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-191">Specify a password.</span></span>  
  
 <span data-ttu-id="0b0ae-192">**包路径**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-192">**Package path**</span></span>  
 <span data-ttu-id="0b0ae-193">指定逻辑文件夹的名称，或者输入 "/" 作为默认文件夹。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-193">Specify the name of the logical folder, or enter "/" for the default folder.</span></span>  
  
 <span data-ttu-id="0b0ae-194">若要在“SSIS 包”  对话框中选择该文件夹，请单击“浏览(...)”。但是，该对话框不提供用来选择默认文件夹的方法。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-194">To select the folder in the **SSIS Package** dialog box, click browse (...). However, the dialog box does not provide a means to select the default folder.</span></span> <span data-ttu-id="0b0ae-195">如果要使用默认文件夹，则必须在该文本框中输入 "/"。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-195">If you want to use the default folder, you have to enter "/" in the text box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0b0ae-196">如果没有输入有效的包路径，则会出现下面的错误消息：“一个或多个参数无效。”</span><span class="sxs-lookup"><span data-stu-id="0b0ae-196">If you do not enter a valid package path, the following error message appears: "One or more arguments are invalid."</span></span>  
  
 <span data-ttu-id="0b0ae-197">**依靠服务器存储进行加密**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-197">**Rely on server storage for encryption**</span></span>  
 <span data-ttu-id="0b0ae-198">选择此项可以使用 [!INCLUDE[ssDE](../includes/ssde-md.md)] 的安全功能来帮助保护包。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-198">Select to use security features of the [!INCLUDE[ssDE](../includes/ssde-md.md)] to help secure the packages.</span></span>  
  
 <span data-ttu-id="0b0ae-199">**Next**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-199">**Next**</span></span>  
 <span data-ttu-id="0b0ae-200">转到向导的下一页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-200">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="0b0ae-201">**“完成”**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-201">**Finish**</span></span>  
 <span data-ttu-id="0b0ae-202">跳到“完成包安装向导”页。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-202">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="0b0ae-203">如果返回到向导前面的页修改所选项，并指定了所有必需的选项，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-203">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="finish-the-package-installation-page"></a><span data-ttu-id="0b0ae-204">“完成包安装”页</span><span class="sxs-lookup"><span data-stu-id="0b0ae-204">Finish the Package Installation Page</span></span>  
 <span data-ttu-id="0b0ae-205">可以使用 **“完成包安装向导”** 页查看包安装结果的摘要。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-205">Use the **Finish the Package Installation Wizard** page to view a summary of the package installation results.</span></span> <span data-ttu-id="0b0ae-206">此页提供了如所部署 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目的名称、已安装的包、配置文件和安装位置等之类的详细信息。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-206">This page provides details such as the name of the deployed [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, the packages that were installed, the configuration files, and the installation location.</span></span>  
  
 <span data-ttu-id="0b0ae-207">**“完成”**</span><span class="sxs-lookup"><span data-stu-id="0b0ae-207">**Finish**</span></span>  
 <span data-ttu-id="0b0ae-208">单击“完成”  即可退出该向导。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-208">Exit the wizard by clicking **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b0ae-209">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b0ae-209">See Also</span></span>  
 [<span data-ttu-id="0b0ae-210">包部署 &#40;SSIS&#41;</span><span class="sxs-lookup"><span data-stu-id="0b0ae-210">Package Deployment &#40;SSIS&#41;</span></span>](packages/legacy-package-deployment-ssis.md)  
  
  
