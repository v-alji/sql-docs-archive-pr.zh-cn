---
title: 为数据挖掘选择数据 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content type [data mining]
- nested tables
- key [data mining]
- continuous values
- key sequence [data mining]
- table data type
- key time [data mining]
- discrete values
- discretized
ms.assetid: 7c72d80e-913c-4bbe-b258-444294a78838
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b655e344bd9976c30781efb7be41a3fc602174d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579270"
---
# <a name="choosing-data-for-data-mining"></a><span data-ttu-id="a00f0-102">为数据挖掘选择数据</span><span class="sxs-lookup"><span data-stu-id="a00f0-102">Choosing Data for Data Mining</span></span>
  <span data-ttu-id="a00f0-103">开始数据挖掘时，您可能会问 "我需要多少数据？"</span><span class="sxs-lookup"><span data-stu-id="a00f0-103">As you start data mining, you might ask "How much data do I need?"</span></span> <span data-ttu-id="a00f0-104">或者 "在清理数据或设置数据格式时，我是否需要了解一些特殊要求？"</span><span class="sxs-lookup"><span data-stu-id="a00f0-104">or "Are there any special requirements I should know about when cleaning or formatting my data?"</span></span>  
  
 <span data-ttu-id="a00f0-105">具体而言，刚接触数据挖掘的人通常会遇到与 Excel 数据有关的问题，如需要在列中一致地设置数据格式、清除缺失值或对数字装箱。</span><span class="sxs-lookup"><span data-stu-id="a00f0-105">In particular, people new to data mining often run into problems with Excel data, such as needing to format data consistently within columns, cleaning up missing values, or binning numbers.</span></span> <span data-ttu-id="a00f0-106">本节还会列出特定模型类型的数据要求。</span><span class="sxs-lookup"><span data-stu-id="a00f0-106">This section also lists data requirements for specific kinds of models.</span></span>  
  
 [<span data-ttu-id="a00f0-107">选择数据</span><span class="sxs-lookup"><span data-stu-id="a00f0-107">Choosing Data</span></span>](#bkmk_ChoosingData)  
  
 [<span data-ttu-id="a00f0-108">常见数据问题</span><span class="sxs-lookup"><span data-stu-id="a00f0-108">Common Data Problems</span></span>](#bkmk_CommonDataProblems)  
  
 [<span data-ttu-id="a00f0-109">其他数据要求</span><span class="sxs-lookup"><span data-stu-id="a00f0-109">Other Data Requirements</span></span>](#bkmk_OtherRequirements)  
  
##  <a name="choosing-data"></a><a name="bkmk_ChoosingData"></a><span data-ttu-id="a00f0-110">选择数据</span><span class="sxs-lookup"><span data-stu-id="a00f0-110">Choosing Data</span></span>  
 <span data-ttu-id="a00f0-111">选择分析数据可能是数据挖掘过程中最重要的部分，甚至比算法选择更重要。</span><span class="sxs-lookup"><span data-stu-id="a00f0-111">Selection of the data used for analysis is perhaps the most important part of the data mining process, more so even than the selection of an algorithm.</span></span> <span data-ttu-id="a00f0-112">原因在于，数据挖掘通常不是由假设驱动，而是由数据驱动。</span><span class="sxs-lookup"><span data-stu-id="a00f0-112">The reason is that data mining is generally not hypothesis-driven, but data-driven.</span></span> <span data-ttu-id="a00f0-113">数据挖掘可以接收数据并发现新关联（否则完全无法发现任何模式），而不是提前选择和测试变量（传统统计建模可能会这样做）。</span><span class="sxs-lookup"><span data-stu-id="a00f0-113">Rather than select and test variables in advance, as you might with traditional statistical modeling, data mining can take data and discover new correlations (or fail to discover any patterns at all).</span></span> <span data-ttu-id="a00f0-114">数据的质量和数量可能会显著影响结果。</span><span class="sxs-lookup"><span data-stu-id="a00f0-114">The quality and amount of your data can have a significant effect on results.</span></span>  
  
 <span data-ttu-id="a00f0-115">一般而言，请遵守以下规则：</span><span class="sxs-lookup"><span data-stu-id="a00f0-115">In general, observe the following rules:</span></span>  
  
-   <span data-ttu-id="a00f0-116">获取尽可能干净的数据。</span><span class="sxs-lookup"><span data-stu-id="a00f0-116">Get as much clean data as possible.</span></span>  
  
-   <span data-ttu-id="a00f0-117">尝试任何模型之前执行数据事件探查。</span><span class="sxs-lookup"><span data-stu-id="a00f0-117">Conduct data profiling before you try any models.</span></span> <span data-ttu-id="a00f0-118">需要先理解数据，然后才能发现其中的含义。</span><span class="sxs-lookup"><span data-stu-id="a00f0-118">You need to understand your data before you can derive meaning from it.</span></span> <span data-ttu-id="a00f0-119">至少：</span><span class="sxs-lookup"><span data-stu-id="a00f0-119">At minimum:</span></span>  
  
    1.  <span data-ttu-id="a00f0-120">使用外接程序中的工具查找最大值和最小值、最常见的值和平均值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-120">Use the tools in the add-ins to find your maximum and minimum values, the most common values, and average values.</span></span>  
  
    2.  <span data-ttu-id="a00f0-121">填写缺失值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-121">Fill in missing values.</span></span> <span data-ttu-id="a00f0-122">外接程序（以及一些算法）可提供用于输入缺失值的工具。</span><span class="sxs-lookup"><span data-stu-id="a00f0-122">The add-ins (as well as some algorithms) provide tools for imputing missing values.</span></span>  
  
    3.  <span data-ttu-id="a00f0-123">尽可能更正错误的数据。</span><span class="sxs-lookup"><span data-stu-id="a00f0-123">Correct bad data whenever possible.</span></span> <span data-ttu-id="a00f0-124">数据挖掘项目经常充当新数据质量方案的推动力。</span><span class="sxs-lookup"><span data-stu-id="a00f0-124">Data mining projects often serve as the impetus for new data quality initiatives.</span></span>  
  
-   <span data-ttu-id="a00f0-125">尝试生成测试模型，通过这种方式查找数据问题。</span><span class="sxs-lookup"><span data-stu-id="a00f0-125">Try building a test model and find data problems that way.</span></span> <span data-ttu-id="a00f0-126">举例来说，在查看结果时，您可能会发现，销售预测所依据的数据因货币换算错误存在异常。</span><span class="sxs-lookup"><span data-stu-id="a00f0-126">As you look at the results, you might find, for example, that sales projections are based on anomalous data due to a currency conversion error.</span></span>  
  
-   <span data-ttu-id="a00f0-127">尝试将数据转换为不同格式，或尝试将数字存入桶。</span><span class="sxs-lookup"><span data-stu-id="a00f0-127">Try casting your data into different formats, or try bucketing numbers.</span></span> <span data-ttu-id="a00f0-128">转换数据时，经常会出现模式。</span><span class="sxs-lookup"><span data-stu-id="a00f0-128">Patterns often emerge when data is transformed.</span></span>  
  
     <span data-ttu-id="a00f0-129">例如，呼叫中心的服务级别可能会受星期几影响，如果仅使用日期时间值，则不会看到这种模式。</span><span class="sxs-lookup"><span data-stu-id="a00f0-129">For example, the service level at the call center might be affected by the day of the week, which you would not see if you were using only the datetime values.</span></span> <span data-ttu-id="a00f0-130">如果以 10 天周期生成（而不是以每周或每天为单位），预测效果可能更好。</span><span class="sxs-lookup"><span data-stu-id="a00f0-130">Forecasts might be better when generated on 10-day cycles rather than weekly or daily units.</span></span>  
  
-   <span data-ttu-id="a00f0-131">将数字置于合适的箱中，减少要分析的值的数量。</span><span class="sxs-lookup"><span data-stu-id="a00f0-131">Put numbers in appropriate bins, to reduce the number of possible values for analysis.</span></span>  
  
-   <span data-ttu-id="a00f0-132">创建多个版本的数据，生成多个模型。</span><span class="sxs-lookup"><span data-stu-id="a00f0-132">Create multiple versions of your data and build multiple models.</span></span>  
  
 <span data-ttu-id="a00f0-133">有关如何选择、修改和检查数据的其他提示，请参阅[数据挖掘准备工作表](checklist-of-preparation-for-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a00f0-133">For additional tips on how to select, modify, and review data, see [Checklist of Preparation for Data Mining](checklist-of-preparation-for-data-mining.md).</span></span>  
  
### <a name="how-much-data-do-i-need"></a><span data-ttu-id="a00f0-134">我需要多少数据？</span><span class="sxs-lookup"><span data-stu-id="a00f0-134">How Much Data Do I Need?</span></span>  
 <span data-ttu-id="a00f0-135">经验法则是，对于最简单的模型类型和方案，数据行数不小于 50-100 行。</span><span class="sxs-lookup"><span data-stu-id="a00f0-135">A rule of thumb is to never have less than 50-100 rows of data for the simplest models types and scenarios.</span></span> <span data-ttu-id="a00f0-136">例如，如果使用 Naïve Bayes 模型预测单个属性，并且数据集格式正确，使用 50-100 行数据就可能生成相当准确的预测。</span><span class="sxs-lookup"><span data-stu-id="a00f0-136">For example, if you are predicting a single attribute using a Naïve Bayes model and the data set is well-formed, you might be able to generate fairly accurate predictions using 50-100 rows of data.</span></span>  
  
 <span data-ttu-id="a00f0-137">对于关联模型，通常需要更多数据-如果要分析许多属性（如产品间的关联），则可能无法满足几千行的要求。</span><span class="sxs-lookup"><span data-stu-id="a00f0-137">For association models, you typically need much more data - a thousand rows might not suffice if you are analyzing many attributes, such as associations among products.</span></span> <span data-ttu-id="a00f0-138">如果数据集太大或太小，通过将行合为类别有时可以获得更好的结果。</span><span class="sxs-lookup"><span data-stu-id="a00f0-138">If your data set is too big or too small, you can sometimes achieve better results by collapsing rows into categories.</span></span> <span data-ttu-id="a00f0-139">例如，可以对产品分类，而不是分析各个产品间的关联。</span><span class="sxs-lookup"><span data-stu-id="a00f0-139">For example, instead of analyzing associations among individual products, you could categorize the products.</span></span>  
  
 <span data-ttu-id="a00f0-140">如果数据集大小合理，应更注重数据质量而不是添加越来越多的数据。</span><span class="sxs-lookup"><span data-stu-id="a00f0-140">If you have a data set of a reasonable size, focus more on data quality rather than adding more and more data.</span></span> <span data-ttu-id="a00f0-141">达到一定数据量后，会发现统计上有效的所有模式，添加更多数据不会提高其有效性。</span><span class="sxs-lookup"><span data-stu-id="a00f0-141">After a point, all the patterns that are statistically valid will have been found, and adding more data does not improve their validity.</span></span> <span data-ttu-id="a00f0-142">相反，添加更多数据，有时可能引入意外关联。</span><span class="sxs-lookup"><span data-stu-id="a00f0-142">Conversely, as you add more data sometimes you can introduce accidental correlations.</span></span>  
  
### <a name="discrete-vs-continuous-numbers"></a><span data-ttu-id="a00f0-143">离散和连续数字</span><span class="sxs-lookup"><span data-stu-id="a00f0-143">Discrete vs. Continuous Numbers</span></span>  
 <span data-ttu-id="a00f0-144">*离散*列包含有限数量的值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-144">A *discrete* column contains a finite number of values.</span></span> <span data-ttu-id="a00f0-145">例如，文本通常被视为离散值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-145">For example, text is always treated as discrete values.</span></span>  
  
 <span data-ttu-id="a00f0-146">离散值有一些重要属性。</span><span class="sxs-lookup"><span data-stu-id="a00f0-146">There are some important attributes to discrete values.</span></span> <span data-ttu-id="a00f0-147">例如，如果将数字视为离散值，则它们之间不隐含任何顺序，您无法对数字计算平均值或总和。</span><span class="sxs-lookup"><span data-stu-id="a00f0-147">For example, if you treat numbers as discrete, no order is implied among them, and you cannot average or sum the numbers.</span></span> <span data-ttu-id="a00f0-148">电话区号就是离散数值数据，不会用来执行数学运算。</span><span class="sxs-lookup"><span data-stu-id="a00f0-148">Telephone area codes are a good example of discrete numeric data that you would never use to perform mathematical operations.</span></span>  
  
 <span data-ttu-id="a00f0-149">离散值有时候称作类别值，因为您可以按离散值对一组数据进行分组，而对于按无限序列排列的数值，则不能按其对数据进行分组。</span><span class="sxs-lookup"><span data-stu-id="a00f0-149">Discrete values are sometimes referred to as categorical values, because you can group a set of data by them, whereas you cannot with numbers arranged in an infinite series.</span></span>  
  
 <span data-ttu-id="a00f0-150">如果值是明确分开并且不可能有小数值或小数值没有用时，您也可以确定将数字视为离散值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-150">You might also decide to treat numbers as discrete when the values are clearly separated, and there is no possibility of fractional values, or fractional values are not useful.</span></span>  
  
 <span data-ttu-id="a00f0-151">*连续*数值数据可包含无限个小数值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-151">*Continuous* numeric data can contain an infinite number of fractional values.</span></span> <span data-ttu-id="a00f0-152">收入列即为连续属性列的示例。</span><span class="sxs-lookup"><span data-stu-id="a00f0-152">An income column is an example of a continuous attribute column.</span></span> <span data-ttu-id="a00f0-153">如果您指定某一列为数值，则该列中的每个值都必须是数值，只有 null 除外。</span><span class="sxs-lookup"><span data-stu-id="a00f0-153">If you specify that a column is numeric, every value in that column must be a number, except for nulls.</span></span> <span data-ttu-id="a00f0-154">请注意，在 Excel 中，可以考虑时间戳以及可转换为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据类型的任何其他日期时间表示形式。</span><span class="sxs-lookup"><span data-stu-id="a00f0-154">Note that in Excel, timestamps and any other date-time representation that can be converted to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data type can be considered.</span></span>  
  
 <span data-ttu-id="a00f0-155">**将数字转换为分类变量**</span><span class="sxs-lookup"><span data-stu-id="a00f0-155">**Converting Numbers to Categorical Variables**</span></span>  
  
 <span data-ttu-id="a00f0-156">因为列包含数值并不意味着您应该将它们视作连续数值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-156">Just because a column contains numbers does not mean that you should treat them as continuous numbers.</span></span> <span data-ttu-id="a00f0-157">*离散*化为分析提供了许多好处。</span><span class="sxs-lookup"><span data-stu-id="a00f0-157">*Discretization* provides many advantages for analysis.</span></span> <span data-ttu-id="a00f0-158">好处之一是缩小了问题空间。</span><span class="sxs-lookup"><span data-stu-id="a00f0-158">One is that the problem space is reduced.</span></span> <span data-ttu-id="a00f0-159">另一好处是数字有时不适合表示结果。</span><span class="sxs-lookup"><span data-stu-id="a00f0-159">Another is that sometimes numbers are not the appropriate way to express a result.</span></span>  
  
 <span data-ttu-id="a00f0-160">例如，一个家庭的孩子数既可视为连续值，也可视为离散值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-160">For example, the number of children per household can be treated either as a continuous or discrete value.</span></span> <span data-ttu-id="a00f0-161">因为家庭中不可能有 2.5 个孩子，有 3 个或更多孩子的家庭的行为方式可能与有 2 个孩子的家庭非常不同，所以将此数字视为类别可以获得更好的结果。</span><span class="sxs-lookup"><span data-stu-id="a00f0-161">Since it is not possible to have 2.5 children in the household, and households with 3 or more children can behave very differently from households with 2 children, you might get better results by treating this number as a category.</span></span> <span data-ttu-id="a00f0-162">但是，如果要生成回归模型或由于其他原因需要平均值（如每个家庭 1.357 个孩子），则可使用连续数字数据类型。</span><span class="sxs-lookup"><span data-stu-id="a00f0-162">However, if you are building a regression model or otherwise require an average (such as 1.357 children per household), then you would use a continuous number data type.</span></span>  
  
 <span data-ttu-id="a00f0-163">如果创建一个包含连续数据的挖掘模型，之后又希望将列视为离散的，则是不可能的。</span><span class="sxs-lookup"><span data-stu-id="a00f0-163">It is not possible to create a mining model that has continuous data and then treat the column as discrete later.</span></span> <span data-ttu-id="a00f0-164">两个数据集必须以不同的方式处理，作为单独的挖掘结构在后端进行处理。</span><span class="sxs-lookup"><span data-stu-id="a00f0-164">The two data sets must be processed differently and are handled on the backend as separate mining structures.</span></span> <span data-ttu-id="a00f0-165">如果不确定数据的正确处理方式，应创建单独的模型以不同方式处理数据。</span><span class="sxs-lookup"><span data-stu-id="a00f0-165">If you are unsure of the right way to handle the data, you should create separate models that handle the data differently.</span></span> <span data-ttu-id="a00f0-166">在任何情况下，这都是获得有关数据的不同观点（可能还有不同结果）的好方法。</span><span class="sxs-lookup"><span data-stu-id="a00f0-166">In any case, this is a good way to get a different perspective on your data, and perhaps different results.</span></span>  
  
 <span data-ttu-id="a00f0-167">**将数字转换为文本**</span><span class="sxs-lookup"><span data-stu-id="a00f0-167">**Converting Numbers to Text**</span></span>  
  
 <span data-ttu-id="a00f0-168">诸如男性和女性之类的应该是离散的非常常见的值表示为数值数据（如使用标签 1 和 2）。</span><span class="sxs-lookup"><span data-stu-id="a00f0-168">Very often values that should be discrete, such as Male and Female, are represented as numeric data, using the labels 1 and 2.</span></span> <span data-ttu-id="a00f0-169">通常执行此编码是为了简化数据输入或者节省数据库的存储空间，不过此编码可能导致值的性质和意义不明确。</span><span class="sxs-lookup"><span data-stu-id="a00f0-169">Typically this coding is performed to simplify data entry, or to save storage space in a database, but the coding can lead to ambiguity about the nature or meaning of the values.</span></span> <span data-ttu-id="a00f0-170">此外，由于离散值以数字形式存储，当您在应用程序之间移动数据时，可能会遇到数据类型转换错误，这些值可能被计算或被视为连续值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-170">Moreover, because discrete values are stored as numbers, as you move data between applications you may encounter data type conversion errors, and the values might be calculated or otherwise treated as continuous.</span></span> <span data-ttu-id="a00f0-171">若要避免此类问题，应该在开始数据挖掘之前，将数值标签转换回离散的文本标签。</span><span class="sxs-lookup"><span data-stu-id="a00f0-171">To prevent such problems, before beginning data mining, you should convert the numeric labels back to discrete text labels.</span></span>  
  
 <span data-ttu-id="a00f0-172">**对数字装箱**</span><span class="sxs-lookup"><span data-stu-id="a00f0-172">**Binning Numbers**</span></span>  
  
 <span data-ttu-id="a00f0-173">虽然原则上的所有数字都是无限的，因而是连续的，但在对信息进行建模时，您可能会发现，更有效的方法是*离散化*或将可用值*装箱*。</span><span class="sxs-lookup"><span data-stu-id="a00f0-173">Although all numbers in principle are infinite and are therefore continuous, when you are modeling information you might find it more effective to *discretize* or *bin* the available values.</span></span>  
  
 <span data-ttu-id="a00f0-174">您可以通过许多方式将数据装箱：</span><span class="sxs-lookup"><span data-stu-id="a00f0-174">You can bin data in many ways:</span></span>  
  
-   <span data-ttu-id="a00f0-175">指定数目有限的存储桶并且让算法对存储桶中的值进行排序。</span><span class="sxs-lookup"><span data-stu-id="a00f0-175">Specify a finite number of buckets and let the algorithm sort the values into buckets.</span></span>  
  
-   <span data-ttu-id="a00f0-176">通过创建某些分组集合（具有业务上的意义或者易于使用），自己预先对值进行分组。</span><span class="sxs-lookup"><span data-stu-id="a00f0-176">Pre-group them yourself, by creating some set of groupings that either has business meaning or is easier to work with.</span></span> <span data-ttu-id="a00f0-177">使用此方法，您常常会丧失值的真正分布，但范围更易于用户读取。</span><span class="sxs-lookup"><span data-stu-id="a00f0-177">With this approach, you often miss the true distribution of values, but the ranges are easier for users to read.</span></span>  
  
-   <span data-ttu-id="a00f0-178">让算法确定存储桶的最佳数目以及值的分布。</span><span class="sxs-lookup"><span data-stu-id="a00f0-178">Let the algorithm determine both the optimum number of buckets and the distribution of values.</span></span> <span data-ttu-id="a00f0-179">这是大多数工具中的默认设置，但你可以在**数据挖掘**工具栏向导中覆盖这些默认值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-179">This is the default in most tools, but you can override these defaults in the **Data Mining** toolbar wizards.</span></span>  
  
-   <span data-ttu-id="a00f0-180">将值逼近中心平均值或代表值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-180">Approximating values to a central mean or representative value.</span></span>  
  
##  <a name="common-data-problems"></a><a name="bkmk_CommonDataProblems"></a><span data-ttu-id="a00f0-181">常见数据问题</span><span class="sxs-lookup"><span data-stu-id="a00f0-181">Common Data Problems</span></span>  
  
### <a name="excel-number-formats"></a><span data-ttu-id="a00f0-182">Excel 数字格式</span><span class="sxs-lookup"><span data-stu-id="a00f0-182">Excel Number Formats</span></span>  
 <span data-ttu-id="a00f0-183">Excel 是一种易于使用的工具，因为它是包容性的，可以在任何位置放置几乎任何类型的数据！</span><span class="sxs-lookup"><span data-stu-id="a00f0-183">Excel is an easy tool to use because it is forgiving - you can put just about any kind of data anywhere!</span></span> <span data-ttu-id="a00f0-184">但是，在您开始查找模式和对相关性进行分析之前，需要对您的数据强制某种结构或某些约束。</span><span class="sxs-lookup"><span data-stu-id="a00f0-184">However, before you begin to look for patterns and analyze correlations, you need to impose some structure or constraints on your data.</span></span>  
  
 <span data-ttu-id="a00f0-185">默认情况下，在将数值数据导入 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 时，这些数字会存储为带两位小数的小数格式。</span><span class="sxs-lookup"><span data-stu-id="a00f0-185">By default, when you import numeric data into [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel, the numbers are stored in a decimal format with two decimal places.</span></span> <span data-ttu-id="a00f0-186">如果此数字格式不符合您的要求，您应该将其更改为其他数值格式，也可更改小数位数。</span><span class="sxs-lookup"><span data-stu-id="a00f0-186">If this is not an appropriate number format, you should change to another numeric format, or change the number of decimal places.</span></span>  
  
 <span data-ttu-id="a00f0-187">一种选择是使用重新[标记](relabel-sql-server-data-mining-add-ins.md)工具来更改数字显示或分组的方式。</span><span class="sxs-lookup"><span data-stu-id="a00f0-187">One option is to use the [Relabel](relabel-sql-server-data-mining-add-ins.md) tool to change the way that numbers are displayed or grouped.</span></span>  
  
 <span data-ttu-id="a00f0-188">但是，如果数据太复杂，无法使用重新**标记**工具进行处理，则可以使用 Excel 中的数值函数将数据转换为离散范围，将结果保存到单独的列中，然后使用离散化列作为分类。</span><span class="sxs-lookup"><span data-stu-id="a00f0-188">However, if your data is too complex to process with the **Relabel** tool, you can use the numeric functions in Excel to convert your data to discrete ranges, save that result into a separate column, and then use the discretized column for classification instead.</span></span>  
  
 <span data-ttu-id="a00f0-189">例如，如果要分析赛跑结果并希望按照完成时间（以分钟为单位）对赛跑者进行分组，则您可以向上舍入为最接近的分钟数并将该舍入值保存到新列中。</span><span class="sxs-lookup"><span data-stu-id="a00f0-189">For example, if you are analyzing race results and want to group racers by their finish times in minutes, you can round up to the nearest minute and save that rounded value to a new column.</span></span> <span data-ttu-id="a00f0-190">您还可以使用 `MINUTE` 函数仅提取分钟值，然后将该值保存到新列以供分析使用。</span><span class="sxs-lookup"><span data-stu-id="a00f0-190">You could also extract only the minute value by using the `MINUTE` function, and then save that value to a new column for use in analysis.</span></span>  
  
### <a name="discretizing-numbers-and-dates-in-excel"></a><span data-ttu-id="a00f0-191">在 Excel 中离散化数字和日期</span><span class="sxs-lookup"><span data-stu-id="a00f0-191">Discretizing Numbers and Dates in Excel</span></span>  
 <span data-ttu-id="a00f0-192">默认情况下，Excel 中的数值数据以 `Double` 格式存储。</span><span class="sxs-lookup"><span data-stu-id="a00f0-192">By default, numeric data in Excel is stored as a `Double`.</span></span> <span data-ttu-id="a00f0-193">日期和时间也以数值格式存储。</span><span class="sxs-lookup"><span data-stu-id="a00f0-193">Dates and times also are stored in a numeric format.</span></span> <span data-ttu-id="a00f0-194">如果您需要使数字或日期离散化以进行数据挖掘，则应在生成数据挖掘模型之前添加新列或者预先将日期和数字转换为其他格式。</span><span class="sxs-lookup"><span data-stu-id="a00f0-194">If you need to discretize numbers or dates for data mining, you should add new columns before you build your data mining model, or convert dates and numbers to another format beforehand.</span></span>  
  
### <a name="scientific-number-formats"></a><span data-ttu-id="a00f0-195">科学记数数字格式</span><span class="sxs-lookup"><span data-stu-id="a00f0-195">Scientific Number Formats</span></span>  
 <span data-ttu-id="a00f0-196">数据挖掘工具通常以科学记数法输出概率，以表示非常大或非常小的数字。</span><span class="sxs-lookup"><span data-stu-id="a00f0-196">The data mining tools often output probabilities in scientific notation, to represent numbers that are very large or very small.</span></span> <span data-ttu-id="a00f0-197">如果您不熟悉科学记数法，只需更改单元格格式即可以另一种格式显示这些数字。</span><span class="sxs-lookup"><span data-stu-id="a00f0-197">If you are not familiar with scientific notation, you can easily display these numbers in another format by simply changing the cell formatting.</span></span>  
  
##### <a name="to-change-scientific-notation-to-a-decimal-numeric-format"></a><span data-ttu-id="a00f0-198">将科学记数改为小数数值格式</span><span class="sxs-lookup"><span data-stu-id="a00f0-198">To change scientific notation to a decimal numeric format</span></span>  
  
1.  <span data-ttu-id="a00f0-199">在 Excel 数据表中，突出显示包含以科学记数法表示的数字的列或单元格。</span><span class="sxs-lookup"><span data-stu-id="a00f0-199">In the Excel data table, highlight the column or cell that contains the number in scientific notation.</span></span>  
  
2.  <span data-ttu-id="a00f0-200">右键单击并从快捷菜单中选择 "**设置单元格格式**"。</span><span class="sxs-lookup"><span data-stu-id="a00f0-200">Right-click and select **Format cells** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="a00f0-201">在 "**类别**" 列表中，选择 "**数字**"。</span><span class="sxs-lookup"><span data-stu-id="a00f0-201">In the **Category** list, select **Number**.</span></span>  
  
4.  <span data-ttu-id="a00f0-202">增加小数位数的个数。</span><span class="sxs-lookup"><span data-stu-id="a00f0-202">Increase the number of decimal places.</span></span> <span data-ttu-id="a00f0-203">以科学记数法表示的概率通常非常小。</span><span class="sxs-lookup"><span data-stu-id="a00f0-203">A probability that is represented in scientific notation is generally very small.</span></span>  
  
     <span data-ttu-id="a00f0-204">只有数字的显示方式会发生变化，基础值不会变化。</span><span class="sxs-lookup"><span data-stu-id="a00f0-204">Only the display of the number is changed, not the underlying value.</span></span>  
  
### <a name="working-with-dates-and-times"></a><span data-ttu-id="a00f0-205">处理日期和时间</span><span class="sxs-lookup"><span data-stu-id="a00f0-205">Working with Dates and Times</span></span>  
 <span data-ttu-id="a00f0-206">如果您的 Excel 表中包含日期，并且您将该列用于输入或预测，则您可能会收到意外结果，具体取决于日期信息或时间信息的格式设置。</span><span class="sxs-lookup"><span data-stu-id="a00f0-206">When you have dates in an Excel table and use the column either as input or for prediction, you might receive unexpected results, depending on how the date or time information is formatted.</span></span> <span data-ttu-id="a00f0-207">例如，当你使用 "**检测类别**" 或 "**分类**" 并包含包含日期的列时，日期会分类为包含多个小数位的数字。</span><span class="sxs-lookup"><span data-stu-id="a00f0-207">For example, when you use **Detect Categories** or **Classify** and include a column that contains dates, the dates are categorized as numbers with many decimal places.</span></span> <span data-ttu-id="a00f0-208">这并不是错误；这是基础数据的精确表示形式。</span><span class="sxs-lookup"><span data-stu-id="a00f0-208">This is not an error; it is an accurate representation of the underlying data.</span></span> <span data-ttu-id="a00f0-209">数据挖掘算法使用的是基础存储格式，而不是显示格式。</span><span class="sxs-lookup"><span data-stu-id="a00f0-209">The data mining algorithm works with the underlying storage format, not the display format.</span></span>  
  
 <span data-ttu-id="a00f0-210">如果您在使用日期时遇到困难，希望使用如月或天这样的常规分组方式来分析日期，则可使用 Excel 中的 DATE 函数，将年、月或日提取到单独一列中，然后使用该列进行分类。</span><span class="sxs-lookup"><span data-stu-id="a00f0-210">If you have difficulty working with dates and want to analyze dates using such common-sense groupings as month or day, you can use the DATE functions in Excel to extract the year, month, or day into a separate column and then use that column for classification instead.</span></span>  
  
##  <a name="other-data-requirements"></a><a name="bkmk_OtherRequirements"></a><span data-ttu-id="a00f0-211">其他数据要求</span><span class="sxs-lookup"><span data-stu-id="a00f0-211">Other Data Requirements</span></span>  
  
### <a name="requirements-by-algorithm-type"></a><span data-ttu-id="a00f0-212">算法类型要求</span><span class="sxs-lookup"><span data-stu-id="a00f0-212">Requirements by Algorithm Type</span></span>  
 <span data-ttu-id="a00f0-213">某些在外接程序中使用的算法需要特定的数据类型或内容类型才能创建模型。</span><span class="sxs-lookup"><span data-stu-id="a00f0-213">Some algorithms that are used in the add-ins require specific data types or content types to create a model.</span></span>  
  
 <span data-ttu-id="a00f0-214">**Naïve Bayes 模型**</span><span class="sxs-lookup"><span data-stu-id="a00f0-214">**Naïve Bayes models**</span></span>  
  
-   <span data-ttu-id="a00f0-215">[!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes 算法不能使用连续列作为输入。</span><span class="sxs-lookup"><span data-stu-id="a00f0-215">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes algorithm cannot use continuous columns as input.</span></span> <span data-ttu-id="a00f0-216">这意味着，您必须对数字装箱，或者如果值足够少，可以按离散值处理。</span><span class="sxs-lookup"><span data-stu-id="a00f0-216">That means you must either bin numbers, or if there are few enough values, handle them as discrete values.</span></span>  
  
-   <span data-ttu-id="a00f0-217">此类模型也不能预测连续值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-217">This type of model also cannot predict continuous values.</span></span> <span data-ttu-id="a00f0-218">因此，如果要预测连续数字（如收入），应先将值装箱到有意义的范围中。</span><span class="sxs-lookup"><span data-stu-id="a00f0-218">Therefore, if you want to predict a continuous number such as income (for example) you should first bin the values into meaningful ranges.</span></span> <span data-ttu-id="a00f0-219">如果不确定合适的范围，可以使用聚类分析算法确定数据中的数字聚类。</span><span class="sxs-lookup"><span data-stu-id="a00f0-219">If you are not sure what the appropriate ranges are, you can use the clustering algorithm to identify clumps of numbers in your data.</span></span>  
  
-   <span data-ttu-id="a00f0-220">如果使用基于此算法的向导 (如[&#40;表分析工具 "Excel&#41;) 分析关键影响因素](analyze-key-influencers-table-analysis-tools-for-excel.md)，则向导将装箱连续的列。</span><span class="sxs-lookup"><span data-stu-id="a00f0-220">When you use a wizard based on this algorithm (such as [Analyze Key Influencers &#40;Table Analysis Tools for Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)), columns that are continuous will be binned by the wizard you.</span></span>  
  
-   <span data-ttu-id="a00f0-221">如果使用[高级建模 &#40;Excel 数据挖掘外接程序&#41;](advanced-modeling-data-mining-add-ins-for-excel.md) "选项生成 Naive Bayes 模型，将从模型中删除数字列。</span><span class="sxs-lookup"><span data-stu-id="a00f0-221">If you build a Naive Bayes model using the [Advanced Modeling &#40;Data Mining Add-ins for Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md) option, number columns will be removed from the model.</span></span> <span data-ttu-id="a00f0-222">如果要避免这种情况，请使用 "重新[标记 &#40;SQL Server 数据挖掘外接程序"&#41;](relabel-sql-server-data-mining-add-ins.md)工具创建一个具有装箱值的新列。</span><span class="sxs-lookup"><span data-stu-id="a00f0-222">If you want to avoid this, use the [Relabel &#40;SQL Server Data Mining Add-ins&#41;](relabel-sql-server-data-mining-add-ins.md) tool to create a new column with binned values.</span></span>  
  
 <span data-ttu-id="a00f0-223">**聚类分析模型**</span><span class="sxs-lookup"><span data-stu-id="a00f0-223">**Clustering Models**</span></span>  
  
-   <span data-ttu-id="a00f0-224">"聚类分析工具" ([群集 &#40;向导 "用于 excel 的数据挖掘外接程序&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)和[检测类别 &#40;用于 Excel 的表分析工具&#41;](detect-categories-table-analysis-tools-for-excel.md)) 也不能使用连续数字，但这两种工具都将自动为您的数字列送箱。</span><span class="sxs-lookup"><span data-stu-id="a00f0-224">The clustering tools ([Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) and [Detect Categories &#40;Table Analysis Tools for Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)) also cannot use continuous numbers, but both of these tools will automatically bin number columns for you.</span></span>  
  
-   <span data-ttu-id="a00f0-225">这两种工具都向您提供选项以便可以选择结果中输出类别的数目，但是，如果您想要控制对单独列中的值进行分组的方式，则应该通过所需分组来创建新列。</span><span class="sxs-lookup"><span data-stu-id="a00f0-225">Both tools give you the option to choose the number of output categories in the results, but if you want to control the way that values in individual columns are grouped, you should create a new column with the grouping you want.</span></span>  
  
 <span data-ttu-id="a00f0-226">**预测模型**</span><span class="sxs-lookup"><span data-stu-id="a00f0-226">**Forecasting Models**</span></span>  
  
-   <span data-ttu-id="a00f0-227">所有预测工具都要求您预测连续数值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-227">All forecasting tools require that you predict a continuous number.</span></span> <span data-ttu-id="a00f0-228">无法预测已保存为文本的数字。</span><span class="sxs-lookup"><span data-stu-id="a00f0-228">You cannot predict a number that has been saved as text.</span></span>  
  
-   <span data-ttu-id="a00f0-229">如果数据包含数据类型错误的数字列，可以使用 Excel 函数或 PowerPivot 功能创建数字数据类型正确的列的副本。</span><span class="sxs-lookup"><span data-stu-id="a00f0-229">If your data contains number columns that have the wrong data type, you can use Excel functions or PowerPivot functions to make a copy of the column that has the correct numeric data type.</span></span> <span data-ttu-id="a00f0-230">如果执行此操作，请务必删除包含文本数字的列的副本，以便值不会重复。</span><span class="sxs-lookup"><span data-stu-id="a00f0-230">If you do this, be sure to remove the copy of the column that has the text numbers, so that the values are not duplicated.</span></span>  
  
-   <span data-ttu-id="a00f0-231">如果要创建回归模型的散点图，则输入变量也必须是连续数字（表示为合适的数据类型）。</span><span class="sxs-lookup"><span data-stu-id="a00f0-231">If you want to create a scatter plot of a regression model, the input variables must also be continuous numbers, expressed as an appropriate data type.</span></span>  
  
### <a name="using-content-types-to-make-better-models"></a><span data-ttu-id="a00f0-232">使用内容类型生成更好的模型</span><span class="sxs-lookup"><span data-stu-id="a00f0-232">Using Content Types to Make Better Models</span></span>  
 <span data-ttu-id="a00f0-233">"*内容类型*" 是应用于列的属性，用于指定模型应使用列数据的方式。</span><span class="sxs-lookup"><span data-stu-id="a00f0-233">A *content type* is a property you apply to a column to specify how the column data should be used by the model.</span></span> <span data-ttu-id="a00f0-234">执行分析时，算法可以使用内容类型作为说明或提示。</span><span class="sxs-lookup"><span data-stu-id="a00f0-234">The algorithm can use the content type as an instruction or hint when performing the analysis.</span></span>  
  
 <span data-ttu-id="a00f0-235">例如，如果列中的数字以特定的间隔重复，来指示一周中的某几天，则可以将该列的内容类型指定为 `Cyclical`。</span><span class="sxs-lookup"><span data-stu-id="a00f0-235">For example, if a column contains numbers that repeat in a specific interval to indicate the days of the week, you might specify the content type of that column as `Cyclical`.</span></span>  
  
 <span data-ttu-id="a00f0-236">如果使用此加载项中提供的向导和工具，则无需担心内容类型。但是，如果您使用 "[添加模型来构造 &#40;用于 Excel 的数据挖掘外接程序&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)建模选项来向现有数据添加新模型，则可能会收到与内容类型相关的错误。</span><span class="sxs-lookup"><span data-stu-id="a00f0-236">You don't have to worry about content types if you use the wizards and tools provided in this add-ins. However, if you use the [Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md) modeling option to add a new model to existing data, you might get an error relating to content types.</span></span>  
  
 <span data-ttu-id="a00f0-237">得到错误的原因是，某些类型的模型要求某种类型的数据（例如时间戳）。</span><span class="sxs-lookup"><span data-stu-id="a00f0-237">The reason is that some types of model require a certain kind of data (such as a time stamp).</span></span> <span data-ttu-id="a00f0-238">这些工具根据特定要求处理这些列，并且还添加内容类型属性。</span><span class="sxs-lookup"><span data-stu-id="a00f0-238">The tools process these columns according to specific requirements and also add a content type property.</span></span> <span data-ttu-id="a00f0-239">因此，如果对完全不同的算法重复使用数据，则可能需要更改数据类型或内容类型。</span><span class="sxs-lookup"><span data-stu-id="a00f0-239">Therefore, if you re-use the data with a completely different algorithm, you might need to change the data type or content type.</span></span>  
  
 <span data-ttu-id="a00f0-240">下表介绍了数据挖掘中使用的内容类型，并标识了支持每种类型的数据类型。</span><span class="sxs-lookup"><span data-stu-id="a00f0-240">The following list describes the content types that are used in data mining, and identifies the data types that support each type.</span></span>  
  
 `Discrete`  
 <span data-ttu-id="a00f0-241">该列包含各值之间没有连续体的有限数量的值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-241">The column contains a finite number of values with no continuum between the values.</span></span> <span data-ttu-id="a00f0-242">例如，性别列是一个典型的离散属性列，这是因为该数据表示特定数量的类别。</span><span class="sxs-lookup"><span data-stu-id="a00f0-242">For example, a gender column is a typical discrete attribute column, in that the data represents a specific number of categories.</span></span>  
  
 <span data-ttu-id="a00f0-243"> 内容类型可用于所有数据类型。</span><span class="sxs-lookup"><span data-stu-id="a00f0-243">The `Discrete` content type can be used with all data types.</span></span>  
  
 `Continuous`  
 <span data-ttu-id="a00f0-244">此列包含的值表示某一允许中间值的范围中的数值数据。</span><span class="sxs-lookup"><span data-stu-id="a00f0-244">The column contains values that represent numeric data on a scale that allows interim values.</span></span> <span data-ttu-id="a00f0-245">连续列表示可缩放度量，且数据可能包含无限数目的小数值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-245">A continuous column represents scalable measurements, and it is possible for the data to contain an infinite number of fractional values.</span></span> <span data-ttu-id="a00f0-246">温度列即为连续属性列的示例。</span><span class="sxs-lookup"><span data-stu-id="a00f0-246">A column of temperatures is an example of a continuous attribute column.</span></span>  
  
 <span data-ttu-id="a00f0-247">`Continuous` 内容类型可用于以下数据类型：`Date`、`Double` 和 `Long`。</span><span class="sxs-lookup"><span data-stu-id="a00f0-247">The `Continuous` content type can be used with the following data types: `Date`, `Double`, and `Long`.</span></span>  
  
 `Discretized`  
 <span data-ttu-id="a00f0-248">该列包含表示值组的值，这些值是从连续列派生的值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-248">The column contains values that represent groups of values that have been derived from a continuous column.</span></span> <span data-ttu-id="a00f0-249">Bucket 被视为**有序**的离散值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-249">The buckets are treated as **ordered** and discrete values.</span></span>  
  
 <span data-ttu-id="a00f0-250"> 内容类型可用于以下数据类型：、、。</span><span class="sxs-lookup"><span data-stu-id="a00f0-250">The `Discretized` content type can be used with the following data types: `Date`, `Double`, `Long`.</span></span>  
  
 <span data-ttu-id="a00f0-251">**Key**</span><span class="sxs-lookup"><span data-stu-id="a00f0-251">**Key**</span></span>  
 <span data-ttu-id="a00f0-252">该列唯一标识某一行。</span><span class="sxs-lookup"><span data-stu-id="a00f0-252">The column uniquely identifies a row.</span></span>  
  
 <span data-ttu-id="a00f0-253">通常，键列是数值或文本标识符，不应该用于分析，只应用于跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="a00f0-253">Typically the key column is a numeric or text identifier that should not be used for analysis, only for tracking records.</span></span> <span data-ttu-id="a00f0-254">时序键和序列键是例外。</span><span class="sxs-lookup"><span data-stu-id="a00f0-254">The exceptions are time series keys and sequence keys.</span></span>  
  
 <span data-ttu-id="a00f0-255">仅当从已定义为数据源视图的外部数据源获取数据时，才使用**嵌套表键** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a00f0-255">**Nested table keys** are used only when you get data from an external data source that has been defined as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source view.</span></span> <span data-ttu-id="a00f0-256">有关嵌套表的详细信息，请参阅 [https://msdn.microsoft.com/library/ms175659.aspx](https://msdn.microsoft.com/library/ms175659.aspx) ：</span><span class="sxs-lookup"><span data-stu-id="a00f0-256">For more information about nested tables, see [https://msdn.microsoft.com/library/ms175659.aspx](https://msdn.microsoft.com/library/ms175659.aspx):</span></span>  
  
 <span data-ttu-id="a00f0-257">此内容类型可用于以下数据类型：`Date`、`Double`、`Long` 和 `Text`。</span><span class="sxs-lookup"><span data-stu-id="a00f0-257">This content type can be used with the following data types: `Date`, `Double`, `Long`, and `Text`.</span></span>  
  
 <span data-ttu-id="a00f0-258">**键序列**</span><span class="sxs-lookup"><span data-stu-id="a00f0-258">**Key Sequence**</span></span>  
 <span data-ttu-id="a00f0-259">该列包含表示事件序列的值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-259">The column contains values that represent a sequence of events.</span></span> <span data-ttu-id="a00f0-260">这些值是有序值，但不必按等差排列。</span><span class="sxs-lookup"><span data-stu-id="a00f0-260">The values are ordered, but do not have to be an equal distance apart.</span></span>  
  
 <span data-ttu-id="a00f0-261">以下数据类型支持此内容类型：`Double`、`Long`、`Text` 和 `Date`。</span><span class="sxs-lookup"><span data-stu-id="a00f0-261">This content type is supported by the following data types: `Double`, `Long`, `Text`, and `Date`.</span></span>  
  
 <span data-ttu-id="a00f0-262">**键时间**</span><span class="sxs-lookup"><span data-stu-id="a00f0-262">**Key Time**</span></span>  
 <span data-ttu-id="a00f0-263">该列包含按顺序排列并表示时间刻度的值。</span><span class="sxs-lookup"><span data-stu-id="a00f0-263">The column contains values that are ordered and represent a time scale.</span></span> <span data-ttu-id="a00f0-264">仅当模型为时序模型或顺序分析和聚类分析模型时才能使用键时间内容类型。</span><span class="sxs-lookup"><span data-stu-id="a00f0-264">You can use the key time content type only if the model is a time series model or a sequence clustering model.</span></span>  
  
 <span data-ttu-id="a00f0-265">以下数据类型支持此内容类型：`Double`、`Long` 和 `Date`。</span><span class="sxs-lookup"><span data-stu-id="a00f0-265">This content type is supported by the following data types: `Double`, `Long`, and `Date`.</span></span>  
  
 <span data-ttu-id="a00f0-266">**表**</span><span class="sxs-lookup"><span data-stu-id="a00f0-266">**Table**</span></span>  
 <span data-ttu-id="a00f0-267">只有在您从已定义为 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据源视图的外部数据源获取数据时，还可以使用此内容类型。</span><span class="sxs-lookup"><span data-stu-id="a00f0-267">This content type also is used only when you get data from an external data source that has been defined as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source view.</span></span>  
  
 <span data-ttu-id="a00f0-268">这意味着，数据的每一行都实际包含嵌套数据表，并且具有一个或多个列以及一个或多个行。</span><span class="sxs-lookup"><span data-stu-id="a00f0-268">What it means is that each row of data actually contains a nested data table, with one or more columns and one or more rows.</span></span>  
  
 <span data-ttu-id="a00f0-269">嵌套表非常方便，但只能将其用于[高级建模 &#40;Excel 数据挖掘外接程序&#41;](advanced-modeling-data-mining-add-ins-for-excel.md)建模选项。</span><span class="sxs-lookup"><span data-stu-id="a00f0-269">Nested tables are very handy, but you can use them only with the [Advanced Modeling &#40;Data Mining Add-ins for Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md) modeling options.</span></span> <span data-ttu-id="a00f0-270">例如，使用 "Excel&#41;向导" 的 "数据挖掘客户端" 和 "购物篮分析" &#40;用于 excel 的[数据挖掘客户端](associate-wizard-data-mining-client-for-excel.md)向导和[购物篮&#41;&#40;分析](shopping-basket-analysis-table-analysistools-for-excel.md)的示例数据包含已从嵌套表中平展的数据。</span><span class="sxs-lookup"><span data-stu-id="a00f0-270">For example, the sample data for the [Associate Wizard &#40;Data Mining Client for Excel&#41;](associate-wizard-data-mining-client-for-excel.md) wizard and [Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) tool contains data that has been flattened from a nested table.</span></span>  

  
  
