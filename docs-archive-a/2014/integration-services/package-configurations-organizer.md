---
title: 包配置组织程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.packageconfigurationorganizer.f1
helpviewer_keywords:
- Package Configurations Organizer dialog box
ms.assetid: f20ae6cb-9e6a-4d24-88ff-d7a903a4e8d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67fdc9ca0faeff57c18fdb6e4d10acca3e9963f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691787"
---
# <a name="package-configurations-organizer"></a><span data-ttu-id="b998a-102">“包配置组织程序”</span><span class="sxs-lookup"><span data-stu-id="b998a-102">Package Configurations Organizer</span></span>
  <span data-ttu-id="b998a-103">可以使用 **“包配置组织程序”** 对话框启用包配置，查看当前包的配置列表以及指定加载这些配置的首选顺序。</span><span class="sxs-lookup"><span data-stu-id="b998a-103">Use the **Package Configurations Organizer** dialog box to enable package configurations, view a list of configurations for the current package, and specify the preferred order in which the configurations should be loaded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b998a-104">配置可用于包部署模型。</span><span class="sxs-lookup"><span data-stu-id="b998a-104">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="b998a-105">对于项目部署模型，参数用于代替配置。</span><span class="sxs-lookup"><span data-stu-id="b998a-105">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="b998a-106">项目部署模型使您可以将 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="b998a-106">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="b998a-107">有关部署模型的详细信息，请参阅 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="b998a-107">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="b998a-108">如果多个配置更新同一属性，则在配置列表中排列靠后的配置的值将代替在列表中排列靠前的配置的值。</span><span class="sxs-lookup"><span data-stu-id="b998a-108">If multiple configurations update the same property, values from configurations listed lower in the configuration list will replace values from configurations higher in the list.</span></span> <span data-ttu-id="b998a-109">最后加载到属性中的值是在包运行时将要使用的值。</span><span class="sxs-lookup"><span data-stu-id="b998a-109">The last value loaded into the property is the value that is used when the package runs.</span></span> <span data-ttu-id="b998a-110">而且，如果包使用直接配置（例如 XML 配置文件）和间接配置（例如环境变量）的组合，那么指向直接配置的位置的间接配置必须在列表中处于靠前位置。</span><span class="sxs-lookup"><span data-stu-id="b998a-110">Also, if the package uses a combination of direct configuration such as an XML configuration file and an indirect configuration such as an environment variable, the indirect configuration that points to the location of the direct configuration must be higher in the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b998a-111">如果包配置按照首选顺序加载，则配置按照从 **“包配置组织程序”** 对话框中显示的列表顶部到列表底部的顺序进行加载。</span><span class="sxs-lookup"><span data-stu-id="b998a-111">When package configurations load in the preferred order, configurations load from the top of the list shown in the **Package Configuration Organizer** dialog box to the bottom of the list.</span></span> <span data-ttu-id="b998a-112">但是，在运行时，包配置可能不会按照首选顺序加载。</span><span class="sxs-lookup"><span data-stu-id="b998a-112">However, at run time, package configurations might not load in the preferred order.</span></span> <span data-ttu-id="b998a-113">父包配置将在其他类型的配置之后加载的情况尤其如此。</span><span class="sxs-lookup"><span data-stu-id="b998a-113">In particular, Parent Package Configurations load after configurations of other types.</span></span>  
  
 <span data-ttu-id="b998a-114">在运行时，包配置将更新包对象的属性值。</span><span class="sxs-lookup"><span data-stu-id="b998a-114">Package configurations update the values of properties of package objects at run time.</span></span> <span data-ttu-id="b998a-115">加载包时，配置中的值将替换开发包时所设置的值。</span><span class="sxs-lookup"><span data-stu-id="b998a-115">When a package is loaded, the values from the configurations replace the values that were set when the package was developed.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="b998a-116">支持不同的配置类型。</span><span class="sxs-lookup"><span data-stu-id="b998a-116">supports different configuration types.</span></span> <span data-ttu-id="b998a-117">例如，您可以使用包含多个配置的 XML 文件或包含单个配置的环境变量。</span><span class="sxs-lookup"><span data-stu-id="b998a-117">For example, you can use an XML file that can contain multiple configurations, or an environment variable that contains a single configuration.</span></span> <span data-ttu-id="b998a-118">有关详细信息，请参阅 [Package Configurations](../../2014/integration-services/package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="b998a-118">For more information, see [Package Configurations](../../2014/integration-services/package-configurations.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b998a-119">选项</span><span class="sxs-lookup"><span data-stu-id="b998a-119">Options</span></span>  
 <span data-ttu-id="b998a-120">**启用包配置**</span><span class="sxs-lookup"><span data-stu-id="b998a-120">**Enable package configurations**</span></span>  
 <span data-ttu-id="b998a-121">选择此选项可对包使用配置。</span><span class="sxs-lookup"><span data-stu-id="b998a-121">Select to use configurations with the package.</span></span>  
  
 <span data-ttu-id="b998a-122">**配置名称**</span><span class="sxs-lookup"><span data-stu-id="b998a-122">**Configuration Name**</span></span>  
 <span data-ttu-id="b998a-123">查看配置的名称。</span><span class="sxs-lookup"><span data-stu-id="b998a-123">View the name of the configuration.</span></span>  
  
 <span data-ttu-id="b998a-124">**配置类型**</span><span class="sxs-lookup"><span data-stu-id="b998a-124">**Configuration Type**</span></span>  
 <span data-ttu-id="b998a-125">查看存储配置的位置类型。</span><span class="sxs-lookup"><span data-stu-id="b998a-125">View the type of the location where configurations are stored.</span></span>  
  
 <span data-ttu-id="b998a-126">**配置字符串**</span><span class="sxs-lookup"><span data-stu-id="b998a-126">**Configuration String**</span></span>  
 <span data-ttu-id="b998a-127">查看存储配置值的位置。</span><span class="sxs-lookup"><span data-stu-id="b998a-127">View the location where the configuration values are stored.</span></span> <span data-ttu-id="b998a-128">该位置可以是文件路径、环境变量的名称、父级包变量的名称、注册表项或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 表的名称。</span><span class="sxs-lookup"><span data-stu-id="b998a-128">The location can be the path of a file, the name of an environment variable, the name of a parent package variable, a Registry key, or the name of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="b998a-129">**目标对象**</span><span class="sxs-lookup"><span data-stu-id="b998a-129">**Target Object**</span></span>  
 <span data-ttu-id="b998a-130">查看配置更新的对象的名称。</span><span class="sxs-lookup"><span data-stu-id="b998a-130">View the name of the object that the configuration updates.</span></span> <span data-ttu-id="b998a-131">如果配置是 XML 配置文件或 SQL Server 表，则列为空，因为配置可以包含多个对象。</span><span class="sxs-lookup"><span data-stu-id="b998a-131">If the configuration is an XML configuration file or a SQL Server table, the column is blank because the configuration can include multiple objects.</span></span>  
  
 <span data-ttu-id="b998a-132">**目标属性**</span><span class="sxs-lookup"><span data-stu-id="b998a-132">**Target Property**</span></span>  
 <span data-ttu-id="b998a-133">查看配置修改的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="b998a-133">View the name of the property modified by the configuration.</span></span> <span data-ttu-id="b998a-134">如果配置类型支持多个配置，则此列为空白。</span><span class="sxs-lookup"><span data-stu-id="b998a-134">This column is blank if the configuration type supports multiple configurations.</span></span>  
  
 <span data-ttu-id="b998a-135">**添加**</span><span class="sxs-lookup"><span data-stu-id="b998a-135">**Add**</span></span>  
 <span data-ttu-id="b998a-136">通过使用包配置向导来添加配置。</span><span class="sxs-lookup"><span data-stu-id="b998a-136">Add a configuration by using the Package Configuration Wizard.</span></span>  
  
 <span data-ttu-id="b998a-137">**编辑**</span><span class="sxs-lookup"><span data-stu-id="b998a-137">**Edit**</span></span>  
 <span data-ttu-id="b998a-138">通过重新运行包配置向导来编辑现有配置。</span><span class="sxs-lookup"><span data-stu-id="b998a-138">Edit an existing configuration by rerunning the Package Configuration Wizard.</span></span>  
  
 <span data-ttu-id="b998a-139">**删除**</span><span class="sxs-lookup"><span data-stu-id="b998a-139">**Remove**</span></span>  
 <span data-ttu-id="b998a-140">选择一个配置，再单击“删除”。</span><span class="sxs-lookup"><span data-stu-id="b998a-140">Select a configuration, and then click **Remove**.</span></span>  
  
 <span data-ttu-id="b998a-141">**箭头**</span><span class="sxs-lookup"><span data-stu-id="b998a-141">**Arrows**</span></span>  
 <span data-ttu-id="b998a-142">在列表中选择一个配置，再使用向上键和向下键可将其上移或下移。</span><span class="sxs-lookup"><span data-stu-id="b998a-142">Select a configuration and use the up and down arrows to move it up or down in the list.</span></span> <span data-ttu-id="b998a-143">配置将按照在列表中的显示顺序来进行加载。</span><span class="sxs-lookup"><span data-stu-id="b998a-143">Configurations are loaded in the sequence in which they appear in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b998a-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b998a-144">See Also</span></span>  
 [<span data-ttu-id="b998a-145">创建包配置</span><span class="sxs-lookup"><span data-stu-id="b998a-145">Create Package Configurations</span></span>](../../2014/integration-services/create-package-configurations.md)  
  
  
