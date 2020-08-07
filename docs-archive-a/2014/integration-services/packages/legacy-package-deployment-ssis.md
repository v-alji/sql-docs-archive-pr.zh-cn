---
title: 包部署 (SSIS) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, deploying
- deploying packages [Integration Services]
- SQL Server Integration Services packages, deploying
- deploying packages [Integration Services], about deploying packages
- packages [Integration Services], deploying
- SSIS packages, deploying
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 32627eddf5e7a696decd549e9b87ebb5c3b9d031
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587896"
---
# <a name="package-deployment-ssis"></a><span data-ttu-id="63fed-102">包部署 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="63fed-102">Package Deployment (SSIS)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="63fed-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包括一些工具和向导，它们简化了将包从开发计算机部署到生产服务器或其他计算机的过程。</span><span class="sxs-lookup"><span data-stu-id="63fed-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes tools and wizards that make it simple to deploy packages from the development computer to the production server or to other computers.</span></span>  
  
 <span data-ttu-id="63fed-104">包部署过程中有四个步骤：</span><span class="sxs-lookup"><span data-stu-id="63fed-104">There are four steps in the package deployment process:</span></span>  
  
1.  <span data-ttu-id="63fed-105">第一个可选步骤是可选的，包括创建在运行时更新包元素属性的包配置。</span><span class="sxs-lookup"><span data-stu-id="63fed-105">The first optional step is optional and involves creating package configurations that update properties of package elements at run time.</span></span> <span data-ttu-id="63fed-106">部署包时会自动包括这些配置。</span><span class="sxs-lookup"><span data-stu-id="63fed-106">The configurations are automatically included when you deploy the packages.</span></span>  
  
2.  <span data-ttu-id="63fed-107">第二步是生成 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目，用于创建包部署实用工具。</span><span class="sxs-lookup"><span data-stu-id="63fed-107">The second step is to build the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project to create a package deployment utility.</span></span> <span data-ttu-id="63fed-108">项目的部署实用工具包含要部署的包</span><span class="sxs-lookup"><span data-stu-id="63fed-108">The deployment utility for the project contains the packages that you want to deploy</span></span>  
  
3.  <span data-ttu-id="63fed-109">第三步是将生成 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目时创建的部署文件夹复制到目标计算机中。</span><span class="sxs-lookup"><span data-stu-id="63fed-109">The third step is to copy the deployment folder that was created when you built the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project to the target computer.</span></span>  
  
4.  <span data-ttu-id="63fed-110">第四步是在目标计算机上运行包安装向导，以将包安装到文件系统或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="63fed-110">The fourth step is to run, on the target computer, the Package Installation Wizard to install the packages to the file system or to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="63fed-111">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="63fed-111">Related Tasks</span></span>  
 <span data-ttu-id="63fed-112">有关如何创建部署实用工具的信息，请参阅 [创建部署实用工具](../create-a-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="63fed-112">For information about how to create a deployment utility, see [Create a Deployment Utility](../create-a-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="63fed-113">有关如何使用部署实用工具部署包的信息，请参阅 [使用部署实用工具部署包](../deploy-packages-by-using-the-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="63fed-113">For information about how to deploy packages using the deployment utility, see [Deploy Packages by Using the Deployment Utility](../deploy-packages-by-using-the-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="63fed-114">有关如何创建包配置的信息，请参阅 [创建包配置](../create-package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="63fed-114">For information about how to create package configurations, see [Create Package Configurations](../create-package-configurations.md).</span></span>  
  
  
