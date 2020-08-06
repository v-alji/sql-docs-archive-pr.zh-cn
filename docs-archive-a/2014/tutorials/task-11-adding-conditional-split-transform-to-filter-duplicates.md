---
title: 任务11：添加有条件拆分转换以筛选重复项 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3094bd57-5cf4-4860-bf51-fadd1b309f94
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e8370563c4275df0d0513d5434a8b16efba728d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694181"
---
# <a name="task-11-adding-conditional-split-transform-to-filter-duplicates"></a><span data-ttu-id="09f9c-102">任务 11：添加有条件拆分转换以筛选重复项</span><span class="sxs-lookup"><span data-stu-id="09f9c-102">Task 11: Adding Conditional Split Transform to Filter Duplicates</span></span>
  <span data-ttu-id="09f9c-103">在本任务中，您将向数据流添加有条件拆分转换。</span><span class="sxs-lookup"><span data-stu-id="09f9c-103">In this task, you add the Conditional Split Transform to the data flow.</span></span> <span data-ttu-id="09f9c-104">此转换帮助您从传入的记录集筛选重复项。</span><span class="sxs-lookup"><span data-stu-id="09f9c-104">This transform helps you filter duplicates from the incoming record set.</span></span> <span data-ttu-id="09f9c-105">模糊分组转换将它找到的记录分组为匹配项并选择其中一个记录作为透视记录。</span><span class="sxs-lookup"><span data-stu-id="09f9c-105">The Fuzzy Group transform groups the records that it finds to be matches and picks one of the records as a pivot record.</span></span> <span data-ttu-id="09f9c-106">组中的所有记录都具有相同的 _key_out 值。</span><span class="sxs-lookup"><span data-stu-id="09f9c-106">All the records in a group have the same _key_out value.</span></span> <span data-ttu-id="09f9c-107">组中的透视记录具有与 _key_out 值相同的 _key_in。</span><span class="sxs-lookup"><span data-stu-id="09f9c-107">The pivot record in the group has _key_in same as the _key_out value.</span></span> <span data-ttu-id="09f9c-108">组中的其他记录的 _key_in 和 _key_out 值不同。</span><span class="sxs-lookup"><span data-stu-id="09f9c-108">The other records in the group have different values for _key_in and _key_out.</span></span> <span data-ttu-id="09f9c-109">因此，当使用条件 _key_in==_key_out 筛选时，只能得到组中的透视行。</span><span class="sxs-lookup"><span data-stu-id="09f9c-109">Therefore, when you filter using the condition _key_in==_key_out, you only get the pivot row in the group.</span></span>  
  
1.  <span data-ttu-id="09f9c-110">从 " **SSIS 工具箱**" 中的 "**公共**" 部分**拖放到**"**数据流" 选项卡**上。</span><span class="sxs-lookup"><span data-stu-id="09f9c-110">Drag-drop **Conditional Split** Transform from **Common** section in the **SSIS Toolbox** to the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="09f9c-111">右键单击 "数据流 **" 选项卡**中的 "有**条件拆分转换**"，然后单击 "**重命名**"。</span><span class="sxs-lookup"><span data-stu-id="09f9c-111">Right-click **Conditional Split Transform** in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="09f9c-112">键入**筛选器重复项**，然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="09f9c-112">Type **Filter Duplicates** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="09f9c-113">连接**组具有匹配 id 的供应商**以**筛选重复项**。</span><span class="sxs-lookup"><span data-stu-id="09f9c-113">Connect **Group Suppliers with Matching IDs** to **Filter Duplicates**.</span></span>  
  
4.  <span data-ttu-id="09f9c-114">双击 "**筛选重复项**" 以启动 "有**条件拆分转换编辑器**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="09f9c-114">Double-click **Filter Duplicates** to launch the **Conditional Split Transform Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="09f9c-115">在左上方窗格中展开 "**列**"。</span><span class="sxs-lookup"><span data-stu-id="09f9c-115">Expand **Columns** in the top-left pane.</span></span>  
  
6.  <span data-ttu-id="09f9c-116">将 **_key_in**拖放到 "**条件**" 列。</span><span class="sxs-lookup"><span data-stu-id="09f9c-116">Drag-drop **_key_in** to the **Condition** column.</span></span>  
  
7.  <span data-ttu-id="09f9c-117">键入 = = (等于 **_key_in**并拖放 **_key_out**) 旁边。</span><span class="sxs-lookup"><span data-stu-id="09f9c-117">Type == (equals to) next to **_key_in** and drag-drop **_key_out**.</span></span>  
  
8.  <span data-ttu-id="09f9c-118">单击 "**输出名称**" 列中的 "**事例 1** "，键入 "**唯一记录**"，然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="09f9c-118">Click **Case 1** in the **Output Name** column, type **Unique Records**, and press **ENTER**.</span></span>  
  
     <span data-ttu-id="09f9c-119">![有条件拆分转换编辑器](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "有条件拆分转换编辑器")</span><span class="sxs-lookup"><span data-stu-id="09f9c-119">![Conditional Split Transformation Editor](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "Conditional Split Transformation Editor")</span></span>  
  
9. <span data-ttu-id="09f9c-120">单击 **"确定"** 以关闭 "有**条件拆分转换编辑器**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="09f9c-120">Click **OK** to close the **Conditional Split Transformation Editor** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="09f9c-121">下一步</span><span class="sxs-lookup"><span data-stu-id="09f9c-121">Next Step</span></span>  
 [<span data-ttu-id="09f9c-122">任务 12：添加派生列转换以添加 MDS 所需的列</span><span class="sxs-lookup"><span data-stu-id="09f9c-122">Task 12: Adding Derived Column Transform to Add Columns Required by MDS</span></span>](../../2014/tutorials/task-12-adding-derived-column-transform-to-add-columns-required-by-mds.md)  
  
  
