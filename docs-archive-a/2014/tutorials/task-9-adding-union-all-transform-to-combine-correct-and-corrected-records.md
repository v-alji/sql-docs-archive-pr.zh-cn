---
title: 任务9：添加 Union All 转换以合并正确和已更正的记录 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 24ba466d-a7d3-49e7-9111-b348399c9e58
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 83afb5ea9367660048fe36d00ab59d808da17b81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694179"
---
# <a name="task-9-adding-union-all-transform-to-combine-correct-and-corrected-records"></a><span data-ttu-id="dccdd-102">任务 9：添加 Union All 转换以合并正确和已更正的记录</span><span class="sxs-lookup"><span data-stu-id="dccdd-102">Task 9: Adding Union All Transform to Combine Correct and Corrected Records</span></span>
  <span data-ttu-id="dccdd-103">在本任务中，您将向数据流添加 Union All 转换。</span><span class="sxs-lookup"><span data-stu-id="dccdd-103">In this task, you add the Union All Transform to the data flow.</span></span> <span data-ttu-id="dccdd-104">Union All 转换将多个输入组合到一个输出中。</span><span class="sxs-lookup"><span data-stu-id="dccdd-104">The Union All transformation combines multiple inputs into one output.</span></span> <span data-ttu-id="dccdd-105">在您的方案中，它将正确记录和已更正的记录合并到一个流中。</span><span class="sxs-lookup"><span data-stu-id="dccdd-105">In your scenario, it combine both Correct and Corrected records into one stream.</span></span>  
  
1.  <span data-ttu-id="dccdd-106">将 " **SSIS 工具箱**" 的 "**通用**" 部分中的 "**合并所有**转换" 拖放到 "**数据流" 选项**卡，然后在 "**选择正确和已更正的记录**" 下放置。</span><span class="sxs-lookup"><span data-stu-id="dccdd-106">Drag-drop **Union All** Transform from **Common** section of the **SSIS Toolbox** to the **Data Flow** tab and place it under **Pick Correct and Corrected Records**.</span></span>  
  
2.  <span data-ttu-id="dccdd-107">右键**单击 "数据流**" 选项卡中的 " **Union All**转换"，然后单击 "**重命名**"。</span><span class="sxs-lookup"><span data-stu-id="dccdd-107">Right-click **Union All** Transform in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="dccdd-108">键入 "**合并正确和已更正的记录**"，然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="dccdd-108">Type **Combine Correct and Corrected Records**, and press **ENTER**.</span></span>  
  
     <span data-ttu-id="dccdd-109">![合并正确和已更正的记录](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "合并正确和已更正的记录")</span><span class="sxs-lookup"><span data-stu-id="dccdd-109">![Combine Correct and Corrected Reocrds](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "Combine Correct and Corrected Reocrds")</span></span>  
  
3.  <span data-ttu-id="dccdd-110">"连接"**选择正确和已更正的记录**，以便在 "**数据流" 选项卡**中使用蓝色连接器**合并正确和更正的记录**。</span><span class="sxs-lookup"><span data-stu-id="dccdd-110">Connect **Pick Correct and Corrected Records** to **Combine Correct and Corrected Records** in the **Data Flow** tab by using the blue connector.</span></span> <span data-ttu-id="dccdd-111">应会看到 "**输入输出选择**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="dccdd-111">You should see the **Input Output Selection** dialog box.</span></span>  
  
4.  <span data-ttu-id="dccdd-112">在 "**输入输出**" 对话框中，为 "**输出**" 选择 "**正确**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="dccdd-112">In the **Input Output** dialog box, select **Correct** for **Output** and click **OK**.</span></span>  
  
     <span data-ttu-id="dccdd-113">![“选择输入输出”对话框](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "“选择输入输出”对话框")</span><span class="sxs-lookup"><span data-stu-id="dccdd-113">![Input Output Selection Dialog Box](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "Input Output Selection Dialog Box")</span></span>  
  
5.  <span data-ttu-id="dccdd-114">将标题为 "**正确**" 的连接线拖放到左侧的连接符末尾处。</span><span class="sxs-lookup"><span data-stu-id="dccdd-114">Move the connector titled **Correct** to the left by dragging and dropping the dot at the end of the connector to left.</span></span>  
  
     <span data-ttu-id="dccdd-115">![连接正确的以合并正确和已更正的记录](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "连接正确的以合并正确和已更正的记录")</span><span class="sxs-lookup"><span data-stu-id="dccdd-115">![Connect Correct to Combine Correct and Corrected](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "Connect Correct to Combine Correct and Corrected")</span></span>  
  
6.  <span data-ttu-id="dccdd-116">如果选择 "选择**正确和已更正的记录**" 转换，应会看到另一个蓝色连接器。</span><span class="sxs-lookup"><span data-stu-id="dccdd-116">If you select **Pick Correct and Corrected Records** transform, you should see another blue connector.</span></span> <span data-ttu-id="dccdd-117">拖动该蓝色连接器以**合并正确和已更正的记录**。</span><span class="sxs-lookup"><span data-stu-id="dccdd-117">Drag that blue connector to **Combine Correct and Corrected Records**.</span></span>  
  
     <span data-ttu-id="dccdd-118">![连接已更正的以合并正确和已更正的记录](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "连接已更正的以合并正确和已更正的记录")</span><span class="sxs-lookup"><span data-stu-id="dccdd-118">![Connect Corrected to Combine Correct and Corrected](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "Connect Corrected to Combine Correct and Corrected")</span></span>  
  
7.  <span data-ttu-id="dccdd-119">应**更正**此**连接器**的标题。</span><span class="sxs-lookup"><span data-stu-id="dccdd-119">This **connector** should be titled **Corrected**.</span></span> <span data-ttu-id="dccdd-120">由于只有两个条件是**正确**的并且已**更正**，并且已经使用了一个条件，此时不会显示 "**输入输出选择**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="dccdd-120">Since you have only two conditions **Correct** and **Corrected**, and one condition was already used, the **Input Output Selection** dialog box is not displayed this time.</span></span> <span data-ttu-id="dccdd-121">如果连接器重叠，则通过将连接器向左或向右拖将一个连接器向左移，将另一个连接器向右移。</span><span class="sxs-lookup"><span data-stu-id="dccdd-121">If the connectors overlap, move one to left and the other one to right by dragging the connector to left or right.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="dccdd-122">下一步</span><span class="sxs-lookup"><span data-stu-id="dccdd-122">Next Step</span></span>  
 [<span data-ttu-id="dccdd-123">任务 10：添加模糊分组转换以确定重复项</span><span class="sxs-lookup"><span data-stu-id="dccdd-123">Task 10: Adding Fuzzy Group Transform to Identify Duplicates</span></span>](../../2014/tutorials/task-10-adding-fuzzy-group-transform-to-identify-duplicates.md)  
  
  
