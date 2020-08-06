---
title: " (数据挖掘向导) 指定&#39;s 内容和数据类型的列 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifycontentdatatype.f1
ms.assetid: 7061f674-e806-46f2-8c15-e260a3c69a17
author: minewiskan
ms.author: owend
ms.openlocfilehash: 66af7280e444036468b9cc33a131993524d3586d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589243"
---
# <a name="specify-the-column39s-content-and-data-type-data-mining-wizard"></a><span data-ttu-id="f9390-102">在数据挖掘向导 (指定&#39;s 内容和数据类型的列) </span><span class="sxs-lookup"><span data-stu-id="f9390-102">Specify the Column&#39;s Content and Data Type (Data Mining Wizard)</span></span>
  <span data-ttu-id="f9390-103">可以使用 **“指定列的内容和数据类型”** 页修改向导已设置的列和内容类型。</span><span class="sxs-lookup"><span data-stu-id="f9390-103">Use the **Specify the Column's Content and Data Type** page to modify the column and content types that have already been set by the wizard.</span></span> <span data-ttu-id="f9390-104">向导使用源列的数据类型和所选算法的功能来确定每个列的默认数据和内容类型。</span><span class="sxs-lookup"><span data-stu-id="f9390-104">The wizard uses the data types of the source columns and the capabilities of the selected algorithm to determine the default data and content types for each column.</span></span>  
  
 <span data-ttu-id="f9390-105">**有关详细信息，请参阅** [数据挖掘向导（Analysis Services - 数据挖掘）](data-mining/data-mining-wizard-analysis-services-data-mining.md)[创建关系挖掘结构](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="f9390-105">**For More Information:** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="f9390-106">选项</span><span class="sxs-lookup"><span data-stu-id="f9390-106">Options</span></span>  
 <span data-ttu-id="f9390-107">**“列”**</span><span class="sxs-lookup"><span data-stu-id="f9390-107">**Columns**</span></span>  
 <span data-ttu-id="f9390-108">在向导的“指定定型数据”\*\*\*\* 页中定义的列的列表。</span><span class="sxs-lookup"><span data-stu-id="f9390-108">A list of the columns that are defined in the **Specify the Training Data** page of the wizard.</span></span>  
  
 <span data-ttu-id="f9390-109">**内容类型**</span><span class="sxs-lookup"><span data-stu-id="f9390-109">**Content Type**</span></span>  
 <span data-ttu-id="f9390-110">为每个列分配的内容类型。</span><span class="sxs-lookup"><span data-stu-id="f9390-110">The content type that is assigned to each column.</span></span> <span data-ttu-id="f9390-111">单击单元内的区域可以更改内容类型。</span><span class="sxs-lookup"><span data-stu-id="f9390-111">Click inside a cell to change the content type.</span></span> <span data-ttu-id="f9390-112">有关内容类型的详细信息，请参阅[内容类型（数据挖掘）](data-mining/content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="f9390-112">For more information about content types, see [Content Types &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="f9390-113">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="f9390-113">**Data Type**</span></span>  
 <span data-ttu-id="f9390-114">为每个列分配的数据类型。</span><span class="sxs-lookup"><span data-stu-id="f9390-114">The data types that are assigned to each column.</span></span> <span data-ttu-id="f9390-115">单击单元内的区域可以更改数据类型。</span><span class="sxs-lookup"><span data-stu-id="f9390-115">Click inside a cell to change the data type.</span></span> <span data-ttu-id="f9390-116">有关数据类型的详细信息，请参阅[数据类型（数据挖掘）](data-mining/data-types-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="f9390-116">For more information about data types, see [Data Types &#40;Data Mining&#41;](data-mining/data-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="f9390-117">**Detect**</span><span class="sxs-lookup"><span data-stu-id="f9390-117">**Detect**</span></span>  
 <span data-ttu-id="f9390-118">单击可自动检测数值列的连续内容类型和离散内容类型。</span><span class="sxs-lookup"><span data-stu-id="f9390-118">Click to automatically detect the continuous and discrete content types for numeric column.</span></span> <span data-ttu-id="f9390-119">此选项不适用于基于 OLAP 数据源的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="f9390-119">This does not apply to mining structures that are based on OLAP data sources.</span></span> <span data-ttu-id="f9390-120">对于 OLAP 挖掘结构，该向导将自动检测内容类型，并选择与所选算法兼容的类型。</span><span class="sxs-lookup"><span data-stu-id="f9390-120">For OLAP mining structures, the wizard automatically detects content types and chooses a type that is compatible with the selected algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9390-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9390-121">See Also</span></span>  
 <span data-ttu-id="f9390-122">[完成向导 &#40;数据挖掘向导&#41;](completing-the-wizard-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="f9390-122">[Completing the Wizard &#40;Data Mining Wizard&#41;](completing-the-wizard-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="f9390-123">[数据挖掘向导 F1 帮助 &#40;Analysis Services 数据挖掘&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f9390-123">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="f9390-124">在数据挖掘向导 &#40;指定定型数据&#41;</span><span class="sxs-lookup"><span data-stu-id="f9390-124">Specify the Training Data &#40;Data Mining Wizard&#41;</span></span>](specify-the-training-data-data-mining-wizard.md)  
  
  
