---
title: 将包另存为包模板 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- reusing packages
- templates [Integration Services]
ms.assetid: efe66cec-3933-4f6e-8d35-fe3d300de66c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 30bddb5a343e7c7aef279bc66c25be30a2cf1a12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688986"
---
# <a name="save-a-package-as-a-package-template"></a><span data-ttu-id="d8db6-102">将包另存为包模板</span><span class="sxs-lookup"><span data-stu-id="d8db6-102">Save a Package as a Package Template</span></span>
  <span data-ttu-id="d8db6-103">本主题介绍在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中创建新的 Integration Services 包时如何指定自定义包以及将自定义包作为模板。</span><span class="sxs-lookup"><span data-stu-id="d8db6-103">This topic describes how to designate and use custom packages as templates when you create new Integration Services packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="d8db6-104">默认情况下，在将新包添加到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中时， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 使用创建空包的包模板。</span><span class="sxs-lookup"><span data-stu-id="d8db6-104">By default, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] uses a package template that creates an empty package when you add a new package to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="d8db6-105">您无法替换此默认模板，但可以添加新的模板。</span><span class="sxs-lookup"><span data-stu-id="d8db6-105">You cannot replace this default template, but you can add new templates.</span></span>  
  
 <span data-ttu-id="d8db6-106">可以指定多个包用作模板。</span><span class="sxs-lookup"><span data-stu-id="d8db6-106">You can designate multiple packages to use as templates.</span></span> <span data-ttu-id="d8db6-107">必须先创建这些包，然后才能实现将自定义包作为模板。</span><span class="sxs-lookup"><span data-stu-id="d8db6-107">Before you can implement custom packages as templates, you must create the packages.</span></span>  
  
 <span data-ttu-id="d8db6-108">使用自定义包作为模板来创建包时，新的包将具有与模板相同的名称和 GUID。</span><span class="sxs-lookup"><span data-stu-id="d8db6-108">When you create package using custom packages as templates, the new packages have the same name and GUID as the template.</span></span> <span data-ttu-id="d8db6-109">若要区分这些包，应当更新 `Name` 属性的值，并为 `ID` 属性生成新的 GUID。</span><span class="sxs-lookup"><span data-stu-id="d8db6-109">To differentiate among packages you should update the value of the `Name` property and generate a new GUID for the `ID` property.</span></span> <span data-ttu-id="d8db6-110">有关详细信息，请参阅 [在 SQL Server Data Tools 中创建包](create-packages-in-sql-server-data-tools.md) 和 [设置包属性](set-package-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d8db6-110">For more information, see [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) and [Set Package Properties](set-package-properties.md).</span></span>  
  
### <a name="to-designate-a-custom-package-as-a-package-template"></a><span data-ttu-id="d8db6-111">将自定义包指定为包模板</span><span class="sxs-lookup"><span data-stu-id="d8db6-111">To designate a custom package as a package template</span></span>  
  
1.  <span data-ttu-id="d8db6-112">在文件系统中，找到要用作模板的包。</span><span class="sxs-lookup"><span data-stu-id="d8db6-112">In the file system, locate the package that you want to use as template.</span></span>  
  
2.  <span data-ttu-id="d8db6-113">将此包复制到 DataTransformationItems 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="d8db6-113">Copy the package to the DataTransformationItems folder.</span></span> <span data-ttu-id="d8db6-114">默认情况下，此文件夹位于 C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject。</span><span class="sxs-lookup"><span data-stu-id="d8db6-114">By default this folder is in C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject.</span></span>  
  
3.  <span data-ttu-id="d8db6-115">对每个要用作模板的包重复步骤 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="d8db6-115">Repeat steps 1 and 2 for each package that you want to use as a template.</span></span>  
  
### <a name="to-use-a-custom-package-as-a-package-template"></a><span data-ttu-id="d8db6-116">使用自定义包作为包模板</span><span class="sxs-lookup"><span data-stu-id="d8db6-116">To use a custom package as a package template</span></span>  
  
1.  <span data-ttu-id="d8db6-117">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开要在其中创建包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="d8db6-117">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in which you want to create a package.</span></span>  
  
2.  <span data-ttu-id="d8db6-118">在解决方案资源管理器中，右键单击项目，指向“添加”，然后单击“新建项”。</span><span class="sxs-lookup"><span data-stu-id="d8db6-118">In Solution Explorer, right-click the project, point to **Add**, and then click **New Item**.</span></span>  
  
3.  <span data-ttu-id="d8db6-119">在“添加新项 -\<project name>”对话框中，单击要用作模板的包。</span><span class="sxs-lookup"><span data-stu-id="d8db6-119">In the **Add New Item -\<project name>** dialog box, click the package that you want to use as a template.</span></span>  
  
     <span data-ttu-id="d8db6-120">模板列表包括名为“新建 SSIS 包”的默认包模板。</span><span class="sxs-lookup"><span data-stu-id="d8db6-120">The list of templates includes the default package template named New SSIS Package.</span></span> <span data-ttu-id="d8db6-121">包图标将标识可以用作包模板的模板。</span><span class="sxs-lookup"><span data-stu-id="d8db6-121">The package icon identifies templates that can be used as package templates.</span></span>  
  
4.  <span data-ttu-id="d8db6-122">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="d8db6-122">Click **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8db6-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8db6-123">See Also</span></span>  
 <span data-ttu-id="d8db6-124">[在 SQL Server Data Tools 中创建包](create-packages-in-sql-server-data-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d8db6-124">[Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) </span></span>  
 [<span data-ttu-id="d8db6-125">Integration Services (SSIS) 包</span><span class="sxs-lookup"><span data-stu-id="d8db6-125">Integration Services &#40;SSIS&#41; Packages</span></span>](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
