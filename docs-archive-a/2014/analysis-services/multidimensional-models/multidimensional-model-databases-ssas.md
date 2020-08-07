---
title: 多维模型数据库 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [Analysis Services], databases
- SQL Server Analysis Services, databases
- SSAS, databases
- Analysis Services, databases
- databases [Analysis Services], designing
- Business Intelligence Development Studio, databases [Analysis Services]
- databases [Analysis Services]
ms.assetid: 78b2f22a-b7bd-4a2b-b6fc-0bff4d2b3168
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8dc4e7c872f87244e8353c80bd9acfcce584c167
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587624"
---
# <a name="multidimensional-model-databases-ssas"></a><span data-ttu-id="8f37a-102">多维模型数据库 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="8f37a-102">Multidimensional Model Databases (SSAS)</span></span>
  <span data-ttu-id="8f37a-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库是数据源、数据源视图、多维数据集、维度以及角色的集合。</span><span class="sxs-lookup"><span data-stu-id="8f37a-103">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database is a collection of data sources, data source views, cubes, dimensions, and roles.</span></span> <span data-ttu-id="8f37a-104">此外， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库可以选择包含数据挖掘的结构以及一些自定义程序集，通过这些程序集，您可以将用户定义函数添加到数据库。</span><span class="sxs-lookup"><span data-stu-id="8f37a-104">Optionally, an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database can include structures for data mining, and custom assemblies that provide a way for you to add user-defined functions to the database.</span></span>  
  
 <span data-ttu-id="8f37a-105">多维数据集是 Analysis Services 中的基本查询对象。</span><span class="sxs-lookup"><span data-stu-id="8f37a-105">Cubes are the fundamental query objects in Analysis Services.</span></span> <span data-ttu-id="8f37a-106">当通过客户端应用程序连接到 Analysis Services 数据库时，可以连接到该数据库中的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8f37a-106">When you connect to an Analysis Services database via a client application, you connect to a cube within that database.</span></span> <span data-ttu-id="8f37a-107">如果正在跨多个上下文重用维度、程序集、角色或挖掘结构，数据库可能包含多个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8f37a-107">A database might contain multiple cubes if you are reusing dimensions, assemblies, roles, or mining structures across multiple contexts.</span></span>  
  
 <span data-ttu-id="8f37a-108">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 可以使用下列交互方式之一或以编程方式创建和修改  数据库：</span><span class="sxs-lookup"><span data-stu-id="8f37a-108">You can create and modify a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database programmatically or by using one of these interactive methods:</span></span>  
  
-   <span data-ttu-id="8f37a-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 项目从 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]部署到指定的  实例。</span><span class="sxs-lookup"><span data-stu-id="8f37a-109">Deploy an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to a designated instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="8f37a-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 如果该实例中没有同名的数据库，则此过程会创建  数据库，并在新创建的数据库中实例化已设计的对象。</span><span class="sxs-lookup"><span data-stu-id="8f37a-110">This process creates an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, if a database with that name does not already exist within that instance, and instantiates the designed objects within the newly created database.</span></span> <span data-ttu-id="8f37a-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库时，仅当将 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目部署到  实例时，对此项目中的对象所做的更改才会生效。</span><span class="sxs-lookup"><span data-stu-id="8f37a-111">When working with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], changes made to objects in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project take effect only when the project is deployed to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="8f37a-112">使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 实例中创建一个空的 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]数据库，然后使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 直接连接到该数据库并在其中（而不是在项目中）创建对象。</span><span class="sxs-lookup"><span data-stu-id="8f37a-112">Create an empty [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database within an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and then connect directly to that database using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and create objects within it (rather than within a project).</span></span> <span data-ttu-id="8f37a-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 按此方式使用  数据库时，保存已更改的对象后，对对象所做的更改也会在要连接到的数据库中生效。</span><span class="sxs-lookup"><span data-stu-id="8f37a-113">When working with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in this manner, changes made to objects take effect in the database to which you are connecting when the changed object is saved.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="8f37a-114">通过与源代码管理软件集成来支持多个开发人员同时使用一个 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目中的不同对象。</span><span class="sxs-lookup"><span data-stu-id="8f37a-114">uses integration with source control software to support multiple developers working with different objects within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project at the same time.</span></span> <span data-ttu-id="8f37a-115">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 开发人员也可以与 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库直接进行交互，而不通过 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目，但是这样做的风险是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库中的对象可能会与用于其部署的  项目不同步。</span><span class="sxs-lookup"><span data-stu-id="8f37a-115">A developer can also interact with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database directly, rather than through an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, but the risk of this is that the objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database can become out of sync with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project that was used for its deployment.</span></span> <span data-ttu-id="8f37a-116">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署之后，可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]来管理  数据库。</span><span class="sxs-lookup"><span data-stu-id="8f37a-116">After deployment, you administer an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="8f37a-117">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 还可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]对 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库（例如对分区和角色）进行某些更改，这些更改也可能会导致 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库中的对象与用于其部署的  项目不同步。</span><span class="sxs-lookup"><span data-stu-id="8f37a-117">Certain changes can also be made to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], such as to partitions and roles, which can also cause the objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database to become out of sync with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project that was used for its deployment.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="8f37a-118">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="8f37a-118">Related Tasks</span></span>  
 [<span data-ttu-id="8f37a-119">附加和分离 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="8f37a-119">Attach and Detach Analysis Services Databases</span></span>](attach-and-detach-analysis-services-databases.md)  
  
 [<span data-ttu-id="8f37a-120">备份和还原 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="8f37a-120">Backup and Restore of Analysis Services Databases</span></span>](backup-and-restore-of-analysis-services-databases.md)  
  
 [<span data-ttu-id="8f37a-121">记录和编写 Analysis Services 数据库脚本</span><span class="sxs-lookup"><span data-stu-id="8f37a-121">Document and Script an Analysis Services Database</span></span>](document-and-script-an-analysis-services-database.md)  
  
 [<span data-ttu-id="8f37a-122">修改或删除 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="8f37a-122">Modify or Delete an Analysis Services Database</span></span>](modify-or-delete-an-analysis-services-database.md)  
  
 [<span data-ttu-id="8f37a-123">移动 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="8f37a-123">Move an Analysis Services Database</span></span>](move-an-analysis-services-database.md)  
  
 [<span data-ttu-id="8f37a-124">重命名多维数据库 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8f37a-124">Rename a Multidimensional Database &#40;Analysis Services&#41;</span></span>](rename-a-multidimensional-database-analysis-services.md)  
  
 [<span data-ttu-id="8f37a-125">设置多维数据库 &#40;Analysis Services 的兼容级别&#41;</span><span class="sxs-lookup"><span data-stu-id="8f37a-125">Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;</span></span>](compatibility-level-of-a-multidimensional-database-analysis-services.md)  
  
 [<span data-ttu-id="8f37a-126">设置多维数据库属性 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8f37a-126">Set Multidimensional Database Properties &#40;Analysis Services&#41;</span></span>](set-multidimensional-database-properties-analysis-services.md)  
  
 [<span data-ttu-id="8f37a-127">同步 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="8f37a-127">Synchronize Analysis Services Databases</span></span>](synchronize-analysis-services-databases.md)  
  
 [<span data-ttu-id="8f37a-128">在 ReadOnly 和 ReadWrite 模式之间切换 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="8f37a-128">Switch an Analysis Services database between ReadOnly and ReadWrite modes</span></span>](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
## <a name="see-also"></a><span data-ttu-id="8f37a-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f37a-129">See Also</span></span>  
 <span data-ttu-id="8f37a-130">[以联机模式连接到 Analysis Services 数据库](connect-in-online-mode-to-an-analysis-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="8f37a-130">[Connect in Online Mode to an Analysis Services Database](connect-in-online-mode-to-an-analysis-services-database.md) </span></span>  
 <span data-ttu-id="8f37a-131">[&#40;SSDT 创建 Analysis Services 项目&#41;](create-an-analysis-services-project-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="8f37a-131">[Create an Analysis Services Project &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md) </span></span>  
 [<span data-ttu-id="8f37a-132">使用 MDX 查询多维数据</span><span class="sxs-lookup"><span data-stu-id="8f37a-132">Querying Multidimensional Data with MDX</span></span>](mdx/querying-multidimensional-data-with-mdx.md)  
  
  
