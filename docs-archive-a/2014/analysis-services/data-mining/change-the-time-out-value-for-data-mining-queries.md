---
title: 更改数据挖掘查询的超时值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time-out
ms.assetid: f1add4bc-e882-440a-a98b-333cfa274c3e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9dcdcdcbb6e2aef48dd8725f10f38180c73f5f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588160"
---
# <a name="change-the-time-out-value-for-data-mining-queries"></a><span data-ttu-id="fc649-102">更改数据挖掘查询的超时值</span><span class="sxs-lookup"><span data-stu-id="fc649-102">Change the Time-out Value for Data Mining Queries</span></span>
  <span data-ttu-id="fc649-103">在生成提升图或执行预测查询时，生成预测所需的所有数据有时可能需要很长时间。</span><span class="sxs-lookup"><span data-stu-id="fc649-103">When you build a lift chart or execute a prediction query, sometimes it can take a long time to generate all the data required for the prediction.</span></span> <span data-ttu-id="fc649-104">为防止查询超时，您可以更改控制 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器要等待完成查询的时间值。</span><span class="sxs-lookup"><span data-stu-id="fc649-104">To prevent the query from timing out, you can change the value that controls how long the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server waits to complete a query.</span></span>  
  
 <span data-ttu-id="fc649-105">默认值为 15；不过，如果您的模型比较复杂或者数据源较大，此值可能不够。</span><span class="sxs-lookup"><span data-stu-id="fc649-105">The default value is 15; however, if your models are complex or the data source is large, this might not be enough.</span></span> <span data-ttu-id="fc649-106">如果必要，可以大幅增大该值，以便有足够的时间进行处理。</span><span class="sxs-lookup"><span data-stu-id="fc649-106">If necessary, you can increase the value significantly, to enable enough time for processing.</span></span> <span data-ttu-id="fc649-107">例如，如果将 **“查询超时值”** 设置为 600，则查询可以持续运行 10 分钟之久。</span><span class="sxs-lookup"><span data-stu-id="fc649-107">For example, if you set **Query Timeout** to 600, the query could continue to run for up to 10 minutes.</span></span>  
  
 <span data-ttu-id="fc649-108">有关预测查询的详细信息，请参阅 [数据挖掘查询任务和操作指南](data-mining-query-tasks-and-how-tos.md)。</span><span class="sxs-lookup"><span data-stu-id="fc649-108">For more information about prediction queries, see [Data Mining Query Tasks and How-tos](data-mining-query-tasks-and-how-tos.md).</span></span>  
  
### <a name="configure-the-time-out-value-for-data-mining-queries"></a><span data-ttu-id="fc649-109">配置数据挖掘查询的超时值</span><span class="sxs-lookup"><span data-stu-id="fc649-109">Configure the time-out value for data mining queries</span></span>  
  
1.  <span data-ttu-id="fc649-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，从 **“工具”** 菜单中选择 **“选项”**。</span><span class="sxs-lookup"><span data-stu-id="fc649-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], from the **Tools** menu, selection **Options**.</span></span>  
  
2.  <span data-ttu-id="fc649-111">在 **“选项”** 窗格中，展开 **“商业智能设计器”**。</span><span class="sxs-lookup"><span data-stu-id="fc649-111">In the **Options** pane, expand **Business Intelligence Designers**.</span></span>  
  
3.  <span data-ttu-id="fc649-112">单击 **“查询超时值”** 文本框，然后键入一个秒数值。</span><span class="sxs-lookup"><span data-stu-id="fc649-112">Click the **Query Timeout** text box, and type a value for the number of seconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc649-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc649-113">See Also</span></span>  
 <span data-ttu-id="fc649-114">[数据挖掘查询任务和操作指南](data-mining-query-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="fc649-114">[Data Mining Query Tasks and How-tos](data-mining-query-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="fc649-115">数据挖掘查询</span><span class="sxs-lookup"><span data-stu-id="fc649-115">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
