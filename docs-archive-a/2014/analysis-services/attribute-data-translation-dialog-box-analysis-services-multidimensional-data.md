---
title: "\"属性数据转换\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.dimensionstoragesettings.f1
helpviewer_keywords:
- Attribute Data Translation dialog box
ms.assetid: bed286de-1e9b-49de-b09e-3cd076aba152
author: minewiskan
ms.author: owend
ms.openlocfilehash: b61022ec2cb8726fc034e13a0d63e432df6ec151
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579367"
---
# <a name="attribute-data-translation-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="a4523-102">“翻译属性数据”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="a4523-102">Attribute Data Translation Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="a4523-103">可以使用 **“翻译属性数据”** 对话框设置包含翻译标题数据的列，以及与翻译数据一起使用的排序规则和排序顺序。</span><span class="sxs-lookup"><span data-stu-id="a4523-103">Use the **Attribute Data Translation** dialog box to set the column that contains the translation caption data, as well as the collation and sort order to be used with the translated data.</span></span> <span data-ttu-id="a4523-104">通过执行以下操作可以显示 **“翻译属性数据”** 对话框：</span><span class="sxs-lookup"><span data-stu-id="a4523-104">You can display the **Attribute Data Translation** dialog box by:</span></span>  
  
-   <span data-ttu-id="a4523-105">在 **维度设计器** 的 **“翻译”** 选项卡上，在 **“工具栏”** 窗格中单击 **“新建标题列”** 或 **“编辑标题列”**。</span><span class="sxs-lookup"><span data-stu-id="a4523-105">Clicking **New caption column** or **Edit caption column** from the **Toolbar** pane on the **Translations** tab of **Dimension Designer**.</span></span>  
  
-   <span data-ttu-id="a4523-106">在**维度设计器**的“翻译”选项卡上，右键单击“翻译详细信息”窗格，再选择“新建标题列”或“编辑标题列”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a4523-106">Right-clicking the **Translation Details** pane on the **Translations** tab of **Dimension Designer** and selecting **New caption column** or **Edit caption column**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a4523-107">选项</span><span class="sxs-lookup"><span data-stu-id="a4523-107">Options</span></span>  
 <span data-ttu-id="a4523-108">**特性**</span><span class="sxs-lookup"><span data-stu-id="a4523-108">**Attribute**</span></span>  
 <span data-ttu-id="a4523-109">显示所选属性。</span><span class="sxs-lookup"><span data-stu-id="a4523-109">Displays the selected attribute.</span></span>  
  
 <span data-ttu-id="a4523-110">**语言**</span><span class="sxs-lookup"><span data-stu-id="a4523-110">**Language**</span></span>  
 <span data-ttu-id="a4523-111">显示所选语言。</span><span class="sxs-lookup"><span data-stu-id="a4523-111">Displays the selected language.</span></span>  
  
 <span data-ttu-id="a4523-112">**翻译后的标题**</span><span class="sxs-lookup"><span data-stu-id="a4523-112">**Translated caption**</span></span>  
 <span data-ttu-id="a4523-113">为所选属性设置当前已翻译的标题。</span><span class="sxs-lookup"><span data-stu-id="a4523-113">Sets the current translated caption for the selected attribute.</span></span>  
  
 <span data-ttu-id="a4523-114">**翻译列**</span><span class="sxs-lookup"><span data-stu-id="a4523-114">**Translation columns**</span></span>  
 <span data-ttu-id="a4523-115">设置存储翻译标题数据的列。</span><span class="sxs-lookup"><span data-stu-id="a4523-115">Sets the column where the translation caption data is stored.</span></span> <span data-ttu-id="a4523-116">只能选择一列。</span><span class="sxs-lookup"><span data-stu-id="a4523-116">Only one column can be selected.</span></span> <span data-ttu-id="a4523-117">将显示主维度表引用的所有相关表。</span><span class="sxs-lookup"><span data-stu-id="a4523-117">All related tables that are referred to by the primary dimension table will be displayed.</span></span>  
  
 <span data-ttu-id="a4523-118">**排序规则指示符**</span><span class="sxs-lookup"><span data-stu-id="a4523-118">**Collation designator**</span></span>  
 <span data-ttu-id="a4523-119">为所选属性设置排序规则指示符。</span><span class="sxs-lookup"><span data-stu-id="a4523-119">Sets the collation designator for the selected attribute.</span></span> <span data-ttu-id="a4523-120">默认情况下，选择当前的 Windows 排序规则。</span><span class="sxs-lookup"><span data-stu-id="a4523-120">By default, the current Windows collation is selected.</span></span> <span data-ttu-id="a4523-121">单击下箭头可以从可用的排序规则中进行选择。</span><span class="sxs-lookup"><span data-stu-id="a4523-121">Click the down arrow to select from the available collations.</span></span>  
  
 <span data-ttu-id="a4523-122">**二进制**</span><span class="sxs-lookup"><span data-stu-id="a4523-122">**Binary**</span></span>  
 <span data-ttu-id="a4523-123">选择此选项可根据为每个字符定义的位模式对数据进行排序和比较。</span><span class="sxs-lookup"><span data-stu-id="a4523-123">Select this option to sort and compare data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="a4523-124">二进制排序顺序区分大小写，即先小写字母后大写字母，并区分重音。</span><span class="sxs-lookup"><span data-stu-id="a4523-124">Binary sort order is case-sensitive, that is, lowercase precedes uppercase, and accent-sensitive.</span></span> <span data-ttu-id="a4523-125">这是最快的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="a4523-125">This is the fastest sorting order.</span></span>  
  
 <span data-ttu-id="a4523-126">如果未选择此选项，则 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将遵循字典中定义的相关语言或字母表的排序和比较规则。</span><span class="sxs-lookup"><span data-stu-id="a4523-126">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] follows sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4523-127">如果选择此选项，将会禁用“区分大小写”、“区分重音”、“区分假名”和“区分全半角”选项。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a4523-127">If this option is selected, the **Case sensitive**, **Accent sensitive**, **Kana sensitive**, and **Width sensitive** options are disabled.</span></span>  
  
 <span data-ttu-id="a4523-128">**区分大小写**</span><span class="sxs-lookup"><span data-stu-id="a4523-128">**Case sensitive**</span></span>  
 <span data-ttu-id="a4523-129">选择此选项可以根据为相关语言或字母表提供的字典规则对数据进行排序和比较，并区分大小写字母。</span><span class="sxs-lookup"><span data-stu-id="a4523-129">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between uppercase and lowercase letters.</span></span>  
  
 <span data-ttu-id="a4523-130">如果不选择此选项， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将认为大小写字母是等价的。</span><span class="sxs-lookup"><span data-stu-id="a4523-130">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the uppercase and lowercase versions of letters to be equal.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="a4523-131">如果未选择 "**区分大小写**"，则不会定义小写字母是否根据大写字母进行排序。</span><span class="sxs-lookup"><span data-stu-id="a4523-131">does not define whether lowercase letters sort lower or higher in relation to uppercase letters when **Case-sensitive** is not selected.</span></span>  
  
 <span data-ttu-id="a4523-132">**区分重音**</span><span class="sxs-lookup"><span data-stu-id="a4523-132">**Accent sensitive**</span></span>  
 <span data-ttu-id="a4523-133">选择此选项可以根据为相关语言或字母表提供的字典规则对数据进行排序和比较，并区分重音和非重音字符。</span><span class="sxs-lookup"><span data-stu-id="a4523-133">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between accented and unaccented characters.</span></span> <span data-ttu-id="a4523-134">例如，“a”和“á”将被视为不同的字符。</span><span class="sxs-lookup"><span data-stu-id="a4523-134">For example, 'a' is not equal to 'á'.</span></span>  
  
 <span data-ttu-id="a4523-135">如果不选择此选项， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将认为重音与相应的非重音字母是等价的。</span><span class="sxs-lookup"><span data-stu-id="a4523-135">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the accented and unaccented versions of letters to be equal.</span></span>  
  
 <span data-ttu-id="a4523-136">**区分假名**</span><span class="sxs-lookup"><span data-stu-id="a4523-136">**Kana sensitive**</span></span>  
 <span data-ttu-id="a4523-137">选择此选项可以根据为相关语言或字母表提供的字典规则对数据进行排序和比较，并区分日语中的两种假名字符类型：平假名和片假名。</span><span class="sxs-lookup"><span data-stu-id="a4523-137">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between the two types of Japanese kana characters: Hiragana and Katakana.</span></span>  
  
 <span data-ttu-id="a4523-138">如果不选择此选项， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将认为平假名和片假名字符是等价的。</span><span class="sxs-lookup"><span data-stu-id="a4523-138">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers Hiragana and Katakana characters to be equal.</span></span>  
  
 <span data-ttu-id="a4523-139">**区分全半角**</span><span class="sxs-lookup"><span data-stu-id="a4523-139">**Width sensitive**</span></span>  
 <span data-ttu-id="a4523-140">选择此选项可以根据为相关语言或字母表提供的字典规则对数据进行排序和比较，并区分以单字节字符（半角）和双字节字符（全角）表示的相同字符。</span><span class="sxs-lookup"><span data-stu-id="a4523-140">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between a single-byte character (half-width) and the same character when represented as a double-byte character (full-width).</span></span>  
  
 <span data-ttu-id="a4523-141">如果不选择此选项， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将认为相同字符的单字节表示法和双字节表示法是等价的。</span><span class="sxs-lookup"><span data-stu-id="a4523-141">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the single-byte and double-byte representation of the same character to be equal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4523-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4523-142">See Also</span></span>  
 <span data-ttu-id="a4523-143">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a4523-143">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="a4523-144">翻译详细信息 &#40;翻译 "选项卡，维度设计器&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="a4523-144">Translation Details &#40;Translations Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](translation-details-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
