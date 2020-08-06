---
title: 数据挖掘)  (内容类型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], content types
- KEY SEQUENCE column
- content types [data mining]
- attributes [data mining]
- DISCRETIZED column
- CONTINUOUS column
- CYCLICAL column
- ORDERED column
- discretized columns [data mining]
- discrete columns [Analysis Services]
- DISCRETE column
- KEY column
- KEY TIME column
- continuous columns
- coding [Data Mining]
ms.assetid: 2dacd968-70e8-4993-88b6-a6d36024a4e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8e3400d904bc857bc282bb1ad9220c1e01fe5a4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682452"
---
# <a name="content-types-data-mining"></a><span data-ttu-id="62f0f-102">内容类型（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="62f0f-102">Content Types (Data Mining)</span></span>
  <span data-ttu-id="62f0f-103">在中， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 您可以为挖掘结构中的列定义物理数据类型，并在模型中使用该列时定义该列的逻辑内容类型。</span><span class="sxs-lookup"><span data-stu-id="62f0f-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can define the both the physical data type for a column in a mining structure, and a logical content type for the column when used in a model,</span></span>  
  
 <span data-ttu-id="62f0f-104">“数据类型 \*\* ”确定在您创建挖掘模型时算法如何处理这些列中的数据。</span><span class="sxs-lookup"><span data-stu-id="62f0f-104">The *data type* determines how algorithms process the data in those columns when you create mining models.</span></span> <span data-ttu-id="62f0f-105">定义列的数据类型可为算法提供有关列中的数据类型以及如何处理数据的信息。</span><span class="sxs-lookup"><span data-stu-id="62f0f-105">Defining the data type of a column gives the algorithm information about the type of data in the columns, and how to process the data.</span></span> <span data-ttu-id="62f0f-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的每种数据类型均支持用于数据挖掘的一种或多种内容类型。</span><span class="sxs-lookup"><span data-stu-id="62f0f-106">Each data type in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports one or more content types for data mining.</span></span>  
  
 <span data-ttu-id="62f0f-107">“内容类型 \*\* ”描述列中包含的内容的行为。</span><span class="sxs-lookup"><span data-stu-id="62f0f-107">The *content type* describes the behavior of the content that the column contains.</span></span> <span data-ttu-id="62f0f-108">例如，如果列中的内容以特定的间隔（如一周中的某几天）重复，则可以将该列的内容类型指定为循环。</span><span class="sxs-lookup"><span data-stu-id="62f0f-108">For example, if the content in a column repeats in a specific interval, such as days of the week, you can specify the content type of that column as cyclical.</span></span>  
  
 <span data-ttu-id="62f0f-109">有些算法要求提供特定的数据类型和特定的内容类型才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="62f0f-109">Some algorithms require specific data types and specific content types to be able to function correctly.</span></span> <span data-ttu-id="62f0f-110">例如，Microsoft Naive Bayes 算法的输入不能为连续列，而且不能预测连续值。</span><span class="sxs-lookup"><span data-stu-id="62f0f-110">For example, the Microsoft Naive Bayes algorithm cannot use continuous columns as input, and cannot predict continuous values.</span></span> <span data-ttu-id="62f0f-111">某些内容类型（如 Key Sequence）只能由特定算法使用。</span><span class="sxs-lookup"><span data-stu-id="62f0f-111">Some content types, such as Key Sequence, are used only by a specific algorithm.</span></span> <span data-ttu-id="62f0f-112">有关算法列表和每种算法所支持的内容类型，请参阅[数据挖掘算法（Analysis Services - 数据挖掘）](data-mining-algorithms-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="62f0f-112">For a list of the algorithms and the content types that each supports, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="62f0f-113">下表介绍了数据挖掘中使用的内容类型，并标识了支持每种类型的数据类型。</span><span class="sxs-lookup"><span data-stu-id="62f0f-113">The following list describes the content types that are used in data mining, and identifies the data types that support each type.</span></span>  
  
## <a name="discrete"></a><span data-ttu-id="62f0f-114">离散</span><span class="sxs-lookup"><span data-stu-id="62f0f-114">Discrete</span></span>  
 <span data-ttu-id="62f0f-115">“\*\* ”意味着列包含数值之间没有连续体的有限数量的数值。</span><span class="sxs-lookup"><span data-stu-id="62f0f-115">*Discrete* means that the column contains a finite number of values with no continuum between values.</span></span> <span data-ttu-id="62f0f-116">例如，性别列是一个典型的离散属性列，这是因为该数据表示特定数量的类别。</span><span class="sxs-lookup"><span data-stu-id="62f0f-116">For example, a gender column is a typical discrete attribute column, in that the data represents a specific number of categories.</span></span>  
  
 <span data-ttu-id="62f0f-117">离散属性列中的值不能意味着排序，即使这些值为数值也是如此。</span><span class="sxs-lookup"><span data-stu-id="62f0f-117">The values in a discrete attribute column cannot imply ordering, even if the values are numeric.</span></span> <span data-ttu-id="62f0f-118">此外，即使用于离散列的值为数值，也无法计算小数值。</span><span class="sxs-lookup"><span data-stu-id="62f0f-118">Moreover, even if the values used for the discrete column are numeric, fractional values cannot be calculated.</span></span> <span data-ttu-id="62f0f-119">电话区号即为数值离散数据的典型示例。</span><span class="sxs-lookup"><span data-stu-id="62f0f-119">Telephone area codes are a good example of discrete data that is numeric.</span></span>  
  
 <span data-ttu-id="62f0f-120">所有的数据挖掘数据类型均支持 `Discrete` 内容类型。</span><span class="sxs-lookup"><span data-stu-id="62f0f-120">The `Discrete` content type is supported by all data mining data types.</span></span>  
  
## <a name="continuous"></a><span data-ttu-id="62f0f-121">连续</span><span class="sxs-lookup"><span data-stu-id="62f0f-121">Continuous</span></span>  
 <span data-ttu-id="62f0f-122">“\*\* ”意味着列包含的值表示某一允许中间值的范围中的数值数据。</span><span class="sxs-lookup"><span data-stu-id="62f0f-122">*Continuous* means that the column contains values that represent numeric data on a scale that allows interim values.</span></span> <span data-ttu-id="62f0f-123">与表示有限、可数数据的离散列不同，连续列表示可缩放度量，且数据可能包含无限数目的小数值。</span><span class="sxs-lookup"><span data-stu-id="62f0f-123">Unlike a discrete column, which represents finite, countable data, a continuous column represents scalable measurements, and it is possible for the data to contain an infinite number of fractional values.</span></span> <span data-ttu-id="62f0f-124">温度列即为连续属性列的示例。</span><span class="sxs-lookup"><span data-stu-id="62f0f-124">A column of temperatures is an example of a continuous attribute column.</span></span>  
  
 <span data-ttu-id="62f0f-125">当一列中包含连续数值数据并且您知道这些数据应如何分布时，则有可能通过指定期望的值分布来提高分析的精确性。</span><span class="sxs-lookup"><span data-stu-id="62f0f-125">When a column contains continuous numeric data, and you know how the data should be distributed, you can potentially improve the accuracy of the analysis by specifying the expected distribution of values.</span></span> <span data-ttu-id="62f0f-126">您将在挖掘结构级别指定列分布。</span><span class="sxs-lookup"><span data-stu-id="62f0f-126">You specify the column distribution at the level of the mining structure.</span></span> <span data-ttu-id="62f0f-127">因此，该设置将应用到基于该结构的所有模型。有关详细信息，请参阅[列分布（数据挖掘）](column-distributions-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="62f0f-127">Therefore, the setting applies to all models that are based on the structure, For more information, see [Column Distributions &#40;Data Mining&#41;](column-distributions-data-mining.md).</span></span>  
  
 <span data-ttu-id="62f0f-128">以下数据类型支持 `Continuous` 内容类型：`Date`、`Double` 和 `Long`。</span><span class="sxs-lookup"><span data-stu-id="62f0f-128">The `Continuous` content type is supported by the following data types: `Date`, `Double`, and `Long`.</span></span>  
  
## <a name="discretized"></a><span data-ttu-id="62f0f-129">离散化</span><span class="sxs-lookup"><span data-stu-id="62f0f-129">Discretized</span></span>  
 <span data-ttu-id="62f0f-130">“离散化”\*\* 是将一组连续数据的值放入存储桶以便得到有限数量的可能值的过程。</span><span class="sxs-lookup"><span data-stu-id="62f0f-130">*Discretization* is the process of putting values of a continuous set of data into buckets so that there are a limited number of possible values.</span></span> <span data-ttu-id="62f0f-131">只能离散数值数据。</span><span class="sxs-lookup"><span data-stu-id="62f0f-131">You can discretize only numeric data.</span></span>  
  
 <span data-ttu-id="62f0f-132">因此，“discretized \*\* ”内容类型指示列中包含的值表示其中包括源自连续列的值的组或存储桶。</span><span class="sxs-lookup"><span data-stu-id="62f0f-132">Thus, the *discretized* content type indicates that the column contains values that represent groups, or buckets, of values that are derived from a continuous column.</span></span> <span data-ttu-id="62f0f-133">Bucket 被视为有序的离散值。</span><span class="sxs-lookup"><span data-stu-id="62f0f-133">The buckets are treated as ordered and discrete values.</span></span>  
  
 <span data-ttu-id="62f0f-134">您可以手动离散数据，以确保获取所需的存储桶，也可以使用 SQL Server Analysis Services 中提供的离散化方法。</span><span class="sxs-lookup"><span data-stu-id="62f0f-134">You can discretize your data manually, to ensure that you get the buckets you want, or you can use the discretization methods provided in SQL Server Analysis Services.</span></span> <span data-ttu-id="62f0f-135">某些算法自动执行离散化。</span><span class="sxs-lookup"><span data-stu-id="62f0f-135">Some algorithms perform discretization automatically.</span></span> <span data-ttu-id="62f0f-136">有关详细信息，请参阅 [更改挖掘模型中列的离散化](change-the-discretization-of-a-column-in-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="62f0f-136">For more information, see [Change the Discretization of a Column in a Mining Model](change-the-discretization-of-a-column-in-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="62f0f-137">以下数据类型支持 `Discretized` 内容类型：`Date`、`Double`、`Long` 和 `Text`。</span><span class="sxs-lookup"><span data-stu-id="62f0f-137">The `Discretized` content type is supported by the following data types: `Date`, `Double`, `Long`, and `Text`.</span></span>  
  
## <a name="key"></a><span data-ttu-id="62f0f-138">密钥</span><span class="sxs-lookup"><span data-stu-id="62f0f-138">Key</span></span>  
 <span data-ttu-id="62f0f-139">“key \*\* ”内容类型意味着该列唯一标识一行。</span><span class="sxs-lookup"><span data-stu-id="62f0f-139">The *key* content type means that the column uniquely identifies a row.</span></span> <span data-ttu-id="62f0f-140">在事例表中，键列通常为数值或文本标识符。</span><span class="sxs-lookup"><span data-stu-id="62f0f-140">In a case table, typically the key column is a numeric or text identifier.</span></span> <span data-ttu-id="62f0f-141">将内容类型设置为 `key` 可指示该列不应该用于分析，而仅应用于跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="62f0f-141">You set the content type to `key` to indicate that the column should not be used for analysis, only for tracking records.</span></span>  
  
 <span data-ttu-id="62f0f-142">嵌套表也有键，但嵌套表键的用法稍有不同。</span><span class="sxs-lookup"><span data-stu-id="62f0f-142">Nested tables also have keys, but the usage of the nested table key is a little different.</span></span> <span data-ttu-id="62f0f-143">如果某列是您需要分析的属性，则在嵌套表中将内容类型设置为 `key`。</span><span class="sxs-lookup"><span data-stu-id="62f0f-143">You set the content type to `key` in a nested table if the column is the attribute that you want to analyze.</span></span> <span data-ttu-id="62f0f-144">嵌套表键的值对于每个事例来说都必须唯一，但在整个事例集中可以重复。</span><span class="sxs-lookup"><span data-stu-id="62f0f-144">The values in the nested table key must be unique for each case but there can be duplicates across the entire set of cases.</span></span>  
  
 <span data-ttu-id="62f0f-145">例如，如果分析的是客户购买的产品，则可以对于事例表中 **CustomerID** 列将内容类型设置为键，然后对于嵌套表中 **PurchasedProducts** 列再次将内容类型设置为键。</span><span class="sxs-lookup"><span data-stu-id="62f0f-145">For example, if you are analyzing the products that customers purchase, you would set content type to key for the **CustomerID** column in the case table, and set content type to key again for the **PurchasedProducts** column in the nested table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="62f0f-146">只有在使用已被定义为 Analysis Services 数据源视图的外部数据源中的数据时，嵌套表才可用。</span><span class="sxs-lookup"><span data-stu-id="62f0f-146">Nested tables are available only if you use data from an external data source that has been defined as an Analysis services data source view.</span></span>  
  
 <span data-ttu-id="62f0f-147">以下数据类型支持此内容类型：`Date`、`Double`、`Long` 和 `Text`。</span><span class="sxs-lookup"><span data-stu-id="62f0f-147">This content type is supported by the following data types: `Date`, `Double`, `Long`, and `Text`.</span></span>  
  
## <a name="key-sequence"></a><span data-ttu-id="62f0f-148">键序列</span><span class="sxs-lookup"><span data-stu-id="62f0f-148">Key Sequence</span></span>  
 <span data-ttu-id="62f0f-149">“key sequence \*\* ”内容类型只能在顺序分析和聚类分析模型中使用。</span><span class="sxs-lookup"><span data-stu-id="62f0f-149">The *key sequence* content type can only be used in sequence clustering models.</span></span> <span data-ttu-id="62f0f-150">将内容类型设置为 `key sequence` 时，它指示列包含表示一个事件序列的值。</span><span class="sxs-lookup"><span data-stu-id="62f0f-150">When you set content type to `key sequence`, it indicates that the column contains values that represent a sequence of events.</span></span> <span data-ttu-id="62f0f-151">这些值是有序值，但不必按等差排列。</span><span class="sxs-lookup"><span data-stu-id="62f0f-151">The values are ordered, but do not have to be an equal distance apart.</span></span>  
  
 <span data-ttu-id="62f0f-152">以下数据类型支持此内容类型：`Double`、`Long`、`Text` 和 `Date`。</span><span class="sxs-lookup"><span data-stu-id="62f0f-152">This content type is supported by the following data types: `Double`, `Long`, `Text`, and `Date`.</span></span>  
  
## <a name="key-time"></a><span data-ttu-id="62f0f-153">键时间</span><span class="sxs-lookup"><span data-stu-id="62f0f-153">Key Time</span></span>  
 <span data-ttu-id="62f0f-154">“key time \*\* ”内容类型只能在时序模型中使用。</span><span class="sxs-lookup"><span data-stu-id="62f0f-154">The *key time* content type can only be used in time series models.</span></span> <span data-ttu-id="62f0f-155">将内容类型设置为 `key time` 时，它指示值是有序值并表示时间刻度。</span><span class="sxs-lookup"><span data-stu-id="62f0f-155">When you set content type to `key time`, it indicates that the values are ordered and represent a time scale.</span></span>  
  
 <span data-ttu-id="62f0f-156">以下数据类型支持此内容类型：`Double`、`Long` 和 `Date`。</span><span class="sxs-lookup"><span data-stu-id="62f0f-156">This content type is supported by the following data types: `Double`, `Long`, and `Date`.</span></span>  
  
## <a name="table"></a><span data-ttu-id="62f0f-157">表</span><span class="sxs-lookup"><span data-stu-id="62f0f-157">Table</span></span>  
 <span data-ttu-id="62f0f-158">“table \*\* ”内容类型指示列包含其中有一列或多列以及一行或多行的另一个数据表。</span><span class="sxs-lookup"><span data-stu-id="62f0f-158">The *table* content type indicates that the column contains another data table, with one or more columns and one or more rows.</span></span> <span data-ttu-id="62f0f-159">对于事例表中的任意特定行，此列可以包含多个值，所有的值均与父事例记录相关。</span><span class="sxs-lookup"><span data-stu-id="62f0f-159">For any particular row in the case table, this column can contain multiple values, all related to the parent case record.</span></span> <span data-ttu-id="62f0f-160">例如，如果主事例表包含一个客户列表，则可能有多个包含嵌套表的列，例如 **ProductsPurchased** 列和 **Hobbies** 列，嵌套表在 ProductsPurchased 列中列出了此客户过去购买的产品，而 Hobbies 列则列出了该客户的兴趣。</span><span class="sxs-lookup"><span data-stu-id="62f0f-160">For example, if the main case table contains a listing of customers, you could have several columns that contain nested tables, such as a **ProductsPurchased** column, where the nested table lists products bought by this customer in the past, and a **Hobbies** column that lists the interests of the customer.</span></span>  
  
 <span data-ttu-id="62f0f-161">此列的数据类型始终为 `Table`。</span><span class="sxs-lookup"><span data-stu-id="62f0f-161">The data type of this column is always `Table`.</span></span>  
  
## <a name="cyclical"></a><span data-ttu-id="62f0f-162">Cyclical</span><span class="sxs-lookup"><span data-stu-id="62f0f-162">Cyclical</span></span>  
 <span data-ttu-id="62f0f-163">“cyclical \*\* ”内容类型意味着列包含表示循环有序集的值。</span><span class="sxs-lookup"><span data-stu-id="62f0f-163">The *cyclical* content type means that the column contains values that represent a cyclical ordered set.</span></span> <span data-ttu-id="62f0f-164">例如，一周内顺序编号的七天便是循环有序集，因为第一天紧跟第七天。</span><span class="sxs-lookup"><span data-stu-id="62f0f-164">For example, the numbered days of the week is a cyclical ordered set, because day number one follows day number seven.</span></span>  
  
 <span data-ttu-id="62f0f-165">循环列就内容类型而言既有序又离散。</span><span class="sxs-lookup"><span data-stu-id="62f0f-165">Cyclical columns are considered both ordered and discrete in terms of content type.</span></span>  
  
 <span data-ttu-id="62f0f-166">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中所有的数据挖掘数据类型都支持此内容类型。</span><span class="sxs-lookup"><span data-stu-id="62f0f-166">This content type is supported by all the data mining data types in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="62f0f-167">但是，大多数算法将循环值视为离散值，不会进行特殊处理。</span><span class="sxs-lookup"><span data-stu-id="62f0f-167">However, most algorithms treat cyclical values as discrete values and do not perform special processing.</span></span>  
  
## <a name="ordered"></a><span data-ttu-id="62f0f-168">已订购</span><span class="sxs-lookup"><span data-stu-id="62f0f-168">Ordered</span></span>  
 <span data-ttu-id="62f0f-169">“Ordered \*\* ”内容类型也指示列包含定义序列或顺序的值。</span><span class="sxs-lookup"><span data-stu-id="62f0f-169">The *Ordered* content type also indicates that the column contains values that define a sequence or order.</span></span> <span data-ttu-id="62f0f-170">但是，在此内容类型中，用于排序的值并不表示该集中值之间的任何差或量级关系。</span><span class="sxs-lookup"><span data-stu-id="62f0f-170">However, in this content type the values used for ordering do not imply any distance or magnitude relationship between values in the set.</span></span> <span data-ttu-id="62f0f-171">例如，如果有序属性列包含按照等级顺序从一到五排列的有关技术等级的信息，则技术等级之间的差并不包含什么暗示信息；技术等级五不一定比技术等级一好五倍。</span><span class="sxs-lookup"><span data-stu-id="62f0f-171">For example, if an ordered attribute column contains information about skill levels in rank order from one to five, there is no implied information in the distance between skill levels; a skill level of five is not necessarily five times better than a skill level of one.</span></span>  
  
 <span data-ttu-id="62f0f-172">有序属性列就内容类型而言是离散的。</span><span class="sxs-lookup"><span data-stu-id="62f0f-172">Ordered attribute columns are considered to be discrete in terms of content type.</span></span>  
  
 <span data-ttu-id="62f0f-173">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中所有的数据挖掘数据类型都支持此内容类型。</span><span class="sxs-lookup"><span data-stu-id="62f0f-173">This content type is supported by all the data mining data types in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="62f0f-174">但是，大多数算法会将有序值视为离散值，不会进行特殊处理。</span><span class="sxs-lookup"><span data-stu-id="62f0f-174">However, however, most algorithms treat ordered values as discrete values and do not perform special processing.</span></span>  
  
## <a name="classified"></a><span data-ttu-id="62f0f-175">Classified</span><span class="sxs-lookup"><span data-stu-id="62f0f-175">Classified</span></span>  
 <span data-ttu-id="62f0f-176">除了前面列出的可通用于所有模型的内容类型以外，对于某些数据类型，还可以使用已分类列定义内容类型。</span><span class="sxs-lookup"><span data-stu-id="62f0f-176">In addition to the preceding content types that are in common use with all models, for some data types you can use classified columns to define content types.</span></span> <span data-ttu-id="62f0f-177">有关已分类列的详细信息，请参阅[已分类列（数据挖掘）](classified-columns-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="62f0f-177">For more information about classified columns, see [Classified Columns &#40;Data Mining&#41;](classified-columns-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f0f-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62f0f-178">See Also</span></span>  
 <span data-ttu-id="62f0f-179">[内容类型 &#40;DMX&#41;](/sql/dmx/content-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="62f0f-179">[Content Types &#40;DMX&#41;](/sql/dmx/content-types-dmx) </span></span>  
 <span data-ttu-id="62f0f-180">[数据挖掘 &#40;的数据类型&#41;](data-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="62f0f-180">[Data Types &#40;Data Mining&#41;](data-types-data-mining.md) </span></span>  
 <span data-ttu-id="62f0f-181">[DMX&#41;的数据类型 &#40;](/sql/dmx/data-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="62f0f-181">[Data Types &#40;DMX&#41;](/sql/dmx/data-types-dmx) </span></span>  
 <span data-ttu-id="62f0f-182">[更改挖掘结构的属性](change-the-properties-of-a-mining-structure.md) </span><span class="sxs-lookup"><span data-stu-id="62f0f-182">[Change the Properties of a Mining Structure](change-the-properties-of-a-mining-structure.md) </span></span>  
 [<span data-ttu-id="62f0f-183">挖掘结构列</span><span class="sxs-lookup"><span data-stu-id="62f0f-183">Mining Structure Columns</span></span>](mining-structure-columns.md)  
  
  
