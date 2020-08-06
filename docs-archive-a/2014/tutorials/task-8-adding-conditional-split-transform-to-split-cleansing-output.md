---
title: 任务8：添加有条件拆分转换以拆分清理输出 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d4ebe420-a4a9-4076-89d3-41abe726fc5c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9be7ea6f5330382ad0417df99e18bcba5b59a4e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577124"
---
# <a name="task-8-adding-conditional-split-transform-to-split-cleansing-output"></a><span data-ttu-id="596ba-102">任务 8：添加有条件拆分转换以拆分清理输出</span><span class="sxs-lookup"><span data-stu-id="596ba-102">Task 8: Adding Conditional Split Transform to Split Cleansing Output</span></span>
  <span data-ttu-id="596ba-103">在此转换中，您向数据流添加有条件拆分转换。</span><span class="sxs-lookup"><span data-stu-id="596ba-103">In this transform, you add a Conditional Split Transform to the data flow.</span></span> <span data-ttu-id="596ba-104">有条件拆分转换可以根据数据内容将行路由到不同的输出。</span><span class="sxs-lookup"><span data-stu-id="596ba-104">The Conditional Split transformation can route rows to different outputs based on the content of the data.</span></span> <span data-ttu-id="596ba-105">对于本教程，请使用 DQS 清理转换中的 "**记录状态**" 输出列。</span><span class="sxs-lookup"><span data-stu-id="596ba-105">For this tutorial, you use the **Record Status** output column from the DQS Cleansing transform.</span></span> <span data-ttu-id="596ba-106">在本教程中，您将只向 MDS 服务器上载正确或已更正的记录。</span><span class="sxs-lookup"><span data-stu-id="596ba-106">You will upload only correct or corrected records to MDS server in this tutorial.</span></span> <span data-ttu-id="596ba-107">因此，您需要检查**记录状态**是否**正确**，**并**在将记录上载到 MDS 之前合并记录。</span><span class="sxs-lookup"><span data-stu-id="596ba-107">Therefore you check if the **Record Status** is **Correct** or **Corrected**, and combine the records before uploading the records to MDS.</span></span>  
  
1.  <span data-ttu-id="596ba-108">从 " **SSIS 工具箱**" 中的 "**公共**" 部分拖放到 "**清理供应商数据**" 下**的 "数据流**" 选项**卡中。**</span><span class="sxs-lookup"><span data-stu-id="596ba-108">Drag-drop **Conditional Split Transform** from **Common** section in the **SSIS Toolbox** to the **Data Flow** tab under **Cleanse Supplier Data**.</span></span>  
  
2.  <span data-ttu-id="596ba-109">右键单击 "**条件拆分**"，然后单击 "**重命名**"。</span><span class="sxs-lookup"><span data-stu-id="596ba-109">Right-click **Conditional Split**, and click **Rename**.</span></span> <span data-ttu-id="596ba-110">键入 "**选择正确和已更正的记录**"，然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="596ba-110">Type **Pick Correct and Corrected Records** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="596ba-111">连接**清理供应商数据**，并使用蓝色连接器**选择正确和更正的记录**。</span><span class="sxs-lookup"><span data-stu-id="596ba-111">Connect **Cleanse Supplier Data** and **Pick Correct and Corrected Records** using the blue connector.</span></span>  
  
     <span data-ttu-id="596ba-112">![清理供应商数据-> 选取正确的 & 更正](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "清理供应商数据 -> 选择正确和已更正的记录")</span><span class="sxs-lookup"><span data-stu-id="596ba-112">![Cleanse Supplier Data -> Pick Correct & Corrected](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "Cleanse Supplier Data -> Pick Correct & Corrected")</span></span>  
  
4.  <span data-ttu-id="596ba-113">双击 **"数据流" 选项**卡中的 "**选择正确和已更正的记录**"。</span><span class="sxs-lookup"><span data-stu-id="596ba-113">Double-click **Pick Correct and Corrected Records** in the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="596ba-114">更改屏幕底部的**默认输出名称**以**更正**。</span><span class="sxs-lookup"><span data-stu-id="596ba-114">Change the **Default Output Name** at the bottom of the screen to **Correct**.</span></span>  
  
6.  <span data-ttu-id="596ba-115">在**左上方窗格**中展开 "**列**"。</span><span class="sxs-lookup"><span data-stu-id="596ba-115">Expand **Columns** in the **top-left pane**.</span></span>  
  
     <span data-ttu-id="596ba-116">![有条件拆分转换编辑器](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "有条件拆分转换编辑器")</span><span class="sxs-lookup"><span data-stu-id="596ba-116">![Conditional Split Transformation Editor](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "Conditional Split Transformation Editor")</span></span>  
  
7.  <span data-ttu-id="596ba-117">将**记录状态**拖放到 "**条件**" 列。</span><span class="sxs-lookup"><span data-stu-id="596ba-117">Drag-drop **Record Status** to the **Condition** column.</span></span>  
  
8.  <span data-ttu-id="596ba-118">对于 "**条件**"**列，Type** **= = "更正"** 。</span><span class="sxs-lookup"><span data-stu-id="596ba-118">Type **=="Corrected"** next to **[Record Status]** for the **Condition** column.</span></span>  
  
9. <span data-ttu-id="596ba-119">单击 "**输出名称" 列**中的 "**事例 1** "，然后将名称更改为 "已**更正**"。</span><span class="sxs-lookup"><span data-stu-id="596ba-119">Click **Case 1** in the **Output Name Column**, and change the name to **Corrected**.</span></span>  
  
10. <span data-ttu-id="596ba-120">单击 **"确定"** 以关闭 "有**条件拆分转换编辑器**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="596ba-120">Click **OK** to close the **Conditional Split Transformation Editor** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="596ba-121">下一步</span><span class="sxs-lookup"><span data-stu-id="596ba-121">Next Step</span></span>  
 [<span data-ttu-id="596ba-122">任务 9：添加 Union All 转换以合并正确和已更正的记录</span><span class="sxs-lookup"><span data-stu-id="596ba-122">Task 9: Adding Union All Transform to Combine Correct and Corrected Records</span></span>](../../2014/tutorials/task-9-adding-union-all-transform-to-combine-correct-and-corrected-records.md)  
  
  
