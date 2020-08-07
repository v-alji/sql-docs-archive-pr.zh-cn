---
title: 第2课：创建部署捆绑 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab17289d-c3d4-4a5e-b7f5-4fea8ae21707
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 927bcd393e4b54e92971c197d93dcc1e2804dcd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588603"
---
# <a name="lesson-2-creating-the-deployment-bundle"></a><span data-ttu-id="7591a-102">第 2 课：创建部署捆绑</span><span class="sxs-lookup"><span data-stu-id="7591a-102">Lesson 2: Creating the Deployment Bundle</span></span>
  <span data-ttu-id="7591a-103">在 [第 1 课：准备创建部署捆绑](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)中，创建了名为 Deployment Tutorial 的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目，将包和支持文件添加到该项目，并在包中实现了配置。</span><span class="sxs-lookup"><span data-stu-id="7591a-103">In [Lesson 1: Preparing to Create the Deployment Bundle](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md), you created the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project named Deployment Tutorial, added the packages and supporting files to the project, and implemented configurations in packages.</span></span>  
  
 <span data-ttu-id="7591a-104">在本课中，您将创建部署捆绑，它是一个文件夹，其中包含您在其他计算机上安装包所需的项。</span><span class="sxs-lookup"><span data-stu-id="7591a-104">In this lesson, you will create the deployment bundle, which is a folder that contains the items that you need to install packages on another computer.</span></span> <span data-ttu-id="7591a-105">部署捆绑将包括部署清单、来自 Deployment Tutorial 项目的包副本和支持文件副本。</span><span class="sxs-lookup"><span data-stu-id="7591a-105">The deployment bundle will include a deployment manifest, copies of the packages, and copies of the supporting files from the Deployment Tutorial project.</span></span> <span data-ttu-id="7591a-106">部署清单列出部署捆绑中的包、杂项文件和配置。</span><span class="sxs-lookup"><span data-stu-id="7591a-106">The deployment manifest lists the packages, miscellaneous files, and configurations in the deployment bundle.</span></span>  
  
 <span data-ttu-id="7591a-107">您还将验证部署捆绑中的文件列表以及检查清单的内容。</span><span class="sxs-lookup"><span data-stu-id="7591a-107">You will also verify the file list in the deployment bundle and examine the contents of the manifest.</span></span>  
  
 <span data-ttu-id="7591a-108">**学完本课的估计时间：** 30 分钟</span><span class="sxs-lookup"><span data-stu-id="7591a-108">**Estimated time to complete this lesson:** 30 minutes</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="7591a-109">课程任务</span><span class="sxs-lookup"><span data-stu-id="7591a-109">Lesson Tasks</span></span>  
 <span data-ttu-id="7591a-110">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="7591a-110">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="7591a-111">步骤 1：生成部署实用工具</span><span class="sxs-lookup"><span data-stu-id="7591a-111">Step 1: Building the Deployment Utility</span></span>](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
-   [<span data-ttu-id="7591a-112">步骤 2：验证部署捆绑</span><span class="sxs-lookup"><span data-stu-id="7591a-112">Step 2: Verifying the Deployment Bundle</span></span>](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="7591a-113">开始课程</span><span class="sxs-lookup"><span data-stu-id="7591a-113">Start the Lesson</span></span>  
 [<span data-ttu-id="7591a-114">步骤 1：生成部署实用工具</span><span class="sxs-lookup"><span data-stu-id="7591a-114">Step 1: Building the Deployment Utility</span></span>](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
<span data-ttu-id="7591a-115">![Integration Services 图标 (小型) ](media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="7591a-115">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="7591a-116">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="7591a-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="7591a-117">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="7591a-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="7591a-118">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="7591a-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
