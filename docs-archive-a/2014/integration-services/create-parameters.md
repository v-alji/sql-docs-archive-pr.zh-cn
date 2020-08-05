---
title: 创建参数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.parameterwindow.f1
ms.assetid: cd5d675b-dd5d-49cc-8b1f-dc717a973f99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a26ae08c08a32b0593be8c9a2777b7cfe9c884fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578983"
---
# <a name="create-parameters"></a><span data-ttu-id="9973c-102">Create Parameters</span><span class="sxs-lookup"><span data-stu-id="9973c-102">Create Parameters</span></span>
  <span data-ttu-id="9973c-103">使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 可以创建项目参数和包参数。</span><span class="sxs-lookup"><span data-stu-id="9973c-103">You use [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create project parameters and package parameters.</span></span> <span data-ttu-id="9973c-104">下面的过程提供了有关创建包参数/项目参数的分步说明。</span><span class="sxs-lookup"><span data-stu-id="9973c-104">The following procedures provide step-by-step instructions for creating package/project parameters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9973c-105">若要将使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的早期版本创建的项目转换为项目部署模型，则可以使用 **“Integration Services 项目转换向导”** 来创建基于配置的参数。</span><span class="sxs-lookup"><span data-stu-id="9973c-105">If you are converting a project that you created using an earlier version of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] to the project deployment model, you can use the **Integration Services Project Conversion Wizard** to create parameters based on configurations.</span></span> <span data-ttu-id="9973c-106">有关详细信息，请参阅 [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9973c-106">For more information, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
### <a name="to-create-package-parameters"></a><span data-ttu-id="9973c-107">创建包参数</span><span class="sxs-lookup"><span data-stu-id="9973c-107">To create package parameters</span></span>  
  
1.  <span data-ttu-id="9973c-108">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中打开包，然后在 SSIS 设计器中单击 **“参数”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="9973c-108">Open the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], and then click the **Parameters** tab in the SSIS Designer.</span></span>  
  
     <span data-ttu-id="9973c-109">![包参数选项卡](media/denali-package-parameters.gif "包参数选项卡")</span><span class="sxs-lookup"><span data-stu-id="9973c-109">![Package Parameters Tab](media/denali-package-parameters.gif "Package Parameters Tab")</span></span>  
  
2.  <span data-ttu-id="9973c-110">单击工具栏上的 **“添加参数”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="9973c-110">Click the **Add Parameter** button on the toolbar.</span></span>  
  
     <span data-ttu-id="9973c-111">![添加工具栏按钮](media/denali-parameter-add.gif "添加工具栏按钮")</span><span class="sxs-lookup"><span data-stu-id="9973c-111">![Add Toolbar Button](media/denali-parameter-add.gif "Add Toolbar Button")</span></span>  
  
3.  <span data-ttu-id="9973c-112">为列表自身中或 **“属性”** 窗口中的 **“名称”**、 **“数据类型”**、 **“值”**、 **“敏感”** 和 **“必需”** 属性输入值。</span><span class="sxs-lookup"><span data-stu-id="9973c-112">Enter values for the **Name**, **Data Type**, **Value**, **Sensitive**, and **Required** properties in the list itself or in the **Properties** window.</span></span> <span data-ttu-id="9973c-113">下表对这些属性进行了说明：</span><span class="sxs-lookup"><span data-stu-id="9973c-113">The following table describes these properties.</span></span>  
  
    |<span data-ttu-id="9973c-114">属性</span><span class="sxs-lookup"><span data-stu-id="9973c-114">Property</span></span>|<span data-ttu-id="9973c-115">说明</span><span class="sxs-lookup"><span data-stu-id="9973c-115">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="9973c-116">名称</span><span class="sxs-lookup"><span data-stu-id="9973c-116">Name</span></span>|<span data-ttu-id="9973c-117">参数的名称。</span><span class="sxs-lookup"><span data-stu-id="9973c-117">The name of the parameter.</span></span>|  
    |<span data-ttu-id="9973c-118">数据类型</span><span class="sxs-lookup"><span data-stu-id="9973c-118">Data type</span></span>|<span data-ttu-id="9973c-119">参数的数据类型。</span><span class="sxs-lookup"><span data-stu-id="9973c-119">The data type of the parameter.</span></span>|  
    |<span data-ttu-id="9973c-120">默认值</span><span class="sxs-lookup"><span data-stu-id="9973c-120">Default value</span></span>|<span data-ttu-id="9973c-121">在设计时分配的参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="9973c-121">The default value for the parameter assigned at design time.</span></span> <span data-ttu-id="9973c-122">这也称为设计默认值。</span><span class="sxs-lookup"><span data-stu-id="9973c-122">This is also known as the design default.</span></span>|  
    |<span data-ttu-id="9973c-123">敏感</span><span class="sxs-lookup"><span data-stu-id="9973c-123">Sensitive</span></span>|<span data-ttu-id="9973c-124">敏感参数值在目录中加密，并且在使用 Transact-SQL 或 SQL Server Management Studio 查看时以 NULL 值的形式出现。</span><span class="sxs-lookup"><span data-stu-id="9973c-124">Sensitive parameter values are encrypted in the catalog and appear as a NULL value when viewed with Transact-SQL or SQL Server Management Studio.</span></span>|  
    |<span data-ttu-id="9973c-125">必需</span><span class="sxs-lookup"><span data-stu-id="9973c-125">Required</span></span>|<span data-ttu-id="9973c-126">需要首先指定并非设计默认值的值，包才能执行。</span><span class="sxs-lookup"><span data-stu-id="9973c-126">Requires that a value, other than the design default, is specified before the package can execute.</span></span>|  
    |<span data-ttu-id="9973c-127">说明</span><span class="sxs-lookup"><span data-stu-id="9973c-127">Description</span></span>|<span data-ttu-id="9973c-128">出于可维护性目的而提供的参数的说明。</span><span class="sxs-lookup"><span data-stu-id="9973c-128">For maintainability, the description of the parameter.</span></span> <span data-ttu-id="9973c-129">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，当在适用的参数窗口中选择参数时，在“Visual Studio 属性”窗口中设置参数说明。</span><span class="sxs-lookup"><span data-stu-id="9973c-129">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], set the parameter description in the Visual Studio Properties window when the parameter is selected in the applicable parameters window.</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="9973c-130">在您向目录部署某一项目时，还有几个属性将与该项目相关联。</span><span class="sxs-lookup"><span data-stu-id="9973c-130">When you deploy a project to the catalog, several more properties become associated with the project.</span></span> <span data-ttu-id="9973c-131">若要查看目录中所有参数的全部属性，请使用 [catalog.object_parameters（SSISDB 数据库）](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database)视图。</span><span class="sxs-lookup"><span data-stu-id="9973c-131">To see all properties for all parameters in the catalog, use the [catalog.object_parameters &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) view.</span></span>  
  
4.  <span data-ttu-id="9973c-132">保存项目以保存对参数所做的更改。</span><span class="sxs-lookup"><span data-stu-id="9973c-132">Save the project to save changes to parameters.</span></span> <span data-ttu-id="9973c-133">参数值将存储在项目文件中。</span><span class="sxs-lookup"><span data-stu-id="9973c-133">Parameter values are stored in the project file.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="9973c-134">可以直接在列表中编辑，也可以使用“属性”窗口来修改参数属性的值。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="9973c-134">You can in-place edit in the list or use the **Properties** window to modify the values of parameter properties.</span></span> <span data-ttu-id="9973c-135">可以使用“删除 (X)”工具栏按钮来删除参数。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="9973c-135">You can delete a parameter by using the **Delete (X)** toolbar button.</span></span> <span data-ttu-id="9973c-136">使用最后一个工具栏按钮，可以为仅在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中执行包时使用的参数指定值。</span><span class="sxs-lookup"><span data-stu-id="9973c-136">Using the last toolbar button, you can specify a value for a parameter that is used only when you execute the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9973c-137">如果未在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中打开项目便重新打开包文件，则“参数”选项卡将为空且被禁用。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="9973c-137">If you re-open the package file without opening the project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], the **Parameters** tab will be empty and disabled.</span></span>  
  
### <a name="to-create-project-parameters"></a><span data-ttu-id="9973c-138">创建项目参数</span><span class="sxs-lookup"><span data-stu-id="9973c-138">To create project parameters</span></span>  
  
1.  <span data-ttu-id="9973c-139">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中打开项目。</span><span class="sxs-lookup"><span data-stu-id="9973c-139">Open the project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="9973c-140">在解决方案资源管理器中右键单击“Project.params”，然后单击“打开”，或者双击“Project.params”将其打开。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="9973c-140">Right-click **Project.params** in Solution Explorer, and then click **Open** (OR) double-click **Project.params** to open it.</span></span>  
  
     <span data-ttu-id="9973c-141">![项目参数窗口](media/denali-project-parameters.gif "项目参数窗口")</span><span class="sxs-lookup"><span data-stu-id="9973c-141">![Project Parameters Window](media/denali-project-parameters.gif "Project Parameters Window")</span></span>  
  
3.  <span data-ttu-id="9973c-142">单击工具栏上的 **“添加参数”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="9973c-142">Click the **Add Parameter** button on the toolbar.</span></span>  
  
     <span data-ttu-id="9973c-143">![添加工具栏按钮](media/denali-parameter-add.gif "添加工具栏按钮")</span><span class="sxs-lookup"><span data-stu-id="9973c-143">![Add Toolbar Button](media/denali-parameter-add.gif "Add Toolbar Button")</span></span>  
  
4.  <span data-ttu-id="9973c-144">为 **“名称”**、 **“数据类型”**、 **“值”**、 **“敏感”** 和 **“必需”** 属性输入值。</span><span class="sxs-lookup"><span data-stu-id="9973c-144">Enter values for the **Name**, **Data Type**, **Value**, **Sensitive**, and **Required** properties.</span></span>  
  
    |<span data-ttu-id="9973c-145">属性</span><span class="sxs-lookup"><span data-stu-id="9973c-145">Property</span></span>|<span data-ttu-id="9973c-146">说明</span><span class="sxs-lookup"><span data-stu-id="9973c-146">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="9973c-147">名称</span><span class="sxs-lookup"><span data-stu-id="9973c-147">Name</span></span>|<span data-ttu-id="9973c-148">参数的名称。</span><span class="sxs-lookup"><span data-stu-id="9973c-148">The name of the parameter.</span></span>|  
    |<span data-ttu-id="9973c-149">数据类型</span><span class="sxs-lookup"><span data-stu-id="9973c-149">Data type</span></span>|<span data-ttu-id="9973c-150">参数的数据类型。</span><span class="sxs-lookup"><span data-stu-id="9973c-150">The data type of the parameter.</span></span>|  
    |<span data-ttu-id="9973c-151">默认值</span><span class="sxs-lookup"><span data-stu-id="9973c-151">Default value</span></span>|<span data-ttu-id="9973c-152">在设计时分配的参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="9973c-152">The default value for the parameter assigned at design time.</span></span> <span data-ttu-id="9973c-153">这也称为设计默认值。</span><span class="sxs-lookup"><span data-stu-id="9973c-153">This is also known as the design default.</span></span>|  
    |<span data-ttu-id="9973c-154">敏感</span><span class="sxs-lookup"><span data-stu-id="9973c-154">Sensitive</span></span>|<span data-ttu-id="9973c-155">敏感参数值在目录中加密，并且在使用 Transact-SQL 或 SQL Server Management Studio 查看时以 NULL 值的形式出现。</span><span class="sxs-lookup"><span data-stu-id="9973c-155">Sensitive parameter values are encrypted in the catalog and appear as a NULL value when viewed with Transact-SQL or SQL Server Management Studio.</span></span>|  
    |<span data-ttu-id="9973c-156">必需</span><span class="sxs-lookup"><span data-stu-id="9973c-156">Required</span></span>|<span data-ttu-id="9973c-157">需要首先指定并非设计默认值的值，包才能执行。</span><span class="sxs-lookup"><span data-stu-id="9973c-157">Requires that a value, other than the design default, is specified before the package can execute.</span></span>|  
    |<span data-ttu-id="9973c-158">说明</span><span class="sxs-lookup"><span data-stu-id="9973c-158">Description</span></span>|<span data-ttu-id="9973c-159">出于可维护性目的而提供的参数的说明。</span><span class="sxs-lookup"><span data-stu-id="9973c-159">For maintainability, the description of the parameter.</span></span> <span data-ttu-id="9973c-160">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，当在适用的参数窗口中选择参数时，在“Visual Studio 属性”窗口中设置参数说明。</span><span class="sxs-lookup"><span data-stu-id="9973c-160">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], set the parameter description in the Visual Studio Properties window when the parameter is selected in the applicable parameters window.</span></span>|  
  
5.  <span data-ttu-id="9973c-161">保存项目以保存对参数所做的更改。</span><span class="sxs-lookup"><span data-stu-id="9973c-161">Save the project to save changes to parameters.</span></span> <span data-ttu-id="9973c-162">参数值将存储在项目文件的配置中。</span><span class="sxs-lookup"><span data-stu-id="9973c-162">Parameter values are stored in configurations in the project file.</span></span> <span data-ttu-id="9973c-163">保存项目文件以将对参数值的所有更改提交到磁盘。</span><span class="sxs-lookup"><span data-stu-id="9973c-163">Save the project file to commit to disk any changes in the parameter values.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="9973c-164">可以直接在列表中编辑，也可以使用“属性”窗口来修改参数属性的值。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="9973c-164">You can in-place edit in the list or use the **Properties** window to modify the values of parameter properties.</span></span> <span data-ttu-id="9973c-165">可以使用“删除 (X)”工具栏按钮来删除参数。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="9973c-165">You can delete a parameter by using the **Delete (X)** toolbar button.</span></span> <span data-ttu-id="9973c-166">使用最后一个工具栏按钮打开 **“管理参数值”** 对话框，您可以为仅在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中执行包时使用的参数指定值。</span><span class="sxs-lookup"><span data-stu-id="9973c-166">Using the last toolbar button to open the **Manage Parameter Values** dialog box, you can specify a value for a parameter that is used only when you execute the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9973c-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9973c-167">See Also</span></span>  
 [<span data-ttu-id="9973c-168">&#40;SSIS&#41; 参数 Integration Services</span><span class="sxs-lookup"><span data-stu-id="9973c-168">Integration Services &#40;SSIS&#41; Parameters</span></span>](integration-services-ssis-package-and-project-parameters.md)  
  
  
