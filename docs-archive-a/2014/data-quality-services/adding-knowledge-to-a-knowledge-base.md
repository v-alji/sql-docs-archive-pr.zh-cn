---
title: 将知识添加到知识库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: da148a7f-55bc-4990-a157-e61968b831d7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d3450f220b7d879e76c112232081dfec22665dae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578470"
---
# <a name="adding-knowledge-to-a-knowledge-base"></a><span data-ttu-id="f29d0-102">将知识添加到知识库</span><span class="sxs-lookup"><span data-stu-id="f29d0-102">Adding Knowledge to a Knowledge Base</span></span>
  <span data-ttu-id="f29d0-103">本主题介绍可在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中将知识添加到知识库的方法。</span><span class="sxs-lookup"><span data-stu-id="f29d0-103">This topic describes the ways in which you can add knowledge to a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="f29d0-104">您必须具备有关数据的知识才可以执行数据质量操作。</span><span class="sxs-lookup"><span data-stu-id="f29d0-104">Before you can perform data quality operations, you have to have knowledge about the data.</span></span> <span data-ttu-id="f29d0-105">您可以通过生成和维护数据质量知识库，并向知识库添加与特定类型的数据源相关的知识，以获得知识。</span><span class="sxs-lookup"><span data-stu-id="f29d0-105">You acquire that knowledge by building and maintaining a data quality knowledge base, and adding to it knowledge related to a specific type of data source.</span></span> <span data-ttu-id="f29d0-106">知识库是有关数据的知识的存储库，通过它您可以了解自己的数据并维护其完整性。</span><span class="sxs-lookup"><span data-stu-id="f29d0-106">The knowledge base is a repository of knowledge about your data that enables you to understand your data and maintain its integrity.</span></span>  
  
 <span data-ttu-id="f29d0-107">知识库包含与数据源相关的数据域。</span><span class="sxs-lookup"><span data-stu-id="f29d0-107">The knowledge base contains data domains that relate to the data source.</span></span> <span data-ttu-id="f29d0-108">对于每个数据域，DQKB 存储所有标识的字词、拼写错误、验证和业务规则，以及可用于对数据源执行数据质量操作的引用数据。</span><span class="sxs-lookup"><span data-stu-id="f29d0-108">For each data domain, the DQKB stores all identified terms, spelling errors, validation and business rules, and reference data that can be used to perform data quality actions on the data source.</span></span> <span data-ttu-id="f29d0-109">DQS 使用该知识来标识不正确或无效的数据，或执行匹配。</span><span class="sxs-lookup"><span data-stu-id="f29d0-109">DQS uses this knowledge to identify incorrect or invalid data, or perform matching.</span></span>  
  
 <span data-ttu-id="f29d0-110">您可以采用以下计算机辅助方法或交互式方法将知识添加到知识库。</span><span class="sxs-lookup"><span data-stu-id="f29d0-110">You can add knowledge to a knowledge base in the following computer-assisted or interactive ways.</span></span>  
  
-   [<span data-ttu-id="f29d0-111">执行知识发现</span><span class="sxs-lookup"><span data-stu-id="f29d0-111">Perform Knowledge Discovery</span></span>](#Discovery)  
  
-   [<span data-ttu-id="f29d0-112">管理域中的数据值</span><span class="sxs-lookup"><span data-stu-id="f29d0-112">Manage Data Values in a Domain</span></span>](#ManageDomain)  
  
-   [<span data-ttu-id="f29d0-113">从 .dqs 文件导入知识</span><span class="sxs-lookup"><span data-stu-id="f29d0-113">Import Knowledge from a .dqs File</span></span>](#DQSFile)  
  
-   [<span data-ttu-id="f29d0-114">从 Excel 文件导入知识</span><span class="sxs-lookup"><span data-stu-id="f29d0-114">Import Knowledge from an Excel File</span></span>](#Excel)  
  
-   [<span data-ttu-id="f29d0-115">将知识从项目导入回知识库</span><span class="sxs-lookup"><span data-stu-id="f29d0-115">Import Knowledge from a Project Back into the Knowledge Base</span></span>](#Project)  
  
-   [<span data-ttu-id="f29d0-116">使用默认 DQS 知识库</span><span class="sxs-lookup"><span data-stu-id="f29d0-116">Use the Default DQS Knowledge Base</span></span>](#Default)  
  
##  <a name="perform-knowledge-discovery"></a><a name="Discovery"></a><span data-ttu-id="f29d0-117">执行知识发现</span><span class="sxs-lookup"><span data-stu-id="f29d0-117">Perform Knowledge Discovery</span></span>  
 <span data-ttu-id="f29d0-118">知识发现将分析数据样本以确定是否满足数据质量标准，然后将获得的知识添加到知识库中。</span><span class="sxs-lookup"><span data-stu-id="f29d0-118">Knowledge discovery analyzes a sample of data for data quality criteria, and then adds the knowledge it has gained to the knowledge base.</span></span> <span data-ttu-id="f29d0-119">这是一个计算机辅助过程，用于标识数据不一致和语法错误，随后提出数据更改建议。</span><span class="sxs-lookup"><span data-stu-id="f29d0-119">This is a computer-assisted process that identifies data inconsistencies and syntax errors, and proposes changes to the data.</span></span> <span data-ttu-id="f29d0-120">知识发现活动是一个向导，其中包括可以按交互方式管理域值的页面。</span><span class="sxs-lookup"><span data-stu-id="f29d0-120">The knowledge discovery activity is a wizard that includes a page that you can interactively manage domain values on.</span></span>  
  
-   <span data-ttu-id="f29d0-121">有关文档的详细信息，请参阅 [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="f29d0-121">For more information in documentation, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md).</span></span>  
  
-   <span data-ttu-id="f29d0-122">有关演示如何执行知识发现的视频，请单击 [此处](https://msdn.microsoft.com/sqlserver/hh323825.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f29d0-122">For a video demonstrating how to perform knowledge discovery, click [here](https://msdn.microsoft.com/sqlserver/hh323825.aspx).</span></span>  
  
##  <a name="manage-data-values-in-a-domain"></a><a name="ManageDomain"></a><span data-ttu-id="f29d0-123">管理域中的数据值</span><span class="sxs-lookup"><span data-stu-id="f29d0-123">Manage Data Values in a Domain</span></span>  
 <span data-ttu-id="f29d0-124">通过 DQS 可以按交互方式更改和增加由计算机辅助知识发现活动生成的元数据。</span><span class="sxs-lookup"><span data-stu-id="f29d0-124">DQS enables you to interactively change and augment the metadata that is generated by the computer-assisted knowledge discovery activity.</span></span> <span data-ttu-id="f29d0-125">在域管理活动中执行此操作，从中您可以向特定数据值应用更改。</span><span class="sxs-lookup"><span data-stu-id="f29d0-125">You do so in the Domain Management activity, where you can apply a change to a specific data value.</span></span>  
  
-   <span data-ttu-id="f29d0-126">有关文档的详细信息，请参阅 [Change Domain Values](../../2014/data-quality-services/change-domain-values.md)。</span><span class="sxs-lookup"><span data-stu-id="f29d0-126">For more information in documentation, see [Change Domain Values](../../2014/data-quality-services/change-domain-values.md).</span></span>  
  
-   <span data-ttu-id="f29d0-127">有关演示如何执行域管理的视频，请单击 [此处](https://msdn.microsoft.com/sqlserver/hh323825.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f29d0-127">For a video demonstrating how to perform domain management, click [here](https://msdn.microsoft.com/sqlserver/hh323825.aspx).</span></span> <span data-ttu-id="f29d0-128">请注意，在此视频中，您将在知识发现向导的“管理域值”页中更改域值。</span><span class="sxs-lookup"><span data-stu-id="f29d0-128">Note that in this video, you change domain values in the Managing Domain Values page of the Knowledge Discovery wizard.</span></span> <span data-ttu-id="f29d0-129">还可以在域管理活动的“域值”页中执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="f29d0-129">You can also perform these steps in the Domain Values Page of the Domain Management activity.</span></span>  
  
##  <a name="import-knowledge-from-a-dqs-file"></a><a name="DQSFile"></a><span data-ttu-id="f29d0-130">从 dqs 文件导入知识</span><span class="sxs-lookup"><span data-stu-id="f29d0-130">Import Knowledge from a .dqs File</span></span>  
 <span data-ttu-id="f29d0-131">可以将域从 .dqs 数据文件导入到现有知识库，也可以将整个知识库从 .dqs 导入到新的知识库。</span><span class="sxs-lookup"><span data-stu-id="f29d0-131">You can import a domain from a .dqs data file into an existing knowledge base, or you can import an entire knowledge base from a .dqs into a new knowledge base.</span></span> <span data-ttu-id="f29d0-132">为此，您首先需要将现有域或知识库导出到 .dqs 文件。</span><span class="sxs-lookup"><span data-stu-id="f29d0-132">To do so, you first need to export an existing domain or knowledge base to a .dqs file.</span></span> <span data-ttu-id="f29d0-133">包含域的 dqs 文件包含所有域数据；包含知识库的 .dqs 文件将包含所有知识库信息，其中包括域和匹配策略。</span><span class="sxs-lookup"><span data-stu-id="f29d0-133">A .dqs file containing a domain includes all domain data; a .dqs file containing a knowledge base will contain all knowledge base information, including domains and the matching policy.</span></span>  
  
-   <span data-ttu-id="f29d0-134">有关文档的详细信息，请参阅[从 .dqs 文件导入域](../../2014/data-quality-services/import-a-domain-from-a-dqs-file.md)或[从 .dqs 文件导入知识库](../../2014/data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)。</span><span class="sxs-lookup"><span data-stu-id="f29d0-134">For more information in documentation, see [Import a Domain from a .dqs File](../../2014/data-quality-services/import-a-domain-from-a-dqs-file.md) or [Import a Knowledge Base from a .dqs File](../../2014/data-quality-services/import-a-knowledge-base-from-a-dqs-file.md).</span></span>  
  
##  <a name="import-knowledge-from-an-excel-file"></a><a name="Excel"></a><span data-ttu-id="f29d0-135">从 Excel 文件导入知识</span><span class="sxs-lookup"><span data-stu-id="f29d0-135">Import Knowledge from an Excel File</span></span>  
 <span data-ttu-id="f29d0-136">您可以将域值从 Excel 电子表格文件导入到现有域或知识库。</span><span class="sxs-lookup"><span data-stu-id="f29d0-136">You can import domain values from an Excel spreadsheet file into an existing domain or knowledge base.</span></span> <span data-ttu-id="f29d0-137">为此，您必须首先创建一个容纳要导入的域值的 Excel 电子表格，并确保 Excel 安装在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 计算机上，以便您能够使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]导入值。</span><span class="sxs-lookup"><span data-stu-id="f29d0-137">To do so, you must first create an Excel spreadsheet with the domain values that you want to import, and ensure that Excel is installed on the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] computer for you to be able to import values using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="f29d0-138">您不能将域值从域或知识库中导出到 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="f29d0-138">You cannot export domain values from a domain or knowledge base to an Excel file.</span></span>  
  
-   <span data-ttu-id="f29d0-139">有关文档的详细信息，请参阅[将值从 Excel 文件导入到域](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md)或[在知识发现中从 Excel 文件中导入域](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="f29d0-139">For more information in documentation, see [Import Values from an Excel File into a Domain](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md) or [Import Domains from an Excel File in Knowledge Discovery](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md).</span></span>  
  
##  <a name="import-knowledge-from-a-project-back-into-the-knowledge-base"></a><a name="Project"></a><span data-ttu-id="f29d0-140">将知识从项目导入回知识库</span><span class="sxs-lookup"><span data-stu-id="f29d0-140">Import Knowledge from a Project Back into the Knowledge Base</span></span>  
 <span data-ttu-id="f29d0-141">在使用知识库运行清理或匹配数据质量项目之后，可以将在清理或匹配过程中创建的知识导入回该知识库。</span><span class="sxs-lookup"><span data-stu-id="f29d0-141">After you have run a cleansing or matching data quality project using a knowledge base, you can import knowledge created during cleansing or matching back into that knowledge base.</span></span> <span data-ttu-id="f29d0-142">这样，您就可以保留在项目过程中生成的知识，并在知识库中不断地生成知识。</span><span class="sxs-lookup"><span data-stu-id="f29d0-142">This enables you to keep knowledge generated during the project, and to continuously build the knowledge in the knowledge base.</span></span>  
  
-   <span data-ttu-id="f29d0-143">有关文档的详细信息，请参阅[将清理项目值导入到域中](../../2014/data-quality-services/import-cleansing-project-values-into-a-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="f29d0-143">For more information in documentation, see [Import Cleansing Project Values into a Domain](../../2014/data-quality-services/import-cleansing-project-values-into-a-domain.md).</span></span>  
  
##  <a name="use-the-default-dqs-knowledge-base"></a><a name="Default"></a><span data-ttu-id="f29d0-144">使用默认 DQS 知识库</span><span class="sxs-lookup"><span data-stu-id="f29d0-144">Use the Default DQS Knowledge Base</span></span>  
 <span data-ttu-id="f29d0-145">DQS 附带一个预生成的知识库（称为 DQS 数据），其中包含针对美国公司和地址数据的域。</span><span class="sxs-lookup"><span data-stu-id="f29d0-145">DQS ships with a pre-built knowledge base called DQS Data that contains domains for United States company and address data.</span></span> <span data-ttu-id="f29d0-146">可以使用此知识库快速启动项目，而无需创建新的知识库。</span><span class="sxs-lookup"><span data-stu-id="f29d0-146">This knowledge base can be used to quickly start a project without creating a new knowledge base.</span></span> <span data-ttu-id="f29d0-147">DQS 数据知识库是只读的，但数据专员可以基于该知识库创建新的知识库。</span><span class="sxs-lookup"><span data-stu-id="f29d0-147">The DQS Data knowledge base is read-only, but the data steward can create a new knowledge base based on it.</span></span>  
  
-   <span data-ttu-id="f29d0-148">有关文档的详细信息，请参阅 [Using the DQS Default Knowledge Base](../../2014/data-quality-services/using-the-dqs-default-knowledge-base.md)。</span><span class="sxs-lookup"><span data-stu-id="f29d0-148">For more information in documentation, see [Using the DQS Default Knowledge Base](../../2014/data-quality-services/using-the-dqs-default-knowledge-base.md).</span></span>  
  
  
