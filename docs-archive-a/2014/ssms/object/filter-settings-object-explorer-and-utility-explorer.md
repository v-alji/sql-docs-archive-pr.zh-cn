---
title: 筛选设置（对象资源管理器和实用工具资源管理器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.filtersettings.f1
- sql12.swb.common.filtersettings.f1
ms.assetid: 4aab04bc-e1ab-4d4b-ab74-b287fc805bc2
author: stevestein
ms.author: sstein
ms.openlocfilehash: c31fbcbef9cbab86a7bd3ab7b2fae21e626aaa59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576495"
---
# <a name="filter-settings-object-explorer-and-utility-explorer"></a><span data-ttu-id="82ed1-102">筛选设置（对象资源管理器和实用工具资源管理器）</span><span class="sxs-lookup"><span data-stu-id="82ed1-102">Filter Settings (Object Explorer and Utility Explorer)</span></span>
  <span data-ttu-id="82ed1-103">使用此对话框可以指定筛选器。</span><span class="sxs-lookup"><span data-stu-id="82ed1-103">Use this dialog box to specify a filter.</span></span> <span data-ttu-id="82ed1-104">使用筛选器，可以将对象资源管理器和实用工具资源管理器配置为仅显示符合特定条件的项。</span><span class="sxs-lookup"><span data-stu-id="82ed1-104">A filter allows you to configure Object Explorer and Utility Explorer to display only items that meet specific criteria.</span></span> <span data-ttu-id="82ed1-105">例如，可以使用筛选器仅显示名称中包含词语“维护”的作业。</span><span class="sxs-lookup"><span data-stu-id="82ed1-105">For example, you can use a filter to show only jobs with names that contain the word "Maintenance."</span></span> <span data-ttu-id="82ed1-106">“筛选设置”  对话框的标题包含服务器的名称，还可能包含数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="82ed1-106">The header for the **Filter Settings** dialog box contains the name of the server, and it may contain the name of the database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="82ed1-107">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="82ed1-107">UI element list</span></span>  
 <span data-ttu-id="82ed1-108">**属性**</span><span class="sxs-lookup"><span data-stu-id="82ed1-108">**Property**</span></span>  
 <span data-ttu-id="82ed1-109">显示要筛选的属性。</span><span class="sxs-lookup"><span data-stu-id="82ed1-109">Displays the property to filter on.</span></span>  
  
 <span data-ttu-id="82ed1-110">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="82ed1-110">**Operator**</span></span>  
 <span data-ttu-id="82ed1-111">选择筛选器将值应用于属性的方式。</span><span class="sxs-lookup"><span data-stu-id="82ed1-111">Select the way that the filter applies the value to the property.</span></span> <span data-ttu-id="82ed1-112">下面是可用的选项：</span><span class="sxs-lookup"><span data-stu-id="82ed1-112">There are the following options:</span></span>  
  
-   <span data-ttu-id="82ed1-113">**等于**</span><span class="sxs-lookup"><span data-stu-id="82ed1-113">**Equals**</span></span>  
  
     <span data-ttu-id="82ed1-114">筛选器将显示属性和值都精确匹配的项。</span><span class="sxs-lookup"><span data-stu-id="82ed1-114">The filter shows items where the property and the value are an exact match.</span></span>  
  
-   <span data-ttu-id="82ed1-115">**包含**</span><span class="sxs-lookup"><span data-stu-id="82ed1-115">**Contains**</span></span>  
  
     <span data-ttu-id="82ed1-116">筛选器将显示属性包含指定值的项。</span><span class="sxs-lookup"><span data-stu-id="82ed1-116">The filter shows items where the property contains the value.</span></span> <span data-ttu-id="82ed1-117">属性可能会包含其他文本。</span><span class="sxs-lookup"><span data-stu-id="82ed1-117">The property may contain other text.</span></span>  
  
-   <span data-ttu-id="82ed1-118">**不包含**</span><span class="sxs-lookup"><span data-stu-id="82ed1-118">**Does not contain**</span></span>  
  
     <span data-ttu-id="82ed1-119">筛选器将显示属性不包含指定值的项。</span><span class="sxs-lookup"><span data-stu-id="82ed1-119">The filter shows items that where the property does not contain the value.</span></span>  
  
-   <span data-ttu-id="82ed1-120">**小于**</span><span class="sxs-lookup"><span data-stu-id="82ed1-120">**Less than**</span></span>  
  
     <span data-ttu-id="82ed1-121">此筛选器适用于日期，将显示日期早于指定值的项。</span><span class="sxs-lookup"><span data-stu-id="82ed1-121">Available for dates, this filter shows items whose date is before the value provided.</span></span>  
  
-   <span data-ttu-id="82ed1-122">**小于或等于**</span><span class="sxs-lookup"><span data-stu-id="82ed1-122">**Less than or equal**</span></span>  
  
     <span data-ttu-id="82ed1-123">此筛选器适用于日期，将显示日期早于或等于指定值的项。</span><span class="sxs-lookup"><span data-stu-id="82ed1-123">Available for dates, this filter shows items whose date contains or is before the value provided.</span></span>  
  
-   <span data-ttu-id="82ed1-124">**大于**</span><span class="sxs-lookup"><span data-stu-id="82ed1-124">**Greater than**</span></span>  
  
     <span data-ttu-id="82ed1-125">此筛选器适用于日期，将显示日期晚于指定值的项。</span><span class="sxs-lookup"><span data-stu-id="82ed1-125">Available for dates, this filter shows items whose date is after the value provided.</span></span>  
  
-   <span data-ttu-id="82ed1-126">**大于或等于**</span><span class="sxs-lookup"><span data-stu-id="82ed1-126">**Greater than or equal**</span></span>  
  
     <span data-ttu-id="82ed1-127">此筛选器适用于日期，将显示日期晚于或等于指定值的项。</span><span class="sxs-lookup"><span data-stu-id="82ed1-127">Available for dates, this filter shows items whose date contains or is after the value provided.</span></span>  
  
-   <span data-ttu-id="82ed1-128">**Between**</span><span class="sxs-lookup"><span data-stu-id="82ed1-128">**Between**</span></span>  
  
     <span data-ttu-id="82ed1-129">此筛选器适用于日期，将显示日期介于指定的两个日期之间的项。</span><span class="sxs-lookup"><span data-stu-id="82ed1-129">Available for dates, this filter shows items whose date is between two dates provided.</span></span> <span data-ttu-id="82ed1-130">选择“介于”  并按 Tab 即可添加另一行，用于指定第二个日期。</span><span class="sxs-lookup"><span data-stu-id="82ed1-130">Select **Between** and press TAB to add another row allowing entry of the second date.</span></span>  
  
-   <span data-ttu-id="82ed1-131">**不介于**</span><span class="sxs-lookup"><span data-stu-id="82ed1-131">**Not between**</span></span>  
  
     <span data-ttu-id="82ed1-132">此筛选器适用于日期，将显示日期不介于指定的两个日期之间的项。</span><span class="sxs-lookup"><span data-stu-id="82ed1-132">Available for dates, this filter shows items whose date is before or after two dates provided.</span></span> <span data-ttu-id="82ed1-133">选择“不介于”  并按 Tab 移出“运算符”  列，即可添加另一行，用于指定第二个日期。</span><span class="sxs-lookup"><span data-stu-id="82ed1-133">Select **Not Between** and tab out of the **Operator** column to add another row allowing entry of the second date.</span></span>  
  
 <span data-ttu-id="82ed1-134">**值**</span><span class="sxs-lookup"><span data-stu-id="82ed1-134">**Value**</span></span>  
 <span data-ttu-id="82ed1-135">键入要与属性进行比较的值。</span><span class="sxs-lookup"><span data-stu-id="82ed1-135">Type the value to compare to the property.</span></span> <span data-ttu-id="82ed1-136">对于日期，请单击下箭头显示日历，以选择日期。</span><span class="sxs-lookup"><span data-stu-id="82ed1-136">For dates, click the down arrow to show a calendar for selecting the date.</span></span>  
  
 <span data-ttu-id="82ed1-137">**清除筛选器**</span><span class="sxs-lookup"><span data-stu-id="82ed1-137">**Clear Filter**</span></span>  
 <span data-ttu-id="82ed1-138">删除所有当前筛选设置。</span><span class="sxs-lookup"><span data-stu-id="82ed1-138">Removes all current filter settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ed1-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="82ed1-139">See Also</span></span>  
 <span data-ttu-id="82ed1-140">[使用 SQL Server Management Studio](../sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="82ed1-140">[Use SQL Server Management Studio](../sql-server-management-studio-ssms.md) </span></span>  
 [<span data-ttu-id="82ed1-141">SQL Server 实用工具功能和任务</span><span class="sxs-lookup"><span data-stu-id="82ed1-141">SQL Server Utility Features and Tasks</span></span>](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
