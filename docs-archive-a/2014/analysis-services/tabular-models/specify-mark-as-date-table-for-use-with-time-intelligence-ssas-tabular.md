---
title: 指定 "标记为日期表" 以便用于时间智能 (SSAS 表格) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 30841d1f-0c3b-4575-8f4a-27a1492e248c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 81038369b8cb8636a2aa216f1c26783a96d5f7ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682390"
---
# <a name="specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular"></a><span data-ttu-id="c0b0a-102">指定“标记为日期表”以便用于时间智能（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="c0b0a-102">Specify Mark as Date Table for use with Time Intelligence (SSAS Tabular)</span></span>
  <span data-ttu-id="c0b0a-103">要在 DAX 公式中使用时间智能函数，必须指定一个日期表和一个数据类型为 Date 的唯一标识符 (datetime) 列。</span><span class="sxs-lookup"><span data-stu-id="c0b0a-103">In order to use time intelligence functions in DAX formulas, you must specify a date table and a unique identifier (datetime) column of the Date data type.</span></span> <span data-ttu-id="c0b0a-104">将日期表中的某列指定为唯一标识符后，您可以在日期表中各列与任何事实数据表之间创建关系。</span><span class="sxs-lookup"><span data-stu-id="c0b0a-104">Once a column in the date table is specified as a unique identifier, you can create relationships between columns in the date table and any fact tables.</span></span>  
  
 <span data-ttu-id="c0b0a-105">使用时间智能函数时，下列规则适用：</span><span class="sxs-lookup"><span data-stu-id="c0b0a-105">When using time intelligence functions, the following rules apply:</span></span>  
  
-   <span data-ttu-id="c0b0a-106">使用 DAX 时间智能函数时，绝不要从事实数据表中指定 datetime 列。</span><span class="sxs-lookup"><span data-stu-id="c0b0a-106">When using DAX time intelligence functions, never specify a datetime column from a fact table.</span></span> <span data-ttu-id="c0b0a-107">在您的模型中，始终使用至少一个数据类型为 Date 的 datetime 列和唯一值来创建单独的日期表。</span><span class="sxs-lookup"><span data-stu-id="c0b0a-107">Always create a separate date table in your model with at least one datetime column of Date data type and with unique values.</span></span>  
  
-   <span data-ttu-id="c0b0a-108">请确保您的日期表具有一个连续的日期范围。</span><span class="sxs-lookup"><span data-stu-id="c0b0a-108">Make sure your date table has a continuous date range.</span></span>  
  
-   <span data-ttu-id="c0b0a-109">日期表中的 datetime 列应该以天为粒度（不应包含不足一天）。</span><span class="sxs-lookup"><span data-stu-id="c0b0a-109">The datetime column in the date table should be at day granularity (without fractions of a day).</span></span>  
  
-   <span data-ttu-id="c0b0a-110">必须使用 **“标记日期表”** 对话框指定一个日期表和一个唯一标识符列。</span><span class="sxs-lookup"><span data-stu-id="c0b0a-110">You must specify a date table and a unique identifier column by using the **Mark the Date Table** dialog box.</span></span>  
  
-   <span data-ttu-id="c0b0a-111">在事实数据表与日期表中数据类型为 Date 的列之间创建关系。</span><span class="sxs-lookup"><span data-stu-id="c0b0a-111">Create relationships between fact tables and columns of Date data type in the date table.</span></span>  
  
#### <a name="to-specify-a-date-table-and-unique-identifier"></a><span data-ttu-id="c0b0a-112">指定日期表和唯一标识符</span><span class="sxs-lookup"><span data-stu-id="c0b0a-112">To specify a date table and unique identifier</span></span>  
  
1.  <span data-ttu-id="c0b0a-113">在模型设计器中，单击日期表。</span><span class="sxs-lookup"><span data-stu-id="c0b0a-113">In the model designer, click the date table.</span></span>  
  
2.  <span data-ttu-id="c0b0a-114">单击 **“表”** 菜单，然后依次单击 **“日期”** 和 **Mark as “日期” “表”**。</span><span class="sxs-lookup"><span data-stu-id="c0b0a-114">Click the **Table** menu, then click **Date**, and then click **Mark as Date Table**</span></span>  
  
3.  <span data-ttu-id="c0b0a-115">在 **“标记日期表”** 对话框的 **“日期”** 列表框中，选择要用作唯一标识符的列。</span><span class="sxs-lookup"><span data-stu-id="c0b0a-115">In the **Mark as Date Table** dialog box, in the **Date** listbox, select a column to be used as a unique identifier.</span></span> <span data-ttu-id="c0b0a-116">此列必须包含唯一值，并且数据类型应为 Date。</span><span class="sxs-lookup"><span data-stu-id="c0b0a-116">This column must contain unique values and should be of Date data type.</span></span> <span data-ttu-id="c0b0a-117">例如：</span><span class="sxs-lookup"><span data-stu-id="c0b0a-117">For example:</span></span>  
  
    |<span data-ttu-id="c0b0a-118">Date</span><span class="sxs-lookup"><span data-stu-id="c0b0a-118">Date</span></span>|  
    |----------|  
    |<span data-ttu-id="c0b0a-119">7/1/2010 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="c0b0a-119">7/1/2010 12:00:00 AM</span></span>|  
    |<span data-ttu-id="c0b0a-120">7/2/2010 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="c0b0a-120">7/2/2010 12:00:00 AM</span></span>|  
    |<span data-ttu-id="c0b0a-121">7/3/2010 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="c0b0a-121">7/3/2010 12:00:00 AM</span></span>|  
    |<span data-ttu-id="c0b0a-122">7/4/2010 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="c0b0a-122">7/4/2010 12:00:00 AM</span></span>|  
    |<span data-ttu-id="c0b0a-123">7/5/2010 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="c0b0a-123">7/5/2010 12:00:00 AM</span></span>|  
  
4.  <span data-ttu-id="c0b0a-124">根据需要在事实数据表和日期表之间创建任何关系。</span><span class="sxs-lookup"><span data-stu-id="c0b0a-124">If necessary, create any relationships between fact tables and the date table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0b0a-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0b0a-125">See Also</span></span>  
 <span data-ttu-id="c0b0a-126">[&#40;SSAS 表格&#41;计算](calculations-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="c0b0a-126">[Calculations &#40;SSAS Tabular&#41;](calculations-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="c0b0a-127">&#40;DAX 的时间智能函数&#41;</span><span class="sxs-lookup"><span data-stu-id="c0b0a-127">Time Intelligence Functions &#40;DAX&#41;</span></span>](/dax/time-intelligence-functions-dax)  
  
  
