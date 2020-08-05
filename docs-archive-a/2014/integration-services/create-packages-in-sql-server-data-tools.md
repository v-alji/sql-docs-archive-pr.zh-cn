---
title: 在 SQL Server Data Tools 中创建包 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: bb3c085b-1458-49fa-8348-6a76b6e97ea6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 330e0271421dc620f7c4fad9c6944331ebe94881
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580800"
---
# <a name="create-packages-in-sql-server-data-tools"></a><span data-ttu-id="8f82a-102">在 SQL Server Data Tools 中创建包</span><span class="sxs-lookup"><span data-stu-id="8f82a-102">Create Packages in SQL Server Data Tools</span></span>
  <span data-ttu-id="8f82a-103">使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 设计器在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 中创建的包被保存到文件系统。</span><span class="sxs-lookup"><span data-stu-id="8f82a-103">The packages that you create in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] using [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer are saved to the file system.</span></span> <span data-ttu-id="8f82a-104">若要将包保存到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或保存到包存储区，则需要保存包的副本。</span><span class="sxs-lookup"><span data-stu-id="8f82a-104">To save a package to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to the package store, you need to save a copy of the package.</span></span> <span data-ttu-id="8f82a-105">有关详细信息，请参阅 [保存一个包副本](../../2014/integration-services/save-a-copy-of-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="8f82a-105">For more information, see [Save a Copy of a Package](../../2014/integration-services/save-a-copy-of-a-package.md).</span></span>  
  
 <span data-ttu-id="8f82a-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，可以使用以下方法之一来创建新包：</span><span class="sxs-lookup"><span data-stu-id="8f82a-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can create a new package by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="8f82a-107">使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包含的包模板。</span><span class="sxs-lookup"><span data-stu-id="8f82a-107">Use the package template that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] includes.</span></span>  
  
-   <span data-ttu-id="8f82a-108">使用自定义模板</span><span class="sxs-lookup"><span data-stu-id="8f82a-108">Use a custom template</span></span>  
  
     <span data-ttu-id="8f82a-109">若要使用自定义包作为创建新包的模板，只需将它们复制到 DataTransformationItems 文件夹中即可。</span><span class="sxs-lookup"><span data-stu-id="8f82a-109">To use custom packages as templates for creating new packages, you simply copy them to the DataTransformationItems folder.</span></span> <span data-ttu-id="8f82a-110">默认情况下，此文件夹位于 C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject。</span><span class="sxs-lookup"><span data-stu-id="8f82a-110">By default, this folder is in C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject.</span></span>  
  
-   <span data-ttu-id="8f82a-111">复制现有包。</span><span class="sxs-lookup"><span data-stu-id="8f82a-111">Copy an existing package.</span></span>  
  
     <span data-ttu-id="8f82a-112">如果现有包中包括了您希望重用的功能，则可以通过复制并粘贴其他包中的对象，在新包中更快地生成控制流和数据流。</span><span class="sxs-lookup"><span data-stu-id="8f82a-112">If existing packages include functionality that you want to reuse, you can build the control flow and data flows in the new package more quickly by copying and pasting objects from other packages.</span></span> <span data-ttu-id="8f82a-113">有关在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中使用复制和粘贴的详细信息，请参阅 [重用包对象](reuse-of-package-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="8f82a-113">For more information about using copy and paste in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects, see [Reuse of Package Objects](reuse-of-package-objects.md).</span></span>  
  
     <span data-ttu-id="8f82a-114">如果通过复制现有包或使用自定义包作为模板来创建新包，则现有包的名称和 GUID 也会被复制。</span><span class="sxs-lookup"><span data-stu-id="8f82a-114">If you create a new package by copying an existing package or by using a custom package as a template, the name and the GUID of the existing package are copied as well.</span></span> <span data-ttu-id="8f82a-115">应当更新新包的名称和 GUID，以便将它与原始包区分开来。</span><span class="sxs-lookup"><span data-stu-id="8f82a-115">You should update the name and the GUID of the new package to help differentiate it from the package from which it was copied.</span></span> <span data-ttu-id="8f82a-116">例如，如果包有相同的 GUID，则难以识别日志数据属于哪个包。</span><span class="sxs-lookup"><span data-stu-id="8f82a-116">For example, if packages have the same GUID, it is more difficult to identify the package to which log data belongs.</span></span> <span data-ttu-id="8f82a-117">您可以通过使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的“属性”窗口，重新生成 `ID` 属性中的 GUID 以及更新 `Name` 属性的值。</span><span class="sxs-lookup"><span data-stu-id="8f82a-117">You can regenerate the GUID in the `ID` property and update the value of the `Name` property by using the Properties window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="8f82a-118">有关详细信息，请参阅 [设置包属性](set-package-properties.md) 和 [dtutil 实用工具](dtutil-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="8f82a-118">For more information, see [Set Package Properties](set-package-properties.md) and [dtutil Utility](dtutil-utility.md).</span></span>  
  
-   <span data-ttu-id="8f82a-119">使用已指定为模板的自定义包。</span><span class="sxs-lookup"><span data-stu-id="8f82a-119">Use a custom package that you have designated as a template.</span></span>  
  
-   <span data-ttu-id="8f82a-120">运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 导入和导出向导</span><span class="sxs-lookup"><span data-stu-id="8f82a-120">Run the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard</span></span>  
  
     <span data-ttu-id="8f82a-121">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 导入和导出向导创建一个用于简单导入或导出的完整包。</span><span class="sxs-lookup"><span data-stu-id="8f82a-121">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard creates a complete package for a simple import or export.</span></span> <span data-ttu-id="8f82a-122">此向导可以配置连接、源和目标，以及添加允许您立即运行导入或导出所需的任何数据转换。</span><span class="sxs-lookup"><span data-stu-id="8f82a-122">This wizard configures the connections, source, and destination, and adds any data transformations that are required to let you run the import or export immediately.</span></span> <span data-ttu-id="8f82a-123">您还可以保存包以便以后再次运行该包，或者在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中完善和增强该包。</span><span class="sxs-lookup"><span data-stu-id="8f82a-123">You can optionally save the package to run it again later, or to refine and enhance the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="8f82a-124">但是，如果保存该包，则必须先将该包添加到现有的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中，然后才能更改该包或者在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中运行该包。</span><span class="sxs-lookup"><span data-stu-id="8f82a-124">However, if you save the package, you must add the package to an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project before you can change the package or run the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
 <span data-ttu-id="8f82a-125">下列过程说明如何在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中创建或删除包。</span><span class="sxs-lookup"><span data-stu-id="8f82a-125">The following procedures describe how to create or delete a package in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="8f82a-126">有关演示如何使用默认的包模板创建基本包的视频，请参阅 [创建基本包（SQL Server 视频）](https://go.microsoft.com/fwlink/?LinkId=131023)。</span><span class="sxs-lookup"><span data-stu-id="8f82a-126">For a video that demonstrates how to create a basic package using the default package template, see [Creating a Basic Package (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131023).</span></span>  
  
### <a name="to-create-a-package-in-sql-server-data-tools-using-the-package-template"></a><span data-ttu-id="8f82a-127">在 SQL Server Data Tools 中使用报模板创建包</span><span class="sxs-lookup"><span data-stu-id="8f82a-127">To create a package in SQL Server Data Tools using the Package Template</span></span>  
  
1.  <span data-ttu-id="8f82a-128">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开要在其中创建包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="8f82a-128">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in which you want to create a package.</span></span>  
  
2.  <span data-ttu-id="8f82a-129">在解决方案资源管理器中，右键单击“SSIS 包”文件夹，然后单击“新建 SSIS 包”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8f82a-129">In Solution Explorer, right-click the **SSIS Packages** folder, and then click **New SSIS Package**.</span></span>  
  
3.  <span data-ttu-id="8f82a-130">还可以向包中添加控制流、数据流任务和事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="8f82a-130">Optionally, add control flow, data flow tasks, and event handlers to the package.</span></span> <span data-ttu-id="8f82a-131">有关详细信息，请参阅[控制流](control-flow/control-flow.md)、[数据流](data-flow/data-flow.md)和[Integration Services (SSIS) 事件处理程序](integration-services-ssis-event-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="8f82a-131">For more information, see [Control Flow](control-flow/control-flow.md), [Data Flow](data-flow/data-flow.md), and [Integration Services &#40;SSIS&#41; Event Handlers](integration-services-ssis-event-handlers.md).</span></span>  
  
4.  <span data-ttu-id="8f82a-132">在 **“文件”** 菜单上，单击 **“保存选定项”** ，以保存新建的包。</span><span class="sxs-lookup"><span data-stu-id="8f82a-132">On the **File** menu, click **Save Selected Items** to save the new package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8f82a-133">可以保存空包。</span><span class="sxs-lookup"><span data-stu-id="8f82a-133">You can save an empty package.</span></span>  
  
  
