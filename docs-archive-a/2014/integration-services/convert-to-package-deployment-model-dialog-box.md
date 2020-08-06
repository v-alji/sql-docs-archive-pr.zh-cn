---
title: "\"转换为包部署模型\" 对话框 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.bids.converttolegacydeployment.f1
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b52932ad26f8cebd2e67b0025f4b881241119f6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587538"
---
# <a name="convert-to-package-deployment-model-dialog-box"></a><span data-ttu-id="7d5b4-102">“转换为包部署模型”对话框</span><span class="sxs-lookup"><span data-stu-id="7d5b4-102">Convert to Package Deployment Model Dialog Box</span></span>
  <span data-ttu-id="7d5b4-103">使用 **“转换为包部署模型”** 命令可以在检查项目和项目中的每个包与包部署模型是否兼容后将包转换为该模型。</span><span class="sxs-lookup"><span data-stu-id="7d5b4-103">The **Convert to Package Deployment Model** command allows you to convert a package to the package deployment model after checking the project and each package in the project for compatibility with that model.</span></span> <span data-ttu-id="7d5b4-104">如果包使用项目部署模型特有的功能（如参数），则不能转换该包。</span><span class="sxs-lookup"><span data-stu-id="7d5b4-104">If a package uses features unique to the project deployment model, such as parameters, then the package cannot be converted.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="7d5b4-105">任务列表</span><span class="sxs-lookup"><span data-stu-id="7d5b4-105">Task List</span></span>  
 <span data-ttu-id="7d5b4-106">将包转换为包部署模型需要两个步骤。</span><span class="sxs-lookup"><span data-stu-id="7d5b4-106">Converting a package to the package deployment model requires two steps.</span></span>  
  
1.  <span data-ttu-id="7d5b4-107">从 **“项目”** 菜单选择 **“转换为包部署模型”** 命令时，检查项目和其中的每个包是否与此模型兼容。</span><span class="sxs-lookup"><span data-stu-id="7d5b4-107">When you select the **Convert to Package Deployment Model** command from the **Project** menu, the project and each package are checked for compatibility with this model.</span></span> <span data-ttu-id="7d5b4-108">结果显示在 **“结果”** 表中。</span><span class="sxs-lookup"><span data-stu-id="7d5b4-108">The results are displayed in the **Results** table.</span></span>  
  
     <span data-ttu-id="7d5b4-109">如果项目或其中的某个包未通过兼容测试，单击 **“结果”** 列中的 **“失败”** 可以获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="7d5b4-109">If the project or a package fails the compatibility test, click **Failed** in the **Result** column for more information.</span></span> <span data-ttu-id="7d5b4-110">单击 **“保存报告”** ，以将此信息的副本保存到文本文件。</span><span class="sxs-lookup"><span data-stu-id="7d5b4-110">Click **Save Report** to save a copy of this information to a text file.</span></span>  
  
2.  <span data-ttu-id="7d5b4-111">如果项目和所有包都通过了兼容测试，则单击 **“确定”** 以转换包。</span><span class="sxs-lookup"><span data-stu-id="7d5b4-111">If the project and all packages pass the compatibility test, then click **OK** to convert the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d5b4-112">若要将项目转换为项目部署模型，请使用 **“Integration Services 项目转换向导”**。</span><span class="sxs-lookup"><span data-stu-id="7d5b4-112">To convert a project to the project deployment model, use the **Integration Services Project Conversion Wizard**.</span></span> <span data-ttu-id="7d5b4-113">有关详细信息，请参阅 [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="7d5b4-113">For more information, see [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d5b4-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d5b4-114">See Also</span></span>  
 <span data-ttu-id="7d5b4-115">[项目和包的部署](packages/deploy-integration-services-ssis-projects-and-packages.md) </span><span class="sxs-lookup"><span data-stu-id="7d5b4-115">[Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md) </span></span>  
 <span data-ttu-id="7d5b4-116">[包部署 &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md) </span><span class="sxs-lookup"><span data-stu-id="7d5b4-116">[Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md) </span></span>  
 [<span data-ttu-id="7d5b4-117">Integration Services 项目转换向导</span><span class="sxs-lookup"><span data-stu-id="7d5b4-117">Integration Services Project Conversion Wizard</span></span>](../../2014/integration-services/integration-services-project-conversion-wizard.md)  
  
  
