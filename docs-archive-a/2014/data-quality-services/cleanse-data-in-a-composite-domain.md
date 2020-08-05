---
title: 清理复合域中的数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 7d1076e0-7710-469a-9107-e293e4bd80ac
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c9e00342933f18112707e43b479bced763eca44c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580893"
---
# <a name="cleanse-data-in-a-composite-domain"></a><span data-ttu-id="0b7b8-102">清理复合域中的数据</span><span class="sxs-lookup"><span data-stu-id="0b7b8-102">Cleanse Data in a Composite Domain</span></span>
  <span data-ttu-id="0b7b8-103">本主题提供有关清理 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中的复合域的信息。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-103">This topic provides information about cleansing of composite domains in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="0b7b8-104">一个复合域由两个或更多的单一域构成，并且映射到一个由多个相关字词构成的数据字段。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-104">A composite domain consists of two or more single domains, and maps to a data field that consists of multiple related terms.</span></span> <span data-ttu-id="0b7b8-105">复合域中的单独的域必须具有一个共同的知识范畴。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-105">The individual domains in a composite domain must have a common area of knowledge.</span></span> <span data-ttu-id="0b7b8-106">有关复合域的详细信息，请参阅 [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-106">For detailed information about composite domains, see [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md).</span></span>  
  
##  <a name="mapping-a-composite-domain-to-the-source-data"></a><a name="Mapping"></a> <span data-ttu-id="0b7b8-107">将复合域映射到源数据</span><span class="sxs-lookup"><span data-stu-id="0b7b8-107">Mapping a Composite Domain to the Source Data</span></span>  
 <span data-ttu-id="0b7b8-108">有两种方法可以将源数据映射到复合域：</span><span class="sxs-lookup"><span data-stu-id="0b7b8-108">There are two ways in which you can map your source data to a composite domain:</span></span>  
  
-   <span data-ttu-id="0b7b8-109">源数据是单个字段（即“全名”），该字段映射到某个复合域。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-109">The source data is a single field (let's say Full Name), which is mapped to a composite domain.</span></span>  
  
    -   <span data-ttu-id="0b7b8-110">如果该复合域映射到某一引用数据服务，则源数据将按原样发送到引用数据服务以便进行更正和分析。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-110">If the composite domain is mapped to a reference data service, the source data will be sent as is to the reference data service for correction and parsing.</span></span>  
  
    -   <span data-ttu-id="0b7b8-111">如果该复合域未映射到某一引用数据服务，则将基于为该复合域定义的分析方法对复合域进行分析。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-111">If the composite domain is not mapped to a reference data service, will be parsed based on the parsing method defined for the composite domain.</span></span> <span data-ttu-id="0b7b8-112">有关为复合域指定分析方法的详细信息，请参阅 [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-112">For more information about specifying a parsing method for composite domains, see [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md)</span></span>  
  
-   <span data-ttu-id="0b7b8-113">源数据由多个字段构成（例如“名字”、“中间名”和“姓氏”），这些字段映射到复合域内的单独域。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-113">The source data consists of multiple fields (let's say First Name, Middle Name, and Last Name), which are mapped to individual domains within a composite domain.</span></span>  
  
 <span data-ttu-id="0b7b8-114">有关如何将复合域映射到源数据的示例，请参阅[将域或复合域附加到引用数据](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-114">For an example of how to map composite domains to source data, see [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>  
  
##  <a name="data-correction-using-definitive-cross-domain-rules"></a><a name="CDCorrection"></a> <span data-ttu-id="0b7b8-115">使用明确的跨域规则更正数据</span><span class="sxs-lookup"><span data-stu-id="0b7b8-115">Data Correction using Definitive Cross-Domain Rules</span></span>  
 <span data-ttu-id="0b7b8-116">通过复合域中的跨域规则，您可以创建指示一个复合域中各域之间的关系的规则。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-116">Cross-domain rules in composite domain enable you to create rules that indicate relationship between individual domains in a composite domain.</span></span> <span data-ttu-id="0b7b8-117">在您对涉及复合域的源数据运行清理活动时将考虑跨域规则。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-117">Cross-domain rules are taken into account when you run the cleansing activity on your source data involving composite domains.</span></span> <span data-ttu-id="0b7b8-118">除了让您知道跨域规则的有效性之外，明确的 *Then* 跨域规则 **“值等于”** 还在数据清理活动过程中更正数据。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-118">Apart from just letting you know about the validity of a cross-domain rule, the definitive *Then* cross-domain rule, **Value is equal to**, also corrects the data during the data-cleansing activity.</span></span>  
  
 <span data-ttu-id="0b7b8-119">请考虑下面的示例：有一个复合域 Product，该复合域有三个单独的域：ProductName、CompanyName 和 ProductVersion。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-119">Consider the following example: there is a composite domain, Product, with three individual domains: ProductName, CompanyName, and ProductVersion.</span></span> <span data-ttu-id="0b7b8-120">创建以下明确的跨域规则：</span><span class="sxs-lookup"><span data-stu-id="0b7b8-120">Create the following definitive cross-domain rule:</span></span>  
  
 <span data-ttu-id="0b7b8-121">如果域 "公司名称" 的值包含*Microsoft* ，并且域 "Productname" 值等于 " *Office* "，并且 "ProductVersion" 值等于*2010* ，则域 "ProductName" 的值等于*Microsoft Office 2010*。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-121">IF Domain 'CompanyName' Value contains *Microsoft* and Domain 'ProductName' Value is equal to *Office* and 'ProductVersion' Value is equal to *2010* THEN Domain 'ProductName' Value is equal to *Microsoft Office 2010*.</span></span>  
  
 <span data-ttu-id="0b7b8-122">当此跨域规则运行时，源数据 (ProductName) 将在清理活动后进行如下更正：</span><span class="sxs-lookup"><span data-stu-id="0b7b8-122">When this cross-domain rule runs, the source data (ProductName) gets corrected to the following after the cleansing activity:</span></span>  
  
 <span data-ttu-id="0b7b8-123">**源数据**</span><span class="sxs-lookup"><span data-stu-id="0b7b8-123">**Source Data**</span></span>  
  
|<span data-ttu-id="0b7b8-124">ProductName</span><span class="sxs-lookup"><span data-stu-id="0b7b8-124">ProductName</span></span>|<span data-ttu-id="0b7b8-125">CompanyName</span><span class="sxs-lookup"><span data-stu-id="0b7b8-125">CompanyName</span></span>|<span data-ttu-id="0b7b8-126">ProductVersion</span><span class="sxs-lookup"><span data-stu-id="0b7b8-126">ProductVersion</span></span>|  
|-----------------|-----------------|--------------------|  
|<span data-ttu-id="0b7b8-127">Office</span><span class="sxs-lookup"><span data-stu-id="0b7b8-127">Office</span></span>|<span data-ttu-id="0b7b8-128">Microsoft Inc.</span><span class="sxs-lookup"><span data-stu-id="0b7b8-128">Microsoft Inc.</span></span>|<span data-ttu-id="0b7b8-129">2010</span><span class="sxs-lookup"><span data-stu-id="0b7b8-129">2010</span></span>|  
  
 <span data-ttu-id="0b7b8-130">**输出数据**</span><span class="sxs-lookup"><span data-stu-id="0b7b8-130">**Output Data**</span></span>  
  
|<span data-ttu-id="0b7b8-131">ProductName</span><span class="sxs-lookup"><span data-stu-id="0b7b8-131">ProductName</span></span>|<span data-ttu-id="0b7b8-132">CompanyName</span><span class="sxs-lookup"><span data-stu-id="0b7b8-132">CompanyName</span></span>|<span data-ttu-id="0b7b8-133">ProductVersion</span><span class="sxs-lookup"><span data-stu-id="0b7b8-133">ProductVersion</span></span>|  
|-----------------|-----------------|--------------------|  
|<span data-ttu-id="0b7b8-134">Microsoft Office 2010</span><span class="sxs-lookup"><span data-stu-id="0b7b8-134">Microsoft Office 2010</span></span>|<span data-ttu-id="0b7b8-135">Microsoft Inc.</span><span class="sxs-lookup"><span data-stu-id="0b7b8-135">Microsoft Inc.</span></span>|<span data-ttu-id="0b7b8-136">2010</span><span class="sxs-lookup"><span data-stu-id="0b7b8-136">2010</span></span>|  
  
 <span data-ttu-id="0b7b8-137">在您测试明确的 *Then* 跨域规则 **“值等于”** 时， **“测试复合域规则”** 对话框将包含一个新列 **“更正为”**，该列将显示正确的数据。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-137">When you test the definitive *Then* cross-domain rule, **Value is equal to**, the **Test Composite Domain Rule** dialog box contains a new column, **Correct To**, which displays the correct data.</span></span> <span data-ttu-id="0b7b8-138">在清理数据质量项目中，此明确的跨域规则将数据更改为100% 的置信度，**原因**列显示以下消息：已由规则 " *\<Cross-Domain Rule Name>* " 更正。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-138">In a cleansing data quality project, this definitive cross-domain rule changes the data with 100% confidence, and the **Reason** column displays the following message: Corrected by Rule '*\<Cross-Domain Rule Name>*'.</span></span> <span data-ttu-id="0b7b8-139">有关跨域规则的详细信息，请参阅 [Create a Cross-Domain Rule](../../2014/data-quality-services/create-a-cross-domain-rule.md)。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-139">For more information about cross domain rules, see [Create a Cross-Domain Rule](../../2014/data-quality-services/create-a-cross-domain-rule.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0b7b8-140">明确的跨域规则将不适用于附加到引用数据服务的复合域。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-140">The definitive cross-domain rule will not work for composite domains that are attached to reference data service.</span></span>  
  
##  <a name="data-profiling-for-composite-domains"></a><a name="DataProfiling"></a> <span data-ttu-id="0b7b8-141">针对复合域的数据事件探查</span><span class="sxs-lookup"><span data-stu-id="0b7b8-141">Data Profiling for Composite Domains</span></span>  
 <span data-ttu-id="0b7b8-142">DQS 事件探查在清理活动中提供两种数据质量维度： \*\* “完整性”（提供数据的范围）和 \*\* “准确性”（数据可用于目标用途的程度）。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-142">DQS profiling provides two data quality dimensions: *completeness* (the extent to which data is present) and *accuracy* (the extent to which data can be used for its intended use) during the cleansing activity.</span></span> <span data-ttu-id="0b7b8-143">事件探查不会提供有关复合域的可靠完整性统计信息。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-143">Profiling may not provide reliable completeness statistics for composite domains.</span></span> <span data-ttu-id="0b7b8-144">如果您需要完整性统计信息，请使用单一域而非复合域。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-144">If you need completeness statistics, use single domains instead of composite domains.</span></span> <span data-ttu-id="0b7b8-145">如果您要使用复合域，则最好使用用于进行事件探查的单一域创建一个知识库以确定完整性，并使用复合域创建另一个域来执行清理活动。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-145">If you want to use composite domains, you may want to create one knowledge base with single domains for profiling, to determine completeness, and create another domain with a composite domain for the cleansing activity.</span></span> <span data-ttu-id="0b7b8-146">例如，使用复合域时，事件探查可能对于地址记录显示 95% 的完整性，但对于其中一列（例如，邮政编码列）可能显示高得多的不完整性。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-146">For example, profiling could show 95% completeness for address records using a composite domain, but there could be a much higher level of incompleteness for one of the columns, for example, a postal (zip) code column.</span></span> <span data-ttu-id="0b7b8-147">在此示例中，您可能要衡量单一域的邮政编码列的完整性。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-147">In this example, you might want to measure the completeness of the zip code column with a single domain.</span></span>  
  
 <span data-ttu-id="0b7b8-148">事件探查可能为复合域提供可靠的准确性统计信息，因为您可以同时为多个列衡量准确性。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-148">Profiling will likely provide reliable accuracy statistics for composite domains because you can measure accuracy for multiple columns together.</span></span> <span data-ttu-id="0b7b8-149">此数据的值位于复合聚合中，因此，您最好使用复合域来衡量准确性。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-149">The value of this data is in the composite aggregation, so you may want to measure the accuracy with a composite domain.</span></span>  
  
 <span data-ttu-id="0b7b8-150">有关清理活动期间的数据事件探查的详细信息，请参阅[使用 DQS（内部）知识清理数据](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)中的[事件探查器统计信息](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Profiler)。</span><span class="sxs-lookup"><span data-stu-id="0b7b8-150">For detailed information about data profiling during the cleansing activity, see [Profiler Statistics](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Profiler) in [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).</span></span>  
  
  
