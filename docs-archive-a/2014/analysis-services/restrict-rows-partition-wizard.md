---
title: 限制 (分区向导) 的行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.typefilterexpression.f1
ms.assetid: eec8da8f-eab4-4ac4-a81d-995c814f88ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b0acc9ab24cfe92877d9abcd86353c85b4f8905
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579134"
---
# <a name="restrict-rows-partition-wizard"></a><span data-ttu-id="9307d-102">限制行（分区向导）</span><span class="sxs-lookup"><span data-stu-id="9307d-102">Restrict Rows (Partition Wizard)</span></span>
  <span data-ttu-id="9307d-103">可以使用 **“限制行”** 页，限制从指定表中检索、聚合并包括到分区中的行。</span><span class="sxs-lookup"><span data-stu-id="9307d-103">Use the **Restrict Rows** page to restrict the rows that will be retrieved from the specified table and will be aggregated and included in the partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9307d-104"> 只有在 **“指定源信息”** 页中选择了单个表时，才会显示此页。</span><span class="sxs-lookup"><span data-stu-id="9307d-104">This page is appears only if you selected a single table in the **Specify Source Information** page.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="9307d-105"> 如果在 **“指定源信息”** 页上的 **“可用表”** 中指定了由另一个分区使用的表，则必须在 **“限制行”** 页中提供查询，否则在多维数据集中会出现数据重复的风险。</span><span class="sxs-lookup"><span data-stu-id="9307d-105">If you specified a table in **Available Tables** on the **Specify Source Information** page that is used by another partition, you must provide a query in the **Restrict Rows** page or risk duplicating data in the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9307d-106">选项</span><span class="sxs-lookup"><span data-stu-id="9307d-106">Options</span></span>  
 <span data-ttu-id="9307d-107">**指定查询以限制行**</span><span class="sxs-lookup"><span data-stu-id="9307d-107">**Specify a query to restrict rows**</span></span>  
 <span data-ttu-id="9307d-108">选择此选项可以输入查询，对进入“查询”\*\*\*\* 框中的行进行限制。</span><span class="sxs-lookup"><span data-stu-id="9307d-108">Select to enter a query that restricts rows into the **Query** box.</span></span>  
  
 <span data-ttu-id="9307d-109">如果在选择此选项时 **“提供 WHERE 子句”** 为空，将使用一个从前面选择的表中检索所有列和所有行的 SQL 语句来填充该选项。</span><span class="sxs-lookup"><span data-stu-id="9307d-109">If **Supply a WHERE clause** is empty when this option is selected, that option is populated with an SQL statement that retrieves all columns and all rows from the previously selected table.</span></span>  
  
 <span data-ttu-id="9307d-110">**查询**</span><span class="sxs-lookup"><span data-stu-id="9307d-110">**Query**</span></span>  
 <span data-ttu-id="9307d-111">键入或修改在处理分区过程中从表中检索行时所使用的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="9307d-111">Type or modify the SQL statement used when retrieving rows from the table when the partition is processed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9307d-112">通过指定 WHERE 子句，可以将记录的子集用于此分区。</span><span class="sxs-lookup"><span data-stu-id="9307d-112">By specifying a WHERE clause, a subset of records can be used for this partition.</span></span> <span data-ttu-id="9307d-113">当多个分区都基于单一事实数据表时，防止数据重复很重要。</span><span class="sxs-lookup"><span data-stu-id="9307d-113">This is essential to prevent duplication of data when multiple partitions are based on a single fact table.</span></span>  
  
 <span data-ttu-id="9307d-114">**检查**</span><span class="sxs-lookup"><span data-stu-id="9307d-114">**Check**</span></span>  
 <span data-ttu-id="9307d-115">验证“查询”\*\*\*\* 中的语句是否为有效的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="9307d-115">Verifies that the statement in **Query** is a valid SQL statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9307d-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9307d-116">See Also</span></span>  
 [<span data-ttu-id="9307d-117">分区（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="9307d-117">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
