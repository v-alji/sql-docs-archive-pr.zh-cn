---
title: 生成知识库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 51eff161-6ecd-4ee4-8187-1dd8ef4814bd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 03c9fc6c3a9168a66e8293c61db21a87fadc260f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578464"
---
# <a name="building-a-knowledge-base"></a><span data-ttu-id="544d2-102">生成知识库</span><span class="sxs-lookup"><span data-stu-id="544d2-102">Building a Knowledge Base</span></span>
  <span data-ttu-id="544d2-103">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中的知识库是有关数据的知识的存储库，通过它您可以了解自己的数据并维护其完整性。</span><span class="sxs-lookup"><span data-stu-id="544d2-103">A knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) is a repository of knowledge about your data that enables you to understand your data and maintain its integrity.</span></span> <span data-ttu-id="544d2-104">知识库由域构成，每个域都表示一个数据字段中的数据。</span><span class="sxs-lookup"><span data-stu-id="544d2-104">A knowledge base consists of domains, each of which represents the data in a data field.</span></span> <span data-ttu-id="544d2-105">DQS 使用知识库来对数据库执行数据清理和消除重复。</span><span class="sxs-lookup"><span data-stu-id="544d2-105">The knowledge base is used by DQS to perform data cleansing and deduplication on a database.</span></span> <span data-ttu-id="544d2-106">若要为数据清理对知识库进行准备，您可以对数据示例运行计算机辅助分析，并且以交互方式管理域中的值。</span><span class="sxs-lookup"><span data-stu-id="544d2-106">To prepare the knowledge base for data cleansing, you can run a computer-assisted analysis of a data sample, and interactively manage values in the domains.</span></span> <span data-ttu-id="544d2-107">通过 DQS，您可以导入知识、创建规则和关系、直接更改数据值以及利用默认数据库。</span><span class="sxs-lookup"><span data-stu-id="544d2-107">DQS enables you to import knowledge, create rules and relationships, change data values directly, and leverage a default database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="544d2-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="544d2-108">In This Section</span></span>  
 <span data-ttu-id="544d2-109">您可以对知识库执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="544d2-109">You can perform the following operations on a knowledge base:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="544d2-110">从头开始、从现有知识库或从一个 .dqs 数据文件创建新的知识库。</span><span class="sxs-lookup"><span data-stu-id="544d2-110">Create a new knowledge base from scratch, from an existing knowledge base, or from a .dqs data file.</span></span>|[<span data-ttu-id="544d2-111">创建知识库</span><span class="sxs-lookup"><span data-stu-id="544d2-111">Create a Knowledge Base</span></span>](../../2014/data-quality-services/create-a-knowledge-base.md)|  
|<span data-ttu-id="544d2-112">打开一个现有知识库以便执行知识发现、域管理或者添加匹配策略。</span><span class="sxs-lookup"><span data-stu-id="544d2-112">Open an existing knowledge base to perform knowledge discovery, domain management, or add a matching policy.</span></span>|[<span data-ttu-id="544d2-113">打开知识库</span><span class="sxs-lookup"><span data-stu-id="544d2-113">Open a Knowledge Base</span></span>](../../2014/data-quality-services/open-a-knowledge-base.md)|  
|<span data-ttu-id="544d2-114">对知识库执行管理操作，包括打开知识库、取消锁定知识库、放弃您对知识库所做的工作、重命名知识库、删除知识库或查看知识库的属性。</span><span class="sxs-lookup"><span data-stu-id="544d2-114">Perform management actions on a knowledge base, including opening it, unlocking it, discarding your work on it, renaming it, deleting it, or viewing its properties.</span></span>|[<span data-ttu-id="544d2-115">管理知识库</span><span class="sxs-lookup"><span data-stu-id="544d2-115">Manage a Knowledge Base</span></span>](../../2014/data-quality-services/manage-a-knowledge-base.md)|  
|<span data-ttu-id="544d2-116">通过知识发现向知识库添加知识；域值管理；添加匹配策略；导入知识、域或值；或者使用默认知识库（即 DQS 数据）。</span><span class="sxs-lookup"><span data-stu-id="544d2-116">Add knowledge to a knowledge base through knowledge discovery; domain value management; adding a matching policy; importing a knowledge, domain, or values; or using the default knowledge base, DQS Data.</span></span>|[<span data-ttu-id="544d2-117">将知识添加到知识库</span><span class="sxs-lookup"><span data-stu-id="544d2-117">Adding Knowledge to a Knowledge Base</span></span>](../../2014/data-quality-services/adding-knowledge-to-a-knowledge-base.md)|  
|<span data-ttu-id="544d2-118">根据数据质量条件分析数据样本。</span><span class="sxs-lookup"><span data-stu-id="544d2-118">Analyze a data sample for data quality criteria.</span></span>|[<span data-ttu-id="544d2-119">执行知识发现</span><span class="sxs-lookup"><span data-stu-id="544d2-119">Perform Knowledge Discovery</span></span>](../../2014/data-quality-services/perform-knowledge-discovery.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="544d2-120">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="544d2-120">Related Tasks</span></span>  
  
|<span data-ttu-id="544d2-121">任务说明</span><span class="sxs-lookup"><span data-stu-id="544d2-121">Task Description</span></span>|<span data-ttu-id="544d2-122">主题</span><span class="sxs-lookup"><span data-stu-id="544d2-122">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="544d2-123">将知识导入知识库，或从知识库中导出知识。</span><span class="sxs-lookup"><span data-stu-id="544d2-123">Importing knowledge into, or exporting it from, a knowledge base.</span></span>|[<span data-ttu-id="544d2-124">导入和导出知识</span><span class="sxs-lookup"><span data-stu-id="544d2-124">Importing and Exporting Knowledge</span></span>](../../2014/data-quality-services/importing-and-exporting-knowledge.md)|  
|<span data-ttu-id="544d2-125">创建单一域，并将知识添加到该域中。</span><span class="sxs-lookup"><span data-stu-id="544d2-125">Creating a single domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="544d2-126">管理域</span><span class="sxs-lookup"><span data-stu-id="544d2-126">Managing a Domain</span></span>](../../2014/data-quality-services/managing-a-domain.md)|  
|<span data-ttu-id="544d2-127">创建一个复合域，并将知识添加到该域中。</span><span class="sxs-lookup"><span data-stu-id="544d2-127">Creating a composite domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="544d2-128">管理复合域</span><span class="sxs-lookup"><span data-stu-id="544d2-128">Managing a Composite Domain</span></span>](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  
