---
title: " (数据源视图向导中选择表和视图)  (Analysis Services) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourceviewwizard.selecttablesandviews.f1
ms.assetid: ea7d1232-f213-46e9-90d9-0fd616ca003d
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac7159255ef526d871ed8906fc873d9f16d2eb64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692574"
---
# <a name="select-tables-and-views-data-source-view-wizard-analysis-services"></a><span data-ttu-id="183f5-102">选择表和视图（数据源视图向导）(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="183f5-102">Select Tables and Views (Data Source View Wizard) (Analysis Services)</span></span>
  <span data-ttu-id="183f5-103">可以使用 **“选择表和视图”** 页，从要包含在数据源视图中的数据源选择表或视图。</span><span class="sxs-lookup"><span data-stu-id="183f5-103">Use the **Select Tables and Views** page to select the tables or views from the data source that you want to include in the data source view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="183f5-104">选项</span><span class="sxs-lookup"><span data-stu-id="183f5-104">Options</span></span>  
 <span data-ttu-id="183f5-105">**Available objects**</span><span class="sxs-lookup"><span data-stu-id="183f5-105">**Available objects**</span></span>  
 <span data-ttu-id="183f5-106">在数据源架构中列出表和视图。</span><span class="sxs-lookup"><span data-stu-id="183f5-106">Lists the tables and views in the data source schema.</span></span> <span data-ttu-id="183f5-107">如果列出多个架构，则每个对象都以架构名称为前缀。</span><span class="sxs-lookup"><span data-stu-id="183f5-107">The schema name prefixes the name of every object if more than one schema is listed.</span></span> <span data-ttu-id="183f5-108">如果只列出一个架构，那么对象名称就不是以架构名称为前缀。</span><span class="sxs-lookup"><span data-stu-id="183f5-108">If only one schema is listed, the schema's name does not prefix the object names.</span></span>  
  
 <span data-ttu-id="183f5-109">若要按照升序或降序顺序对列表重新排序，请单击 **“名称”** 或 **“类型”**。</span><span class="sxs-lookup"><span data-stu-id="183f5-109">To reorder the list in ascending or descending order, click either **Name** or **Type**.</span></span>  
  
 <span data-ttu-id="183f5-110">**Included objects**</span><span class="sxs-lookup"><span data-stu-id="183f5-110">**Included objects**</span></span>  
 <span data-ttu-id="183f5-111">列出要包含在数据源视图中的表和视图。</span><span class="sxs-lookup"><span data-stu-id="183f5-111">Lists the tables and views to include in the data source view.</span></span>  
  
 <span data-ttu-id="183f5-112">若要按照升序或降序顺序对列表重新排序，请单击 **“名称”** 或 **“类型”**。</span><span class="sxs-lookup"><span data-stu-id="183f5-112">To reorder the list in ascending or descending order, click either **Name** or **Type**.</span></span>  
  
 <span data-ttu-id="183f5-113">**Filter**</span><span class="sxs-lookup"><span data-stu-id="183f5-113">**Filter**</span></span>  
 <span data-ttu-id="183f5-114">筛选“可用对象”下列出的对象。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="183f5-114">Filters the objects listed under **Available objects**.</span></span> <span data-ttu-id="183f5-115">键入字符串，再单击 **“筛选器”** 以仅列出包含指定字符串的名称。</span><span class="sxs-lookup"><span data-stu-id="183f5-115">Type a string, and then click **Filter** to list only the names that contain a specified string.</span></span> <span data-ttu-id="183f5-116">若要查找确切的字符串，请用双引号把字符串括起。</span><span class="sxs-lookup"><span data-stu-id="183f5-116">To find an exact string of characters, enclose the string between double quotation marks.</span></span> <span data-ttu-id="183f5-117">筛选器不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="183f5-117">The filter is not case sensitive.</span></span>  
  
 <span data-ttu-id="183f5-118">可以在筛选器字符串中的任意位置使用下表所列出的通配符：</span><span class="sxs-lookup"><span data-stu-id="183f5-118">You can include the wildcard characters listed in the following table anywhere in the filter string.</span></span>  
  
|<span data-ttu-id="183f5-119">通配符</span><span class="sxs-lookup"><span data-stu-id="183f5-119">Wildcard character</span></span>|<span data-ttu-id="183f5-120">值</span><span class="sxs-lookup"><span data-stu-id="183f5-120">Value</span></span>|  
|------------------------|-----------|  
|**\***|<span data-ttu-id="183f5-121">任何字符串</span><span class="sxs-lookup"><span data-stu-id="183f5-121">Any string of characters</span></span>|  
|**%**|<span data-ttu-id="183f5-122">任何字符串</span><span class="sxs-lookup"><span data-stu-id="183f5-122">Any string of characters</span></span>|  
|<span data-ttu-id="183f5-123">**?**</span><span class="sxs-lookup"><span data-stu-id="183f5-123">**?**</span></span>|<span data-ttu-id="183f5-124">单个字符</span><span class="sxs-lookup"><span data-stu-id="183f5-124">A single character</span></span>|  
|<span data-ttu-id="183f5-125">**"** *string* **"**</span><span class="sxs-lookup"><span data-stu-id="183f5-125">**"** *string* **"**</span></span>|<span data-ttu-id="183f5-126">文字字符串。</span><span class="sxs-lookup"><span data-stu-id="183f5-126">A literal string of characters.</span></span> <span data-ttu-id="183f5-127">此通配符将与对象名称中的任何子字符串相匹配。</span><span class="sxs-lookup"><span data-stu-id="183f5-127">This wildcard character will match any substring within the object name.</span></span>|  
  
 <span data-ttu-id="183f5-128">**Show system objects**</span><span class="sxs-lookup"><span data-stu-id="183f5-128">**Show system objects**</span></span>  
 <span data-ttu-id="183f5-129">显示“可用对象”下的系统对象。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="183f5-129">Displays system objects under **Available objects**.</span></span> <span data-ttu-id="183f5-130">只有在数据源提供程序显示系统对象时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="183f5-130">This option is available only if the data source provider exposes system objects.</span></span> <span data-ttu-id="183f5-131">从 **“包含的对象”** 列表中删除系统对象时，将自动选择此项。</span><span class="sxs-lookup"><span data-stu-id="183f5-131">Removing a system object from the **Included objects** list automatically selects this option.</span></span>  
  
 <span data-ttu-id="183f5-132">**Add related tables**</span><span class="sxs-lookup"><span data-stu-id="183f5-132">**Add related tables**</span></span>  
 <span data-ttu-id="183f5-133">添加与“包含的对象”下所列表相关的所有表。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="183f5-133">Adds all the tables that are related to those listed under **Included objects**.</span></span> <span data-ttu-id="183f5-134">此选项不能添加视图。</span><span class="sxs-lookup"><span data-stu-id="183f5-134">This option does not add views.</span></span> <span data-ttu-id="183f5-135">不过，此选项可以添加分区表。</span><span class="sxs-lookup"><span data-stu-id="183f5-135">However, this option does add partitioned tables.</span></span> <span data-ttu-id="183f5-136">如果在向导的“名称匹配”页选择名称匹配条件，则此选项还将根据所选条件包括逻辑相关表。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="183f5-136">If you select name-matching criteria on the **Name Matching** page of the wizard, this option also includes logically related tables according to the criteria you select.</span></span> <span data-ttu-id="183f5-137">如果表与新添加的相关表有关，并与原始表具有相同结构，那么也会添加该表。</span><span class="sxs-lookup"><span data-stu-id="183f5-137">Tables are also included if they are related to the newly added related tables, and if they have an identical structure to the original table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="183f5-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="183f5-138">See Also</span></span>  
 <span data-ttu-id="183f5-139">[数据源视图向导的 F1 帮助 &#40;Analysis Services&#41;](data-source-view-wizard-f1-help-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="183f5-139">[Data Source View Wizard F1 Help &#40;Analysis Services&#41;](data-source-view-wizard-f1-help-analysis-services.md) </span></span>  
 [<span data-ttu-id="183f5-140">多维模型中的数据源视图</span><span class="sxs-lookup"><span data-stu-id="183f5-140">Data Source Views in Multidimensional Models</span></span>](multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
