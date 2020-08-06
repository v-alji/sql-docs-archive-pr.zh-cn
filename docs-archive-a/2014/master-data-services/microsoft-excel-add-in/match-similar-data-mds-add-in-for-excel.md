---
title: 匹配相似数据 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6fd6fc1-3569-42a5-b6cb-87a921c88f3b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 70dea36de557c6fda909d06ee19ff8fa2ed6908d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689471"
---
# <a name="match-similar-data-mds-add-in-for-excel"></a><span data-ttu-id="fe46c-102">匹配相似数据（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="fe46c-102">Match Similar Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="fe46c-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，使用 Data Quality Services (DQS) 功能查找数据中的相似性。</span><span class="sxs-lookup"><span data-stu-id="fe46c-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use Data Quality Services (DQS) functionality to find similarities in your data.</span></span>  
  
 <span data-ttu-id="fe46c-104">若要执行此过程，您可以：</span><span class="sxs-lookup"><span data-stu-id="fe46c-104">To perform this procedure, you can:</span></span>  
  
-   <span data-ttu-id="fe46c-105">使用默认的 Data Quality Services 知识库，或</span><span class="sxs-lookup"><span data-stu-id="fe46c-105">Use the default Data Quality Services knowledge base, or</span></span>  
  
-   <span data-ttu-id="fe46c-106">创建您自己的自定义 DQS 知识库和匹配策略。</span><span class="sxs-lookup"><span data-stu-id="fe46c-106">Create your own custom DQS knowledge base and matching policy.</span></span> <span data-ttu-id="fe46c-107">有关详细信息，请参阅 [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="fe46c-107">For more information, see [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fe46c-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="fe46c-108">Prerequisites</span></span>  
  
-   <span data-ttu-id="fe46c-109">必须具有包含 MDS 管理的数据的工作表。</span><span class="sxs-lookup"><span data-stu-id="fe46c-109">You must have a worksheet that contains MDS-managed data.</span></span> <span data-ttu-id="fe46c-110">有关详细信息，请参阅将[数据从 MDS 加载到 Excel](export-data-to-excel-from-master-data-services.md)中。</span><span class="sxs-lookup"><span data-stu-id="fe46c-110">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="fe46c-111">可选。</span><span class="sxs-lookup"><span data-stu-id="fe46c-111">Optional.</span></span> <span data-ttu-id="fe46c-112">您可以在检查是否存在相似性之前将其他数据和 MDS 管理的数据合并在一起。</span><span class="sxs-lookup"><span data-stu-id="fe46c-112">You can combine other data with the MDS-managed data before checking for similarities.</span></span> <span data-ttu-id="fe46c-113">有关详细信息，请参阅 [合并数据（用于 Excel 的 MDS 外接程序）](combine-data-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="fe46c-113">For more information, see [Combine Data &#40;MDS Add-in for Excel&#41;](combine-data-mds-add-in-for-excel.md).</span></span>  
  
### <a name="to-find-similarities-by-using-the-default-knowledge-base"></a><span data-ttu-id="fe46c-114">使用默认知识库查找相似性</span><span class="sxs-lookup"><span data-stu-id="fe46c-114">To find similarities by using the default knowledge base</span></span>  
  
1.  <span data-ttu-id="fe46c-115">从包含 MDS 管理的数据的工作表中，在“数据质量”组中单击“匹配数据”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fe46c-115">From the worksheet that contains MDS-managed data, in the **Data Quality** group, click **Match Data**.</span></span>  
  
2.  <span data-ttu-id="fe46c-116">在“匹配数据”对话框中，从“DQS 知识库”列表中选择“DQS 数据(默认)”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fe46c-116">In the **Match Data** dialog box, from the **DQS Knowledge Base** list, select **DQS Data (default)**.</span></span>  
  
3.  <span data-ttu-id="fe46c-117">对于包含要匹配的数据的每个列，在该对话框中添加一行。</span><span class="sxs-lookup"><span data-stu-id="fe46c-117">For each column that contains data you want to match, add a row in the dialog box.</span></span> <span data-ttu-id="fe46c-118">有关此对话框中字段的详细信息，请参阅 [How to Set Matching Rule Parameters](../../data-quality-services/create-a-matching-policy.md#MatchingRules)。</span><span class="sxs-lookup"><span data-stu-id="fe46c-118">For information about the fields in this dialog box, see [How to Set Matching Rule Parameters](../../data-quality-services/create-a-matching-policy.md#MatchingRules).</span></span>  
  
4.  <span data-ttu-id="fe46c-119">在所有权重值的总和等于 100% 时，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="fe46c-119">When the total of all weight values equals 100 percent, click **OK**.</span></span>  
  
### <a name="to-find-similarities-by-using-a-custom-knowledge-base"></a><span data-ttu-id="fe46c-120">使用自定义知识库查找相似性</span><span class="sxs-lookup"><span data-stu-id="fe46c-120">To find similarities by using a custom knowledge base</span></span>  
  
1.  <span data-ttu-id="fe46c-121">从包含 MDS 管理的数据的工作表中，在“数据质量”组中单击“匹配数据”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fe46c-121">From the worksheet that contains MDS-managed data, in the **Data Quality** group, click **Match Data**.</span></span>  
  
2.  <span data-ttu-id="fe46c-122">从 **“DQS 知识库”** 列表中，选择您的自定义知识库的名称。</span><span class="sxs-lookup"><span data-stu-id="fe46c-122">From the **DQS Knowledge Base** list, select the name of your custom knowledge base.</span></span>  
  
3.  <span data-ttu-id="fe46c-123">对于该工作表中每一列，选择一个 DQS 域。</span><span class="sxs-lookup"><span data-stu-id="fe46c-123">For each column in the worksheet, select a DQS domain.</span></span>  
  
4.  <span data-ttu-id="fe46c-124">在所有 DQS 域都映射到该工作表中的列后，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="fe46c-124">When all DQS domains are mapped to columns in the worksheet, click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="fe46c-125">后续步骤</span><span class="sxs-lookup"><span data-stu-id="fe46c-125">Next Steps</span></span>  
  
-   <span data-ttu-id="fe46c-126">查看其他信息以便确定哪些数据是类似的。</span><span class="sxs-lookup"><span data-stu-id="fe46c-126">View additional information to determine which data is similar.</span></span> <span data-ttu-id="fe46c-127">有关详细信息，请参阅[数据质量匹配列（用于 Excel 的 MDS 外接程序）](data-quality-matching-columns-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="fe46c-127">For more information, see [Data Quality Matching Columns &#40;MDS Add-in for Excel&#41;](data-quality-matching-columns-mds-add-in-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe46c-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe46c-128">See Also</span></span>  
 <span data-ttu-id="fe46c-129">[MDS Add-in for Excel 中的数据质量匹配](data-quality-matching-in-the-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="fe46c-129">[Data Quality Matching in the MDS Add-in for Excel](data-quality-matching-in-the-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="fe46c-130">数据匹配</span><span class="sxs-lookup"><span data-stu-id="fe46c-130">Data Matching</span></span>](../../data-quality-services/data-matching.md)  
  
  
