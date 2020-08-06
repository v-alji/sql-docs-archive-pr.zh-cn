---
title: 步骤 2：验证部署捆绑 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6c13f5c9-c75e-4e52-94dc-2d2db2c578fe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f452a87154175ac05a050761d8f12b6bfe61cd8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578309"
---
# <a name="step-2-verifying-the-deployment-bundle"></a><span data-ttu-id="4b4ad-102">步骤 2：验证部署捆绑</span><span class="sxs-lookup"><span data-stu-id="4b4ad-102">Step 2: Verifying the Deployment Bundle</span></span>
  <span data-ttu-id="4b4ad-103">在第 1 课中，创建了 Deployment Tutorial 项目，并向该项目添加了包和辅助文件；在上一任务中，您为项目生成了部署实用工具。</span><span class="sxs-lookup"><span data-stu-id="4b4ad-103">In lesson 1, you created the Deployment Tutorial project and added packages and ancillary files to the project; in the previous task you built a deployment utility for the project.</span></span>  
  
 <span data-ttu-id="4b4ad-104">在此任务中，您将验证部署捆绑的内容。</span><span class="sxs-lookup"><span data-stu-id="4b4ad-104">In this task, you will verify the contents of the deployment bundle.</span></span> <span data-ttu-id="4b4ad-105">部署捆绑是将复制到目标计算机并用来安装包的文件夹。</span><span class="sxs-lookup"><span data-stu-id="4b4ad-105">The deployment bundle is the folder that you will copy to the destination computer and use to install packages.</span></span> <span data-ttu-id="4b4ad-106">如果将默认值 bin\Deployment 用作部署实用工具的位置，则在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中部署捆绑是 Deployment Tutorial 文件夹中的 Bin\Deployment 文件夹。</span><span class="sxs-lookup"><span data-stu-id="4b4ad-106">If you used the default value-bin\Deployment-as the location of the deployment utility, the deployment bundle is the Bin\Deployment folder within the Deployment Tutorial folder in the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
### <a name="to-verify-the-content-of-deployment-bundle"></a><span data-ttu-id="4b4ad-107">验证部署捆绑的内容</span><span class="sxs-lookup"><span data-stu-id="4b4ad-107">To verify the content of deployment bundle</span></span>  
  
1.  <span data-ttu-id="4b4ad-108">找到计算机上的 bin\Deployment 文件夹。</span><span class="sxs-lookup"><span data-stu-id="4b4ad-108">Locate the bin\Deployment folder on your computer.</span></span>  
  
2.  <span data-ttu-id="4b4ad-109">验证是否存在下列文件：</span><span class="sxs-lookup"><span data-stu-id="4b4ad-109">Verify that the following files are present:</span></span>  
  
    -   <span data-ttu-id="4b4ad-110">DataTransfer.dtsx</span><span class="sxs-lookup"><span data-stu-id="4b4ad-110">DataTransfer.dtsx</span></span>  
  
    -   <span data-ttu-id="4b4ad-111">datatransferconfig.dtsconfig</span><span class="sxs-lookup"><span data-stu-id="4b4ad-111">datatransferconfig.dtsconfig</span></span>  
  
    -   <span data-ttu-id="4b4ad-112">Deployment Tutorial.SSISDeploymentManifest</span><span class="sxs-lookup"><span data-stu-id="4b4ad-112">Deployment Tutorial.SSISDeploymentManifest</span></span>  
  
    -   <span data-ttu-id="4b4ad-113">LoadXMLData.dtsx</span><span class="sxs-lookup"><span data-stu-id="4b4ad-113">LoadXMLData.dtsx</span></span>  
  
    -   <span data-ttu-id="4b4ad-114">loadxmldataconfig.dtsconfig</span><span class="sxs-lookup"><span data-stu-id="4b4ad-114">loadxmldataconfig.dtsconfig</span></span>  
  
    -   <span data-ttu-id="4b4ad-115">NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="4b4ad-115">NewCustomers.txt</span></span>  
  
    -   <span data-ttu-id="4b4ad-116">orders.xml</span><span class="sxs-lookup"><span data-stu-id="4b4ad-116">orders.xml</span></span>  
  
    -   <span data-ttu-id="4b4ad-117">orders.xsd</span><span class="sxs-lookup"><span data-stu-id="4b4ad-117">orders.xsd</span></span>  
  
    -   <span data-ttu-id="4b4ad-118">Readme.txt</span><span class="sxs-lookup"><span data-stu-id="4b4ad-118">Readme.txt</span></span>  
  
3.  <span data-ttu-id="4b4ad-119">右键单击“Deployment Tutorial.SSISDeploymentManifest”，指向“打开方式”  ，再单击“Internet Explorer”  。</span><span class="sxs-lookup"><span data-stu-id="4b4ad-119">Right-click Deployment Tutorial.SSISDeploymentManifest, point **to Open With**, and then click **Internet Explorer**.</span></span> <span data-ttu-id="4b4ad-120">也可以在文本编辑器（如记事本）中打开该文件。</span><span class="sxs-lookup"><span data-stu-id="4b4ad-120">You can also open the file in a text editor such as Notepad.</span></span> <span data-ttu-id="4b4ad-121">文件的 XML 代码应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="4b4ad-121">The XML code of the file should be the following:</span></span>  
  
     `<?xml version="1.0"?><DTSDeploymentManifest GeneratedBy="Domain\UserName" GeneratedFromProjectName="Deployment Tutorial" GeneratedDate="2006-02-24T13:29:02.6537669-08:00" AllowConfigurationChanges="true"><Package>DataTransfer.dtsx</Package><Package>LoadXMLData.dtsx</Package><ConfigurationFile>datatransferconfig.dtsconfig</ConfigurationFile><ConfigurationFile>loadxmldataconfig.dtsconfig</ConfigurationFile><MiscellaneousFile>Readme.txt</MiscellaneousFile><MiscellaneousFile>orders.xml</MiscellaneousFile><MiscellaneousFile>NewCustomers.txt</MiscellaneousFile><MiscellaneousFile>orders.xsd</MiscellaneousFile></DTSDeploymentManifest>`  
  
4.  <span data-ttu-id="4b4ad-122">验证特性的值是否为 `AllowConfigurationChanges` **true** ，并且 XML 是否包含两个 `Package` 包中的每个包的元素、 `MiscellaneousFile` 四个非包文件中每个文件的元素以及 `ConfigurationFile` 两个 XML 配置文件中每个文件的元素。</span><span class="sxs-lookup"><span data-stu-id="4b4ad-122">Verify that the value of the `AllowConfigurationChanges` attribute is **true** and the XML includes a `Package` element for each of the two packages, a `MiscellaneousFile` element for each of the four non-package files, and a `ConfigurationFile` element for each of the two XML configuration files.</span></span>  
  
5.  <span data-ttu-id="4b4ad-123">退出 Internet Explorer 或文本编辑器。</span><span class="sxs-lookup"><span data-stu-id="4b4ad-123">Exit Internet Explorer or the text editor.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="4b4ad-124">下一课</span><span class="sxs-lookup"><span data-stu-id="4b4ad-124">Next Lesson</span></span>  
 [<span data-ttu-id="4b4ad-125">第 3 课：安装包</span><span class="sxs-lookup"><span data-stu-id="4b4ad-125">Lesson 3: Installing Packages</span></span>](../integration-services/lesson-3-install-ssis-package.md)  
  
<span data-ttu-id="4b4ad-126">![Integration Services 图标 (小型) ](media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="4b4ad-126">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="4b4ad-127">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="4b4ad-127">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="4b4ad-128">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="4b4ad-128">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="4b4ad-129">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="4b4ad-129">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
