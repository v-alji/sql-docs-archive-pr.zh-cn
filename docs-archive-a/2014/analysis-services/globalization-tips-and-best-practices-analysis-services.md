---
title: 全球化提示和最佳做法 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- translations [Analysis Services], client applications
- date comparisons
- day-of-week comparisons [Analysis Services]
- time [Analysis Services]
- month comparisons [Analysis Services]
ms.assetid: 71a8c438-1370-4c69-961e-d067ee4e47c2
author: minewiskan
ms.author: owend
ms.openlocfilehash: c5bf99878a08e3d2ca57b76e3f902fded2099381
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590977"
---
# <a name="globalization-tips-and-best-practices-analysis-services"></a><span data-ttu-id="0e739-102">全球化提示和最佳实践 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="0e739-102">Globalization Tips and Best Practices (Analysis Services)</span></span>
  <span data-ttu-id="0e739-103">**[!INCLUDE[applies](../includes/applies-md.md)]** 仅多维</span><span class="sxs-lookup"><span data-stu-id="0e739-103">**[!INCLUDE[applies](../includes/applies-md.md)]**  Multidimensional only</span></span>  
  
 <span data-ttu-id="0e739-104">这些提示和准则有助于提高你的商业智能解决方案的可移植性，并避免直接与语言和排序规则设置相关的错误。</span><span class="sxs-lookup"><span data-stu-id="0e739-104">These tips and guidelines can help increase the portability of your business intelligence solutions and avoid errors that are directly related to language and collation settings.</span></span>  
  
-   [<span data-ttu-id="0e739-105">在整个堆栈中使用相似排序规则</span><span class="sxs-lookup"><span data-stu-id="0e739-105">Use similar collations throughout the stack</span></span>](#bkmk_sameColl)  
  
-   [<span data-ttu-id="0e739-106">通用排序规则建议</span><span class="sxs-lookup"><span data-stu-id="0e739-106">Common collation recommendations</span></span>](#bkmk_recos)  
  
-   [<span data-ttu-id="0e739-107">对象标识符区分大小写</span><span class="sxs-lookup"><span data-stu-id="0e739-107">Case sensitivity of object identifiers</span></span>](#bkmk_objid)  
  
-   [<span data-ttu-id="0e739-108">使用 Excel 和 SQL Server Profiler 进行区域设置测试</span><span class="sxs-lookup"><span data-stu-id="0e739-108">Locale testing using Excel and SQL Server Profiler</span></span>](#bkmk_test)  
  
-   [<span data-ttu-id="0e739-109">在包含翻译的解决方案中编写 MDX 查询</span><span class="sxs-lookup"><span data-stu-id="0e739-109">Writing MDX queries in a solution containing Translations</span></span>](#bkmk_mdx)  
  
-   [<span data-ttu-id="0e739-110">编写包含日期和时间值的 MDX 查询</span><span class="sxs-lookup"><span data-stu-id="0e739-110">Writing MDX queries containing Date and Time Values</span></span>](#bkmk_datetime)  
  
##  <a name="use-similar-collations-throughout-the-stack"></a><a name="bkmk_sameColl"></a><span data-ttu-id="0e739-111">在整个堆栈中使用相似的排序规则</span><span class="sxs-lookup"><span data-stu-id="0e739-111">Use similar collations throughout the stack</span></span>  
 <span data-ttu-id="0e739-112">如果可能，请在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中使用与用于数据库引擎的排序规则设置相同的排序规则设置，尽量采用一致的全半角区分、大小写区分以及重音区分。</span><span class="sxs-lookup"><span data-stu-id="0e739-112">If possible, try to use the same collation settings in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you use for the database engine, striving for correspondence in width-sensitivity and case-sensitivity, and access-sensitivity.</span></span>  
  
 <span data-ttu-id="0e739-113">每个服务都有其自己的排序规则设置，数据库引擎默认设置为 SQL_Latin1_General_CP1_CI_AS 且 Analysis Services 设置为 Latin1_General_AS。</span><span class="sxs-lookup"><span data-stu-id="0e739-113">Each service has its own collation settings, with the database engine default set to SQL_Latin1_General_CP1_CI_AS and Analysis Services set to Latin1_General_AS.</span></span> <span data-ttu-id="0e739-114">在区分大小写、区分全半角和区分重音方面，默认设置是兼容的。</span><span class="sxs-lookup"><span data-stu-id="0e739-114">The defaults are compatible in term of case, width, and accent sensitivity.</span></span> <span data-ttu-id="0e739-115">请注意，如果你改变任一排序规则的设置，则在排序规则属性以基本方式分离时会遇到问题。</span><span class="sxs-lookup"><span data-stu-id="0e739-115">Be forewarned that if you vary the settings of either collation, you can run into problems when the collation properties diverge in fundamental ways.</span></span>  
  
 <span data-ttu-id="0e739-116">即便排序规则设置功能相当，你也会遇到特殊情况，即每个服务对字符串内任意位置的空格做出不同解释。</span><span class="sxs-lookup"><span data-stu-id="0e739-116">Even when collation settings are functionally equivalent, you can run into a special case where an empty space anywhere within a string is interpreted differently by each service.</span></span>  
  
 <span data-ttu-id="0e739-117">空格字符是“特殊情况”，因为它能以 Unicode 格式用单字节字符集 (SBCS) 或双字节字符集 (DBCS) 来表示。</span><span class="sxs-lookup"><span data-stu-id="0e739-117">The space character is a 'special case' because it can be represented as a single-byte (SBCS) or double-byte character set (DBCS) in Unicode.</span></span> <span data-ttu-id="0e739-118">在关系引擎中，两个由空格隔开的复合字符串 - 一个使用 SBCS，另一个使用 DBCS - 被视为相同。</span><span class="sxs-lookup"><span data-stu-id="0e739-118">In the relational engine, two compound strings separated by a space -- one using SBCS, the other in DBCS -- are considered identical.</span></span> <span data-ttu-id="0e739-119">在 Analysis Services 中，处理期间，同样的两个复合字符串不等同，第二个实例将被标记为副本。</span><span class="sxs-lookup"><span data-stu-id="0e739-119">In Analysis Services, during processing, the same two compound strings are not identical, and the second instance will be flagged as a duplicate.</span></span>  
  
 <span data-ttu-id="0e739-120">有关详细信息和建议的解决方法，请参见 [根据不同的排序规则，Unicode 字符串中的空白具有不同的处理结果](https://social.technet.microsoft.com/wiki/contents/articles/23979.ssas-processing-error-blanks-in-a-unicode-string-have-different-processing-outcomes-based-on-collation-and-character-set.aspx)。</span><span class="sxs-lookup"><span data-stu-id="0e739-120">For more details and suggested workarounds, see [Blanks in a Unicode string have different processing outcomes based on collation](https://social.technet.microsoft.com/wiki/contents/articles/23979.ssas-processing-error-blanks-in-a-unicode-string-have-different-processing-outcomes-based-on-collation-and-character-set.aspx).</span></span>  
  
##  <a name="common-collation-recommendations"></a><a name="bkmk_recos"></a> <span data-ttu-id="0e739-121">通用排序规则建议</span><span class="sxs-lookup"><span data-stu-id="0e739-121">Common collation recommendations</span></span>  
 <span data-ttu-id="0e739-122">Analysis Services 始终显示所有可用语言和排序规则的完整列表；它不基于你所选的语言来筛选排序规则。</span><span class="sxs-lookup"><span data-stu-id="0e739-122">Analysis Services always presents the full list of all available languages and collations; it does not filter the collations based on the language you selected.</span></span> <span data-ttu-id="0e739-123">请务必选择可操作的组合。</span><span class="sxs-lookup"><span data-stu-id="0e739-123">Be sure to choose a workable combination.</span></span>  
  
 <span data-ttu-id="0e739-124">一些更常使用的排序规则包括以下列表中的排序规则。</span><span class="sxs-lookup"><span data-stu-id="0e739-124">Some of the more commonly used collations include those in the following list.</span></span>  
  
 <span data-ttu-id="0e739-125">你应该考虑将此列表作为进一步调查的起点，而非排除其他选项的最终建议。</span><span class="sxs-lookup"><span data-stu-id="0e739-125">You should consider this list to be a starting point for further investigation, rather than a definitive recommendation that excludes other options.</span></span> <span data-ttu-id="0e739-126">你可能会发现未专门建议使用的排序规则最适用于你的数据。</span><span class="sxs-lookup"><span data-stu-id="0e739-126">You might find that a collation not specifically recommended is the one that works best for your data.</span></span> <span data-ttu-id="0e739-127">彻底的测试是验证是否正确排序或比较数据值的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="0e739-127">Thorough testing is the only way to verify whether data values are sorted and compared appropriately.</span></span> <span data-ttu-id="0e739-128">与以前一样，测试排序规则时，务必运行处理和查询工作负荷。</span><span class="sxs-lookup"><span data-stu-id="0e739-128">As always, be sure to run both processing and query workloads when testing collation.</span></span>  
  
-   <span data-ttu-id="0e739-129">Latin1_General_100_AS 通常用于使用 [ISO 基本拉丁字母表](http://en.wikipedia.org/wiki/ISO_basic_Latin_alphabet)26 个字符的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0e739-129">Latin1_General_100_AS is often used for applications that use the 26 characters of the [ISO basic Latin alphabet](http://en.wikipedia.org/wiki/ISO_basic_Latin_alphabet).</span></span>  
  
-   <span data-ttu-id="0e739-130">包含斯堪的纳维亚字母（如 ø）的北欧语言可使用 Finnish_Swedish_100。</span><span class="sxs-lookup"><span data-stu-id="0e739-130">North European languages that include Scandinavian letters (such as ø) can use Finnish_Swedish_100.</span></span>  
  
-   <span data-ttu-id="0e739-131">东欧语言（例如俄语）通常使用 Cyrillic_General_100。</span><span class="sxs-lookup"><span data-stu-id="0e739-131">East European languages, such as Russian, often use Cyrillic_General_100.</span></span>  
  
-   <span data-ttu-id="0e739-132">中文语言和排序规则因地区而异，但通常不是简体中文就是繁体中文。</span><span class="sxs-lookup"><span data-stu-id="0e739-132">Chinese language and collations vary by region, but are generally either Chinese Simplified or Chinese Traditional.</span></span>  
  
     <span data-ttu-id="0e739-133">在中国和新加坡，Microsoft 技术支持部门通常见到的是简体中文，简体中文以拼音作为首选的排序方式。</span><span class="sxs-lookup"><span data-stu-id="0e739-133">In PRC and Singapore, Microsoft Support tends to see Simplified Chinese, with Pinyin as the preferred sort order.</span></span> <span data-ttu-id="0e739-134">建议使用的排序规则是 Chinese_PRC（用于 SQL Server 2000）、Chinese_PRC_90（用于 SQL Server 2005）或 Chinese_Simplified_Pinyin_100（用于 SQL Server 2008 和更高版本）。</span><span class="sxs-lookup"><span data-stu-id="0e739-134">The recommended collations are Chinese_PRC (for SQL Server 2000), Chinese_PRC_90 (for SQL Server 2005) or Chinese_Simplified_Pinyin_100 (for SQL Server 2008 and later).</span></span>  
  
     <span data-ttu-id="0e739-135">在中国台湾地区，更常见的是繁体中文，建议使用的是基于笔画数的排序方式：Chinese_Taiwan_Stroke（用于 SQL Server 2000）、Chinese_Taiwan_Stroke_90（用于 SQL Server 2005）或 Chinese_Traditional_Stroke_Count_100（用于 SQL Server 2008 和更高版本）。</span><span class="sxs-lookup"><span data-stu-id="0e739-135">In Taiwan, it is more common to see Traditional Chinese with the recommended sort order is based on Stroke Count: Chinese_Taiwan_Stroke (for SQL Server 2000), Chinese_Taiwan_Stroke_90 (for SQL Server 2005) or Chinese_Traditional_Stroke_Count_100 (for SQL Server 2008 and later).</span></span>  
  
     <span data-ttu-id="0e739-136">其他区域 (例如香港特别行政区特别行政区和澳门特别行政区) 也使用繁体中文。</span><span class="sxs-lookup"><span data-stu-id="0e739-136">Other regions (such as Hong Kong SAR and Macao SAR) also use Traditional Chinese.</span></span> <span data-ttu-id="0e739-137">在中国香港，就排序规则而言，Chinese_Hong_Kong_Stroke_90（在 SQL Server 2005 上）的使用较为常见。</span><span class="sxs-lookup"><span data-stu-id="0e739-137">For collations, in Hong Kong, it's not unusual to see Chinese_Hong_Kong_Stroke_90 (on SQL Server 2005).</span></span> <span data-ttu-id="0e739-138">在澳门特别行政区，SQL Server 2008 和更高) 版本上的 Chinese_Traditional_Stroke_Count_100 (会相当频繁地使用。</span><span class="sxs-lookup"><span data-stu-id="0e739-138">In Macao, Chinese_Traditional_Stroke_Count_100 (on SQL Server 2008 and later) is used fairly often.</span></span>  
  
-   <span data-ttu-id="0e739-139">对于日语，最常使用的排序规则是 Japanese_CI_AS。</span><span class="sxs-lookup"><span data-stu-id="0e739-139">For Japanese, the most commonly used collation is Japanese_CI_AS.</span></span> <span data-ttu-id="0e739-140">Japanese_XJIS_100 用于支持 [JIS2004](http://en.wikipedia.org/wiki/JIS_X_0213)的安装。</span><span class="sxs-lookup"><span data-stu-id="0e739-140">Japanese_XJIS_100 is used in installations supporting [JIS2004](http://en.wikipedia.org/wiki/JIS_X_0213).</span></span> <span data-ttu-id="0e739-141">Japanese_BIN2 的使用通常见于数据迁移项目，用于由非 Windows 平台或数据源而非 SQL Server 关系数据引擎发出的数据。</span><span class="sxs-lookup"><span data-stu-id="0e739-141">Japanese_BIN2 is typically seen in data migration projects, with data originating from non-Windows platforms, or from data sources other than the SQL Server relational database engine.</span></span>  
  
     <span data-ttu-id="0e739-142">Japanese_Bushu_Kakusu_100 很少见于运行 Analysis Services 工作负荷的服务器。</span><span class="sxs-lookup"><span data-stu-id="0e739-142">Japanese_Bushu_Kakusu_100 is rarely seen in servers that run Analysis Services workloads.</span></span>  
  
-   <span data-ttu-id="0e739-143">建议针对朝鲜语使用 Korean_100。</span><span class="sxs-lookup"><span data-stu-id="0e739-143">Korean_100 is recommended for Korean.</span></span> <span data-ttu-id="0e739-144">虽然在列表中 Korean_Wansung_Unicode 仍可用，但不推荐使用。</span><span class="sxs-lookup"><span data-stu-id="0e739-144">Although Korean_Wansung_Unicode is still available in the list, it has been deprecated.</span></span>  
  
##  <a name="case-sensitivity-of-object-identifiers"></a><a name="bkmk_objid"></a><span data-ttu-id="0e739-145">对象标识符区分大小写</span><span class="sxs-lookup"><span data-stu-id="0e739-145">Case sensitivity of object identifiers</span></span>  
 <span data-ttu-id="0e739-146">在 SQL Server 2012 SP2 中启动，对象 ID 区分大小写独立于排序规则而强制执行，但是行为随着语言变化：</span><span class="sxs-lookup"><span data-stu-id="0e739-146">Starting in SQL Server 2012 SP2, case sensitivity of object IDs is enforced independently of the collation, but the behavior varies by language:</span></span>  
  
|<span data-ttu-id="0e739-147">语言脚本</span><span class="sxs-lookup"><span data-stu-id="0e739-147">Language script</span></span>|<span data-ttu-id="0e739-148">事例敏感性</span><span class="sxs-lookup"><span data-stu-id="0e739-148">Case sensitivity</span></span>|  
|---------------------|----------------------|  
|<span data-ttu-id="0e739-149">**基本拉丁字母表**</span><span class="sxs-lookup"><span data-stu-id="0e739-149">**Basic Latin alphabet**</span></span>|<span data-ttu-id="0e739-150">以拉丁语脚本表示的对象标识符（任意 26 个英语大写或小写字母）将视为区分大小写，无论排序规则如何。</span><span class="sxs-lookup"><span data-stu-id="0e739-150">Object identifiers expressed in Latin script (any of the 26 English upper or lower case letters) are treated as case-insensitive, regardless of collation.</span></span> <span data-ttu-id="0e739-151">例如，以下对象 ID 被认为是相同的：54321**abcdef**、54321**ABCDEF**、54321**AbCdEf**。</span><span class="sxs-lookup"><span data-stu-id="0e739-151">For example, the following object IDs are considered identical: 54321**abcdef**, 54321**ABCDEF**, 54321**AbCdEf**.</span></span> <span data-ttu-id="0e739-152">在内部，Analysis Services 将字符串中的字符都视作是大写，然后执行与语言无关的简单字节比较。</span><span class="sxs-lookup"><span data-stu-id="0e739-152">Internally, Analysis Services treats the characters in the string as if all are uppercase, and then performs a simple byte comparison that is independent of language.</span></span><br /><br /> <span data-ttu-id="0e739-153">请注意，只有这 26 个字符会受到影响。</span><span class="sxs-lookup"><span data-stu-id="0e739-153">Note that only the 26 characters are affected.</span></span> <span data-ttu-id="0e739-154">如果语言是西欧语言，但使用斯堪的纳维亚语言字符，则其他字符将不为大写。</span><span class="sxs-lookup"><span data-stu-id="0e739-154">If the language is West European, but uses Scandinavian characters, the additional character will not be upper-cased.</span></span>|  
|<span data-ttu-id="0e739-155">**西里尔语，希腊语，科普特语，亚美尼亚语**</span><span class="sxs-lookup"><span data-stu-id="0e739-155">**Cyrillic, Greek, Coptic, Armenian**</span></span>|<span data-ttu-id="0e739-156">非拉丁语双脚本中的对象标识符（如西里尔语）总是区分大小写。</span><span class="sxs-lookup"><span data-stu-id="0e739-156">Object identifiers in non-Latin bicameral script, such as Cyrillic, are always case-sensitive.</span></span> <span data-ttu-id="0e739-157">例如，Измерение 和 измерение 被视为两个不同值，尽管唯一的区别是首字母的大小写。</span><span class="sxs-lookup"><span data-stu-id="0e739-157">For example, Измерение and измерение are considered two distinct values, even though the only difference is the case of the first letter.</span></span>|  
  
 <span data-ttu-id="0e739-158">**对象标识符区分大小写的意义**</span><span class="sxs-lookup"><span data-stu-id="0e739-158">**Implications of case-sensitivity for object identifiers**</span></span>  
  
 <span data-ttu-id="0e739-159">仅对象标识符（而非对象名）受限于表中描述的大小写行为。</span><span class="sxs-lookup"><span data-stu-id="0e739-159">Only object identifiers, and not object names, are subject to the casing behaviors described in the table.</span></span> <span data-ttu-id="0e739-160">如果你看到解决方案工作方式有所变化（之前和之后的比较 - 安装 SQL Server 2012 SP2 或更高版本之后），它将最可能是一个处理问题。</span><span class="sxs-lookup"><span data-stu-id="0e739-160">If you see a change in how your solution works (a before and after comparison -- after installing SQL Server 2012 SP2 or later), it will most likely be a processing issue.</span></span> <span data-ttu-id="0e739-161">查询不受对象标识符影响。</span><span class="sxs-lookup"><span data-stu-id="0e739-161">Queries are not impacted by object identifiers.</span></span> <span data-ttu-id="0e739-162">对于两种查询语言（DAX 和 MDX），公式引擎会使用对象名（而非标识符）。</span><span class="sxs-lookup"><span data-stu-id="0e739-162">For both query languages (DAX and MDX), the formula engine uses the object name (not the identifier).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e739-163">与区分大小写相关的代码更改对某些应用程序来说是重大更改。</span><span class="sxs-lookup"><span data-stu-id="0e739-163">Code changes related to case-sensitivity have been a breaking change for some applications.</span></span> <span data-ttu-id="0e739-164">有关详细信息，请参阅[SQL Server 2014 中 Analysis Services 功能的重大更改](breaking-changes-to-analysis-services-features-in-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="0e739-164">See [Breaking Changes to Analysis Services Features in SQL Server 2014](breaking-changes-to-analysis-services-features-in-sql-server-2014.md) for more information.</span></span>  
  
##  <a name="locale-testing-using-excel-sql-server-profiler-and-sql-server-management-studio"></a><a name="bkmk_test"></a> <span data-ttu-id="0e739-165">使用 Excel、SQL Server Profiler 和 SQL Server Management Studio 进行区域设置测试</span><span class="sxs-lookup"><span data-stu-id="0e739-165">Locale testing using Excel, SQL Server Profiler and SQL Server Management Studio</span></span>  
 <span data-ttu-id="0e739-166">测试翻译时，连接必须指定翻译的 LCID。</span><span class="sxs-lookup"><span data-stu-id="0e739-166">When testing translations, the connection must specify the LCID of the translation.</span></span> <span data-ttu-id="0e739-167">如 [从 SSAS 获取不同语言到 Excel](http://extremeexperts.com/sql/Tips/ExcelDiffLocale.aspx)中所述，你可以使用 Excel 测试你的翻译。</span><span class="sxs-lookup"><span data-stu-id="0e739-167">As documented in [Get Different Language from SSAS into Excel](http://extremeexperts.com/sql/Tips/ExcelDiffLocale.aspx), you can use Excel to test your translations.</span></span>  
  
 <span data-ttu-id="0e739-168">你可以通过手动编辑 .odc 文件以包括区域设置标识符连接字符串属性来实现此操作。</span><span class="sxs-lookup"><span data-stu-id="0e739-168">You can do this by hand editing the .odc file to include the locale identifier connection string property.</span></span> <span data-ttu-id="0e739-169">使用 Adventure Works 示例多维数据库尝试此操作。</span><span class="sxs-lookup"><span data-stu-id="0e739-169">Try this out with the Adventure Works sample multidimensional database.</span></span>  
  
-   <span data-ttu-id="0e739-170">搜索现有的 .odc 文件。</span><span class="sxs-lookup"><span data-stu-id="0e739-170">Search for existing .odc files.</span></span> <span data-ttu-id="0e739-171">当你找到一个 Adventure Works 多维数据库时，右键单击该文件在记事本中将其打开。</span><span class="sxs-lookup"><span data-stu-id="0e739-171">When you find the one for Adventure Works multidimensional, right-click the file to open it in Notepad.</span></span>  
  
-   <span data-ttu-id="0e739-172">将 `Locale Identifier=1036` 添加到连接字符串。</span><span class="sxs-lookup"><span data-stu-id="0e739-172">Add `Locale Identifier=1036` to the connection string.</span></span> <span data-ttu-id="0e739-173">保存并关闭该文件。</span><span class="sxs-lookup"><span data-stu-id="0e739-173">Save and close the file.</span></span>  
  
-   <span data-ttu-id="0e739-174">打开 Excel |**数据**  | **现有连接**。</span><span class="sxs-lookup"><span data-stu-id="0e739-174">Open Excel | **Data** | **Existing Connections**.</span></span> <span data-ttu-id="0e739-175">在列表中筛选此计算机上的连接文件。</span><span class="sxs-lookup"><span data-stu-id="0e739-175">Filter the list to just connections files on this computer.</span></span> <span data-ttu-id="0e739-176">查找 Adventure Works 的连接（仔细查看名称；你可能发现不止一个）。</span><span class="sxs-lookup"><span data-stu-id="0e739-176">Find the connection for Adventure Works (look at the name carefully; you might have more than one).</span></span> <span data-ttu-id="0e739-177">打开连接。</span><span class="sxs-lookup"><span data-stu-id="0e739-177">Open the connection.</span></span>  
  
     <span data-ttu-id="0e739-178">你会看到 Adventure Works 示例数据库的法语翻译。</span><span class="sxs-lookup"><span data-stu-id="0e739-178">You should see the French translations from the Adventure Works sample database.</span></span>  
  
     <span data-ttu-id="0e739-179">![带有法语翻译的 Excel 数据透视表](media/ssas-localetest-excel.png "带有法语翻译的 Excel 数据透视表")</span><span class="sxs-lookup"><span data-stu-id="0e739-179">![Excel PivotTable with French translations](media/ssas-localetest-excel.png "Excel PivotTable with French translations")</span></span>  
  
 <span data-ttu-id="0e739-180">作为后续步骤，可以使用 Server Profiler 来确认区域设置。</span><span class="sxs-lookup"><span data-stu-id="0e739-180">As a follow up, you can use SQL Server Profiler to confirm the locale.</span></span> <span data-ttu-id="0e739-181">单击一个 `Session Initialize` 事件，然后查看下方文本区域中的属性列表以找到 `<localeidentifier>1036</localeidentifier>`。</span><span class="sxs-lookup"><span data-stu-id="0e739-181">Click a `Session Initialize` event and then look at the property list in the text area below to find `<localeidentifier>1036</localeidentifier>`.</span></span>  
  
 <span data-ttu-id="0e739-182">在 Management Studio 中，你可以指定服务器连接上的区域设置标识符。</span><span class="sxs-lookup"><span data-stu-id="0e739-182">In Management Studio, you can specify Locale Identifier on a server connection.</span></span>  
  
-   <span data-ttu-id="0e739-183">在对象资源管理器 |**连接**  | **Analysis Services**  | **选项**，单击 "**其他连接参数**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="0e739-183">In Object Explorer | **Connect** | **Analysis Services** | **Options**, click the **Additional Connection Parameters** tab.</span></span>  
  
-   <span data-ttu-id="0e739-184">输入 `Local Identifier=1036` ，然后单击 \*\*\*\*“连接”。</span><span class="sxs-lookup"><span data-stu-id="0e739-184">Enter `Local Identifier=1036` and then click **Connect**.</span></span>  
  
-   <span data-ttu-id="0e739-185">对 Adventure Works 数据库执行 MDX 查询。</span><span class="sxs-lookup"><span data-stu-id="0e739-185">Execute an MDX query against the Adventure Works database.</span></span> <span data-ttu-id="0e739-186">查询结果应为法语翻译。</span><span class="sxs-lookup"><span data-stu-id="0e739-186">The query results should be the French translations.</span></span>  
  
     <span data-ttu-id="0e739-187">![SSMS 中带法语翻译的 MDX 查询](media/ssas-localetest-ssms.png "SSMS 中带法语翻译的 MDX 查询")</span><span class="sxs-lookup"><span data-stu-id="0e739-187">![MDX query with French translations in SSMS](media/ssas-localetest-ssms.png "MDX query with French translations in SSMS")</span></span>  
  
##  <a name="writing-mdx-queries-in-a-solution-containing-translations"></a><a name="bkmk_mdx"></a> <span data-ttu-id="0e739-188">在包含翻译的解决方案中撰写 MDX 查询</span><span class="sxs-lookup"><span data-stu-id="0e739-188">Writing MDX queries in a solution containing Translations</span></span>  
 <span data-ttu-id="0e739-189">翻译提供 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象名称的显示信息，但是不翻译相同对象的标识符。</span><span class="sxs-lookup"><span data-stu-id="0e739-189">Translations provide display information for the names of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects, but the identifiers for the same objects are not translated.</span></span> <span data-ttu-id="0e739-190">尽可能使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象的标识符和键，而不使用翻译后的标题和名称。</span><span class="sxs-lookup"><span data-stu-id="0e739-190">Whenever possible, use the identifiers and keys for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects instead of the translated captions and names.</span></span> <span data-ttu-id="0e739-191">例如，使用多维表达式 (MDX) 语句和脚本的成员键而不是成员名称以确保多种语言之间的可移植性。</span><span class="sxs-lookup"><span data-stu-id="0e739-191">For example, use member keys instead of member names for Multidimensional Expressions (MDX) statements and scripts to ensure portability across multiple languages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e739-192">回想一下，表格对象名总是区分大小写，无论排序规则如何。</span><span class="sxs-lookup"><span data-stu-id="0e739-192">Recall that tabular object names are always case-insensitive, regardless of collation.</span></span> <span data-ttu-id="0e739-193">另一方面，多维对象名区分排序规则的大小写。</span><span class="sxs-lookup"><span data-stu-id="0e739-193">Multidimensional object names, on the other hand, follow the case sensitivity of the collation.</span></span> <span data-ttu-id="0e739-194">由于仅多维对象名区分大小写，请确保所有引用多维对象的 MDX 查询的大小写正确。</span><span class="sxs-lookup"><span data-stu-id="0e739-194">Since only multidimensional object names are case-sensitive make sure that all MDX queries referencing multidimensional objects are cased correctly.</span></span>  
  
##  <a name="writing-mdx-queries-containing-date-and-time-values"></a><a name="bkmk_datetime"></a> <span data-ttu-id="0e739-195">撰写包含日期和时间值的 MDX 查询</span><span class="sxs-lookup"><span data-stu-id="0e739-195">Writing MDX queries containing Date and Time Values</span></span>  
 <span data-ttu-id="0e739-196">以下建议能使你的基于日期和时间的 MDX 查询在不同语言之间更易于移植：</span><span class="sxs-lookup"><span data-stu-id="0e739-196">The following suggestions to make your date and time-based MDX queries more portable across different languages:</span></span>  
  
1.  <span data-ttu-id="0e739-197">**使用数值部分进行比较与操作**</span><span class="sxs-lookup"><span data-stu-id="0e739-197">**Use numeric parts for comparisons and operations**</span></span>  
  
     <span data-ttu-id="0e739-198">执行月份和星期的比较和操作时，请使用数值日期和时间部分，不要使用等效的字符串（例如，使用 MonthNumberofYear 而不是 MonthName）。</span><span class="sxs-lookup"><span data-stu-id="0e739-198">When you perform month and day-of-week comparisons and operations, use the numeric date and time parts instead of the string equivalents (for example, use MonthNumberofYear instead of MonthName).</span></span> <span data-ttu-id="0e739-199">数值受语言翻译的差异的影响最小。</span><span class="sxs-lookup"><span data-stu-id="0e739-199">Numeric values are least affected by differences in language translations.</span></span>  
  
2.  <span data-ttu-id="0e739-200">**在结果集中使用等效的字符串**</span><span class="sxs-lookup"><span data-stu-id="0e739-200">**Use string equivalents in a result set**</span></span>  
  
     <span data-ttu-id="0e739-201">生成面向最终用户的结果集时，考虑使用此字符串（如 MonthName），那么你的多语言受众就能从你提供的翻译中获益。</span><span class="sxs-lookup"><span data-stu-id="0e739-201">When building result sets seen by end-users, consider using the string (such as MonthName) so that your multi-lingual audience can benefit from the translations you've provided.</span></span>  
  
3.  <span data-ttu-id="0e739-202">**使用 ISO 日期格式表示通用日期和时间信息**</span><span class="sxs-lookup"><span data-stu-id="0e739-202">**Use ISO date formats for universal date and time information**</span></span>  
  
     <span data-ttu-id="0e739-203">一个 [Analysis Services 专家](http://geekswithblogs.net/darrengosbell/Default.aspx) 提出了这一建议：“我一直对传递到 SQL 或 MDX 中的查询的任何日期字符串使用 ISO 日期格式 yyyy-mm-dd，因为它很明确而且无论客户端或服务器的区域设置如何都将正常工作。</span><span class="sxs-lookup"><span data-stu-id="0e739-203">One [Analysis Services expert](http://geekswithblogs.net/darrengosbell/Default.aspx) has this recommendation: "I always use the ISO date format yyyy-mm-dd for any date strings that I pass in to queries in SQL or MDX because it's unambiguous and will work regardless of the client or server's regional settings.</span></span> <span data-ttu-id="0e739-204">我同意在分析不明确的日期格式时服务器应遵从其区域设置，但是我也认为如果你已有不对解释开放的选项，总之最好选择那个选项。”</span><span class="sxs-lookup"><span data-stu-id="0e739-204">I would agree that the server should defer to its regional settings when parsing an ambiguous date format, but I also think that if you've got an option that is not open to interpretation that you are better choosing that anyway".</span></span>  
  
4.  `Use the Format function to enforce a specific format, regardless of regional language settings`  
  
     <span data-ttu-id="0e739-205">以下 MDX 查询（借用自一个论坛帖子）演示了如何使用 Format 以指定格式返回日期，不管基础区域设置如何。</span><span class="sxs-lookup"><span data-stu-id="0e739-205">The following MDX query, borrowed from a forum post, illustrates how to use Format to return dates in a specific format, irrespective of the underlying regional settings.</span></span>  
  
     <span data-ttu-id="0e739-206">请参阅 [SSAS 2012 generates invalid dates](http://www.networksteve.com/forum/topic.php/SSAS_2012_generates_invalid_dates/?TopicId=40504&Posts=2) （SSAS 2012 生成无效日期）（Network Steve 上的论坛帖子）查看原始帖子内容。</span><span class="sxs-lookup"><span data-stu-id="0e739-206">See [SSAS 2012 generates invalid dates (forum post on Network Steve](http://www.networksteve.com/forum/topic.php/SSAS_2012_generates_invalid_dates/?TopicId=40504&Posts=2) for the original post.</span></span>  
  
    ```  
    WITH MEMBER [LinkTimeAdd11Date_Manual] as Format(dateadd("d",15,"2014-12-11"), "mm/dd/yyyy")  
    member [LinkTimeAdd15Date_Manual] as Format(dateadd("d",11,"2014-12-13"), "mm/dd/yyyy")  
    SELECT  
    { [LinkTimeAdd11Date_Manual]  
    ,[LinkTimeAdd15Date_Manual]  
    }  
    ON COLUMNS   
    FROM [Adventure Works]  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0e739-207">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e739-207">See Also</span></span>  
 <span data-ttu-id="0e739-208">[Analysis Services 多维的全球化方案](globalization-scenarios-for-analysis-services-multiidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="0e739-208">[Globalization scenarios for Analysis Services Multidimensional](globalization-scenarios-for-analysis-services-multiidimensional.md) </span></span>  
 [<span data-ttu-id="0e739-209">编写国际化 Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="0e739-209">Write International Transact-SQL Statements</span></span>](../relational-databases/collations/write-international-transact-sql-statements.md)  
