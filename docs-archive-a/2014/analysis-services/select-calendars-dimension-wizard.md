---
title: 选择日历 (维度向导) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.serverSpecialCalendars.f1
ms.assetid: 6e28a020-2586-4b13-9333-b499fb1b33af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2048ee20dd91c942f01982d02f3265a6bad670dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587621"
---
# <a name="select-calendars-dimension-wizard"></a><span data-ttu-id="b737c-102">选择日历（维度向导）</span><span class="sxs-lookup"><span data-stu-id="b737c-102">Select Calendars (Dimension Wizard)</span></span>
  <span data-ttu-id="b737c-103">可以使用“选择日历”\*\*\*\* 页，为时间维度创建表示会计、报表、生产或国际标准化组织 (ISO) 8601 日历的其他层次结构。</span><span class="sxs-lookup"><span data-stu-id="b737c-103">Use the **Select Calendars** page to create additional hierarchies representing fiscal, reporting, manufacturing, or International Standards Organization (ISO) 8601 calendars for the time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b737c-104"> 只有在 **“选择维度类型”** 页上选择 **“服务器时间维度”** ，或者在 **“维度定义”** 页上选择 **“不使用数据源生成维度”** 并在 **“选择维度类型”** 页上选择 **“时间维度”** 时，才会显示此页。</span><span class="sxs-lookup"><span data-stu-id="b737c-104">This page will appear only if you have selected **Server time dimension** on the **Select the Dimension Type** page, or if you selected **Build the dimension without using a data source** on the **Dimension Definition** page and selected **Time dimension** on the **Select the Dimension Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b737c-105">选项</span><span class="sxs-lookup"><span data-stu-id="b737c-105">Options</span></span>  
 <span data-ttu-id="b737c-106">**会计日历**</span><span class="sxs-lookup"><span data-stu-id="b737c-106">**Fiscal calendar**</span></span>  
 <span data-ttu-id="b737c-107">选择此选项可以基于会计日历创建时间层次结构。</span><span class="sxs-lookup"><span data-stu-id="b737c-107">Select to create a time hierarchy based on a fiscal calendar.</span></span>  
  
 <span data-ttu-id="b737c-108">**起始日和月份**</span><span class="sxs-lookup"><span data-stu-id="b737c-108">**Start day and month**</span></span>  
 <span data-ttu-id="b737c-109">选择会计日历开始的日期和月份。</span><span class="sxs-lookup"><span data-stu-id="b737c-109">Select the day and month on which the fiscal calendar begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b737c-110"> 只有在选择了 **“会计日历”** 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="b737c-110">This option is available only when **Fiscal calendar** is selected.</span></span>  
  
 <span data-ttu-id="b737c-111">**会计日历命名约定**</span><span class="sxs-lookup"><span data-stu-id="b737c-111">**Fiscal calendar naming convention**</span></span>  
 <span data-ttu-id="b737c-112">选择会计日历使用的命名约定。</span><span class="sxs-lookup"><span data-stu-id="b737c-112">Select the naming convention used by the fiscal calendar.</span></span> <span data-ttu-id="b737c-113">选择“日历年名称”\*\*\*\* 或“日历年名称 + 1”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b737c-113">Select either **Calendar year name** or **Calendar year name +1**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b737c-114"> 只有在选择了 **“会计日历”** 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="b737c-114">This option is available only when **Fiscal calendar** is selected.</span></span>  
  
 <span data-ttu-id="b737c-115">**报表(或营销)日历**</span><span class="sxs-lookup"><span data-stu-id="b737c-115">**Reporting (or marketing) calendar**</span></span>  
 <span data-ttu-id="b737c-116">选择此项可以基于报表日历创建时间层次结构。</span><span class="sxs-lookup"><span data-stu-id="b737c-116">Select to create a time hierarchy based on a reporting calendar.</span></span>  
  
 <span data-ttu-id="b737c-117">**起始周和月份**</span><span class="sxs-lookup"><span data-stu-id="b737c-117">**Start week and month**</span></span>  
 <span data-ttu-id="b737c-118">选择报表日历开始的周和月份。</span><span class="sxs-lookup"><span data-stu-id="b737c-118">Select the week and month on which the reporting calendar begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b737c-119">只有在选择了“报表(或营销)日历”\*\*\*\* 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="b737c-119">This option is available when **Reporting (or marketing) calendar** is selected.</span></span>  
  
 <span data-ttu-id="b737c-120">**月份周别模式**</span><span class="sxs-lookup"><span data-stu-id="b737c-120">**Week by month pattern**</span></span>  
 <span data-ttu-id="b737c-121">选择报表日历使用的月份周别模式。</span><span class="sxs-lookup"><span data-stu-id="b737c-121">Select the week by month pattern used by the reporting calendar.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b737c-122">只有在选择了“报表(或营销)日历”\*\*\*\* 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="b737c-122">This option is available when **Reporting (or marketing) calendar** is selected.</span></span>  
  
 <span data-ttu-id="b737c-123">下表列出了月份周别模式可用的选项：</span><span class="sxs-lookup"><span data-stu-id="b737c-123">The following table lists the options available for the week by month pattern.</span></span>  
  
|<span data-ttu-id="b737c-124">值</span><span class="sxs-lookup"><span data-stu-id="b737c-124">Value</span></span>|<span data-ttu-id="b737c-125">说明</span><span class="sxs-lookup"><span data-stu-id="b737c-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b737c-126">**Week 445**</span><span class="sxs-lookup"><span data-stu-id="b737c-126">**Week 445**</span></span>|<span data-ttu-id="b737c-127">季度的第一个月有 4 周，第二个月有 4 周，第三个月有 5 周。</span><span class="sxs-lookup"><span data-stu-id="b737c-127">The first month in the quarter has 4 weeks, the second month in the quarter has 4 weeks, and the third month in the quarter has 5 weeks.</span></span>|  
|<span data-ttu-id="b737c-128">**Week 454**</span><span class="sxs-lookup"><span data-stu-id="b737c-128">**Week 454**</span></span>|<span data-ttu-id="b737c-129">季度的第一个月有 4 周，第二个月有 5 周，第三个月有 4 周。</span><span class="sxs-lookup"><span data-stu-id="b737c-129">The first month in the quarter has 4 weeks, the second month in the quarter has 5 weeks, and the third month in the quarter has 4 weeks.</span></span>|  
|<span data-ttu-id="b737c-130">**周 544**</span><span class="sxs-lookup"><span data-stu-id="b737c-130">**Week 544**</span></span>|<span data-ttu-id="b737c-131">季度的第一个月有 5 周，第二个月有 4 周，第三个月有 4 周。</span><span class="sxs-lookup"><span data-stu-id="b737c-131">The first month in the quarter has 5 weeks, the second month in the quarter has 4 weeks, and the third month in the quarter has 4 weeks.</span></span>|  
  
 <span data-ttu-id="b737c-132">**生产日历**</span><span class="sxs-lookup"><span data-stu-id="b737c-132">**Manufacturing calendar**</span></span>  
 <span data-ttu-id="b737c-133">选择此项可以基于生产日历创建时间层次结构。</span><span class="sxs-lookup"><span data-stu-id="b737c-133">Select to create a time hierarchy based on a manufacturing calendar.</span></span>  
  
 <span data-ttu-id="b737c-134">**起始周和月份**</span><span class="sxs-lookup"><span data-stu-id="b737c-134">**Start week and month**</span></span>  
 <span data-ttu-id="b737c-135">选择生产日历开始的周和月份。</span><span class="sxs-lookup"><span data-stu-id="b737c-135">Select the week and month on which the manufacturing calendar begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b737c-136"> 只有在选择了 **“生产日历”** 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="b737c-136">This option is available when **Manufacturing calendar** is selected.</span></span>  
  
 <span data-ttu-id="b737c-137">**包含附加期间的季度**</span><span class="sxs-lookup"><span data-stu-id="b737c-137">**Quarter with extra periods**</span></span>  
 <span data-ttu-id="b737c-138">选择或键入将包含附加期间的季度。</span><span class="sxs-lookup"><span data-stu-id="b737c-138">Select or type the quarter that will contain the extra periods.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b737c-139"> 只有在选择了 **“生产日历”** 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="b737c-139">This option is available when **Manufacturing calendar** is selected.</span></span>  
  
 <span data-ttu-id="b737c-140">**ISO 8601 日历**</span><span class="sxs-lookup"><span data-stu-id="b737c-140">**ISO 8601 calendar**</span></span>  
 <span data-ttu-id="b737c-141">选择此项可以基于 ISO 8601 日历创建层次结构。</span><span class="sxs-lookup"><span data-stu-id="b737c-141">Select to create a hierarchy based on the ISO 8601 calendar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b737c-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b737c-142">See Also</span></span>  
 <span data-ttu-id="b737c-143">[维度向导的 F1 帮助](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="b737c-143">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="b737c-144">[Analysis Services 多维数据 &#40;维度&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b737c-144">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="b737c-145">多维模型中的维度</span><span class="sxs-lookup"><span data-stu-id="b737c-145">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
