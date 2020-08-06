---
title: DQS 清除转换 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data correction
- correct data
ms.assetid: d2ec1b1a-c745-4741-b57c-6fdb524a154c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e980497905b8fa96a73516916af17f934221992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577759"
---
# <a name="dqs-cleansing-transformation"></a><span data-ttu-id="7cf58-102">DQS 清除转换</span><span class="sxs-lookup"><span data-stu-id="7cf58-102">DQS Cleansing Transformation</span></span>
  <span data-ttu-id="7cf58-103">DQS 清除转换使用 Data Quality Services (DQS)，通过应用为连接的数据源或类似数据源创建的已批准规则来更正来自连接的数据源的数据。</span><span class="sxs-lookup"><span data-stu-id="7cf58-103">The DQS Cleansing transformation uses Data Quality Services (DQS) to correct data from a connected data source, by applying approved rules that were created for the connected data source or a similar data source.</span></span> <span data-ttu-id="7cf58-104">有关数据更正规则的详细信息，请参阅 [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md)。</span><span class="sxs-lookup"><span data-stu-id="7cf58-104">For more information about data correction rules, see [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span> <span data-ttu-id="7cf58-105">有关 DQS 的详细信息，请参阅 [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="7cf58-105">For more information DQS, see [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md).</span></span>  
  
 <span data-ttu-id="7cf58-106">为了确定是否必须更正数据，DQS 清除转换在满足以下条件时处理输入列中的数据：</span><span class="sxs-lookup"><span data-stu-id="7cf58-106">To determine whether the data has to be corrected, the DQS Cleansing transformation processes data from an input column when the following conditions are true:</span></span>  
  
-   <span data-ttu-id="7cf58-107">该列已选定用于数据更正。</span><span class="sxs-lookup"><span data-stu-id="7cf58-107">The column is selected for data correction.</span></span>  
  
-   <span data-ttu-id="7cf58-108">数据更正支持该列数据类型。</span><span class="sxs-lookup"><span data-stu-id="7cf58-108">The column data type is supported for data correction.</span></span>  
  
-   <span data-ttu-id="7cf58-109">该列映射到的域具有兼容数据类型。</span><span class="sxs-lookup"><span data-stu-id="7cf58-109">The column is mapped a domain that has a compatible data type.</span></span>  
  
 <span data-ttu-id="7cf58-110">该转换还包括您配置为处理行级错误的错误输出。</span><span class="sxs-lookup"><span data-stu-id="7cf58-110">The transformation also includes an error output that you configure to handle row-level errors.</span></span> <span data-ttu-id="7cf58-111">若要配置错误输出，请使用 **“DQS 清理转换编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="7cf58-111">To configure the error output, use the **DQS Cleansing Transformation Editor**.</span></span>  
  
 <span data-ttu-id="7cf58-112">您可以在数据流中包含 [Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) 来标识可能为重复项的数据行。</span><span class="sxs-lookup"><span data-stu-id="7cf58-112">You can include the [Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) in the data flow to identify rows of data that are likely to be duplicates.</span></span>  
  
## <a name="data-quality-projects-and-values"></a><span data-ttu-id="7cf58-113">数据质量项目和值</span><span class="sxs-lookup"><span data-stu-id="7cf58-113">Data Quality Projects and Values</span></span>  
 <span data-ttu-id="7cf58-114">使用 DQS 清理转换处理数据时，会在数据质量服务器上创建一个清理项目。</span><span class="sxs-lookup"><span data-stu-id="7cf58-114">When you process data with the DQS Cleansing transformation, a cleansing project is created on the Data Quality Server.</span></span> <span data-ttu-id="7cf58-115">使用数据质量客户端管理项目。</span><span class="sxs-lookup"><span data-stu-id="7cf58-115">You use the Data Quality Client to manage the project.</span></span> <span data-ttu-id="7cf58-116">此外，您还可以使用数据质量客户端将项目值导入 DQS 知识库域。</span><span class="sxs-lookup"><span data-stu-id="7cf58-116">In addition, you can use the Data Quality Client to import the project values into a DQS knowledge base domain.</span></span> <span data-ttu-id="7cf58-117">只能将值导入配置为使用 DQS 清理转换的域（或链接域）。</span><span class="sxs-lookup"><span data-stu-id="7cf58-117">You can import the values only to a domain (or linked domain) that the DQS Cleansing transformation was configured to use.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="7cf58-118">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="7cf58-118">Related Tasks</span></span>  
  
-   [<span data-ttu-id="7cf58-119">在 Data Quality Client 中打开 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="7cf58-119">Open Integration Services Projects in Data Quality Client</span></span>](../../../data-quality-services/open-integration-services-projects-in-data-quality-client.md)  
  
-   [<span data-ttu-id="7cf58-120">将清理项目值导入域</span><span class="sxs-lookup"><span data-stu-id="7cf58-120">Import Cleansing Project Values into a Domain</span></span>](../../../data-quality-services/import-cleansing-project-values-into-a-domain.md)  
  
-   [<span data-ttu-id="7cf58-121">将数据质量规则应用于数据源</span><span class="sxs-lookup"><span data-stu-id="7cf58-121">Apply Data Quality Rules to Data Source</span></span>](apply-data-quality-rules-to-data-source.md)  
  
## <a name="related-content"></a><span data-ttu-id="7cf58-122">相关内容</span><span class="sxs-lookup"><span data-stu-id="7cf58-122">Related Content</span></span>  
  
-   [<span data-ttu-id="7cf58-123">管理数据质量项目&#41; &#40;打开、解锁、重命名和删除</span><span class="sxs-lookup"><span data-stu-id="7cf58-123">Manage &#40;Open, Unlock, Rename, and Delete&#41; a Data Quality Project</span></span>](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)  
  
-   <span data-ttu-id="7cf58-124">social.technet.microsoft.com 上的文章： [使用复合域清理复杂数据](https://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx)。</span><span class="sxs-lookup"><span data-stu-id="7cf58-124">Article, [Cleansing complex data using composite domains](https://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx), on social.technet.microsoft.com.</span></span>  
  
  
