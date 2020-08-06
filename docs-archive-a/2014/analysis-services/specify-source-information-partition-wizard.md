---
title: " (分区向导) 指定源信息 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.specifydsvandfacttables.f1
ms.assetid: b6c13587-c690-45d9-af90-b3d652afc55b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 088a8abf7b143b68766f22af37f8ff4fa2065d65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589246"
---
# <a name="specify-source-information-partition-wizard"></a><span data-ttu-id="cf7c4-102">指定源信息（分区向导）</span><span class="sxs-lookup"><span data-stu-id="cf7c4-102">Specify Source Information (Partition Wizard)</span></span>
  <span data-ttu-id="cf7c4-103">可以使用 **“指定源信息”** 页，选择要在其中创建分区的度量值组以及该分区的数据源视图和筛选表。</span><span class="sxs-lookup"><span data-stu-id="cf7c4-103">Use the **Specify Source Information** page to select the measure group in which to create the partition, and also the data source view and filter tables for your partition.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="cf7c4-104"> 如果在其他分区所使用的 **“可用表”** 中指定了表，则必须在 **“限制行”** 页上提供查询，否则多维数据集中的数据可能会发生重复。</span><span class="sxs-lookup"><span data-stu-id="cf7c4-104">If you specify a table in **Available Tables** that is used by another partition, you must provide a query in the **Restrict Rows** page or risk duplicating data in the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cf7c4-105">选项</span><span class="sxs-lookup"><span data-stu-id="cf7c4-105">Options</span></span>  
 <span data-ttu-id="cf7c4-106">**度量值组**</span><span class="sxs-lookup"><span data-stu-id="cf7c4-106">**Measure group**</span></span>  
 <span data-ttu-id="cf7c4-107">选择此分区的度量值组。</span><span class="sxs-lookup"><span data-stu-id="cf7c4-107">Select a measure group for this partition.</span></span>  
  
 <span data-ttu-id="cf7c4-108">**查找范围**</span><span class="sxs-lookup"><span data-stu-id="cf7c4-108">**Look in**</span></span>  
 <span data-ttu-id="cf7c4-109">选择包含此分区的源表的数据源或数据源视图。</span><span class="sxs-lookup"><span data-stu-id="cf7c4-109">Select the data source or data source view that contains the source tables for this partition.</span></span> <span data-ttu-id="cf7c4-110">默认情况下，将选择该度量值组使用的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="cf7c4-110">The data source view used by the measure group is selected by default.</span></span>  
  
 <span data-ttu-id="cf7c4-111">**筛选表**</span><span class="sxs-lookup"><span data-stu-id="cf7c4-111">**Filter tables**</span></span>  
 <span data-ttu-id="cf7c4-112">键入字符串，用于按表名对“可用表”\*\*\*\* 中显示的表进行限制。</span><span class="sxs-lookup"><span data-stu-id="cf7c4-112">Type the string used to restrict, by table name, the tables displayed in **Available tables**.</span></span>  
  
 <span data-ttu-id="cf7c4-113">**查找表**</span><span class="sxs-lookup"><span data-stu-id="cf7c4-113">**Find tables**</span></span>  
 <span data-ttu-id="cf7c4-114">选择此项可以刷新“可用表”\*\*\*\* 中表的列表，如果在“筛选表”\*\*\*\* 中指定了字符串，则可以进一步限制该列表。</span><span class="sxs-lookup"><span data-stu-id="cf7c4-114">Select to refresh the list of tables in **Available tables**, further restricting the list if a string was specified in **Filter tables**.</span></span>  
  
 <span data-ttu-id="cf7c4-115">**可用表**</span><span class="sxs-lookup"><span data-stu-id="cf7c4-115">**Available tables**</span></span>  
 <span data-ttu-id="cf7c4-116">选择要用作分区的源表的表。</span><span class="sxs-lookup"><span data-stu-id="cf7c4-116">Select the tables to use as source tables for partitions.</span></span> <span data-ttu-id="cf7c4-117">**分区向导** 将为 **“可用表”** 中所选的每一个表创建一个分区。</span><span class="sxs-lookup"><span data-stu-id="cf7c4-117">The **Partition Wizard** creates one partition for each table selected in **Available tables**.</span></span>  
  
 <span data-ttu-id="cf7c4-118">如果 **“筛选表”** 中未指定筛选条件，此选项将在数据源或数据源视图中列出 **“查找范围”** 中指定的所有表，以及与 **“度量值组”** 中指定的度量值组所使用的事实数据表结构相似的所有表。</span><span class="sxs-lookup"><span data-stu-id="cf7c4-118">If no filter is specified in **Filter tables**, this option lists all tables in the data source or data source view that are specified in **Look in** and that are similar in structure to the fact table used by the measure group specified in **Measure group**.</span></span>  
  
 <span data-ttu-id="cf7c4-119">如果在 **“筛选表”** 中指定了筛选条件，通过将该筛选条件与符合先前条件的表名进行对比，可以进一步限制列表。</span><span class="sxs-lookup"><span data-stu-id="cf7c4-119">If a filter is specified in **Filter tables**, the list is further restricted by comparing the filter against the table names that meet the previous criteria.</span></span> <span data-ttu-id="cf7c4-120">只有那些包含 **“筛选表”** 中指定字符串的表才会显示。</span><span class="sxs-lookup"><span data-stu-id="cf7c4-120">Only those tables that contain the string specified in **Filter tables** are displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf7c4-121">如果选择了多个表，则无法显示 **“限制行”** 页，也无法对从这些所选表创建的分区限制行。</span><span class="sxs-lookup"><span data-stu-id="cf7c4-121">If more than one table is selected, the **Restrict Rows** page cannot be displayed and rows cannot be restricted for the partitions created from the selected tables.</span></span> <span data-ttu-id="cf7c4-122">若要对每个分区限制行，请为要从中创建分区的每一个表运行一次分区向导。</span><span class="sxs-lookup"><span data-stu-id="cf7c4-122">To restrict rows for each partition, run the Partition Wizard once for each table from which a partition is to be created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf7c4-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf7c4-123">See Also</span></span>  
 [<span data-ttu-id="cf7c4-124">分区（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="cf7c4-124">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
