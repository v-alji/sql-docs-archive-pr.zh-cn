---
title: 定义 (维度向导) 的时间段 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.timefrequency.f1
ms.assetid: 6bda6b7e-d306-4e68-9acb-84de8f44d1b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 88b69eaa265b7a98f7d32063b602897d02016fa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590428"
---
# <a name="define-time-periods-dimension-wizard"></a><span data-ttu-id="d56ff-102">定义时间段（维度向导）</span><span class="sxs-lookup"><span data-stu-id="d56ff-102">Define Time Periods (Dimension Wizard)</span></span>
  <span data-ttu-id="d56ff-103">可以使用 **“定义时间段”** 页，定义要包含在时间维度或服务器时间维度中的日历年信息和时间频率。</span><span class="sxs-lookup"><span data-stu-id="d56ff-103">Use the **Define Time Periods** page to define the calendar year information and time frequencies to include in the time dimension or server time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d56ff-104"> 只有在 **“选择维度类型”** 页上选择 **“服务器时间维度”** ，或者在 **“选择生成方法”** 页上选择 **“不使用数据源生成维度”** 并在 **“选择维度类型”** 页上选择 **“时间维度”** 时，才会显示此页。</span><span class="sxs-lookup"><span data-stu-id="d56ff-104">This page will appear only if you have selected **Server time dimension** on the **Select the Dimension Type** page, or if you selected **Build the dimension without using a data source** on the **Select Build Method** page and selected **Time dimension** on the **Select the Dimension Type** page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d56ff-105">此页用于定义时间维度的日历年。</span><span class="sxs-lookup"><span data-stu-id="d56ff-105">This page is for defining the calendar year of a time dimension.</span></span> <span data-ttu-id="d56ff-106">若要定义时间维度的会计年度、生产年度、报表年度或国际标准化组织 (ISO) 8601 年，请使用“选择日历”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="d56ff-106">To define a fiscal, manufacturing, reporting, or International Standards Organization (ISO) 8601 year for the time dimension, use the **Select Calendars** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d56ff-107">选项</span><span class="sxs-lookup"><span data-stu-id="d56ff-107">Options</span></span>  
 <span data-ttu-id="d56ff-108">**第一个日历日**</span><span class="sxs-lookup"><span data-stu-id="d56ff-108">**First calendar day**</span></span>  
 <span data-ttu-id="d56ff-109">键入或选择当前年份的起始日期。</span><span class="sxs-lookup"><span data-stu-id="d56ff-109">Type or select the day that begins the current year.</span></span>  
  
 <span data-ttu-id="d56ff-110">**最后一个日历日**</span><span class="sxs-lookup"><span data-stu-id="d56ff-110">**Last calendar day**</span></span>  
 <span data-ttu-id="d56ff-111">键入或选择当前年份的结束日期。</span><span class="sxs-lookup"><span data-stu-id="d56ff-111">Type or select the day that ends the current year.</span></span>  
  
 <span data-ttu-id="d56ff-112">**每周第一天**</span><span class="sxs-lookup"><span data-stu-id="d56ff-112">**First day of the week**</span></span>  
 <span data-ttu-id="d56ff-113">选择每周从星期几开始。</span><span class="sxs-lookup"><span data-stu-id="d56ff-113">Select the day that begins a week.</span></span>  
  
 <span data-ttu-id="d56ff-114">**时间段**</span><span class="sxs-lookup"><span data-stu-id="d56ff-114">**Time periods**</span></span>  
 <span data-ttu-id="d56ff-115">为时间维度的日历年选择时间段。</span><span class="sxs-lookup"><span data-stu-id="d56ff-115">Select the time periods for the calendar year of the time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d56ff-116">`Date` 时间段是必需的。</span><span class="sxs-lookup"><span data-stu-id="d56ff-116">The `Date` time period is required.</span></span>  
  
 <span data-ttu-id="d56ff-117">**时间成员名称所用的语言**</span><span class="sxs-lookup"><span data-stu-id="d56ff-117">**Language for time member names**</span></span>  
 <span data-ttu-id="d56ff-118">选择时间维度中的成员所用的语言。</span><span class="sxs-lookup"><span data-stu-id="d56ff-118">Select the language for the members in the time dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d56ff-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d56ff-119">See Also</span></span>  
 <span data-ttu-id="d56ff-120">[维度向导的 F1 帮助](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="d56ff-120">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="d56ff-121">[Analysis Services 多维数据 &#40;维度&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d56ff-121">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="d56ff-122">[多维模型中的维度](multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="d56ff-122">[Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="d56ff-123">&#40;维度向导选择日历&#41;</span><span class="sxs-lookup"><span data-stu-id="d56ff-123">Select Calendars &#40;Dimension Wizard&#41;</span></span>](select-calendars-dimension-wizard.md)  
  
  
