---
title: 在 Management Studio 中创建 Analysis Services 脚本 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services objects, scripts
- objects [Analysis Services], scripts
- scripts [Analysis Services], objects
ms.assetid: 4f1b965c-9ca6-427b-8f4d-0ce1eea7c0fe
author: minewiskan
ms.author: owend
ms.openlocfilehash: bb380e271510ea5a35860d4850bfaeed3aad8cf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689115"
---
# <a name="create-analysis-services-scripts-in-management-studio"></a><span data-ttu-id="934c3-102">在 Management Studio 中创建 Analysis Services 脚本</span><span class="sxs-lookup"><span data-stu-id="934c3-102">Create Analysis Services Scripts in Management Studio</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="934c3-103">包括您可以用来对 Analysis Services 对象和任务编写脚本的脚本生成功能、模板和编辑器。</span><span class="sxs-lookup"><span data-stu-id="934c3-103">includes script generation features, templates, and editors that you can use to script Analysis Services objects and tasks.</span></span>  
  
## <a name="script-analysis-services-tasks-in-management-studio"></a><span data-ttu-id="934c3-104">在 Management Studio 中编写 Analysis Services 任务的脚本</span><span class="sxs-lookup"><span data-stu-id="934c3-104">Script Analysis Services Tasks in Management Studio</span></span>  
 <span data-ttu-id="934c3-105">通过单击面向任务的对话框中的某一个脚本选项，可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中编写任务脚本。</span><span class="sxs-lookup"><span data-stu-id="934c3-105">Scripting tasks in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is accomplished by clicking one of the Script options in a task-oriented dialog box.</span></span> <span data-ttu-id="934c3-106">用来执行备份或还原数据库、处理对象或设计聚合之类的任务的所有对话框都在顶部包括一个脚本选项。</span><span class="sxs-lookup"><span data-stu-id="934c3-106">All of the dialog boxes that you use to perform tasks such as backup or restore database, process an object, or design an aggregation, include a Script option at the top of the dialog box.</span></span> <span data-ttu-id="934c3-107">选择其中一个选项可以根据对话框中的信息和设置生成一个 XMLA 脚本。</span><span class="sxs-lookup"><span data-stu-id="934c3-107">Selecting one of these options generates an XMLA script based on the information and settings in the dialog box.</span></span>  
  
 <span data-ttu-id="934c3-108">默认情况下，在 XMLA 查询编辑器中生成并放置脚本，但是您也可以扩展脚本选项列表，将脚本保存到 Windows 剪贴板或某个文件中。</span><span class="sxs-lookup"><span data-stu-id="934c3-108">By default, the script is generated and placed in an XMLA query editor, but you can also expand the Script option list to direct the script to the Windows Clipboard or a file.</span></span>  
  
#### <a name="to-script-an-analysis-services-task"></a><span data-ttu-id="934c3-109">编写 Analysis Services 任务脚本</span><span class="sxs-lookup"><span data-stu-id="934c3-109">To script an Analysis Services task</span></span>  
  
1.  <span data-ttu-id="934c3-110">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="934c3-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="934c3-111">右键单击某个数据库，然后单击“备份”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="934c3-111">Right-click a database and click **Backup**.</span></span> <span data-ttu-id="934c3-112">这将打开“备份数据库”对话框。</span><span class="sxs-lookup"><span data-stu-id="934c3-112">This opens the Backup Database dialog box.</span></span> <span data-ttu-id="934c3-113">指定备份文件的名称，并选择要用于此备份的选项。</span><span class="sxs-lookup"><span data-stu-id="934c3-113">Specify a backup file name and choose the options you want for this backup.</span></span>  
  
3.  <span data-ttu-id="934c3-114">单击对话框顶部的 **“脚本”** 。</span><span class="sxs-lookup"><span data-stu-id="934c3-114">Click **Script** at the top of the dialog box.</span></span> <span data-ttu-id="934c3-115">脚本功能是 Management Studio 中所有基于任务的对话框的一部分。</span><span class="sxs-lookup"><span data-stu-id="934c3-115">The Script feature is part of all task-based dialog boxes in Management Studio.</span></span> <span data-ttu-id="934c3-116">该功能具有以下选项： **“将操作脚本保存到‘新建查询’窗口”** （用于打开查询编辑器窗口）、 **“将操作脚本保存到文件”** （用于将 XMLA 脚本保存到文件）或 **“将操作脚本保存到剪贴板”** （用于将 XMLA 脚本保存到剪贴板）。</span><span class="sxs-lookup"><span data-stu-id="934c3-116">It has the following options: **Script Action to New Query Window** to open the query editor window, **Script Action to File** to save the XMLA script to a file, or **Script Action to Clipboard** to save the XMLA script to the Clipboard.</span></span>  
  
     <span data-ttu-id="934c3-117">请注意，Analysis Services 脚本不支持在 Management Studio 中列为脚本选项的 **“将操作脚本保存到作业”** 选项。</span><span class="sxs-lookup"><span data-stu-id="934c3-117">Note that the **Script Action to Job** option that is listed as a script option in Management Studio is not supported for Analysis Services scripts.</span></span>  
  
4.  <span data-ttu-id="934c3-118">如果选择默认选项 **“将操作脚本保存到‘新建查询’窗口”**，生成的脚本将放置在 XMLA 查询窗口中。</span><span class="sxs-lookup"><span data-stu-id="934c3-118">If you select the default option, **Script Action to New Query Window**, a generated script is placed in an XMLA query window.</span></span>  
  
     <span data-ttu-id="934c3-119">您现在可以关闭“备份数据库”对话框，并编辑或直接运行 XMLA 脚本。</span><span class="sxs-lookup"><span data-stu-id="934c3-119">You can now close the Backup Database dialog box and edit or run the XMLA script directly.</span></span>  
  
## <a name="script-analysis-services-objects-in-management-studio"></a><span data-ttu-id="934c3-120">在 Management Studio 中编写 Analysis Services 对象的脚本</span><span class="sxs-lookup"><span data-stu-id="934c3-120">Script Analysis Services Objects in Management Studio</span></span>  
 <span data-ttu-id="934c3-121">可通过下列方法在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中编写对象脚本：右键单击 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象，然后选择“Create 到”、“Alter 到”或“Delete 到”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="934c3-121">Scripting objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is accomplished by right-clicking an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and selecting either **Create to**, **Alter to**, or **Delete to**.</span></span> <span data-ttu-id="934c3-122">这些选项中的每一个都可定向到窗口或文件，但是无论脚本定向到何处，它都会以 DDL 脚本或 XMLA 包装的形式出现。</span><span class="sxs-lookup"><span data-stu-id="934c3-122">Each of these options can be directed to a window or a file, but regardless of where the script is directed to, it will come in the form of a DDL script in an XMLA wrapper.</span></span> <span data-ttu-id="934c3-123">此类脚本的一个突出优点就是可以在其指向的任何服务器中运行。</span><span class="sxs-lookup"><span data-stu-id="934c3-123">One great advantage to such scripts is that they can be run against any server you point them at.</span></span> <span data-ttu-id="934c3-124">此外，脚本中的名称可以更改，并可针对大规模的构造、修改或删除对象进行迭代运行。</span><span class="sxs-lookup"><span data-stu-id="934c3-124">Also, names in the scripts can be changed and run on an iterative basis for mass construction, alteration, or deletion of objects.</span></span>  
  
 <span data-ttu-id="934c3-125">您可以编写脚本的对象包括 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库的元素，具体包括数据源、数据源视图、多维数据集、维度、挖掘结构和角色。</span><span class="sxs-lookup"><span data-stu-id="934c3-125">Objects that you can script include the elements of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, including data sources, data source views, cubes, dimensions, mining structures, and roles.</span></span>  
  
 <span data-ttu-id="934c3-126">前提条件是要对 XML for Analysis (XMLA) 有所了解。</span><span class="sxs-lookup"><span data-stu-id="934c3-126">Prerequisites include an understanding of XML for Analysis (XMLA).</span></span> <span data-ttu-id="934c3-127">幸运的是， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中具有自动创建 XMLA 脚本（用于创建多维数据集之类的对象）的功能。</span><span class="sxs-lookup"><span data-stu-id="934c3-127">Fortunately, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] has a feature that automatically creates the XMLA script required to create objects, such as cubes.</span></span> <span data-ttu-id="934c3-128">该自动化功能可帮助在学习 XMLA 时少走弯路。</span><span class="sxs-lookup"><span data-stu-id="934c3-128">This automation feature helps reduce the learning curve for XMLA.</span></span> <span data-ttu-id="934c3-129">有关如何使用 XMLA 的详细信息，请参阅 [在 Analysis Services 中使用 XMLA 开发](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="934c3-129">For more information about how to use XMLA, see [Developing with XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).</span></span> <span data-ttu-id="934c3-130">有关如何使用 XMLA 的详细信息，请参阅 [在 Analysis Services 中使用 XMLA 开发](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="934c3-130">For more information about how to use XMLA, see [Developing with XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="934c3-131">编写 Role 对象的脚本时，需要注意安全权限包含在这些权限保护的对象中，而非包含在与这些权限关联的安全角色中。</span><span class="sxs-lookup"><span data-stu-id="934c3-131">When scripting the Role Object, be aware that security permissions are contained by the objects they secure rather than with the security role with which they are associated.</span></span>  
  
#### <a name="to-script-analysis-services-objects"></a><span data-ttu-id="934c3-132">编写 Analysis Services 对象脚本</span><span class="sxs-lookup"><span data-stu-id="934c3-132">To script Analysis Services objects</span></span>  
  
1.  <span data-ttu-id="934c3-133">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="934c3-133">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="934c3-134">找到要为其创建脚本（该脚本可以创建、更改或删除对象）的对象。</span><span class="sxs-lookup"><span data-stu-id="934c3-134">Locate the object for which you want to create a script that either creates, alters, or deletes objects.</span></span>  
  
3.  <span data-ttu-id="934c3-135">右键单击该对象，指向“编写多维数据集脚本为”，再指向“CREATE 到”、“ALTER 到”或“DELETE 到”，然后单击以下选项之一：“新查询编辑器窗口”（用于打开查询编辑器窗口）、“文件”（用于将 XMLA 脚本保存到文件）或“剪贴板”（用于将 XMLA 脚本保存到剪贴板）\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="934c3-135">Right-click the object, point to **Script Cube as**, point to **CREATE To**, **ALTER To**, or **Delete To**, and then click one of the following options: **New Query Editor Window** to open the query editor window, **File** to save the XMLA script to a file, or **Clipboard** to save the XMLA script to the Clipboard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="934c3-136"> 通常，如果您想要创建该文件的多个不同版本，请选择 **“文件”** 。</span><span class="sxs-lookup"><span data-stu-id="934c3-136">Typically, you would select **File** if you want to create multiple different versions of the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934c3-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="934c3-137">See Also</span></span>  
 <span data-ttu-id="934c3-138">[在 Analysis Services 中编写管理任务脚本](../script-administrative-tasks-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="934c3-138">[Script Administrative Tasks in Analysis Services](../script-administrative-tasks-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="934c3-139">XMLA 查询编辑器（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="934c3-139">XMLA Query Editor &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../xmla-query-editor-analysis-services-multidimensional-data.md)  
  
  
