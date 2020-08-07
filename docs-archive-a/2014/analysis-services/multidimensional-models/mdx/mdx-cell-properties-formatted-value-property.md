---
title: FORMATED_VALUE 上的语言和 FORMAT_STRING |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7534ff5f-954e-47d4-a2ed-4b5b8ccb30e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: ba4aacbbd440da6048680054771c86c40ef96daa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577005"
---
# <a name="language-and-format_string-on-formated_value"></a><span data-ttu-id="9e151-102">基于 LANGUAGE 和 FORMAT_STRING 的 FORMATED_VALUE</span><span class="sxs-lookup"><span data-stu-id="9e151-102">LANGUAGE and FORMAT_STRING on FORMATED_VALUE</span></span>
  <span data-ttu-id="9e151-103">FORMATTED_VALUE 属性是基于单元的 VALUE、FORMAT_STRING 和 LANGUAGE 属性的交互生成的。</span><span class="sxs-lookup"><span data-stu-id="9e151-103">The FORMATTED_VALUE property is built on the interactions of the VALUE, FORMAT_STRING and LANGUAGE properties of the cell.</span></span> <span data-ttu-id="9e151-104">本主题说明这些属性通过何种方式进行交互来生成 FORMATTED_VALUE 属性。</span><span class="sxs-lookup"><span data-stu-id="9e151-104">This topic explains how these properties interact to build the FORMATTED_VALUE property.</span></span>  
  
## <a name="value-format_string-language-properties"></a><span data-ttu-id="9e151-105">VALUE、FORMAT_STRING、LANGUAGE 属性</span><span class="sxs-lookup"><span data-stu-id="9e151-105">VALUE, FORMAT_STRING, LANGUAGE properties</span></span>  
 <span data-ttu-id="9e151-106">下表说明了这些属性的定义，可为我们将来合并使用这些属性提供帮助。</span><span class="sxs-lookup"><span data-stu-id="9e151-106">The following table explains what these properties are, to help prepare us to use them in combination.</span></span>  
  
 <span data-ttu-id="9e151-107">值</span><span class="sxs-lookup"><span data-stu-id="9e151-107">VALUE</span></span>  
 <span data-ttu-id="9e151-108">单元的未格式化值。</span><span class="sxs-lookup"><span data-stu-id="9e151-108">The unformatted value of the cell.</span></span>  
  
 <span data-ttu-id="9e151-109">FORMAT_STRING</span><span class="sxs-lookup"><span data-stu-id="9e151-109">FORMAT_STRING</span></span>  
 <span data-ttu-id="9e151-110">将应用于单元的值以生成 FORMATTED_VALUE 属性的格式模板。</span><span class="sxs-lookup"><span data-stu-id="9e151-110">The formatting template to be applied to the value of the cell to generate FORMATTED_VALUE property</span></span>  
  
 <span data-ttu-id="9e151-111">LANGUAGE</span><span class="sxs-lookup"><span data-stu-id="9e151-111">LANGUAGE</span></span>  
 <span data-ttu-id="9e151-112">要与 FORMAT_STRING 一起应用以生成本地化版本的 FORMATTED_VALUE 的区域设置规范。</span><span class="sxs-lookup"><span data-stu-id="9e151-112">The locale specification to be applied alongside FORMAT_STRING to generate a localized version of FORMATTED_VALUE</span></span>  
  
## <a name="formatted_value-constructed"></a><span data-ttu-id="9e151-113">FORMATTED_VALUE 的构造</span><span class="sxs-lookup"><span data-stu-id="9e151-113">FORMATTED_VALUE constructed</span></span>  
 <span data-ttu-id="9e151-114">FORMATTED_VALUE 属性是通过使用 VALUE 属性中的值并对该值应用 FORMAT_STRING 属性中指定的格式模板构造而成。</span><span class="sxs-lookup"><span data-stu-id="9e151-114">The FORMATTED_VALUE property is constructed by using the value from the VALUE property and applying the format template specified in the FORMAT_STRING property to that value.</span></span> <span data-ttu-id="9e151-115">另外，每当格式值为 `named formatting literal` 时，LANGUAGE 属性规范便会修改 FORMAT_STRING 的输出结果以遵守命名格式的语言用法。</span><span class="sxs-lookup"><span data-stu-id="9e151-115">In addition, whenever the formatting value is a `named formatting literal` the LANGUAGE property specification modifies the output of FORMAT_STRING to follow the language usage for the named formatting.</span></span> <span data-ttu-id="9e151-116">所有命名格式文字都定义为可本地化。</span><span class="sxs-lookup"><span data-stu-id="9e151-116">Named formatting literals are all defined in a way that can be localized.</span></span> <span data-ttu-id="9e151-117">例如， `"General Date"` 为可以本地化的规范，而下面的模板 `"YYYY-MM-DD hh:nn:ss",` 则相反，该模板指定所显示的日期由模板定义，与语言规范无关。</span><span class="sxs-lookup"><span data-stu-id="9e151-117">For example, `"General Date"` is a specification that can be localized, as opposed to the following template `"YYYY-MM-DD hh:nn:ss",` which states that the date is to be presented as defined by the template regardless of the language specification.</span></span>  
  
 <span data-ttu-id="9e151-118">如果 FORMAT_STRING 模板和 LANGUAGE 规范之间有冲突，则 FORMAT_STRING 模板将优先于 LANGUAGE 规范。</span><span class="sxs-lookup"><span data-stu-id="9e151-118">If there is a conflict between the FORMAT_STRING template and the LANGUAGE specification, the FORMAT_STRING template overrides the LANGUAGE specification.</span></span> <span data-ttu-id="9e151-119">例如，如果指定 FORMAT_STRING="$ #0" 且 LANGUAGE=1034（西班牙），VALUE=123.456，则 FORMATTED_VALUE="$ 123" 而不是 FORMATTED_VALUE="€ 123"（期望的格式为欧元），因为格式模板的值优先于指定的语言。</span><span class="sxs-lookup"><span data-stu-id="9e151-119">For example, if FORMAT_STRING="$ #0" and LANGUAGE=1034 (Spain), and VALUE=123.456 then FORMATTED_VALUE="$ 123" instead of FORMATTED_VALUE="€ 123", the expected format is in Euros, because the value of the format template overrides the language specified.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="9e151-120">示例</span><span class="sxs-lookup"><span data-stu-id="9e151-120">Examples</span></span>  
 <span data-ttu-id="9e151-121">以下示例显示了将 LANGUAGE 与 FORMAT_STRING 合并使用时获得的输出结果。</span><span class="sxs-lookup"><span data-stu-id="9e151-121">The following examples show the output obtained when LANGUAGE is used in conjunction with FORMAT_STRING.</span></span>  
  
 <span data-ttu-id="9e151-122">第一个示例说明了数字值的格式设置；第二个示例说明了日期和时间值的格式设置。</span><span class="sxs-lookup"><span data-stu-id="9e151-122">The first example explains formatting numerical values; the second example explains formatting date and time values.</span></span>  
  
 <span data-ttu-id="9e151-123">对每个示例均指定了多维表达式 (MDX) 代码。</span><span class="sxs-lookup"><span data-stu-id="9e151-123">For each example the Multidimensional Expressions (MDX) code is given.</span></span>  
  
 `with`  
  
 `member measures.A as 5040, FORMAT_STRING="Currency"`  
  
 `member measures.B as measures.A, LANGUAGE=1034`  
  
 `member measures.C as measures.A, LANGUAGE=1034 , FORMAT_STRING="$#,##0.00"`  
  
 `member measures.D as measures.A, FORMAT_STRING="Scientific"`  
  
 `member measures.E as measures.A, LANGUAGE=1034 , FORMAT_STRING="Scientific"`  
  
 `member measures.F as 0.5040, FORMAT_STRING="Percent"`  
  
 `member measures.G as measures.F, LANGUAGE=1034`  
  
 `member measures.H as 0, LANGUAGE=1034 , FORMAT_STRING="Yes/No"`  
  
 `member measures.I as 59, LANGUAGE=1034 , FORMAT_STRING="Yes/No"`  
  
 `member measures.J as 0, LANGUAGE=1034 , FORMAT_STRING="ON/OFF"`  
  
 `member measures.K as -312, LANGUAGE=1034 , FORMAT_STRING="ON/OFF"`  
  
 `Select {measures.A, measures.B, measures.C, measures.D, measures.E, measures.F, measures.G, measures.H, measures.I, measures.J, measures.K} on 0`  
  
 `from [Adventure Works]`  
  
 `cell properties VALUE, FORMAT_STRING, LANGUAGE, FORMATTED_VALUE`  
  
 <span data-ttu-id="9e151-124">使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在区域设置为 1033 的服务器和客户端上运行上述 MDX 查询时，转置后的结果为如下所示：</span><span class="sxs-lookup"><span data-stu-id="9e151-124">The results, transposed, when the above MDX query was run using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] over a server and client with locale 1033 are as follows:</span></span>  
  
|<span data-ttu-id="9e151-125">成员</span><span class="sxs-lookup"><span data-stu-id="9e151-125">Member</span></span>|<span data-ttu-id="9e151-126">FORMATTED_VALUE</span><span class="sxs-lookup"><span data-stu-id="9e151-126">FORMATTED_VALUE</span></span>|<span data-ttu-id="9e151-127">说明</span><span class="sxs-lookup"><span data-stu-id="9e151-127">Explanation</span></span>|  
|------------|----------------------|-----------------|  
|<span data-ttu-id="9e151-128">A</span><span class="sxs-lookup"><span data-stu-id="9e151-128">A</span></span>|<span data-ttu-id="9e151-129">$5,040.00</span><span class="sxs-lookup"><span data-stu-id="9e151-129">$5,040.00</span></span>|<span data-ttu-id="9e151-130">FORMAT_STRING 设置为 `Currency` ，LANGUAGE 为从系统区域设置值继承的 `1033`</span><span class="sxs-lookup"><span data-stu-id="9e151-130">FORMAT_STRING is set to `Currency` and LANGUAGE is `1033`, inherited from system locale value</span></span>|  
|<span data-ttu-id="9e151-131">B</span><span class="sxs-lookup"><span data-stu-id="9e151-131">B</span></span>|<span data-ttu-id="9e151-132">€5.040,00</span><span class="sxs-lookup"><span data-stu-id="9e151-132">€5.040,00</span></span>|<span data-ttu-id="9e151-133">FORMAT_STRING 设置为 `Currency` （从 A 继承），并且 LANGUAGE 显式设置为 `1034` （西班牙），因此显示的是欧元符号，所使用的小数分隔符和千分分隔符也与前面的示例不相同。</span><span class="sxs-lookup"><span data-stu-id="9e151-133">FORMAT_STRING is set to `Currency` (inherited from A) and LANGUAGE is explicitly set to `1034` (Spain) hence the Euro sign, the different decimal separator and the different thousand separator.</span></span>|  
|<span data-ttu-id="9e151-134">C</span><span class="sxs-lookup"><span data-stu-id="9e151-134">C</span></span>|<span data-ttu-id="9e151-135">$5.040,00</span><span class="sxs-lookup"><span data-stu-id="9e151-135">$5.040,00</span></span>|<span data-ttu-id="9e151-136">FORMAT_STRING 设置为 `$#,##0.00` ，取代了来自 A 的 Currency，并且 LANGUAGE 显式设置为 `1034` （西班牙）。</span><span class="sxs-lookup"><span data-stu-id="9e151-136">FORMAT_STRING is set to `$#,##0.00` an override to Currency, from A, and LANGUAGE is explicitly set to `1034` (Spain).</span></span> <span data-ttu-id="9e151-137">因为 FORMAT_STRING 属性将货币符号显式设置为 $，因此 FORMATTED_VALUE 将使用 $ 符号显示。</span><span class="sxs-lookup"><span data-stu-id="9e151-137">Because the FORMAT_STRING property explicitly set the currency symbol to $, the FORMATTED_VALUE is presented with the $ sign.</span></span> <span data-ttu-id="9e151-138">然而，因为 `.` （点）和 `,` （逗号）分别为小数分隔符和千位分隔符的占位符，因此该语言规范将对这些占位符所生成的小数点分隔符和千位分隔符的本地化输出结果产生影响。</span><span class="sxs-lookup"><span data-stu-id="9e151-138">However, because `.` (dot) and `,` (comma) are placeholders for decimal separator and thousand separator respectively, the language specification affects them generating an output that is localized for decimal and thousand separators.</span></span>|  
|<span data-ttu-id="9e151-139">D</span><span class="sxs-lookup"><span data-stu-id="9e151-139">D</span></span>|<span data-ttu-id="9e151-140">5.04E+03</span><span class="sxs-lookup"><span data-stu-id="9e151-140">5.04E+03</span></span>|<span data-ttu-id="9e151-141">FORMAT_STRING 设置为 `Scientific` ，LANGUAGE 设置为从系统区域设置值继承的 `1033`，因此以 `.` （点）作为小数分隔符。</span><span class="sxs-lookup"><span data-stu-id="9e151-141">FORMAT_STRING is set to `Scientific` and LANGUAGE is set to `1033`, inherited from system locale value, hence `.` (dot) is the decimal separator.</span></span>|  
|<span data-ttu-id="9e151-142">E</span><span class="sxs-lookup"><span data-stu-id="9e151-142">E</span></span>|<span data-ttu-id="9e151-143">5,04E+03</span><span class="sxs-lookup"><span data-stu-id="9e151-143">5,04E+03</span></span>|<span data-ttu-id="9e151-144">FORMAT_STRING 设置为 `Scientific` ，LANGUAGE 显式设置为 `1034,` ，因此以 `,` （逗号）作为小数分隔符。</span><span class="sxs-lookup"><span data-stu-id="9e151-144">FORMAT_STRING is set to `Scientific` and LANGUAGE is set explicitly to `1034,` hence `,` (comma) is the decimal separator.</span></span>|  
|<span data-ttu-id="9e151-145">F</span><span class="sxs-lookup"><span data-stu-id="9e151-145">F</span></span>|<span data-ttu-id="9e151-146">50.40%</span><span class="sxs-lookup"><span data-stu-id="9e151-146">50.40%</span></span>|<span data-ttu-id="9e151-147">FORMAT_STRING 设置为 `Percent` ，LANGUAGE 设置为从系统区域设置值继承的 `1033`，因此以 `.` （点）作为小数分隔符。</span><span class="sxs-lookup"><span data-stu-id="9e151-147">FORMAT_STRING is set to `Percent` and LANGUAGE is set to `1033`, inherited from system locale value, hence `.` (dot) is the decimal separator.</span></span><br /><br /> <span data-ttu-id="9e151-148">请注意，VALUE 已从 5040 更改为 0.5040</span><span class="sxs-lookup"><span data-stu-id="9e151-148">Note that VALUE was changed from 5040 to 0.5040</span></span>|  
|<span data-ttu-id="9e151-149">G</span><span class="sxs-lookup"><span data-stu-id="9e151-149">G</span></span>|<span data-ttu-id="9e151-150">50,40%</span><span class="sxs-lookup"><span data-stu-id="9e151-150">50,40%</span></span>|<span data-ttu-id="9e151-151">FORMAT_STRING 设置为 `Percent`（从 F 继承），LANGUAGE 显式设置为 `1034` ，因此以 `,` （逗号）作为小数点分隔符。</span><span class="sxs-lookup"><span data-stu-id="9e151-151">FORMAT_STRING is set to `Percent`, inherited from F, and LANGUAGE is set explicitly to `1034` hence `,` (comma) is the decimal separator.</span></span><br /><br /> <span data-ttu-id="9e151-152">请注意，VALUE 从 F 的值继承。</span><span class="sxs-lookup"><span data-stu-id="9e151-152">Note that VALUE was inherited from F value.</span></span>|  
|<span data-ttu-id="9e151-153">H</span><span class="sxs-lookup"><span data-stu-id="9e151-153">H</span></span>|<span data-ttu-id="9e151-154">否</span><span class="sxs-lookup"><span data-stu-id="9e151-154">No</span></span>|<span data-ttu-id="9e151-155">FORMAT_STRING 设置为 `YES/NO`，VALUE 设置为 0，并且 LANGUAGE 显式设置为 `1034`；因为英语 NO 和西班牙语 NO 之间并无区别，因此用户在 FORMATTED_VALUE 中看不到任何差别。</span><span class="sxs-lookup"><span data-stu-id="9e151-155">FORMAT_STRING is set to `YES/NO`, VALUE is set to 0 and LANGUAGE is set explicitly to `1034`; because there is no difference between English NO and Spanish NO the user sees no difference in the FORMATTED_VALUE.</span></span>|  
|<span data-ttu-id="9e151-156">I</span><span class="sxs-lookup"><span data-stu-id="9e151-156">I</span></span>|<span data-ttu-id="9e151-157">SI</span><span class="sxs-lookup"><span data-stu-id="9e151-157">SI</span></span>|<span data-ttu-id="9e151-158">FORMAT_STRING 设置为 `YES/NO`，VALUE 设置为 59，并且 LANGUAGE 显式设置为 `1034`；根据针对 YES/NO 格式设置的定义，任何零 (0) 以外的值均为 YES，并且因为语言设置为西班牙语，所以 FORMATTED_VALUE 为 SI。</span><span class="sxs-lookup"><span data-stu-id="9e151-158">FORMAT_STRING is set to `YES/NO`, VALUE is set to 59 and LANGUAGE is set explicitly to `1034`; as defined for YES/NO formatting, any value different from zero (0) is a YES and because language is set to Spanish then the FORMATTED_VALUE is SI.</span></span>|  
|<span data-ttu-id="9e151-159">J</span><span class="sxs-lookup"><span data-stu-id="9e151-159">J</span></span>|<span data-ttu-id="9e151-160">Desactivado</span><span class="sxs-lookup"><span data-stu-id="9e151-160">Desactivado</span></span>|<span data-ttu-id="9e151-161">FORMAT_STRING 设置为 `ON/OFF`，VALUE 设置为 0，并且 LANGUAGE 显式设置为 `1034`；根据针对 ON/OFF 格式设置的定义，任何等于零 (0) 的值均为 OFF，并且因为语言设置为西班牙语，因此 FORMATTED_VALUE 为 Desactivado。</span><span class="sxs-lookup"><span data-stu-id="9e151-161">FORMAT_STRING is set to `ON/OFF`, VALUE is set to 0 and LANGUAGE is set explicitly to `1034`; as defined for ON/OFF formatting, any value equal to zero (0) is an OFF and because language is set to Spanish then the FORMATTED_VALUE is Desactivado.</span></span>|  
|<span data-ttu-id="9e151-162">K</span><span class="sxs-lookup"><span data-stu-id="9e151-162">K</span></span>|<span data-ttu-id="9e151-163">Activado</span><span class="sxs-lookup"><span data-stu-id="9e151-163">Activado</span></span>|<span data-ttu-id="9e151-164">FORMAT_STRING 设置为 `ON/OFF`，VALUE 设置为 -312，并且 LANGUAGE 显式设置为 `1034`；根据针对 ON/OFF 格式设置的定义，任何零 (0) 以外的值均为 ON，并且因为语言设置为西班牙语，因此 FORMATTED_VALUE 为 Activado。</span><span class="sxs-lookup"><span data-stu-id="9e151-164">FORMAT_STRING is set to `ON/OFF`, VALUE is set to -312 and LANGUAGE is set explicitly to `1034`; as defined for ON/OFF formatting, any value different from zero (0) is an ON and because language is set to Spanish then the FORMATTED_VALUE is Activado.</span></span>|  
  
 `with`  
  
 `member measures.A as 'CDate("1959-03-12 06:30")'`  
  
 `member measures.B as measures.A, FORMAT_STRING="Long Date"`  
  
 `member measures.C as measures.A, LANGUAGE=1034 , FORMAT_STRING="General Date"`  
  
 `member measures.D as measures.A, LANGUAGE=1034, FORMAT_STRING="Long Date"`  
  
 `member measures.E as measures.A, LANGUAGE=1041 , FORMAT_STRING="General Date"`  
  
 `member measures.F as measures.A, LANGUAGE=1041 , FORMAT_STRING="Long Date"`  
  
 `member measures.G as measures.A, FORMAT_STRING="Long Time"`  
  
 `member measures.H as measures.A, FORMAT_STRING="Short Time"`  
  
 `member measures.I as measures.A, LANGUAGE=1034 , FORMAT_STRING="Long Time"`  
  
 `member measures.J as measures.A, LANGUAGE=1034 , FORMAT_STRING="Short Time"`  
  
 `member measures.K as measures.A, LANGUAGE=1041 , FORMAT_STRING="Long Time"`  
  
 `member measures.L as measures.A, LANGUAGE=1041 , FORMAT_STRING="Short Time"`  
  
 `Select {measures.A, measures.B, measures.C, measures.D, measures.E, measures.F`  
  
 `, measures.G, measures.H, measures.I, measures.J, measures.K, measures.L} on 0`  
  
 `from [Adventure Works]`  
  
 `cell properties VALUE, FORMAT_STRING, LANGUAGE, FORMATTED_VALUE`  
  
 <span data-ttu-id="9e151-165">使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在区域设置为 1033 的服务器和客户端上运行上述 MDX 查询时，转置后的结果为如下所示：</span><span class="sxs-lookup"><span data-stu-id="9e151-165">The results, transposed, when the above MDX query was run using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] over a server and client with locale 1033 are as follows:</span></span>  
  
|<span data-ttu-id="9e151-166">成员</span><span class="sxs-lookup"><span data-stu-id="9e151-166">Member</span></span>|<span data-ttu-id="9e151-167">FORMATTED_VALUE</span><span class="sxs-lookup"><span data-stu-id="9e151-167">FORMATTED_VALUE</span></span>|<span data-ttu-id="9e151-168">说明</span><span class="sxs-lookup"><span data-stu-id="9e151-168">Explanation</span></span>|  
|------------|----------------------|-----------------|  
|<span data-ttu-id="9e151-169">A</span><span class="sxs-lookup"><span data-stu-id="9e151-169">A</span></span>|<span data-ttu-id="9e151-170">3/12/1959 6:30:00 AM</span><span class="sxs-lookup"><span data-stu-id="9e151-170">3/12/1959 6:30:00 AM</span></span>|<span data-ttu-id="9e151-171">FORMAT_STRING 通过 CDate() 表达式隐式设置为 `General Date` ，并且 LANGUAGE 为从系统区域设置值继承的 `1033` （英语）</span><span class="sxs-lookup"><span data-stu-id="9e151-171">FORMAT_STRING is set implicitly to `General Date` by the CDate() expression and LANGUAGE is `1033` (English), inherited from system locale value</span></span>|  
|<span data-ttu-id="9e151-172">B</span><span class="sxs-lookup"><span data-stu-id="9e151-172">B</span></span>|<span data-ttu-id="9e151-173">Thursday, March 12, 1959</span><span class="sxs-lookup"><span data-stu-id="9e151-173">Thursday, March 12, 1959</span></span>|<span data-ttu-id="9e151-174">FORMAT_STRING 显式设置为 `Long Date` ，并且 LANGUAGE 为从系统区域设置值继承的 `1033` （英语）</span><span class="sxs-lookup"><span data-stu-id="9e151-174">FORMAT_STRING is set explicitly to `Long Date` and LANGUAGE is `1033` (English), inherited from system locale value</span></span>|  
|<span data-ttu-id="9e151-175">C</span><span class="sxs-lookup"><span data-stu-id="9e151-175">C</span></span>|<span data-ttu-id="9e151-176">12/03/1959 6:30:00</span><span class="sxs-lookup"><span data-stu-id="9e151-176">12/03/1959 6:30:00</span></span>|<span data-ttu-id="9e151-177">FORMAT_STRING 显式设置为 `General Date` ，并且 LANGUAGE 为显式 `1034` （西班牙语）。</span><span class="sxs-lookup"><span data-stu-id="9e151-177">FORMAT_STRING is set explicitly to `General Date` and LANGUAGE is explicitly `1034` (Spanish).</span></span><br /><br /> <span data-ttu-id="9e151-178">请注意，在与美国格式设置样式进行比较时应切换月和天</span><span class="sxs-lookup"><span data-stu-id="9e151-178">Note that month and day are switched when compared to U.S. formatting style</span></span>|  
|<span data-ttu-id="9e151-179">D</span><span class="sxs-lookup"><span data-stu-id="9e151-179">D</span></span>|<span data-ttu-id="9e151-180">jueves, 12 de marzo de 1959</span><span class="sxs-lookup"><span data-stu-id="9e151-180">jueves, 12 de marzo de 1959</span></span>|<span data-ttu-id="9e151-181">FORMAT_STRING 显式设置为 `Long Date` ，并且 LANGUAGE 为显式 `1034` （西班牙语）。</span><span class="sxs-lookup"><span data-stu-id="9e151-181">FORMAT_STRING is set explicitly to `Long Date` and LANGUAGE is explicitly `1034` (Spanish).</span></span><br /><br /> <span data-ttu-id="9e151-182">请注意月和星期是用西班牙语拼写的</span><span class="sxs-lookup"><span data-stu-id="9e151-182">Note that month and day of the week are worded in Spanish</span></span>|  
|<span data-ttu-id="9e151-183">E</span><span class="sxs-lookup"><span data-stu-id="9e151-183">E</span></span>|<span data-ttu-id="9e151-184">1959/03/12 6:30:00</span><span class="sxs-lookup"><span data-stu-id="9e151-184">1959/03/12 6:30:00</span></span>|<span data-ttu-id="9e151-185">FORMAT_STRING 显式设置为 `General Date` ，并且 LANGUAGE 为显式 `1041` （日语）。</span><span class="sxs-lookup"><span data-stu-id="9e151-185">FORMAT_STRING is set explicitly to `General Date` and LANGUAGE is explicitly `1041` (Japanese).</span></span><br /><br /> <span data-ttu-id="9e151-186">请注意，现在的日期格式设置为：年/月/日 小时:分钟:秒钟</span><span class="sxs-lookup"><span data-stu-id="9e151-186">Note that the date is now formatted Year/Month/Day Hour:Minutes:Seconds</span></span>|  
|<span data-ttu-id="9e151-187">F</span><span class="sxs-lookup"><span data-stu-id="9e151-187">F</span></span>|<span data-ttu-id="9e151-188">1959年3月12日</span><span class="sxs-lookup"><span data-stu-id="9e151-188">1959年3月12日</span></span>|<span data-ttu-id="9e151-189">FORMAT_STRING 显式设置为 `Long Date` ，并且 LANGUAGE 为显式 `1041` （日语）。</span><span class="sxs-lookup"><span data-stu-id="9e151-189">FORMAT_STRING is set explicitly to `Long Date` and LANGUAGE is explicitly `1041` (Japanese).</span></span>|  
|<span data-ttu-id="9e151-190">G</span><span class="sxs-lookup"><span data-stu-id="9e151-190">G</span></span>|<span data-ttu-id="9e151-191">6:30:00 AM</span><span class="sxs-lookup"><span data-stu-id="9e151-191">6:30:00 AM</span></span>|<span data-ttu-id="9e151-192">FORMAT_STRING 显式设置为 `Long Time` ，并且 LANGUAGE 为从系统区域设置值继承的 `1033` （英语）。</span><span class="sxs-lookup"><span data-stu-id="9e151-192">FORMAT_STRING is set explicitly to `Long Time` and LANGUAGE is `1033` (English), inherited from system locale value.</span></span>|  
|<span data-ttu-id="9e151-193">H</span><span class="sxs-lookup"><span data-stu-id="9e151-193">H</span></span>|<span data-ttu-id="9e151-194">06:30</span><span class="sxs-lookup"><span data-stu-id="9e151-194">06:30</span></span>|<span data-ttu-id="9e151-195">FORMAT_STRING 显式设置为 `Short Time` ，并且 LANGUAGE 为从系统区域设置值继承的 `1033` （英语）。</span><span class="sxs-lookup"><span data-stu-id="9e151-195">FORMAT_STRING is set explicitly to `Short Time` and LANGUAGE is `1033` (English), inherited from system locale value.</span></span>|  
|<span data-ttu-id="9e151-196">I</span><span class="sxs-lookup"><span data-stu-id="9e151-196">I</span></span>|<span data-ttu-id="9e151-197">6:30:00</span><span class="sxs-lookup"><span data-stu-id="9e151-197">6:30:00</span></span>|<span data-ttu-id="9e151-198">FORMAT_STRING 显式设置为 `Long Time` ，并且 LANGUAGE 显式设置为 `1034` （西班牙语）。</span><span class="sxs-lookup"><span data-stu-id="9e151-198">FORMAT_STRING is set explicitly to `Long Time` and LANGUAGE is set explicitly to `1034` (Spanish).</span></span>|  
|<span data-ttu-id="9e151-199">J</span><span class="sxs-lookup"><span data-stu-id="9e151-199">J</span></span>|<span data-ttu-id="9e151-200">06:30</span><span class="sxs-lookup"><span data-stu-id="9e151-200">06:30</span></span>|<span data-ttu-id="9e151-201">FORMAT_STRING 显式设置为 `Short Time` ，并且 LANGUAGE 显式设置为 `1034` （西班牙语）。</span><span class="sxs-lookup"><span data-stu-id="9e151-201">FORMAT_STRING is set explicitly to `Short Time` and LANGUAGE is set explicitly to `1034` (Spanish).</span></span>|  
|<span data-ttu-id="9e151-202">K</span><span class="sxs-lookup"><span data-stu-id="9e151-202">K</span></span>|<span data-ttu-id="9e151-203">6:30:00</span><span class="sxs-lookup"><span data-stu-id="9e151-203">6:30:00</span></span>|<span data-ttu-id="9e151-204">FORMAT_STRING 显式设置为 `Long Time` ，并且 LANGUAGE 显式设置为 `1041` （日语）。</span><span class="sxs-lookup"><span data-stu-id="9e151-204">FORMAT_STRING is set explicitly to `Long Time` and LANGUAGE is set explicitly to `1041` (Japanese).</span></span>|  
|<span data-ttu-id="9e151-205">L</span><span class="sxs-lookup"><span data-stu-id="9e151-205">L</span></span>|<span data-ttu-id="9e151-206">06:30</span><span class="sxs-lookup"><span data-stu-id="9e151-206">06:30</span></span>|<span data-ttu-id="9e151-207">FORMAT_STRING 显式设置为 `Short Time` ，并且 LANGUAGE 显式设置为 `1041` （日语）。</span><span class="sxs-lookup"><span data-stu-id="9e151-207">FORMAT_STRING is set explicitly to `Short Time` and LANGUAGE is set explicitly to `1041` (Japanese).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e151-208">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e151-208">See Also</span></span>  
 <span data-ttu-id="9e151-209">[FORMAT_STRING 内容 &#40;MDX&#41;](mdx-cell-properties-format-string-contents.md) </span><span class="sxs-lookup"><span data-stu-id="9e151-209">[FORMAT_STRING Contents &#40;MDX&#41;](mdx-cell-properties-format-string-contents.md) </span></span>  
 <span data-ttu-id="9e151-210">[使用单元属性 &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md) </span><span class="sxs-lookup"><span data-stu-id="9e151-210">[Using Cell Properties &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md) </span></span>  
 <span data-ttu-id="9e151-211">[&#40;MDX&#41;创建和使用属性值](../../creating-and-using-property-values-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="9e151-211">[Creating and Using Property Values &#40;MDX&#41;](../../creating-and-using-property-values-mdx.md) </span></span>  
 [<span data-ttu-id="9e151-212">MDX 查询基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="9e151-212">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
