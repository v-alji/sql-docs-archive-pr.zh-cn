---
title: " (SSDT) 部署 Analysis Services 项目 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- deploy [Analysis Services]
- projects [Analysis Services], deploying
- Business Intelligence Development Studio, deploying projects [Analysis Services]
ms.assetid: 29490a5b-1573-4a35-9277-10c6a6e4ef0e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5317eea19d088a8d3f9d8bfb86da4e0429d62c3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587080"
---
# <a name="deploy-analysis-services-projects-ssdt"></a><span data-ttu-id="d1ddc-102">部署 Analysis Services 项目 (SSDT)</span><span class="sxs-lookup"><span data-stu-id="d1ddc-102">Deploy Analysis Services Projects (SSDT)</span></span>
  <span data-ttu-id="d1ddc-103">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中开发 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]项目时，应经常将项目部署到开发服务器以创建项目所定义的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-103">During development of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you frequently deploy the project to a development server in order to create the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database defined by the project.</span></span> <span data-ttu-id="d1ddc-104">这是测试项目所必需的；例如，浏览多维数据集中的单元，浏览维度成员或验证关键绩效指标 (KPI) 公式。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-104">This is required to test the project; for example, to browse cells in the cube, browse dimension members, or verify key performance indicators (KPIs) formulas.</span></span>  
  
## <a name="deploying-a-project"></a><span data-ttu-id="d1ddc-105">部署项目</span><span class="sxs-lookup"><span data-stu-id="d1ddc-105">Deploying a Project</span></span>  
 <span data-ttu-id="d1ddc-106">您可以独立部署项目，也可以部署解决方案中的所有项目。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-106">You can deploy a project independently, or you can deploy all of the projects within the solution.</span></span> <span data-ttu-id="d1ddc-107">部署项目时，将按顺序执行数个操作。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-107">When you deploy a project, several things happen in sequence.</span></span> <span data-ttu-id="d1ddc-108">首先，生成项目。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-108">First, the project is built.</span></span> <span data-ttu-id="d1ddc-109">此步骤创建了定义 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库及其构成对象的输出文件。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-109">This step creates the output files that define the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and its constituent objects.</span></span> <span data-ttu-id="d1ddc-110">接下来，验证目标服务器。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-110">Next, the destination server is validated.</span></span> <span data-ttu-id="d1ddc-111">最后，在目标服务器上创建目标数据库及其对象。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-111">Finally, the destination database and its objects are created on the destination server.</span></span> <span data-ttu-id="d1ddc-112">除非在先前的部署过程中项目创建了这些对象，否则部署过程中，部署引擎会将预先存在的数据库完全替换为项目内容。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-112">During deployment, the deployment engine totally replaces any pre-existing database with the contents of the project unless those objects were created by the project during a previous deployment.</span></span>  
  
 <span data-ttu-id="d1ddc-113">初始部署后，在 \obj 文件夹中生成 IncrementalSnapshot.xml 文件 \<Project Name> 。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-113">After an initial deployment, an IncrementalSnapshot.xml file is generated in the \<Project Name>\obj folder.</span></span> <span data-ttu-id="d1ddc-114">此文件用于确定目标服务器上的数据库或其对象是否已在项目外部进行了更改。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-114">This file is used to determine if the database or its objects on the destination server have changed outside of the project.</span></span> <span data-ttu-id="d1ddc-115">如果进行了更改，则系统将提示您覆盖目标数据库中的所有对象。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-115">If so, you will be prompted to overwrite all objects in the destination database.</span></span> <span data-ttu-id="d1ddc-116">如果在项目中进行了所有更改并且将项目配置为增量部署，则仅将更改部署到目标服务器。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-116">If all changes were made within the project and the project is configured for incremental deployment, only the changes will be deployed to the destination server.</span></span>  
  
 <span data-ttu-id="d1ddc-117">项目配置及其关联的设置确定将用于部署项目的部署属性。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-117">The project configuration and its associated settings determine the deployment properties that will be used to deploy the project.</span></span> <span data-ttu-id="d1ddc-118">对于共享项目，每个开发人员都可以将自己的配置用于自己的项目配置选项。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-118">For a shared project, each developer can use their own configuration with their own project configuration options.</span></span> <span data-ttu-id="d1ddc-119">例如，每个开发人员都可以指定不同的测试服务器，以便将自己的工作与其他开发人员的工作区隔开来。</span><span class="sxs-lookup"><span data-stu-id="d1ddc-119">For example, each developer can specify a different test server to work in isolation from other developers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ddc-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1ddc-120">See Also</span></span>  
 [<span data-ttu-id="d1ddc-121">创建 Analysis Services 项目 (SSDT)</span><span class="sxs-lookup"><span data-stu-id="d1ddc-121">Create an Analysis Services Project &#40;SSDT&#41;</span></span>](create-an-analysis-services-project-ssdt.md)  
  
  
