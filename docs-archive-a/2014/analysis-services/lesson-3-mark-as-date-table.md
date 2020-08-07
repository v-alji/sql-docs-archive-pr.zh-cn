---
title: 第4课：标记为日期表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
author: minewiskan
ms.author: owend
ms.openlocfilehash: c3ccc57d770d954e9523196d2393fa9dc2ada5b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588128"
---
# <a name="lesson-4-mark-as-date-table"></a><span data-ttu-id="36373-102">第 4 课：标记为日期表</span><span class="sxs-lookup"><span data-stu-id="36373-102">Lesson 4: Mark as Date Table</span></span>
  <span data-ttu-id="36373-103">在“第 2 课：添加数据”中，您导入了名为 DimDate 的维度表。</span><span class="sxs-lookup"><span data-stu-id="36373-103">In Lesson 2: Add Data, you imported a dimension table named DimDate.</span></span> <span data-ttu-id="36373-104">然后您在“第 3 课：重命名列”中将 DimDate 表重命名为简单的 Date。</span><span class="sxs-lookup"><span data-stu-id="36373-104">You then renamed the DimDate table, in Lesson 3: Rename Columns, to simply, Date.</span></span> <span data-ttu-id="36373-105">虽然在模型中该表已命名为 Date，它也可以称为“日期表”\*\*，该表中包含日期和时间数据。</span><span class="sxs-lookup"><span data-stu-id="36373-105">While in your model this table is now named Date, it can also be known as a *Date table*, in that it contains date and time data.</span></span>  
  
 <span data-ttu-id="36373-106">每当在计算中使用时间智能函数（和稍后创建度量值时所要做的一样），必须指定日期表属性，其中包括“日期表”和该表中的唯一标识符“日期列”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="36373-106">Whenever you use Time Intelligence functions in calculations, as you will do when you create measures a little later, you must specify date table properties, which include a *Date table* and a unique identifier *Date column* in that table.</span></span> <span data-ttu-id="36373-107">您然后可以创建其他表和日期表之间的有效关系，这对于使用 DAX 时间智能函数的计算是必需的。</span><span class="sxs-lookup"><span data-stu-id="36373-107">You can then create valid relationships between other tables and the Date table; necessary for calculations using DAX time intelligence functions.</span></span>  
  
 <span data-ttu-id="36373-108">在本课中，将导入和重命名的 Date 表标记为“日期表”，将 Date 列（Date 表中）标记为“日期列”（唯一标识符）。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="36373-108">In this lesson, you will mark the imported and renamed Date table as the *Date table* and the Date column (in the Date table) as the *Date column* (unique identifier).</span></span> <span data-ttu-id="36373-109">名称日期的所有使用可能会令人感到困惑，但您很快就会明白。</span><span class="sxs-lookup"><span data-stu-id="36373-109">All the use of the name Date can get kind of confusing, but you'll soon get the idea.</span></span>  
  
 <span data-ttu-id="36373-110">学完本课的估计时间： **3 分钟**</span><span class="sxs-lookup"><span data-stu-id="36373-110">Estimated time to complete this lesson: **3 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="36373-111">必备条件</span><span class="sxs-lookup"><span data-stu-id="36373-111">Prerequisites</span></span>  
 <span data-ttu-id="36373-112">本主题是表格建模教程的一部分，应当按顺序完成。</span><span class="sxs-lookup"><span data-stu-id="36373-112">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="36373-113">执行本课中的任务之前，应已完成上一课： [第 3 课：重命名列](rename-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="36373-113">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 3: Rename Columns](rename-columns.md).</span></span>  
  
### <a name="to-set-mark-as-date-table"></a><span data-ttu-id="36373-114">标记为日期表</span><span class="sxs-lookup"><span data-stu-id="36373-114">To set Mark as Date Table</span></span>  
  
1.  <span data-ttu-id="36373-115">在模型设计器中，单击“Date”\*\*\*\* 表（选项卡）。</span><span class="sxs-lookup"><span data-stu-id="36373-115">In the model designer, click the **Date** table (tab).</span></span>  
  
2.  <span data-ttu-id="36373-116">单击 "**表**" 菜单，然后单击 "**日期**"，然后单击 "**标记为日期表**"。</span><span class="sxs-lookup"><span data-stu-id="36373-116">Click the **Table** menu, then click **Date**, and then click **Mark as Date Table**.</span></span>  
  
3.  <span data-ttu-id="36373-117">在“标记为日期表”对话框中，在“Date”列表框中，选择“Date”列作为唯一标识符。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="36373-117">In the **Mark as Date Table** dialog box, in the **Date** listbox, select the **Date** column as the unique identifier.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="36373-118">后续步骤</span><span class="sxs-lookup"><span data-stu-id="36373-118">Next Steps</span></span>  
 <span data-ttu-id="36373-119">若要继续学习本教程，请转到下一课： [第 5 课：创建关系](lesson-4-create-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="36373-119">To continue this tutorial, go to the next lesson: [Lesson 5: Create Relationships](lesson-4-create-relationships.md).</span></span>  
  
  
