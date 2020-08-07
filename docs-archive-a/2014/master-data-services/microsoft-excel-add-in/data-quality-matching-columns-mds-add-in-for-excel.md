---
title: 数据质量匹配列 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 939ec9727cc81ce3b206b8bc7ca3ed8dd62c3877
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576856"
---
# <a name="data-quality-matching-columns-mds-add-in-for-excel"></a><span data-ttu-id="87819-102">数据质量匹配列（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="87819-102">Data Quality Matching Columns (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="87819-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 中，匹配数据后，在功能区上的“数据质量”组中，可单击“显示详细信息”以显示提供匹配详细信息的列\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87819-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], after you match data, in the **Data Quality** group on the ribbon, you can click **Show Details** to display columns that provide matching details.</span></span>  
  
 <span data-ttu-id="87819-104">下表显示匹配数据时显示的列。</span><span class="sxs-lookup"><span data-stu-id="87819-104">The following table shows the columns that are displayed when matching data.</span></span>  
  
|<span data-ttu-id="87819-105">名称</span><span class="sxs-lookup"><span data-stu-id="87819-105">Name</span></span>|<span data-ttu-id="87819-106">说明</span><span class="sxs-lookup"><span data-stu-id="87819-106">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="87819-107">**CLUSTER_ID**</span><span class="sxs-lookup"><span data-stu-id="87819-107">**CLUSTER_ID**</span></span>|<span data-ttu-id="87819-108">用于对相似记录进行分组的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="87819-108">A unique identifier used to group similar records.</span></span> <span data-ttu-id="87819-109">所有相似的行都具有相同的 **CLUSTER_ID**。</span><span class="sxs-lookup"><span data-stu-id="87819-109">All rows that are similar have the same **CLUSTER_ID**.</span></span> <span data-ttu-id="87819-110">如果没有为某一行显示 **CLUSTER_ID** ，则找不到相似的记录。</span><span class="sxs-lookup"><span data-stu-id="87819-110">If no **CLUSTER_ID** is displayed for a row, then no similar records were found.</span></span>|  
|<span data-ttu-id="87819-111">**RECORD_ID**</span><span class="sxs-lookup"><span data-stu-id="87819-111">**RECORD_ID**</span></span>|<span data-ttu-id="87819-112">用于标识记录的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="87819-112">A unique identifier used to identify records.</span></span> <span data-ttu-id="87819-113">与在 MDS 存储库中存储的代码值相似，它是用于标识记录的值。</span><span class="sxs-lookup"><span data-stu-id="87819-113">Similar to the Code value stored in the MDS repository, it is a value used to identify a record.</span></span> <span data-ttu-id="87819-114">每次出现匹配时都将自动生成该值。</span><span class="sxs-lookup"><span data-stu-id="87819-114">It is generated automatically each time matching takes place.</span></span>|  
|<span data-ttu-id="87819-115">**PIVOT_MARK**</span><span class="sxs-lookup"><span data-stu-id="87819-115">**PIVOT_MARK**</span></span>|<span data-ttu-id="87819-116">其他记录与其进行比较的任意记录；它不具有得分值。</span><span class="sxs-lookup"><span data-stu-id="87819-116">An arbitrary record that other records are compared to; it does not have a score value.</span></span>|  
|<span data-ttu-id="87819-117">**分值**</span><span class="sxs-lookup"><span data-stu-id="87819-117">**SCORE**</span></span>|<span data-ttu-id="87819-118">表示组中的记录与透视记录的相似程度。</span><span class="sxs-lookup"><span data-stu-id="87819-118">Represents how similar the records in the group are to the pivot record.</span></span> <span data-ttu-id="87819-119">该得分是由 DQS 确定的。</span><span class="sxs-lookup"><span data-stu-id="87819-119">This score is determined by DQS.</span></span> <span data-ttu-id="87819-120">如果没有显示任何得分，则该记录是其他记录的透视记录，或者找不到匹配项。</span><span class="sxs-lookup"><span data-stu-id="87819-120">If no score is displayed, either the record is the pivot for other records, or no matches were found.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87819-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87819-121">See Also</span></span>  
 <span data-ttu-id="87819-122">[MDS Add-in for Excel 中的数据质量匹配](data-quality-matching-in-the-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="87819-122">[Data Quality Matching in the MDS Add-in for Excel](data-quality-matching-in-the-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="87819-123">[匹配相似的数据 &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="87819-123">[Match Similar Data &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="87819-124">数据匹配</span><span class="sxs-lookup"><span data-stu-id="87819-124">Data Matching</span></span>](../../data-quality-services/data-matching.md)  
  
  
