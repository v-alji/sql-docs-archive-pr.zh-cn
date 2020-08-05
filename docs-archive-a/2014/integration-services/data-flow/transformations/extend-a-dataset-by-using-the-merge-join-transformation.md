---
title: 使用合并联接转换扩展数据集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Merge Join transformation
- datasets [Integration Services], joining
- datasets [Integration Services], extending
- joining datasets [Integration Services]
ms.assetid: 9e512c3c-f89b-45f3-8281-cdb8f35a2b1f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a387c4ad840eb739d36023be9323c063dcb9a68e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578973"
---
# <a name="extend-a-dataset-by-using-the-merge-join-transformation"></a><span data-ttu-id="059ee-102">使用合并联接转换扩展数据集</span><span class="sxs-lookup"><span data-stu-id="059ee-102">Extend a Dataset by Using the Merge Join Transformation</span></span>
  <span data-ttu-id="059ee-103">若要添加和配置合并联接转换，则包中必须已包含至少一个数据流任务和为合并联接转换提供输入的两个数据流组件。</span><span class="sxs-lookup"><span data-stu-id="059ee-103">To add and configure a Merge Join transformation, the package must already include at least one Data Flow task and two data flow components that provide inputs to the Merge Join transformation.</span></span>  
  
 <span data-ttu-id="059ee-104">合并联接转换需要两个已排序的输入。</span><span class="sxs-lookup"><span data-stu-id="059ee-104">The Merge Join transformation requires two sorted inputs.</span></span> <span data-ttu-id="059ee-105">有关详细信息，请参阅 [为合并转换和合并联接转换排序数据](sort-data-for-the-merge-and-merge-join-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="059ee-105">For more information, see [Sort Data for the Merge and Merge Join Transformations](sort-data-for-the-merge-and-merge-join-transformations.md).</span></span>  
  
### <a name="to-extend-a-dataset"></a><span data-ttu-id="059ee-106">扩展数据集</span><span class="sxs-lookup"><span data-stu-id="059ee-106">To extend a dataset</span></span>  
  
1.  <span data-ttu-id="059ee-107">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="059ee-107">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="059ee-108">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="059ee-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="059ee-109">单击 **“数据流”** 选项卡，然后从 **“工具箱”** 中将合并联接转换拖动到设计图面上。</span><span class="sxs-lookup"><span data-stu-id="059ee-109">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Merge Join transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="059ee-110">将连接线从数据源或前一个转换拖到合并联接转换，从而将合并联接转换连接到数据流。</span><span class="sxs-lookup"><span data-stu-id="059ee-110">Connect the Merge Join transformation to the data flow by dragging the connector from a data source or a previous transformation to the Merge Join transformation.</span></span>  
  
5.  <span data-ttu-id="059ee-111">双击合并联接转换。</span><span class="sxs-lookup"><span data-stu-id="059ee-111">Double-click the Merge Join transformation.</span></span>  
  
6.  <span data-ttu-id="059ee-112">在 **“合并联接转换编辑器”** 对话框的 **“联接类型”** 列表中，选择要用的联接类型。</span><span class="sxs-lookup"><span data-stu-id="059ee-112">In the **Merge Join Transformation Editor** dialog box, select the type of join to use in the **Join type** list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="059ee-113">如果选择了“左外部联接”  类型，那么可以单击“交换输入”  来切换输入，将左外部联接转换为右外部联接。</span><span class="sxs-lookup"><span data-stu-id="059ee-113">If you select the **Left outer join** type, you can click **Swap Inputs** to switch the inputs and convert the left outer join to a right outer join.</span></span>  
  
7.  <span data-ttu-id="059ee-114">将左输入中的列拖动到右输入中的列，以指定联接列。</span><span class="sxs-lookup"><span data-stu-id="059ee-114">Drag columns in the left input to columns in the right input to specify the join columns.</span></span> <span data-ttu-id="059ee-115">如果这些列名称相同，则可以选中 **“联接键”** 复选框，合并联接转换将自动创建联接。</span><span class="sxs-lookup"><span data-stu-id="059ee-115">If the columns have the same name, you can select the **Join Key** check box and the Merge Join transformation automatically creates the join.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="059ee-116">只能在具有相同排序位置的列之间创建联接，而且必须按照排序位置所指定的顺序创建联接。</span><span class="sxs-lookup"><span data-stu-id="059ee-116">You can create joins only between columns that have the same sort position, and the joins must be created in the order specified by the sort position.</span></span> <span data-ttu-id="059ee-117">如果尝试不按顺序创建联接， **“合并联接转换编辑器”** 会提示您为跳过的排序顺序位置创建其他联接。</span><span class="sxs-lookup"><span data-stu-id="059ee-117">If you attempt to create the joins out of order, the **Merge Join Transformation Editor** prompts you to create additional joins for the skipped sort order positions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="059ee-118">默认情况下，输出根据联接列进行排序。</span><span class="sxs-lookup"><span data-stu-id="059ee-118">By default, the output is sorted on the join columns.</span></span>  
  
8.  <span data-ttu-id="059ee-119">在左输入和右输入中，选中要包含在输出中的其他列的复选框。</span><span class="sxs-lookup"><span data-stu-id="059ee-119">In the left and right inputs, select the check boxes of additional columns to include in the output.</span></span> <span data-ttu-id="059ee-120">默认情况下包含联接列。</span><span class="sxs-lookup"><span data-stu-id="059ee-120">Join columns are included by default.</span></span>  
  
9. <span data-ttu-id="059ee-121">还可以更新 **“输出别名”** 列中的输出列名称。</span><span class="sxs-lookup"><span data-stu-id="059ee-121">Optionally, update the names of output columns in the **Output Alias** column.</span></span>  
  
10. <span data-ttu-id="059ee-122">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="059ee-122">Click **OK**.</span></span>  
  
11. <span data-ttu-id="059ee-123">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="059ee-123">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="059ee-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="059ee-124">See Also</span></span>  
 <span data-ttu-id="059ee-125">[合并联接转换](merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="059ee-125">[Merge Join Transformation](merge-join-transformation.md) </span></span>  
 <span data-ttu-id="059ee-126">[Integration Services 转换](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="059ee-126">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="059ee-127">[Integration Services 路径](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="059ee-127">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="059ee-128">数据流任务</span><span class="sxs-lookup"><span data-stu-id="059ee-128">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
