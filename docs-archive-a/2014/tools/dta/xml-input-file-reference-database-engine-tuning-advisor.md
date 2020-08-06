---
title: XML 输入文件参考（数据库引擎优化顾问）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3bbd38299e4921db33cbaf318883c2f0a9041d92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693586"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a><span data-ttu-id="495d5-102">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="495d5-102">XML Input File Reference (Database Engine Tuning Advisor)</span></span>
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="495d5-103">优化顾问可以使用 XML 输入文件来优化数据库。</span><span class="sxs-lookup"><span data-stu-id="495d5-103">Tuning Advisor can use an XML input file to tune a database.</span></span> <span data-ttu-id="495d5-104">此 XML 文件指定要用于优化会话的数据库、表、工作负荷文件或表以及优化选项。</span><span class="sxs-lookup"><span data-stu-id="495d5-104">This XML file designates which databases, tables, workload files or tables, and tuning options to use for the tuning session.</span></span> <span data-ttu-id="495d5-105">您还可以使用此文件指定一个用户指定的配置来执行“假设”分析。</span><span class="sxs-lookup"><span data-stu-id="495d5-105">You can also use this file to specify a user-specified configuration to perform "what-if" analysis.</span></span>  
  
 <span data-ttu-id="495d5-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问 XML 输入文件包含 XML 元素（每个元素包含文本或其他用于指定优化会话设置的元素）的层次结构。</span><span class="sxs-lookup"><span data-stu-id="495d5-106">A [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML input file contains a hierarchy of XML elements, each containing text or other elements that specify the tuning session settings.</span></span> <span data-ttu-id="495d5-107">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问 XML 输入文件必须符合格式正确的 XML 的标准，因此所有的元素名称都区分大小写。</span><span class="sxs-lookup"><span data-stu-id="495d5-107">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML input file must conform to the standards for well-formed XML, so all element names are case sensitive.</span></span> <span data-ttu-id="495d5-108">使用 Pascal case 来指定元素，即第一个字符大写，随后的所有串连单词的第一个字母都大写。</span><span class="sxs-lookup"><span data-stu-id="495d5-108">Elements are specified using Pascal case, which means that the first character is uppercase and the first letter of any subsequent concatenated word is uppercase.</span></span>  
  
 <span data-ttu-id="495d5-109">所有元素值都必须符合 XML 命名约定。</span><span class="sxs-lookup"><span data-stu-id="495d5-109">All element values must conform to XML naming conventions.</span></span> <span data-ttu-id="495d5-110">有关这些约定的详细信息，请参阅 MSDN Library 中的 [XML Textual Content](https://go.microsoft.com/fwlink/?LinkId=7614) 。</span><span class="sxs-lookup"><span data-stu-id="495d5-110">For more information about these conventions, see [XML Textual Content](https://go.microsoft.com/fwlink/?LinkId=7614) in the MSDN Library.</span></span>  
  
 <span data-ttu-id="495d5-111">请注意，此参考并非综合性参考。</span><span class="sxs-lookup"><span data-stu-id="495d5-111">Note that this reference is not comprehensive.</span></span> <span data-ttu-id="495d5-112">有关可用于定义 XML 输入的所有元素的信息，请参考 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问 XML 架构 (DTASchema.xsd)。</span><span class="sxs-lookup"><span data-stu-id="495d5-112">For information about all the elements you can use to define XML input, refer to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema, DTASchema.xsd.</span></span>  
  
## <a name="xml-declaration"></a><span data-ttu-id="495d5-113">XML 声明</span><span class="sxs-lookup"><span data-stu-id="495d5-113">XML Declaration</span></span>  
  
-   [<span data-ttu-id="495d5-114">XML 数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="495d5-114">XML Data &#40;SQL Server&#41;</span></span>](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a><span data-ttu-id="495d5-115">DTAXML 根元素</span><span class="sxs-lookup"><span data-stu-id="495d5-115">DTAXML Root Element</span></span>  
  
-   [<span data-ttu-id="495d5-116">DTAXML 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-116">DTAXML Element &#40;DTA&#41;</span></span>](dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a><span data-ttu-id="495d5-117">DTAInput 元素</span><span class="sxs-lookup"><span data-stu-id="495d5-117">DTAInput Elements</span></span>  
  
-   [<span data-ttu-id="495d5-118">DTAInput 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-118">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)  
  
-   [<span data-ttu-id="495d5-119">服务器元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-119">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)  
  
-   [<span data-ttu-id="495d5-120">工作负荷元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-120">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)  
  
-   [<span data-ttu-id="495d5-121">TuningOptions 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-121">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)  
  
-   [<span data-ttu-id="495d5-122">配置元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-122">Configuration Element &#40;DTA&#41;</span></span>](configuration-element-dta.md)  
  
## <a name="server-elements"></a><span data-ttu-id="495d5-123">服务器元素</span><span class="sxs-lookup"><span data-stu-id="495d5-123">Server Elements</span></span>  
  
-   [<span data-ttu-id="495d5-124">服务器的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-124">Name Element for Server &#40;DTA&#41;</span></span>](name-element-for-server-dta.md)  
  
-   [<span data-ttu-id="495d5-125">服务器的数据库元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-125">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a><span data-ttu-id="495d5-126">工作负荷元素</span><span class="sxs-lookup"><span data-stu-id="495d5-126">Workload Elements</span></span>  
  
-   [<span data-ttu-id="495d5-127">文件元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-127">File Element &#40;DTA&#41;</span></span>](file-element-dta.md)  
  
-   [<span data-ttu-id="495d5-128">工作负荷的数据库元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-128">Database Element for Workload &#40;DTA&#41;</span></span>](database-element-for-workload-dta.md)  
  
-   [<span data-ttu-id="495d5-129">EventString 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-129">EventString Element &#40;DTA&#41;</span></span>](eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a><span data-ttu-id="495d5-130">优化选项元素</span><span class="sxs-lookup"><span data-stu-id="495d5-130">Tuning Options Elements</span></span>  
  
-   [<span data-ttu-id="495d5-131">TuningTimeInMin 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-131">TuningTimeInMin Element &#40;DTA&#41;</span></span>](tuningtimeinmin-element-dta.md)  
  
-   [<span data-ttu-id="495d5-132">StorageBoundInMB 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-132">StorageBoundInMB Element &#40;DTA&#41;</span></span>](storageboundinmb-element-dta.md)  
  
-   [<span data-ttu-id="495d5-133">TestServer 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-133">TestServer Element &#40;DTA&#41;</span></span>](testserver-element-dta.md)  
  
-   [<span data-ttu-id="495d5-134">FeatureSet 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-134">FeatureSet Element &#40;DTA&#41;</span></span>](featureset-element-dta.md)  
  
-   [<span data-ttu-id="495d5-135">分区元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-135">Partitioning Element &#40;DTA&#41;</span></span>](partitioning-element-dta.md)  
  
-   [<span data-ttu-id="495d5-136">DropOnlyMode 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-136">DropOnlyMode Element &#40;DTA&#41;</span></span>](droponlymode-element-dta.md)  
  
-   [<span data-ttu-id="495d5-137">KeepExisting 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-137">KeepExisting Element &#40;DTA&#41;</span></span>](keepexisting-element-dta.md)  
  
-   [<span data-ttu-id="495d5-138">OnlineIndexOperation 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-138">OnlineIndexOperation Element &#40;DTA&#41;</span></span>](onlineindexoperation-element-dta.md)  
  
-   [<span data-ttu-id="495d5-139">DatabaseToConnect 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-139">DatabaseToConnect Element &#40;DTA&#41;</span></span>](databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a><span data-ttu-id="495d5-140">配置元素</span><span class="sxs-lookup"><span data-stu-id="495d5-140">Configuration Elements</span></span>  
  
-   [<span data-ttu-id="495d5-141">用于配置的服务器元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-141">Server Element for Configuration &#40;DTA&#41;</span></span>](server-element-for-configuration-dta.md)  
  
-   [<span data-ttu-id="495d5-142">配置的数据库元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-142">Database Element for Configuration &#40;DTA&#41;</span></span>](database-element-for-configuration-dta.md)  
  
-   [<span data-ttu-id="495d5-143">建议元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-143">Recommendation Element &#40;DTA&#41;</span></span>](recommendation-element-dta.md)  
  
-   [<span data-ttu-id="495d5-144">创建元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-144">Create Element &#40;DTA&#41;</span></span>](create-element-dta.md)  
  
-   [<span data-ttu-id="495d5-145">索引元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-145">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)  
  
-   [<span data-ttu-id="495d5-146">索引的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-146">Name Element for Index &#40;DTA&#41;</span></span>](name-element-for-index-dta.md)  
  
-   [<span data-ttu-id="495d5-147">索引的列元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-147">Column Element for Index &#40;DTA&#41;</span></span>](column-element-for-index-dta.md)  
  
-   [<span data-ttu-id="495d5-148">列的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-148">Name Element for Column &#40;DTA&#41;</span></span>](name-element-for-column-dta.md)  
  
-   [<span data-ttu-id="495d5-149">索引的文件组元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-149">Filegroup Element for Index &#40;DTA&#41;</span></span>](filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a><span data-ttu-id="495d5-150">数据库元素</span><span class="sxs-lookup"><span data-stu-id="495d5-150">Database Elements</span></span>  
  
-   [<span data-ttu-id="495d5-151">数据库的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-151">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)  
  
-   [<span data-ttu-id="495d5-152">数据库的架构元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-152">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)  
  
-   [<span data-ttu-id="495d5-153">架构的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-153">Name Element for Schema &#40;DTA&#41;</span></span>](name-element-for-schema-dta.md)  
  
-   [<span data-ttu-id="495d5-154">架构的表元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-154">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)  
  
-   [<span data-ttu-id="495d5-155">表的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="495d5-155">Name Element for Table &#40;DTA&#41;</span></span>](name-element-for-table-dta.md)  
  
## <a name="see-also"></a><span data-ttu-id="495d5-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="495d5-156">See Also</span></span>  
 [<span data-ttu-id="495d5-157">Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="495d5-157">Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
