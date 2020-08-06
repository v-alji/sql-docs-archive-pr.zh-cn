---
title: "\"级别命名模板\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.levelnamingtemplatedialog.f1
helpviewer_keywords:
- Level Naming Template dialog box
ms.assetid: 96cad715-213e-4eac-9003-130a2f5fc985
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dd704e619e49f0dd1adb8fed8f1e743b61309af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694625"
---
# <a name="level-naming-template-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="d1c29-102">“级别命名模板”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="d1c29-102">Level Naming Template Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="d1c29-103">可以使用 **中的** “级别命名模板” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 对话框，为维度的父属性构造级别命名模板。</span><span class="sxs-lookup"><span data-stu-id="d1c29-103">Use the **Level Naming Template** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to construct the level naming template for a parent attribute in a dimension.</span></span> <span data-ttu-id="d1c29-104">有关级别命名模板的详细信息，请参阅 [NamingTemplate 元素 (ASSL)](https://docs.microsoft.com/bi-reference/assl/properties/namingtemplate-element-assl)。</span><span class="sxs-lookup"><span data-stu-id="d1c29-104">For more information about level naming templates, see [NamingTemplate Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/namingtemplate-element-assl).</span></span> <span data-ttu-id="d1c29-105">通过在维度设计器的 "翻译" 选项卡上的 " **...** 翻译详细信息" 窗格中，通过单击省略号按钮 (...) ，可以显示 "**级别命名模板**" 对话框。 `NamingTemplate` **Translation Details** **Translations** **Dimension Designer**</span><span class="sxs-lookup"><span data-stu-id="d1c29-105">You can display the **Level Naming Template** dialog box by clicking the ellipsis button (**...**) on the `NamingTemplate` value of a translation for an attribute in the **Translation Details** pane on the **Translations** tab of **Dimension Designer**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d1c29-106">选项</span><span class="sxs-lookup"><span data-stu-id="d1c29-106">Options</span></span>  
  
|<span data-ttu-id="d1c29-107">术语</span><span class="sxs-lookup"><span data-stu-id="d1c29-107">Term</span></span>|<span data-ttu-id="d1c29-108">定义</span><span class="sxs-lookup"><span data-stu-id="d1c29-108">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="d1c29-109">**定义级别模板**</span><span class="sxs-lookup"><span data-stu-id="d1c29-109">**Define the level template**</span></span>|<span data-ttu-id="d1c29-110">显示一个网格，您可以在其中设计父属性中级别的层次结构。</span><span class="sxs-lookup"><span data-stu-id="d1c29-110">Displays a grid in which you can design the hierarchy of levels in the parent attribute.</span></span> <span data-ttu-id="d1c29-111">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="d1c29-111">The grid contains the following columns:</span></span><br /><br /> <span data-ttu-id="d1c29-112">**Level**：显示在 "**名称**" 中指定名称的级别的序号位置。</span><span class="sxs-lookup"><span data-stu-id="d1c29-112">**Level**: Displays the ordinal position of the level for which the name specified in **Name** is used.</span></span> <span data-ttu-id="d1c29-113">若要为级别添加新的命名模板，请在“级别”\*\*\*\* 中包含星号 (\*) 的行上选择“名称”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1c29-113">To add a new naming template for a level, select **Name** on the row that contains an asterisk (\*) in **Level**.</span></span><br /><br /> <span data-ttu-id="d1c29-114">"**名称**"：包含用于 "**级别**" 中所指示级别的命名模板。</span><span class="sxs-lookup"><span data-stu-id="d1c29-114">**Name**: Contains the naming template used for the level indicated in **Level**.</span></span> <span data-ttu-id="d1c29-115">若要在命名模板中为级别序号位置添加占位符，请添加单个星号 (\*)。</span><span class="sxs-lookup"><span data-stu-id="d1c29-115">To add a placeholder for the level ordinal position in the naming template, add a single asterisk (\*).</span></span> <span data-ttu-id="d1c29-116">若要添加星号作为命名模板创建的名称的一部分，请添加两个星号 (\* \*) 。</span><span class="sxs-lookup"><span data-stu-id="d1c29-116">To add an asterisk as part of the name created by the naming template, add two asterisks (\*\*).</span></span>|  
|<span data-ttu-id="d1c29-117">**全部清除**</span><span class="sxs-lookup"><span data-stu-id="d1c29-117">**Clear All**</span></span>|<span data-ttu-id="d1c29-118">选择此项可以删除 **“定义级别模板”** 中的所有行。</span><span class="sxs-lookup"><span data-stu-id="d1c29-118">Select to remove all rows in **Define the level template**.</span></span>|  
|<span data-ttu-id="d1c29-119">**结果**</span><span class="sxs-lookup"><span data-stu-id="d1c29-119">**Result**</span></span>|<span data-ttu-id="d1c29-120">显示由对话框生成的级别命名模板。</span><span class="sxs-lookup"><span data-stu-id="d1c29-120">Displays the level naming template constructed by the dialog box.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1c29-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1c29-121">See Also</span></span>  
 <span data-ttu-id="d1c29-122">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d1c29-122">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="d1c29-123">&#41; &#40;Analysis Services 多维&#41;数据的翻译 &#40;维度设计器</span><span class="sxs-lookup"><span data-stu-id="d1c29-123">Translations &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
