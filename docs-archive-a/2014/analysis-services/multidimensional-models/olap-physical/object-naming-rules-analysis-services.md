---
title: 对象命名规则 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], naming
ms.assetid: b338a60d-4802-4b68-862a-6dc6a3f75e48
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6adfd4b23b6fe9129641271fc3c2381e161119ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589289"
---
# <a name="object-naming-rules-analysis-services"></a><span data-ttu-id="10bce-102">对象命名规则 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="10bce-102">Object Naming Rules (Analysis Services)</span></span>
  <span data-ttu-id="10bce-103">本主题介绍对象命名约定，以及无法在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中的任何对象名称、代码或脚本中使用的保留字和字符。</span><span class="sxs-lookup"><span data-stu-id="10bce-103">This topic describes object naming conventions, as well as the reserved words and characters that cannot be used in any object name, in code or script in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
##  <a name="naming-conventions"></a><a name="bkmk_Names"></a><span data-ttu-id="10bce-104">命名约定</span><span class="sxs-lookup"><span data-stu-id="10bce-104">Naming Conventions</span></span>  
 <span data-ttu-id="10bce-105">每个对象都拥有一个 `Name` 和 `ID` 属性，该属性在父集合的范围内必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="10bce-105">Every object has a `Name` and `ID` property that must be unique within the scope of the parent collection.</span></span> <span data-ttu-id="10bce-106">例如，只要两个维度分别驻留在不同的数据库中，这两个维度就能具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="10bce-106">For example, two dimensions can have same name as long as each one resides in a different database.</span></span>  
  
 <span data-ttu-id="10bce-107">虽然可以手动指定 `ID`，但它通常会在创建对象时自动生成。</span><span class="sxs-lookup"><span data-stu-id="10bce-107">Although you can specify it manually, the `ID` is typically auto-generated when the object is created.</span></span> <span data-ttu-id="10bce-108">在开始构建模型之后，您绝不应更改 `ID`。</span><span class="sxs-lookup"><span data-stu-id="10bce-108">You should never change the `ID` once you have begun building a model.</span></span> <span data-ttu-id="10bce-109">模型中的所有对象引用都基于 `ID`，</span><span class="sxs-lookup"><span data-stu-id="10bce-109">All object references throughout a model are based on the `ID`.</span></span> <span data-ttu-id="10bce-110">因此，更改 `ID` 容易导致模型损坏。</span><span class="sxs-lookup"><span data-stu-id="10bce-110">Thus, changing an `ID` can easily result in model corruption.</span></span>  
  
 <span data-ttu-id="10bce-111">`DataSource` 和 `DataSourceView` 对象是命名约定的两个值得注意的例外。</span><span class="sxs-lookup"><span data-stu-id="10bce-111">`DataSource` and `DataSourceView` objects have notable exceptions to naming conventions.</span></span> <span data-ttu-id="10bce-112">`DataSource` ID 可以设置为不具唯一性的一个点 (.)，这表示对当前数据库的引用。</span><span class="sxs-lookup"><span data-stu-id="10bce-112">`DataSource` ID can be set to a single dot (.), which is not unique, as a reference to the current database.</span></span> <span data-ttu-id="10bce-113">另一个例外是 `DataSourceView`，它遵循的是针对 .NET Framework 中的 `DataSet` 对象定义的命名约定（其中的 `Name` 用作标识符）。</span><span class="sxs-lookup"><span data-stu-id="10bce-113">A second exception is `DataSourceView`, which adheres to the naming conventions defined for `DataSet` objects in the .NET Framework, where the `Name` is used as the identifier.</span></span>  
  
 <span data-ttu-id="10bce-114">以下规则适用于 `Name` 和 `ID` 属性。</span><span class="sxs-lookup"><span data-stu-id="10bce-114">The following rules apply to `Name` and `ID` properties.</span></span>  
  
-   <span data-ttu-id="10bce-115">名称不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="10bce-115">Names are case insensitive.</span></span> <span data-ttu-id="10bce-116">在同一数据库中，不能有一个名为 "sales" 的多维数据集和名为 "Sales" 的另一个。</span><span class="sxs-lookup"><span data-stu-id="10bce-116">You cannot have a cube named "sales" and another named "Sales" in the same database.</span></span>  
  
-   <span data-ttu-id="10bce-117">对象名称中不允许使用前导空格或尾随空格，但可以在名称中嵌入空格。</span><span class="sxs-lookup"><span data-stu-id="10bce-117">No leading or trailing spaces allowed in an object name, although you can embed spaces within a name.</span></span> <span data-ttu-id="10bce-118">前导空格和尾随空格将会被隐式删除。</span><span class="sxs-lookup"><span data-stu-id="10bce-118">Leading and trailing spaces are implicitly trimmed.</span></span> <span data-ttu-id="10bce-119">这适用于对象的 `Name` 和 `ID`。</span><span class="sxs-lookup"><span data-stu-id="10bce-119">This applies to both the `Name` and `ID` of an object.</span></span>  
  
-   <span data-ttu-id="10bce-120">最大字符数为 100。</span><span class="sxs-lookup"><span data-stu-id="10bce-120">The maximum number of characters is 100.</span></span>  
  
-   <span data-ttu-id="10bce-121">对标识符的第一个字符没有特殊要求。</span><span class="sxs-lookup"><span data-stu-id="10bce-121">There is no special requirement for the first character of an identifier.</span></span> <span data-ttu-id="10bce-122">第一个字符可为任意有效字符。</span><span class="sxs-lookup"><span data-stu-id="10bce-122">The first character may be any valid character.</span></span>  
  
##  <a name="reserved-words-and-characters"></a><a name="bkmk_reserved"></a><span data-ttu-id="10bce-123">保留字和字符</span><span class="sxs-lookup"><span data-stu-id="10bce-123">Reserved Words and Characters</span></span>  
 <span data-ttu-id="10bce-124">保留字用英语表示，且适用于对象名称而非标题。</span><span class="sxs-lookup"><span data-stu-id="10bce-124">Reserved words are in English, and apply to object names, not Captions.</span></span> <span data-ttu-id="10bce-125">如果您在对象名称中意外使用了保留字，则将发生验证错误。</span><span class="sxs-lookup"><span data-stu-id="10bce-125">If you inadvertently use a reserved word in an object name, a validation error will occur.</span></span> <span data-ttu-id="10bce-126">对于多维和数据挖掘模型，在任何对象名称中任何时候都不能使用下面描述的保留字。</span><span class="sxs-lookup"><span data-stu-id="10bce-126">For multidimensional and data mining models, the reserved words described below cannot be used in any object name, at any time.</span></span>  
  
 <span data-ttu-id="10bce-127">对于表格模型（其中的数据库兼容性设置为 1103），已放宽了针对某些对象、扩展字符的不合规要求和某些客户端应用程序命名约定的验证规则。</span><span class="sxs-lookup"><span data-stu-id="10bce-127">For tabular models, where the database compatibility is set to 1103, validation rules have been relaxed for certain objects, out of compliance for the extended character requirements and naming conventions of certain client applications.</span></span> <span data-ttu-id="10bce-128">满足这些条件的数据库受更放宽的验证规则约束。</span><span class="sxs-lookup"><span data-stu-id="10bce-128">Databases that meet these criteria are subject to less stringent validation rules.</span></span> <span data-ttu-id="10bce-129">在这种情况下，对象名称可以包含受限制的字符且能够通过验证。</span><span class="sxs-lookup"><span data-stu-id="10bce-129">In this case, it's possible for an object name to include a restricted character and still pass validation.</span></span>  
  
 <span data-ttu-id="10bce-130">**保留字**</span><span class="sxs-lookup"><span data-stu-id="10bce-130">**Reserved Words**</span></span>  
  
-   <span data-ttu-id="10bce-131">AUX</span><span class="sxs-lookup"><span data-stu-id="10bce-131">AUX</span></span>  
  
-   <span data-ttu-id="10bce-132">CLOCK$</span><span class="sxs-lookup"><span data-stu-id="10bce-132">CLOCK$</span></span>  
  
-   <span data-ttu-id="10bce-133">COM1 到 COM9（COM1、COM2、COM3 等）</span><span class="sxs-lookup"><span data-stu-id="10bce-133">COM1 through COM9 (COM1, COM2, COM3, and so on)</span></span>  
  
-   <span data-ttu-id="10bce-134">CON</span><span class="sxs-lookup"><span data-stu-id="10bce-134">CON</span></span>  
  
-   <span data-ttu-id="10bce-135">LPT1 到 LPT9（LPT1、LPT2、LPT3 等）</span><span class="sxs-lookup"><span data-stu-id="10bce-135">LPT1 through LPT9 (LPT1, LPT2, LPT3, and so on)</span></span>  
  
-   <span data-ttu-id="10bce-136">NUL</span><span class="sxs-lookup"><span data-stu-id="10bce-136">NUL</span></span>  
  
-   <span data-ttu-id="10bce-137">PRN</span><span class="sxs-lookup"><span data-stu-id="10bce-137">PRN</span></span>  
  
-   <span data-ttu-id="10bce-138">XML 内的任何字符串的字符都不可为 NULL</span><span class="sxs-lookup"><span data-stu-id="10bce-138">NULL is not allowed as a character in any string within the XML</span></span>  
  
 <span data-ttu-id="10bce-139">**保留字符**</span><span class="sxs-lookup"><span data-stu-id="10bce-139">**Reserved Characters**</span></span>  
  
 <span data-ttu-id="10bce-140">下表列出了特定对象的无效字符。</span><span class="sxs-lookup"><span data-stu-id="10bce-140">The following table lists invalid characters for specific objects.</span></span>  
  
|<span data-ttu-id="10bce-141">对象</span><span class="sxs-lookup"><span data-stu-id="10bce-141">Object</span></span>|<span data-ttu-id="10bce-142">无效字符</span><span class="sxs-lookup"><span data-stu-id="10bce-142">Invalid characters</span></span>|  
|------------|------------------------|  
|`Server`|<span data-ttu-id="10bce-143">在对服务器对象进行命名时，请遵循 Windows 服务器命名约定。</span><span class="sxs-lookup"><span data-stu-id="10bce-143">Follow Windows server naming conventions when naming a server object.</span></span> <span data-ttu-id="10bce-144">有关详细信息，请参阅[命名约定 (Windows) ](/windows/desktop/DNS/naming-conventions) 。</span><span class="sxs-lookup"><span data-stu-id="10bce-144">See [Naming Conventions (Windows)](/windows/desktop/DNS/naming-conventions) for details.</span></span>|  
|`DataSource`| `: / \ * \| ? " () [] {} <>` |  
|<span data-ttu-id="10bce-145">`Level` 或 `Attribute`</span><span class="sxs-lookup"><span data-stu-id="10bce-145">`Level` or `Attribute`</span></span>|````. , ; ' ` : / \ * & \| ? " & % $ ! + = [] {} < >````|  
|<span data-ttu-id="10bce-146">`Dimension` 或 `Hierarchy`</span><span class="sxs-lookup"><span data-stu-id="10bce-146">`Dimension` or `Hierarchy`</span></span>|````. , ; ' ` : / \ * \| ? " & % $ ! + = () [] {} <,>````|  
|<span data-ttu-id="10bce-147">所有其他对象</span><span class="sxs-lookup"><span data-stu-id="10bce-147">All other objects</span></span>|````. , ; ' ` : / \ * \| ? " & % $ ! + = () [] {} < >````|  
  
 <span data-ttu-id="10bce-148">**例外：允许保留字符的情况**</span><span class="sxs-lookup"><span data-stu-id="10bce-148">**Exceptions: When Reserved Characters are Allowed**</span></span>  
  
 <span data-ttu-id="10bce-149">如前所述，特定模式和兼容级别的数据库可以具有包含保留字符的对象名称。</span><span class="sxs-lookup"><span data-stu-id="10bce-149">As noted, databases of a specific modality and compatibility level can have object names that include reserved characters.</span></span> <span data-ttu-id="10bce-150">对于允许使用扩展字符的表格数据库（1103 或更高），维度属性、层次结构、级别、度量值和 KPI 对象名称可以包含保留字符：</span><span class="sxs-lookup"><span data-stu-id="10bce-150">Dimension attribute, hierarchy, level, measure and KPI object names can include reserved characters, for tabular databases (1103 or higher) that allow the use of extended characters:</span></span>  
  
|<span data-ttu-id="10bce-151">服务器模式和数据库兼容级别</span><span class="sxs-lookup"><span data-stu-id="10bce-151">Server mode and database compatibility level</span></span>|<span data-ttu-id="10bce-152">是否允许保留字符？</span><span class="sxs-lookup"><span data-stu-id="10bce-152">Reserved characters allowed?</span></span>|  
|--------------------------------------------------|----------------------------------|  
|<span data-ttu-id="10bce-153">MOLAP（所有版本）</span><span class="sxs-lookup"><span data-stu-id="10bce-153">MOLAP (all versions)</span></span>|<span data-ttu-id="10bce-154">否</span><span class="sxs-lookup"><span data-stu-id="10bce-154">No</span></span>|  
|<span data-ttu-id="10bce-155">表格 - 1050</span><span class="sxs-lookup"><span data-stu-id="10bce-155">Tabular - 1050</span></span>|<span data-ttu-id="10bce-156">否</span><span class="sxs-lookup"><span data-stu-id="10bce-156">No</span></span>|  
|<span data-ttu-id="10bce-157">表格 - 1100</span><span class="sxs-lookup"><span data-stu-id="10bce-157">Tabular - 1100</span></span>|<span data-ttu-id="10bce-158">否</span><span class="sxs-lookup"><span data-stu-id="10bce-158">No</span></span>|  
|<span data-ttu-id="10bce-159">表格-1130 和更高版本</span><span class="sxs-lookup"><span data-stu-id="10bce-159">Tabular - 1130 and higher</span></span>|<span data-ttu-id="10bce-160">是</span><span class="sxs-lookup"><span data-stu-id="10bce-160">Yes</span></span>|  
  
 <span data-ttu-id="10bce-161">数据库可以拥有默认的 ModelType。</span><span class="sxs-lookup"><span data-stu-id="10bce-161">Databases can have a ModelType of default.</span></span> <span data-ttu-id="10bce-162">默认值等效于多维的，因此不支持在列名称中使用保留字符。</span><span class="sxs-lookup"><span data-stu-id="10bce-162">Default is equivalent to multidimensional, and thus does not support the use of reserved characters in column names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10bce-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10bce-163">See Also</span></span>  
 <span data-ttu-id="10bce-164">[MDX 保留字](/sql/mdx/mdx-reserved-words) </span><span class="sxs-lookup"><span data-stu-id="10bce-164">[MDX Reserved Words](/sql/mdx/mdx-reserved-words) </span></span>  
 <span data-ttu-id="10bce-165">[翻译 &#40;Analysis Services&#41;](/analysis-services/translation-support-in-analysis-services) </span><span class="sxs-lookup"><span data-stu-id="10bce-165">[Translations &#40;Analysis Services&#41;](/analysis-services/translation-support-in-analysis-services) </span></span>  
 [<span data-ttu-id="10bce-166">XML for Analysis 符合性 &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="10bce-166">XML for Analysis Compliance &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-compliance-xmla)  
  
  
