---
title: DirectQuery 模式下的 DAX 公式兼容性 (SSAS 2014) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: de83cfa9-9ffe-4e24-9c74-96a3876cb4bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: acaac82d6930787a45281c0e942def8df764f4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581012"
---
# <a name="dax-formula-compatibility-in-directquery-mode-ssas-2014"></a><span data-ttu-id="02f87-102">DirectQuery 模式下的 DAX 公式兼容性 (SSAS 2014)</span><span class="sxs-lookup"><span data-stu-id="02f87-102">DAX Formula Compatibility in DirectQuery Mode (SSAS 2014)</span></span>
<span data-ttu-id="02f87-103">可以使用数据分析表达式语言 (DAX) 来创建度量值和其他自定义公式，以便在 Analysis Services 表格模型、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] Excel 工作簿中的数据模型和 Power BI Desktop 数据模型中使用。</span><span class="sxs-lookup"><span data-stu-id="02f87-103">The Data Analysis Expression language (DAX) can be used to create measures and other custom formulas for use in Analysis Services Tabular models, [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] data models in Excel workbooks, and Power BI Desktop data models.</span></span> <span data-ttu-id="02f87-104">在大多数情况下，你在这些环境中创建的模型是相同的，你可以使用相同的度量值、关系和 Kpi 等。但是，如果您创作 Analysis Services 表格模型并在 DirectQuery 模式下部署该模型，则可以使用的公式有一些限制。</span><span class="sxs-lookup"><span data-stu-id="02f87-104">In most respects, the models you create in these environments are identical, and you can use the same measures, relationships, and KPIs, etc. However, if you author an Analysis Services Tabular model and deploy it in DirectQuery mode, there are some restrictions on the formulas that you can use.</span></span> <span data-ttu-id="02f87-105">本主题概述了这些差异，并列出了在兼容级别1100或1103与 DirectQuery 模式下 SQL Server 2014 Analysis Services tabulars 模型不支持的函数，并列出了支持但可能返回不同结果的函数。</span><span class="sxs-lookup"><span data-stu-id="02f87-105">This topic provides an overview of those differences, lists the functions that are not supported in SQL Server 2014 Analysis Services tabulars model at compatibility level 1100 or 1103 and in DirectQuery mode, and lists the functions that are supported but might return different results.</span></span>  
  
<span data-ttu-id="02f87-106">在本主题中，我们使用术语 "*内存中模型*" 指的是表格模型，它是在表格模式下运行的 Analysis Services 服务器上完全托管的内存中缓存数据。</span><span class="sxs-lookup"><span data-stu-id="02f87-106">Within this topic, we use the term *in-memory model* to refer to  Tabular models, which are fully hosted in-memory cached data on an Analysis Services server running in Tabular mode.</span></span> <span data-ttu-id="02f87-107">使用*directquery 模型*引用在 DirectQuery 模式下编写和/或部署的表格模型。</span><span class="sxs-lookup"><span data-stu-id="02f87-107">We use *DirectQuery models* to refer to Tabular models that have been authored and/or deployed in DirectQuery mode.</span></span> <span data-ttu-id="02f87-108">有关 DirectQuery 模式的信息，请参阅[Directquery 模式 (SSAS 表格) ](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5)。</span><span class="sxs-lookup"><span data-stu-id="02f87-108">For information about DirectQuery mode, see [DirectQuery Mode (SSAS Tabular)](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5).</span></span>  
  
  
## <a name="differences-between-in-memory-and-directquery-mode"></a><a name="bkmk_SemanticDifferences"></a><span data-ttu-id="02f87-109">内存中模式和 DirectQuery 模式之间的差异</span><span class="sxs-lookup"><span data-stu-id="02f87-109">Differences between in-memory and DirectQuery mode</span></span>  
<span data-ttu-id="02f87-110">与内存中模式下部署的模型相比，DirectQuery 模式下部署的相同模型在查询时可能返回不同的结果。</span><span class="sxs-lookup"><span data-stu-id="02f87-110">Queries on a model deployed in DirectQuery mode can return different results than the same model deployed in in-memory mode.</span></span> <span data-ttu-id="02f87-111">这是因为使用 DirectQuery 时，将直接从关系数据存储中查询数据，并使用相关的关系引擎来执行公式所需的聚合，而不是使用 xVelocity 内存中分析引擎 (VertiPaq) 进行存储和计算。</span><span class="sxs-lookup"><span data-stu-id="02f87-111">This is because with DirectQuery, data is queried directly from a relational data store and aggregations required by formulas are performed using the relevant relational engine, rather than using the xVelocity in-memory analytics engine (VertiPaq) for storage and calculation.</span></span>  
  
<span data-ttu-id="02f87-112">例如，某些关系数据存储区在处理数值、日期、Null 等的方式上就存在差异。</span><span class="sxs-lookup"><span data-stu-id="02f87-112">For example, there are differences in the way that certain relational data stores handle numeric values, dates, nulls, and so forth.</span></span>  
  
<span data-ttu-id="02f87-113">相比之下，DAX 语言旨在尽可能接近地模拟 Microsoft Excel 中函数的行为。</span><span class="sxs-lookup"><span data-stu-id="02f87-113">In contrast, the DAX language is intended to emulate as closely as possible the behavior of functions in Microsoft Excel.</span></span> <span data-ttu-id="02f87-114">例如，在处理 Null、空字符串和零值时，Excel 尝试提供最佳响应，而不考虑精确的数据类型，因此 xVelocity 引擎执行同样的处理。</span><span class="sxs-lookup"><span data-stu-id="02f87-114">For example, when handling nulls, empty strings and zero values, Excel attempts to provide the best answer regardless of the precise data type, and therefore the xVelocity engine does the same.</span></span> <span data-ttu-id="02f87-115">然而，当表格模型在 DirectQuery 模式下部署并将公式传递到关系数据源进行计算时，必须根据关系数据源的语义处理数据，这通常要求以截然不同的方式处理空字符串与 null。</span><span class="sxs-lookup"><span data-stu-id="02f87-115">However, when a tabular model is deployed in DirectQuery mode and passes formulas to a relational data source for evaluation, the data must be handled according to the semantics of the relational data source, which typically require distinct handling of empty strings vs. nulls.</span></span> <span data-ttu-id="02f87-116">因此，当针对缓存的数据和针对只从关系存储中返回的数据进行计算时，同一个公式可能返回不同的结果。</span><span class="sxs-lookup"><span data-stu-id="02f87-116">For this reason, the same formula might return a different result when evaluated against cached data and against data returned solely from the relational store.</span></span>  
  
<span data-ttu-id="02f87-117">此外，某些函数不能在 DirectQuery 模式下使用，因为计算需要将当前上下文中的数据作为参数发送到关系数据源。</span><span class="sxs-lookup"><span data-stu-id="02f87-117">Additionally, some functions cannot be used at all in DirectQuery mode because the calculation would require the data in the current context be sent to the relational data source as a parameter.</span></span> <span data-ttu-id="02f87-118">例如，工作簿中的度量值 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 通常使用时间智能函数，这些函数引用工作簿中提供的日期范围。</span><span class="sxs-lookup"><span data-stu-id="02f87-118">For example, measures in a [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] workbook often use time-intelligence functions that reference date ranges available within the workbook.</span></span> <span data-ttu-id="02f87-119">在 DirectQuery 模式下，一般不能使用此类公式。</span><span class="sxs-lookup"><span data-stu-id="02f87-119">Such formulas generally cannot be used in DirectQuery mode.</span></span>  
  
## <a name="semantic-differences"></a><span data-ttu-id="02f87-120">语义差异</span><span class="sxs-lookup"><span data-stu-id="02f87-120">Semantic differences</span></span>  
<span data-ttu-id="02f87-121">本节列出您可以预期的语义差异类型，并介绍可能适用于函数使用或查询结果的任何限制。</span><span class="sxs-lookup"><span data-stu-id="02f87-121">This section lists the types of semantic differences that you can expect, and describes any limitations that might apply to the usage of functions or to query results.</span></span>  
  
### <a name="comparisons"></a><a name="bkmk_Comparisons"></a><span data-ttu-id="02f87-122">比较</span><span class="sxs-lookup"><span data-stu-id="02f87-122">Comparisons</span></span>  
<span data-ttu-id="02f87-123">内存中模型中的 DAX 支持对两个解析为不同数据类型的标量值的表达式进行比较。</span><span class="sxs-lookup"><span data-stu-id="02f87-123">DAX in in-memory models support comparisons of two expressions that resolve to scalar values of different data types.</span></span> <span data-ttu-id="02f87-124">但是，在 DirectQuery 模式下部署的模型使用关系引擎的数据类型和比较运算符，因此可能返回不同的结果。</span><span class="sxs-lookup"><span data-stu-id="02f87-124">However, models that are deployed in DirectQuery mode use the data types and comparison operators of the relational engine, and therefore might return different results.</span></span>  
  
<span data-ttu-id="02f87-125">当在针对 DirectQuery 数据源的计算中使用以下比较时，将始终返回错误：</span><span class="sxs-lookup"><span data-stu-id="02f87-125">The following comparisons will always return an error when used in a calculation on a DirectQuery data source:</span></span>  
  
-   <span data-ttu-id="02f87-126">数值数据类型与任何字符串数据类型相比较</span><span class="sxs-lookup"><span data-stu-id="02f87-126">Numeric data type compared to any string data type</span></span>  
  
-   <span data-ttu-id="02f87-127">数值数据类型与布尔值相比较</span><span class="sxs-lookup"><span data-stu-id="02f87-127">Numeric data type compared to a Boolean value</span></span>  
  
-   <span data-ttu-id="02f87-128">任何字符串数据类型与布尔值相比较</span><span class="sxs-lookup"><span data-stu-id="02f87-128">Any string data type compared to a Boolean value</span></span>  
  
<span data-ttu-id="02f87-129">通常，DAX 在内存中模型内更能容忍数据类型不匹配，并最多尝试两次对值进行隐式转换，如本节中所述。</span><span class="sxs-lookup"><span data-stu-id="02f87-129">In general, DAX is more forgiving of data type mismatches in in-memory models and will attempt an implicit cast of values up to two times, as described in this section.</span></span> <span data-ttu-id="02f87-130">但是，将根据关系引擎的规则，对在 DirectQuery 模式下发送到关系数据存储区的公式进行计算，且这些公式失败的可能性更高。</span><span class="sxs-lookup"><span data-stu-id="02f87-130">However, formulas sent to a relational data store in DirectQuery mode are evaluated more strictly, following the rules of the relational engine, and are more likely to fail.</span></span>  
  
<span data-ttu-id="02f87-131">**字符串和数字的比较**</span><span class="sxs-lookup"><span data-stu-id="02f87-131">**Comparisons of strings and numbers**</span></span>  
<span data-ttu-id="02f87-132">示例： `"2" < 3`</span><span class="sxs-lookup"><span data-stu-id="02f87-132">EXAMPLE: `"2" < 3`</span></span>  
  
<span data-ttu-id="02f87-133">此公式比较文本字符串与数字。</span><span class="sxs-lookup"><span data-stu-id="02f87-133">The formula compares a text string to a number.</span></span> <span data-ttu-id="02f87-134">对于 DirectQuery 模式和内存中模型，此表达式均为 **true** 。</span><span class="sxs-lookup"><span data-stu-id="02f87-134">The expression is **true** in both DirectQuery mode and in-memory models.</span></span>  
  
<span data-ttu-id="02f87-135">在内存中模型中，结果为 **true** ，因为作为字符串的数字将隐式转换为数值数据类型，以便与其他数字进行比较。</span><span class="sxs-lookup"><span data-stu-id="02f87-135">In an in-memory model, the result is **true** because numbers as strings are implicitly cast to a numerical data type for comparisons with other numbers.</span></span> <span data-ttu-id="02f87-136">SQL 还隐式将作为比较所用数字的文本数字转换为数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="02f87-136">SQL also implicitly casts text numbers as numbers for comparison to numerical data types.</span></span>  
  
<span data-ttu-id="02f87-137">请注意，这表示的第一个版本中的行为发生了变化 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ，这会返回**false**，因为文本 "2" 始终被视为大于任何数字。</span><span class="sxs-lookup"><span data-stu-id="02f87-137">Note that this represents a change in behavior from the first version of [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], which would return **false**, because the text "2" would always be considered larger than any number.</span></span>  
  
<span data-ttu-id="02f87-138">**文本与布尔值的比较**</span><span class="sxs-lookup"><span data-stu-id="02f87-138">**Comparison of text with Boolean**</span></span>  
<span data-ttu-id="02f87-139">示例： `"VERDADERO" = TRUE`</span><span class="sxs-lookup"><span data-stu-id="02f87-139">EXAMPLE: `"VERDADERO" = TRUE`</span></span>  
  
<span data-ttu-id="02f87-140">此表达式比较文本字符串与布尔值。</span><span class="sxs-lookup"><span data-stu-id="02f87-140">This expression compares a text string with a Boolean value.</span></span> <span data-ttu-id="02f87-141">通常，对于 DirectQuery 或内存中模型，将字符串值与布尔值进行比较将导致错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-141">In general, for DirectQuery or In-Memory models, comparing a string value to a Boolean value results in an error.</span></span> <span data-ttu-id="02f87-142">此规则的唯一例外是当字符串包含字词 **true** 或 **false**时；如果字符串包含 true 或 false 值之一，则将执行到布尔值的转换，此时将发生比较，并给出逻辑结果。</span><span class="sxs-lookup"><span data-stu-id="02f87-142">The only exceptions to the rule are when the string contains the word **true** or the word **false**; if the string contains any of true or false values, a conversion to Boolean is made and the comparison takes place giving the logical result.</span></span>  
  
<span data-ttu-id="02f87-143">**Null 值的比较**</span><span class="sxs-lookup"><span data-stu-id="02f87-143">**Comparison of nulls**</span></span>  
<span data-ttu-id="02f87-144">示例： `EVALUATE ROW("X", BLANK() = BLANK())`</span><span class="sxs-lookup"><span data-stu-id="02f87-144">EXAMPLE: `EVALUATE ROW("X", BLANK() = BLANK())`</span></span>  
  
<span data-ttu-id="02f87-145">此公式比较 null 的 SQL 等效值与 null。</span><span class="sxs-lookup"><span data-stu-id="02f87-145">This formula compares the SQL equivalent of a null to a null.</span></span> <span data-ttu-id="02f87-146">它在内存中模型和 DirectQuery 模型中返回 **true** ；在 DirectQuery 模型中进行了预配，以保证与内存中模型相似的行为。</span><span class="sxs-lookup"><span data-stu-id="02f87-146">It returns **true** in in-memory and DirectQuery models; a provision is made in DirectQuery model to guarantee similar behavior to in-memory model.</span></span>  
  
<span data-ttu-id="02f87-147">请注意，在 Transact-SQL 中，null 值始终不等于 null。</span><span class="sxs-lookup"><span data-stu-id="02f87-147">Note that in Transact-SQL, a null is never equal to a null.</span></span> <span data-ttu-id="02f87-148">但在 DAX 中，空白等于另一个空白。</span><span class="sxs-lookup"><span data-stu-id="02f87-148">However, in DAX, a blank is equal to another blank.</span></span> <span data-ttu-id="02f87-149">这种行为对于所有内存中模型都是相同的。</span><span class="sxs-lookup"><span data-stu-id="02f87-149">This behavior is the same for all in-memory models.</span></span> <span data-ttu-id="02f87-150">务必注意，DirectQuery 模式使用大多数的 SQL Server 语义；但在此情况下，它对于 NULL 比较给出不同的新行为。</span><span class="sxs-lookup"><span data-stu-id="02f87-150">It is important to note that DirectQuery mode uses, most of, the semantics of SQL Server; but, in this case it separates from it giving a new behavior to NULL comparisons.</span></span>  
  
### <a name="casts"></a><a name="bkmk_Casts"></a><span data-ttu-id="02f87-151">强制</span><span class="sxs-lookup"><span data-stu-id="02f87-151">Casts</span></span>  
  
<span data-ttu-id="02f87-152">在 DAX 中没有此类转换函数，但在许多比较和算术运算中会执行隐式转换。</span><span class="sxs-lookup"><span data-stu-id="02f87-152">There is no cast function as such in DAX, but implicit casts are performed in many comparison and arithmetic operations.</span></span> <span data-ttu-id="02f87-153">它是确定结果的数据类型的比较或算术运算。</span><span class="sxs-lookup"><span data-stu-id="02f87-153">It is the comparison or arithmetic operation that determines the data type of the result.</span></span> <span data-ttu-id="02f87-154">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="02f87-154">For example,</span></span>  
  
-   <span data-ttu-id="02f87-155">布尔值在算术运算中被当作数值（如 TRUE + 1 或应用于布尔值列的函数 MIN）。</span><span class="sxs-lookup"><span data-stu-id="02f87-155">Boolean values are treated as numeric in arithmetic operations, such as TRUE + 1, or the function MIN applied to a column of Boolean values.</span></span> <span data-ttu-id="02f87-156">NOT 运算也返回一个数值。</span><span class="sxs-lookup"><span data-stu-id="02f87-156">A NOT operation also returns a numeric value.</span></span>  
  
-   <span data-ttu-id="02f87-157">在比较中以及在与 EXACT、AND、OR、 &amp;&amp;或 || 结合使用时，布尔值始终被当作逻辑值。</span><span class="sxs-lookup"><span data-stu-id="02f87-157">Boolean values are always treated as logical values in comparisons and when used with EXACT, AND, OR, &amp;&amp;, or ||.</span></span>  
  
<span data-ttu-id="02f87-158">**从字符串转换为布尔值**</span><span class="sxs-lookup"><span data-stu-id="02f87-158">**Cast from string to Boolean**</span></span>  
<span data-ttu-id="02f87-159">在内存中和 DirectQuery 模型中，只允许强制转换为以下字符串中的布尔值： " **"** (空字符串) 、 **"true"**、 **"false"**;，其中空字符串转换为 false 值。</span><span class="sxs-lookup"><span data-stu-id="02f87-159">In in-memory and DirectQuery models, casts are permitted to Boolean values from these strings only: **""** (empty string), **"true"**, **"false"**; where an empty string casts to false value.</span></span>  
  
<span data-ttu-id="02f87-160">将任何其他字符串转换为布尔数据类型会导致错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-160">Casts to the Boolean data type of any other string results in an error.</span></span>  
  
<span data-ttu-id="02f87-161">**从字符串转换为日期/时间**</span><span class="sxs-lookup"><span data-stu-id="02f87-161">**Cast from string to date/time**</span></span>  
<span data-ttu-id="02f87-162">在 DirectQuery 模式中，从日期和时间的字符串表示形式转换为实际的 **datetime** 值的行为与在 SQL Server 中相同。</span><span class="sxs-lookup"><span data-stu-id="02f87-162">In DirectQuery mode, casts from string representations of dates and times to actual **datetime** values behave the same way as they do in SQL Server.</span></span>  
  
<span data-ttu-id="02f87-163">有关在模型中控制从 string 到**datetime**数据类型的强制转换规则的信息 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ，请参阅[DAX 语法参考](/dax/dax-syntax-reference)。</span><span class="sxs-lookup"><span data-stu-id="02f87-163">For information about the rules governing casts from string to **datetime** data types in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] models, see the [DAX Syntax Reference](/dax/dax-syntax-reference).</span></span>
  
<span data-ttu-id="02f87-164">使用内存中数据存储区的模型所支持的日期文本格式范围比 SQL Server 支持的日期字符串格式的范围更加有限。</span><span class="sxs-lookup"><span data-stu-id="02f87-164">Models that use the in-memory data store support a more limited range of text formats for dates than the string formats for dates that are supported by SQL Server.</span></span> <span data-ttu-id="02f87-165">然而，DAX 支持自定义日期和时间格式。</span><span class="sxs-lookup"><span data-stu-id="02f87-165">However, DAX supports custom date and time formats.</span></span>  
  
<span data-ttu-id="02f87-166">**从字符串转换为非布尔值的其他类型**</span><span class="sxs-lookup"><span data-stu-id="02f87-166">**Cast from string to other non Boolean values**</span></span>  
<span data-ttu-id="02f87-167">当从字符串转换为非布尔值时，DirectQuery 模式的行为与 SQL Server 相同。</span><span class="sxs-lookup"><span data-stu-id="02f87-167">When casting from strings to non-Boolean values, DirectQuery mode behaves the same as SQL Server.</span></span> <span data-ttu-id="02f87-168">有关详细信息，请参阅 [CAST 和 CONVERT (Transact-SQL)](https://msdn.microsoft.com/a87d0850-c670-4720-9ad5-6f5a22343ea8)。</span><span class="sxs-lookup"><span data-stu-id="02f87-168">For more information, see [CAST and CONVERT (Transact-SQL)](https://msdn.microsoft.com/a87d0850-c670-4720-9ad5-6f5a22343ea8).</span></span>  
  
<span data-ttu-id="02f87-169">**不允许从数字转换为字符串**</span><span class="sxs-lookup"><span data-stu-id="02f87-169">**Cast from numbers to string not allowed**</span></span>  
<span data-ttu-id="02f87-170">示例： `CONCATENATE(102,",345")`</span><span class="sxs-lookup"><span data-stu-id="02f87-170">EXAMPLE: `CONCATENATE(102,",345")`</span></span>  
  
<span data-ttu-id="02f87-171">在 SQL Server 中，不允许从数字转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="02f87-171">Casting from numbers to strings is not allowed in SQL Server.</span></span>  
  
<span data-ttu-id="02f87-172">此公式在表格模型和 DirectQuery 模式下返回一个错误；然而，此公式在 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]中将生成一个结果。</span><span class="sxs-lookup"><span data-stu-id="02f87-172">This formula returns an error in tabular models and in DirectQuery mode; however, the formula produces a result in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)].</span></span>  
  
<span data-ttu-id="02f87-173">**在 DirectQuery 中不支持两次尝试转换**</span><span class="sxs-lookup"><span data-stu-id="02f87-173">**No support for two-try casts in DirectQuery**</span></span>  
<span data-ttu-id="02f87-174">当第一次转换失败时，内存中模型常常尝试第二次转换。</span><span class="sxs-lookup"><span data-stu-id="02f87-174">In-memory models often attempt a second cast when the first one fails.</span></span> <span data-ttu-id="02f87-175">这在 DirectQuery 模式下绝不会发生。</span><span class="sxs-lookup"><span data-stu-id="02f87-175">This never happens in DirectQuery mode.</span></span>  
  
<span data-ttu-id="02f87-176">示例： `TODAY() + "13:14:15"`</span><span class="sxs-lookup"><span data-stu-id="02f87-176">EXAMPLE: `TODAY() + "13:14:15"`</span></span>  
  
<span data-ttu-id="02f87-177">在此表达式中，第一个参数具有类型 **datetime** ；第二个参数具有类型 **string**。</span><span class="sxs-lookup"><span data-stu-id="02f87-177">In this expression, the first parameter has type **datetime** and second parameter has type **string**.</span></span> <span data-ttu-id="02f87-178">但是，将以不同方式处理组合操作数时的转换。</span><span class="sxs-lookup"><span data-stu-id="02f87-178">However, the casts when combining the operands are handled differently.</span></span> <span data-ttu-id="02f87-179">DAX 将执行从 **string** 到 **double**的隐式转换。</span><span class="sxs-lookup"><span data-stu-id="02f87-179">DAX will perform an implicit cast from **string** to **double**.</span></span> <span data-ttu-id="02f87-180">在内存中模型内，公式引擎尝试直接转换为 **double**；如果失败，它将尝试将字符串转换为 **datetime**。</span><span class="sxs-lookup"><span data-stu-id="02f87-180">In in-memory models, the formula engine attempts to cast directly to **double**, and if that fails, it will try to cast the string to **datetime**.</span></span>  
  
<span data-ttu-id="02f87-181">在 DirectQuery 模式下，只适用从 **string** 到 **double** 的直接转换。</span><span class="sxs-lookup"><span data-stu-id="02f87-181">In DirectQuery mode, only the direct cast from **string** to **double** will be applied.</span></span> <span data-ttu-id="02f87-182">如果此转换失败，公式将返回错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-182">If this cast fails, the formula will return an error.</span></span>  
  
### <a name="math-functions-and-arithmetic-operations"></a><a name="bkmk_Math"></a><span data-ttu-id="02f87-183">数学函数和算术运算</span><span class="sxs-lookup"><span data-stu-id="02f87-183">Math functions and arithmetic operations</span></span>  
<span data-ttu-id="02f87-184">在 DirectQuery 模式下，某些数学函数将返回不同的结果，因为基础数据类型或可应用于运算中的转换存在差异。</span><span class="sxs-lookup"><span data-stu-id="02f87-184">Some mathematical functions will return different results in DirectQuery mode because of differences in the underlying data type or the casts that can be applied in operations.</span></span> <span data-ttu-id="02f87-185">此外，上面介绍的有关允许的值范围的限制可能影响算术运算的结果。</span><span class="sxs-lookup"><span data-stu-id="02f87-185">Also, the restrictions described above on the allowed range of values might affect the outcome of arithmetic operations.</span></span>  
  
<span data-ttu-id="02f87-186">**添加顺序**</span><span class="sxs-lookup"><span data-stu-id="02f87-186">**Order of addition**</span></span>  
<span data-ttu-id="02f87-187">当您创建一个添加一系列数字的公式时，内存中模型可能以不同于 DirectQuery 模型的顺序处理这些数字。</span><span class="sxs-lookup"><span data-stu-id="02f87-187">When you create a formula that adds a series of numbers, an in-memory model might process the numbers in a different order than a DirectQuery model.</span></span>  <span data-ttu-id="02f87-188">因此，当您具有许多非常大的正数和非常大的负数时，您可能在一个运算中获得错误，而导致另一个运算。</span><span class="sxs-lookup"><span data-stu-id="02f87-188">Therefore, when you have many very large positive numbers and very large negative numbers, you may get an error in one operation and results in another operation.</span></span>  
  
<span data-ttu-id="02f87-189">**使用 POWER 函数**</span><span class="sxs-lookup"><span data-stu-id="02f87-189">**Use of the POWER function**</span></span>  
<span data-ttu-id="02f87-190">示例： `POWER(-64, 1/3)`</span><span class="sxs-lookup"><span data-stu-id="02f87-190">EXAMPLE: `POWER(-64, 1/3)`</span></span>  
  
<span data-ttu-id="02f87-191">在 DirectQuery 模式下，当求小数指数的值时，POWER 函数无法使用负数作为底数。</span><span class="sxs-lookup"><span data-stu-id="02f87-191">In DirectQuery mode, the POWER function cannot use negative values as the base when raised to a fractional exponent.</span></span> <span data-ttu-id="02f87-192">这在 SQL Server 中是预期行为。</span><span class="sxs-lookup"><span data-stu-id="02f87-192">This is the expected behavior in SQL Server.</span></span>  
  
<span data-ttu-id="02f87-193">在内存中模型内，该公式返回 -4。</span><span class="sxs-lookup"><span data-stu-id="02f87-193">In an in-memory model, the formula returns -4.</span></span>  
  
<span data-ttu-id="02f87-194">**数值溢出运算**</span><span class="sxs-lookup"><span data-stu-id="02f87-194">**Numerical overflow operations**</span></span>  
<span data-ttu-id="02f87-195">在 Transact-SQL 中，导致数值溢出的运算会返回溢出错误；因此，导致溢出的公式也会在 DirectQuery 模式中引发错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-195">In Transact-SQL, operations that result in a numerical overflow return an overflow error; therefore, formulas that result in an overflow also raise an error in DirectQuery mode.</span></span>  
  
<span data-ttu-id="02f87-196">但是，同一公式在内存中模型内使用时会返回一个 8 字节整数。</span><span class="sxs-lookup"><span data-stu-id="02f87-196">However, the same formula when used in an in-memory model returns an eight-byte integer.</span></span> <span data-ttu-id="02f87-197">这是因为公式引擎不检查是否出现了数值溢出。</span><span class="sxs-lookup"><span data-stu-id="02f87-197">That is because the formula engine does not perform checks for numerical overflows.</span></span>  
  
<span data-ttu-id="02f87-198">**具有空白的 LOG 函数返回不同的结果**</span><span class="sxs-lookup"><span data-stu-id="02f87-198">**LOG functions with blanks return different results**</span></span>  
<span data-ttu-id="02f87-199">SQL Server 处理 Null 值和空白的方式与 xVelocity 引擎不同。</span><span class="sxs-lookup"><span data-stu-id="02f87-199">SQL Server handles nulls and blanks differently than the xVelocity engine.</span></span> <span data-ttu-id="02f87-200">因此，以下公式在 DirectQuery 模式下返回错误，但在内存中模式下返回无穷 ( inf) 。</span><span class="sxs-lookup"><span data-stu-id="02f87-200">As a result, the following formula returns an error in DirectQuery mode, but return infinity (-inf) in in-memory mode.</span></span>  
  
`EXAMPLE: LOG(blank())`  
  
<span data-ttu-id="02f87-201">同样的限制应用于其他对数函数：LOG10 和 LN。</span><span class="sxs-lookup"><span data-stu-id="02f87-201">The same limitations apply to the other logarithmic functions: LOG10 and LN.</span></span>  
  
<span data-ttu-id="02f87-202">有关 DAX 中的 **blank** 数据类型的详细信息，请参阅 [DAX 语法参考](/dax/dax-syntax-reference)。</span><span class="sxs-lookup"><span data-stu-id="02f87-202">For more information about the **blank** data type in DAX, see [DAX Syntax Reference](/dax/dax-syntax-reference).</span></span>
  
<span data-ttu-id="02f87-203">**被零除和除以空白**</span><span class="sxs-lookup"><span data-stu-id="02f87-203">**Division by 0 and division by Blank**</span></span>  
<span data-ttu-id="02f87-204">在 DirectQuery 模式下，被零 (0) 除和除以空白将始终导致错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-204">In DirectQuery mode, division by zero (0) or division by BLANK will always result in an error.</span></span> <span data-ttu-id="02f87-205">SQL Server 不支持无穷大的概念，并且因为任何被零除的自然结果都是无穷大，所以，结果是一个错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-205">SQL Server does not support the notion of infinity, and because the natural result of any division by 0 is infinity, the result is an error.</span></span> <span data-ttu-id="02f87-206">但是，SQL Server 支持除以 Null 值，其结果必须始终为 Null。</span><span class="sxs-lookup"><span data-stu-id="02f87-206">However, SQL Server supports division by nulls, and the result must always equal null.</span></span>  
  
<span data-ttu-id="02f87-207">在 DirectQuery 模式下将不会针对这些运算返回不同结果，但这两种运算类型（被零除和被 Null 除）将返回错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-207">Rather than return different results for these operations, in DirectQuery mode, both types of operations (division by zero and division by null) return an error.</span></span>  
  
<span data-ttu-id="02f87-208">请注意，在 Excel 和 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 模型中，被零除也返回错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-208">Note that, in Excel and in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] models, division by zero also returns an error.</span></span> <span data-ttu-id="02f87-209">除以空白将返回空白。</span><span class="sxs-lookup"><span data-stu-id="02f87-209">Division by a blank returns a blank.</span></span>  
  
<span data-ttu-id="02f87-210">下面的表达式在内存中模型中都是有效的，但在 DirectQuery 模式下将失败：</span><span class="sxs-lookup"><span data-stu-id="02f87-210">The following expressions are all valid in in-memory models, but will fail in DirectQuery mode:</span></span>  
  
`1/BLANK`  
  
`1/0`  
  
`0.0/BLANK`  
  
`0/0`  
  
<span data-ttu-id="02f87-211">表达式 `BLANK/BLANK` 是一种特殊情况，它在内存中模型和 DirectQuery 模式下同时返回 `BLANK` 。</span><span class="sxs-lookup"><span data-stu-id="02f87-211">The expression `BLANK/BLANK` is a special case that returns `BLANK` in both for in-memory models, and in DirectQuery mode.</span></span>  
  
### <a name="supported-numeric-and-date-time-ranges"></a><a name="bkmk_Ranges"></a><span data-ttu-id="02f87-212">支持的数值和日期时间范围</span><span class="sxs-lookup"><span data-stu-id="02f87-212">Supported numeric and date-time ranges</span></span>  
<span data-ttu-id="02f87-213">[!INCLUDE[ssGemini](../includes/ssgemini-md.md)]和中的表格模型中的公式与 Excel 具有相同的限制，与实际数字和日期的最大允许值相关。</span><span class="sxs-lookup"><span data-stu-id="02f87-213">Formulas in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] and tabular models in-memory are subject to the same limitations as Excel with regard to maximum allowed values for real numbers and dates.</span></span> <span data-ttu-id="02f87-214">但是，当从计算或查询中返回最大值时，或者当转换、强制转换、舍入或截断值时，将出现差异。</span><span class="sxs-lookup"><span data-stu-id="02f87-214">However, differences can arise when the maximum value is returned from a calculation or query, or when values are converted, cast, rounded, or truncated.</span></span>  
  
-   <span data-ttu-id="02f87-215">如果在 DirectQuery 模式下，类型 **Currency** 和 **Real** 的值相乘，并且结果大于可能的最大值，则不会引发错误，而返回 Null。</span><span class="sxs-lookup"><span data-stu-id="02f87-215">If values of types **Currency** and **Real** are multiplied, and the result is larger than the maximum possible value, in DirectQuery mode, no error is raised, and a null is returned.</span></span>  
  
-   <span data-ttu-id="02f87-216">在内存中模型中，不会引发错误，但返回最大值。</span><span class="sxs-lookup"><span data-stu-id="02f87-216">In in-memory models, no error is raised, but the maximum value is returned.</span></span>  
  
<span data-ttu-id="02f87-217">通常，因为接受的日期范围对于 Excel 和 SQL Server 是不同的，所以，仅当日期在共同的日期范围内（包括以下日期）时，才能保证结果匹配。</span><span class="sxs-lookup"><span data-stu-id="02f87-217">In general, because the accepted date ranges are different for Excel and SQL Server, results can be guaranteed to match only when dates are within the common date range, which is inclusive of the following dates:</span></span>  
  
-   <span data-ttu-id="02f87-218">最早日期：1990 年 3 月 1 日</span><span class="sxs-lookup"><span data-stu-id="02f87-218">Earliest date: March 1, 1990</span></span>  
  
-   <span data-ttu-id="02f87-219">最晚日期：9999 年 12 月 31 日</span><span class="sxs-lookup"><span data-stu-id="02f87-219">Latest date: December 31, 9999</span></span>  
  
<span data-ttu-id="02f87-220">如果公式中使用的任何日期超出此范围，则公式将导致错误，或结果不匹配。</span><span class="sxs-lookup"><span data-stu-id="02f87-220">If any dates used in formulas fall outside this range, either the formula will result in an error, or the results will not match.</span></span>  
  
<span data-ttu-id="02f87-221">**CEILING 支持的浮点值**</span><span class="sxs-lookup"><span data-stu-id="02f87-221">**Floating point values supported by CEILING**</span></span>  
<span data-ttu-id="02f87-222">示例： `EVALUATE ROW("x", CEILING(-4.398488E+30, 1))`</span><span class="sxs-lookup"><span data-stu-id="02f87-222">EXAMPLE: `EVALUATE ROW("x", CEILING(-4.398488E+30, 1))`</span></span>  
  
<span data-ttu-id="02f87-223">DAX CEILING 函数的 Transact-SQL 对等函数只支持数量级为 10^19 或更低的值。</span><span class="sxs-lookup"><span data-stu-id="02f87-223">The Transact-SQL equivalent of the DAX CEILING function only supports values with magnitude of 10^19 or less.</span></span> <span data-ttu-id="02f87-224">一个常识是浮点值应能够适合 **bigint**。</span><span class="sxs-lookup"><span data-stu-id="02f87-224">A rule of thumb is that floating point values should be able to fit into **bigint**.</span></span>  
  
<span data-ttu-id="02f87-225">**所含日期超出范围的 Datepart 函数**</span><span class="sxs-lookup"><span data-stu-id="02f87-225">**Datepart functions with dates that are out of range**</span></span>  
<span data-ttu-id="02f87-226">仅当用作参数的日期在有效的日期范围内时，DirectQuery 模式下的结果才与内存中模型中的结果匹配。</span><span class="sxs-lookup"><span data-stu-id="02f87-226">Results in DirectQuery mode are guaranteed to match those in in-memory models only when the date used as the argument is in the valid date range.</span></span> <span data-ttu-id="02f87-227">如果未满足这些条件，则要么引发错误，要么公式在 DirectQuery 模式下将返回与在内存中模式下不同的结果。</span><span class="sxs-lookup"><span data-stu-id="02f87-227">If these conditions are not satisfied, either an error will be raised, or the formula will return different results in DirectQuery than in in-memory mode.</span></span>  
  
<span data-ttu-id="02f87-228">示例： `MONTH(0)` 或 `YEAR(0)`</span><span class="sxs-lookup"><span data-stu-id="02f87-228">EXAMPLE: `MONTH(0)` or `YEAR(0)`</span></span>  
  
<span data-ttu-id="02f87-229">在 DirectQuery 模式下，此表达式分别返回 12 和 1899。</span><span class="sxs-lookup"><span data-stu-id="02f87-229">In DirectQuery mode, the expressions return 12 and 1899, respectively.</span></span>  
  
<span data-ttu-id="02f87-230">在内存中模型内，此表达式分别返回 1 和 1900。</span><span class="sxs-lookup"><span data-stu-id="02f87-230">In in-memory models, the expressions return 1 and 1900, respectively.</span></span>  
  
<span data-ttu-id="02f87-231">示例：  `EOMONTH(0.0001, 1)`</span><span class="sxs-lookup"><span data-stu-id="02f87-231">EXAMPLE:  `EOMONTH(0.0001, 1)`</span></span>  
  
<span data-ttu-id="02f87-232">仅当作为参数提供的数据在有效的日期范围内时，此表达式的结果才匹配。</span><span class="sxs-lookup"><span data-stu-id="02f87-232">The results of this expression will match only when the data supplied as a parameter is within the valid date range.</span></span>  
  
<span data-ttu-id="02f87-233">示例： `EOMONTH(blank(), blank())` 或 `EDATE(blank(), blank())`</span><span class="sxs-lookup"><span data-stu-id="02f87-233">EXAMPLE: `EOMONTH(blank(), blank())` or `EDATE(blank(), blank())`</span></span>  
  
<span data-ttu-id="02f87-234">此表达式的结果在 DirectQuery 模式和内存中模式下应该是相同的。</span><span class="sxs-lookup"><span data-stu-id="02f87-234">The results of this expression should be the same in DirectQuery mode and in-memory mode.</span></span>  
  
<span data-ttu-id="02f87-235">**截断时间值**</span><span class="sxs-lookup"><span data-stu-id="02f87-235">**Truncation of time values**</span></span>  
<span data-ttu-id="02f87-236">示例： `SECOND(1231.04097222222)`</span><span class="sxs-lookup"><span data-stu-id="02f87-236">EXAMPLE: `SECOND(1231.04097222222)`</span></span>  
  
<span data-ttu-id="02f87-237">在 DirectQuery 模式下，将按照 SQL Server 的规则截断结果，并且表达式的计算结果为 59。</span><span class="sxs-lookup"><span data-stu-id="02f87-237">In DirectQuery mode, the result is truncated, following the rules of SQL Server, and the expression evaluates to 59.</span></span>  
  
<span data-ttu-id="02f87-238">在内存中模型内，每个临时运算的结果将四舍五入；因此，表达式的计算结果为 0。</span><span class="sxs-lookup"><span data-stu-id="02f87-238">In in-memory models, the results of each interim operation are rounded; therefore, the expression evaluates to 0.</span></span>  
  
<span data-ttu-id="02f87-239">下面的示例演示如何计算此值：</span><span class="sxs-lookup"><span data-stu-id="02f87-239">The following example demonstrates how this value is calculated:</span></span>  
  
1.  <span data-ttu-id="02f87-240">输入的小数部分 (0.04097222222) 乘以 24。</span><span class="sxs-lookup"><span data-stu-id="02f87-240">The fraction of the input (0.04097222222) is multiplied by 24.</span></span>  
  
2.  <span data-ttu-id="02f87-241">生成的小时值 (0.98333333328) 乘以 60。</span><span class="sxs-lookup"><span data-stu-id="02f87-241">The resulting hour value (0.98333333328) is multiplied by 60.</span></span>  
  
3.  <span data-ttu-id="02f87-242">生成的分钟值为 58.9999999968。</span><span class="sxs-lookup"><span data-stu-id="02f87-242">The resulting minute value is 58.9999999968.</span></span>  
  
4.  <span data-ttu-id="02f87-243">分钟值的小数部分 (0.9999999968) 乘以 60。</span><span class="sxs-lookup"><span data-stu-id="02f87-243">The fraction of the minute value (0.9999999968) is multiplied by 60.</span></span>  
  
5.  <span data-ttu-id="02f87-244">生成的秒钟值 (59.999999808) 舍入到 60。</span><span class="sxs-lookup"><span data-stu-id="02f87-244">The resulting second value (59.999999808) rounds up to 60.</span></span>  
  
6.  <span data-ttu-id="02f87-245">60 等效于 0。</span><span class="sxs-lookup"><span data-stu-id="02f87-245">60 is equivalent to 0.</span></span>  
  
<span data-ttu-id="02f87-246">**不支持的 SQL 时间数据类型**</span><span class="sxs-lookup"><span data-stu-id="02f87-246">**SQL Time data type not supported**</span></span>  
<span data-ttu-id="02f87-247">内存中模型不支持使用新的 SQL **Time** 数据类型。</span><span class="sxs-lookup"><span data-stu-id="02f87-247">In-memory models do not support use of the new SQL **Time** data type.</span></span> <span data-ttu-id="02f87-248">在 DirectQuery 模式下，引用具有此数据类型的列的公式将返回错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-248">In DirectQuery mode, formulas that reference columns with this data type will return an error.</span></span> <span data-ttu-id="02f87-249">时间数据列不能导入到内存中模型内。</span><span class="sxs-lookup"><span data-stu-id="02f87-249">Time data columns cannot be imported into an in-memory model.</span></span>  
  
<span data-ttu-id="02f87-250">但是，在 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 和缓存模型中，有时引擎会将时间值转换为可接受的数据类型，并且公式将返回结果。</span><span class="sxs-lookup"><span data-stu-id="02f87-250">However, in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] and in cached models, sometimes the engine casts the time value to an acceptable data type, and the formula returns a result.</span></span>  
  
<span data-ttu-id="02f87-251">这种行为影响将日期列用作参数的所有函数。</span><span class="sxs-lookup"><span data-stu-id="02f87-251">This behavior affects all functions that use a date column as a parameter.</span></span>  
  
### <a name="currency"></a><a name="bkmk_Currency"></a><span data-ttu-id="02f87-252">货币</span><span class="sxs-lookup"><span data-stu-id="02f87-252">Currency</span></span>  
<span data-ttu-id="02f87-253">在 DirectQuery 模式下，如果算术运算的结果具有类型 **Currency**，则值必须在以下范围内：</span><span class="sxs-lookup"><span data-stu-id="02f87-253">In DirectQuery mode, if the result of an arithmetic operation has the type **Currency**, the value must be within the following range:</span></span>  
  
-   <span data-ttu-id="02f87-254">最小值：-922337203685477.5808</span><span class="sxs-lookup"><span data-stu-id="02f87-254">Minimum: -922337203685477.5808</span></span>  
  
-   <span data-ttu-id="02f87-255">最大值：922337203685477.5807</span><span class="sxs-lookup"><span data-stu-id="02f87-255">Maximum: 922337203685477.5807</span></span>  
  
<span data-ttu-id="02f87-256">**结合使用 Currency 和 REAL 数据类型**</span><span class="sxs-lookup"><span data-stu-id="02f87-256">**Combining currency and REAL data types**</span></span>  
<span data-ttu-id="02f87-257">示例： `Currency sample 1`</span><span class="sxs-lookup"><span data-stu-id="02f87-257">EXAMPLE: `Currency sample 1`</span></span>  
  
<span data-ttu-id="02f87-258">如果 **Currency** 和 **Real** 类型相乘，并且结果大于 9223372036854774784 (0x7ffffffffffffc00)，则 DirectQuery 模式不会引发错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-258">If **Currency** and **Real** types are multiplied, and the result is larger than 9223372036854774784 (0x7ffffffffffffc00), DirectQuery mode will not raise an error.</span></span>  
  
<span data-ttu-id="02f87-259">在内存中模型内，如果结果的绝对值大于 922337203685477.4784，则引发错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-259">In an in-memory model, an error is raised if the absolute value of the result is larger than 922337203685477.4784.</span></span>  
  
<span data-ttu-id="02f87-260">**运算导致值超出范围**</span><span class="sxs-lookup"><span data-stu-id="02f87-260">**Operation results in an out-of-range value**</span></span>  
<span data-ttu-id="02f87-261">示例： `Currency sample 2`</span><span class="sxs-lookup"><span data-stu-id="02f87-261">EXAMPLE: `Currency sample 2`</span></span>  
  
<span data-ttu-id="02f87-262">如果针对两种货币值的运算导致值超出指定的范围，则在内存中模型内将引发错误，但在 DirectQuery 模型中不引发错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-262">If operations on any two currency values result in a value that is outside the specified range, an error is raised in in-memory models, but not in DirectQuery models.</span></span>  
  
<span data-ttu-id="02f87-263">**结合使用 Currency 以及其他数据类型**</span><span class="sxs-lookup"><span data-stu-id="02f87-263">**Combining currency with other data types**</span></span>  
<span data-ttu-id="02f87-264">将货币值除以其他数值类型的值可能导致不同的结果。</span><span class="sxs-lookup"><span data-stu-id="02f87-264">Division of currency values by values of other numeric types can result in different results.</span></span>  
  
### <a name="aggregation-functions"></a><a name="bkmk_Aggregations"></a><span data-ttu-id="02f87-265">聚合函数</span><span class="sxs-lookup"><span data-stu-id="02f87-265">Aggregation functions</span></span>  
<span data-ttu-id="02f87-266">对包含一行的表执行统计函数会返回不同的结果。</span><span class="sxs-lookup"><span data-stu-id="02f87-266">Statistical functions on a table with one row return different results.</span></span> <span data-ttu-id="02f87-267">对空表执行聚合函数的行为对于内存中模型和 DirectQuery 模式也不相同。</span><span class="sxs-lookup"><span data-stu-id="02f87-267">Aggregation functions over empty tables also behave differently in in-memory models than they do in DirectQuery mode.</span></span>  
  
<span data-ttu-id="02f87-268">**针对具有单行的表执行统计函数**</span><span class="sxs-lookup"><span data-stu-id="02f87-268">**Statistical functions over a table with a single row**</span></span>  
<span data-ttu-id="02f87-269">如果在 DirectQuery 模式下用作参数的表包含单个行，则统计函数（如 STDEV 和 VAR）将返回 Null。</span><span class="sxs-lookup"><span data-stu-id="02f87-269">If the table that is used as argument contains a single row, in DirectQuery mode, statistical functions such as STDEV and VAR return null.</span></span>  
  
<span data-ttu-id="02f87-270">在内存中模型中，对具有单一行的表使用 STDEV 或 VAR 的公式将返回被零除错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-270">In an in-memory model, a formula that uses STDEV or VAR over a table with a single row returns a division by zero error.</span></span>  
  
### <a name="text-functions"></a><a name="bkmk_Text"></a><span data-ttu-id="02f87-271">文本函数</span><span class="sxs-lookup"><span data-stu-id="02f87-271">Text functions</span></span>  
<span data-ttu-id="02f87-272">因为关系数据存储区与 Excel 提供的文本数据类型不同，所以，当您搜索字符串或使用子字符串时，可能看到不同的结果。</span><span class="sxs-lookup"><span data-stu-id="02f87-272">Because relational data stores provide different text data types than does Excel, you may see different results when searching strings or working with substrings.</span></span> <span data-ttu-id="02f87-273">字符串的长度也可能不同。</span><span class="sxs-lookup"><span data-stu-id="02f87-273">The length of strings also can be different.</span></span>  
  
<span data-ttu-id="02f87-274">通常，使用固定大小列作为参数的任何字符串运算函数都可能具有不同的结果。</span><span class="sxs-lookup"><span data-stu-id="02f87-274">In general, any string manipulation functions that use fixed-size columns as arguments can have different results.</span></span>  
  
<span data-ttu-id="02f87-275">此外，在 SQL Server 中，一些文本函数支持 Excel 中未提供的其他参数。</span><span class="sxs-lookup"><span data-stu-id="02f87-275">Additionally, in SQL Server, some text functions support additional arguments that are not provided in Excel.</span></span> <span data-ttu-id="02f87-276">如果公式需要缺少的参数，则在内存中模型内可能获得不同的结果或错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-276">If the formula requires the missing argument you can get different results or errors in the in-memory model.</span></span>  
  
<span data-ttu-id="02f87-277">**使用 LEFT、RIGHT 等返回字符的运算可能返回正确的字符但大小写不同，或者不返回结果。**</span><span class="sxs-lookup"><span data-stu-id="02f87-277">**Operations that return a character using LEFT, RIGHT, etc. may return the correct character but in a different case, or no results**</span></span>  
<span data-ttu-id="02f87-278">示例： `LEFT(["text"], 2)`</span><span class="sxs-lookup"><span data-stu-id="02f87-278">EXAMPLE: `LEFT(["text"], 2)`</span></span>  
  
<span data-ttu-id="02f87-279">在 DirectQuery 模式下，所返回的字符的大小写始终与数据库中存储的字母完全相同。</span><span class="sxs-lookup"><span data-stu-id="02f87-279">In DirectQuery mode, the case of the character that is returned is always exactly the same as the letter that is stored in the database.</span></span> <span data-ttu-id="02f87-280">但是，xVelocity 引擎针对值的压缩和编制索引使用不同的算法以提高性能。</span><span class="sxs-lookup"><span data-stu-id="02f87-280">However, the xVelocity engine uses a different algorithm for compression and indexing of values, to improve performance.</span></span>  
  
<span data-ttu-id="02f87-281">默认情况下使用 Latin1_General 排序规则，它不区分大小写，但区分重音。</span><span class="sxs-lookup"><span data-stu-id="02f87-281">By default, the Latin1_General collation is used, which is case-insensitive but accent-sensitive.</span></span> <span data-ttu-id="02f87-282">因此，如果一个文本字符串的多个实例为小写、大写或混合大小写，则所有实例都被视为相同的字符串，索引中只存储字符串的第一个实例。</span><span class="sxs-lookup"><span data-stu-id="02f87-282">Therefore, if there are multiple instances of a text string in lower case, upper case, or mixed case, all instances are considered the same string, and only the first instance of the string is stored in the index.</span></span> <span data-ttu-id="02f87-283">针对存储的字符串执行的所有文本函数都将检索编入索引的表单的指定部分。</span><span class="sxs-lookup"><span data-stu-id="02f87-283">All text functions that operate on stored strings will retrieve the specified portion of the indexed form.</span></span> <span data-ttu-id="02f87-284">因此，此示例公式将使用第一个实例作为输入，针对整列返回相同的值。</span><span class="sxs-lookup"><span data-stu-id="02f87-284">Therefore, the example formula would return the same value for the entire column, using the first instance as the input.</span></span>  
  
[<span data-ttu-id="02f87-285">表格模型中的字符串存储和排序规则</span><span class="sxs-lookup"><span data-stu-id="02f87-285">String Storage and Collation in Tabular Models</span></span>](https://msdn.microsoft.com/8516f0ad-32ee-4688-a304-e705143642ca)  
  
<span data-ttu-id="02f87-286">这种行为也适用于其他文本函数，包括 RIGHT、MID 等。</span><span class="sxs-lookup"><span data-stu-id="02f87-286">This behavior also applies to other text functions, including RIGHT, MID, and so forth.</span></span>  
  
<span data-ttu-id="02f87-287">**字符串长度影响结果**</span><span class="sxs-lookup"><span data-stu-id="02f87-287">**String length affects results**</span></span>  
<span data-ttu-id="02f87-288">示例： `SEARCH("within string", "sample target  text", 1, 1)`</span><span class="sxs-lookup"><span data-stu-id="02f87-288">EXAMPLE: `SEARCH("within string", "sample target  text", 1, 1)`</span></span>  
  
<span data-ttu-id="02f87-289">如果您使用 SEARCH 函数某个搜索字符串，并且目标字符串大于此内部包含的字符串，DirectQuery 模式将引发错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-289">If you search for a string using the SEARCH function, and the target string is longer than the within string, DirectQuery mode raises an error.</span></span>  
  
<span data-ttu-id="02f87-290">在内存中模型内，将返回所搜索的字符串，但其长度截断为 &lt;内含文本&gt;的长度。</span><span class="sxs-lookup"><span data-stu-id="02f87-290">In an in-memory model, the searched string is returned, but with its length truncated to the length of &lt;within text&gt;.</span></span>  
  
<span data-ttu-id="02f87-291">示例： `EVALUATE ROW("X", REPLACE("CA", 3, 2, "California") )`</span><span class="sxs-lookup"><span data-stu-id="02f87-291">EXAMPLE: `EVALUATE ROW("X", REPLACE("CA", 3, 2, "California") )`</span></span>  
  
<span data-ttu-id="02f87-292">如果在 DirectQuery 模式下，替换字符串的长度大于原始字符串的长度，则公式将返回 Null。</span><span class="sxs-lookup"><span data-stu-id="02f87-292">If the length of the replacement string is greater than the length of the original string, in DirectQuery mode, the formula returns null.</span></span>  
  
<span data-ttu-id="02f87-293">在内存中模型内，公式遵循 Excel 的行为，它将源字符串和替换字符串串联起来，返回 CACalifornia。</span><span class="sxs-lookup"><span data-stu-id="02f87-293">In in-memory models, the formula follows the behavior of Excel, which concatenates the source string and the replacement string, which returns CACalifornia.</span></span>  
  
<span data-ttu-id="02f87-294">**字符串中间的隐式 TRIM**</span><span class="sxs-lookup"><span data-stu-id="02f87-294">**Implicit TRIM in the middle of strings**</span></span>  
<span data-ttu-id="02f87-295">示例： `TRIM(" A sample sentence with leading white space")`</span><span class="sxs-lookup"><span data-stu-id="02f87-295">EXAMPLE: `TRIM(" A sample sentence with leading white space")`</span></span>  
  
<span data-ttu-id="02f87-296">DirectQuery 模式将 DAX TRIM 函数转换为 SQL 语句 `LTRIM(RTRIM(<column>))`。</span><span class="sxs-lookup"><span data-stu-id="02f87-296">DirectQuery mode translates the DAX TRIM function to the SQL statement `LTRIM(RTRIM(<column>))`.</span></span> <span data-ttu-id="02f87-297">因此，将只删除前导和尾随空格。</span><span class="sxs-lookup"><span data-stu-id="02f87-297">As a result, only leading and trailing white space is removed.</span></span>  
  
<span data-ttu-id="02f87-298">相比较而言，内存中模型内的相同公式将遵循 Excel 的行为，删除字符串内的空格。</span><span class="sxs-lookup"><span data-stu-id="02f87-298">In contrast, the same formula in an in-memory model removes spaces within the string, following the behavior of Excel.</span></span>  
  
<span data-ttu-id="02f87-299">**隐式 RTRIM 并使用 LEN 函数**</span><span class="sxs-lookup"><span data-stu-id="02f87-299">**Implicit RTRIM with use of LEN function**</span></span>  
<span data-ttu-id="02f87-300">示例： `LEN('string_column')`</span><span class="sxs-lookup"><span data-stu-id="02f87-300">EXAMPLE: `LEN('string_column')`</span></span>  
  
<span data-ttu-id="02f87-301">与 SQL Server 类似，DirectQuery 模式自动从字符串列的末尾删除空格；也即，它执行隐式 RTRIM。</span><span class="sxs-lookup"><span data-stu-id="02f87-301">Like SQL Server, DirectQuery mode automatically removes white space from the end of string columns: that is, it performs an implicit RTRIM.</span></span> <span data-ttu-id="02f87-302">因此，如果字符串具有尾随空格，则使用 LEN 函数的公式可能返回不同的值。</span><span class="sxs-lookup"><span data-stu-id="02f87-302">Therefore, formulas that use the LEN function can return different values if the string has trailing spaces.</span></span>  
  
<span data-ttu-id="02f87-303">**内存中模式支持 SUBSTITUTE 的其他参数**</span><span class="sxs-lookup"><span data-stu-id="02f87-303">**In-memory supports additional parameters for SUBSTITUTE**</span></span>  
<span data-ttu-id="02f87-304">示例： `SUBSTITUTE([Title],"Doctor","Dr.")`</span><span class="sxs-lookup"><span data-stu-id="02f87-304">EXAMPLE: `SUBSTITUTE([Title],"Doctor","Dr.")`</span></span>  
  
<span data-ttu-id="02f87-305">示例： `SUBSTITUTE([Title],"Doctor","Dr.", 2)`</span><span class="sxs-lookup"><span data-stu-id="02f87-305">EXAMPLE: `SUBSTITUTE([Title],"Doctor","Dr.", 2)`</span></span>  
  
<span data-ttu-id="02f87-306">在 DirectQuery 模式下，只能使用此函数具有三 (3) 个参数的版本：对列的引用、旧文本和新文本。</span><span class="sxs-lookup"><span data-stu-id="02f87-306">In DirectQuery mode, you can use only the version of this function that has three (3) parameters: a reference to a column, the old text, and the new text.</span></span> <span data-ttu-id="02f87-307">如果您使用第二个公式，将引发错误。</span><span class="sxs-lookup"><span data-stu-id="02f87-307">If you use the second formula, an error is raised.</span></span>  
  
<span data-ttu-id="02f87-308">在内存中模型中，您可以使用可选的第四个参数来指定要替换的字符串的实例编号。</span><span class="sxs-lookup"><span data-stu-id="02f87-308">In in-memory models, you can use an optional fourth parameter to specify the instance number of the string to replace.</span></span> <span data-ttu-id="02f87-309">例如，您可以只替换第二个实例等。</span><span class="sxs-lookup"><span data-stu-id="02f87-309">For example, you can replace only the second instance, etc.</span></span>  
  
<span data-ttu-id="02f87-310">**REPT 运算的字符串长度限制**</span><span class="sxs-lookup"><span data-stu-id="02f87-310">**Restrictions on string lengths for REPT operations**</span></span>  
<span data-ttu-id="02f87-311">在内存中模型内，使用 REPT 的运算所生成的字符串的长度应小于 32,767 个字符。</span><span class="sxs-lookup"><span data-stu-id="02f87-311">In in-memory models, the length of a string resulting from an operation using REPT must be less than 32,767 characters.</span></span>  
  
<span data-ttu-id="02f87-312">在 DirectQuery 模式下，这种限制不适用。</span><span class="sxs-lookup"><span data-stu-id="02f87-312">This limitation does not apply in DirectQuery mode.</span></span>  
  
<span data-ttu-id="02f87-313">**子字符串运算根据字符类型返回不同的结果**</span><span class="sxs-lookup"><span data-stu-id="02f87-313">**Substring operations return different results depending on character type**</span></span>  
<span data-ttu-id="02f87-314">示例： `MID([col], 2, 5)`</span><span class="sxs-lookup"><span data-stu-id="02f87-314">EXAMPLE: `MID([col], 2, 5)`</span></span>  
  
<span data-ttu-id="02f87-315">如果输入文本为 **varchar** 或 **nvarchar**，则公式的结果始终相同。</span><span class="sxs-lookup"><span data-stu-id="02f87-315">If the input text is **varchar** or **nvarchar**, the result of the formula is always the same.</span></span>  
  
<span data-ttu-id="02f87-316">但是，如果文本是固定长度的字符，并且\* &lt; num_chars &gt; \*的值大于目标字符串的长度，则在 DirectQuery 模式下，将在结果字符串的末尾添加一个空白。</span><span class="sxs-lookup"><span data-stu-id="02f87-316">However, if the text is a fixed-length character and the value for *&lt;num_chars&gt;* is greater than the length of the target string, in DirectQuery mode, a blank is added at the end of the result string.</span></span>  
  
<span data-ttu-id="02f87-317">在内存中模型内，结果将在字符串的最后一个字符处终止，且没有填充。</span><span class="sxs-lookup"><span data-stu-id="02f87-317">In an in-memory model, the result terminates at the last string character, with no padding.</span></span>  
  
## <a name="functions-supported-in-directquery-mode"></a><a name="bkmk_SupportedFunc"></a><span data-ttu-id="02f87-318">DirectQuery 模式下支持的函数</span><span class="sxs-lookup"><span data-stu-id="02f87-318">Functions supported in DirectQuery mode</span></span>  
<span data-ttu-id="02f87-319">以下 DAX 函数可用于 DirectQuery 模式下，但具有前面章节所介绍的限制条件。</span><span class="sxs-lookup"><span data-stu-id="02f87-319">The following DAX functions can be used in DirectQuery mode, but with the qualifications as described in the preceding section.</span></span>  
  
<span data-ttu-id="02f87-320">**文本函数**</span><span class="sxs-lookup"><span data-stu-id="02f87-320">**Text functions**</span></span>  
  
<span data-ttu-id="02f87-321">CONCATENATE</span><span class="sxs-lookup"><span data-stu-id="02f87-321">CONCATENATE</span></span>  
  
<span data-ttu-id="02f87-322">FIND</span><span class="sxs-lookup"><span data-stu-id="02f87-322">FIND</span></span>  
  
<span data-ttu-id="02f87-323">LEFT</span><span class="sxs-lookup"><span data-stu-id="02f87-323">LEFT</span></span>  
  
<span data-ttu-id="02f87-324">LEN</span><span class="sxs-lookup"><span data-stu-id="02f87-324">LEN</span></span>  
  
<span data-ttu-id="02f87-325">MID</span><span class="sxs-lookup"><span data-stu-id="02f87-325">MID</span></span>  
  
<span data-ttu-id="02f87-326">REPLACE</span><span class="sxs-lookup"><span data-stu-id="02f87-326">REPLACE</span></span>  
  
<span data-ttu-id="02f87-327">REPT</span><span class="sxs-lookup"><span data-stu-id="02f87-327">REPT</span></span>  
  
<span data-ttu-id="02f87-328">RIGHT</span><span class="sxs-lookup"><span data-stu-id="02f87-328">RIGHT</span></span>  
  
<span data-ttu-id="02f87-329">SUBSTITUTE</span><span class="sxs-lookup"><span data-stu-id="02f87-329">SUBSTITUTE</span></span>  
  
<span data-ttu-id="02f87-330">TRIM</span><span class="sxs-lookup"><span data-stu-id="02f87-330">TRIM</span></span>  
  
<span data-ttu-id="02f87-331">**统计函数**</span><span class="sxs-lookup"><span data-stu-id="02f87-331">**Statistical functions**</span></span>  
  
<span data-ttu-id="02f87-332">COUNT</span><span class="sxs-lookup"><span data-stu-id="02f87-332">COUNT</span></span>  
  
<span data-ttu-id="02f87-333">STDEV.P</span><span class="sxs-lookup"><span data-stu-id="02f87-333">STDEV.P</span></span>  
  
<span data-ttu-id="02f87-334">STDEV.S</span><span class="sxs-lookup"><span data-stu-id="02f87-334">STDEV.S</span></span>  
  
<span data-ttu-id="02f87-335">STDEVX.P</span><span class="sxs-lookup"><span data-stu-id="02f87-335">STDEVX.P</span></span>  
  
<span data-ttu-id="02f87-336">STDEVX.S</span><span class="sxs-lookup"><span data-stu-id="02f87-336">STDEVX.S</span></span>  
  
<span data-ttu-id="02f87-337">VAR.P</span><span class="sxs-lookup"><span data-stu-id="02f87-337">VAR.P</span></span>  
  
<span data-ttu-id="02f87-338">VAR.S</span><span class="sxs-lookup"><span data-stu-id="02f87-338">VAR.S</span></span>  
  
<span data-ttu-id="02f87-339">VARX.P</span><span class="sxs-lookup"><span data-stu-id="02f87-339">VARX.P</span></span>  
  
<span data-ttu-id="02f87-340">VARX.S</span><span class="sxs-lookup"><span data-stu-id="02f87-340">VARX.S</span></span>  
  
<span data-ttu-id="02f87-341">**日期/时间函数**</span><span class="sxs-lookup"><span data-stu-id="02f87-341">**Date/time functions**</span></span>  
  
<span data-ttu-id="02f87-342">DATE</span><span class="sxs-lookup"><span data-stu-id="02f87-342">DATE</span></span>  
  
<span data-ttu-id="02f87-343">EDATE</span><span class="sxs-lookup"><span data-stu-id="02f87-343">EDATE</span></span>  
  
<span data-ttu-id="02f87-344">EOMONTH</span><span class="sxs-lookup"><span data-stu-id="02f87-344">EOMONTH</span></span>  
  
<span data-ttu-id="02f87-345">DATE</span><span class="sxs-lookup"><span data-stu-id="02f87-345">DATE</span></span>  
  
<span data-ttu-id="02f87-346">TIME</span><span class="sxs-lookup"><span data-stu-id="02f87-346">TIME</span></span>  
  
<span data-ttu-id="02f87-347">SECOND</span><span class="sxs-lookup"><span data-stu-id="02f87-347">SECOND</span></span>  
  
<span data-ttu-id="02f87-348">**数学和数值函数**</span><span class="sxs-lookup"><span data-stu-id="02f87-348">**Math and number functions**</span></span>  
  
<span data-ttu-id="02f87-349">CEILING</span><span class="sxs-lookup"><span data-stu-id="02f87-349">CEILING</span></span>  
  
<span data-ttu-id="02f87-350">LN</span><span class="sxs-lookup"><span data-stu-id="02f87-350">LN</span></span>  
  
<span data-ttu-id="02f87-351">LOG</span><span class="sxs-lookup"><span data-stu-id="02f87-351">LOG</span></span>  
  
<span data-ttu-id="02f87-352">LOG10</span><span class="sxs-lookup"><span data-stu-id="02f87-352">LOG10</span></span>  
  
<span data-ttu-id="02f87-353">POWER</span><span class="sxs-lookup"><span data-stu-id="02f87-353">POWER</span></span>  
  
<span data-ttu-id="02f87-354">**DAX 表查询**</span><span class="sxs-lookup"><span data-stu-id="02f87-354">**DAX Table queries**</span></span>  
  
<span data-ttu-id="02f87-355">当您针对 DirectQuery 模型使用 DAX 表查询计算公式时，存在一些限制。</span><span class="sxs-lookup"><span data-stu-id="02f87-355">There are some limitations when you evaluate formulas against a DirectQuery model by using DAX Table queries.</span></span> <span data-ttu-id="02f87-356">DirectQuery 不支持在 ORDER BY 子句中两次引用同一列。</span><span class="sxs-lookup"><span data-stu-id="02f87-356">DirectQuery does not support referring to the same column twice in an ORDER BY clause.</span></span> <span data-ttu-id="02f87-357">无法创建等效的 Transact-SQL 语句，并且查询将失败。</span><span class="sxs-lookup"><span data-stu-id="02f87-357">The equivalent Transact-SQL statement cannot be created and the query fails.</span></span>  
  
<span data-ttu-id="02f87-358">在内存中模型中，重复 ORDER by 子句对结果没有影响。</span><span class="sxs-lookup"><span data-stu-id="02f87-358">In an in-memory model, repeating the ORDER by clause has no effect on the results.</span></span>  
  
## <a name="functions-not-supported-in-directquery-mode"></a><a name="bkmk_NotSupportedFunc"></a><span data-ttu-id="02f87-359">DirectQuery 模式下不支持的函数</span><span class="sxs-lookup"><span data-stu-id="02f87-359">Functions not supported in DirectQuery Mode</span></span>  
<span data-ttu-id="02f87-360">对于在 DirectQuery 模式下部署的模型，不支持某些 DAX 函数。</span><span class="sxs-lookup"><span data-stu-id="02f87-360">Some DAX functions are not supported in models that are deployed in DirectQuery mode.</span></span> <span data-ttu-id="02f87-361">不支持特定函数的原因可能包括以下任一原因或这些原因的组合：</span><span class="sxs-lookup"><span data-stu-id="02f87-361">The reasons that a particular function is not supported can include any or a combination of these reasons:</span></span>  
  
-   <span data-ttu-id="02f87-362">基础关系引擎无法执行与 xVelocity 引擎执行的计算等效的计算。</span><span class="sxs-lookup"><span data-stu-id="02f87-362">The underlying relational engine cannot perform calculations equivalent to those performed by the xVelocity engine.</span></span>  
  
-   <span data-ttu-id="02f87-363">公式不能转换为等效的 SQL 表达式。</span><span class="sxs-lookup"><span data-stu-id="02f87-363">The formula cannot be converted to en equivalent SQL expression.</span></span>  
  
-   <span data-ttu-id="02f87-364">转换后的表达式和生成的计算的性能不可接受。</span><span class="sxs-lookup"><span data-stu-id="02f87-364">The performance of the converted expression and the resulting calculations would be unacceptable.</span></span>  
  
<span data-ttu-id="02f87-365">在 DirectQuery 模型中不能使用以下 DAX 函数。</span><span class="sxs-lookup"><span data-stu-id="02f87-365">The following DAX functions cannot be used in DirectQuery models.</span></span>  
  
<span data-ttu-id="02f87-366">**路径函数**</span><span class="sxs-lookup"><span data-stu-id="02f87-366">**Path functions**</span></span>  
  
<span data-ttu-id="02f87-367">PATH</span><span class="sxs-lookup"><span data-stu-id="02f87-367">PATH</span></span>  
  
<span data-ttu-id="02f87-368">PATHCONTAINS</span><span class="sxs-lookup"><span data-stu-id="02f87-368">PATHCONTAINS</span></span>  
  
<span data-ttu-id="02f87-369">PATHITEM</span><span class="sxs-lookup"><span data-stu-id="02f87-369">PATHITEM</span></span>  
  
<span data-ttu-id="02f87-370">PATHITEMREVERSE</span><span class="sxs-lookup"><span data-stu-id="02f87-370">PATHITEMREVERSE</span></span>  
  
<span data-ttu-id="02f87-371">PATHLENGTH</span><span class="sxs-lookup"><span data-stu-id="02f87-371">PATHLENGTH</span></span>  
  
<span data-ttu-id="02f87-372">**其他函数**</span><span class="sxs-lookup"><span data-stu-id="02f87-372">**Misc functions**</span></span>  
  
<span data-ttu-id="02f87-373">COUNTBLANK</span><span class="sxs-lookup"><span data-stu-id="02f87-373">COUNTBLANK</span></span>  
  
<span data-ttu-id="02f87-374">FIXED</span><span class="sxs-lookup"><span data-stu-id="02f87-374">FIXED</span></span>  
  
<span data-ttu-id="02f87-375">FORMAT</span><span class="sxs-lookup"><span data-stu-id="02f87-375">FORMAT</span></span>  
  
<span data-ttu-id="02f87-376">RAND</span><span class="sxs-lookup"><span data-stu-id="02f87-376">RAND</span></span>  
  
<span data-ttu-id="02f87-377">RANDBETWEEN</span><span class="sxs-lookup"><span data-stu-id="02f87-377">RANDBETWEEN</span></span>  
  
<span data-ttu-id="02f87-378">**时间智能函数：开始日期和结束日期**</span><span class="sxs-lookup"><span data-stu-id="02f87-378">**Time intelligence functions: Start and end dates**</span></span>  
  
<span data-ttu-id="02f87-379">DATESQTD</span><span class="sxs-lookup"><span data-stu-id="02f87-379">DATESQTD</span></span>  
  
<span data-ttu-id="02f87-380">DATESYTD</span><span class="sxs-lookup"><span data-stu-id="02f87-380">DATESYTD</span></span>  
  
<span data-ttu-id="02f87-381">DATESMTD</span><span class="sxs-lookup"><span data-stu-id="02f87-381">DATESMTD</span></span>  
  
<span data-ttu-id="02f87-382">DATESQTD</span><span class="sxs-lookup"><span data-stu-id="02f87-382">DATESQTD</span></span>  
  
<span data-ttu-id="02f87-383">DATESINPERIOD</span><span class="sxs-lookup"><span data-stu-id="02f87-383">DATESINPERIOD</span></span>  
  
<span data-ttu-id="02f87-384">TOTALMTD</span><span class="sxs-lookup"><span data-stu-id="02f87-384">TOTALMTD</span></span>  
  
<span data-ttu-id="02f87-385">TOTALQTD</span><span class="sxs-lookup"><span data-stu-id="02f87-385">TOTALQTD</span></span>  
  
<span data-ttu-id="02f87-386">TOTALYTD</span><span class="sxs-lookup"><span data-stu-id="02f87-386">TOTALYTD</span></span>  
  
<span data-ttu-id="02f87-387">DATESINPERIOD</span><span class="sxs-lookup"><span data-stu-id="02f87-387">DATESINPERIOD</span></span>  
  
<span data-ttu-id="02f87-388">SAMEPERIODLASTYEAR</span><span class="sxs-lookup"><span data-stu-id="02f87-388">SAMEPERIODLASTYEAR</span></span>  
  
<span data-ttu-id="02f87-389">PARALLELPERIOD</span><span class="sxs-lookup"><span data-stu-id="02f87-389">PARALLELPERIOD</span></span>  
  
<span data-ttu-id="02f87-390">**时间智能函数：余额**</span><span class="sxs-lookup"><span data-stu-id="02f87-390">**Time-intelligence functions: Balances**</span></span>  
  
<span data-ttu-id="02f87-391">OPENINGBALANCEMONTH</span><span class="sxs-lookup"><span data-stu-id="02f87-391">OPENINGBALANCEMONTH</span></span>  
  
<span data-ttu-id="02f87-392">OPENINGBALANCEQUARTER</span><span class="sxs-lookup"><span data-stu-id="02f87-392">OPENINGBALANCEQUARTER</span></span>  
  
<span data-ttu-id="02f87-393">OPENINGBALANCEYEAR</span><span class="sxs-lookup"><span data-stu-id="02f87-393">OPENINGBALANCEYEAR</span></span>  
  
<span data-ttu-id="02f87-394">CLOSINGBALANCEMONTH</span><span class="sxs-lookup"><span data-stu-id="02f87-394">CLOSINGBALANCEMONTH</span></span>  
  
<span data-ttu-id="02f87-395">CLOSINGBALANCEQUARTER</span><span class="sxs-lookup"><span data-stu-id="02f87-395">CLOSINGBALANCEQUARTER</span></span>  
  
<span data-ttu-id="02f87-396">CLOSINGBALANCEYEAR</span><span class="sxs-lookup"><span data-stu-id="02f87-396">CLOSINGBALANCEYEAR</span></span>  
  
<span data-ttu-id="02f87-397">**时间智能函数：上一期间和下一期间**</span><span class="sxs-lookup"><span data-stu-id="02f87-397">**Time intelligence functions: Previous and next periods**</span></span>  
  
<span data-ttu-id="02f87-398">PREVIOUSDAY</span><span class="sxs-lookup"><span data-stu-id="02f87-398">PREVIOUSDAY</span></span>  
  
<span data-ttu-id="02f87-399">PREVIOUSMONTH</span><span class="sxs-lookup"><span data-stu-id="02f87-399">PREVIOUSMONTH</span></span>  
  
<span data-ttu-id="02f87-400">PREVIOUSQUARTER</span><span class="sxs-lookup"><span data-stu-id="02f87-400">PREVIOUSQUARTER</span></span>  
  
<span data-ttu-id="02f87-401">PREVIOUSYEAR</span><span class="sxs-lookup"><span data-stu-id="02f87-401">PREVIOUSYEAR</span></span>  
  
<span data-ttu-id="02f87-402">NEXTDAY</span><span class="sxs-lookup"><span data-stu-id="02f87-402">NEXTDAY</span></span>  
  
<span data-ttu-id="02f87-403">NEXTMONTH</span><span class="sxs-lookup"><span data-stu-id="02f87-403">NEXTMONTH</span></span>  
  
<span data-ttu-id="02f87-404">NEXTQUARTER</span><span class="sxs-lookup"><span data-stu-id="02f87-404">NEXTQUARTER</span></span>  
  
<span data-ttu-id="02f87-405">NEXTYEAR</span><span class="sxs-lookup"><span data-stu-id="02f87-405">NEXTYEAR</span></span>  
  
<span data-ttu-id="02f87-406">**时间智能函数：期间和针对期间的计算**</span><span class="sxs-lookup"><span data-stu-id="02f87-406">**Time intelligence functions: Periods and calculations over periods**</span></span>  
  
<span data-ttu-id="02f87-407">STARTOFMONTH</span><span class="sxs-lookup"><span data-stu-id="02f87-407">STARTOFMONTH</span></span>  
  
<span data-ttu-id="02f87-408">STARTOFQUARTER</span><span class="sxs-lookup"><span data-stu-id="02f87-408">STARTOFQUARTER</span></span>  
  
<span data-ttu-id="02f87-409">STARTOFYEAR</span><span class="sxs-lookup"><span data-stu-id="02f87-409">STARTOFYEAR</span></span>  
  
<span data-ttu-id="02f87-410">ENDOFMONTH</span><span class="sxs-lookup"><span data-stu-id="02f87-410">ENDOFMONTH</span></span>  
  
<span data-ttu-id="02f87-411">ENDOFQUARTER</span><span class="sxs-lookup"><span data-stu-id="02f87-411">ENDOFQUARTER</span></span>  
  
<span data-ttu-id="02f87-412">ENDOFYEAR</span><span class="sxs-lookup"><span data-stu-id="02f87-412">ENDOFYEAR</span></span>  
  
<span data-ttu-id="02f87-413">FIRSTDATE</span><span class="sxs-lookup"><span data-stu-id="02f87-413">FIRSTDATE</span></span>  
  
<span data-ttu-id="02f87-414">LASTDATE</span><span class="sxs-lookup"><span data-stu-id="02f87-414">LASTDATE</span></span>  
  
<span data-ttu-id="02f87-415">DATEADD</span><span class="sxs-lookup"><span data-stu-id="02f87-415">DATEADD</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f87-416">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02f87-416">See also</span></span>  
[<span data-ttu-id="02f87-417">DirectQuery 模式（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="02f87-417">DirectQuery Mode (SSAS Tabular)</span></span>](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5)  
  

