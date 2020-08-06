---
title: 步骤 5：测试更新的包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a075af2e030c8257d01abf5eba7d330b1cc8efe7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586826"
---
# <a name="step-5-testing-the-updated-packages"></a><span data-ttu-id="adccb-102">步骤 5：测试更新的包</span><span class="sxs-lookup"><span data-stu-id="adccb-102">Step 5: Testing the Updated Packages</span></span>
  <span data-ttu-id="adccb-103">继续学习下一课（在该课中，您将创建用来在目标计算机上安装教程包的部署捆绑）之前，您应该测试包。</span><span class="sxs-lookup"><span data-stu-id="adccb-103">Before you go on to the next lesson, in which you will create the deployment bundle to use to install the tutorial packages on the destination computer, you should test the packages.</span></span> <span data-ttu-id="adccb-104">在此任务中，您将运行已添加到 Deployment Tutorial 项目中再用配置进行扩展的包 DataTransfer.dtsx 和 LoadXMLData。</span><span class="sxs-lookup"><span data-stu-id="adccb-104">In this task, you will run the packages, DataTransfer.dtsx and LoadXMLData, that you added to the Deployment Tutorial project and then extended with configurations.</span></span>  
  
 <span data-ttu-id="adccb-105">当包运行时，随着它成功完成，包中的每个可执行文件都将变为绿色。</span><span class="sxs-lookup"><span data-stu-id="adccb-105">When the packages run, each executable in the package becomes a green color as it completes successfully.</span></span> <span data-ttu-id="adccb-106">当所有可执行文件都为绿色时，包已成功完成。</span><span class="sxs-lookup"><span data-stu-id="adccb-106">When all executables are green, the package has completed successfully.</span></span> <span data-ttu-id="adccb-107">还可以在“进度”  选项卡上查看包的执行进度。</span><span class="sxs-lookup"><span data-stu-id="adccb-107">You can also view the package execution progress on the **Progress** tab.</span></span>  
  
 <span data-ttu-id="adccb-108">如果包未成功运行，则您必须先修复它们，再继续学习下一课。</span><span class="sxs-lookup"><span data-stu-id="adccb-108">If the packages do not run successfully, you must fix them before you go on to the next lesson.</span></span>  
  
### <a name="to-run-the-datatransfer-package"></a><span data-ttu-id="adccb-109">运行 DataTransfer 包</span><span class="sxs-lookup"><span data-stu-id="adccb-109">To run the DataTransfer package</span></span>  
  
1.  <span data-ttu-id="adccb-110">在解决方案资源管理器中，单击 DataTransfer.dtsx。</span><span class="sxs-lookup"><span data-stu-id="adccb-110">In Solution Explorer, click DataTransfer.dtsx.</span></span>  
  
2.  <span data-ttu-id="adccb-111">在 **“调试”** 菜单中，单击 **“启动调试”** 。</span><span class="sxs-lookup"><span data-stu-id="adccb-111">On **Debug** menu, click **Start Debugging**.</span></span>  
  
3.  <span data-ttu-id="adccb-112">当包运行完毕后，在 **“调试”** 菜单中，单击 **“停止调试”** 。</span><span class="sxs-lookup"><span data-stu-id="adccb-112">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
### <a name="to-run-the-loadxmldata-package"></a><span data-ttu-id="adccb-113">运行 LoadXMLData 包</span><span class="sxs-lookup"><span data-stu-id="adccb-113">To run the LoadXMLData package</span></span>  
  
1.  <span data-ttu-id="adccb-114">在解决方案资源管理器中，单击 LoadXMLData.dtsx。</span><span class="sxs-lookup"><span data-stu-id="adccb-114">In Solution Explorer, click LoadXMLData.dtsx.</span></span>  
  
2.  <span data-ttu-id="adccb-115">在 **“调试”** 菜单中，单击 **“启动调试”** 。</span><span class="sxs-lookup"><span data-stu-id="adccb-115">On **Debug** menu, click **Start Debugging**.</span></span>  
  
3.  <span data-ttu-id="adccb-116">当包运行完毕后，在 **“调试”** 菜单中，单击 **“停止调试”** 。</span><span class="sxs-lookup"><span data-stu-id="adccb-116">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="adccb-117">下一课</span><span class="sxs-lookup"><span data-stu-id="adccb-117">Next Lesson</span></span>  
 [<span data-ttu-id="adccb-118">第 2 课：创建部署捆绑</span><span class="sxs-lookup"><span data-stu-id="adccb-118">Lesson 2: Creating the Deployment Bundle</span></span>](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
  
<span data-ttu-id="adccb-119">![Integration Services 图标 (小型) ](media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="adccb-119">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="adccb-120">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="adccb-120">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="adccb-121">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="adccb-121">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="adccb-122">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="adccb-122">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
