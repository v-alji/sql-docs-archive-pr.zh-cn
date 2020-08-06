---
title: " (数据挖掘向导) 中指定定型数据 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifytrainingdata.f1
ms.assetid: cb04deeb-0f89-4bba-b3f1-efccada16825
author: minewiskan
ms.author: owend
ms.openlocfilehash: 87a802256d287a3e8e9e7fb65bbd91687cb71a4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589240"
---
# <a name="specify-the-training-data-data-mining-wizard"></a><span data-ttu-id="b81d0-102">指定定型数据（数据挖掘向导）</span><span class="sxs-lookup"><span data-stu-id="b81d0-102">Specify the Training Data (Data Mining Wizard)</span></span>
  <span data-ttu-id="b81d0-103">可以使用 **“指定定型数据”** 页，确定要在挖掘结构中包括哪些列。</span><span class="sxs-lookup"><span data-stu-id="b81d0-103">Use the **Specify the Training Data** page to identify which columns to include in the mining structure.</span></span> <span data-ttu-id="b81d0-104">即使在所有模型中都不使用某些列，也可以选择将其包括在结构中。</span><span class="sxs-lookup"><span data-stu-id="b81d0-104">You can select columns to include in the structure even if you do not use them in all models.</span></span> <span data-ttu-id="b81d0-105">例如，如果希望从挖掘模型中钻取到列，则您可以将其包括在结构中但不包括在模型中。</span><span class="sxs-lookup"><span data-stu-id="b81d0-105">For example, if you want to drill through to the columns from the mining model, you can include them in the structure but not in the model.</span></span>  
  
 <span data-ttu-id="b81d0-106">结构中包括的每个表至少需要一个键列。</span><span class="sxs-lookup"><span data-stu-id="b81d0-106">At least one key column is required for each table that is included in the structure.</span></span> <span data-ttu-id="b81d0-107">选作键的列取决于该表是事例表还是嵌套表。</span><span class="sxs-lookup"><span data-stu-id="b81d0-107">The column that you pick as the key depends on whether the table is a case table or a nested table.</span></span> <span data-ttu-id="b81d0-108">如果该表是嵌套表，则键通常还是可预测列，而不是关系外键。</span><span class="sxs-lookup"><span data-stu-id="b81d0-108">If the table is a nested table, the key is often also the predictable column, not the relational foreign key.</span></span> <span data-ttu-id="b81d0-109">若要了解嵌套键，请参阅[嵌套表（Analysis Services - 数据挖掘）](data-mining/nested-tables-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="b81d0-109">To learn about nested keys, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](data-mining/nested-tables-analysis-services-data-mining.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b81d0-110">不同的挖掘算法使用键的方式也不同。</span><span class="sxs-lookup"><span data-stu-id="b81d0-110">Different mining algorithms use keys differently.</span></span> <span data-ttu-id="b81d0-111">若要了解不同种类的键，请参阅[内容类型（数据挖掘）](data-mining/content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="b81d0-111">To learn about the different kinds of keys, see [Content Types &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="b81d0-112">**有关详细信息：** [挖掘结构（Analysis Services - 数据挖掘）](data-mining/mining-structures-analysis-services-data-mining.md)、[挖掘模型列](data-mining/mining-model-columns.md)、[数据挖掘向导（Analysis Services - 数据挖掘）](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[创建关系挖掘结构](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="b81d0-112">**For More Information:** [Mining Structures &#40;Analysis Services - Data Mining&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [Mining Model Columns](data-mining/mining-model-columns.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="b81d0-113">选项</span><span class="sxs-lookup"><span data-stu-id="b81d0-113">Options</span></span>  
 <span data-ttu-id="b81d0-114">**表/列**</span><span class="sxs-lookup"><span data-stu-id="b81d0-114">**Tables/Columns**</span></span>  
 <span data-ttu-id="b81d0-115">显示在向导上一页中选择的表和列。</span><span class="sxs-lookup"><span data-stu-id="b81d0-115">Displays the tables and columns that you selected on the previous page of the wizard.</span></span>  
  
 **\<check box>**  
 <span data-ttu-id="b81d0-116">选择挖掘结构中要包括的列。</span><span class="sxs-lookup"><span data-stu-id="b81d0-116">Select the columns to include in the mining structure.</span></span>  
  
 <span data-ttu-id="b81d0-117">如果数据源包括嵌套表或多个视图，请展开列列表以查看嵌套的表。</span><span class="sxs-lookup"><span data-stu-id="b81d0-117">If your data source includes nested tables or multiple views, expand the column list to view the nested tables.</span></span>  
  
 <span data-ttu-id="b81d0-118">**Key**</span><span class="sxs-lookup"><span data-stu-id="b81d0-118">**Key**</span></span>  
 <span data-ttu-id="b81d0-119">选择此选项可将相应的列用作数据的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="b81d0-119">Select to use the column as a unique identifier for the data.</span></span>  
  
 <span data-ttu-id="b81d0-120">对于事例表，键通常为唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="b81d0-120">For a case table, the key is usually the unique identifier.</span></span>  
  
 <span data-ttu-id="b81d0-121">对于嵌套表， **“键”** 指示关联事例上下文中行的标识符。</span><span class="sxs-lookup"><span data-stu-id="b81d0-121">For nested table, the **Key** indicates the identifier of a row in the context of the associated case.</span></span>  
  
 <span data-ttu-id="b81d0-122">**输入**</span><span class="sxs-lookup"><span data-stu-id="b81d0-122">**Input**</span></span>  
 <span data-ttu-id="b81d0-123">选择此选项可在创建预测时使用相应的列。</span><span class="sxs-lookup"><span data-stu-id="b81d0-123">Select to use the column in creating predictions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b81d0-124">只有在创建挖掘结构的同时创建挖掘模型时，此列才可用。</span><span class="sxs-lookup"><span data-stu-id="b81d0-124">This column is only available when you are creating a mining model together with the mining structure.</span></span>  
  
 <span data-ttu-id="b81d0-125">**可预测**</span><span class="sxs-lookup"><span data-stu-id="b81d0-125">**Predictable**</span></span>  
 <span data-ttu-id="b81d0-126">如果选择此选项，则相应的表或列可以根据将来的额外输入来进行预测。</span><span class="sxs-lookup"><span data-stu-id="b81d0-126">Select to enable the table or column to be predicted based on additional future input.</span></span>  
  
 <span data-ttu-id="b81d0-127">如果还将某个嵌套表标记为可预测的，则整个嵌套表都可预测。</span><span class="sxs-lookup"><span data-stu-id="b81d0-127">If you also mark a nested table as predictable, the whole nested table becomes predictable.</span></span> <span data-ttu-id="b81d0-128">如果嵌套表中没有标记为输入列或可预测列的列，则嵌套表将显示在挖掘结构中，但在模型中将被忽略。</span><span class="sxs-lookup"><span data-stu-id="b81d0-128">If no columns in the nested table are marked as input or predictable, the nested table will appear in the mining structure, but will be ignored in the model.</span></span>  
  
 <span data-ttu-id="b81d0-129">**注意** ：只有在创建挖掘结构的同时创建挖掘模型时，此列才可用。</span><span class="sxs-lookup"><span data-stu-id="b81d0-129">**Note** This column is only available when you are creating a mining model together with the mining structure.</span></span>  
  
 <span data-ttu-id="b81d0-130">**建议**</span><span class="sxs-lookup"><span data-stu-id="b81d0-130">**Suggest**</span></span>  
 <span data-ttu-id="b81d0-131">单击此项可打开“提供相关列建议”\*\*\*\* 对话框，该对话框可根据 entropy 对数据样本进行分析，以标识与所选“可预测”\*\*\*\* 列最为相关的输入列。</span><span class="sxs-lookup"><span data-stu-id="b81d0-131">Click to open the **Suggest Related Columns** dialog box, which performs an analysis on a sample of data to identify input columns that show the greatest relationship to the selected **Predictable** column based on entropy.</span></span> <span data-ttu-id="b81d0-132">此分析也适用于嵌套表列或基于 OLAP 源的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="b81d0-132">This analysis also applies to nested table columns or mining structures that are based on OLAP sources.</span></span>  
  
 <span data-ttu-id="b81d0-133">**注意** ：只有在创建挖掘结构的同时创建挖掘模型时，此列才可用。</span><span class="sxs-lookup"><span data-stu-id="b81d0-133">**Note** This column only available when you are creating a mining model together with the mining structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b81d0-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b81d0-134">See Also</span></span>  
 <span data-ttu-id="b81d0-135">[数据挖掘向导 F1 帮助 &#40;Analysis Services 数据挖掘&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b81d0-135">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="b81d0-136">[在数据挖掘向导 &#40;建议相关列&#41;](suggest-related-columns-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="b81d0-136">[Suggest Related Columns &#40;Data Mining Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="b81d0-137">[在数据挖掘向导 &#40;指定表类型&#41;](specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="b81d0-137">[Specify Table Types &#40;Data Mining Wizard&#41;](specify-table-types-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="b81d0-138">指定数据挖掘向导 &#40;列的内容和数据类型&#41;</span><span class="sxs-lookup"><span data-stu-id="b81d0-138">Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;</span></span>](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
