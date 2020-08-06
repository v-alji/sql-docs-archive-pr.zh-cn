---
title: 使用部署实用工具部署包 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], installing
- installing packages
- dependencies [Integration Services]
- deploying packages [Integration Services], installing
ms.assetid: eaf4b56e-2023-4d17-971c-703031da758c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a09ad307dc0215fca679cfb1ef5a37031f951caf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690769"
---
# <a name="deploy-packages-by-using-the-deployment-utility"></a><span data-ttu-id="b46d5-102">使用部署实用工具部署包</span><span class="sxs-lookup"><span data-stu-id="b46d5-102">Deploy Packages by Using the Deployment Utility</span></span>
  <span data-ttu-id="b46d5-103">如果要使用所生成的部署实用工具将 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中的包安装到与生成该工具的计算机不同的其他计算机上，则必须首先将部署文件夹复制到目标计算机上。</span><span class="sxs-lookup"><span data-stu-id="b46d5-103">When you have built a deployment utility to install packages from an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project on a different computer than the one on which the deployment utility was built, you must first copy the deployment folder to the destination computer.</span></span>  
  
 <span data-ttu-id="b46d5-104">部署文件夹的路径是在为其创建部署实用工具的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目的 DeploymentOutputPath 属性中指定的。</span><span class="sxs-lookup"><span data-stu-id="b46d5-104">The path of the deployment folder is specified in the DeploymentOutputPath property of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project for which you created the deployment utility.</span></span> <span data-ttu-id="b46d5-105">默认路径为 bin\Deployment，它相对于 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="b46d5-105">The default path is bin\Deployment, relative to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="b46d5-106">有关详细信息，请参阅 [Create a Deployment Utility](../../2014/integration-services/create-a-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="b46d5-106">For more information, see [Create a Deployment Utility](../../2014/integration-services/create-a-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="b46d5-107">可以使用包安装向导安装包。</span><span class="sxs-lookup"><span data-stu-id="b46d5-107">You use the Package Installation Wizard to install the packages.</span></span> <span data-ttu-id="b46d5-108">若要启动向导，在将部署文件夹复制到服务器之后，请双击部署实用工具文件。</span><span class="sxs-lookup"><span data-stu-id="b46d5-108">To launch the wizard, double-click the deployment utility file after you have copied the deployment folder to the server.</span></span> <span data-ttu-id="b46d5-109">此文件名为 \<project name>.SSISDeploymentManifest，可以在目标计算机上的部署文件夹找到它。</span><span class="sxs-lookup"><span data-stu-id="b46d5-109">This file is named \<project name>.SSISDeploymentManifest, and can be found in the deployment folder on the destination computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b46d5-110">如果并行安装了不同版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，根据你部署的包的版本，可能会遇到错误。</span><span class="sxs-lookup"><span data-stu-id="b46d5-110">Depending on the version of the package that you are deploying, you might encounter an error if you have different versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installed side-by-side.</span></span> <span data-ttu-id="b46d5-111">因为 .SSISDeploymentManifest 文件扩展名对于 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的所有版本是相同的，因此可能出现此错误。</span><span class="sxs-lookup"><span data-stu-id="b46d5-111">This error can occur because the .SSISDeploymentManifest file name extension is the same for all versions of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="b46d5-112">针对最近安装的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]版本双击该文件调用安装程序 (dtsinstall.exe)，它的版本可能与部署实用工具文件的版本不同。</span><span class="sxs-lookup"><span data-stu-id="b46d5-112">Double-clicking the file calls the installer (dtsinstall.exe) for the most recently installed version of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], which might not be the same version as the deployment utility file.</span></span> <span data-ttu-id="b46d5-113">若要解决这个问题，请从命令行运行正确的 dtsinstall.exe 版本，并且提供部署实用工具文件的路径。</span><span class="sxs-lookup"><span data-stu-id="b46d5-113">To work around this problem, run the correct version of dtsinstall.exe from the command line, and provide the path of the deployment utility file.</span></span>  
  
 <span data-ttu-id="b46d5-114">包安装向导指导您完成将包安装到文件系统或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中的步骤。</span><span class="sxs-lookup"><span data-stu-id="b46d5-114">The Package Installation Wizard guides you through the steps to install packages to the file system or to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b46d5-115">可以按下列方式配置安装：</span><span class="sxs-lookup"><span data-stu-id="b46d5-115">You can configure the installation in the following ways:</span></span>  
  
-   <span data-ttu-id="b46d5-116">选择安装包的位置类型和位置。</span><span class="sxs-lookup"><span data-stu-id="b46d5-116">Choosing the location type and location to install the packages.</span></span>  
  
-   <span data-ttu-id="b46d5-117">选择安装包的依赖项的位置。</span><span class="sxs-lookup"><span data-stu-id="b46d5-117">Choosing location to install package dependencies.</span></span>  
  
-   <span data-ttu-id="b46d5-118">在目标服务器上安装包之后对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="b46d5-118">Validating the packages after they are installed on the target server.</span></span>  
  
 <span data-ttu-id="b46d5-119">包的基于文件的依赖项始终都安装到文件系统中。</span><span class="sxs-lookup"><span data-stu-id="b46d5-119">The file-based dependencies for packages are always installed to the file system.</span></span> <span data-ttu-id="b46d5-120">如果要将包安装到文件系统中，则依赖项也会安装到您为包所指定的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="b46d5-120">If you install a package to the file system, the dependencies are installed in the same folder as the one that you specify for the package.</span></span> <span data-ttu-id="b46d5-121">如果将包安装到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，您可以指定存储基于文件的依赖项的文件夹。</span><span class="sxs-lookup"><span data-stu-id="b46d5-121">If you install a package to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can specify the folder in which to store the file-based dependencies.</span></span>  
  
 <span data-ttu-id="b46d5-122">如果包包括要进行修改以便在目标计算机上使用的配置，您可以使用该向导更新属性的值。</span><span class="sxs-lookup"><span data-stu-id="b46d5-122">If the package includes configurations that you want to modify for use on the destination computer, you can update the values of the properties by using the wizard.</span></span>  
  
 <span data-ttu-id="b46d5-123">除了使用包安装向导安装包之外，还可以使用 **dtutil** 命令提示实用工具来复制和移动包。</span><span class="sxs-lookup"><span data-stu-id="b46d5-123">In addition to installing packages by using the Package Installation Wizard, you can copy and move packages by using the **dtutil** command prompt utility.</span></span> <span data-ttu-id="b46d5-124">有关详细信息，请参阅 [dtutil Utility](dtutil-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="b46d5-124">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
### <a name="to-deploy-packages-to-an-instance-of-sql-server"></a><span data-ttu-id="b46d5-125">将包部署到 SQL Server 的实例</span><span class="sxs-lookup"><span data-stu-id="b46d5-125">To deploy packages to an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="b46d5-126">在目标计算机上打开部署文件夹。</span><span class="sxs-lookup"><span data-stu-id="b46d5-126">Open the deployment folder on the target computer.</span></span>  
  
2.  <span data-ttu-id="b46d5-127">双击清单文件 \<project name>.SSISDeploymentManifest，以启动包安装向导。</span><span class="sxs-lookup"><span data-stu-id="b46d5-127">Double-click the manifest file, \<project name>.SSISDeploymentManifest, to start the Package Installation Wizard.</span></span>  
  
3.  <span data-ttu-id="b46d5-128">在 **“部署 SSIS 包”** 页上，选择 **“SQL Server 部署”** 选项。</span><span class="sxs-lookup"><span data-stu-id="b46d5-128">On the **Deploy SSIS Packages** page, select the **SQL Server deployment** option.</span></span>  
  
4.  <span data-ttu-id="b46d5-129">还可以选择 **“安装后验证包”** ，以便在将包安装到目标服务器之后对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="b46d5-129">Optionally, select **Validate packages after installation** to validate packages after they are installed on the target server.</span></span>  
  
5.  <span data-ttu-id="b46d5-130">在 **“指定目标 SQL Server”** 页上，指定要将包安装到的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，并选择身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="b46d5-130">On the **Specify Target SQL Server** page, specify the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to install the packages to and select an authentication mode.</span></span> <span data-ttu-id="b46d5-131">如果选择 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，则必须提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="b46d5-131">If you select [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and a password.</span></span>  
  
6.  <span data-ttu-id="b46d5-132">在 **“选择安装文件夹”** 页上，指定文件系统中用来安装包依赖项的文件夹。</span><span class="sxs-lookup"><span data-stu-id="b46d5-132">On the **Select Installation Folder** page, specify the folder in the file system for the package dependencies that will be installed.</span></span>  
  
7.  <span data-ttu-id="b46d5-133">如果包包括配置，可以通过更新“配置包”页上 **“值”** 列表中的值来编辑这些配置。</span><span class="sxs-lookup"><span data-stu-id="b46d5-133">If the package includes configurations, you can edit configurations by updating values in the **Value** list on the Configure Packages page.</span></span>  
  
8.  <span data-ttu-id="b46d5-134">如果选择了在安装之后验证包，请查看所部署的包的验证结果。</span><span class="sxs-lookup"><span data-stu-id="b46d5-134">If you elected to validate packages after installation, view the validation results of the deployed packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b46d5-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b46d5-135">See Also</span></span>  
 [<span data-ttu-id="b46d5-136">包部署 &#40;SSIS&#41;</span><span class="sxs-lookup"><span data-stu-id="b46d5-136">Package Deployment &#40;SSIS&#41;</span></span>](packages/legacy-package-deployment-ssis.md)  
  
  
