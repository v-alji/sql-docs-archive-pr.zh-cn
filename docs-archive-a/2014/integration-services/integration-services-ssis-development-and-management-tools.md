---
title: Integration Services (SSIS) 和工作室环境 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- studio environments [Integration Services]
- tools [Integration Services], Business Intelligence Development Studio
- Business Intelligence Development Studio, Integration Services in
- SQL Server Management Studio [Integration Services]
- SSIS, studio environments
- SQL Server Integration Services, studio environments
- tools [Integration Services], SQL Server Management Studio
ms.assetid: 4eb73e65-d9f3-4ac6-a408-abfa85afc537
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bfe0cf7ef482dce3870db8c730c597daf1d539e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586870"
---
# <a name="integration-services-ssis-and-studio-environments"></a><span data-ttu-id="44e9e-102">ntegration Services (SSIS) 与 Studio 环境</span><span class="sxs-lookup"><span data-stu-id="44e9e-102">Integration Services (SSIS) and Studio Environments</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="44e9e-103">包含两个与 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]一起使用的 Studio：</span><span class="sxs-lookup"><span data-stu-id="44e9e-103">includes two studios for working with [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="44e9e-104">（用于开发商业解决方案所需的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包）。</span><span class="sxs-lookup"><span data-stu-id="44e9e-104">for developing the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages that a business solution requires.</span></span> [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="44e9e-105">提供了可在其中创建包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="44e9e-105">provides the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in which you create packages.</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="44e9e-106">（用于在生产环境中管理包）。</span><span class="sxs-lookup"><span data-stu-id="44e9e-106">for managing packages in a production environment.</span></span>  
  
## <a name="sql-server-data-tools"></a><span data-ttu-id="44e9e-107">SQL Server Data Tools</span><span class="sxs-lookup"><span data-stu-id="44e9e-107">SQL Server Data Tools</span></span>  
 <span data-ttu-id="44e9e-108">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]使用 ，您可以执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="44e9e-108">Working in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="44e9e-109">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 运行  导入和导出向导以创建将数据从源复制到目标的基本包。</span><span class="sxs-lookup"><span data-stu-id="44e9e-109">Run the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard to create basic packages that copy data from a source to a destination.</span></span>  
  
-   <span data-ttu-id="44e9e-110">创建包含复杂的控制流、数据流、事件驱动逻辑和日志记录的包。</span><span class="sxs-lookup"><span data-stu-id="44e9e-110">Create packages that include complex control flow, data flow, event-driven logic, and logging.</span></span>  
  
-   <span data-ttu-id="44e9e-111">[!INCLUDE[ssIS](../includes/ssis-md.md)] 使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]设计器中的故障排除和监视功能以及  中的调试功能测试并调试包。</span><span class="sxs-lookup"><span data-stu-id="44e9e-111">Test and debug packages by using the troubleshooting and monitoring features in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, and the debugging features in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="44e9e-112">创建运行时更新包和包对象属性的配置。</span><span class="sxs-lookup"><span data-stu-id="44e9e-112">Create configurations that update the properties of packages and package objects at run time.</span></span>  
  
-   <span data-ttu-id="44e9e-113">创建可在其他计算机上安装包及其依赖项的部署实用工具。</span><span class="sxs-lookup"><span data-stu-id="44e9e-113">Create a deployment utility that can install packages and their dependencies on other computers.</span></span>  
  
-   <span data-ttu-id="44e9e-114">将包的副本保存到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb 数据库、[!INCLUDE[ssIS](../includes/ssis-md.md)] 包存储和文件系统。</span><span class="sxs-lookup"><span data-stu-id="44e9e-114">Save copies of packages to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database, the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
 <span data-ttu-id="44e9e-115">有关 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的详细信息，请参阅 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686.aspx)。</span><span class="sxs-lookup"><span data-stu-id="44e9e-115">For more information about [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], see [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686.aspx).</span></span>  
  
## <a name="sql-server-management-studio"></a><span data-ttu-id="44e9e-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="44e9e-116">SQL Server Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="44e9e-117">提供 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务，该服务可用于管理包、监视正在运行的包和确定 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象的影响和数据沿袭。</span><span class="sxs-lookup"><span data-stu-id="44e9e-117">provides the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service that you use to manage packages, monitor running packages, and determine impact and data lineage for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
 <span data-ttu-id="44e9e-118">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]使用 ，您可以执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="44e9e-118">Working in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="44e9e-119">创建文件夹，用对您的单位有意义的方式来组织包。</span><span class="sxs-lookup"><span data-stu-id="44e9e-119">Create folders to organize packages in a way that is meaningful to your organization.</span></span>  
  
-   <span data-ttu-id="44e9e-120">使用执行包实用工具，运行存储在本地计算机中的包。</span><span class="sxs-lookup"><span data-stu-id="44e9e-120">Run packages that are stored on the local computer by using the Execute Package utility.</span></span>  
  
-   <span data-ttu-id="44e9e-121">运行执行包实用工具，以生成运行 **dtexec** 命令提示实用工具 (dtexec.exe) 时要使用的命令行。</span><span class="sxs-lookup"><span data-stu-id="44e9e-121">Run the Execute Package utility to generate a command line to use when you run the **dtexec** command prompt utility (dtexec.exe).</span></span>  
  
-   <span data-ttu-id="44e9e-122">对 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb 数据库、[!INCLUDE[ssIS](../includes/ssis-md.md)] 包存储区和文件系统，执行包的导入和导出。</span><span class="sxs-lookup"><span data-stu-id="44e9e-122">Import and export packages to and from the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database, the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
