---
title: 第 1 课：准备创建部署捆绑 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6fe283c-9856-4ba1-a497-e3912424fd18
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0deda2a81ddd86d4e40c1c546232b8056264508a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586817"
---
# <a name="lesson-1-preparing-to-create-the-deployment-bundle"></a><span data-ttu-id="64f7d-102">第 1 课：准备创建部署捆绑</span><span class="sxs-lookup"><span data-stu-id="64f7d-102">Lesson 1: Preparing to Create the Deployment Bundle</span></span>
  <span data-ttu-id="64f7d-103">在本课中，将创建支持教程的工作文件夹和环境变量，创建 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目，将几个包及其支持文件添加到项目，然后在包中实现配置。</span><span class="sxs-lookup"><span data-stu-id="64f7d-103">In this lesson, you will create the working folders and environment variables that support the tutorial, create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, add several packages and their supporting files to the project, and implement configurations in packages.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="64f7d-104">基于项目部署包；因此，作为创建部署捆绑的第一步，必须将所有包和包依赖项集合到一个 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中。</span><span class="sxs-lookup"><span data-stu-id="64f7d-104">deploys packages on a project basis; therefore, as the first step in creating the deployment bundle, you must collect all the packages and package dependencies into one [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="64f7d-105">通常，包括已部署包的其他信息是很有用的：例如，您还将向项目中添加提供此组包的基本文档的自述文件。</span><span class="sxs-lookup"><span data-stu-id="64f7d-105">Frequently it is useful to include other information with the deployed packages: for example you will also add to the project a Readme file that provides basic documentation for this group of packages.</span></span>  
  
 <span data-ttu-id="64f7d-106">添加包和文件后，将配置添加到尚未使用配置的包。</span><span class="sxs-lookup"><span data-stu-id="64f7d-106">After you have added the packages and files, you will add configurations to packages that do not already use configurations.</span></span> <span data-ttu-id="64f7d-107">配置在运行时更新包和包对象的属性。</span><span class="sxs-lookup"><span data-stu-id="64f7d-107">The configurations update properties of packages and package objects at run time.</span></span> <span data-ttu-id="64f7d-108">在后面的课程中，将在包部署期间修改这些配置的值，以便在部署到的环境中支持包。</span><span class="sxs-lookup"><span data-stu-id="64f7d-108">In a later lesson, you will modify the values of these configurations during package deployment to support the packages in the deployed-to environment.</span></span>  
  
 <span data-ttu-id="64f7d-109">添加配置后，应该在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器（用于生成 ETL 包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 图形工具）中打开包，并检查包属性、包元素以及包配置，以便更好地了解部署需要解决的问题。</span><span class="sxs-lookup"><span data-stu-id="64f7d-109">After you have added the configurations, you should open the packages in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] graphical tool for building ETL packages, and examine the properties of packages and package elements as well as the package configurations to better understand the issues that the deployment needs to address.</span></span> <span data-ttu-id="64f7d-110">例如，其中一个包从文本文件提取数据，因此必须先更新数据文件的位置，已部署的包才能成功运行。</span><span class="sxs-lookup"><span data-stu-id="64f7d-110">For example, one of the packages extracts data from text files, so the location of the data files must be updated before the deployed packages will run successfully.</span></span>  
  
 <span data-ttu-id="64f7d-111">**学完本课的估计时间：** 1 小时</span><span class="sxs-lookup"><span data-stu-id="64f7d-111">**Estimated time to complete this lesson:** 1 hour</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="64f7d-112">课程任务</span><span class="sxs-lookup"><span data-stu-id="64f7d-112">Lesson Tasks</span></span>  
 <span data-ttu-id="64f7d-113">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="64f7d-113">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="64f7d-114">步骤 1：创建工作文件夹和环境变量</span><span class="sxs-lookup"><span data-stu-id="64f7d-114">Step 1: Creating Working Folders and Environment Variables</span></span>](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
-   [<span data-ttu-id="64f7d-115">步骤 2：创建部署项目</span><span class="sxs-lookup"><span data-stu-id="64f7d-115">Step 2: Creating the Deployment Project</span></span>](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
-   [<span data-ttu-id="64f7d-116">步骤 3：添加包和其他文件</span><span class="sxs-lookup"><span data-stu-id="64f7d-116">Step 3: Adding Packages and Other Files</span></span>](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
-   [<span data-ttu-id="64f7d-117">步骤 4：添加包配置</span><span class="sxs-lookup"><span data-stu-id="64f7d-117">Step 4: Adding Package Configurations</span></span>](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
-   [<span data-ttu-id="64f7d-118">步骤 5：测试更新的包</span><span class="sxs-lookup"><span data-stu-id="64f7d-118">Step 5: Testing the Updated Packages</span></span>](../integration-services/lesson-1-5-testing-the-updated-packages.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="64f7d-119">开始课程</span><span class="sxs-lookup"><span data-stu-id="64f7d-119">Start the Lesson</span></span>  
 [<span data-ttu-id="64f7d-120">步骤 1：创建工作文件夹和环境变量</span><span class="sxs-lookup"><span data-stu-id="64f7d-120">Step 1: Creating Working Folders and Environment Variables</span></span>](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
<span data-ttu-id="64f7d-121">![Integration Services 图标 (小型) ](media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="64f7d-121">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="64f7d-122">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="64f7d-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="64f7d-123">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="64f7d-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="64f7d-124">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="64f7d-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
