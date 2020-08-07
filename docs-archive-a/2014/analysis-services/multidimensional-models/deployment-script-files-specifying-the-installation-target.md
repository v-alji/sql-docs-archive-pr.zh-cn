---
title: 指定安装目标 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- installation targets [Analysis Services]
- Analysis Services deployments, installation targets
- Analysis Services Deployment Wizard, installation targets
- deploying [Analysis Services], installation targets
- modifying installation targets
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
author: minewiskan
ms.author: owend
ms.openlocfilehash: e830fc353898e3ec835b338e84765a0cad0de43f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587636"
---
# <a name="specifying-the-installation-target"></a><span data-ttu-id="0cc7d-102">指定安装目标</span><span class="sxs-lookup"><span data-stu-id="0cc7d-102">Specifying the Installation Target</span></span>
  <span data-ttu-id="0cc7d-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]部署向导从 .deploymenttargets 文件中读取安装目标信息 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="0cc7d-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the installation target information from the \<*project name*>.deploymenttargets file.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="0cc7d-104">在生成项目时创建此文件 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0cc7d-104">creates this file when you build the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="0cc7d-105">使用在 "属性页" 对话框的 "**部署**" 页上指定的数据库和服务器 *\<project name>* **Properties Pages**来创建 \<*project name*> .targets 文件。</span><span class="sxs-lookup"><span data-stu-id="0cc7d-105">uses the database and server specified on the **Deployment** page of the *\<project name>* **Properties Pages** dialog box to create the \<*project name*>.targets file.</span></span>  
  
## <a name="modifying-the-installation-target-for-deployment"></a><span data-ttu-id="0cc7d-106">修改部署的安装目标</span><span class="sxs-lookup"><span data-stu-id="0cc7d-106">Modifying the Installation Target for Deployment</span></span>  
 <span data-ttu-id="0cc7d-107">在有些情况下，可能需要将 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目部署到与 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] “部署” **页上指定的项不同的数据库或** 实例。</span><span class="sxs-lookup"><span data-stu-id="0cc7d-107">In some situations, you may need to deploy an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project to a database or [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that is different than the one specified on the **Deployment** page.</span></span> <span data-ttu-id="0cc7d-108">例如，可能要在部署之前将项目部署到用于测试的服务器，再在测试完成后将其部署到生产服务器。</span><span class="sxs-lookup"><span data-stu-id="0cc7d-108">For example, you may want to deploy the project to a server for testing before deployment, and then deploy it to a production server after testing is finished.</span></span> <span data-ttu-id="0cc7d-109">此外，还可能需要将已完成且经过测试的项目部署到网络负载平衡群集中的多台生产服务器，或将其部署到临时服务器和生产服务器。</span><span class="sxs-lookup"><span data-stu-id="0cc7d-109">You may also want to deploy a completed and tested project to multiple production servers in a Network Load Balancing cluster, or to a staging server and a production server.</span></span>  
  
 <span data-ttu-id="0cc7d-110">若要将 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目部署到其他数据库或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例，可使用下列过程中介绍的方法之一，在输入文件中更改安装目标。</span><span class="sxs-lookup"><span data-stu-id="0cc7d-110">To deploy an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project to a different database or [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, you can change the installation target in the input file by using one of the methods described in the following procedure.</span></span>  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a><span data-ttu-id="0cc7d-111">在生成了输入文件后更改安装目标</span><span class="sxs-lookup"><span data-stu-id="0cc7d-111">To change the installation target after the input files have been generated</span></span>  
  
-   <span data-ttu-id="0cc7d-112">以交互方式运行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导。</span><span class="sxs-lookup"><span data-stu-id="0cc7d-112">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard interactively.</span></span> <span data-ttu-id="0cc7d-113">在 **“安装目标”** 页上，为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例和数据库指定新的目标。</span><span class="sxs-lookup"><span data-stu-id="0cc7d-113">On the **Installation Target** page, specify a new destination for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and database.</span></span>  
  
     <span data-ttu-id="0cc7d-114">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="0cc7d-114">-or-</span></span>  
  
-   <span data-ttu-id="0cc7d-115">在命令提示符下运行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导，并设置向导，使其以应答文件模式运行。</span><span class="sxs-lookup"><span data-stu-id="0cc7d-115">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt and set the wizard to run in answer file mode.</span></span> <span data-ttu-id="0cc7d-116">有关应答文件模式的详细信息，请参阅 [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="0cc7d-116">For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).</span></span>  
  
     <span data-ttu-id="0cc7d-117">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="0cc7d-117">-or-</span></span>  
  
-   <span data-ttu-id="0cc7d-118">\<*project name*>使用任意文本编辑器修改 .deploymenttargets 文件。</span><span class="sxs-lookup"><span data-stu-id="0cc7d-118">Modify the \<*project name*>.deploymenttargets file by using any text editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cc7d-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0cc7d-119">See Also</span></span>  
 <span data-ttu-id="0cc7d-120">[指定分区和角色部署选项](deployment-script-files-partition-and-role-deployment-options.md) </span><span class="sxs-lookup"><span data-stu-id="0cc7d-120">[Specifying Partition and Role Deployment Options](deployment-script-files-partition-and-role-deployment-options.md) </span></span>  
 <span data-ttu-id="0cc7d-121">[为解决方案部署指定配置设置](deployment-script-files-solution-deployment-config-settings.md) </span><span class="sxs-lookup"><span data-stu-id="0cc7d-121">[Specifying Configuration Settings for Solution Deployment](deployment-script-files-solution-deployment-config-settings.md) </span></span>  
 [<span data-ttu-id="0cc7d-122">指定处理选项</span><span class="sxs-lookup"><span data-stu-id="0cc7d-122">Specifying Processing Options</span></span>](deployment-script-files-specifying-processing-options.md)  
  
  
