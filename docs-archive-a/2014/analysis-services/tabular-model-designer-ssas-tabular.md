---
title: " (SSAS 表格) 的表格模型设计器 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.BIDTOOLSET.TOPLEVSEMMODUIENTRY.F1
ms.assetid: 45735c57-2a95-4e45-8994-7242df6c9c5f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac63826d3e8a93f341c181faeef44714afd92353
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580438"
---
# <a name="tabular-model-designer-ssas-tabular"></a><span data-ttu-id="c4021-102">表格模型设计器（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="c4021-102">Tabular Model Designer (SSAS Tabular)</span></span>
  <span data-ttu-id="c4021-103">表格模型设计器是 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 与 Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 2010 或更高版本集成的一部分，它具有专用于开发专业表格模型解决方案的附加项目类型模板。</span><span class="sxs-lookup"><span data-stu-id="c4021-103">The tabular model designer is part of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], integrated with Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 2010 or later, with additional project type templates specifically for developing professional tabular model solutions.</span></span>  
  
 <span data-ttu-id="c4021-104">本主题的内容：</span><span class="sxs-lookup"><span data-stu-id="c4021-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="c4021-105">优点</span><span class="sxs-lookup"><span data-stu-id="c4021-105">Benefits</span></span>](#bkmk_benefits)  
  
-   [<span data-ttu-id="c4021-106">项目模板</span><span class="sxs-lookup"><span data-stu-id="c4021-106">Project Templates</span></span>](#bkmk_proj_temp)  
  
-   [<span data-ttu-id="c4021-107">窗口和菜单</span><span class="sxs-lookup"><span data-stu-id="c4021-107">Windows and Menus</span></span>](#bkmk_wind_men)  
  
-   [<span data-ttu-id="c4021-108">Visual Studio 集成</span><span class="sxs-lookup"><span data-stu-id="c4021-108">Visual Studio Integration</span></span>](#bkmk_vsint)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> <span data-ttu-id="c4021-109">优势</span><span class="sxs-lookup"><span data-stu-id="c4021-109">Benefits</span></span>  
 <span data-ttu-id="c4021-110">在您安装 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]时，用于创建表格模型的新项目模板将添加到可用项目类型中。</span><span class="sxs-lookup"><span data-stu-id="c4021-110">When you install [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], new project templates for creating tabular models are added to the available project types.</span></span> <span data-ttu-id="c4021-111">在使用这些模板之一创建了新的表格模型项目后，您可以通过使用表格模型设计器工具和向导开始创建模型。</span><span class="sxs-lookup"><span data-stu-id="c4021-111">After creating a new tabular model project by using one of the templates, you can begin model authoring by using the tabular model designer tools and wizards.</span></span>  
  
 <span data-ttu-id="c4021-112">除了用于创建专业多维和表格模型解决方案的新模板和工具外， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 环境还提供调试和项目生命周期功能，确保您可以为组织创建功能最强大的 BI 解决方案。</span><span class="sxs-lookup"><span data-stu-id="c4021-112">In addition to new templates and tools for authoring professional multidimensional and tabular model solutions, the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environment provides debugging and project lifecycle capabilities that ensure you create the most powerful BI solutions for your organization.</span></span> <span data-ttu-id="c4021-113">有关 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的详细信息，请参阅 [Getting Started with Visual Studio](https://go.microsoft.com/fwlink/?LinkId=206389)（Visual Studio 入门）。</span><span class="sxs-lookup"><span data-stu-id="c4021-113">For more information about [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], see [Getting Started with Visual Studio](https://go.microsoft.com/fwlink/?LinkId=206389).</span></span>  
  
##  <a name="project-templates"></a><a name="bkmk_proj_temp"></a><span data-ttu-id="c4021-114">项目模板</span><span class="sxs-lookup"><span data-stu-id="c4021-114">Project Templates</span></span>  
 <span data-ttu-id="c4021-115">在您安装 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]时，以下表格模型项目模板将添加到商业智能项目类型中：</span><span class="sxs-lookup"><span data-stu-id="c4021-115">When you install [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the following tabular model project templates are added to the Business Intelligence project types:</span></span>  
  
 <span data-ttu-id="c4021-116">**Analysis Services 表格项目**</span><span class="sxs-lookup"><span data-stu-id="c4021-116">**Analysis Services Tabular Project**</span></span>  
 <span data-ttu-id="c4021-117">此模板可用于创建新的空白表格模型项目。</span><span class="sxs-lookup"><span data-stu-id="c4021-117">This template can be used to create a new, blank tabular model project.</span></span>  
  
 <span data-ttu-id="c4021-118">**从服务器导入（表格）**</span><span class="sxs-lookup"><span data-stu-id="c4021-118">**Import from Server (Tabular)**</span></span>  
 <span data-ttu-id="c4021-119">此模板可用于通过从 Analysis Services 中的现有表格模型提取元数据，创建新的表格模型项目。</span><span class="sxs-lookup"><span data-stu-id="c4021-119">This template can be used to create a new tabular model project by extracting the metadata from an existing tabular model in Analysis Services.</span></span>  
  
 <span data-ttu-id="c4021-120">**从 PowerPivot 导入**</span><span class="sxs-lookup"><span data-stu-id="c4021-120">**Import from PowerPivot**</span></span>  
 <span data-ttu-id="c4021-121">此模板用于通过从 [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] 文件提取元数据和数据，创建新的表格模型项目。</span><span class="sxs-lookup"><span data-stu-id="c4021-121">This template is used for creating a new tabular model project by extracting the metadata and data from a [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c4021-122">表格模型项目要求处于表格模式的 Analysis Services 服务器实例正在本地或网络上运行。</span><span class="sxs-lookup"><span data-stu-id="c4021-122">Tabular model projects require an Analysis Services server instance in tabular mode be running locally or on the network.</span></span>  
  
##  <a name="windows-and-menus"></a><a name="bkmk_wind_men"></a> <span data-ttu-id="c4021-123">窗口和菜单</span><span class="sxs-lookup"><span data-stu-id="c4021-123">Windows and Menus</span></span>  
 <span data-ttu-id="c4021-124">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 表格模型创建环境包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="c4021-124">The [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] tabular model authoring environment includes the following:</span></span>  
  
### <a name="designer-window"></a><span data-ttu-id="c4021-125">设计器窗口</span><span class="sxs-lookup"><span data-stu-id="c4021-125">Designer Window</span></span>  
 <span data-ttu-id="c4021-126">通过提供模型的直观表示形式，设计器窗口用于创建表格模型。</span><span class="sxs-lookup"><span data-stu-id="c4021-126">The designer window is used to author tabular models by providing a visual representation of the model.</span></span> <span data-ttu-id="c4021-127">当您打开 Model.bim 文件时，该模型将在设计器窗口中打开。</span><span class="sxs-lookup"><span data-stu-id="c4021-127">When you open the Model.bim file, the model opens in the designer window.</span></span> <span data-ttu-id="c4021-128">您可以使用两种不同的视图模式在设计器窗口中创建模型：</span><span class="sxs-lookup"><span data-stu-id="c4021-128">You can author a model in the designer window by using two different view modes:</span></span>  
  
 <span data-ttu-id="c4021-129">**数据视图**</span><span class="sxs-lookup"><span data-stu-id="c4021-129">**Data View**</span></span>  
 <span data-ttu-id="c4021-130">数据视图以表格网格格式显示表。</span><span class="sxs-lookup"><span data-stu-id="c4021-130">The data view displays tables in a tabular, grid format.</span></span> <span data-ttu-id="c4021-131">您还可以使用度量值网格（仅为“数据视图”中的每个表显示）定义度量值。</span><span class="sxs-lookup"><span data-stu-id="c4021-131">You can also define measures by using the measure grid, which can be shown for each table in Data View only.</span></span>  
  
 <span data-ttu-id="c4021-132">**图示视图**</span><span class="sxs-lookup"><span data-stu-id="c4021-132">**Diagram View**</span></span>  
 <span data-ttu-id="c4021-133">关系图视图以图形格式显示表以及表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="c4021-133">The diagram view displays tables, with relationships between them, in a graphical format.</span></span> <span data-ttu-id="c4021-134">可以筛选列、度量值、层次结构和 KPI，并且可以选择使用定义的透视查看模型。</span><span class="sxs-lookup"><span data-stu-id="c4021-134">Columns, measures, hierarchies, and KPIs can be filtered, and you can choose to view the model by using a defined perspective.</span></span>  
  
 <span data-ttu-id="c4021-135">可以在这两个视图中的任何一个执行大多数模型创建任务。</span><span class="sxs-lookup"><span data-stu-id="c4021-135">Most model authoring tasks can be performed in either view.</span></span>  
  
### <a name="solution-explorer"></a><span data-ttu-id="c4021-136">“解决方案资源管理器”</span><span class="sxs-lookup"><span data-stu-id="c4021-136">Solution Explorer</span></span>  
 <span data-ttu-id="c4021-137">“解决方案资源管理器”窗口将该活动解决方案显示为表格模型项目及其关联项的逻辑容器。</span><span class="sxs-lookup"><span data-stu-id="c4021-137">The Solution Explorer window presents the active solution as a logical container for a tabular model project and its associated items.</span></span> <span data-ttu-id="c4021-138">模型项目 (.smproj) 只包含一个 References 对象（空）和 Model.bim 文件。</span><span class="sxs-lookup"><span data-stu-id="c4021-138">The model project (.smproj) contains only a References object (empty) and the Model.bim file.</span></span> <span data-ttu-id="c4021-139">您可以直接从该视图打开项目项进行修改及执行其他管理任务。</span><span class="sxs-lookup"><span data-stu-id="c4021-139">You can open project items for modification and perform other management tasks directly from this view.</span></span>  
  
 <span data-ttu-id="c4021-140">表格模型解决方案通常只包含一个项目，但是，一个解决方案也可以包含其他项目，例如 Integration Services 或 Reporting Services 项目。</span><span class="sxs-lookup"><span data-stu-id="c4021-140">Tabular model solutions typically contain only one project; however, a solution can contain other projects too, for example, Integration Services or Reporting services project.</span></span> <span data-ttu-id="c4021-141">您可以添加任意数目的文件，只要这些文件不是表格模型项目文件所属的类型，并且将“生成操作”属性设置为“无”或将“复制到输出”属性设置为“不复制”。</span><span class="sxs-lookup"><span data-stu-id="c4021-141">You can add any number of files provided they are not of the same type as tabular model project files and their Build Action property is set to None, or Copy to Output property is set to Do Not Copy.</span></span>  
  
 <span data-ttu-id="c4021-142">若要查看解决方案资源管理器，请单击 **“视图”** 菜单，然后单击 **“解决方案资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="c4021-142">To view Solution Explorer, click the **View** menu, and then click **Solution Explorer**.</span></span>  
  
### <a name="properties-window"></a><span data-ttu-id="c4021-143">“属性”窗口</span><span class="sxs-lookup"><span data-stu-id="c4021-143">Properties Window</span></span>  
 <span data-ttu-id="c4021-144">“属性”窗口列出所选对象的属性。</span><span class="sxs-lookup"><span data-stu-id="c4021-144">The Properties window lists the properties of the selected object.</span></span> <span data-ttu-id="c4021-145">下列对象具有可以在“属性”窗口中查看和编辑的属性：</span><span class="sxs-lookup"><span data-stu-id="c4021-145">The following objects have properties that can be viewed and edited in the Properties window:</span></span>  
  
-   <span data-ttu-id="c4021-146">Model.bim</span><span class="sxs-lookup"><span data-stu-id="c4021-146">Model.bim</span></span>  
  
-   <span data-ttu-id="c4021-147">表</span><span class="sxs-lookup"><span data-stu-id="c4021-147">Table</span></span>  
  
-   <span data-ttu-id="c4021-148">列</span><span class="sxs-lookup"><span data-stu-id="c4021-148">Column</span></span>  
  
-   <span data-ttu-id="c4021-149">度量</span><span class="sxs-lookup"><span data-stu-id="c4021-149">Measure</span></span>  
  
 <span data-ttu-id="c4021-150">项目属性在“属性”窗口中只显示项目名称和项目文件夹。</span><span class="sxs-lookup"><span data-stu-id="c4021-150">Project Properties display only the project name and project folder in the Properties window.</span></span> <span data-ttu-id="c4021-151">项目还具有您可以使用模式属性对话框设置的其他部署选项和部署服务器设置。</span><span class="sxs-lookup"><span data-stu-id="c4021-151">Projects also have additional deployment Options and deployment server settings that you can set using a modal properties dialog box.</span></span> <span data-ttu-id="c4021-152">若要查看这些属性，请在 **“解决方案资源管理器”** 中右键单击相应的项目，然后单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="c4021-152">To view these properties, in **Solution Explorer**, right click the project, and then click **Properties**.</span></span>  
  
 <span data-ttu-id="c4021-153">“属性”窗口的字段中嵌入了控件，单击这些控件便可将其打开。</span><span class="sxs-lookup"><span data-stu-id="c4021-153">Fields in the Properties window have embedded controls that open when you click them.</span></span> <span data-ttu-id="c4021-154">编辑控件的类型取决于具体属性。</span><span class="sxs-lookup"><span data-stu-id="c4021-154">The type of edit control depends on the particular property.</span></span> <span data-ttu-id="c4021-155">控件包括编辑框、下拉列表和指向自定义对话框的链接。</span><span class="sxs-lookup"><span data-stu-id="c4021-155">Controls include edit boxes, dropdown lists, and links to custom dialog boxes.</span></span> <span data-ttu-id="c4021-156">灰显的属性为只读属性。</span><span class="sxs-lookup"><span data-stu-id="c4021-156">Properties that are shown as dimmed are read-only.</span></span>  
  
 <span data-ttu-id="c4021-157">若要查看 **“属性”** 窗口，请单击 **“视图”** 菜单，然后单击 **“属性窗口”**。</span><span class="sxs-lookup"><span data-stu-id="c4021-157">To view the **Properties** window, click the **View** menu, and then click **Properties Window**.</span></span>  
  
### <a name="error-list"></a><span data-ttu-id="c4021-158">错误列表</span><span class="sxs-lookup"><span data-stu-id="c4021-158">Error List</span></span>  
 <span data-ttu-id="c4021-159">“错误列表”窗口包含有关模型状态的消息：</span><span class="sxs-lookup"><span data-stu-id="c4021-159">The Error List window contains messages about the model state:</span></span>  
  
-   <span data-ttu-id="c4021-160">有关安全最佳实践的通知</span><span class="sxs-lookup"><span data-stu-id="c4021-160">Notifications about security best practices.</span></span>  
  
-   <span data-ttu-id="c4021-161">数据处理要求。</span><span class="sxs-lookup"><span data-stu-id="c4021-161">Requirements for data processing.</span></span>  
  
-   <span data-ttu-id="c4021-162">有关角色的计算列、度量值和行筛选器的语义错误信息。</span><span class="sxs-lookup"><span data-stu-id="c4021-162">Semantic error information for calculated columns, measures, and row filters for roles.</span></span> <span data-ttu-id="c4021-163">对于计算列，可以双击该错误消息来导航到错误的源。</span><span class="sxs-lookup"><span data-stu-id="c4021-163">For calculated columns, you can double-click the error message to navigate to the source of the error.</span></span>  
  
-   <span data-ttu-id="c4021-164">DirectQuery 验证错误。</span><span class="sxs-lookup"><span data-stu-id="c4021-164">DirectQuery validation errors.</span></span>  
  
 <span data-ttu-id="c4021-165">默认情况下，将不显示 **“错误列表”** ，除非返回一个错误。</span><span class="sxs-lookup"><span data-stu-id="c4021-165">By default, the **Error List** does not appear unless an error is returned.</span></span> <span data-ttu-id="c4021-166">不过可以随时查看 **“错误列表”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="c4021-166">You can, however, view the **Error List** window at any time.</span></span> <span data-ttu-id="c4021-167">若要查看 **“错误列表”** 窗口，请单击 **“视图”** 菜单，然后单击 **“错误列表”**。</span><span class="sxs-lookup"><span data-stu-id="c4021-167">To view the **Error List** window, click the **View** menu, and then click **Error List**.</span></span>  
  
### <a name="output"></a><span data-ttu-id="c4021-168">Output</span><span class="sxs-lookup"><span data-stu-id="c4021-168">Output</span></span>  
 <span data-ttu-id="c4021-169">生成和部署信息显示在“输出”\*\*\*\* 窗口中（还显示在模式进度对话框中）。</span><span class="sxs-lookup"><span data-stu-id="c4021-169">Build and deployment information is displayed in the **Output** Window (in addition to the modal progress dialog).</span></span> <span data-ttu-id="c4021-170">若要查看 **“输出”** 窗口，请单击 **“视图”** 菜单，然后单击“输出”。</span><span class="sxs-lookup"><span data-stu-id="c4021-170">To view the **Output** window, click the **View** menu, and then click Output.</span></span>  
  
### <a name="menu-items"></a><span data-ttu-id="c4021-171">菜单项</span><span class="sxs-lookup"><span data-stu-id="c4021-171">Menu Items</span></span>  
 <span data-ttu-id="c4021-172">在您安装 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]时，专用于创建表格模型的附加菜单项将添加到 Visual Studio 菜单栏中。</span><span class="sxs-lookup"><span data-stu-id="c4021-172">When you install [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], additional menu items specifically for authoring tabular models are added to the Visual Studio menu bar.</span></span> <span data-ttu-id="c4021-173">**“模型”** 菜单可用于启动数据导入向导、查看现有连接、处理工作区数据以及在 [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 中浏览模型工作区。</span><span class="sxs-lookup"><span data-stu-id="c4021-173">The **Model** menu can be used to launch the Data Import Wizard, view existing connections, process workspace data, and browse the model workspace in [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel.</span></span> <span data-ttu-id="c4021-174">**“表”** 菜单用于创建和管理表之间的关系、创建和管理度量值、指定数据表设置、指定计算选项以及指定其他表属性。</span><span class="sxs-lookup"><span data-stu-id="c4021-174">The **Table** menu is used to create and manage relationships between tables, create and manage measures, specify data table settings, specify calculation options, and specify other table properties.</span></span> <span data-ttu-id="c4021-175">使用 **“列”** 菜单，您可以添加和删除表中的列、隐藏和取消隐藏列以及指定其他列属性（例如数据类型和筛选器）。</span><span class="sxs-lookup"><span data-stu-id="c4021-175">With the **Column** menu, you can add and delete columns in a table, hide and unhide columns, and specify other column properties such as data types and filters.</span></span> <span data-ttu-id="c4021-176">可以在 **“生成”** 菜单上生成和部署表格模型解决方案。</span><span class="sxs-lookup"><span data-stu-id="c4021-176">You can build and deploy tabular model solutions on the **Build** menu.</span></span> <span data-ttu-id="c4021-177">“复制/粘贴”功能包含在“编辑”\*\*\*\* 菜单中。</span><span class="sxs-lookup"><span data-stu-id="c4021-177">Copy/Paste functions are included on the **Edit** menu.</span></span>  
  
 <span data-ttu-id="c4021-178">除了这些菜单项之外，还有一些设置添加到了“工具”菜单项上的 Analysis Services 选项中。</span><span class="sxs-lookup"><span data-stu-id="c4021-178">In addition to these menu items, additional settings are added to the Analysis Services options on the Tools menu items.</span></span>  
  
### <a name="toolbar"></a><span data-ttu-id="c4021-179">工具栏</span><span class="sxs-lookup"><span data-stu-id="c4021-179">Toolbar</span></span>  
 <span data-ttu-id="c4021-180">Analysis Services 工具栏提供了快速轻松访问最常用的模型创建命令的方式。</span><span class="sxs-lookup"><span data-stu-id="c4021-180">The Analysis Services toolbar provides quick and easy access to the most frequently used model authoring commands.</span></span>  
  
##  <a name="visual-studio-integration"></a><a name="bkmk_vsint"></a> <span data-ttu-id="c4021-181">Visual Studio 集成</span><span class="sxs-lookup"><span data-stu-id="c4021-181">Visual Studio Integration</span></span>  
 <span data-ttu-id="c4021-182">**源代码管理**</span><span class="sxs-lookup"><span data-stu-id="c4021-182">**Source Control**</span></span>  
 <span data-ttu-id="c4021-183">Analysis Services 项目与所选的源代码管理插件集成。</span><span class="sxs-lookup"><span data-stu-id="c4021-183">Analysis Services projects integrate with the selected source control plug-in.</span></span> <span data-ttu-id="c4021-184">如果您将 Visual Studio 配置为使用源代码管理，可以使用解决方案资源管理器中的“签入”/“签出”。</span><span class="sxs-lookup"><span data-stu-id="c4021-184">If you have configured Visual Studio to use source control, you can use check in/check out from Solution Explorer.</span></span> <span data-ttu-id="c4021-185">若要配置为使用 Team Foundation Server，请参阅 [为 Visual Studio 配置 Team Foundation 版本控制](https://msdn.microsoft.com/library/ms253064.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c4021-185">To configure to use Team Foundation Server, see [Configure Visual Studio with Team Foundation Version Control](https://msdn.microsoft.com/library/ms253064.aspx).</span></span> <span data-ttu-id="c4021-186">还支持很多第三方源代码管理插件。</span><span class="sxs-lookup"><span data-stu-id="c4021-186">Many third-party source control plug-ins are supported as well.</span></span>  
  
 <span data-ttu-id="c4021-187">**字体**</span><span class="sxs-lookup"><span data-stu-id="c4021-187">**Fonts**</span></span>  
 <span data-ttu-id="c4021-188">表格模型使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 环境字体来控制显示的字体。</span><span class="sxs-lookup"><span data-stu-id="c4021-188">Tabular models use the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environment font to control the fonts in the display.</span></span> <span data-ttu-id="c4021-189">如果默认 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 字体未能包含您语言所需的所有 Unicode 字符，可能需要更改此字体。</span><span class="sxs-lookup"><span data-stu-id="c4021-189">It can be necessary to change this font if the default [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] font does not have all of the Unicode characters you need for your language.</span></span> <span data-ttu-id="c4021-190">若要更改字体，请单击 **“工具”** 菜单，单击 **“选项”**，然后单击 **“字体和颜色”**。</span><span class="sxs-lookup"><span data-stu-id="c4021-190">To change fonts, click the **Tools** menu, then click **Options**, and then click **Fonts and Colors**.</span></span>  
  
 <span data-ttu-id="c4021-191">**键盘快捷方式**</span><span class="sxs-lookup"><span data-stu-id="c4021-191">**Keyboard Shortcuts**</span></span>  
 <span data-ttu-id="c4021-192">Analysis Services 键盘快捷键可以通过“工具”->“选项”->“键盘”对话框进行配置/重新映射。</span><span class="sxs-lookup"><span data-stu-id="c4021-192">The Analysis Services keyboard shortcuts can be configured/remapped through the Tools->Options->Keyboard dialog.</span></span> <span data-ttu-id="c4021-193">一些全局 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 快捷方式（如生成、保存、调试、新建项目等）在表格模型设计器上下文中受支持。</span><span class="sxs-lookup"><span data-stu-id="c4021-193">Some global [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shortcuts, such as build, save, debug, new project, etc. are supported in the tabular model designer context.</span></span> <span data-ttu-id="c4021-194">Analysis Services 上下文中支持其他表格模型设计器的特定快捷键。</span><span class="sxs-lookup"><span data-stu-id="c4021-194">Other tabular model designer specific shortcuts are in the Analysis Services context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4021-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4021-195">See Also</span></span>  
 <span data-ttu-id="c4021-196">[&#40;SSAS 表格&#41;的表格模型项目](tabular-models/tabular-model-projects-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="c4021-196">[Tabular Model Projects &#40;SSAS Tabular&#41;](tabular-models/tabular-model-projects-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="c4021-197">属性（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="c4021-197">Properties &#40;SSAS Tabular&#41;</span></span>](tabular-models/properties-ssas-tabular.md)  
  
  
