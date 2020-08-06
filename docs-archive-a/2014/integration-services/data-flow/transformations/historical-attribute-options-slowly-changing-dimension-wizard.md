---
title: 历史属性选项（渐变维度向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.histattriboption.f1
ms.assetid: a176ec66-ec39-4c99-99d1-c1afa8450e1e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fad005d6b8f80973abeb47dd881ef02b669d7b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589807"
---
# <a name="historical-attribute-options-slowly-changing-dimension-wizard"></a><span data-ttu-id="4dcee-102">历史属性选项（渐变维度向导）</span><span class="sxs-lookup"><span data-stu-id="4dcee-102">Historical Attribute Options (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="4dcee-103">可以使用 **“历史属性选项”** 对话框按开始日期和结束日期显示历史属性，或者将历史属性记录到专门的列中。</span><span class="sxs-lookup"><span data-stu-id="4dcee-103">Use the **Historical Attributes Options** dialog box to show historical attributes by start and end dates, or to record historical attributes in a column specially created for this purpose.</span></span>  
  
 <span data-ttu-id="4dcee-104">若要了解有关此向导的详细信息，请参阅 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="4dcee-104">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="4dcee-105">选项</span><span class="sxs-lookup"><span data-stu-id="4dcee-105">Options</span></span>  
 <span data-ttu-id="4dcee-106">**使用单独的列显示当前和过期记录**</span><span class="sxs-lookup"><span data-stu-id="4dcee-106">**Use a single column to show current and expired records**</span></span>  
 <span data-ttu-id="4dcee-107">如果您选择使用单独的列来记录历史属性的状态，则下列选项可用：</span><span class="sxs-lookup"><span data-stu-id="4dcee-107">If you choose to use a single column to record the status of historical attributes, the following options are available:</span></span>  
  
|<span data-ttu-id="4dcee-108">选项</span><span class="sxs-lookup"><span data-stu-id="4dcee-108">Option</span></span>|<span data-ttu-id="4dcee-109">说明</span><span class="sxs-lookup"><span data-stu-id="4dcee-109">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4dcee-110">**指示当前记录的列**</span><span class="sxs-lookup"><span data-stu-id="4dcee-110">**Column to indicate current record**</span></span>|<span data-ttu-id="4dcee-111">选择一个要在其中指示当前记录的列。</span><span class="sxs-lookup"><span data-stu-id="4dcee-111">Select a column in which to indicate the current record.</span></span>|  
|<span data-ttu-id="4dcee-112">**表示当前记录的值**</span><span class="sxs-lookup"><span data-stu-id="4dcee-112">**Value when current**</span></span>|<span data-ttu-id="4dcee-113">使用 **True** 或 **“当前”** 来显示该记录是否为当前记录。</span><span class="sxs-lookup"><span data-stu-id="4dcee-113">Use either **True** or **Current** to show whether the record is current.</span></span>|  
|<span data-ttu-id="4dcee-114">**表示过期记录的值**</span><span class="sxs-lookup"><span data-stu-id="4dcee-114">**Expiration value**</span></span>|<span data-ttu-id="4dcee-115">使用 **False** 或 **“过期”** 来显示该记录是否为历史值。</span><span class="sxs-lookup"><span data-stu-id="4dcee-115">Use either **False** or **Expired** to show whether the record is a historical value.</span></span>|  
  
 <span data-ttu-id="4dcee-116">**使用开始日期和结束日期确定当前记录和过期记录**</span><span class="sxs-lookup"><span data-stu-id="4dcee-116">**Use start and end dates to identify current and expired records**</span></span>  
 <span data-ttu-id="4dcee-117">此选项的维度表必须包括一个日期列。</span><span class="sxs-lookup"><span data-stu-id="4dcee-117">The dimension table for this option must include a date column.</span></span> <span data-ttu-id="4dcee-118">如果您选择按开始日期和结束日期显示历史属性，则下列选项可用：</span><span class="sxs-lookup"><span data-stu-id="4dcee-118">If you choose to show historical attributes by start and end dates, the following options are available:</span></span>  
  
|<span data-ttu-id="4dcee-119">选项</span><span class="sxs-lookup"><span data-stu-id="4dcee-119">Option</span></span>|<span data-ttu-id="4dcee-120">说明</span><span class="sxs-lookup"><span data-stu-id="4dcee-120">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4dcee-121">**开始日期列**</span><span class="sxs-lookup"><span data-stu-id="4dcee-121">**Start date column**</span></span>|<span data-ttu-id="4dcee-122">在维度表中选择要包含开始日期的列。</span><span class="sxs-lookup"><span data-stu-id="4dcee-122">Select the column in the dimension table to contain the start date.</span></span>|  
|<span data-ttu-id="4dcee-123">**结束日期列**</span><span class="sxs-lookup"><span data-stu-id="4dcee-123">**End date column**</span></span>|<span data-ttu-id="4dcee-124">在维度表中选择要包含结束日期的列。</span><span class="sxs-lookup"><span data-stu-id="4dcee-124">Select the column in the dimension table to contain the end date.</span></span>|  
|<span data-ttu-id="4dcee-125">**用来设置日期值的变量**</span><span class="sxs-lookup"><span data-stu-id="4dcee-125">**Variable to set date values**</span></span>|<span data-ttu-id="4dcee-126">从该列表中选择日期变量。</span><span class="sxs-lookup"><span data-stu-id="4dcee-126">Select a date variable from the list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4dcee-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4dcee-127">See Also</span></span>  
 [<span data-ttu-id="4dcee-128">使用渐变维度向导配置输出</span><span class="sxs-lookup"><span data-stu-id="4dcee-128">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
