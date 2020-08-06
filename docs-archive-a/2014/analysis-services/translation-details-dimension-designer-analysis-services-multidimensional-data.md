---
title: 翻译详细信息 (翻译 "选项卡，维度设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.translations.translationpane.tranlationdetails.f1
ms.assetid: 0aa61df3-f2b0-4703-a63b-124da672dcc3
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7cbe4a3c69111d0f82f96ff5125f80fe0c2c57f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692535"
---
# <a name="translation-details-translations-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="29255-102">翻译详细信息（“翻译”选项卡，维度设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="29255-102">Translation Details (Translations Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="29255-103">可以使用维度设计器中的 **“翻译”** 选项卡上的 **“翻译详细信息”** 窗格，定义和管理当前所选维度的翻译。</span><span class="sxs-lookup"><span data-stu-id="29255-103">Use the **Translation Details** pane on the **Translations** tab of Dimension Designer to define and manage translations for the currently selected dimension.</span></span>  
  
 <span data-ttu-id="29255-104">**显示“翻译详细信息”窗格**</span><span class="sxs-lookup"><span data-stu-id="29255-104">**To display the Translations Details pane**</span></span>  
  
1.  <span data-ttu-id="29255-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目，然后打开所需的维度。</span><span class="sxs-lookup"><span data-stu-id="29255-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then open the dimension that you want.</span></span>  
  
2.  <span data-ttu-id="29255-106">单击 **“翻译”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="29255-106">Click the **Translations** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="29255-107">选项</span><span class="sxs-lookup"><span data-stu-id="29255-107">Options</span></span>  
 <span data-ttu-id="29255-108">**默认语言**</span><span class="sxs-lookup"><span data-stu-id="29255-108">**Default Language**</span></span>  
 <span data-ttu-id="29255-109">以默认语言设置维度对象的名称。</span><span class="sxs-lookup"><span data-stu-id="29255-109">Sets the names of the dimension objects in the default language.</span></span>  
  
 <span data-ttu-id="29255-110">“对象类型”</span><span class="sxs-lookup"><span data-stu-id="29255-110">**Object Type**</span></span>  
 <span data-ttu-id="29255-111">显示将翻译的属性。</span><span class="sxs-lookup"><span data-stu-id="29255-111">Displays the property that will be translated.</span></span> <span data-ttu-id="29255-112">只能翻译已指定值的对象和属性。</span><span class="sxs-lookup"><span data-stu-id="29255-112">Only objects and properties for which values have been specified can be translated.</span></span> <span data-ttu-id="29255-113">可以翻译以下属性：</span><span class="sxs-lookup"><span data-stu-id="29255-113">The following properties can be translated:</span></span>  
  
-   <span data-ttu-id="29255-114">维度</span><span class="sxs-lookup"><span data-stu-id="29255-114">Dimension</span></span>  
  
     <span data-ttu-id="29255-115">`Caption` 和 `AttributeAllMember` 属性</span><span class="sxs-lookup"><span data-stu-id="29255-115">`Caption` and `AttributeAllMember` properties</span></span>  
  
-   <span data-ttu-id="29255-116">Attribute</span><span class="sxs-lookup"><span data-stu-id="29255-116">Attribute</span></span>  
  
     <span data-ttu-id="29255-117">`Caption`、`AttributeHierarchyDisplayFolder` 和 `NamingTemplate` 属性</span><span class="sxs-lookup"><span data-stu-id="29255-117">`Caption`, `AttributeHierarchyDisplayFolder`, and `NamingTemplate` properties</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="29255-118">只有父属性才具有 `NamingTemplate` 属性。</span><span class="sxs-lookup"><span data-stu-id="29255-118">The `NamingTemplate` property is available only for parent attributes.</span></span>  
  
-   <span data-ttu-id="29255-119">层次结构</span><span class="sxs-lookup"><span data-stu-id="29255-119">Hierarchy</span></span>  
  
     <span data-ttu-id="29255-120">`Caption` 和 `AllMemberName` 属性</span><span class="sxs-lookup"><span data-stu-id="29255-120">`Caption` and `AllMemberName` properties</span></span>  
  
-   <span data-ttu-id="29255-121">级别</span><span class="sxs-lookup"><span data-stu-id="29255-121">Level</span></span>  
  
     <span data-ttu-id="29255-122">`Caption` 属性</span><span class="sxs-lookup"><span data-stu-id="29255-122">`Caption` property</span></span>  
  
 **\<Language>**  
 <span data-ttu-id="29255-123">在所选语言中键入或选择维度对象的属性值。</span><span class="sxs-lookup"><span data-stu-id="29255-123">Type or select the property value of the dimension object in the selected language.</span></span> <span data-ttu-id="29255-124">单击省略号按钮 (**...**) 可打开其他对话框，具体取决于所编辑的属性：</span><span class="sxs-lookup"><span data-stu-id="29255-124">Clicking the ellipsis button (**...**) opens additional dialog boxes, depending on the property being edited:</span></span>  
  
-   <span data-ttu-id="29255-125">`NamingTemplate` 属性</span><span class="sxs-lookup"><span data-stu-id="29255-125">`NamingTemplate` property</span></span>  
  
     <span data-ttu-id="29255-126">显示[“级别命名模板”对话框（Analysis Services - 多维数据）](level-naming-template-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="29255-126">Displays the [Level Naming Template Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](level-naming-template-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
-   <span data-ttu-id="29255-127">`Caption` 属性（针对特性）</span><span class="sxs-lookup"><span data-stu-id="29255-127">`Caption` property (for attributes)</span></span>  
  
     <span data-ttu-id="29255-128">显示[“翻译属性数据”对话框（Analysis Services - 多维数据）](attribute-data-translation-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="29255-128">Displays the [Attribute Data Translation Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](attribute-data-translation-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="shortcut-menu"></a><span data-ttu-id="29255-129">快捷菜单</span><span class="sxs-lookup"><span data-stu-id="29255-129">Shortcut Menu</span></span>  
 <span data-ttu-id="29255-130">右键单击“翻译详细信息”窗格中的翻译，所显示的快捷菜单中以下选项可用：\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="29255-130">The following options are available in the shortcut menu displayed by right-clicking a translation in the **Translation Details** pane:</span></span>  
  
 <span data-ttu-id="29255-131">**新翻译**</span><span class="sxs-lookup"><span data-stu-id="29255-131">**New Translation**</span></span>  
 <span data-ttu-id="29255-132">选择此项将显示 **“选择语言”** 对话框并创建一个新翻译。</span><span class="sxs-lookup"><span data-stu-id="29255-132">Select to display the **Select Language** dialog box and create a new translation.</span></span> <span data-ttu-id="29255-133">该翻译将在 **“翻译详细信息”** 网格中显示为一个新列。</span><span class="sxs-lookup"><span data-stu-id="29255-133">The translation will appear as a new column in the **Translation Details** grid.</span></span>  
  
 <span data-ttu-id="29255-134">**删除翻译**</span><span class="sxs-lookup"><span data-stu-id="29255-134">**Delete Translation**</span></span>  
 <span data-ttu-id="29255-135">选择此项将会删除选定翻译。</span><span class="sxs-lookup"><span data-stu-id="29255-135">Select to delete the selected translation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="29255-136">只有右键单击一个要删除其中翻译的单元后，才可启用该选项。</span><span class="sxs-lookup"><span data-stu-id="29255-136">The option is enabled only if you right-clicked a cell to delete the translation.</span></span>  
  
 <span data-ttu-id="29255-137">**新标题列**</span><span class="sxs-lookup"><span data-stu-id="29255-137">**New Caption Column**</span></span>  
 <span data-ttu-id="29255-138">在“翻译详细信息”网格中修改属性时，选择此项将显示“翻译属性数据”对话框，并可以定义新的标题列。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="29255-138">Select to display the **Attribute Data Translation** dialog box and define a new caption column when you modify an attribute in the **Translation Details** grid.</span></span> <span data-ttu-id="29255-139">若要启用此选项，必须在 **“翻译详细信息”** 网格中选择了属性的翻译列中的某个单元。</span><span class="sxs-lookup"><span data-stu-id="29255-139">To enable this option, a cell in a translation column for an attribute must be selected in the **Translation Details** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="29255-140">只有右键单击一个单元删除属性的翻译列后，才可启用该选项。</span><span class="sxs-lookup"><span data-stu-id="29255-140">The option is enabled only if you right-clicked a cell to delete the translation column of an attribute.</span></span>  
  
 <span data-ttu-id="29255-141">**编辑标题列**</span><span class="sxs-lookup"><span data-stu-id="29255-141">**Edit Caption Column**</span></span>  
 <span data-ttu-id="29255-142">在“翻译详细信息”网格中修改属性时，选择此项将显示“翻译属性数据”对话框，并可以修改现有标题列。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="29255-142">Select to display the **Attribute Data Translation** dialog box and modify an existing caption column when you modify an attribute in the **Translation Details** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="29255-143"> 只有在 **“翻译详细信息”** 网格中选择了包含属性标题列的翻译列中的某个单元时，才会启用该选项。</span><span class="sxs-lookup"><span data-stu-id="29255-143">The option is enabled only if a cell in a translation column that contains a caption column for an attribute must be selected in the **Translation Details** grid.</span></span>  
  
 <span data-ttu-id="29255-144">**删除标题列**</span><span class="sxs-lookup"><span data-stu-id="29255-144">**Delete Caption Column**</span></span>  
 <span data-ttu-id="29255-145">选择此项将删除在“翻译详细信息”网格中所选属性的标题列。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="29255-145">Select to delete the caption column for the selected attribute in the **Translation Details** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="29255-146">只有右键单击翻译列中包含属性标题列的单元时，才可启用该选项。</span><span class="sxs-lookup"><span data-stu-id="29255-146">The option is enabled only if you right-clicked a cell in a translation column that contains a caption column for an attribute.</span></span>  
  
 <span data-ttu-id="29255-147">**显示所有属性**</span><span class="sxs-lookup"><span data-stu-id="29255-147">**Show All Attributes**</span></span>  
 <span data-ttu-id="29255-148">选择此项将对为所选维度定义的所有属性（包括为属性层次结构所禁用的属性）切换显示。</span><span class="sxs-lookup"><span data-stu-id="29255-148">Select to toggle the display of all attributes defined for the selected dimension, including attributes for which attribute hierarchies are disabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29255-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29255-149">See Also</span></span>  
 [<span data-ttu-id="29255-150">&#41; &#40;Analysis Services 多维&#41;数据的翻译 &#40;维度设计器</span><span class="sxs-lookup"><span data-stu-id="29255-150">Translations &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
