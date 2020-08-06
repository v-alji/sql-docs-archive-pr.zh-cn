---
title: 第2课：使用供应商知识库清理供应商数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 215c14de-fc3f-46de-a022-bf69b9ea2a96
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ebc0231cd0f28fcad23656cf22abd8d68eca7dc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577156"
---
# <a name="lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base"></a><span data-ttu-id="49e28-102">第 2 课：使用 Suppliers 知识库清理供应商数据</span><span class="sxs-lookup"><span data-stu-id="49e28-102">Lesson 2: Cleansing Supplier Data using the Suppliers Knowledge Base</span></span>
  <span data-ttu-id="49e28-103">在本课中，您将使用在第一课中创建的**供应商**知识库来清理 Excel 文件中的供应商数据。</span><span class="sxs-lookup"><span data-stu-id="49e28-103">In this lesson, you cleanse the supplier data in an Excel file by using the **Suppliers** knowledge base you have created in the first lesson.</span></span> <span data-ttu-id="49e28-104">DQS 中的数据清理包括一个**计算机辅助过程**，该过程分析数据与知识库中知识的符合程度，并提供一个**交互式过程**，使您可以查看和修改计算机辅助过程的结果。</span><span class="sxs-lookup"><span data-stu-id="49e28-104">Data cleansing in DQS includes a **computer-assisted process** that analyzes how data conforms to the knowledge in a knowledge base, and an **interactive process** that enables you to review and modify results from the computer-assisted process.</span></span> <span data-ttu-id="49e28-105">数据清理功能可以识别数据源中不正确的数据，然后对这些数据进行更正或提出更正建议。</span><span class="sxs-lookup"><span data-stu-id="49e28-105">The data cleansing feature identifies incorrect data in your data source and then corrects or suggests corrections for the incorrect data.</span></span> <span data-ttu-id="49e28-106">它还通过使用域值、同义词的前导值、域规则、基于字词的关系和参考数据来使客户数据标准化和更加丰富。</span><span class="sxs-lookup"><span data-stu-id="49e28-106">It also standardizes and enriches customer data by using domain values, leading values for synonyms, domain rules, term-based relations, and reference data.</span></span> <span data-ttu-id="49e28-107">您可以通过交互方式批准或拒绝计算机辅助过程建议的更改。</span><span class="sxs-lookup"><span data-stu-id="49e28-107">You can interactively approve or reject changes proposed by the computer-assisted process.</span></span> <span data-ttu-id="49e28-108">有关更多详细信息，请参阅[数据清理](https://msdn.microsoft.com/library/gg524800.aspx)。</span><span class="sxs-lookup"><span data-stu-id="49e28-108">See [Data Cleansing](https://msdn.microsoft.com/library/gg524800.aspx) for more details.</span></span>  
  
 <span data-ttu-id="49e28-109">计算机辅助过程使用以下阈值，您可以使用 DQS 客户端主页上的“配置”选项来配置这些阈值。</span><span class="sxs-lookup"><span data-stu-id="49e28-109">The computer-assisted process uses the following threshold values that you can configure using the Configuration option on the DQS Client main page.</span></span>  
  
-   <span data-ttu-id="49e28-110">**建议的最低分数：** DQS 用于建议替换值的最低分数或置信度。</span><span class="sxs-lookup"><span data-stu-id="49e28-110">**Min score for suggestions:** The minimum score or confidence level that is used by DQS for suggesting replacement for a value.</span></span>  
  
-   <span data-ttu-id="49e28-111">**自动更正的最低分数：** DQS 用于自动更正值的最低分数或置信度级别。</span><span class="sxs-lookup"><span data-stu-id="49e28-111">**Min score for auto corrections:** The minimum score or confidence level that is used by DQS for automatically correcting a value.</span></span>  
  
 <span data-ttu-id="49e28-112">有关如何配置这些设置的详细信息，请参阅[配置清理和匹配的阈值](https://msdn.microsoft.com/library/hh510415.aspx)。</span><span class="sxs-lookup"><span data-stu-id="49e28-112">See [Configure Threshold Values for Cleansing and Matching](https://msdn.microsoft.com/library/hh510415.aspx) for details on how to configure these settings.</span></span>  
  
 <span data-ttu-id="49e28-113">在本课中，您将执行以下任务来使用 Suppliers 知识库清理输入数据。</span><span class="sxs-lookup"><span data-stu-id="49e28-113">In this lesson, you perform the following tasks to cleanse the input data by using the Suppliers knowledge base.</span></span>  
  
1.  <span data-ttu-id="49e28-114">创建用于清理的数据质量项目，选择 Suppliers 知识库作为要用于分析和清理 Excel 文件中源数据的知识库，然后选择“清理”活动。</span><span class="sxs-lookup"><span data-stu-id="49e28-114">Create a Data Quality Project for Cleansing, select the Suppliers knowledge base as the knowledge base to use to analyze and cleanse the source data in an Excel file, and select the Cleansing activity.</span></span>  
  
2.  <span data-ttu-id="49e28-115">将要清理的 Excel 列映射为知识库中适当的 DQS 域/复合域。</span><span class="sxs-lookup"><span data-stu-id="49e28-115">Map the Excel columns that you want to cleanse to appropriate DQS domains/composite domains in the knowledge base.</span></span>  
  
3.  <span data-ttu-id="49e28-116">运行计算机辅助的清理活动。</span><span class="sxs-lookup"><span data-stu-id="49e28-116">Run the computer-assisted cleansing activity.</span></span> <span data-ttu-id="49e28-117">计算机辅助过程会在数据质量客户端中显示数据质量信息，您可以使用该客户端以交互方式清理数据。</span><span class="sxs-lookup"><span data-stu-id="49e28-117">The computer-assisted process displays data quality information in the Data Quality Client that you can use to cleanse the data interactively.</span></span>  
  
4.  <span data-ttu-id="49e28-118">查看和管理清理活动的结果。</span><span class="sxs-lookup"><span data-stu-id="49e28-118">View and manage the results of the cleansing activity.</span></span> <span data-ttu-id="49e28-119">您可以查看计算机辅助过程找到的正确值、不正确但是已更正的值、不正确并提供更改建议的值或无效值。</span><span class="sxs-lookup"><span data-stu-id="49e28-119">You can review the values that the computer-assisted process finds to be correct, incorrect but corrected, incorrect with a suggested change, or invalid.</span></span> <span data-ttu-id="49e28-120">您可以交互方式批准或拒绝更改，通过使用“更正为”字段更正或覆盖计算机辅助过程给出的建议值。</span><span class="sxs-lookup"><span data-stu-id="49e28-120">You can interactively approve or reject changes, correcting or overriding the suggestion from the computer-assisted process by using the Correct To field.</span></span>  
  
5.  <span data-ttu-id="49e28-121">将清理过程的结果导出到 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="49e28-121">Export the results from the cleansing process to an Excel file.</span></span>  
  
6.  <span data-ttu-id="49e28-122">将清理项目中的值导入到域中，以通过新的规则、值、更正等来增强知识库中的知识。</span><span class="sxs-lookup"><span data-stu-id="49e28-122">Import the values from the cleansing project into domains to augment the knowledge in the knowledge base with new rules, values, corrections etc...</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="49e28-123">下一步</span><span class="sxs-lookup"><span data-stu-id="49e28-123">Next Step</span></span>  
 [<span data-ttu-id="49e28-124">任务 1：创建数据质量项目</span><span class="sxs-lookup"><span data-stu-id="49e28-124">Task 1: Creating a Data Quality Project</span></span>](../../2014/tutorials/task-1-creating-a-data-quality-project.md)  
  
  
