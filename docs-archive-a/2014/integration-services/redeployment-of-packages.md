---
title: 重新部署包 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- redeploying packages [Integration Services]
- deploying packages [Integration Services], redeploying
ms.assetid: 86806efb-8cf4-4f9d-9824-1152cb4c495c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c5286d406d96f62fc74eb619f7e7a6064fde2a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687992"
---
# <a name="redeployment-of-packages"></a><span data-ttu-id="bc74e-102">重新部署包</span><span class="sxs-lookup"><span data-stu-id="bc74e-102">Redeployment of Packages</span></span>
  <span data-ttu-id="bc74e-103">在部署项目后，您可能需要更新或扩展包功能，然后重新部署包含更新包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="bc74e-103">After a project is deployed, you may need to update or extend package functionality and then redeploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the updated packages.</span></span> <span data-ttu-id="bc74e-104">在重新部署包的过程中，您应该检查部署实用工具中包括的配置属性。</span><span class="sxs-lookup"><span data-stu-id="bc74e-104">As part of the process of redeploying packages, you should review the configuration properties that are included in the deployment utility.</span></span> <span data-ttu-id="bc74e-105">例如，您可能不希望在重新部署包后允许对配置进行更改。</span><span class="sxs-lookup"><span data-stu-id="bc74e-105">For example, you may not want to allow configuration changes after the package is redeployed.</span></span>  
  
## <a name="process-for-redeployment"></a><span data-ttu-id="bc74e-106">重新部署过程</span><span class="sxs-lookup"><span data-stu-id="bc74e-106">Process for Redeployment</span></span>  
 <span data-ttu-id="bc74e-107">在完成更新包后，您应该重新生成该项目，将部署文件夹复制到目标计算机，然后重新运行包安装向导。</span><span class="sxs-lookup"><span data-stu-id="bc74e-107">After you finish updating the packages, you rebuild the project, copy the deployment folder to the target computer, and then rerun the Package Installation Wizard.</span></span>  
  
 <span data-ttu-id="bc74e-108">如果只更新项目中的少数几个包，您可能不希望重新部署整个项目。</span><span class="sxs-lookup"><span data-stu-id="bc74e-108">If you update only a few packages in the project, you may not want to redeploy the entire project.</span></span> <span data-ttu-id="bc74e-109">若要仅部署几个包，可以新建一个 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目，将更新后的包添加到新的项目，然后生成并部署该项目。</span><span class="sxs-lookup"><span data-stu-id="bc74e-109">To deploy only a few packages, you can create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, add the updated packages to the new project, and then build and deploy the project.</span></span> <span data-ttu-id="bc74e-110">在将包添加到其他项目时，包配置会自动随包一起复制。</span><span class="sxs-lookup"><span data-stu-id="bc74e-110">Package configurations are automatically copied with the package when you add the package to a different project.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="bc74e-111">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="bc74e-111">Related Tasks</span></span>  
 [<span data-ttu-id="bc74e-112">使用部署实用工具部署包</span><span class="sxs-lookup"><span data-stu-id="bc74e-112">Deploy Packages by Using the Deployment Utility</span></span>](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)  
  
  
