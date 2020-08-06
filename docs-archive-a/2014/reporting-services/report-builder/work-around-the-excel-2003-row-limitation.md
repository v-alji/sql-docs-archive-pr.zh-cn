---
title: 解决 Excel 行限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a4c8700b-bef5-4440-a99c-bba5dcc46bfd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 128f65cf09833d23234da10bf7744c6ce30065ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579506"
---
# <a name="work-around-the-excel-row-limitation"></a><span data-ttu-id="e17fa-102">避开 Excel 行限制</span><span class="sxs-lookup"><span data-stu-id="e17fa-102">Work Around the Excel Row Limitation</span></span>
  <span data-ttu-id="e17fa-103">本主题介绍在将报表导出到 Excel 时，如何避开 Excel 2003 的行限制。</span><span class="sxs-lookup"><span data-stu-id="e17fa-103">This topic explains how to work around the Excel 2003 row limitation when you export reports to Excel.</span></span> <span data-ttu-id="e17fa-104">本解决方法适用于只包含表的报表。</span><span class="sxs-lookup"><span data-stu-id="e17fa-104">The workaround is for a report that contains only a table.</span></span>  
  
 <span data-ttu-id="e17fa-105">Excel 2003 每个工作表最多支持 65,536 行。</span><span class="sxs-lookup"><span data-stu-id="e17fa-105">Excel 2003 supports a maximum of 65,536 rows per worksheet.</span></span> <span data-ttu-id="e17fa-106">您可通过在特定行数后强制添加一个显式的分页符来避开此限制。</span><span class="sxs-lookup"><span data-stu-id="e17fa-106">You can work around this limitation by forcing an explicit page break after a certain number of rows.</span></span> <span data-ttu-id="e17fa-107">Excel 呈现器会为每个显式分页符创建一个新的工作表。</span><span class="sxs-lookup"><span data-stu-id="e17fa-107">The Excel renderer creates a new worksheet for each explicit page break.</span></span>  
  
### <a name="to-create-an-explicit-page-break"></a><span data-ttu-id="e17fa-108">创建显式分页符</span><span class="sxs-lookup"><span data-stu-id="e17fa-108">To create an explicit page break</span></span>  
  
1.  <span data-ttu-id="e17fa-109">在 [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] 或报表管理器中打开报表。</span><span class="sxs-lookup"><span data-stu-id="e17fa-109">Open the report in [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] or Report Manager.</span></span>  
  
2.  <span data-ttu-id="e17fa-110">右键单击表中的数据行，然后单击 "**添加组**" "  >  **父组**" 以添加外部表组。</span><span class="sxs-lookup"><span data-stu-id="e17fa-110">Right click the Data row in the table, and then click **Add Group** > **Parent Group** to add an outer table group.</span></span>  
  
     <span data-ttu-id="e17fa-111">![选择父组](../media/datarow-selectparentgroup.png "选择父组")</span><span class="sxs-lookup"><span data-stu-id="e17fa-111">![Select the Parent Group](../media/datarow-selectparentgroup.png "Select the Parent Group")</span></span>  
  
3.  <span data-ttu-id="e17fa-112">在 **“分组依据”** 表达式框中输入下面的公式，然后单击 **“确定”** 添加父组。</span><span class="sxs-lookup"><span data-stu-id="e17fa-112">Enter the following formula in the **Group by** expression box, and then click **OK** to add the parent group.</span></span>  
  
     <span data-ttu-id="e17fa-113">=Int((RowNumber(Nothing)-1)/65000)</span><span class="sxs-lookup"><span data-stu-id="e17fa-113">=Int((RowNumber(Nothing)-1)/65000)</span></span>  
  
     <span data-ttu-id="e17fa-114">此公式会为数据集中的每个组（65000 行为一组）分配一个编号。</span><span class="sxs-lookup"><span data-stu-id="e17fa-114">The formula assigns a number to each set of 65000 rows in the dataset.</span></span> <span data-ttu-id="e17fa-115">如果为组定义了分页符，则此表达式会每隔 65000 行插入一个分页符。</span><span class="sxs-lookup"><span data-stu-id="e17fa-115">When a page break is defined for the group, the expression results in a page break every 65000 rows.</span></span>  
  
     <span data-ttu-id="e17fa-116">添加外部表组会向报表添加一个组列。</span><span class="sxs-lookup"><span data-stu-id="e17fa-116">Adding the outer table group adds a group column to the report.</span></span>  
  
4.  <span data-ttu-id="e17fa-117">删除组列：右键单击列标题，单击“删除列”，选择“仅删除列”，然后单击“确定”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e17fa-117">Delete the group column by right-clicking on the column header, clicking **Delete Columns**, selecting **Delete columns only**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e17fa-118">![删除组列](../media/groupcolumn-delete-updated.png "删除组列")</span><span class="sxs-lookup"><span data-stu-id="e17fa-118">![Delete a group column](../media/groupcolumn-delete-updated.png "Delete a group column")</span></span>  
  
5.  <span data-ttu-id="e17fa-119">右键单击 **“行组”** 部分中的 **“组 1”** ，然后单击 **“组属性”**。</span><span class="sxs-lookup"><span data-stu-id="e17fa-119">Right click **Group 1** in the **Row Groups** section, and then click **Group Properties**.</span></span>  
  
     <span data-ttu-id="e17fa-120">![查看组属性](../media/groupproperties-updated.png "查看组属性")</span><span class="sxs-lookup"><span data-stu-id="e17fa-120">![View group properties](../media/groupproperties-updated.png "View group properties")</span></span>  
  
6.  <span data-ttu-id="e17fa-121">在 **“组属性”** 对话框的 **“排序”** 页面上，选择默认排序选项，然后单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="e17fa-121">On the **Sorting** page of the **Group Properties** dialog box, select the default sorting option and click **Delete**.</span></span>  
  
     <span data-ttu-id="e17fa-122">![删除默认排序](../media/groupproperties-sorting-updated.png "删除默认排序")</span><span class="sxs-lookup"><span data-stu-id="e17fa-122">![Delete default sorting](../media/groupproperties-sorting-updated.png "Delete default sorting")</span></span>  
  
7.  <span data-ttu-id="e17fa-123">在 **“分页符”** 页面上，单击 **“在组的各实例之间”** ，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="e17fa-123">On the **Page Breaks** page, click **Between each instance of a group** and then click **OK**.</span></span>  
  
     <span data-ttu-id="e17fa-124">![设置分页符](../media/groupproperties-pagebreaks-updated.png "设置分页符")</span><span class="sxs-lookup"><span data-stu-id="e17fa-124">![Set page breaks](../media/groupproperties-pagebreaks-updated.png "Set page breaks")</span></span>  
  
8.  <span data-ttu-id="e17fa-125">保存报表。</span><span class="sxs-lookup"><span data-stu-id="e17fa-125">Save the report.</span></span> <span data-ttu-id="e17fa-126">在将其导出至 Excel 时，其会导出成多个工作表，且每个工作表最多包含 65000 行。</span><span class="sxs-lookup"><span data-stu-id="e17fa-126">When you export it to Excel, it exports to multiple worksheets and each worksheet contains a maximum of 65000 rows.</span></span>  
  
  
