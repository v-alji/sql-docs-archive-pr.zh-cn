---
title: 数据源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Integration Services], about data sources
ms.assetid: 7ac81612-9822-470f-8d0f-a1dc96142fe3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a52889627dbe61254ac1359ae97f25ee8521b6e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587967"
---
# <a name="data-sources"></a><span data-ttu-id="c84c5-102">“数据源”</span><span class="sxs-lookup"><span data-stu-id="c84c5-102">Data Sources</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="c84c5-103">包括一个可在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包中使用的设计时对象：数据源。</span><span class="sxs-lookup"><span data-stu-id="c84c5-103">includes a design-time object that you can use in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages: the data source.</span></span>  
  
 <span data-ttu-id="c84c5-104">数据源对象是对连接的引用，它至少包括一个连接字符串和一个数据源标识符。</span><span class="sxs-lookup"><span data-stu-id="c84c5-104">A data source object is a reference to a connection, and at a minimum, it includes a connection string and a data source identifier.</span></span> <span data-ttu-id="c84c5-105">数据源对象还可以包括其他元数据，如说明、名称、用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="c84c5-105">It can also include additional metadata such a description, a name, a user name, and a password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c84c5-106">只能将数据源添加到配置为使用包部署模型的项目。</span><span class="sxs-lookup"><span data-stu-id="c84c5-106">You can add data sources only to projects that are configured to use the package deployment model.</span></span> <span data-ttu-id="c84c5-107">如果将项目配置为使用项目部署模型，您使用在项目级别创建的连接管理器来共享连接，而不使用数据源。</span><span class="sxs-lookup"><span data-stu-id="c84c5-107">If a project is configured to use the project deployment model, you use connection managers created at the project level to share connections, in place of using data sources.</span></span>  
>   
>  <span data-ttu-id="c84c5-108">有关部署模型的详细信息，请参阅 [Deployment of Projects and Packages](../packages/deploy-integration-services-ssis-projects-and-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="c84c5-108">For more information about the deployment models, see [Deployment of Projects and Packages](../packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span> <span data-ttu-id="c84c5-109">有关将项目转换为项目部署模型的详细信息，请参阅 [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c84c5-109">For more information about converting a project to the project deployment model, see [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="c84c5-110">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包中使用数据源的好处如下：</span><span class="sxs-lookup"><span data-stu-id="c84c5-110">The advantages of using data sources in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages include the following:</span></span>  
  
-   <span data-ttu-id="c84c5-111">数据源具有项目作用域，这意味着在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目中创建的数据源对该项目的所有包都可用。</span><span class="sxs-lookup"><span data-stu-id="c84c5-111">A data source has project scope, which means that a data source created in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project is available to all the packages in the project.</span></span> <span data-ttu-id="c84c5-112">数据源可以在一次定义后，由多个包中的连接管理器引用。</span><span class="sxs-lookup"><span data-stu-id="c84c5-112">A data source can be defined one time and then referenced by connection managers in multiple packages.</span></span>  
  
-   <span data-ttu-id="c84c5-113">数据源提供数据源对象与其包引用之间的同步。</span><span class="sxs-lookup"><span data-stu-id="c84c5-113">A data source offers synchronization between the data source object and its package references.</span></span> <span data-ttu-id="c84c5-114">如果数据源和引用它的包在同一个项目中，在数据源更改时就会自动更新数据源引用的连接字符串属性。</span><span class="sxs-lookup"><span data-stu-id="c84c5-114">If the data source and the packages that reference it reside in the same project, the connection string property of the data source references is automatically updated when the data source changes.</span></span>  
  
## <a name="reference-data-sources"></a><span data-ttu-id="c84c5-115">引用数据源</span><span class="sxs-lookup"><span data-stu-id="c84c5-115">Reference Data Sources</span></span>  
 <span data-ttu-id="c84c5-116">要将数据源对象添加到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目，请在“解决方案资源管理器”中右键单击“数据源”文件夹，然后单击“新建数据源”。</span><span class="sxs-lookup"><span data-stu-id="c84c5-116">To add a data source object to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, right-click the **Data Sources** folder in **Solution Explorer** and then click **New Data Source**.</span></span> <span data-ttu-id="c84c5-117">该项将添加到 **“数据源”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="c84c5-117">The item is added to the **Data Sources** folder.</span></span> <span data-ttu-id="c84c5-118">如果要使用在其他项目中创建的数据源对象，则必须首先将其添加到该项目。</span><span class="sxs-lookup"><span data-stu-id="c84c5-118">If you want to use data source objects that were created in other projects, you must first add them to the project.</span></span>  
  
 <span data-ttu-id="c84c5-119">将引用数据源对象的连接管理器添加到包之后，便可以在该包中使用数据源对象。</span><span class="sxs-lookup"><span data-stu-id="c84c5-119">You use a data source object in a package by adding a connection manager that references the data source object to the package.</span></span> <span data-ttu-id="c84c5-120">可以在生成包控制流和数据流之前将其添加到包中，也可以作为构造控制流和数据流的一个步骤来添加。</span><span class="sxs-lookup"><span data-stu-id="c84c5-120">You can add it to the package before you build the package control flow and data flows, or as a step in constructing the control flow or data flow.</span></span>  
  
 <span data-ttu-id="c84c5-121">数据源对象表示对数据源的简单连接，通过它可以访问它所引用的数据存储区中的对象。</span><span class="sxs-lookup"><span data-stu-id="c84c5-121">A data source object represents a simple connection to a data source and provides access to the objects in the data store that it references.</span></span> <span data-ttu-id="c84c5-122">例如，连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]AdventureWorks 示例数据库的数据源对象包括来自该数据库的所有 60 个表。</span><span class="sxs-lookup"><span data-stu-id="c84c5-122">For example, a data source object that connects to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]AdventureWorks Sample Database includes all 60 tables from the database.</span></span>  
  
 <span data-ttu-id="c84c5-123">在数据源和引用它的连接管理器之间没有依赖关系。</span><span class="sxs-lookup"><span data-stu-id="c84c5-123">There is no dependency between a data source and the connection managers that reference it.</span></span> <span data-ttu-id="c84c5-124">即使数据源不再是项目的一部分，包仍然有效，因为有关该数据源的信息（例如其连接类型和连接字符串）已包括在包定义中。</span><span class="sxs-lookup"><span data-stu-id="c84c5-124">If a data source is no longer part of the project, the packages continue to be valid, because information about the data source, such as its connection type and connection string, is included in the package definition.</span></span>  
  
  
