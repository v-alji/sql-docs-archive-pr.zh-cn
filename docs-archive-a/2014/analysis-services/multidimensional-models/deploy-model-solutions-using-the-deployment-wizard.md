---
title: 使用部署向导部署模型解决方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard
- deploying [Analysis Services], Analysis Services Deployment Wizard
- Analysis Services deployments, Analysis Services Deployment Wizard
- Analysis Services Deployment Wizard, about Analysis Services Deployment Wizard
ms.assetid: ff711e8e-971c-43ba-b479-effc034af4a4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6e3dfd0b727fd917c37aa44aa8fd1d29326aaaa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682424"
---
# <a name="deploy-model-solutions-using-the-deployment-wizard"></a><span data-ttu-id="1322f-102">使用部署向导部署模型解决方案</span><span class="sxs-lookup"><span data-stu-id="1322f-102">Deploy Model Solutions Using the Deployment Wizard</span></span>
  <span data-ttu-id="1322f-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]部署向导使用从项目生成的 XML 输出文件 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 作为输入文件。</span><span class="sxs-lookup"><span data-stu-id="1322f-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard uses the XML output files generated from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project as input files.</span></span> <span data-ttu-id="1322f-104">可以轻松地修改这些输入文件，以自定义 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目的部署。</span><span class="sxs-lookup"><span data-stu-id="1322f-104">These input files are easily modifiable to customize the deployment of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="1322f-105">随后，可以立即运行生成的部署脚本，也可以保留此脚本供以后部署。</span><span class="sxs-lookup"><span data-stu-id="1322f-105">The generated deployment script can then either be immediately run or saved for later deployment.</span></span>  
  
 <span data-ttu-id="1322f-106">您可以使用此处介绍的向导来进行部署。</span><span class="sxs-lookup"><span data-stu-id="1322f-106">You can deploy by using the wizard as discussed here.</span></span> <span data-ttu-id="1322f-107">也可以实现自动部署或使用同步功能。</span><span class="sxs-lookup"><span data-stu-id="1322f-107">You can also automate deployment or use the Synchronize capability.</span></span> <span data-ttu-id="1322f-108">如果部署的数据库很大，则需要考虑在目标系统上使用分区。</span><span class="sxs-lookup"><span data-stu-id="1322f-108">If the deployed database is large, consider using partitions on target systems.</span></span> <span data-ttu-id="1322f-109">您还可以使用分析管理对象 (AMO)，实现分区创建和填充自动化。</span><span class="sxs-lookup"><span data-stu-id="1322f-109">You can also automate partition creation and population by using Analysis Management Objects (AMO).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1322f-110">如果在用于数据源的连接字符串中指定用户 ID 或密码或出于模拟目的而指定用户 ID 和密码，则 XML 输出文件和部署脚本都不包含该用户 ID 或密码。</span><span class="sxs-lookup"><span data-stu-id="1322f-110">Neither the XML output files nor the deployment script will contain the user id or password if these are specified in either the connection string for a data source or for impersonation purposes.</span></span> <span data-ttu-id="1322f-111">在此情况下，由于处理时需要用户 ID 和密码，因此必须手动添加此信息。</span><span class="sxs-lookup"><span data-stu-id="1322f-111">Since these are required for processing purposes in this scenario, you will add this information manually.</span></span> <span data-ttu-id="1322f-112">如果部署不包括处理，则可以在部署后根据需要添加此连接和模拟信息。</span><span class="sxs-lookup"><span data-stu-id="1322f-112">If the deployment will not include processing, you can add this connection and impersonation information as needed after deployment.</span></span> <span data-ttu-id="1322f-113">如果部署包括处理，则可以在向导中添加此信息，也可以在保存部署脚本后在脚本中添加此信息。</span><span class="sxs-lookup"><span data-stu-id="1322f-113">If the deployment will include processing, you can either add this information within the wizard or in the deployment script after it is saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1322f-114">本节内容</span><span class="sxs-lookup"><span data-stu-id="1322f-114">In This Section</span></span>  
 <span data-ttu-id="1322f-115">以下主题说明了如何使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导、输入文件和部署脚本：</span><span class="sxs-lookup"><span data-stu-id="1322f-115">The following topics describe how to work with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard, the input files, and the deployment script:</span></span>  
  
|<span data-ttu-id="1322f-116">主题</span><span class="sxs-lookup"><span data-stu-id="1322f-116">Topic</span></span>|<span data-ttu-id="1322f-117">说明</span><span class="sxs-lookup"><span data-stu-id="1322f-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1322f-118">运行 Analysis Services 部署向导</span><span class="sxs-lookup"><span data-stu-id="1322f-118">Running the Analysis Services Deployment Wizard</span></span>](running-the-analysis-services-deployment-wizard.md)|<span data-ttu-id="1322f-119">说明可用于运行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导的各种方式。</span><span class="sxs-lookup"><span data-stu-id="1322f-119">Describes the various ways in which you can run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard.</span></span>|  
|[<span data-ttu-id="1322f-120">了解用于创建部署脚本的输入文件</span><span class="sxs-lookup"><span data-stu-id="1322f-120">Understanding the Input Files Used to Create the Deployment Script</span></span>](deployment-script-files-input-used-to-create-deployment-script.md)|<span data-ttu-id="1322f-121">说明 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导将哪些文件用作输入值以及每个文件包含什么内容，并提供指向说明如何修改每个输入文件中的值的主题链接。</span><span class="sxs-lookup"><span data-stu-id="1322f-121">Describes which files the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard uses as input values, what each of those files contains, and provides links to topics that describe how to modify the values in each of the input files.</span></span>|  
|[<span data-ttu-id="1322f-122">了解 Analysis Services 部署脚本</span><span class="sxs-lookup"><span data-stu-id="1322f-122">Understanding the Analysis Services Deployment Script</span></span>](understanding-the-analysis-services-deployment-script.md)|<span data-ttu-id="1322f-123">说明部署脚本包含的内容以及脚本的运行方式。</span><span class="sxs-lookup"><span data-stu-id="1322f-123">Describes what the deployment script contains and how the script runs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1322f-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1322f-124">See Also</span></span>  
 <span data-ttu-id="1322f-125">[使用 XMLA 部署模型解决方案](deploy-model-solutions-using-xmla.md) </span><span class="sxs-lookup"><span data-stu-id="1322f-125">[Deploy Model Solutions Using XMLA](deploy-model-solutions-using-xmla.md) </span></span>  
 <span data-ttu-id="1322f-126">[同步 Analysis Services 数据库](synchronize-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="1322f-126">[Synchronize Analysis Services Databases](synchronize-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="1322f-127">[了解用于创建部署脚本的输入文件](deployment-script-files-input-used-to-create-deployment-script.md) </span><span class="sxs-lookup"><span data-stu-id="1322f-127">[Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md) </span></span>  
 [<span data-ttu-id="1322f-128">使用部署实用工具部署模型解决方案</span><span class="sxs-lookup"><span data-stu-id="1322f-128">Deploy Model Solutions with the Deployment Utility</span></span>](deploy-model-solutions-with-the-deployment-utility.md)  
  
  
