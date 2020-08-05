---
title: 指定基于使用情况的优化向导) 的查询条件 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.specifyquerycriteria.f1
ms.assetid: 3193adc2-af9f-4234-a4cc-dea0c280a724
author: minewiskan
ms.author: owend
ms.openlocfilehash: f3b93034a089ff3121155e35de4cec96846824a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579812"
---
# <a name="specify-query-criteria-usage-based-optimization-wizard"></a><span data-ttu-id="f3190-102">指定查询条件（基于使用情况的优化向导）</span><span class="sxs-lookup"><span data-stu-id="f3190-102">Specify Query Criteria (Usage-Based Optimization Wizard)</span></span>
  <span data-ttu-id="f3190-103">可以使用 **“指定查询条件”** 页，选择一个或多个筛选器选项以指定要优化的查询。</span><span class="sxs-lookup"><span data-stu-id="f3190-103">Use the **Specify Query Criteria** page to choose one or more filter options in order to identify queries to optimize.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3190-104">如果 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 无法连接到查询日志，则将禁用此页。</span><span class="sxs-lookup"><span data-stu-id="f3190-104">This page is disabled if [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cannot connect to the query log.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f3190-105">选项</span><span class="sxs-lookup"><span data-stu-id="f3190-105">Options</span></span>  
 <span data-ttu-id="f3190-106">**查询日志统计信息**</span><span class="sxs-lookup"><span data-stu-id="f3190-106">**Query log statistics**</span></span>  
 <span data-ttu-id="f3190-107">显示有关在所选分区的查询日志中所存储查询的信息。</span><span class="sxs-lookup"><span data-stu-id="f3190-107">Displays information about the queries stored in the query log for the selected partitions.</span></span> <span data-ttu-id="f3190-108">将显示以下项：</span><span class="sxs-lookup"><span data-stu-id="f3190-108">The following items are displayed:</span></span>  
  
|<span data-ttu-id="f3190-109">术语</span><span class="sxs-lookup"><span data-stu-id="f3190-109">Term</span></span>|<span data-ttu-id="f3190-110">定义</span><span class="sxs-lookup"><span data-stu-id="f3190-110">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="f3190-111">**查询总计**</span><span class="sxs-lookup"><span data-stu-id="f3190-111">**Total queries**</span></span>|<span data-ttu-id="f3190-112">显示在所选分区的查询日志中所存储查询的总数。</span><span class="sxs-lookup"><span data-stu-id="f3190-112">Displays the total number of queries stored in the query log for the selected partitions.</span></span>|  
|<span data-ttu-id="f3190-113">**不同查询**</span><span class="sxs-lookup"><span data-stu-id="f3190-113">**Distinct queries**</span></span>|<span data-ttu-id="f3190-114">显示在所选分区的查询日志中所存储的不同查询数。</span><span class="sxs-lookup"><span data-stu-id="f3190-114">Displays the number of distinct queries stored in the query log for the selected partitions.</span></span>|  
|<span data-ttu-id="f3190-115">**不同用户数**</span><span class="sxs-lookup"><span data-stu-id="f3190-115">**Distinct users**</span></span>|<span data-ttu-id="f3190-116">显示与在所选分区的查询日志中所存储查询关联的不同用户总数。</span><span class="sxs-lookup"><span data-stu-id="f3190-116">Displays the total number of distinct users associated with queries stored in the query log for the selected partitions.</span></span>|  
|<span data-ttu-id="f3190-117">**平均响应时间**</span><span class="sxs-lookup"><span data-stu-id="f3190-117">**Average response time**</span></span>|<span data-ttu-id="f3190-118">显示在所选分区的查询日志中所存储查的平均响应时间。</span><span class="sxs-lookup"><span data-stu-id="f3190-118">Displays the average response time for queries stored in the query log for the selected partitions.</span></span>|  
  
 <span data-ttu-id="f3190-119">**开始日期**</span><span class="sxs-lookup"><span data-stu-id="f3190-119">**Beginning date**</span></span>  
 <span data-ttu-id="f3190-120">基于开始日期和时间对查询日志中的查询进行筛选。</span><span class="sxs-lookup"><span data-stu-id="f3190-120">Filters queries in the query log based on a starting date and time.</span></span> <span data-ttu-id="f3190-121">在下拉列表中选择或键入日期。</span><span class="sxs-lookup"><span data-stu-id="f3190-121">Choose or type a date in the dropdown list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3190-122"> 如果未选择 **“结束日期”** ，则将对查询日志中此选项指定日期和时间之后（包括该日期）的所有查询进行筛选。</span><span class="sxs-lookup"><span data-stu-id="f3190-122">If **Ending date** is not selected, all queries in the query log on or after the date and time specified for this option are considered.</span></span>  
  
 <span data-ttu-id="f3190-123">**结束日期**</span><span class="sxs-lookup"><span data-stu-id="f3190-123">**Ending date**</span></span>  
 <span data-ttu-id="f3190-124">基于结束日期和时间对查询日志中的查询进行筛选。</span><span class="sxs-lookup"><span data-stu-id="f3190-124">Filters queries in the query log based on an ending date and time.</span></span> <span data-ttu-id="f3190-125">在下拉列表中选择或键入日期。</span><span class="sxs-lookup"><span data-stu-id="f3190-125">Choose or type a date in the dropdown list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3190-126"> 如果未选择 **“开始日期”** ，则将对查询日志中此选项指定日期和时间之前（包括该日期）的所有查询进行筛选。</span><span class="sxs-lookup"><span data-stu-id="f3190-126">If **Beginning date** is not selected, all queries in the query log on or before the date and time specified for this option are considered.</span></span>  
  
 <span data-ttu-id="f3190-127">**用户**</span><span class="sxs-lookup"><span data-stu-id="f3190-127">**Users**</span></span>  
 <span data-ttu-id="f3190-128">基于指定的用户集对查询日志中的查询进行筛选。</span><span class="sxs-lookup"><span data-stu-id="f3190-128">Filters queries in the query log based on a specified set of users.</span></span> <span data-ttu-id="f3190-129">单击省略号按钮 (**...**) 可以显示“用户选择”\*\*\*\* 对话框，并选择要对其筛选查询的用户。</span><span class="sxs-lookup"><span data-stu-id="f3190-129">Click the ellipsis (**...**) button to display the **User Selection** dialog box and choose users on which to filter queries.</span></span> <span data-ttu-id="f3190-130">有关“用户选择”\*\*\*\* 对话框的详细信息，请参阅[“用户选择”对话框（Analysis Services - 多维数据）](user-selection-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f3190-130">For more information about the **User Selection** dialog box, see [User Selection Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](user-selection-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="f3190-131">**最常见的查询**</span><span class="sxs-lookup"><span data-stu-id="f3190-131">**Most frequent queries**</span></span>  
 <span data-ttu-id="f3190-132">基于对所选分区运行最为频繁的不同查询所占的百分比，对查询日志中的查询进行筛选。</span><span class="sxs-lookup"><span data-stu-id="f3190-132">Filters queries in the query log based on the topmost percentage of the distinct queries most often run for the selected partitions.</span></span> <span data-ttu-id="f3190-133">在文本框中选择或键入一个百分比值。</span><span class="sxs-lookup"><span data-stu-id="f3190-133">Choose or type a percent value in the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3190-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f3190-134">See Also</span></span>  
 <span data-ttu-id="f3190-135">[基于使用情况的优化向导的 F1 帮助](usage-based-optimization-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="f3190-135">[Usage-Based Optimization Wizard F1 Help](usage-based-optimization-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="f3190-136">&#40;多维数据的 Analysis Services 向导&#41;</span><span class="sxs-lookup"><span data-stu-id="f3190-136">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
