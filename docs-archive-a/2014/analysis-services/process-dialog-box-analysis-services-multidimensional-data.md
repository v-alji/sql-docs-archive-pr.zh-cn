---
title: "\"处理\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.processdialog.f1
ms.assetid: c065248c-9001-4f0c-928f-9c59eccb618b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 369c121713894bba9b2ce6c40aa2869de49eaa72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693518"
---
# <a name="process-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="fcd56-102">“处理”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="fcd56-102">Process Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="fcd56-103">可以使用 **和** 中的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] “处理” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 对话框处理 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="fcd56-103">Use the **Process** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to process [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="fcd56-104">在 **中，可以执行以下操作以显示** “处理” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 对话框：</span><span class="sxs-lookup"><span data-stu-id="fcd56-104">You can display the **Process** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] by:</span></span>  
  
-   <span data-ttu-id="fcd56-105">在“解决方案资源管理器”中右键单击某个 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目、多维数据集、维度或挖掘结构，然后选择“处理”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fcd56-105">Right-clicking an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, cube, dimension, or mining structure in **Solution Explorer** and selecting **Process**.</span></span>  
  
-   <span data-ttu-id="fcd56-106">在 **多维数据集设计器** 的所有页、 **维度设计器**的所有页或 **数据挖掘模型设计器**的 **“挖掘结构”** 和 **“挖掘模型”** 页上，从工具栏中选择 **“处理”**。</span><span class="sxs-lookup"><span data-stu-id="fcd56-106">Selecting **Process** from the toolbar on every page of **Cube Designer**, every page of **Dimension Designer**, or the **Mining Structure** and **Mining Models** pages of **Data Mining Model Designer**.</span></span>  
  
-   <span data-ttu-id="fcd56-107">在“数据挖掘模型设计器”的“挖掘模型”页中，右键单击某个挖掘模型，然后选择“处理挖掘结构和所有模型”或“处理模型”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fcd56-107">Right-clicking a mining model in the **Mining Models** page of **Data Mining Model Designer** and selecting **Process Mining Structure and All Models** or **Process Model**.</span></span>  
  
 <span data-ttu-id="fcd56-108">在 **SQL Server Management Studio** 中，可以通过执行以下操作显示 **“处理”** 对话框：</span><span class="sxs-lookup"><span data-stu-id="fcd56-108">You can display the **Process** dialog box in **SQL Server Management Studio** by:</span></span>  
  
-   <span data-ttu-id="fcd56-109">在“对象资源管理器”中右键单击某个 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库、多维数据集、度量值组、分区、维度、挖掘结构或挖掘模型，然后选择“处理”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fcd56-109">Right-clicking an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, cube, measure group, partition, dimension, mining structure, or mining model in **Object Explorer** and selecting **Process**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fcd56-110">选项</span><span class="sxs-lookup"><span data-stu-id="fcd56-110">Options</span></span>  
 <span data-ttu-id="fcd56-111">**对象列表**</span><span class="sxs-lookup"><span data-stu-id="fcd56-111">**Object list**</span></span>  
 <span data-ttu-id="fcd56-112">选择要处理的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象和要应用的处理选项及设置。</span><span class="sxs-lookup"><span data-stu-id="fcd56-112">Select the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects to be processed and the processing options and settings to be applied.</span></span> <span data-ttu-id="fcd56-113">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="fcd56-113">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="fcd56-114">**Object Name**</span><span class="sxs-lookup"><span data-stu-id="fcd56-114">**Object Name**</span></span>  
 <span data-ttu-id="fcd56-115">显示要处理的对象的名称。</span><span class="sxs-lookup"><span data-stu-id="fcd56-115">Displays the name of the object to be processed.</span></span> <span data-ttu-id="fcd56-116">名称左侧的图标指示对象类型。</span><span class="sxs-lookup"><span data-stu-id="fcd56-116">The icon to the left of the name indicates the object type.</span></span>  
  
 <span data-ttu-id="fcd56-117">**Type**</span><span class="sxs-lookup"><span data-stu-id="fcd56-117">**Type**</span></span>  
 <span data-ttu-id="fcd56-118">显示要处理的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="fcd56-118">Displays the type of the object to be processed.</span></span>  
  
 <span data-ttu-id="fcd56-119">**处理选项**</span><span class="sxs-lookup"><span data-stu-id="fcd56-119">**Process Options**</span></span>  
 <span data-ttu-id="fcd56-120">选择要对所选对象执行的处理类型。</span><span class="sxs-lookup"><span data-stu-id="fcd56-120">Select the type of processing to perform on the selected object.</span></span> <span data-ttu-id="fcd56-121">有关可用的处理选项的详细信息，请参阅[多维模型对象处理](multidimensional-models/processing-a-multidimensional-model-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fcd56-121">For more information about available processing options, see [Multidimensional Model Object Processing](multidimensional-models/processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
 <span data-ttu-id="fcd56-122">**设置**</span><span class="sxs-lookup"><span data-stu-id="fcd56-122">**Settings**</span></span>  
 <span data-ttu-id="fcd56-123">对于多维数据集、度量值组或分区，在“处理选项”中选择“处理增量”时，会显示“配置”超链接\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fcd56-123">Displays the **Configure** hyperlink when you choose **Process Incremental** in **Process Options** for cubes, measure groups, or partitions.</span></span> <span data-ttu-id="fcd56-124">单击 **“配置”** 可启动 **“增量更新”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="fcd56-124">Click **Configure** to launch the **Incremental Update** dialog box.</span></span> <span data-ttu-id="fcd56-125">有关“增量更新”\*\*\*\* 对话框的详细信息，请参阅[“增量更新”对话框（Analysis Services - 多维数据）](incremental-update-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="fcd56-125">For more information about the **Incremental Update** dialog box, see [Incremental Update Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](incremental-update-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="fcd56-126">**移除**</span><span class="sxs-lookup"><span data-stu-id="fcd56-126">**Remove**</span></span>  
 <span data-ttu-id="fcd56-127">单击此项可从\*\*\*\*“对象列表”中删除所选项。</span><span class="sxs-lookup"><span data-stu-id="fcd56-127">Click to remove the selected items from **Object list**.</span></span>  
  
 <span data-ttu-id="fcd56-128">**影响分析**</span><span class="sxs-lookup"><span data-stu-id="fcd56-128">**Impact Analysis**</span></span>  
 <span data-ttu-id="fcd56-129">单击此项可打开“影响分析”\*\*\*\* 对话框，并显示将被处理任务影响的对象。</span><span class="sxs-lookup"><span data-stu-id="fcd56-129">Click to open the **Impact Analysis** dialog box and display the objects that will be affected by the processing task.</span></span> <span data-ttu-id="fcd56-130">有关\*\*\*\*“影响分析”对话框的详细信息，请参阅[“影响分析”对话框（Analysis Services - 多维数据）](impact-analysis-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="fcd56-130">For more information about the **Impact Analysis** dialog box, see [Impact Analysis Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](impact-analysis-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fcd56-131">当在“更改设置”对话框中选中“处理影响的对象”选项时，将禁用此选项\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fcd56-131">This option is disabled when the **Process affected objects** option is selected in the **Change Settings** dialog box.</span></span>  
  
 <span data-ttu-id="fcd56-132">**更改设置**</span><span class="sxs-lookup"><span data-stu-id="fcd56-132">**Change Settings**</span></span>  
 <span data-ttu-id="fcd56-133">单击此项可打开\*\*\*\*“更改设置”对话框，并更改用于控制所选对象的处理方式的设置，包括批处理设置、写回设置、维度键错误设置。</span><span class="sxs-lookup"><span data-stu-id="fcd56-133">Click to open the **Change Settings** dialog box and change the settings that govern processing of the selected objects, including batch processing settings, writeback settings, and dimension key error settings.</span></span> <span data-ttu-id="fcd56-134">有关“更改设置”\*\*\*\* 对话框的详细信息，请参阅[“更改设置”对话框（Analysis Services - 多维数据）](change-settings-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="fcd56-134">For more information about the **Change Settings** dialog box, see [Change Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](change-settings-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="fcd56-135">**Run**</span><span class="sxs-lookup"><span data-stu-id="fcd56-135">**Run**</span></span>  
 <span data-ttu-id="fcd56-136">单击此项可处理对象。</span><span class="sxs-lookup"><span data-stu-id="fcd56-136">Click to process the objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcd56-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fcd56-137">See Also</span></span>  
 <span data-ttu-id="fcd56-138">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fcd56-138">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="fcd56-139">"处理进度" 对话框 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="fcd56-139">Process Progress Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](process-progress-dialog-box-analysis-services-multidimensional-data.md)  
  
  
