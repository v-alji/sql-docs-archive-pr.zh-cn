---
title: 表绑定详细信息 (分区源 "对话框中)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitiontableselection.f1
ms.assetid: 67d05389-81ae-4a6b-947b-986d37ec72b1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10845e18a2b7c74a8ed3aeec42f710b9706dc94a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580912"
---
# <a name="table-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="aabe1-102">表绑定详细信息（“分区源”对话框）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="aabe1-102">Table Binding Detail (Partition Source Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="aabe1-103">可以使用 **“分区源”** 对话框中的 **“表绑定”** 选项，指定为分区提供数据的事实数据表。</span><span class="sxs-lookup"><span data-stu-id="aabe1-103">Use the **Table Binding** option in the **Partition Source** dialog box to specify the fact table that provides the data for the partition.</span></span> <span data-ttu-id="aabe1-104">通过从 **“分区源”** 对话框中的 **“绑定类型”** 选项中选择 **“表绑定”** ，可以显示此窗格。</span><span class="sxs-lookup"><span data-stu-id="aabe1-104">You can display this pane by selecting **Table Binding** from the **Binding type** option in the **Partition Source** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="aabe1-105">选项</span><span class="sxs-lookup"><span data-stu-id="aabe1-105">Options</span></span>  
 <span data-ttu-id="aabe1-106">**度量值组**</span><span class="sxs-lookup"><span data-stu-id="aabe1-106">**Measure group**</span></span>  
 <span data-ttu-id="aabe1-107">显示此分区的度量值组。</span><span class="sxs-lookup"><span data-stu-id="aabe1-107">Displays the measure group for this partition.</span></span>  
  
 <span data-ttu-id="aabe1-108">**查找范围**</span><span class="sxs-lookup"><span data-stu-id="aabe1-108">**Look in**</span></span>  
 <span data-ttu-id="aabe1-109">选择包含此分区的源表的数据源或数据源视图。</span><span class="sxs-lookup"><span data-stu-id="aabe1-109">Select the data source or data source view that contains the source tables for this partition.</span></span> <span data-ttu-id="aabe1-110">默认情况下，将选择所选度量值组使用的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="aabe1-110">The data source view used by the selected measure group is selected by default.</span></span>  
  
 <span data-ttu-id="aabe1-111">**筛选表**</span><span class="sxs-lookup"><span data-stu-id="aabe1-111">**Filter tables**</span></span>  
 <span data-ttu-id="aabe1-112">键入字符串，用于按表名对“可用表”\*\*\*\* 中显示的表进行限制。</span><span class="sxs-lookup"><span data-stu-id="aabe1-112">Type the string used to restrict, by table name, the tables displayed in **Available tables**.</span></span>  
  
 <span data-ttu-id="aabe1-113">**查找表**</span><span class="sxs-lookup"><span data-stu-id="aabe1-113">**Find tables**</span></span>  
 <span data-ttu-id="aabe1-114">选择此项可以刷新“可用表”\*\*\*\* 中表的列表，如果在“筛选表”\*\*\*\* 中指定了字符串，则可以进一步限制该列表。</span><span class="sxs-lookup"><span data-stu-id="aabe1-114">Select to refresh the list of tables in **Available tables**, further restricting the list if a string was specified in **Filter tables**.</span></span>  
  
 <span data-ttu-id="aabe1-115">**可用表**</span><span class="sxs-lookup"><span data-stu-id="aabe1-115">**Available tables**</span></span>  
 <span data-ttu-id="aabe1-116">单击此项可选择要用作分区的源表的表。</span><span class="sxs-lookup"><span data-stu-id="aabe1-116">Click to select the table to use as a source table for the partition.</span></span>  
  
 <span data-ttu-id="aabe1-117">如果 **“筛选表”** 中未指定任何筛选器，则对于 **“查找范围”** 中指定的数据源或数据源视图中的表，只要在结构上与 **“度量值组”** 中指定的度量值组所使用的事实数据表相似，就会在列表中列出。</span><span class="sxs-lookup"><span data-stu-id="aabe1-117">If no filter is specified in **Filter tables**, all tables in the data source or data source view specified in **Look in** that are similar in structure to the fact table used by the measure group specified in **Measure group** are listed.</span></span>  
  
 <span data-ttu-id="aabe1-118">如果 **“筛选表”** 中指定了筛选器，通过将筛选器与符合上述条件的表名进行对比，可以进一步限制列表。</span><span class="sxs-lookup"><span data-stu-id="aabe1-118">If a filter is specified in **Filter tables**, the list is further restricted by comparing the filter against the table names that meet the above criteria.</span></span> <span data-ttu-id="aabe1-119">只有那些包含 **“筛选表”** 中指定字符串的表才会显示。</span><span class="sxs-lookup"><span data-stu-id="aabe1-119">Only those tables that contain the string specified in **Filter tables** are displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aabe1-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aabe1-120">See Also</span></span>  
 [<span data-ttu-id="aabe1-121">"分区源" 对话框 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="aabe1-121">Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  
