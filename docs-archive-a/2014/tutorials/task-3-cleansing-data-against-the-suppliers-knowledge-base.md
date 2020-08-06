---
title: 任务3：针对供应商知识库清理数据 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 647c924a-9b91-4294-8d96-e81416e4e90e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 13201a8b904a5fc5232b9fa860710e4e39cce67a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691366"
---
# <a name="task-3-cleansing-data-against-the-suppliers-knowledge-base"></a><span data-ttu-id="2c474-102">任务 3：对照 Suppliers 知识库清理数据</span><span class="sxs-lookup"><span data-stu-id="2c474-102">Task 3: Cleansing Data against the Suppliers Knowledge Base</span></span>
  <span data-ttu-id="2c474-103">在本任务中，您将运行计算机辅助的清理过程。</span><span class="sxs-lookup"><span data-stu-id="2c474-103">In this task, you run the computer-assisted cleansing process.</span></span> <span data-ttu-id="2c474-104">DQS 基于指定的域值，使用高级算法和置信度来针对所选知识库分析数据，然后清理数据。</span><span class="sxs-lookup"><span data-stu-id="2c474-104">DQS uses advanced algorithms and confidence levels based on the threshold values specified to analyze the data against the selected knowledge base, and then cleanse it.</span></span> <span data-ttu-id="2c474-105">有关更多详细信息，请参阅[使用 DQS (内部) 知识清理数据](https://msdn.microsoft.com/library/hh213061.aspx)。</span><span class="sxs-lookup"><span data-stu-id="2c474-105">See [Cleansing Data Using DQS (Internal) Knowledge](https://msdn.microsoft.com/library/hh213061.aspx) for more details.</span></span>

1.  <span data-ttu-id="2c474-106">单击 "**启动**" 以启动计算机辅助清理过程。</span><span class="sxs-lookup"><span data-stu-id="2c474-106">Click **Start** to start the computer-assisted cleansing process.</span></span>

     <span data-ttu-id="2c474-107">![清理过程的“清理”页](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-01.jpg "清理过程的“清理”页")</span><span class="sxs-lookup"><span data-stu-id="2c474-107">![Cleanse Page of the Cleansing Process](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-01.jpg "Cleanse Page of the Cleansing Process")</span></span>

2.  <span data-ttu-id="2c474-108">清理过程完成后，请在 "**探查器**" 选项卡中查看**统计信息**。源统计信息提供已处理的记录数、找到的正确记录数、DQS 更正的记录数、DQS 建议的更改记录数，以及无效的记录数。</span><span class="sxs-lookup"><span data-stu-id="2c474-108">When the cleansing process is completed, review **statistics** in the **Profiler** tab. The Source Statistics provide the number of records processed, number of records that are found to be correct, number of records that DQS corrects, number of records that have changes suggested by DQS, and the number of records that are invalid.</span></span> <span data-ttu-id="2c474-109">在右侧的列表框中，您可以看到清理过程中涉及的每个域的已更正的值、建议的值和值的完成度（提供数据的程度）和准确性（数据可用于目标用途的程度）。</span><span class="sxs-lookup"><span data-stu-id="2c474-109">In the list box to the right, you can see the corrected values, suggested values, and the completeness (the extent to which the data is present) and accuracy (the extent to which the data can be used for intended purposes) of values for each domain involved in the cleansing process.</span></span>

     <span data-ttu-id="2c474-110">![清理结果](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-02.jpg "清理结果")</span><span class="sxs-lookup"><span data-stu-id="2c474-110">![Cleansing Results](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-02.jpg "Cleansing Results")</span></span>

3.  <span data-ttu-id="2c474-111">单击 "**下一步**" 切换到 "**管理和查看结果**" 页。</span><span class="sxs-lookup"><span data-stu-id="2c474-111">Click **Next** to switch to **Manage and View Results** page.</span></span>

## <a name="next-step"></a><span data-ttu-id="2c474-112">下一步</span><span class="sxs-lookup"><span data-stu-id="2c474-112">Next Step</span></span>
 [<span data-ttu-id="2c474-113">任务 4：管理和查看报表</span><span class="sxs-lookup"><span data-stu-id="2c474-113">Task 4: Manaing and Viewing Results</span></span>](../../2014/tutorials/task-4-manaing-and-viewing-results.md)


