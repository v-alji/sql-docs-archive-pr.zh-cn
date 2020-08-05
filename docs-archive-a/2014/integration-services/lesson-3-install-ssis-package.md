---
title: 第3课：安装包 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 87bc4d82-39d8-424f-886f-98cf1e4bb07a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f8b58cee7bd8e16cd0ca2e726dc8e5eff2cfec5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581372"
---
# <a name="lesson-3-installing-packages"></a><span data-ttu-id="d346a-102">第 3 课：安装包</span><span class="sxs-lookup"><span data-stu-id="d346a-102">Lesson 3: Installing Packages</span></span>
  <span data-ttu-id="d346a-103">在[第2课：创建部署捆绑](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)中，生成了部署实用工具，并创建了包含必须在另一台计算机上安装包的项的部署捆绑。</span><span class="sxs-lookup"><span data-stu-id="d346a-103">In [Lesson 2: Creating the Deployment Bundle](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md), you built a deployment utility and created the deployment bundle that contains the items that you must install packages on another computer.</span></span> <span data-ttu-id="d346a-104">您还验证了部署捆绑中的文件列表，检查了在生成部署实用工具时创建的清单文件的内容。</span><span class="sxs-lookup"><span data-stu-id="d346a-104">You also verified the file list in the deployment bundle and examined the contents of the manifest file that was created when you built the deployment utility.</span></span>  
  
 <span data-ttu-id="d346a-105">在本课中，将部署捆绑复制到目标计算机，然后在该计算机上运行包安装向导以安装包、包的依赖项和辅助文件。</span><span class="sxs-lookup"><span data-stu-id="d346a-105">In this lesson, you will copy the deployment bundle to the destination computer and then run the Package Installation Wizard to install the packages, package dependencies, and ancillary files on that computer.</span></span> <span data-ttu-id="d346a-106">包将安装在**msdb** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库中，其他项将安装在文件系统中。</span><span class="sxs-lookup"><span data-stu-id="d346a-106">The packages will be installed in the **msdb**[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database and the other items will be installed in the file system.</span></span> <span data-ttu-id="d346a-107">完成包的安装后，将通过使用执行包实用工具从 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 运行包来测试部署。</span><span class="sxs-lookup"><span data-stu-id="d346a-107">After you complete the package installation, you will test the deployment by running the packages from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] using the Execute Package Utility.</span></span>  
  
 <span data-ttu-id="d346a-108">**学完本课的估计时间：** 30 分钟</span><span class="sxs-lookup"><span data-stu-id="d346a-108">**Estimated time to complete this lesson:** 30 minutes</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="d346a-109">课程任务</span><span class="sxs-lookup"><span data-stu-id="d346a-109">Lesson Tasks</span></span>  
 <span data-ttu-id="d346a-110">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="d346a-110">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="d346a-111">步骤 1：复制部署捆绑</span><span class="sxs-lookup"><span data-stu-id="d346a-111">Step 1: Copying the Deployment Bundle</span></span>](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
-   [<span data-ttu-id="d346a-112">步骤 2：运行包安装向导</span><span class="sxs-lookup"><span data-stu-id="d346a-112">Step 2: Running the Package Installation Wizard</span></span>](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
-   [<span data-ttu-id="d346a-113">步骤 3：测试已部署的包</span><span class="sxs-lookup"><span data-stu-id="d346a-113">Step 3: Testing the Deployed Packages</span></span>](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="d346a-114">开始课程</span><span class="sxs-lookup"><span data-stu-id="d346a-114">Start the Lesson</span></span>  
 [<span data-ttu-id="d346a-115">步骤 1：复制部署捆绑</span><span class="sxs-lookup"><span data-stu-id="d346a-115">Step 1: Copying the Deployment Bundle</span></span>](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
<span data-ttu-id="d346a-116">![Integration Services 图标 (小型) ](media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="d346a-116">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d346a-117">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="d346a-117">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d346a-118">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="d346a-118">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d346a-119">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="d346a-119">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
