---
title: 字词提取转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextractiontrans.f1
helpviewer_keywords:
- word boundaries [Integration Services]
- extracting data [Integration Services]
- sentence boundaries
- word extractions [Integration Services]
- Term Extraction transformation
- tagging words
- normalized data [Integration Services]
- tokenizing text [Integration Services]
- parts of speech [Integration Services]
- text extraction [Integration Services]
- term extractions [Integration Services]
- stemming words [Integration Services]
ms.assetid: d0821526-1603-4ea6-8322-2d901568fbeb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8215b53de7da43bbdbcbe29a9bb7f5ad8edc0d61
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692460"
---
# <a name="term-extraction-transformation"></a><span data-ttu-id="a093b-102">字词提取转换</span><span class="sxs-lookup"><span data-stu-id="a093b-102">Term Extraction Transformation</span></span>
  <span data-ttu-id="a093b-103">字词提取转换从转换输入列的文本中提取字词，然后将这些字词写入转换输出列。</span><span class="sxs-lookup"><span data-stu-id="a093b-103">The Term Extraction transformation extracts terms from text in a transformation input column, and then writes the terms to a transformation output column.</span></span> <span data-ttu-id="a093b-104">该转换仅处理英文文本，并使用它自身的英语字典和有关英语的语言信息。</span><span class="sxs-lookup"><span data-stu-id="a093b-104">The transformation works only with English text and it uses its own English dictionary and linguistic information about English.</span></span>  
  
 <span data-ttu-id="a093b-105">可以用字词提取转换搜索数据集的内容。</span><span class="sxs-lookup"><span data-stu-id="a093b-105">You can use the Term Extraction transformation to discover the content of a data set.</span></span> <span data-ttu-id="a093b-106">例如，包含电子邮件的文本可能会提供关于产品有用的反馈信息，因此，作为分析反馈的一种方法，可以用字词提取转换提取邮件中的讨论主题。</span><span class="sxs-lookup"><span data-stu-id="a093b-106">For example, text that contains e-mail messages may provide useful feedback about products, so that you could use the Term Extraction transformation to extract the topics of discussion in the messages, as a way of analyzing the feedback.</span></span>  
  
## <a name="extracted-terms-and-data-types"></a><span data-ttu-id="a093b-107">提取的字词和数据类型</span><span class="sxs-lookup"><span data-stu-id="a093b-107">Extracted Terms and Data Types</span></span>  
 <span data-ttu-id="a093b-108">字词提取转换可以仅提取名词、仅提取名词短语，或者同时提取名词和名词短语。</span><span class="sxs-lookup"><span data-stu-id="a093b-108">The Term Extraction transformation can extract nouns only, noun phrases only, or both nouns and noun phases.</span></span> <span data-ttu-id="a093b-109">名词是单个名词；名词短语至少是两个词，其中一个为名词，另一个为名词或形容词。</span><span class="sxs-lookup"><span data-stu-id="a093b-109">A noun is a single noun; a noun phrases is at least two words, of which one is a noun and the other is a noun or an adjective.</span></span> <span data-ttu-id="a093b-110">例如，如果转换使用仅名词选项，则将提取如 *bicycle* 和 *landscape*等字词；如果转换使用名词短语选项，则将提取如 *new blue bicycle*、 *bicycle helmet*和 *boxed bicycles*等字词。</span><span class="sxs-lookup"><span data-stu-id="a093b-110">For example, if the transformation uses the nouns-only option, it extracts terms like *bicycle* and *landscape*; if the transformation uses the noun phrase option, it extracts terms like *new blue bicycle*, *bicycle helmet*, and *boxed bicycles*.</span></span>  
  
 <span data-ttu-id="a093b-111">冠词和代词不提取。</span><span class="sxs-lookup"><span data-stu-id="a093b-111">Articles and pronouns are not extracted.</span></span> <span data-ttu-id="a093b-112">例如，字词提取转换将从文本 *the bicycle* 、 *my bicycle*和 *that bicycle*中提取字词 *bicycle*。</span><span class="sxs-lookup"><span data-stu-id="a093b-112">For example, the Term Extraction transformation extracts the term *bicycle* from the text *the bicycle*, *my bicycle*, and *that bicycle*.</span></span>  
  
 <span data-ttu-id="a093b-113">字词提取转换为所提取的每个字词生成分数。</span><span class="sxs-lookup"><span data-stu-id="a093b-113">The Term Extraction transformation generates a score for each term that it extracts.</span></span> <span data-ttu-id="a093b-114">该分数可以是 TFIDF 值，也可以是原始频率（表示规范的字词在输入中出现的次数）。</span><span class="sxs-lookup"><span data-stu-id="a093b-114">The score can be either a TFIDF value or the raw frequency, meaning the number of times the normalized term appears in the input.</span></span> <span data-ttu-id="a093b-115">不管哪种情况，分数都表示为大于 0 的实数。</span><span class="sxs-lookup"><span data-stu-id="a093b-115">In either case, the score is represented by a real number that is greater than 0.</span></span> <span data-ttu-id="a093b-116">例如，TFIDF 分数可能为 0.5 的值，而频率可能为像 1.0 或 2.0 这样的值。</span><span class="sxs-lookup"><span data-stu-id="a093b-116">For example, the TFIDF score might have the value 0.5, and the frequency would be a value like 1.0 or 2.0.</span></span>  
  
 <span data-ttu-id="a093b-117">字词提取转换的输出仅包括两列。</span><span class="sxs-lookup"><span data-stu-id="a093b-117">The output of the Term Extraction transformation includes only two columns.</span></span> <span data-ttu-id="a093b-118">一列包含提取的字词，另一列包含分数。</span><span class="sxs-lookup"><span data-stu-id="a093b-118">One column contains the extracted terms and the other column contains the score.</span></span> <span data-ttu-id="a093b-119">列的默认名称是 "**字词**" 和 `Score` 。</span><span class="sxs-lookup"><span data-stu-id="a093b-119">The default names of the columns are **Term** and `Score`.</span></span> <span data-ttu-id="a093b-120">由于输入中的文本列可能包含多个字词，所以字词提取转换输出的行通常比输入的多。</span><span class="sxs-lookup"><span data-stu-id="a093b-120">Because the text column in the input may contain multiple terms, the output of the Term Extraction transformation typically has more rows than the input.</span></span>  
  
 <span data-ttu-id="a093b-121">如果提取字词写入表中，则其他查找转换（如字词查找、模糊查找和查找转换）可以使用它们。</span><span class="sxs-lookup"><span data-stu-id="a093b-121">If the extracted terms are written to a table, they can be used by other lookup transformation such as the Term Lookup, Fuzzy Lookup, and Lookup transformations.</span></span>  
  
 <span data-ttu-id="a093b-122">字词提取转换仅可用于 DT_WSTR 或 DT_NTEXT 数据类型的列中的文本。</span><span class="sxs-lookup"><span data-stu-id="a093b-122">The Term Extraction transformation can work only with text in a column that has either the DT_WSTR or the DT_NTEXT data type.</span></span> <span data-ttu-id="a093b-123">如果列包含文本但其数据类型不是这些之一，则可使用数据转换向数据流添加 DT_WSTR 或 DT_NTEXT 数据类型的列并将该列值复制到新列。</span><span class="sxs-lookup"><span data-stu-id="a093b-123">If a column contains text but does not have one of these data types, the Data Conversion transformation can be used to add a column with the DT_WSTR or DT_NTEXT data type to the data flow and copy the column values to the new column.</span></span> <span data-ttu-id="a093b-124">然后，数据转换的输出可用作对字词提取转换的输入。</span><span class="sxs-lookup"><span data-stu-id="a093b-124">The output from the Data Conversion transformation can then be used as the input to the Term Extraction transformation.</span></span> <span data-ttu-id="a093b-125">有关详细信息，请参阅 [Data Conversion Transformation](data-conversion-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="a093b-125">For more information, see [Data Conversion Transformation](data-conversion-transformation.md).</span></span>  
  
## <a name="exclusion-terms"></a><span data-ttu-id="a093b-126">排除字词</span><span class="sxs-lookup"><span data-stu-id="a093b-126">Exclusion Terms</span></span>  
 <span data-ttu-id="a093b-127">根据需要，字词提取转换还可以引用包含排除字词（表示转换从数据集中提取字词时应跳过的字词）的表中的列。</span><span class="sxs-lookup"><span data-stu-id="a093b-127">Optionally, the Term Extraction transformation can reference a column in a table that contains exclusion terms, meaning terms that the transformation should skip when it extracts terms from a data set.</span></span> <span data-ttu-id="a093b-128">当一组字词在特定业务或行业中已标识为不重要（通常是由于该字词出现频率过高，以致其成为干扰词）时，这会很有用。</span><span class="sxs-lookup"><span data-stu-id="a093b-128">This is useful when a set of terms has already been identified as inconsequential in a particular business and industry, typically because the term occurs with such high frequency that it becomes a noise word.</span></span> <span data-ttu-id="a093b-129">例如，从包含特定汽车品牌的客户支持信息的数据集中提取字词时，品牌本身由于过于频繁地被提到而变得毫无意义，因此可以排除。</span><span class="sxs-lookup"><span data-stu-id="a093b-129">For example, when extracting terms from a data set that contains customer support information about a particular brand of cars, the brand name itself might be excluded because it is mentioned too frequently to have significance.</span></span> <span data-ttu-id="a093b-130">因此，排除列表中的值必须按照正在使用中的数据集进行自定义。</span><span class="sxs-lookup"><span data-stu-id="a093b-130">Therefore, the values in the exclusion list must be customized to the data set you are working with.</span></span>  
  
 <span data-ttu-id="a093b-131">如果将某一字词添加到排除列表中，则包含该字词的所有字词（不论是单词还是名词短语）也都将被排除。</span><span class="sxs-lookup"><span data-stu-id="a093b-131">When you add a term to the exclusion list, all the terms-words or noun phrases-that contain the term are also excluded.</span></span> <span data-ttu-id="a093b-132">例如，如果排除列表中包含单个单词 *data*，则包含该单词的所有字词（如 *data*、 *data mining*、 *data integrity*和 *data validation* ）也都将被排除。</span><span class="sxs-lookup"><span data-stu-id="a093b-132">For example, if the exclusion list includes the single word *data*, then all the terms that contain this word, such as *data*, *data mining*, *data integrity*, and *data validation* will also be excluded.</span></span> <span data-ttu-id="a093b-133">如果只希望排除包含单词 *data*的复合词，则必须将这些复合字词显式添加到排除列表中。</span><span class="sxs-lookup"><span data-stu-id="a093b-133">If you want to exclude only compounds that contain the word *data*, you must explicitly add those compound terms to the exclusion list.</span></span> <span data-ttu-id="a093b-134">例如，如果要提取 *data*，而排除 *data validation*，则需要将 *data validation* 添加到排除列表中，并确保将 *data* 从排除列表中删除。</span><span class="sxs-lookup"><span data-stu-id="a093b-134">For example, if you want to extract incidences of *data*, but exclude *data validation*, you would add *data validation* to the exclusion list, and make sure that *data* is removed from the exclusion list.</span></span>  
  
 <span data-ttu-id="a093b-135">引用表必须是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或 Access 数据库中的一个表。</span><span class="sxs-lookup"><span data-stu-id="a093b-135">The reference table must be a table in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or an Access database.</span></span> <span data-ttu-id="a093b-136">字词提取转换使用单独的 OLE DB 连接以便连接到引用表。</span><span class="sxs-lookup"><span data-stu-id="a093b-136">The Term Extraction transformation uses a separate OLE DB connection to connect to the reference table.</span></span> <span data-ttu-id="a093b-137">有关详细信息，请参阅 [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="a093b-137">For more information, see [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="a093b-138">字词提取转换在完全预缓存模式下工作。</span><span class="sxs-lookup"><span data-stu-id="a093b-138">The Term Extraction transformation works in a fully precached mode.</span></span> <span data-ttu-id="a093b-139">在运行时，字词提取转换从引用表中读取排除字词并将这些字词存储在转换的专用内存中，然后才处理任何转换输入行。</span><span class="sxs-lookup"><span data-stu-id="a093b-139">At run time, the Term Extraction transformation reads the exclusion terms from the reference table and stores them in its private memory before it processes any transformation input rows.</span></span>  
  
## <a name="extraction-of-terms-from-text"></a><span data-ttu-id="a093b-140">从文本中提取字词</span><span class="sxs-lookup"><span data-stu-id="a093b-140">Extraction of Terms from Text</span></span>  
 <span data-ttu-id="a093b-141">若要从文本中提取字词，字词提取转换要执行下列任务。</span><span class="sxs-lookup"><span data-stu-id="a093b-141">To extract terms from text, the Term Extraction transformation performs the following tasks.</span></span>  
  
### <a name="identification-of-words"></a><span data-ttu-id="a093b-142">单词的标识</span><span class="sxs-lookup"><span data-stu-id="a093b-142">Identification of Words</span></span>  
 <span data-ttu-id="a093b-143">首先，字词提取转换执行下列任务以标识单词：</span><span class="sxs-lookup"><span data-stu-id="a093b-143">First, the Term Extraction transformation identifies words by performing the following tasks:</span></span>  
  
-   <span data-ttu-id="a093b-144">使用英语中的空格、换行符和其他单词终止符将文本分隔为单词。</span><span class="sxs-lookup"><span data-stu-id="a093b-144">Separating text into words by using spaces, line breaks, and other word terminators in the English language.</span></span> <span data-ttu-id="a093b-145">例如，标点符号（如 *?*</span><span class="sxs-lookup"><span data-stu-id="a093b-145">For example, punctuation marks such as *?*</span></span> <span data-ttu-id="a093b-146">和 *:* 为断字符。</span><span class="sxs-lookup"><span data-stu-id="a093b-146">and *:* are word-breaking characters.</span></span>  
  
-   <span data-ttu-id="a093b-147">保留由连字符或下划线连接的单词。</span><span class="sxs-lookup"><span data-stu-id="a093b-147">Preserving words that are connected by hyphens or underscores.</span></span> <span data-ttu-id="a093b-148">例如，单词 *copy-protected* 和 *read-only* 保留为一个单词。</span><span class="sxs-lookup"><span data-stu-id="a093b-148">For example, the words *copy-protected* and *read-only* remain one word.</span></span>  
  
-   <span data-ttu-id="a093b-149">原封不动地保留包含句点的首字母缩略词。</span><span class="sxs-lookup"><span data-stu-id="a093b-149">Keeping intact acronyms that include periods.</span></span> <span data-ttu-id="a093b-150">例如， *A.B.C* Company 将词汇切分为 **ABC** 和 **Company**。</span><span class="sxs-lookup"><span data-stu-id="a093b-150">For example, the *A.B.C* Company would be tokenized as **ABC** and **Company**.</span></span>  
  
-   <span data-ttu-id="a093b-151">拆分带有特殊字符的单词。</span><span class="sxs-lookup"><span data-stu-id="a093b-151">Splitting words on special characters.</span></span> <span data-ttu-id="a093b-152">例如，单词 *date/time* 提取为 *date* 和 *time*， *(bicycle)* 提取为 *bicycle*，而 C# 则视为 C。特殊字符将被放弃且不能被编入词汇。</span><span class="sxs-lookup"><span data-stu-id="a093b-152">For example, the word *date/time* is extracted as *date* and *time*, *(bicycle)* as *bicycle*, and C# is treated as C. Special characters are discarded and cannot be lexicalized.</span></span>  
  
-   <span data-ttu-id="a093b-153">确认诸如撇号之类的特殊字符何时不应拆分单词。</span><span class="sxs-lookup"><span data-stu-id="a093b-153">Recognizing when special characters such as the apostrophe should not split words.</span></span> <span data-ttu-id="a093b-154">例如，词 *bicycle's* 不会拆分为两个单词，而是生成一个词 *bicycle* （名词）。</span><span class="sxs-lookup"><span data-stu-id="a093b-154">For example, the word *bicycle's* is not split into two words, and yields the single term *bicycle* (noun).</span></span>  
  
-   <span data-ttu-id="a093b-155">拆分时间表达式、货币表达式、电子邮件地址和邮寄地址。</span><span class="sxs-lookup"><span data-stu-id="a093b-155">Splitting time expressions, monetary expressions, e-mail addresses, and postal addresses.</span></span> <span data-ttu-id="a093b-156">例如，日期 *January 31, 2004* 可分隔为三个标记， *January*、 *31*和 *2004*。</span><span class="sxs-lookup"><span data-stu-id="a093b-156">For example, the date *January 31, 2004* is separated into the three tokens *January*, *31*, and *2004*.</span></span>  
  
### <a name="tagged-words"></a><span data-ttu-id="a093b-157">带标记的单词</span><span class="sxs-lookup"><span data-stu-id="a093b-157">Tagged Words</span></span>  
 <span data-ttu-id="a093b-158">第二，字词提取转换将单词标记为下列词类之一：</span><span class="sxs-lookup"><span data-stu-id="a093b-158">Second, the Term Extraction transformation tags words as one of the following parts of speech:</span></span>  
  
-   <span data-ttu-id="a093b-159">单数形式的名词。</span><span class="sxs-lookup"><span data-stu-id="a093b-159">A noun in the singular form.</span></span> <span data-ttu-id="a093b-160">例如， *bicycle* 和 *potato*。</span><span class="sxs-lookup"><span data-stu-id="a093b-160">For example, *bicycle* and *potato*.</span></span>  
  
-   <span data-ttu-id="a093b-161">复数形式的名词。</span><span class="sxs-lookup"><span data-stu-id="a093b-161">A noun in the plural form.</span></span> <span data-ttu-id="a093b-162">例如， *bicycles* 和 *potatoes*。</span><span class="sxs-lookup"><span data-stu-id="a093b-162">For example, *bicycles* and *potatoes*.</span></span> <span data-ttu-id="a093b-163">所有未按异体形式进行归类的复数名词要进行词干提取。</span><span class="sxs-lookup"><span data-stu-id="a093b-163">All plural nouns that are not lemmatized are subject to stemming.</span></span>  
  
-   <span data-ttu-id="a093b-164">单数形式的专有名词。</span><span class="sxs-lookup"><span data-stu-id="a093b-164">A proper noun in the singular form.</span></span> <span data-ttu-id="a093b-165">例如， *April* 和 *Peter*。</span><span class="sxs-lookup"><span data-stu-id="a093b-165">For example, *April* and *Peter*.</span></span>  
  
-   <span data-ttu-id="a093b-166">复数形式的专有名词。</span><span class="sxs-lookup"><span data-stu-id="a093b-166">A proper noun in the plural form.</span></span> <span data-ttu-id="a093b-167">例如， *Aprils* 和 *Peters*。</span><span class="sxs-lookup"><span data-stu-id="a093b-167">For example *Aprils* and *Peters*.</span></span> <span data-ttu-id="a093b-168">对于要进行词干提取的专有名词来说，它必须为内部词典（仅限于标准英文单词）的一部分。</span><span class="sxs-lookup"><span data-stu-id="a093b-168">For a proper noun to be subject to stemming, it must be a part of the internal lexicon, which is limited to standard English words.</span></span>  
  
-   <span data-ttu-id="a093b-169">形容词。</span><span class="sxs-lookup"><span data-stu-id="a093b-169">An adjective.</span></span> <span data-ttu-id="a093b-170">例如， *blue*。</span><span class="sxs-lookup"><span data-stu-id="a093b-170">For example, *blue*.</span></span>  
  
-   <span data-ttu-id="a093b-171">对两个事物进行比较的比较级形容词。</span><span class="sxs-lookup"><span data-stu-id="a093b-171">A comparative adjective that compares two things.</span></span> <span data-ttu-id="a093b-172">例如， *higher* 和 *taller*。</span><span class="sxs-lookup"><span data-stu-id="a093b-172">For example, *higher* and *taller*.</span></span>  
  
-   <span data-ttu-id="a093b-173">标识事物的性质高于或低于至少其他两个事物的形容词最高级。</span><span class="sxs-lookup"><span data-stu-id="a093b-173">A superlative adjective that identifies a thing that has a quality above or below the level of at least two others.</span></span> <span data-ttu-id="a093b-174">例如， *highest* 和 *tallest*。</span><span class="sxs-lookup"><span data-stu-id="a093b-174">For example, *highest* and *tallest*.</span></span>  
  
-   <span data-ttu-id="a093b-175">数词。</span><span class="sxs-lookup"><span data-stu-id="a093b-175">A number.</span></span> <span data-ttu-id="a093b-176">例如， *62* 和 *2004*。</span><span class="sxs-lookup"><span data-stu-id="a093b-176">For example, *62* and *2004*.</span></span>  
  
 <span data-ttu-id="a093b-177">不属于以上词类的单词将被放弃。</span><span class="sxs-lookup"><span data-stu-id="a093b-177">Words that are not one of these parts of speech are discarded.</span></span> <span data-ttu-id="a093b-178">例如，动词和代词将被放弃。</span><span class="sxs-lookup"><span data-stu-id="a093b-178">For example, verbs and pronouns are discarded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a093b-179">词类是根据统计模型进行标记的，因此标记可能不完全准确。</span><span class="sxs-lookup"><span data-stu-id="a093b-179">The tagging of parts of speech is based on a statistical model and the tagging may not be completely accurate.</span></span>  
  
 <span data-ttu-id="a093b-180">如果将字词提取转换配置为仅提取名词，那么将只提取标记为单数或复数形式的名词和专有名词的单词。</span><span class="sxs-lookup"><span data-stu-id="a093b-180">If the Term Extraction transformation is configured to extract only nouns, only the words that are tagged as singular or plural forms of nouns and proper nouns are extracted.</span></span>  
  
 <span data-ttu-id="a093b-181">如果将字词提取转换配置为仅提取名词短语，那么标记为名词、专有名词、形容词和数词的单词可以组合成名词短语，但该短语必须包含至少一个标记为单数或复数形式的名词或者专有名词的单词。</span><span class="sxs-lookup"><span data-stu-id="a093b-181">If the Term Extraction transformation is configured to extract only noun phrases, words that are tagged as nouns, proper nouns, adjectives, and numbers may be combined to make a noun phrase, but the phrase must include at least one word that is tagged as a singular or plural form of a noun or a proper noun.</span></span> <span data-ttu-id="a093b-182">例如，名词短语 *highest mountain* 由标记为形容词最高级的单词 (*highest*) 和标记为名词的单词 (*mountain*) 组成。</span><span class="sxs-lookup"><span data-stu-id="a093b-182">For example, the noun phrase *highest mountain* combines a word tagged as a superlative adjective (*highest*) and a word tagged as noun (*mountain*).</span></span>  
  
 <span data-ttu-id="a093b-183">如果将字词提取转换配置为可提取名词和名词短语，那么对名词和名词短语的规则都适用。</span><span class="sxs-lookup"><span data-stu-id="a093b-183">If the Term Extraction is configured to extract both nouns and noun phrases, both the rules for nouns and the rules for noun phrases apply.</span></span> <span data-ttu-id="a093b-184">例如，转换从文本 *many beautiful blue bicycles* 中提取 *bicycle* 和 *beautiful blue bicycle*。</span><span class="sxs-lookup"><span data-stu-id="a093b-184">For example, the transformation extracts *bicycle* and *beautiful blue bicycle* from the text *many beautiful blue bicycles*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a093b-185">提取的字词仍然受转换所使用的最大字词长度和频率阈值的限制。</span><span class="sxs-lookup"><span data-stu-id="a093b-185">The extracted terms remain subject to the maximum term length and frequency threshold that the transformation uses.</span></span>  
  
### <a name="stemmed-words"></a><span data-ttu-id="a093b-186">词干字词</span><span class="sxs-lookup"><span data-stu-id="a093b-186">Stemmed Words</span></span>  
 <span data-ttu-id="a093b-187">字词提取转换还可以提取名词词干，从而仅提取名词的单数形式。</span><span class="sxs-lookup"><span data-stu-id="a093b-187">The Term Extraction transformation also stems nouns to extract only the singular form of a noun.</span></span> <span data-ttu-id="a093b-188">例如，转换从 *men* 中提取 *man*，从 *mice* 中提取 *mouse*以及从 *bicycles* 中提取 *bicycle*。</span><span class="sxs-lookup"><span data-stu-id="a093b-188">For example, the transformation extracts *man* from *men*, *mouse* from *mice*, and *bicycle* from *bicycles*.</span></span> <span data-ttu-id="a093b-189">转换使用其字典来提取名词词干。</span><span class="sxs-lookup"><span data-stu-id="a093b-189">The transformation uses its dictionary to stem nouns.</span></span> <span data-ttu-id="a093b-190">其字典中的动名词将视为名词。</span><span class="sxs-lookup"><span data-stu-id="a093b-190">Gerunds are treated as nouns if they are in the dictionary.</span></span>  
  
 <span data-ttu-id="a093b-191">字词提取转换使用其内部字典，将单词的词干提取为其字典格式，如这些示例中所示。</span><span class="sxs-lookup"><span data-stu-id="a093b-191">The Term Extraction transformation stems words to their dictionary form as shown in these examples by using the dictionary internal to the Term Extraction transformation.</span></span>  
  
-   <span data-ttu-id="a093b-192">删除名词中的 *s* 。</span><span class="sxs-lookup"><span data-stu-id="a093b-192">Removing *s* from nouns.</span></span> <span data-ttu-id="a093b-193">例如， *bicycles* 变为 *bicycle*。</span><span class="sxs-lookup"><span data-stu-id="a093b-193">For example, *bicycles* becomes *bicycle*.</span></span>  
  
-   <span data-ttu-id="a093b-194">删除名词中的 *es* 。</span><span class="sxs-lookup"><span data-stu-id="a093b-194">Removing *es* from nouns.</span></span> <span data-ttu-id="a093b-195">例如， *stories* 变为 *story*。</span><span class="sxs-lookup"><span data-stu-id="a093b-195">For example, *stories* becomes *story*.</span></span>  
  
-   <span data-ttu-id="a093b-196">从字典中检索不规则名词的单数形式。</span><span class="sxs-lookup"><span data-stu-id="a093b-196">Retrieving the singular form for irregular nouns from the dictionary.</span></span> <span data-ttu-id="a093b-197">例如， *geese* 变为 *goose*。</span><span class="sxs-lookup"><span data-stu-id="a093b-197">For example, *geese* becomes *goose*.</span></span>  
  
### <a name="normalized-words"></a><span data-ttu-id="a093b-198">规范化的字词</span><span class="sxs-lookup"><span data-stu-id="a093b-198">Normalized Words</span></span>  
 <span data-ttu-id="a093b-199">对仅因位于句首而大写的字词，字词提取转换一律采用其非首字母大写形式。</span><span class="sxs-lookup"><span data-stu-id="a093b-199">The Term Extraction transformation normalizes terms that are capitalized only because of their position in a sentence, and uses their non-capitalized form instead.</span></span> <span data-ttu-id="a093b-200">例如，在短语 *Dogs chase cats* 和 *Mountain paths are steep*中， *Dogs* 和 *Mountain* 将被规范为 *dog* 和 *mountain*。</span><span class="sxs-lookup"><span data-stu-id="a093b-200">For example, in the phrases *Dogs chase cats* and *Mountain paths are steep*, *Dogs* and *Mountain* would be normalized to *dog* and *mountain*.</span></span>  
  
 <span data-ttu-id="a093b-201">字词提取转换对单词进行规范，从而不将大写和非大写单词视为不同的字词。</span><span class="sxs-lookup"><span data-stu-id="a093b-201">The Term Extraction transformation normalizes words so that the capitalized and noncapitalized versions of words are not treated as different terms.</span></span> <span data-ttu-id="a093b-202">例如，在文本 *You see many bicycles in Seattle* 和 *Bicycles are blue*中， *bicycles* 和 *Bicycles* 识别为相同的字词并且转换仅保留 *bicycle*。</span><span class="sxs-lookup"><span data-stu-id="a093b-202">For example, in the text *You see many bicycles in Seattle* and *Bicycles are blue*, *bicycles* and *Bicycles* are recognized as the same term and the transformation keeps only *bicycle*.</span></span> <span data-ttu-id="a093b-203">内部字典中未列出的专有名词和单词不进行规范。</span><span class="sxs-lookup"><span data-stu-id="a093b-203">Proper nouns and words that are not listed in the internal dictionary are not normalized.</span></span>  
  
### <a name="case-sensitive-normalization"></a><span data-ttu-id="a093b-204">区分大小写的规范</span><span class="sxs-lookup"><span data-stu-id="a093b-204">Case-Sensitive Normalization</span></span>  
 <span data-ttu-id="a093b-205">字词提取转换可以配置为将小写和大写单词视为不同的字词，或者相同字词的不同变体。</span><span class="sxs-lookup"><span data-stu-id="a093b-205">The Term Extraction transformation can be configured to consider lowercase and uppercase words as either distinct terms, or as different variants of the same term.</span></span>  
  
-   <span data-ttu-id="a093b-206">如果将转换配置为可识别大小写，则 *Method* 和 *method* 这样的字词将被提取为两个不同的字词。</span><span class="sxs-lookup"><span data-stu-id="a093b-206">If the transformation is configured to recognize differences in case, terms like *Method* and *method* are extracted as two different terms.</span></span> <span data-ttu-id="a093b-207">对非句首词的大写单词从不进行规范，并将其标记为专有名词。</span><span class="sxs-lookup"><span data-stu-id="a093b-207">Capitalized words that are not the first word in a sentence are never normalized, and are tagged as proper nouns.</span></span>  
  
-   <span data-ttu-id="a093b-208">如果将转换配置为不区分大小写，则如 *Method* 和 *method* 这样的字词将被识别为单个字词的变体。</span><span class="sxs-lookup"><span data-stu-id="a093b-208">If the transformation is configured to be case-insensitive, terms like *Method* and *method* are recognized as variants of a single term.</span></span> <span data-ttu-id="a093b-209">提取的字词列表可能包括 *Method* 或 *method*，这取决于哪个单词首先出现在输入数据集中。</span><span class="sxs-lookup"><span data-stu-id="a093b-209">The list of extracted terms might include either *Method* or *method*, depending on which word occurs first in the input data set.</span></span> <span data-ttu-id="a093b-210">如果 *Method* 仅因其是句首词而大写，则将以规范形式提取它。</span><span class="sxs-lookup"><span data-stu-id="a093b-210">If *Method* is capitalized only because it is the first word in a sentence, it is extracted in normalized form.</span></span>  
  
## <a name="sentence-and-word-boundaries"></a><span data-ttu-id="a093b-211">句子和词边界</span><span class="sxs-lookup"><span data-stu-id="a093b-211">Sentence and Word Boundaries</span></span>  
 <span data-ttu-id="a093b-212">字词提取转换使用下列字符作为句子边界将文本分隔为多个句子：</span><span class="sxs-lookup"><span data-stu-id="a093b-212">The Term Extraction transformation separates text into sentences using the following characters as sentence boundaries:</span></span>  
  
-   <span data-ttu-id="a093b-213">ASCII 换行字符 0x0d（回车符）和 0x0a（换行符）。</span><span class="sxs-lookup"><span data-stu-id="a093b-213">ASCII line-break characters 0x0d (carriage return) and 0x0a (line feed).</span></span> <span data-ttu-id="a093b-214">若要使用此字符作为句子的边界，则每行中必须有两个或更多的换行字符。</span><span class="sxs-lookup"><span data-stu-id="a093b-214">To use this character as a sentence boundary, there must be two or more line-break characters in a row.</span></span>  
  
-   <span data-ttu-id="a093b-215">连字符 (-)。</span><span class="sxs-lookup"><span data-stu-id="a093b-215">Hyphens (-).</span></span> <span data-ttu-id="a093b-216">若要将此字符用作句子边界，连字符左侧和右侧的字符均不能为字母。</span><span class="sxs-lookup"><span data-stu-id="a093b-216">To use this character as a sentence boundary, neither the character to the left nor to the right of the hyphen can be a letter.</span></span>  
  
-   <span data-ttu-id="a093b-217">下划线 (_)。</span><span class="sxs-lookup"><span data-stu-id="a093b-217">Underscore (_).</span></span> <span data-ttu-id="a093b-218">若要将此字符用作句子边界，连字符左侧和右侧的字符均不能为字母。</span><span class="sxs-lookup"><span data-stu-id="a093b-218">To use this character as a sentence boundary, neither the character to the left nor to the right of the hyphen can be a letter.</span></span>  
  
-   <span data-ttu-id="a093b-219">小于等于 0x19 或大于等于 0x7b 的所有 Unicode 字符。</span><span class="sxs-lookup"><span data-stu-id="a093b-219">All Unicode characters that are less than or equal to 0x19, or greater than or equal to 0x7b.</span></span>  
  
-   <span data-ttu-id="a093b-220">数字、标点符号和字母字符的组合。</span><span class="sxs-lookup"><span data-stu-id="a093b-220">Combinations of numbers, punctuation marks, and alphabetical characters.</span></span> <span data-ttu-id="a093b-221">例如， *A23B#99* 返回字词 *A23B*。</span><span class="sxs-lookup"><span data-stu-id="a093b-221">For example, *A23B#99* returns the term *A23B*.</span></span>  
  
-   <span data-ttu-id="a093b-222">字符：%、@，&、$、#、\*、:、;、.、,、!、?、\<, >、+、=、^、~、|、\\、/、(、)、[、]、{、}、" 和 '。</span><span class="sxs-lookup"><span data-stu-id="a093b-222">The characters, %, @, &, $, #, \*, :, ;, ., **,** , !, ?, \<, >, +, =, ^, ~, |, \\, /, (, ), [, ], {, }, ", and '.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a093b-223">包括一个或多个句点 (.) 的首字母缩略词不分隔为多个句子。</span><span class="sxs-lookup"><span data-stu-id="a093b-223">Acronyms that include one or more periods (.) are not separated into multiple sentences.</span></span>  
  
 <span data-ttu-id="a093b-224">然后，字词提取转换使用下列词边界将句子分隔为单词：</span><span class="sxs-lookup"><span data-stu-id="a093b-224">The Term Extraction transformation then separates the sentence into words using the following word boundaries:</span></span>  
  
-   <span data-ttu-id="a093b-225">Space</span><span class="sxs-lookup"><span data-stu-id="a093b-225">Space</span></span>  
  
-   <span data-ttu-id="a093b-226">选项卡</span><span class="sxs-lookup"><span data-stu-id="a093b-226">Tab</span></span>  
  
-   <span data-ttu-id="a093b-227">ASCII 0x0d（回车符）</span><span class="sxs-lookup"><span data-stu-id="a093b-227">ASCII 0x0d (carriage return)</span></span>  
  
-   <span data-ttu-id="a093b-228">ASCII 0x0a（换行符）</span><span class="sxs-lookup"><span data-stu-id="a093b-228">ASCII 0x0a (line feed)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a093b-229">如果缩写的单词中包含撇号，如 *we're* 或 *it's*，则在撇号处断词，否则，撇号后的字母将被剪裁掉。</span><span class="sxs-lookup"><span data-stu-id="a093b-229">If an apostrophe is in a word that is a contraction, such as *we're* or *it's*, the word is broken at the apostrophe; otherwise, the letters following the apostrophe are trimmed.</span></span> <span data-ttu-id="a093b-230">例如， *we're* 拆分为 *we* 和 *'re*，而 *bicycle's* 则剪裁为 *bicycle*。</span><span class="sxs-lookup"><span data-stu-id="a093b-230">For example, *we're* is split into *we* and *'re*, and *bicycle's* is trimmed to *bicycle*.</span></span>  
  
## <a name="configuration-of-the-term-extraction-transformation"></a><span data-ttu-id="a093b-231">配置字词提取转换</span><span class="sxs-lookup"><span data-stu-id="a093b-231">Configuration of the Term Extraction Transformation</span></span>  
 <span data-ttu-id="a093b-232">文本提取转换使用内部算法和统计模型来生成其结果。</span><span class="sxs-lookup"><span data-stu-id="a093b-232">The Text Extraction transformation uses internal algorithms and statistical models to generate its results.</span></span> <span data-ttu-id="a093b-233">可能需要多次运行字词提取转换并检查结果，以配置转换使其生成用于文本挖掘解决方案的结果类型。</span><span class="sxs-lookup"><span data-stu-id="a093b-233">You may have to run the Term Extraction transformation several times and examine the results to configure the transformation to generate the type of results that works for your text mining solution.</span></span>  
  
 <span data-ttu-id="a093b-234">字词提取转换有一个常规输入、一个输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="a093b-234">The Term Extraction transformation has one regular input, one output, and one error output.</span></span>  
  
 <span data-ttu-id="a093b-235">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="a093b-235">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="a093b-236">有关可在 **“字词提取转换编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="a093b-236">For more information about the properties that you can set in the **Term Extraction Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="a093b-237">字词提取转换编辑器（“字词提取”选项卡）</span><span class="sxs-lookup"><span data-stu-id="a093b-237">Term Extraction Transformation Editor &#40;Term Extraction Tab&#41;</span></span>](../../term-extraction-transformation-editor-term-extraction-tab.md)  
  
-   [<span data-ttu-id="a093b-238">字词提取转换编辑器（“排除”选项卡）</span><span class="sxs-lookup"><span data-stu-id="a093b-238">Term Extraction Transformation Editor &#40;Exclusion Tab&#41;</span></span>](../../term-extraction-transformation-editor-exclusion-tab.md)  
  
-   [<span data-ttu-id="a093b-239">字词提取转换编辑器（“高级”选项卡）</span><span class="sxs-lookup"><span data-stu-id="a093b-239">Term Extraction Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../term-extraction-transformation-editor-advanced-tab.md)  
  
 <span data-ttu-id="a093b-240">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="a093b-240">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="a093b-241">Common Properties</span><span class="sxs-lookup"><span data-stu-id="a093b-241">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="a093b-242">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="a093b-242">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="a093b-243">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="a093b-243">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
