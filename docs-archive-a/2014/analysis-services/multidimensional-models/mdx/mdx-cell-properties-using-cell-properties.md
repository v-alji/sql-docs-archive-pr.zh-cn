---
title: 使用单元属性 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- intrinsic cell properties [MDX]
- cells [MDX]
- cell properties [MDX]
- CELL PROPERTIES keyword
ms.assetid: a593c74d-8c5e-485e-bd92-08f9d22451d4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 996b873bfd52f1d695eb613d1fd407decbf493c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587063"
---
# <a name="using-cell-properties-mdx"></a><span data-ttu-id="a0cf1-102">使用单元属性 (MDX)</span><span class="sxs-lookup"><span data-stu-id="a0cf1-102">Using Cell Properties (MDX)</span></span>
  <span data-ttu-id="a0cf1-103">多维表达式 (MDX) 中的单元属性包含有关多维数据源（如多维数据集）中的单元的内容和格式的信息。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-103">Cell properties in Multidimensional Expressions (MDX) contain information about the content and format of cells in a multidimensional data source, such as a cube.</span></span>  
  
 <span data-ttu-id="a0cf1-104">MDX 支持使用 MDX SELECT 语句中的 CELL PROPERTIES 关键字来检索内部单元属性。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-104">MDX supports the CELL PROPERTIES keyword in an MDX SELECT statement to retrieve intrinsic cell properties.</span></span> <span data-ttu-id="a0cf1-105">内部单元属性通常用于协助单元数据的直观显示。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-105">Intrinsic cell properties are most commonly used to assist in the visual presentation of cell data.</span></span>  
  
## <a name="cell-properties-keyword-syntax"></a><span data-ttu-id="a0cf1-106">CELL PROPERTIES 关键字的语法</span><span class="sxs-lookup"><span data-stu-id="a0cf1-106">CELL PROPERTIES Keyword Syntax</span></span>  
 <span data-ttu-id="a0cf1-107">MDX `CELL PROPERTIES` 语句中的 `SELECT` 关键字使用下列语法：</span><span class="sxs-lookup"><span data-stu-id="a0cf1-107">Use the following syntax for the `CELL PROPERTIES` keyword of the MDX `SELECT` statement:</span></span>  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
[<cell_props>]  
```  
  
 <span data-ttu-id="a0cf1-108">下列语法显示了 `<cell_props>` 值的格式，以及此值如何将 `CELL PROPERTIES` 关键字与一个或多个内部单元属性一起使用：</span><span class="sxs-lookup"><span data-stu-id="a0cf1-108">The following syntax shows the format of the `<cell_props>` value and how this value uses the `CELL PROPERTIES` keyword along with one or more intrinsic cell properties:</span></span>  
  
```  
<cell_props> ::= CELL PROPERTIES <property> [, <property>...]  
```  
  
## <a name="supported-intrinsic-cell-properties"></a><span data-ttu-id="a0cf1-109">支持的内部单元属性</span><span class="sxs-lookup"><span data-stu-id="a0cf1-109">Supported Intrinsic Cell Properties</span></span>  
 <span data-ttu-id="a0cf1-110">下表列出了 `<property>` 值中使用的、支持的内部单元属性。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-110">The following table lists the supported intrinsic cell properties that are used in the `<property>` value.</span></span>  
  
|<span data-ttu-id="a0cf1-111">属性</span><span class="sxs-lookup"><span data-stu-id="a0cf1-111">Property</span></span>|<span data-ttu-id="a0cf1-112">说明</span><span class="sxs-lookup"><span data-stu-id="a0cf1-112">Description</span></span>|  
|--------------|-----------------|  
|`ACTION_TYPE`|<span data-ttu-id="a0cf1-113">指示单元中存在何种操作的位掩码。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-113">A bitmask that indicates which types of actions exist on the cell.</span></span> <span data-ttu-id="a0cf1-114">此属性可以具有下列值之一：</span><span class="sxs-lookup"><span data-stu-id="a0cf1-114">This property can have one of the following values:</span></span><br /><br /> <span data-ttu-id="a0cf1-115">**MDACTION_TYPE_URL**</span><span class="sxs-lookup"><span data-stu-id="a0cf1-115">**MDACTION_TYPE_URL**</span></span><br /><br /> <span data-ttu-id="a0cf1-116">**MDACTION_TYPE_HTML**</span><span class="sxs-lookup"><span data-stu-id="a0cf1-116">**MDACTION_TYPE_HTML**</span></span><br /><br /> <span data-ttu-id="a0cf1-117">**MDACTION_TYPE_STATEMENT**</span><span class="sxs-lookup"><span data-stu-id="a0cf1-117">**MDACTION_TYPE_STATEMENT**</span></span><br /><br /> <span data-ttu-id="a0cf1-118">**MDACTION_TYPE_DATASET**</span><span class="sxs-lookup"><span data-stu-id="a0cf1-118">**MDACTION_TYPE_DATASET**</span></span><br /><br /> <span data-ttu-id="a0cf1-119">**MDACTION_TYPE_ROWSET**</span><span class="sxs-lookup"><span data-stu-id="a0cf1-119">**MDACTION_TYPE_ROWSET**</span></span><br /><br /> <span data-ttu-id="a0cf1-120">**MDACTION_TYPE_COMMANDLINE**</span><span class="sxs-lookup"><span data-stu-id="a0cf1-120">**MDACTION_TYPE_COMMANDLINE**</span></span><br /><br /> <span data-ttu-id="a0cf1-121">**MDACTION_TYPE_PROPRIETARY**</span><span class="sxs-lookup"><span data-stu-id="a0cf1-121">**MDACTION_TYPE_PROPRIETARY**</span></span><br /><br /> <span data-ttu-id="a0cf1-122">**MDACTION_TYPE_REPORT**</span><span class="sxs-lookup"><span data-stu-id="a0cf1-122">**MDACTION_TYPE_REPORT**</span></span><br /><br /> <span data-ttu-id="a0cf1-123">**MDACTION_TYPE_DRILLTHROUGH**</span><span class="sxs-lookup"><span data-stu-id="a0cf1-123">**MDACTION_TYPE_DRILLTHROUGH**</span></span><br /><br /> <br /><br /> <span data-ttu-id="a0cf1-124">注意：对于在 where 子句中包含集的查询来说，不包含钻取操作。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-124">Note: Drillthrough actions are not included for queries containing a set in the where clause.</span></span>|  
|<span data-ttu-id="a0cf1-125">**BACK_COLOR**</span><span class="sxs-lookup"><span data-stu-id="a0cf1-125">**BACK_COLOR**</span></span>|<span data-ttu-id="a0cf1-126">用于显示 `VALUE` 或 `FORMATTED_VALUE` 属性的背景色。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-126">The background color for displaying the `VALUE` or `FORMATTED_VALUE` property.</span></span> <span data-ttu-id="a0cf1-127">有关详细信息，请参阅 [FORE_COLOR 和 BACK_COLOR 内容 (MDX)](mdx-cell-properties-fore-color-and-back-color-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-127">For more information, see [FORE_COLOR and BACK_COLOR Contents &#40;MDX&#41;](mdx-cell-properties-fore-color-and-back-color-contents.md).</span></span>|  
|`CELL_ORDINAL`|<span data-ttu-id="a0cf1-128">数据集中单元的序号。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-128">The ordinal number of the cell in the dataset.</span></span>|  
|<span data-ttu-id="a0cf1-129">**FONT_FLAGS**</span><span class="sxs-lookup"><span data-stu-id="a0cf1-129">**FONT_FLAGS**</span></span>|<span data-ttu-id="a0cf1-130">字体的位掩码细节效果。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-130">The bitmask detailing effects on the font.</span></span> <span data-ttu-id="a0cf1-131">例如，值 5 表示粗体 (`MDFF_BOLD`) 和下划线 (`MDFF_UNDERLINE`) 字体效果的组合。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-131">For example, the value 5 represents the combination of bold (`MDFF_BOLD`) and underline (`MDFF_UNDERLINE`) font effects.</span></span> <span data-ttu-id="a0cf1-132">该值是对以下一个或多个常量执行按位 OR 操作的结果：</span><span class="sxs-lookup"><span data-stu-id="a0cf1-132">The value is the result of a bitwise OR operation of one or more of the following constants:</span></span><br /><br /> <span data-ttu-id="a0cf1-133">`MDFF_BOLD` = 1</span><span class="sxs-lookup"><span data-stu-id="a0cf1-133">`MDFF_BOLD` = 1</span></span><br /><br /> <span data-ttu-id="a0cf1-134">`MDFF_ITALIC` = 2</span><span class="sxs-lookup"><span data-stu-id="a0cf1-134">`MDFF_ITALIC` = 2</span></span><br /><br /> <span data-ttu-id="a0cf1-135">`MDFF_UNDERLINE` = 4</span><span class="sxs-lookup"><span data-stu-id="a0cf1-135">`MDFF_UNDERLINE` = 4</span></span><br /><br /> <span data-ttu-id="a0cf1-136">`MDFF_STRIKEOUT` = 8</span><span class="sxs-lookup"><span data-stu-id="a0cf1-136">`MDFF_STRIKEOUT` = 8</span></span>|  
|<span data-ttu-id="a0cf1-137">**FONT_NAME**</span><span class="sxs-lookup"><span data-stu-id="a0cf1-137">**FONT_NAME**</span></span>|<span data-ttu-id="a0cf1-138">用来显示 `VALUE` 或 `FORMATTED_VALUE` 属性的字体。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-138">The font to be used to display the `VALUE` or `FORMATTED_VALUE` property.</span></span>|  
|<span data-ttu-id="a0cf1-139">**FONT_SIZE**</span><span class="sxs-lookup"><span data-stu-id="a0cf1-139">**FONT_SIZE**</span></span>|<span data-ttu-id="a0cf1-140">用来显示 `VALUE` 或 `FORMATTED_VALUE` 属性的字体大小。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-140">Font size to be used to display the `VALUE` or `FORMATTED_VALUE` property.</span></span>|  
|<span data-ttu-id="a0cf1-141">**FORE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="a0cf1-141">**FORE_COLOR**</span></span>|<span data-ttu-id="a0cf1-142">用来显示 `VALUE` 或 `FORMATTED_VALUE` 属性的前景色。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-142">The foreground color for displaying the `VALUE` or `FORMATTED_VALUE` property.</span></span> <span data-ttu-id="a0cf1-143">有关详细信息，请参阅 [FORE_COLOR 和 BACK_COLOR 内容 (MDX)](mdx-cell-properties-fore-color-and-back-color-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-143">For more information, see [FORE_COLOR and BACK_COLOR Contents &#40;MDX&#41;](mdx-cell-properties-fore-color-and-back-color-contents.md).</span></span>|  
|`FORMAT`|<span data-ttu-id="a0cf1-144">与 `FORMAT_STRING` 相同。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-144">Same as `FORMAT_STRING`.</span></span>|  
|`FORMAT_STRING`|<span data-ttu-id="a0cf1-145">用来创建 `FORMATTED_VALUE` 属性值的格式字符串。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-145">The format string used to create the `FORMATTED_VALUE` property value.</span></span> <span data-ttu-id="a0cf1-146">有关详细信息，请参阅 [FORMAT_STRING 内容 (MDX)](mdx-cell-properties-format-string-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-146">For more information, see [FORMAT_STRING Contents &#40;MDX&#41;](mdx-cell-properties-format-string-contents.md).</span></span>|  
|`FORMATTED_VALUE`|<span data-ttu-id="a0cf1-147">表示 `VALUE` 属性的格式化显示的字符串。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-147">The character string that represents a formatted display of the `VALUE` property.</span></span>|  
|`LANGUAGE`|<span data-ttu-id="a0cf1-148">应用 `FORMAT_STRING` 的区域设置。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-148">The locale where the `FORMAT_STRING` will be applied.</span></span> <span data-ttu-id="a0cf1-149">`LANGUAGE` 通常用于进行货币转换。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-149">`LANGUAGE` is usually used for currency conversion.</span></span>|  
|`UPDATEABLE`|<span data-ttu-id="a0cf1-150">指示单元是否可更新的值。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-150">A value that indicates whether the cell can be updated.</span></span> <span data-ttu-id="a0cf1-151">此属性可以具有下列值之一：</span><span class="sxs-lookup"><span data-stu-id="a0cf1-151">This property can have one of the following values:</span></span><br /><br /> <span data-ttu-id="a0cf1-152">`MD_MASK_ENABLED` (0x00000000) 可以更新单元。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-152">`MD_MASK_ENABLED` (0x00000000)   The cell can be updated.</span></span><br /><br /> <span data-ttu-id="a0cf1-153">`MD_MASK_NOT_ENABLED` (0x10000000) 无法更新单元。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-153">`MD_MASK_NOT_ENABLED` (0x10000000)   The cell cannot be updated.</span></span><br /><br /> <span data-ttu-id="a0cf1-154">`CELL_UPDATE_ENABLED` (0x00000001) 可在单元集中更新单元。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-154">`CELL_UPDATE_ENABLED` (0x00000001)   Cell can be updated in the cellset.</span></span><br /><br /> <span data-ttu-id="a0cf1-155">`CELL_UPDATE_ENABLED_WITH_UPDATE` (0x00000002) 可以使用 update 语句更新单元。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-155">`CELL_UPDATE_ENABLED_WITH_UPDATE` (0x00000002)   The cell can be updated with an update statement.</span></span> <span data-ttu-id="a0cf1-156">如果更新的叶单元未启用写操作，更新可能会失败。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-156">The update may fail if a leaf cell is updated that is not write-enabled.</span></span><br /><br /> <span data-ttu-id="a0cf1-157">`CELL_UPDATE_NOT_ENABLED_FORMULA`无法更新 0x10000001)  (，因为该单元在其坐标中有一个计算成员;使用 where 子句中的集检索该单元。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-157">`CELL_UPDATE_NOT_ENABLED_FORMULA` (0x10000001)   The cell cannot be updated because the cell has a calculated member among its coordinates; the cell was retrieved with a set in the where clause.</span></span> <span data-ttu-id="a0cf1-158">即使公式影响单元值或单元值上存在计算单元（在沿聚合路径的某个位置），仍可以更新单元。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-158">A cell can be updated even though a formula affects, or a calculated cell is on, the value of a cell (is somewhere along the aggregation path).</span></span> <span data-ttu-id="a0cf1-159">在这种情况下，单元的最终值可能不是更新后的值，因为计算将影响结果。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-159">In this scenario, the final value of the cell may not be the updated value, because the calculation will affect the result</span></span><br /><br /> <span data-ttu-id="a0cf1-160">`CELL_UPDATE_NOT_ENABLED_NONSUM_MEASURE` (0x10000002) 无法更新单元，因为不能更新非 sum 度量值 (计数、最小值、最大值、非重复计数、半累加性) 。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-160">`CELL_UPDATE_NOT_ENABLED_NONSUM_MEASURE` (0x10000002)   The cell cannot be updated because non-sum measures (count, min, max, distinct count, semi-additive) can not be updated.</span></span><br /><br /> <span data-ttu-id="a0cf1-161">`CELL_UPDATE_NOT_ENABLED_NACELL_VIRTUALCUBE` (0x10000003) 无法更新该单元，因为该单元不是位于度量值和与该度量值的度量值组无关的维度成员的交集。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-161">`CELL_UPDATE_NOT_ENABLED_NACELL_VIRTUALCUBE` (0x10000003)   The cell cannot be updated because the cell does not exist as it is at the intersection of a measure and a dimension member unrelated to the measure's measure group.</span></span><br /><br /> <span data-ttu-id="a0cf1-162">`CELL_UPDATE_NOT_ENABLED_SECURE`无法更新 0x10000005)  (，因为该单元受保护。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-162">`CELL_UPDATE_NOT_ENABLED_SECURE` (0x10000005)    The cell cannot be updated because the cell is secured.</span></span><br /><br /> <span data-ttu-id="a0cf1-163">`CELL_UPDATE_NOT_ENABLED_CALCLEVEL` (0x10000006) 保留以供将来使用。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-163">`CELL_UPDATE_NOT_ENABLED_CALCLEVEL` (0x10000006)   Reserved for future use.</span></span><br /><br /> <span data-ttu-id="a0cf1-164">`CELL_UPDATE_NOT_ENABLED_CANNOTUPDATE`由于内部原因， (0x10000007) 无法更新单元。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-164">`CELL_UPDATE_NOT_ENABLED_CANNOTUPDATE` (0x10000007)   The cell cannot be updated because of internal reasons.</span></span><br /><br /> <span data-ttu-id="a0cf1-165">`CELL_UPDATE_NOT_ENABLED_INVALIDDIMENSIONTYPE` (0x10000009) 无法更新该单元，因为在挖掘模型、间接或数据挖掘维度中不支持更新。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-165">`CELL_UPDATE_NOT_ENABLED_INVALIDDIMENSIONTYPE` (0x10000009)   The cell cannot be updated because update is not supported in mining model, indirect, or data mining dimensions.</span></span>|  
|`VALUE`|<span data-ttu-id="a0cf1-166">单元的未格式化值。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-166">The unformatted value of the cell.</span></span>|  
  
 <span data-ttu-id="a0cf1-167">只有 `CELL_ORDINAL`、`FORMATTED_VALUE` 和 `VALUE` 单元属性是必需的。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-167">Only the `CELL_ORDINAL`, `FORMATTED_VALUE`, and `VALUE` cell properties are required.</span></span> <span data-ttu-id="a0cf1-168">所有的单元属性（内部单元属性或特定于提供程序的单元属性）都在 `PROPERTIES` 架构行集中进行定义，包括它们的数据类型和提供程序支持。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-168">All cell properties, intrinsic or provider-specific, are defined in the `PROPERTIES` schema rowset, including their data types and provider support.</span></span> <span data-ttu-id="a0cf1-169">有关 `PROPERTIES` 架构行集的详细信息，请参阅[MDSCHEMA_PROPERTIES 行集](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-properties-rowset)。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-169">For more information about the `PROPERTIES` schema rowset, see [MDSCHEMA_PROPERTIES Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-properties-rowset).</span></span>  
  
 <span data-ttu-id="a0cf1-170">默认情况下，如果未使用 `CELL PROPERTIES` 关键字，返回的单元属性为 `VALUE`、`FORMATTED_VALUE` 和 `CELL_ORDINAL`（按这里显示的顺序）。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-170">By default, if the `CELL PROPERTIES` keyword is not used, the cell properties returned are `VALUE`, `FORMATTED_VALUE`, and `CELL_ORDINAL` (in that order).</span></span> <span data-ttu-id="a0cf1-171">如果使用了 `CELL PROPERTIES` 关键字，将只返回用该关键字显式声明的那些单元属性。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-171">If the `CELL PROPERTIES` keyword is used, only those cell properties explicitly stated with the keyword are returned.</span></span>  
  
 <span data-ttu-id="a0cf1-172">下面的示例显示了 `CELL PROPERTIES` 关键字在 MDX 查询中的使用：</span><span class="sxs-lookup"><span data-stu-id="a0cf1-172">The following example demonstrates the use of the `CELL PROPERTIES` keyword in an MDX query:</span></span>  
  
```  
SELECT  
   {[Measures].[Reseller Gross Profit]} ON COLUMNS,  
   {[Reseller].[Reseller Type].[Reseller Name].Members} ON ROWS  
FROM [Adventure Works]  
CELL PROPERTIES VALUE, FORMATTED_VALUE, FORMAT_STRING, FORE_COLOR, BACK_COLOR  
```  
  
 <span data-ttu-id="a0cf1-173">对于返回简化格式的行集的 MDX 查询，不返回单元属性；这种情况下，每个单元表现为似乎只返回了 `FORMATTED_VALUE` 单元属性。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-173">Cell properties are not returned for MDX queries that return flattened rowsets; in this case, each cell is represented as if only the `FORMATTED_VALUE` cell property were returned.</span></span>  
  
## <a name="setting-cell-properties"></a><span data-ttu-id="a0cf1-174">设置单元属性</span><span class="sxs-lookup"><span data-stu-id="a0cf1-174">Setting Cell Properties</span></span>  
 <span data-ttu-id="a0cf1-175">可以在不同位置设置单元属性 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a0cf1-175">Cell properties can be set in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in various places.</span></span> <span data-ttu-id="a0cf1-176">例如，可以在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]的多维数据集编辑器的“多维数据集结构”选项卡上为常规度量值设置格式字符串属性；可以为在多维数据集编辑器的“计算”选项卡上的多维数据集上定义的计算度量值设置相同属性；在查询的 WITH 子句中定义的计算度量值也具有其在此处定义的格式字符串。以下查询演示了如何在计算的度量值上设置单元属性：</span><span class="sxs-lookup"><span data-stu-id="a0cf1-176">For example, the Format String property can be set for regular measures on the Cube Structure tab of the Cube Editor in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]; the same property can be set for calculated measures defined on the cube on the Calculations tab of the Cube Editor; calculated measures defined in the WITH clause of a query have their format string defined there too.The following query demonstrates how cell properties can be set on a calculated measure::</span></span>  
  
```  
WITH MEMBER MEASURES.CELLPROPERTYDEMO AS [Measures].[Internet Sales Amount]  
, FORE_COLOR=RGB(0,0,255)  
, BACK_COLOR=IIF([Measures].[Internet Sales Amount]>7000000, RGB(255,0,0), RGB(0,255,0))  
, FONT_SIZE=10  
, FORMAT_STRING='#,#.000'  
SELECT MEASURES.CELLPROPERTYDEMO ON 0,  
[Date].[Calendar Year].[Calendar Year].MEMBERS ON 1  
FROM [Adventure Works]  
CELL PROPERTIES VALUE, FORMATTED_VALUE, FORE_COLOR, BACK_COLOR, FONT_SIZE  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0cf1-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a0cf1-177">See Also</span></span>  
 [<span data-ttu-id="a0cf1-178">MDX 查询基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a0cf1-178">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  