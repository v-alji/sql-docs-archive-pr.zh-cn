---
title: 管理域 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: c5ab71a3-0dac-45b1-be8e-93bf7e0e03ce
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 67f58df490bca5a811442fb33805ceb546de92d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578456"
---
# <a name="managing-a-domain"></a><span data-ttu-id="beba9-102">管理域</span><span class="sxs-lookup"><span data-stu-id="beba9-102">Managing a Domain</span></span>
  <span data-ttu-id="beba9-103">本主题介绍如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中使用域。</span><span class="sxs-lookup"><span data-stu-id="beba9-103">This topic describes the use of domains in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="beba9-104">域包含要分析的数据源的特定字段中数据的语义表示。</span><span class="sxs-lookup"><span data-stu-id="beba9-104">A domain contains a semantic representation of the data in a specific field in the data source that is to be analyzed.</span></span> <span data-ttu-id="beba9-105">域是您为数据源创建的知识库的一部分，并且，通过分析样本数据源或导入数据而逐步建立的知识将添加到在该知识库中定义的域。</span><span class="sxs-lookup"><span data-stu-id="beba9-105">A domain is part of the knowledge base that you create for a data source, and the knowledge that you build up by analyzing a sample data source, or importing data, is added to the domains defined in the knowledge base.</span></span> <span data-ttu-id="beba9-106">这些域中的知识随后用于在数据质量项目中执行清除和匹配。</span><span class="sxs-lookup"><span data-stu-id="beba9-106">The knowledge in those domains is later used to perform cleansing and matching in a data quality project.</span></span> <span data-ttu-id="beba9-107">域是 Data Quality Services 中所有活动的核心。</span><span class="sxs-lookup"><span data-stu-id="beba9-107">Domains are at the core of all activities in Data Quality Services.</span></span>  
  
 <span data-ttu-id="beba9-108">域映射到数据源字段，并在知识发现、域管理和匹配活动中进行填充。</span><span class="sxs-lookup"><span data-stu-id="beba9-108">A domain is mapped to a data source field, and is populated in the knowledge discovery, domain management, and matching activities.</span></span> <span data-ttu-id="beba9-109">如何从数据源加载数据以及如何在报表中输出数据是在域属性中定义的。</span><span class="sxs-lookup"><span data-stu-id="beba9-109">How you load data from the data source and output data in a report is defined in domain properties.</span></span> <span data-ttu-id="beba9-110">当您使用引用数据提供程序清理数据时，您会将引用数据服务附加到单一域或复合域。</span><span class="sxs-lookup"><span data-stu-id="beba9-110">When you use a reference data provider to cleanse data, you attach a reference data service to a single or composite domain.</span></span> <span data-ttu-id="beba9-111">创建要应用于域中数据的规则，并且可以为域创建基于字词的关系。</span><span class="sxs-lookup"><span data-stu-id="beba9-111">You create rules to be applied to your data in a domain, and you can create term-based relations for a domain.</span></span> <span data-ttu-id="beba9-112">您可以查看并更正域中的数据。</span><span class="sxs-lookup"><span data-stu-id="beba9-112">You can view and correct data in the domain.</span></span>  
  
 <span data-ttu-id="beba9-113">还可以创建复合域，该域包含两个或更多单一域，而每个单一域包含有关共用数据的知识。</span><span class="sxs-lookup"><span data-stu-id="beba9-113">You can also create a composite domain that is comprised of two or more individual domains that each contains knowledge about common data.</span></span> <span data-ttu-id="beba9-114">有关详细信息，请参阅[管理复合域](../../2014/data-quality-services/managing-a-composite-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="beba9-114">For more information, see [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md).</span></span>  
  
## <a name="domain-properties"></a><span data-ttu-id="beba9-115">域属性</span><span class="sxs-lookup"><span data-stu-id="beba9-115">Domain Properties</span></span>  
 <span data-ttu-id="beba9-116">当您创建域时，您具有以下有关如何从源数据填充域以及如何输出域值的选项。</span><span class="sxs-lookup"><span data-stu-id="beba9-116">When you create a domain, you have the following options for how to populate the domain from the source data and how to output the domain values.</span></span> <span data-ttu-id="beba9-117">有关详细信息，请参阅[设置域属性](../../2014/data-quality-services/set-domain-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="beba9-117">For more information, see [Set Domain Properties](../../2014/data-quality-services/set-domain-properties.md).</span></span>  
  
-   <span data-ttu-id="beba9-118">选择您用来填充域的数据的类型。</span><span class="sxs-lookup"><span data-stu-id="beba9-118">Select the type of the data that you populate the domain with.</span></span> <span data-ttu-id="beba9-119">有关每个域数据类型的支持的数据类型的信息，请参阅 [DQS 域支持的 SQL Server 和 SSIS 数据类型](../../2014/data-quality-services/supported-sql-server-and-ssis-data-types-for-dqs-domains.md)。</span><span class="sxs-lookup"><span data-stu-id="beba9-119">For information about data types supported for each domain data type, see [Supported SQL Server and SSIS Data Types for DQS Domains](../../2014/data-quality-services/supported-sql-server-and-ssis-data-types-for-dqs-domains.md).</span></span>  
  
-   <span data-ttu-id="beba9-120">指定仅从域中输出前导值，而不输出它们的同义词。</span><span class="sxs-lookup"><span data-stu-id="beba9-120">Specify that only leading values, not their synonyms, will be output from the domain.</span></span>  
  
-   <span data-ttu-id="beba9-121">指定使用特定的格式输出域值，具体取决于数据类型。</span><span class="sxs-lookup"><span data-stu-id="beba9-121">Specify that domain values be output in a certain format, depending on the data type.</span></span>  
  
-   <span data-ttu-id="beba9-122">如果数据类型为字符串，则可以通过在将该字符串从数据源加载到域时删除特殊字符来规范化该字符串。</span><span class="sxs-lookup"><span data-stu-id="beba9-122">If the data type is a string, you can normalize the string by removing special characters when the string is loaded from the data source into the domain.</span></span>  
  
-   <span data-ttu-id="beba9-123">如果数据类型为字符串，您可以运行 DQS 拼写检查器检查字符串值的语法、拼写和句子结构，并在 **“域管理”** 的 **“域值”** 页中指示可能存在的错误。</span><span class="sxs-lookup"><span data-stu-id="beba9-123">If the data type is a string, you can run the DQS Speller to check the syntax, spelling, and sentence structure of the string, and indicate any potential errors in the **Domain Values** page of **Domain Management**.</span></span> <span data-ttu-id="beba9-124">这包括指定运行拼写检查器的语言。</span><span class="sxs-lookup"><span data-stu-id="beba9-124">This includes specifying the language that the Speller will run in.</span></span>  
  
-   <span data-ttu-id="beba9-125">如果数据类型是字符串，当您知道字符串中不会出现语法错误时，您可以指定 DQS 不标识语法错误。</span><span class="sxs-lookup"><span data-stu-id="beba9-125">If the data type is a string, you can specify that DQS not identify syntax errors when you know that syntax errors will not occur in strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="beba9-126">本节内容</span><span class="sxs-lookup"><span data-stu-id="beba9-126">In This Section</span></span>  
 <span data-ttu-id="beba9-127">通过使用域，您可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="beba9-127">Using a domain enables you to do the following:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="beba9-128">为具有特定数据类型的数据字段创建语义表示，指定如何填充域以及如何设置域的输出格式</span><span class="sxs-lookup"><span data-stu-id="beba9-128">Create a semantic representation for a data field with a specific data type, specify how the domain is populated, and format the output of the domain</span></span>|[<span data-ttu-id="beba9-129">创建域</span><span class="sxs-lookup"><span data-stu-id="beba9-129">Create a Domain</span></span>](../../2014/data-quality-services/create-a-domain.md)|  
|<span data-ttu-id="beba9-130">将某个域链接到另一个域，使其能够共享相同的设置和值</span><span class="sxs-lookup"><span data-stu-id="beba9-130">Link a domain to another domain, enabling it to share the same settings and values</span></span>|[<span data-ttu-id="beba9-131">创建链接域</span><span class="sxs-lookup"><span data-stu-id="beba9-131">Create a Linked Domain</span></span>](../../2014/data-quality-services/create-a-linked-domain.md)|  
|<span data-ttu-id="beba9-132">将引用数据服务附加到单一域或复合域</span><span class="sxs-lookup"><span data-stu-id="beba9-132">Attach a reference data service to a single or composite domain</span></span>|[<span data-ttu-id="beba9-133">将域或复合域附加到参考数据</span><span class="sxs-lookup"><span data-stu-id="beba9-133">Attach a Domain or Composite Domain to Reference Data</span></span>](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)|  
|<span data-ttu-id="beba9-134">更改或增加知识库中的值</span><span class="sxs-lookup"><span data-stu-id="beba9-134">Change or augment the values in a knowledge base</span></span>|[<span data-ttu-id="beba9-135">更改域值</span><span class="sxs-lookup"><span data-stu-id="beba9-135">Change Domain Values</span></span>](../../2014/data-quality-services/change-domain-values.md)|  
|<span data-ttu-id="beba9-136">使用验证和标准化规则</span><span class="sxs-lookup"><span data-stu-id="beba9-136">Use validation and standardization rules</span></span>|[<span data-ttu-id="beba9-137">创建域规则</span><span class="sxs-lookup"><span data-stu-id="beba9-137">Create a Domain Rule</span></span>](../../2014/data-quality-services/create-a-domain-rule.md)|  
|<span data-ttu-id="beba9-138">使用关系更正作为域中值的一部分的字词</span><span class="sxs-lookup"><span data-stu-id="beba9-138">Use relations to correct a term that is part of a value in a domain</span></span>|[<span data-ttu-id="beba9-139">创建基于字词的关系</span><span class="sxs-lookup"><span data-stu-id="beba9-139">Create Term-Based Relations</span></span>](../../2014/data-quality-services/create-term-based-relations.md)|  
|<span data-ttu-id="beba9-140">完成、关闭或取消域管理活动</span><span class="sxs-lookup"><span data-stu-id="beba9-140">Complete, close, or cancel the domain management activity</span></span>|[<span data-ttu-id="beba9-141">结束域管理活动</span><span class="sxs-lookup"><span data-stu-id="beba9-141">End the Domain Management Activity</span></span>](../../2014/data-quality-services/end-the-domain-management-activity.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="beba9-142">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="beba9-142">Related Tasks</span></span>  
  
|<span data-ttu-id="beba9-143">任务说明</span><span class="sxs-lookup"><span data-stu-id="beba9-143">Task Description</span></span>|<span data-ttu-id="beba9-144">主题</span><span class="sxs-lookup"><span data-stu-id="beba9-144">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="beba9-145">通过运行知识发现并以交互方式管理知识来生成知识库</span><span class="sxs-lookup"><span data-stu-id="beba9-145">Building a knowledge base by running knowledge discovery and interactively managing knowledge</span></span>|[<span data-ttu-id="beba9-146">生成知识库</span><span class="sxs-lookup"><span data-stu-id="beba9-146">Building a Knowledge Base</span></span>](../../2014/data-quality-services/building-a-knowledge-base.md)|  
|<span data-ttu-id="beba9-147">将知识导入知识库，或从知识库中导出知识。</span><span class="sxs-lookup"><span data-stu-id="beba9-147">Importing knowledge into, or exporting it from, a knowledge base.</span></span>|[<span data-ttu-id="beba9-148">导入和导出知识</span><span class="sxs-lookup"><span data-stu-id="beba9-148">Importing and Exporting Knowledge</span></span>](../../2014/data-quality-services/importing-and-exporting-knowledge.md)|  
|<span data-ttu-id="beba9-149">创建一个复合域，并将知识添加到该域中。</span><span class="sxs-lookup"><span data-stu-id="beba9-149">Creating a composite domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="beba9-150">管理复合域</span><span class="sxs-lookup"><span data-stu-id="beba9-150">Managing a Composite Domain</span></span>](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  
